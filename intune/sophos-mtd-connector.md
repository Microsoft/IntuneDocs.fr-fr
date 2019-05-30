---
title: Configurer l’intégration de Sophos Mobile à Intune
titleSuffix: Intune on Azure
description: Découvrez comment configurer la solution Sophos Mobile avec Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4363bb4feba52c15b8918a7c6ea02fa2917a00de
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044944"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Connecteur Sophos Mobile Threat Defense avec Intune
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise grâce à l’accès conditionnel basé sur une analyse des risques menée par Sophos Mobile, une solution de défense contre les menaces mobiles qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies sur les appareils exécutant l’application Sophos Mobile.
Vous pouvez configurer des stratégies d’accès conditionnel qui s’appuient sur l’analyse des risques de Sophos Mobile par le biais de stratégies de conformité des appareils Intune, et les utiliser pour autoriser les appareils non conformes à accéder aux ressources de l’entreprise ou les en empêcher en fonction des menaces détectées.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Comment Intune et Sophos Mobile aident-ils à protéger les ressources de votre entreprise ?
L’application Sophos Mobile pour Android et iOS capture le système de fichiers, la pile réseau, l’appareil et les données de télémétrie des applications quand elles sont disponibles, puis les envoie au service cloud Sophos Mobile pour évaluer les risques de l’appareil face aux menaces mobiles.
La stratégie de conformité des appareils Intune comporte une règle pour Sophos Mobile Threat Defense, qui s’appuie sur l’analyse des risques de Sophos Mobile. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée. Si l’appareil est détecté comme non conforme, les utilisateurs ne peuvent pas accéder aux ressources de l’entreprise comme Exchange Online et SharePoint Online. Les utilisateurs reçoivent aussi des conseils de l’application Sophos Mobile installée sur leurs appareils pour résoudre le problème et rétablir l’accès aux ressources de l’entreprise.  

## <a name="sample-scenarios"></a>Exemples de scénario
Voici quelques scénarios courants.  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes
Quand des applications malveillantes telles que des programmes malveillants sont détectés sur des appareils, vous pouvez bloquer les actions suivantes sur ces appareils jusqu’à ce que la menace soit écartée :
- Connexion à la messagerie de l’entreprise
- Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work
- Accès aux applications d’entreprise

**Blocage quand des applications malveillantes sont détectées** :
 
![Image conceptuelle d’applications malveillantes détectées](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**Accès accordé après correction** :  
![Image conceptuelle de l’accès accordé après correction](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau  
Détectez les menaces pour votre réseau, comme les attaques de l’intercepteur (« Man-in-the-middle »), et protégez l’accès aux réseaux Wi-Fi en fonction du risque évalué pour l’appareil.  

**Bloquer l’accès au réseau via le Wi-Fi** :  
![Bloquer l’accès au réseau via le Wi-Fi](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**Accès accordé après correction** :   
![Accès accordé après correction](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau  
Détectez les menaces pour votre réseau, comme les attaques de l’intercepteur, et empêchez la synchronisation des fichiers d’entreprise en fonction du risque évalué pour l’appareil.  

**Bloquer SharePoint Online quand des menaces réseau sont détectées** :   
![Bloquer SharePoint Online quand des menaces réseau sont détectées](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**Accès accordé après correction** :  
![Accès accordé après correction pour un exemple Sharepoint](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>Plateformes prises en charge  
- Android 5.0 et ultérieur
- iOS 11.0 et versions ultérieures

## <a name="prerequisites"></a>Prérequis  
- Azure Active Directory Premium
- Abonnement Microsoft Intune 
- Abonnement Sophos Mobile Threat Defense

Pour plus d’informations, consultez le [site web de Sophos](https://www.sophos.com/products/mobile-control).  

## <a name="next-steps"></a>Étapes suivantes  
- [Intégrer Sophos avec Intune](sophos-mtd-connector-integration.md)
- [Configurer les applications Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Créer une stratégie de conformité des appareils Sophos](mtd-device-compliance-policy-create.md)
- [Activer le connecteur MTD Sophos](mtd-connector-enable.md)
