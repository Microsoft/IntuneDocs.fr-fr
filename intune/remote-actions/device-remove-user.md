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
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713161"
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

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Tous les appareils**.
3. Dans la liste des appareils que vous gérez, sélectionnez un appareil iOS.
4. Dans le volet de l’appareil, sélectionnez **Utilisateurs**.
5. Dans la liste, cliquez avec le bouton droit sur l’utilisateur que vous souhaitez supprimer, puis sélectionnez **Supprimer l’utilisateur**.

## <a name="next-steps"></a>Étapes suivantes

- Pour consulter l’état de l’action **Supprimer l’utilisateur**, sélectionnez **Appareils** > **Actions de l’appareil**.
