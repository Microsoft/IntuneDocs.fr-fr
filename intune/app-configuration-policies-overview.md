---
title: Stratégies de configuration des applications pour Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser des stratégies de configuration des applications sur un appareil iOS ou Android dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e5ddf39a201f1a70f997e03f0b65706853adefa
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885114"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Stratégies de configuration des applications pour Microsoft Intune

Utilisez des stratégies de configuration des applications dans Microsoft Intune afin de fournir des paramètres de configuration pour une application iOS ou Android. Ces paramètres de configuration permettent la personnalisation d’une application à l’aide d’une approche relative aux normes industrielles pour la gestion et la configuration des applications. Les paramètres de stratégie de configuration sont utilisés quand l’application les recherche, en général lors de sa première exécution.

Vous pouvez attribuer une stratégie de configuration des applications à un groupe d’utilisateurs et d’appareils à l’aide d’une combinaison d’affectations d’inclusion et d’exclusion. Dès que vous ajoutez une stratégie de configuration d’application, vous pouvez définir les affectations de la stratégie de configuration d’application. Quand vous définissez les affectations de la stratégie, vous pouvez choisir d’inclure et d’exclure les groupes d’utilisateurs auxquels la stratégie s’applique. Quand vous choisissez d’inclure un ou plusieurs groupes, vous pouvez choisir de sélectionner des groupes spécifiques à inclure ou sélectionner des groupes intégrés. Les groupes intégrés sont notamment **Tous les utilisateurs**, **Tous les appareils** et **Tous les utilisateurs + Tous les appareils**.

Un paramètre de configuration d’application, par exemple, peut vous obliger à spécifier les détails suivants :

- Un numéro de port personnalisé
- Paramètres de langue
- Paramètres de sécurité
- Paramètres de personnalisation comme le logo de l’entreprise

Si les utilisateurs devaient plutôt entrer ces paramètres, ils pourraient le faire incorrectement, ce qui occasionnerait plus de travail à votre assistance technique et ralentirait l’adoption des nouvelles applications.

Les stratégies de configuration des applications peuvent vous aider à éliminer les problèmes d’installation des applications en vous permettant d’affecter des paramètres de configuration à une stratégie à son tour affectée aux utilisateurs avant qu’ils n’exécutent l’application. Les paramètres sont alors fournis automatiquement, les utilisateurs n’ont aucune action à effectuer.

Les paramètres de configuration sont utilisés chaque fois que l’application les vérifie. En général, une application vérifie les paramètres de configuration la première fois qu’elle est exécutée par l’utilisateur.

Vous disposez de deux options pour indiquer la façon dont vous souhaitez utiliser des configurations d’applications avec Intune :
- **Appareils gérés** : l’appareil est géré par Intune en tant que fournisseur de gestion des appareils mobiles (MDM).
- **Applications gérées** : une application est gérée sans inscription des appareils.

> [!NOTE]
> En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. Les applications connexes traitent la configuration d’application, suppriment et bloquent les comptes non approuvés.

## <a name="apps-that-support-app-configuration"></a>Applications qui prennent en charge la configuration d’application

### <a name="managed-devices"></a>Appareils gérés
Vous pouvez utiliser des stratégies de configuration d’applications pour les applications qui les prennent en charge. Pour que la configuration des applications soit prise en charge dans Intune, les applications doivent avoir été écrites afin de prendre en charge l’utilisation des configurations d’applications, tel que défini par la [Communauté Appconfig](https://www.appconfig.org/members). Pour plus de détails, consultez l’éditeur de l’application.

### <a name="managed-apps"></a>Applications gérées
Vous pouvez préparer votre application métier en incorporant le SDK d’application Intune dans l’application ou en enveloppant (wrap) l’application une fois qu’elle a été développée. Le Kit de développement logiciel (SDK) des applications Intune, disponible pour iOS et Android, permet d'appliquer des stratégies de protection des applications Intune sur votre application. Il s’efforce de minimiser la quantité de modifications du code pour les développeurs d’applications. Pour plus d’informations, consultez [Vue d’ensemble du SDK d’application Intune](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Prise en charge de l’API Graph pour la configuration d’application

En outre, vous pouvez utiliser l’API Graph pour accomplir des tâches de configuration d’application. Pour plus d’informations, consultez [Configuration ciblée de gestion des applications mobiles de référence pour API Graph](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Étapes suivantes

### <a name="managed-devices"></a>Appareils gérés

- Découvrez comment utiliser la configuration d’application avec vos appareils iOS.  Consultez [Ajouter des stratégies de configuration d’applications pour les appareils iOS gérés](app-configuration-policies-use-ios.md).
- Découvrez comment utiliser la configuration d’application avec vos appareils Android.  Consultez [Ajouter des stratégies de configuration d’applications pour les appareils Android gérés](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Applications gérées

- Découvrez comment utiliser la configuration d’application avec des applications gérées. Consultez [Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil](app-configuration-policies-managed-app.md).
