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
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991978"
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

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **administration du locataire** > **journaux d’audit**.
3. Pour filtrer les résultats, sélectionnez **Filtrer** et affiner les résultats à l’aide des options suivantes.
    - **Catégorie**: par exemple, **la conformité**, l' **appareil**et le **rôle**.
    - **Activité**: les options répertoriées ici sont limitées par l’option choisie sous **catégorie**.
    - **Plage de dates**: vous pouvez choisir des journaux pour le mois, la semaine ou le jour précédent.
4. Choisissez **Appliquer**.
4. Sélectionnez un élément dans la liste pour afficher les détails de l’activité.

## <a name="route-logs-to-azure-monitor"></a>Router des journaux vers Azure Monitor

Les journaux d’audit et les journaux des opérations peuvent également être routés vers Azure Monitor. Dans **Journaux d’audit**, sélectionnez **Exporter les paramètres de données** :

![Exporter les données de journal vers Azure Monitor en sélectionnant Exporter les paramètres de données dans Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> Pour plus d’informations sur cette fonctionnalité et pour connaître les conditions préalables à l’utilisation, consultez [Envoyer des données de journal à Storage, Event hubs ou log Analytics](review-logs-using-azure-monitor.md).

> [!NOTE]
> **Initié par (utilisateur)** comprend des informations sur l’utilisateur qui a exécuté la tâche et l’emplacement de l’exécution. Par exemple, si vous exécutez l’activité dans Intune dans le portail Azure, **Application** répertorie toujours **Extension du portail Microsoft Intune** et **l’ID d’application** utilise toujours le même GUID.
>
> La section **Cible(s)** répertorie plusieurs cibles et les propriétés qui ont été modifiées.  

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utiliser l’API Graph pour récupérer des événements d’audit

Pour plus d’informations sur l’utilisation de l’API Graph pour récupérer jusqu’à 1 an d’événements d’audit, consultez [Répertorier les événements d’audit](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Étapes suivantes

[Envoyer les données de journal vers des comptes de stockage, des hubs d’événements ou Log Analytics](review-logs-using-azure-monitor.md).

[Consulter les journaux de la protection des applications clientes](../apps/app-protection-policy-settings-log.md).
