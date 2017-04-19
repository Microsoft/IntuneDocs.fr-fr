---
title: "Gérer les applications achetées en volume"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : Découvrez comment synchroniser les applications que vous avez achetées en volume à partir de l’App Store iOS dans Intune et ensuite gérer et suivre leur utilisation."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: 3b0a674fadf30c660ff3e8e8db172a590f07c8be
ms.lasthandoff: 04/06/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Guide pratique pour gérer les applications iOS que vous avez achetées par le biais d’un programme d’achat en volume avec Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

L’App Store iOS vous permet d’acheter plusieurs licences pour une application que vous souhaitez exécuter dans votre entreprise. Vous pouvez ainsi réduire les coûts d’administration liés au suivi de plusieurs copies d’application achetées.

Microsoft Intune vous aide à gérer les applications que vous avez achetées par le biais de ce programme, en important les informations de licence à partir du magasin d’applications, en effectuant le suivi du nombre de licences que vous avez utilisées, et en vous empêchant d’installer un nombre de copies de l’application supérieur au nombre dont vous êtes propriétaire.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gérer les applications pour appareils iOS achetées en volume
Vous achetez plusieurs licences pour des applications iOS via le [Programme d’achat en volume Apple pour les entreprises](http://www.apple.com/business/vpp/) ou [Programme d’achat en volume Apple pour les organismes éducatifs](http://volume.itunes.apple.com/us/store). Cela implique la configuration d’un compte Apple VPP à partir du site web Apple et l’importation du jeton Apple VPP dans Intune.  Vous pouvez ensuite synchroniser vos informations d’achat en volume avec Intune et suivre votre utilisation des applications achetées en volume.

## <a name="before-you-start"></a>Avant de commencer
Avant de commencer, vous devez obtenir un jeton VPP auprès d’Apple et l’importer dans votre compte Intune. En outre, vous devez comprendre ce qui suit :

* Vous pouvez associer plusieurs jetons de programme d’achat de volume à votre compte Intune.
* Si vous avez déjà utilisé un jeton VPP avec un autre produit, vous devez en générer un nouveau à utiliser avec Intune.
* Chaque jeton est valide pendant un an.
* Par défaut, Intune se synchronise avec le service Apple VPP deux fois par jour. Vous pouvez lancer une synchronisation manuelle à tout moment.
* Après avoir importé le jeton VPP dans Intune, n’importez pas le même jeton dans une autre solution de gestion d’appareils, car cela peut entraîner la perte des enregistrements utilisateur et de l’attribution de licence.
* Avant de commencer à utiliser iOS VPP avec Intune, supprimez les comptes d’utilisateur VPP existants créés avec d’autres fournisseurs de gestion des appareils mobiles. En guise de mesure de sécurité, Intune ne synchronise pas ces comptes d’utilisateur dans Intune. Intune synchronise uniquement les données du service Apple VPP qui ont été créées par Intune.
* Vous ne pouvez pas attribuer d’applications VPP iOS à des appareils qui ont été inscrits à l’aide du protocole d’inscription d’appareils (DEP).

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Pour obtenir et charger un jeton Apple VPP

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de services** > **Autres** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Gérer les applications**.
1.  Dans la charge de travail **Gérer les applications**, choisissez **Installation** > **jetons VPP iOS**.
2.  Dans la liste du panneau des jetons VPP, cliquez sur **Ajouter**.
3.  Dans le volet Nouveau jeton VPP, spécifiez les informations suivantes :
    - **Fichier de jeton VPP** : si vous ne l’avez pas encore fait, inscrivez-vous pour le Programme d’achat en volume Apple pour les entreprises ou Programme d’achat en volume Apple pour les organismes éducatifs. Après inscription, téléchargez le jeton VPP Apple de votre compte et sélectionnez-le ici.
    - **ID Apple** : saisissez l’ID Apple du compte associé au programme d’achats en volume.
    - **Type de compte VPP** : choisissez **Entreprise** ou **Éducation**.
4. Une fois ces opérations effectuées, cliquez sur **Télécharger**.

Le jeton est affiché dans le panneau de liste de jetons.


Vous pouvez synchroniser les données détenues par Apple avec Intune à tout moment en sélectionnant **Synchroniser maintenant**.

## <a name="to-assign-a-volume-purchased-app"></a>Pour affecter une application achetée en volume

1. Dans la charge de travail **Gérer les applications**, choisissez **Gérer** > **Applications sous licence**.
2. Dans le panneau de liste d’applications, choisissez l’application que vous souhaitez affecter, puis choisissez «**...** » > **Affecter des groupes**.
3. Dans le panneau <*Nom de l’application*> - **Groupes affectés**, choisissez **Gérer** > **Groupes affectés**.
4. Choisissez **Affecter des groupes** puis, dans le panneau **Sélectionner des groupes**, choisissez les groupes d’utilisateurs ou d’appareils Azure AD auxquels vous souhaitez affecter l’application.
Vous devez choisir une action d’affectation **Requise**. Les installations disponibles ne sont pas prises en charge. En outre, les affectations à des groupes d’appareils sont disponibles pour les nouveaux clients créés après le mois de janvier 2017. Si votre client a été créé avant cette date et que vous ne pouvez pas affecter des applications VPP à des groupes d’appareils, contactez le support technique Intune.
5. Une fois que vous avez terminé, choisissez **Enregistrer**.

Consultez la page [Guide pratique pour surveiller des applications](monitor-apps.md) pour plus d’informations pour vous aider à contrôler les affectations de l’application.

## <a name="further-information"></a>Informations supplémentaires

Lorsque vous affectez l’application comme une installation **Requise**, chaque utilisateur qui installe l’application utilise une licence.

Pour libérer une licence, vous devez modifier l’action d’affectation sur **Désinstallation**. La licence est récupérée une fois l’application désinstallée.

Quand un utilisateur avec un appareil éligible essaie pour la première fois d’installer une application VPP, il est invité à participer au programme VPP d’Apple. Il doit accepter pour que l’installation de l’application se poursuivre.

