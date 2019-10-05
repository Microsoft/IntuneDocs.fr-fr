---
title: Changements et événements d’audit dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez comment consulter les journaux d’audit qui consignent les activités Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d999603abc539fda4d152d15dd1ab965c465f39e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736297"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Utiliser les journaux d’audit pour suivre et superviser les événements dans Microsoft Intune

Les journaux d’audit consignent les activités qui génèrent un changement dans Microsoft Intune. Les opérations de création, de mise à jour (modification), de suppression et d’affectation, ainsi que les opérations distantes, créent des événements d’audit que les administrateurs peuvent consulter pour la plupart des charges de travail Intune. Par défaut, l’audit est activé pour tous les clients. Il ne peut pas être désactivé.

> [!NOTE]
> Les événements d’audit sont enregistrés depuis la version de décembre 2017. Les événements antérieurs ne sont pas disponibles.

## <a name="who-can-access-the-data"></a>Qui peut accéder aux données ?

Les utilisateurs disposant des autorisations suivantes peuvent consulter les journaux d’audit :

- Administrateur général
- Administrateur du service Intune
- Les administrateurs ayant un rôle Intune avec les autorisations **Données d’audit** - **Lecture**

## <a name="audit-logs-for-intune-workloads"></a>Journaux d’audit pour les charges de travail Intune

Vous pouvez consulter les journaux d’audit dans le groupe d’analyse pour chaque charge de travail Intune :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Choisissez la charge de travail pour laquelle vous souhaitez consulter les journaux d’audit. Par exemple, sélectionnez **Appareils**.
3. Sous **Surveillance**, choisissez **Journaux d’audit**.

## <a name="route-logs-to-azure-monitor"></a>Router des journaux vers Azure Monitor

Les journaux d’audit et les journaux des opérations peuvent également être routés vers Azure Monitor. Dans **Journaux d’audit**, sélectionnez **Exporter les paramètres de données** :

![Exporter les données de journal vers Azure Monitor en sélectionnant Exporter les paramètres de données dans Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

Pour plus d’informations sur cette fonctionnalité, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Consulter les journaux d'audit

![Choisir des journaux d’audit dans Intune pour voir les actions et les dates auxquelles sont survenus les événements](./media/monitor-audit-logs/monitor-audit-logs.png "Journaux d’audit")

Un journal d’audit propose par défaut une vue par liste qui affiche les éléments suivants :

- Date et heure de l’événement
- Initié par (acteur)
- Nom de l'application
- Activité
- Cible(s)
- Category
- État

Pour voir des informations détaillées sur un événement, sélectionnez un élément dans la liste :

![Obtenir des informations détaillées sur les actions effectuées et leurs auteurs dans les journaux d’audit Intune](./media/monitor-audit-logs/monitor-audit-log-detail.png "Informations détaillées des journaux d’audit")

> [!NOTE]
> **Initié par (utilisateur)** comprend des informations sur l’utilisateur qui a exécuté la tâche et l’emplacement de l’exécution. Par exemple, si vous exécutez l’activité dans Intune dans le portail Azure, **Application** répertorie toujours **Extension du portail Microsoft Intune** et **l’ID d’application** utilise toujours le même GUID.
> 
> La section **Cible(s)** répertorie plusieurs cibles et les propriétés qui ont été modifiées.  

## <a name="filter-audit-events"></a>Filtrer les événements d’audit

Chaque charge de travail comporte un élément de menu qui pré-filtre la catégorie d’événements d’audit associée à ce volet. Une option de filtre distincte vous permet de sélectionner d’autres catégories ainsi que les détails de l’action de l’événement pour cette catégorie. Vous pouvez rechercher par nom d’utilisateur principal (UPN), par exemple l’utilisateur qui a effectué l’action. Un filtre de plage de dates permet d’afficher les dernières 24 heures, les 7 derniers jours ou les 30 derniers jours. Par défaut, les événements d’audit des 30 derniers jours sont affichés.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utiliser l’API Graph pour récupérer des événements d’audit

Pour plus d’informations sur l’utilisation de l’API Graph pour récupérer jusqu’à 1 an d’événements d’audit, consultez [Répertorier les événements d’audit](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Étapes suivantes

[Envoyer les données de journal vers des comptes de stockage, des hubs d’événements ou Log Analytics](review-logs-using-azure-monitor.md).

[Consulter les journaux de la protection des applications clientes](../apps/app-protection-policy-settings-log.md).
