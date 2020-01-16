---
title: Ajouter des paramètres personnalisés aux appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Ajouter ou créer un profil personnalisé pour les appareils Android afin de créer un profil Wi-Fi avec une clé prépartagée, créer un profil VPN par application ou autoriser/bloquer des applications pour les appareils Samsung Knox Standard dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8137a806598facd540781702b1c2c359e89d6bda
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206786"
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

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Saisissez les paramètres suivants :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil correct est un **profil personnalisé Android**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Android**.
    - **Type de profil**: sélectionnez **personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. Saisissez les paramètres suivants :

    - **Nom** : entrez un nom unique pour le paramètre OMA-URI afin de le retrouver facilement.
    - **Description** : entrez une description qui présente le paramètre et tout autre détail important.
    - **OMA-URI** : entrez l’identificateur OMA-URI à utiliser comme paramètre.
    - **Type de données** : choisissez le type de données que vous allez utiliser pour ce paramètre OMA-URI. Les options disponibles sont les suivantes :

      - Chaîne
      - Chaîne (fichier XML)
      - Date et heure
      - Entier
      - Virgule flottante
      - Booléen
      - Base64 (fichier)

    - **Valeur** : entrez la valeur de données à associer à l’identificateur OMA-URI que vous avez entré. La valeur dépend du type de données que vous avez sélectionné. Par exemple, si vous choisissez **Date et heure**, sélectionnez la valeur à partir d’un sélecteur de dates.

    Une fois que vous avez ajouté des paramètres, vous pouvez sélectionner **Exporter**. L’option **Exporter** crée une liste de toutes les valeurs que vous avez ajoutées dans un fichier de valeurs séparées par des virgules (.csv).

5. Cliquez sur **OK** pour enregistrer vos modifications. Continuez à ajouter d’autres paramètres si besoin.
6. Une fois terminé, sélectionnez **OK** > **Créer** pour créer le profil Intune. Quand vous avez terminé, votre profil apparaît dans la liste **Appareils - Profils de configuration**.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](../device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Créez un [profil personnalisé sur les appareils Android Enterprise](custom-settings-android-for-work.md).
