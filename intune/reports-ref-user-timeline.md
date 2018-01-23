---
title: "Chronologie des entités utilisateur de l’entrepôt de données | Microsoft Docs"
description: "L’entrepôt de données Intune représente les utilisateurs sous forme de chronologie."
keywords: "Entrepôt de données Intune"
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: af9ccd1400127801e5d4de0a3a3e143fabf525f6
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2018
---
# <a name="user-lifetime-representation-in-the-intune-data-warehouse"></a>Représentation de durée de vie utilisateur dans l’entrepôt de données Intune

Vous pouvez utiliser le mois des instantanés de données stockés dans l’entrepôt de données Intune pour répondre aux questions relatives aux tendances basées sur la durée. Par exemple, vous pouvez rechercher le nombre d’utilisateurs ajoutés au cours d’un mois. Vous pouvez également consulter le nombre d’utilisateurs ayant été supprimés du système.

Pour fournir ces informations, l’entrepôt de données stocke des informations d’historique. Cela signifie qu’il peut effectuer le suivi de la durée de vie d’une entité. L’entrepôt enregistre la date de création d’une entité, la date de modification de son état et sa date de suppression. L’historique capturé à l’aide d’instantanés quotidiens de mesures quantitatives vous permet de comparer un jour donné avec le jour précédent, etc.

Le suivi de la durée de vie d’entités peut s’avérer complexe en raison de leurs changements d’état. Par exemple, si vous consultez un instantané le 30 d’un mois particulier, un enregistrement utilisateur peut ne pas exister dans un état actif dans les données. Mais le 28 et le 29 de ce même mois, l’enregistrement d’entité existe peut-être dans un état actif. Et avant le 28, l’utilisateur n’existait pas du tout.

Cet exemple sera plus clair si nous examinons le suivi de la durée de vie d’une entité.

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

 - Pour en savoir plus sur l’entité **Current User**, consultez [Informations de référence sur l’entité Current User](reports-ref-current-user.md).
 - Pour en savoir plus sur l’entité **User**, consultez [Informations de référence sur l’entité User](reports-ref-user.md).