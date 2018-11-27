---
title: Démarrage rapide - Inscrire un appareil Windows 10 Desktop dans Microsoft Intune
description: Démarrage rapide - Utilisez le portail d’entreprise pour inscrire votre appareil Windows 10 Desktop dans Microsoft Intune.
services: microsoft-intune
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 13ffb9e7091b484c59f44802de675b1ab45b1c77
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183466"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>Démarrage rapide : Inscrire un appareil Windows 10

Dans ce guide de démarrage rapide, vous jouez d’abord le rôle d’un utilisateur Intune et inscrivez votre appareil Windows 10 dans Microsoft Intune. Vous revenez ensuite à Intune et confirmez l’appareil inscrit.

L’inscription de vos appareils à Microsoft Intune permet à vos appareils Windows 10 d’avoir accès aux données sécurisées de votre organisation, comme les e-mails, les fichiers et d’autres ressources. Sont à la fois concernés les appareils Windows 10 Desktop et Windows 10 Mobile. L’inscription de vos appareils permet de sécuriser cet accès pour vous et votre organisation. Elle vous permet de séparer vos données professionnelles de vos données personnelles.

> [!TIP]
> Découvrez ce qui se passe quand vous [inscrivez votre appareil dans Intune](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md) et ce que cela signifie pour les [informations contenues dans votre appareil](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Abonnement Microsoft Intune ([inscrivez-vous pour créer un compte d’essai gratuit](free-trial-sign-up.md)).
- Pour suivre ce guide de démarrage rapide, vous devez [configurer l’inscription automatique dans Intune](quickstart-setup-auto-enrollment.md).

## <a name="confirm-your-windows-10-desktop-version"></a>Confirmer votre version de Windows 10 Desktop

Avant d’inscrire votre appareil Windows 10 Desktop, vous devez confirmer la version de Windows que vous avez installée.

1. Cliquez avec le bouton droit sur l’icône **Démarrer** de Windows, puis sélectionnez **Paramètres** pour afficher les options des paramètres Windows.

   ![Capture d’écran de Paramètres Windows - Système](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. Sélectionnez **Système** > **À propos de**. 

   ![Capture d’écran des paramètres système](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > Vous pouvez également taper « à propos de votre PC » dans la **barre de recherche**, puis sélectionner **À propos de votre PC**.

3. Dans la fenêtre **Paramètres**, la liste **Spécifications de Windows** s’affiche pour votre PC. Dans cette liste, repérez la **Version**.

4. Vérifiez que la **Version** de Windows 10 indique **1607 ou ultérieure**.

    > [!IMPORTANT]
    > Les étapes présentées dans ce guide de démarrage rapide s’appliquent à Windows 10 version **1607 ou ultérieure**. Si vous utilisez la version **1511 ou antérieure**, effectuez [ces étapes](/intune-user-help/enroll-your-w10-device-your-account.md).

## <a name="enroll-windows-10-desktop"></a>Inscrire Windows 10 Desktop

1. Revenez à Paramètres Windows, puis sélectionnez **Comptes**.

   ![Capture d’écran des paramètres système - Comptes](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. Sélectionnez **Accès Professionnel ou Scolaire** > **Se connecter**.

    ![Sélectionner le compte Accès Professionnel ou Scolaire](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. Connectez-vous à Intune avec votre compte professionnel ou scolaire, puis sélectionnez **Suivant**. Si vous avez suivi le guide de démarrage rapide Créer un utilisateur et affecter une licence, connectez-vous avec le compte d’utilisateur que vous avez créé.

    > [!NOTE]
    > Si vous configurez un compte « .onmicrosoft.com », l’adresse du compte d’utilisateur contient **.onmicrosoft.com**. 

   ![Entrer un compte professionnel ou scolaire](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    Vous verrez un message indiquant que votre société ou votre école procède à l’inscription de votre appareil.

4. Lorsque l’écran **Vous voilà prêt !** s’affiche, sélectionnez **Terminé**. Vous avez terminé.

5. Le compte ajouté fait désormais partie des paramètres **Accès Professionnel ou Scolaire** de votre poste de travail Windows.

   ![Capture d’écran du compte nouvellement ajouté](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    Si vous avez suivi les étapes précédentes, mais que vous ne pouvez toujours pas accéder à votre compte e-mail ou vos fichiers professionnels ou scolaires, consultez les [Étapes de dépannage à suivre si vous voyez Accès scolaire ou professionnel](/intune-user-help/troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

## <a name="confirm-your-device-enrollment-in-intune"></a>Confirmer l’inscription de votre appareil dans Intune

1. Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune.
2. Sélectionnez **Appareils** pour afficher les appareils inscrits dans Intune.
3. Vérifiez qu’un appareil supplémentaire est bien inscrit dans Intune.

   ![Capture d’écran des appareils inscrits à Intune](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour désinscrire votre appareil Windows, consultez [Supprimer votre appareil Windows de la gestion](/intune-user-help/unenroll-your-device-from-intune-windows.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à inscrire un appareil Windows 10 à Intune. Vous pouvez découvrir d’autres moyens d’inscrire des appareils sur toutes les plateformes. Pour plus d’informations sur l’utilisation d’appareils avec Intune, consultez [Utiliser des appareils gérés pour réaliser vos tâches](/intune-user-help/use-managed-devices-to-get-work-done.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : définir une longueur de mot de passe requise pour les appareils Android](quickstart-set-password-length-android.md)