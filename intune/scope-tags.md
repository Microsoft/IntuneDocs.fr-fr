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
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0da6861b6c49fc37691b8c6e464a506670643fa3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203329"
---
# <a name="use-scope-tags-to-filter-policies"></a>Utiliser des étiquettes de délimitation pour filtrer les stratégies

Les étiquettes de délimitation vous permettent de filtrer les stratégies avec des étiquettes que vous personnalisez. Vous pouvez appliquer des étiquettes de délimitation aux rôles et aux applications.

Par exemple, créez une étiquette de délimitation appelée « Service Ingénierie », puis affectez-la aux profils de configuration liés au service d’ingénierie. Affectez cette même étiquette à un rôle « Administrateurs Ingénierie ». Ceux-ci verront uniquement les stratégies avec l’étiquette « Département Ingénierie ».

## <a name="to-create-a-scope-tag"></a>Pour créer une étiquette de délimitation

Choisissez **Rôles** > **Délimitation (étiquettes)** > **Créer**.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Pour ajouter une étiquette de délimitation à un profil de configuration

Choisissez **Configuration de l’appareil** > **Profils** > choisissez un profil > **Propriétés** > **Délimitation (étiquettes)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Pour affecter une étiquette de délimitation à un rôle

Choisissez **Rôles** > **Tous les rôles** > **Policy and Profile Manager (Gestionnaire des stratégies et des profils)** > **Affectations** > **Délimitation (étiquettes)**.

## <a name="to-assign-a-scope-tag-to-an-app"></a>Pour affecter une étiquette de délimitation à une application

Choisissez **Applications clientes** > **Applications** > choisissez une application > **Propriétés** > **Étendue (balises)** > **Ajouter** > choisissez les étiquettes > **Sélectionner** > **OK** > **Enregistrer**.


## <a name="next-steps"></a>Étapes suivantes

Gérez vos [rôles](role-based-access-control.md) et vos [profils](device-profile-assign.md).

