---
title: Installer Office 365 sur des appareils macOS à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser Microsoft Intune pour installer des applications Office 365 sur des appareils macOS.
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
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01ca17c9f8e3fd86e12f225621e6dc0e07bb4acb
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564074"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Affecter Office 365 à des appareils macOS avec Microsoft Intune

Ce type d’application vous permet d’affecter facilement des applications Office 365 2016 à des appareils macOS. En utilisant ce type d’application, vous pouvez installer Word, Excel, PowerPoint, Outlook et OneNote. Ces applications bénéficient également de Microsoft AutoUpdate (MAU) qui garantit que les applications sont sécurisées et à jour. Les applications souhaitées sont affichées sous la forme d’une application unique dans la liste des applications de la console Intune.


## <a name="before-you-start"></a>Avant de commencer

Avant d’ajouter Office 365 à des appareils macOS, vous devez comprendre les détails suivants :

- Les appareils sur lesquels vous déployez ces applications doivent exécuter macOS 10.10 ou ultérieur.
- Intune prend uniquement en charge l’ajout d’applications Office qui sont incluses dans la suite Office 2016 pour Mac.
- Si des applications Office sont ouvertes au moment où Intune installe la suite d’applications, les utilisateurs risquent de perdre les données contenues dans des fichiers non enregistrés.

## <a name="create-and-configure-the-app-suite"></a>Créer et configurer la suite d’applications

Ajoutez Office 365 à partir du volet **Applications**.
1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans la liste **Type d’application**, sélectionnez **macOS** dans le groupe **Suite Office 365**.
4. Sélectionnez **Informations sur la suite d’applications** pour obtenir des informations sur la suite d’applications.  
    Ces informations vous permettent d’identifier la suite d’applications dans Intune. Elles aident aussi les utilisateurs à trouver la suite d’applications dans le portail d’entreprise.
5. Entrez les informations suivantes :
    - **Nom de la suite** : entrez le nom de la suite d’applications tel qu’il apparaît dans le portail d’entreprise. Vérifiez que chaque nom de suite que vous utilisez est unique. Si un même nom de suite d’applications est utilisé deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description de la suite** : Entrez une description pour la suite d’applications.
    - **Éditeur** : Microsoft apparaît comme éditeur.
    - **Catégorie** : Sélectionnez une ou plusieurs des catégories d’applications intégrées ou une catégorie que vous avez créée. Ce paramètre permet de faciliter la recherche de la suite d’applications pour les utilisateurs qui naviguent dans le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : Microsoft apparaît comme développeur.
    - **Propriétaire** : Microsoft apparaît comme propriétaire.
    - **Remarques** : entrez les éventuelles remarques à associer à cette application.
    - **Logo** : le logo Office 365 est affiché avec l’application quand les utilisateurs naviguent dans le portail d’entreprise.
6. Sélectionnez **OK**.
7. Dans le volet **Ajouter une application**, sélectionnez **Ajouter**.  
    La suite apparaît dans la liste des applications en tant qu’entrée unique.

## <a name="configure-app-assignments"></a>Configurer les affectations d’applications

Dans cette étape, configurez les affectations de la suite d’applications. 

1. Sélectionnez la suite d’applications **Office 365** dans la liste des applications pour afficher le volet de vue d’ensemble **Office 365**.
2. Dans le volet **Office 365**, sélectionnez **Affectations**.
3. Pour ajouter un groupe qui utilisera la suite d’applications, sélectionnez **Ajouter un groupe**.  
    Le volet **Ajouter un groupe** s’affiche.
4. Affectez la valeur **Obligatoire** ou **Disponible** à **Type d’affectation**.
5. Affectez la suite aux groupes que vous sélectionnez. Pour plus d’informations, consultez [Affecter des applications à des groupes avec Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Vous ne pouvez pas désinstaller la suite d’applications Office 365 via Intune.

5. Dans le volet **Affecter**, sélectionnez **OK**.
6. Dans le volet **Ajouter un groupe**, sélectionnez **OK**.
7. Sélectionnez **Enregistrer** pour valider vos affectations.

## <a name="next-steps"></a>Étapes suivantes

- Pour en savoir plus sur l’ajout d’applications Office 365 à des appareils Windows 10, consultez [Affecter des applications Office 365 ProPlus 2016 à des appareils Windows 10 avec Microsoft Intune](apps-add-office365.md).
- Pour en savoir plus sur l’inclusion et l’exclusion d’affectations d’application pour des groupes d’utilisateurs, consultez [Inclure et exclure des affectations d’applications](apps-inc-exl-assignments.md).
