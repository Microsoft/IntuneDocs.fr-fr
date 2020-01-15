---
title: Inscription de l’administrateur d’appareil Android dans Microsoft Intune
titleSuffix: ''
description: Inscrire des appareils Android dans Intune à l’aide de l’inscription de l’administrateur d’appareil.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ebeb5830136ad6dae19babbc8ecf45c1d6e5c36c
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885970"
---
# <a name="android-device-administrator-enrollment"></a>Inscription de l’administrateur d’appareil Android

L’administrateur d’appareil Android (parfois appelé gestion Android « héritée » et publiée avec Android 2.2) est un moyen de gérer les appareils Android. Toutefois, des fonctionnalités de gestion améliorées sont désormais disponibles avec [Android Enterprise](https://www.android.com/enterprise/management/) (fournie avec Android 5.0). Dans le but de passer à une gestion des périphériques modernes, plus riche et plus sécurisée, Google diminue le support des administrateurs d’appareil dans les nouvelles versions Android.

Par conséquent, pour éviter de telles fonctionnalités réduites, nous vous recommandons d’inscrire les nouveaux appareils à l’aide du processus administrateur d’appareil décrit ci-dessous.

Pour les mêmes raisons, nous vous recommandons également de migrer les appareils hors de la gestion des administrateurs d’appareil si les appareils vont être mis à jour vers Android 10. 

Pour plus d’informations sur le support d’Intune pour le support d’un administrateur d’appareil Android, consultez la [section Remarques](../fundamentals/whats-new.md#decreasing-support-for-android-device-administrator).

Si vous décidez quand même que les utilisateurs inscrivent leurs appareils Android auprès de la gestion des administrateurs d’appareil, passez à la section suivante.  

Pour plus d’informations sur les fonctionnalités d’Android Enterprise de Google, consultez les articles suivants :
- [Aide de Google pour la migration de l’administrateur d’appareil vers Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentation Google sur le plan de dépréciation de l’API de l’administrateur d’appareil](https://developers.google.com/android/work/device-admin-deprecation)


## <a name="set-up-device-administrator-enrollment"></a>Configurer l’inscription de l’administrateur d’appareil

1. Pour préparer la gestion des appareils mobiles, vous devez définir l’autorité de gestion des appareils mobiles (MDM) sur **Microsoft Intune**. Consultez la page [Configurer l’autorité MDM](../fundamentals/mdm-authority-set.md) pour obtenir des instructions. Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.
2. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison](https://go.microsoft.com/fwlink/?linkid=2109431), puis choisissez > **Appareils** > **Android** > **Inscription Android** > **Appareils personnels et appartenant à l’entreprise avec privilèges d’administration d’appareils** > **Utiliser un administrateur d’appareils pour gérer les appareils**.
3. [Indiquez à vos utilisateurs comment inscrire leurs appareils](/intune-user-help/enroll-your-device-in-intune-android).  

Une fois qu’un utilisateur est inscrit, vous pouvez commencer à gérer ses appareils dans Intune, notamment [affecter des stratégies de conformité](../protect/compliance-policy-create-android.md), [gérer les applications](../apps/app-management.md), etc.

Pour plus d’informations sur les autres tâches de l’utilisateur, consultez les articles suivants :
- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](../fundamentals/end-user-educate.md)
- [Utilisation de votre appareil Android avec Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)


## <a name="block-device-administrator-enrollment"></a>Bloquer l’inscription de l’administrateur d’appareil
Pour bloquer l’inscription des périphériques des administrateurs d’appareil Android ou uniquement des périphériques des administrateurs d’appareil Android personnels, consultez [Définir des restrictions de type d’appareil](enrollment-restrictions-set.md).



## <a name="next-steps"></a>Étapes suivantes
- [Attribuer des stratégies de conformité](../protect/compliance-policy-create-android.md)
- [Gestion des applications](../apps/app-management.md)
