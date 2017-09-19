---
title: "Restrictions d'appareil Intune pour Windows 10 Collaboration"
titlesuffix: Azure portal
description: "Découvrez les restrictions d’appareils disponibles pour les appareils Windows 10 Collaboration."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0826b57656a756cf0a9f57a4b02b734a23b2919
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2017
---
# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Paramètres de restriction des appareils Windows 10 Collaboration dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="apps-and-experience"></a>Applications et expérience

- **Sortir l'écran du mode veille quand une personne est dans la pièce** - Permet à l’appareil de sortir automatiquement quand son capteur détecte la présence d’une personne dans la pièce.
- **Informations sur la réunion affichées sur l’écran d’accueil** - Activez cette option pour choisir les informations qui s’affichent sur la vignette Réunions de l’écran d’accueil. Vous pouvez :
    - **Afficher uniquement l’organisateur et l’heure**
    - **Afficher l’organisateur, l’heure et l’objet (objet masqué pour les réunions privées)**
- **URL de l'image d'arrière-plan de l'écran d'accueil** - Activez ce paramètre pour afficher un arrière-plan personnalisé sur l’écran **Bienvenue** des appareils Windows 10 Collaboration à partir de l’URL que vous spécifiez.<br>L’image doit être au format PNG et l’URL doit commencer par **https://**.

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights** - Azure Operational Insights, qui fait partie de la suite Microsoft Operations Manager, collecte, stocke et analyse les données des fichiers journaux provenant d’appareils Windows 10 Collaboration.
Pour vous connecter à Azure Operational insights, vous devez spécifier un **ID d’espace de travail** et une **Clé d’espace de travail**.

## <a name="maintenance"></a>Maintenance

- **Fenêtre de maintenance pour les mises à jour** - Configure la fenêtre quand des mises à jour peuvent avoir lieu sur l’appareil. Vous pouvez configurer l’**Heure de début** de la fenêtre et la **Durée en heures** (de 1 à 5 heures).

## <a name="wireless-projection"></a>Projection sans fil

- **Code confidentiel pour la projection sans fil** - Indique si vous devez entrer un code confidentiel avant de pouvoir utiliser les fonctionnalités de projection sans fil de l’appareil.
- **Projection sans fil Miracast** - Si vous voulez que l’appareil Windows 10 Collaboration utilise des appareils activés pour Miracast pour la projection, sélectionnez cette option.
- **Canal de projection sans fil Miracast** -Choisissez le canal Miracast qui va servir à établir la connexion.


## <a name="next-steps"></a>Étapes suivantes

Aidez-vous des informations contenues dans le [Guide pratique pour configurer des paramètres de restriction d’appareils](device-restrictions-configure.md) pour enregistrer et affecter le profil à des utilisateurs et appareils.
