---
title: Ajouter des stratégies de configuration d’applications pour les appareils Android Entreprise gérés
titleSuffix: Microsoft Intune
description: Utilisez des stratégies de configuration des applications dans Microsoft Intune pour fournir des paramètres quand les utilisateurs exécutent une application Google Play gérée.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 52c8d10f0b8d06d68d75450c3d708f910bc5ddd4
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415041"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Ajouter des stratégies de configuration d’applications pour les appareils Android Entreprise gérés

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Les stratégies de configuration des applications dans Microsoft Intune fournissent des paramètres aux applications Google Play gérées sur les appareils Android Entreprise gérés. Le développeur de l’application expose les paramètres de configuration des applications gérées par Android. Intune utilise ces paramètres exposés pour permettre à l’administrateur de configurer les fonctionnalités de l’application. La stratégie de configuration des applications est attribuée à vos groupes d’utilisateurs. Les paramètres de stratégie sont utilisés quand l’application les vérifie, en général, à sa première exécution.

> [!NOTE]  
> Toutes les applications ne prennent pas en charge la configuration d’application. Vérifiez auprès du développeur d’application si son application prend en charge les stratégies de configuration des applications.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter** > **Applications gérées**. Notez que vous avez le choix entre deux options : **Appareils gérés** et **Applications gérées**. Pour plus d’informations, consultez [Applications qui prennent en charge la configuration d’application](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. Dans la page **De base**, définissez les informations suivantes :
    - **Nom** : nom du profil qui s’affiche dans le portail Azure.
    - **Description** : description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil** : le paramètre est défini sur **Appareils gérés**.
4. Sélectionnez **Android Enterprise** comme **plateforme**.
5. Cliquez sur **Sélectionner l’application** en regard de **Application ciblée**. Le volet **Application associée** s’affiche. 
6. Dans le volet **Application associée**, choisissez l'application gérée à associer à la stratégie de configuration, puis cliquez sur **OK**.
7. Cliquez sur **Suivant** pour afficher la page **Paramètres**.
8. Cliquez sur **Ajouter** pour afficher le volet **Ajouter des autorisations**.
9. Cliquez sur les autorisations que vous souhaitez remplacer. Les autorisations accordées remplacent la stratégie « Autorisations des applications par défaut » pour les applications sélectionnées.
10. Définissez l’**état d’autorisation** pour chaque autorisation. Vous pouvez choisir entre les options **Demander**, **Accorder automatiquement** ou **Refuser automatiquement**. Pour plus d’informations sur les autorisations, consultez [Paramètres Android Entreprise pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune](~/protect/compliance-policy-create-android-for-work.md).
11. Dans le menu déroulant, sélectionnez le **format des paramètres de configuration**. Sélectionnez l’une des méthodes suivantes pour ajouter des informations de configuration :
    - **Utiliser le concepteur de configuration**
    - **Entrer des données JSON**<br><br>
    Pour plus d’informations sur l’utilisation du concepteur de configuration, consultez [Utiliser le concepteur de configuration](#use-the-configuration-designer). Pour plus d’informations sur l’entrée de données XML, consultez [Entrer des données JSON](#enter-json-data). 
12. Cliquez sur **Suivant** pour afficher la page **Affectations**.
13. Dans la liste déroulante en regard de **Affecter à**, sélectionnez soit **Groupes sélectionnés**, **Tous les utilisateurs**, **Tous les appareils**, ou **Tous les utilisateurs et tous les appareils** pour leur affecter la stratégie de configuration de l'application.

    ![Capture d’écran de l’onglet Inclure des affectations de stratégies](./media/app-configuration-policies-use-ios/app-config-policy01.png)

14. Sélectionnez **Tous les utilisateurs** dans la liste déroulante.

    ![Capture d’écran de l’option de liste déroulante Tous les utilisateurs des affectations de stratégies](./media/app-configuration-policies-use-ios/app-config-policy02.png)

15. Cliquez sur **Sélectionner des groupes à exclure** pour afficher le volet correspondant.

    ![Capture d’écran du volet Sélectionner les groupes à exclure des affectations de stratégies](./media/app-configuration-policies-use-ios/app-config-policy03.png)

16. Choisissez les groupes à exclure, puis cliquez sur **Sélectionner**.

    >[!NOTE]
    >Quand vous ajoutez un groupe, si un autre groupe a déjà été inclus pour un type d’affectation donnée, il est présélectionné et ne peut pas être affecté à un autre type d’affectation d’inclusion. Par conséquent, ce groupe déjà utilisé ne peut pas être sélectionné comme groupe à exclure.

17. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**.
18. Cliquez sur **Créer** pour ajouter la stratégie de configuration de l'application à Intune.

## <a name="use-the-configuration-designer"></a>Utiliser le concepteur de configuration

Vous pouvez utiliser le concepteur de configuration pour les applications Google Play gérées lorsque l’application a été conçue pour prendre en charge les paramètres de configuration. La configuration s’applique aux appareils inscrits dans Intune. Le concepteur vous permet de configurer des valeurs de configuration spécifiques pour les paramètres exposés par l’application.

1. Sélectionnez **Ajouter**. Choisissez la liste de paramètres de configuration que vous souhaitez entrer pour l’application.

    Si vous utilisez GMail ou Nine Work pour votre application de messagerie, consultez [Paramètres d’appareil Android Entreprise pour configurer la messagerie](../email-settings-android-enterprise.md) pour plus d’informations sur ces paramètres.

2. Pour chaque clé et valeur de la configuration, définissez les éléments suivants :

    - **Type de valeur** : Type de données de la valeur de configuration. Pour les types de valeur String, vous pouvez éventuellement choisir un profil de certificat ou une variable comme type de valeur.
    - **Valeur de configuration** : Valeur de la configuration. Si vous sélectionnez une variable ou un certificat pour **Type de valeur**, vous pouvez choisir parmi une liste de variables ou de profils de certificat. Si vous choisissez un certificat, l’alias de certificat du certificat déployé sur l’appareil est renseigné lors de l’exécution.

### <a name="supported-variables-for-configuration-values"></a>Variables prises en charge pour les valeurs de configuration

Vous pouvez choisir les options suivantes si vous choisissez une variable comme type de valeur :

| Option | Exemple |
|----|----|
| ID d’appareil AAD | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| ID de compte | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID d’appareil Intune | b9841cd9-9843-405f-be28-b2265c59ef97 |
| Domaine | contoso.com |
| Mail | john@contoso.com |
| UPN partiel | john |
| ID utilisateur | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Nom d'utilisateur | John Doe |
| Nom d'utilisateur principal | john@contoso.com |


### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Autoriser uniquement les comptes d’organisation configurés dans les applications avec plusieurs identités 

Pour les appareils Android, utilisez les paires clé/valeur suivantes :

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Valeurs** | <ul><li>Un ou plusieurs UPN <code>;</code> délimités.</li><li>Le ou les seuls comptes autorisés sont le ou les comptes utilisateur managés définis par cette clé.</li><li> Pour les appareils inscrits à Intune, le jeton <code>{{userprincipalname}}</code> peut être utilisé pour représenter le compte utilisateur inscrit.</li></ul> |

   > [!NOTE]
   > Vous devez utiliser Outlook pour Android 2.2.222 et versions ultérieures, Word, Excel, PowerPoint pour Android 16.0.9327.1000 et versions ultérieures ou OneDrive pour Android 5.28 et versions ultérieures en autorisant uniquement les comptes d’organisation configurés avec la prise en charge plusieurs identités.<p></p>
   > En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. Les applications connexes traitent la configuration d’application, suppriment et bloquent les comptes non approuvés.<p></p>

## <a name="enter-json-data"></a>Entrer des données JSON

Certains paramètres de configuration des applications (comme celles avec des types Bundle) ne peuvent pas être configurés avec le concepteur de configuration. Utilisez l’éditeur JSON pour ces valeurs. Les paramètres sont automatiquement fournis aux applications lors de leur installation.

1. Pour **Format des paramètres de configuration**, sélectionnez **Saisir dans l’éditeur JSON**.
2. Dans l’éditeur, vous pouvez définir des valeurs JSON pour les paramètres de configuration. Vous pouvez choisir **Télécharger un modèle JSON** pour télécharger un exemple de fichier que vous pouvez ensuite configurer.
3. Choisissez **OK**, puis **Ajouter**.

La stratégie est créée et apparaît dans la liste.

Quand l’application affectée est exécutée sur un appareil, elle s’exécute avec les paramètres que vous avez configurés dans la stratégie de configuration des applications.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Préconfigurer l’état d’octroi d’autorisations pour les applications

Vous pouvez également préconfigurer l’autorisation pour les applications d’accéder aux fonctionnalités des appareils Android. Par défaut, les applications Android qui nécessitent des autorisations d’appareils (telles que l’accès à la géolocalisation ou à l’appareil photo) invitent les utilisateurs à accepter ou à refuser les autorisations.

Par exemple, une application utilise le microphone de l’appareil. L’utilisateur est invité à accorder à l’application l’autorisation d’utiliser le microphone.

1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Applications** > **Stratégies de configuration des applications** >  **Ajouter** > **Appareils gérés**.
2. Ajouter les propriétés suivantes :

    - **Nom** : Attribuez un nom descriptif à la stratégie. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, un bon nom de stratégie est **Stratégie de l’application de demande d’autorisations Android Enterprise pour toute l’entreprise**.
    - **Description**. Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Type d’inscription de l’appareil** : Ce paramètre est défini sur **Appareils gérés**.
    - **Plateforme** : Sélectionnez **Android**.

3. Sélectionnez **Application associée**. Choisissez l’application pour laquelle vous souhaitez définir une stratégie de configuration. Sélectionnez-la dans la liste d’applications avec profil professionnel Android que vous avez approuvées et synchronisées avec Intune.
4. Sélectionnez **Autorisations** > **Ajouter**. Dans la liste, sélectionnez les autorisations d’application disponibles > **OK**.
5. Sélectionnez une option pour chaque autorisation à accorder avec cette stratégie :
    - **Demander**. Inviter l’utilisateur à accepter ou à refuser
    - **Accorder automatiquement**. Approuver automatiquement sans avertir l’utilisateur.
    - **Refuser automatiquement**. Refuser automatiquement sans avertir l’utilisateur.
6. Pour affecter la stratégie de configuration d’application, sélectionnez la stratégie de configuration d’application > **Attribution** > **Sélectionner des groupes**. Choisissez les groupes d’utilisateurs à attribuer > **Sélectionner**.
7. Choisissez **Enregistrer** pour affecter la stratégie.

## <a name="additional-information"></a>Informations supplémentaires

- [Attribution d’une application Google Play gérée à des appareils Android Entreprise](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Déploiement des paramètres de configuration des applications Outlook pour iOS/iPadOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Étapes suivantes

Continuez à [affecter](apps-deploy.md) et à [surveiller](apps-monitor.md) l’application.
