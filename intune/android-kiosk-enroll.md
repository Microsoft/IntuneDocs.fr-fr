---
title: Configurer l’inscription Intune pour les appareils Android Entreprise dédiés
titlesuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android Entreprise dédiés dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b3ced7e52de05e98c2f4a7ec9a828972ab60cf71
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290721"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Configurer l’inscription Intune d’appareils Android Entreprise dédiés

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android prend en charge les appareils appartenant à l’entreprise, à usage unique et kiosque avec son ensemble de solutions pour appareils dédiés. Ces appareils sont destinés à un usage unique, tel que la signalisation numérique, l’impression de ticket ou la gestion des stocks, pour n’en nommer que quelques-uns. Les administrateurs verrouillent l’utilisation d’un appareil pour un ensemble limité d’applications et de liens web. Les utilisateurs ne peuvent pas non plus ajouter d’autres applications ou effectuer d’autres actions sur l’appareil.

Intune vous aide à déployer des applications et des paramètres sur des appareils Android dédiés. Pour plus d’informations sur Android Entreprise, consultez [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Les appareils que vous gérez de cette façon sont inscrits dans Intune sans compte d’utilisateur et ne sont associés à aucun utilisateur final. Ils ne sont pas conçus pour les applications à usage personnel, ni pour celles qui exigent un grand nombre de données de compte propres à l’utilisateur, comme Outlook ou Gmail.

## <a name="device-requirements"></a>Exigences relatives aux périphériques

Les appareils doivent respecter les exigences suivantes pour pouvoir être gérés en tant qu’appareils Android Entreprise dédiés :

- Système d’exploitation Android version 5.1 et ultérieures.
- Les appareils doivent exécuter une distribution d’Android qui dispose d’une connectivité GMS (Google Mobile Services). Les appareils doivent avoir accès à GMS et doivent pouvoir s’y connecter.

## <a name="set-up-android-dedicated-device-management"></a>Configurer la gestion d’appareils Android dédiés

Pour configurer la gestion d’appareils Android dédiés, effectuez les étapes suivantes :

1. Pour préparer la gestion des appareils mobiles, vous devez [définir l’autorité de gestion des appareils mobiles (MDM) sur **Microsoft Intune**](mdm-authority-set.md) afin d’obtenir des instructions. Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.
2. [Connectez votre compte de locataire Intune à votre compte d’entreprise Android](connect-intune-android-enterprise.md).
3. [Créez un profil d’inscription.](#create-an-enrollment-profile)
4. [Créez un groupe d’appareils.](#create-a-device-group)
5. [Inscrire les appareils dédiés](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Créer un profil d’inscription

Vous devez créer un profil d’inscription pour pouvoir inscrire vos appareils dédiés. Quand le profil est créé, vous obtenez un jeton d’inscription (chaîne aléatoire) et un code QR. En fonction du système d’exploitation Android et de la version de l’appareil, vous pouvez utiliser le jeton ou le code QR pour [inscrire l’appareil dédié](#enroll-the-dedicated-devices).

1. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Inscription de l’appareil** > **Inscription Android** > **Inscriptions d’appareils en mode kiosque et tâche**.
2. Choisissez **Créer** et remplissez les champs requis.
    - **Nom** : tapez un nom que vous utiliserez lors de l’affectation du profil au groupe d’appareils dynamique.
    - **Date d’expiration du jeton** : Date à laquelle le jeton expirera. Google applique un maximum de 90 jours.
3. Sélectionnez **Créer** pour enregistrer le profil.

### <a name="create-a-device-group"></a>Créer un groupe d'appareils

Vous pouvez cibler des applications et des stratégies à des groupes d’appareils dynamiques ou affectés. Vous pouvez configurer des groupes d’appareils AAD dynamiques de façon à spécifier automatiquement des appareils qui sont inscrits avec un profil d’inscription particulier en suivant ces étapes :

1. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Groupes** > **Tous les groupes** > **Nouveau groupe**.
2. Dans le panneau **Groupe**, renseignez les champs obligatoires comme suit :
    - **Type de groupe** : Sécurité
    - **Nom du groupe** : tapez un nom intuitif (par exemple, « appareils de l’usine n°1 »)
    - **Type d’appartenance** : appareil dynamique
3. Choisissez **Ajouter une requête dynamique**.
4. Dans le panneau **Règles d’appartenance dynamique**, renseignez les champs comme suit :
    - **Ajouter une règle d’appartenance dynamique** : règle simple
    - **Ajouter des appareils où** : nom_profil_inscription
    - Dans la zone du milieu, choisissez **Correspondance**.
    - Dans le dernier champ, entrez le nom du profil d’inscription que vous avez créé.
    Pour plus d’informations sur les règles d’appartenance dynamique, consultez [Règles d’appartenance dynamique pour les groupes dans AAD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Choisissez **Ajouter une requête** > **Créer**.

### <a name="replace-or-remove-tokens"></a>Remplacer ou supprimer des jetons

Vous pouvez remplacer ou supprimer des jetons et des codes QR.

- **Remplacer le jeton** : vous pouvez générer un nouveau jeton/code QR quand sa date d’expiration approche à l’aide de l’option Remplacer le jeton.
- **Révoquer le jeton** : vous pouvez révoquer le jeton/code QR pour qu’il expire immédiatement. À partir de ce moment-là, le jeton/code QR n’est plus utilisable. Vous pouvez utiliser cette option si vous :
    - partagez accidentellement le jeton/code QR avec un tiers non autorisé.
    - effectuez toutes les inscriptions et n’avez plus besoin du jeton/code QR.

Le remplacement ou la révocation d’un jeton/code QR n’a aucun effet sur les appareils qui sont déjà inscrits.

1. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Inscription de l’appareil** > **Inscription Android** > **Inscriptions d’appareils en mode kiosque et tâche**.
2. Choisissez le profil à utiliser.
3. Choisissez **Jeton**.
4. Pour remplacer le jeton, choisissez **Remplacer le jeton**.
5. Pour révoquer le jeton, choisissez **Révoquer le jeton**.

## <a name="enroll-the-dedicated-devices"></a>Inscrire les appareils dédiés

Vous pouvez à présent [inscrire vos appareils dédiés](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-dedicated-devices"></a>Gestion d’applications sur des appareils Android dédiés

Seules les applications dont le type Affectation [a la valeur Obligatoire](apps-deploy.md#assign-an-app) peuvent être installées sur des appareils Android dédiés. Les applications sont installées à partir du store Google Play géré de la même manière que les appareils avec profil professionnel Android.

Les applications sont mises à jour automatiquement sur les appareils gérés quand le développeur d’application publie une mise à jour sur Google Play.

Pour supprimer une application des appareils Android dédiés, vous pouvez effectuer l’une des opérations suivantes :
-   Supprimez le déploiement d’application Obligatoire.
-   Créez un déploiement de désinstallation pour l’application.

## <a name="next-steps"></a>Étapes suivantes
- [Déployer des applications Android](apps-deploy.md)
- [Ajouter des stratégies de configuration Android](device-profiles.md)
