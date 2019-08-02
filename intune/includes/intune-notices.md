---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 4423e731bc1538cd2454de32f0d50f2d08eedc69
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670919"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune. 


### <a name="decreasing-support-for-android-device-administrator"></a>Diminution du support pour l’administrateur d’appareil Android 
L’administrateur d’appareil Android (parfois appelé gestion Android « héritée » et publiée avec Android 2.2) est un moyen de gérer les appareils Android. Toutefois, des fonctionnalités de gestion améliorées sont désormais disponibles avec [Android Enterprise]( https://docs.microsoft.com/intune/connect-intune-android-enterprise) (fournie avec Android 5.0). Dans le but de passer à une gestion des périphériques modernes, plus riche et plus sécurisée, Google diminue le support des administrateurs d’appareil dans les nouvelles versions Android.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
En raison de ces modifications apportées par Google, les utilisateurs Intune seront affectés des manières suivantes : 
- Intune pourra uniquement assurer le support des appareils Android gérés par l’administrateur d’appareil exécutant Android 10 et versions ultérieures (également appelé Android Q) jusqu’à l’été 2020. Il s’agit de la date à laquelle la prochaine version principale d’Android est censée être publiée.  
- Les appareils gérés par l’administrateur d’appareil qui exécutent Android 10 ou une version ultérieure après l’été 2020 ne peuvent plus être entièrement gérés.    
- Les appareils Android gérés par l’administrateur d’appareil qui restent sur les versions Android inférieures à Android 10 ne sont pas affectés et peuvent continuer à être entièrement gérés avec l’administrateur d’appareil.  
- Pour tous les appareils Android 10 et versions ultérieures, Google a limité la possibilité pour les agents de gestion des administrateurs d’appareil, notamment le Portail d’entreprise, d’accéder aux informations d’identification de l’appareil. Cela a un impact sur les fonctionnalités Intune suivantes après la mise à jour d’un appareil vers Android 10 ou version ultérieure : 
    - Le contrôle d’accès réseau pour VPN ne fonctionnera plus.  
    - L’identification des appareils comme appartenant à l’entreprise avec le numéro IMEI ou le numéro de série ne marque pas automatiquement les appareils comme appartenant à l’entreprise. 
    - Le numéro IMEI et le numéro de série ne seront plus visibles pour les administrateurs informatiques dans Intune. 
        > [!Note]
        > Cela affecte uniquement les appareils gérés par l’administrateur d’appareil sur Android 10 et versions ultérieures et n’affecte pas les appareils gérés comme Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Pour éviter la réduction des fonctionnalités de l’été 2020, nous vous recommandons d’effectuer les opérations suivantes :
- N’intégrez pas de nouveaux appareils dans la gestion des administrateurs d’appareil.
- Si un appareil est censé recevoir une mise à jour d’Android 10, migrez-le de la gestion de l’administrateur d’appareil vers la gestion Android Enterprise et/ou des stratégies de protection d’application.

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Mettre à jour votre application de Portail d’entreprise Android vers la dernière version <!--4536963-->
Intune publie régulièrement des mises à jour vers l’application Portail d’entreprise Android. En novembre 2018, nous avons publié une mise à jour du portail d’entreprise, incluant un commutateur principal pour vous préparer à la modification de Google à partir de leur plateforme de notification existante vers Firebase Cloud Messaging (FCM) de Google. Une fois que Google a retiré sa plateforme de notification et s’est déplacé vers FCM, les utilisateurs finaux doivent avoir mis à jour leur application Portail d’entreprise au moins vers la version de novembre 2018 pour continuer à communiquer avec Google Play Store.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Notre télémétrie indique que vous avez des appareils avec une version du Portail d’entreprise antérieure à 5.0.4269.0. Si cette version ou une version ultérieure de l’application Portail d’entreprise n’est pas installée, les professionnels de l’informatique lancent des actions telles que la réinitialisation de tout l’appareil, la réinitialisation du mot de passe, l’installation des applications disponibles et requises et l’inscription des certificats peut ne pas fonctionner comme prévu. Si vos appareils sont inscrits à la Gestion des données de référence dans Intune, vous pouvez voir les versions du portail d’entreprise et les utilisateurs en accédant à des applications clientes – applications découvertes. En sélectionnant les versions antérieures du Portail d’entreprise, vous pourrez voir ce quels utilisateurs finaux disposent des appareils qui n’ont pas de mises à jour du portail d’entreprise.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Demandez aux utilisateurs finaux d’appareils Android qui n’ont pas été mis à jour de mettre à jour le portail d’entreprise via Google Play. Informez le support technique au cas où un utilisateur n’a pas conservé la mise à jour automatique de l’application Portail d’entreprise. Consultez le lien informations supplémentaires pour en savoir plus sur la plateforme FCM et les modifications apportées par Google.

#### <a name="additional-information"></a>Informations supplémentaires
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Nouvelle expérience plein écran prochainement disponible sur Intune <!--4593669-->
Nous déployons actuellement une mise à jour des options de création et d’édition dans l’interface utilisateur Intune sur le portail Azure. Cette nouvelle expérience simplifiera les flux de travail existants grâce à un format de style assistant condensé au sein d’un seul panneau. Cette mise à jour fera disparaître la « prolifération de panneaux » ainsi que tous les flux de création et d’édition qui vous obligent à parcourir de façon approfondie une multitude de panneaux. Les flux de travail de création seront également à jour pour inclure des affectations (à l’exception de l’affectation d’applications).

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
L’expérience plein écran sera déployée sur Intune à la fois sur portal.azure.com et sur devicemanagement.microsoft.com dans les prochains mois. Cette mise à jour de l’interface utilisateur n’aura aucune incidence sur la fonctionnalité de vos stratégies et profils existants : vous bénéficierez simplement d’un flux de travail légèrement modifié. Lorsque vous créez des stratégies, par exemple, vous pourrez définir certaines attributions dans le cadre de ce flux au lieu d’effectuer cette opération après la création de la stratégie. Consultez le billet de blog de la section Informations supplémentaires pour obtenir des captures d’écran présentant la nouvelle expérience dans la console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Vous n’avez rien à faire, mais nous vous recommandons de mettre à jour vos ressources informatiques professionnelles. Nous mettrons à jour notre documentation à mesure que cette expérience est déployée sur les différents panneaux Intune dans le portail Azure.

#### <a name="additional-information"></a>Informations supplémentaires 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Modification planifiée : Intune est appelé à prendre en charge iOS versions 11 et ultérieures en septembre <!-- 4665342-->
En septembre, nous pensons qu’iOS 13 sera publié par Apple. L’inscription à Intune, le Portail d’entreprise et Managed Browser prendront en charge iOS versions 11 et ultérieures, peu de temps après la publication d’iOS 13.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Dans la mesure où les applications mobiles O365 seront prises en charge sur iOS versions 11.0 et ultérieures, vous ne serez pas affecté, vous aurez probablement déjà mis à niveau votre système d’exploitation ou vos appareils. Toutefois, si vous avez l’un des appareils listés ci-dessous ou que vous décidez d’inscrire l’un de ces appareils, sachez qu’ils ne prennent pas charge un système d’exploitation ultérieur à iOS 10. Ces appareils auront besoin d’être mis à niveau vers iOS versions 11 ou ultérieures :

- iPhone 5
- iPhone 5c
- iPad (4e génération)

À compter de juillet, les appareils inscrits à MDM utilisant iOS 10 et le Portail d’entreprise recevront une invite de mise à niveau du système d’exploitation ou de l’appareil. Si vous utilisez des stratégies de protection des applications, vous pouvez également définir le paramètre d’accès « Exiger une version minimale du système d’exploitation iOS (avertissement seulement) ».

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Vérifiez vos rapports Intune pour voir quels appareils ou utilisateurs sont concernés. Accédez à **Appareils** > **Tous les appareils**, puis filtrez par Système d’exploitation. Vous pouvez ajouter des colonnes supplémentaires pour aider à identifier les membres de votre organisation disposant d’appareils exécutant iOS 10. Demandez aux utilisateurs finaux de mettre à niveau leurs appareils avant septembre, avec une version de système d’exploitation prise en charge.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Modification planifiée : Prise en charge des versions 8.1.1 et ultérieures du SDK d’application Intune pour iOS <!-- 3586942-->
À compter de septembre 2019, Intune est appelé à prendre en charge les applications iOS avec le SDK d’application Intune versions 8.1.1 et ultérieures. Les applications créées avec des versions du SDK inférieures à 8.1.1 ne seront plus prises en charge. Ce changement entrera en vigueur avec la publication par Apple d’iOS 13, attendue en septembre prochain et annoncée dans MC181399.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Avec l’intégration du SDK d’application Intune ou de la création de package de restrictions d’application, vous pouvez protéger les données d’entreprise contre les applications et utilisateurs non approuvés par chiffrement des données. Le SDK d’application Intune pour iOS va utiliser des clés de chiffrement 256 bits par défaut lorsque le chiffrement sera activé par des stratégies de protection des applications Intune. Après ce changement, toutes les applications iOS sur les versions de SDK antérieures à 8.1.1, qui utilisent des clés de chiffrement 128 bits, ne seront plus en mesure de partager des données avec des applications intégrées au SDK 8.1.1 ou utilisant des clés 256 bits. Toutes les applications iOS auront besoin d’un SDK versions 8.1.1 ou ultérieures pour autoriser le partage de données protégées.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Vérifiez vos applications Microsoft, tierces et métier. Veillez à ce que toutes vos applications protégées par des stratégies de protection des applications Intune utilisent la version 8.1.1 du Kit de développement logiciel (SDK) ou versions ultérieures.

- Pour les applications métier : Vous devrez peut-être republier vos applications intégrées au SDK versions 8.1.1 ou ultérieures. Nous vous recommandons d’utiliser la dernière version du SDK. Pour plus d’informations sur la façon de préparer vos applications métier aux stratégies de protection des applications, consultez [Préparer les applications métier aux stratégies de protection des applications](../apps-prepare-mobile-application-management.md).
- Pour les applications Microsoft/tierces : Vérifiez que vous déployez la dernière version de ces applications vers vos utilisateurs.

Vous devez également mettre à jour votre documentation ou vos directives de développement le cas échéant afin d’intégrer ce changement dans la prise en charge du SDK.

#### <a name="additional-information"></a>Informations supplémentaires
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Modification planifiée : Nouveaux paramètres des mises à jour Windows dans Intune <!-- 4464404 -->
À partir de la version d’août du service Intune ou 1908, nous ajoutons de nouveaux « Paramètres d’échéance », que vous pouvez configurer à la place des paramètres « Autoriser l’utilisateur à redémarrer (redémarrage engagé) ». Nous prévoyons de désactiver les paramètres de redémarrage activés dans l’interface utilisateur de la version 1909 ou de la mise à jour de septembre, puis de les supprimer complètement de la console vers la fin octobre. 

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Si vous gérez des appareils Windows 10 dans votre environnement : 
- Avec la mise à jour Intune d’août ou la version 1908, vous verrez de nouveaux paramètres d’échéance dans la console en plus des anciens paramètres de redémarrage.
- Lorsque ces anciens et nouveaux paramètres sont configurés, les valeurs des paramètres d’échéance remplacent les valeurs du paramètre de redémarrage engagé.
- Les paramètres d’échéance remplacent l’option « Autoriser l’utilisateur à redémarrer (redémarrage engagé) » dans la console de la mise à jour 1910.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Commencez à utiliser les paramètres d’échéance dans la version 1908 en les configurant avec les valeurs souhaitées. Une fois cela en place, vous pouvez définir le paramètre de redémarrage engagé sur « Non configuré » pour préparer la suppression de ces paramètres de la console en octobre.

Mettez à jour votre documentation et tous les scripts d’automatisation si nécessaire. 

Nous vous tiendrons au courant et publierons un rappel dans le Centre de messages avant de supprimer les paramètres de redémarrage engagé.

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Modification planifiée : Les stratégies de protection des applications et du Kit de développement logiciel (SDK) des applications Intune pour Android évoluent vers le support d’Android 5.0 et versions ultérieures en octobre <!--4911065 -->
Intune passera au support d’Android 5.x (lollipop) et versions ultérieures en octobre. Mettez à jour les applications inclues dans un wrapper avec le dernier Kit de développement logiciel (SDK) des applications Intune et mettez à jour vos appareils.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Si vous n’utilisez pas ou si vous envisagez d’utiliser le Kit de développement logiciel (SDK) ou l’APP pour Android, cette modification n’aura aucun effet. Si vous utilisez le Kit de développement logiciel (SDK) d’applications Intune, veillez à mettre à jour vers la dernière version et à mettre à jour vos appareils vers Android 5.x et versions ultérieures. Si vous ne mettez pas à jour, les applications ne recevront aucune mise à jour et perdront en qualité au fil du temps. 

Vous trouverez ci-dessous une liste des appareils courants inscrits dans Intune qui exécutent Android version 4.x. Si vous avez l’un de ces appareils, prenez les mesures appropriées pour vous assurer que cet appareil prendra en charge Android version 5.0 ou ultérieure ou qu’il sera remplacé par un appareil qui prend en charge Android version 5.0 ou ultérieure. Cette liste n’est pas exhaustive de tous les appareils qui peuvent avoir besoin d’être évalués :
- Samsung SM-T561  
- Samsung SM-T365 
- Samsung GT-I9195 
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Incluez dans un wrapper vos applications avec le dernier Kit de développement logiciel (SDK) d’application Intune. Vous pouvez également définir le paramètre de lancement conditionnel « Exiger une version minimale du système d’exploitation (avertissement uniquement) » pour informer les utilisateurs finaux des appareils personnels à mettre à niveau.
