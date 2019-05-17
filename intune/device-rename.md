---
title: Renommer un appareil Windows avec Microsoft Intune - Azure | Microsoft Docs
description: Renommez un appareil Windows à l’aide de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567099"
---
# <a name="rename-a-windows-device-in-intune"></a>Renommer un appareil Windows dans Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L’action **Renommer un appareil** vous permet de renommer un appareil Windows d’entreprise qui est inscrit dans Intune. Le nom de l’appareil est modifié dans Intune et sur l’appareil. 

Cette fonctionnalité ne prend actuellement pas en charge le renommage des appareils Azure AD Windows hybrides.

## <a name="rename-a-device"></a>Renommer un appareil

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services**, filtrez sur **Intune**, puis choisissez **Microsoft Intune**.
3. Choisissez **Appareils** > **Tous les appareils** > choisissez un appareil Windows > **Plus** > **Renommer un appareil**.
4. Dans le panneau **Renommer un appareil**, saisissez le nouveau nom dans la zone de texte. Vous pouvez utiliser des lettres, des chiffres et des traits d’union. Le nom doit contenir au moins une lettre ou un trait d’union.
5. Si vous souhaitez redémarrer l’appareil après l’avoir renommé, choisissez **Oui** en regard de **Redémarrer après le renommage**.
6. Choisissez **Renommer**.



## <a name="next-steps"></a>Étapes suivantes

Pour connaître l’état de l’action d’appareil **Renommer**, consultez la page **Vue d’ensemble** de l’appareil.
