---
title: Affecter des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le portail Azure pour affecter des stratégies et des profils d’appareils à des utilisateurs et des appareils. Découvrez comment exclure des groupes d’une affectation de profil dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2019
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
ms.openlocfilehash: a19515e859f5e78f7611bbd10088aea5f7c44650
ms.sourcegitcommit: f12bd2ce10b6241715bae2d2857f33c474287166
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72892630"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous créez un profil, et il inclut tous les paramètres que vous avez entrés. L’étape suivante consiste à déployer sur ou à « attribuer » le profil à vos utilisateurs ou groupes d’utilisateurs Azure Active Directory (Azure AD). Lorsqu’il est attribué, les utilisateurs et appareils reçoivent votre profil et les paramètres que vous avez entrés sont appliqués.

Cet article vous montre comment attribuer un profil et inclut des informations sur l’utilisation de balises d’étendue sur vos profils.

> [!NOTE]  
> Lorsqu’une stratégie est supprimée ou n’est plus affectée à un appareil, le paramètre peut conserver la valeur existante. Le paramètre ne reprend pas une valeur par défaut. Pour modifier le paramètre sur une autre valeur, créez une nouvelle stratégie et affectez-la.

## <a name="before-you-begin"></a>Avant de commencer

Veillez à disposer du rôle approprié pour affecter des stratégies. Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="assign-a-device-profile"></a>Attribuer un profil d’appareil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils**. Tous les profils sont répertoriés.
3. Sélectionnez le profil que vous souhaitez attribuer > **Affectations**.
4. Choisissez d’**Inclure** des groupes ou d’**Exclure** des groupes, puis sélectionnez vos groupes. Quand vous sélectionnez vos groupes, vous choisissez un groupe Azure AD. Pour sélectionner plusieurs groupes, maintenez la touche **Ctrl** enfoncée et sélectionnez vos groupes.

    ![Capture d’écran des options permettant d’inclure ou exclure des groupes dans une affectation de profil](./media/device-profile-assign/group-include-exclude.png)

5. **Enregistrez** les changements apportés.

### <a name="evaluate-how-many-users-are-targeted"></a>Évaluer le nombre d’utilisateurs ciblés

Lorsque vous attribuez le profil, vous pouvez également **évaluer** le nombre d’utilisateurs affectés. Cette fonctionnalité calcule les utilisateurs ; elle ne calcule pas les appareils.

1. Dans Intune, sélectionnez **Configuration de l’appareil** > **Profils**.
2. Sélectionnez un profil > **Affectations** > **Évaluer**. Un message vous indique le nombre d’utilisateurs ciblés par ce profil.

Si le bouton **Évaluer** est grisé, vérifiez que le profil est attribué à un ou plusieurs groupes.

## <a name="use-scope-tags-or-applicability-rules"></a>Utiliser des balises d’étendue ou des règles d'applicabilité

Lorsque vous créez ou mettez à jour un profil, vous pouvez également ajouter des balises d’étendue et des règles d’applicabilité au profil.

Les **balises d’étendue** permettent d’attribuer et de filtrer les stratégies à des groupes spécifiques, tels que les ressources humaines ou tous les employés US-NC. [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée) fournit plus d’informations.

Sur les appareils Windows 10, vous pouvez ajouter des **règles d'applicabilité** afin que le profil ne s'applique qu'à une version spécifique du système d'exploitation ou à une édition Windows spécifique. Consultez [Règles de mise en application](device-profile-create.md#applicability-rules) pour plus d’informations.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exclure des groupes d’une affectation de profil

Les profils de configuration d’appareils Intune permettent d’inclure des groupes dans l’affectation de stratégies et d’en exclure.

Il est recommandé de créer et d’affecter des stratégies propres aux groupes d’utilisateurs, et d’autres stratégies propres aux groupes d’appareils. Pour plus d’informations sur les groupes, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils](../fundamentals/groups-add.md).

Lorsque vous affectez vos stratégies, appuyez-vous sur le tableau suivant pour inclure et exclure des groupes. Les affectations prises en charge sont celles qui sont cochées :

![Options prises en charge : inclure des groupes dans une affectation de profil ou les en exclure](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>Bon à savoir

- L’exclusion est prioritaire sur l’inclusion dans les scénarios « même type de groupe » suivants :

  - Inclure des groupes d’utilisateurs et exclure des groupes d’utilisateurs
  - Inclure des groupes d’appareils et exclure des groupes d’appareils

  Par exemple, vous pouvez attribuer un profil d’appareil au groupe d’utilisateurs de **tous les utilisateurs de l’entreprise**, mais exclure des membres du groupe d’utilisateurs des **cadres supérieurs**. Comme les deux groupes sont des groupes d’utilisateurs, **Tous les utilisateurs de l’entreprise** à l’exception de la **Direction** reçoivent la stratégie.

- Intune n’évalue pas les relations entre groupes d’utilisateurs et groupes d’appareils. Si vous affectez des stratégies à des groupes mixtes, les résultats risquent de ne pas correspondre à votre intention ou à vos attentes.

  Supposons par exemple que vous affectiez un profil d’appareil au groupe d’utilisateurs **Tous les utilisateurs**, mais que vous excluiez un groupe d’appareils **Tous les appareils personnels**. Dans cette affectation de stratégie de groupe mixte, **Tous les utilisateurs** reçoivent la stratégie. L’exclusion ne s’applique pas.

  Par conséquent, il n’est pas recommandé d’affecter des stratégies à des groupes mixtes.

## <a name="next-steps"></a>Étapes suivantes

Consultez [Surveiller les profils d’appareil](device-profile-monitor.md) pour obtenir des conseils sur la surveillance de vos profils et sur les appareils exécutant vos profils.
