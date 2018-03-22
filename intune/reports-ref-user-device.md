---
title: 'Association appareil-utilisateur : Entrepôt de données Intune'
titlesuffix: Microsoft Intune
description: Liste des modifications dans l’API de l’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: de14444376cb2998f17f406f084c428523ef4e4f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2018
---
# <a name="user-device-association"></a>Association appareil-utilisateur

L’entité **UserDeviceAssociation** contient les associations appareil-utilisateur dans votre organisation.

| Nom               | Description                                                                                      | Exemple                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificateur unique de l’utilisateur dans l’entrepôt de données. (Clé de substitution).                              | 123                    |
| DeviceKey          | Identificateur unique de l’appareil dans l’entrepôt de données.                                            | 123                    |
| CreatedDateTimeUTC | Date et heure auxquelles l’association appareil-utilisateur a été créée. Utilise le format UTC.                                | 11/23/2016 12:00:00 AM |
| IsDeleted          | Indique que l’utilisateur a désinscrit cet appareil et que l’association n’est plus d’actualité. | Vrai/Faux             |
| EndedDateTimeUTC   | Date et heure UTC à laquelle IsDeleted est passé à **True**.                                              | 23/06/2017 00:00:00 |
