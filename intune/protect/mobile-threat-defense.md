---
title: Mobile Threat Defense avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilisez Intune Mobile Threat Defense (MTD) avec votre partenaire Mobile Threat Defense pour protéger l’accès aux ressources d’entreprise en fonction des risques des appareils.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b67e3b14fd94376fb6dacad88fa58ddc460a6bc5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73057582"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Intégration de la protection contre les menaces mobiles avec Intune

Intune peut intégrer les données d’un fournisseur Mobile Threat Defense (MTD) comme source d’informations pour les stratégies de conformité des appareils et les règles d’accès conditionnel des appareils. Vous pouvez utiliser ces informations pour mieux protéger les ressources d’entreprise comme Exchange et SharePoint, en bloquant l’accès à partir d’appareils mobiles compromis.

Intune peut utiliser ces mêmes données comme source pour les appareils non inscrits à l’aide de stratégies de protection d’applications Intune. Les administrateurs peuvent utiliser ces informations pour aider à protéger les données d’entreprise au sein d’une [application protégée par Microsoft Intune](~/apps/apps-supported-intune-apps.md), et émettre un blocage ou une réinitialisation sélective.

## <a name="protect-corporate-resources"></a>Protéger les ressources de l'entreprise

Il peut être utile d’intégrer les informations provenant des fournisseurs MTD pour protéger les ressources de l’entreprise contre les menaces qui affectent les plateformes mobiles.  

En règle générale, les entreprises se montrent proactives pour protéger les ordinateurs contre les vulnérabilités et attaques, alors que les appareils mobiles restent souvent non supervisés et non protégés. Alors que les plateformes mobiles offrent maintenant une protection intégrée grâce notamment à l’isolation d’application et à la vérification des applications des App Stores, elles restent vulnérables aux attaques sophistiquées. De plus en plus d’employés utilisent des appareils pour travailler et accéder à des informations sensibles ; c’est pourquoi les informations provenant des fournisseurs MTD peuvent vous aider à protéger les appareils et vos ressources contre des attaques de plus en plus sophistiquées.

## <a name="intune-mobile-threat-defense-connectors"></a>Connecteurs de protection contre les menaces mobiles Intune

Intune utilise un connecteur Mobile Threat Defense pour créer un canal de communication entre Intune et le fournisseur MTD que vous avez choisi. Les partenaires MTD d’Intune proposent des applications intuitives et faciles à déployer pour les appareils mobiles. Ces applications analysent activement les informations sur les menaces à partager avec Intune. Intune peut utiliser ces données pour générer des rapports ou à des fins de mise en œuvre.

Par exemple : Une application MTD connectée signale au fournisseur MTD qu’un téléphone de votre réseau est actuellement connecté à un réseau vulnérable aux attaques de l’intercepteur. Ces informations sont classées à un niveau de risque approprié : faible, moyen ou élevé. Ce niveau de risque est ensuite comparé aux autorisations de niveau de risque que vous définissez dans Intune. Suite à cette comparaison, l’accès à certaines ressources de votre choix peut être révoqué tant que l’appareil est compromis.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Données collectées par Intune pour Mobile Threat Defense

Si cette option est activée, Intune collecte les informations de l’inventaire des applications sur les appareils personnels et détenus par l’entreprise, et les met à disposition des fournisseurs MTD, comme Lookout for Work. Vous pouvez collecter un inventaire des applications auprès des utilisateurs d’appareils iOS.

Ce service est basé sur un abonnement : aucune information d’inventaire des applications n’est partagée par défaut. Un administrateur Intune doit activer la **synchronisation des applications pour les appareils iOS** dans les paramètres du connecteur Mobile Threat Defense avant que des informations d’inventaire des applications soient partagées.

**Inventaire des applications**  
Si vous activez la synchronisation des applications pour les appareils iOS, les inventaires à partir des appareils iOS personnels et d’entreprise sont envoyés à votre fournisseur de service de détection des menaces mobiles(MDT). Les données de l’inventaire des applications comprennent les informations suivantes :

- ID de l’application
- Version de l’application
- Version abrégée de l’application
- Nom de l’application
- Taille du bundle d’applications
- Taille dynamique de l’application
- Validation, ou non, de l’application
- Gestion, ou non, de l’application

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Exemples de scénarios pour les appareils inscrits utilisant des stratégies de conformité des appareils

Quand un appareil est considéré comme infecté par la solution de protection contre les menaces mobiles :

![Image illustrant un appareil infecté par Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-1.png)

L’accès est autorisé une fois que le problème lié à l’appareil a été résolu :

![Image illustrant un accès accordé à Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Exemples de scénarios pour les appareils non inscrits utilisant des stratégies de protection d’applications Intune

Quand un appareil est considéré comme infecté par la solution de protection contre les menaces mobiles :<br>
![Image illustrant un appareil infecté par Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-3.png)

L’accès est autorisé une fois que le problème lié à l’appareil a été résolu :<br>
![Image illustrant un accès accordé à Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> Il est possible d’utiliser plusieurs fournisseurs Mobile Threat Defense avec un seul locataire Intune. Toutefois, lorsque plusieurs fournisseurs sont configurés pour la même plateforme, tous les appareils qui exécutent cette plateforme doivent installer chacune des applications MTD et rechercher les menaces. Si vous n’envoyez pas d’analyse à partir d’une application configurée, l’appareil est marqué comme non conforme. 

## <a name="mobile-threat-defense-partners"></a>Partenaires de protection contre les menaces mobiles

Découvrez comment protéger l’accès aux ressources d’entreprise en fonction du risque évalué pour l’appareil, le réseau et l’application avec :

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
