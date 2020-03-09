---
title: Créer une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Intune
titleSuffix: Microsoft Intune
description: Créez une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 900858d9c437f2d2662260ca62534a987446d2b2
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782132"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Créer une stratégie de protection d’applications Mobile Threat Defense avec Intune

Intune avec Mobile Threat Defense (MTD) vous aide à détecter les menaces et à évaluer les risques sur les appareils mobiles. Vous pouvez créer une stratégie de protection d’applications Intune qui évaluera les risques pour déterminer si l’appareil sera autorisé à accéder aux données d’entreprise.

> [!NOTE]
> Cet article s’applique à tous les partenaires Mobile Threat Defense qui prennent en charge des stratégies de protection d’applications :
>
> - Better Mobile (Android, iOS/iPadOS)
> - Zimperium (Android, iOS/iPadOS)
> - Lookout for Work (Android, iOS/iPadOS).

## <a name="before-you-begin"></a>Avant de commencer

Dans le cadre de l’installation de MTD, dans la console de partenaire MTD, vous avez créé une stratégie qui classe les diverses menaces d’après leur gravité : élevée, moyenne et faible. Vous devez maintenant définir le niveau Mobile Threat Defense dans la stratégie de protection d’applications Intune.

Prérequis pour la stratégie de protection d’applications avec MTD :

- Configurez l’intégration de MTD avec Intune. Sans cette intégration, la stratégie de protection d’applications MTD n’aura aucun effet.

## <a name="to-create-an-mtd-app-protection-policy"></a>Pour créer une stratégie de protection d’applications MTD

Utilisez la procédure pour [créer une stratégie de protection d’application pour iOS/iPados ou Android](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps) et utilisez les informations suivantes dans les pages *Applications*, *Lancement conditionnel* et *Affectations* :

- **Applications** : Sélectionnez les applications que les stratégies de protection des applications doivent cibler. Pour cet ensemble de fonctionnalités, ces applications sont bloquées ou réinitialisées de manière sélective en fonction de l’évaluation des risques de l’appareil établie par le fournisseur Mobile Threat Defense que vous avez choisi.
- **Lancement conditionnel** :  Sous *Conditions de l’appareil*, utilisez la zone de liste déroulante pour sélectionner **Niveau de menace maximal autorisé pour l’appareil**.

  Options pour la **valeur** du niveau de menace :

  - **Sécurisé** : ce niveau est le plus sûr. L'appareil ne peut pas avoir de menace présente et continuer à accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.
  - **Faible** : l’appareil est conforme seulement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyenne** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.
  - **Élevée** : ce niveau est le moins sécurisé et autorise tous les niveaux de menace (Mobile Threat Defense est uniquement utilisé à des fins de création de rapport). L’application MTD doit être activée avec ce paramètre sur les appareils.

  Options pour l’**action** :

  - **Bloquer l’accès**
  - **Réinitialiser les données**

- **Affectations** : attribuez la stratégie à des groupes d’utilisateurs.  Les appareils utilisés par les membres du groupe sont évalués concernant l’accès aux données d’entreprise sur les applications ciblées via la protection des applications Intune.

## <a name="next-steps"></a>Étapes suivantes

- Découvrez plus en détail [Mobile Threat Defense](~/protect/mobile-threat-defense.md) dans Microsoft Intune.
