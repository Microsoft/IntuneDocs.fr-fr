---
title: Paramètres de plein écran pour les appareils Windows et Holographic dans Microsoft Intune – Azure | Microsoft Docs
description: Configurez vos appareils Windows 10 (et versions ultérieures) et Windows Holographic for Business en tant que bornes monoapplications et multiapplications, personnalisez le menu Démarrer, ajoutez des applications, affichez la barre des tâches et configurez un navigateur web dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19641a36cf429773a8c0e06a90ee279d2baa06f7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723916"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Paramètres des appareils Windows 10 et Windows Holographic for Business à exécuter en tant que bornes dédiées avec Intune

Sur les appareils Windows 10, utilisez Intune pour exécuter ces derniers en tant que kiosques, parfois appelés appareils dédiés. Un appareil en mode kiosque peut exécuter une ou plusieurs applications. Vous pouvez afficher et personnaliser un menu de démarrage, ajouter différentes applications, notamment les applications Win32, ajouter une page d’accueil spécifique à un navigateur web, et bien plus encore. 

Cette fonctionnalité s’applique aux appareils qui fonctionnent sous :

- Windows 10 et versions ultérieures
- Windows Holographic for Business

Intune prend en charge un profil de kiosque par appareil. Si vous avez besoin de plusieurs profils de kiosque sur un seul appareil, vous pouvez utiliser un [OMA-URI personnalisé](custom-settings-windows-10.md).

Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités à un profil, envoyez (push) ou déployez ces paramètres auprès des différents groupes de votre organisation.

Cet article explique comment créer un profil de configuration d’appareil. Pour connaître la liste de tous les paramètres, ainsi que leur rôle, voir [Paramètres de plein écran Windows 10](kiosk-settings-windows.md) et [Paramètres de plein écran Windows Holographic for Business](kiosk-settings-holographic.md).

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

   - **Nom** : Entrez un nom descriptif pour le nouveau profil.
   - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**
   - **Type de profil** : Sélectionnez **Kiosque**

4. Dans **Paramètres**, sélectionnez un **mode plein écran**. **Mode kiosque** : identifie le type de mode kiosque pris en charge par la stratégie. Les options sont les suivantes :

    - **Non configuré** (par défaut) : La stratégie n’active pas le mode kiosque.
    - **Kiosque plein écran mono-application** : l’appareil s’exécute en tant que compte d’utilisateur unique et le verrouille sur une seule application de Store. De cette façon, quand l’utilisateur se connecte, une application spécifique démarre. Ce mode empêche également l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
    - **Kiosque multiapplication** : l’appareil exécute plusieurs applications de Store, des applications Win32 ou des applications fournies avec Windows à l’aide de l’AUMID (ID de modèle utilisateur d’application). Seules les applications que vous ajoutez sont disponibles sur l’appareil.

        L’avantage d’un kiosque multiapplication ou d’un appareil à usage fixe est que l’utilisateur accède uniquement aux applications dont il a besoin. Celles dont il n’a pas besoin sont retirées de sa vue.

    Pour obtenir la liste de tous les paramètres, ainsi que leur rôle, voir :
      - [Paramètres de plein écran Windows 10](kiosk-settings-windows.md)
      - [Paramètres de plein écran Windows Holographic for Business](kiosk-settings-holographic.md)

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications. 

Le profil est créé et apparaît dans la liste des profils. Maintenant, [affectez-le](device-profile-assign.md).

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Il est possible de créer des profils de plein écran pour les appareils qui fonctionnent sur les plateformes suivantes :
- [Android](device-restrictions-android.md#kiosk)
- [Android Entreprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 et versions ultérieures](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
