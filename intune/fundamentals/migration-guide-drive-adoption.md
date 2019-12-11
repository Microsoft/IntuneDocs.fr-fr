---
title: Encourager l’adoption par les utilisateurs finaux avec l’accès conditionnel
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser l’accès conditionnel pour encourager les inscriptions dans Microsoft Intune.
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
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 115313816542fd642e6a0c67900abd48b7146e42
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510069"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Encourager l’adoption par les utilisateurs finaux avec l’accès conditionnel dans Microsoft Intune

En activant les fonctionnalités d’accès conditionnel avec Intune (par exemple, le blocage des e-mails sur les appareils non inscrits), vous pouvez encourager l’inscription des appareils et leur mise en conformité. Toutefois, ce n’est pas nécessaire pour assurer la réussite de la migration. En effet, ce sont les objectifs relatifs à l’adoption et les exigences en matière de sécurité qui déterminent sa réussite.

## <a name="migration-campaign-with-conditional-access"></a>Campagne de migration avec accès conditionnel

Voici une méthode d’amélioration classique des campagnes de migration avec accès conditionnel :

1. Définissez les règles d’accès conditionnel à appliquer pour tous les utilisateurs, mais excluez spécifiquement ceux qui doivent effectuer la migration depuis l’ancien fournisseur MDM. Vous pouvez créer un groupe d’utilisateurs Azure AD, qui rassemble tous les utilisateurs exclus avec accès conditionnel.

2. À mesure que les utilisateurs migrent, supprimez-les du groupe des utilisateurs exclus de l’accès conditionnel.

3. Une fois la migration terminée, configurez toutes les stratégies d’accès conditionnel de manière à appliquer un blocage par défaut, sauf si Intune autorise l’accès.

### <a name="advantages"></a>Avantages

- Propose un contrôle d’accès pour les nouveaux comptes d’utilisateur, ou ceux qui n’ont pas été gérés par la précédente solution.

- Propose aux utilisateurs une période de grâce pour la migration depuis la solution précédente.

- Minimise les pertes de productivité.

### <a name="disadvantages"></a>Inconvénients

- Les utilisateurs de la solution précédente avaient la possibilité d’accéder aux ressources à l’aide d’appareils non gérés tant que l’accès conditionnel n’était pas activé pour ces utilisateurs.


Il s’agit d’une approche parmi d’autres. Vous pouvez choisir un processus plus simple, qui diffère tout accès conditionnel jusqu’à la fin de chaque phase de l’inscription, ou mettre en place un procédé plus strict, qui applique l’accès conditionnel dès le départ et requiert une conformité complète pour tout accès.

- En savoir plus sur l'[accès conditionnel](../protect/conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Liste de tâches relatives à l’accès conditionnel

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Tâche 1 : Définir la façon dont vous allez implémenter l’accès conditionnel

[Utilisations courantes de l’accès conditionnel](../protect/conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>Tâche 2 : Configurer l’accès conditionnel Intune

Choisissez l'une des options suivantes :

- [Configurer l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [Installer le connecteur Exchange local avec Intune](../protect/exchange-connector-install.md)

- [Configurer les stratégies d’accès conditionnel basé sur l’application pour Exchange Online](../protect/app-based-conditional-access-intune-create.md)

- [Configurer des stratégies d’accès conditionnel basé sur l’application pour SharePoint Online](../protect/app-based-conditional-access-intune-create.md)

- [Bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL)](../protect/app-modern-authentication-block.md)

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur le [cycle de migration classique](../migration-guide-cycle.md).
