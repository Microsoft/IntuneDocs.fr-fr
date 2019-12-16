---
title: Configurer des paramètres de réseau câblé pour les appareils macOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Créez ou ajoutez un profil de configuration d’appareil de réseau câblé pour les appareils macOS. Consultez les différents paramètres, y compris l’ajout de certificats, le choix d’un type EAP et la sélection d’une méthode d’authentification dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/4/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dba36d03489bcdeee3c3c1f69a4995823dd21ee
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74994330"
---
# <a name="add-wired-network-settings-for-macos-devices-in-microsoft-intune"></a>Ajouter des paramètres de réseau câblé pour les appareils macOS dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez créer un profil avec des paramètres de réseau câblé spécifiques, puis le déployer sur vos appareils macOS. Microsoft Intune offre de nombreuses fonctionnalités, notamment l’authentification auprès de votre réseau, l’ajout d’un certificat PKS ou SCEP et bien plus encore. 

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil d’appareil](device-profile-create.md).

> [!NOTE]
> Ces paramètres sont disponibles pour tous les types d’inscription. Pour plus d’informations sur les types d’inscription, consultez [inscription MacOS](../enrollment/macos-enroll.md).

## <a name="profiles"></a>Profils

- **Type de profil**: choisissez **réseau câblé**.
- **Interface réseau** : 
- **Type EAP** : choisissez le type de protocole EAP (Extensible Authentication Protocol) utilisé pour authentifier les connexions sans fil sécurisées. Les options disponibles sont les suivantes :
  - **EAP-FAST** : entrez les **Paramètres d’identification d’accès protégé (PAC)** . Cette option utilise les informations d'identification d'accès protégé pour créer un tunnel authentifié entre le client et le serveur d'authentification. Les options disponibles sont les suivantes :
    - **Ne pas utiliser (PAC)**
    - **Utiliser (PAC)**  : si un fichier PAC existe, utilisez-le.
    - **Utiliser et approvisionner PAC** : créez et ajoutez le fichier PAC sur vos appareils.
    - **Utiliser et configurer anonymement le fichier PAC** : créer et ajouter le fichier PAC sur vos appareils sans l’authentification auprès du serveur.
  - **EAP-TLS** : entrez également :
    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.
    - **Authentification du client** - **Certificat client pour l’authentification du client (certificat d’identité)**  : choisissez le profil de certificat client SCEP ou PKCS qui est également déployée sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.
  - **EAP-TLS** : entrez également :
    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.
    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :
      - **Nom d’utilisateur et mot de passe** : invitez l’utilisateur d’un nom d’utilisateur et d’un mot de passe à authentifier la connexion. Entrez également :
        - **Méthode non EAP (identité interne)**  : choisissez comment authentifier la connexion. Veillez à choisir le même protocole que celui qui est configuré sur votre réseau Wi-Fi.
          Vos options : **Mot de passe non chiffré (PAP)** , **Protocole CHAP (Challenge Handshake Authentication Protocol)** , **Microsoft CHAP (MS-CHAP)** ou **Microsoft CHAP Version 2 (MS-CHAP v2)**
      - **Certificats** : choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.
      - **Confidentialité de l’identité (identité externe)**  : entrez le texte envoyé en réponse à une requête d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.
  - **LEAP**
  - **PEAP** : entrez également :
    - **Approbation de serveur** - **Noms des serveurs de certificats** : **Ajoutez** un ou plusieurs noms communs utilisés dans les certificats émis par votre autorité de certification approuvée (CA). Lorsque vous entrez ces informations, vous pouvez ignorer la boîte de dialogue d’approbation dynamique qui s’affiche sur les appareils des utilisateurs quand ils se connectent à ce réseau Wi-Fi.
    - **Certificat racine pour la validation du serveur** : choisissez un profil de certificat racine approuvé existant. Ce certificat est présenté au serveur lorsque le client se connecte au réseau et est utilisé pour authentifier la connexion.
    - **Authentification du client** : choisissez une **méthode d’authentification**. Les options disponibles sont les suivantes :
      - **Nom d’utilisateur et mot de passe** : invitez l’utilisateur d’un nom d’utilisateur et d’un mot de passe à authentifier la connexion. 
      - **Certificats** : choisissez le profil de certificat client SCEP or PKCS qui est également déployé sur l’appareil. Ce certificat est l’identité présentée par l’appareil au serveur pour authentifier la connexion.
      - **Confidentialité de l’identité (identité externe)**  : entrez le texte envoyé en réponse à une requête d’identité EAP. Ce texte peut être n'importe quelle valeur, par exemple `anonymous`. Lors de l'authentification, cette identité anonyme est envoyée en premier, suivie de l'identification réelle adressée dans un tunnel sécurisé.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Maintenant, [affectez ce profil](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

Configurez les paramètres Wi-Fi sur les appareils [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [iOS](wi-fi-settings-ios.md)et [Windows 10](wi-fi-settings-windows.md) .
