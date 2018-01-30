---
title: "Utilisateur actuel - Entrepôt de données Intune | Microsoft Docs"
description: "Rubrique de référence sur la catégorie Utilisateur de collections d’entités dans l’API d’entrepôt de données Intune."
keywords: "Entrepôt de données Intune"
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d25825910e878d428bde72414c4bbee2d5092a89
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="reference-for-current-user-entity"></a>Informations de référence sur l’entité d’utilisateur actuel

La catégorie **Utilisateur actuel** contient les propriétés des utilisateurs dans le modèle de données. La collection d’entités **Utilisateur actuel** est limitée aux utilisateurs actuellement actifs. L’entité contient tous les utilisateurs Azure Active Directory qui disposent actuellement d’une licence. Il peut s’agir d’une licence Intune, d’une licence hybride ou d’une licence Microsoft Office 365. Les utilisateurs supprimés ne sont pas représentés dans la collecte Utilisateur actuel. Pour créer une collection qui contient un historique des modifications de l’état utilisateur, consultez la page [Informations de référence sur l’entité Utilisateur](reports-ref-user.md).


## <a name="current-user"></a>Utilisateur actuel

L’entité **Utilisateur actuel** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| UserKey |Identificateur unique de l’utilisateur dans l’entrepôt de données (clé de substitution). |123 |
| UserId |Identificateur unique de l’utilisateur (semblable à UserKey, mais il s’agit d’une clé naturelle). |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Adresse e-mail de l’utilisateur. |John@constoso.com |
| UPN | Nom d'utilisateur principal de l'utilisateur. | John@constoso.com |
| DisplayName |Nom d’affichage de l’utilisateur. |John |
| IntuneLicensed |Spécifie si cet utilisateur dispose d’une licence Intune ou non. |Vrai/Faux |
| StartDateInclusiveUTC |Date et heure UTC de création de cet utilisateur dans l’entrepôt de données. |11/23/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Date et heure UTC de la dernière modification de cet utilisateur dans l’entrepôt de données. |11/23/2016 12:00:00 AM |

## <a name="next-steps"></a>Étapes suivantes
 - Il est possible d’utiliser la collection d’entités **Utilisateurs** pour étendre les données utilisateurs aux utilisateurs qui ne sont pas actifs actuellement. Pour plus d’informations, consultez la page [Informations de référence sur l’entité Utilisateur](reports-ref-user.md).
 - Pour plus d’informations sur la façon dont l’entrepôt de données effectue le suivi de la durée de vie des utilisateurs dans Intune, consultez la page [Représentation de la durée de vie des utilisateurs dans l’entrepôt de données Intune](reports-ref-user-timeline.md).
