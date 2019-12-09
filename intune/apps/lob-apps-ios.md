---
title: Ajouter une application métier iOS à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter une application métier (LOB) iOS à Microsoft Intune.
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
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e1d3c6a427dcbd4a7946c5f3e180de56e8cb955
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563524"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Ajouter une application métier iOS à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aidez-vous des informations contenues dans cet article pour ajouter une application métier iOS à Microsoft Intune. Une application métier est une application que vous ajoutez à Intune à partir d’un fichier d’installation d’application IPA. En règle générale, ce genre d’application est écrite en interne. Vous devrez d'abord vous inscrire au programme iOS Developer Enterprise Program. Pour plus d'informations sur la procédure à suivre, visitez le [site web d’Apple](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Les utilisateurs d’appareils iOS peuvent supprimer certaines applications iOS intégrées, par exemple Bourse et Plans. Vous ne pouvez pas utiliser Intune pour redéployer ces applications. Si les utilisateurs suppriment ces applications, ils doivent se rendre sur l’App Store et les réinstaller manuellement.
>
>Les applications métier iOS ont une limite de taille maximale de 4 Go par application.

## <a name="step-1-specify-the-software-setup-file"></a>Étape 1 : Spécifier le fichier d'installation de logiciel

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Ajouter une application**, sélectionnez **Application métier** comme **Type d’application**.

## <a name="step-2-configure-the-app-package-file"></a>Étape 2 : Configurer le fichier de package d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Fichier de package d’application**.
2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Sélectionnez ensuite un fichier d’installation iOS ayant l’extension **.ipa**.
3. Une fois que vous avez fini, sélectionnez **OK**.


## <a name="step-3-configure-app-information"></a>Étape 3 : Configurer les informations de l’application

1. Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, ajoutez les détails de votre application. Selon l’application que vous avez choisie, certaines valeurs de ce volet peuvent être remplies automatiquement.
    - **Nom** : Entrez le nom de l’application, tel qu’il apparaît dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d’application existe deux fois, une seule des applications apparaît dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. La description s’affiche dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **Système d’exploitation minimal** : dans la liste, choisissez la version de système d’exploitation minimale sur laquelle l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Catégorie** : sélectionnez une ou plusieurs catégories d’application intégrées, ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver l’application plus facilement quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : Afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. L’URL s’affiche dans le portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. L’URL s’affiche dans le portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application. Exemple : **Service des ressources humaines**.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : chargez une icône associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
3. Une fois que vous avez fini, sélectionnez **OK**.

## <a name="step-4-finish-up"></a>Étape 4 : Terminer

1. Dans le volet **Ajouter une application**, vérifiez que les détails relatifs à votre application sont corrects.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

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
