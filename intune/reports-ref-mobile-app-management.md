---
title: Gestion des applications mobiles (GAM) | Microsoft Docs
description: "Rubrique de référence sur la catégorie Gestion des applications mobiles de collections d’entités dans l’API d’entrepôt de données Intune."
keywords: "Entrepôt de données Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 44358d68a653760804f11668ab64d30ebf7ae9eb
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Informations de référence sur les entités de gestion des applications mobiles (GAM)

La catégorie **Gestion des applications mobiles** contient des entités pour applications mobiles, par exemple :

  -  Applications
  -  Instances
  -  État de l’enregistrement
  -  État de l’intégrité
  -  État de la stratégie
  -  État de l'inscription
  -  Types de plateformes

## <a name="mamapplication"></a>MAMApplication

L’entité **MamApplication** répertorie les applications métier qui sont gérées par le biais de la gestion des applications mobiles (GAM) sans inscription dans votre entreprise.

| Propriété | Description | Exemple |
|---------|------------|--------|
| ApplicationKey |Identificateur unique de l’application GAM dans l’entrepôt de données |123 |
| ApplicationName |Nom de l’application GAM |"Word" |
| ApplicationId |ID de l’application GAM |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Indique si cet enregistrement d’application GAM a été mis à jour. True : l’application GAM a un nouvel enregistrement avec des champs mis à jour dans cette table. False : dernier enregistrement pour cette application GAM. |Vrai/Faux |
| StartDateInclusiveUTC |Date et heure UTC de création de cette application GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |
| DeletedDateUTC |Date et heure UTC de l’affectation de la valeur True à IsDeleted |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cette application GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

L’entité **MamApplicationInstance** répertorie les applications GAM gérées comme instances singulières, par utilisateur et par appareil. Tous les utilisateurs et appareils répertoriés dans l’entité sont protégés si au moins une stratégie GAM leur est affectée.

| Propriété | Description | Exemple |
|---------|------------|--------|
| ApplicationInstanceKey |Identificateur unique de l’instance de l’application GAM dans l’entrepôt de données (clé de substitution) |123 |
| UserId |ID de l’utilisateur ayant installé cette application GAM |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |Identificateur unique de l’instance de l’application GAM (semblable à ApplicationInstanceKey, mais l’identificateur est une clé naturelle) |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |ID de cette application GAM |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |Version de cette application GAM |2 |
| CreatedDate |Date de création de cet enregistrement de l’instance d’application GAM. La valeur peut être Null. |11/23/2016 12:00:00 AM |
| Plate-forme |Plateforme de l’appareil sur lequel cette application GAM est installée |2 |
| PlatformVersion |Version de la plateforme de l’appareil sur lequel cette application GAM est installée |2.2 |
| SdkVersion |Version du SDK GAM utilisé pour inclure cette application GAM dans un wrapper |3.2 |
| DeviceId |ID de l’appareil sur lequel cette application GAM est installée |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Nom de l’appareil sur lequel cette application GAM est installée |"MyDevice" |
| IsDeleted |Indique si l’enregistrement de cette application GAM a été mis à jour. True : cette instance d’application GAM a un nouvel enregistrement avec des champs mis à jour dans cette table. False : dernier enregistrement pour cette instance d’application GAM. |Vrai/Faux |
| StartDateInclusiveUtc |Date et heure UTC de création de cette instance d’application GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |
| DeletedDateUtc |Date et heure UTC de l’affectation de la valeur True à IsDeleted |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUtc |Date et heure UTC de la dernière modification de cette instance d’application GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |

## <a name="mamcheckin"></a>MamCheckin

L’entité **MamCheckin** représente les données collectées au moment de l’enregistrement d’une instance d’application gérée par la gestion des applications mobiles (GAM) auprès du service Intune. 

> [!Note]  
> Quand une instance d’application s’enregistre plusieurs fois par jour, l’entrepôt de données la stocke sous la forme d’un enregistrement unique.

| Propriété | Description | Exemple |
|---------|------------|--------|
| DateKey |Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données | 20160703 |
| ApplicationInstanceKey |Clé de l’instance d’application associée à l’enregistrement de cette application GAM |5/2/1900 12:00:00 AM |
| UserKey |Clé de l’utilisateur associée à l’enregistrement de cette application GAM |1/12/1900 12:00:00 AM |
| ApplicationKey |Clé de l’application GAM enregistrée |1/10/1900 12:00:00 AM |
| DeviceHealthKey |Clé de DeviceHealth associée à l’enregistrement de cette application GAM |1/2/1900 12:00:00 AM |
| PlatformKey |Représente la plateforme de l’appareil associé à l’enregistrement de cette application GAM |1/1/1900 12:00:00 AM |
| EffectiveAppliedPolicyKey |Représente la stratégie appliquée actuelle qui est associée à l’application GAM enregistrée. Une stratégie appliquée actuelle est le résultat de la fusion de toutes les stratégies relatives à une application et à un utilisateur particuliers. |5/2/1900 12:00:00 AM |
| LastCheckInDate |Date et heure du dernier enregistrement de cette application GAM. La valeur peut être Null. |11/23/2016 12:00:00 AM |

## <a name="mamdevicehealth"></a>MamDeviceHealth

L’entité **MamDeviceHealth** représente les appareils sur lesquels des stratégies de gestion des applications mobiles (GAM) sont déployées, même s’ils sont jailbreakés.

| Propriété | Description | Exemple |
|---------|------------|--------|
| DeviceHealthKey |Identificateur unique de l’appareil et de son état d’intégrité associé dans l’entrepôt de données (clé de substitution) |1/1/1900 12:00:00 AM |
| DeviceHealth |Identificateur unique de l’appareil et de son état d’intégrité associé (semblable à DeviceHealthKey, mais l’identificateur est une clé naturelle) |1/1/1900 12:00:00 AM |
| DeviceHealthName |Représente l’état de l’appareil. Non disponible : aucune information n’est disponible sur cet appareil. Sain : appareil non jailbreaké. Défectueux : appareil jailbreaké. |Non disponible Sain Défectueux |
| RowLastModifiedDateTimeUtc |Date et heure UTC de la dernière modification de l’intégrité de cet appareil GAM spécifique dans l’entrepôt de données |11/23/2016 12:00:00 AM |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

L’entité **MamEffectivePolicy** répertorie toutes les stratégies actuelles de gestion des applications mobiles (GAM) appliquées dans votre organisation. Une stratégie appliquée actuelle est le résultat de la fusion de toutes les stratégies relatives à une application et à un utilisateur particuliers.

| Propriété | Description | Exemple |
|---------|------------|--------|
| EffectivePolicyKey |Identificateur unique de la stratégie actuelle GAM dans l’entrepôt de données |2 |
| RealPolicyKey |Identificateur unique de la stratégie GAM créée par un professionnel de l’informatique |1 |
| RowCreatedDateTimeUtc |Date et heure UTC de création de cette stratégie actuelle GAM dans l’entrepôt de données |11/23/2016 12:00:00 AM |

## <a name="mamglobalapplication"></a>MamGlobalApplication

L’entité **MamGlobalApplication** répertorie les applications du Store qui sont gérées par le biais de la gestion des applications mobiles (GAM) sans inscription dans votre entreprise.

| Propriété | Description | Exemple |
|---------|------------|--------|
| ApplicationKey |Identificateur unique de l’application du Store dans l’entrepôt de données (clé de substitution). |123 |
| ApplicationId |Identificateur unique de l’application du Store. L’identificateur est semblable à ApplicationKey, mais il s’agit d’une clé naturelle. |com.microsoft.skydrive.<ios> |
| ApplicationName |Nom de l’application globale GAM. |Skydrive |
| RowLastModifiedDateTimeUtc |Date et heure UTC de la dernière modification de cette application globale GAM spécifique dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="mamplatform"></a>MamPlatform

L’entité **MamPlatform** répertorie les noms et types des plateformes sur lesquelles une application gérée par la gestion des applications mobiles (GAM) a été installée.

| Propriété | Description | Exemple |
|---------|------------|--------|
| PlatformKey |Identificateur unique de la plateforme dans l’entrepôt de données (clé de substitution) |123 |
| Plate-forme |Identificateur unique de la plateforme (semblable à PlatformKey, mais il s’agit d’une clé naturelle) |123 |
| PlatformName |Nom de la plateforme |Non disponible Aucun Windows IOS Android |
| RowLastModifiedDateTimeUtc |Date et heure UTC de la dernière modification de cette plateforme dans l’entrepôt de données |11/23/2016 12:00:00 AM |