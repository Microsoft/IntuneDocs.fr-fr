---
title: Ajouter des stratégies de configuration d’applications pour les appareils iOS gérés | Microsoft Docs
titlesuffix: Microsoft Intune
description: Apprenez à utiliser les stratégies de configuration d’applications pour fournir des données de configuration à une application iOS quand elle est exécutée.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b39afeaf6daf8b08c58becd0b4af07299bd79e7a
ms.sourcegitcommit: ab08dd841f16ae11f958c43b6262a9f6a0cabdd4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101987"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Ajouter des stratégies de configuration d’applications pour les appareils iOS gérés | Microsoft Docs

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilisez des stratégies de configuration des applications dans Microsoft Intune afin de fournir des paramètres de configuration personnalisés pour une application iOS. Ces paramètres de configuration permettent la personnalisation d’une application en fonction des indications des fournisseurs. Vous devez obtenir ces paramètres de configuration (les clés et les valeurs) auprès du fournisseur de l’application. Pour configurer l’application, vous spécifiez les paramètres sous forme de clés et de valeurs, ou en tant que fichier XML contenant les clés et les valeurs. Vous n’affectez pas ces stratégies de configuration directement aux appareils et aux utilisateurs. Au lieu de cela, vous associez une stratégie de configuration à une application, puis vous affectez l’application. Les paramètres de stratégie de configuration sont utilisés quand l’application les recherche, en général lors de sa première exécution.

Dès que vous ajoutez une stratégie de configuration d’application, vous pouvez définir les affectations de la stratégie de configuration d’application. Quand vous définissez les affectations de la stratégie, vous pouvez choisir d’inclure et d’exclure les groupes d’utilisateurs auxquels la stratégie s’applique. Quand vous choisissez d’inclure un ou plusieurs groupes, vous pouvez choisir de sélectionner des groupes spécifiques à inclure ou sélectionner des groupes intégrés. Les groupes intégrés sont notamment **Tous les utilisateurs**, **Tous les appareils** et **Tous les utilisateurs + Tous les appareils**. 

>[!NOTE]
>Intune fournit des groupes **Tous les utilisateurs** et **Tous les appareils** précréés dans la console avec des optimisations intégrées pour votre commodité. Nous vous recommandons vivement d’utiliser ces groupes pour cibler tous les utilisateurs et tous les appareils au lieu de créer vous-même des groupes « Tous les utilisateurs » ou « Tous les appareils ».<p></p>
>En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. Les applications connexes traitent la configuration d’application, suppriment et bloquent les comptes non approuvés.

Une fois que vous avez sélectionné les groupes inclus pour votre stratégie de configuration d’application, vous pouvez aussi choisir les groupes spécifiques à exclure. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Ce type de stratégie est disponible uniquement pour les appareils exécutant iOS 8.0 ou version ultérieure. Elle prend en charge les types d’installation d’application suivants :
>
> -   **Application iOS gérée à partir de l’App Store**
> -   **Package d'application pour iOS**
>
> Pour plus d’informations sur les types d’installation d’application, consultez [Guide pratique pour ajouter une application à Microsoft Intune](apps-add.md).

## <a name="create-an-app-configuration-policy"></a>Créer une stratégie de configuration des applications

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Choisissez la charge de travail **Applications clientes**.
4. Choisissez **Stratégies de configuration des applications** dans le groupe **Gérer**, puis choisissez **Ajouter**.
5. Définissez les détails suivants :
    - **Nom** : nom du profil qui s’affiche dans le portail Azure.
    - **Description** : description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil** : choisissez **Appareils gérés**.
6. Sélectionnez **iOS** comme **Plateforme**.
7.  Choisissez **Application associée**. Ensuite, dans le volet **Application associée**, choisissez l’application gérée à laquelle vous souhaitez appliquer la configuration, puis sélectionnez **OK**.
8.  Dans le volet **Ajouter une stratégie de configuration**, choisissez **Paramètres de configuration**.
9. Sélectionnez **Format des paramètres de configuration**. Sélectionnez une des options suivantes pour ajouter des informations XML :
    - **Utiliser le concepteur de configuration**
    - **Entrer des données XML**<br><br>
    Pour plus d’informations sur l’utilisation du concepteur de configuration, consultez [Utiliser le concepteur de configuration](#use-configuration-designer). Pour plus d’informations sur l’entrée de données XML, consultez [Entrer des données XML](#enter-xml-data). 
10. Après avoir ajouté vos informations XML, choisissez **OK**, puis **Ajouter** pour ajouter la stratégie de configuration. Le volet de vue d’ensemble de la stratégie de configuration s’affiche.
11. Sélectionnez **Affectations** pour afficher les options d’inclusion et d’exclusion. 

    ![Capture d’écran de l’onglet Inclure des affectations de stratégies](./media/app-config-policy01.png)
12. Sélectionnez **Tous les utilisateurs** sous l’onglet **Inclure**.

    ![Capture d’écran de l’option de liste déroulante Tous les utilisateurs des affectations de stratégies](./media/app-config-policy02.png)
13. Sélectionnez l’onglet **Exclure**. 
14. Cliquez sur **Sélectionner des groupes à exclure** pour afficher le volet correspondant.

    ![Capture d’écran du panneau Sélectionner les groupes à exclure des affectations de stratégies](./media/app-config-policy03.png)
15. Choisissez les groupes à exclure, puis cliquez sur **Sélectionner**.

    >[!NOTE]
    >Quand vous ajoutez un groupe, si un autre groupe a déjà été inclus pour un type d’affectation donnée, il est présélectionné et ne peut pas être affecté à un autre type d’affectation d’inclusion. Par conséquent, ce groupe déjà utilisé ne peut pas être sélectionné comme groupe à exclure.
16. Cliquez sur **Save**.

## <a name="use-configuration-designer"></a>Utiliser le concepteur de configuration

Microsoft Intune fournit des paramètres de configuration qui sont uniques pour une application. Vous pouvez utiliser le concepteur de configuration pour les applications sur les appareils qui sont inscrits ou non dans Intune. Le concepteur vous permet de configurer des clés et des valeurs de configuration spécifiques qui vous aident à créer le code XML sous-jacent. Vous devez également spécifier le type de données pour chaque valeur. Ces paramètres sont fournis automatiquement aux applications lors de leur installation.

### <a name="add-a-setting"></a>Ajouter un paramètre

1. Pour chaque clé et valeur de la configuration, définissez les éléments suivants :
   - **Clé de configuration** : clé qui identifie de façon univoque la configuration spécifique du paramètre.
   - **Type de valeur** : type de données de la valeur de configuration. Les types incluent Integer, Real, String ou Boolean.
   - **Valeur de configuration** : valeur pour la configuration.
2. Choisissez **OK** pour définir vos paramètres de configuration.

### <a name="delete-a-setting"></a>Supprimer un paramètre

1. Choisissez le bouton de sélection (**...** ) en regard du paramètre.
2. Sélectionnez **Supprimer**.

Les caractères \{\{ et \}\} sont utilisés uniquement par les types de jetons. Ils ne doivent pas être utilisés à d’autres fins.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Autoriser uniquement les comptes d’organisation configurés dans les applications avec plusieurs identités 

Pour les appareils Android, utilisez les paires clé/valeur suivantes :

| **Key** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valeurs** | <ul><li>**Activé** : le seul compte autorisé est le compte utilisateur managé défini par la clé [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Désactivé** (ou toute valeur qui n’est pas une correspondance ne respectant pas la casse de la valeur **Activé**) : n’importe quel compte est autorisé.</li></ul> |

   > [!NOTE]
   > Vous devez utiliser OneDrive pour iOS 10.34 ou version ultérieure et Outlook pour iOS 2.99.0 ou version ultérieure lorsque vous autorisez uniquement les comptes d’organisation configurés avec plusieurs identités.

## <a name="enter-xml-data"></a>Entrer des données XML

Vous pouvez taper ou coller une liste de propriétés XML contenant les paramètres de configuration d’application pour les appareils inscrits dans Intune. Le format de la liste de propriétés XML varie en fonction de l’application que vous configurez. Pour plus d’informations sur le format exact à utiliser, contactez le fournisseur de l’application.

Intune valide le format XML. Toutefois, il ne vérifie pas que la liste de propriétés XML (PList) fonctionne avec l’application cible.

Pour en savoir plus sur les listes de propriétés XML :

  -  Consultez [Configurer des applications iOS avec des stratégies de configuration d’applications mobiles dans Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -  Reportez-vous à [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Présentation des listes de propriétés XML) sur le site iOS Developer Library.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Exemple de format de fichier XML de configuration d’application

Quand vous créez un fichier de configuration d’application, vous pouvez spécifier une ou plusieurs des valeurs suivantes à l’aide de ce format :

```
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
- \{\{userprincipalname\}\} : par exemple, **John@contoso.com**
- \{\{mail\}\} : par exemple, **John@contoso.com**
- \{\{partialupn\}\} : par exemple, **John**
- \{\{accountid\}\} : par exemple, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} : par exemple, **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} : par exemple, **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} : par exemple, **John Doe**
- \{\{serialnumber\}\} : par exemple, **F4KN99ZUG5V2** (pour les appareils iOS)
- \{\{serialnumberlast4digits\}\} : par exemple, **G5V2** (pour les appareils iOS)
- \{\{aaddeviceid\}\} : par exemple **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="monitor-ios--app-configuration-status-per-device"></a>Suivre l’état de configuration d’applications iOS par appareil 
Une fois qu’une stratégie de configuration a été affectée, vous pouvez suivre l’état de configuration d’applications iOS pour chaque appareil géré. À partir de **Microsoft Intune** dans le portail Azure, sélectionnez **Appareils** > **Tous les appareils**. Dans la liste des appareils gérés, sélectionnez un appareil spécifique pour afficher le panneau correspondant. Dans le panneau de l’appareil, sélectionnez **Configuration de l’application**.  

## <a name="next-steps"></a>Étapes suivantes

Continuez à [affecter](apps-deploy.md) et à [surveiller](apps-monitor.md) l’application.
