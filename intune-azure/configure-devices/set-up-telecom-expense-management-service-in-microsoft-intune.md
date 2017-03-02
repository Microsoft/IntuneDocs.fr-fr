---
title: "Configurer un service de gestion des dépenses en télécommunications"
titleSuffix: Intune Azure preview
description: "Préversion d’Intune Azure : configuration du service de gestion de frais de télécommunications Saaswedo pour l’intégration à Intune."
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: aa2e668641da1a87e6145fe826d88c2ca5b184a2
ms.lasthandoff: 02/18/2017

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Configurer un service de gestion des dépenses en télécommunications dans la préversion d’Intune Azure
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune vous permet de gérer les dépenses en télécommunications inhérentes à l’utilisation des données sur les appareils mobiles d’entreprise. Pour activer cette fonctionnalité, Intune est intégré à la solution de gestion des dépenses en télécommunications Datalert du développeur de logiciels tiers Saaswedo. Datalert est un logiciel de gestion des frais de télécommunications en temps réel qui vous permet de gérer l’utilisation des données de télécommunications et éviter de des dépassements inattendus et coûteux de données d’itinérance pour vos appareils gérés par Intune. 

L’intégration d’Intune avec Datalert vous permet de définir, surveiller et appliquer de façon centralisée des limites d’utilisation de données d’itinérance et locales à l’aide d’alertes automatiques lorsque les limites dépassent des seuils définis. Vous pouvez configurer le service pour appliquer différentes actions à des individus ou des groupes d’utilisateurs finaux, notamment la désactivation de l’itinérance, lorsque les utilisateurs dépassent le seuil. Des rapports qui fournissent des informations de surveillance et d’utilisation des données sont disponibles à partir de la console de gestion Datalert.

Le diagramme suivant montre comment Intune s’intègre à Datalert.

  ![Diagramme de l’intégration d’Intune et de Datalert](../media/tem-datalert-intune-solution-diagram.png)

Avant de pouvoir utiliser le service Datalert avec Intune, vous devez configurer les paramètres dans la console Datalert et dans Intune. La connexion doit être activée pour le service Datalert et pour Intune. Si le côté Datalert de la connexion est activé, mais pas la partie Intune, Intune reçoit la communication, mais l’ignore.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Samsung Knox
- iOS 8.0 et versions ultérieures

## <a name="prerequisites"></a>Conditions préalables

- Un abonnement à Microsoft Intune et un accès au portail Azure, qui est actuellement en préversion publique.
- Un abonnement au service de gestion des frais de télécommunications Datalert

## <a name="list-of-telecom-expense-management-providers"></a>Liste de fournisseurs de gestion des dépenses en télécommunications

Actuellement, Intune s’intègre avec les fournisseurs de gestion de frais de télécommunications suivants :

[Service de gestion des dépenses en télécommunications Saaswedo Datalert](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Déployer la solution intégrée Intune et Datalert

Avant de commencer, vérifiez que vous avez déjà un abonnement à Intune et à un service de gestion des dépenses en télécommunications Datalert.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Étape 1 : Connecter le service Datalert à Microsoft Intune

1. Connectez-vous à la console de gestion Datalert avec vos informations d’identification d’administrateur.

2. Dans la console de gestion Datalert, accédez à l’onglet **Paramètres**, puis à **Configuration MDM**.

3. Sélectionnez **Déverrouiller** pour pouvoir entrer les paramètres dans la page.

4. Pour **serveur MDM**, choisissez **Microsoft Intune**.

5. Pour **Domaine Azure AD**, entrez votre ID de client Azure, puis sélectionnez le bouton **Connexion**.

    Sélectionnez **Connexion** pour que le service Datalert vérifie auprès d’Intune qu’il n’existe aucune connexion Datalert préexistante avec Intune. Après quelques secondes, une page de connexion de Microsoft s’affiche, suivie de l’authentification Datalert Azure.

6. Sur la page d’authentification Microsoft, sélectionnez **Accepter**. Vous êtes redirigé vers une page de remerciement de Datalert, qui se ferme après quelques secondes. Datalert valide la connexion et affiche des coches vertes à côté d’une liste d’éléments validés. Si la validation échoue, vous verrez un message en rouge. Dans ce cas, contactez le support technique de Datalert pour de l’aide.

    La capture d’écran suivante montre les coches vertes que vous pouvez vous attendre à voir une fois la connexion établie.

  ![Page Datalert présentant une connexion établie](../media/tem-mdm-configuration-mdm-server-page.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Étape 2 : Vérifier que la fonctionnalité de gestion des dépenses en télécommunications est active dans Intune

Une fois l’étape 1 ci-dessus effectuée, votre connexion doit être automatiquement activée et l’état de connexion **Actif** doit figurer dans le portail Azure. Les étapes suivantes vous montrent comment vérifier que l’état est **Actif**.

1. Connectez-vous au portail Azure.

2. Choisissez **Plus de services** > **Analyse + Gestion** > **Intune**.

3. Dans le panneau **Intune**, choisissez **Configurer des appareils**.

4. Dans le panneau **Configuration de l’appareil**, choisissez **Installation** > **Gestion des dépenses de télécommunications**. 

   Recherchez l’état de connexion **Actif** en haut de la page.

  ![Portail Azure affichant l’état de connexion Actif de Datalert](../media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Étape 3 : Déployer l’application Datalert sur des appareils inscrits par l’entreprise

Pour vérifier que l’utilisation des données à partir de lignes appartenant uniquement à l’entreprise est collectée, vous devez créer des catégories d’appareils dans Intune, puis cibler l’application Datalert uniquement sur les téléphones d’entreprise. Exécutez les étapes des sous-sections suivantes.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Définir des catégories d’appareils et des groupes d’appareils mappés à ces catégories

En fonction des besoins de votre organisation, vous devez créer au moins deux catégories d’appareils (par exemple, Entreprise et Personnels) et créer des groupes d’appareils dynamiques pour chaque catégorie. Si nécessaire, vous pouvez créer des catégories supplémentaires pour votre organisation. 

Ces catégories s’affichent aux utilisateurs lors de l’inscription. En fonction de la catégorie choisie par les utilisateurs, l’appareil inscrit est déplacé vers le groupe d’appareils correspondant. Pour connaître les étapes permettant de créer des catégories d’appareils, consultez [Mapper des appareils à des groupes](https://docs.microsoft.com/intune-azure/enroll-devices/how-to-use-device-group-mapping).

  ![Capture d’écran du panneau Ajouter une stratégie](../media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Créer l’application Datalert dans Intune

Procédez comme suit pour créer l’application Datalert dans Intune pour chaque plateforme. iOS est utilisé comme exemple dans ces étapes.

1. Dans le panneau **Intune** du portail Azure, choisissez **Gérer les applications**.

2. Dans le panneau **Gérer les applications**, choisissez **Gérer** > **Applications**. 

3. Sélectionnez **Ajouter** pour ajouter une application.

4. Sélectionnez le type d’application. Par exemple, pour iOS, sélectionnez **Application de l’App Store iOS**.

5. Dans **Rechercher dans l’App Store**, recherchez l’application Datalert en tapant **Datalert** dans la fenêtre de recherche.

6. Sélectionnez l’application **Datalert**, puis sélectionnez **OK**.

  ![Capture d’écran du panneau Ajouter une stratégie](../media/tem-select-app-from-apple-app-store.png)

7. Effectuez les étapes restantes pour créer une application pour iOS.

  ![Capture d’écran du panneau Ajouter une stratégie](../media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Affecter l’application Datalert au groupe d’appareils d’entreprise

1. Sélectionnez l’application Datalert iOS créée à l’étape précédente.

2. Dans le panneau **Applications**, accédez à **Gérer** > **Affectations**. 

3. Choisissez **Sélectionner des groupes**, puis suivez les étapes permettant de sélectionner le groupe d’appareils d’entreprise.

4. Choisissez de rendre l’installation de l’application obligatoire ou facultative pour le groupe. L’exemple de capture d’écran suivant montre l’installation quand elle est obligatoire, ce qui signifie que les utilisateurs doivent installer l’application Datalert après avoir inscrit leur appareil.

  ![Capture d’écran du panneau Ajouter une stratégie](../media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Étape 4 : Ajouter des lignes téléphoniques payées par l’entreprise à la console Datalert 

Vous avez configuré les services Intune et Datalert pour qu’ils communiquent entre eux. Vous devez maintenant ajouter des lignes téléphoniques payées par votre entreprise à la console Datalert, et définir des seuils et actions concernant toutes les violations de l’utilisation de ces lignes par des téléphones portables ou en itinérance. 

Pour définir ces éléments, accédez à la page relative au [programme d’installation de Datalert pour Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup), puis suivez les étapes de l’Assistant Installation sous l’onglet **Paramètres**.

  ![Capture d’écran du panneau Ajouter une stratégie](../media/tem-add-phone-lines-to-datalert-console.png)


Le service Datalert est maintenant actif, et commence à surveiller l’utilisation des données et la désactivation des données cellulaires et d’itinérance sur les appareils qui dépassent les limites d’utilisation configurées.

## <a name="turning-off-the-datalert-service"></a>Désactivation du service Datalert

Si vous désactivez le service Datalert dans le portail Azure :

- Toutes les actions qui ont été appliquées aux appareils, en raison de violations des limites d’utilisation, sont annulées.
- L’accès aux données et à l’itinérance n’est plus bloqué pour les utilisateurs.
- Intune reçoit toujours les signaux provenant du service, mais les ignore.

**Pour désactiver le service**

1. Dans le panneau **Gestion des dépenses de télécommunications** dans le portail Azure, sélectionnez **Désactiver**.

2. Sélectionnez **Enregistrer**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Affichage de rapports d’utilisation de données et d’itinérance

Pour l’instant, le rapport d’utilisation des données est disponible uniquement dans la console de gestion de Datalert de Saaswedo.

Les instructions que vos utilisateurs finaux suivent pour installer l’application Datalert seront bientôt disponibles.
