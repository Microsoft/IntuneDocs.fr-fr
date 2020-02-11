---
title: Ajouter des applications de l’App Store iOS dans Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications de l’App Store iOS à Microsoft Intune. Vous pouvez affecter des applications à l’aide de cette méthode si elles sont gratuites dans l’App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2daa7428cf8677f9e1a2b11db2b3ce65e2df8bc4
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754998"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Ajouter des applications de l’App Store iOS dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Aidez-vous des informations contenues dans cet article pour ajouter des applications de l’App Store iOS à Microsoft Intune. Les applications de l’App Store iOS sont des applications installées par Intune sur les appareils de vos utilisateurs. Un utilisateur fait partie du personnel de votre entreprise. Les applications de l’App Store iOS sont automatiquement mises à jour.

>[!NOTE]
>Bien que les utilisateurs d’appareils iOS puissent supprimer certaines applications iOS intégrées, telles que Bourse et Plans, vous ne pouvez pas vous servir d’Intune pour redéployer ces applications. Si les utilisateurs suppriment ces applications, ils doivent se rendre sur l’App Store et les réinstaller manuellement.

## <a name="before-you-start"></a>Avant de commencer

Vous pouvez affecter des applications à l’aide de cette méthode uniquement si elles sont gratuites dans l’App Store. Si vous souhaitez affecter des applications payantes à l’aide d’Intune, utilisez le [programme d’achat en volume (VPP) iOS](vpp-apps-ios.md).

>[!NOTE]
>Avec Microsoft Intune, nous vous recommandons d’utiliser le navigateur Microsoft Edge ou Google Chrome.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Sélectionner le type d’application**, sous les types **Application du Store** disponibles, sélectionnez **Application de l’App Store iOS**.
4. Cliquez sur **Sélectionner**.<br>
   Les étapes **Ajouter une application** sont affichées.
5. Sélectionnez **Rechercher dans l’App Store**.
6. Dans le volet **Rechercher dans l’App Store**, sélectionnez les paramètres régionaux du pays/de la région de l’App Store.
7. Dans la zone **Rechercher**, tapez le nom (ou une partie du nom) de l’application.  
    Intune recherche dans le Store et retourne la liste des résultats pertinents.
8. Dans la liste des résultats, sélectionnez l’application de votre choix, puis **Sélectionner**.<br>

   La page **Informations sur l’application** s’affiche dans le volet **Ajouter une application**. Lorsque cela est possible, les informations sur l’application sont ajoutées en fonction de l’application que vous avez sélectionnée dans le magasin.

9. Dans la page **Informations sur l'application**, ajoutez les détails de l'application. Selon l’application choisie, certaines valeurs de ce volet peuvent avoir été renseignées automatiquement :
    - **Nom** : Entrez le nom de l’application tel qu’il apparaîtra dans le portail d’entreprise. Veillez à choisir un nom d’application unique. Si vous utilisez un nom d’application qui existe déjà, un seul sera présenté aux utilisateurs dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. Cette description est fournie aux utilisateurs dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **URL de l’App Store** : tapez l’URL de l’App Store de l’application à créer.
    - **Système d’exploitation minimal** : dans la liste, choisissez la version de système d’exploitation la plus ancienne sur laquelle l’application peut être installée. Si vous affectez l’application à un appareil avec un système d’exploitation antérieur, elle ne sera pas installée.
    - **Type d’appareil applicable** : dans la liste, sélectionnez les appareils qui sont utilisés par l’application.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver facilement l’application quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de la déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application. Ce champ est visible uniquement par les administrateurs. Les utilisateurs ne le voient pas.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application (par exemple, *Ressources humaines*). Ce champ est visible uniquement par les administrateurs. Les utilisateurs ne le voient pas.
    - **Remarques** : entrez les éventuelles remarques à associer à cette application. Ce champ est visible seulement par un administrateur ; les utilisateurs finaux ne le voient pas.
    - **Logo** : si vous le souhaitez, chargez une icône à associer à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
10. Cliquez sur **Suivant** pour afficher la page **Balises d’étendue**.
11. Cliquez sur **Sélectionner des balises d’étendue** pour ajouter éventuellement des balises d’étendue pour l'application. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée](~/fundamentals/scope-tags.md).
12. Cliquez sur **Suivant** pour afficher la page **Affectations**.
13. Sélectionnez les affectations de groupe pour l'application. Pour plus d’informations, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils](~/fundamentals/groups-add.md). 
14. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**. Vérifiez les valeurs et les paramètres que vous avez saisis pour l'application.
15. Lorsque vous avez terminé, cliquez sur **Créer** pour ajouter l'application à Intune.

Le volet **Vue d’ensemble** de l'application que vous avez créée s'affiche.

## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)
