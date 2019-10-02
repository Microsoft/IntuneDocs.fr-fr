---
title: Créer un profil Wi-Fi pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Suivez les étapes pour créer un profil de configuration d’appareil dans Microsoft Intune. Créez des profils pour Android, Android Entreprise, Android Kiosk, iOS, macOS, Windows 10 et versions ultérieures et Windows Holographic for Business. Utilisez ces profils pour créer une connexion Wi-Fi afin d’utiliser des certificats, choisissez un type EAP, sélectionnez une méthode d’authentification, activez un proxy et bien plus encore.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80e70db4b64770af1a96ee7f24a3cf875269adce
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723734"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Ajoutez et utilisez des paramètres Wi-Fi sur vos appareils dans Microsoft Intune

Wi-Fi est un réseau sans fil qui est utilisé par de nombreux appareils mobiles pour obtenir un accès réseau. Microsoft Intune inclut des paramètres Wi-Fi intégrés qui peuvent être déployés pour les utilisateurs et appareils de votre organisation. Ce groupe de paramètres est appelé « profil » et peut être attribué à différents utilisateurs et groupes. Une fois le profil attribué, vos utilisateurs peuvent accéder au réseau Wi-Fi de votre organisation sans le configurer eux-mêmes.

Par exemple, vous installez un nouveau réseau Wi-Fi nommé Contoso Wi-Fi. Ensuite, vous souhaitez configurer tous les appareils iOS pour vous connecter à ce réseau. Voici le processus :

1. Créez un profil Wi-Fi incluant les paramètres pour se connecter au réseau sans fil Contoso Wi-Fi.
2. Attribuez le profil à un groupe contenant tous les utilisateurs d’appareils iOS.
3. Les utilisateurs recherchent le nouveau réseau Wi-Fi Contoso dans la liste des réseaux sans fil sur leur appareil. Ils peuvent alors se connecter au réseau, à l’aide de la méthode d’authentification de votre choix.

Cet article répertorie les étapes pour créer un profil Wi-Fi. Il inclut également des liens qui décrivent les différents paramètres pour chaque plateforme.

## <a name="supported-device-platforms"></a>Plateformes d’appareil prises en charge

Les profils Wi-Fi prennent en charge les plateformes suivantes :

- Android 4 et versions ultérieures
- Android Enterprise et Kiosk
- iOS 8.0 et versions ultérieures
- macOS X 10.11 et versions plus récentes
- Windows 10 et versions ultérieures, Windows 10 Mobile et Windows Holographic for Business

> [!NOTE]
> Pour les appareils exécutant Windows 8.1, vous pouvez importer une configuration Wi-Fi précédemment exportée à partir d’un autre appareil.

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Dans [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
2. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil approprié est **Profil WiFi pour toute l’entreprise**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :

      - **Android**
      - **Android Entreprise**
      - **iOS/iPadOS**
      - **MacOS**
      - **Windows 8.1 et versions ultérieures**
      - **Windows 10 et versions ultérieures**

    - **Type de profil** : Sélectionnez **Wi-Fi**.

      > [!TIP]
      >
      > - Pour les appareils **Android Enterprise** s’exécutant en tant qu’appareil dédié (plein écran), choisissez **Propriétaire de l’appareil uniquement** > **WiFi**.
      > - Pour **Windows 8.1 et versions ultérieures**, vous pouvez choisir **Importer Wi-Fi**. Cette option vous permet d’importer des paramètres Wi-Fi dans un fichier XML que vous avez préalablement exporté à partir d’un autre appareil.

3. Certains des paramètres Wi-Fi sont différents pour chaque plateforme. Pour afficher les paramètres pour une plateforme spécifique, choisissez votre plateforme :

    - [Android](wi-fi-settings-android.md)
    - [Android Entreprise](wi-fi-settings-android-enterprise.md), notamment des appareils dédiés
    - [iOS/iPadOS](wi-fi-settings-ios.md)
    - [MacOS](wi-fi-settings-macos.md)
    - [Windows 10 et versions ultérieures](wi-fi-settings-windows.md)
    - [Windows 8.1 et versions ultérieures](wi-fi-settings-import-windows-8-1.md), y compris Windows Holographic for Business

4. Quand vous avez terminé, sélectionnez **Créer un profil** > **Créer**.

Le profil est créé et s’affiche dans la liste des profils (**Configuration de l’appareil** > **Profils**).

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Vous devez à présent [attribuer ce profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).
