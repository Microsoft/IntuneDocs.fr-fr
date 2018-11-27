---
title: Mobile Threat Defense avec Microsoft Intune
titleSuffix: ''
description: Utilisez Intune Mobile Threat Defense (MTD) avec votre partenaire Mobile Threat Defense pour protéger l’accès aux ressources d’entreprise en fonction des risques des appareils.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65bbc207f96ae2b1670fa2ddc45cad56466580df
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183636"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Qu’est-ce que l’intégration Mobile Threat Defense avec Intune ?


Les connecteurs de protection contre les menaces mobiles Intune vous permettent de tirer parti de votre fournisseur de protection contre les menaces mobiles choisi comme source d’informations pour vos stratégies de conformité et vos règles d’accès conditionnel. Ceci permet aux administrateurs informatiques d’ajouter une couche de protection à leurs ressources d’entreprise, comme Exchange et Sharepoint, en particulier contre les appareils mobiles compromis.

## <a name="what-problem-does-this-solve"></a>Quel problème cette fonctionnalité résout-elle ?

Les entreprises doivent protéger leurs données sensibles contre diverses menaces émergentes, notamment les menaces ciblant le matériel, les applications et le réseau, ainsi que les vulnérabilités du système d’exploitation.

Historiquement, les entreprises ont été proactives en matière de protection des PC contre les attaques, tandis que les appareils mobiles restent non contrôlés et non protégés. Les plateformes mobiles offrent maintenant une protection intégrée grâce notamment à l’isolation d’application et à la vérification des applications des App Store, mais elles restent vulnérables aux attaques sophistiquées. Aujourd'hui, de plus en plus d’employés utilisent des appareils pour travailler et ils ont besoin d’accéder à des informations sensibles. Les appareils doivent être protégés contre les attaques qui sont de plus en plus sophistiquées.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Comment les connecteurs Mobile Threat Defense Intune fonctionnent-ils ?

Le connecteur protège les ressources de l’entreprise en créant un canal de communication entre Intune et le fournisseur de protection contre les menaces mobiles que vous avez choisi. Les partenaires Mobile Threat Defense d’Intune offrent des applications intuitives et faciles à déployer pour les appareils mobiles, qui analysent de manière active les informations relatives aux menaces pour les partager avec Intune, à des fins de création de rapports ou d’application de stratégies. 

Par exemple, si une application Mobile Threat Defense connectée signale au fournisseur Mobile Threat Defense qu’un téléphone sur votre réseau est connecté à un réseau vulnérable aux « attaques de l’intercepteur », ces informations sont partagées et classées à un niveau de risque approprié (faible/moyen/élevé), qui peut ensuite être comparé à vos quotas de niveau de risque configurés dans Intune, afin de déterminer si l’accès à certaines ressources doit être révoqué quand l’appareil est compromis.

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
