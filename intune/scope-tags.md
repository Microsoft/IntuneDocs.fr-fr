---
title: Filtrer les stratégies avec des étiquettes de délimitation dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des étiquettes de délimitation pour filtrer les profils de configuration de manière à n’afficher que certains rôles.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bca2d52bb47a149c6a36bc1b8cbc4d65e50c0f4c
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756800"
---
# <a name="use-rbac-and-scope-tags-for-distributed-it"></a>Utiliser des balises RBAC et l’étendue pour distribuée informatique

Vous pouvez utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour vous assurer que les administrateurs de droite ont l’accès approprié et la visibilité aux objets Intune appropriées. Les rôles déterminent quel accès administrateurs ont à quels objets. Balises d’étendue déterminent les objets que les administrateurs peuvent voir.

Par exemple, supposons qu’un administrateur de bureau régional de Seattle est attribué au rôle de gestionnaire de stratégie et profil. Vous souhaitez que cet administrateur pour afficher et gérer les profils et les stratégies qui s’appliquent uniquement aux appareils de Seattle. Pour ce faire, vous devez :

1. Créer une balise d’étendue nommée Seattle.
2. Créer une attribution de rôle pour le rôle de gestionnaire de stratégie et profil avec : 
    - Membres (groupes) = un groupe de sécurité nommé administrateurs informatiques de Seattle. Tous les administrateurs de ce groupe disposent des autorisations pour gérer les stratégies et les profils des utilisateurs/appareils dans l’étendue (groupes).
    - Étendue (groupes) = une sécurité groupe utilisateurs de Seattle nommés. Tous les utilisateurs/appareils de ce groupe peut avoir leurs profils et des stratégies gérés par les administrateurs dans les membres (groupes). 
    - Étendue (balises) = Seattle. Administrateurs dans le membre (groupes) peuvent voir les appareils qui ont également la balise d’étendue de Seattle.
3. Ajoutez la balise d’étendue de Seattle pour les stratégies et les profils que vous souhaitez que les administrateurs de membres (groupes) pour être en mesure d’accéder.
4. Ajoutez la balise d’étendue de Seattle pour les périphériques que vous voulez visible pour les administrateurs dans les membres (groupes). 


## <a name="to-create-a-scope-tag"></a>Pour créer une étiquette de délimitation

1. Dans Intune, choisissez **rôles** > **étendue (balises)** > **créer**.

    ![Capture d’écran de créer une balise d’étendue.](./media/scope-tags/create-scope-tag.png)

2. Indiquez un **Nom** et une **Description**.
3. Choisissez **Créer**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Pour affecter une étiquette de délimitation à un rôle

1. Dans Intune, choisissez **rôles** > **tous les rôles** > Choisissez un rôle > **affectations** > **affecter**.

    ![Capture d’écran d’affecter l’étendue à un rôle.](./media/scope-tags/assign-scope-to-role.png)

2. Fournir un **nom de l’affectation** et **Description**.
3. Choisissez **membres (groupes)** > **ajouter** > Choisissez les groupes que vous souhaitez dans le cadre de cette attribution > **sélectionnez**  >   **OK**. mUsers dans ce groupe ont des autorisations pour gérer des stratégies et des profils pour les utilisateurs/appareils dans l’étendue (groupes).

    ![Capture d’écran de groupes de sélectionner un membre.](./media/scope-tags/select-member-groups.png)

4. Si vous souhaitez gérer les utilisateurs/appareils dans un ensemble spécifique de groupes, choisissez **étendue (groupes)** > **groupes sélectionnés** > **sélectionner les groupes à inclure**> Choisissez les groupes > **sélectionnez** > **OK**. Tous les utilisateurs/appareils de ce groupe peut avoir leurs profils et des stratégies gérés par les administrateurs dans les membres (groupe).

    ![Capture d’écran de groupes d’étendue select.](./media/scope-tags/select-scope-groups.png)

    Alternativement, vous pouvez choisir **tous les appareils**, **tous les utilisateurs**, ou **tous les utilisateurs et tous les appareils**.

    ![Capture d’écran d’autres options pour les groupes d’étendue select.](./media/scope-tags/scope-group-other-options.png)
    
5. Choisissez **étendue (balises)** > **ajouter** > Choisissez les balises que vous souhaitez ajouter à ce rôle > **sélectionnez** > **OK**. Utilisateurs de membres (groupes) auront accès aux stratégies et profils qui possèdent également la même balise d’étendue.

    ![Capture d’écran de balises d’étendue select.](./media/scope-tags/select-scope-tags.png)

6. Choisissez **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Pour ajouter une étiquette de délimitation à un profil de configuration
1. Dans Intune, choisissez **configuration de l’appareil** > **profils** > Choisissez un profil.

    ![Capture d’écran de sélectionner un profil.](./media/scope-tags/choose-profile.png)

2. Choisissez **propriétés** > **étendue (balises)** > **ajouter**.

    ![Capture d’écran de balises d’étendue ajouter.](./media/scope-tags/add-scope-tags.png)

3. Sous **balises Select**, choisissez les balises que vous souhaitez ajouter au profil.
4. Choisissez **sélectionnez** > **OK** > **enregistrer**.

## <a name="scope-tag-details"></a>Détails de l’étiquette étendue
Lorsque vous travaillez avec des balises d’étendue, n’oubliez pas ces détails :

- Vous pouvez actuellement affecter des balises d’étendue à :
    - Attributions de rôles
    - Stratégies de conformité des appareils
    - Profils de configuration d’appareil
    - Anneaux des mises à jour Windows 10
    - Appareils gérés
    - Applications
    - Stratégies de configuration : les appareils gérés
    - Scripts PowerShell
    - Jetons DEP
- Lorsqu’un administrateur crée un objet dans Intune, toutes les balises d’étendue qu’administrateur seront automatiquement attribués au nouvel objet.
- RBAC d’Intune ne s’applique pas aux rôles Azure Active Directory. Par conséquent, les rôles des administrateurs de Service Intune et les administrateurs généraux ont accès d’administrateur complets à Intune, quel que soit les balises d’étendue sont-ils.
- Les administrateurs dans une attribution de rôle avec les balises d’étendue peuvent également voir les objets Intune sans balises d’étendue.
- Vous pouvez uniquement affecter une balise d’étendue que vous avez dans vos attributions de rôles.
- Vous pouvez uniquement les groupes de cibles qui sont répertoriées dans l’étendue (groupes) de votre attribution de rôle.
- Si vous avez une balise d’étendue à votre rôle, vous ne pouvez pas supprimer toutes les balises d’étendue sur un objet Intune. Balise d’au moins une étendue est requise.
- Si un utilisateur a plusieurs attributions de rôles, les autorisations dans les affectations de rôle s’étendent à des objets différents comme suit :
    - Affecter des autorisations s’appliquent uniquement aux objets (tels que les stratégies ou applications) dans l’attribution d’un rôle étendue (groupes). Affecter des autorisations ne s’appliquent aux objets dans d’autres affectations de rôle, sauf si l’autre attribution leur ait spécifiquement accordé.
    - Autres autorisations (par exemple, créer et de lecture), s’appliquent à tous les objets du même type (par exemple, toutes les stratégies ou toutes les applications) dans des affectations de l’utilisateur.
    - Autorisations pour les objets de types différents (par exemple, les stratégies ou applications), ne s’appliquent pas à eux. Par exemple, une autorisation de lecture pour une stratégie, ne fournit pas une autorisation de lecture pour les applications dans les attributions de l’utilisateur.





## <a name="next-steps"></a>Étapes suivantes

Gérez vos [rôles](role-based-access-control.md) et vos [profils](device-profile-assign.md).
