---
title: Connecteur Lookout MTD avec Microsoft Intune | Microsoft Intune
description: Découvrez-en plus sur l’intégration d’Intune avec Lookout Mobile Threat Defense (MTD) pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bd61b10ee60e1f9413c22d0d618bc5c270dc76a6
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817073"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Connecteur de protection contre les menaces mobiles pour Lookout avec Intune

Vous pouvez contrôler l’accès des appareils mobiles aux ressources d’entreprise en fonction de l’évaluation des risques effectuée par Lookout, une solution de défense contre les menaces mobiles intégrée à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies à partir des appareils par le service Lookout, notamment :
- Vulnérabilités du système d’exploitation
- Applications malveillantes installées
- Profils de réseau malveillants

Vous pouvez configurer des stratégies d’accès conditionnel basé sur l’évaluation des risques Lookout activée par le biais des stratégies de conformité Intune. Les paramètres vous permettent d’autoriser ou de bloquer les appareils non conformes en fonction des menaces détectées.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>Comment Intune et Lookout Mobile Threat Defense aident-ils à protéger les ressources de l’entreprise ?
L'application mobile Lookout, **Lookout for work**, est installée et exécutée sur les appareils mobiles. Cette application capture le système de fichiers, la pile réseau ainsi que les données de télémétrie des appareils et des applications (le cas échéant), puis les envoie au service cloud Lookout pour évaluer les risques de l’appareil face aux menaces mobiles. Vous pouvez modifier la classification des niveaux de risque des menaces dans la console Lookout pour l’adapter à vos besoins.  

La stratégie de conformité d’Intune inclut une règle Lookout Mobile Threat Defense basée sur l’évaluation des risques Lookout. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée.

Si l’appareil est considéré comme non conforme, l'accès aux ressources comme Exchange Online et SharePoint Online peut être bloqué. Les utilisateurs d'appareils bloqués reçoivent une procédure à suivre pour résoudre le problème et accéder à nouveau aux ressources. Cette procédure est lancée à partir de l'application Lookout for work.

## <a name="supported-platforms"></a>Plateformes prises en charge
Les plateformes suivantes sont prises en charge lorsque Lookout est inscrit dans Intune :
* **Android 4.1 et versions ultérieures**
* **iOS 8 et versions ultérieures** Pour plus d’informations sur les plate-formes et les langues prises en charge, consultez le [site Web de Lookout](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Prérequis
* Abonnement Microsoft Intune
* Azure Active Directory
* Abonnement d’entreprise à Lookout Mobile EndPoint Security  

Pour plus d’informations, consultez [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Exemples de scénario

Voici les scénarios courants lors de l’utilisation de la protection contre les menaces mobiles Lookout avec Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes
Lorsque des applications malveillantes telles que des logiciels malveillants sont détectés sur des appareils, vous pouvez isoler ces appareils jusqu'à ce que la menace soit résolue :
* Connexion à la messagerie de l’entreprise
* Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work
* Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Image conceptuelle de la stratégie bloquant l’accès en raison de la détection d’applications malveillantes](./media/malicious-apps-blocked.png)

**Accès accordé après correction :**

![Image conceptuelle montrant l’accès accordé aux appareils après correction](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau
Détectez les menaces pour votre réseau, telles que les attaques de l’intercepteur (« Man-in-the-middle »), et protégez l’accès aux réseaux Wi-Fi en fonction du risque évalué pour l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Image montrant le blocage de l’accès par Wi-Fi en fonction des menaces pour le réseau](./media/network-wifi-blocked.png)

**Accès accordé après correction :**

![Image conceptuelle de l’accès conditionnel autorisant l’accès après correction](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces pour votre réseau, telles que les attaques de l’intercepteur, et empêchez la synchronisation des fichiers d’entreprise en fonction du risque évalué pour l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Image conceptuelle du blocage de l’accès à SharePoint Online](./media/network-spo-blocked.png)


**Accès accordé après correction :**

![Image conceptuelle de l’accès accordé après correction de la menace réseau](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>Étapes suivantes
Voici les principales étapes à effectuer pour implémenter cette solution :
1.  [Configurer l’intégration de Lookout](lookout-mtd-connector-integration.md)
2.  [Activer Lookout Mobile Threat Defense dans Intune](mtd-connector-enable.md)
3.  [Ajouter et affecter l’application Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Configurer la stratégie de conformité d’appareil Lookout](mtd-device-compliance-policy-create.md)
