---
title: "Réinitialiser un code d’accès d’appareil avec Intune"
titlesuffix: Azure portal
description: "Comment réinitialiser le code d’accès sur les appareils que vous gérez avec Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3defec3624944918d14b9c4527487c368c487dd6
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>Réinitialiser le code d’accès sur les appareils gérés par Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L’action **Réinitialiser le code secret** génère un nouveau code pour l’appareil qui est affiché dans le panneau <*Nom de l’appareil*> **Vue d’ensemble**.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Non prise en charge
- Windows Phone - Prise en charge de Windows Phone 8.1 à Windows 10 Creators Update (non joint à Azure AD), et de Windows 10 Creators Update et ultérieur
- iOS - Prise en charge
- macOS - Non prise en charge
- Android - Prise en charge des versions d’Android antérieures à Android 7. Android for Work n’est pas pris en charge.

## <a name="how-to-reset-a-passcode"></a>Comment réinitialiser un code secret

1. Connectez-vous au portail Azure.
2. Choisissez **Autres services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Appareils**.
4. Dans le panneau **Appareils et groupes**, choisissez **Tous les appareils**.
5. Dans la liste des appareils que vous gérez, choisissez un appareil, puis choisissez l’action à distance d’appareil **Réinitialiser le code d’accès**.

## <a name="next-steps"></a>Étapes suivantes

Pour connaître l’état de l’action que vous venez d’effectuer, allez dans le panneau **Appareils et groupes**, et choisissez **Actions d’appareil**.
