---
title: Paramètres Wi-Fi pour appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil de configuration Wi-Fi à l’aide des paramètres Wi-Fi pour appareils Windows 10 (et versions ultérieures) dans Microsoft Intune. Vous pouvez configurer des paramètres de base ou des paramètres d’entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/8/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 76d9efc969f68188d9752996267ff7a88363f76f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180814"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Ajouter des paramètres Wi-Fi pour appareils Windows 10 (et ultérieurs) dans Intune

Vous pouvez créer un profil avec des paramètres Wi-Fi spécifiques, puis le déployer sur vos appareils Windows versions 10 et ultérieures. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau à l’aide d’une clé prépartagée.

Cet article décrit ces paramètres.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](device-profile-create.md).

## <a name="basic-profile"></a>Profil de base

- **Type de Wi-Fi** : choisissez **De base**. 

- **Nom du Wi-Fi (SSID)** : identificateur SSID. Cette valeur correspond au nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, lorsque les utilisateurs choisissent la connexion, ils voient uniquement le **nom de connexion** que vous avez configuré.

- **Nom de la connexion** : entrez un nom convivial pour la connexion Wi-Fi. Le texte que vous entrez correspond au nom que voient les utilisateurs quand ils parcourent la liste des connexions disponibles sur leur appareil.

- **Se connecter automatiquement une fois à portée** : si vous sélectionnez **Oui**, les appareils se connectent automatiquement lorsqu’ils sont dans la portée de ce réseau. Si vous sélectionnez **Non**, les appareils ne se connectent pas automatiquement.

  - **Se connecter au réseau préféré si disponible** : si les appareils se trouvent dans la portée du réseau préféré, choisissez **Oui** pour utiliser ce réseau. Choisissez **Non** pour utiliser le réseau Wi-Fi du profil de configuration.

    Par exemple, vous créez un réseau Wi-Fi **ContosoCorp** et utilisez **ContosoCorp** dans le profil de configuration. Vous avez également un réseau Wi-Fi **ContosoGuest** à portée. Lorsque vos appareils d’entreprise sont à portée, ils doivent se connecter automatiquement à **ContosoCorp**. Dans ce scénario, définissez la propriété **Se connecter au réseau préféré si disponible** sur **Non**.

  - **Me connecter même si le réseau ne diffuse pas son SSID** : choisissez **Oui** pour le profil de configuration afin de vous connecter automatiquement à votre réseau, même lorsque celui-ci est masqué (c’est-à-dire que son SSID n’est pas diffusé publiquement). Choisissez **Non** si vous ne souhaitez pas que ce profil de configuration se connecte à votre réseau masqué.

- **Limite de connexion contrôlée** : un administrateur peut choisir la façon dont le trafic du réseau est limité. Les applications peuvent ensuite ajuster leur comportement de trafic réseau en fonction de ce paramètre. Les options disponibles sont les suivantes :

  - **Illimité** : option par défaut. La connexion n’est pas limitée, et il n’existe aucune restriction sur le trafic.
  - **Fixe** : utilisez cette option si le réseau est configuré avec une limite fixe pour le trafic réseau. Une fois cette limite atteinte, l’accès réseau est interdit.
  - **Variable** : utilisez cette option si le trafic réseau est facturé par octet (coût par octet).

- **Type de sécurité sans fil** : entrez le protocole de sécurité utilisé pour authentifier les appareils sur votre réseau. Les options disponibles sont :
  - **Ouvert (aucune authentification)** : utilisez cette option uniquement si le réseau n’est pas sécurisé.
  - **WPA/WPA2-Personnel** : option plus sécurisée, couramment utilisée pour la connectivité Wi-Fi. Pour plus de sécurité, vous pouvez également entrer une clé de réseau ou de mot de passe prépartagée. 

    - **Clé prépartagée** : facultatif. Affichée quand vous choisissez **WPA/WPA2-Personnel** comme type de sécurité. Lorsque le réseau de votre organisation est configuré ou configuré, un mot de passe ou une clé réseau sont également configurés. Entrez cette clé de mot de passe ou de réseau pour la valeur PSK. Entrez une chaîne comportant entre 8 et 64 caractères. Si votre clé de mot de passe ou réseau comprend 64 caractères, entrez des caractères hexadécimaux.
    
      > [!NOTE]
      > Quand vous enregistrez le profil WiFi, la clé prépartagée que vous avez entrée est masquée pour des raisons de sécurité. Le filigrane de la clé prépartagée affiche toujours **Non configuré** même si la clé prépartagée a été enregistrée dans le profil. Pour changer la clé prépartagée, entrez une nouvelle clé, puis enregistrez le profil. Si vous enregistrez une clé prépartagée, modifiez la stratégie et ne renseignez pas le champ de clé prépartagée afin de continuer à utiliser la clé prépartagée existante.

- **Paramètres du proxy de l’entreprise** : pour utiliser les paramètres proxy au sein de votre organisation. Les options disponibles sont les suivantes :
  - **Aucun** : aucun paramètre de proxy n’est configuré.
  - **Configurer manuellement** : entrez **l’adresse IP du serveur proxy** et son **numéro de port**.
  - **Configurer automatiquement** : entrez l’URL qui pointe vers un script de configuration automatique du proxy. Par exemple, entrez `http://proxy.contoso.com/proxy.pac`.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et apparaît dans la liste des profils.

## <a name="enterprise-profile"></a>Profil d’entreprise

- **Type de Wi-Fi** : choisissez **Entreprise**. 

- **Nom du Wi-Fi (SSID)** : identificateur SSID. Cette valeur correspond au nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, lorsque les utilisateurs choisissent la connexion, ils voient uniquement le **nom de connexion** que vous avez configuré.

- **Nom de la connexion** : entrez un nom convivial pour la connexion Wi-Fi. Le texte que vous entrez correspond au nom que voient les utilisateurs quand ils parcourent la liste des connexions disponibles sur leur appareil.

- **Se connecter automatiquement une fois à portée** : si vous sélectionnez **Oui**, les appareils se connectent automatiquement lorsqu’ils sont dans la portée de ce réseau. Si vous sélectionnez **Non**, les appareils ne se connectent pas automatiquement.
  - **Se connecter au réseau préféré si disponible** : si les appareils se trouvent dans la portée du réseau préféré, choisissez **Oui** pour utiliser ce réseau. Choisissez **Non** pour utiliser le réseau Wi-Fi du profil de configuration.

    Par exemple, vous créez un réseau Wi-Fi **ContosoCorp** et utilisez **ContosoCorp** dans le profil de configuration. Vous avez également un réseau Wi-Fi **ContosoGuest** à portée. Lorsque vos appareils d’entreprise sont à portée, ils doivent se connecter automatiquement à **ContosoCorp**. Dans ce scénario, définissez la propriété **Se connecter au réseau préféré si disponible** sur **Non**.

  - **Me connecter même si le réseau ne diffuse pas son SSID** : choisissez **Oui** pour le profil de configuration afin de vous connecter automatiquement à votre réseau, même lorsque celui-ci est masqué (c’est-à-dire que son SSID n’est pas diffusé publiquement). Choisissez **Non** si vous ne souhaitez pas que ce profil de configuration se connecte à votre réseau masqué.

- **Limite de connexion contrôlée** : un administrateur peut choisir la façon dont le trafic du réseau est limité. Les applications peuvent ensuite ajuster leur comportement de trafic réseau en fonction de ce paramètre. Les options disponibles sont les suivantes :

  - **Illimité** : option par défaut. La connexion n’est pas limitée, et il n’existe aucune restriction sur le trafic.
  - **Fixe** : utilisez cette option si le réseau est configuré avec une limite fixe pour le trafic réseau. Une fois cette limite atteinte, l’accès réseau est interdit.
  - **Variable** : utilisez cette option si le trafic réseau est facturé par octet.

- **Authentification unique (SSO)**  : pour configurer l’authentification unique (SSO), qui permet d’utiliser les mêmes informations d’identification pour la connexion à l’ordinateur et la connexion au réseau Wi-Fi. Les options disponibles sont :
  - **Désactiver** : désactive l’authentification unique. L’utilisateur doit s’authentifier auprès du réseau séparément.
  - **Activer avant que l’utilisateur se connecte à l’appareil** : utilisez l’authentification unique auprès du réseau juste avant la connexion de l’utilisateur.
  - **Activer après que l’utilisateur se connecte à l’appareil** : utilisez l’authentification unique auprès du réseau juste après la connexion de l’utilisateur.
  - **Durée maximale de l’authentification avant expiration** : entrez le délai maximal avant authentification au réseau (de 1 à 120 secondes).
  - **Autoriser Windows à demander à l’utilisateur d’autres informations d’identification d’authentification** : choisissez **Oui** pour autoriser Windows à demander à l’utilisateur de fournir des informations d’identification supplémentaires, si la méthode d’authentification l’exige. Choisissez **Non** pour masquer cette invite.

- **Activer la mise en cache de la clé PMK (Pairwise Master Key)** : sélectionnez **Oui** pour mettre en cache la clé PMK utilisée pour l’authentification. En général, cette mise en cache permet d’accélérer l’authentification au réseau. Choisissez **Non** pour forcer la négociation d’authentification chaque fois que vous vous connectez au réseau Wi-Fi.

  - **Durée maximale de stockage d’une clé PMK dans le cache** : entrez le nombre de minutes pendant lesquelles une clé PMK doit être stockée dans le cache (de 5 à 1 440 minutes).
  - **Nombre maximal de clés PMK stockées dans le cache** : entrez le nombre de clés stockées dans le cache (entre 1 et 255).

- **Activer la préauthentification** : la préauthentification permet au profil de s’authentifier auprès de tous les points d’accès du réseau du profil avant la connexion. La préauthentification reconnecte l’utilisateur ou les appareils plus rapidement lors du passage d’un point d’accès à un autre. Choisissez **Oui** pour que le profil s’authentifie auprès de tous les points d’accès du réseau qui se trouvent dans la portée. Choisissez **Non** pour exiger de l’utilisateur ou de l’appareil qu’ils s’authentifient séparément à chaque point d’accès.

  - **Nb max. de tentatives de préauthentification** : entrez le nombre maximal de tentatives de préauthentification (de 1 à 16).

- **Type EAP** : choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes :

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **PEAP (Protected EAP)**

    **Paramètres supplémentaires EAP-TLS, EAP-TTLS et PEAP** :
    
    > [!NOTE]
    > Seuls les profils de certificat SCEP sont pris en charge lors de l’utilisation d’un type EAP. Les profils de certificat PKCS ne sont pas pris en charge. Veillez à choisir un certificat SCEP pour toutes les fois où un utilisateur est invité à entrer un certificat.

      - **Approbation du serveur**  

        **Noms des serveurs de certificats** : à utiliser avec les types EAP **EAP-TLS**, **EAP-TTLS** ou **PEAP**. Entrez un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Si vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.  

        **Certificat racine pour la validation de serveur** : à utiliser avec les types EAP **EAP-TLS**, **EAP-TTLS** ou **PEAP**. Choisissez le profil de certificat racine approuvé utilisé pour authentifier la connexion.  

        **Confidentialité de l’identité (identité externe)**  : à utiliser avec le type EAP **PEAP**. Entrez le texte envoyé en réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.  

      - **Authentification client**

        **Certificat client pour l’authentification du client (certificat d’identité)**  : à utiliser avec le type EAP **EAP-TLS**. Choisissez le profil de certificat utilisé pour authentifier la connexion.

        **Méthode d’authentification** : à utiliser avec le type EAP **EAP-TTLS**. Sélectionnez la méthode d'authentification de la connexion :  

          - **Certificats** : sélectionnez le certificat client SCEP qui correspond au certificat d’identité présenté au serveur.
          - **Nom utilisateur et mot de passe** : entrez une **méthode non EAP (identité interne)** pour l’authentification. Les options disponibles sont les suivantes :

            - **Mot de passe non chiffré (PAP)**
            - **Protocole CHAP (Challenge Handshake)**
            - **Microsoft CHAP (MS-CHAP)**
            - **Microsoft CHAP Version 2 (MS-CHAP v2)**

        **Confidentialité de l’identité (identité externe)**  : à utiliser avec le type EAP **EAP-TTLS**. Entrez le texte envoyé en réponse à une demande d’identité EAP. Ce texte peut être n'importe quelle valeur. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

- **Paramètres du proxy de l’entreprise** : pour utiliser les paramètres proxy au sein de votre organisation. Les options disponibles sont les suivantes :
  - **Aucun** : aucun paramètre de proxy n’est configuré.
  - **Configurer manuellement** : entrez **l’adresse IP du serveur proxy** et son **numéro de port**.
  - **Configurer automatiquement** : entrez l’URL qui pointe vers un script de configuration automatique du proxy. Par exemple, entrez `http://proxy.contoso.com/proxy.pac`.

- **Forcer la conformité du profil Wi-Fi aux normes FIPS (Federal Information Processing Standard)**  : choisissez **Oui** lors de la validation par rapport à la norme FIPS 140-2. Cette norme est obligatoire pour toutes les agences du gouvernement fédéral des États-Unis qui utilisent des systèmes de sécurité basés sur le chiffrement afin de protéger les informations sensibles, mais non classifiées, stockées numériquement. Choisissez **Non** pour ne pas appliquer la conformité FIPS.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et apparaît dans la liste des profils.

## <a name="use-an-imported-settings-file"></a>Utiliser un fichier de paramètres importés

Pour tous les paramètres non disponibles dans Intune, vous pouvez exporter les paramètres Wi-Fi à partir d’un autre appareil Windows. Cette exportation génère un fichier .xml contenant tous les paramètres. Ensuite, importez ce fichier dans Intune et utilisez-le comme profil Wi-Fi. Consultez [Exporter et importer des paramètres Wi-Fi pour appareils Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Ensuite, [affectez ce profil](device-profile-assign.md).

## <a name="more-resources"></a>Ressources complémentaires

- Consultez les paramètres disponibles pour [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
- [Vue d’ensemble des paramètres Wi-Fi](wi-fi-settings-configure.md), y compris d’autres plateformes
