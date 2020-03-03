---
title: Affecter des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le centre d’administration Microsoft Endpoint Manager pour attribuer des stratégies et des profils d’appareil aux utilisateurs et aux appareils. Découvrez comment exclure des groupes d’une affectation de profil dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6678c3fbc247ac0595775c0ccc72c7bdb9c55e1
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513093"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune

Vous créez un profil, et il inclut tous les paramètres que vous avez entrés. L’étape suivante consiste à déployer sur ou à « attribuer » le profil à vos utilisateurs ou groupes d’utilisateurs Azure Active Directory (Azure AD). Lorsqu’il est attribué, les utilisateurs et appareils reçoivent votre profil et les paramètres que vous avez entrés sont appliqués.

Cet article vous montre comment attribuer un profil et inclut des informations sur l’utilisation de balises d’étendue sur vos profils.

> [!NOTE]  
> Lorsqu'un profil est supprimé ou n'est plus attribué à un appareil, différents événements peuvent se produire, en fonction des paramètres du profil. Les paramètres sont basés sur des fournisseurs de services de configuration (CSP), et chaque CSP peut gérer différemment la suppression du profil. Par exemple, un paramètre peut conserver la valeur existante, et ne pas revenir à une valeur par défaut. Le comportement est contrôlé par chaque CSP dans le système d'exploitation. Pour obtenir une liste des fournisseurs de services de configuration (CSP) Windows, consultez la référence [Fournisseur de services de configuration (CSP) ](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).
>
> Pour attribuer à un paramètre une valeur différente, créez un nouveau profil, définissez le paramètre sur **Non configuré**, puis attribuez le profil. Une fois ce paramètre appliqué à l'appareil, l'utilisateur pourra attribuer au paramètre la valeur de son choix.
>
> Lors de la configuration de ces paramètres, nous suggérons de les déployer sur un groupe pilote. Pour plus de conseils sur le déploiement d'Intune, consultez [Créer un plan de déploiement](../fundamentals/planning-guide-rollout-plan.md).

## <a name="before-you-begin"></a>Avant de commencer

Veillez à disposer du rôle approprié pour affecter des profils. Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Attribuer un profil d’appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration**. Tous les profils sont répertoriés.
3. Sélectionnez le profil que vous souhaitez attribuer > **Affectations**.
4. Choisissez d’**Inclure** des groupes ou d’**Exclure** des groupes, puis sélectionnez vos groupes. Quand vous sélectionnez vos groupes, vous choisissez un groupe Azure AD. Pour sélectionner plusieurs groupes, maintenez la touche **Ctrl** enfoncée et sélectionnez vos groupes.

    ![Capture d’écran des options permettant d’inclure ou exclure des groupes dans une affectation de profil](./media/device-profile-assign/group-include-exclude.png)

5. **Enregistrez** les changements apportés.

### <a name="evaluate-how-many-users-are-targeted"></a>Évaluer le nombre d’utilisateurs ciblés

Lorsque vous attribuez le profil, vous pouvez également **évaluer** le nombre d’utilisateurs affectés. Cette fonctionnalité calcule les utilisateurs ; elle ne calcule pas les appareils.

1. Dans le centre d’administration, sélectionnez **Appareils** > **Profils de configuration**.
2. Sélectionnez un profil > **Affectations** > **Évaluer**. Un message vous indique le nombre d’utilisateurs ciblés par ce profil.

Si le bouton **Évaluer** est grisé, vérifiez que le profil est attribué à un ou plusieurs groupes.

## <a name="use-scope-tags-or-applicability-rules"></a>Utiliser des balises d’étendue ou des règles d'applicabilité

Lorsque vous créez ou mettez à jour un profil, vous pouvez également ajouter des balises d’étendue et des règles d’applicabilité au profil.

Les **balises d’étendue** sont un excellent moyen de filtrer des profils dans des groupes spécifiques, tels que `US-NC IT Team` et `JohnGlenn_ITDepartment`. [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée) fournit plus d’informations.

Sur les appareils Windows 10, vous pouvez ajouter des **règles d'applicabilité** afin que le profil ne s'applique qu'à une version spécifique du système d'exploitation ou à une édition Windows spécifique. Consultez [Règles de mise en application](device-profile-create.md#applicability-rules) pour plus d’informations.

## <a name="user-groups-vs-device-groups"></a>Groupes d’utilisateurs et groupes d’appareils

De nombreux utilisateurs demandent quand utiliser des groupes d’utilisateurs et quand utiliser des groupes d’appareils. La réponse dépend de votre objectif. Voici quelques conseils pour vous aider à démarrer.

### <a name="device-groups"></a>Groupes d'appareils

Si vous souhaitez appliquer des paramètres sur un appareil, quelle que soit la personne qui est connectée, affectez vos profils à un groupe d’appareils. Les paramètres appliqués aux groupes d’appareils sont toujours associés à l’appareil, et non à l’utilisateur.

Par exemple :

- Les groupes d’appareils sont utiles pour gérer les appareils qui n’ont pas d’utilisateur dédié. Par exemple, vous avez des appareils qui impriment des tickets, analysent l’inventaire, sont partagés par des employés lors de différents postes, sont attribués à un entrepôt spécifique, et ainsi de suite. Placez ces appareils dans un groupe d’appareils et affectez vos profils à ce groupe d’appareils.

- Vous créez un [profil d’interface de configuration du microprogramme d’appareil (DFCI) Intune](device-firmware-configuration-interface-windows.md) qui met à jour les paramètres dans le BIOS. Par exemple, vous configurez ce profil pour désactiver l’appareil photo ou verrouiller les options de démarrage pour empêcher les utilisateurs de démarrer un autre système d’exploitation. Ce profil est un bon scénario à attribuer à un groupe d’appareils.

- Sur certains appareils Windows spécifiques, vous devez toujours contrôler certains paramètres de Microsoft Edge, quel que soit l’utilisateur qui utilise l’appareil. Par exemple, vous souhaitez bloquer tous les téléchargements, limiter tous les cookies à la session de navigation active et supprimer l’historique de navigation. Pour ce scénario, placez ces appareils Windows spécifiques dans un groupe d’appareils. Ensuite, créez un [modèle d’administration dans Intune](administrative-templates-windows.md), ajoutez ces paramètres d’appareil, puis attribuez ce profil au groupe d’appareils.

Pour résumer, utilisez des groupes d’appareils lorsque vous ne vous souciez pas de la personne qui est connectée à l’appareil ou de si quelqu’un est connecté. Vous souhaitez que vos paramètres se trouvent toujours sur l’appareil.

### <a name="user-groups"></a>Groupes d’utilisateurs

Les paramètres de profil appliqués aux groupes d’utilisateurs sont toujours associés à l’utilisateur et s’appliquent lorsqu’il se connecte à ses nombreux appareils. Il est normal que les utilisateurs disposent de nombreux appareils, par exemple un Surface Pro pour le travail et un appareil iOS/iPadOS personnel. Et il est normal qu’une personne accède à la messagerie et aux autres ressources de l’organisation à partir de ces appareils.

Par exemple :

- Vous souhaitez placer une icône de support technique pour tous les utilisateurs sur tous leurs appareils. Dans ce scénario, placez ces utilisateurs dans un groupe d’utilisateurs et affectez votre profil d’icône de support technique à ce groupe d’utilisateurs.
- Un utilisateur reçoit un nouvel appareil appartenant à l’organisation. L’utilisateur se connecte à l’appareil avec son compte de domaine. L’appareil est automatiquement inscrit dans Azure AD et géré automatiquement par Intune. Ce profil est un bon scénario à attribuer à un groupe d’utilisateurs.
- Chaque fois qu’un utilisateur se connecte à un appareil, vous souhaitez contrôler les fonctionnalités dans des applications, comme OneDrive ou Office. Dans ce scénario, affectez vos paramètres de profil OneDrive ou Office à un groupe d’utilisateurs.

  Par exemple, vous souhaitez bloquer les contrôles ActiveX non fiables dans vos applications Office. Vous pouvez créer un [modèle d’administration dans Intune](administrative-templates-windows.md), configurer ce paramètre, puis affecter ce profil à un groupe d’utilisateurs.

Pour résumer, utilisez des groupes d’utilisateurs lorsque vous souhaitez que vos paramètres et règles soient toujours utilisés par l’utilisateur, quel que soit l’appareil qu’il utilise.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exclure des groupes d’une affectation de profil

Les profils de configuration d’appareils Intune permettent d’inclure des groupes dans l’affectation de profils et d’en exclure.

Il est recommandé de créer et d’affecter de profils propres aux groupes d’utilisateurs. Et créez et affectez différents profils propres à vos groupes d’appareils. Pour plus d’informations sur les groupes, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils](../fundamentals/groups-add.md).

Lorsque vous affectez vos profils, appuyez-vous sur le tableau suivant pour inclure et exclure des groupes. Les affectations prises en charge sont celles qui sont cochées :

![Options prises en charge : inclure des groupes dans une affectation de profil ou les en exclure](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Bon à savoir

- L’exclusion est prioritaire sur l’inclusion dans les scénarios « même type de groupe » suivants :

  - Inclure des groupes d’utilisateurs et exclure des groupes d’utilisateurs
  - Inclure des groupes d’appareils et exclure des groupes d’appareils

  Par exemple, vous pouvez attribuer un profil d’appareil au groupe d’utilisateurs de **tous les utilisateurs de l’entreprise**, mais exclure des membres du groupe d’utilisateurs des **cadres supérieurs**. Comme les deux groupes sont des groupes d’utilisateurs, **Tous les utilisateurs de l’entreprise** à l’exception de la **Direction** reçoivent le profil.

- Intune n’évalue pas les relations entre groupes d’utilisateurs et groupes d’appareils. Si vous affectez des profils à des groupes mixtes, les résultats risquent de ne pas correspondre à votre intention ou à vos attentes.

  Supposons par exemple que vous affectiez un profil d’appareil au groupe d’utilisateurs **Tous les utilisateurs**, mais que vous excluiez un groupe d’appareils **Tous les appareils personnels**. Dans cette affectation de profil de groupe mixte, **Tous les utilisateurs** reçoivent le profil. L’exclusion ne s’applique pas.

  Par conséquent, il n’est pas recommandé d’affecter des profils à des groupes mixtes.

## <a name="next-steps"></a>Étapes suivantes

Consultez [Surveiller les profils d’appareil](device-profile-monitor.md) pour obtenir des conseils sur la surveillance de vos profils et sur les appareils exécutant vos profils.
