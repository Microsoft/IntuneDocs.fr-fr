---
title: Gestion des applications mobiles (GAM)
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Gestion des applications mobiles de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
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
ms.openlocfilehash: 5a8d16e058afbedfd1a343560b3727d33776da45
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547867"
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

## <a name="mamapplication"></a>MAMApplication

L’entité **MamApplication** répertorie les applications métier qui sont gérées par le biais de la gestion des applications mobiles (GAM) sans inscription dans votre entreprise.

| Propriété | Description | Exemple |
|---------|------------|--------|
| mamApplicationKey |Identificateur unique de l’application MAM. | 432 |
| mamApplicationName |Nom de l’application MAM. |Exemple de nom d’application MAM |
| mamApplicationId |ID d’application de l’application MAM. | 123 |
| IsDeleted |Indique si cet enregistrement d’application GAM a été mis à jour. <br>True : l’application GAM a un nouvel enregistrement avec des champs mis à jour dans cette table. <br>False : dernier enregistrement pour cette application GAM. |Vrai/Faux |
| StartDateInclusiveUTC |Date et heure UTC de création de cette application MAM dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Date et heure UTC de l’affectation de la valeur True à IsDeleted. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cette application MAM dans l’entrepôt de données. |11/23/2016 12:00:00 AM |


## <a name="mamapplicationinstance"></a>MamApplicationInstance

L’entité **MamApplicationInstance** répertorie les applications GAM gérées comme instances singulières, par utilisateur et par appareil. Tous les utilisateurs et appareils répertoriés dans l’entité sont protégés si au moins une stratégie GAM leur est affectée.


|          Propriété          |                                                                                                  Description                                                                                                  |               Exemple                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Identificateur unique de l’instance de l’application MAM dans l’entrepôt de données (clé de substitution).                                                                |                 123                  |
|           UserId           |                                                                              ID de l’utilisateur ayant installé cette application MAM.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Identificateur unique de l’instance de l’application MAM (semblable à ApplicationInstanceKey, mais l’identificateur est une clé naturelle).                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | ID d’application de l’application MAM pour laquelle cette instance de l’application MAM a été créée.   | 11/23/2016 12:00:00 AM   |
|     ApplicationVersion     |                                                                                     Version de cette application MAM.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Date de création de cet enregistrement de l’instance d’application GAM. La valeur peut être Null.                                                                 |        11/23/2016 12:00:00 AM        |
|          Plate-forme          |                                                                          Plateforme de l’appareil sur lequel cette application MAM est installée.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Version de la plateforme de l’appareil sur lequel cette application MAM est installée.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            Version du SDK MAM avec laquelle cette application MAM a été enveloppée (wrapped).                                                                            |                 3.2                  |
| mamDeviceId | ID d’appareil de l’appareil auquel l’instance de l’application MAM est associée.   | 11/23/2016 12:00:00 AM   |
| mamDeviceType | Type d’appareil de l’appareil auquel l’instance de l’application MAM est associée.   | 11/23/2016 12:00:00 AM   |
| mamDeviceName | Nom d’appareil de l’appareil auquel l’instance de l’application MAM est associée.   | 11/23/2016 12:00:00 AM   |
|         IsDeleted          | Indique si l’enregistrement de cette application GAM a été mis à jour. <br>True : cette instance d’application GAM a un nouvel enregistrement avec des champs mis à jour dans cette table. <br>False : dernier enregistrement pour cette instance d’application GAM. |              Vrai/Faux              |
|   StartDateInclusiveUtc    |                                                              Date et heure UTC de création de cette instance d’application MAM dans l’entrepôt de données.                                                               |        11/23/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             Date et heure UTC de l’affectation de la valeur True à IsDeleted.                                                                              |        11/23/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           Date et heure UTC de la dernière modification de cette instance d’application MAM dans l’entrepôt de données.                                                            |        11/23/2016 12:00:00 AM        |


## <a name="mamcheckin"></a>MamCheckin

L’entité **MamCheckin** représente les données collectées au moment de l’enregistrement d’une instance d’application gérée par la gestion des applications mobiles (GAM) auprès du service Intune. 

> [!Note]  
> Quand une instance d’application s’enregistre plusieurs fois par jour, l’entrepôt de données la stocke sous la forme d’un enregistrement unique.

| Propriété | Description | Exemple |
|---------|------------|--------|
| DateKey |Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données. | 20160703 |
| ApplicationInstanceKey |Clé de l’instance d’application associée à l’enregistrement de cette application MAM. | 123 |
| UserKey |Clé de l’utilisateur associée à l’enregistrement de cette application MAM. | 4323 |
| mamApplicationKey |Clé d’application de l’application associée à l’enregistrement de l’application MAM. | 432 |
| DeviceHealthKey |Clé de DeviceHealth associée à l’enregistrement de cette application MAM. | 321 |
| PlatformKey |Représente la plateforme de l’appareil associé à l’enregistrement de cette application MAM. |123 |
| EffectiveAppliedPolicyKey |Représente la stratégie appliquée actuelle qui est associée à l’application GAM enregistrée. Une stratégie appliquée actuelle est le résultat de la fusion de toutes les stratégies relatives à une application et à un utilisateur particuliers. | 322 |
| LastCheckInDate |Date et heure du dernier enregistrement de cette application GAM. La valeur peut être Null. |11/23/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>MamDeviceHealth

L’entité **MamDeviceHealth** représente les appareils sur lesquels des stratégies de gestion des applications mobiles (GAM) sont déployées, même s’ils sont jailbreakés.

| Propriété | Description | Exemple |
|---------|------------|--------|
| DeviceHealthKey |Identificateur unique de l’appareil et de son état d’intégrité associé dans l’entrepôt de données (clé de substitution). |123 |
| DeviceHealth |Identificateur unique de l’appareil et de son état d’intégrité associé (semblable à DeviceHealthKey, mais l’identificateur est une clé naturelle). |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Représente l’état de l’appareil. <br>Non disponible : aucune information n’est disponible sur cet appareil. <br>Sain : appareil non jailbreaké. <br>Défectueux : appareil jailbreaké. |Non disponible Sain Défectueux |
| RowLastModifiedDateTimeUtc |Date et heure UTC de la dernière modification de l’intégrité de cet appareil MAM spécifique dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

L’entité **MamEffectivePolicy** répertorie toutes les stratégies actuelles de gestion des applications mobiles (GAM) appliquées dans votre organisation. Une stratégie appliquée actuelle est le résultat de la fusion de toutes les stratégies relatives à une application et à un utilisateur particuliers.

| Propriété | Description | Exemple |
|---------|------------|--------|
| EffectivePolicyKey |Identificateur unique de la stratégie actuelle MAM dans l’entrepôt de données. |2 |
| RealPolicyKey |Identificateur unique de la stratégie GAM créée par un professionnel de l’informatique |1 |
| RowCreatedDateTimeUtc |Date et heure UTC de création de cette stratégie actuelle GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |

## <a name="mamglobalapplication"></a>MamGlobalApplication

L’entité **MamGlobalApplication** répertorie les applications du Store qui sont gérées par le biais de la gestion des applications mobiles (GAM) sans inscription dans votre entreprise.


|          Propriété          |                                               Description                                               |           Exemple            |
|----------------------------|---------------------------------------------------------------------------------------------------------|------------------------------|
|       ApplicationKey       |          Identificateur unique de l’application du Store dans l’entrepôt de données (clé de substitution).          |             123              |
|       ApplicationId        | Identificateur unique de l’application du Store. L’identificateur est semblable à ApplicationKey, mais il s’agit d’une clé naturelle.  | com.microsoft.skydrive.<ios> |
|      ApplicationName       |                                      Nom de l’application globale GAM.                                       |           Skydrive           |
| RowLastModifiedDateTimeUtc | Date et heure UTC de la dernière modification de cette application globale GAM spécifique dans l’entrepôt de données. |    11/23/2016 12:00:00 AM    |

## <a name="mamplatform"></a>MamPlatform

L’entité **MamPlatform** répertorie les noms et types des plateformes sur lesquelles une application gérée par la gestion des applications mobiles (GAM) a été installée.


|          Propriété          |                                    Description                                    |                         Exemple                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Identificateur unique de la plateforme dans l’entrepôt de données (clé de substitution).      |                           123                           |
|          Plate-forme          | Identificateur unique de la plateforme (semblable à PlatformKey, mais il s’agit d’une clé naturelle). |                           123                           |
|        PlatformName        |                                   Nom de la plateforme                                   | Non disponible <br>Aucune <br>Windows <br>IOS <br>Android. |
| RowLastModifiedDateTimeUtc | Date et heure UTC de la dernière modification de cette plateforme dans l’entrepôt de données.  |                 11/23/2016 12:00:00 AM                  |

