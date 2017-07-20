---
title: Connecteur Skycure avec Intune
titleSuffix: Intune on Azure
description: "Intégration du connecteur Skycure à Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2a7c15cf695fd88ba5961611c78ecc28a29238af
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Connecteur Skycure Mobile Threat Defense

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Skycure, une solution de protection contre les menaces mobiles qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant Skycure, notamment :

-   Défense physique

-   Défense du réseau

-   Défense des applications

-   Défense contre les vulnérabilités

Vous pouvez configurer des stratégies d’accès conditionnel basées sur l’évaluation des risques Skycure par le biais des stratégies de conformité d’appareil Intune, permettant d’autoriser ou d’empêcher des appareils non conformes d’accéder aux ressources de l’entreprise en fonction des menaces détectées.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Comment Intune et Skycure aident-ils à protéger les ressources de votre entreprise ?

L’application mobile Skycure pour Android ou iOS capture le système de fichiers, la pile réseau, les appareils et les données de télémétrie de l’application lorsqu’elles sont disponibles, puis les envoie au service cloud Skycure pour évaluer les risques de l’appareil face aux menaces mobiles.

La stratégie de conformité d’appareil Intune inclut une règle pour Skycure Mobile Threat Defense, basée sur l’évaluation des risques Skycure. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée.

Si l’appareil est détecté non conforme, l’accès aux ressources comme Exchange Online et SharePoint Online est bloqué. Les utilisateurs d’appareils bloqués reçoivent de l’aide à partir de l’application mobile Skycure pour résoudre le problème et récupérer l’accès aux ressources de l’entreprise.

Intune prend en charge deux modes d’intégration avec Skycure :

-   **Configuration de base** : un mode en lecture seule qui permet à Skycure d’identifier les appareils dans Intune.

-   **Intégration complète** : qui permet à Skycure de transmettre à Intune des informations sur les incidents de sécurité et les risques de l’appareil.

## <a name="sample-scenarios"></a>Exemples de scénario

Voici quelques scénarios courants :

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes

Lorsque des applications malveillantes, des logiciels malveillants par exemple, sont détectées sur des appareils, vous pouvez bloquer ces appareils jusqu'à ce que la menace soit écartée :

-   Connexion à la messagerie de l’entreprise

-   Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work

-   Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Applications malveillantes détectées](./media/skycure-arch-1.png)

**Accès accordé après correction :**

![Applications malveillantes détectées et accès accordé](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et protégez l’accès aux réseaux Wi-Fi compte tenu du risque de l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Bloquer l’accès au réseau via le Wi-Fi](./media/skycure-arch-3.png)

**Accès accordé après correction :**

![Accès accordé après correction](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et empêchez la synchronisation des fichiers d’entreprise compte tenu du risque de l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Bloquer SharePoint Online lorsque des menaces réseau sont détectées](./media/skycure-arch-5.png)

**Accès accordé après correction :**

![Accès accordé après correction pour un exemple Sharepoint](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>Plateformes prises en charge

-   **Android 4.1 et versions ultérieures**

-   **iOS 8 et versions ultérieures**

## <a name="pre-requisites"></a>Conditions préalables

-   Azure Active Directory Premium

-   Abonnement Microsoft Intune

-   Abonnement Skycure Mobile Threat Defense

Pour plus d'informations, consultez le [site web Skycure](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Étapes suivantes

Voici les étapes que vous devez effectuer pour intégrer Intune à Skycure :

1.  [Ajouter et affecter des applications Skycure, Microsoft Authenticator et une stratégie de configuration d’application iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)

2.  [Configurer l’intégration de Skycure à Intune](skycure-mtd-connector-integration.md)

3.  [Activer le connecteur Skycure MTD dans Intune](mtd-connector-enable.md)

4.  [Créer une stratégie de conformité des appareils Skycure avec Intune](mtd-device-compliance-policy-create.md)
