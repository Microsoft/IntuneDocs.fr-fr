---
title: Démarrage rapide - Créer et attribuer un rôle personnalisé dans Intune
description: Démarrage rapide - Créer et attribuer un rôle personnalisé pour un gestionnaire d’appareils distants.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: be3ef61d3bdce2f1ad74a388a2ec50691313a1d1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400281"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Démarrage rapide : Créer et affecter un rôle personnalisé

Dans ce guide de démarrage rapide d’Intune, vous allez créer un rôle personnalisé avec des autorisations spécifiques pour un service des opérations de sécurité. Vous allez ensuite attribuer le rôle au groupe d’opérateurs correspondant. Il existe plusieurs rôles par défaut que vous pouvez utiliser immédiatement. Toutefois, en créant des rôles personnalisés comme celui-ci, vous disposez d’un contrôle d’accès précis à toutes les parties de votre système de gestion des appareils mobiles.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez [créer un groupe](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune.

## <a name="create-a-custom-role"></a>Créer un rôle personnalisé

Quand vous créez un rôle personnalisé, vous pouvez définir des autorisations pour un large éventail d’actions. Pour le rôle des opérations de sécurité, nous allons définir quelques autorisations d’accès en lecture afin que l’opérateur puisse vérifier les configurations et les stratégies d’un appareil.

1. Dans Intune, choisissez **Rôles** > **Tous les rôles** > **Ajouter**.
![Navigateur](media/quickstart-create-custom-role/add-custom-role.png)
2. Sous **Ajouter un rôle personnalisé**, dans la zone **Nom**, entrez *Opérations de sécurité*.
3. Dans la zone **Description**, entrez *Ce rôle permet à un opérateur de sécurité de superviser les informations de configuration et de conformité des appareils.*
4. Choisissez **Configurer** > **Identificateurs d’appareil d’entreprise** > **Oui** en regard de **Lire** > **OK**.
![Navigateur](media/quickstart-create-custom-role/corp-device-id-read.png)
5. Choisissez **Stratégies de conformité d’appareil** > **Oui** en regard de **Lire** > **OK**.
6. Choisissez **Configurations d’appareils** > **Oui** en regard de **Lire** > **OK**.
7. Choisissez **Organisation** > **Oui** en regard de **Lire** > **OK**.
8. Choisissez **OK** > **Créer**.

## <a name="assign-the-role-to-a-group"></a>Attribuer le rôle à un groupe

Pour permettre à votre opérateur de sécurité d’utiliser les nouvelles autorisations, vous devez attribuer le rôle à un groupe qui contient l’utilisateur de sécurité.

1. Dans Intune, choisissez **Rôles** > **Tous les rôles** > **Opérations de sécurité**.
2. Sous **Rôles Intune**, choisissez **Affectations** > **Attribuer**.
3. Dans la zone **Nom de l’attribution**, entrez *Opérateurs de sécurité*.
4. Choisissez **Membre (groupes)** > **Ajouter**.
5. Choisissez le groupe **Testeurs Contoso**.
6. Choisissez **Sélectionner** > **OK**.
7. Choisissez **Étendue (Groupes)** > **Sélectionnez les groupes à inclure** > **Testeurs Contoso**.
8. Choisissez **Sélectionner** > **OK** > **OK**.

Désormais, tous les membres du groupe sont membres du rôle *Opérations de sécurité* et peuvent consulter les informations suivantes relatives à un appareil : identificateurs d’appareil d’entreprise, stratégies de conformité d’appareil, configurations d’appareil et informations sur l’organisation.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous ne souhaitez plus utiliser le nouveau rôle personnalisé, vous pouvez le supprimer. Choisissez **Rôles** > **Tous les rôles** > choisissez les points de suspension en regard du rôle > **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un rôle d’opérations de sécurité personnalisé, et vous l’avez attribué à un groupe. Pour plus d’informations sur les rôles dans Intune, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune](role-based-access-control.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Créer un profil d’appareil de messagerie pour iOS](quickstart-email-profile.md)
