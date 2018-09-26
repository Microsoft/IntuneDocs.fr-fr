---
title: Créer un rapport à partir du flux OData avec Power BI
titlesuffix: Microsoft Intune
description: Créez une visualisation treemap à l’aide de Power BI Desktop avec un filtre interactif à partir de l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f4425f508164332295899a6132782833889aa830
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602263"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Créer un rapport à partir du flux OData avec Power BI

Ce didacticiel explique comment créer une visualisation treemap à l’aide de Power BI Desktop avec un filtre interactif. Imaginons que votre directeur financier souhaite comparer le nombre d’appareils d’entreprise au nombre d’appareils personnels dans votre distribution globale. La visualisation treemap fournit des insights sur les différents types d’appareils. Vous pouvez ainsi voir le nombre d’appareils iOS, Android et Windows qui appartiennent à l’entreprise ou qui sont personnels.

### <a name="overview-of-creating-the-chart"></a>Vue d’ensemble de la création du graphique

Pour créer ce graphique, effectuez les étapes suivantes :
1. Installez Power BI Desktop si ce n’est pas déjà fait.
2. Connectez-vous au modèle de données de l’entrepôt de données Intune et récupérez les données actuelles du modèle.
3. Créez ou gérez les relations du modèle de données.
4. Créez le graphique avec les données de la table **devices**.
5. Créez un filtre interactif.
6. Affichez le graphique terminé.

### <a name="a-note-about-tables-and-entities"></a>Remarque à propos des tables et des entités

Dans Power BI, vous travaillez avec des tables. Une table contient des champs de données. Chaque champ de données a un type de données. Le champ ne peut contenir que des données du type de données (nombre, texte, date, etc.). Quand vous chargez le modèle dans Power BI, les tables sont remplies avec les données d’historique récentes de votre locataire. Bien que les données spécifiques évoluent au fil du temps, la structure de la table ne change pas, sauf si le modèle de données sous-jacent est mis à jour.

Les termes _entité_ et _table_ peuvent prêter à confusion. Le modèle de données est accessible par le biais d’un flux OData. Dans l’univers OData, les conteneurs appelés tables dans Power BI sont appelés des entités. Ces termes font tous les deux référence au même conteneur de données.

## <a name="install-power-bi-desktop"></a>Installer Power BI Desktop

Installez la dernière version de Power BI Desktop. Power BI Desktop est disponible en téléchargement à l’emplacement suivant : [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Se connecter au flux OData pour l’entrepôt de données Intune de votre locataire

> [!Note]  
> Vous devez être autorisé à accéder à **Rapports** dans Intune. Pour plus d’informations, consultez [Autorisation](reports-api-url.md).

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Ouvrez le volet **Entrepôt de données Intune**.
4. Copier l’URL du flux personnalisé. Par exemple : `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. Ouvrez Power BI Desktop.
6. Choisissez **Obtenir des données** > **Flux Odata**.
7. Collez l’URL du flux personnalisé dans la zone URL de la fenêtre **Flux OData**.
8. Sélectionnez **De base**.

    ![Flux OData](media/reports-create-01-odatafeed.png)

9. Sélectionnez **OK**.
10. Sélectionnez **Compte professionnel**, puis connectez-vous avec vos informations d’identification Intune.

    ![Informations d’identification du compte professionnel](media/reports-create-02-org-account.png)

11. Sélectionnez **Connexion**. Le Navigateur s’ouvre et affiche la liste des tables dans l’entrepôt de données Intune.

    ![Navigateur](media/reports-create-02-loadentities.png)

12. Sélectionnez les tables **devices** et **ownerTypes**.  Sélectionnez **Charger**. Power BI charge les données dans le modèle.

## <a name="create-a-relationship"></a>Créer une relation

Vous pouvez importer plusieurs tables pour analyser non seulement les données dans une table unique, mais aussi les données connexes contenues dans plusieurs tables.  Power BI comprend une fonctionnalité appelée **Détection automatique** qui recherche et crée des relations pour vous. Les tables de l’entrepôt de données sont générées pour fonctionner avec la fonctionnalité de détection automatique de Power BI. Même si Power BI ne trouve pas automatiquement de relations, c’est vous qui gérez les relations.

![Gérer les relations](media/reports-create-03-managerelationships.png)

1. Sélectionnez **Gérer les relations**.
2. Sélectionnez **Détection automatique** si Power BI n’a pas encore détecté les relations.

La relation est présentée dans une colonne De et une colonne À. Dans cet exemple, le champ de données **ownerTypeKey** dans la table **devices** est lié au champ de données **ownerTypeKey** dans la table **ownerTypes**. Vous utilisez la relation pour rechercher le nom brut du code de type d’appareil dans la table **devices**.

## <a name="create-a-treemap-visualization"></a>Créer une visualisation treemap

Un graphique treemap affiche les données hiérarchiques sous forme de zones dans des zones. Chaque branche de la hiérarchie est une zone qui contient des zones plus petites correspondant à des sous-branches. Vous pouvez utiliser Power BI Desktop pour créer un treemap de vos données Intune.

![Visualisations > treemap](media/reports-create-03-treemap.png)

1. Sélectionnez un type de graphique. Sélectionnez **Treemap**.
2. Dans le modèle de données, recherchez la table **devices**.
3. Développez la **table devices**, puis sélectionnez le champ de données **manufacturer** dans le panneau **Champs**.
4. Faites glisser le champ de données **manufacturer** dans le graphique Treemap sur le canevas de rapport.
5. Faites glisser le champ de données **deviceKey** de la table **devices** dans la section **Valeurs** sous le volet **Visualisations** et déposez-le sur la zone étiquetée **Faites glisser ici les champs de données**.  

Vous disposez maintenant d’un visuel qui montre la distribution des fabricants d’appareils dans votre organisation.

![Treemap avec des données](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Ajouter un filtre

Pour répondre à des questions supplémentaires à l’aide de votre application, vous pouvez ajouter un filtre à votre treemap.


1. Pour ajouter un filtre, sélectionnez le canevas de rapport, puis l’**icône Segment** (![Treemap avec des données](media/reports-create-slicer.png)) sous **Visualisations**.
2. Recherchez la table **ownerTypes** et faites glisser le champ de données **ownerTypeName** sous la section **Filtres** dans le panneau **Visualisations**.  

   Sous la table des appareils, recherchez le champ de données **OwnerTypeKey**. Celui-ci contient un code indiquant si l’appareil appartient à l’entreprise ou à un individu. Pour afficher des noms conviviaux dans ce filtre, recherchez la table **ownerTypes** et faites glisser le champ de données **ownerTypeName**. Cet exemple montre comment le modèle de données prend en charge les relations entre les tables.

![Treemap avec filtre](media/reports-create-08_ownertype.png)

Vous disposez maintenant d’un filtre interactif qui vous permet de basculer entre les appareils d’entreprise et les appareils personnels. Utilisez ce filtre pour voir comment la distribution change.

1. Sélectionnez **Entreprise** pour voir la distribution des appareils d’entreprise.
2. Sélectionnez **Personnel** pour voir les appareils personnels.

## <a name="next-steps"></a>Étapes suivantes

 - Découvrez plus en détail [la création et la gestion des relations](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) dans Power BI Desktop dans la documentation sur Power BI.
 - Consultez le [modèle de l’entrepôt de données Intune](https://docs.microsoft.com/intune/reports-ref-data-model).
