---
title: Configurer des paramètres Wi-Fi pour les appareils macOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Créez ou ajoutez un profil de configuration d’appareil Wi-Fi pour les appareils macOS. Consultez les différents paramètres, y compris l’ajout de certificats, le choix d’un type EAP et la sélection d’une méthode d’authentification dans Microsoft Intune.
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
ms.openlocfilehash: 8aa9fa9462b6278da566a3ff54264540144a38de
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512260"
---
# <a name="add-wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>Paramètres Wi-Fi pour les appareils macOS dans Microsoft Intune

Vous pouvez créer un profil avec des paramètres Wi-Fi spécifiques, puis le déployer sur vos appareils macOS. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau, l’ajout d’un certificat PKS ou SCEP et bien plus encore.

Ces paramètres Wi-Fi sont divisés en deux catégories : Paramètres de base et paramètres de niveau entreprise.

Cet article décrit ces paramètres.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](device-profile-create.md).

> [!NOTE]
> Ces paramètres sont disponibles pour tous les types d’inscription. Pour plus d’informations sur les types d’inscriptions, consultez [Inscription macOS](../enrollment/macos-enroll.md).

## <a name="basic-profiles"></a>Profils de base

- **Type de Wi-Fi** : Choisissez **De base**.
- **Nom du réseau** : Entrez un nom pour cette connexion Wi-Fi. Cette valeur est le nom que voient les utilisateurs quand ils parcourent la liste des connexions disponibles sur leur appareil.
- **SSID** : Abréviation de**Service Set Identifier**. Cette propriété est le nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le nom de réseau que vous avez configuré quand ils choisissent la connexion.
- **Se connecter automatiquement** : Choisissez **Activer** pour vous connecter automatiquement à ce réseau quand l’appareil est à portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.
- **Type de sécurité** : Sélectionnez le protocole de sécurité à utiliser pour s’authentifier sur le réseau Wi-Fi. Les options disponibles sont les suivantes :

  - **Ouvert (aucune authentification)**  : Utilisez cette option uniquement si le réseau n’est pas sécurisé.
  - **WPA/WPA2 - Personnel** : Entrez le mot de passe dans **Clé prépartagée**. Lorsque le réseau de votre organisation est configuré ou configuré, un mot de passe ou une clé réseau sont également configurés. Entrez cette clé de mot de passe ou de réseau pour la valeur PSK.
  - **WEP**

- **Paramètres du proxy** : Les options disponibles sont les suivantes :
  - **Aucune** : Aucun paramètre de proxy n’est configuré.
  - **Manuel** : Entrez l’**Adresse du serveur proxy** comme adresse IP et son **Numéro de port**.
  - **Automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez **l’URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui contient le fichier de configuration.

## <a name="enterprise-profiles"></a>Profils d’entreprise

- **Type de Wi-Fi** : Choisissez **Entreprise**.
- **SSID** : Abréviation de**Service Set Identifier**. Cette propriété est le nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le nom de réseau que vous avez configuré quand ils choisissent la connexion.
- **Se connecter automatiquement** : Choisissez **Activer** pour vous connecter automatiquement à ce réseau quand l’appareil est à portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.

- **Type EAP** : Choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes :

  - **EAP-FAST** : Entrez les **Paramètres des informations d’identification à accès protégé**. Cette option utilise les informations d'identification d'accès protégé pour créer un tunnel authentifié entre le client et le serveur d'authentification. Les options disponibles sont les suivantes :
    - **Ne pas utiliser (PAC)**
    - **Utiliser (Informations d’identification à accès protégé)**  : S’il existe un fichier PAC, utilisez-le.
    - **Utiliser et configurer les informations d’identification à accès protégé** : Créez et ajoutez le fichier PAC à vos appareils.
    - **Utiliser et configurer les informations d’identification à accès protégé anonymement** : Créez et ajoutez le fichier PAC à vos appareils sans authentification auprès du serveur.

  - **EAP-SIM**

  - **EAP-TLS** : Entrez également :

    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

    - **Authentification du client** - **Certificat client pour l’authentification du client (certificat d’identité)**  : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

  - **EAP-TTLS** : Entrez également :

    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : Invitez l’utilisateur à fournir un nom d’utilisateur et un mot de passe pour authentifier la connexion. Entrez également :
        - **Méthode non-EAP (identité interne)**  : Choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.

          Les options disponibles sont les suivantes : **Mot de passe non chiffré (PAP)** , **Protocole CHAP (Challenge Handshake Authentication Protocol)** , **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

  - **LEAP**

  - **PEAP** : Entrez également :

    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : Invitez l’utilisateur à fournir un nom d’utilisateur et un mot de passe pour authentifier la connexion. 

      - **Certificats** : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

- **Paramètres du proxy** : Les options disponibles sont les suivantes :
  - **Aucune** : Aucun paramètre de proxy n’est configuré.
  - **Manuel** : Entrez l’**Adresse du serveur proxy** comme adresse IP et son **Numéro de port**.
  - **Automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez **l’URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui contient le fichier de configuration.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Maintenant, [affectez ce profil](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

Configurez les paramètres Wi-Fi sur les appareils [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [iOS/iPadOS](wi-fi-settings-ios.md) et [Windows 10](wi-fi-settings-windows.md).
