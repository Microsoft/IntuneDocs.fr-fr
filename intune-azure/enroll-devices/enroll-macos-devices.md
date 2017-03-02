---
title: "Inscrire des appareils macOS dans Intune | Préversion Intune Azure | Microsoft Docs"
description: "Préversion Intune Azure : Découvrez comment inscrire des appareils macOS dans la préversion d’Intune Azure."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a2e840797c06322b9efc59438e0675e57b7cdb24
ms.openlocfilehash: f217988313debd33bcba3f8168aa03b6dbf8586e
ms.lasthandoff: 02/14/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Inscrire des appareils macOS dans la préversion d’Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune vous permet de gérer les appareils Mac OS. Pour activer la gestion des appareils, vos utilisateurs doivent inscrire leurs appareils en accédant au [site web Portail d’entreprise](http://portal.manage.microsoft.com), puis en suivant les invites. Une fois que les appareils Mac OS sont gérés, vous pouvez [créer des paramètres personnalisés pour les appareils Mac OS](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-macos). D’autres fonctionnalités seront bientôt disponibles.

## <a name="prerequisites"></a>Conditions préalables

Avant de configurer l’inscription des appareils macOS, effectuez les préparatifs suivants :

- [Configurer des domaines](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Configurer l’autorité MDM](set-mdm-authority.md)
- [Créer des groupes](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurer le portail d’entreprise](/intune-azure/manage-apps/company-portal-app.md)
- Attribuer des licences utilisateur dans le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtenir un certificat Push MDM Apple](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Configurer l’inscription macOS

Par défaut, Intune autorise déjà l’inscription des appareils Mac OS. 

Pour empêcher l’inscription des appareils Mac OS, consultez [Définir des restrictions de type d’appareil](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions). 

Pour définir le nombre maximal d’appareils qu’un utilisateur peut inscrire, consultez [Définir des restrictions de limite d’appareil](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indiquez à vos utilisateurs comment inscrire leurs appareils de manière à ce qu’ils puissent accéder aux ressources de l’entreprise

Vous devez indiquer à vos utilisateurs finaux d’accéder au [site web Portail d’entreprise](http://portal.manage.microsoft.com) et de suivre les invites pour inscrire leurs appareils. Vous pouvez également leur envoyer un lien vers les étapes d’inscription en ligne : [Inscrire votre appareil Mac OS dans Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos). 

Pour plus d’informations sur les autres tâches de l’utilisateur final, consultez les articles suivants :

- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Utilisation de votre appareil iOS ou MacOS avec Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)