---
title: Réinitialiser des appareils Windows 10 avec Microsoft Intune - Azure | Microsoft Docs
description: Utilisez Redémarrage à zéro pour supprimer ou désinstaller des applications sur des PC Windows 10 à l’aide de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e48b7dac5064f9daeb62e141a4c1b2a4adf11b7
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782191"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utiliser Fresh Start pour réinitialiser les appareils Windows 10 avec Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action d’appareil **Redémarrage à zéro** supprime toutes les applications installées sur un PC Windows 10 (version 1703 ou ultérieure). Elle permet de supprimer les applications préinstallées (OEM) qui sont généralement installées avec un nouveau PC. 

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) et sélectionnez **Appareils** > **Tous les appareils**.
2. Dans la liste des appareils que vous gérez, choisissez un appareil de bureau Windows 10.
3. Cliquez sur **Redémarrage à zéro**. 
4. Sélectionnez **Conserver les données utilisateur sur cet appareil** pour que :
   * l’appareil reste joint à Azure AD ;
   * L’appareil est de nouveau inscrit dans la gestion des appareils mobiles quand un annuaire Azure Active Directory a activé la connexion d’un utilisateur à l’appareil.
   * le contenu du dossier de base de l’utilisateur de l’appareil soit conservé, et les applications et les paramètres supprimés.

  > [!IMPORTANT]
 > Si vous ne conservez pas les données de l'utilisateur, l'appareil sera restauré à l'état terminé par défaut OOBE (out-of-box experience) en conservant le compte administrateur intégré.
 > Les appareils BYOD seront désinscrits d’Azure AD et de la gestion des appareils mobiles.
 > Les appareils joints à Azure AD seront de nouveau inscrits dans la gestion des appareils mobiles quand un annuaire Azure Active Directory aura activé la connexion d’un utilisateur à l’appareil.
 
5. Cliquez sur **OK**.   
6. Pour afficher l’état de cette action, revenez à **Appareils** et cliquez sur **Actions d’appareil**.  
7. L'appareil sera restauré à l'écran de connexion initial.
