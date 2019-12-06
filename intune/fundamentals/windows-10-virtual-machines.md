---
title: Utilisation de machines virtuelles Windows 10 avec Microsoft Intune
titleSuffix: ''
description: Instructions pour l’utilisation de machines virtuelles Windows 10 avec Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afaf2c8a63bfaed1fdb593baf42c8fa258d7893
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74263115"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Utilisation de machines virtuelles Windows 10 avec Intune

Intune prend en charge la gestion des machines virtuelles exécutant Windows 10 Entreprise avec certaines limitations. La gestion Intune ne dépend pas ou interfère avec la gestion Windows Virtual Desktop de la même machine virtuelle.

Lorsque vous gérez des machines virtuelles Windows 10 avec Intune, gardez les points suivants à l’esprit :

## <a name="enrollment"></a>Inscription
- Nous vous déconseillons de gérer des machines virtuelles hôtes de session et à la demande avec Intune. Chaque machine virtuelle doit être inscrite au moment de sa création. En outre, la suppression régulière de machines virtuelles laissera des enregistrements d’appareil orphelins dans Intune jusqu’à ce qu’ils soient [nettoyés](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules). 
- Le mode de déploiement automatique de Windows Autopilot n’est pas pris en charge, car il requiert un module de plateforme sécurisée (TPM). 
- L’inscription OOBE (Out-of-Box Experience) n’est pas prise en charge sur les machines virtuelles qui ne sont accessibles qu’à l’aide du protocole RDP (comme les machines virtuelles hébergées sur Azure). Cette restriction signifie ce qui suit :
    - Windows Autopilot et les OOBE commerciales ne sont pas pris en charge.
    - Les options de page d’état d’inscription pour les stratégies de contexte d’appareil ne sont pas prises en charge.

## <a name="configuration"></a>Configuration
Intune ne prend en charge aucune configuration qui utilise un module de plateforme sécurisée (TPM) ou une gestion matérielle, notamment :
- [Paramètres de BitLocker](../configuration/device-profiles.md#endpoint-protection)
- [Paramètres d’interface de configuration du microprogramme d’appareil](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>Rapports
Intune détecte automatiquement les machines virtuelles et les signale comme « Machine virtuelle » dans le champ **Appareils** > **Tous les appareils** > Choisissez un appareil > **Vue d’ensemble** > **Modèle**. 

Les machines virtuelles libérées peuvent contribuer à des rapports d’appareils non conformes, car elles ne parviennent pas à [s’enregistrer auprès du service Intune](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retirement"></a>Mise hors service
Si vous ne disposez que d’un accès RDP, n’utilisez pas l’[action de réinitialisation](../remote-actions/devices-wipe.md#wipe). L’action de réinitialisation supprime les paramètres RDP de la machine virtuelle et vous empêche de vous reconnecter.


