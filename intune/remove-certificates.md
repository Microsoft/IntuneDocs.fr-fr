---
title: Supprimer des certificats SCEP ou PKCS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Les administrateurs peuvent utiliser l’action de réinitialisation ou de mise hors service pour supprimer des certificats de Microsoft Intune. Il existe certains scénarios où les certificats sont automatiquement supprimés, tels que la désinscription d’un appareil ou la suppression d’une stratégie de conformité. Dans d’autres scénarios, les certificats restent automatiquement sur l’appareil, par exemple quand la licence Intune est perdue ou supprimée. Consultez les différentes procédures pour les appareils Android, Android Entreprise, iOS, macOS et Windows.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dabd5b6ca2f8bb01421c24cb7c16ab57cf59ef56
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180984"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Supprimer des certificats SCEP et PKCS dans Microsoft Intune

Dans Microsoft Intune, vous pouvez ajouter des certificats SCEP et PKCS à des appareils. En outre, vous pouvez supprimer ces certificats quand vous [réinitialisez](devices-wipe.md#wipe) ou [mettez hors service](devices-wipe.md#retire) l’appareil. Il existe d’autres scénarios où les certificats sont automatiquement supprimés et d’autres encore où les certificats restent sur l’appareil.

Cet article liste quelques scénarios courants et leur impact sur les certificats PKCS et SCEP.

> [!NOTE]
> Pour supprimer et révoquer des certificats pour un utilisateur qui est en cours de suppression d’Active Directory (AD) ou d’Azure AD, veillez à suivre les étapes dans l’ordre :
>
>    1. Réinitialiser ou mettre hors service l’appareil de l’utilisateur
>    2. Supprimer l’utilisateur d’AD ou d’Azure AD

## <a name="windows-devices"></a>Appareils Windows

#### <a name="scep-certificates"></a>Certificats SCEP

- Un certificat SCEP est révoqué *et* supprimé quand :

  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)
  - L’appareil est supprimé du groupe Azure Active Directory (AD)
  - La stratégie de conformité est supprimée de l’affectation de groupe
  - Le profil de configuration est supprimé de l’affectation de groupe

- Un certificat SCEP est révoqué quand :
  - L’administrateur change ou met à jour le profil SCEP

- Le certificat racine est supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)
  - La stratégie de conformité est supprimée de l’affectation de groupe

- Les certificats SCEP **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD

#### <a name="pkcs-certificates"></a>Certificats PKCS

- Un certificat PKCS est révoqué *et* supprimé quand :

  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Le certificat racine est supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Les certificats PKCS **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD
  - L’administrateur change ou met à jour le profil PKCS
  - Le profil de configuration est supprimé de l’affectation de groupe
  - La stratégie de conformité est supprimée de l’affectation de groupe 


## <a name="ios-devices"></a>Périphériques iOS

#### <a name="scep-certificates"></a>Certificats SCEP

- Un certificat SCEP est révoqué *et* supprimé quand :

  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)
  - L’appareil est supprimé du groupe Azure Active Directory (AD)
  - La stratégie de conformité est supprimée de l’affectation de groupe
  - Le profil de configuration est supprimé de l’affectation de groupe

- Un certificat SCEP est révoqué quand :
  - L’administrateur change ou met à jour le profil SCEP

- Le certificat racine est supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)
  - La stratégie de conformité est supprimée de l’affectation de groupe

- Les certificats SCEP **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD

#### <a name="pkcs-certificates"></a>Certificats PKCS

- Un certificat PKCS est révoqué *et* supprimé quand :

  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Un certificat PKCS est supprimé quand :
  - La stratégie de conformité est supprimée de l’affectation de groupe
  - Le profil de configuration est supprimé de l’affectation de groupe
  
- Le certificat racine est supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Les certificats PKCS **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD
  - L’administrateur change ou met à jour le profil PKCS

## <a name="android-knox-devices"></a>Appareils Android Knox

#### <a name="scep-certificates"></a>Certificats SCEP

- Un certificat SCEP est révoqué *et* supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)

- Un certificat SCEP est révoqué quand :
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)
  - L’appareil est supprimé du groupe Azure Active Directory (AD)
  - La stratégie de conformité est supprimée de l’affectation de groupe
  - Le profil de configuration est supprimé de l’affectation de groupe
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure Active Directory (AD)
  - L’administrateur change ou met à jour le profil SCEP

- Le certificat racine est supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Les certificats SCEP **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD

#### <a name="pkcs-certificates"></a>Certificats PKCS

- Un certificat PKCS est révoqué *et* supprimé quand :

  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Le certificat racine est supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [réinitialisation](devices-wipe.md#wipe)
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)

- Les certificats PKCS **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD
  - L’administrateur change ou met à jour le profil PKCS
  - Le profil de configuration est supprimé de l’affectation de groupe
  - La stratégie de conformité est supprimée de l’affectation de groupe 
  
  
> [!NOTE]
> Les scénarios ci-dessus ne s’appliquent pas aux appareils Android for Work. Les appareils Android d’ancienne génération (tous les appareils autres que Samsung, avec un profil non professionnel) ne sont pas activés pour la suppression de certificat. 

## <a name="macos-certificates"></a>Certificats macOS

#### <a name="scep-certificates"></a>Certificats SCEP

- Un certificat SCEP est révoqué *et* supprimé quand :
  - Un utilisateur final se désinscrit
  - L’administrateur exécute une action de [mise hors service](devices-wipe.md#retire)
  - L’appareil est supprimé du groupe Azure Active Directory (AD)
  - La stratégie de conformité est supprimée de l’affectation de groupe
  - Le profil de configuration est supprimé de l’affectation de groupe

- Un certificat SCEP est révoqué quand :
  - L’administrateur change ou met à jour le profil SCEP

- Les certificats SCEP **restent** sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
  - Un utilisateur final perd la licence Intune
  - L’administrateur retire la licence Intune
  - L’administrateur supprime l’utilisateur ou le groupe d’Azure AD

> [!NOTE]
> L’utilisation de l’action de [réinitialisation](devices-wipe.md#wipe) pour réinitialiser des appareils macOS aux paramètres d’usine n’est pas prise en charge.

#### <a name="pkcs-certificates"></a>Certificats PKCS

Les certificats PKCS ne sont pas pris en charge sur macOS.

