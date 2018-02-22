---
title: "Guide pratique pour configurer des paramètres Wi-Fi Intune"
titleSuffix: Azure portal
description: "Apprenez à utiliser Intune pour configurer des connexions Wi-Fi sur les appareils que vous gérez."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e03df2525b413ca33f81836292a05dac11bb8349
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Guide pratique pour configurer des paramètres Wi-Fi dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilisez les profils Wi-Fi de Microsoft Intune pour affecter les paramètres de réseau sans fil aux utilisateurs et appareils de votre organisation. Quand vous attribuez un profil Wi-Fi, vos utilisateurs ont accès à votre réseau Wi-Fi d’entreprise sans avoir à le configurer eux-mêmes.

Par exemple, vous installez un nouveau réseau Wi-Fi nommé Contoso Wi-Fi et souhaitez configurer tous les appareils iOS pour qu’ils se connectent à ce réseau. Voici le processus :

1. Créez un profil Wi-Fi contenant les paramètres nécessaires pour se connecter au réseau sans fil Contoso Wi-Fi.
2. Affectez le profil à un groupe contenant tous les utilisateurs d’appareils iOS.
3. Les utilisateurs recherchent le nouveau réseau Wi-Fi Contoso dans la liste des réseaux sans fil sur leur appareil et peuvent facilement se connecter à celui-ci.

## <a name="supported-device-platforms"></a>Plateformes d’appareil prises en charge

Les profils Wi-Fi prennent en charge les plateformes suivantes :

- Android 4 et versions ultérieures
- Android for Work
- iOS 8.0 et versions ultérieures
- Mac OS (Mac OS X 10.9 et versions ultérieures)

Pour les appareils exécutant Windows 8.1, Windows 10, Windows 10 Mobile et Windows Holographic for Business, vous pouvez importer une configuration Wi-Fi précédemment exportée à partir d’un autre appareil.

Utilisez les informations de cette rubrique pour apprendre les notions de base sur la configuration d’un profil Wi-Fi et lisez autres rubriques pour chaque plateforme pour en savoir plus sur les caractéristiques des appareils.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Création d’un profil d'appareil contenant des paramètres Wi-Fi

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de Services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le panneau **Configuration de l’appareil**, choisissez **Gérer** > **Profils**.
3. Dans le panneau des profils, sélectionnez **Créer un profil**.
4. Dans le panneau **Créer un profil** , saisissez un **Nom** et une **Description** pour votre profil Wi-Fi.
5. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres Wi-Fi. Actuellement, vous pouvez choisir une des plateformes suivantes pour les paramètres Wi-Fi :
    - **Android**
    - **Android for Work**
    - **iOS**
    - **MacOS**
    - **Windows 8.1 et versions ultérieures (importer un profil)**

   > [!IMPORTANT]
   > Si vous créez un profil pour les appareils exécutant Windows 10, y compris Windows Holographic for Business, vous devez choisir la plateforme **Windows 8.1 et versions ultérieures**. La plateforme **Windows 10 et versions ultérieures** n’a pas de type de profil Wi-Fi. 

6. Pour les appareils Apple ou Android, dans la liste déroulante **Type de Wi-Fi**, choisissez **De base** ou **Entreprise**. Vous pouvez utiliser **De base** pour fournir des fonctionnalités de base comme le nom et le SSID du réseau. **Entreprise** vous permet de fournir des informations supplémentaires comme le protocole d’authentification extensible (EAP) si votre réseau Wi-Fi l’utilise. 

   Le profil **Importation Wi-Fi** (pour Windows 8.1 et versions ultérieures) vous permet d’importer des paramètres Wi-Fi dans un fichier XML que vous avez exporté à partir d’un autre appareil.
1. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Accédez à l’une des rubriques suivantes pour obtenir les paramètres détaillés pour chaque plateforme :
    - [Paramètres Android et Android for Work](wi-fi-settings-android.md)
    - [Paramètres iOS](wi-fi-settings-ios.md)
    - [Paramètres macOS](wi-fi-settings-macos.md)
    - [Paramètres Windows 8.1 et version ultérieures](wi-fi-settings-import-windows-8-1.md) (y compris Windows Holographic for Business)
1. Lorsque vous avez terminé, revenez au panneau **Créer un profil** et appuyez sur **Créer**.

Le profil est créé et s’affiche dans le panneau de la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Si vous souhaitez continuer et attribuer ce profil à des groupes, consultez [Guide pratique pour l’attribution de profils d’appareils](device-profile-assign.md).
