---
title: Guide pratique pour ajouter des applications métier macOS à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications métier macOS à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1ec8e45cfc0478e25127ba4ab2ca54c25622cff
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724709"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Guide pratique pour ajouter des applications métier macOS à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilisez les informations contenues dans cet article pour ajouter des applications métier macOS à Microsoft Intune. Vous devez télécharger un outil externe pour pré-traiter vos fichiers *.pkg* avant de pouvoir charger votre fichier métier dans Microsoft Intune. Le traitement préalable de vos fichiers *.pkg* doit avoir lieu sur un appareil macOS.

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
    
    - `IntuneAppUtil -h`<br>
    Cette commande affiche les informations d’utilisation de l’outil.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Cette commande inclut le fichier d’application métier *.pkg* dans un wrapper vers un fichier *.intunemac*.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Cette commande extrait les paramètres détectés et la version pour le fichier *.intunemac* créé.

## <a name="step-1---specify-the-software-setup-file"></a>Étape 1 : spécifier le fichier d’installation de logiciel

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, choisissez **Applications clientes**.
4. Dans la charge de travail **Applications clientes**, choisissez **Gérer** > **Applications**.
5. Au-dessus de la liste des applications, choisissez **Ajouter**.
6. Dans le volet **Ajouter une application**, choisissez **Application métier**.

## <a name="step-2---configure-the-app-package-file"></a>Étape 2 : configurer le fichier de package d’application

1. Dans le volet **Ajouter une application**, choisissez **Fichier de package d’application**.
2. Dans le volet **Fichier de package d’application**, cliquez sur le bouton Parcourir et sélectionnez un fichier d’installation macOS avec l’extension *.intunemac*.
3. Quand vous avez terminé, cliquez sur **OK**.


## <a name="step-3---configure-app-information"></a>Étape 3 : configurer les informations de l’application

1. Dans le volet **Ajouter une application**, choisissez **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, ajoutez les détails de votre application. Selon l’application choisie, certaines valeurs de ce volet peuvent avoir été renseignées automatiquement :
    - **Nom** : Entrez le nom de l’application à afficher dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d'application existe deux fois, seule l'une des applications sera proposée aux utilisateurs du portail d'entreprise.
    - **Description** : Entrez une description de l’application à afficher aux utilisateurs dans le portail d’entreprise.
    - **Éditeur :** entrez le nom de l’éditeur de l’application.
    - **Système d’exploitation minimal** : dans la liste, choisissez le système d’exploitation minimal sur lequel l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Catégorie** : sélectionnez une ou plusieurs des catégories d’applications intégrées ou une catégorie que vous avez créée. Ceci facilite la recherche de l’application pour les utilisateurs qui naviguent dans le portail d’entreprise.
    - **Afficher comme application en une sur le portail d’entreprise** : met en valeur l’application sur la page principale du portail d’entreprise lorsque les utilisateurs cherchent des applications.
    - **URL d’informations** : si vous le souhaitez, saisissez l’URL d’un site Web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de confidentialité** : si vous le souhaitez, saisissez l’URL d’un site Web qui contient des informations de confidentialité pour cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : si vous le souhaitez, saisissez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, saisissez un nom pour le propriétaire de cette application, par exemple, **Département des ressources humaines**.
    - **Notes** : saisissez les éventuelles notes que vous souhaitez associer à cette application.
    - **Logo** : chargez l’icône qui est associée à l’application. Il s’agit de l’icône qui est affichée avec l’application quand les utilisateurs naviguent dans le portail d’entreprise.
3. Quand vous avez terminé, cliquez sur **OK**.

## <a name="step-4---finish-up"></a>Étape 4 : Terminer

1. Dans le volet **Ajouter une application**, vérifiez que les détails de votre application sont corrects.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

L’application que vous avez créée apparaît dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

> [!NOTE]
> Si le fichier *.pkg* contient plusieurs applications ou programmes d’installation d’applications, Microsoft Intune ne signale que l’*application* est installé correctement que lorsque toutes les applications installées sont détectées sur l’appareil.

## <a name="step-5---update-a-line-of-business-app"></a>Étape 5 : Mise à jour d’une application métier

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Pour permettre au service Intune de déployer correctement un nouveau fichier *.pkg* sur l’appareil, vous devez incrémenter le package `version` et la chaîne `CFBundleVersion` dans le fichier *packageinfo* de votre package *.pkg*.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée s’affiche dans la liste des applications. Vous pouvez maintenant l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Pour plus d’informations, consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Pour plus d’informations, consultez [Vue d’ensemble des cycles de vie des appareils et des applications](../fundamentals/device-lifecycle.md).
