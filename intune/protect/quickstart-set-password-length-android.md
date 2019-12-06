---
title: 'Démarrage rapide : stratégie de conformité des mots de passe pour les appareils Android'
titleSuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour définir une longueur de mot de passe minimale pour les appareils Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409775"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>Démarrage rapide : Créer une stratégie de conformité des mots de passe pour les appareils Android

Dans ce démarrage rapide, vous allez utiliser Microsoft Intune pour exiger de votre personnel utilisant Android qu’il entre un mot de passe d’une longueur spécifique avant de pouvoir accéder aux informations sur ses appareils Android.

Une stratégie de conformité des appareils Intune spécifie les règles et les paramètres que ces appareils doivent respecter pour être considérés conformes. Vous pouvez utiliser ces stratégies de conformité avec un accès conditionnel pour autoriser ou bloquer l’accès aux ressources de l’entreprise. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité.

> [!IMPORTANT]
> En plus des paramètres de mot de passe, vous devez également prendre en compte d'autres paramètres de sécurité système pour protéger votre personnel. Pour plus d'informations, consultez [Paramètres de sécurité système](compliance-policy-create-android-for-work.md).

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) comme [Administrateur général](../fundamentals/users-add.md#types-of-administrators) ou [Administrateur de service Intune](../fundamentals/users-add.md#types-of-administrators).

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils

Créez une stratégie de conformité des appareils pour demander aux utilisateurs Android de votre effectif d’entrer un mot de passe d’une longueur donnée afin de pouvoir accéder aux informations stockées sur leurs appareils Android.

1. Dans Intune, sélectionnez **Appareils** > **Stratégies de conformité** > **Créer une stratégie**.

2. Ajoutez **Conformité Android** comme **Nom**. Ajoutez également une **Description**.

3. Pour **Plateforme**, sélectionnez **Android Entreprise**.

4. Pour **Type de profil**, sélectionnez **Profil professionnel**.

5. Sélectionnez **Paramètres** > **Sécurité système** pour afficher le panneau Android **Sécurité système**.

6. Pour **Exiger un mot de passe pour déverrouiller des appareils mobiles**, sélectionnez **Exiger**.

7. Pour le **Type de mot de passe requis**, sélectionnez **Au moins numérique**.

8. Pour **Longueur minimale du mot de passe**, entrez **6**.

    ![Capture d’écran de création d’un groupe dans Microsoft Intune](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. Quand vous avez terminé, sélectionnez **OK** > **OK** > **Créer** pour créer la stratégie.

Une fois que la stratégie a été créée, elle apparaît dans votre liste de stratégies de conformité des appareils.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Quand la stratégie n’est plus nécessaire, supprimez-la. Pour ce faire, sélectionnez la stratégie de conformité et cliquez sur **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Pour ce démarrage rapide, vous avez utilisé Intune pour créer une stratégie de conformité pour les appareils Android de votre personnel afin d’exiger un mot de passe d’au moins six caractères. Pour en savoir plus sur la création de stratégies de conformité, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](device-compliance-get-started.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Envoyer des notifications aux appareils non conformes](../quickstart-send-notification.md)
