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
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e21fa0285c769f98eada3fd4cb31f3fe82fb8bb9
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "55841811"
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>Un certificat qui est généralement installé sur votre téléphone est absent de votre appareil Android.

Si votre appareil n’est pas inscrit dans Intune et qu’il manque un certificat qui devrait être installé sur votre téléphone, vous ne pouvez pas vous connecter à l’application Portail d’entreprise. Quand vous essayez de vous connecter, le message suivant s’affiche :

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Vous pouvez résoudre ce problème en obtenant le certificat exigé depuis la [page relative au certificat Digicert](https://www.digicert.com/digicert-root-certificates.htm).

1. Recherchez et téléchargez le certificat __Baltimore CyberTrust Root__. Vous pouvez également le télécharger directement [ici](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

2. Faites glisser à partir du haut de l’écran pour afficher la liste de vos notifications récentes, puis appuyez sur **BaltimoreCyberTrustRoot.crt**.

3. Votre appareil vous demandera de donner un **nom au certificat**. Ne modifiez pas le nom de certificat par défaut qui s’affiche.

4. Vérifiez que **Credential Use** (Utilisation des informations d’identification) a la valeur **Used for VPN and apps** (Utilisé pour le VPN et les applications), puis appuyez sur **OK**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. Fermez votre navigateur et l’application Portail d’entreprise.

6. Rouvrez l’application Portail d’entreprise. Vous devriez pouvoir vous connecter à l’application Portail d’entreprise. Si vous ne pouvez toujours pas utiliser l’application Portail d’entreprise, contactez le support technique de votre entreprise à l’aide des informations fournies sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour obtenir des instructions.

>[!NOTE]
> Si l’installation de ce certificat ne résout pas le problème, et que vous voyez un message différent indiquant un certificat manquant, vous devez prendre des mesures supplémentaires pour [installer le certificat manquant](your-device-is-missing-an-IT-required-certificate-android.md).

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
