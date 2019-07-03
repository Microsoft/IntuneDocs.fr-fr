---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 756fafc02a6d64b1495a838ab8eee4130ee77361
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389335"
---
# <a name="whats-new-in-microsoft-intune"></a>Nouveautés de Microsoft Intune

Découvrez les nouveautés hebdomadaires dans Microsoft Intune. Vous pouvez également trouver des [annonces importantes](#notices), des [publications précédentes](whats-new-archive.md) et des informations sur [le mode de publication des mises à jour par le service Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Chaque [mise à jour mensuelle](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) peut mettre jusqu'à trois jours pour être déployée et le sera dans l’ordre suivant :
> - Jour 1 : Asie-Pacifique (APAC)
> - Jour 2 : Europe, Moyen-Orient et Afrique (EMEA)
> - Jour 3 : Amérique du Nord
> 
> Le lancement de certaines fonctionnalités peut s’étaler sur plusieurs semaines. Ces fonctionnalités risquent de ne pas être accessibles à tous les clients la première semaine.
>
> Consultez la [page En développement](in-development.md) pour obtenir une liste des fonctionnalités à venir dans une version.

**Flux RSS** : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-june-17-2019"></a>Semaine du 17 juin 2019   

### <a name="app-management"></a>Gestion d'applications

#### <a name="new-features-in-microsoft-intune-app"></a>Nouvelles fonctionnalités dans l’application Microsoft Intune
Nous avons ajouté de nouvelles fonctionnalités à l’application Microsoft Intune (préversion) pour Android. Les utilisateurs sur des appareils Android complètement managés peuvent maintenant :  

* afficher et gérer des appareils qu’ils ont inscrits via le Portail d’entreprise Intune ou l’application Microsoft Intune ;    
* contacter leur organisation pour bénéficier d’un support ;    
* envoyer leurs commentaires à Microsoft ;    
* afficher les conditions générales, si elles ont été définies par leur organisation.  

## <a name="week-of-june-10-2019"></a>Semaine du 10 juin 2019 

### <a name="app-management"></a>Gestion d'applications  

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Nouveaux exemples d’applications illustrant l’intégration du kit de développement logiciel (SDK) Intune disponible sur GitHub <!-- 2653471 -->
Le compte GitHub msintuneappsdk a ajouté de nouveaux exemples d'application pour iOS (Swift), Android, Xamarin.iOS, Xamarin Forms et Xamarin.Android. Ces applications sont censées remplacer notre documentation existante et fournir des exemples d’intégration du kit de développement logiciel (SDK) de l’application Intune dans vos propres applications mobiles. Si vous êtes développeur d’applications et que vous avez besoin de conseils supplémentaires concernant le kit de développement logiciel (SDK) Intune, consultez les exemples liés :
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) : une application de messagerie instantanée iOS native (Swift) qui utilise la bibliothèque d'authentification Azure Active Directory (ADAL) pour l’authentification répartie.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) : une application Android native de listes de tâches à effectuer qui utilise la bibliothèque d'authentification Active Directory pour l’authentification répartie.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) : application Xamarin.Android de listes de tâches à effectuer qui utilise la bibliothèque d'authentification Active Directory pour l’authentification répartie. Ce référentiel contient également l’application Xamarin.Forms.
- [Exemple d’application Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) : un exemple d’application « barebones ».

## <a name="week-of-may-27-2019"></a>Semaine du 27 mai 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Création de rapports pour les applications potentiellement dangereuses sur les appareils Android <!-- 4223162 -->
Intune fournit désormais des informations supplémentaires sur la création de rapports pour les applications potentiellement dangereuses sur les appareils Android. 

## <a name="week-of-may-20-2019"></a>Semaine du 20 mai 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="windows-company-portal-app----3316993---"></a>Application Portail d’entreprise Windows <!-- 3316993 -->
L’application Portail d’entreprise Windows a désormais une nouvelle page intitulée **Appareils**. La page **Appareils** montre aux utilisateurs finaux tous leurs appareils inscrits. Les utilisateurs voient cette modification dans le portail d’entreprise dès lors qu’ils utilisent la version 10.3.4291.0 et ultérieure. Pour plus d’informations sur la configuration du portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nom de l’attribut OrderID des appareils Autopilot changé en Balise de groupe <!-- 4659453 -->

Pour le rendre plus intuitif, le nom de l’attribut **OrderID** sur les appareils Autopilot est devenu **Balise de groupe**. Quand vous utilisez des fichiers CSV pour charger les informations des appareils Autopilot, vous devez utiliser Balise de groupe comme en-tête de colonne, et non plus OrderID.  

## <a name="week-of-may-13-2019"></a>Semaine du 13 mai 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise  <!-- 1927359 idready wnready-->
Sur les appareils déjà inscrits via l’Assistant Configuration avec l’une des méthodes d’inscription des appareils d’entreprise d’Apple, Intune ne prendra plus en charge le Portail d’entreprise lorsqu’il est installé manuellement par les utilisateurs finaux à partir de l’App store. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. 

Par ailleurs, l’écran **Identifier votre appareil** du Portail d’entreprise iOS est en cours de suppression. Par conséquent, les administrateurs qui souhaitent activer l’accès conditionnel ou déployer des applications d’entreprise doivent mettre à jour le profil d’inscription DEP. Cette exigence s’applique uniquement si l’inscription DEP est authentifiée avec l’Assistant Configuration. Dans ce cas, vous devez envoyer le Portail d’entreprise sur l’appareil. Pour ce faire, choisissez **Intune** > **Inscription d’appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisir un jeton > **Profils** > choisir un profil > **Propriétés** > définir **Installer le Portail d’entreprise** sur **Oui**.

Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurer comment les utilisateurs finaux mettent à jour une application métier (LOB) à l’aide d’une stratégie de protection d’application <!-- 3568384 -->
Vous pouvez maintenant configurer où vos utilisateurs finaux peuvent obtenir une version mise à jour d’une application métier (LOB). Les utilisateurs finaux voient cette fonctionnalité dans la boîte de dialogue **Version de l’application min** du lancement conditionnel qui invite les utilisateurs finaux à mettre à jour vers une version minimale de l’application métier. Vous devez fournir ces détails de mise à jour dans le cadre de votre stratégie de protection des applications métier (APPLICATION). Cette fonctionnalité est disponible sur iOS et Android. Sur iOS, cette fonctionnalité nécessite que l’application soit intégrée (ou incluse dans un wrapper à l’aide de l’outil correspondant) dans le kit de développement logiciel (SDK) Intune pour iOS version 10.0.7 ou supérieure. Sur Android, cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise. Pour configurer la façon dont un utilisateur final met à jour une application métier, cette dernière a besoin d’une stratégie de configuration d’application managée reçue avec la clé, `com.microsoft.intune.myappstore`. La valeur envoyée définit à partir de quel magasin de l’utilisateur final doit télécharger l’application. Si l’application est déployée via le Portail d’entreprise, la valeur doit être `CompanyPortal`. Pour tous les autres magasins, vous devez entrer une URL complète.

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Scripts PowerShell pour Intune Management Extension  <!-- 3734186 idready -->
Vous pouvez configurer des scripts PowerShell, qui s’exécuteront avec les privilèges Administrateur de l’utilisateur sur l’appareil. Pour en savoir plus, voir [Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune](intune-management-extension.md) et [Gestion de l’application Win32](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Gestion d’applications Android Entreprise <!-- 4459905 -->
Pour aider les administrateurs informatiques à configurer et à utiliser les fonctions de gestion d’applications Android Entreprise, Intune ajoute automatiquement quatre applications liées à cette solution dans la console d’administration Intune. Ces applications sont les suivantes :

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : cette application est utilisée pour les scénarios impliquant une instance Android Entreprise entièrement gérée.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ce logiciel vous aide à vous connecter à vos comptes lorsque vous utilisez la vérification à deux facteurs.
- **[Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : cette application est utilisée pour les scénarios impliquant des stratégies de protection des applications et des profils de travail Android Entreprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : cette fonctionnalité est utilisée pour les scénarios impliquant des kiosques/une instance Android Entreprise dédiée.

Auparavant, les administrateurs informatiques devaient manuellement rechercher et approuver ces applications dans le [store Google Play géré](https://play.google.com/store/apps) lors de la configuration. Cette modification supprime ces étapes manuelles, afin que la gestion de l’application Android Entreprise soit plus simple et plus rapide pour les clients.

Ces quatre fonctionnalités sont automatiquement ajoutées à la liste des applications Intune des administrateurs la première fois qu’ils connectent leur locataire Intune au store Google Play géré. Pour en savoir plus, voir [Connecter votre compte Intune à votre compte professionnel Android](connect-intune-android-enterprise.md). Pour les locataires qui ont déjà connecté leur locataire ou qui utilisent déjà Android Entreprise, les administrateurs n’ont pas besoin d’intervenir. Ces quatre applications s’afficheront automatiquement dans les 7 jours suivant la fin du lancement de service de mai 2019.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Mise à jour du connecteur de certificat PFX pour Microsoft Intune  <!-- 1533038 -->
Nous avons publié une mise à jour pour [PFX Certificate Connector pour Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) qui permet de résoudre le problème suivant : les certificats PFX existants sont continuellement retraités, ce qui entraîne l’arrêt du traitement des nouvelles demandes par le connecteur.

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Tâches de sécurité Intune pour Defender ATP (en préversion publique)     <!-- 3208597 -->
Dans la préversion publique, vous pouvez utiliser Intune pour gérer les [tâches de sécurité pour Microsoft Defender Advanced Threat Protection (ATP)](atp-manage-vulnerabilities.md). Cette intégration dans ATP ajoute une approche basée sur les risques de la détection, de la hiérarchisation et des mauvaises configurations des points de terminaison tout en réduisant le délai entre la découverte et la correction.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10 <!-- 3617671   idstaged-->
De nombreux appareils Windows 10 et ultérieur ont des circuits microprogrammés Module de plateforme sécurisée (TPM). Cette mise à jour inclut un nouveau paramètre de conformité, qui vérifie la version de la puce TPM sur l’appareil. 

La section [Paramètres de stratégie de conformité de Windows 10 et ultérieur](compliance-policy-create-windows.md#device-security) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Empêcher les utilisateurs finaux de modifier leur point d’accès personnel et désactiver la journalisation de serveur Siri sur des appareils iOS <!-- 4097904   -->  
Vous pouvez créer un profil de restrictions pour un appareil iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres, que vous pouvez configurer :

- **Applications intégrées** : Journalisation côté serveur pour les commandes de Siri
- **Sans fil** : Modification par l’utilisateur du point d’accès personnel (mode supervisé uniquement)

Pour afficher ces paramètres, accédez à [Paramètres d’application intégrée pour iOS](device-restrictions-ios.md#built-in-apps) et [Paramètres sans fil pour iOS](device-restrictions-ios.md#wireless).

S’applique à : iOS 12.2 et plus

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nouveaux paramètres de restriction pour les applications de salle de classe sur les appareils macOS <!-- 4097905   --> 
Vous pouvez créer des profils de configuration pour les appareils macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut les nouveaux paramètres pour les applications de salle de classe, l’option de blocage des captures d’écran et l’option de désactivation de la solution iCloud Photo Library.

Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](device-restrictions-macos.md).

S’applique à : macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Le paramètre du mot de passe iOS permettant d’accéder à l’App Store est renommé.<!-- 4557891  -->
Le paramètre **Mot de passe permettant d’accéder à l’App Store** est renommé pour **Demander le mot de passe iTunes Store pour tous les achats** (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour plateforme > **Restrictions d’appareil** pour type de profil > **App Store, affichage de documents et jeux**).

Pour afficher les paramètres disponibles, accédez aux [paramètres iOS App Store, affichage de documents et jeux](device-restrictions-ios.md#app-store-doc-viewing-gaming).

S’applique à : iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Base de référence de Microsoft Defender Advanced Threat Protection (préversion)  <!--  3754134 -->
Nous avons ajouté une préversion de base de référence de la sécurité pour les paramètres [Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md). Cette ligne de base est disponible lorsque votre environnement répond à la configuration requise pour l’utilisation de [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Une page d’état de l’inscription Windows (ESP) est désormais disponible <!-- 3605348 -->
La Page d’état d’inscription n’est désormais plus une préversion. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Mise à jour de l’interface utilisateur Intune : création d’un profil d'inscription Autopilot  <!-- 4593669 -->
L’interface utilisateur pour la création d’un profil d’inscription Autopilot a été mise à jour pour s’aligner sur les styles d’interface utilisateur d’Azure. Pour plus d’informations, consultez [Créer un profil d'inscription Autopilot](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). À l’avenir, des scénarios supplémentaires Intune seront actualisés conformément à ce nouveau style d’interface utilisateur.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Activer la réinitialisation d’Autopilot pour tous les appareils Windows <!-- 4225665 -->
La réinitialisation d’Autopilot fonctionne maintenant pour tous les appareils Windows, y compris ceux qui ne sont pas configurés pour utiliser la page d’état d’inscription. Si une page d’état d’inscription n’a pas été configurée pour l’appareil lors de son inscription initiale, l’appareil passera directement au bureau après la connexion. La synchronisation et l’affichage conforme dans Intune peuvent prendre jusqu’à huit heures. Pour plus d’informations, consultez [Réinitialiser les appareils par réinitialisation à distance de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Format IMEI exact non requis lors de la recherche dans Tous les appareils <!--30407680 -->
Vous n’aurez pas à inclure d’espaces dans les chiffres IMEI pour effectuer une recherche dans **Tous les appareils**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Application sur le portail Intune de la suppression d’un appareil sur le portail Apple <!--2489996 -->
Si un appareil est supprimé sur le portail du Programme d’inscription des appareils ou sur le portail Apple Business Manager, cette suppression est automatiquement appliquée à Intune lors de la synchronisation suivante.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>La Page d’état d’inscription effectue maintenant le suivi des applications Win32 <!-- 2714451 -->
Cela s’applique uniquement aux appareils exécutant Windows 10 version 1903 et versions ultérieures. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

### <a name="device-management"></a>Gestion des appareils

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Réinitialiser et effacer en bloc le contenu des appareils à l’aide de l’API Graph <!-- 3295288 -->
L’API Graph permet désormais de réinitialiser et d’effacer le contenu d’un maximum de 100 appareils à la fois.


### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Le rapport de chiffrement ne fait pas partie de la préversion publique   <!-- 4587546      -->
Le [rapport pour le chiffrement de lecteur BitLocker et d’appareil](encryption-monitor.md) est maintenant généralement disponible et ne fait plus partie de la préversion publique. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Signature Outlook et paramètres biométriques pour les appareils iOS et Android <!-- 4050557 -->
Vous pouvez maintenant spécifier si la signature par défaut est activée dans Outlook sur les appareils iOS et Android. De plus, vous pouvez choisir d’autoriser les utilisateurs à modifier le paramètre biométrique dans Outlook sur iOS.

## <a name="week-of-may-6-2019"></a>Semaine du 6 mai 2019 

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Prise en charge du contrôle d’accès réseau (NAC) pour l’accès F5 sur les appareils iOS <!-- 4500808 -->

F5 a publié une mise à jour vers BIG-IP 13 qui autorise la fonctionnalité NAC pour l’accès F5 sur iOS dans Intune. Pour utiliser cette fonctionnalité :

- Effectuez une mise à jour de BIG-IP avec la version 13.1.1.5 actualisée. BIG-IP 14 n’est pas pris en charge.
- Intégrez BIG-IP avec Intune pour le contrôle d’accès réseau. Étapes dans [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Cochez le paramètre **Activer le contrôle d'accès réseau (NAC)** dans le profil VPN dans Intune.

Pour voir le paramètre disponible, accédez à [Configurer les paramètres VPN sur les appareils iOS](vpn-settings-ios.md).

S’applique à : iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Mise à jour du connecteur de certificat PFX pour Microsoft Intune <!-- doc-vso 1521237  -->  
Nous avons publié une mise à jour pour le [connecteur de certificat PFX pour Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) qui baisse l’intervalle d’interrogation de 5 minutes à 30 secondes.

## <a name="week-of-april-22-2019"></a>Semaine du 22 avril 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Utiliser le Gestionnaire de conformité pour créer des évaluations pour Microsoft Intune<!-- 4404750 -->

Le [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) (qui ouvre un autre site Microsoft) est un outil d’évaluation des risques basés sur les workflows dans le portail Microsoft Service Trust. Il vous permet de suivre, d’attribuer et de vérifier les activités de conformité aux normes de votre organisation liées aux services Microsoft. Vous pouvez créer votre propre évaluation de conformité avec Office 365, Azure, Dynamics, les Services professionnels et Intune. Deux évaluations sont disponibles dans Intune : FFIEC et RGPD.

Le Gestionnaire de conformité vous permet de faire converger vos efforts en décomposant les contrôles : les contrôles gérés par Microsoft et les contrôles gérés par votre organisation. Vous pouvez effectuer les évaluations, puis les exporter et les imprimer.

La conformité au [FFIEC (Federal Financial Institutions examen Conseil)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (qui ouvre un autre site Microsoft) est un ensemble de normes applicables aux opérations bancaires en ligne émises par le FFIEC. Il s’agit de l’évaluation la plus demandée pour les établissements financiers qui utilisent Intune. Elle interprète la façon dont Intune aide à satisfaire les exigences de cybersécurité liées aux workloads dans le cloud public. L’évaluation FFIEC d’Intune est la deuxième évaluation FFIEC dans le Gestionnaire de conformité.

Dans l’exemple suivant, vous pouvez voir la répartition des contrôles FFIEC. Microsoft traite 64 contrôles. Vous êtes chargé des 12 autres contrôles.

![Consultez un exemple d’évaluation Intune pour le FFIEC, notamment les actions du client et les actions de Microsoft](./media/intune-ffiec-assessment-status.png)

Le [Règlement général sur la protection des données (RGPD)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (qui ouvre un autre site Microsoft) est une loi de l’Union européenne (UE) qui permet de protéger les droits des individus et leurs données. Le RGPD est l’évaluation la plus demandée pour permettre de se conformer aux réglementations sur la protection des données personnelles. 

Dans l’exemple suivant, vous voyez la répartition des contrôles RGPD. Microsoft traite 49 contrôles. Vous êtes chargé des 66 autres contrôles.

![Consultez un exemple d’évaluation Intune pour le RGPD, notamment les actions du client et les actions de Microsoft](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Semaine du 15 avril 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Chiffrement OpenSSL pour les stratégies de protection des applications Android <!-- 3747362 -->
Les stratégies de protection des applications Intune sur les appareils Android utilise désormais une bibliothèque de chiffrement OpenSSL qui est conforme à la norme FIPS 140-2. Pour plus d’informations, consultez la section [Chiffrement](app-protection-policy-settings-android.md#encryption) de [Paramètres de la stratégie de protection des applications Android dans Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Activer les dépendances d’application Win32 <!-- 2617348  -->
En qualité d’administrateur, vous pouvez exiger que les autres applications soient installées en tant que dépendances avant d’installer votre application Win32. Plus précisément, l’appareil doit installer la ou les applications dépendantes avant d’installer l’application Win32. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Sélectionnez **Application Windows (Win32)** comme **Type d’application**. Après avoir ajouté l’application, vous pouvez sélectionner **Dépendances** pour ajouter l’application dépendante qui doit être installée avant que l’application Win32 puisse être installée. Pour plus d’informations, consultez [Intune autonome - Gestion des applications Win32](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Informations sur l’installation de versions d’application pour les applications Microsoft Store pour Entreprises <!-- 3537391   -->
Les rapports d’installation des applications incluent des informations sur les versions d’application concernant Microsoft Store pour les applications métier. Dans Intune, sélectionnez **Applications clientes** > **Applications**. Sélectionnez une **Application du Microsoft Store pour Entreprises** , puis **État de l’installation de l’appareil** sous la section **Superviser**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Ajouts apportés aux règles de spécification des applications Win32 <!-- 3676883   -->
Vous pouvez créer des règles de spécification basées sur des scripts PowerShell, des valeurs de Registre et des informations sur le système de fichiers. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Application Windows (Win32)** comme **Type d’application** dans le panneau **Ajouter une application**.  Sélectionnez **Spécifications** > **Ajouter** pour configurer des règles de spécification supplémentaires. Ensuite, sélectionnez **Type de fichier**, **Registre** ou **Script** comme **Type de spécification**. Pour plus d’informations, consultez [Gestion des applications Win32](apps-win32-app-management.md).

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune <!-- 3695227  -->
Vous pouvez attribuer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune. Pour plus d’informations sur les applications Win32 dans Intune, consultez [Gestion des applications Win32](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---794259----"></a>La vue d’ensemble de l’appareil indique l’utilisateur principal <!--794259  -->
La page de vue d’ensemble de l’appareil indique l’utilisateur principal, également appelé utilisateur d’UDA (affinité entre appareil et utilisateur). Pour voir l’utilisateur principal d’un appareil, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil. L’utilisateur principal apparaît en haut de la page **Vue d’ensemble**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Création de rapports d’applications Google Play gérées supplémentaires pour les appareils avec profil professionnel Android Entreprise <!-- 4105925  -->
Pour les applications Google Play gérées qui sont déployées sur des appareils avec profil professionnel Android Entreprise, vous pouvez afficher le numéro de version spécifique de l’application installée sur un appareil. Cela concerne uniquement les applications obligatoires.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Claviers tiers iOS <!-- 4111843   -->
La prise en charge de la stratégie de protection des applications Intune pour le paramètre **Claviers tiers** pour iOS n’existe plus en raison d’un changement de plateforme iOS. Vous ne pouvez plus configurer ce paramètre dans la console d’administration Intune, ni l’appliquer sur le client dans le kit SDK de l’application Intune.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Définir les paramètres de connexion et contrôler les options de redémarrage sur les appareils macOS <!-- 1210083  -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de fenêtre de connexion, comme l’affichage d’une bannière personnalisée, le choix de la façon dont les utilisateurs se connectent, l’affichage ou le masquage des paramètres d’alimentation, et plus encore.

Pour afficher ces paramètres, accédez à [Paramètres des fonctionnalités d’appareil macOS](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurer le Wi-Fi sur les appareils dédiés des propriétaires d’appareils Android Entreprise s’exécutant en mode kiosque multi-application <!--3041940  -->
Vous pouvez activer des paramètres sur un propriétaire d’appareil Android Entreprise en cas d’exécution en tant qu’appareil dédié en mode kiosque multi-application. Dans cette mise à jour, vous pouvez permettre aux utilisateurs de configurer des réseaux Wi-Fi et à s’y connecter (**Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions sur l’appareil** pour le type de profil >  **Appareils dédiés** > **Mode kiosque** : **Multi-application** > **Configuration Wi-Fi**). 

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md).

S’applique à : Appareils dédiés Android Entreprise s’exécutant en mode kiosque multi-application


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurer le Bluetooth et l’appairage sur les appareils dédiés des propriétaires d’appareils Android Entreprise s’exécutant en mode kiosque multi-application <!-- 3041941  -->
Vous pouvez activer des paramètres sur un propriétaire d’appareil Android Entreprise en cas d’exécution en tant qu’appareil dédié en mode kiosque multi-application. Dans cette mise à jour, vous pouvez autoriser les utilisateurs finaux à activer le Bluetooth et à appairer les appareils en Bluetooth (**Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions sur l’appareil** pour le type de profil >  **Appareils dédiés** > **Mode kiosque** : **Multi-application** > **Configuration Bluetooth**). 

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md).

S’applique à : Appareils dédiés Android Entreprise s’exécutant en mode kiosque multi-application

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Créer et utiliser des profils de configuration d’appareils OEMConfig dans Intune <!-- 3305883  -->
Dans cette mise à jour, Intune prend en charge la configuration des appareils Android Entreprise avec OEMConfig. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres à des appareils Android Entreprise à l’aide d’OEMConfig (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme).

La prise en charge des fabricants OEM s’effectue actuellement par OEM. Si une application OEMConfig que vous voulez n’est pas disponible dans la liste des applications OEMConfig, contactez `IntuneOEMConfig@microsoft.com`.

Pour en savoir plus sur cette fonctionnalité, accédez à [Utiliser et gérer des appareils Android Entreprise avec OEMConfig dans Microsoft Intune](android-oem-configuration-overview.md).

S’applique à : Android Entreprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notifications Windows Update  <!-- 3316758, 3316782  -->
Nous avons ajouté deux *paramètres d’expérience utilisateur* aux configurations des anneaux de mise à jour Windows que vous pouvez gérer à partir de la console Intune. Vous pouvez désormais :
- Bloquer ou autoriser des utilisateurs à [rechercher des mises à jour Windows](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- Gérer le [niveau de notification Windows Update](windows-update-settings.md#windows-update-notification-level) que voient les utilisateurs.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nouveaux paramètres de restriction d’appareil pour les propriétaires d’appareils Android Entreprise <!-- 3574254  -->
Sur les appareils Android Entreprise, vous pouvez créer un profil de restriction d’appareil pour autoriser ou restreindre les fonctionnalités, définir des règles de mot de passe, et plus encore (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement > Restrictions sur l’appareil** pour le type de profil). 

Cette mise à jour inclut de nouveaux paramètres de mot de passe et permet un accès complet aux applications dans Google Play Store pour les appareils complètement gérés, entre autres. Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md). 

S’applique à : Appareils Android Entreprise complètement gérés

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10 <!-- 3617671 -->

Cette fonctionnalité a été différée et devrait être publiée ultérieurement.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Mise à jour des changements apportés à l’interface utilisateur pour le navigateur Microsoft Edge sur les appareils Windows 10 et versions ultérieures <!-- 3775833   -->
Quand vous créez un profil de configuration d’appareil, vous pouvez autoriser ou limiter les fonctionnalités Microsoft Edge sur les appareils Windows 10 et les versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** sur la plateforme > **restrictions d’appareil** pour le type de profil > **Navigateur Microsoft Edge**). Dans cette mise à jour, les paramètres Microsoft Edge sont plus descriptifs et plus faciles à comprendre. 

Pour voir ces fonctionnalités, accédez à [Paramètres de restriction d’appareil pour le navigateur Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

S’applique à : Windows 10 et versions ultérieures

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Prise en charge étendue des appareils Android Entreprise complètement gérés (préversion)  <!--   3903241, 3903244, 3903246   -->
Toujours dans la préversion publique, nous avons développé notre prise en charge des appareils Android Entreprise complètement gérés ([annoncée en janvier 2019](whats-new.md#week-of-january-14-2019) pour inclure les éléments suivants : 

- Sur les appareils dédiés et complètement gérés, vous pouvez créer des [stratégies de conformité](compliance-policy-create-android-for-work.md) pour inclure des règles de mot de passe et une configuration requise pour le système d’exploitation (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil** pour le type de profil). 

  Sur les appareils dédiés, l’appareil peut s’afficher comme étant **Non conforme**. L’accès conditionnel n’est pas disponible sur les appareils dédiés. Veillez à effectuer toutes les tâches ou actions pour obtenir des appareils dédiés conformes à vos stratégies attribuées.

- [Accès conditionnel](conditional-access.md) : les stratégies d’accès conditionnel qui s’appliquent à Android s’appliquent également aux appareils Android Entreprise complètement gérés. Les utilisateurs peuvent désormais inscrire leur appareil complètement géré dans Azure Active Directory à l’aide de l’**application Microsoft Intune**. Ensuite, recherchez et résolvez tous les problèmes de conformité pour accéder aux ressources de l’organisation.

- Nouvelle application utilisateur final (application Microsoft Intune) : il existe une nouvelle application utilisateur final pour les appareils Android complètement gérés appelée **Microsoft Intune**. Cette nouvelle application est légère et moderne, et offre des fonctionnalités similaires à celles de l’application Portail d’entreprise, mais pour les appareils complètement gérés. Pour plus d’informations, consultez [Application Microsoft Intune sur Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Pour configurer des appareils Android complètement managés, accédez à **Inscription des appareils** > **Inscription Android** > **Appareils des utilisateurs complètement managés appartenant à l’entreprise**. La prise en charge des appareils Android complètement gérés reste en préversion et certaines fonctionnalités Intune peuvent ne pas être entièrement opérationnelles.  

Pour en savoir plus sur cette préversion, consultez notre blog [Microsoft Intune - Preview 2 pour les appareils Android complètement gérés](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>Configurer le profil pour ignorer certains écrans lors de l’exécution de l’Assistant Configuration <!-- 2276470  wnstaged-->
Lors de la création d’un profil d’inscription macOS, vous pouvez le configurer pour ignorer les écrans suivants quand un utilisateur exécute l’Assistant Configuration :
- Apparence
- Display Tone (Indiquer la tonalité)
- iCloudStorage : si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple.  Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.
Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils ou Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Nommage d’appareils en bloc lors de l’inscription d’appareils iOS d’entreprise<!--3566569  -->
Quand vous utilisez l’une des méthodes d’inscription d’entreprise d’Apple (DEP/ABM/ASM), vous pouvez définir un format de nom d’appareil pour nommer automatiquement les appareils iOS entrants. Vous pouvez spécifier un format qui inclut le type d’appareil et le numéro de série dans votre modèle. Pour ce faire, choisissez **Intune** > **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription** > **Sélectionner un jeton** >**Créer un profil** > **Format de nommage d’appareil**. Vous pouvez modifier des profils existants, mais le nom sera appliqué uniquement aux appareils récemment synchronisés.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Mise à jour du message d’expiration par défaut dans la page d’état d’inscription <!-- 3959331 -->
Nous avons mis à jour le message d’expiration par défaut que les utilisateurs voient quand la page d’état d’inscription (ESP) dépasse la valeur de délai spécifiée dans le profil ESP. Le nouveau message par défaut est ce que les utilisateurs voient et ce qui les aide à comprendre les actions suivantes à entreprendre avec leur déploiement ESP.  

### <a name="device-management"></a>Gestion des appareils

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Mettre hors service les appareils non conformes  <!-- 1827291   -->
Cette fonctionnalité a été différée et devrait être publiée ultérieurement.


### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Changements de l’entrepôt de données Intune V1.0 se reflétant vers la version bêta <!-- 4403765 -->
Quand la version V1.0 a été introduite dans 1808, elle comportait certaines différences significatives par rapport à la version bêta de l’API. Dans 1903, ces changements seront reflétés dans la version bêta de l’API. Si vous avez des rapports importants qui utilisent la version bêta de l’API, nous vous recommandons vivement de passer ces rapports en version V1.0 afin d’éviter les changements cassants. Pour plus d’informations, consultez [Journal des changements pour l’API de l’entrepôt de données Intune](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Superviser l’état de la base de référence de sécurité (préversion publique) <!-- 3082047 --> 
Nous avons ajouté une [vue par catégorie](security-baselines-monitor.md#per-category-view) pour la supervision des bases de référence de sécurité. (Les bases de référence de sécurité restent en préversion). La vue par catégorie affiche chaque catégorie de la base de référence, ainsi que le pourcentage d’appareils appartenant à chaque groupe d’état pour cette catégorie. Vous pouvez maintenant voir combien d’appareils ne correspondent pas aux catégories individuelles, sont mal configurés ou ne sont pas applicables.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Balises d’étendue pour les jetons VPP Apple <!--2371886  -->
Vous pouvez maintenant ajouter des balises d’étendue à des jetons VPP Apple. Seuls les utilisateurs attribués avec la même balise d’étendue ont accès au jeton VPP Apple ayant cette balise. Les applications et livres électroniques VPP achetés avec ce jeton héritent de ses balises d’étendue. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Semaine du 1 avril 2019

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Mise à jour des connecteurs de certificat  <!-- ICM 113304612 -->
Nous avons publié des mises à jour à la fois pour le [connecteur de certificat Intune et le connecteur de certificat PFX](certficates-pfx-configure.md#whats-new-for-connectors). Les nouvelles versions résolvent plusieurs problèmes connus.  

### <a name="app-management"></a>Gestion d'applications

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Mise à jour de l’expérience utilisateur de l’application Portail d’entreprise pour iOS <!-- 2536024 -->
La page d’accueil de l’application Portail d’entreprise pour les appareils iOS a été repensée. Désormais, elle adhère davantage aux modèles d’interface utilisateur iOS, et fournit également une meilleure détectabilité des applications et des livres électroniques.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Changements apportés à l’inscription sur le portail d’entreprise pour les utilisateurs d’appareils iOS 12 <!--3448635 -->  
Les étapes et les écrans d’inscription iOS sur le portail d’entreprise ont été mis à jour afin de s’aligner avec les changements de l’inscription MDM publiés dans Apple iOS 12.2. Le workflow mis à jour invite les utilisateurs à effectuer les opérations suivantes :  

* Autoriser Safari à ouvrir le site web Portail d’entreprise et à télécharger le profil de gestion avant de retourner à l’application Portail d’entreprise.  
* Ouvrir l’application Paramètres pour installer le profil de gestion sur leur appareil.
* Retourner à l’application Portail d’entreprise pour terminer l’inscription.  

Pour connaître les étapes et les écrans d’inscription mis à jour, consultez [Inscrire un appareil iOS dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Semaine du 25 mars 2019

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Prise en charge de l’application Conformité de Power BI à partir du panneau Entrepôt de données dans Microsoft Intune <!-- 4260871 -->
Auparavant, le lien **Télécharger le fichier Power BI** dans le panneau **Entrepôt de données Intune** téléchargeait un rapport de l’entrepôt de données Intune (fichier .pbix). Ce rapport a été remplacé par l’application Conformité de Power BI. L’application Conformité de Power BI ne nécessite pas de chargement ou de configuration spéciaux. Elle s’ouvrira directement dans le portail en ligne Power BI et affichera des données spécifiquement pour votre locataire Intune en fonction de vos informations d’identification. Dans Intune, sélectionnez le lien **Configurer l’entrepôt de données Intune** à droite du panneau Intune. Cliquez ensuite sur **Obtenir l’application Power BI**. Pour plus d’informations, consultez [Se connecter à l’entrepôt de données avec Power BI](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Semaine du 18 mars 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Déployer Microsoft Visio et Microsoft Project <!-- 3725386  -->
Vous pouvez désormais déployer Microsoft Visio Pro pour Office 365 et le client de bureau Microsoft Project Online en tant qu’applications indépendantes pour les appareils Windows 10 à l’aide de Microsoft Intune, si vous possédez des licences pour ces applications. À partir d’Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Dans le panneau **Ajouter une application**, sélectionnez **Windows 10** comme **Type d’application**. Sélectionnez ensuite **Configurer la suite d’applications** pour sélectionner les applications à installer. Pour plus d’informations sur les applications Office 365 pour des appareils Windows 10, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Changement de nom du produit Microsoft Visio Pro pour Office 365 <!-- 3593653  -->
**Microsoft Visio Pro pour Office 365** s’appellera désormais **Microsoft Visio Online - Plan 2**.  Pour plus d’informations sur Microsoft Visio, consultez [Visio Online - Plan 2](https://products.office.com/visio/visio-online-plan-2). Pour plus d’informations sur les applications Office 365 pour des appareils Windows 10, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Paramètre de limite de caractères d’une stratégie de protection d’application Intune <!-- 3291302  -->
Les administrateurs Intune peuvent spécifier une exception au paramètre de stratégie **Restreindre les opérations Couper, Copier et Coller avec d’autres applications** de la stratégie de protection d’application Intune.  En tant qu’administrateur, vous pouvez spécifier le nombre de caractères qui peuvent être coupés ou copiés à partir d’une application gérée. Ce paramètre permet de partager le nombre spécifié de caractères avec toute application, quelle que soit la valeur du paramètre « Restreindre les opérations Couper, Copier et Coller avec d’autres applications ». Notez que la version de l’application Portail d’entreprise Intune pour Android exige la version 5.0.4364.0 ou une version ultérieure. Pour plus d’informations, consultez [Protection des données iOS](app-protection-policy-settings-ios.md#data-protection), [Protection des données Android](app-protection-policy-settings-android.md#data-protection) et [Consulter les journaux de la protection des applications clientes](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Code XML de l’outil Déploiement d’Office (ODT) pour le déploiement d’Office ProPlus <!-- 3192477   -->
Vous pourrez fournir le code XML de l’outil Déploiement d’Office (ODT) lors de la création d’une instance d’Office ProPlus dans la console d’administration Intune. Cela offre davantage de possibilités de personnalisation si les options existantes de l’interface utilisateur Intune ne répondent pas à vos besoins. Pour plus d’informations, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) et [Options de configuration pour l’outil Déploiement d’Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Les icônes d’application s’affichent désormais avec un arrière-plan généré automatiquement <!-- 1429026  -->
Dans l’application Portail d’entreprise Windows, des icônes d’application s’afficheront désormais avec un arrière-plan généré automatiquement en fonction de la couleur dominante de l’icône (si elle peut être détectée). S’il y a lieu, cet arrière-plan remplacera la bordure grise qui était précédemment visible sur les vignettes d’application. Les utilisateurs verront ce changement dans les versions du portail d’entreprise ultérieures à 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installer des applications disponibles à l’aide de l’application Portail d’entreprise après l’inscription en bloc de Windows <!-- 2751523   -->
Les appareils Windows inscrits auprès d’Intune à l’aide de l’[inscription en bloc de Windows](windows-bulk-enroll.md) (packages de provisionnement) pourront utiliser l’application Portail d’entreprise pour installer des applications disponibles. Pour plus d’informations sur l’application Portail d’entreprise, consultez [Ajouter manuellement l’application Portail d’entreprise Windows 10](store-apps-company-portal-app.md) et [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md).

> [!Note]
> Cette fonctionnalité n’est pas encore entièrement déployée sur tous les clients. Si vous ne pouvez pas utiliser le portail d’entreprise sur les appareils inscrits en bloc, vous devrez peut-être attendre jusqu’à ce que ce changement soit déployé sur votre compte.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>L’application Microsoft Teams peut être sélectionnée comme faisant partie de la suite d’applications Office <!-- 3828932  -->
L’application Microsoft Teams peut être incluse ou exclue dans l’installation de la suite d’applications Office ProPlus. Cette fonctionnalité fonctionne pour le numéro de build 16.0.11328.20116+ d’Office ProPlus. L’utilisateur doit se déconnecter puis se connecter à l’appareil pour terminer l’installation. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez l’un des types d’application de la **Suite Office 365**, puis sélectionnez **Configurer la suite d’applications**.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Démarrer automatiquement une application quand vous exécutez plusieurs applications en mode kiosque sur les appareils Windows 10 et les versions ultérieures <!-- 2351390 -->

Sur Windows 10 et les versions ultérieures, vous pouvez exécuter un appareil en mode kiosque et exécuter de nombreuses applications. Cette mise à jour comprend un paramètre **Démarrage automatique** (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil > **Kiosque multi-application**). Utilisez ce paramètre pour démarrer automatiquement une application quand l’utilisateur se connecte à l’appareil.

Pour obtenir la liste et la description de tous les paramètres kiosque, consultez [Paramètres d’appareil Windows 10 et versions ultérieures pour une exécution en tant que kiosque dans Intune](kiosk-settings-windows.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Les journaux des opérations donnent également des détails sur les appareils non conformes <!-- 4063755  -->
Lors du routage de journaux Intune vers des fonctionnalités de supervision Azure, vous pouvez également router les journaux des opérations. Dans cette mise à jour, les journaux des opérations fournissent également des informations sur les appareils non conformes. 

Pour plus d’informations sur cette fonctionnalité, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Router des journaux vers Azure Monitor dans un plus grand nombre de workloads Intune <!-- 3804627 -->
Dans Intune, vous pouvez router des journaux d’audit et des journaux des opérations vers des hubs d’événements, du stockage et de l’analytique des journaux d’activité dans Azure Monitor (**Intune** > **Supervision** > **Paramètres de diagnostic**). Dans cette mise à jour, vous pouvez router ces journaux dans un plus grand nombre de workloads Intune, notamment la conformité, les configurations, les applications clientes, entre autres. 

Pour en savoir plus sur le routage de journaux vers Azure Monitor, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Créer et utiliser Mobility Extensions sur les appareils Android Zebra dans Intune <!-- 3305880   -->
Dans cette mise à jour, Intune prend en charge la configuration des appareils Android Zebra. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres aux appareils Android Zebra à l’aide de profils Mobility Extensions (MX) générés par StageNow (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android** pour la plateforme > **Profil MX (Zebra uniquement)** pour le type de profil).

Pour plus d’informations sur cette fonctionnalité, consultez [Utiliser et gérer des appareils Zebra avec des extensions de mobilité dans Intune](android-zebra-mx-overview.md).

S’applique à : Android

### <a name="device-management"></a>Gestion des appareils

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Rapport de chiffrement pour les appareils Windows 10 (en préversion publique)<!-- 2351538 -->  
Utilisez le nouveau [rapport de chiffrement (préversion)](encryption-monitor.md) pour voir des détails sur l’état de chiffrement de vos appareils Windows 10. Les détails disponibles incluent la version TPM d’un appareil, la préparation et l’état du chiffrement, la création de rapports d’erreurs, et plus encore.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Accéder aux clés de récupération BitLocker à partir du portail Intune (en préversion publique) <!-- 2351547   -->  
Vous pouvez désormais utiliser Intune pour [afficher des détails](encryption-monitor.md) sur l’ID de clé BitLocker et les clés de récupération BitLocker à partir d’Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Prise en charge de Microsoft Edge pour des scénarios Intune sur des appareils iOS et Android <!-- 3411007 -->
Microsoft Edge prendra en charge les mêmes scénarios de gestion qu’Intune Managed Browser avec, en plus, des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise de Microsoft Edge qui sont activées par des stratégies Intune incluent la double identité, l’intégration de stratégies de protection des applications, l’intégration de proxy d’application Azure, ainsi que les raccourcis de page d’accueil et les favoris gérés. Pour plus d’informations, consultez [Prise en charge de Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Le connecteur Exchange Online/Intune cessera de prendre en charge les appareils uniquement EAS <!--3105122  -->
La console Intune ne prend plus en charge l’affichage et la gestion des appareils uniquement EAS connectés à Exchange Online avec le connecteur Intune. À la place, vous disposez des options suivantes :
- inscrire les appareils auprès de la gestion des appareils mobiles (MDM) ;
- utiliser des stratégies Intune App Protection pour gérer vos appareils ;
- utiliser les contrôles Exchange comme indiqué dans [Appareils clients et mobiles dans Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online).

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Rechercher un appareil précis dans la page Tous les appareils à l’aide de [nom] <!--4254930 -->
Vous pouvez désormais rechercher un nom de d’appareil exact. Accédez à **Intune** > **Appareils** > **Tous les appareils** > dans la zone de recherche, placez le nom de l’appareil entre {} pour rechercher un correspondance exacte. Par exemple, **{Appareil12345}** .

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Prise en charge de connecteurs supplémentaires dans la page État du locataire <!-- 3617202  -->
La [page État du locataire](tenant-status.md) affiche maintenant des informations sur l’état des connecteurs supplémentaires, notamment *Windows Defender - Protection avancée contre les menaces* (ATP) et d’autres connecteurs Mobile Threat Defense.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Octroi d’un accès en lecture seule Intune à certains rôles Azure Active Directory <!-- 3637917  -->
L’accès en lecture seule Intune a été octroyé aux rôles Azure AD suivants. Les autorisations accordées avec les rôles Azure AD remplacent les autorisations accordées avec le contrôle d’accès en fonction du rôle (RBAC) Intune.

Accès en lecture seule aux données d’audit Intune :

- Administrateur de conformité
- Administrateur des données de conformité

Accès en lecture seule à toutes les données Intune :

- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur Sécurité

Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Balises d’étendue pour les profils de provisionnement d’applications iOS <!--2934430   -->
Vous pouvez ajouter une balise d’étendue à un profil de provisionnement d’application iOS afin que seules les personnes avec des rôles auxquels cette balise d’étendue a également été attribuée aient accès au profil de provisionnement d’application iOS. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Balises d’étendue pour les stratégies de configuration des applications <!--2371891   -->
Vous pouvez ajouter une balise d’étendue à une stratégie de configuration des applications afin que seules les personnes avec des rôles auxquels cette balise d’étendue a également été attribuée aient accès à la stratégie de configuration des applications. La stratégie de configuration des applications peut uniquement cibler des applications auxquelles la même balise d’étendue a été attribuée ou être associée à ces applications. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Prise en charge de Microsoft Edge pour des scénarios Intune sur des appareils iOS et Android <!-- 3411007 -->
Microsoft Edge prendra en charge les mêmes scénarios de gestion qu’Intune Managed Browser avec, en plus, des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise de Microsoft Edge qui sont activées par des stratégies Intune incluent la double identité, l’intégration de stratégies de protection des applications, l’intégration de proxy d’application Azure, ainsi que les raccourcis de page d’accueil et les favoris gérés. Pour plus d’informations, consultez [Prise en charge de Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Semaine du 25 février 2019

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="intune-powershell-module----951068----"></a>Module PowerShell Intune <!-- 951068  -->
Le nouveau module PowerShell Intune, qui offre une prise en charge de l’API Intune par le biais de Microsoft Graph, est désormais disponible dans [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Informations sur la façon d’utiliser ce module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemples de scénarios utilisant ce module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Prise en charge améliorée de l’optimisation de la distribution  <!--3183757  -->
Nous avons étendu la prise en charge de la configuration de l’optimisation de la distribution dans Intune. Vous pouvez désormais configurer une liste développée de [paramètres d’optimisation de la distribution](delivery-optimization-settings.md) et la cibler sur vos appareils directement à partir de la console Intune.


## <a name="week-of-february-18-2019"></a>Semaine du 18 février 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune exploitera les API Google Play Protect sur les appareils Android <!-- 2577355   -->
Certains administrateurs informatiques sont confrontés à un « paysage » BYOD où les téléphones mobiles des utilisateurs finaux peuvent être rootés ou jailbreakés. Ce comportement, bien que n’étant parfois pas mal intentionné, entraîne un contournement de nombreuses stratégies Intune définies pour protéger les données de l’organisation sur les appareils des utilisateurs finaux. Par conséquent, Intune permet donc la détection du rootage et du jailbreaking pour les appareils inscrits et désinscrits. Avec cette version, Intune peut désormais tirer parti des API Google Play Protect, qui s’ajoutent à nos contrôles de détection du rootage pour les appareils non inscrits. Même si Google ne partage pas l’intégralité des contrôles de détection du rootage qui sont effectués, nous pensons que ces API vont détecter les utilisateurs qui ont rooté leurs appareils pour une raison quelconque, allant de la personnalisation de l’appareil à l’obtention de mises à jour plus récentes du système d’exploitation sur des appareils plus anciens. L’accès de ces utilisateurs aux données de l’entreprise peut alors être bloqué, ou leurs comptes professionnels peuvent être supprimés des applications pour lesquelles une stratégie est activée. L’administrateur informatique dispose désormais de plusieurs mises à jour d’amélioration des rapports dans le panneau Intune App Protection : le rapport « Utilisateurs avec indicateur » montre les utilisateurs qui sont détectés via l’analyse de l’API SafetyNet de Google Play Protect, et le rapport « Applications potentiellement dangereuses » montre les applications qui sont détectées via l’analyse de l’API Verify Apps de Google. Cette fonctionnalité est disponible sur Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informations sur les applications Win32 disponibles dans le panneau Résolution des problèmes <!-- 2617342   -->
Vous pouvez désormais collecter des fichiers journaux des échecs pour l’installation d’une application Win32 à partir du panneau **Résolution des problèmes** des applications Intune. Pour plus d’informations sur la résolution des problèmes liés à l’installation d’une application, consultez [Résoudre les problèmes d’installation d’applications](troubleshoot-app-install.md) et [Résoudre les problèmes d’application Win32](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Détails de l’état des applications pour les applications iOS <!-- 3761235   -->
Des nouveaux messages d’erreur d’installation d’une application ont été ajoutés et concernent les échecs suivants :
- Échec pour les applications VPP lors de l’installation sur un iPad partagé
- Échec quand l’App Store est désactivé
- Échec de la recherche d’une licence VPP pour l’application
- Échec de l’installation d’applications système avec le fournisseur MDM
- Échec de l’installation d’applications quand l’appareil est en mode perdu ou en mode kiosque
- Échec de l’installation d’applications quand l’utilisateur n’est pas connecté à l’App Store

Dans Intune, sélectionnez **Applications clientes** > **Applications** > « Nom de l’application » > **État de l’installation de l’appareil**. Les nouveaux messages d’erreur sont disponibles dans la colonne **Détails du statut**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nouvel écran Catégories d’application dans l’application Portail d’entreprise pour Windows 10<!-- 3834780  -->
Un nouvel écran appelé **Catégories d’application** a été ajouté pour améliorer l’expérience de navigation et de sélection des applications dans le portail d’entreprise pour Windows 10. Les applications des utilisateurs s’affichent désormais triées dans des catégories telles que **Proposée(s)** , **Éducation** et **Productivité**. Ce changement apparaît dans la version 10.3.3451.0 et les versions ultérieures du portail d’entreprise. Pour afficher le nouvel écran, consultez [Nouveautés de l’interface utilisateur des applications](https://docs.microsoft.com/intune/whats-new-app-ui). Pour plus d’informations sur les applications dans le portail d’entreprise, consultez [Installer et partager des applications sur votre appareil](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Application Conformité de Power BI <!-- 1455231 doc-work-item -->
Accédez à votre entrepôt de données Intune dans Power BI à l’aide de l’application [Conformité Intune (Entrepôt de données)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Avec cette application Power BI, vous pouvez désormais accéder à des rapports précréés et les partager sans aucune configuration supplémentaire et sans quitter votre navigateur web. Pour plus d’informations, consultez [Journal des changements - Application Conformité de Power BI](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Les scripts PowerShell peuvent s’exécuter dans un hôte 64 bits sur des appareils 64 bits <!-- 1862675   -->
Quand vous ajoutez un script PowerShell à un profil de configuration d’appareil, le script s’exécute toujours en 32 bits, même sur les systèmes d’exploitation 64 bits. Avec cette mise à jour, un administrateur peut exécuter le script dans un hôte PowerShell 64 bits sur des appareils 64 bits (**Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter** > **Configurer** > **Exécuter le script dans un hôte PowerShell 64 bits**).

Pour plus d’informations sur l’utilisation de PowerShell, consultez [Scripts PowerShell dans Intune](intune-management-extension.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>Les utilisateurs macOS sont invités à mettre à jour leur mot de passe <!-- 1873216 -->
Intune applique le paramètre **ChangeAtNextAuth** sur les appareils macOS. Ce paramètre a un impact sur les utilisateurs finaux et sur les appareils qui ont des stratégies de conformité des mots de passe ou des profils de mot de passe de restriction sur les appareils. Les utilisateurs finaux sont invités à mettre à jour une fois leur mot de passe. Cette invite se produit chaque fois qu’un utilisateur exécute pour la première fois une tâche nécessitant une authentification, comme la connexion à l’appareil. Les utilisateurs peuvent également être invités à mettre à jour leur mot de passe lors de l’exécution de toute opération nécessitant des privilèges d’administration, comme la demande d’accès au trousseau. 

Tout changement apporté à une stratégie de mot de passe nouvelle ou existante par l’administrateur invite les utilisateurs finaux à mettre à nouveau à jour leur mot de passe.

S’applique à :  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>Attribuer des certificats SCEP à un appareil macOS sans utilisateur  <!-- 2340521  -->
Vous pouvez attribuer des certificats SCEP (Simple Certificate Enrollment Protocol, protocole d’inscription de certificats simple) à l’aide d’attributs d’appareil à des appareils macOS, notamment à des appareils sans affinité utilisateur, et associer le profil de certificat à des profils Wi-Fi ou VPN. La prise en charge existante est ainsi étendue, permettant d’[attribuer des certificats SCEP à des appareils avec et sans affinité utilisateur](certificates-scep-configure.md#create-a-scep-certificate-profile) qui exécutent Windows, iOS et Android.  Cette mise à jour ajoute la possibilité de sélectionner le type de certificat *Appareil* quand vous configurez un profil de certificat SCEP pour macOS.

S’applique à : 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Mise à jour de l’interface utilisateur de l’accès conditionnel Intune   <!-- 2432313   -->
Nous avons apporté des améliorations à l’interface utilisateur pour l’accès conditionnel dans la console Intune. Par exemple :
-  Remplacement du panneau *Accès conditionnel* d’Intune par le panneau d’Azure Active Directory. Cela garantit que vous avez accès à la gamme complète des paramètres et des configurations pour l’[accès conditionnel](conditional-access.md) (qui reste une technologie Azure AD) à partir de la console Intune. 
- Nous avons renommé le panneau *Accès local* en *Accès à Exchange*, et déplacé le programme d’installation *Connecteur de service Exchange* dans ce panneau renommé.  Ce changement consolide l’endroit où vous [configurez et supervisez les détails relatifs à Exchange Online et local](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Les applications de navigateur kiosque et de navigateur Microsoft Edge peuvent s’exécuter sur des appareils Windows 10 en mode kiosque <!-- 2935135   -->
Vous pouvez utiliser des appareils Windows 10 en mode kiosque pour exécuter une ou plusieurs applications. Cette mise à jour inclut plusieurs modifications de l’utilisation des applications de navigateur en mode kiosque, notamment :

- Ajoutez le navigateur Microsoft Edge ou le navigateur kiosque pour qu’ils s’exécutent comme applications sur l’appareil kiosque (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil).
- De nouvelles fonctionnalités et de nouveaux paramètres sont disponibles pour définir des autorisations ou des restrictions (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **Windows 10 et ultérieur** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil), notamment :

  - Navigateur Microsoft Edge :
  - Utiliser le mode kiosque Microsoft Edge
  - Actualiser le navigateur après la durée d’inactivité

 - Favoris et recherche :
  - Autoriser les changements sur le moteur de recherche

Pour obtenir la liste de ces paramètres, consultez :

- [Paramètres d’appareil Windows 10 et ultérieur pour une exécution en tant que kiosque ](kiosk-settings-windows.md)
- [Restrictions d’appareil pour le navigateur Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Restrictions d’appareils concernant les favoris et la recherche](device-restrictions-windows-10.md##favorites-and-search)

S’applique à : Windows 10 et versions ultérieures

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nouveaux paramètres de restriction d’appareil pour les appareils iOS et macOS <!-- 3448774   -->
Vous pouvez restreindre certains paramètres et certaines fonctionnalités sur les appareils exécutant iOS et macOS (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **iOS** ou **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour ajoute des fonctionnalités et des paramètres que vous pouvez contrôler, notamment définir l’heure de l’écran, modifier les paramètres eSIM et les forfaits mobiles, entre autres, sur les appareils iOS. Citons également le retardement de la visibilité par l’utilisateur des mises à jour logicielles, ainsi que le blocage de la mise en cache du contenu sur les appareils iOS. 

Pour connaître les fonctionnalités et les paramètres que vous pouvez restreindre, consultez :

- [Paramètres de restriction d’appareil iOS](device-restrictions-ios.md)
- [Paramètres de restriction d’appareil macOS](device-restrictions-macos.md)

S’applique à :

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Les appareils « kiosque » sont désormais appelés « appareils dédiés » sur les appareils Android Entreprise <!-- 3598402   -->
Pour s’aligner sur la terminologie d’Android, **kiosque** est remplacé par **appareils dédiés** pour les appareils Android Entreprise (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise pour la plateforme > **Propriétaire de l’appareil uniquement** > **Restrictions sur l’appareil** > **Appareils dédiés**).

Pour afficher les paramètres disponibles, accédez à [Paramètres des appareils pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md#dedicated-device-settings).

S’applique à :  
Android Entreprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Les paramètres Safari et Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS sont déplacés dans l’interface utilisateur Intune <!-- 3640850, 3803313   -->
Pour les appareils iOS, vous pouvez définir des paramètres Safari et configurer les mises à jour logicielles. Dans cette mise à jour, ces paramètres sont déplacés dans différentes parties de l’interface utilisateur Intune :

- Les paramètres Safari sont passés de **Safari** (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil) à **[Applications intégrées](device-restrictions-ios.md#built-in-apps)** .
- Le paramètre **Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS supervisés** (**Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS**) est déplacé dans  **Restrictions sur l’appareil** >  **[Général](device-restrictions-ios.md#general)** .  Pour plus d’informations sur l’impact sur les stratégies existantes, consultez [Mises à jour logicielles iOS](software-updates-ios.md#configure-the-policy). 

Pour obtenir la liste des paramètres, consultez :

- [Restrictions sur les appareils iOS](device-restrictions-ios.md) 
- [Mises à jour logicielles iOS](software-updates-ios.md)

Cette fonctionnalité s’applique à : 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>L’option Activation des restrictions dans les paramètres de l’appareil est renommée en Heure de l’écran sur les appareils iOS <!-- 3699164   -->
Vous pouvez configurer **Activation des restrictions dans les paramètres de l’appareil** sur les appareils iOS supervisés (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour le type de profil > **Général**). Dans cette mise à jour, ce paramètre est renommé en **Heure de l’écran (mode supervisé uniquement)** . 

Le comportement reste le même. Plus précisément : 

- iOS 11.4.1 et antérieur : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. 
- iOS 12.0 et ultérieur : **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil, notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 ne voient plus l’onglet Restrictions dans les paramètres de l’appareil. Ces paramètres se trouvent dans **Heure de l’écran**. 

Pour obtenir la liste des paramètres, consultez [Restrictions sur les appareils iOS](device-restrictions-ios.md#general).

S’applique à : 
- iOS


### <a name="device-management"></a>Gestion des appareils

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Renommer un appareil Windows inscrit <!-- 1911112  -->
Vous pouvez maintenant renommer un appareil Windows 10 inscrit (RS4 ou version ultérieure). Pour cela, choisissez **Intune** > **Appareils** > **Tous les appareils** > Choisissez un appareil > **Renommer l’appareil**. Cette fonctionnalité ne prend actuellement pas en charge le renommage des appareils Azure AD Windows hybrides.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Attribuer automatiquement des balises d’étendue à des ressources créées par un administrateur avec cette étendue <!-- 3173823  -->
Quand un administrateur crée une ressource, les étiquettes d’étendue affectées à l’administrateur sont automatiquement affectées à cette nouvelle ressource.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Le rapport des échecs d’inscription est déplacé dans le panneau Inscription des appareils <!-- 3560202  -->
Le rapport **Échecs d’inscription** a été déplacé dans la section **Superviser** du panneau **Inscription de l’appareil**. Deux nouvelles colonnes (Méthode d’inscription et Version du système d’exploitation) ont été ajoutées.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Rapport d’abandon du portail d’entreprise renommé en Inscriptions d’utilisateur incomplètes <!--3815076 eemiss -->
Le **rapport d’abandon du portail d’entreprise** a été renommé en **Inscriptions d’utilisateur incomplètes**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Semaine du 4 février 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Mode sombre du portail d’entreprise macOS Intune <!-- 3300524  -->
Le portail d’entreprise Intune macOS prend désormais en charge le Mode sombre pour macOS. Quand vous activez le Mode sombre sur un appareil macOS 10.14+, le portail d’entreprise ajuste son apparence à des couleurs reflétant ce mode.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Semaine du 21 janvier 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifications toast pour les applications Win32 <!-- 3136566   -->
Vous pouvez supprimer l’affichage des notifications toast à l’utilisateur final par affectation d’applications. Dans Intune, sélectionnez **Applications clientes** > **Applications** > sélectionnez l’application > **Affectations** > **Inclure les groupes**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Mise à jour de l’interface utilisateur des stratégies de protection des applications Intune <!-- 3251427  -->
Nous avons modifié les étiquettes des paramètres et des boutons d’Intune App Protection pour qu’ils soient tous plus faciles à comprendre. Quelques exemples de modifications :  
- Les commandes **Oui** / **Non** sont remplacées principalement par les commandes **Bloquer** / **Autoriser** et **Désactiver** / **Activer**. Les étiquettes sont également mises à jour.  
- Les paramètres ont également été remis en forme pour qu’ils apparaissent à côté de l’étiquette correspondante dans le contrôle, ce qui facilite la navigation.   

Les paramètres par défaut et le nombre de paramètres restent identiques. Toutefois, ce changement permet à l’utilisateur de comprendre, de parcourir et d’utiliser les paramètres plus facilement pour appliquer les stratégies App Protection sélectionnées. Pour plus d’informations, consultez [Paramètres iOS](app-protection-policy-settings-ios.md) et [Paramètres Android](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Paramètres supplémentaires pour Outlook <!-- 3301182  -->
Vous pouvez désormais configurer les paramètres supplémentaires suivants pour Outlook pour iOS et Android à l’aide d’Intune :

- Autoriser uniquement les comptes professionnels ou scolaires à être utilisés dans Outlook sur iOS et Android
- Déployer une authentification moderne pour Office 365 et une authentification moderne hybride pour les comptes locaux
- Utiliser `SAMAccountName` pour le champ de nom d’utilisateur dans le profil d’e-mail quand l’authentification de base est sélectionnée
- Autoriser l’enregistrement des contacts
- Configurer la fonctionnalité Infos-courrier pour les destinataires externes
- Configurer la **Boîte de réception Prioritaire**
- Imposer la biométrie pour accéder à Outlook pour iOS
- Bloquer les images externes

> [!NOTE]
> Si vous utilisez des stratégies Intune App Protection pour gérer l’accès aux identités d’entreprise, n’activez pas la **biométrie obligatoire**. Pour plus d’informations, consultez **Exiger des informations d’identification d’entreprise pour l’accès** dans les [paramètres d’accès iOS](app-protection-policy-settings-ios.md#access-requirements) et les [paramètres d’accès Android](app-protection-policy-settings-android.md#access-requirements).

Pour plus d’informations, consultez [Paramètres de configuration Microsoft Outlook](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Supprimer les applications Android Entreprise <!-- 1352553 -->
Vous pouvez supprimer des applications Google Play géré à partir de Microsoft Intune. Pour supprimer une application Google Play géré, ouvrez Microsoft Intune dans le portail Azure et sélectionnez **Applications clientes** > **Applications**. À partir de la liste des applications, sélectionnez les points de suspension (...) à droite de l’application Google Play géré, puis sélectionnez **Supprimer** dans la liste affichée. Lorsque vous supprimez une application Google Play gérée à partir de la liste des applications, l’application Google Play gérée devient automatiquement non approuvée.

#### <a name="managed-google-play-app-type----1352580---"></a>Type d’application Google Play géré <!-- 1352580 -->
Le type d’application **Google Play géré** vous permet d’ajouter spécifiquement [les applications Google Play gérées](https://play.google.com/work/search?q=microsoft&c=apps) à Intune. En tant qu’administrateur Intune, vous pouvez désormais parcourir, rechercher, approuver, synchroniser et attribuer des applications Google Play géré approuvées dans Intune.  Vous n’avez plus besoin d’accéder séparément à la console Google Play géré, ni de vous authentifier de nouveau.  Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application**, sélectionnez le type d’application **Google Play géré**.

### <a name="default-android-pin-keyboard----3802457---"></a>Clavier de code PIN Android par défaut <!-- 3802457 -->
Les utilisateurs finaux qui ont défini un code PIN de stratégie Intune App Protection sur leurs appareils Android avec un type de code PIN « Numérique » verront désormais le clavier Android par défaut, au lieu de l’interface utilisateur du clavier Android fixe qui était affichée précédemment. Cette modification a été apportée pour des raisons de cohérence lors de l’utilisation des claviers par défaut sur Android et iOS, pour les deux types de code PIN « Numérique » et/ou « Code secret ». Pour plus d’informations sur les paramètres d’accès de l’utilisateur final sur Android, comme le code PIN de la stratégie de protection des applications, consultez [Exigences d’accès Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Utiliser les paramètres recommandés par Microsoft avec les bases de référence de sécurité (préversion publique) <!-- 2055484   -->

Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur peut créer des stratégies de sécurité directement à partir de ces bases de référence, puis les déployer pour ses utilisateurs. Vous pouvez également personnaliser les recommandations en fonction des besoins de votre organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

Cette fonctionnalité étant en préversion publique, les profils créés maintenant ne sont pas déplacés vers les modèles Base de référence de la sécurité qui sont en disponibilité générale. Nous vous déconseillons d’utiliser ces modèles en préversion dans votre environnement de production.

Pour en savoir plus sur les bases de référence de la sécurité, consultez [Créer une base de référence de la sécurité Windows 10 dans Intune](security-baselines-monitor.md).

Cette fonctionnalité s’applique à : Windows 10 et versions ultérieures

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Les utilisateurs non-administrateurs peuvent activer BitLocker sur des appareils Windows 10 joints à Azure AD<!-- 2147379   -->
Lorsque vous activez les paramètres BitLocker sur des appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **Endpoint Protection** comme type de profil > **Chiffrement Windows**), vous ajoutez des paramètres BitLocker. 

Cette mise à jour comprend un nouveau paramètre BitLocker permettant aux utilisateurs standard (non administrateurs) d’activer le chiffrement. 

Pour voir les paramètres, accédez à [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Vérifier la conformité de Configuration Manager <!-- 2192052  eepublished  -->
Cette mise à jour inclut un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**  >  **Windows 10 et ultérieur** > **Conformité de Configuration Manager**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide de ce paramètre, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

[Conformité de Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personnaliser le papier peint sur les appareils iOS supervisés à l’aide d’un profil de configuration d’appareil <!-- 2809324   -->
Lorsque vous créez un profil de configuration d’appareil pour des appareils iOS, vous pouvez personnaliser certaines fonctionnalités (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de **papier peint** qui permettent à un administrateur d’utiliser une image .png, .jpg ou .jpeg sur l’écran d’accueil ou l’écran de verrouillage. Ces paramètres de papier peint s’appliquent uniquement aux appareils supervisés. 

Pour obtenir la liste de ces paramètres, consultez [Paramètres des fonctionnalités d’appareil iOS](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>La fonctionnalité Kiosque Windows 10 est en disponibilité générale <!-- 3594661  -->
Dans cette mise à jour, la fonctionnalité Kiosque est en disponibilité générale sur les appareils Windows 10 et ultérieur. Pour voir tous les paramètres que vous pouvez ajouter et configurer, consultez [Paramètres kiosque pour Windows 10 (et ultérieur)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Le paramètre Partage de contacts via Bluetooth est supprimé dans Restrictions sur l’appareil > Propriétaire de l’appareil pour Android Entreprise <!-- 3598396   -->
Lorsque vous créez un profil de restrictions d’appareil pour les appareils Android Enterprise, vous disposez d’un paramètre **Partage de contacts via Bluetooth**. Dans cette mise à jour, le paramètre **Partage de contacts via Bluetooth** est supprimé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Restrictions d’appareil > Propriétaire de l’appareil** pour le type de profil > **Général**). 

Le paramètre **Partage de contacts via Bluetooth** n’est pas pris en charge pour la gestion du Propriétaire de l’appareil Android Enterprise. Par conséquent, la suppression de ce paramètre n’affectera aucun périphérique ni aucun client, même si ce paramètre est activé et configuré dans votre environnement.

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md).

S’applique à : Propriétaire d’appareil Android Entreprise

### <a name="device-management"></a>Gestion des appareils

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Prise en charge de la réinitialisation sélective pour les appareils WIP sans inscription <!-- 1434452 -->
WIP-WE (Windows Information Protection Without Enrollment) permet aux clients de protéger leurs données d’entreprise sur des appareils Windows 10 sans nécessiter une inscription complète à MDM. Une fois les documents protégés par une stratégie WIP-WE, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie WIP-WE. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nouveaux journaux des opérations et possibilité d’envoyer des journaux aux services Azure Monitor <!-- 3762211  -->
Intune propose une journalisation d’audit intégrée qui assure le suivi des événements lorsque des modifications sont apportées. Cette mise à jour inclut de nouvelles fonctionnalités de journalisation, notamment les suivantes : 
- Journaux des opérations (préversion) qui présentent des détails sur les utilisateurs et les appareils inscrits, notamment les tentatives qui ont abouti et celles qui ont échoué.
- Les journaux d’audit et les journaux des opérations peuvent être envoyés à Azure Monitor, notamment aux comptes de stockage, aux hubs d’événements et à Log Analytics. Ces services vous permettent de stocker et d’utiliser des analyses comme Splunk et QRadar, ainsi que d’obtenir des visualisations de vos données de journalisation.

[Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](review-logs-using-azure-monitor.md) fournit plus d’informations sur cette fonctionnalité.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorer des autres écrans de l’Assistant Configuration sur un appareil DEP iOS <!-- 2687509  -->
En plus des écrans que vous pouvez déjà ignorer, vous pouvez définir des appareils DEP iOS pour ignorer les écrans suivants de l’Assistant Installation quand un utilisateur inscrit l’appareil : Afficher la sonnerie, Confidentialité, Migration Android, Bouton d’accueil, iMessage et FaceTime, Intégration, Surveiller la migration, Apparence, Heure de l’écran, Mise à jour logicielle, Configuration SIM.
Pour choisir quels écrans ignorer, accédez à **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton > **Profils** > choisissez un profil > **Propriétés** > **Personnalisation de l’Assistant Configuration** > choisissez **Masquer** pour tous les écrans que vous souhaitez ignorer > **OK**.
Si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple. Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises <!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie de protection des applications sans inscription) non inscrit, vous pouvez désormais utiliser Google Play dans sa version managée pour déployer des applications du Store et des applications métier pour les utilisateurs. Plus précisément, vous pouvez proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle ils n’ont plus besoin d’assouplir la posture de sécurité de leurs appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Semaine du 14 janvier 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Préversion de la prise en charge des appareils Android complètement gérés appartenant à l’entreprise <!-- 1574342  -->
Intune prend désormais en charge les appareils Android entièrement gérés, un scénario de type « entreprise propriétaire de l’appareil » dans lequel les appareils sont étroitement gérés par le service informatique et affiliés à différents utilisateurs. Les administrateurs pourront ainsi gérer l’ensemble de l’appareil, appliquer un large éventail de contrôles de stratégie non disponibles avec les profils professionnels et imposer aux utilisateurs d’installer les applications sur la version gérée de Google Play. Pour plus d’informations, consultez [Configurer l’inscription d’appareils Android entièrement gérés dans Intune](android-fully-managed-enroll.md) et [Inscrire vos appareils dédiés ou entièrement gérés](android-dedicated-devices-fully-managed-enroll.md).  Veuillez noter que cette fonctionnalité est en préversion. Certaines fonctionnalités Intune, telles que les certificats, la conformité et l’Accès conditionnel, ne sont pas actuellement disponibles avec les appareils Android des utilisateurs complètement managés.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Semaine du 7 janvier 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-app-pin----2298397---"></a>Code PIN d’application Intune <!-- 2298397 -->
En tant qu’administrateur informatique, vous pouvez maintenant configurer le nombre de jours d’attente possibles pour un utilisateur final avant qu’il ne doive changer le code PIN d’application Intune. Le nouveau paramètre, *Réinitialisation du code PIN au bout d’un nombre de jours*, est accessible dans le portail Azure en sélectionnant **Intune** > **Applications clientes** > **Stratégies de protection des applications** > **Créer une stratégie** > **Paramètres** > **Conditions d’accès**. Disponible pour les appareils [iOS](app-protection-policy-settings-ios.md) et [Android](app-protection-policy-settings-android.md), cette fonctionnalité prend en charge une valeur entière positive.


#### <a name="intune-device-reporting-fields----2748738---"></a>Champs de création de rapport sur les appareils Intune <!-- 2748738 -->
Intune fournit des champs de création de rapport supplémentaires sur les appareils, notamment l’ID d’inscription d’application, le fabricant Android, le modèle et la version du correctif de sécurité ainsi que le modèle iOS. Dans Intune, ces champs sont disponibles quand vous sélectionnez **Applications clientes** > **État de protection de l’application**, et que vous choisissez **Rapport de protection d’application : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration <!-- 3322847 -->

Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion publique. Avec cette mise à jour :

- Les modèles d’administration comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
- Les modèles d’administration sont disponibles en préversion publique.
- Les modèles d’administration sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et ultérieur**, dans **Type de profil**, choisissez **Modèles d’administration**.
- La création de rapports est activée

Pour plus d’informations sur cette fonctionnalité, accédez à [Modèles Windows 10 pour configurer les paramètres de stratégie de groupe](administrative-templates-windows.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Utiliser S/MIME pour chiffrer et signer plusieurs appareils pour un utilisateur  <!-- 1333642 -->
Cette mise à jour inclut le chiffrement S/MIME des e-mails à l’aide d’un nouveau profil de certificat importé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > type de profil **Certificat PKCS importé**). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :
- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.
Pour plus d’informations sur cette fonctionnalité, consultez [Vue d’ensemble de S/MIME pour signer et chiffrer des e-mails](certificates-s-mime-encryption-sign.md).
Pris en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nouvelles options de connexion automatique et de conservation automatique des règles quand vous utilisez des paramètres DNS sur les appareils Windows 10 et les versions ultérieures <!-- 1333665, 2999078 -->
Sur les appareils Windows 10 et ultérieur, vous pouvez créer un profil de configuration VPN qui comporte la liste des serveurs DNS permettant de résoudre les domaines, par exemple contoso.com. Cette mise à jour contient de nouveaux paramètres de résolution de noms (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez  **Windows 10 et ultérieur** comme plateforme > choisissez **VPN** comme type de profil > **Paramètres DNS** >**Ajouter**) : 
- **Connexion automatique** : lorsque ce paramètre est **Activé**, l’appareil se connecte automatiquement au VPN lorsqu’il contacte le domaine saisi, par exemple, contoso.com.
- **Persistant** : par défaut, toutes les règles de la table de stratégie de résolution de noms (NRPT) sont actives tant que l’appareil est connecté avec ce profil VPN. Lorsque ce paramètre est **Activé** sur une règle NRPT, celle-ci reste active sur l’appareil, même si la connexion VPN est interrompue. La règle tient jusqu'à ce que le profil VPN soit supprimé ou jusqu'à ce que la règle soit supprimée manuellement, ce qui peut être effectuée avec PowerShell.
La page [Paramètres VPN Windows 10](vpn-settings-windows-10.md) décrit les paramètres. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utiliser la détection des réseaux approuvés pour les profils VPN sur les appareils Windows 10 <!-- 1500165 -->
Avec la détection des réseaux approuvés, vous pouvez empêcher les profils VPN de créer automatiquement une connexion VPN si l’utilisateur se trouve déjà sur un réseau approuvé. Cette mise à jour vous permet d’ajouter des suffixes DNS pour activer la détection des réseaux approuvés sur les appareils exécutant Windows 10 et versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **VPN** comme type de profil).
La page [Paramètres VPN Windows 10](vpn-settings-windows-10.md) liste les paramètres VPN actuels.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gérer les appareils Windows Holographic for Business utilisés par plusieurs utilisateurs <!-- 1907917, 1063203 -->
Actuellement, vous pouvez configurer les paramètres de PC partagé sur les appareils Windows 10 et Windows Holographic for Business avec un paramètre OMA-URI personnalisé. Avec cette mise à jour, un nouveau profil est ajouté pour configurer les paramètres d’appareil partagé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Appareil multi-utilisateur partagé**).
Pour en savoir plus sur cette fonctionnalité, accédez à [Paramètres Intune pour gérer les appareils partagés](shared-user-device-settings.md).
S’applique à : Windows 10 (et versions ultérieures), Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nouveaux paramètres de mise à jour de Windows 10 <!--2626030  2512994  -->
Pour vos [boucles de mise à jour Windows 10](windows-update-for-business-configure.md), vous pouvez configurer :
- **Comportement des mises à jour automatiques**  :utilisez une nouvelle option, *Rétablir les valeurs par défaut*, pour restaurer les paramètres de mise à jour automatique d’origine sur un ordinateur Windows 10 exécutant la *mise à jour d’octobre 2018*
- **Empêcher l’utilisateur de suspendre l’installation des mises à jour Windows** : configurez un nouveau paramètre sous Mises à jour logicielles qui vous permet de refuser ou permettre aux utilisateurs de suspendre l’installation des mises à jour dans les *Paramètres* de leurs ordinateurs. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>Les profils de messagerie iOS peuvent utiliser la signature et le chiffrement S/MIME <!-- 2662949 -->
Vous pouvez créer un profil de messagerie comportant différents paramètres. Cette mise à jour contient des paramètres S/MIME servant à signer et à chiffrer les communications par e-mail sur les appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > **E-mail** comme type de profil).
La page [Paramètres de configuration de la messagerie iOS](email-settings-ios.md) liste les paramètres.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Certains paramètres BitLocker prennent en charge l’édition Windows 10 Professionnel<!-- 2727036 -->
Vous pouvez créer un profil de configuration définissant des paramètres Endpoint Protection sur les appareils Windows 10, notamment BitLocker. Cette mise à jour ajoute la prise en charge de l’édition Windows 10 Professionnel pour certains paramètres BitLocker. Pour afficher ces paramètres de protection, accédez à [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Le paramètre Configuration des appareils partagés est renommé Message d’écran de verrouillage pour les appareils iOS dans le portail Azure<!-- 2809362 -->
Lors de la création d’un profil de configuration pour des appareils iOS, vous avez la possibilité d’ajouter des paramètres **Configuration des appareils partagés** pour afficher un texte spécifique sur l’écran de verrouillage. Cette mise à jour inclut les modifications suivantes : 
- Les paramètres **Configuration des appareils partagés** sur le Portail Azure sont renommés « Message de l’écran de verrouillage (mode supervisé uniquement) » (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > choisissez **Fonctionnalités de l’appareil** comme type de profil > **Message de l’écran de verrouillage**).
- Lorsque vous ajoutez des messages d’écran de verrouillage, vous pouvez insérer un numéro de série, un nom d’appareil ou toute autre valeur propre à l’appareil comme variable dans **Informations de l’étiquette** et **Note de l’écran de verrouillage**. Par exemple, vous pouvez entrer `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` entre accolades. [Jetons iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) liste les jetons utilisables.
La page [Paramètres d’affichage des messages sur l’écran de verrouillage](shared-device-settings-ios.md) liste les paramètres.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nouveaux paramètres de restriction d’appareil App Store, affichage de document, jeux ajoutés aux appareils iOS <!-- 2827760-->
Dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions d’appareil** comme type de profil > **App Store, affichage de document, jeux**, les paramètres suivants sont ajoutés : Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés et Autoriser les applications non gérées à lire à partir de comptes de contacts gérés. Pour voir ces paramètres, consultez [Restrictions d’appareil iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nouveaux paramètres de notification, d’indicateurs et de keyguard pour les appareils des propriétaires d’appareils Android Entreprise <!-- 3201839 3201843 -->
Cette mise à jour comporte de nouvelles fonctionnalités pour les propriétaires d’appareils Android pour les entreprises. Pour pouvoir les utiliser, accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Android pour les entreprises** > dans **Type de profil**, choisissez **Propriétaire de l’appareil uniquement** > **Restrictions de l’appareil**.

Les nouvelles fonctionnalités comprennent : 

- Désactiver l’affichage des notifications système, notamment les appels entrant, les alertes système, les erreurs système, etc.
- Suggérer d’ignorer les tutoriels de démarrage et les conseils sur les applications qui sont ouvertes pour la première fois.
- Désactiver les paramètres avancés de verrouillage du clavier, notamment l’appareil photo, les notifications, le déverrouillage par empreinte digitale, etc.


Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Les appareils des propriétaires d’appareils Android Entreprise peuvent utiliser des connexions VPN Always On <!-- 3202194 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN Always On sur les appareils Android pour les entreprises des propriétaires d’appareils. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer le VPN Always On dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android pour les entreprises** comme plateforme > **Restrictions de l’appareil** sur Propriétaire de l’appareil uniquement > paramètres **Connectivité**. Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10 <!-- 3285177 --> 
Cette mise à jour comporte un nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10. À l’aide d’un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme** , choisissez **Windows 10** > dans **Type de profil**, choisissez les paramètres **Restrictions de l’appareil** > **Général**), vous choisissez d’autoriser ou non ce paramètre.
Pour afficher ces paramètres, accédez à [Paramètres de restriction d’appareil Windows 10](device-restrictions-windows-10.md).
S’applique à : Windows 10 et versions ultérieures


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Messages d’échec de la restriction d’inscription plus détaillés <!-- 3111564 -->
Des messages d’erreur plus détaillés sont disponibles en cas de non-respect des restrictions d’inscription. Pour voir ces messages, accédez à **Intune** > **Résoudre les problèmes** > et consultez la table des échecs d’inscription. Pour plus d’informations, consultez la [liste des échecs d’inscription](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="tenant-status-dashboard-----1124854---"></a>Tableau de bord État du locataire  <!-- 1124854 -->
La nouvelle [page État du locataire](tenant-status.md) fournit un emplacement unique où vous pouvez voir l’état et les détails associés de votre locataire.  Le tableau de bord est divisé en quatre zones :
- **Détails du locataire** : affiche des informations telles que le nom et l’emplacement de votre locataire, votre autorité MDM, le nombre total d’appareils inscrits dans votre locataire et le nombre de licences. Cette section liste également la version de service actuelle de votre locataire.
- **État du connecteur** : affiche des informations sur les connecteurs disponibles que vous avez configurés et peut également répertorier ceux que vous n’avez pas encore activés.  
   En fonction de leur état actuel, les connecteurs sont marqués comme Sain, Avertissement ou Non sain. Sélectionnez un connecteur pour extraire et afficher des détails ou configurer des informations supplémentaires associées.
-  **Intégrité du service Intune** : affiche des détails sur les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.
-  **Actualités Intune** : affiche les messages actifs pour votre locataire. Les messages incluent les éléments tels que des notifications quand votre locataire reçoit les dernières fonctionnalités Intune.  Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nouvelle expérience d’aide et de support dans le portail d’entreprise pour Windows 10 <!-- 1488939-->
La nouvelle page Aide et support du portail d’entreprise permet aux utilisateurs de résoudre les problèmes et demander de l’aide pour les problèmes liés à l’accès et aux applications. À partir de la nouvelle page, ils peuvent envoyer par e-mail des détails du journal de diagnostic et des erreurs ainsi que rechercher les informations relatives au support technique de leur organisation. Ils y trouveront également une section FAQ avec des liens vers la documentation Intune appropriée. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nouvelle expérience d’aide et de support pour Intune   <!-- #3307080 -->
Nous allons déployer la nouvelle expérience Aide et support sur tous les locataires au cours des prochains jours. Cette nouvelle expérience est disponible pour Intune et est accessible quand vous utilisez les panneaux Intune dans le [portail Azure](https://portal.azure.com/).
Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs. En plus de recevoir une aide spécifique à chaque problème, vous utilisez le nouveau workflow de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone. Cette nouvelle expérience remplace l’expérience Aide et support précédente incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support. Pour plus d’informations, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-apps----1081941---"></a>Balises d’étendue pour les applications <!-- 1081941 -->
Vous pouvez créer des étiquettes de délimitation afin de limiter l’accès pour les rôles et applications. Vous pouvez ajouter une étiquette de délimitation à une application afin que seules les personnes avec des rôles ayant également reçu cette étiquette de délimitation aient accès à l’application. Il n’est actuellement pas possible d’attribuer des balises d’étendue aux applications ajoutées à Intune par Google Play géré ou achetées avec le programme d’achat en volume (VPP) Apple (une prise en charge future est planifiée). Pour plus d’informations, consultez [Utiliser des étiquettes de délimitation pour filtrer les stratégies](scope-tags.md).

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>Semaine du 10 décembre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="updates-for-application-transport-security----748318---"></a>Mises à jour pour Application Transport Security <!-- 748318 -->

Microsoft Intune prend en charge le protocole TLS (Transport Layer Security) 1.2+ pour fournir un chiffrement de qualité, garantir une meilleure sécurisation par défaut et s’aligner avec d’autres services Microsoft comme Microsoft Office 365. Pour répondre à cette exigence, les portails d’entreprise iOS et macOS vont appliquer les impératifs de la fonctionnalité ATS (Application Transport Security) mise à jour d’Apple, celle-ci nécessitant également TLS 1.2+. ATS est utilisé pour renforcer la sécurité de toutes les communications d’application via le protocole HTTPS. Ce changement impacte les clients Intune qui utilisent les applications du portail d’entreprise iOS et macOS. Pour plus d’informations, voir le [blog du support Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Le SDK d’application Intune prendra en charge les clés de chiffrement 256 bits <!-- 1832174 -->
Le kit de développement logiciel (SDK) Intune App pour Android utilise maintenant des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Le kit SDK continuera de prendre en charge les clés 128 bits pour assurer la compatibilité avec le contenu et les applications qui utilisent des versions antérieures du kit SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>La mise à jour automatique de Microsoft version 4.5.0 doit être appliquée aux appareils macOS <!-- 3503442 -->
Pour continuer à recevoir des mises à jour pour le portail d’entreprise et les applications Office, les appareils macOS gérés par Intune doivent être mis à niveau à l’aide de la mise à jour automatique Microsoft 4.5.0. Il est possible que les utilisateurs disposent déjà de cette version pour leurs applications Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune nécessite macOS 10.12 ou une version ultérieure <!-- 2827778 -->
Intune nécessite désormais macOS 10.12 ou une version ultérieure. Les appareils sur lesquels est installée une version macOS antérieure à celle-ci ne peuvent pas utiliser le portail d’entreprise pour s’inscrire auprès d’Intune. Pour recevoir une assistance technique et pour profiter des nouvelles fonctionnalités, les utilisateurs doivent mettre à niveau leur appareil vers macOS 10.12 ou une version ultérieure, mais également mettre à niveau le portail d’entreprise vers la version la plus récente.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Semaine du 26 novembre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Désinstallation d’applications sur des appareils iOS supervisés appartenant à l’entreprise <!-- 1281677 -->

Vous pouvez supprimer les applications de votre choix sur les appareils iOS supervisés appartenant à l’entreprise. Vous pouvez supprimer une application en ciblant des groupes d’utilisateurs ou des groupes d’appareils ayant le type d’affectation **Désinstaller**. Pour les appareils iOS personnels ou non supervisés, vous êtes toujours limité à la suppression des applications installées à l’aide d’Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Télécharger du contenu d’applications Win32 Intune <!-- 2617320 -->
Les clients Windows 10 RS3 (et versions ultérieures) téléchargent du contenu d’applications Win32 Intune à l’aide d’un composant d’optimisation de la distribution sur le client Windows 10. L’optimisation de la distribution offre la fonctionnalité pair à pair, activée par défaut. Actuellement, l’optimisation de la distribution peut être configurée par la stratégie de groupe. Pour plus d’informations, voir [Optimisation de la distribution pour Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu contenu de l’application et appareil de l’utilisateur final <!-- 2771453 -->
Les utilisateurs finaux peuvent désormais utiliser le menu contextuel sur l’appareil et dans les applications pour déclencher des actions courantes telles que la modification du nom d’un appareil ou la vérification de la conformité.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Définir un arrière-plan personnalisé dans l’application Managed Home Screen  <!-- 3041945 -->
Nous ajoutons un paramètre permettant de personnaliser l’apparence de l’arrière-plan de l’application Managed Home Screen sur les appareils Android pour les entreprises en mode plein écran multiapplication.  Pour configurer l’**l’arrière-plan de l’URL personnalisée**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Enregistrement et application d’attributions de stratégies de protection des applications <!-- 3104570 -->
Vous avez maintenant un meilleur contrôle de vos [affectations de stratégies App Protection](app-protection-policies.md#deploy-a-policy-to-users). Lorsque vous sélectionnez *Affectations* afin de définir ou de modifier les affectations d’une stratégie, vous devez **Enregistrer** votre configuration pour que la modification s’applique. Utilisez **Ignorer** pour effacer toutes les modifications apportées sans les enregistrer dans les listes Inclure et Exclure.  Comme il est obligatoire de choisir entre Enregistrer et Ignorer, seuls les utilisateurs souhaités se voient affecter une stratégie App Protection.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nouveaux paramètres du navigateur Microsoft Edge pour Windows 10 et versions ultérieures <!-- 3174639 -->
Cette mise à jour comporte de nouveaux paramètres permettant de contrôler et de gérer le navigateur Microsoft Edge sur les appareils. Pour connaître la liste de ces paramètres, voir [Restriction des appareils pour Windows 10 (et versions ultérieures)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Prise en charge de nouvelles applications avec des stratégies de protection des applications <!-- 3330037 -->
Vous pouvez maintenant gérer les applications suivantes avec les [stratégies Intune App Protection](app-protection-policies.md) :
- Stream (iOS)
- To-Do (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Utilisez des stratégies App Protection pour protéger les données d’entreprise et en contrôler le transfert pour ces applications, comme les autres applications gérées par la stratégie Intune. Remarque : Si Flow n’apparaît pas encore dans la console, ajoutez-le lorsque vous créez ou modifiez des stratégies de protection des données. Pour cela, utilisez l’option **+ Plus d’applications** et spécifiez *l’ID d’application* Flow dans le champ d’entrée : *com.microsoft.flow* pour Android et *com.microsoft.procsimo* pour iOS.


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Les numéros de version et de build iOS et macOS sont affichés <!-- 1892471 -->
Dans **Conformité de l’appareil** > **Conformité de l’appareil**, les versions des systèmes d’exploitation iOS et macOS indiquées peuvent être utilisées dans les stratégies de conformité. Cette mise à jour comporte le numéro de build, configurable pour les deux plateformes.
Quand des mises à jour de sécurité sont publiées, Apple laisse généralement le numéro de version tel quel, mais met à jour le numéro de build. En utilisant le numéro de build dans une stratégie de conformité, vous pouvez facilement vérifier si une mise à jour des vulnérabilités est installée.
Pour utiliser cette fonctionnalité, voir les stratégies de conformité [iOS](compliance-policy-create-ios.md#device-health) et [macOS](compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Les anneaux de mise à jour sont remplacés par les paramètres d’optimisation de la distribution pour Windows 10 et les versions ultérieures <!-- 2753807 -->
L’optimisation de la distribution est un nouveau profil de configuration pour Windows 10 (et versions ultérieures). Cette fonctionnalité simplifie l’expérience de distribution des mises à jour de logiciels aux appareils de l’organisation. Cette mise à jour permet également de fournir les paramètres dans les boucles de mise à jour nouvelles et actuelles à l’aide d’un profil de configuration.
Pour configurer un profil de configuration d’optimisation de la distribution, voir [Paramètres d’optimisation de la distribution de Windows 10 (et versions ultérieures)](delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Ajout de nouveaux paramètres de restriction d’appareil aux appareils iOS et macOS <!-- 2827760 -->
Cette mise à jour comprend de nouveaux paramètres pour vos appareils iOS et macOS qui sont publiés avec iOS 12 :

**Paramètres iOS** : 
- Général : Bloquer la suppression d’applications (mode supervisé uniquement)
- Général : Bloquer le mode USB restreint (mode supervisé uniquement)
- Général : Forcer une date et une heure automatiques (mode supervisé uniquement)
- Mot de passe : Bloquer le remplissage automatique du mot de passe (mode supervisé uniquement)
- Mot de passe : Bloquer les demandes de proximité du mot de passe (mode supervisés uniquement)
- Mot de passe : Bloquer le partage de mot de passe (mode supervisé uniquement)

**Paramètres macOS** : 
- Mot de passe : Bloquer le remplissage automatique du mot de passe
- Mot de passe : Bloquer les demandes de proximité du mot de passe
- Mot de passe : Bloquer le partage de mot de passe

Pour en savoir plus sur ces paramètres, consultez les paramètres de restriction d’appareil [iOS](device-restrictions-ios.md) et [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Sélectionner les applications suivies dans la page d’état d’inscription<!-- 2531007 -->
Vous pouvez choisir les applications à suivre sur la page d’état de l’inscription. Tant que ces applications ne sont pas installées, l’utilisateur ne peut pas utiliser l’appareil. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Rechercher un appareil Autopilot par numéro de série <!--2595788 -->
Vous pouvez maintenant rechercher des appareils Autopilot par numéro de série. Pour cela, choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > tapez un numéro de série dans la zone **Rechercher par numéro de série** > appuyez sur Entrée.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Effectuer le suivi de l’installation d’Office ProPlus <!--2620217 -->
Les utilisateurs peuvent suivre la progression de l’installation [d’Office ProPlus](apps-add-office365.md) sur la [Page d’état de l’inscription](windows-enrollment-status.md). Pour plus d’informations, voir [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertes signalant l’expiration du jeton VPP ou un nombre insuffisant de licences du portail d’entreprise <!-- 2237572 -->
Si vous utilisez le Programme d’achat en volume (VPP) pour préprovisionner le Portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le Portail d’entreprise.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Prise en charge du Programme d’inscription des appareils macOS pour les comptes Apple School Manager <!--3006133 -->
Intune prend maintenant en charge l’utilisation du Programme d’inscription des appareils sur les appareils macOS pour les comptes Apple School Manager.  Pour plus d’informations, voir [Inscrire automatiquement des appareils macOS avec Apple School Manager ou le Programme d’inscription des appareils](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nouvelle référence (SKU) d’abonnement d’appareil Intune <!--3312071-->
Pour aider les entreprises à réduire le coût de la gestion des appareils, une nouvelle référence (SKU) d’abonnement basée sur les appareils est désormais disponible. Cette référence (SKU) d’appareil Intune est concédée sous licence par appareil sur une base mensuelle. Les prix varient selon le programme de licence. Vous pouvez l’obtenir directement par le biais du Centre d’administration Microsoft 365 ainsi que par le biais du [Contrat Entreprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), le [Contrat de Fourniture de Produits et de Services Microsoft ](https://www.microsoft.com/licensing/mpsa/default), les [contrats Open Microsoft ](https://partner.microsoft.com/licensing/licensing-agreements) et le [fournisseur de solutions Cloud](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453).

### <a name="device-management"></a>Gestion des appareils

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Suspendre temporairement le mode kiosque sur les appareils Android pour apporter des changements <!-- 3041935 -->
Pendant que vous utilisez un appareil Android en mode kiosque multiapplication, un administrateur informatique peut être amené à effectuer des changements sur l’appareil. Cette mise à jour comporte de nouveaux paramètres de mode plein écran multiapplication permettant à un administrateur informatique de suspendre temporairement le mode plein écran à l’aide d’un code PIN et d’accéder à la totalité de l’appareil.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Activer le bouton d’accueil virtuel sur les appareils kiosque Android Entreprise  <!-- 3042021 -->
Un nouveau paramètre permet aux utilisateurs d’appuyer sur un bouton programmable de leur appareil pour passer de l’application Managed Home Screen à d’autres applications affectées (et inversement) sur leur appareil en mode kiosque multiapplication. Ce paramètre est particulièrement utile dans les scénarios où l’application en mode kiosque d’un utilisateur ne répond pas correctement au bouton Précédent. Vous allez pouvoir configurer ce paramètre pour les appareils Android à usage unique appartenant à l’entreprise. Pour activer ou désactiver le **bouton d’accueil virtuel**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Semaine du 12 novembre 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Prise en charge du contrôle d’accès réseau (NAC) pour Citrix SSO pour iOS <!-- 3259404 -->

Citrix a publié une mise à jour de Citrix Gateway pour permettre le contrôle d’accès réseau (NAC) pour Citrix SSO pour iOS dans Intune. Vous pouvez choisir d’inclure un ID d’appareil au sein d’un profil VPN dans Intune, puis d’envoyer (Push) ce profil à vos appareils iOS. Vous devrez installer la dernière mise à jour de Citrix Gateway pour utiliser cette fonctionnalité.

[Configurer les paramètres VPN sur les appareils iOS](vpn-settings-ios.md#base-vpn-settings) fournit plus d’informations sur l’utilisation du contrôle d’accès réseau, notamment certaines exigences supplémentaires. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Semaine du 5 novembre 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Prise en charge d’iOS 12 OAuth dans les profils de messagerie iOS <!--2155106 -->

Les profils de messagerie iOS d’Intune prennent en charge iOS 12 OAuth (Open Authorization). Pour voir cette fonctionnalité, créez un profil (**Configuration de l’appareil** > **Profils** > **Créer un profil**  >  **iOS** comme plateforme > **E-mail** comme type de profil). Vous pouvez également mettre à jour un profil de messagerie iOS existant. Si vous activez OAuth dans un profil qui est déjà déployé sur des utilisateurs, ces derniers sont invités à se réauthentifier et à retélécharger leurs e-mails.

[Profils de messagerie iOS](email-settings-ios.md) comprend davantage d’informations sur l’utilisation d’OAuth dans un profil de messagerie.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Prise en charge d’Autopilot pour les appareils joints à un domaine Azure Active Directory hybride (préversion) <!-- 1048100-->
Vous pouvez désormais configurer les appareils joints à un domaine Azure Active Directory hybride à l’aide d’Autopilot. Les appareils doivent être joints au réseau de votre organisation afin d’utiliser la fonctionnalité Autopilot hybride. Pour plus d’informations, consultez [Déployer des appareils joints à un domaine Azure AD hybride à l’aide d’Intune et de Windows Autopilot](windows-autopilot-hybrid.md).
Cette fonctionnalité va être lancée parmi la base d’utilisateurs au cours des prochains jours. Vous ne pourrez donc peut-être pas suivre ces étapes tant que la fonctionnalité n’aura pas été lancée pour votre compte.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Semaine du 29 octobre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Demander un code PIN non biométrique après le délai spécifié <!-- 1506985 -->
En demandant un code PIN non biométrique après un délai d’expiration spécifié par l’administrateur, Intune offre une sécurité renforcée pour les applications compatibles avec GAM (gestion des applications mobiles) en limitant l’utilisation de l’identification biométrique pour l’accès aux données d’entreprise. Les paramètres affectent les utilisateurs qui s’appuient sur Touch ID (iOS), Face ID (iOS), Android Biometric ou d’autres méthodes d’authentification biométriques à venir pour accéder à leurs applications compatibles APP/GAM. Ces paramètres permettent aux administrateurs Intune d’avoir un contrôle plus précis sur l’accès utilisateur, en supprimant les cas où un appareil avec plusieurs empreintes digitales ou d’autres méthodes d’accès biométriques peut révéler des données d’entreprise à un utilisateur inapproprié. Dans le portail Azure, ouvrez **Microsoft Intune**. Sélectionnez **Applications clientes** > **Stratégies de protection des applications** > **Ajouter une stratégie** > **Paramètres**. Recherchez la section **Accès** pour des paramètres spécifiques. Pour plus d’informations sur les paramètres d’accès, consultez [Paramètres iOS](app-protection-policy-settings-ios.md#access-requirements) et [Paramètres Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Paramètres de transfert de données Intune APP sur des appareils inscrits dans la MDM iOS <!-- 2244713 -->
Vous pouvez séparer le contrôle des paramètres de transfert de données d’Intune APP sur les appareils inscrits à la solution MDM pour iOS de la spécification de l’identité de l’utilisateur inscrit, également appelé UPN (nom d’utilisateur principal). Les administrateurs qui n’utilisent pas IntuneMAMUPN ne verront aucun changement de comportement. Lorsque cette fonctionnalité est disponible, les administrateurs qui utilisent IntuneMAMUPN pour contrôler le comportement du transfert de données sur les appareils inscrits doivent consulter les nouveaux paramètres et mettre à jour leurs paramètres APP si nécessaire.

#### <a name="windows-10-win32-apps----2617325---"></a>Applications Win32 Windows 10 <!-- 2617325 -->
Vous pouvez configurer vos applications Win32 pour qu’elles soient installées dans un contexte d’utilisateur individuel, au lieu d’être installées pour tous les utilisateurs de l’appareil.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Applications Win32 Windows et scripts PowerShell <!-- 2617330 -->
Les utilisateurs finaux ne sont plus obligés de se connecter à l’appareil pour installer des applications Win32 ou exécuter des scripts PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Résolution des problèmes liés à l’installation des applications clientes <!-- 1363711 -->
Vous pouvez résoudre les problèmes d’installation des applications clientes en consultant la colonne intitulée **Installation de l’application** dans le panneau **Résoudre les problèmes**. Pour voir le panneau **Résoudre les problèmes**, accédez au portail Intune, puis sélectionnez **Résoudre les problèmes** sous **Aide et support**.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Prise en charge du contrôle d’accès réseau sur les clients VPN iOS <!-- 1333693 -->
Avec cette mise à jour, un nouveau paramètre permet d’activer le NAC (contrôle d’accès réseau) quand vous créez un profil de configuration VPN pour Cisco AnyConnect, F5 Access et Citrix SSO pour iOS. Ce paramètre permet d’inclure l’ID NAC de l’appareil dans le profil VPN. Pour le moment, il n’existe aucun client VPN, ni aucune solution partenaire NAC prenant en charge ce nouvel ID NAC. Toutefois, nous vous tiendrons informés via notre [billet de blog de support](ttps://aka.ms/iOS12_and_vpn) le moment venu.

Pour utiliser NAC, vous devez :
1. Autoriser Intune à inclure des ID d’appareil dans les profils VPN
2. Mettre à jour le logiciel/microprogramme de votre fournisseur NAC, avec l’aide directe de ce dernier

Pour plus d’informations sur ce paramètre dans un profil VPN iOS, consultez [Ajouter des paramètres VPN sur des appareils iOS dans Microsoft Intune](vpn-settings-ios.md). Pour plus d’informations sur le contrôle d’accès réseau, consultez [Intégration du NAC (contrôle d’accès réseau) avec Intune](network-access-control-integrate.md). 

S’applique à : iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Supprimer un profil de messagerie d’un appareil, même s’il n’y a qu’un seul profil <!-- 1818139 -->
Avant, vous ne pouviez pas supprimer un profil de messagerie d’un appareil *si* celui-ci était le seul profil de messagerie. Avec cette mise à jour, ce comportement change. Maintenant, vous pouvez supprimer un profil de messagerie, même si ce profil de messagerie est le seul sur l’appareil. Pour plus d’informations, consultez [Ajouter des paramètres de messagerie à des appareils à l’aide d’Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts PowerShell et AAD <!-- 2309469 -->
Les scripts PowerShell dans Intune peuvent être ciblés sur les groupes de sécurité des appareils AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nouveau paramètre par défaut « Type de mot de passe obligatoire » pour Android et Android Entreprise<!-- 2649963 -->
Quand vous créez une stratégie de conformité (**Intune** > **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android** ou **Android Entreprise** pour Plateforme > Sécurité du système), la valeur par défaut de **Type de mot de passe obligatoire** change :

De : Paramètre par défaut de l’appareil : Au moins numérique

S’applique à : Android, Android Entreprise

Pour voir ces paramètres, accédez à [Android](compliance-policy-create-android.md) et [Android Entreprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utiliser une clé prépartagée dans un profil Wi-Fi Windows 10 <!-- 2662938 -->
Via cette mise à jour, vous pouvez utiliser une clé prépartagée (PSK) avec le protocole de sécurité WPA/WPA2-Personnel afin d’authentifier un profil de configuration Wi-Fi pour Windows 10. Vous pouvez également spécifier la configuration des coûts d’une connexion réseau limitée pour les appareils dans la mise à jour d’octobre 2018 de Windows 10.

Actuellement, vous devez importer un profil Wi-Fi ou créer un profil personnalisé pour utiliser une clé prépartagée. Les paramètres actuels sont répertoriés dans [Paramètres Wi-Fi pour Windows 10](wi-fi-settings-windows.md). 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Supprimer les certificats PKCS et SCEP de vos appareils <!-- 3218390 -->
Dans certains scénarios, les certificats PKCS et SCEP restaient sur les appareils, même après le retrait d’une stratégie d’un groupe, la suppression d’un déploiement de configuration ou de conformité, ou la mise à jour administrative d’un profil SCEP ou PKCS existant. Cette mise à jour change le comportement. Il existe des scénarios où les certificats PKCS et SCEP sont supprimés des appareils et d’autres scénarios où ces certificats restent sur l’appareil. Pour en savoir plus sur ces scénarios, consultez [Supprimer des certificats SCEP et PKCS dans Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Utiliser Gatekeeper sur les appareils macOS à des fins de conformité <!-- 2504381 -->
Cette mise à jour inclut macOS Gatekeeper pour évaluer la conformité des appareils. Pour définir la propriété Gatekeeper, vous devez [ajouter une stratégie de conformité des appareils pour les appareils macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="enrollment-abandonment-report----1382924---"></a>Rapport d’abandon de l’inscription <!-- 1382924 -->
Un nouveau rapport contenant des informations détaillées sur les inscriptions abandonnées est disponible sous **Inscription de l’appareil** > **Surveiller**. Pour plus d’informations, consultez le [rapport d’abandon du portail d’entreprise](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nouvelle fonctionnalité Conditions d’utilisation d’Azure Active Directory <!-- 2870393 -->
Azure Active Directory comporte une fonctionnalité relative aux conditions d’utilisation que vous pouvez utiliser à la place des conditions générales Intune existantes. La fonctionnalité Conditions d’utilisation d’Azure AD offre davantage de flexibilité quant aux choix des conditions d’utilisation à afficher et au moment où elles sont affichées, une meilleure prise en charge de la localisation, un meilleur contrôle de l’affichage des conditions générales, ainsi que des fonctionnalités améliorées de création de rapports. La fonctionnalité Conditions d’utilisation d’Azure AD nécessite Azure Active Directory Premium P1, qui fait également partie de la suite Enterprise Mobility + Security E3. Pour en savoir plus, consultez l’article [Gérer les conditions générales de votre entreprise pour l’accès utilisateur](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Prise en charge du mode Propriétaire de l’appareil Android <!--3188762-->
Pour l’inscription Samsung Knox Mobile, Intune prend désormais en charge l’inscription d’appareils en mode de gestion Device Owner pour Android. Les utilisateurs sur des réseaux Wi-Fi ou mobiles peuvent s’inscrire en quelques clics quand ils allument leurs appareils pour la première fois. Pour plus d’informations, consultez [Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung](android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Gestion des appareils
#### <a name="new-settings-for-software-updates------1907869---"></a>Nouveaux paramètres pour les mises à jour logicielles   <!-- 1907869 -->  
- Vous pouvez désormais configurer des notifications pour informer les utilisateurs finaux des redémarrages qui doivent être effectués dans le but de finaliser l’installation des dernières mises à jour logicielles.   
- Vous pouvez désormais configurer un message d’avertissement pour les redémarrages qui seront effectués en dehors des heures de travail, ce qui convient aux scénarios BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Regrouper les appareils inscrits auprès de Windows Autopilot par ID de corrélation <!-- 2075110 -->
Intune prend désormais en charge le regroupement d’appareils Windows par ID de corrélation en cas d’inscription à l’aide d’[Autopilot pour les appareils existants](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. L’ID de corrélation est un paramètre du fichier de configuration Autopilot. Intune définit automatiquement l’[attribut d’appareil Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) pour qu’il ait la valeur « OfflineAutopilotprofile-<correlator ID> ». Cela permet de créer des groupes dynamiques Azure AD arbitraires en fonction de l’ID de corrélation par le biais de l’attribut enrollmentprofilename pour les inscriptions Autopilot hors connexion. Pour plus d’informations, consultez [Windows Autopilot pour les appareils existants](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Stratégies de protection des applications Intune <!-- 2984657 -->
Les stratégies de protection des applications Intune vous permettent de configurer divers paramètres de protection des données pour des applications protégées Intune, par exemple Microsoft Outlook et Microsoft Word. Nous avons changé l’aspect de ces paramètres pour [iOS](app-protection-policy-settings-ios.md) et [Android](app-protection-policy-settings-android.md) afin de faciliter la recherche de paramètres individuels. Il existe trois catégories pour les paramètres de stratégie :
- **Réadressage des données** - Ce groupe comprend les contrôles DLP (protection contre la perte de données), par exemple les restrictions d’opérations consistant à couper, copier, coller et enregistrer sous. Ces paramètres déterminent la manière dont les utilisateurs interagissent avec les données dans les applications.
- **Conditions d’accès** - Ce groupe contient les options de code PIN par application, qui déterminent le mode d’accès de l’utilisateur final aux applications dans un contexte professionnel.  
- **Lancement conditionnel** - Ce groupe contient des paramètres tels que les paramètres minimum du système d’exploitation, la détection d’appareils jailbreakés/rootés, ainsi que les périodes de grâce hors connexion.  
  
La fonctionnalité des paramètres ne change pas, mais il est plus facile de les trouver quand vous utilisez le flux de création de stratégies.

### <a name="intune-apps"></a>Applications Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune prend en charge une taille de package maximale de 8 Go pour les applications métier <!-- 1727158 -->
Intune a augmenté la taille maximale de package à 8 Go pour les applications métier. Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Ajouter une image de marque personnalisée pour l’application du portail d’entreprise <!-- 1916266 -->
En tant qu’administrateur Microsoft Intune, vous pouvez charger une image de marque personnalisée, qui est affichée en tant qu’image d’arrière-plan dans la page de profil de l’utilisateur au sein de l’application Portail d’entreprise iOS. Pour plus d’informations sur la configuration de l’application Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune conserve la langue localisée d’Office lors de la mise à jour d’Office sur les ordinateurs des utilisateurs finaux <!-- 2971030 -->
Quand Intune installe Office sur les machines de vos utilisateurs finaux, ceux-ci obtiennent automatiquement les mêmes modules linguistiques que ceux qu’ils avaient avec les installations .MSI Office précédentes. Pour plus d’informations, consultez [Assigner des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nouvelle expérience de support Intune dans le portail de gestion des appareils Microsoft 365 <!-- 3076965 -->
Nous lançons une nouvelle expérience utilisateur d’aide et de support pour Intune dans le [portail de Gestion des appareils Microsoft 365]( http://devicemanagement.microsoft.com). Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs.  

En plus de recevoir une aide spécifique à chaque problème, vous pouvez également utiliser le nouveau flux de travail de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone.  

Pour les clients concernés par le lancement, cette nouvelle expérience utilisateur remplace l’expérience actuelle d’aide et de support incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support.  

*Cette nouvelle expérience utilisateur d’aide et de support est en cours de lancement sur certains locataires. Elle est disponible dans le portail de gestion des appareils. Les participants à cette nouvelle expérience sont choisis au hasard parmi les locataires Intune disponibles. De nouveaux locataires vont être ajoutés au fur et à mesure que nous étendrons le lancement.*  

Pour plus d’informations, consultez [Expérience Aide et support](get-support.md#help-and-support-experience) dans Guide pratique pour obtenir un support technique pour Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Module PowerShell pour Intune - Préversion disponible <!-- 951068 -->
Un nouveau module PowerShell, qui offre une prise en charge de l’API Intune via Microsoft Graph, est désormais disponible en préversion sur [GitHub]( https://aka.ms/intunepowershell). Pour plus d’informations sur l’utilisation de ce module, consultez le fichier README à cet emplacement. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Semaine du 15 octobre 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Invite PIN lorsque vous modifiez des empreintes digitales ou Face ID sur un appareil iOS  <!-- 2637704  -->
Les utilisateurs sont maintenant invités à entrer un code PIN après avoir apporté des modifications biométriques sur leur appareil iOS. Cela inclut les changements apportés aux empreintes digitales ou au Face ID. Le délai de la demande dépend de la configuration du délai d’attente *Revérifier les conditions d’accès requises après (minutes)* .  Si aucun code PIN n’est défini, l’utilisateur est invité à en configurer un. 
 
Cette fonctionnalité est uniquement disponible pour iOS et nécessite la participation d’applications qui intègrent le SDK d’application Intune pour iOS 9.0.1 ou version ultérieure. L’intégration du SDK est nécessaire afin que le comportement puisse être ajouté aux applications ciblées. Cette intégration se produit en continu et repose sur les équipes d’application spécifiques. Certaines applications participantes incluent WXP, Outlook, Managed Browser et Yammer.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>Semaine du 1er octobre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Accès aux propriétés de profil clés à l’aide de l’application Portail d’entreprise <!-- 772203 -->
Les utilisateurs finaux peuvent désormais accéder aux propriétés et aux actions de compte de clé, comme la réinitialisation de mot de passe, à partir de l’application Portail d’entreprise. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Les claviers tiers peuvent être bloqués par des paramètres APP sur iOS <!-- 1248481 -->
Sur les appareils iOS, les administrateurs Intune peuvent bloquer l’utilisation de claviers tiers lors de l’accès à des données de l’entreprise dans des applications protégées par une stratégie. Quand la stratégie de protection des applications (APP, Application Protection Policy) est configurée pour bloquer les claviers tiers, l’utilisateur de l’appareil reçoit un message la première fois qu’il interagit avec les données de l’entreprise en utilisant un clavier tiers. Toutes les options autres que celles du clavier natif sont bloquées et les utilisateurs de l’appareil ne les voient pas. La boîte de message ne s’affiche qu’une seule fois aux utilisateurs. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Accès des applications Intune aux comptes d’utilisateurs sur les appareils iOS et Android gérés <!-- 1248496 -->
En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Stratégie de configuration des applications Outlook pour iOS et Android <!--1828527 -->
Vous pouvez maintenant créer une stratégie de configuration d’application Outlook pour iOS et Android pour les utilisateurs locaux qui utilisent de l’authentification de base avec le protocole ActiveSync. Des paramètres de configuration supplémentaires sont ajoutés au fur et à mesure qu’ils seront activés pour l’application Outlook pour iOS et Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Modules linguistiques Office 365 Pro Plus <!-- 1833450 -->
En tant qu’administrateur Intune, vous pouvez déployer des langues supplémentaires pour les applications Office 365 Pro Plus gérées par le biais d’Intune. La liste des langues disponibles inclut le **Type** du module linguistique (principal, partiel et de vérification). Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application** du panneau **Ajouter une application**, sélectionnez **Windows 10** sous la **Suite Office 365**. Sélectionnez **Langues** dans le panneau **Paramètres de la suite d’applications**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensions de fichier des applications métier Windows <!-- 1884873 -->
Les extensions de fichier des applications métier Windows sont désormais *.msi*, *.appx*, *.appxbundle*, *.msix* et *.msixbundle*. Vous pouvez ajouter une application dans Microsoft Intune en sélectionnant **Applications clientes** > **Applications** > **Ajouter**. Le volet **Ajouter une application** s’affiche et vous permet de sélectionner le **Type d’application**. Pour les applications métier Windows, sélectionnez **Métier** comme type d’application, sélectionnez **Fichier de package d’application**, puis entrez un fichier d’installation avec l’extension appropriée.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Déploiement d’applications Windows 10 à l’aide d’Intune <!-- 2309001 -->
S’appuyant sur la prise en charge existante des applications métier et des applications Microsoft Store pour Entreprises, les administrateurs peuvent utiliser Intune pour déployer la plupart des applications existantes de leur organisation sur les utilisateurs finaux d’appareils Windows 10. Les administrateurs peuvent ajouter, installer et désinstaller des applications pour les utilisateurs de Windows 10 dans un large éventail de formats, tels que les fichiers MSI, Setup.exe ou MSP. Intune évaluera les règles de spécification avant le téléchargement et l’installation, et informera les utilisateurs finaux de l’état ou des exigences de redémarrage par le biais du Centre de maintenance de Windows 10. Cette fonctionnalité permettra aux organisations intéressées de faire basculer cette charge de travail vers Intune et le cloud. Cette fonctionnalité est actuellement en préversion publique, et nous prévoyons d’y ajouter de nouvelles capacités significatives dans les prochains mois. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Paramètres de stratégie de protection d’application pour les données web <!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu contenu de l’application et appareil de l’utilisateur final <!-- 2771453 -->
Les utilisateurs finaux peuvent désormais utiliser le menu contextuel sur un appareil et des applications pour déclencher des actions courantes comme le renommage d’un appareil ou de vérification de la conformité. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Raccourcis clavier du Portail d’entreprise Windows <!-- 2771518 -->
Les utilisateurs finaux peuvent désormais déclencher des actions d’application et d’appareil dans le Portail d’entreprise Windows à l’aide de raccourcis clavier (accélérateurs).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Créer des suffixes DNS dans les profils de configuration VPN sur les appareils exécutant Windows 10<!-- 1333668 -->
Lorsque vous créez un profil de configuration d’appareil VPN (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **VPN** pour le type de profil), vous entrez des paramètres DNS. Avec cette mise à jour, vous pouvez également entrer plusieurs **suffixes DNS** dans Intune. Lorsque vous utilisez des suffixes DNS, vous pouvez rechercher une ressource réseau à l’aide de son nom court, au lieu du nom de domaine complet (FQDN). Cette mise à jour vous permet également de modifier l’ordre des suffixes DNS dans Intune.
Les paramètres DNS actuels sont répertoriés dans [Paramètres VPN Windows 10](vpn-settings-windows-10.md#dns-settings).
S’applique à : Appareils Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Prise en charge de VPN Always On pour les profils professionnels d’Android Entreprise <!-- 1333705 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN AlwaysOn sur les appareils d’entreprise Android avec des profils professionnels managés. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer un VPN AlwaysOn on dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Restrictions d’appareil** > **Connectivité**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Émettre des certificats SCEP aux appareils sans utilisateur <!-- 1744554 -->
Actuellement, les certificats sont émis aux utilisateurs. Avec cette mise à jour, vous pouvez émettre des certificats SCEP pour des appareils, notamment des appareils sans utilisateur comme les appareils kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Certificat SCEP** pour le profil). Autres mises à jour :
- La propriété **Objet** dans un profil SCEP est maintenant une zone de texte personnalisée et peut inclure de nouvelles variables. 
- La propriété **Autre nom de l'objet (SAN)** dans un profil SCEP est désormais un format de tableau et peut inclure de nouvelles variables. Dans le tableau, un administrateur peut ajouter un attribut et indiquer la valeur dans une zone de texte personnalisée. Le SAN prendra en charge les attributs suivants : 
  - DNS
  - Adresse de messagerie
  - UPN

  Ces nouvelles variables peuvent être ajoutées avec du texte statique dans une zone de texte de valeur personnalisée. Par exemple, l’attribut DNS peut être ajouté en tant que `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Les accolades, les points-virgules et les barres verticales « { } ; | » ne fonctionnent pas dans le texte statique du SAN. Les accolades ne doivent encadrer qu’une des nouvelles variables de certificat d’appareil acceptées pour `Subject` ou `Subject alternative name`. 

Nouvelles variables de certificat d’appareil :  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` fonctionne uniquement pour Windows et les appareils joints à un domaine. 
>  -  Lorsque vous spécifiez les propriétés de l’appareil, comme l’IMEI, le numéro de série et le nom de domaine complet dans l’objet ou le SAN pour un certificat d’appareil, n’oubliez pas que ces propriétés peuvent être usurpées par une personne ayant accès à l’appareil. 

Les variables actuelles lors de la création d’un profil de configuration SCEP sont répertoriées dans [Créer un profil de certificat SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile). 

S’applique à : Windows 10 (et versions ultérieures) et iOS, compatible avec le Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Verrouiller à distance des appareils non conformes <!-- 2064495 -->
Si un appareil n’est pas conforme, vous pouvez créer une action dans la stratégie de conformité qui verrouille l’appareil à distance. Dans Intune > **Conformité de l’appareil**, créez une stratégie ou sélectionnez une stratégie existante > **Propriétés**. Sélectionnez **Actions en cas de non-conformité** > **Ajouter** et choisissez de verrouiller l’appareil à distance.
Pris en charge sur : 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 et versions ultérieures 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Améliorations du profil Kiosk Windows 10 et des versions ultérieures dans le portail Azure <!-- 2748224 -->
Cette mise à jour comprend les améliorations suivantes du profil de configuration d’appareil Windows 10 Kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Préversion Kiosk** pour le type de profil) : 
- Actuellement, vous pouvez créer plusieurs profils kiosk sur le même appareil. Avec cette mise à jour, Intune ne prendra en charge qu’un seul profil kiosk par appareil. Si vous avez toujours besoin de plusieurs profils kiosk sur un seul appareil, vous pouvez utiliser un URI personnalisé.
- Dans un profil **Kiosque multi-application**, vous pouvez sélectionner la taille de la vignette d’application et l’ordre de **présentation du menu Démarrer** dans la grille de l’application. Si vous préférez avoir plus de personnalisation, vous pouvez continuer à charger un fichier XML.
- Les paramètres Navigateur Kiosk sont déplacés dans les paramètres **Kiosk**. Actuellement, les paramètres **Navigateur web Kiosk** ont leur propre catégorie dans le portail Azure.
S’applique à : Windows 10 et versions ultérieures




### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Appliquer le profil Autopilot à des appareils Windows 10 inscrits qui ne sont pas encore inscrits pour Autopilot <!-- 1558983 -->
Vous pouvez appliquer des profils Autopilot à des appareils Win 10 inscrits qui n’ont pas encore été enregistrés dans Autopilot. Dans le profil Autopilot, choisissez l’option **Convertir tous les appareils ciblés vers Autopilot** pour enregistrer automatiquement les appareils non Autopilot dans le service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures. Lorsque l’appareil est désinscrit et réinitialisé, Autopilot le provisionne.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Créer plusieurs profils Page d’état d’inscription et les attribuer à des groupes Azure AD <!-- 2526564 -->
Vous pouvez maintenant [créer et attribuer](windows-enrollment-status.md) plusieurs profils Page d’état d’inscription aux groupes Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migration du Programme d’inscription des appareils vers Apple Business Manager dans Intune <!--2748613-->
Apple Business Manager (ABM) fonctionne dans Intune. Vous pouvez donc mettre à niveau votre compte du Programme d’inscription des appareils (DEP) vers ABM. Le processus est identique dans Intune. Pour mettre à niveau votre compte Apple de DEP vers ABM, accédez à [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Onglets de l’état des alertes et des inscriptions dans la page de vue d’ensemble Inscription de l’appareil <!--2748656-->
Les alertes et les échecs d’inscription apparaissent maintenant sous des onglets distincts sur la page de présentation de l’inscription des appareils.

### <a name="device-management"></a>Gestion des appareils

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restreindre les applications et bloquer l’accès aux ressources d’entreprise sur les appareils Android <!-- 2451462  -->  
Dans **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android**  >  **Sécurité du système**, il existe un nouveau paramètre dans la section *Sécurité de l’appareil* nommé **Applications restreintes**. Le paramètre **Applications restreintes** utilise une stratégie de conformité pour bloquer l’accès aux ressources d’entreprise si certaines applications sont installées sur l’appareil. L’appareil est considéré comme non conforme jusqu’à ce que les applications restreintes soient supprimées de l’appareil.
S’applique à : 
- Android

<!-- ########################### -->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
