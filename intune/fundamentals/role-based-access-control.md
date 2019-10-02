---
title: Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune
description: Découvrez comment le contrôle d’accès en fonction du rôle (RBAC) vous permet de contrôler qui peut exécuter des actions et apporter des modifications dans Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: eab50a21ea01cd4075bd78add980d2839606a1a2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721875"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune

Le contrôle d’accès en fonction du rôle (RBAC) vous permet de gérer qui a accès aux ressources de votre organisation et ce qu’ils peuvent faire avec ces ressources.  En [attribuant des rôles](assign-role.md) à vos utilisateurs Intune, vous pouvez limiter ce qu’ils peuvent voir et modifier. Chaque rôle a un jeu d’autorisations qui déterminent ce à quoi les utilisateurs disposant de ce rôle peuvent accéder et ce qu’ils peuvent modifier au sein de votre organisation.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- **Administrateur général**
- **Administrateur du service Intune** (également appelé **Administrateur Intune**)

Pour obtenir des conseils et des suggestions sur Intune RBAC, vous pouvez consulter cette série de cinq vidéos qui présentent des exemples et procédures pas à pas : [1](https://www.youtube.com/watch?v=5deXLMLcnKY), [2](https://www.youtube.com/watch?v=38dnMBLuxbQ), [3](https://www.youtube.com/watch?v=6vqg9cAkMbY), [4](https://www.youtube.com/watch?v=5yOLajFFMHE), [5](https://www.youtube.com/watch?v=P5DDvsSF4Wk).

## <a name="roles"></a>Rôles
Un rôle définit le jeu d’autorisations accordées aux utilisateurs affectés à ce rôle.
Vous pouvez utiliser les rôles intégrés et personnalisés. Les rôles intégrés couvrent des scénarios courants dans Intune. Vous pouvez [créer vos propres rôles personnalisés](create-custom-role.md) avec le jeu d’autorisations exact dont vous avez besoin. Plusieurs rôles Azure Active Directory disposent d’autorisations pour Intune.
Pour afficher un rôle, choisissez **Intune** > **Rôles** > **Tous les rôles** > choisissez un rôle. Vous verrez les pages suivantes :

- **Propriétés** : nom, description, type, affectations et balises d’étendue pour le rôle. 
- **Autorisations** : liste un long ensemble de boutons bascules définissant les autorisations dont dispose le rôle.
- **Affectations** : liste d’[attributions de rôles]( assign-role.md) identifiant quels utilisateurs ont accès à quels utilisateurs/appareils. Un rôle peut avoir plusieurs attributions, et un utilisateur peut figurer dans plusieurs attributions.

### <a name="built-in-roles"></a>Rôles intégrés
Vous pouvez attribuer des rôles intégrés aux groupes sans configuration supplémentaire. Vous ne pouvez pas supprimer ou modifier le nom, la description, le type ou les autorisations d’un rôle intégré.

- **Opérateur du support technique** : Effectue des tâches à distance sur les utilisateurs et les appareils, et peut attribuer des applications ou des stratégies aux utilisateurs ou aux appareils.
- **Gestionnaire de stratégie et de profils** : Gère la stratégie de conformité, les profils de configuration, l’inscription auprès d’Apple, les identificateurs d’appareils d’entreprise et les bases de référence de la sécurité.
- **Opérateur en lecture seule** : Affiche des informations sur les utilisateurs, les appareils, l’inscription, la configuration et les applications. Il ne peut pas apporter de modifications à Intune.
- **Gestionnaire d’applications** : Gère les applications mobiles et gérées, peut lire les informations de l’appareil et peut afficher les profils de configuration de l’appareil.
- **Administrateur de rôles Intune** : Gère les rôles Intune personnalisés et ajoute des affectations pour les rôles Intune intégrés. C’est le seul rôle Intune qui peut affecter des autorisations aux administrateurs.
- **Administrateur scolaire** : Gère les appareils Windows 10 dans [Intune pour l’Éducation](../introduction-intune-education.md).

### <a name="custom-roles"></a>Rôles personnalisés
Vous pouvez créer vos propres rôles avec des autorisations personnalisées. Pour plus d’informations sur les rôles personnalisés, consultez [Créer un rôle personnalisé](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Rôles Azure Active Directory avec accès Intune
| Rôle Azure Active Directory | Toutes les données Intune | Données d’audit Intune |
| --- | :---: | :---: |
| Administrateur général | Lecture/écriture | Lecture/écriture |
| Administrateur du service Intune | Lecture/écriture | Lecture/écriture |
| Administrateur de l’accès conditionnel | Aucune | Aucune |
| Administrateur de sécurité | Lecture seule | Lecture seule |
| Opérateur de sécurité | Lecture seule | Lecture seule |
| Lecteur Sécurité | Lecture seule | Lecture seule |
| Administrateur de conformité | Aucune | Lecture seule |
| Administrateur des données de conformité | Aucune | Lecture seule |

> [!TIP]
> Intune présente également trois extensions d’Azure AD : **Utilisateurs**, **Groupes** et **Accès conditionnel**, qui sont contrôlées à l’aide du contrôle d’accès en fonction du rôle (RBAC) d’Azure AD. En outre, **l’administrateur de comptes d’utilisateurs** accomplit uniquement les activités relatives aux groupes et aux utilisateurs AAD ; il n’a pas l’autorisation d’effectuer toutes les activités possibles dans Intune. Pour plus d’informations, consultez [RBAC avec Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Rôles créés dans le portail classique Intune
Seuls les utilisateurs de type **Administrateurs de Service** d’Intune disposant de toutes les autorisations sont migrés du portail classique Intune vers Intune dans le portail Azure. Vous devez les réaffecter**Administrateurs de Service**avec l’accès « Lecture seule » ou « Support technique » dans les rôles Intune sur le Portail Azure, et les supprimer du Portail Classic.
> [!IMPORTANT]
> Vous devrez peut-être conserver l’accès Administrateur du service Intune dans le portail classique si vos administrateurs ont encore besoin d’un accès pour gérer les PC avec Intune.

## <a name="role-assignments"></a>Attributions de rôles
Une attribution de rôle définit :

- Les utilisateurs affectés au rôle.
- Les ressources qu’ils peuvent voir.
- Les ressources qu’ils peuvent modifier.

Vous pouvez affecter des rôles personnalisés et intégrés à vos utilisateurs. Pour être affecté à un rôle Intune, l’utilisateur doit disposer d’une licence Intune.
Pour afficher une attribution de rôle, choisissez **Intune** > **Rôles** > **Tous les rôles** > choisissez un rôle > choisissez une attribution. Vous verrez les pages suivantes :

- **Propriétés** : nom, description, rôle, membres, étendues et balises de l’attribution.
- **Membres** : tous les utilisateurs des groupes de sécurité Azure listés sont autorisés à gérer les utilisateurs/appareils figurant dans Étendue (groupes).
- **Étendue (groupes)**  : tous les utilisateurs/appareils dans ces groupes de sécurité Azure peuvent être gérés par les utilisateurs figurant dans Membres.
- **[Étendue balises)](scope-tags.md)**  : les utilisateurs figurant dans Membres peuvent voir les ressources qui ont les mêmes balises d’étendue.

### <a name="multiple-role-assignments"></a>Attributions de rôles multiples
Si un utilisateur a plusieurs attributions de rôles, autorisations et balises d’étendue, ces attributions de rôles s’étendent à différents objets comme suit :

- Les autorisations d’affectation et les balises d’étendue s’appliquent uniquement aux objets (tels que les stratégies ou applications) dans l’Étendue (groupe) de l’affectation de ce rôle. Les autorisations d’affectation et les balises d’étendue ne s’appliquent aux objets dans d’autres attribution de rôles, sauf si l’autre attribution les accorde spécifiquement.
- Les autres autorisations (telles que Créer, Mettre à jour, Supprimer) et les balises d’étendue s’appliquent à tous les objets du même type (par exemple toutes les stratégies ou toutes les applications) dans toutes les affectations de l’utilisateur.
- Les autorisations et les balises d’étendue pour les objets de types différents (tels que les stratégies ou applications) ne s’appliquent pas les unes aux autres. Par exemple, une autorisation de lecture pour une stratégie ne fournit pas d’autorisation de lecture aux applications dans les attributions de l’utilisateur.

## <a name="next-steps"></a>Étapes suivantes
- [Attribuer un rôle à un utilisateur](assign-role.md)
- [Créer un rôle personnalisé](create-custom-role.md)
