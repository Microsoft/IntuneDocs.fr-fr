---
title: Ajouter des paramètres VPN aux appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Pour les appareils Android, Android Entreprise, iOS, macOS et Windows, utilisez les paramètres intégrés pour créer des connexions de réseau privé virtuel (VPN) dans Microsoft Intune.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9fab50e0aefd926b4dc7a2b3559576642d5d6b79
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059305"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Créer des profils VPN pour se connecter à des serveurs VPN dans Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès distant sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec le serveur VPN. Les **profils VPN** dans Microsoft Intune attribuent des paramètres VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter à votre réseau d’entreprise facilement et en toute sécurité.

Par exemple, supposons que vous souhaitiez configurer tous les appareils iOS en fonction des paramètres nécessaires pour vous connecter à un partage de fichiers sur le réseau de l’entreprise. Vous créez un profil VPN qui comprend ces paramètres. Vous affectez ensuite ce profil à tous les utilisateurs disposant d’appareils iOS. Les utilisateurs voient la connexion VPN dans la liste des réseaux disponibles et peuvent se connecter avec un minimum d’effort.

> [!NOTE]
> Vous pouvez utiliser des [stratégies de configuration personnalisées Intune](custom-settings-configure.md) afin de créer des profils VPN pour les plateformes suivantes :
>
> * Android 4 et versions ultérieures
> * Appareils inscrits qui exécutent Windows 8.1 et versions ultérieures
> * Windows Phone 8.1 et versions ultérieures
> * Appareils inscrits qui exécutent Windows 10 Desktop
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>Types de connexions VPN

Vous pouvez créer des profils VPN à l’aide des types de connexions suivants :

|Type de connexion|Plate-forme|
|-|-|
|Automatique|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Profils professionnels Android Entreprise<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Profils professionnels Android Entreprise<br/>- Propriétaire d’appareil Android Entreprise (complètement managé)<br/>- iOS<br/>- macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|- Android<br/>- Profils professionnels Android Entreprise : Utilisez la [stratégie de configuration d’applications](../apps/app-configuration-policies-use-android.md)<br/>- Propriétaire d’appareil Android Entreprise (complètement managé) : Utilisez la [stratégie de configuration d’applications](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|VPN personnalisé|- iOS<br/>- macOS|
|Accès F5|- Android<br/>- Profils professionnels Android Entreprise<br/>- Propriétaire d’appareil Android Entreprise (complètement managé)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Profils professionnels Android Entreprise : Utilisez la [stratégie de configuration d’applications](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Profils professionnels Android Entreprise<br/>- Propriétaire d’appareil Android Entreprise (complètement managé)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Profils professionnels Android Entreprise<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Profils professionnels Android Entreprise : Utilisez la [stratégie de configuration d’applications](../apps/app-configuration-policies-use-android.md)<br/>- iOS|

> [!IMPORTANT]
> Avant de pouvoir utiliser les profils VPN affectés à un appareil, vous devez installer l’application VPN applicable pour le profil. Vous pouvez utiliser les informations de l’article [Qu’est-ce que la gestion des applications dans Microsoft Intune ?](../apps/app-management.md) pour vous aider à affecter l’application avec Intune.  

Découvrez comment créer des profils VPN personnalisés à l’aide des paramètres d’URI dans [Créer un profil avec des paramètres personnalisés](custom-settings-configure.md).

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil approprié est **Profil VPN pour toute l’entreprise**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :

      - **Android**
      - **Android Entreprise** > **Propriétaire d’appareil uniquement**
      - **Android Entreprise** > **Profil professionnel uniquement**
      - **iOS/iPadOS**
      - **MacOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 et versions ultérieures**
      - **Windows 10 et versions ultérieures**

    - **Type de profil** : sélectionnez **VPN**.

4. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Consultez l’un des articles suivants pour obtenir les paramètres détaillés pour chaque plateforme :

    - [Paramètres Android](vpn-settings-android.md)
    - [Paramètres Android Entreprise](vpn-settings-android-enterprise.md)
    - [Paramètres iOS/iPadOS](vpn-settings-ios.md)
    - [Paramètres macOS](vpn-settings-macos.md)
    - [Paramètres Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Paramètres Windows 8.1](vpn-settings-windows-8-1.md)
    - [Paramètres Windows 10](vpn-settings-windows-10.md) (y compris Windows Holographic for Business)

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste des profils. Pour affecter ce profil à des groupes, consultez [Affecter des profils d’appareil](device-profile-assign.md).

## <a name="secure-your-vpn-profiles"></a>Sécuriser vos profils VPN

Les profils VPN peuvent utiliser différents types de connexion et protocole de fabricants différents. Ces connexions sont généralement sécurisées à l’aide des méthodes suivantes.

### <a name="certificates"></a>Certificats

Quand vous créez le profil VPN, vous choisissez un profil de certificat SCEP ou PKCS que vous avez créé précédemment dans Intune. Ce profil est connu comme étant le certificat d’identité. Il est utilisé dans le cadre de l’authentification auprès d’un profil de certificat approuvé (ou *certificat racine*), que vous créez pour permettre à l’appareil de l’utilisateur de se connecter. Le certificat approuvé est affecté à l’ordinateur qui authentifie la connexion VPN, en règle générale le serveur VPN.

Pour plus d’informations sur la création et l’utilisation des profils de certificat dans Intune, consultez [Guide pratique pour configurer des certificats avec Microsoft Intune](../protect/certificates-configure.md).

### <a name="user-name-and-password"></a>Nom d'utilisateur et mot de passe

L’utilisateur s’authentifie auprès du serveur VPN en fournissant un nom d’utilisateur et un mot de passe.

## <a name="next-steps"></a>Étapes suivantes

Une fois le profil créé, il ne fait rien pour le moment. L’étape suivante consiste à [attribuer le profil](device-profile-assign.md) à certains appareils.

Vous pouvez également créer et utiliser des réseaux VPN par application sur les appareils [Android](android-pulse-secure-per-app-vpn.md) et [iOS](vpn-setting-configure-per-app.md).
