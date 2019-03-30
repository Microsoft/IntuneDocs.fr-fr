---
title: Ajouter des paramètres personnalisés pour les appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil personnalisé pour utiliser les paramètres OMA-URI sur les appareils exécutant Windows 10 dans Microsoft Intune. Utilisez un profil personnalisé pour ajouter des paramètres personnalisés.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44be460ee910818d52179da55151d1bceeb8b306
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565908"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Utiliser des paramètres personnalisés pour les appareils Windows 10 dans Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils Windows 10 au moyen de « profils personnalisés ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Les profils personnalisés Windows 10 utilisent des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour configurer différentes fonctionnalités. Ces paramètres sont généralement utilisés par les fabricants d’appareils mobiles pour contrôler les fonctionnalités sur l’appareil. 

De nombreux paramètres de fournisseur de services de configuration (CSP) sont disponibles dans Windows 10, comme [Fournisseur CSP de stratégie](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Si vous recherchez un paramètre spécifique, n’oubliez pas que le [profil de restriction d’appareil Windows 10](device-restrictions-windows-10.md) comporte de nombreux paramètres intégrés. Vous n’aurez donc peut-être pas besoin d’entrer des valeurs personnalisées.

Cet article :

- Montre comment créer un profil personnalisé pour les appareils Windows 10
- Inclut une liste des paramètres OMA-URI recommandés
- Fournit un exemple d’un profil personnalisé qui ouvre une connexion VPN

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `windows 10 custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez **Windows 10 et ultérieur**.
    - **Type de profil** : choisissez **Personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. entrez les paramètres suivants :

    - **Nom** : entrez un nom unique pour paramètre OMA-URI, qui vous permette de l’identifier dans la liste des paramètres.
    - **Description** : entrez une description qui donne une vue d’ensemble du paramètre et tout autre détail important.
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

## <a name="example"></a>Exemple

Dans l’exemple suivant, le paramètre **Connectivity/AllowVPNOverCellular** est activé. Il permet à un appareil Windows 10 d’ouvrir une connexion VPN sur un réseau de téléphonie mobile.

![Exemple de stratégie personnalisée contenant des paramètres VPN](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Trouver les stratégies que vous pouvez configurer

La liste complète de tous les fournisseurs de services de configuration pris en charge par Windows 10 est disponible dans les [Informations de référence sur les fournisseurs de services de configuration](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Les paramètres ne sont pas tous compatibles avec toutes les versions de Windows 10. [Informations de référence sur les fournisseurs de services de configuration](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) vous indique quelles versions sont prises en charge pour chaque fournisseur de services de configuration.

De plus, Intune ne prend pas en charge tous les paramètres listés dans les [Informations de référence sur les fournisseurs de services de configuration](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference). Pour savoir si Intune prend en charge le paramètre de votre choix, ouvrez l’article relatif à ce paramètre. Chaque page de paramètre indique ses opérations prises en charge. Pour fonctionner avec Intune, le paramètre doit prendre en charge les opérations **Ajouter**, **Remplacer** et **Get**. Si la valeur retournée par la **obtenir** opération ne correspond pas à la valeur fournie par le **ajouter** ou **remplacer** operations, puis Intune signale une erreur de conformité.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md).
