---
title: Ajouter des paramètres VPN aux appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil de configuration VPN (réseau privé virtuel) à l’aide des paramètres de configuration VPN disponibles, notamment les détails de la connexion, les méthodes d’authentification et la tunnelisation fractionnée, dans les paramètres de base ; les paramètres VPN personnalisés avec l’identificateur et les paires clé-valeur ; les paramètres VPN par application qui incluent des URL Safari et des réseaux VPN à la demande avec SSID ou domaines de recherche DNS ; les paramètres de proxy pour inclure un script de configuration, une adresse IP ou FQDN (nom de domaine complet) et le port TCP dans Microsoft Intune sur les appareils exécutant iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d922ecde0159603acbfbc3dc0590592592d72645
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67046210"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Configurer les paramètres VPN sur les appareils iOS dans Microsoft Intune

Microsoft Intune inclut de nombreux paramètres VPN que vous pouvez déployer sur vos appareils iOS. Ces paramètres permettent de créer et de configurer des connexions VPN au réseau de votre organisation. Cet article décrit ces paramètres. Certains paramètres sont disponibles uniquement sur certains clients VPN, par exemple Citrix, Zscaler, etc.

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
- **Zscaler** : pour utiliser l’accès conditionnel ou autoriser les utilisateurs à contourner l’écran de connexion de Zscaler, vous devez intégrer Zscaler Private Access (ZPA) à votre compte Azure AD. Pour des instructions détaillées, consultez la [documentation Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
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
  - **Certificats** : sous **Certificat d’authentification**, sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer les certificats](certificates-configure.md) fournit quelques conseils sur les profils de certificat.
  - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent entrer un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.  

    > [!NOTE]
    > Si le nom d’utilisateur et le mot de passe sont utilisés comme méthode d’authentification pour les VPN IPsec Cisco, ils doivent fournir le SharedSecret par le biais d’un profil Apple Configurator personnalisé.

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

## <a name="next-step"></a>Étape suivante
[Créer des profils VPN dans Intune](vpn-settings-configure.md)  
