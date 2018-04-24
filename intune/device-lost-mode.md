---
title: Activer le mode Perdu iOS avec Microsoft Intune - Azure | Microsoft Docs
description: Activez ou démarrez le mode Perdu pour personnaliser un message qui s’affiche sur l’écran de verrouillage d’un appareil iOS perdu ou volé à l’aide de Microsoft Intune. Obtenez également plus d’informations sur la sécurité et les informations de confidentialité lors de l’utilisation de l’action mode Perdu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 070256ce5267189731c3565f4332a3bd57c326f5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Activer le mode Perdu sur des appareils iOS avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L’action d’appareil **Mode Perdu** vous permet d’activer le mode Perdu sur les appareils iOS perdus ou volés. Ce mode vous permet d’entrer un message et un numéro de téléphone qui s’affichent sur l’écran de verrouillage de l’appareil. Pour utiliser le mode Perdu, l’appareil doit être un appareil iOS en mode supervisé.

## <a name="supported-platforms"></a>Plateformes prises en charge

- iOS 9.3 et version ultérieure

Cette fonctionnalité n’est pas prise en charge pour : 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Activer le mode Perdu

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Appareils**, puis **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, choisissez un appareil iOS, puis **...Plus**. Ensuite, choisissez l’action à distance **Mode Perdu**.
5. En **Mode Perdu**, activez cette fonctionnalité. Entrez ensuite le message à afficher et le numéro de téléphone du contact.
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