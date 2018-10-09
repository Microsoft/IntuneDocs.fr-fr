---
title: Affecter des applications à des appareils avec profil professionnel Android
titlesuffix: Microsoft Intune
description: Découvrez comment synchroniser et affecter des applications à des appareils avec profil professionnel Android à partir du store Google Play géré.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0cfb3dab58676b12b0227f381e9fd7c51e956895
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799555"
---
# <a name="assign-apps-to-android-work-profile-devices-with-intune"></a>Affecter des applications à des appareils avec profil professionnel Android en utilisant Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android Entreprise est un programme pour les appareils avec profil professionnel Android et les appareils en mode kiosque. Pour les appareils avec profil professionnel Android, Android Entreprise est un ensemble de fonctionnalités et de services qui séparent les applications et les données personnelles des applications et des données professionnelles. Android Entreprise offre des options de gestion et une confidentialité supplémentaires quand les personnes utilisent leurs appareils Android à titre professionnel. Intune vous permet de déployer des applications et des paramètres sur des appareils avec profil professionnel Android de manière à ce que les informations professionnelles soient séparées des informations personnelles. Toutes les applications que vous installez sur des appareils avec profil professionnel Android proviennent du store Google Play géré. La façon dont vous affectez des applications à des appareils avec profil professionnel Android diffère de celle dont vous les affectez à des appareils Android standard. Vous vous connectez au store, recherchez les applications souhaitées et les approuvez. L’application apparaît ensuite dans le nœud **Applications sous licence** du portail Azure, et vous pouvez gérer l’affectation de l’application de la même façon que pour toute autre application.

En outre, si vous avez créé vos propres applications métier, vous pouvez les affecter comme suit :
- Inscrivez-vous à un compte de développeur Google qui vous permet de publier des applications dans une zone privée dans Google Play.
- Synchronisez les applications avec Intune.

## <a name="before-you-start"></a>Avant de commencer

Vérifiez que vous avez configuré des profils Intune et des profils professionnels Android pour qu’ils fonctionnent ensemble dans la charge de travail **Inscription de l’appareil** du portail Azure. Pour plus d’informations, consultez [Inscrire des appareils Android](android-work-profile-enroll.md).

## <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Synchroniser une application à partir du store Google Play géré

1. Accédez au [store Google Play géré](https://play.google.com/work). Connectez-vous avec le compte que vous avez utilisé pour configurer la connexion entre Intune et Android Entreprise.
2. Dans le store, recherchez et sélectionnez l’application à affecter à l’aide d’Intune.
3. Dans la page qui affiche l’application, sélectionnez **Approuver**.  
    Dans l’exemple suivant, l’application Microsoft Excel a été choisie.

    ![Bouton Approuver dans le store Google Play géré](media/approve.png)
    
   Une fenêtre de l’application s’ouvre, vous demandant d’accorder des autorisations pour que l’application puisse effectuer diverses opérations. 

4. Sélectionnez **Approuver** pour accepter les autorisations des applications et continuer.

    ![Bouton Approuver pour les autorisations d’application](media/approve-app-permissions.png)

5. Sélectionnez une option pour gérer les nouvelles demandes d’autorisation d’application, puis sélectionnez **Enregistrer**.

    ![Options de gestion des nouvelles demandes d’autorisation d’application](media/approve-app-settings.png)

    L’application est approuvée et s’affiche dans votre console d’administration informatique. Vous pouvez ensuite [synchroniser l’application de profil professionnel Android avec Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-a-managed-google-play-app-with-intune"></a>Synchroniser une application de Google Play géré avec Intune

Si vous avez approuvé une application à partir du Store et qu’elle ne se trouve pas dans le nœud **Applications sous licence** de la charge de travail **Applications clientes**, forcez une synchronisation immédiate en procédant de la manière suivante :

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet de la charge de travail **Applications clientes**, sous **Installation**, sélectionnez **Google Play géré**.
5. Dans le volet **Google Play géré**, choisissez **Actualiser**.  
    La page met à jour l’heure et l’état de la dernière synchronisation.
6. Dans le volet de la charge de travail **Applications clientes**, sélectionnez **Applications**.  
    L’application Google Play géré nouvellement disponible est affichée.

Quand l’application s’affiche dans le nœud **Applications sous licence** du volet de la charge de travail **Applications clientes**, vous pouvez [l’affecter comme toute autre application](/intune-azure/manage-apps/deploy-apps). Vous pouvez affecter l’application sur des groupes d’utilisateurs uniquement.

Une fois l’application affectée, elle est installée sur les appareils que vous avez ciblés. L’utilisateur de l’appareil n’est pas invité à approuver l’installation.

## <a name="manage-android-enterprise-app-permissions"></a>Gérer les autorisations des applications Android Entreprise
Android Entreprise nécessite l’approbation des applications dans la console web Google Play gérée avant qu’il soit possible de les synchroniser avec Intune et de les affecter à vos utilisateurs. Comme Android Entreprise vous permet d’envoyer (push) les applications automatiquement et en mode silencieux aux appareils des utilisateurs, vous devez accepter les autorisations des applications pour le compte de tous vos utilisateurs. Les utilisateurs ne voient aucune des autorisations des applications au moment de leur installation : il est donc important que vous compreniez les autorisations.

Quand un développeur d’applications met à jour des autorisations avec une nouvelle version de l’application, les autorisations ne sont pas acceptées automatiquement, même si vous avez approuvé les autorisations précédentes. Les appareils qui exécutent la version précédente de l’application peuvent continuer à l’utiliser. Toutefois, l’application n’est pas mise à niveau tant que les nouvelles autorisations ne sont pas approuvées. Les appareils sur lesquels l’application n’est pas installée ne procèdent pas à son installation jusqu’à ce que vous en approuviez les nouvelles autorisations.

### <a name="update-app-permissions"></a>Mettre à jour les autorisations d’application

Consultez régulièrement la console Google Play gérée pour y rechercher l’existence de nouvelles autorisations. Vous pouvez configurer Google Play pour vous envoyer à vous-même ou à d’autres un e-mail quand de nouvelles autorisations sont exigées pour une application approuvée. Si vous affectez une application et que vous constatez qu’elle n’est pas installée sur les appareils, recherchez les nouvelles autorisations en effectuant ces étapes :

1. Accédez à [Google Play](http://play.google.com/work).
2. Connectez-vous avec le compte Google que vous avez utilisé pour publier et approuver les applications.
3. Sélectionnez l’onglet **Mises à jour** et vérifiez si toutes les applications nécessitent une mise à jour.  
    Les applications répertoriées nécessitent de nouvelles autorisations et ne sont pas affectées avant l’application de ces autorisations.

Vous pouvez également configurer Google Play pour réapprouver automatiquement les autorisations d’application en fonction de l’application. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Utilisation d’une application métier provenant du store Google Play géré

1. Connectez-vous à [Google Play Developer Console](https://play.google.com/apps/publish) avec le compte que vous avez utilisé pour configurer la connexion entre Intune et Android Entreprise.  
    Si vous vous connectez pour la première fois, vous devez vous inscrire et payer des frais pour devenir membre du programme de développement Google.
2. Dans la console, sélectionnez **Ajouter une nouvelle application**.
3. Vous chargez votre application et fournissez des informations la concernant de la même manière que vous publiez une application sur le Google Play Store. Toutefois, vous devez sélectionner **Mettre cette application à la disposition de mon organisation uniquement (<*nom de l’organisation*>)**.

    ![Mettre l’application à la disposition de votre organisation uniquement](media/restrict.png)

    Cette opération rend l’application disponible seulement pour votre organisation. Elle ne sera pas disponible sur le store Google Play public.

    Pour plus d’informations sur le chargement et la publication d’applications Android, consultez [l’aide de Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Une fois votre application publiée, connectez-vous au [store Google Play géré](https://play.google.com/work) avec le compte que vous avez utilisé pour configurer la connexion entre Intune et Android Entreprise.
5. Dans le nœud **Applications** du store, vérifiez que l’application que vous avez publiée est affichée.  
    L’application a été automatiquement approuvée pour être synchronisée avec Intune.

## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md) 

