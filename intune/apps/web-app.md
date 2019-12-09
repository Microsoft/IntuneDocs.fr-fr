---
title: Ajouter des applications web à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications web (applications client-serveur) à Microsoft Intune.
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
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68e2e768067a88b8ae58adeb38c17d90ac995a30
ms.sourcegitcommit: b752acefec077c719e169e665c955adb944e85c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74781224"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Ajouter des applications web à Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune prend en charge divers types d’applications, notamment les applications web. Une application web est une application client-serveur. Le serveur fournit l’application web, qui englobe l’interface utilisateur, le contenu et les fonctionnalités. De plus, les plateformes d’hébergement web modernes offrent généralement, entre autres avantages, la sécurité et l’équilibrage de charge. Une application web est gérée séparément sur le web. Vous utilisez Microsoft Intune pour pointer vers ce type d’application. Vous affectez également les groupes d’utilisateurs qui peuvent accéder à cette application. 

Avant de pouvoir gérer et attribuer une application pour vos utilisateurs, ajoutez cette application à Intune. 

Intune crée un raccourci vers l’application web sur l’appareil de l’utilisateur. Pour les appareils iOS, un raccourci vers l’application web est ajouté à l’écran d’accueil. Pour les appareils de l’administrateur Android, un raccourci vers l’application web est ajouté au widget de portail d’entreprise Intune et le widget doit être épinglé manuellement par l’utilisateur. Pour les appareils Windows, un raccourci vers l’application web est placé dans le menu Démarrer.

> [!Note]
> Un navigateur doit être installé sur le périphérique de l’utilisateur pour lancer les applications web. 

> [!Note]
> Pour les appareils Android Enterprise, voir [Liens web Google Play géré](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>Ajouter une application web à Intune
Pour ajouter une application à Intune comme raccourci vers une application sur le web, effectuez les étapes suivantes :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Ajouter une application**, dans la liste déroulante **Type d’application**, sélectionnez le type **Lien web**.
4. Sélectionnez **Configurer**.
5. Dans le volet **Informations sur l’application**, ajoutez les informations suivantes :
    - **Nom** :  Entrez le nom de l’application tel qu’il apparaîtra dans le portail d’entreprise. 

        > [!NOTE]
        > Si vous modifiez le nom de l’application sur le portail Intune Azure après l’avoir déployée et installée, vous ne pourrez plus la cibler à l’aide de commandes.

    - **Description** : Entrez une description de l'application. Cette description est fournie aux utilisateurs dans le portail d’entreprise.
    - **Éditeur** : entrez le nom de l'éditeur de cette application.
    - **URL de l’application** : entrez l’URL du site web qui héberge l’application que vous souhaitez affecter.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver facilement l’application quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **Exiger l’ouverture de ce lien dans Managed Browser** : sélectionnez cette option pour affecter aux utilisateurs un lien vers un site web ou une application web qu’ils peuvent ouvrir dans Intune Managed Browser. Ce navigateur doit être installé sur leur appareil.
    - **Logo** : Chargez une icône qui sera associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
6. Sélectionnez **OK**.
7. Dans le volet **Ajouter une application**, sélectionnez **Ajouter**.

> [!Note]
> Actuellement, le déploiement d’applications web Intune sur des appareils iOS est associé au profil de gestion et ne peut pas être supprimé manuellement. Vous pouvez modifier le type de déploiement sur **Désinstaller** dans le portail Intune, où l’application web peut être supprimée automatiquement. Toutefois, si vous supprimez le déploiement avant de modifier l’intention d’affectation d'applications sur **Désinstaller**, l’application web sera définitivement en place sur l’appareil jusqu'à ce qu’il soit désinscrit d’Intune.

Les utilisateurs finaux peuvent lancer des applications web directement à partir de l’application Windows Portail d’entreprise en sélectionnant l’application web, puis en choisissant l’option **Ouvrir dans le navigateur**. L’URL web publiée est ouverte directement dans le navigateur web. 

## <a name="next-steps"></a>Étapes suivantes

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. Pour obtenir de l’aide, consultez [Affecter des applications à des groupes](apps-deploy.md). 
