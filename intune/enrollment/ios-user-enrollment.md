---
title: Inscription des appareils iOS/iPadOS – Inscription des utilisateurs
titleSuffix: Microsoft Intune
description: Découvrez comment configurer l’inscription des utilisateurs iOS/iPadOS et iPadOS.
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
ms.openlocfilehash: d22d8d4772754fddbd366610402d64acc28ffc65
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415267"
---
# <a name="set-up-iosipados-and-ipados-user-enrollment-preview"></a>Configuration de l’inscription des utilisateurs iOS/iPadOS et iPadOS (préversion)

Vous pouvez configurer Intune pour inscrire des appareils iOS/iPadOS et iPadOS suivant le processus d’inscription des utilisateurs d’Apple. L'inscription des utilisateurs fournit aux administrateurs un sous-ensemble simplifié d'options de gestion par rapport aux autres méthodes d'inscription.

Pour plus d'informations sur les options disponibles avec l'inscription des utilisateurs, voir [Actions, mots de passe et autres options prises en charge par l'inscription des utilisateurs](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> La prise en charge de l'inscription des utilisateurs d’Apple dans Intune est actuellement en préversion.

## <a name="prerequisites"></a>Prérequis
- [Autorité de gestion des appareils mobiles (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificat Push MDM Apple](apple-mdm-push-certificate-get.md)
- [ID Apple gérés](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Créer un profil d'inscription des utilisateurs dans Intune

Un profil d'inscription définit les paramètres appliqués à un groupe d'appareils lors de l’inscription. 

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **iOS** > **Inscription iOS** > **Types d’inscription (préversion)**  > **Créer un profil** > **iOS/iPadOS**. Ce profil permet d’indiquer de quelle expérience d’inscription vos utilisateurs finaux iOS/iPadOS et iPadOS bénéficieront sur les appareils non inscrits suivant une méthode Apple d’entreprise. Si vous souhaitez apporter des modifications, vous pouvez modifier ce profil après l'avoir créé.

    ![Créer un profil d’inscription Apple](./media/ios-user-enrollment/create-profile.png)

2. Sur la page **de base**, entrez un **nom** et une **description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ **Nom** pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et attribuer des appareils avec ce profil d’inscription. En savoir plus sur les [groupes dynamiques Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Page Informations de base](./media/ios-user-enrollment/basics-page.png)


3. Sélectionnez **Suivant**.

4. Dans la page **Paramètres**, sélectionnez l'une des options suivantes pour le **type d’inscription** :

    ![Page Paramètres](./media/ios-user-enrollment/settings-page.png)

    - **Inscription de l’appareil** : Tous les utilisateurs de ce profil utiliseront l'inscription de l’appareil.
    - **Inscription des utilisateurs** : Tous les utilisateurs de ce profil utiliseront l'inscription des utilisateurs.
    - **Déterminer en fonction du choix de l'utilisateur** : Tous les utilisateurs de ce groupe auront le choix du type d'inscription à utiliser. Lorsque les utilisateurs inscrivent leurs appareils, ils peuvent choisir entre l’option **I own this device (Je possède cet appareil)** et **(Company) owns this device ((L’entreprise) possède cet appareil)** . S'ils choisissent la seconde option, l'appareil sera inscrit à l’aide de l'inscription des appareils. Si l'utilisateur choisit **I own this device (Je possède cet appareil)** , il pourra également sécuriser l'ensemble de l’appareil ou uniquement ses applications et données professionnelles. Le choix de l'utilisateur final d’indiquer s’il possède ou non l'appareil détermine le type d'inscription mis en place sur son appareil. Par ailleurs, ce choix n’est pas répercuté dans l'attribut Propriété de l'appareil d’Intune. Pour plus d’informations sur l’expérience utilisateur, consultez [Configuration de l’accès des appareils iOS/iPadOS aux ressources de l’entreprise](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
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


