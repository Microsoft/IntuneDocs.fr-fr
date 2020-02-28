---
title: Utiliser des paramètres VPN pour Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez tous les paramètres pour créer des connexions VPN sur les appareils Android Entreprise dans Microsoft Intune. Entrez le nom de la connexion, l’adresse IP ou le nom de domaine complet du serveur VPN, choisissez la méthode d’authentification des utilisateurs, puis choisissez les types de connexion Citrix, SonicWall, Check Point Capsule et Pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81300651355e52f438ea2a314eeb1d0d48e3fcbc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510862"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Paramètres de l’appareil Android Entreprise pour configurer le VPN dans Intune

Cet article liste et décrit les différents paramètres de messagerie que vous pouvez contrôler sur les appareils Android. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour créer une connexion VPN, choisir le mode d’authentification du VPN, sélectionner un type de serveur VPN, et bien plus encore.

En tant qu’administrateur Intune, vous pouvez créer et affecter des paramètres VPN aux appareils Android Enterprise. 

Pour plus d’informations sur les profils VPN dans Intune, consultez [Profils VPN](vpn-settings-configure.md).

> [!NOTE]
> Pour configurer un VPN AlwaysOn, vous devez créer un profil VPN et un profil de [restriction d’appareil](device-restrictions-android-for-work.md#connectivity) en configurant le paramètre VPN AlwaysOn.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](vpn-settings-configure.md#create-a-device-profile), puis choisissez **Android Enterprise**.

## <a name="device-owner-only"></a>Propriétaire de l’appareil uniquement

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles. Par exemple, entrez `Contoso VPN`.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :
  
    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](../protect/certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer un nom d’utilisateur et un mot de passe.

- **Type de connexion** : Sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Cisco AnyConnect**
  - **Accès F5**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Profil professionnel uniquement

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles. Par exemple, entrez `Contoso VPN`.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :
  
    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](../protect/certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer un nom d’utilisateur et un mot de passe.

- **Type de connexion** : Sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Cisco AnyConnect**
  - **Accès F5**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils VPN pour les appareils [Android](vpn-settings-android.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), [Windows 10 et versions ultérieures](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md) et [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md).
