---
title: Ajouter des paramètres personnalisés aux appareils Windows Phone 8.1 dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez ou créez un profil personnalisé pour utiliser les paramètres OMA-URI sur les appareils exécutant Windows Phone 8.1 dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb54f5e4cede6141c87073a7dfb6570cf85e920b
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042899"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Utiliser des paramètres personnalisés pour les appareils Windows Phone 8.1 dans Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils Windows Phone 8.1 au moyen de « profils personnalisés ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Les profils personnalisés Windows Phone 8.1 utilisent des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour configurer différentes fonctionnalités. Ces paramètres sont généralement utilisés par les fabricants d’appareils mobiles pour contrôler les fonctionnalités sur l’appareil.

Cet article vous montre comment créer un profil personnalisé pour les appareils Windows Phone 8.1. 

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `windows phone custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez **Windows Phone 8.1**.
    - **Type de profil** : choisissez **Personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. entrez les paramètres suivants :

    - **Nom** : entrez un nom unique pour paramètre OMA-URI, qui vous permette de l’identifier dans la liste des paramètres.
    - **Description** : entrez une description générale du paramètre et toute information pertinente pour faciliter la recherche du profil.
    - **OMA-URI (sensible à la casse)**  : entrez l’identificateur OMA-URI à utiliser comme paramètre.
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

Découvrez comment créer un profil personnalisé sur les [appareils Windows 10](custom-settings-windows-10.md).
