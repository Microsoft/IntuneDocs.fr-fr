---
title: "Gérer des appareils avec Intune"
titleSuffix: Intune on Azure
description: "Découvrez comment afficher les appareils que vous gérez avec Intune et effectuer diverses opérations dessus."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Qu’est-ce que la gestion des appareils Microsoft Intune ?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La charge de travail **Appareils** vous donne des informations sur les appareils que vous gérez et vous permet de procéder à des tâches à distance sur ces appareils. Pour accéder à la charge de travail :

1. Connectez-vous au portail Azure.
2. Choisissez **Autres services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Appareils**.
4. Vous pouvez à présent effectuer les actions de l’appareil à distance répertoriées. Les actions disponibles varient selon la plateforme et la configuration de l’appareil :

## <a name="available-device-actions"></a>Actions d’appareils disponibles

- [Afficher l’inventaire des appareils](device-inventory.md)
- Effectuez les actions d’appareil à distance :
    - [Supprimer les données d’entreprise](device-company-data-remove.md) 
    - [Réinitialisation aux paramètres d’usine](device-factory-reset.md)
    - [Verrouillage à distance](device-remote-lock.md)
    - [Réinitialiser le code secret](device-passcode-reset.md)
    - [Contourner le verrou d’activation](device-activation-lock-bypass.md)
    - [Redémarrage à zéro](device-fresh-start.md)
    - [Mode Perdu](device-lost-mode.md)
    - [Localiser l’appareil](device-locate.md)
    - [Redémarrer](device-restart.md)
    - [Réinitialisation du code PIN Windows 10](device-windows-pin-reset.md)
    - [Contrôle à distance pour Android](device-profile-android-teamviewer.md)
    - [Synchroniser l’appareil](device-sync.md)


## <a name="next-steps"></a>Étapes suivantes

- Choisissez **Actions de l’appareil** pour connaître l’état des actions effectuées sur les appareils que vous gérez. 
![Surveiller les actions des appareils](./media/monitor-device-actions.png)
