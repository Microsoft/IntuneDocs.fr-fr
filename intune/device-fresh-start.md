---
title: Réinitialiser des appareils Windows 10 avec Microsoft Intune - Azure | Microsoft Docs
description: Utilisez Redémarrage à zéro pour supprimer ou désinstaller des applications sur des PC Windows 10 à l’aide de Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b66cd00f734cab3ca85f6d87f056f8c482a377d
ms.sourcegitcommit: 2811df0f851ca6b08f6ae8c926fb2e6971c41690
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251731"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Utiliser Fresh Start pour réinitialiser les appareils Windows 10 avec Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L’action d’appareil **Redémarrage à zéro** supprime toutes les applications installées sur un PC Windows 10 (version 1703 ou ultérieure). Elle permet de supprimer les applications préinstallées (OEM) qui sont généralement installées avec un nouveau PC.  

1. Connectez-vous au [Portail Azure](https://portal.azure.com) et accédez à > **Microsoft Intune** > **Appareils** > **Tous les appareils**.
2. Dans la liste des appareils que vous gérez, choisissez un appareil de bureau Windows 10.
3. Cliquez sur **Redémarrage à zéro**. 
4. Sélectionnez **Conserver les données utilisateur sur cet appareil** pour que :
   * l’appareil reste joint à Azure AD ;
    * l’appareil reste inscrit à la gestion des appareils mobiles ; 
    * le contenu du dossier de base de l’utilisateur de l’appareil soit conservé, et les applications et les paramètres supprimés.  
  > [!IMPORTANT]
 > Si vous ne conservez pas les données utilisateur, l’appareil sera restauré à son état d’origine. Il sera désinscrit d’Azure AD et de la gestion des appareils mobiles. 
 
5. Cliquez sur **OK**.   
6. Pour afficher l’état de cette action, revenez à **Appareils** et cliquez sur **Actions d’appareil**.  
