---
title: Surveiller les informations sur les applications et les affectations
titlesuffix: Microsoft Intune
description: Une fois que vous avez affecté une application à des utilisateurs ou à des appareils, utilisez ces informations pour surveiller son état.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0408ce3a4c2d4224780b4b23b0fb1b7d690471fe
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Surveiller les informations sur les applications et les affectations avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune propose plusieurs façons de surveiller les propriétés des applications que vous gérez et de gérer leur état d’affectation.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le menu **Intune**, sélectionnez **Applications mobiles**.
4. Dans la section **Gérer** du menu, sélectionnez **Applications**.
5. Dans la liste des applications, sélectionnez une application à surveiller. Le volet de l’application s’affiche, avec une vue d’ensemble de l’état de l’appareil et de l’état de l’utilisateur.

## <a name="app-overview-pane"></a>Volet de vue d’ensemble de l’application

Dans le volet de l’application, vous pouvez passer en revue des détails de l’état d’une application dans votre environnement.

### <a name="essentials"></a>Base
La section **Bases** contient les informations suivantes sur l’application :

 | **Détails de l’application**            | **Description**                                                      |
|------------------------|------------------------------------------------------------------|
| **Éditeur**          | Éditeur de l’application.                                            |
| **Système d'exploitation**   | Système d’exploitation de l’application (Windows, iOS, Android, etc.). |
| **Créé le**             | Date et heure de création de cette révision.                         |
| **Affecté**           | Si l’application a été affectée (**Oui** ou **Non**).                  |

### <a name="device-and-user-status-graphs"></a>Graphiques des états de l’appareil et de l’utilisateur
Les graphiques indiquent le nombre d’applications liées aux états suivants :

| **État de l’appareil**       | **Description**                                       |
|-----------------------|-------------------------------------------------------|
| **Installé**         | Nombre d’applications installées.                         |
| **Non installé**     | Nombre d’applications non installées.                     |
| **Échec**            | Nombre d’installations ayant échoué.                   |
| **Installation en attente**   | Nombre d’applications qui sont en cours d’installation. |
| **Non applicable**           | Nombre d’applications auxquelles l’état n’est pas applicable.            |

### <a name="device-install-status"></a>État de l’installation de l’appareil

Une listes des états de l’appareil s’affiche quand vous sélectionnez **État de l’installation de l’appareil** dans la section **Surveiller** du menu. Le tableau des détails inclut les colonnes suivantes :

| **Colonne de l’appareil**      | **Description**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nom de l’appareil**      | Nom de l’appareil sur les plateformes qui autorisent à nommer un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut n’est disponible pour aucun autre appareil.                                                                       |
| **Nom d’utilisateur**        | Nom de l’utilisateur.                                                                                                                                                                                                                                      |
| **Plateforme**         | Système d’exploitation de l’appareil (Windows, iOS, Android, etc.).                                                                                                                                                                                           |
| **Version**          | Numéro de version de l’application. Pour les applications métier, le numéro de version complet de l’application s’affiche. Le numéro de version complet identifie une version spécifique de l’application. Le numéro apparaît sous la forme _Version_(_Build_). Par exemple, 2.2(2.2.17560800). |
| **Statut**           | État de l’application.                                                                                                                                                                                                                                     |
| **Détails de l’état**   | Détails de l’état.                                                                                                                                                                                                                                     |
| **Dernier archivage**    | Date de la dernière synchronisation de l’appareil avec Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>État de l’installation de l’utilisateur

Une listes des états de l’utilisateur s’affiche quand vous sélectionnez **État de l’installation de l’utilisateur** dans la section **Surveiller** du menu. Le tableau des détails inclut les colonnes suivantes :

| **Colonne de l’utilisateur**     | **Description**                           |
|---------------------|-------------------------------------------|
| **Nom**            | Nom de l’utilisateur dans Azure Active Directory.         |
| **Nom d’utilisateur**       | Nom unique de l’utilisateur.              |
| **Installations**   | Nombre d’applications installées par l’utilisateur. |
| **Échecs**        | Nombre d’installations d’applications ayant échoué pour l’utilisateur.     |
| **Non installé**   | Nombre d’installations non installées par l’utilisateur. |


## <a name="next-steps"></a>Étapes suivantes

- Pour en savoir plus sur l’utilisation de vos données Intune, consultez [Utiliser l’entrepôt de données Intune](reports-nav-create-intune-reports.md).
- Pour en savoir plus sur les stratégies de configuration d’applications, consultez [Stratégies de configuration d’applications pour Intune](app-configuration-policies-overview.md).
