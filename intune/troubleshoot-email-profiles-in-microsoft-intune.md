---
title: Résoudre les problèmes de profils de messagerie dans Microsoft Intune - Azure | Microsoft Docs
description: Cette rubrique présente des problèmes de profils de messagerie et fournit des instructions pour les résoudre.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: troubleshooting
ms.prod: ''
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
ms.openlocfilehash: 02eac7eaa42f6f9c97426e0536e48a4bc399ed08
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461020"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Résoudre les problèmes de profil de messagerie dans Microsoft Intune

Découvrez quelques problèmes de profils de messagerie courants et des instructions pour les résoudre.

Si ces informations ne vous aident pas, vous pouvez également [bénéficier d’un support technique pour Microsoft Intune](get-support.md).

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

## <a name="device-already-has-an-email-profile-installed"></a>Un profil de messagerie est déjà installé sur l’appareil

Si l’utilisateur a installé un profil de messagerie avant de configurer un profil Intune, le résultat du déploiement du profil de messagerie Intune dépend de la plateforme de l’appareil :

- **iOS**: Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Le profil de messagerie en double créé par l’utilisateur bloque le déploiement d’un profil créé par un administrateur Intune. Il s’agit d’un problème courant, car les utilisateurs iOS créent généralement un profil de messagerie, puis s’inscrivent. Le portail d’entreprise signale à l’utilisateur qu’il n’est pas conforme à cause de son profil de messagerie configuré manuellement et l’invite à supprimer ce profil. L’utilisateur doit supprimer son profil de messagerie pour que le profil Intune puisse être déployé. Pour éviter ce problème, demandez à vos utilisateurs de s’inscrire et autorisez Intune à déployer le profil. Ensuite, installez le profil de messagerie créé par l’utilisateur.

- **Windows** : Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Intune remplace le profil de messagerie existant créé par l’utilisateur.

- **Samsung KNOX Standard** : Intune identifie un compte de messagerie en double en fonction de l’adresse e-mail et le remplace par le profil Intune. Si l’utilisateur configure ce compte, il est remplacé à nouveau par le profil Intune. Cela peut entraîner une certaine confusion pour l’utilisateur dont la configuration de compte est remplacée.

Samsung KNOX n’utilise pas le nom d’hôte pour identifier le profil. Nous vous recommandons de ne pas créer plusieurs profils de messagerie à déployer sur la même adresse e-mail sur des hôtes différents, car ils se remplacent mutuellement.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>Erreur 0x87D1FDE8 pour appareil KNOX Standard
**Problème** : Après la création et le déploiement d’un profil de messagerie Exchange Active Sync pour Samsung KNOX Standard sur différents appareils Android, l’erreur **0x87D1FDE8** ou un **échec de correction** est signalé(e) sous l’onglet Propriétés > Stratégie de l’appareil.

Examinez la configuration de votre profil EAS pour Samsung KNOX et la stratégie source. L’option de synchronisation Samsung Notes n’étant plus prise en charge, nous vous invitons à ne pas la sélectionner dans votre profil. Assurez-vous que les appareils ont suffisamment de temps pour traiter la stratégie (jusqu’à 24 heures).

## <a name="next-steps"></a>Étapes suivantes
Si ces informations ne vous aident pas, vous pouvez également [bénéficier d’un support technique pour Microsoft Intune](get-support.md).
