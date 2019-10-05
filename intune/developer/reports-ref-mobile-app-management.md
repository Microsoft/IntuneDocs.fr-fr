---
title: Gestion des applications mobiles (GAM)
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Gestion des applications mobiles de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f06d2b4b61d522dced12e5d08cd1e854aefd9de8
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939943"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Informations de référence sur les entités de gestion des applications mobiles (GAM)

La catégorie **Gestion des applications mobiles** contient des entités pour applications mobiles, par exemple :

- Applications
- Instances
- État de l’enregistrement
- État de l’intégrité
- État de la stratégie
- État de l'inscription
- Types de plateformes

## <a name="mamapplications"></a>mamApplications

L’entité **mamApplication** répertorie les applications métier qui sont gérées par le biais de la gestion des applications mobiles (GAM) sans inscription dans votre entreprise.

| Propriété | Description | Exemple |
|---------|------------|--------|
| mamApplicationKey |Identificateur unique de l’application MAM. | 432 |
| mamApplicationName |Nom de l’application MAM. |Exemple de nom d’application MAM |
| mamApplicationId |ID d’application de l’application MAM. | 123 |
| isDeleted |Indique si cet enregistrement d’application GAM a été mis à jour. <br>True : l’application GAM a un nouvel enregistrement avec des champs mis à jour dans cette table. <br>False : dernier enregistrement pour cette application GAM. |Vrai/Faux |
| startDateInclusiveUTC |Date et heure UTC de création de cette application MAM dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| deletedDateUTC |Date et heure UTC de l’affectation de la valeur True à IsDeleted. |11/23/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cette application MAM dans l’entrepôt de données. |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

L’entité **mamApplicationInstance** répertorie les applications GAM gérées comme instances singulières, par utilisateur et par appareil. Tous les utilisateurs et appareils répertoriés dans l’entité sont protégés si au moins une stratégie GAM leur est affectée.


|          Propriété          |                                                                                                  Description                                                                                                  |               Exemple                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               Identificateur unique de l’instance de l’application MAM dans l’entrepôt de données (clé de substitution).                                                                |                 123                  |
|           userId           |                                                                              ID de l’utilisateur ayant installé cette application MAM.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              Identificateur unique de l’instance de l’application MAM (semblable à ApplicationInstanceKey, mais l’identificateur est une clé naturelle).                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | ID d’application de l’application MAM pour laquelle cette instance de l’application MAM a été créée.   | 11/23/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     Version de cette application MAM.                                                                                      |                  2                   |
|        createdDate         |                                                                 Date de création de cet enregistrement de l’instance d’application GAM. La valeur peut être Null.                                                                 |        11/23/2016 12:00:00 AM        |
|          Plateforme          |                                                                          Plateforme de l’appareil sur lequel cette application MAM est installée.                                                                           |                  2                   |
|      platformVersion       |                                                                      Version de la plateforme de l’appareil sur lequel cette application MAM est installée.                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            Version du SDK MAM avec laquelle cette application MAM a été enveloppée (wrapped).                                                                            |                 3.2                  |
| mamDeviceId | ID d’appareil de l’appareil auquel l’instance de l’application MAM est associée.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | Type d’appareil de l’appareil auquel l’instance de l’application MAM est associée.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | Nom d’appareil de l’appareil auquel l’instance de l’application MAM est associée.   | 11/23/2016 12:00:00 AM   |
|         isDeleted          | Indique si l’enregistrement de cette application GAM a été mis à jour. <br>True : cette instance d’application GAM a un nouvel enregistrement avec des champs mis à jour dans cette table. <br>False : dernier enregistrement pour cette instance d’application GAM. |              Vrai/Faux              |
|   startDateInclusiveUtc    |                                                              Date et heure UTC de création de cette instance d’application MAM dans l’entrepôt de données.                                                               |        11/23/2016 12:00:00 AM        |
|       deletedDateUtc       |                                                                             Date et heure UTC de l’affectation de la valeur True à IsDeleted.                                                                              |        11/23/2016 12:00:00 AM        |
| rowLastModifiedDateTimeUtc |                                                           Date et heure UTC de la dernière modification de cette instance d’application MAM dans l’entrepôt de données.                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckins

L’entité **mamCheckin** représente les données collectées au moment de l’enregistrement d’une instance d’application gérée par la gestion des applications mobiles (GAM) auprès du service Intune. 

> [!Note]  
> Quand une instance d’application s’enregistre plusieurs fois par jour, l’entrepôt de données la stocke sous la forme d’un enregistrement unique.

| Propriété | Description | Exemple |
|---------|------------|--------|
| dateKey |Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données. | 20160703 |
| applicationInstanceKey |Clé de l’instance d’application associée à l’enregistrement de cette application MAM. | 123 |
| UserKey |Clé de l’utilisateur associée à l’enregistrement de cette application MAM. | 4323 |
| mamApplicationKey |Clé d’application de l’application associée à l’enregistrement de l’application MAM. | 432 |
| deviceHealthKey |Clé de DeviceHealth associée à l’enregistrement de cette application MAM. | 321 |
| platformKey |Représente la plateforme de l’appareil associé à l’enregistrement de cette application MAM. |123 |
| effectiveAppliedPolicyKey |Représente la stratégie appliquée actuelle qui est associée à l’application GAM enregistrée. Une stratégie appliquée actuelle est le résultat de la fusion de toutes les stratégies relatives à une application et à un utilisateur particuliers. | 322 |
| pastCheckInDate |Date et heure du dernier enregistrement de cette application GAM. La valeur peut être Null. |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>mamDeviceHealth

L’entité **mamDeviceHealth** représente les appareils sur lesquels des stratégies de gestion des applications mobiles (GAM) sont déployées, même s’ils sont jailbreakés.

| Propriété | Description | Exemple |
|---------|------------|--------|
| deviceHealthKey |Identificateur unique de l’appareil et de son état d’intégrité associé dans l’entrepôt de données (clé de substitution). |123 |
| deviceHealth |Identificateur unique de l’appareil et de son état d’intégrité associé (semblable à DeviceHealthKey, mais l’identificateur est une clé naturelle). |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |Représente l’état de l’appareil. <br>Non disponible : aucune information n’est disponible sur cet appareil. <br>Sain : appareil non jailbreaké. <br>Défectueux : appareil jailbreaké. |Non disponible Sain Défectueux |
| rowLastModifiedDateTimeUtc |Date et heure UTC de la dernière modification de l’intégrité de cet appareil MAM spécifique dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

L’entité **mamEffectivePolicy** répertorie toutes les stratégies actuelles de gestion des applications mobiles (GAM) appliquées dans votre organisation. Une stratégie appliquée actuelle est le résultat de la fusion de toutes les stratégies relatives à une application et à un utilisateur particuliers.

| Propriété | Description | Exemple |
|---------|------------|--------|
| effectivePolicyKey |Identificateur unique de la stratégie actuelle MAM dans l’entrepôt de données. |2 |
| realPolicyKey |Identificateur unique de la stratégie GAM créée par un professionnel de l’informatique |1 |
| rowCreatedDateTimeUtc |Date et heure UTC de création de cette stratégie actuelle GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatforms

L’entité **mamPlatform** répertorie les noms et types des plateformes sur lesquelles une application gérée par la gestion des applications mobiles (GAM) a été installée.


|          Propriété          |                                    Description                                    |                         Exemple                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     Identificateur unique de la plateforme dans l’entrepôt de données (clé de substitution).      |                           123                           |
|          Plateforme          | Identificateur unique de la plateforme (semblable à PlatformKey, mais il s’agit d’une clé naturelle). |                           123                           |
|        platformName        |                                   Nom de la plateforme                                   | Non disponible <br>Aucune <br>Windows <br>IOS <br>Android. |
| rowLastModifiedDateTimeUtc | Date et heure UTC de la dernière modification de cette plateforme dans l’entrepôt de données.  |                 11/23/2016 12:00:00 AM                  |

