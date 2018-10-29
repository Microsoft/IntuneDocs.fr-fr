---
title: Point de terminaison de l’API d’entrepôt de données Intune
titlesuffix: Microsoft Intune
description: La rubrique de référence décrit la structure de l’URL de l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d552ec61d148d0489dc263405eac52448c10f9ef
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49642875"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Point de terminaison de l’API d’entrepôt de données Intune

Pour utiliser l’API d’entrepôt de données Intune, vous devez disposer d’un compte avec des informations d’identification Azure AD et des contrôles d’accès en fonction du rôle spécifiques. Vous devez ensuite autoriser votre client REST auprès d’Azure AD à l’aide d’OAuth 2.0. Enfin, vous devez former une URL explicite pour appeler une ressource d’entrepôt de données.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Authorization

Azure Active Directory (Azure AD) utilise OAuth 2.0 pour vous permettre d'autoriser l'accès aux applications et API Web dans votre locataire Azure AD. Ce guide, indépendant du langage, décrit comment envoyer et recevoir des messages HTTP sans utiliser de bibliothèque open source. Le flux du code d’autorisation OAuth 2.0 est décrit dans la [section 4.1](https://tools.ietf.org/html/rfc6749#section-4.1) de la spécification OAuth 2.0.

Pour plus d’informations, consultez [Autoriser l’accès aux applications web à l’aide d’OAuth 2.0 et d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>Structure de l’URL de l’API

Les points de terminaison de l’API d’entrepôt de données lisent les entités pour chaque jeu. L’API prend en charge un verbe HHTP **GET** et un sous-ensemble d’options de requête.

L’URL pour Intune a le format suivant :  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> Dans l’URL ci-dessus, remplacez `{location}`, `{entity-collection}` et `{api-version}` en fonction des détails fournis dans le tableau ci-dessous.

L’URL contient les éléments suivants :

| Élément | Exemple | Description |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| emplacement | msua06 | Pour trouver l’URL de base, examinez le panneau de l’API d’entrepôt de données dans le portail Azure. |
| collection_entités | dates | Nom de la collection d’entités OData. Pour plus d’informations sur les collections et entités du modèle de données, consultez [Modèle de données](reports-ref-data-model.md). |
| api-version | beta | Version de l’API à laquelle accéder. Pour plus d’informations, consultez [Version](#API-version-information). |
| maxhistorydays | 7 | (Facultatif) Nombre maximal de jours d’historique à récupérer. Ce paramètre peut être fourni à n’importe quelle collection, mais n’entre en vigueur que pour les collections qui incluent `dateKey` dans le cadre de leur propriété de clé. Pour plus d’informations, consultez [Filtres de plage DateKey](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>Informations sur la version de l’API

Version actuelle de l’API : `beta`. 

## <a name="odata-query-options"></a>Options de requête OData

La version actuelle prend en charge les paramètres de requête OData suivants : `$filter, $orderby, $select, $skip,` et `$top`.

## <a name="datekey-range-filters"></a>Filtres de plage DateKey

Vous pouvez utiliser les filtres de plage `DateKey` pour limiter la quantité de données à télécharger pour certaines des collections ayant `dateKey` comme propriété de clé. Vous pouvez utiliser le filtre `DateKey` pour optimiser les performances du service en fournissant le paramètre de requête `$filter` suivant :

1.  `DateKey` seul dans le `$filter`, prenant en charge les opérateurs `lt/le/eq/ge/gt` et assurant la jointure avec l’opérateur logique `and`, où ils peuvent être mappés à une date de début et/ou une date de fin.
2.  `maxhistorydays` est fourni en tant qu’option de requête personnalisée.<br>

## <a name="filter-examples"></a>Exemples de filtres

> [!NOTE]
> Les exemples de filtres partent du principe que nous sommes le 21 février 2018.

|                             Filtre                             |           Optimisation des performances           |                                          Description                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Complet                                      |    Retourner des données avec `DateKey` compris entre 20180214 et 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Complet                                      |    Retourner des données avec `DateKey` égal à 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Complet                                      |    Retourner des données avec `DateKey` compris entre 20180214 et 20180220.                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    Partiel, l’ID gt 1 ne sera pas optimisé    |    Retourner des données avec `DateKey` compris entre 20180214 20180221, et ID supérieur à 1.             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Complet                                      |    Retourner des données avec `DateKey` égal à 20180214. `maxhistorydays` est ignoré.                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    Aucune                                      |    Non traité en tant que filtre de plage `DateKey`, donc aucune amélioration des performances.                              |
|    `$filter=DateKey ne 20180214`                                 |    Aucune                                      |    Non traité en tant que filtre de plage `DateKey`, donc aucune amélioration des performances.                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    Aucune                                      |    Non traité en tant que filtre de plage `DateKey`, donc aucune amélioration des performances. `maxhistorydays` ignoré.    |
