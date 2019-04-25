---
title: Démarrage rapide - Créer un utilisateur dans Intune
description: Démarrage rapide - Créer un utilisateur dans Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: b49595493b5db3e5735e0a4717c27e91f058b8d8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511361"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Démarrage rapide : Créer un utilisateur dans Intune et lui attribuer une licence

Dans ce guide de démarrage rapide, vous allez créer un utilisateur, puis lui attribuer une licence Intune. Avec Intune, chaque personne devant accéder aux données d’entreprise doit avoir son propre compte d’utilisateur. Les administrateurs Intune peuvent configurer les utilisateurs pour gérer le contrôle d’accès.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’[administrateur général ou en tant qu’administrateur de services fédérés Intune](users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="create-a-user"></a>Créer un utilisateur

Les utilisateurs qui souhaitent s’inscrire à la gestion des appareils Intune doit avoir un compte d’utilisateur. Pour créer un utilisateur :

1. Dans Intune, choisissez **Utilisateurs** > **Tous les utilisateurs** > **Nouvel utilisateur**.
![Navigateur](media/quickstart-create-user/create-user.png)
2. Dans la zone **Nom**, entrez un nom, tel que *Fabrice Canel*.
3. Dans la zone **Nom d’utilisateur**, entrez un identificateur d’utilisateur, tel que Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Si vous n’avez pas configuré votre nom de domaine de client, utilisez le nom de domaine vérifié que vous avez utilisé pour créer l’abonnement Intune (ou un [essai gratuit](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Choisissez **Afficher le mot de passe**, puis notez le mot de passe généré automatiquement pour pouvoir l’utiliser et vous connecter à un appareil de test.
5. Choisissez **Créer**.

## <a name="assign-a-license-to-the-user"></a>Affecter une licence à l’utilisateur

Après avoir créé un utilisateur, vous devez utiliser le [Centre d’administration Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) pour lui attribuer une licence Intune. Si vous n’attribuez pas de licence à l’utilisateur, il ne pourra pas inscrire son appareil dans Intune. 

Pour attribuer une licence Intune à un compte d’utilisateur :

1. Connectez-vous au [Centre d’administration Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) avec les mêmes informations d’identification que celles utilisées pour vous connecter à Intune.
2. Choisissez **Utilisateurs** > **Utilisateurs actifs** > et choisissez l’utilisateur que vous venez de créer.
3. En regard de **Licences des produits**, sélectionnez **Modifier**.
4. Sous **Emplacement**, choisissez un emplacement pour l’utilisateur.
5. Cliquez sur **Activé** en regard de la licence Intune (ou d’une autre de vos licences incluant Intune). Le [nom de produit](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** affiché est utilisé comme plan de service dans la gestion Azure. 

   > [!NOTE]
   > Ce paramètre utilise l’une de vos licences pour cet utilisateur. Si vous utilisez un environnement d’essai, vous réattribuez ultérieurement cette licence à un utilisateur réel dans un environnement de production.
6. Choisissez **Enregistrer** > **Fermer**.

Le nouvel utilisateur Intune actif apparaît à présent comme utilisant une licence **Intune**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’avez plus besoin de cet utilisateur, vous pouvez le supprimer ; accédez au [Centre d’administration Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), choisissez **Utilisateurs** > **Utilisateurs actifs** > *choisissez l’utilisateur dans la liste* > **Supprimer l’utilisateur** > **Supprimer l’utilisateur** > **Confirmer les modifications** > **Fermer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un utilisateur auquel vous avez attribué une licence Intune. Pour plus d’informations sur l’ajout d’utilisateurs dans Intune, consultez [Ajouter des utilisateurs et accorder une autorisation d’administration dans Intune](users-add.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer un groupe pour gérer les utilisateurs](quickstart-create-group.md)
