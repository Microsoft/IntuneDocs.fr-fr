---
title: Utiliser des paramètres VPN pour Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez tous les paramètres pour créer des connexions VPN sur les appareils Android Enterprise dans Microsoft Intune. Entrez le nom de la connexion, l’adresse IP ou le nom de domaine complet du serveur VPN, choisissez la méthode d’authentification des utilisateurs, puis choisissez Citrix, SonicWall, check point capsule et Pulse Secure Connection types.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9f52d3a7c40f27555a07682adf86b0339cef616
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72491933"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Paramètres d’appareil Android Enterprise pour configurer un VPN dans Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres de messagerie que vous pouvez contrôler sur les appareils Android. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour créer une connexion VPN, choisir la manière dont le VPN s’authentifie, sélectionner un type de serveur VPN, et bien plus encore.

En tant qu’administrateur Intune, vous pouvez créer et affecter des paramètres VPN aux appareils Android Enterprise. 

Pour en savoir plus sur les profils VPN dans Intune, consultez [profils VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](vpn-settings-configure.md#create-a-device-profile), puis choisissez **Android Enterprise**.

## <a name="device-owner-only"></a>Propriétaire de l’appareil uniquement

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles. Par exemple, entrez `Contoso VPN`.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez comment les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :
  
    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](../protect/certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer leur nom d’utilisateur et leur mot de passe.

- **Type de connexion** : sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Cisco AnyConnect**
  - **Accès F5**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Profil professionnel uniquement

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles. Par exemple, entrez `Contoso VPN`.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez comment les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :
  
    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](../protect/certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer leur nom d’utilisateur et leur mot de passe.

- **Type de connexion** : sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Cisco AnyConnect**
  - **Accès F5**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils VPN pour les appareils [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 et versions ultérieures](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)et [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) .
