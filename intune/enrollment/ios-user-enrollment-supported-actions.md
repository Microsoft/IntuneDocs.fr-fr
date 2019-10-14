---
title: Actions et options Intune prises en charge par l’inscription des utilisateurs d’Apple
titleSuffix: Microsoft Intune
description: Découvrez les actions et options Intune prises en charge par l’inscription des utilisateurs d’Apple
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: acf1112f96b28b156b3c4857485de30d7ad553ef
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955247"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Actions et options Intune prises en charge par l’inscription des utilisateurs d’Apple

L'inscription des utilisateurs prend en charge un sous-ensemble d'options de gestion des appareils. Si un profil de configuration préexistant est appliqué à un appareil avec inscription des utilisateurs, seuls les paramètres pris en charge par l'inscription des utilisateurs seront appliqués à cet appareil.

## <a name="password-settings"></a>Paramètres de mot de passe

Sur les appareils avec inscription des utilisateurs, si vous configurez un paramètre de mot de passe, le paramètre **Mots de passe simples** est automatiquement défini sur **Bloquer**, et un code PIN à 6 chiffres est appliqué.

Par exemple, vous configurez le paramètre **Expiration du mot de passe** et envoyez cette stratégie aux appareils avec inscription des utilisateurs. Sur les appareils, les événements suivants se produisent :
- Le paramètre **Expiration du mot de passe** est ignoré.
- Les mots de passe simples comme `1111` ou `1234` ne sont pas autorisés.
- Un code PIN à 6 chiffres est appliqué.

## <a name="administrator-remote-device-actions-and-options"></a>Actions et options de l'administrateur des appareils distants
Les administrateurs peuvent effectuer les actions et options suivantes sur les appareils avec inscription des utilisateurs :
- Mettre hors service
- Supprimer
- Verrouillage à distance
- Synchronisation

Toutes les autres actions ne sont pas prises en charge.

## <a name="end-user-actions"></a>Actions de l’utilisateur final
Sur les appareils avec inscription des utilisateurs, les utilisateurs finaux peuvent effectuer ces actions sur leurs appareils à partir de l'application Portail d'entreprise et du site Web :
- Renommer. Cette action ne s'applique qu'au nom d'utilisateur dans le Portail d'entreprise. Elle ne renommera pas complètement l’appareil en dehors de ce contexte.
- Supprimer
- Verrouillage à distance
- Vérifier le statut

## <a name="other-supported-options"></a>Autres options prises en charge

Les options suivantes sont prises en charge dans Intune pour les appareils inscrits avec l'inscription des utilisateurs d’Apple :
- VPN par application Cette prise en charge exclut les domaines Safari car l'inscription des utilisateurs ne prend pas en charge la configuration des paramètres Safari.
- Wi-Fi 
- Suppression d'une application d'entreprise lors de la désinscription
- Déploiement d’une application via un Programme d'achat en volume (VPP) sous licence utilisateur
- Détection de jailbreak

Les restrictions suivantes sont prises en charge :
- Afficher des documents d’entreprise dans les applications non gérées
- Affichage de documents externes à l’entreprise dans les applications d’entreprise
- Autoriser les applications non gérées à lire à partir de comptes de contacts gérés
- AirDrop comme une destination non gérée
- Sauvegarde chiffrée exigée
- Applications gérées synchronisées avec le cloud
- Accès au centre de contrôle quand l’appareil est verrouillé
- Accès au Centre de notifications quand l’appareil est verrouillé
- Mode Aujourd’hui quand l’appareil est verrouillé
- Bloquer les captures d’écran
- Bloquer la sauvegarde des livres d’entreprise
- Bloquer la synchronisation des métadonnées des livres d’entreprise
- Exiger la sauvegarde chiffrée
- Exiger la détection de la montre au poignet
- Bloquer Siri
- Bloquer Siri quand l’appareil est verrouillé
- Exiger des avertissements de fraude Safari
- Bloquer l’envoi des diagnostics à Apple


## <a name="options-not-supported"></a>Options non prises en charge
Les options suivantes ne sont pas prises en charge sur les appareils inscrits avec l'inscription des utilisateurs. Si vous avez besoin de ces options, consultez les rubriques consacrées à l’inscription des appareils personnels ou à l’inscription automatique des appareils appartenant à l'entreprise.
- Collecter l'inventaire des applications pour les applications en dehors du volume APFS géré.
- Collecter l'inventaire des certificats et des profils d'approvisionnement en dehors du volume APFS géré.
- Collecter les UDID et autres identificateurs d'appareils persistants.
- L'inscription des utilisateurs prend en charge un ID d'inscription unique pour chaque appareil inscrit, mais cet ID n’est pas conservé après la désinscription.
- Les fonctionnalités Intune suivantes ne sont pas prises en charge à cause de cette limitation :
- Profils d'utilisateur SCEP avec format du nom de l’objet de type Numéro de série.
- VPN au niveau de l'appareil.
- Déploiement d'applications VPP sous licence.
- Contrôle MDM des applications en dehors du volume APFS géré.
- Les stratégies de protection des applications s'appliqueront toujours à ces applications. Cependant, vous ne pourrez pas prendre en charge la gestion ou déployer une version gérée de ces applications, à moins que l'utilisateur ne les supprime de son appareil.
- Actions, configurations, paramètres et commandes nécessitant une supervision. 

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’inscription des utilisateurs iOS et iPadOS](ios-user-enrollment.md)