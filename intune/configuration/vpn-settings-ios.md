---
title: Configurer les paramètres VPN sur les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil de configuration VPN (réseau privé virtuel) à l’aide des paramètres de configuration VPN disponibles, notamment les détails de la connexion, les méthodes d’authentification et la tunnelisation fractionnée, dans les paramètres de base ; les paramètres VPN personnalisés avec l’identificateur et les paires clé-valeur ; les paramètres VPN par application qui incluent des URL Safari et des réseaux VPN à la demande avec SSID ou domaines de recherche DNS ; les paramètres de proxy pour inclure un script de configuration, une adresse IP ou FQDN (nom de domaine complet) et le port TCP dans Microsoft Intune sur les appareils exécutant iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d7b831899a740e722560c509c4b09c31d2a42b
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593791"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Ajouter les paramètres VPN sur les appareils iOS dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune inclut de nombreux paramètres VPN que vous pouvez déployer sur vos appareils iOS. Ces paramètres permettent de créer et de configurer des connexions VPN au réseau de votre organisation. Cet article décrit ces paramètres. Certains paramètres sont disponibles uniquement sur certains clients VPN, par exemple Citrix, Zscaler, etc.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](vpn-settings-configure.md).

> [!NOTE]
> Ces paramètres sont disponibles pour tous les types d’inscription. Pour plus d’informations sur les types d’inscription, consultez [inscription iOS](../enrollment/ios-enroll.md).

## <a name="connection-type"></a>Type de connexion

Sélectionnez le type de connexion VPN dans la liste de fournisseurs suivante :

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect** : applicable à la version 4.0.5x de l’application [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) et aux versions antérieures
- **Cisco AnyConnect** : applicable à la version 4.0.7x de l’application [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) et aux versions ultérieures.
- **SonicWall Mobile Connect**
- **F5 Access Legacy** : applicable à la version 2.1 de l’application F5 Access Legacy et aux versions antérieures.
- **F5 Access** : applicable à la version 3.0 de l’application F5 Access et aux versions ultérieures.
- **Palo Alto Networks GlobalProtect (hérité)** : applicable à la version 4.1 de Palo Alto Networks GlobalProtect et aux versions antérieures.
- **Palo Alto Networks GlobalProtect** : applicable à la version 5.0 de Palo Alto Networks GlobalProtect et aux versions ultérieures.
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN** (VPN Citrix)
- **Citrix SSO**
- **Zscaler** : pour utiliser l’accès conditionnel ou autoriser les utilisateurs à contourner l’écran de connexion de Zscaler, vous devez intégrer Zscaler Private Access (ZPA) à votre compte Azure AD. Pour des instructions détaillées, consultez la [documentation Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **IKEv2**: les [paramètres IKEv2](#ikev2-settings) (dans cet article) décrivent les propriétés.
- **VPN personnalisé**

> [!NOTE]
> Cisco, Citrix, F5 et Palo Alto ont annoncé que leurs clients hérités ne fonctionnaient pas sur iOS 12. Vous devrez donc effectuer la migration des nouvelles applications dès que possible. Pour plus d’informations, consultez le [blog de l’équipe du support technique Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## <a name="base-vpn-settings"></a>Paramètres VPN de base

Les paramètres affichés dans la liste suivante sont déterminés par le type de connexion VPN que vous choisissez.  

- **Nom de la connexion** : les utilisateurs finaux voient ce nom quand ils recherchent sur leur appareil une liste de connexions VPN disponibles.
- **Nom de domaine personnalisé** (Zscaler uniquement) : vous pouvez préremplir le champ de connexion à l’application Zscaler avec le domaine auquel appartiennent vos utilisateurs. Par exemple, si le nom d’utilisateur est `Joe@contoso.net`, le domaine `contoso.net` s’affiche de manière statique dans le champ à l’ouverture de l’application. Si vous n’entrez pas de nom de domaine, la partie domaine de l’UPN dans Azure AD (Active Directory) est utilisée.
- **Adresse IP ou nom de domaine complet** : adresse IP ou nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez `192.168.1.1` ou `vpn.contoso.com`.
- **Nom du cloud de l’organisation** (Zscaler uniquement) : entrez le nom du cloud où votre organisation est provisionnée. Ce nom se trouve dans l’URL que vous utilisez pour vous connecter à Zscaler.  
- **Méthode d’authentification** : choisissez comment les appareils s’authentifient auprès du serveur VPN. 
  - **Certificats** : sous **Certificat d’authentification**, sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer les certificats](../protect/certificates-configure.md) fournit quelques conseils sur les profils de certificat.
  - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent entrer un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.  

    > [!NOTE]
    > Si le nom d’utilisateur et le mot de passe sont utilisés comme méthode d’authentification pour les VPN IPsec Cisco, ils doivent fournir le SharedSecret par le biais d’un profil Apple Configurator personnalisé.

  - **Informations d’identification dérivées**: si aucun émetteur d’informations d’identification dérivé n’a été configuré, Intune vous invite à le faire.

- **URL exclues** (Zscaler uniquement) : lorsque vous êtes connecté au VPN Zscaler, les URL répertoriées sont accessibles en dehors du cloud Zscaler. 

- **Fractionner le tunneling** : vous pouvez **Activer** ou **Désactiver** cette option pour laisser les appareils décider quelle connexion utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder à ses fichiers de travail, mais utilise le réseau standard de l’hôtel pour surfer sur Internet.

- **Identificateur VPN** (VPN personnalisé, Zscaler et Citrix) : identificateur pour l’application VPN que vous utilisez, qui est fourni par votre fournisseur VPN.
  - **Entrer les paires clé-valeur pour les attributs du VPN personnalisé de votre organisation** : ajoutez ou importez des **Clés** et des **Valeurs** pour personnaliser votre connexion VPN. N’oubliez pas que ces valeurs sont généralement indiquées par votre fournisseur VPN.

- **Activer le contrôle d’accès réseau (NAC)** (Citrix SSO, Accès F5) : lorsque vous choisissez **J’accepte**, l’ID d’appareil est inclus dans le profil VPN. Cet ID peut être utilisé pour l’authentification sur le VPN pour autoriser ou empêcher l’accès au réseau.

  **Lorsque vous utilisez l’accès F5**, veillez à :

  - confirmer que vous utilisez F5 BIG-IP 13.1.1.5. BIG-IP 14 n’est pas pris en charge.
  - Intégrez BIG-IP avec Intune pour le contrôle d’accès réseau. Consultez le guide F5 [Présentation : configuration APM pour vérifications de posture d’appareils avec systèmes de gestion de point de terminaison](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89).
  - Activer le contrôle d’accès réseau dans le profil VPN.

  **Lorsque vous utilisez Citrix SSO avec Gateway**, veillez à :

  - Confirmer que vous utilisez Citrix Gateway 12.0.59 ou une version ultérieure.
  - Confirmer que vos utilisateurs ont Citrix SSO 1.1.6 ou une version ultérieure installée sur leurs appareils.
  - Intégrez la passerelle Citrix avec Intune pour le contrôle d’accès réseau. Consultez le guide de déploiement Citrix [Intégration de Microsoft Intune/Enterprise Mobility Suite avec NetScaler (scénario LDAP + OTP)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf).
  - Activer le contrôle d’accès réseau dans le profil VPN.

  **Détails importants** :  

  - Quand le contrôle d’accès réseau est activé, le VPN est déconnecté toutes les 24 heures. Le VPN peut être immédiatement reconnecté.
  - L’ID d’appareil fait partie du profil, mais il n’est pas visible dans Intune. Cet ID n’est stocké nulle part et n’est pas partagé par Microsoft.

  Lorsque l’ID d’appareil est pris en charge par des partenaires VPN, le client VPN, tel que Citrix SSO, peut obtenir l’ID. Il peut ensuite interroger Intune afin de confirmer l’inscription de l’appareil et la conformité du profil VPN.

  - Pour supprimer ce paramètre, recréez le profil et ne sélectionnez pas **J’accepte**. Réaffectez ensuite le profil.

## <a name="ikev2-settings"></a>Paramètres IKEv2

Ces paramètres s’appliquent lorsque vous choisissez le **type de connexion**  > **IKEv2**.

- **Identificateur distant**: entrez l’adresse IP réseau, le nom de domaine complet, le UserFQDN ou le ASN1DN du serveur IKEv2. Par exemple, entrez `10.0.0.3` ou `vpn.contoso.com`. En règle générale, vous entrez la même valeur que le nom de la [**connexion**](#base-vpn-settings) (dans cet article). Toutefois, cela dépend de vos paramètres de serveur IKEv2.

- **Type d’authentification du client**: choisissez la manière dont le client VPN s’authentifie auprès du VPN. Les options disponibles sont les suivantes :
  - **Authentification utilisateur** (par défaut) : les informations d’identification de l’utilisateur s’authentifient auprès du VPN.
  - **Authentification**de l’ordinateur : les informations d’identification de l’appareil s’authentifient auprès du VPN.

- **Méthode d’authentification**: choisissez le type d’informations d’identification du client à envoyer au serveur. Les options disponibles sont les suivantes :
  - **Certificats**: utilise un profil de certificat existant pour s’authentifier auprès du VPN. Assurez-vous que ce profil de certificat est déjà attribué à l’utilisateur ou au périphérique. Dans le cas contraire, la connexion VPN échoue.
    - **Type de certificat**: sélectionnez le type de chiffrement utilisé par le certificat. Assurez-vous que le serveur VPN est configuré pour accepter ce type de certificat. Les options disponibles sont les suivantes :
      - **RSA** (par défaut)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **Nom d’utilisateur et mot de passe** (authentification utilisateur uniquement) : quand les utilisateurs se connectent au VPN, ils sont invités à entrer leur nom d’utilisateur et leur mot de passe.
  - **Secret partagé** (authentification de l’ordinateur uniquement) : vous permet d’entrer un secret partagé à envoyer au serveur VPN.
    - **Secret partagé**: entrez le secret partagé, également appelé clé prépartagée (PSK). Assurez-vous que la valeur correspond au secret partagé configuré sur le serveur VPN.

- **Nom commun**de l’émetteur du certificat de serveur : permet au serveur VPN de s’authentifier auprès du client VPN. Entrez le nom commun de l’émetteur du certificat (CN) du certificat de serveur VPN envoyé au client VPN sur l’appareil. Assurez-vous que la valeur CN correspond à la configuration sur le serveur VPN. Dans le cas contraire, la connexion VPN échoue.
- **Nom commun du certificat de serveur**: entrez le nom commun du certificat. Si le champ n’est pas renseigné, la valeur de l’identificateur distant est utilisée.

- **Taux de détection d’homologue mort**: choisissez la fréquence à laquelle le client VPN vérifie si le tunnel VPN est actif. Les options disponibles sont les suivantes :
  - **Non configuré**: utilise le système IOS par défaut, qui peut être le même que le choix de **moyenne**.
  - **None**: désactive la détection d’homologue mort.
  - **Low**: envoie un message KeepAlive toutes les 30 minutes.
  - **Moyenne** (valeur par défaut) : envoie un message KeepAlive toutes les 10 minutes.
  - **High**: envoie un message KeepAlive toutes les 60 secondes.

- **Plage de versions TLS minimale**: entrez la version TLS minimale à utiliser. Entrez `1.0`, `1.1` ou `1.2`. Si le champ n’est pas renseigné, la valeur par défaut de `1.0` est utilisée.
- **Plage de versions TLS maximale**: entrez la version maximale de TLS à utiliser. Entrez `1.0`, `1.1` ou `1.2`. Si le champ n’est pas renseigné, la valeur par défaut de `1.2` est utilisée.
- **Confidentialité de transfert parfaite**: sélectionnez **activer** pour activer le secret de transfert parfait (PFS). PFS est une fonctionnalité de sécurité IP qui réduit l’impact si une clé de session est compromise. **Désactiver** (valeur par défaut) n’utilise pas PFS.
- **Vérification de la révocation des certificats**: sélectionnez **activer** pour vous assurer que les certificats ne sont pas révoqués avant d’autoriser la connexion VPN. Ce contrôle est le meilleur effort. Si le serveur VPN expire avant de déterminer si le certificat est révoqué, l’accès est accordé. **Désactiver** (valeur par défaut) ne vérifie pas les certificats révoqués.

- **Configurer les paramètres d’association de sécurité**: **non configuré** (par défaut) utilise le système IOS par défaut. Sélectionnez **activer** pour entrer les paramètres utilisés lors de la création d’associations de sécurité avec le serveur VPN :
  - **Algorithme de chiffrement**: sélectionnez l’algorithme que vous souhaitez :
    - DES
    - 3DES
    - AES-128
    - AES-256 (valeur par défaut)
    - AES-128-GCM
    - AES-256-GCM
  - **Algorithme d’intégrité**: sélectionnez l’algorithme que vous souhaitez :
    - SHA1-96
    - SHA1-160
    - SHA2-256 (valeur par défaut)
    - SHA2-384
    - SHA2-512
  - **Groupe Diffie-Hellman**: sélectionnez le groupe de votre choix. La valeur par défaut est `2` de groupe.
  - **Durée de vie** (minutes) : choisissez la durée pendant laquelle l’Association de sécurité reste active jusqu’à ce que les touches pivotent. Entrez une valeur entière comprise entre `10` et `1440` (1440 minutes est de 24 heures). La valeur par défaut est `1440`.

- **Configurer un ensemble distinct de paramètres pour les associations de sécurité enfants**: iOS vous permet de configurer des paramètres distincts pour la connexion IKE et toutes les connexions enfants. 

  **Non configuré** (par défaut) utilise les valeurs que vous entrez dans le paramètre **configurer les paramètres d’association de sécurité** précédents. Sélectionnez **activer** pour entrer les paramètres utilisés lors de la création d’associations de sécurité *enfants* avec le serveur VPN :
  - **Algorithme de chiffrement**: sélectionnez l’algorithme que vous souhaitez :
    - DES
    - 3DES
    - AES-128
    - AES-256 (valeur par défaut)
    - AES-128-GCM
    - AES-256-GCM
  - **Algorithme d’intégrité**: sélectionnez l’algorithme que vous souhaitez :
    - SHA1-96
    - SHA1-160
    - SHA2-256 (valeur par défaut)
    - SHA2-384
    - SHA2-512
  - **Groupe Diffie-Hellman**: sélectionnez le groupe de votre choix. La valeur par défaut est `2` de groupe.
  - **Durée de vie** (minutes) : choisissez la durée pendant laquelle l’Association de sécurité reste active jusqu’à ce que les touches pivotent. Entrez une valeur entière comprise entre `10` et `1440` (1440 minutes est de 24 heures). La valeur par défaut est `1440`.

## <a name="automatic-vpn-settings"></a>Paramètres VPN automatiques

- **VPN par application** : active le VPN par application. Permet à la connexion VPN de se déclencher automatiquement quand certaines applications sont ouvertes. Associez également les applications à ce profil VPN. Pour plus d’informations, consultez les [instructions de configuration du VPN par application pour iOS](vpn-setting-configure-per-app.md).
  - **Type de fournisseur** : uniquement disponible pour Pulse Secure et VPN personnalisé.
  - Quand vous utilisez des profils **VPN par application** iOS avec Pulse Secure ou un VPN personnalisé, choisissez entre le tunneling de couche application (app-proxy) ou le tunneling de couche paquet (packet-tunnel). Affectez à **ProviderType** la valeur **app-proxy** pour le tunneling de couche application, ou la valeur **packet-tunnel** pour le tunneling de couche paquet. Si vous ne savez pas quelle valeur utiliser, consultez la documentation de votre fournisseur VPN.
  - **URL Safari qui déclenchent ce VPN** : ajoutez une ou plusieurs URL de site web. Quand ces URL sont consultées sur l’appareil à l’aide du navigateur Safari, la connexion VPN est établie automatiquement.

- **VPN à la demande** : configurez des règles conditionnelles qui contrôlent le démarrage de la connexion VPN. Par exemple, créez une condition dans laquelle la connexion VPN est utilisée uniquement quand un appareil n’est pas connecté au réseau Wi-Fi d’une entreprise. Sinon, créez une condition. Par exemple, la connexion VPN n’est pas lancée si un appareil ne peut pas accéder au domaine de recherche DNS que vous entrez.

  - **Domaines de recherche DNS ou SSID** : indiquez si cette condition utilise les **SSID** de réseau sans fil ou les **domaines de recherche DNS**. Cliquez sur **Ajouter** pour configurer un ou plusieurs SSID ou domaines de recherche.
  - **Sonde de chaîne d’URL** : facultatif. Entrez une URL que la règle utilise comme test. Si l’appareil ayant ce profil accède à cette URL sans redirection, la connexion VPN est lancée. Et l’appareil se connecte à l’URL cible. L’utilisateur ne voit pas le site de la sonde de chaîne d’URL. Par exemple, une sonde de chaîne d’URL peut être l’adresse d’un serveur web d’audit qui vérifie la compatibilité de l’appareil avant la connexion du VPN. Autre exemple, l’URL teste la capacité du VPN à se connecter à un site avant de connecter l’appareil à l’URL cible via le VPN.
  - **Action du domaine** : choisissez l’un des éléments suivants :
    - Se connecter si nécessaire
    - Ne jamais se connecter
  - **Action** : choisissez l’un des éléments suivants :
    - Se connecter
    - Évaluer la connexion
    - Ignorer
    - Déconnecter

## <a name="proxy-settings"></a>Paramètres du proxy

Si vous utilisez un proxy, configurez les paramètres suivants. Les paramètres de proxy ne sont pas disponibles pour les connexions VPN Zscaler.  

- **Script de configuration automatique** : utilisez un fichier de configuration pour configurer le serveur proxy. Entrez l’**URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui inclut le fichier config.
- **Adresse** : entrez l’adresse IP du nom d’hôte complet du serveur proxy.
- **Numéro de port** : entrez le numéro de port associé au serveur proxy.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Configurez les paramètres VPN sur les appareils [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)et [Windows 10](vpn-settings-windows-10.md) .
