---
title: Connecteur Pradeo Mobile Threat Defense avec Intune
titleSuffix: Intune on Azure
description: Découvrez-en plus sur l’intégration d’Intune avec le connecteur Pradeo Mobile Threat Defense pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1e881886a060646af700fa7affe4b65b5685087
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726893"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Connecteur Pradeo Mobile Threat Defense avec Intune

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Pradeo, une solution MTD qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant l’application Pradeo.

Vous pouvez configurer des stratégies d’accès conditionnel basées sur l’évaluation des risques de Pradeo par le biais des stratégies de conformité des appareils Intune, et les utiliser pour autoriser ou empêcher les appareils non conformes d’accéder aux ressources de l’entreprise en fonction des menaces détectées.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Comment Intune et Pradeo aident-ils à protéger les ressources de votre entreprise ?

L’application Pradeo pour Android et iOS capture le système de fichiers, la pile réseau, l’appareil et les données de télémétrie des applications quand elles sont disponibles, puis les envoie au service cloud Pradeo pour évaluer les risques de l’appareil face aux menaces mobiles.

La stratégie de conformité des appareils Intune inclut une règle pour Pradeo Mobile Threat Defense, basée sur l’évaluation des risques Pradeo. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée. Si l’appareil est détecté comme non conforme, les utilisateurs ne peuvent pas accéder aux ressources de l’entreprise comme Exchange Online et SharePoint Online. Les utilisateurs reçoivent aussi des conseils de l’application Pradeo installée sur leurs appareils pour résoudre le problème et rétablir l’accès aux ressources de l’entreprise.

## <a name="sample-scenarios"></a>Exemples de scénario

Voici quelques scénarios courants.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes

Quand des applications malveillantes telles que des programmes malveillants sont détectés sur des appareils, vous pouvez bloquer les actions suivantes sur ces appareils jusqu’à ce que la menace soit écartée :

- Connexion à la messagerie de l’entreprise

- Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work

- Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Image conceptuelle d’applications malveillantes détectées](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_blocked.png)

**Accès accordé après correction :**

![Applications malveillantes détectées et accès accordé](./media/pradeo-mobile-threat-defense-connector/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau

Détectez les menaces pour votre réseau, comme les **attaques de l’intercepteur (« Man-in-the-middle »)** , et protégez l’accès aux réseaux Wi-Fi en fonction du risque évalué pour l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Bloquer l’accès au réseau via le Wi-Fi](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_blocked.png)

**Accès accordé après correction :**

![Image conceptuelle de l’accès accordé après correction](./media/pradeo-mobile-threat-defense-connector/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces pour votre réseau, comme les **attaques de l’intercepteur**, et empêchez la synchronisation des fichiers d’entreprise en fonction du risque évalué pour l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Bloquer SharePoint Online lorsque des menaces réseau sont détectées](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_blocked.png)

**Accès accordé après correction :**

![Image conceptuelle de l’accès accordé après correction pour un exemple Sharepoint](./media/pradeo-mobile-threat-defense-connector/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plateformes prises en charge

- **Android 4.0.3 et versions ultérieures**

- **iOS 7 et versions ultérieures**

## <a name="prerequisites"></a>Prérequis

- Azure Active Directory Premium

- Abonnement Microsoft Intune

- Abonnement Pradeo Mobile pour Mobile Threat Defense

  - Pour plus d’informations, consultez le [site web Pradeo](https://www.pradeo.com/en-US/mobile-threat-protection).

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer Pradeo à Intune](pradeo-mtd-connector-integration.md)

- [Configurer les applications Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Créer une stratégie de conformité des appareils Pradeo](mtd-device-compliance-policy-create.md)

- [Activer le connecteur MTD Pradeo](mtd-connector-enable.md)
