---
title: Paramètres Kiosk pour Windows Holographic for Business dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez vos appareils Windows Holographic for Business en tant que kiosques monoapplication et multiapplication, personnalisez le menu Démarrer, ajoutez des applications, affichez la barre des tâches et configurez un navigateur web dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f38803d3be05182639ac8eca2578e9ce121f7c2f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566010"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Paramètres d’appareils Windows Holographic for Business à exécuter en tant que kiosques dans Intune

Vous pouvez configurer les appareils Windows Holographic for Business pour qu’ils s’exécutent en mode kiosque mono-application ou en mode kiosque multi-application. Certaines fonctionnalités ne sont pas prises en charge sur Windows Holographic for Business.

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Windows Holographic for Business. Dans le cadre de votre solution MDM (gestion des appareils mobiles), utilisez ces paramètres pour configurer vos appareils Windows Holographic for Business afin qu’ils s’exécutent en mode kiosque.

En tant qu’administrateur Intune, vous pouvez créer et affecter ces paramètres à vos appareils.

Pour en savoir plus sur la fonctionnalité de kiosque Windows dans Intune, consultez [Configurer les paramètres kiosque](kiosk-settings.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez le profil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran

Lorsque vous choisissez le mode kiosque à application unique, entrez les paramètres suivants :

- **Type d’ouverture de session d’utilisateur** : sélectionnez **Compte d’utilisateur local** pour entrer le compte d’utilisateur local (sur l’appareil) ou un compte Microsoft Account (MSA) associé à l’application kiosque. Les types de comptes d’utilisateur **Ouverture de session automatique** ne sont pas pris en charge sur Windows Holographic for Business.

- **Type d’application** : sélectionnez **application Store**.

- **Application à exécuter en mode kiosque** : choisissez **Ajouter une application Store**, puis sélectionnez une application dans la liste.

    Aucune application n’est répertoriée ? En ajouter à l’aide de la procédure sous [Applications clientes](apps-add.md).

    Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="multi-app-kiosks"></a>Applications multiples plein écran

Dans ce mode, les applications sont disponibles dans le menu Démarrer. Ce sont les seules applications que l’utilisateur peut ouvrir. Lorsque vous choisissez le mode kiosque multi-application, entrez les paramètres suivants :

- **Cibler Windows 10 dans les appareils en mode S** : choisissez **Non**. Le mode S n’est pas pris en charge sur Windows Holographic for Business.

- **Type d’ouverture de session d’utilisateur** : ajoutez un ou plusieurs comptes d’utilisateurs qui peuvent utiliser les applications que vous ajoutez. Les options disponibles sont les suivantes : 

  - **Ouverture de session automatique** : pas prise en charge sur Windows Holographic for Business.
  - **Comptes d'utilisateurs locaux** : **Ajouter** le compte d'utilisateur local (à l’appareil). Le compte que vous entrez est utilisé pour la connexion au kiosque.
  - **Utilisateur ou groupe Azure AD (Windows 10, version 1803 et versions ultérieures)**  : nécessite des informations d’identification de l’utilisateur pour se connecter à l’appareil. Sélectionnez **Ajouter** pour choisir les utilisateurs ou groupes Azure AD dans la liste. Vous pouvez sélectionner plusieurs utilisateurs et groupes. Choisissez **Sélectionner** pour enregistrer vos changements.
  - **Visiteur HoloLens** : Le compte visiteur est un compte invité ne nécessitant pas d’informations d’identification de l’utilisateur ou d’authentification, comme décrit dans [Concepts du mode PC partagé](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applications** : ajoutez les applications à exécuter sur l’appareil kiosque. N’oubliez pas que vous pouvez ajouter plusieurs applications.

  - **Ajouter des applications Store** : sélectionnez une application existante que vous avez ajoutée avec [Applications clientes](apps-add.md). Si vous n’avez aucune application répertoriée, vous pouvez obtenir des applications et [les ajouter à Intune](store-apps-windows.md).
  - **Ajouter une application Win32** : pas pris en charge sur Windows Holographic for Business.
  - **Ajouter par AUMID** : utilisez cette option pour ajouter des applications Windows de boîte de réception. Entrez les propriétés suivantes : 

    - **Nom de l’application** : requis. Entrez un nom pour l'application.
    - **Identifiant du modèle utilisateur de l’application (AUMID)**  : requis. Entrez l’identifiant AUMID de l’application Windows. Pour obtenir cet ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Taille de la mosaïque** : requise. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.

- **Paramètres du navigateur de kiosque** : pas pris en charge sur Windows Holographic for Business.

- **Utiliser une autre mise en page de démarrage** : choisissez **Oui** pour entrer un fichier XML qui décrit comment les applications s’affichent dans le menu Démarrer, notamment l’ordre des applications. Utilisez cette option si vous avez besoin de davantage de personnalisation dans votre menu Démarrer. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) fournit quelques conseils et inclut un fichier XML spécifique pour les appareils Windows Holographic for Business.

- **Barre des tâches Windows** : pas prise en charge sur Windows Holographic for Business.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils plein écran pour des appareils [Android](device-restrictions-android.md#kiosk), [Android pour les entreprises](device-restrictions-android-for-work.md#dedicated-device-settings) et [Windows 10 et versions ultérieures](kiosk-settings-windows.md).
