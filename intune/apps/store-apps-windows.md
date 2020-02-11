---
title: Ajouter des applications du Microsoft Store à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications du Microsoft Store (Windows Store) à Microsoft Intune.
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
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8743af2a05f6daebca5e1394ba5b7b8f13fcf7e3
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754896"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Ajouter des applications du Microsoft Store à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pour pouvoir affecter, surveiller, configurer ou protéger des applications, vous devez les ajouter à Intune. 

## <a name="add-an-app-to-intune"></a>Ajouter une application à Intune
Pour ajouter une application du Microsoft Store à Intune, effectuez les étapes suivantes :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Sélectionner le type d’application**, sous les types **Application du Store** disponibles, sélectionnez **Application du Windows Store**.
4. Cliquez sur **Sélectionner**. Les étapes **Ajouter une application** sont affichées.
5. Pour configurer les **informations sur l’application** pour les applications du Windows Store, accédez au [Microsoft Store](https://www.microsoft.com/store/apps) et recherchez l'application que vous souhaitez déployer. Affichez la page de l'application et notez les détails de l'application. 
6. Dans la page **Informations sur l'application**, ajoutez les détails de l'application :
    - **Nom** : Entrez le nom de l’application tel qu’il apparaîtra dans le portail d’entreprise. Veillez à choisir un nom d’application unique. Si vous utilisez un nom d’application qui existe déjà, un seul sera présenté aux utilisateurs dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. Cette description est fournie aux utilisateurs dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **URL de l’App Store** : tapez l’URL de l’App Store de l’application à créer. Vous pouvez trouver l’URL en recherchant l’application souhaitée dans le [Microsoft Store](https://www.microsoft.com/store/apps). Utilisez l’URL à partir de la barre d’adresses du navigateur.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver facilement l’application quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
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

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix.

> [!IMPORTANT]
> Les applications Microsoft Store peuvent uniquement être affectées à des groupes ayant le type d’affectation **Disponible pour les appareils inscrits** (les utilisateurs installent l’application à partir du site web ou de l’application Portail d’entreprise).

## <a name="next-steps"></a>Étapes suivantes
- [Affecter des applications à des groupes](apps-deploy.md)
