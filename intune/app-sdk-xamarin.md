---
title: Liaisons Xamarin du kit SDK d’application Microsoft Intune
description: Les liaisons Xamarin du kit SDK d’application Intune activent la stratégie de protection des applications Intune dans les applications iOS et Android générées avec Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d42fab929d6fa3e7fbaed8e9557573ebbaa1f3ad
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292348"
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
    **Important** : l’activation du partage de trousseau pour une application est légèrement différente dans Visual Studio par rapport à Xcode. Ouvrez le fichier plist de droits de l’application et vérifiez que l’option « Activer le trousseau » est activée et que les groupes de partage de trousseau appropriés sont ajoutés dans cette section. Vérifiez ensuite que le fichier plist des droits est spécifié dans le champ « Droits personnalisés » des options « Signature du bundle iOS » du projet pour toutes les combinaisons de configuration/plate-forme appropriées.
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

1. Ajoutez le paquet NuGet [Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) à votre projet Xamarin.Android.
    1. Pour une application Xamarin.Forms, ajoutez le [package NuGet de Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) à votre projet Xamarin.Android. 
2. Suivez les étapes générales requises pour [l’intégration du SDK d’application Intune](app-sdk-android.md) dans une application mobile Android la référence à ce document pour plus d’informations.

### <a name="xamarinandroid-integration"></a>Intégration de Xamarin.Android

Vous trouverez une présentation complète d’intégration du SDK d’application Intune dans le [Microsoft Intune App SDK for guide du développeur Android](app-sdk-android.md). Lorsque vous lisez le guide et intégrez le SDK d’application Intune à votre application Xamarin les sections suivantes sont destinées à mettre en évidence les différences entre l’implémentation pour une application Android native développé en Java et d’une application Xamarin développées dans C#. Ces sections doivent être traitées comme supplémentaires et ne peut pas agir comme un substitut pour lire le guide dans son intégralité.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Méthodes renommées](app-sdk-android.md#renamed-methods)
Dans de nombreux cas, une méthode disponible dans la classe Android a été marquée comme finale dans la classe de remplacement GAM. Dans ce cas, la classe de remplacement GAM fournit une méthode portant un nom similaire (avec le suffixe `MAM`) que vous devez remplacer. Par exemple, quand vous dérivez de `MAMActivity` au lieu de remplacer `OnCreate()` et d’appeler `base.OnCreate()`, `Activity` doit remplacer `OnMAMCreate()` et appeler `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Application de gestion des applications mobiles](app-sdk-android.md#mamapplication)
Votre application doit définir un `Android.App.Application` classe qui hérite de `MAMApplication`. Vérifiez que votre sous-classe est correctement décorée avec l’attribut `[Application]` et qu’elle se substitue au constructeur `(IntPtr, JniHandleOwnership)`.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> Un problème avec les liaisons de la gestion des applications mobiles Xamarin peut entraîner l’application à se bloquer lors du déploiement en mode débogage. Pour résoudre ce problème, le `Debuggable=false` attribut doit être ajouté à la `Application` classe et le `android:debuggable="true"` indicateur doit être supprimé à partir du manifeste si elle a été définie manuellement.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Activer les fonctionnalités qui nécessitent la participation de l’application](app-sdk-android.md#enable-features-that-require-app-participation)
Exemple : Déterminer si le code PIN est nécessaire pour l’application
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

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Gestionnaire d’inscription de gestion des applications mobiles](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Intégration de Xamarin.Forms

Pour `Xamarin.Forms` applications que nous avons fourni le `Microsoft.Intune.MAM.Remapper` package pour effectuer automatiquement de remplacement de la classe GAM en injectant `MAM` des classes dans la hiérarchie de classes d’objets couramment utilisés `Xamarin.Forms` classes. 

> [!NOTE]
> L’intégration de Xamarin.Forms consiste à le faire en outre à l’intégration de Xamarin.Android détaillée plus haut.

Une fois que le Remapper est ajouté à votre projet, vous devrez effectuer les remplacements équivalents GAM. Par exemple, `FormsAppCompatActivity` et `FormsApplicationActivity` peuvent continuer à utiliser dans vos remplacements application fournie à `OnCreate` et `OnResume` sont remplacés par les équivalents GAM `OnMAMCreate` et `OnMAMResume` respectivement.

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
Si les remplacements ne sont pas apportées vous pouvez rencontrer les erreurs de compilation suivantes jusqu'à ce que vous effectuez les remplacements :
* [Erreur du compilateur CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). cette erreur apparaît couramment dans ce formulaire ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
C’est normal puisque quand le remappeur modifie l’héritage des classes Xamarin, certaines fonctions deviennent `sealed` et une nouvelle variante de gestion des applications mobiles est ajoutée au remplacement à la place.
* [Erreur du compilateur CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): cette erreur se produite souvent dans ce formulaire ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Lorsque l’outil de remappage change l’héritage de certaines classes Xamarin, certaines fonctions membres sont changées en `public`. Si vous substituez une de ces fonctions, vous devrez modifier ces modificateurs d’accès pour les remplacements pour être `public` également.

> [!NOTE]
> Le Remapper réécrit de façon unique une dépendance que Visual Studio utilise pour la saisie automatique IntelliSense. Par conséquent, vous devrez peut-être recharger et régénérez le projet lors de l’ajout d’IntelliSense pour reconnaître correctement les modifications le Remapper.

## <a name="support"></a>Prise en charge
Si votre organisation est déjà un client Intune, contactez votre conseiller du support Microsoft pour ouvrir un ticket de support et créer un enregistrement [dans la page des problèmes GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Nous vous aiderons dès que possible. 
