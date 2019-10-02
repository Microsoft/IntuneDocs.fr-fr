---
title: Supprimer un utilisateur d’un appareil iOS avec Microsoft Intune
titleSuffix: ''
description: Découvrez comment supprimer un utilisateur d’un appareil iOS partagé avec Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f418149d8640f7fd663f0bbf4b3151ffb428a75e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728479"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Supprimer un utilisateur d’un appareil iOS partagé


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action **Supprimer l’utilisateur** supprime un utilisateur que vous sélectionnez dans le cache local sur un iPad partagé. L’iPad doit être configuré pour gérer l’application iOS Classroom à l’aide d’un [profil Éducation iOS](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Non prise en charge
- Windows Phone - Non prise en charge
- iOS - Prise en charge d’iOS 9.3 et ultérieur (appareils iPad partagés uniquement)
- macOS - Non prise en charge
- Android - Non prise en charge

## <a name="remove-a-user"></a>Supprimer un utilisateur

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Appareils**.
4. Dans le volet **Appareils**, sélectionnez **Tous les appareils**.
5. Dans la liste des appareils que vous gérez, sélectionnez un appareil iOS.
6. Dans le volet de l’appareil, sélectionnez **Utilisateurs**.
7. Dans la liste, cliquez avec le bouton droit sur l’utilisateur que vous souhaitez supprimer, puis sélectionnez **Supprimer l’utilisateur**.

## <a name="next-steps"></a>Étapes suivantes

- Pour consulter l’état de l’action **Supprimer l’utilisateur**, sélectionnez **Appareils** > **Actions de l’appareil**.
