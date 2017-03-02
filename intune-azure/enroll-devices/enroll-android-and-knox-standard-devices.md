---
title: "Inscrire des appareils Android dans Intune | Préversion Intune Azure | Microsoft Docs"
description: "Préversion Intune Azure : Découvrez comment inscrire des appareils Android dans la préversion d’Intune Azure."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 99b790e33843efcf83a4687490b186a6e174bd81
ms.lasthandoff: 02/15/2017


---

# <a name="enroll-android-devices"></a>Inscrire des appareils Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune vous permet de gérer des appareils Android, dont les appareils Samsung KNOX Standard. Pour activer la gestion des appareils, vos utilisateurs doivent inscrire leurs appareils en téléchargeant l’application Portail d’entreprise Intune, qui est disponible à partir de Google Play, puis en ouvrant l’application et en suivant les invites d’inscription. Une fois que les appareils Android sont gérés, vous pouvez [créer des stratégies de conformité](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android), [gérer les applications](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management), et bien plus encore.

## <a name="prerequisite"></a>Configuration requise

Vous devez définir l’autorité MDM sur **Microsoft Intune** pour préparer la gestion des appareils mobiles. Consultez la page [Configurer l’autorité MDM](set-mdm-authority.md) pour obtenir des instructions. Cet élément ne se définit qu’une seule fois, lorsque vous configurez pour la première fois Intune pour la gestion des appareils mobiles, donc vous l’avez peut-être déjà défini. 

## <a name="set-up-android-enrollment"></a>Configurer l’inscription Android

Par défaut, Intune autorise déjà l’inscription des appareils Android et Samsung Knox Standard. 

Pour empêcher l’inscription des appareils Android, ou uniquement des appareils personnels Android, consultez [Définir des restrictions de type d’appareil](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions). 

Pour définir le nombre maximal d’appareils qu’un utilisateur peut inscrire, consultez [Définir des restrictions de limite d’appareil](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indiquez à vos utilisateurs comment inscrire leurs appareils de manière à ce qu’ils puissent accéder aux ressources de l’entreprise

Vous devez indiquer à vos utilisateurs finaux d’accéder à Google Play pour télécharger l’application Portail d’entreprise Intune, puis d’ouvrir l’application et de suivre les invites pour inscrire leur appareil. L’application guide les utilisateurs tout au long du processus d’inscription en leur expliquant ce qu’ils peuvent attendre, et ce que les administrateurs informatiques peuvent et ne peuvent pas voir sur leurs appareils.

Vous pouvez également leur envoyer un lien vers les étapes d’inscription en ligne : [Inscrire un appareil Android dans Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android). 

Pour plus d’informations sur les autres tâches de l’utilisateur final, consultez les articles suivants :

- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Utilisation de votre appareil Android avec Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)
