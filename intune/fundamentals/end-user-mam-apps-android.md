---
title: Applications Android avec stratégies de protection des applications
description: Cet article décrit ce qui se produit lorsque votre application est gérée par des stratégies de protection d’application.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7aa439fcf60173cac71f0fc71ebac481660c785
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514691"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application

Cet article décrit l’expérience utilisateur dans les applications associées à des stratégies de protection d’application. Les stratégies de protection d’application s’appliquent uniquement quand les applications sont utilisées dans un contexte professionnel, par exemple, quand l’utilisateur accède à des applications à l’aide d’un compte professionnel ou accède à des fichiers stockés dans un emplacement OneDrive Entreprise.

## <a name="access-apps"></a>Accéder aux applications

L’application Portail d’entreprise est requise pour toutes les applications qui sont associées aux stratégies de protection d’application sur les appareils Android.

Pour les appareils qui ne sont pas inscrits dans Intune, l’application Portail d’entreprise doit être installée sur l’appareil. Toutefois, l’utilisateur n’a pas besoin de lancer l’application Portail d’entreprise ou de s’y connecter pour utiliser les applications gérées par les stratégies de protection d’application.

L’application Portail d’entreprise est un moyen pour Intune de partager des données dans un emplacement sécurisé. Ainsi, l’application Portail d’entreprise est obligatoire pour toutes les applications qui sont associés à des stratégies de protection d’application, même si l’appareil n’est pas inscrit dans Intune.

## <a name="use-apps-with-multi-identity-support"></a>Utiliser des applications avec prise en charge de plusieurs identités

Les stratégies de protection d’application s’appliquent uniquement dans le contexte professionnel. Ainsi, l’application peut se comporter différemment selon qu’il s’agit d’un contexte professionnel ou personnel.

Par exemple, l’utilisateur reçoit une invite de code confidentiel quand il accède à des données professionnelles. Pour l’**application Outlook**, l’utilisateur est invité à entrer un code confidentiel quand il lance l’application. Pour l’**application OneDrive**, l’utilisateur est invité à entrer le code confidentiel quand il entre son compte professionnel. Pour Microsoft **Word**, **PowerPoint** et **Excel**, l’utilisateur est invité à entrer le code confidentiel quand il accède à des documents stockés à l’emplacement OneDrive Entreprise de la société.

## <a name="manage-user-accounts-on-the-device"></a>Gérer les comptes d’utilisateur sur l’appareil

Les applications avec plusieurs identités permettent aux utilisateurs d’ajouter plusieurs comptes.  Intune APP prend en charge un seul compte géré.  Intune APP ne limite pas le nombre de comptes non gérés.

Quand une application contient un compte géré :

* Si un utilisateur tente d’ajouter un deuxième compte géré, il est invité à sélectionner le compte géré à utiliser.  L’autre compte est supprimé.
* Si l’administrateur informatique ajoute une stratégie à un deuxième compte existant, l’utilisateur est invité à sélectionner le compte géré à utiliser.  L’autre compte est supprimé.

Lisez l’exemple de scénario suivant pour mieux comprendre le comportement quand il existe plusieurs comptes d’utilisateur.

L’utilisateur A travaille pour deux sociétés : **Société X** et **Société Y**. L’utilisateur A a un compte professionnel pour chaque société, et tous deux utilisent Intune pour déployer des stratégies de protection d'application. La **Société X** déploie des stratégies de protection d'application **avant** la  **Société Y**. Le compte associé à **Société X** obtient la stratégie de protection d’application, contrairement au compte associé à Société Y. Si vous souhaitez que le compte d’utilisateur associé à Société Y soit géré par les stratégies de protection d’application, vous devez supprimer le compte d’utilisateur associé à Société X et ajouter le compte associé à Société Y.

### <a name="add-a-second-account"></a>Ajouter un deuxième compte

#### <a name="android"></a>Android

Sur un appareil Android, un message de blocage peut s’afficher avec des instructions permettant de supprimer le compte existant et d’en ajouter un nouveau.  Pour supprimer le compte existant, accédez à **Paramètres &gt;Général &gt; Gestionnaire d’applications &gt;Portail d’entreprise**. Ensuite, choisissez **Effacer les données**.

![Capture d’écran du message d’erreur et des instructions pour supprimer le compte](./media/end-user-mam-apps-android/Android_SwitchUser.png)

## <a name="view-media-files-with-the-azure-information-protection-app"></a>Afficher des fichiers multimédias avec l’application Azure Information Protection

Pour afficher les fichiers image, AV et PDF d’entreprise sur des appareils Android, utilisez l’[application Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (anciennement « application de partage Microsoft Rights Management »).

Vous pouvez télécharger cette application à partir de Google Play Store.  

Les types de fichiers suivants sont pris en charge :

* **Audio :** AAC-LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ amélioré), AAC-ELD (AAC avec délai court amélioré), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Vidéo :** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Image :** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **Documents :** PDF, PPDF

|**pfile**|
|----|
|Pfile est un format « wrapper » générique pour les fichiers protégés qui encapsulent du contenu chiffré ainsi que des licences Azure Information Protection. Il peut être utilisé pour protéger tout type de fichier.|

## <a name="next-steps"></a>Étapes suivantes
[Ce qui se passe quand l’application iOS/iPadOS est gérée par des stratégies de protection d’applications](end-user-mam-apps-ios.md)
