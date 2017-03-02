---
title: "Paramètres personnalisés d’Intune pour les appareils macOS | Préversion Intune Azure | Microsoft Docs"
description: "Préversion Intune Azure : découvrez les paramètres que vous pouvez utiliser dans un profil personnalisé macOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 13648aa35057201ac7420e2f1d334aee206605fe
ms.lasthandoff: 02/16/2017


---

# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Paramètres personnalisés pour les appareils Mac OS dans Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilisez le profil personnalisée macOS de Microsoft Intune pour déployer les paramètres que vous avez créés à l’aide de [l’outil Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) sur des appareils macOS. Cet outil vous permet de créer plusieurs paramètres qui contrôlent le fonctionnement de ces appareils et de les exporter vers un profil de configuration. Vous pouvez ensuite importer ce profil de configuration dans un profil personnalisé macOS Intune et déployer les paramètres sur les utilisateurs et les appareils de votre organisation.

Cette fonctionnalité vous permet de déployer des paramètres macOS qui ne sont pas configurables avec des types de profil Intune.


1. Suivez les instructions figurant dans le [Guide pratique pour configurer des paramètres d’appareils personnalisés](how-to-configure-custom-settings.md) pour commencer.
2. Dans le panneau **Créer un profil**, spécifiez les valeurs suivantes :

- **Nom du profil de configuration personnalisé** : entrez le nom de la stratégie tel qu’il sera affiché sur l’appareil et dans l'état Intune.
- **Fichier du profil de configuration** : accédez au profil de configuration que vous avez créé à l’aide de l’outil Apple Configurator.
Vérifiez que les paramètres que vous exportez à partir de l'outil Apple Configurator sont compatibles avec la version de macOS sur les appareils sur lesquels vous déployez la stratégie personnalisée macOS. Pour en savoir plus sur la résolution des paramètres incompatibles, recherchez l’élément **Configuration Profile Reference** et **Mobile Device Management Protocol Reference** sur le site web [Apple Developer](https://developer.apple.com/).

Le fichier importé s’affichera dans la zone **Contenu du fichier** du panneau.
