---
title: Point de terminaison de l’API d’entrepôt de données Intune
titleSuffix: Microsoft Intune
description: Cette rubrique de référence décrit la structure de l’URL de l’API d’entrepôt de données Microsoft Intune. Des exemples de filtre sont fournis.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/25/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50be11f9ada92670c201fc2540499effa5a7edef
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798496"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Point de terminaison de l’API d’entrepôt de données Intune

Pour utiliser l’API d’entrepôt de données Intune, vous devez disposer d’un compte avec des informations d’identification Azure AD et des contrôles d’accès en fonction du rôle spécifiques. Vous devez ensuite autoriser votre client REST auprès d’Azure AD à l’aide d’OAuth 2.0. Enfin, vous devez former une URL explicite pour appeler une ressource d’entrepôt de données.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorisation

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
| api-version | beta | Version de l’API à laquelle accéder. Pour plus d’informations, consultez [Version](reports-api-url.md#api-version-information). |
| maxhistorydays | 7 | (Facultatif) Nombre maximal de jours d’historique à récupérer. Ce paramètre peut être fourni à n’importe quelle collection, mais n’entre en vigueur que pour les collections qui incluent `dateKey` dans le cadre de leur propriété de clé. Pour plus d’informations, consultez [Filtres de plage DateKey](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>Informations sur la version de l’API

Vous pouvez maintenant utiliser la version v1.0 d’Intune Data Warehouse en définissant le paramètre de requête  `api-version=v1.0`. Les mises à jour de collections dans l’entrepôt de données sont additives par nature et n’interrompent pas les scénarios existants.

Utilisez la version bêta pour essayer les fonctionnalités les plus récentes de l’entrepôt de données. Pour accéder à la version bêta, votre URL doit contenir le paramètre de requête  `api-version=beta`. La version bêta vous permet d’utiliser des fonctionnalités avant qu’elles ne soient disponibles dans le cadre d’un service pris en charge. À mesure que de nouvelles fonctionnalités sont ajoutées à Intune, le comportement et le contrat de données de la version bêta peuvent être amenés à changer. Il est possible que le code personnalisé ou les outils de génération de rapports qui dépendent de la version bêta ne fonctionnent plus après l’application de mises à jour.

## <a name="odata-query-options"></a>Options de requête OData

La version actuelle prend en charge les paramètres de requête OData suivants : `$filter`, `$select`, `$skip,` et `$top`. Dans `$filter`, seuls `DateKey` ou `RowLastModifiedDateTimeUTC` peut être pris en charge lorsque les colonnes sont applicables, et autres propriétés déclenche une demande incorrecte.

## <a name="datekey-range-filters"></a>Filtres de plage DateKey

Vous pouvez utiliser les filtres de plage `DateKey` pour limiter la quantité de données à télécharger pour certaines des collections ayant `dateKey` comme propriété de clé. Vous pouvez utiliser le filtre `DateKey` pour optimiser les performances du service en fournissant le paramètre de requête `$filter` suivant :

1.  `DateKey` seul dans le `$filter`, prenant en charge les opérateurs `lt/le/eq/ge/gt` et assurant la jointure avec l’opérateur logique `and`, où ils peuvent être mappés à une date de début et/ou une date de fin.
2.  `maxhistorydays` est fourni en tant qu’option de requête personnalisée.<br>

## <a name="filter-examples"></a>Exemples de filtres

> [!NOTE]
> Les exemples de filtres partent du principe que nous sommes le 21 février 2019.

|                             Filtre                             |           Optimisation des performances           |                                          Description                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Complète                                      |    Retourner des données avec `DateKey` compris entre 20180214 et 20180221.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Complète                                      |    Retourner des données avec `DateKey` égal à 20180214.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Complète                                      |    Retourner des données avec `DateKey` compris entre 20180214 et 20180220.                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Complète                                      |    Retourner des données avec `DateKey` égal à 20180214. `maxhistorydays` est ignoré.                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    Complète                                       |    Retourne des données avec `RowLastModifiedDateTimeUTC` est supérieur ou égal à `2018-02-21T23:18:51.3277273Z`                             |
