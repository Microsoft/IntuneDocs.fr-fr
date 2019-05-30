---
title: Connecteur Better Mobile Threat Defense avec Intune
titleSuffix: Intune on Azure
description: Configurez le connecteur Better Mobile Threat Defense avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 72835ce45860eb6b10ac7967693cc50b9ceaa96f
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043571"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Connecteur Better Mobile Threat Defense avec Intune

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise grâce à l’accès conditionnel basé sur une analyse des risques menée par Better Mobile, une solution de défense contre les menaces mobiles qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies sur les appareils exécutant l’application Better Mobile.

Vous pouvez configurer des stratégies d’accès conditionnel qui s’appuient sur l’analyse des risques de Better Mobile par le biais de stratégies de conformité des appareils Intune, et les utiliser pour autoriser les appareils non conformes à accéder aux ressources de l’entreprise ou les en empêcher en fonction des menaces détectées.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Comment Intune et Better Mobile aident-ils à protéger les ressources de votre entreprise ?

L'application Better Mobile est installée et exécutée sur des appareils mobiles. Cette application capture les données de télémétrie disponibles sur le système de fichiers, la pile logicielle, les appareils et les applications, puis les envoie au service cloud Better Mobile pour évaluer les risques de l’appareil face aux menaces mobiles.

La stratégie de conformité des appareils Intune comporte une règle pour la défense contre les menaces mobiles, qui s’appuie sur l’analyse des risques de Better Mobile. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée. Si l’appareil est détecté comme non conforme, les utilisateurs ne peuvent pas accéder aux ressources de l’entreprise comme Exchange Online et SharePoint Online. Les utilisateurs reçoivent aussi des conseils de l’application Better Mobile installée sur leurs appareils pour résoudre le problème et rétablir l’accès aux ressources de l’entreprise.

## <a name="sample-scenarios"></a>Exemples de scénario

Voici quelques scénarios courants.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes

Quand des applications malveillantes telles que des programmes malveillants sont détectés sur des appareils, vous pouvez bloquer les actions suivantes sur ces appareils jusqu’à ce que la menace soit écartée :

-   Connexion à la messagerie de l’entreprise

-   Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work

-   Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Image montrant des applications malveillantes détectées](./media/better_mobile_maliciousapps_blocked.png)

**Accès accordé après correction :**

![Applications malveillantes détectées et accès accordé](./media/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau

Détectez les menaces pour votre réseau, comme les **attaques de l’intercepteur (« Man-in-the-middle »)**, et protégez l’accès aux réseaux Wi-Fi en fonction du risque évalué pour l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Bloquer l’accès au réseau via le Wi-Fi](./media/better_mobile_network_wifi_blocked.png)

**Accès accordé après correction :**

![Image montrant l’accès accordé après correction](./media/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces pour votre réseau, comme les **attaques de l’intercepteur**, et empêchez la synchronisation des fichiers d’entreprise en fonction du risque évalué pour l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Bloquer SharePoint Online lorsque des menaces réseau sont détectées](./media/better_mobile_network_spo_blocked.png)

**Accès accordé après correction :**

![Accès accordé après correction pour un exemple Sharepoint](./media/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Plateformes prises en charge

-   **Android 4.1 et versions ultérieures**

-   **iOS 8.0 et versions ultérieures**

## <a name="prerequisites"></a>Prérequis

-   Azure Active Directory Premium

-   Abonnement Microsoft Intune

-   Abonnement Better Mobile Threat Defense

    -   Pour plus d’informations, voir le [site web Better Mobile](https://www.better.mobi/).

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer Better Mobile à Intune](better-mobile-mtd-connector-integration.md)

- [Configurer les applications Better Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Créer une stratégie de conformité des appareils Better Mobile](mtd-device-compliance-policy-create.md)

- [Activer le connecteur Better Mobile MTD](mtd-connector-enable.md)
