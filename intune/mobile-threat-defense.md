---
title: Protection contre les menaces mobiles avec Intune
titleSuffix: Azure portal
description: "Protéger l’accès aux ressources d’entreprise en fonction du risque évalué pour l’appareil"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16402b30895e61d9a4ff8393fd4d4c6efa061e9e
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Intégration de la protection contre les menaces mobiles avec Intune


Les connecteurs de protection contre les menaces mobiles Intune vous permettent de tirer parti de votre fournisseur de protection contre les menaces mobiles choisi comme source d’informations pour vos stratégies de conformité et vos règles d’accès conditionnel. Ceci permet aux administrateurs informatiques d’ajouter une couche de protection à leurs ressources d’entreprise, comme Exchange et Sharepoint, en particulier contre les appareils mobiles compromis.

## <a name="what-problem-does-this-solve"></a>Quel problème cette fonctionnalité résout-elle ?

Les entreprises doivent protéger leurs données sensibles contre diverses menaces émergentes, notamment les menaces ciblant le matériel, les applications et le réseau, ainsi que les vulnérabilités du système d’exploitation.

Historiquement, les entreprises ont été proactives en matière de protection des PC contre les attaques, tandis que les appareils mobiles restent non contrôlés et non protégés. Les plateformes mobiles offrent maintenant une protection intégrée grâce notamment à l’isolation d’application et à la vérification des applications des App Store, mais elles restent vulnérables aux attaques sophistiquées. Aujourd'hui, de plus en plus d’employés utilisent des appareils pour travailler et ils ont besoin d’accéder à des informations sensibles. Les appareils doivent être protégés contre des attaques de plus en plus sophistiquées.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Comment les connecteurs de protection contre les menaces mobiles Intune fonctionnent-ils ?

Le connecteur protège les ressources de l’entreprise en créant un canal de communication entre Intune et le fournisseur de protection contre les menaces mobiles que vous avez choisi. Les partenaires de protection contre les menaces mobiles Intune offrent des applications intuitives et faciles à déployer pour les appareils mobiles, qui analysent de manière active les informations relatives aux menaces pour les partager avec Intune, à des fins de création de rapports ou d’application de stratégies. 

Par exemple, si une application de protection contre les menaces mobiles connectée signale au fournisseur de protection contre les menaces mobiles qu’un téléphone sur votre réseau est connecté à un réseau vulnérable aux « attaques de l’intercepteur », ces informations sont partagées et classées à un niveau de risque approprié (faible/moyen/élevé), qui peut ensuite être comparé à vos quotas de niveau de risque configurés dans Intune afin de déterminer si l’accès à certaines ressources doit être révoqué pendant que le appareil est compromis.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Quelles sont les données collectées par Intune pour Mobile Threat Defense ?

Intune collecte les informations d’inventaire des applications sur les appareils personnels et de l’entreprise et les met à disposition des fournisseurs MTD (Mobile Thread Defense), comme Lookout for Work. Vous pouvez collecter un inventaire des applications auprès des utilisateurs d’appareils iOS 11+.

**Inventaire des applications**  
Les inventaires à partir des appareils personnels et d’entreprise iOS 11 sont envoyés à votre fournisseur de service de détection des menaces mobiles. Les données de l’inventaire des applications comprennent les informations suivantes :

 - ID de l’application
 - Version de l’application
 - Version abrégée de l’application
 - Nom de l’application
 - Taille du bundle d’applications
 - Taille dynamique de l’application
 - Application validée ou non
 - Application gérée ou non

## <a name="sample-scenarios"></a>Exemples de scénario

Quand un appareil est considéré comme infecté par la solution de protection contre les menaces mobiles :

![Appareil Mobile Threat Defense infecté](./media/MTD-image-1.png)

L’accès est autorisé une fois que le problème lié à l’appareil a été résolu :

![Mobile Threat Defense - accès accordé](./media/MTD-image-2.png)

> [!NOTE] 
> L’utilisation de plusieurs fournisseurs Mobile Threat Defense avec Intune n’est pas prise en charge. L’activation de plusieurs outils Mobile Threat Defense force l’installation de toutes les applications Mobile Threat Defense et effectue une recherche des menaces sur les appareils.

## <a name="mobile-threat-defense-partners"></a>Partenaires de protection contre les menaces mobiles

Découvrez comment protéger l’accès aux ressources d’entreprise en fonction du risque évalué pour l’appareil, le réseau et l’application avec :

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
