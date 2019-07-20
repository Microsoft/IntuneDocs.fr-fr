---
title: Supprimer votre appareil iOS d’Intune | Microsoft Docs
description: Explique comment supprimer un appareil iOS d’Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2eb47240516737f03c10d1280887fea275c5ed99
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883937"
---
# <a name="remove-your-ios-device-from-intune"></a>Supprimer votre appareil iOS d’Intune

Quand vous supprimez votre appareil iOS d’Intune, ce dernier ne peut plus accéder aux ressources de l’entreprise et n’est plus géré par Intune.


## <a name="removing-the-device-from-my-devices"></a>Suppression de l’appareil de Mes appareils

Pour supprimer votre appareil d’Intune, suivez ces étapes ou regardez cette vidéo :


1. Dans l’application Portail d’entreprise, appuyez sur **Appareils** et sélectionnez l’appareil que vous voulez désinscrire. Si vous avez un seul appareil, quand vous appuyez sur **Appareils**, accédez directement à l’écran des détails de l’appareil.

2. À côté de **RENOMMER**, appuyez sur le bouton de sélection > **Supprimer l’appareil** > **Supprimer**.  

    |![Capture d’écran de l’écran Appareils de l’application Portail d’entreprise, montrant les options une fois que l’utilisateur a cliqué sur Supprimer. Montre les boutons « Supprimer l’appareil », « Réinitialisation aux paramètres d’usine » et « Annuler ».](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Capture d’écran de l’écran Appareils de l’application Portail d’entreprise, montrant les options une fois que l’utilisateur a cliqué sur le bouton Supprimer l’appareil. Montre le bouton « Supprimer » en rouge, le bouton « En savoir plus » en bleu et le bouton « Annuler ».](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


    La désinscription de votre appareil d’Intune a les conséquences suivantes :

    - Votre appareil n’apparaît plus dans le portail d’entreprise.

    - Vous ne pouvez plus installer d’applications à partir du portail d’entreprise.

    - Les paramètres que vous avez modifiés au moment d’ajouter l’appareil (par exemple, le fait de désactiver l’appareil photo ou d’imposer une certaine longueur de mot de passe) ne s’appliquent plus.

    - Il se peut que vous n'ayez plus accès à certaines ressources de l'entreprise, telles que les partages de fichiers ou les sites Web internes.

    - Vous ne pouvez plus utiliser les applications et les données d'entreprise sur votre appareil.

    - Vous ne pourrez peut-être plus vous connecter au réseau de votre entreprise via le Wi-Fi ou un réseau privé virtuel (VPN).

    - Les profils de messagerie d'entreprise sont supprimés de l'appareil.

    - Les appareils configurés pour la messagerie uniquement n’apparaissent plus dans l’application ou le site web Portail d’entreprise.

    - Les applications sont désinstallées. Les données des applications de l'entreprise sont supprimées.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Suppression des données collectées par l’application Portail d’entreprise

Il existe trois emplacements où le portail d’entreprise stocke des données locales sur votre appareil.

- **Journaux d’information** : les données standard de l’activité de l’application que Microsoft collecte, comme la durée pendant laquelle l’application reste ouverte ou si elle a planté, sont automatiquement effacées quand vous supprimez l’appareil du portail d’entreprise.

- **Apple analytics** : données standard de plantage de l’application que collecte Apple. Ces informations peuvent être supprimées seulement en réinitialisant votre appareil aux paramètres d’usine. Cette opération efface toutes vos informations personnelles de votre appareil. Pour ce faire, ouvrez **Réglages** > **Général** > **Réinitialiser** > **Effacer contenu et réglages**.

- **Keychain** : votre appareil stocke vos mots de passe et autres informations utilisées pour les connexions dans votre Keychain. Les applications Microsoft partagent vos informations de connexion avec toutes les applications développées par Microsoft présentes sur votre appareil, notamment Microsoft Outlook et Microsoft Authenticator. Comme avec Apple analytics, ces informations peuvent être supprimées seulement en réinitialisant votre appareil aux paramètres d’usine. Cette opération efface toutes vos informations personnelles de votre appareil. Pour ce faire, ouvrez **Réglages** > **Général** > **Réinitialiser** > **Effacer contenu et réglages**.


Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
