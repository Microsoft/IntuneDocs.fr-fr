---
title: "Guide pratique pour configurer des paramètres VPN Intune"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : Découvrez comment utiliser Intune pour configurer des connexions VPN sur les appareils que vous gérez."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: d44eec0cdfc2a7762a0f0ca62da4dacd0d083484
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017


---

# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Guide pratique pour configurer des paramètres VPN dans Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès distant sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec le serveur VPN. Utilisez les **profils VPN** dans Microsoft Intune pour affecter des paramètres VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter au réseau facilement et en toute sécurité.

Par exemple, supposons que vous voulez approvisionner tous les appareils iOS en fonction des paramètres nécessaires pour se connecter à un partage de fichiers sur le réseau d’entreprise. Vous créez un profil VPN contenant les paramètres nécessaires pour se connecter au réseau d’entreprise, puis vous attribuez ce profil à tous les utilisateurs qui ont des appareils iOS. Les utilisateurs voient la connexion VPN dans la liste des réseaux disponibles et peuvent se connecter avec un minimum d’effort.

## <a name="vpn-connection-types"></a>Types de connexions VPN

Vous pouvez créer des profils VPN à l’aide des types de connexions suivants :

||||||||
|-|-|-|-|-|-|-|
|Type de connexion|Android|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|Pulse Secure|Oui|Oui|Oui|Oui|Oui|Oui|
|Cisco (IPSec)|Non|Oui|Non|Non|Non|Non|
|Citrix|Oui|Oui|Non|Non|Non|Non|
|Client F5 Microsoft Edge|Oui|Oui|Oui|Oui|Oui|Oui|
|Dell SonicWALL Mobile Connect|Oui|Oui|Oui|Oui|Oui|Oui|
|Check Point Capsule VPN|Oui|Oui|Oui|Oui|Oui|Oui|
|Cisco AnyConnect|Oui|Oui|Oui|Non|Non|Non|
|Automatique|Non|Non|Non|Non|Non|Oui|
|IKEv2|Non|Non|Non|Non|Non|Oui|
|L2TP|Non|Non|Non|Non|Non|Oui|
|PPTP|Non|Non|Non|Non|Non|Oui|
|Personnalisé|Non|Oui|Oui|Non|Non|Non|


> [!IMPORTANT]
> Avant de pouvoir utiliser les profils VPN affectés à un appareil, vous devez installer l’application VPN applicable pour le profil. Vous pouvez utiliser les informations fournies dans la rubrique [Qu’est-ce que la gestion des applications dans Microsoft Intune ?](../manage-apps/what-is-app-management.md) pour vous aider à affecter l’application avec Intune.  

Découvrez comment créer des profils VPN personnalisés à l’aide des paramètres de l’URI dans [Créer des profils VPN personnalisés](create-custom-vpn-profiles.md).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Créer un profil d’appareil contenant des paramètres VPN

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de services** > **Autres** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le panneau **Configuration de l’appareil**, choisissez **Gérer** > **Profils**.
3. Dans le panneau des profils, sélectionnez **Créer un profil**.
4. Dans le panneau **Créer un profil**, entrez un **Nom** et une **Description** pour votre profil VPN.
5. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres VPN. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres VPN :
    - **Android**
    - **iOS**
    - **MacOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 et versions ultérieures**
    - **Windows 10 et versions ultérieures**
6. Dans la liste déroulante **Type de profil**, choisissez **VPN**.
7. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Accédez à l’une des rubriques suivantes pour obtenir les paramètres détaillés pour chaque plateforme :
    - [Paramètres Android](vpn-for-android.md)
    - [Paramètres iOS](vpn-for-ios.md)
    - [Paramètres macOS](vpn-for-macos.md)
    - [Paramètres Windows Phone 8.1](vpn-for-windows-phone-8-1.md)
    - [Paramètres Windows 8.1](vpn-for-windows-8-1.md)
    - [Paramètres Windows 10](vpn-for-windows-10.md)
8. Lorsque vous avez terminé, revenez au panneau **Créer un profil** et appuyez sur **Créer**.

Le profil est créé et s’affiche dans le panneau de la liste des profils.
Si vous souhaitez continuer et attribuer ce profil à des groupes, consultez [Guide pratique pour attribuer des profils d’appareils](how-to-assign-device-profiles.md).


## <a name="methods-of-securing-vpn-profiles"></a>Méthodes de sécurisation des profils VPN

Les profils VPN peuvent utiliser différents types de connexion et protocole de fabricants différents. Ces connexions sont généralement sécurisées à l’aide de l’une des deux méthodes suivantes.

### <a name="certificates"></a>Certificats

Quand vous créez le profil VPN, vous choisissez un profil de certificat SCEP ou PKCS que vous avez créé précédemment dans Intune. Il s’agit du certificat d’identité. Il est utilisé pour effectuer une authentification auprès d’un profil de certificat approuvé (ou *certificat racine*) que vous avez créé pour établir que l’utilisateur est autorisé à se connecter. Le certificat approuvé est affecté à l’ordinateur qui authentifie la connexion VPN, en règle générale le serveur VPN.

Pour plus d’informations sur la création et l’utilisation des profils de certificat dans Intune, consultez [Guide pratique pour configurer des certificats avec Microsoft Intune](how-to-configure-certificates.md).

### <a name="user-name-and-password"></a>Nom d'utilisateur et mot de passe

L’utilisateur s’authentifie auprès du serveur VPN en fournissant un nom d’utilisateur et un mot de passe.

