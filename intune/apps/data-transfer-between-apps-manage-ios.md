---
title: Gérer le transfert de données entre applications iOS
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser des stratégies de gestion des applications mobiles dans Microsoft Intune pour gérer les transferts de données entre les applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db583b1fc89edf72f329a605cc86363593eaaa9d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497920"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Comment gérer les transferts de données entre applications iOS dans Microsoft Intune

Pour protéger les données de l’entreprise, limitez les transferts de fichiers aux applications que vous gérez uniquement. Vous pouvez gérer les applications iOS comme suit :

- Protégez les données d’organisation pour les comptes professionnels ou scolaires en configurant une stratégie de protection pour les applications, que nous appelons *applications gérées par stratégie*.  Consultez [toutes les applications gérées par Intune que vous pouvez gérer avec la stratégie de protection des applications](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Déployez et gérez les applications via la gestion des appareils iOS, ce qui nécessite d’inscrire les appareils dans une solution de gestion des appareils mobiles (MDM). Les applications que vous déployez peuvent être des applications *gérées par stratégie* ou d’autres applications iOS gérées.

La fonctionnalité **gestion Open-in** des appareils iOS inscrits peut limiter les transferts de fichiers entre des applications iOS gérées. Définissez des restrictions de *gestion Open-in* dans les paramètres de configuration, puis déployez-les avec votre solution MDM.  Quand l’utilisateur installe l’application déployée, les restrictions que vous avez définies sont appliquées.

## <a name="use-app-protection-with-ios-apps"></a>Utiliser la protection des applications avec des applications iOS
Utilisez des stratégies de protection des applications avec la fonctionnalité de **gestion Open-in** d’iOS pour protéger les données d’entreprise des façons suivantes :

- **Appareils non gérés par une solution MDM :** Vous pouvez définir les paramètres de la stratégie de protection des applications pour contrôler le partage des données avec d’autres applications via *Open-in* ou *Extensions de partage*.  Pour ce faire, configurez le paramètre **Envoyer des données de l’organisation à une autre application** sur la valeur **Applications gérées par stratégie avec filtrage Open-In/Partage**.  Le comportement *Open-In/Partage* dans l’*application gérée par stratégie* présente uniquement d’autres *applications gérées par stratégie* en tant qu’options de partage. 

- **Appareils managés par des solutions de gestion des données de référence** : Pour des appareils inscrits dans Intune ou des solutions de gestion des données de référence tierces, le partage des données entre les applications avec les stratégies de protection des applications et d’autres applications iOS managées déployées via la gestion des données de référence est contrôlé par les stratégies d’application Intune et la fonctionnalité iOS **Ouvrir dans la gestion**. Pour vous assurer que les applications que vous déployez à l’aide d’une solution de gestion des données de référence sont également associées à vos stratégies de protection des applications Intune, configurez le paramètre UPN d’utilisateur comme décrit dans la section suivante [Configurer le paramètre UPN d’utilisateur](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Pour spécifier la façon dont vous souhaitez autoriser le transfert de données sur d’autres applications, activez **Envoyer des données d’organisation vers d’autres applications** et choisissez le niveau de partage de votre choix. Pour spécifier la façon dont vous souhaitez autoriser une application à recevoir des données d’autres applications, activez **Recevoir des données d’autres applications** et choisissez le niveau de réception de données de votre choix. Pour plus d’informations sur la réception et le partage des données d’application, consultez [Paramètres de réadressage des données](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurer le paramètre UPN d’utilisateur pour Microsoft Intune ou une solution de gestion de la mobilité d’entreprise tierce
Le paramètre UPN d’utilisateur est **requis** pour les appareils gérés par Intune ou par une solution de gestion de la mobilité d’entreprise tierce pour identifier le compte d'utilisateur inscrit. La configuration de l’UPN fonctionne avec les stratégies de protection des applications que vous déployez depuis Intune. La procédure suivante est un flux général indiquant comment configurer le paramètre UPN et l’expérience utilisateur qui en résulte :

1. Dans le [portail Azure](https://portal.azure.com), [créez et attribuez une stratégie de protection des applications](app-protection-policies.md) pour iOS. Configurez les paramètres de stratégie selon les besoins de votre entreprise et sélectionnez les applications iOS qui doivent disposer de cette stratégie.

2. Déployez les applications et le profil de messagerie que vous souhaitez gérer par le biais d’Intune ou de votre solution MDM tierce en suivant les étapes généralisées suivantes. Cette expérience est également abordée dans l’*Exemple 1*.

3. Déployez l’application avec les paramètres de configuration d’application suivants sur l’appareil géré :

      **clé** = IntuneMAMUPN, **valeur** = <username@company.com>

      Exemple : [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > Dans Intune, le type d’inscription App Configuration doit être défini sur **Appareils gérés**.
     > En outre, l’application doit être soit installée à partir du portail d’entreprise Intune (si elle est définie sur disponible) ou envoyée (push) en fonction des besoins à l’appareil. 

4. Déployez la stratégie **Open in management** en utilisant Intune ou votre fournisseur MDM tiers sur les appareils inscrits.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemple 1 : Expérience de l’administrateur dans Intune ou dans la console MDM tierce

1. Accédez à la console d’administration Intune ou à votre fournisseur MDM tiers. Accédez à la section de la console dans laquelle vous déployez les paramètres de configuration d’application sur les appareils iOS inscrits.

2. Dans la section Configuration de l’application, entrez le paramètre suivant :

   **clé** = IntuneMAMUPN, **valeur** = <username@company.com>

   La syntaxe exacte de la paire clé/valeur peut varier en fonction du fournisseur de gestion des appareils mobiles tiers. Le tableau suivant présente des exemples de fournisseurs de gestion des appareils mobiles tiers et les valeurs exactes à entrer dans la paire clé/valeur.

   |Fournisseur de gestion des appareils mobiles tiers| Clé Configuration | Type de valeur | Valeur Configuration|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Chaîne | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Chaîne | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Chaîne | ${userUPN} **ou** ${userEmailAddress} |
   |Gestion de point de terminaison Citrix | IntuneMAMUPN | Chaîne | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Chaîne | %upn% |

> [!NOTE]  
> Pour l’application Outlook dans iOS si vous déployez une stratégie App Configuration avec l’option « Utilisation du concepteur de configuration » la clé de configuration IntuneMAMUPN est configurée automatiquement dans les coulisses de la stratégie. Pour plus d’informations, consultez la section FAQ dans [Nouvelle expérience Outlook pour iOS et de stratégie App Configuration Android – App Configuration générale](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481). 


### <a name="example-2-end-user-experience"></a>Exemple 2 : Expérience de l’utilisateur final

*Partage à partir d’une* application gérée par stratégie *vers d’autres applications avec partage du système d’exploitation*

1. Un utilisateur ouvre l’application Microsoft OneDrive sur un appareil iOS inscrit et se connecte à son compte professionnel.  Le compte entré par l’utilisateur doit correspondre au compte UPN que vous avez spécifié dans les paramètres de configuration de l’application pour l’application Microsoft OneDrive.

2. Après la connexion, vos paramètres d’application configurés par l’administrateur s’appliquent au compte d’utilisateur dans Microsoft OneDrive.  Ceci inclut la configuration du paramètre **Envoyer des données de l’organisation à d’autres applications** sur la valeur **Applications gérées par stratégie avec partage du système d’exploitation**.

3. L’utilisateur affiche un aperçu d’un fichier de travail et tente de partager via Open-in vers une application gérée iOS.  

4. Le transfert de données réussit et les données sont désormais protégées par la **gestion Open-in** dans l’application gérée iOS.  L’application Intune ne s’applique pas aux applications qui ne sont pas *des applications gérées par stratégie*.

Le *partage à partir d’une* application gérée iOS *vers une* application gérée par stratégie *avec des données d’organisation entrantes*

1. Un utilisateur ouvre un courrier natif sur un appareil iOS inscrit avec un profil de messagerie géré.  

1. L’utilisateur ouvre une pièce jointe de document de travail à partir de la messagerie native dans Microsoft Word.

1. Lors du lancement de l’application Word, l’une des deux expériences suivantes se produit :
   1. Les données sont protégées par l’application Intune dans les cas suivants :
      - L’utilisateur est connecté à son compte professionnel, qui correspond au compte UPN que vous avez spécifié dans les paramètres de configuration de l’application pour Microsoft Word. 
      - Vos paramètres d’application configurés par l’administrateur s’appliquent au compte d’utilisateur dans Microsoft Word.  Ceci inclut la configuration du paramètre **Recevoir des données d’autres applications** sur la valeur **Toutes les applications avec des données d’organisation entrantes**.
      - Le transfert de données se déroule avec succès et le document est marqué avec l’identité professionnelle dans l’application.  L’application Intune protège les actions de l’utilisateur pour le document.
   1. Les données ne sont **pas** protégées par l’application Intune dans les cas suivants :
      - L’utilisateur n’est **pas** connecté à son compte professionnel.
      - Vos paramètres configurés par l’administrateur ne sont **pas** appliqués à Microsoft Word, car l’utilisateur n’est pas connecté.
      - Le transfert de données se déroule avec succès et le document n’est **pas** marqué avec l’identité professionnelle dans l’application.  L’application Intune ne protège **pas** les actions de l’utilisateur pour le document, car elle n’est pas active.

    > [!NOTE]
    > L’utilisateur peut ajouter et utiliser ses comptes personnels avec Word. Les stratégies de protection des applications ne s’appliquent pas quand l’utilisateur se sert de Word en dehors d’un contexte professionnel. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Valider le paramètre UPN d’utilisateur pour une solution de gestion de la mobilité d’entreprise tierce

Après avoir configuré le paramètre UPN d’utilisateur, vérifiez que l’application iOS peut recevoir la stratégie de protection des applications Intune et s’y conformer.

Par exemple, le paramètre de stratégie **Exiger le code confidentiel de l’application** est facile à tester. Quand le paramètre de stratégie a la valeur **Requérir**, l’utilisateur doit voir une invite pour définir ou entrer un code PIN avant de pouvoir accéder aux données de l’entreprise.

Tout d’abord, [créez et attribuez une stratégie de protection des applications](app-protection-policies.md) à l’application iOS. Pour plus d’informations sur la façon de tester la stratégie de protection des applications, consultez [Valider les stratégies de protection des applications](app-protection-policies-validate.md).


## <a name="see-also"></a>Voir aussi
[Qu’est ce qu’une stratégie de protection d’application Intune ?](app-protection-policy.md)
