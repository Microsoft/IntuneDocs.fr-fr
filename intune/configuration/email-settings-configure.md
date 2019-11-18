---
title: Configurer les paramètres e-mail dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Créez un profil de messagerie dans Microsoft Intune et déployez-le sur des appareils Android Entreprise, iOS et Windows. Utilisez un profil de messagerie pour configurer les paramètres e-mail courants, notamment un serveur de messagerie et une méthode d’authentification pour permettre la connexion à l’e-mail d’entreprise sur les appareils que vous gérez.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75644ac4d8ccfb8a63e077f2b6625ac96364f5d7
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755194"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Ajouter des paramètres e-mail à des appareils à l’aide d’Intune

Microsoft Intune inclut différents paramètres e-mail que vous pouvez déployer sur des appareils dans votre organisation. Un administrateur informatique crée des profils de messagerie avec des paramètres spécifiques pour permettre la connexion à un serveur de messagerie, comme Office 365 et Gmail. Les utilisateurs finaux peuvent alors, sur leurs appareils mobiles, se connecter à leurs comptes e-mail professionnels, s’authentifier auprès de ces derniers et les synchroniser. En créant et en déployant un profil de messagerie, vous pouvez standardiser les paramètres sur de nombreux appareils. En outre, vous contribuez à réduire les appels au support technique des utilisateurs finaux qui ignorent les paramètres e-mail corrects.

Vous pouvez utiliser des profils de messagerie afin de configurer les paramètres e-mail intégrés pour les appareils suivants :

- Android Samsung Knox Standard 4.0 et versions ultérieures
- Android Entreprise
- iOS 8.0 et versions ultérieures
- Windows Phone 8.1 et versions ultérieures
- Windows 10 Desktop et Windows 10 Mobile

Cet article vous montre comment créer un profil de messagerie dans Microsoft Intune. Il inclut également des liens vers les différentes plateformes, pour lesquelles existent des paramètres plus spécifiques.

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Attribuez un nom descriptif à la stratégie. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, un bon nom de stratégie est **Paramètres de messagerie pour tous les appareils Windows**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :

        - **Android** (Samsung Android Knox Standard uniquement)
        - **Android Entreprise**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 et versions ultérieures**

    - **Type de profil** : Sélectionner un **e-mail**.

4. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Choisissez votre plateforme pour connaître les paramètres détaillés :

    - [Paramètres Android Samsung Knox Standard](../email-settings-android.md)
    - [Paramètres Android Entreprise](../email-settings-android-enterprise.md)
    - [Paramètres iOS/iPadOS](email-settings-ios.md)
    - [Paramètres Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Paramètres Windows 10](email-settings-windows-10.md)

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Une fois que vous avez entré les paramètres et créé le profil, ce dernier apparaît dans la liste des profils. Ensuite, [affectez ce profil à certains groupes](../device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Supprimer un profil de messagerie

Les profils d’e-mail sont affectés à des groupes d’appareils, et non à des groupes d’utilisateurs. Il existe différentes façons de supprimer un profil d’e-mail d’un appareil, même si celui-ci ne contient qu’un seul profil d’e-mail :

- **Option 1** : Ouvrez le profil de messagerie (**Appareils** > **Profils de configuration** > sélectionnez votre profil), puis choisissez **Affectations**. L’onglet **Inclure** affiche les groupes auxquels le profil a été affecté. Cliquez avec le bouton droit sur le groupe, puis choisissez **Supprimer**. Veillez à **Enregistrer** vos modifications.

- **Option 2** : [Réinitialisez l’appareil ou mettez-le hors service](../remote-actions/devices-wipe.md). Vous pouvez utiliser ces actions pour supprimer des données et des paramètres en totalité ou de manière sélective.

## <a name="secure-email-access"></a>Sécuriser l’accès à l’e-mail

Vous pouvez aider à sécuriser les profils de messagerie à l’aide des options suivantes :

- **Certificats** : Quand vous créez le profil de messagerie, vous choisissez un profil de certificat créé dans Intune. Ce certificat est connu comme étant le certificat d’identité. Il s’authentifie auprès d’un profil de certificat approuvé ou d’un certificat racine pour confirmer que l’utilisateur est autorisé à se connecter. Le certificat approuvé est affecté à l’ordinateur qui authentifie la connexion e-mail. En règle générale, cet ordinateur est le serveur de messagerie natif.

  Pour plus d’informations sur la création et l’utilisation des profils de certificat dans Intune, consultez [Guide pratique pour configurer des certificats avec Intune](../protect/certificates-configure.md).

- **Nom d'utilisateur et mot de passe** : L’utilisateur final s’authentifie auprès du serveur de messagerie natif en entrant un nom d’utilisateur et un mot de passe. Le mot de passe n’existe pas dans le profil de messagerie. Ainsi, l’utilisateur final entre le mot de passe quand il se connecte à l’e-mail.

## <a name="how-intune-handles-existing-email-accounts"></a>Comment Intune gère les comptes de messagerie existants

Si l’utilisateur a déjà configuré un compte e-mail, le profil de messagerie est attribué différemment, selon la plateforme.

- **iOS** : Un profil de messagerie en double existant est détecté en fonction du nom d’hôte et de l’adresse e-mail. Le profil de messagerie en doublon bloque l’affectation d’un profil Intune. Dans ce cas, l’application Portail d’entreprise signale à l’utilisateur final qu’il n’est pas conforme et l’invite à supprimer manuellement le profil configuré. Pour éviter ce scénario, demandez à vos utilisateurs finaux de s’inscrire *avant* d’installer un profil de messagerie, ce qui permet à Intune de configurer le profil.

- **Windows :** Un profil de messagerie en double existant est détecté en fonction du nom d’hôte et de l’adresse e-mail. Intune remplace le profil de messagerie existant créé par l’utilisateur final.

- **Android Samsung Knox Standard** : Un profil de messagerie en double existant est détecté en fonction de l’adresse e-mail et le remplace par le profil Intune. Android n’utilise pas le nom d’hôte pour identifier le profil. Ne créez pas plusieurs profils de messagerie à l’aide de la même adresse e-mail sur des hôtes différents. Les profils se remplacent les uns les autres.

- **Profils professionnels Android** : Intune fournit deux profils de messagerie professionnels Android, un pour l’application Gmail, l’autre pour l’application Nine Work. Ces applications sont disponibles dans le Google Play Store et s’installent dans le profil professionnel de l’appareil. Ces applications ne créent pas de profils en double. Ces deux applications prennent en charge les connexions à Exchange. Pour utiliser la connectivité e-mail, déployez une de ces applications e-mail sur les appareils de vos utilisateurs. Ensuite, créez et déployez le profil de messagerie approprié. Les applications e-mail telles que Nine Work peuvent ne pas être gratuites. Vérifiez les détails de licence de l’application ou contactez le fabricant de l’application si vous avez des questions.

## <a name="changes-to-assigned-email-profiles"></a>Modifications apportées aux profils de messagerie attribués

Si vous apportez des modifications à un profil de messagerie que vous avez attribué, les utilisateurs finaux peuvent voir un message leur demandant d’approuver la reconfiguration de leurs paramètres e-mail.

## <a name="next-steps"></a>Étapes suivantes

Une fois le profil créé, il ne fait rien pour le moment. À présent, [affectez le profil](../device-profile-assign.md).
