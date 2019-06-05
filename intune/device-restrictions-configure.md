---
title: Configurer des paramètres de restriction d’appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Ajouter un profil d’appareil pour limiter les fonctionnalités sur les appareils Android, Mac OS, iOS, Windows Phone et Windows 10 dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cae90723c7ff92a8042f068fb49c1709506c7ff
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412438"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurer des paramètres de restriction d’appareils dans Microsoft Intune

Les restrictions de l’appareil vous permettent de contrôler un large éventail de paramètres et de fonctionnalités que vous gérez dans diverses catégories comme :
- Sécurité
- Navigateur
- Matériel
- Paramètres de partage des données

Par exemple, vous pouvez créer un profil de restriction de l’appareil qui empêche les utilisateurs d’appareils iOS d’accéder à l’appareil photo.

Découvrez les principes de base des profils de restriction, puis lisez d’autres articles décrivant les spécificités des appareils sur chaque plateforme.

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez un **Nom** et une **Description** pour le profil de restriction de l’appareil.
4. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres personnalisés. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres de restriction de l’appareil :

    - **Android**
    - **Android Entreprise**
    - **iOS**
    - **MacOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 et versions ultérieures**
    - **Windows 10 et versions ultérieures**

5. Dans la liste déroulante **Type de profil**, choisissez **Restrictions de l’appareil**. Si vous souhaitez créer un profil de restrictions pour des appareils Windows 10 Collaboration, par exemple Surface Hub, choisissez **Restrictions des appareils (Windows 10 Collaboration)** .
6. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Choisissez votre plateforme pour connaître les paramètres détaillés :

    - [Paramètres Android](device-restrictions-android.md)
    - [Paramètres Android pour les entreprises](device-restrictions-android-for-work.md)
    - [Paramètres iOS](device-restrictions-ios.md)
    - [Paramètres macOS](device-restrictions-macos.md)
    - [Paramètres Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Paramètres Windows 10](device-restrictions-windows-10.md)
    - [Paramètres Windows 10 Collaboration](device-restrictions-windows-10-teams.md)
    - [Paramètres Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
