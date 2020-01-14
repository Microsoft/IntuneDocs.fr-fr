---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune fournit des types de rapports spécifiques avec des vues ciblées qui contiennent des données cohérentes et ponctuelles.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ae06ae3f9f76d86a792721d45f8319bfe6491fd
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654224"
---
# <a name="intune-reports"></a>Rapports Intune
Les rapports Microsoft Intune vous permettent de surveiller de manière plus efficace et proactive l’intégrité et l’activité des points de terminaison au sein de votre organisation, et fournissent également d’autres données de rapport dans Intune. Par exemple, vous serez en mesure d’afficher des rapports sur la conformité, l’intégrité et les tendances des appareils. En outre, vous pouvez créer des rapports personnalisés pour obtenir des données plus spécifiques. 

> [!NOTE]
> Les modifications apportées à Intune sont déployées progressivement sur une certaine période de temps pour vous aider à vous préparer et à vous adapter à la nouvelle structure.

Les types de rapports sont organisés dans les domaines suivants :
- **Opérationnel** : fournit des données ciblées en temps voulu qui vous aident à vous concentrer et à prendre des mesures. Les administrateurs, les experts techniques et le support technique trouveront ces rapports utiles.
- **Organisationnel** : fournit un résumé plus large d’une vue globale, comme l’état de la gestion des appareils. Les responsables et administrateurs trouveront ces rapports utiles.
- **Historique** : fournit les modèles et tendances sur une période donnée. Les responsables et administrateurs trouveront ces rapports utiles.
- **Spécialiste** : vous permet d’utiliser des données brutes pour créer vos propres rapports personnalisés. Les administrateurs trouveront ces rapports utiles.

L’infrastructure de création de rapports offre une expérience de création de rapports cohérente et plus complète. Les rapports disponibles offrent les fonctionnalités suivantes :
- **Recherche et tri** : vous pouvez rechercher et trier toutes les colonnes, quelle que soit la taille du jeu de données.
- **Pagination des données** : vous pouvez analyser vos données en fonction de la pagination, page par page ou en accédant à une page spécifique.
- **Performances** : vous pouvez rapidement générer et afficher des rapports créés à partir de grands locataires.
- **Exportation** : vous pouvez rapidement exporter les données de rapports générées à partir de clients volumineux.

### <a name="who-can-access-the-data"></a>Qui peut accéder aux données ?

Les utilisateurs disposant des autorisations suivantes peuvent consulter les journaux :

- Administrateur général
- Administrateur du service Intune
- Les administrateurs ayant un rôle Intune avec les autorisations **Lecture**

## <a name="non-compliant-devices-report-operational"></a>Rapport sur les appareils non conformes (opérationnel)
Les appareils non conformes indiquent les données généralement utilisées par le support technique ou les rôles d’administrateur pour identifier les problèmes et les résoudre. Les données qui se trouvent dans ces rapports sont ponctuelles, signalent un comportement inattendu et sont censées être actionnables. Le rapport est disponible en même temps que la charge de travail, ce qui rend le rapport des appareils non conformes accessible sans quitter les workflows actifs. Ce rapport fournit des fonctionnalités de filtrage, de recherche, de pagination et de tri. En outre, vous pouvez accéder à l’aide pour résoudre les problèmes.

Vous pouvez afficher le rapport **Appareils non conformes** en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Surveiller** > **Appareils non conformes**.

    ![Rapport d’appareil non conforme](./media/intune-reports/intune-reports-02.png)

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Conformité de l’appareil** > **Appareils non conformes**.

## <a name="device-compliance-report-organizational"></a>Rapport de conformité des appareils (organisationnel)
Les rapports de conformité des appareils sont conçus pour être exhaustifs et fournissent une vue de rapport plus classique des données pour identifier les métriques agrégées. Ce rapport est conçu pour fonctionner avec des jeux de données volumineux afin d’obtenir une vue complète de la conformité des appareils. Par exemple, le rapport de conformité des appareils pour la conformité des appareils affiche tous les états de conformité des appareils pour fournir une vue plus large des données, quelle que soit la taille du jeu de données. Ce rapport affiche la répartition complète des enregistrements, en plus d’une visualisation pratique des métriques agrégées. Ce rapport peut être généré en appliquant des filtres et en sélectionnant le bouton « Générer le rapport ». Cette opération actualise les données pour afficher l’état le plus récent avec la possibilité d’afficher les enregistrements individuels qui composent les données agrégées. Comme la plupart des rapports dans la nouvelle infrastructure, ces enregistrements peuvent être triés et parcourus pour se concentrer sur les informations dont vous avez besoin. 

Pour afficher un rapport d’état des appareils généré, vous pouvez utiliser les étapes suivantes :
1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Rapports** pour afficher le résumé des rapports.
3. Sélectionnez **Conformité de l’appareil**.
4. Sélectionnez les filtres **État de conformité**, **Système d’exploitation** et **Propriété** pour affiner votre rapport.
5. Cliquez sur **Générer le rapport** (ou **Générer à nouveau**) pour récupérer les données actuelles.

    ![Rapport de conformité des appareils](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Ce rapport de **Conformité des appareils** fournit un horodatage de la dernière génération du rapport. 

Pour les informations liées, consultez [Appliquer la conformité pour Microsoft Defender ATP avec accès conditionnel dans Intune](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Résumé des rapports 

Le rapport de conformité des appareils est disponible sous forme de rapport de synthèse dans la charge de travail **Rapports**. Pour afficher le rapport de conformité des appareils, procédez comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Rapports** pour afficher le résumé des rapports.

    ![Résumé des rapports Intune](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Rapport de tendance de conformité des appareils (historique)
Les rapports de tendance de conformité des appareils sont plus susceptibles d’être utilisés par les administrateurs et architectes pour identifier les tendances à long terme de la conformité des appareils. Les données agrégées sont affichées sur une période donnée et sont utiles pour prendre de futures décisions d’investissement, favoriser l’amélioration des processus ou encourager l’examen des anomalies. Des filtres peuvent également être appliqués pour voir des tendances spécifiques. Les données fournies par ce rapport sont un instantané de l’état actuel du locataire (quasiment en temps réel). 

Un rapport de tendance sur la conformité des appareils pour les tendances de conformité des appareils peut montrer la tendance des états de conformité des appareils sur une période donnée. Vous pouvez identifier l’endroit où les pics de conformité se sont produits et concentrer votre temps et vos efforts en conséquence.

Vous pouvez afficher le rapport **Tendances** en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Rapports** > **Tendances** pour afficher la conformité des appareils sur une tendance de 60 jours.

    ![Rapport de tendance Intune](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Rapports d’intégration Azure Monitor (spécialiste)
Vous pouvez personnaliser vos propres rapports pour obtenir les données souhaitées. Les données de vos rapports seront éventuellement disponibles via [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview), avec [Log Analytics](reports.md#log-analytics) et les [classeurs Azure Monitor](reports.md#workbooks). Ces solutions vous permettent de créer des requêtes personnalisées, de configurer des alertes et de créer des tableaux de bord pour afficher les données de conformité des appareils comme vous le souhaitez. En outre, vous pouvez conserver les journaux d’activité dans votre compte de stockage Azure, les intégrer aux rapports à l’aide des [outils SIEM (Security Information and Event Management)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration) et mettre en corrélation les rapports avec les journaux d’activité d’Azure AD. Les classeurs Azure Monitor peuvent être utilisés en plus de l’importation de tableaux de bord pour les besoins de création de rapports personnalisés.

> [!NOTE]
> Les fonctionnalités de création de rapports complexes nécessitent un abonnement Azure.

Un exemple de rapport spécialisé associe des données de propriétés d’appareil à des données d’inscription de plateforme dans un rapport personnalisé. Ce rapport personnalisé peut ensuite être affiché sur un tableau de bord existant dans le portail Azure Active Directory.

Vous pouvez créer et afficher des rapports personnalisés en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Rapports** > **Paramètres de diagnostic**, puis ajoutez un [Paramètre de diagnostic](reports.md#diagnostic-settings).

    ![Résumé des rapports Intune](./media/intune-reports/intune-reports-04.png)

3. Cliquez sur **Ajouter un paramètre de diagnostic** pour afficher le volet **Paramètres de diagnostic**. 
4. Ajoutez un **Nom** pour les paramètres de diagnostic. 
5. Sélectionnez les paramètres **Envoyer à Log Analytics** et **DeviceComplianceOrg**.

    ![Résumé des rapports Intune](./media/intune-reports/intune-reports-04a.png)

6. Cliquez sur **Save**.
7. Ensuite, sélectionnez **Log Analytics** pour créer et exécuter une nouvelle requête de journal à l’aide de [Log Analytics](reports.md#log-analytics).

   ![Log Analytics - Requête de journal](./media/intune-reports/intune-reports-05.png)

8. Sélectionnez **Classeurs** pour créer ou ouvrir un rapport interactif à l’aide des [classeurs Azure Monitor](reports.md#workbooks).

   ![Classeurs - Rapports interactifs](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Paramètres de diagnostic
Chaque ressource Azure requiert son propre paramètre de diagnostic. Le paramètre de diagnostic définit ce qui suit pour une ressource :

- Catégories de journaux et données de métriques envoyées aux destinations définies dans le paramètre. Les catégories disponibles varient en fonction des types de ressources.
- Une ou plusieurs destinations auxquelles envoyer les journaux. Les destinations actuelles sont l’espace de travail Log Analytics, Event Hubs et le Stockage Azure.
- Stratégie de rétention pour les données stockées dans le Stockage Azure.

Un seul paramètre de diagnostic peut définir l’une des destinations. Si vous souhaitez envoyer des données à plus d’un type de destination (par exemple, deux espaces de travail Log Analytics), créez plusieurs paramètres. Chaque ressource peut avoir jusqu’à 5 paramètres de diagnostic.

Pour plus d’informations sur les paramètres de diagnostic, consultez [Créer un paramètre de diagnostic pour collecter des journaux et métriques de plateforme dans Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Analyse de journal
Log Analytics est le principal outil dans le portail Azure pour l’écriture de requêtes de journal et l’analyse interactive des résultats des requêtes. Même si une requête de journal est utilisée ailleurs dans Azure Monitor, vous allez généralement commencer par écrire et tester la requête dans Log Analytics. Pour plus d’informations sur l’utilisation de Log Analytics et la création de requêtes de journal, consultez [Vue d’ensemble des requêtes de journal dans Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Classeurs
Les classeurs regroupent du texte, des requêtes Analytics, les métriques Azure et des paramètres sous la forme de rapports interactifs riches en contenu. Les classeurs sont modifiables par tous les membres de l’équipe ayant accès aux mêmes ressources Azure. Pour plus d’informations sur les classeurs, consultez [Classeurs Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). En outre, vous pouvez utiliser les modèles de classeur et y contribuer. Pour plus d’informations, consultez [Modèles de classeur Azure Monitor](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>Étapes suivantes 

Découvrez plus en détail les technologies suivantes :
- [Blog - Infrastructure de rapports de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Présentation de Log Analytics](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Requêtes de journal](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Prise en main de Log Analytics dans Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Classeurs Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [Outils Informations et événements gestion des événements (SIEM)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
