---
title: Guide de configuration de l'application Portail d’entreprise
titleSuffix: Microsoft Intune
description: Découvrez comment appliquer un logo spécifique d'entreprise à l’application Portail d’entreprise Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aed2bec6e6fea40fdbd78bc487896d167d036f06
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le portail d’entreprise Microsoft Intune permet aux utilisateurs d’accéder aux données de l’entreprise et d’effectuer des tâches courantes, notamment l’inscription d’appareils ou l’installation d’applications, et d’accéder à des informations d’assistance fournies par le département informatique.        

> [!Tip]        
> Quand vous personnalisez le Portail d’entreprise, les configurations s’appliquent au site web du Portail d’entreprise et aux applications du Portail d’entreprise.       

La personnalisation du Portail d’entreprise permet de fournir une expérience familière et utile à vos utilisateurs finaux. Pour cela, à partir de la charge de travail **Applications mobiles**, choisissez **Configuration** > **Personnalisation de Portail d’entreprise**, puis configurez les paramètres nécessaires.      

## <a name="company-contact-information-and-privacy-statement"></a>Informations de contact et déclaration de confidentialité de l'entreprise        
Le nom de l’entreprise s’affiche comme titre du Portail d’entreprise. Les informations de contact et les détails sont présentés aux utilisateurs dans l’écran **Contacter le service informatique** du Portail d’entreprise. La déclaration de confidentialité s’affiche lorsqu’un utilisateur clique sur le lien correspondant.        


|                   Nom du champ                   | Longueur maximale |                                                                                                 Plus d’informations                                                                                                 |
|------------------------------------------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <strong>Nom de la société</strong>          |     40     |                                                                            Ce nom s’affiche comme titre du Portail d’entreprise.                                                                            |
|  <strong>Nom du contact du service informatique</strong>   |     40     |                                                                         Ce nom s’affiche dans la page <strong>Contacter le service informatique</strong>.                                                                          |
|  <strong>Numéro de téléphone du service informatique</strong>   |     20     |                                                                    Ce numéro s’affiche dans la page <strong>Contacter le service informatique</strong>.                                                                     |
|  <strong>Adresse e-mail du service informatique</strong>  |     40     |                       Cette adresse s’affiche dans la page <strong>Contacter le service informatique</strong>. Vous devez entrer une adresse e-mail valide au format <strong>alias@domainname.com</strong>.                       |
|    <strong>Informations supplémentaires</strong>     |    120     |                                                                                S’affiche dans la page <strong>Contacter le service informatique</strong>.                                                                                |
| <strong>URL de la déclaration de confidentialité de l'entreprise</strong> |     79     | Vous pouvez spécifier la déclaration de confidentialité de votre entreprise qui s’affiche lorsque les utilisateurs cliquent sur les liens de confidentialité à partir du Portail d’entreprise. Vous devez entrer une URL valide au format <strong><https://www.contoso.com></strong>. |

## <a name="support-contacts"></a>Contacts du support     
Les utilisateurs peuvent voir le lien du site web de support dans le Portail d’entreprise et l’utiliser pour accéder au support en ligne.        



|Nom du champ|Longueur maximale|Plus d’informations|        
|-|-|-|     
|**URL du site web du support technique**|150|Si vous avez un site web de support technique auquel vous aimeriez que les utilisateurs accèdent, spécifiez cette URL ici. Elle doit être au format **https://www.contoso.com**. Si vous ne spécifiez aucune URL, rien ne s’affiche pour le site web de support technique dans la page **Contacter le service informatique** du Portail d’entreprise.|        
|**Nom du site web du support technique**|40|Il s'agit du nom convivial qui s'affiche pour l'URL permettant d'accéder au site Web de support technique. Si vous spécifiez l’URL d’un site web de support technique sans aucun nom convivial, Accéder au site web du service informatique apparaît dans la page **Contacter le service informatique** du Portail d’entreprise.       

## <a name="company-branding-customization"></a>Personnalisation de l’image de la société       
Vous pouvez personnaliser votre Portail d’entreprise avec le logo et le nom de votre société, un thème chromatique et un arrière-plan.     



|Nom du champ|Plus d’informations|       
|-|-|       
|**Couleur de thème**|Sélectionnez une couleur de thème à appliquer au Portail d’entreprise. Vous pouvez choisir une couleur dans le sélecteur de couleurs, ou entrer un code hexadécimal spécifique.|      
|**Afficher le logo de la société**|Lorsque vous activez cette option, vous pouvez télécharger le logo de votre entreprise pour qu’il apparaisse sur le Portail de celle-ci. Vous pouvez télécharger deux logos : un qui s’affiche quand l’arrière-plan du Portail d’entreprise est blanc, et un autre qui s’affiche quand l’arrière-plan du Portail d’entreprise utilise la couleur de thème que vous avez sélectionnée. Chaque logo doit être un fichier de type .png ou .jpg, et avoir une résolution maximale de 400 x 100 pixels et une taille inférieure ou égale à 750 Ko.<br>Vous pouvez également afficher le nom de société que vous avez entré à côté du logo chargé.|      

Après avoir enregistré vos modifications, vous pouvez choisir **Affichez un aperçu de vos paramètres dans le portail web Intune** pour voir l'aspect de vos configurations.
