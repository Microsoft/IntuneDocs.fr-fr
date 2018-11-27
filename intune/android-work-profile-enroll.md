---
title: Inscrire des appareils avec profil professionnel Android dans Intune
titlesuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils avec profil professionnel Android dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b3592ceb2b1a4e7ba32fc0a8b3de53e0f0329d8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179726"
---
# <a name="set-up-enrollment-of-android-work-profile-devices"></a>Configurer l’inscription des appareils avec profil professionnel Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune vous permet de déployer des applications et des paramètres sur des appareils avec profil professionnel Android de manière à ce que les informations professionnelles soient séparées des informations personnelles. Pour plus d’informations sur Android Entreprise, consultez [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Pour configurer la gestion des profils professionnels Android, effectuez les étapes suivantes :

1. [Connectez votre compte de locataire Intune à votre compte d’entreprise Android](connect-intune-android-enterprise.md).
2. Spécifiez les paramètres d’inscription de profil professionnel Android. Les profils professionnels Android sont [pris en charge uniquement sur certains appareils Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Tout appareil qui prend en charge les profils professionnels Android prend également en charge la gestion Android conventionnelle. Intune vous permet de spécifier la façon dont les appareils qui prennent en charge les profils professionnels Android doivent être gérés dans [Restrictions d’inscription](enrollment-restrictions-set.md).
    - **Bloquer (défini par défaut)**  : Tous les appareils Android, notamment ceux qui prennent en charge les profils professionnels Android, sont inscrits comme des appareils Android conventionnels.
    - **Autoriser** : Tous les appareils qui prennent en charge les profils professionnels Android sont inscrits comme des appareils avec profil professionnel Android. Tout appareil Android qui ne prend pas en charge les profils professionnels Android est inscrit comme appareil Android conventionnel.
3. [Indiquez à vos utilisateurs comment inscrire leurs appareils](/intune-user-help/enroll-your-device-in-intune-android).


Si vous voulez inscrire des appareils dans des profils professionnels Android, mais que ces appareils étaient auparavant inscrits comme appareils Android ordinaires, vous devez d’abord les désinscrire, puis les réinscrire.

Si vous inscrivez des appareils avec profils professionnels Android à l’aide d’un compte de [Gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md), il existe une limite de 10 appareils pouvant être inscrits par compte.

Pour plus d’informations, consultez [Données envoyées par Intune à Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Approuver l’application Portail d’entreprise dans le Google Play Store géré

Pour être sûr que les utilisateurs ont toujours accès à la version la plus récente de l’application Portail d’entreprise, vous devez approuver l’application Portail d’entreprise pour Android dans le store Google Play géré. En l’approuvant, vous garantissez que chaque utilisateur reçoit des mises à jour automatiques. Si vous ne l’approuvez pas, le portail d’entreprise finit par devenir obsolète et risque de ne pas recevoir les correctifs de bogues importants ou les nouvelles fonctionnalités publiés par Microsoft.

Pour approuver le portail d’entreprise Intune, effectuez les étapes suivantes :

1.  Accédez à l’application Portail d’entreprise sur le [Google Play Store géré](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Connectez-vous au store Google Play géré avec le même compte Google que celui utilisé pour configurer la liaison pour Android Entreprise.
3.  Cliquez sur **Approuver** ; une nouvelle boîte de dialogue s’ouvre.
4.  Vérifiez les autorisations dans cette boîte de dialogue, puis cliquez sur **Approuver**. Vous devez affecter ces autorisations afin de permettre à l’application Portail d’entreprise de gérer le profil professionnel sur l’appareil.
5.  Sélectionnez **Keep approved when app requests new permissions** (Laisser approuvé quand l’application demande de nouvelles autorisations), puis cliquez sur **Enregistrer.**

## <a name="next-steps-for-android-work-profiles"></a>Prochaines étapes pour les profils professionnels Android
- [Déployer des applications de profil professionnel Android](apps-add-android-for-work.md)
- [Ajouter des stratégies de configuration de profil professionnel Android](device-profiles.md)
