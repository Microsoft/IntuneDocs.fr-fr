---
title: Ajouter une application métier iOS à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter une application métier (LOB) iOS à Microsoft Intune.
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
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 507c7ecff9715ebf9f24567c735592f3f255ccc9
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609177"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Ajouter une application métier iOS à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aidez-vous des informations contenues dans cet article pour ajouter une application métier iOS à Microsoft Intune. Une application métier est une application que vous ajoutez à Intune à partir d’un fichier d’installation d’application IPA. En règle générale, ce genre d’application est écrite en interne. Vous devrez d'abord vous inscrire au programme iOS Developer Enterprise Program. Pour plus d'informations sur la procédure à suivre, visitez le [site web d’Apple](https://developer.apple.com/programs/ios/enterprise/).

> [!NOTE]
> Les utilisateurs d’appareils iOS peuvent supprimer certaines applications iOS intégrées, par exemple Bourse et Plans. Vous ne pouvez pas utiliser Intune pour redéployer ces applications. Si les utilisateurs suppriment ces applications, ils doivent se rendre sur l’App Store et les réinstaller manuellement.
>
> Les applications métier iOS ont une limite de taille maximale de 4 Go par application.

> [!NOTE]
> Les identificateurs de bundle (par exemple *com.contoso.app*) sont censés être des identificateurs uniques d’une application. Par exemple, pour installer une version bêta d’une application métier à coté de la version de production à des fins de test, la version bêta doit avoir un identificateur unique différent (par exemple *com.contoso.app-beta*). Dans le cas contraire, la version bêta remplace la version de production et est traitée comme une mise à niveau. Le fait de renommer le fichier .ipa n’a pas d’effet sur ce comportement.

## <a name="select-the-app-type"></a>Sélectionner le type d’application

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Sélectionner le type d’application**, sous les types d’application **Autre**, sélectionnez **Application métier**.
4. Cliquez sur **Sélectionner**. Les étapes **Ajouter une application** sont affichées.

## <a name="step-1---app-information"></a>Étape 1 - Informations de l’application

### <a name="select-the-app-package-file"></a>Sélectionner le fichier de package d’application

1. Dans le volet **Ajouter une application**, cliquez sur **Sélectionner un fichier de package d’application**. 
2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Sélectionnez ensuite un fichier d’installation iOS ayant l’extension **.ipa**.
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

L’application que vous avez créée apparaît à présent dans la liste des applications. Dans la liste, vous pouvez affecter les applications aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

> [!NOTE]
> Les profils d’approvisionnement des applications métier iOS comportent un préavis de 30 jours avant expiration.

## <a name="step-5-update-a-line-of-business-app"></a>Étape 5 : Mettre à jour une application métier

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

La mise à jour de l'application métier sera automatiquement installée.

> [!NOTE]
> Pour permettre au service Intune de déployer correctement un nouveau fichier IPA sur l’appareil, vous devez incrémenter la chaîne `CFBundleVersion` dans le fichier Info.plist du package IPA.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée apparaît dans la liste des applications. Vous pouvez à présent l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Consultez [Vue d’ensemble des cycles de vie des appareils et des applications](../fundamentals/device-lifecycle.md).
