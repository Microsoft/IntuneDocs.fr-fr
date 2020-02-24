---
title: Stratégies de protection des applications et profils professionnels dans Microsoft Intune - Azure | Microsoft Docs
description: Voyez les différences ainsi que les avantages et inconvénients de l’utilisation de stratégies de protection des applications ou de profils professionnels pour les appareils personnels ou BYOD Android Entreprise dans Microsoft Intune. Comparez les différences et les fonctionnalités que vous obtenez avec des stratégies de protection des applications sans inscription (APP-WE) et des profils professionnels Android Entreprise.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 99738de7efc473c7886762534c6e377b4dba8397
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415105"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Stratégies de protection des applications et profils professionnels sur des appareils Android Entreprise dans Intune

Dans de nombreuses organisations, les administrateurs sont appelés à protéger des ressources et des données sur différents appareils. L’un des défis consiste à protéger des ressources pour les utilisateurs dotés d’appareils Android Enterprise personnels, également appelés BYOD (Apportez votre propre appareil). Microsoft Intune prend en charge deux scénarios de déploiement Android pour le BYOD :

- Stratégies de protection des applications sans inscription (APP-WE)
- Profils professionnels Android Entreprise

Les scénarios de déploiement de stratégies de protection des applications sans inscription et de profils professionnels Android incluent les fonctionnalités clés suivantes, importantes pour les environnements BYOD :

1. **Protection et ségrégation des données gérées par l’organisation** : les deux solutions de protègent les données d’entreprise en appliquant des contrôles de prévention des pertes de données (DLP) aux données gérées par l’organisation. Ces protections empêchent les fuites accidentelles de données protégées, telles que leur partage accidentel sur une application ou un compte personnel par un utilisateur final. Elles servent également à garantir qu’un appareil accédant aux données est sain et non compromis.

2. **Confidentialité de l'utilisateur final** : Les stratégies de protection des applications sans inscription et les profils professionnels Android Entreprise séparent le contenu des utilisateurs finaux sur l’appareil et les données gérées par l’administrateur de gestion des appareils mobiles (MDM). Dans les deux scénarios, les administrateurs informatiques appliquent des stratégies, telles que l’authentification par code confidentiel (PIN) uniquement, à des applications ou identités gérées par l’organisation. Les administrateurs informatiques ne peuvent ni lire ni effacer des données détenues ou contrôlées par les utilisateurs finaux, ni y accéder.

Vous choisirez des stratégies de protection des applications sans inscription ou des profils professionnels Android Entreprise pour votre déploiement BYOD en fonction de vos exigences et de vos besoins métier. L’objectif de cet article est de vous aider à prendre une décision.

## <a name="about-intune-app-protection-policies"></a>À propos des stratégies de protection des applications Intune

Les stratégies de protection des applications (APP) Intune sont des stratégies de protection des données destinées aux utilisateurs. Les stratégies s’appliquent la protection contre la perte de données au niveau de l’application. Les stratégies de protection des applications (APP) Intune nécessitent que les développeurs d’applications activent les fonctionnalités APP sur les applications qu’ils créent.

Les différentes applications Android sont activées de plusieurs façons pour la stratégie de protection des applications :

1. **Intégration native dans les applications internes de Microsoft** : les applications Microsoft Office pour Android et une sélection d’autres applications Microsoft sont fournies avec des stratégies de protection des applications Intune intégrées. Ces applications Office, telles que Word, OneDrive, Outlook, etc., n’ont pas besoin d’être personnalisées pour appliquer les stratégies. Ces applications peuvent être installées par les utilisateurs finaux directement depuis Google Play Store .

2. **Intégration dans les builds d’applications par les développeurs à l’aide du kit de développement logiciel (SDK) Intune** : les développeurs d’applications peuvent intégrer le kit de développement logiciel (SDK) Intune dans leur code source et recompiler leurs applications pour prendre en charge des fonctionnalités de stratégie de protection des applications Intune.

3. **Inclusion à l’aide de l’outil de création de package d’applications Intune** : certains clients compilent des applications Android (fichier .APK) sans accès au code source. Sans le code source, le développeur ne peut pas intégrer le kit de développement logiciel (SDK) Intune. Sans le kit de développement logiciel (SDK), il ne peut pas activer son application pour les stratégies de protection des applications. Le développeur doit modifier ou recoder l’application pour prendre en charge les stratégies de protection des applications.

    Pour vous aider, Intune inclut l’**outil de création de packages d’applications** pour les applications Android (APK) existantes et crée une application qui reconnaît les stratégies d’application.

    Pour plus d’informations sur cet outil, consultez [Préparer les applications métier aux stratégies de protection des applications](../developer/apps-prepare-mobile-application-management.md).

Pour voir une liste des applications activées avec la stratégie de protection des applications, consultez les [applications gérées avec un ensemble complet de stratégies de protection des applications mobiles](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Scénarios de déploiement

Cette section décrit les caractéristiques importantes des scénarios de déploiement de stratégies de protection des applications sans inscription et du profil professionnel Android Entreprise.

### <a name="app-we"></a>APP-WE

Le déploiement d’APP-WE (stratégies de protection des applications sans inscription) définit des stratégies pour les applications, pas pour les appareils. Dans ce scénario, les appareils ne sont généralement ni inscrits ni gérés par une autorité de gestion des appareils mobiles comme Intune. Pour protéger des applications et l’accès à des données d’entreprise, les administrateurs utilisent des applications pouvant être gérées par des stratégies de protection des applications et appliquent des stratégies de protection des données à ces applications.

Cette fonctionnalité s’applique à :

- Android 4.4 et versions ultérieures

> [!TIP]
> Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md).

Les scénarios des stratégies de protection des applications sans inscription sont destinés aux utilisateurs finaux qui souhaitent avoir une faible empreinte organisationnelle de leurs appareils et ne veulent pas s’engager dans la gestion d’appareils mobiles. En tant qu’administrateur, vous devez toujours protéger vos données. Ces appareils ne sont pas gérés. Des tâches et des fonctionnalités de gestion d’appareils mobiles, telles que le Wi-Fi, le VPN et la gestion des certificats, ne font donc pas partie de ce scénario de déploiement.

### <a name="android-enterprise-work-profiles"></a>Profils professionnels Android Entreprise

Les profils professionnels sont au cœur du scénario de déploiement Android Enterprise, qui est le seul ciblant les cas d’utilisation de BYOD. Le profil professionnel est une partition distincte créée au niveau du système d’exploitation Android et pouvant être gérée par Intune.

Cette fonctionnalité s’applique à :

- appareils Android 5.0 et versions ultérieures avec Google Mobile Services

Un profil professionnel inclut les fonctionnalités suivantes :

- **Fonctionnalités traditionnelles de gestion des appareils mobiles** : Les fonctionnalités clés de gestion des appareils mobiles, telles que la gestion du cycle de vie des applications à l’aide de Google Play géré, sont disponibles dans n’importe quel scénario Android Entreprise. Google Play géré fournit une expérience solide pour installer et mettre à jour des applications sans aucune intervention de l’utilisateur. L’informatique peut également transmettre les paramètres de configuration d’application aux applications d’entreprise. Il ne demande pas non plus aux utilisateurs finaux d’autoriser des installations de sources inconnues. D’autres activités de gestion des appareils mobiles courantes, telles que le déploiement de certificats, la configuration de réseaux Wi-Fi/VPN et la définition de codes secrets, sont disponibles avec des profils professionnels.

- **DLP à la limite du profil professionnel** : Comme les stratégies de protection des applications sans inscription, l’informatique peut appliquer des stratégies de protection des données. Avec un profil professionnel, les stratégies DLP sont appliquées au niveau du profil professionnel, pas au niveau de l’application. Par exemple, la protection contre le copier/coller est appliquée par les paramètres de la stratégie de protection des applications, ou par le profil professionnel. Lorsque l’application est déployée dans un profil professionnel, les administrateurs peuvent suspendre la protection contre le copier/coller dans le profil professionnel en désactivant cette stratégie au niveau de la stratégie de protection des applications.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Conseils d’optimisation de l’expérience avec le profil professionnel

### <a name="when-to-use-app-within-work-profiles"></a>Quand utiliser la stratégie de protection des applications dans des profils professionnels

La stratégie de protection des applications Intune et les profils professionnels sont des technologies complémentaires qui peuvent être utilisées ensemble ou séparément. Du point de vue architectural, les deux solutions appliquent des stratégies sur différentes couches : sur la couche des applications individuelles pour la stratégie de protection des applications, et sur la couche du profil pour le profil professionnel. Le déploiement d’applications gérées avec une stratégie de protection des applications sur une application d’un profil professionnel est un scénario valide et pris en charge. L’utilisation d’une stratégie de protection des applications, de profils professionnels ou d’une combinaison des deux dépend de vos exigences en matière de prévention des pertes de données.

Les paramètres des profils professionnels et des stratégies de protection des applications se complètent en fournissant une couverture supplémentaire si un profil n’est pas conforme aux exigences de protection des données de votre organisation. Par exemple, des profils professionnels natifs ne fournissent pas de contrôles pour restreindre l’enregistrement d’une application à un emplacement de stockage cloud non approuvé. La stratégie de protection des applications inclut cette fonctionnalité. Vous pouvez décider que la prévention des pertes de données assurée uniquement par le profil professionnel est suffisante et choisir de ne pas utiliser de stratégie de protection des applications. Mais vous pouvez également demander une protection assurée par une combinaison des deux.

### <a name="suppress-app-policy-for-work-profiles"></a>Supprimer la stratégie de protection des applications pour les profils professionnels

Vous devrez peut-être prendre en charge les utilisateurs individuels qui disposent de plusieurs appareils (appareils non gérés dans un scénario de stratégies de protection des applications sans inscription et appareils gérés avec des profils professionnels).

Par exemple, vous demandez aux utilisateurs finaux d’entrer un PIN lorsqu’ils ouvrent une application professionnelle. En fonction de l’appareil, les fonctionnalités de PIN sont gérées par la stratégie de protection des applications ou par le profil professionnel. Pour les appareils avec des stratégies de protection des applications sans inscription, le comportement du PIN de lancement est appliqué par la stratégie de protection des applications. Pour les appareils de profils professionnels, vous pouvez utiliser un PIN d’appareil ou de profil professionnel appliqué par le système d’exploitation. Pour réaliser ce scénario, configurez les paramètres de la stratégie de protection des applications de manière qu’ils ne s’appliquent pas *lorsqu’* une application est déployée dans un profil professionnel. Si vous ne configurez pas de cette façon, l’utilisateur final est invité à entrer un PIN, d’abord par l’appareil, et ensuite au niveau de la couche de la stratégie de protection des applications.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Contrôler le comportement de plusieurs identités dans des profils professionnels

Les applications Office, telles qu’Outlook et OneDrive, ont un comportement « multi-identité ». Au sein d’une instance de l’application, l’utilisateur final peut ajouter des connexions à plusieurs comptes distincts ou à des emplacements de stockage dans le cloud. Dans l’application, les données récupérées à ces emplacements peuvent être séparées ou fusionnées. Et l’utilisateur peut basculer entre les identités personnelles (user@outlook.com) et les identités de l’organisation (user@contoso.com) en fonction du contexte.

Lorsque vous utilisez des profils professionnels, vous pouvez vouloir désactiver ce comportement multi-identité. Lorsque vous le désactivez, les instances badgées de l’application dans le profil professionnel peuvent être configurées uniquement avec une identité de l’organisation. Utilisez le paramètre de configuration d’application Comptes autorisés pour prendre en charge les applications Office Android.

Pour plus d’informations, consultez [Déploiement des paramètres de configuration des applications Outlook pour iOS/iPadOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Quand utiliser la stratégie de protection des applications Intune

Il existe plusieurs scénarios de mobilité d’entreprise pour lesquels l’utilisation de la stratégie de protection des applications Intune est la meilleure recommandation.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Des appareils anciens exécutant Android 4.4 à 5.1 sont utilisées

Officiellement, n’importe quel appareil Android à partir de la version 5.0 avec Google Mobile Services prend en charge les profils professionnels et est susceptible d’être géré de cette façon. Toutefois, certains appareils Android 5.0 et 5.1 de certains OEM ne prennent pas en charge les profils professionnels.

Si vous utilisez des versions qui ne prennent pas en charge les profils professionnels, et pour garantir la protection contre les pertes de données de l’organisation sur les appareils, vous devez utiliser les fonctionnalités d’application Intune.

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Pas de gestion des appareils mobiles, pas d’inscription, les services Google ne sont pas disponibles

Certains clients ne souhaitent aucune forme de gestion des appareils, notamment la gestion de profil professionnels et ce, pour différentes raisons :

- Raisons juridiques et de responsabilité
- Par souci de cohérence de l’expérience utilisateur
- L’environnement de l’appareil Android est hautement hétérogène
- Il n’existe pas de connectivité avec les services Google, ce qui est requis pour la gestion de profils professionnels.

Par exemple, les clients qui se trouvent en Chine ou y ont des utilisateurs ne peuvent pas utiliser la gestion des appareils Android dans la mesure où les services Google sont bloqués. Dans ce cas, utilisez la stratégie de protection des applications Intune pour la protection contre la perte de données.

## <a name="summary"></a>Résumé

Avec Intune, les stratégies de protection des applications sans inscription et les profils professionnels Android Entreprise sont disponibles pour votre programme BYOD Android. Le choix de stratégies de protection des applications sans inscription ou des profils professionnels dépend de vos exigences métier et d’utilisation. En résumé, utilisez des profils professionnels si vous avez besoin d’activités de gestion des appareils mobiles sur des appareils gérés, telles que le déploiement de certificats, l’envoi d’applications, etc. Utilisez la stratégie de protection des applications sans inscription si vous ne voulez ou ne pouvez pas gérer des appareils et que vous utilisez uniquement des applications activées avec la stratégie de protection des applications Intune.

## <a name="next-steps"></a>Étapes suivantes
[Commencer à utiliser les stratégies de protection des applications](app-protection-policy.md), ou [Inscrire vos appareils](../enrollment/android-enroll.md).
