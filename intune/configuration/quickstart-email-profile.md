---
title: 'Démarrage rapide : Créer un profil d’appareil de messagerie pour les appareils iOS/iPadOS'
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser Microsoft Intune pour créer un profil d’appareil de messagerie afin que les appareils iOS/iPadOS puissent se connecter de façon sécurisée à la messagerie d’entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af2576c44e0486dbd859a56896db3b7d0ffc6cff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511066"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>Démarrage rapide : Créer un profil d’appareil de messagerie pour iOS/iPadOS

Dans ce guide de démarrage rapide, vous verrez comment créer un profil d’appareil de messagerie pour les appareils iOS/iPadOS. Ce profil spécifie les paramètres dont a besoin l’application de messagerie intégrée sur l’appareil iOS/iPadOS pour se connecter à la messagerie d’entreprise. Les profils d’appareil e-mail aident à standardiser les paramètres parmi les appareils et permettent aux utilisateurs finaux d’accéder à l’e-mail d’entreprise sur leurs appareils personnels sans aucune autre configuration de leur part. Pour protéger davantage votre e-mail, vous pouvez utiliser un profil e-mail pour déterminer si les appareils sont conformes, puis configurer l’accès conditionnel pour n’autoriser que les appareils conformes à accéder à l’e-mail. Pour plus d’informations sur les profils e-mail, consultez [Guide pratique pour configurer des paramètres de messagerie dans Microsoft Intune](email-settings-configure.md).

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) comme Administrateur général ou Administrateur de service Intune. Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="create-an-iosipados-email-profile"></a>Créer un profil de messagerie iOS/iPadOS

1. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

   ![Créer un profil de messagerie pour iOS/iPadOS dans Intune](./media/quickstart-email-profile/ios-create-profile.png)

2. Sous **Nom**, attribuez un nom descriptif au nouveau profil. Pour cet exemple, entrez **iOS require work email** (iOS : adresse e-mail professionnelle requise).
3. Entrez les informations de profil suivantes :
    - Pour **Description**, entrez **Require iOS/iPadOS devices to use work email** (Exiger que les appareils iOS/iPadOS utilisent l’adresse e-mail professionnelle).
    - Pour l’option **Plateforme**, sélectionnez **iOS/iPadOS**.
    - Pour **Type de profil**, sélectionnez **E-mail**.

        ![Créer un profil de messagerie destiné à être utilisé avec des appareils iOS/iPadOS dans Intune](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Sélectionnez **Paramètres**, puis entrez les paramètres suivants (laissez les valeurs par défaut pour les autres paramètres) :
   - **Serveur de messagerie** : pour ce guide de démarrage rapide, entrez **outlook.office365.com**. Ce paramètre spécifie l’emplacement Exchange (URL) du serveur de messagerie que l’application de messagerie iOS/iPadOS utilisera pour se connecter à la messagerie.
   - **Nom du compte** : entrez **E-mail de l’entreprise**.
   - **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (Azure AD). Intune génère dynamiquement le nom d’utilisateur pour ce profil en utilisant ce nom. Pour ce guide de démarrage rapide, nous supposons que le **Nom d’utilisateur principal** doit être utilisé comme nom d’utilisateur pour le profil (par exemple, user1@contoso.com).
   - **Attribut d’adresse e-mail d’AAD** : ce paramètre est l’adresse e-mail issue d’Azure AD qui est utilisée pour la connexion à Exchange. Pour ce guide de démarrage rapide, sélectionnez **Nom d’utilisateur principal**.
   - **Méthode d’authentification** : pour ce guide de démarrage rapide, sélectionnez **Nom d’utilisateur et mot de passe**. (Vous pouvez également choisir **Certificat** si vous avez déjà configuré un certificat pour Intune.)

        ![Créer un profil de messagerie pour une utilisation avec iOS/iPadOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Sélectionnez **OK** > **Créer**. Le nouveau profil apparaît dans la liste des profils avec le tableau de bord affiché pour vous permettre de superviser l’affectation du profil aux appareils iOS/iPadOS et aux utilisateurs iOS/iPadOS.
6. Sélectionnez **Affectations**.
7. Sélectionnez l’onglet **Inclure**, puis sélectionnez **Tous les utilisateurs et tous les appareils**. 
8. Sélectionnez **Enregistrer**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’envisagez pas d’utiliser le profil que vous avez créé pour d’autres tutoriels ou tests, vous pouvez le supprimer maintenant.

1. Dans Intune, sélectionnez **Configuration de l’appareil**, puis **Profils**.
2. Sélectionnez le profil de test que vous avez créé, **iOS/iPadOS require work email** (iOS/iPadOS : adresse e-mail professionnelle requise).
3. Sélectionnez les points de suspension (**...**) en regard du profil, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un profil de messagerie pour les appareils iOS/iPadOS. Vous pouvez maintenant utiliser ce profil pour déterminer si un appareil iOS/iPadOS est conforme en créant une stratégie de conformité qui marque comme non conforme tout appareil iOS/iPadOS qui ne correspond pas au profil. Pour une protection accrue, vous pouvez créer une stratégie d’accès conditionnel qui empêche les appareils iOS/iPadOS non conformes d’accéder à la messagerie. Pour en savoir plus sur les stratégies de conformité des appareils, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutoriel : Protéger la messagerie Exchange Online sur les appareils gérés](../tutorial-protect-email-on-enrolled-devices.md)
