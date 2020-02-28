---
title: Résoudre les problèmes de profils de messagerie dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les problèmes courants et les solutions avec les profils de messagerie dans Microsoft Intune, notamment les profils de messagerie en double et les erreurs sur les appareils Android Samsung KNOX Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512668"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Problèmes courants avec les profils de messagerie dans Microsoft Intune et résolutions

Découvrez quelques problèmes de profils de messagerie courants et des instructions pour les résoudre.

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Les profils de messagerie sont déployés pour l’utilisateur qui a inscrit l’appareil. Pour configurer le profil de messagerie, Intune utilise les propriétés Azure Active Directory (AD) dans le profil de messagerie de l’utilisateur lors de l’inscription. La section [Ajouter des paramètres e-mail à des appareils](email-settings-configure.md) peut constituer une bonne ressource.
- Pour Android Entreprise, déployez Gmail ou Nine for Work à l’aide du Google Play Store géré. La section [Ajouter des applications de Google Play géré](../apps/apps-add-android-for-work.md) répertorie les différentes étapes.
- Microsoft Outlook pour iOS/iPadOS et Android ne prennent pas en charge les profils de messagerie. Déployez à la place une stratégie de configuration d’application. Pour plus d’informations, consultez [Paramètres de configuration Outlook](../apps/app-configuration-policies-outlook.md).
- Les profils de messagerie ciblés sur des groupes d’appareils (et non des groupes d’utilisateurs) peuvent ne pas être remis à l’appareil. Lorsque l’appareil possède un utilisateur principal, le ciblage de l’appareil devrait fonctionner. Si le profil de messagerie contient des certificats d’utilisateur, assurez-vous de cibler des groupes d’utilisateurs.
- Les utilisateurs peuvent être invités à entrer leur mot de passe de manière répétée pour le profil de messagerie. Dans ce scénario, vérifiez tous les certificats référencés dans le profil de messagerie. Si l’un des certificats n’est pas ciblé pour un utilisateur, Intune tente de déployer le profil de messagerie.

## <a name="device-already-has-an-email-profile-installed"></a>Un profil de messagerie est déjà installé sur l’appareil

Si les utilisateurs créent un profil de messagerie avant de s’inscrire dans Intune ou Office 365 MDM, le profil de messagerie déployé par Intune peut ne pas fonctionner comme prévu :

- **iOS/iPadOS** : Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Le profil de messagerie créé par l’utilisateur bloque le déploiement du profil créé par Intune. Il s’agit d’un problème courant, car les utilisateurs iOS/iPadOS créent généralement un profil de messagerie, puis s’inscrivent. L’application Portail d’entreprise indique que l’utilisateur n’est pas conforme et peut inviter l’utilisateur à supprimer le profil de messagerie.

  L’utilisateur doit supprimer son profil de messagerie pour que le profil Intune puisse être déployé. Pour éviter ce problème, demandez à vos utilisateurs de s’inscrire et autorisez Intune à déployer le profil de messagerie. Ensuite, les utilisateurs peuvent créer leur profil de messagerie.

- **Windows** : Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Intune remplace le profil de messagerie existant créé par l’utilisateur.

- **Samsung KNOX Standard** : Intune identifie un compte de messagerie en double en fonction de l’adresse e-mail et le remplace par le profil Intune. Si l’utilisateur configure ce compte, il est remplacé à nouveau par le profil Intune. Cela peut entraîner une certaine confusion pour l’utilisateur dont la configuration de compte est remplacée.

Samsung KNOX n’utilise pas le nom d’hôte pour identifier le profil. Nous vous recommandons de ne pas créer plusieurs profils de messagerie à déployer sur la même adresse e-mail sur des hôtes différents, car ils se remplacent mutuellement.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>Erreur 0x87D1FDE8 pour appareil KNOX Standard

**Problème** : après la création et le déploiement d’un profil de messagerie Exchange Active Sync pour Samsung KNOX Standard sur différents appareils Android, l’erreur **0x87D1FDE8** ou un **échec de correction** est affiché(e) sous l’onglet Propriétés > Stratégie de l’appareil.

Examinez la configuration de votre profil EAS pour Samsung KNOX et la stratégie source. L’option de synchronisation Samsung Notes n’étant plus prise en charge, nous vous invitons à ne pas la sélectionner dans votre profil. Assurez-vous que les appareils ont suffisamment de temps pour traiter la stratégie (jusqu’à 24 heures).

## <a name="unable-to-send-images-from--email-account"></a>Impossible d’envoyer des images à partir du compte de messagerie

Les utilisateurs qui disposent de comptes de messagerie configurés automatiquement ne peuvent pas envoyer des photos ou des images à partir de leur appareil. Ce scénario peut se produire si l’option **Autoriser l’envoi d’e-mails à partir d’applications tierces** n’est pas activée.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration**.
3. Sélectionnez votre profil de messagerie > **Propriétés** > **Paramètres**.
4. Définissez le paramètre **Autoriser l’envoi de courrier électronique à partir d’applications tierces** sur **Activer**.

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](../fundamentals/get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
