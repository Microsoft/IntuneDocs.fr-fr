---
title: Créer des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou configurez un profil d’appareil dans Microsoft Intune, ce qui inclut la sélection du type de plateforme et la configuration des paramètres dans le portail Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aaa8692a17e7e78378905e79b4046727d91c7c92
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238878"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Créer un profil d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.

2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.

3. Entrez les propriétés suivantes :

   - **Nom** : Entrez un nom descriptif pour le nouveau profil.
   - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : sélectionnez le type de plateforme :  

       - **Android**
       - **Android Entreprise**
       - **iOS**
       - **MacOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 et versions ultérieures**
       - **Windows 10 et versions ultérieures**

   - **Type de profil** : sélectionnez le type que vous souhaitez créer. La liste dépend de la plateforme que vous choisissez.
   - **Paramètres** : Les articles suivants décrivent les paramètres pour chaque type de profil :

       -  [Fonctionnalités de l’appareil](device-features-configure.md)
       -  [Restrictions relatives aux appareils](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [Identity protection](identity-protection-configure.md)  
       -  [Kiosque](kiosk-settings.md)
       -  [Courrier électronique](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  Éducation pour [Windows 10](education-settings-configure.md) et [iOS](wi-fi-settings-ios.md)
       -  [Mise à niveau de l’édition Windows 10](edition-upgrade-configure-windows-10.md)
       -  [Stratégies de mise à jour iOS](software-updates-ios.md)
       -  [Certificats](certificates-configure.md)
       -  [Protection des informations Windows](windows-information-protection-configure.md)
       -  [Personnalisé](custom-settings-configure.md)

     ![Capture d’écran de création d’un profil](./media/create-device-profile.png)

4. Sélectionnez **Créer** quand vous avez terminé.

Le profil est créé et apparaît dans la liste.

## <a name="next-steps"></a>Étapes suivantes
[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
