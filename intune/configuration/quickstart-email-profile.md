---
title: 'Démarrage rapide : Créer un profil d’appareil e-mail pour iOS'
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser Microsoft Intune pour créer un profil d’appareil e-mail afin que les appareils iOS puissent se connecter de manière sécurisée à l’e-mail d’entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
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
ms.openlocfilehash: 2b2f1372a6d7ced09a9ebdfc11cbad69501827bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059325"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Démarrage rapide : Créer un profil d’appareil de messagerie pour iOS

Dans ce guide de démarrage rapide, vous verrez comment créer un profil d’appareil e-mail pour les appareils iOS. Ce profil spécifie les paramètres dont a besoin l’application e-mail intégrée sur l’appareil iOS pour se connecter à l’e-mail d’entreprise. Les profils d’appareil e-mail aident à standardiser les paramètres parmi les appareils et permettent aux utilisateurs finaux d’accéder à l’e-mail d’entreprise sur leurs appareils personnels sans aucune autre configuration de leur part. Pour protéger davantage votre e-mail, vous pouvez utiliser un profil e-mail pour déterminer si les appareils sont conformes, puis configurer l’accès conditionnel pour n’autoriser que les appareils conformes à accéder à l’e-mail. Pour plus d’informations sur les profils e-mail, consultez [Guide pratique pour configurer des paramètres de messagerie dans Microsoft Intune](email-settings-configure.md).

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) comme Administrateur général ou Administrateur de service Intune. Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="create-an-ios-email-profile"></a>Créer un profil e-mail iOS

1. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

   ![Créer un profil e-mail pour iOS](./media/quickstart-email-profile/ios-create-profile.png)

2. Sous **Nom**, attribuez un nom descriptif au nouveau profil. Pour cet exemple, entrez **iOS require work email** (iOS : adresse e-mail professionnelle requise).
3. Entrez les informations de profil suivantes :
    - Pour **Description**, entrez **Require iOS devices to use work email** (Exiger que les appareils iOS utilisent l’adresse e-mail professionnelle).
    - Pour l’option **Plateforme**, sélectionnez **iOS**.
    - Pour **Type de profil**, sélectionnez **E-mail**.

        ![Créer un profil de messagerie pour iOS](./media/quickstart-email-profile/ios-email-profile-name.png)

4. Sélectionnez **Paramètres**, puis entrez les paramètres suivants (laissez les valeurs par défaut pour les autres paramètres) :
   - **Serveur de messagerie** : pour ce guide de démarrage rapide, entrez **outlook.office365.com**. Ce paramètre spécifie l’emplacement Exchange (URL) du serveur e-mail que l’application e-mail iOS utilisera pour se connecter à l’e-mail.
   - **Nom du compte** : entrez **E-mail de l’entreprise**.
   - **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (Azure AD). Intune génère dynamiquement le nom d’utilisateur pour ce profil en utilisant ce nom. Pour ce guide de démarrage rapide, nous supposons que le **Nom d’utilisateur principal** doit être utilisé comme nom d’utilisateur pour le profil (par exemple, user1@contoso.com).
   - **Attribut d’adresse e-mail d’AAD** : ce paramètre est l’adresse e-mail issue d’Azure AD qui est utilisée pour la connexion à Exchange. Pour ce guide de démarrage rapide, sélectionnez **Nom d’utilisateur principal**.
   - **Méthode d’authentification** : pour ce guide de démarrage rapide, sélectionnez **Nom d’utilisateur et mot de passe**. (Vous pouvez également choisir **Certificat** si vous avez déjà configuré un certificat pour Intune.)

        ![Créer un profil de messagerie pour iOS](./media/quickstart-email-profile/ios-email-profile.png)

5. Sélectionnez **OK** > **Créer**. Le nouveau profil apparaît dans la liste des profils, et le tableau de bord affiché afin que vous puissiez superviser l’affectation du profil aux appareils iOS et aux utilisateurs d’iOS.
6. Sélectionnez **Affectations**.
7. Sélectionnez l’onglet **Inclure**, puis sélectionnez **Tous les utilisateurs et tous les appareils**. 
8. Sélectionnez **Enregistrer**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous n’envisagez pas d’utiliser le profil que vous avez créé pour d’autres tutoriels ou tests, vous pouvez le supprimer maintenant.

1. Dans Intune, sélectionnez **Configuration de l’appareil**, puis **Profils**.
2. Sélectionnez le profil de test que vous avez créé, **iOS require work email** (iOS : adresse e-mail professionnelle requise).
3. Sélectionnez les points de suspension ( **...** ) en regard du profil, puis sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un profil e-mail pour les appareils iOS. Maintenant, vous pouvez utiliser ce profil pour déterminer si un appareil iOS est conforme en créant une stratégie de conformité qui marque comme non conforme tout appareil iOS qui ne correspond pas au profil. Pour une protection accrue, vous pouvez créer une stratégie d’accès conditionnel qui empêche les appareils iOS non conformes d’accéder à l’e-mail. Pour en savoir plus sur les stratégies de conformité des appareils, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Tutoriel : Protéger la messagerie Exchange Online sur les appareils gérés](../tutorial-protect-email-on-enrolled-devices.md)
