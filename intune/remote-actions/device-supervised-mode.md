---
title: Activer le mode supervisé iOS avec Microsoft Intune
titleSuffix: ''
description: Découvrez comment activer le mode supervisé iOS avec Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99f27992009332a2a5fae0768225d8c69d3ac5ad
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509399"
---
# <a name="turn-on-ios-supervised-mode"></a>Activer le mode supervisé iOS


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Le mode supervisé Apple iOS donne aux administrateurs des options supplémentaires pour gérer les appareils Apple, ce qui peut s’avérer utile dans les déploiements à grande échelle d’appareils d’entreprise. Par exemple, vous pouvez restreindre AirDrop ou empêcher les utilisateurs de changer le nom de l’appareil. Pour obtenir la liste des paramètres qui nécessitent le mode supervisé, consultez [Paramètres de restriction des appareils iOS dans Intune](../configuration/device-restrictions-ios.md).

Intune prend en charge le mode supervisé dans le cadre du [Programme d’inscription des appareils (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) Apple.

Pour obtenir la liste des contrôle Apple nécessitant une supervision, consultez la [Référence en matière de réglages de données utiles](http://help.apple.com/configurator/mac/2.4/#/cad5370d089).

## <a name="turn-on-supervised-mode-during-enrollment"></a>Activer le mode supervisé à l’inscription

Dans Intune, vous pouvez activer le mode supervisé pour des appareils quand vous [créez un profil d’inscription Apple dans DEP](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Sous **Paramètres de gestion des appareils**, cochez la case **Supervisé**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Activer le mode supervisé après l’inscription

Après l’inscription, la seule façon d’activer le mode supervisé est de connecter l’appareil iOS à un Mac et [d’utiliser Apple Configurator](../enrollment/apple-configurator-enroll-ios.md) (qui réinitialise l’appareil). Vous ne pouvez pas configurer un appareil pour le mode supervisé dans Intune après l’inscription.

## <a name="identify-a-supervised-device"></a>Identifier un appareil supervisé

Pour déterminer si un appareil est supervisé, consultez l’écran de verrouillage ou la page **À propos de** :
- Sur l’écran de verrouillage de l’appareil, vous avez la mention **Cet iPhone est géré par « Nom de l’entreprise ».**
- Dans la page **À propos de** de l’appareil, vous avez la mention **Cet iPhone est supervisé. Nom de l’entreprise peut surveiller votre trafic Internet et localiser cet appareil.**

## <a name="next-steps"></a>Étapes suivantes

Pour connaître les autres options de gestion des appareils, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md)
