---
title: Créer un profil Wi-Fi pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Suivez les étapes pour créer un profil de configuration d’appareil dans Microsoft Intune. Créez des profils pour Android, Android Entreprise, Android Kiosk, iOS, macOS, Windows 10 et versions ultérieures et Windows Holographic for Business. Utilisez ces profils pour créer une connexion Wi-Fi afin d’utiliser des certificats, choisissez un type EAP, sélectionnez une méthode d’authentification, activez un proxy et bien plus encore.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16273910220dae238e15910af0557dd8b73646b9
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425255"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Ajoutez et utilisez des paramètres Wi-Fi sur vos appareils dans Microsoft Intune

Utilisez les profils Wi-Fi de Microsoft Intune pour affecter les paramètres de réseau sans fil aux utilisateurs et appareils de votre organisation. Quand vous attribuez un profil Wi-Fi, vos utilisateurs peuvent accéder au réseau Wi-Fi de votre organisation sans le configurer eux-mêmes.

Par exemple, vous installez un nouveau réseau Wi-Fi nommé Contoso Wi-Fi. Ensuite, vous souhaitez configurer tous les appareils iOS pour vous connecter à ce réseau. Voici le processus :

1. Créez un profil Wi-Fi incluant les paramètres pour se connecter au réseau sans fil Contoso Wi-Fi.
2. Affectez le profil à un groupe contenant tous les utilisateurs d’appareils iOS.
3. Les utilisateurs recherchent le nouveau réseau Wi-Fi Contoso dans la liste des réseaux sans fil sur leur appareil. Ils peuvent alors se connecter au réseau, à l’aide de la méthode d’authentification de votre choix.

Utilisez les étapes décrites dans cet article pour créer un profil Wi-Fi. Ensuite, passez en revue les rubriques sur les paramètres spécifiques à la plateforme et les détails.

## <a name="supported-device-platforms"></a>Plateformes d’appareil prises en charge

Les profils Wi-Fi prennent en charge les plateformes suivantes :

- Android 4 et versions ultérieures
- Android Enterprise et Kiosk
- iOS 8.0 et versions ultérieures
- macOS (Mac OS X 10.11 et ultérieur)
- Windows 10 et versions ultérieures, Windows 10 Mobile et Windows Holographic for Business

> [!NOTE]
> Pour les appareils exécutant Windows 8.1, vous pouvez importer une configuration Wi-Fi précédemment exportée à partir d’un autre appareil.

## <a name="create-a-wi-fi-device-profile"></a>Créez un profil d’appareil Wi-Fi

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**. 
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez un **Nom** et une **Description** pour le profil Wi-Fi.
4. Dans la liste déroulante de la **Plateforme**, sélectionnez la plateforme de l’appareil auquel appliquer les paramètres Wi-Fi. Les options disponibles sont les suivantes :

    - **Android**
    - **Android Entreprise**
    - **iOS**
    - **MacOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 et versions ultérieures**
    - **Windows 10 et versions ultérieures**

5. Dans **Type de profil**, choisissez **Wi-Fi**.

    - Pour **Android Enterprise** les appareils s’exécutant en tant que kiosque, vous pouvez choisir **propriétaire de l’appareil uniquement** > **Wi-Fi**.
    - Pour **Windows 8.1 et versions ultérieures**, vous pouvez choisir **Importer Wi-Fi**. Cette option vous permet d’importer des paramètres Wi-Fi dans un fichier XML que vous avez préalablement exporté à partir d’un autre appareil.

6. Certains des paramètres Wi-Fi sont différents pour chaque plateforme. Pour afficher les paramètres pour une plateforme spécifique, choisissez :

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise et Kiosk](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [MacOS](wi-fi-settings-macos.md)
    - [Windows 10 et versions ultérieures](wi-fi-settings-windows.md)
    - [Windows 8.1 et versions ultérieures](wi-fi-settings-import-windows-8-1.md), y compris Windows Holographic for Business

    La plupart des plateformes ont des paramètres **De base** et **D’entreprise**. **De base** inclut des fonctionnalités telles que le nom de réseau et le SSID. **Entreprise** vous permet de fournir des informations supplémentaires comme le protocole d’authentification extensible (EAP).

7. Lorsque vous avez fini d’ajouter vos paramètres Wi-Fi, sélectionnez **Créer un profil** > **Créer** pour ajouter le profil de configuration. Le profil est créé et s’affiche dans la liste des profils (**Configuration de l’appareil** > **Profils**).

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Ensuite, [affectez ce profil](device-profile-assign.md).
