---
title: Créer une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Intune
titleSuffix: Microsoft Intune
description: Créez une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: 48dc7de86965741d8ed42bd5a5f29f72ae66d4f3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188493"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Créer une stratégie de protection d’applications Mobile Threat Defense avec Intune

Intune avec Mobile Threat Defense (MTD) vous aide à détecter les menaces et à évaluer les risques sur les appareils mobiles. Vous pouvez créer une stratégie de protection d’applications Intune qui évaluera les risques pour déterminer si l’appareil sera autorisé à accéder aux données d’entreprise.


> [!NOTE]
> Cet article s’applique à tous les partenaires Mobile Threat Defense qui prennent en charge des stratégies de protection d’applications :
>
> - Better Mobile (Android)
> - Zimperium (iOS)
> - Lookout for Work (Android, iOS).

## <a name="before-you-begin"></a>Avant de commencer

Dans le cadre de l’installation de MTD, dans la console de partenaire MTD, vous avez créé une stratégie qui classe les diverses menaces d’après leur gravité : élevée, moyenne et faible. Vous devez maintenant définir le niveau Mobile Threat Defense dans la stratégie de protection d’applications Intune.

Prérequis pour la stratégie de protection d’applications avec MTD :

- Configurez l’intégration de MTD avec Intune. Sans cette intégration, la stratégie de protection d’applications MTD n’aura aucun effet.

## <a name="to-create-an-mtd-app-protection-policy"></a>Pour créer une stratégie de protection d’applications MTD

Utilisez la procédure pour [créer une stratégie de protection d’application pour iOS/iPados ou Android](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps) et utilisez les informations suivantes dans les pages *Applications*, *Lancement conditionnel* et *Affectations* :

- **Applications** : sélectionnez l’application pour le partenaire Mobile Threat Defense que vous utilisez.
- **Lancement conditionnel** :  Sous *Conditions de l’appareil*, utilisez la zone de liste déroulante pour sélectionner **Niveau de menace maximal autorisé pour l’appareil**.

  Options pour la **valeur** du niveau de menace :

  - **Sécurisé** : ce niveau est le plus sûr. L'appareil ne peut pas avoir de menace présente et continuer à accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.
  - **Faible** : l’appareil est conforme seulement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.
  - **Élevé** : ce niveau est le moins sûr. Cela active tous les niveaux de menace et utilise la défense contre les menaces mobiles uniquement à des fins de création de rapport. L’application MTD doit être activée avec ce paramètre sur les appareils.

  Options pour l’**action** :

  - **Bloquer l’accès**
  - **Réinitialiser les données**

- **Affectations** : attribuez la stratégie à des groupes d’utilisateurs.  Les appareils utilisés par les membres du groupe sont évalués concernant l’accès aux données d’entreprise sur les applications ciblées via la protection des applications Intune.


## <a name="next-steps"></a>Étapes suivantes  

- Découvrez plus en détail [Mobile Threat Defense](~/protect/mobile-threat-defense.md) dans Microsoft Intune.
