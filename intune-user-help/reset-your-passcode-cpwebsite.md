---
title: Guide pratique pour réinitialiser votre code secret à partir du site web du Portail d’entreprise | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5e973e18a79c18af6b201194fc1a6534da5fa38a
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "55838034"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Guide pratique pour réinitialiser le code secret de votre appareil à partir du site web du portail d’entreprise

Si vous perdez le code PIN ou le mot de passe de votre appareil, vous pouvez utiliser le [site web du portail d’entreprise](https://portal.manage.microsoft.com) pour le réinitialiser.  

Si vous utilisez un appareil d’entreprise, vous ne verrez peut-être pas l’option permettant de réinitialiser votre code secret. Contactez le support de votre entreprise pour réinitialiser le code secret.

   > [!NOTE]
   > Vous ne pouvez pas réinitialiser le code secret pour les appareils Android 7.0 et versions ultérieures. Si vous oubliez un code secret, vous devez réinitialiser l’appareil aux paramètres d’usine. 

## <a name="reset-your-passcode"></a>Réinitialiser votre code d’accès

1.  Accédez au [site web du portail d’entreprise](https://portal.manage.microsoft.com), puis sélectionnez le bouton __Menu__ > __Appareils__.  

2. Sélectionnez l’appareil dont le code secret doit être réinitialisé.  

    ![Capture d’écran de la page Appareils, avec 2 vignettes montrant des appareils non identifiés, portant un nom générique. Sous les appareils, une bannière grise invite l’utilisateur à identifier l’appareil qu’il utilise ou à en ajouter un nouveau.](./media/rename-reset-device-step2-1808.png) 

3. Sélectionnez **Réinitialiser le code secret**. Si cette option n’est pas visible en haut de la page, sélectionnez **Plus (...)** > **Réinitialiser le code secret**.   

   ![Page de détails de l’appareil pour un appareil sélectionné sur le site web du portail d’entreprise, avec une liste de liens en haut montrant Renommer, Supprimer, Réinitialiser l’appareil, Réinitialiser le code secret et Verrouillage à distance. ](./media/rename-reset-device-1808.png)   

    ![Zoom avant sur l’icône Plus, mise en surbrillance avec une flèche rouge.](./media/rename-reset-device-step3-more-1808.png)  

4. À l’invite, cliquez sur **Se déconnecter**. À la nouvelle invite, reconnectez-vous. Vous devez vous reconnecter au site web du portail d’entreprise dans les cinq minutes, sinon le portail d’entreprise ne réinitialise pas le code secret de l’appareil.  

   > [!NOTE]
   > Vous devez vous reconnecter afin de confirmer votre identité. Cette mesure vite à éviter toute tentative malveillante de réinitialisation de votre code d’accès.

   ![Captures d’écran montrant une invite à vous déconnecter du portail d’entreprise. Les boutons disponibles pour l’utilisateur sont Se déconnecter et Annuler.](./media/iwp-reset-passcode-popup-1808.png)

5. Un message s’affiche pour vous avertir que le code secret existant de l’appareil est sur le point d’être supprimé. Cliquez sur **Réinitialiser le code secret** pour confirmer.  
    > [!WARNING]
    > Une fois le code secret réinitialisé, toute personne ayant un accès physique à l’appareil pourra accéder à la plupart des informations personnelles et d’entreprise qui y sont stockées. Si l’appareil n’est pas en votre possession actuellement, ne réinitialisez pas le code secret.  

   ![Capture d’écran montrant le deuxième message de réinitialisation de code secret. Inclut un lien pour en savoir plus sur la définition d’un nouveau code secret dans la documentation, ainsi que des boutons permettant de réinitialiser le code secret et d’annuler l’opération.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Si vous réinitialisez le code secret d’un appareil iOS, son code secret existant sera supprimé. Pour les appareils Android ou Windows, un code secret temporaire vous sera délivré afin de déverrouiller l’appareil et de définir un nouveau code secret. 

   > [!NOTE]
   > Vous trouverez le code secret temporaire pour les appareils Windows et Android dans le portail d’entreprise, dans la page de détails de l’appareil. Pour obtenir des descriptions des codes secrets propres aux systèmes d’exploitation, consultez la section [Configurer un nouveau code secret](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode).  
   
7. Sur votre appareil, accédez à **Paramètres** et changez le code secret temporaire. 

8. Un indicateur s’affiche dans le coin supérieur droit du site web du portail d’entreprise. Cliquez dessus pour lire la notification et confirmer que le code secret a bien été réinitialisé.  

## <a name="set-up-a-new-passcode"></a>Configurer un nouveau code secret  

Cette section décrit le comportement relatif à la réinitialisation du code secret et à la création de code secret temporaire pour chaque plateforme d’appareil.  

**Android** : supprime le code secret existant et crée un code secret temporaire composé de lettres et de chiffres.

**iOS** : supprime le code secret existant et ne crée pas de code secret temporaire. Si vous utilisez le scanneur d’empreinte digitale Touch ID pour ouvrir votre appareil ou effectuer des achats, vous devez le reconfigurer.  

**Windows 10 Mobile** : supprime le code secret existant et crée un code secret temporaire composé de lettres et de chiffres. Si la reconnaissance faciale Windows Hello est configurée, elle continuera à fonctionner avec l’appareil.
    
**Windows Phone 8.1** : supprime le code secret existant et crée un code secret temporaire composé de chiffres.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
