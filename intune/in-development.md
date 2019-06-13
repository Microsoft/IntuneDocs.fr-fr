---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc5ea7076e77e5071724168fab58fa78f59601c4
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744305"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>En développement pour Microsoft Intune - Juin 2019

Pour faciliter votre préparation et votre planification, cette page liste les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore publiées. De plus :

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité est lancée en production, en préversion ou en disponibilité générale, la description de la fonctionnalité disparaît de cette page et de la [page Nouveautés](whats-new.md).
- Cette page et la [page Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!Note]
> Ces éléments reflètent les attentes actuelles de Microsoft sur les fonctionnalités Intune qui apparaîtront dans une version future. Les dates et les fonctionnalités individuelles peuvent changer. Certains éléments en développement n’ont pas de description de fonctionnalité sur cette page.

**Flux RSS** : recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure

<!-- ***********************************************-->
### <a name="app-management"></a>Gestion d'applications

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Les utilisateurs d’un appareil peuvent voir toutes les applications gérées qu’ils ont installées ou tenté d’installer <!-- 2352913 -->
Le portail d’entreprise pour Windows liste toutes les applications gérées (qu’elles soient obligatoires ou disponibles), qui sont installées sur l’appareil d’un utilisateur. Les utilisateurs pourront voir les installations d’applications tentées et en attente ainsi que leur état actuel. Si votre organisation ne rend pas les applications obligatoires ou disponibles, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Les utilisateurs pourront également trier ou filtrer leurs applications par état de l’installation.

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956---"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android <!-- 3041956 -->
Pour les installations d’applications disponibles sur les appareils avec profil professionnel Android, vous pourrez afficher l’état d’installation des applications, ainsi que la version installée des applications de Google Play gérées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](android-enterprise-overview.md) et [Type d’application Google Play gérée](apps-add-android-for-work.md#managed-google-play-app-type).

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configurer le navigateur qui est autorisé à établir une liaison aux données de l’organisation <!-- 3145939 -->
Les stratégies de protection d’application Intune sur les appareils Android et iOS vous permettent de transférer des liens web de l’organisation vers un navigateur spécifique au-delà d’Intune Managed Browser ou de Microsoft Edge.  Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md).

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>Page des applications installées sur le site web Portail d’entreprise  <!-- 4224326 -->
Le [site web Portail d’entreprise](https://portal.manage.microsoft.com/) inclut une nouvelle page permettant d’afficher aux utilisateurs toutes les applications qui ont été installées sur leur appareil. Cette liste inclut les applications disponibles et les applications exigées par leur organisation. À partir de cette page, les utilisateurs pourront voir l’état des installations et l’état des exigences des applications sur leur appareil. Pour plus d’informations sur le site web Portail d’entreprise, consultez [Utilisation du site web Portail d’entreprise Intune](/intune-user-help/using-the-intune-company-portal-website.md) et [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md).

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>Appeler des opérations de lecture d’API Graph à partir d’une application sans informations d’identification d’utilisateur <!-- 4655885 -->
Les applications pourront appeler des opérations de lecture d’API Graph Intune avec leur identité sans informations d’identification d’utilisateur. Pour plus d’informations, consultez [Obtenir un accès utilisateur](https://docs.microsoft.com/graph/auth-v2-service).

<!-- ***********************************************-->
### <a name="device-configuration"></a>Configuration des appareils


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Prise en charge des profils VPN IKEv2 pour iOS <!-- 1943438 -->
Vous pourrez créer des profils VPN pour le client VPN natif iOS en utilisant le protocole IKEv2. IKEv2 est un nouveau type de connexion dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **VPN** comme type de profil > **Paramètres**.

Ces profils VPN configurent le client VPN natif. Par conséquent, aucune application cliente VPN n’est installée ou envoyée (par push) aux appareils gérés. Cette fonctionnalité nécessite que les appareils soient inscrits auprès d’Intune (inscription MDM).

Pour afficher les paramètres VPN actuels que vous pouvez configurer, consultez [Configurer les paramètres VPN sur les appareils iOS dans Microsoft Intune](vpn-settings-ios.md).

S’applique à : iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>Configurer les paramètres pour les extensions de noyau sur les appareils macOS <!-- 20430240 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme). Une prochaine mise à jour inclura un nouveau groupe de paramètres permettant de configurer et d’utiliser les extensions de noyau sur vos appareils.

S’applique à : macOS 10.13.2 et versions ultérieures

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Prise en charge de la base de référence lors d’une recherche par mot clé  <!-- 3082036         -->
Lors de la création ou de la modification d’un profil de base de référence de la sécurité, vous serez bientôt en mesure d’utiliser la fonction de *recherche* pour filtrer les paramètres qui s’affichent dans la console.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilisez « règles d’applicabilité » lors de la création de profils de configuration d’appareil Windows 10 <!-- 2549910 -->
Vous créez des profils de configuration d’appareil Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme). Vous serez en mesure de créer une **règle d’applicabilité** pour que le profil s’applique seulement à une édition spécifique ou à une version spécifique. Par exemple, vous créez un profil qui active certains paramètres de BitLocker. Une fois que vous avez ajouté le profil, utilisez une règle d’applicabilité pour que le profil s’applique seulement aux appareils exécutant Windows 10 Entreprise.

S’applique à : 
- Windows 10 et versions ultérieures

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>Le paramètre Applications du Store uniquement pour les appareils Windows 10 inclut des options de configuration supplémentaires <!-- 2697002  -->

Quand vous créez un profil de restrictions d’appareil pour les appareils Windows, vous pouvez utiliser le paramètre **Applications du Store uniquement** afin que les utilisateurs installent uniquement des applications de l’App Store Windows (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **Restrictions sur l’appareil** comme type de profil). Dans une prochaine mise à jour, ce paramètre sera développé pour prendre en charge davantage d’options. 

Pour consulter les paramètres actuels, accédez à la section [Paramètres des appareils Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités dans Intune](device-restrictions-windows-10.md#app-store).

S’applique à : Windows 10 et versions ultérieures

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Déployez plusieurs profils d’appareils Extensions de mobilité Zebra sur un appareil, sur le même groupe d’utilisateurs ou sur le même groupe d’appareils <!-- 4089955 -->
Dans Intune, vous pouvez utiliser des Extensions de mobilité (MX) Zebra dans un profil de configuration d’appareil pour personnaliser des paramètres, ou ajouter des paramètres non intégrés à Intune. Actuellement, vous pouvez déployer un profil sur un seul appareil. Dans une prochaine mise à jour, vous pourrez déployer plusieurs profils pour :

- Le même groupe d’utilisateurs
- Le même groupe d’appareils
- Un seul appareil

[Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Microsoft Intune](android-zebra-mx-overview.md) montre comment utiliser MX dans Intune.

S’applique à : Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Certains paramètres kiosque sur les appareils iOS sont définis avec « Bloquer » à la place de « Autoriser » <!-- 4404075  -->
Quand vous créez un profil de restrictions d’appareil sur des appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions sur l’appareil** comme type de profil > **Kiosque**), vous définissez le **Verrouillage automatique**, la **Modification de sonnerie**, la **Rotation de l'écran**, le **Bouton de veille de l’écran** et les **Boutons de volume**. 

Actuellement, ces paramètres sont configurés avec la valeur **Autoriser** (pour bloquer la fonctionnalité) ou **Non configuré** (pour autoriser la fonctionnalité). Dans une prochaine mise à jour, les valeurs seront **Bloquer** (pour bloquer la fonctionnalité) ou **Non configuré** (pour autoriser la fonctionnalité).

Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](device-restrictions-ios.md). 

S’applique à : iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>Utiliser Face ID pour l’authentification par mot de passe sur les appareils iOS <!-- 4490704  -->
Quand vous créez un profil de restrictions d’appareil pour les appareils iOS, vous pouvez utiliser une empreinte digitale comme mot de passe. Dans une prochaine mise à jour, les paramètres de mot de passe par empreinte digitale autoriseront également la reconnaissance faciale (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions sur l’appareil** comme type de profil > **Mot de passe**). Par conséquent, les paramètres suivants changent :

- **Déverrouillage par empreinte digitale** est désormais **Déverrouillage de Touch ID et Face ID**.
- **Modification de l’empreinte digitale (supervisé uniquement)** est désormais **Modification de Touch ID et Face ID (supervisé uniquement)** .

Face ID est disponible dans iOS 11.0 et versions ultérieures. Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](device-restrictions-ios.md#password).

S’applique à : iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>Les fonctionnalités des applications dépendent de la région des classifications lors de la limitation des fonctionnalités de jeu et de l’App Store dans les appareils iOS <!-- 4593948  -->
Dans les appareils iOS, vous pouvez autoriser ou restreindre les fonctionnalités liées au jeu, à l’App Store et à l’affichage de documents (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions sur l’appareil** comme type de profil > **App Store, affichage de documents, jeux**). Vous pouvez également choisir la région des classifications ; par exemple, les États-Unis. Dans une prochaine mise à jour, la fonctionnalité **Applications** deviendra un enfant de **Région des classifications** et dépendra de **Région des classifications**.

Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

S’applique à : iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>Modèles d’administration pour la stratégie de groupe     <!--  3510695 -->
Pour améliorer la sécurité des appareils dans le cloud, nous publierons des modèles d’administration qui vous permettront d’utiliser Intune pour configurer les paramètres de sélection d’une stratégie de groupe pour les PC Windows.  Ces modèles utilisent le fournisseur de services de configuration de stratégie pour fournir jusqu’à 2 500 paramètres supplémentaires à partir d’Office, de Windows et de OneDrive.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Nouveaux paramètres pour la base de référence de sécurité Windows  <!-- 3534649, 4217151          -->
Nous ajoutons de nouveaux paramètres à la base de référence de sécurité Windows. Le premier paramètre concerne la sécurité basée sur la virtualisation, qui nécessite la fonctionnalité de démarrage sécurisé. Le deuxième paramètre vous permettra de gérer l’activation vocale des applications Windows quand l’écran est verrouillé.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>Les bases de référence de sécurité seront en disponibilité générale  <!--  3785395       -->
La fonctionnalité Bases de référence de sécurité ne sera bientôt plus en préversion et sera en disponibilité générale. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Le modèle Base de référence de sécurité Windows sera en disponibilité générale   <!--  3794072       -->
Le modèle Base de référence de sécurité Windows ne sera bientôt plus en préversion et sera en disponibilité générale. La préversion du modèle va être retirée et un nouveau modèle sera disponible.

<!-- ***********************************************-->
### <a name="device-management"></a>Gestion des appareils

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Affecter des balises d’étendue à tous les appareils gérés d’un groupe de sécurité <!-- 3173810 -->
Actuellement, vous pouvez affecter une balise d’étendue à un appareil en accédant à la page **Propriétés** de chaque appareil individuel et en sélectionnant les balises d’étendue. Dans une prochaine mise à jour, vous pourrez affecter des balises d’étendue à un groupe de sécurité et tous les appareils qu’il contient seront également associés à ces balises. Pour ce faire, choisissez **Intune** > **Rôles** > **Étendue (balises)**  > **Créer** > **Étendue (balises)**  > choisissez les groupes auxquels vous voulez affecter la balise d’étendue. La balise d’étendue sera également affectée à tous les appareils présents dans ces groupes. Les balises d’étendue définies avec cette fonctionnalité remplacent les balises d’étendue définies avec le flux actuel de balises d’étendue d’appareil. (Dans une prochaine mise à jour, le flux actuel d’affectation de balises d’étendue à des appareils est effectué en lecture seule.)

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Voir le niveau du correctif de sécurité pour les appareils Android <!-- 4461911  -->
Vous pourrez voir le niveau du correctif de sécurité pour les appareils Android. Pour ce faire, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil > **Superviser** > **Matériel**.


<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.


