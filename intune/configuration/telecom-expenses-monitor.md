---
title: Configurer un service de gestion des dépenses de télécommunications dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Intégrez Microsoft Intune au service de gestion des dépenses en télécommunications Saaswedo pour surveiller l’utilisation des données et définir des seuils ou des limites sur les appareils Android et iOS.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce9a6916cc77714a87aeac33555c0be1e59463f5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506625"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurer un service de gestion des dépenses en télécommunications dans Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Avec Intune, vous pouvez gérer les dépenses de télécommunications à partir de l’utilisation des données sur les appareils mobiles appartenant à l’organisation. Intune s’intègre à la [gestion des dépenses en télécommunications Datalert](http://datalert.biz/get-started) de Saaswedo. Datalert est une solution de gestion des dépenses de télécommunications en temps réel qui gère l’utilisation des données de télécommunications. Il peut vous aider à éviter les surcoûts de données et d’itinérance sur vos appareils gérés par Intune.

L’intégration avec Datalert permet de définir, surveiller et appliquer de façon centralisée des limites d’utilisation de données d’itinérance et locales. Lorsque les limites dépassent les seuils définis, des alertes sont déclenchées automatiquement. Vous pouvez également configurer le service pour appliquer différentes actions (comme la désactivation de l’itinérance en cas de dépassement de seuil) à des individus ou à des groupes d’utilisateurs finaux. La console de gestion Datalert comprend des rapports qui affichent des informations sur l’utilisation et la surveillance des données.

L’image suivante montre comment Intune s’intègre à Datalert :

  ![Diagramme de l’intégration d’Intune et de Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Pour utiliser le service Datalert avec Intune, il existe des paramètres de configuration dans Datalert et Intune. Cet article vous montre comment :

- Configurez les paramètres dans la console Datalert pour connecter le service Datalert à Intune.
- Vérifiez que cette connexion est active et activée dans Intune.
- Utilisez Intune pour ajouter l’application Datalert à vos appareils.
- Désactivez le service Datalert et pour Intune (facultatif).

## <a name="supported-platforms"></a>Plateformes prises en charge

- Appareils Android 4.4 et plus récents compatibles Knox (Samsung)

  La page [Versions d’Android prenant en charge Knox](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (ouvre le site web de Samsung) répertorie les versions compatibles Knox.

- iOS 8.0 et versions ultérieures

## <a name="prerequisites"></a>Prérequis

- Un abonnement à Microsoft Intune et un accès au [portail Azure](https://portal.azure.com)
- Un abonnement à [Datalert](http://www.datalert.biz/) (ouvre le site web de Datalert)

## <a name="telecom-expense-management-providers"></a>Fournisseurs de gestion des dépenses en télécommunications

Intune s’intègre avec le fournisseur de gestion de frais de télécommunications suivant :

- [Service de gestion des dépenses en télécommunications Saaswedo Datalert](http://www.datalert.biz/) (ouvre le site web de Datalert)

## <a name="deploy-the-intune-and-datalert-solution"></a>Déployer la solution Intune et Datalert

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Étape 1 : Connecter le service Datalert à Intune

1. Connectez-vous à la console de gestion Datalert avec vos informations d’identification d’administrateur.

2. Dans la console, accédez à l’onglet **Paramètres** > **Configuration MDM**.

3. Sélectionnez **Débloquer**. **Débloquer** vous permet de modifier ou de mettre à jour les paramètres de la page.

4. Dans **Connexion Intune/Datalert** > **Serveur MDM**, sélectionnez **Microsoft Intune**.

5. Pour **Azure AD domain** (Domaine Azure AD), entrez votre ID de locataire Azure. Sélectionnez **Connexion**.

    Lorsque vous sélectionnez **Connexion**, le service Datalert s’intègre à Intune. Il confirme qu’il n’y a aucune connexion Datalert existante. Après quelques instants, une page de connexion de Microsoft s’affiche, suivie de l’authentification Datalert Azure.

6. Sur la page d’authentification Microsoft, sélectionnez **Accepter**.

    Vous êtes redirigé vers une page de **remerciement** de Datalert, qui se ferme après quelques instants. Datalert valide la connexion et affiche des coches vertes en regard d’une liste d’éléments validés. Si la validation échoue, vous verrez un message en rouge. Contactez le support Datalert pour de l’aide.

    L’illustration suivante montre les coches vertes lorsque la connexion est établie :

      ![Page Datalert présentant une connexion établie](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. Dans **Datalert App / ADAL Consent** (Application Datalert/Consentement ADAL), définissez le commutateur sur **On** (Activé). Sur la page d’authentification Microsoft, sélectionnez **Accepter**.

    Vous êtes redirigé vers une page de **remerciement** de Datalert, qui se ferme après quelques instants. Datalert valide la connexion et affiche des coches vertes en regard d’une liste d’éléments validés. Si la validation échoue, vous verrez un message en rouge. Contactez le support Datalert pour de l’aide.

    L’illustration suivante montre les coches vertes lorsque la connexion est établie :

      ![Page Datalert présentant une connexion établie](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. Dans la **MDM Profiles management (optional)** (gestion des profils MDM (facultatif)), définissez le commutateur sur **On** (Activé). Ce paramètre permet à Datalert de lire les profils disponibles dans Intune pour vous aider à configurer des stratégies. 

    Sur la page d’authentification Microsoft, sélectionnez **Accepter**.

    Vous êtes redirigé vers une page de **remerciement** de Datalert, qui se ferme après quelques instants. Datalert valide la connexion et affiche des coches vertes en regard d’une liste d’éléments validés. Si la validation échoue, vous verrez un message en rouge. Contactez le support Datalert pour de l’aide.

    L’illustration suivante montre les coches vertes lorsque la connexion est établie :

   ![Page Datalert présentant une connexion établie](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Étape 2 : Confirmer que la gestion des dépenses en télécommunications est active dans Intune

Une fois l’étape 1 terminée, votre connexion est automatiquement activée. Dans Intune, l’état de la connexion affiche **Active**. Pour confirmer que l’État est actif, procédez comme suit :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Sélectionnez **Configuration de l’appareil** > **Gestion des dépenses en télécommunications**. Recherchez l’état de connexion **Active** :

   ![Page Intune affichant l’état de connexion Actif de Datalert](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Étape 3 : Déployer l’application Datalert sur des appareils

Pour vérifier que seules les données d’utilisation de lignes appartenant à l’organisation sont collectées, veillez à :

- Créer des catégories d’appareils dans Intune.
- Cibler l’application Datalert uniquement pour les téléphones de l’organisation.

Cette section décrit ces étapes.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Créer des catégories d’appareils et des groupes d’appareils mappés à vos catégories

En fonction des besoins de votre organisation, créez au moins deux catégories d’appareils, par exemple, Professionnel et Personnel. Ensuite, créez des groupes d’appareils dynamiques pour chaque catégorie. Si nécessaire, vous pouvez créer des catégories supplémentaires pour votre organisation.

Pour créer des catégories d’appareils dans Intune, consultez [Mapper des appareils à des groupes](../enrollment/device-group-mapping.md).

Ces catégories sont présentées aux utilisateurs lors de l’inscription ([inscrire des appareils Android](../enrollment/android-enroll.md)). En fonction de la catégorie choisie par les utilisateurs, l’appareil inscrit est déplacé vers le groupe d’appareils correspondant.

  ![Capture d’écran du volet Ajouter une stratégie](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Ajouter l’application Datalert à Intune

Les étapes suivantes ajoutent l’application Datalert. Pour cet exemple, iOS est utilisé. [Ajouter des applications](../apps/apps-add.md) et [Utiliser des balises d’étendue](../fundamentals/scope-tags.md) contiennent des informations plus spécifiques sur ces étapes.

1. Dans **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** , sélectionnez **Applications clientes** > **Applications** > **Ajouter**.

2. Sélectionnez votre **Type d’application**. Par exemple, pour iOS, sélectionnez **Application Store - iOS**.

3. Dans **Rechercher dans l’App Store**, saisissez **Datalert** pour rechercher l’application Datalert.

4. Choisissez l’application **Datalert** > **Sélectionner**  :

   ![Ajouter l’application Datalert à partir de l’App Store aux applications clientes Intune](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Entrez les éventuelles propriétés supplémentaires, comme des informations sur l’application et les balises d’étendue :

   ![Entrez les propriétés de l’application, y compris son nom, sa description, le système d’exploitation et d’autres paramètres de l’application dans Intune](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Cliquez sur **OK** > **Ajouter** pour enregistrer vos modifications. L’application Datalert s’affiche dans la liste.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Affecter l’application Datalert au groupe d’appareils d’entreprise

1. Dans **Applications clientes - Applications**, sélectionnez l’application Datalert que vous avez ajoutée à l’étape précédente.

2. Sélectionnez **Attributions** > **Ajouter un groupe**. Choisissez la façon dont l’application est affectée. [Affecter des applications à des groupes dans Intune](../apps/apps-deploy.md) contient plus de détails sur ces paramètres.

    Lors de ces étapes, vous choisissez de rendre l’installation de l’application obligatoire ou facultative pour le groupe. L’exemple suivant illustre l’installation si nécessaire. Quand cela est nécessaire, les utilisateurs doivent installer l’application Datalert après l’inscription de leur appareil.

   ![Capture d’écran du volet Ajouter une stratégie](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Étape 4 : Ajouter des lignes téléphoniques de l’organisation à la console Datalert

Les services Intune et Datalert sont maintenant configurés pour communiquer entre eux. Ensuite, ajoutez les lignes téléphoniques payantes de votre organisation à la console Datalert. Puis entrez les seuils et les actions pour toute violation de l’utilisation des données cellulaires ou de l’itinérance. Vous pouvez soit ajouter manuellement des lignes téléphoniques d’entreprise payantes à la console Datalert, soit les ajouter automatiquement une fois l’appareil inscrit dans Intune.

Pour définir ces éléments, accédez à [Configuration de Datalert pour Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (ouvre le site web de Datalert). Sous l’onglet **Paramètres**, suivez les étapes de l’assistant de configuration.

  ![Capture d’écran du volet Ajouter une stratégie](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Le service Datalert est maintenant actif. Il commence à surveiller l’utilisation des données et la désactivation des données cellulaires et d’itinérance sur les appareils qui dépassent les limites d’utilisation configurées.

## <a name="end-user-enrollment"></a>Inscription des utilisateurs finaux

Pour l’expérience utilisateur final, les articles suivants peuvent vous aider :

- [Inscrire votre appareil iOS pour la gestion des dépenses de télécommunications](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Inscrire votre appareil Android pour la gestion des dépenses de télécommunications](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Désactivation du service Datalert

1. Dans **[Intune](https://go.microsoft.com/fwlink/?linkid=2090973)** , sélectionnez **Configuration de l’appareil** > **Gestion des dépenses en télécommunications**.
2. Définissez **Activer la gestion des dépenses en télécommunications et bloquer les données cellulaires ou itinérantes sur les appareils qui dépassent les quotas d’utilisation que vous configurez** sur **Désactiver**.
3. **Enregistrez** les changements apportés.

> [!IMPORTANT]
> Si vous désactivez le service Datalert dans Intune :
>
> - Toutes les actions qui sont appliquées aux appareils, en raison de violations des limites d’utilisation, sont annulées.
> - L’accès aux données et à l’itinérance n’est plus bloqué pour les utilisateurs.
> - Intune reçoit toujours les signaux provenant du service, mais Intune ignore les signaux.

## <a name="next-steps"></a>Étapes suivantes

Le rapport d’utilisation des données est disponible dans la console de gestion de Datalert de Saaswedo.
