---
title: 'Tutoriel : Protéger la messagerie Exchange Online sur les appareils gérés'
titleSuffix: Microsoft Intune
description: Apprenez à sécuriser Exchange Online avec les stratégies de conformité iOS Intune et l’accès conditionnel Azure AD pour exiger des appareils gérés et l’application Outlook.
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
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c134eb1fc413a32f2a27034d8c3a993f18f8a9c9
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576277"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Tutoriel : Protéger la messagerie Exchange Online sur les appareils gérés

Découvrez l’utilisation des stratégies de conformité des appareils avec accès conditionnel pour vous assurer que les appareils iOS peuvent accéder à la messagerie Exchange Online uniquement s’ils sont gérés par Intune et à l’aide d’une application de messagerie approuvée.

Dans ce tutoriel, vous apprendrez à :

> [!div class="checklist"]
> * Créer une stratégie de conformité d’appareil Intune iOS pour définir les conditions qu’un appareil doit respecter pour être considéré comme conforme.
> * Créer une stratégie d’accès conditionnel Azure Active Directory (Azure AD) qui nécessite que les appareils iOS soient inscrits dans Intune, conformes aux stratégies Intune et utilisent l’application mobile Outlook approuvée pour accéder à la messagerie Exchange Online.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin d’un locataire de test avec les abonnements suivants pour ce tutoriel :

- Azure Active Directory Premium ([essai gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))

- Abonnement Office 365 Entreprise qui inclut Exchange ([essai gratuit](https://go.microsoft.com/fwlink/p/?LinkID=510938))

Avant de commencer, créez un profil d’appareil de test pour les appareils iOS en suivant les étapes décrites dans [Démarrage rapide : Créer un profil d’appareil de messagerie pour iOS/iPadOS](../configuration/quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) comme [Administrateur général](../fundamentals/users-add.md#types-of-administrators) ou [Administrateur de service Intune](../fundamentals/users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="create-the-ios-device-compliance-policy"></a>Créer la stratégie de conformité des appareils iOS

Configurez une stratégie de conformité d’appareil Intune pour définir les conditions qu’un appareil doit respecter pour être considéré comme conforme. Pour ce tutoriel, nous allons créer une stratégie de conformité pour des appareils iOS. Les stratégies de conformité sont spécifiques à la plateforme, donc vous avez besoin d’une stratégie de conformité distincte pour chaque plateforme d’appareil que vous souhaitez évaluer.

1. Dans Intune, sélectionnez **Appareils** > **Stratégies de conformité** > **Créer une stratégie**.

2. Dans le champ **Nom**, entrez **Test de stratégie de conformité iOS**.

3. Dans le champ **Description**, entrez **Test de stratégie de conformité iOS**.

4. Pour l’option **Plateforme**, sélectionnez **iOS/iPadOS**.

5. Sélectionnez **Paramètres** > **E-mail**.

   1. En regard de **Exiger que les appareils mobiles aient un profil de messagerie géré**, sélectionnez **Exiger**.

   2. Sélectionnez **OK**.

   ![Définir la stratégie de conformité e-mail pour exiger un profil de messagerie géré](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)

6. Sélectionnez **Intégrité de l’appareil**. En regard de **Appareils jailbreakés**, sélectionnez **Bloquer**, puis sélectionnez **OK**.

7. Sélectionnez **Sécurité du système** et entrez les paramètres **Mot de passe**. Pour ce tutoriel, sélectionnez les paramètres recommandés suivants :

   - Pour **Exiger un mot de passe pour déverrouiller des appareils mobiles**, sélectionnez **Exiger**.

   - Pour **Mots de passe simples**, sélectionnez **Bloquer**.

   - Pour **Longueur minimale du mot de passe**, entrez **4**.

     > [!TIP]
     > Les valeurs par défaut grisées et en italique sont uniquement des recommandations. Vous devez remplacer les valeurs qui sont des recommandations pour configurer un paramètre.

   - Pour **Type de mot de passe requis**, choisissez **Alphanumérique**.

   - Pour **Nombre maximal de minutes après le verrouillage d’écran avant que le mot de passe ne soit obligatoire**, choisissez **Immédiatement**.

   - Pour **Expiration du mot de passe (jours)** , entrez **41**.

   - Pour **Nombre de mots de passe précédents pour empêcher la réutilisation**, entrez **5**.
 
   ![Définir les paramètres de mot de passe pour la stratégie de conformité e-mail](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Sélectionnez **OK**, puis **OK** à nouveau.

9. Sélectionnez **Créer**.

## <a name="create-the-conditional-access-policy"></a>Créer la stratégie d'accès conditionnel

Nous allons maintenant créer une stratégie d’accès conditionnel qui requiert que toutes les plateformes d’appareils soient inscrites dans Intune et respectent notre stratégie de conformité Intune pour accéder à Exchange Online. Nous allons également avoir besoin de l’application Outlook pour l’accès à la messagerie. Les stratégies d’accès conditionnel sont configurables dans le portail Azure AD ou le portail Intune. Étant donné que nous sommes déjà dans le portail Intune, nous allons créer la stratégie ici.

1. Dans Intune, sélectionnez **Sécurité des points de terminaison** > **Accès conditionnel** > **Nouvelle stratégie**.

2. Pour **Nom**, entrez **Stratégie de test pour la messagerie Office 365**.

3. Sous **Affectations**, sélectionnez **Utilisateurs et groupes**. Dans l’onglet **Inclure**, sélectionnez **Tous les utilisateurs**, puis **Terminé**.

4. Sous **Affectations**, sélectionnez **Applications ou actions cloud**. Étant donné que nous souhaitons protéger la messagerie Office 365 Exchange Online, nous allons la sélectionner en suivant ces étapes :

   1. Dans l’onglet **Inclure**, choisissez **Sélectionner les applications**.

   2. Choisissez **Sélectionner**. 

   3. Dans la liste des applications, sélectionnez **Office 365 Exchange Online**, puis choisissez **Sélectionner**. 

   4. Sélectionnez **Terminé**.
  
   ![Sélectionnez l’application Office 365 Exchange Online](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. Sous **Affectations**, sélectionnez **Conditions** > **Plateformes d’appareils**.

   1. Sous **Configurer**, sélectionnez **Oui**.

   2. Dans l’onglet **Inclure**, sélectionnez **N’importe quel appareil**, puis **Terminé**. 

   3. Sélectionnez **Terminé** à nouveau.

   ![Inclure un appareil](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. Sous **Affectations**, sélectionnez **Conditions** > **Applications clientes**.

   1. Sous **Configurer**, sélectionnez **Oui**.

   2. Pour ce tutoriel, sélectionnez **Applications mobiles et clients de bureau** et **Clients d'authentification moderne** (qui fait référence aux applications comme Outlook pour iOS et Outlook pour Android). Décochez toutes les autres cases.

   3. Sélectionnez **Terminé**, puis sélectionnez **Terminé** à nouveau.

   ![Sélectionner les applications et clients](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. Sous **Contrôles d’accès**, sélectionnez **Accorder**.

   1. Dans le volet **Accorder**, sélectionnez **Accorder l’accès**.

   2. Sélectionnez **Exiger que l'appareil soit marqué comme conforme**.

   3. Sélectionnez **Demander une application cliente approuvée**.

   4. Sous **Pour plusieurs contrôles**, sélectionnez **Demander tous les contrôles sélectionnés**. Ce paramètre garantit que les deux exigences que vous avez sélectionnées sont appliquées quand un appareil tente d’accéder à la messagerie.

   5. Choisissez **Sélectionner**.

   ![Contrôles de sélection](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. Sous **Activer la stratégie**, sélectionnez **Activé**.

   ![Activer la stratégie](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Sélectionnez **Créer**.

## <a name="try-it-out"></a>Faites un essai

Avec les stratégies que vous avez créées, n’importe quel appareil iOS qui tente de se connecter à la messagerie Office 365 devra s’inscrire dans Intune et utiliser l’application mobile Outlook pour iOS/iPadOS. Pour tester ce scénario sur un appareil iOS, essayez de vous connecter à Exchange Online à l’aide des informations d’identification d’un utilisateur dans votre locataire de test. Vous serez invité à inscrire l’appareil et à installer l’application mobile Outlook.

1. Pour tester sur un iPhone, accédez à **Paramètres** > **Mots de passe et comptes** > **Ajouter un compte** > **Exchange** .

2. Entrez l’adresse e-mail d’un utilisateur dans votre locataire de test, puis appuyez sur **Suivant**.

3. Appuyez sur **Se connecter**.

4. Entrez le mot de passe de l’utilisateur de test, puis appuyez sur **Se connecter**.

5. Un message s’affiche indiquant que votre appareil doit être géré pour accéder à la ressource, accompagné d’une option pour vous inscrire.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Lorsque les stratégies de test ne sont plus nécessaires, vous pouvez les supprimer.
1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) comme Administrateur général ou Administrateur de service Intune.

2. Sélectionnez **Appareils** > **Stratégies de conformité**.

3. Dans la liste **Nom de la stratégie**, sélectionnez le menu contextuel ( **...** ) pour votre stratégie de test, puis sélectionnez **Supprimer**. Sélectionnez **OK** pour confirmer.

4. Sélectionnez **Sécurité des points de terminaison** > **Accès conditionnel**.

5. Dans la liste **Nom de la stratégie**, sélectionnez le menu contextuel ( **...** ) pour votre stratégie de test, puis sélectionnez **Supprimer**. Cliquez sur **Oui** pour confirmer la suppression.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé des stratégies qui exigent que les appareils iOS s’inscrivent dans Intune et utilisent l’application Outlook pour accéder à la messagerie Exchange Online. Pour en savoir plus sur l’utilisation d’Intune avec accès conditionnel pour protéger d’autres applications et services, notamment les clients Exchange ActiveSync pour Office 365 Exchange Online, consultez [Configurer l’accès conditionnel](conditional-access.md).
