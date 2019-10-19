---
title: Groupes classiques Intune dans le portail Azure
titleSuffix: Microsoft Intune
description: Découvrez les nouveautés concernant les groupes dans le portail Azure de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/31/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0cf8e136b3ef5c3d4329e075af4c180423d74a15
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502846"
---
# <a name="microsoft-intune-classic-groups-in-the-azure-portal"></a>Groupes classiques Microsoft Intune dans le portail Azure

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Nous avons tenu compte de vos commentaires et apporté des modifications à l’utilisation des groupes dans Microsoft Intune.
Si vous utilisez Intune à partir du portail Azure, vos groupes Intune ont été migrés vers des groupes de sécurité Azure Active Directory.

Vous pouvez ainsi utiliser la même expérience de groupes dans l’ensemble des applications Enterprise Mobility + Security et Azure AD. En outre, vous pouvez utiliser PowerShell et l’API Graph pour étendre et personnaliser cette nouvelle fonctionnalité.

Les groupes de sécurité Azure AD prennent en charge tous les types de déploiements Intune pour les utilisateurs et les appareils. En outre, vous pouvez utiliser des groupes dynamiques Azure AD qui se mettent automatiquement à jour en fonction des attributs que vous fournissez. Par exemple, vous pouvez créer un groupe d'appareils exécutant iOS 9. Chaque fois qu’un appareil exécutant iOS 9 est inscrit, il s’affiche automatiquement dans le groupe dynamique.

## <a name="what-is-not-available"></a>Qu’est-ce qui n’est pas disponible ?

Certaines des fonctionnalités relatives aux groupes Intune que vous utilisiez peut-être auparavant ne sont pas disponibles dans Azure AD :

- Les groupes Intune **Utilisateurs non groupés** et **Appareils non groupés** ne sont plus disponibles.
- L’option permettant **d’exclure des membres spécifiques** d’un groupe n’existe pas dans le portail Azure. Toutefois, vous pouvez utiliser un groupe de sécurité Azure AD avec des règles avancées pour répliquer ce comportement. Par exemple, pour créer une règle avancée qui inclut toutes les personnes de votre service Ventes dans un groupe de sécurité, mais exclut les groupes dont la fonction contient le mot « Assistant », vous pouvez utiliser la règle avancée suivante :

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Le groupe **Tous les appareils gérés par Exchange ActiveSync** dans la console classique Intune n’a pas été migré vers Azure AD. Toutefois, vous pouvez toujours accéder aux informations sur les appareils gérés par Exchange ActiveSync à partir du portail Azure.

## <a name="how-to-get-started"></a>Commencer

- Lisez les rubriques suivantes pour en savoir plus sur les groupes de sécurité Azure AD et leur fonctionnement :
  - [Gestion de l’accès aux ressources avec les groupes Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-manage-groups/).
  - [Gestion des groupes dans Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/).
  - [Utilisation d’attributs pour créer des règles avancées](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
- Vérifiez que les administrateurs qui ont besoin de créer des groupes sont ajoutés au rôle Azure AD **Administrateur de service Intune**. Le rôle d’administrateur de service Azure AD n’a pas d’autorisations **Gérer le groupe**.
- Si vos groupes Intune utilisaient l’option **Exclure des membres spécifiques**, déterminez si vous pouvez modifier ces groupes sans exclusions, ou si vous avez besoin des règles avancées pour répondre aux besoins de l’entreprise.


## <a name="what-happened-to-intune-groups"></a>Qu’est-il advenu aux groupes Intune ?
Quand les groupes sont migrés du portail Azure vers Intune dans le portail Azure, les règles suivantes sont appliquées :

| Groupes dans Intune|Groupes dans Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Groupe d’utilisateurs statique|Groupe de sécurité Azure AD statique|
|Groupe d’utilisateurs dynamique|Groupes de sécurité Azure AD statiques avec une hiérarchie de groupes de sécurité Azure AD|
|Groupe d'appareils statique|Groupe de sécurité Azure AD statique|
|Groupe d'appareils dynamique|Groupe de sécurité Azure AD dynamique|
|Groupe avec une condition d’inclusion|Groupe de sécurité Azure AD statique contenant des membres statiques ou dynamiques de la condition d’inclusion dans Intune|
|Un groupe avec une condition d’exclusion|Non migré|
|Groupes intégrés :<br>- **Tous les utilisateurs**<br>- **Utilisateurs non groupés**<br>- **Tous les appareils**<br>- **Appareils non groupés**<br>- **Tous les ordinateurs**<br>- **Tous les appareils mobiles**<br>- **Tous les appareils gérés par MDM**<br>- **Tous les appareils gérés par EAS**|Groupes de sécurité Azure AD|

## <a name="group-hierarchy"></a>Hiérarchie de groupe

Dans la console Intune, tous les groupes avaient un groupe parent. Les groupes pouvaient contenir uniquement des membres de leur groupe parent. Dans Azure AD, les groupes enfants peuvent contenir des membres qui n’appartiennent pas au groupe parent.

## <a name="group-attributes"></a>Attributs de groupe
Les attributs sont des propriétés d’appareils qui peuvent être utilisés dans la définition de groupes. Ce tableau décrit comment ces critères sont migrés vers les groupes de sécurité Azure AD.

| Attribut dans Intune|Attribut dans Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Attribut d’unité d’organisation pour les groupes d’appareils|Attribut d’unité d’organisation pour les groupes dynamiques.|
|Attribut de nom de domaine pour les groupes d’appareils|Attribut de nom de domaine pour les groupes dynamiques.|
|Groupe de sécurité comme attribut pour les groupes d’utilisateurs|Les groupes ne peuvent pas être des attributs dans les requêtes dynamiques Azure AD. Les groupes dynamiques peuvent contenir seulement des attributs spécifiques à des utilisateurs ou à des appareils.|
|Attribut de gestionnaire pour les groupes d’utilisateurs|Règle avancée pour l’attribut *gestionnaire* dans les groupes dynamiques|
|Tous les utilisateurs du groupe d’utilisateurs parent|Groupe statique avec ce groupe comme membre|
|Tous les appareils mobiles du groupe d’appareils parent|Groupe statique avec ce groupe comme membre|
|Tous les appareils mobiles gérés par Intune|Attribut de type de gestion avec « MDM » comme valeur pour le groupe dynamique|
|Groupes imbriqués dans des groupes statiques |Groupes imbriqués dans des groupes statiques|
|Groupes imbriqués dans des groupes dynamiques|Groupe dynamique avec un seul niveau d’imbrication|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>Que se passe-t-il pour les stratégies et les applications que vous aviez déployées ?

Les applications et les stratégies continuent d'être déployées sur les groupes, comme avant. Toutefois, vous devez désormais gérer ces groupes à partir du portail Azure au lieu de la console Intune.
