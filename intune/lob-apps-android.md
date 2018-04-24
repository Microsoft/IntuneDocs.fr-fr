---
title: Guide pratique pour ajouter des applications métier Android à Microsoft Intune
titlesuffix: ''
description: Découvrez comment ajouter des applications métier Android à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0297cb0b399d487f548bf6fdd9fb74946bbcb7b1
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Guide pratique pour ajouter des applications métier Android à Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Une application métier est une application que vous ajoutez à Intune à partir d’un fichier d’installation d’application. Ces types d’applications sont généralement écrites en interne. Intune installe l’application métier sur l’appareil de l’utilisateur. 

> [!Note]
> Pour plus d’informations sur les applications métier du Google Play for Work Store, consultez [Utiliser une application métier du Google Play for Work Store](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store). 

## <a name="step-1---specify-the-software-setup-file"></a>Étape 1 : spécifier le fichier d’installation de logiciel

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Applications mobiles**.
4. Dans la charge de travail **Applications mobiles**, choisissez **Gérer** > **Applications**.
5. Au-dessus de la liste des applications, choisissez **Ajouter**.
6. Dans le volet **Ajouter une application**, choisissez **Application métier**.

## <a name="step-2---configure-the-app-package-file"></a>Étape 2 : configurer le fichier de package d’application

1. Dans le volet **Ajouter une application**, choisissez **Fichier de package d’application**.
2. Dans le volet **Fichier de package d’application**, cliquez sur le bouton Parcourir et sélectionnez un fichier d’installation Android avec l’extension **.apk**.
3. Quand vous avez terminé, cliquez sur **OK**.


## <a name="step-3---configure-app-information"></a>Étape 3 : configurer les informations de l’application

1. Dans le volet **Ajouter une application**, choisissez le fichier **Package de l’application**.
2. Dans le volet **Informations sur l’application**, ajoutez les détails de votre application. Selon l’application choisie, certaines valeurs de ce volet peuvent avoir été renseignées automatiquement :
    - **Nom** : entrez le nom de l’application à afficher dans le portail d’entreprise. Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d'application existe deux fois, seule l'une des applications sera proposée aux utilisateurs du portail d'entreprise.
    - **Description** : entrez la description de l’application à afficher aux utilisateurs dans le portail d’entreprise.
    - **Éditeur :** entrez le nom de l’éditeur de l’application.
    - **Système d’exploitation minimal** : dans la liste, choisissez le système d’exploitation minimal sur lequel l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Ignorer la version de l’application** : définissez cette valeur sur **Oui** si l’application est automatiquement mise à jour par son développeur.
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

1. Dans le volet **Ajouter une application**, vérifiez les détails de votre application.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

L’application que vous avez créée s’affichera dans la liste des applications, où vous pouvez l’affecter aux groupes que vous choisissez. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Étape 5 : Mise à jour d’une application métier

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Pour que le service Intune parvienne à déployer un nouveau fichier APK sur l’appareil, il faut incrémenter la chaîne android:versionCode dans le fichier AndroidManifest.xml du package APK.

## <a name="next-steps"></a>Étapes suivantes

- L’application que vous avez créée s’affiche dans la liste des applications. Vous pouvez maintenant l’affecter aux groupes de votre choix. Pour plus d’aide, consultez [Guide pratique pour attribuer des applications à des groupes](apps-deploy.md).

- Découvrez plus d’informations sur les façons dont vous pouvez surveiller les propriétés et l’affectation de votre application. Pour plus d’informations, consultez [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).

- Découvrez plus d’informations sur le contexte de votre application dans Intune. Pour plus d’informations, consultez [Vue d’ensemble des cycles de vie des appareils et des applications](introduction-device-app-lifecycles.md).
