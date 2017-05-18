---
title: "Prise en main du Kit de développement logiciel (SDK) d’applications Microsoft Intune | Documentation Microsoft"
description: Activez rapidement la gestion des applications mobiles (MAM) dans votre application mobile avec Microsoft Intune.
keywords: 
author: mtillman
manager: angrobe
ms.author: oydang
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 95c12111693e00fb6f67d20464dd159aeb4bb609
ms.lasthandoff: 04/14/2017


---

# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Prise en main du Kit de développement logiciel (SDK) d’applications Microsoft Intune

Ce guide va vous permettre d’activer rapidement votre application mobile pour les stratégies de protection d'applications mobiles (MAM) avec Microsoft Intune. Il peut s’avérer utile de comprendre d’abord les avantages du SDK d’application Intune, tels qu’ils sont expliqués dans la [présentation du Kit SDK d’application Intune](intune-app-sdk.md).

Le SDK d’application Intune, qui prend en charge des scénarios similaires sur iOS et Android, est destiné à créer une expérience cohérente entre les plateformes pour les administrateurs informatiques. Cependant, en raison des limitations de chaque plateforme, il existe de petites différences dans la prise en charge de certaines fonctionnalités.

## <a name="register-your-store-app-with-microsoft"></a>Inscrire votre application de Store auprès de Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Si votre application est interne à votre organisation et ne sera pas disponible publiquement :

Vous *n’avez pas besoin* d’inscrire votre application. Pour les applications métier internes, l’administrateur informatique déploie l’application en interne. Intune détectera que l’application a été créée avec le SDK et autorisera l’administrateur informatique à lui appliquer une stratégie de protection des applications. Vous pouvez passer à la section [Activer votre application iOS ou Android pour la stratégie de protection des applications](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Si votre application doit être publiée sur un App Store public, comme l’Apple App Store ou Google Play :

Vous _**devez**_ d’abord inscrire votre application auprès de Microsoft Intune et accepter les conditions d’inscription. Les administrateurs informatiques peuvent ensuite appliquer une stratégie de protection des applications à l’application concernée, qui apparaît comme un partenaire d’application Intune.

Tant que l’inscription n’est pas terminée et confirmée par l’équipe de Microsoft Intune, les administrateurs Intune ne peuvent pas appliquer une stratégie de protection des applications au lien ciblé de votre application. Microsoft ajoute également vos applications à sa [page de partenaires Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). L’icône de l’application y est affichée pour montrer qu’elle prend en charge les stratégies de protection des applications Intune.

Pour commencer le processus d’inscription, remplissez le [questionnaire de partenariat d’application Microsoft Intune](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

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

Si votre application est une application Xamarin ou Cordova, utilisez les variantes SDK suivantes :

* [Composant Xamarin du SDK d’application Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Plug-in Cordova du SDK d’application Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Nous vous recommandons de créer un compte GitHub que vous pouvez utiliser pour créer des copies et faire des extractions depuis nos référentiels. GitHub permet aux développeurs de communiquer avec notre équipe produit, de faire part de problèmes et de recevoir des réponses rapides, de consulter les notes de publication et de fournir des commentaires à Microsoft. Pour toute question sur Intune App SDK GitHub, contactez msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Activer votre application iOS ou Android pour la stratégie de protection des applications

Vous aurez besoin d'un des guides de développement suivants pour intégrer le SDK d’application Intune à votre application :

* **[Guide du Kit de développement logiciel (SDK) d’applications Intune pour les développeurs iOS](intune-app-sdk-ios.md)** : ce document vous guide tout au long des étapes à suivre pour activer votre application iOS native avec le SDK d’application Intune.

* **[Guide du Kit de développement logiciel (SDK) d’applications Intune pour les développeurs Android](intune-app-sdk-android.md)** : ce document vous guide tout au long des étapes à suivre pour activer votre application Android native avec le SDK d’application Intune.

* **[Guide du plug-in Cordova du SDK d’application Intune](intune-app-sdk-cordova.md)** : ce document vous aide à générer des applications iOS et Android avec Cordova pour les stratégies de protection des applications Intune.

* **[Guide du composant Xamarin du SDK d’application Intune](intune-app-sdk-xamarin.md)** : ce document vous aide à générer des applications iOS et Android avec Cordova pour les stratégies de protection des applications Intune.




## <a name="configure-telemetry-for-your-app"></a>Configurer la télémétrie pour votre application

Microsoft Intune collecte des données sur les statistiques d’utilisation pour votre application.

* **SDK d’application Intune pour iOS** : le SDK enregistre par défaut les données de télémétrie du SDK sur les événements d’utilisation. Ces données sont envoyées à Microsoft Intune.

    * Si vous choisissez de ne pas envoyer les données de télémétrie du SDK à Microsoft Intune à partir de votre application, vous devez désactiver la transmission de la télémétrie du SDK en définissant la propriété `MAMTelemetryDisabled` sur « YES » dans le dictionnaire IntuneMAMSettings.


* **SDK d’application Intune pour Android** : les données de télémétrie ne sont pas enregistrées via le SDK.

## <a name="next-steps-after-integration"></a>Étapes suivantes après intégration

### <a name="test-your-app"></a>Tester votre application
Après avoir terminé les étapes nécessaires pour intégrer votre application iOS ou Android au SDK d’application Intune, vous devez vérifier que toutes les stratégies de protection d’application sont activées et opérationnelles pour l’utilisateur final et l’administrateur informatique. Pour tester votre application intégrée, vous avez besoin des éléments suivants :

* **Compte de test Microsoft Intune**: pour tester votre application compatible avec Intune sur les fonctionnalités de protection des applications Intune, vous aurez besoin d'un compte Microsoft Intune.

    * Si vous êtes un éditeur de logiciels indépendant et que vous configurez vos applications de Store iOS ou Android pour qu’elles prennent en charge la stratégie de protection des applications Intune, vous recevez un code promotionnel à l’issue de votre inscription auprès de Microsoft Intune, comme indiqué durant l’étape d’inscription. Ce code promotionnel vous permettra de vous inscrire à une version d’évaluation de Microsoft Intune valable un an.

    * Si vous développez une application métier qui n’est pas destinée au Store, vous êtes tenu d’avoir accès à Microsoft Intune dans votre organisation. Vous pouvez aussi vous inscrire à une version d’évaluation gratuite de [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) valable un mois.

* **Stratégies de protection des applications Intune**: pour tester votre application avec toutes les stratégies de protection des applications Intune, vous devez connaître le comportement attendu pour chaque paramètre de la stratégie. Consultez les descriptions des [stratégies de protection des applications iOS](../deploy-use/ios-mam-policy-settings.md) et des [stratégies de protection des applications Android](../deploy-use/android-mam-policy-settings.md).

* **Dépannage** : si vous rencontrez des problèmes pendant que vous testez manuellement l’expérience utilisateur de votre application, consultez la section [Dépannage de MAM](../troubleshoot/troubleshoot-mam.md). Cet article propose une aide pour résoudre les problèmes courants, des boîtes de dialogue et des messages d’erreur qui peuvent s'afficher dans les applications compatibles avec Intune. 

### <a name="badge-your-app-optional"></a>Badger votre application (facultatif)

Après avoir vérifié que les stratégies de protection des applications Intune fonctionnent dans votre application, vous pouvez badge l’icône de votre application avec le logo de protection des applications Intune.

Ce badge indique aux administrateurs informatiques, utilisateurs finaux et clients Intune potentiels que votre application fonctionne avec les stratégies de protection des applications Intune. Il encourage l’utilisation et l’adoption de votre application par les clients Intune.

Le badge est une icône en forme de porte-documents, visible dans les exemples ci-dessous :

![Exemple de badge 1](../media/intune-app-badge/example-1.png) ![Exemple de badge 2](../media/intune-app-badge/example-2.png)

**Éléments nécessaires pour badger votre application** :

* Une application de manipulation d’image qui peut lire les fichiers **.eps**, ou une application Adobe qui peut lire les fichiers **.ai**.

* Vous trouverez les [ressources et directives du badge de l'application Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) sur Microsoft Intune GitHub.

