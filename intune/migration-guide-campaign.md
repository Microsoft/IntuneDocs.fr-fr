---
title: Démarrer une campagne de migration Intune
titleSuffix: Microsoft Intune
description: Cet article donne des conseils pour lancer une campagne de migration Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5e409683c294b9d0321458f40c9b7f66bc3660ac
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046511"
---
# <a name="phase-2-migration-campaign"></a>Phase 2 : Campagne de migration

Choisissez l’approche de migration qui répond le mieux aux besoins de votre organisation et ajustez les stratégies d’implémentation en fonction de vos exigences spécifiques. Les autres sections de ce guide vous procurent les outils dont vous avez besoin pour atteindre votre objectif, à savoir inscrire les appareils de vos utilisateurs sur Intune.

## <a name="keys-to-a-successful-migration"></a>Garantir la réussite de la migration

Les conditions de la réussite d’une migration d’un fournisseur MDM tiers vers Intune sont les suivantes :

-   Une communication claire et utile peut limiter les temps d’arrêt et le mécontentement des utilisateurs finaux.

-   Veillez à proposer des instructions de migration spécifiques et concrètes.

-   Tous les appareils gérés doivent être désinscrits de votre fournisseur MDM existant avant de pouvoir être inscrits dans Intune.

-   Donnez des conseils aux utilisateurs finaux pour désinscrire leurs appareils du fournisseur MDM existant.

-   Utilisez une approche progressive. Commencez par un petit groupe d’utilisateurs pilotes, puis ajoutez des groupes supplémentaires de manière incrémentielle, jusqu’au niveau de déploiement à grande échelle.

-   Surveillez la charge du support technique et vérifiez que chaque inscription a abouti. Consacrez un certain temps à l’évaluation des critères de réussite pour chaque groupe avant de passer à la migration du groupe suivant. Votre déploiement pilote doit vérifier les points suivants :

    -   Les taux de réussite et d’échec des inscriptions sont inclus dans les plages prévues.

    -   Productivité des utilisateurs :

        -   Les ressources d’entreprise telles que le VPN, le Wi-Fi, la messagerie et les certificats fonctionnent correctement.

        -   Les applications configurées sont accessibles.

    -   Sécurité des données :

        -   Des rapports de conformité sont créés.

        -   Les protections pour applications mobiles sont appliquées.

Dès que vous êtes satisfait de la première phase de migration, répétez le [cycle de migration](migration-guide-cycle.md) pour la phase suivante.

-   Répétez chaque cycle progressif jusqu’à ce que tous les utilisateurs soient migrés vers Intune.

-   Vérifiez que l’équipe de support technique est prête à porter assistance aux utilisateurs finaux tout au long de la campagne de migration. Exécutez une migration volontaire, afin de pouvoir estimer la charge de travail liée aux appels de support.

-   Ne fixez pas d’échéances pour l’inscription tant que le support technique n’a pas pu prendre en charge tous les utilisateurs restants.

> [!IMPORTANT]
> Ne configurez pas Intune et votre solution MDM tierce de façon à appliquer des contrôles d’accès aux ressources telles que Microsoft Exchange ou SharePoint Online. En outre, les appareils doivent uniquement être inscrits auprès d’une solution à la fois.

## <a name="next-steps"></a>Étapes suivantes

Créez votre [plan de communication](migration-guide-communication-plan.md).
