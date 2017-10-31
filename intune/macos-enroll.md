---
title: Inscrire des appareils macOS dans Intune
titlesuffix: Azure portal
description: "Apprenez à inscrire des appareils macOS dans Intune."
keywords: 
author: arob98
ms.author: angrobe
nmanager: angrobe
ms.date: 10/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a18aa5091c8be2095e2ac95717c2b8294b845cd5
ms.sourcegitcommit: 623c52116bc3fdd12680b9686dcd0e1eeb6ea5ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="enroll-macos-devices-in-intune"></a>Inscrire des appareils macOS dans Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune vous permet de gérer les appareils Mac OS. Pour activer la gestion des appareils, vos utilisateurs doivent inscrire leurs appareils en accédant au [site web Portail d’entreprise](http://portal.manage.microsoft.com), puis en suivant les invites. Une fois que les appareils Mac OS sont gérés, vous pouvez [créer des paramètres personnalisés pour les appareils Mac OS](custom-settings-macos.md). D’autres fonctionnalités seront bientôt disponibles.

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’inscription des appareils macOS, effectuez les prérequis suivants :

- [Configurer des domaines](custom-domain-name-configure.md)
- [Configurer l’autorité MDM](mdm-authority-set.md)
- [Créer des groupes](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurer le portail d’entreprise](company-portal-app.md)
- Attribuer des licences utilisateur dans le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtenir un certificat Push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>Configurer l’inscription macOS

Par défaut, Intune autorise déjà l’inscription des appareils Mac OS.

Pour empêcher l’inscription des appareils Mac OS, consultez [Définir des restrictions de type d’appareil](enrollment-restrictions-set.md).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indiquez à vos utilisateurs comment inscrire leurs appareils de manière à ce qu’ils puissent accéder aux ressources de l’entreprise

Vous devez indiquer à vos utilisateurs finaux d’accéder au [site web Portail d’entreprise](http://portal.manage.microsoft.com) et de suivre les invites pour inscrire leurs appareils. Vous pouvez également leur envoyer un lien vers les étapes d’inscription en ligne : [Inscrire votre appareil Mac OS dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Pour plus d’informations sur les autres tâches de l’utilisateur final, consultez les articles suivants :

- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](end-user-educate.md)
- [Utilisation de votre appareil iOS ou MacOS avec Intune](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)
