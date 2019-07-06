---
title: Il manque un certificat à votre appareil | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bdf97e6a36a49bc6df5a182af7676c357440f3e
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529331"
---
# <a name="your-android-device-is-missing-a-certificate-required-by-your-company-support"></a>Un certificat exigé par le support technique de votre entreprise est manquant sur votre appareil Android

Si votre appareil n’est pas inscrit dans Intune et qu’il manque un certificat exigé par le support technique de votre entreprise, vous ne pouvez pas vous connecter à l’application Portail d’entreprise. Quand vous essayez de vous connecter, le message suivant s’affiche :

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Pour résoudre ce problème et obtenir le certificat nécessaire, vous devez suivre deux étapes :

- Identifier le certificat manquant en le recherchant sur votre ordinateur professionnel ou scolaire.
- Utiliser votre appareil pour télécharger le certificat manquant à partir d’Internet.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Identifier le certificat manquant en le recherchant sur votre ordinateur professionnel ou scolaire

1. Ouvrez Internet Explorer sur votre PC. Si vous n’avez pas de PC utilisable pour cette action, contactez le support technique de votre entreprise. Pour obtenir les coordonnées du support technique de votre entreprise, consultez le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Accédez au site web [Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980), puis connectez-vous à l’aide de vos informations d’identification professionnelles ou scolaires.

3. À l’extrême droite de la barre d’adresse du navigateur, choisissez le symbole qui ressemble à un verrou, comme illustré dans la capture d’écran suivante.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Si vous ne voyez pas le symbole de verrou, arrêtez et contactez le support technique de votre entreprise. Le verrou signifie que vous êtes connecté en toute sécurité, donc ne continuez pas tant que vous ne voyez pas ce symbole.

4. Choisissez **Afficher les certificats**.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Dans la boîte de dialogue **Certificat**, choisissez l’onglet **Chemin d’accès de certification**, puis identifiez le certificat que vous devez obtenir à partir d’Internet. Le nom de ce certificat est affiché au même endroit que celui mis en surbrillance dans la capture d’écran précédente.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Télécharger et installer le certificat manquant sur votre appareil mobile Android

1. À l’aide d’un moteur de recherche tel que Bing ou Google, recherchez le nom du certificat manquant que vous avez identifié dans la section précédente. Le nom du certificat peut se terminer par différentes extensions, telles que « .crt » ou « .pem », etc.

2. Téléchargez le certificat racine à partir du site web.

3. Une fois le certificat téléchargé, faites défiler l’écran de votre appareil de bas en haut pour accéder à vos notifications, puis cliquez sur le nom du certificat dans la liste des notifications.

4. Dans la boîte de dialogue **Name the certificate** (Nommer le certificat) illustrée dans la capture d’écran suivante, acceptez le nom du certificat par défaut.

5. Vérifiez que **Credential Use** (Utilisation des informations d’identification) a la valeur **Used for VPN and apps** (Utilisé pour le VPN et les applications), puis appuyez sur **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Fermez l’application Portail d’entreprise.

7. Rouvrez l’application Portail d’entreprise. Vous devriez pouvoir vous connecter à l’application Portail d’entreprise. Si vous avez besoin d’aide, contactez le support technique de votre entreprise.

Si un message « Certificat manquant » semblable à celui indiqué précédemment s’affiche alors que vous avez déjà suivi la procédure, il manque probablement un autre certificat. Vous devez demander au support technique de votre entreprise de vous aider à l’installer. Contactez le support technique de votre entreprise pour obtenir de l’aide sur les informations de contact disponibles sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
