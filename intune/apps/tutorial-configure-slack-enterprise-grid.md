---
title: 'Tutoriel : Configurer Slack afin d’utiliser Intune pour l’EMM et la configuration d’applications'
titleSuffix: Microsoft Intune
description: Dans le tutoriel, vous allez configurer Slack afin d’utiliser Intune pour l’EMM et la configuration d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3b01c1444b44e3f5c66fc129f78f321c9c9f5aa
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563396"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Tutoriel : Configurer Slack afin d’utiliser Intune pour l’EMM et la configuration d’applications

Slack est une application de collaboration que vous pouvez utiliser avec Microsoft Intune.   

Dans ce tutoriel, vous allez :
> [!div class="checklist"]
> - Définir Intune comme le fournisseur de gestion de mobilité d’entreprise (EMM) sur votre outil Slack Enterprise Grid. Vous serez en mesure de limiter l’accès aux espaces de travail de votre plan Grid aux appareils gérés par Intune.
> - Créer des stratégies de configuration des applications afin de gérer l’application Slack pour l’EMM sur iOS et l’application Slack pour les appareils avec profil professionnel Android.
> - Créer des stratégies de conformité d’appareil Intune pour définir les conditions que des appareils Android et iOS doivent remplir pour être considérés comme conformes.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
Vous aurez besoin d’un locataire de test avec les abonnements suivants pour ce tutoriel :
- Azure Active Directory Premium ([essai gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Abonnement Intune ([essai gratuit](../fundamentals/free-trial-sign-up.md))

Vous aurez également besoin d’un plan [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-).

## <a name="configure-your-slack-enterprise-grid-plan"></a>Configurer votre plan Slack Enterprise Grid
Activer la gestion de la mobilité d’entreprise pour votre plan Slack Enterprise Grid en suivant les [instructions de Slack](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) et [Connecter Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) en tant que fournisseur d’identité de votre plan (IDP) Grid.

## <a name="sign-in-to-intune"></a>Se connecter à Intune
Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune. Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Configurer Slack pour l’EMM sur des appareils iOS
Ajoutez l’application Slack iOS pour l’EMM à votre locataire et créez une stratégie de configuration des applications pour permettre aux utilisateurs iOS de votre organisation d’accéder à Slack avec Intune en tant que fournisseur d’EMM.

### <a name="add-slack-for-emm-to-intune"></a>Ajouter Slack à Intune pour l’EMM
Ajouter Slack pour l’EMM en tant qu’application iOS managée dans Intune et affecter vos utilisateurs Slack. Les applications étant spécifiques à la plateforme, vous devez ajouter une application Intune distincte pour vos utilisateurs Slack sur des appareils Android.
1. Dans Intune, sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
2. Sous le type d’applications, sélectionnez **Application Store - iOS**.
3. Sélectionnez **Rechercher dans l’App Store**. Entrez le terme de recherche « Slack pour l’EMM » et sélectionnez l’application.
4. Sélectionnez **Informations sur l’application** et configurez toutes les modifications comme bon vous semble.
5. Sélectionnez **Ajouter**.
6. Dans la barre de recherche, entrez « Slack pour l’EMM » et sélectionnez l’application que vous venez d’ajouter.
7. Sous Gérer, sélectionnez **Affectations**.
8. Sélectionnez **Ajouter un groupe**. En fonction des utilisateurs choisis pour être affectés lorsqu’EMM pour Slack est activé, sous **Type d’affectation** vous pouvez souhaiter sélectionner :
    - **Disponible pour les appareils inscrits** si vous choisissez « Tous les membres (invités compris) » OU
    - **Disponible avec ou sans inscription** si vous avez choisi « Tous les membres (sauf les invités) » ou « Facultatif ».
9. Sélectionnez **Groupes inclus** et, sous Rendre cette application accessible à tous les utilisateurs, sélectionnez **Oui**.
10. Cliquez sur **OK**, puis de nouveau sur **OK**.
11. Cliquez sur **Save**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Ajouter une stratégie de configuration des applications pour Slack pour l’EMM
Ajouter une stratégie de configuration des applications pour Slack pour l’EMM iOS. Les stratégies de configuration pour les appareils gérés étant spécifiques à la plateforme, vous devez ajouter une stratégie distincte pour vos utilisateurs Slack sur des appareils Android.
1. Dans Intune, sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter**.
2. Dans le champ Nom, entrez Test de la stratégie de configuration de l’application Slack.
3. Sous le type d’inscription de l’appareil, sélectionnez **Appareils gérés**.
4. Sous Plateforme, sélectionnez **iOS**.
5. Sélectionnez **Application associée**.
6. Dans la barre de recherche, entrez « Slack pour l’EMM » et sélectionnez l’application.
7. Cliquez sur **OK**, puis sélectionnez **Paramètres de configuration**. 
8. Sélectionnez **OK**, puis **Ajouter**.
9. Dans la barre de recherche, entrez « Test de stratégie de configuration de l’application Slack » et sélectionnez la stratégie que vous venez d’ajouter.
10. Sous Gérer, sélectionnez **Affectations**.
11. Sous Affecter à, sélectionnez **Tous les utilisateurs + Tous les appareils**.
12. Cliquez sur **Save**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Facultatif) Créer une stratégie de conformité des appareils iOS
Configurez une stratégie de conformité d’appareil Intune pour définir les conditions qu’un appareil doit respecter pour être considéré comme conforme. Pour ce tutoriel, nous allons créer une stratégie de conformité pour des appareils iOS. Les stratégies de conformité étant spécifiques à la plateforme, vous devez créer une stratégie distincte pour vos utilisateurs Slack sur des appareils Android.
1. Dans Intune, sélectionnez **Conformité des appareils** > **Stratégies** > **Créer une stratégie**.
2. Dans le champ Nom, entrez « Test de stratégie de conformité iOS ».
3. Dans le champ Description, entrez « Test de stratégie de conformité iOS ».
4. Sous Plateforme, sélectionnez **iOS**.
5. Sélectionnez **Intégrité de l’appareil**. En regard d’Appareils jailbreakés, sélectionnez **Bloquer**, puis **OK**.
6. Sélectionnez **Sécurité système** et entrez les paramètres du mot de passe. Pour ce tutoriel, sélectionnez les paramètres recommandés suivants :
    - Pour Exiger un mot de passe pour déverrouiller des appareils mobiles, sélectionnez **Exiger**.
    - Pour Mots de passe simples, sélectionnez **Bloquer**.
    - Pour Longueur minimale du mot de passe, entrez 4.
    - Pour Type de mot de passe requis, choisissez**Alphanumérique**.
    - Pour Nombre maximal de minutes après le verrouillage d’écran avant que le mot de passe ne soit obligatoire, choisissez **Immédiatement**.
    - Pour Expiration du mot de passe (jours), entrez 41.
    - Pour Nombre de mots de passe précédents pour empêcher la réutilisation, entrez 5.
7. Cliquez sur **OK**, puis sélectionnez à nouveau **OK**.
8. Cliquez sur **Create (Créer)** .

## <a name="set-up-slack-on-android-work-profile-devices"></a>Configurer Slack sur les appareils avec profil professionnel Android
Ajoutez l’application Google Play managée Slack à votre locataire et créez une stratégie de configuration des applications pour permettre aux utilisateurs Android de votre organisation d’accéder à Slack avec Intune en tant que fournisseur d’EMM.

### <a name="add-slack-to-intune"></a>Ajouter Slack à Intune
Ajouter Slack en tant qu’application Google Play managée dans Intune et affecter vos utilisateurs Slack. Les applications étant spécifiques à la plateforme, vous devez ajouter une application Intune distincte pour vos utilisateurs Slack sur des appareils iOS.
1. Dans Intune, sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
2. Sous Type d’application, sélectionnez **application Store - Google Play managée**.
3. Sélectionnez **Google Play managée - Approuver**. Entrez le terme de recherche « Slack pour l’EMM » et sélectionnez l’application.
4. Sélectionnez **Approuver**.
5. Dans la barre de recherche, entrez « Slack » et sélectionnez l’application que vous venez d’ajouter.
6. Sous Gérer, sélectionnez **Affectations**.
7. Sélectionnez **Ajouter un groupe**. En fonction des utilisateurs choisis pour être affectés lorsqu’EMM pour Slack est activé, sous **Type d’affectation** vous pouvez souhaiter sélectionner :
    - **Disponible pour les appareils inscrits** si vous choisissez « Tous les membres (invités compris) » OU
    - **Disponible avec ou sans inscription** si vous avez choisi « Tous les membres (sauf les invités) » ou « Facultatif ».
8. Sélectionnez Groupes inclus et, sous Rendre cette application accessible à tous les utilisateurs, sélectionnez **Oui**.
9. Cliquez sur **OK**, puis de nouveau sur **OK**.
10. Cliquez sur **Save**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Ajouter une stratégie de configuration des applications pour Slack
Ajouter une stratégie de configuration des applications pour Slack. Les stratégies de configuration pour les appareils gérés étant spécifiques à la plateforme, vous devez ajouter une stratégie distincte pour vos utilisateurs Slack sur des appareils iOS.
1. Dans Intune, sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter**.
2. Dans le champ Nom, entrez Test de la stratégie de configuration de l’application Slack.
3. Sous le type d’inscription de l’appareil, sélectionnez **Appareils gérés**.
4. Sous Plateforme, sélectionnez **Android**.
5. Sélectionnez **Application associée**.
6. Dans la barre de recherche, entrez « Slack pour » et sélectionnez l’application.
7. Sélectionnez **OK**, puis **Paramètres de configuration**.
    - Pour plus d’informations sur les clés de configuration et leurs valeurs, consultez la documentation sur l’onglet « Technique » de la [page web AppConfig de Slack](https://www.appconfig.org/company/slack/).
8. Sélectionnez **OK**, puis **Ajouter**.
9. Dans la barre de recherche, entrez « Test de stratégie de configuration de l’application Slack » et sélectionnez la stratégie que vous venez d’ajouter.
10. Sous Gérer, sélectionnez **Affectations**.
11. Sous Affecter à, sélectionnez **Tous les utilisateurs + Tous les appareils**.
12. Cliquez sur **Save**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Facultatif) Créer une stratégie de conformité des appareils Android
Configurez une stratégie de conformité d’appareil Intune pour définir les conditions qu’un appareil doit respecter pour être considéré comme conforme. Pour ce tutoriel, nous allons créer une stratégie de conformité pour des appareils Android. Les stratégies de conformité étant spécifiques à la plateforme, vous devez créer une stratégie distincte pour vos utilisateurs Slack sur des appareils iOS.
1. Dans Intune, sélectionnez **Conformité des appareils** > **Stratégies** > **Créer une stratégie**.
2. Dans le champ Nom, entrez « Test de stratégie de conformité Android ».
3. Dans le champ Description, entrez « Test de stratégie de conformité Android ».
4. Sous Plateforme, sélectionnez **Android Entreprise**.
5. Sous Type de profil, sélectionnez **Profil professionnel**.
6. Sélectionnez **Intégrité de l’appareil**. En regard d’Appareils rootés, sélectionnez **Bloquer**, puis sélectionnez **OK**.
7. Sélectionnez **Sécurité système** et entrez les **Paramètres du mot de passe**. Pour ce tutoriel, sélectionnez les paramètres recommandés suivants :
    - Pour Exiger un mot de passe pour déverrouiller des appareils mobiles, sélectionnez **Exiger**.
    - Pour le type de mot de passe requis, sélectionnez **Au moins alphanumérique**.
    - Pour Longueur minimale du mot de passe, entrez 4.
    - Pour Nombre maximal de minutes après le verrouillage d’écran avant que le mot de passe ne soit obligatoire, choisissez **15 minutes**.
    - Pour Expiration du mot de passe (jours), entrez 41.
    - Pour Nombre de mots de passe précédents pour empêcher la réutilisation, entrez 5.
8. Cliquez sur **OK**, puis de nouveau sur **OK**.
9. Cliquez sur **Create (Créer)** .

## <a name="launch-slack"></a>Lancez Slack

Avec les stratégies que vous venez de créer, tout appareil iOS ou Android à profil professionnel qui tentera de se connecter à l’un de vos espaces de travail devra être inscrit à Intune. Pour tester ce scénario, essayez de lancer Slack pour l’EMM sur un appareil iOS ou sur un appareil à profil professionnel Android inscrits à Intune. 

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel :
- Vous avez défini Intune comme le fournisseur de gestion de mobilité d’entreprise (EMM) sur votre outil Slack Enterprise Grid. 
- Vous avez créé des stratégies de configuration des applications afin de gérer l’application Slack pour l’EMM sur iOS et l’application Slack pour les appareils avec profil professionnel Android.
- Vous avez créé des stratégies de conformité d’appareil Intune pour définir les conditions que des appareils Android et iOS doivent remplir pour être considérés comme conformes.

Pour en savoir plus sur les stratégies de configuration d’applications, consultez [Stratégies de configuration d’applications pour Microsoft Intune](app-configuration-policies-overview.md). Pour en savoir plus sur les stratégies de conformité des appareils, consultez [Définir des règles sur les appareils pour autoriser l’accès aux ressources de votre organisation à l’aide d’Intune](../protect/device-compliance-get-started.md).
