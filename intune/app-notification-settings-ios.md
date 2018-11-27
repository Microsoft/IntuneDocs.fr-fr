---
title: Créer des notifications d’application pour les appareils iOS - Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez des notifications d’application pour les appareils iOS dans Microsoft Intune. Choisissez les applications auxquelles envoyer des notifications, configurez les paramètres de notification sur l’écran de verrouillage, activez le son, choisissez le type d’alerte et ajoutez un badge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2bf4919fecbba8ad4c0f3b8535adf8b97a35342e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182191"
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Configurer les paramètres des notifications d’application sur les appareils iOS dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurez la manière dont les applications installées sur un appareil iOS envoient des notifications. Ces paramètres prennent en charge les appareils supervisés exécutant iOS 9.3 et ultérieur.

## <a name="add-the-app-notification"></a>Ajouter la notification d’application

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Dans votre profil iOS ou macOS, sélectionnez **Fonctionnalités de l’appareil**. [Fonctionnalités des appareils iOS ou macOS](device-features-configure.md) répertorie les étapes de création d’un profil.
3. Sélectionnez **Notifications de l’application (mode supervisé uniquement)**, puis **Ajouter** : ![Ajouter la notification d’application dans un profil iOS ou macOS dans Intune](./media/ios-macos-app-notifications.png)
4. Entrez les propriétés suivantes :

   - **ID d’ensemble d’applications** : entrez l’**ID d’ensemble d’applications** de l’application que vous voulez configurer. Pour obtenir de l’aide, consultez la section **Référence à un ID d’ensemble pour les applications iOS intégrées** de cet article.
   - **Nom de l’application** : entrez le nom de l’application que vous voulez configurer. Ce nom ne s’affiche pas sur l’appareil et est utilisé pour vous aider à identifier l’application dans la liste.
   - **Éditeur** : indiquez l’éditeur de l’application que vous voulez configurer. Le nom de l’éditeur ne s’affiche pas sur l’appareil et est utilisé uniquement pour vous aider à identifier l’application dans la liste.
   - **Notifications** : permet d’activer ou désactiver l’envoi de notifications entre l’application et l’appareil. Si vous désactivez ce paramètre, les paramètres suivants sont également désactivés.
     - **Afficher dans le centre de notifications** : activez ce paramètre pour permettre à l’application d’afficher des notifications dans le centre de notifications de l’appareil.
     - **Afficher dans l’écran de verrouillage** : activez ce paramètre pour afficher les notifications de l’application sur l’écran de verrouillage de l’appareil.
     - **Type d’alerte** : sélectionnez le type de notification que vous voulez afficher lorsque l’appareil est déverrouillé. Plusieurs options sont possibles :
       - **Aucune** : aucune notification n’est affichée.
       - **Bannière** : une bannière s’affiche brièvement pour montrer la notification.
       - **Modal** : la notification s’affiche et l’utilisateur doit la fermer manuellement pour pouvoir continuer à utiliser l’appareil.
     - **Badge sur l’icône de l’application** : activez ce paramètre pour ajouter un badge à l’icône de l’application afin d’indiquer que l’application a envoyé une notification.
     - **Sons** : activez ce paramètre pour émettre un son quand une notification est envoyée.

5. Continuez à ajouter autant d’applications que nécessaire. Une fois toutes les applications ajoutées, sélectionnez **OK**.
6. Sélectionnez **Créer** pour enregistrer votre profil.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Référence à un ID d’ensemble pour les applications iOS intégrées

La liste suivante indique l’ID d’ensemble de quelques applications iOS intégrées parmi les plus courantes. Pour rechercher l’ID d’ensemble d’autres applications, contactez votre éditeur de logiciels.

|||
|-|-|
|Nom de l’application|ID d’ensemble|
|App Store|com.apple.AppStore|
|Calculatrice|com.apple.calculator|
|Calendrier|com.apple.mobilecal|
|Appareil photo|com.apple.camera|
|Horloge|com.apple.mobiletimer|
|Boussole|com.apple.compass|
|Contacts|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Trouver des amis|com.apple.mobileme.fmf1|
|Trouver un iPhone|com.apple.mobileme.fmip1|
|Centre de jeux|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Intégrité|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|Mappages|com.apple.Maps|
|Messages|com.apple.MobileSMS|
|Musique|com.apple.Music|
|Actualités|com.apple.news|
|Remarques|com.apple.mobilenotes|
|Nombres|com.apple.Numbers|
|Pages|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Photo|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Rappels|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Paramètres|com.apple.Preferences|
|Bourse|com.apple.stocks|
|Conseils|com.apple.tips|
|Vidéos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Portefeuille|com.apple.Passbook|
|Regardez|com.apple.Bridge|
|Météo|com.apple.weather|

## <a name="next-steps"></a>Étapes suivantes

Attribuez le profil d’appareil aux groupes de votre choix. Les étapes sont décrites dans le [Guide pratique pour attribuer des profils d’appareil](device-profile-assign.md).