---
title: Prise en main du kit SDK d’application Microsoft Intune
description: Activez rapidement la gestion des applications mobiles (MAM) dans votre application mobile avec Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 3362de6231aa8b045d064d1f3764cb2b13f5be3c
ms.sourcegitcommit: 6ff5df63a2fff291d7ac5fed9c51417fe808650d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52167431"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Prise en main du Kit de développement logiciel (SDK) d’applications Microsoft Intune

Ce guide va vous permettre d’activer rapidement votre application mobile pour les stratégies de protection d'applications mobiles (MAM) avec Microsoft Intune. Il peut s’avérer utile de comprendre d’abord les avantages du SDK d’application Intune, tels qu’ils sont expliqués dans la [présentation du Kit SDK d’application Intune](app-sdk.md).

Le SDK d’application Intune, qui prend en charge des scénarios similaires sur iOS et Android, est destiné à créer une expérience cohérente entre les plateformes pour les administrateurs informatiques. Cependant, en raison des limitations de chaque plateforme, il existe de petites différences dans la prise en charge de certaines fonctionnalités.

## <a name="register-your-store-app-with-microsoft"></a>Inscrire votre application de Store auprès de Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Si votre application est interne à votre organisation et ne sera pas disponible publiquement :

Vous *n’avez pas besoin* d’inscrire votre application. Pour les applications métier internes, l’administrateur informatique déploie l’application en interne. Intune détectera que l’application a été créée avec le SDK et autorisera l’administrateur informatique à lui appliquer une stratégie de protection des applications. Vous pouvez passer à la section [Activer votre application iOS ou Android pour la stratégie de protection des applications](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Si votre application doit être publiée sur un App Store public, comme l’Apple App Store ou Google Play :

Vous _**devez**_ d’abord inscrire votre application auprès de Microsoft Intune et accepter les conditions d’inscription. Les administrateurs informatiques peuvent ensuite appliquer une stratégie de protection des applications à l’application gérée, qui apparaît comme un partenaire d’application Intune.

Tant que l’inscription n’est pas terminée et confirmée par l’équipe de Microsoft Intune, les administrateurs Intune ne peuvent pas appliquer une stratégie de protection des applications au lien ciblé de votre application. Microsoft ajoute également vos applications à sa [page de partenaires Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). L’icône de l’application y est affichée pour montrer qu’elle prend en charge les stratégies de protection des applications Intune.

Pour commencer le processus d’inscription et si vous n’utilisez pas déjà un contact Microsoft, remplissez le formulaire [Microsoft Intune App Partner Questionnaire](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

Nous utilisons les adresses e-mail répertoriées dans les réponses du questionnaire pour communiquer et continuer le processus d’inscription. Nous utilisons également l’adresse e-mail d’inscription pour vous contacter en cas de problème.

> [!NOTE]
> Toutes les informations collectées dans le questionnaire ci-dessus et par le biais des e-mails échangés avec l’équipe Microsoft Intune respectent la [déclaration de confidentialité Microsoft](https://www.microsoft.com/privacystatement/default.aspx).

**Ce qui se passe dans le processus d’inscription** :

1. Après l’envoi de votre questionnaire, nous vous contacterons par le biais de votre adresse e-mail d’inscription pour confirmer la bonne réception de votre formulaire ou vous demander des informations supplémentaires pour terminer l’inscription.

2. Une fois reçues toutes les informations nécessaires de votre part, nous vous enverrons le contrat de partenariat de l’application Microsoft Intune à signer. Ce contrat décrit les conditions que votre entreprise doit accepter avant de devenir partenaire de l’application Microsoft Intune.

3. Microsoft vous avertira également quand votre application sera inscrite auprès du service Microsoft Intune et quand elle sera proposée sur le site des [partenaires Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

4. Enfin, le lien ciblé de votre application est ajouté à la prochaine mise à jour mensuelle du service Intune. Par exemple, si les informations d’inscription sont complétées en juillet, le lien ciblé est pris en charge à la mi-août.

Si le lien ciblé de votre application vient à changer, vous devrez réinscrire votre application.

> [!NOTE]
> Veillez à nous prévenir si vous mettez à jour votre application avec une nouvelle version du SDK d’application Intune.

## <a name="download-the-sdk-files"></a>Télécharger les fichiers du SDK

Les SDK d’application Intune pour iOS et Android natifs sont hébergés sur un compte Microsoft GitHub. Ces référentiels publics contiennent les fichiers du SDK pour iOS et Android en mode natif, respectivement :

* [SDK d’application Intune pour iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK d’application Intune pour Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Si votre application est une application Xamarin, utilisez cette variante du SDK :

* [Liaisons Xamarin du SDK d’application Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Nous vous recommandons de créer un compte GitHub que vous pouvez utiliser pour créer des copies et faire des extractions depuis nos référentiels. GitHub permet aux développeurs de communiquer avec notre équipe produit, de faire part de problèmes et de recevoir des réponses rapides, de consulter les notes de publication et de fournir des commentaires à Microsoft. Pour toute question sur Intune App SDK GitHub, contactez msintuneappsdk@microsoft.com.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Activer votre application iOS ou Android pour la stratégie de protection des applications

Vous aurez besoin d'un des guides de développement suivants pour intégrer le SDK d’application Intune à votre application :

* **[Guide du Kit de développement logiciel (SDK) d’applications Intune pour les développeurs iOS](app-sdk-ios.md)** : ce document vous guide tout au long des étapes à suivre pour activer votre application iOS native avec le SDK d’application Intune.

* **[Guide du Kit de développement logiciel (SDK) d’applications Intune pour les développeurs Android](app-sdk-android.md)** : ce document vous guide tout au long des étapes à suivre pour activer votre application Android native avec le SDK d’application Intune.

* **[Guide des liaisons Xamarin du SDK d’application Intune](app-sdk-xamarin.md)** : ce document vous aide à générer des applications iOS et Android avec Xamarin pour les stratégies de protection des applications Intune.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Activer votre application iOS ou Android pour l’accès conditionnel basé sur l’application
 
 En plus de permettre la définition d’une stratégie de protection des applications pour votre application spécifique, les conditions suivantes sont requises pour que votre application puisse fonctionner correctement avec l’accès conditionnel basé sur l’application Azure ActiveDirectory (AAD) :
 
 * L’application est conçue avec la [bibliothèque d’authentification Azure ActiveDirectory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) et permet l’authentification d’AAD Broker.
 
 * L’[ID de client AAD](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) pour votre application doit être unique sur les plateformes iOS et Android.
 
## <a name="configure-telemetry-for-your-app"></a>Configurer la télémétrie pour votre application

Microsoft Intune collecte des données sur les statistiques d’utilisation pour votre application.

* **SDK d’application Intune pour iOS** : le SDK enregistre par défaut les données de télémétrie du SDK sur les événements d’utilisation. Ces données sont envoyées à Microsoft Intune.

    * Si vous choisissez de ne pas envoyer les données de télémétrie du SDK à Microsoft Intune à partir de votre application, vous devez désactiver la transmission de la télémétrie du SDK en définissant la propriété `MAMTelemetryDisabled` sur « YES » dans le dictionnaire IntuneMAMSettings.

* **SDK d’application Intune pour Android** : le kit SDK d’application Intune pour Android ne contrôle pas la collecte de données à partir de votre application. Par défaut, l’application Portail d’entreprise enregistre des données de télémétrie. Ces données sont envoyées à Microsoft Intune. Conformément à la stratégie Microsoft, nous ne collectons aucune information d’identification personnelle (PII). 

    * Si les utilisateurs finaux choisissent de ne pas envoyer ces données, ils doivent désactiver la télémétrie sous Paramètres dans l’application Portail d’entreprise. Pour en savoir plus, consultez [Désactiver la collecte de données d’utilisation Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="line-of-business-app-version-numbers"></a>Numéros de version des applications métier

Les applications métier dans Intune affichent désormais le numéro de version des applications Android et iOS. Le numéro s’affiche dans le portail Azure, dans la liste des applications et dans le panneau de vue d’ensemble des applications. Les utilisateurs finaux peuvent voir le numéro d’application dans l’application Portail d’entreprise et dans le portail web.

### <a name="full-version-number"></a>Numéro de version complet

Le numéro de version complet identifie une version spécifique de l’application. Le numéro apparaît sous la forme _Version_(_Build_). Par exemple, 2.2(2.2.17560800). 

Le numéro de version complet est composé de deux éléments :

 - **Version**  
   Le numéro de version est le numéro de version explicite de l’application. Il est utilisé par les utilisateurs finaux pour identifier les différentes versions de l’application.

 - **Numéro de build**  
    Le numéro de build est un numéro interne qui peut être utilisé pour la détection de l’application et pour gérer l’application par programmation. Le numéro de build fait référence à une itération de l’application qui référence les changements apportés au code.

### <a name="version-and-build-number-in-android-and-ios"></a>Numéro de version et de build dans Android et iOS

Android et iOS utilisent des numéros de version et de build en référence aux applications. Toutefois, les deux systèmes d’exploitation utilisent des significations qui leur sont propres. Le tableau suivant compare ces termes.

Quand vous développez une application métier pour une utilisation dans Intune, pensez à utiliser les numéros de version et de build. Les fonctionnalités de gestion d’une application Intune s’appuient sur des numéros **CFBundleVersion** (pour iOS) et **PackageVersionCode** (pour Android) significatifs. Ces numéros sont inclus dans le manifeste d’application. 

Intune|iOS|Android|Description|
|---|---|---|---|
Numéro de version|CFBundleShortVersionString|PackageVersionName |Ce numéro indique une version spécifique de l’application pour les utilisateurs finaux.|
Numéro de version|CFBundleVersion|PackageVersionCode |Ce numéro est utilisé pour indiquer une itération dans le code d’application.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
    Spécifie le numéro de version du bundle. Ce numéro identifie une version publiée de l’application. Le numéro est utilisé par les utilisateurs finaux pour référencer l’application.
- **CFBundleVersion**  
    Version de build de l’application, qui identifie une itération du bundle. Le numéro peut identifier une version ou un bundle non publié. Le numéro est utilisé pour la détection de l’application.

#### <a name="android"></a>Android

 - **PackageVersionName**  
    Numéro de version présenté aux utilisateurs. Cet attribut peut être défini sous forme de chaîne brute ou de référence à une ressource de chaîne. La chaîne n’a d’autre fin que d’être présentée aux utilisateurs.
 - **PackageVersionCode**  
    Numéro de version interne. Ce numéro est utilisé uniquement pour déterminer si une version est plus récente qu’une autre, la version la plus récente des deux portant un numéro plus élevé. Il ne s’agit pas de la version. 

## <a name="next-steps-after-integration"></a>Étapes suivantes après intégration

### <a name="test-your-app"></a>Tester votre application
Après avoir terminé les étapes nécessaires pour intégrer votre application iOS ou Android au SDK d’application Intune, vous devez vérifier que toutes les stratégies de protection d’application sont activées et opérationnelles pour l’utilisateur final et l’administrateur informatique. Pour tester votre application intégrée, vous avez besoin des éléments suivants :

* **Compte de test Microsoft Intune** : pour tester votre application gérée par Intune sur les fonctionnalités de protection des applications Intune, vous aurez besoin d’un compte Microsoft Intune.

    * Si vous êtes un éditeur de logiciels indépendant et que vous configurez vos applications de Store iOS ou Android pour qu’elles prennent en charge la stratégie de protection des applications Intune, vous recevez un code promotionnel à l’issue de votre inscription auprès de Microsoft Intune, comme indiqué durant l’étape d’inscription. Ce code promotionnel vous permettra de vous inscrire à une version d’évaluation de Microsoft Intune valable un an.

    * Si vous développez une application métier qui n’est pas destinée au Store, vous êtes tenu d’avoir accès à Microsoft Intune dans votre organisation. Vous pouvez aussi vous inscrire à une version d’évaluation gratuite de [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) valable un mois.

* **Stratégies de protection des applications Intune**: pour tester votre application avec toutes les stratégies de protection des applications Intune, vous devez connaître le comportement attendu pour chaque paramètre de la stratégie. Consultez les descriptions des [stratégies de protection des applications iOS](app-protection-policy-settings-ios.md) et des [stratégies de protection des applications Android](app-protection-policy-settings-android.md).

* **Dépannage** : si vous rencontrez des problèmes pendant les tests manuels de l’expérience utilisateur lors de l’installation de votre application, consultez [Résoudre les problèmes d’installation d’applications](troubleshoot-app-install.md). 

### <a name="give-your-app-access-to-the-intune-app-protection-service-optional"></a>Autoriser votre application à accéder au service de protection d’application Intune (facultatif)

Si votre application utilise ses propres paramètres Azure Active Directory (AAD) personnalisés pour l’authentification, les étapes suivantes doivent être effectuées pour les applications de magasin public, ainsi que les applications métier internes. Les étapes **n’ont pas besoin d’être effectuées si votre application utilise l’ID client par défaut du SDK Intune**. 

Une fois que vous avez inscrit votre application auprès d’un locataire Azure, et qu’elle s’affiche sous **Toutes les applications**, vous devez autoriser votre application à accéder au service de protection d’application Intune (précédemment appelé service MAM). Dans le portail Azure :

1.  Accédez au panneau **Azure Active Directory**.
2.  Sélectionnez la configuration d’**Inscription d’application** pour l’application.
3.  Dans **Paramètres**, sous l’en-tête **Accès d’API**, sélectionnez **Autorisation requise**. 
4.  Cliquez sur **+ Ajouter**.
5.  Cliquez sur **Sélectionner une API**. 
6.  Dans la zone de recherche, entrez **Gestion des applications mobiles Microsoft**.
7.  Sélectionnez **Gestion des applications mobiles Microsoft** dans la liste des API et cliquez sur Sélectionner.
8.  Sélectionnez **Lire et écrire les données de gestion d’application de l’utilisateur**.
9.  Cliquez sur **Terminé**.
10. Cliquez sur **Accorder des autorisations**, puis sur **Oui**. 

### <a name="badge-your-app-optional"></a>Badger votre application (facultatif)

Après avoir vérifié que les stratégies de protection des applications Intune fonctionnent dans votre application, vous pouvez badge l’icône de votre application avec le logo de protection des applications Intune.

Ce badge indique aux administrateurs informatiques, utilisateurs finaux et clients Intune potentiels que votre application fonctionne avec les stratégies de protection des applications Intune. Il encourage l’utilisation et l’adoption de votre application par les clients Intune.

Le badge est une icône en forme de porte-documents, visible dans les exemples ci-dessous :

![Exemple de badge 1](./media/badge-example-1.png) ![Exemple de badge 2](./media/badge-example-2.png)

**Éléments nécessaires pour badger votre application** :

* Une application de manipulation d’image qui peut lire les fichiers **.eps**, ou une application Adobe qui peut lire les fichiers **.ai**.

* Vous trouverez les [ressources et directives du badge de l'application Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) sur Microsoft Intune GitHub.
