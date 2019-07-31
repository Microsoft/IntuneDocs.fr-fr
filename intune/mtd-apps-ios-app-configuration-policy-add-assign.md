---
title: Ajouter et affecter des applications MTD à Microsoft Intune
titleSuffix: Microsoft Intune
description: Utiliser Intune pour ajouter des applications MTD (Mobile Threat Defense), l’application Microsoft Authenticator et une stratégie de configuration iOS dans le portail Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fef4b6969680101e2e4f045bc83a8974536eaf2a
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660969"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Ajouter et affecter des applications Mobile Threat Defense (MTD) avec Intune  

> [!NOTE] 
> Cet article s’applique à tous les partenaires Mobile Threat Defense.

Vous pouvez utiliser Intune pour ajouter et déployer des applications MTD (Mobile Threat Defense) afin que les utilisateurs finaux puissent recevoir des notifications quand une menace est identifiée sur leurs appareils mobiles et recevoir des conseils pour contrer les menaces.

## <a name="before-you-begin"></a>Avant de commencer    
Les étapes ci-dessous doivent être effectuées dans le [portail Azure](https://portal.azure.com/). Vérifiez que vous êtes familiarisé avec ce processus :

- [Ajout d’une application dans Intune](apps-add.md).
- [Ajout d’une stratégie de configuration d’applications iOS dans Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
- [Affectation d’une application avec Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

> [!TIP]
> Le Portail d’entreprise Intune fonctionne en tant que service broker sur les appareils Android, pour que l’identité des utilisateurs puisse être vérifiée par Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Configurer Microsoft Authenticator pour iOS  
Pour les appareils iOS, vous avez besoin de [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) pour que l’identité des utilisateurs puisse être vérifiée par Azure AD. Vous avez aussi besoin d’une stratégie de configuration d’application iOS qui configure l’application iOS MTD que vous utilisez avec Intune.

Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL du magasin de l’application ;icrosoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) à **l’étape 12** dans la section **Configurer les informations sur l’application**.

## <a name="configure-mtd-applications"></a>Configurer les applications MTD  
Choisissez la section correspondant à votre fournisseur MTD :

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Configurer les applications Lookout for Work  
- **Android**  
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez cette [URL d’App Store Google Lookout for work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) à **l’étape 7**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store Lookout for Work iOS](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) à l’**étape 11** pour l’**URL de l’App Store**.

- **Application Lookout for Work en dehors de l’Apple Store**  
  - Vous devez resigner l’application iOS Lookout for Work. Lookout distribue son application iOS Lookout for Work en dehors de l’App Store iOS. Avant de distribuer l’application, vous devez resigner l’application avec votre certificat de développeur d’entreprise iOS.  
  - Pour obtenir des instructions détaillées pour resigner des applications iOS Lookout for Work, consultez [Lookout for Work iOS app re-signing process](https://personal.support.lookout.com/hc/articles/114094038714) (Processus pour resigner des applications iOS Lookout for Work) sur le site web de Lookout.

  - **Activez l’authentification Azure AD pour les utilisateurs d’applications iOS Lookout for Work.**

    1. Accédez au [portail Azure](https://portal.azure.com), connectez-vous avec vos informations d’identification, puis accédez à la page d’application.

    2. Ajoutez l’**application iOS Lookout for Work**  comme **application cliente native**.

    3. Remplacez **com.lookout.enterprise.nom_de_votre_entreprise** par l’ID d’ensemble client que vous avez sélectionné quand vous avez signé le package IPA.

    4. Ajouter un URI de redirection supplémentaire : **&lt;companyportal://code/>** suivi d’une version encodée URL de votre URI de redirection d’origine.

    5. Ajoutez **Autorisations déléguées** à votre application.

    > [!NOTE] 
    > Pour plus d’informations, consultez [Configurer une application cliente native avec Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

  - **Ajoutez le fichier ipa Lookout for Work.**

    - Chargez le fichier .ipa resigné comme décrit dans l’article [Ajouter des applications métier iOS avec Intune](lob-apps-ios.md). Vous devez aussi définir la version de système d’exploitation minimale sur iOS version 8.0 ou ultérieure.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Configurer les applications Symantec Endpoint Protection Mobile (SEP Mobile)  
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). À l’**étape 7**, utilisez cette [URL du magasin de l’application SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Pour **système d’exploitation Minimum**, sélectionnez **Android 4.0 (Ice Cream Sandwich)** .

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store SEP Mobile](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) à l’**étape 11** pour l’**URL de l’App Store**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Configurer les applications Check Point SandBlast Mobile  
- **Android**  
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez l’[URL du magasin de l’application Check Point SandBlast Mobile](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) à l’**étape 7**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store Check Point SandBlast Mobile](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) à l’**étape 11** pour l’**URL de l’App Store**.  

### <a name="configure-zimperium-apps"></a>Configurer les applications Zimperium  
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez cette [URL d’App Store Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) à **l’étape 7**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) à l’**étape 11** pour l’**URL de l’App Store**.  
 
### <a name="configure-pradeo-apps"></a>Configurer des applications Pradeo  
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez cette [URL de l’App Store Pradeo](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) à **l’étape 7**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store Pradeo](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) à l’**étape 11** pour l’**URL de l’App Store**.

### <a name="configure-better-mobile-apps"></a>Configurer des applications Better Mobile  
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez cette [URL du magasin d’application Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) à **l’étape 7**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store ActiveShield](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) à l’**étape 11** pour l’**URL de l’App Store**.

### <a name="configure-sophos-apps"></a>Configurer des applications Sophos  
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez cette [URL d’App Store Sophos](https://play.google.com/store/apps/details?id=com.sophos.smsec) à l’**étape 7**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](store-apps-ios.md). Utilisez cette [URL d’App Store ActiveShield](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) à l’**étape 11** pour l’**URL de l’App Store**.

### <a name="configure-wandera-apps"></a>Configurer des applications Wandera  
 
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](store-apps-android.md). Utilisez cette [URL d’App Store Wandera Mobile](https://play.google.com/store/apps/details?id=com.wandera.android) à l’**étape 7**. Pour **Système d’exploitation minimal**, sélectionnez **Android 5.0**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](https://docs.microsoft.com/intune/store-apps-ios). Utilisez cette [URL d’App Store Wandera Mobile](https://itunes.apple.com/app/wandera/id605469330) à l’**étape 11** pour l’**URL de l’App Store**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Configurer vos applications MTD avec une stratégie de configuration des applications iOS  

### <a name="lookout-for-work-app-configuration-policy"></a>Stratégie de configuration des applications Lookout for Work  
- Créez la stratégie de configuration d’application iOS comme décrit dans l’article [Utilisation de la stratégie de configuration d’application iOS](app-configuration-policies-use-ios.md).

### <a name="sep-mobile-app-configuration-policy"></a>Stratégie de configuration des applications mobiles SEP  
- Utilisez le même compte Azure AD configuré précédemment dans la [console de gestion Symantec Endpoint Protection](https://aad.skycure.com), qui doit être le même compte que celui utilisé pour vous connecter au portail classique Intune.

- **Téléchargez** le fichier de la stratégie de configuration d’applications iOS : 
  - Accédez à la [console de gestion Symantec Endpoint Protection](https://aad.skycure.com) et connectez-vous avec vos informations d’identification d’administrateur.

  - Accédez à **Paramètres**et, sous **intégrations**, choisissez **Intune**. Choisissez **Sélection d’intégration EMM**. Choisissez **Microsoft**, puis enregistrez votre sélection.

  - Cliquez sur le lien **Fichiers d’installation de l’intégration** et enregistrez le fichier \*.zip généré. Le fichier .zip contient le fichier * **.plist** qui sera utilisé pour créer la stratégie de configuration des applications iOS dans Intune.

  - Consultez les instructions [d’utilisation de stratégies de configuration d’application Microsoft Intune pour iOS](app-configuration-policies-use-ios.md) pour ajouter la stratégie de configuration d’application SEP Mobile iOS.

  - À l’**étape 8**, utilisez l’option **Entrer des données XML**, copiez le contenu à partir du fichier * **.plist** et collez son contenu dans le corps de la stratégie de configuration.

> [!NOTE]  
> Si vous ne parvenez pas à récupérer les fichiers, contactez [Support d’entreprise Symantec Endpoint Protection Mobile](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Stratégie de configuration des applications Check Point SandBlast Mobile  
- Consultez les instructions [d’utilisation de stratégies de configuration d’application Microsoft Intune pour iOS](app-configuration-policies-use-ios.md) pour ajouter la stratégie de configuration d’application iOS Check Point SandBlast Mobile.
  - À l’**étape 8**, utilisez l’option **Entrer des données XML**, copiez le contenu ci-dessous et collez-le dans le corps de la stratégie de configuration.

        <dict><key>MDM</key><string>INTUNE</string></dict>


### <a name="zimperium-app-configuration-policy"></a>Stratégie de configuration des applications Zimperium  
- Consultez les instructions [d’utilisation de stratégies de configuration d’application Microsoft Intune pour iOS](app-configuration-policies-use-ios.md) pour ajouter la stratégie de configuration d’application iOS Zimperium.
  - À l’**étape 8**, utilisez l’option **Entrer des données XML**, copiez le contenu ci-dessous et collez-le dans le corps de la stratégie de configuration.
 
        <dict>
        <key>provider</key><string>Intune</string>
        <key>userprincipalname</key><string>{{userprincipalname}}</string>
        <key>deviceid</key>
        <string>{{deviceid}}</string>
        <key>serialnumber</key>
        <string>{{serialnumber}}</string>
        <key>udidlast4digits</key>
        <string>{{udidlast4digits}}</string>
        </dict>

### <a name="pradeo-app-configuration-policy"></a>Stratégies de configuration des applications Pradeo  
Pradeo ne prend en charge la stratégie de configuration des applications sur iOS.  Au lieu de cela, pour obtenir une application configurée, collaborez avec Pradeo pour implémenter des fichiers IPA ou APK personnalisés qui sont préconfigurées avec les paramètres souhaités.

### <a name="better-mobile-app-configuration-policy"></a>Stratégie de configuration des applications Better Mobile  
- Consultez les instructions [d’utilisation de stratégies de configuration d’application Microsoft Intune pour iOS](app-configuration-policies-use-ios.md) pour ajouter la stratégie de configuration d’application iOS Better Mobile.
  - À l’**étape 8**, utilisez l’option **Entrer des données XML**, copiez le contenu ci-dessous et collez-le dans le corps de la stratégie de configuration. Remplacez l’URL `https://client.bmobi.net` par l’URL de la console concernée.

        <dict>
        <key>better_server_url</key>
        <string>https://client.bmobi.net</string>
        <key>better_udid</key>
        <string>{{aaddeviceid}}</string>
        <key>better_user</key>
        <string>{{userprincipalname}}</string>
        </dict>


### <a name="sophos-mobile-app-configuration-policy"></a>Stratégie de configuration des applications Sophos Mobile  
Créez la stratégie de configuration d’application iOS comme décrit dans l’article [Utilisation de la stratégie de configuration d’application iOS](app-configuration-policies-use-ios.md).

### <a name="wandera-app-configuration-policy"></a>Stratégie de configuration des applications Wandera  
Pour ajouter la stratégie de configuration des applications iOS Wandera, consultez les instructions concernant l’[utilisation de stratégies de configuration d’applications Microsoft Intune pour iOS](app-configuration-policies-use-ios.md).
- À l’**étape 8**, utilisez l’option **Entrer des données XML**. Connectez-vous au portail Wandera RADAR, puis accédez à **Settings** > **EMM Integration** > **App Push** (Paramètres/Intégration EMM/Envoyer l’application). Sélectionnez **Intune**, puis copiez le contenu ci-dessous et collez-le dans le corps de la stratégie de configuration.  

      <dict><key>secretKey</key>
       <string>SeeRADAR</string>
       <key>apiKey</key>
       <string> SeeRADAR </string>
       <key>customerId</key>
       <string> SeeRADAR </string>
       <key>email</key>
       <string>{{mail}}</string>
       <key>firstName</key>
       <string>{{username}}</string>
       <key>lastName</key>
       <string></string>
       <key>activationType</key>
       <string>PROVISION_THEN_AWP</string></dict>  

## <a name="assign-apps-to-groups"></a>Affecter des applications à des groupes  
- Cette étape s’applique à tous les partenaires MTD. Consultez les instructions relatives à [l’affectation des applications à des groupes avec Intune](apps-deploy.md).

## <a name="next-steps"></a>Étapes suivantes  
- [Configurer la stratégie de conformité des appareils pour MTD](mtd-device-compliance-policy-create.md)
