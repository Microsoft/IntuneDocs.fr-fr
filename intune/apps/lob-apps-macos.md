---
title: Guide pratique pour ajouter des applications métier macOS à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications métier macOS à Microsoft Intune.
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755168"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Guide pratique pour ajouter des applications métier macOS à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilisez les informations contenues dans cet article pour ajouter des applications métier macOS à Microsoft Intune. Vous devez télécharger un outil externe pour pré-traiter vos fichiers *.pkg* avant de pouvoir charger votre fichier métier dans Microsoft Intune. Le traitement préalable de vos fichiers *.pkg* doit avoir lieu sur un appareil macOS.

> [!NOTE]
> Depuis la publication de macOS Catalina 10.15, avant d’ajouter vos applications à Intune, vérifiez que vos applications métier macOS sont certifiées. Si les développeurs de vos applications métier n’ont pas certifié leurs applications, elles ne pourront pas s’exécuter sur les appareils macOS de vos utilisateurs. Pour plus d’informations sur la façon de vérifier si une application est certifiée, visitez [Certifier vos applications macOS pour vous préparer à macOS Catalina](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579).

> [!NOTE]
> Bien que les utilisateurs d’appareils macOS puissent supprimer certaines applications macOS intégrées, telles que Stocks et Maps, vous ne pouvez pas vous servir d’Intune pour redéployer ces applications. Si des utilisateurs finaux suppriment ces applications, ils doivent se rendre sur l’App Store et les réinstaller manuellement.

## <a name="before-your-start"></a>Avant de commencer

Vous devez télécharger un outil externe, le marquer comme exécutable, puis pré-traiter vos fichiers *.pkg* à l’aide de cet outil avant de pouvoir charger votre fichier métier dans Microsoft Intune. Le traitement préalable de vos fichiers *.pkg* doit avoir lieu sur un appareil macOS. Utilisez l’outil Intune App Wrapping Tool pour Mac pour permettre aux applications Mac d’être gérées par Microsoft Intune.

> [!IMPORTANT]
> Le fichier *.pkg* doit être signé en utilisant le certificat « Developer ID Installer » obtenu auprès d'un compte développeur Apple. Seuls les fichiers *.pkg* peuvent être utilisés pour charger des applications métier macOS à Microsoft Intune. La conversion d’autres formats, tels que *.dmg* vers *.pkg*, n’est pas prise en charge.
>

1. Téléchargez l’outil [Intune App Wrapping Tool pour Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > L’outil **Intune App Wrapping Tool pour Mac** doit être exécuté sur un ordinateur Mac OS. 

2. Marquez l'outil téléchargé comme exécutable :
   - Démarrez l’app Terminal.
   - Remplacez le répertoire par l'emplacement où figure `IntuneAppUtil`.
   - Exécutez la commande suivante pour rendre l'outil exécutable :<br> 
       `chmod +x IntuneAppUtil`

3. Utilisez la commande `IntuneAppUtil` au sein de l’outil **Intune App Wrapping Tool pour Mac** pour inclure le fichier d’application métier *.pkg* dans un wrapper à partir d’un fichier *.intunemac*.<br>

    Exemples de commandes à utiliser pour l’outil Microsoft Intune App Wrapping Tool pour macOS :
    > [!IMPORTANT]
    > Assurez-vous que l'argument `<source_file>` ne contient pas d'espaces avant d'exécuter les commandes `IntuneAppUtil`.

    - `IntuneAppUtil -h`<br>
    Cette commande affiche les informations d’utilisation de l’outil.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Cette commande inclut le fichier d’application métier *.pkg* dans un wrapper vers un fichier *.intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Cette commande extrait les paramètres détectés et la version pour le fichier *.intunemac* créé.

## <a name="select-the-app-type"></a>Sélectionner le type d’application

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Sélectionner le type d’application**, sous les types d’application **Autre**, sélectionnez **Application métier**.
4. Cliquez sur **Sélectionner**. Les étapes **Ajouter une application** sont affichées.

## <a name="step-1---app-information"></a>Étape 1 - Informations sur l’application

### <a name="select-the-app-package-file"></a>Sélectionner le fichier de package d’application

1. Dans le volet **Ajouter une application**, cliquez sur **Sélectionner un fichier de package d'application**. 
2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Ensuite, sélectionnez un fichier d’installation macOS avec l’extension *.intunemac*.
   Les détails de l'application s’affichent.
3. Lorsque vous avez terminé, sélectionnez **OK** dans le volet **Fichier de package d'application** pour ajouter l'application.

### <a name="set-app-information"></a>Définir les informations de l’application

1. Dans la page **Informations sur l’application**, ajoutez les détails de votre application. Selon l’application que vous avez choisie, certaines valeurs de ce volet peuvent être remplies automatiquement.
    - **Nom** : Entrez le nom de l’application, tel qu’il apparaît dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d’application existe deux fois, une seule des applications apparaît dans le portail d’entreprise.
    - **Description** : entrez la description de l’application. La description s’affiche dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **Système d’exploitation minimal** : dans la liste, choisissez la version de système d’exploitation minimale sur laquelle l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Catégorie** : sélectionnez une ou plusieurs catégories d’application intégrées, ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver l’application plus facilement quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : Afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. L’URL s’affiche dans le portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. L’URL s’affiche dans le portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application. Exemple : **Service des ressources humaines**.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : chargez une icône associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
2. Cliquez sur **Suivant** pour afficher la page **Balises d’étendue**.

## <a name="step-2---select-scope-tags-optional"></a>Étape 2 - Sélectionner les balises d’étendue (facultatif)
Vous pouvez utiliser des balises d’étendue pour déterminer qui peut afficher des informations sur l’application cliente dans Intune. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md).

1. Cliquez sur **Sélectionner des balises d’étendue** pour ajouter éventuellement des balises d’étendue pour l'application. 
2. Cliquez sur **Suivant** pour afficher la page **Affectations**.

## <a name="step-3---assignments"></a>Étape 3 – Affectations

1. Sélectionnez les affectations de groupe **Requis**, **Disponible pour les appareils inscrits** ou **Désinstaller** pour l’application. Pour plus d'informations, voir [Ajouter des groupes pour organiser des utilisateurs et des appareils](~/fundamentals/groups-add.md) et [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md).
2. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**. 

## <a name="step-4---review--create"></a>Étape 4 – Vérifier + créer

1. Vérifiez les valeurs et les paramètres que vous avez saisis pour l'application.
2. Lorsque vous avez terminé, cliquez sur **Créer** pour ajouter l'application à Intune.

    Le panneau **Vue d’ensemble** de l'application métier s’affiche.

L’application que vous avez créée apparaît dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

> [!NOTE]
> Si le fichier *.pkg* contient plusieurs applications ou programmes d’installation d’applications, Microsoft Intune ne signale que l’*application* est installé correctement que lorsque toutes les applications installées sont détectées sur l’appareil.

## <a name="update-a-line-of-business-app"></a>Mettre à jour une application métier

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Pour permettre au service Intune de déployer correctement un nouveau fichier *.pkg* sur l’appareil, vous devez incrémenter le package `version` et la chaîne `CFBundleVersion` dans le fichier *packageinfo* de votre package *.pkg*.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée s’affiche dans la liste des applications. Vous pouvez maintenant l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Pour plus d’informations, consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Pour plus d’informations, consultez [Vue d’ensemble des cycles de vie des appareils et des applications](../fundamentals/device-lifecycle.md).
