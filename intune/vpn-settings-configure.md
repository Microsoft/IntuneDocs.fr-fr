---
title: Créer un profil d’appareil VPN dans Microsoft Intune - Azure | Microsoft Docs
description: Pour les appareils iOS, affichez les types de connexion VPN (réseau privé virtuel), créez un profil d’appareil VPN dans le portail Azure et consultez vos options pour sécuriser le profil VPN avec des certificats, ou un nom d’utilisateur et un mot de passe, dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0588d3e01994092ca48a8a3bb4844883f7a5b100
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57235342"
---
# <a name="create-vpn-profiles-in-intune"></a>Créer des profils VPN dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès distant sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec le serveur VPN. Utilisez les **profils VPN** dans Microsoft Intune pour affecter des paramètres VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter au réseau facilement et en toute sécurité.

Par exemple, supposons que vous voulez approvisionner tous les appareils iOS en fonction des paramètres nécessaires pour se connecter à un partage de fichiers sur le réseau d’entreprise. Vous créez un profil VPN contenant les paramètres de connexion au réseau d’entreprise. Vous affectez ensuite ce profil à tous les utilisateurs disposant d’appareils iOS. Les utilisateurs voient la connexion VPN dans la liste des réseaux disponibles et peuvent se connecter avec un minimum d’effort.

Vous pouvez utiliser des stratégies de configuration personnalisées Intune afin de créer des profils VPN pour les plateformes suivantes :

* Android 4 et versions ultérieures
* Appareils inscrits qui exécutent Windows 8.1 et versions ultérieures
* Windows Phone 8.1 et versions ultérieures
* Appareils inscrits qui exécutent Windows 10 Desktop
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>Types de connexions VPN

Vous pouvez créer des profils VPN à l’aide des types de connexions suivants :

|Type de connexion|Android<br>Profils professionnels Android|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Automatique|Non|Non|Non|Non|Non|Oui|
|Check Point Capsule VPN|Oui|Oui|Oui|Oui|Oui|Oui|
|Cisco AnyConnect|Oui|Oui|Oui|Non|Non|Non|
|SonicWall Mobile Connect|Oui|Oui|Oui|Oui|Oui|Oui|
|Client F5 Microsoft Edge|Oui|Oui|Oui|Oui|Oui|Oui|
|Palo Alto Networks GlobalProtect|Non|Oui|Non|Non|Non|Oui|
|Pulse Secure|Oui|Oui|Oui|Oui|Oui|Oui|
|Cisco (IPSec)|Non|Oui|Non|Non|Non|Non|
|Citrix|Oui (Android uniquement)|Oui|Non|Non|Non|Oui|
|IKEv2|Non|Non|Non|Non|Non|Oui|
|L2TP|Non|Non|Non|Non|Non|Oui|
|PPTP|Non|Non|Non|Non|Non|Oui|
|Zscaler|Non|Oui|Non|Non|Non|Non|
|VPN personnalisé|Non|Oui|Oui|Non|Non|Non|

> [!IMPORTANT]
> Avant de pouvoir utiliser les profils VPN affectés à un appareil, vous devez installer l’application VPN applicable pour le profil. Vous pouvez utiliser les informations de l’article [Qu’est-ce que la gestion des applications dans Microsoft Intune ?](app-management.md) pour vous aider à affecter l’application avec Intune.  

Découvrez comment créer des profils VPN personnalisés à l’aide des paramètres d’URI dans [Créer un profil avec des paramètres personnalisés](custom-settings-configure.md).

## <a name="create-a-device-profile-containing-vpn-settings"></a>Créer un profil d’appareil contenant des paramètres VPN

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
4. Entrez un **Nom** et une **Description** pour le profil VPN.
5. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres VPN. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres VPN :
   - **Android**
   - **Android Entreprise**
   - **iOS**
   - **MacOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 et versions ultérieures**
   - **Windows 10 et versions ultérieures**
6. Dans la liste déroulante **Type de profil**, choisissez **VPN**.
7. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Accédez à l’une des rubriques suivantes pour obtenir les paramètres détaillés pour chaque plateforme :
   - [Paramètres d’Android et de profil professionnel Android](vpn-settings-android.md)
   - [Paramètres iOS](vpn-settings-ios.md)
   - [Paramètres macOS](vpn-settings-macos.md)
   - [Paramètres Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
   - [Paramètres Windows 8.1](vpn-settings-windows-8-1.md)
   - [Paramètres Windows 10](vpn-settings-windows-10.md) (y compris Windows Holographic for Business)
8. Une fois que vous avez fini, il ne vous reste plus qu’à **Créer** votre profil

Le profil est créé et apparaît dans la liste des profils. Pour affecter ce profil à des groupes, consultez [Affecter des profils d’appareil](device-profile-assign.md).

## <a name="methods-of-securing-vpn-profiles"></a>Méthodes de sécurisation des profils VPN

Les profils VPN peuvent utiliser différents types de connexion et protocole de fabricants différents. Ces connexions sont généralement sécurisées à l’aide de l’une des deux méthodes suivantes.

### <a name="certificates"></a>Certificats

Quand vous créez le profil VPN, vous choisissez un profil de certificat SCEP ou PKCS que vous avez créé précédemment dans Intune. Ce profil est connu comme étant le certificat d’identité. Il est utilisé dans le cadre de l’authentification auprès d’un profil de certificat approuvé (ou *certificat racine*), que vous créez pour permettre à l’appareil de l’utilisateur de se connecter. Le certificat approuvé est affecté à l’ordinateur qui authentifie la connexion VPN, en règle générale le serveur VPN.

Pour plus d’informations sur la création et l’utilisation des profils de certificat dans Intune, consultez [Guide pratique pour configurer des certificats avec Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Nom d'utilisateur et mot de passe

L’utilisateur s’authentifie auprès du serveur VPN en fournissant un nom d’utilisateur et un mot de passe.
