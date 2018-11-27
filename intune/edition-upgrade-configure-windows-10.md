---
title: Mettre à niveau des appareils Windows 10 ou les utiliser en mode S avec Microsoft Intune - Azure | Microsoft Docs
description: Créez un profil d’appareil dans Microsoft Intune pour mettre à niveau les appareils Windows 10 vers d’autres éditions. Par exemple, vous pouvez effectuer une mise à niveau de Windows 10 Professionnel vers Windows 10 Entreprise. Vous pouvez également activer le mode S sur un appareil, ou sortir de ce mode, à l’aide du profil de configuration. Découvrez également les chemins de mise à niveau pris en charge pour Windows 10 Professionnel, Édition N, Éducation, Cloud, Entreprise, Standard, Holographique et Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eb44647e50e406b9ef5052c576660c9b7eebf6dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189756"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Utiliser un profil de configuration pour mettre à niveau Windows 10, ou pour sortir du mode S dans Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurez un profil de mise à niveau dans Intune pour mettre à niveau automatiquement les appareils qui exécutent Windows 10 vers une version différente. Découvrez également les chemins de mise à niveau pris en charge.

## <a name="before-you-begin"></a>Avant de commencer
Avant de mettre à niveau des appareils vers la dernière version, vous devez connaître les prérequis suivants :

- Une clé de produit valide pour installer la version de Windows mise à jour sur tous les appareils que vous ciblez avec la stratégie (pour les éditions Windows 10 Desktop). Vous pouvez utiliser les touches Clés d’activation multiple (MAK) ou Serveur gestionnaire de clés (KMS). Pour les éditions Windows 10 Mobile et Windows 10 Holographique, vous pouvez utiliser un fichier de licence Microsoft comprenant les informations de licence afin d’installer la version mise à jour de Windows sur tous les appareils ciblés avec la stratégie.
- Les appareils Windows 10 auxquels vous affectez la stratégie sont inscrits dans Microsoft Intune. Vous ne pouvez pas utiliser la stratégie de mise à niveau d’édition avec des PC qui exécutent le logiciel client PC Intune.

## <a name="supported-upgrade-paths"></a>Chemins de mise à niveau pris en charge
Le tableau suivant indique les chemins de mise à niveau pris en charge pour le profil de mise à niveau de l’édition Windows 10.

| Mise à niveau à partir de | Mise à niveau vers |
|---|---|
| Windows 10 Professionnel | Windows 10 Éducation <br/>Windows 10 Entreprise <br/>Windows 10 Pro Éducation |
| Windows 10 Professionnel N | Windows 10 Éducation N <br/>Windows 10 Édition Entreprise N <br/>Windows 10 Pro Éducation N | 
| Windows 10 Pro Éducation | Windows 10 Éducation | 
| Windows 10 Pro Éducation N | Windows 10 Éducation N |
| Windows 10 Cloud | Windows 10 Éducation <br/>Windows 10 Entreprise <br/>Windows 10 Professionnel <br/>Windows 10 Pro Éducation | 
| Windows 10 Cloud N | Windows 10 Éducation N <br/>Windows 10 Édition Entreprise N <br/>Windows 10 Professionnel N <br/>Windows 10 Pro Éducation N | 
| Windows 10 Entreprise | Windows 10 Éducation | 
| Windows 10 Édition Entreprise N | Windows 10 Éducation N | 
| Windows 10 Core | Windows 10 Éducation <br/>Windows 10 Entreprise <br/>Windows 10 Pro Éducation | 
| Windows 10 Core N | Windows 10 Éducation N <br/>Windows 10 Édition Entreprise N <br/>Windows 10 Pro Éducation N | 
| Windows 10 Holographique | Windows 10 Holographique pour entreprises |
| Windows 10 Mobile | Windows 10 Mobile Entreprise |


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="upgrade-the-edition"></a>Mettre à niveau l’édition

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez un **Nom** et une **Description** pour le profil. Par exemple, entrez quelque chose du genre `Windows 10 edition upgrade`
4. Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
5. Pour **Type de profil**, sélectionnez **Mise à niveau d’édition**.
6. Dans les propriétés **Mise à niveau d’édition**, entrez les paramètres suivants :

   - **Édition vers laquelle la mise à niveau est effectuée** : sélectionnez l’édition de Windows 10 vers laquelle vous effectuez la mise à niveau. Les appareils ciblés par cette stratégie sont mis à niveau vers l’édition de votre choix.
   - **Clé de produit** : entrez la clé de produit fournie par Microsoft. Une fois que vous avez créé la stratégie basée sur la clé de produit, la clé ne peut plus être mise à jour et est masquée pour des raisons de sécurité. Pour changer la clé de produit, retapez-la en entier.
   - **Fichier de licence** : pour **Windows 10 Holographic for Business** ou **Windows 10 Mobile**, choisissez **Parcourir** afin de sélectionner le fichier de licence fourni par Microsoft. Ce fichier de licence contient des informations de licence pour les éditions vers lesquelles vous mettez à niveau les appareils ciblés.

7. Cliquez sur **OK** pour enregistrer vos modifications. Sélectionnez **Créer** pour créer le profil.

## <a name="switch-out-of-s-mode"></a>Sortir du mode S

Le [mode S de Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) est conçu pour la sécurité et les performances. Si vos appareils exécutent uniquement des applications provenant du Microsoft Store, vous pouvez utiliser le mode S pour sécuriser ces appareils. Si vos appareils nécessitent des applications qui ne sont pas disponibles dans le Microsoft Store, vous pouvez sortir du mode S. La sortie du mode S est définitive. Une fois que vous êtes sorti du mode S, vous ne pouvez plus revenir au mode S Windows 10.

Les étapes suivantes montrent comment créer un profil qui contrôle le mode S sur des appareils Windows 10 (1809 ou version ultérieure).

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez un **Nom** et une **Description** pour le profil. Par exemple, entrez quelque chose du genre `Windows 10 switch off S mode`
4. Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
5. Pour **Type de profil**, sélectionnez **Mise à niveau d’édition**.
6. Sélectionnez **Changement de mode (Windows Insider uniquement)**, puis définissez la propriété **Sortir du mode S**. Les options disponibles sont les suivantes :

    - **Aucune configuration** : un appareil en mode S reste en mode S. Un utilisateur final peut sortir l’appareil du mode S.
    - **Rester en mode S** : empêche l’utilisateur final de sortir l’appareil du mode S.
    - **Changer** : permet de sortir l’appareil du mode S.

7. Cliquez sur **OK** pour enregistrer vos modifications. Sélectionnez **Créer** pour créer le profil.

Le profil est créé et apparaît dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

[Affectez ce profil](device-profile-assign.md) à vos groupes.

>[!NOTE]
>Si vous supprimez plus tard l’affectation de stratégie, la version de Windows de l’appareil n’est pas restaurée et continue de fonctionner normalement.
