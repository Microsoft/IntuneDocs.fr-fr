---
title: Résoudre les problèmes de profils de messagerie dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les problèmes courants et les solutions avec les profils de messagerie dans Microsoft Intune, notamment les profils de messagerie en double et les erreurs sur les appareils Android Samsung KNOX Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0fe37deb63457fef869df0f7263970a4e53cb29
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402720"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problèmes courants avec les profils de messagerie dans Microsoft Intune et résolutions

Découvrez quelques problèmes de profils de messagerie courants et des instructions pour les résoudre.

## <a name="device-already-has-an-email-profile-installed"></a>Un profil de messagerie est déjà installé sur l’appareil

Si les utilisateurs créent un profil de messagerie avant de s’inscrire dans Intune, le profil de messagerie Intune peut ne pas fonctionner comme prévu :

- **iOS**: Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Le profil de messagerie créé par l’utilisateur bloque le déploiement du profil créé par Intune. Il s’agit d’un problème courant, car les utilisateurs iOS créent généralement un profil de messagerie, puis s’inscrivent. L’application Portail d’entreprise indique que l’utilisateur n’est pas conforme et peut inviter l’utilisateur à supprimer le profil de messagerie.

  L’utilisateur doit supprimer son profil de messagerie pour que le profil Intune puisse être déployé. Pour éviter ce problème, demandez à vos utilisateurs de s’inscrire et autorisez Intune à déployer le profil de messagerie. Ensuite, les utilisateurs peuvent créer leur profil de messagerie.

- **Windows** : Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Intune remplace le profil de messagerie existant créé par l’utilisateur.

- **Samsung KNOX Standard** : Intune identifie un compte de messagerie en double en fonction de l’adresse e-mail et le remplace par le profil Intune. Si l’utilisateur configure ce compte, il est remplacé à nouveau par le profil Intune. Cela peut entraîner une certaine confusion pour l’utilisateur dont la configuration de compte est remplacée.

Samsung KNOX n’utilise pas le nom d’hôte pour identifier le profil. Nous vous recommandons de ne pas créer plusieurs profils de messagerie à déployer sur la même adresse e-mail sur des hôtes différents, car ils se remplacent mutuellement.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Erreur 0x87D1FDE8 pour appareil KNOX Standard

**Problème** : Après la création et le déploiement d’un profil de messagerie Exchange Active Sync pour Samsung KNOX Standard sur différents appareils Android, l’erreur **0x87D1FDE8** ou un **échec de correction** est affiché(e) sous l’onglet Propriétés > Stratégie de l’appareil.

Examinez la configuration de votre profil EAS pour Samsung KNOX et la stratégie source. L’option de synchronisation Samsung Notes n’étant plus prise en charge, nous vous invitons à ne pas la sélectionner dans votre profil. Assurez-vous que les appareils ont suffisamment de temps pour traiter la stratégie (jusqu’à 24 heures).

## <a name="unable-to-send-images-from--email-account"></a>Impossible d’envoyer des images à partir du compte de messagerie

S’applique à Intune dans le portail Azure Classic.

Les utilisateurs qui disposent de comptes de messagerie configurés automatiquement ne peuvent pas envoyer des photos ou des images à partir de leur appareil. Ce scénario peut se produire si l’option **Autoriser l’envoi d’e-mails à partir d’applications tierces** n’est pas activée.

### <a name="intune-solution"></a>Solution Intune

1. Ouvrez la console d’administration Microsoft Intune, sélectionnez **Stratégie** Charge de travail > **Stratégie de configuration**.

2. Sélectionnez le profil de messagerie et choisissez **Modifier**.

3. Sélectionnez **Autoriser l’envoi de courrier électronique à partir d’applications tierces**.

### <a name="configuration-manager-integrated-with-intune-solution"></a>Configuration Manager intégré à la solution Intune

1. Dans la console Configuration Manager, ouvrez > **Ressources et Conformité**.

2. Développez **Vue d’ensemble** > **Paramètres de conformité** > **Accès aux ressources d’entreprise**, puis sélectionnez **Profils de messagerie**.

3. Cliquez avec le bouton droit sur le profil de messagerie, puis ouvrez **Propriétés**.

4. Sous l’onglet **Paramètres de synchronisation**, sélectionnez **Autoriser l’envoi de courrier électronique à partir d’applications tierces**.

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).