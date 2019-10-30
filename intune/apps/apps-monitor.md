---
title: Surveiller les informations sur les applications et les affectations
titleSuffix: Microsoft Intune
description: Une fois que vous avez affecté une application à des utilisateurs ou à des appareils, utilisez ces informations pour surveiller son état.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee22ee435830137a423423aa692376aabbb6cecb
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585415"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Surveiller les informations sur les applications et les affectations avec Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune propose plusieurs façons de surveiller les propriétés des applications que vous gérez et de gérer leur état d’affectation.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans la section **Gérer** du menu, sélectionnez **Applications**.
5. Dans la liste des applications, sélectionnez une application à surveiller. Le volet de l’application s’affiche alors, avec une vue d’ensemble de l’état de l’appareil et de l’état de l’utilisateur.

> [!NOTE]
> Les applications de l’Android Store qui sont déployées comme étant **disponibles** ne signalent pas leur état d’installation.
>
> Pour les applications Google Play gérées qui sont déployées sur des appareils avec profil professionnel Android Entreprise, vous pouvez afficher l’état et le numéro de version de l’application installée sur un appareil à l’aide d’Intune. 

## <a name="app-overview-pane"></a>Volet de vue d’ensemble de l’application

Dans le volet de l’application, vous pouvez passer en revue des détails de l’état d’une application dans votre environnement.

### <a name="essentials"></a>Essentials
La section **Bases** contient les informations suivantes sur l’application :

 | **Détails de l’application**            | **Description**                                                      |
|------------------------|------------------------------------------------------------------|
| **Éditeur**          | Éditeur de l’application.                                            |
| **Système d'exploitation**   | Système d’exploitation de l’application (Windows, iOS, Android, etc.). |
| **Créé le**             | Date et heure de création de cette révision. <b>**Remarque** : Cette valeur de date est mise à jour lorsqu’un administrateur informatique modifie les métadonnées de l’application, en modifiant la catégorie d’application ou la description de l’application par exemple.                        |
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
> N’oubliez pas que les applications métier Android (.APK) déployées comme **Disponible avec ou sans inscription** signalent leur état d’installation seulement pour les appareils inscrits. L’état d’installation des applications n’est pas disponible pour les appareils qui ne sont pas inscrits dans Intune.

### <a name="device-install-status"></a>État de l’installation de l’appareil

Une listes des états de l’appareil s’affiche quand vous sélectionnez **État de l’installation de l’appareil** dans la section **Surveiller** du menu. Le tableau des détails inclut les colonnes suivantes :

| **Colonne de l’appareil**      | **Description**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nom de l’appareil**      | Nom de l’appareil sur les plateformes qui autorisent à nommer un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut n’est disponible pour aucun autre appareil.                                                                       |
| **Nom d’utilisateur**        | Nom de l'utilisateur.                                                                                                                                                                                                                                      |
| **Plateforme**         | Système d’exploitation de l’appareil (Windows, iOS, Android, etc.).                                                                                                                                                                                           |
| **Version**          | Numéro de version de l’application. Pour les applications métier (LOB) et les applications Microsoft Store pour Entreprises, le numéro de version complet de l’application s’affiche. Le numéro de version complet identifie une version spécifique de l’application. Le numéro apparaît sous la forme _Version_(_Build_). Par exemple, 2.2(2.2.17560800). Pour les applications de Store standard, aucune version n’est affichée. |
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

- Pour en savoir plus sur l’utilisation de vos données Intune, consultez [Utiliser l’entrepôt de données Intune](../reports-nav-create-intune-reports.md).
- Pour en savoir plus sur les stratégies de configuration d’applications, consultez [Stratégies de configuration d’applications pour Intune](app-configuration-policies-overview.md).
