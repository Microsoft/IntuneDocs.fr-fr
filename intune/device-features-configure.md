---
title: Créer un profil d’appareil iOS ou macOS avec Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil d’appareil iOS ou macOS, puis configurez les paramètres pour AirPrint, disposition de l’écran d’accueil, notifications des applications, appareil partagé, authentification unique et paramètres de filtre de contenu web dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aad3ad2a4f2e45fd94de057500686a718e8ee024
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839454"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Paramètres des fonctionnalités de l’appareil iOS ou macOS dans Intune

Intune inclut de nombreuses fonctionnalités et paramètres qui aident les administrateurs à contrôler des appareils iOS et macOS. Par exemple, les administrateurs peuvent faire ce qui suit :

- Autoriser les utilisateurs à accéder à des imprimantes AirPrint sur votre réseau
- Ajouter des applications et dossiers à l’écran d’accueil, notamment ajouter de nouvelles pages
- Choisir si et comment des notifications de l’application s’affichent
- Configurer l’écran de verrouillage pour afficher un message ou l’étiquette d’inventaire, en particulier pour les appareils partagés
- Donner aux utilisateurs une expérience d’authentification unique sécurisée pour partager des informations d’identification entre les applications
- Filtrer les sites web qui utilisent du langage réservé aux adultes et autoriser ou bloquer des sites web spécifiques

Ces fonctionnalités sont disponibles dans Intune et sont configurables par l’administrateur. Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités dans un profil, vous pouvez alors envoyer (push) ou déployer le profil aux appareils iOS et macOS dans votre organisation.

Cet article vous montre comment créer un profil de configuration d’appareil. Vous pouvez également voir tous les paramètres disponibles pour les appareils [iOS](ios-device-features-settings.md) et [macOS](macos-device-features-settings.md).

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez votre plateforme :
        - **iOS**
        - **MacOS**
    - **Type de profil** : sélectionnez **Fonctionnalités de l’appareil**.
    - **Paramètres** : Entrez les paramètres à configurer. Pour obtenir la liste de tous les paramètres, et ce qu’ils font, consultez :

        - [iOS](ios-device-features-settings.md)
        - [MacOS](macos-device-features-settings.md)

4. Lorsque vous avez terminé, sélectionnez **OK**, puis choisissez **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste. [Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Affichez tous les paramètres des fonctionnalités de l’appareil pour les appareils [iOS](ios-device-features-settings.md) et [macOS](macos-device-features-settings.md).
