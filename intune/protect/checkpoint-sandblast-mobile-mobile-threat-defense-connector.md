---
title: Configurer Check Point SandBlast MTD
titleSuffix: Microsoft Intune
description: Découvrez-en plus sur l’intégration d’Intune à Check Point SandBlast Mobile Threat Defense pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c1d6620c120a3102803c84270ac1880c6904320
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504715"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Connecteur de protection contre les menaces mobiles Check Point SandBlast Mobile avec Intune

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Check Point SandBlast Mobile, solution de protection contre les menaces mobiles qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant l’application Check Point SandBlast Mobile.

Vous pouvez configurer des stratégies d’accès conditionnel basées sur l’évaluation des risques de Check Point SandBlast Mobile par le biais des stratégies de conformité d’appareil Intune et les utiliser pour autoriser ou empêcher les appareils non conformes d’accéder aux ressources de l’entreprise en fonction des menaces détectées.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>Comment Intune et Check Point SandBlast Mobile vous aident-ils à protéger les ressources de votre entreprise ?

L’application Check Point SandBlast Mobile pour Android et iOS capture le système de fichiers, la pile réseau, les données de télémétrie de l’appareil et des applications quand elles sont disponibles, puis les envoie au service cloud Check Point SandBlast pour évaluer les risques de l’appareil face aux menaces mobiles.

La stratégie de conformité des appareils Intune comprend une règle de protection contre les menaces mobiles Check Point SandBlast Mobile, qui est basée sur l’évaluation des risques Check Point SandBlast. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée. Si l’appareil est détecté comme non conforme, les utilisateurs ne peuvent pas accéder aux ressources de l’entreprise comme Exchange Online et SharePoint Online. Les utilisateurs reçoivent aussi des conseils de l’application mobile Check Point SandBlast installée sur leurs appareils pour résoudre le problème et rétablir l’accès aux ressources de l’entreprise.

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

Voici quelques scénarios courants :

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes

Lorsque des applications malveillantes, des logiciels malveillants par exemple, sont détectées sur des appareils, vous pouvez bloquer ces appareils jusqu'à ce que la menace soit écartée :

- Connexion à la messagerie de l’entreprise

- Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work

- Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Blocage de Check Point MTD quand des applications malveillantes sont détectées](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-2.PNG)

**Accès accordé après correction :**

![Accès accordé à Check Point MTD](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et protégez l’accès aux réseaux Wi-Fi compte tenu du risque de l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Blocage par Check Point MTD de l’accès réseau via le Wi-Fi](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-4.PNG)

**Accès accordé après correction :**

![Accès Wi-Fi accordé par Check Point MTD](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et empêchez la synchronisation des fichiers d’entreprise compte tenu du risque de l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Blocage par Check Point MTD de l’accès à SharePoint Online](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-6.PNG)

**Accès accordé après correction :**

![Accès à SharePoint Online accordé par Check Point MTD](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>Plateformes prises en charge

- **Android 4.1 et versions ultérieures**

- **iOS 8 et versions ultérieures**

## <a name="pre-requisites"></a>Conditions préalables

- Azure Active Directory Premium

- Abonnement Microsoft Intune

- Abonnement Check Point SandBlast Mobile Threat Defense
  - Pour plus d’informations, consultez le [site web de CheckPoint SandBlast](https://www.checkpoint.com/).

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer Check Point SandBlast à Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Configurer l’application Check Point SandBlast Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Créer une stratégie de conformité d’appareil CheckPoint SandBlast Mobile](mtd-device-compliance-policy-create.md)

- [Activer le connecteur MTD de CheckPoint SandBlast Mobile](mtd-connector-enable.md)
