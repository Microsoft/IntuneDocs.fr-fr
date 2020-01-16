---
title: Stratégie Microsoft Intune pour autoriser ou bloquer des applications pour Samsung Knox
titleSuffix: ''
description: Créez un profil personnalisé pour autoriser et bloquer des applications pour les appareils Samsung Knox Standard.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207075"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Utiliser des stratégies personnalisées dans Microsoft Intune pour autoriser et bloquer des applications pour les appareils Samsung Knox Standard 

Appliquez la procédure de cet article pour créer une stratégie personnalisée Microsoft Intune qui crée l’un des éléments suivants :

- Une liste d’applications qui sont bloquées sur l’appareil. Les applications figurant dans cette liste ne peuvent pas s’exécuter, même si elles étaient déjà installées quand la stratégie a été appliquée.
- Une liste d’applications que les utilisateurs de l’appareil sont autorisés à installer à partir du magasin Google Play. Seules les applications figurant dans la liste peuvent être installées. Aucune autre application ne peut être installée à partir du Store.

Ces paramètres peuvent uniquement être utilisés par les appareils qui exécutent Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Créer une liste d’applications autorisées ou bloquées

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Saisissez les paramètres suivants :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil correct est le **profil personnalisé Windows Phone**.
    - **Description** : entrez une description qui présente le paramètre et tout autre détail important.
    - **Plateforme** : Sélectionnez **Android**.
    - **Type de profil**: sélectionnez **personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. Saisissez les paramètres suivants :

    Pour afficher une liste d’applications qui sont bloquées sur l’appareil :

    - **Nom** : Entrez **PreventStartPackages**.
    - **Description** : entrez une description générale du paramètre et toute information pertinente pour faciliter la recherche du profil. Par exemple, entrez la **liste des applications dont l’exécution est bloquée**.
    - **OMA-URI (sensible à la casse)**  : entrez **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
    - **Type de données**: sélectionnez **chaîne**.
    - **Valeur** : Entrez une liste de noms de packages d’applications que vous souhaitez autoriser. Vous pouvez utiliser `;`, `:` ou `|` comme délimiteur. Par exemple, entrez `package1;package2;`.

   Pour obtenir la liste des applications que les utilisateurs sont autorisés à installer à partir du Google Play Store tout en excluant toutes les autres applications :

    - **Nom** : Entrez **AllowInstallPackages**.
    - **Description** : entrez une description générale du paramètre et toute information pertinente pour faciliter la recherche du profil. Par exemple, entrez la **liste des applications que les utilisateurs peuvent installer à partir de Google Play**.
    - **OMA-URI (sensible à la casse)**  : entrez **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
    - **Type de données**: sélectionnez **chaîne**.
    - **Valeur** : Entrez une liste de noms de packages d’applications que vous souhaitez autoriser. Vous pouvez utiliser `;`, `:` ou `|` comme délimiteur. Par exemple, entrez `package1;package2;`.

5. Cliquez sur **OK** pour enregistrer vos modifications.
6. Une fois terminé, sélectionnez **OK** > **Créer** pour créer le profil Intune. Quand vous avez terminé, votre profil apparaît dans la liste **Appareils - Profils de configuration**.

>[!TIP]
> Vous pouvez connaître l’ID de package d’une application en accédant à l’application dans le Google Play Store. L’ID de package est contenu dans l’URL de la page d’application. Par exemple, l’ID de package de l’application Microsoft Word est **com.microsoft.office.word**.

La prochaine fois que chaque appareil ciblé se connecte, les paramètres d’application sont appliqués.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Ensuite, [attribuez le profil](../device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).
