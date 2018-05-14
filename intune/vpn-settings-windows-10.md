---
title: Configurer les paramètres VPN Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez les paramètres VPN disponibles dans Microsoft Intune, à quoi ils servent et ce qu’ils font, notamment les règles de trafic, l’accès conditionnel et les paramètres DNS et de proxy pour les appareils Windows 10 et les appareils Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: b6371da954aa913e1378c065b203fa197f3fc767
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="windows-10-vpn-settings-in-intune"></a>Paramètres VPN de Windows 10 dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez configurer des connexions VPN avec Intune. Cet article décrit ces paramètres, les règles de trafic, l’accès conditionnel, ainsi que les paramètres DNS et de proxy.

Ces paramètres s’appliquent aux :

- Appareils exécutant Windows 10
- Appareils exécutant Windows Holographic for Business

Selon les paramètres que vous choisissez, toutes les valeurs ne sont pas nécessairement configurables.

## <a name="base-vpn-settings"></a>Paramètres VPN de base

- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Serveurs** : ajoutez un ou plusieurs serveurs VPN auxquels les appareils se connectent. Lorsque vous ajoutez un serveur, vous entrez les informations suivantes :
  - **Description** : entrez un nom descriptif pour le serveur, comme **Serveur VPN Contoso**.
  - **Adresse IP ou nom de domaine complet** : entrez l’adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent, comme **192.168.1.1** ou **vpn.contoso.com**.
  - **Serveur par défaut** : active ce serveur comme serveur par défaut que les appareils utilisent pour établir la connexion. Ne définissez qu’un seul serveur par défaut.
  - **Importer** : accédez à un fichier séparé par des virgules contenant une liste de serveurs au format description, adresse IP ou nom de domaine complet, serveur par défaut. Choisissez **OK** pour importer ces serveurs dans la liste **Serveurs**.
  - **Exporter** : exporte la liste des serveurs dans un fichier de valeurs séparées par des virgules (csv).

- **Type de connexion** : sélectionnez le type de connexion VPN dans la liste de fournisseurs suivante :

  - **Pulse Secure**
  - **Client F5 Edge**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Automatique**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Lorsque vous choisissez un type de connexion VPN, vous pouvez également être invité à entrer les paramètres suivants :  
    - **Always On** : activez cette option pour vous connecter automatiquement à la connexion VPN dans les cas suivants : 
      - À la connexion des utilisateurs à leurs appareils
      - Au changement du réseau sur l’appareil
      - À la réactivation de l’écran de l’appareil 

    - **Méthode d’authentification** : sélectionnez la manière dont les utilisateurs doivent s’authentifier auprès du serveur VPN. L’utilisation de **certificats** offre des fonctionnalités améliorées, comme l’expérience sans intervention, VPN à la demande et VPN par application.
    - **Mémoriser les informations d’identification à chaque ouverture de session** : choisissez de mettre en cache les informations d’identification d’authentification.
    - **XML personnalisé** : entrez des commandes XML personnalisées qui configurent la connexion VPN.
    - **EAP XML** : entrez des commandes EAP XML qui configurent la connexion VPN

#### <a name="pulse-secure-example"></a>Exemple Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Exemple F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Exemple SonicWall Mobile Connect
**Groupe de connexion ou domaine** : cette propriété ne peut pas être définie dans le profil VPN. À la place, Mobile Connect analyse cette valeur lorsque le nom d’utilisateur et le domaine sont entrés dans les formats `username@domain` ou `DOMAIN\username`.

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

<<<<<<< HEAD
- **Associer des TEC ou des applications à ce VPN** : activez cette option si vous souhaitez que seules certaines applications utilisent la connexion VPN. Les options disponibles sont les suivantes :

  - **Associer un TEC à cette connexion** : entrez un **domaine TEC pour cette connexion**
  - **Associer des applications à cette connexion** : vous pouvez **Limiter la connexion VPN à ces applications**, puis ajoutez des **Applications associées**. Les applications que vous entrez automatiquement utilisent la connexion VPN. Le type d'application détermine l'identificateur de l'application. Pour une application universelle, entrez le nom de famille du package. Pour une application de bureau, indiquez le chemin de l’application.
=======
**Limiter la connexion VPN à ces applications** : activez cette option si vous souhaitez que seules certaines applications utilisent la connexion VPN.

**Applications associées** : entrez une liste d’applications qui utilisent automatiquement la connexion VPN. Le type d'application détermine l'identificateur de l'application. Pour une application universelle, entrez le nom de famille du package. Pour une application de bureau, indiquez le chemin de l’application.
>>>>>>> b2f641d045b7649f641fb98e07accc745e697d84

  >[!IMPORTANT]
  >Nous vous recommandons de sécuriser toutes les listes d’applications créées pour des VPN par application. Si un utilisateur non autorisé modifie cette liste et que vous l’importez dans la liste d’applications du VPN par application, vous autorisez alors potentiellement un accès VPN à des applications qui ne doivent pas y avoir accès. Pour sécuriser les listes d’applications, vous avez la possibilité d’utiliser une liste de contrôle d’accès (liste ACL).

- **Règles de trafic réseau pour cette connexion VPN** : sélectionnez les protocoles, les ports locaux/distants et les plages d’adresses à activer pour la connexion VPN. Si vous ne créez pas de règle de trafic réseau, tous les protocoles, les ports et les plages d’adresses sont alors activés. Une fois qu’une règle est créée, la connexion VPN utilise uniquement les protocoles, les ports et les plages d’adresses que vous entrez dans cette règle.

## <a name="conditional-access"></a>Accès conditionnel

- **Accès conditionnel pour cette connexion VPN** : active le flux de conformité des appareils à partir du client. Quand cette option est activée, le client VPN tente de communiquer avec Azure Active Directory (AD) pour obtenir un certificat à utiliser pour l’authentification. Le VPN doit être configuré pour utiliser l’authentification par certificat, et le serveur VPN doit approuver le serveur retourné par Azure AD.

- **Authentification unique avec certificat de remplacement** : pour la conformité des appareils, utilisez un certificat autre que le certificat d’authentification VPN pour l’authentification Kerberos. Entrez le certificat avec les paramètres suivants :

  - **Nom** : nom pour l’utilisation améliorée de la clé
  - **Identificateur d’objet** : identificateur d’objet pour l’utilisation améliorée de la clé
  - **Hachage de l’émetteur** : empreinte numérique du certificat SSO

## <a name="dns-settings"></a>Paramètres DNS

**Domaine et serveurs pour cette connexion VPN** : ajoutez le domaine et le serveur DNS pour la connexion VPN à utiliser. Vous pouvez choisir les serveurs DNS qu’utilise la connexion VPN quand celle-ci est établie. Pour chaque serveur, entrez :
- **Domaine**
- **Serveur DNS**
- **Proxy**

## <a name="proxy-settings"></a>Paramètres du proxy

- **Script de configuration automatique** : utilisez un fichier de configuration pour configurer le serveur proxy. Entrez l’**URL du serveur Proxy**, comme `http://proxy.contoso.com`, qui contient le fichier de configuration.
- **Adresse** : entrez l’adresse du serveur proxy, comme une adresse IP ou `vpn.contoso.com`
- **Numéro de port** : entrez le numéro de port TCP utilisé par votre serveur proxy
- **Contourner le proxy pour les adresses locales** : si vous ne souhaitez pas utiliser un serveur proxy pour les adresses locales, choisissez Activer. Ce paramètre s’applique si votre serveur VPN nécessite un serveur proxy pour la connexion.

## <a name="split-tunneling"></a>Tunneling fractionné

- **Tunneling fractionné** : **activez**ou **désactivez** cette option pour laisser les appareils décider quelle connexion utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder à ses fichiers de travail, mais utilise le réseau standard de l’hôtel pour surfer sur Internet.
- **Fractionner les itinéraires de tunneling pour cette connexion VPN** : ajoutez des itinéraires facultatifs pour les fournisseurs VPN tiers. Entrez un préfixe de destination et une taille de préfixe pour chaque connexion.
