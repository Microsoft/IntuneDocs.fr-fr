---
title: Créer des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou configurez un profil d’appareil dans Microsoft Intune, ce qui inclut la sélection du type de plateforme et la configuration des paramètres dans le portail Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3f62e306574606ffa1eb1e6f242c3cb30b1a9c1b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744650"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Créer un profil d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 et versions ultérieures**
       - **Windows 10 et versions ultérieures**

   - **Type de profil** : sélectionnez le type que vous souhaitez créer. La liste dépend de la plateforme que vous choisissez.
   - **Paramètres** : les rubriques suivantes décrivent les paramètres pour chaque type de profil.

       -  [Fonctionnalités de l’appareil](device-features-configure.md)
       -  [Restrictions relatives aux appareils](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [Kiosque](kiosk-settings.md)
       -  [E-mail](email-settings-configure.md)
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
