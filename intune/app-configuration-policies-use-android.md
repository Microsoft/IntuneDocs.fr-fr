---
title: Ajouter des stratégies de configuration d’applications pour les appareils Android gérés
titlesuffix: Microsoft Intune
description: Utilisez des stratégies de configuration des applications dans Microsoft Intune pour fournir des paramètres quand les utilisateurs exécutent une application avec profil professionnel Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: db6aed3d87b8a8df55c5c95e52eb3dd9ccc690a7
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386965"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Ajouter des stratégies de configuration d’applications pour les appareils Android gérés

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilisez des stratégies de configuration des applications dans Microsoft Intune pour fournir des paramètres aux applications avec profil professionnel Android. Le développeur d’applications doit exposer les paramètres de configuration d’application gérés Android pour spécifier les paramètres de configuration de l’application. Affectez la stratégie de configuration d’applications au groupe d’utilisateurs pour lequel vous souhaitez appliquer les paramètres.  Les paramètres de stratégie sont utilisés quand l’application les vérifie, en général, à sa première exécution.

> [!Note]  
> Toutes les applications ne prennent pas en charge la configuration d’application. Vérifiez auprès du développeur d’application si son application a été conçue pour prendre en charge les stratégies de configuration des applications.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Choisissez la charge de travail **Applications clientes**.
4. Choisissez **Stratégies de configuration des applications** dans le groupe **Gérer**, puis choisissez **Ajouter**.
5. Définissez les détails suivants :
    - **Nom** : nom du profil qui s’affiche dans le portail Azure.
    - **Description** : description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil** : choisissez **Appareils gérés**.
6. Sélectionnez **Android** comme **Plateforme**.
7. Sélectionnez **Application associée** pour choisir l’application pour laquelle vous souhaitez définir une stratégie de configuration d’applications. Sélectionnez-la dans la liste d’applications avec profil professionnel Android que vous avez approuvées et synchronisées avec Intune.
8. Sélectionnez **Autorisations**. Vous pouvez définir des configurations à l’aide de :
    - [Concepteur de configuration](#Use-the-configuration-designer)
    - [Éditeur JSON](#Enter-the-JSON-editor)
9. Choisissez **OK**, puis **Ajouter**.

## <a name="use-the-configuration-designer"></a>Utiliser le concepteur de configuration

Vous pouvez utiliser le concepteur de configuration pour les applications Android qui prennent en charge la configuration. La configuration s’appliquera aux appareils qui sont inscrits dans Intune. Le concepteur vous permet de configurer des valeurs de configuration spécifiques pour les paramètres qu’une application expose.

Sélectionnez **Ajouter** pour sélectionner la liste de paramètres de configuration que vous souhaitez spécifier pour l’application.  
Pour chaque clé et valeur de la configuration, définissez les éléments suivants :

  - **Type de valeur**  
    Type de données de la valeur de configuration. Pour les types de valeur String, vous pouvez éventuellement choisir un profil de certificat ou une variable comme type de valeur.
  - **Valeur de configuration**  
    Valeur de la configuration. Si vous sélectionnez une variable ou un certificat pour le type de valeur, vous pouvez choisir parmi une liste de variables ou de profils de certificat dans la liste déroulante des valeurs de configuration.  Si vous choisissez un certificat, l’alias de certificat du certificat déployé sur l’appareil est renseigné lors de l’exécution.
    
### <a name="supported-variables-for-configuration-values"></a>Variables prises en charge pour les valeurs de configuration

Vous pouvez choisir les options suivantes si vous choisissez une variable comme type de valeur :

| Option | Exemple |
|----|----|
| Mail | john@contoso.com |
| Nom d'utilisateur principal | john@contoso.com |
| UPN partiel | john |
| Domaine | contoso.com |
| Nom d’utilisateur | John Doe |
| ID de compte | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID utilisateur | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| ID Périphérique | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Autoriser uniquement les comptes d’organisation configurés dans les applications avec plusieurs identités 

Pour les appareils Android, utilisez les paires clé/valeur suivantes :

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valeurs** | <ul><li>Un ou plusieurs UPN <code>;</code> délimités.</li><li>Le ou les seuls comptes autorisés sont le ou les comptes utilisateur managés définis par cette clé.</li><li> Pour les appareils inscrits à Intune, le jeton <code>{{userprincipalname}}</code> peut être utilisé pour représenter le compte utilisateur inscrit.</li></ul> |

   > [!NOTE]
   > Vous devez utiliser Outlook pour Android 2.2.222 ou version ultérieure lorsque vous autorisez uniquement les comptes d’organisation configurés avec plusieurs identités.<p></p>
   > En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. Les applications connexes traitent la configuration d’application, suppriment et bloquent les comptes non approuvés.<p></p>
   > Pour Microsoft Word, Microsoft Excel, Microsoft PowerPoint, vous devez utiliser l’application version 16.0.9327.1000 et versions ultérieures. 

## <a name="enter-the-json-editor"></a>Utiliser l’éditeur JSON

Certains paramètres de configuration des applications (comme celles avec des types Bundle) ne peuvent pas être configurés avec le concepteur de configuration. Vous devez utiliser l’éditeur JSON pour ces valeurs. Les paramètres sont automatiquement fournis aux applications lors de leur installation.

1. Pour **Format des paramètres de configuration**, sélectionnez **Saisir dans l’éditeur JSON**.
2. Dans l’éditeur, vous pouvez définir des valeurs JSON pour les paramètres de configuration. Vous pouvez choisir **Télécharger un modèle JSON** pour télécharger un exemple de fichier que vous pouvez ensuite configurer.
3. Choisissez **OK**, puis **Ajouter**.

La stratégie est créée et s’affiche dans le panneau de liste des stratégies.

Quand l’application affectée est exécutée sur un appareil, elle s’exécute avec les paramètres que vous avez configurés dans la stratégie de configuration des applications.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Préconfigurer l’état d’octroi d’autorisations pour les applications

Vous pouvez également préconfigurer l’autorisation pour les applications d’accéder aux fonctionnalités des appareils Android. Par défaut, les applications Android qui nécessitent des autorisations d’appareils (telles que l’accès à la géolocalisation ou à l’appareil photo) invitent les utilisateurs à accepter ou à refuser les autorisations. Par exemple, si une application utilise le microphone de l’appareil, l’utilisateur final est invité à autoriser l’application à utiliser le microphone.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Choisissez **Applications clientes**.
3. Sous **Gérer**, choisissez **Stratégies de configuration des applications**, puis **Ajouter**.
4. Définissez les détails suivants :
    - **Nom**. Nom du profil qui s’affiche dans le portail Azure.
    - **Description**. Description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil**. Sélectionnez **Appareils gérés**.
    - **Plateforme**. Sélectionnez **Android**.
5. Sélectionnez **Application associée** pour choisir l’application pour laquelle vous souhaitez définir une stratégie de configuration. Sélectionnez-la dans la liste d’applications avec profil professionnel Android que vous avez approuvées et synchronisées avec Intune.
6. Sélectionnez **Autorisations**, puis **Ajouter**.
7. Effectuez votre sélection dans la liste des autorisations d’application disponibles, puis choisissez **OK**.
8. Sélectionnez une option pour chaque autorisation à accorder avec cette stratégie :
    - **Demander**. Inviter l’utilisateur à accepter ou à refuser
    - **Accorder automatiquement**. Approuver automatiquement sans avertir l’utilisateur.
    - **Refuser automatiquement**. Refuser automatiquement sans avertir l’utilisateur.
9. Pour affecter la stratégie de configuration d’application, sélectionnez la stratégie de configuration d’application, sélectionnez **Affectation**, puis choisissez **Sélectionner des groupes**.
10. Sélectionnez les groupes d’utilisateurs à affecter, puis choisissez **Sélectionner**.
11. Choisissez **Enregistrer** pour affecter la stratégie.

## <a name="next-steps"></a>Étapes suivantes

Continuez à [affecter](apps-deploy.md) et à [surveiller](apps-monitor.md) l’application.

