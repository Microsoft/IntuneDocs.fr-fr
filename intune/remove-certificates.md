---
title: Supprimer des certificats SCEP ou PKCS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Les administrateurs peuvent utiliser l’action de réinitialisation ou de mise hors service pour supprimer des certificats de Microsoft Intune. Il existe certains scénarios où les certificats sont automatiquement supprimés, tels que la désinscription d’un appareil ou la suppression d’une stratégie de conformité. Dans d’autres scénarios, les certificats restent automatiquement sur l’appareil, par exemple quand la licence Intune est perdue ou supprimée. Consultez les différentes procédures pour les appareils Android, Android Entreprise, iOS, macOS et Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: 6a1280ca2a78853ae188ad68620f0b82846a365a
ms.sourcegitcommit: 9daaeba9a960c50efcc951856234fbfec3635737
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59569257"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Supprimer des certificats SCEP et PKCS dans Microsoft Intune

Dans Microsoft Intune, vous pouvez ajouter des certificats SCEP (Simple Certificate Enrollment Protocol) et PKCS (Public Key Cryptography Standards) à des appareils. En outre, vous pouvez supprimer ces certificats quand vous [réinitialisez](devices-wipe.md#wipe) ou [mettez hors service](devices-wipe.md#retire) l’appareil. 

Il existe d’autres scénarios où les certificats sont automatiquement supprimés et d’autres encore où les certificats restent sur l’appareil. Cet article liste quelques scénarios courants et leur impact sur les certificats PKCS et SCEP.

> [!NOTE]
> Pour supprimer et révoquer des certificats pour un utilisateur qui est supprimé du service Azure AD (Azure Active Directory) ou Active Directory local, effectuez les étapes suivantes dans l’ordre :
>
> 1. Réinitialiser ou mettre hors service l’appareil de l’utilisateur.
> 2. Supprimer l’utilisateur du service Azure AD ou Active Directory local.

## <a name="windows-devices"></a>Appareils Windows

#### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).
- L’appareil est supprimé d’un groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat SCEP est révoqué quand :
- Un administrateur change ou met à jour le profil SCEP.

Un certificat racine est supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

#### <a name="pkcs-certificates"></a>Certificats PKCS

Un certificat PKCS est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Un certificat racine est supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Les certificats PKCS *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil PKCS.
- Un profil de certificat est supprimé de l’affectation de groupe.


## <a name="ios-devices"></a>Périphériques iOS

#### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).
- L’appareil est supprimé du groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat SCEP est révoqué quand :
- Un administrateur change ou met à jour le profil SCEP.

Un certificat racine est supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

#### <a name="pkcs-certificates"></a>Certificats PKCS

Un certificat PKCS est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Un certificat PKCS est supprimé quand :
- Un profil de certificat est supprimé de l’affectation de groupe.
  
Un certificat racine est supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Les certificats PKCS *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil PKCS.

## <a name="android-knox-devices"></a>Appareils Android Knox

#### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).

Un certificat SCEP est révoqué quand :
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).
- L’appareil est supprimé d’un groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil SCEP.

Un certificat racine est supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

#### <a name="pkcs-certificates"></a>Certificats PKCS

Un certificat PKCS est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Un certificat racine est supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](devices-wipe.md#retire).

Les certificats PKCS *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil PKCS.
- Un profil de certificat est supprimé de l’affectation de groupe.
  
  
> [!NOTE]
> Les scénarios précédents ne s’appliquent pas aux appareils Android for Work. Les appareils Android d’ancienne génération (tous les appareils autres que Samsung, avec un profil non professionnel) ne sont pas activés pour la suppression de certificat. 

## <a name="macos-certificates"></a>Certificats macOS

#### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :
- Un utilisateur se désinscrit.
- Un administrateur exécute une action de [mise hors service](devices-wipe.md#retire).
- L’appareil est supprimé d’un groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat SCEP est révoqué quand :
- Un administrateur change ou met à jour le profil SCEP.

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

> [!NOTE]
> L’utilisation de l’action de [réinitialisation](devices-wipe.md#wipe) pour réinitialiser des appareils macOS aux paramètres d’usine n’est pas prise en charge.

#### <a name="pkcs-certificates"></a>Certificats PKCS

Les certificats PKCS ne sont pas pris en charge sur macOS.

