---
title: Vue d’ensemble des scénarios guidés
titleSuffix: Microsoft Intune
description: Découvrez les scénarios guidés Intune disponibles sur le portail Gestion des appareils Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 460cabead711e6fa4559bcec39e556448cdf2237
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635363"
---
# <a name="intune-guided-scenarios-overview"></a>Vue d’ensemble des scénarios guidés Intune 

Un scénario guidé est une série d’étapes personnalisée centrée sur un cas d’usage de bout en bout. Les scénarios courants sont basés sur le rôle joué par un administrateur, un utilisateur ou un appareil dans votre organisation. Ces rôles nécessitent généralement un ensemble de profils, de paramètres, d’applications et de contrôles de sécurité soigneusement orchestrés pour offrir une expérience utilisateur et une sécurité optimales.    

Si les étapes et les ressources nécessaires à l’implémentation d’un scénario Intune particulier ne vous sont pas familières, les scénarios guidés peuvent vous servir de point de départ. Le scénario guidé assemble automatiquement les stratégies, les applications, les affectations et d’autres configurations de gestion. Par ailleurs, les scénarios guidés peuvent omettre délibérément certaines options non applicables ou peu courantes pour le scénario donné. 

Les scénarios guidés ne représentent pas un espace de gestion différent des workflows normaux d’Intune. Ces workflows sont pensés pour être utilisés conjointement avec les workflows existants d’Intune pour les profils, les applications et les stratégies. Une fois le scénario guidé terminé, la gestion future du scénario doit se faire entièrement à partir des menus existants pour les stratégies, les applications et les profils. Un scénario guidé n’enregistre pas de type de ressource « scénario guidé » ni ne suit les modifications apportées ultérieurement ressources. Chaque ressource créée par un scénario guidé s’affiche dans sa charge de travail respective. Toutes les options, y compris celles omises dans le scénario guidé, peuvent être modifiées à partir des menus existants.  

## <a name="types-of-guided-scenarios"></a>Types de scénarios guidés 

Par souci de simplicité, tous les scénarios guidés omettent les fonctionnalités d’étendue complexes, comme les balises d’étendue <link>, les groupes d’exclusion et les affectations de groupes virtuels <link>. Toutes les ressources créées par un scénario guidé héritent de chaque balise d’étendue de l’administrateur qui effectue le scénario. Certains scénarios offrent un certain niveau de personnalisation pour les paramètres courants, ceci afin de couvrir les scénarios étroitement liés. Ces scénarios prennent en charge l’affectation de groupe pour les groupes d’inclusion uniquement. Les autres scénarios guidés garantissent une expérience cohérente en n’offrant aucune personnalisation et génèrent automatiquement un nouveau groupe pour accueillir l’ensemble des affectations. Une fois le scénario guidé terminé, vous êtes libre d’utiliser d’autres affectations plus sophistiquées directement à partir des charges de travail de stratégie, d’application et de profil existantes.  

Voici les différents scénarios guidés : 
- Déployer Microsoft Edge pour mobile 
- Essayer un PC géré par le cloud
- Microsoft Office pour mobile sécurisé 

## <a name="guided-scenario-functionality"></a>Fonctionnalités des scénarios guidés 

Les scénarios guidés offrent des fonctionnalités spécifiques. Vous trouverez ci-dessous des explications détaillées sur ce que vous pouvez faire et ne pouvez pas faire quand vous suivez un scénario guidé.

### <a name="launching"></a>Lancement  

Tous les scénarios guidés sont accessibles via **[Portail Gestion des appareils](https://devicemanagement.microsoft.com)**  > **Résolution des problèmes + Support** > **Scénarios guidés**. 

Le scénario guidé commence par une introduction expliquant l’objectif du scénario et indique les prérequis à respecter pour effectuer la configuration. À ce stade, vos autorisations d’administrateur sont vérifiées pour s’assurer que vous avez bien tous les privilèges nécessaires à la mise en œuvre du scénario.  

Une fois la vérification des prérequis terminée, le scénario propose des paramètres propices à la personnalisation. Les scénarios guidés ont été conçus pour ne demander qu’un minimum d’entrées, et les paramètres avancés ou peu courants sont masqués tant qu’ils ne sont pas nécessaires. Chaque scénario guidé propose des liens vers une documentation qui fournit des détails supplémentaires. 

Une fois que tous les paramètres obligatoires ont été entrés, le scénario guidé présente un récapitulatif de ces paramètres et des ressources utiles au scénario. À ce stade, sauf indication contraire, rien n’est enregistré.

L’étape suivante consiste à déployer le scénario. Pendant le déploiement du scénario, toutes les ressources nécessaires et les paramètres sélectionnés sont créés et enregistrés. Le temps nécessaire au déploiement varie selon le scénario. À l’issue du déploiement, le scénario guidé présente la liste des ressources créées avec, pour chaque ressource, des liens vers la vue de gestion, la charge de travail normale et la documentation. 

> [!IMPORTANT]
> La liste présentée à la fin du scénario guidé n’est pas enregistrée et n’est visible que si le scénario guidé est ouvert.  
Si une erreur se produit pendant le déploiement du scénario, toutes les modifications sont annulées. 

### <a name="editing"></a>Modification 

Les scénarios guidés ne permettent pas de modifier les ressources existantes. Une fois créés, les groupes, les ressources et les affectations doivent être modifiés en utilisant les charges de travail existantes.

### <a name="monitoring"></a>Surveillance 

Les scénarios guidés ne permettent pas de superviser les ressources existantes en dehors du processus de création initial. Une fois créés, les groupes, les ressources et les affectations doivent être supervisés en utilisant les charges de travail existantes. 

### <a name="retiring"></a>Mise hors service 

Les scénarios guidés ne permettent pas de mettre des ressources existantes hors service, en dehors du nettoyage automatisé qui intervient quand une erreur se produit pendant le déploiement initial. Une fois créés, les groupes, les ressources et les affectations doivent être mis hors service en utilisant les charges de travail existantes. 

### <a name="updating"></a>Mise à jour

Au fur et à mesure que la technologie évolue, Intune peut de temps à autre mettre à jour un scénario guidé pour améliorer l’expérience utilisateur, la sécurité ou d’autres aspects du scénario. Cette mise à jour affecte uniquement les nouveaux déploiements exécutés par le scénario guidé. Intune ne met pas à jour les ressources existantes que le scénario guidé a générées antérieurement pour s’aligner sur les bonnes pratiques ou les recommandations nouvelles.  

## <a name="next-steps"></a>Étapes suivantes

Pour être rapidement opérationnel sur Microsoft Intune, parcourez les scénarios détaillés Intune. Si vous débutez avec Intune, configurez votre locataire Intune en suivant le [guide de démarrage rapide de l’essai gratuit](free-trial-sign-up.md).
