---
title: Audit des modifications et les événements dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez comment consulter les journaux d’audit qui consignent les activités Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394899"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Utiliser les journaux d’audit pour suivre et surveiller les événements dans Microsoft Intune

Les journaux d’audit consignent les activités qui génèrent un changement dans Microsoft Intune. Créer, mettre à jour (modifier), delete, affectez et actions à distance, créent des événements d’audit que les administrateurs peuvent consulter pour la plupart des charges de travail Intune. Par défaut, l’audit est activé pour tous les clients. Elle ne peut pas être désactivée.

> [!NOTE]
> Auditer les événements de début de l’enregistrement sur la version de décembre 2017. Les événements antérieurs ne sont pas disponibles.

## <a name="who-can-access-the-data"></a>Qui peut accéder aux données ?

Les utilisateurs disposant des autorisations suivantes peuvent consulter les journaux d’audit :

- Administrateur général
- Administrateur du service Intune
- Les administrateurs ayant un rôle Intune avec les autorisations **Données d’audit** - **Lecture**

## <a name="audit-logs-for-intune-workloads"></a>Journaux d’audit pour les charges de travail Intune

Vous pouvez consulter les journaux d’audit dans le groupe d’analyse pour chaque charge de travail Intune :

1. Dans le [portail Azure](https://portal.azure.com/), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.
2. Choisissez la charge de travail que vous souhaitez consulter les journaux d’audit. Par exemple, sélectionnez **appareils**.
3. Sous **surveillance**, choisissez **journaux d’Audit**.

## <a name="route-logs-to-azure-monitor"></a>Router des journaux vers Azure Monitor

Journaux d’audit et journaux des opérations peuvent également être routées vers Azure Monitor. Dans **journaux d’Audit**, sélectionnez **exporter les paramètres de données**:

![Exporter des données de journal dans Azure monitor en sélectionnant les paramètres de données d’exportation dans Intune](./media/audit-logs-export-data-settings.png)

Pour plus d’informations sur cette fonctionnalité, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Consulter les journaux d'audit

![Choisissez les journaux d’audit dans Intune pour voir les actions et les dates lorsque les événements survenus](./media/monitor-audit-logs.png "journaux d’Audit")

Un journal d’audit propose par défaut une vue par liste qui affiche les éléments suivants :

- Date et heure de l’événement
- Initié par (acteur)
- Nom de l'application
- Activité
- Cible(s)
- Catégorie
- État

Pour afficher des informations plus spécifiques sur un événement, sélectionnez un élément dans la liste :

![Obtenir des informations spécifiques sur qui a fait que dans l’audit journaux dans Intune](./media/monitor-audit-log-detail.png "les détails du journal d’Audit")

> [!NOTE]
> **Initié par (acteur)** inclut des informations sur qui ont exécuté la tâche, et où il a été exécuté. Par exemple, si vous exécutez l’activité dans Intune dans le portail Azure, **Application** répertorie toujours **Extension du portail Microsoft Intune** et **l’ID d’application** utilise toujours le même GUID.
> 
> La section **Cible(s)** répertorie plusieurs cibles et les propriétés qui ont été modifiées.  

## <a name="filter-audit-events"></a>Filtrer les événements d’audit

Chaque charge de travail comporte un élément de menu qui pré-filtre la catégorie d’événements d’audit associée à ce volet. Une option de filtre distincte vous permet de sélectionner d’autres catégories ainsi que les détails de l’action de l’événement pour cette catégorie. Vous pouvez rechercher par nom UPN, telles que l’utilisateur qui a effectué l’action. Un filtre de plage de dates permet d’afficher les dernières 24 heures, les 7 derniers jours ou les 30 derniers jours. Par défaut, les événements d’audit des 30 derniers jours sont affichés.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utiliser l’API Graph pour récupérer des événements d’audit

Pour plus d’informations sur l’utilisation de l’API graph pour obtenir jusqu'à un an d’événements d’audit, consultez [liste des événements d’audit](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Étapes suivantes

[Envoyer des données de journal vers le stockage, concentrateurs d’événements, ou ouvrir une session analytique](review-logs-using-azure-monitor.md).

[Consulter les journaux de la protection des applications clientes](app-protection-policy-settings-log.md).
