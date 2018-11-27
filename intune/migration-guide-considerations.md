---
title: Facteurs de migration spécifiques à prendre en compte
titlesuffix: Microsoft Intune
description: Cet article présente les facteurs de migration spécifiques à prendre en compte avant de lancer une campagne de migration vers Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 039b3dc4d45b340a7d7f8ed0314661a2505a779b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179814"
---
# <a name="special-migration-considerations"></a>Facteurs de migration spécifiques à prendre en compte

Selon l’environnement de votre fournisseur MDM existant, certains facteurs de migration spécifiques peuvent s’appliquer.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Réinitialiser pour le Programme d’inscription des appareils Apple (DEP)

Le programme Apple DEP définit des configurations d’appareil qui ne peuvent pas être supprimées par l’utilisateur final. Pour conserver les fonctionnalités de gestion avancée du programme DEP, vous devez restaurer l’état initial de l’appareil en le réinitialisant pour l’inscrire dans Intune.

Pour continuer à utiliser DEP pour gérer les appareils dans Intune, [configurez l’inscription des appareils iOS avec le programme d’inscription des appareils](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Étapes suivantes

[Phase 2 : Campagne de migration](migration-guide-campaign.md)
