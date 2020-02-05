---
title: Ajouter Microsoft Edge sur les appareils macOS à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter Microsoft Edge sur les appareils macOS à l’aide de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ebcb81cd0f186a3fd23e0701d12ea871eab129a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912568"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Ajouter Microsoft Edge sur les appareils macOS à l’aide de Microsoft Intune

Pour pouvoir déployer, configurer, superviser ou protéger des applications, vous devez les ajouter au préalable à Intune. L’un des [types d’application](~/apps/apps-add.md#app-types-in-microsoft-intune) disponibles est Microsoft Edge *version 77 ou ultérieure*. En sélectionnant ce type d’application dans Intune, vous pouvez affecter et installer Microsoft Edge *version 77 ou ultérieure* sur des appareils macOS que vous gérez. Ce type d’application vous permet d’affecter facilement Microsoft Edge à des appareils macOS sans avoir besoin d’utiliser l’outil de création de package de restrictions d’application macOS. L’application est accompagnée de Microsoft AutoUpdate (MAU) qui garantit que les applications resteront sécurisées et à jour.

> [!IMPORTANT]
> Ce type d’application est en **préversion publique** et offre des canaux de développement et bêta pour macOS. Le déploiement s’effectue en anglais (EN) uniquement, mais les utilisateurs finaux peuvent changer la langue d’affichage dans le navigateur sous **Paramètres** > **Langues**. 

> [!NOTE]
> Microsoft Edge *version 77 ou ultérieure* est également disponible pour Windows 10.

## <a name="prerequisites"></a>Prérequis
- L’appareil macOS doit exécuter macOS 10.12 ou version ultérieure avant d’installer Microsoft Edge.

## <a name="add-microsoft-edge-to-intune"></a>Ajouter Microsoft Edge à Intune
Vous pouvez ajouter Microsoft Edge version 77 ou ultérieure à Intune en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans la liste **Type d’application**, sous **Microsoft Edge, version 77 ou ultérieure**, sélectionnez **macOS**.

## <a name="configure-app-information"></a>Configurer les informations de l’application
Dans cette étape, vous fournissez des informations sur le déploiement de cette application. Ces informations vous permettent d’identifier l’application dans Intune et aux utilisateurs de trouver l’application dans le portail d’entreprise.

1. Cliquez sur **Informations sur l’application** pour afficher le volet **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, vous fournissez des informations sur le déploiement de cette application. Ces informations vous permettent d’identifier l’application dans Intune et aux utilisateurs de trouver l’application dans le portail d’entreprise.
    - **Nom** : Entrez le nom de l'application tel qu'il s'affichera dans le portail d'entreprise. Assurez-vous que tous les noms sont uniques. Si le même nom d’application existe deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description** : Entrez une description de l'application. Par exemple, vous pouvez lister les utilisateurs ciblés dans la description.
    - **Éditeur** : Microsoft apparaît comme éditeur.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Ce paramètre facilite la recherche de l’application pour les utilisateurs qui parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l’application en premier sur la page principale du portail d’entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de la déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : Microsoft apparaît comme développeur.
    - **Propriétaire** : Microsoft apparaît comme propriétaire.
    - **Remarques** : entrez les éventuelles remarques à associer à cette application.
3. Sélectionnez **OK**.

## <a name="configure-microsoft-edge-settings"></a>Configurer les paramètres Microsoft Edge
Dans cette étape, configurez les options d’installation de l’application.

1. Dans le volet **Ajouter une application**, sélectionnez **Paramètres de l’application**.
2. Dans le volet **Paramètres de l’application**, sélectionnez **Stable**, **Bêta** ou **Dev** dans la liste **Canal** pour déterminer le canal Edge à partir duquel vous allez déployer l’application.

    - Le canal **Stable** est le canal recommandé pour le déploiement à grande échelle dans des environnements d’entreprise. Il est mis à jour toutes les six semaines, chaque version intégrant des améliorations du canal bêta.
    - Le canal **Bêta** correspond à l’expérience de préversion la plus stable de Microsoft Edge et au meilleur choix pour un pilote complet au sein de votre organisation. Avec des mises à jour majeures toutes les six semaines, chaque version intègre les connaissances et les améliorations du canal Dev.
    - Le canal **Dev** est prêt pour les commentaires d’entreprise sur Windows, Windows Server et macOS. Il est mis à jour chaque semaine et contient les dernières améliorations et les derniers correctifs.

    > [!NOTE]
    > Le logo du navigateur Microsoft Edge est affiché avec l’application quand les utilisateurs parcourent le portail d’entreprise.

3.  Sélectionnez **OK**.

## <a name="select-scope-tags-optional"></a>Sélectionner les balises d’étendue (facultatif)
Vous pouvez utiliser des balises d’étendue pour déterminer qui peut afficher des informations sur l’application cliente dans Intune. Pour plus d’informations sur les balises d’étendue, consultez Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée.
1.  Sélectionnez **Étendue (balises)**  > **Ajouter**.
2.  Utilisez la case **Sélectionner** pour rechercher les balises d’étendue.
3.  Cochez la case en regard des balises d’étendue que vous souhaitez attribuer à cette application.
4.  Cliquez sur **Sélectionner** > **OK**.

## <a name="add-the-app"></a>Ajouter l’application
Une fois que vous avez terminé la configuration, sélectionnez **Ajouter** dans le volet **Ajouter une application**. 

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. 

> [!NOTE]
> Actuellement, Apple n’offre aucun moyen pour Intune de désinstaller Microsoft Edge sur les appareils macOS.

## <a name="next-steps"></a>Étapes suivantes
- Pour apprendre à configurer Microsoft Edge sur les appareils macOS, consultez [Configurer Microsoft Edge sur les appareils macOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Pour en savoir plus sur l’inclusion et l’exclusion d’affectations d’application pour des groupes d’utilisateurs, consultez [Inclure et exclure des affectations d’applications](~/apps/apps-inc-exl-assignments.md).
- [Affecter des applications à des groupes](~/apps/apps-deploy.md)

