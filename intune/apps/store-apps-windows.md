---
title: Ajouter des applications du Microsoft Store à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications du Microsoft Store (Windows Store) à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: 3c13d7960c0bb5c73908a0a574ab7d6c169d6460
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563433"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Ajouter des applications du Microsoft Store à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Pour pouvoir affecter, surveiller, configurer ou protéger des applications, vous devez les ajouter à Intune. 

## <a name="add-an-app-to-intune"></a>Ajouter une application à Intune
Pour ajouter une application du Microsoft Store à Intune, effectuez les étapes suivantes :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Ajouter une application**, sélectionnez **Windows** comme **Type d’application**, puis sélectionnez **Informations sur l’application**.
4. Renseignez le volet **Informations sur l’application**. Selon l’application choisie, certaines valeurs de ce volet peuvent avoir été renseignées automatiquement :
    - **Nom** : Entrez le nom de l’application tel qu’il apparaîtra dans le portail d’entreprise. Veillez à choisir un nom d’application unique. Si vous utilisez un nom d’application qui existe déjà, un seul sera présenté aux utilisateurs dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. Cette description est fournie aux utilisateurs dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **URL de l’App Store** : tapez l’URL de l’App Store de l’application à créer. Vous pouvez trouver l’URL en recherchant l’application souhaitée dans le [Microsoft Store](https://store.microsoft.com). Utilisez l’URL à partir de la barre d’adresses du navigateur.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver facilement l’application quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application (par exemple, *Ressources humaines*).
    - **Remarques** : entrez les éventuelles remarques à associer à cette application.
    - **Logo** : si vous le souhaitez, chargez une icône à associer à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
5. Sélectionnez **OK**.
6. Sélectionnez **Ajouter**.

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. Les applications Microsoft Store peuvent uniquement être affectées à des groupes ayant le type d’affectation **Disponible pour les appareils inscrits** (les utilisateurs installent l’application à partir du site web ou de l’application Portail d’entreprise).

## <a name="next-steps"></a>Étapes suivantes
- [Affecter des applications à des groupes](apps-deploy.md)
