---
title: Déterminer les groupes ciblés pour le déploiement et les délais
titleSuffix: Microsoft Intune
description: Cet article vous aide à décider sur quels groupes déployer Microsoft Intune et la plage de temps pour ces déploiements.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a1ac47fd512323ce809d4ee13c5e98f563ce51c
ms.sourcegitcommit: e6edfbfd63dd7c2500ce1123205aa2af9a7e8e2e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68783105"
---
# <a name="develop-a-rollout-plan"></a>Développer un plan de déploiement

Votre plan de déploiement identifie les groupes organisationnels que vous souhaitez cibler pour votre déploiement d’Intune, le délai de déploiement pour chaque groupe et les méthodes d’inscription que vous allez utiliser.

## <a name="targeted-groups-and-timeframes"></a>Groupes ciblés et plages de temps

Tout d’abord, passez en revue les groupes qui sont ciblés avec votre déploiement Intune et que vous avez identifiés dans vos [scénarios d’utilisation](planning-guide-scenarios.md).

Ensuite, déterminez la plage de temps pour chaque groupe ciblé. Cette tâche nécessite généralement une discussion entre l’équipe de déploiement Intune et les groupes ciblés afin de déterminer le délai de déploiement le plus approprié pour chaque groupe. Les points à passer en revue lors d’une telle discussion comprennent notamment :
* La disposition au changement du groupe
* Le nombre d’utilisateurs et d’appareils
* Les types de plateformes d’appareils
* Configuration requise
* Emplacement géographique
* Le risque pour l’entreprise

## <a name="rollout-phases"></a>Phases de déploiement
Les organisations choisissent généralement de démarrer le déploiement Intune avec un pilote initial, en ciblant un petit groupe d’utilisateurs au sein du service informatique. Le pilote peut ensuite être étendu afin d'inclure un ensemble plus large d’utilisateurs et peut comprendre la participation d’autres groupes de l’organisation.

### <a name="pilot"></a>Pilote
La première phase de déploiement doit représenter des utilisateurs pilotes. Les utilisateurs pilotes doivent comprendre qu’ils sont les premiers utilisateurs d’une nouvelle solution. Ils doivent être prêts à fournir des commentaires afin d'améliorer la configuration, la documentation, les notifications et ouvrir ainsi la voie à tous les autres utilisateurs dans les phases de déploiement ultérieures. Ces utilisateurs ne doivent pas être des cadres ou des VIP.

Le pilote est une bonne occasion de tester les [défis](planning-guide-deployment-goals.md) et d’affiner les [exigences](planning-guide-requirements.md) que vous avez collectées précédemment.

Incluez votre plan de [communication](planning-guide-communication-plan.md), votre plan de [support](planning-guide-support-plan.md), et [le test et la validation](planning-guide-test-validation.md) pour résoudre les problèmes tant que l’impact sur les utilisateurs est encore modéré.

### <a name="production-rollout"></a>Déploiement de production
Après la réussite d’un pilote, vous êtes prêt à commencer un déploiement en production, en ciblant le reste des groupes de votre organisation. Voici quelques exemples de groupes et phases de déploiement différents :

- **Services** <br/>Chaque service peut être une phase de déploiement. Vous ciblez un service à la fois. Dans ce type de déploiement, les utilisateurs de chaque service ont tendance à utiliser l’appareil mobile de la même manière et à accéder aux mêmes applications. Les utilisateurs auront probablement les mêmes types de stratégies.

- **Géographie** <br/>Dans cette approche, vous déployez sur tous les utilisateurs d’une zone géographique spécifique, qu’il s’agisse des mêmes continent, pays/région ou bâtiment de la société. Ce type de déploiement par phases vous permet de vous concentrer sur l’emplacement spécifique des utilisateurs. Il favorise également une meilleure approche de type [gant blanc](#user-assisted-enrollment) car le nombre d’emplacements de déploiement Intune simultanés est réduit. Étant donné qu’il est probable que différents services ou cas d’utilisation se trouvent au même endroit, différents cas d’utilisation peuvent être déployés en même temps.

- **Plateforme** <br/>Ce type de déploiement consiste à déployer simultanément des plateformes similaires. Exemple : tous les appareils iOS le premier mois, puis les appareils Android, suivis des appareils Windows. Ce type de déploiement échelonné simplifie la prise en charge du support technique, car le support technique n’a à prendre en charge qu’une seule plateforme à la fois.

Voici un exemple de plan de déploiement Intune incluant des groupes et des délais ciblés :

| **Phases de déploiement** | **Juillet** | **Août** | **Septembre** | **Octobre** |
|:---:|:---:|:---:|:---:|:---:|
| Pilote limité | Informatique (50 utilisateurs) |  |  |  |                                                         
| Pilote développé | Informatique (200 utilisateurs), cadres informatiques (10 utilisateurs) |  |  |  |                                                         
| Phase 1 du déploiement de production |  | Ventes et marketing (2000 utilisateurs) |  |  |
| Phase 2 du déploiement de production |  |  | Vente au détail (1 000 utilisateurs) |  |
| Phase 3 du déploiement de production |  |  |  | Ressources humaines (50 utilisateurs), finances (40 utilisateurs), cadres (30 utilisateurs) |

Vous pouvez [télécharger un modèle du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour saisir les phases de déploiement de votre organisation.
## <a name="match-rollout-groups-to-enrollment-approaches"></a>Faire correspondre les groupes de déploiement aux approches d’inscription

Maintenant que vous avez déterminé les groupes et les délais ciblés pour votre déploiement Intune, l’étape suivante consiste à choisir l’approche d’inscription Intune la plus appropriée pour chaque groupe. Il existe différentes approches d’inscription, notamment :
* Libre-service pour utilisateur
* Inscription avec assistance de l'utilisateur
* Salon informatique

### <a name="user-self-service"></a>Libre-service pour utilisateur

Dans ce cas, l’utilisateur est responsable de l’inscription de ses propres appareils, généralement en suivant les instructions d’inscription fournies par son service informatique. Cette approche est plus couramment utilisée dans des organisations et elle est plus évolutive que l’inscription avec assistance de l'utilisateur.

### <a name="user-assisted-enrollment"></a>Inscription avec assistance de l’utilisateur

Il s’agit d’une approche dite de « Gant blanc ». Un membre de l’équipe informatique aide l’utilisateur via le processus d’inscription, en personne ou sur Skype. Cette approche est généralement utilisée avec les cadres et autres groupes qui peuvent nécessiter une assistance plus poussée pendant le processus d’inscription.

### <a name="it-tech-fair"></a>Salon informatique

Une autre option d’inscription de l'utilisateur Intune consiste à organiser un salon informatique. Au cours de cet événement, le service informatique installe un stand d'assistance pour l'inscription Intune d’inscription où les utilisateurs peuvent recevoir des informations sur l’inscription à Intune, poser des questions et recevoir de l’aide sur le processus d’inscription. Cette option peut être utile à la fois pour le service informatique et l’utilisateur, en particulier au cours des premières phases de déploiement Intune.

Voici un exemple de mis à jour du plan de déploiement Intune ci-dessus pour inclure les approches d’inscription :

| **Phases de déploiement** | **Juillet** | **Août** | **Septembre** | **Octobre** |
|:---:|:---:|:---:|:---:|:---:|
| Pilote limité |  |  |  |  |
| Libre-service | Informatique |  |  |  |
| Pilote développé |  |  |  |  |
| Libre-service | Informatique |  |  |  |
| Gant blanc | Cadres informatiques |  |  |  |
| Phase 1 du déploiement de production |  | Ventes, marketing |  |  |
| Libre-service |  | Ventes et marketing |  |  |
| Phase 2 du déploiement de production |  |  | Commerce |  |
| Libre-service |  |  | Commerce |  |
| Phase 3 du déploiement de production |  |  |  | Dirigeants, RH, Finance |
| Libre-service |  |  |  | Ressources humaines, finances |
| Gant blanc |  |  |  | Cadres |

## <a name="next-steps"></a>Étapes suivantes

La section suivante fournit des conseils sur [le développement d'un plan de communication de déploiement Intune](planning-guide-communication-plan.md).
