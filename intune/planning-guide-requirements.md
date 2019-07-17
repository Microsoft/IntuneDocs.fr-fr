---
title: Déterminer les exigences du scénario d’utilisation
titleSuffix: Microsoft Intune
description: Cet article permet de déterminer les exigences du scénario de cas d’utilisation et de cas d'utilisation secondaires Intune dans le cadre de l'implémentation d'un cloud Microsoft Intune uniquement.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 703509c316a22995d26223f6c386de0a2ec66c31
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882720"
---
# <a name="determine-use-case-scenario-requirements"></a>Déterminer les exigences du scénario d’utilisation

Dans cette section, vous déterminez les exigences de chaque groupe organisationnel pour chaque scénario de cas d’utilisation. Ce processus vous aidera à préparer les autres phases de planification du déploiement Intune comme l’architecture et la conception, l’intégration et le déploiement. Il peut également vous aider à identifier les lacunes potentielles et les difficultés liées à votre projet de déploiement Intune.

Vous pouvez avoir différents ensembles d'exigences pour vos scénarios de cas d'utilisation/cas d'utilisation secondaires, avec leurs groupes organisationnels et plateformes d'appareils mobiles associés. Par exemple, vos exigences de scénario d’utilisation d’entreprise peuvent nécessiter l’inscription d’appareils dans Intune avec un ensemble de paramètres d’appareil plus restrictif, comme un code confidentiel de 6 caractères ou la désactivation de la sauvegarde sur le cloud. Votre scénario d’utilisation BYOD (apportez votre propre appareil), peut être moins restrictif et autorise un code confidentiel de 4 caractères et la sauvegarde sur le cloud.

Vous utilisez peut-être également des groupes organisationnels pour le scénario de cas d’utilisation d’entreprise avec différents ensembles d'exigences (par exemple, paramètres de code PIN, profil Wi-Fi ou VPN, applications déployées). Vos exigences peuvent également être déterminées par les fonctionnalités de la plateforme de l'appareil mobile (par exemple, lecteur d'empreinte digitale, profil de messagerie).

Voici quelques exemples d'exigences de cas d'utilisation d'une organisation, illustrant différents ensembles d'exigences pour chaque scénario de cas d'utilisation et de cas d'utilisation secondaire, groupe organisationnel et plateforme d'appareils mobiles. Vous pouvez également utiliser le tableau suivant pour entrer les exigences de cas d’utilisation de votre organisation :

| **Scénarios d'utilisation** | **Cas d'utilisation secondaires** | **Groupes** | **Plateformes d'appareils** | **Configuration requise** |
|:---:|:---:|:---:|:---:|:---:|
| Entreprise | Travailleur de l'information | Ressources humaines, finances | iOS | Messagerie sécurisée, paramètres des appareils, profils, applications |                                                          
| Entreprise | Cadres | Ressources humaines, finances | iOS | Messagerie sécurisée, paramètres des appareils, profils, applications |                                                         
| Entreprise | Kiosk | Commerce | Android | Paramètres des appareils, profils, applications |
| BYOD | Travailleur de l'information | Marketing, Ventes | iOS | Messagerie sécurisée, paramètres des appareils, profils, applications |                                                         
| BYOD | Cadres | Marketing, Ventes | iOS | Messagerie sécurisée, paramètres des appareils, profils, applications |

Vous pouvez [télécharger un modèle du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour saisir les exigences de cas d’utilisation et de cas d'utilisation secondaires de votre organisation.


## <a name="examples-of-requirements"></a>Exemples d'exigences

Voici quelques exemples supplémentaires qui peuvent être utilisés dans la colonne « Exigences » :

- **Messagerie sécurisée**
  - Accès conditionnel pour Exchange Online/sur site
  - Stratégies de protection des applications Outlook

- **Paramètres de l’appareil**
  - Code confidentiel avec quatre ou six caractères
  - Restreindre la sauvegarde sur le cloud

- **Profils**
  - Wi-Fi
  - VPN
  - E-mail (Windows 10 mobile)

- **Applications**
  - Office 365 avec stratégies de protection des applications
  - Activité commerciale avec stratégies de protection des applications

## <a name="next-steps"></a>Étapes suivantes

La section suivante fournit des conseils sur le [développement d'un plan de déploiement Intune](planning-guide-rollout-plan.md).
