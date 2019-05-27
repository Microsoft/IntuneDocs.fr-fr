---
title: Résoudre des conflits de stratégie entre les objets de stratégie de groupe et Intune
titleSuffix: Microsoft Intune
description: Découvrez comment résoudre les conflits entre les stratégies de configuration de la stratégie de groupe et Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6c7de15c3839548e8edf5056579eab1c0c0751a
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66045256"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>Résoudre des conflits de stratégie entre les objets de stratégie de groupe (GPO) et Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Intune utilise des stratégies qui vous aident à gérer des paramètres sur les PC Windows. Par exemple, vous pouvez utiliser une stratégie de contrôle des paramètres du Pare-feu Windows sur les PC. De nombreux paramètres Intune sont identiques à ceux que vous pouvez configurer avec la stratégie de groupe Windows. Toutefois, il est possible que, dans certains cas, les deux méthodes entrent en conflit l’une avec l’autre.

Lorsque des conflits se produisent, la stratégie de groupe au niveau du domaine est prioritaire sur la stratégie Intune, sauf si le PC ne peut pas se connecter au domaine. Dans ce cas, la stratégie Intune est appliquée au PC client.

## <a name="what-to-do-if-you-are-using-group-policy"></a>Que faire si vous utilisez la stratégie de groupe ?
Vérifiez que toutes les stratégies que vous appliquez ne sont pas gérées par la stratégie de groupe. Pour mieux éviter les conflits, vous pouvez employer une ou plusieurs des méthodes suivantes :

-   Déplacez vos PC vers une unité d’organisation Active Directory à laquelle les paramètres de la stratégie de groupe ne sont pas appliqués avant d’installer le client Intune. Vous pouvez également bloquer l’héritage de la stratégie de groupe sur les unités d’organisation contenant les PC inscrits dans Intune auxquels vous ne voulez pas appliquer les paramètres de la stratégie de groupe.

-   Utilisez un filtre de groupe de sécurité pour restreindre les objets de stratégie de groupe aux seuls PC qui ne sont pas gérés par Intune.

-   Désactivez ou supprimez les objets de stratégie de groupe en conflit avec les stratégies Intune.

Pour plus d'informations sur Active Directory et la stratégie de groupe Windows, consultez votre documentation Windows Server.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Comment filtrer les objets de stratégie de groupe existants pour éviter les conflits avec la stratégie Intune
Si vous avez identifié des objets de stratégie de groupe dont les paramètres sont en conflit avec les stratégies Intune, vous pouvez utiliser des filtres de groupe de sécurité pour restreindre ces objets aux seuls PC qui ne sont pas gérés par Intune.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Vous ne pouvez appliquer des objets de stratégie de groupe (GPO) qu’aux groupes de sécurité qui sont spécifiés dans la zone **Filtrage de sécurité** de la console de gestion des stratégies de groupe d’un GPO sélectionné. Par défaut, les GPO s’appliquent aux *Utilisateurs authentifiés*.

-   Dans le composant logiciel enfichable **Utilisateurs et ordinateurs Active Directory**, créez un groupe de sécurité contenant les ordinateurs et les comptes d’utilisateurs que vous ne voulez pas gérer avec Intune. Par exemple, vous pouvez nommer le groupe *Pas dans Microsoft Intune*.

-   Dans la console de gestion des stratégies de groupe, sous l’onglet **Délégation** pour le GPO sélectionné, cliquez avec le bouton droit de la souris sur le nouveau groupe de sécurité pour déléguer les autorisations **Lecture** et **Appliquer la stratégie de groupe** appropriées aux utilisateurs et aux ordinateurs dans le groupe de sécurité. (Les autorisations**Appliquer stratégie de groupe** sont disponibles dans la boîte de dialogue **Options avancées** ).

-   Ensuite, appliquez le nouveau filtre de groupe de sécurité à un GPO sélectionné et supprimez le filtre par défaut **Utilisateurs authentifiés**.

Le nouveau groupe de sécurité doit être maintenu comme inscription dans les modifications de service Intune.

### <a name="see-also"></a>Voir aussi
[Gérer des PC Windows avec Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
