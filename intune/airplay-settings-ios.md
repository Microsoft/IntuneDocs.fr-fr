---
title: "Paramètres Intune AirPlay pour appareils iOS"
titlesuffix: Azure portal
description: "Découvrez comment utiliser Intune pour connecter automatiquement des appareils iOS à des appareils compatibles AirPlay."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9de6f0e2f7c74e7aec45c27f0fa20189b26c5e22
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="intune-airplay-settings-for-ios-devices"></a>Paramètres Intune AirPlay pour appareils iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilisez ces paramètres pour vous aider à connecter des appareils iOS que vous gérez à des appareils compatibles AirPlay (tels que des téléviseurs Apple) de votre réseau.
Avec cette fonctionnalité, vous pouvez :

- **Configurer une liste d’appareils et de mots de passe** - laissez les utilisateurs se connecter automatiquement aux appareils AirPlay qui se trouvent à portée. Configurez-les avec le nom et le mot de passe des appareils AirPlay afin qu’ils n’aient pas besoin de les fournir lorsqu’ils se connectent.
- **Configurer des destinations autorisées** : configurez une liste d’appareils AirPlay (par ID d’appareil). Les utilisateurs finaux peuvent uniquement voir et se connecter aux appareils répertoriés (pour les appareils supervisés uniquement).

## <a name="get-started"></a>Prise en main

1. À partir d’[Intune dans le portail Azure](https://portal.azure.com), accédez à [**Fonctionnalités de l’appareil** dans la zone de configuration de l’appareil](device-features-configure.md). 
1. Dans le volet **Fonctionnalités de l’appareil**, sélectionnez **AirPlay**.
2. Dans le volet **AirPlay**, choisissez l’une ou l’autre des actions suivantes, ou les deux :

## <a name="configure-a-device-and-password-list"></a>Configurer une liste d’appareils et de mots de passe

1. Dans le volet **Mots de passe**, entrez le **nom de l’appareil** et le **mot de passe** d’un appareil AirPlay, par exemple **Contoso Apple TV**.
2. Après avoir entré les détails de l’appareil, cliquez sur **Ajouter**. L’appareil s’affiche dans la liste **Nom de l’appareil**.
3. Continuez à ajouter des appareils. Quand vous avez terminé, cliquez sur **OK**.


## <a name="configure-allowed-destinations"></a>Configurer des destinations autorisées

1. Dans le volet **Allowed destinations (supervised only)** (Destinations autorisées [mode supervisé uniquement]), entrez **l’ID d’appareil** d’un appareil AirPlay, par exemple 52:46:CD:51:83:4 C.
2. Après avoir entré l’ID de l’appareil, cliquez sur **Ajouter**. L’ID s’affiche dans la liste **ID d’appareil**.
3. Continuez à ajouter des appareils. Quand vous avez terminé, cliquez sur **OK**.

Vous pouvez également importer des appareils et des mots de passe, ainsi que des destinations autorisées, à partir d’un fichier csv.


## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant affecter le profil d’appareil aux groupes que vous choisissez. Pour plus d’informations, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).

