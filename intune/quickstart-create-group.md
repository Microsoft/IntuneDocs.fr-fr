---
title: Démarrage rapide - Créer un groupe pour gérer les utilisateurs
titleSuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour créer un groupe basé sur des utilisateurs existants.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/25/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a9cf1b610830928a753be176de2643fa1826bd0
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050325"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Démarrage rapide : Créer un groupe pour gérer les utilisateurs

Dans ce guide de démarrage rapide, vous allez utiliser Intune pour créer un groupe basé sur un utilisateur existant. Les groupes permettent de gérer vos utilisateurs et de contrôler l’accès des employés aux ressources de votre entreprise. Ces ressources peuvent faire partie de l’intranet de votre entreprise ou correspondre à des ressources externes, par exemple des sites SharePoint, des applications SaaS ou des applications web.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

>[!NOTE]
>Intune fournit des groupes **Tous les utilisateurs** et **Tous les appareils** précréés dans la console avec des optimisations intégrées pour votre commodité.

## <a name="prerequisites"></a>Prérequis

- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez [créer un utilisateur](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au [portail Intune](https://aka.ms/intuneportal) comme [administrateur général ou administrateur de service Intune](users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="create-a-group"></a>Créer un groupe

Vous allez créer un groupe que vous utiliserez dans cette série de guides de démarrage rapide. Pour créer un groupe :

1. Une fois que vous avez ouvert le volet **Microsoft Intune**, sélectionnez **Groupes** > **Nouveau groupe**.
2. Dans la zone déroulante **Type de groupe**, sélectionnez **Sécurité**.
3. Dans le champ **Nom du groupe** , entrez le nom du nouveau groupe (par exemple, **Contoso testeurs**).
4. Ajoutez une **Description** du groupe.
5. Définissez **Type d’appartenance** sur **Affecté**. 
6. Cliquez sur **Membres**, puis sélectionnez un ou plusieurs membres du groupe dans la liste.

    ![Capture d’écran de création d’un groupe dans Microsoft Intune](./media/quickstart-use-groups-01.png)

7. Cliquez sur **Sélectionner** > **Créer**.

Une fois le groupe créé, il apparaît dans la liste **Tous les groupes**. 

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez utilisé Intune pour créer un groupe basé sur un utilisateur existant. Pour plus d’informations sur l’ajout de groupes dans Intune, consultez [Ajouter des groupes pour organiser des utilisateurs et des appareils](groups-add.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Configurer l’inscription automatique pour les appareils Windows 10](quickstart-setup-auto-enrollment.md)
