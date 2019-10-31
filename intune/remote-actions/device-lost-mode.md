---
title: Activer le mode Perdu iOS avec Microsoft Intune - Azure | Microsoft Docs
description: Activez ou démarrez le mode Perdu pour personnaliser un message qui s’affiche sur l’écran de verrouillage d’un appareil iOS perdu ou volé à l’aide de Microsoft Intune. Obtenez également plus d’informations sur la sécurité et les informations de confidentialité lors de l’utilisation de l’action mode Perdu.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34a4c8adeef7e8b28c90ad38579f0f9ac7c4784d
ms.sourcegitcommit: 807ab3e35f4d9ffa18655410b7d61e5e772ab348
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73057521"
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Activer le mode Perdu sur des appareils iOS avec Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’action d’appareil **Mode Perdu** vous permet d’activer le mode Perdu sur les appareils iOS perdus ou volés. Ce mode vous permet d’entrer un message et un numéro de téléphone qui s’affichent sur l’écran de verrouillage de l’appareil. Pour utiliser le mode Perdu, l’appareil doit être un appareil iOS en mode supervisé.

## <a name="supported-platforms"></a>Plateformes prises en charge

- iOS 9.3 et version ultérieure

Cette fonctionnalité n’est pas prise en charge pour : 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Activer le mode Perdu

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Sélectionnez **Appareils**, puis **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, choisissez un appareil iOS, puis choisissez l’action **Mode perdu (supervisé uniquement)** .
5. Sous **Mode perdu**, sélectionnez **Activer**.
6. Dans **Message à afficher sur l’écran de verrouillage**, tapez un message à afficher sur l’écran de verrouillage de l’appareil.
7. Si vous le souhaitez, entrez un numéro de téléphone dans la zone **Numéro de téléphone à afficher**.
6. Cliquez sur **OK** pour enregistrer vos modifications.

Lorsque vous activez le mode Perdu, vous bloquez toute utilisation de l’appareil. L’utilisateur final ne peut pas accéder à l’appareil tant que vous n’avez pas désactivé le mode Perdu. Quand le mode Perdu est activé, utilisez l’action [Localiser l’appareil](device-locate.md) pour rechercher l’emplacement de l’appareil.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informations de sécurité et de confidentialité pour le mode Perdu et actions Localiser l’appareil
- Aucune information sur l’emplacement de l’appareil n’est envoyée à Intune tant que vous n’activez pas cette action.
- Quand vous utilisez l’action Localiser l’appareil, les coordonnées de latitude et de longitude de l’appareil sont envoyées à Intune et affichées dans le portail Azure.
- Les données sont stockées pendant 24 heures avant d’être supprimées. Vous ne pouvez pas supprimer manuellement les données d’emplacement.
- Les données d’emplacement sont chiffrées aussi bien pendant leur stockage que leur transmission.
- Dans le message entré à afficher sur l’écran de verrouillage, veillez à inclure des détails spécifiques pour retourner l’appareil perdu.

## <a name="next-steps"></a>Étapes suivantes

Pour afficher l’état de l’activation du mode Perdu, ouvrez **Appareils**, puis sélectionnez **Actions de l’appareil**.
