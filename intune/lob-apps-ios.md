---
title: Ajouter une application métier iOS à Microsoft Intune
titlesuffix: ''
description: Découvrez comment ajouter une application métier iOS à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9ee132a1b1c79e9829e5d28dc33b5cac2e52c8ac
ms.sourcegitcommit: 27f365f5e67e83562883e0c1fc9fdfae8fd60ce4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2018
ms.locfileid: "40251899"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Ajouter une application métier iOS à Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Aidez-vous des informations contenues dans cet article pour ajouter une application métier iOS à Microsoft Intune.

>[!NOTE]
>Les utilisateurs d’appareils iOS peuvent supprimer certaines applications iOS intégrées, par exemple Bourse et Plans. Vous ne pouvez pas utiliser Intune pour redéployer ces applications. Si les utilisateurs suppriment ces applications, ils doivent se rendre sur l’App Store et les réinstaller manuellement.

## <a name="step-1-specify-the-software-setup-file"></a>Étape 1 : Spécifier le fichier d’installation du logiciel

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Applications mobiles**.
4. Dans la charge de travail **Applications mobiles**, sélectionnez **Gérer** > **Applications**.
5. Au-dessus de la liste des applications, sélectionnez **Ajouter**.
6. Dans le volet **Ajouter une application**, sélectionnez **Application métier**.

## <a name="step-2-configure-the-app-package-file"></a>Étape 2 : Configurer le fichier de package d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Fichier de package d’application**.
2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Sélectionnez ensuite un fichier d’installation iOS ayant l’extension **.ipa**.
3. Une fois que vous avez fini, sélectionnez **OK**.


## <a name="step-3-configure-app-information"></a>Étape 3 : Configurer les informations de l’application

1. Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, ajoutez les détails de votre application. Selon l’application que vous avez choisie, certaines valeurs de ce volet peuvent être remplies automatiquement.
    - **Nom** : entrez le nom de l’application, tel qu’il apparaît dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d’application existe deux fois, une seule des applications apparaît dans le portail d’entreprise.
    - **Description :** entrez la description de l’application. La description s’affiche dans le portail d’entreprise.
    - **Éditeur :** entrez le nom de l’éditeur de l’application.
    - **Système d’exploitation minimal** : dans la liste, choisissez la version de système d’exploitation minimale sur laquelle l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Ignorer la version de l’application** : choisissez **Oui** si le développeur de l’application met celle-ci automatiquement à jour.
    - **Catégorie** : sélectionnez une ou plusieurs catégories d’application intégrée, ou une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver l’application plus facilement quand ils parcourent le portail d’entreprise.
    - **Proposer cette application dans le portail d’entreprise** : met en évidence l’application sur la page principale du portail d’entreprise quand les utilisateurs recherchent des applications.
    - **URL d’information** : si vous le souhaitez, entrez l’URL d’un site web qui contient des informations sur cette application. L’URL s’affiche dans le portail d’entreprise.
    - **URL de déclaration de confidentialité** : si vous le souhaitez, entrez l’URL d’un site web qui contient des informations de confidentialité relatives à cette application. L’URL s’affiche dans le portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application. Exemple : **Service des ressources humaines**.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : chargez une icône associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
3. Une fois que vous avez fini, sélectionnez **OK**.

## <a name="step-4-finish-up"></a>Étape 4 : Terminer

1. Dans le volet **Ajouter une application**, vérifiez que les détails relatifs à votre application sont corrects.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

L’application que vous avez créée apparaît à présent dans la liste des applications. Dans la liste, vous pouvez affecter les applications aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

> [!NOTE]
> Les profils d’approvisionnement des applications métier iOS comportent un préavis de 30 jours avant expiration.

## <a name="step-5-update-a-line-of-business-app"></a>Étape 5 : Mettre à jour une application métier

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> Pour permettre au service Intune de déployer correctement un nouveau fichier IPA sur l’appareil, vous devez incrémenter la chaîne `CFBundleVersion` dans le fichier Info.plist du package IPA.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée apparaît dans la liste des applications. Vous pouvez à présent l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Consultez [Vue d’ensemble des cycles de vie des appareils et des applications](introduction-device-app-lifecycles.md).
