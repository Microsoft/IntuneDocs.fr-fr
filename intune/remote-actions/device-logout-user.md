---
title: Déconnecter l’utilisateur d’un appareil iOS
titleSuffix: Microsoft Intune
description: Découvrez comment déconnecter l’utilisateur actuel d’un appareil iOS avec Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8336f5b29cd21bb6875285177071542080eb95f3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509459"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Déconnecter l’utilisateur actuel sur les appareils iOS gérés par Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action **Déconnecter l’utilisateur actuel** déconnecte l’utilisateur actuel d’un appareil iPad partagé. 

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Non prise en charge
- Windows Phone - Non prise en charge
- iOS - Prise en charge d’iOS 9.3 et ultérieur (appareils iPad partagés uniquement)
- macOS - Non prise en charge
- Android - Non prise en charge

## <a name="how-to-log-out-the-current-user"></a>Guide pratique pour déconnecter l’utilisateur actuel

1. Connectez-vous au portail Azure.
2. Choisissez **Autres services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Appareils**.
4. Dans le panneau **Appareils et groupes**, choisissez **Tous les appareils**.
5. Dans la liste des appareils que vous gérez, choisissez un appareil iOS, puis choisissez l’action à distance **Déconnecter l’utilisateur actuel**.

## <a name="next-steps"></a>Étapes suivantes

Pour connaître l’état de l’action que vous venez d’effectuer, allez dans le panneau **Appareils et groupes**, et choisissez **Actions d’appareil**.
