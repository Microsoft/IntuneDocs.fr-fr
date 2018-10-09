---
title: Connecteur Symantec avec Microsoft Intune
titlesuffix: ''
description: Découvrez-en plus sur l’intégration d’Intune avec Endpoint Protection Mobile pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf28e91789549cc82db01b052e41cfd99eafb60d
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231319"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Connecteur Symantec Endpoint Protection Mobile

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise avec un accès conditionnel basé sur une évaluation des risques effectuée par Symantec Endpoint Protection Mobile (SEP), qui est une solution de protection contre les menaces mobiles qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant SEP Mobile, notamment :

-   Défense physique

-   Défense du réseau

-   Défense des applications

-   Défense contre les vulnérabilités

Vous pouvez activer l’évaluation des risques par SEP Mobile via les stratégies de conformité d’appareil Intune, puis utiliser les stratégies d’accès conditionnel pour autoriser un appareil non conforme à accéder aux ressources de l’entreprise en fonction des menaces détectées, ou l’en empêcher.

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Comment Intune et SEP Mobile aident-ils à protéger les ressources de votre entreprise ?

L’application SEP Mobile pour Android ou iOS capture le système de fichiers, la pile réseau, les appareils et les données de télémétrie de l’application lorsqu’elles sont disponibles, puis les envoie au service cloud Symantec pour évaluer les risques de l’appareil face aux menaces mobiles.

La stratégie de conformité d’appareil Intune inclut une règle pour SEP Mobile, basée sur l’évaluation des risques SEP Mobile. Quand cette règle est activée, Intune évalue si l’appareil est conforme à la stratégie activée.

Si l’appareil est détecté comme non conforme, l’accès aux ressources comme Exchange Online et SharePoint Online est bloqué. Les utilisateurs d’appareils bloqués reçoivent de l’aide à partir de l’application mobile SEP Mobile pour résoudre le problème et récupérer l’accès aux ressources de l’entreprise.

Intune prend en charge deux modes d’intégration avec SEP Mobile :

-   **Configuration de base** : un mode en lecture seule qui permet à SEP Mobile d’identifier les appareils dans Intune.

-   **Intégration complète** : permet à SEP Mobile de transmettre à Intune des informations sur les incidents de sécurité et les risques de l’appareil.

## <a name="sample-scenarios"></a>Exemples de scénario

Voici quelques scénarios courants :

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Contrôler l’accès en fonction des menaces émanant des applications malveillantes

Lorsque des applications malveillantes, des logiciels malveillants par exemple, sont détectées sur des appareils, vous pouvez bloquer ces appareils jusqu'à ce que la menace soit écartée :

-   Connexion à la messagerie de l’entreprise

-   Synchroniser les fichiers d’entreprise à l’aide de l’application OneDrive for Work

-   Accès aux applications d’entreprise

**Blocage lorsque des applications malveillantes sont détectées :**

![Applications malveillantes détectées](./media/symantec-arch-1.png)

**Accès accordé après correction :**

![Accès accordé après correction suite à la détection d’applications malveillantes](./media/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Contrôler l’accès en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et protégez l’accès aux réseaux Wi-Fi compte tenu du risque de l’appareil.

**Bloquer l’accès au réseau via le Wi-Fi :**

![Bloquer l’accès au réseau via le Wi-Fi](./media/symantec-arch-3.png)

**Accès accordé après correction :**

![Accès accordé après correction](./media/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Contrôler l’accès à SharePoint Online en fonction de la menace pour le réseau

Détectez les menaces, par exemple les interceptions (**Man-in-the-middle**), sur le réseau et empêchez la synchronisation des fichiers d’entreprise compte tenu du risque de l’appareil.

**Bloquer SharePoint Online lorsque des menaces réseau sont détectées :**

![Bloquer SharePoint Online lorsque des menaces réseau sont détectées](./media/symantec-arch-5.png)

**Accès accordé après correction :**

![Accès accordé après correction pour un exemple Sharepoint](./media/symantec-arch-6.png)

## <a name="supported-platforms"></a>Plateformes prises en charge

-   **Android 4.1 et versions ultérieures**

-   **iOS 8 et versions ultérieures**

## <a name="pre-requisites"></a>Conditions préalables

-   Azure Active Directory Premium

-   Abonnement Microsoft Intune

-   Abonnement Symantec Endpoint Protection Mobile

Pour plus d'informations, consultez le [site web Symantec](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Étapes suivantes

Voici les étapes que vous devez effectuer pour intégrer Intune à SEP Mobile :

- [Configurez l’intégration de SEP Mobile à Intune](skycure-mtd-connector-integration.md)

- [Ajoutez et affectez des applications SEP Mobile, Microsoft Authenticator et une stratégie de configuration d’application iOS](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Créez une stratégie de conformité des appareils SEP Mobile avec Intune](mtd-device-compliance-policy-create.md)

- [Activez le connecteur SEP Mobile MTD dans Intune](mtd-connector-enable.md)
