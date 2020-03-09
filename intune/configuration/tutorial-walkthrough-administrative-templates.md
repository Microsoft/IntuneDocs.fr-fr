---
title: 'Procédure pas à pas : créer un modèle d’administration dans Microsoft Intune - Azure | Microsoft Docs'
description: Ce tutoriel ou cette procédure pas à pas utilise Microsoft Intune pour configurer des modèles ADMX Microsoft Edge, Windows et Office sur les appareils Windows versions 10 et ultérieures.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77688088"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>Tutoriel : Utiliser le cloud pour configurer une stratégie de groupe sur des appareils Windows 10 avec des modèles ADMX et Microsoft Intune

> [!NOTE]
> Ce tutoriel a été créé en tant qu’atelier technique pour Microsoft Ignite. Il a plus de prérequis que les tutoriels classiques, car il compare l’utilisation et la configuration des stratégies ADMX dans Intune et localement.

Les modèles d’administration de stratégie de groupe, également appelés modèles ADMX, incluent des paramètres que vous pouvez configurer sur les appareils Windows 10, notamment les PC. Les paramètres de modèle ADMX sont disponibles pour différents services. Ces paramètres sont utilisés par les fournisseurs de gestion des appareils mobiles (MDM, mobile device management), notamment Microsoft Intune. Par exemple, vous pouvez activer Idées de conception dans PowerPoint, définir une page d’accueil dans Microsoft Edge, bloquer les contrôles ActiveX dans Internet Explorer et plus encore.

Les modèles ADMX sont disponibles pour les services suivants :

- **Microsoft Edge** : téléchargez depuis la page des [fichiers de stratégie Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/enterprise).
- **Office** : téléchargez depuis la page [Office 365 ProPlus, Office 2019 et Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).
- **Windows** : intégré au système d’exploitation Windows 10.

Pour plus d’informations sur les stratégies ADMX, consultez [Fonctionnement des stratégies ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies).

Dans Microsoft Intune, ces modèles sont intégrés au service Intune et sont disponibles en tant que profils de **modèles d’administration**. Dans ce profil, vous configurez les paramètres que vous souhaitez inclure, puis vous « attribuez » ce profil à vos appareils.

Dans ce tutoriel, vous allez :

> [!div class="checklist"]
> * Découvrir le [centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)
> * Créer des groupes d’utilisateurs et des groupes d’appareils
> * Comparer les paramètres dans Intune et les paramètres ADMX locaux
> * Créer différents modèles d’administration et configurer les paramètres qui ciblent les différents groupes

À la fin de ce labo, vous aurez les compétences nécessaires pour commencer à utiliser Intune et Microsoft 365 afin de gérer vos utilisateurs et de déployer des modèles d’administration.

Cette fonctionnalité s’applique à :

- Windows 10, versions 1703 et ultérieures

## <a name="prerequisites"></a>Prérequis

- Un abonnement Microsoft 365 E3 ou E5, qui comprend Intune et Azure Active Directory (AD) Premium. Si vous n’avez pas d’abonnement E3 ou E5, [essayez-en un gratuitement](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  Pour plus d’informations sur ce qu’offrent les différentes licences de Microsoft 365, consultez [Transformez votre entreprise avec Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

- Microsoft Intune est configuré en tant qu’**autorité MDM Intune**. Pour plus d’informations, consultez [Définir l’autorité de gestion des appareils mobiles](../fundamentals/mdm-authority-set.md).

  > [!div class="mx-imgBorder"]
  > ![Définir l’autorité MDM sur Microsoft Intune dans l’état de votre locataire](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- Sur un contrôleur de domaine Active Directory local :

  1. Copiez les modèles Office et Microsoft Edge suivants dans le [magasin central (dossier SYSVOL)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra) :

      - [Modèles d’administration Office](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Modèles d’administration Microsoft Edge > Fichier de stratégie](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. Créez une stratégie de groupe pour envoyer (push) ces modèles à un ordinateur d’administration Windows 10 Entreprise dans le même domaine que le contrôleur de domaine. Dans ce tutoriel :

      - La stratégie de groupe que nous avons créée avec ces modèles est appelée **OfficeandEdge**. Vous verrez ce nom dans les images.
      - L’ordinateur d’administration Windows 10 Entreprise que nous utilisons est appelé **ordinateur d’administration**.

      Dans certaines organisations, un administrateur de domaine a deux comptes : un compte de travail de domaine standard et un compte administrateur de domaine différent utilisé uniquement pour les tâches d’administrateur de domaine, telles que la stratégie de groupe.

      La finalité de cet **ordinateur d’administration** est que les administrateurs se connectent avec leur compte administrateur de domaine et accèdent aux outils conçus pour gérer la stratégie de groupe.

- Sur cet **ordinateur d’administration**  :

  - Connectez-vous avec un compte administrateur de domaine.

  - Installez **RSAT : Outils de gestion des stratégies de groupe** :

    1. Ouvrez l’application **Paramètres** > **Applications** > **Fonctionnalités facultatives** > **Ajouter une fonctionnalité**.
    2. Sélectionnez **RSAT : Outils de gestion des stratégies de groupe** > **Installer**.

        Patientez pendant que Windows installe la fonctionnalité. Une fois l’opération terminée, la fonctionnalité apparaît dans l’application **Outils d’administration Windows**.

        > [!div class="mx-imgBorder"]
        > ![Applications Outils d’administration Windows, y compris l’application Gestion des stratégies de groupe](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Veillez à disposer d’un accès à Internet et des droits d’administrateur sur l’abonnement Microsoft 365, qui comprend le centre d’administration du Gestionnaire de points de terminaison.

## <a name="open-the-endpoint-manager-admin-center"></a>Ouvrir le centre d’administration du Gestionnaire de points de terminaison

1. Ouvrez un navigateur web Chromium, tel que Microsoft Edge versions 77 et ultérieures.
2. Accédez au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com). Connectez-vous avec le compte suivant :

    **Utilisateur** : entrez le compte administrateur de votre abonnement de locataire Microsoft 365.  
    **Mot de passe** : entrez son mot de passe.

Ce centre d’administration est axé sur la gestion des appareils et comprend des services Azure, tels qu’Azure AD et Intune. Vous ne verrez peut-être pas les personnalisations **Azure Active Directory** et **Intune**, mais vous les utilisez.

Vous pouvez également ouvrir le centre d’administration du Gestionnaire de points de terminaison à partir du [centre d’administration Microsoft 365](https://admin.microsoft.com) :

1. Accédez à [https://admin.microsoft.com](https://admin.microsoft.com).
2. Connectez-vous avec le compte administrateur de votre abonnement de locataire Microsoft 365.
3. Sous **Centres d’administration**, sélectionnez **Tous les centres d’administration** > **Gestion des points de terminaison**. Le centre d’administration du Gestionnaire de points de terminaison s’ouvre.

    > [!div class="mx-imgBorder"]
    > ![Voir tous les centres d’administration dans le centre d’administration Microsoft 365](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>Créer des groupes et ajouter des utilisateurs

Les stratégies locales sont appliquées dans l’ordre suivant : localement, site, domaine et unité d’organisation (UO). Dans cette hiérarchie, les stratégies d’UO remplacent les stratégies locales, les stratégies de domaine remplacent les stratégies de site, et ainsi de suite.

Dans Intune, les stratégies sont appliquées aux utilisateurs et aux groupes que vous créez. Il n’existe pas de hiérarchie. Si deux stratégies mettent à jour le même paramètre, ce dernier s’affiche en tant que conflit. Si deux stratégies de conformité sont en conflit, la stratégie la plus restrictive s’applique. Si deux profils de configuration sont en conflit, le paramètre n’est pas appliqué. Pour plus d’informations, consultez [Questions, problèmes et solutions concernant les stratégies et les profils d’appareil](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied).

Au cours des étapes suivantes, vous allez créer des groupes de sécurité et y ajouter des utilisateurs. Vous pouvez ajouter un utilisateur à plusieurs groupes. Par exemple, il est normal qu’un utilisateur dispose de plusieurs appareils, tels qu’un Surface Pro pour le travail et un appareil mobile Android à titre personnel. Et il est normal qu’une personne accède aux ressources de l’organisation à partir de ces divers appareils.

1. Dans le Centre d’administration du Gestionnaire de points de terminaison, sélectionnez **Groupes** > **Nouveau groupe**.

2. Saisissez les paramètres suivants :

    - **Type de groupe** : sélectionnez **Sécurité**.
    - **Nom du groupe** : entrez **Tous les appareils d’étudiants Windows 10**.
    - **Type d’appartenance** : sélectionnez **Affecté**.

3. Sélectionnez **Membres** et ajoutez des appareils.

    L’ajout d’appareils est facultatif. L’objectif est de vous exercer à créer des groupes et à y ajouter des appareils. Si vous utilisez ce tutoriel dans un environnement de production, vous devez être conscient de ce que vous êtes en train de faire.

4. **Sélectionnez** > **Créer** pour enregistrer vos modifications.

    Vous ne voyez pas votre groupe ? Sélectionnez **Actualiser**.

5. Sélectionnez **Nouveau groupe**, puis entrez les paramètres suivants :

    - **Type de groupe** : sélectionnez **Sécurité**.
    - **Nom du groupe** : Entrez **Tous les appareils Windows**.
    - **Type d’appartenance** : sélectionnez **Appareil dynamique**.
    - **Membres de dispositif dynamique** : configurez votre requête :

        - **Propriété** : sélectionnez **deviceOSType**.
        - **Opérateur** : sélectionnez **Égal à**.
        - **Valeur** : entrez **Windows**.

        1. Sélectionnez **Ajouter une expression**. Votre expression est indiquée dans la **Syntaxe de la règle** :

            > [!div class="mx-imgBorder"]
            > ![Créer une requête dynamique et ajouter une expression dans le modèle d’administration Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            Quand des utilisateurs ou des appareils répondent aux critères que vous entrez, ils sont automatiquement ajoutés aux groupes dynamiques. Dans cet exemple, les appareils sont automatiquement ajoutés à ce groupe quand le système d’exploitation est Windows. Si vous utilisez ce tutoriel dans un environnement de production, faites attention. L’objectif est de vous exercer à créer des groupes dynamiques.

        2. Sélectionnez **Enregistrer** > **Créer** pour enregistrer vos modifications.

6. Créez le groupe **Tous les enseignants** avec les paramètres suivants :

    - **Type de groupe** : sélectionnez **Sécurité**.
    - **Nom du groupe** : entrez **Tous les enseignants**.
    - **Type d’appartenance** : sélectionnez **Utilisateur dynamique**.
    - **Membres utilisateurs dynamiques** : configurez votre requête :

      - **Propriété** : Sélectionnez **Département**.
      - **Opérateur** : sélectionnez **Égal à**.
      - **Valeur** : Entrez **Enseignants**.

        1. Sélectionnez **Ajouter une expression**. Votre expression est indiquée dans la **Syntaxe de la règle**.

            Quand des utilisateurs ou des appareils répondent aux critères que vous entrez, ils sont automatiquement ajoutés aux groupes dynamiques. Dans cet exemple, les utilisateurs sont automatiquement ajoutés à ce groupe quand leur département est Enseignants. Vous pouvez entrer le département et d’autres propriétés quand des utilisateurs sont ajoutés à votre organisation. Si vous utilisez ce tutoriel dans un environnement de production, faites attention. L’objectif est de vous exercer à créer des groupes dynamiques.

        2. Sélectionnez **Enregistrer** > **Créer** pour enregistrer vos modifications.

### <a name="talking-points"></a>Points de discussion

- Les groupes dynamiques sont une fonctionnalité d’Azure AD Premium. Si vous n’avez pas Azure AD Premium, vous disposez d’une licence pour créer uniquement des groupes affectés. Pour plus d’informations sur les groupes dynamiques, consultez :

  - [Dynamic Group Membership in Azure Active Directory (Part 1)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Dynamic Group Membership in Azure Active Directory (Part 2)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- Azure AD Premium inclut d’autres services couramment utilisés lors de la gestion des applications et des appareils, notamment l’[authentification multifacteur (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) et l’[accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

- De nombreux administrateurs demandent quand utiliser des groupes d’utilisateurs et quand utiliser des groupes d’appareils. Pour obtenir des instructions, consultez [Groupes d’utilisateurs et groupes d’appareils](device-profile-assign.md#user-groups-vs-device-groups).

- N’oubliez pas qu’un utilisateur peut appartenir à plusieurs groupes. Considérez certains des autres groupes d’utilisateurs et d’appareils dynamiques que vous pouvez créer, par exemple :

  - Tous les étudiants
  - Tous les appareils Android
  - Tous les appareils iOS/iPadOS
  - Marketing
  - Ressources humaines
  - Tous les employés de Charlotte
  - Tous les employés de Redmond
  - Administrateurs informatiques de la côte ouest
  - Administrateurs informatiques de la côte est

Les utilisateurs et les groupes créés sont également affichés dans le [centre d’administration Microsoft 365](https://admin.microsoft.com), Azure AD dans le portail Azure et [Microsoft Intune dans le portail Azure](https://go.microsoft.com/fwlink/?linkid=2090973). Vous pouvez créer et gérer des groupes dans tous ces domaines pour votre abonnement de locataire. **Si votre objectif est la gestion des appareils, utilisez le [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)** .

### <a name="review-group-membership"></a>Passer en revue l’appartenance aux groupes

1. Dans le centre d’administration du Gestionnaire de points de terminaison, sélectionnez **Utilisateurs**, le nom d’un utilisateur existant.

    > [!div class="mx-imgBorder"]
    > ![Dans le centre d’administration du Gestionnaire de points de terminaison, sélectionner Utilisateurs](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. Passez en revue certaines des informations que vous pouvez ajouter ou changer. Par exemple, examinez les propriétés que vous pouvez configurer, telles que la fonction, le département, la ville, le lieu du bureau et plus encore. Vous pouvez utiliser ces propriétés dans vos requêtes dynamiques lors de la création de groupes dynamiques.
3. Sélectionnez **Groupes** pour voir l’appartenance de cet utilisateur. Vous pouvez également supprimer l’utilisateur d’un groupe.
4. Sélectionnez certaines des autres options pour voir plus d’informations et ce que vous pouvez faire. Par exemple, examinez la licence attribuée, les appareils de l’utilisateur, et bien plus encore.

### <a name="what-did-i-just-do"></a>Actions effectuées

Dans le centre d’administration du Gestionnaire de points de terminaison, vous avez créé des groupes de sécurité et ajouté à ces derniers des utilisateurs et des appareils existants. Nous utiliserons ces groupes au cours des étapes ultérieures de ce tutoriel.

## <a name="create-a-template-in-intune"></a>Créer un modèle dans Intune

Dans cette section, nous créons un modèle d’administration dans Intune, nous examinons certains paramètres dans **Gestion des stratégies de groupe** et nous comparons le même paramètre dans Intune. L’objectif est d’afficher un paramètre dans la stratégie de groupe et d’afficher le même paramètre dans Intune.

1. Dans le Centre d’administration du Gestionnaire de points de terminaison, sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
2. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, entrez **Modèle d’administration - Appareils d’étudiants Windows 10**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Modèles d’administration**.

3. Sélectionnez **Créer**. Dans la liste déroulante **Sélectionner une catégorie**, sélectionnez **Tous les produits**. Tous les paramètres sont affichés. Dans ces paramètres, notez les propriétés suivantes :

    - Le **Chemin** de la stratégie est le même que Gestion des stratégies de groupe ou GPEdit.
    - Le paramètre s’applique aux utilisateurs ou aux appareils.

### <a name="open-group-policy-management"></a>Ouvrir Gestion des stratégies de groupe

Dans cette section, nous allons montrer une stratégie dans Intune et la stratégie correspondante dans l’Éditeur de gestion des stratégies de groupe.

#### <a name="compare-a-device-policy"></a>Comparer une stratégie d’appareil

1. Sur l’**ordinateur d’administration**, ouvrez l’application **Gestion des stratégies de groupe**.

    Cette application est installée avec **RSAT : Outils de gestion des stratégies de groupe**, fonctionnalité facultative que vous installez sur Windows. La [section Prérequis](#prerequisites) (dans cet article) liste les étapes à suivre pour l’installer.

2. Développez **Domaines**, puis sélectionnez votre domaine. Par exemple, sélectionnez **contoso.net**.
3. Cliquez avec le bouton droit sur la stratégie **OfficeandEdge**, puis cliquez sur **Modifier**. Cette action ouvre l’application Éditeur de gestion des stratégies de groupe.

    > [!div class="mx-imgBorder"]
    > ![Cliquer avec le bouton droit sur la stratégie de groupe ADMX OfficeandEdge, puis sélectionner Modifier](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge** est une stratégie de groupe qui comprend les modèles ADMX Office et Microsoft Edge. Cette stratégie est décrite dans la section [Prérequis](#prerequisites) de cet article.

4. Développez **Configuration ordinateur** > **Stratégies** > **Modèles d’administration** > **Panneau de configuration** > **Personnalisation**. Notez les paramètres disponibles.

    > [!div class="mx-imgBorder"]
    > ![Développer Configuration ordinateur dans l’Éditeur de gestion des stratégies de groupe, puis accéder à Personnalisation](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    Double-cliquez sur **Empêcher l’activation de l’appareil photo de l’écran de verrouillage** et consultez les options disponibles :

    > [!div class="mx-imgBorder"]
    > ![Consulter les options des paramètres de configuration de l’ordinateur dans la stratégie de groupe](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. Dans le centre d’administration de la gestion des appareils, accédez à votre **Modèle d’administration - Appareils d’étudiants Windows 10**.
6. Sélectionnez **Tous les produits** dans la liste déroulante, puis recherchez **personnalisation** :

    > [!div class="mx-imgBorder"]
    > ![Rechercher personnalisation dans le modèle d’administration dans Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    Notez les paramètres disponibles.

    Le type de paramètre est **Appareil** et le chemin est **\Panneau de configuration\Personnalisation**. Ce chemin est similaire à ce que vous venez de voir dans l’Éditeur de gestion des stratégies de groupe. Si vous ouvrez le paramètre, vous voyez les mêmes options **Non configuré**, **Activé** et **Désactivé** que dans l’Éditeur de gestion des stratégies de groupe.

#### <a name="compare-a-user-policy"></a>Comparer une stratégie d’utilisateur

1. Dans votre modèle d’administration, recherchez **navigation InPrivate**. Notez le chemin et le fait que le paramètre s’applique aux utilisateurs et aux appareils.

2. Dans l’**Éditeur de gestion des stratégies de groupe**, recherchez les paramètres d’utilisateur et d’appareil correspondants :

    - Appareil : développez **Configuration ordinateur** > **Stratégies** > **Modèles d’administration** > **Composants Windows** > **Internet Explorer** > **Confidentialité** > **Désactiver la navigation InPrivate**.
    - Utilisateur : développez **Configuration utilisateur** > **Stratégies** > **Modèles d’administration** > **Composants Windows** > **Internet Explorer** > **Confidentialité** > **Désactiver la navigation InPrivate**.

    > [!div class="mx-imgBorder"]
    > ![Désactiver la navigation InPrivate dans Internet Explorer à l’aide du modèle ADMX](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> Pour voir les stratégies Windows intégrées, vous pouvez également utiliser GPEdit (application **Éditer la stratégie de groupe**).

#### <a name="compare-an-edge-policy"></a>Comparer une stratégie Edge

1. Dans le centre d’administration de la gestion des appareils, accédez à votre **Modèle d’administration - Appareils d’étudiants Windows 10**.
2. Sélectionnez **Edge version 77 et ultérieure** dans la liste déroulante.
3. Recherchez **démarrage**. Notez les paramètres disponibles.
4. Dans l’Éditeur de gestion des stratégies de groupe, recherchez les paramètres suivants :

    - Appareil : développez **Configuration ordinateur** > **Stratégies** > **Modèles d’administration** > **Microsoft Edge** > **Démarrage, page d’accueil et Page Nouvel onglet**.
    - Utilisateur : développez **Configuration utilisateur** > **Stratégies** > **Modèles d’administration** > **Microsoft Edge** > **Démarrage, page d’accueil et Page Nouvel onglet**.

### <a name="what-did-i-just-do"></a>Actions effectuées

Vous avez créé un modèle d’administration dans Intune. Dans ce modèle, nous avons examiné certains paramètres ADMX et regardé les mêmes paramètres ADMX dans Gestion des stratégies de groupe.

## <a name="add-settings-to-the-students-admin-template"></a>Ajouter des paramètres au modèle d’administration des étudiants

Dans ce modèle, nous configurons des paramètres Internet Explorer pour verrouiller les appareils partagés par plusieurs étudiants.

1. Dans votre **Modèle d’administration - Appareils d’étudiants Windows 10**, recherchez **Désactiver la navigation InPrivate**, puis sélectionnez la stratégie d’appareil :

    > [!div class="mx-imgBorder"]
    > ![Désactiver la stratégie d’appareil de navigation InPrivate dans le modèle d’administration dans Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. Dans cette fenêtre, notez la description et les valeurs que vous pouvez définir. Ces options sont similaires à celles que vous voyez dans la stratégie de groupe.
3. Sélectionnez **Activé** > **OK** pour enregistrer vos modifications.
4. Configurez également les paramètres Internet Explorer suivants. Veillez à cliquer sur **OK** pour enregistrer vos modifications.

    - **Autoriser le glisser-déplacer ou le copier-coller des fichiers**
      - **Type** : Appareil
      - **Chemin** : \Composants Windows\Internet Explorer\Panneau de configuration Internet\Onglet Sécurité\Zone Internet
      - **Valeur** : Désactivé

    - **Empêcher la non-prise en compte des erreurs de certificat**
      - **Type** : Appareil
      - **Chemin** : \Composants Windows\Internet Explorer\Panneau de configuration Internet
      - **Valeur** : Permis

    - **Désactiver la modification de la page d’accueil**
      - **Type** : Utilisateur
      - **Chemin** : \Composants Windows\Internet Explorer
      - **Valeur** : Permis
      - **Page d’accueil** : entrez une URL, par exemple `contoso.com`.

5. Effacez votre filtre de recherche. Notez que les paramètres que vous avez configurés sont listés en haut :

    > [!div class="mx-imgBorder"]
    > ![Les paramètres configurés sont listés en haut de Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>Attribuer votre modèle

1. Dans votre modèle, sélectionnez **Attributions**. Vous devrez peut-être fermer votre modèle, puis le sélectionner dans la liste **Appareils - Profils de configuration** :

    > [!div class="mx-imgBorder"]
    > ![Sélectionner votre profil de modèle d’administration dans la liste des profils de configuration d’appareil dans Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. Choisissez **Sélectionner les groupes à inclure**. Une liste d’utilisateurs et de groupes existants s’affiche.
3. Sélectionnez le groupe **Tous les appareils d’étudiants Windows 10** que vous avez créé, puis choisissez **Sélectionner**.

    Si vous utilisez ce tutoriel dans un environnement de production, envisagez d’ajouter des groupes vides. L’objectif est de vous exercer à l’attribution de votre modèle.

4. **Enregistrez** les changements apportés.

Dès que le profil est enregistré, il s’applique aux appareils quand ils effectuent un check-in auprès d’Intune. Si les appareils sont connectés à Internet, cela peut se produire immédiatement. Pour plus d’informations sur les cycles d’actualisation des stratégies, consultez [Combien de temps faut-il pour que les appareils obtiennent une stratégie, un profil ou une application une fois que ceux-ci ont été attribués ?](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Quand vous attribuez des stratégies et des profils stricts ou restrictifs, ne vous excluez pas. Envisagez de créer un groupe qui est exclu de vos stratégies et profils. L’idée est d’avoir accès à la résolution des problèmes. Supervisez ce groupe pour confirmer qu’il est utilisé comme prévu.

### <a name="what-did-i-just-do"></a>Actions effectuées

Dans le centre d’administration du Gestionnaire de points de terminaison, vous avez créé un profil de configuration d’appareil de modèle d’administration et attribué ce profil à un groupe que vous avez créé.

## <a name="create-a-onedrive-template"></a>Créer un modèle OneDrive

Dans cette section, vous allez créer un modèle d’administrateur OneDrive dans Intune pour contrôler certains paramètres. Ces paramètres spécifiques sont choisis, car ils sont couramment utilisés par les organisations.

1. Créez un autre profil (**Appareils** > **Profils de configuration** > **Créer un profil**).

2. Entrez les propriétés suivantes :

    - **Nom** : Entrez **Modèle d’administration - Stratégies OneDrive qui s’appliquent à tous les utilisateurs Windows 10**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Modèles d’administration**.

3. Sélectionnez **Créer**.
4. Sélectionnez **Office** dans la liste déroulante.
5. **Activez** les paramètres suivants. Veillez à cliquer sur **OK** pour enregistrer vos modifications.

    - **Connecter silencieusement les utilisateurs du client de synchronisation OneDrive avec leurs informations d’identification Windows**
    - **Activer les Fichiers à la demande OneDrive**
    - **Empêcher les utilisateurs de synchroniser leurs comptes OneDrive personnels**

Vos paramètres ressemblent aux suivants :

> [!div class="mx-imgBorder"]
> ![Créer un modèle d’administration OneDrive dans Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

Pour plus d’informations sur les paramètres clients OneDrive, consultez [Utiliser une stratégie de groupe pour contrôler les paramètres clients de synchronisation OneDrive](https://docs.microsoft.com/onedrive/use-group-policy).

### <a name="assign-your-template"></a>Attribuer votre modèle

1. Dans votre modèle, sélectionnez **Attributions**.
2. Choisissez **Sélectionner les groupes à inclure**. Une liste d’utilisateurs et de groupes existants s’affiche.
3. Sélectionnez le groupe **Tous les appareils Windows** que vous avez créé, puis choisissez **Sélectionner**.

    Si vous utilisez ce tutoriel dans un environnement de production, envisagez d’ajouter des groupes vides. L’objectif est de vous exercer à l’attribution de votre modèle.

4. **Enregistrez** les changements apportés.

À ce stade, vous avez créé des modèles d’administration et vous les avez attribués à des groupes que vous avez créés. L’étape suivante consiste à créer un modèle d’administration à l’aide de Windows PowerShell et de l’API Microsoft Graph pour Intune.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>Facultatif : créer une stratégie à l’aide de PowerShell et de l’API Graph

Cette section utilise les ressources suivantes. Nous allons installer ces ressources dans cette section.

- [Kit SDK PowerShell Intune](https://github.com/microsoft/Intune-PowerShell-SDK)
- [API Microsoft Graph pour Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. Sur l’**ordinateur d’administration**, ouvrez **Windows PowerShell** en tant qu’administrateur :

    1. Dans votre barre de recherche, entrez **powershell**.
    2. Cliquez avec le bouton droit sur **Windows PowerShell** > **Exécuter en tant qu’administrateur**.

    > [!div class="mx-imgBorder"]
    > ![Exécuter Windows PowerShell en tant qu’administrateur](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. Obtenez et définissez la stratégie d’exécution.

    1. Entrez : `get-ExecutionPolicy`

        Notez la valeur associée, qui peut être **Restricted**. Quand vous avez terminé le tutoriel, redéfinissez la stratégie sur sa valeur d’origine.

    2. Entrez : `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. Entrez `Y` pour la changer.

    La stratégie d’exécution de PowerShell permet d’empêcher l’exécution de scripts malveillants. Pour plus d’informations, consultez [À propos des stratégies d’exécution](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).

3. Entrez : `Install-Module -Name Microsoft.Graph.Intune`

    Entrez `Y` si :

    - Vous êtes invité à Installer le fournisseur NuGet
    - Vous êtes invité à installer les modules à partir d’un dépôt non approuvé

    L’opération peut prendre plusieurs minutes. Quand vous avez terminé, une invite similaire à l’invite suivante s’affiche :

    > [!div class="mx-imgBorder"]
    > ![Invite Windows PowerShell après l’installation d’un module](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. Dans votre navigateur web, accédez à [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases), puis sélectionnez le fichier **Intune-PowerShell-SDK_v6.1907.00921.0001.zip**.

    1. Sélectionnez **Enregistrer sous**, puis sélectionnez un dossier dont vous vous souviendrez. `c:\psscripts` est un bon choix.
    2. Ouvrez votre dossier, cliquez avec le bouton droit sur le fichier .zip, puis choisissez **Extraire tout** > **Extraire**. La structure de dossiers ressemble au dossier suivant :

        > [!div class="mx-imgBorder"]
        > ![Structure de dossiers du SDK PowerShell Intune après extraction](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. Sous l’onglet **Affichage**, cochez la case **Extensions de noms de fichiers** :

    > [!div class="mx-imgBorder"]
    > ![Sélectionner les extensions de nom de fichier sous l’onglet Affichage dans l’Explorateur](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. Dans votre dossier, accédez à `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`. Cliquez avec le bouton droit sur chaque fichier .dll, puis choisissez **Propriétés** > **Débloquer**.

    > [!div class="mx-imgBorder"]
    > ![Débloquer les fichiers DLL](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. Dans votre application **Windows PowerShell**, entrez :

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    Entrez `R` si vous êtes invité à procéder à l’exécution à partir de l’éditeur non approuvé.

8. Les modèles d’administration Intune utilisent la version bêta de Graph :

    1. Entrez : `Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. Entrez : `Connect-MSGraph -AdminConsent`

    3. Quand vous y êtes invité, connectez-vous avec le même compte administrateur Microsoft 365. Ces applets de commande créent la stratégie dans votre organisation locataire.

        **Utilisateur** : entrez le compte administrateur de votre abonnement de locataire Microsoft 365.  
        **Mot de passe** : entrez son mot de passe.

    4. Sélectionnez **Accepter**.

9. Créez le profil de configuration **Configuration de test**. Entrez :

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    Quand ces applets de commande sont correctement exécutées, le profil est créé. Pour confirmer, accédez au centre d’administration du Gestionnaire de points de terminaison, puis sélectionnez **Profils de configuration**. Votre profil **Configuration de test** doit être listé.

10. Récupérez toutes les définitions de paramètre. Entrez :

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. Recherchez l’ID de définition en utilisant le nom complet du paramètre. Entrez :

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. Configurez un paramètre. Entrez :

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>Voir votre stratégie

1. Dans le centre d’administration du Gestionnaire de points de terminaison, sélectionnez **Profils de configuration** > **Actualiser**.
2. Sélectionnez votre profil **Configuration de test**, puis **Paramètres**.
3. Dans la liste déroulante, sélectionnez **Tous les produits**.

Vous pouvez voir que le paramètre **Connecter silencieusement les utilisateurs du client de synchronisation OneDrive avec leurs informations d’identification Windows** est configuré.

## <a name="policy-best-practices"></a>Bonnes pratiques pour les stratégies

Quand vous créez des stratégies et des profils dans Intune, vous devez prendre en compte certaines recommandations et bonnes pratiques. Pour plus d’informations, consultez [Bonnes pratiques pour les stratégies et les profils](device-profile-create.md#recommendations).

## <a name="clean-up-resources"></a>Nettoyer les ressources

Quand vous n’en avez plus besoin, vous pouvez :

- Supprimer les groupes que vous avez créés :

  - **Tous les appareils d’étudiants Windows 10**
  - **Tous les appareils Windows**
  - **Tous les enseignants**

- Supprimer les modèles d’administration que vous avez créés :

  - **Modèle d’administration - Appareils d’étudiants Windows 10**
  - **Modèle d’administration - Stratégies OneDrive qui s’appliquent à tous les utilisateurs Windows 10**
  - **Configuration de test**

- Réaffecter à la stratégie d’exécution de Windows PowerShell sa valeur d’origine. L’exemple suivant définit la stratégie d’exécution sur Restricted :

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous vous êtes familiarisé avec le [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), avez utilisé le générateur de requêtes pour créer des groupes dynamiques et avez créé des modèles d’administration dans Intune pour configurer les [paramètres ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies). Vous avez également comparé les modèles ADMX en local et dans le cloud avec Intune. En prime, vous avez utilisé des applets de commande PowerShell pour créer un modèle d’administration.

Pour plus d’informations sur les modèles d’administration dans Intune, consultez :

> [!div class="nextstepaction"]
> [Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Microsoft Intune](administrative-templates-windows.md)
