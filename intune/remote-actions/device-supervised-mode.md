---
title: Activation du mode supervisé iOS/iPadOS avec Microsoft Intune
titleSuffix: ''
description: Découvrez comment activer le mode supervisé iOS/iPadOS avec Intune.
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
ms.openlocfilehash: 0d266dbc9fa72b1579e05e7798315e2e718a9797
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413661"
---
# <a name="turn-on-iosipados-supervised-mode"></a>Activation du mode iOS/iPadOS supervisé


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Le mode supervisé Apple iOS/iPadOS donne aux administrateurs des options supplémentaires pour gérer les appareils Apple, ce qui peut s’avérer utile dans les déploiements à grande échelle d’appareils détenus par l’entreprise. Par exemple, vous pouvez restreindre AirDrop ou empêcher les utilisateurs de changer le nom de l’appareil. Pour obtenir la liste des paramètres qui nécessitent le mode supervisé, consultez [Paramètres de restriction des appareils iOS dans Intune](../configuration/device-restrictions-ios.md).

Intune prend en charge le mode supervisé dans le cadre du [Programme d’inscription des appareils (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) Apple.

Pour obtenir la liste des contrôle Apple nécessitant une supervision, consultez la [Référence en matière de réglages de données utiles](http://help.apple.com/configurator/mac/2.4/#/cad5370d089).

## <a name="turn-on-supervised-mode-during-enrollment"></a>Activer le mode supervisé à l’inscription

Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), vous pouvez activer le mode supervisé des appareils quand vous [créez un profil d’inscription Apple dans le programme DEP](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Sous **Paramètres de gestion des appareils**, cochez la case **Supervisé**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Activer le mode supervisé après l’inscription

Après l’inscription, la seule façon d’activer le mode supervisé est de connecter l’appareil iOS/iPadOS à un Mac et [d’utiliser Apple Configurator](../enrollment/apple-configurator-enroll-ios.md) (qui réinitialise l’appareil). Vous ne pouvez pas configurer un appareil pour le mode supervisé dans Intune après l’inscription.

## <a name="identify-a-supervised-device"></a>Identifier un appareil supervisé

Pour déterminer si un appareil est supervisé, consultez l’écran de verrouillage ou la page **À propos de** :
- Sur l’écran de verrouillage de l’appareil, vous avez la mention **Cet iPhone est géré par « Nom de l’entreprise ».**
- Dans la page **À propos de** de l’appareil, vous avez la mention **Cet iPhone est supervisé. Nom de l’entreprise peut surveiller votre trafic Internet et localiser cet appareil.**

## <a name="next-steps"></a>Étapes suivantes

Pour connaître les autres options de gestion des appareils, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md)
