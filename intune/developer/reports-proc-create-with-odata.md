---
title: Créer un rapport Intune à partir du flux OData avec Power BI
titleSuffix: Microsoft Intune
description: Créez une visualisation treemap à l’aide de Power BI Desktop avec un filtre interactif à partir de l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fbbffb187fc9e9537bf647bc33e3d98879369c3
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576048"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Créer un rapport Intune à partir du flux OData avec Power BI

Cet article explique comment créer une visualisation treemap de vos données Intune à l’aide de Power BI Desktop qui utilise un filtre interactif. Imaginons que votre directeur financier souhaite connaître comment l’ensemble des appareils sont distribués entre les appareils appartenant à l’entreprise et les appareils personnels. La visualisation treemap fournit des insights sur les différents types d’appareils. Vous pouvez consulter le nombre d’appareils iOS/iPadOS, Android et Windows qui appartiennent à l’entreprise ou qui sont des appareils personnels.

## <a name="overview-of-creating-the-chart"></a>Vue d’ensemble de la création du graphique

Pour créer ce graphique, effectuez les étapes suivantes :
1. Installez Power BI Desktop si ce n’est pas déjà fait.
2. Connectez-vous au modèle de données de l’entrepôt de données Intune et récupérez les données actuelles du modèle.
3. Créez ou gérez les relations du modèle de données.
4. Créez le graphique avec les données de la table **devices**.
5. Créez un filtre interactif.
6. Affichez le graphique terminé.

### <a name="a-note-about-tables-and-entities"></a>Remarque à propos des tables et des entités

Dans Power BI, vous travaillez avec des tables. Une table contient des champs de données. Chaque champ de données a un type de données. Le champ ne peut contenir que des données du type de données (nombre, texte, date, etc.). Quand vous chargez le modèle dans Power BI, les tables sont remplies avec les données d’historique récentes de votre locataire. Bien que les données spécifiques évoluent au fil du temps, la structure de la table ne change pas, sauf si le modèle de données sous-jacent est mis à jour.

Les termes *entité* et *table* peuvent prêter à confusion. Le modèle de données est accessible par le biais d’un flux OData (Open Data Protocol). Dans l’univers OData, les conteneurs appelés tables dans Power BI sont appelés des entités. Ces termes font tous les deux référence au même conteneur de données. Pour plus d’informations sur OData, consultez la [Vue d’ensemble d’OData](/odata/overview).

## <a name="install-power-bi-desktop"></a>Installer Power BI Desktop

Installez la dernière version de Power BI Desktop. Power BI Desktop est disponible en téléchargement à l’emplacement suivant : [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Se connecter au flux OData pour l’entrepôt de données Intune de votre locataire

> [!Note]  
> Vous devez être autorisé à accéder à **Rapports** dans Intune. Pour plus d’informations, consultez [Autorisation](../reports-api-url.md).

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Ouvrez le volet **Intune Data Warehouse** en sélectionnant le lien Data Warehouse sous **Autres tâches** sur le côté droit du panneau **Microsoft Intune - Vue d’ensemble**.
3. Copier l’URL du flux personnalisé. Par exemple : `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Ouvrez Power BI Desktop.
5. Dans la barre de menus, sélectionnez **Fichier** > **Obtenir des données** > **Flux OData**.
6. Collez l’URL du flux personnalisé, que vous avez copiée à l’étape précédente, dans la zone URL de la fenêtre **Flux OData**.
7. Sélectionnez **De base**.

    ![Flux OData pour l’entrepôt de données Intune de votre abonné](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. Sélectionnez **OK**.
9. Sélectionnez **Compte professionnel**, puis connectez-vous avec vos informations d’identification Intune.

    ![Informations d’identification du compte professionnel](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. Sélectionnez **Connexion**. Le Navigateur s’ouvre et affiche la liste des tables dans l’entrepôt de données Intune.

    ![Capture d’écran du navigateur - liste des tables de l’entrepôt de données](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. Sélectionnez les tables **devices** et **ownerTypes**.  Sélectionnez **Charger**. Power BI charge les données dans le modèle.

## <a name="create-a-relationship"></a>Créer une relation

Vous pouvez importer plusieurs tables pour analyser non seulement les données dans une table unique, mais aussi les données connexes contenues dans plusieurs tables. Power BI comprend une fonctionnalité appelée **Détection automatique** qui recherche et crée des relations pour vous. Les tables de l’entrepôt de données sont générées pour fonctionner avec la fonctionnalité de détection automatique de Power BI. Toutefois, même si Power BI ne trouve pas automatiquement de relations, vous pouvez toujours gérer les relations.

![Gérer les relations des données associées entre les tables](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. Sélectionnez **Gérer les relations**.
2. Sélectionnez **Détection automatique** si Power BI n’a pas encore détecté les relations.

La relation est présentée dans une colonne De et une colonne À. Dans cet exemple, le champ de données **ownerTypeKey** dans la table **devices** est lié au champ de données **ownerTypeKey** dans la table **ownerTypes**. Vous utilisez la relation pour rechercher le nom brut du code de type d’appareil dans la table **devices**.

## <a name="create-a-treemap-visualization"></a>Créer une visualisation treemap

Un graphique treemap affiche les données hiérarchiques sous forme de zones dans des zones. Chaque branche de la hiérarchie est une zone qui contient des zones plus petites correspondant à des sous-branches. Vous pouvez utiliser Power BI Desktop pour créer un treemap de vos données de locataire Intune qui affichent des quantités relatives de types de fabricants d’appareils.

![Visualisations treemap Power BI](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. Dans le volet **visualisations**, recherchez et sélectionnez **TreeMap**. Le **graphique de compartimentage** sera ajouté au canevas de rapport.
2. Dans le volet **Champs**, recherchez la table `devices`.
3. Développez la table `devices`, puis sélectionnez le champ de données `manufacturer`.
4. Faites glisser le champ de données `manufacturer` dans le canevas de rapport, puis placez-le sur le graphique **Treemap**.
5. Faites glisser `deviceKey` le champ de données `devices` de la table vers le volet **visualisations** et déposez-le sous la section **valeurs** de la zone intitulée **Ajouter des champs de données ici**.  

Vous disposez maintenant d’un visuel qui montre la distribution des fabricants d’appareils dans votre organisation.

![TreeMap avec des données - distribution des fabricants d’appareils](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Ajouter un filtre

Pour répondre à des questions supplémentaires à l’aide de votre application, vous pouvez ajouter un filtre à votre treemap.

1. Pour ajouter un filtre, sélectionnez le canevas de rapport, puis l’**icône Segment** (![Treemap avec le modèle de données et les relations prises en charge](./media/reports-proc-create-with-odata/reports-create-slicer.png)) sous **Visualisations**. La visualisation **Segment** vide apparaît sur le canevas.
2. Dans le volet **Champs**, recherchez la table `ownerTypes`.
3. Développez la table `ownerTypes`, puis sélectionnez le champ de données `ownerTypeName`.
4. Faites glisser `onwerTypeName` le champ de données `ownerTypes` de la table vers le volet **Filtres** et déposez-le sous la section **Filtres sur cette page** de la zone intitulée **Ajouter des champs de données ici**.  

   Sous la table `OwnerTypes` se trouve un champ appelé `OwnerTypeKey`. Il contient des données indiquant si un appareil appartient à l’entreprise ou s’il est personnel. Pour afficher des noms conviviaux dans ce filtre, recherchez la table `ownerTypes` et faites glisser le champ de données **ownerTypeName** vers le segment. Cet exemple montre comment le modèle de données prend en charge les relations entre les tables.

![TreeMap avec un filtre - prise en charge des relations entre les tables](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

Vous disposez maintenant d’un filtre interactif qui vous permet de basculer entre les appareils d’entreprise et les appareils personnels. Utilisez ce filtre pour voir comment la distribution change.

1. Sélectionnez **Company** (Entreprise) pour voir la distribution des appareils appartenant à l’entreprise.
2. Sélectionnez **Personal** (Personnel) dans le segment pour voir les appareils personnels.

## <a name="next-steps"></a>Étapes suivantes

- Découvrez plus en détail [la création et la gestion des relations](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) dans Power BI Desktop dans la documentation sur Power BI.
- Consultez le [modèle de l’entrepôt de données Intune](reports-ref-data-model.md).
