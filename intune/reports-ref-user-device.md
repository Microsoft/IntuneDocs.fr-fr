---
title: 'Association appareil-utilisateur : Entrepôt de données Intune'
titlesuffix: Microsoft Intune
description: L’entité UserDeviceAssociation contient les associations appareil-utilisateur dans votre organisation.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.openlocfilehash: 02c579a7371a59a46cfb0017e6aa1a17af92bd03
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429557"
---
# <a name="reference-for-user-device-association-entity"></a>Informations de référence sur l’entité Association appareil-utilisateur

L’entité **UserDeviceAssociation** contient les associations appareil-utilisateur dans votre organisation.

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        Nom        |                                           Description                                            |        Exemple         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Identificateur unique de l’utilisateur dans l’entrepôt de données. (Clé de substitution).               |          123           |
|     DeviceKey      |                      Identificateur unique de l’appareil dans l’entrepôt de données.                      |          123           |
| CreatedDateTimeUTC |           Date et heure auxquelles l’association appareil-utilisateur a été créée. Utilise le format UTC.           | 11/23/2016 12:00:00 AM |
|     IsDeleted      | Indique que l’utilisateur a désinscrit cet appareil et que l’association n’est plus d’actualité. |       Vrai/Faux       |
|  EndedDateTimeUTC  |              Date et heure UTC à laquelle IsDeleted est passé à <strong>True</strong>.               | 23/06/2017 00:00:00 |

## <a name="next-steps"></a>Étapes suivantes

- Apprenez en plus sur [l’entrepôt de données Intune](reports-nav-create-intune-reports.md).