---
title: Ajouter Microsoft Edge pour Windows 10 à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter Microsoft Edge pour Windows 10 à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
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
ms.openlocfilehash: 42f1c8fae156eaf08203f4a88cad8433749940ac
ms.sourcegitcommit: b6fe084b0419b3c9d456a8b0439b00f8c784db23
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2020
ms.locfileid: "76294793"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>Ajouter Microsoft Edge pour Windows 10 à Microsoft Intune

Pour pouvoir déployer, configurer, superviser ou protéger des applications, vous devez les ajouter au préalable à Intune. L’un des [types d’application](~/apps/apps-add.md#app-types-in-microsoft-intune) disponibles est Microsoft Edge *version 77 ou ultérieure*. En sélectionnant ce type d’application dans Intune, vous pouvez affecter et installer Microsoft Edge *version 77 ou ultérieure* sur des appareils Windows 10 que vous gérez.

> [!IMPORTANT]
> Ce type d’application est en **préversion publique** et offre des canaux stables, bêta et de développement pour Windows 10. Le déploiement s’effectue en anglais (EN) uniquement, mais les utilisateurs finaux peuvent changer la langue d’affichage dans le navigateur sous **Paramètres** > **Langues**. Microsoft Edge est une application Win32 installée dans le contexte du système et sur des architectures similaires (application x86 sur un système d’exploitation x86 et application x64 sur un système d’exploitation x64). Intune détecte les éventuelles installations Microsoft Edge préexistantes. S’il est installé dans le contexte utilisateur, l’installation du système le remplace. S’il est installé dans le contexte système, l’installation est signalée comme réussie. Par ailleurs, les mises à jour automatiques de Microsoft Edge sont définies sur **Activé** par défaut, et il n’est pas possible de désinstaller Microsoft Edge.

> [!NOTE]
> Microsoft Edge *version 77 ou ultérieure* est également disponible pour macOS.
> 
> Vous ne pouvez pas utiliser le déploiement d’applications intégré de Microsoft Edge pour des ordinateurs à rattacher à l’espace de travail. Le déploiement d’applications intégré nécessite l’extension de gestion Intune, qui existe uniquement pour les appareils rattachés à AAD. Vous pouvez toujours déployer Microsoft Edge *version 77 ou ultérieure* en chargeant un fichier *.msi* sur les **applications**. Consultez [Ajouter une application métier Windows à Microsoft Intune](~/apps/lob-apps-windows.md).

## <a name="prerequisites"></a>Prérequis
- Windows 10 RS2 ou version ultérieure est nécessaire.
- Toutes les versions préinstallées de Microsoft Edge *version 77 ou ultérieure* pour tous les canaux dans le contexte utilisateur sont remplacées par l’installation d’Edge dans le contexte système.

## <a name="configure-the-app-in-intune"></a>Configurer l’application dans Intune
Vous pouvez ajouter Microsoft Edge version 77 ou ultérieure à Intune en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans la liste **Type d’application**, sous **Microsoft Edge, version 77 ou ultérieure**, sélectionnez **Windows 10**.

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

## <a name="configure-app-settings"></a>Configurer les paramètres de l’application
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
Une fois que vous avez terminé la configuration de l’application, sélectionnez **Ajouter** dans le volet **Ajouter une application**. 

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. 

> [!NOTE]
> Actuellement, si vous annulez l’affectation du déploiement de Microsoft Edge, il reste sur l’appareil.

## <a name="troubleshooting"></a>Résolution des problèmes
**Microsoft Edge version 77 ou ultérieure pour Windows 10 :**<br>
Intune utilise l’extension de gestion Intune pour télécharger et déployer le programme d’installation de Microsoft Edge sur les appareils Windows 10 affectés, puis communique les paramètres de déploiement au programme d’installation de Microsoft Edge, qui télécharge et installe le navigateur Microsoft Edge directement à partir du réseau de distribution de contenu. Reportez-vous aux [prérequis pour l’extension de gestion Intune](~/apps/intune-management-extension.md#prerequisites) et aux bonnes pratiques d’accès à Azure Update Service et au réseau de distribution de contenu pour vous assurer que votre configuration réseau permet aux appareils Windows 10 d’accéder à ces emplacements. En outre, pour autoriser l’accès aux fichiers d’installation à partir d’un CDN afin d’installer le navigateur, vous devez autoriser l’accès aux points de terminaison Windows Update. Pour plus d’informations, voir [Gérer les points de terminaison de connexion pour Windows 10, version 1809 – Windows Update](https://docs.microsoft.com/windows/privacy/manage-windows-1809-endpoints#windows-update) et [Points de terminaison réseau pour Microsoft Intune](~/fundamentals/intune-endpoints.md).

## <a name="next-steps"></a>Étapes suivantes
- [Affecter des applications à des groupes](~/apps/apps-deploy.md)
