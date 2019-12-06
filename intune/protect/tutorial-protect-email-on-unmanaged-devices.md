---
title: Didacticiel - Protéger la messagerie Exchange Online sur les appareils non gérés
titleSuffix: Microsoft Intune
description: Apprenez à sécuriser Office 365 Exchange Online avec les stratégies de protection des applications Intune et l’accès conditionnel Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 810a898a3b2d1981babc231f32ed386bde37a856
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465793"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutoriel : Protéger la messagerie Exchange Online sur les appareils non gérés

Apprenez en plus sur l’utilisation des stratégies de protection des applications avec un accès conditionnel pour protéger Exchange Online, même lorsque les appareils ne sont pas inscrits dans une solution de gestion des appareils comme Intune. Dans ce tutoriel, vous apprendrez à :

> [!div class="checklist"]
> * Créez une stratégie de protection des applications Intune pour l’application Outlook. Vous allez limiter ce que l’utilisateur peut faire avec les données de l’application en empêchant l’option « Enregistrer sous » et en restreignant les opérations couper, copier et coller.
> * Créer des stratégies d’accès conditionnel Azure Active Directory (Azure AD) qui donnent une autorisation exclusive à l’application Outlook pour accéder à la messagerie d’entreprise dans Exchange Online. Vous allez également exiger une authentification multifacteur (MFA) pour des clients d’authentification moderne, comme Outlook pour iOS et Android.

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin d’un locataire de test avec les abonnements suivants pour ce tutoriel :

- Azure Active Directory Premium ([essai gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Abonnement Intune ([essai gratuit](../fundamentals/free-trial-sign-up.md))
- Abonnement Office 365 Entreprise qui inclut Exchange ([essai gratuit](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Pour ce tutoriel, lorsque vous vous connectez au [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), connectez-vous comme [Administrateur général](../fundamentals/users-add.md#types-of-administrators) ou [Administrateur de service Intune](../fundamentals/users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte que vous avez utilisé est l’administrateur général.

## <a name="create-the-app-protection-policy"></a>Créer la stratégie de protection des applications

Pour ce didacticiel, nous allons configurer une stratégie de protection des applications Intune pour iOS pour l’application Outlook afin de mettre des protections en place au niveau de l’application. Nous allons exiger un code PIN pour ouvrir une application dans un contexte professionnel. Nous allons également limiter le partage des données entre les applications et empêcher l’enregistrement des données d’entreprise sur un emplacement personnel.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Applications** > **Stratégies de protection des applications** > **Créer une stratégie**, puis sélectionnez **iOS/iPadOS** pour la plateforme.

3. Sur la page **Bases**, configurez les paramètres suivants :

   - **Nom** : Entrez **test de la stratégie d’application Outlook**.
   - **Description** : Entrez **test de la stratégie d’application Outlook**.

   La valeur de **Plateforme** est définie sur votre choix précédent.

   Cliquez sur **Suivant** pour continuer.

4. La page **Applications** vous permet de choisir la façon dont vous souhaitez appliquer cette stratégie aux applications sur différents appareils. Configurez les options suivantes :

   - Pour **Cibler sur tous les types d’application** : Sélectionnez **Non**, puis pour **Types d’application**, cochez la case **Applications sur les appareils non gérés**.
   - Cliquez sur **Sélectionner les applications publiques**. Dans la liste des applications, sélectionnez **Outlook**, puis choisissez **Sélectionner**.  Outlook apparaît désormais sous *Applications publiques*.

   Cliquez sur **Suivant** pour continuer.

5. La page **Protection des données** fournit des paramètres qui déterminent la manière dont les utilisateurs interagissent avec les données dans les applications auxquelles cette stratégie de protection d’applications s’applique. Configurez les options suivantes :

   Sous *Transfert de données*, configurez les paramètres suivants, en conservant les valeurs par défaut de tous les autres paramètres :

   - Pour **Envoyer les données d’organisation à d’autres applications**, sélectionnez **Aucune**.  
   - Pour **Recevoir des données d’autres applications**, sélectionnez **Aucune**.  
   - Pour **Enregistrer des copies des données d’organisation**, sélectionnez **Bloquer**.  
   - Pour **Limiter les opérations couper, copier et coller entre les autres applications**, sélectionnez **Bloqué**. 

   ![Sélectionner les paramètres de réadressage des données de la stratégie de protection de l’application Outlook](./media/tutorial-protect-email-on-unmanaged-devices/data-protection-settings.png)

   Sélectionnez **Suivant** pour continuer.

6. La page **Conditions d’accès** fournit des paramètres qui vous permettent de configurer les exigences en matière de code confidentiel et d’informations d’identification que les utilisateurs doivent remplir pour accéder aux applications dans un contexte professionnel. Configurez les paramètres suivants, en conservant les valeurs par défaut de tous les autres paramètres :

   - Pour **Accès par code PIN**, sélectionnez **Exiger**.
   - Pour **Informations d’identification du compte professionnel ou scolaire pour l’accès**, sélectionnez **Exiger**.

   ![Sélectionner les actions d’accès de stratégie de protection de l’application Outlook](./media/tutorial-protect-email-on-unmanaged-devices/access-requirements-settings.png)

   Sélectionnez **Suivant** pour continuer.

7. La page **Lancement conditionnel** fournit des paramètres permettant de définir les exigences de sécurité de connexion pour votre stratégie de protection d’applications. Pour ce tutoriel, vous n’avez pas besoin de configurer ces paramètres.

   Cliquez sur **Suivant** pour continuer.

8. Utilisez la page **Attributions** pour attribuer la stratégie de protection des applications à des groupes d’utilisateurs. Pour ce tutoriel, vous n’affectez pas cette stratégie à un groupe.  
 Vous n’avez pas besoin de configurer ces paramètres.

   Cliquez sur **Suivant** pour continuer.

9. Sur la page **Suivant : Vérifier + créer**, vérifiez les valeurs et les paramètres que vous avez entrés pour cette stratégie de protection des applications. Cliquez sur **Créer** pour créer la stratégie de protection des applications dans Intune.

La stratégie de protection d’application pour Outlook est créée. Ensuite, vous allez configurer l’accès conditionnel pour exiger que les appareils utilisent l’application Outlook.

## <a name="create-conditional-access-policies"></a>Créer des stratégies d’accès conditionnel

Nous allons maintenant créer deux stratégies d’accès conditionnel pour couvrir toutes les plateformes d’appareils.  

- La première stratégie exige les clients d’authentification moderne utilisent l’application Outlook approuvée et l’authentification multifacteur (MFA). Les clients d’authentification moderne incluent Outlook pour iOS et Outlook pour Android.  

- La seconde stratégie exige que les clients Exchange ActiveSync utilisent l’application Outlook approuvée. (Actuellement, Exchange Active Sync ne prend pas en charge d’autres conditions que la plateforme de l’appareil). Vous pouvez configurer les stratégies d’accès conditionnel depuis le portail Azure AD ou le portail Intune. Étant donné que nous sommes déjà dans le portail Intune, nous allons créer la stratégie ici.  

### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Créer une stratégie d’authentification Multifacteur pour les clients de l’authentification moderne  

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Sécurité des points de terminaison** >  **Accès conditionnel** > **Nouvelle stratégie**.  

3. Pour **Nom**, entrez **Stratégie de test pour les clients d’authentification moderne**.  

4. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**. Dans l’onglet **Inclure**, sélectionnez **Tous les utilisateurs**, puis **Terminé**.

5. Sous **Affectations**, sélectionnez **Applications ou actions cloud**. Étant donné que nous souhaitons protéger la messagerie Office 365 Exchange Online, nous allons la sélectionner en suivant ces étapes :

   1. Dans l’onglet **Inclure**, choisissez **Sélectionner les applications**.
   2. Choisissez **Sélectionner**.
   3. Dans la liste des applications, sélectionnez **Office 365 Exchange Online**, puis choisissez **Sélectionner**.
   4. Sélectionnez **Terminé** pour revenir au volet Nouvelle stratégie.

   ![Sélectionnez l’application Office 365 Exchange Online](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

6. Sous **Affectations**, sélectionnez **Conditions** > **Plateformes d’appareils**.

   1. Sous **Configurer**, sélectionnez **Oui**.
   2. Dans l’onglet **Inclure**, sélectionnez **N'importe quel appareil**.
   3. Sélectionnez **Terminé**.

7. Dans le volet **Intune**, sélectionnez **Applications clientes**.

   1. Sous **Configurer**, sélectionnez **Oui**.
   2. Sélectionnez **Applications mobiles et clients de bureau** et **Clients d'authentification modernes**.
   3. Décochez les autres cases.
   4. Sélectionnez **Terminé** > **Terminé** pour revenir au volet Nouvelle stratégie.

   ![Sélectionner les applications mobiles et les clients](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

8. Sous **Contrôles d’accès**, sélectionnez **Accorder**.

   1. Dans le volet **Accorder**, sélectionnez **Accorder l’accès**.
   2. Sélectionnez **Exiger une authentification multifacteur**.
   3. Sélectionnez **Demander une application cliente approuvée**.
   4. Sous **Pour plusieurs contrôles**, sélectionnez **Demander tous les contrôles sélectionnés**. Ce paramètre garantit que les deux exigences que vous avez sélectionnées sont appliquées quand un appareil tente d’accéder à la messagerie.
   5. Choisissez **Sélectionner**.

   ![Sélectionner les contrôles d’accès](./media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

9. Sous **Activer la stratégie**, sélectionnez **Activé**, puis sélectionnez **Créer**.

   ![Créer une stratégie](./media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)  

La stratégie d’accès conditionnel pour les clients d’authentification moderne est créée. Vous pouvez maintenant créer une stratégie pour les clients Exchange Active Sync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Créer une stratégie pour les clients Exchange Active Sync

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Sécurité des points de terminaison** > **Accès conditionnel** > **Nouvelle stratégie**.

3. Pour **Nom**, entrez **Stratégie de test pour les clients EAS**.

4. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**. Dans l’onglet *Inclure*, sélectionnez **Tous les utilisateurs**, puis **Terminé**.

5. Sous **Affectations**, sélectionnez **Applications ou actions cloud**. Sélectionnez la messagerie Office 365 Exchange Online avec ces étapes :

   1. Dans l’onglet *Inclure*, choisissez **Sélectionner les applications**.
   2. Choisissez **Sélectionner**.
   3. Dans la liste des *applications*, sélectionnez **Office 365 Exchange Online**, choisissez **Sélectionner**, puis **Terminé**.
  
6. Sous **Affectations**, sélectionnez **Conditions** > **Plateformes d’appareils**.

   1. Sous **Configurer**, sélectionnez **Oui**.
   2. Dans l’onglet **Inclure**, sélectionnez **N’importe quel appareil**, puis **Terminé**.

7. Dans le volet **Intune**, sélectionnez **Applications clientes**.

   1. Sous **Configurer**, sélectionnez **Oui**.
   2. Sélectionnez **Applications mobiles et clients de bureau**.
   3. Sélectionnez **Clients Exchange ActiveSync** et **Appliquer la stratégie uniquement aux plateformes prises en charge**.  
   4. Décochez toutes les autres cases.  
   5. Sélectionnez **Terminé**, puis sélectionnez **Terminé** à nouveau.  

   ![Appliquer aux plateformes prises en charge](./media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)  

8. Sous **Contrôles d’accès**, sélectionnez **Accorder**.

   1. Dans le volet **Accorder**, sélectionnez **Accorder l’accès**.
   2. Sélectionnez **Demander une application cliente approuvée**. Décochez toutes les autres cases.
   3. Choisissez **Sélectionner**.

   ![Demander une application cliente approuvée](./media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

9. Sous **Activer la stratégie**, sélectionnez **Activé**, puis sélectionnez **Créer**.

Vos stratégies de protection des applications et l’accès conditionnel sont maintenant en place et prêts à être testés.

## <a name="try-it-out"></a>Faîtes un essai

Avec les stratégies que vous avez créées,les appareils doivent s’inscrire dans Intune et utiliser l’application mobile Outlook pour accéder à la messagerie d’Office 365. Pour tester ce scénario sur un appareil iOS, essayez de vous connecter à Exchange Online à l’aide des informations d’identification d’un utilisateur dans votre locataire de test.

1. Pour tester sur un iPhone, accédez à **Paramètres** > **Mots de passe et comptes** > **Ajouter un compte** > **Exchange** .

2. Entrez l’adresse e-mail d’un utilisateur dans votre locataire de test, puis appuyez sur **Suivant**.  
3. Appuyez sur **Se connecter**.

4. Entrez le mot de passe de l’utilisateur de test, puis appuyez sur **Se connecter**.

5. Le message **Plus d’informations sont nécessaires** s’affiche, ce qui signifie que vous êtes invité à configurer l’authentification multifacteur. Continuez et configurez une méthode de vérification supplémentaire.

6. Vous verrez ensuite un message indiquant que vous tentez d’ouvrir cette ressource avec une application qui n’a pas été approuvée par votre service informatique. Ce message signifie que vous ne pouvez pas utiliser l’application de messagerie native. Annulez l’ouverture de session.

7. Ouvrez l’application Outlook et sélectionnez **Paramètres** > **Ajouter un compte** > **Ajouter un compte de messagerie**.

8. Entrez l’adresse e-mail d’un utilisateur dans votre locataire de test, puis appuyez sur **Suivant**.

9. Appuyez sur **Se connecter avec Office 365**. Vous êtes invité à procéder à une inscription et à une authentification supplémentaires. Une fois connecté, vous pouvez tester les actions telles que couper, copier, coller et « Enregistrer sous ».

## <a name="clean-up-resources"></a>Nettoyer les ressources

Lorsque les stratégies de test ne sont plus nécessaires, vous pouvez les supprimer.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** **Stratégies de conformité**.

3. Dans la liste **Nom de la stratégie**, sélectionnez le menu contextuel ( **...** ) pour votre stratégie de test, puis sélectionnez **Supprimer**. Sélectionnez **OK** pour confirmer.

4. Sélectionnez **Sécurité des points de terminaison** > **Accès conditionnel**.

5. Dans la liste **Nom de la stratégie**, sélectionnez le menu contextuel ( **...** ) pour chacune de vos stratégies de test, puis sélectionnez **Supprimer**. Cliquez sur **Oui** pour confirmer la suppression.

## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez créé des stratégies de protection afin de limiter les actions d’un utilisateur avec l’application Outlook et vous avez créé des stratégies d’accès conditionnel pour exiger l’utilisation de l’application Outlook et de l’authentification multifacteur pour les clients d’authentification moderne. Pour en savoir plus sur l’utilisation d’Intune avec accès conditionnel pour protéger d’autres applications et services, consultez [Configurer l’accès conditionnel](conditional-access.md).
