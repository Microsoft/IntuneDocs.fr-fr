---
title: Affecter des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le portail Azure pour affecter des stratégies et des profils d’appareils à des utilisateurs et des appareils. Découvrez comment exclure des groupes d’une affectation de profil dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344ffdfefd8b354c9d2ab31f2d08c2a25456f970
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724111"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous créez un profil, et il inclut tous les paramètres que vous avez entrés. L’étape suivante consiste à déployer sur ou à « attribuer » le profil à vos utilisateurs ou groupes d’utilisateurs Azure Active Directory (Azure AD). Lorsqu’il est attribué, les utilisateurs et appareils reçoivent votre profil et les paramètres que vous avez entrés sont appliqués.

Cet article vous montre comment attribuer un profil et inclut des informations sur l’utilisation de balises d’étendue sur vos profils.

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

Les profils de configuration d’appareil Intune vous permettent d’exclure des groupes de l’attribution de stratégie.

Intune ne prend pas en compte les relations de groupe utilisateur-à-appareil. L’inclusion de groupes d’utilisateurs tout en excluant des groupes d’appareils peut ne pas aboutir aux résultats voulus. Dans les scénarios groupe d’utilisateurs-à-groupe d’utilisateurs et groupe d'appareils-à-groupe d’appareils, l'exclusion prime sur l'inclusion.

Par exemple, vous pouvez attribuer un profil d’appareil au groupe d’utilisateurs de **tous les utilisateurs de l’entreprise**, mais exclure des membres du groupe d’utilisateurs des **cadres supérieurs**. Étant donné que les deux groupes sont des groupes d'utilisateurs, tous les membres du groupe **Cadres supérieurs** sont exclus de la stratégie, même s'ils sont membres du groupe **Tous les utilisateurs de l'entreprise**.

L'inclusion prime sur l'exclusion lorsqu'on utilise des groupes mixtes, par exemple une relation groupe d'utilisateurs-à-groupe d’appareils, ou groupe d'appareils-à-groupe d’utilisateurs.

Par exemple, vous souhaitez attribuer un profil d’appareil à tous les utilisateurs de votre organisation, à l’exception des bornes. Vous incluez le groupe **Tous les utilisateurs**, mais excluez le groupe **Tous les appareils**. Dans ce cas, tous les utilisateurs et leurs appareils obtiennent la stratégie, même si l’appareil de l’utilisateur se trouve dans le groupe **Tous les appareils**.

L’exclusion examine uniquement les membres directs du groupe. Elle n’inclut pas les appareils associés à un utilisateur. Toutefois, les appareils qui n’ont pas d’utilisateur n’obtiennent pas la stratégie. Ce comportement se produit car les appareils sans utilisateurs n’ont aucune relation au groupe **Tous les utilisateurs**.

Si vous incluez **Tous les appareils** et que vous excluez **Tous les utilisateurs**, tous les appareils reçoivent alors la stratégie. Dans ce scénario, le but est d’exclure les appareils associés à un utilisateur de cette stratégie. Toutefois, les appareils ne sont pas exclus car l’exclusion ne compare que les membres directs des groupes.

## <a name="next-steps"></a>Étapes suivantes

Consultez [Surveiller les profils d’appareil](device-profile-monitor.md) pour obtenir des conseils sur la surveillance de vos profils et sur les appareils exécutant vos profils.
