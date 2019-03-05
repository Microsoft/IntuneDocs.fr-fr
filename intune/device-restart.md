---
title: Redémarrer des appareils avec Microsoft Intune - Azure | Microsoft Docs
description: Redémarrez des appareils iOS et Windows à l’aide de Microsoft Intune dans le portail Azure à l’aide de l’action de redémarrage à distance.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc9cc03c5ca0243d41990e1aeab1d9bf4a707de8
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229715"
---
# <a name="remotely-restart-devices-with-intune"></a>Redémarrer à distance des appareils avec Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L’action d’appareil **Redémarrer** entraîne le redémarrage de l’appareil que vous choisissez. Le propriétaire de l’appareil n’est pas automatiquement informé du redémarrage et risque de perdre son travail.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Prise en charge de Windows 8.1 et ultérieur
- Windows Phone - Prise en charge de Windows Phone 8.1 et ultérieur
- Appareils kiosque Android - Prise en charge sur Android 7.0 et ultérieur
- iOS - Prise en charge

    > [!Note]  
    > Cette commande nécessite un appareil supervisé et le droit d’accès **Verrouillage de l’appareil**. L’appareil redémarre immédiatement. Les appareils iOS verrouillés avec un code secret ne rejoignent pas de réseau Wi-Fi après un redémarrage. Après le redémarrage, l’appareil risque de ne pas pouvoir communiquer avec le serveur.
- macOS - Non prise en charge
- Appareils Android et profils professionnels Android - Pas de prise en charge

## <a name="restart-a-device"></a>Redémarrer un appareil

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Appareils** > **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, sélectionnez un appareil, sélectionnez **Plus**, puis l’action à distance **Redémarrer**.

## <a name="next-steps"></a>Étapes suivantes

- Pour consulter l’état de l’action d’appareil **Redémarrer**, sélectionnez **Appareils** > **Actions de l’appareil**.
