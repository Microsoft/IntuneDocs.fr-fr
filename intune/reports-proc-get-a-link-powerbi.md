---
title: Se connecter à l’entrepôt de données avec Power BI
titlesuffix: Microsoft Intune
description: Vous pouvez télécharger un fichier destiné à Microsoft Power BI qui vous permet de charger des rapports interactifs et dynamiques pour votre locataire Microsoft Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/28/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b93bb9911fa93998e443a797d085a568280c278
ms.sourcegitcommit: e23e78a563928ed2b2cbc588f2aa65678f7bb409
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58618499"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Se connecter à l’entrepôt de données avec Power BI

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez télécharger un fichier destiné à Microsoft Power BI qui vous permet de charger des rapports interactifs et dynamiques pour votre locataire Intune. Le fichier Power BI (pbix) d’entrepôt de données contient des paramètres de connexion à votre locataire ainsi que les exemples de rapports et de graphiques suivants :  

  -  Périphériques
  -  Inscription
  -  Stratégie de protection des applications
  -  Stratégie de conformité
  -  Profils de configuration d’appareil
  -  Mises à jour logicielles
  -  Journaux d’inventaire des appareils

Les tendances sont également mises en évidence dans les catégories suivantes : inscription, conformité, profil de configuration d’appareil et mises à jour logicielles. Les exemples de graphiques et de rapports appliquent des filtres conviviaux au canevas. Pour utiliser des filtres avancés, explorez le volet **Filtre** dans Power BI Desktop.

Les étapes suivantes vous montrent comment télécharger le fichier Power BI et comment utiliser le lien OData avec Power BI.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Installer Power BI

Installez la dernière version de Power BI Desktop. Power BI Desktop est disponible en téléchargement à l’emplacement suivant : [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Charger les données et les rapports à l’aide du fichier Power BI (pbix)

Le fichier Power BI (pbix) contient les informations de connexion pour votre locataire et un ensemble de rapports prédéfinis basés sur le modèle de données de l’entrepôt de données. Ouvrez le fichier dans Power BI Desktop et connectez-vous à Azure AD. Le rapport charge les données de votre locataire Intune.

> [!Important]  
> Les fichiers Power BI (pbix) peuvent varier selon l’emplacement du locataire. Si vous gérez plusieurs locataires Intune, veillez à utiliser le fichier téléchargé à partir du portail Azure tout en étant connecté au locataire.  

1.  Connectez-vous au portail Azure et choisissez **Surveillance + gestion** > **Intune**. Vous pouvez aussi rechercher **Intune** dans les ressources.  
2.  Ouvrez le **configurer l’entrepôt de données Intune** panneau.
3.  Sélectionnez **Télécharger le fichier Power BI**. Un fichier portant l’extension pbix est téléchargé à l’emplacement indiqué.
4.  Ouvrez le fichier avec Power BI. Les *rapports de l’entrepôt de données Intune* se chargent, mais l’obtention des données de votre locataire peut prendre quelques secondes.
5.  Sélectionnez **Actualiser** pour charger les données de votre locataire et passer en revue les rapports.
6.  Si Power BI n’a pas été authentifié avec vos informations d’identification Azure Active Directory, vous êtes invité à les entrer. Quand vous sélectionnez vos informations d’identification, choisissez **Compte professionnel** comme méthode d’authentification.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Charger les données dans Power BI à l’aide du lien OData

Quand un client est authentifié auprès d’Azure AD, l’URL OData se connecte au point de terminaison RESTful dans l’API d’entrepôt de données qui expose le modèle de données à votre client de création de rapports. Pour utiliser Power BI Desktop pour vous connecter et créer vos propres rapports, suivez ces instructions. Vous n’êtes pas limité à Power BI Desktop. Vous pouvez utiliser votre outil d’analyse préféré avec l’URL OData, à condition toutefois que le client prenne en charge l’authentification OAUTH2.0 et la norme OData v4.0.

1.  Connectez-vous au portail Azure et choisissez **Surveillance + gestion** > **Intune**. Vous pouvez aussi rechercher **Intune** dans les ressources.  
2.  Ouvrez le **configurer l’entrepôt de données Intune** panneau.
3. Récupérez l’URL du flux personnalisé dans le panneau de création de rapports, par exemple, `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4. Ouvrez **Power BI Desktop**.
5. Choisissez **Accueil** > **Obtenir des données**. Sélectionnez **Flux OData**.
6. Choisissez **De base**.
7. Tapez ou collez l’**URL OData** dans la zone URL.
8. Sélectionnez **OK**.
9. Si vous n’êtes pas authentifié auprès d’Azure AD pour votre locataire à partir du client Power BI Desktop, tapez vos informations d’identification. Pour accéder à vos données, vous devez obtenir l’autorisation auprès d’Azure Active Directory (Azure AD) à l’aide d’OAuth 2.0.  
    1.  Sélectionnez **Compte professionnel**.  
    2.  Tapez vos nom d’utilisateur et mot de passe.  
    3.  Sélectionnez **Se connecter.**  
    4.  Sélectionnez **Connexion**.  
10. Sélectionnez **Charger**.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez obtenir les réponses aux questions relatives à votre environnement, par exemple le nombre d’appareils inscrits par jour au cours de la semaine dernière. Vous pouvez obtenir des insights sur votre population de locataires et de clients Intune à l’aide des rapports basés sur le fichier Power BI (pbix) de l’entrepôt de données Intune récupéré à partir du panneau dans Azure. Toutefois, Intune vous propose plusieurs façons d’étendre ou de réutiliser les données. Power BI et l’API d’entrepôt de données Intune offrent bien d’autres fonctionnalités, par exemple :

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  Les données du locataire sont organisées pour vous aider à obtenir des insights sur vos données. Pour plus d’informations sur la façon dont les données sont organisées, consultez [Modèle de données de l’entrepôt de données](reports-ref-data-model.md).
 -  Vous pouvez également accéder aux données à partir d’une interface RESTful et les incorporer à votre propre application. Pour plus d’informations, consultez [Obtenir des données à partir de l’API d’entrepôt de données avec un client REST](reports-proc-data-rest.md).
