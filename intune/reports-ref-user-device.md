---
title: 'Association appareil-utilisateur : Entrepôt de données Intune'
titleSuffix: Microsoft Intune
description: L’entité UserDeviceAssociation contient les associations appareil-utilisateur dans votre organisation.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8d24716f65d5ff8afba5fc0a89cfef082712429
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313667"
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

- Apprenez en plus sur [l’entrepôt de données Intune](reports-nav-create-intune-reports.md).
