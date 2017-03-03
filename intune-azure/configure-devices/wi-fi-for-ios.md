---
title: "Paramètres Wi-Fi Intune pour les appareils iOS | Préversion Intune Azure | Microsoft Docs"
description: "Préversion Intune Azure : Découvrez les paramètres Intune que vous pouvez utiliser pour configurer les connexions Wi-Fi sur des appareils iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89229a5e-3421-4221-a62f-fa800620cc0d
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 85224b2758eeb1f9c7745b9f18f250a7d1292e0f
ms.lasthandoff: 02/16/2017


---

# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Paramètres Wi-Fi pour les appareils iOS dans Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]



## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Paramètres Wi-Fi pour les profils de base et d’entreprise

- **Nom du réseau** : saisissez un nom pour cette connexion Wi-Fi. Il s'agit du nom que voient les utilisateurs lorsqu’ils parcourent la liste des connexions disponibles sur leurs appareils.
- **SSID** : identificateur SSID. Il s’agit du nom réel du réseau sans fil auquel les appareils se connectent. Toutefois, les utilisateurs voient uniquement le nom de réseau créé ci-dessus lorsqu’ils choisissent la connexion.
- **Se connecter automatiquement** : l’appareil se connecte chaque fois qu’il se trouve dans la portée de ce réseau.
- **Réseau masqué** : empêche ce réseau de s’afficher dans la liste des réseaux disponibles sur l’appareil.
- **Paramètres de proxy** : choisissez parmi :
    - **Aucun** : aucun paramètre de proxy n’est configuré.
    - **Manuel** : saisissez **l’Adresse du serveur proxy** (comme une adresse IP), et son **Numéro de port** associé.
    - **Automatique** : utilisez un fichier pour configurer le serveur proxy. Saisissez **l’URL du serveur proxy** (par exemple **http://proxy.contoso.com**) qui contient le fichier de configuration.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Paramètres Wi-Fi pour les profils de base uniquement

- **Type de sécurité** : sélectionnez le protocole de sécurité à utiliser pour s’authentifier sur le réseau Wi-Fi depuis :
    - **Ouvert (aucune authentification)** : utilisez cette option uniquement si le réseau n’est pas sécurisé.
    - **WPA/WPA2 - Personal**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Paramètres Wi-Fi pour les profils d’entreprise uniquement

- **Type EAP** : choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées :
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Options supplémentaires lorsque vous choisissez un type EAP


|Nom du paramètre|Plus d'informations|À effectuer quand :|
|--------------|-------------|----------|
|**Paramètres PAC (Protected Access Credential (informations d’identification d’accès protégé))**|Sélectionnez cette option si vous voulez utiliser les informations d'identification d'accès protégé pour établir un tunnel authentifié entre le client et le serveur d'authentification. Vous avez le choix entre :<br>- **Utiliser PAC** : utilisez un fichier PAC existant.<br>- **Utiliser et approvisionner PAC** : configurez le fichier PAC sur vos appareils.<br>- **Utiliser et approvisionner les informations d'identification à accès protégé anonymement** : approvisionnez le fichier PAC sur vos appareils pour vous assurer que le fichier PAC est configuré sans authentifier le serveur.|Le Type EAP est **EAP-FAST**|

#### <a name="server-trust"></a>Approbation du serveur


|Nom du paramètre|Plus d'informations|À effectuer quand :|
|--------------|-------------|----------|
|**Noms de serveurs de certificats**|Spécifiez un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification de confiance. Si vous fournissez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs finaux lorsqu’ils se connectent à ce réseau Wi-Fi.|Le type EAP est **EAP-TLS**, **EAP-TTLS** ou **PEAP**.|
|**Certificat racine pour la validation du serveur**|Choisissez le profil de certificat racine approuvé utilisé pour authentifier la connexion. |Le type EAP est **EAP-TLS**, **EAP-TTLS** ou **PEAP**|
|**Confidentialité de l’identité (identité externe)**|Spécifiez le texte envoyé en réponse à une demande d'identité EAP. Ce texte peut être n'importe quelle valeur. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.|Le type EAP est **PEAP**|


#### <a name="client-authentication"></a>Authentification du client


|Nom du paramètre|Plus d'informations|À effectuer quand :|
|--------------|-------------|----------|
|**Certificat client pour l'authentification du client (certificat d'identité)**|Choisissez le profil de certificat SCEP ou PKCS utilisé pour authentifier la connexion.|Le type EAP est **EAP-TLS**|
|**Méthodes d’authentification**|Sélectionnez la méthode d'authentification de la connexion :<br>- **Certificats** pour sélectionner le certificat d’identité client SCEP ou PKCS présenté au serveur.<br><br>- **Nom d’utilisateur et mot de passe** pour spécifier une autre méthode d’authentification. <br><br>Si vous avez sélectionné **Nom d’utilisateur et mot de passe**, configurez :<br><br>-  **Méthode non EAP (identité interne)**, puis sélectionnez la méthode d’authentification de la connexion :<br>- **Aucun**<br>- **Mot de passe non chiffré (PAP)**<br>- **Protocole CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Version 2 (MS-CHAP v2)**<br>Les options disponibles dépendent du type EAP sélectionné.<br><br>**et**<br><br>- **Confidentialité de l'identité (identité externe)** : spécifiez le texte envoyé en réponse à une demande d'identité EAP. Ce texte peut être n'importe quelle valeur. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.|Le type EAP est **EAP-TTLS** ou *

