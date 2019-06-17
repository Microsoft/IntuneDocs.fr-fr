---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fab8f2be48a30f6ad058b3eeb6874a44ff04e6ac
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744311"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune. 

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
Vérifiez vos applications Microsoft, tierces et métier. Veillez à ce que toutes vos applications protégées par des stratégies de protection des applications Intune utilisent le SDK versions 8.1.1 ou ultérieures.

- Pour les applications métier : Vous devrez peut-être republier vos applications intégrées au SDK versions 8.1.1 ou ultérieures. Nous vous recommandons d’utiliser la dernière version du SDK. Pour plus d’informations sur la façon de préparer vos applications métier aux stratégies de protection des applications, consultez [Préparer les applications métier aux stratégies de protection des applications](../apps-prepare-mobile-application-management.md).
- Pour les applications Microsoft/tierces : Vérifiez que vous déployez la dernière version de ces applications vers vos utilisateurs.

Vous devez également mettre à jour votre documentation ou vos directives de développement le cas échéant afin d’intégrer ce changement dans la prise en charge du SDK.

#### <a name="additional-information"></a>Informations supplémentaires
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management
