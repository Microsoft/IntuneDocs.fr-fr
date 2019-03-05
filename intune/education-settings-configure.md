---
title: Ajouter ou configurer des paramètres Éducation dans Microsoft Intune – Azure | Microsoft Docs
description: Utilisez l’application Examen dans un profil de configuration d’appareil sur des appareils Windows 10 (et versions ultérieures) dans Microsoft Intune. Créez un profil de configuration avec les paramètres Éducation et entrez une URL de test d’application, choisissez le mode de connexion des utilisateurs, surveillez l’écran pendant le test et autorisez ou empêchez les suggestions de texte pendant le test.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3c34935f161050bae51a2fbbee9b49f9fc1156f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228882"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Utiliser l’application Examen sur des appareils Windows 10 dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les profils Éducation d’Intune sont conçus pour permettre aux étudiants de passer un test ou un examen sur des appareils. Cette fonctionnalité inclut l’application **Examen** et des paramètres servant à ajouter une URL de test, à choisir le mode de connexion des utilisateurs finaux et plus encore. Elle est compatible avec la plateforme suivante :

- Windows 10 et versions ultérieures

Lorsque l’utilisateur se connecte, l’application Examen s’ouvre automatiquement sur le test que vous avez entré. Aucune autre application ne peut s’exécuter sur l’appareil tant que le test est en cours. Pour plus d’informations sur l’application Examen, voir [Passer des tests sur Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).

Cet article liste les étapes à suivre pour créer un profil de configuration d’appareil dans Microsoft Intune. Il comporte également des informations sur les paramètres Éducation disponibles pour les appareils Windows 10.

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez **Windows 10 et ultérieur**.
    - **Profil** : choisissez **Profil Éducation**.

4. Entrez les paramètres à configurer :

    - [Windows 10 et versions ultérieures](education-settings-windows.md)

5. Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Une fois que vous avez entré les paramètres et créé le profil, ce dernier apparaît dans la liste des profils. Ensuite, [affectez ce profil à certains groupes](device-profile-assign.md).

## <a name="next-steps"></a>Étapes suivantes

Voir la liste des [Paramètres Windows 10 Éducation](education-settings-windows.md) et leur description.

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
