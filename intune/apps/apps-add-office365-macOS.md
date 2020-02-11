---
title: Installer Office 365 sur des appareils macOS à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser Microsoft Intune pour installer des applications Office 365 sur des appareils macOS.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755355"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Affecter Office 365 à des appareils macOS avec Microsoft Intune

Ce type d’application vous permet d’affecter facilement des applications Office 365 2016 à des appareils macOS. En utilisant ce type d’application, vous pouvez installer Word, Excel, PowerPoint, Outlook et OneNote. Ces applications bénéficient également de Microsoft AutoUpdate (MAU) qui garantit que les applications sont sécurisées et à jour. Les applications souhaitées sont affichées sous la forme d’une application unique dans la liste des applications de la console Intune.


## <a name="before-you-start"></a>Avant de commencer

Avant d’ajouter Office 365 à des appareils macOS, vous devez comprendre les détails suivants :

- Les appareils sur lesquels vous déployez ces applications doivent exécuter macOS 10.10 ou ultérieur.
- Intune prend uniquement en charge l’ajout d’applications Office qui sont incluses dans la suite Office 2016 pour Mac.
- Si des applications Office sont ouvertes au moment où Intune installe la suite d’applications, les utilisateurs risquent de perdre les données contenues dans des fichiers non enregistrés.

## <a name="select-the-office-365-suite-app-type"></a>Sélectionner le type d'application Office 365 Suite

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Sélectionnez **macOS** dans la section **Suite Office 365** du volet **Sélectionner le type d’application**.
4. Cliquez sur **Sélectionner**. Les étapes **Ajouter la suite Office 365** sont affichées.

## <a name="step-1---app-suite-information"></a>Étape 1 - Informations sur la suite d'applications

Dans cette étape, indiquez des informations sur la suite d’applications. Ces informations vous permettent d’identifier la suite d’applications dans Intune. Elles aident aussi les utilisateurs à trouver la suite d’applications dans le portail d’entreprise.

1. Dans la page **Informations sur la suite d'applications**, vous pouvez confirmer ou modifier les valeurs par défaut :
    - **Nom de la suite** : entrez le nom de la suite d’applications tel qu’il apparaît dans le portail d’entreprise. Vérifiez que chaque nom de suite que vous utilisez est unique. Si un même nom de suite d’applications est utilisé deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description de la suite** : Entrez une description pour la suite d’applications. Vous pouvez par exemple répertorier les applications que vous avez choisies d’inclure.
    - **Éditeur** : Microsoft apparaît comme éditeur.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Ce paramètre permet de faciliter la recherche de la suite d’applications pour les utilisateurs qui naviguent dans le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de la déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : Microsoft apparaît comme développeur.
    - **Propriétaire** : Microsoft apparaît comme propriétaire.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : le logo Office 365 est affiché avec l’application quand les utilisateurs naviguent dans le portail d’entreprise.
2. Cliquez sur **Suivant** pour afficher la page **Balises d’étendue**.

## <a name="step-2---select-scope-tags-optional"></a>Étape 2 - Sélectionner les balises d’étendue (facultatif)
Vous pouvez utiliser des balises d’étendue pour déterminer qui peut afficher des informations sur l’application cliente dans Intune. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md).

1. Cliquez sur **Sélectionner des balises d’étendue** pour ajouter éventuellement des balises d’étendue pour la suite d’applications. 
2. Cliquez sur **Suivant** pour afficher la page **Affectations**.

## <a name="step-3---assignments"></a>Étape 3 – Affectations

1. Sélectionnez les affectations de groupe **Requis**, **Disponible pour les appareils inscrits** pour la suite d’applications. Pour plus d'informations, voir [Ajouter des groupes pour organiser des utilisateurs et des appareils](~/fundamentals/groups-add.md) et [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Vous ne pouvez pas désinstaller la suite d’applications Office 365 pour macOS via Intune.

2. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**. 

## <a name="step-4---review--create"></a>Étape 4 – Vérifier + créer

1. Vérifiez les valeurs et les paramètres que vous avez saisis pour la suite d'applications.
2. Lorsque vous avez terminé, cliquez sur **Créer** pour ajouter l'application à Intune.

    Le volet **Vue d’ensemble** de la suite d’applications Office 365 Window 10 que vous avez créée s'affiche. La suite apparaît dans la liste des applications en tant qu’entrée unique.

## <a name="next-steps"></a>Étapes suivantes

- Pour en savoir plus sur l’ajout d’applications Office 365 à des appareils Windows 10, consultez [Affecter des applications Office 365 ProPlus 2016 à des appareils Windows 10 avec Microsoft Intune](apps-add-office365.md).
- Pour en savoir plus sur l’inclusion et l’exclusion d’affectations d’application pour des groupes d’utilisateurs, consultez [Inclure et exclure des affectations d’applications](apps-inc-exl-assignments.md).
