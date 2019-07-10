---
title: Guide de migration de la gestion des appareils mobiles Intune
titleSuffix: Microsoft Intune
description: Ce guide vous présente des informations détaillées sur la migration à partir d’un fournisseur MDM tiers vers Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b34143e17245de61026a536cc0b8c5e8a7f80107
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549396"
---
# <a name="intune-migration-guide"></a>Guide de migration Intune

![Image du guide de migration de MDM Microsoft Intune](./media/MDM-migration-guide-art.PNG)

Pour réussir votre migration vers Microsoft Intune, vous devez d’abord élaborer un plan robuste prenant en compte votre environnement actuel de gestion des appareils mobiles (MDM), les objectifs commerciaux et les critères techniques. De plus, vous devez inclure les parties prenantes qui prendront en charge et participeront à votre plan de migration.

Ce guide vous présente des informations détaillées sur la migration à partir d’un fournisseur MDM tiers vers Intune.

## <a name="whats-included-in-this-guide"></a>Que contient ce guide ?

Ce guide divise la migration en deux phases comprenant des tâches, des stratégies et des conseils tactiques destinés à faciliter le processus de migration de bout en bout vers Intune MDM.

- [Phase 1 : Préparation de Microsoft Intune à la gestion des appareils mobiles](migration-guide-prepare.md)

    - [Évaluer les besoins concernant la migration de MDM](migration-guide-prepare.md#assess-mdm-requirements)

    - [Configuration de base](migration-guide-setup.md)

    - [Configurer les stratégies de gestion des appareils mobiles et des applications](migration-guide-configure-policies.md)

    - [Configurer les stratégies de protection des applications](migration-guide-app-protection-policies.md)

    - [Facteurs de migration spécifiques à prendre en compte](migration-guide-considerations.md)

- [Phase 2 : Campagne de migration](migration-guide-campaign.md)

    - [Plan de communication](migration-guide-communication-plan.md)

    - [Encourager l’adoption par les utilisateurs finaux avec l’accès conditionnel](migration-guide-drive-adoption.md)

    - [Cycle de migration classique](migration-guide-cycle.md)
        - [Surveillance de la migration](migration-guide-cycle.md#monitoring-migration)
        - [Tâches de post-migration](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Hypothèses

- Vous avez déjà évalué Intune dans un environnement de preuve de concept et avez décidé de l’utiliser comme solution MDM dans votre organisation.

- Vous êtes déjà familiarisé avec Intune et ses fonctionnalités.

## <a name="before-you-begin"></a>Avant de commencer

Il est important de savoir que votre nouveau déploiement Microsoft Intune peut être différent de l’ancien déploiement MDM. Contrairement aux services MDM traditionnels, Intune se concentre sur le contrôle d’accès basé sur les identités. Pour cette raison, il ne nécessite aucune appliance de proxy réseau pour contrôler l’accès aux données de l’entreprise depuis des appareils mobiles situés en dehors du périmètre réseau de l’organisation. Microsoft propose des solutions permettant de sécuriser les services de données dans le cloud lui-même, par le biais d’une suite de services cloud étroitement intégrés, regroupés au sein de l’offre Enterprise Client + Security.

- Consultez les [utilisations courantes d’Intune](common-scenarios.md).

## <a name="next-steps"></a>Étapes suivantes

[Phase 1 : Préparation de Microsoft Intune à la gestion des appareils mobiles](migration-guide-prepare.md)
