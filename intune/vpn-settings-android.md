---
title: Paramètres VPN Microsoft Intune pour les appareils exécutant Android
titlesuffix: ''
description: Découvrir les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant Android
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f52c43f8918589c1b66034ad68908f4d5ddba6d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905119"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Configurer les paramètres VPN dans Microsoft Intune pour les appareils exécutant Android 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant Android.


Vous pouvez configurer les paramètres VPN pour les plateformes suivantes :

- [Android](#android-vpn-settings)
- [Appareils avec profil professionnel Android](#android-for-work-vpn-settings)

Selon les paramètres que vous choisissez, toutes les valeurs suivantes ne sont pas nécessairement configurables.

## <a name="android-vpn-settings"></a>Paramètres VPN Android
- **Nom de connexion** : saisissez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Adresse IP ou nom de domaine complet** : fournissez l'adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
    - **Méthode d’authentification** : choisissez la façon dont les appareils s’authentifient auprès du serveur VPN à partir de :
        - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS que vous avez créé précédemment pour authentifier la connexion. Pour plus d’informations sur les profils de certificat, consultez [Guide pratique pour configurer des certificats](certificates-configure.md).
        - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent fournir un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.
- **Type de connexion** : sélectionnez le type de connexion VPN à partir de la liste de fournisseurs suivante :
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **Client F5 Edge**
    - **Pulse Secure**
    - **Citrix**

- **Empreinte digitale** (VPN Check Point Capsule uniquement) : spécifiez une chaîne (par exemple « Code d’empreinte digitale Contoso ») qui est utilisée pour vérifier que le serveur VPN est digne de confiance. Une empreinte digitale peut être envoyée au client pour que celui-ci sache qu’il peut approuver n’importe quel serveur présentant cette même empreinte lors de la connexion. Si l’appareil n’a pas encore l’empreinte digitale, il invite l’utilisateur à approuver le serveur VPN auquel il se connecte en affichant l’empreinte digitale (l’utilisateur vérifie l’empreinte manuellement et choisit Approuver pour se connecter).
- **Entrer les paires clé / valeur pour les attributs de Citrix VPN** (Citrix uniquement) : entrez les paires de clé / valeur fournies par Citrix pour configurer les propriétés de la connexion VPN.

## <a name="android-work-profile-device-vpn-settings"></a>Paramètres VPN des appareils avec profil professionnel Android

- **Nom de connexion** : saisissez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Adresse IP ou nom de domaine complet** : fournissez l'adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
    - **Méthode d’authentification** : choisissez la façon dont les appareils s’authentifient auprès du serveur VPN à partir de :
        - **Certificats** : sélectionnez un profil de certificat SCEP ou PKCS que vous avez créé précédemment pour authentifier la connexion. Pour plus d’informations sur les profils de certificat, consultez [Guide pratique pour configurer des certificats](certificates-configure.md).
        - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent fournir un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.
- **Type de connexion** : sélectionnez le type de connexion VPN à partir de la liste de fournisseurs suivante :
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **Client F5 Edge**
    - **Pulse Secure**

