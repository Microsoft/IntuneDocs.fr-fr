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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cda0453009855d96e7c13e170ba908479a0773ea
ms.sourcegitcommit: 513e805bbea8bf652c2901dfc5460e34946077df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160576"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Stratégies de configuration des applications pour Microsoft Intune

Les stratégies de configuration des applications peuvent vous aider à éliminer les problèmes d’installation des applications en vous permettant d’affecter des paramètres de configuration à une stratégie, à son tour attribuée aux utilisateurs finaux avant qu’ils n’exécutent l’application. Les paramètres sont ensuite fournis automatiquement quand l’application est configurée sur l’appareil des utilisateurs finaux, lesquels n’ont aucune action à effectuer. Les paramètres de configuration sont uniques pour chaque application. 

Vous pouvez créer et utiliser des stratégies de configuration des applications afin de fournir des paramètres de configuration pour des applications iOS ou Android. Ces paramètres de configuration permettent de personnaliser une application selon une [approche conforme aux standards du secteur](https://www.appconfig.org/) pour la gestion et la configuration des applications. Les paramètres de stratégie de configuration sont utilisés quand l’application les recherche, en général à la première exécution. 

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
> ![Capture d’écran d’une application configurée](./media/app-configuration-policy-overview/configured-app.png)
>
> Quand vous choisissez Appareils gérés comme type d’inscription pour les appareils Android, vous voyez uniquement les applications du [Google Play Store géré](https://play.google.com/work) et pas celle du [Google Play Store](https://play.google.com/store/apps). Le Google Play Store géré, aussi appelé Android for Work (AfW), et Android Enterprise sont les applications du profil professionnel qui contiennent les versions d’application qui prennent en charge la configuration des applications.

Vous pouvez attribuer une stratégie de configuration des applications à un groupe d’utilisateurs finaux et d’appareils à l’aide d’une combinaison d’[attributions d’inclusion et d’exclusion](apps-inc-exl-assignments.md). Dès que vous ajoutez une stratégie de configuration d’application, vous pouvez définir les affectations de la stratégie de configuration d’application. Quand vous définissez les attributions de la stratégie, vous pouvez choisir d’inclure et d’exclure les [groupes](groups-add.md) d’utilisateurs finaux auxquels la stratégie s’applique. Quand vous choisissez d’inclure un ou plusieurs groupes, vous pouvez choisir de sélectionner des groupes spécifiques à inclure ou sélectionner des groupes intégrés. Les groupes intégrés sont notamment **Tous les utilisateurs**, **Tous les appareils** et **Tous les utilisateurs + Tous les appareils**.

Vous avez deux options pour utiliser les stratégies de configuration des applications avec Intune :
- **Appareils gérés** : l’appareil est géré par Intune en tant que fournisseur de gestion des appareils mobiles (MDM). L’application doit être conçue pour prendre en charge la configuration des applications.
- **Applications gérées** : application qui a été développée pour intégrer le SDK d’application Intune. Également connu sous le nom de Gestion des applications mobiles sans inscription ([MAM-WE](app-management.md#mobile-application-management-mam-basics)). Vous pouvez également wrapper une application pour implémenter et prendre en charge le SDK d’application Intune. Pour plus d’informations sur le wrapping d’une application, consultez [Préparer des applications métier pour les stratégies de protection des applications](apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Les applications gérées par Intune effectuent un check-in toutes les 30 minutes pour connaître l’état de la stratégie de configuration des applications Intune, quand elles sont déployées conjointement avec une stratégie de protection d’application Intune. Si une stratégie de protection d’application Intune n’est pas attribuée à l’utilisateur, l’intervalle de check-in de la stratégie de configuration des applications Intune est défini sur 720 minutes.

## <a name="apps-that-support-app-configuration"></a>Applications qui prennent en charge la configuration d’application

### <a name="managed-devices"></a>Appareils gérés
Vous pouvez utiliser des stratégies de configuration des applications pour les applications qui les prennent en charge. Pour que la configuration des applications soit prise en charge dans Intune, les applications doivent être écrites de sorte à prendre en charge l’utilisation des configurations d’applications, comme défini par la [Communauté Appconfig](https://www.appconfig.org/members). Pour plus de détails, consultez l’éditeur de l’application.

### <a name="managed-apps"></a>Applications gérées
Vous pouvez préparer votre application métier en incorporant le [SDK d’application Intune](app-sdk.md) dans l’application ou en wrappant l’application une fois qu’elle a été développée à l’aide de l’[outil de wrapping d’application Intune](apps-prepare-mobile-application-management.md). Le SDK d’application Intune s’efforce de minimiser la quantité de modifications du code pour les développeurs d’applications. Pour plus d’informations, consultez [Vue d’ensemble du SDK d’application Intune](app-sdk.md). Pour voir la différence entre le SDK d’application Intune et l’outil de wrapping d’application Intune, consultez [Préparer des applications métier pour les stratégies de protection des applications](apps-prepare-mobile-application-management.md#feature-comparison).

Le **type d’inscription d’appareil** **Applications gérées** référence en particulier les applications configurées par des stratégies de configuration Intune sur les appareils qui ne sont pas inscrits dans la gestion des appareils, alors que le type **Appareils gérés** s’applique aux applications déployées sur le canal MDM et donc gérées par Intune. Sélectionnez le choix approprié en fonction de ces descriptions. 

![Type d’inscription de l’appareil](./media/app-configuration-policy-overview/device-enrollment-type.png)

> [!NOTE]
> Pour les applications qui ont plusieurs identités, comme Microsoft Outlook, les préférences utilisateur peuvent être prises en compte. La boîte de réception Prioritaire, par exemple, respecte le paramètre utilisateur et ne change pas la configuration. D’autres paramètres vous permettent de contrôler si un utilisateur peut ou ne peut pas changer le paramètre. Pour plus d’informations, consultez [Déploiement des paramètres de configuration de l’application Outlook pour iOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Valider la stratégie de configuration d’applications appliquée

Vous pouvez valider la stratégie de configuration des applications à l’aide des trois méthodes suivantes :

   1. En observant l’appareil. L’application ciblée a-t-elle le comportement appliqué dans la stratégie de configuration des applications ?
   2. Via les journaux de diagnostic (consultez la section Journaux de diagnostic ci-dessous).
   3. Dans le portail Intune. La section **Superviser** d’une stratégie peut indiquer l’état approprié :

      ![Première capture d’écran de l’état d’installation de l’appareil](./media/app-configuration-policy-overview/device-install-status-1.png)

      ![Deuxième capture d’écran de l’état d’installation de l’appareil](./media/app-configuration-policy-overview/device-install-status-2.png)

      Par ailleurs, sous **Intune** -> **Appareils** -> **Tous les appareils** à gauche de l’écran, l’option **Configuration de l’application** montre toutes les stratégies attribuées et leur état :

      ![Capture d’écran de la configuration de l’application](./media/app-configuration-policy-overview/app-configuration.png)

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
