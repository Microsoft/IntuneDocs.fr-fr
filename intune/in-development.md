---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4bd5392abba3ea22127cb9bcbbb53ec4929f2d5e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166326"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>En développement pour Microsoft Intune - Septembre 2019

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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestion d'applications

### <a name="managed-google-play-private-lob-apps----1464182----"></a>Applications métier privées Google Play gérées <!-- 1464182  -->
Intune permettra aux administrateurs informatiques de publier des applications métier Android privées sur des Google Play gérés via un IFRAME incorporé dans la console Intune.  Actuellement, les administrateurs informatiques doivent publier des applications métier directement sur la console de publication de Google, ce qui nécessite de nombreuses étapes et prend beaucoup de temps.  Cette nouvelle fonctionnalité permet de faciliter la publication d’applications métier avec un ensemble minimal d’étapes sans avoir à sortir de la console Intune.  Les scénarios de gestion d’entreprise Android qui utilisent des Google Play gérés peuvent tirer parti de cette fonctionnalité (profil de travail, appareils dédiés, entièrement gérés et non inscrits).  Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Google Play géré** dans la liste **type d’application** . Pour plus d’informations sur les applications de Google Play gérées, consultez [Ajouter des applications de Google Play gérées à des appareils Android Enterprise avec Intune](apps-add-android-for-work.md).

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portail d’entreprise les messages d’état d’installation de l’application <!-- 2514416  -->
L’application Portail d’entreprise affiche des messages d’état d’installation d’application supplémentaires pour les utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.
- L’application a été correctement installée mais nécessite un redémarrage.
- L’application est en cours d’installation, mais nécessite un redémarrage pour continuer.

### <a name="managed-google-play-iframe-support----2871756----"></a>Prise en charge des Google Play iframe managés <!-- 2871756  -->
Intune fournit la prise en charge de l’ajout et de la gestion des liens Web directement dans la console Intune, via le Google Play iframe géré.  Cela permet aux administrateurs informatiques de soumettre une URL et une image d’icône, puis de les déployer sur des appareils comme des applications Android standard. Les scénarios de gestion d’entreprise Android qui utilisent des Google Play gérés peuvent tirer parti de cette fonctionnalité (profil de travail, appareils dédiés, entièrement gérés et non inscrits).  Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Google Play géré** dans la liste **type d’application** . Pour plus d’informations sur les applications de Google Play gérées, consultez [Ajouter des applications de Google Play gérées à des appareils Android Enterprise avec Intune](apps-add-android-for-work.md).

### <a name="macos-support-for-vpp-apps----3173501----"></a>Prise en charge macOS pour les applications VPP <!-- 3173501  -->
Les applications macOS, achetées à l’aide d’Apple Business Manager, s’afficheront dans la console lors de la synchronisation des jetons Apple VPP dans Intune. Vous pouvez attribuer, révoquer et réassigner des licences d’appareil et d’utilisateur pour des groupes à l’aide de la console. Microsoft Intune vous aide à gérer les applications VPP achetées pour une utilisation dans votre entreprise en :
- Signalant les informations de licence de l’App Store.
- Effectuant le suivi du nombre de licences utilisées.
- Vous empêchant d’installer davantage de copies de l’application que vous n’en possédez.
Pour plus d’informations sur Intune et VPP, consultez [Gérer les applications et les livres achetés en volume avec Microsoft Intune](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>prise en charge macOS pour les applications web <!-- 3174427  -->
Vous pourrez installer les applications web, qui vous permettent d’ajouter un raccourci vers une URL sur le web, sur le Dock à l’aide du Portail d’entreprise macOS. Les utilisateurs finaux peuvent accéder à l’action **Installer** à partir de la page des détails de l’application pour une application web dans le Portail d’entreprise MacOS. Pour plus d’informations sur le type d’application **lien Web** , consultez [Ajouter des applications à Microsoft Intune](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Affecter Microsoft Edge Beta pour macOS <!-- 4678761  -->
Vous pourrez ajouter et affecter la dernière version de Microsoft Edge Beta à Intune pour les appareils macOS. Dans Intune, sélectionnez applications **clientes** > **applications** > **Ajouter une application** > **Microsoft Edge-MacOS**. Ensuite, affectez la version bêta de Microsoft Edge aux groupes prévus. Microsoft AutoUpdate (MAU) assure la mise à jour de Microsoft Edge. Pour plus d’informations sur Microsoft Edge, consultez [gérer l’accès Web à l’aide de Microsoft Edge avec Microsoft Intune](manage-microsoft-edge.md).

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Lire et écrire des opérations de API Graph pour les applications Intune <!-- 5031704  -->
Les applications peuvent appeler le API Graph Intune avec des opérations de lecture et d’écriture à l’aide de l’identité de l’application sans informations d’identification de l’utilisateur. Pour en savoir plus sur l’accès à l’API Microsoft Graph API pour Intune, consultez la section relative à [l’utilisation d’Intune dans Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation <!-- 2576686 -->
Les stratégies de protection des applications Intune (application) sur les appareils Android et iOS vous permettront de contrôler le contenu des notifications d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android <!-- 3041956  -->
Pour les installations d’applications disponibles sur les appareils avec profil professionnel Android, vous pouvez afficher l’état d’installation des applications, ainsi que la version installée des applications Google Play managées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](android-enterprise-overview.md) et [Type d’application Google Play gérée](apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>Les fonctionnalités de l’appareil, les restrictions de l’appareil et les profils d’extension pour les paramètres iOS et macOS sont affichés par type d’inscription. <!-- 4886161  -->

Dans Intune, vous créez des profils pour les appareils iOS et MacOS (**profils** > de**configuration** > d’appareil**créer un profil** > **iOS** ou **MacOS** pour les fonctionnalités de plateforme > **appareil** , **Restrictions d’appareil**ou **Extensions** pour le type de profil). Actuellement, les paramètres disponibles dans ces profils sont répertoriés. 

Dans une prochaine mise à jour, les paramètres disponibles dans le portail Intune sont catégorisés par le type d’inscription auquel ils s’appliquent :

- iOS
  - Tous les types d’inscription
  - Inscription des appareils et inscription automatique des appareils
  - Inscription automatique des appareils

- macOS
  - Tous les types d’inscription
  - Inscription des appareils
  - Inscription d’appareils automatisée et approuvée par l’utilisateur
  - Inscription automatique des appareils

S’applique à :

- iOS
  - [Fonctionnalités de l’appareil](ios-device-features-settings.md)
  - [Restrictions relatives aux appareils](device-restrictions-ios.md)

- macOS
  - [Fonctionnalités de l’appareil](macos-device-features-settings.md)
  - [Restrictions relatives aux appareils](device-restrictions-macos.md)
  - [Extensions](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>Nouveaux paramètres de contrôle vocal pour les appareils iOS supervisés exécutés en mode plein écran <!-- 4892835  -->

Dans Intune, vous pouvez créer des stratégies pour exécuter des appareils iOS supervisés comme une borne ou un appareil dédié (**profils** > de**configuration** > d’appareil**créer un profil** > **iOS** pour la plateforme >  **Restrictions d’appareil** pour le type de profil > **kiosque (mode supervisé uniquement)** ). 

Dans une prochaine mise à jour, vous pouvez contrôler les nouveaux paramètres suivants :

- **Contrôle vocal**: active le contrôle vocal sur l’appareil en mode plein écran.
- **Modification du contrôle vocal**: permet aux utilisateurs de modifier le paramètre de contrôle vocal sur l’appareil en mode plein écran.

Pour afficher les paramètres actuels, accédez à [iOS bornes (mode supervisé uniquement)](device-restrictions-ios.md#kiosk).

S’applique à :

- iOS 13.0 et versions ultérieures

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Utiliser l’authentification unique pour les applications et sites Web sur vos appareils iOS et macOS <!-- 4893175  -->
Dans une prochaine mise à jour, il y aura de nouveaux paramètres d’authentification unique pour les appareils iOS et MacOS (**profils** > de**configuration** > d’appareil**créer un profil** > **iOS** ou **MacOS** pour fonctionnalités de l' **appareil** > de la plateforme pour le type de profil).

Utilisez ces paramètres pour configurer une expérience d’authentification unique, en particulier pour les applications et les sites Web qui utilisent l’authentification Kerberos. Vous pouvez choisir entre une extension d’application d’authentification unique d’informations d’identification générique et une extension Kerberos intégrée à Apple.

Pour afficher les fonctionnalités actuelles de l’appareil que vous pouvez configurer, accédez à fonctionnalités de l' [appareil iOS](ios-device-features-settings.md) et fonctionnalités de l' [appareil MacOS](macos-device-features-settings.md).

S’applique à :

- iOS 13.0 et ultérieur
- macOS 10.15 et ultérieur

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Associer des domaines à des applications sur macOS 10.15 + appareils <!-- 4898079  -->
Sur les appareils MacOS, vous pouvez configurer différentes fonctionnalités et envoyer ces fonctionnalités sur vos appareils à l’aide d’une stratégie (**profils** > de**configuration** > d’appareil**créer un profil** > **MacOS** pour fonctionnalités de l' **appareil** > de la plateforme pour le type de profil). Dans une prochaine mise à jour, vous serez en mesure d’associer des domaines à vos applications. Cette fonctionnalité permet de partager des informations d’identification avec des sites Web associés à votre application et peut être utilisée avec l’extension d’authentification unique d’Apple, les liens universels et le remplissage automatique de mot de passe. 

Pour afficher les fonctionnalités actuelles que vous pouvez configurer, accédez à [paramètres des fonctionnalités de l’appareil MacOS dans Intune](macos-device-features-settings.md).

S’applique à :

- macOS 10.15 et ultérieur

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Utilisez « iTunes » et « apps » dans l’URL de l’App Store iTunes lors de l’émission ou du masquage d’applications sur des appareils iOS supervisés <!-- 4928474  --> 
Dans Intune, vous pouvez créer des stratégies pour afficher ou masquer des applications sur vos appareils iOS supervisés (**profils** > de**configuration** > d’appareil**créer un profil** > **iOS** pour la plateforme > **appareil restrictions** pour le type de profil > **afficher ou masquer des applications (mode supervisé uniquement)** ). 

Vous pouvez entrer l’URL de l’App Store iTunes, `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`telle que. Dans une prochaine mise à jour, vous serez en mesure d' `apps` utiliser `itunes` à la fois et dans l’URL, par exemple :

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Pour plus d’informations sur ces paramètres, consultez [afficher ou masquer des applications](device-restrictions-ios.md#show-or-hide-apps).

S’applique à :

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Prise en charge des profils VPN IKEv2 pour iOS <!-- 1943438 -->
Vous pourrez créer des profils VPN pour le client VPN natif iOS en utilisant le protocole IKEv2. IKEv2 est un nouveau type de connexion dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **VPN** comme type de profil > **Paramètres**.

Ces profils VPN configurent le client VPN natif. Par conséquent, aucune application cliente VPN n’est installée ou envoyée (par push) aux appareils gérés. Cette fonctionnalité nécessite que les appareils soient inscrits auprès d’Intune (inscription MDM).

Pour afficher les paramètres VPN actuels que vous pouvez configurer, consultez [Configurer les paramètres VPN sur les appareils iOS dans Microsoft Intune](vpn-settings-ios.md).

S’applique à : iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscription des appareils

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Par défaut, les nouveaux locataires sont éloignés de la gestion des administrateurs d’appareils Android <!-- 4869790  -->
Les fonctionnalités d’administrateur d’appareils Android ont été remplacées par Android Enterprise. Par conséquent, nous vous recommandons d’utiliser Android Enterprise pour de nouvelles inscriptions à la place. Dans une prochaine mise à jour, les nouveaux locataires devront suivre les étapes préalables suivantes de l’inscription Android pour utiliser la gestion des administrateurs d’appareils : accéder à l’inscription d'**appareils** >  **Intune** > inscription**Android** Les appareils **personnels et d’entreprise avec des privilèges** > d’administration d’appareils**utilisent l’administrateur de l’appareil pour gérer les appareils.**  > 

Les locataires existants ne subissent aucune modification dans leurs environnements. 

Pour plus d’informations sur l’administrateur d’appareils Android dans Intune, consultez inscription de l' [administrateur d’appareils Android](android-enroll-device-administrator.md).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Pour les appareils iOS, personnalisez l’écran de confidentialité du processus d’inscription du Portail d’entreprise <!-- 4394993  -->
À l’aide de Markdown, vous pourrez personnaliser l’écran de confidentialité du Portail d’entreprise que les utilisateurs finaux voient lors de l’inscription à iOS. Plus précisément, vous serez en mesure de personnaliser la liste des éléments que votre organisation ne peut pas voir ou faire sur l’appareil.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Déployer des mises à jour logicielles sur des appareils macOS <!-- 3194876 -->
Vous serez en mesure de déployer des mises à jour logicielles sur des groupes d’appareils macOS. Cette fonctionnalité comprend des mises à jour critiques, de microprogramme, de fichier de configuration et autres. Vous pouvez envoyer des mises à jour lors de l’archivage suivant de l’appareil ou sélectionner une planification hebdomadaire pour déployer les mises à jour dans ou les fenêtres hors temps que vous définissez. Cela vous aide quand vous souhaitez mettre à jour des appareils en dehors des heures de travail standard ou lorsque votre support technique est entièrement personnel. Vous obtiendrez également un rapport détaillé de tous les appareils macOS avec les mises à jour déployées. Vous pouvez affiner le rapport en fonction de l’appareil pour afficher les États des mises à jour particulières.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Envoyer des notifications personnalisées à un appareil <!-- 4928910  -->
Vous pouvez envoyer des notifications personnalisées à des appareils spécifiques sur lesquels l’application Portail d’entreprise ou Intune est installée. Pour ce faire, accédez à**appareils** >  **Intune** > **tous les appareils** > Choisissez un appareil **> plus** > **Envoyer une notification personnalisée**. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Mises à jour apportées aux fonctionnalités entièrement managées d’Android Enterprise <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Nous allons ajouter la prise en charge suivante pour les appareils Android entièrement gérés :

- Les certificats SCEP pour Android entièrement géré seront disponibles pour l’authentification par certificat sur les appareils gérés en tant que propriétaire de l’appareil. Les certificats SCEP sont déjà pris en charge sur les appareils de profil professionnel.  Avec les certificats SCEP pour le propriétaire de l’appareil, vous serez en mesure d’effectuer les opérations suivantes : <!-- 5227935 -->
    - créer un profil SCEP sous DO section of Android Enterprise
    - lier les certificats SCEP pour effectuer un profil Wi-Fi pour l’authentification
    - lier les certificats SCEP pour effectuer des profils VPN pour l’authentification
    - lier les certificats SCEP pour effectuer des profils de messagerie pour l’authentification (via la configuration de l’application)
- Les applications système seront prises en charge sur les appareils Android Enterprise. Dans Intune, vous allez ajouter une application de système d’entreprise Android en sélectionnant applications **clientes** > **applications** > **Ajouter**. Dans la liste **type d’application** , sélectionnez **application système Android Enterprise**. Pour plus d’informations sur l’ajout d’applications à Intune, consultez [Ajouter des applications à Microsoft Intune](apps-add.md). <!-- 4062195 -->
- Dans **conformité** > de l’appareil,**propriétaire**de l’appareil**Android Enterprise** > , vous pouvez créer une stratégie de conformité qui définit le niveau d’attestation Google SafetyNet.   <!-- 4631425 -->
- Sur les appareils Android Enterprise entièrement gérés, les fournisseurs de protection contre les menaces mobiles sont pris en charge. Dans **conformité** > de l’appareil,**propriétaire**de l’appareil**Android Enterprise** > , vous pouvez choisir un niveau de menace acceptable. <!-- 4631440 --> [Paramètres Android Entreprise pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune](compliance-policy-create-android-for-work.md#device-owner) répertorie les paramètres actuels.


S’applique à : 
- Appareils Android Entreprise complètement gérés

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

### <a name="updated-support-experience-------5012398------"></a>Expérience de support mise à jour   <!--  5012398    -->
Dans le cadre des améliorations continues, nous mettons à jour l’expérience de prise en charge dans la console pour Intune.  Nous allons améliorer la recherche et les commentaires dans la console pour les problèmes courants et rationaliser le flux de travail pour contacter le support technique.     

<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Protection contre les falsifications de l’antivirus Windows Defender  <!-- 4705448       -->
Nous allons ajouter une *protection contre les falsifications* aux paramètres que Intune peut gérer pour l’antivirus Windows Defender. Vous pouvez utiliser un profil de configuration d’appareil pour Windows 10 Endpoint Protection pour activer ou désactiver la protection contre les falsifications.  Pour plus d’informations sur la protection contre les falsifications, voir [empêcher la modification des paramètres de sécurité avec protection contre la falsification](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) dans la documentation Windows. 


<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.




