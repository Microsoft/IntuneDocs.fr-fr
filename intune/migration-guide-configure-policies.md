---
title: Configurer la conformité des applications et des appareils durant une migration Intune
titlesuffix: Microsoft Intune
description: Cet article décrit les étapes nécessaires pour configurer des stratégies de gestion des applications et de conformité des appareils durant une migration Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1880d580a8719dcf72f54f9c22306bea001bc3b0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834568"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Configurer des stratégies de gestion des applications et de conformité lors de la migration vers Microsoft Intune

Durant la migration vers Intune, l’objectif principal consiste à assurer l’inscription de l’ensemble des appareils dans Intune et ce, dans le respect des stratégies en place. En effet, les stratégies de gestion des appareils vous permettent d’administrer les appareils d’entreprise d’un seul utilisateur, mais également les appareils personnels (BYOD) et partagés tels que les bornes, les terminaux de vente, les tablettes partagées par plusieurs étudiants ou les appareils sans utilisateur (iOS uniquement).

Chaque plate-forme d’appareil peut proposer des paramètres différents, mais les stratégies de gestion des appareils de Microsoft Intune fonctionnent avec chacune d’elles, en fournissant les fonctionnalités de gestion des appareils mobiles suivantes :

-   Régulation du nombre d’appareils inscrits par chaque utilisateur

-   Gestion des paramètres des appareils (par exemple : inscription au niveau de l’appareil, longueur du mot de passe, utilisation de l’appareil photo)

-   Fourniture d’applications, de profils d’e-mail et VPN, etc.

-   Évaluation des critères au niveau de l’appareil dans le cadre des stratégies de conformité de la sécurité

> [!IMPORTANT]
> Les stratégies de gestion des appareils ne sont pas directement affectées à des appareils ou utilisateurs individuels, mais plutôt à des groupes d’utilisateurs. Les stratégies peuvent être appliquées directement à un groupe d’utilisateurs et, de ce fait, à l’appareil d’un de ces utilisateurs. Cependant, vous pouvez aussi les appliquer à un groupe d’appareils et donc aux membres de ce groupe.

## <a name="task-list-for-device-compliance-policies"></a>Liste de tâches relatives aux stratégies de conformité des appareils

### <a name="task-1-add-device-groups-optional"></a>Tâche 1 : Ajouter des groupes d’appareils (facultatif)

Vous pouvez créer des groupes d’appareils quand vous devez exécuter des tâches d’administration en fonction de l’identité de l’appareil, et non de l’utilisateur.

Les groupes d’appareils sont utiles pour la gestion des appareils sans utilisateurs dédiés (comme des bornes, des appareils partagés par plusieurs employés ou des appareils affectés à un emplacement spécifique).

En configurant des groupes d’appareils avant l’inscription, vous pouvez utiliser des catégories d’appareils pour les ajouter automatiquement à des groupes au moment de l’inscription. Les appareils se voient ensuite affecter automatiquement les stratégies du groupe auxquels ils appartiennent. [Bien démarrer avec les groupes](groups-get-started.md)

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Tâche 2 : Utiliser des profils d’accès aux ressources (WiFi, VPN et certificats de messagerie)

Les profils d’accès aux ressources fournissent des certificats et des configurations d’accès aux appareils inscrits. Si vous utilisez l’authentification basée sur les certificats, [configurez des certificats](certificates-configure.md).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Tâche 3 : Créer et déployer des profils de configuration d’appareil

Vous devez créer un profil de configuration d’appareil pour appliquer des paramètres au niveau de ce dernier, par exemple la désactivation de l’appareil photo et de l’App Store, la configuration du mode d’application unique et de l’écran d’accueil, etc. Découvrez-en davantage sur [profils d’appareil](device-profiles.md).

####  <a name="directly-import-ios-configuration-profiles-optional"></a>Importer directement des profils de configuration iOS (facultatif)

-   **Profils iOS Apple Configurator (iOS 7.1 et versions ultérieures) :** si votre solution MDM utilise des profils Apple Configurator (fichiers .mobileconfig), Intune peut les importer directement comme stratégies de configuration personnalisées.

-   **Stratégies de configuration des applications mobiles iOS :** si votre solution MDM utilise des stratégies de configuration des applications mobiles iOS, Intune peut les importer directement, à condition que les listes de propriétés présentent le format XML spécifié par Apple.

- Découvrez comment ajouter une stratégie personnalisée pour [iOS](custom-settings-ios.md).

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Tâche 4 : Créer et déployer des stratégies de conformité des appareils (facultatif)

Les stratégies de conformité des appareils évaluent les paramètres axés sur la sécurité et fournissent des rapports qui indiquent si les appareils sont conformes aux normes de l’entreprise ou non. Parmi ces paramètres, citons les suivants :

-   Longueur du code PIN

-   Statut jailbreaké

-   Version du système d'exploitation

Consultez les ressources supplémentaires pour connaître les paramètres de conformité des appareils :

-   Découvrez plus d’informations sur les [stratégies de conformité des appareils](device-compliance.md).

-   Découvrez comment [créer une stratégie de conformité des appareils](device-compliance-get-started.md).

### <a name="task-5-publish-and-deploy-apps"></a>Tâche 5 : Publier et déployer des applications

Quand vous utilisez Intune MDM, vous pouvez fournir des applications en demandant leur installation automatique ou en les mettant à la disposition des utilisateurs sur le portail d’entreprise.

-   [Guide pratique pour ajouter des applications](apps-add.md)

-   [Guide pratique pour déployer des applications](apps-deploy.md)

### <a name="task-6-enable-device-enrollment"></a>Tâche 6 : Activer l’inscription d’appareil

Pour gérer un appareil, vous devez l’inscrire. Découvrez comment [inscrire des appareils d’entreprise et personnels](device-enrollment.md).

## <a name="next-steps"></a>Étapes suivantes

[Configurer des stratégies de protection des applications (facultatif)](migration-guide-app-protection-policies.md)
