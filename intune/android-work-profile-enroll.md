---
title: Inscrire des appareils avec profil professionnel Android Entreprise dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils avec profil professionnel Android Entreprise dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66574fe66f90b73d8ebf5835c5b16e93276579e4
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568217"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurer l’inscription des appareils avec profil professionnel Android Entreprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune vous permet de déployer des applications et des paramètres sur des appareils avec profil professionnel Android Entreprise de manière à ce que les informations professionnelles soient séparées des informations personnelles. Pour plus d’informations sur Android Entreprise, consultez [Exigences Android Entreprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Pour configurer la gestion des profils professionnels Android Entreprise, effectuez les étapes suivantes :

1. [Connectez votre compte de locataire Intune à votre compte Android Entreprise](connect-intune-android-enterprise.md).
2. Spécifiez les paramètres d’inscription de profil professionnel Android Entreprise. Les profils professionnels Android Entreprise sont [pris en charge uniquement sur certains appareils Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Tout appareil qui prend en charge les profils professionnels Android Entreprise prend également en charge la gestion Android conventionnelle. Intune vous permet de spécifier la façon dont les appareils qui prennent en charge les profils professionnels Android Entreprise doivent être gérés dans [Restrictions d’inscription](enrollment-restrictions-set.md).
    - **Bloquer (défini par défaut)** :  Tous les appareils Android, notamment ceux qui prennent en charge les profils professionnels Android Entreprise, sont inscrits comme des appareils Android conventionnels.
    - **Autoriser** : Tous les appareils qui prennent en charge les profils professionnels Android Entreprise sont inscrits comme des appareils avec profil professionnel Android Entreprise. Tout appareil Android qui ne prend pas en charge les profils professionnels Android Entreprise est inscrit comme appareil Android conventionnel.
3. [Indiquez à vos utilisateurs comment inscrire leurs appareils](/intune-user-help/enroll-your-device-in-intune-android).


Si vous voulez inscrire des appareils avec des profils professionnels Android Entreprise, mais que ces appareils étaient auparavant inscrits comme appareils Android ordinaires, vous devez d’abord les désinscrire, puis les réinscrire.

Si vous inscrivez des appareils avec profils professionnels Android Entreprise à l’aide d’un compte de [Gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md), il existe une limite de 10 appareils pouvant être inscrits par compte.

Pour plus d’informations, consultez [Données envoyées par Intune à Google](data-intune-sends-to-google.md).

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Approuver l’application Portail d’entreprise dans le Google Play Store géré

Pour être sûr que les utilisateurs ont toujours accès à la version la plus récente de l’application Portail d’entreprise, vous devez approuver l’application Portail d’entreprise pour Android dans le store Google Play géré. En l’approuvant, vous garantissez que chaque utilisateur reçoit des mises à jour automatiques. Si vous ne l’approuvez pas, le portail d’entreprise finit par devenir obsolète et risque de ne pas recevoir les correctifs de bogues importants ou les nouvelles fonctionnalités publiés par Microsoft.

Pour approuver le portail d’entreprise Intune, effectuez les étapes suivantes :

1.  Accédez à l’application Portail d’entreprise sur le [Google Play Store géré](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Connectez-vous au Google Play Store géré avec le même compte Google que celui utilisé pour configurer la liaison pour Android Entreprise.
3.  Cliquez sur **Approuver** ; une nouvelle boîte de dialogue s’ouvre.
4.  Vérifiez les autorisations dans cette boîte de dialogue, puis cliquez sur **Approuver**. Vous devez affecter ces autorisations afin de permettre à l’application Portail d’entreprise de gérer le profil professionnel sur l’appareil.
5.  Sélectionnez **Keep approved when app requests new permissions** (Laisser approuvé quand l’application demande de nouvelles autorisations), puis cliquez sur **Enregistrer.**

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Étapes suivantes pour les profils professionnels Android Entreprise
- [Déplacer des applications avec profil professionnel Android Entreprise](apps-add-android-for-work.md)
- [Ajouter des stratégies de configuration de profil professionnel Android Entreprise](device-profiles.md)
