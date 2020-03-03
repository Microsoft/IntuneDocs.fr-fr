---
title: Facteurs de migration spécifiques à prendre en compte
titleSuffix: Microsoft Intune
description: Cet article présente les facteurs de migration spécifiques à prendre en compte avant de lancer une campagne de migration vers Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 936e4836938ddddc8e795d85de5a449ee77edaa4
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514997"
---
# <a name="special-migration-considerations"></a>Facteurs de migration spécifiques à prendre en compte

Selon l’environnement de votre fournisseur MDM existant, certains facteurs de migration spécifiques peuvent s’appliquer.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Réinitialiser pour le Programme d’inscription des appareils Apple (DEP)

Le programme Apple DEP définit des configurations d’appareil qui ne peuvent pas être supprimées par l’utilisateur final. Pour conserver les fonctionnalités de gestion avancée du programme DEP, vous devez restaurer l’état initial de l’appareil en le réinitialisant pour l’inscrire dans Intune.

Pour continuer à utiliser DEP pour gérer les appareils dans Intune, [configurez l’inscription des appareils iOS/iPadOS avec le programme d’inscription des appareils](../enrollment/device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Étapes suivantes

[Phase 2 : Campagne de migration](../migration-guide-campaign.md)
