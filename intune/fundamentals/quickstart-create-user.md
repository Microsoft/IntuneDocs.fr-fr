---
title: Démarrage rapide - Créer un utilisateur dans Intune
description: Démarrage rapide - Créer un utilisateur dans Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754488"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>Démarrage rapide : Créer un utilisateur dans Intune et lui attribuer une licence

Dans ce guide de démarrage rapide, vous créez un utilisateur et lui attribuez une licence Intune. Dans Intune, chaque personne devant accéder aux données d’entreprise doit avoir son propre compte d’utilisateur. Les administrateurs Intune peuvent configurer les utilisateurs pour gérer le contrôle d’accès.

## <a name="prerequisites"></a>Prérequis

- Abonnement Microsoft Intune. [Inscrivez-vous à un compte d’évaluation gratuite](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Se connecter à Intune dans le Gestionnaire de points de terminaison Microsoft

Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) comme [Administrateur général ou Administrateur de service Intune](users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte que vous avez utilisé est l’administrateur général.

## <a name="create-a-user"></a>Créer un utilisateur

Un utilisateur qui souhaite s’inscrire à la gestion des appareils Intune doit avoir un compte d’utilisateur. Pour créer un utilisateur :

1. Dans le Gestionnaire de points de terminaison Microsoft, sélectionnez **Utilisateurs** > **Tous les utilisateurs** > **Nouvel utilisateur** :  ![Dans le Gestionnaire de points de terminaison Microsoft, sélectionnez Nouvel utilisateur](./media/quickstart-create-user/create-user.png)
2. Dans la zone **Nom**, entrez un nom, tel que *Fabrice Canel* :  ![Ajouter les détails de l'utilisateur](./media/quickstart-create-user/create-user-02.png)
3. Dans la zone **Nom d’utilisateur**, entrez un identificateur d’utilisateur, tel que Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Si vous n’avez pas configuré votre nom de domaine de client, utilisez le nom de domaine vérifié que vous avez utilisé pour créer l’abonnement Intune (ou un [essai gratuit](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Sélectionnez **Afficher le mot de passe** et veillez à mémoriser le mot de passe généré automatiquement pour pouvoir l’utiliser et vous connecter à un appareil de test.
5. Sélectionnez **Créer**.

## <a name="assign-a-license-to-the-user"></a>Affecter une licence à l’utilisateur

Après avoir créé un utilisateur, vous devez utiliser le [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) pour lui attribuer une licence Intune. Si vous n’attribuez pas de licence à l’utilisateur, il ne peut pas inscrire son appareil dans Intune.

Pour attribuer une licence Intune à un compte d’utilisateur :

1. Connectez-vous au [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) avec les mêmes informations d’identification que celles utilisées pour vous connecter à Intune.
2. Sélectionnez **Utilisateurs** > **Utilisateurs actifs**, puis sélectionnez l’utilisateur que vous venez de créer.
3. Sélectionnez l'onglet **Licences et applications**.
4. Sous **Sélectionner l’emplacement**, choisissez un emplacement pour l'utilisateur, s'il n'est pas déjà défini.
2. Cochez la case **Intune** dans la section **Licences**. Si une autre licence inclut Intune, vous pouvez sélectionner cette licence. Le [nom de produit](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) affiché est utilisé comme plan de service dans la gestion Azure.

    ![Sélectionner l’emplacement et la licence Intune](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Ce paramètre utilise l’une de vos licences pour l’utilisateur. Si vous utilisez un environnement d’essai, vous réattribuerez ultérieurement cette licence à un utilisateur réel dans un environnement de production.

6. Sélectionnez **Enregistrer les modifications**.

Le nouvel utilisateur Intune actif apparaît à présent comme utilisant une licence **Intune**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n'avez plus besoin de cet utilisateur, vous pouvez le supprimer en accédant au [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) et en sélectionnant **Utilisateurs** > *l’utilisateur* > *l’icône Supprimer un utilisateur* > **Supprimer un utilisateur** > **Fermer**.

   ![Sélectionner l'icône de suppression](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un utilisateur auquel vous avez attribué une licence Intune. Pour plus d’informations sur l’ajout d’utilisateurs dans Intune, consultez [Ajouter des utilisateurs et accorder une autorisation d’administration dans Intune](users-add.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au guide suivant :

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer un groupe pour gérer les utilisateurs](../quickstart-create-group.md)
