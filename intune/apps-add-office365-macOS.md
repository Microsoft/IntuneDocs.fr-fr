---
title: Installer Office 365 sur des appareils macOS à l’aide de Microsoft Intune
titlesuffix: ''
description: Découvrez comment utiliser Microsoft Intune pour installer des applications Office 365 sur des appareils macOS.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4aa5cb24bc153839c6aac193f074128dd46a2e5f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185404"
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
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Surveillance + Gestion** > **Intune**.
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet de la charge de travail **Applications clientes**, sous **Gérer**, sélectionnez **Applications**. 
5. Sélectionnez **Ajouter**.
6. Dans la liste **Type d’application**, sélectionnez **macOS** dans le groupe **Suite Office 365**.
7. Sélectionnez **Informations sur la suite d’applications** pour obtenir des informations sur la suite d’applications.  
    Ces informations vous permettent d’identifier la suite d’applications dans Intune. Elles aident aussi les utilisateurs à trouver la suite d’applications dans le portail d’entreprise.
8. Entrez les informations suivantes :
    - **Nom de la suite** : entrez le nom de la suite d’applications tel qu’il apparaît dans le portail d’entreprise. Vérifiez que chaque nom de suite que vous utilisez est unique. Si un même nom de suite d’applications est utilisé deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description de la suite** : entrez la description de la suite d’applications.
    - **Éditeur** : Microsoft apparaît comme éditeur.
    - **Catégorie** : sélectionnez une ou plusieurs des catégories d’applications intégrées ou une catégorie que vous avez créée. Ce paramètre permet de faciliter la recherche de la suite d’applications pour les utilisateurs qui naviguent dans le portail d’entreprise.
    - **Proposer cette application dans le portail d’entreprise** : sélectionnez cette option pour afficher la suite d’applications dans la page principale du portail d’entreprise quand les utilisateurs cherchent des applications.
    - **URL d’information** : si vous le souhaitez, entrez l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de déclaration de confidentialité** : si vous le souhaitez, entrez l’URL d’un site web qui contient des informations de confidentialité relatives à cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : Microsoft apparaît comme développeur.
    - **Propriétaire** : Microsoft apparaît comme propriétaire.
    - **Notes** : entrez les éventuelles notes à associer à cette application.
    - **Logo** : le logo Office 365 est affiché avec l’application quand les utilisateurs naviguent dans le portail d’entreprise.
9. Sélectionnez **OK**.
10. Dans le volet **Ajouter une application**, sélectionnez **Ajouter**.  
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
