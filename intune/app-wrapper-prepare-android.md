---
title: Inclure des applications Android dans un wrapper avec l’outil de création de package de restrictions d’application Intune
description: Découvrez comment inclure une application iOS dans un wrapper sans changer son code. Préparez les applications afin d’appliquer des stratégies de gestion des applications mobiles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: e9d3b82fb544b1c73671438440b108573343795a
ms.sourcegitcommit: 874d9a00cc4666920069d54f99c6c2e687fa34a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53324903"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Préparer des applications Android pour les stratégies de protection des applications avec l’outil de création de package de restrictions d’application Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Utilisez l’outil de création de package de restrictions d’application Microsoft Intune pour Android pour changer le comportement de vos applications Android internes en limitant les fonctionnalités de l’application sans modifier le code de l’application proprement dit.

L’outil est une application en ligne de commande Windows qui s’exécute dans PowerShell et crée un wrapper autour de votre application Android. Une fois l’application encapsulée, vous pouvez modifier sa fonctionnalité en configurant des [stratégies de gestion des applications mobiles](app-protection-policies.md) dans Intune.


Avant d’exécuter l’outil, passez en revue les [considérations en matière de sécurité pour l’exécution de l’outil de création de package de restrictions d’application](#security-considerations-for-running-the-app-wrapping-tool). Pour télécharger l’outil, accédez à la page [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) (Outil de création de package de restrictions d’application Microsoft Intune pour Android) sur GitHub.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Remplir les prérequis pour l’utilisation de l’outil de création de package de restrictions d’application

-   Vous devez exécuter l’outil de création de package de restrictions d’application sur un ordinateur Windows exécutant Windows 7 ou version ultérieure.

-   Votre application d’entrée doit être un package d’application Android valide avec l’extension de fichier .apk et :

    -   elle ne doit pas être chiffrée ;
    -   elle ne doit pas avoir déjà été encapsulée par l’outil de création de package de restrictions d’application Intune ;
    -   elle doit être écrite pour Android 4.0 ou version ultérieure.

-   L’application doit être développée par ou pour votre entreprise. Vous ne pouvez pas utiliser cet outil sur des applications téléchargées à partir de Google Play Store.

-   Pour exécuter l’outil de création de package de restrictions d’application, vous devez installer la dernière version de [Java Runtime Environment](https://java.com/download/) et vous assurer que la variable de chemin d’accès de Java a pour valeur C:\ProgramData\Oracle\Java\javapath dans vos variables d’environnement Windows. Pour plus d’informations, consultez la [documentation Java](https://java.com/download/help/).

    > [!NOTE]
    > Dans certains cas, la version 32 bits de Java peut occasionner des problèmes de mémoire. Nous vous conseillons d’installer la version 64 bits.

- Android nécessite que tous les packages d’application (.apk) soient signés. Pour obtenir de l’aide sur la**réutilisation** de certificats existants et sur les certificats de signature en général, consultez [Réutilisation de certificats de signature et inclusion d’applications dans un wrapper](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps). L’exécutable Java keytool.exe permet de générer de **nouvelles** informations d’identification nécessaires pour signer l’application de sortie incluse dans un wrapper. Tous les mots de passe définis doivent être sécurisés, mais notez-les car ils sont nécessaires pour exécuter l’outil de création de package de restrictions d’application.

> [!NOTE]
> Intune App Wrapping Tool ne prend pas en charge les schémas de signature d’applications de la v2 et de la v3 à venir. Une fois le fichier .apk inclus dans un wrapper à l’aide d’Intune App Wrapping Tool, il est recommandé d’utiliser [l’outil apksigner fourni par Google]( https://developer.android.com/studio/command-line/apksigner). Ainsi, lorsque l’application arrive sur les appareils des utilisateurs finaux, elle peut être lancée correctement selon les standards Android. 

- (Facultatif) Activez Multidex dans l’application d’entrée. Parfois, une application peut atteindre la limite de taille du fichier exécutable Dalvik (DEX) à cause des classes du SDK Intune MAM ajoutées pendant le wrapping. Les fichiers DEX font partie de la compilation d’une application Android. Dans ce scénario, une bonne pratique consiste à activer Multidex au sein de l’application elle-même. Dans certaines organisations, il peut être nécessaire de contacter la personne compile l’application (c’est-à-dire l’équipe de génération des applications). 

## <a name="install-the-app-wrapping-tool"></a>installer l'outil de création de package de restrictions d'application

1.  À partir du [dépôt GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android), téléchargez le fichier d’installation InstallAWT.exe de l’outil de création de package de restrictions d’application Intune pour Android sur un ordinateur Windows. Ouvrez le fichier d’installation.

2.  Acceptez le contrat de licence, puis terminez l’installation.

Notez le dossier dans lequel vous avez installé l'outil. L'emplacement par défaut est : C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>exécuter l'outil de création de package de restrictions d'application

1. Sur l’ordinateur Windows où vous avez installé l’outil de création de package de restrictions d’application, ouvrez une fenêtre PowerShell.

2. À partir du dossier où vous avez installé l’outil, importez le module PowerShell de l’outil de création de package de restrictions d’application :

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Exécutez l’outil à l’aide de la commande **invoke-AppWrappingTool**, dont la syntaxe est la suivante :
   ```PowerShell
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   Le tableau suivant décrit les propriétés de la commande **invoke-AppWrappingTool** :

|Propriété|Informations|Exemple|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|Chemin d'accès de l'application Android source (.apk).| |
 |**-OutputPath**&lt;String&gt;|Chemin d’accès à l’application Android de sortie. S'il s'agit du même chemin de répertoire qu'InputPath, la création de package échoue.| |
|**-KeyStorePath**&lt;String&gt;|Chemin d’accès au fichier de magasin de clés qui détient la paire de clés publique/privée pour la signature.|Par défaut, les fichiers de magasin de clés sont stockés dans « C:\Program Files (x86)\Java\jreX.X.X_XX\bin ». |
|**-KeyStorePassword**&lt;SecureString&gt;|Mot de passe utilisé pour déchiffrer le magasin de clés. Android requiert la signature de tous les packages d’applications (.apk). Recourez à l’utilitaire Java keytool pour générer le mot de passe du magasin de clés (KeyStorePassword). Vous pouvez en savoir plus sur le [magasin de clés](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) Java ici.| |
|**-KeyAlias**&lt;String&gt;|Nom de la clé à utiliser pour la signature.| |
|**-KeyPassword**&lt;SecureString&gt;|Mot de passe utilisé pour déchiffrer la clé privée qui sera utilisée pour la signature.| |
|**-SigAlg**&lt;SecureString&gt;| (Facultatif) Nom de l’algorithme de signature à utiliser pour la signature. L’algorithme doit être compatible avec la clé privée.|Exemples : SHA256withRSA, SHA1withRSA|
| **&lt;CommonParameters&gt;** | (Facultatif) La commande prend en charge les paramètres PowerShell communs tels que verbose et debug. |


- Pour obtenir la liste des paramètres communs, consultez le [Centre de scripts Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Pour afficher des informations détaillées sur l’utilisation de l’outil, entrez la commande suivante :

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Exemple :**

Importez le module PowerShell.
```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
Exécutez l’outil de création de package de restrictions d’application sur l’application native HelloWorld.apk.
```PowerShell
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Vous êtes ensuite invité à entrer des valeurs pour **KeyStorePassword** et **KeyPassword**. Entrez les informations d’identification que vous avez utilisées pour créer le fichier de magasin de clés.

L’application encapsulée et un fichier journal sont générés et enregistrés dans le chemin de sortie spécifié.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>À quelle fréquence dois-je réencapsuler mon application Android avec l’outil de création de package de restrictions d’application Intune ?
Les principaux scénarios dans lesquels vous devez réencapsuler vos applications sont les suivants :
* L’application elle-même a publié une nouvelle version. La version précédente de l’application a été empaquetée et chargée sur la console Intune.
* L’outil de création de package de restrictions d’application Intune pour Android a publié une nouvelle version qui intègre la correction de bogues importants, ou des fonctionnalités des stratégies de protection d’application Intune nouvelles et spécifiques. Ceci se produit toutes les 6 à 8 semaines via un dépôt GitHub pour [l’outil de création de package de restrictions d’application Microsoft Intune pour Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android).

Voici quelques bonnes pratiques de réencapsulation : 
* Conserver les certificats de signature utilisés lors du processus de génération. Consultez [Réutilisation de certificats de signature et inclusion d’applications dans un wrapper](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Réutilisation de certificats de signature et inclusion d’applications dans un wrapper
Android exige que toutes les applications soient signées par un certificat valide pour être installées sur des appareils Android.

Les applications incluses dans un wrapper peuvent être signées au cours du processus d’inclusion dans un wrapper ou *après* celui-ci à l’aide de vos outils de signature existants (toutes les informations de signature figurant dans l’application avant l’inclusion dans un wrapper sont ignorées). Si possible, les informations de signature utilisées pendant le processus de génération doivent être réutilisées durant l’inclusion dans un wrapper. Dans certaines organisations, il peut être nécessaire de contacter la personne qui détient les informations du magasin de clés (c’est-à-dire l’équipe de génération des applications). 

Si le certificat de signature précédent ne peut pas être utilisé ou que l’application n’a pas encore été déployée, vous pouvez créer un certificat de signature en suivant les instructions du [Guide du développeur Android](https://developer.android.com/studio/publish/app-signing.html#signing-manually).

Si l’application a déjà été déployée avec un autre certificat de signature, elle ne peut pas être chargée vers Intune après la mise à niveau. Tout scénario de mise à niveau d’application est interrompu si votre application est signée avec un certificat différent de celui avec lequel elle a été générée. Tout nouveau certificat de signature doit donc être conservé pour les mises à niveau des applications. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Considérations en matière de sécurité lors de l’exécution de l’outil de création de package de restrictions d’application
Pour empêcher l'usurpation d'identité, la divulgation d'informations et les attaques par élévation de privilège, procédez comme suit :

-   Vérifiez que l’application métier d’entrée, l’application de sortie et le magasin de clés Java se trouvent sur le même ordinateur Windows que celui sur lequel l’outil de création de package de restrictions d’application est en cours d’exécution.

-   Importez l’application de sortie dans Intune sur l’ordinateur où l’outil est en cours d’exécution. Voir [Keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html) pour en savoir plus sur Java Keytool.

-   Si l’application de sortie et l’outil se trouvent sur un chemin d’accès UNC (Universal Naming Convention) et que vous n’exécutez pas l’outil et les fichiers d’entrée sur le même ordinateur, sécurisez l’environnement en utilisant la [sécurité du protocole Internet (IPsec)](https://wikipedia.org/wiki/IPsec) ou la [signature SMB (Server Message Block)](https://support.microsoft.com/kb/887429).

-   Vérifiez que l’application provient d’une source approuvée.

-   Sécurisez le répertoire de sortie qui a l’application encapsulée. Envisagez d'utiliser un répertoire au niveau utilisateur pour la sortie.

## <a name="requiring-user-login-prompt-for-an-automatic-app-we-service-enrollment-requiring-intune-app-protection-policies-in-order-to-use-your-wrapped-android-lob-app-and-enabling-adal-sso-optional"></a>Nécessité d’une invite de connexion utilisateur pour une inscription au service APP-WE automatique, nécessité des stratégies de protection des applications Intune afin d’utiliser votre application métier Android empaquetée et activation de l’authentification unique ADAL (facultatif)

Vous trouverez ci-dessous des conseils afin d’exiger une invite utilisateur au lancement de l’application pour une inscription au service APP-WE automatique (désignée comme **inscription par défaut** dans cette section), ainsi que des stratégies de protection des applications Intune pour autoriser uniquement les utilisateurs protégés par Intune à utiliser votre application métier Android empaquetée. Ces conseils portent également sur l’activation de l’authentification unique pour votre application métier Android empaquetée. 

> [!NOTE] 
> Les avantages de **l’inscription par défaut** incluent une méthode simplifiée d’obtention de stratégie à partir du service APP-WE pour une application sur l’appareil.

### <a name="general-requirements"></a>Conditions générales requises
* L’équipe du kit SDK Intune nécessite l’ID de votre application. Vous pouvez le localiser par le biais du [portail Azure](https://portal.azure.com/), sous **Toutes les applications**, dans la colonne **ID d’application**. Pour contacter l’équipe du kit SDK Intune, envoyez un e-mail à l’adresse msintuneappsdk@microsoft.com.
     
### <a name="working-with-the-intune-sdk"></a>Utilisation du kit SDK Intune
Ces instructions sont spécifiques à toutes les applications Android et Xamarin qui souhaitent exiger des stratégies de protection des applications Intune à utiliser sur l’appareil d’un utilisateur final.

1. Configurez la bibliothèque ADAL à l’aide de la procédure définie dans le [Guide du Kit SDK de l’application Microsoft Intune pour les développeurs Android](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).

> [!NOTE]
> Le terme « ID client » associé à votre application est le même que le terme « ID d’application » du portail Azure associé à votre application. 
> * Pour activer l’authentification unique, la configuration numéro 2 dans « Configurations ADAL courantes » est celle dont vous avez besoin.

2. Activez l’inscription par défaut en insérant la valeur suivante dans le manifeste :
   ```xml
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Il doit s’agir de la seule intégration MAM-WE dans l’application. Si d’autres tentatives sont effectuées pour appeler des API MAMEnrollmentManager, des conflits peuvent se produire.

3. Activez la stratégie MAM requise en insérant la valeur suivante dans le manifeste :
   ```xml
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > Cela oblige l’utilisateur à télécharger l’application Portail d’entreprise sur l’appareil et à effectuer le flux d’inscription par défaut avant utilisation.

### <a name="see-also"></a>Voir aussi
- [Décider comment préparer les applications pour la gestion des applications mobiles avec Microsoft Intune](apps-prepare-mobile-application-management.md)

- [Guide du SDK de l’application Microsoft Intune pour les développeurs Android](app-sdk-android.md)
