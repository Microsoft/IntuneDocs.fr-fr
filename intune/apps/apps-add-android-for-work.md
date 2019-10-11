---
title: Affecter des applications gérées Google Play à des appareils d’entreprise Android
titleSuffix: Microsoft Intune
description: Découvrez comment synchroniser et affecter des applications à des appareils d’entreprise Android à partir du store Google Play géré.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbcc777cc6d8b803c502d847114ef7cff04ceb26
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725333"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Ajouter des applications de Google Play géré à des appareils d’entreprise Android avec Intune

Google Play géré est la boutique professionnelle d’applications Google et la seule source d’applications pour Android Entreprise. Vous pouvez utiliser Intune pour orchestrer le déploiement d’applications via Google Play géré pour tout scénario Android Entreprise (y compris les inscriptions de profils professionnels, dédiées et entièrement gérées). La façon dont vous ajoutez des applications de Google Play géré à Intune diffère de la façon dont les applications Android sont ajoutées hors Android Entreprise. Les applications du Store, les applications métier et les applications web sont approuvées ou ajoutées à Google Play géré, puis synchronisées dans Intune afin qu’elles apparaissent dans la liste des applications clientes. Une fois qu’elles apparaissent dans la liste des applications clientes, vous pouvez gérer l’attribution d’une application de Google Play géré comme vous le feriez pour toute autre application.

Pour vous aider à configurer et à utiliser les fonctions de gestion d’applications Android Entreprise, lors de la connexion de votre locataire Intune à Google Play géré, Intune ajoute automatiquement quatre applications liées à cette solution dans la console d’administration Intune. Les quatre applications sont les suivantes :

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : cette application est utilisée pour les scénarios impliquant une instance Android Entreprise entièrement gérée. Cette application est automatiquement installée sur les appareils entièrement gérés pendant le processus d’inscription des appareils.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ce logiciel vous aide à vous connecter à vos comptes lorsque vous utilisez la vérification à deux facteurs. Cette application est automatiquement installée sur les appareils entièrement gérés pendant le processus d’inscription des appareils.
- **[Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : cette application est utilisée pour les scénarios impliquant des stratégies de protection des applications et des profils de travail Android Entreprise.
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** : cette fonctionnalité est utilisée pour les scénarios impliquant des kiosques multi-applications sur une instance Android Entreprise dédiée. Les administrateurs informatiques doivent créer une affectation pour installer cette application sur des appareils dédiés qui seront utilisés dans des scénarios impliquant des kiosques à plusieurs applications.

>[!NOTE]
>Lorsqu’un utilisateur final inscrit son appareil Android Entreprise entièrement géré, l’application du portail d’entreprise Intune est automatiquement installée et l’icône de l’application peut être visible pour l’utilisateur final. Si l’utilisateur final tente de lancer l’application du portail d’entreprise Intune, l’utilisateur final est redirigé vers l’application Microsoft Intune et l’icône de l’application du portail d’entreprise est masquée par la suite.

## <a name="before-you-start"></a>Avant de commencer
- Assurez-vous d’avoir connecté votre client Intune à Google Play géré.  Pour en savoir plus, voir [Connecter votre compte Intune à votre compte professionnel Android](../enrollment/connect-intune-android-enterprise.md).
- Si vous prévoyez de mettre en œuvre des appareils avec profil professionnel, vérifiez que vous avez configuré des profils Intune et des profils professionnels Android pour qu’ils fonctionnent ensemble dans la charge de travail **Inscription de l’appareil** du portail Azure. Pour plus d’informations, consultez [Inscrire des appareils Android](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>Avec Microsoft Intune, nous vous recommandons d’utiliser le navigateur Microsoft Edge ou Google Chrome.

## <a name="managed-google-play-app-types"></a>Types d’application Google Play gérés
Trois types d’applications sont disponibles avec Google Play géré :

* **Application de boutique Google Play gérée** : des applications publiques qui sont généralement disponibles dans le Play Store. Gérez ces applications dans Intune en recherchant les applications que vous souhaitez gérer, en les approuvant, puis en les synchronisant dans Intune.
* **Application de boutique Google Play gérée privée** : il s’agit d’applications métier publiées sur Google Play géré par les administrateurs Intune.  Ces applications sont privées et ne sont disponibles que pour votre locataire Intune. C’est ainsi que les applications métier sont gérées et déployées avec Google Play géré et Android Enterprise.
* **Lien web Google Play géré** : des liens web avec les icônes définies par l’administrateur informatique qui peuvent être déployés sur les appareils Android Entreprise. Ils apparaissent sur les appareils dans la liste des applications de l’appareil, tout comme les applications normales.

## <a name="managed-google-play-store-apps"></a>Applications Google Play Store gérées
Il existe deux façons de parcourir et d’approuver des applications Google Play Store gérées avec Intune :

1. Directement dans la console Intune : Parcourez et approuvez les applications du Store dans une vue hébergée dans Intune. Elle s’ouvre directement dans la console Intune et n’exige pas que vous vous authentifiiez à nouveau avec un autre compte.
1. Dans la console Google Play gérée : vous pouvez éventuellement ouvrir la console Google Play gérée directement et y approuver les applications. Pour plus d’informations, consultez [Synchroniser une application de Google Play géré avec Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).  Pour ce faire, vous devez disposer d’une connexion distincte utilisant le compte que vous avez utilisé pour connecter votre client Intune à Google Play géré.


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Ajouter une application Google Play Store gérée directement dans la console Intune

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications**.
5. Dans le volet **Applications**, sélectionnez **Ajouter**.
6. Dans la liste déroulante **Type d’application**, sélectionnez **Google Play géré**.
7. Sélectionnez **Google Play managé - Ouvrir** pour ouvrir le catalogue Google Play managé.
7. Sélectionnez **Rechercher dans Play Store** dans le catalogue Google Play.
8. Utilisez la zone de recherche pour rechercher des applications que vous souhaitez gérer.
9. Cliquez sur **Approuver** pour approuver l’application Google Play managée, puis sur **Approuver** pour accepter les autorisations de l’application.
10. Sélectionnez **Keep approved when app requests new permissions** (Laisser approuvé quand l’application demande de nouvelles autorisations) dans la fenêtre Paramètres d’autorisation, puis cliquez sur **Enregistrer**. Si vous ne choisissez pas cette option, vous devez approuver manuellement les nouvelles autorisations si le développeur d’applications publie une mise à jour. Les installations et les mises à jour de l’application sont stoppées jusqu'à ce que les autorisations soient approuvées. Pour cette raison, il est recommandé de sélectionner l’option permettant d’approuver automatiquement de nouvelles autorisations. 
11. Cliquez sur **OK** pour inclure la ou les applications approuvées.
12. Cliquez sur **Synchroniser** dans le volet **Application** pour vous synchroniser avec le service Google Play géré.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Ajouter une application Google Play Store gérée dans la console Google Play gérée (alternative)
Si vous préférez synchroniser une application Google Play géré avec Intune, au lieu de l’ajouter directement à l’aide d’Intune, effectuez les étapes ci-après.

> [!IMPORTANT]
> Les informations fournies ci-dessous sont une méthode alternative pour ajouter une application Google Play géré à l’aide d’Intune comme décrit ci-dessus.

1. Accédez au [store Google Play géré](https://play.google.com/work). Connectez-vous avec le compte que vous avez utilisé pour configurer la connexion entre Intune et Android Entreprise.
2. Dans le store, recherchez et sélectionnez l’application à affecter à l’aide d’Intune.
3. Dans la page qui affiche l’application, sélectionnez **Approuver**.  
    Dans l’exemple suivant, l’application Microsoft Excel a été choisie.

    ![Bouton Approuver dans le store Google Play géré](./media/apps-add-android-for-work/approve.png)

   Une fenêtre de l’application s’ouvre, vous demandant d’accorder des autorisations pour que l’application puisse effectuer diverses opérations.

4. Sélectionnez **Approuver** pour accepter les autorisations des applications et continuer.

    ![Bouton Approuver pour les autorisations d’application](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Sélectionnez une option pour gérer les nouvelles demandes d’autorisation d’application, puis sélectionnez **Enregistrer**.

    ![Options de gestion des nouvelles demandes d’autorisation d’application](./media/apps-add-android-for-work/approve-app-settings.png)

    L’application est approuvée et s’affiche dans votre console d’administration informatique. Vous pouvez ensuite [Synchroniser l’application de profil professionnel Android avec Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

## <a name="managed-google-play-private-lob-apps"></a>Applications métier privées Google Play gérées

Il existe deux façons d’ajouter des applications métier à Google Play géré :

1. Directement dans la console Intune : cela vous permet d’ajouter des applications métier en soumettant uniquement l’APK de l’application et un titre directement dans Intune. Cette méthode ne vous oblige pas à avoir un compte développeur Google et ne vous demande pas de payer les frais d’inscription auprès de Google en tant que développeur.  Cette méthode est plus simple et a un nombre d’étapes considérablement réduit, et rend les applications métier disponibles pour la gestion en 10 minutes.
1. Dans la console développeur Google Play : Si vous avez un compte de développeur Google ou si vous souhaitez configurer des fonctionnalités de distribution avancées qui sont uniquement disponibles dans la console développeur Google Play Developer (par exemple l’ajout de captures d’écran d’application supplémentaires), vous pouvez utiliser la [Console développeur Google Play](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Publication d’applications Google Play gérées privées (métier) directement dans la console Intune

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications**.
5. Dans le volet **Applications**, sélectionnez **Ajouter**.
6. Dans la liste déroulante **Type d’application**, sélectionnez **Google Play géré**.
7. Sélectionnez **Google Play managé - Ouvrir** pour ouvrir le catalogue Google Play managé.
7. Sélectionnez **Applications privées** dans le catalogue Google Play.
7. Cliquez sur le bouton **« + »** pour ajouter une nouvelle application
8. Envoyer un titre d’application et un package APK pour l’application
9. Cliquez sur **Créer**
9. Fermez le volet Google Play géré si vous avez fini d’ajouter des applications
12. Cliquez sur **Synchroniser** dans le volet **Application** pour vous synchroniser avec le service Google Play géré. Notez que les applications privées peuvent nécessiter plusieurs minutes pour être synchronisées. Si elle n’apparaît pas la première fois que vous effectuez une synchronisation, patientez quelques minutes et lancez une nouvelle synchronisation.

Pour plus d’informations sur les applications Google Play gérées privées, avec notamment un Forum aux questions, consultez l’article du support technique de Google : https://support.google.com/googleplay/work/answer/9146439

>[!NOTE]
>Les applications privées ajoutées à l’aide de cette méthode ne peuvent jamais être rendues publiques. Utilisez cette option de publication uniquement si vous avec la certitude que cette application sera toujours privée pour votre organisation.
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Publication d’applications Google Play gérées privées (métier) à l’aide de la console développeur Google

1. Connectez-vous à [Google Play Developer Console](https://play.google.com/apps/publish) avec le compte que vous avez utilisé pour configurer la connexion entre Intune et Android Entreprise.  
    Si vous vous connectez pour la première fois, vous devez vous inscrire et payer des frais pour devenir membre du programme de développement Google.
2. Dans la console, sélectionnez **Ajouter une nouvelle application**.
3. Vous chargez votre application et fournissez des informations la concernant de la même manière que vous publiez une application sur le Google Play Store. Toutefois, vous devez sélectionner **Mettre cette application à la disposition de mon organisation uniquement (<*nom de l’organisation*>)** .

    ![Mettre l’application à la disposition de votre organisation uniquement](./media/apps-add-android-for-work/restrict.png)

    Cette opération rend l’application disponible seulement pour votre organisation. Elle ne sera pas disponible sur le store Google Play public.

    Pour plus d’informations sur le chargement et la publication d’applications Android, consultez [l’aide de Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Une fois votre application publiée, connectez-vous au [store Google Play géré](https://play.google.com/work) avec le compte que vous avez utilisé pour configurer la connexion entre Intune et Android Entreprise.
5. Dans le nœud **Applications** du store, vérifiez que l’application que vous avez publiée est affichée.  
    L’application a été automatiquement approuvée pour être synchronisée avec Intune.

## <a name="managed-google-play-web-links"></a>Liens web Google Play gérés

Les liens web Google Play gérés peuvent être installés et gérés comme les autres applications Android. Lorsqu’ils sont installés sur un appareil, ils s’affichent dans la liste des applications de l’utilisateur en même temps que les autres applications qu’ils ont installées. Lorsque les utilisateurs appuient dessus, ils s’ouvrent dans le navigateur de l’appareil.

Les liens web s’ouvrent avec Microsoft Edge ou toute autre application de navigateur que vous choisissez de déployer. Veillez à déployer au moins une application de navigateur sur les appareils afin que les liens web puissent s’ouvrir correctement. Toutefois, toutes les options **Affichage** disponibles pour les liens web (plein écran, autonome et interface utilisateur minimale) ne fonctionnent qu’avec le navigateur Chrome. 

> [!IMPORTANT]
> En date de la publication de ce document, il existe un bogue de Google connu qui empêche les liens web de s’ouvrir sur des appareils avec des navigateurs autres que Chrome. Google s’est engagé à résoudre ce bogue.  Cet avis sera supprimé lorsque Microsoft aura confirmé que Google a publié son correctif.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications**.
5. Dans le volet **Applications**, sélectionnez **Ajouter**.
6. Dans la liste déroulante **Type d’application**, sélectionnez **Google Play géré**.
7. Sélectionnez **Google Play managé - Ouvrir** pour ouvrir le catalogue Google Play managé.
7. Sélectionnez **Applications web** dans le catalogue Google Play.
7. Cliquez sur le bouton **« + »** pour ajouter une nouvelle application
7. Entrez les informations demandées, puis cliquez sur **Créer**
7. Fermez le volet Google Play géré si vous avez fini d’ajouter des applications
12. Cliquez sur **Synchroniser** dans le volet **Application** pour vous synchroniser avec le service Google Play géré. Notez que les applications privées peuvent nécessiter plusieurs minutes pour être synchronisées. Si elle n’apparaît pas la première fois que vous effectuez une synchronisation, patientez quelques minutes et lancez une nouvelle synchronisation.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Synchroniser une application de Google Play géré avec Intune

Si vous avez approuvé une application à partir du Store et qu’elle ne se trouve pas dans la charge de travail **Applications clientes**, forcez une synchronisation immédiate en procédant de la manière suivante :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet de la charge de travail **Applications clientes**, sous **Installation**, sélectionnez **Google Play géré**.
5. Dans le volet **Google Play géré**, choisissez **Actualiser**.  
    La page met à jour l’heure et l’état de la dernière synchronisation.
6. Dans le volet de la charge de travail **Applications clientes**, sélectionnez **Applications**.  
    L’application Google Play géré nouvellement disponible est affichée.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Affectation d’applications Google Play gérées supplémentaires à des appareils avec profil professionnel Android Entreprise

Quand l’application s’affiche dans le nœud **Applications sous licence** du volet de la charge de travail **Applications clientes**, vous pouvez [l’assigner comme toute autre application](/intune-azure/manage-apps/deploy-apps) en l’assignant à des groupes d’utilisateurs.

Une fois l’application affectée, elle est installée (ou disponible pour installation) sur les appareils des utilisateurs que vous avez ciblés. L’utilisateur de l’appareil n’est pas invité à approuver l’installation. Pour plus d’informations sur les appareils de profil professionnel Android Entreprise, consultez [Configurer l’inscription d’appareils de profil professionnel Android Entreprise](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Seules les applications qui ont été affectées s’affichent dans la boutique Google Play gérée pour l’utilisateur final. Par conséquent, il s’agit d’une étape clé que l’administrateur doit effectuer lors de la configuration des applications avec Google Play géré.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Affectation d’applications Google Play gérées supplémentaires à des appareils entièrement gérés Android Entreprise

Les [appareils Android Entreprise entièrement gérés](../enrollment/android-fully-managed-enroll.md) sont des appareils de l’entreprise associés à un seul utilisateur et utilisés exclusivement à des fins professionnelles. Les utilisateurs sur des appareils entièrement gérés peuvent accéder à leurs applications d’entreprise disponibles à partir de l’application Google Play gérée sur leur appareil.

Par défaut, un appareil Android Entreprise entièrement géré ne permet pas aux employés d’installer des applications qui ne sont pas approuvées par l’organisation. En outre, les employés ne seront pas en mesure de supprimer les applications installées contre la stratégie. Si vous souhaitez autoriser les utilisateurs à accéder à la boutique Google Play complète pour installer des applications au lieu d’avoir uniquement accès aux applications approuvées dans la boutique Google Play gérée, vous pouvez définir **Autoriser l’accès à toutes les applications dans la boutique Google Play** sur **Autoriser**. Avec ce paramètre, l’utilisateur peut accéder à toutes les applications dans la boutique Google Play à l’aide de son compte d’entreprise, mais les achats peuvent être limités. Vous pouvez supprimer la restriction des achats en permettant aux utilisateurs d’ajouter de nouveaux comptes à l’appareil. Cela permettra aux utilisateurs finaux d’acheter des applications à partir de la boutique Google Play à l’aide de comptes personnels, ainsi que d’effectuer des achats dans l’application. Pour plus d’informations, consultez [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> L’application Microsoft Intune et l’application Microsoft Authenticator seront installées en tant qu’applications requises sur tous les appareils entièrement gérés pendant l’intégration. Si ces applications sont installées automatiquement, une prise en charge de l’accès conditionnel est fournie et les utilisateurs de l’application Microsoft Intune peuvent voir et résoudre les problèmes de conformité. 

## <a name="manage-android-enterprise-app-permissions"></a>Gérer les autorisations des applications Android Entreprise
Android Entreprise nécessite l’approbation des applications dans la console web Google Play gérée avant qu’il soit possible de les synchroniser avec Intune et de les affecter à vos utilisateurs. Comme Android Entreprise vous permet d’envoyer (push) les applications automatiquement et en mode silencieux aux appareils des utilisateurs, vous devez accepter les autorisations des applications pour le compte de tous vos utilisateurs. Les utilisateurs ne voient aucune des autorisations des applications au moment de leur installation : il est donc important que vous compreniez les autorisations.

Quand un développeur d’applications met à jour des autorisations avec une nouvelle version de l’application, les autorisations ne sont pas acceptées automatiquement, même si vous avez approuvé les autorisations précédentes. Les appareils qui exécutent la version précédente de l’application peuvent continuer à l’utiliser. Toutefois, l’application n’est pas mise à niveau tant que les nouvelles autorisations ne sont pas approuvées. Les appareils sur lesquels l’application n’est pas installée ne procèdent pas à son installation jusqu’à ce que vous en approuviez les nouvelles autorisations. 

### <a name="update-app-permissions"></a>Mettre à jour les autorisations d’application

Consultez régulièrement la console Google Play gérée pour y rechercher l’existence de nouvelles autorisations. Vous pouvez configurer Google Play pour vous envoyer à vous-même ou à d’autres un e-mail quand de nouvelles autorisations sont exigées pour une application approuvée. Si vous affectez une application et que vous constatez qu’elle n’est pas installée sur les appareils, recherchez les nouvelles autorisations en effectuant ces étapes :

1. Accédez à [Google Play](https://play.google.com/work).
2. Connectez-vous avec le compte Google que vous avez utilisé pour publier et approuver les applications.
3. Sélectionnez l’onglet **Mises à jour** et vérifiez si toutes les applications nécessitent une mise à jour.  
    Les applications répertoriées nécessitent de nouvelles autorisations et ne sont pas affectées avant l’application de ces autorisations.

Vous pouvez également configurer Google Play pour réapprouver automatiquement les autorisations d’application en fonction de l’application.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Création de rapports d’applications Google Play gérées supplémentaires pour les appareils avec profil professionnel Android Entreprise

Pour les applications Google Play gérées qui sont déployées sur des appareils avec profil professionnel Android Entreprise, vous pouvez afficher le numéro de version spécifique de l’application installée sur un appareil. Cela concerne uniquement les applications obligatoires. 


## <a name="delete-managed-google-play-apps"></a>Supprimer des applications Google Play géré
Si besoin, vous pouvez supprimer des applications Google Play géré à partir de Microsoft Intune. Pour supprimer une application Google Play géré, ouvrez Microsoft Intune dans le portail Azure et sélectionnez **Applications clientes** > **Applications**. À partir de la liste des applications, sélectionnez les points de suspension (...) à droite de l’application Google Play géré, puis sélectionnez **Supprimer** dans la liste affichée. Lorsque vous supprimez une application Google Play gérée à partir de la liste des applications, l’application Google Play gérée devient automatiquement non approuvée.

## <a name="android-enterprise-system-apps"></a>Applications système Android Entreprise

Vous pouvez activer une application système Android Entreprise pour les [appareils Android Entreprise dédiés](../enrollment/android-kiosk-enroll.md) ou les [appareils entièrement gérés](../enrollment/android-fully-managed-enroll.md). Pour plus d’informations sur l’ajout d’une application système Android Entreprise, consultez [Ajouter des applications système Android à Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)
