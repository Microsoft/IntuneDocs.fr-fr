---
title: Ajouter des paramètres personnalisés aux appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Exportez les paramètres iOS à partir des outils Apple Configurator ou Gestionnaire de profils Apple, puis importez-les dans Microsoft Intune. Ces paramètres peuvent créer, utiliser et contrôler les paramètres et fonctionnalités personnalisés sur les appareils iOS. Vous pouvez ensuite assigner ou distribuer ce profil personnalisé aux appareils iOS de votre organisation pour créer une base de référence ou un standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e1edae77144b85d100bf590716768792afd8470
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565535"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Utiliser des paramètres personnalisés pour les appareils iOS dans Microsoft Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils iOS au moyen de « profils personnalisés ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Quand vous utilisez des appareils iOS, il existe deux façons d’obtenir des paramètres personnalisés dans Intune :

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Gestionnaire de profils Apple](https://support.apple.com/profile-manager)

Vous pouvez utiliser ces outils pour exporter les paramètres dans un profil de configuration. Dans Intune, importez ce fichier, puis attribuez le profil à vos utilisateurs et appareils iOS. Une fois le profil attribué, les paramètres sont distribués et créent une base de référence ou un standard pour iOS dans votre organisation.

Cet article vous montre comment créer un profil personnalisé pour les appareils iOS. Il fournit également des conseils sur l’utilisation d’Apple Configurator et du Gestionnaire de profils Apple.

## <a name="before-you-begin"></a>Avant de commencer

- Quand vous utilisez **Apple Configurator** pour créer le profil de configuration, vérifiez que les paramètres que vous exportez sont compatibles avec la version iOS des appareils dont vous vous servez. Pour plus d’informations sur la résolution des paramètres incompatibles, recherchez les éléments **Configuration Profile Reference** et **Mobile Device Management Protocol Reference** sur le site web [Apple Developer](https://developer.apple.com/).

- Quand vous utilisez le **Gestionnaire de profils Apple**, veillez à effectuer les actions suivantes :

  - Activez la [gestion des appareils mobiles](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) dans le Gestionnaire de profils.
  - Ajoutez des [appareils iOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) dans le Gestionnaire de profils.
  - Une fois que vous avez ajouté un appareil dans le Gestionnaire de profils, accédez à **Sous la bibliothèque**  > **Appareils** > sélectionnez votre appareil > **Réglages**. Entrez les paramètres généraux de l’appareil.

    Téléchargez et enregistrez ce fichier. Vous intégrerez ce fichier au profil Intune.

  - Vérifiez que les paramètres que vous exportez à partir du Gestionnaire de profils Apple sont compatibles avec la version d’iOS sur les appareils que vous utilisez. Pour plus d’informations sur la résolution des paramètres incompatibles, recherchez les éléments **Configuration Profile Reference** et **Mobile Device Management Protocol Reference** sur le site web [Apple Developer](https://developer.apple.com/).

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `ios custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez **iOS**.
    - **Type de profil** : choisissez **Personnalisé**.

4. Dans **Configuration personnalisée**, entrez les paramètres suivants :

    - **Nom du profil de configuration personnalisé** : entrez un nom pour la stratégie. Ce nom est affiché sur l’appareil et dans l’état Intune.
    - **Fichier du profil de configuration** : accédez au profil de configuration que vous avez créé à l’aide de l’outil Apple Configurator ou du Gestionnaire de profils Apple. Le fichier importé s’affiche dans la zone **Contenu du fichier**.

5. Sélectionnez **OK** > **Créer** pour créer le profil Intune. Quand vous avez terminé, votre profil apparaît dans la liste **Configuration de l’appareil - Profils**.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md).

Découvrez comment [créer le profil sur des appareils macOS](custom-settings-macos.md). 
