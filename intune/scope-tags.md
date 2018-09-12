---
title: Filtrer les stratégies avec des étiquettes de délimitation dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des étiquettes de délimitation pour filtrer les profils de configuration de manière à n’afficher que certains rôles.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 000505df3c0898ed0939244dfe1b075c64097611
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329425"
---
# <a name="use-scope-tags-to-filter-policies"></a>Utiliser des étiquettes de délimitation pour filtrer les stratégies

Les étiquettes de délimitation vous permettent de filtrer les stratégies avec des étiquettes que vous personnalisez.

Par exemple, créez une étiquette de délimitation appelée « Service Ingénierie », puis affectez-la aux profils de configuration liés au service d’ingénierie. Affectez cette même étiquette à un rôle « Administrateurs Ingénierie ». Ceux-ci verront uniquement les stratégies avec l’étiquette « Département Ingénierie ».

## <a name="to-create-a-scope-tag"></a>Pour créer une étiquette de délimitation

Choisissez **Rôles** > **Délimitation (étiquettes)** > **Créer**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Pour ajouter une étiquette de délimitation à un profil de configuration

Choisissez **Configuration de l’appareil** > **Profils** > choisissez un profil > **Propriétés** > **Délimitation (étiquettes)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Pour affecter une étiquette de délimitation à un rôle

Choisissez **Rôles** > **Tous les rôles** > **Policy and Profile Manager (Gestionnaire des stratégies et des profils)** > **Affectations** > **Délimitation (étiquettes)**.

## <a name="next-steps"></a>Étapes suivantes

Gérez vos [rôles](role-based-access-control.md) et vos [profils](device-profile-assign.md).

