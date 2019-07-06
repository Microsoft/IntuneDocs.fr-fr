---
title: Nouveautés de l’archive du portail classique Microsoft Intune
description: Nouveautés archivées de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29aa32b02f5ab97707ce76eb10a84a8913a9f702
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67572307"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Nouveautés du portail classique Intune - mois précédents

[!INCLUDE [classic-portal](./includes/classic-portal.md)]

Cette page présente les nouvelles fonctionnalités et remarques précédemment annoncées sur la [page Nouveautés](whats-new.md) pour le portail classique Intune.

## <a name="april-2017"></a>Avril 2017

### <a name="new-capabilities"></a>Nouvelles fonctionnalités

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps disponibles pour Managed Browser <!--822308, 822303-->

Microsoft MyApps bénéficie d’une meilleure prise en charge dans Managed Browser. Les utilisateurs de Managed Browser qui ne sont pas ciblés pour la gestion sont dirigés directement vers le service MyApps, où il peuvent accéder à leurs applications SaaS configurées par l’administrateur. Les utilisateurs ciblés pour la gestion Intune continueront à pouvoir accéder à MyApps à partir du signet Managed Browser intégré.

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nouvelles icônes pour Managed Browser et le Portail d’entreprise <!--918433, 918431, 971473-->

Managed Browser reçoit des icônes mises à jour pour les versions iOS et Android de l’application. La nouvelle icône contient le badge Intune mis à jour, pour une meilleure cohérence avec d’autres applications Enterprise Mobility + Security (EM+S). Vous pouvez voir la nouvelle icône de Managed Browser sur la [page Nouveautés de l’interface utilisateur des applications Intune](whats-new-app-ui.md).

Le portail d’entreprise reçoit également des icônes mises à jour pour les versions Android, iOS et Windows de l’application pour améliorer la cohérence avec les autres applications EM+S. Ces icônes seront publiées progressivement sur toutes les plateformes du mois d’avril jusqu’à fin mai.

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicateur de progression de connexion dans le Portail d’entreprise Android <!--953374-->

Une mise à jour de l’application Portail d’entreprise Android affiche un indicateur de progression de connexion quand l’utilisateur lance l’application ou effectue une reprise. L’indicateur affiche successivement les nouveaux états, en commençant par « Connexion... », puis « Connexion en cours », puis « Vérification des exigences de sécurité... », avant d’autoriser l’utilisateur à accéder à l’application. Vous pouvez voir les nouveaux écrans de l’application Portail d’entreprise pour Android sur la [page Nouveautés de l’interface utilisateur des applications Intune](whats-new-app-ui.md).

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Empêcher les applications d’accéder à SharePoint Online <!-- 679339 -->

Vous pouvez maintenant créer une stratégie d’accès conditionnel basé sur l’application pour bloquer l’accès à [SharePoint Online](app-based-conditional-access-intune-create.md) pour les applications sur lesquelles n’a été appliquée aucune stratégie de protection des applications. Dans le scénario d’accès conditionnel basé sur les applications, vous pouvez spécifier les applications qui doivent avoir accès à SharePoint Online à l’aide du portail Azure.

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Prise en charge de l’authentification unique du Portail d’entreprise pour iOS pour Outlook pour iOS <!--834012-->
Les utilisateurs n’ont plus besoin de se connecter à l’application Outlook s’ils sont connectés à l’application Portail d’entreprise pour iOS sur le même appareil avec le même compte. Quand les utilisateurs lancent l’application Outlook, ils peuvent sélectionner leur compte et se connecter automatiquement. Nous travaillons également à l’ajout de cette fonctionnalité à d’autres applications Microsoft.

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Amélioration de la messagerie d’état dans l’application Portail d’entreprise pour iOS <!--744866-->
De nouveaux messages d’erreur plus spécifiques sont désormais affichés dans l’application Portail d’entreprise pour iOS, afin de fournir des informations plus accessibles sur ce qui se passe sur les appareils. Ces cas d’erreur étaient dans un message d’erreur général intitulé « Portail d’entreprise temporairement indisponible ». En outre, si un utilisateur lance le portail d’entreprise sur iOS quand il ne dispose pas d’une connexion Internet, une barre d’état persistante indiquant « Aucune connexion Internet » est affichée dans la page d’accueil.

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Amélioration de l’état d’installation de l’application pour l’application Portail d’entreprise de Windows 10 <!--676495-->

Parmi les améliorations apportées aux installations d’applications démarrées dans l’application Portail d’entreprise Windows 10, citons les suivantes :
- Indication plus rapide de la progression de l’installation des packages MSI
- Indication plus rapide de la progression de l’installation d’applications modernes sur les appareils exécutant au minimum Mise à jour anniversaire Windows 10
- Nouvelle barre de progression pour les installations d’applications modernes sur les appareils exécutant au minimum Mise à jour anniversaire Windows 10

Vous pouvez voir la nouvelle barre de progression dans la [page Nouveautés de l’interface utilisateur des applications Intune](whats-new-app-ui.md).

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscription en bloc des appareils Windows 10 <!-- 747607 -->

Vous pouvez désormais joindre un grand nombre d’appareils qui exécutent la mise à jour Windows 10 Creators pour Azure Active Directory et Intune à l’aide du Concepteur de configuration Windows (WCD). Pour activer [l’inscription MDM en bloc](windows-bulk-enroll.md) pour votre client Azure AD, créez un package de configuration qui joint les appareils à votre client Azure AD à l’aide du Concepteur de configuration Windows, puis appliquez le package aux appareils d’entreprise que vous souhaitez inscrire et gérer en bloc. Une fois le package appliqué à vos appareils, ceux-ci se connectent à Azure AD et s’inscrivent dans Intune. Ils sont alors prêts pour que vos utilisateurs Azure AD s’y connectent.  Les utilisateurs d’Azure AD agissent sur ces appareils en tant qu’utilisateurs standard ; ils reçoivent les stratégies qui leur sont affectées ainsi que les applications dont ils ont besoin. Les scénarios de libre-service et de portail d’entreprise ne sont pas pris en charge pour le moment.

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Nouveautés de la préversion publique d’Intune dans le Portail Azure<!--736542-->

Début 2017, nous migrerons l’intégralité de notre expérience administrateur vers Azure, permettant ainsi une gestion puissante et intégrée des principaux flux de travail EMS sur une plateforme de services moderne et extensible à l’aide des API Graph.

Les nouveaux locataires de test pourront accéder à la préversion publique de la nouvelle expérience administrateur dans le portail Azure ce mois-ci. Dans un état d’aperçu, les fonctionnalités et la parité avec la console Intune existante seront remises en mode itératif.

L’expérience administrateur dans le portail Azure utilisera la nouvelle fonctionnalité de regroupement et de ciblage précédemment annoncée ; lorsque votre client existant est migré vers la nouvelle expérience de regroupement, vous le serez également afin d’afficher un aperçu de la nouvelle expérience administrateur sur votre client. En attendant, si vous souhaitez tester ou examiner toute nouvelle fonctionnalité avant la migration du client, inscrivez-vous à un nouveau compte d’évaluation Intune ou consultez la [nouvelle documentation](whats-new.md).

Vous pouvez découvrir les nouveautés de la préversion Intune dans Azure [ici](whats-new.md).

### <a name="notices"></a>Remarques

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accès direct aux scénarios d’inscription d’Apple <!--951869-->

Pour les comptes Intune créés après janvier 2017, Intune a activé un accès direct aux scénarios d’inscription Apple à l’aide de la charge de travail Inscrire des appareils dans le portail Azure en version préliminaire. Auparavant, la version préliminaire de l’inscription Apple était uniquement accessible à partir de liens dans le portail Azure. Les comptes Intune créés avant janvier 2017 nécessiteront une migration unique pour que ces fonctionnalités deviennent disponibles dans Azure. La planification de la migration n’a pas encore été annoncée, mais les détails correspondants seront diffusés dès que possible. Si votre compte existant ne peut pas accéder à la version préliminaire, nous vous recommandons vivement de créer un compte d’évaluation afin de tester la nouvelle expérience.

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Nouveautés pour Appx dans Intune sur le Portail Azure <!-- 1000270 -->

Dans le cadre de la migration vers Intune dans le portail Azure, nous avons apporté trois modifications à appx :

1. Ajout d’un nouveau type d’application appx dans la console Intune qui ne peut être déployé que vers des appareils inscrits pour la gestion des appareils mobiles.
2. Réaffectation du type d’application appx existant pour cibler uniquement les ordinateurs gérés par l’intermédiaire de l’agent de PC Intune.
3. Conversion de tous les appxs existants en appxs MDM avec la migration.

##### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?

Cela n’affecte aucun de vos déploiements existants vers des appareils qui sont gérés par l’intermédiaire de l’agent de PC Intune. Toutefois, après la migration, vous ne pourrez pas déployer ces appxs migrés vers de nouveaux appareils gérés par l’intermédiaire de l’agent de PC Intune qui n’étaient pas précédemment ciblés.

##### <a name="what-action-do-i-need-to-take"></a>Que dois-je faire ?

Après la migration, vous devez retélécharger l’appx en tant qu’appx PC si vous voulez effectuer de nouveaux déploiements de PC. Pour en savoir plus, consultez [Appx changes in Intune in the Azure portail](https://aka.ms/appxchange) (Changement relatif aux appx dans Intune dans le portail Azure) sur le blog de l’équipe de support technique Intune.  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Rôles d’administration remplacés dans le portail Azure

Les rôles d’administration de la gestion des applications mobiles (GAM), à savoir Contributeur, Propriétaire et Lecture seule, qui sont utilisés dans le portail Intune classique, sont remplacés par un nouvel ensemble complet de contrôles d’administration basés sur des rôles (RBAC) dans le portail Intune Azure. Une fois la migration effectuée vers le portail Azure, vous devez associer vos administrateurs à ces nouveaux rôles d’administration. Pour en savoir plus sur les contrôles RBAC et les nouveaux rôles, voir [Rôles Intune (RBAC) pour Microsoft Intune](role-based-access-control.md).

### <a name="whats-coming"></a>Nouveautés à venir

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Amélioration de l’expérience de connexion sur l’ensemble des applications du Portail d’entreprise pour toutes les plateformes <!--User Story 1132123-->

Dans les mois à venir, nous introduirons des changements visant à améliorer l’expérience de connexion aux applications Portail d’entreprise Intune pour Android, iOS et Windows. La nouvelle expérience utilisateur s’affiche automatiquement sur toutes les plates-formes utilisées pour l’application du portail d’entreprise lorsqu’Azure AD apporte cette modification. En outre, les utilisateurs peuvent désormais se connecter au portail d’entreprise à partir d’un autre appareil grâce à un code à usage unique automatiquement généré. Cette fonction se révèle particulièrement utile lorsque les utilisateurs doivent se connecter sans informations d’identification.

La page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md) contient des captures d’écran illustrant l’expérience de connexion précédente, la nouvelle expérience de connexion avec des informations d’identification, ainsi que la nouvelle expérience de connexion depuis un autre appareil.

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Modification planifiée : Intune transforme l’expérience du portail pour les partenaires Intune <!-- 1050016 -->

Nous supprimons la page des partenaires Intune du site manage.microsoft.com à compter de la mise à jour de service prévue mi-mai 2017.  

Si vous êtes un administrateur de partenaires, vous ne pourrez plus afficher la page des partenaires Intune et agir pour le compte de vos clients, et vous devrez vous connecter à un des deux autres portails des partenaires sur le site de Microsoft.

Le [Centre pour partenaires Microsoft](https://partnercenter.microsoft.com/) et le[ Centre d’administration Microsoft 365](https://admin.microsoft.com/) vous permettent de vous connecter aux comptes client que vous gérez. En tant que partenaire, utilisez à partir de maintenant l’un de ces sites pour gérer vos clients.


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Mises à jour pour Application Transport Security requises par Apple <!--748318-->

La société Apple a annoncé qu’elle appliquera des exigences spécifiques pour ATS (Application Transport Security). ATS est utilisé pour renforcer la sécurité de toutes les communications d’application via le protocole HTTPS. Cette modification a une incidence sur les clients Intune qui utilisent les applications de portail d’entreprise iOS.

Nous avons publié, par le biais du programme Apple TestFlight, une version de l’application Portail d’entreprise pour iOS qui respecte les nouvelles exigences d’ATS. Si vous souhaitez l’essayer pour tester votre conformité à ATS, envoyez un e-mail à <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> en indiquant votre prénom, votre nom, votre adresse e-mail et le nom de votre société. Pour plus d’informations, consultez notre [blog de support Intune](https://aka.ms/compportalats).

## <a name="march-2017"></a>Mars 2017

### <a name="new-capabilities"></a>Nouvelles fonctionnalités

#### <a name="support-for-skycure"></a>Prise en charge de Skycure

Vous pouvez désormais contrôler l’accès des appareils mobiles aux ressources d’entreprise, à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Skycure, une solution de protection contre les menaces mobiles qui s’intègre à Microsoft Intune. Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant Skycure, notamment :

- Défense physique
- Défense du réseau
- Défense des applications
- Défense contre les vulnérabilités

Vous pouvez configurer des stratégies d’accès conditionnel EMS selon l’évaluation des risques de Symantec Endpoint Protection Mobile (Skycure) activée par le biais des stratégies de conformité des appareils Intune. Vous pouvez utiliser ces stratégies pour autoriser ou bloquer l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées. Pour plus d’informations, consultez [Connecteur Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nouvelle expérience utilisateur dans l’application Portail d’entreprise pour Android <!--621622-->

L’application Portail d’entreprise pour Android a mis à jour son interface utilisateur afin d’en moderniser l’aspect et d’améliorer l’expérience utilisateur. Les mises à jour notables sont les suivantes :

- Couleurs : les en-têtes de l’onglet Portail d’entreprise sont colorés selon une personnalisation définie par le service informatique.
- Applications : dans l’onglet **Applications**, les boutons **Applications proposées** et **Toutes les applications** sont mis à jour.
- Recherche : dans l’onglet **Applications**, le bouton **Rechercher** est un bouton d’action flottant.
- Navigation dans les applications : la vue **Toutes les applications** affiche une vue comprenant les onglets **Applications proposées**, **Toutes les applications** et **Catégories** pour faciliter la navigation.
- Support : les onglets **Mes appareils** et **Contacter le service informatique** sont mis à jour pour améliorer la lisibilité.

Pour plus d’informations sur ces modifications, consultez [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](whats-new-app-ui.md).

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Les appareils non gérés peuvent accéder aux applications attribuées <!--664691-->

Dans le cadre des modifications conceptuelles du site web du portail d’entreprise, les utilisateurs iOS et Android peuvent installer les applications attribuées indiquées comme « disponibles sans inscription » sur leurs appareils non gérés. À l’aide de leurs informations d’identification Intune, les utilisateurs peuvent se connecter au site web du portail d’entreprise et afficher la liste des applications qui leur sont attribuées. Les packages des applications « disponibles sans inscription » peuvent être téléchargés sur le site web du portail d’entreprise. Les applications dont l’installation nécessite une inscription ne sont pas affectées par cette modification, car les utilisateurs sont invités à inscrire leur appareil s’ils souhaitent installer ces applications.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script de signature pour le Portail d’entreprise Windows 10 <!--941642-->

Si vous avez besoin de télécharger de l’application Portail d’entreprise Windows 10 et d’en charger une version test, vous pouvez à présent utiliser un script qui simplifie le processus de signature d’application pour votre organisation.   Pour télécharger le script et les instructions d’utilisation, consultez [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script de signature Microsoft Intune pour le portail d’entreprise Windows 10) sur la galerie TechNet. Pour plus d’informations sur cette annonce, consultez [Mise à jour de votre application de portail d’entreprise Windows 10](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) sur le blog de l’équipe de support technique Intune.


### <a name="notices"></a>Remarques

#### <a name="support-for-ios-103"></a>Prise en charge d’iOS 10.3

Le déploiement de la version 10.3 d’iOS a débuté le 27 mars 2017 pour les utilisateurs d’iOS. Tous les scénarios MDM et MAM Intune existants sont compatibles avec la dernière version du système d’exploitation Apple. Toutes les fonctionnalités Intune existantes actuellement disponibles pour la gestion des appareils iOS devraient continuer à fonctionner une fois les appareils des utilisateurs migrés vers iOS 10.3.

Actuellement, nous n’avons aucun problème connu à signaler. Si vous rencontrez des problèmes liés à iOS 10.3, n’hésitez pas à contacter [l’équipe de support Intune](get-support.md).

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Amélioration du support pour les utilisateurs Android basés en Chine <!--720444-->

En l’absence de Google Play Store en Chine, les appareils Android doivent obtenir les applications sur les places de marché chinoises. L’application Portail d’entreprise prend en charge ce flux de travail en redirigeant les utilisateurs Android chinois vers les App Stores locaux à partir desquels ils pourront télécharger des applications Portail d’entreprise et Outlook. Cette approche améliore l’expérience utilisateur lorsque les stratégies d’accès conditionnel sont activées, à la fois pour la gestion des appareils mobiles et pour la gestion des applications mobiles. Les applications Portail d’entreprise et Outlook pour Android sont disponibles dans les App Stores chinois suivants :

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Meilleure pratique : vérifiez que vos applications Portail d’entreprise sont à jour <!--879465-->

En décembre 2016, nous avons publié une mise à jour qui a activé l’authentification multifacteur (MFA) sur un groupe d’utilisateurs lorsque ceux-ci inscrivent un appareil iOS, Android, Windows 8.1+ ou Windows Phone 8.1+. Cette fonctionnalité ne peut pas fonctionner sans certaines versions de ligne de base de l’application Portail d’entreprise pour Android (v5.0.3419.0 +) et iOS (v2.1.17+).

Microsoft améliore en permanence Intune en ajoutant de nouvelles fonctions aussi bien à la console qu’aux applications Portail d’entreprise sur toutes les plateformes prises en charge. Par conséquent, Microsoft publie uniquement des correctifs pour les problèmes que nous trouvons dans la version actuelle de l’application Portail d’entreprise. Il est donc recommandé d’utiliser les dernières versions des applications Portail d’entreprise pour bénéficier d’une expérience utilisateur optimale.

>[!Tip]
> Demandez à vos utilisateurs de définir leurs appareils de façon à ce qu’ils mettent à jour automatiquement les applications à partir de l’App Store approprié. Si vous avez partagé l’application Portail d’entreprise Android sur un partage réseau, vous pouvez télécharger la dernière version à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams est maintenant activé pour MAM sur iOS et Android

Microsoft a annoncé la disponibilité générale de Microsoft Teams. Les applications Microsoft Teams mises à jour pour iOS et Android sont maintenant activées avec les fonctionnalités de gestion des applications mobiles Intune (MAM). Vous donnez ainsi la possibilité à vos équipes de travailler librement sur les appareils, tout en veillant à ce que les conversations et les données d’entreprise soient protégées en permanence. Pour plus d’informations, consultez l’[annonce Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) sur le blog Enterprise Mobility and Security.


## <a name="february-2017"></a>Février 2017

### <a name="new-capabilities"></a>Nouvelles fonctionnalités

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisation du site web Portail d’entreprise <!--753980-->
Le site web du portail d’entreprise prend en charge les applications destinées aux utilisateurs qui n’ont pas d’appareils gérés. Le site web s’aligne sur les autres produits et services Microsoft et utilise un nouveau modèle de couleurs contrastées, des illustrations dynamiques et un « menu hamburger », ![Petite image du menu hamburger désormais ajouté en haut à gauche du site web du portail d’entreprise](./media/CP_hamburger_menu.png).

### <a name="notices"></a>Remarques

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migration de groupe n’implique pas la mise à jour des groupes ou des stratégies pour les appareils iOS <!--898837-->
Pour chaque groupe d’appareils Intune préattribué par un profil d’inscription des appareils de l’entreprise, un groupe d’appareils dynamique correspondant est créé dans AAD à partir du nom du profil d’inscription des appareils de l’entreprise pendant la migration vers des groupes d’appareils Azure Active Directory. De cette façon, les appareils inscrits sont automatiquement regroupés et reçoivent les mêmes stratégies et applications que le groupe Intune d’origine.

Dès qu’un client entre dans l’étape de regroupement et de ciblage du processus de migration, Intune crée automatiquement un groupe AAD dynamique qui correspond à un groupe Intune ciblé par un profil d’inscription des appareils de l’entreprise. Si l’administrateur Intune supprime le groupe Intune cible, le groupe AAD dynamique correspondant n’est pas supprimé. Les membres du groupe et la requête dynamique disparaissent, mais le groupe lui-même est conservé jusqu’à ce que l’administrateur informatique le supprime dans le portail AAD.

De même, si l’administrateur informatique change le groupe Intune qui est ciblé par un profil d’inscription des appareils de l’entreprise, Intune crée un groupe dynamique qui reflète la nouvelle attribution de profil, mais ne supprime pas le groupe dynamique créé pour l’ancienne attribution.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Gestion par défaut des appareils de bureau Windows via les paramètres Windows <!--663050-->
Le comportement par défaut pour l’inscription d'ordinateurs de bureau Windows 10 change. Les nouvelles inscriptions se feront via le flux d'inscription d'agent MDM classique plutôt que via l’agent PC. Le site Web du portail d’entreprise fournira aux utilisateurs d'ordinateurs de bureau Windows 10 des instructions d’inscription qui les guideront tout au long du processus d’ajout d’ordinateurs de bureau Windows 10 comme appareils mobiles. Cela n’affectera pas les ordinateurs actuellement inscrits, et votre organisation pourra toujours gérer des ordinateurs de bureau Windows 10 à l’aide de l’agent PC [si vous préférez](manage-windows-pcs-with-microsoft-intune.md).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Amélioration de la prise en charge de la gestion des applications mobiles pour la réinitialisation sélective <!--581242-->
Les utilisateurs finaux recevront des instructions supplémentaires sur la façon de récupérer l’accès aux données professionnelles ou scolaires si ces données sont supprimées automatiquement à cause de la stratégie « Intervalle en mode hors connexion avant la réinitialisation des données d’application ».<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Le Portail d’entreprise pour obtenir des liens iOS s’ouvre au sein de l’application <!--665954-->
Les liens au sein de l’application Portail d’entreprise pour iOS, y compris ceux vers la documentation et les applications, s’ouvriront directement dans l’application Portail d’entreprise à l’aide d’une vue dans l’application de Safari. Cette mise à jour sera disponible séparément à partir de la mise à jour de service de janvier.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nouvelle adresse du serveur GPM pour les appareils Windows <!--893007-->
Les utilisateurs de Windows et Windows Phone ne parviennent pas à inscrire un appareil s’ils entrent __manage.microsoft.com__ comme adresse du serveur MDM (s’ils y sont invités). L’adresse du serveur MDM __manage.microsoft.com__ devient __enrollment.manage.microsoft.com__. Demandez à vos utilisateurs d’utiliser __enrollment.manage.microsoft.com__ comme adresse du serveur MDM, s’ils y sont invités lors de l’inscription d’un appareil Windows ou Windows Phone. Aucune modification de votre configuration CNAME n’est nécessaire. Pour plus d’informations sur cette modification, visitez [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nouvelle expérience utilisateur dans l’application Portail d’entreprise pour Android <!--621622-->
À compter de mars, l’application Portail d’entreprise pour Android suit les [directives de conception matérielle](https://material.io/guidelines/material-design/introduction.html) pour créer une apparence plus moderne. Cette expérience utilisateur améliorée inclut les éléments suivants :

* __Couleurs__ : La couleur de l’en-tête des onglets peut être assortie à votre palette de couleurs personnalisée.
* __Interface__ : Les boutons Applications proposées et Toutes les applications ont été mis à jour sous l’onglet Applications. Le bouton Rechercher est désormais un bouton d’action flottant.
* __Navigation__ : Le bouton Toutes les applications propose une vue comprenant les onglets Applications proposées, Toutes les applications et Catégories pour faciliter la navigation.
* __Service__ : Les onglets Mes appareils et Contacter le service informatique sont plus lisibles.

Des images « Avant » et « Après » sont disponibles dans la [page des mises à jour de l’interface utilisateur](whats-new-app-ui.md).

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>Associer plusieurs outils de gestion au Microsoft Store pour Entreprises <!--926135-->
Si vous utilisez plusieurs outils de gestion pour déployer des applications Microsoft Store pour Entreprises, vous ne pouviez auparavant en associer qu’un au Microsoft Store pour Entreprises. Désormais, vous pouvez associer plusieurs outils de gestion au Windows Store, par exemple, Intune et Configuration Manager. Pour plus d’informations, consultez [Gérer les applications que vous avez achetées dans le Microsoft Store pour Entreprises avec Microsoft Intune](windows-store-for-business.md).

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Nouveautés de la préversion publique d’Intune dans le Portail Azure <!--736542-->

Début 2017, nous migrerons l’intégralité de notre expérience administrateur vers Azure, permettant ainsi une gestion puissante et intégrée des principaux flux de travail EMS sur une plateforme de services moderne et extensible à l’aide des API Graph.

Les nouveaux locataires de test pourront accéder à la préversion publique de la nouvelle expérience administrateur dans le portail Azure ce mois-ci. Dans un état d’aperçu, les fonctionnalités et la parité avec la console Intune existante seront remises en mode itératif.

L’expérience administrateur dans le portail Azure utilisera la nouvelle fonctionnalité de regroupement et de ciblage précédemment annoncée ; lorsque votre client existant est migré vers la nouvelle expérience de regroupement, vous le serez également afin d’afficher un aperçu de la nouvelle expérience administrateur sur votre client. En attendant, si vous souhaitez tester ou examiner toute nouvelle fonctionnalité avant la migration du client, inscrivez-vous à un nouveau compte d’évaluation Intune ou consultez la [nouvelle documentation](whats-new.md).

Vous pouvez découvrir les nouveautés de la préversion Intune dans Azure [ici](whats-new.md).

## <a name="january-2017"></a>Janvier 2017

### <a name="new-capabilities"></a>Nouvelles fonctionnalités

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Rapports générés dans la console pour la gestion des applications mobiles sans inscription <!--677961-->
De nouveaux rapports de protection des applications ont été ajoutés pour les appareils inscrits et les appareils qui n’ont pas été inscrits. Découvrez plus d’informations sur la façon dont vous pouvez [superviser les stratégies de gestion des applications mobiles avec Intune](app-protection-policies-monitor.md).

#### <a name="android-711-support---694397--"></a>Prise en charge d’Android 7.1.1 <!--694397-->
Intune prend désormais entièrement en charge et gère Android 7.1.1.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Résoudre le problème quand les appareils iOS sont inactifs ou que la console d’administration ne peut pas communiquer avec eux <!--unknown-->
Quand les appareils des utilisateurs perdent le contact avec Intune, vous pouvez leur appliquer de nouvelles étapes de dépannage pour leur permettre de récupérer l’accès aux ressources d’entreprise. Consultez [Les appareils sont inactifs ou la console d’administration ne peut pas communiquer avec eux](troubleshoot-device-enrollment-in-intune.md#devices-are-inactive-or-the-admin-console-cant-communicate-with-them).

### <a name="notices"></a>Remarques

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Gestion par défaut des appareils de bureau Windows via les paramètres Windows <!--663050-->
Le comportement par défaut pour l’inscription d'ordinateurs de bureau Windows 10 change. Les nouvelles inscriptions se feront via le flux d'inscription d'agent MDM classique plutôt que via l’agent PC.

Le site Web du portail d’entreprise fournira aux utilisateurs d'ordinateurs de bureau Windows 10 des instructions d’inscription qui les guideront tout au long du processus d’ajout d’ordinateurs de bureau Windows 10 comme appareils mobiles. Cela n’affectera pas les ordinateurs actuellement inscrits, et votre organisation pourra toujours gérer des ordinateurs de bureau Windows 10 à l’aide de l’agent PC [si vous préférez](manage-windows-pcs-with-microsoft-intune.md).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Amélioration de la prise en charge de la gestion des applications mobiles pour la réinitialisation sélective <!--581242-->
Les utilisateurs finaux recevront des instructions supplémentaires sur la façon de récupérer l’accès aux données professionnelles ou scolaires si ces données sont supprimées automatiquement à cause de la stratégie « Intervalle en mode hors connexion avant la réinitialisation des données d’application ».<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Le Portail d’entreprise pour obtenir des liens iOS s’ouvre au sein de l’application <!--665954-->
Les liens au sein de l’application Portail d’entreprise pour iOS, y compris ceux vers la documentation et les applications, s’ouvriront directement dans l’application Portail d’entreprise à l’aide d’une vue dans l’application de Safari. Cette mise à jour sera disponible séparément à partir de la mise à jour de service de janvier.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisation du site web Portail d’entreprise <!--753980-->
À compter de février, le site web du portail d’entreprise prend en charge les applications destinées aux utilisateurs qui n’ont pas d’appareils gérés. Le site web s’aligne sur les autres produits et services Microsoft et utilise un nouveau modèle de couleurs contrastées, des illustrations dynamiques et un « menu hamburger », ![Menu hamburger du site web du portail d’entreprise](./media/CP_hamburger_menu.png).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nouvelle documentation concernant les stratégies de protection des applications <!--583398-->
Nous avons mis à jour notre documentation pour les administrateurs et les développeurs d'applications qui souhaitent activer les stratégies de protection des applications (appelées stratégies MAM) dans leurs applications iOS et Android à l’aide de l'outil de création de package de restrictions d’application Intune ou du SDK d’application Intune.

Les articles suivants ont été mis à jour :

* [Décider comment préparer les applications pour la gestion des applications mobiles avec Microsoft Intune](apps-prepare-mobile-application-management.md)
* [Préparer des applications iOS pour la gestion des applications mobiles avec l’outil de création de package de restrictions d’application Intune](app-wrapper-prepare-ios.md)
* [Prise en main du Kit de développement logiciel (SDK) d’applications Microsoft Intune](app-sdk-get-started.md)
* [Guide du Kit de développement logiciel (SDK) d’applications Intune pour les développeurs iOS](app-sdk-ios.md)

Les articles suivants constituent de nouveaux ajouts à la bibliothèque de documents :

* [Plug-in Cordova du SDK d’application Intune](app-sdk-cordova.md)
* [Composant Xamarin du SDK d’application Intune](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Barre de progression lors du lancement du Portail d’entreprise sur iOS <!--665978-->
Le portail d’entreprise pour iOS introduit une barre de progression sur l’écran de démarrage pour fournir à l’utilisateur des informations sur les processus de chargement qui se produisent. Il y aura un déploiement échelonné de la barre de progression pour remplacer le compteur. Cela signifie que certains de vos utilisateurs verront la nouvelle barre de progression tandis que d’autres verront encore le compteur.

## <a name="december-2016"></a>Décembre 2016

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Préversion publique d’Intune dans le Portail Azure<!--736542-->
Début 2017, nous migrerons l’intégralité de notre expérience administrateur vers Azure, permettant ainsi une gestion puissante et intégrée des principaux flux de travail EMS sur une plateforme de services moderne et extensible à l’aide des API Graph. Avant la disponibilité générale de ce portail pour tous les clients Intune, nous sommes heureux d’annoncer que nous commencerons le déploiement d’une préversion de cette nouvelle expérience d’administration ce mois-ci pour certains clients.

L’expérience administrateur dans le portail Azure utilisera la nouvelle fonctionnalité de regroupement et de ciblage précédemment annoncée ; lorsque votre client existant est migré vers la nouvelle expérience de regroupement, vous le serez également afin d’afficher un aperçu de la nouvelle expérience administrateur sur votre client. En attendant, découvrez toutes les nouveautés de Microsoft Intune dans le portail Azure dans notre [nouvelle documentation](/intune/what-is-intune).

__Intégration de la gestion des dépenses de télécommunications dans la préversion publique du Portail Azure__ <!--747605-->
Nous avons commencé à afficher un aperçu de l’intégration aux services de gestion des dépenses de télécommunications au sein du portail Azure. Vous pouvez utiliser Intune pour appliquer des limites à l’utilisation des données domestiques et itinérantes. Nous allons commencer ces intégrations avec [Saaswedo](http://www.saaswedo.com/). Pour activer cette fonctionnalité dans votre client d’évaluation, veuillez [contacter le support technique Microsoft](get-support.md).

### <a name="new-capabilities"></a>Nouvelles fonctionnalités

__Authentification multifacteur sur toutes les plateformes__ <!--747590-->
Vous pouvez appliquer l’authentification multifacteur (MFA) sur un groupe sélectionné d’utilisateurs lorsqu’ils inscrivent un appareil iOS, Android, Windows 8.1+ ou Windows Phone 8.1+ depuis le portail de gestion Azure en configurant l’authentification MFA sur l’application de l’inscription à Microsoft Intune dans Azure Active Directory.

__Possibilité de limiter l’inscription des appareils mobiles__ <!--747596-->
Intune ajoute de nouvelles restrictions d’inscription qui contrôlent les plateformes d’appareils mobiles autorisées à être inscrites. Intune sépare les plateformes d’appareils mobiles comme iOS, MacOS, Android, Windows et Windows Mobile.
* La restriction de l’inscription d’appareils mobiles ne limite pas l’inscription des clients de PC.
* Pour iOS uniquement, il existe une option supplémentaire pour bloquer l’inscription des appareils personnels.

Intune marque tous les nouveaux appareils comme personnels, sauf si l’administrateur prend des mesures pour les marquer comme appareils d’entreprise, comme expliqué dans [cet article](device-enrollment.md).

### <a name="notices"></a>Remarques

__Déplacement de l’authentification multifacteur pour les inscriptions vers le Portail Azure__ <!--VSO 750545-->
Auparavant, les administrateurs accédaient à la console Intune ou à la console Configuration Manager (antérieure à la version d’octobre 2016) pour définir l’authentification multifacteur pour les inscriptions Intune. Grâce à cette fonctionnalité mise à jour, vous pouvez désormais vous connecter au [portail Microsoft Azure](https://manage.windowsazure.com) à l’aide de vos informations d’identification Intune et configurer les paramètres de l’authentification multifacteur via Azure AD. En savoir plus sur ce point [ici](https://aka.ms/mfa_ad).

__L’application Portail d’entreprise pour Android est désormais disponible en Chine__ <!--VSO 658093-->
Nous publions l’application Portail d’entreprise pour Android pour le téléchargement en Chine. En l’absence de Google Play Store en Chine, les appareils Android doivent obtenir les applications dans les places de marché des applications chinoises. L’application Portail d’entreprise pour Android sera disponible en téléchargement dans les Stores suivants :
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

L’application Portail d’entreprise pour Android utilise Google Play Services pour communiquer avec le service Microsoft Intune. Étant donné que les services Google Play ne sont pas encore disponibles en Chine, le traitement des tâches suivantes peut prendre jusqu’à 8 heures. 

|Console d’administration Intune| Application Portail d’entreprise Intune pour Android |Site web du portail d’entreprise Intune|   
|---|---|---|
|réinitialisation complète| Supprimer un appareil distant| Supprimer l’appareil (local et distant)|
|Réinitialisation sélective| Réinitialiser l’appareil| Réinitialiser un appareil|
|Déploiements d’applications nouvelles ou mises à jour| Installer des applications métier disponibles| Réinitialisation du code secret d’un appareil|
|Verrouillage à distance|||
|Réinitialiser le code secret|||

### <a name="deprecations"></a>Dépréciations

__Firefox ne prendra plus en charge Silverlight__ <!--VSO TBA-->
Mozilla supprime la prise en charge de Silverlight dans la version 52 du [navigateur Firefox](https://www.mozilla.org/firefox), à compter de mars 2017. Ainsi, vous ne pourrez plus vous connecter à la console Intune existante à l’aide de versions de Firefox ultérieures à la version 51. Nous vous recommandons d’utiliser Internet Explorer 10 ou 11 pour accéder à la console d’administration, ou une [version de Firefox antérieure à la version 52](https://ftp.mozilla.org/pub/firefox/releases/). La transition d’Intune vers le portail Azure lui permettra de prendre en charge plusieurs [navigateurs modernes](/azure/azure-preview-portal-supported-browsers-devices) sans dépendance envers Silverlight.

__Suppression des stratégies de boîte aux lettres mobile Exchange Online__ <!--770687-->
À compter du mois décembre, les administrateurs ne seront plus en mesure d’afficher ou de configurer les stratégies de boîte aux lettres mobile Exchange Online (EAS) dans la console Intune. Cette modification s’appliquera à tous les clients Intune entre décembre et janvier. La configuration des stratégies existantes restera inchangée. Pour configurer de nouvelles stratégies, utilisez l’environnement de ligne de commande Exchange Management Shell. Obtenez plus d’informations [ici](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx).

__Les applications Intune AV Player, Image Viewer et PDF Viewer ne sont plus prises en charge sur Android__ <!--747553-->
À partir de mi-décembre 2016, les utilisateurs ne seront n’est plus en mesure d’utiliser les applications Intune AV Player, Image Viewer et PDF Viewer. Ces applications ont été remplacées par l’application Azure Information Protection. En savoir plus sur l’application Azure Information Protection [ici](/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>Novembre 2016

### <a name="new-capabilities"></a>Nouvelles fonctionnalités

__Nouveau portail d’entreprise Microsoft Intune disponible pour les appareils Windows 10__ Microsoft lance une nouvelle [application Portail d’entreprise Microsoft Intune pour les appareils Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Cette application, au nouveau format Windows 10 universel, fournira à l’utilisateur une expérience inédite de l’application et une expérience identique sur tous les appareils Windows 10, PC et mobiles, tout en offrant les mêmes fonctionnalités qu’aujourd’hui.

La nouvelle application permettra également aux utilisateurs de tirer parti de fonctionnalités de plateforme supplémentaires telles que l’authentification unique (SSO) et par certificat sur les appareils Windows 10. Elle sera disponible en tant que mise à niveau du portail d’entreprise Windows 8.1 actuel et du portail d’entreprise Windows Phone 8.1 installés à partir du Microsoft Store. Pour plus d’informations, consultez [aka.ms/intunecp_universalapp](https://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __Mise à jour sur Intune et Android for Work__ Vous pouvez déployer des applications Android for Work avec l’action __Obligatoire__, mais vous pouvez uniquement déployer les applications __disponibles__ si vos groupes Intune ont été migrés vers la nouvelle expérience Azure AD pour les groupes.

__Le SDK d’application Intune pour le plug-in Cordova prend maintenant en charge la gestion des applications mobiles (GAM) sans inscription__ Les développeurs d’applications peuvent maintenant utiliser le plug-in Cordova du SDK d’application Intune pour activer la fonctionnalité GAM sans inscription d’appareils dans leurs applications Cordova pour Android et iOS. Vous trouverez le plug-in Cordova du SDK d’application Intune [ici](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__Le composant Xamarin du SDK d’application Intune prend maintenant en charge la gestion des applications mobiles (GAM) sans inscription__ Les développeurs d’applications peuvent maintenant utiliser le composant Xamarin du SDK d’application Intune pour activer la fonctionnalité GAM sans inscription d’appareils dans leurs applications Xamarin pour Android et iOS. Vous pouvez trouver le composant Xamarin du SDK d’application Intune [ici](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Remarques

__Le certificat de signature Symantec n’a plus besoin du portail d’entreprise Windows Phone 8 signé pour le chargement__ Le chargement du certificat de signature Symantec n’a plus besoin de l’application Portail d’entreprise Windows Phone 8 signée. Le certificat peut être chargé séparément.

### <a name="deprecations"></a>Dépréciations

__Prise en charge du portail d’entreprise Windows Phone 8__ La prise en charge du portail d’entreprise Windows Phone 8 est désormais dépréciée. La prise en charge des plateformes Windows Phone 8 et WinRT a été dépréciée en octobre 2016. La prise en charge du portail d’entreprise Windows 8 a également été dépréciée en octobre 2016.


### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.
