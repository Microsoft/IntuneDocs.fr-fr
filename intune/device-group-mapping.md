---
title: Catégoriser les appareils en groupes dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment catégoriser les appareils en groupes pour faciliter la gestion.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 0abc42de95f90b3690e91908f92bb53d11a802d8
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53031753"
---
# <a name="categorize-devices-into-groups"></a>Catégoriser les appareils en groupes

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pour faciliter la gestion des appareils, vous pouvez utiliser des catégories d’appareils Microsoft Intune pour ajouter automatiquement des appareils à des groupes en fonction des catégories que vous définissez.

Les catégories d'appareils suivent le processus suivant :
1. Créez des catégories parmi lesquelles les utilisateurs effectuent leur choix quand ils inscrivent leurs appareils.
2. Quand des utilisateurs d’appareils iOS et Android inscrivent un appareil, ils doivent choisir une catégorie dans la liste des catégories que vous avez configurées. Pour attribuer une catégorie à un appareil Windows, les utilisateurs doivent utiliser le site web Portail d’entreprise.
3. Vous pouvez ensuite déployer des stratégies et des applications sur ces groupes.

Vous pouvez créer toute catégorie d’appareils souhaitée. Par exemple :
- Appareil de point de vente
- Appareil de démonstration
- Ventes
- Gestion des comptes
- Manager

## <a name="how-to-configure-device-categories"></a>Comment configurer des catégories d'appareils

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Étape 1 : Créer des catégories d’appareils dans le panneau Intune du portail Azure
1. Dans [Intune du portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils**.
2. Dans le panneau **Inscription de l’appareil** choisissez **Catégories d’appareils**.
3. Dans la page **Catégories d’appareils**, choisissez **Créer** pour ajouter une nouvelle catégorie.
4. Dans le panneau **Créer une catégorie d’appareils**, entrez un **Nom** pour la nouvelle catégorie et une **Description** facultative.
5. Quand vous avez terminé, sélectionnez **Créer**. Vous pouvez voir la nouvelle catégorie dans la liste des catégories.

Vous utiliserez le nom de catégorie d’appareil quand vous créerez des groupes de sécurité Active Directory Azure (Azure AD) à l’étape 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Étape 2 : Créer des groupes de sécurité Azure Active Directory
Au cours de cette étape, vous allez créer des groupes dynamiques dans le portail Azure, basés sur la catégorie d’appareil et le nom de la catégorie d’appareil.

Pour continuer, reportez-vous à [Utilisation d’attributs pour créer des règles avancées](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) dans la documentation d’Azure AD.

Utilisez les informations de cette section pour créer un groupe d’appareils avec une règle avancée à l’aide de l’attribut **deviceCategory**. Par exemple **device.deviceCategory -eq** "*nom de catégorie d’appareil que vous avez obtenu à partir du portal Azure*".

Une fois que vous configurez des groupes d'appareils et que les utilisateurs inscrivent leurs appareils, ces derniers peuvent voir une liste des catégories que vous avez configurées. Une fois qu’ils choisissent une catégorie et terminent l’inscription, leur appareil est ajouté au groupe de sécurité Active Directory qui correspond à la catégorie choisie.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Voir les catégories d’appareils que vous gérez

1.  Dans [Intune du portail Azure](https://aka.ms/intuneportal), choisissez **Appareils**.

2.  Sous **Gérer**, sélectionnez **Tous les appareils**.

3.  Dans la liste des appareils, examinez la colonne **Catégorie d’appareil**.

Si la colonne **Catégorie d’appareil** n’est pas affichée, sélectionnez **Colonnes**. Choisissez **Catégorie d’appareils** dans la liste, puis sélectionnez **Appliquer**.

### <a name="change-the-category-of-a-device"></a>Changer la catégorie d’un appareil

1. Dans [Intune du portail Azure](https://aka.ms/intuneportal), choisissez **Appareils**.
2. Dans le panneau **Appareils**, sous **Gérer**, choisissez **Tous les appareils**.
3. Dans la liste des appareils, choisissez l’appareil souhaité. Ensuite, dans le panneau des propriétés de l’appareil, sous la section **Gérer**, choisissez **Propriétés**.
4. Dans le panneau suivant, vous pouvez modifier la **Catégorie** de l’appareil sélectionné sur un des noms de catégorie que vous avez configurés précédemment.

## <a name="after-you-configure-device-groups"></a>Après avoir configuré des groupes d’appareils

Quand des utilisateurs d’appareils iOS et Android inscrivent leur appareil, ils doivent choisir une catégorie dans la liste des catégories que vous avez configurées. Une fois qu’ils ont choisi une catégorie et terminé l’inscription, leur appareil est ajouté au groupe d’appareils Intune ou au groupe de sécurité Active Directory correspondant à la catégorie choisie.

Les utilisateurs Windows doivent utiliser le site web Portail d’entreprise pour sélectionner une catégorie.

Quelle que soit la plateforme, vos utilisateurs peuvent toujours accéder à portal.manage.microsoft.com après avoir inscrit l’appareil. Invitez l’utilisateur à se rendre sur le site web Portail d’entreprise et à accéder à **Mes appareils**. L’utilisateur peut choisir un appareil inscrit répertorié à l’écran, puis sélectionner une catégorie.

Une fois le choix de catégorie effectué, l’appareil est ajouté automatiquement au groupe correspondant que vous avez créé. Si un appareil est déjà inscrit avant que vous ne configuriez des catégories, l’utilisateur voit une notification concernant l’appareil sur le site web Portail d’entreprise. Elle l’invite à sélectionner une catégorie la prochaine fois qu’il accédera à l’application Portail d’entreprise sur iOS ou Android.

## <a name="further-information"></a>Informations supplémentaires
- Vous pouvez modifier une catégorie d’appareil dans le portail Azure, mais vous devez manuellement mettre à jour tous les groupes de sécurité Azure AD qui référencent cette catégorie.

- Si vous supprimez une catégorie, les appareils qui lui ont été affectés affichent le nom de catégorie **Non affecté**.
