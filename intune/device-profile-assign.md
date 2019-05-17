---
title: Affecter des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le portail Azure pour affecter des stratégies et des profils d’appareils à des utilisateurs et des appareils. Découvrez comment exclure des groupes d’une affectation de profil dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c950efdd95fd8d856ec677385712a022dead870
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570505"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous créez un profil, et il inclut tous les paramètres que vous avez entrés. L’étape suivante consiste à déployer sur ou à « attribuer » le profil à vos utilisateurs ou groupes d’utilisateurs Azure Active Directory (Azure AD). Lorsqu’il est attribué, les utilisateurs et appareils reçoivent votre profil et les paramètres que vous avez entrés sont appliqués.

Cet article vous montre comment attribuer un profil et inclut des informations sur l’utilisation de balises d’étendue sur vos profils.

## <a name="assign-a-device-profile"></a>Attribuer un profil d’appareil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils**. Tous les profils sont répertoriés.
3. Sélectionnez le profil que vous souhaitez attribuer > **Affectations**.
4. Choisissez d’**Inclure** des groupes ou d’**Exclure** des groupes, puis sélectionnez vos groupes. Quand vous sélectionnez vos groupes, vous choisissez un groupe Azure AD. Pour sélectionner plusieurs groupes, maintenez la touche **Ctrl** enfoncée et sélectionnez vos groupes.

    ![Capture d’écran des options permettant d’inclure ou exclure des groupes dans une affectation de profil](./media/group-include-exclude.png)

5. **Enregistrez** les changements apportés.

### <a name="evaluate-how-many-users-are-targeted"></a>Évaluer le nombre d’utilisateurs ciblés

Lorsque vous attribuez le profil, vous pouvez également **évaluer** le nombre d’utilisateurs affectés. Cette fonctionnalité calcule les utilisateurs ; elle ne calcule pas les appareils.

1. Dans Intune, sélectionnez **Configuration de l’appareil** > **Profils**.
2. Sélectionnez un profil > **Affectations** > **Évaluer**. Un message vous indique le nombre d’utilisateurs ciblés par ce profil.

Si le bouton **Évaluer** est grisé, vérifiez que le profil est attribué à un ou plusieurs groupes.


## <a name="use-scope-tags"></a>Utiliser des balises d’étendue

Lorsque vous créez ou mettez à jour un profil, vous pouvez également ajouter des balises d’étendue au profil.

Les **balises d’étendue** permettent d’attribuer et de filtrer les stratégies à des groupes spécifiques, tels que les ressources humaines ou tous les employés US-NC. [Use RBAC and scope tags for distributed IT](scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée) fournit plus d’informations.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exclure des groupes d’une affectation de profil

Les profils de configuration d’appareil Intune vous permettent d’exclure des groupes de l’attribution de stratégie. Par exemple, vous pouvez attribuer un profil d’appareil au groupe de **tous les utilisateurs de l’entreprise**, mais exclure des membres du groupe des **cadres supérieurs**.

Lorsque vous excluez des groupes, excluez uniquement des utilisateurs ou uniquement des groupes d’appareils (pas un mélange de groupes) d’une affectation, Intune ne traite pas les relations utilisateur à appareil. L’inclusion de groupes d’utilisateurs tout en excluant des groupes d’appareils peut ne pas aboutir aux résultats voulus. Lorsque vous utilisez des groupes mixtes, ou en présence d’autres conflits, l’inclusion est prioritaire sur l’exclusion.

Par exemple, vous souhaitez attribuer un profil d’appareil à tous les appareils de votre organisation, à l’exception des bornes. Vous incluez le groupe **Tous les utilisateurs**, mais excluez le groupe **Tous les appareils**. Dans ce cas, tous les utilisateurs et leurs appareils obtiennent la stratégie, même si l’appareil de l’utilisateur se trouve dans le groupe **Tous les appareils**.

L’exclusion examine uniquement les membres directs du groupe. Elle n’inclut pas les appareils associés à un utilisateur. Toutefois, les appareils qui n’ont pas d’utilisateur n’obtiennent pas la stratégie. En effet, ces appareils n’ont aucune relation au groupe **Tous les utilisateurs**.

Si vous incluez **Tous les appareils** et que vous excluez **Tous les utilisateurs**, tous les appareils reçoivent alors la stratégie. Dans ce scénario, le but est d’exclure les appareils associés à un utilisateur de cette stratégie. Toutefois, les appareils ne sont pas exclus car l’exclusion ne compare que les membres directs des groupes.

## <a name="next-steps"></a>Étapes suivantes

Consultez [Surveiller les profils d’appareil](device-profile-monitor.md) pour obtenir des conseils sur la surveillance de vos profils et sur les appareils exécutant vos profils.