---
title: "Paramètres de filtrage de contenu web Intune pour les appareils iOS"
titlesuffix: Azure portal
description: "Découvrez les paramètres que vous pouvez utiliser pour autoriser et bloquer l’accès à des sites web à partir d’appareils iOS."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 54202baa7871f38581f4828bb80213be0f88ef61
ms.sourcegitcommit: 1a390b47b91e743fb0fe82e88be93a8d837e8b6a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Paramètres de filtrage de contenu web pour les appareils iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Ces paramètres permettent de configurer les URL que les utilisateurs de navigateurs web peuvent ou non visiter sur des appareils iOS. Il existe deux méthodes que vous pouvez utiliser pour configurer les URL :

- **Configurer les URL** : utilisez le filtre web intégré d’Apple pour rechercher des termes réservés aux adultes, par exemple des propos blasphématoires ou sexuellement explicites. Cette fonction évalue chaque page web chargée et tente d’identifier et de bloquer les contenus inappropriés. Vous pouvez également configurer des URL qui ne sont pas vérifiées par le filtre ou encore des URL qui sont bloquées, indépendamment des paramètres de filtre.

- **Sites web spécifiques uniquement** (pour le navigateur web Safari uniquement) : ces URL sont ajoutées aux signets du navigateur Safari. L’utilisateur est **uniquement** autorisé à accéder à ces sites ; aucun autre site n’est accessible. Utilisez cette option uniquement si vous connaissez la liste exacte des URL auxquelles les utilisateurs peuvent accéder.
Si vous ne spécifiez aucune URL, les utilisateurs ne peuvent accéder à aucun site web à l’exception de microsoft.com, microsoft.net et apple.com.



## <a name="get-started"></a>Prise en main

1. Dans le panneau Fonctionnalités de l’appareil, sélectionnez **Filtre de contenu web (mode supervisé uniquement)**.
2. Dans le panneau **Filtre de contenu web** panneau, choisissez le **type de filtre** que vous souhaitez configurer. Vous pouvez choisir plusieurs options :
    - **Non configuré** : aucun filtrage n’est effectué.
    - **Configurer les URL**
    - **Sites web spécifiques uniquement**
3. Ensuite, selon le type de filtre que vous utilisez, suivez l’une des procédures ci-dessous :


## <a name="configure-urls"></a>Configurer les URL

1. Dans le panneau **Filtre de contenu web**, choisissez l’un des paramètres suivants si nécessaire :
   - **URL autorisées** : dans le panneau **URL autorisées**, entrez les URL que vous souhaitez autoriser (sans passer par le filtre web d’Apple), puis appuyez sur Entrée après chaque URL.
     > [!NOTE]
     > Les URL que vous spécifiez ici sont celles que vous ne souhaitez pas soumettre au filtre web d’Apple. Ces URL ne représentent pas une liste des seuls sites web autorisés. Si c’est ce que vous souhaitez, utilisez **Sites web spécifiques uniquement**.

   - **URL bloquées** : dans le panneau **URL bloquées**, entrez les URL que vous souhaitez bloquer (quel que soit le filtre web d’Apple), puis appuyez sur Entrée après chaque URL.
2. Lorsque vous avez terminé, cliquez sur **OK**.


## <a name="specific-websites-only"></a>Sites web spécifiques uniquement

1. Dans le panneau **Filtre de contenu web**, configurez les paramètres suivants pour chaque site web que vous souhaitez autoriser :
    - **URL** : entrez l’URL du site web que vous souhaitez autoriser, par exemple, **http://www.contoso.com**.
    - **Chemin de signet** : entrez le chemin d’accès où vous voulez stocker le signet, par exemple **Contoso/Business Apps**. Si vous n’ajoutez pas de chemin, le signet est ajouté au dossier de signets par défaut sur l’appareil.
    - **Titre** : entrez un titre descriptif pour le signet.
2. Cliquez sur **Ajouter** après avoir entré les informations pour chaque site web.
3. Lorsque vous avez terminé, cliquez sur **OK**.

>[!IMPORTANT] 
> Les URL suivantes sont ajoutées automatiquement par Intune.
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>Terminer

Cliquez sur **OK** pour revenir au panneau **Créer un profil**, puis cliquez sur **Créer**.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant affecter le profil d’appareil aux groupes que vous choisissez. Pour plus d’informations, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).
