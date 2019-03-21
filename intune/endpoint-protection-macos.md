---
title: Ajouter Endpoint Protection sur macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils macOS, utilisez Gatekeeper pour déterminer l’emplacement où les applications peuvent être installées, notamment le Mac App Store. Activez ou configurez également un pare-feu pour autoriser ou bloquer des applications spécifiques, utiliser le mode furtif et même bloquer certains types de connexion entrante à l’aide de Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2c3a33b996a68263550fc05d3af853c263c930a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565933"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Paramètres Endpoint Protection pour macOS dans Intune

Cet article décrit les paramètres Endpoint Protection que vous pouvez configurer pour les appareils macOS. Ces paramètres incluent les paramètres relatifs à Gatekeeper et au pare-feu sur ces appareils. Vous pouvez les configurer à l’aide d’un profil d’appareil dans Microsoft Intune.

## <a name="gatekeeper"></a>Gatekeeper

- **Autoriser les applications téléchargées à partir de ces emplacements** : permet de limiter les applications en fonction de leur emplacement de téléchargement. L’objectif est de protéger les appareils contre les programmes malveillants et d’autoriser uniquement les applications provenant de sources fiables. Options d’autorisation : 
  - **Mac App Store**
  - **Mac App Store et développeurs identifiés**
  - **Partout**

- **L’utilisateur peut remplacer Gatekeeper** : permet d’empêcher les utilisateurs de remplacer les paramètres Gatekeeper et d’appuyer de façon prolongée sur la touche Ctrl pour installer une application. Quand cette option est activée, les utilisateurs peuvent appuyer de façon prolongée sur la touche Ctrl en ciblant une application de leur choix pour installer cette dernière.

## <a name="firewall"></a>Pare-feu

Utilisez le pare-feu pour contrôler les connexions par application, et non par port. L’utilisation de paramètres par application permet de tirer parti plus facilement de la protection par pare-feu. Elle contribue également à empêcher les applications indésirables de prendre le contrôle des ports réseau ouverts pour les applications légitimes.

- **Utilisez un pare-feu pour protéger les appareils contre un accès réseau non autorisé en contrôlant les connexions par application.**
  - **Pare-feu** : activez le pare-feu pour configurer le mode de prise en charge des connexions entrantes dans votre environnement.
  - **Connexions entrantes** : bloquez toutes les connexions entrantes, à l’exception des connexions nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Cette fonctionnalité bloque également tous les services de partage, par exemple le partage de fichiers et le partage d’écran. Si vous utilisez des services de partage, conservez ce paramètre avec l’état **Non configuré**.

- **Autorisez ou bloquez les connexions entrantes pour des applications spécifiques**
  - **Applications autorisées** : sélectionnez les applications explicitement autorisées à recevoir des connexions entrantes.
  - **Applications bloquées** : sélectionnez les applications qui doivent bloquer les connexions entrantes.
  - **Mode furtif** : pour empêcher l’ordinateur de répondre aux demandes de sondage, activez le mode furtif. L’appareil continue de répondre aux requêtes entrantes des applications autorisées. Les demandes inattendues, comme ICMP (ping), sont ignorées.
