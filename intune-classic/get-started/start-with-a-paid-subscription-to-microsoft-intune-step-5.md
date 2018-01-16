---
title: "Créer des groupes pour organiser les utilisateurs et les appareils"
description: "Créer des utilisateurs et des groupes pour votre abonnement Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 309994268b061f844e26dea8df8ce3c0fd237e95
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2018
---
# <a name="create-groups-to-organize-users-and-devices"></a>Créer des groupes pour organiser les utilisateurs et les appareils

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Cette rubrique explique aux administrateurs comment créer des groupes d’utilisateurs dans Intune.

Les groupes créés dans Intune vous permettent de gérer vos utilisateurs et appareils avec une grande souplesse. Vous pouvez configurer des groupes qui répondent aux besoins de votre organisation (par exemple, en fonction de l'emplacement géographique, du service ou de caractéristiques matérielles) et les utiliser pour effectuer diverses tâches d'administration, du déploiement de stratégies pour un ensemble d'utilisateurs au déploiement d'applications sur un ensemble d'appareils.

## <a name="group-management-moving-to-azure-ad"></a>Déplacement de la gestion des groupes vers Azure AD

**Depuis novembre 2016**, les nouveaux comptes gèrent les groupes d’utilisateurs et d’appareils dans le portail Azure Active Directory (AD). En décembre 2016, l’équipe produit Intune commencera la migration des clients actuels vers la nouvelle expérience de gestion de groupes Azure AD. Tous les groupes d’utilisateurs et d’appareils Intune seront migrés vers les groupes de sécurité Azure AD. Nous ne démarrerons pas la migration tant que nous ne serons pas sûrs de pouvoir minimiser l’impact sur votre travail quotidien et garantir qu’il n’y aura aucun impact sur les utilisateurs. Par ailleurs, nous vous avertirons avant d’effectuer la migration de votre compte.


>[!IMPORTANT]
>
>Si vous ouvrez l’espace de travail Groupes dans le portail Intune et que vous voyez le message **Les groupes d’utilisateurs Intune sont désormais gérés comme groupes dans Azure Active Directory** avec un lien vers le portail Azure Active Directory, cela signifie que vous utilisez la *nouvelle* approche des groupes de sécurité Azure AD pour gérer les groupes dans Intune. Pour savoir comment créer des groupes, voir [Gestion des groupes dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
>
>Si vous ne voyez pas le lien vers le portail Azure AD, cela signifie que vous utilisez toujours le portail Intune pour la gestion des groupes.

## <a name="group-management-in-the-intune-portal"></a>Gestion des groupes dans le portail Intune

Les groupes d’appareils et d’utilisateurs sont créés dans l’espace de travail GROUPES de la console d’administration Intune.

![Espace de travail Groupe de la console d’administration](./media/groups.png)


> [!TIP]
> Pour en savoir plus sur l’utilisation des groupes, consultez [Créer des groupes pour gérer les utilisateurs et les appareils](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## <a name="create-a-device-group"></a>Créer un groupe d'appareils
Les groupes d'appareils permettent de déployer des applications et des mises à jour et de configurer d'autres fonctionnalités. Par exemple, vous pouvez configurer un groupe « Mes appareils » en procédant comme suit :

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **Groupes**  > **Vue d’ensemble** > **Créer un groupe**.

2.  Pour le **Nom de groupe**, tapez « Mes appareils » et, dans la liste de groupes parents, sélectionnez **Tous les appareils**, puis cliquez sur **Suivant**.

3.  Dans la page **Définir les critères d'appartenance** , sélectionnez **Tous les appareils** , pour indiquer que le groupe inclut à la fois des appareils mobiles et des ordinateurs.

4.  Dans la page **Définir l’appartenance directe**, cliquez sur **Suivant**. Si vous aviez créé un groupe qui n'incluait pas tous les appareils et que vous voulez ajouter des appareils spécifiques à votre nouveau groupe, vous pouvez le faire ici.

5.  Dans la page **Résumé**, passez en revue les actions à entreprendre, puis choisissez **Terminer**.

Le groupe récemment créé est disponible dans la liste **Groupes**, dans l’espace de travail **Groupes**, sous **Tous les appareils**. À ce stade, vous pouvez également modifier ou supprimer le groupe.

## <a name="create-a-user-group"></a>Créer un groupe d'utilisateurs
Les groupes d'utilisateurs permettent de déployer des stratégies d'appareils et de logiciels. Par exemple, vous pouvez configurer un groupe « Utilisateurs Intune » en procédant comme suit :

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **Groupes**  > **Vue d’ensemble** > **Créer un groupe**.

2.  Pour le **Nom de groupe**, tapez « Utilisateurs Intune » et, dans la liste de groupes parents, sélectionnez **Tous les utilisateurs**, puis cliquez sur **Suivant**.

3.  Dans la page **Définir les critères d'appartenance** , définissez **Commencer l'appartenance au groupe par** avec la valeur **Tous les utilisateurs du groupe parent**.

4.  En regard de l’option **Exclure les membres de ces groupes de sécurité**, cliquez sur **Parcourir** , puis sélectionnez **Administrateur de la société** Cette exclusion vous permet de gérer le groupe Utilisateurs Intune sans affecter le compte Administrateur de la société (également appelé Administrateur clients).

5.  Dans la page **Définir l’appartenance directe**, cliquez sur **Suivant**. Vous n'avez pas besoin de faire quoi que ce soit ici, car vous voulez que le groupe Utilisateurs Intune intègre tous les utilisateurs, à l'exception de l'administrateur de la société.

6.  Dans la page **Résumé**, passez en revue les actions à entreprendre, puis cliquez sur **Terminer**.

Le groupe récemment créé est disponible dans la liste **Groupes**, dans l’espace de travail **Groupes**, sous **Tous les utilisateurs**. À ce stade, vous pouvez également modifier ou supprimer le groupe.

>[!div class="step-by-step"]
/intune/licenses-assign [&larr; **Gérer les licences Intune**](/intune/licenses-assign)       [**Créer des stratégies et des applications** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  
