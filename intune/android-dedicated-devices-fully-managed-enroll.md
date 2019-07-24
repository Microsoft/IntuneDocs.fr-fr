---
title: Inscrire des appareils dédiés Android Entreprise ou des appareils entièrement gérés dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android Entreprise dédiés ou entièrement gérés dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c13ebdd6cf908a62c99d4c81443c94ce6a07d8e
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353825"
---
# <a name="enroll-your-android-enterprise-dedicated-devices-or-fully-managed-devices-preview"></a>Inscrire vos appareils Android Entreprise dédiés ou entièrement gérés (préversion)

Après avoir configuré vos [appareils Android Entreprise dédiés](android-kiosk-enroll.md) ou [entièrement gérés](android-fully-managed-enroll.md) dans Intune, vous pouvez les inscrire. La façon dont vous inscrivez vos appareils Android Entreprise varie en fonction du système d’exploitation.

| Méthode d’inscription | Version minimale du système d’exploitation Android pour les appareils dédiés et complètement managés |
| ----- | ----- |
| Communication en champ proche (NFC) | 5.1 |
| Entrée de jeton | 6.0 |
| Code QR | 7.0 |
| Zero Touch  | 8.0\* |

\* Sur les fabricants participants.

## <a name="enroll-by-using-near-field-communication-nfc"></a>Inscrire à l’aide de NFC

Pour les appareils prenant en charge NFC, vous pouvez provisionner vos appareils en créant une balise NFC spécialement mise en forme. Vous pouvez utiliser votre propre application ou n’importe quel outil de création de balise NFC. Pour plus d’informations, consultez [C-based Android Enterprise device enrollment with Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) et la [documentation Google sur les API de gestion Android](https://developers.google.com/android/management/provision-device#nfc_method).

## <a name="enroll-by-using-a-token"></a>Inscrire à l’aide d’un jeton

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

## <a name="enroll-by-using-a-qr-code"></a>Inscrire à l’aide d’un code QR

Sur les appareils Android 7 et ultérieur, vous pouvez scanner le code QR à partir du profil d’inscription pour inscrire l’appareil.

> [!Note]
> Le zoom du navigateur peut empêcher les appareils d’analyser le code QR. L’augmentation du zoom du navigateur résout le problème.

1. Pour lancer une lecture de code QR sur l’appareil Android, appuyez plusieurs fois sur le premier écran visible après une réinitialisation.
2. Pour les appareils Android 7 et 8, vous serez invité à installer un lecteur de code QR. Les appareils Android 9 et ultérieur ont déjà un lecteur de code QR installé.
3. Utilisez le lecteur de code QR pour scanner le code QR du profil d’inscription, puis suivez les invites à l’écran pour effectuer l’inscription.

## <a name="enroll-by-using-google-zero-touch"></a>S’inscrire à l’aide de Google Zero Touch

Pour utiliser le système Zero Touch de Google, l’appareil doit le prendre en charge et être affilié à un fournisseur qui fait partie du service.  Pour plus d’informations, consultez [le site web du programme Zero Touch de Google](https://www.android.com/enterprise/management/zero-touch/).

1. Créez une configuration dans la console Zero Touch.
2. Choisissez **Microsoft Intune** dans la liste déroulante EMM DPC.
3. Dans la console Zero Touch de Google, copiez/collez le code JSON suivant dans le champ de suppléments DPC. Remplacez la chaîne *YourEnrollmentToken* par le jeton d’inscription que vous avez créé dans le cadre de votre profil d’inscription. Veillez à entourer le jeton d’inscription dans des guillemets doubles.

    ```json
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


## <a name="next-steps"></a>Étapes suivantes
- [Déployer des applications Android](apps-deploy.md)
- [Ajouter des stratégies de configuration Android](device-profiles.md)

