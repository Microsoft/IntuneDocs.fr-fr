---
title: 'Tutoriel - Procédure pas à pas : Intune dans le portail Azure'
titleSuffix: Microsoft Intune
description: Dans ce tutoriel, vous allez suivre une visite guidée de Microsoft Intune pour mieux comprendre comment accomplir certaines tâches.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 03/28/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c601af8c2b73ac68ec88f45d3684fcfd41f1c87f
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567586"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Tutoriel : Présentation détaillée de Microsoft Intune dans le portail Azure

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) comprend plus de 100 services pour vous aider dans divers scénarios et possibilités de cloud computing. Microsoft Intune est l’un des différents services disponibles dans Azure. Intune vous permet de garantir que les appareils, applications et données de votre entreprise répondent aux exigences de sécurité de cette dernière. C’est vous qui définissez les exigences à vérifier et ce qui se passe quand ces exigences ne sont pas respectées. Le [portail Azure](https://portal.azure.com) est l’endroit où se trouve le service Microsoft Intune. Le fait de comprendre les fonctionnalités disponibles dans Intune vous aidera à accomplir différentes tâches de gestion des appareils mobiles (MDM) et de gestion des applications mobiles (MAM).

Dans ce tutoriel, vous allez :
> [!div class="checklist"]
> * Suivre une visite guidée de Microsoft Intune
> * Configurer le portail Azure

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
Avant de configurer Microsoft Intune, passez en revue les exigences suivantes :

   - [Systèmes d’exploitation et navigateurs pris en charge](supported-devices-browsers.md) 
   - [Exigences et bande passante de la configuration réseau](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>S’inscrire à une version d’évaluation gratuite de Microsoft Intune

L’essai d’Intune est gratuit pendant 30 jours. Si vous disposez déjà d’un compte professionnel ou scolaire, **connectez-vous** avec ce compte et ajoutez Intune à votre abonnement. Sinon, vous pouvez [vous inscrire à un compte d’essai gratuit](free-trial-sign-up.md) afin d’utiliser Intune pour votre organisation.

> [!IMPORTANT]
> Vous ne pouvez pas combiner un compte professionnel ou scolaire existant après avoir ouvert un nouveau compte.

## <a name="tour-microsoft-intune"></a>Suivre une visite guidée de Microsoft Intune

Suivez les étapes ci-dessous pour mieux comprendre Intune dans le portail Azure. Une fois la visite guidée effectuée, vous aurez une meilleure compréhension de certaines des zones principales d’Intune.

1. Ouvrez un navigateur et connectez-vous au [portail Intune](https://aka.ms/intuneportal). Si vous débutez avec Intune, utilisez votre abonnement d’essai gratuit.

    ![Capture d’écran du portail Microsoft Intune](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Quand vous ouvrez Intune ou n’importe quel autre service dans Azure, le service s’affiche dans un volet. Parmi les premières charges de travail que vous pouvez utiliser dans Intune figurent les **appareils**, les **applications clientes**, les **utilisateurs** et les **groupes**. Une charge de travail est simplement une sous-zone d’un service. Quand vous sélectionnez la charge de travail, ce volet s’ouvre en pleine page. D’autres volets s’ouvrent en glissant à partir de la droite du volet et se ferment pour faire apparaître le volet précédent. Un volet est également appelé « panneau ». 

    Par défaut, quand vous ouvrez Intune, le volet **Vue d’ensemble** est affiché. Ce volet fournit un aperçu visuel global de l’état d’attribution et de conformité des appareils, ainsi que l’état d’installation des applications.

2. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Inscription de l’appareil** pour afficher des détails sur les appareils inscrits dans votre locataire Intune. Si vous commencez avec un nouveau locataire Intune, vous n’aurez encore aucun appareil inscrit. 

    ![Capture d’écran du volet d’inscription des appareils](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune vous permet de gérer les appareils et les applications de votre personnel, notamment la façon dont il accède aux données de votre entreprise. Pour utiliser ce service de gestion des appareils mobiles (MDM), les appareils doivent d’abord être inscrits auprès d’Intune. Quand un appareil est inscrit, il reçoit un certificat MDM. Ce certificat est utilisé pour communiquer avec le service Intune. 

    Plusieurs méthodes permettent d’inscrire les appareils de votre personnel dans Intune. Chaque méthode dépend de la propriété de l’appareil (personnel ou d’entreprise), du type d’appareil (iOS, Windows, Android) et des exigences de gestion (réinitialisations, affinité, verrouillage). Toutefois, avant de pouvoir activer l’inscription des appareils, vous devez configurer votre infrastructure Intune. Pour inscrire des appareils, vous devez notamment [définir votre autorité de gestion des appareils mobiles](mdm-authority-set.md). Pour plus d’informations sur la préparation de votre environnement (locataire) Intune, consultez [Configurer Intune](setup-steps.md). Une fois que votre locataire Intune est prêt, vous pouvez inscrire des appareils. Pour plus d’informations sur l’inscription des appareils, consultez [Qu’est-ce que l’inscription d’appareils ?](device-enrollment.md)

3. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Conformité de l’appareil** pour afficher les détails sur la conformité des appareils gérés par Intune. Des informations semblables à l’image suivante s’affichent.

    ![Capture d’écran du volet de conformité des appareils](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Les exigences de conformité sont essentiellement des règles, comme exiger un code confidentiel (PIN) d’appareil ou un chiffrement des appareils. Les stratégies de conformité des appareils définissent les règles et les paramètres que doit suivre un appareil pour être considéré comme conforme. Pour utiliser la conformité des appareils, vous devez disposer des éléments suivants :
    - Un abonnement Intune et Azure Active Directory (Azure AD) Premium
    - Des appareils exécutant une plateforme prise en charge
    - Les appareils doivent être inscrits dans Intune
    - Des appareils inscrits auprès d’un utilisateur ou d’aucun utilisateur principal
    
    Pour plus d’informations, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](device-compliance-get-started.md).

4. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Configuration de l’appareil** pour afficher des informations sur les profils des appareils dans Intune. 

    ![Capture d’écran du volet de configuration des appareils](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune inclut des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils de votre organisation. Ces paramètres et fonctionnalités sont ajoutés aux « profils de configuration ». Vous pouvez créer des profils pour différents appareils et différentes plateformes, notamment iOS, Android et Windows. Ensuite, vous pouvez utiliser Intune pour appliquer le profil aux appareils de votre organisation.   

    Pour plus d’informations sur la configuration des appareils, consultez [Appliquer des paramètres de fonctionnalités sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune](device-profiles.md).

5. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Appareils** pour afficher des détails sur les appareils inscrits de votre locataire Intune. Si vous commencez avec une nouvelle inscription Intune, vous n’aurez encore aucun appareil inscrit. 

    ![Capture d’écran du volet d’inscription des appareils](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)
    
    Le volet **Appareils** fournit des détails sur les appareils inscrits de votre locataire. Vous pouvez cliquer sur **Tous les appareils** pour afficher la liste d’appareils de votre locataire Intune. 

6. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Applications clientes** pour afficher l’état d’installation des applications.

    ![Capture d’écran du volet des applications clientes](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)
    
    En tant qu’administrateur informatique, vous pouvez utiliser Microsoft Intune pour gérer les applications clientes utilisées par les équipes de votre entreprise. Cette fonctionnalité s’ajoute à la gestion des appareils et à la protection des données. L’une des priorités d’un administrateur est de vérifier que les utilisateurs finaux ont accès aux applications dont ils ont besoin pour travailler. Vous pourrez également souhaiter affecter et gérer des applications sur les appareils qui ne sont pas inscrits avec Intune. Intune propose une gamme de fonctionnalités pour vous aider à obtenir les applications dont vous avez besoin, sur les appareils de votre choix. Pour plus d’informations sur l’ajout et l’attribution d’applications, consultez [Ajouter des applications à Microsoft Intune](apps-add.md) et [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md).

7. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Accès conditionnel** pour afficher plus d’informations sur les stratégies d’accès.

    ![Capture d’écran du volet d’accès conditionnel](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    L’accès conditionnel fait référence aux moyens grâce auxquels vous pouvez contrôler les appareils et les applications qui sont autorisés à se connecter à vos ressources d’entreprise et de messagerie. Pour en savoir plus sur l’accès conditionnel basé sur l’application et basé sur l’appareil, et découvrir des scénarios courants d’utilisation de l’accès conditionnel avec Intune, consultez [Qu’est-ce que l’accès conditionnel ?](conditional-access.md)

8. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Utilisateurs** pour afficher les détails sur les utilisateurs que vous avez inclus dans Intune. Ces utilisateurs sont le personnel de votre entreprise. 
 
    ![Capture d’écran du volet Utilisateurs](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Vous pouvez ajouter directement des utilisateurs à Intune ou synchroniser des utilisateurs à partir de votre annuaire Active Directory local. Une fois ajoutés, les utilisateurs peuvent inscrire des appareils et accéder aux ressources de l’entreprise. Vous pouvez également accorder aux utilisateurs des autorisations supplémentaires pour accéder à Intune. Pour plus d’informations, consultez [Ajouter des utilisateurs et accorder une autorisation d’administration dans Intune](users-add.md).

9. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Groupes** pour afficher plus d’informations sur les groupes Azure Active Directory (Azure AD) inclus dans Intune. En tant qu’administrateur Intune, vous utilisez des groupes pour gérer les appareils et les utilisateurs. 

    ![Capture d’écran du volet Groupes](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Vous pouvez configurer des groupes en fonction des besoins de votre organisation. Créez des groupes pour organiser les utilisateurs ou appareils par emplacement géographique, service ou spécification matérielle. Utilisez des groupes pour gérer les tâches à l’échelle. Par exemple, vous pouvez définir des stratégies pour de nombreux utilisateurs ou déployer des applications sur un ensemble d’appareils. Pour plus d’informations sur les groupes, consultez [Ajouter des groupes pour organiser des utilisateurs et des appareils](groups-add.md).

10. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Aide et support** pour demander de l’aide. En tant qu’administrateur informatique, vous pouvez utiliser l’option **Aide et support** pour rechercher et afficher des solutions, ainsi que pour créer un ticket de support en ligne pour Intune. 

    ![Capture d’écran du volet Aide et de support](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Pour créer un ticket de support, vous devez attribuer à votre compte un rôle d’administrateur dans Azure Active Directory. Les rôles d’administrateur incluent **Administrateur Intune**, **Administrateur général** et **Administrateur de service**. Pour plus d’informations, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).

11. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **État du locataire** pour afficher des détails sur votre locataire Intune.

    ![Capture d’écran du volet État du locataire](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    Les détails d’état du locataire incluent l’état du connecteur, l’intégrité du service Intune et les actualités Intune. En cas de problème avec votre locataire ou Intune lui-même, vous trouverez des détails dans le volet **État du locataire**. Pour plus d’informations, consultez [État du locataire Intune](tenant-status.md).

12. À partir d’[Intune](https://aka.ms/intuneportal), sélectionnez **Résoudre les problèmes** pour accéder à un raccourci vers des conseils de résolution des problèmes, demander de l’aide ou vérifier l’état d’Intune. Ces informations sont propres à l’utilisateur Intune que vous sélectionnez.

    ![Capture d’écran du volet Résoudre les problèmes](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Pour plus d’informations sur la résolution des problèmes dans Intune, consultez [Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise](help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Configurer le portail Azure

Azure vous permet de personnaliser et de configurer l’affichage du portail.

### <a name="change-the-sidebar"></a>Changer la barre latérale

La **barre latérale** à gauche du portail Azure affiche une liste de tous les services Azure disponibles. L’affichage par défaut de cette liste complète peut être changé pour que vous puissiez conserver un affichage persistant des services qui vous intéressent le plus. Le scénario ci-dessous utilise l’exemple d’Intune comme service à ajouter en haut de la liste.

![Utilisateur recherchant Microsoft Intune dans la liste « Autres services ».](./media/azure-add-intune1.png)

1. Sélectionnez **Tous les services** dans la barre latérale à gauche de la page.
2. Recherchez **Intune** dans la zone de filtre.
3. Sélectionnez **l’étoile** pour ajouter Intune en bas de la liste de vos services favoris.
4. Pointez sur le service Intune. Sélectionnez et faites glisser Intune à l’aide des **trois points verticaux** à droite du nom du service.

### <a name="change-the-dashboard"></a>Changer le tableau de bord

Votre page d’arrivée par défaut est le **tableau de bord**. C’est dans cette page que vous personnalisez vos vignettes pour qu’elles affichent les informations que vous jugez pertinentes.

![Image du nouveau tableau de bord générique. Elle affiche la barre latérale avec tous les services sur la gauche et le tableau de bord principal au centre. Les boutons de modification du tableau de bord sont en haut, avec des vignettes qui offrent un accès à toutes les ressources, des didacticiels de démarrage rapide, l’intégrité du service et la place de marché Azure.](./media/azure-default-dashboard.png)

Pour modifier votre tableau de bord actuel, sélectionnez le bouton **Modifier le tableau de bord**. Si vous ne voulez pas modifier votre tableau de bord par défaut, vous pouvez également en créer un en cliquant sur **Nouveau tableau de bord**. Quand vous créez un tableau de bord, vous obtenez un tableau de bord privé vide. La **Galerie de vignettes** vous permet d’ajouter ou de réorganiser des vignettes. Vous pouvez rechercher des vignettes par leur catégorie **Général**, leur **Type**, par le biais de **Rechercher**, et par le biais d’un **Groupe de ressources** ou d’une **Balise**.

Vous pouvez aussi ajouter des vignettes directement à votre tableau de bord en cliquant sur l’un des boutons en forme de **points de suspension** et en sélectionnant **Épingler au tableau de bord**.

![Gros plan de l’emplacement Utilisateurs et groupes > Tous les groupes dans Intune, avec l’option « Épingler au tableau de bord » affichée à l’extrême droite d’un groupe.](./media/azure-pin-to-dashboard.png)

Cette fonctionnalité est plus pertinente une fois que vous avez ajouté davantage de contenu, comme des groupes et des utilisateurs, dans Intune.

## <a name="next-steps"></a>Étapes suivantes

Pour être rapidement opérationnel sur Microsoft Intune, parcourez les étapes des Guides de démarrage rapide Intune en commençant par configurer un compte Intune gratuit.

> [!div class="nextstepaction"]
> [Démarrage rapide : Essayer gratuitement Microsoft Intune](free-trial-sign-up.md)


