---
title: Paramètres VPN pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Voir les paramètres de configuration de réseau privé virtuel (VPN) disponibles, notamment les détails de la connexion, les méthodes d’authentification et la tunnelisation fractionnée, dans les paramètres de base ; les paramètres VPN personnalisés avec l’identificateur et les paires clé-valeur ; les paramètres VPN par application qui incluent des URL Safari et des réseaux VPN à la demande avec SSID ou domaines de recherche DNS ; et les paramètres de proxy pour inclure un script de configuration, une adresse IP ou de nom de domaine complet et le port TCP dans Microsoft Intune sur les appareils exécutant iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: deb6a230573ff20237e6eee386052baba472832a
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313868"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Configurer les paramètres VPN dans Microsoft Intune pour les appareils exécutant iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant iOS.

Selon les paramètres que vous choisissez, toutes les valeurs de la liste suivante ne sont pas nécessairement configurables.

## <a name="base-vpn-settings"></a>Paramètres VPN de base
Les paramètres que vous voyez dans la liste ci-dessous sont déterminés par le type de connexion VPN que vous sélectionnez.  
- **Nom de la connexion** : les utilisateurs finaux voient ce nom quand ils recherchent sur leur appareil une liste de connexions VPN disponibles.
- **Nom de domaine personnalisé** (Zscaler uniquement) : vous pouvez préremplir le champ de connexion à l’application Zscaler avec le domaine auquel appartiennent vos utilisateurs. Par exemple, si le nom d’utilisateur est **Joe@contoso.net**, le domaine **contoso.net** s’affichera statiquement dans le champ lors de l’ouverture de l’application. Si vous ne tapez pas de nom de domaine, c’est la partie de l’UPN relative au domaine d’Azure Active Directory qui est utilisée.
- **Adresse IP ou nom de domaine complet** : adresse IP ou nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent. Par exemple, entrez **192.168.1.1** ou **vpn.contoso.com**. 
- **Nom du cloud de l'organisation** (Zscaler uniquement) : tapez le nom du cloud dans lequel votre organisation est provisionnée. Pour trouver le nom, regardez l’URL que vous utilisez pour vous connecter à Zscaler.  
- **Méthode d’authentification** : choisissez comment les appareils s’authentifient auprès du serveur VPN. 
  - **Certificats** : sous **Certificat d’authentification**, sélectionnez un profil de certificat SCEP ou PKCS existant pour authentifier la connexion. [Configurer les certificats](certificates-configure.md) fournit quelques conseils sur les profils de certificat.
  - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent entrer un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.  

    > [!NOTE]
    > Si le nom d’utilisateur et le mot de passe sont utilisés comme méthode d’authentification pour les VPN IPsec Cisco, ils doivent fournir le SharedSecret par le biais d’un profil Apple Configurator personnalisé.
  
- **Type de connexion** : sélectionnez le type de connexion VPN dans la liste de fournisseurs suivante :
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
  - **Zscaler** : nécessite l’intégration de Zscaler Private Access (ZPA) à votre compte Azure Active Directory. Pour des instructions détaillées, consultez la [documentation Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
  - **VPN personnalisé**    

    > [!NOTE]
    > Cisco, Citrix, F5 et Palo Alto ont annoncé que leurs clients hérités ne fonctionneront pas avec la prochaine version d’iOS 12. Vous devrez donc effectuer la migration des nouvelles applications dès que possible. Pour plus d’informations, consultez le [blog de l’équipe du support technique Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

* **URL exclues** (Zscaler uniquement) : lorsque vous êtes connecté au VPN Zscaler, les URL répertoriées sont accessibles en dehors du cloud Zscaler. 

- **Fractionner le tunneling** : vous pouvez **Activer** ou **Désactiver** cette option pour laisser les appareils décider quelle connexion utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder à ses fichiers de travail, mais utilise le réseau standard de l’hôtel pour surfer sur Internet.   

## <a name="custom-vpn-settings"></a>Paramètres VPN personnalisés

Si vous avez sélectionné **VPN personnalisé** comme type de connexion, configurez les paramètres suivants. Ces paramètres sont également visibles pour les connexions Zscaler et Citrix.

- **Identificateur VPN** : identificateur pour l’application VPN que vous utilisez, qui est fourni par votre fournisseur VPN.
- **Entrer les paires clé-valeur pour les attributs du VPN personnalisé de votre organisation** : ajoutez ou importez des **Clés** et des **Valeurs** pour personnaliser votre connexion VPN. Là encore, ces valeurs sont généralement fournies par votre fournisseur de VPN.

## <a name="automatic-vpn-settings"></a>Paramètres VPN automatiques

- **VPN par application** : cette option active le VPN par application, ce qui permet aux connexions VPN d’être déclenchées automatiquement lorsque certaines applications sont ouvertes. En plus de choisir cette option, vous devez également associer les applications à ce profil VPN. Pour plus d’informations, consultez les [instructions pour configurer le VPN par application pour iOS](vpn-setting-configure-per-app.md). 
  - Le paramètre **Type de fournisseur** est uniquement disponible pour Pulse Secure et le VPN personnalisé.
  - Quand vous utilisez des profils **VPN par application** iOS avec Pulse Secure ou un VPN personnalisé, vous pouvez choisir d’utiliser le tunneling de couche application (app-proxy) ou le tunneling de couche paquet (packet-tunnel). Définissez la valeur **ProviderType** sur **app-proxy** pour le tunneling de couche application ou **packet-tunnel** pour le tunneling de couche paquet. Si vous n’êtes pas sûr de la valeur à utiliser, consultez la documentation de votre fournisseur VPN. 
  - **URL Safari qui déclenchent ce VPN** : sélectionnez cette option pour ajouter une ou plusieurs URL de site web. Quand ces URL sont consultées sur l’appareil à l’aide du navigateur Safari, la connexion VPN est établie automatiquement.

- **VPN à la demande** : configurez des règles conditionnelles qui contrôlent l’activation de la connexion VPN. Par exemple, créez une condition dans laquelle la connexion VPN est utilisée uniquement quand un appareil n’est pas connecté au réseau Wi-Fi d’une société. Ou bien créez une condition dans laquelle la connexion VPN n’est pas lancée si un appareil ne peut pas accéder à un domaine de recherche DNS que vous spécifiez.

  - **Domaines de recherche DNS ou SSID** : indiquez si cette condition utilise les **SSID** de réseau sans fil ou les **domaines de recherche DNS**. Cliquez sur **Ajouter** pour configurer un ou plusieurs SSID ou domaines de recherche.
  - **Sonde de chaîne d’URL** : facultatif. Entrez une URL que la règle utilise comme test. Si l’appareil sur lequel ce profil est installé peut accéder à cette URL sans redirection, la connexion VPN est lancée et l’appareil se connecte à l’URL cible. L’utilisateur ne voit pas le site de la sonde de chaîne d’URL. Par exemple, une sonde de chaîne d’URL peut être l’adresse d’un serveur web d’audit qui vérifie la compatibilité de l’appareil avant la connexion du VPN. Autre exemple, l’URL teste la capacité du VPN à se connecter à un site avant de connecter l’appareil à l’URL cible via le VPN.
  - **Action du domaine** : choisissez l’un des éléments suivants :
    - Se connecter si nécessaire
    - Ne jamais se connecter
  - **Action** : choisissez l’un des éléments suivants :
    - Se connecter
    - Évaluer la connexion
    - Ignorer
    - Se déconnecter

## <a name="proxy-settings"></a>Paramètres du proxy
Si vous utilisez un proxy, configurez les paramètres suivants. Les paramètres de proxy ne sont pas disponibles pour les connexions VPN Zscaler.  

- **Script de configuration automatique** : utilisez un fichier de configuration pour configurer le serveur proxy. Entrez **l’URL du serveur proxy** (par exemple **http://proxy.contoso.com**) qui contient le fichier de configuration.
- **Adresse** : entrez l’adresse IP du nom d’hôte complet du serveur proxy.
- **Numéro de port** : entrez le numéro de port associé au serveur proxy.

## <a name="next-step"></a>Étape suivante
[Créer des profils VPN dans Intune](vpn-settings-configure.md)  
