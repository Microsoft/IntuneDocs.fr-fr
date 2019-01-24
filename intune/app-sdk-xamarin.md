---
title: Liaisons Xamarin du kit SDK d’application Microsoft Intune
description: Les liaisons Xamarin du kit SDK d’application Intune activent la stratégie de protection des applications Intune dans les applications iOS et Android générées avec Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 65a461928c377dd4a674f8f3f2eeeef148ab56b2
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316897"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Liaisons Xamarin du kit SDK d’application Microsoft Intune

> [!NOTE]
> Vous pouvez d’abord lire l’article [Bien démarrer avec le SDK d’application Intune](app-sdk-get-started.md), qui explique comment préparer l’intégration sur chaque plateforme prise en charge.

## <a name="overview"></a>Vue d’ensemble
Les [liaisons Xamarin du kit SDK d’application Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) activent la [stratégie de protection des applications Intune](app-protection-policy.md) dans les applications iOS et Android générées avec Xamarin. Les liaisons permettent aux développeurs de générer facilement des fonctionnalités de protection des applications Intune dans leur application Xamarin.

Les liaisons Xamarin du kit SDK d’application Microsoft Intune vous permettent d’incorporer des stratégies de protection des applications Intune (également appelées stratégies APP ou MAM) dans vos applications développées avec Xamarin. Une application prenant en charge la gestion GAM est une application intégrée au kit SDK d’application Intune. Les administrateurs informatiques peuvent déployer des stratégies de protection des applications sur votre application mobile quand celle-ci est activement gérée par Intune.

## <a name="whats-supported"></a>Ce qui est pris en charge

### <a name="developer-machines"></a>Ordinateurs de développement
* Windows (Visual Studio version 15.7+)
* macOS

### <a name="mobile-app-platforms"></a>Plateformes d’applications mobiles
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Scénarios de gestion des applications mobiles Intune

* Service APP-WE Intune (sans inscription d’appareils)
* Appareils inscrits auprès de MDM Intune
* Appareils inscrits auprès d’une gestion de la mobilité d’entreprise tierce

Les applications Xamarin générées avec les liaisons Xamarin du kit SDK d’application Intune peuvent désormais recevoir des stratégies de protection des applications Intune sur des appareils inscrits et non inscrits auprès de la solution MDM (gestion des appareils mobiles) Intune.

## <a name="prerequisites"></a>Prérequis

Consultez les [termes du contrat de licence](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Imprimez et conservez une copie des termes du contrat de licence pour vos archives. En téléchargeant et en utilisant les liaisons Xamarin du kit SDK d’application Intune, vous acceptez les termes du contrat de licence. Si vous ne les acceptez pas, n'utilisez pas le logiciel.

Le SDK s’appuie sur la [Bibliothèque d’authentification Active Directory (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) pour ses scénarios [d’authentification](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) et de lancement conditionnel, ce qui nécessite que les applications soient configurées avec [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Si votre application est déjà configurée pour utiliser la bibliothèque ADAL ou MSAL et que son propre ID client personnalisé permet l’authentification auprès d’Azure Active Directory, vérifiez que les étapes pour accorder à votre application Xamarin des autorisations vis-à-vis du service de gestion des applications mobiles (MAM) Intune sont respectées. Suivez les instructions de la section « [Autoriser votre application à accéder au service de protection d’application Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional) » de [Prise en main du guide du SDK Intune](app-sdk-get-started.md).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Activation des stratégies de protection des applications Intune dans votre application mobile iOS
1. Ajoutez le paquet NuGet [Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) à votre projet Xamarin.iOS.
2.  Suivez les étapes générales requises pour l’intégration du Kit SDK d’application Intune dans une app mobile iOS. Vous pouvez commencer à l’étape 3 des instructions de l’intégration dans le [Guide du kit SDK d’application Intune pour les développeurs iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Vous pouvez ignorer l’étape finale indiquée dans cette section sur l’exécution de l’outil IntuneMAMConfigurator, car il est inclus dans le package Microsoft.Intune.MAM.Xamarin.iOS et il s’exécute automatiquement au moment de la génération.
    **Important** : l’activation du partage de trousseau pour une application est légèrement différente dans Visual Studio par rapport à Xcode. Ouvrez le fichier plist de droits de l’application et vérifiez que l’option « Activer le trousseau » est activée et que les groupes de partage de trousseau appropriés sont ajoutés dans cette section. Vérifiez ensuite que le fichier plist des droits est spécifié dans le champ « Droits personnalisés » des options « Signature du bundle iOS » du projet pour toutes les combinaisons de configuration/plate-forme appropriées.
3.  Une fois les liaisons ajoutées et l’application correctement configurée, celle-ci peut commencer à utiliser les API du kit SDK Intune. Pour cela, vous devez inclure l’espace de noms suivant :

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Pour commencer à recevoir des stratégies de protection d’application, votre application doit s’inscrire auprès du service GAM d’Intune. Si votre application n’utilise pas la [bibliothèque d’authentification Azure Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) ou la [bibliothèque d’authentification Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) pour authentifier les utilisateurs, et souhaitez que le SDK Intune gère l’authentification, votre application doit fournir l’UPN de l’utilisateur à la méthode LoginAndEnrollAccount d’IntuneMAMEnrollmentManager :
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      Les applications peuvent passer une valeur Null si l’UPN de l’utilisateur est inconnu au moment de l’appel. Dans ce cas, les utilisateurs seront invités à entrer leur adresse e-mail et leur mot de passe.
      
      Si votre application utilise déjà la bibliothèque ADAL ou MSAL pour authentifier les utilisateurs, vous pouvez configurer une authentification unique (SSO) entre votre application et le SDK Intune. Pour commencer, vous devez configurer la bibliothèque ADAL/MSAL pour stocker les jetons dans le même groupe d’accès au trousseau qui est utilisé par les liaisons Xamarin d’Intune pour iOS (com.microsoft.adalcache). Pour la bibliothèque ADAL, [définissez la propriété KeychainSecurityGroup d’AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications). Pour la bibliothèque MSAL, [définissez la propriété KeychainSecurityGroup de PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios). Ensuite, vous devez remplacer les paramètres AAD par défaut utilisés par le kit SDK Intune par les paramètres de votre application. Vous pouvez le faire via le dictionnaire IntuneMAMSettings dans le fichier Info.plist de l’application, comme indiqué dans le [Guide du kit SDK d’application Intune pour les développeurs iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), ou vous pouvez utiliser les propriétés de substitution AAD de l’instance IntuneMAMPolicyManager. L’approche Info.plist est recommandée pour les applications dont les paramètres ADAL sont statiques, tandis que les propriétés de substitution sont recommandées pour les applications qui déterminent ces valeurs lors de l’exécution. Une fois que tous les paramètres de l’authentification unique ont été configurés, votre application doit fournir l’UPN de l’utilisateur à la méthode RegisterAndEnrollAccount d’IntuneMAMEnrollmentManager une fois l’authentification réussie :
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      Les applications peuvent déterminer le résultat d’une tentative d’inscription en implémentant la méthode EnrollmentRequestWithStatus dans une sous-classe d’IntuneMAMEnrollmentDelegate et en définissant la propriété Delegate d’IntuneMAMEnrollmentManager sur une instance de cette classe. Pour obtenir un exemple, consultez notre [exemple d’application Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

      Une fois que l’inscription a réussi, les applications peuvent déterminer l’UPN du compte inscrit (si cet UPN était inconnu) en interrogeant la propriété suivante : 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> Il n’existe pas de remappeur pour iOS. L’intégration dans une application Xamarin.Forms doit être la même que pour un projet Xamarin.iOS normal. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Activation de stratégies de protection des applications Intune dans votre application mobile Android

Pour les applications Android basées sur Xamarin qui n’utilisent pas un framework d’interface utilisateur, vous devez lire et suivre le [Guide du kit SDK d’application Intune pour les développeurs Android](app-sdk-android.md). Pour votre application Android basée sur Xamarin, vous devez remplacer la classe, les méthodes et les activités par leurs équivalents GAM conformément au [tableau des remplacements de classe et de méthode](app-sdk-android.md#class-and-method-replacements) inclus dans le guide. Si votre application ne définit pas de classe `android.app.Application`, vous devez en créer une et vérifier que vous héritez de `MAMApplication`. Les valeurs de configuration ADAL sont communiquées au SDK par le biais de métadonnées AndroidManifest. Lisez notre documentation sur la [configuration d’ADAL pour votre application](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="xamarinandroid-integration"></a>Intégration de Xamarin.Android

1. Ajoutez la dernière version du [paquet NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) à votre projet Xamarin.Android. Vous disposerez ainsi des références nécessaires à Intune pour activer votre application.

2. Lisez et suivez le [Guide du kit SDK d’application Intune pour les développeurs Android](app-sdk-android.md) en intégralité. Soyez particulièrement attentifs aux sections suivantes :

    1. [Remplacement des classes et des méthodes](app-sdk-android.md#class-and-method-replacements). 
    2. [MAMApplication](app-sdk-android.md#mamapplication). Vérifiez que votre sous-classe est correctement décorée avec l’attribut `[Application]` et qu’elle se substitue au constructeur `(IntPtr, JniHandleOwnership)`.
    3. [Intégration à ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) si votre application effectue l’authentification auprès d’AAD. 
    4. [Inscription à MAM-WE](app-sdk-android.md#app-protection-policy-without-device-enrollment) si vous prévoyez d’obtenir une stratégie à partir du service MAM dans votre application.

> [!NOTE]
> Quand vous tentez de trouver des API équivalentes à partir du [Guide du SDK d’application Intune pour les développeurs Android](app-sdk-android.md) dans les liaisons `Microsoft.Intune.MAM.Xamarin.Android`, ou quand vous convertissez des extraits de code à partir du guide, sachez que le générateur de liaisons de Xamarin modifie les API Android comme suit :
> * Tous les identificateurs sont convertis en casse Pascal (com.foo.bar -> Com.Foo.Bar)
> * Toutes les opérations get/set sont converties en opérations de propriété (par exemple, Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Les noms de toutes les interfaces sont précédés du caractère « I » (FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Intégration de Xamarin.Forms

**En plus des étapes ci-dessus**, nous fournissons le paquet `Xamarin.Forms` pour les applications `Microsoft.Intune.MAM.Remapper`. Ce paquet accomplit pour vous le remplacement de classe en injectant des classes `MAM` dans la hiérarchie des classes `Xamarin.Forms` couramment utilisées comme `FormsAppCompatActivity` et `FormsApplicationActivity`. Vous pouvez donc continuer à utiliser ces classes en fournissant des substitutions pour les fonctions MAM équivalentes comme `OnMAMCreate` et `OnMAMResume`. Pour l’utiliser, procédez comme suit :

1.  Ajoutez le paquet NuGet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) à votre projet. Des liaisons Xamarin du SDK d’application Intune sont automatiquement ajoutées si elle n’ont pas déjà été incluses.

2.  Ajoutez un appel à `Xamarin.Forms.Forms.Init(Context, Bundle)` dans la fonction `OnMAMActivity` de la classe `MAMApplication` que vous avez créée à l’étape 2.2 ci-dessus. Cette opération est nécessaire, car avec Intune, la gestion de votre application peut être démarrée en arrière-plan.

> [!NOTE]
> Étant donné que cette opération réécrit une dépendance que Visual Studio utilise pour la saisie semi-automatique Intellisense, vous devrez peut-être redémarrer Visual Studio après la première exécution du remappeur pour qu’Intellisense reconnaisse correctement les changements. 

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Exigence de stratégies de protection d’application Intune afin d’utiliser votre application métier Android basée sur Xamarin (facultatif) 

Vous pouvez suivre les conseils ci-dessous pour que seuls les utilisateurs protégés par Intune puissent utiliser des applications métier Android basées sur Xamarin sur leur appareil. 
    
### <a name="working-with-the-intune-sdk"></a>Utilisation du kit SDK Intune
Ces instructions sont spécifiques à toutes les applications Android et Xamarin qui souhaitent exiger des stratégies de protection des applications Intune à utiliser sur l’appareil d’un utilisateur final.

1. Configurez la bibliothèque ADAL à l’aide de la procédure définie dans le [Guide du Kit SDK de l’application Microsoft Intune pour les développeurs Android](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).
> [!NOTE] 
> Le terme « ID client » est le même que le terme « ID d’application » du portail Azure associé à votre application. 
* Pour activer l’authentification unique, la configuration numéro 2 dans « Configurations ADAL courantes » est celle dont vous avez besoin.

2. Activez l’inscription par défaut en insérant la valeur suivante dans le manifeste : ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> Il doit s’agir de la seule intégration MAM-WE dans l’application. Si d’autres tentatives sont effectuées pour appeler des API MAMEnrollmentManager, des conflits peuvent se produire.

3. Activez la stratégie GAM requise en insérant la valeur suivante dans le manifeste : ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> Cela oblige les applications à télécharger l’application Portail d’entreprise sur l’appareil et à effectuer le flux d’inscription par défaut avant utilisation.

### <a name="working-with-adal"></a>Utilisation d’ADAL
Vous devez suivre ces instructions pour les applications .NET/Xamarin qui souhaitent exiger des stratégies de protection des applications Intune à utiliser sur l’appareil d’un utilisateur final.

1. Suivez toutes les étapes définies dans la documentation ADAL sous [Authentification répartie pour Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android).

## <a name="potential-compilation-errors"></a>Erreurs de compilation potentielles
Voici quelques-unes des erreurs de compilation couramment rencontrées durant le développement d’une application basée sur Xamarin.

* [Erreur du compilateur CS0239](https://docs.microsoft.com/en-us/dotnet/csharp/misc/cs0239) : cette erreur apparaît couramment dans ce formulaire ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Quand le remappeur modifie l’héritage des classes Xamarin, certaines fonctions sont rendues `sealed` et une nouvelle variante MAM est ajoutée au remplacement à la place. Renommez simplement vos remplacements comme décrit [ici](https://docs.microsoft.com/en-us/intune/app-sdk-android#renamed-methods). Par exemple `MainActivity.OnCreate()` est renommé `MainActivity.OnMAMCreate()`

* [Erreur du compilateur CS0507](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-messages/cs0507) : cette erreur apparaît couramment dans ce formulaire ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Comme l’outil de remappage change l’héritage de certaines classes Xamarin, certaines fonctions membres sont changées en `public`. Si vous remplacez l’une de ces fonctions, vous devrez peut-être changer ces remplacements pour qu’ils soient également `public`.

## <a name="support"></a>Prise en charge
Si votre organisation est déjà un client Intune, contactez votre conseiller du support Microsoft pour ouvrir un ticket de support et créer un enregistrement [dans la page des problèmes GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Nous vous aiderons dès que possible. 
