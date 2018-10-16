---
title: Bien démarrer avec les applications dans Microsoft Intune
titlesuffix: ''
description: Recherchez et ajoutez des applications sur les appareils pour permettre à votre personnel d’effectuer leur travail.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 399efad4f4cbe4dde1b45004daa9d0264e0db777
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903401"
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Bien démarrer avec l’ajout d’applications dans Microsoft Intune

Pour pouvoir affecter, surveiller, configurer ou protéger des applications, vous devez les ajouter à Intune. Intune prend en charge plusieurs types d’applications. Les options disponibles varient selon le type d’application.

Intune vous permet d’ajouter et d’affecter ces types d’applications à vos appareils d’entreprise :
- **Applications du Store** : pour les appareils où vous devez appliquer une gestion des applications mobiles supplémentaire à des applications disponibles dans l’App Store.
- **Applications écrites en interne (métiers)** : quand vous chargez un fichier qui est téléchargé sur les appareils de vos utilisateurs.
- **Applications intégrées** : quand vous affectez des applications gérées organisées, comme les applications Office 365, à des appareils iOS et Android.
- **Applications sur le web** : quand Intune crée un raccourci vers l’application web sur l’écran d’accueil de l’appareil.

> [!NOTE]
> Les nouvelles stratégies appliquées à un groupe d’appareils dynamique peuvent nécessiter jusqu’à huit heures pour être propagées à tous les appareils du groupe.

## <a name="how-do-i-assign-a-public-store-app"></a>Comment attribuer une application de magasin public ?

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Sélectionnez **Applications clientes**, puis **Applications**.
4. Sélectionnez **Ajouter**, puis sélectionnez **iOS** comme le **Type d’application**.
5. Choisissez **Sélectionner une application** pour afficher le volet **Rechercher dans l’App Store**.
6. Dans la zone de texte, recherchez une application à affecter à l’appareil. Choisissez l’application, puis cliquez sur **Sélectionner**.
7. Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application**, puis vérifiez que toutes les informations sur l’application sont renseignées. Vous pouvez ajouter d’autres détails facultatifs pour vous aider à organiser cette application, comme **Propriétaire**, **Remarques**, **Développeur** et une **URL de confidentialité** pour la politique de confidentialité de votre entreprise.
8. Vérifiez que vous avez sélectionné **Oui** pour **Proposer cette application dans le portail d’entreprise**, puis sélectionnez **OK**.
9. Sélectionnez **Ajouter** dans le volet **Ajouter une application** pour ajouter l’application. Vous accédez alors à la **Vue d’ensemble** de cette application. Choisissez **Attributions**, puis cliquez sur **Ajouter le groupe** pour l’assigner à votre groupe de test. Rendez l’application **Disponible** pour le téléchargement. L’application doit alors apparaître comme **Application proposée** sur votre appareil de test.


- [Guide pratique pour affecter des applications à des groupes](apps-deploy.md)

## <a name="learn-more"></a>En savoir plus

* [Qu’est-ce que la gestion des applications avec Intune ?](app-management.md)
* [Vue d’ensemble du cycle de vie des applications](app-lifecycle.md)
* [Que sont les stratégies de protection des applications ?](app-protection-policy.md)
