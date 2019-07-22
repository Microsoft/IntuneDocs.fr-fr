---
title: Guide du SDK des applications Microsoft Intune pour les développeurs iOS
description: Le SDK d’application Microsoft Intune pour iOS vous permet d’incorporer des stratégies de protection des applications Intune (également appelées stratégies APP ou MAM) dans votre application iOS native.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 961470b9f5671dc39864dac45fdcb49862de4da9
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735560"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guide du SDK des applications Microsoft Intune pour les développeurs iOS

> [!NOTE]
> Vous pouvez d’abord lire l’article [Bien démarrer avec le SDK d’application Intune](app-sdk-get-started.md), qui explique comment préparer l’intégration sur chaque plateforme prise en charge.

Le SDK d’application Microsoft Intune pour iOS vous permet d’incorporer des stratégies de protection des applications Intune (également appelées stratégies APP ou MAM) dans votre application iOS native. Une application MAM est une application intégrée au SDK des applications Intune. Les administrateurs informatiques peuvent déployer des stratégies de protection des applications sur votre application mobile quand Intune gère activement l’application.

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer d’un ordinateur Mac OS exécutant OS X 10.8.5 ou version ultérieure et avec Xcode 9 ou version ultérieure installée.

* Votre application doit être ciblée pour iOS 10 ou ultérieur.

* Passez en revue les [Termes du contrat de licence du SDK des applications Intune pour iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Imprimez et conservez une copie des termes du contrat de licence pour vos archives. En téléchargeant et en utilisant le SDK des applications Intune pour iOS, vous acceptez les termes du contrat de licence.  Si vous ne les acceptez pas, n’utilisez pas le logiciel.

* Téléchargez les fichiers du SDK des applications Intune pour iOS sur [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk-repository"></a>Contenu du référentiel du kit de développement logiciel (SDK)

Les fichiers suivants s’appliquent aux applications/extensions qui ne contiennent pas de code SWIFT, ou qui sont compilées avec une version de Xcode antérieure à 10,2:

* **IntuneMAM.framework** : Framework du SDK des applications Intune. Nous vous recommandons de lier cette infrastructure à vos applications/extensions pour activer la gestion des applications clientes Intune. Toutefois, certains développeurs peuvent préférer les avantages en matière de performances de la bibliothèque statique. Consultez les rubriques suivantes.

* **libIntuneMAM.a** : Bibliothèque statique du SDK des applications Intune. Les développeurs peuvent choisir de lier la bibliothèque statique à la place de l’infrastructure. Étant donné que les bibliothèques statiques sont incorporées directement dans le fichier binaire de l’application/de l’extension au moment de la génération, l’utilisation de la bibliothèque statique présente des avantages en matière de performances au moment du lancement. Toutefois, l’intégration dans votre application est un processus plus complexe. Si votre application comprend des extensions, la liaison de la bibliothèque statique à l’application et aux extensions se traduira par une taille de lot d’applications plus importante, car la bibliothèque statique sera incorporée dans chaque fichier binaire d’application/extension. Lorsque vous utilisez l’infrastructure, les applications et les extensions peuvent partager le même binaire du kit de développement logiciel (SDK) Intune, ce qui réduit la taille de l’application.

* **IntuneMAMResources.Bundle** : une offre groupée de ressources qui contient les ressources sur lesquelles le kit de développement logiciel (SDK) est basé. Le groupe de ressources est requis uniquement pour les applications qui intègrent la bibliothèque statique (libIntuneMAM. a).

Les fichiers suivants s’appliquent aux applications/extensions qui contiennent du code SWIFT et sont compilés avec Xcode 10.2 +:

* **IntuneMAMSwift. Framework**: Framework SWIFT SDK de l’application Intune. Cette infrastructure contient tous les en-têtes des API que votre application appellera. Liez ce Framework à vos applications/extensions pour activer la gestion des applications clientes Intune.

* **IntuneMAMSwiftStub. Framework**: infrastructure de stub SWIFT du SDK de l’application Intune. Il s’agit d’une dépendance obligatoire de IntuneMAMSwift. Framework que les applications/extensions doivent lier.


Les fichiers suivants s’appliquent à toutes les applications/extensions:

* **IntuneMAMConfigurator**: outil utilisé pour configurer le fichier info. plist de l’application ou de l’extension avec les modifications minimales requises pour la gestion Intune. Selon les fonctionnalités de votre application ou de votre extension, vous devrez peut-être apporter des modifications manuelles supplémentaires au fichier info. plist.

* **En-têtes** : expose les API publiques du kit de développement logiciel (SDK) des applications Intune. Ces en-têtes sont inclus dans les frameworks IntuneMAM/IntuneMAMSwift, de sorte que les développeurs qui consomment l’un des frameworks n’ont pas besoin d’ajouter manuellement les en-têtes à leur projet. Les développeurs qui choisissent d’établir une liaison avec la bibliothèque statique (libIntuneMAM. a) doivent inclure manuellement ces en-têtes dans leur projet.

Les fichiers d’en-tête suivants incluent les API, les types de données et les protocoles que le SDK d’application Intune met à disposition des développeurs :

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMDiagnosticConsole.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h

Les développeurs peuvent mettre à disposition le contenu de toutes les en-têtes précédentes simplement en important IntuneMAM.h


## <a name="how-the-intune-app-sdk-works"></a>Fonctionnement du SDK de l’application Intune

L’objectif du SDK des applications Intune pour iOS consiste à ajouter des fonctionnalités de gestion aux applications iOS par le biais de modifications minimales du code. Moins le code change, plus la commercialisation est rapide, la cohérence et la stabilité de votre application mobile n’étant pas affectées.


## <a name="build-the-sdk-into-your-mobile-app"></a>Intégrer le SDK à votre application mobile

Pour activer le SDK des applications Intune, effectuez les étapes suivantes :

1. **Option 1-Framework (recommandé)** : Si vous utilisez Xcode 10.2 + et que votre application/extension contient le code SWIFT, `IntuneMAMSwift.framework` le `IntuneMAMSwiftStub.framework` lien et vers votre cible `IntuneMAMSwift.framework` : `IntuneMAMSwiftStub.framework` faites glisser **** vers la liste des binaires incorporés de la cible du projet.

    Sinon, liez `IntuneMAM.framework` à votre cible: faites `IntuneMAM.framework` glisser vers **** la liste des binaires incorporés de la cible du projet.

   > [!NOTE]
   > Si vous utilisez le framework, vous devez manuellement supprimer les architectures de simulateur du framework universel avant d’envoyer votre application à l’App Store. Pour plus de détails, consultez [Envoyer votre application à l’App Store](#submit-your-app-to-the-app-store).

   **Option 2-bibliothèque statique**: cette option est disponible uniquement pour les applications/extensions qui ne contiennent pas de code SWIFT, ou qui ont été créées avec Xcode < 10,2. créez un lien vers la bibliothèque `libIntuneMAM.a`. Faites glisser `libIntuneMAM.a` dans la liste **Frameworks et bibliothèques liés** de la cible du projet.

    ![SDK des applications Intune pour iOS : Frameworks et bibliothèques liés](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Ajoutez `-force_load {PATH_TO_LIB}/libIntuneMAM.a` à l’un des éléments suivants, en remplaçant `{PATH_TO_LIB}` par l’emplacement du SDK des applications Intune :
   * Le paramètre de configuration de build `OTHER_LDFLAGS` du projet.
   * Les **autres indicateurs de l’éditeur de liens** de l’interface utilisateur Xcode.

     > [!NOTE]
     > Pour rechercher `PATH_TO_LIB`, sélectionnez le fichier `libIntuneMAM.a` et choisissez **Obtenir des informations** dans le menu **Fichier**. Copiez et collez les informations correspondant au champ **Where** (le chemin) à partir de la section **General** de la fenêtre **Info**.

     Ajoutez le bundle de ressources `IntuneMAMResources.bundle` au projet en le faisant glisser sous **Copy Bundle Resources** (Copier les ressources du bundle) dans **Build Phases** (Phases de génération).

     ![SDK des applications Intune pour iOS : Copier les ressources du bundle](./media/intune-app-sdk-ios-copy-bundle-resources.png)
     
2. Si vous devez appeler l’une des API Intune à partir de SWIFT, votre application/extension doit importer les en-têtes du kit de développement logiciel (SDK) Intune requis via un en-tête de pontage objective-C. Si votre application/extension n’inclut pas encore d’en-tête de pontage objective-c, vous pouvez `SWIFT_OBJC_BRIDGING_HEADER` en spécifier une via le paramètre de configuration de build ou le champ d' **en-tête d’en-tête de pontage objective-c** de Xcode. Votre en-tête de pontage doit ressembler à ceci:

   ```objc
      #import <IntuneMAMSwift/IntuneMAM.h>
   ```
   
   Toutes les API du kit de développement logiciel (SDK) Intune seront ainsi disponibles dans tous les fichiers sources SWIFT de votre application/extension. 
   
    > [!NOTE]
    > * Vous pouvez choisir de relier uniquement des en-têtes du kit de développement logiciel (SDK) Intune spécifiques à SWIFT, plutôt qu’à IntuneMAM. h
    > * Selon le Framework/la bibliothèque statique que vous avez intégré, le chemin d’accès au (x) fichier (s) d’en-tête peut différer.
    > * Le fait de rendre les API du kit de développement logiciel (SDK) Intune disponibles dans SWIFT via une instruction d’importation de module (par exemple, Import IntuneMAMSwift) n’est pas pris en charge actuellement. L’utilisation d’un en-tête de pontage objective-C est l’approche recommandée.
    
3. Ajoutez ces frameworks iOS au projet :  
    * MessageUI.framework  
    * Security.framework  
    * MobileCoreServices.framework  
    * SystemConfiguration.framework  
    * libsqlite3.tbd  
    * libc++.tbd  
    * ImageIO.framework  
    * LocalAuthentication.framework  
    * AudioToolbox.framework  
    * QuartzCore.framework  
    * WebKit.framework

4. Activez le partage de trousseau (s’il ne l’est pas déjà) en choisissant **Capabilities** (Fonctionnalités) dans chaque cible du projet et en activant le commutateur **Keychain Sharing** (Partage de trousseau). Le partage de trousseau est nécessaire pour passer à l’étape suivante.

   > [!NOTE]
   > Votre profil de configuration doit prendre en charge les nouvelles valeurs de partage de trousseau. Les groupes de trousseau d’accès doivent prendre en charge un caractère générique. Vous pouvez le vérifier en ouvrant le fichier .mobileprovision dans un éditeur de texte, en recherchant **keychain-access-groups** et en vérifiant que vous avez un caractère générique. Par exemple :
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

5. Après avoir activé le partage de trousseau, procédez comme suit pour créer un groupe d’accès distinct dans lequel le kit de développement logiciel (SDK) de l’application Intune stockera ses données. Vous pouvez créer un groupe d’accès au trousseau à l’aide de l’interface utilisateur ou du fichier des droits. Si vous utilisez l’interface utilisateur pour créer le groupe d’accès au trousseau, assurez-vous de suivre les étapes ci-dessous :

     a. Si votre application mobile n’a pas de groupes d’accès au trousseau définis, ajoutez l’ID de bundle de l’application comme **premier** groupe.
    
    b. Ajoutez le groupe du trousseau partagé `com.microsoft.intune.mam` à vos groupes d’accès existants. Le SDK des applications Intune utilise ce groupe d’accès pour stocker des données.
    
    c. Ajoutez `com.microsoft.adalcache` à vos groupes d’accès existants.
    
        ![Intune App SDK iOS: keychain sharing](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    d. Si vous modifiez le fichier de droits directement, plutôt que d’utiliser l’IU Xcode illustrée ci-dessus pour créer les groupes d’accès au trousseau, ajoutez `$(AppIdentifierPrefix)` devant les groupes d’accès au trousseau (Xcode gère cela automatiquement). Par exemple :
    
        - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
        - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
        > [!NOTE]
        > An entitlements file is an XML file that is unique to your mobile application. It is used to specify special permissions and capabilities in your iOS app. If your app did not previously have an entitlements file, enabling keychain sharing (step 3) should have caused Xcode to generate one for your app. Ensure the app's bundle ID is the first entry in the list.

6. Incluez chaque protocole que votre application mobile passe à `UIApplication canOpenURL` dans le tableau `LSApplicationQueriesSchemes` du fichier Info.plist de votre application. Veillez à enregistrer vos modifications avant de passer à l’étape suivante.

7. Si votre application n’utilise pas encore FaceID, vérifiez que la clé [NSFaceIDUsageDescription Info.plist key](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) est configurée avec un message par défaut. Cela est obligatoire pour permettre à iOS d’informer l’utilisateur de la façon dont l’application a l’intention d’utiliser FaceID. Un paramètre de stratégie de protection des applications Intune permet que FaceID soit utilisé comme méthode d’accès aux applications quand il est configuré par l’administrateur informatique.

8. Utilisez l’outil IntuneMAMConfigurator inclus dans le [référentiel du Kit SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) pour terminer la configuration du fichier Info.plist de votre application. L’outil a trois paramètres :

   |Propriété|Comment l’utiliser|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (Facultatif) `<Path to the output plist>` |

Si le paramètre '-o' n’est pas spécifié, le fichier d’entrée sera modifié sur place. L’outil est idempotent et doit être réexécuté chaque fois que des modifications ont été apportées au fichier Info.plist ou aux droits de l’application. Vous devez également télécharger et exécuter la dernière version de cet outil en cas de mise à jour du Kit SDK Intune, au cas où les exigences de configuration du fichier Info.plist ont été modifiées dans la dernière version.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurer Azure Active Directory Authentication Library (ADAL)

Le SDK des applications Intune utilise [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) pour son authentification et les scénarios de lancement conditionnel. Il s’appuie également sur la bibliothèque ADAL pour inscrire l’identité de l’utilisateur au service MAM pour une gestion sans inscription d’appareil.

En règle générale, la bibliothèque ADAL nécessite que les applications s’inscrivent dans Azure Active Directory (AAD) et obtiennent un ID unique (ClientID) et d’autres identificateurs, pour garantir la sécurité des jetons accordés à l’application. Sauf indication contraire, le SDK des applications Intune utilise les valeurs d’inscription par défaut quand il contacte Azure AD.  

Si votre application utilise déjà la bibliothèque ADAL pour authentifier les utilisateurs, l’application doit utiliser ses valeurs d’inscription existantes et remplacer les valeurs par défaut du SDK des applications Intune. Cela empêche les utilisateurs d’avoir à s’authentifier deux fois (une fois pour le SDK des applications Intune et une fois pour l’application).

Votre application doit être, de préférence, liée à la [dernière version de la bibliothèque ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) sur sa branche maître. Le SDK d’application Intune utilise actuellement la branche de broker d’ADAL pour prendre en charge les applications qui nécessitent un accès conditionnel. (Ces applications dépendent par conséquent de l’application Microsoft Authenticator.) Toutefois, le SDK est toujours compatible avec la branche maître de la bibliothèque ADAL. Utilisez la branche qui convient à votre application.

### <a name="link-to-adal-binaries"></a>Créer une liaison aux fichiers binaires ADAL

Suivez les étapes ci-dessous pour lier votre application aux fichiers binaires ADAL :

1. Téléchargez [Azure Active Directory Authentication Library (ADAL) pour Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) à partir de GitHub, puis suivez les [instructions](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) de téléchargement de la bibliothèque ADAL à l’aide de sous-modules Git ou de CocoaPods.

2. Ajoutez l’infrastructure ADAL (option 1) ou la bibliothèque statique (option 2) à votre projet.

3. Si vous n’avez pas défini de groupe d’accès au trousseau pour votre application, ajoutez l’ID de bundle de l’application comme premier groupe.

4. Activez l’authentification unique (SSO) ADAL en ajoutant `com.microsoft.adalcache` aux groupes d’accès du trousseau.

5. Si vous définissez explicitement le groupe Keychain du cache partagé ADAL, vérifiez qu’il est défini sur `<appidprefix>.com.microsoft.adalcache`. La bibliothèque ADAL définit ce paramètre pour vous, sauf si vous le remplacez. Si vous voulez spécifier un groupe d’accès au trousseau personnalisé pour remplacer `com.microsoft.adalcache`, spécifiez-le dans le fichier Info.plist sous IntuneMAMSettings, à l’aide de la clé `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Configurer les paramètres ADAL pour le SDK des applications Intune

Si votre application utilise déjà la bibliothèque ADAL pour l’authentification et qu’elle a ses propres paramètres ADAL, vous pouvez forcer le SDK des applications Intune à utiliser les mêmes paramètres pendant l’authentification auprès d’Azure Active Directory. De cette façon, l’application ne demande pas deux fois à l’utilisateur de s’authentifier. Consultez [Configurer les paramètres du SDK des applications Intune](#configure-settings-for-the-intune-app-sdk) pour plus d’informations sur le remplissage des paramètres suivants :  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Si votre application utilise déjà la bibliothèque ADAL, les configurations suivantes sont nécessaires :

1. Dans le fichier Info.plist du projet, sous le dictionnaire **IntuneMAMSettings** avec le nom de clé `ADALClientId`, spécifiez l’ID de client à utiliser pour les appels ADAL.

2. Également sous le dictionnaire **IntuneMAMSettings** avec le nom de clé `ADALAuthority`, indiquez l’autorité Azure AD.

3. Toujours sous le dictionnaire **IntuneMAMSettings** avec le nom de clé `ADALRedirectUri`, indiquez l’URI de redirection à utiliser pour les appels ADAL. Vous pouvez également spécifier à la place `ADALRedirectScheme`, si l’URI de redirection de l’application est au format `scheme://bundle_id`.

En outre, les applications peuvent remplacer ces paramètres Azure AD lors de l’exécution. Pour ce faire, il vous suffit de définir les propriétés `aadAuthorityUriOverride`, `aadClientIdOverride` et `aadRedirectUriOverride` sur l’instance `IntuneMAMPolicyManager`.

4. Vérifiez que les étapes pour donner des autorisations à votre application iOS pour le service de stratégie de protection d’application (APP) sont respectées. Suivez les instructions de la [mise en route avec le guide du SDK Intune](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) sous « Autoriser votre application à accéder au service de protection d’application Intune (facultatif) ».  

> [!NOTE]
> L’approche du fichier Info.plist est recommandée pour tous les paramètres statiques et qui n’ont pas besoin d’être définis lors de l’exécution. Les valeurs affectées aux propriétés `IntuneMAMPolicyManager` prévalent sur toutes les valeurs correspondantes spécifiées dans le fichier Info.plist et persistent même après le redémarrage de l’application. Le Kit SDK continue à les utiliser pour les archivages de stratégie, jusqu'à ce que l’utilisateur soit désinscrit ou que les valeurs soient effacées ou modifiées.

### <a name="if-your-app-does-not-use-adal"></a>Si votre application n’utilise pas la bibliothèque ADAL

Comme mentionné plus haut, le SDK d’application Intune utilise la [Bibliothèque d’authentification Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) pour ses scénarios d’authentification et de lancement conditionnel. Il s’appuie également sur la bibliothèque ADAL pour inscrire l’identité de l’utilisateur au service MAM pour une gestion sans inscription d’appareil. Si **votre application n’utilise pas ADAL pour son propre mécanisme d’authentification**, le SDK d’application Intune fournit des valeurs par défaut pour les paramètres ADAL et gère l’authentification auprès d’Azure AD. Vous n’avez pas besoin de spécifier de valeurs pour les paramètres ADAL répertoriés ci-dessus. Tout mécanisme d’authentification éventuellement utilisé par votre application s’affiche en haut des invites ADAL. 

## <a name="configure-settings-for-the-intune-app-sdk"></a>Configurer les paramètres du SDK des applications Intune

Vous pouvez utiliser le dictionnaire **IntuneMAMSettings** du fichier Info.plist de l’application pour configurer le SDK des applications Intune. Si le dictionnaire IntuneMAMSettings n’apparaît pas dans votre fichier Info.plist, vous devez le créer.

Sous le dictionnaire IntuneMAMSettings, vous pouvez ajouter les paramètres pris en charge suivants pour configurer le SDK d’application Intune.

Certains de ces paramètres ont pu être traités dans les sections précédentes et d’autres ne s’appliquent pas à toutes les applications.

Paramètre  | Tapez  | Définition | Nécessaire ?
--       |  --   |   --       |  --
ADALClientId  | Chaîne  | Identificateur de client Azure AD de l’application. | Obligatoire si l’application utilise la bibliothèque ADAL. |
ADALAuthority | Chaîne | Autorité Azure AD de l’application en cours d’utilisation. Vous devez utiliser votre propre environnement dans lequel les comptes AAD ont été configurés. | Obligatoire si l’application utilise la bibliothèque ADAL. Si cette valeur est absente, une valeur par défaut Intune est utilisée.|
ADALRedirectUri  | Chaîne  | URI de redirection Azure AD de l’application. | ADALRedirectUri ou ADALRedirectScheme est nécessaire si l’application utilise la bibliothèque ADAL.  |
ADALRedirectScheme  | Chaîne  | Schéma de redirection Azure AD de l’application. Ce paramètre peut être utilisé à la place d’ADALRedirectUri si l’URI de redirection de l’application est au format `scheme://bundle_id`. | ADALRedirectUri ou ADALRedirectScheme est nécessaire si l’application utilise la bibliothèque ADAL. |
ADALLogOverrideDisabled | Booléen  | Indique si le SDK achemine tous les journaux de la bibliothèque ADAL (y compris les appels ADAL à partir de l’application, le cas échéant) dans son propre fichier journal. La valeur par défaut est NON. Définissez la valeur sur OUI si l’application doit définir le rappel de son propre journal ADAL. | Facultatif. |
ADALCacheKeychainGroupOverride | Chaîne  | Spécifie le groupe d’accès au trousseau à utiliser pour le cache ADAL, à la place de « com.microsoft.adalcache ». Notez que ce paramètre n’a pas le préfixe app-id. Ce préfixe est ajouté à la chaîne fournie au moment de l’exécution. | Facultatif. |
AppGroupIdentifiers | Table de chaînes  | Tableau de groupes d’applications issu de la section com.apple.security.application-groups des droits de l’application. | Obligatoire si l’application utilise des groupes d’applications. |
ContainingAppBundleId | Chaîne | Spécifie l’ID de bundle de l’application conteneur de l’extension. | Obligatoire pour les extensions iOS. |
DebugSettingsEnabled| Booléen | Si la valeur est OUI, les stratégies de test dans le bundle de paramètres peuvent être appliquées. Les applications ne doivent *pas* être publiées avec ce paramètre activé. | Facultatif. La valeur par défaut est Non.|
MainNibFile <br> MainNibFile~ipad  | Chaîne  | Ce paramètre doit contenir le nom du fichier nib principal de l’application.  | Obligatoire si l’application définit MainNibFile dans Info.plist. |
MainStoryboardFile <br> MainStoryboardFile~ipad  | Chaîne  | Ce paramètre doit contenir le nom du fichier storyboard principal de l’application. | Obligatoire si l’application définit UIMainStoryboardFile dans Info.plist. |
MAMPolicyRequired| Booléen| Spécifie si le démarrage de l’application doit être bloqué si l’application n’a pas de stratégie APP Intune. La valeur par défaut est NON. <br><br> Remarque : Les applications ne peuvent pas être envoyées à l’App Store avec MAMPolicyRequired défini sur YES. | Facultatif. La valeur par défaut est Non.|
MAMPolicyWarnAbsent | Booléen| Spécifie si l’application avertit l’utilisateur pendant le lancement si l’application n’a pas de stratégie APP Intune. <br><br> Remarque : Les utilisateurs pourront continuer à utiliser l’application sans stratégie après avoir ignoré l’avertissement. | Facultatif. La valeur par défaut est Non. |
MultiIdentity | Booléen| Spécifie si l’application prend en charge plusieurs identités. | Facultatif. La valeur par défaut est Non. |
SplashIconFile <br> SplashIconFile~ipad | Chaîne  | Spécifie le fichier de l’icône de démarrage Intune. | Facultatif. |
SplashDuration | Nombre | Durée minimale, en secondes, de l’affichage de l’écran de démarrage Intune au lancement de l’application. La valeur par défaut est 1,5. | Facultatif. |
BackgroundColor| Chaîne| Spécifie la couleur d’arrière-plan des écrans de démarrage et de code PIN. Accepte une chaîne hexadécimale RVB au format #XXXXXX, où X peut être compris entre 0 et 9 ou A et F. Le signe dièse peut être omis.   | Facultatif. La valeur par défaut est gris clair. |
ForegroundColor| Chaîne| Spécifie la couleur de premier plan pour les écrans de démarrage et d’entrée du code confidentiel, comme la couleur du texte. Accepte une chaîne hexadécimale RVB au format #XXXXXX, où X peut être compris entre 0 et 9 ou A et F. Le signe dièse peut être omis.  | Facultatif. La valeur par défaut est noir. |
AccentColor | Chaîne| Spécifie la couleur d’accentuation de l’écran d’entrée du code confidentiel, comme la couleur de texte des boutons et la couleur de surbrillance des zones. Accepte une chaîne hexadécimale RVB au format #XXXXXX, où X peut être compris entre 0 et 9 ou A et F. Le signe dièse peut être omis.| Facultatif. La valeur par défaut est bleu système. |
MAMTelemetryDisabled| Booléen| Spécifie que le SDK n’envoie pas les données de télémétrie au serveur principal.| Facultatif. La valeur par défaut est Non. |
MAMTelemetryUsePPE | Booléen | Spécifie si le SDK MAM envoie des données au backend de télémétrie PPE. Utilisez ceci quand vous testez vos applications avec une stratégie Intune pour que les données de télémétrie de test ne se mélangent pas avec les données du client. | Facultatif. La valeur par défaut est Non. |
MaxFileProtectionLevel | Chaîne | Facultatif. Autorise l’application à spécifier la valeur maximale `NSFileProtectionType` qu’elle peut prendre en charge. Cette valeur remplacera la stratégie envoyée par le service si le niveau est supérieur à ce que l’application peut prendre en charge. Valeurs possibles : `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Booléen | Affecter la valeur YES pour les extensions Open-In Action. Pour plus d’informations, consultez la section Partage de données par le biais d’UIActivityViewController. |
WebViewHandledURLSchemes | Tableau de chaînes | Spécifie les schémas d’URL gérés par l’affichage web de votre application. | Obligatoire si votre application utilise un affichage web qui gère les URL au moyen de liens et/ou de code JavaScript. |

## <a name="receive-app-protection-policy"></a>Recevoir une stratégie de protection des applications

### <a name="overview"></a>Vue d'ensemble

Pour recevoir la stratégie de protection des applications Intune, les applications doivent lancer une demande d’inscription auprès du service de gestion des applications mobiles Intune. Les applications peuvent être configurées dans la console Intune pour recevoir la stratégie de protection des applications avec ou sans inscription de l’appareil. La stratégie de protection des applications sans inscription, également appelée **APP-WE** ou MAM-WE, permet aux applications d’être gérées par Intune sans nécessiter l’inscription de l’appareil auprès de la gestion des appareils mobiles (MDM) Intune. Dans les deux cas, l’inscription auprès du service de gestion des applications mobiles Intune est nécessaire pour recevoir la stratégie.

### <a name="apps-that-use-adal"></a>Applications qui utilisent ADAL

Les applications qui utilisent déjà ADAL doivent appeler la méthode `registerAndEnrollAccount` sur l’instance `IntuneMAMEnrollmentManager` une fois que l’utilisateur a été authentifié avec succès :

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

En appelant la méthode `registerAndEnrollAccount`, le SDK inscrit le compte d’utilisateur et tente d’inscrire l’application pour ce compte. En cas d’échec de l’inscription pour une raison quelconque, le SDK retente automatiquement l’inscription 24 heures plus tard. Pour le débogage, l’application peut recevoir des [notifications](#status-result-and-debug-notifications), par le biais d’un délégué, sur les résultats de toute demande d’inscription.

Une fois que cette API a été appelée, l’application peut continuer à fonctionner normalement. Si l’inscription est effectuée, le SDK informe l’utilisateur qu’un redémarrage de l’application est nécessaire. À ce stade, l’utilisateur peut redémarrer immédiatement l’application.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal"></a>Applications qui n’utilisent pas la bibliothèque ADAL

Les applications qui ne connectent pas l’utilisateur avec ADAL peuvent toujours recevoir une stratégie de protection d’application du service de gestion des applications mobiles Intune en appelant l’API pour que le SDK gère cette authentification. Les applications doivent utiliser cette technique quand elles n’ont pas authentifié un utilisateur avec Azure AD, mais doivent quand même récupérer une stratégie de protection des applications pour renforcer la protection des données. C’est le cas, par exemple, quand un autre service d’authentification est utilisé pour se connecter à l’application ou quand l’application ne prend pas en charge la connexion. Pour cela, l’application peut appeler la méthode `loginAndEnrollAccount` sur l’instance `IntuneMAMEnrollmentManager` :

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

Avec cette méthode, le SDK demande à l’utilisateur des informations d’identification quand il n’existe aucun jeton. Le SDK tente alors d’inscrire l’application auprès du service de gestion des applications mobiles Intune au nom du compte d’utilisateur fourni. La méthode peut être appelée avec l’identité « nil ». Dans ce cas, le SDK effectue l’inscription avec l’utilisateur géré existant sur l’appareil (dans le cas de la gestion des appareils mobiles) ou demande un nom d’utilisateur à l’utilisateur si aucun utilisateur existant n’est trouvé.

En cas d’échec de l’inscription, l’application doit rappeler cette API plus tard, en fonction des détails de l’échec de l’appel. L’application peut recevoir des [notifications](#status-result-and-debug-notifications), via un délégué, concernant les résultats de toutes les demandes d’inscription.

Une fois que cette API a été appelée, l’application peut continuer à fonctionner normalement. Si l’inscription est effectuée, le SDK informe l’utilisateur qu’un redémarrage de l’application est nécessaire.

Exemple :

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Laisser Intune gérer l’authentification et l’inscription au lancement

Si vous souhaitez que le SDK Intune gère toutes les authentifications à l’aide de l’inscription et de la bibliothèque ADAL avant la fin du lancement de votre application, et que votre application exige toujours la stratégie APP, vous n’êtes pas obligé d’utiliser l’API `loginAndEnrollAccount`. Vous pouvez simplement affecter la valeur YES aux deux paramètres ci-dessous dans le dictionnaire IntuneMAMSettings dans le fichier Info.plist de l’application.

Paramètre  | Tapez  | Définition |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Booléen| Spécifie si l’application doit tenter de s’inscrire automatiquement au lancement si une identité gérée existante est détectée et qu’elle ne l’a pas encore fait. La valeur par défaut est NON. <br><br> Remarque : Si aucune identité managée n’est trouvée ou si aucun jeton valide pour l’identité n’est disponible dans le cache ADAL, la tentative d’inscription échoue en mode silencieux sans demander d’informations d’identification, sauf si l’application a également affecté la valeur Oui à MAMPolicyRequired. |
MAMPolicyRequired| Booléen| Spécifie si le démarrage de l’application est bloqué en cas d’absence de stratégie de protection des applications Intune. La valeur par défaut est NON. <br><br> Remarque : Les applications ne peuvent pas être envoyées à l’App Store avec MAMPolicyRequired défini sur YES. Lorsque vous définissez MAMPolicyRequired avec la valeur Oui, AutoEnrollOnLaunch doit également être défini avec la valeur Oui. |

Si vous choisissez cette option pour votre application, vous n’êtes pas obligé de gérer le redémarrage de votre application après l’inscription.

### <a name="deregister-user-accounts"></a>Désinscrire des comptes d’utilisateurs

Avant qu’un utilisateur se déconnecte d’une application, celle-ci doit désinscrire l’utilisateur dans le SDK. De cette façon :

1. Le compte de l’utilisateur ne peut plus s’inscrire.

2. La stratégie de protection des applications est supprimée.

3. Si l’application lance une réinitialisation sélective (facultative), toutes les données d’entreprise sont supprimées.

Avant que l’utilisateur ne soit déconnecté, l’application doit appeler la méthode suivante sur l’instance `IntuneMAMEnrollmentManager` :

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Cette méthode doit être appelée avant la suppression des jetons Azure AD du compte d’utilisateur. Le SDK a besoin des jetons AAD du compte d’utilisateur pour effectuer des demandes spécifiques au service de gestion des applications mobiles Intune au nom de l’utilisateur.

Si l’application supprime elle-même les données d’entreprise de l’utilisateur, l’indicateur `doWipe` peut être défini sur false. Sinon, l’application peut demander au SDK de lancer une réinitialisation sélective. Cela se traduit par un appel au délégué de réinitialisation sélective de l’application.

Exemple :

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Notifications d’état, de résultat et de débogage

L’application peut recevoir des notifications d’état, de résultat et de débogage concernant les demandes au service MAM Intune suivantes :

* Demandes d’inscription
* Demandes de mise à jour de stratégie
* Demandes de désinscription

Les notifications sont présentées via des méthodes déléguées dans `IntuneMAMEnrollmentDelegate.h` :

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

Ces méthodes déléguées retournent un objet `IntuneMAMEnrollmentStatus` avec les informations suivantes :

* L’identité du compte associé à la demande
* Un code d’état qui indique le résultat de la demande
* Une chaîne d’erreur avec une description du code d’état
* Objet `NSError`. Cet objet est défini dans `IntuneMAMEnrollmentStatus.h`, ainsi que les codes d’état spécifiques qui peuvent être retournés.

> [!NOTE]
> Ces informations sont destinées à des fins de débogage uniquement. Aucune logique métier dans votre application ne doit être basée sur ces notifications. Ces informations peuvent être envoyées à un service de télémétrie à des fins de débogage ou de surveillance.

### <a name="sample-code"></a>Exemple de code

Voici des exemples d’implémentation de méthodes déléguées :

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>Redémarrage de l’application

Quand une application reçoit des stratégies GAM pour la première fois, elle doit redémarrer pour appliquer les hooks nécessaires. Pour signaler à l’application qu’un redémarrage doit être effectué, le SDK fournit une méthode déléguée dans `IntuneMAMPolicyDelegate.h`.

```objc
 - (BOOL) restartApplication
```

La valeur de retour de cette méthode indique au SDK si l’application doit gérer le redémarrage nécessaire :

* Si la valeur true est retournée, l’application doit gérer le redémarrage.

* Si la valeur false est retournée, le SDK redémarre l’application après le retour de la méthode. Le SDK affiche immédiatement une boîte de dialogue qui demande à l’utilisateur de redémarrer l’application.

## <a name="customize-your-apps-behavior-with-apis"></a>Personnaliser le comportement de votre application avec des API

Le SDK d’application Intune comporte plusieurs API que vous pouvez appeler pour obtenir des informations sur la stratégie APP Intune déployée sur l’application. Vous pouvez utiliser ces données pour personnaliser le comportement de votre application. Le tableau suivant fournit des informations sur certaines classes Intune essentielles que vous utiliserez.

Class | Description
----- | -----------
IntuneMAMPolicyManager.h | La classe IntuneMAMPolicyManager expose la stratégie APP Intune déployée sur l’application. En particulier, elle expose les API qui sont utiles pour l’[activation de plusieurs identités](app-sdk-ios.md#enable-multi-identity-optional). |
IntuneMAMPolicy.h | La classe IntuneMAMPolicy expose certains paramètres de stratégie MAM qui s’appliquent à l’application. Ces paramètres de stratégie sont exposées afin que l’application puisse personnaliser son interface utilisateur. La plupart des paramètres de stratégie sont appliqués par le SDK, et non par l’application. Le seul que l’application doit implémenter est le contrôle Enregistrer sous. Cette classe expose certaines API nécessaires pour implémenter Enregistrer sous. |
IntuneMAMFileProtectionManager.h | La classe IntuneMAMFileProtectionManager expose des API que l’application peut utiliser pour sécuriser explicitement des fichiers et des répertoires en fonction d’une identité fournie. L’identité peut être gérée par Intune ou ne pas être gérée, et le SDK appliquera la stratégie MAM appropriée. L’utilisation de cette classe est facultative. |
IntuneMAMDataProtectionManager.h | La classe IntuneMAMDataProtectionManager expose des API que l’application peut utiliser pour sécuriser les mémoires tampons de données en fonction de l’identité fournie. L’identité peut être gérée par Intune ou ne pas être gérée, et le SDK appliquera le chiffrement en conséquence. |

## <a name="implement-save-as-controls"></a>Implémenter des contrôles Save-as

Intune permet aux administrateurs informatiques de sélectionner les emplacements de stockage dans lesquels une application gérée peut enregistrer des données. Les applications peuvent interroger le SDK d’application Intune pour connaître les emplacements de stockage autorisés à l’aide de l’API `isSaveToAllowedForLocation`, définie dans `IntuneMAMPolicy.h`.

Avant d’enregistrer des données gérées dans un emplacement de stockage local ou de type cloud, les applications doivent vérifier si l’administrateur a autorisé l’enregistrement de données à cet emplacement à l’aide de l’API `isSaveToAllowedForLocation`.

Quand les applications utilisent l’API `isSaveToAllowedForLocation`, elles doivent passer l’UPN utilisé pour l’emplacement de stockage, s’il est disponible.

### <a name="supported-save-locations"></a>Emplacements d’enregistrement pris en charge

L’API `isSaveToAllowedForLocation` fournit des constantes pour vérifier si l’administrateur informatique autorise l’enregistrement des données aux emplacements suivants définis dans `IntuneMAMPolicy.h` :

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Les applications doivent utiliser les constantes dans `isSaveToAllowedForLocation` pour vérifier si les données peuvent être enregistrées dans des emplacements considérés comme « gérés », tels que OneDrive Entreprise, ou « personnels ». Par ailleurs, l’API doit être utilisée quand l’application ne peut pas vérifier si un emplacement est « géré » ou « personnel ».

Les emplacements considérés comme étant « personnels » sont représentés par la constante `IntuneMAMSaveLocationOther`.

La constante `IntuneMAMSaveLocationLocalDrive` doit être utilisée quand l’application enregistre les données à un emplacement quelconque sur l’appareil local.

## <a name="share-data-via-uiactivityviewcontroller"></a>Partage de données par le biais d’UIActivityViewController

À compter de la version 8.0.2, le SDK d’application Intune peut filtrer les actions `UIActivityViewController` afin que seuls les emplacements de partage gérés par Intune puissent être sélectionnés. Ce comportement sera contrôlé par la stratégie de transfert de données d’application.

### <a name="copy-to-actions"></a>Actions « Copier vers »

Quand vous partagez des documents par le biais d’`UIActivityViewController` et `UIDocumentInteractionController`, iOS affiche les actions « Copier vers » pour chaque application prenant en charge l’ouverture du document partagé. Les applications déclarent les types de document qu’elles prennent en charge par le biais du paramètre `CFBundleDocumentTypes` dans leur fichier Info.plist. Ce type de partage n’est plus disponible si la stratégie interdit le partage avec les applications non gérées. À la place, l’utilisateur doit ajouter une extension d’action non-IU à son application, et la lier au SDK de l’application Intune. L’extension d’action est simplement un stub. Le SDK implémente le comportement de partage des fichiers. Effectuez les étapes ci-dessous :

1. Votre application doit avoir au moins un schemeURL défini sous `CFBundleURLTypes` dans le fichier Info.plist.

2. Votre application et votre extension d’action doivent partager au moins un groupe d’applications. Celui-ci doit être répertorié sous le tableau `AppGroupIdentifiers`, sous les dictionnaires IntuneMAMSettings de l’application et de l’extension.

3. Nommez l’extension d’action « Ouvrir dans » en ajoutant le nom de l’application. Localisez le fichier Info.plist selon les besoins.

4. Spécifiez une icône de modèle pour l’extension, comme décrit dans la [documentation destinée aux développeurs Apple](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/). Vous pouvez également utiliser l’outil IntuneMAMConfigurator pour générer ces images à partir du répertoire .app de l’application. Pour ce faire, exécutez :

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. Sous IntuneMAMSettings dans le fichier Info.plist de l’extension, ajoutez un paramètre booléen nommé `OpenInActionExtension` avec la valeur YES.

6. Configurez `NSExtensionActivationRule` pour prendre en charge un seul fichier et tous les types du `CFBundleDocumentTypes` de l’application avec le préfixe `com.microsoft.intune.mam`. Par exemple, si l’application prend en charge public.text et public.image, la règle d’activation est :

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>Mettre à jour les extensions de partage et d’action existantes

Si votre application contient déjà des extensions de partage ou d’action, vous devrez modifier leur `NSExtensionActivationRule` pour autoriser les types Intune. Pour chaque type pris en charge par l’extension, ajoutez un type supplémentaire commençant par `com.microsoft.intune.mam`. Par exemple, si la règle d’activation existante est :  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

Vous devez la changer en :

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> Vous pouvez utiliser l’outil IntuneMAMConfigurator pour ajouter des types Intune à la règle d’activation. Si votre règle d’activation existante utilise les constantes de chaîne prédéfinies (par exemple NSExtensionActivationSupportsFileWithMaxCount, NSExtensionActivationSupportsText, etc.), la syntaxe du prédicat peut devenir assez complexe. Vous pouvez également utiliser l’outil IntuneMAMConfigurator pour convertir la règle d’activation des constantes de chaîne en chaîne de prédicat tout en ajoutant les types Intune.

### <a name="what-the-ui-should-look-like"></a>Ce à quoi doit ressembler l’interface utilisateur

Ancienne interface utilisateur :

![Partage de données - Ancienne interface utilisateur de partage iOS](./media/sharing-UI-old.png)

Nouvelle interface utilisateur :

![Partage de données - Nouvelle interface utilisateur de partage iOS](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Activer la configuration ciblée (configuration d’application APP/MAM) pour vos applications iOS

La configuration ciblée de gestion des applications mobiles (également appelée configuration d’application MAM) permet à une application de recevoir des données de configuration par le biais du SDK Intune. Les variantes et le format de ces données doivent être définis et communiqués aux clients Intune par le propriétaire/développeur d’application.

Les administrateurs Intune peuvent cibler et déployer des données de configuration par le biais du portail Intune Azure et de l’API Graph Intune. À compter de la version 7.0.1 du SDK d’application Intune pour iOS, les applications qui participent à la configuration ciblée de gestion des applications mobiles peuvent recevoir des données de configuration ciblée de gestion des applications mobiles par le biais du service de gestion des applications mobiles. Les données de configuration d’application sont envoyées via notre service de gestion des applications mobiles directement à l’application au lieu de passer par le canal de gestion des appareils mobiles. Le SDK d’application Intune fournit une classe pour accéder aux données récupérées à partir de ces consoles. Les prérequis sont les suivants :

* L’application doit être inscrite auprès du service de gestion des applications mobiles Intune pour que vous puissiez accéder à l’interface utilisateur de configuration ciblée de la gestion des applications mobiles. Pour plus d’informations, consultez [Recevoir la stratégie de protection d’application](#receive-app-protection-policy).

* Incluez `IntuneMAMAppConfigManager.h` dans le fichier source de votre application.

* Appelez `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` pour obtenir l’objet de configuration d’application.

* Appelez le sélecteur approprié sur l’objet `IntuneMAMAppConfig`. Par exemple, si la clé de votre application est une chaîne, vous devez utiliser `stringValueForKey` ou `allStringsForKey`. Pour obtenir une description détaillée des valeurs de retour et des conditions d’erreur, consultez `IntuneMAMAppConfig.h`.

Pour plus d’informations sur les fonctionnalités de l’API Graph, consultez [Référence de l’API Graph](https://developer.microsoft.com/graph/docs/concepts/overview).

Pour plus d’informations sur la façon de créer une stratégie de configuration ciblée de gestion des applications mobiles dans iOS, consultez la section sur la configuration ciblée de gestion des applications mobiles dans [How to use Microsoft Intune app configuration policies for iOS (Guide pratique pour utiliser des stratégies de configuration d’application Microsoft Intune pour iOS)](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).

## <a name="telemetry"></a>Télémétrie

Par défaut, le SDK d’application Intune pour iOS collecte des données de télémétrie pour les types d’événements suivants :

* **Lancement d’applications** : Permet à Microsoft Intune d’en savoir plus sur l’utilisation des applications MAM par type de gestion (MAM avec gestion des appareils mobiles, MAM sans inscription à la gestion des appareils mobiles, etc.).

* **Appels d’inscription** : Permet à Microsoft Intune d’en savoir plus sur les taux de réussite et d’autres mesures de performances des appels d’inscription côté client.

* **Actions Intune** : Pour aider à diagnostiquer les problèmes et garantir la fonctionnalité Intune, nous collectons des informations sur les actions du SDK Intune.

> [!NOTE]
> Si vous choisissez de ne pas envoyer les données de télémétrie du SDK des applications Intune à Microsoft Intune à partir de votre application mobile, vous devez désactiver la capture de télémétrie du SDK des applications Intune. Définissez la propriété `MAMTelemetryDisabled` sur OUI dans le dictionnaire IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Activer plusieurs identités (facultatif)

Par défaut, le SDK applique une stratégie à l’ensemble de l’application. La possibilité d’activer plusieurs identités est une fonctionnalité MAM que vous pouvez utiliser pour appliquer une stratégie selon l’identité. Cette fonctionnalité implique davantage de participation de l’application que les autres fonctionnalités MAM.

L’application doit informer le SDK quand elle a l’intention de changer l’identité active. Le SDK indique également à l’application quand un changement d’identité est nécessaire. Actuellement, seule une identité gérée est prise en charge. Une fois que l’utilisateur a inscrit l’appareil ou l’application, le SDK utilise cette identité et la considère comme l’identité gérée principale. Les autres utilisateurs de l’application sont considérés comme étant non gérés avec des paramètres de stratégie non restreints.

Notez qu’une identité est définie simplement sous forme de chaîne. Les identités respectent la casse. Les demandes d’identité au SDK peuvent ne pas retourner la même casse que celle utilisée à l’origine quand l’identité à été définie.

### <a name="identity-overview"></a>Vue d’ensemble de l’identité

Une identité est simplement le nom d’utilisateur d’un compte (par exemple, user@contoso.com). Les développeurs peuvent définir l’identité de l’application sur les niveaux suivants :

* **Identité du processus** : Définit l’identité au niveau du processus. Principalement utilisée pour les applications avec identité unique. Cette identité affecte tous les fichiers, tâches et interface utilisateur.

* **Identité de l’interface utilisateur** : Détermine les stratégies qui sont appliquées aux tâches de l’interface utilisateur sur le thread principal, comme les opérations de couper/copier/coller, l’entrée du code PIN, l’authentification et le partage de données. L’identité de l’interface utilisateur n’affecte pas les tâches de fichier comme la sauvegarde et le chiffrement.

* **Identité du thread** : Concerne les stratégies qui sont appliquées sur le thread actuel. Cette identité affecte toutes les tâches, les fichiers et l’interface utilisateur.

L’application est chargée de définir les identités de manière appropriée, que l’utilisateur soit géré ou non.

À tout moment, chaque thread a une identité effective pour les tâches d’interface utilisateur et des tâches de fichier. Il s’agit de l’identité utilisée pour vérifier les stratégies, le cas échéant, qui doivent être appliquées. Si l’identité est définie sur « Aucune identité » ou que l’utilisateur n’est pas géré, aucune stratégie n’est appliquée. Les graphiques ci-dessous montrent comment les identités effectives sont déterminées.

  ![SDK de l’application Intune pour iOS : Processus de détermination de l’identité](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Files d’attente du thread

Les applications distribuent souvent des tâches synchrones et asynchrones aux files d’attente du thread. Le SDK intercepte les appels GCD (Grand Central Dispatch) et associe l’identité du thread actuel aux tâches distribuées. Quand les tâches sont terminées, le SDK remplace temporairement l’identité du thread par l’identité associée aux tâches, termine les tâches, puis restaure l’identité du thread d’origine.


Comme `NSOperationQueue` repose sur GCD, `NSOperations` s’exécute sur l’identité du thread au moment où les tâches sont ajoutées à `NSOperationQueue`. `NSOperations` ou les fonctions distribuées directement par le biais de GCD peuvent également changer l’identité du thread actuel lors de leur exécution. Cette identité remplace l’identité héritée du thread de distribution.

### <a name="file-owner"></a>Propriétaire du fichier

Le SDK effectue le suivi de l’identité des propriétaires de fichier local et applique des stratégies en conséquence. Un propriétaire de fichier est établi quand un fichier est créé ou qu’il est ouvert en mode tronqué. Le propriétaire est défini sur l’identité de la tâche de fichier effective du thread qui effectue la tâche.

Sinon, les applications peuvent définir l’identité du propriétaire du fichier explicitement à l’aide de `IntuneMAMFilePolicyManager`. Les applications peuvent utiliser `IntuneMAMFilePolicyManager` pour récupérer le propriétaire du fichier et définir l’identité de l’interface utilisateur avant d’afficher le contenu du fichier.

### <a name="shared-data"></a>Données partagées

Si l’application crée des fichiers avec des données d’utilisateurs gérés et non gérés, elle doit chiffrer les données de l’utilisateur géré. Vous pouvez chiffrer des données à l’aide des API `protect` et `unprotect` dans `IntuneMAMDataProtectionManager`.

La méthode `protect` accepte une identité qui peut être un utilisateur géré ou non géré. Si l’utilisateur est géré, les données sont chiffrées. Si l’utilisateur n’est pas géré, un en-tête est ajouté aux données qui encodent l’identité, mais les données ne sont pas chiffrées. Vous pouvez utiliser la méthode `protectionInfo` pour récupérer le propriétaire des données.

### <a name="share-extensions"></a>Extensions de partage

Si l’application a une extension de partage, le propriétaire de l’élément partagé peut être récupéré par le biais de la méthode `protectionInfoForItemProvider` dans `IntuneMAMDataProtectionManager`. Si l’élément partagé est un fichier, le SDK gère la définition du propriétaire du fichier. Si l’élément partagé est représenté par des données, l’application doit définir le propriétaire du fichier si ces données sont conservées dans un fichier et doit appeler l’API `setUIPolicyIdentity` avant d’afficher ces données dans l’interface utilisateur.

### <a name="turn-on-multi-identity"></a>Activer la multi-identité

Par défaut, les applications sont considérées comme ayant une identité unique. Le SDK définit l’identité du processus pour l’utilisateur inscrit. Pour activer la prise en charge de plusieurs identités, ajoutez un paramètre booléen avec le nom `MultiIdentity` et la valeur OUI au dictionnaire IntuneMAMSettings dans le fichier Info.plist de l’application.

> [!NOTE]
> Quand plusieurs identités sont activées, l’identité du processus, l’identité de l’interface utilisateur et les identités de thread sont définies sur zéro. L’application est chargée de les définir correctement.

### <a name="switch-identities"></a>Changer d’identité

* **Changement d’identité lancé par l’application** :

    Au lancement, les applications gérant plusieurs identités sont considérées comme s’exécutant sous un compte inconnu non géré. L’interface utilisateur de lancement conditionnel ne s’exécute pas et aucune stratégie n’est appliquée à l’application. L’application notifie le SDK chaque fois que l’identité doit être changée. En général, cela se produit chaque fois que l’application est sur le point d’afficher les données d’un compte d’utilisateur spécifique.

    C’est le cas, par exemple, quand l’utilisateur tente d’ouvrir un document, une boîte aux lettres ou un onglet sur un ordinateur portable. L’application doit notifier le SDK avant que le fichier, la boîte aux lettres ou l’onglet ne soit réellement ouvert. Cette opération est effectuée avec l’API `setUIPolicyIdentity` dans `IntuneMAMPolicyManager`. Cette API doit être appelée, que l’utilisateur soit géré ou non. Si l’utilisateur est géré, le SDK effectue les vérifications du lancement conditionnel, comme la détection de jailbreak, l’entrée du code PIN et l’authentification.

    Le résultat du changement d’identité est retourné à l’application de façon asynchrone par le biais d’un gestionnaire d’achèvement. L’application reporte l’ouverture du document, de la boîte aux lettres ou de l’onglet tant qu’un code de résultat n’est pas retourné. En cas d’échec du changement d’identité, l’application doit annuler la tâche.

* **Changement d’identité lancé par le SDK** :

    Parfois, le SDK doit demander à l’application de basculer sur une identité spécifique. Les applications gérant plusieurs identités doivent implémenter la méthode `identitySwitchRequired` dans `IntuneMAMPolicyDelegate` pour traiter cette demande.

    Quand cette méthode est appelée, si l’application peut gérer la demande de basculement sur l’identité spécifiée, elle doit passer `IntuneMAMAddIdentityResultSuccess` au gestionnaire d’achèvement. Si elle ne peut pas gérer le basculement de l’identité, l’application doit passer `IntuneMAMAddIdentityResultFailed` au gestionnaire d’achèvement.

    L’application n’a pas besoin d’appeler `setUIPolicyIdentity` en réponse à cet appel. Si le SDK a besoin que l’application bascule sur un compte d’utilisateur non géré, une chaîne vide est passée dans l’appel `identitySwitchRequired`.

* **Réinitialisation sélective** :

    Quand une réinitialisation sélective est effectuée dans l’application, le SDK appelle la méthode `wipeDataForAccount` dans `IntuneMAMPolicyDelegate`. L’application est chargée de supprimer le compte de l’utilisateur spécifié et toutes les données associées. Le SDK est capable de supprimer tous les fichiers appartenant à l’utilisateur et le fait si l’application retourne la valeur FALSE pour l’appel `wipeDataForAccount`.

    Notez que cette méthode est appelée à partir d’un thread d’arrière-plan. L’application ne doit pas retourner de valeur tant que toutes les données de l’utilisateur n’ont pas été supprimées (à l’exception des fichiers, si l’application retourne FALSE).

## <a name="ios-best-practices"></a>Bonnes pratiques pour iOS

Voici les pratiques recommandées dans le cadre du développement pour iOS :

* Le système de fichiers iOS respecte la casse. Vérifiez que la casse est correcte pour les noms de fichier comme `libIntuneMAM.a` et `IntuneMAMResources.bundle`.

* Si Xcode a des difficultés à localiser `libIntuneMAM.a`, vous pouvez résoudre ce problème en ajoutant le chemin à cette bibliothèque dans les chemins de recherche de l’éditeur de liens.

## <a name="faqs"></a>FAQ

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>Est-ce que toutes les API sont adressables par le biais du code Swift natif ou de l’interopérabilité Objective-C et Swift ?

Les API du SDK des applications Intune sont écrites en Objective-C uniquement et ne prennent pas en charge le code Swift **natif**. L’interopérabilité entre Swift et Objective-C est nécessaire.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>Tous les utilisateurs de mon application doivent-ils être inscrits auprès du service APP-WE ?

Non. En réalité, seuls les comptes professionnels ou scolaires doivent être inscrits dans le SDK des applications Intune. Les applications sont chargées de déterminer si un compte est utilisé dans un contexte professionnel ou scolaire.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>Qu’en est-il des utilisateurs qui se sont déjà connectés à l’application ? Doivent-ils être inscrits ?

L’application est chargée de l’inscription des utilisateurs une fois qu’ils ont été authentifiés. L’application est également chargée de l’inscription de tous les comptes potentiellement préexistants quand l’application a reçu les fonctionnalités MAM sans gestion des appareils mobiles.

Pour ce faire, l’application doit utiliser la méthode `registeredAccounts:`. Cette méthode retourne un NSDictionary contenant tous les comptes inscrits au service MAM Intune. Si un compte existant dans l’application ne figure pas dans la liste, l’application doit l’inscrire via `registerAndEnrollAccount:`.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>À quelle fréquence le SDK réessaye-t-il les inscriptions ?

Le SDK réessaie automatiquement toutes les inscriptions ayant échouées dans un intervalle de 24 heures. De cette façon, le SDK vérifie que l’utilisateur est inscrit et reçoit les stratégies si son organisation a activé la gestion MAM une fois que l’utilisateur s’est connecté à l’application.

Le SDK n’effectue plus de nouvelle tentative quand il détecte qu’un utilisateur a inscrit l’application. C’est parce que seul un utilisateur peut inscrire une application à un moment donné. Si l’utilisateur est désinscrit, les nouvelles tentatives recommencent dans le même intervalle de 24 heures.

### <a name="why-does-the-user-need-to-be-deregistered"></a>Pourquoi l’utilisateur doit-il être désinscrit ?

Le SDK prend ces actions en arrière-plan régulièrement :

* Si l’application n’est pas encore inscrite, il tente d’inscrire les comptes inscrits toutes les 24 heures.
* Si l’application est inscrite, le SDK recherche les mises à jour des stratégies GAM toutes les 8 heures.

La désinscription d’un utilisateur indique au SDK que l’utilisateur n’utilise plus l’application et qu’il peut arrêter les événements périodiques ci-dessus pour ce compte d’utilisateur. Il déclenche également une désinscription de l’application ainsi qu’une réinitialisation sélective si nécessaire.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>Dois-je définir l’indicateur doWipe sur true dans la méthode de désinscription ?

Cette méthode doit être appelée avant que l’utilisateur ne soit déconnecté de l’application.  Si les données de l’utilisateur sont supprimées de l’application dans le cadre de la déconnexion, `doWipe` peut être défini sur false. En revanche, si l’application ne supprime pas les données de l’utilisateur, `doWipe` doit être défini sur true pour que le SDK puisse supprimer les données.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>Existe-t-il d’autres façons de désinscrire une application ?

Oui, l’administrateur informatique peut envoyer une commande de réinitialisation sélective à l’application. Cette opération désinscrit l’utilisateur et efface ses données. Le SDK gère automatiquement ce scénario et envoie une notification via la méthode déléguée de désinscription.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>Existe-t-il un exemple d’application qui montre comment intégrer le SDK ?

Oui ! Nous avons récemment amélioré notre exemple d’application open source [Wagr pour iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App). Wagr est maintenant compatible avec la stratégie de protection des applications à l’aide du SDK d’application Intune.

### <a name="how-can-i-troubleshoot-my-app"></a>Comment puis-je résoudre les problèmes liés à mon application?

Le kit de développement logiciel (SDK) Intune pour iOS 9.0.3 + prend en charge la possibilité d’ajouter une console de diagnostic dans l’application mobile pour tester les stratégies et les erreurs de journalisation. `IntuneMAMDiagnosticConsole.h`définit l' `IntuneMAMDiagnosticConsole` interface de classe, que les développeurs peuvent utiliser pour afficher la console de diagnostic Intune. Cela permet aux utilisateurs finaux ou aux développeurs au cours du test de collecter et de partager des journaux Intune pour aider à diagnostiquer tout problème qu’ils peuvent rencontrer. Cette API est facultative pour les intégrateurs.

## <a name="submit-your-app-to-the-app-store"></a>Envoyer votre application à l’App Store

Les versions de bibliothèque statique et de framework du SDK des applications Intune sont des fichiers binaires universels. Cela signifie qu’elles contiennent le code de toutes les architectures d’appareil et de simulateur. Apple rejette les applications envoyées à l’App Store si elles contiennent du code de simulateur. Lors de la compilation de versions de bibliothèque statique ou d’appareil uniquement, l’éditeur de liens supprime automatiquement le code du simulateur. Suivez les étapes ci-dessous pour vérifier que tout le code de simulateur est supprimé avant de charger votre application dans l’App Store.

1. Vérifiez que `IntuneMAM.framework` se trouve sur votre bureau.

2. Exécutez ces commandes :

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    La première commande supprime les architectures de simulateur du fichier DYLIB du framework. La deuxième commande copie le fichier DYLIB d’appareil uniquement dans le répertoire du framework.
