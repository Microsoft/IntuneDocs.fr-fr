---
title: Guide pratique de surveillance des stratégies de protection des applications
titleSuffix: Microsoft Intune
description: Cette rubrique décrit comment surveiller l’état de conformité des stratégies de gestion des applications mobiles dans Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d8c34f1947a0abaa4cdf0bbcd65dcf31e4c11ff
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59566787"
---
# <a name="how-to-monitor-app-protection-policies"></a>Guide pratique de surveillance des stratégies de protection des applications
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez surveiller l’état de conformité des stratégies de gestion des applications mobiles (GAM) que vous avez appliquées aux utilisateurs depuis le volet de protection des applications Intune dans le [portail Azure](https://portal.azure.com). Vous pouvez également y trouver des informations sur les utilisateurs concernés par les stratégies GAM, l’état de conformité de la stratégie GAM et tous les problèmes que vos utilisateurs pourraient rencontrer.

Vous pouvez surveiller l’état de conformité des stratégies GAM à trois endroits différents :
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

- **Utilisateurs attribués** : indique le nombre total d’utilisateurs attribués dans votre société, qui se servent d’une application associée à une stratégie dans un contexte de travail et qui sont dotés d’une protection ainsi que d’une licence. Représente également le nombre d’utilisateurs attribués sans protection et sans licence.
- **Utilisateurs marqués d’un indicateur** : nombre d’utilisateurs ayant rencontré des problèmes. Les appareils jailbreakés (iOS) et rootés (Android) sont signalés sous **Utilisateurs marqués d’un indicateur**. Les utilisateurs d’appareils qui sont marqués d’un indicateur par la vérification de l’attestation d’appareil Google SafetyNet (si activée par l’administrateur informatique) sont présentés ici. 
- **Statut de l’utilisateur pour iOS** et **Statut de l’utilisateur pour Android** : nombre d’utilisateurs qui ont utilisé une application, et auxquels une stratégie a été affectée dans un contexte professionnel pour la plateforme associée. Ces informations indiquent le nombre d’utilisateurs gérés par la stratégie ainsi que le nombre d’utilisateurs qui se servent d’une application non ciblée par une stratégie dans un contexte professionnel. Vous pouvez envisager d’ajouter ces utilisateurs à la stratégie.
- **Top des applications iOS protégées** : En fonction des applications iOS les plus utilisées, cette information indique le nombre d’applications iOS protégées et non protégées.
- **Top des applications Android protégées** : En fonction des applications Android les plus utilisées, cette information indique le nombre d’applications Android protégées et non protégées.
- **Principales applications iOS configurées sans inscription** : En fonction des applications iOS les plus utilisées pour les appareils non inscrits, cette information indique le nombre d’applications iOS configurées.
- **Principales applications Android configurées sans inscription** : En fonction des applications Android les plus utilisées pour les appareils non inscrits, cette information indique le nombre d’applications Android configurées.

    > [!NOTE]
    > Si vous avez plusieurs stratégies par plateforme, un utilisateur est considéré comme étant géré par une stratégie lorsqu’au moins une stratégie lui a été attribuée.

## <a name="detailed-view"></a>Vue détaillée
Vous pouvez accéder à la vue détaillée du résumé en choisissant les vignettes **État de l’utilisateur** (selon la plateforme de système d’exploitation de l’appareil) et **Utilisateurs marqués d’un indicateur**.

### <a name="user-status"></a>État de l’utilisateur
Vous pouvez rechercher un utilisateur et vérifier son état de conformité. Le volet **Rapport d’application** montre les informations suivantes sur un utilisateur sélectionné :
- **Icône** : Indique si l’état de l’application est à jour.
- **Nom de l’application** : Nom de l’application.
- **Nom de l’appareil** : Appareils associés au compte d’utilisateur.
- **Type d’appareil** : Type d’appareil ou de système d’exploitation exécuté par l’appareil.
- **Stratégies** : Stratégies associées à l’application.
- **État** :
  - **Activé** : la stratégie a été déployée pour l’utilisateur, et l’application a été utilisée au moins une fois dans le contexte professionnel.
  - **Non activé** : la stratégie a été déployée pour l’utilisateur, mais l’application n’a depuis jamais été utilisée dans le contexte professionnel.
- **Dernière synchronisation** : Dernière synchronisation de l’appareil.

>[!NOTE]
> Si la stratégie MAM n’est pas déployée pour l’utilisateur que vous recherchez, un message vous informe que l’utilisateur n’est ciblé par aucune stratégie MAM.

Pour afficher le rapport d’un utilisateur, procédez comme suit :

1.  Pour sélectionner un utilisateur, choisissez la vignette récapitulative **État de l’utilisateur**.

    ![Capture d’écran de la vignette Résumé dans Gestion des applications mobiles Intune](./media/MAM-reporting-6.png)

2. Dans le volet **Rapport d’application**, choisissez **Sélectionner un utilisateur** pour rechercher un utilisateur Azure Active Directory.

    ![Capture d’écran de l’option Sélectionner un utilisateur dans le volet Rapport d’application](./media/MAM-reporting-2.png)

3. Sélectionnez l’utilisateur dans la liste. Vous pouvez voir les détails de l’état de conformité pour cet utilisateur.

### <a name="flagged-users"></a>Utilisateurs marqués d’un indicateur
La vue détaillée montre le message d’erreur, l’application à laquelle l’utilisateur a accédé quand l’erreur s’est produite, la plateforme de système d’exploitation de l’appareil concernée et un horodatage. Les utilisateurs d’appareils qui sont marqués d’un indicateur par la vérification de l’attestation d’appareil Google SafetyNet sont présentés ici avec la raison telle que signalée par Google.

## <a name="reporting-view"></a>Vue Rapports

Vous trouverez les mêmes rapports en haut du panneau **État de protection de l’application**.

> [!NOTE]
> Intune fournit des champs de rapport supplémentaires sur les appareils, notamment l’ID d’inscription d’application, le fabricant Android, le modèle et la version du correctif de sécurité ainsi que le modèle iOS. Dans Intune, ces champs sont disponibles quand vous sélectionnez **Applications clientes** > **État de protection de l’application**, et que vous choisissez **Rapport de protection d’application : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 

Des rapports supplémentaires sont disponibles pour vous aider à d’obtenir l’état de conformité de la stratégie MAM. Pour voir ces rapports, sélectionnez **Applications clientes** > **État de protection de l’application** > **Rapports**. 

Le panneau **Rapports** fournit plusieurs rapports basés sur l’utilisateur et l’application, notamment :


- **Rapport utilisateur** : Ce rapport présente les mêmes informations que celles qui figurent dans le rapport **État de l’utilisateur** sous la section [Vue détaillée](app-protection-policies-monitor.md#detailed-view) ci-dessus.

- **Rapport de l’application** : En plus de la sélection de la plateforme et de l’application, ce rapport fournit deux états distincts de protection de l’application que vous pouvez sélectionner avant de générer le rapport. Les états peuvent être **protégé** ou **non protégé**.

    -   État de l’utilisateur pour l’activité GAM gérée (**protégé**) : ce rapport présente l’activité de chaque application GAM gérée, par utilisateur. Il affiche toutes les applications ciblées par les stratégies GAM de chaque utilisateur et détaille l’état de chaque application enregistrée dans les stratégies GAM ou ciblée par une stratégie GAM mais jamais enregistrée.
    -   État de l’utilisateur pour l’activité GAM non gérée (**non protégé**) : ce rapport présente l’activité des applications compatibles avec GAM qui ne sont actuellement pas gérées, par utilisateur. Cela peut se produire pour les raisons suivantes :
        -   Ces applications sont utilisées par un utilisateur ou une application qui n’est actuellement pas ciblée par une stratégie GAM.
        -   Toutes les applications sont enregistrées, mais ne reçoivent aucune stratégie GAM.

        ![Capture d’écran du panneau Rapport d’application d’un utilisateur, affichant les détails de trois applications](./media/MAM-reporting-4.png)

- **Rapport de configuration des utilisateurs** : En fonction de l’utilisateur sélectionné, ce rapport fournit des détails sur les configurations d’application que l’utilisateur a reçues.
- **Rapport de configuration de l’application** : En fonction de la plateforme et de l’application sélectionnées, ce rapport fournit des détails sur les utilisateurs qui ont reçu des configurations pour l’application sélectionnée.
- **Rapport d’apprentissage d’application pour la Protection des informations Windows** : Ce rapport indique les applications qui tentent de franchir des limites de stratégie.
- **Apprentissage de site web pour la Protection des informations Windows** : Ce rapport indique les sites web qui tentent de franchir des limites de stratégie.

## <a name="table-grouping"></a>Regroupement de tables

Une fois que les données du **rapport d’utilisateur de la protection des applications** sont affichées, vous pouvez les regrouper selon les éléments suivants :

- **Résultat de la validation :** les données affichées sont regroupées en fonction de l’état de protection de l’application (échec, avertissement ou succès).
- **Nom de l’application :** les données affichées sont regroupées par application (nom réel de l’application) avec l’état (échec, avertissement ou succès).

## <a name="export-app-protection-activities-to-csv"></a>Exportation des activités de protection d’application au format CSV

Vous pouvez exporter toutes vos activités de stratégie de protection des applications vers un fichier *.csv*. Cela peut être utile pour analyser tous les états de protection des applications signalés par les utilisateurs.

Suivez ces étapes pour générer le rapport de protection des applications :

1. Dans le volet Gestion des applications mobiles Intune, choisissez **Rapport de protection des applications**.

    ![Capture d’écran du lien de téléchargement de la protection d’application](./media/app-protection-report-csv-2.png)

2. Choisissez **Oui** pour enregistrer votre rapport, puis cliquez sur **Enregistrer sous** et sélectionnez le dossier dans lequel vous souhaitez enregistrer le rapport.

    ![Capture d’écran de la boîte de confirmation Enregistrer le rapport](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Voir aussi
- [Gérer les transferts de données entre applications iOS](data-transfer-between-apps-manage-ios.md)
- [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](app-protection-enabled-apps-android.md)
- [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](app-protection-enabled-apps-ios.md)
