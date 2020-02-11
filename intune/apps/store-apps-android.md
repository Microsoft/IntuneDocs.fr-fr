---
title: Ajouter des applications de l’Android Store à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications de l’Android store venant de Google Play store à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6b9f6a9303e53652959639193633cdcc00dfb99
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755083"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Ajouter des applications de l’Android Store à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Avant d’affecter une application à un appareil ou un groupe d’utilisateurs, vous devez d’abord l’ajouter à Microsoft Intune. 

## <a name="add-an-app"></a>Ajouter une application

Vous pouvez ajouter une application de l’Android Store à Intune à partir du portail Azure. Pour cela, effectuez les étapes suivantes :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Sélectionner le type d’application**, sous les types **Application du Store** disponibles, sélectionnez **Application de l’Android Store**.
4. Cliquez sur **Sélectionner**.<br>
   Les étapes **Ajouter une application** sont affichées.
5. Pour configurer les **informations sur l’application** pour l'application Android, accédez au [Google Play Store](https://play.google.com/store) et recherchez l'application que vous souhaitez déployer. Affichez la page de l'application et notez les détails de l'application. 
6. Dans la page **Informations sur l'application**, ajoutez les détails de l'application :
    - **Nom** : Entrez le nom de l’application tel qu’il apparaîtra dans le portail d’entreprise. Veillez à choisir un nom d’application unique. Si vous utilisez un nom d’application qui existe déjà, un seul sera présenté aux utilisateurs dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. Cette description est fournie aux utilisateurs dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **URL de l’App Store** : Saisissez l’URL du magasin d’applications de l’application que vous souhaitez créer. Utilisez l'URL de la page de l'application lorsque les détails de l'application apparaissent dans le magasin. 
    - **Système d’exploitation minimal** : dans la liste, choisissez la version de système d’exploitation la plus ancienne sur laquelle l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver facilement l’application quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications. S'applique aux applications déployées avec l'intention Disponible.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de la déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application (par exemple, *Ressources humaines*).
    - **Remarques** : entrez les éventuelles remarques à associer à cette application.
    - **Logo** : si vous le souhaitez, chargez une icône à associer à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
7. Cliquez sur **Suivant** pour afficher la page **Balises d’étendue**.
8. Cliquez sur **Sélectionner des balises d’étendue** pour ajouter éventuellement des balises d’étendue pour l'application. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée](~/fundamentals/scope-tags.md).
9. Cliquez sur **Suivant** pour afficher la page **Affectations**.
10. Sélectionnez les affectations de groupe pour l'application. Pour plus d’informations, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils](~/fundamentals/groups-add.md). 
11. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**. Vérifiez les valeurs et les paramètres que vous avez saisis pour l'application.
12. Lorsque vous avez terminé, cliquez sur **Créer** pour ajouter l'application à Intune.

Le volet **Vue d’ensemble** de l'application que vous avez créée s'affiche.

## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)
