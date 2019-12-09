---
title: Inscrire des appareils iOS - Inscription des utilisateurs
titleSuffix: Microsoft Intune
description: En savoir plus sur la configuration de l’inscription des utilisateurs iOS et iPadOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d77a275e3a48845f56b22ecc21b75f664ea619c5
ms.sourcegitcommit: f26039d674eb4d61ab68264dd1a10b2e5e1d842c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74691751"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>Configurer l’inscription des utilisateurs iOS et iPadOS (préversion)

Vous pouvez configurer Intune pour inscrire des appareils iOS et iPadOS en utilisant le processus d'inscription des utilisateurs d'Apple. L'inscription des utilisateurs fournit aux administrateurs un sous-ensemble simplifié d'options de gestion par rapport aux autres méthodes d'inscription.

Pour plus d'informations sur les options disponibles avec l'inscription des utilisateurs, voir [Actions, mots de passe et autres options prises en charge par l'inscription des utilisateurs](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> La prise en charge de l'inscription des utilisateurs d’Apple dans Intune est actuellement en préversion.

## <a name="prerequisites"></a>Prérequis
- [Autorité de gestion des appareils mobiles (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificat Push MDM Apple](apple-mdm-push-certificate-get.md)
- [ID Apple gérés](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Créer un profil d'inscription des utilisateurs dans Intune

Un profil d'inscription définit les paramètres appliqués à un groupe d'appareils lors de l’inscription. 

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **iOS** > **Inscription iOS** > **Types d’inscription (préversion)**  > **Créer un profil** > **iOS/iPadOS**. Ce profil est l'endroit où vous indiquerez l’expérience d'inscription dont vos utilisateurs finaux iOS et iPadOS bénéficieront sur les appareils non inscrits via par une méthode Apple d'entreprise. Si vous souhaitez apporter des modifications, vous pouvez modifier ce profil après l'avoir créé.

    ![Créer un profil d’inscription Apple](./media/ios-user-enrollment/create-profile.png)

2. Sur la page **de base**, entrez un **nom** et une **description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ **Nom** pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et attribuer des appareils avec ce profil d’inscription. En savoir plus sur les [groupes dynamiques Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Page Informations de base](./media/ios-user-enrollment/basics-page.png)


3. Sélectionnez **Suivant**.

4. Sur la page **Paramètres**, vous pouvez donner aux utilisateurs la possibilité un type d'inscription. Vous pouvez également définir un type d’inscription par défaut.

    ![Page Paramètres](./media/ios-user-enrollment/settings-page.png)

    - Si vous voulez que tous les utilisateurs de ce profil utilisent l'inscription des utilisateurs, procédez comme suit :
        1. Pour l’option **Require user to select device type (Obliger l'utilisateur à sélectionner le type d’appareil)** , sélectionnez **Not configured (Non configuré)** .
        2. Pour l’option **Default enrollment type (Type d’inscription par défaut)** , sélectionnez **User Enrollment (Inscription des utilisateurs)** .
    - Si vous voulez que tous les utilisateurs de ce profil utilisent l'inscription des appareils, procédez comme suit :
        1. Pour l’option **Require user to select device type (Obliger l'utilisateur à sélectionner le type d’appareil)** , sélectionnez **Not configured (Non configuré)** .
        2. Pour l’option **Default enrollment type (Type d’inscription par défaut)** , sélectionnez **Device Enrollment (Inscription des appareils)** .
    - Si vous voulez donner à tous les utilisateurs de ce groupe le choix du type d'inscription à utiliser, sélectionnez **Required (Requis)** pour l’option **Require user to select device type (Obliger l’utilisateur à sélectionner un type d’appareil)** . Lorsque les utilisateurs inscrivent leurs appareils, ils peuvent choisir entre l’option **I own this device (Je possède cet appareil)** et **(Company) owns this device ((L’entreprise) possède cet appareil)** . S'ils choisissent la première option, l'appareil sera inscrit à l’aide de l'inscription des utilisateurs. S'ils choisissent la seconde option, l'appareil sera inscrit à l’aide de l'inscription des appareils. Si l'utilisateur choisit **I own this device (Je possède cet appareil)** , il pourra également sécuriser l'ensemble de l’appareil ou uniquement ses applications et données professionnelles. Le choix de l'utilisateur final d’indiquer s’il possède ou non l'appareil détermine uniquement le type d'inscription mis en place sur son appareil. Ce choix n’est pas répercuté dans l'attribut Propriété de l'appareil d’Intune. Pour en savoir plus sur l'expérience utilisateur, voir [Configurer l’accès d’un appareil iOS aux ressources de l’entreprise](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
    > [!NOTE]
    > L'information suivante est inexacte et sera retirée de l'interface utilisateur.
    > « Pour que l'accès conditionnel fonctionne sur les appareils ciblés par l'inscription des utilisateurs, vous devrez transmettre en mode push l'application Azure Authenticator comme application requise pour ce groupe d'utilisateurs afin d'activer l’authentification unique (SSO) et la jonction d’espace de travail. »
    > En tant qu'administrateur, vous n'avez rien à faire pour transmettre en mode push l'application Authenticator à vos utilisateurs. Vos utilisateurs seront invités à installer l'application Authenticator dans le portail d'entreprise afin de compléter le processus d'inscription et s'assurer que ces scénarios fonctionnent correctement.

5. Sélectionnez **Suivant**.

6. Dans la page **Affectations**, choisissez les groupes d'utilisateurs contenant les utilisateurs auxquels vous voulez que ce profil soit affecté. Vous pouvez choisir d'affecter le profil à tous les utilisateurs ou à des groupes spécifiques. Tous les utilisateurs des groupes sélectionnés utiliseront le type d'inscription choisi ci-dessus. Les groupes d’appareils ne sont pas pris en charge pour les scénarios d'inscription des utilisateurs, car la fonctionnalité est basée sur les identités des utilisateurs et non sur les appareils. Vous pouvez choisir d'affecter le profil à tous les utilisateurs ou à des groupes spécifiques.

    ![Page Affectations](./media/ios-user-enrollment/assignments-page.png)

7. Sélectionnez **Suivant**.

8. Dans la page **Review and Create (Examiner et créer)** , passez en revue vos choix, puis sélectionnez **Créer** pour attribuer le profil aux utilisateurs.

    ![Page Affectations](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Priorité du profil

Après avoir créé plusieurs profils de type d’inscription, vous pouvez modifier l'ordre de priorité dans lequel ils sont appliqués.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **iOS** > **Inscription iOS** > **Types d’inscription (préversion)** .
2. Glissez-déplacez les profils dans la liste, dans l'ordre dans lequel vous voulez les appliquer.

En cas de conflit entre les profils d'un utilisateur, le profil avec la priorité la plus élevée est appliqué pour l'utilisateur.


