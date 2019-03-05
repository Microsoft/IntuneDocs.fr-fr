---
title: Configurer des paramètres VPN pour les appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Lors de la création d’un profil de configuration VPN pour des appareils Android et Android for Work, entrez le nom de connexion, l’adresse IP ou le nom de domaine complet du serveur VPN, choisissez comment les utilisateurs s’authentifient auprès du serveur VPN, puis choisissez les types de connexion Citrix, SonicWall, Check Point Capsule, Pulse Secure et Microsoft Edge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aff0aad055aee08dfbf17622e3d9f9c3061165b8
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233965"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Configurer des paramètres VPN pour les appareils exécutant Android dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant Android.

Vous pouvez configurer les paramètres VPN pour les plateformes suivantes :

- [Android](#android-vpn-settings)
- [Android Entreprise](#android-enterprise-vpn-settings)

Selon les paramètres que vous choisissez, toutes les valeurs suivantes ne sont pas nécessairement configurables.

## <a name="android-vpn-settings"></a>Paramètres VPN Android

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :

    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer un nom d’utilisateur et un mot de passe.

- **Type de connexion** : Sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **Client F5 Edge**
  - **Pulse Secure**
  - **Citrix**

- **Empreinte numérique** (VPN Check Point Capsule uniquement) : entrez une chaîne, par exemple **Code d’empreinte numérique Contoso**, pour vérifier que le serveur VPN est digne de confiance. Une empreinte digitale peut être envoyée au client pour que celui-ci sache qu’il peut approuver n’importe quel serveur ayant cette même empreinte lors de la connexion. Si l’appareil n’a pas l’empreinte digitale, il invite l’utilisateur à approuver le serveur VPN tout en affichant l’empreinte digitale. L’utilisateur vérifie manuellement l’empreinte digitale et choisit confiance pour se connecter.
- **Entrer les paires clé/valeur des attributs du VPN Citrix** (Citrix uniquement) : entrez les paires clé/valeur fournies par Citrix. Ces valeurs configurent les propriétés de la connexion VPN.

## <a name="android-enterprise-vpn-settings"></a>Paramètres du VPN Android Enterprise

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil les connexions VPN disponibles.
- **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**.

  - **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN. Les options disponibles sont les suivantes :
  
    - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer des certificats](certificates-configure.md) répertorie les étapes permettant de créer un profil de certificat.
    - **Nom d’utilisateur et mot de passe** : lors de la connexion au serveur VPN, les utilisateurs finaux sont invités à entrer un nom d’utilisateur et un mot de passe.

- **Type de connexion** : Sélectionnez le type de connexion VPN. Les options disponibles sont les suivantes :

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **Accès F5**
  - **Pulse Secure**

## <a name="next-steps"></a>Étapes suivantes
[Profils VPN dans Intune](vpn-settings-configure.md)
