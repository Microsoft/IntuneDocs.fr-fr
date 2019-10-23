---
title: Inscrire des appareils iOS dans Intune
titleSuffix: Microsoft Intune
description: Configurez l’inscription des appareils iOS dans Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fb5208cd7df6dc68bcd20455ae9e06a9dbd7ff5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503150"
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrire des appareils iOS dans Intune

Intune permet la gestion des appareils mobiles pour les iPad et les iPhone afin que les utilisateurs puissent accéder en toute sécurité à la messagerie, aux données et aux applications de leur entreprise.

En tant qu'administrateur d'Intune, vous pouvez configurer l'inscription des appareils iOS et iPadOS pour accéder aux ressources de l'entreprise. Vous pouvez autoriser les utilisateurs à inscrire eux-mêmes leurs appareils. Il s’agit là d’une inscription de type BYOD (Bring Your Own Device). Vous pouvez également configurer l’inscription d’appareils appartenant à l’entreprise.

## <a name="prerequisites-for-ios-enrollment"></a>Prérequis pour l’inscription d’appareils iOS

Avant de pouvoir activer des appareils iOS, effectuez les étapes suivantes :

- [Assurez-vous que votre appareil est pris en charge par la procédure d’inscription d’appareils Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurer Intune](../fundamentals/setup-steps.md) : ces étapes ont pour but de configurer votre infrastructure Intune. Pour inscrire des appareils, vous devez notamment [définir votre autorité de gestion des appareils mobiles](../fundamentals/mdm-authority-set.md).
- [Obtenir un certificat Push MDM Apple](apple-mdm-push-certificate-get.md) : Apple exige un certificat pour activer la gestion des appareils iOS et macOS.

## <a name="user-owned-ios-and-ipados-devices-byod"></a>Appareils iOS et iPadOS de l’utilisateur (BYOD)

Vous pouvez laisser les utilisateurs inscrire leurs appareils personnels pour la gestion Intune, approche communément appelée « BYOD » (Bring Your Own Device). Trois options sont disponibles pour inscrire des utilisateurs :
- Les stratégies de protection de l’application vous donnent l'expérience BYOD la plus simple, avec une gestion au niveau de l'application seulement. Toutefois, si vous souhaitez également sécuriser l'appareil avec un code PIN complexe à 6 chiffres, vous pouvez utiliser ces stratégies conjointement avec l'inscription utilisateur.
- L'inscription des appareils s’apparente à une inscription BYOD standard. Elle offre aux administrateurs un large éventail d'options de gestion.
- L'inscription des utilisateurs est un processus d'inscription simplifié qui fournit aux administrateurs un sous-ensemble d'options de gestion des appareils. Cette fonctionnalité est actuellement en préversion. 

Une fois que vous avez répondu aux prérequis et affecté des licences aux utilisateurs, ces derniers peuvent télécharger l’application Portail d’entreprise Intune à partir de l’App Store et suivre les instructions d’inscription dans l’application. Vous pouvez personnaliser la déclaration de confidentialité du Portail d’entreprise sur les appareils iOS, comme expliqué dans la [personnalisation de la déclaration de confidentialité](../apps/company-portal-app.md#privacy-statement-customization).

## <a name="company-owned-ios-devices"></a>Appareils d’entreprise iOS

Pour les organisations qui achètent des appareils pour leurs utilisateurs, Intune prend en charge les méthodes d’inscription d’appareils d’entreprise iOS suivantes :

- Programme d’inscription des appareils Apple (DEP)
- Apple School Manager
- Inscription par le biais de l’Assistant Configuration Apple Configurator
- Inscription directe Apple Configurator

Vous pouvez aussi inscrire des appareils iOS d’entreprise avec un compte [Gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programme d’inscription d’appareils

Les organisations peuvent acheter des appareils iOS par le biais du Programme d’inscription des appareils (DEP) d’Apple. DEP vous permet de déployer un profil d’inscription « à distance » pour inscrire des appareils à la gestion. Pour plus d’informations, consultez [Programme d’inscription des appareils](device-enrollment-program-enroll-ios.md).

## <a name="user-enrollment"></a>Inscription des utilisateurs
L'inscription des utilisateurs fournit aux administrateurs un sous-ensemble d'options de gestion par rapport aux autres méthodes d'inscription. Pour plus d'informations, voir [Actions, mots de passe et autres options prises en charge par l'inscription des utilisateurs](ios-user-enrollment-supported-actions.md) et [Configurer l’inscription des utilisateurs iOS et iPadOS](ios-user-enrollment.md).

## <a name="apple-school-manager"></a>Apple School Manager

Apple School Manager est un programme d’achat et d’inscription d’appareils pour les écoles. Comme pour DEP, vous pouvez déployer un profil pour inscrire des appareils à la gestion. Découvrez plus en détail [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator

Vous pouvez inscrire des appareils iOS avec Apple Configurator en cours d’exécution sur un ordinateur Mac. Pour préparer les appareils, connectez-les au moyen d’un câble USB et installez un profil d’inscription. Vous pouvez inscrire des appareils avec Apple Configurator de deux manières :

- Inscription de l’Assistant Configuration : réinitialise l’appareil, le prépare à exécuter l’Assistant Configuration et installe les stratégies d’entreprise pour le nouvel utilisateur de l’appareil.
- Inscription directe : ne réinitialise pas l’appareil et l’inscrit auprès d’une stratégie prédéfinie. Cette méthode est destinée aux appareils ne disposant d’aucune affinité utilisateur.

Découvrez plus en détail l’[inscription avec Apple Configurator](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Utiliser le Portail d’entreprise sur des appareils inscrits via l’outil Apple Configurator ou DEP

Des appareils configurés avec une affinité utilisateur peuvent installer et exécuter l’application Portail d’entreprise pour télécharger des applications et gérer des appareils. Une fois que les utilisateurs reçoivent leurs appareils, ils doivent effectuer un certain nombre d’étapes supplémentaires pour terminer l’exécution de l’Assistant Installation et installer l’application Portail d’entreprise.

Une affinité utilisateur est nécessaire pour prendre en charge les éléments suivants :

- Applications de gestion des applications mobiles (GAM)
- Accès conditionnel aux données e-mail et de l’entreprise
- Application Portail d’entreprise

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Comment les utilisateurs inscrivent des appareils iOS d’entreprise avec l’affinité utilisateur

1. Quand les utilisateurs allument leur appareil, ils sont invités à terminer l’exécution de l’Assistant Installation.
2. Une fois l’installation terminée, les utilisateurs sont invités à fournir un identifiant Apple. Ils doivent fournir un identifiant Apple pour permettre à l’appareil d’installer le Portail d’entreprise.
3. L’appareil iOS installe automatiquement l’application Portail d’entreprise à partir de l’App Store.
4. Les utilisateurs doivent lancer l’application Portail d’entreprise et se connecter à l’aide des informations d’identification (par exemple, l’UPN) qui sont associées à leur abonnement dans Intune.
5. Une fois que vous êtes connecté, l’inscription est terminée. Les utilisateurs peuvent désormais utiliser cet appareil avec l’ensemble complet des fonctionnalités.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>À propos des appareils gérés d’entreprise sans aucune affinité utilisateur

Les appareils configurés sans aucune affinité utilisateur ne prennent pas en charge le Portail d’entreprise et ne doivent pas être dotés de l’application. Le Portail d’entreprise est conçu pour les utilisateurs détenteurs d’informations d’identification d’entreprise, qui ont besoin d’accéder à des ressources d’entreprise personnalisées (par exemple, aux e-mails). Les appareils inscrits sans aucune affinité utilisateur ne sont pas destinés à un utilisateur dédié. Une borne, un point de vente (PDV) ou un appareil à usage partagé sont des exemples typiques d’utilisation d’appareils inscrits sans aucune affinité utilisateur.

Si une affinité utilisateur est obligatoire, vérifiez que l’option **Affinité utilisateur** est sélectionnée pour le profil d’inscription de l’appareil avant d’inscrire ce dernier. Pour modifier l’état d’affinité d’un appareil, vous devez le mettre hors service et le réinscrire.

## <a name="see-also"></a>Voir aussi

[Résolution des problèmes d’inscription d’appareils iOS dans Microsoft Intune](https://support.microsoft.com/help/4039809)
