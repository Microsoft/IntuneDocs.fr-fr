---
title: Redémarrer des appareils avec Microsoft Intune - Azure | Microsoft Docs
description: Redémarrez des appareils Windows et iOS/iPadOS avec Microsoft Intune sur le Portail Azure à l’aide de l’action Redémarrer à distance.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54fa0f796e96a2487793197cbbbe548fd8490856
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415612"
---
# <a name="remotely-restart-devices-with-intune"></a>Redémarrer à distance des appareils avec Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action d’appareil **Redémarrer** entraîne le redémarrage de l’appareil que vous choisissez (dans les 5 minutes). Le propriétaire de l’appareil n’est pas automatiquement informé du redémarrage et risque de perdre son travail.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Prise en charge de Windows 8.1 et ultérieur
- Windows Phone - Prise en charge de Windows Phone 8.1 et ultérieur
- Appareils kiosque Android - Prise en charge sur Android 7.0 et ultérieur
- iOS/iPadOS – Prise en charge

    > [!Note]  
    > Cette commande nécessite un appareil supervisé et le droit d’accès **Verrouillage de l’appareil**. L’appareil redémarre immédiatement. Les appareils iOS/iPadOS verrouillés par un code secret ne rejoignent pas de réseau Wi-Fi après redémarrage. Après le redémarrage, l’appareil risque de ne pas pouvoir communiquer avec le serveur.
- macOS - Non prise en charge
- Appareils Android et profils professionnels Android - Pas de prise en charge

## <a name="restart-a-device"></a>Redémarrer un appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Sélectionnez **Appareils** > **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, sélectionnez un appareil > **Redémarrer** > **Oui**.

## <a name="next-steps"></a>Étapes suivantes

- Pour consulter l’état de l’action d’appareil **Redémarrer**, sélectionnez **Appareils** > **Actions de l’appareil**.
