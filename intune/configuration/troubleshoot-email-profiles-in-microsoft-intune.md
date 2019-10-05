---
title: Résoudre les problèmes de profils de messagerie dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les problèmes courants et les solutions avec les profils de messagerie dans Microsoft Intune, notamment les profils de messagerie en double et les erreurs sur les appareils Android Samsung KNOX Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
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
ms.openlocfilehash: ec3a5a5aa4d30dcac0f954057f0cc51ffde6a950
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734295"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problèmes courants avec les profils de messagerie dans Microsoft Intune et résolutions

Découvrez quelques problèmes de profils de messagerie courants et des instructions pour les résoudre.

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Les profils de messagerie sont déployés pour l’utilisateur qui a inscrit l’appareil. Pour configurer le profil de messagerie, Intune utilise les propriétés de Azure Active Directory (AD) dans le profil de messagerie de l’utilisateur lors de l’inscription. L' [Ajout de paramètres de messagerie aux appareils](email-settings-configure.md) peut être une bonne ressource.
- Après la migration de Configuration Manager hybride vers la version autonome d’Intune, le profil de messagerie de Configuration Manager hybride reste sur l’appareil pendant 7 jours. Ce comportement est normal. Si vous avez besoin de supprimer le profil de messagerie plus tôt, contactez le [support technique Intune](../fundamentals/get-support.md).
- Pour Android Enterprise, déployez Gmail ou neuf pour le travail à l’aide de la Google Play Store gérée. [Ajouter des applications de Google Play gérées](../apps/apps-add-android-for-work.md) répertorie les étapes.
- Microsoft Outlook pour iOS et Android ne prend pas en charge les profils de messagerie. Au lieu de cela, déployez une stratégie de configuration d’application. Pour plus d’informations, consultez [paramètres de configuration d’Outlook](../apps/app-configuration-policies-outlook.md).
- Les profils de messagerie ciblés sur des groupes d’appareils (et non des groupes d’utilisateurs) peuvent ne pas être remis à l’appareil. Lorsque l’appareil a un utilisateur principal, le ciblage de l’appareil doit fonctionner. Si le profil de messagerie contient des certificats d’utilisateur, assurez-vous de cibler des groupes d’utilisateurs.
- Les utilisateurs peuvent être invités à entrer leur mot de passe de manière répétée pour le profil de messagerie. Dans ce scénario, vérifiez tous les certificats référencés dans le profil de messagerie. Si l’un des certificats n’est pas ciblé pour un utilisateur, Intune tente de déployer le profil de messagerie.

## <a name="device-already-has-an-email-profile-installed"></a>Un profil de messagerie est déjà installé sur l’appareil

Si les utilisateurs créent un profil de messagerie avant de s’inscrire dans Intune ou Office 365 MDM, le profil de messagerie déployé par Intune peut ne pas fonctionner comme prévu :

- **iOS**: Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Le profil de messagerie créé par l’utilisateur bloque le déploiement du profil créé par Intune. Il s’agit d’un problème courant, car les utilisateurs iOS créent généralement un profil de messagerie, puis s’inscrivent. L’application Portail d’entreprise indique que l’utilisateur n’est pas conforme et peut inviter l’utilisateur à supprimer le profil de messagerie.

  L’utilisateur doit supprimer son profil de messagerie pour que le profil Intune puisse être déployé. Pour éviter ce problème, demandez à vos utilisateurs de s’inscrire et autorisez Intune à déployer le profil de messagerie. Ensuite, les utilisateurs peuvent créer leur profil de messagerie.

- **Windows** : Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Intune remplace le profil de messagerie existant créé par l’utilisateur.

- **Samsung KNOX Standard** : Intune identifie un compte de messagerie en double en fonction de l’adresse e-mail et le remplace par le profil Intune. Si l’utilisateur configure ce compte, il est remplacé à nouveau par le profil Intune. Cela peut entraîner une certaine confusion pour l’utilisateur dont la configuration de compte est remplacée.

Samsung KNOX n’utilise pas le nom d’hôte pour identifier le profil. Nous vous recommandons de ne pas créer plusieurs profils de messagerie à déployer sur la même adresse e-mail sur des hôtes différents, car ils se remplacent mutuellement.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Erreur 0x87D1FDE8 pour appareil KNOX Standard

**Problème** : Après la création et le déploiement d’un profil de messagerie Exchange Active Sync pour Samsung KNOX Standard sur différents appareils Android, l’erreur **0x87D1FDE8** ou un **échec de correction** est affiché(e) sous l’onglet Propriétés > Stratégie de l’appareil.

Examinez la configuration de votre profil EAS pour Samsung KNOX et la stratégie source. L’option de synchronisation Samsung Notes n’étant plus prise en charge, nous vous invitons à ne pas la sélectionner dans votre profil. Assurez-vous que les appareils ont suffisamment de temps pour traiter la stratégie (jusqu’à 24 heures).

## <a name="unable-to-send-images-from--email-account"></a>Impossible d’envoyer des images à partir du compte de messagerie

Les utilisateurs qui disposent de comptes de messagerie configurés automatiquement ne peuvent pas envoyer des photos ou des images à partir de leur appareil. Ce scénario peut se produire si l’option **Autoriser l’envoi d’e-mails à partir d’applications tierces** n’est pas activée.

### <a name="intune-solution"></a>Solution Intune

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils**.
3. Sélectionnez votre profil de messagerie > **propriétés** > **paramètres**.
4. Définissez le paramètre **autoriser l’envoi du courrier électronique à partir d’applications tierces** à **activer**.

### <a name="configuration-manager-hybrid"></a>Configuration Manager hybride

1. Dans la console Configuration Manager, ouvrez > **Ressources et Conformité**.

2. Développez **Vue d’ensemble** > **Paramètres de conformité** > **Accès aux ressources d’entreprise**, puis sélectionnez **Profils de messagerie**.

3. Cliquez avec le bouton droit sur le profil de messagerie, puis ouvrez **Propriétés**.

4. Sous l’onglet **Paramètres de synchronisation**, sélectionnez **Autoriser l’envoi de courrier électronique à partir d’applications tierces**.

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](../fundamentals/get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
