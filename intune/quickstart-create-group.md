---
title: Démarrage rapide - Créer un groupe pour gérer les utilisateurs
titlesuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour créer un groupe basé sur des utilisateurs existants.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581661"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Démarrage rapide : Créer un groupe pour gérer les utilisateurs

Dans ce guide de démarrage rapide, vous allez utiliser Intune pour créer un groupe basé sur un utilisateur existant. Les groupes permettent de gérer vos utilisateurs et de contrôler l’accès des employés aux ressources de votre entreprise. Ces ressources peuvent faire partie de l’intranet de votre entreprise ou correspondre à des ressources externes, par exemple des sites SharePoint, des applications SaaS ou des applications web.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

>[!NOTE]
>Intune fournit des groupes **Tous les utilisateurs** et **Tous les appareils** précréés dans la console avec des optimisations intégrées pour votre commodité.

## <a name="prerequisites"></a>Prérequis

- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez [créer un utilisateur](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune. Pour accéder à Intune dans le Portail Azure, choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.

## <a name="create-a-group"></a>Créer un groupe
1. Une fois que vous avez ouvert le volet **Microsoft Intune**, sélectionnez **Groupes** > **Nouveau groupe**.
2. Dans le volet **Groupe**, sélectionnez **Type de groupe** > **Sécurité**.
3. Dans **Nom**, indiquez « Testeurs Contoso », puis ajoutez une **Description** pour le groupe.
4. Sélectionnez **Affecté** comme **Type d’appartenance**. 
5. Cliquez sur **Membres**, puis sélectionnez les **Membres** du groupe dans la liste existante.

    ![Capture d’écran de création d’un groupe dans Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Cliquez sur **Sélectionner**.
7. Cliquez sur **Create (Créer)**.

Si vous avez réussi à créer le groupe, il apparaît dans la liste **Tous les groupes**. 

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez utilisé Intune pour créer un groupe basé sur un utilisateur existant.

> [!div class="nextstepaction"]
> [Créer une stratégie de conformité des appareils](quickstart-create-policy.md)
