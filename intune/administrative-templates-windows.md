---
title: Utiliser des modèles pour les appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des modèles d’administration dans Microsoft Intune afin de créer des groupes de paramètres pour les appareils Windows 10. En définissant ces paramètres dans un profil de configuration d’appareil, vous pouvez contrôler les programmes Office, sécuriser les fonctionnalités dans Internet Explorer, contrôler l’accès à OneDrive, utiliser les fonctionnalités du Bureau à distance, activer la lecture automatique, définir les paramètres de gestion de l’alimentation, utiliser l’impression HTTP, utiliser différentes options d’ouverture de session utilisateur et contrôler la taille du journal des événements.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9309b110d37795f840e10f22b71b06507aea4c62
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373719"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Microsoft Intune

Vous gérez les appareils dans votre organisation et souhaitez créer un groupe des paramètres qui sont appliqués à différents groupes d’appareils. Supposons que vous avez plusieurs groupes d’appareils. Vous souhaitez assigner des ensembles de paramètres distincts au groupe A et au groupe B. Vous voulez également voir rapidement tous les paramètres que vous pouvez configurer.

Vous pouvez effectuer tout cela à l’aide des **modèles d’administration** fournis dans Microsoft Intune. Les modèles d’administration contiennent des centaines de paramètres qui vous permettent de contrôler les fonctionnalités dans Internet Explorer, les programmes Microsoft Office, le Bureau à distance, l’accès à OneDrive, la connexion par mot de passe image ou code PIN, et bien plus encore. Ces modèles sont similaires aux paramètres de stratégie de groupe (GPO) dans Active Directory (AD). Ce sont des [paramètres ADMX sauvegardés](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) (ouverture d’un autre site Docs) qui utilisent XML. Toutefois, les modèles dans Intune sont entièrement basés dans le cloud. Ils offrent un moyen plus simple et rapide de configurer les paramètres et de trouver les paramètres souhaités.

Les **modèles d’administration** sont intégrés à Intune et ne nécessitent aucune personnalisation, y compris l’utilisation d’OMA-URI. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres de modèle comme un moyen centralisé de gérer vos appareils Windows 10.

Cet article présente les étapes de la création d’un modèle pour les appareils Windows 10 et montre comment filtrer tous les paramètres disponibles dans Microsoft Intune. Quand vous créez un modèle, vous créez en même temps un profil de configuration d’appareil. Vous pouvez ensuite assigner ou déployer ce profil sur les appareils Windows 10 dans votre organisation.

## <a name="create-a-template"></a>Créer un modèle

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom pour le profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Modèles d’administration (préversion)** .

4. Sélectionnez **Créer**. Dans la nouvelle fenêtre, sélectionnez **Paramètres**. Vous pouvez voir tous les paramètres listés, et afficher davantage de paramètres à l’aide des flèches Précédent et Suivant :

    ![Voir un exemple de liste de paramètres et utiliser les boutons Précédent et Suivant](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. Sélectionnez l’un des paramètres. Par exemple, sélectionnez **Autoriser les téléchargements de fichiers**. Une description détaillée du paramètre s’affiche. Choisissez **Activer** ou **Désactiver**, ou laissez le paramètre défini sur **Non configuré** (valeur par défaut). La description détaillée explique également ce qui se produit quand vous choisissez l’option **Activer**, **Désactiver** ou **Non configuré**.
6. Cliquez sur **OK** pour enregistrer vos modifications.

Continuez à parcourir la liste des paramètres et configurez les paramètres souhaités dans votre environnement. Voici quelques exemples :

- Utilisez le paramètre **Paramètres de notification de macro VBA** pour gérer les macros VBA dans différents programmes Microsoft Office, comme Word et Excel.
- Utilisez le paramètre **Autoriser les téléchargements de fichiers** pour autoriser ou bloquer les téléchargements à partir d’Internet Explorer.
- Utilisez le paramètre **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (sur secteur)** pour demander aux utilisateurs d’entrer un mot de passe quand les appareils sortent du mode veille.
- Utilisez le paramètre **Télécharger les contrôles ActiveX non signés** pour empêcher les utilisateurs de télécharger des contrôles ActiveX non signés depuis Internet Explorer.
- Utilisez le paramètre **Désactiver la restauration du système** pour autoriser ou empêcher les utilisateurs d’effectuer une restauration du système sur l’appareil.
- Et il y a bien d’autres exemples...

## <a name="find-some-settings"></a>Rechercher des paramètres spécifiques

Les modèles contiennent des centaines de paramètres. Pour trouver plus facilement des paramètres spécifiques, utilisez les fonctionnalités intégrées disponibles :

- Dans votre modèle, sélectionnez la colonne **Paramètres**, **État** ou **Chemin** sur laquelle vous voulez trier la liste de paramètres. Par exemple, sélectionnez la colonne **Chemin** pour afficher tous les paramètres situés dans le chemin `Microsoft Excel` :

  ![Cliquer sur Chemin pour trier par ordre alphabétique](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Dans votre modèle, utilisez la zone **Rechercher** pour trouver des paramètres spécifiques. Par exemple, recherchez `copy`. Tous les paramètres avec `copy` sont affichés :

  ![Cliquer sur Chemin pour trier par ordre alphabétique](./media/administrative-templates-windows/search-copy-settings.png)

  En guide d’autre exemple, recherchez `microsoft word`. Vous voyez alors tous les paramètres que vous pouvez définir pour le programme Microsoft Word. Recherchez `explorer` pour voir tous les paramètres Internet Explorer que vous pouvez ajouter à votre modèle.

Cette fonctionnalité utilise des [fournisseurs de services de configuration de stratégie Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) (ouverture d’un autre site Docs). Les fournisseurs de services de configuration fonctionnent sur les différentes éditions de Windows, telles que les éditions Famille, Professionnel et Entreprise. Pour voir si un fournisseur de services de configuration fonctionne sur une édition spécifique, accédez à [Fournisseurs de services de configuration de stratégie Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) (ouverture d’un autre site Docs).

## <a name="next-steps"></a>Étapes suivantes

Le modèle est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le modèle (également appelé profil)](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).
