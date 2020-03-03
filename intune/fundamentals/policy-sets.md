---
title: Ensembles de stratégie
titleSuffix: Microsoft Intune
description: L’utilisation d’ensembles de stratégies vise à regrouper des objets de gestion dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48bfe727615f5165fc70ed2e08f98f01203dc895
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514827"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Utiliser des ensembles de stratégies pour regrouper des objets de gestion

Les ensembles de stratégies vous permettent de créer un ensemble de références à des entités de gestion existantes qui doivent être identifiées, ciblées et supervisées comme une seule unité conceptuelle. Un ensemble de stratégies est un regroupement affectable d’applications, de stratégies et autres objets de gestion que vous avez créés. En créant un ensemble de stratégies, vous pouvez sélectionner un grand nombre d’objets différents à la fois et les affecter à partir d’un même emplacement. À mesure que votre organisation évolue, vous pouvez réviser un ensemble de stratégies de façon à y ajouter ou supprimer des objets et affectations. Vous pouvez utiliser un ensemble de stratégies pour associer et affecter des objets existants, notamment des applications, des stratégies et des VPN, dans un package unique. 

> [!IMPORTANT]
> Pour obtenir la liste des problèmes connus liés aux ensembles de stratégies, consultez [Problèmes connus des ensembles de stratégies](~/fundamentals/policy-sets.md#policy-sets-known-issues).

Les ensembles de stratégies ne remplacent pas les concepts ou objets existants. Vous pouvez continuer à affecter et référencer des objets individuels dans un ensemble de stratégies. Par conséquent, toute modification apportée à ces objets individuels sera répercutée dans l’ensemble de stratégies. 

Vous pouvez utiliser des ensembles de stratégies pour :

- Regrouper des objets qui doivent être affectés en totalité
- Affecter les exigences de configuration minimale de votre organisation à tous les appareils gérés
- Affecter des applications couramment utilisées ou dignes d’intérêt à tous les utilisateurs

Voici les objets de gestion que vous pouvez inclure dans un ensemble de stratégies :
- Applications
- Stratégies de configuration des applications
- Stratégies de protection des applications
- Profils de configuration d’appareil
- Stratégies de conformité des appareils
- Restrictions de type d’appareil
- Profils Windows Autopilot Deployment
- Page d’état de l’inscription

Quand vous créez un ensemble de stratégies, vous créez une unité d’affectation et gérez les associations entre les différents objets. Un ensemble de stratégies est une référence à des objets externes. Toute modification apportée aux objets inclus se répercute aussi à l’ensemble de stratégies. Après avoir créé un ensemble de stratégies, vous pouvez afficher et modifier à plusieurs reprises les objets et affectations qu’il contient. 

> [!NOTE]
> Les ensembles de stratégies prennent en charge les paramètres Windows, Android, macOS et iOS/iPadOS, et ils peuvent être affectés à plusieurs plateformes.

## <a name="how-to-create-a-policy-set"></a>Comment créer un ensemble de stratégies

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Ensembles de stratégies** > **Ensembles de stratégies** > **Créer**.
3. Dans la page **De base**, ajoutez les valeurs suivantes :
    - **Nom de l’ensemble de stratégies** – Attribuez un nom à cet ensemble de stratégies.
    - **Description** – Décrivez l’ensemble de stratégies (facultatif).
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Cliquez sur **Suivant : Gestion des applications**.<br>
   Dans la page **Gestion des applications**, vous pouvez éventuellement [ajouter des applications](~/apps/apps-add.md), des [stratégies de configuration des applications](~/apps/app-configuration-policies-overview.md) et des [stratégies de protection des applications](~/apps/app-protection-policy.md) à votre ensemble de stratégies. Pour obtenir des informations sur la gestion des applications, consultez [Qu’est-ce que la gestion des applications Microsoft Intune ?](~/apps/app-management.md) 
5. Cliquez sur **Suivant : Gestion des appareils**.<br>
   La page **Gestion des appareils** vous permet d’ajouter des objets de gestion des appareils à votre jeu de stratégies, par exemple des [profils de configuration des appareils](~/configuration/device-profiles.md) et des [stratégies de conformité d’appareil](~/protect/device-compliance-get-started.md). Veillez à inclure tous les objets associés, qu’il s’agisse d’autres stratégies, certificats ou profils de base de référence de sécurité.
6. Cliquez sur **Suivant : Inscription de l’appareil**.<br>
   La page **Inscription de l’appareil** vous permet d’ajouter des objets d’inscription d’appareil à votre jeu de stratégies, par exemple des [restrictions de type d’appareil](~/enrollment/enrollment-restrictions-set.md), des [profils Windows Autopilot Deployment](~/enrollment/enrollment-autopilot.md) et des [profils de page d’état d’inscription](~/enrollment/windows-enrollment-status.md).
7. Cliquez sur **Suivant : Affectations**.<br>
   La page **Affectations** vous permet d’affecter l’ensemble de stratégies à des utilisateurs et des appareils. Il est important de noter que vous pouvez affecter un ensemble de stratégies à un appareil, que celui-ci soit ou non géré par Intune.
8. Cliquez sur **Suivant : Vérifier + créer** pour examiner les valeurs que vous avez entrées pour le profil.
9. Quand vous avez terminé, cliquez sur **Créer** pour créer l’ensemble de stratégies dans Intune. 

## <a name="policy-sets-known-issues"></a>Problèmes connus des ensembles de stratégies

Les ensembles de stratégies, nouveauté de la mise à jour 1910, présentent les problèmes connus suivants.

- Si un administrateur inclus dans l’étendue tente de créer un ensemble de stratégies sans avoir sélectionné de balises d’étendue, la validation échoue et une erreur s’affiche dans la barre d’état au moment d’accéder à la page **Vérifier + créer**. L’administrateur doit alors basculer vers une autre page du processus, puis revenir à la page **Vérifier + créer**. Cela a pour effet d’activer l’option **Créer**.  
 
- Voici les types d’application actuellement pris en charge par les ensembles de stratégies :
    - Application du Store iOS/iPadOS
    - Application métier iOS/iPadOS
    - Application métier iOS/iPadOS gérée
    - Application de l’Android Store
    - Application métier Android
    - Application métier Android gérée
    - Suite Office 365 ProPlus (Windows 10)
    - Lien web
    - Application iOS/iPadOS intégrée
    - Application Android intégrée

- Il n’est pas possible de définir une affectation d’ensemble de stratégies de **Tous les utilisateurs** sur **Profil Autopilot**.

- Les ensembles de stratégies présentent des problèmes liés aux restrictions d’inscription et aux pages d’état d’inscription, à savoir :
    - Les restrictions et les pages d’état d’inscription ne prennent pas en charge les affectations de groupes virtuels.
    - Les restrictions et les pages d’état d’inscription ne prennent absolument pas en charge les affectations de groupes d’exclusion. 
    - Les restrictions et les pages d’état d’inscription utilisent la résolution des conflits basée sur les priorités. Il se peut que les restrictions et les pages d’état d’inscription ne soient pas appliqués aux mêmes utilisateurs que les autres charges utiles d’un ensemble de stratégies si les restrictions et les pages d’état d’inscription sont aussi ciblés par des restrictions et pages d’état d’inscription de priorité plus élevée.
    - Les restrictions et les pages d’état d’inscription par défaut ne peuvent pas être ajoutés à un ensemble de stratégies.

- Les types de stratégie MAM qui prennent en charge les ensembles de stratégies sont les suivants : 
    - Protection des applications gérées ciblées MAM WIP( Windows) MDM 
    - Protection des applications gérées ciblées MAM iOS/iPadOS
    - Protection des applications gérées ciblées par Android
    - Configuration des applications gérées ciblées MAM iOS/iPadOS
    - Configuration des applications gérées ciblées MAM Android

- Les types de stratégie MAM qui prennent pas en charge les ensembles de stratégies sont les suivants : 
    - Protection des applications gérées ciblées MAM WIP (Windows)

- MAM traite les affectations d’ensembles de stratégies en tant qu’affectations directes pour les types de stratégie suivants :
    - Protection des applications gérées ciblées MAM iOS/iPadOS
    - Protection des applications gérées ciblées par Android
    - Configuration des applications gérées ciblées MAM iOS/iPadOS
    - Configuration des applications gérées ciblées MAM Android

    Si une stratégie est ajoutée à un ensemble de stratégies déployé dans un groupe, celui-ci est indiqué comme étant directement affecté dans la charge de travail, et non « affecté via l’ensemble de stratégies ». Par conséquent, MAM ne traite pas les suppressions d’affectations de groupes provenant d’ensembles de stratégies.

- MAM ne prend pas en charge le déploiement dans les groupes virtuels **Tous les utilisateurs** et **Tous les appareils**, quel que soit le type de stratégie.

## <a name="next-steps"></a>Étapes suivantes

- [Inscrire des appareils dans Microsoft Intune](~/enrollment/index.yml).