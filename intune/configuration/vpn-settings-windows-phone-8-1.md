---
title: Configurer des paramètres VPN sur des appareils Windows Phone 8.1 dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil de configuration VPN à l’aide des paramètres de configuration du réseau privé virtuel (VPN), y compris les détails de connexion et les paramètres de proxy pour inclure l’adresse IP ou le nom de domaine complet, et le port TCP dans Microsoft Intune sur les appareils exécutant Windows Phone 8,1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f33fe132eb6c3dbf91c5dc313369d75f4f3e24
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207024"
---
# <a name="add-vpn-settings-on-windows-phone-81-devices-in-microsoft-intune"></a>Ajouter des paramètres VPN sur les appareils Windows Phone 8.1 dans Microsoft Intune



Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant Windows Phone 8.1. 

Selon les paramètres que vous choisissez, toutes les valeurs de la liste suivante ne sont pas nécessairement configurables.

>[!IMPORTANT]
>Les profils VPN Windows Phone 8,1 s’appliquent également aux appareils Windows 10.

## <a name="base-vpn-settings"></a>Paramètres VPN de base

- **Appliquer tous les paramètres à Windows Phone 8,1 uniquement**: configurez ce paramètre dans le portail classique Intune. Ce paramètre ne peut pas être modifié dans le centre d’administration du gestionnaire des points de terminaison Microsoft. Quand la valeur est **Configuré**, les paramètres sont appliqués uniquement aux appareils Windows Phone 8.1. Quand la valeur est **Non configuré**, ces paramètres s’appliquent également aux appareils Windows 10 Mobile.
- **Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN :
  - **Certificats** : sous **Certificat d’authentification**, choisissez le profil de certificat SCEP ou PKCS que vous avez créé précédemment pour authentifier la connexion. Pour plus d’informations sur les profils de certificat, consultez [Guide pratique pour configurer des certificats](../protect/certificates-configure.md).
  - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent fournir un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.
- **Serveurs** : ajoutez un ou plusieurs serveurs VPN auxquels les appareils se connectent.
  - **Ajouter** : ouvre le panneau **Ajouter une ligne** dans lequel vous pouvez spécifier les informations suivantes :
    - **Description** : spécifiez un nom descriptif pour le serveur, comme **Serveur VPN Contoso**.
    - **Adresse IP ou nom de domaine complet** : Fournissez l’adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
    - **Serveur par défaut** : active ce serveur comme serveur par défaut que les appareils utilisent pour établir la connexion. Veillez à ne définir qu’un seul serveur par défaut.
  - **Importer** : accédez à un fichier séparé par des virgules avec une liste de serveurs au format description, adresse IP ou nom de domaine complet, serveur par défaut. Choisissez **OK** pour importer ces serveurs dans la liste **Serveurs**.
  - **Exporter** : exporte la liste des serveurs dans un fichier de valeurs séparées par des virgules (csv).

- **Contourner le VPN sur le réseau Wi-Fi d’entreprise** : activez cette option pour indiquer que la connexion VPN n’est pas utilisée quand l’appareil est connecté au réseau Wi-Fi d’entreprise.
- **Contourner le VPN sur le réseau Wi-Fi domestique** : activez cette option pour indiquer que la connexion VPN n’est pas utilisée quand l’appareil est connecté à un réseau Wi-Fi privé.

- **Type de connexion** : Sélectionnez le type de connexion VPN dans la liste de fournisseurs suivante :
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **Client F5 Edge**
  - **Pulse Secure**

- **Groupe de connexion ou domaine** (SonicWALL Mobile Connect uniquement) : Spécifiez le nom du groupe de connexion ou domaine auquel vous souhaitez vous connecter.
- **Rôle** (Pulse Secure uniquement) : Spécifiez le nom du rôle d'utilisateur qui a accès à cette connexion. Un rôle d’utilisateur définit des options et des paramètres personnels, et active ou désactive certaines fonctionnalités d’accès.
- **Domaine** (Pulse Secure uniquement) : Spécifiez le nom du domaine d'authentification que vous souhaitez utiliser. Un domaine d’authentification est un regroupement de ressources d’authentification qu’utilise le type de connexion Pulse Secure.

- **Liste de recherche de suffixes DNS** : **ajoutez** un ou plusieurs suffixes DNS. Chaque suffixe DNS que vous spécifiez est recherché lors de la connexion à un site web en utilisant un nom court. Par exemple, si vous spécifiez les suffixes DNS **domain1.contoso.com** et **domain2.contoso.com** et que vous visitez l’URL `http://mywebsite`, la recherche est effectuée dans les URL `http://mywebsite.domain1.contoso.com` et `http://mywebsite.domain2.contoso.com`.

- **XML personnalisé** : entrez des commandes XML personnalisées qui configurent la connexion VPN.

  **Exemple Pulse Secure** :

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **Exemple CheckPoint Mobile VPN** :

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **Exemple SonicWall Mobile Connect** :

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **Exemple F5 Edge Client** :

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  pour plus d’informations sur l’écriture des commandes XML personnalisées, consultez la documentation du VPN du fabricant.

- **Fractionner le tunneling** : **activez** ou **désactivez** cette option qui permet aux appareils de choisir la connexion à utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder aux fichiers de travail, mais utilise le réseau standard de l’hôtel pour la navigation web ordinaire.

## <a name="proxy-settings"></a>Paramètres du proxy

- **Détecter automatiquement les paramètres du proxy** : Si votre serveur VPN nécessite un serveur proxy pour la connexion, spécifiez si vous souhaitez que les appareils détectent automatiquement les paramètres de connexion.
- **Script de configuration automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez l’**URL du serveur proxy** (par exemple `http://proxy.contoso.com`) qui contient le fichier config.
- **Utiliser le serveur proxy** : activez cette option si vous souhaitez saisir manuellement les paramètres du serveur proxy.
  - **Adresse** : entrez l’adresse du serveur proxy (comme une adresse IP).
  - **Numéro de port** : entrez le numéro de port associé au serveur proxy.
- **Contourner le proxy pour les adresses locales** : Si votre serveur VPN nécessite un serveur proxy pour la connexion et que vous ne souhaitez pas utiliser le serveur proxy pour les adresses locales que vous spécifiez, sélectionnez cette option.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Configurez les paramètres VPN sur les appareils [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)et [Windows 10](vpn-settings-windows-10.md) .
