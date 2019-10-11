---
title: Renommer un appareil avec Microsoft Intune - Azure | Microsoft Docs
description: Renommez un appareil à l’aide de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35fae5ea1b3294772db4f4db51179892e08ed5d1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728505"
---
# <a name="rename-a-device-in-intune"></a>Renommer un appareil dans Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action **Renommer un appareil** vous permet de renommer un appareil inscrit dans Intune. Le nom de l’appareil est modifié dans Intune et sur l’appareil.

Vous pouvez renommer les types d’appareils suivants :
- Windows et appartenant à l’entreprise 
- Supervisé iOS
- macOS 10 et appartenant à l’entreprise

Cette fonctionnalité ne prend actuellement pas en charge le renommage des appareils Azure AD Windows hybrides.

## <a name="rename-a-device"></a>Renommer un appareil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Choisissez **Appareils** > **Tous les appareils** > choisissez un appareil > **Plus** > **Renommer un appareil**.
4. Dans le panneau **Renommer un appareil**, saisissez le nouveau nom dans la zone de texte. Vous pouvez utiliser des lettres, des chiffres et des traits d’union. Le nom doit contenir au moins une lettre ou un trait d’union.
5. Si vous souhaitez redémarrer l’appareil après l’avoir renommé, choisissez **Oui** en regard de **Redémarrer après le renommage**.
6. Choisissez **Renommer**.



## <a name="next-steps"></a>Étapes suivantes

Pour connaître l’état de l’action d’appareil **Renommer**, consultez la page **Vue d’ensemble** de l’appareil.
