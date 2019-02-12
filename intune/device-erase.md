---
title: Effacer un appareil macOS
titleSuffix: Microsoft Intune
description: Découvrez comment effacer toutes les données, y compris le système d’exploitation, d’un appareil macOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 92fd3b9ac83ba5b279fb234fb82242138f1405af
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839173"
---
# <a name="erase-all-data-from-a-macos-device"></a>Effacer toutes les données d’un appareil macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez effacer toutes les données d’un appareil macOS, y compris le système d’exploitation. L’appareil dans ce cas n’est plus géré par Intune. Aucun avertissement n’est envoyé à l’utilisateur final.

1. Dans [le portail Azure d’Intune](https://aka.ms/intuneportal), choisissez **Appareils** > **Tous les appareils**, puis choisissez l’appareil à effacer.
![Capture d’écran](./media/device-erase/choosedevice.png)
2. Cliquez sur **Plus** > **Effacer** > fournissez un nombre à 6 chiffres pour le **Code PIN de récupération**. Il s’agit du code PIN que vous devez donner à l’utilisateur pour qu’il puisse réinstaller le système d’exploitation sur son appareil. Notez ce code PIN quelque part, car vous ne le verrez plus une fois l’action d’effacement effectuée.
![Capture d’écran](./media/device-erase/providepin.png)
3. Cliquez sur **OK** pour effacer l’appareil.
