---
title: "Guide pratique pour ajouter des applications métier Windows Phone à Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : en savoir plus sur l’ajout des applications métier Windows Phone à Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 95d0c1b5598785ff30bfd912f65c39cc5e46b85c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---

# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Guide pratique pour ajouter des applications métier Windows Phone à Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Étape 1 : spécifier le fichier d’installation de logiciel

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Gérer les applications**.
4. Dans la charge de travail **Applications mobiles**, choisissez **Gérer** > **Applications**.
5. Au-dessus de la liste des applications, choisissez **Ajouter**.
6. Dans le panneau **Ajouter une application**, choisissez **Application métier**.

## <a name="step-2---configure-the-app-package-file"></a>Étape 2 : configurer le fichier de package d’application

1. Dans le panneau **Ajouter une application**, choisissez **Package d’application**.
2. Dans le panneau de fichiers **Package d’application**, cliquez sur le bouton Parcourir et sélectionnez un fichier d’installation Windows Phone avec l’extension **.xap**.
3. Quand vous avez terminé, cliquez sur **OK**.


## <a name="step-3---configure-app-information"></a>Étape 3 : configurer les informations de l’application

1. Dans le panneau **Ajouter une application**, choisissez **Package d’application**.
2. Dans le panneau **Informations sur l’application**, configurez les informations suivantes. Selon l’application choisie, certaines valeurs de ce panneau peuvent avoir été renseignées automatiquement :
    - **Nom** : entrez le nom de l’application tel qu’il sera affiché dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d'application existe deux fois, seule l'une des applications sera proposée aux utilisateurs du portail d'entreprise.
    - **Description :** entrez la description de l’application. Ce libellé s'affichera dans le portail d'entreprise.
    - **Éditeur :** entrez le nom de l’éditeur de l’application.
    - **Catégorie** : sélectionnez une ou plusieurs des catégories d’applications intégrées ou une catégorie que vous avez créée. Cela permettra aux utilisateurs de trouver aisément l'application lorsqu'ils parcourront le portail d'entreprise.
    - **Afficher comme application en une sur le portail d’entreprise** : met en valeur l’application sur la page principale du portail d’entreprise lorsque les utilisateurs cherchent des applications.
    - **URL d’informations** : si vous le souhaitez, saisissez l’URL d’un site Web qui contient des informations sur cette application. Cette URL s'affichera dans le portail d'entreprise.
    - **URL de confidentialité** : si vous le souhaitez, saisissez l’URL d’un site Web qui contient des informations de confidentialité pour cette application. Cette URL s'affichera dans le portail d'entreprise.
    - **Développeur** : si vous le souhaitez, saisissez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, saisissez un nom pour le propriétaire de cette application, par exemple, **Département des ressources humaines**.
    - **Notes** : saisissez les éventuelles notes que vous souhaitez associer à cette application.
    - **Logo** : chargez une icône qui sera associée à l’application. Il s'agit de l'icône qui s'affichera avec l'application lorsque les utilisateurs parcourront le portail d'entreprise.
3. Quand vous avez terminé, cliquez sur **OK**.

## <a name="step-4---finish-up"></a>Étape 4 : terminer

1. Dans le panneau **Ajouter une application**, vérifiez l’exactitude des informations que vous avez configurées.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

L’application que vous avez créée s’affichera dans la liste des applications, où vous pouvez l’affecter aux groupes que vous choisissez. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](deploy-apps.md).

