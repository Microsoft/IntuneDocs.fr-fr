---
title: Restreindre des fonctionnalités d’appareils à l'aide d'une stratégie dans Microsoft Intune - Azure | Microsoft Docs
description: Ajouter un profil d’appareil pour limiter les fonctionnalités sur les appareils Android, macOS, iOS, iPadOS, Windows Phone et Windows 10 dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 704da2ee4f0f2e6dce222c89704c83a35368c02c
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059533"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurer des paramètres de restriction d’appareils dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune inclut des stratégies de restriction d’appareil qui aident les administrateurs à contrôler les appareils Android, iOS, macOS et Windows. Ces restrictions vous permettent de contrôler un large éventail de paramètres et de fonctionnalités pour protéger les ressources de votre entreprise. Par exemple, les administrateurs peuvent faire ce qui suit :

- Autoriser ou bloquer l'appareil photo
- Contrôler l'accès à Google Play, aux magasins d'applications, à la consultation de documents, et aux jeux
- Bloquer les applications intégrées ou créer une liste des applications autorisées ou interdites
- Autoriser ou empêcher la sauvegarde de fichiers sur des comptes dans le cloud et de stockage
- Définir une longueur minimale de mot de passe et bloquer les mots de passe simples

Ces fonctionnalités, disponibles dans Intune, sont configurables par l’administrateur. Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités dans un profil, vous pouvez alors envoyer (push) ou déployer le profil aux appareils dans votre organisation.

Cet article vous explique comment créer un profil de restrictions d’appareil. Vous pouvez également voir tous les paramètres disponibles pour les différentes plates-formes.

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Attribuez un nom descriptif à la stratégie. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de stratégie correct est **iOS : Bloquer l’appareil photo sur les appareils**.
    - **Description** : Entrez une description de la stratégie. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :  

        - **Android**
        - **Android Entreprise**
        - **iOS/iPadOS**
        - **MacOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 et versions ultérieures**
        - **Windows 10 et versions ultérieures**

    - **Type de profil** : Sélectionnez **Restrictions de l’appareil**.

        Si vous souhaitez créer un profil de restrictions pour des appareils Windows 10 Collaboration, par exemple Surface Hub, choisissez **Restrictions des appareils (Windows 10 Collaboration)** .

4. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Choisissez votre plateforme pour connaître les paramètres détaillés :

    - [Paramètres Android](../device-restrictions-android.md)
    - [Paramètres Android pour les entreprises](../device-restrictions-android-for-work.md)
    - [Paramètres iOS/iPadOS](device-restrictions-ios.md)
    - [Paramètres macOS](device-restrictions-macos.md)
    - [Paramètres Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Paramètres Windows 10](device-restrictions-windows-10.md)
    - [Paramètres Windows 10 Collaboration](device-restrictions-windows-10-teams.md)
    - [Paramètres Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](../device-profile-assign.md) et [superviser son état](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
