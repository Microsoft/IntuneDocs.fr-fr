---
title: Entité IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie d’entités IntuneManagementExtension dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae99e747f9c0540418c15f24fbe0c27c585f869c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490309"
---
# <a name="reference-for-intune-management-extensions"></a>Informations de référence sur les extensions de la gestion Intune

La catégorie **intuneManagementExtensions** contient des entités pour les appareils mobiles qui font le suivi d’informations telles que :

- Versions d’une IntuneManagementExtension
- État de l’installation d’une IntuneManagementExtension

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

L’entité **intuneManagementExtensionVersion** répertorie toutes les versions utilisées par intuneManagementExtensions.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| extensionVersionKey |Identificateur unique de la version intuneManagementExtensions. | 1 |
| extensionVersion |Numéro de version à quatre chiffres. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

**intuneManagementExtensionHealthState** répertorie tous les états d’intégrité possibles d’intuneManagementExtensions.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| extensionStateKey |Identificateur unique de l’état d’intégrité. | 2 |
| extensionState |État d’intégrité d’une IntuneManagementExtension. | Healthy |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

**intuneManagementExtension** répertorie l’intégrité d’IntuneManagementExtensions sur chaque appareil Windows 10 par jour.
Les données sont conservées pendant les 60 derniers jours. 


|      Propriété       |                         Description                         | Exemple |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               Identificateur unique de la date.                |   123   |
|      tenantKey      |              Identificateur unique du locataire.               |   456   |
|      deviceKey      |              Identificateur unique de l’appareil.               |   789 %   |
| extensionVersionKey | Identificateur unique de la version intuneManagementExtension. |    1    |
|  extensionStateKey  |             Identificateur unique de l’état d’intégrité.              |    2    |

