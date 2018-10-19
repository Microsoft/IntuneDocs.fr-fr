---
title: Démarrage rapide - Créer un utilisateur dans Intune
description: Démarrage rapide - Créer un utilisateur dans Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581673"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Démarrage rapide : Créer un utilisateur et lui affecter une licence

Dans ce guide de démarrage rapide, vous allez créer un utilisateur, puis lui affecter une licence. Avec Intune, chaque personne pour laquelle vous souhaitez accéder aux données d’entreprise doit avoir un compte d’utilisateur. Les administrateurs Intune peuvent ensuite configurer ces utilisateurs pour gérer le contrôle d’accès.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune.

## <a name="create-a-user"></a>Créer un utilisateur

Toute personne qui souhaite s’inscrire à la gestion des appareils Intune doit avoir un compte d’utilisateur.

1. Dans Intune, choisissez **Utilisateurs** > **Tous les utilisateurs** > **Nouvel utilisateur**.
![Navigateur](media/quickstart-create-user/create-user.png)
2. Dans la zone **Nom**, entrez *Fabrice Canel*.
3. Dans la zone **Nom d’utilisateur**, entrez *Dewey@contoso.onmicrosoft.com*.
4. Choisissez **Groupes** > **Tout le monde** > **Sélectionner**.
5. Choisissez **Afficher le mot de passe**, puis notez le mot de passe généré automatiquement pour pouvoir l’utiliser et vous connecter à un appareil de test.
6. Choisissez **Créer**.

## <a name="assign-a-license-to-the-user"></a>Affecter une licence à l’utilisateur

Après avoir créé un utilisateur, vous devez utiliser le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) pour lui affecter une licence Intune. Si vous ne lui affectez pas de licence, il ne peut pas inscrire son appareil dans Intune. 

1. Connectez-vous au [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) avec les mêmes informations d’identification que celles utilisées pour vous connecter à Intune.
2. Choisissez **Utilisateurs** > **Utilisateurs actifs** > choisissez l’utilisateur que vous venez de créer.
3. Sous **Emplacement**, choisissez un emplacement pour l’utilisateur.
3. Choisissez **Licences des produits**, puis affectez à **Enterprise Mobility + Security E3** (ou une autre de vos licences incluant Intune) la valeur **Activé**.
   > [!NOTE]
   > Cela utilise l’une de vos licences pour cet utilisateur. Si vous utilisez votre environnement en production, vous pourrez désactiver l’utilisation de cette licence plus tard pour la réaffecter à un utilisateur réel.
5. Choisissez **Enregistrer**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’avez plus besoin de cet utilisateur, vous pouvez le supprimer en choisissant **Utilisateurs** > **Tous les utilisateurs** > choisissez l’utilisateur dans la liste > **Supprimer l’utilisateur** > **Oui**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un utilisateur auquel vous avez affecté une licence. Vous pouvez maintenant affecter cet utilisateur à un groupe.

> [!div class="nextstepaction"]
> [Créer un groupe](quickstart-create-group.md)
