---
title: Inscrire des appareils kiosque d’entreprise Android dans Intune
titlesuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils kiosque d’entreprise Android dans Intune.
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
ms.custom: seodec18
ms.openlocfilehash: 5a84bcd820b7596d1b1df01342604562c7853140
ms.sourcegitcommit: a44359b426e19b8bf4b99eca6af2755c6d3c6fb8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54098315"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-kiosk-devices"></a>Configurer l’inscription d’appareils kiosque d’entreprise Android dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android prend en charge les appareils kiosque avec son ensemble de solutions [Appareils dédiés](https://developers.google.com/android/work/overview#company-owned-devices-for-dedicated-use). Ces appareils sont destinés à un usage unique, tel que la signalisation numérique, l’impression de ticket ou la gestion des stocks, pour n’en nommer que quelques-uns. Les administrateurs verrouillent l’utilisation d’un appareil pour un ensemble limité d’applications et de liens web. Les utilisateurs ne peuvent pas non plus ajouter d’autres applications ou effectuer d’autres actions sur l’appareil.

Intune vous aide à déployer des applications et des paramètres sur des appareils kiosque Android. Pour plus d’informations sur Android Entreprise, consultez [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Les appareils que vous gérez de cette façon sont inscrits dans Intune sans compte d’utilisateur et ne sont associés à aucun utilisateur final. Ils ne sont pas conçus pour les applications à usage personnel, ni pour celles qui exigent un grand nombre de données de compte propres à l’utilisateur, comme Outlook ou Gmail.

## <a name="device-requirements"></a>Exigences relatives aux périphériques

Les appareils doivent respecter les conditions requises suivantes pour être gérés en tant qu’appareils kiosque d’entreprise Android :

- Système d’exploitation Android version 5.1 et ultérieures.
- Les appareils doivent exécuter une distribution d’Android qui dispose d’une connectivité GMS (Google Mobile Services). Les appareils doivent avoir accès à GMS et doivent pouvoir s’y connecter.

## <a name="set-up-android-kiosk-management"></a>Configurer la gestion des appareils kiosque Android

Pour configurer la gestion des appareils kiosque Android, effectuez les étapes suivantes :

1. Pour préparer la gestion des appareils mobiles, vous devez [définir l’autorité de gestion des appareils mobiles (MDM) sur **Microsoft Intune**](mdm-authority-set.md) afin d’obtenir des instructions. Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.
2. [Connectez votre compte de locataire Intune à votre compte d’entreprise Android](connect-intune-android-enterprise.md).
3. [Créez un profil d’inscription.](#create-an-enrollment-profile)
4. [Créez un groupe d’appareils.](#create-a-device-group)
5. [Inscrivez les appareils kiosque.](#enroll-the-kiosk-devices)

### <a name="create-an-enrollment-profile"></a>Créer un profil d’inscription

Vous devez créer un profil d’inscription afin de pouvoir inscrire vos appareils kiosque. Quand le profil est créé, vous obtenez un jeton d’inscription (chaîne aléatoire) et un code QR. En fonction du système d’exploitation Android et de la version de l’appareil, vous pouvez utiliser le jeton ou le code QR pour [inscrire l’appareil kiosque](#enroll-the-kiosk-devices).

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

## <a name="enroll-the-kiosk-devices"></a>Inscrire les appareils kiosque

Une fois que vous avez créé le profil d’inscription et le groupe d’appareils dynamique, vous pouvez inscrire vos appareils kiosque. La façon dont vous inscrivez vos appareils Android varie en fonction du système d’exploitation.

| Méthode d’inscription | Version de système d’exploitation Android minimale prise en charge |
| ----- | ----- |
| Communication en champ proche (NFC) | 5.1 |
| Entrée de jeton | 6.0 |
| Code QR | 7.0 |
| Zero Touch | 8.0, avec les fabricants participants |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Inscrire à l’aide de NFC

Pour les appareils Android 5.1 et ultérieur qui prennent en charge NFC, vous pouvez provisionner vos appareils en créant une balise NFC spécialement mise en forme. Vous pouvez utiliser votre propre application ou n’importe quel outil de création de balise NFC. Pour plus d’informations, consultez la [documentation sur les API de gestion Android de Google](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Inscrire à l’aide d’un jeton

Pour les appareils Android 6 et ultérieur, vous pouvez utiliser le jeton pour inscrire l’appareil. Android version 6.1 et ultérieure peut également tirer profit de l’analyse de code QR quand la méthode d’inscription **afw#setup** est utilisée.

1. Allumez votre appareil réinitialisé.
2. Sur l’écran de **Bienvenue**, sélectionnez votre langue.
3. Connectez-vous à votre réseau **Wi-Fi**, puis choisissez **Suivant**.
4. Acceptez les conditions de Google, puis choisissez **Suivant**.
5. Sur l’écran de connexion de Google, entrez **afw#setup** au lieu d’un compte Gmail, puis choisissez **Suivant**.
6. Choisissez **Installer** pour l’application **Stratégie de l’appareil Android**.
7. Poursuivez l’installation de cette stratégie.  Certains appareils peuvent nécessiter l’acceptation de conditions supplémentaires. 
8. Sur l’écran **Inscrire cet appareil**, autorisez votre appareil à scanner le code QR ou choisissez d’entrer le jeton manuellement.
9. Suivez les invites à l’écran pour terminer l’inscription. 

### <a name="enroll-by-using-a-qr-code"></a>Inscrire à l’aide d’un code QR

Sur les appareils Android 7 et ultérieur, vous pouvez scanner le code QR à partir du profil d’inscription pour inscrire l’appareil.

> [!Note]
> Le zoom du navigateur peut empêcher les appareils d’analyser le code QR. L’augmentation du zoom du navigateur résout le problème.

1. Pour lancer une lecture de code QR sur l’appareil Android, appuyez plusieurs fois sur le premier écran visible après une réinitialisation.
2. Pour les appareils Android 7 et 8, vous serez invité à installer un lecteur de code QR. Les appareils Android 9 et ultérieur ont déjà un lecteur de code QR installé.
3. Utilisez le lecteur de code QR pour scanner le code QR du profil d’inscription, puis suivez les invites à l’écran pour effectuer l’inscription.

### <a name="enroll-by-using-google-zero-touch"></a>S’inscrire à l’aide de Google Zero Touch

Pour utiliser le système Zero Touch de Google, l’appareil doit le prendre en charge et être affilié à un fournisseur qui fait partie du service.  Pour plus d’informations, consultez [le site web du programme Zero Touch de Google](https://www.android.com/enterprise/management/zero-touch/). 


1. Créez une configuration dans la console Zero Touch.
2. Choisissez **Microsoft Intune** dans la liste déroulante EMM DPC.
3. Dans la console Zero Touch de Google, copiez/collez le code JSON suivant dans le champ de suppléments DPC. Remplacez la chaîne *YourEnrollmentToken* par le jeton d’inscription que vous avez créé dans le cadre de votre profil d’inscription. Veillez à entourer le jeton d’inscription dans des guillemets doubles.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Choisissez **Appliquer**.

## <a name="managing-apps-on-android-kiosk-devices"></a>Gestion d’applications sur des appareils kiosque Android

Seules les applications qui ont le type d’affectation [défini sur Obligatoire](apps-deploy.md#to-assign-an-app) peuvent être installées sur des appareils kiosque Android. Les applications sont installées à partir du store Google Play géré de la même manière que les appareils avec profil professionnel Android.

Les applications sont mises à jour automatiquement sur les appareils gérés quand le développeur d’application publie une mise à jour sur Google Play.

Pour supprimer une application des appareils kiosque Android, vous pouvez effectuer l’une des opérations suivantes :
-   Supprimez le déploiement d’application Obligatoire.
-   Créez un déploiement de désinstallation pour l’application.


## <a name="next-steps"></a>Étapes suivantes
- [Déployer des applications kiosque Android](apps-deploy.md)
- [Ajouter des stratégies de configuration kiosque Android](device-profiles.md)
