---
title: L’optimisation de l’alimentation empêche l’accès à l’e-mail | Microsoft Docs
description: Découvrez comment désactiver l’optimisation de l’alimentation pour Android pour être certain d’obtenir vos e-mails.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98b8d4636b3f402b2b7246311e8027722fa01953
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838104"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Outlook ne synchronise pas l’e-mail géré quand l’optimisation de la batterie pour Android est activée

> [!IMPORTANT]
> Ce problème est documenté ici, car nous recevons à ce sujet un nombre croissant de messages de clients. Si ce problème persiste après avoir suivi ces étapes, demandez de l’aide au [support technique de votre entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).

En inscrivant votre appareil dans Intune, vous pouvez accéder aux ressources de l’entreprise. L’une des ressources les plus courantes est l’accès à l’e-mail. Dans le cas des appareils Android, nous avons constaté que l’accès à l’e-mail via Outlook pouvait être contrarié quand l’optimisation de la batterie était activée. Or, cette fonctionnalité peut être activée automatiquement pour optimiser l’autonomie de votre appareil. Cette intention louable est toutefois contrariée par le fait qu’elle tente d’interrompre le téléchargement automatique du courrier électronique.

L’équipe Microsoft Intune s’emploie énergiquement à trouver une solution à ce problème. Un moyen d’empêcher l’appareil de passer en mode de faible alimentation est de veiller à ce que la batterie conserve une charge supérieure à 30 %. Pour éviter que le problème se produise quand vous passez en mode de faible alimentation, supprimez le portail d’entreprise et Outlook de la liste des applications affectées par les paramètres d’optimisation de la batterie et d’économie d’énergie.

Les appareils Android sont produits par un grand nombre de fabricants différents. Nous ne pouvons pas documenter les procédures exactes pour chaque appareil. Vous serez peut-être amené à effectuer cette opération dans vos paramètres système ou même dans certains paramètres propres au fabricant. À travers plusieurs exemples courants, nous vous expliquons comment résoudre ce problème sur les appareils Android.

## <a name="unmodified-android-devices"></a>Appareils Android non modifiés

De nombreux fabricants ajoutent des modifications à leurs appareils Android. Cela peut changer quelque peu la façon dont vous interagissez avec l’appareil. Tel est le cas des thèmes et des notifications. En règle générale, Google n’apporte pas ce type de modification à leurs téléphones. Par exemple, sur un appareil Google Pixel équipé d’Android version 7.0 ou ultérieure, voici les étapes à suivre pour ôter ces applications de l’optimisation de la batterie :

1. Ouvrez **Settings** (Paramètres).
2. Appuyez sur **Battery** (Batterie) > **More** (Plus) > **Battery optimization** (Optimisation de la batterie).
3. Appuyez sur la flèche vers le bas, puis sur **Not optimized** (Non optimisé).
4. Sélectionnez les applications Portail d’entreprise et Outlook, puis désactivez l’optimisation de batterie.

## <a name="samsung-devices"></a>Appareils Samsung

Pour d’autres types d’appareils Android, tels que les appareils Samsung équipés d’Android version 7.0 ou ultérieure, les étapes à suivre pour ôter les applications Outlook et Portail d’entreprise de l’optimisation de la batterie sont quelque peu différentes.

1. Ouvrez **Settings** (Paramètres).
2. Appuyez sur **Menu (...)**  > **Special access** (Accès spécial) > **Optimize battery usage** (Optimiser l’utilisation de la batterie).
3. Sélectionnez **All apps** (Toutes les applications) dans la liste déroulante.
4. Mettez le bouton bascule en regard des applications Portail d’entreprise et Outlook en position **Off** (Désactivé) pour désactiver l’optimisation de batterie.

Par ailleurs, si vous utilisez un appareil Samsung doté d’une version antérieure d’Android, voici comment procéder pour ôter ces applications du mode économie d’énergie.

1. Ouvrez **Settings** (Paramètres).
2. Appuyez sur **Device maintenance** (Maintenance de l’appareil) > **Battery** (Batterie) > **Unmonitored apps** (Applications non surveillées).
3. Appuyez sur **Add apps** (Ajouter des applications).
4. Sélectionnez les applications Portail d’entreprise et Outlook, puis appuyez sur **Done** (Terminé).

## <a name="oneplus-devices"></a>Appareils OnePlus

Un autre moyen de trouver ces paramètres est d’effectuer une recherche dans les paramètres système. Par exemple, sur un OnePlus 3 équipé d’Android 7.1.1, voici comment procéder : 

1. Ouvrez **System Settings** (Paramètres système). 
2. Appuyez sur le bouton **Search** (Rechercher). Il s’agit de la loupe située à haut à droite de l’écran. 
3. Tapez **battery optimization** (optimisation de la batterie) dans la recherche, puis sélectionnez l’option **Battery Optimization** (Optimisation de la batterie) dans l’écran **Settings** (Paramètres) qui s’affiche. 
4. Appuyez sur **Battery**(Batterie) > **Battery optimization**(Optimisation de la batterie).
5. Sélectionnez les applications Portail d’entreprise et Outlook, puis appuyez sur **Don’t optimize** (Ne pas optimiser). Appuyez sur **Terminé**.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses informations de contact, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
