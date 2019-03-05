---
title: Journaux d’audit pour les activités Microsoft Intune
description: Découvrez comment consulter les journaux d’audit qui consignent les activités Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f44d25f75ccc68912bea7b108ca56afe6aecb528
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57239048"
---
# <a name="audit-logs-for-intune-activities"></a>Journaux d’audit pour les activités Intune
Les journaux d’audit vous indiquent les activités qui génèrent un changement dans Microsoft Intune. Les actions Créer, Mettre à jour (modifier), Supprimer et Affecter, ou les tâches à distance, génèrent des événements d’audit que vous pouvez consulter. Vous pouvez consulter les journaux d’audit pour la plupart des charges de travail Intune. L’audit est activé par défaut pour tous les clients et il ne peut pas être désactivé. L’enregistrement des événements d’audit a commencé avec la version de fonctionnalités de décembre 2017 ; les événements antérieurs ne sont pas disponibles.

## <a name="who-can-access-the-data"></a>Qui peut accéder aux données ?
Les utilisateurs disposant des autorisations suivantes peuvent consulter les journaux d’audit :
- Administrateur général
- Administrateur du service Intune
- Les administrateurs ayant un rôle Intune avec les autorisations **Données d’audit** - **Lecture**

## <a name="audit-logs-for-intune-workloads"></a>Journaux d’audit pour les charges de travail Intune
Vous pouvez consulter les journaux d’audit dans le groupe d’analyse pour chaque charge de travail Intune.  
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez la charge de travail pour laquelle vous souhaitez consulter les journaux d’audit, par exemple, **Appareils**.
4. Dans le groupe **d’analyse** de la charge de travail, choisissez **Journaux d’audit**.

## <a name="review-audit-events"></a>Consulter les journaux d'audit
![Journaux d’audit](./media/monitor-audit-logs.png "Journaux d’audit")

Un journal d’audit propose par défaut une vue par liste qui affiche les éléments suivants :    

- Date et heure de l’événement
- Initié par (acteur)
- Nom de l'application
- Activité
- Cible(s)
- Category
- État

En cliquant sur un élément de la liste, vous obtenez toutes les informations disponibles à ce sujet.

![Journaux d’audit](./media/monitor-audit-log-detail.png "Journaux d’audit")

> [!Note]    
> La section **Initié par (acteur)** dans les détails du journal d’audit fournit des informations sur les personnes qui ont effectué l’activité et le lieu où cette activité a été effectuée. Par exemple, si vous effectuez l’activité dans Intune dans le portail Azure, **Application** répertorie toujours **Extension du portail Microsoft Intune** et **l’ID d’application** utilise toujours le même GUID. 
>    
> La section **Cible(s)** peut répertorier plusieurs cibles et les propriétés qui ont été modifiées.  


## <a name="filter-audit-events"></a>Filtrer les événements d’audit
Chaque charge de travail comporte un élément de menu qui pré-filtre la catégorie d’événements d’audit associée à ce volet. Une option de filtre distincte vous permet de sélectionner d’autres catégories ainsi que les détails de l’action de l’événement pour cette catégorie. Vous pouvez rechercher par nom d’utilisateur principal (UPN), par exemple l’utilisateur qui a effectué l’action. Un filtre de plage de dates permet d’afficher les dernières 24 heures, les 7 derniers jours ou les 30 derniers jours. Par défaut, les événements d’audit des 30 derniers jours sont affichés.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Utiliser l’API Graph pour récupérer des événements d’audit
Pour plus d’informations sur l’utilisation de l’API Graph pour récupérer jusqu'à un an d’événements d’audit, consultez [Répertorier les événements d’audit](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list).
