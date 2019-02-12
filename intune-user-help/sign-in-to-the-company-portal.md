---
title: Guide pratique pour se connecter à l’application Portail d’entreprise | Microsoft Docs
description: Découvrez comment vous connecter à l’application Portail d’entreprise sur plusieurs plateformes.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 370d6372cf3df2ff807069fe8d54f30da23e7ba2
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842607"
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>Comment faire pour se connecter à l’application Portail d’entreprise ? <!--User Story 1132123-->

Vous utilisez l’application Portail d’entreprise pour accéder aux ressources de votre entreprise telles que l’e-mail et les applications métier. Il existe deux principales façons de se connecter au portail d’entreprise :

* Utilisation de votre adresse e-mail et mot de passe professionnels
* Connexion à partir d’un autre appareil

Bien que les images suivantes concernent iOS, le processus est quasiment identique pour vos appareils Android et Windows.

## <a name="signing-in-with-your-email-address-and-password"></a>Connexion avec votre e-mail et votre mot de passe

1. Ouvrez l’application Portail d’entreprise sur votre appareil et appuyez sur **Se connecter**.

   ![Page de connexion du Portail d’entreprise, contenant une icône de personne devant une représentation graphique d’un site web. Dessous se trouvent le texte « Obtenir l’accès aux ressources de l’entreprise et les sécuriser » et le bouton « Se connecter ». Un lien situé au bas de la page permet d’accéder aux informations Confidentialité et cookies de Microsoft.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   Vous n’avez pas l’application Portail d’entreprise ? Découvrez comment l’installer et la télécharger pour [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) ou [Android](install-the-company-portal-app-android.md).

2. Entrez votre **compte professionnel ou scolaire** et appuyez sur **Suivant**.

   ![L’utilisateur est invité à renseigner simplement son adresse e-mail, et non plus son adresse e-mail et son mot de passe sur le même écran.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Entrez votre mot de passe et appuyez sur **Connexion**.

   ![Une fois l’adresse e-mail validée, l’utilisateur est invité à saisir son mot de passe.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Après que le portail d’entreprise a accepté votre connexion, il vous connecte et vous permet d’accéder aux ressources de votre entreprise.   

   ![Une fois le processus d’authentification terminé, l’application Portail d’entreprise procède à la connexion et affiche une barre de chargement pour indiquer l’avancement du processus.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>Connexion avec authentification basée sur les certificats

1.  Ouvrez l'application Portail d'entreprise sur votre appareil.

2.  Entrez votre **Compte professionnel ou scolaire**.

3.  Appuyez sur le lien **Se connecter avec un certificat**.

4.  Appuyez sur **Continuer** pour utiliser le certificat.

## <a name="signing-in-from-another-device"></a>Connexion à partir d’un autre appareil

Si vous n’utilisez pas de mot de passe pour vous connecter aux ressources de votre entreprise, vous pouvez utiliser un autre appareil pour confirmer votre identité et vos niveaux d’accès adéquats. Si votre entreprise utilise des cartes à puce pour accéder à vos ordinateurs, vous devrez peut-être vous connecter à l’aide d’un autre appareil.

1. Au lieu d’entrer votre e-mail, sélectionnez le lien **Se connecter à partir d’un autre appareil** sous la zone de texte d’e-mail.

   ![La page de connexion du portail d’entreprise invite l’utilisateur à entrer son e-mail.  Dessous se trouvent le bouton « Suivant » et un lien vers « Se connecter à partir d’un autre appareil ». Il y a aussi un lien « Vous n’arrivez pas à accéder à votre compte ? » Un lien situé au bas de la page permet d’accéder aux informations Confidentialité et cookies de Microsoft.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Vous recevez un code à usage unique pour vous connecter au portail d’entreprise.

   ![Suivez les instructions fournies pour accéder à la page https://microsoft.com/devicelogin avec un code d’accès unique à partir de votre ordinateur, puis utilisez le code pour vous connecter.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. Sur votre autre appareil, ouvrez votre navigateur et accédez à [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin) pour entrer le code.

   ![Une image du navigateur de l’utilisateur sur son ordinateur de travail plutôt sur son application Portail d’entreprise. La page « Connexion à l’appareil » invite l’utilisateur à saisir le code qu’il a reçu dans l’application Portail d’entreprise.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Une fois que la page **Connexion à l’appareil** a vérifié le code, sélectionnez __Continuer__ pour autoriser le portail d’entreprise à se connecter sur votre autre appareil.

   ![L’utilisateur a saisi son code unique dans le champ, et le site « Connexion à l’appareil » lui a demandé de confirmer que le portail d’entreprise Intune était l’application appropriée pour recevoir l’autorisation de se connecter.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Une fois le code vérifié, vous pouvez fermer la fenêtre.

   ![Une page de confirmation indiquant que l’utilisateur est maintenant connecté à l’application Portail d’entreprise sur son appareil et qu’il peut fermer cette page.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. Sur votre appareil d’origine, l’application Portail d’entreprise commence l’ouverture de session.

   ![Une fois le processus d’authentification terminé, l’application Portail d’entreprise procède à la connexion et affiche une barre de chargement pour indiquer l’avancement du processus.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
