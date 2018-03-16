---
title: "Créer et déployer des stratégies de protection d’applications"
titleSuffix: Microsoft Intune
description: "Découvrez comment créer et affecter des stratégies de protection des applications Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c7ad60a27e32aaab49e77789364aecdc5ea7fc60
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Guide pratique de gestion et affectation des stratégies de protection des applications

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Découvrez comment créer des stratégies de protection des applications Microsoft Intune et les affecter à vos utilisateur. Cette rubrique décrit également comment modifier des stratégies existantes.

## <a name="before-you-begin"></a>Avant de commencer

Si vous cherchez des instructions dans le portail classique Intune, consultez [Comment créer des stratégies de protection des applications](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).

Les stratégies de protection d'application peuvent être appliquées à des applications qui s’exécutent sur des appareils gérés ou non par Intune. Pour une description plus détaillée du fonctionnement des stratégies de protection d’application et les scénarios pris en charge par les stratégies de protection d’application Intune, consultez [Nouveautés des stratégies de protection d’application Microsoft Intune](app-protection-policy.md).

Si vous recherchez une liste d’applications prises en charge par la gestion des applications mobiles, consultez [Liste d’applications de gestion des applications mobiles](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

##  <a name="create-an-app-protection-policy"></a>Créer une stratégie de protection des applications
1.  Dans la charge de travail **Applications mobiles**, sélectionnez **Stratégies de protection des applications** dans la section **Gérer**. Cette sélection ouvre les informations des **Stratégies de protection des applications**, où vous pouvez créer des stratégies et modifier les stratégies existantes.
2. Choisissez **Ajouter une stratégie**.

  ![Capture d’écran du panneau « Ajouter une stratégie »](./media/app-protection-add-policy.png)

3.  Tapez un nom pour la stratégie, ajoutez une brève description et sélectionnez le type de plateforme. Vous pouvez créer plusieurs stratégies pour chaque plateforme, selon vos besoins.

4.  Choisissez **Applications** pour ouvrir le panneau **Applications** qui contient la liste des applications disponibles. Dans cette liste, sélectionnez une ou plusieurs applications à associer à la stratégie que vous créez.
5. Une fois que vous avez sélectionné les applications, choisissez **Sélectionner** pour enregistrer votre sélection.

    > [!IMPORTANT]
    > Vous devez sélectionner au moins une application pour créer une stratégie.

6.  Choisissez **Configurer les paramètres nécessaires** dans le panneau **Ajouter une stratégie** pour ouvrir **Paramètres**.

    Il existe deux catégories de paramètres de stratégie : **Réadressage des données** et **Accès**.  Les stratégies de réadressage des données sont applicables au déplacement des données dans et en dehors des applications. Les stratégies d’accès déterminent la façon dont l’utilisateur final accède aux applications dans un contexte professionnel.
    Pour bien démarrer, les paramètres de stratégie sont définis par défaut. Si les valeurs par défaut répondent à vos besoins, vous n’avez pas besoin de les changer.

    > [!TIP]
    > Ces paramètres de stratégie sont appliqués uniquement quand vous utilisez des applications dans le contexte de travail. Quand l’utilisateur final utilise l’application pour effectuer une tâche personnelle, il n’est pas affecté par ces stratégies.

7.  Choisissez **OK** pour enregistrer cette configuration. Vous êtes maintenant de retour dans le volet **Ajouter une stratégie**. Choisissez **Créer** pour créer la stratégie et enregistrer vos paramètres.
8. Choisissez **OK** pour enregistrer cette configuration. Vous êtes maintenant de retour dans le panneau **Ajouter une stratégie**.
9. Choisissez **Créer** pour créer la stratégie et enregistrer vos paramètres.

Quand vous avez fini de créer une stratégie comme décrit dans la procédure précédente, elle n’est pas déployée sur les utilisateurs. Pour déployer une stratégie, consultez [Déployer une stratégie pour les utilisateurs](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Déployer une stratégie sur les utilisateurs


1. Dans le volet **Stratégies de protection des applications**, sélectionnez une stratégie.

1. Dans le volet **Stratégie**, choisissez **Affectations** pour ouvrir le volet **Protection des applications Intune - Affectations**. Choisissez **Sélectionner les groupes à inclure** dans le volet **Affectations** pour ouvrir le volet **Sélectionner les groupes à inclure**.

   ![Capture d’écran du volet Affectations avec l’option de menu Sélectionner les groupes à inclure en surbrillance](./media/app-protection-policy-add-users.png)

2.  La liste de groupes d’utilisateurs s’affiche sur le volet **Ajouter un groupe d’utilisateurs**. Il s’agit de la liste de tous les groupes de sécurité figurant dans votre **Azure Active Directory**. Sélectionnez les groupes d’utilisateurs auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Sélectionner**. Si vous choisissez **Sélectionner**, la stratégie est déployée pour les utilisateurs.

    ![Capture d’écran du volet Ajouter un groupe d’utilisateurs montrant la liste des utilisateurs Azure Active Directory](./media/azure-ad-user-group-list.png)

Vous avez créé une stratégie et l’avez déployée pour les utilisateurs.

Seuls les utilisateurs avec des licences Microsoft Intune sont affectés par la stratégie. Les utilisateurs du groupe de sécurité sélectionné qui n’ont pas de licence Intune ne sont pas affectés.

>[!IMPORTANT]
> Si vous utilisez Intune avec Configuration Manager pour gérer vos appareils, la stratégie est appliquée uniquement aux utilisateurs du groupe que vous avez sélectionné. Les membres des groupes enfants imbriqués dans le groupe que vous avez sélectionné ne sont pas affectés.

Les utilisateurs finaux peuvent télécharger les applications à partir de l’App Store ou de Google Play. Pour plus d'informations, voir :
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](app-protection-enabled-apps-android.md)
* [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](app-protection-enabled-apps-ios.md)

##  <a name="change-existing-policies"></a>Modifier des stratégies existantes
Vous pouvez modifier une stratégie existante et l’appliquer aux utilisateurs ciblés. Toutefois, quand vous modifiez des stratégies existantes, les utilisateurs déjà connectés aux applications ne voient pas les changements pendant 8 heures.

Pour voir immédiatement l’effet des changements, l’utilisateur final doit se déconnecter de l’application et se reconnecter.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Pour modifier la liste des applications associées à la stratégie

1.  Dans le volet **Stratégies de protection des applications**, choisissez la stratégie à modifier pour ouvrir le volet spécifique de cette stratégie.

2.  Dans le volet de la stratégie, choisissez **Applications ciblées** pour ouvrir la liste des applications.

3.  Supprimez ou ajoutez des applications dans la liste et choisissez l’icône **Enregistrer** pour enregistrer les modifications.

### <a name="to-change-the-list-of-user-groups"></a>Pour modifier la liste des groupes d’utilisateurs


1.  Dans le volet **Stratégies de protection des applications**, choisissez la stratégie à modifier pour ouvrir le volet spécifique de cette stratégie.

2.  Dans le volet de la stratégie, choisissez **Affectations** pour ouvrir le volet **Protection des applications Intune - Affectations** qui affiche la liste des groupes d’utilisateurs actuels qui ont cette stratégie.

3.  Pour ajouter un nouveau groupe d’utilisateurs à la stratégie, sous l’onglet **Inclure**, choisissez **Sélectionner les groupes à inclure**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour déployer la stratégie pour le groupe que vous avez sélectionné.

4.  Pour supprimer un groupe d’utilisateurs, sous l’onglet **Exclure**, choisissez **Sélectionner les groupes à exclure**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour supprimer le groupe d’utilisateurs.

### <a name="to-change-policy-settings"></a>Pour modifier les paramètres d’une stratégie

1.  Dans le volet **Stratégies de protection des applications**, choisissez la stratégie à modifier pour ouvrir le volet spécifique de cette stratégie.

2.  Choisissez **Paramètres de stratégie** pour ouvrir le volet **Paramètres de stratégie**.

3.  Modifiez les paramètres, puis choisissez l’icône **Enregistrer** pour enregistrer les modifications.

## <a name="policy-settings"></a>Paramètres de stratégie
Pour afficher la liste complète des paramètres de stratégie pour iOS et Android, sélectionnez l’un des liens suivants :

- [Stratégies iOS](app-protection-policy-settings-ios.md)
- [Stratégies Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Étapes suivantes
[Surveiller l’état de la conformité et des utilisateurs](app-protection-policies-monitor.md)

### <a name="see-also"></a>Voir aussi
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](app-protection-enabled-apps-android.md)
* [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](app-protection-enabled-apps-ios.md)
