---
title: "Inscrire des appareils d’entreprise avec le gestionnaire d’inscription d’appareil | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.sourcegitcommit: 7b0154d73ab540e7543fab9088463ed8b61b45a0
ms.openlocfilehash: 74ff3209d00dee0b5ddd14e107b5544b364d08f7


---


# Inscrire des appareils d'entreprise avec le Gestionnaire d'inscription d'appareil dans Microsoft Intune
Les organisations peuvent utiliser Intune pour gérer un grand nombre d'appareils mobiles avec un seul compte d'utilisateur. Le compte du *gestionnaire d’inscription d’appareil* (DEM) est un compte Intune spécial autorisé à inscrire jusqu’à 1 000 appareils. Utilisez des appareils inscrits à l’aide du compte du gestionnaire d’inscription d’appareil en tant qu’appareil partagés plutôt qu’en tant qu’appareils personnels (« BYOD »). Les utilisateurs ne pourront pas utiliser des applications de messagerie « natives », par exemple. Vous pouvez affecter à un directeur ou responsable de magasin, par exemple, un compte de gestionnaire d'inscription d'appareil pour lui permettre d'effectuer les opérations suivantes :

-   Inscrire des appareils dans Intune

-   Se connecter au portail d'entreprise pour obtenir des applications d'entreprise

-   Installer et désinstaller des logiciels

-   Configurer l'accès aux données de l'entreprise


**Exemples de scénarios faisant intervenir un gestionnaire d’inscription d’appareil :** Un restaurant souhaite que son personnel de service utilise des tablettes et son personnel de cuisine des moniteurs de commande. Les employés n'ont jamais besoin d'accéder aux données de l'entreprise ni d'ouvrir de session en tant qu'utilisateur. L'administrateur Intune crée un compte de gestionnaire d'inscription d'appareil et inscrit les appareils d'entreprise à l'aide de ce compte. L'administrateur pourrait également donner les informations d'identification du gestionnaire d'inscription d'appareil au directeur du restaurant, puis lui permettre d'inscrire et de gérer les appareils.

L'administrateur ou le directeur peuvent déployer des applications propres aux rôles sur les appareils du restaurant. Un administrateur peut également sélectionner un appareil dans la console Intune et le retirer de la gestion des appareils mobiles avec la console d'administration.

Les appareils inscrits avec un compte de gestionnaire d’inscription d’appareil ont les restrictions suivantes :
  - Aucun utilisateur spécifique, si bien que tous les appareils sont « sans utilisateur ». Par conséquent, pas d’accès aux e-mails ni aux données d’entreprise, même si un VPN, par exemple, pourrait fournir aux applications pour appareil un accès aux données
  - Aucun accès conditionnel car il s’agit de scénarios par utilisateur
  - Impossible de réinitialiser les appareils à partir du Portail d’entreprise
  - Seul l’appareil local s’affiche dans l’application Portail d’entreprise ou le site web
  - Aucune application du programme VPP (Volume Purchase Program) d’Apple en raison des exigences d’ID Apple par utilisateur pour la gestion des applications
  - Ils ne peuvent pas également être inscrits avec Apple Configurator ni le programme d’inscription d’appareils Apple (appareils iOS)

> [!NOTE]
> Pour déployer des applications d’entreprise sur des appareils gérés avec le gestionnaire d’inscription d’appareil, déployez l’application Portail d’entreprise en tant qu’**Installation requise** sur le compte d’utilisateur du gestionnaire d’inscription d’appareil.
> Pour améliorer les performances, l’affichage de l’application Portail d’entreprise sur un appareil DEM affiche uniquement les appareils locaux. La gestion à distance d’autres appareils DEM est possible uniquement à partir de la console d’administration Intune.

## Créer des comptes de gestionnaire d’inscription d’appareil
Les comptes de gestionnaire d'inscription d'appareil sont des comptes d'utilisateur autorisés à inscrire un grand nombre d'appareils d'entreprise. Seuls les utilisateurs existants dans la console Intune peuvent être gestionnaires d'inscription d'appareil.

#### Ajouter un gestionnaire d'inscription d'appareil à Intune

1.  Accédez au [portail du compte Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) et connectez-vous à l’aide de votre compte d’administrateur.

2.  Choisissez **Ajouter un utilisateur**.

3.  Vérifiez que le compte d'utilisateur qui sera gestionnaire d'inscription d'appareil est répertorié. Si ce n’est pas le cas, ajoutez l’utilisateur en choisissant **Nouveau** , puis en procédant à l’ajout de l’utilisateur. Une licence d'abonnement est nécessaire pour chaque utilisateur qui accède au service. Par ailleurs, le *gestionnaire d'inscription d'appareil* ne peut pas être un administrateur Intune. Déterminez si vous devez ajouter des licences supplémentaires avant d'utiliser cette fonctionnalité.

4.  Connectez-vous à la [console d'administration Microsoft Intune](http://manage.microsoft.com) avec vos informations d'identification d'administrateur.

5.  Dans le volet de navigation, choisissez **Admin**, puis accédez à **Gestion des administrateurs** et sélectionnez **Gestionnaires d’inscription d’appareil**. La page Gestionnaires d'inscription d'appareil s'ouvre.

6.  Choisissez **Ajouter...** La boîte de dialogue **Ajouter un gestionnaire d'inscription d'appareil** s'ouvre.

7.  Entrez l’**ID d’utilisateur** du compte Intune, puis choisissez **OK**. Le gestionnaire d'inscription d'appareil ne peut pas être administrateur Intune.

8.  À présent, le gestionnaire d'inscription d'appareil peut inscrire des appareils mobiles en suivant la même procédure qu'un utilisateur final pour un scénario BYOD dans le portail d'entreprise.

## Supprimer un gestionnaire d'inscription d'appareil d'Intune

1.  Connectez-vous au [portail de compte Microsoft Intune](http://manage.microsoft.com) avec votre connexion d’administrateur.

2.  Dans le volet de navigation, choisissez **Admin**, puis accédez à **Gestion des administrateurs** et sélectionnez **Gestionnaires d’inscription d’appareil**. La page Gestionnaires d'inscription d'appareil s'ouvre.

3.  Sélectionnez l’**Utilisateur** du gestionnaire d’inscription d’appareil à supprimer, puis choisissez **Supprimer**. Cet utilisateur ne sera pas supprimé d'Intune et les appareils qu'il gère resteront inscrits dans Intune. La suppression d'un gestionnaire d'inscription d'appareil empêche l'utilisateur correspondant d'inscrire plusieurs appareils dans Intune.

4.  Choisissez **Oui** pour confirmer la suppression du gestionnaire d’inscription d’appareil.

La suppression d'un gestionnaire d'inscription d'appareil n'affecte pas les appareils inscrits. Quand un gestionnaire d'inscription d'appareil est supprimé :

-   aucun appareil inscrit n'est affecté ;

-   les appareils inscrits continuent à être entièrement gérés ;

-   les informations d'identification de compte du gestionnaire d'inscription d'appareil supprimé restent valides et vous permettent de vous connecter au portail d'entreprise pour accéder aux applications ;

-   la suppression du gestionnaire d'inscription d'appareil n'entraîne pas la réinitialisation ou la mise hors service des appareils ;

-   il existe toujours une relation entre le compte du gestionnaire d'inscription d'appareil supprimé et les appareils inscrits, mais aucun appareil supplémentaire ne peut être inscrit.


<!--HONumber=Jul16_HO2-->


