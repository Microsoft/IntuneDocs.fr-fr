---
title: Gérer les appareils avec Microsoft Intune - Azure | Microsoft Docs
description: Passez en revue les appareils que vous gérez avec Microsoft Intune, notamment l’exportation d’une liste d’appareils au format csv, affichez vos appareils joints à Azure Active Directory, consultez un journal des modifications des actions sur l’appareil, utilisez le connecteur TeamViewer pour autoriser les administrateurs informatiques à résoudre à distance les problèmes liés aux appareils Android et consultez toutes les actions que vous pouvez exécuter sur vos appareils.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b780f22fd6823499128a3975f1812a1d1f7c032b
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413785"
---
# <a name="what-is-microsoft-intune-device-management"></a>Qu’est-ce que la gestion des appareils Microsoft Intune ?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En tant qu’administrateur informatique, vous devez vous assurer que les appareils gérés fournissent les ressources dont vos utilisateurs ont besoin pour effectuer leur travail, tout en protégeant les données contre les risques.

La charge de travail **Appareils** vous donne des informations sur les appareils que vous gérez et vous permet de procéder à des tâches à distance sur ces appareils.

## <a name="get-to-your-devices"></a>Accéder à vos appareils

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Sélectionnez **Appareils**. Cette vue montre des informations détaillées sur les différents appareils, et ce que vous pouvez faire avec eux, notamment les informations suivantes :

   - La **Vue d’ensemble** présente un aperçu visuel des appareils inscrits et indique également combien d’appareils utilisent les différentes plateformes, notamment Android et iOS/iPadOS.
   - **Tous les appareils** montre la liste des appareils inscrits que vous gérez.

     Utilisez la fonctionnalité **Exporter** pour créer une liste .csv de tous les appareils, par incréments de 10 000 (Internet Explorer) ou 30 000 (Microsoft Edge, Chrome).

     Sélectionnez un appareil pour [voir plus d’informations sur cet appareil](device-inventory.md), dont les détails sur le matériel, les applications installées et son état de stratégie de conformité.

   - **Appareils Azure AD** montre les appareils inscrits ou joints à Azure Active Directory (Azure AD). Découvrez plus d’informations sur la [gestion des appareils dans Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Actions des appareils** inclut un historique des actions à distance exécutées sur les différents appareils, notamment l’action, son état, la personne qui a lancé l’action et l’heure.

     ![Capture d’écran de la surveillance des actions des appareils](./media/device-management/monitor-device-actions.png)

   - Les **journaux d’audit** recensent les activités qui génèrent un changement dans Intune. Les [Journaux d’audit](../fundamentals/monitor-audit-logs.md) fournissent plus de détails.
   - Le **connecteur TeamViewer** est un service TeamViewer qui permet aux utilisateurs d’appareils Android gérés par Intune d’obtenir une assistance à distance auprès de leur administrateur informatique. Découvrez plus d’informations sur [TeamViewer](teamviewer-support.md).
   - **Aide et support** fournit un accès direct à des conseils de dépannage et aux fonctionnalités de demande d’assistance ou de vérification de l’état d’Intune.

## <a name="available-device-actions"></a>Actions d’appareils disponibles
Les actions disponibles varient selon la plateforme et la configuration de l’appareil.

- [Afficher l’inventaire des appareils](device-inventory.md)
- Exécutez les actions d’appareil à distance :
  - [Mettre hors service](devices-wipe.md#retire)
  - [Réinitialisation](devices-wipe.md#wipe)
  - [Verrouillage à distance](device-remote-lock.md)
  - [Réinitialiser le code secret](device-passcode-reset.md)
  - [Désactiver le verrouillage d’activation](device-activation-lock-bypass.md) (iOS uniquement)
  - [Redémarrage à zéro](device-fresh-start.md) (Windows uniquement)
  - [Mode Perdu](device-lost-mode.md) (iOS uniquement)
  - [Localiser l’appareil](device-locate.md) (iOS uniquement)
  - [Redémarrer](device-restart.md) (Windows uniquement)
  - [Réinitialisation du code PIN Windows 10](device-windows-pin-reset.md)
  - [Contrôle à distance pour Android](teamviewer-support.md)
  - [Synchroniser l’appareil](device-sync.md)
  - [Renommer un appareil](device-rename.md)
  - [Envoyer des notifications personnalisées](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, iOS/iPadOS)
  - [Rotation de clés BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (Windows uniquement)

## <a name="next-steps"></a>Étapes suivantes

- Dans **Tous les appareils**, sélectionnez un appareil pour voir plus de détails à son sujet.
- Choisissez **Actions de l’appareil** pour connaître l’état des actions effectuées sur les appareils que vous gérez.
