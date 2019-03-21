---
title: Configurer des paramètres Wi-Fi pour les appareils Android dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Créez ou ajoutez un profil de configuration d’appareil Wi-Fi pour Android. Consultez les différents paramètres, y compris l’ajout de certificats, le choix d’un type EAP et la sélection d’une méthode d’authentification dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bac109164a1e75ce14efc5d61201e829e572e502
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565976"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Ajouter des paramètres Wi-Fi dans Microsoft Intune pour les appareils exécutant Android dans Microsoft Intune

Vous pouvez créer un profil avec des paramètres Wi-Fi spécifiques, puis le déployer sur vos appareils Android. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau, l’ajout d’un certificat PKS ou SCEP et bien plus encore.

Ces paramètres Wi-Fi sont séparés en deux catégories : les paramètres de base et les paramètres d’entreprise.

Cet article décrit ces paramètres.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](device-profile-create.md).

## <a name="basic-profile"></a>Profil de base

- **Type de Wi-Fi** : choisissez **De base**.
- **SSID** : abréviation d’**identificateur SSID (Service Set Identifier)**. Ce paramètre correspond au nom réel du réseau sans fil auquel les appareils se connectent.
- **Se connecter automatiquement** : choisissez **Activer** pour vous connecter automatiquement à ce réseau lorsque celui-ci se trouve à votre portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.

## <a name="enterprise-profile"></a>Profil d’entreprise

- **Type de Wi-Fi** : choisissez **Entreprise**.
- **SSID** : abréviation d’**identificateur SSID (Service Set Identifier)**. Ce paramètre correspond au nom réel du réseau sans fil auquel les appareils se connectent.
- **Se connecter automatiquement** : choisissez **Activer** pour vous connecter automatiquement à ce réseau lorsque celui-ci se trouve à votre portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.
- **Type EAP** : choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes : 

  - **EAP-TLS** : entrez également :

    - **Approbation de serveur** - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** - **Certificat client pour l’authentification du client (certificat d’identité)**  : choisissez le profil de certificat client SCEP ou PKCS qui est également déployée sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

  - **EAP-TLS** : entrez également :

    - **Approbation de serveur** - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : invitez l’utilisateur d’un nom d’utilisateur et d’un mot de passe à authentifier la connexion. Entrez également :
        - **Méthode non EAP (identité interne)**  : choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.

          Vos options : **Mot de passe non chiffré (PAP)**, **Protocole CHAP (Challenge Handshake Authentication Protocol)**, **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

        Cliquez sur **OK** pour enregistrer vos modifications.

      - **Confidentialité de l’identité (identité externe)**  : entrez le texte envoyé en réponse à une requête d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

  - **PEAP** : entrez également :

    - **Approbation de serveur** - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : invitez l’utilisateur d’un nom d’utilisateur et d’un mot de passe à authentifier la connexion. Entrez également :
        - **Méthode non EAP pour l’authentification (identité interne)**  : choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.

          Vos options : **Aucune** ou **Microsoft CHAP version 2 (MS-CHAP v2)**

      - **Certificats** : choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

        Cliquez sur **OK** pour enregistrer vos modifications.

      - **Confidentialité de l’identité (identité externe)**  : entrez le texte envoyé en réponse à une requête d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et apparaît dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Ensuite, [affectez ce profil](device-profile-assign.md).

## <a name="more-resources"></a>Ressources complémentaires

- [Vue d’ensemble des paramètres Wi-Fi](wi-fi-settings-configure.md), y compris d’autres plateformes.

- À l’aide d’appareils Android Enterprise ou Android Kiosk ? Si ou, examinez les [paramètres Wi-Fi pour des appareils exécutant Android Entreprise et Android Kiosk](wi-fi-settings-android-enterprise.md).
