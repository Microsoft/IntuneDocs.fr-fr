---
title: Se connecter à l’entrepôt de données avec Power BI
titleSuffix: Microsoft Intune
description: Vous pouvez télécharger un fichier destiné à Microsoft Power BI qui vous permet de charger des rapports interactifs et dynamiques pour votre locataire Microsoft Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ee5cdb6bbdcce229fbc217726a1ee118f77beff
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733411"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Se connecter à l’entrepôt de données avec Power BI

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez utiliser l’application de conformité Power BI afin de charger des rapports interactifs générés dynamiquement pour votre locataire Intune. Vous pouvez aussi charger vos données de locataire dans Power BI en utilisant le lien OData. Intune fournit des paramètres de connexion à votre locataire pour que vous puissiez afficher les exemples de rapports suivants ainsi que leurs graphiques :  

- Appareils
- Inscription
- Stratégie de protection des applications
- Stratégie de conformité
- Profils de configuration d’appareil
- Mises à jour logicielles
- Journaux d’inventaire des appareils

Les tendances sont également mises en évidence dans les catégories suivantes : inscription, conformité, profil de configuration d’appareil et mises à jour logicielles. Les exemples de graphiques et de rapports appliquent des filtres conviviaux au canevas. Pour utiliser des filtres avancés, explorez le volet **Filtre** dans Power BI Desktop.

Les étapes suivantes vous montrent comment télécharger le fichier Power BI et comment utiliser le lien OData avec Power BI.

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Installer Power BI

Installez la dernière version de [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi). Pour plus d’informations, consultez [Power BI Desktop](https://powerbi.microsoft.com/desktop).

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>Charger les données et les rapports à l’aide de l’application de conformité Power BI pour l’entrepôt de données Intune

L’[application de conformité pour l’entrepôt de données Intune](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) Power BI contient les informations de connexion pour votre locataire ainsi qu’un ensemble de rapports prédéfinis basés sur le modèle de données de l’entrepôt de données.

1. Accédez à la page **AppSource** de l’application de [mise en conformité pour l’entrepôt de données Intune](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) pour lancer le processus d’installation.
2. Cliquez sur le bouton **Télécharger maintenant** , puis sur **Continuer**.
3. Lorsque vous êtes invité à installer l’application Power BI, cliquez sur **installer**.
4. Une fois l’installation terminée, cliquez sur la vignette application de **conformité Intune (Data Warehouse)** .
5. Cliquez sur le bouton **Connecter**. La boîte de dialogue de **connexion à l’application de conformité pour l’entrepôt de données Intune** s’affiche.
6. Cliquez sur le bouton **Se connecter**.
7. Connectez-vous avec un compte d’utilisateur pouvant accéder à l’entrepôt de données Intune du locataire qui a des rapports que vous souhaitez voir.
8. Pour afficher le tableau de bord inclus, cliquez sur l’onglet **tableaux de bord** , puis sur le tableau de bord **vue d’ensemble** de la conformité.
9. Pour afficher tous les rapports disponibles, cliquez sur l’onglet **rapports** , puis sur le rapport **conformité v 1.0** . Parcourez les pages du rapport en cliquant sur les onglets en bas.
10. Pour revenir plus facilement à ces rapports, cliquez sur l’étoile en regard du rapport **Compliance V1.0**. Cette opération ajoute le rapport à vos favoris Power BI.

Vous pouvez également installer l’application à partir du portail Intune :

1. Connectez-vous au portail Azure et choisissez **Surveillance + gestion** > **Intune**. Vous pouvez également rechercher des ressources Intune.
2. Ouvrez le panneau **Configurer l’entrepôt de données Intune**.
3. Sélectionnez **Obtenir l’application Power BI** pour accéder aux rapports Power BI précréés du locataire et les partager dans le navigateur.
4. Suivez les étapes 2 à 10 ci-dessus.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Charger les données dans Power BI à l’aide du lien OData

Quand un client est authentifié auprès d’Azure AD, l’URL OData se connecte au point de terminaison RESTful dans l’API d’entrepôt de données qui expose le modèle de données à votre client de création de rapports. Pour utiliser Power BI Desktop pour vous connecter et créer vos propres rapports, suivez ces instructions. Vous n’êtes pas limité à Power BI Desktop. Vous pouvez utiliser votre outil d’analyse préféré avec l’URL OData, à condition toutefois que le client prenne en charge l’authentification OAUTH2.0 et la norme OData v4.0.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Cliquez sur **configurer Intune Data Warehouse** sous la section **autres tâches** sur le côté droit du panneau vue d’ensemble. Le panneau **Data Warehouse Intune** s’affiche.
3. Récupérez l’URL du flux personnalisé dans le panneau de création de rapports, par exemple : `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Ouvrez **Power BI Desktop**.
5. Choisissez **Accueil** > **Obtenir des données**. Sélectionnez **Flux OData**.
6. Choisissez **De base**.
7. Tapez ou collez l’**URL OData** dans la zone URL.
8. Sélectionnez **OK**.
9. Si vous n’êtes pas authentifié auprès d’Azure AD pour votre locataire à partir du client Power BI Desktop, tapez vos informations d’identification. Pour accéder à vos données, vous devez obtenir l’autorisation auprès d’Azure Active Directory (Azure AD) à l’aide d’OAuth 2.0.  
    1. Sélectionnez **Compte professionnel**.  
    2. Tapez vos nom d’utilisateur et mot de passe.  
    3. Sélectionnez **Se connecter.**  
    4. Sélectionnez **Connexion**.  
10. Sélectionnez **Charger**.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez obtenir les réponses aux questions relatives à votre environnement, par exemple le nombre d’appareils inscrits par jour au cours de la semaine dernière. Vous pouvez obtenir des insights sur votre population de locataires et de clients Intune à l’aide des rapports Power BI sur l’entrepôt de données Intune récupérés à partir du panneau dans Azure. Toutefois, Intune vous propose plusieurs façons d’étendre ou de réutiliser les données. Power BI et l’API Intune Data Warehouse fournissent des fonctionnalités supplémentaires, par exemple :

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- Les données du locataire sont organisées pour vous aider à obtenir des insights sur vos données. Pour plus d’informations sur la façon dont les données sont organisées, consultez [Modèle de données de l’entrepôt de données](reports-ref-data-model.md).
- Vous pouvez également accéder aux données à partir d’une interface RESTful et les incorporer à votre propre application. Pour plus d’informations, consultez [Obtenir des données à partir de l’API d’entrepôt de données avec un client REST](../reports-proc-data-rest.md).
