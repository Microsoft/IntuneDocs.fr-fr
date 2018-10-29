---
title: Démarrage rapide –Ddéfinir une longueur de mot de passe requise pour les appareils Android
titlesuffix: Microsoft Intune
description: Dans ce démarrage rapide vous allez utiliser Microsoft Intune pour définir une longueur de mot de passe requise pour les appareils Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395282"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>Démarrage rapide : définir une longueur de mot de passe requise pour les appareils Android

Dans ce démarrage rapide, vous allez utiliser Microsoft Intune pour exiger de votre personnel utilisant Android qu’il entre un mot de passe d’une longueur spécifique avant de pouvoir accéder aux informations sur ses appareils Android. 

> [!IMPORTANT]
> En plus des paramètres de mot de passe, vous devez également prendre en compte d'autres paramètres de sécurité système pour protéger votre personnel. Pour plus d'informations, consultez [Paramètres de sécurité système](compliance-policy-create-android-for-work.md#system-security-settings).

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune. Pour accéder à Intune dans le Portail Azure, choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils
1. Une fois que vous avez ouvert le panneau **Microsoft Intune**, sélectionnez **Conformité des appareils** > **Stratégies** > **Créer une stratégie**.
2. Ajoutez **Conformité Android** comme **Nom**. Ajoutez également une **Description**.
3. Pour l’option **Plateforme**, sélectionnez **Android**. 
4. Sélectionnez **Paramètres** > **Sécurité système** pour afficher le panneau Android **Sécurité système**.
5. Dans la section **Mot de passe**, en regard d’**Exiger un mot de passe pour déverrouiller des appareils mobiles**, cliquez sur **Requérir**.
6. En regard de **Longueur minimale du mot de passe**, entrez **6**.  

    ![Capture d’écran de création d’un groupe dans Microsoft Intune](./media/quickstart-set-password-length-android-01.png)

7. Lorsque vous avez terminé, cliquez sur **OK** pour fermer le panneau **Sécurité système**. 
8. Cliquez sur **OK** pour fermer le panneau **Stratégie de conformité Android**. 
9. Cliquez sur **Créer** pour créer la stratégie.

Lorsque vous avez réussi à créer la stratégie, elle apparaît dans la liste **Conformité des appareils : stratégies**. 

## <a name="next-steps"></a>Étapes suivantes

Pour ce démarrage rapide, vous avez utilisé Intune pour créer une stratégie de conformité pour les appareils Android de votre personnel afin d’exiger un mot de passe d’au moins six caractères.

> [!div class="nextstepaction"]
> [Configurer l’inscription automatique](quickstart-setup-auto-enrollment.md)
