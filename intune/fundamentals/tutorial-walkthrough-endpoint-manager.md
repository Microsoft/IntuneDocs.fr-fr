---
title: Tutoriel – Visite guidée d’Intune dans le Gestionnaire de points de terminaison Microsoft
titleSuffix: Microsoft Intune
description: Dans ce tutoriel, vous allez suivre une visite guidée de Microsoft Intune dans le centre d’administration du Gestionnaire de points de terminaison Microsoft pour mieux comprendre comment accomplir certaines tâches.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514079"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Tutoriel : Visite guidée d’Intune dans le Gestionnaire de points de terminaison Microsoft

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) comprend plus de 100 services pour vous aider dans divers scénarios et possibilités de cloud computing. Microsoft Intune est l’un des différents services disponibles dans Azure. Intune vous permet de garantir que les appareils, applications et données de votre entreprise répondent aux exigences de sécurité de cette dernière. C’est vous qui définissez les exigences à vérifier et ce qui se passe quand ces exigences ne sont pas respectées. Le [centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) permet de trouver le service Microsoft Intune ainsi que d’autres paramètres liés à la gestion des appareils. Le fait de comprendre les fonctionnalités disponibles dans Intune vous aidera à accomplir différentes tâches de gestion des appareils mobiles (MDM) et de gestion des applications mobiles (MAM).

> [!NOTE]
> Microsoft Endpoint Manager est une plateforme de gestion de points de terminaison intégrée unique pour la gestion de tous vos points de terminaison. Ce Centre d’administration de Microsoft Endpoint Manager intègre ConfigMgr et Microsoft Intune.

Dans ce tutoriel, vous allez :
> [!div class="checklist"]
> * Effectuer une visite guidée du centre d’administration du Gestionnaire de points de terminaison Microsoft
> * Personnaliser votre affichage du centre d’administration du Gestionnaire de points de terminaison Microsoft

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
Avant de configurer Microsoft Intune, passez en revue les exigences suivantes :

- [Systèmes d’exploitation et navigateurs pris en charge](../supported-devices-browsers.md) 
- [Exigences et bande passante de la configuration réseau](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>S’inscrire à une version d’évaluation gratuite de Microsoft Intune

L’essai d’Intune est gratuit pendant 30 jours. Si vous disposez déjà d’un compte professionnel ou scolaire, **connectez-vous** avec ce compte et ajoutez Intune à votre abonnement. Sinon, vous pouvez [vous inscrire à un compte d’essai gratuit](free-trial-sign-up.md) afin d’utiliser Intune pour votre organisation.

> [!IMPORTANT]
> Vous ne pouvez pas combiner un compte professionnel ou scolaire existant après avoir ouvert un nouveau compte.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Visite guidée de Microsoft Intune dans le centre d’administration du Gestionnaire de points de terminaison Microsoft

Suivez les étapes ci-dessous pour mieux comprendre Intune dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Une fois la visite guidée effectuée, vous aurez une meilleure compréhension de certaines des zones principales d’Intune.

1. Ouvrez un navigateur et connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). Si vous débutez avec Intune, utilisez votre abonnement d’essai gratuit.

    ![Capture d’écran du volet Page d’accueil dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Quand vous ouvrez le Gestionnaire de points de terminaison Microsoft ou n’importe quel autre service dans Azure, le service s’affiche dans un volet. Parmi les premières charges de travail que vous pouvez utiliser dans Intune figurent les **appareils**, les **applications**, les **utilisateurs** et les **groupes**. Une charge de travail est simplement une sous-zone d’un service. Quand vous sélectionnez la charge de travail, ce volet s’ouvre en pleine page. D’autres volets s’ouvrent en glissant à partir de la droite du volet et se ferment pour faire apparaître le volet précédent. 

    Par défaut, lorsque vous ouvrez le Gestionnaire de points de terminaison Microsoft, le volet **Page d’accueil** s’affiche. Ce volet fournit un aperçu visuel global de l’état du locataire et de l’état de conformité, ainsi que d’autres liens utiles associés.

2. Dans le volet de navigation, sélectionnez **Tableau de bord** pour afficher des détails généraux sur les appareils et les applications clientes figurant dans votre locataire Intune. Si vous commencez avec un nouveau locataire Intune, vous n’aurez encore aucun appareil inscrit. 

    ![Capture d’écran du volet Tableau de bord dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune vous permet de gérer les appareils et les applications de votre personnel, notamment la façon dont il accède aux données de votre entreprise. Pour utiliser ce service de gestion des appareils mobiles (MDM), les appareils doivent d’abord être inscrits auprès d’Intune. Quand un appareil est inscrit, il reçoit un certificat MDM. Ce certificat est utilisé pour communiquer avec le service Intune. 

    Plusieurs méthodes permettent d’inscrire les appareils de votre personnel dans Intune. Chaque méthode dépend de la propriété de l’appareil (personnel ou d’entreprise), du type d’appareil (iOS/iPadOS, Windows, Android) et des exigences de gestion (réinitialisations, affinité, verrouillage). Toutefois, avant de pouvoir activer l’inscription des appareils, vous devez configurer votre infrastructure Intune. Pour inscrire des appareils, vous devez notamment [définir votre autorité de gestion des appareils mobiles](mdm-authority-set.md). Pour plus d’informations sur la préparation de votre environnement (locataire) Intune, consultez [Configurer Intune](setup-steps.md). Une fois que votre locataire Intune est prêt, vous pouvez inscrire des appareils. Pour plus d’informations sur l’inscription des appareils, consultez [Qu’est-ce que l’inscription d’appareils ?](../enrollment/device-enrollment.md)

3. Dans le volet de navigation, sélectionnez **Appareils** pour afficher des détails sur les appareils inscrits dans votre locataire Intune. 

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Appareils**.

    Le volet **Appareils - Vue d’ensemble** comporte plusieurs onglets qui vous permettent d’afficher un résumé des états et des alertes ci-dessous :
    - **État de l’inscription** – Passez en revue les détails sur les appareils inscrits dans Intune par plateforme et les échecs d’inscription.
    - **Alertes d’inscription** – Recherchez plus d’informations sur les appareils non affectés par plateforme. 
    - **État de conformité** – Passez en revue l’état de conformité en fonction de l’appareil, de la stratégie, des paramètres, des menaces et de la protection. En outre, ce volet fournit la liste des appareils sans stratégie de conformité.
    - **État de la configuration** – Examinez l’état de configuration des profils d’appareils, ainsi que le déploiement de profil. 
    - **État des mises à jour logicielles** – Examinez un visuel de l’état de déploiement pour tous les appareils et tous les utilisateurs.

    ![Capture d’écran du volet Appareils dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. À partir du volet **Appareils - Vue d’ensemble**, sélectionnez **Stratégies de conformité** pour afficher les détails sur la conformité des appareils gérés par Intune. Des informations semblables à l’image suivante s’affichent.

    ![Capture d’écran du volet Stratégies de conformité dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Conformité de l’appareil**.

    Les exigences de conformité sont essentiellement des règles, comme exiger un code confidentiel (PIN) d’appareil ou un chiffrement des appareils. Les stratégies de conformité des appareils définissent les règles et les paramètres que doit suivre un appareil pour être considéré comme conforme. Pour utiliser la conformité des appareils, vous devez disposer des éléments suivants :
    - Un abonnement Intune et Azure Active Directory (Azure AD) Premium
    - Des appareils exécutant une plateforme prise en charge
    - Les appareils doivent être inscrits dans Intune
    - Des appareils inscrits auprès d’un utilisateur ou d’aucun utilisateur principal
    
    Pour plus d’informations, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](../protect/device-compliance-get-started.md).

5. Dans le volet **Appareils - Vue d’ensemble**, sélectionnez **Accès conditionnel** pour afficher des détails sur les stratégies d’accès.

    ![Capture d’écran du volet Accès conditionnel dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Accès conditionnel**.

    L’accès conditionnel fait référence aux moyens grâce auxquels vous pouvez contrôler les appareils et les applications qui sont autorisés à se connecter à vos ressources d’entreprise et de messagerie. Pour en savoir plus sur l’accès conditionnel basé sur l’application et basé sur l’appareil, et découvrir des scénarios courants d’utilisation de l’accès conditionnel avec Intune, consultez [Qu’est-ce que l’accès conditionnel ?](../protect/conditional-access.md)

6. Dans le volet de navigation, sélectionnez **Appareils** > **Profils de configuration** pour afficher des détails sur les profils des appareils dans Intune.

    ![Capture d’écran du volet Profils de configuration dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Configuration du périphérique**.

    Intune inclut des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils de votre organisation. Ces paramètres et fonctionnalités sont ajoutés aux « profils de configuration ». Vous pouvez créer des profils pour différents appareils et différentes plateformes, notamment iOS/iPadOS, Android, macOS et Windows. Ensuite, vous pouvez utiliser Intune pour appliquer le profil aux appareils de votre organisation.   

    Pour plus d’informations sur la configuration des appareils, consultez [Appliquer des paramètres de fonctionnalités sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune](../configuration/device-profiles.md).

7. Dans le volet de navigation, sélectionnez **Appareils** > **Tous les appareils** pour afficher des détails sur les appareils inscrits dans votre locataire Intune. Si vous commencez avec une nouvelle inscription Intune, vous n’aurez encore aucun appareil inscrit.

    ![Capture d’écran du volet Tous les appareils dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    Cette liste d’appareils affiche des détails clés sur la conformité, la version du système d’exploitation et la date du dernier archivage.

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Périphériques** > **Tous les périphériques**.
 
8. Dans le volet de navigation, sélectionnez **Applications** pour afficher une vue d’ensemble de l’état des applications. Ce volet fournit l’état d’installation des applications en fonction des onglets suivants :

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Applications clientes**.

    Le volet **Applications - Vue d’ensemble** comporte deux onglets qui vous permettent d’afficher un résumé des états ci-dessous :
    - **État de l’installation** – Affichez les principaux échecs d’installation par appareil, ainsi que les applications avec échec d’installation.  
    - **État de la stratégie de protection des applications** – Recherchez des détails sur les utilisateurs affectés aux stratégies de protection des applications, ainsi que les utilisateurs marqués d’un indicateur.

    ![Capture d’écran du volet Applications dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    En tant qu’administrateur informatique, vous pouvez utiliser Microsoft Intune pour gérer les applications clientes utilisées par les équipes de votre entreprise. Cette fonctionnalité s’ajoute à la gestion des appareils et à la protection des données. L’une des priorités d’un administrateur est de vérifier que les utilisateurs finaux ont accès aux applications dont ils ont besoin pour travailler. Vous pourrez également souhaiter affecter et gérer des applications sur les appareils qui ne sont pas inscrits avec Intune. Intune propose une gamme de fonctionnalités pour vous aider à obtenir les applications dont vous avez besoin, sur les appareils de votre choix. 

    > [!NOTE]
    > Le volet **Applications - Vue d’ensemble** fournit également l’état du locataire et les détails du compte.

    Pour plus d’informations sur l’ajout et l’attribution d’applications, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md) et [Attribuer des applications à des groupes avec Microsoft Intune](../apps/apps-deploy.md).

9. Dans le volet **Applications - Vue d’ensemble**, sélectionnez **Toutes les applications** pour afficher la liste des applications qui ont été ajoutées dans Intune.

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Applications clientes** > **Applications**.

    Vous pouvez ajouter dans Intune divers types d’application différents en fonction de la plateforme. Une fois qu’une application a été ajoutée, vous pouvez l’affecter à des groupes d’utilisateurs. 

    ![Capture d’écran du volet Toutes les applications dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](~/apps/apps-add.md). 

10. Dans le volet de navigation, sélectionnez **Utilisateurs** pour afficher des détails sur les utilisateurs que vous avez inclus dans Intune. Ces utilisateurs sont le personnel de votre entreprise.

    ![Capture d’écran du volet Utilisateurs dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Utilisateurs**.

    Vous pouvez ajouter directement des utilisateurs à Intune ou synchroniser des utilisateurs à partir de votre annuaire Active Directory local. Une fois ajoutés, les utilisateurs peuvent inscrire des appareils et accéder aux ressources de l’entreprise. Vous pouvez également accorder aux utilisateurs des autorisations supplémentaires pour accéder à Intune. Pour plus d’informations, consultez [Ajouter des utilisateurs et accorder une autorisation d’administration dans Intune](users-add.md).

11. Dans le volet de navigation, sélectionnez **Groupes** pour afficher des détails sur les groupes Azure Active Directory (Azure AD) inclus dans Intune. En tant qu’administrateur Intune, vous utilisez des groupes pour gérer les appareils et les utilisateurs.

    ![Capture d’écran du volet Groupes dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Groupes**.

    Vous pouvez configurer des groupes en fonction des besoins de votre organisation. Créez des groupes pour organiser les utilisateurs ou appareils par emplacement géographique, service ou spécification matérielle. Utilisez des groupes pour gérer les tâches à l’échelle. Par exemple, vous pouvez définir des stratégies pour de nombreux utilisateurs ou déployer des applications sur un ensemble d’appareils. Pour plus d’informations sur les groupes, consultez [Ajouter des groupes pour organiser des utilisateurs et des appareils](../groups-add.md).

12. Dans le volet de navigation, sélectionnez **Administration de locataire** pour afficher des détails sur votre locataire Intune.

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **État du locataire**.

    Le volet **Administrateur de locataire - État du locataire** comporte des onglets pour les **détails du locataire**, l’**état du connecteur** et le **tableau de bord Service Health**. En cas de problème avec votre locataire ou Intune lui-même, vous trouverez des détails dans ce volet. 

    ![Capture d’écran du volet État du locataire dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Pour plus d’informations, consultez [État du locataire Intune](../tenant-status.md).

13. Dans le volet de navigation, sélectionnez **Résolution des problèmes + support** > **Dépanner** pour vérifier les détails de l’état pour un utilisateur spécifique. 

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Résoudre les problèmes**.

    Dans la liste déroulante **Affectations**, vous pouvez choisir d’afficher les affectations ciblées des applications clientes, des stratégies, des anneaux de mise à jour et des restrictions d’inscription. En outre, ce volet fournit des détails sur l’appareil, l’état de protection d’application et les échecs d’inscription pour un utilisateur spécifique.

    ![Capture d’écran du volet Dépanner dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Pour plus d’informations sur la résolution des problèmes dans Intune, consultez [Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise](../help-desk-operators.md).

14. Dans le volet de navigation, sélectionnez **Résolution des problèmes + support** > **Aide et support** pour demander de l’aide. 

    > [!TIP]
    > Si vous utilisiez déjà Intune dans le Portail Azure, vous trouviez les détails ci-dessus dans le Portail Azure en vous connectant à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et en sélectionnant **Aide et support**.

    En tant qu’administrateur informatique, vous pouvez utiliser l’option **Aide et support** pour rechercher et afficher des solutions, ainsi que pour créer un ticket de support en ligne pour Intune. 

    ![Capture d’écran du volet Aide et support dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Pour créer un ticket de support, vous devez attribuer à votre compte un rôle d’administrateur dans Azure Active Directory. Les rôles d’administrateur incluent **Administrateur Intune**, **Administrateur général** et **Administrateur de service**. 

    Pour plus d’informations, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](../get-support.md).

15. Dans le volet de navigation, sélectionnez **Résolution des problèmes + support** > **Scénarios guidés** pour afficher les scénarios guidés Intune disponibles. 

    Un scénario guidé est une série d’étapes personnalisée centrée sur un cas d’usage de bout en bout. Les scénarios courants sont basés sur le rôle joué par un administrateur, un utilisateur ou un appareil dans votre organisation. Ces rôles nécessitent généralement un ensemble de profils, de paramètres, d’applications et de contrôles de sécurité soigneusement orchestrés pour offrir une expérience utilisateur et une sécurité optimales.

    Si les étapes et les ressources nécessaires à l’implémentation d’un scénario Intune particulier ne vous sont pas familières, les scénarios guidés peuvent vous servir de point de départ. 

    ![Capture d’écran du volet Scénarios guidés dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Pour plus d’informations sur les scénarios guidés, consultez [Vue d’ensemble des scénarios guidés](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Configurer le centre d’administration du Gestionnaire de points de terminaison Microsoft

Azure vous permet de personnaliser et de configurer l’affichage du portail.

### <a name="change-the-dashboard"></a>Modifier le tableau de bord

Le **Tableau de bord** affiche des détails généraux sur les appareils et les applications clientes figurant dans votre locataire Intune. Les tableaux de bord permettent de créer une vue ciblée et organisée dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Utilisez les tableaux de bord comme un espace de travail dans lequel vous pouvez rapidement lancer des tâches pour les opérations quotidiennes et superviser les ressources. Créer des tableaux de bord personnalisés basés sur des projets, des tâches ou des rôles d’utilisateur, par exemple. Le centre d’administration du Gestionnaire de points de terminaison Microsoft fournit un tableau de bord par défaut comme point de départ. Vous pouvez modifier ce tableau de bord par défaut, créer et personnaliser des tableaux de bord supplémentaires, ainsi que publier et partager des tableaux de bord pour les mettre à la disposition d’autres utilisateurs. 

   ![Capture d’écran du volet Tableau de bord dans le centre d’administration du Gestionnaire de points de terminaison Microsoft](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Pour modifier votre tableau de bord actuel, sélectionnez **Modifier**. Si vous ne voulez pas modifier votre tableau de bord par défaut, vous pouvez également en créer un en cliquant sur **Nouveau tableau de bord**. Quand vous créez un tableau de bord, vous obtenez un tableau de bord privé vide. La **Galerie de vignettes** vous permet d’ajouter ou de réorganiser des vignettes. Vous pouvez rechercher les vignettes par catégorie ou par type de ressource. Vous pouvez également rechercher des vignettes particulières. Sélectionnez **Mon tableau de bord** pour sélectionner l’un de vos tableaux de bord personnalisés.

### <a name="change-the-portal-settings"></a>Modifier les paramètres du portail

Vous pouvez personnaliser le centre d’administration du Gestionnaire de points de terminaison Microsoft en choisissant la vue par défaut, le thème, le délai d’expiration des informations d’identification, ainsi que les paramètres de langue et de région.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Étapes suivantes

Pour être rapidement opérationnel sur Microsoft Intune, parcourez les étapes des Guides de démarrage rapide Intune en commençant par configurer un compte Intune gratuit.

> [!div class="nextstepaction"]
> [Démarrage rapide : Essayer gratuitement Microsoft Intune](free-trial-sign-up.md)
