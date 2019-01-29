---
title: Configurer l’inscription Intune pour les appareils Android entièrement gérés
titlesuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android entièrement gérés dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: d457ca413f3069e8528dc6f4951f834e3f1dac6a
ms.sourcegitcommit: 2a1720184cec577684a64af85d0d731693d11d81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55146908"
---
# <a name="set-up-intune-enrollment-of-android-fully-managed-devices-preview"></a>Configurer l’inscription Intune des appareils Android entièrement gérés (préversion)

Les appareils Android entièrement gérées sont des appareils d’entreprise associés à un seul utilisateur et utilisées exclusivement à des fins professionnelles. Les administrateurs peuvent gérer entièrement l’appareil et appliquer des contrôles de stratégie non disponibles dans les profils professionnels, pour notamment :
- autoriser l’installation d’applications provenant uniquement du Google Play géré ;
- bloquer la désinstallation d’applications gérées ;
- empêcher les utilisateurs de réinitialiser leur appareil aux paramètres d’usine, etc.

Intune vous permet de déployer des applications et des paramètres sur des appareils Android Enterprise, y compris des appareils Android entièrement gérés. Pour plus d’informations sur Android Entreprise, consultez [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Spécifications techniques

Vous devez disposer d’un locataire autonome Intune pour gérer des appareils Android entièrement gérés. La gestion d’appareils entièrement gérés n’est pas disponible en mode hybride (avec connexion à SCCM) ni dans la console de gestion Silverlight héritée.

Les appareils doivent respecter les exigences suivantes pour pouvoir être gérés en tant qu’appareils Android entièrement gérés :

- Système d’exploitation Android version 5.1 et ultérieures.
- Les appareils doivent exécuter une build d’Android disposant d’une connectivité à GMS (Google Mobile Services). Les appareils doivent avoir accès à GMS et doivent pouvoir s’y connecter.

Aucune restriction ne vise le fabricant de l’appareil/OEM si les exigences ci-dessus sont remplies.

## <a name="set-up-android-fully-managed-device-management"></a>Configurer la gestion d’appareils Android entièrement gérés

Pour configurer la gestion d’appareils Android entièrement gérés, effectuez les étapes suivantes :

1. Pour préparer la gestion des appareils mobiles, vous devez [choisir **Microsoft Intune** comme autorité de gestion des appareils mobiles (MDM)](mdm-authority-set.md). Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.
2. [Connectez votre compte de locataire Intune à votre compte d’entreprise Android](connect-intune-android-enterprise.md).
3. [Activez les appareils utilisateur appartenant à l’entreprise](#enable-corporate-owned-user-devices).
4. [Inscrivez les appareils entièrement gérés](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Activer les appareils utilisateur appartenant à l’entreprise

1. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Inscription d’appareil** > **Inscription Android** > **Appareils utilisateur entièrement gérés appartenant à l’entreprise (préversion)**.
2. Sous **Autoriser les utilisateurs à inscrire des appareils d’utilisateur appartenant à l’entreprise**, choisissez **Oui**.

Si vous choisissez **Oui**, vous recevez un jeton d’inscription (chaîne aléatoire) et un code QR pour votre locataire Intune. Ce jeton d’inscription unique est valide pour tous vos utilisateurs et n’expire pas. En fonction du système d’exploitation Android et de la version de l’appareil, vous pouvez utiliser le jeton ou le code QR pour inscrire l’appareil kiosque.

## <a name="enroll-the-fully-managed-devices"></a>Inscrire les appareils entièrement gérés
Vous pouvez à présent [inscrire vos appareils entièrement gérés](android-dedicated-devices-fully-managed-enroll.md).

## <a name="considerations-for-this-preview-feature"></a>Considérations liées à cette fonctionnalité d’évaluation
Cette préversion publique inclut un ensemble de fonctionnalités de base pour le jeu de solutions Android entièrement gérées. Nous aimerions avoir votre avis sur votre utilisation des fonctionnalités d’évaluation. Utilisez l’un de vos canaux de communication actuels, comme [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas?category_id=210853), pour envoyer vos commentaires à l’équipe.

Cette préversion prend en charge les fonctionnalités suivantes pour les appareils Android entièrement gérés :
- Inscription des appareils à l’aide de NFC, d’une entrée de jeton, d’un code QR et de Zero Touch
- Configuration d’appareils pour des groupes d’utilisateurs
- Distribution et configuration d’applications pour des groupes d’utilisateurs


Quand vous utilisez ces fonctionnalités d’évaluation, gardez les points suivants à l’esprit :
- Les fonctionnalités d’évaluation ne sont pas recommandées pour les déploiements stratégiques ou de production. 
- Les fonctionnalités d’évaluation sont implémentées selon les normes de production de Microsoft Intune. Cependant, toutes les fonctionnalités Intune ne sont pas disponibles pour une utilisation avec des appareils utilisateur Android entièrement gérés. Les fonctionnalités d’évaluation sont clairement identifiées dans la console Intune avec l’indication « (préversion) ». 
- Les fonctionnalités d’évaluation sont entièrement prises en charge par le biais des canaux de support Intune habituels.
- L’inscription d’appareils Android entièrement gérés à l’aide de Samsung Knox Mobile Enrollment n’est pas prise en charge dans la préversion. 
- L’utilisation de l’application Portail d’entreprise Intune n’est pas prise en charge sur les appareils Android entièrement gérés. 
- Certaines fonctionnalités Intune comme l’accès conditionnel, les stratégies de protection d’applications et le déploiement de certificats ne sont pas prises en charge dans la préversion. 
- Le ciblage de groupes d’appareils dans un profil ou une application n’est pas pris en charge dans la préversion. Seul le ciblage de groupes d’utilisateurs est pris en charge. 
- Il n’y a pas d’interface utilisateur de première classe pour la configuration de la messagerie, du WiFi ou du VPN. Utilisez des stratégies de configuration d’application pour configurer les paramètres de configuration d’application pris en charge.

## <a name="next-steps"></a>Étapes suivantes
- [Ajouter des stratégies de configuration des appareils Android entièrement gérés](device-restrictions-android-for-work.md#device-owner-only)
- [Configurer des stratégies de configuration d’applications pour les appareils Android entièrement gérés](app-configuration-policies-use-android.md)

