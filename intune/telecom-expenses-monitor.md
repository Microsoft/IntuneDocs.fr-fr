---
title: Configurer un service de gestion des dépenses en télécommunications
titleSuffix: Microsoft Intune
description: Intégrez Intune avec le service de gestion des dépenses de télécommunications Saaswedo.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e4c44552a0df369767bb91749351674af9eab4b3
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959551"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurer un service de gestion des dépenses en télécommunications dans Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune vous permet de gérer les dépenses de télécommunications inhérentes à l’utilisation des données sur les appareils mobiles d’entreprise. Pour activer cette fonctionnalité, Intune est intégré à la solution de [gestion des dépenses de télécommunications Datalert](http://datalert.biz/get-started) du développeur de logiciels tiers Saaswedo. Datalert est un logiciel de gestion des dépenses de télécommunications en temps réel qui vous permet de gérer l’utilisation des données de télécommunications. Il vous aide à éviter les surcoûts de données et d’itinérance sur vos appareils gérés par Intune.

L’intégration d’Intune avec Datalert vous permet de définir, surveiller et appliquer de façon centralisée des limites d’utilisation de données d’itinérance et locales. Des alertes automatisées sont déclenchées quand les limites dépassent des seuils définis. Vous pouvez configurer le service pour appliquer différentes actions à des individus ou à des groupes d’utilisateurs finaux (comme la désactivation de l’itinérance en cas de dépassement de seuil). Des rapports qui fournissent des informations de surveillance et d’utilisation des données sont disponibles à partir de la console de gestion Datalert.

Le diagramme suivant montre comment Intune s’intègre à Datalert.

  ![Diagramme de l’intégration d’Intune et de Datalert](./media/tem-datalert-intune-solution-diagram.png)

Avant de pouvoir utiliser le service Datalert avec Intune, vous devez configurer les paramètres dans la console Datalert et dans Intune. La connexion doit être activée pour le service Datalert et pour Intune. Si le côté Datalert de la connexion est activé, mais pas la partie Intune, Intune reçoit la communication, mais l’ignore.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Samsung Knox
- iOS 8.0 et versions ultérieures

## <a name="prerequisites"></a>Prérequis

- Un abonnement à Microsoft Intune et un accès au portail Azure.
- Un abonnement au service de gestion des frais de télécommunications Datalert

## <a name="list-of-telecom-expense-management-providers"></a>Liste de fournisseurs de gestion des dépenses en télécommunications

Actuellement, Intune s’intègre avec les fournisseurs de gestion de frais de télécommunications suivants :

[Service de gestion des dépenses en télécommunications Saaswedo Datalert](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Déployer la solution intégrée Intune et Datalert

Avant de commencer, vérifiez que vous avez déjà un abonnement à Intune et à un service de gestion des dépenses en télécommunications Datalert.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Étape 1 : Connecter le service Datalert à Microsoft Intune

1. Connectez-vous à la console de gestion Datalert avec vos informations d’identification d’administrateur.

2. Dans la console de gestion Datalert, accédez à l’onglet **Paramètres**, puis à **Configuration MDM**.

3. Sélectionnez **Unblock** (Débloquer) en bas de la page, ce qui vous permet de modifier les paramètres dans la page.

4. Dans la section **Intune / Datalert Connection** (Connexion Intune/Datalert), choisissez **Microsoft Intune** pour **MDM server** (Serveur MDM).    

5. Pour **Azure AD domain** (Domaine Azure AD), entrez votre ID de locataire Azure, puis sélectionnez **Connection**.

    Quand vous sélectionnez **Connection**, le service Datalert vérifie auprès d’Intune qu’il n’existe aucune connexion Datalert préexistante avec Intune. Après quelques secondes, une page de connexion de Microsoft s’affiche, suivie de l’authentification Datalert Azure.

6. Sur la page d’authentification Microsoft, sélectionnez **Accepter**. Vous êtes redirigé vers une page de **remerciement** de Datalert, qui se ferme après quelques secondes. Datalert valide la connexion et affiche des coches vertes en regard d’une liste d’éléments validés. Si la validation échoue, un message s’affiche en rouge et vous devez contacter le support Datalert afin d’obtenir de l’aide.

    La capture d’écran suivante montre les coches vertes que vous pouvez vous attendre à voir une fois la connexion établie.

   ![Page Datalert présentant une connexion établie](./media/tem-datalert-connection.png)

7. Dans la section **Datalert App / ADAL Consent** (Application Datalert/Consentement ADAL), définissez le commutateur sur **On** (Activé). Sur la page d’authentification Microsoft, sélectionnez **Accepter**. Vous êtes redirigé vers une page de **remerciement** de Datalert, qui se ferme après quelques secondes. Datalert valide la connexion et affiche des coches vertes en regard d’une liste d’éléments validés. Si la validation échoue, un message s’affiche en rouge et vous devez contacter le support Datalert afin d’obtenir de l’aide.    

    La capture d’écran suivante montre les coches vertes que vous pouvez vous attendre à voir une fois la connexion établie.

   ![Page Datalert présentant une connexion établie](./media/tem-datalert-adal-consent.png)

8. Dans la section **MDM Profiles management (optional)** (Gestion des profils MDM - facultatif), définissez le commutateur sur **On** pour permettre à Datalert de lire les profils disponibles dans Intune afin de vous aider à configurer des stratégies. Sur la page d’authentification Microsoft, sélectionnez **Accepter**. Vous êtes redirigé vers une page de **remerciement** de Datalert, qui se ferme après quelques secondes. Datalert valide la connexion et affiche des coches vertes en regard d’une liste d’éléments validés. Si la validation échoue, un message s’affiche en rouge et vous devez contacter le support Datalert afin d’obtenir de l’aide.    

    La capture d’écran suivante montre les coches vertes que vous pouvez vous attendre à voir une fois la connexion établie.

   ![Page Datalert présentant une connexion établie](./media/tem-datalert-mdm-profiles.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Étape 2 : Vérifier que la fonctionnalité de gestion des dépenses en télécommunications est active dans Intune

Une fois l’étape 1 ci-dessus effectuée, votre connexion doit être automatiquement activée et l’état de connexion **Actif** doit figurer dans le portail Azure. Les étapes suivantes vous montrent comment vérifier que l’état est **Actif**.

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.

3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.

4. Dans le volet **Configuration de l’appareil**, choisissez **Installation** > **Gestion des dépenses de télécommunications**.

   Recherchez l’état de connexion **Actif** en haut de la page.

   ![Page Intune affichant l’état de connexion Actif de Datalert](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Étape 3 : Déployer l’application Datalert sur des appareils inscrits de l’entreprise

Pour vous assurer que seule l’utilisation des données à partir de lignes détenues par l’entreprise est collectée, vous devez faire deux choses :
- Créer des catégories d’appareils dans Intune
- Cibler l’application Datalert seulement pour les téléphones de l’entreprise

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Définir des catégories d’appareils et des groupes d’appareils mappés à ces catégories

En fonction des besoins de votre organisation, créez au moins deux catégories d’appareils (par exemple, Professionnel et Personnel). Ensuite, créez des groupes d’appareils dynamiques pour chaque catégorie. Si nécessaire, vous pouvez créer des catégories supplémentaires pour votre organisation.

Ces catégories s’affichent aux utilisateurs lors de l’inscription. En fonction de la catégorie choisie par les utilisateurs, l’appareil inscrit est déplacé vers le groupe d’appareils correspondant. Pour connaître les étapes permettant de créer des catégories d’appareils, consultez [Mapper des appareils à des groupes](device-group-mapping.md).

  ![Capture d’écran du volet Ajouter une stratégie](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Créer l’application Datalert dans Intune

Effectuez les étapes suivantes pour créer l’application Datalert dans Intune pour chaque plateforme. iOS est utilisé comme exemple dans ces étapes.

1. Dans le volet **Intune** du [portail Azure](https://portal.azure.com), choisissez **Applications clientes**.

2. Dans le volet **Applications clientes**, choisissez **Gérer** > **Applications**.

3. Sélectionnez **Ajouter** pour ajouter une application.

4. Sélectionnez le type d’application. Par exemple, pour iOS, sélectionnez **Application de l’App Store iOS**.

5. Dans **Rechercher dans l’App Store**, recherchez l’application Datalert en tapant **Datalert** dans la fenêtre de recherche.

6. Sélectionnez l’application **Datalert**, puis **OK**.

   ![Capture d’écran du volet Ajouter une stratégie](./media/tem-select-app-from-apple-app-store.png)

7. Effectuez les étapes restantes pour créer une application pour iOS.

   ![Capture d’écran du volet Ajouter une stratégie](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Affecter l’application Datalert au groupe d’appareils d’entreprise

1. Dans le volet **Applications client - Applications**, sélectionnez l’application Datalert iOS créée à l’étape précédente.

2. Dans le volet **Applications**, choisissez **Gérer** > **Affectations**.

3. Choisissez **Ajouter un groupe**, puis suivez les étapes permettant de sélectionner le groupe d’appareils de l’entreprise.

4. Choisissez de rendre l’installation de l’application obligatoire ou facultative pour le groupe. L’exemple de capture d’écran suivant montre l’installation quand elle est obligatoire, ce qui signifie que les utilisateurs doivent installer l’application Datalert après avoir inscrit leur appareil.

   ![Capture d’écran du volet Ajouter une stratégie](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Étape 4 : Ajouter des lignes téléphoniques payées par l’entreprise à la console Datalert

Vous avez configuré les services Intune et Datalert pour qu’ils communiquent entre eux. Vous devez maintenant ajouter des lignes téléphoniques payées par votre entreprise à la console Datalert, et définir des seuils et actions concernant toutes les violations de l’utilisation de ces lignes par des téléphones portables ou en itinérance. Vous pouvez soit ajouter manuellement des lignes téléphoniques d’entreprise payantes à la console Datalert, soit les ajouter automatiquement une fois l’appareil inscrit dans Intune.

Pour définir ces éléments, accédez à la page relative au [programme d’installation de Datalert pour Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup), puis suivez les étapes de l’Assistant Installation sous l’onglet**Paramètres**.

  ![Capture d’écran du volet Ajouter une stratégie](./media/tem-add-phone-lines-to-datalert-console.png)


Le service Datalert est maintenant actif, et commence à surveiller l’utilisation des données et la désactivation des données cellulaires et d’itinérance sur les appareils qui dépassent les limites d’utilisation configurées.

## <a name="client-enrollment-experience"></a>Expérience d’inscription du client
Pour l’expérience d’inscription du client, consultez les rubriques suivantes :
-   [Inscrire votre appareil iOS pour la gestion des dépenses de télécommunications](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [Inscrire votre appareil Android pour la gestion des dépenses de télécommunications](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Désactivation du service Datalert

Si vous désactivez le service Datalert dans le portail Azure :

- Toutes les actions qui ont été appliquées aux appareils, en raison de violations des limites d’utilisation, sont annulées.
- L’accès aux données et à l’itinérance n’est plus bloqué pour les utilisateurs.
- Intune reçoit toujours les signaux provenant du service, mais les ignore.

**Pour désactiver le service**

1. Dans le volet **Gestion des dépenses de télécommunications** dans le portail Azure, sélectionnez **Désactiver**.

2. Sélectionnez **Enregistrer**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Affichage de rapports d’utilisation de données et d’itinérance

Pour l’instant, le rapport d’utilisation des données est disponible uniquement dans la console de gestion de Datalert de Saaswedo.

Les instructions que vos utilisateurs finaux suivent pour installer l’application Datalert seront bientôt disponibles.
