---
title: "Utilisateur - Entrepôt de données Intune | Microsoft Docs"
description: "Rubrique de référence sur la catégorie Utilisateur de collections d’entités dans l’API d’entrepôt de données Intune."
keywords: "Entrepôt de données Intune"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8088127f5968c0b4f07f83b1dad02ba90f4e6b9a
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="reference-for-user-entity"></a>Informations de référence sur l’entité User

La catégorie **Utilisateur** contient l’entité **User** qui définit les propriétés des utilisateurs et des agents dans le modèle de données.

**Utilisateur**

L’entité **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| UserKey |Identificateur unique de l’utilisateur dans l’entrepôt de données (clé de substitution). |123 |
| UserId |Identificateur unique de l’utilisateur (semblable à UserKey, mais il s’agit d’une clé naturelle). |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Adresse e-mail de l’utilisateur. |John@constoso.com |
| DisplayName |Nom d’affichage de l’utilisateur. |Jean |
| IntuneLicensed |Spécifie si cet utilisateur dispose d’une licence Intune ou non. |Vrai/Faux |
| IsDeleted |Indique si cet enregistrement d’utilisateur a été mis à jour.  True : cet utilisateur a un nouvel enregistrement avec des champs mis à jour dans cette table. False : dernier enregistrement pour cet utilisateur. |Vrai/Faux |
| StartDateInclusiveUTC |Date et heure UTC de création de cet utilisateur dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Date et heure UTC de l’affectation de la valeur True à IsDeleted. |11/23/2016 12:00:00 AM |
| IsCurrent |Indique si cet enregistrement d’utilisateur est actif ou non dans l’entrepôt de données. |Vrai/Faux |
| RowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cet utilisateur dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

