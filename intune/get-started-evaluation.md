---
title: Que peut faire Microsoft Intune pour mon entreprise ?
titleSuffix: ''
description: Problèmes métier courants que Microsoft Intune peut résoudre.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0118087d5084830ac7b1761109a2bb542ec37421
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041814"
---
# <a name="what-can-intune-do-for-my-company"></a>Que peut faire Intune pour mon entreprise ?
Microsoft Intune est un service de gestion de la mobilité en entreprise, basé sur le cloud, qui permet à vos équipes de rester productives tout en protégeant vos données d’entreprise.

Avec Intune, vous pouvez :

- gérer les appareils mobiles que votre personnel utilise pour accéder aux données d’entreprise ;
- gérer les applications mobiles que votre personnel utilise ;
- protéger vos informations d’entreprise en contrôlant la façon dont votre personnel y accède et les partage ;
- vérifier que les appareils et les applications sont conformes aux exigences de sécurité de l’entreprise.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problématiques courantes auxquelles Intune permet de répondre

* [Protéger votre messagerie et vos données locales pour qu’elles soient accessibles par les appareils mobiles](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Protéger votre messagerie et vos données Office 365 pour qu’elles soient accessibles en toute sécurité par les appareils mobiles](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Fournir des téléphones d’entreprise à votre personnel](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Offrir un programme BYOD (Apportez votre propre appareil) à tous les employés](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permettre à vos employés d’accéder en toute sécurité à Office 365 à partir d’une borne publique non gérée](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Fournir des tablettes partagées à utilisation limitée à vos employés](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>Guides de démarrage rapide

Nous sommes conscients du fait que la prise en main de la gestion des appareils mobiles peut être difficile. Vous avez de nombreuses décisions à prendre au nom de votre entreprise. Les guides de démarrage rapide suivants sont là pour vous aider à bien démarrer avec Intune et à effectuer certaines tâches courantes en un minimum de temps.

Pour suivre les **Guides de démarrage rapide** dans l’ordre, référez-vous à la table des matières située à gauche de cette page.

- [Essayer gratuitement Intune](free-trial-sign-up.md) - Créez un abonnement gratuit pour essayer Intune dans un environnement de test.    
- [Créer un utilisateur](quickstart-create-user.md) - Ajoutez un utilisateur à Intune pour lui permettre d’accéder aux ressources d’entreprise sur des appareils mobiles.
- [Créer un groupe](quickstart-create-group.md) : Organisez les utilisateurs en groupes pour faciliter la gestion des stratégies et des applications auxquelles ils ont accès.
- [Configurer l’inscription automatique](quickstart-setup-auto-enrollment.md): Configurez Intune de façon à inscrire automatiquement les appareils quand certains utilisateurs se connectent à des appareils Windows 10.
- [Inscrire un appareil](quickstart-enroll-windows-device.md) : Prenez le rôle d’un utilisateur Intune et inscrivez votre appareil dans Intune. Ensuite, revenez dans Intune vérifier que l’appareil est bien inscrit.
- [Créer une stratégie de conformité d’appareil](quickstart-set-password-length-android.md) : Créez une stratégie de conformité d’appareil et attribuez-lui un groupe.
- [Envoyer des notifications aux appareils non conformes](quickstart-send-notification.md) : Envoyez un e-mail de notification aux employés qui utilisent des appareils non conformes en créant et en attribuant une stratégie de conformité.
- [Ajouter et attribuer une application](quickstart-add-assign-app.md): Ajoutez une application cliente et attribuez-la au personnel de votre entreprise.
- [Créer et attribuer une stratégie de protection des applications](quickstart-create-assign-app-policy.md) : Créez une stratégie de protection des applications et attribuez-la à une application cliente sur l’appareil d’un utilisateur final.
- [Créer et attribuer un rôle personnalisé](quickstart-create-custom-role.md) - Créez et attribuez un rôle personnalisé avec des autorisations spécifiques pour un service d’opérations de sécurité. 
- [Créer un profil d’appareil e-mail pour iOS](quickstart-email-profile.md) - Créez un profil d’e-mail pour les appareils iOS.

## <a name="prerequisites"></a>Prérequis

Avant de commencer, vous devez activer un compte Administrateur et un compte locataire Intune. Créez un abonnement gratuit pour [essayer Intune gratuitement](free-trial-sign-up.md) dans un environnement de test. Les abonnés peuvent également effectuer ces activités dans leur locataire en ligne. Ces articles de prise en main supposent de travailler sur des appareils de test.

Vous devez également vérifier que vous êtes l’administrateur général de votre organisation afin d’effectuer toutes les tâches du guide Bien démarrer.

## <a name="intune-architecture"></a>Architecture Intune

Intune est le composant de la solution Enterprise Mobility + Security (EMS) qui gère les applications et les appareils mobiles. Intune s’intègre étroitement à d’autres composants EMS comme Azure Active Directory (Azure AD) pour le contrôle d’identité et d’accès, et Azure Information Protection pour la protection des données. Si vous l’utilisez avec Office 365, vous offrez à vos employés la possibilité de rester productifs sur tous leurs appareils, tout en assurant la protection des informations de votre organisation.

![Diagramme architectural de haut niveau pour Microsoft Intune](/intune/media/intunearchitecture.svg)

## <a name="next-steps"></a>Étapes suivantes

[Bien démarrer avec Azure](get-started-azure.md) : Découvrez l’anatomie du portail Azure et comment apporter des modifications à la page que vous consultez.

## <a name="learn-more"></a>En savoir plus

* [Qu’est-ce qu’Intune ?](introduction-intune.md)
* [Qu’est-ce que le portail Azure ?](what-is-intune.md)
* [Cycles de vie des applications et des appareils](introduction-device-app-lifecycles.md)
