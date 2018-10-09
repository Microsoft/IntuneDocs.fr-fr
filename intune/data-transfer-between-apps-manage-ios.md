---
title: Gérer le transfert de données entre applications iOS
titlesuffix: Microsoft Intune
description: Découvrez comment utiliser des stratégies de gestion des applications mobiles dans Microsoft Intune pour gérer les transferts de données entre les applications.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 23e18ef2d7870a22699d898ad937febf9e61b804
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231650"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Comment gérer les transferts de données entre applications iOS dans Microsoft Intune
## <a name="manage-ios-apps"></a>Gérer les applications iOS
La protection des données de votre entreprise nécessite notamment de vérifier que les transferts de fichiers sont limités aux applications que vous gérez.  Vous pouvez gérer les applications iOS comme suit :

-   Empêchez la perte de données d’entreprise en configurant une stratégie de protection des applications pour les applications. Ces dernières sont appelées des applications **gérées par une stratégie**. Consultez [toutes les applications gérées par Intune que vous pouvez gérer avec la stratégie de protection des applications](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Vous pouvez également déployer et gérer des applications via le **canal MDM**.  Ceci nécessite que les appareils soient inscrits dans la solution MDM. Il peut s’agir d’applications **gérées par une stratégie** ou d’autres applications gérées.

La fonctionnalité **Ouvrir dans la gestion** pour les appareils iOS peut limiter les transferts de fichiers entre des applications déployées sur le **canal MDM**. Les restrictions de gestion de l’ouverture sont définies dans les paramètres de configuration et déployées à l’aide de votre solution de gestion des appareils mobiles (MDM).  Quand l’utilisateur installe l’application déployée, les restrictions que vous avez définies sont appliquées.

##  <a name="using-app-protection-with-ios-apps"></a>Utilisation de la protection des applications avec des applications iOS
Vous pouvez utiliser les stratégies de protection des applications avec la fonctionnalité **Open in management** d’iOS pour protéger les données d’entreprise des façons suivantes :

-   **Appareils appartenant à l’entreprise non gérés par une solution MDM :** vous pouvez définir les paramètres de la stratégie de protection des applications pour **autoriser l’application à transférer des données uniquement vers des applications gérées par une stratégie**. Le comportement Open In dans une application gérée par stratégie présente uniquement d’autres applications gérées par stratégie en tant qu’options de partage. Si un utilisateur tente d’envoyer un fichier protégé par stratégie en tant que pièce jointe de OneDrive vers la messagerie native, ce fichier sera illisible.

-   **Appareils gérés par Intune :** pour les appareils inscrits dans Intune, le transfert de données entre les applications avec les stratégies de protection des applications et les autres applications iOS gérées déployées par le biais d'Intune est autorisé automatiquement. Pour permettre le transfert de données entre les applications avec les stratégies protection des applications, activez le paramètre **Autoriser l’application à transférer des données uniquement vers des applications gérées**. Vous pouvez utiliser la fonctionnalité **Ouvrir dans la gestion** pour contrôler le transfert de données entre les applications qui sont déployées via Intune.   

-   **Appareils gérés par une solution MDM tierce** : vous pouvez limiter le transfert de données uniquement à des applications gérées en utilisant la fonctionnalité **Ouvrir d’iOS dans la gestion**.
Pour vous assurer que les applications que vous déployez à l’aide de votre solution MDM tierce sont également associées aux stratégies de protection des applications que vous avez configurées dans Intune, vous devez configurer le paramètre de nom UPN d’utilisateur comme décrit dans la procédure [Configurer le paramètre UPN d’utilisateur](#configure-user-upn-setting-for-third-party-emm).  Quand les applications sont déployées avec le paramètre UPN de l’utilisateur, les stratégies de protection des applications sont appliquées à l’application quand l’utilisateur final se connecte en utilisant son compte professionnel.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurer le paramètre UPN d’utilisateur pour Microsoft Intune ou une solution de gestion de la mobilité d’entreprise tierce
Le paramètre UPN d’utilisateur **doit être configuré** pour les appareils gérés par Intune ou par une solution de gestion de la mobilité d’entreprise tierce. La procédure décrite ci-dessous est un flux général indiquant comment configurer le paramètre UPN et l’expérience résultante pour l’utilisateur final :

1.  Dans le [portail Azure](https://portal.azure.com), [créez et attribuez une stratégie de protection des applications](app-protection-policies.md) pour iOS. Configurez les paramètres de stratégie selon les besoins de votre entreprise et sélectionnez les applications iOS qui doivent disposer de cette stratégie.

2.  Déployez les applications et le profil de messagerie que vous souhaitez gérer par le biais d’Intune ou de votre solution MDM tierce en suivant les étapes généralisées ci-dessous. Cette expérience est également abordée dans l’Exemple 1.

3.  Déployez l’application avec les paramètres de configuration d’application suivants :

      **key** = IntuneMAMUPN,  **value** = <username@company.com>

      Exemple : [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Déployez la stratégie **Open in management** en utilisant Intune ou votre fournisseur MDM tiers sur les appareils inscrits.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemple 1 : Expérience de l’administrateur dans Intune ou dans la console MDM tierce

1. Accédez à la console d’administration Intune ou à votre fournisseur MDM tiers. Accédez à la section de la console dans laquelle vous déployez les paramètres de configuration d’application sur les appareils iOS inscrits.

2. Dans la section Configuration de l’application, entrez le paramètre suivant :

   **key** = IntuneMAMUPN,  **value** = <username@company.com>

   La syntaxe exacte de la paire clé/valeur peut varier en fonction du fournisseur de gestion des appareils mobiles tiers. Le tableau ci-dessous présente des exemples de fournisseurs de gestion des appareils mobiles tiers et les valeurs exactes à entrer dans la paire clé/valeur.

|Fournisseur de gestion des appareils mobiles tiers| Clé Configuration | Type de valeur | Valeur Configuration|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | Chaîne | {{UserPrincipalName}}|
|VMware AirWatch| IntuneMAMUPN | Chaîne | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | Chaîne | ${userUPN} **ou** ${userEmailAddress} |
|ManageEngine Mobile Device Manager | IntuneMAMUPN | Chaîne | %upn% |


### <a name="example-2-end-user-experience"></a>Exemple 2 : Expérience de l’utilisateur final

1.  L’utilisateur installe l’application Microsoft Word sur l’appareil.

2.  L’utilisateur final lance l’application de messagerie native gérée pour accéder à sa messagerie.

3.  L’utilisateur final tente d’ouvrir un document provenant de la messagerie native dans Microsoft Word.

4.  Quand l’application Word démarre, l’utilisateur final est invité à se connecter en utilisant son compte professionnel.  Ce compte de travail que l’utilisateur final saisit lors de l’invite doit correspondre à celui que vous avez spécifié dans les paramètres de configuration de l’application pour Microsoft Word.

    > [!NOTE]
    > L’utilisateur final peut ajouter d’autres comptes personnels dans Word pour effectuer son travail personnel sans être affecté par les stratégies de protection des applications lors de l’utilisation de l’application Word dans un contexte personnel.

5.  Quand la connexion est établie, les paramètres de la stratégie de protection des applications sont appliqués à l’application Word.

6.  Le transfert de données se déroule maintenant avec succès et le document est marqué avec l’identité de l’entreprise dans l’application. En outre, les données sont traitées dans un contexte de travail et les paramètres de stratégie sont donc appliqués.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Valider le paramètre UPN d’utilisateur pour une solution de gestion de la mobilité d’entreprise tierce

Après avoir configuré le paramètre UPN d’utilisateur, vous devez vérifier que l’application iOS peut recevoir la stratégie de protection des applications Intune et s’y conformer.

Par exemple, le paramètre de stratégie **Exiger le code confidentiel de l’application** est facile à tester visuellement sur un appareil. Si le paramètre de stratégie a la valeur **Oui**, l’utilisateur final est invité à définir ou à entrer un code confidentiel quand il tente d’accéder aux données de l’entreprise.

Tout d’abord, [créez et attribuez une stratégie de protection des applications](app-protection-policies.md) à l’application iOS. Pour plus d’informations sur la façon de tester la stratégie de protection des applications, consultez [Valider les stratégies de protection des applications](app-protection-policies-validate.md).


### <a name="see-also"></a>Voir aussi
[Qu’est ce qu’une stratégie de protection d’application Intune ?](app-protection-policy.md)
