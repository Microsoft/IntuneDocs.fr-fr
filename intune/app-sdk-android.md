---
title: "Guide du Kit SDK de l’application Microsoft Intune pour les développeurs Android"
description: "Le SDK d’application Microsoft Intune pour Android vous permet d’incorporer la gestion des applications mobiles Intune à votre application Android."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 403917adb1fb1156f0ed0027a316677d1e4f2f84
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2017
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guide du Kit SDK de l’application Microsoft Intune pour les développeurs Android

> [!NOTE]
> Vous pouvez d’abord consulter la [Présentation du SDK de l’application Intune](app-sdk.md), qui aborde les fonctionnalités actuelles du SDK et la manière de préparer l’intégration sur chaque plateforme prise en charge.

Le Kit de développement logiciel SDK (SDK) d’application Microsoft Intune pour Android vous permet d’incorporer des stratégies de protection des applications Intune (également appelées stratégies **APP** ou GAM) dans votre application Android native. Une application compatible avec Intune est une application intégrée au SDK d’application Intune. Les administrateurs Intune peuvent facilement déployer des stratégies de protection des applications sur votre application compatible avec Intune quand Intune gère activement l’application.


## <a name="whats-in-the-sdk"></a>Contenu du SDK

Le SDK d’application Intune se compose des fichiers suivants :  

* **Microsoft.Intune.MAM.SDK.aar** : composants du SDK, à l’exception des fichiers JAR Support.V4 et Support.V7. Si votre système de génération prend en charge les fichiers AAR, ce fichier peut être utilisé à la place des composants individuels.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar** : interfaces nécessaires pour prendre en charge la gestion des applications mobiles dans les applications qui utilisent la bibliothèque de prise en charge v4 Android. Les applications nécessitant cette prise en charge doivent référencer directement le fichier JAR.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar** : interfaces nécessaires pour prendre en charge la gestion des applications mobiles dans les applications qui utilisent la bibliothèque de prise en charge v7 Android. Les applications nécessitant cette prise en charge doivent référencer directement le fichier JAR.
* **proguard.txt** : contient des règles ProGuard qui doivent être appliquées en cas de génération avec ProGuard.
* **CHANGELOG.txt** : contient un historique des modifications apportées dans chaque version du SDK.
* **THIRDPARTYNOTICES.TXT** : avis d’attribution qui reconnaît que le code tiers et/ou OSS sera compilé dans votre application.

Si votre système de génération ne prend pas en charge les fichiers AAR, vous pouvez utiliser les fichiers suivants à la place de Microsoft.Intune.MAM.SDK.aar.
* **Microsoft.Intune.MAM.SDK.jar** : interfaces nécessaires pour prendre en charge la gestion des applications mobiles, ainsi que l’interopérabilité avec l’application Portail d’entreprise Intune. Les applications doivent spécifier ce fichier en tant que référence de bibliothèque Android.
* **Répertoire res** : ressources (telles que des chaînes) sur lesquelles repose le SDK.
* **AndroidManifest.xml** : points d’entrée et exigences de la bibliothèque.


## <a name="requirements"></a>Configuration requise

Le SDK de l’application Intune est un projet Android compilé. Ainsi, il est en grande partie non affecté par la version d’Android utilisée par l’application pour ses versions d’API (minimale ou cible). Le SDK prend en charge Android API 14 (Android 4.0 +) et Android API 25 (Android 7.1).



### <a name="company-portal-app"></a>Application Portail d’entreprise
Le SDK d’application Intune pour Android repose sur la présence de l’application [Portail d’entreprise](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) sur l’appareil pour activer les stratégies de protection des applications. Le portail d’entreprise récupère les stratégies de protection des applications à partir du service Intune. Quand l’application s’initialise, elle charge la stratégie et le code pour appliquer cette stratégie à partir du portail d’entreprise.

> [!NOTE]
> Quand l’application Portail d’entreprise n’est pas sur l’appareil, une application compatible avec Intune se comporte comme une application normale qui ne prend pas en charge les stratégies de protection des applications Intune.

Pour la protection des applications sans inscription des appareils, l’utilisateur n’est _**pas**_ obligé d’inscrire l’appareil à l’aide de l’application Portail d’entreprise.

## <a name="sdk-integration"></a>Intégration du SDK

### <a name="build-integration"></a>Intégration de build

Le SDK d’application Intune pour Android est une bibliothèque Android standard sans dépendances externes. **Microsoft.Intune.MAM.SDK.jar** contient les interfaces nécessaires pour l’activation d’une stratégie de protection des applications et le code nécessaire pour interagir avec l’application Portail d’entreprise Microsoft Intune.

Vous devez spécifier **Microsoft.Intune.MAM.SDK.jar** en tant que référence de bibliothèque Android. Pour ce faire, ouvrez votre projet d’application dans Android Studio et accédez à **File > New > New module** et sélectionnez **Import .JAR/.AAR Package**. Sélectionnez notre package d’archive Android Microsoft.Intune.MAM.SDK.aar.

En outre, **Microsoft.Intune.MAM.SDK.Support.v4** et **Microsoft.Intune.MAM.SDK.Support.v7** contiennent respectivement des variantes Intune de `android.support.v4` et `android.support.v7`. Ils ne sont pas intégrés à Microsoft.Intune.MAM.SDK.aar, pour le cas où une application ne souhaiterait pas inclure les bibliothèques de prise en charge. Il s’agit de fichiers JAR standard plutôt que de projets de bibliothèque Android.

#### <a name="proguard"></a>ProGuard

Si [ProGuard](http://proguard.sourceforge.net/) (ou tout autre mécanisme de réduction/obscurcissement) est utilisé comme étape de génération, les classes du SDK Intune doivent être exclues. Pour ProGuard, vous pouvez pour cela inclure les règles à partir du fichier proguard.txt distribué avec le SDK.

La bibliothèque d’authentification ADAL (Azure Active Directory Authentication Library) peut avoir ses propres restrictions ProGuard. Si votre application intègre la bibliothèque ADAL, vous devez suivre la documentation ADAL concernant ces restrictions.

### <a name="entry-points"></a>Points d’entrée

La bibliothèque d’authentification Azure Active Directory ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) exige ces autorisations pour effectuer l’authentification répartie. Si ces autorisations ne sont pas accordées à l’application ou qu’elles sont révoquées par l’utilisateur, les flux d’authentification qui requièrent le service broker (l’application Portail d’entreprise) sont désactivés.

Le SDK d’application Intune nécessite la modification du code source d’une application pour permettre l’activation des stratégies de protection des applications Intune. Pour cela, vous devez remplacer les classes de base Android par des classes de base Intune équivalentes, dont les noms portent le préfixe **MAM**. Les classes du SDK résident entre la classe de base Android et la propre version dérivée de cette classe de l’application. Si vous prenez l’exemple d’une activité, vous vous retrouvez avec une hiérarchie d’héritage qui ressemble à ceci : `Activity` > `MAMActivity` > `AppSpecificActivity`.

Par exemple, quand `AppSpecificActivity` interagit avec son parent (par exemple, un appel à `super.onCreate()`), `MAMActivity` est la super classe.

Les applications Android classiques ont un seul mode et peuvent accéder au système par l’intermédiaire de leur objet [**Context**](https://developer.android.com/reference/android/content/Context.html). En revanche, les applications qui intègrent le SDK d’application Intune ont deux modes. Ces applications continuent à accéder au système par le biais de l’objet `Context`. En fonction de l’`Activity` de base utilisée, l’objet `Context` sera fourni par Android ou sera multiplexé intelligemment entre une vue restreinte du système et le `Context` fourni par Android.


## <a name="replace-classes-methods-and-activities-with-their-mam-equivalent"></a>Remplacer les classes, méthodes et activités par leurs équivalents GAM

Les classes de base Android doivent être remplacées par leurs équivalents GAM respectifs. Pour ce faire, recherchez toutes les instances des classes répertoriées dans le tableau suivant et remplacez-les par leur équivalent dans le SDK de l’application Intune.

| Classe de base Android | Classe de remplacement (SDK de l’application Intune) |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (voir les remarques ci-dessous) |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (nécessaire uniquement si le Binder n’est pas généré à partir d’une interface AIDL (Android Interface Definition Language)) |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar :

| Classe Android (MAM Intune) | Classe de remplacement (SDK de l’application Intune) |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar :

|Classe Android | Classe de remplacement (SDK de l’application Intune) |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


### <a name="renamed-methods"></a>Méthodes renommées
Une fois que vous avez dérivé de l’un des points d’entrée GAM, vous pouvez sans risque utiliser `Context` comme vous le feriez normalement (par exemple, démarrer des classes `Activity` et utiliser `PackageManager`).

Dans de nombreux cas, une méthode disponible dans la classe Android a été marquée comme finale dans la classe de remplacement GAM. Dans ce cas, la classe de remplacement GAM fournit une méthode portant un nom similaire (généralement avec le suffixe `MAM`) que vous devez remplacer. Par exemple, quand vous dérivez de `MAMActivity` au lieu de remplacer `onCreate()` et d’appeler `super.onCreate()`, `Activity` doit remplacer `onMAMCreate()` et appeler `super.onMAMCreate()`. Le compilateur Java doit appliquer les restrictions finales pour éviter que la méthode d’origine ne soit remplacée accidentellement à la place de l’équivalent GAM.

### <a name="pendingintent"></a>PendingIntent
Au lieu de `PendingIntent.get*`, vous devez utiliser la méthode `MAMPendingIntent.get*`. Après cela, vous pouvez utiliser la classe `PendingIntent` résultante comme d’habitude.

### <a name="manifest-replacements"></a>Remplacements de manifeste
Notez qu’il peut être nécessaire d’effectuer certains des remplacements de classe ci-dessus dans le manifeste, ainsi que dans le code Java. À noter en particulier :
* Les références de manifeste à `android.support.v4.content.FileProvider` doivent être remplacées par `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.


## <a name="sdk-permissions"></a>Autorisations du SDK

Le SDK d’application Intune nécessite trois [autorisations système Android](https://developer.android.com/guide/topics/security/permissions.html) sur les applications qui l’intègrent :

* `android.permission.GET_ACCOUNTS` (demandée au moment de l’exécution, si nécessaire)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

La bibliothèque d’authentification Azure Active Directory ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) exige ces autorisations pour effectuer l’authentification répartie. Si ces autorisations ne sont pas accordées à l’application ou qu’elles sont révoquées par l’utilisateur, les flux d’authentification qui requièrent le service broker (l’application Portail d’entreprise) sont désactivés.

## <a name="logging"></a>Journalisation

La journalisation doit être initialisée tôt afin de tirer le meilleur parti des données enregistrées. `Application.onMAMCreate()` est généralement le meilleur emplacement pour initialiser la journalisation.

Pour recevoir des journaux GAM dans votre application, créez un [gestionnaire Java](http://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) et ajoutez-le au `MAMLogHandlerWrapper`. `publish()` sera appelé sur le gestionnaire d’application pour chaque message de journal.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>Activer les fonctionnalités qui nécessitent la participation de l’application

Il existe plusieurs stratégies de protection des applications que le SDK ne peut pas implémenter seul. L’application peut contrôler son comportement pour avoir ces fonctionnalités à l’aide de plusieurs API que vous trouverez dans l’interface `AppPolicy` suivante.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}

```

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` retourne toujours une stratégie d’application non null, même si l’appareil ou l’application n’est pas placé sous une stratégie de gestion Intune.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Exemple : Déterminer si le code PIN est nécessaire pour l’application

Si l’application a sa propre expérience utilisateur de code PIN, vous souhaiterez peut-être la désactiver si l’administrateur informatique a configuré le SDK pour demander un code PIN d’application. Pour déterminer si l’administrateur informatique a déployé la stratégie de code PIN d’application sur cette application, pour l’utilisateur final actuel, appelez la méthode suivante :

```java
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Exemple : Déterminer l’utilisateur Intune principal

Outre les API exposées dans AppPolicy, le nom d’utilisateur principal (**UPN**) est également exposé par l’API `getPrimaryUser()` définie dans l’interface `MAMUserInfo`. Pour obtenir l’UPN, appelez ce qui suit :

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

Voici la définition complète de l’interface MAMUserInfo :

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Exemple : Déterminer si l’enregistrement sur l’appareil ou le stockage cloud est autorisé

Bon nombre d’applications implémentent des fonctionnalités permettant aux utilisateurs finaux d’enregistrer des fichiers localement ou dans un service de stockage cloud. Grâce au SDK de l’application Intune, les administrateurs informatiques peuvent se protéger contre les fuites de données en appliquant des restrictions de stratégie adaptées à leur organisation.  Parmi les stratégies dont il a le contrôle, l’administrateur informatique peut définir si l’utilisateur final est autorisé à enregistrer dans un magasin de données non géré « personnel ». (emplacement local, carte SD, services de sauvegarde tiers, etc.).

**La participation de l’application est nécessaire pour activer la fonctionnalité.** Si votre application permet d’enregistrer des données dans des emplacements personnels ou dans le cloud directement à partir de l’application, vous devez implémenter cette fonctionnalité de manière à ce que l’administrateur informatique puisse vérifier si l’enregistrement dans un emplacement est autorisé. L’API ci-dessous permet à l’application de savoir si l’enregistrement dans un magasin personnel est autorisé par la stratégie de l’administrateur Intune actuelle. L’application peut ensuite appliquer la stratégie puisqu’elle a connaissance du magasin de données personnel accessible à l’utilisateur final dans l’application.  

Pour déterminer si la stratégie est appliquée, effectuez l’appel suivant :

```java
MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

… où `service` est l’un des SaveLocations suivants :


    * SaveLocation.ONEDRIVE_FOR_BUSINESS
    * SaveLocation.LOCAL
    * SaveLocation.OTHER

La méthode précédente permettant de déterminer si la stratégie d’un utilisateur l’autorisait à enregistrer des données à différents emplacements était `getIsSaveToPersonalAllowed()` dans la même classe **AppPolicy**. Cette fonction est maintenant **dépréciée** et ne doit pas être utilisée. L’appel suivant équivaut à `getIsSaveToPersonalAllowed()` :

```java

MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> Utilisez `SaveLocation.OTHER` si l’emplacement en question n’est pas répertorié dans l’énumération **SaveLocations**.


## <a name="register-for-notifications-from-the-sdk"></a>S’inscrire aux notifications à partir du SDK

### <a name="overview"></a>Vue d’ensemble
Le SDK d’application Intune permet à votre application de contrôler le comportement de certaines stratégies, notamment la réinitialisation sélective, quand elles sont déployées par l’administrateur informatique. Quand un administrateur informatique déploie une stratégie de ce type, le service Intune envoie une notification au SDK.

Votre application doit s’inscrire aux notifications en provenance du SDK en créant un `MAMNotificationReceiver` et en l’inscrivant auprès de `MAMNotificationReceiverRegistry`. Vous devez fournir le récepteur et le type de notification souhaité dans `App.onCreate`, comme l’illustre l’exemple ci-dessous :

```java
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
        .registerReceiver(
            new ToastNotificationReceiver(),
            MAMNotificationType.WIPE_USER_DATA);
    }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

L’interface `MAMNotificationReceiver` reçoit simplement des notifications à partir du service Intune. Certaines notifications sont gérées directement par le SDK, tandis que d’autres nécessitent la participation de l’application. Une application **doit** retourner true ou false à la suite d’une notification. Elle doit toujours retourner true, sauf en cas d’échec d’une action entreprise après la notification.

* Cet échec peut être signalé au service Intune. C’est par exemple le cas si l’application ne peut pas réinitialiser les données de l’utilisateur après le lancement d’une réinitialisation par l’administrateur informatique.

>[!NOTE]
> Le blocage de `MAMNotificationReceiver.onReceive` peut se faire en toute sécurité, car son rappel n’est pas exécuté sur le thread de l’interface utilisateur.

L’interface `MAMNotificationReceiver` telle que définie dans le SDK est incluse ci-après :

```java
/**
 * The SDK is signaling that a MAM event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}

```

### <a name="types-of-notifications"></a>Types de notifications

Les notifications suivantes sont envoyées à l’application et certaines d’entre elles peuvent nécessiter la participation de l’application :

* **WIPE_USER_DATA** : cette notification est envoyée dans une classe `MAMUserNotification`. Quand cette notification est reçue, l’application est censée supprimer toutes les données associées à l’identité « d’entreprise » passée avec le `MAMUserNotification`. Cette notification est actuellement envoyée lors de l’annulation de l’inscription APP-WE. Le nom principal de l’utilisateur est généralement spécifié au cours du processus d’inscription. Si vous vous inscrivez à cette notification, votre application doit s’assurer que toutes les données de l’utilisateur ont été supprimées. Si vous ne vous inscrivez pas à cette notification, le comportement de réinitialisation sélective par défaut est adopté.

* **WIPE_USER_AUXILIARY_DATA** : les applications peuvent s’inscrire à cette notification si elles souhaitent que le SDK d’application Intune adopte le comportement de réinitialisation sélective par défaut, tout en ayant la possibilité de supprimer des données auxiliaires au moment de la réinitialisation.

* **REFRESH_POLICY** : cette notification est envoyée dans un `MAMUserNotification`. Quand cette notification est reçue, toute stratégie Intune mise en cache doit être invalidée et mise à jour. C’est généralement le SDK qui s’en charge ; toutefois, cette tâche peut revenir à l’application si la stratégie est utilisée de façon permanente.

* **MANAGEMENT_REMOVED** : cette notification est envoyée dans un `MAMUserNotification` et signale à l’application qu’elle est sur le point de devenir non gérée. Une fois non gérée, elle ne pourra plus lire les fichiers chiffrés, lire des données chiffrées avec MAMDataProtectionManager, interagir avec le Presse-papiers chiffré, ni participer à l’écosystème d’applications gérées.


> [!NOTE]
> Une application ne doit jamais s’inscrire à la fois pour les notifications `WIPE_USER_DATA` et `WIPE_USER_AUXILIARY_DATA`.


## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurer Azure Active Directory Authentication Library (ADAL)

Tout d’abord, lisez les instructions d’intégration de la bibliothèque ADAL dans le [dépôt ADAL sur GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

Le SDK s’appuie sur la bibliothèque [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) pour ses scénarios d’[authentification](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) et de lancement conditionnel, ce qui nécessite que les applications soient configurées avec [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). Les valeurs de configuration sont communiquées au SDK par le biais de métadonnées AndroidManifest.

Pour configurer votre application et mettre en œuvre une authentification approprié, ajoutez le code suivant au nœud de l’application dans AndroidManifest.xml. Certaines de ces configurations sont uniquement nécessaires si votre application utilise la bibliothèque ADAL pour l’authentification en général. Dans ce cas, vous avez besoin des valeurs spécifiques que votre application utilise pour s’inscrire auprès d’AAD. De cette façon, l’utilisateur final n’est pas invité à s’authentifier à deux reprises quand AAD détecte deux valeurs d’inscription distinctes : l’une provenant de l’application et l’autre du SDK.

```xml
<meta-data
    android:name="com.microsoft.intune.mam.aad.Authority"
    android:value="https://AAD authority/" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.ClientID"
    android:value="your-client-ID-GUID" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
    android:value="your-redirect-URI" />
<meta-data
    android:name="com.microsoft.intune.mam.aad.SkipBroker"
    android:value="[true | false]" />
```

### <a name="adal-metadata"></a>Métadonnées de la bibliothèque ADAL

* **Authority** est l’autorité AAD actuelle en cours d’utilisation. Si elle est présente, vous devez utiliser votre propre environnement où les comptes AAD ont été configurés. Si cette valeur est omise, une valeur par défaut Intune est utilisée.

* **ClientID** est l’ID client AAD à utiliser. Vous devez utiliser l’ID client de votre propre application si elle est inscrite auprès d’Azure AD. Si cette valeur est omise, une valeur par défaut Intune est utilisée.

* **NonBrokerRedirectURI** est l’URI de redirection AAD à utiliser dans les cas sans broker. Si aucune valeur n’est spécifiée, la valeur par défaut `urn:ietf:wg:oauth:2.0:oob` est utilisée. Cette valeur par défaut convient à la plupart des applications.

* **SkipBroker** est utilisé dans le cas où l’ID client n’a pas été configuré pour utiliser l’URI de redirection de broker. La valeur par défaut est « false ».
    * Pour les applications qui **n’intègrent pas la bibliothèque ADAL** et **ne souhaitent pas participer à l’authentification (unique) répartie à l’échelle de l’appareil**, vous devez affecter la valeur « true ». Quand cette valeur est « true », le seul URI de redirection utilisé est NonBrokerRedirectURI.

    * Pour les applications qui ne prennent pas en charge la répartition de l’authentification unique à l’échelle de l’appareil, cette valeur doit être « false ». Quand la valeur est « false », le SDK sélectionne un broker parmi le résultat de [`com.microsoft.aad.adal.AuthenticationContext.getRedirectUriForBroker()`](https://github.com/AzureAD/azure-activedirectory-library-for-android) et NonBrokerRedirectURI, en fonction de la disponibilité du broker sur le système. En général, le broker est disponible à partir de l’application Portail d’entreprise ou Azure Authenticator.

### <a name="common-adal-configurations"></a>Configurations ADAL courantes

Vous trouverez ci-dessous quelques approches courantes pour la configuration d’une application avec la bibliothèque ADAL. Recherchez la configuration de votre application et assurez-vous d’affecter les valeurs nécessaires aux paramètres de métadonnées de la bibliothèque ADAL (décrits ci-dessus).

1. **L’application n’intègre pas la bibliothèque ADAL :**

    | Paramètre ADAL requis | Valeur |
    |--|--|
    | Authority | Environnement souhaité dans lequel les comptes AAD ont été configurés |
    | SkipBroker | True |

2. **L’application intègre la bibliothèque ADAL :**

    |Paramètre ADAL requis| Valeur |
    |--|--|
    | Authority | Environnement souhaité dans lequel les comptes AAD ont été configurés |
    | ClientID | ID client de l’application (généré par Azure AD quand l’application est inscrite) |
    | NonBrokerRedirectURI | URI de redirection valide pour l’application, ou `urn:ietf:wg:oauth:2.0:oob` par défaut. <br><br> Veillez à configurer la valeur comme URI de redirection acceptable pour l’ID client de votre application.
    | SkipBroker | False |


3. **L’application intègre la bibliothèque ADAL, mais ne prend pas en charge l’authentification répartie ou l’authentification unique à l’échelle de l’appareil :**

    |Paramètre ADAL requis| Valeur |
    |--|--|
    | Authority | Environnement souhaité dans lequel les comptes AAD ont été configurés |
    | ClientID | ID client de l’application (généré par Azure AD quand l’application est inscrite) |
    | NonBrokerRedirectURI | URI de redirection valide pour l’application, ou `urn:ietf:wg:oauth:2.0:oob` par défaut. <br><br> Veillez à configurer la valeur comme URI de redirection acceptable pour l’ID client de votre application.
    | SkipBroker | **True** |

## <a name="app-protection-policy-without-device-enrollment"></a>Stratégie de protection des applications sans inscription des appareils

### <a name="overview"></a>Vue d’ensemble
La stratégie de protection des applications Intune sans inscription d’appareil, également appelée APP-WE ou MAM-WE, permet aux applications d’être gérées par Intune sans nécessiter l’inscription de l’appareil auprès de la gestion des appareils mobiles (MDM) Intune. APP-WE fonctionne avec ou sans inscription d’appareil. Le portail d’entreprise doit toujours être installé sur l’appareil, mais l’utilisateur n’a pas besoin de se connecter au portail d’entreprise et d’inscrire l’appareil.

> [!NOTE]
> Toutes les applications doivent prendre en charge la stratégie de protection des applications sans l’inscription d’appareil.

### <a name="workflow"></a>Workflow

Quand une application crée un compte d’utilisateur, elle doit l’inscrire pour la gestion avec le SDK d’application Intune. Le SDK gère les détails de l’inscription de l’application dans le service APP-WE. Si nécessaire, il réessaiera d’effectuer toute inscription ayant échoué aux intervalles appropriés.

L’application peut également interroger le SDK d’application Intune pour connaître l’état d’un utilisateur inscrit, afin de déterminer si l’accès au contenu d’entreprise doit lui être interdit. Plusieurs comptes peuvent être inscrits pour la gestion, mais actuellement un seul compte à la fois peut être inscrit activement avec le service APP-WE. Cela signifie qu’un seul compte à la fois sur l’application peut recevoir la stratégie de protection des applications.

L’application doit fournir un rappel pour obtenir le jeton d’accès approprié à partir de la bibliothèque ADAL pour le compte du SDK. Il est supposé que l’application utilise déjà la bibliothèque ADAL pour l’authentification utilisateur et pour obtenir ses propres jetons d’accès.

Quand l’application supprime complètement un compte, elle doit annuler l’inscription de ce compte pour indiquer qu’elle ne doit plus appliquer de stratégie pour cet utilisateur. Si l’utilisateur a été inscrit dans le service GAM, son inscription sera annulée et l’application sera réinitialisée.


### <a name="overview-of-app-requirements"></a>Vue d’ensemble des exigences d’application

Pour implémenter l’intégration APP-WE, votre application doit inscrire le compte d’utilisateur avec le SDK GAM :

1. L’application _doit_ implémenter et inscrire une instance de l’interface `MAMServiceAuthenticationCallback`. L’instance de rappel doit être inscrite dès que possible dans le cycle de vie de l’application (en général, dans la méthode `onMAMCreate()` de la classe d’application).

2. Quand un compte d’utilisateur est créé et que l’utilisateur se connecte avec succès avec la bibliothèque ADAL, l’application _doit_ appeler le `registerAccountForMAM()`.

3. Quand un compte d’utilisateur est supprimé complètement, l’application doit appeler `unregisterAccountForMAM()` pour supprimer le compte de la gestion Intune.

    > [!NOTE]
    > Si un utilisateur se déconnecte temporairement de l’application, l’application n’a pas besoin d’appeler `unregisterAccountForMAM()`. L’appel peut lancer une réinitialisation pour supprimer complètement les données d’entreprise pour l’utilisateur.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Toutes les API d’inscription et d’authentification nécessaires sont disponibles dans l’interface `MAMEnrollmentManager`. Vous pouvez obtenir une référence à `MAMEnrollmentManager` comme suit :

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr

```

L’instance de `MAMEnrollmentManager` retournée sera obligatoirement non null. Les méthodes d’API appartiennent à deux catégories : **authentification** et **inscription de compte**.

> [!NOTE]
> `MAMEnrollmentManager` contient des méthodes d’API qui seront bientôt dépréciées. Pour plus de clarté, seuls les méthodes et les codes de résultats pertinents sont affichés dans le bloc de code ci-dessous.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Authentification du compte

Cette section décrit les méthodes d’API d’authentification dans `MAMEnrollmentManager` et comment les utiliser.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. L’application doit implémenter l’interface `MAMServiceAuthenticationCallback` pour permettre au SDK de demander un jeton ADAL pour l’ID de ressource et l’utilisateur donnés. L’instance de rappel doit être fournie au `MAMEnrollmentManager` en appelant sa méthode `registerAuthenticationCallback()`. Un jeton peut être nécessaire très tôt dans le cycle de vie d’application pour les nouvelles tentatives d’inscription ou les archivages d’actualisation de stratégie de protection des applications. Ainsi, l’emplacement idéal pour enregistrer le rappel est dans la méthode `onMAMCreate()` de la sous-classe `MAMApplication` de l’application.

2. La méthode `acquireToken()` doit acquérir le jeton d’accès pour l’ID de ressource demandé pour l’utilisateur donné. Si elle ne peut pas acquérir le jeton demandé, elle doit retourner la valeur null.

3. Au cas où l’application est incapable de fournir un jeton quand le SDK appelle `acquireToken()` (par exemple si l’authentification en mode silencieux échoue et que le moment est inopportun pour afficher une interface utilisateur), l’application peut fournir un jeton ultérieurement en appelant la méthode `updateToken()`. Les mêmes UPN, ID AAD et ID de ressource que ceux demandés par l’appel précédent à `acquireToken()` doivent être passés à `updateToken()`, avec le jeton qui a été acquis en fin de compte. L’application doit appeler cette méthode dès que possible après avoir retourné la valeur null à partir du rappel fourni.

> [!NOTE]
> Le SDK appelle `acquireToken()` périodiquement pour obtenir le jeton. Ainsi, l’appel de `updateToken()` n’est pas strictement nécessaire. Toutefois, il est recommandé car il peut aider à ce que les inscriptions et les archivages de stratégie de protection des applications se terminent dans un délai raisonnable.


### <a name="account-registration"></a>Inscription du compte

Cette section décrit les méthodes d’API d’inscription de compte dans `MAMEnrollmentManager` et comment les utiliser.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Pour inscrire un compte pour la gestion, l’application doit appeler `registerAccountForMAM()`. Un compte d’utilisateur est identifié à la fois par son UPN et par son ID utilisateur AAD. L’ID de locataire est également nécessaire pour associer les données d’inscription au locataire AAD de l’utilisateur. Le SDK peut tenter d’inscrire l’application pour l’utilisateur donné dans le service GAM. Si l’inscription échoue, il réessaiera périodiquement d’effectuer l’inscription jusqu’à ce que le compte soit désinscrit. La période de nouvelle tentative est généralement de 12 et 24 heures. Le SDK fournit l’état des tentatives d’inscription de manière asynchrone par l’intermédiaire de notifications.

2. Étant donné que l’authentification AAD est requise, le meilleur moment pour inscrire le compte d’utilisateur est une fois que l’utilisateur s’est connecté à l’application et a été authentifié avec succès à l’aide de la bibliothèque ADAL.
    * L’ID AAD et l’ID de locataire de l’utilisateur sont retournés à partir de l’appel d’authentification ADAL dans le cadre de l’objet [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android). L’ID de locataire provient de la méthode `AuthenticationResult.getTenantID()`.
    * Les informations sur l’utilisateur se trouvent dans un sous-objet de type `UserInfo` provenant de `AuthenticationResult.getUserInfo()`, et l’ID utilisateur AAD est récupéré à partir de cet objet en appelant `UserInfo.getUserId()`.

3. Pour désinscrire un compte de la gestion Intune, l’application doit appeler `unregisterAccountForMAM()`. Si le compte a été inscrit avec succès et qu’il est géré, le SDK annulera l’inscription du compte et réinitialisera ses données. Les nouvelles tentatives d’inscription périodiques pour le compte seront arrêtées. Le SDK fournit l’état des demandes d’annulation d’inscription de manière asynchrone par l’intermédiaire de notifications.

### <a name="important-implementation-notes"></a>Remarques importantes concernant l’implémentation

#### <a name="authentication"></a>Authentification

* Quand l’application appelle `registerAccountForMAM()`, elle peut recevoir juste après un rappel sur son interface `MAMServiceAuthenticationCallback`, sur un thread différent. Dans l’idéal, l’application a obtenu son propre jeton à partir de la bibliothèque ADAL avant d’inscrire le compte, afin d’accélérer l’acquisition du **jeton MAMService**. Si l’application retourne un jeton valide à partir du rappel, l’inscription se poursuit et l’application obtiendra le résultat final par l’intermédiaire d’une notification.

* Si l’application ne retourne pas un jeton AAD valide, le résultat final de la tentative d’inscription est `AUTHENTICATION_NEEDED`. Si l’application reçoit ce résultat par l’intermédiaire d’une notification, elle peut accélérer le processus d’inscription en acquérant le **jeton MAMService** et en appelant la méthode `updateToken()` pour relancer le processus d’inscription. Toutefois, il ne s’agit _pas_ d’une exigence stricte, étant donné que le SDK retente régulièrement d’effectuer l’inscription et appelle le rappel pour acquérir le jeton.

* Le `MAMServiceAuthenticationCallback` inscrit de l’application est également appelé pour acquérir un jeton pour les archivages d’actualisation de stratégie de protection des applications périodiques. Si l’application est incapable de fournir un jeton demandé, elle ne reçoit pas de notification, mais elle doit essayer d’acquérir un jeton et d’appeler `updateToken()` le plus rapidement possible afin d’accélérer le processus d’archivage. Si aucun jeton n’est fourni, le rappel est quand même appelé à la prochaine tentative d’archivage.

#### <a name="registration"></a>Inscription

* Par souci pratique, les méthodes d’inscription sont idempotent. Par exemple, `registerAccountForMAM()` inscrit un compte et tente d’inscrire l’application uniquement si le compte n’est pas encore inscrit, et `unregisterAccountForMAM()` annule l’inscription d’un compte uniquement s’il est actuellement inscrit. Les appels suivants étant non-opérationnels, il n’y a aucun risque à appeler ces méthodes plusieurs fois. En outre, la correspondance entre les appels à ces méthodes et les notifications de résultats n’est pas garantie : autrement dit, si `registerAccountForMAM` est appelé pour une identité déjà inscrite, la notification peut ne pas être envoyée à nouveau pour cette identité. Il est possible que des notifications envoyées ne correspondent à aucun appel à ces méthodes, car le SDK peut tenter d’effectuer périodiquement des inscriptions en arrière-plan, et des annulations d’inscription peuvent être déclenchées par des demandes de réinitialisation envoyées par le service Intune.

* Les méthodes d’inscription peuvent être appelées pour un nombre quelconque d’identités différentes, mais à l’heure actuelle un seul compte d’utilisateur peut être inscrit. Si plusieurs comptes d’utilisateur disposant d’une licence Intune et ciblés par la stratégie de protection des applications sont inscrits simultanément (ou presque), il n’existe aucun moyen de savoir lequel l’emportera.

* Pour finir, vous pouvez interroger `MAMEnrollmentManager` pour savoir si un compte particulier est inscrit et pour obtenir son état actuel à l’aide de la méthode `getRegisteredAccountStatus`. Si le compte spécifié n’est pas inscrit, cette méthode retourne **null**. Si le compte est inscrit, cette méthode retourne l’état du compte en tant que membre de l’énumération `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Codes de résultat et d’état

Quand un compte est inscrit initialement, il commence à l’état `PENDING`, ce qui indique que la tentative initiale d’inscription au service GAM est incomplète. Une fois la tentative d’inscription terminée, une notification est envoyée avec l’un des codes de résultat mentionnés dans le tableau ci-dessous. De plus, la méthode `getRegisteredAccountStatus()` retourne l’état du compte pour que l’application puisse toujours déterminer si l’accès au contenu d’entreprise est bloqué pour cet utilisateur. Si la tentative d’inscription échoue, l’état du compte peut changer au fil du temps à mesure que le SDK retente l’inscription en arrière-plan.

|Code de résultat | Explication |
| -- | -- |
|AUTHORIZATION_NEEDED | Ce résultat indique qu’aucun jeton n’a été fourni par l’instance `MAMServiceAuthenticationCallback` inscrite de l’application, ou que le jeton fourni n’était pas valide.  L’application doit acquérir un jeton valide et appeler `updateToken()` si possible. |
| NOT_LICENSED | L’utilisateur ne dispose pas de licence pour Intune, ou la tentative de contact du service GAM Intune a échoué.  L’application doit continuer dans un état non géré (normal) et l’utilisateur ne doit pas être bloqué.  Les inscriptions seront retentées régulièrement dans le cas où l’utilisateur obtiendrait une licence ultérieurement. |
| ENROLLMENT_SUCCEEDED | La tentative d’inscription a réussi, ou l’utilisateur est déjà inscrit.  En cas de réussite de l’inscription, une notification d’actualisation de la stratégie est envoyée avant cette notification.  L’accès aux données d’entreprise doit être autorisé. |
| ENROLLMENT_FAILED | La tentative d’inscription a échoué.  Les journaux de l’appareil contiennent des informations supplémentaires.  L’application ne doit pas autoriser l’accès aux données d’entreprise dans cet état, car il a été précédemment déterminé que l’utilisateur disposait d’une licence pour Intune.|
| WRONG_USER | Un seul utilisateur par appareil peut inscrire une application auprès du service GAM.  Pour que l’application puisse s’inscrire en tant qu’autre utilisateur, toutes les applications inscrites doivent d’abord être désinscrites.  Dans le cas contraire, cette application doit s’inscrire en tant qu’utilisateur principal.  Cette vérification est effectuée après la vérification de la licence. L’accès aux données d’entreprise doit donc être interdit à l’utilisateur jusqu’à ce que l’application soit correctement inscrite.|
| UNENROLLMENT_SUCCEEDED | L’annulation de l’inscription a réussi.|
| UNENROLLMENT_FAILED | La demande d’annulation de l’inscription a échoué.  Les journaux de l’appareil contiennent des informations supplémentaires. |
| PENDING | La tentative d’inscription initiale de l’utilisateur est en cours.  L’application peut bloquer l’accès aux données d’entreprise jusqu’à ce que le résultat de l’inscription soit connu, mais cela n’est pas obligatoire. |
| COMPANY_PORTAL_REQUIRED | L’utilisateur dispose d’une licence pour Intune, mais l’application ne peut pas être inscrite tant que l’application Portail d’entreprise n’a pas été installée sur l’appareil. Le SDK d’application Intune tentera de bloquer l’accès à l’application pour l’utilisateur donné et l’invitera à installer l’application Portail d’entreprise (voir ci-dessous pour plus de détails). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Ignorer l’invite relative à l’obligation de présence du portail d’entreprise (facultatif)

Si le résultat `COMPANY_PORTAL_REQUIRED` est reçu, le SDK bloque les activités qui utilisent l’identité pour laquelle l’inscription a été demandée. Il fait en sorte que ces activités affichent une invite de téléchargement du portail d’entreprise. Si vous souhaitez éviter ce comportement dans votre application, les activités peuvent implémenter `MAMActivity.onMAMCompanyPortalRequired`.

Cette méthode est appelée avant que le SDK affiche son interface utilisateur de blocage par défaut. Si l’application change l’identité d’activité ou annule l’inscription de l’utilisateur qui a tenté d’effectuer l’inscription, le SDK ne bloque pas l’activité. Dans ce cas, c’est à l’application d’éviter toute fuite de données d’entreprise.

### <a name="notifications"></a>Notifications

Un nouveau type de `MAMNotification` a été ajouté afin de signaler à l’application que la demande d’inscription est terminée.  Le `MAMEnrollmentNotification` est reçu par l’intermédiaire de l’interface `MAMNotificationReceiver` comme décrit dans la section [S’inscrire aux notifications à partir du SDK](#register-for-notifications-from-the-sdk) .

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}

```

La méthode `getEnrollmentResult()` retourne le résultat de la demande d’inscription.  Étant donné que `MAMEnrollmentNotification` étend `MAMUserNotification`, l’identité de l’utilisateur pour lequel l’inscription a été tentée est également disponible. L’application doit implémenter l’interface `MAMNotificationReceiver` pour recevoir ces notifications, détaillées dans la section [S’inscrire aux notifications à partir du SDK](#Register-for-notifications-from-the-SDK).

L’état du compte d’utilisateur inscrit peut changer lors de la réception d’une notification d’inscription, mais il ne changera pas dans certains cas (par exemple, si une notification `AUTHORIZATION_NEEDED` est reçue après un résultat plus explicite tel que `WRONG_USER`, le résultat le plus explicite est conservé comme état du compte).


## <a name="protecting-backup-data"></a>Protection des données de sauvegarde

À compter d’Android Marshmallow (API 23), les applications Android peuvent sauvegarder leurs données de deux façons. Chaque option est disponible pour votre application et requiert différentes étapes pour assurer l’implémentation correcte de la protection des données Intune. Vous pouvez consulter le tableau ci-dessous qui indique les actions correspondantes requises à l’adoption d’un comportement de protection des données approprié.  Pour en savoir plus sur les méthodes de sauvegarde, vous pouvez consulter le [guide des API Android](http://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Sauvegarde automatique pour les applications

Android a commencé à proposer des [sauvegardes complètes automatiques](https://developer.android.com/guide/topics/data/autobackup.html) vers Google Drive aux applications sur les appareils Android Marshmallow, quelle que soit l’API cible de l’application. Dans votre fichier AndroidManifest.xml, si vous définissez explicitement `android:allowBackup` sur **false**, votre application n’est jamais placée en file d’attente en vue d’une sauvegarde par Android, et les données « d’entreprise » demeurent dans l’application. Dans ce cas, aucune action supplémentaire n’est nécessaire.

Toutefois, par défaut l’attribut `android:allowBackup` est défini sur true, même si `android:allowBackup` n’est pas spécifié dans le fichier manifeste. Cela signifie que toutes les données d’application sont automatiquement sauvegardées dans le compte Google Drive de l’utilisateur, comportement par défaut qui représente un **risque de fuite de données**. Ainsi, le SDK exige les modifications répertoriées ci-dessous pour vérifier que la protection des données est appliquée.  Il est important de suivre les instructions ci-dessous pour protéger correctement les données des clients si vous souhaitez que votre application s’exécute sur les appareils Android Marshmallow.  

Intune vous permet d’utiliser toutes les [fonctionnalités de sauvegarde automatique](https://developer.android.com/guide/topics/data/autobackup.html) disponibles à partir d’Android, y compris la possibilité de définir des règles personnalisées en XML, mais vous devez suivre les étapes ci-dessous pour sécuriser vos données :

1. Si votre application n’utilise **pas** son propre BackupAgent personnalisé, utilisez le MAMBackupAgent par défaut pour permettre l’exécution de sauvegardes complètes automatiques conformes aux stratégies Intune. Dans ce cas, vous pouvez ignorer l’attribut de manifeste `android:fullBackupOnly`, car il ne s’applique pas à notre agent de sauvegarde. Placez le code suivant dans le manifeste d’application :

    ```xml
android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```

2. **[Facultatif]** Si vous avez implémenté un BackupAgent personnalisé facultatif, vous devez utiliser MAMBackupAgent ou MAMBackupAgentHelper. Voir les sections suivantes. Songez à passer au **MAMDefaultFullBackupAgent** d’Intune (décrit à l’étape 1), qui permet de sauvegarder facilement sur Android M et versions ultérieures.

3. Quand vous choisissez le type de sauvegarde complète que votre application doit recevoir (non filtré, filtré ou aucun) vous devez définir l’attribut `android:fullBackupContent` sur true, false ou une ressource XML dans votre application.

4. Ensuite, vous _**devez**_ copier tout ce que vous mettez dans `android:fullBackupContent` dans une balise de métadonnées nommée `com.microsoft.intune.mam.FullBackupContent` dans le manifeste.

    **Exemple 1** : Si vous souhaitez que votre application ait des sauvegardes complètes sans exclusions, affectez la valeur **true** à l’attribut `android:fullBackupContent` et à la balise de métadonnées `com.microsoft.intune.mam.FullBackupContent` :

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **Exemple 2** : Si vous souhaitez que votre application utilise son BackupAgent personnalisé et ne participe pas aux sauvegardes automatiques complètes et conformes aux stratégies Intune, vous devez affecter la valeur **false** à l’attribut et à la balise de métadonnées :

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **Exemple 3** : Si vous souhaitez que votre application ait des sauvegardes complètes conformément à vos règles personnalisées définies dans un fichier XML, affectez à l’attribut et à la balise de métadonnées la même ressource XML :

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>Sauvegarde de clé/valeur

L’option [Sauvegarde de clé/valeur](https://developer.android.com/guide/topics/data/keyvaluebackup.html) est disponible pour toutes les API 8+. Elle charge les données d’application vers le [Service de sauvegarde Android](https://developer.android.com/google/backup/index.html). La quantité de données par utilisateur de votre application est limitée à 5 Mo. Si vous utilisez Sauvegarde de clé/valeur, vous devez utiliser un **BackupAgentHelper** ou **BackupAgent**.

### <a name="backupagenthelper"></a>BackupAgentHelper

BackupAgentHelper est plus simple à implémenter que BackupAgent tant sur le plan des fonctionnalités Android natives que de l’intégration de la gestion des applications mobiles Intune. BackupAgentHelper permet au développeur d’inscrire des fichiers entiers et des préférences partagées auprès de **FileBackupHelper** ou de **SharedPreferencesBackupHelper** (respectivement), qui sont ensuite ajoutés à BackupAgentHelper au moment de la création. Suivez les étapes ci-dessous pour utiliser un BackupAgentHelper avec GAM Intune :

1. Pour utiliser la sauvegarde de plusieurs identités avec un BackupAgentHelper, suivez le guide Android d’[extension de BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper).

2. Faites en sorte que votre classe étende l’équivalent GAM de BackupAgentHelper, FileBackupHelper et SharedPreferencesBackupHelper.

|Classe Android | Équivalent GAM |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Le respect de ces recommandations est garant du succès de la sauvegarde et de la restauration des identités multiples.

### <a name="backupagent"></a>BackupAgent

Un BackupAgent vous permet d’être beaucoup plus explicite quant aux données à sauvegarder. Dans la mesure où le développeur a la responsabilité de l’implémentation, d’autres étapes sont requises pour assurer la protection appropriée des données Intune. Étant donné que l’essentiel du travail incombe au développeur, c’est-à-dire vous, l’intégration d’Intune est un peu plus complexe.

**Intégrer GAM :**

1. Veuillez lire attentivement le guide Android de [Sauvegarde de clé/valeur](https://developer.android.com/guide/topics/data/keyvaluebackup.html), et spécifiquement [Extension de BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent), pour être sûr que votre implémentation de BackupAgent respecte les recommandations Android.

2. Faites en sorte que votre classe étende `MAMBackupAgent`.

**Sauvegarde de plusieurs identités :**

1. Avant de commencer la sauvegarde, vérifiez que la sauvegarde des fichiers ou des mémoires tampons de données que vous souhaitez sauvegarder est bien **autorisée par l’administrateur informatique** dans les scénarios à plusieurs identités. Pour cela, utilisez la fonction `isBackupAllowed` disponible dans `MAMFileProtectionManager` et `MAMDataProtectionManager`. Si la sauvegarde du fichier ou de la mémoire tampon de données n’est pas autorisée, vous ne devez pas continuer à l’inclure dans votre sauvegarde.

2. À un moment donné de la sauvegarde, si vous souhaitez sauvegarder les identités des fichiers vérifiés à l’étape 1, vous devez appeler `backupMAMFileIdentity(BackupDataOutput data, File … files)` avec les fichiers dont vous souhaitez extraire les données. Des entités de sauvegarde sont alors automatiquement créées et écrites dans `BackupDataOutput` pour vous. Ces entités sont automatiquement consommées lors de la restauration.

**Restauration de plusieurs identités :**

Le guide de sauvegarde des données spécifie un algorithme général pour la restauration des données de votre application et fournit un exemple de code dans la section [Extension de BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). Pour que la restauration de plusieurs identités réussisse, vous devez suivre la structure générale fournie dans cet exemple de code, en accordant une attention particulière à ce qui suit :

1.  Vous devez utiliser une boucle `while(data.readNextHeader())`* pour parcourir les entités de sauvegarde.

2.  Vous devez appeler `data.skipEntityData()`* si `data.getKey()`* ne correspond pas à la clé que vous avez écrite dans `onBackup`. Sans cette étape, vos restaurations peuvent échouer.

3.  Éviter de retourner tout en consommant des entités de sauvegarde dans la construction `while(data.readNextHeader())`*, car les entités que nous écrivons automatiquement seront perdues.

* Où `data` est le nom de variable locale pour le **BackupDataInput** passé à votre application lors de la restauration.

## <a name="multi-identity-optional"></a>Multi-identité (facultatif)

### <a name="overview"></a>Vue d’ensemble
Par défaut, le SDK d’application Intune applique une stratégie à l’application comme un tout. La multi-identité est une fonctionnalité de protection des applications Intune qui peut être activée pour permettre d’appliquer la stratégie à un niveau par identité. Ceci nécessite une participation nettement accrue de l’application par rapport à d’autres fonctionnalités de protection des applications.

L’application _doit_ informer le SDK quand elle a l’intention de modifier l’identité active ; de même, le SDK notifie l’application quand un changement d’identité est nécessaire. Une fois que l’utilisateur inscrit l’appareil ou l’application, le SDK inscrit cette identité et la considère comme l’identité gérée Intune principale. Les autres utilisateurs de l’application sont considérés comme non gérés, avec des paramètres de stratégie non limités.

> [!NOTE]
> À l’heure actuelle, une seule identité gérée Intune est prise en charge par appareil.

Notez qu’une identité est simplement définie sous la forme d’une chaîne. Les identités **ne respectent pas la casse** et les demandes d’une identité au SDK peuvent ne pas retourner la même casse que celle initialement utilisée lors de la définition de l’identité.


### <a name="enabling-multi-identity"></a>Activation de la multi-identité

Par défaut, toutes les applications sont considérées comme des applications d’identité unique. Vous pouvez déclarer une application comme application prenant en charge plusieurs identités en plaçant les métadonnées suivantes dans AndroidManifest.xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Définition de l’identité

Les développeurs peuvent définir l’identité de l’utilisateur d’application sur les niveaux suivants dans l’ordre de priorité décroissant :

  1. Thread
  2. Contexte (en général, activité)
  3. Processus

Une identité définie au niveau du thread remplace une identité définie au niveau du contexte, qui remplace elle-même une identité définie au niveau du processus. Une identité définie sur un contexte est utilisée uniquement dans les scénarios associés appropriés. Les opérations d’E/S de fichiers, par exemple, n’ont pas de contexte associé. Vous pouvez utiliser les méthodes suivantes dans `MAMPolicyManager` pour définir l’identité et extraire les valeurs d’identité définies précédemment.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

  /**
   * Get the currently applicable app policy. Same as
   * MAMComponents.get(AppPolicy.class). This method does
   * not take the context identity into account.
   */
  public static AppPolicy getPolicy();

  /**
   * Get the currently applicable app policy, taking the context
   * identity into account.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);

  ```

>[!NOTE]
> Vous pouvez effacer l’identité de l’application en lui affectant la valeur null.
>
> La chaîne vide peut être utilisée comme une identité qui n’aura jamais de stratégie de protection des applications.

#### <a name="results"></a>Résultats
Toutes les méthodes utilisées pour définir l’identité transmettent les valeurs obtenues par le biais de `MAMIdentitySwitchResult`. Quatre valeurs peuvent être retournées :

| Valeur renvoyée | Scénario |
|--|--|
| SUCCEEDED | Le changement d’identité a réussi. |
| NOT_ALLOWED | Le changement d’identité n’est pas autorisé. <br><br>Cela se produit en cas de tentative de changement en faveur d’un autre utilisateur géré appartenant à la même organisation que l’utilisateur inscrit. Cela se produit également si l’identité de l’interface utilisateur (contexte) fait l’objet d’une tentative de définition alors qu’une identité différente est définie sur le thread actuel. |
| CANCELLED | L’utilisateur a annulé le changement d’identité, généralement en appuyant sur le bouton Précédent dans une invite de code PIN ou d’authentification. |
| FAILED | Le changement d’identité a échoué pour une raison non précisée.|


Dans le cas de la définition d’une identité de contexte, le résultat est signalé de manière asynchrone. Si le contexte est une activité, le SDK ne sait pas si le changement d’identité a réussi tant que le lancement conditionnel n’est pas effectué, ce qui peut nécessiter que l’utilisateur entre un code PIN ou des informations d’identification d’entreprise. L’application est censée implémenter un `MAMSetUIIdentityCallback` pour recevoir ce résultat. Vous pouvez passer la valeur null pour ce paramètre.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

Vous pouvez également définir l’identité d’une activité directement par le biais d’une méthode dans `MAMActivity`, au lieu d’appeler `MAMPolicyManager.setUIPolicyIdentity`. Pour ce faire, utilisez la méthode suivante :

```java
     public final void switchMAMIdentity(final String newIdentity);
```

Vous pouvez aussi substituer une méthode dans `MAMActivity` si vous voulez que l’application soit informée du résultat des tentatives de changement de l’identité de cette activité.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

>[!NOTE]
> Le changement d’identité peut nécessiter la recréation de l’activité. Dans ce cas, le rappel `onSwitchMAMIdentityComplete` est remis à la nouvelle instance de l’activité.


### <a name="implicit-identity-changes"></a>Modifications d’identité implicites

Outre la possibilité pour l’application de définir l’identité, l’identité d’un contexte ou d’un thread peut changer en fonction de l’entrée de données à partir d’une autre application compatible avec Intune ayant une stratégie de protection des applications.

#### <a name="examples"></a>Exemples

  1. Si une activité est lancée à partir d’un `Intent` envoyé par une autre application GAM, l’identité de l’activité est définie en fonction de l’identité effective dans l’autre application au point où le `Intent` a été envoyé.

  2.  Pour les services, l’identité du thread est définie de la même façon pendant la durée d’un appel `onStart` ou `onBind`. Les appels dans `Binder` retournés par `onBind` définissent également temporairement l’identité du thread.

  3. Les appels dans un `ContentProvider` définissent de la même façon l’identité du thread pendant leur durée.


  En outre, l’interaction utilisateur avec une activité peut entraîner un changement d’identité implicite.

  **Exemple :** Si un utilisateur annule une invite d’autorisation pendant `Resume`, un changement implicite en faveur d’une identité vide a lieu.

  L’application peut être informée de ces modifications et, si elle le doit, elle peut les interdire. `MAMService` et `MAMContentProvider` exposent la méthode suivante, que les sous-classes peuvent substituer :

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
  ```

  Dans la classe `MAMActivity`, un paramètre supplémentaire est présent dans la méthode :

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
  ```

  * `AppIdentitySwitchReason` capture la source du changement implicite et peut accepter les valeurs `CREATE`, `RESUME_CANCELLED` et `NEW_INTENT`.  La raison `RESUME_CANCELLED` est utilisée quand la reprise de l’activité entraîne l’affichage de l’interface utilisateur de saisie de code confidentiel, d’authentification ou d’autres données de conformité et que l’utilisateur tente d’annuler cette interface utilisateur, généralement en utilisant le bouton précédent.


  * `AppIdentitySwitchResultCallback` se présente comme suit :

    ```java
    public interface AppIdentitySwitchResultCallback {
        /**
         * @param result
         *            whether the identity switch can proceed.
         */
        void reportIdentitySwitchResult(AppIdentitySwitchResult result);
    }
    ```

    Où ```AppIdentitySwitchResult``` est SUCCESS ou FAILURE.

La méthode `onMAMIdentitySwitchRequired` est appelée pour toutes les modifications d’identité implicites, à l’exception de celles effectuées par le biais d’un Binder retourné à partir de `MAMService.onMAMBind`. Les implémentations par défaut de `onMAMIdentitySwitchRequired` appellent immédiatement :

*  `reportIdentitySwitchResult(FAILURE)` quand la cause est RESUME_CANCELLED.

*  `reportIdentitySwitchResult(SUCCESS)` dans tous les autres cas.

  Il est peu probable que la plupart des applications aient besoin de bloquer ou différer un changement d’identité d’une manière différente, mais si une application a besoin de le faire, les points suivants doivent être pris en compte :

  * Si un changement d’identité est bloqué, le résultat est le même que si les paramètres de partage `Receive` avaient interdit la saisie de données.

  * Si un service est en cours d’exécution sur le thread principal, `reportIdentitySwitchResult` **doit** être appelé de façon synchrone, sinon le thread d’interface utilisateur se bloque.

  * Pour la création d’**Activité**, `onMAMIdentitySwitchRequired` est appelé avant `onMAMCreate`. Si l’application doit afficher l’interface utilisateur pour déterminer s’il faut autoriser le changement d’identité, cette interface utilisateur doit être affichée à l’aide d’une *autre* activité.

  * Dans une **Activité**, quand un changement en faveur de l’identité vide est demandé et que la raison est RESUME_CANCELLED, l’application doit modifier l’activité reprise pour afficher des données cohérentes avec ce changement d’identité.  Si ce n’est pas possible, l’application doit refuser le changement et l’utilisateur est invité à se reconformer à la stratégie associée à l’identité en cours de reprise (stratégie qui, par exemple, peut prévoir la présentation de l’écran de saisie du code PIN d’application).

    > [!NOTE]
    > Une application qui prend en charge plusieurs identités reçoit toujours les données entrantes à partir d’applications gérées et non gérées. Il appartient à l’application de traiter de manière gérée les données issues d’identités gérées.

  Si une identité demandée est gérée (utilisez `MAMPolicyManager.getIsIdentityManaged` pour le vérifier), mais que l’application ne peut pas utiliser ce compte (par exemple, du fait que les comptes, tels que les comptes e-mail, doivent d’abord être configurés dans l’application), le changement d’identité doit être refusé.



  ### <a name="file-protection"></a>Protection des fichiers

  Chaque fichier se voit associer une identité au moment de la création, en fonction de l’identité de thread et de processus. Cette identité est utilisée pour le chiffrement de fichier et la réinitialisation sélective. Seuls les fichiers dont l’identité est gérée et a une stratégie qui exige le chiffrement sont chiffrés. La réinitialisation sélective par défaut du SDK réinitialise uniquement les fichiers associés à l’identité gérée pour laquelle une réinitialisation a été demandée. L’application peut interroger ou changer l’identité d’un fichier à l’aide de la classe `MAMFileProtectionManager`.

  ```java
    public final class MAMFileProtectionManager {

        /**
         * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
         * future protection changes.
         *
         * @param identity
         *            Identity to set.
         * @param file
         *            File to protect.
         * @throws IOException
         *             If the file cannot be changed.
         */
        public static void protect(final File file, final String identity) throws IOException;

        /**
         * Get the protection info on a file.
         *
         * @param file
         *            File or directory to get information on.
         * @return File protection info, or null if there is no protection info.
         * @throws IOException
         *             If the file cannot be read or opened.
         */
        public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

        /**
         * Get the protection info on a file.
         *
         * @param file
         *            File to get information on.
         * @return File protection info, or null if there is no protection info.
         * @throws IOException
         *             If the file cannot be read or opened.
         */
        public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

    }

    public interface MAMFileProtectionInfo {
        String getIdentity();
    }

  ```

Le balisage de l’identité d’un fichier est sensible au mode hors connexion. Les points suivants doivent être pris en compte :

  * Si le portail d’entreprise n’est pas installé, les fichiers ne peuvent pas faire l’objet d’un balisage d’identité.

  * Si le portail d’entreprise est installé, mais que l’application n’a pas de stratégie GAM Intune, les fichiers ne peuvent pas faire l’objet d’un balisage d’identité de façon fiable.

  * Quand le balisage d’identité des fichiers devient disponible, tous les fichiers déjà créés sont traités comme personnels/non gérés (appartenant à l’identité à chaîne vide), sauf si l’application a été installée en tant qu’application gérée à identité unique, auquel cas ils sont considérés comme appartenant à l’utilisateur inscrit.

### <a name="directory-protection"></a>Protection des répertoires

Les répertoires peuvent être protégés à l’aide de la même méthode `protect` que celle utilisée pour protéger les fichiers. Notez que la protection des répertoires s’applique de manière récursive à tous les fichiers et sous-répertoires contenus dans le répertoire, ainsi qu’aux fichiers créés dans le répertoire. La protection des répertoires étant appliquée de manière récursive, l’appel `protect` peut prendre du temps pour les répertoires très volumineux. Pour cette raison, si des applications appliquent la protection à un répertoire contenant un grand nombre de fichiers, il vaut peut-être mieux qu’elles exécutent `protect` de façon asynchrone sur un thread d’arrière-plan.

### <a name="data-protection"></a>Protection des données

Il est impossible de baliser un fichier comme appartenant à plusieurs identités. Les applications qui doivent stocker des données appartenant à différents utilisateurs dans le même fichier peuvent le faire manuellement à l’aide des fonctionnalités fournies par `MAMDataProtectionManager`. Ainsi, l’application peut chiffrer les données et les lier à un utilisateur particulier. Les données chiffrées peuvent ensuite être stockées sur disque dans un fichier. Vous pouvez interroger les données associées à l’identité, et les données peuvent être déchiffrées ultérieurement.

Les applications qui utilisent `MAMDataProtectionManager` doivent implémenter un récepteur pour la notification `MANAGEMENT_REMOVED`. Après cette notification, les mémoires tampons qui étaient protégées à l’aide de cette classe ne seront plus lisibles si le chiffrement de fichier était activé quand les mémoires tampons étaient protégées. Une application peut corriger cette situation en appelant MAMDataProtectionManager.unprotect sur toutes les mémoires tampons pendant cette notification. Notez que vous pouvez aussi appeler protect durant cette notification si vous souhaitez conserver les informations d’identité : la désactivation du chiffrement est garantie durant la notification.

```java

public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
     * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
     *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
     *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
     *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
     *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
     * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
     *            stream must have been returned by a previous call to
     *            protect OR input.markSupported() must return true.
     *            Otherwise it will be impossible to get protection info
     *            without advancing the stream position. The stream must be
     *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
     *            returned by a previous call to protect() or a copy of
     *            such bytes.
     * @return Data protection info, or null if there is no protection
     *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}

```

### <a name="content-providers"></a>Fournisseurs de contenu

Si l’application fournit des données d’entreprise autres qu’un **ParcelFileDescriptor** par l’intermédiaire d’un **ContentProvider**, elle doit appeler la méthode `isProvideContentAllowed(String)` dans `MAMContentProvider`, et passer l’UPN de l’identité propriétaire pour le contenu. Si cette fonction retourne la valeur false, le contenu *peut ne pas être retourné* à l’appelant. Les descripteurs de fichier retournés par le biais d’un fournisseur de contenu sont gérés automatiquement en fonction de l’identité des fichiers.

### <a name="selective-wipe"></a>Réinitialisation sélective

Si une application s’inscrit à la notification `WIPE_USER_DATA`, elle ne bénéficie plus du comportement de réinitialisation sélective par défaut du SDK. Pour les applications prenant en charge plusieurs identités, cette perte peut être d’autant plus importante, car la réinitialisation sélective GAM par défaut réinitialise uniquement les fichiers dont l’identité est ciblée par une réinitialisation.

Si une application prenant en charge plusieurs identités souhaite que la réinitialisation sélective GAM par défaut soit effectuée _**et**_ souhaite effectuer ses propres actions de réinitialisation, elle doit s’inscrire pour les notifications `WIPE_USER_AUXILIARY_DATA`. Cette notification sera envoyée par le SDK juste avant d’effectuer la réinitialisation sélective par défaut GAM. Une application ne doit jamais s’inscrire à la fois pour WIPE_USER_DATA et WIPE_USER_AUXILIARY_DATA.


## <a name="style-customization-optional"></a>Personnalisation du style (facultatif)

Les vues générées par le SDK GAM peuvent être personnalisées afin d’avoir une apparence visuelle plus proche de l’application dans laquelle elles sont intégrées. Vous pouvez personnaliser les couleurs principale, secondaire et d’arrière-plan, ainsi que la taille du logo de l’application. Cette personnalisation du style est facultative, et les valeurs par défaut sont utilisées si aucun style personnalisé n’est configuré.


### <a name="how-to-customize"></a>Comment personnaliser
Pour que les modifications de style s’appliquent aux vues GAM Intune, vous devez d’abord créer un fichier XML de substitution de style. Vous devez placer ce fichier dans le répertoire « /res/xml » de votre application et vous pouvez le nommer comme vous le souhaitez. Voici un exemple du format que doit avoir ce fichier.

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>

```

Vous devez réutiliser des ressources qui existent déjà dans votre application. Par exemple, vous devez définir la couleur verte dans le fichier colors.xml et la référencer ici. Vous ne pouvez pas utiliser le code de couleur hexadécimal « #0000ff ». La taille maximale du logo d’application est de 110 dip (dp). Vous pouvez utiliser une image de logo plus petite, mais l’adoption de la taille maximale donne des résultats de meilleure qualité. Si vous dépassez la limite de 110 dip, l’image est mise à l’échelle, avec éventuellement un effet de flou.

Voici la liste complète des attributs de style autorisés, les éléments d’interface utilisateur qu’ils contrôlent, leurs noms d’éléments d’attributs XML et le type de ressource attendu pour chacun.

|Attribut de style | Éléments d’interface utilisateur affectés | Nom de l’élément d’attribut | Type de ressource attendu |
| -- | -- | -- | -- |
| Couleur d’arrière-plan | Couleur d’arrière-plan de l’écran de code PIN <Br>Couleur de remplissage de la zone de code PIN | background_color | Couleur |
| Couleur de premier plan | Couleur du texte de premier plan <br> Bordure de la zone de code PIN à l’état par défaut <br> Caractères (notamment les caractères obscurcis) dans la zone de code PIN quand l’utilisateur entre un code PIN| foreground_color | Couleur|
| Couleur d’accentuation | Bordure de la zone de code PIN en cas de mise en surbrillance <br> Liens hypertexte |accent_color | Couleur |
| Logo de l’application | Grande icône qui apparaît dans l’écran de code PIN d’application Intune | logo_image | Dessinable |

## <a name="limitations"></a>Limitations

### <a name="file-size-limitations"></a>Limitations concernant la taille des fichiers

Pour les grandes bases de code qui s’exécutent sans [ProGuard](http://proguard.sourceforge.net/), les limitations du format de fichier exécutable Dalvik deviennent un problème. Plus précisément, les limitations suivantes peuvent se produire :

1.  Limite de 65 Ko sur les champs
2.  Limite de 65 Ko sur les méthodes



### <a name="policy-enforcement-limitations"></a>Limitations concernant l’application de la stratégie

* **Capture d’écran**: le SDK ne peut pas appliquer une nouvelle valeur de capture d’écran dans les activités qui sont déjà passées par Activity.onCreate. Il peut en résulter une période au cours de laquelle l’application est configurée pour désactiver les captures d’écran ; toutefois, il est toujours possible d’en prendre.

* **Utilisation de programmes de résolution de contenu** : la stratégie Intune de transfert ou de réception peut bloquer entièrement ou en partie l’utilisation d’un programme de résolution de contenu pour accéder au fournisseur de contenu dans une autre application. Par conséquent, les méthodes ContentResolver retournent null ou lèvent une valeur d’échec (par exemple, `openOutputStream` lève `FileNotFoundException` en cas de blocage). L’application peut déterminer si l’échec de l’écriture des données par le biais d’un programme de résolution de contenu est causé par une stratégie (ou pourrait être causé par une stratégie) en appelant :

    ```java
    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI);
    ```

### <a name="exported-services"></a>Services exportés

 Le fichier AndroidManifest.xml inclus dans le SDK d’application Intune contient **MAMNotificationReceiverService**. Il doit s’agir d’un service exporté pour autoriser le portail d’entreprise à envoyer des notifications à une application compatible. Le service vérifie l’appelant pour s’assurer que seul le Portail d’entreprise est autorisé à envoyer des notifications.



## <a name="expectations-of-the-sdk-consumer"></a>Attentes du consommateur de SDK

Le SDK Intune respecte le contrat fourni par l’API Android, bien que des conditions d’échec puissent être déclenchées plus fréquemment à la suite de l’application de stratégies. Ces meilleures pratiques pour Android réduisent la probabilité d’un échec :

* Il est fort probable que les fonctions du SDK Android susceptibles de retourner null sont déjà null.  Pour réduire les problèmes, assurez-vous que les vérifications null sont placées au bon endroit.

* Les fonctionnalités qui peuvent faire l’objet d’une vérification doivent être vérifiées par l’intermédiaire de leurs API de substitution GAM.

* Les appels des fonctions dérivées doivent être acheminés aux versions de leurs superclasses.

* Évitez d’utiliser les API de façon ambiguë. Par exemple, l’utilisation de `Activity.startActivityForResult` sans vérifier requestCode entraîne un comportement étrange.

## <a name="recommended-android-best-practices"></a>Bonnes pratiques recommandées pour Android

* Tous les projets de bibliothèque doivent partager le même android:package dans la mesure du possible. Cela ne se traduit pas par un échec sporadique au moment de l’exécution. Il s’agit simplement d’un problème au moment de la génération. Les versions plus récentes du SDK d’application Intune supprimeront une partie de la redondance.

* Utilisez les outils de génération du SDK Android les plus récents.

* Supprimez toutes les bibliothèques inutiles et inutilisées (par exemple, android.support.v4).
