---
title: Stratégies de configuration des applications pour Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser des stratégies de configuration des applications sur un appareil iOS ou Android dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 42d17c15a2a32f828c5715dfad51f34c5e531e76
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72507551"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Stratégies de configuration des applications pour Microsoft Intune

Les stratégies de configuration des applications peuvent vous aider à éliminer les problèmes d’installation des applications en vous permettant d’affecter des paramètres de configuration à une stratégie, à son tour attribuée aux utilisateurs finaux avant qu’ils n’exécutent l’application. Les paramètres sont ensuite fournis automatiquement quand l’application est configurée sur l’appareil des utilisateurs finaux, lesquels n’ont aucune action à effectuer. Les paramètres de configuration sont uniques pour chaque application. 

Vous pouvez créer et utiliser des stratégies de configuration des applications afin de fournir des paramètres de configuration pour des applications iOS ou Android. Ces paramètres de configuration permettent de personnaliser une application en utilisant la gestion et la configuration des applications. Les paramètres de stratégie de configuration sont utilisés quand l’application les recherche, en général à la première exécution. 

Un paramètre de configuration d’application, par exemple, peut vous obliger à spécifier les détails suivants :

- Un numéro de port personnalisé
- Paramètres de langue
- Paramètres de sécurité
- Paramètres de personnalisation comme le logo de l’entreprise

Si les utilisateurs finaux doivent entrer ces paramètres à la place, ils risquent de le faire de manière incorrecte. Les stratégies de configuration des applications peuvent vous aider à assurer la cohérence au sein d’une entreprise et à réduire les appels au support technique des utilisateurs finaux qui essaient de configurer eux-mêmes les paramètres. L’utilisation de stratégies de configuration des applications peut permettre d’adopter plus facilement et plus rapidement de nouvelles applications.

Les paramètres de configuration disponibles sont en fin de compte déterminés par les développeurs de l’application. Consultez la documentation du fournisseur de l’application pour savoir si cette application prend en charge les configurations et quelles sont celles qui sont disponibles. Pour certaines applications, Intune renseigne les paramètres de configuration disponibles. 

> [!NOTE]
> Dans le Google Play Store géré, les applications qui prennent en charge les configurations sont identifiées :
> 
> ![Capture d’écran d’une application configurée](./media/app-configuration-policies-overview/configured-app.png)
>
> Quand vous choisissez Appareils gérés comme type d’inscription pour les appareils Android, vous voyez uniquement les applications du [Google Play Store géré](https://play.google.com/work) et pas celle du [Google Play Store](https://play.google.com/store/apps). Le Google Play Store géré, aussi appelé Android for Work (AfW), et Android Enterprise sont les applications du profil professionnel qui contiennent les versions d’application qui prennent en charge la configuration des applications.

Vous pouvez attribuer une stratégie de configuration des applications à un groupe d’utilisateurs finaux et d’appareils à l’aide d’une combinaison d’[attributions d’inclusion et d’exclusion](apps-inc-exl-assignments.md). Dès que vous ajoutez une stratégie de configuration d’application, vous pouvez définir les affectations de la stratégie de configuration d’application. Quand vous définissez les attributions de la stratégie, vous pouvez choisir d’inclure et d’exclure les [groupes](../fundamentals/groups-add.md) d’utilisateurs finaux auxquels la stratégie s’applique. Quand vous choisissez d’inclure un ou plusieurs groupes, vous pouvez choisir de sélectionner des groupes spécifiques à inclure ou sélectionner des groupes intégrés. Les groupes intégrés sont notamment **Tous les utilisateurs**, **Tous les appareils** et **Tous les utilisateurs + Tous les appareils**.

Vous avez deux options pour utiliser les stratégies de configuration des applications avec Intune :
- **Appareils gérés** : l’appareil est géré par Intune en tant que fournisseur de gestion des appareils mobiles (MDM). L’application doit être conçue pour prendre en charge la configuration des applications.
- **Applications gérées** : application qui a été développée pour intégrer le SDK d’application Intune. Également connu sous le nom de Gestion des applications mobiles sans inscription ([MAM-WE](app-management.md#mobile-application-management-mam-basics)). Vous pouvez également wrapper une application pour implémenter et prendre en charge le SDK d’application Intune. Pour plus d’informations sur le wrapping d’une application, consultez [Préparer des applications métier pour les stratégies de protection des applications](../developer/apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Les applications gérées par Intune effectuent un check-in toutes les 30 minutes pour connaître l’état de la stratégie de configuration des applications Intune, quand elles sont déployées conjointement avec une stratégie de protection d’application Intune. Si une stratégie de protection d’application Intune n’est pas attribuée à l’utilisateur, l’intervalle de check-in de la stratégie de configuration des applications Intune est défini sur 720 minutes.

## <a name="apps-that-support-app-configuration"></a>Applications qui prennent en charge la configuration d’application

### <a name="managed-devices"></a>Appareils gérés
Vous pouvez utiliser des stratégies de configuration des applications pour les applications qui les prennent en charge. Pour que la configuration des applications soit prise en charge dans Intune, les applications doivent être écrites de sorte à prendre en charge l’utilisation des configurations d’applications, comme défini par le système d’exploitation. Pour plus d’informations sur les clés de configuration d’application prises en charge, consultez le fournisseur de votre application.

### <a name="managed-apps"></a>Applications gérées
Vous pouvez préparer votre application métier en incorporant le [SDK d’application Intune](../developer/app-sdk.md) dans l’application ou en wrappant l’application une fois qu’elle a été développée à l’aide de l’[outil de wrapping d’application Intune](../developer/apps-prepare-mobile-application-management.md). Le SDK d’application Intune s’efforce de minimiser la quantité de modifications du code pour les développeurs d’applications. Pour plus d’informations, consultez [Vue d’ensemble du SDK d’application Intune](../developer/app-sdk.md). Pour voir la différence entre le SDK d’application Intune et l’outil de wrapping d’application Intune, consultez [Préparer des applications métier pour les stratégies de protection des applications](../developer/apps-prepare-mobile-application-management.md#feature-comparison).

Le **type d’inscription d’appareil** **Applications gérées** référence en particulier les applications configurées par des stratégies de configuration Intune sur les appareils qui ne sont pas inscrits dans la gestion des appareils, alors que le type **Appareils gérés** s’applique aux applications déployées sur le canal MDM et donc gérées par Intune. Sélectionnez le choix approprié en fonction de ces descriptions. 

![Type d’inscription de l’appareil](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Pour les applications qui ont plusieurs identités, comme Microsoft Outlook, les préférences utilisateur peuvent être prises en compte. La boîte de réception Prioritaire, par exemple, respecte le paramètre utilisateur et ne change pas la configuration. D’autres paramètres vous permettent de contrôler si un utilisateur peut ou ne peut pas changer le paramètre. Pour plus d’informations, consultez [Déploiement des paramètres de configuration de l’application Outlook pour iOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Valider la stratégie de configuration d’applications appliquée

Vous pouvez valider la stratégie de configuration des applications à l’aide des trois méthodes suivantes :

   1. En observant l’appareil. L’application ciblée a-t-elle le comportement appliqué dans la stratégie de configuration des applications ?
   2. Via les journaux de diagnostic (consultez la section Journaux de diagnostic ci-dessous).
   3. Dans le portail Intune. La section **Superviser** d’une stratégie peut indiquer l’état approprié :

      ![Première capture d’écran de l’état d’installation de l’appareil](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Deuxième capture d’écran de l’état d’installation de l’appareil](./media/app-configuration-policies-overview/device-install-status-2.png)

      Par ailleurs, sous **Intune** -> **Appareils** -> **Tous les appareils** à gauche de l’écran, l’option **Configuration de l’application** montre toutes les stratégies attribuées et leur état :

      ![Capture d’écran de la configuration de l’application](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="diagnostic-logs"></a>Journaux de diagnostic

### <a name="ios-configuration-on-unmanaged-devices"></a>Configuration iOS sur les appareils non gérés

Vous pouvez valider une configuration iOS avec **le journal de diagnostic Intune** sur les appareils non gérés pour la configuration des apps gérées.

1. Si ce n'est pas déjà fait, téléchargez et installez l’app **Intune Managed Browser** depuis l'App Store. Pour plus d’informations, consultez [Applications protégées par Microsoft Intune](apps-supported-intune-apps.md).
2. Lancez **Intune Managed Browser** et sélectionnez **à propos de** > **intunehelp** dans la barre de navigation.
3. Cliquez sur **Mise en route**.
4. Cliquez sur **Partager les journaux**.
5. Utilisez l'application de messagerie de votre choix pour vous envoyer le journal et l’afficher sur votre PC. 
6. Passez en revue le fichier **IntuneMAMDiagnostics.txt** dans votre visionneuse de fichier texte.
7. Recherchez `ApplicationConfiguration`. Les résultats ressemblent à ce qui suit :

    ``` JSON
        {
            (
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.BlockListURLs";
                    Value = "https://www.aol.com";
                },
                {
                    Name = "com.microsoft.intune.mam.managedbrowser.bookmarks";
                    Value = "Outlook Web|https://outlook.office.com||Bing|https://www.bing.com";
                }
            );
        },
        {
            ApplicationConfiguration =             
            (
                {
                Name = IntuneMAMUPN;
                Value = "CMARScrubbedM:13c45c42712a47a1739577e5c92b5bc86c3b44fd9a27aeec3f32857f69ddef79cbb988a92f8241af6df8b3ced7d5ce06e2d23c33639ddc2ca8ad8d9947385f8a";
                },
                {
                Name = "com.microsoft.outlook.Mail.NotificationsEnabled";
                Value = false;
                }
            );
        }
    ```

Les détails de configuration de votre application doivent correspondre aux stratégies de configuration de l'application configurées pour votre locataire. 

![Configuration d’application ciblée](./media/app-configuration-policies-overview/targeted-app-configuration-3.png)

### <a name="ios-configuration-on-managed-devices"></a>Configuration iOS sur les appareils gérés

Vous pouvez valider une configuration iOS avec **le journal de diagnostic Intune** sur les appareils gérés pour la configuration des apps gérées.

1. Si ce n'est pas déjà fait, téléchargez et installez l’app **Intune Managed Browser** depuis l'App Store. Pour plus d’informations, consultez [Applications protégées par Microsoft Intune](apps-supported-intune-apps.md).
2. Lancez **Intune Managed Browser** et sélectionnez **à propos de** > **intunehelp** dans la barre de navigation.
3. Cliquez sur **Mise en route**.
4. Cliquez sur **Partager les journaux**.
5. Utilisez l'application de messagerie de votre choix pour vous envoyer le journal et l’afficher sur votre PC. 
6. Passez en revue le fichier **IntuneMAMDiagnostics.txt** dans votre visionneuse de fichier texte.
7. Recherchez `AppConfig`. Vos résultats doivent correspondre aux stratégies de configuration de l'application configurées pour votre locataire.

### <a name="android-configuration-on-managed-devices"></a>Configuration Android sur les appareils gérés

Vous pouvez valider une configuration iOS avec **le journal de diagnostic Intune** sur les appareils gérés pour la configuration des apps gérées.

Pour collecter les journaux à partir d'un appareil Android, vous ou l'utilisateur final devez télécharger les journaux à partir de l'appareil via une connexion USB (ou l’**explorateur de fichiers** équivalent disponible sur l'appareil). Voici la procédure à suivre :

1. Connectez l’appareil Android à votre ordinateur avec le câble USB.
2. Sur l’ordinateur, recherchez un répertoire portant le nom de votre appareil. Dans ce répertoire, recherchez `Android Device\Phone\Android\data\com.microsoft.windowsintune.companyportal`.
3. Dans le dossier `com.microsoft.windowsintune.companyportal`, ouvrez le dossier Fichiers, puis `OMADMLog_0`.
3. Recherchez `AppConfigHelper` pour trouver les messages relatifs à la configuration de l'application. Les résultats ressembleront au bloc de données suivant :

    `2019-06-17T20:09:29.1970000       INFO   AppConfigHelper     10888  02256  Returning app config JSON [{"ApplicationConfiguration":[{"Name":"com.microsoft.intune.mam.managedbrowser.BlockListURLs","Value":"https:\/\/www.aol.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.bookmarks","Value":"Outlook Web|https:\/\/outlook.office.com||Bing|https:\/\/www.bing.com"},{"Name":"com.microsoft.intune.mam.managedbrowser.homepage","Value":"https:\/\/www.arstechnica.com"}]},{"ApplicationConfiguration":[{"Name":"IntuneMAMUPN","Value":"AdeleV@M365x935807.OnMicrosoft.com"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled","Value":"false"},{"Name":"com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed","Value":"false"}]}] for user User-875363642`
    
## <a name="graph-api-support-for-app-configuration"></a>Prise en charge de l’API Graph pour la configuration d’application

Vous pouvez utiliser l’API Graph pour accomplir des tâches de configuration d’application. Pour plus d’informations, consultez [Configuration ciblée de gestion des applications mobiles de référence pour API Graph](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="using-logs-to-show-a-configuration-parameter"></a>Utilisation des journaux pour afficher un paramètre de configuration
Quand les journaux montrent un paramètre de configuration qui est effectivement appliqué, mais ne semble pas fonctionner, il y a peut-être un problème au niveau de l’implémentation de la configuration par le développeur de l’application. Contactez d’abord le développeur de l’application ou consultez sa base de connaissances pour éviter d’appeler le support Microsoft. Si le problème est lié à la gestion de la configuration dans une application, il doit être résolu dans une prochaine version mise à jour de cette application.

## <a name="next-steps"></a>Étapes suivantes

### <a name="managed-devices"></a>Appareils gérés

- Découvrez comment utiliser la configuration d’application avec vos appareils iOS.  Consultez [Ajouter des stratégies de configuration d’applications pour les appareils iOS gérés](app-configuration-policies-use-ios.md).
- Découvrez comment utiliser la configuration d’application avec vos appareils Android.  Consultez [Ajouter des stratégies de configuration d’applications pour les appareils Android gérés](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Applications gérées

- Découvrez comment utiliser la configuration d’application avec des applications gérées. Consultez [Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil](app-configuration-policies-managed-app.md).
