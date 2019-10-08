---
title: Configurer l’inscription Intune pour les appareils Android Entreprise entièrement gérés
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android Entreprise entièrement gérés dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2abf391ddbdb1f7087cd06ed1865b3da8b155178
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723578"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Configurer l’inscription Intune des appareils Android Entreprise entièrement gérés 

Les appareils Android Entreprise entièrement gérés sont des appareils de l’entreprise associés à un seul utilisateur et utilisées exclusivement à des fins professionnelles. Les administrateurs peuvent gérer entièrement l’appareil et appliquer des contrôles de stratégie non disponibles dans les profils professionnels, pour notamment :
- Autoriser l’installation d’applications provenant uniquement du Google Play géré.
- Bloquer la désinstallation d’applications gérées.
- Empêcher les utilisateurs de réinitialiser leur appareil aux paramètres d’usine, etc.

Intune vous permet de déployer des applications et des paramètres sur des appareils Android Entreprise, y compris des appareils Android Entreprise entièrement gérés. Pour plus d’informations sur Android Entreprise, consultez [Exigences Android Entreprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="technical-requirements"></a>Spécifications techniques

Vous devez disposer d’un locataire autonome Intune pour gérer des appareils Android Entreprise entièrement gérés. La gestion d’appareils entièrement gérés n’est pas disponible en mode hybride (avec connexion à Configuration Manager) ni dans la console de gestion Silverlight héritée.

Les appareils doivent respecter les exigences suivantes pour pouvoir être gérés en tant qu’appareils Android Entreprise entièrement gérés :

- Système d’exploitation Android versions 6.0 et ultérieures.
- Les appareils doivent exécuter une build d’Android disposant d’une connectivité à GMS (Google Mobile Services). Les appareils doivent avoir accès à GMS et doivent pouvoir s’y connecter.

Aucune restriction ne vise le fabricant de l’appareil/OEM si les exigences ci-dessus sont remplies.

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Configurer la gestion d’appareils Android Entreprise entièrement gérés

Pour configurer la gestion d’appareils Android Entreprise entièrement gérés, effectuez les étapes suivantes :

1. Pour préparer la gestion des appareils mobiles, vous devez [choisir **Microsoft Intune** comme autorité de gestion des appareils mobiles (MDM)](../fundamentals/mdm-authority-set.md). Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.
2. [Connectez votre compte de locataire Intune à votre compte Android Entreprise](connect-intune-android-enterprise.md).
3. [Activez les appareils utilisateur appartenant à l’entreprise](#enable-corporate-owned-user-devices).
4. [Inscrivez les appareils entièrement gérés](#enroll-the-fully-managed-devices).

### <a name="enable-corporate-owned-user-devices"></a>Activer les appareils utilisateur appartenant à l’entreprise

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et choisissez **Inscription d’appareil** > **Inscription Android** > **Appareils utilisateur entièrement gérés appartenant à l’entreprise**.
2. Sous **Autoriser les utilisateurs à inscrire des appareils d’utilisateur appartenant à l’entreprise**, choisissez **Oui**.

> [!NOTE]
> Si vous avez une stratégie d’accès conditionnel Azure AD définie qui utilise le contrôle *Exiger que l’appareil soit marqué comme conforme* et qui s’applique à **toutes les applications cloud**, à **Android** et aux **navigateurs**, vous devez exclure l’application cloud **Microsoft Intune** de cette stratégie. En effet, les processus de configuration Android utilisent un onglet Chrome pour authentifier vos utilisateurs pendant l’inscription. Pour plus d’informations, consultez la [documentation sur l’accès conditionnel Azure AD](https://docs.microsoft.com/azure/active-directory/conditional-access/).

Si vous choisissez **Oui**, vous recevez un jeton d’inscription (chaîne aléatoire) et un code QR pour votre locataire Intune. Ce jeton d’inscription unique est valide pour tous vos utilisateurs et n’expire pas. En fonction du système d’exploitation Android et de la version de l’appareil, vous pouvez utiliser le jeton ou le code QR pour inscrire l’appareil kiosque.

## <a name="enroll-the-fully-managed-devices"></a>Inscrire les appareils entièrement gérés
Vous pouvez à présent [inscrire vos appareils entièrement gérés](android-dedicated-devices-fully-managed-enroll.md).

## <a name="next-steps"></a>Étapes suivantes
- [Ajouter des stratégies de configuration des appareils Android Entreprise entièrement gérés](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Configurer des stratégies de configuration d’applications pour les appareils Android Entreprise entièrement gérés](../apps/app-configuration-policies-use-android.md)
