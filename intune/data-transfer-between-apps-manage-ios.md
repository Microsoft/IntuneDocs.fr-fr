---
title: Gérer le transfert de données entre applications iOS
titlesuffix: Microsoft Intune
description: Découvrez comment utiliser des stratégies de gestion des applications mobiles dans Microsoft Intune pour gérer les transferts de données entre les applications.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d5a2bc0939da5ee4cb35585a930f145b832a58ad
ms.sourcegitcommit: 0dbce0415e53fe963dc7f927ac4b0c06411f199c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281103"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Comment gérer les transferts de données entre applications iOS dans Microsoft Intune

Pour protéger les données de l’entreprise, limitez les transferts de fichiers aux applications que vous gérez uniquement. Vous pouvez gérer les applications iOS comme suit :

-   Empêchez la perte de données d’entreprise en configurant une stratégie de protection des applications pour les applications, appelées applications **gérées par une stratégie**. Consultez [toutes les applications gérées par Intune que vous pouvez gérer avec la stratégie de protection des applications](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Déployez et gérez des applications via le **canal MDM**, ce qui demande d’inscrire les appareils dans une solution de gestion des appareils mobiles (MDM). Les applications que vous déployez peuvent être **gérées par une stratégie** ou d’autres applications gérées.

La fonctionnalité **Open-in management** pour les appareils iOS peut limiter les transferts de fichiers entre des applications déployées sur le **canal MDM**. Définissez des restrictions *Open-in management* dans les paramètres de configuration et déployez-les avec votre solution MDM.  Quand l’utilisateur installe l’application déployée, les restrictions que vous avez définies sont appliquées.

##  <a name="use-app-protection-with-ios-apps"></a>Utiliser la protection des applications avec des applications iOS
Utilisez des stratégies de protection des applications avec la fonctionnalité **Open in management** d’iOS pour protéger les données d’entreprise des façons suivantes :

-   **Appareils appartenant à l’entreprise non gérés par une solution MDM :** vous pouvez définir les paramètres de la stratégie de protection des applications pour **autoriser l’application à transférer des données uniquement vers des applications gérées par une stratégie**. Le comportement *Open-In* dans une application gérée par stratégie présente uniquement d’autres applications gérées par stratégie en tant qu’options de partage. Si un utilisateur tente d’envoyer un fichier protégé par stratégie en tant que pièce jointe depuis OneDrive vers l’application de messagerie native, ce fichier est illisible.

-   **Appareils gérés par Intune :** pour les appareils inscrits dans Intune, le transfert de données entre les applications avec les stratégies de protection des applications et les autres applications iOS gérées qui sont déployées par le biais de Microsoft Intune est automatiquement autorisé. Pour spécifier la façon dont vous souhaitez autoriser le transfert de données sur d’autres applications, activez **Autoriser l’application à transférer des données vers d’autres applications** et choisissez le niveau de partage de votre choix. Pour spécifier la façon dont vous souhaitez autoriser une application à recevoir des données d’autres applications, activez **Autoriser l’application à recevoir des données d’autres applications** et choisissez le niveau de réception de données votre choix. Vous pouvez utiliser la fonctionnalité **Open-in management** pour contrôler le transfert de données entre les applications qui sont déployées via Intune. Pour plus d’informations sur la réception et le partage des données d’application, consultez [Paramètres de réadressage des données](app-protection-policy-settings-ios.md#data-relocation-settings).   

-   **Appareils gérés par une solution MDM tierce** : vous pouvez limiter le transfert de données uniquement à des applications gérées en utilisant la fonctionnalité iOS **Open-in management**.
Pour vous assurer que les applications que vous déployez à l’aide d’une solution MDM tierce sont également associées à vos stratégies de protection des applications Intune, configurez le paramètre UPN d’utilisateur comme décrit dans la section suivante [Configurer le paramètre UPN d’utilisateur](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Quand les applications sont déployées avec le paramètre UPN de l’utilisateur, les stratégies de protection des applications sont implémentées dans l’application quand l’utilisateur se connecte avec son compte professionnel.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurer le paramètre UPN d’utilisateur pour Microsoft Intune ou une solution de gestion de la mobilité d’entreprise tierce
Le paramètre UPN d’utilisateur **doit être configuré** pour les appareils gérés par Intune ou par une solution de gestion de la mobilité d’entreprise tierce. La configuration de l’UPN fonctionne avec les stratégies de protection des applications que vous déployez depuis Intune. La procédure suivante est un flux général indiquant comment configurer le paramètre UPN et l’expérience utilisateur qui en résulte :

1.  Dans le [portail Azure](https://portal.azure.com), [créez et attribuez une stratégie de protection des applications](app-protection-policies.md) pour iOS. Configurez les paramètres de stratégie selon les besoins de votre entreprise et sélectionnez les applications iOS qui doivent disposer de cette stratégie.

2.  Déployez les applications et le profil de messagerie que vous souhaitez gérer par le biais d’Intune ou de votre solution MDM tierce en suivant les étapes généralisées suivantes. Cette expérience est également abordée dans l’*Exemple 1*.

3.  Déployez l’application avec les paramètres de configuration d’application suivants :

      **key** = IntuneMAMUPN,  **value** = <username@company.com>

      Exemple : [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Déployez la stratégie **Open in management** en utilisant Intune ou votre fournisseur MDM tiers sur les appareils inscrits.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemple 1 : Expérience de l’administrateur dans Intune ou dans la console MDM tierce

1. Accédez à la console d’administration Intune ou à votre fournisseur MDM tiers. Accédez à la section de la console dans laquelle vous déployez les paramètres de configuration d’application sur les appareils iOS inscrits.

2. Dans la section Configuration de l’application, entrez le paramètre suivant :

   **key** = IntuneMAMUPN,  **value** = <username@company.com>

   La syntaxe exacte de la paire clé/valeur peut varier en fonction du fournisseur de gestion des appareils mobiles tiers. Le tableau suivant présente des exemples de fournisseurs de gestion des appareils mobiles tiers et les valeurs exactes à entrer dans la paire clé/valeur.

   |Fournisseur de gestion des appareils mobiles tiers| Clé Configuration | Type de valeur | Valeur Configuration|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Chaîne | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Chaîne | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Chaîne | ${userUPN} **ou** ${userEmailAddress} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Chaîne | %upn% |


### <a name="example-2-end-user-experience"></a>Exemple 2 : Expérience de l’utilisateur final

1.  L’utilisateur installe l’application Microsoft Word sur un appareil.

2.  L’utilisateur lance l’application de messagerie native gérée pour accéder à son e-mail.

3.  L’utilisateur tente d’ouvrir un document de la messagerie native dans Microsoft Word.

4.  Quand l’application Word démarre, l’utilisateur est invité à se connecter avec son compte professionnel. Ce compte que l’utilisateur entre doit correspondre à celui que vous avez spécifié dans les paramètres de configuration de l’application pour Microsoft Word.

    > [!NOTE]
    > L’utilisateur peut ajouter et utiliser ses comptes personnels avec Word. Les stratégies de protection des applications ne s’appliquent pas quand l’utilisateur se sert de Word en dehors d’un contexte professionnel. 

5.  Après la connexion, les paramètres de stratégie de protection des applications sont implémentés dans l’application Word.

6.  Le transfert de données se déroule maintenant avec succès et le document est marqué avec l’identité de l’entreprise dans l’application.  Les données sont traitées dans un contexte professionnel et les paramètres de stratégie s’appliquent. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Valider le paramètre UPN d’utilisateur pour une solution de gestion de la mobilité d’entreprise tierce

Après avoir configuré le paramètre UPN d’utilisateur, vérifiez que l’application iOS peut recevoir la stratégie de protection des applications Intune et s’y conformer.

Par exemple, le paramètre de stratégie **Exiger le code confidentiel de l’application** est facile à tester. Quand le paramètre de stratégie a la valeur **Oui**, l’utilisateur doit voir une invite pour définir ou entrer un code PIN avant de pouvoir accéder aux données de l’entreprise.

Tout d’abord, [créez et attribuez une stratégie de protection des applications](app-protection-policies.md) à l’application iOS. Pour plus d’informations sur la façon de tester la stratégie de protection des applications, consultez [Valider les stratégies de protection des applications](app-protection-policies-validate.md).


### <a name="see-also"></a>Voir aussi
[Qu’est ce qu’une stratégie de protection d’application Intune ?](app-protection-policy.md)
