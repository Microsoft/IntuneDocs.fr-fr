---
title: Mobile Threat Defense avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilisez Intune Mobile Threat Defense (MTD) avec votre partenaire Mobile Threat Defense pour protéger l’accès aux ressources d’entreprise en fonction des risques des appareils.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0452229d6c1ea2d9e87a302675167d200bd348eb
ms.sourcegitcommit: 6bba9f2ef4d1ec699f5713a4da4f960e7317f1cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67407167"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Qu’est-ce que l’intégration Mobile Threat Defense avec Intune ?
Intune peut intégrer les données d’un fournisseur Mobile Threat Defense en tant que source d’informations pour des stratégies de conformité et des règles d’accès conditionnel. Vous pouvez utiliser ces informations pour mieux protéger les ressources d’entreprise comme Exchange et SharePoint, en bloquant l’accès à partir d’appareils mobiles compromis.  

## <a name="what-problem-does-this-solve"></a>Quel problème cette fonctionnalité résout-elle ?
L’intégration des informations provenant d’un fournisseur Mobile Threat Defense peut vous aider à protéger les ressources de votre entreprise contre les menaces qui affectent les plateformes mobiles.  

En règle générale, les entreprises se montrent proactives pour protéger les ordinateurs contre les vulnérabilités et attaques, alors que les appareils mobiles restent souvent non supervisés et non protégés. Alors que les plateformes mobiles offrent maintenant une protection intégrée grâce notamment à l’isolation d’application et à la vérification des applications des App Stores, elles restent vulnérables aux attaques sophistiquées. Alors qu’un nombre croissant d’employés utilisent des appareils pour travailler et accéder à des informations sensibles, les informations du fournisseur Mobile Threat Defense peuvent vous aider à protéger les appareils et vos ressources contre les attaques de plus en plus sophistiquées.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Comment les connecteurs Mobile Threat Defense Intune fonctionnent-ils ?

Intune utilise un connecteur Mobile Threat Defense pour créer un canal de communication entre Intune et le fournisseur Mobile Threat Defense que vous avez choisi. Les partenaires Mobile Threat Defense d’Intune proposent des applications intuitives et faciles à déployer pour les appareils mobiles. Ces applications analysent activement les informations sur les menaces à partager avec Intune. Intune peut utiliser ces données pour générer des rapports ou à des fins de mise en œuvre.  

Par exemple : Une application Mobile Threat Defense connectée signale au fournisseur Mobile Threat Defense qu’un téléphone de votre réseau est actuellement connecté à un réseau vulnérable aux attaques d’intercepteurs. Ces informations sont classées à un niveau de risque approprié : faible, moyen ou élevé. Ce niveau de risque est ensuite comparé aux autorisations de niveau de risque que vous définissez dans Intune. Suite à cette comparaison, l’accès à certaines ressources de votre choix peut être révoqué tant que l’appareil est compromis.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Quelles sont les données collectées par Intune pour Mobile Threat Defense ?

Si cette option est activée, Intune collecte les informations d’inventaire des applications sur les appareils personnels et de l’entreprise, et les met à disposition des fournisseurs MTD (Mobile Threat Defense), comme Lookout for Work. Vous pouvez collecter un inventaire des applications auprès des utilisateurs d’appareils iOS.

Ce service est basé sur un abonnement : aucune information d’inventaire des applications n’est partagée par défaut. Un administrateur Intune doit activer la synchronisation des applications pour les appareils iOS dans les paramètres de service avant que des informations d’inventaire des applications soient partagées.

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

## <a name="sample-scenarios"></a>Exemples de scénario

Quand un appareil est considéré comme infecté par la solution de protection contre les menaces mobiles :

![Image illustrant un appareil infecté par Mobile Threat Defense](./media/MTD-image-1.png)

L’accès est autorisé une fois que le problème lié à l’appareil a été résolu :

![Image illustrant un accès accordé à Mobile Threat Defense](./media/MTD-image-2.png)

> [!NOTE] 
> L’utilisation de plusieurs fournisseurs Mobile Threat Defense avec Intune n’est pas prise en charge. L’activation de plusieurs outils Mobile Threat Defense force l’installation de toutes les applications Mobile Threat Defense et effectue une recherche des menaces sur les appareils.

## <a name="mobile-threat-defense-partners"></a>Partenaires de protection contre les menaces mobiles

Découvrez comment protéger l’accès aux ressources d’entreprise en fonction du risque évalué pour l’appareil, le réseau et l’application avec :

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
