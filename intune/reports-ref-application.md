---
title: Informations de référence sur les entités d’application
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Application de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1ee376bdf2dff6dc59b6c51b20ff87c1ed81d82
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549233"
---
# <a name="reference-for-application-entities"></a>Informations de référence sur les entités d’application

La catégorie **Application** contient des entités pour appareils mobiles qui font le suivi d’informations, notamment les suivantes :

  - Versions d’une application
  - Source d’installation d’une application
  - Type de développeur à l’origine d’une application
  - Types de logiciels gérés pour une application, par exemple **sidecar** ou **desktop**
  - État du programme d’achat en volume (VPP) d’une application

## <a name="apprevision"></a>AppRevision

L’entité **AppRevision** répertorie toutes les versions des applications.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| AppKey |Identificateur unique de l’application. |123 |
| ApplicationId |Identificateur unique de l’application (semblable à AppKey, mais il s’agit d’une clé naturelle) |b66bc706-ffff-7437-0340-032819502773 |
| Révision |Version mentionnée par l’administrateur durant le chargement du binaire. |2 |
| Titre |Titre de l’application. |Excel |
| Éditeur |Éditeur de l’application. |Microsoft |
| UploadState |État de chargement de l’application. |1 |
| AppTypeKey |Référence à AppType décrite dans la section suivante | |
| VppProgramTypeKey |Référence à VppProgramType décrite ci-dessous. | |
| CreationTime |Heure de création de cette révision. |11/23/2016 12:00:00 AM |
| ModifiedTime |Heure du dernier changement apporté à cette révision. |11/23/2016 12:00:00 AM |
| Size |Taille du binaire. | |
| StartDateInclusiveUTC |Date et heure UTC de création de la révision de cette application dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Date et heure UTC correspondant au moment auquel cette révision d’application est devenue obsolète. |11/23/2016 12:00:00 AM |
| IsCurrent |Indique si cette version de l’application est active ou non dans l’entrepôt de données. |Vrai/Faux |
| RowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cette version d’application dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>AppTypes

L’entité **AppTypes** répertorie la source d’installation d’une application.

| Propriété  | Description |
|---------|------------|
| AppTypeID |ID du type |
| AppTypeKey |Clé de substitution pour la clé |
| AppTypeName |Type d’application |

### <a name="example"></a>Exemple

| AppTypeID  | Nom | Description |
|---------|------------|--------|
| 0 |Application de l’Android Store | Application de l’Android Store. |
| 1 |Application métier Android | Application métier Android. |
| 2 |Application de l’Android Store gérée (GAM) | Application de l’Android Store activée pour la gestion. |
| 3 |Application de l’App Store iOS | Application de l’App Store iOS. |
| 4 |Application métier iOS | Application métier iOS. |
| 5 |Application de l’App Store iOS gérée (GAM ?) | Application de l’App Store iOS activée pour la gestion. |
| 6 |Office 365 Pro Plus Suite | Office 365 Pro Plus Suite pour Windows 10. |
| 7 |Application web | Application web. |
| 8 |Application du Windows Phone 8.1 Store | Application du Windows Phone 8.1 Store. |
| 9 |Application du Windows Store | Application du Windows Store. |
| 10 |Applications métier Windows | Application métier AppX Windows. |
| 11 |Windows Mobile MSI | Application métier MSI. |
| 12 |Application métier Windows Phone | Application métier Windows Phone. |


## <a name="vppprogramtypes"></a>VppProgramTypes

L’entité **VppProgramTypes** répertorie les types de VPP possibles pour une application.

| Propriété  | Description |
|---------|------------|
| VppProgramTypeID | ID du type. |
| VppProgramTypeKey | Clé de substitution pour la clé. |
| VppProgramTypeName | Type de programme VPP. |

### <a name="example"></a>Exemple

| VppProgramID  | Nom | Description |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programme VPP Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Pas encore disponible | Valeur par défaut : aucun VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programme VPP Apple. |



## <a name="applicationinventory"></a>ApplicationInventory

L’entité **ApplicationInventory** répertorie les applications trouvées sur l’appareil au moment du regroupement d’inventaire.

| Propriété  | Description |
|---------|------------|
| DeviceKey | Il s’agit d’une référence à la table d’appareils qui contient l’ID d’appareil Intune. |
| DateKey | Référence à la table de dates indiquant le jour de l’inventaire. |
| ApplicationName | Nom de l’application. |
| ApplicationVersion | Version de l’application. |
| BundleSize | Taille de l’application en octets. |

## <a name="mobileappinstallstate"></a>MobileAppInstallState

L’entité **MobileAppInstallState** représente l’état d’installation d’une application mobile qui a été affectée à un groupe contenant des appareils, des utilisateurs ou les deux.

| Propriété | Description |
|---|---|
| AppInstallStateKey | ID unique de l’état d’installation de l’application pour votre compte. |
| AppInstallState | Valeur d’énumération de l’état d’installation de l’application. |
| AppInstallStateName | Nom de l’état d’installation de l’application. |



