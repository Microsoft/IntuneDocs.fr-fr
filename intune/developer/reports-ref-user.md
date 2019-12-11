---
title: 'Utilisateur : Entrepôt de données Intune'
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Utilisateur de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 996e28f9dceff88637c93e667597e3364215b965
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505637"
---
# <a name="reference-for-user-entity"></a>Informations de référence sur l’entité d’utilisateur

La catégorie **Users** contient l’entité **user** qui définit les propriétés des utilisateurs dans le modèle de données.

## <a name="users"></a>utilisateurs

L’entité **user** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise.

La collection d’entités **user** contient les données des utilisateurs. Parmi ces enregistrements figurent les états utilisateurs de la période de collecte de données, même si l’utilisateur a été supprimé. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données du mois précédent. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

|          Propriété          |                                                                                                           Description                                                                                                          |                Exemple               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Identificateur unique de l’utilisateur dans l’entrepôt de données (clé de substitution).                                                                                                                                                         | 123                                  |
| userId                     | Identificateur unique de l’utilisateur (semblable à UserKey, sauf qu’il s’agit d’une clé naturelle).                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| userEmail                  | Adresse e-mail de l’utilisateur.                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | Nom d’utilisateur principal de l’utilisateur.                                                                                                                                                                                               | John@constoso.com                    |
| displayName                | Nom d’affichage de l’utilisateur.                                                                                                                                                                                                      | Jean                                 |
| intuneLicensed             | Spécifie si cet utilisateur dispose d’une licence Intune ou non.                                                                                                                                                                              | Vrai/Faux                           |
| isDeleted                  | Indique si toutes les licences de l’utilisateur ont expiré et si ce dernier a, de ce fait, été supprimé d’Intune. Pour un enregistrement unique, cet indicateur ne change pas. En revanche, un autre enregistrement est créé pour le nouvel état de l’utilisateur. | Vrai/Faux                           |
| RowLastModifiedDateTimeUTC | Date et heure UTC de la dernière modification de l’enregistrement dans l’entrepôt de données                                                                                                                                                 | 23/11/2016 0:00                      |


## <a name="next-steps"></a>Étapes suivantes
- Il est possible d’utiliser la collection d’entités **Utilisateur actuel** pour limiter les données utilisateurs aux seuls utilisateurs actuellement actifs. Pour plus d’informations, consultez la page [Informations de référence sur l’entité Utilisateur en cours](../reports-ref-current-user.md).
- Pour plus d’informations sur la façon dont l’entrepôt de données effectue le suivi de la durée de vie des utilisateurs dans Intune, consultez la page [Représentation de la durée de vie des utilisateurs dans l’entrepôt de données Intune](reports-ref-user-timeline.md).
