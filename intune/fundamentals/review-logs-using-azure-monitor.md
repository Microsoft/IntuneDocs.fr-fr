---
title: Router des journaux vers Azure Monitor à l’aide de Microsoft Intune - Azure | Microsoft Docs
description: Utilisez les paramètres de diagnostic pour envoyer les journaux d’audit et des opérations dans Microsoft Intune à Azure (comptes de stockage, hubs d’événements ou Log Analytics). Choisissez la durée pendant laquelle vous souhaitez conserver les données et passez en revue les estimations de coûts pour des locataires de tailles différentes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 95191d64-9895-4f2e-8c5b-f0e85be086d8
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a9c74281df61fbf81914461286353d49b89a4f9
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510743"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune (préversion)

Microsoft Intune intègre des journaux qui fournissent des informations sur votre environnement :

- Les **journaux d’audit** montrent un enregistrement des activités qui génèrent une modification dans Intune, notamment les actions créer, mettre à jour (modifier), supprimer et attribuer, et les actions à distance.
- Les **journaux des opérations (préversion)** donnent des détails sur les utilisateurs et les appareils dont l’inscription a réussi (ou échoué), ainsi que des détails sur les appareils non conformes.
- Les **journaux organisationnels de conformité des appareils (préversion)** montrent un rapport organisationnel de conformité des appareils dans Intune, et des détails sur les appareils non conformes.

Ces journaux peuvent également être envoyés à des services Azure Monitor, notamment des comptes de stockage, des hubs d’événements et Log Analytics. Plus précisément, vous pouvez :

* Archiver les journaux Intune dans un compte de stockage Azure pour conserver les données ou les archiver pendant une durée définie.
* Diffuser en streaming les journaux Intune vers un hub d’événements Azure, à des fins analytiques, à l’aide d’outils SIEM (Security Information and Event Management) tels que Splunk et QRadar.
* Intégrer les journaux Intune à vos propres solutions de journal personnalisées en les diffusant en streaming vers un hub d’événements.
* Envoyer les journaux Intune à Log Analytics pour bénéficier de visualisations enrichies et de fonctionnalités de supervision et d’alerte sur les données connectées.

Ces fonctionnalités font partie des **paramètres de diagnostic** dans Intune.

Cet article montre comment utiliser les **paramètres de diagnostic** pour envoyer les données de journal à différents services, donne des exemples et des estimations de coûts, et répond à certaines questions fréquemment posées. Une fois cette fonctionnalité activée, vos journaux sont routés vers le service Azure Monitor que vous choisissez.

## <a name="prerequisites"></a>Prérequis

Pour utiliser cette fonctionnalité, vous avez besoin des éléments suivants :

* Un abonnement Azure. Si vous n’avez pas d’abonnement Azure, [inscrivez-vous pour obtenir un essai gratuit](https://azure.microsoft.com/free/).
* Un environnement Microsoft Intune (locataire) dans Azure.
* Un utilisateur qui est **administrateur général** ou **administrateur de service Intune** pour le locataire Intune.

Selon l’endroit où vous souhaitez acheminer les données du journal d’audit, vous devez disposer de l’un des services suivants :

* Un [compte de stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview) avec des autorisations*ListKeys*. Nous vous recommandons d’utiliser un compte de stockage général, et non un compte de stockage d’objets blob. Pour connaître les tarifs du stockage, consultez le [calculateur de prix du stockage Azure](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* L’[espace de noms d’un hub d’événements Azure](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) à intégrer à des solutions tierces.
* Un [espace de travail Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) pour envoyer les journaux à Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Envoyer des journaux à Azure Monitor

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Rapports** > **Paramètres de diagnostic**. Vous devez les activer la première fois que vous les utilisez. Sinon, ajoutez un paramètre.

    > [!div class="mx-imgBorder"]
    > ![Activer Paramètres de diagnostic dans Intune pour envoyer les journaux à Azure Monitor](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. Entrez les propriétés suivantes :

    - **Nom** : donnez un nom aux paramètres de diagnostic. Ce paramètre inclut toutes les propriétés que vous entrez. Par exemple, entrez `Route audit logs to storage account`.
    - **Archiver dans un compte de stockage** : enregistre les données de journal dans un compte de stockage Azure. Utilisez cette option pour enregistrer ou archiver les données.

        1. Sélectionnez cette option > **Configurer**. 
        2. Choisissez un compte de stockage existant à partir de la liste > **OK**.

    - **Diffuser vers un hub d’événements** : diffuse en streaming les journaux vers un hub d’événements Azure. Si vous souhaitez analyser vos données de journal à l’aide d’outils SIEM tels que Splunk et QRadar, choisissez cette option.

        1. Sélectionnez cette option > **Configurer**. 
        2. Choisissez l’espace de noms et la stratégie d’un hub d’événements existant dans la liste > **OK**.

    - **Envoyer à Log Analytics** : envoie les données à Azure Log Analytics. Si vous souhaitez bénéficier de fonctionnalités de visualisation, de supervision et d’alerte pour vos journaux, choisissez cette option.

        1. Sélectionnez cette option > **Configurer**. 
        2. Créez un espace de travail, puis entrez les détails de l’espace de travail. Vous pouvez également choisir un espace de travail existant dans la liste > **OK**.

            L’article consacré à la [création d’un espace de travail Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) fournit plus de détails sur ces paramètres.

    - **LOG** > **AuditLogs** : choisissez cette option pour envoyer les [journaux d’audit Intune](../monitor-audit-logs.md) à votre compte de stockage, votre hub d’événements ou Log Analytics. Les journaux d’audit affichent l’historique de chaque tâche générant un changement dans Intune, avec notamment des informations sur l’initiateur de la tâche et la date et l’heure auxquelles elle a eu lieu.

      Si vous choisissez d’utiliser un compte de stockage, entrez également le nombre de jours pendant lesquels vous souhaitez conserver les données. Pour conserver les données indéfiniment, définissez **Conservation (jours)** avec la valeur `0` (zéro).

    - **LOG** > **OperationalLogs** : les journaux des opérations (préversion) indiquent la réussite ou l’échec des utilisateurs et des appareils qui s’inscrivent dans Intune, ainsi que des détails sur les appareils non conformes. choisissez cette option pour envoyer les journaux d’inscription à votre compte de stockage, à votre hub d’événements ou à Log Analytics.

      Si vous choisissez d’utiliser un compte de stockage, entrez également le nombre de jours pendant lesquels vous souhaitez conserver les données. Pour conserver les données indéfiniment, définissez **Conservation (jours)** avec la valeur `0` (zéro).

      > [!NOTE]
      > Les journaux des opérations sont en préversion. Pour fournir des commentaires, notamment des informations incluses dans les journaux des opérations, accédez à [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    - **LOG** > **DeviceComplianceOrg** : Les journaux organisationnels de conformité des appareils (préversion) montrent le rapport organisationnel de conformité des appareils dans Intune, et des détails sur les appareils non conformes. Choisissez cette option pour envoyer les journaux de conformité à votre compte de stockage, votre hub d’événements ou Log Analytics.

      Si vous choisissez d’utiliser un compte de stockage, entrez également le nombre de jours pendant lesquels vous souhaitez conserver les données. Pour conserver les données indéfiniment, définissez **Conservation (jours)** avec la valeur `0` (zéro).
 
      > [!NOTE]
      > Les journaux organisationnels de conformité des appareils sont en préversion. Pour fournir des commentaires, notamment des informations incluses dans le rapport, accédez à [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback).

    Quand vous avez terminé, vos paramètres ressemblent aux suivants : 

    > [!div class="mx-imgBorder"]
    > ![Exemple d’image qui envoie des journaux d’audit Intune à un compte de stockage Azure](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. **Enregistrez** les changements apportés. Votre paramètre est affiché dans la liste. Une fois le paramètre créé, vous pouvez le changer en sélectionnant **Modifier le paramètre** > **Enregistrer**.

## <a name="use-audit-logs-throughout-intune"></a>Utiliser les journaux d’audit dans Intune

Vous pouvez également exporter les journaux d’audit dans d’autres parties d’Intune, notamment l’inscription, la conformité, la configuration, les appareils, les applications clientes et bien plus encore.

Pour plus d’informations, consultez [Utiliser les journaux d’audit pour suivre et surveiller les événements](monitor-audit-logs.md). Vous pouvez choisir où envoyer les journaux d’audit, comme décrit dans [Envoyer des journaux à Azure Monitor](#send-logs-to-azure-monitor) (dans cet article).

## <a name="cost-considerations"></a>Considérations relatives aux coûts

Si vous avez déjà une licence Microsoft Intune, vous devez disposer d’un abonnement Azure pour configurer le compte de stockage et le hub d’événements. L’abonnement Azure est généralement gratuit. Toutefois, vous payez l’utilisation des ressources Azure, notamment le compte de stockage pour l’archivage et le hub d’événements pour le streaming. La quantité de données et les coûts varient en fonction de la taille du locataire.

### <a name="storage-size-for-activity-logs"></a>Taille de stockage pour les journaux d’activité

Chaque événement du journal d’audit utilise environ 2 Ko de stockage de données. Pour un locataire avec 100 000 utilisateurs, vous pouvez avoir environ 1,5 million d’événements par jour. Vous pouvez avoir besoin d’environ 3 Go par jour pour stocker vos données. Comme les écritures se produisent généralement par lots de cinq minutes, vous pouvez vous attendre à environ 9 000 opérations d’écriture par mois.

Les tableaux suivants présentent une estimation des coûts en fonction de la taille du locataire. Un compte de stockage v2 universel est également inclus dans la région USA Ouest pour conserver les données pendant au moins un an. Pour obtenir une estimation du volume de données attendu pour vos journaux, utilisez le [calculateur de prix du stockage Azure](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Journal d’audit avec 100 000 utilisateurs**

| | |
|---|---|
|Événements par jour| 1,5 million|
|Estimation du volume de données par mois| 90 Go|
|Estimation du coût par mois (USD)| 1,93 $|
|Estimation du coût par an (USD)| 23,12 $|

**Journal d’audit avec 1 000 utilisateurs**

| | |
|---|---|
|Événements par jour| 15 000|
|Estimation du volume de données par mois| 900 Mo|
|Estimation du coût par mois (USD)| 0,02 $|
|Estimation du coût par an (USD)| 0,24 $|

### <a name="event-hub-messages-for-activity-logs"></a>Messages du hub d’événements pour les journaux d’activité

Les événements sont généralement mis en lot par intervalles de cinq minutes, puis envoyés sous forme d’un message unique contenant tous les événements de cette période. Un message dans le hub d’événements a une taille maximale de 256 Ko. Si la taille totale de tous les messages dans la période dépasse ce volume, plusieurs messages sont alors envoyés.

Par exemple, environ 18 événements par seconde se produisent généralement pour un grand locataire de plus de 100 000 utilisateurs. Cela équivaut à 5 400 événements toutes les cinq minutes (300 secondes x 18 événements). Les journaux d’audit font environ 2 Ko par événement. Cela équivaut à 10,8 Mo de données. Ainsi, 43 messages sont envoyés au hub d’événements dans cet intervalle de cinq minutes.

Le tableau suivant présente l’estimation des coûts mensuels pour un hub d’événements de base dans la région USA Ouest, en fonction du volume des données d’événement. Pour obtenir une estimation du volume de données attendu pour vos journaux, utilisez le [calculateur de prix Event Hubs](https://azure.microsoft.com/pricing/details/event-hubs/).

**Journal d’audit avec 100 000 utilisateurs**

| | |
|---|---|
|Événements par seconde| 18|
|Événements par intervalle de cinq minutes| 5 400|
|Volume par intervalle| 10,8 Mo|
|Messages par intervalle| 43|
|Messages par mois| 371 520|
|Estimation du coût par mois (USD)| 10,83 $|

**Journal d’audit avec 1 000 utilisateurs**

| | |
|---|---|
|Événements par seconde|0,1 |
|Événements par intervalle de cinq minutes| 52|
|Volume par intervalle|104 Ko |
|Messages par intervalle|1 |
|Messages par mois|8 640 |
|Estimation du coût par mois (USD)|10,80 $ |

### <a name="log-analytics-cost-considerations"></a>Considérations relatives aux coûts de Log Analytics

Pour passer en revue les coûts liés à la gestion de l’espace de travail Log Analytics, consultez [Gérer les coûts en contrôlant le volume et la conservation des données dans Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Forum aux questions

Obtenez des réponses aux questions fréquemment posées et découvrez les problèmes connus liés aux journaux Intune dans Azure Monitor.

### <a name="which-logs-are-included"></a>Quels journaux sont inclus ?

Les journaux d’audit et les journaux des opérations (préversion) peuvent être acheminés à l’aide de cette fonctionnalité.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Après une action, quand les journaux correspondants apparaissent-ils dans le hub d’événements ?

Les journaux apparaissent généralement dans votre hub d’événements dans les minutes qui suivent l’action. L’article de [présentation d’Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs/) fournit des informations supplémentaires.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Après une action, quand les journaux correspondants apparaissent dans le compte de stockage ?

Pour les comptes de stockage Azure, la latence va de 5 à 15 minutes après l’exécution de l’action.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>Que se passe-t-il si un administrateur change la période de conservation d’un paramètre de diagnostic ?

La nouvelle stratégie de conservation est appliquée aux journaux collectés après le changement. Les journaux collectés avant le changement de stratégie ne sont pas affectés.

### <a name="how-much-does-it-cost-to-store-my-data"></a>Combien coûte le stockage de mes données ?

Les coûts de stockage dépendent de la taille de vos journaux et de la période de conservation que vous choisissez. Pour obtenir la liste des estimations de coûts pour les locataires, en fonction du volume du fichier journal généré, consultez [Taille de stockage pour les journaux d’activité](#storage-size-for-activity-logs) (dans cet article).

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Combien coûte le streaming de mes données vers un hub d’événements ?

Les coûts de streaming varient en fonction du nombre de messages reçus par minute. Pour plus d’informations sur le calcul des coûts et les estimations de coûts en fonction du nombre de messages, consultez [Messages du hub d’événements pour les journaux d’activité](#event-hub-messages-for-activity-logs) (dans cet article).

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Comment intégrer les journaux d’audit Intune à mon système SIEM ?

Utilisez Azure Monitor avec Event Hubs pour diffuser en streaming les journaux vers votre système SIEM. Commencez par [diffuser en streaming les journaux vers un hub d’événements](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Ensuite, [configurez votre outil SIEM](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) avec le hub d’événements configuré. 

### <a name="what-siem-tools-are-currently-supported"></a>Quels sont les outils SIEM actuellement pris en charge ?

À l’heure actuelle, Azure Monitor est pris en charge par [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar et [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (ouvre un nouveau site web). Pour plus d’informations sur le fonctionnement des connecteurs, consultez [Diffuser en streaming les données de supervision Azure vers un hub d’événements à des fins de consommation par un outil externe](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Puis-je accéder aux données à partir d’un hub d’événements sans recourir à un outil SIEM externe ?

Oui. Pour accéder aux journaux à partir de votre application personnalisée, vous pouvez utiliser l’[API Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

### <a name="what-data-is-stored"></a>Quelles données sont stockées ?

Intune ne stocke aucune donnée envoyée par le biais du pipeline. Intune achemine les données au pipeline Azure Monitor, sous l’autorité du locataire. Pour plus d’informations, consultez [Vue d’ensemble d’Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Étapes suivantes

* [Archiver les journaux d’activité dans un compte de stockage](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Acheminer les journaux d’activité à un hub d’événements](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Intégrer les journaux d’activité à Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
