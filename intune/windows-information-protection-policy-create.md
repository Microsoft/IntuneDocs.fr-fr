---
title: Créer et déployer une stratégie de protection des applications Protection des informations Windows (WIP)
titlesuffix: Microsoft Intune
description: Créer et déployer une stratégie de protection des applications Protection des informations Windows (WIP) avec Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b5599e98b9712d30979c327167b19b159d3ff5dc
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181325"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Créer et déployer une stratégie de protection d’application Protection des informations Windows (WIP) avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez utiliser des stratégies de protection des applications avec les applications Windows 10 pour protéger les applications sans inscrire les appareils.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez comprendre certains concepts lors de l’ajout d’une stratégie WIP :

### <a name="list-of-allowed-and-exempt-apps"></a>Liste des applications autorisées et exemptes

-   **Applications protégées** : il s’agit des applications qui doivent adhérer à cette stratégie.

-   **Applications exemptes** Ces applications sont exemptes de cette stratégie et peuvent accéder aux données d’entreprise sans restrictions.

### <a name="types-of-apps"></a>Types d’applications

-   **Applications recommandées :**  une liste préremplie d’applications (principalement Microsoft Office) que vous pouvez facilement importer dans la stratégie.
-   **Applications du Store** : vous pouvez ajouter n’importe quelle application du Windows Store à la stratégie.
-   **Applications de bureau Windows** : vous pouvez ajouter n’importe quelle application de bureau Windows traditionnelle à la stratégie (.exe, .dll, etc.).

## <a name="prerequisites"></a>Prérequis

Vous devez configurer le fournisseur GAM avant de pouvoir créer une stratégie de protection d’application WIP. En savoir plus sur la façon de [configurer le fournisseur MAM avec Intune](app-protection-policies-configure-windows-10.md).  

> [!IMPORTANT]
> WIP ne prend pas en charge les identités multiples, une seule identité gérée peut exister à la fois.

Vous devez aussi disposer des licences et des mises à jour suivantes :

-   Licence [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)





## <a name="to-add-a-wip-app-protection-policy"></a>Pour ajouter une stratégie de protection des applications WIP

Une fois Intune configuré dans votre organisation, vous pouvez créer une stratégie propre à WIP.

> [!TIP]  
> Pour plus d’informations sur la création de stratégies WIP pour Intune, notamment les paramètres disponibles et la façon de les configurer, consultez [Créer une stratégie Protection des informations Windows (WIP) avec GAM à l’aide du portail Azure pour Microsoft Intune](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure) dans la bibliothèque de documentation sur la sécurité Windows. 


1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**.
3. Sélectionnez **Applications clientes** dans le panneau **Microsoft Intune**.
4. Sélectionnez **Stratégies de protection des applications**  sur le panneau **Applications clientes**.
5. Sélectionnez **Ajouter une stratégie** pour afficher le panneau **Ajouter une stratégie**.
6. Ajoutez les valeurs suivantes :
    - **Nom :** tapez un nom (obligatoire) pour votre nouvelle stratégie.
    - **Description :** (facultatif) entrez une description.
    - **Plateforme :** choisissez **Windows 10** comme plateforme prise en charge pour votre stratégie de protection d’application.
    - **État d’inscription :** choisissez **Sans inscription** en tant qu’état d’inscription de votre stratégie.
7.  Choisissez **Créer**. La stratégie est créée et apparaît dans le tableau du panneau **Stratégies de protection des applications**.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>Pour ajouter les applications recommandées à votre liste d’applications protégées

1. Sélectionnez **Applications clientes** dans le panneau **Microsoft Intune**.
2. Sélectionnez **Stratégies de protection des applications**  sur le panneau **Applications clientes**.
3. Sur le panneau **Stratégies de protection des applications**, choisissez la stratégie que vous souhaitez modifier. Le panneau **Protection des applications Intune** s’affiche.
4. Choisissez **Applications protégées** dans le panneau **Protection des applications Intune**. Le panneau **Applications protégées** s’ouvre et affiche toutes les applications qui sont déjà incluses dans la liste pour cette stratégie de protection des applications.
5. Sélectionnez **Ajouter des applications**. Les informations **Ajouter des applications** affichent une liste filtrée des applications. La liste en haut du panneau vous permet de modifier le filtre de la liste.
6. Sélectionnez chaque application pouvant accéder à vos données d’entreprise.
7. Cliquez sur **OK**. Le panneau **Applications protégées** est mis à jour et affiche toutes les applications sélectionnées.
8. Cliquez sur **Save**.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>Ajouter une application de Store à votre liste d’applications protégées

**Pour ajouter une application du Windows Store**
1. Sélectionnez **Applications clientes** dans le panneau **Microsoft Intune**.
2. Sélectionnez **Stratégies de protection des applications**  sur le panneau **Applications clientes**.
3. Sur le panneau **Stratégies de protection des applications**, choisissez la stratégie que vous souhaitez modifier. Le panneau **Protection des applications Intune** s’affiche.
4. Choisissez **Applications protégées** dans le panneau **Protection des applications Intune**. Le panneau **Applications protégées** s’ouvre et affiche toutes les applications qui sont déjà incluses dans la liste pour cette stratégie de protection des applications.
5. Sélectionnez **Ajouter des applications**. Les informations **Ajouter des applications** affichent une liste filtrée des applications. La liste en haut du panneau vous permet de modifier le filtre de la liste.
6. Dans la liste, sélectionnez **Applications Store**.
7. Entrez les valeurs **Nom**, **Éditeur**, **Nom du produit** et **Action**. Veillez à définir la valeur **Action** sur **Autoriser**, de sorte que l’application ait accès à vos données d’entreprise.
9. Cliquez sur **OK**. Le panneau **Applications protégées** est mis à jour et affiche toutes les applications sélectionnées.
10. Cliquez sur **Save**.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>Ajouter une application de bureau à votre liste d’applications protégées

**Pour ajouter une application de bureau**
1. Sélectionnez **Applications clientes** dans le panneau **Microsoft Intune**.
2. Sélectionnez **Stratégies de protection des applications**  sur le panneau **Applications clientes**.
3. Sur le panneau **Stratégies de protection des applications**, choisissez la stratégie que vous souhaitez modifier. Le panneau **Protection des applications Intune** s’affiche.
4. Choisissez **Applications protégées** dans le panneau **Protection des applications Intune**. Le panneau **Applications protégées** s’ouvre et affiche toutes les applications qui sont déjà incluses dans la liste pour cette stratégie de protection des applications.
5. Sélectionnez **Ajouter des applications**. Les informations **Ajouter des applications** affichent une liste filtrée des applications. La liste en haut du panneau vous permet de modifier le filtre de la liste.
6. Dans la liste, sélectionnez **Applications de bureau**.
7. Entrez les valeurs **Nom**, **Éditeur**, **Nom du produit**, **Fichier**, **Version mini**, **Version maxi** et **Action**. Veillez à définir la valeur **Action** sur **Autoriser**, de sorte que l’application ait accès à vos données d’entreprise.
9. Cliquez sur **OK**. Le panneau **Applications protégées** est mis à jour et affiche toutes les applications sélectionnées.
10. Cliquez sur **Save**.

## <a name="wip-learning"></a>WIP Learning
Après avoir ajouté les applications que vous souhaitez protéger avec WIP, vous devez appliquer un mode de protection à l’aide de **WIP Learning**.

### <a name="before-you-begin"></a>Avant de commencer

WIP Learning est un rapport qui vous permet de surveiller vos applications WIP et les applications inconnues de WIP. Les applications inconnues sont celles non déployées par le département informatique de votre organisation. Vous pouvez exporter ces applications à partir du rapport et les ajouter à vos stratégies WIP pour éviter une perturbation de la productivité avant l’application de WIP en mode « Bloquer ».

<!-- 1631908 --> En plus de l’affichage des informations sur les applications WIP, vous pouvez consulter un récapitulatif des appareils qui partagent des données de travail avec des sites web. Ces informations vous permettront d’identifier les sites web à ajouter aux stratégies WIP des utilisateurs et des groupes. Le résumé montre les URL du site Web accessibles par des applications compatibles WIP.

Quand vous utilisez des applications WIP et des applications inconnues de WIP, nous vous recommandons de commencer par **Silencieux** ou **Autoriser les substitutions** quand vous vérifiez sur un petit groupe que vous avez les bonnes applications dans votre liste d’applications protégées. Une fois cela fait, vous pouvez passer sur votre stratégie d’application finale, **Bloquer**.

### <a name="what-are-the-protection-modes"></a>Quels sont les modes de protection ?

#### <a name="block"></a>Bloquer
WIP recherche des pratiques de partage de données inappropriées et empêche l’utilisateur de terminer l’action. Les actions bloquées peuvent inclure le partage d’informations entre des applications non protégées pas votre entreprise, ou le partage de données d’entreprise entre des personnes et appareils en dehors de votre organisation.

#### <a name="allow-overrides"></a>Autoriser l’utilisateur à ignorer les avertissements
WIP recherche les partages de données inappropriés, et avertit les utilisateurs quand ils font quelque chose de potentiellement dangereux. Toutefois, ce mode permet à l’utilisateur de remplacer la stratégie et de partager les données. L’action est alors consignée dans votre journal d’audit.

#### <a name="silent"></a>Silencieux
WIP s’exécute en mode silencieux, en consignant les partages de données inappropriés, sans bloquer l’utilisateur avec les invites qui s’affichent dans le mode Autoriser l’utilisateur à ignorer les avertissements. Les actions non autorisées d’applications, comme les tentatives d’accès inappropriées à une ressource réseau ou à des données protégées par WIP sont toujours arrêtées.

#### <a name="off-not-recommended"></a>Désactivé (non recommandé)
WIP est désactivé et ne permet pas de protéger ou vérifier vos données.

Après avoir désactivé WIP, une tentative est effectuée pour déchiffrer les fichiers marqués par WIP sur les disques connectés localement. Notez que les informations de déchiffrement et de stratégie précédentes ne sont pas réappliquées automatiquement si vous réactivez la protection WIP.

### <a name="add-a-protection-mode"></a>Ajouter un mode de protection

1.  Dans le panneau **Stratégie d’application**, choisissez le nom de votre stratégie, puis **Paramètres obligatoires**.

    ![Capture d’écran du mode d’apprentissage](./media/learning-mode-sc1.png)

1.  Sélectionnez un paramètre, puis choisissez **Enregistrer**.

### <a name="use-wip-learning"></a>Utiliser WIP Learning

1. Ouvrez le [portail Azure](https://portal.azure.com). Choisissez **Tous les services**. Tapez **Intune** dans la zone de texte du filtre.

3. Choisissez **Intune** > **Applications clientes**.

4. Choisissez **État de protection de l’application** > **Rapports** > **Apprentissage Protection des informations Windows**.  

    Une fois que les applications s’affichent dans le rapport de journalisation Apprentissage Protection des informations Windows, vous pouvez les ajouter à vos stratégies de protection d’application.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés
Autorise ou interdit l’indexation des éléments. Ce commutateur concerne l’indexeur de recherche Windows, qui contrôle s’il indexe les éléments chiffrés, comme les fichiers protégés par la Protection des informations Windows.

Cette option de stratégie de protection d’application se trouve dans les **Paramètres avancés** de la stratégie de Protection des informations Windows. La stratégie de protection d’application doit être définie sur la plateforme *Windows 10* et la stratégie d’application **État de l’inscription** doit être définie sur **Avec inscription**.

Quand la stratégie est activée, les éléments protégés par la Protection des informations Windows sont indexés et leurs métadonnées sont stockées à un emplacement non chiffré. Les métadonnées incluent des éléments comme le chemin et la date de modification des fichiers.

Quand la stratégie est désactivée, les éléments protégés par la Protection des informations Windows ne sont pas indexés et n’apparaissent pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Il peut également y avoir un impact sur les performances pour les photos et les applications Groove si de nombreux fichiers multimédias sont protégés par la Protection des informations Windows sur l’appareil.

## <a name="add-encrypted-file-extensions"></a>Ajouter des extensions de fichiers chiffrés

En plus de définir l’option **Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés**, vous pouvez spécifier une liste d’extensions de fichiers. Les fichiers avec ces extensions sont chiffrés lors de la copie à partir d’un partage SMB (Server Message Block) dans les limites de l’entreprise, telles qu’elles sont définies dans la liste des emplacements réseau. Quand cette stratégie n’est pas spécifiée, le comportement existant de chiffrement automatique est appliqué. Quand cette stratégie est configurée, seuls les fichiers avec les extensions présentes dans la liste sont chiffrés.

## <a name="deploy-your-wip-app-protection-policy"></a>Déployer une stratégie de protection d’application WIP

> [!IMPORTANT]
> Ces informations s’appliquent à la Protection des informations Windows sans inscription d’appareils.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Une fois que vous avez créé votre stratégie de protection d’application WIP, vous devez la déployer dans votre organisation à l’aide de MAM.

1.  Dans le panneau **Stratégie d’application**, choisissez votre nouvelle stratégie de protection d’application, puis **Groupes d’utilisateurs** > **Ajouter un groupe d’utilisateurs**.

    Une liste de groupes d’utilisateurs, composée de tous les groupes de sécurité figurant dans Azure Active Directory, s’ouvre dans le panneau **Ajouter un groupe d’utilisateurs**.

2.  Choisissez le groupe auquel vous souhaitez appliquer votre stratégie, puis **Sélectionner** pour déployer la stratégie.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la Protection des informations Windows, consultez [Protéger vos données d’entreprise à l’aide de la Protection des informations Windows](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
