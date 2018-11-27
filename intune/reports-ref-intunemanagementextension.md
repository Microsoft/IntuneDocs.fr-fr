---
title: Entité IntuneManagementExtension
titlesuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie d’entités IntuneManagementExtension dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 48e08b93468fb177fd3a724e5bcc6758cf262e99
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189365"
---
# <a name="reference-for-intune-management-extension"></a>Informations de référence sur l’extension de la gestion Intune

La catégorie **IntuneManagementExtension** contient des entités pour les appareils mobiles qui font le suivi d’informations telles que :

  -  Versions d’une IntuneManagementExtension
  -  État de l’installation d’une IntuneManagementExtension

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

L’entité **IntuneManagementExtensionVersion** liste toutes les versions utilisées par IntuneManagementExtension.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| ExtensionVersionKey |Identificateur unique de la version IntuneManagementExtension. | 1 |
| ExtensionVersion |Numéro de version à quatre chiffres. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState** liste tous les états d’intégrité possibles de l’IntuneManagementExtension.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| ExtensionStateKey |Identificateur unique de l’état d’intégrité. | 2 |
| ExtensionState |État d’intégrité d’une IntuneManagementExtension. | Healthy |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

**IntuneManagementExtension** liste l’intégrité d’IntuneManagementExtension sur chaque appareil Windows 10 par jour.
Les données sont conservées pendant les 60 derniers jours. 


|      Propriété       |                         Description                         | Exemple |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Identificateur unique de la date.                |   123   |
|      TenantKey      |              Identificateur unique du locataire.               |   456   |
|      DeviceKey      |              Identificateur unique de l’appareil.               |   789 %   |
| ExtensionVersionKey | Identificateur unique de la version IntuneManagementExtension. |    1    |
|  ExtensionStateKey  |             Identificateur unique de l’état d’intégrité.              |    2    |

