---
title: Paramètres VPN Microsoft Intunes pour les appareils Windows Phone 8.1
titleSuffix: ''
description: Découvrez les paramètres Intune que vous pouvez utiliser pour configurer des connexions VPN sur les appareils exécutant Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 147431f6143d1ff81e170c656c636d0bd4f3837f
ms.sourcegitcommit: dec09e9c91322ca347276785aca3c50036956f32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2018
ms.locfileid: "51859526"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Configurer les paramètres VPN dans Microsoft Intune pour les appareils exécutant Windows Phone 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant Windows Phone 8.1.


Selon les paramètres que vous choisissez, toutes les valeurs de la liste suivante ne sont pas nécessairement configurables.

## <a name="base-vpn-settings"></a>Paramètres VPN de base

- **Appliquer tous les paramètres à Windows Phone 8.1 uniquement** : il s’agit d’un paramètre que vous pouvez configurer dans le portail classique Intune. Dans le portail Azure, ce paramètre ne peut pas être modifié. Si la valeur est **Configuré**, les paramètres sont appliqués uniquement aux appareils Windows Phone 8.1. Si la valeur est **Non configuré**, ces paramètres s’appliquent également aux appareils Windows 10 Mobile.
- **Nom de connexion** : saisissez un nom pour cette connexion. Les utilisateurs voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Méthode d’authentification** : choisissez la façon dont les appareils s’authentifient auprès du serveur VPN à partir de :
    - **Certificats** : sous **Certificat d’authentification**, choisissez le profil de certificat SCEP ou PKCS que vous avez créé précédemment pour authentifier la connexion. Pour plus d’informations sur les profils de certificat, consultez [Guide pratique pour configurer des certificats](certificates-configure.md).
    - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent fournir un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.
- **Serveurs** : Ajoutez un ou plusieurs serveurs VPN auxquels les appareils se connectent.
    - **Ajouter** : ouvre le panneau **Ajouter une ligne** dans lequel vous pouvez spécifier les informations suivantes :
        - **Description** : spécifiez un nom descriptif pour le serveur, comme **Serveur VPN Contoso**.
        - **Adresse IP ou nom de domaine complet** : fournissez l'adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
        - **Serveur par défaut** : Active ce serveur comme serveur par défaut que les appareils utilisent pour établir la connexion. Veillez à ne définir qu’un seul serveur par défaut.
    - **Importer** : accédez à un fichier qui contient une liste séparée par des virgules de serveurs au format description, adresse IP ou nom de domaine complet, serveur par défaut. Choisissez **OK** pour les importer dans la liste **Serveurs**.
    - **Exporter** : exporte la liste des serveurs dans un fichier de valeurs séparées par des virgules (csv).

- **Contourner le VPN sur le réseau Wi-Fi d’entreprise** : activez cette option pour indiquer que les connexions VPN ne sont pas utilisées quand l’appareil est connecté au réseau Wi-Fi d’entreprise.
- **Contourner le VPN sur le réseau Wi-Fi domestique** : activez cette option pour indiquer que la connexion VPN n’est pas utilisée quand l’appareil est connecté à un réseau Wi-Fi domestique.

- **Type de connexion** : sélectionnez le type de connexion VPN à partir de la liste de fournisseurs suivante :
    - **Check Point Capsule VPN**
    - **SonicWall Mobile Connect**
    - **Client F5 Edge**
    - **Pulse Secure**

- **Groupe de connexion ou domaine** (SonicWall Mobile Connect uniquement) : spécifiez le nom du groupe de connexion ou domaine auquel vous souhaitez vous connecter.
- **Rôle** (Pulse Secure uniquement) : spécifiez le nom du rôle d'utilisateur qui a accès à cette connexion. Un rôle d’utilisateur définit des options et des paramètres personnels, et active ou désactive certaines fonctionnalités d’accès.
- **Domaine** (Pusle Secure uniquement) : spécifiez le nom du domaine d'authentification que vous souhaitez utiliser. Un domaine d’authentification est un regroupement de ressources d’authentification qu’utilise le type de connexion Pulse Secure.

- **Liste de recherche de suffixes DNS** - **Ajouter** un ou plusieurs suffixes DNS. Chaque suffixe DNS que vous spécifiez est recherché lors de la connexion à un site web en utilisant un nom court. Par exemple, si vous spécifiez les suffixes DNS **domain1.contoso.com** et **domain2.contoso.com** et que vous visitez l’URL `http://mywebsite`, la recherche est effectuée dans les URL `http://mywebsite.domain1.contoso.com` et `http://mywebsite.domain2.contoso.com`.

- **XML personnalisé** : spécifiez des commandes XML personnalisées qui configurent la connexion VPN.

    **Exemple pour Pulse Secure :**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exemple pour CheckPoint Mobile VPN :**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exemple pour SonicWall Mobile Connect :**
```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exemple pour Client F5 Edge :**
```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Pour plus d’informations sur l’écriture des commandes XML personnalisées, reportez-vous à la documentation du VPN de chaque fabricant.

- **Tunneling fractionné** - **Activez** ou **désactivez** cette option qui permet aux appareils de choisir la connexion à utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder aux fichiers de travail, mais utilise le réseau standard de l’hôtel pour la navigation web ordinaire.




## <a name="proxy-settings"></a>Paramètres du proxy

- **Détecter automatiquement les paramètres du proxy** : si votre serveur VPN nécessite un serveur proxy pour la connexion, spécifiez si vous souhaitez que les appareils détectent automatiquement les paramètres de connexion. Pour plus d'informations, consultez la documentation de Windows Server.
- **Script de configuration automatique** : utilisez un fichier de configuration pour configurer le serveur proxy. Entrez l’**URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui contient le fichier config.
- **Utiliser un serveur proxy** : activez cette option si vous souhaitez saisir manuellement les paramètres du serveur proxy.
    - **Adresse** : saisissez l’adresse du serveur proxy (comme une adresse IP).
    - **Numéro de port** : saisissez le numéro de port associé au serveur proxy.
- **Contourner le proxy pour les adresses locales** : si votre serveur VPN nécessite un serveur proxy pour la connexion, sélectionnez cette option si vous ne souhaitez pas utiliser le serveur proxy pour les adresses locales que vous spécifiez. Pour plus d'informations, consultez la documentation de Windows Server.
