---
title: Effacer un appareil macOS
titleSuffix: Microsoft Intune
description: Découvrez comment effacer toutes les données, y compris le système d’exploitation, d’un appareil macOS.
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
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 446c88dabb070c42e47e2bb2d2ac87d6acecdedc
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781948"
---
# <a name="erase-all-data-from-a-macos-device"></a>Effacer toutes les données d’un appareil macOS

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez effacer toutes les données d’un appareil macOS, y compris le système d’exploitation. L’appareil dans ce cas n’est plus géré par Intune. Aucun avertissement n’est envoyé à l’utilisateur final.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil que vous voulez effacer.
2. Cliquez sur **Plus** > **Effacer** > fournissez un nombre à 6 chiffres pour le **Code PIN de récupération**. Il s’agit du code PIN que vous devez donner à l’utilisateur pour qu’il puisse réinstaller le système d’exploitation sur son appareil. Notez ce code PIN quelque part, car vous ne le verrez plus une fois l’action d’effacement effectuée.
![Capture d’écran](./media/device-erase/providepin.png)
3. Cliquez sur **OK** pour effacer l’appareil.
