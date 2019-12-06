---
title: Supprimer des certificats SCEP ou PKCS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Les administrateurs peuvent utiliser l’action de réinitialisation ou de mise hors service pour supprimer des certificats de Microsoft Intune. Il existe certains scénarios où les certificats sont automatiquement supprimés, tels que la désinscription d’un appareil ou la suppression d’une stratégie de conformité. Dans d’autres scénarios, les certificats restent automatiquement sur l’appareil, par exemple quand la licence Intune est perdue ou supprimée. Consultez les différentes procédures pour les appareils Android, Android Entreprise, iOS, macOS et Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: dbf6d95c8902a95993b972ff7639d4afb4324ac8
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410173"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Supprimer des certificats SCEP et PKCS dans Microsoft Intune

Dans Microsoft Intune, vous pouvez utiliser des certificats SCEP (Simple Certificate Enrollment Protocol) et des profils de certificat PKCS (Public Key Cryptography Standards) pour ajouter des certificats à des appareils.

Vous pouvez supprimer ces certificats quand vous [réinitialisez](../remote-actions/devices-wipe.md#wipe) ou [mettez hors service](../remote-actions/devices-wipe.md#retire) l’appareil. Il existe également des scénarios où les certificats sont automatiquement supprimés et d’autres encore où les certificats restent sur l’appareil. Cet article liste quelques scénarios courants et leur impact sur les certificats PKCS et SCEP.

> [!NOTE]
> Pour supprimer et révoquer des certificats pour un utilisateur qui est supprimé du service Azure AD (Azure Active Directory) ou Active Directory local, effectuez les étapes suivantes dans l’ordre :
>
> 1. Réinitialiser ou mettre hors service l’appareil de l’utilisateur.
> 2. Supprimer l’utilisateur du service Azure AD ou Active Directory local.

## <a name="manually-deleted-certificates"></a>Supprimer manuellement des certificats

La suppression manuelle d'un certificat est un scénario qui s'applique à toutes les plateformes et à tous les certificats fournis par les modèles de certificats SCEP ou PKCS. Par exemple, un utilisateur peut supprimer un certificat d'un appareil lorsque cet appareil reste ciblé par une stratégie de certificat.

Dans ce scénario, après la suppression du certificat, la prochaine fois que l’appareil se connecte avec Intune, il est considéré comme non conforme car il lui manque le certificat attendu. Intune émet alors un nouveau certificat pour rétablir la conformité de l'appareil. Aucune autre action n'est nécessaire pour restaurer le certificat.

## <a name="windows-devices"></a>Appareils Windows

### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).
- L’appareil est supprimé d’un groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat SCEP est révoqué quand :

- Un administrateur change ou met à jour le profil SCEP.

Un certificat racine est supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :

- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

### <a name="pkcs-certificates"></a>Certificats PKCS

Un certificat PKCS est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Un certificat racine est supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Les certificats PKCS *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :

- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil PKCS.
- Un profil de certificat est supprimé de l’affectation de groupe.


## <a name="ios-devices"></a>Périphériques iOS

### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).
- L’appareil est supprimé du groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat SCEP est révoqué quand :

- Un administrateur change ou met à jour le profil SCEP.

Un certificat racine est supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :

- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

### <a name="pkcs-certificates"></a>Certificats PKCS

Un certificat PKCS est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Un certificat PKCS est supprimé quand :

- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat racine est supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Les certificats PKCS *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :

- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil PKCS.

## <a name="android-knox-devices"></a>Appareils Android Knox

### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).

Un certificat SCEP est révoqué quand :

- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).
- L’appareil est supprimé d’un groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil SCEP.

Un certificat racine est supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :

- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

### <a name="pkcs-certificates"></a>Certificats PKCS

Un certificat PKCS est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Un certificat racine est supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe).
- Un administrateur exécute l’action de [mise hors service](../remote-actions/devices-wipe.md#retire).

Les certificats PKCS *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :
- Un utilisateur perd la licence Intune.

- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.
- Un administrateur change ou met à jour le profil PKCS.
- Un profil de certificat est supprimé de l’affectation de groupe.


> [!NOTE]
> Les scénarios précédents ne s’appliquent pas aux appareils Android for Work.
> Les appareils Android d’ancienne génération (tous les appareils autres que Samsung, avec un profil non professionnel) ne sont pas activés pour la suppression de certificat.

## <a name="macos-certificates"></a>Certificats macOS

### <a name="scep-certificates"></a>Certificats SCEP

Un certificat SCEP est révoqué *et* supprimé quand :

- Un utilisateur se désinscrit.
- Un administrateur exécute une action de [mise hors service](../remote-actions/devices-wipe.md#retire).
- L’appareil est supprimé d’un groupe Azure AD.
- Un profil de certificat est supprimé de l’affectation de groupe.

Un certificat SCEP est révoqué quand :

- Un administrateur change ou met à jour le profil SCEP.

Les certificats SCEP *restent* sur l’appareil (ils ne sont pas révoqués ni supprimés) quand :

- Un utilisateur perd la licence Intune.
- Un administrateur retire la licence Intune.
- Un administrateur supprime l’utilisateur ou le groupe d’Azure AD.

> [!NOTE]
> L’utilisation de l’action de [réinitialisation](../remote-actions/devices-wipe.md#wipe) pour réinitialiser des appareils macOS aux paramètres d’usine n’est pas prise en charge.

### <a name="pkcs-certificates"></a>Certificats PKCS

Les certificats PKCS ne sont pas pris en charge sur macOS.

## <a name="next-steps"></a>Étapes suivantes

[Utiliser des certificats pour l’authentification](certificates-configure.md)