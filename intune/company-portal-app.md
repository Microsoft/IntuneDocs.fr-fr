---
title: Guide de configuration de l'application Portail d’entreprise
titleSuffix: Microsoft Intune
description: Découvrez comment appliquer un logo spécifique d'entreprise à l’application Portail d’entreprise Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01de402a48362f04680c569c40a812b6a4b83cc6
ms.sourcegitcommit: 38afcff149f9c86e92e5f1eccaa927859c395926
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307404"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le portail d’entreprise Microsoft Intune permet aux utilisateurs d’accéder aux données de l’entreprise et d’effectuer des tâches courantes, notamment l’inscription d’appareils ou l’installation d’applications, et d’accéder à des informations d’assistance fournies par le département informatique.        

> [!Tip]        
> Quand vous personnalisez le Portail d’entreprise, les configurations s’appliquent au site web du Portail d’entreprise et aux applications du Portail d’entreprise.       

La personnalisation du Portail d’entreprise permet de fournir une expérience familière et utile à vos utilisateurs finaux. Pour cela, à partir de la charge de travail **Applications clientes**, choisissez **Configuration** > **Personnalisation de Portail d’entreprise**, puis configurez les paramètres nécessaires.  

> [!Note]       
> Si vous utilisez Azure Government, l’utilisateur final dispose de journaux des applications pour décider du mode de partage des informations, quand il lance le processus d’obtention d’aide sur un problème. Toutefois, si vous n’utilisez pas Azure Government, le Portail d’entreprise pour Windows 10 envoie les journaux des applications directement à Microsoft, quand l’utilisateur lance le processus d’obtention d’aide sur un problème. L’envoi des journaux des applications à Microsoft facilite l’analyse et la résolution des problèmes. 

## <a name="company-information-and-privacy-statement"></a>Informations et déclaration de confidentialité de l’entreprise        
Le nom de l’entreprise s’affiche comme titre du Portail d’entreprise. La déclaration de confidentialité s’affiche lorsqu’un utilisateur clique sur le lien correspondant.

Les champs marqués d’un astérisque (*) sont obligatoires.       


| Nom du champ | Longueur maximale | Plus d’informations |
|---|---|---|
|**Nom de la société**| 40 | Ce nom s’affiche comme titre du Portail d’entreprise et sous forme de texte dans l’ensemble de l’expérience utilisateur Intune. |
| **URL de la déclaration de confidentialité** |     79     | Vous pouvez spécifier la déclaration de confidentialité de votre entreprise qui s’affiche lorsque les utilisateurs cliquent sur les liens de confidentialité à partir du Portail d’entreprise. Vous devez entrer une URL valide au format `<https://www.contoso.com>`. |

## <a name="support-information"></a>Informations concernant le support      
Entrez les informations de support de votre entreprise afin de fournir à vos employés un contact pour les questions relatives à Intune.       

|Nom du champ|Longueur maximale|Plus d’informations|
|---|---|---|
|**Nom du contact** | 40 | Ce nom s’affiche dans la page **Contacter le service informatique**. |
|**Numéro de téléphone** | 20 | Ce numéro de contact se trouve dans la page **Contacter l’administrateur** afin de permettre aux employés de vous contacter pour obtenir de l’aide. |
|**Adresse de messagerie**| 40 | Cette adresse s’affiche dans la page **Contacter le service informatique**. Vous devez entrer une adresse e-mail valide au format `alias@domainname.com`. |
|**Nom du site web**| 40 | Il s'agit du nom convivial qui s'affiche pour l'URL permettant d'accéder au site Web de support technique. Si vous spécifiez l’URL d’un site web de support technique sans aucun nom convivial, Accéder au site web du service informatique apparaît dans la page **Contacter le service informatique** du Portail d’entreprise. |
|**URL du site web**| 150 | Si vous avez un site web de support technique auquel vous aimeriez que les utilisateurs accèdent, spécifiez cette URL ici. Elle doit être au format `https://www.contoso.com`. Si vous ne spécifiez aucune URL, rien ne s’affiche pour le site web de support technique dans la page **Contacter le service informatique** du Portail d’entreprise. |
| **Informations supplémentaires**| 120 | S’affiche dans la page **Contacter le service informatique**. |


## <a name="company-branding-customization"></a>Personnalisation de l’image de la société       
Vous pouvez personnaliser votre Portail d’entreprise avec le logo et le nom de votre société, un thème chromatique et un arrière-plan. Pour afficher un aperçu rapide de la configuration de marque sans un appareil de test, vous pouvez accéder au site [portal.manage.microsoft.com](https://portal.manage.microsoft.com). Notez que le logo que vous chargez sera utilisé pour les modèles d’e-mail.      

### <a name="theme-color"></a>Couleur de thème
Appliquez une couleur de thème au portail d’entreprise. Sélectionnez une couleur standard ou entrez le code hexadécimal à six chiffres d’une couleur personnalisée.

|Nom du champ|Plus d’informations|
|---|---|
|**Type de couleur**| Sélectionnez une couleur de thème à appliquer au Portail d’entreprise. Vous pouvez choisir une couleur standard ou entrer un code hexadécimal spécifique. |
|**Choisir une couleur** ou un **code de couleur hexadécimal**| Sélectionnez une couleur de thème à appliquer au Portail d’entreprise. Vous pouvez choisir une couleur standard ou entrer un code hexadécimal spécifique. Ces options sont fournies en fonction du **type de couleur** sélectionné.  |

### <a name="company-logo"></a>Logo de la société
Chargez le logo de votre société pour le rendre visible dans l’ensemble de l’expérience utilisateur Intune.

|Nom du champ|Plus d’informations|
|---|---|
|**Afficher le logo de la société**|Lorsque vous activez cette option, vous pouvez télécharger le logo de votre entreprise pour qu’il apparaisse sur le Portail de celle-ci. Vous pouvez télécharger deux logos : un qui s’affiche quand l’arrière-plan du Portail d’entreprise est blanc, et un autre qui s’affiche quand l’arrière-plan du Portail d’entreprise utilise la couleur de thème que vous avez sélectionnée. |
|**Charger un logo à utiliser sur les arrière-plans en couleur des thèmes**| Cette option est disponible si vous avez choisi d’afficher le logo de la société. Chaque logo doit être un fichier de type .png ou .jpg, et avoir une résolution maximale de 400 x 400 pixels ainsi qu’une taille inférieure ou égale à 750 Ko. |
|**Charger le logo à utiliser sur les arrière-plans clairs**| Cette option est disponible si vous avez choisi d’afficher le logo de la société. Chaque logo doit être un fichier de type .png ou .jpg, et avoir une résolution maximale de 400 x 400 pixels ainsi qu’une taille inférieure ou égale à 750 Ko. |
|**Afficher le nom de la société à côté du logo**| Sélectionnez cette option pour afficher le nom de société que vous avez entré à côté du logo chargé. |

Après avoir enregistré vos modifications, vous pouvez choisir **Afficher un aperçu de vos paramètres dans le portail web Intune** en haut du panneau pour voir à quoi ressemblent vos configurations.

## <a name="windows-company-portal-keyboard-shortcuts"></a>Raccourcis clavier du Portail d’entreprise Windows

Les utilisateurs finaux peuvent déclencher des actions de navigation, d’application et d’appareil dans le Portail d’entreprise Windows à l’aide de raccourcis clavier (accélérateurs).

Les raccourcis clavier suivants sont disponibles dans l’application Portail d’entreprise Windows.

| Domaine | Description | Raccourci clavier |
|:------------------:|:--------------:|:-----------------:|
| Menu de navigation | Navigation | Alt+M |
|  | Accueil | Alt+H |
|  | Toutes les applications | Alt+A |
|  | Applications installées | Alt+I |
|  | Envoyer des commentaires | Alt+F |
|  | Mon profil | Alt+U |
|  | Paramètres | Alt+T |
| Accueil - Vignette de l’appareil | Renommer | F2 |
|  | Supprimer | Ctrl+D ou Supprimer |
|  | Vérifier l’accès | Ctrl+M ou F9 |
| Détails sur l'appareil | Renommer | F2 |
|  | Supprimer | Ctrl+D ou Supprimer |
|  | Vérifier l’accès | Ctrl+M ou F9 |
| Détails de l’application | Installer | Ctrl+I |

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter manuellement l’application Portail d’entreprise Windows 10 à l’aide de Microsoft Intune](store-apps-company-portal-app.md)