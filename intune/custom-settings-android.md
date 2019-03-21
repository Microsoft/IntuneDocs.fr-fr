---
title: Ajouter des paramètres personnalisés aux appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Ajouter ou créer un profil personnalisé pour les appareils Android afin de créer un profil Wi-Fi avec une clé prépartagée, créer un profil VPN par application ou autoriser/bloquer des applications pour les appareils Samsung Knox Standard dans Microsoft Intune
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
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba6d2f60d91388aa1c8ceea6580f1d583d4c987c
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564820"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Utiliser des paramètres personnalisés pour les appareils Android dans Microsoft Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils Android au moyen d’un « profil personnalisé ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Les profils personnalisés Android utilisent des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour configurer différentes fonctionnalités sur les appareils Android. Ces paramètres sont généralement utilisés par les fabricants d’appareils mobiles pour contrôler ces fonctionnalités.

Avec un profil personnalisé, vous pouvez configurer et attribuer les paramètres Android suivants. Les paramètres suivants ne sont pas intégrés à Intune :

- [Création d’un profil Wi-Fi avec une clé prépartagée](/intune/wi-fi-profile-shared-key)
- [Créer un profil VPN par application](/intune/android-pulse-secure-per-app-vpn)
- [Autoriser et bloquer des applications pour les appareils Samsung Knox Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Seuls les paramètres listés peuvent être configurés dans un profil personnalisé. Les appareils Android n’exposent pas une liste complète des paramètres OMA-URI que vous pouvez configurer. Si vous souhaitez afficher davantage de paramètres, votez pour des paramètres supplémentaires sur le [site Intune Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas).

Cet article vous montre comment créer un profil personnalisé pour les appareils Android.

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `android custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez **Android**.
    - **Type de profil** : choisissez **Personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. entrez les paramètres suivants :

    - **Nom** : entrez un nom unique pour le paramètre OMA-URI afin de le retrouver facilement.
    - **Description** : entrez une description qui donne une vue d’ensemble du paramètre et tout autre détail important.
    - **OMA-URI** : entrez l’identificateur OMA-URI à utiliser comme paramètre.
    - **Type de données** : choisissez le type de données que vous allez utiliser pour ce paramètre OMA-URI. Les options disponibles sont les suivantes :

      - Chaîne
      - Chaîne (fichier XML)
      - Date et heure
      - Entier
      - Virgule flottante
      - Booléen
      - Base64 (fichier)

    - **Valeur** : entrez la valeur de données à associer à l’identificateur OMA-URI que vous avez entré. La valeur dépend du type de données que vous avez sélectionné. Par exemple, si vous choisissez **Date et heure**, sélectionnez la valeur à partir d’un sélecteur de dates.

    Une fois que vous avez ajouté des paramètres, vous pouvez sélectionner **Exporter**. L’option **Exporter** crée une liste de toutes les valeurs que vous avez ajoutées dans un fichier de valeurs séparées par des virgules (.csv).

5. Cliquez sur **OK** pour enregistrer vos modifications. Continuez à ajouter d’autres paramètres si besoin. 
6. Quand vous avez terminé, choisissez **OK** > **Créer** pour créer le profil Intune. Quand vous avez terminé, votre profil apparaît dans la liste **Configuration de l’appareil - Profils**.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md).

Découvrez comment [créer le profil sur des appareils Android Entreprise](custom-settings-android-for-work.md).
