---
title: Gérer les appareils avec Microsoft Intune - Azure | Microsoft Docs
description: Passez en revue les appareils que vous gérez avec Microsoft Intune, notamment l’exportation d’une liste d’appareils au format csv, affichez vos appareils joints à Azure Active Directory, consultez un journal des modifications des actions sur l’appareil, utilisez le connecteur TeamViewer pour autoriser les administrateurs informatiques à résoudre à distance les problèmes liés aux appareils Android et consultez toutes les actions que vous pouvez exécuter sur vos appareils.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 8ae7a15f623b82cabed5314c4770c2edef902414
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253559"
---
# <a name="what-is-microsoft-intune-device-management"></a>Qu’est-ce que la gestion des appareils Microsoft Intune ?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En tant qu’administrateur informatique, vous devez vous assurer que les appareils gérés fournissent les ressources dont vos utilisateurs ont besoin pour effectuer leur travail, tout en protégeant les données contre les risques.

La charge de travail **Appareils** vous donne des informations sur les appareils que vous gérez et vous permet de procéder à des tâches à distance sur ces appareils.

## <a name="get-to-your-devices"></a>Accéder à vos appareils

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Appareils**. Cette vue montre des informations détaillées sur les différents appareils, et ce que vous pouvez faire avec eux, notamment les informations suivantes :

   - **Vue d’ensemble** affiche un aperçu des appareils inscrits et indique également le nombre d’appareils qui utilisent les différentes plateformes, dont Android et iOS.
   - **Tous les appareils** montre la liste des appareils inscrits que vous gérez.

     Utilisez la fonctionnalité **Exporter** pour créer une liste .csv de tous les appareils, par incréments de 10 000 (Internet Explorer) ou 30 000 (Edge, Chrome).

     Sélectionnez un appareil pour [voir plus d’informations sur cet appareil](device-inventory.md), dont les détails sur le matériel, les applications installées et son état de stratégie de conformité.

   - **Appareils Azure AD** montre les appareils inscrits ou joints à Azure Active Directory (Azure AD). Découvrez plus d’informations sur la [gestion des appareils dans Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Actions des appareils** inclut un historique des actions à distance exécutées sur les différents appareils, notamment l’action, son état, la personne qui a lancé l’action et l’heure.

     ![Capture d’écran de la surveillance des actions des appareils](./media/monitor-device-actions.png)

   - Les **journaux d’audit** recensent les activités qui génèrent un changement dans Intune. Les [Journaux d’audit](monitor-audit-logs.md) fournissent plus de détails.
   - Le **connecteur TeamViewer** est un service TeamViewer qui permet aux utilisateurs d’appareils Android gérés par Intune d’obtenir une assistance à distance auprès de leur administrateur informatique. Découvrez plus d’informations sur [TeamViewer](device-profile-android-teamviewer.md).
   - **Aide et support** fournit un accès direct à des conseils de dépannage et aux fonctionnalités de demande d’assistance ou de vérification de l’état d’Intune.

## <a name="available-device-actions"></a>Actions d’appareils disponibles
Les actions disponibles varient selon la plateforme et la configuration de l’appareil.

- [Afficher l’inventaire des appareils](device-inventory.md)
- Exécutez les actions d’appareil à distance :
    - [Mettre hors service](devices-wipe.md#retire)
    - [Réinitialisation](devices-wipe.md#wipe)
    - [Verrouillage à distance](device-remote-lock.md)
    - [Réinitialiser le code secret](device-passcode-reset.md)
    - [Contourner le verrouillage d’activation](device-activation-lock-bypass.md) (iOS uniquement)
    - [Redémarrage à zéro](device-fresh-start.md) (Windows uniquement)
    - [Mode Perdu](device-lost-mode.md) (iOS uniquement)
    - [Localiser l’appareil](device-locate.md) (iOS uniquement)
    - [Redémarrer](device-restart.md) (Windows uniquement)
    - [Réinitialisation du code PIN Windows 10](device-windows-pin-reset.md)
    - [Contrôle à distance pour Android](device-profile-android-teamviewer.md)
    - [Synchroniser l’appareil](device-sync.md)

## <a name="next-steps"></a>Étapes suivantes

- Dans **Tous les appareils**, sélectionnez un appareil pour voir plus de détails à son sujet.
- Choisissez **Actions de l’appareil** pour connaître l’état des actions effectuées sur les appareils que vous gérez.
