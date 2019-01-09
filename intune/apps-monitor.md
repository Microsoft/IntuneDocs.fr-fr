---
title: Surveiller les informations sur les applications et les affectations
titlesuffix: Microsoft Intune
description: Une fois que vous avez affecté une application à des utilisateurs ou à des appareils, utilisez ces informations pour surveiller son état.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bff4e2b3afe684fe12243fa0f410728eb16eeaba
ms.sourcegitcommit: 874d9a00cc4666920069d54f99c6c2e687fa34a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53325175"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Surveiller les informations sur les applications et les affectations avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune propose plusieurs façons de surveiller les propriétés des applications que vous gérez et de gérer leur état d’affectation.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le menu **Intune**, sélectionnez **Applications clientes**.
4. Dans la section **Gérer** du menu, sélectionnez **Applications**.
5. Dans la liste des applications, sélectionnez une application à surveiller. Le volet de l’application s’affiche alors, avec une vue d’ensemble de l’état de l’appareil et de l’état de l’utilisateur.

> [!NOTE]
> Les applications du Android Store qui sont déployées comme étant **disponibles** et les applications métier Android déployées comme étant **disponibles avec ou sans inscription** ne signalent pas leur état d’installation.

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

> [!NOTE]
> Il peut arriver que le nombre d’applications découvertes ne corresponde pas au nombre d’états d’installation d’applications. Voici quelques sources d’incohérences :
>    - Une modification de ciblage d’une application managée installée peut faire baisser le nombre d’installations dans le panneau d’état, tandis que l’application reste comptée parmi les applications détectées.
>    - Si plusieurs instances de la même application sont ciblées dans un locataire, le chevauchement potentiel d’utilisateurs ou d’appareils entraîne des disparités dans les volumes. Chaque instance de l’application compte les utilisateurs qui se chevauchent, mais les applications découvertes sont comptées plusieurs fois.
>    - Les applications découvertes et leur état sont collectés à différents intervalles de temps, ce qui peut causer des écarts dans le nombre d’applications.
> 
> De plus, n’oubliez pas que les applications Android déployées comme **Disponible avec ou sans inscription** signalent leur état d’installation seulement pour les appareils inscrits. L’état d’installation des applications n’est pas disponible pour les appareils qui ne sont pas inscrits dans Intune.

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
