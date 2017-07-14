---
title: "Applications Android avec stratégies de protection des applications"
description: "Cet article décrit ce qui se produit lorsque votre application est gérée par des stratégies de protection d’application."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 030e17a9f28a9476c82e89d4dd26151a2d3cb953
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2017
---
# Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application
<a id="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Cet article décrit l’expérience utilisateur relative aux applications avec des stratégies de protection d’application. Les stratégies de protection d’application ne s’appliquent que lorsque les applications sont utilisées dans un contexte professionnel, par exemple quand l’utilisateur accède à des applications à l’aide d’un compte professionnel ou accède à des fichiers stockés à l’emplacement OneDrive Entreprise d’une société.
##  Accéder aux applications
<a id="access-apps" class="xliff"></a>

L’application Portail d’entreprise est requise pour toutes les applications qui sont associées aux stratégies de protection d’application sur les appareils Android.

Pour les appareils qui ne sont pas inscrits dans Intune, l’application Portail d’entreprise doit être installée sur l’appareil. Toutefois, l’utilisateur n’a pas besoin de lancer l’application Portail d’entreprise ou de s’y connecter pour utiliser les applications gérées par les stratégies de protection d’application.

L’application Portail d’entreprise est un moyen pour Intune de partager des données dans un emplacement sécurisé. Ainsi, l’application Portail d’entreprise est obligatoire pour toutes les applications qui sont associés à des stratégies de protection d’application, même si l’appareil n’est pas inscrit dans Intune.


##  Utiliser des applications avec prise en charge de plusieurs identités
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

Les stratégies de protection d’application s’appliquent uniquement dans le contexte professionnel. Ainsi, l’application peut se comporter différemment selon qu’il s’agit d’un contexte professionnel ou personnel.

Par exemple, l’utilisateur reçoit une invite de code confidentiel quand il accède à des données professionnelles. Pour l’**application Outlook**, l’utilisateur est invité à entrer un code confidentiel quand il lance l’application. Pour l’**application OneDrive**, l’utilisateur est invité à entrer le code confidentiel quand il entre son compte professionnel. Pour Microsoft **Word**, **PowerPoint** et **Excel**, l’utilisateur est invité à entrer le code confidentiel quand il accède à des documents stockés à l’emplacement OneDrive Entreprise de la société.

##  Gérer les comptes d’utilisateur sur l’appareil
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

Intune prend en charge le déploiement de stratégies de protection d’application sur un seul compte d’utilisateur par appareil.

* Il est possible que le deuxième utilisateur soit bloqué sur l’appareil, mais cela dépend de l’application utilisée. Toutefois, dans tous les cas, seul le premier utilisateur sujet aux stratégies de protection d'application est affecté par la stratégie.

  * **Microsoft Word**, **Excel** et **PowerPoint** ne bloquent pas un deuxième compte d’utilisateur, mais celui-ci n’est pas affecté par les stratégies de protection d'application.

  * Pour les applications **OneDrive** et **Outlook**, vous ne pouvez utiliser qu’un seul compte professionnel.  Vous ne pouvez pas ajouter plusieurs comptes professionnels pour ces applications.  Toutefois, vous pouvez supprimer un utilisateur et en ajouter un autre sur l’appareil.


* Si un appareil possède plusieurs comptes d’utilisateurs existants avant le déploiement des stratégies de protection d’application, le premier compte sur lequel les stratégies de protection d’application sont déployées est géré par les stratégies de protection d’application Intune.


Lisez l’exemple de scénario suivant pour mieux comprendre le comportement quand il existe plusieurs comptes d’utilisateur.

L’utilisateur A travaille pour deux sociétés : **Société X** et **Société Y**. L’utilisateur A a un compte professionnel pour chaque société, et tous deux utilisent Intune pour déployer des stratégies de protection d'application. **Société X** déploie des stratégies de protection d'application **avant** **Société Y**. Le compte associé à **Société X** est soumis à la stratégie de protection d’application, contrairement au compte associé à Société Y. Si vous souhaitez que le compte d’utilisateur associé à Société Y soit géré par les stratégies de protection d’application, vous devez supprimer le compte d’utilisateur associé à Société X.
### Ajouter un deuxième compte
<a id="add-a-second-account" class="xliff"></a>
####  Android
<a id="android" class="xliff"></a>
Sur un appareil Android, un message de blocage peut s’afficher avec des instructions permettant de supprimer le compte existant et d’en ajouter un nouveau.  Pour supprimer le compte existant, accédez à **Paramètres &gt;Général &gt; Gestionnaire d’applications &gt;Portail d’entreprise**. Ensuite, choisissez **Effacer les données**.

![Capture d’écran du message d’erreur et des instructions pour supprimer le compte](./media/Android_SwitchUser.png)

##  Afficher des fichiers multimédias avec l’application Azure Information Protection
<a id="view-media-files-with-the-azure-information-protection-app" class="xliff"></a>
Pour afficher les fichiers image, AV et PDF d’entreprise sur des appareils Android, utilisez l’[application Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (anciennement « application de partage Microsoft Rights Management »).

Vous pouvez télécharger cette application à partir de Google Play Store.  

Les types de fichiers suivants sont pris en charge :

* **Audio :** AAC-LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ amélioré), AAC-ELD (AAC avec délai court amélioré), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Vidéo :** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Image :** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **Documents :** PDF, PPDF


|**pfile**|**text**|
|----|----|
|Pfile est un format « wrapper » générique pour les fichiers protégés qui encapsulent du contenu chiffré ainsi que des licences Azure Information Protection. Il peut être utilisé pour protéger tout type de fichier.|Les fichiers texte, notamment XML, CSV, et ainsi de suite, peuvent être ouverts pour être affichés dans l’application même quand ils sont protégés. Types de fichiers : .txt, .ptxt, .csv, .pcsv, .log, .plog, .xml, .pxml.|

## Étapes suivantes
<a id="next-steps" class="xliff"></a>
[Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](end-user-mam-apps-ios.md)
