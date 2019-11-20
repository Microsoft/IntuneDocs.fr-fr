---
title: Utiliser des modèles pour les appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des modèles d’administration dans Microsoft Intune afin de créer des groupes de paramètres pour les appareils Windows 10. En définissant ces paramètres dans un profil de configuration d’appareil, vous pouvez contrôler les programmes Office, Microsoft Edge, sécuriser les fonctionnalités dans Internet Explorer, contrôler l’accès à OneDrive, utiliser les fonctionnalités du Bureau à distance, activer la lecture automatique, définir les paramètres de gestion de l’alimentation, utiliser l’impression HTTP, utiliser différentes options de connexion utilisateur et contrôler la taille du journal des événements.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9cec7395fc766f6a937e6c43ef3a32fb21610be
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059988"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Microsoft Intune

Vous gérez les appareils dans votre organisation et souhaitez créer des groupes de paramètres à appliquer à différents groupes d’appareils. Supposons que vous avez plusieurs groupes d’appareils. Vous souhaitez assigner des ensembles de paramètres distincts au groupe A et au groupe B. Vous voulez également voir rapidement tous les paramètres que vous pouvez configurer.

Vous pouvez effectuer tout cela à l’aide des **modèles d’administration** fournis dans Microsoft Intune. Les modèles d’administration contiennent des centaines de paramètres qui contrôlent des fonctionnalités dans Microsoft Edge version 77 et ultérieure, Internet Explorer, les programmes Microsoft Office, le Bureau à distance, OneDrive, les mots de passe et les codes PIN, et plus encore. Ces paramètres permettent aux administrateurs de groupe de gérer les stratégies de groupe à l’aide du cloud.

Les paramètres Windows sont similaires aux paramètres de stratégie de groupe (GPO) dans Active Directory (AD). Ces paramètres sont intégrés à Windows et sont des [paramètres basés sur ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) qui utilisent XML. Les paramètres Office et Microsoft Edge sont ingérés par ADMX et utilisent les paramètres ADMX dans les [fichiers de modèles d’administration Office](https://www.microsoft.com/download/details.aspx?id=49030) et les [fichiers de modèles d’administration Microsoft Edge](https://www.microsoftedgeinsider.com/enterprise). Toutefois, les modèles Intune sont entièrement basés dans le cloud. Ils offrent un moyen simple et rapide de configurer les paramètres et de trouver les paramètres souhaités.

Les **modèles d’administration** sont intégrés à Intune et ne nécessitent aucune personnalisation, y compris l’utilisation d’OMA-URI. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres de modèle comme un moyen centralisé de gérer vos appareils Windows 10.

Cet article présente les étapes de la création d’un modèle pour les appareils Windows 10 et montre comment filtrer tous les paramètres disponibles dans Intune. Quand vous créez un modèle, vous créez en même temps un profil de configuration d’appareil. Vous pouvez ensuite assigner ou déployer ce profil sur les appareils Windows 10 dans votre organisation.

## <a name="before-you-begin"></a>Avant de commencer

- Certains de ces paramètres sont disponibles à partir de la version 1703 de Windows 10 (RS2). Certains paramètres ne sont pas inclus dans toutes les éditions de Windows. Pour une expérience optimale, il est recommandé d’utiliser Windows 10 Entreprise version 1903 (19H1) et les versions ultérieures.

- Les paramètres Windows utilisent des [fournisseurs de services de configuration de stratégie Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies). Les fournisseurs de services de configuration fonctionnent sur les différentes éditions de Windows, telles que les éditions Famille, Professionnel et Entreprise. Pour voir si un fournisseur de services de configuration fonctionne sur une édition spécifique, accédez à [Fournisseurs de services de configuration de stratégie Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies).

## <a name="create-a-template"></a>Créer un modèle

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom pour le profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Modèles d’administration**.

4. Sélectionnez **Créer**. Dans la nouvelle fenêtre, sélectionnez **Paramètres**. Vous pouvez voir tous les paramètres listés, et afficher davantage de paramètres à l’aide des flèches Précédent et Suivant :

    ![Voir un exemple de liste de paramètres et utiliser les boutons Précédent et Suivant](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Les paramètres Windows dans Intune sont mis en corrélation avec le chemin d’accès à la stratégie de groupe locale que vous voyez dans l’éditeur de stratégie de groupe local (`gpedit`).

5. Dans la liste déroulante, sélectionnez **Tous les produits**. Dans la liste, vous pouvez également filtrer les paramètres pour afficher uniquement les paramètres **Windows**, les paramètres **Office** ou les paramètres **Edge version 77 ou ultérieure** :

    ![Filtrer la liste pour afficher tous les paramètres Windows ou Office dans les modèles d’administration dans Intune](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Les paramètres Microsoft Edge s’appliquent à :
    >
    > - Microsoft Edge version 77 ou ultérieure. Pour configurer Microsoft Edge version 45 et les versions antérieures, consultez [Paramètres de restriction d’appareil du navigateur Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).
    > - Windows 10 RS4 et versions ultérieures avec la mise à jour [KB 4512509](https://support.microsoft.com/kb/4512509) installée
    > - Windows 10 RS5 et versions ultérieures avec la mise à jour [KB 4512534](https://support.microsoft.com/kb/4512534) installée
    > - Windows 10 19H1 et versions ultérieures avec la mise à jour [KB 4512941](https://support.microsoft.com/kb/4512941) installée

6. Sélectionnez l’un des paramètres. Par exemple, filtrez sur **Office**, puis sélectionnez **Activer la navigation restreinte**. Une description détaillée du paramètre s’affiche. Choisissez **Activé** ou **Désactivé**, ou laissez le paramètre défini sur **Non configuré** (valeur par défaut). La description détaillée explique également ce qui se produit quand vous choisissez l’option **Activé**, **Désactivé** ou **Non configuré**.
7. Cliquez sur **OK** pour enregistrer vos modifications.

Continuez à parcourir la liste des paramètres et configurez les paramètres souhaités dans votre environnement. Voici quelques exemples :

- Utilisez le paramètre **Paramètres de notification de macro VBA** pour gérer les macros VBA dans différents programmes Microsoft Office, comme Word et Excel.
- Utilisez le paramètre **Autoriser les téléchargements de fichiers** pour autoriser ou bloquer les téléchargements à partir d’Internet Explorer.
- Utilisez **Demander un mot de passe lorsqu’un ordinateur sort de la veille (sur secteur)** pour demander aux utilisateurs d’entrer un mot de passe quand les appareils sortent du mode veille.
- Utilisez le paramètre **Télécharger les contrôles ActiveX non signés** pour empêcher les utilisateurs de télécharger des contrôles ActiveX non signés depuis Internet Explorer.
- Utilisez le paramètre **Désactiver la restauration du système** pour autoriser ou empêcher les utilisateurs d’effectuer une restauration du système sur l’appareil.
- Utilisez le paramètre **Autoriser l’importation des favoris** pour autoriser ou non les utilisateurs à importer les favoris d’un autre navigateur dans Microsoft Edge.
- Et il y a bien d’autres exemples...

## <a name="find-some-settings"></a>Rechercher des paramètres spécifiques

Les modèles contiennent des centaines de paramètres. Pour trouver plus facilement des paramètres spécifiques, utilisez les fonctionnalités intégrées disponibles :

- Dans votre modèle, sélectionnez la colonne **Paramètres**, **État**, **Type de paramètre** ou **Chemin** sur laquelle vous voulez trier la liste de paramètres. Par exemple, sélectionnez la colonne **Chemin** pour afficher tous les paramètres situés dans le chemin `Microsoft Excel` :

  ![Cliquez sur chemin d’accès pour afficher tous les paramètres regroupés par stratégie de groupe ou chemin d’accès ADMX dans modèles d’administration dans Intune](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Dans votre modèle, utilisez la zone **Rechercher** pour trouver des paramètres spécifiques. Vous pouvez effectuer une recherche en définissant le titre ou le chemin d’accès. Par exemple, recherchez `copy`. Tous les paramètres avec `copy` sont affichés :

  ![Rechercher une copie pour afficher tous les paramètres Windows et Office dans les modèles d’administration dans Intune](./media/administrative-templates-windows/search-copy-settings.png) 

  En guide d’autre exemple, recherchez `microsoft word`. Vous voyez alors tous les paramètres que vous pouvez définir pour le programme Microsoft Word. Recherchez `explorer` pour voir tous les paramètres Internet Explorer que vous pouvez ajouter à votre modèle.

## <a name="next-steps"></a>Étapes suivantes

Le modèle est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le modèle (également appelé profil)](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).
