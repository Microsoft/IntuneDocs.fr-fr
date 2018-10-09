---
title: Applications Android avec stratégies de protection des applications
titlesuffix: Microsoft Intune
description: Découvrez ce qui vous attend dans le cas d’une application Android associée à des stratégies de protection.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e8c606f9b304f91e02ba977c801bd8de18682612
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231693"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Découvrez ce qui vous attend dans le cas d’applications Android associées à des stratégies de protection d’application. Les stratégies de protection d’application ne sont appliquées que si les applications sont utilisées dans le contexte professionnel. C’est le cas par exemple quand vous accédez à une application avec un compte professionnel ou à des fichiers stockés dans l’emplacement OneDrive de votre entreprise.
##  <a name="accessing-apps"></a>Accès aux applications

L’application Portail d’entreprise est obligatoire pour toutes les applications associées à des stratégies de protection d’application sur des appareils Android.

Installez le Portail d’entreprise sur tous les appareils qui ne sont pas inscrits dans Intune. Les utilisateurs ne sont pas contraints de se connecter à l’application Portail d’entreprise pour utiliser des applications associées à des stratégies de protection d’application.
L’application Portail d’entreprise vous permet de partager des données dans un emplacement sécurisé. Elle est donc nécessaire même pour les appareils non inscrits.


##  <a name="using-apps-with-multi-identity-support"></a>Utilisation d’applications avec prise en charge de plusieurs identités

Les stratégies de protection d’application n’entrent en vigueur qu’au moment où un utilisateur tente d’accéder à des données professionnelles.  Vous pouvez constater des comportements différents si l’utilisateur accède à l’application pour une utilisation personnelle.

Certaines applications prennent en charge plusieurs identités. Dans ce cas, Intune n’applique les stratégies de protection d’application qu’au moment où un utilisateur accède à des données professionnelles.  Par exemple, un utilisateur peut recevoir une invite lui demandant d’entrer un code PIN.  Dans **l’application Outlook**, une invite s’affiche quand un utilisateur lance l’application. Dans **l’application OneDrive**, une invite s’affiche quand un utilisateur tape le compte professionnel.  Dans Microsoft **Word**, **PowerPoint** et **Excel**, une invite s’affiche quand un utilisateur accède à des documents d’entreprise sur OneDrive.
##  <a name="managing-user-accounts-on-the-device"></a>Gestion des comptes d’utilisateur sur l’appareil

Intune prend en charge le déploiement de stratégies de protection d’application sur un seul compte d’utilisateur par appareil.

* Il est possible que le deuxième utilisateur soit bloqué sur l’appareil, mais cela dépend de l’application utilisée. Toutefois, dans tous les cas, seul le premier utilisateur sujet aux stratégies de protection d'application est affecté par la stratégie.

  * **Microsoft Word**, **Excel** et **PowerPoint** ne bloquent pas l’accès à un compte d’utilisateur supplémentaire. Toutefois, le compte d’utilisateur n’est pas affecté par les stratégies de protection d’application.

  * Pour les **applications OneDrive et Outlook**, vous ne pouvez utiliser qu’un seul compte professionnel.  L’ajout de plusieurs comptes professionnels est bloqué sur ces applications.  Toutefois, vous pouvez supprimer un utilisateur d’un appareil, puis en ajouter un autre.


* Avant le déploiement de la stratégie de protection application, un appareil peut avoir plusieurs comptes d’utilisateur existants. Dans ce cas, le premier compte sur lequel les stratégies de protection d’application sont déployées est géré par les stratégies de protection d’application Intune.


Lisez l’exemple de scénario suivant pour découvrir comment Intune gère plusieurs comptes d’utilisateur.

L’utilisateur A travaille pour deux sociétés : **Société X** et **Société Y**. L’utilisateur A a un compte professionnel pour chaque société, et tous deux utilisent Intune pour déployer des stratégies de protection d'application. **Société X** déploie des stratégies de protection d'application **avant** **Société Y**. Le compte associé à **Société X** est soumis à la stratégie de protection d’application, contrairement au compte associé à Société Y. Pour que le compte d’utilisateur associé à Société Y soit géré par les stratégies de protection d’application, l’utilisateur A doit supprimer le compte d’utilisateur de la Société X.
### <a name="adding-a-second-account"></a>Ajout d’un deuxième compte
####  <a name="android"></a>Android
Vous pouvez également être invité à supprimer le compte existant et à en ajouter un nouveau.  Pour supprimer le compte existant, accédez à **Paramètres &gt;Général &gt; Gestionnaire d’applications &gt;Portail d’entreprise. Ensuite, sélectionnez « Effacer les données ».**

![Capture d’écran du message d’erreur et des instructions pour supprimer le compte](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Affichage des fichiers multimédias avec l’application Azure Information Protection (anciennement Rights Management)
Pour afficher les fichiers image, AV et PDF d’entreprise sur des appareils Android, utilisez l’[application Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Vous pouvez télécharger cette application à partir de la boutique Google Play.  

Les types de fichiers suivants sont pris en charge :

* **Audio :** AAC-LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ amélioré), AAC-ELD (AAC avec délai court amélioré), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Vidéo :** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Image :** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **Documents :** PDF, PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>text</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile est un format « wrapper » générique pour les fichiers protégés. Il encapsule le contenu chiffré et les licences Azure Information Protection. Il peut être utilisé pour protéger tout type de fichier. | Les fichiers texte, notamment XML, CSV, etc., peuvent être ouverts pour être affichés dans l’application même quand ils sont protégés. Types de fichiers : txt, ptxt, csv, pcsv, log, plog, xml, pxml. |

---------------
## <a name="next-steps"></a>Étapes suivantes
[Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Voir aussi
[Créer et déployer des stratégies de protection d’application à l’aide de Microsoft Intune](app-protection-policies.md)
