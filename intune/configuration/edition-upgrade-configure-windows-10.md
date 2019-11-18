---
title: Mettre à niveau des appareils Windows 10 ou les utiliser en mode S – Microsoft Intune – Azure | Microsoft Docs
description: Utilisez Microsoft Intune pour mettre à niveau des appareils Windows 10 vers une autre édition ou activer le mode S. Les administrateurs peuvent utiliser un profil de configuration d’appareil pour mettre à niveau Windows 10 Professionnel vers Windows 10 Entreprise et désactiver le mode S. Découvrez les chemins de mise à niveau pris en charge pour Windows 10 Professionnel, Édition N, Éducation, Cloud, Entreprise, Standard, Holographique et Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cce3fafa1a8a074ea70692f855be1e032f0462f
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755246"
---
# <a name="upgrade-windows-10-editions-or-switch-out-of-s-mode-on-devices-using-microsoft-intune"></a>Mettre à niveau les éditions Windows 10 ou désactiver le mode S sur des appareils avec Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Dans le cadre de votre solution de gestion des appareils mobiles (MDM), vous pouvez chercher à mettre à niveau vos appareils Windows 10, par exemple, de Windows 10 Professionnel vers Windows 10 Entreprise. Ou, vous voulez que l'appareil sorte du mode S.

Le [mode S Windows 10](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) (ouvre un autre site web Microsoft) est conçu pour la sécurité et la performance. Vous pouvez utiliser Intune pour sortir du mode S. La sortie du mode S est définitive. Une fois que vous êtes sorti du mode S, vous ne pouvez plus revenir au mode S Windows 10.

Consultez quelques [questions fréquemment posées](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq) sur le mode S.

Cette fonctionnalité s’applique à :

- Windows 10 et versions ultérieures
- Windows 10 1809 (ou version ultérieure) pour le mode S
- Windows Holographic for Business

Ces fonctionnalités, disponibles dans Intune, sont configurables par l’administrateur. Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités à un profil, vous pouvez envoyer (push) ou déployer ce profil auprès des appareils Windows 10 de votre organisation. Lorsque vous le déployez, Intune met automatiquement à niveau les appareils ou désactive le mode S.

Cet article liste les chemins de mise à niveau pris en charge et explique comment créer le profil de configuration d’appareil. Vous y trouverez également tous les paramètres de mise à niveau et de mode S disponibles pour [Windows 10](edition-upgrade-windows-settings.md).

> [!NOTE]
> Si, plus tard, vous supprimez l’affectation de stratégie, l’appareil ne revient pas à la dernière version de Windows. Il continue de fonctionner normalement.

## <a name="prerequisites"></a>Prérequis

Avant de mettre à niveau des appareils, vérifiez que les conditions suivantes sont remplies :

- Une clé de produit valide pour installer la version de Windows mise à jour sur tous les appareils que vous ciblez avec la stratégie (pour les éditions Windows 10 Desktop). Vous pouvez utiliser les touches Clés d’activation multiple (MAK) ou Serveur gestionnaire de clés (KMS).
- Pour les éditions Windows 10 Mobile et Windows 10 Holographic, vous pouvez utiliser un fichier de licence Microsoft. Il comporte les informations de licence permettant d’installer l’édition mise à jour sur tous les appareils ciblés par la stratégie.
- Les appareils Windows 10 auxquels vous affectez la stratégie sont inscrits dans Microsoft Intune. Vous ne pouvez pas utiliser la stratégie de mise à niveau d’édition avec des PC qui exécutent le logiciel client PC Intune.

## <a name="supported-upgrade-paths"></a>Options de mise à niveau prises en charge

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

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)  (X) = not supported    
![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Mobile|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Holographic|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png) -->

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil. Par exemple, entrez quelque chose comme `Windows 10 edition upgrade profile` ou `Windows 10 switch off S mode`.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : sélectionnez **Mise à niveau d’édition**.
    - **Paramètres** : Entrez les paramètres à configurer. Pour obtenir la liste de tous les paramètres, ainsi que leur rôle, voir :

        - [Mise à niveau de Windows 10 et mode S](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste. [Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Consultez les paramètres de mise à niveau et de mode S pour les appareils [Windows 10](edition-upgrade-windows-settings.md) et [Windows Holographic for Business](holographic-upgrade.md).
