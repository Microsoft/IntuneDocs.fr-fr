---
title: Effectuer une mise à niveau vers Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Découvrir comment mettre à niveau les appareils exécutant Windows Holographique vers Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c268785e3cce7477203e78f321af15c5067d51ae
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041749"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Mettre à niveau les appareils exécutant Windows Holographique vers Windows Holographic for Business

Microsoft Intune comporte de nombreux paramètres permettant de gérer et de protéger les appareils. Cet article liste et décrit les paramètres servant à mettre à niveau des appareils Windows Holographic vers Windows Holographic for Business. Ces paramètres sont créés dans un profil de configuration de mise à niveau dans Intune, qui est envoyé (push) ou déployé sur les appareils.

Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour mettre à niveau vos appareils Windows Holographic. En ce qui concerne Microsoft HoloLens, vous pouvez acheter Commercial Suite pour obtenir la licence nécessaire à la mise à niveau. Pour plus d’informations, consultez [Déverrouiller les fonctionnalités de Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise).

Pour plus d’informations sur cette fonctionnalité, voir [Mettre à niveau les éditions Windows 10 ou activer le mode S](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Mise à niveau d’édition

- **Édition vers laquelle la mise à niveau est effectuée** : sélectionnez **Windows 10 Holographic for Business**.
- **Fichier de licence** : recherchez et sélectionnez le fichier de licence XML qui vous a été fourni.

  ![Entrer le nom du fichier XML comportant les informations de licence Holographic for Business](media/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il peut ne rien faire pour le moment. [Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

Vous pouvez également créer des profils de mise à niveau d’édition pour les appareils [Windows 10 (et versions ultérieures)](edition-upgrade-windows-settings.md).
