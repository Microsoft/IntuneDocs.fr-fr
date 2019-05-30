---
title: Ajouter des applications intégrées sur des appareils mobiles à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser Intune pour faciliter l’installation d’applications intégrées sur des appareils mobiles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a424655241f44125b51ef2f75cb6c537b10dd91d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049517"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Ajouter des applications intégrées à Microsoft Intune

Le type d’application *Intégré* vous permet d’attribuer facilement des applications gérées organisées, comme les applications Office 365, à des appareils iOS et Android. Vous pouvez affecter des applications spécifiques à ce type d’application, comme Excel, OneDrive, Outlook, Skype et d’autres. Une fois que vous avez ajouté une application, elle s’affiche avec le type *Application iOS intégrée* ou *Application Android intégrée*. En utilisant le type application intégrée, vous pouvez choisir les applications à publier pour les utilisateurs d’appareils.

Dans les versions antérieures de la console Intune, Intune fournissait plusieurs applications Office 365 gérées par défaut, par exemple Outlook et OneDrive. Les types de ces applications gérées étaient *Application de l’App Store iOS gérée* ou *Application Android gérée*. Au lieu d’utiliser ces types d’application, nous vous recommandons d’utiliser le type application intégrée. En utilisant le type application intégrée, vous disposez d’une flexibilité supplémentaire pour modifier et supprimer des applications Office 365.

>[!NOTE]
>Les applications Office 365 par défaut marquées en tant qu’*Application de l’App Store iOS gérée* et *Application Android gérée* sont supprimées de la liste d’applications quand toutes les affectations sont supprimées.

## <a name="add-a-built-in-app"></a>Ajouter une application intégrée

Pour ajouter une application intégrée à vos applications disponibles dans Microsoft Intune, suivez les instructions ci-dessous :
1. Connectez-vous au portail Azure.
2. Pour afficher le volet Microsoft Intune, sélectionnez **Plus de services** > **Surveillance + Gestion** > **Intune**.
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet **Applications clientes**, sous **Gérer**, sélectionnez **Applications**.
5. Sélectionnez **Ajouter**.
6. Dans le volet **Ajouter une application**, dans la liste **Type d’application**, sélectionnez **Application intégrée**.
7. Sélectionnez **Sélectionner une application**.
8. Dans le volet **Application intégrée**, sélectionnez les applications à inclure.
9. Dans le volet **Ajouter une application**, sélectionnez **Ajouter**.


## <a name="configure-app-information"></a>Configurer les informations de l’application

Vous pouvez modifier les informations de l’application intégrée. Ces informations vous aident à identifier l’application dans Intune. Elles permettent également aux utilisateurs de trouver l’application dans le portail d’entreprise.
1. Dans le volet **Applications clientes - Applications**, sélectionnez l’application intégrée à modifier.  
    Un volet s’affiche pour l’application intégrée.
2. Sous **Gérer**, sélectionnez l’option **Propriétés**.
3. Pour modifier les informations de l’application intégrée, sélectionnez l’option **Configurer**.
4. Dans le volet **Informations sur l’application**, vous pouvez modifier les informations suivantes :
    - **Nom** : entrez le nom de l’application intégrée, tel qu’il est affiché dans le portail d’entreprise. Tous les noms que vous utilisez doivent être uniques. Si le même nom d’application existe deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description** : Entrez une description de l'application. 
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs catégories d’application intégrée. La définition de cette option facilite la recherche de l’application pour les utilisateurs qui naviguent dans le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : Afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application (par exemple, *Ressources humaines*).
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Charger l’icône** : chargez une icône qui s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
4. Sélectionnez **OK**.
5. Dans le volet **Propriétés**, sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

- Vous pouvez désormais affecter les applications aux groupes de votre choix. Pour plus d’informations, consultez [Affecter des applications à des groupes](apps-deploy.md).
