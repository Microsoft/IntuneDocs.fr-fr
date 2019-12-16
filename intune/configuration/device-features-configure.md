---
title: Créer un profil d’appareil iOS ou macOS avec Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil d’appareil iOS ou macOS, puis configurez les paramètres pour AirPrint, disposition de l’écran d’accueil, notifications des applications, appareil partagé, authentification unique et paramètres de filtre de contenu web dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d887c7bc3c7e9ea8b6719993b5ba4909e9c18ea8
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992923"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Paramètres des fonctionnalités de l’appareil iOS ou macOS dans Intune

Intune inclut de nombreuses fonctionnalités et paramètres qui aident les administrateurs à contrôler des appareils iOS et macOS. Par exemple, les administrateurs peuvent faire ce qui suit :

- Autoriser les utilisateurs à accéder à des imprimantes AirPrint sur votre réseau
- Ajouter des applications et dossiers à l’écran d’accueil, notamment ajouter de nouvelles pages
- Choisir si et comment des notifications de l’application s’affichent
- Configurer l’écran de verrouillage pour afficher un message ou l’étiquette d’inventaire, en particulier pour les appareils partagés
- Donner aux utilisateurs une expérience d’authentification unique sécurisée pour partager des informations d’identification entre les applications
- Filtrer les sites web qui utilisent du langage réservé aux adultes et autoriser ou bloquer des sites web spécifiques

Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités dans un profil, vous les envoyez (push) ou déployez le profil aux appareils iOS et macOS dans votre organisation.

Cet article décrit les différentes fonctionnalités que vous pouvez configurer, et vous montre comment créer un profil de configuration d’appareil. Vous pouvez également voir tous les paramètres disponibles pour les appareils [iOS](ios-device-features-settings.md) et [macOS](macos-device-features-settings.md).

## <a name="airprint"></a>AirPrint

AirPrint est une fonctionnalité Apple qui permet aux appareils d’imprimer dans des fichiers sur un réseau sans fil. Dans Intune, vous pouvez ajouter des informations AirPrint à des appareils.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [AirPrint sur iOS](ios-device-features-settings.md#airprint) et [AirPrint sur macOS](macos-device-features-settings.md#airprint).

Pour plus d’informations sur l’impression, consultez [À propos d’AirPrint](https://support.apple.com/HT201311) sur le site web d’Apple.

S’applique à :

- iOS 7.0 et versions ultérieures
- iPadOS 13.0 et versions ultérieures
- macOS 10.10 et ultérieur

## <a name="app-notifications"></a>Notifications d’applications

Choisissez la façon dont les applications sur vos appareils iOS et iPad reçoivent des notifications. Par exemple, à partir d’Intune, envoyez des notifications d’application afin qu’elles s’affichent dans le centre de notification ou sur l’écran de verrouillage, ou qu’elles émettent un son.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Notifications d’application sur iOS](ios-device-features-settings.md#app-notifications).

Pour plus d’informations sur cette fonctionnalité, consultez [Notifications](https://developer.apple.com/notifications/) sur le site web d’Apple.

S’applique à :

- iOS 9.3 et versions ultérieures
- iPadOS 13.0 et versions ultérieures

## <a name="associated-domains"></a>Domaines associés

Les domaines associés vous permettent de créer une relation entre vos domaines, par exemple `contoso.com`, et vos applications. Cette fonctionnalité vous permet d’effectuer les opérations suivantes :

- Partager des données et informations d’identification entre les applications et sites web de votre organisation.
- Utiliser des fonctionnalités d’application basées sur votre site web, telles que l’extension d’application d’authentification unique, les liens universels et le remplissage automatique de mot de passe.

  Par exemple, créez un domaine associé pour autoriser le remplissage automatique du mot de passe afin de recommander des informations d’identification, comme un mot de passe, pour les sites web associés à votre application.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Domaines associés sur macOS](macos-device-features-settings.md#associated-domains).

Pour plus d’informations sur cette fonctionnalité, consultez [Configuration des domaines associés à une application](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) sur le site web d’Apple.

S’applique à :

- macOS 10.15 et ultérieur

## <a name="home-screen-layout"></a>disposition de l’écran d’accueil

Ces paramètres configurent la disposition des applications et des dossiers sur les écrans d’ancrage et d’accueil des appareils iOS et iPadOS. Vous pouvez :

- Utilisez les paramètres **Dock** pour ajouter des applications ou des dossiers à l’écran. Par exemple, affichez Safari et l’application Mail sur l’espace d’ancrage de l’appareil.
- Ajoutez les **Pages** que vous souhaitez afficher sur l’écran d’accueil et les applications à afficher dans chaque page. Par exemple, ajoutez une page **Contoso** et ajoutez l’application Paramètres sur cette page.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Disposition de l’écran d’accueil sur iOS](ios-device-features-settings.md#home-screen-layout).

S’applique à :

- iOS 9.3 et versions ultérieures
- iPadOS 13.0 et versions ultérieures

## <a name="lock-screen-message"></a>Message d’écran de verrouillage

Utilisez ces paramètres pour afficher un texte ou un message personnalisé sur l’écran de verrouillage et dans la fenêtre de connexion, Par exemple, vous pouvez entrer un message de type « En cas de perte, renvoyez à », et afficher des informations d’étiquette d’inventaire.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Paramètres de message de l’écran de verrouillage sur iOS](ios-device-features-settings.md#lock-screen-message).

Pour plus d’informations sur le message de l’écran de verrouillage, consultez [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) sur le site web d’Apple.

S’applique à :

- iOS 9.3 et versions ultérieures
- iPadOS 13.0 et versions ultérieures

## <a name="login-items"></a>Éléments de connexion

Utilisez cette fonctionnalité pour choisir les applications, les applications personnalisées, les fichiers et les dossiers qui s’ouvrent quand les utilisateurs se connectent aux appareils.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Éléments de connexion sur macOS](macos-device-features-settings.md#login-items).

S’applique à :

- macOS 10.13 et versions ultérieures

## <a name="login-window"></a>Fenêtre de connexion

Contrôlez l’apparence de l’écran de connexion et des fonctions disponibles pour les utilisateurs avant qu’ils se connectent. Par exemple, ajoutez une bannière avec un message personnalisé, choisissez si le bouton de mise en veille s’affiche, et bien plus encore.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Fenêtre de connexion sur macOS](macos-device-features-settings.md#login-window).

S’applique à :

- macOS 10.7 et ultérieur

## <a name="single-sign-on"></a>Authentification unique

La plupart des applications métier nécessitent un certain niveau d’authentification utilisateur pour prendre en charge la sécurité. Dans de nombreux cas, le processus d’authentification oblige les utilisateurs à entrer les mêmes informations d’identification à plusieurs reprises. Pour améliorer l’expérience utilisateur, les développeurs peuvent créer des applications qui utilisent l’authentification unique (SSO). Ce type d’authentification permet de réduire le nombre de fois où l’utilisateur doit entrer ses informations d’identification.

L’authentification unique est possible si les conditions suivantes sont réunies :

- Vous devez avoir une application codée qui recherche le magasin d’informations d’identification utilisateur dans l’authentification unique sur l’appareil.
- Intune doit être configuré pour l’authentification unique des appareils iOS.

![Volet Authentification unique](./media/device-features-configure/sso-blade.png)

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Authentification unique sur iOS](ios-device-features-settings.md#single-sign-on).

S’applique à :

- iOS 7.0 et versions ultérieures
- iPadOS 13.0 et versions ultérieures

## <a name="single-sign-on-app-extension"></a>Extension d’application d’authentification unique

Ces paramètres configurent une extension d’application qui active l’authentification unique (SSO) pour vos appareils iOS, iPadOS et macOS. La plupart des applications métier et sites web d’organisation nécessitent un certain niveau de sécurité d’authentification des utilisateurs. Dans de nombreux cas, le processus d’authentification oblige les utilisateurs à entrer les mêmes informations d’identification à plusieurs reprises. L’authentification unique permet aux utilisateurs d’accéder aux applications et aux sites web après avoir entré leurs informations d’identification une seule fois. Une fois qu’ils se connectent, les utilisateurs peuvent accéder aux applications et aux sites web automatiquement, ou utiliser un Face ID, un Touch ID ou le code secret Apple pour y accéder.

Dans Intune, utilisez ces paramètres pour configurer une extension d’application d’authentification unique créée par votre organisation, un fournisseur d’identité ou Apple. L’extension d’application d’authentification unique gère l’authentification pour vos utilisateurs. Ces paramètres configurent les extensions d’application SSO de type de redirection et de type d’informations d’identification.

- Le type de redirection est conçu pour les protocoles d’authentification modernes, tels qu’OAuth et SAML2.
- Le type d’informations d’identification est conçu pour les flux d’authentification de type challenge et réponse. Vous pouvez choisir entre une extension d’informations d’identification spécifique à Kerberos fournie par Apple et une extension d’informations d’identification générique.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Extension d’application SSO iOS](ios-device-features-settings.md#single-sign-on-app-extension) et [Extension d’application SSO macOS](macos-device-features-settings.md#single-sign-on-app-extension).

Pour plus d’informations sur le développement d’une extension d’application SSO, consultez [Authentification unique d'entreprise extensible](https://developer.apple.com/videos/play/tech-talks/301) sur le site web d’Apple. Pour lire la description d’Apple de la fonctionnalité, consultez [Réglages des données utiles Extensions pour l’authentification unique](https://support.apple.com/guide/mdm/single-sign-on-extensions-mdmfd9cdf845/web). 

> [!NOTE]
> La fonctionnalité **Extension de l’application d’authentification unique** est différente de la fonctionnalité **Authentification unique** :
>
> - Les paramètres **Extension d’application d’authentification unique** s’appliquent à iPadOS 13.0 (et versions ultérieures), à iOS 13.0 (et versions ultérieures) et à macOS 10.15 (et versions ultérieures). Les paramètres de **l’authentification unique** s’appliquent à iPadOS 13.0 (et versions ultérieures) et à iOS 7.0 et versions ultérieures.
>
> - Les paramètres **Extension d’application d’authentification unique** définissent les extensions pouvant être utilisées par des fournisseurs d’identité ou des organisations pour offrir une expérience d’authentification d’entreprise transparente. Les paramètres d’**authentification unique** définissent des informations de compte Kerberos pour les cas où les utilisateurs accèdent aux serveurs ou aux applications.
>
> - **L’extension d’application d’authentification unique** utilise le système d’exploitation Apple pour l’authentification. Par conséquent, elle peut offrir à l’utilisateur final une meilleure expérience que celle de l’**authentification unique**.
>
> - Du point de vue du développement, avec l’**extension d’application d’authentification unique**, vous pouvez utiliser n’importe quel type d’authentification unique par redirection ou informations d’identification. Avec **l’authentification unique**, vous pouvez uniquement utiliser l’authentification unique Kerberos.
>
> - L’**extension d’application d’authentification unique** Kerberos a été développée par Apple et est intégrée aux plateformes iOS 13.0+ et macOS 10.15+. L’extension Kerberos intégrée peut être utilisée pour connecter les utilisateurs aux applications natives et sites web qui prennent en charge l’authentification Kerberos. L’**authentification unique** n’est pas une implémentation Apple de Kerberos.
>
> - L’**extension d’application d’authentification unique** Kerberos intégrée gère les défis Kerberos pour les applications et les pages web tout comme l’**authentification unique**. Toutefois, l’extension Kerberos intégrée prend en charge les modifications de mot de passe et se comporte mieux dans les réseaux d’entreprise. Lorsque vous choisissez entre l’**extension d’application d’authentification unique** Kerberos et l’**authentification unique**, nous vous recommandons d’utiliser l’extension en raison des performances et des fonctionnalités améliorées.

S’applique à :

- iOS 13.0 et ultérieur
- iPadOS 13.0 et versions ultérieures
- macOS 10.15 et ultérieur

## <a name="wallpaper"></a>Papier peint

Ajoutez une image .png, .jpg ou .jpeg personnalisée sur vos appareils iOS supervisés. Par exemple, utilisez Intune pour ajouter un logo de société à l’écran de verrouillage sur vos appareils.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Papier peint sur iOS](ios-device-features-settings.md#wallpaper).

S’applique à :

- iOS
- iPadOS 13.0 et versions ultérieures

## <a name="web-content-filter"></a>Filtrage de contenu web

Ces paramètres peuvent utiliser l’algorithme intégré de filtre automatique d’Apple pour évaluer les pages web et bloquer le contenu pour adultes et le langage réservé aux adultes. Vous pouvez également créer une liste de liens web autorisés et de liens web restreints. Par exemple, vous pouvez uniquement autoriser l’ouverture de sites web `contoso`.

Pour obtenir la liste des paramètres que vous pouvez configurer dans Intune, consultez [Filtre de contenu web sur iOS](ios-device-features-settings.md#web-content-filter).

S’applique à :

- iOS 7.0 et versions ultérieures
- iPadOS 13.0 et versions ultérieures

## <a name="create-a-device-profile"></a>Créer un profil d’appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Attribuez un nom descriptif à la stratégie. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de stratégie correct est **macOS : Configure l’écran de connexion**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :  
        - **iOS/iPadOS**
        - **MacOS**
    - **Type de profil** : sélectionnez **Fonctionnalités de l’appareil**.

4. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Choisissez votre plateforme pour connaître les paramètres détaillés :

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [MacOS](macos-device-features-settings.md)

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et affiché dans la liste des profils. [Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Affichez tous les paramètres des fonctionnalités de l’appareil pour les appareils [iOS](ios-device-features-settings.md) et [macOS](macos-device-features-settings.md).
