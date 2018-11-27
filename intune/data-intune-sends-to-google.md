---
title: Données envoyées par Intune à Google
titleSuffix: Microsoft Intune
description: Liste des données envoyées à Google par Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bb205472c4407dab6ff990e33737a8bd8b24a010
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188640"
---
# <a name="data-intune-sends-to-google"></a>Données envoyées par Intune à Google

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quand la gestion des appareils Android Enterprise est activée sur un appareil, Microsoft Intune établit une connexion avec Google et partage les informations relatives aux utilisateurs et aux appareils avec Google. Pour que Microsoft Intune puisse établir une connexion, vous devez créer un compte Google.

Le tableau suivant répertorie les données que Microsoft Intune envoie à Google quand la gestion des appareils est activée sur un appareil :


| Données envoyées à Google | Détails | Rôle | Exemple |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Provient de Google après liaison de votre compte Gmail à Intune. | Identificateur principal utilisé pour communiquer entre Intune et Google.  Cette communication inclut la définition de stratégies, la gestion des appareils et la liaison/annulation de la liaison d’entreprise Android avec Intune. | Identificateur unique. Exemple de format : LC04eik8a6 |
| Corps de la stratégie | Provient d’Intune lors de l’enregistrement d’une nouvelle stratégie d’application ou de configuration. | Application de stratégies à des appareils. | Il s’agit d’une collection de tous les paramètres configurés pour une stratégie d’application ou de configuration. Ceci peut contenir des informations du client si elles sont fournies dans le cadre d’une stratégie, comme des noms de réseau, des noms d’application et des paramètres spécifiques à une application. |
| Données des appareils | Les scénarios des appareils pour les profils professionnels commencent par l’inscription dans Intune. Les scénarios des appareils pour les appareils gérés commencent par l’inscription dans Intune. | Des informations sur les données des appareils sont envoyées entre Intune et Google pour différentes actions, comme l’application de stratégies, la gestion de l’appareil et des rapports généraux. | **Identificateur unique pour représenter le nom de l’appareil.** Exemple : enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Identificateur unique pour représenter le nom de l’utilisateur.** Exemple : Enterprises/LC04ebru7b/users/116838519924207449711<br>**État de l’appareil.** Exemples : Actif, Désactivé, Provisionnement.<br>**État de la conformité.** Exemples : Paramètre non pris en charge, applications obligatoires manquantes<br>**Infos logiciel.** Exemples : versions des logiciels et niveau des correctifs logiciels.<br>**Infos réseau.** Exemples : Numéro IMEI, MEID, WifiMacAddress<br>**Paramètres de l’appareil.** Exemples : Informations sur les niveaux de chiffrement, et si appareil autorise les applications inconnues.<br> Vous pouvez trouver un exemple de message JSON ci-dessous. |
| newPassword | Provient d’Intune. | Réinitialisation du code secret de l’appareil. | Chaîne représentant le nouveau mot de passe. |
| Utilisateur Google | Google | Gestion du profil professionnel pour les scénarios Profil professionnel (BYOD). | Identificateur unique pour représenter le compte Gmail lié. Exemple : 114223373813435875042 |
| Données d'application | Proviennent d’Intune, lors de l’enregistrement d’une stratégie d’application. |  | Chaîne du nom d’application. Exemple : app:com.microsoft.windowsintune.companyportal |
| Compte de service d’entreprise | Provient de Google, suite à une demande d’Intune. | Utilisé pour l’authentification entre Intune et Google, pour les transactions impliquant ce client. | Constitué de plusieurs parties :<br> **Id d’entreprise** : déjà documenté.<br>**UPN** : UPN généré utilisé dans l’authentification pour le compte du client.<br>Exemple : w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Clé** : objet blob codé en Base64 utilisé dans les demandes d’authentification, stocké chiffré dans le service. Voici à quoi ressemble cet objet blob :<br> Identificateur unique pour représenter la clé du client<br>Exemple : a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Pour cesser d’utiliser la gestion des appareils Android Enterprise avec Microsoft Intune et supprimer les données, vous devez à la fois désactiver la gestion des appareils Android Enterprise de Microsoft Intune et supprimer votre compte Google. Reportez-vous au compte Google pour savoir comment effectuer la gestion du compte.


