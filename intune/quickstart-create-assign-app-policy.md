---
title: 'Démarrage rapide : Créer et attribuer une stratégie de protection des applications'
titlesuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour créer et attribuer une stratégie de protection des applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dee5407b39d9299081bf526b117c64b5883a106
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57393365"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>Démarrage rapide : Créer et affecter une stratégie de protection des applications

Dans ce guide de démarrage rapide, vous allez utiliser Intune pour créer une stratégie de protection des applications et l’attribuer à une application cliente sur l’appareil d’un utilisateur final. Intune utilise des stratégies de protection des applications pour garantir que vos applications remplissent les exigences de protection des données dans votre organisation.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Pour suivre ce guide de démarrage rapide, vous devez [créer un utilisateur](quickstart-create-user.md), [créer un groupe](quickstart-create-group.md), [inscrire un appareil](quickstart-setup-auto-enrollment.md), puis [ajouter et attribuer une application](quickstart-add-assign-app.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’[administrateur général ou administrateur de services Intune](users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="create-an-app-protection-policy"></a>Créer une stratégie de protection des applications

Effectuez les étapes suivantes pour créer une stratégie de protection des applications :

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Applications clientes** > **Stratégies de protection des applications** > **Créer une stratégie**. 
2. Entrez les informations suivantes : 

    - **Nom** : *Protection du contenu Windows 10*
    - **Description** : *Les utilisateurs associés à cette stratégie ne pourront pas couper, copier ou coller du contenu entre l’application attribuée et d’autres applications non gérées sur l’appareil.*
    - **Plateforme** : *Windows 10*
    - **État d’inscription** : *Avec inscription*

3. Sélectionnez **Applications protégées** pour choisir les applications auxquelles appliquer cette stratégie.
4. Cliquez sur **Ajouter des applications**.
5. Sous **Applications recommandées**, sélectionnez **Word Mobile**.
5. Cliquez sur **OK** > **OK**. 
6. Sélectionnez **Paramètres obligatoires** pour configurer l’application.
7. Cliquez sur **Autoriser l’utilisateur à ignorer les avertissements** pour définir le mode Protection des informations Windows. Quand elle est sélectionnée, cette option empêche le déplacement des données d’entreprise à partir de l’application protégée.
8. Cliquez sur **OK** > **Créer**.

Vous voyez maintenant la stratégie de protection des applications dans Intune.

### <a name="assign-the-app-protection-policy"></a>Attribuer la stratégie de protection des applications

Une fois que vous avez créé une stratégie de protection des applications dans Intune, vous pouvez l’attribuer à des groupes. 

Effectuez les étapes suivantes pour attribuer la stratégie de protection des applications :

1.  Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Intune** > **Applications clientes** > **Stratégies de protection des applications**. 
2.  Sélectionnez la stratégie de protection des applications que vous avez créée précédemment. Dans ce guide de démarrage rapide, la stratégie s’appelle **Protection du contenu Windows 10**.
3.  Sélectionnez **Affectations**.
4.  Cliquez sur **Sélectionner les groupes à inclure** dans l’onglet **Inclure**.
5.  Sélectionnez **Testeurs Contoso** comme groupe à inclure.
6.  Cliquez sur **Sélectionner**. 

Vous avez maintenant attribué la stratégie de protection des applications.

> [!NOTE]
> Les stratégies de protection des applications sont applicables aux groupes d’utilisateurs uniquement, pas aux groupes d’appareils.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé et attribué une stratégie de protection des applications. Les utilisateurs de l’application auxquels cette stratégie a été attribuée ne pourront pas couper, copier ou coller du contenu entre l’application attribuée et d’autres applications non managées sur l’appareil. Ce type de protection contribue à mieux protéger les données de votre organisation. Pour plus d’informations sur les stratégies de protection des applications dans Intune, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer et attribuer un rôle personnalisé](quickstart-create-custom-role.md)
