---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833545"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>En développement pour Microsoft Intune - Août 2019

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

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>Contrôler le comportement de désinstallation de l’application iOS lors de la désinscription du périphérique <!-- 3504144 -->
Les administrateurs pourront gérer si une application est supprimée ou conservée sur un appareil quand l’appareil est désinscrit au niveau d’un utilisateur ou d’un groupe d’appareils. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Catégoriser les applications du Microsoft Store pour Entreprises <!-- 3926922 -->
Vous pouvez classer Microsoft Store pour les applications métier. Pour ce faire, choisissez **applications** > **clientes**  >  **Intuneapplications** > sélectionnez une application de >**d’Microsoft Store pour l’application métier**   > **Catégoried'** informations. Dans le menu déroulant, attribuez une catégorie.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation <!-- 2576686 -->
Les stratégies de protection des applications Intune (application) sur les appareils Android et iOS vous permettront de contrôler le contenu des notifications d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android <!-- 3041956  -->
Pour les installations d’applications disponibles sur les appareils avec profil professionnel Android, vous pouvez afficher l’état d’installation des applications, ainsi que la version installée des applications Google Play managées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](android-enterprise-overview.md) et [Type d’application Google Play gérée](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Certaines restrictions d’appareils iOS non supervisés seront supervisées uniquement avec la version iOS 13,0 <!-- 4867809  -->
Certains paramètres s’appliquent aux appareils supervisés à partir de la version 13,0 d’iOS. Ces paramètres incluent :

- App Store, affichage de document, jeux
  - App Store
  - Contenu explicite iTunes, musique, podcast ou Actualités
  - Ajout d’amis Game Center
  - Jeux multijoueur
- Applications intégrées
  - Appareil photo
    - FaceTime
  - Safari
    - Remplissage automatique
- Cloud et stockage
  - Sauvegarder sur iCloud
  - Bloquer la synchronisation des documents iCloud
  - Bloquer la synchronisation du trousseau iCloud

Si ces paramètres sont configurés et attribués à des appareils non supervisés avant la version iOS 13,0, les paramètres sont toujours appliqués à ces appareils non supervisés. Ils s’appliquent également après la mise à niveau des appareils vers iOS 13,0. Ces restrictions sont supprimées sur les appareils non supervisés qui sont sauvegardés et restaurés. 

Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](device-restrictions-ios.md).

S’applique à :  
- iOS 13,0 et versions ultérieures

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Nouveaux paramètres et modifications apportées aux paramètres existants pour restreindre les fonctionnalités sur les appareils iOS et macOS <!-- 4867699 4867709  -->
Vous pouvez créer des profils pour limiter les paramètres sur les appareils exécutant iOS et MacOS (**profils** >  **de configuration** > **d’appareil créer un profil**  > **iOS** **ouMacOS**pour le type de plateforme >**restrictionsd’appareil)** . Les fonctionnalités suivantes seront ajoutées :

- Dans **le**Cloud et le stockage  > **desrestrictions** >   **d’appareils MacOS** ,**utilisez le nouveau paramètre de remise pour** Empêchez les utilisateurs de commencer à travailler sur un appareil macOS et continuez à travailler sur un autre appareil macOS ou iOS.
  Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](device-restrictions-macos.md).
- Sur **les** > restrictions**d’appareils iOS, il existe quelques modifications:**
  - **Applications** >  **intégrées Rechercher mon iPhone (mode supervisé uniquement)** : nouveau paramètre qui bloque cette fonctionnalité dans la fonctionnalité Rechercher mon application. 
  - **Applications** >  **intégrées trouver mes amis (mode supervisé uniquement)** : nouveau paramètre qui bloque cette fonctionnalité dans la fonctionnalité Rechercher mon application. 
  - **Modification**sans fil >  **de l’État Wi-Fi (mode supervisé uniquement)** : nouveau paramètre qui empêche les utilisateurs d’activer ou de désactiver le Wi-Fi sur l’appareil.
  - **Clavier et dictionnaire** >  **QuickPath (mode supervisé uniquement)** : nouveau paramètre qui bloque la fonctionnalité QuickPath.
  - **Cloud et stockage**: **la continuation** d’activité est renommée **en**remise.

  Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](device-restrictions-ios.md).

S’applique à :  
- macOS 10,15 et versions ultérieures
- iOS 13 et versions ultérieures

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Contrôler les applications, les fichiers, les documents et les dossiers qui s’ouvrent quand l’utilisateur se connecte à des appareils macOS <!--3914202  -->
Vous pouvez activer et configurer les fonctionnalités sur les appareils MacOS (**profils** > **de configuration**  > **d’appareil créer** un profil >  **MacOS** pour plateforme >**lesfonctionnalités** de l’appareil pour le type de profil). 

De nouveaux paramètres d’éléments de connexion s’affichent pour contrôler les applications, fichiers, documents et dossiers ouverts lorsqu’un utilisateur se connecte à l’appareil inscrit. 

Pour voir les paramètres actuels, accédez à [Paramètres des fonctionnalités d’appareil macOS dans Intune](macos-device-features-settings.md).

S’applique à :  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Nouvelles fonctionnalités pour les appareils Android Enterprise dédiés en mode multi-application <!-- 3755304 3041943 3041946  -->
Vous pouvez contrôler les fonctionnalités et les paramètres dans une expérience de type plein écran sur vos appareils Android Enterprise dédiés. Pour ce faire, choisissez **configuration**  >  **de l’appareil profils créer unprofil** >  **Android Enterprise** >  **pour la plateforme** **> propriétaire de l’appareil uniquement** , restrictions de l’appareil pour le type de profil.

Les fonctionnalités suivantes seront ajoutées :
- **Périphériques dédiés** >  **multi-application**: **lebouton** Accueil virtuel peut être affiché en balayant sur l’appareil ou flottant à l’écran afin que les utilisateurs puissent le déplacer.
- **Périphériques** >  dédiés **multi-application** :**l'accès** au flash permet aux utilisateurs d’utiliser la torche. 
- **Périphériques** >  dédiés **multi-application** :**lecontrôle** du volume de média permet aux utilisateurs de contrôler le volume de média de l’appareil à l’aide d’un curseur. 
- **Périphériques** >  **dédiés multi-application**: activez un économiseur d’écran, téléchargez une image personnalisée et contrôlez le moment où l’écran de veille est affiché.

Pour voir les paramètres actuels, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

S’applique à :  
- Appareils dédiés Android Entreprise

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Nouveaux profils d’application et de configuration pour les appareils Android Enterprise entièrement gérés <!-- 3574215  -->
À l’aide de profils, vous serez en mesure de configurer les paramètres qui appliquent les paramètres VPN, de messagerie et Wi-Fi à vos appareils Android Enterprise entièrement gérés. Vous serez en mesure d’effectuer les opérations suivantes:
- Utilisez les profils d’application pour déployer les paramètres de messagerie Outlook, Gmail et Nine Work.
- Utilisez des profils de configuration d’appareil pour déployer des paramètres de certificat racine approuvés.
- Utilisez des profils de configuration d’appareil pour déployer des paramètres VPN et Wi-Fi.

Les utilisateurs s’authentifient avec leur nom d’utilisateur et leur mot de passe pour les profils VPN, Wi-Fi et de messagerie. Actuellement, l’authentification basée sur les certificats n’est pas disponible. 

S’applique à :  
- Android Entreprise complètement managé

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Prise en charge des profils VPN IKEv2 pour iOS <!-- 1943438 -->
Vous pourrez créer des profils VPN pour le client VPN natif iOS en utilisant le protocole IKEv2. IKEv2 est un nouveau type de connexion dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **VPN** comme type de profil > **Paramètres**.

Ces profils VPN configurent le client VPN natif. Par conséquent, aucune application cliente VPN n’est installée ou envoyée (par push) aux appareils gérés. Cette fonctionnalité nécessite que les appareils soient inscrits auprès d’Intune (inscription MDM).

Pour afficher les paramètres VPN actuels que vous pouvez configurer, consultez [Configurer les paramètres VPN sur les appareils iOS dans Microsoft Intune](vpn-settings-ios.md).

S’applique à : iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscription des appareils

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>Ignorer d’autres écrans dans l’Assistant Configuration <!--4877451 -->
Vous pouvez définir des profils de Programme d’inscription des appareils pour ignorer les écrans suivants de l’Assistant Configuration: 
- Extinction de l’écran
- Configuration Touch ID

Pour ce faire, accédez à **inscriptiond'**  > **appareil inscription** Apple > jetons**duprogrammed’inscription>** **choisissez un jeton > Profils** > Choisissez un profil > **propriétés** >  **modifier en regard de lapersonnalisation**de l’**Assistant Configuration**.
Pour plus d’informations sur la personnalisation de l’Assistant [configuration, consultez créer un profil ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)d’inscription Apple.

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Prise en charge des administrateurs d’appareils d’inscription Android <!-- 4869749  -->
L’option d’inscription de l’administrateur d’appareils Android sera ajoutée à la page**inscription Android (inscription** > **d’appareil Intune**  >  **Android inscription**). L’administrateur de l’appareil Android est toujours activé par défaut pour tous les locataires.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Pour les appareils iOS, personnalisez l’écran de confidentialité du processus d’inscription de l’Portail d’entreprise <!-- 4394993  -->
À l’aide de la démarque, vous serez en mesure de personnaliser l’écran de confidentialité de Portail d’entreprise que les utilisateurs finaux voient lors de l’inscription iOS. Plus précisément, vous serez en mesure de personnaliser la liste des éléments que votre organisation ne peut pas voir ou faire sur l’appareil.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Numéro de build inclus sur la page matérielle du périphérique Android <!-- 4461910  -->
Une nouvelle entrée sur la page matériel de chaque appareil Android inclut le numéro de version du système d’exploitation de l’appareil.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurer la limite de temps de nettoyage automatique des appareils jusqu’à 30 jours <!--4231059  -->
Vous serez en mesure de définir la limite de temps de nettoyage automatique des appareils sur 30 jours (au lieu de la limite actuelle de 90 jours) après la dernière connexion. Pour ce faire, accédez à **la**configuration > **appareilsIntuneconfigurer** > **les règlesde** > **nettoyage des appareils**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

### <a name="default-scope-tag----3702875---"></a>Balise d’étendue par défaut <!-- 3702875 -->
Une nouvelle balise d’étendue par défaut intégrée sera disponible. Tous les objets Intune non balisés qui prennent en charge les balises d’étendue sont automatiquement affectés à la balise d’étendue par défaut. La **balise d’étendue par défaut** sera ajoutée à toutes les attributions de rôles existantes pour maintenir la parité avec l’expérience d’administration dès aujourd’hui. Si vous ne souhaitez pas qu’un administrateur affiche des objets Intune avec des balises d’étendue par défaut, supprimez la balise d’étendue par défaut de l’attribution de rôle. Cette fonctionnalité est similaire à la fonctionnalité étendues de sécurité de System Center Configuration Manager.

<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="import-and-export-security-baselines------3408610------------"></a>Importer et exporter des lignes de base de sécurité    <!--3408610          -->  
Nous ajoutons la possibilité d’exporter et d’importer des lignes de base de sécurité. Cette fonctionnalité vous permet d’effectuer vos personnalisations avec vous et de les partager entre les environnements Intune.

<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.




