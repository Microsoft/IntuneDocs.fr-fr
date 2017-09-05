---
title: Choisir comment inscrire les appareils Windows dans Intune
titleSuffix: Intune on Azure
description: "Découvrez comment configurer l’inscription des appareils Windows dans Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8bae9bd48493f20bb4abb94290013f27a6a75dd6
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Inscrire des appareils iOS dans Intune

Intune permet la gestion des appareils mobiles pour les iPad et les iPhone afin que les utilisateurs puissent accéder à la messagerie et aux applications de leur entreprise.

En tant qu’administrateur Intune, vous pouvez activer l’inscription pour les appareils iOS. Vous pouvez autoriser les utilisateurs à inscrire eux-mêmes leurs propres appareils. Ce type d’inscription a pour nom « Apportez votre propre appareil » (BYOD). Vous pouvez également activer l’inscription d’appareils appartenant à l’entreprise.

## <a name="prerequisites-for-ios-enrollment"></a>Prérequis pour l’inscription d’appareils iOS
Avant de pouvoir activer des appareils iOS, effectuez les étapes suivantes :
- [Configurer Intune](setup-steps.md) : ces étapes ont pour but de configurer votre infrastructure Intune. Pour inscrire des appareils, vous devez notamment [définir votre autorité de gestion des appareils mobiles](mdm-authority-set.md).
- [Obtenir un certificat Push MDM Apple](apple-mdm-push-certificate-get.md) : Apple exige un certificat pour activer la gestion des appareils iOS et macOS.

## <a name="user-owned-ios-devices-byod"></a>Appareils iOS de l’utilisateur (BYOD)

Vous pouvez laisser les utilisateurs inscrire leurs appareils personnels pour la gestion Intune, approche communément appelée « BYOD » (Bring Your Own Device). Une fois que vous avez répondu aux prérequis et affecté des licences aux utilisateurs, ces derniers peuvent télécharger l’application Portail d’entreprise iOS à partir de l’App Store et suivre les instructions d’inscription dans l’application.

## <a name="company-owned-ios-devices"></a>Appareils iOS de l’entreprise
Pour les organisations qui achètent des appareils pour leurs utilisateurs, Intune prend en charge les méthodes d’inscription d’appareils d’entreprise iOS suivantes :

- Programme d’inscription des appareils Apple (DEP)
- Apple School Manager
- Inscription par le biais de l’Assistant Configuration Apple Configurator
- Inscription directe Apple Configurator

Vous pouvez aussi inscrire des appareils iOS d’entreprise avec un compte [Gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programme d’inscription des appareils
Les organisations peuvent acheter des appareils iOS par le biais du Programme d’inscription des appareils (DEP) d’Apple. DEP vous permet de déployer un profil d’inscription « à distance » pour inscrire des appareils à la gestion. Découvrez plus en détail le [Programme d’inscription des appareils](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager est un programme d’achat et d’inscription d’appareils pour les écoles. Comme pour DEP, vous pouvez déployer un profil pour inscrire des appareils à la gestion. Découvrez plus en détail [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Vous pouvez inscrire des appareils iOS avec Apple Configurator en cours d’exécution sur un ordinateur Mac. Pour préparer les appareils, connectez-les au moyen d’un câble USB et installez un profil d’inscription. Vous pouvez inscrire des appareils avec Apple Configurator de deux manières :
- Inscription Assistant de configuration : réinitialise l’appareil aux paramètres d’usine, le prépare à exécuter l’Assistant Configuration et installe les stratégies de l’entreprise pour le nouvel utilisateur de l’appareil.
- Inscription directe : ne réinitialise pas l’appareil aux paramètres d’usine et l’inscrit avec une stratégie prédéfinie. Cette méthode est destinée aux appareils ne disposant d’aucune affinité utilisateur.

Découvrez plus en détail l’[inscription avec Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
