---
title: Gérer les appareils avec profil professionnel Android Entreprise dans Microsoft Intune
titleSuffix: ''
description: Microsoft Intune gère les appareils avec profil professionnel Android Entreprise pour renforcer la confidentialité et les fonctionnalités de gestion dans le cadre de l’utilisation professionnelle des appareils Android personnels.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 305ed5c18ad0e8beeaa47bc644266d4cb19f80e6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61501049"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Gérer les appareils avec profil professionnel Android avec Intune

Android Entreprise offre un ensemble d’options d’inscription qui fournissent aux utilisateurs les fonctionnalités les plus à jour et sécurisées. L’inscription avec profil professionnel Android Entreprise autorise un ensemble de fonctionnalités et de services qui séparent les applications et les données personnelles des applications et des données professionnelles. Elle offre également des fonctionnalités de gestion et une confidentialité supplémentaires dans le cadre de l’utilisation professionnelle des appareils Android personnels. 

## <a name="supported-devices"></a>Appareils pris en charge

Les fonctionnalités de gestion d’Android Entreprise s’appuient sur des fonctionnalités qui font partie des systèmes d’exploitation Android plus récents. Pour les appareils qui ne prennent pas en charge Android Entreprise, la gestion Android conventionnelle reste disponible. Pour plus d’informations, consultez [Configuration requise pour Android Entreprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Intégration

Avant d’inscrire des appareils Android Entreprise avec profil professionnel, vous devez effectuer certaines étapes d’intégration. Ces étapes établissent une connexion entre votre locataire Intune et Google Play géré. Pour plus d’informations, consultez [Activer l’inscription des appareils avec profil professionnel Android Entreprise](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Gestion des profils professionnels

Quand vous gérez un appareil avec profil professionnel Android Entreprise avec Intune, vous ne gérez pas tout l’appareil. Les fonctionnalités de gestion affectent seulement le profil professionnel créé sur l’appareil lors de l’inscription. Toutes les applications déployées sur l’appareil avec Intune sont installées dans le profil professionnel. Les icônes des applications du profil professionnel diffèrent des applications personnelles sur l’appareil. Toutes les applications Android et les données en dehors de la partie Android Entreprise de l’appareil restent personnelles et sous le contrôle de l’utilisateur final. Les utilisateurs peuvent installer les applications de leur choix dans la partie personnelle de l’appareil. Les administrateurs peuvent gérer et surveiller les applications et les actions dans les limites du profil professionnel.

Intune fournit un certain nombre de paramètres généraux intégrés que vous pouvez configurer sur les appareils avec profil professionnel Android. Pour plus d’informations, consultez [Paramètres de stratégie des appareils avec profil professionnel Android](compliance-policy-create-android-for-work.md).

## <a name="app-publishing-and-distribution"></a>Distribution et publication des applications

Google Play géré fait partie intégrante de la distribution et de la gestion des applications Android Entreprise. Toutes les applications déployées sur les appareils Android avec profil professionnel Android Entreprise dans le profil professionnel proviennent du service Google Play géré. Pour gérer et déployer des applications dans le Play Store, vous vous connectez au site web de Google Play avec les informations d’identification d’administrateur de votre entreprise pour la gestion de Google. Vous pouvez approuver des applications pour le déploiement Android Entreprise afin qu’elles apparaissent dans les profils professionnels des appareils. Ces applications peuvent alors se synchroniser à la console Intune où elles peuvent ensuite être déployées et gérées à l’aide d’Intune. Les applications métier développées par votre organisation doivent être publiées sur Google Play géré avec la console de publication des applications Android de Google. Les applications métier doivent être configurées dans la console de publication d’applications Android pour restreindre l’accès à votre organisation.

Les applications peuvent être installées sans que l’utilisateur n’intervienne ni n’autorise une **installation provenant de sources inconnues**. Pour rechercher et installer des applications facultatives ou disponibles, l’utilisateur peut parcourir le magasin Play for Work sur son appareil. Pour plus d’informations, consultez [Affecter des applications à des appareils avec profil professionnel Android Entreprise en utilisant Intune](apps-add-android-for-work.md).

## <a name="app-configuration"></a>Configuration de l’application

Android Entreprise fournit une infrastructure pour le déploiement de valeurs de configuration d’application sur les applications qui les prennent en charge. En spécifiant des valeurs de configuration pour les applications professionnelles, ces valeurs sont correctement définies quand les utilisateurs lancent l’application pour la première fois. Pour que la configuration des applications soit prise en charge, les développeurs d’applications doivent créer leurs applications Android afin que celles-ci prennent en charge les valeurs de configuration gérées. Si tel est le cas, vous pouvez utiliser Intune pour spécifier et appliquer ces paramètres de configuration. Pour plus d’informations, consultez [Ajouter des stratégies de configuration d’applications pour les appareils Android gérés](app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>Configuration de la messagerie

Android Entreprise ne fournit pas d’application de messagerie par défaut ou de profil de messagerie natif, contrairement à iOS. Par contre, vous pouvez définir les configurations de messagerie en appliquant les paramètres de configuration d’application aux applications de messagerie qui les prennent en charge. Gmail et Nine Work sont deux applications clientes Exchange ActiveSync (EAS) du Play Store, qui prennent en charge la configuration avec la configuration d’applications Android Entreprise.

Intune fournit des modèles de configuration pour les applications Gmail et Nine Work gérées en tant qu’applications de travail. Les autres applications de messagerie qui prennent en charge les profils de configuration d’application peuvent être configurées avec des stratégies de configuration d’application mobile.

Si vous utilisez un accès conditionnel Exchange ActiveSync pour des appareils Android avec profil professionnel Android Entreprise, envisagez d’utiliser l’application de messagerie Gmail ou Nine Work. L’application Microsoft Outlook pour Android, ou toute autre application de messagerie qui utilise l’authentification moderne par le biais d’ADAL, est également prise en charge. Pour plus d’informations, consultez [Guide pratique pour configurer des paramètres de messagerie dans Microsoft Intune](email-settings-configure.md).

## <a name="app-protection-policies"></a>Stratégies de protection des applications

Les stratégies de protection des applications sont entièrement prises en charge dans le profil de travail du profil personnel. Vous pouvez publier des applications métier dans la console de publication d’applications Android à l’adresse https://play.google.com/apps/publish. Cette console inclut une option permettant de réserver les applications à votre organisation. Pour plus d’informations, consultez [Ajouter une stratégie de conformité des appareils pour les appareils avec profil professionnel Android Entreprise dans Intune](compliance-policy-create-android-for-work.md). Pour des informations générales sur les stratégies de protection d’application, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md).

## <a name="vpn-profiles"></a>Profils VPN

La prise en charge VPN est similaire à celle des profils VPN Android. Les mêmes fournisseurs de VPN et les mêmes options de configuration de base sont disponibles pour la gestion Android Entreprise, à deux différences près :

-  **VPN limité au profil professionnel** : les connexions VPN sont limitées aux applications déployées sur le profil professionnel. Seules les applications gérées par Android Entreprise peuvent utiliser la connexion VPN. Les applications personnelles sur l’appareil ne peuvent pas utiliser de connexion VPN gérée. Pour plus d’informations, consultez [Paramètres VPN pour Android Entreprise](vpn-settings-android.md#android-enterprise-vpn-settings).

-  **VPN spécifique à une application** : un VPN spécifique à une application peut être configuré dans Intune si le fournisseur de VPN prend en charge les éléments suivants :
    - configuration pour un VPN spécifique à l’application
    - capacité à configurer un VPN par application via le profil de configuration d’application Android Entreprise.
    Pour plus d’informations, consultez [Utiliser un profil personnalisé Microsoft Intune pour créer un profil VPN par application pour les appareils Android](android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Profils de certificat

Les options de configuration de profil de certificat qui sont disponibles pour la gestion Android sont également disponibles sur les appareils Android Entreprise avec profil professionnel. Android Entreprise fournit des API de gestion de certificats avancée. La gestion de certificats avancée offre les fonctionnalités suivantes :

-  Elle garantit que le déploiement des certificats s’effectue sans assistance et de façon transparente vis-à-vis de l’utilisateur.
-  Elle garantit que les certificats déployés sont supprimés quand un appareil est mis hors service dans Intune et que le profil professionnel est supprimé.
-  Elle fournit une messagerie améliorée qui informe les utilisateurs que le certificat a été déployé et configuré par leur service informatique par le biais de leur service de gestion.

Pour plus d’informations, consultez [Configurer un profil de certificat pour vos appareils dans Microsoft Intune](certificates-configure.md).

## <a name="wi-fi-profiles"></a>Profils Wi-Fi

Les profils Wi-Fi gérés par Android Entreprise sont supprimés quand l’appareil est mis hors service dans Intune et que le profil professionnel est supprimé. Pour plus d’informations, consultez [Guide pratique pour configurer des paramètres Wi-Fi dans Microsoft Intune](wi-fi-settings-configure.md).

## <a name="next-steps"></a>Étapes suivantes
- [Inscrire des appareils Android](android-enroll.md)
- [Affecter des applications à des appareils avec profil professionnel Android Entreprise en utilisant Intune](apps-add-android-for-work.md)
