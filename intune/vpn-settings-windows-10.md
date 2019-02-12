---
title: Paramètres VPN Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez tous les paramètres VPN disponibles dans Microsoft Intune, à quoi ils servent et ce qu’ils font, notamment les règles de trafic, l’accès conditionnel et les paramètres DNS et de proxy pour les appareils Windows 10 et Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e38d5e68e79facfd270de64c79708b74aa460189
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838187"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Paramètres des appareils Windows 10 et Windows Holographic permettant d’ajouter des connexions VPN en utilisant Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez ajouter et configurer des connexions VPN pour les appareils à l’aide de Microsoft Intune. Cet article liste et décrit les fonctionnalités et paramètres couramment utilisés lors de la création de réseaux privés virtuels (VPN). Ces fonctionnalités et paramètres VPN sont utilisés dans les profils de configuration des appareils d’Intune et sont envoyés (push) ou déployés sur les appareils. 

Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver des fonctionnalités, notamment l’utilisation d’un fournisseur VPN, l’activation d’Always On, l’utilisation de DNS, l’ajout d’un proxy et plus encore.

Ces paramètres s'appliquent aux appareils exécutant :

- Windows 10
- Windows Holographic for Business

Selon les paramètres que vous choisissez, toutes les valeurs ne sont pas nécessairement configurables.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil VPN](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Paramètres VPN de base

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Serveurs** : ajoutez un ou plusieurs serveurs VPN auxquels les appareils se connectent. Lorsque vous ajoutez un serveur, vous entrez les informations suivantes :
  - **Description** : entrez un nom descriptif pour le serveur, comme **Serveur VPN Contoso**.
  - **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur VPN auquel les appareils se connectent, comme **192.168.1.1** ou **vpn.contoso.com**.
  - **Serveur par défaut** : active ce serveur comme serveur par défaut que les appareils utilisent pour établir la connexion. Ne définissez qu’un seul serveur par défaut.
  - **Importer** : accédez à un fichier séparé par des virgules incluant une liste de serveurs au format description, adresse IP ou nom de domaine complet, serveur par défaut. Choisissez **OK** pour importer ces serveurs dans la liste **Serveurs**.
  - **Exporter** : exporte la liste des serveurs dans un fichier de valeurs séparées par des virgules (csv).

- **Inscrire les adresses IP au DNS interne** : sélectionnez **Activer** pour configurer le profil VPN Windows 10 pour inscrire dynamiquement les adresses IP affectées à l’interface VPN auprès du DNS interne. Sélectionnez **Désactiver** pour ne pas inscrire dynamiquement les adresses IP.

- **Type de connexion** : Sélectionnez le type de connexion VPN dans la liste de fournisseurs suivante :

  - **Pulse Secure**
  - **Client F5 Edge**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automatique**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Lorsque vous choisissez un type de connexion VPN, vous pouvez également être invité à entrer les paramètres suivants :  
    - **Always On** : **activez** cette option pour vous connecter automatiquement à la connexion VPN quand les événements suivants se produisent : 
      - À la connexion des utilisateurs à leurs appareils
      - Au changement du réseau sur l’appareil
      - À la réactivation de l’écran de l’appareil 

    - **Méthode d’authentification** : sélectionnez le mode d’authentification des utilisateurs auprès du serveur VPN. L’utilisation de **certificats** offre des fonctionnalités améliorées, comme l’expérience sans intervention, VPN à la demande et VPN par application.
    - **Mémoriser les informations d’identification à chaque ouverture de session ** : choisissez de mettre en cache les informations d’identification d’authentification.
    - **XML personnalisé** : entrez des commandes XML personnalisées qui configurent la connexion VPN.
    - **Code XML EAP** : entrez des commandes XML EAP qui configurent la connexion VPN.

#### <a name="pulse-secure-example"></a>Exemple Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Exemple F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Exemple SonicWall Mobile Connect
**Groupe de connexion ou domaine** : cette propriété ne peut pas être définie dans le profil VPN. À la place, Mobile Connect analyse cette valeur lorsque le nom d’utilisateur et le domaine sont entrés dans les formats `username@domain` ou `DOMAIN\username`.

Exemple :

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>Exemple CheckPoint Mobile VPN

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Écriture de code XML personnalisé
Pour plus d’informations sur l’écriture des commandes XML personnalisées, consultez la documentation du VPN de chaque fabricant.

Pour plus d’informations sur la création de code XML EAP personnalisé, consultez [Configuration EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Règles de trafic et d’application

- **Associer la protection des informations Windows ou des applications à ce VPN** : activez ce paramètre si vous souhaitez que seules certaines applications utilisent la connexion VPN. Les options disponibles sont les suivantes :

  - **Associer une protection des informations Windows à cette connexion** : entrez un **domaine WIP pour cette connexion**.
  - **Associer des applications à cette connexion** : vous pouvez **Limiter la connexion VPN à ces applications** et ajouter des **Applications associées**. Les applications que vous entrez automatiquement utilisent la connexion VPN. Le type d'application détermine l'identificateur de l'application. Pour une application universelle, entrez le nom de famille du package. Pour une application de bureau, indiquez le chemin de l’application.
  >[!IMPORTANT]
  >Nous vous recommandons de sécuriser toutes les listes d’applications créées pour des VPN par application. Si un utilisateur non autorisé modifie cette liste et que vous l’importez dans la liste d’applications du VPN par application, vous autorisez alors potentiellement un accès VPN à des applications qui ne doivent pas y avoir accès. Pour sécuriser les listes d’applications, vous avez la possibilité d’utiliser une liste de contrôle d’accès (liste ACL).

- **Règles de trafic réseau pour cette connexion VPN** : sélectionnez les protocoles, les ports locaux et distants et les plages d’adresses à activer pour la connexion VPN. Si vous ne créez pas de règle de trafic réseau, tous les protocoles, les ports et les plages d’adresses sont alors activés. Une fois qu’une règle est créée, la connexion VPN utilise uniquement les protocoles, les ports et les plages d’adresses que vous entrez dans cette règle.

## <a name="conditional-access"></a>Accès conditionnel

- **Accès conditionnel pour cette connexion VPN** : active le flux de conformité des appareils à partir du client. Quand cette option est activée, le client VPN communique avec Azure Active Directory (AD) pour obtenir un certificat à utiliser pour l’authentification. Le VPN doit être configuré pour utiliser l’authentification par certificat, et le serveur VPN doit approuver le serveur retourné par Azure AD.

- **Authentification unique (SSO) avec certificat de remplacement** : pour la conformité des appareils, utilisez un certificat autre que le certificat d’authentification VPN pour l’authentification Kerberos. Entrez le certificat avec les paramètres suivants :

  - **Nom** : nom pour l’utilisation améliorée de la clé
  - **Identificateur d’objet** : Identificateur d’objet pour l’utilisation améliorée de la clé
  - **Hachage de l’émetteur** : empreinte numérique du certificat SSO

## <a name="dns-settings"></a>Paramètres DNS

- **Liste de recherche de suffixes DNS** : dans **Suffixes DNS**, entrez un suffixe DNS et cliquez sur **Ajouter**. Vous pouvez ajouter un grand nombre de suffixes.

  Lorsque vous utilisez des suffixes DNS, vous pouvez rechercher une ressource réseau à l’aide de son nom court, au lieu du nom de domaine complet (FQDN). Si vous effectuez la recherche à l’aide du nom court, le suffixe est déterminé automatiquement par le serveur DNS. Par exemple, `utah.contoso.com` se trouve dans la liste de suffixes DNS. Vous effectuez un test ping sur `DEV-comp`. Dans ce scénario, le test est résolu en `DEV-comp.utah.contoso.com`.

  Les suffixes DNS sont résolus dans l’ordre indiqué, et l’ordre peut être changé. Par exemple, `colorado.contoso.com` et `utah.contoso.com` se trouvent dans la liste de suffixes DNS et ont une ressource appelée `DEV-comp`. Dans la mesure où `colorado.contoso.com` apparaît en premier dans la liste, il est résolu en `DEV-comp.colorado.contoso.com`.
  
  Pour changer l’ordre, cliquez sur les points à gauche du suffixe DNS, puis faites-le glisser vers le haut :

  ![Sélectionner les trois points et cliquer-déplacer pour déplacer le suffixe dns](./media/vpn-settings-windows10-move-dns-suffix.png)

- **Règles de la table de stratégie de résolution des noms (NRPT)**  : Les règles de la table de stratégie de résolution des noms (NRPT) définissent la manière dont DNS résout les noms quand il est connecté au VPN. Une fois que la connexion VPN est établie, choisissez les serveurs DNS qu’utilise la connexion VPN.

  Vous pouvez ajouter des règles à la table, qui incluent le domaine, le serveur DNS, le proxy et autres détails, pour résoudre le domaine que vous entrez. La connexion VPN utilise ces règles quand les utilisateurs se connectent aux domaines que vous entrez.

  Sélectionnez **Ajouter** pour ajouter une nouvelle règle. Pour chaque serveur, entrez :

  - **Domaine** : entrez le nom de domaine complet (FQDN) ou un suffixe DNS pour appliquer la règle. Vous pouvez également entrer un point (.) au début d’un suffixe DNS. Par exemple, entrez `contoso.com` ou `.allcontososubdomains.com`.
  - **Serveurs DNS** : entrez l’adresse IP ou le serveur DNS qui résout le domaine. Par exemple, entrez `10.0.0.3` ou `vpn.contoso.com`.
  - **Proxy** : entrez le serveur proxy web qui résout le domaine. Par exemple, entrez `http://proxy.com`.
  - **Connexion automatique** : quand il est **Activé**, l’appareil se connecte automatiquement au VPN quand il se connecte à un domaine entré, par exemple `contoso.com`. Quand il est **Non configuré** (valeur par défaut), l’appareil ne se connecte pas automatiquement au VPN.
  - **Persistant** : quand elle est définie sur **Activé**, la règle reste dans la table de stratégie de résolution des noms (NRPT) tant qu’elle n’est pas supprimée manuellement de l’appareil, même après la déconnexion du VPN. Quand elles sont définies sur **Non configuré** (valeur par défaut), les règles NRPT du profil VPN sont supprimées de l’appareil lors de la déconnexion du VPN.

## <a name="proxy-settings"></a>Paramètres du proxy

- **Script de configuration automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez l’**URL du serveur Proxy**, comme `http://proxy.contoso.com`, qui inclut le fichier de configuration.
- **Adresse** : entrez l’adresse du serveur proxy, comme une adresse IP ou `vpn.contoso.com`
- **Numéro de port** : entrez le numéro de port TCP utilisé par votre serveur proxy
- **Contourner le proxy pour les adresses locales** : si vous ne souhaitez pas utiliser un serveur proxy pour les adresses locales, choisissez Activer. Ce paramètre s’applique si votre serveur VPN nécessite un serveur proxy pour la connexion.

## <a name="split-tunneling"></a>Tunneling fractionné

- **Fractionner le tunneling** : vous pouvez **Activer** ou **Désactiver** cette option pour laisser les appareils décider quelle connexion utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder à ses fichiers de travail, mais utilise le réseau standard de l’hôtel pour surfer sur Internet.
- **Fractionner les routages de tunneling pour cette connexion VPN ** : ajoutez des routes facultatives pour les fournisseurs VPN tiers. Entrez un préfixe de destination et une taille de préfixe pour chaque connexion.

## <a name="trusted-network-detection"></a>Détection de réseaux approuvés

**Suffixes DNS de réseau approuvé** : quand les utilisateurs sont déjà connectés à un réseau approuvé, vous pouvez empêcher les appareils de se connecter automatiquement à d’autres connexions VPN.

Dans **Suffixes DNS**, entrez un suffixe DNS que vous souhaitez approuver, par exemple contoso.com, puis sélectionnez **Ajouter**. Vous pouvez ajouter autant de suffixes que vous le voulez.

Si un utilisateur est connecté à un suffixe DNS de la liste, il ne se connecte pas automatiquement à une autre connexion VPN. L’utilisateur continue à utiliser la liste approuvée des suffixes DNS que vous entrez. Le réseau approuvé est toujours utilisé, même si un déclencheur automatique est défini.

Par exemple, si l’utilisateur est déjà connecté à un suffixe DNS approuvé, les déclencheurs automatiques suivants sont ignorés. Plus précisément, les suffixes DNS de la liste annulent tous les autres déclencheurs automatiques de connexion, notamment :

- Always on
- Déclencheur basé sur les applications
- Déclencheur automatique DNS

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md), puis [supervisez son état](device-profile-monitor.md).

Configurez les paramètres VPN sur les appareils [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md) et [macOS](vpn-settings-macos.md).
