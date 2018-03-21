---
title: "Créer un profil d’appareil iOS ou macOS avec Microsoft Intune - Azure | Microsoft Docs"
description: "Ajoutez ou créez un profil d’appareil iOS ou macOS, puis configurez les paramètres pour AirPrint, AirPlay, disposition de l’écran d’accueil, notifications des applications, appareil partagé, authentification unique et paramètres de filtre de contenu web dans Microsoft Intune"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e3de7d1bccd57da1290987a714416373cbdd2b0d
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2018
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Paramètres des fonctionnalités de l’appareil iOS ou macOS dans Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Les fonctionnalités de l’appareil vous permettent de contrôler une gamme de paramètres et fonctionnalités sur des appareils iOS et macOS, notamment :

- paramètres AirPrint et AirPlay
- disposition de l’écran d’accueil
- notifications à partir d’applications
- configuration de l'appareil partagé
- Configurer l'authentification unique
- Filtrage du contenu web

Cet article explique les notions de base de la configuration des profils de fonctionnalités d’appareils iOS. Vous pouvez alors parcourir des articles supplémentaires pour configurer les paramètres spécifiques à la plateforme sur vos appareils.

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil**, **Profils**, puis **Créer un profil**.
4. Entrez les propriétés suivantes :

  - **Nom** : attribuez un nom descriptif au nouveau profil.
  - **Description** : (facultatif mais recommandé), entrez une description du profil
  - **Plateforme** : sélectionnez le type de plateformes :
    - **iOS**
    - **MacOS**
  - **Type de profil** : sélectionnez **Fonctionnalités de l’appareil**
  - **Paramètres** : les paramètres varient selon la plateforme que vous choisissez. Les articles suivants décrivent les paramètres pour chaque type de profil :

    - [Paramètres Intune AirPrint pour appareils iOS et Mac OS](air-print-settings-ios-macos.md)
    - [Paramètres Intune AirPlay pour appareils iOS](airplay-settings-ios.md)
    - [Paramètres de disposition de l’écran d’accueil Intune pour les appareils iOS](home-screen-settings-ios.md)
    - [Paramètres de notification des applications Intune pour les appareils iOS](app-notification-settings-ios.md)
    - [Paramètres de configuration des appareils Intune partagés pour iOS](shared-device-settings-ios.md)
    - [Configurer Intune pour l’authentification unique des appareils iOS](sso-ios.md)
    - [Paramètres de filtrage de contenu web Intune pour les appareils iOS](web-content-filter-settings-ios.md)

5. Lorsque vous avez terminé, sélectionnez **OK**, puis choisissez **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste.

## <a name="next-step"></a>Étape suivante

Pour affecter ce profil à des groupes, consultez [Guide pratique pour affecter des profils d’appareil](device-profile-assign.md).