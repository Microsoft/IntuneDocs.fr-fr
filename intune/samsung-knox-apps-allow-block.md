---
title: Stratégie Microsoft Intune pour autoriser ou bloquer des applications pour Samsung Knox
titlesuffix: ''
description: Créez un profil personnalisé pour autoriser et bloquer des applications pour les appareils Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7c40f17ba05c19cd1bc0967f6d343e5871c0388
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845684"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Utiliser des stratégies personnalisées dans Microsoft Intune pour autoriser et bloquer des applications pour les appareils Samsung Knox Standard 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Appliquez la procédure de cet article pour créer une stratégie personnalisée Microsoft Intune qui crée l’un des éléments suivants :

- Une liste d’applications qui sont bloquées sur l’appareil. Les applications figurant dans cette liste ne peuvent pas s’exécuter, même si elles étaient déjà installées quand la stratégie a été appliquée.
- Une liste d’applications que les utilisateurs de l’appareil sont autorisés à installer à partir du magasin Google Play. Seules les applications figurant dans la liste peuvent être installées. Aucune autre application ne peut être installée à partir du Store.

Ces paramètres peuvent uniquement être utilisés par les appareils qui exécutent Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Créer une liste d’applications autorisées ou bloquées

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le volet **Configuration de l’appareil**, choisissez **Gérer** > **Profils**.
2. Dans le volet de la liste des profils, choisissez **Créer un profil**.
3. Dans le volet **Créer un profil**, entrez un **nom** et éventuellement une **description** pour ce profil d’appareil.
2. Choisissez la **Plateforme** **Android** et le **Type de profil** **Personnalisé**.
3. Cliquez sur **Paramètres**.
3. Dans le volet **Paramètres OMA-URI personnalisés**, choisissez **Ajouter**.
4. Dans la boîte de dialogue **Ajouter ou modifier un paramètre OMA-URI**, spécifiez les paramètres suivants :

   Pour afficher une liste d’applications qui sont bloquées sur l’appareil :

   - **Nom** - Entrez **PreventStartPackages**.
   - **Description** - Entrez une description facultative, comme « Liste des applications dont l’exécution est bloquée ».
   -    **Type de données** - Dans la liste déroulante, choisissez **Chaîne**.
   -    **OMA-URI** - Entrez **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   -    **Valeur** - Entrez une liste de noms de packages d’applications que vous souhaitez autoriser. Vous pouvez utiliser **; : ,** ou **|** comme délimiteur. (Exemple : package1;package2;)

   Pour obtenir la liste des applications que les utilisateurs sont autorisés à installer à partir du Google Play Store tout en excluant toutes les autres applications :
   - **Nom** - Entrez **AllowInstallPackages**.
   - **Description** - Entrez une description facultative, comme « Liste des applications que les utilisateurs peuvent installer à partir de Google Play ».
   - **Type de données** - Dans la liste déroulante, choisissez **Chaîne**.
   - **OMA-URI** - Entrez **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **Valeur** - Entrez une liste de noms de packages d’applications que vous souhaitez autoriser. Vous pouvez utiliser **; : ,** ou **|** comme délimiteur. (Exemple : package1;package2;)

4. Cliquez sur **OK** puis, dans le volet **Créer un profil**, choisissez **Créer**.

>[!TIP]
> Vous pouvez connaître l’ID de package d’une application en accédant à l’application dans le Google Play Store. L’ID de package est contenu dans l’URL de la page d’application. Par exemple, l’ID de package de l’application Microsoft Word est **com.microsoft.office.word**.

La prochaine fois que chaque appareil ciblé se connectera, les paramètres d’application seront appliqués.


<!---## Assign the custom profile--->
