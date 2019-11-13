---
title: Gérer les livres électroniques iOS achetés en volume
titleSuffix: Microsoft Intune
description: Découvrez comment synchroniser les livres que vous avez achetés en volume à partir de l’App Store iOS dans Intune, puis gérer et suivre leur utilisation.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae29d2ee5add475db89f6895b22299793a94ac36
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984097"
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Guide pratique pour gérer les livres électroniques iOS que vous avez achetés par le biais d’un programme d’achat en volume avec Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Le Programme d’achat en volume (VPP) Apple vous permet d’acheter plusieurs licences pour un livre que vous souhaitez distribuer aux utilisateurs dans votre entreprise. Vous pouvez distribuer des livres à partir du Business Store ou de l’Education Store.

Microsoft Intune vous permet de synchroniser, de gérer et d’affecter des livres que vous avez achetés par le biais de ce programme. Vous pouvez importer les informations de licence depuis la boutique et suivre le nombre de licences utilisées.

Les procédures permettant de gérer les livres sont similaires à celles de la [gestion des applications VPP](../vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Gérer les livres achetés en volume pour les appareils iOS
Vous achetez plusieurs licences pour des livres iOS par le biais du [Programme d’achat en volume (VPP) Apple pour les entreprises](https://www.apple.com/business/vpp/) ou du [Programme d’achat en volume (VPP) Apple pour l’éducation](https://volume.itunes.apple.com/us/store). Cela implique la configuration d’un compte Apple VPP à partir du site web Apple et l’importation du jeton Apple VPP dans Intune.  Vous pouvez ensuite synchroniser vos informations d’achat en volume avec Intune et suivre votre utilisation des livres achetés en volume.

## <a name="before-you-start"></a>Avant de commencer
Avant de commencer, vous devez obtenir un jeton VPP auprès d’Apple et l’importer dans votre compte Intune. En outre :

* Si vous avez déjà utilisé un jeton VPP avec un autre produit, vous devez en générer un nouveau à utiliser avec Intune.
* Chaque jeton est valide pendant un an.
* Par défaut, Intune se synchronise avec le service Apple VPP deux fois par jour. Vous pouvez lancer une synchronisation manuelle à tout moment.
* Après avoir importé le jeton VPP dans Intune, n’importez pas le même jeton dans une autre solution de gestion d’appareils, car cela peut entraîner la perte des enregistrements utilisateur et de l’attribution de licence.
* Avant de commencer à utiliser des livres iOS avec Intune, supprimez les comptes d’utilisateur VPP existants créés avec d’autres fournisseurs GPM (gestion des périphériques mobiles). Par mesure de sécurité, ces comptes d’utilisateur ne sont pas synchronisés dans Intune. Intune synchronise uniquement les données du service Apple VPP qui ont été créées par Intune.
* Lorsque vous affectez un livre à un appareil, celui-ci doit disposer de l’application iBook intégrée. Dans le cas contraire, l’utilisateur doit réinstaller l’application pour pouvoir lire le livre. Vous ne pouvez pas actuellement utiliser Intune pour restaurer les applications intégrées qui ont été supprimées.
* Vous pouvez uniquement affecter des livres obtenus par le biais du Programme d’achat en volume (VPP) Apple. Vous ne pouvez pas télécharger, puis affecter, des livres que vous avez créés en interne.
* Actuellement, vous ne pouvez pas affecter des livres à des catégories d’utilisateur final de la même façon que pour les applications.
* Vous ne pouvez pas récupérer une licence une fois que le livre est affecté.
* Quand un utilisateur disposant d’un appareil compatible essaie pour la première fois d’installer un livre VPP, il est invité à participer au Programme d’achat en volume (VPP) Apple avant de pouvoir installer le livre. Vous pouvez également attribuer des licences à des groupes de sécurité avec des ID Apple managés. Dans ce cas, les utilisateurs ne sont pas invités à saisir leur ID Apple lors de l’installation d’un livre.
* Les appareils doivent être inscrits avec une affinité utilisateur car les livres électroniques peuvent uniquement être affectés à des groupes d'utilisateurs.   


## <a name="to-get-and-upload-an-apple-vpp-token"></a>Pour obtenir et charger un jeton Apple VPP

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, choisissez **Applications clientes**.
1. Dans la charge de travail **Applications clientes**, choisissez **Installation** > **Jetons VPP iOS**.
2. Dans la liste du volet des jetons VPP, cliquez sur **Créer**.
3. Dans le volet **Nouveau jeton VPP**, spécifiez les informations suivantes :
    - **Fichier de jeton VPP** : vérifiez que vous êtes inscrit au Programme d’achat en volume (VPP) Apple pour les entreprises ou au Programme d’achat en volume (VPP) Apple pour l’éducation. Ensuite, téléchargez le jeton Apple VPP pour votre compte et sélectionnez-le ici.
    - **ID Apple** : saisissez l’ID Apple du compte associé au programme d’achats en volume.
    - **Type de compte VPP** : choisissez **Entreprise** ou **Éducation**.
4. Quand vous avez terminé, cliquez sur **Créer**.

Le jeton est affiché dans le volet de la liste de jetons.


Vous pouvez synchroniser les données détenues par Apple avec Intune à tout moment en sélectionnant **Synchroniser maintenant**.

## <a name="to-assign-a-volume-purchased-app"></a>Pour affecter une application achetée en volume

3. Dans le volet **Intune**, choisissez **Livres électroniques**.
1. Dans la charge de travail **Livres électroniques**, choisissez **Gérer** > **Tous les livres électroniques**.
2. Dans le volet contenant la liste des livres, choisissez le livre à attribuer, puis choisissez «  **...**  » > **Attribuer des groupes**.
3. Dans le volet <*nom du livre*> - **Groupes affectés**, choisissez **Gérer** > **Groupes affectés**.
4. Choisissez **Affecter des groupes** puis, dans le volet **Sélectionner des groupes**, sélectionnez les groupes d’utilisateurs Azure AD auxquels vous souhaitez affecter le livre. Pour le moment, les groupes d’appareils ne sont pas pris en charge.
Choisissez une action d’attribution **Disponible** ou **Obligatoire**. 
5. Une fois que vous avez terminé, choisissez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

Consultez la page [Guide pratique pour surveiller des applications](apps-monitor.md) pour apprendre à contrôler les affectations de livres.






