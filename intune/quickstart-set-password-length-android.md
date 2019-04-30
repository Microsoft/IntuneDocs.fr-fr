---
title: 'Démarrage rapide : stratégie de conformité des mots de passe pour les appareils Android'
titleSuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour définir une longueur de mot de passe minimale pour les appareils Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e71a9a69cfc474f311bc6acd9e8f24c776a44476
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512775"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Démarrage rapide : Créer une stratégie de conformité des mots de passe pour les appareils Android

Dans ce démarrage rapide, vous allez utiliser Microsoft Intune pour exiger de votre personnel utilisant Android qu’il entre un mot de passe d’une longueur spécifique avant de pouvoir accéder aux informations sur ses appareils Android. 

Une stratégie de conformité des appareils Intune spécifie les règles et les paramètres que ces appareils doivent respecter pour être considérés conformes. Vous pouvez utiliser ces stratégies de conformité avec un accès conditionnel pour autoriser ou bloquer l’accès aux ressources de l’entreprise. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité.

> [!IMPORTANT]
> En plus des paramètres de mot de passe, vous devez également prendre en compte d'autres paramètres de sécurité système pour protéger votre personnel. Pour plus d'informations, consultez [Paramètres de sécurité système](compliance-policy-create-android-for-work.md).

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune. 

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils

Dans ce guide de démarrage rapide, vous allez utiliser Intune pour demander aux utilisateurs d’appareils Android de votre organisation d’entrer un mot de passe d’une longueur donnée afin de pouvoir accéder aux informations stockées sur leurs appareils Android.

1. Dans Intune, sélectionnez **Conformité des appareils** > **Stratégies** > **Créer une stratégie**.
2. Ajoutez **Conformité Android** comme **Nom**. Ajoutez également une **Description**.
3. Pour l’option **Plateforme**, sélectionnez **Android**. 
4. Sélectionnez **Paramètres** > **Sécurité système** pour afficher le panneau Android **Sécurité système**.
5. Cliquez sur **Exiger** à côté de **Exiger un mot de passe pour déverrouiller des appareils mobiles**.
6. Sélectionnez **Au moins numérique** en regard de **Type de mot de passe requis**.
7. Entrez **6** à côté de **Longueur minimale du mot de passe**. 

    ![Capture d’écran de création d’un groupe dans Microsoft Intune](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. Quand vous avez terminé, cliquez sur **OK** > **OK** > **Créer** pour créer la stratégie.

Une fois que la stratégie a été créée, elle apparaît dans votre liste de stratégies de conformité des appareils. 

## <a name="clean-up-resources"></a>Nettoyer les ressources

Quand la stratégie n’est plus nécessaire, supprimez-la. Pour ce faire, sélectionnez la stratégie de conformité et cliquez sur **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Pour ce démarrage rapide, vous avez utilisé Intune pour créer une stratégie de conformité pour les appareils Android de votre personnel afin d’exiger un mot de passe d’au moins six caractères. Pour en savoir plus sur la création de stratégies de conformité, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](device-compliance-get-started.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Envoyer des notifications aux appareils non conformes](quickstart-send-notification.md)
