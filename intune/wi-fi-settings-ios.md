---
title: Configurer des paramètres Wi-Fi pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Créez ou ajoutez un profil de configuration d’appareil Wi-Fi pour les appareils iOS. Consultez les différents paramètres, y compris l’ajout de certificats, le choix d’un type EAP et la sélection d’une méthode d’authentification dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6d84c64e93f986a86e90cd9b7b5341fd8ea97d12
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180202"
---
# <a name="add-wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Ajouter des paramètres Wi-Fi pour les appareils iOS dans Microsoft Intune

Vous pouvez créer un profil avec des paramètres Wi-Fi spécifiques, puis le déployer sur vos appareils iOS. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau, l’ajout d’un certificat PKS ou SCEP et bien plus encore.

Ces paramètres Wi-Fi sont séparés en deux catégories : les paramètres de base et les paramètres d’entreprise.

Cet article décrit ces paramètres.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](device-profile-create.md).

## <a name="basic-profiles"></a>Profils de base

- **Type de Wi-Fi** : choisissez **De base**.
- **Nom du réseau** : entrez un nom pour cette connexion Wi-Fi. Cette valeur est le nom que voient les utilisateurs quand ils parcourent la liste des connexions disponibles sur leur appareil.
- **SSID** : abréviation d’**identificateur SSID (Service Set Identifier)**. Cette propriété est le nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le nom de réseau que vous avez configuré quand ils choisissent la connexion.
- **Se connecter automatiquement** : choisissez **Activer** pour vous connecter automatiquement à ce réseau lorsque celui-ci se trouve à votre portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.
- **Type de sécurité** : sélectionnez le protocole de sécurité à utiliser pour s’authentifier sur le réseau Wi-Fi. Les options disponibles sont les suivantes :

  - **Ouvert (aucune authentification)** : utilisez cette option uniquement si le réseau n’est pas sécurisé.
  - **WPA/WPA2 - Personal** : entrez le mot de passe dans **Clé prépartagée**. Lorsque le réseau de votre organisation est configuré ou configuré, un mot de passe ou une clé réseau sont également configurés. Entrez cette clé de mot de passe ou de réseau pour la valeur PSK.
  - **WEP**

- **Paramètres de proxy** : vos options :
  - **Aucun** : aucun paramètre de proxy n’est configuré.
  - **Manuel** : saisissez l’**Adresse du serveur proxy** comme adresse IP et son **Numéro de port**.
  - **Automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez **l’URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui contient le fichier de configuration.

## <a name="enterprise-profiles"></a>Profils d’entreprise

- **Type de Wi-Fi** : choisissez **Entreprise**.
- **SSID** : abréviation d’**identificateur SSID (Service Set Identifier)**. Cette propriété est le nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le nom de réseau que vous avez configuré quand ils choisissent la connexion.
- **Se connecter automatiquement** : choisissez **Activer** pour vous connecter automatiquement à ce réseau lorsque celui-ci se trouve à votre portée. Choisissez **Désactiver** pour empêcher la connexion automatique des appareils.
- **Réseau masqué** : choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.

- **Type EAP** : choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes :

  - **EAP-FAST** : entrez les **Paramètres d’identification d’accès protégé (PAC)**. Cette option utilise les informations d'identification d'accès protégé pour créer un tunnel authentifié entre le client et le serveur d'authentification. Les options disponibles sont les suivantes :
    - **Ne pas utiliser (PAC)**
    - **Utiliser (PAC)**  : si un fichier PAC existe, utilisez-le.
    - **Utiliser et approvisionner PAC** : créez et ajoutez le fichier PAC sur vos appareils.
    - **Utiliser et configurer anonymement le fichier PAC** : créer et ajouter le fichier PAC sur vos appareils sans l’authentification auprès du serveur.

  - **EAP-SIM**

  - **EAP-TLS** : entrez également :

    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** - **Certificat client pour l’authentification du client (certificat d’identité)**  : choisissez le profil de certificat client SCEP ou PKCS qui est également déployée sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

  - **EAP-TLS** : entrez également :

    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : invitez l’utilisateur d’un nom d’utilisateur et d’un mot de passe à authentifier la connexion. Entrez également :
        - **Méthode non EAP (identité interne)**  : choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.

          Vos options : **Mot de passe non chiffré (PAP)**, **Protocole CHAP (Challenge Handshake Authentication Protocol)**, **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

        Cliquez sur **OK** pour enregistrer vos modifications.

      - **Confidentialité de l’identité (identité externe)**  : entrez le texte envoyé en réponse à une requête d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

  - **LEAP**

  - **PEAP** : entrez également :

    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : invitez l’utilisateur d’un nom d’utilisateur et d’un mot de passe à authentifier la connexion. 

      - **Certificats** : choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

        Cliquez sur **OK** pour enregistrer vos modifications.

      - **Confidentialité de l’identité (identité externe)**  : entrez le texte envoyé en réponse à une requête d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

- **Paramètres de proxy** : vos options :
  - **Aucun** : aucun paramètre de proxy n’est configuré.
  - **Manuel** : saisissez l’**Adresse du serveur proxy** comme adresse IP et son **Numéro de port**.
  - **Automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez **l’URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui contient le fichier de configuration.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et apparaît dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Ensuite, [affectez ce profil](device-profile-assign.md).

## <a name="more-resources"></a>Ressources complémentaires

[Vue d’ensemble des paramètres Wi-Fi](wi-fi-settings-configure.md), y compris d’autres plateformes disponibles.