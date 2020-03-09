---
title: Synchroniser des appareils avec Microsoft Intune - Azure | Microsoft Docs
description: Synchronisez des appareils qui sont inscrits ou gérés avec Microsoft Intune afin d’obtenir les stratégies et les actions les plus récentes. Inclut les étapes permettant de synchroniser à l’aide du portail Azure et répertorie les codes d’erreur qui peuvent être retentée.
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
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee3020c2a1dfadb21b55ca29a2295498bf893080
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781966"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Synchroniser des appareils pour obtenir les stratégies et les actions les plus récentes avec Intune


L’action d’appareil **Synchroniser** force l’appareil sélectionné à s’enregistrer immédiatement auprès d’Intune. Quand un appareil s’enregistre, il reçoit immédiatement les actions ou les stratégies en attente qui lui ont été affectées. Cette fonctionnalité peut vous aider à valider et dépanner immédiatement les stratégies que vous avez assignées, sans attendre la prochaine vérification planifiée.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Synchroniser un appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). 
3. Sélectionnez **Appareils** > **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, sélectionnez un appareil pour ouvrir son volet *Vue d’ensemble*, puis sélectionnez **Synchroniser**.
5. Pour confirmer, sélectionnez **Oui**.

Pour voir l’état de l’action de synchronisation, choisissez **Appareils** > **Superviser** > **Actions de l’appareil**.

Vous pouvez trouver les fréquences d’archivage standard des stratégies Intune dans [Durées de cycle d’actualisation](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retryable-error-codes"></a>Codes d’erreur renouvelable

Quand un administrateur exécute l’action d’appareil **Synchroniser**, les applications iOS/iPadOS et Android qui ont rencontré un échec et généré un code d’erreur avec nouvelle tentative possible sont toujours disponibles sur l’appareil. Cependant, les applications qui ont généré un code d’erreur non renouvelable doivent attendre sept jours avant d’être à nouveau disponibles sur l’appareil.


| Code d'erreur  | Description suggérée | Renouvelable |
|---|---|---|
| 2016330898 | Une erreur inconnue s'est produite. | Non |
| 2016330897 | Votre connexion à Intune a expiré. Réinitialisez votre connexion. | Oui |
| 2016330896 | Vous avez perdu la connexion à Internet. Réinitialisez votre connexion. | Oui |
| 2016330895 | Vous avez perdu la connexion à Internet. Réinitialisez votre connexion. | Oui |
| 2016330894 | Vous avez perdu la connexion à Internet. Réinitialisez votre connexion. | Oui |
| 2016330893 | Vous avez perdu la connexion à Internet. Réinitialisez votre connexion. | Oui|
| 2016330892 | L’itinérance internationale est désactivée. | Non|
| 2016330891 | La connexion de données mobiles pour cet appareil n’est pas accessible pendant un appel téléphonique. Attendez la fin de l’appel téléphonique. | Oui|
| 2016330890 | Réseau mobile pour cet appareil. Ces appareils ne peut pas être utilisés pour l’instant. | Non|
| 2016330889 | Échec de la connexion sécurisée. Réinitialisez votre connexion. | Oui|
| 2016330888 | Échec de l’évaluation de la confiance du serveur. | Non|

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez [consulter les informations](device-inventory.md) de l’appareil.
 
