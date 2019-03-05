---
title: 'Association appareil-utilisateur : Entrepôt de données Intune'
titlesuffix: Microsoft Intune
description: L’entité UserDeviceAssociation contient les associations appareil-utilisateur dans votre organisation.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bff8e67a3c6df4364491ba1407aeaee43ff976c4
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236617"
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
