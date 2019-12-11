---
title: 'Association appareil-utilisateur : Entrepôt de données Intune'
titleSuffix: Microsoft Intune
description: L’entité UserDeviceAssociation contient les associations appareil-utilisateur dans votre organisation.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f04575ce32d3d02a1869ed8c3225905b9e6b7dc
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899272"
---
# <a name="reference-for-user-device-association-entity"></a>Informations de référence sur l’entité Association appareil-utilisateur

L’entité **userDeviceAssociation** contient les associations appareil-utilisateur dans votre organisation.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Nom        |                                           Description                                            |        Exemple         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Identificateur unique de l’utilisateur dans l’entrepôt de données. (Clé de substitution).               |          123           |
|     deviceKey      |                      Identificateur unique de l’appareil dans l’entrepôt de données.                      |          123           |
| createdDateTimeUTC |           Date et heure auxquelles l’association appareil-utilisateur a été créée. Utilise le format UTC.           | 11/23/2016 12:00:00 AM |
|     isDeleted      | Indique que l’utilisateur a désinscrit cet appareil et que l’association n’est plus d’actualité. |       Vrai/Faux       |
|  endedDateTimeUTC  |              Date et heure UTC à laquelle IsDeleted est passé à <strong>True</strong>.               | 23/06/2017 00:00:00 |

## <a name="next-steps"></a>Étapes suivantes

- Apprenez en plus sur [l’entrepôt de données Intune](../reports-nav-create-intune-reports.md).
