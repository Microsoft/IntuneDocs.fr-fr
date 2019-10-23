---
title: Identifier des scénarios d’utilisation
titleSuffix: Microsoft Intune
description: Cet article permet de déterminer les scénarios d'utilisation principaux et secondaires d’Intune dans le cadre d’une implémentation Microsoft Intune exclusivement cloud.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96ebae46fd4935c3070319f16d35d5b53888e94c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505175"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>Identifier les scénarios d'utilisation de la gestion des périphériques mobiles

L’identification des scénarios d'utilisation représente une part importante du processus de planification pour un déploiement Intune réussi. Les scénarios d’utilisation sont utiles en ce qu’ils permettent de segmenter les utilisateurs dans différents groupes gérables en fonction de leur type ou de leur rôle et du propriétaire de l’appareil utilisé (par exemple, l’entreprise ou l’utilisateur).

Examinons quelques exemples qui aideront votre organisation à identifier les scénarios d'utilisation d’Intune, ainsi que les groupes organisationnels et les plateformes d’appareils mobiles associées à chaque cas d’utilisation.

## <a name="device-ownership"></a>Propriété des appareils
Pour commencer, vous pouvez vous reporter aux objectifs de déploiement Intune de votre organisation afin d’identifier les principaux scénarios d’utilisation de votre déploiement. Dans le cadre de votre plan de déploiement d’Intune, répondez aux questions suivantes :

- Envisagez-vous de prendre en charge des appareils appartenant à l’entreprise ?

- Envisagez-vous de prendre en charge des appareils appartenant aux employés (BYOD) ?

Il n’y a pas d’options soit/ou. Vous aurez peut-être besoin de prendre en charge les deux types de propriétaires des appareils pour répondre aux objectifs de votre entreprise. Les cas d’utilisation secondaires vous aideront à savoir à quoi appliquer les différentes stratégies de gestion de périphériques.

### <a name="user-type-or-device-role"></a>Type utilisateur ou rôle de l’appareil

Pour chaque scénario d’utilisation, déterminez s’il comprend également des cas d’usage secondaires. Par exemple, votre organisation peut avoir identifié les exigences à respecter pour prendre en charge un scénario d’utilisation professionnelle qui comprend d'autres cas d’usage secondaires concernant le type utilisateur ou le rôle de l’appareil, notamment :

- Travailleur de l'information

- Équipe dirigeante

- Kiosk

Voici quelques exemples de scénarios d’utilisation principaux et secondaires :

| **Scénarios d'utilisation** | **Cas d'utilisation secondaires** |
|:---:|:---:|
| Entreprise | Travailleur de l'information |              
| Entreprise | Cadres |           
| Entreprise | Kiosk |
| BYOD | Travailleur de l'information |           
| BYOD | Cadres |

Vous pouvez [télécharger un modèle du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour entrer les scénarios d’utilisation principaux et secondaires de votre organisation.

## <a name="organizational-groups-for-your-scenarios"></a>Groupes organisationnels pour les scénarios

Vous devez maintenant identifier les groupes organisationnels associés à chaque scénario d'utilisation principal ou secondaire. Par exemple :

| **Scénarios d'utilisation** | **Cas d'utilisation secondaires** | **Groupes organisationnels** |
|:---:|:---:|:---:|
| Entreprise | Travailleur de l'information | Ressources humaines, finances |               
| Entreprise | Équipe dirigeante | Ressources humaines, finances |            
| Entreprise | Kiosk | Commerce |
| BYOD | Travailleur de l'information | Marketing, Ventes |            
| BYOD | Équipe dirigeante | Marketing, Ventes |


## <a name="mobile-device-platforms-for-your-scenarios"></a>Plateformes d’appareils mobiles pour vos scénarios

À ce stade, l’objectif est d’identifier les plateformes d'appareils mobiles associées à chaque scénario d’utilisation. Il peut y en avoir plusieurs.

Par exemple, votre scénario d’utilisation professionnelle prend peut-être en charge les plateformes d’appareils iOS et Android Samsung Knox. Il est possible que votre stratégie BYOD inclue la prise en charge de plateformes d’appareils mobiles supplémentaires comme Android (hors Samsung Knox) et Windows 10 Mobile. À partir des exemples précédents, nous avons associé les plateformes d’appareils mobiles à chaque scénario d’utilisation.

| **Scénarios d'utilisation** | **Cas d'utilisation secondaires** | **Groupes** | **Plateformes d'appareils** |   
|:---:|:---:|:---:|:---:|
| Entreprise | Travailleur de l'information | Ressources humaines, finances | iOS |                                                           
| Entreprise | Cadres | Ressources humaines, finances | iOS |                                                           
| Entreprise | Kiosk | Commerce | Android |
| BYOD | Travailleur de l'information | Marketing, Ventes | iOS |                                                           
| BYOD | Cadres | Marketing, Ventes | iOS |

## <a name="next-steps"></a>Étapes suivantes

La section suivante fournit des conseils sur [l'identification des exigences Intune pour chaque scénario de cas d’utilisation](../planning-guide-requirements.md).
