---
title: Paramètres Wi-Fi pour les appareils Android Enterprise et les bornes – Microsoft Intune | Microsoft Docs
description: Créez ou ajoutez un profil de configuration d’appareil Wi-Fi pour Android Enterprise et Android Kiosk. Consultez les différents paramètres, y compris l’ajout de certificats, le choix d’un type EAP et la sélection d’une méthode d’authentification dans Microsoft Intune. Pour les appareils de kiosques, entrez également entrer la clé prépartagée de votre réseau.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ea72cda4cb72af9028c52078e2215619bb2bef3c
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831477"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Configurer des paramètres Wi-Fi pour des appareils exécutant Android Entreprise et Android Kiosk dans Microsoft Intune

Vous pouvez créer un profil avec des paramètres Wi-Fi spécifiques, puis le déployer sur vos appareils Android Entreprise et Android Kiosk. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau à l’aide d’une clé prépartagée.

Cet article décrit ces paramètres. Pour plus d’informations sur la fonctionnalité Wi-Fi dans Microsoft Intune, voir [Utiliser le Wi-Fi sur des appareils](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only---kiosk"></a>Propriétaire de l’appareil uniquement - kiosque

Sélectionnez cette option si vous utilisez un appareil Android Entreprise comme kiosque.

- **Nom du réseau** : Entrez un nom pour cette connexion Wi-Fi. Cette valeur est le nom que voient les utilisateurs quand ils parcourent la liste des connexions disponibles sur leur appareil.
- **SSID** : Abréviation de**Service Set Identifier**. Ce paramètre correspond au nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le **nom de réseau** que vous avez configuré quand ils choisissent la connexion.
- **Se connecter automatiquement** : Choisissez **Activer** pour vous connecter automatiquement à ce réseau quand l’appareil est à portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.
- **Type de Wi-Fi** : Sélectionnez le protocole de sécurité à utiliser pour s’authentifier sur le réseau Wi-Fi. Les options disponibles sont les suivantes :

  - **Ouvert (aucune authentification)**  : Utilisez cette option uniquement si le réseau n’est pas sécurisé.
  - **Clé WEP prépartagée** : Entrez le mot de passe dans **Clé prépartagée**. Lorsque le réseau de votre organisation est configuré ou configuré, un mot de passe ou une clé réseau sont également configurés. Entrez cette clé de mot de passe ou de réseau pour la valeur PSK.
  - **Clé WPA prépartagée** : Entrez le mot de passe dans **Clé prépartagée**. Lorsque le réseau de votre organisation est configuré ou configuré, un mot de passe ou une clé réseau sont également configurés. Entrez cette clé de mot de passe ou de réseau pour la valeur PSK.

Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="work-profile-only"></a>Profil professionnel uniquement

### <a name="basic-settings"></a>Paramètres de base

- **Type de Wi-Fi** : Choisissez **De base**.
- **SSID** : Abréviation de**Service Set Identifier**. Ce paramètre correspond au nom réel du réseau sans fil auquel les appareils se connectent.
- **Se connecter automatiquement** : Choisissez **Activer** pour vous connecter automatiquement à ce réseau quand l’appareil est à portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.

## <a name="enterprise-profile"></a>Profil d’entreprise

- **Type de Wi-Fi** : Choisissez **Entreprise**.
- **SSID** : Abréviation de**Service Set Identifier**. Ce paramètre correspond au nom réel du réseau sans fil auquel les appareils se connectent.
- **Se connecter automatiquement** : Choisissez **Activer** pour vous connecter automatiquement à ce réseau quand l’appareil est à portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.
- **Type EAP** : Choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes : 

  - **EAP-TLS** : Entrez également :

    - **Approbation du serveur** - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Lorsque le client se connecte au réseau, ce certificat est présenté au serveur pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** - **Certificat client pour l’authentification du client (certificat d’identité)**  : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

  - **EAP-TTLS** : Entrez également :

    - **Approbation du serveur** - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Lorsque le client se connecte au réseau, ce certificat est présenté au serveur pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : Invitez l’utilisateur à fournir un nom d’utilisateur et un mot de passe pour authentifier la connexion. Entrez également :
        - **Méthode non-EAP (identité interne)**  : Choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.

          Les options disponibles sont les suivantes : **Mot de passe non chiffré (PAP)**, **Protocole CHAP (Challenge Handshake Authentication Protocol)**, **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

        Cliquez sur **OK** pour enregistrer vos modifications.

      - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

  - **PEAP** : Entrez également :

    - **Approbation du serveur** - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Lorsque le client se connecte au réseau, ce certificat est présenté au serveur pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : Invitez l’utilisateur à fournir un nom d’utilisateur et un mot de passe pour authentifier la connexion. Entrez également :
        - **Méthode non-EAP pour l’authentification (identité interne)**  : Choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.

          Les options disponibles sont les suivantes : **Aucune** ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

        Cliquez sur **OK** pour enregistrer vos modifications.

      - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et apparaît dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Maintenant, [affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

Vous pouvez également créer des profils Wi-Fi pour des appareils [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md) et [Windows 8.1](wi-fi-settings-import-windows-8-1.md).