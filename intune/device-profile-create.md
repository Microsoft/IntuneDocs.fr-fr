---
title: Créer des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou configurez un profil d’appareil dans Microsoft Intune, ce qui inclut la sélection du type de plateforme et la configuration des paramètres dans le portail Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e5070052c0d4cce3cfd81a7bae259bc7dfb22e7f
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Créer un profil d’appareil dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Créer le profil
1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, puis recherchez **Microsoft Intune**.

2. Dans **Microsoft Intune**, sélectionnez **Configuration de l’appareil**, puis **Profils**. Ensuite, sélectionnez **Créer un profil**.

3. Entrez les propriétés suivantes :

    - **Nom** : attribuez un nom descriptif au nouveau profil.
    - **Description :** entrez une description pour le profil. (Ceci est facultatif mais recommandé.)
    - **Plateforme** : sélectionnez le type de plateforme.  

        - **Android**
        - **Android for Work**
        - **iOS**
        - **MacOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 et versions ultérieures**
        - **Windows 10 et versions ultérieures**

    - **Type de profil** : sélectionnez le type que vous souhaitez créer. La liste dépend de la plateforme que vous choisissez.
    - **Paramètres** : les rubriques suivantes décrivent les paramètres pour chaque type de profil.

        -  [Paramètres de fonctionnalité d’appareil](device-features-configure.md)
        -  [Paramètres de restriction d'appareil](device-restrictions-configure.md)
        -  [Paramètres de courrier électronique](email-settings-configure.md)
        -  [Paramètres VPN](vpn-settings-configure.md)
        -  [Paramètres Wi-Fi](wi-fi-settings-configure.md)
        -  [Paramètres de mise à niveau Windows 10](edition-upgrade-configure-windows-10.md)
        -  [Paramètres de certificat](certificates-configure.md)
        -  [Paramètres de Windows Information Protection](windows-information-protection-configure.md)
        -  [Paramètres de formation](education-settings-configure.md)
        -  [Paramètres personnalisés](custom-settings-configure.md)

    ![Capture d’écran de création d’un profil](./media/create-device-profile.png)

4. Sélectionnez **Créer** quand vous avez terminé.

Le profil est créé et apparaît dans la liste.


## <a name="next-steps"></a>Étapes suivantes
Pour affecter des profils d’appareil, consultez [Guide pratique pour affecter des profils d’appareil avec Microsoft Intune](device-profile-assign.md).
