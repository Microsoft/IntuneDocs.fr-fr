---
title: Obtenir une clé de récupération pour un appareil macOS à partir du site Web Portail d’entreprise Intune
description: Affichez la clé de récupération d’un appareil macOS géré et géré.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 1e7831712b4c07d015aa0f587ff6ba6183940897
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855234"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>Obtenir une clé de récupération pour un appareil macOS

Utilisez le site Web Portail d’entreprise pour obtenir une clé de récupération pour votre appareil macOS verrouillé. Si vous oubliez le mot de passe de votre appareil, vous pouvez vous connecter au Portail d’entreprise à partir d’un autre appareil pour récupérer votre clé.  

## <a name="get-recovery-key-from-company-portal-website"></a>Récupérer la clé de récupération à partir du site Web Portail d’entreprise

Cette option est disponible pour les appareils qui ont été chiffrés par votre organisation à l’aide de FileVault. Elle n’est pas disponible pour les appareils que vous avez chiffrés personnellement.

1. Sur n’importe quel appareil, connectez-vous au [site web portail d’entreprise](https://portal.manage.microsoft.com) et sélectionnez le bouton de **menu** > **appareils**.  
2. Sélectionnez l’appareil macOS chiffré.  
3. Sélectionnez **Obtenir la clé de récupération**.  

    ![Capture d’écran de Portail d’entreprise site Web, en mettant en surbrillance la section récupérer la clé de récupération.](./media/1907-recovery2-cpweb-intune.PNG)  

4. Votre clé de récupération s’affiche.

    ![Capture d’écran de Portail d’entreprise site Web, avec la clé de récupération.](./media/1907-recovery-cpweb-intune.PNG)  

    Pour des raisons de sécurité, la clé disparaîtra au bout de cinq minutes. Pour afficher à nouveau la clé, sélectionnez **obtenir une clé de récupération**.

Si une clé est introuvable mais que votre appareil est correctement chiffré, contactez la personne chargée du support technique de votre organisation. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>Obtenir la clé de récupération à partir de Portail d’entreprise application pour iOS

Vous pouvez récupérer votre clé de récupération personnelle (clé FileVault) à l’aide de l’application Portail d’entreprise pour iOS. Votre appareil avec la clé de récupération personnelle doit être inscrit auprès d’Intune et chiffré avec FileVault via Intune. Cette option n’est pas disponible pour les appareils que vous avez chiffrés personnellement. 

À l’aide de l’application Portail d’entreprise, vous pouvez ouvrir l’affichage Web de Safari et récupérer votre clé de récupération personnelle. 

1. Ouvrez le Portail d’entreprise.
2. Cliquez sur **récupérer la clé de récupération**.

    ![Capture d’écran de l’application Portail d’entreprise pour iOS, avec la clé de récupération](./media/get-recovery-key-cpweb-02.png)  

Le site Web Portail d’entreprise s’ouvre dans l’affichage Web de Safari et affiche la clé. 

## <a name="it-pro-support"></a>Support technique pour les professionnels de l’informatique

Si vous êtes une personne du support informatique et que vous souhaitez configurer et gérer le chiffrement FileVault pour les appareils macOS, consultez [utiliser le chiffrement de l’appareil avec Intune](/intune/protect/encrypt-devices).

## <a name="next-steps"></a>Étapes suivantes

Découvrez ce que vous pouvez faire d’autre à partir du site Web Portail d’entreprise. Consultez [utilisation du site web portail d’entreprise Intune](using-the-intune-company-portal-website.md) pour obtenir la liste des actions.  

Encore besoin d’aide ? Contactez votre responsable de support informatique. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
