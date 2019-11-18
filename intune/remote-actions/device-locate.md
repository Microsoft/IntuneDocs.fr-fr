---
title: Rechercher des appareils iOS perdus avec Microsoft Intune - Azure | Microsoft Docs
description: Recherchez les appareils iOS perdus ou volés à l’aide de l’option Localiser l’appareil dans Microsoft Intune. Obtenez également plus d’informations sur la sécurité et les informations de confidentialité lors de l’utilisation de l’action Localiser l’appareil.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 817f46558932c074abc37b45d2885496419a0db0
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712428"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Localiser des appareils iOS perdus ou volés avec Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pour obtenir l’emplacement d’un appareil iOS perdu ou volé sur une carte, utilisez l’action **Localiser l’appareil**. L’appareil doit être en mode supervisé. Avant d’utiliser cette action, veillez à ce que l’appareil soit en [mode Perdu](device-lost-mode.md).

## <a name="supported-platforms"></a>Plateformes prises en charge

- iOS 9.3 et version ultérieure

Cette fonctionnalité n’est pas prise en charge pour les systèmes suivants : 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Localiser un appareil perdu ou volé

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Sélectionnez **Appareils**, puis **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, choisissez un appareil iOS, puis **...Plus**. Ensuite, choisissez l’action à distance **Localiser l’appareil**.
5. Une fois que l’appareil est localisé, son emplacement s’affiche dans **Localiser l’appareil**.
    ![Capture d’écran de localisation de l’appareil à l’aide d’Intune dans Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Activer l’alerte sonore sur un appareil iOS en mode de perte

Si quelqu’un a perdu son appareil iOS 9.3 ou un appareil plus récent, vous pouvez le déclencher à distance pour qu’il émette un son d’alerte qui permettra à l’utilisateur de le retrouver. L’appareil doit être en [mode de perte](device-lost-mode.md).

Dans le [Intune dans le portail Azure](https://aka.ms/intuneportal), choisissez **Appareils** > **Tous les appareils** > sélectionnez un appareil iOS > **Vue d’ensemble**  >  **Plus** > **Émettre un son en mode de perte (superviser uniquement)** .

Le son est émis jusqu’à ce que l’utilisateur désactive le son sur l’appareil, ou jusqu’à ce que l’appareil soit supprimé du mode de perte.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Informations de sécurité et de confidentialité pour les actions Mode Perdu et Localiser l’appareil
- Aucune information sur l’emplacement de l’appareil n’est envoyée à Intune tant que vous n’activez pas cette action.
- Quand vous utilisez l’action Localiser l’appareil, les coordonnées de latitude et de longitude de l’appareil peuvent être récupérées avec l’API Graph.
- Les données sont stockées pendant 24 heures avant d’être supprimées. Vous ne pouvez pas supprimer manuellement les données d’emplacement.
- Les données d’emplacement sont chiffrées aussi bien pendant leur stockage que leur transmission.
- Quand vous configurez le mode Perdu, vous pouvez personnaliser un message qui s’affiche sur l’écran de verrouillage. Afin d’aider la personne qui trouve l’appareil, veillez à inclure dans le message des détails spécifiques pour retourner l’appareil perdu.

## <a name="next-steps"></a>Étapes suivantes

Pour afficher l’état d’activation de la fonction Localiser l’appareil, ouvrez **Appareils**, puis sélectionnez **Actions de l’appareil**.
