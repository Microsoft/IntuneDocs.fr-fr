---
title: Ajout de stratégies de configuration des applications pour les appareils iOS/iPadOS gérés
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser les stratégies de configuration des applications pour fournir des données de configuration à une application iOS/iPadOS quand elle s’exécute.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6044ff5f8d169e36a11f9289f1772c809723b7fc
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77438002"
---
# <a name="add-app-configuration-policies-for-managed-iosipados-devices"></a>Ajout de stratégies de configuration des applications pour les appareils iOS/iPadOS gérés

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilisez des stratégies de configuration des applications dans Microsoft Intune afin de fournir des paramètres de configuration personnalisés pour une application iOS/iPadOS. Ces paramètres de configuration permettent la personnalisation d’une application en fonction des indications des fournisseurs de l’application. Vous devez obtenir ces paramètres de configuration (les clés et les valeurs) auprès du fournisseur de l’application. Pour configurer l’application, vous spécifiez les paramètres sous forme de clés et de valeurs, ou en tant que fichier XML contenant les clés et les valeurs.

En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. Les applications connexes traitent la configuration d’application, suppriment et bloquent les comptes non approuvés. Les paramètres de stratégie de configuration sont utilisés quand l’application les recherche, en général lors de sa première exécution.

Dès que vous ajoutez une stratégie de configuration d’application, vous pouvez définir les affectations de la stratégie de configuration d’application. Quand vous définissez les affectations de la stratégie, vous pouvez choisir d’inclure et d’exclure les groupes d’utilisateurs auxquels la stratégie s’applique. Quand vous choisissez d’inclure un ou plusieurs groupes, vous pouvez choisir de sélectionner des groupes spécifiques à inclure ou sélectionner des groupes intégrés. Les groupes intégrés sont notamment **Tous les utilisateurs**, **Tous les appareils** et **Tous les utilisateurs + Tous les appareils**. 

> [!NOTE]
> Intune fournit des groupes **Tous les utilisateurs** et **Tous les appareils** précréés dans la console avec des optimisations intégrées pour votre commodité. Nous vous recommandons vivement d’utiliser ces groupes pour cibler tous les utilisateurs et tous les appareils au lieu de créer vous-même des groupes « Tous les utilisateurs » ou « Tous les appareils ».

Une fois que vous avez sélectionné les groupes inclus pour votre stratégie de configuration d’application, vous pouvez aussi choisir les groupes spécifiques à exclure. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Ce type de stratégie n’est disponible à l’heure actuelle que pour les appareils possédant la version 8.0 ou une version ultérieure d’iOS/iPadOS. Elle prend en charge les types d’installation d’application suivants :
>
> - **Application iOS gérée à partir de l’App Store**
> - **Package d'application pour iOS**
>
> Pour plus d’informations sur les types d’installation d’application, consultez [Guide pratique pour ajouter une application à Microsoft Intune](apps-add.md). Pour plus d’informations sur l’intégration de la configuration de l’application dans votre package d’application .ipa pour les appareils gérés, consultez Configuration des applications gérées dans la [documentation pour les développeurs iOS](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Créer une stratégie de configuration des applications

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter** > **Applications gérées**. Notez que vous avez le choix entre deux options : **Appareils gérés** et **Applications gérées**. Pour plus d’informations, consultez [Applications qui prennent en charge la configuration d’application](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. Dans la page **De base**, définissez les informations suivantes :
    - **Nom** : nom du profil qui s’affiche dans le portail Azure.
    - **Description** : description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil** : le paramètre est défini sur **Appareils gérés**.
4. Sélectionnez **iOS/iPadOS** comme **Plateforme**.
5. Cliquez sur **Sélectionner l’application** en regard de **Application ciblée**. Le volet **Application associée** s’affiche. 
6. Dans le volet **Application ciblée**, choisissez l'application gérée à associer à la stratégie de configuration, puis cliquez sur **OK**.
7. Cliquez sur **Suivant** pour afficher la page **Paramètres**.
8. Dans le menu déroulant, sélectionnez le **format des paramètres de configuration**. Sélectionnez l’une des méthodes suivantes pour ajouter des informations de configuration :
    - **Utiliser le concepteur de configuration**
    - **Entrer des données XML**<br><br>
    Pour plus d’informations sur l’utilisation du concepteur de configuration, consultez [Utiliser le concepteur de configuration](#use-configuration-designer). Pour plus d’informations sur l’entrée de données XML, consultez [Entrer des données XML](#enter-xml-data). 
9. Cliquez sur **Suivant** pour afficher la page **Affectations**.
10. Dans la liste déroulante en regard de **Affecter à**, sélectionnez soit **Groupes sélectionnés**, **Tous les utilisateurs**, **Tous les appareils**, ou **Tous les utilisateurs et tous les appareils** pour leur affecter la stratégie de configuration de l'application.

    ![Capture d’écran de l’onglet Inclure des affectations de stratégies](./media/app-configuration-policies-use-ios/app-config-policy01.png)

11. Sélectionnez **Tous les utilisateurs** dans la liste déroulante.

    ![Capture d’écran de l’option de liste déroulante Tous les utilisateurs des affectations de stratégies](./media/app-configuration-policies-use-ios/app-config-policy02.png)

12. Cliquez sur **Sélectionner des groupes à exclure** pour afficher le volet correspondant.

    ![Capture d’écran du volet Sélectionner les groupes à exclure des affectations de stratégies](./media/app-configuration-policies-use-ios/app-config-policy03.png)

13. Choisissez les groupes à exclure, puis cliquez sur **Sélectionner**.

    >[!NOTE]
    >Quand vous ajoutez un groupe, si un autre groupe a déjà été inclus pour un type d’affectation donnée, il est présélectionné et ne peut pas être affecté à un autre type d’affectation d’inclusion. Par conséquent, ce groupe déjà utilisé ne peut pas être sélectionné comme groupe à exclure.

14. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**.
15. Cliquez sur **Créer** pour ajouter la stratégie de configuration de l'application à Intune.

## <a name="use-configuration-designer"></a>Utiliser le concepteur de configuration

Microsoft Intune fournit des paramètres de configuration qui sont uniques pour une application. Vous pouvez utiliser le concepteur de configuration pour les applications sur les appareils qui sont inscrits ou non dans Intune. Le concepteur vous permet de configurer des clés et des valeurs de configuration spécifiques qui vous aident à créer le code XML sous-jacent. Vous devez également spécifier le type de données pour chaque valeur. Ces paramètres sont fournis automatiquement aux applications lors de leur installation.

### <a name="add-a-setting"></a>Ajouter un paramètre

1. Pour chaque clé et valeur de la configuration, définissez les éléments suivants :
   - **Clé de configuration** : clé qui identifie de façon univoque la configuration spécifique du paramètre.
   - **Type de valeur** : type de données de la valeur de configuration. Les types incluent Integer, Real, String ou Boolean.
   - **Valeur de configuration** : valeur pour la configuration.
2. Choisissez **OK** pour définir vos paramètres de configuration.

### <a name="delete-a-setting"></a>Supprimer un paramètre

1. Choisissez le bouton de sélection ( **...** ) en regard du paramètre.
2. Sélectionnez **Supprimer**.

Les caractères \{\{ et \}\} sont utilisés uniquement par les types de jetons. Ils ne doivent pas être utilisés à d’autres fins.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Autoriser uniquement les comptes d’organisation configurés dans les applications avec plusieurs identités 

Pour les appareils iOS/iPadOS, utilisez les paires clé/valeur suivantes :

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valeurs** | <ul><li>**Activé** : le seul compte autorisé est le compte utilisateur managé défini par la clé [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Désactivé** (ou toute valeur qui n’est pas une correspondance ne respectant pas la casse de la valeur **Activé**) : n’importe quel compte est autorisé.</li></ul> |.

   > [!NOTE]
   > Vous devez utiliser OneDrive pour iOS 10.34 ou version ultérieure, Outlook pour iOS 2.99.0 ou version ultérieure ou Edge pour iOS 44.8.7 ou version ultérieure et l’application doit être ciblée avec des [stratégies de protection des applications Intune](app-protection-policy.md) lorsque vous autorisez uniquement les comptes d’organisation configurés avec plusieurs identités.

## <a name="enter-xml-data"></a>Entrer des données XML

Vous pouvez taper ou coller une liste de propriétés XML contenant les paramètres de configuration d’application pour les appareils inscrits dans Intune. Le format de la liste de propriétés XML varie en fonction de l’application que vous configurez. Pour plus d’informations sur le format exact à utiliser, contactez le fournisseur de l’application.

Intune valide le format XML. Toutefois, il ne vérifie pas que la liste de propriétés XML (PList) fonctionne avec l’application cible.

Pour en savoir plus sur les listes de propriétés XML :

- Reportez-vous à [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Présentation des listes de propriétés XML) sur le site iOS Developer Library.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Exemple de format de fichier XML de configuration d’application

Quand vous créez un fichier de configuration d’application, vous pouvez spécifier une ou plusieurs des valeurs suivantes à l’aide de ce format :

```xml
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
</dict>
```

### <a name="supported-xml-plist-data-types"></a>Types de données PList XML pris en charge

Intune prend en charge les types de données suivants dans une liste de propriétés :

- &lt;integer&gt;
- &lt;real&gt;
- &lt;string&gt;
- &lt;array&gt;
- &lt;dict&gt;
- &lt;true /&gt; ou &lt;false /&gt;

### <a name="tokens-used-in-the-property-list"></a>Jetons utilisés dans la liste des propriétés

De plus, Intune prend en charge les types de jetons suivants dans la liste de propriétés :
- \{\{userprincipalname\}\} : par exemple **John\@contoso.com**
- \{\{mail\}\} : par exemple **John\@contoso.com**
- \{\{partialupn\}\} : par exemple, **John**
- \{\{accountid\}\} : par exemple, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} : par exemple, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} : par exemple, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} : par exemple, **John Doe**
- \{\{serialnumber\}\} : par exemple, **F4KN99ZUG5V2** (pour les appareils iOS/iPadOS)
- \{\{serialnumberlast4digits\}\} : par exemple, **G5V2** (pour les appareils iOS/iPadOS)
- \{\{aaddeviceid\}\} : par exemple **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>Configuration de l’application Portail d’entreprise pour la prise en charge des appareils DEP iOS

Les inscriptions DEP (programme d’inscription des appareils d’Apple) ne sont pas compatibles avec la version de l’App Store de l’application Portail d’entreprise. Toutefois, vous pouvez configurer l’application Portail d’entreprise de façon à prendre en charge les appareils DEP iOS/iPadOS suivant les étapes ci-dessous.

1. Dans Intune, ajoutez l’application Portail d’entreprise Intune si nécessaire, en accédant à **Intune** > **Applications** > **Toutes les applications** > **Ajouter**.
2. Accédez à **Applications** > **Stratégie de configuration des applications**, pour créer une stratégie de configuration des applications pour l’application Portail d’entreprise.
3. Créez une stratégie de configuration des applications avec le code XML ci-dessous. Pour plus d’informations sur la création d’une stratégie de configuration des applications et la saisie de données XML, consultez [Ajout de stratégies de configuration des applications pour les appareils iOS/iPadOS gérés](app-configuration-policies-use-ios.md).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Déployez le Portail d’entreprise sur les appareils avec la stratégie de configuration des applications ciblée sur les groupes désirés. Veillez à ne déployer la stratégie que sur des groupes d’appareils qui sont déjà inscrits au DEP.
4. Dites aux utilisateurs finaux de se connecter à l’application Portail d’entreprise lorsqu’elle est automatiquement installée.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Suivre l’état de configuration d’applications iOS par appareil 
Une fois une stratégie de configuration affectée, vous pouvez suivre l’état de configuration des applications iOS/iPadOS pour chaque appareil géré. À partir de **Microsoft Intune** dans le portail Azure, sélectionnez **Appareils** > **Tous les appareils**. Dans la liste des appareils gérés, sélectionnez un appareil spécifique pour afficher le volet correspondant. Dans le volet de l’appareil, sélectionnez **Configuration de l’application**.  

## <a name="additional-information"></a>Informations supplémentaires

- [Déploiement des paramètres de configuration des applications Outlook pour iOS/iPadOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Étapes suivantes

Continuez à [affecter](apps-deploy.md) et à [surveiller](apps-monitor.md) l’application.
