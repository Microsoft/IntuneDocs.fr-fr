---
title: Configurer une stratégie d’accès conditionnel en fonction de l’application avec Intune
titleSuffix: Microsoft Intune
description: Découvrez comment créer une stratégie d’accès conditionnel basée sur l’application avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712838"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurer des stratégies d’accès conditionnel basées sur des applications avec Intune

Configurez des stratégies d’accès conditionnel basées sur des applications pour les applications qui figurent dans la liste des applications approuvées. La liste des applications approuvées se compose d’applications ayant été testées par Microsoft.

Vous devez appliquer les [stratégies Intune App Protection](../apps/app-protection-policies.md) à vos applications pour pouvoir utiliser des stratégies d’accès conditionnel en fonction de l’application.

> [!IMPORTANT]
> Cet article décrit les étapes permettant d’ajouter une stratégie d’accès conditionnel basé sur l’application. Vous pouvez utiliser les mêmes étapes quand vous ajoutez des applications comme SharePoint Online, Microsoft Teams et Microsoft Exchange Online à partir de la liste des applications approuvées.

## <a name="create-app-based-conditional-access-policies"></a>Créer des stratégies d’accès conditionnel basées sur l’application

L’accès conditionnel est une technologie Azure Active Directory (Azure AD). Le nœud Accès conditionnel accessible à partir *d’Intune* est le même que celui qui est accessible à partir *d’Azure AD*. Comme il s’agit du même nœud, il n’est pas nécessaire de basculer entre Intune et Azure AD pour configurer des stratégies.

Vous devez disposer d’une licence Azure AD Premium pour pouvoir créer des stratégies d’accès conditionnel dans le Centre d’administration du Gestionnaire de points de terminaison Microsoft.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Créer des stratégies d’accès conditionnel basées sur l’application

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Sécurité des points de terminaison** > **Accès conditionnel** > **Nouvelle stratégie**.

3. Entrez un **Nom** de stratégie, puis sélectionnez **Utilisateurs et groupes** sous *Affectations*. Utilisez les options Inclure et Exclure pour ajouter vos groupes à la stratégie, puis sélectionnez **Terminé**.

4. Sélectionnez **Applications cloud ou actions**, puis choisissez les applications à protéger. Par exemple, choisissez **Sélectionner les applications**, puis sélectionnez **Office 365 SharePoint Online** et **Office 365 Exchange Online**.

   Sélectionnez **Terminé** pour enregistrer vos changements.

5. Sélectionnez **Conditions** > **Applications clientes** pour appliquer la stratégie aux applications et aux navigateurs. Par exemple, sélectionnez **Oui**, puis activez **Navigateur** et **Applications mobiles et clients de bureau**.

   Sélectionnez **Terminé** pour enregistrer vos changements.

6. Sous *Contrôles d’accès*, sélectionnez **Accorder** pour appliquer l’accès conditionnel en fonction de la conformité des appareils. Par exemple, sélectionnez **Accorder l’accès** > **Exiger que l’appareil soit marqué comme conforme**.

   Choisissez **Sélectionner** pour enregistrer vos changements.

7. Dans **Activer la stratégie**, sélectionnez **Activé**, puis sélectionnez **Créer** pour enregistrer vos modifications.





## <a name="next-steps"></a>Étapes suivantes
[Bloquer les applications sans authentification moderne](app-modern-authentication-block.md)

## <a name="see-also"></a>Voir aussi

[Protéger les données d’application à l’aide de stratégies de protection des applications](../apps/app-protection-policies.md)
[Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
