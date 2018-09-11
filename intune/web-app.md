---
title: Ajouter des applications web à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications web à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec483218cb86426b237c40c8831a2f0880847ade
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347455"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Ajouter des applications web à Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune prend en charge divers types d’applications, notamment les applications web. Une application web est une application client-serveur. Le serveur fournit l’application web, qui englobe l’interface utilisateur, le contenu et les fonctionnalités. De plus, les plateformes d’hébergement web modernes offrent généralement, entre autres avantages, la sécurité et l’équilibrage de charge. Une application web est gérée séparément sur le web. Vous utilisez Microsoft Intune pour pointer vers ce type d’application. Vous affectez également les groupes d’utilisateurs qui peuvent accéder à cette application. 

Avant de pouvoir gérer et attribuer une application pour vos utilisateurs, ajoutez cette application à Intune. Intune crée un raccourci vers l’application web sur l’écran d’accueil de l’appareil de l’utilisateur.

> [!Note]
> Les applications web ne sont pas prises en charge sur les appareils macOS et avec profil professionnel Android.

## <a name="add-a-web-app-to-intune"></a>Ajouter une application web à Intune
Pour ajouter une application à Intune comme raccourci vers une application sur le web, effectuez les étapes suivantes :

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**.  
    Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet de la charge de travail **Applications clientes**, sous **Gérer**, sélectionnez **Applications**.
5. Dans le volet **Applications**, sélectionnez **Ajouter**.
6. Dans le volet **Ajouter une application**, dans la liste déroulante **Type d’application**, sélectionnez le type **Lien web**.
7. Sélectionnez **Configurer**.
8. Dans le volet **Informations sur l’application**, ajoutez les informations suivantes :
    - **Nom** : entrez le nom de l’application tel qu’il apparaîtra dans le portail d’entreprise. 
    
        > [!NOTE]
        > Si vous modifiez le nom de l’application sur le portail Intune Azure après l’avoir déployée et installée, vous ne pourrez plus la cibler à l’aide de commandes.
    
    - **Description :** entrez la description de l’application. Cette description est fournie aux utilisateurs dans le portail d’entreprise.
    - **Éditeur** : entrez le nom de l’éditeur de cette application.
    - **URL de l’application** : entrez l’URL du site web qui héberge l’application que vous souhaitez affecter.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver facilement l’application quand ils parcourent le portail d’entreprise.
    - **Proposer cette application dans le portail d’entreprise** : sélectionnez cette option pour afficher la suite d’applications dans la page principale du portail d’entreprise quand les utilisateurs cherchent des applications.
    - **Exiger l’ouverture de ce lien dans Managed Browser** : sélectionnez cette option pour affecter aux utilisateurs un lien vers un site web ou une application web qu’ils peuvent ouvrir dans Intune Managed Browser. Ce navigateur doit être installé sur leur appareil.
    - **Logo** : chargez une icône qui sera associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
9. Sélectionnez **OK**.
10. Dans le volet **Ajouter une application**, sélectionnez **Ajouter**.

> [!Note]
> Les utilisateurs doivent ajouter le widget Intune à leur écran d’accueil pour afficher les applications web qui ont été affectées à des appareils Android.

## <a name="next-steps"></a>Étapes suivantes

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. Pour obtenir de l’aide, consultez [Affecter des applications à des groupes](apps-deploy.md). 
