---
title: Utiliser des paramètres VPN pour les appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez tous les paramètres pour créer des connexions VPN sur les appareils Android dans Microsoft Intune. Entrez le nom de la connexion, l’adresse IP ou le nom de domaine complet du serveur VPN, choisissez la méthode d’authentification des utilisateurs, puis choisissez les types de connexion Citrix, SonicWall, Check Point Capsule et Pulse Secure.
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
ms.openlocfilehash: 3f82cc74aa2e351ee63ffba2629e9ddddb57fc76
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512515"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Paramètres de l’appareil Android pour configurer le VPN dans Intune

Cet article liste et décrit les différents paramètres de connexion VPN que vous pouvez contrôler sur les appareils Android. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour créer une connexion VPN, choisir le mode d’authentification du VPN, sélectionner un type de serveur VPN, et bien plus encore.

En tant qu’administrateur Intune, vous pouvez créer et assigner ces paramètres VPN aux appareils Android. 

Pour plus d’informations sur les profils VPN dans Intune, consultez [Profils VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](vpn-settings-configure.md#create-a-device-profile), puis choisissez **Android**.

## <a name="base-vpn"></a>VPN de base

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles. Par exemple, entrez `Contoso VPN`.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :

    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](../protect/certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer un nom d’utilisateur et un mot de passe.

- **Type de connexion** : Sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **Accès F5**
  - **Pulse Secure**
  - **Citrix SSO**

- **Empreinte numérique** (VPN Check Point Capsule uniquement) : entrez une chaîne, par exemple **Code d’empreinte numérique Contoso**, pour vérifier que le serveur VPN est digne de confiance. Une empreinte digitale est envoyée au client pour que celui-ci sache qu’il peut approuver n’importe quel serveur ayant cette même empreinte. Si l’appareil n’a pas l’empreinte digitale, il invite l’utilisateur à approuver le serveur VPN tout en affichant l’empreinte digitale. L’utilisateur vérifie manuellement l’empreinte digitale et choisit de faire confiance pour se connecter.
- **Entrer les paires clé/valeur des attributs du VPN Citrix** (Citrix uniquement) : entrez les paires clé/valeur fournies par Citrix. Ces valeurs configurent les propriétés de la connexion VPN. 

  Vous pouvez également **importer** un fichier de valeurs séparées par des virgules (.csv) contenant des paires clé/valeur. Veillez à examiner les propriétés **Mes données comprennent des en-têtes** et **Clé**.

  Une fois que vous avez ajouté vos paires clé/valeur, utilisez l'option **Exporter** pour sauvegarder vos données dans un fichier .csv.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils VPN pour les appareils [Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), [Windows 10 et versions ultérieures](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md) et [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md).
