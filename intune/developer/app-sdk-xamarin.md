---
title: Liaisons Xamarin du kit SDK d’application Microsoft Intune
description: Les liaisons Xamarin du kit SDK d’application Intune activent la stratégie de protection des applications Intune dans les applications iOS et Android générées avec Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10f3d4c54d9a8fcb797ae3359b1a833ac9080548
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912697"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Liaisons Xamarin du kit SDK d’application Microsoft Intune

> [!NOTE]
> Vous pouvez d’abord lire l’article [Bien démarrer avec le SDK d’application Intune](app-sdk-get-started.md), qui explique comment préparer l’intégration sur chaque plateforme prise en charge.

## <a name="overview"></a>Vue d’ensemble
Les [liaisons Xamarin du kit SDK d’application Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) activent la [stratégie de protection des applications Intune](../apps/app-protection-policy.md) dans les applications iOS et Android générées avec Xamarin. Les liaisons permettent aux développeurs de générer facilement des fonctionnalités de protection des applications Intune dans leur application Xamarin.

Les liaisons Xamarin du kit SDK d’application Microsoft Intune vous permettent d’incorporer des stratégies de protection des applications Intune (également appelées stratégies APP ou MAM) dans vos applications développées avec Xamarin. Une application MAM est une application intégrée au SDK des applications Intune. Les administrateurs informatiques peuvent déployer des stratégies de protection des applications sur votre application mobile quand celle-ci est activement gérée par Intune.

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

Consultez les [termes du contrat de licence](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Imprimez et conservez une copie des termes du contrat de licence pour vos archives. En téléchargeant et en utilisant les liaisons Xamarin du kit SDK d’application Intune, vous acceptez les termes du contrat de licence. Si vous ne les acceptez pas, n’utilisez pas le logiciel.

Le SDK Intune s’appuie sur la [Bibliothèque d’authentification Active Directory (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) pour ses scénarios [d’authentification](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) et de lancement conditionnel, ce qui nécessite que les applications soient configurées avec [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Si votre application est déjà configurée pour utiliser la bibliothèque ADAL ou MSAL et que son propre ID client personnalisé permet l’authentification auprès d’Azure Active Directory, vérifiez que les étapes pour accorder à votre application Xamarin des autorisations vis-à-vis du service de gestion des applications mobiles (MAM) Intune sont respectées. Suivez les instructions de la section « [Autoriser votre application à accéder au service de protection d’application Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional) » de [Prise en main du guide du SDK Intune](app-sdk-get-started.md).

## <a name="security-considerations"></a>Considérations relatives à la sécurité

Pour empêcher l'usurpation d'identité, la divulgation d'informations et les attaques par élévation de privilège, procédez comme suit :

* Vérifiez que le développement d’applications Xamarin est effectué sur une station de travail sécurisée.
* Vérifiez que les liaisons proviennent d’une source Microsoft valide :
  * [Profil NuGet MS Intune App SDK](https://www.nuget.org/profiles/msintuneappsdk)
  * [Dépôt GitHub Xamarin Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* Configurez votre configuration NuGet pour que votre projet approuve les packages NuGet signés et non modifiés.
Pour plus d’informations, consultez [Installation de packages signés](https://docs.microsoft.com/nuget/consume-packages/installing-signed-packages).
* Sécurisez le répertoire de sortie contenant l’application Xamarin. Envisagez d'utiliser un répertoire au niveau utilisateur pour la sortie.


## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Activation des stratégies de protection des applications Intune dans votre application mobile iOS
1. Ajoutez le paquet NuGet [Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) à votre projet Xamarin.iOS.
2. Suivez les étapes générales requises pour l’intégration du Kit SDK d’application Intune dans une app mobile iOS. Vous pouvez commencer à l’étape 3 des instructions de l’intégration dans le [Guide du kit SDK d’application Intune pour les développeurs iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Vous pouvez ignorer l’étape finale indiquée dans cette section sur l’exécution de l’outil IntuneMAMConfigurator, car il est inclus dans le package Microsoft.Intune.MAM.Xamarin.iOS et il s’exécute automatiquement au moment de la génération.
    **Important** : l’activation du partage de trousseau pour une application est légèrement différente dans Visual Studio par rapport à Xcode. Ouvrez le fichier plist de droits de l’application et vérifiez que l’option « Activer le trousseau » est activée et que les groupes de partage de trousseau appropriés sont ajoutés dans cette section. Vérifiez ensuite que le fichier plist des droits est spécifié dans le champ « Droits personnalisés » des options « Signature du bundle iOS » du projet pour toutes les combinaisons de configuration/plate-forme appropriées.
3. Une fois les liaisons ajoutées et l’application correctement configurée, celle-ci peut commencer à utiliser les API du kit SDK Intune. Pour cela, vous devez inclure l’espace de noms suivant :

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Pour commencer à recevoir des stratégies de protection d’application, votre application doit s’inscrire auprès du service MAM Intune. Si votre application n’utilise pas la [bibliothèque d’authentification Azure Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) ou la [bibliothèque d’authentification Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) pour authentifier les utilisateurs, et souhaitez que le SDK Intune gère l’authentification, votre application doit fournir l’UPN de l’utilisateur à la méthode LoginAndEnrollAccount d’IntuneMAMEnrollmentManager :

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      Les applications peuvent passer une valeur Null si l’UPN de l’utilisateur est inconnu au moment de l’appel. Dans ce cas, les utilisateurs seront invités à entrer leur adresse e-mail et leur mot de passe.
      
      Si votre application utilise déjà la bibliothèque ADAL ou MSAL pour authentifier les utilisateurs, vous pouvez configurer une authentification unique (SSO) entre votre application et le SDK Intune. Vous devez d’abord remplacer les paramètres AAD par défaut utilisés par le kit SDK Intune par les paramètres de votre application. Vous pouvez le faire via le dictionnaire IntuneMAMSettings dans le fichier Info.plist de l’application, comme indiqué dans le [Guide du kit SDK d’application Intune pour les développeurs iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), ou dans le code via les propriétés de substitution AAD de la classe IntuneMAMSettings. L’approche Info.plist est recommandée pour les applications dont les paramètres ADAL sont statiques, tandis que les propriétés de substitution sont recommandées pour les applications qui déterminent ces valeurs lors de l’exécution. Une fois que tous les paramètres de l’authentification unique ont été configurés, votre application doit fournir l’UPN de l’utilisateur à la méthode RegisterAndEnrollAccount d’IntuneMAMEnrollmentManager une fois l’authentification réussie :

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      Les applications peuvent déterminer le résultat d’une tentative d’inscription en implémentant la méthode EnrollmentRequestWithStatus dans une sous-classe d’IntuneMAMEnrollmentDelegate et en définissant la propriété Delegate d’IntuneMAMEnrollmentManager sur une instance de cette classe. 

      Une fois que l’inscription a réussi, les applications peuvent déterminer l’UPN du compte inscrit (si cet UPN était inconnu) en interrogeant la propriété suivante : 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>Exemples d'applications
Des exemples d’applications mettant en évidence les fonctionnalités MAM dans des applications Xamarin.iOS sont disponibles sur [GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

> [!NOTE] 
> Il n’existe pas de remappeur pour iOS. L’intégration dans une application Xamarin.Forms doit être la même que pour un projet Xamarin.iOS normal. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Activation de stratégies de protection des applications Intune dans votre application mobile Android
1. Ajoutez le paquet NuGet [Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) à votre projet Xamarin.Android.
    1. Pour une application Xamarin.Forms, ajoutez le [package NuGet Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) à votre projet Xamarin.Android. 
2. Suivez les étapes générales nécessaires pour [l’intégration du SDK d’application Intune](app-sdk-android.md) dans une application mobile Android tout en vous référant à ce document pour des informations plus détaillées.

### <a name="xamarinandroid-integration"></a>Intégration de Xamarin.Android

Vous trouverez une présentation complète d’intégration du SDK d’application Intune dans le [Guide du kit SDK d’application Microsoft Intune pour les développeurs Android](app-sdk-android.md). Quand vous lisez le guide et que vous intégrez le SDK d’application Intune à votre application Xamarin, vous pouvez noter que les sections suivantes sont destinées à mettre en évidence les différences entre l’implémentation pour une application Android native développée en Java et une application Xamarin développée en C#. Ces sections doivent être traitées comme venant en complément et non pas comme substitut de la lecture du guide dans son intégralité.

#### <a name="remapper"></a>Remappeur
À compter de la version 1.4428.1, le package `Microsoft.Intune.MAM.Remapper` peut être ajouté à une application Xamarin.Android en tant qu’[outils de génération](app-sdk-android.md#build-tooling) pour effectuer les remplacements de classe, de méthode et des services système MAM. Si le remappeur est inclus, les parties de remplacement équivalentes MAM des sections Méthodes renommées et Application MAM seront automatiquement exécutées lors de la génération de l’application.

Pour exclure une classe de la transformation MAM par le remappeur, la propriété suivante peut être ajoutée dans le fichier `.csproj` de vos projets.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> Le remappeur empêche actuellement le débogage dans les applications Xamarin.Android. L’intégration manuelle est recommandée pour déboguer votre application.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Méthodes renommées](app-sdk-android.md#renamed-methods)
Dans de nombreux cas, une méthode disponible dans la classe Android a été marquée comme finale dans la classe de remplacement MAM. Dans ce cas, la classe de remplacement MAM fournit une méthode portant un nom similaire (avec le suffixe `MAM`) que vous devez remplacer. Par exemple, quand vous dérivez de `MAMActivity` au lieu de remplacer `OnCreate()` et d’appeler `base.OnCreate()`, `Activity` doit remplacer `OnMAMCreate()` et appeler `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Application MAM](app-sdk-android.md#mamapplication)
Votre application doit définir une classe `Android.App.Application`. Si vous intégrez manuellement MAM, elle doit hériter de `MAMApplication`. Vérifiez que votre sous-classe est correctement décorée avec l’attribut `[Application]` et qu’elle se substitue au constructeur `(IntPtr, JniHandleOwnership)`.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> Un problème avec les liaisons Xamarin MAM peut entraîner le plantage de l’application lors d’un déploiement en mode de débogage. Une solution de contournement consiste à ajouter l’attribut `Debuggable=false` à la classe `Application` et à supprimer l’indicateur `android:debuggable="true"` dans le manifeste s’il a été défini manuellement.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Activer les fonctionnalités qui nécessitent la participation de l’application](app-sdk-android.md#enable-features-that-require-app-participation)
Exemple : Déterminer si le code PIN est nécessaire pour l’application

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

Exemple : Déterminer l’utilisateur Intune principal

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

Exemple : Déterminer si l’enregistrement sur l’appareil ou le stockage cloud est autorisé

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[S’inscrire aux notifications depuis le Kit de développement logiciel (SDK)](app-sdk-android.md#register-for-notifications-from-the-sdk)
Votre application doit s’inscrire aux notifications en provenance du kit de développement logiciel (SDK) en créant un `MAMNotificationReceiver` et en l’inscrivant auprès de `MAMNotificationReceiverRegistry`. Vous devez fournir le récepteur et le type de notification souhaité dans `App.OnMAMCreate`, comme l’illustre l’exemple ci-dessous :

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Gestionnaire d’inscription MAM](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Intégration de Xamarin.Forms

Pour les applications `Xamarin.Forms`, le package `Microsoft.Intune.MAM.Remapper` effectue automatiquement le remplacement de la classe MAM en injectant des classes `MAM` dans la hiérarchie des classes des classes `Xamarin.Forms` couramment utilisées. 

> [!NOTE]
> L’intégration de Xamarin.Forms doit être effectuée en plus de l’intégration de Xamarin.Android détaillée plus haut. Le remappeur se comporte différemment pour les applications Xamarin.Forms : les remplacements MAM manuels doivent donc toujours être effectués.

Une fois que le remappeur est ajouté à votre projet, vous devez effectuer les remplacements MAM équivalents. Par exemple, `FormsAppCompatActivity` et `FormsApplicationActivity` peuvent continuer à être utilisés dans votre application, à condition que les remplacements fournis à `OnCreate` et à `OnResume` soient remplacés par les équivalents MAM `OnMAMCreate` et `OnMAMResume`, respectivement.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

Si les remplacements ne sont pas effectués, vous pouvez rencontrer les erreurs de compilation suivantes tant qu’ils ne sont pas faits :
* [Erreur du compilateur CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). cette erreur apparaît couramment dans ce formulaire ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
C’est normal puisque quand le remappeur modifie l’héritage des classes Xamarin, certaines fonctions deviennent `sealed` et une nouvelle variante de gestion des applications mobiles est ajoutée au remplacement à la place.
* [Erreur du compilateur CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507) : cette erreur apparaît couramment dans ce formulaire ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Lorsque l’outil de remappage change l’héritage de certaines classes Xamarin, certaines fonctions membres sont changées en `public`. Si vous remplacez une de ces fonctions, vous devez aussi changer ces modificateurs d’accès pour ces remplacements en `public`.

> [!NOTE]
> Le remappeur réécrit une dépendance que Visual Studio utilise pour l’autocomplétion IntelliSense. Ainsi, il peut être nécessaire de recharger et de regénérer le projet quand le remappeur est ajouté, pour qu’IntelliSense reconnaisse correctement les modifications.

#### <a name="troubleshooting"></a>Résolution des problèmes
* Si vous rencontrez un écran vide et blanc dans votre application lors du lancement, il peut être nécessaire de forcer les appels de navigation à s’exécuter sur le thread principal.
* Les liaisons Xamarin du SDK Intune ne prennent pas en charge les applications qui utilisent une infrastructure multiplateforme, comme MvvmCross, en raison de conflits entre les classes MvvmCross et MAM Intune. Bien que certains clients aient pu réussir l’intégration après avoir déplacé leurs applications vers Xamarin.Forms, nous ne fournissons pas de conseils explicites ou de plug-ins pour les développeurs d’applications utilisant MvvmCross.

### <a name="company-portal-app"></a>Application Portail d’entreprise
Les liaisons Xamarin du SDK Intune s’appuient sur la présence de l’application Android [Portail d’entreprise](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) sur l’appareil pour activer les stratégies de protection des applications. Le portail d’entreprise récupère les stratégies de protection des applications à partir du service Intune. Quand l’application s’initialise, elle charge la stratégie et le code pour appliquer cette stratégie à partir du portail d’entreprise. L’utilisateur n’a pas besoin d’être connecté.

> [!NOTE]
> Quand l’application Portail d’entreprise n’est pas sur l’appareil **Android**, une application gérée par Intune se comporte comme une application normale qui ne prend pas en charge les stratégies de protection des applications Intune.

Pour la protection des applications sans inscription des appareils, l’utilisateur n’est _**pas**_ obligé d’inscrire l’appareil à l’aide de l’application Portail d’entreprise.

### <a name="sample-applications"></a>Exemples d'applications
Des exemples d’applications mettant en évidence les fonctionnalités MAM dans Xamarin.Android et Xamarin.Forms sont disponibles sur [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Assistance
Si votre organisation est déjà un client Intune, contactez votre conseiller du support Microsoft pour ouvrir un ticket de support et créer un enregistrement [dans la page des problèmes GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Nous vous aiderons dès que possible. 
