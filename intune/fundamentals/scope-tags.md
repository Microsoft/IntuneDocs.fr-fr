---
title: Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour les distribuer dans Intune | Microsoft Docs
description: Utilisez des étiquettes de délimitation pour filtrer les profils de configuration de manière à n’afficher que certains rôles.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1f81d26227bb206aa55ca495f4a4ee5e8ae9907
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548129"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée

Vous pouvez utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour garantir que les administrateurs ont la visibilité et l’accès appropriés pour les bons objets Intune. Les rôles déterminent quel accès ont les administrateurs sur quels objets. Les balises d’étendue déterminent quels objets les administrateurs peuvent voir.

Par exemple, supposons que l’administrateur d’un bureau régional de Seattle a le rôle de gestionnaire de stratégie et de profil. Vous voulez que cet administrateur voie et gère seulement les profils et les stratégies qui s’appliquent uniquement aux appareils de Seattle. Pour configurer cet accès, vous pouvez :

1. Créer une balise d’étendue nommée Seattle.
2. Créer une attribution de rôle pour le rôle de gestionnaire de stratégie et de profil avec : 
    - Membres (Groupes) = un groupe de sécurité nommé Administrateurs informatiques Seattle. Tous les administrateurs de ce groupe disposent des autorisations pour gérer les stratégies et les profils des utilisateurs/appareils dans Étendue (Groupes).
    - Étendue (Groupes) = un groupe de sécurité nommé Utilisateurs Seattle. Les profils et les stratégies de tous les utilisateurs/appareils de ce groupe peuvent être gérés par les administrateurs de Membres (Groupes). 
    - Étendue (balises) = Seattle. Les administrateurs dans Membre (Groupes) peuvent voir des objets Intune qui ont également la balise d’étendue Seattle.
3. Ajoutez la balise d’étendue Seattle aux stratégies et aux profils auxquels vous voulez que les administrateurs de Membres (Groupes) aient accès.
4. Ajoutez la balise d’étendue Seattle aux appareils que vous voulez rendre visibles par les administrateurs de Membres (Groupes). 

## <a name="default-scope-tag"></a>Balise d’étendue par défaut
La balise d’étendue par défaut est automatiquement ajoutée à tous les objets non balisés qui prennent en charge les balises d’étendue.

La fonctionnalité de balise d’étendue par défaut est similaire à la fonctionnalité d’étendues de sécurité de Microsoft Endpoint Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>Pour créer une étiquette de délimitation

1. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **administration du locataire** > **rôles** > **étendue (balises)**  > **créer**.

    ![Capture d’écran de la création d’une balise d’étendue](./media/scope-tags/create-scope-tag.png)

2. Indiquez un **nom** et éventuellement une **description**.
3. Si vous souhaitez que tous les appareils se trouvent dans des groupes spécifiques, choisissez **attribuer une étiquette d’étendue à tous les appareils dans les groupes sélectionnés**.
    1. Dans la page **Sélectionner les groupes à inclure** , choisissez les groupes contenant les appareils auxquels vous souhaitez affecter cette balise d’étendue.
    2. Choisissez **Sélectionner**.
4. Choisissez **Créer**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Pour affecter une étiquette de délimitation à un rôle

1. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **administration du locataire** > **rôles** > **tous les rôles** > choisissez un rôle > **affectations** > **attribuer**.
2. Spécifiez un **Nom de l’affectation** et une **Description**.
3. Choisissez **Membres (Groupes)**  > **Ajouter** > choisissez les groupes dont vous souhaitez qu’ils fassent partie de cette affectation > **Sélectionner** >  **OK**. Les utilisateurs de ce groupe sont autorisés à gérer des utilisateurs/appareils dans l’étendue (groupes).

    ![Capture d’écran de la sélection de groupes de membres](./media/scope-tags/select-member-groups.png)

4. Si vous voulez gérer les utilisateurs/appareils dans un ensemble spécifique de groupes, choisissez **Étendue (Groupes)**  > **Groupes sélectionnés** > **Sélectionner les groupes à inclure** > choisissez les groupes > **Sélectionner** > **OK**. Tous les utilisateurs/appareils de ce groupe seront gérés par les administrateurs dans les membres (groupe).

    ![Capture d’écran de la sélection de groupes de l’étendue](./media/scope-tags/select-scope-groups.png)

    Vous pouvez aussi choisir **Tous les appareils**, **Tous les utilisateurs** ou **Tous les utilisateurs et tous les appareils**.

    ![Capture d’écran d’autres options pour la sélection de groupes de l’étendue.](./media/scope-tags/scope-group-other-options.png)
    
5. Choisissez **Étendue (balises)**  > **Ajouter** > choisissez les balises que vous voulez ajouter à ce rôle > **Sélectionner** > **OK**. Les utilisateurs des membres (groupes) auront accès aux objets Intune qui ont également la même balise d’étendue.

    ![Capture d’écran de la sélection de balises d’étendue](./media/scope-tags/select-scope-tags.png)

6. Choisissez **OK**. 

## <a name="assign-scope-tags-to-other-objects"></a>Affecter des balises d’étendue à d’autres objets

Pour les objets qui prennent en charge les balises d’étendue, les balises d’étendue apparaissent généralement sous **Propriétés**. Par exemple, pour affecter une étiquette d’étendue à un profil de configuration, procédez comme suit :

1. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **appareils** > **profils de configuration** > Choisissez un profil.

2. Choisissez **Propriétés** > **Étendue (balises)**  > **Ajouter**.

    ![Capture d’écran de l’ajout de balises d’étendue](./media/scope-tags/add-scope-tags.png)

3. Sous **Sélectionner des balises**, choisissez les balises que vous voulez ajouter au profil.
4. Choisissez **Sélectionner** > **OK** > **Enregistrer**.


## <a name="scope-tag-details"></a>Informations détaillées sur les balises d’étendue
Quand vous utilisez des balises d’étendue, rappelez-vous de ceci : 

- Vous pouvez assigner des balises d’étendue à un type d’objet Intune si le locataire peut avoir plusieurs versions de cet objet (telles que des attributions de rôles ou des applications).
  Les objets Intune suivants sont des exceptions à cette règle et ne prennent actuellement pas en charge les balises d’étendue :
    - Profils Windows ESP
    - Catégories d'appareils
    - Restrictions d'inscription
    - Identificateurs d’appareils Corp
    - Appareils AutoPilot
    - Emplacements de conformité des appareils
    - Appareils JAMF
- Les applications VPP et les livres électroniques associés au jeton VPP héritent des balises d’étendue affectées au jeton VPP associé.
- Les appareils Programme d’inscription des appareils (DEP) et les profils DEP associés au jeton DEP héritent des balises d’étendue affectées au jeton DEP associé.
- Quand un administrateur crée un objet dans Intune, toutes les balises d’étendue affectées à cet administrateur sont automatiquement affectées au nouvel objet.
- Le contrôle d’accès en fonction du rôle (RBAC) d’Intune ne s’applique pas aux rôles Azure Active Directory. Ainsi, les rôles Administrateur de service et Administrateur général d’Intune ont un accès d’administrateur complet à Intune, quelles que soient leurs balises d’étendue.
- Si une attribution de rôle n’a pas de balise d’étendue, l’administrateur informatique peut voir tous les objets en fonction des autorisations des administrateurs informatiques. Les administrateurs qui n’ont pas de balises d’étendue possèdent essentiellement toutes les balises d’étendue.
- Vous pouvez affecter seulement une balise d’étendue que vous avez dans vos attributions de rôles.
- Vous pouvez cibler seulement des groupes qui sont listés dans l’étendue (groupes) de votre attribution de rôle.
- Si une balise d’étendue est affectée à votre rôle, vous ne pouvez pas supprimer toutes les balises d’étendue sur un objet Intune. Au moins une balise d’étendue est obligatoire.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment les balises d’étendue se comportent lorsqu’il existe [plusieurs attributions de rôles](role-based-access-control.md#multiple-role-assignments).
Gérez vos [rôles](role-based-access-control.md) et vos [profils](../configuration/device-profile-assign.md).
