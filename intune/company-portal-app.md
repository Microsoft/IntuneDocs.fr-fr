---
title: "Guide de configuration de l'application Portail d’entreprise"
titleSuffix: Azure portal
description: "Découvrez comment appliquer un logo spécifique d'entreprise à l’application Portail d’entreprise Intune. \""
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e40b4000df61176d4f252aa7ded776f91eeecd82
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le portail d’entreprise Microsoft Intune permet aux utilisateurs d’accéder aux données de l’entreprise et d’effectuer des tâches courantes, notamment l’inscription d’appareils ou l’installation d’applications, et d’accéder à des informations d’assistance fournies par le département informatique.        

> [!Tip]        
> Quand vous personnalisez le Portail d’entreprise, les configurations s’appliquent au site web du Portail d’entreprise et aux applications du Portail d’entreprise.       

La personnalisation du Portail d’entreprise permet de fournir une expérience familière et utile à vos utilisateurs finaux. Pour cela, à partir de la charge de travail **Applications mobiles**, choisissez **Configuration** > **Personnalisation de Portail d’entreprise**, puis configurez les paramètres nécessaires.      

## <a name="company-contact-information-and-privacy-statement"></a>Informations de contact et déclaration de confidentialité de l'entreprise        
Le nom de l’entreprise s’affiche comme titre du Portail d’entreprise. Les informations de contact et les détails sont présentés aux utilisateurs dans l’écran **Contacter le service informatique** du Portail d’entreprise. La déclaration de confidentialité s’affiche lorsqu’un utilisateur clique sur le lien correspondant.        


|Nom du champ|Longueur maximale|Plus d’informations|        
|-|-|-|     
|**Nom de la société**|40|Ce nom s’affiche comme titre du Portail d’entreprise.|        
|**Nom du contact du service informatique**|40|Ce nom s’affiche dans la page **Contacter le service informatique**.|      
|**Numéro de téléphone du service informatique**|20|Ce numéro s’affiche dans la page **Contacter le service informatique**.|        
|Adresse de messagerie du service informatique|40|Cette adresse s’affiche dans la page **Contacter le service informatique**. Vous devez entrer une adresse e-mail valide au format **alias@domainname.com**.|     
|**Informations supplémentaires**|120|S’affiche dans la page **Contacter le service informatique**.|      
|**URL de la déclaration de confidentialité de l'entreprise**|79|Vous pouvez spécifier la déclaration de confidentialité de votre entreprise qui s’affiche lorsque les utilisateurs cliquent sur les liens de confidentialité à partir du Portail d’entreprise. Vous devez entrer une URL valide au format **https://www.contoso.com**.|        

## <a name="support-contacts"></a>Contacts du support     
Les utilisateurs peuvent voir le lien du site web de support dans le Portail d’entreprise et l’utiliser pour accéder au support en ligne.        



|Nom du champ|Longueur maximale|Plus d’informations|        
|-|-|-|     
|**URL du site web du support technique**|150|Si vous avez un site web de support technique auquel vous aimeriez que les utilisateurs accèdent, spécifiez cette URL ici. Elle doit être au format **htps://www.contoso.com** . Si vous ne spécifiez aucune URL, rien ne s’affiche pour le site web de support technique dans la page **Contacter le service informatique** du Portail d’entreprise.|        
|**Nom du site web du support technique**|40|Il s'agit du nom convivial qui s'affiche pour l'URL permettant d'accéder au site Web de support technique. Si vous spécifiez l’URL d’un site web de support technique sans aucun nom convivial, Accéder au site web du service informatique apparaît dans la page **Contacter le service informatique** du Portail d’entreprise.       

## <a name="company-branding-customization"></a>Personnalisation de l’image de la société       
Vous pouvez personnaliser votre Portail d’entreprise avec le logo et le nom de votre société, un thème chromatique et un arrière-plan.     



|Nom du champ|Plus d’informations|       
|-|-|       
|**Couleur de thème**|Sélectionnez une couleur de thème à appliquer au Portail d’entreprise.|      
|**Afficher le logo de la société**|Lorsque vous activez cette option, vous pouvez télécharger le logo de votre entreprise pour qu’il apparaisse sur le Portail de celle-ci. Vous pouvez télécharger deux logos : un qui s’affiche quand l’arrière-plan du Portail d’entreprise est blanc, et un autre qui s’affiche quand l’arrière-plan du Portail d’entreprise utilise la couleur de thème que vous avez sélectionnée. Chaque logo doit être un fichier de type .png ou .jpg, et avoir une résolution maximale de 400 x 100 pixels et une taille inférieure ou égale à 750 Ko.<br>Vous pouvez également afficher le nom de société que vous avez entré à côté du logo chargé.|      

Après avoir enregistré vos modifications, vous pouvez choisir **Affichez un aperçu de vos paramètres dans le portail web Intune** pour voir l'aspect de vos configurations.
