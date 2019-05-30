---
title: Données envoyées par JAMF Pro à Intune
titleSuffix: Microsoft Intune
description: Liste des données envoyées par Jamf Pro à Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 287ed06ddab0b98117aa4a75942087f360e4656d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048550"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Données envoyées par Jamf Pro à Intune

Quand vous utilisez [Jamf Pro](https://www.jamf.com) pour gérer vos ordinateurs Mac pour utilisateurs finaux avec Intune, Jamf Pro capture des données d’inventaire sur les appareils macOS gérés. Jamf Pro fournit les informations suivantes à Intune :

* ID d’appareil Azure AD
* État de l’inventaire Jamf (état de l’inventaire d’un ordinateur enregistré auprès de Jamf Pro au cours des dernières 24 heures)
* Version de système d'exploitation
* ID d’utilisateur Azure AD
* Chiffré (FileVault 2)
* État de l’opérateur de contrôle d’appels
* Mot de passe : nombre minimal de jeux de caractères
* Expiration du mot de passe (jours)
* Type de mot de passe : simple, alphanumérique ou inconnu
* Empêcher la connexion automatique
* Longueur de mot de passe requise
* Mot de passe : nombre de mots de passe précédents pour empêcher la réutilisation
* Protection de l’intégrité du système
* Dernière heure d’enregistrement
* Type d’architecture
* Emplacements de mémoire RAM disponibles
* Capacité de la batterie
* ROM de démarrage
* Vitesse du bus
* Taille de cache
* Nom de l'appareil
* Jonction de domaine
* ID Jamf
* Adresse MAC
* Make
* Modèle
* Identificateur du modèle
* Vitesse de la carte réseau
* Nombre de cœurs
* Nombre de processeurs
* Système d’exploitation
* Plate-forme
* vitesse du processeur
* Type de processeur
* Adresse MAC secondaire
* Numéro de série
* Version SMC
* RAM totale
* UDID
* Adresse e-mail de l’utilisateur


Vous pouvez supprimer un appareil géré par Jamf dans la console Intune en sélectionnant **Supprimer** dans l’affichage **Tous les appareils**. Pour supprimer des appareils en bloc, sélectionnez les appareils concernés, puis cliquez sur **Supprimer**.

Vous pouvez obtenir des informations sur la façon de [supprimer un appareil géré par Jamf dans la documentation de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Vous pouvez aussi ouvrir un ticket de support auprès du [Support Jamf](https://www.jamf.com/support/) pour obtenir une aide supplémentaire. 

