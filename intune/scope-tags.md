---
title: Filtrer les stratégies avec des étiquettes de délimitation dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des étiquettes de délimitation pour filtrer les profils de configuration de manière à n’afficher que certains rôles.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 627899eafb2175b2d3034045bd765a10f4a203d6
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882502"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée

Vous pouvez utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour garantir que les administrateurs ont la visibilité et l’accès appropriés pour les bons objets Intune. Les rôles déterminent quel accès ont les administrateurs sur quels objets. Les balises d’étendue déterminent quels objets les administrateurs peuvent voir.

Par exemple, supposons que le rôle de gestionnaire de stratégie et de profil est attribué à l’administrateur d’un bureau régional de Seattle. Vous voulez que cet administrateur voie et gère seulement les profils et les stratégies qui s’appliquent uniquement aux appareils de Seattle. Pour cela, vous devez :

1. Créer une balise d’étendue nommée Seattle.
2. Créer une attribution de rôle pour le rôle de gestionnaire de stratégie et de profil avec : 
    - Membres (Groupes) = un groupe de sécurité nommé Administrateurs informatiques Seattle. Tous les administrateurs de ce groupe disposent des autorisations pour gérer les stratégies et les profils des utilisateurs/appareils dans Étendue (Groupes).
    - Étendue (Groupes) = un groupe de sécurité nommé Utilisateurs Seattle. Les profils et les stratégies de tous les utilisateurs/appareils de ce groupe peuvent être gérés par les administrateurs de Membres (Groupes). 
    - Étendue (balises) = Seattle. Les administrateurs dans Membre (Groupes) peuvent voir les appareils qui ont également la balise d’étendue Seattle.
3. Ajoutez la balise d’étendue Seattle aux stratégies et aux profils auxquels vous voulez que les administrateurs de Membres (Groupes) puissent accéder.
4. Ajoutez la balise d’étendue Seattle aux appareils que vous voulez rendre visibles par les administrateurs de Membres (Groupes). 


## <a name="to-create-a-scope-tag"></a>Pour créer une étiquette de délimitation

1. Dans Intune, Choisissez **Rôles** > **Étendue (balises)**  > **Créer**.

    ![Capture d’écran de la création d’une balise d’étendue](./media/scope-tags/create-scope-tag.png)

3. Si vous souhaitez que tous les appareils se trouvent dans des groupes spécifiques, choisissez **attribuer une étiquette d’étendue à tous les appareils dans les groupes sélectionnés**.
    1. Dans la page **Sélectionner les groupes à inclure** , choisissez les groupes contenant les appareils auxquels vous souhaitez affecter cette balise d’étendue.
    2. Choisissez **Sélectionner**.
4. Choisissez **Créer**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Pour affecter une étiquette de délimitation à un rôle

1. Dans Intune, choisissez **Rôles** > **Tous les rôles** > choisissez un rôle > **Affectations** > **Affecter**.

    ![Capture d’écran de l’affectation d’une étendue à un rôle.](./media/scope-tags/assign-scope-to-role.png)

2. Spécifiez un **Nom de l’affectation** et une **Description**.
3. Choisissez **Membres (Groupes)**  > **Ajouter** > choisissez les groupes dont vous souhaitez qu’ils fassent partie de cette affectation > **Sélectionner** >  **OK**. Les utilisateurs de ce groupe disposent des autorisations pour gérer les stratégies et les profils des utilisateurs/appareils dans Étendue (Groupes).

    ![Capture d’écran de la sélection de groupes de membres](./media/scope-tags/select-member-groups.png)

4. Si vous voulez gérer les utilisateurs/appareils dans un ensemble spécifique de groupes, choisissez **Étendue (Groupes)**  > **Groupes sélectionnés** > **Sélectionner les groupes à inclure** > choisissez les groupes > **Sélectionner** > **OK**. Les profils et les stratégies de tous les utilisateurs/appareils de ce groupe peuvent être gérés par les administrateurs de Membres (Groupe).

    ![Capture d’écran de la sélection de groupes de l’étendue](./media/scope-tags/select-scope-groups.png)

    Vous pouvez aussi choisir **Tous les appareils**, **Tous les utilisateurs** ou **Tous les utilisateurs et tous les appareils**.

    ![Capture d’écran d’autres options pour la sélection de groupes de l’étendue.](./media/scope-tags/scope-group-other-options.png)
    
5. Choisissez **Étendue (balises)**  > **Ajouter** > choisissez les balises que vous voulez ajouter à ce rôle > **Sélectionner** > **OK**. Les utilisateurs de Membres (Groupes) auront accès aux stratégies et aux profils qui ont aussi la même balise d’étendue.

    ![Capture d’écran de la sélection de balises d’étendue](./media/scope-tags/select-scope-tags.png)

6. Choisissez **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Pour ajouter une étiquette de délimitation à un profil de configuration
1. Dans Intune, choisissez **Configuration de l’appareil** > **Profils** > choisissez un profil.

    ![Capture d’écran de la sélection d’un profil.](./media/scope-tags/choose-profile.png)

2. Choisissez **Propriétés** > **Étendue (balises)**  > **Ajouter**.

    ![Capture d’écran de l’ajout de balises d’étendue](./media/scope-tags/add-scope-tags.png)

3. Sous **Sélectionner des balises**, choisissez les balises que vous voulez ajouter au profil.
4. Choisissez **Sélectionner** > **OK** > **Enregistrer**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Pour affecter une balise d’étendue à une stratégie de configuration d’application
Pour les appareils avec **Type d’inscription de l’appareil** défini sur **Appareils gérés** :
1. Choisissez **Applications clientes** > **Stratégies de configuration des applications** > choisissez une stratégie de configuration des applications.
2. Choisissez **Propriétés** > **Étendue (balises)** > choisissez les balises que vous voulez affecter à la stratégie.

Pour les appareils avec **Type d’inscription de l’appareil** défini sur **Applications gérées** :
1. Choisissez **Applications clientes** > **Stratégies de configuration des applications** > choisissez une stratégie de configuration des applications.
2. Choisissez **Étendue (balises)** > choisissez les balises que vous voulez affecter à la stratégie.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Pour affecter une balise d’étendue à un profil de provisionnement d’application iOS
1. Dans Intune, choisissez **Applications clientes** > **Profils de provisionnement d’application iOS** > choisissez un profil.
2. Choisissez **Propriétés** > **Étendue (balises)** > choisissez les balises que vous voulez affecter au profil.
3. Choisissez **Sélectionner** > **OK** > **Enregistrer**.

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Pour affecter une balise d’étendue à un jeton Programme d’achat en volume (VPP) Apple
1. Dans Intune, choisissez **Applications clientes** > **Jetons VPP Apple** > choisissez un jeton VPP.
2. Sélectionnez **Étendue (balises)** > choisissez les balises que vous voulez affecter au profil. Les applications VPP et les livres électroniques associés au jeton VPP héritent des balises affectées.
3. Choisissez **Sélectionner** > **OK** > **Enregistrer**.

## <a name="scope-tag-details"></a>Informations détaillées sur les balises d’étendue
Quand vous utilisez des balises d’étendue, rappelez-vous de ceci :

- Vous pouvez actuellement affecter des balises d’étendue aux éléments suivants :
  - Attributions de rôles
  - Stratégies de conformité des appareils
  - Profils de configuration d’appareil
  - Anneaux des mises à jour Windows 10
  - Appareils gérés
  - Applications
  - Stratégies de configuration d’applications - appareils gérés
  - Scripts PowerShell
  - Jetons DEP
  - Profil de provisionnement d’applications iOS
  - Jetons Programme d’achat en volume (VPP) Apple
- Quand un administrateur crée un objet dans Intune, toutes les balises d’étendue affectées à cet administrateur sont automatiquement affectées au nouvel objet.
- Le contrôle d’accès en fonction du rôle (RBAC) d’Intune ne s’applique pas aux rôles Azure Active Directory. Ainsi, les rôles Administrateur de service et Administrateur général d’Intune ont un accès d’administrateur complet à Intune, quelles que soient leurs balises d’étendue.
- Les administrateurs dans une attribution de rôle avec des balises d’étendue peuvent également voir les objets Intune sans balises d’étendue.
- Vous pouvez affecter seulement une balise d’étendue que vous avez dans vos attributions de rôles.
- Vous pouvez cibler seulement des groupes qui sont listés dans l’étendue (groupes) de votre attribution de rôle.
- Si une balise d’étendue est affectée à votre rôle, vous ne pouvez pas supprimer toutes les balises d’étendue sur un objet Intune. Au moins une balise d’étendue est obligatoire.

## <a name="next-steps"></a>Étapes suivantes

Gérez vos [rôles](role-based-access-control.md) et vos [profils](device-profile-assign.md).
