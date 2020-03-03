---
title: Créer et déployer des stratégies de protection d’applications
titleSuffix: Microsoft Intune
description: Cette partie explique comment créer et attribuer des stratégies de protection des applications Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f31b2964-e932-4cee-95c4-8d5506966c85
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d1a55f758be50c342a5c8851106f0c37e6aec50
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513722"
---
# <a name="how-to-create-and-assign-app-protection-policies"></a>Guide pratique de gestion et affectation des stratégies de protection des applications

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Découvrez comment créer et affecter des stratégies de protection d’applications Microsoft Intune pour les utilisateurs de votre organisation. Cette rubrique décrit également comment modifier des stratégies existantes.

## <a name="before-you-begin"></a>Avant de commencer

Vous pouvez appliquer les stratégies de protection des applications aux applications qui s’exécutent sur des appareils gérés ou non par Intune. Pour une description plus détaillée du fonctionnement des stratégies de protection des applications et des scénarios pris en charge par les stratégies Intune App Protection, consultez [Présentation des stratégies Microsoft Intune App Protection](app-protection-policy.md).

Si vous recherchez une liste d’applications prises en charge par la gestion des applications mobiles, consultez [Liste d’applications de gestion des applications mobiles](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

Pour plus d’informations sur l’ajout d’applications métier professionnelles à Microsoft Intune dans le but de préparer des stratégies de protection d’applications, voir [Ajouter des applications à Microsoft Intune](apps-add.md).

## <a name="app-protection-policies-for-iosipados-and-android-apps"></a>Stratégies de protection d’applications pour les applications iOS/iPadOS et Android

Lorsque vous créez une stratégie de protection d’applications pour les applications iOS/iPadOS et Android, vous suivez un flux de processus Intune moderne qui génère une nouvelle stratégie de protection d’applications.

### <a name="create-an-iosipados-or-android-app-protection-policy"></a>Créer une stratégie de protection d’applications pour les applications iOS/iPadOS ou Android
1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Dans le portail Intune, choisissez **Applications** > **Stratégies de protection des applications**. Cette sélection ouvre les informations des **Stratégies de protection des applications**, où vous pouvez créer des stratégies et modifier les stratégies existantes.
3. Sélectionnez **Créer une stratégie** et sélectionnez **iOS/iPadOS** ou **Android**. Le volet **Créer une stratégie** s’affiche.
4. Dans la page **De base**, ajoutez les valeurs suivantes :

    | Valeur | Description |
    |--------------|------------------------------------------------|
    | Nom | Nom de cette stratégie de protection d’applications. |
    | Description | [Facultatif] Description de cette stratégie de protection d’applications. |


    La valeur de **Plateforme** est définie en fonction de votre choix ci-dessus.

    ![Capture d’écran de la page De base du volet Créer une stratégie](~/apps/media/app-protection-policies/app-protection-add-policies-01.png)

5. Cliquez sur **Suivant** pour afficher la page **Applications**.<br>
    La page **Applications** vous permet de choisir la façon dont vous souhaitez appliquer cette stratégie aux applications sur différents appareils. Vous devez ajouter au moins une application.<p>
    
    | Valeur/Option | Description |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Cibler sur les applications figurant sur tous les types d’appareils | Utilisez cette option pour cibler votre stratégie sur les applications figurant sur des appareils présentant un état de gestion quelconque. Choisissez **Non** pour cibler des applications sur des types d’appareils spécifiques. Pour plus d’informations, consultez [Cibler les stratégies de protection d’application en fonction de l’état de la gestion des appareils](#target-app-protection-policies-based-on-device-management-state). |
    |     Types d’appareils | Utilisez cette option pour indiquer si cette stratégie s’applique aux appareils gérés par MDM ou aux appareils non gérés. Dans le cas des stratégies de protection d’applications iOS/iPadOS, sélectionnez **Appareils non gérés** ou **Appareils gérés**. Pour les stratégies de protection des applications Android, sélectionnez **Appareils non gérés**, **Administrateur d’appareil Android** et **Android Entreprise**.  |
    | Applications publiques | Cliquez sur **Sélectionner des applications publiques** pour choisir les applications à cibler. |
    | Applications personnalisées | Cliquez sur **Sélectionner des applications personnalisées** pour sélectionner les applications personnalisées à cibler en fonction d’un ID d’offre groupée. |
    
    La ou les applications que vous avez sélectionnées s’affichent dans la liste des applications publiques et personnalisées. 
6. Cliquez sur **Suivant** pour afficher la page **Protection des données**.<br>
    Cette page fournit des paramètres pour les contrôles de protection contre la perte de données (DLP), dont notamment les restrictions d’opérations Couper, Copier, Coller et Enregistrer sous. Ces paramètres déterminent la manière dont les utilisateurs interagissent avec les données dans les applications auxquelles cette stratégie de protection d’applications s’applique.

    **Paramètres de protection des données** :<br>
    - **Protection des données iOS/iPadOS** - Pour plus d’informations, consultez [Paramètres de stratégie de protection des applications iOS/iPadOS - Protection des données](~/apps/app-protection-policy-settings-ios.md#data-protection).
    - **Protection des données Android** - Pour obtenir des informations, consultez [Paramètres de stratégie de protection des applications Android - Protection des données](~/apps/app-protection-policy-settings-android.md#data-protection).

7. Cliquez sur **Suivant** pour afficher la page **Conditions d’accès**.<br>
    Cette page fournit des paramètres qui vous permettent de configurer les exigences en matière de code confidentiel et d’informations d’identification que les utilisateurs doivent remplir pour accéder aux applications dans un contexte professionnel. 
 
    **Paramètres des conditions d’accès** :<br>
    - **Conditions d’accès iOS/iPadOS** - Pour plus d’informations, consultez [Paramètres de stratégie de protection des applications iOS/iPadOS - Conditions d’accès](~/apps/app-protection-policy-settings-ios.md#access-requirements).
    - **Conditions d’accès Android** - Pour obtenir des informations, consultez [Paramètres de stratégie de protection des applications Android - Conditions d’accès](~/apps/app-protection-policy-settings-android.md#access-requirements).

8. Cliquez sur **Suivant** pour afficher la page **Lancement conditionnel**.<br>
    Cette page fournit des paramètres permettant de définir les exigences de sécurité de connexion pour votre stratégie de protection d’applications. Sélectionnez un **Paramètre** et entrez la **Valeur** que les utilisateurs doivent satisfaire pour se connecter à votre application d’entreprise. Ensuite, sélectionnez l’**action** à effectuer si les utilisateurs ne satisfont pas vos exigences. Dans certains cas, vous pouvez configurer plusieurs actions pour un même paramètre.

    **Paramètres de lancement conditionnel** :<br>
    - **Lancement conditionnel iOS/iPadOS** - Pour plus d’informations, consultez [Paramètres de stratégie de protection des applications iOS/iPadOS - Lancement conditionnel](~/apps/app-protection-policy-settings-ios.md#conditional-launch).
    - **Lancement conditionnel Android** - Pour obtenir des informations, consultez [Paramètres de stratégie de protection des applications Android - Lancement conditionnel](~/apps/app-protection-policy-settings-android.md#conditional-launch).

9. Cliquez sur **Suivant** pour afficher la page **Affectations**.<br>
   La page **Attributions** vous permet d’attribuer la stratégie de protection des applications à des groupes d’utilisateurs.

10. Cliquez sur **Suivant : Vérifier + créer** pour vérifier les valeurs et les paramètres que vous avez entrés pour cette stratégie de protection des applications.

11. Après avoir terminé, cliquez sur **Créer** pour créer la stratégie de protection des applications dans Intune. 

    > [!TIP]
    > Ces paramètres de stratégie sont appliqués uniquement quand vous utilisez des applications dans le contexte de travail. Quand l’utilisateur final utilise l’application pour effectuer une tâche personnelle, il n’est pas affecté par ces stratégies. Notez que quand vous créez un fichier, ce dernier est considéré comme étant un fichier personnel. 

Les utilisateurs finaux peuvent télécharger les applications à partir de l’App Store ou de Google Play. Pour plus d'informations, voir :
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-android.md)
* [Ce qui se passe quand l’application iOS/iPadOS est gérée par des stratégies de protection d’applications](../fundamentals/end-user-mam-apps-ios.md)

## <a name="change-existing-policies"></a>Modifier des stratégies existantes
Vous pouvez modifier une stratégie existante et l’appliquer aux utilisateurs ciblés. Toutefois, quand vous changez des stratégies existantes, les utilisateurs déjà connectés aux applications ne voient pas ces changements pendant une période de huit heures.

Pour voir immédiatement l’effet des changements, l’utilisateur final doit se déconnecter de l’application, puis se reconnecter.

### <a name="to-change-the-list-of-apps-associated-with-the-policy"></a>Pour modifier la liste des applications associées à la stratégie

1. Dans le volet **Stratégies de protection des applications**, sélectionnez la stratégie à changer.

2. Dans le volet *Intune App Protection*, sélectionnez **Propriétés**.

3. En regard de la section intitulée *Applications*, sélectionnez **Modifier**.

4. La page **Applications** vous permet de choisir la façon dont vous souhaitez appliquer cette stratégie aux applications sur différents appareils. Vous devez ajouter au moins une application.<p>
    
    | Valeur/Option | Description |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Cibler sur les applications figurant sur tous les types d’appareils | Utilisez cette option pour cibler votre stratégie sur les applications figurant sur des appareils présentant un état de gestion quelconque. Choisissez **Non** pour cibler des applications sur des types d’appareils spécifiques. Pour plus d’informations, consultez [Cibler les stratégies de protection d’application en fonction de l’état de la gestion des appareils](#target-app-protection-policies-based-on-device-management-state). |
    |     Types d’appareils | Utilisez cette option pour indiquer si cette stratégie s’applique aux appareils gérés par MDM ou aux appareils non gérés. Dans le cas des stratégies de protection d’applications iOS/iPadOS, sélectionnez **Appareils non gérés** ou **Appareils gérés**. Pour les stratégies de protection des applications Android, sélectionnez **Appareils non gérés**, **Administrateur d’appareil Android** et **Android Entreprise**.  |
    | Applications publiques | Cliquez sur **Sélectionner des applications publiques** pour choisir les applications à cibler. |
    | Applications personnalisées | Cliquez sur **Sélectionner des applications personnalisées** pour sélectionner les applications personnalisées à cibler en fonction d’un ID d’offre groupée. |

    La ou les applications que vous avez sélectionnées s’affichent dans la liste des applications publiques et personnalisées. 

5. Cliquez sur **Vérifier + créer** pour passer en revue les applications sélectionnées pour cette stratégie.

6. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour mettre à jour la stratégie de protection des applications.
 
#### <a name="to-change-the-list-of-user-groups"></a>Pour modifier la liste des groupes d’utilisateurs

1. Dans le volet **Stratégies de protection des applications**, sélectionnez la stratégie à changer.

2. Dans le volet *Intune App Protection*, sélectionnez **Propriétés**.

3. En regard de la section intitulée *Attributions*, sélectionnez **Modifier**.

4. Pour ajouter un nouveau groupe d’utilisateurs à la stratégie, sous l’onglet *Inclure*, choisissez **Sélectionner les groupes à inclure**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour ajouter le groupe. 

5. Pour exclure un groupe d’utilisateurs, sous l’onglet *Exclure*, choisissez **Sélectionner les groupes à exclure**, puis sélectionnez le groupe d’utilisateurs. Choisissez **Sélectionner** pour supprimer le groupe d’utilisateurs.  

6. Pour supprimer des groupes qui ont été ajoutés précédemment, dans l’onglet *Inclure* ou l’onglet *Exclure*, sélectionnez les points de suspension (...) et sélectionnez **Supprimer**.

7. Cliquez sur **Vérifier + créer** pour passer en revue les groupes d’utilisateurs sélectionnés pour cette stratégie.

8. Une fois vos modifications aux affectations prêtes, sélectionnez **Enregistrer** pour enregistrer la configuration et déployer la stratégie vers le nouvel ensemble d’utilisateurs. Si vous sélectionnez **Annuler** avant d’enregistrer votre configuration, vous abandonnez toutes les modifications apportées aux onglets *Inclure* et *Exclure*.

### <a name="to-change-policy-settings"></a>Pour modifier les paramètres d’une stratégie

1. Dans le volet **Stratégies de protection des applications**, sélectionnez la stratégie à changer.

2. Dans le volet *Intune App Protection*, sélectionnez **Propriétés**.

3. En regard de la section correspondant aux paramètres que vous souhaitez modifier, sélectionnez **Modifier**. Affectez ensuite de nouvelles paramètres aux paramètres.

7. Cliquez sur **Vérifier + créer** pour passer en revue les paramètres mis à jour pour cette stratégie.

4. Sélectionnez **Enregistrer** pour enregistrer vos changements. Répétez le processus pour sélectionner une zone de paramètres, la modifier, puis enregistrer vos changements, jusqu’à ce que vous ayez effectué tous les changements nécessaires. Vous pouvez ensuite fermer le volet *Protection d’application Intune - Propriétés*. 

## <a name="target-app-protection-policies-based-on-device-management-state"></a>Cibler les stratégies de protection d’application en fonction de l’état de la gestion des appareils
Dans de nombreuses organisations, il est courant d’autoriser les utilisateurs finaux à se servir à la fois d’appareils gérés par Intune MDM (Mobile Device Management), par exemple les appareils d’entreprise, et d’appareils non gérés, protégés uniquement à l’aide des stratégies de protection des applications Intune. Les appareils non gérés sont souvent appelés appareils BYOD (Apportez votre propre appareil).

Dans la mesure où les stratégies de protection des applications Intune ciblent l’identité d’un utilisateur, les paramètres de protection d’un utilisateur peuvent s’appliquer à la fois aux appareils inscrits (gérés par MDM) et aux appareils non inscrits (non gérés par MDM). Ainsi, vous pouvez cibler une stratégie Intune App Protection sur des appareils iOS/iPadOS et Android inscrits ou non auprès d’Intune. Vous pouvez avoir une stratégie de protection pour les appareils non gérés dans laquelle des contrôles de protection contre la perte de données (DLP) stricts sont en place, et une stratégie de protection distincte pour les appareils gérés par MDM, où les contrôles DLP peuvent être un peu plus souples. Pour plus d’informations sur le fonctionnement de cette stratégie sur les appareils personnels Android Entreprise, consultez [Stratégies de protection des applications et profils professionnels](android-deployment-scenarios-app-protection-work-profiles.md).

Pour créer ces stratégies, accédez à **Applications** > **Stratégies de protection des applications** dans la console Intune, puis sélectionnez **Créer une stratégie**. Vous pouvez également modifier une stratégie de protection d’application existante. Pour que la stratégie de protection des applications s’applique aux appareils gérés et non gérés, accédez à la page **Applications** et vérifiez que l’option **Cibler les applications de tous les types d’appareil** a la valeur par défaut **Oui**. Si vous souhaitez effectuer une affectation précise en fonction de l’état de gestion, affectez à l’option **Cibler les applications de tous les types d’appareil** la valeur **Non**. 

### <a name="device-types"></a>Types d’appareils

- **Non géré** : Les appareils non gérés sont des appareils pour lesquels la gestion MDM Intune n'a pas été détectée. cela inclut les appareils gérés par des fournisseurs MDM tiers.
- **Appareils gérés Intune** : Les appareils gérés sont gérés par Intune MDM.
- **Administrateur d’appareil Android** : appareils gérés par Intune utilisant l’API d’administration des appareils Android.
- **Android Enterprise** : appareils gérés par Intune utilisant des profils de travail Android Enterprise ou la gestion complète des appareils Android Enterprise.

> [!NOTE]
> Les appareils Android vous demandent d’installer l’application Portail d’entreprise Intune, quel que soit le type d’appareil choisi. Par exemple, si vous sélectionnez « Android Enterprise », les utilisateurs avec des appareils Android non gérés reçoivent toujours une invite.

Pour iOS/iPadOS, des paramètres de configuration d’application supplémentaires sont nécessaires pour cibler les paramètres de stratégie de protection d’application (APP) sur les applications se trouvant sur des appareils inscrits auprès d’Intune :

- **IntuneMAMUPN** doit être configuré pour toutes les applications managées de gestion des appareils mobiles. Pour plus d’informations, consultez [Guide pratique pour gérer le transfert de données entre applications iOS/iPadOS dans Microsoft Intune](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).
- **IntuneMAMDeviceID** doit être configuré pour toutes les applications gérées MDM tierces et métier. Le paramètre **IntuneMAMDeviceID** doit être configuré avec, comme valeur, le jeton d’ID d’appareil. Par exemple, `key=IntuneMAMDeviceID, value={{deviceID}}`. Pour plus d’informations, consultez [Ajout de stratégies de configuration des applications pour les appareils iOS/iPadOS gérés](app-configuration-policies-use-ios.md).
- Si seul le paramètre **IntuneMAMDeviceID** est configuré, l’application Intune considère l’appareil comme non géré.

> [!NOTE]
> Pour plus d’informations sur la prise en charge iOS/iPadOS des stratégies de protection d’applications en fonction de l’état de la gestion des appareils, consultez [Stratégies de protection MAM ciblées en fonction de l’état de la gestion](../fundamentals/whats-new-archive.md#mam-protection-policies-targeted-based-on-management-state).

## <a name="policy-settings"></a>Paramètres de stratégie
Pour afficher la liste complète des paramètres de stratégie pour iOS/iPadOS et Android, sélectionnez l’un des liens suivants :

- [Stratégies iOS/iPadOS](app-protection-policy-settings-ios.md)
- [Stratégies Android](app-protection-policy-settings-android.md)

## <a name="next-steps"></a>Étapes suivantes
[Surveiller l’état de la conformité et des utilisateurs](app-protection-policies-monitor.md)

## <a name="see-also"></a>Voir aussi
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-android.md)
* [Ce qui se passe quand l’application iOS/iPadOS est gérée par des stratégies de protection d’applications](../fundamentals/end-user-mam-apps-ios.md)
