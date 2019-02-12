---
title: Modèle de données de l’entrepôt de données
titlesuffix: Microsoft Intune
description: L’entrepôt de données Microsoft Intune échantillonne quotidiennement les données pour vous offrir un historique de votre environnement mobile en constante évolution.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b45f8d5b548bd88715381f25ba0b5c3e9155b344
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841791"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Modèle de données de l’entrepôt de données Microsoft Intune

L’entrepôt de données Intune échantillonne quotidiennement les données pour vous offrir un historique de votre environnement d’appareils mobiles, qui évolue en permanence. L’affichage se compose d’entités associées dans le temps.

## <a name="entities-entity-sets"></a>Entités : Ensemble d'entités

L’entrepôt expose les données dans les zones générales suivantes :

  -  Applications protégées par App Protection et utilisation
  -  Appareils inscrits, propriétés et inventaire
  -  Inventaire des applications et des logiciels
  -  Configuration des appareils et stratégies de conformité

Ces zones contiennent les entités qui sont significatives pour l’environnement Intune. Pour plus d’informations sur les jeux d’entités, consultez les rubriques suivantes :

  -  [Application](reports-ref-application.md)
  -  [Date](reports-ref-date.md)
  -  [Appareils](reports-ref-devices.md)
  -  [Extension de la gestion Intune](reports-ref-intunemanagementextension.md)
  -  [Stratégie](reports-ref-policy.md)
  -  [Gestion des applications mobiles (GAM)](reports-ref-mobile-app-management.md)
  -  [Utilisateur](reports-ref-user.md)
  -  [Utilisateur actuel](reports-ref-current-user.md)
  -  [Associations appareil-utilisateur](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>Relations : Modèle de schéma en étoile

L’entrepôt organise les entités selon des relations utiles pour répondre aux questions que vous souhaitez poser. Vous pouvez, par exemple, consulter le nombre d’installations d’une application Android développée en interne. La structure de l’entrepôt de données vous permet d’obtenir des insights sur votre environnement mobile. Des outils analytiques comme Microsoft Power BI peuvent ensuite utiliser le modèle de données de l’entrepôt de données pour créer des visualisations et des tableaux de bord dynamiques.

Les entités et les relations suivent un modèle de schéma en étoile. Un schéma en étoile corrèle des faits par rapport à la dimension temps. Dans le contexte du modèle, un *fait* est une mesure quantitative comme le nombre d’appareils, le nombre d’applications ou l’heure de l’inscription. Les tables de faits stockent une grande quantité de données. Elles peuvent devenir très volumineuses, c’est pourquoi elles limitent généralement les informations à 30 jours. Une *dimension* présente le contexte des faits. Là où le fait reflète ce qu’il s’est passé, les dimensions indiquent à qui. Les tables de dimensions, comme la table **Utilisateur**, sont plus petites et peuvent conserver les données plus longtemps que les tables de faits. 

Optimisé pour la flexibilité et l’analyse des données, un modèle de schéma en étoile vous permet de créer les rapports nécessaires pour comprendre l’évolution de votre environnement mobile.

## <a name="time-daily-snapshots"></a>Heure : instantanés quotidiens

L’entrepôt est en aval des données Intune. Intune prend un instantané quotidien à minuit UTC, et le stocke dans l’entrepôt. La durée de conservation des instantanés varie d’une table de faits à l’autre : sept jours pour certaines, 30 jours pour d’autres, voire encore plus longtemps.

## <a name="next-steps"></a>Étapes suivantes

 - Pour plus d’informations sur la façon dont l’entrepôt de données effectue le suivi de la durée de vie des utilisateurs dans Intune, consultez la page [Représentation de la durée de vie des utilisateurs dans l’entrepôt de données Intune](reports-ref-user-timeline.md).
 - Pour plus d’informations sur l’utilisation des entrepôts de données, consultez la page [Créer un premier entrepôt de données](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse).
 - Pour plus d’informations sur l’utilisation de Power BI et d’un entrepôt de données, consultez la page [Créer un rapport Power BI en important un jeu de données](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/). 
