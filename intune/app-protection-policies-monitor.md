---
title: Guide pratique de surveillance des stratégies de protection des applications
titleSuffix: Microsoft Intune
description: Surveillez l’état de conformité des stratégies de gestion des applications mobiles dans Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7efa888344b91c74672563730bbdea6c7424214b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835093"
---
# <a name="how-to-monitor-app-protection-policies"></a>Guide pratique de surveillance des stratégies de protection des applications
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Surveillez l’état de conformité des stratégies de gestion des applications mobiles (MAM) que vous avez appliquées aux utilisateurs dans le volet de protection des applications Intune du [portail Azure](https://portal.azure.com). Recherchez des informations sur les utilisateurs affectés par les stratégies MAM, l’état de conformité et tous les problèmes que vos utilisateurs pourraient rencontrer.

Vous pouvez surveiller l’état de conformité à trois endroits différents :

-   Vue Résumé

-   Vue détaillée

-   Vue Rapports

> [!NOTE]
> Pour plus d’informations sur la création de stratégies de protection des applications, consultez [Guide pratique pour créer et affecter des stratégies de protection des applications](app-protection-policies.md).

## <a name="summary-view"></a>Vue Résumé

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Applications clientes**.
4. Dans la charge de travail **Applications clientes**, choisissez **État de la protection des applications** dans la section **Surveiller** pour afficher la vue récapitulative :

![Vignette Résumé sur le volet Gestion des applications mobiles Intune](./media/app-protection-user-status-summary.png)

-   **Utilisateurs attribués** : indique le nombre total d’utilisateurs attribués dans votre société, qui se servent d’une application associée à une stratégie dans un contexte de travail et qui sont dotés d’une protection ainsi que d’une licence. Représente également le nombre d’utilisateurs attribués sans protection et sans licence.
-   **Utilisateurs marqués d’un indicateur** : nombre d’utilisateurs ayant rencontré des problèmes. Les appareils jailbreakés sont signalés sous **Utilisateurs avec indicateur**.
-   **Statut de l’utilisateur pour iOS** et **Statut de l’utilisateur pour Android** : nombre d’utilisateurs qui ont utilisé une application, et auxquels une stratégie a été affectée dans un contexte professionnel pour la plateforme associée. Ces informations indiquent le nombre d’utilisateurs gérés par la stratégie ainsi que le nombre d’utilisateurs qui se servent d’une application non ciblée par une stratégie dans un contexte professionnel. Vous pouvez envisager d’ajouter ces utilisateurs à la stratégie.

    > [!NOTE]
    > Si vous avez plusieurs stratégies par plateforme, un utilisateur est considéré comme étant géré par une stratégie quand au moins une stratégie lui a été affectée.

## <a name="detailed-view"></a>Vue détaillée
Vous pouvez accéder à la vue détaillée du résumé en choisissant les vignettes **État de l’utilisateur** (selon la plateforme de système d’exploitation de l’appareil) et **Utilisateurs marqués d’un indicateur**.

### <a name="user-status"></a>État de l’utilisateur
Vous pouvez rechercher un utilisateur et vérifier son état de conformité. Le volet **Rapport d’application** montre les informations suivantes sur un utilisateur sélectionné :
- Les appareils associés au compte d’utilisateur

- Applications avec une stratégie GAM sur l’appareil

- État :

  - **Activé** : la stratégie a été déployée pour l’utilisateur, et l’application a été utilisée au moins une fois dans le contexte professionnel.

  - **Non activé** : la stratégie a été déployée pour l’utilisateur, mais l’application n’a depuis jamais été utilisée dans le contexte professionnel.

>[!NOTE]
> Si la stratégie MAM n’est pas déployée pour l’utilisateur que vous recherchez, un message vous informe que l’utilisateur n’est ciblé par aucune stratégie MAM.

Pour afficher le rapport d’un utilisateur, procédez comme suit :

1.  Pour sélectionner un utilisateur, choisissez la vignette récapitulative **État de l’utilisateur**.

    ![Capture d’écran de la vignette Résumé dans Gestion des applications mobiles Intune](./media/MAM-reporting-6.png)

2. Dans le volet **Rapport d’application**, choisissez **Sélectionner un utilisateur** pour rechercher un utilisateur Azure Active Directory.

    ![Capture d’écran de l’option Sélectionner un utilisateur dans le volet Rapport d’application](./media/MAM-reporting-2.png)

3. Sélectionnez l’utilisateur dans la liste. Vous pouvez voir les détails de l’état de conformité pour cet utilisateur.

### <a name="flagged-users"></a>Utilisateurs marqués d’un indicateur
La vue détaillée montre le message d’erreur, l’application à laquelle l’utilisateur a accédé quand l’erreur s’est produite, la plateforme de système d’exploitation de l’appareil concernée et un horodatage.

## <a name="reporting-view"></a>Vue Rapports

Vous trouverez les mêmes rapports dans le panneau **État de protection de l’application**.

> [!NOTE]
> Intune fournit des champs de rapport supplémentaires sur les appareils, notamment l’ID d’inscription d’application, le fabricant Android, le modèle et la version du correctif de sécurité ainsi que le modèle iOS. Dans Intune, ces champs sont disponibles quand vous sélectionnez **Applications clientes** > **État de protection de l’application**, et que vous choisissez **Rapport de protection d’application : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 

Des rapports supplémentaires sont disponibles pour vous aider à d’obtenir l’état de conformité de la stratégie MAM. Pour voir ces rapports, sélectionnez **Applications clientes** > **État de protection de l’application** > **Rapports**. 

Le panneau **Rapports** fournit plusieurs rapports basés sur l’utilisateur et l’application, notamment :


-   **Rapport utilisateur** : il présente les mêmes informations que celles qui figurent dans le rapport **État de l’utilisateur** sous la section Vue détaillée ci-dessus.

-   **Rapport de l’application** : il fournit deux états distincts de protection de l’application, que les administrateurs peuvent sélectionner avant de générer le rapport. Les états peuvent être protégés ou non protégés.

    -   État de l’utilisateur pour l’activité GAM gérée (protégé) : ce rapport présente l’activité de chaque application GAM gérée, par utilisateur.

        -   Il affiche toutes les applications ciblées par les stratégies GAM de chaque utilisateur et détaille l’état de chaque application enregistrée dans les stratégies GAM ou ciblée par une stratégie GAM mais jamais enregistrée.
<br><br>
    -   État de l’utilisateur pour l’activité GAM non gérée (non protégé) : ce rapport présente l’activité des applications compatibles avec GAM qui ne sont actuellement pas gérées, par utilisateur. Cela peut se produire pour les raisons suivantes :

        -   Ces applications sont utilisées par un utilisateur ou une application qui n’est actuellement pas ciblée par une stratégie GAM.

        -   Toutes les applications sont enregistrées, mais ne reçoivent aucune stratégie GAM.

![Capture d’écran du panneau Rapport d’application d’un utilisateur, affichant les détails de trois applications](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Regroupement de tables

Une fois que les données du **rapport d’utilisateur de la protection des applications** s’affichent, vous pouvez les regrouper selon les éléments suivants :

- **Résultat de la validation :** les données affichées sont regroupées en fonction de l’état de protection de l’application (échec, avertissement ou succès).
- **Nom de l’application :** les données affichées sont regroupées par application (nom réel de l’application) avec l’état (échec, avertissement ou succès).

## <a name="export-app-protection-activities-to-csv"></a>Exportation des activités de protection d’application au format CSV

Vous pouvez exporter toutes vos activités de stratégie de protection des applications vers un fichier .csv. Cela peut être utile pour analyser tous les états de protection des applications signalés par les utilisateurs.

Suivez ces étapes pour générer le rapport de protection des applications :

1. Dans le volet Gestion des applications mobiles Intune, choisissez **Rapport de protection des applications**.

    ![Capture d’écran du lien de téléchargement de la protection d’application](./media/app-protection-report-csv-2.png)

2. Choisissez Oui pour enregistrer votre rapport, puis cliquez sur Enregistrer sous et sélectionnez le dossier dans lequel vous souhaitez enregistrer le rapport.

    ![Capture d’écran de la boîte de confirmation Enregistrer le rapport](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Voir aussi
[Gérer les transferts de données entre applications iOS](data-transfer-between-apps-manage-ios.md)

* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](app-protection-enabled-apps-android.md)
* [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](app-protection-enabled-apps-ios.md)
