---
title: "Paramètres VPN Intune pour les appareils Windows 8.1"
titleSuffix: Azure portal
description: "Découvrez les paramètres Intune que vous pouvez utiliser pour configurer des connexions VPN sur les appareils Windows 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0126c483ec905d4c073e19b35498c27069ecd285
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="vpn-settings-for-windows-81-devices-in-microsoft-intune"></a>Paramètres VPN pour les appareils Windows 8.1 dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Selon les paramètres que vous choisissez, toutes les valeurs dans la liste ci-dessous ne peuvent pas nécessairement être configurées.

## <a name="base-vpn-settings"></a>Paramètres VPN de base


- **Appliquer tous les paramètres à Windows 8.1 uniquement** : il s’agit d’un paramètre que vous pouvez configurer dans le portail classique Intune. Dans le portail Azure, ce paramètre ne peut pas être modifié. Si la valeur est **Configuré**, les paramètres seront uniquement appliqués aux appareils Windows 8.1. Si la valeur est **Non configuré**, ces paramètres s’appliquent également aux appareils Windows 10.
- **Nom de connexion** : saisissez un nom pour cette connexion. Les utilisateurs finaux voient ce nom lorsqu’ils consultent leur appareil pour obtenir la liste des connexions VPN disponibles.
- **Serveurs** : ajoutez un ou plusieurs serveurs VPN auxquels les appareils se connectent.
    - **Ajouter** : ouvre le panneau **Ajouter une ligne** dans lequel vous pouvez spécifier les informations suivantes :
        - **Description** : spécifiez un nom descriptif pour le serveur, comme **Serveur VPN Contoso**.
        - **Adresse IP ou nom de domaine complet** : fournissez l'adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
        - **Serveur par défaut** : active ce serveur comme serveur par défaut que les appareils utiliseront pour établir la connexion. Veillez à ne définir qu’un seul serveur par défaut.
    - **Importer** : accédez à un fichier contenant une liste séparée par virgules de serveurs au format description, adresse IP ou nom de domaine complet, serveur par défaut. Choisissez **OK** pour les importer dans la liste **Serveurs**.
    - **Exporter** : exporte la liste des serveurs dans un fichier de valeurs séparées par des virgules (csv).

- **Type de connexion** : sélectionnez le type de connexion VPN à partir de la liste de fournisseurs suivante :
- **Check Point Capsule VPN**
- **Dell SonicWALL Mobile Connect**
- **Client F5 Edge**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Groupe de connexion ou domaine** (Dell SonicWALL Mobile Connect uniquement) : spécifiez le nom du groupe de connexion ou domaine auquel vous souhaitez vous connecter.

- **Rôle** (Pulse Secure uniquement) : spécifiez le nom du rôle d'utilisateur qui a accès à cette connexion. Un rôle d’utilisateur définit des options et des paramètres personnels, et active ou désactive certaines fonctionnalités d’accès.

- **Domaine** (Pusle Secure uniquement) : spécifiez le nom du domaine d'authentification que vous souhaitez utiliser. Un domaine d’authentification est un regroupement de ressources d’authentification qu’utilise le type de connexion Pulse Secure.


- **XML personnalisé** : spécifiez des commandes XML personnalisées qui configurent la connexion VPN.

**Exemple pour Pulse Secure :**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>

```

**Exemple pour CheckPoint Mobile VPN :**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />

```

**Exemple pour Dell SonicWALL Mobile Connect :**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**Exemple pour Client F5 Edge :**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

Pour plus d’informations sur l’écriture des commandes XML personnalisées, reportez-vous à la documentation du VPN de chaque fabricant.


## <a name="proxy-settings"></a>Paramètres du proxy

- **Détecter automatiquement les paramètres du proxy** : si votre serveur VPN nécessite un serveur proxy pour la connexion, spécifiez si vous souhaitez que les appareils détectent automatiquement les paramètres de connexion. Pour plus d'informations, consultez la documentation de Windows Server.
- **Script de configuration automatique** : utilisez un fichier de configuration pour configurer le serveur proxy. Saisissez **l’URL du serveur proxy** (par exemple **http://proxy.contoso.com**) qui contient le fichier de configuration.
- **Utiliser un serveur proxy** : activez cette option si vous souhaitez saisir manuellement les paramètres du serveur proxy.
    - **Adresse** : saisissez l’adresse du serveur proxy (comme une adresse IP).
    - **Numéro de port** : saisissez le numéro de port associé au serveur proxy.
- **Contourner le proxy pour les adresses locales** : si votre serveur VPN nécessite un serveur proxy pour la connexion, sélectionnez cette option si vous ne souhaitez pas utiliser le serveur proxy pour les adresses locales que vous spécifiez. Pour plus d'informations, consultez la documentation de Windows Server.
