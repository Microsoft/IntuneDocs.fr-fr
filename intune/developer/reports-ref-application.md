---
title: Informations de référence sur les entités d’application
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Application de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 1e737f1cce594b5dd40b2f43048ba37578f5d7c9
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940442"
---
# <a name="reference-for-application-entities"></a>Informations de référence sur les entités d’application

La catégorie **Application** contient des entités pour appareils mobiles qui font le suivi d’informations, notamment les suivantes :

- Versions d’une application
- Source d’installation d’une application
- Type de développeur à l’origine d’une application
- Types de logiciels gérés pour une application, par exemple **sidecar** ou **desktop**
- État du programme d’achat en volume (VPP) d’une application

## <a name="apprevisions"></a>appRevisions

Les listes d’entités **appRevision** répertorient toutes les versions des applications.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| appKey |Identificateur unique de l’application. |123 |
| applicationId |Identificateur unique de l’application (semblable à AppKey, mais il s’agit d’une clé naturelle) |b66bc706-ffff-7437-0340-032819502773 |
| revision |Version mentionnée par l’administrateur durant le chargement du binaire. |2 |
| title |Titre de l’application. |Excel |
| publisher |Éditeur de l’application. |Microsoft |
| uploadState |État de chargement de l’application. |1 |
| appTypeKey |Référence à AppType décrite dans la section suivante | |
| vppProgramTypeKey |Référence à VppProgramType décrite ci-dessous. | |
| creationTime |Heure de création de cette révision. |11/23/2016 12:00:00 AM |
| modifiedTime |Heure du dernier changement apporté à cette révision. |11/23/2016 12:00:00 AM |
| est |Taille du binaire. | |
| startDateInclusiveUTC |Date et heure UTC de création de la révision de cette application dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| endDateExclusiveUTC |Date et heure UTC correspondant au moment auquel cette révision d’application est devenue obsolète. |11/23/2016 12:00:00 AM |
| isCurrent |Indique si cette version de l’application est active ou non dans l’entrepôt de données. |Vrai/Faux |
| rowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cette version d’application dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="apptypes"></a>appTypes

L’entité **appTypes** répertorie la source d’installation d’une application.

| Propriété  | Description |
|---------|------------|
| appTypeID |ID du type |
| appTypeKey |Clé de substitution pour la clé |
| appTypeName |Type d’application |

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


## <a name="vppprogramtypes"></a>vppProgramTypes

L’entité **VppProgramTypes** répertorie les types de VPP possibles pour une application.

| Propriété  | Description |
|---------|------------|
| vppProgramTypeID | ID du type. |
| vppProgramTypeKey | Clé de substitution pour la clé. |
| vppProgramTypeName | Type de programme VPP. |

### <a name="example"></a>Exemple

| VppProgramID  | Nom | Description |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programme VPP Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Pas encore disponible | Valeur par défaut : aucun VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programme VPP Apple. |



## <a name="applicationinventories"></a>applicationInventories

L’entité **applicationInventory** répertorie les applications trouvées sur l’appareil au moment du regroupement d’inventaire.

| Propriété  | Description |
|---------|------------|
| deviceKey | Il s’agit d’une référence à la table d’appareils qui contient l’ID d’appareil Intune. |
| dateKey | Référence à la table de dates indiquant le jour de l’inventaire. |
| applicationName | Nom de l’application. |
| applicationVersion | Version de l’application. |
| bundleSize | Taille de l’application en octets. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

L’entité **mobileAppInstallState** représente l’état d’installation d’une application mobile après qu’elle a été affectée à un groupe contenant des appareils, des utilisateurs ou les deux.

| Propriété | Description |
|---|---|
| appInstallStateKey | ID unique de l’état d’installation de l’application pour votre compte. |
| appInstallState | Valeur d’énumération de l’état d’installation de l’application. |
| appInstallStateName | Nom de l’état d’installation de l’application. |



