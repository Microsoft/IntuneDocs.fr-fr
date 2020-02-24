---
title: Vue d’ensemble du cycle de vie des applications pour Microsoft Intune
description: Découvrez le cycle de vie des applications gérées dans Microsoft Intune. Le cycle de vie des applications implique l’ajout, le déploiement, la configuration, la protection et la mise hors service des applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 569906cea8467d568d302f4e44b26c3394213b62
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414965"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Vue d’ensemble du cycle de vie des applications dans Microsoft Intune

Le cycle de vie des applications Microsoft Intune commence quand une application est ajoutée et évolue en différentes phases jusqu’à sa suppression. En comprenant ces phases, vous disposerez de toutes les informations nécessaires pour commencer à gérer des applications dans Intune.

![Le cycle de vie de l’application - Ajouter, déployer, configurer, protéger et mettre hors service.](./media/app-lifecycle/app-lifecycle.png "Cycle de vie des applications Intune")

## <a name="add"></a>Ajouter

La première étape du déploiement d’applications consiste à ajouter celles que vous voulez gérer et affecter dans Intune. Il existe certes différents types d’applications avec lesquels vous pouvez travailler, mais les procédures de base sont les mêmes. Avec Intune, vous pouvez ajouter différents types d’applications, notamment des applications écrites en interne (applications métier), des applications du Windows Store, des applications intégrées et des applications sur le web. Pour plus d’informations sur chacun de ces types d’application, consultez [Guide pratique pour ajouter une application à Microsoft Intune](apps-add.md).

## <a name="deploy"></a>Déploiement

Une fois que vous avez ajouté l’application à Intune, vous pouvez [l’affecter aux utilisateurs et appareils que vous gérez](apps-deploy.md). Intune facilite ce processus et, une fois que l’application est déployée, vous pouvez [surveiller la réussite](apps-monitor.md) du déploiement à partir de la console d’administration Intune dans le portail Azure. Certains magasins d’applications, tels que l’[Apple App Store](vpp-apps-ios.md) et le [Windows Store](windows-store-for-business.md), vous permettent également d’acheter des licences d’application en bloc pour votre société. Intune peut synchroniser des données grâce à ces magasins pour vous permettre de déployer des licences et d’effectuer leur suivi pour ces types d’applications directement à partir de la console d’administration Intune.

## <a name="configure"></a>Configurer

Dans le cadre du cycle de vie des applications, des nouvelles versions des applications sont publiées régulièrement. Intune propose des outils permettant de facilement [mettre à jour les applications](apps-add.md) que vous avez déployées vers une version plus récente. En outre, vous pouvez configurer des fonctionnalités supplémentaires pour certaines applications, comme par exemple :

- Les [stratégies de configuration des applications iOS](app-configuration-policies-use-ios.md) permettent de définir des paramètres pour les applications iOS/iPadOS compatibles, utilisables à l’exécution des applications. Par exemple, une application peut nécessiter des paramètres de marque spécifiques ou le nom d’un serveur auquel elle doit se connecter.
- Les [stratégies Managed Browser](app-configuration-managed-browser.md) vous aident à configurer les paramètres de [Microsoft Edge](~/apps/apps-supported-intune-apps.md#microsoft-apps), qui remplace le navigateur par défaut de l’appareil et vous permet de limiter les sites web auxquels vos utilisateurs peuvent accéder.

## <a name="protect"></a>Protéger

Intune propose différentes manières de protéger les données dans vos applications. Les principales méthodes sont :

- L’[accès conditionnel](../protect/conditional-access.md), qui contrôle l’accès à la messagerie et aux autres services en fonction des conditions que vous spécifiez. Les conditions incluent les types d’appareils ou la conformité à l’une des [stratégies de conformité des appareils](../protect/device-compliance-get-started.md) que vous avez déployées.
- Les [stratégies de protection des applications](app-protection-policy.md) fonctionnent avec différentes applications pour protéger les données d’entreprise que ces dernières utilisent. Par exemple, vous pouvez limiter la copie de données entre des applications non gérées et des applications que vous gérez, ou vous pouvez empêcher les applications de s’exécuter sur des appareils jailbroken ou rootés.

## <a name="retire"></a>Mettre hors service

Enfin, il est probable que des applications que vous avez déployées deviennent obsolètes et doivent être supprimées. Intune facilite [la mise hors service d’applications](../remote-actions/device-management.md).

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur la [gestion des applications dans Microsoft Intune](app-management.md)
