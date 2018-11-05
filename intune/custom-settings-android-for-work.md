---
title: Ajouter des paramètres personnalisés aux appareils Android Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Ajouter ou créer un profil personnalisé pour les appareils Android Entreprise dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a622264ed7cc091849bacbd02f8ae7bdb33603fe
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983140"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Utiliser des paramètres personnalisés pour les appareils Android Entreprise dans Microsoft Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils Android Entreprise au moyen d’un « profil personnalisé ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Les profils personnalisés Android Entreprise utilisent des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour contrôler les fonctionnalités sur les appareils Android Entreprise. Ces paramètres sont généralement utilisés par les fabricants d’appareils mobiles pour contrôler ces fonctionnalités.

Intune prend en charge un nombre limité de profils personnalisés Android.

Cet article vous montre comment créer un profil personnalisé pour les appareils Android Entreprise. Il fournit également un exemple d’un profil personnalisé qui bloque la fonction copier/coller.

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `android enterprise custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez Choose **Android Entreprise**.
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

## <a name="example"></a>Exemple

Dans cet exemple, vous créez un profil personnalisé qui restreint les actions de copier et coller entre applications professionnelles et personnelles sur les appareils Android Entreprise.

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `android ent block copy paste custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez **Android Entreprise**.
    - **Type de profil** : choisissez **Personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. entrez les paramètres suivants :

    - **Nom** : entrez quelque chose comme `Block copy and paste`.
    - **Description** : entrez quelque chose comme `Blocks copy/paste between work and personal apps`.
    - **OMA-URI** : entrez `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Type de données** : choisissez **Booléen** afin que la valeur de cet identificateur OMA-URI soit **Vrai** ou **Faux**.
    - **Valeur** : choisissez **Vrai**.

5. Une fois les paramètres entrés, votre environnement doit ressembler à l’image suivante :

    ![Bloquer la fonction copier/coller pour un profil professionnel Android.](./media/custom-policy-afw-copy-paste.png)

Quand vous attribuez ce profil aux appareils Android Entreprise que vous gérez, la fonction copier/coller est bloquée entre les applications du profil professionnel et du profil personnel.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md).

Découvrez comment [créer le profil sur des appareils Android](custom-settings-android.md).