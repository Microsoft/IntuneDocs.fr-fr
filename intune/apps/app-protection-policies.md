---
title: Créer et déployer des stratégies de protection d’applications
titleSuffix: Microsoft Intune
description: Cette partie explique comment créer et attribuer des stratégies de protection des applications Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4958a35f3a83fecffacf26421e4c1d797f45ddaa
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940392"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Guide pratique de gestion et affectation des stratégies de protection des applications

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Découvrez comment créer des stratégies de protection des applications Microsoft Intune et les affecter à vos utilisateur. Cette rubrique décrit également comment modifier des stratégies existantes.

## <a name="before-you-begin"></a>Avant de commencer

Vous pouvez appliquer les stratégies de protection des applications aux applications qui s’exécutent sur des appareils gérés ou non par Intune. Pour une description plus détaillée du fonctionnement des stratégies de protection des applications et des scénarios pris en charge par les stratégies Intune App Protection, consultez [Présentation des stratégies Microsoft Intune App Protection](app-protection-policy.md).

Si vous recherchez une liste d’applications prises en charge par la gestion des applications mobiles, consultez [Liste d’applications de gestion des applications mobiles](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Pour plus d’informations sur l’ajout d’applications métier professionnelles à Microsoft Intune dans le but de préparer des stratégies de protection d’applications, voir [Ajouter des applications à Microsoft Intune](apps-add.md).

## <a name="create-an-app-protection-policy"></a>Créer une stratégie de protection des applications
1. Dans le portail Intune, accédez à **Applications clientes** > **Stratégies de protection des applications**. Cette sélection ouvre les informations des **Stratégies de protection des applications**, où vous pouvez créer des stratégies et modifier les stratégies existantes.
2. Sélectionnez **Créer une stratégie**.

   ![Capture d’écran du panneau « Ajouter une stratégie »](./media/app-protection-policies/app-protection-add-policy.png)

3. Spécifiez un nom pour la stratégie, ajoutez une brève description, puis sélectionnez le type de plateforme de votre stratégie. Vous pouvez créer plusieurs stratégies pour chaque plateforme.

4. Sélectionnez **Applications** pour ouvrir le panneau **Applications**, qui contient la liste des applications disponibles. Dans cette liste, sélectionnez une ou plusieurs applications à associer à la stratégie que vous créez. Sélectionnez au moins une application pour créer une stratégie.  

5. Une fois que vous avez sélectionné les applications, choisissez **Sélectionner** pour enregistrer votre sélection.

6. Dans le panneau **Ajouter une stratégie**, sélectionnez **Configurer les paramètres requis** pour ouvrir **Paramètres**.

   Il existe trois catégories pour les paramètres de stratégie :
   - **Protection des données** - Ce groupe comprend les contrôles de protection contre la perte de données (DLP), par exemple les restrictions d’opérations Couper, Copier, Coller et Enregistrer sous. Ces paramètres déterminent la manière dont les utilisateurs interagissent avec les données dans les applications.
   - **Conditions d’accès** - Ce groupe contient les options de code PIN par application, qui déterminent le mode d’accès de l’utilisateur final aux applications dans un contexte professionnel.  
   - **Lancement conditionnel** - Ce groupe contient des paramètres tels que les paramètres minimum du système d’exploitation, la détection d’appareils jailbreakés/rootés, ainsi que les périodes de grâce hors connexion.

   Pour bien démarrer, les paramètres de stratégie sont définis par défaut. Si les valeurs par défaut répondent à vos besoins, vous n’avez pas besoin de les changer.

   > [!TIP]
   > Ces paramètres de stratégie sont appliqués uniquement quand vous utilisez des applications dans le contexte de travail. Quand l’utilisateur final utilise l’application pour effectuer une tâche personnelle, il n’est pas affecté par ces stratégies. Notez que quand vous créez un fichier, ce dernier est considéré comme étant un fichier personnel. 

7. Sélectionnez **OK** pour enregistrer cette configuration. Vous êtes maintenant de retour dans le panneau **Ajouter une stratégie**.
8. Sélectionnez **Créer** pour créer la stratégie et enregistrer vos paramètres.

Les nouvelles stratégies que vous créez ne sont pas déployées sur les utilisateurs, tant que vous ne le faites pas explicitement. Pour déployer une stratégie, consultez [Déployer une stratégie pour les utilisateurs](app-protection-policies.md#deploy-a-policy-to-users).

## <a name="deploy-a-policy-to-users"></a>Déployer une stratégie sur les utilisateurs

1. Dans le volet **Stratégies de protection des applications**, sélectionnez une stratégie.

2. Dans le volet ***Protection d’application Intune**, sélectionnez **Affectations** pour ouvrir le volet **Protection d’application Intune - Affectations**. Sous l’onglet *Inclure*, sélectionnez **Sélectionner les groupes à inclure**. 

   ![Capture d’écran du volet Affectations avec le menu Sélectionner les groupes à inclure](./media/app-protection-policies/app-protection-policy-add-users.png)

3. Une liste de tous les groupes de sécurité de votre domaine **Azure Active Directory** s’affiche. Sélectionnez les groupes d’utilisateurs auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Sélectionner**. 

    ![Capture d’écran du volet Ajouter un groupe d’utilisateurs avec la liste des utilisateurs Azure AD](./media/app-protection-policies/azure-ad-user-group-list.png)

4. Une fois que vous incluez et excluez des groupes, sélectionnez **Enregistrer** pour enregistrer la configuration et déployer la stratégie aux utilisateurs. Si vous sélectionnez **Ignorer** avant d’enregistrer votre configuration, vous abandonnez toutes les modifications apportées aux onglets *Inclure* et *Exclure*.   
 
     ![Capture d’écran illustrant les options Enregistrer et Ignorer](./media/app-protection-policies/save-assignment.png)
  
Vous avez créé une stratégie et l’avez déployée pour les utilisateurs.

Seuls les utilisateurs avec des licences Microsoft Intune sont affectés par la stratégie. Les utilisateurs du groupe de sécurité sélectionné qui n’ont pas de licence Intune ne sont pas affectés.

>[!IMPORTANT]
> Si vous utilisez Intune avec Configuration Manager pour gérer vos appareils, la stratégie est appliquée uniquement aux utilisateurs du groupe que vous avez sélectionné. Les membres des groupes enfants imbriqués dans le groupe que vous avez sélectionné ne sont pas affectés.

Les utilisateurs finaux peuvent télécharger les applications à partir de l’App Store ou de Google Play. Pour plus d'informations, voir :
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-android.md)
* [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Modifier des stratégies existantes
Vous pouvez modifier une stratégie existante et l’appliquer aux utilisateurs ciblés. Toutefois, quand vous changez des stratégies existantes, les utilisateurs déjà connectés aux applications ne voient pas ces changements pendant une période de huit heures.

Pour voir immédiatement l’effet des changements, l’utilisateur final doit se déconnecter de l’application, puis se reconnecter.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Pour modifier la liste des applications associées à la stratégie

1. Dans le volet **Stratégies de protection des applications**, sélectionnez la stratégie à changer.

2. Dans le volet *Protection d’application Intune*, sélectionnez **Applications ciblées** pour ouvrir la liste des applications.

3. Supprimez ou ajoutez des applications dans la liste, puis sélectionnez l’icône **Enregistrer** pour enregistrer vos changements.

### <a name="to-change-the-list-of-user-groups"></a>Pour modifier la liste des groupes d’utilisateurs


1. Dans le volet **Stratégies de protection des applications**, sélectionnez la stratégie à changer.

2. Dans le volet *Protection d’application Intune*, sélectionnez **Affectations** pour ouvrir le volet **Protection d’application Intune - Affectations**, qui affiche la liste des groupes d’utilisateurs actuels ayant cette stratégie.

3. Pour ajouter un nouveau groupe d’utilisateurs à la stratégie, sous l’onglet *Inclure*, choisissez **Sélectionner les groupes à inclure**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour ajouter le groupe. 

4. Pour exclure un groupe d’utilisateurs, sous l’onglet *Exclure*, choisissez **Sélectionner les groupes à exclure**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour supprimer le groupe d’utilisateurs.  

5. Pour supprimer des groupes qui ont été ajoutés précédemment, dans l’onglet *Inclure* ou l’onglet *Exclure*, sélectionnez les points de suspension (...) et sélectionnez **Supprimer**. 

5. Une fois vos modifications aux affectations prêtes, sélectionnez **Enregistrer** pour enregistrer la configuration et déployer la stratégie vers le nouvel ensemble d’utilisateurs. Si vous sélectionnez **Ignorer** avant d’enregistrer votre configuration, vous abandonnez toutes les modifications apportées aux onglets *Inclure* et *Exclure*.

### <a name="to-change-policy-settings"></a>Pour modifier les paramètres d’une stratégie

1. Dans le volet **Stratégies de protection des applications**, choisissez la stratégie à changer.

2. Dans le volet *Protection d’application Intune*, sélectionnez **Propriétés** pour ouvrir la liste des zones de paramètres que vous pouvez modifier. 

3. Sélectionnez la zone de paramètres qui comporte les paramètres à changer, par exemple **Réadressage des données** ou **Conditions d’accès**. Affectez ensuite de nouvelles paramètres aux paramètres.

4. Sélectionnez l’icône **Enregistrer** pour enregistrer vos changements. Répétez le processus pour sélectionner une zone de paramètres, la modifier, puis enregistrer vos changements, jusqu’à ce que vous ayez effectué tous les changements nécessaires. Vous pouvez ensuite fermer le volet *Protection d’application Intune - Propriétés*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Cibler les stratégies de protection d’application en fonction de l’état de la gestion des appareils
Dans de nombreuses organisations, il est courant d’autoriser les utilisateurs finaux à se servir à la fois d’appareils gérés par Intune MDM (Mobile Device Management), par exemple les appareils d’entreprise, et d’appareils non gérés, protégés uniquement à l’aide des stratégies de protection des applications Intune. Les appareils non gérés sont souvent appelés appareils BYOD (Apportez votre propre appareil).

Dans la mesure où les stratégies de protection des applications Intune ciblent l’identité d’un utilisateur, les paramètres de protection d’un utilisateur peuvent s’appliquer à la fois aux appareils inscrits (gérés par MDM) et aux appareils non inscrits (non gérés par MDM). Ainsi, vous pouvez cibler une stratégie de protection des applications Intune sur des appareils iOS et Android inscrits ou non inscrits auprès d’Intune. Vous pouvez avoir une stratégie de protection pour les appareils non gérés dans laquelle des contrôles de protection contre la perte de données (DLP) stricts sont en place, et une stratégie de protection distincte pour les appareils gérés par MDM, où les contrôles DLP peuvent être un peu plus souples. Pour plus d'informations sur le fonctionnement de cette stratégie sur les appareils personnels Android Entreprise, voir [Ajouter des stratégies de protection et des profils professionnels](android-deployment-scenarios-app-protection-work-profiles.md).

Pour créer ces stratégies, accédez à **Applications clientes** > **Stratégies de protection des applications** dans la console Intune, puis sélectionnez **Créer une stratégie**. Vous pouvez également modifier une stratégie de protection d’application existante. Pour que la stratégie de protection des applications s’applique aux appareils gérés et non gérés, vérifiez que **Cibler sur tous les types d’application** a la valeur par défaut **Oui**. Si vous souhaitez effectuer une affectation précise en fonction de l’état de gestion, affectez à l’option **Cibler sur tous les types d’application** la valeur **Non**. 

![Capture d’écran du panneau Ajouter une stratégie avec l’option Cibler sur tous les types d’application](./media/app-protection-policies/app-protection-policies-target-all.png)

### <a name="app-types"></a>Types d’applications

- **Applications sur des appareils non gérés** : Les appareils non gérés sont des appareils pour lesquels la gestion MDM Intune n'a pas été détectée. Cela inclut les fournisseurs MDM tiers.
- **Applications sur des appareils gérés Intune** : Les appareils gérés sont gérés par Intune MDM.
- **Applications dans le profil professionnel Android** : Appareils gérés qui ont été inscrits comme appareils de profil professionnel Android Enterprise.

> Notez que les appareils Android vous demanderont d'installer l'application Portail d'entreprise Intune, quel que soit le type d'application choisi. Par exemple, si vous sélectionnez 'Applications sur des appareils gérés Intune', les utilisateurs avec des appareils Android non gérés recevront toujours une invite.

Pour iOS, des paramètres de configuration d’application supplémentaires sont nécessaires pour cibler les paramètres de stratégie de protection d’application (APP) sur des applications se trouvant sur des appareils inscrits auprès d’Intune :

- **IntuneMAMUPN** doit être configuré pour toutes les applications managées de gestion des appareils mobiles. Pour plus d’informations, consultez [Guide pratique pour gérer le transfert de données entre applications iOS dans Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** doit être configuré pour toutes les applications managées MDM tierces et métier. Le paramètre **IntuneMAMDeviceID** doit être configuré avec, comme valeur, le jeton d’ID d’appareil. Par exemple, `key=IntuneMAMDeviceID, value={{deviceID}}`. Pour plus d’informations, consultez [Ajouter des stratégies de configuration d’applications pour les appareils iOS gérés](app-configuration-policies-use-ios.md).
- Si seul le paramètre **IntuneMAMDeviceID** est configuré, l’application Intune considère l’appareil comme non géré.

> [!NOTE]
> Pour plus d’informations sur la prise en charge iOS des stratégies de protection d’application basées sur l’état de la gestion des appareils, consultez [MAM protection policies targeted based on management state](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state-) (Ciblage des stratégies de protection MAM en fonction de l’état de la gestion).

## <a name="policy-settings"></a>Paramètres de stratégie
Pour afficher la liste complète des paramètres de stratégie pour iOS et Android, sélectionnez l’un des liens suivants :

- [Stratégies iOS](app-protection-policy-settings-ios.md)
- [Stratégies Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Étapes suivantes
[Surveiller l’état de la conformité et des utilisateurs](app-protection-policies-monitor.md)

## <a name="see-also"></a>Voir aussi
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-android.md)
* [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-ios.md)
