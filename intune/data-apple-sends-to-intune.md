---
title: Données envoyées par Apple à Intune
titleSuffix: Microsoft Intune
description: Liste des données envoyées par Apple à Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf27fdb8-f408-425c-9a7c-146de1534425
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4362983bbcdb78f82ce7b16f675c6f61fbefd1e1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396321"
---
# <a name="data-apple-sends-to-intune"></a>Données envoyées par Apple à Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quand un ou plusieurs des services Apple suivants sont activés sur un appareil, Microsoft Intune établit une connexion avec Apple pour partager des informations sur l’utilisateur et l’appareil :

- [Programme d’inscription d’appareils Apple (DEP)](device-enrollment-program-enroll-ios.md)
- [Certificat Push MDM Apple (APNs)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Programme d’achats en volume (VPP) Apple](vpp-apps-ios.md)

Pour que Microsoft Intune puisse établir une connexion, vous devez créer un compte Apple pour chacun des services Apple.

Le tableau suivant répertorie les données qu’un appareil Apple envoie à Intune. [Intune envoie également des données à Apple](data-intune-sends-to-apple.md). 

| Service | Message | Données envoyées à Intune | Utilisé pour |
|:---:|:---:|:---:| ---|
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | MessageType | Type de message : authenticate. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | Rubrique | Rubrique écoutée par l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | MesUDID | UDID des appareils. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | OSVersion | Version du système d’exploitation de l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | BuildVersion | Version de build de l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | ProductName | Nom de produit de l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | SerialNumber | Numéro de série de l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | IMEI | IMEI (International Mobile Equipment Identity) de l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Authentifier | MEID | MEID (Mobile Equipment Identifier) de l’appareil |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | Rubrique | Rubrique écoutée par l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | UDID | UDID de l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | Jeton | Jeton push de l’appareil. Le serveur doit utiliser ce jeton mis à jour au moment de l’envoi de notifications Push à l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | PushMagic | Chaîne magique à inclure dans le message de notification Push.  |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | UnlockToken | Objet blob de données pouvant être utilisé pour déverrouiller l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | TokenUpdate | AwaitingConfiguration | Si la valeur est true, l’appareil attend une commande MDM DeviceConfigured avant de passer à l’Assistant Installation.  |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Checkout | MessageType | Type de message : checkout. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Checkout | Rubrique | Rubrique écoutée par l’appareil. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Checkout | UDID | UDID de l’appareil |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Protocole MDM | État | État.  |
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Protocole MDM | UDID |UDID de l’appareil.  |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Protocole MDM | CommandUUID | UUID de la commande correspondant à cette réponse. |
| [APNs](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Protocole MDM | ErrorChain | Tableau de dictionnaires représentant la chaîne d’erreurs qui se sont produites.  |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Numéro de série | Numéro de série de l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | model | Nom du modèle de l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Description | Description de l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Couleur | Couleur de l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Étiquette d’inventaire | Étiquette d’inventaire de l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | État du profil | État de l’installation du profil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | UUID du profil | UUID du profil affecté. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Heure d’affectation du profil | Horodatage au format ISO 8601 indiquant quand un profil a été affecté à l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Heure d’envoi (push) du profil | Horodatage au format ISO 8601 indiquant quand un profil a été envoyé (push) à l’appareil.|
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Date d’affectation de l’appareil | Horodatage au format ISO 8601 indiquant quand l’appareil a été inscrit dans le Programme d’inscription des appareils. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Appareil affecté par | Adresse e-mail de la personne qui a affecté l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Système d’exploitation | Système d’exploitation de l’appareil. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Jeton du programme d’inscription | Famille de périphériques | Famille de produits Apple de l’appareil. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | Identifiant utilisateur Apple | Identifiant utilisateur généré par Apple. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | description de l’application | Description d’une application VPP. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | icône d’application | URL d’une icône hébergée par Apple pour une application VPP. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | ID d'application | Identifiant d’application Apple, également appelé adamsId. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | nom de l’application | Nom d’une application VPP. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | assignedCount | Nombre de licences affectées pour une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | availableCount | Nombre de licences non affectées pour une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | bundleId | Identifiant de bundle d’une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | copyright | Informations de copyright d’une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | CountryCode | Code pays d’un programme VPP. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | deviceAssignable | Apple retourne true si l’administrateur peut affecter une licence d’appareil pour une application. Sinon, la valeur false est retournée. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | facilitatorMemberId | Identifiant de membre d’un organisateur de compte VPP.  |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | genres | Genres d’une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | GUID de l’ID utilisateur Intune | GUID généré par Intune. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | isIrrevocable | Apple retourne true si la licence ne peut pas être révoquée. Si elle peut être révoquée, la valeur false est retournée. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | Identifiant de licence | Identifiant généré par Apple pour identifier une licence spécifique. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | Localisation | Emplacement stocké dans les données de configuration VPP d’apple. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | UPN de l’ID Apple géré | E-mail AppleID pour l’utilisateur, l’administrateur et le membre organisateur. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | OrganizationId | Identifiant d’organisation affecté par Apple. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | pricingParam | Type de tarification Apple pour une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | productType | Type de produit d’une application VPP. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | retiredCount | Nombre de licences hors service pour une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | totalCount | Nombre total de licences achetées pour une application. |
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | url | URL de l’iTunes Store d’une application.|
| [VPP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/5-Web_Service_Protocol_VPP/webservice.html#//apple_ref/doc/uid/TP40017387-CH8-SW1) | Jeton VPP Apple | État des utilisateurs | Statut de l’utilisateur dans les programmes VPP Apple. |


Pour arrêter d’utiliser les services Apple avec Microsoft Intune et supprimer les données, vous devez à la fois désactiver le jeton Apple de Microsoft Intune et supprimer votre compte Apple. Reportez-vous au compte Apple pour savoir comment effectuer la gestion du compte.


