---
title: Ajouter des paramètres personnalisés aux appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Exportez les paramètres iOS à partir des outils Apple Configurator ou Gestionnaire de profils Apple, puis importez-les dans Microsoft Intune. Ces paramètres peuvent créer, utiliser et contrôler les paramètres et fonctionnalités personnalisés sur les appareils iOS. Vous pouvez ensuite assigner ou distribuer ce profil personnalisé aux appareils iOS de votre organisation pour créer une base de référence ou un standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a167fa4f0ddc9832ea70b4281a42b5c0aae5bb81
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74694928"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Utiliser des paramètres personnalisés pour les appareils iOS dans Microsoft Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils iOS au moyen de « profils personnalisés ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Quand vous utilisez des appareils iOS, il existe deux façons d’obtenir des paramètres personnalisés dans Intune :

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Gestionnaire de profils Apple](https://support.apple.com/profile-manager)

Vous pouvez utiliser ces outils pour exporter les paramètres dans un profil de configuration. Dans Intune, importez ce fichier, puis attribuez le profil à vos utilisateurs et appareils iOS. Une fois attribués, les paramètres sont distribués. Ils créent également une ligne de base ou une norme pour iOS dans votre organisation.

Cet article fournit des conseils sur l’utilisation d’Apple Configurator et du gestionnaire de profils Apple, et décrit les propriétés que vous pouvez configurer.

## <a name="before-you-begin"></a>Avant de commencer

[Créez le profil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Lorsque vous utilisez **Apple Configurator** pour créer le profil de configuration, vérifiez que les paramètres exportés sont compatibles avec la version iOS sur les périphériques. Pour plus d’informations sur la résolution des paramètres incompatibles, recherchez les éléments **Configuration Profile Reference** et **Mobile Device Management Protocol Reference** sur le site web [Apple Developer](https://developer.apple.com/).

- Quand vous utilisez le **Gestionnaire de profils Apple**, veillez à effectuer les actions suivantes :

  - Activez la [gestion des appareils mobiles](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) dans le Gestionnaire de profils.
  - Ajoutez des [appareils iOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) dans le Gestionnaire de profils.
  - Une fois que vous avez ajouté un appareil dans le Gestionnaire de profils, accédez à **Sous la bibliothèque**  > **Appareils** > sélectionnez votre appareil > **Réglages**. Entrez les paramètres généraux de l’appareil.

    Téléchargez et enregistrez ce fichier. Vous intégrerez ce fichier au profil Intune.

  - Vérifiez que les paramètres que vous exportez à partir du Gestionnaire de profils Apple sont compatibles avec la version d’iOS sur les périphériques. Pour plus d’informations sur la résolution des paramètres incompatibles, recherchez les éléments **Configuration Profile Reference** et **Mobile Device Management Protocol Reference** sur le site web [Apple Developer](https://developer.apple.com/).

## <a name="custom-configuration-profile-settings"></a>Paramètres du profil de configuration personnalisé

- **Nom du profil de configuration personnalisé** : entrez un nom pour la stratégie. Ce nom est affiché sur l’appareil et dans l’état Intune.
- **Fichier du profil de configuration** : accédez au profil de configuration que vous avez créé à l’aide de l’outil Apple Configurator ou du Gestionnaire de profils Apple. La taille de fichier maximale est de 1 million octets (juste moins de 1 Mo). Le fichier importé s’affiche dans la zone **Contenu du fichier**.

  Vous pouvez également ajouter des jetons d’appareil à vos fichiers de configuration personnalisés. Les jetons de périphérique sont utilisés pour ajouter des informations spécifiques à l’appareil. Par exemple, pour afficher le numéro de série, entrez `{{serialnumber}}`. Sur l’appareil, le texte présente un aspect similaire à `123456789ABC` qui est unique à chaque périphérique. Quand vous entrez les variables, veillez à utiliser des accolades `{{ }}`. [Jetons de configuration d’application](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) inclut une liste de variables qui peuvent être utilisées. Vous pouvez également utiliser `deviceid` ou toute autre valeur propre à l’appareil.

  > [!NOTE]
  > Les variables ne sont pas validées dans l’interface utilisateur et respectent la casse. Par conséquent, vous pouvez voir des profils enregistrés avec une entrée incorrecte. Par exemple, si vous entrez `{{DeviceID}}` au lieu de `{{deviceid}}`, la chaîne littérale s’affiche à la place de l’ID unique de l’appareil. Veillez à entrer les informations correctes.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et affiché dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md).

Découvrez comment [créer le profil sur des appareils macOS](custom-settings-macos.md). 
