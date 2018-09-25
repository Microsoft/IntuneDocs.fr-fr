---
title: Gérer des applications à partir du Microsoft Store pour Entreprises
titlesuffix: Microsoft Intune
description: Découvrez comment synchroniser des applications dans Intune à partir de Microsoft Store pour Entreprises, puis assignez et suivez ces applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0d1fe40b1cb5a496b3111b2630718a3dd17486ab
ms.sourcegitcommit: 63b74a60aafa8d2d6af0594448ae0471fbd79194
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494011"
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Guide pratique pour gérer les applications que vous avez achetées dans le Microsoft Store pour Entreprises avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le [Microsoft Store pour Entreprises](https://www.microsoft.com/business-store) propose un emplacement dans lequel vous pouvez trouver et acheter des applications pour votre organisation, individuellement ou en volume. En connectant le Windows Store à Microsoft Intune, vous pouvez gérer les applications achetées en volume depuis le portail Azure. Par exemple :
* Vous pouvez synchroniser la liste des applications que vous avez achetées dans le Store avec Intune.
* Les applications qui sont synchronisées apparaissent dans la console d’administration Intune. Vous pouvez les affecter comme toute autre application.
* Vous pouvez effectuer un suivi du nombre de licences disponibles et de la quantité de licences utilisée dans la console d’administration Intune.
* Intune bloque l’attribution et l’installation des applications s’il n’y a pas suffisamment de licences disponibles.
* Les applications gérées par Microsoft Store pour Entreprises révoquent automatiquement les licences quand un utilisateur quitte l’entreprise ou quand l’administrateur supprime l’utilisateur et ses appareils.

## <a name="before-you-start"></a>Avant de commencer

Passez en revue les informations suivantes avant de commencer la synchronisation et l’affectation des applications à partir du Microsoft Store pour Entreprises :

- Configurez Intune comme autorité de gestion des appareils mobiles pour votre organisation.
- Vous devez disposer d’un compte Microsoft Store pour Entreprises.
- Une fois que vous avez associé un compte Microsoft Store pour Entreprises avec Intune, vous ne pouvez pas passer à un autre compte ultérieurement.
- Les applications achetées depuis le Store ne peuvent pas être manuellement ajoutées ou supprimées d’Intune. Elles peuvent uniquement être synchronisées avec le Microsoft Store pour Entreprises.
- Les applications sous licence en ligne et hors connexion que vous avez achetées auprès de Microsoft Store pour Entreprises sont synchronisées dans le portail Intune. Vous pouvez alors déployer ces applications sur des groupes d’utilisateurs ou d’appareils. 
- Les installations d’applications en ligne sont gérées par le Store.
- Les applications hors connexion qui sont gratuites peuvent aussi être synchronisées avec Intune. Ces applications sont installées par Intune et non pas par le Store.
- Les appareils doivent être joints aux services de domaine Active Directory ou à un espace de travail pour pouvoir utiliser cette fonctionnalité.
- Les appareils inscrits doivent utiliser la version 1511 de Windows 10 ou version ultérieure.

En outre, les ensembles liés et les applications en mode hors connexion sous licence synchronisées provenant de Microsoft Store pour Entreprises sont désormais consolidés dans une même entrée d’application dans l’interface utilisateur. Les détails du déploiement des packages individuels seront migrés vers cette même entrée. Pour voir les ensembles liés dans le portail Azure, sélectionnez **Licences d’application** dans le panneau **Applications clientes**.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associer votre compte Microsoft Store pour Entreprises à Intune
Avant d’activer la synchronisation dans la console Intune, vous devez configurer votre compte de Store pour utiliser Intune comme outil de gestion :
1. Veillez à vous connecter à Business Store avec le compte de locataire que vous utilisez pour accéder à Intune.
2. Dans Business Store, choisissez **Paramètres** > **Outils de gestion**.
3. Sur la page Outils de gestion, choisissez **Ajouter un outil de gestion**, puis sélectionnez **Microsoft Intune**.

> [!NOTE]
> Auparavant, vous ne pouviez associer qu’un seul outil de gestion pour affecter des applications au Microsoft Store pour Entreprises. Désormais, vous pouvez associer plusieurs outils de gestion au Windows Store, par exemple, Intune et Configuration Manager.

Vous pouvez maintenant continuer et configurer la synchronisation dans la console Intune.

## <a name="configure-synchronization"></a>Configuration de la synchronisation

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Applications clientes**.
1. Dans le volet **Applications clientes**, choisissez **Installation** > **Microsoft Store pour Entreprises**.
2. Cliquez sur **Activer**.
3. Si ce n’est déjà fait, cliquez sur le lien pour vous inscrire au Microsoft Store pour Entreprises et associer votre compte comme détaillé précédemment.
5. Dans la liste déroulante **Langue**, choisissez la langue d’affichage des applications Microsoft Store pour Entreprises dans le portail Azure. Quelle que soit la langue dans laquelle elles sont affichées, elles sont installées dans la langue de l’utilisateur final quand elles sont disponibles.
6. Cliquez sur **Synchroniser** pour récupérer les applications que vous avez achetées sur le Microsoft Store dans Intune.

## <a name="synchronize-apps"></a>Synchroniser les applications

1. Dans la charge de travail **Applications clientes**, choisissez **Installation** > **Microsoft Store pour Entreprises**.
2. Cliquez sur **Synchroniser** pour récupérer les applications que vous avez achetées sur le Microsoft Store dans Intune.

## <a name="assign-apps"></a>Attribuer des applications

Vous affectez des applications à partir du Windows Store de la même façon que vous affectez toute autre application Intune. Pour plus d’informations, consultez [Guide pratique pour attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md). Toutefois, au lieu d’affecter les applications à partir de la page **Toutes les applications**, affectez-les à partir de la page **Applications sous licence**.

Les applications hors connexion peuvent cibler des groupes d’utilisateurs, des groupes d’appareils ou des groupes contenant des utilisateurs et des appareils.
Les applications hors connexion peuvent être installées pour un utilisateur spécifique sur un appareil ou pour tous les utilisateurs sur un appareil. 


Quand vous affectez une application Microsoft Store pour Entreprises, une licence est utilisée par chaque utilisateur qui installe l’application. Si vous avez utilisé toutes les licences disponibles pour une application affectée, vous ne pouvez plus affecter d’autres copies. Effectuez l’une des actions suivantes :
* Désinstallez l’application de certains appareils.
* Réduisez la portée de l’attribution actuelle pour cibler uniquement les utilisateurs pour lesquels vous avez suffisamment de licences.
* Achetez plus de copies de l’application dans le Microsoft Store pour Entreprises.


