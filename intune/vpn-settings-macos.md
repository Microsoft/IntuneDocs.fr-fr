---
title: Paramètres VPN Microsoft Intune pour les appareils Mac OS
titlesuffix: ''
description: Découvrez les paramètres Intune que vous pouvez utiliser pour configurer des connexions VPN sur les appareils macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5bc1ed991109ff32d03ae9a2e1da33adb62e6a4c
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565262"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>Configurer les paramètres VPN dans Microsoft Intune pour les appareils exécutant macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant macOS.

Selon les paramètres que vous choisissez, toutes les valeurs de la liste suivante ne sont pas nécessairement configurables.

## <a name="base-vpn-settings"></a>Paramètres VPN de base

**Nom de connexion** : saisissez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Adresse IP ou nom de domaine complet** : fournissez l'adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
- **Méthode d’authentification** : choisissez la façon dont les appareils s’authentifient auprès du serveur VPN à partir de :
    - **Certificats** : sous **Certificat d’authentification**, choisissez le profil de certificat SCEP ou PKCS que vous avez créé précédemment pour authentifier la connexion. Pour plus d’informations sur les profils de certificat, consultez [Guide pratique pour configurer des certificats](certificates-configure.md).
    - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent fournir un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.
- **Type de connexion** : sélectionnez le type de connexion VPN à partir de la liste de fournisseurs suivante :
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **Client F5 Edge**
    - **Pulse Secure**
    - **VPN personnalisé**
- **Tunneling fractionné** - **Activez** ou **désactivez** cette option qui permet aux appareils de choisir la connexion à utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder aux fichiers de travail, mais utilise le réseau standard de l’hôtel pour la navigation web ordinaire.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Paramètres VPN personnalisés

Si vous avez sélectionné **VPN personnalisé**, configurez ces paramètres supplémentaires :

- **Identificateur VPN** : il s’agit d’un identificateur pour l’application VPN que vous utilisez, et qui est fourni par votre fournisseur VPN.
- **Entrez les paires clé-valeur pour les attributs du VPN personnalisé** Ajoutez ou importez des **Clés** et **Valeurs** pour personnaliser votre connexion VPN. Là encore, ces valeurs sont généralement fournies par votre fournisseur de VPN.


## <a name="proxy-settings"></a>Paramètres du proxy

- **Script de configuration automatique** : utilisez un fichier de configuration pour configurer le serveur proxy. Entrez l’**URL du serveur Proxy** qui contient le fichier de configuration. Par exemple, entrez `http://proxy.contoso.com`.
- **Adresse** : saisissez l’adresse du serveur proxy (comme une adresse IP).
- **Numéro de port** : saisissez le numéro de port associé au serveur proxy.
