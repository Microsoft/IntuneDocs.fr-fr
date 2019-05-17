---
title: Données envoyées par Intune à Apple
titleSuffix: Microsoft Intune
description: Liste des données envoyées à Apple par Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1fbf8f37b989112025bd6d54328dd61246913f7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400209"
---
# <a name="data-intune-sends-to-apple"></a>Données envoyées par Intune à Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quand un des services Apple suivant est activé sur un appareil, Microsoft Intune établit une connexion avec Apple, et partage des informations sur l’utilisateur et sur l’appareil avec Apple : 

- [Programme d’inscription d’appareils Apple (DEP)](device-enrollment-program-enroll-ios.md)
- [Certificat Push MDM Apple (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Programme d’achats en volume (VPP) Apple](vpp-apps-ios.md)

Pour que Microsoft Intune puisse établir une connexion, vous devez créer un compte Apple pour chacun des services Apple.

Le tableau suivant répertorie les données que Microsoft Intune envoie depuis un appareil vers les services Apple activés. 

| Service | Données envoyées à Apple | Utilisé pour |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton, PushMagic | Si le serveur accepte l’appareil, l’appareil fournit son jeton d’appareil de notification Push au serveur. Le serveur doit utiliser ce jeton pour envoyer des messages Push à l’appareil. Ce message d’archivage contient également une chaîne PushMagic. Le serveur doit stocker cette chaîne en mémoire et l’inclure dans les messages Push qu’il envoie à l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton de serveur | Jeton d’appareil de notification Push utilisé pour l’authentification auprès du service Apple. |
| ASM/DEP | nom_serveur | Nom identifiable pour le serveur MDM. |
| ASM/DEP | server_uuid | Identificateur de serveur généré par le système. |
| ASM/DEP | admin_id | ID Apple de la personne qui a généré les jetons actuels qui sont utilisés. |
| ASM/DEP | org_name | Nom de l’organisation. |
| ASM/DEP | org_email | Adresse e-mail de l’organisation. |
| ASM/DEP | org_phone | Téléphone de l’organisation. |
| ASM/DEP | org_address | Adresse de l’organisation. |
| ASM/DEP | org_id | ID client du programme d’inscription des appareils Cette clé est disponible seulement dans le protocole version 3 et ultérieure. |
| ASM/DEP | serial_number | Numéro de série de l’appareil (chaîne). |
| ASM/DEP | model | Nom du modèle (chaîne). |
| ASM/DEP | description | Description de l’appareil (chaîne). |
| ASM/DEP | asset_tag | Étiquette d’actif de l’appareil (chaîne). |
| ASM/DEP | profile_status | État de l’installation du profil. Valeurs possibles : **empty**, **assigned**, **pushed** ou **removed**. |
| ASM/DEP | profile_uuid | ID unique du profil affecté. |
| ASM/DEP | device_assigned_by | Adresse e-mail de la personne qui a affecté l’appareil. |
| ASM/DEP | os | Système d’exploitation de l’appareil : iOS, OSX ou tvOS. Cette clé est valide dans le protocole X-Server version 2 et ultérieure. |
| ASM/DEP | device_family | Famille de produits Apple de l’appareil : iPad, iPhone, iPod, Mac ou AppleTV. Cette clé est valide dans le protocole X-Server version 2 et ultérieure. |
| ASM/DEP | profile_name | Chaîne. Nom explicite pour le profil. |
| ASM/DEP | support_phone_number | Facultatif. Chaîne. Numéro de téléphone du support pour l’organisation. |
| ASM/DEP | support_email_address | Facultatif. Chaîne. Adresse e-mail du support pour l’organisation. Cette clé est valide dans le protocole X-Server version 2 et ultérieure. |
| ASM/DEP | du service | Facultatif. Chaîne. Nom du département ou de l’emplacement défini par l’utilisateur. |
| ASM/DEP | périphériques | Tableau de chaînes contenant les numéros de série des appareils. (Peut être vide.) |
| VPP | GUID de l’ID utilisateur Intune | GUID généré par Intune. |
| VPP | UPN de l’ID Apple géré | ID Apple qui a été spécifié par l’administrateur lors de la configuration de la connexion de jeton VPP auprès d’Apple. |
| VPP | Numéro de série | Numéro de série de l’appareil géré. |

Pour arrêter d’utiliser les services Apple avec Microsoft Intune et supprimer les données, vous devez à la fois désactiver le jeton Apple de Microsoft Intune et supprimer votre compte Apple. Reportez-vous au compte Apple pour savoir comment effectuer la gestion du compte.


