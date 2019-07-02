---
title: Gérer les applications à partir du site Web du portail d’entreprise Intune
description: Gérer et afficher les applications disponibles et installées
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/27/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c7b91e63a559c45cbbcbd7056a7f5e259e07481
ms.sourcegitcommit: 690e680e854b7d707421c5e06f134e493f4f4194
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416850"
---
# <a name="manage-apps-from-the-company-portal-website"></a>Gérer des applications à partir du site web du portail d’entreprise 
Visitez le [site Web portail d’entreprise](https://portal.manage.microsoft.com) pour afficher et gérer des applications à partir de votre organisation. 

## <a name="view-all-apps"></a>Afficher toutes les applications  
Dans le menu, sélectionnez **applications** pour voir toutes les applications mises à disposition par votre organisation. 

   ![Capture d’écran du portail d’entreprise page du site Web, applications, écran des options d’affiner.](./media/intune-view-apps-1907.png)  

Cette page répertorie les informations suivantes sur chaque application :  

* Nom : Nom de l’application, avec un lien vers la page de détails de l’application.
* Serveur de publication : Le nom du développeur ou de la société qui distribué l’application. Un serveur de publication est généralement un fournisseur de logiciels ou votre organisation.  
* Publié de date : Date à laquelle l’application a été proposée pour téléchargement. Publier date peut afficher la version initiale d’une application ou mettre à jour de la plus récente d’une application.
* État : L’état actuel de l’application sur votre appareil, ce qui inclut disponibles, installé et l’installation. 
* Catégorie : L’application (fonction) ou objectif, tel que proposé, ingénierie, l’enseignement et la productivité.  

### <a name="search-and-refine"></a>Recherche et affiner   

Utilisez la barre de recherche pour trouver des applications. Les résultats de la recherche sont automatiquement triés selon la pertinence.  

   ![Capture d’écran du portail d’entreprise page du site Web, applications, écran des options d’affiner.](./media/intune-refine-all-apps-1907.png)  

Sélectionnez **affiner** pour voir les filtrer et trier des options. Filtrer la liste pour afficher les applications avec des critères spécifiques, y compris **Type**, **disponibilité**, et **éditeurs**. Sélectionnez **tri** pour réorganiser les applications par :

* Nom de l’application, par ordre croissant ou décroissant par ordre alphabétique 
* Nom de l’éditeur, par ordre croissant ou décroissant par ordre alphabétique 
* Date, la plus ancienne ou plus récente de publication  

## <a name="view-installed-apps"></a>Affichage installé des applications  
Dans le menu, sélectionnez **applications installées** pour afficher une liste de toutes les applications installées sur votre appareil.  

   ![Capture d’écran du portail d’entreprise page du site Web, applications installées.](./media/intune-installed-apps-1907.png)  


Cette page répertorie les informations suivantes sur chaque application :  

* Nom : Nom de l’application, avec un lien vers la page de détails de l’application.
* Type d’affectation : comment l’application est affectée et à votre disposition. Voir disponible et les applications requises pour plus d’informations. Votre organisation peut rendre une application que vous pouvez installer vous-même, ou ils peuvent nécessiter et installer une application sur votre appareil automatiquement.  
* Serveur de publication : Le nom du développeur ou de la société qui distribué l’application. Un serveur de publication est généralement un fournisseur de logiciels ou votre organisation.  
* Publié de date : Date à laquelle l’application a été proposée pour téléchargement. Publier date peut afficher la version initiale d’une application ou mettre à jour de la plus récente d’une application.
* État : Installation état actuel de l’application sur votre appareil. Applications peuvent indiquer que l’installation, installé et l’installer a échoué. Les applications requises peut prendre jusqu'à 10 minutes pour afficher un état à jour.  

### <a name="search-and-refine"></a>Recherche et affiner  

Utilisez la barre de recherche pour trouver des applications. Les résultats de la recherche sont automatiquement triés selon la pertinence.  

   ![Site Web de capture d’écran du portail d’entreprise, les applications installées, affiner les options.](./media/intune-installed-refine-1907.png)  

Sélectionnez **affiner** pour voir les filtrer et trier des options. Filtrer la liste pour afficher les applications avec des critères spécifiques, y compris **Types**, **éditeurs**, et **états**. Sélectionnez **tri** pour réorganiser les applications par :

* Nom de l’application, par ordre croissant ou décroissant par ordre alphabétique  
* Nom de l’éditeur, par ordre croissant ou décroissant par ordre alphabétique  
* Date, la plus ancienne ou plus récente de publication  

Vous avez besoin d’aide supplémentaire ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  

### <a name="available-and-required-apps"></a>Applications disponibles et requises
Applications sont attribuées par votre organisation et étiquetées comme disponible ou obligatoire. Le **applications installées** page affiche les applications que vous avez sous la **Type d’affectation** colonne. 


* Applications disponibles : ces applications sont sélectionnées par votre organisation et sont appropriées et utiles pour les professionnels ou scolaires. Ils sont facultatifs à installer, et sont les seules applications que vous trouverez dans le portail d’entreprise à installer. 

* Applications requises : votre organisation peut déployer nécessaire les applications professionnelles et scolaires directement sur votre appareil. Ces applications sont automatiquement installées pour vous sans intervention. 

Des applications sont également mises à votre disposition en fonction de votre type d’appareil. Par exemple, si vous utilisez le site web Portail d’entreprise sur un appareil Windows, vous aurez accès aux applications Windows, mais pas aux applications iOS.  

## <a name="view-app-details"></a>Vue Détails de l’application  
Sélectionnez une application sur le **applications** ou **applications installées** page pour afficher ses détails. Vous êtes dirigé vers **détails de l’application**, où vous trouverez une description et les exigences de l’application. Si une application n’est pas déjà installée sur votre appareil, vous pouvez l’installer à partir de cette page. 


   ![Capture d’écran de site Web, page de détails de l’application.](./media/intune-app-details-1907.png)  

## <a name="next-steps"></a>Étapes suivantes
Besoin d'aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
