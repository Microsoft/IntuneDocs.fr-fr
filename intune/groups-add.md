---
title: Ajouter des groupes pour organiser des utilisateurs et des appareils
titleSuffix: Microsoft Intune
description: Ajoutez des groupes pour organiser des utilisateurs et des appareils par zone géographique, service ou caractéristique matérielle.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bab0a33eee5f4d4856fb9d01d822236d1927a4e3
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071724"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Ajouter des groupes pour organiser des utilisateurs et des appareils
Intune utilise les groupes Azure Active Directory (AD) pour gérer les utilisateurs et les appareils. En tant qu’administrateur Intune, vous pouvez configurer des groupes en fonction des besoins de votre organisation. Créez des groupes pour organiser les utilisateurs ou appareils par emplacement géographique, service ou spécification matérielle. Utilisez des groupes pour gérer les tâches à l’échelle. Par exemple, vous pouvez définir des stratégies pour de nombreux utilisateurs ou déployer des applications sur un ensemble d’appareils.

Vous pouvez ajouter les types de groupes suivants :
- **Groupes affectés** : ajoutez manuellement des utilisateurs ou des appareils à un groupe statique
- **Groupes dynamiques** (avec Azure Active Directory Premium) : vous permettent de générer de manière dynamique des groupes d’utilisateurs ou d’appareils définis avec des règles simples ou avancées

## <a name="add-a-new-group"></a>Ajouter un nouveau groupe

Utilisez les étapes ci-après pour créer un groupe.
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, choisissez **Groupes** puis **Nouveau groupe** dans le volet **Tous les groupes**.
   ![Capture d’écran du portail Azure avec l’option Nouveau groupe sélectionnée](./media/groups-add-new.png)
4. Pour **Type de groupe**, choisissez l'une des options suivantes :
    - **Sécurité** : Les groupes de sécurité constituent un bon point de départ pour remplir les groupes d’utilisateurs. Étant donné que les groupes de sécurité définissent qui a accès aux différentes ressources, leur conversion en groupes d’utilisateurs Intune ne pose aucun problème. Quand vous créez des groupes d’utilisateurs dans Intune, vous pouvez utiliser les groupes de sécurité qui sont synchronisés entre Active Directory et Azure Active Directory, ou ceux que vous créez directement dans Azure Active Directory par le biais du Centre d’administration Microsoft 365 ou du portail Azure.
    - **Office 365**

5. Tapez un **Nom** et une **Description** pour le nouveau groupe. Ces propriétés s’affichent uniquement dans le portail de gestion et ne sont pas visibles pour les utilisateurs.

6. Choisissez **Type d’appartenance** :
   - **Affecté** pour créer un groupe avec des membres affectés manuellement. En savoir plus sur les [groupes affectés Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
   - **Utilisateur dynamique** pour créer un groupe d’utilisateurs défini avec une **requête dynamique**.
   - **Appareil dynamique** pour créer un groupe d’appareils défini avec une **requête dynamique**.

   ![Capture d’écran des propriétés du groupe Intune](./media/groups-add-properties.png)

   Azure AD vous permet de créer des groupes dynamiques en fonction des règles qui définissent l’appartenance. Découvrez comment [créer des groupes dynamiques basés sur des attributs](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

7. Vous pouvez sélectionner **Activer les fonctionnalités Office** pour permettre aux membres du groupe d’utilisateurs d’accéder à des applications Office 365 partagées. En savoir plus sur les [groupes Office 365](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).
8. Choisissez **Créer** pour ajouter le nouveau groupe.

## <a name="groups-and-policies"></a>Groupes et stratégies

Quand vous créez des groupes, pensez à la façon dont vous allez appliquer des [stratégies](device-compliance-get-started.md). Par exemple, vous pouvez avoir des stratégies propres au système d’exploitation d’un appareil, ainsi que des stratégies spécifiques pour les différents rôles définis dans votre organisation ou pour les unités d’organisation que vous avez déjà définies dans Active Directory. Il peut être utile de créer des groupes d’appareils distincts pour iOS, Android et Windows, et un groupe d'utilisateurs pour chaque rôle organisationnel.

Vous souhaiterez sans doute aussi créer une stratégie par défaut applicable à tous les groupes et appareils pour établir les exigences de base de votre organisation en matière de conformité. Ensuite, vous pouvez créer des stratégies particulières pour les catégories d’utilisateurs et d’appareils les plus générales, par exemple des stratégies de messagerie pour chaque système d’exploitation des appareils.



## <a name="see-also"></a>Voir aussi
- [Gérer l’accès aux ressources avec les groupes Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Groupes classiques Intune dans le portail Azure](groups-get-started.md)
