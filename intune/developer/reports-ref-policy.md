---
title: Informations de référence sur les entités de stratégie
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Stratégie de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fe4fabc86e7be647fa161d68fe8a4fe35e9eb6b
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654122"
---
# <a name="reference-for-policy-entities"></a>Informations de référence sur les entités de stratégie

La catégorie **policies** contient des entités pour appareils mobiles qui font le suivi d’informations, notamment les suivantes :

- Inventaire des profils de configuration d’appareil, des profils de configuration d’application et des stratégies de conformité  
- Nombre d’appareils, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur  
- Nombre d’appareils, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur  
- Nombre cumulé d’appareils dans un état de réussite, d’attente, d’échec ou d’erreur  

## <a name="policies"></a>stratégies

L’entité **policy** répertorie les profils de configuration d’appareil, les profils de configuration d’application et les profils de conformité. Vous pouvez affecter les stratégies à un groupe de votre entreprise à l’aide de la gestion des appareils mobiles (MDM).

| Propriété  | Description | Exemple |
|---------|------------|--------|
| policyKey |Clé unique représentant la stratégie dans l’entrepôt de données. |123 |
| policyId |Identificateur unique de la stratégie dans l’entrepôt de données. |b66bc706-ffff-7437-0340-032819502773 |
| policyName |Nom de la stratégie. |« Ligne de base Windows 10 » |
| policyVersion |Version de la stratégie. Quand la stratégie est modifiée ou changée, une version plus récente est créée. |1, 2, 3 |
| isDeleted |Indique si l’enregistrement de stratégie a été mis à jour.  <br>True : la stratégie a un nouvel enregistrement avec des champs mis à jour. <br>False : dernier enregistrement de la stratégie. |Vrai/Faux |
| startDateInclusiveUTC |Date et heure UTC de création de la stratégie dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| deletedDateUTC |Date et heure UTC de l’affectation de la valeur True à IsDeleted. |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de la stratégie dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="policytypes"></a>policyTypes

L’entité **policyType** répertorie les types de profils de configuration d’appareil, de profils de configuration d’application et de profils de conformité. Vous pouvez affecter les stratégies à un groupe de votre entreprise à l’aide de la gestion des appareils mobiles (MDM).

| Propriété  | Description | Exemple |
|---------|------------|--------|
| policyTypeId |Identificateur unique de la stratégie dans le système source. |123 |
| policyTypeKey |Identificateur unique de la stratégie dans l’entrepôt de données. |1 |
| policyTypeName |Nom du type de stratégie |Stratégie de conformité Windows 10. |

## <a name="device-configuration"></a>Configuration des appareils

L’entité **deviceConfigurationProfileDeviceActivity** répertorie le nombre **d’appareils** dans un état de réussite, d’attente, d’échec ou d’erreur, par jour. Le nombre reflète les profils de configuration d’appareil affectés à l’entité. Par exemple, si toutes les stratégies affectées à un **appareil** sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si deux profils sont affectés à un appareil, l’un dans un état de réussite et l’autre dans un état d’erreur, l’entité incrémente le compteur de réussite et affecte à l’appareil un état d’erreur. L’entité répertorie le nombre d’appareils dans chaque état pour un jour donné au cours des 30 derniers jours.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| dateKey |Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données. |20160703 |
| en attente |Nombre d’appareils uniques en état d’attente. |123 |
| réussi |Nombre d’appareils uniques en état de réussite. |12 |
| erreur |Nombre d’appareils uniques en état d’erreur. |10 |
| échec |Nombre d’appareils uniques en état d’échec. |2 |

L’entité **deviceConfigurationProfileUserActivity** répertorie le nombre **d’utilisateurs** dans un état de réussite, d’attente, d’échec ou d’erreur, par jour. Le nombre reflète les profils de configuration d’appareil affectés à l’entité. Par exemple, si toutes les stratégies affectées à un **utilisateur** sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si un utilisateur a deux profils affectés, l’un dans un état de réussite et l’autre dans un état d’erreur, l’utilisateur dans l’état d’erreur est pris en compte.  L’entité **deviceConfigurationProfileUserActivity** répertorie le nombre d’utilisateurs dans chaque état pour un jour donné au cours des 30 derniers jours.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| dateKey |Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données. |20160703 |
| en attente |Nombre d’utilisateurs uniques en état d’attente. |123 |
| réussi |Nombre d’utilisateurs uniques en état de réussite. |12 |
| erreur |Nombre d’utilisateurs uniques en état d’erreur. |10 |
| échec |Nombre d’utilisateurs uniques en état d’échec. |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

L’entité **policyTypeActivity** répertorie le nombre cumulé d’appareils dans un état de réussite, d’attente, d’échec ou d’erreur. Elle répertorie ces états, par jour, par rapport à un profil de configuration d’appareil, un profil de configuration d’application ou une stratégie de conformité.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| dateKey |Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil a été enregistré dans l’entrepôt de données. |20160703 |
| policyKey |Clé de stratégie pouvant être jointe à la stratégie pour obtenir le nom de l’entité policyName. |Ligne de base Windows 10 |
| policyTypeKey |Type de clé de stratégie pouvant être joint au type de stratégie pour obtenir le nom du type de la stratégie. |Stratégie de conformité Windows 10 |
| en attente |Nombre d’appareils uniques en état d’attente. |123 |
| réussi |Nombre d’appareils uniques en état de réussite. |12 |
| erreur |Nombre d’appareils uniques en état d’erreur. |10 |
| échec |Nombre d’appareils uniques en état d’échec. |2 |

## <a name="compliance-policy"></a>Stratégie de conformité

Les informations de référence de l’API de stratégie de conformité contiennent des entités qui fournissent des informations sur l’état des stratégies de conformité affectées aux appareils.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

Le tableau suivant récapitule l’état d’affectation des stratégies de conformité pour les appareils. Il répertorie le nombre d’appareils dans chaque état de conformité.


|Propriété     |Description  |Exemple  |
|---------|---------|---------|
|dateKey  |Clé de date à la création du récapitulatif pour la stratégie de conformité.|20161204 |
|unknown  |Nombre d’appareils hors connexion ou qui n’ont pas pu communiquer avec Intune ou Azure AD pour d’autres raisons. |5|
|notApplicable      |Nombre d’appareils pour lesquelles des stratégies de conformité ciblées par l’administrateur ne sont pas applicables.|201 |
|compliant      |Nombre d’appareils qui ont appliqué une ou plusieurs stratégies de conformité d’appareil ciblées par l’administrateur. |4083 |
|inGracePeriod      |Nombre d’appareils qui ne sont pas conformes, mais se trouvent dans la période de grâce définie par l’administrateur. |57|
|nonCompliant      |Nombre d’appareils qui n’ont pas pu appliquer une ou plusieurs stratégie de conformité d’appareil ciblées par l’administrateur ou dont l’utilisateur n’a pas respecté les stratégies ciblées par l’administrateur.|43 |
|erreur      |Nombre d’appareils qui n’ont pas pu communiquer avec Intune ou Azure AD et ont retourné un message d’erreur. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

Le tableau suivant récapitule l’état d’affectation des stratégies de conformité pour les appareils par stratégie et par type de stratégie. Il répertorie le nombre d’appareils dans chaque état de conformité pour chaque stratégie de conformité affectée.



|Propriété  |Description  |Exemple  |
|---------|---------|---------|
|dateKey  |Clé de date à la création du récapitulatif pour la stratégie de conformité.|20161219|
|policyKey     |Clé de la stratégie de conformité pour laquelle le récapitulatif a été créé. |10178 |
|policyPlatformKey      |Clé du type de plateforme de la stratégie de conformité pour laquelle le récapitulatif a été créé.|5|
|unknown     |Nombre d’appareils hors connexion ou qui n’ont pas pu communiquer avec Intune ou Azure AD pour d’autres raisons.|13|
|notApplicable     |Nombre d’appareils pour lesquelles des stratégies de conformité ciblées par l’administrateur ne sont pas applicables.|3|
|compliant      |Nombre d’appareils qui ont appliqué une ou plusieurs stratégies de conformité d’appareil ciblées par l’administrateur. |45|
|inGracePeriod      |Nombre d’appareils qui ne sont pas conformes, mais se trouvent dans la période de grâce définie par l’administrateur. |3|
|nonCompliant      |Nombre d’appareils qui n’ont pas pu appliquer une ou plusieurs stratégie de conformité d’appareil ciblées par l’administrateur ou dont l’utilisateur n’a pas respecté les stratégies ciblées par l’administrateur.|7|
|erreur      |Nombre d’appareils qui n’ont pas pu communiquer avec Intune ou Azure AD et ont retourné un message d’erreur. |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

Le tableau suivant contient les types de plateforme de toutes les stratégies affectées. Les types de plateformes de stratégies qui n’ont jamais été affectés à un appareil ne sont pas présents dans ce tableau.


|Propriété  |Description  |Exemple  |
|---------|---------|---------|
|policyPlatformTypeKey      |Clé unique du type de plateforme de stratégie. |20170519 |
|policyPlatformTypeId      |Identificateur unique du type de plateforme de stratégie.|1|
|policyPlatformTypeName      |Nom du type de plateforme de stratégie.|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

Le tableau suivant répertorie le nombre d’appareils, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur. Le nombre reflète les données par profil de type de stratégie. Par exemple, si toutes les stratégies affectées à un appareil sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si deux profils sont affectés à un appareil, l’un dans un état de réussite et l’autre dans un état d’erreur, l’entité incrémente le compteur de réussite et affecte à l’appareil un état d’erreur. L’entité policyDeviceActivity répertorie le nombre d’appareils dans chaque état à une date donnée au cours des 30 derniers jours.

|Propriété  |Description  |Exemple  |
|---------|---------|---------|
|dateKey|Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données.|20160703|
|en attente|Nombre d’appareils uniques en état d’attente.|123|
|Succès|Nombre d’appareils uniques en état de réussite.|12|
|policyKey|Clé de stratégie pouvant être jointe à la stratégie pour obtenir le nom de l’entité policyName.|Ligne de base Windows 10|
|erreur|Nombre d’appareils uniques en état d’erreur.|10|
|échec|Nombre d’appareils uniques en état d’échec.|2|

### <a name="policyuseractivities"></a>policyUserActivities

Le tableau suivant répertorie le nombre d’utilisateurs, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur. Le nombre reflète les données par profil de type de stratégie. Par exemple, si toutes les stratégies affectées à un utilisateur sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si un utilisateur a deux profils affectés, l’un dans un état de réussite et l’autre dans un état d’erreur, l’utilisateur dans l’état d’erreur est pris en compte. L’entité PolicyUserActivity répertorie le nombre d’utilisateurs dans chaque état pour un jour donné au cours des 30 derniers jours.


| Propriété  |                                         Description                                         |       Exemple       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données. |      20160703       |
|  en attente  |                         Nombre d’appareils uniques en état d’attente.                          |         123         |
| réussi |                         Nombre d’appareils uniques en état de réussite.                          |         12          |
| policyKey |                 Clé de stratégie pouvant être jointe à la stratégie pour obtenir le nom de l’entité policyName.                 | Ligne de base Windows 10 |
|   erreur   |                          Nombre d’appareils uniques en état d’erreur.                           |         10          |

