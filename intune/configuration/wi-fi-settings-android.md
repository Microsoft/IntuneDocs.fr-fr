---
title: Configurer des paramètres Wi-Fi pour les appareils Android dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Créez ou ajoutez un profil de configuration d’appareil Wi-Fi pour Android. Consultez les différents paramètres, y compris l’ajout de certificats, le choix d’un type EAP et la sélection d’une méthode d’authentification dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/24/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ea0a60537bb488d3280990747d3e337e73fddc0
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754556"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Ajouter des paramètres Wi-Fi dans Microsoft Intune pour les appareils exécutant Android dans Microsoft Intune

Vous pouvez créer un profil avec des paramètres Wi-Fi spécifiques, puis le déployer sur vos appareils Android. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau, l’ajout d’un certificat PKS ou SCEP et bien plus encore.

Ces paramètres Wi-Fi sont divisés en deux catégories : Paramètres de base et paramètres de niveau entreprise.

Cet article décrit ces paramètres.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](device-profile-create.md).

## <a name="basic"></a>De base

- **Type de Wi-Fi** : Choisissez **De base**.
- **SSID** : entrez l’**identificateur SSID**, qui est le nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le **nom de réseau** que vous avez configuré quand ils choisissent la connexion.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.

## <a name="enterprise"></a>Enterprise

- **Type de Wi-Fi** : Choisissez **Entreprise**.
- **SSID** : entrez l’**identificateur SSID**, qui est le nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le **nom de réseau** que vous avez configuré quand ils choisissent la connexion.
- **Réseau masqué** : Choisissez **Activer** pour que ce réseau ne s’affiche pas dans la liste des réseaux disponibles sur l’appareil. Le SSID n’est pas diffusé. Choisissez **désactiver** pour afficher ce réseau dans la liste des réseaux disponibles sur l’appareil.
- **Type EAP** : Choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes :

  - **EAP-TLS** : Entrez également :

    - **Approbation du serveur** - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur quand le client se connecte au réseau. Il authentifie la connexion.

    - **Authentification du client** - **Certificat client pour l’authentification du client (certificat d’identité)**  : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

    - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

    - **Paramètres du proxy** : spécifiez la configuration du proxy utilisée par votre organisation. Les options disponibles sont les suivantes :

      - **Aucun** : vous n’utilisez pas de serveur proxy.
      - **Automatique** : sélectionnez cette option pour rendre disponible le paramètre *URL du serveur proxy*, que vous utilisez pour spécifier votre serveur proxy ou un fichier de configuration automatique du proxy (PAC, Proxy Auto-Configuration) contenant une liste de vos serveurs proxy.

    - **URL du serveur proxy** : ce paramètre est disponible quand vous définissez *Paramètres du proxy* sur *Automatique*. Spécifiez une des options suivantes pour diriger les appareils vers votre serveur proxy :

      - Adresse IP. Par exemple, `10.0.0.11`
      - Une URL. Par exemple, `http://proxyserver.contoso.com`.
      - L’URL d’un fichier de configuration automatique de proxy. Par exemple : `http://proxy.contoso.com/proxy.pac`.

      Pour plus d’informations sur les fichiers PAC, consultez [Fichier de configuration automatique de proxy (PAC)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (ouvre un site non-Microsoft).

  - **EAP-TTLS** : Entrez également :

    - **Approbation du serveur** - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur quand le client se connecte au réseau. Il authentifie la connexion.

    - **Authentification du client** : Choisissez une **Méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : Invitez l’utilisateur à fournir un nom d’utilisateur et un mot de passe pour authentifier la connexion. Entrez également :
        - **Méthode non-EAP (identité interne)**  : Choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi. Les options disponibles sont les suivantes :

          - **Mot de passe non chiffré (PAP)**
          - **Protocole CHAP (Challenge Handshake Authentication Protocol)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

    - **Paramètres du proxy** : spécifiez la configuration du proxy utilisée par votre organisation. Les options disponibles sont les suivantes :

      - **Aucun** : vous n’utilisez pas de serveur proxy.
      - **Automatique** : sélectionnez cette option pour rendre disponible le paramètre *URL du serveur proxy*, que vous utilisez pour spécifier votre serveur proxy ou un fichier de configuration automatique du proxy (PAC, Proxy Auto-Configuration) contenant une liste de vos serveurs proxy.

    - **URL du serveur proxy** : ce paramètre est disponible quand vous définissez *Paramètres du proxy* sur *Automatique*. Spécifiez une des options suivantes pour diriger les appareils vers votre serveur proxy :

      - Adresse IP. Par exemple, `10.0.0.11`
      - Une URL. Par exemple, `http://proxyserver.contoso.com`.
      - L’URL d’un fichier de configuration automatique de proxy. Par exemple : `http://proxy.contoso.com/proxy.pac`.

      Pour plus d’informations sur les fichiers PAC, consultez [Fichier de configuration automatique de proxy (PAC)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (ouvre un site non-Microsoft).

  - **PEAP** : Entrez également :

    - **Approbation du serveur** - **Certificat racine pour la validation du serveur** : Choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur quand le client se connecte au réseau. Il authentifie la connexion.

    - **Authentification du client** : Choisissez une **Méthode d’authentification**. Les options disponibles sont les suivantes :

      - **Nom d’utilisateur et mot de passe** : Invitez l’utilisateur à fournir un nom d’utilisateur et un mot de passe pour authentifier la connexion. Entrez également :
        - **Méthode non-EAP pour l’authentification (identité interne)**  : Choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi. Les options disponibles sont les suivantes :

          - **Aucun**
          - **Microsoft CHAP Version 2 (MS-CHAP v2)**

      - **Certificats** : Choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.

      - **Confidentialité de l’identité (identité externe)**  : Entrez le texte envoyé dans la réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

      - **Paramètres du proxy** : spécifiez la configuration du proxy utilisée par votre organisation. Les options disponibles sont les suivantes :

        - **Aucun** : vous n’utilisez pas de serveur proxy.
        - **Automatique** : sélectionnez cette option pour rendre disponible le paramètre *URL du serveur proxy*, que vous utilisez pour spécifier votre serveur proxy ou un fichier de configuration automatique du proxy (PAC, Proxy Auto-Configuration) contenant une liste de vos serveurs proxy.

      - **URL du serveur proxy** : ce paramètre est disponible quand vous définissez *Paramètres du proxy* sur *Automatique*. Spécifiez une des options suivantes pour diriger les appareils vers votre serveur proxy :

        - Adresse IP. Par exemple, `10.0.0.11`
        - Une URL. Par exemple, `http://proxyserver.contoso.com`.
        - L’URL d’un fichier de configuration automatique de proxy. Par exemple : `http://proxy.contoso.com/proxy.pac`.

        Pour plus d’informations sur les fichiers PAC, consultez [Fichier de configuration automatique de proxy (PAC)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (ouvre un site non-Microsoft).

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Ensuite, [affectez ce profil](device-profile-assign.md).

## <a name="more-resources"></a>Ressources complémentaires

- [Vue d’ensemble des paramètres Wi-Fi](wi-fi-settings-configure.md), y compris d’autres plateformes.

- À l’aide d’appareils Android Enterprise ou Android Kiosk ? Si oui, examinez les [paramètres Wi-Fi pour des appareils exécutant Android Entreprise et des services dédiés](wi-fi-settings-android-enterprise.md).
