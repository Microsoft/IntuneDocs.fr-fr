---
title: Suppression d’un utilisateur d’un appareil iOS/iPadOS avec Microsoft Intune
titleSuffix: ''
description: Découvrez comment supprimer un utilisateur d’un appareil iOS/iPadOS partagé avec Intune.
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
ms.openlocfilehash: 8b6b2b3492b9edece6b69e4b302741c0443c0a3e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415570"
---
# <a name="remove-a-user-from-a-shared-iosipados-device"></a>Suppression d’un utilisateur d’un appareil iOS/iPadOS partagé


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action **Supprimer l’utilisateur** supprime un utilisateur que vous sélectionnez dans le cache local sur un iPad partagé. L’iPad doit être configuré de façon à gérer l’application iOS/iPadOS Classroom avec un [profil Enseignement iOS/iPadOS](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Non prise en charge
- Windows Phone - Non prise en charge
- iOS/iPadOS – Prise en charge sur la version 9.3 et les versions ultérieures d’iOS/iPadOS (appareils iPad partagés uniquement)
- macOS - Non prise en charge
- Android - Non prise en charge

## <a name="remove-a-user"></a>Supprimer un utilisateur

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Tous les appareils**.
3. Dans la liste des appareils que vous gérez, sélectionnez un appareil iOS/iPadOS.
4. Dans le volet de l’appareil, sélectionnez **Utilisateurs**.
5. Dans la liste, cliquez avec le bouton droit sur l’utilisateur que vous souhaitez supprimer, puis sélectionnez **Supprimer l’utilisateur**.

## <a name="next-steps"></a>Étapes suivantes

- Pour consulter l’état de l’action **Supprimer l’utilisateur**, sélectionnez **Appareils** > **Actions de l’appareil**.
