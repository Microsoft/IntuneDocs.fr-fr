---
title: Préparer les applications pour la gestion d’applications mobiles avec Microsoft Intune
description: Cette rubrique présente des informations pour vous aider à déterminer quand utiliser l’outil de création de package de restrictions d’application et le SDK d’application pour permettre à vos applications métier personnalisées d’utiliser les stratégies de gestion d’applications mobiles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10b2ef5844c2d8889fd1d5c377fcefb8330be9e2
ms.sourcegitcommit: 93de3423d2d8f0019e676a63784edeb3daf47cb7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56325433"
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>Préparer les applications métier aux stratégies de protection des applications

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Vous pouvez configurer vos applications pour utiliser des stratégies de protection des applications à l’aide de l’outil de création de package de restrictions d’application Intune ou du SDK d’application Intune. Utilisez ces informations pour en savoir plus sur ces deux méthodes et quand les utiliser.

## <a name="intune-app-wrapping-tool"></a>Outil de création de package de restrictions d’application Intune
App Wrapping Tool est utilisé principalement pour les applications métier **internes**. Cet outil est une application en ligne de commande qui crée un wrapper autour de l’application, ce qui permet ensuite à l’application d’être gérée par une stratégie de protection des applications Intune. Lorsque l’application à protéger est fournie par un éditeur de logiciels indépendant (ISV), il est important de savoir si ce dernier prendra toujours en charge l’application une fois incluse dans un wrapper.

Vous n’avez pas besoin du code source pour utiliser l’outil, mais vous avez besoin des informations d’identification de signature. Pour plus d’informations sur les informations d’identification de signature, consultez le [blog Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Pour obtenir la documentation de l’outil de création de package de restrictions d’application, consultez [Android App Wrapping Tool](app-wrapper-prepare-android.md) (Outil de création de package de restrictions d’application Android) et [iOS App Wrapping Tool](app-wrapper-prepare-ios.md) (Outil de création de package de restrictions d’application iOS).

L’outil de création de package de restrictions d’application ne prend **pas** en charge les applications de l’Apple App Store ou du Google Play Store. Il ne prend pas non plus en charge certaines fonctionnalités qui nécessitent une intégration de développement (consultez le tableau comparatif des fonctionnalités suivant).

Pour plus d’informations sur l’outil de création de package de restrictions d’application pour les stratégies de protection des applications sur des appareils qui ne sont pas inscrits dans Intune, consultez [Protéger les données et applications métier sur des appareils non inscrits dans Microsoft Intune](apps-add.md).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Raisons d’utiliser l’outil de création de package de restrictions d’application
* Votre application n’a pas de fonctionnalités de protection des données intégrées
* Votre application est simple
* Votre application est déployée en interne
* Vous n’avez pas accès au code source de l’application
* Vous n’avez pas développé l’application
* Votre application a une authentification utilisateur minimale

### <a name="supported-app-development-platforms"></a>Plateformes de développement d’applications prises en charge

|**Outil de création de package de restrictions d’application** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Oui|Oui|
|**Android**|Non : utilisez les [liaisons Xamarin du SDK d’application Intune](app-sdk-xamarin.md).|Oui|

## <a name="intune-app-sdk"></a>Kit SDK d’application Intune
Le SDK d’application est conçu principalement pour les clients qui ont des applications dans l’Apple App Store ou dans le Google Play Store, et qui veulent gérer ces applications avec Intune. Cependant, toute application peut tirer parti de l’intégration du SDK, même s’il s’agit d’applications métier.

Pour en savoir plus sur le SDK, consultez sa [présentation](app-sdk.md). Pour commencer à utiliser le SDK, consultez [Prise en main du Kit SDK d’application Microsoft Intune](app-sdk-get-started.md).

### <a name="reasons-to-use-the-sdk"></a>Raisons d’utiliser le SDK
* Votre application n’a pas de fonctionnalités de protection des données intégrées
* Votre application est complexe et comprend de nombreuses expériences
* Votre application est déployée dans un App Store public tel que Google Play ou l’App Store d’Apple
* Vous êtes développeur d’applications et avez les compétences techniques pour utiliser le SDK
* Votre application présente d’autres intégrations de SDK
* Votre application est fréquemment mise à jour

### <a name="supported-app-development-platforms"></a>Plateformes de développement d’applications prises en charge

|**SDK d’application Intune** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Oui : utilisez les [liaisons Xamarin du SDK d’application Intune](app-sdk-xamarin.md).|Non|
|**Android**| Oui : utilisez les [liaisons Xamarin du SDK d’application Intune](app-sdk-xamarin.md).|Non|

## <a name="feature-comparison"></a>Comparaison des fonctionnalités
Ce tableau répertorie les paramètres que vous pouvez utiliser pour le Kit SDK et pour l’outil de création de package de restrictions d’application.

> [!NOTE]
> Vous pouvez utiliser l’outil de création de package de restrictions d’application avec Intune autonome ou Intune avec Configuration Manager.

|Composant|Kit SDK d’application|Outil de création de package de restrictions d’application|
|-----------|---------------------|-----------|
|Afficher le contenu web uniquement dans Managed Browser|X|X|
|Empêcher les sauvegardes Android, iTunes ou iCloud|X|X|
|Autoriser l'application à transférer des données vers d'autres applications|X|X|
|Autoriser l'application à recevoir des données d'autres applications|X|X|
|Restreindre les opérations Couper, Copier et Coller avec d’autres applications|X|X|
|Demander un code confidentiel simple pour l'accès|X|X|
|Spécifier le nombre de tentatives avant réinitialisation du code confidentiel|X|X|
|Autoriser une empreinte digitale à la place du code confidentiel|X|X|
|Autoriser la reconnaissance faciale à la place du code PIN (iOS uniquement)|X|X|
|Exiger des informations d'identification d'entreprise pour l'accès|X|X|
|Bloquer l’exécution des applications gérées sur les appareils jailbroken ou rootés|X|X|
|Chiffrer les données de l'application|X|X|
|Revérifier les spécifications requises pour l’accès après un nombre de minutes spécifié|X|X|
|Spécifier la période de grâce hors connexion|X|X|
|Bloquer la capture d’écran (Android uniquement)|X|X|
|Prise en charge de GAM sans inscription de l’appareil|X|X|
|Réinitialisation complète de données d’applications|X|X|
|Réinitialisation sélective des données professionnelles et scolaires dans des scénarios multi-identités <br><br>**Remarque :** pour iOS, quand le profil de gestion est supprimé, l’application est également supprimée.|X||
|Empêcher « Enregistrer sous »|X||
|Configuration d'application ciblée|X||
|Prise en charge des identités multiples|X||
|Style personnalisable |X|||
|Connexions VPN d’application à la demande avec Citrix mVPN|X|X| 
|Désactiver la synchronisation des contacts|X|X|
|Désactiver l’impression|X|X|
|Exiger une version minimale de l’application|X|X|
|Exiger une version minimale du système d’exploitation (iOS et Android)|X|X|
|Exiger une version minimale du correctif de sécurité Android (Android uniquement)|X|X|
|Exiger une version minimale du SDK Intune pour iOS (iOS uniquement)|X|X|

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les stratégies de protection des applications et Intune, consultez les rubriques suivantes :

  - [Outil de création de package de restrictions d’application Android](app-wrapper-prepare-android.md)<br>
  - [Outil de création de package de restrictions d’application iOS](app-wrapper-prepare-ios.md)<br>
  - [Utiliser le SDK pour activer des applications pour la gestion des applications mobiles](app-sdk.md)
