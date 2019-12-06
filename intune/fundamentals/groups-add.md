---
title: Ajouter des groupes pour organiser des utilisateurs et des appareils
titleSuffix: Microsoft Intune
description: Ajoutez des groupes pour organiser des utilisateurs et des appareils par zone géographique, service ou caractéristique matérielle.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e3219e32ef9bea838f0c19258d0b22a99083a12
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74261569"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Ajouter des groupes pour organiser des utilisateurs et des appareils

Intune utilise les groupes Azure Active Directory (Azure AD) pour gérer les utilisateurs et les appareils. En tant qu’administrateur Intune, vous pouvez configurer des groupes en fonction des besoins de votre organisation. Créez des groupes pour organiser les utilisateurs ou appareils par emplacement géographique, service ou spécification matérielle. Utilisez des groupes pour gérer les tâches à l’échelle. Par exemple, vous pouvez définir des stratégies pour de nombreux utilisateurs ou déployer des applications sur un ensemble d’appareils.

Vous pouvez ajouter les types de groupes suivants :

- **Groupes affectés** : ajoutez manuellement des utilisateurs ou des appareils à un groupe statique. 
- **Groupes dynamiques** (nécessite Azure AD Premium) : ajoute automatiquement des utilisateurs ou appareils à des groupes d’utilisateurs ou d’appareils en fonction d’une expression que vous créez.

  Par exemple, lorsqu’un utilisateur est ajouté avec le titre de responsable, l’utilisateur est automatiquement ajouté à un groupe d'utilisateurs **Tous les responsables**. Ou, lorsqu’un appareil a le type de système d’exploitation iOS, l’appareil est automatiquement ajouté à un groupe d'appareils **Tous les appareils iOS**.

## <a name="add-a-new-group"></a>Ajouter un nouveau groupe

Utilisez les étapes ci-après pour créer un groupe.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Groupes** > **Nouveau groupe** :

   ![Capture d’écran du portail Azure avec l’option Nouveau groupe sélectionnée](./media/groups-add/groups-add-new.png)

3. Dans **Type de groupe**, choisissez l'une des options suivantes :

    - **Sécurité** : Les groupes de sécurité définissent qui peut accéder aux ressources, et sont recommandés pour vos groupes dans Intune. Par exemple, vous pouvez créer des groupes pour les utilisateurs, comme **Tous les employés de Charlotte** ou **Toutes les femmes chez Contoso**. Vous pouvez aussi créer des groupes pour les appareils, comme **Tous les appareils iOS** ou **Tous les appareils d’élèves Windows 10**.

        > [!TIP]
        > Les utilisateurs et groupes créés peuvent également être consultés dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com), le centre d’administration Azure Active Directory et [Microsoft Intune dans le portail Azure](https://go.microsoft.com/fwlink/?linkid=2090973). Dans le locataire de votre organisation, vous pouvez créer et gérer des groupes dans toutes ces zones.
        >
        > Si votre rôle principal est la gestion des appareils, nous vous recommandons d’utiliser le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

    - **Office 365** : Ces groupes sont conçus pour contrôler l’accès et partager les ressources Office 365. Par exemple, vous pouvez créer un groupe Office 365 pour partager une boîte de réception ou un calendrier Outlook. Pour plus d’informations, consultez [En savoir plus sur les groupes Office 365](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Renseignez les champs **Nom du groupe** et **Description du groupe** pour le nouveau groupe. Soyez spécifique et incluez des informations afin que d’autres personnes sachent à quoi sert le groupe.

    Par exemple, entrez **Tous les appareils d’élèves Windows 10** pour le nom de groupe, et **Tous les appareils Windows 10 utilisés par les lycéens de Contoso** pour la description du groupe.

5. Indiquez le **Type d'appartenance**. Les options disponibles sont les suivantes :

    - **Attribué** : Les administrateurs affectent manuellement les utilisateurs ou appareils à ce groupe et les suppriment manuellement.
    - **Utilisateur dynamique** : Les administrateurs créent des règles d’appartenance dynamique pour ajouter et supprimer automatiquement des membres.
    - **Appareil dynamique** : Les administrateurs créent des règles de groupe dynamique pour ajouter et supprimer automatiquement des appareils.

        ![Capture d’écran des propriétés du groupe Intune](./media/groups-add/groups-add-properties.png)

    Pour plus d’informations sur ces types d’appartenance et sur la création d’expressions dynamiques, consultez :

    - [Créer un groupe de base et ajouter des membres avec Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Règles d’appartenance de groupe dynamique dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > Dans ce centre d’administration, lorsque vous créez des utilisateurs ou des groupes, vous ne verrez peut-être pas la personnalisation **Azure Active Directory**. Mais c’est bien ce que vous utilisez.

6. Choisissez **Créer** pour ajouter le nouveau groupe. Votre groupe s’affiche dans la liste.

> [!TIP]
> Considérez certains des autres groupes d’utilisateurs et d’appareils dynamiques que vous pouvez créer, par exemple :
>
> - Tous les lycéens de Contoso
> - Tous les appareils Android Entreprise
> - Tous les appareils iOS 11 et versions antérieures
> - Marketing
> - Ressources humaines
> - Tous les employés de Charlotte
> - Tous les employés de Washington

## <a name="groups-and-policies"></a>Groupes et stratégies

L’accès aux ressources de votre organisation est contrôlé par les utilisateurs et les groupes que vous créez.

Lorsque vous créez des groupes, réfléchissez à la façon dont vous allez appliquer les [stratégies de conformité](../protect/device-compliance-get-started.md) et les [profils de configuration](../configuration/device-profiles.md). Par exemple, vous pouvez avoir :

- Stratégies spécifiques au système d’exploitation de l’appareil.
- Stratégies spécifiques aux différents rôles de votre organisation.
- Stratégies spécifiques aux unités d’organisation que vous avez définies dans Active Directory.

Vous pouvez créer une stratégie par défaut applicable à tous les groupes et appareils pour établir les exigences de base de votre organisation en matière de conformité. Ensuite, créez des stratégies particulières pour les catégories d’utilisateurs et d’appareils les plus générales, par exemple des stratégies de messagerie pour chaque système d’exploitation des appareils.

Pour obtenir des recommandations et des conseils sur les profils de configuration, consultez [Affecter des stratégies à des groupes d’utilisateurs ou à des groupes d’appareils](../configuration/device-profile-assign.md#user-groups-vs-device-groups) et [Recommandations de profil](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>Voir aussi

- [Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune](role-based-access-control.md)
- [Gérer l’accès à des ressources à l’aide de groupes Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
