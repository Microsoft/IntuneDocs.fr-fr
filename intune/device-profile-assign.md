---
title: Affecter des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le portail Azure pour affecter des stratégies et des profils d’appareils à des utilisateurs et des appareils. Découvrez comment exclure des groupes d’une affectation de profil dans Microsoft InTune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f489f4d53fde988dd9ce8c7c4cc61cbded701fc4
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841213"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Affecter des profils d’utilisateur et d’appareil dans Microsoft Intune

Après avoir créé un profil, vous pouvez l’affecter à des groupes Azure Active Directory (Azure AD).

## <a name="assign-a-device-profile"></a>Attribuer un profil d’appareil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, puis recherchez **Microsoft Intune**.
2. Dans **Microsoft Intune**, sélectionnez **Configuration de l’appareil**, puis **Profils**.
3. Dans la liste des profils, sélectionnez celui à affecter, puis sélectionnez **Affectations**.
4. Choisissez d’**Inclure** des groupes ou d’**Exclure** des groupes, puis sélectionnez des groupes.  

    ![Capture d’écran des options permettant d’inclure ou exclure des groupes dans une affectation de profil](./media/group-include-exclude.png)

5. Quand vous sélectionnez vos groupes, vous choisissez un groupe Azure AD. Pour sélectionner plusieurs groupes, maintenez la touche **Ctrl** enfoncée.
6. Une fois ces opérations effectuées, sélectionnez **Enregistrer**.

## <a name="exclude-groups-from-a-profile-assignment"></a>Exclure des groupes d’une affectation de profil

Les profils de configuration d’appareil Intune vous permettent d’exclure des groupes de l’attribution de stratégie. Par exemple, vous pouvez attribuer un profil d’appareil au groupe de **tous les utilisateurs de l’entreprise**, mais exclure des membres du groupe des **cadres supérieurs**.

Quand vous excluez des groupes d’une affectation, excluez uniquement des utilisateurs ou uniquement des groupes d’appareils (pas un mélange de groupes). Intune ne traite pas les relations utilisateur à appareil. L’inclusion de groupes d’utilisateurs tout en excluant des groupes d’appareils peut ne pas aboutir aux résultats voulus. En cas d’utilisation de groupes mixtes ou en présence d’autres conflits, l’inclusion est prioritaire sur l’exclusion.

Par exemple, vous souhaitez attribuer un profil d’appareil à tous les appareils de votre organisation, à l’exception des bornes. Vous incluez le groupe **Tous les utilisateurs**, mais excluez le groupe **Tous les appareils**. Dans ce cas, tous les utilisateurs et leurs appareils obtiennent la stratégie, même si l’appareil de l’utilisateur fait partie du groupe **Tous les appareils**.

L’exclusion examine uniquement les membres directs des groupes et n’inclut pas les appareils qui sont associés à un utilisateur. Toutefois, les appareils qui n’ont pas d’utilisateur n’obtiennent pas la stratégie. En effet, ces appareils n’ont aucune relation au groupe **Tous les utilisateurs**.

Si vous incluez **Tous les appareils** et que vous excluez **Tous les utilisateurs**, tous les appareils reçoivent alors la stratégie. Dans ce scénario, le but est d’exclure les appareils associés à un utilisateur de cette stratégie. Toutefois, les appareils ne sont pas exclus car l’exclusion ne compare que les membres directs des groupes.

## <a name="next-steps"></a>Étapes suivantes
Pour obtenir de l’aide sur la surveillance des attributions de profils d’appareils, consultez [Guide pratique pour surveiller des profils d’appareils](device-profile-monitor.md).
