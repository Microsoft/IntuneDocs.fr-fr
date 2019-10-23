---
title: Ajouter une application métier Android à Microsoft Intune
description: Découvrez comment ajouter une application métier (LOB) Android à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4c1f3d8b6b7edbf51ca2aaa681909e6c220de3c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507236"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Ajouter une application métier Android à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Une application métier est une application que vous ajoutez à Intune à partir d’un fichier d’installation d’application. En règle générale, ce genre d’application est écrite en interne. Intune installe l’application métier sur l’appareil de l’utilisateur. 

> [!Note]
> Pour plus d'informations sur les applications métier et la console développeur Google Play, voir [Publication d’applications Google Play gérées privées (métier) à l’aide de la console développeur Google](apps-add-android-for-work.md?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console). 

> [!Note]
> Pour les appareils Android for Work, voir [Ajouter des applications Google Play managé à des appareils Android Enterprise avec Intune](apps-add-android-for-work.md). 

## <a name="step-1-specify-the-software-setup-file"></a>Étape 1 : Spécifier le fichier d'installation de logiciel

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet **Intune**, sélectionnez **Applications clientes**.
3. Dans la charge de travail **Applications clientes**, choisissez **Gérer** > **Applications**.
4. Au-dessus de la liste des applications, sélectionnez **Ajouter**.
5. Dans le volet **Ajouter une application**, sélectionnez **Application métier**.

## <a name="step-2-configure-the-app-package-file"></a>Étape 2 : Configurer le fichier de package d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Fichier de package d’application**.
2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Sélectionnez ensuite un fichier d’installation Android ayant l’extension **.apk**.
3. Une fois que vous avez fini, sélectionnez **OK**.

## <a name="step-3-configure-app-information"></a>Étape 3 : Configurer les informations de l’application

1. Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, ajoutez les détails de votre application. Selon l’application que vous avez choisie, certaines valeurs de ce volet peuvent être remplies automatiquement.
    - **Nom** : Entrez le nom de l’application, tel qu’il apparaît dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d’application existe deux fois, une seule des applications apparaît dans le portail d’entreprise.
    - **Description** : entrez la description de l’application. La description s’affiche dans le portail d’entreprise.
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

1. Dans le volet **Ajouter une application**, vérifiez que les détails de votre application sont corrects.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

L’application que vous avez créée apparaît à présent dans la liste des applications. Dans la liste, vous pouvez affecter l’application aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

## <a name="step-5-update-a-line-of-business-app"></a>Étape 5 : Mettre à jour une application métier

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

Si l’option **Check apps from external sources (Vérifier les applications provenant de sources externes)** est activée sur l'appareil Android, l'utilisateur recevra un message avant d'installer la mise à jour. Sinon, la mise à jour sera automatiquement installée.

> [!Note]
> Pour permettre au service Intune de déployer correctement un nouveau fichier APK sur l’appareil, vous devez incrémenter la chaîne `android:versionCode` dans le fichier AndroidManifest.xml du package APK.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée apparaît dans la liste des applications. Vous pouvez à présent l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Consultez [Vue d’ensemble des cycles de vie des appareils et des applications](../fundamentals/device-lifecycle.md).
