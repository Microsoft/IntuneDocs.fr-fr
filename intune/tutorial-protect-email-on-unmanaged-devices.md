---
title: Didacticiel - Protéger la messagerie Exchange Online sur les appareils non gérés
titleSuffix: Microsoft Intune
description: Apprenez à sécuriser Office 365 Exchange Online avec les stratégies de protection des applications Intune et l’accès conditionnel Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6224a0dae7c0aa3d80d4e64331a668953220f65
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798782"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutoriel : Protéger la messagerie Exchange Online sur les appareils non gérés

Apprenez en plus sur l’utilisation des stratégies de protection des applications avec un accès conditionnel pour protéger Exchange Online, même lorsque les appareils ne sont pas inscrits dans une solution de gestion des appareils comme Intune. Dans ce tutoriel, vous apprendrez à : 

> [!div class="checklist"]
> * Créez une stratégie de protection des applications Intune pour l’application Outlook. Vous allez limiter ce que l’utilisateur peut faire avec les données de l’application en empêchant l’option « Enregistrer sous » et en restreignant les opérations couper, copier et coller. 
> * Créer des stratégies d’accès conditionnel Azure Active Directory (Azure AD) qui donnent une autorisation exclusive à l’application Outlook pour accéder à la messagerie d’entreprise dans Exchange Online. Vous allez également exiger une authentification multifacteur (MFA) pour des clients d’authentification moderne, comme Outlook pour iOS et Android.

## <a name="prerequisites"></a>Prérequis
  - Vous aurez besoin d’un locataire de test avec les abonnements suivants pour ce tutoriel :
    - Azure Active Directory Premium ([essai gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Abonnement Intune ([essai gratuit](free-trial-sign-up.md))
    - Abonnement Office 365 Entreprise qui inclut Exchange ([essai gratuit](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune. Pour accéder à Intune dans le Portail Azure, choisissez **Tous les services** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Créer la stratégie de protection des applications
Pour ce didacticiel, nous allons configurer une stratégie de protection des applications Intune pour l’application Outlook afin de mettre des protections en place au niveau de l’application. Nous allons exiger un code PIN pour ouvrir une application dans un contexte professionnel. Nous allons également limiter le partage des données entre les applications et empêcher l’enregistrement des données d’entreprise sur un emplacement personnel.

1.  Dans Intune, sélectionnez **Applications clientes** > **Stratégies de protection des applications** > **Ajouter une stratégie**.
2.  Dans **Nom**, entrez **test de la stratégie d’application Outlook**.
3.  Dans **Description**, entrez **test de la stratégie d’application Outlook**.
4.  Sélectionnez **Applications**. Dans la liste des applications, sélectionnez **Outlook**, puis choisissez **Sélectionner**.
5.  Cliquez sur **Paramètres**. 
6.  Sous **Réadressage des données**, sélectionnez les paramètres suivants pour ce didacticiel :

    - Pour **Autoriser l'application à transférer des données vers d'autres applications**, sélectionnez **Aucune**.
    - Pour **Autoriser l'application à recevoir des données d'autres applications**, sélectionnez **Aucune**.
    - Pour **Empêcher « Enregistrer sous »**, sélectionnez **Oui**.
    - Pour **Restreindre les opérations couper, copier et coller avec d’autres**, sélectionnez **Bloqué**.
   
     ![Sélectionner les paramètres de réadressage des données de la stratégie de protection de l’application Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  Sous **Actions d’accès**, sélectionnez les paramètres suivants pour ce didacticiel :

    - Pour **Exiger un code confidentiel d’accès**, sélectionnez **Oui**.
    - Pour **Exiger des informations d’identification d’entreprise pour l’accès**, sélectionnez **Oui**.
    - Laissez la valeur par défaut pour tous les autres paramètres.
 
     ![Sélectionner les actions d’accès de stratégie de protection de l’application Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  Sélectionnez **OK**.
10. Sélectionnez **Créer**.

La stratégie de protection d’application pour Outlook est créée. Vous pouvez maintenant définir un accès conditionnel pour exiger que les appareils utilisent l’application Outlook.

## <a name="create-conditional-access-policies"></a>Créer des stratégies d’accès conditionnel
Nous allons maintenant créer deux stratégies d’accès conditionnel pour couvrir toutes les plateformes d’appareils. La première stratégie exige que les clients d’authentification moderne, comme Outlook pour iOS et Outlook pour Android, utilisent l’application Outlook et l’authentification multifacteur approuvées. La deuxième stratégie exige que les clients Exchange ActiveSync utilisent l’application Outlook approuvée. (Actuellement, Exchange Active Sync ne prend pas en charge d’autres conditions que la plateforme de l’appareil). Vous pouvez configurer les stratégies d’accès conditionnel depuis le portail Azure AD ou le portail Intune. Étant donné que nous sommes déjà dans le portail Intune, nous allons créer la stratégie ici.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Créer une stratégie d’authentification Multifacteur pour les clients de l’authentification moderne
1.  Dans Intune, sélectionnez **Accès conditionnel** > **Stratégies** > **Nouvelle stratégie**.
1.  Dans **Nom**, entrez **Stratégie de test pour les clients d’authentification modernes**. 
3.  Sous **Affectations**, sélectionnez **Utilisateurs et groupes**. Dans l’onglet **Inclure**, sélectionnez **Tous les utilisateurs**, puis **Terminé**.

4.  Sous **Affectations**, sélectionnez **Applications cloud**. Étant donné que nous souhaitons protéger la messagerie Office 365 Exchange Online, nous allons la sélectionner en suivant ces étapes :
     
    1. Dans l’onglet **Inclure**, choisissez **Sélectionner les applications**.
    2. Choisissez **Sélectionner**. 
    3. Dans la liste des applications, sélectionnez **Office 365 Exchange Online**, puis choisissez **Sélectionner**. 
    4. Sélectionnez **Terminé**.
  
    ![Sélectionnez l’application Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  Sous **Affectations**, sélectionnez **Conditions** > **Plateformes d’appareils**.
     
    1. Sous **Configurer**, sélectionnez **Oui**.
    2. Dans l’onglet **Inclure**, sélectionnez **N'importe quel appareil**.
    1. Sélectionnez **Terminé**.
   
6.  Dans le volet **Intune**, sélectionnez **Applications clientes**.
     
    1. Sous **Configurer**, sélectionnez **Oui**.
    2. Sélectionnez **Applications mobiles et clients de bureau** et **Clients d'authentification modernes**.
    3. Décochez les autres cases.
    4. Sélectionnez **Terminé**, puis sélectionnez **Terminé** à nouveau.
    
    ![Sélectionnez l’application Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  Sous **Contrôles d’accès**, sélectionnez **Accorder**. 
     
    1. Dans le volet **Accorder**, sélectionnez **Accorder l’accès**.
    2. Sélectionnez **Exiger une authentification multifacteur**.
    4. Sélectionnez **Demander une application cliente approuvée**.
    5. Sous **Pour plusieurs contrôles**, sélectionnez **Demander tous les contrôles sélectionnés**. Ce paramètre garantit que les deux exigences que vous avez sélectionnées sont appliquées quand un appareil tente d’accéder à la messagerie.
    6. Choisissez **Sélectionner**.
     
    ![Sélectionnez l’application Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  Sous **Activer la stratégie**, sélectionnez **Activé**.
     
    ![Sélectionnez l’application Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  Sélectionnez **Créer**.

La stratégie d’accès conditionnel pour les clients d’authentification moderne est créée. Vous pouvez maintenant créer une stratégie pour les clients Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Créer une stratégie pour les clients Exchange Active Sync
1.  Dans Intune, sélectionnez **Accès conditionnel** > **Stratégies** > **Nouvelle stratégie**.
2.  Dans **Nom**, entrez **Stratégie de test pour les clients EAS**. 
3.  Sous **Affectations**, sélectionnez **Utilisateurs et groupes**. Dans l’onglet **Inclure**, sélectionnez **Tous les utilisateurs**, puis **Terminé**.

4.  Sous **Affectations**, sélectionnez **Applications cloud**. Sélectionnez la messagerie Office 365 Exchange Online avec ces étapes :
     
    1. Dans l’onglet **Inclure**, choisissez **Sélectionner les applications**.
    2. Choisissez **Sélectionner**. 
    3. Dans la liste des applications, sélectionnez **Office 365 Exchange Online**, puis choisissez **Sélectionner**. 
    4. Sélectionnez **Terminé**.

5.  Sous **Affectations**, sélectionnez **Conditions** > **Plateformes d’appareils**.
     
    1. Sous **Configurer**, sélectionnez **Oui**.
    2. Dans l’onglet **Inclure**, sélectionnez **N’importe quel appareil**, puis **Terminé**. 
    3. Sélectionnez **Terminé** à nouveau.

6.  Dans le volet **Intune**, sélectionnez **Applications clientes**.
     
    1. Sous **Configurer**, sélectionnez **Oui**.
    2. Sélectionnez **Applications mobiles et clients de bureau**.
    3. Sélectionnez **Clients Exchange ActiveSync** et **Appliquer la stratégie uniquement aux plateformes prises en charge**. 
    4. Décochez toutes les autres cases.
    5. Sélectionnez **Terminé**, puis sélectionnez **Terminé** à nouveau.
    
    ![Sélectionnez l’application Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  Sous **Contrôles d’accès**, sélectionnez **Accorder**. 
     
    1. Dans le volet **Accorder**, sélectionnez **Accorder l’accès**.
    4. Sélectionnez **Demander une application cliente approuvée**. Décochez toutes les autres cases.
    6. Choisissez **Sélectionner**.
     
    ![Sélectionnez l’application Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  Sous **Activer la stratégie**, sélectionnez **Activé**.

9.  Sélectionnez **Créer**.

Vos stratégies de protection des applications et l’accès conditionnel sont maintenant en place et prêts à être testés. 

## <a name="try-it-out"></a>Faîtes un essai
Avec les stratégies que vous avez créées,les appareils doivent s’inscrire dans Intune et utiliser l’application mobile Outlook pour accéder à la messagerie d’Office 365. Pour tester ce scénario sur un appareil iOS, essayez de vous connecter à Exchange Online à l’aide des informations d’identification d’un utilisateur dans votre locataire de test.
1. Pour tester sur un iPhone, accédez à **Paramètres** > **Mots de passe et comptes** > **Ajouter un compte** > **Exchange** .
2. Entrez l’adresse e-mail d’un utilisateur dans votre locataire de test, puis appuyez sur **Suivant**.
3. Appuyez sur **Se connecter**.
4. Entrez le mot de passe de l’utilisateur de test, puis appuyez sur **Se connecter**.
5. Le message **Plus d’informations sont nécessaires** s’affiche, ce qui signifie que vous êtes invité à configurer l’authentification multifacteur. Continuez et configurez une méthode de vérification supplémentaire.
6. Vous verrez ensuite un message indiquant que vous tentez d’ouvrir cette ressource avec une application qui n’a pas été approuvée par votre service informatique. Cela signifie que vous ne pouvez pas utiliser l’application de messagerie native. Annulez l’ouverture de session.
7.  Ouvrez l’application Outlook et sélectionnez **Paramètres** > **Ajouter un compte** > **Ajouter un compte de messagerie**.
8. Entrez l’adresse e-mail d’un utilisateur dans votre locataire de test, puis appuyez sur **Suivant**.
9. Appuyez sur **Se connecter avec Office 365**. Vous êtes invité à procéder à une inscription et à une authentification supplémentaires. Une fois connecté, vous pouvez tester les actions telles que couper, copier, coller et « Enregistrer sous ».

## <a name="clean-up-resources"></a>Nettoyer les ressources
Lorsque les stratégies de test ne sont plus nécessaires, vous pouvez les supprimer.
1. Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune.
2. Sélectionnez **Conformité de l’appareil** > **Stratégies**.
3. Dans la liste **Nom de la stratégie**, sélectionnez le menu contextuel (**...** ) pour votre stratégie de test, puis sélectionnez **Supprimer**. Sélectionnez **OK** pour confirmer.
4. Sélectionnez **Accès conditionnel** > **Stratégies**.
5. Dans la liste **Nom de la stratégie**, sélectionnez le menu contextuel (**...** ) pour chacune de vos stratégies de test, puis sélectionnez **Supprimer**. Cliquez sur **Oui** pour confirmer la suppression.

 ## <a name="next-steps"></a>Étapes suivantes 
Dans ce didacticiel, vous avez créé des stratégies de protection afin de limiter les actions d’un utilisateur avec l’application Outlook et vous avez créé des stratégies d’accès conditionnel pour exiger l’utilisation de l’application Outlook et de l’authentification multifacteur pour les clients d’authentification moderne. Pour en savoir plus sur l’utilisation d’Intune avec accès conditionnel pour protéger d’autres applications et services,consultez [Configurer l’accès conditionnel](conditional-access.md).
