---
title: Connecteur Zimperium MTD avec Intune
titleSuffix: Intune on Azure
description: Découvrez-en plus sur l’intégration d’Intune avec Zimperium Mobile Threat Defense pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6deed5de94b72ec3dfb5e8336cc2a58678b4748f
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231472"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Connecteur Zimperium Mobile Threat Defense avec Intune

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Zimperium,une solution MTD qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant l’application Zimperium.

Vous pouvez configurer des stratégies d’accès conditionnel basées sur l’évaluation des risques de Zimperium activée par le biais des stratégies de conformité des appareils Intune, et les utiliser pour autoriser ou bloquer l’accès des appareils non conformes aux ressources de l’entreprise en fonction des menaces détectées.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Comment Intune et Zimperium aident-ils à protéger les ressources de votre entreprise ?

L’application Zimperium pour Android et iOS capture le système de fichiers, la pile réseau, les données de télémétrie de l’appareil et des applications quand elles sont disponibles, puis les envoie au service cloud Zimperium pour évaluer les risques de l’appareil face aux menaces mobiles.

La stratégie de conformité des appareils Intune inclut une règle pour Zimperium Mobile Threat Defense, basée sur l’évaluation des risques Zimperium. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée. Si l’appareil est détecté comme non conforme, les utilisateurs ne peuvent pas accéder aux ressources de l’entreprise comme Exchange Online et SharePoint Online. Les utilisateurs reçoivent aussi des conseils de l’application Zimperium installée sur leurs appareils pour résoudre le problème et rétablir l’accès aux ressources de l’entreprise.

## <a name="sample-scenarios"></a>Exemples de scénario

Voici quelques scénarios courants lors de l’intégration de Zimperium à Intune :

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes

Lorsque des applications malveillantes, des logiciels malveillants par exemple, sont détectées sur des appareils, vous pouvez bloquer ces appareils jusqu'à ce que la menace soit écartée :

-   Connexion à la messagerie de l’entreprise

-   Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work

-   Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Applications malveillantes détectées](./media/Maliciousapps_blocked_Zimperium.png)

**Accès accordé après correction :**

![Applications malveillantes détectées et accès accordé](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et protégez l’accès aux réseaux Wi-Fi compte tenu du risque de l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Bloquer l’accès au réseau via le Wi-Fi](./media/network_wifi_blocked_Zimperium.png)

**Accès accordé après correction :**

![Accès accordé après correction](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et empêchez la synchronisation des fichiers d’entreprise compte tenu du risque de l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Bloquer SharePoint Online lorsque des menaces réseau sont détectées](./media/network_spo_blocked_Zimperium.png)

**Accès accordé après correction :**

![Accès accordé après correction pour un exemple Sharepoint](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Plateformes prises en charge

-   **Android 4.1 et versions ultérieures**

-   **iOS 8 et versions ultérieures**

## <a name="prerequisites"></a>Prérequis

-   Azure Active Directory Premium

-   Abonnement Microsoft Intune

-   Abonnement Zimperium Mobile Threat Defense

    -   Pour plus d’informations, consultez le [site web Zimperium](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Étapes suivantes

- [Intégrer Zimperium à Intune](zimperium-mtd-connector-integration.md)

- [Configurer les applications Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Créer une stratégie de conformité des appareils Zimperium](mtd-device-compliance-policy-create.md)

- [Activer le connecteur Zimperium MTD](mtd-connector-enable.md)
