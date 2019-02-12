---
title: Utiliser des paramètres d’appareil personnalisés dans Microsoft Intune - Azure | Microsoft Docs
description: Ajouter ou créer un profil afin d’utiliser des paramètres personnalisés pour des appareils Windows Phone, Windows 8.1, Windows 10 et ultérieur, Android, Android Entreprise, macOS et iOS à l’aide de Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dd1ea3b6365cd93d7df78597a2e379ebaec7103
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836368"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Créer un profil avec des paramètres personnalisés dans Intune

## <a name="what-are-custom-profiles"></a>Présentation des profils personnalisés

Microsoft Intune comprend de nombreux paramètres intégrés pour contrôler différentes fonctionnalités sur un appareil. Vous pouvez également créer des profils personnalisés. Les profils personnalisés sont idéaux pour utiliser des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune. Ces profils comprennent des fonctionnalités et des paramètres que vous pouvez contrôler sur les appareils de votre organisation. Par exemple, vous pouvez créer un profil personnalisé qui définit la même fonctionnalité pour tous les appareils iOS.

Pour plus d’informations sur les profils de configuration, consultez [Que sont les profils d’appareil Microsoft Intune ?](device-profiles.md). 

Cet article inclut des liens permettant de créer des profils personnalisés pour Android, Android Entreprise, iOS, macOS et Windows.

## <a name="available-platforms"></a>Plateformes disponibles

Les paramètres personnalisés sont configurés différemment pour chaque plateforme. Par exemple, pour contrôler les fonctionnalités sur des appareils Android et Windows, vous pouvez entrer des valeurs OMA-URI (Open Mobile Alliance Uniform Resource Identifier). Pour les appareils Apple, vous pouvez importer un fichier que vous avez créé dans l’outil [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) ou le [Gestionnaire de profils Apple](https://support.apple.com/profile-manager).

Les profils personnalisés sont créés de la même façon que les profils intégrés et sont disponibles sur les plateformes suivantes :

- [Android](custom-settings-android.md)
- [Android Entreprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [MacOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>Étapes suivantes

Choisissez votre plateforme et lancez-vous :

- [Android](custom-settings-android.md)
- [Android Entreprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [MacOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
