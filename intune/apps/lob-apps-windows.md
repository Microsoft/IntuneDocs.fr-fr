---
title: Ajouter une application métier Windows à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter une application métier (LOB) Windows à l’aide de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d9b579e944827e511700073f0b3348b5ef20adc
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724696"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Ajouter une application métier Windows à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Une application métier est une application que vous ajoutez à partir d’un fichier d’installation d’application. En règle générale, ce genre d’application est écrite en interne. Les étapes suivantes fournissent des conseils pour vous aider à ajouter une application métier Windows à Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Étape 1 : Spécifier le fichier d'installation de logiciel

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans la charge de travail **Applications clientes**, choisissez **Gérer** > **Applications**.
5. Au-dessus de la liste des applications, sélectionnez **Ajouter**.
6. Dans le volet **Ajouter une application**, sélectionnez **Application métier**.

## <a name="step-2-configure-the-app-package-file"></a>Étape 2 : Configurer le fichier de package d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Fichier de package d’application**.
2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Sélectionnez ensuite un fichier d’installation Windows ayant l’extension **.msi**, **.appx** ou **.appxbundle**.

    > [!NOTE]
    > Les extensions de fichier des applications Windows incluent **.msi**, **.appx**, **.appxbundle**, **.msix** et **.msixbundle**.  

1. Une fois que vous avez fini, sélectionnez **OK**.


## <a name="step-3-configure-app-information"></a>Étape 3 : Configurer les informations de l’application

1. Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, configurez les informations suivantes. Certaines valeurs de ce volet sont éventuellement renseignées automatiquement.
    - **Nom** : Entrez le nom de l’application, tel qu’il apparaît dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d’application existe deux fois, une seule des applications apparaît dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. La description s’affiche dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **Ignorer la version de l’application** : choisissez **Oui** si le développeur de l’application met celle-ci automatiquement à jour. Cette option s’applique aux applications mobiles .msi uniquement.
    - **Catégorie** : sélectionnez une ou plusieurs catégories d’application intégrées, ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver l’application plus facilement quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : Afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : entrez éventuellement l’URL d’un site web qui contient des informations sur l’application. L’URL s’affiche dans le portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur l’application. L’URL s’affiche dans le portail d’entreprise.
    - **Arguments de ligne de commande** : si vous le souhaitez, entrez les arguments de ligne de commande à appliquer au fichier .msi durant son exécution.  Exemple : **/q**. N’incluez pas la commande msiexec ou des arguments, tel que **/i** ou **/x**, car ils sont automatiquement utilisés. Pour plus d’informations, consultez [Options de ligne de commande](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). Si le fichier .MSI nécessite des options de ligne de commande supplémentaires, vous pouvez utiliser la [gestion des applications Win32](app-management.md).
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application. Exemple : **Service des ressources humaines**.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : chargez une icône associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
3. Une fois que vous avez fini, sélectionnez **OK**.

## <a name="step-4-finish-up"></a>Étape 4 : Terminer

1. Dans le volet **Ajouter une application**, vérifiez que vous avez correctement configuré les informations de l’application.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Étape 5 : Mettre à jour une application métier

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > Pour permettre au service Intune de déployer correctement un nouveau fichier APPX sur l’appareil, vous devez incrémenter la chaîne `Version` dans le fichier AppxManifest.xml du package APPX.
    
## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurer une application MSI mobile avec mise à jour automatique pour ignorer le processus de vérification de version

Vous pouvez configurer une application MSI mobile connue avec mise à jour automatique pour ignorer le processus de vérification de version. 

Certaines applications basées sur un programme d’installation MSI sont automatiquement mises à jour par le développeur de l’application. Pour ces applications MSI mises à jour automatiquement, vous pouvez configurer le paramètre **Ignorer la version de l’application** dans le volet **Informations sur l’application**. Quand vous changez ce paramètre en lui affectant la valeur **Oui**, Microsoft Intune n’applique pas la version de l’application installée sur le client Windows. 

Cette fonctionnalité est utile pour éviter d’introduire une condition de concurrence. Par exemple, une condition de concurrence peut se produire quand l’application est automatiquement mise à jour par le développeur et en même temps par Intune. Tous deux tentent d’appliquer une version de l’application sur un client Windows, ce qui crée un conflit.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée apparaît dans la liste des applications. Vous pouvez à présent l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Consultez [Vue d’ensemble du cycle de vie des applications dans Microsoft Intune](app-lifecycle.md).
