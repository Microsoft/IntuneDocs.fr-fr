---
title: Chronologie des entités utilisateur de l’entrepôt de données
titleSuffix: Microsoft Intune
description: Découvrez la manière dont l’entrepôt de données Microsoft Intune représente les utilisateurs sous forme de chronologie.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b94be3e1454c60f16ff40e73ce37f8c4e349126d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813360"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Représentation de durée de vie utilisateur dans l’entrepôt de données Microsoft Intune

Vous pouvez utiliser le mois des instantanés de données stockés dans l’entrepôt de données Intune pour répondre aux questions relatives aux tendances basées sur la durée. Par exemple, vous pouvez rechercher le nombre d’utilisateurs ajoutés au cours d’un mois. Vous pouvez également consulter le nombre d’utilisateurs ayant été supprimés du système.

Pour fournir ce type d’insight, l’entrepôt de données stocke des informations d’historique. L’entrepôt de données peut effectuer le suivi de la durée de vie d’une entité. L’entrepôt enregistre la date de création d’une entité, la date de modification de son état et sa date de suppression. L’historique capturé à l’aide d’instantanés quotidiens de mesures quantitatives vous permet de comparer un jour donné avec le jour précédent, etc.

Le suivi de la durée de vie d’entités peut s’avérer complexe en raison de leurs changements d’état. Par exemple, si vous consultez un instantané le 30 d’un mois particulier, un enregistrement utilisateur peut ne pas exister dans un état actif dans les données. Mais le 28 et le 29 de ce même mois, l’enregistrement d’entité existe peut-être dans un état actif. Et avant le 28, l’utilisateur n’existait pas du tout.

Cet exemple est plus clair si vous examinez la durée de vie d’une entité.

Supposons qu’une licence est accordée à un utilisateur, **John Smith**, le 01/06/2017. La table **Utilisateur** aurait alors l’entrée suivante : 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | 31/12/9999 | TRUE
 
John Smith résilie sa licence le 25/07/2017. La table **Utilisateur** aurait alors les entrées suivantes. Les modifications dans les enregistrements existants sont `marked`. 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 26/07/2017 | 31/12/9999 | TRUE 

La première ligne indique que John Smith a existé dans Intune du 01/06/2017 au 25/07/2017. Le deuxième enregistrement indique que l’utilisateur a été supprimé le 25/07/2017 et qu’il n’existe plus dans Intune.

Supposons maintenant qu’une nouvelle licence est accordée à John Smith le 31/08/2017. La table Utilisateur aurait alors les entrées suivantes :
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | 26/07/2017 | FALSE 
| John Smith | TRUE | 26/07/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 31/08/2017 | 31/12/9999 | TRUE 
 
Une personne qui souhaite connaître l’état actuel de tous les utilisateurs pourrait appliquer un filtre où `IsCurrent = TRUE`. 
 
Une personne qui souhaite afficher uniquement les utilisateurs existants pourrait appliquer un filtre où `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Tables de dimension dans la durée de vie d’entités

Afin de pouvoir stocker l’historique des changements d’état des entités, Intune ne supprime pas les enregistrements. Il les marque simplement comme supprimés. C’est ce que l’on appelle une suppression réversible. Les tables de dimension utilisent différentes colonnes de métadonnées pour effectuer le suivi de la durée de vie des enregistrements. 

Les colonnes de métadonnées les plus couramment utilisées sont les suivantes : 

| Nom de la propriété de métadonnées  | Interprétation des valeurs |
|--|--|
| IsDeleted | Indique si l’entité a été supprimée dans Intune. |
| StartDateInclusiveUTC  | Date UTC à laquelle l’entité a été chargée dans l’entrepôt de données Intune. L’entité peut avoir été créée avant d’être importée dans l’entrepôt de données Intune. |
| DeletedDateUTC  | Date UTC à laquelle l’entité a été supprimée dans Intune. |  

Toute colonne de métadonnées commençant par le préfixe **Row**, par exemple **RowLastModifiedDateTimeUTC**, indique la date à laquelle un enregistrement a été créé ou modifié dans l’entrepôt de données Intune. L’entrepôt se situe en aval des données dans Intune. Cette valeur n’a aucune relation avec la durée de vie de l’entité dans Intune.  
 
Toute personne souhaitant afficher uniquement ces entités de dimension qui existent actuellement pourrait appliquer un filtre où **IsDeleted = FALSE**.

## <a name="next-steps"></a>Étapes suivantes

- Pour en savoir plus sur l’entité **Utilisateur actuel**, consultez [Informations de référence sur l’entité Utilisateur actuel](../reports-ref-current-user.md).
- Pour en savoir plus sur l’entité **Utilisateur**, consultez [Informations de référence sur l’entité Utilisateur](../reports-ref-user.md).
