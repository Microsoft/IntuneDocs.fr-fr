---
title: 'Démarrage rapide : ajouter et attribuer une application cliente'
titleSuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour ajouter et attribuer une application cliente.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dab6f5c8-1ebb-42c4-a7a7-7af001f94e15
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c5a6b35f7f051ff3060976c12abad1c1e4e7131
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724644"
---
# <a name="quickstart-add-and-assign-a-client-app"></a>Démarrage rapide : ajouter et attribuer une application cliente

Dans ce guide de démarrage rapide, vous allez utiliser Intune pour ajouter une application cliente et l’attribuer au personnel de votre entreprise. L’une des priorités d’un administrateur est de vérifier que les utilisateurs finaux ont accès aux applications dont ils ont besoin pour travailler. 

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Pour suivre ce guide de démarrage rapide, vous devez [créer un utilisateur](../fundamentals/quickstart-create-user.md), [créer un groupe](../fundamentals/quickstart-create-group.md) et [inscrire un appareil](../quickstart-setup-auto-enrollment.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’[administrateur général ou en tant qu’administrateur de services fédérés Intune](../fundamentals/users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="add-the-client-app-to-intune"></a>Ajouter l’application cliente à Intune

Vous pouvez ajouter une application pour permettre à Intune d’en gérer certains aspects. 

Effectuez les étapes suivantes pour ajouter une application dans Intune :
1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Applications clientes** > **Applications** > **Ajouter**. 
2. Sélectionnez **Windows 10** dans la section **Suite Office 365** de la zone de liste déroulante **Type d’application**.
3. Sélectionnez **Configurer la suite d’applications** pour sélectionner les applications Office à attribuer à l’utilisateur Intune.
4. Cliquez sur **OK** pour accepter les applications sélectionnées par défaut.
5. Sélectionnez **Informations sur la suite d’applications**.
6. Entrez **Suite d’applications Microsoft Office 365** dans **Nom de la suite**.
7. Entrez **Suite d’applications Microsoft Office 365** comme **Description de la suite**.
8. Cliquez sur **Oui** à côté de **Afficher en tant qu’application proposée dans le portail d’entreprise**.
9. Cliquez sur **OK**.

    ![Capture d’écran de l’ajout d’informations sur la suite d’applications](./media/quickstart-add-assign-app/quickstart-add-assign-app-01.png)

10. Sélectionnez **Paramètres de la suite d’applications**.
11. Dans la zone de liste déroulante **Canal de mise à jour**, sélectionnez **Mensuel**.
12. Cliquez sur **OK** > **Ajouter**.

## <a name="assign-the-app-to-a-group"></a>Attribuer l’application à un groupe

Une fois que vous avez ajouté une application dans Microsoft Intune, vous pouvez l’attribuer à des groupes d’utilisateurs ou d’appareils.

> [!NOTE]
> Ce guide de démarrage rapide s’appuie sur les guides de démarrage rapide précédents de cette série. Pour plus d’informations, consultez les [prérequis](quickstart-add-assign-app.md#prerequisites) décrits dans ce guide de démarrage rapide.

Effectuez les étapes suivantes pour attribuer une application à un groupe :
1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Applications clientes** > **Applications**. 
2. Sélectionnez l’application que vous voulez attribuer à un groupe.
3. Cliquez sur **Affectations** > **Ajouter un groupe** pour afficher le panneau **Ajouter un groupe**.
4. Sélectionnez **Disponible pour les appareils inscrits** dans la zone de liste déroulante **Type d’attribution**. 
5. Cliquez sur **Groupes inclus** > **Sélectionner les groupes à inclure** > **Testeurs Contoso**.
6. Cliquez sur **Sélectionner** > **OK** > **OK** > **Enregistrer** pour attribuer le groupe.

Vous avez maintenant attribué l’application au groupe **Testeurs Contoso**.

## <a name="install-the-app-on-the-enrolled-device"></a>Installer l’application sur l’appareil inscrit

Vous devez installer et utiliser l’application Portail d’entreprise pour installer l’application **Contoso's To-Do** mise à disposition par Intune. Effectuez les étapes suivantes pour vérifier que l’application est accessible à l’utilisateur de l’appareil inscrit.

1. Connectez-vous à votre appareil Windows 10 Desktop inscrit.

    > [!IMPORTANT]
    > L’appareil doit être [inscrit dans Intune](../quickstart-enroll-windows-device.md). En outre, vous devez vous connecter à l’appareil à l’aide d’un compte appartenant au groupe auquel vous avez attribué l’application.

2. Dans le menu **Démarrer**, ouvrez **Microsoft Store**. Ensuite, recherchez l’application **Portail d’entreprise** et installez-la.
3. Lancez l’application **Portail d’entreprise**.
4. Cliquez sur l’application que vous avez ajoutée à l’aide d’Intune. Dans ce guide de démarrage rapide, vous avez ajouté l’application **Suite d’applications Microsoft Office 365**.

    > [!NOTE]
    > Si vous n’avez pas réussi à attribuer d’application à l’utilisateur Intune, vous voyez le message suivant : *Votre administrateur informatique n’a mis aucune application à votre disposition.*

5. Cliquez sur **Installer**.

Si votre entreprise l’exige, vous pouvez attribuer manuellement l’application Portail d’entreprise Windows 10 à votre personnel, directement à partir d’Intune. Pour plus d’informations, consultez [Ajouter manuellement l’application Portail d’entreprise Windows 10 à l’aide de Microsoft Intune](../company-portal-app.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez ajouté des applications dans Intune, attribué les applications à un groupe et installé les applications sur l’appareil Windows 10 Desktop inscrit. Pour plus d’informations sur la gestion des applications dans Intune, consultez [Qu’est-ce que la gestion d’applications Microsoft Intune ?](app-management.md)

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer et affecter une stratégie de protection des applications](quickstart-create-assign-app-policy.md)
