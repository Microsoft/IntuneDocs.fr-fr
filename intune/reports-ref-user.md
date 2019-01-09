---
title: 'Utilisateur : Entrepôt de données Intune'
titlesuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Utilisateur de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 52201b68e946ec59b7c70ea5ff735c26728e27ce
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429727"
---
# <a name="reference-for-user-entity"></a>Informations de référence sur l’entité d’utilisateur

La catégorie **Utilisateur** contient l’entité **User** qui définit les propriétés des utilisateurs dans le modèle de données.

## <a name="user"></a>Utilisateur

L’entité **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise.

La collection d’entités **Utilisateur** contient les données des utilisateurs. Parmi ces enregistrements figurent les états utilisateurs de la période de collecte de données, même si l’utilisateur a été supprimé. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données du mois précédent. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| UserKey |Identificateur unique de l’utilisateur dans l’entrepôt de données (clé de substitution). |123 |
| UserId |Identificateur unique de l’utilisateur (semblable à UserKey, mais il s’agit d’une clé naturelle). |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Adresse e-mail de l’utilisateur. |John@constoso.com |
| UPN | Nom d'utilisateur principal de l'utilisateur. | John@constoso.com |
| DisplayName |Nom d’affichage de l’utilisateur. |Jean |
| IntuneLicensed |Spécifie si cet utilisateur dispose d’une licence Intune ou non. |Vrai/Faux |
| IsDeleted | Indique si toutes les licences de l’utilisateur ont expiré et si ce dernier a de ce fait été supprimé d’Intune. Pour un enregistrement unique, cet indicateur ne change pas. En revanche, un autre enregistrement est créé pour le nouvel état de l’utilisateur. |Vrai/Faux |
| StartDateInclusiveUTC |Si IsDeleted = FALSE, DateHeure UTC à laquelle l’utilisateur a obtenu une licence et a commencé à être présent sur Intune. Si IsDeleted = TRUE, DateHeure UTC à laquelle l’utilisateur a vu sa licence expirer et a été supprimé d’Intune. |11/23/2016 12:00:00 AM |
| EndDateExclusiveUTC |Si IsDeleted = FALSE, DateHeure UTC à laquelle l’utilisateur a vu sa licence expirer et a été supprimé d’Intune. La licence a expiré au cours du jour précédent. Si IsDeleted = TRUE, DateHeure UTC à laquelle l’utilisateur a récupéré une nouvelle licence et a été recréé sur Intune.  |11/23/2016 12:00:00 AM |
| IsCurrent |Indique si cet enregistrement représente le dernier état de l’utilisateur. Plusieurs enregistrements peuvent coexister pour un même utilisateur, mais un seul d’entre eux représente l’état actuel.  |Vrai/Faux |
| RowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de l’enregistrement dans l’entrepôt de données.  |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>Étapes suivantes
 - Il est possible d’utiliser la collection d’entités **Utilisateur actuel** pour limiter les données utilisateurs aux seuls utilisateurs actuellement actifs. Pour plus d’informations, consultez la page [Informations de référence sur l’entité Utilisateur en cours](reports-ref-current-user.md).
 - Pour plus d’informations sur la façon dont l’entrepôt de données effectue le suivi de la durée de vie des utilisateurs dans Intune, consultez la page [Représentation de la durée de vie des utilisateurs dans l’entrepôt de données Intune](reports-ref-user-timeline.md).
