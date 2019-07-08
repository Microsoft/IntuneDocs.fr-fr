---
title: Configurer Wandera Mobile Security avec Intune
titleSuffix: Intune on Azure
description: Découvrez comment configurer Wandera Mobile Security avec Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6219d4a176eebf81747461b3cc8b478e46e86898
ms.sourcegitcommit: 6bba9f2ef4d1ec699f5713a4da4f960e7317f1cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67407286"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Connecteur Wandera Mobile Threat Defense avec Intune  

Contrôlez l’accès des appareils mobiles aux ressources d’entreprise à l’aide d’un accès conditionnel et en fonction de l’évaluation des risques effectuée par Lookout. Wandera est une solution de protection contre les menaces mobiles (MTD) qui s'intègre à Microsoft Intune.  Le risque est évalué en fonction des données de télémétrie recueillies à partir des appareils par le service Wandera, notamment :
- Vulnérabilités du système d’exploitation
- Applications malveillantes installées
- Profils de réseau malveillants
- Cryptojacking

Vous pouvez configurer des stratégies *d’accès conditionnel* basées sur l’évaluation des risques de Wandera, activée par le biais des stratégies de conformité Intune. Une stratégie d’évaluation des risques autorise ou bloque l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>Comment Intune et Wandera Threat Defense aident-ils à protéger les ressources de votre entreprise ?  

L'application mobile Wandera s'installe de manière transparente à l'aide de Microsoft Intune. Cette application capture le système de fichiers, la pile réseau et les données de télémétrie des appareils et des applications (lorsque ces informations sont disponibles). Ces informations sont synchronisées avec le service cloud de Wandera afin d'évaluer le risque de menaces mobiles pour l'appareil. Ces classifications de niveau de risque sont configurables selon vos besoins dans RADAR, la console Wandera.

La stratégie de conformité d’Intune inclut une règle MTD basée sur l’évaluation des risques Wandera. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée.

Pour les appareils non conformes, l'accès aux ressources comme Office 365 peut être bloqué. Les utilisateurs d’appareils bloqués reçoivent de l’aide à partir de l’application mobile Wandera pour résoudre le problème et récupérer l’accès.

## <a name="supported-platforms"></a>Plateformes prises en charge  

Les plateformes suivantes sont prises en charge lorsque Wandera est inscrit dans Intune :

- Android 5.0 et ultérieur  
- iOS 10.2 et versions ultérieures  

Pour plus d'informations sur la plate-forme et l'appareil, consultez le site web [Wandera](https://www.wandera.com/why-wandera/features/device-support/).

## <a name="prerequisites"></a>Prérequis  

- Abonnement Microsoft Intune  
- Azure Active Directory  
- Wandera Mobile Threat Defense (anciennement Wandera Secure)  

Pour plus d’informations, consultez [Wandera Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Exemples de scénario

Voici les scénarios courants lors de l’utilisation de Wandera MTD avec Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes  

Lorsque des applications malveillantes telles que des logiciels malveillants sont détectées sur des appareils, vous pouvez empêcher ces appareils d’exécuter ces applications jusqu'à ce que la menace soit résolue. Les blocages communs incluent :  
- Connexion à la messagerie de l’entreprise  
- Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work  
- Accès aux applications d’entreprise  

**Blocage quand des applications malveillantes sont détectées** :

![Image conceptuelle d’applications malveillantes détectées](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Accès accordé après correction** : 

![Image conceptuelle de l’accès accordé après correction](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau  

Détectez les menaces pour votre réseau, telles que les attaques de l’intercepteur (« Man-in-the-middle »), et protégez l’accès aux réseaux Wi-Fi en fonction du risque évalué pour l’appareil.  

**Bloquer l’accès au réseau via le Wi-Fi** :  

![Bloquer l’accès au réseau via le Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Accès accordé après correction** :  

![Accès accordé après correction](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces pour votre réseau, telles que les attaques de l’intercepteur, et empêchez la synchronisation des fichiers d’entreprise en fonction du risque évalué pour l’appareil.

**Bloquer SharePoint Online quand des menaces réseau sont détectées** :  

![Bloquer SharePoint Online lorsque des menaces réseau sont détectées](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Accès accordé après correction** :  

![Accès accordé après correction pour un exemple SharePoint](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer Wandera à Intune](Wandera-mtd-connector-integration.md)
- [Configurer les applications Wandera](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Créer une stratégie de conformité des appareils Wandera](mtd-device-compliance-policy-create.md)
- [Activer le connecteur MTD Wandera](mtd-connector-enable.md)