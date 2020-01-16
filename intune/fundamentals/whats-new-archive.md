---
title: Nouveautés des mois précédents dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Passer en revue les annonces antérieures sur la page Nouveautés d’Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a9454d11fd1209e715cbcb1e9d2ce7aae4a003c
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886054"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Nouveautés de la préversion de Microsoft Intune - mois précédents

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

<!-- ########################## -->
## <a name="april-2019"></a>Avril 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications
#### <a name="user-experience-update-for-the-company-portal-app-for-ios---2536024---"></a>Mise à jour de l’expérience utilisateur de l’application Portail d’entreprise pour iOS<!-- 2536024 -->
La page d’accueil de l’application Portail d’entreprise pour les appareils iOS a été repensée. Désormais, elle adhère davantage aux modèles d’interface utilisateur iOS, et fournit également une meilleure détectabilité des applications et des livres électroniques.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users--3448635---"></a>Changements apportés à l’inscription sur le portail d’entreprise pour les utilisateurs d’appareils iOS 12<!--3448635 -->
Les étapes et les écrans d’inscription iOS sur le portail d’entreprise ont été mis à jour afin de s’aligner avec les changements de l’inscription MDM publiés dans Apple iOS 12.2. Le workflow mis à jour invite les utilisateurs à effectuer les opérations suivantes :  

* Autoriser Safari à ouvrir le site web Portail d’entreprise et à télécharger le profil de gestion avant de retourner à l’application Portail d’entreprise.  
* Ouvrir l’application Paramètres pour installer le profil de gestion sur leur appareil.
* Retourner à l’application Portail d’entreprise pour terminer l’inscription.  

Pour connaître les étapes et les écrans d’inscription mis à jour, consultez [Inscrire un appareil iOS dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).

#### <a name="openssl-encryption-for-android-app-protection-policies---3747362---"></a>Chiffrement OpenSSL pour les stratégies de protection des applications Android<!-- 3747362 -->
Les stratégies de protection des applications Intune sur les appareils Android utilise désormais une bibliothèque de chiffrement OpenSSL qui est conforme à la norme FIPS 140-2. Pour plus d’informations, consultez la section [Chiffrement](../apps/app-protection-policy-settings-android.md#encryption) de [Paramètres de la stratégie de protection des applications Android dans Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies---2617348----"></a>Activer les dépendances d’application Win32<!-- 2617348  -->
En qualité d’administrateur, vous pouvez exiger que les autres applications soient installées en tant que dépendances avant d’installer votre application Win32. Plus précisément, l’appareil doit installer la ou les applications dépendantes avant d’installer l’application Win32. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Sélectionnez **Application Windows (Win32)** comme **Type d’application**. Après avoir ajouté l’application, vous pouvez sélectionner **Dépendances** pour ajouter l’application dépendante qui doit être installée avant que l’application Win32 puisse être installée. Pour plus d’informations, consultez [Intune autonome - Gestion des applications Win32](./../apps/app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps---3537391-----"></a>Informations sur l’installation de versions d’application pour les applications Microsoft Store pour Entreprises<!-- 3537391   -->
Les rapports d’installation des applications incluent des informations sur les versions d’application concernant Microsoft Store pour les applications métier. Dans Intune, sélectionnez **Applications clientes** > **Applications**. Sélectionnez une **Application du Microsoft Store pour Entreprises**, puis **État de l’installation de l’appareil** sous la section **Superviser**.

#### <a name="additions-to-win32-apps-requirement-rules---3676883-----"></a>Ajouts apportés aux règles de spécification des applications Win32<!-- 3676883   -->
Vous pouvez créer des règles de spécification basées sur des scripts PowerShell, des valeurs de Registre et des informations sur le système de fichiers. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Application Windows (Win32)** comme **Type d’application** dans le panneau **Ajouter une application**.  Sélectionnez **Spécifications** > **Ajouter** pour configurer des règles de spécification supplémentaires. Ensuite, sélectionnez **Type de fichier**, **Registre** ou **Script** comme **Type de spécification**. Pour plus d’informations, consultez [Gestion des applications Win32](./../apps/app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices---3695227----"></a>Configurer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune<!-- 3695227  -->
Vous pouvez attribuer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune. Pour plus d’informations sur les applications Win32 dans Intune, consultez [Gestion des applications Win32](./../apps/app-management.md).

#### <a name="device-overview-shows-primary-user--3794259----"></a>La vue d’ensemble de l’appareil indique l’utilisateur principal<!--3794259  -->
La page de vue d’ensemble de l’appareil indique l’utilisateur principal, également appelé utilisateur d’UDA (affinité entre appareil et utilisateur). Pour voir l’utilisateur principal d’un appareil, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil. L’utilisateur principal apparaît en haut de la page **Vue d’ensemble**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices---4105925----"></a>Création de rapports d’applications Google Play gérées supplémentaires pour les appareils avec profil professionnel Android Entreprise<!-- 4105925  -->
Pour les applications Google Play gérées qui sont déployées sur des appareils avec profil professionnel Android Entreprise, vous pouvez afficher le numéro de version spécifique de l’application installée sur un appareil. Cela concerne uniquement les applications obligatoires.  

#### <a name="ios-third-party-keyboards---4111843-----"></a>Claviers tiers iOS<!-- 4111843   -->
La prise en charge de la stratégie de protection des applications Intune pour le paramètre **Claviers tiers** pour iOS n’existe plus en raison d’un changement de plateforme iOS. Vous ne pouvez plus configurer ce paramètre dans la console d’administration Intune, ni l’appliquer sur le client dans le kit SDK de l’application Intune.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="updated-certificate-connectors---icm-113304612---"></a>Mise à jour des connecteurs de certificat<!-- ICM 113304612 -->
Nous avons publié des mises à jour à la fois pour le [connecteur de certificat Intune et le connecteur de certificat PFX](../protect/certficates-pfx-configure.md#whats-new-for-connectors). Les nouvelles versions résolvent plusieurs problèmes connus.

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices---1210083----"></a>Définir les paramètres de connexion et contrôler les options de redémarrage sur les appareils macOS<!-- 1210083  -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de fenêtre de connexion, comme l’affichage d’une bannière personnalisée, le choix de la façon dont les utilisateurs se connectent, l’affichage ou le masquage des paramètres d’alimentation, et plus encore.

Pour afficher ces paramètres, accédez à [Paramètres des fonctionnalités d’appareil macOS](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode--3041940----"></a>Configurer le Wi-Fi sur les appareils dédiés des propriétaires d’appareils Android Entreprise s’exécutant en mode kiosque multi-application<!--3041940  -->
Vous pouvez activer des paramètres sur un propriétaire d’appareil Android Entreprise en cas d’exécution en tant qu’appareil dédié en mode kiosque multi-application. Dans cette mise à jour, vous pouvez permettre aux utilisateurs de configurer des réseaux Wi-Fi et à s’y connecter (**Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions sur l’appareil** pour le type de profil > **Appareils dédiés** > **Mode kiosque** : **Multi-application** > **Configuration Wi-Fi**).

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md).

S’applique à : Appareils dédiés Android Entreprise s’exécutant en mode kiosque multi-application

#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041941----"></a>Configurer le Bluetooth et l’appairage sur les appareils dédiés des propriétaires d’appareils Android Entreprise s’exécutant en mode kiosque multi-application<!-- 3041941  -->
Vous pouvez activer des paramètres sur un propriétaire d’appareil Android Entreprise en cas d’exécution en tant qu’appareil dédié en mode kiosque multi-application. Dans cette mise à jour, vous pouvez autoriser les utilisateurs finaux à activer le Bluetooth et à appairer les appareils en Bluetooth (**Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions sur l’appareil** pour le type de profil > **Appareils dédiés** > **Mode kiosque** : **Multi-application** > **Configuration Bluetooth**).

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md).

S’applique à : Appareils dédiés Android Entreprise s’exécutant en mode kiosque multi-application

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune---3305883----"></a>Créer et utiliser des profils de configuration d’appareils OEMConfig dans Intune<!-- 3305883  -->
Dans cette mise à jour, Intune prend en charge la configuration des appareils Android Entreprise avec OEMConfig. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres à des appareils Android Entreprise à l’aide d’OEMConfig (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme).

La prise en charge des fabricants OEM s’effectue actuellement par OEM. Si une application OEMConfig que vous voulez n’est pas disponible dans la liste des applications OEMConfig, contactez `IntuneOEMConfig@microsoft.com`.

Pour en savoir plus sur cette fonctionnalité, accédez à [Utiliser et gérer des appareils Android Entreprise avec OEMConfig dans Microsoft Intune](../configuration/android-oem-configuration-overview.md).

S’applique à : Android Entreprise

#### <a name="windows-update-notifications---3316758-3316782----"></a>Notifications Windows Update<!-- 3316758, 3316782  -->
Nous avons ajouté deux *paramètres d’expérience utilisateur* aux configurations des anneaux de mise à jour Windows que vous pouvez gérer à partir de la console Intune. Vous pouvez désormais :
- Bloquer ou autoriser des utilisateurs à [rechercher des mises à jour Windows](../protect/windows-update-settings.md).
- Gérer le [niveau de notification Windows Update](../protect/windows-update-settings.md) que voient les utilisateurs.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner---3574254----"></a>Nouveaux paramètres de restriction d’appareil pour les propriétaires d’appareils Android Entreprise<!-- 3574254  -->
Sur les appareils Android Entreprise, vous pouvez créer un profil de restriction d’appareil pour autoriser ou restreindre les fonctionnalités, définir des règles de mot de passe, et plus encore (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement > Restrictions sur l’appareil** pour le type de profil). 

Cette mise à jour inclut de nouveaux paramètres de mot de passe et permet un accès complet aux applications dans Google Play Store pour les appareils complètement gérés, entre autres. Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md). 

S’applique à : Appareils Android Entreprise complètement gérés

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10<!-- 3617671 -->

Cette fonctionnalité a été différée et devrait être publiée ultérieurement.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices---3775833-----"></a>Mise à jour des changements apportés à l’interface utilisateur pour le navigateur Microsoft Edge sur les appareils Windows 10 et versions ultérieures<!-- 3775833   -->
Quand vous créez un profil de configuration d’appareil, vous pouvez autoriser ou limiter les fonctionnalités Microsoft Edge sur les appareils Windows 10 et les versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** sur la plateforme > **restrictions d’appareil** pour le type de profil > **Navigateur Microsoft Edge**). Dans cette mise à jour, les paramètres Microsoft Edge sont plus descriptifs et plus faciles à comprendre.

Pour voir ces fonctionnalités, accédez à [Paramètres de restriction d’appareil pour le navigateur Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

S’applique à : Windows 10 et versions ultérieures

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-----3903241-3903244-3903246-----"></a>Prise en charge étendue des appareils Android Entreprise complètement gérés (préversion)<!--   3903241, 3903244, 3903246   -->
Toujours dans la préversion publique, nous avons développé notre prise en charge des appareils Android Entreprise complètement gérés annoncée en janvier 2019 pour inclure les éléments suivants :

- Sur les appareils dédiés et complètement gérés, vous pouvez créer des [stratégies de conformité](../protect/compliance-policy-create-android-for-work.md) pour inclure des règles de mot de passe et une configuration requise pour le système d’exploitation (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil** pour le type de profil).

  Sur les appareils dédiés, l’appareil peut s’afficher comme étant **Non conforme**. L’accès conditionnel n’est pas disponible sur les appareils dédiés. Veillez à effectuer toutes les tâches ou actions pour obtenir des appareils dédiés conformes à vos stratégies attribuées.

- [Accès conditionnel](../protect/conditional-access.md) : les stratégies d’accès conditionnel qui s’appliquent à Android s’appliquent également aux appareils Android Entreprise complètement gérés. Les utilisateurs peuvent désormais inscrire leur appareil complètement géré dans Azure Active Directory à l’aide de l’**application Microsoft Intune**. Ensuite, recherchez et résolvez tous les problèmes de conformité pour accéder aux ressources de l’organisation.

- Nouvelle application utilisateur final (application Microsoft Intune) : il existe une nouvelle application utilisateur final pour les appareils Android complètement managés, appelée **Microsoft Intune**. Cette nouvelle application est légère et moderne, et offre des fonctionnalités similaires à celles de l’application Portail d’entreprise, mais pour les appareils complètement gérés. Pour plus d’informations, consultez [Application Microsoft Intune sur Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Pour configurer des appareils Android complètement managés, accédez à **Inscription des appareils** > **Inscription Android** > **Appareils des utilisateurs complètement managés appartenant à l’entreprise**. La prise en charge des appareils Android complètement gérés reste en préversion et certaines fonctionnalités Intune peuvent ne pas être entièrement opérationnelles.  

Pour en savoir plus sur cette préversion, consultez notre blog [Microsoft Intune - Preview 2 pour les appareils Android complètement gérés](https://aka.ms/preview2_AE_fullymanaged).

#### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Utiliser le Gestionnaire de conformité pour créer des évaluations pour Microsoft Intune<!-- 4404750 -->

Le [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) (qui ouvre un autre site Microsoft) est un outil d’évaluation des risques basés sur les workflows dans le portail Microsoft Service Trust. Il vous permet de suivre, d’attribuer et de vérifier les activités de conformité aux normes de votre organisation liées aux services Microsoft. Vous pouvez créer votre propre évaluation de conformité avec Office 365, Azure, Dynamics, les Services professionnels et Intune. Deux évaluations sont disponibles dans Intune : FFIEC et RGPD.

Le Gestionnaire de conformité vous permet de faire converger vos efforts en décomposant les contrôles : les contrôles gérés par Microsoft et les contrôles gérés par votre organisation. Vous pouvez effectuer les évaluations, puis les exporter et les imprimer.

La conformité au [FFIEC (Federal Financial Institutions examen Conseil)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (qui ouvre un autre site Microsoft) est un ensemble de normes applicables aux opérations bancaires en ligne émises par le FFIEC. Il s’agit de l’évaluation la plus demandée pour les établissements financiers qui utilisent Intune. Elle interprète la façon dont Intune aide à satisfaire les exigences de cybersécurité liées aux workloads dans le cloud public. L’évaluation FFIEC d’Intune est la deuxième évaluation FFIEC dans le Gestionnaire de conformité.

Dans l’exemple suivant, vous pouvez voir la répartition des contrôles FFIEC. Microsoft traite 64 contrôles. Vous êtes chargé des 12 autres contrôles.

![Consultez un exemple d’évaluation Intune pour le FFIEC, notamment les actions du client et les actions de Microsoft](./media/whats-new/intune-ffiec-assessment-status.png)

Le [Règlement général sur la protection des données (RGPD)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (qui ouvre un autre site Microsoft) est une loi de l’Union européenne (UE) qui permet de protéger les droits des individus et leurs données. Le RGPD est l’évaluation la plus demandée pour permettre de se conformer aux réglementations sur la protection des données personnelles. 

Dans l’exemple suivant, vous voyez la répartition des contrôles RGPD. Microsoft traite 49 contrôles. Vous êtes chargé des 66 autres contrôles.

![Consultez un exemple d’évaluation Intune pour le RGPD, notamment les actions du client et les actions de Microsoft](./media/whats-new/intune-assessment-status.png)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant---2276470----"></a>Configurer le profil pour ignorer certains écrans lors de l’exécution de l’Assistant Configuration<!-- 2276470  -->
Lors de la création d’un profil d’inscription macOS, vous pouvez le configurer pour ignorer les écrans suivants quand un utilisateur exécute l’Assistant Configuration :
- Apparence
- Display Tone (Indiquer la tonalité)
- iCloudStorage : si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple.  Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.
Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils ou Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Nommage d’appareils en bloc lors de l’inscription d’appareils iOS d’entreprise<!--3566569  -->
Quand vous utilisez l’une des méthodes d’inscription d’entreprise d’Apple (DEP/ABM/ASM), vous pouvez définir un format de nom d’appareil pour nommer automatiquement les appareils iOS entrants. Vous pouvez spécifier un format qui inclut le type d’appareil et le numéro de série dans votre modèle. Pour ce faire, choisissez **Intune** > **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription** > **Sélectionner un jeton** >**Créer un profil** > **Format de nommage d’appareil**. Vous pouvez modifier des profils existants, mais le nom sera appliqué uniquement aux appareils récemment synchronisés.

#### <a name="updated-default-timeout-message-on-enrollment-status-page---3959331---"></a>Mise à jour du message d’expiration par défaut dans la page d’état d’inscription<!-- 3959331 -->
Nous avons mis à jour le message d’expiration par défaut que les utilisateurs voient quand la page d’état d’inscription (ESP) dépasse la valeur de délai spécifiée dans le profil ESP. Le nouveau message par défaut est ce que les utilisateurs voient et ce qui les aide à comprendre les actions suivantes à entreprendre avec leur déploiement ESP.  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques

#### <a name="retire-noncompliant-devices---1827291-----"></a>Mettre hors service les appareils non conformes<!-- 1827291   -->
Cette fonctionnalité a été différée et devrait être publiée ultérieurement.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta---4403765---"></a>Changements de l’entrepôt de données Intune V1.0 se reflétant vers la version bêta<!-- 4403765 -->
Quand la version V1.0 a été introduite dans 1808, elle comportait certaines différences significatives par rapport à la version bêta de l’API. Dans 1903, ces changements seront reflétés dans la version bêta de l’API. Si vous avez des rapports importants qui utilisent la version bêta de l’API, nous vous recommandons vivement de passer ces rapports en version V1.0 afin d’éviter les changements cassants. Pour plus d’informations, consultez [Journal des changements pour l’API de l’entrepôt de données Intune](../developer/reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Superviser l’état de la base de référence de sécurité (préversion publique) <!-- 3082047 --> 
Nous avons ajouté une [vue par catégorie](../protect/security-baselines-monitor.md#per-category-view) pour la supervision des bases de référence de sécurité. (Les bases de référence de sécurité restent en préversion). La vue par catégorie affiche chaque catégorie de la base de référence, ainsi que le pourcentage d’appareils appartenant à chaque groupe d’état pour cette catégorie. Vous pouvez maintenant voir combien d’appareils ne correspondent pas aux catégories individuelles, sont mal configurés ou ne sont pas applicables.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="scope-tags-for-apple-vpp-tokens--2371886----"></a>Balises d’étendue pour les jetons VPP Apple<!--2371886  -->
Vous pouvez maintenant ajouter des balises d’étendue à des jetons VPP Apple. Seuls les utilisateurs attribués avec la même balise d’étendue ont accès au jeton VPP Apple ayant cette balise. Les applications et livres électroniques VPP achetés avec ce jeton héritent de ses balises d’étendue. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

<!-- ########################## -->
## <a name="march-2019"></a>Mars 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications
#### <a name="deploy-microsoft-visio-and-microsoft-project---3725386----"></a>Déployer Microsoft Visio et Microsoft Project<!-- 3725386  -->
Vous pouvez désormais déployer Microsoft Visio Pro pour Office 365 et le client de bureau Microsoft Project Online en tant qu’applications indépendantes pour les appareils Windows 10 à l’aide de Microsoft Intune, si vous possédez des licences pour ces applications. À partir d’Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Dans le panneau **Ajouter une application**, sélectionnez **Windows 10** comme **Type d’application**. Sélectionnez ensuite **Configurer la suite d’applications** pour sélectionner les applications à installer. Pour plus d’informations sur les applications Office 365 pour des appareils Windows 10, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change---3593653----"></a>Changement de nom du produit Microsoft Visio Pro pour Office 365<!-- 3593653  -->
**Microsoft Visio Pro pour Office 365** s’appellera désormais **Microsoft Visio Online - Plan 2**.  Pour plus d’informations sur Microsoft Visio, consultez [Visio Online - Plan 2](https://products.office.com/visio/visio-online-plan-2). Pour plus d’informations sur les applications Office 365 pour des appareils Windows 10, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting---3291302----"></a>Paramètre de limite de caractères d’une stratégie de protection d’application Intune<!-- 3291302  -->
Les administrateurs Intune peuvent spécifier une exception au paramètre de stratégie **Restreindre les opérations Couper, Copier et Coller avec d’autres applications** de la stratégie de protection d’application Intune.  En tant qu’administrateur, vous pouvez spécifier le nombre de caractères qui peuvent être coupés ou copiés à partir d’une application gérée. Ce paramètre permet de partager le nombre spécifié de caractères avec toute application, quelle que soit la valeur du paramètre « Restreindre les opérations Couper, Copier et Coller avec d’autres applications ». Notez que la version de l’application Portail d’entreprise Intune pour Android exige la version 5.0.4364.0 ou une version ultérieure. Pour plus d’informations, consultez [Protection des données iOS](../apps/app-protection-policy-settings-ios.md#data-protection), [Protection des données Android](../apps/app-protection-policy-settings-android.md#data-protection) et [Consulter les journaux de la protection des applications clientes](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment---3192477-----"></a>Code XML de l’outil Déploiement d’Office (ODT) pour le déploiement d’Office ProPlus<!-- 3192477   -->
Vous pourrez fournir le code XML de l’outil Déploiement d’Office (ODT) lors de la création d’une instance d’Office ProPlus dans la console d’administration Intune. Cela offre davantage de possibilités de personnalisation si les options existantes de l’interface utilisateur Intune ne répondent pas à vos besoins. Pour plus d’informations, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md) et [Options de configuration pour l’outil Déploiement d’Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background---1429026----"></a>Les icônes d’application s’affichent désormais avec un arrière-plan généré automatiquement<!-- 1429026  -->
Dans l’application Portail d’entreprise Windows, des icônes d’application s’afficheront désormais avec un arrière-plan généré automatiquement en fonction de la couleur dominante de l’icône (si elle peut être détectée). S’il y a lieu, cet arrière-plan remplacera la bordure grise qui était précédemment visible sur les vignettes d’application. Les utilisateurs verront ce changement dans les versions du portail d’entreprise ultérieures à 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment---2751523-----"></a>Installer des applications disponibles à l’aide de l’application Portail d’entreprise après l’inscription en bloc de Windows<!-- 2751523   -->
Les appareils Windows inscrits auprès d’Intune à l’aide de l’[inscription en bloc de Windows](../enrollment/windows-bulk-enroll.md) (packages de provisionnement) pourront utiliser l’application Portail d’entreprise pour installer des applications disponibles. Pour plus d’informations sur l’application Portail d’entreprise, consultez [Ajouter manuellement l’application Portail d’entreprise Windows 10](../apps/store-apps-company-portal-app.md) et [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite---3828932----"></a>L’application Microsoft Teams peut être sélectionnée comme faisant partie de la suite d’applications Office<!-- 3828932  -->
L’application Microsoft Teams peut être incluse ou exclue dans l’installation de la suite d’applications Office ProPlus. Cette fonctionnalité fonctionne pour le numéro de build 16.0.11328.20116+ d’Office ProPlus. L’utilisateur doit se déconnecter puis se connecter à l’appareil pour terminer l’installation. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez l’un des types d’application de la **Suite Office 365**, puis sélectionnez **Configurer la suite d’applications**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices---2351390---"></a>Démarrer automatiquement une application quand vous exécutez plusieurs applications en mode kiosque sur les appareils Windows 10 et les versions ultérieures<!-- 2351390 -->

Sur Windows 10 et les versions ultérieures, vous pouvez exécuter un appareil en mode kiosque et exécuter de nombreuses applications. Cette mise à jour comprend un paramètre **Démarrage automatique** (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil > **Kiosque multi-application**). Utilisez ce paramètre pour démarrer automatiquement une application quand l’utilisateur se connecte à l’appareil.

Pour obtenir la liste et la description de tous les paramètres kiosque, consultez [Paramètres d’appareil Windows 10 et versions ultérieures pour une exécution en tant que kiosque dans Intune](../configuration/kiosk-settings-windows.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="operational-logs-also-show-details-on-non-compliant-devices---4063755----"></a>Les journaux des opérations donnent également des détails sur les appareils non conformes<!-- 4063755  -->
Lors du routage de journaux Intune vers des fonctionnalités de supervision Azure, vous pouvez également router les journaux des opérations. Dans cette mise à jour, les journaux des opérations fournissent également des informations sur les appareils non conformes.

Pour plus d’informations sur cette fonctionnalité, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads---3804627---"></a>Router des journaux vers Azure Monitor dans un plus grand nombre de workloads Intune<!-- 3804627 -->
Dans Intune, vous pouvez router des journaux d’audit et des journaux des opérations vers des hubs d’événements, du stockage et de l’analytique des journaux d’activité dans Azure Monitor (**Intune** > **Supervision** > **Paramètres de diagnostic**). Dans cette mise à jour, vous pouvez router ces journaux dans un plus grand nombre de workloads Intune, notamment la conformité, les configurations, les applications clientes, entre autres.

Pour en savoir plus sur le routage de journaux vers Azure Monitor, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics](../review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune---3305880-----"></a>Créer et utiliser Mobility Extensions sur les appareils Android Zebra dans Intune<!-- 3305880   -->
Dans cette mise à jour, Intune prend en charge la configuration des appareils Android Zebra. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres aux appareils Android Zebra à l’aide de profils Mobility Extensions (MX) générés par StageNow (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android** pour la plateforme > **Profil MX (Zebra uniquement)** pour le type de profil).

Pour plus d’informations sur cette fonctionnalité, consultez [Utiliser et gérer des appareils Zebra avec des extensions de mobilité dans Intune](../configuration/android-zebra-mx-overview.md).

S’applique à : Android

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques
#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Rapport de chiffrement pour les appareils Windows 10 (en préversion publique)<!-- 2351538 -->
Utilisez le nouveau [rapport de chiffrement (préversion)](../protect/encryption-monitor.md) pour voir des détails sur l’état de chiffrement de vos appareils Windows 10. Les détails disponibles incluent la version TPM d’un appareil, la préparation et l’état du chiffrement, la création de rapports d’erreurs, et plus encore.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview---2351547-----"></a>Accéder aux clés de récupération BitLocker à partir du portail Intune (en préversion publique)<!-- 2351547   -->
Vous pouvez désormais utiliser Intune pour [afficher des détails](../protect/encryption-monitor.md) sur l’ID de clé BitLocker et les clés de récupération BitLocker à partir d’Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Prise en charge de Microsoft Edge pour des scénarios Intune sur des appareils iOS et Android<!-- 3411007 -->
Microsoft Edge prendra en charge les mêmes scénarios de gestion qu’Intune Managed Browser avec, en plus, des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise de Microsoft Edge qui sont activées par des stratégies Intune incluent la double identité, l’intégration de stratégies de protection des applications, l’intégration de proxy d’application Azure, ainsi que les raccourcis de page d’accueil et les favoris gérés. Pour plus d’informations, consultez [Prise en charge de Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices--3105122----"></a>Le connecteur Exchange Online/Intune cessera de prendre en charge les appareils uniquement EAS<!--3105122  -->
La console Intune ne prend plus en charge l’affichage et la gestion des appareils uniquement EAS connectés à Exchange Online avec le connecteur Intune. À la place, vous disposez des options suivantes :
- inscrire les appareils auprès de la gestion des appareils mobiles (MDM) ;
- utiliser des stratégies Intune App Protection pour gérer vos appareils ;
- utiliser les contrôles Exchange comme indiqué dans [Appareils clients et mobiles dans Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online).

#### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name--4254930---"></a>Rechercher un appareil précis dans la page Tous les appareils à l’aide de [nom]<!--4254930 -->
Vous pouvez désormais rechercher un nom de d’appareil exact. Accédez à **Intune** > **Appareils** > **Tous les appareils** > dans la zone de recherche, placez le nom de l’appareil entre {} pour rechercher un correspondance exacte. Par exemple, **{Appareil12345}**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="support-for-additional-connectors-on-the-tenant-status-page---3617202----"></a>Prise en charge de connecteurs supplémentaires dans la page État du locataire<!-- 3617202  -->
La [page État du locataire](../tenant-status.md) affiche maintenant des informations sur l’état des connecteurs supplémentaires, notamment *Windows Defender - Protection avancée contre les menaces* (ATP) et d’autres connecteurs Mobile Threat Defense.

#### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune---4260871---"></a>Prise en charge de l’application Conformité de Power BI à partir du panneau Entrepôt de données dans Microsoft Intune<!-- 4260871 -->
Auparavant, le lien **Télécharger le fichier Power BI** dans le panneau **Entrepôt de données Intune** téléchargeait un rapport de l’entrepôt de données Intune (fichier .pbix). Ce rapport a été remplacé par l’application Conformité de Power BI. L’application Conformité de Power BI ne nécessite pas de chargement ou de configuration spéciaux. Elle s’ouvrira directement dans le portail en ligne Power BI et affichera des données spécifiquement pour votre locataire Intune en fonction de vos informations d’identification. Dans Intune, sélectionnez le lien **Configurer l’entrepôt de données Intune** à droite du panneau Intune. Cliquez ensuite sur **Obtenir l’application Power BI**. Pour plus d’informations, consultez [Se connecter à l’entrepôt de données avec Power BI](../developer/reports-proc-get-a-link-powerbi.md).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles---3637917----"></a>Octroi d’un accès en lecture seule Intune à certains rôles Azure Active Directory<!-- 3637917  -->
L’accès en lecture seule Intune a été octroyé aux rôles Azure AD suivants. Les autorisations accordées avec les rôles Azure AD remplacent les autorisations accordées avec le contrôle d’accès en fonction du rôle (RBAC) Intune.

Accès en lecture seule aux données d’audit Intune :

- Administrateur de conformité
- Administrateur des données de conformité

Accès en lecture seule à toutes les données Intune :

- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur Sécurité

Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles--2934430-----"></a>Balises d’étendue pour les profils de provisionnement d’applications iOS<!--2934430   -->
Vous pouvez ajouter une balise d’étendue à un profil de provisionnement d’application iOS afin que seules les personnes avec des rôles auxquels cette balise d’étendue a également été attribuée aient accès au profil de provisionnement d’application iOS. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies--2371891-----"></a>Balises d’étendue pour les stratégies de configuration des applications<!--2371891   -->
Vous pouvez ajouter une balise d’étendue à une stratégie de configuration des applications afin que seules les personnes avec des rôles auxquels cette balise d’étendue a également été attribuée aient accès à la stratégie de configuration des applications. La stratégie de configuration des applications peut uniquement cibler des applications auxquelles la même balise d’étendue a été attribuée ou être associée à ces applications. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Prise en charge de Microsoft Edge pour des scénarios Intune sur des appareils iOS et Android<!-- 3411007 -->
Microsoft Edge prendra en charge les mêmes scénarios de gestion qu’Intune Managed Browser avec, en plus, des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise de Microsoft Edge qui sont activées par des stratégies Intune incluent la double identité, l’intégration de stratégies de protection des applications, l’intégration de proxy d’application Azure, ainsi que les raccourcis de page d’accueil et les favoris gérés. Pour plus d’informations, consultez [Prise en charge de Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).




<!-- ########################## -->
## <a name="february-2019"></a>Février 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications
#### <a name="intune-macos-company-portal-dark-mode---3300524----"></a>Mode sombre du portail d’entreprise macOS Intune<!-- 3300524  -->
Le portail d’entreprise Intune macOS prend désormais en charge le Mode sombre pour macOS. Quand vous activez le Mode sombre sur un appareil macOS 10.14+, le portail d’entreprise ajuste son apparence à des couleurs reflétant ce mode.

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices---2577355-----"></a>Intune exploitera les API Google Play Protect sur les appareils Android<!-- 2577355   -->
Certains administrateurs informatiques sont confrontés à un « paysage » BYOD où les téléphones mobiles des utilisateurs finaux peuvent être rootés ou jailbreakés. Ce comportement, bien que n’étant parfois pas mal intentionné, entraîne un contournement de nombreuses stratégies Intune définies pour protéger les données de l’organisation sur les appareils des utilisateurs finaux. Par conséquent, Intune permet donc la détection du rootage et du jailbreaking pour les appareils inscrits et désinscrits. Avec cette version, Intune peut désormais tirer parti des API Google Play Protect, qui s’ajoutent à nos contrôles de détection du rootage pour les appareils non inscrits. Même si Google ne partage pas l’intégralité des contrôles de détection du rootage qui sont effectués, nous pensons que ces API vont détecter les utilisateurs qui ont rooté leurs appareils pour une raison quelconque, allant de la personnalisation de l’appareil à l’obtention de mises à jour plus récentes du système d’exploitation sur des appareils plus anciens. L’accès de ces utilisateurs aux données de l’entreprise peut alors être bloqué, ou leurs comptes professionnels peuvent être supprimés des applications pour lesquelles une stratégie est activée. L’administrateur informatique dispose désormais de plusieurs mises à jour d’amélioration des rapports dans le panneau Intune App Protection : le rapport « Utilisateurs avec indicateur » montre les utilisateurs qui sont détectés via l’analyse de l’API SafetyNet de Google Play Protect, et le rapport « Applications potentiellement dangereuses » montre les applications qui sont détectées via l’analyse de l’API Verify Apps de Google. Cette fonctionnalité est disponible sur Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade---2617342-----"></a>Informations sur les applications Win32 disponibles dans le panneau Résolution des problèmes<!-- 2617342   -->
Vous pouvez désormais collecter des fichiers journaux des échecs pour l’installation d’une application Win32 à partir du panneau **Résolution des problèmes** des applications Intune. Pour plus d’informations sur la résolution des problèmes liés à l’installation d’une application, consultez [Résoudre les problèmes d’installation d’applications](./../apps/troubleshoot-app-install.md) et [Résoudre les problèmes d’application Win32](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting).

#### <a name="app-status-details-for-ios-apps---3761235-----"></a>Détails de l’état des applications pour les applications iOS<!-- 3761235   -->
Des nouveaux messages d’erreur d’installation d’une application ont été ajoutés et concernent les échecs suivants :
- Échec pour les applications VPP lors de l’installation sur un iPad partagé
- Échec quand l’App Store est désactivé
- Échec de la recherche d’une licence VPP pour l’application
- Échec de l’installation d’applications système avec le fournisseur MDM
- Échec de l’installation d’applications quand l’appareil est en mode perdu ou en mode kiosque
- Échec de l’installation d’applications quand l’utilisateur n’est pas connecté à l’App Store

Dans Intune, sélectionnez **Applications clientes** > **Applications** > « Nom de l’application » > **État de l’installation de l’appareil**. Les nouveaux messages d’erreur sont disponibles dans la colonne **Détails du statut**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nouvel écran Catégories d’application dans l’application Portail d’entreprise pour Windows 10<!-- 3834780  -->
Un nouvel écran appelé **Catégories d’application** a été ajouté pour améliorer l’expérience de navigation et de sélection des applications dans le portail d’entreprise pour Windows 10. Les applications des utilisateurs s’affichent désormais triées dans des catégories telles que **Proposée(s)**, **Éducation** et **Productivité**. Ce changement apparaît dans la version 10.3.3451.0 et les versions ultérieures du portail d’entreprise. Pour afficher le nouvel écran, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md). Pour plus d’informations sur les applications dans le portail d’entreprise, consultez [Installer et partager des applications sur votre appareil](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app---1455231-doc-work-item---"></a>Application Conformité de Power BI<!-- 1455231 doc-work-item -->
Accédez à votre entrepôt de données Intune dans Power BI à l’aide de l’application [Conformité Intune (Entrepôt de données)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Avec cette application Power BI, vous pouvez désormais accéder à des rapports précréés et les partager sans aucune configuration supplémentaire et sans quitter votre navigateur web. Pour plus d’informations, consultez [Journal des changements - Application Conformité de Power BI](../developer/reports-changelog.md#power-bi-compliance-app).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices---1862675-----"></a>Les scripts PowerShell peuvent s’exécuter dans un hôte 64 bits sur des appareils 64 bits<!-- 1862675   -->
Quand vous ajoutez un script PowerShell à un profil de configuration d’appareil, le script s’exécute toujours en 32 bits, même sur les systèmes d’exploitation 64 bits. Avec cette mise à jour, un administrateur peut exécuter le script dans un hôte PowerShell 64 bits sur des appareils 64 bits (**Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter** > **Configurer** > **Exécuter le script dans un hôte PowerShell 64 bits**).

Pour plus d’informations sur l’utilisation de PowerShell, consultez [Scripts PowerShell dans Intune](../apps/intune-management-extension.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="macos-users-are-prompted-to-update-their-password---1873216---"></a>Les utilisateurs macOS sont invités à mettre à jour leur mot de passe<!-- 1873216 -->
Intune applique le paramètre **ChangeAtNextAuth** sur les appareils macOS. Ce paramètre a un impact sur les utilisateurs finaux et sur les appareils qui ont des stratégies de conformité des mots de passe ou des profils de mot de passe de restriction sur les appareils. Les utilisateurs finaux sont invités à mettre à jour une fois leur mot de passe. Cette invite se produit chaque fois qu’un utilisateur exécute pour la première fois une tâche nécessitant une authentification, comme la connexion à l’appareil. Les utilisateurs peuvent également être invités à mettre à jour leur mot de passe lors de l’exécution de toute opération nécessitant des privilèges d’administration, comme la demande d’accès au trousseau.

Tout changement apporté à une stratégie de mot de passe nouvelle ou existante par l’administrateur invite les utilisateurs finaux à mettre à nouveau à jour leur mot de passe.

S’applique à :  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device---2340521------"></a>Attribuer des certificats SCEP à un appareil macOS sans utilisateur<!-- 2340521    -->
Vous pouvez attribuer des certificats SCEP (Simple Certificate Enrollment Protocol, protocole d’inscription de certificats simple) à l’aide d’attributs d’appareil à des appareils macOS, notamment à des appareils sans affinité utilisateur, et associer le profil de certificat à des profils Wi-Fi ou VPN. La prise en charge existante est ainsi étendue, permettant d’[attribuer des certificats SCEP à des appareils avec et sans affinité utilisateur](../protect/certificates-profile-scep.md) qui exécutent Windows, iOS et Android.  Cette mise à jour ajoute la possibilité de sélectionner le type de certificat *Appareil* quand vous configurez un profil de certificat SCEP pour macOS.

S’applique à :
- macOS

#### <a name="intune-conditional-access-ui-update---2432313-----"></a>Mise à jour de l’interface utilisateur de l’accès conditionnel Intune<!-- 2432313   -->
Nous avons apporté des améliorations à l’interface utilisateur pour l’accès conditionnel dans la console Intune. À savoir :
- Remplacement du panneau *Accès conditionnel* d’Intune par le panneau d’Azure Active Directory. Cela garantit que vous avez accès à la gamme complète des paramètres et des configurations pour l’[accès conditionnel](../protect/conditional-access.md) (qui reste une technologie Azure AD) à partir de la console Intune. 
- Nous avons renommé le panneau *Accès local* en *Accès à Exchange*, et déplacé le programme d’installation *Connecteur de service Exchange* dans ce panneau renommé.  Ce changement consolide l’endroit où vous [configurez et supervisez les détails relatifs à Exchange Online et local](../protect/exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode---2935135-----"></a>Les applications de navigateur kiosque et de navigateur Microsoft Edge peuvent s’exécuter sur des appareils Windows 10 en mode kiosque<!-- 2935135   -->
Vous pouvez utiliser des appareils Windows 10 en mode kiosque pour exécuter une ou plusieurs applications. Cette mise à jour inclut plusieurs modifications de l’utilisation des applications de navigateur en mode kiosque, notamment :

- Ajoutez le navigateur Microsoft Edge ou le navigateur kiosque pour qu’ils s’exécutent comme applications sur l’appareil kiosque (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil).
- De nouvelles fonctionnalités et de nouveaux paramètres sont disponibles pour définir des autorisations ou des restrictions (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **Windows 10 et ultérieur** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil), notamment :

- Navigateur Microsoft Edge :
  - Utiliser le mode kiosque Microsoft Edge
  - Actualiser le navigateur après la durée d’inactivité

- Favoris et recherche :
  - Autoriser les changements sur le moteur de recherche

Pour obtenir la liste de ces paramètres, consultez :

- [Paramètres d’appareil Windows 10 et ultérieur pour une exécution en tant que kiosque ](../configuration/kiosk-settings-windows.md)
- [Restrictions d’appareil pour le navigateur Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Restrictions d’appareils concernant les favoris et la recherche](../configuration/device-restrictions-windows-10.md##favorites-and-search)

S’applique à : Windows 10 et versions ultérieures

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices---3448774-----"></a>Nouveaux paramètres de restriction d’appareil pour les appareils iOS et macOS<!-- 3448774   -->
Vous pouvez restreindre certains paramètres et certaines fonctionnalités sur les appareils exécutant iOS et macOS (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** ou **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour ajoute des fonctionnalités et des paramètres que vous pouvez contrôler, notamment définir l’heure de l’écran, modifier les paramètres eSIM et les forfaits mobiles, entre autres, sur les appareils iOS. Citons également le retardement de la visibilité par l’utilisateur des mises à jour logicielles, ainsi que le blocage de la mise en cache du contenu sur les appareils iOS.

Pour connaître les fonctionnalités et les paramètres que vous pouvez restreindre, consultez :

- [Paramètres de restriction d’appareil iOS](../configuration/device-restrictions-ios.md)
- [Paramètres de restriction d’appareil macOS](../configuration/device-restrictions-macos.md)

S’applique à :

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices---3598402-----"></a>Les appareils « kiosque » sont désormais appelés « appareils dédiés » sur les appareils Android Entreprise<!-- 3598402   -->
Pour s’aligner sur la terminologie d’Android, **kiosque** est remplacé par **appareils dédiés** pour les appareils Android Entreprise (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise pour la plateforme > **Propriétaire de l’appareil uniquement** > **Restrictions sur l’appareil** > **Appareils dédiés**).

Pour afficher les paramètres disponibles, accédez à [Paramètres des appareils pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

S’applique à :  
Android Entreprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui---3640850-3803313-----"></a>Les paramètres Safari et Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS sont déplacés dans l’interface utilisateur Intune<!-- 3640850, 3803313   -->
Pour les appareils iOS, vous pouvez définir des paramètres Safari et configurer les mises à jour logicielles. Dans cette mise à jour, ces paramètres sont déplacés dans différentes parties de l’interface utilisateur Intune :

- Les paramètres Safari sont passés de **Safari** (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil) à **[Applications intégrées](../configuration/device-restrictions-ios.md#built-in-apps)**.
- Le paramètre **Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS supervisés** (**Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS**) est déplacé dans **Restrictions sur l’appareil** > **[Général](../configuration/device-restrictions-ios.md#general)**.  Pour plus d’informations sur l’impact sur les stratégies existantes, consultez [Mises à jour logicielles iOS](../protect/software-updates-ios.md#configure-the-policy).

Pour obtenir la liste des paramètres, consultez :

- [Restrictions sur les appareils iOS](../configuration/device-restrictions-ios.md) 
- [Mises à jour logicielles iOS](../protect/software-updates-ios.md)

Cette fonctionnalité s’applique à :

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices---3699164-----"></a>L’option Activation des restrictions dans les paramètres de l’appareil est renommée en Heure de l’écran sur les appareils iOS<!-- 3699164   -->
Vous pouvez configurer **Activation des restrictions dans les paramètres de l’appareil** sur les appareils iOS supervisés (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour le type de profil > **Général**). Dans cette mise à jour, ce paramètre est renommé en **Heure de l’écran (mode supervisé uniquement)**.

Le comportement reste le même. Plus précisément :

- iOS 11.4.1 et antérieur : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. 
- iOS 12.0 et ultérieur : **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil, notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 ne voient plus l’onglet Restrictions dans les paramètres de l’appareil. Ces paramètres se trouvent dans **Heure de l’écran**. 

Pour obtenir la liste des paramètres, consultez [Restrictions sur les appareils iOS](../configuration/device-restrictions-ios.md#general).

S’applique à :
- iOS


#### <a name="intune-powershell-module---951068----"></a>Module PowerShell Intune<!-- 951068  -->
Le nouveau module PowerShell Intune, qui offre une prise en charge de l’API Intune par le biais de Microsoft Graph, est désormais disponible dans [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Informations sur la façon d’utiliser ce module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemples de scénarios utilisant ce module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization--3183757----"></a>Prise en charge améliorée de l’optimisation de la distribution<!--3183757  -->
Nous avons étendu la prise en charge de la configuration de l’optimisation de la distribution dans Intune. Vous pouvez désormais configurer une liste développée de [paramètres d’optimisation de la distribution](../configuration/delivery-optimization-settings.md) et la cibler sur vos appareils directement à partir de la console Intune.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques

#### <a name="rename-an-enrolled-windows-device---1911112----"></a>Renommer un appareil Windows inscrit<!-- 1911112  -->
Vous pouvez maintenant renommer un appareil Windows 10 inscrit (RS4 ou version ultérieure). Pour cela, choisissez **Intune** > **Appareils** > **Tous les appareils** > Choisissez un appareil > **Renommer l’appareil**. Cette fonctionnalité ne prend actuellement pas en charge le renommage des appareils Azure AD Windows hybrides.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope---3173823----"></a>Attribuer automatiquement des balises d’étendue à des ressources créées par un administrateur avec cette étendue<!-- 3173823  -->
Quand un administrateur crée une ressource, les étiquettes d’étendue affectées à l’administrateur sont automatiquement affectées à cette nouvelle ressource.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade---3560202----"></a>Le rapport des échecs d’inscription est déplacé dans le panneau Inscription des appareils<!-- 3560202  -->
Le rapport **Échecs d’inscription** a été déplacé dans la section **Superviser** du panneau **Inscription de l’appareil**. Deux nouvelles colonnes (Méthode d’inscription et Version du système d’exploitation) ont été ajoutées.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments--3815076-eemiss---"></a>Rapport d’abandon du portail d’entreprise renommé en Inscriptions d’utilisateur incomplètes<!--3815076 eemiss -->
Le **rapport d’abandon du portail d’entreprise** a été renommé en **Inscriptions d’utilisateur incomplètes**.






<!-- ########################## -->
## <a name="january-2019"></a>Janvier 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="intune-app-pin---2298397---"></a>Code PIN d’application Intune<!-- 2298397 -->
En tant qu’administrateur informatique, vous pouvez maintenant configurer le nombre de jours d’attente possibles pour un utilisateur final avant qu’il ne doive changer le code PIN d’application Intune. Le nouveau paramètre, *Réinitialisation du code PIN au bout d’un nombre de jours*, est accessible dans le portail Azure en sélectionnant **Intune** > **Applications clientes** > **Stratégies de protection des applications** > **Créer une stratégie** > **Paramètres** > **Conditions d’accès**. Disponible pour les appareils [iOS](../apps/app-protection-policy-settings-ios.md) et [Android](../apps/app-protection-policy-settings-android.md), cette fonctionnalité prend en charge une valeur entière positive.

#### <a name="intune-device-reporting-fields---2748738---"></a>Champs de création de rapport sur les appareils Intune<!-- 2748738 -->
Intune fournit des champs de création de rapport supplémentaires sur les appareils, notamment l’ID d’inscription d’application, le fabricant Android, le modèle et la version du correctif de sécurité ainsi que le modèle iOS. Dans Intune, ces champs sont disponibles quand vous sélectionnez **Applications clientes** > **État de protection de l’application**, et que vous choisissez **Rapport de protection d’application : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android.

#### <a name="toast-notifications-for-win32-apps---3136566-----"></a>Notifications toast pour les applications Win32<!-- 3136566   -->
Vous pouvez supprimer l’affichage des notifications toast à l’utilisateur final par affectation d’applications. Dans Intune, sélectionnez **Applications clientes** > **Applications** > sélectionnez l’application > **Affectations** > **Inclure les groupes**.

#### <a name="intune-app-protection-policies-ui-update---3251427----"></a>Mise à jour de l’interface utilisateur des stratégies de protection des applications Intune<!-- 3251427  -->
Nous avons modifié les étiquettes des paramètres et des boutons d’Intune App Protection pour qu’ils soient tous plus faciles à comprendre. Quelques exemples de modifications :  
- Les commandes **Oui** / **Non** sont remplacées principalement par les commandes **Bloquer** / **Autoriser** et **Désactiver** / **Activer**. Les étiquettes sont également mises à jour.  
- Les paramètres ont également été remis en forme pour qu’ils apparaissent à côté de l’étiquette correspondante dans le contrôle, ce qui facilite la navigation.

Les paramètres par défaut et le nombre de paramètres restent identiques. Toutefois, ce changement permet à l’utilisateur de comprendre, de parcourir et d’utiliser les paramètres plus facilement pour appliquer les stratégies App Protection sélectionnées. Pour plus d’informations, consultez [Paramètres iOS](../apps/app-protection-policy-settings-ios.md) et [Paramètres Android](../apps/app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook---3301182----"></a>Paramètres supplémentaires pour Outlook<!-- 3301182  -->
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
> Si vous utilisez des stratégies Intune App Protection pour gérer l’accès aux identités d’entreprise, n’activez pas la **biométrie obligatoire**. Pour plus d’informations, consultez **Exiger des informations d’identification d’entreprise pour l’accès** dans les [paramètres d’accès iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) et les [paramètres d’accès Android](../apps/app-protection-policy-settings-android.md#access-requirements).

Pour plus d’informations, consultez [Paramètres de configuration Microsoft Outlook](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps---1352553---"></a>Supprimer les applications Android Entreprise<!-- 1352553 -->
Vous pouvez supprimer des applications Google Play géré à partir de Microsoft Intune. Pour supprimer une application Google Play géré, ouvrez Microsoft Intune dans le portail Azure et sélectionnez **Applications clientes** > **Applications**. À partir de la liste des applications, sélectionnez les points de suspension (...) à droite de l’application Google Play géré, puis sélectionnez **Supprimer** dans la liste affichée. Lorsque vous supprimez une application Google Play gérée à partir de la liste des applications, l’application Google Play gérée devient automatiquement non approuvée.

#### <a name="managed-google-play-app-type---1352580---"></a>Type d’application Google Play géré<!-- 1352580 -->
Le type d’application **Google Play géré** vous permet d’ajouter spécifiquement [les applications Google Play gérées](https://play.google.com/work/search?q=microsoft&c=apps) à Intune. En tant qu’administrateur Intune, vous pouvez désormais parcourir, rechercher, approuver, synchroniser et attribuer des applications Google Play géré approuvées dans Intune.  Vous n’avez plus besoin d’accéder séparément à la console Google Play géré, ni de vous authentifier de nouveau.  Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application**, sélectionnez le type d’application **Google Play géré**.

#### <a name="default-android-pin-keyboard---3802457---"></a>Clavier de code PIN Android par défaut<!-- 3802457 -->
Les utilisateurs finaux qui ont défini un code PIN de stratégie Intune App Protection sur leurs appareils Android avec un type de code PIN « Numérique » verront désormais le clavier Android par défaut, au lieu de l’interface utilisateur du clavier Android fixe qui était affichée précédemment. Cette modification a été apportée pour des raisons de cohérence lors de l’utilisation des claviers par défaut sur Android et iOS, pour les deux types de code PIN « Numérique » et/ou « Code secret ». Pour plus d’informations sur les paramètres d’accès de l’utilisateur final sur Android, comme le code PIN de la stratégie de protection des applications, consultez [Exigences d’accès Android](../apps/app-protection-policy-settings-android.md#access-requirements).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration <!-- 3322847 -->

Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion publique. Avec cette mise à jour :

- Les modèles d’administration comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
- Les modèles d’administration sont disponibles en préversion publique.
- Les modèles d’administration sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et ultérieur**, dans **Type de profil**, choisissez **Modèles d’administration**.
- La création de rapports est activée

Pour plus d’informations sur cette fonctionnalité, accédez à [Modèles Windows 10 pour configurer les paramètres de stratégie de groupe](../configuration/administrative-templates-windows.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user---1333642---"></a>Utiliser S/MIME pour chiffrer et signer plusieurs appareils pour un utilisateur<!-- 1333642 -->
Cette mise à jour inclut le chiffrement S/MIME des e-mails à l’aide d’un nouveau profil de certificat importé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > type de profil **Certificat PKCS importé**). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :
- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.
Pour plus d’informations sur cette fonctionnalité, consultez [Vue d’ensemble de S/MIME pour signer et chiffrer des e-mails](../protect/certificates-s-mime-encryption-sign.md).
Pris en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices---1333665-2999078---"></a>Nouvelles options de connexion automatique et de conservation automatique des règles quand vous utilisez des paramètres DNS sur les appareils Windows 10 et les versions ultérieures<!-- 1333665, 2999078 -->
Sur les appareils Windows 10 et ultérieur, vous pouvez créer un profil de configuration VPN qui comporte la liste des serveurs DNS permettant de résoudre les domaines, par exemple contoso.com. Cette mise à jour contient de nouveaux paramètres de résolution de noms (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Windows 10 et ultérieur** comme plateforme > choisissez **VPN** comme type de profil > **Paramètres DNS** >**Ajouter**) : 
- **Connexion automatique** : lorsque ce paramètre est **Activé**, l’appareil se connecte automatiquement au VPN lorsqu’il contacte le domaine saisi, par exemple, contoso.com.
- **Persistant** : par défaut, toutes les règles de la table de stratégie de résolution de noms (NRPT) sont actives tant que l’appareil est connecté avec ce profil VPN. Lorsque ce paramètre est **Activé** sur une règle NRPT, celle-ci reste active sur l’appareil, même si la connexion VPN est interrompue. La règle tient jusqu'à ce que le profil VPN soit supprimé ou jusqu'à ce que la règle soit supprimée manuellement, ce qui peut être effectuée avec PowerShell.
La page [Paramètres VPN Windows 10](../configuration/vpn-settings-windows-10.md) décrit les paramètres.

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices---1500165---"></a>Utiliser la détection des réseaux approuvés pour les profils VPN sur les appareils Windows 10<!-- 1500165 -->
Avec la détection des réseaux approuvés, vous pouvez empêcher les profils VPN de créer automatiquement une connexion VPN si l’utilisateur se trouve déjà sur un réseau approuvé. Cette mise à jour vous permet d’ajouter des suffixes DNS pour activer la détection des réseaux approuvés sur les appareils exécutant Windows 10 et versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **VPN** comme type de profil).
La page [Paramètres VPN Windows 10](../configuration/vpn-settings-windows-10.md) liste les paramètres VPN actuels.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users---1907917-1063203---"></a>Gérer les appareils Windows Holographic for Business utilisés par plusieurs utilisateurs<!-- 1907917, 1063203 -->
Actuellement, vous pouvez configurer les paramètres de PC partagé sur les appareils Windows 10 et Windows Holographic for Business avec un paramètre OMA-URI personnalisé. Avec cette mise à jour, un nouveau profil est ajouté pour configurer les paramètres d’appareil partagé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Appareil multi-utilisateur partagé**).
Pour en savoir plus sur cette fonctionnalité, accédez à [Paramètres Intune pour gérer les appareils partagés](../configuration/shared-user-device-settings.md).
S’applique à : Windows 10 (et versions ultérieures), Windows Holographic for Business

#### <a name="new-windows-10-update-settings--2626030--2512994----"></a>Nouveaux paramètres de mise à jour de Windows 10<!--2626030  2512994  -->
Pour vos [boucles de mise à jour Windows 10](../protect/windows-update-for-business-configure.md), vous pouvez configurer :
- **Comportement des mises à jour automatiques**  :utilisez une nouvelle option, *Rétablir les valeurs par défaut*, pour restaurer les paramètres de mise à jour automatique d’origine sur un ordinateur Windows 10 exécutant la *mise à jour d’octobre 2018*
- **Empêcher l’utilisateur de suspendre l’installation des mises à jour Windows** : configurez un nouveau paramètre sous Mises à jour logicielles qui vous permet de refuser ou permettre aux utilisateurs de suspendre l’installation des mises à jour dans les *Paramètres* de leurs ordinateurs.

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption---2662949---"></a>Les profils de messagerie iOS peuvent utiliser la signature et le chiffrement S/MIME<!-- 2662949 -->
Vous pouvez créer un profil de messagerie comportant différents paramètres. Cette mise à jour contient des paramètres S/MIME servant à signer et à chiffrer les communications par e-mail sur les appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > **E-mail** comme type de profil).
La page [Paramètres de configuration de la messagerie iOS](../configuration/email-settings-ios.md) liste les paramètres.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Certains paramètres BitLocker prennent en charge l’édition Windows 10 Professionnel<!-- 2727036 -->
Vous pouvez créer un profil de configuration définissant des paramètres Endpoint Protection sur les appareils Windows 10, notamment BitLocker. Cette mise à jour ajoute la prise en charge de l’édition Windows 10 Professionnel pour certains paramètres BitLocker.
Pour afficher ces paramètres de protection, accédez à [Paramètres Endpoint Protection pour Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Le paramètre Configuration des appareils partagés est renommé Message d’écran de verrouillage pour les appareils iOS dans le portail Azure<!-- 2809362 -->
Lors de la création d’un profil de configuration pour des appareils iOS, vous avez la possibilité d’ajouter des paramètres **Configuration des appareils partagés** pour afficher un texte spécifique sur l’écran de verrouillage. Cette mise à jour inclut les modifications suivantes : 
- Les paramètres **Configuration des appareils partagés** sur le Portail Azure sont renommés « Message de l’écran de verrouillage (mode supervisé uniquement) » (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > choisissez **Fonctionnalités de l’appareil** comme type de profil > **Message de l’écran de verrouillage**).
- Lorsque vous ajoutez des messages d’écran de verrouillage, vous pouvez insérer un numéro de série, un nom d’appareil ou toute autre valeur propre à l’appareil comme variable dans **Informations de l’étiquette** et **Note de l’écran de verrouillage**. Par exemple, vous pouvez entrer `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` entre accolades. [Jetons iOS](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) liste les jetons utilisables.
La page [Paramètres d’affichage des messages sur l’écran de verrouillage](../configuration/ios-device-features-settings.md#lock-screen-message) liste les paramètres.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices---2827760--"></a>Nouveaux paramètres de restriction d’appareil App Store, affichage de document, jeux ajoutés aux appareils iOS<!-- 2827760-->
Dans **configuration de l’appareil** > **les profils de** > **créer un profil** > **iOS** pour la plate-forme > **restrictions de l’appareil** pour le type de profil > **magasin d’applications, l’affichage des documents et les**de jeux, les paramètres suivants sont ajoutés : autoriser les applications gérées à écrire des contacts dans des comptes non gérés , accédez à [restrictions des appareils iOS](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices---3201839-3201843---"></a>Nouveaux paramètres de notification, d’indicateurs et de keyguard pour les appareils des propriétaires d’appareils Android Entreprise<!-- 3201839 3201843 -->
Cette mise à jour comporte de nouvelles fonctionnalités pour les propriétaires d’appareils Android pour les entreprises. Pour pouvoir les utiliser, accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Android pour les entreprises** > dans **Type de profil**, choisissez **Propriétaire de l’appareil uniquement** > **Restrictions de l’appareil**.

Les nouvelles fonctionnalités incluent :

- Désactiver l’affichage des notifications système, notamment les appels entrant, les alertes système, les erreurs système, etc.
- Suggérer d’ignorer les tutoriels de démarrage et les conseils sur les applications qui sont ouvertes pour la première fois.
- Désactiver les paramètres avancés de verrouillage du clavier, notamment l’appareil photo, les notifications, le déverrouillage par empreinte digitale, etc.

Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections---3202194---"></a>Les appareils des propriétaires d’appareils Android Entreprise peuvent utiliser des connexions VPN Always On<!-- 3202194 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN Always On sur les appareils Android pour les entreprises des propriétaires d’appareils. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer le VPN Always On dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android pour les entreprises** comme plateforme > **Restrictions de l’appareil** sur Propriétaire de l’appareil uniquement > paramètres **Connectivité**. Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices---3285177---"></a>Nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10<!-- 3285177 --> 
Cette mise à jour comporte un nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10. À l’aide d’un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Windows 10** > dans **Type de profil**, choisissez les paramètres **Restrictions de l’appareil** > **Général**), vous choisissez d’autoriser ou non ce paramètre.
Pour afficher ces paramètres, accédez à [Paramètres de restriction d’appareil Windows 10](../configuration/device-restrictions-windows-10.md).
S’applique à : Windows 10 et versions ultérieures

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview---2055484-----"></a>Utiliser les paramètres recommandés par Microsoft avec les bases de référence de sécurité (préversion publique)<!-- 2055484   -->

Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur peut créer des stratégies de sécurité directement à partir de ces bases de référence, puis les déployer pour ses utilisateurs. Vous pouvez également personnaliser les recommandations en fonction des besoins de votre organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

Cette fonctionnalité étant en préversion publique, les profils créés maintenant ne sont pas déplacés vers les modèles Base de référence de la sécurité qui sont en disponibilité générale. Nous vous déconseillons d’utiliser ces modèles en préversion dans votre environnement de production.

Pour en savoir plus sur les bases de référence de la sécurité, consultez [Créer une base de référence de la sécurité Windows 10 dans Intune](../protect/security-baselines-monitor.md).

Cette fonctionnalité s’applique à : Windows 10 et versions ultérieures

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Les utilisateurs non-administrateurs peuvent activer BitLocker sur des appareils Windows 10 joints à Azure AD<!-- 2147379   -->
Lorsque vous activez les paramètres BitLocker sur des appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **Endpoint Protection** comme type de profil > **Chiffrement Windows**), vous ajoutez des paramètres BitLocker.

Cette mise à jour comprend un nouveau paramètre BitLocker permettant aux utilisateurs standard (non administrateurs) d’activer le chiffrement.

Pour voir les paramètres, accédez à [Paramètres Endpoint Protection pour Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance---2192052--eepublished----"></a>Vérifier la conformité de Configuration Manager<!-- 2192052  eepublished  -->
Cette mise à jour inclut un nouveau paramètre de conformité Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Windows 10 et ultérieur** > **Conformité de Configuration Manager**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide de ce paramètre, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

[Conformité de Configuration Manager](../protect/compliance-policy-create-windows.md#configuration-manager-compliance) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile---2809324-----"></a>Personnaliser le papier peint sur les appareils iOS supervisés à l’aide d’un profil de configuration d’appareil<!-- 2809324   -->
Lorsque vous créez un profil de configuration d’appareil pour des appareils iOS, vous pouvez personnaliser certaines fonctionnalités (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de **papier peint** qui permettent à un administrateur d’utiliser une image .png, .jpg ou .jpeg sur l’écran d’accueil ou l’écran de verrouillage. Ces paramètres de papier peint s’appliquent uniquement aux appareils supervisés. 

Pour obtenir la liste de ces paramètres, consultez [Paramètres des fonctionnalités d’appareil iOS](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available---3594661----"></a>La fonctionnalité Kiosque Windows 10 est en disponibilité générale<!-- 3594661  -->
Dans cette mise à jour, la fonctionnalité Kiosque est en disponibilité générale sur les appareils Windows 10 et ultérieur. Pour voir tous les paramètres que vous pouvez ajouter et configurer, consultez [Paramètres kiosque pour Windows 10 (et ultérieur)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise---3598396-----"></a>Le paramètre Partage de contacts via Bluetooth est supprimé dans Restrictions sur l’appareil > Propriétaire de l’appareil pour Android Entreprise<!-- 3598396   -->
Lorsque vous créez un profil de restrictions d’appareil pour les appareils Android Enterprise, vous disposez d’un paramètre **Partage de contacts via Bluetooth**. Dans cette mise à jour, le paramètre **Partage de contacts via Bluetooth** est supprimé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Restrictions d’appareil > Propriétaire de l’appareil** pour le type de profil > **Général**).

Le paramètre **Partage de contacts via Bluetooth** n’est pas pris en charge pour la gestion du Propriétaire de l’appareil Android Enterprise. Par conséquent, la suppression de ce paramètre n’affectera aucun périphérique ni aucun client, même si ce paramètre est activé et configuré dans votre environnement.

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md).

S’applique à : propriétaire de l’appareil Android Enterprise


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="more-detailed-enrollment-restriction-failure-messaging---3111564---"></a>Messages d’échec de la restriction d’inscription plus détaillés<!-- 3111564 -->
Des messages d’erreur plus détaillés sont disponibles en cas de non-respect des restrictions d’inscription. Pour voir ces messages, accédez à **Intune** > **Résoudre les problèmes** > et consultez la table des échecs d’inscription. Pour plus d’informations, consultez la [liste des échecs d’inscription](help-desk-operators.md#enrollment-failure-reference).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des appareils
#### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices---1574342----"></a>Préversion de la prise en charge des appareils Android complètement gérés appartenant à l’entreprise<!-- 1574342  -->
Intune prend désormais en charge les appareils Android entièrement gérés, un scénario de type « entreprise propriétaire de l’appareil » dans lequel les appareils sont étroitement gérés par le service informatique et affiliés à différents utilisateurs. Les administrateurs pourront ainsi gérer l’ensemble de l’appareil, appliquer un large éventail de contrôles de stratégie non disponibles avec les profils professionnels et imposer aux utilisateurs d’installer les applications sur la version gérée de Google Play. Pour plus d’informations, consultez [Configurer l’inscription d’appareils Android entièrement gérés dans Intune](../enrollment/android-fully-managed-enroll.md) et [Inscrire vos appareils dédiés ou entièrement gérés](../enrollment/android-dedicated-devices-fully-managed-enroll.md).  Veuillez noter que cette fonctionnalité est en préversion. Certaines fonctionnalités Intune, telles que les certificats, la conformité et l’Accès conditionnel, ne sont pas actuellement disponibles avec les appareils Android des utilisateurs complètement managés.

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices---1434452---"></a>Prise en charge de la réinitialisation sélective pour les appareils WIP sans inscription<!-- 1434452 -->
WIP-WE (Windows Information Protection Without Enrollment) permet aux clients de protéger leurs données d’entreprise sur des appareils Windows 10 sans nécessiter une inscription complète à MDM. Une fois les documents protégés par une stratégie WIP-WE, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie WIP-WE. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="tenant-status-dashboard---1124854---"></a>Tableau de bord État du locataire<!-- 1124854 -->
La nouvelle [page État du locataire](tenant-status.md) fournit un emplacement unique où vous pouvez voir l’état et les détails associés de votre locataire.  Le tableau de bord est divisé en quatre zones :
- **Détails du locataire** : affiche des informations telles que le nom et l’emplacement de votre locataire, votre autorité MDM, le nombre total d’appareils inscrits dans votre locataire et le nombre de licences. Cette section liste également la version de service actuelle de votre locataire.
- **État du connecteur** : affiche des informations sur les connecteurs disponibles que vous avez configurés et peut également répertorier ceux que vous n’avez pas encore activés.  
   En fonction de leur état actuel, les connecteurs sont marqués comme Sain, Avertissement ou Non sain. Sélectionnez un connecteur pour extraire et afficher des détails ou configurer des informations supplémentaires associées.
- **Intégrité du service Intune** : affiche des détails sur les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.
- **Actualités Intune** : affiche les messages actifs pour votre locataire. Les messages incluent les éléments tels que des notifications quand votre locataire reçoit les dernières fonctionnalités Intune.  Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10---1488939--"></a>Nouvelle expérience d’aide et de support dans le portail d’entreprise pour Windows 10<!-- 1488939-->
La nouvelle page Aide et support du portail d’entreprise permet aux utilisateurs de résoudre les problèmes et demander de l’aide pour les problèmes liés à l’accès et aux applications. À partir de la nouvelle page, ils peuvent envoyer par e-mail des détails du journal de diagnostic et des erreurs ainsi que rechercher les informations relatives au support technique de leur organisation. Ils y trouveront également une section FAQ avec des liens vers la documentation Intune appropriée.

#### <a name="new-help-and-support-experience-for-intune---3307080---"></a>Nouvelle expérience d’aide et de support pour Intune<!-- #3307080 -->
Nous allons déployer la nouvelle expérience Aide et support sur tous les locataires au cours des prochains jours. Cette nouvelle expérience est disponible pour Intune et est accessible quand vous utilisez les panneaux Intune dans le [portail Azure](https://portal.azure.com/).
Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs. En plus de recevoir une aide spécifique à chaque problème, vous utilisez le nouveau workflow de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone. Cette nouvelle expérience remplace l’expérience Aide et support précédente incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support.
Pour plus d’informations, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services---3762211----"></a>Nouveaux journaux des opérations et possibilité d’envoyer des journaux aux services Azure Monitor<!-- 3762211  -->
Intune propose une journalisation d’audit intégrée qui assure le suivi des événements lorsque des modifications sont apportées. Cette mise à jour inclut de nouvelles fonctionnalités de journalisation, notamment les suivantes : 
- Journaux des opérations (préversion) qui présentent des détails sur les utilisateurs et les appareils inscrits, notamment les tentatives qui ont abouti et celles qui ont échoué.
- Les journaux d’audit et les journaux des opérations peuvent être envoyés à Azure Monitor, notamment aux comptes de stockage, aux hubs d’événements et à Log Analytics. Ces services vous permettent de stocker et d’utiliser des analyses comme Splunk et QRadar, ainsi que d’obtenir des visualisations de vos données de journalisation.

[Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](../review-logs-using-azure-monitor.md) fournit plus d’informations sur cette fonctionnalité.

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device---2687509----"></a>Ignorer des autres écrans de l’Assistant Configuration sur un appareil DEP iOS<!-- 2687509  -->
En plus des écrans que vous pouvez déjà ignorer, vous pouvez définir des appareils DEP iOS pour ignorer les écrans suivants de l’Assistant Installation quand un utilisateur inscrit l’appareil : Afficher la sonnerie, Confidentialité, Migration Android, Bouton d’accueil, iMessage et FaceTime, Intégration, Surveiller la migration, Apparence, Heure de l’écran, Mise à jour logicielle, Configuration SIM.
Pour choisir quels écrans ignorer, accédez à **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton > **Profils** > choisissez un profil > **Propriétés** > **Personnalisation de l’Assistant Configuration** > choisissez **Masquer** pour tous les écrans que vous souhaitez ignorer > **OK**.
Si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple. Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.

#### <a name="android-enterprise-app-we-app-deployment---1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises<!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie de protection des applications sans inscription) non inscrit, vous pouvez désormais utiliser Google Play dans sa version managée pour déployer des applications du Store et des applications métier pour les utilisateurs. Plus précisément, vous pouvez proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle ils n’ont plus besoin d’assouplir la posture de sécurité de leurs appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="scope-tags-for-apps---1081941---"></a>Balises d’étendue pour les applications<!-- 1081941 -->
Vous pouvez créer des étiquettes de délimitation afin de limiter l’accès pour les rôles et applications. Vous pouvez ajouter une étiquette de délimitation à une application afin que seules les personnes avec des rôles ayant également reçu cette étiquette de délimitation aient accès à l’application. Il n’est actuellement pas possible d’attribuer des balises d’étendue aux applications ajoutées à Intune par Google Play géré ou achetées avec le programme d’achat en volume (VPP) Apple (une prise en charge future est planifiée). Pour plus d’informations, consultez [Utiliser des étiquettes de délimitation pour filtrer les stratégies](scope-tags.md).




<!-- ########################## -->
## <a name="december-2018"></a>Décembre 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="updates-for-application-transport-security---748318---"></a>Mises à jour pour Application Transport Security<!-- 748318 -->

Microsoft Intune prend en charge le protocole TLS (Transport Layer Security) 1.2+ pour fournir un chiffrement de qualité, garantir une meilleure sécurisation par défaut et s’aligner avec d’autres services Microsoft comme Microsoft Office 365. Pour répondre à cette exigence, les portails d’entreprise iOS et macOS vont appliquer les impératifs de la fonctionnalité ATS (Application Transport Security) mise à jour d’Apple, celle-ci nécessitant également TLS 1.2+. ATS permet de renforcer la sécurité de toutes les communications d’application sur HTTPS. Ce changement impacte les clients Intune qui utilisent les applications du portail d’entreprise iOS et macOS. Pour plus d’informations, voir le [blog du support Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys---1832174---"></a>Le SDK d’application Intune prendra en charge les clés de chiffrement 256 bits<!-- 1832174 -->
Le kit de développement logiciel (SDK) Intune App pour Android utilise maintenant des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Le kit SDK continuera de prendre en charge les clés 128 bits pour assurer la compatibilité avec le contenu et les applications qui utilisent des versions antérieures du kit SDK.

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices---3503442---"></a>La mise à jour automatique de Microsoft version 4.5.0 doit être appliquée aux appareils macOS<!-- 3503442 -->
Pour continuer à recevoir des mises à jour pour le portail d’entreprise et les applications Office, les appareils macOS gérés par Intune doivent être mis à niveau à l’aide de la mise à jour automatique Microsoft 4.5.0. Il est possible que les utilisateurs disposent déjà de cette version pour leurs applications Office.

### <a name="device-management"></a>Gestion des périphériques

#### <a name="intune-requires-macos-1012-or-later---2827778---"></a>Intune nécessite macOS 10.12 ou une version ultérieure<!-- 2827778 -->
Intune nécessite désormais macOS 10.12 ou une version ultérieure. Les appareils sur lesquels est installée une version macOS antérieure à celle-ci ne peuvent pas utiliser le portail d’entreprise pour s’inscrire auprès d’Intune. Pour recevoir une assistance technique et pour profiter des nouvelles fonctionnalités, les utilisateurs doivent mettre à niveau leur appareil vers macOS 10.12 ou une version ultérieure, mais également mettre à niveau le portail d’entreprise vers la version la plus récente.

<!-- ########################## -->
## <a name="november-2018"></a>Novembre 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices---1281677---"></a>Désinstallation d’applications sur des appareils iOS supervisés appartenant à l’entreprise<!-- 1281677 -->
Vous pouvez supprimer les applications de votre choix sur les appareils iOS supervisés appartenant à l’entreprise. Vous pouvez supprimer une application en ciblant des groupes d’utilisateurs ou des groupes d’appareils ayant le type d’affectation **Désinstaller**. Pour les appareils iOS personnels ou non supervisés, vous êtes toujours limité à la suppression des applications installées à l’aide d’Intune.

#### <a name="downloading-intune-win32-app-content---2617320---"></a>Télécharger du contenu d’applications Win32 Intune<!-- 2617320 -->
Les clients Windows 10 RS3 (et versions ultérieures) téléchargent du contenu d’applications Win32 Intune à l’aide d’un composant d’optimisation de la distribution sur le client Windows 10. L’optimisation de la distribution offre la fonctionnalité pair à pair, activée par défaut. Actuellement, l’optimisation de la distribution peut être configurée par la stratégie de groupe. Pour plus d’informations, voir [Optimisation de la distribution pour Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Menu contenu de l’application et appareil de l’utilisateur final<!-- 2771453 -->
Les utilisateurs finaux peuvent désormais utiliser le menu contextuel sur l’appareil et dans les applications pour déclencher des actions courantes telles que la modification du nom d’un appareil ou la vérification de la conformité.

#### <a name="set-custom-background-in-managed-home-screen-app----3041945---"></a>Définir un arrière-plan personnalisé dans l’application Managed Home Screen <!-- 3041945 -->
Nous ajoutons un paramètre permettant de personnaliser l’apparence de l’arrière-plan de l’application Managed Home Screen sur les appareils Android pour les entreprises en mode plein écran multiapplication.  Pour configurer l’**l’arrière-plan de l’URL personnalisée**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](../configuration/device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply---3104570---"></a>Enregistrement et application d’attributions de stratégies de protection des applications<!-- 3104570 -->
Vous avez maintenant un meilleur contrôle de vos [affectations de stratégies App Protection](../apps/app-protection-policies.md). Lorsque vous sélectionnez *Affectations* afin de définir ou de modifier les affectations d’une stratégie, vous devez **Enregistrer** votre configuration pour que la modification s’applique. Utilisez **Ignorer** pour effacer toutes les modifications apportées sans les enregistrer dans les listes Inclure et Exclure.  Comme il est obligatoire de choisir entre Enregistrer et Ignorer, seuls les utilisateurs souhaités se voient affecter une stratégie App Protection.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later---3174639---"></a>Nouveaux paramètres du navigateur Microsoft Edge pour Windows 10 et versions ultérieures<!-- 3174639 -->
Cette mise à jour comporte de nouveaux paramètres permettant de contrôler et de gérer le navigateur Microsoft Edge sur les appareils. Pour connaître la liste de ces paramètres, voir [Restriction des appareils pour Windows 10 (et versions ultérieures)](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies---3330037---"></a>Prise en charge de nouvelles applications avec des stratégies de protection des applications<!-- 3330037 -->
Vous pouvez maintenant gérer les applications suivantes avec les [stratégies Intune App Protection](../apps/app-protection-policies.md) :
- Stream (iOS)
- To-Do (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Utilisez des stratégies App Protection pour protéger les données d’entreprise et en contrôler le transfert pour ces applications, comme les autres applications gérées par la stratégie Intune. Remarque : Si Flow n’apparaît pas encore dans la console, ajoutez-le lorsque vous créez ou modifiez des stratégies de protection des données. Pour cela, utilisez l’option **+ Plus d’applications** et spécifiez *l’ID d’application* Flow dans le champ d’entrée : *com.microsoft.flow* pour Android et *com.microsoft.procsimo* pour iOS.


### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles--2155106---"></a>Prise en charge d’iOS 12 OAuth dans les profils de messagerie iOS<!--2155106 -->
Les profils de messagerie iOS d’Intune prennent en charge iOS 12 OAuth (Open Authorization). Pour voir cette fonctionnalité, créez un profil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **E-mail** comme type de profil). Vous pouvez également mettre à jour un profil de messagerie iOS existant. Si vous activez OAuth dans un profil qui est déjà déployé sur des utilisateurs, ces derniers sont invités à se réauthentifier et à retélécharger leurs e-mails.

[Profils de messagerie iOS](../configuration/email-settings-ios.md) comprend davantage d’informations sur l’utilisation d’OAuth dans un profil de messagerie.

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios---3259404---"></a>Prise en charge du contrôle d’accès réseau (NAC) pour Citrix SSO pour iOS<!-- 3259404 -->
Citrix a publié une mise à jour de Citrix Gateway pour permettre le contrôle d’accès réseau (NAC) pour Citrix SSO pour iOS dans Intune. Vous pouvez choisir d’inclure un ID d’appareil au sein d’un profil VPN dans Intune, puis d’envoyer (Push) ce profil à vos appareils iOS. Vous devrez installer la dernière mise à jour de Citrix Gateway pour utiliser cette fonctionnalité.

[Configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md#base-vpn-settings) fournit plus d’informations sur l’utilisation du contrôle d’accès réseau, notamment certaines exigences supplémentaires. 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown---1892471---"></a>Les numéros de version et de build iOS et macOS sont affichés<!-- 1892471 -->
Dans **Conformité de l’appareil** > **Conformité de l’appareil**, les versions des systèmes d’exploitation iOS et macOS indiquées peuvent être utilisées dans les stratégies de conformité. Cette mise à jour comporte le numéro de build, configurable pour les deux plateformes.
Quand des mises à jour de sécurité sont publiées, Apple laisse généralement le numéro de version tel quel, mais met à jour le numéro de build. En utilisant le numéro de build dans une stratégie de conformité, vous pouvez facilement vérifier si une mise à jour des vulnérabilités est installée.
Pour utiliser cette fonctionnalité, voir les stratégies de conformité [iOS](../protect/compliance-policy-create-ios.md#device-health) et [macOS](../protect/compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later---2753807---"></a>Les anneaux de mise à jour sont remplacés par les paramètres d’optimisation de la distribution pour Windows 10 et les versions ultérieures<!-- 2753807 -->
L’optimisation de la distribution est un nouveau profil de configuration pour Windows 10 (et versions ultérieures). Cette fonctionnalité simplifie l’expérience de distribution des mises à jour de logiciels aux appareils de l’organisation. Cette mise à jour permet également de fournir les paramètres dans les boucles de mise à jour nouvelles et actuelles à l’aide d’un profil de configuration.
Pour configurer un profil de configuration d’optimisation de la distribution, voir [Paramètres d’optimisation de la distribution de Windows 10 (et versions ultérieures)](../configuration/delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices---2827760---"></a>Ajout de nouveaux paramètres de restriction d’appareil aux appareils iOS et macOS<!-- 2827760 -->
Cette mise à jour comprend de nouveaux paramètres pour vos appareils iOS et macOS qui sont publiés avec iOS 12 :

**Paramètres iOS** : 
- Général : Bloquer la suppression d’applications (mode supervisé uniquement)
- Général : Bloquer le mode USB restreint (mode supervisé uniquement)
- Général : Forcer une date et une heure automatiques (mode supervisé uniquement)
- Mot de passe : Bloquer le remplissage automatique du mot de passe (mode supervisé uniquement)
- Mot de passe : Bloquer les demandes de proximité du mot de passe (mode supervisés uniquement)
- Mot de passe : Bloquer le partage de mot de passe (mode supervisé uniquement)

**Paramètres macOS** : 
- Mot de passe : bloquer le remplissage automatique du mot de passe
- Mot de passe : Bloquer les demandes de proximité du mot de passe
- Mot de passe : bloquer le partage de mot de passe

Pour en savoir plus sur ces paramètres, consultez les paramètres de restriction d’appareil [iOS](../configuration/device-restrictions-ios.md) et [macOS](../configuration/device-restrictions-macos.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview---1048100--"></a>Prise en charge d’Autopilot pour les appareils joints à un domaine Azure Active Directory hybride (préversion)<!-- 1048100-->
Vous pouvez désormais configurer les appareils joints à un domaine Azure Active Directory hybride à l’aide d’Autopilot. Les appareils doivent être joints au réseau de votre organisation afin d’utiliser la fonctionnalité Autopilot hybride. Pour plus d’informations, consultez [Déployer des appareils joints à un domaine Azure AD hybride à l’aide d’Intune et de Windows Autopilot](../enrollment/windows-autopilot-hybrid.md).
Cette fonctionnalité va être lancée parmi la base d’utilisateurs au cours des prochains jours. Vous ne pourrez donc peut-être pas suivre ces étapes tant que la fonctionnalité n’aura pas été lancée pour votre compte.

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Sélectionner les applications suivies dans la page d’état d’inscription<!-- 2531007 -->
Vous pouvez choisir les applications à suivre sur la page d’état de l’inscription. Tant que ces applications ne sont pas installées, l’utilisateur ne peut pas utiliser l’appareil. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number--2595788---"></a>Rechercher un appareil Autopilot par numéro de série<!--2595788 -->
Vous pouvez maintenant rechercher des appareils Autopilot par numéro de série. Pour cela, choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > tapez un numéro de série dans la zone **Rechercher par numéro de série** > appuyez sur Entrée.

#### <a name="track-installation-of-office-proplus--2620217---"></a>Effectuer le suivi de l’installation d’Office ProPlus<!--2620217 -->
Les utilisateurs peuvent suivre la progression de l’installation [d’Office ProPlus](../apps/apps-add-office365.md) sur la [Page d’état de l’inscription](../enrollment/windows-enrollment-status.md). Pour plus d’informations, voir [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low---2237572---"></a>Alertes signalant l’expiration du jeton VPP ou un nombre insuffisant de licences du portail d’entreprise<!-- 2237572 -->
Si vous utilisez le Programme d’achat en volume (VPP) pour préprovisionner le Portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le Portail d’entreprise.

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts--3006133---"></a>Prise en charge du Programme d’inscription des appareils macOS pour les comptes Apple School Manager<!--3006133 -->
Intune prend maintenant en charge l’utilisation du Programme d’inscription des appareils sur les appareils macOS pour les comptes Apple School Manager.  Pour plus d’informations, voir [Inscrire automatiquement des appareils macOS avec Apple School Manager ou le Programme d’inscription des appareils](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="new-intune-device-subscription-sku--3312071--"></a>Nouvelle référence (SKU) d’abonnement d’appareil Intune<!--3312071-->
Pour aider les entreprises à réduire le coût de la gestion des appareils, une nouvelle référence (SKU) d’abonnement basée sur les appareils est désormais disponible. Cette référence (SKU) d’appareil Intune est concédée sous licence par appareil sur une base mensuelle. Les prix varient selon le programme de licence. Vous pouvez l’obtenir directement par le biais du Centre d’administration Microsoft 365 ainsi que par le biais du [Contrat Entreprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), le [Contrat de Fourniture de Produits et de Services Microsoft ](https://www.microsoft.com/licensing/mpsa/default), les [contrats Open Microsoft ](https://partner.microsoft.com/licensing/licensing-agreements) et le [fournisseur de solutions Cloud](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453).

### <a name="device-management"></a>Gestion des périphériques

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes---3041935---"></a>Suspendre temporairement le mode kiosque sur les appareils Android pour apporter des changements<!-- 3041935 -->
Pendant que vous utilisez un appareil Android en mode kiosque multiapplication, un administrateur informatique peut être amené à effectuer des changements sur l’appareil. Cette mise à jour comporte de nouveaux paramètres de mode plein écran multiapplication permettant à un administrateur informatique de suspendre temporairement le mode plein écran à l’aide d’un code PIN et d’accéder à la totalité de l’appareil.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](../configuration/device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices----3042021---"></a>Activer le bouton d’accueil virtuel sur les appareils kiosque Android Entreprise <!-- 3042021 -->
Un nouveau paramètre permet aux utilisateurs d’appuyer sur un bouton programmable de leur appareil pour passer de l’application Managed Home Screen à d’autres applications affectées (et inversement) sur leur appareil en mode kiosque multiapplication. Ce paramètre est particulièrement utile dans les scénarios où l’application en mode kiosque d’un utilisateur ne répond pas correctement au bouton Précédent. Vous allez pouvoir configurer ce paramètre pour les appareils Android à usage unique appartenant à l’entreprise. Pour activer ou désactiver le **bouton d’accueil virtuel**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](../configuration/device-restrictions-android-for-work.md).




<!-- ########################## -->
## <a name="october-2018"></a>Octobre 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="access-to-key-profile-properties-using-the-company-portal-app---772203---"></a>Accès aux propriétés de profil clés à l’aide de l’application Portail d’entreprise<!-- 772203 -->
Les utilisateurs finaux peuvent désormais accéder aux propriétés et aux actions de compte de clé, comme la réinitialisation de mot de passe, à partir de l’application Portail d’entreprise. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios---1248481---"></a>Les claviers tiers peuvent être bloqués par des paramètres APP sur iOS<!-- 1248481 -->
Sur les appareils iOS, les administrateurs Intune peuvent bloquer l’utilisation de claviers tiers lors de l’accès à des données de l’entreprise dans des applications protégées par une stratégie. Quand la stratégie de protection des applications (APP, Application Protection Policy) est configurée pour bloquer les claviers tiers, l’utilisateur de l’appareil reçoit un message la première fois qu’il interagit avec les données de l’entreprise en utilisant un clavier tiers. Toutes les options autres que celles du clavier natif sont bloquées et les utilisateurs de l’appareil ne les voient pas. La boîte de message ne s’affiche qu’une seule fois aux utilisateurs. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices---1248496---"></a>Accès des applications Intune aux comptes d’utilisateurs sur les appareils iOS et Android gérés<!-- 1248496 -->
En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. 

#### <a name="outlook-ios-and-android-app-configuration-policy--1828527---"></a>Stratégie de configuration des applications Outlook pour iOS et Android<!--1828527 -->
Vous pouvez maintenant créer une stratégie de configuration d’application Outlook pour iOS et Android pour les utilisateurs locaux qui utilisent de l’authentification de base avec le protocole ActiveSync. Des paramètres de configuration supplémentaires sont ajoutés au fur et à mesure qu’ils seront activés pour l’application Outlook pour iOS et Android.

#### <a name="office-365-pro-plus-language-packs---1833450---"></a>Modules linguistiques Office 365 Pro Plus<!-- 1833450 -->
En tant qu’administrateur Intune, vous pouvez déployer des langues supplémentaires pour les applications Office 365 Pro Plus gérées par le biais d’Intune. La liste des langues disponibles inclut le **Type** du module linguistique (principal, partiel et de vérification). Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application** du panneau **Ajouter une application**, sélectionnez **Windows 10** sous la **Suite Office 365**. Sélectionnez **Langues** dans le panneau **Paramètres de la suite d’applications**.

#### <a name="windows-line-of-business-lob-apps-file-extensions---1884873---"></a>Extensions de fichier des applications métier Windows<!-- 1884873 -->
Les extensions de fichier des applications métier Windows sont désormais *.msi*, *.appx*, *.appxbundle*, *.msix* et *.msixbundle*. Vous pouvez ajouter une application dans Microsoft Intune en sélectionnant **Applications clientes** > **Applications** > **Ajouter**. Le volet **Ajouter une application** s’affiche et vous permet de sélectionner le **Type d’application**. Pour les applications métier Windows, sélectionnez **Métier** comme type d’application, sélectionnez **Fichier de package d’application**, puis entrez un fichier d’installation avec l’extension appropriée.

#### <a name="windows-10-app-deployment-using-intune---2309001---"></a>Déploiement d’applications Windows 10 à l’aide d’Intune<!-- 2309001 -->
S’appuyant sur la prise en charge existante des applications métier et des applications Microsoft Store pour Entreprises, les administrateurs peuvent utiliser Intune pour déployer la plupart des applications existantes de leur organisation sur les utilisateurs finaux d’appareils Windows 10. Les administrateurs peuvent ajouter, installer et désinstaller des applications pour les utilisateurs de Windows 10 dans un large éventail de formats, tels que les fichiers MSI, Setup.exe ou MSP. Intune évaluera les règles de spécification avant le téléchargement et l’installation, et informera les utilisateurs finaux de l’état ou des exigences de redémarrage par le biais du Centre de maintenance de Windows 10. Cette fonctionnalité permettra aux organisations intéressées de faire basculer cette charge de travail vers Intune et le cloud. Cette fonctionnalité est actuellement en préversion publique, et nous prévoyons d’y ajouter de nouvelles capacités significatives dans les prochains mois. 

#### <a name="app-protection-policy-app-settings-for-web-data---2662995---"></a>Paramètres de stratégie de protection d’application pour les données web<!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android. 

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Menu contenu de l’application et appareil de l’utilisateur final<!-- 2771453 -->
Les utilisateurs finaux peuvent désormais utiliser le menu contextuel sur un appareil et des applications pour déclencher des actions courantes comme le renommage d’un appareil ou de vérification de la conformité. 

#### <a name="windows-company-portal-keyboard-shortcuts---2771518---"></a>Raccourcis clavier du Portail d’entreprise Windows<!-- 2771518 -->
Les utilisateurs finaux peuvent désormais déclencher des actions d’application et d’appareil dans le Portail d’entreprise Windows à l’aide de raccourcis clavier (accélérateurs).

#### <a name="require-non-biometric-pin-after-a-specified-timeout---1506985---"></a>Demander un code PIN non biométrique après le délai spécifié<!-- 1506985 -->
En demandant un code PIN non biométrique après un délai d’expiration spécifié par l’administrateur, Intune offre une sécurité renforcée pour les applications compatibles avec GAM (gestion des applications mobiles) en limitant l’utilisation de l’identification biométrique pour l’accès aux données d’entreprise. Les paramètres affectent les utilisateurs qui s’appuient sur Touch ID (iOS), Face ID (iOS), Android Biometric ou d’autres méthodes d’authentification biométriques à venir pour accéder à leurs applications compatibles APP/GAM. Ces paramètres permettent aux administrateurs Intune d’avoir un contrôle plus précis sur l’accès utilisateur, en supprimant les cas où un appareil avec plusieurs empreintes digitales ou d’autres méthodes d’accès biométriques peut révéler des données d’entreprise à un utilisateur inapproprié. Dans le portail Azure, ouvrez **Microsoft Intune**. Sélectionnez **Applications clientes** > **Stratégies de protection des applications** > **Ajouter une stratégie** > **Paramètres**. Recherchez la section **Accès** pour des paramètres spécifiques. Pour plus d’informations sur les paramètres d’accès, consultez [Paramètres iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) et [Paramètres Android](../apps/app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices---2244713---"></a>Paramètres de transfert de données Intune APP sur des appareils inscrits dans la MDM iOS<!-- 2244713 -->
Vous pouvez séparer le contrôle des paramètres de transfert de données d’Intune APP sur les appareils inscrits à la solution MDM pour iOS de la spécification de l’identité de l’utilisateur inscrit, également appelé UPN (nom d’utilisateur principal). Les administrateurs qui n’utilisent pas IntuneMAMUPN ne verront aucun changement de comportement. Lorsque cette fonctionnalité est disponible, les administrateurs qui utilisent IntuneMAMUPN pour contrôler le comportement du transfert de données sur les appareils inscrits doivent consulter les nouveaux paramètres et mettre à jour leurs paramètres APP si nécessaire.

#### <a name="windows-10-win32-apps---2617325---"></a>Applications Win32 Windows 10<!-- 2617325 -->
Vous pouvez configurer vos applications Win32 pour qu’elles soient installées dans un contexte d’utilisateur individuel, au lieu d’être installées pour tous les utilisateurs de l’appareil.

#### <a name="windows-win32-apps-and-powershell-scripts---2617330---"></a>Applications Win32 Windows et scripts PowerShell<!-- 2617330 -->
Les utilisateurs finaux ne sont plus obligés de se connecter à l’appareil pour installer des applications Win32 ou exécuter des scripts PowerShell. 

#### <a name="troubleshooting-client-app-installation---1363711---"></a>Résolution des problèmes liés à l’installation des applications clientes<!-- 1363711 -->
Vous pouvez résoudre les problèmes d’installation des applications clientes en consultant la colonne intitulée **Installation de l’application** dans le panneau **Résoudre les problèmes**. Pour voir le panneau **Résoudre les problèmes**, accédez au portail Intune, puis sélectionnez **Résoudre les problèmes** sous **Aide et support**.

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Créer des suffixes DNS dans les profils de configuration VPN sur les appareils exécutant Windows 10<!-- 1333668 -->
Lorsque vous créez un profil de configuration d’appareil VPN (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **VPN** pour le type de profil), vous entrez des paramètres DNS. Avec cette mise à jour, vous pouvez également entrer plusieurs **suffixes DNS** dans Intune. Lorsque vous utilisez des suffixes DNS, vous pouvez rechercher une ressource réseau à l’aide de son nom court, au lieu du nom de domaine complet (FQDN). Cette mise à jour vous permet également de modifier l’ordre des suffixes DNS dans Intune.
Les paramètres DNS actuels sont répertoriés dans [Paramètres VPN Windows 10](../configuration/vpn-settings-windows-10.md#dns-settings).
S’applique à : Appareils Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles---1333705---"></a>Prise en charge de VPN Always On pour les profils professionnels d’Android Entreprise<!-- 1333705 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN AlwaysOn sur les appareils d’entreprise Android avec des profils professionnels managés. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer un VPN AlwaysOn on dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Restrictions d’appareil** > **Connectivité**.

#### <a name="issue-scep-certificates-to-user-less-devices---1744554---"></a>Émettre des certificats SCEP aux appareils sans utilisateur<!-- 1744554 -->
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
> - `{{FullyQualifiedDomainName}}` fonctionne uniquement pour Windows et les appareils joints à un domaine. 
> - Lorsque vous spécifiez les propriétés de l’appareil, comme l’IMEI, le numéro de série et le nom de domaine complet dans l’objet ou le SAN pour un certificat d’appareil, n’oubliez pas que ces propriétés peuvent être usurpées par une personne ayant accès à l’appareil. 

Les variables actuelles lors de la création d’un profil de configuration SCEP sont répertoriées dans [Créer un profil de certificat SCEP](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 

S’applique à : Windows 10 (et versions ultérieures) et iOS, compatible avec le Wi-Fi

#### <a name="remotely-lock-uncompliant-devices---2064495---"></a>Verrouiller à distance des appareils non conformes<!-- 2064495 -->
Si un appareil n’est pas conforme, vous pouvez créer une action dans la stratégie de conformité qui verrouille l’appareil à distance. Dans Intune > **Conformité de l’appareil**, créez une stratégie ou sélectionnez une stratégie existante > **Propriétés**. Sélectionnez **Actions en cas de non-conformité** > **Ajouter** et choisissez de verrouiller l’appareil à distance.
Pris en charge sur : 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 et versions ultérieures 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal---2748224---"></a>Améliorations du profil Kiosk Windows 10 et des versions ultérieures dans le portail Azure<!-- 2748224 -->
Cette mise à jour comprend les améliorations suivantes du profil de configuration d’appareil Windows 10 Kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Préversion Kiosk** pour le type de profil) : 
- Actuellement, vous pouvez créer plusieurs profils kiosk sur le même appareil. Avec cette mise à jour, Intune ne prendra en charge qu’un seul profil kiosk par appareil. Si vous avez toujours besoin de plusieurs profils kiosk sur un seul appareil, vous pouvez utiliser un URI personnalisé.
- Dans un profil **Kiosque multi-application**, vous pouvez sélectionner la taille de la vignette d’application et l’ordre de **présentation du menu Démarrer** dans la grille de l’application. Si vous préférez avoir plus de personnalisation, vous pouvez continuer à charger un fichier XML.
- Les paramètres Navigateur Kiosk sont déplacés dans les paramètres **Kiosk**. Actuellement, les paramètres **Navigateur web Kiosk** ont leur propre catégorie dans le portail Azure.
S’applique à : Windows 10 et versions ultérieures

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device----2637704----"></a>Invite PIN lorsque vous modifiez des empreintes digitales ou Face ID sur un appareil iOS <!-- 2637704  -->
Les utilisateurs sont maintenant invités à entrer un code PIN après avoir apporté des modifications biométriques sur leur appareil iOS. Cela inclut les changements apportés aux empreintes digitales ou au Face ID. Le délai de la demande dépend de la configuration du délai d’attente *Revérifier les conditions d’accès requises après (minutes)*.  Si aucun code PIN n’est défini, l’utilisateur est invité à en configurer un. 
 
Cette fonctionnalité est uniquement disponible pour iOS et nécessite la participation d’applications qui intègrent le SDK d’application Intune pour iOS 9.0.1 ou version ultérieure. L’intégration du SDK est nécessaire afin que le comportement puisse être ajouté aux applications ciblées. Cette intégration se produit en continu et repose sur les équipes d’application spécifiques. Certaines applications participantes incluent WXP, Outlook, Managed Browser et Yammer.

#### <a name="network-access-control-support-on-ios-vpn-clients---1333693---"></a>Prise en charge du contrôle d’accès réseau sur les clients VPN iOS<!-- 1333693 -->
Avec cette mise à jour, un nouveau paramètre permet d’activer le NAC (contrôle d’accès réseau) quand vous créez un profil de configuration VPN pour Cisco AnyConnect, F5 Access et Citrix SSO pour iOS. Ce paramètre permet d’inclure l’ID NAC de l’appareil dans le profil VPN. Pour le moment, il n’existe aucun client VPN, ni aucune solution partenaire NAC prenant en charge ce nouvel ID NAC. Toutefois, nous vous tiendrons informés via notre [billet de blog de support](ttps://aka.ms/iOS12_and_vpn) le moment venu.

Pour utiliser NAC, vous devez :
1. Autoriser Intune à inclure des ID d’appareil dans les profils VPN
2. Mettre à jour le logiciel/microprogramme de votre fournisseur NAC, avec l’aide directe de ce dernier

Pour plus d’informations sur ce paramètre dans un profil VPN iOS, consultez [Ajouter des paramètres VPN sur des appareils iOS dans Microsoft Intune](../configuration/vpn-settings-ios.md). Pour plus d’informations sur le contrôle d’accès réseau, consultez [Intégration du NAC (contrôle d’accès réseau) avec Intune](../protect/network-access-control-integrate.md). 

S’applique à : iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile---1818139---"></a>Supprimer un profil de messagerie d’un appareil, même s’il n’y a qu’un seul profil<!-- 1818139 -->
Avant, vous ne pouviez pas supprimer un profil de messagerie d’un appareil *si* celui-ci était le seul profil de messagerie. Avec cette mise à jour, ce comportement change. Maintenant, vous pouvez supprimer un profil de messagerie, même si ce profil de messagerie est le seul sur l’appareil. Pour plus d’informations, consultez [Ajouter des paramètres de messagerie à des appareils à l’aide d’Intune](../configuration/email-settings-configure.md).

#### <a name="powershell-scripts-and-aad---2309469---"></a>Scripts PowerShell et AAD<!-- 2309469 -->
Les scripts PowerShell dans Intune peuvent être ciblés sur les groupes de sécurité des appareils AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nouveau paramètre par défaut « Type de mot de passe obligatoire » pour Android et Android Entreprise<!-- 2649963 -->
Quand vous créez une stratégie de conformité (**Intune** > **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android** ou **Android Entreprise** pour Plateforme > Sécurité du système), la valeur par défaut de **Type de mot de passe obligatoire** change :

De : Paramètre par défaut de l’appareil : Au moins numérique

S’applique à : Android, Android Entreprise

Pour voir ces paramètres, accédez à [Android](../protect/compliance-policy-create-android.md) et [Android Entreprise](../protect/compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile---2662938---"></a>Utiliser une clé prépartagée dans un profil Wi-Fi Windows 10<!-- 2662938 -->
Via cette mise à jour, vous pouvez utiliser une clé prépartagée (PSK) avec le protocole de sécurité WPA/WPA2-Personnel afin d’authentifier un profil de configuration Wi-Fi pour Windows 10. Vous pouvez également spécifier la configuration des coûts d’une connexion réseau limitée pour les appareils dans la mise à jour d’octobre 2018 de Windows 10.

Actuellement, vous devez importer un profil Wi-Fi ou créer un profil personnalisé pour utiliser une clé prépartagée. Les paramètres actuels sont répertoriés dans [Paramètres Wi-Fi pour Windows 10](../configuration/wi-fi-settings-windows.md). 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices---3218390---"></a>Supprimer les certificats PKCS et SCEP de vos appareils<!-- 3218390 -->
Dans certains scénarios, les certificats PKCS et SCEP restaient sur les appareils, même après le retrait d’une stratégie d’un groupe, la suppression d’un déploiement de configuration ou de conformité, ou la mise à jour administrative d’un profil SCEP ou PKCS existant. Cette mise à jour change le comportement. Il existe des scénarios où les certificats PKCS et SCEP sont supprimés des appareils et d’autres scénarios où ces certificats restent sur l’appareil. Pour en savoir plus sur ces scénarios, consultez [Supprimer des certificats SCEP et PKCS dans Microsoft Intune](../protect/remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance---2504381---"></a>Utiliser Gatekeeper sur les appareils macOS à des fins de conformité<!-- 2504381 -->
Cette mise à jour inclut macOS Gatekeeper pour évaluer la conformité des appareils. Pour définir la propriété Gatekeeper, vous devez [ajouter une stratégie de conformité des appareils pour les appareils macOS](../protect/compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot---1558983---"></a>Appliquer le profil Autopilot à des appareils Windows 10 inscrits qui ne sont pas encore inscrits pour Autopilot<!-- 1558983 -->
Vous pouvez appliquer des profils Autopilot à des appareils Win 10 inscrits qui n’ont pas encore été enregistrés dans Autopilot. Dans le profil Autopilot, choisissez l’option **Convertir tous les appareils ciblés vers Autopilot** pour enregistrer automatiquement les appareils non Autopilot dans le service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures. Lorsque l’appareil est désinscrit et réinitialisé, Autopilot le provisionne.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups---2526564---"></a>Créer plusieurs profils Page d’état d’inscription et les attribuer à des groupes Azure AD<!-- 2526564 -->
Vous pouvez maintenant [créer et attribuer](../enrollment/windows-enrollment-status.md) plusieurs profils Page d’état d’inscription aux groupes Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune--2748613--"></a>Migration du Programme d’inscription des appareils vers Apple Business Manager dans Intune<!--2748613-->
Apple Business Manager (ABM) fonctionne dans Intune. Vous pouvez donc mettre à niveau votre compte du Programme d’inscription des appareils (DEP) vers ABM. Le processus est identique dans Intune. Pour mettre à niveau votre compte Apple de DEP vers ABM, accédez à [https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page--2748656--"></a>Onglets de l’état des alertes et des inscriptions dans la page de vue d’ensemble Inscription de l’appareil<!--2748656-->
Les alertes et les échecs d’inscription apparaissent maintenant sous des onglets distincts sur la page de présentation de l’inscription des appareils.

#### <a name="enrollment-abandonment-report---1382924---"></a>Rapport d’abandon de l’inscription<!-- 1382924 -->
Un nouveau rapport contenant des informations détaillées sur les inscriptions abandonnées est disponible sous **Inscription de l’appareil** > **Surveiller**. Pour plus d’informations, consultez le [rapport d’abandon du portail d’entreprise](../enrollment/enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature---2870393---"></a>Nouvelle fonctionnalité Conditions d’utilisation d’Azure Active Directory<!-- 2870393 -->
Azure Active Directory comporte une fonctionnalité relative aux conditions d’utilisation que vous pouvez utiliser à la place des conditions générales Intune existantes. La fonctionnalité Conditions d’utilisation d’Azure AD offre davantage de flexibilité quant aux choix des conditions d’utilisation à afficher et au moment où elles sont affichées, une meilleure prise en charge de la localisation, un meilleur contrôle de l’affichage des conditions générales, ainsi que des fonctionnalités améliorées de création de rapports. La fonctionnalité Conditions d’utilisation d’Azure AD nécessite Azure Active Directory Premium P1, qui fait également partie de la suite Enterprise Mobility + Security E3. Pour en savoir plus, consultez l’article [Gérer les conditions générales de votre entreprise pour l’accès utilisateur](../enrollment/terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support--3188762--"></a>Prise en charge du mode Propriétaire de l’appareil Android<!--3188762-->
Pour l’inscription Samsung Knox Mobile, Intune prend désormais en charge l’inscription d’appareils en mode de gestion Device Owner pour Android. Les utilisateurs sur des réseaux Wi-Fi ou mobiles peuvent s’inscrire en quelques clics quand ils allument leurs appareils pour la première fois. Pour plus d’informations, consultez [Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Gestion des périphériques
#### <a name="new-settings-for-software-updates-----1907869---"></a>Nouveaux paramètres pour les mises à jour logicielles  <!-- 1907869 -->  
- Vous pouvez désormais configurer des notifications pour informer les utilisateurs finaux des redémarrages qui doivent être effectués dans le but de finaliser l’installation des dernières mises à jour logicielles.   
- Vous pouvez désormais configurer un message d’avertissement pour les redémarrages qui seront effectués en dehors des heures de travail, ce qui convient aux scénarios BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id---2075110---"></a>Regrouper les appareils inscrits auprès de Windows Autopilot par ID de corrélation<!-- 2075110 -->
Intune prend désormais en charge le regroupement d’appareils Windows par ID de corrélation en cas d’inscription à l’aide d’[Autopilot pour les appareils existants](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. L’ID de corrélation est un paramètre du fichier de configuration Autopilot. Intune définit automatiquement l’[attribut d’appareil Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) pour qu’il ait la valeur « OfflineAutopilotprofile-<correlator ID> ». Cela permet de créer des groupes dynamiques Azure AD arbitraires en fonction de l’ID de corrélation par le biais de l’attribut enrollmentprofilename pour les inscriptions Autopilot hors connexion. Pour plus d’informations, voir [Windows Autopilot pour les appareils existants](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies---2984657---"></a>Stratégies de protection des applications Intune<!-- 2984657 -->
Les stratégies de protection des applications Intune vous permettent de configurer divers paramètres de protection des données pour des applications protégées Intune, par exemple Microsoft Outlook et Microsoft Word. Nous avons changé l’aspect de ces paramètres pour [iOS](../apps/app-protection-policy-settings-ios.md) et [Android](../apps/app-protection-policy-settings-android.md) afin de faciliter la recherche de paramètres individuels. Il existe trois catégories pour les paramètres de stratégie :
- **Réadressage des données** - Ce groupe comprend les contrôles DLP (protection contre la perte de données), par exemple les restrictions d’opérations consistant à couper, copier, coller et enregistrer sous. Ces paramètres déterminent la manière dont les utilisateurs interagissent avec les données dans les applications.
- **Conditions d’accès** - Ce groupe contient les options de code PIN par application, qui déterminent le mode d’accès de l’utilisateur final aux applications dans un contexte professionnel.  
- **Lancement conditionnel** - Ce groupe contient des paramètres tels que les paramètres minimum du système d’exploitation, la détection d’appareils jailbreakés/rootés, ainsi que les périodes de grâce hors connexion.  
  
La fonctionnalité des paramètres ne change pas, mais il est plus facile de les trouver quand vous utilisez le flux de création de stratégies.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices---2451462----"></a>Restreindre les applications et bloquer l’accès aux ressources d’entreprise sur les appareils Android<!-- 2451462  -->  
Dans **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android** > **Sécurité du système**, il existe un nouveau paramètre dans la section *Sécurité de l’appareil* nommé **Applications restreintes**. Le paramètre **Applications restreintes** utilise une stratégie de conformité pour bloquer l’accès aux ressources d’entreprise si certaines applications sont installées sur l’appareil. L’appareil est considéré comme non conforme jusqu’à ce que les applications restreintes soient supprimées de l’appareil.
S’applique à : 
- Android

### <a name="intune-apps"></a>Applications Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps---1727158---"></a>Intune prend en charge une taille de package maximale de 8 Go pour les applications métier<!-- 1727158 -->
Intune a augmenté la taille maximale de package à 8 Go pour les applications métier. Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app---1916266---"></a>Ajouter une image de marque personnalisée pour l’application du portail d’entreprise<!-- 1916266 -->
En tant qu’administrateur Microsoft Intune, vous pouvez charger une image de marque personnalisée, qui est affichée en tant qu’image d’arrière-plan dans la page de profil de l’utilisateur au sein de l’application Portail d’entreprise iOS. Pour plus d’informations sur la configuration de l’application Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines---2971030---"></a>Intune conserve la langue localisée d’Office lors de la mise à jour d’Office sur les ordinateurs des utilisateurs finaux<!-- 2971030 -->
Quand Intune installe Office sur les machines de vos utilisateurs finaux, ceux-ci obtiennent automatiquement les mêmes modules linguistiques que ceux qu’ils avaient avec les installations .MSI Office précédentes. Pour plus d’informations, consultez [Assigner des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal---3076965---"></a>Nouvelle expérience de support Intune dans le portail de gestion des appareils Microsoft 365<!-- 3076965 -->
Nous lançons une nouvelle expérience utilisateur d’aide et de support pour Intune dans le [portail de Gestion des appareils Microsoft 365]( https://devicemanagement.microsoft.com). Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs.  

En plus de recevoir une aide spécifique à chaque problème, vous pouvez également utiliser le nouveau flux de travail de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone.  

Pour les clients concernés par le lancement, cette nouvelle expérience utilisateur remplace l’expérience actuelle d’aide et de support incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support.  

*Cette nouvelle expérience utilisateur d’aide et de support est en cours de lancement sur certains locataires. Elle est disponible dans le portail de gestion des appareils. Les participants à cette nouvelle expérience sont choisis au hasard parmi les locataires Intune disponibles. De nouveaux locataires vont être ajoutés au fur et à mesure que nous étendrons le lancement.*  

Pour plus d’informations, consultez [Expérience Aide et support](get-support.md#help-and-support-experience) dans Guide pratique pour obtenir un support technique pour Microsoft Intune.  

#### <a name="powershell-module-for-intune--preview-available---951068---"></a>Module PowerShell pour Intune - Préversion disponible<!-- 951068 -->
Un nouveau module PowerShell, qui offre une prise en charge de l’API Intune via Microsoft Graph, est désormais disponible en préversion sur [GitHub](https://aka.ms/intunepowershell). Pour plus d’informations sur l’utilisation de ce module, consultez le fichier README à cet emplacement.

<!-- ########################## -->
## <a name="september-2018"></a>Septembre 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="remove-duplication-of-app-protection-status-tiles---3083391---"></a>Supprimer la duplication des vignettes d’état de protection des applications<!-- 3083391 -->
Les vignettes **Statut de l’utilisateur pour iOS** et **Statut de l’utilisateur pour Android** étaient présentes dans les pages **Applications clientes - Vue d’ensemble** et **Applications clientes - État de protection de l’application**. Les vignettes d’état ont été supprimées de la page **Applications clientes - Vue d’ensemble** pour éviter la duplication. 

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="support-for-more-third-party-certification-authorities-ca---3093107---"></a>Prise en charge de plus d’autorités de certification tierces<!-- 3093107 -->
En utilisant le protocole SCEP (Simple Certificate Enrollment Protocol), vous pouvez maintenant émettre de nouveaux certificats et renouveler des certificats sur les appareils mobiles à l’aide de Windows, iOS, Android et macOS.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="intune-moves-to-support-ios-10-and-later---2454656---"></a>Prise en charge d’iOS 10 et versions ultérieures par Intune<!-- 2454656 -->  
L’inscription à Intune, le Portail d’entreprise et Managed Browser prennent désormais uniquement en charge les appareils iOS exécutant iOS 10 et versions ultérieures. Pour vérifier quels sont les appareils ou utilisateurs concernés dans votre organisation, accédez à Intune dans le portail Azure > **Appareils** > **Tous les appareils**. Filtrez par système d’exploitation, puis cliquez sur **Colonnes** pour afficher les détails de la version du système d’exploitation. Demandez à ces utilisateurs de mettre à niveau leurs appareils vers une version de système d’exploitation prise en charge.  

Si vous avez l’un des appareils répertoriés ci-dessous ou que vous voulez inscrire l’un de ces appareils, sachez qu’il ne prend en charge qu’iOS 9 et versions antérieures.  Pour continuer à accéder au Portail d’entreprise Intune, vous devez mettre à niveau ces appareils pour qu’ils prennent en charge iOS 10 ou version ultérieure :  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ème génération) 
* iPad mini (1ère génération)  

### <a name="device-management"></a>Gestion des périphériques

#### <a name="microsoft-365-device-management-administration-center---3078424---"></a>Centre d’administration Gestion des périphériques Microsoft 365<!-- 3078424 -->
L’une des promesses de Microsoft 365 est la simplification de l’administration, et au fil des années nous avons intégré les services Microsoft 365 backend pour fournir des scénarios de bout en bout tels que l’accès conditionnel Intune et Azure AD. Le nouveau [Centre d’administration Microsoft 365](https://devicemanagement.microsoft.com) est l’endroit où consolider, simplifier et intégrer l’expérience d’administration. L’espace de travail spécialisé pour la gestion des appareils offre un accès aisé à toutes les tâches et les informations de gestion des appareils et des applications dont votre organisation a besoin. Nous pensons qu’il deviendra l’espace de travail cloud principal pour les équipes d’utilisateurs finaux d’enterprise.


<!-- ########################## -->
## <a name="august-2018"></a>Août 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types---1520957---"></a>Prise en charge du tunnel de paquets pour les profils VPN par application iOS pour les types de connexions personnalisés et Pulse Secure<!-- 1520957 -->
Lors de l’utilisation de profils VPN par application iOS, vous pouvez choisir d’utiliser le tunneling de couche application (app-proxy) ou de niveau paquet (packet-tunnel). Ces options sont disponibles avec les types de connexions suivants :
- VPN personnalisé
- Pulse Secure. Si vous ne savez pas quelle valeur utiliser, consultez la documentation de votre fournisseur VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device---1949583---"></a>Différer le moment où les mises à jour logicielles iOS sont affichées sur l’appareil<!-- 1949583 -->
Dans Intune > **Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS**, vous pouvez configurer les jours et heures où vous ne souhaitez pas que les appareils installent des mises à jour. Dans une prochaine mise à jour, vous serez en mesure de différer le moment où une mise à jour logicielle est visiblement indiquée sur l’appareil, entre 1 et 90 jours. 
[Configurer des stratégies de mise à jour iOS dans Microsoft Intune](../protect/software-updates-ios.md) liste les paramètres actuels.

#### <a name="office-365-proplus-version---2213968---"></a>Version d’Office 365 ProPlus<!-- 2213968 -->
Lors de l’affectation des applications Office 365 ProPlus à des appareils Windows 10 avec Intune, vous pouvez sélectionner la version d’Office. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications** > **Ajouter une application**. Sélectionnez ensuite **Suite Office 365 ProPlus (Windows 10)** à partir de la liste déroulante **Type**. Sélectionnez **Paramètres de la suite d’applications** pour afficher le panneau correspondant. Affectez une valeur à **Canal de mise à jour**, par exemple **Tous les mois**. Supprimez éventuellement l’autre version d’Office (msi) des appareils des utilisateurs finaux en sélectionnant **Oui**. Sélectionnez **Spécifique** pour installer une version spécifique de Microsoft Office pour le canal sélectionné sur les appareils des utilisateurs finaux. À ce stade, vous pouvez sélectionner la **Version spécifique** d’Office à utiliser. Les versions disponibles changeront au fil du temps. Par conséquent, quand vous créez un déploiement, les versions disponibles peuvent être plus récentes et ne pas disposer de certaines versions antérieures. Les déploiements actuels continuent de déployer l’ancienne version, mais la liste des versions est en permanence actualisée par canal. Pour plus d’informations, consultez [Présentation des canaux de mise à jour pour Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn---2282852---"></a>Prise en charge du paramètre d’inscription DNS pour VPN Windows 10<!-- 2282852 -->
Avec cette mise à jour, vous pouvez configurer des profils VPN Windows 10 pour inscrire dynamiquement les adresses IP affectées à l’interface VPN auprès du DNS interne, sans avoir besoin d’utiliser des profils personnalisés.
Pour plus d’informations sur les paramètres de profil VPN actuellement disponibles, consultez [Paramètres VPN de Windows 10](../configuration/vpn-settings-windows-10.md).

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name--2652728--"></a>Le nom de fichier du programme d’installation du Portail d’entreprise macOS inclut désormais le numéro de version<!--2652728-->

#### <a name="ios-automatic-app-updates---2729759---"></a>Mises à jour automatiques des applications iOS<!-- 2729759 -->
Les mises à jour automatiques des applications fonctionnent pour les applications sous licence d’appareil et d’utilisateur pour iOS version 11.0 et ultérieure.

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="windows-hello-will-target-users-and-devices---1106609---"></a>Windows Hello cible les utilisateurs et les appareils<!-- 1106609 -->
Quand vous créez une stratégie [Windows Hello Entreprise](../protect/windows-hello.md), elle s’applique à tous les utilisateurs au sein de l’organisation (au niveau locataire). Avec cette mise à jour, la stratégie peut également être appliquée à des utilisateurs ou des appareils spécifiques à l’aide d’une stratégie de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Identity Protection** > **Windows Hello Entreprise**).
Dans le portail Azure d’Intune, la configuration et les paramètres de Windows Hello existent désormais à la fois dans **Inscription de l’appareil** et dans **Configuration de l’appareil**. **Inscription de l’appareil** cible toute l’organisation (au niveau locataire) et prend en charge Windows AutoPilot (OOBE). **Configuration de l’appareil** cible des appareils et des utilisateurs à l’aide d’une stratégie appliquée lors de l’archivage.
Cette fonctionnalité s’applique à :  
- Windows 10 et versions ultérieures
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios---1769858---"></a>Zscaler est une connexion disponible pour les profils VPN sur iOS<!-- 1769858 -->
Quand vous créez un profil de configuration d’appareil VPN iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** >  plateforme **iOS** > type de profil **VPN**), il existe plusieurs types de connexions, notamment Cisco, Citrix et bien plus encore. Cette mise à jour ajoute Zscaler comme type de connexion. 
[Paramètres VPN pour les appareils exécutant iOS](../configuration/vpn-settings-ios.md) liste les types de connexions disponibles.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10---1879077---"></a>Mode FIPS pour les profils Wi-Fi d’entreprise pour Windows 10<!-- 1879077 -->
Vous pouvez désormais activer le mode FIPS (Federal Information Processing Standards) pour les profils Wi-Fi d’entreprise pour Windows 10 dans le portail Azure Intune. Vérifiez que le mode FIPS est activé sur votre infrastructure Wi-Fi si vous l’activez dans vos profils Wi-Fi.
[Paramètres Wi-Fi pour les appareils Windows 10 et ultérieur dans Intune](../configuration/wi-fi-settings-windows.md) vous montre comment créer un profil Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview---1958649---"></a>Contrôle du mode S sur les appareils Windows 10 et versions ultérieures (préversion publique)<!-- 1958649 -->
Avec la mise à jour de cette fonctionnalité, vous pouvez créer un profil de configuration d’appareil qui sort un appareil Windows 10 du mode S ou empêcher les utilisateurs de sortir l’appareil du mode S. Cette fonctionnalité se trouve dans Intune > **Configuration de l’appareil** > **Profils** >  **Windows 10 et ultérieur** > **Mise à niveau d’édition et changement de mode**.
[Présentation de Windows 10 en mode S](https://www.microsoft.com/windows/s-mode) propose d’autres informations sur le mode S.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile---2144658---"></a>Ajout automatique du package de configuration de Windows Defender ATP au profil de configuration<!-- 2144658 -->
Lors de l’utilisation [d’ATP (Advanced Threat Protection) et de l’intégration d’appareils](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile) dans Intune, vous deviez auparavant télécharger un package de configuration et l’ajouter à votre profil de configuration. Avec cette mise à jour, Intune reçoit automatiquement le package du Centre de sécurité Windows Defender et l’ajoute à votre profil.
S’applique à Windows 10 et versions ultérieures.

#### <a name="require-users-to-connect-during-device-setup--2311457--"></a>Exiger que les utilisateurs se connectent pendant la configuration de l’appareil<!--2311457-->
Vous pouvez maintenant définir des profils d’appareil de façon à exiger que l’appareil se connecte à un réseau avant de continuer au-delà de la page Réseau lors de la configuration de Windows 10. Tant que cette fonctionnalité est en préversion, vous avez besoin de Windows Insider build 1809 ou ultérieure pour utiliser ce paramètre.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices---2451462---"></a>Restreindre des applications et bloquer l’accès aux ressources d’entreprise sur les appareils iOS et Android Entreprise<!-- 2451462 -->
Dans **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **iOS** > **Sécurité système**, il existe un nouveau paramètre, **Applications restreintes**. Ce nouveau paramètre utilise une stratégie de conformité pour bloquer l’accès aux ressources d’entreprise si certaines applications sont installées sur l’appareil. L’appareil est considéré comme non conforme jusqu’à ce que les applications restreintes soient supprimées de l’appareil.
S’applique à : iOS

#### <a name="modern-vpn-support-updates-for-ios---2459928-1819876-and-2650856---"></a>Mises à jour de la prise en charge VPN moderne pour iOS<!-- 2459928, 1819876, and 2650856 -->
Cette mise à jour ajoute la prise en charge des clients VPN iOS suivants :
- F5 Access (versions 3.0.1 et ultérieures)
- Citrix SSO
- Palo Alto Networks GlobalProtect versions 5.0 et ultérieure. Également dans cette mise à jour :
- Le type de connexion **Accès F5** existant a été renommé en **Accès F5 hérité** pour iOS.
- Le type de connexion **Palo Alto Networks GlobalProtect** existant est renommé en **Palo Alto Networks GlobalProtect (hérité)** pour iOS.
Les profils existants avec ces types de connexions continuent de fonctionner avec leur client VPN hérité respectif. Si vous utilisez Cisco Legacy AnyConnect, Accès F5 hérité, Citrix VPN ou Palo Alto Networks GlobalProtect version 4.1 et antérieur avec iOS, vous devez passer aux nouvelles applications. Faites-le dès que possible pour vous assurer que l’accès VPN est disponible pour les appareils iOS quand ils effectuent la mise à jour vers iOS 12.
Pour plus d’informations sur iOS 12 et les profils VPN, consultez le [blog de l’équipe du support technique Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal---2469637---"></a>Exporter des stratégies de conformité du portail Azure Classic pour recréer ces stratégies dans le portail Azure Intune<!-- 2469637 -->
Les stratégies de conformité créées dans le portail Azure Classic seront dépréciées. Vous pouvez examiner et supprimer des stratégies de conformité existantes, mais vous ne pouvez pas les mettre à jour. Si vous avez besoin migrer des stratégies de conformité vers le portail Azure Intune actuel, vous pouvez exporter les stratégies sous forme de fichier avec la virgule comme séparateur (fichier *.csv*). Ensuite, utilisez les informations détaillées du fichier pour recréer ces stratégies dans le portail Azure Intune.

> [!IMPORTANT]
> Une fois le portail Azure Classic mis hors service, vous ne pourrez plus accéder à ou afficher vos stratégies de conformité. Veillez donc à exporter et à recréer vos stratégies dans le portail Azure avant la mise hors service du portail Azure Classic.

#### <a name="better-mobile---new-mobile-threat-defense-partner---22662717---"></a>Better Mobile : nouveau partenaire de Mobile Threat Defense<!-- 22662717 -->
Vous pouvez contrôler l’accès des appareils mobiles aux ressources d’entreprise grâce à l’accès conditionnel basé sur une évaluation des risques menée par Better Mobile, une solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in--1067692---"></a>Verrouillage du Portail d’entreprise en mode Application unique jusqu’à la connexion de l’utilisateur<!--1067692 --> 
Vous avez désormais la possibilité d’exécuter le portail d’entreprise en mode Application unique si vous authentifiez un utilisateur via le portail d’entreprise au lieu de l’Assistant Configuration lors de l’inscription DEP. Cette option verrouille l’appareil immédiatement après l’exécution de l’Assistant Configuration afin qu’un utilisateur soit obligé de se connecter pour accéder à l’appareil. Ce processus permet de s’assurer que l’appareil termine l’intégration et qu’il n’est pas laissé orphelin dans un état sans aucun utilisateur lié.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device--1346521---"></a>Attribuer un utilisateur et un nom convivial à un appareil Autopilot<!--1346521 -->
Vous pouvez désormais [affecter un utilisateur à un appareil Autopilot spécifique](../enrollment/enrollment-autopilot.md). Les administrateurs pourront également donner des noms conviviaux pour accueillir l’utilisateur lors de la configuration de leur appareil avec Autopilot.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment---1608345---"></a>Utilisation de licences d’appareil VPP pour préprovisionner le Portail d’entreprise lors d’une inscription DEP<!-- 1608345 -->
Vous pouvez maintenant utiliser des licences d’appareil du programme d’achat en volume (VPP, Volume Purchase Program) pour préprovisionner le portail d’entreprise pendant les inscriptions au Programme d’inscription des appareils (DEP, Device Enrollment Program). Pour ce faire, quand vous [créez ou modifiez un profil d’inscription](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), spécifiez le jeton VPP que vous souhaitez utiliser pour installer le portail d’entreprise. Assurez-vous que votre jeton n’expire pas et que vous avez suffisamment de licences pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune pousse le Portail d’entreprise de l’App Store à la place (un identifiant Apple vous sera demandé).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning---2237634---"></a>Confirmation obligatoire pour supprimer un jeton VPP utilisé pour le préprovisionnement du Portail d’entreprise<!-- 2237634 -->
Une confirmation est maintenant obligatoire pour supprimer un jeton VPP (Volume Purchase Program) si celui-ci est utilisé pour approvisionner préalablement le portail d’entreprise lors d’une inscription DEP.

#### <a name="block-windows-personal-device-enrollments---1849498---"></a>Bloquer les inscriptions d’appareils personnels Windows<!-- 1849498 -->
Vous pouvez [bloquer l’inscription des appareils personnels Windows](../enrollment/enrollment-restrictions-set.md) avec la [gestion des appareils mobiles](../enrollment/windows-enroll.md) dans Intune. Les appareils inscrits avec [l’agent de PC Intune](../manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité. Cette fonctionnalité sera déployée dans les prochaines semaines et il est possible que vous ne la voyiez pas immédiatement dans l’interface utilisateur.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile--1849855--"></a>Spécifier des modèles de nom d’ordinateur dans un profil Autopilot<!--1849855-->
Vous pouvez [spécifier un modèle de nom d’ordinateur](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) pour générer et définir le [nom de l’ordinateur](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) lors de l’inscription Autopilot. S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page--1901669---"></a>Pour les profils Windows Autopilot, masquez les options de changement de compte dans la page de connexion de l’entreprise et la page d’erreur de domaine<!--1901669 -->
De [nouvelles options de profil Windows Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) permettent aux administrateurs de masquer les options de changement de compte sur les pages de connexion et d’erreur de domaine de l’entreprise. Pour masquer ces options, il est nécessaire de configurer la marque de société dans Azure Active Directory. S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

### <a name="macos-support-for-apple-device-enrollment-program---747651---"></a>Prise en charge de macOS pour le Programme d’inscription des appareils Apple<!-- 747651 -->
Intune prend maintenant en charge l’inscription d’appareils macOS dans le Programme d’inscription des appareils (DEP) Apple. Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils d’Apple](../enrollment/device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Gestion des périphériques

#### <a name="delete-jamf-devices---2653306--"></a>Supprimer des appareils Jamf<!-- 2653306-->
Vous pouvez supprimer des appareils gérés par JAMF, en accédant à **Appareils** > choisissez l’appareil Jamf > **Supprimer**.

#### <a name="change-terminology-to-retire-and-wipe---2175759---"></a>Modifier la terminologie pour « mettre hors service » et « réinitialiser »<!-- 2175759 -->
Pour être cohérent avec l’API Graph, les termes suivants ont été changés dans l’interface utilisateur et la documentation d’Intune :
- **Supprimer les données d’entreprise** est remplacé par « Mettre hors service »
- **Réinitialisation d’usine** est remplacé par **réinitialiser**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate---297909500--"></a>Boîte de dialogue de confirmation si l’administrateur essaie de supprimer le Certificat Push MDM Apple<!-- 297909500-->
Si quelqu’un tente de supprimer un certificat Push MDM Apple, une boîte de dialogue de confirmation indique le nombre d’appareils iOS et macOS associés. Si le certificat est supprimé, ces appareils doivent être réinscrits.

#### <a name="additional-security-settings-for-windows-installer---2282430---"></a>Paramètres de sécurité supplémentaires pour le programme d’installation de Windows<!-- 2282430 -->
Vous pouvez permettre aux utilisateurs de contrôler les installations d’applications. Si cette fonctionnalité est activée, les installations qui sinon pourraient être arrêtées en raison d’une violation de sécurité sont autorisées à poursuivre leur exécution. Vous pouvez indiquer au programme d’installation de Windows d’utiliser des autorisations élevées quand il installe un programme sur un système. Vous pouvez en outre autoriser l’indexation des éléments de la Protection des informations Windows et le stockage de leurs métadonnées dans un emplacement non chiffré. Quand la stratégie est désactivée, les éléments protégés par la Protection des informations Windows ne sont pas indexés et n’apparaissent pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Les fonctionnalités de ces options sont désactivées par défaut. 

#### <a name="new-user-experience-update-for-the-company-portal-website--2000968---"></a>Nouvelle mise à jour de l’expérience utilisateur du site web Portail d’entreprise<!--2000968 -->
En nous basant sur les commentaires que nous ont envoyés des clients, nous avons ajouté de nouvelles fonctionnalités au site web Portail d’entreprise. Vous allez constater une nette amélioration des fonctionnalités existantes et de la facilité d’utilisation sur vos appareils. Les différentes zones du site, comme les détails de l’appareil, le feedback et le support, ainsi que la vue d’ensemble de l’appareil, bénéficient d’une nouvelle présentation interactive et moderne. Vous verrez également :

- Des flux de travail simplifiés sur toutes les plateformes d’appareil
- Des flux d’identification et d’inscription d’appareil améliorés
- Des messages d’erreur plus utiles
- Un langage plus convivial, avec moins de jargon technique
- La possibilité de partager des liens directs vers les applications
- Des performances améliorées pour les grands catalogues d’applications
- Une meilleure accessibilité pour tous les utilisateurs  

La [documentation du site web Portail d’entreprise Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) a été mise à jour pour refléter ces modifications. Pour voir un exemple des améliorations de l’application, consultez [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](../whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Détection de jailbreak améliorée dans les rapports de conformité<!-- 2198738 -->
Les états du paramètre de détection de jailbreak améliorée apparaissent désormais dans les rapports de conformité de la console d’administration.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="scope-tags-for-policies--1081974---"></a>Étiquettes de délimitation pour les stratégies<!--1081974 -->
Vous pouvez [créer des étiquettes de délimitation](scope-tags.md) pour limiter l’accès aux ressources Intune. Ajoutez une balise d’étendue à une attribution de rôle, puis la balise d’étendue à un profil de configuration. Le rôle a uniquement accès aux ressources avec des profils de configuration qui ont des balises d’étendue correspondantes (ou aucune balise d’étendue).





<!-- ########################## -->
## <a name="july-2018"></a>Juillet 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="line-of-business-lob-app-support-for-macos---1895847---"></a>Prise en charge des applications métier pour macOS<!-- 1895847 -->
Microsoft Intune permet aux applications métier macOS d’être déployées en mode **Obligatoire** ou **Disponible avec inscription**. Pour les utilisateurs finaux, les applications peuvent être déployées en mode **Disponible** à l’aide du Portail d’entreprise pour macOS ou du [site web Portail d’entreprise](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode---2051098---"></a>Prise en charge des applications intégrées iOS pour le mode plein écran<!-- 2051098 -->
En plus des applications du Store et des applications gérées, vous pouvez maintenant sélectionner une application intégrée (par exemple, Safari) qui s’exécute en mode plein écran sur un appareil iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments---2150145---"></a>Modifier vos déploiements d’applications Office 365 Pro Plus<!-- 2150145 -->
En tant qu’administrateur Microsoft Intune, vous avez une plus grande capacité de modification de vos déploiements d’applications Office 365 Pro Plus. En outre, vous n’avez plus à supprimer vos déploiements pour modifier des propriétés de la suite. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications**. Dans la liste des applications, sélectionnez votre suite Office 365 Pro Plus.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available---2744271--"></a>Une mise à jour du Kit de développement logiciel (SDK) Intune pour Android est maintenant disponible<!-- 2744271-->
Une version mise à jour du SDK d’application Intune pour Android est disponible pour prendre en charge la version Android P. Si vous êtes un développeur d’applications et que vous utilisez le SDK Intune pour Android, vous devez installer la version mise à jour du SDK d’application Intune pour garantir que les fonctionnalités Intune au sein de vos applications Android continuent de fonctionner comme prévu sur les appareils Android P. Cette version du SDK d’application Intune fournit un plug-in intégré qui effectue les mises à jour du Kit SDK. Vous n’avez pas besoin de réécrire le code existant qui est intégré. Pour plus d’informations, consultez [SDK Intune pour Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si vous utilisez l’ancien style de génération de badge pour Intune, nous vous recommandons d’utiliser l’icône porte-documents. Pour plus d’informations sur la personnalisation, consultez [ce référentiel GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Améliorations apportées à la synchronisation dans l’application Portail d’entreprise pour Windows  
L’application Portail d’entreprise pour Windows vous permet désormais de lancer une synchronisation directement à partir de la barre des tâches Windows et du menu Démarrer. Cette fonctionnalité est particulièrement utile si votre seule tâche consiste à synchroniser des appareils et à accéder aux ressources d’entreprise. Pour accéder à la nouvelle fonctionnalité, cliquez avec le bouton droit sur l’icône Portail d’entreprise épinglée à votre barre des tâches ou au menu Démarrer. Dans les options de menu (également appelées liste de raccourcis), sélectionnez **Synchroniser cet appareil**. Le portail d’entreprise s’ouvre à la page **Paramètres** et lance la synchronisation. Pour examiner les nouvelles fonctionnalités, consultez [Nouveautés de l’interface utilisateur](../whats-new-app-ui.md).   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nouvelles expériences d’exploration dans l’application Portail d’entreprise pour Windows  
Désormais, quand vous parcourez ou recherchez des applications dans l’application Portail d’entreprise pour Windows, vous pouvez basculer entre la vue **Vignettes** existante et la nouvelle vue **Détails**. La nouvelle vue répertorie les détails des applications, tels que le nom, l’éditeur, la date de publication et l’état d’installation.  

La vue **Installée** de la page **Applications** vous permet de voir les détails concernant les installations d’applications terminées et en cours. Pour voir à quoi ressemble la nouvelle vue, consultez [Nouveautés de l’interface utilisateur](../whats-new-app-ui.md).  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Amélioration de l’expérience de l’application Portail d’entreprise pour les gestionnaires d’inscription d’appareil  
Quand un gestionnaire d’inscription d’appareil se connecte à l’application Portail d’entreprise pour Windows, l’application affiche à présent uniquement l’appareil en cours d’exécution actuel du gestionnaire. Cette amélioration permet de réduire les délais d’attente qui se produisaient auparavant quand l’application essayait d’afficher tous les appareils inscrits par le gestionnaire d’inscription d’appareil.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models----1425689----"></a>Bloquer l’accès à l’application en fonction des modèles et des fournisseurs d’appareils non approuvés <!-- 1425689 ! -->
L’administrateur informatique Intune peut appliquer une liste donnée de fabricants Android et/ou de modèles iOS par le biais de stratégies Intune App Protection. L’administrateur informatique peut fournir une liste de fabricants (séparés par des points-virgules) pour les stratégies Android et une liste de modèles d’appareils pour les stratégies iOS. Les stratégies de protection des applications Intune concernent uniquement Android et iOS. Deux actions distinctes peuvent être effectuées sur cette liste donnée :
- Blocage de l’accès à l’application sur les appareils qui ne figurent pas dans la liste, ou
- Réinitialisation sélective des données d’entreprise sur les appareils qui ne figurent pas dans la liste 

L’utilisateur ne peut pas accéder à l’application cible si les conditions requises par la stratégie ne sont pas remplies. En fonction des paramètres, l’utilisateur peut être bloqué ou une réinitialisation sélective de ses données d’entreprise est effectuée dans l’application. Sur les appareils iOS, cette fonctionnalité nécessite la participation d’applications (comme WXP, Outlook, Managed Browser ou Yammer) pour intégrer le SDK Intune App dans le but d’appliquer cette fonctionnalité avec les applications ciblées. Cette intégration se produit en continu et repose sur les équipes d’application spécifiques. Sur Android, cette fonctionnalité nécessite la version la plus récente du portail d’entreprise. 

Sur les appareils de l’utilisateur final, le client Intune effectue une action sur la base d’une mise en correspondance simple des chaînes spécifiées dans le panneau Intune pour les stratégies de protection d’application. Cela dépend entièrement de la valeur signalée par l’appareil. Par conséquent, il est conseillé à l’administrateur informatique de vérifier que le comportement prévu est exact. Pour ce faire, vous pouvez tester ce paramètre en ciblant différents fabricants d’appareils et modèles sur un petit groupe d’utilisateurs. Dans Microsoft Intune, sélectionnez **Applications clientes** > **Stratégies de protection des applications** pour afficher et ajouter des stratégies de protection des applications. Pour plus d’informations sur les stratégies de protection d’applications, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md) et [Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Intune](../apps/app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build---1734766---"></a>Accès aux builds de préversion du portail d’entreprise macOS<!-- 1734766 -->
À l’aide de Microsoft AutoUpdate, vous pouvez vous inscrire pour recevoir des builds de manière anticipée en rejoignant le programme Insider. L’inscription vous permet d’utiliser le portail d’entreprise mis à jour avant qu’il soit accessible à vos utilisateurs finaux. Pour plus d’informations, consultez le [blog Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices---1497640---"></a>Créer une stratégie de conformité des appareils à l’aide de paramètres de pare-feu sur ses appareils macOS<!-- 1497640 -->
Quand vous créez une stratégie de conformité macOS (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : macOS** > **Sécurité du système**), de nouveaux paramètres **Pare-feu** sont disponibles : 

- **Pare-feu** : configurez la façon dont les connexions entrantes sont traitées dans votre environnement.
- **Connexions entrantes** : vous pouvez **bloquer** toutes les connexions entrantes, à l’exception de celles nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage.
- **Mode furtif** : vous pouvez **activer** le mode furtif pour empêcher l’appareil de répondre aux requêtes de sondage. L’appareil continue de répondre aux requêtes entrantes des applications autorisées.

S’applique à : macOS 10.12 et versions ultérieures

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later---1879077---"></a>Nouveau profil de configuration d’appareils Wi-Fi pour Windows 10 et versions ultérieures<!-- 1879077 -->
Actuellement, vous pouvez importer et exporter des profils Wi-Fi à l’aide de fichiers XML. Cette mise à jour vous permet de créer un profil de configuration d’appareils Wi-Fi directement dans Intune, tout comme dans certaines autres plateformes.

Pour créer le profil, ouvrez **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Wi-Fi**. 

S’applique à Windows 10 et versions ultérieures.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed---2149998---"></a>Kiosque : (obsolète) est grisé et ne peut pas être modifié<!-- 2149998 -->
La fonctionnalité Kiosque (préversion) (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** > **Restrictions d’appareil**) est obsolète et remplacée par [Paramètres Kiosque pour Windows 10 et ultérieur](../configuration/kiosk-settings.md). Avec cette mise à jour, la fonctionnalité **Kiosque (obsolète)** est grisée et il est impossible de changer ou de mettre à jour l’interface utilisateur. 

Pour activer le mode Kiosque, consultez [Paramètres Kiosque pour Windows 10 et ultérieur](../configuration/kiosk-settings.md).

S’applique à Windows 10 et ultérieur, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities---2184013---"></a>Utilisation d’autorités de certification tierces par les API<!-- 2184013 -->
Dans cette mise à jour, une API Java permet l’intégration d’autorités de certification tierces à Intune et SCEP. Ensuite, les utilisateurs pourront ajouter le certificat SCEP à un profil et l’appliqueront aux appareils avec MDM.

Actuellement, Intune prend en charge les [demandes SCEP avec les services de certificats Active Directory](../protect/certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser---2455253---"></a>Basculer pour afficher ou masquer le bouton Terminer la session sur un navigateur kiosque<!-- 2455253 -->
Vous pouvez maintenant configurer les navigateurs Kiosque pour afficher ou non le bouton Terminer la session. Vous pourrez voir la commande dans **Configuration de l’appareil** > **Kiosque (préversion)** > **Navigateur web kiosque**. Si elle est activée, quand un utilisateur clique sur le bouton, l’application demande une confirmation pour terminer la session. Lorsque vous confirmez, le navigateur efface toutes les données de navigation et retourne à l’URL par défaut.

#### <a name="create-an-esim-cellular-configuration-profile---2564077---"></a>Créer un profil de configuration mobile eSIM<!-- 2564077 -->
Dans **Configuration de l’appareil**, vous pouvez créer un profil mobile eSIM. Vous pouvez importer un fichier qui contient les codes d’activation mobiles fournis par votre opérateur mobile. Vous pouvez ensuite déployer ces profils sur vos appareils Windows 10 eSIM LTE, tels que Surface Pro LTE et autres appareils compatibles eSIM.

Vérifiez si vos [appareils prennent en charge les profils eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

S’applique à Windows 10 et versions ultérieures.

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings---1058963-eenotready---"></a>Sélectionner des catégories d’appareils à l’aide des paramètres Accès Professionnel ou Scolaire<!-- 1058963 eenotready --> 
Si vous avez activé le [mappage de groupe d’appareils](../enrollment/device-group-mapping.md), les utilisateurs de Windows 10 seront désormais invités à sélectionner une catégorie d’appareils après l’inscription via le bouton **Se connecter** situé dans **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles---1500307---"></a>Utiliser sAMAccountName en tant que nom d’utilisateur de compte pour les profils de messagerie<!-- 1500307 -->
Vous pouvez utiliser le **SamAccountName** local comme nom d’utilisateur de compte pour les profils de messagerie pour Android, iOS et Windows 10. Vous pouvez également obtenir le domaine à partir de l’attribut `domain` ou `ntdomain` dans Azure Active Directory (Azure AD). Il est également possible d’entrer un domaine statique personnalisé.

Pour utiliser cette fonctionnalité, vous devez synchroniser l’attribut `sAMAccountName` de votre environnement Active Directory local avec Azure AD.

S’applique à [Android](../configuration/email-settings-android.md), [iOS](../configuration/email-settings-ios.md), [Windows 10 et ultérieur](../configuration/email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict---1556983---"></a>Affichage des profils de configuration d’appareil en conflit<!-- 1556983 -->
Dans **Configuration de l’appareil**, vous voyez une liste des profils existants. Avec cette mise à jour, une nouvelle colonne qui fournit des détails sur les profils en conflit a été ajoutée. Vous pouvez sélectionner une ligne en conflit pour voir le paramètre et le profil en conflit. 

Découvrez-en plus sur la [gestion des profils de configuration](../configuration/device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance---2308882---"></a>Nouveaux états pour les appareils dans la conformité des appareils<!-- 2308882 -->
Dans **Conformité de l’appareil** > **Stratégies** > Sélectionner une stratégie > **Vue d’ensemble**, les nouveaux états suivants ont été ajoutés :
- réussi
- erreur
- conflit
- en attente
- non applicable. Une image indiquant le nombre d’appareils d’une autre plateforme est également affichée. Par exemple, si vous regardez un profil iOS, la nouvelle vignette indique le nombre d’appareils non iOS qui sont également attribués à ce profil. Consultez [Stratégies de conformité des appareils](../protect/compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions---2325484---"></a>La conformité de l’appareil prend en charge les solutions antivirus tierces<!-- 2325484 -->
Lorsque vous créez une stratégie de conformité d’appareil (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : Windows 10 et versions ultérieures** > **Paramètres** > **Sécurité système**), de nouvelles options sont disponibles sous **[Sécurité de l’appareil ](../protect/compliance-policy-create-windows.md)**  : 
- **Antivirus** : quand la valeur est définie sur **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 
- **Logiciel anti-espion** : quand la valeur est définie sur **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 

S’applique à : Windows 10 et versions ultérieures 

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate---2404851---"></a>Marquer automatiquement les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile comme « entreprise ».<!-- 2404851 -->
Par défaut, les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile sont maintenant marqués **entreprise** sous **Propriété de l’appareil**. Vous n’avez pas à identifier manuellement les appareils d’entreprise avec leur numéro IMEI ni de série avant de les inscrire à l’aide de l’inscription Knox Mobile.

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens---1853904---"></a>Colonne indiquant les appareils sans profils dans la liste des jetons du programme d’inscription<!-- 1853904 -->
La liste des jetons du programme d’inscription contient une nouvelle colonne qui indique le nombre d’appareils auxquels aucun profil n’a été affecté. Les administrateurs peuvent ainsi affecter aisément des profils à ces appareils avant de les octroyer à des utilisateurs. Pour voir la nouvelle colonne, accédez à **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.

### <a name="device-management"></a>Gestion des périphériques

#### <a name="bulk-delete-devices-on-devices-blade---1793693---"></a>Suppression en bloc d’appareils dans le panneau Appareils<!-- 1793693 -->
Vous pouvez maintenant supprimer plusieurs appareils à la fois dans le panneau Appareils. Choisissez **Appareils** > **Tous les appareils** > sélectionner les appareils à supprimer > **Supprimer**. Pour les appareils qui ne peuvent pas être supprimés, une alerte s’affiche.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work--842873---"></a>Changement des noms Google pour Android for Work et Play for Work<!--842873 -->
Intune a mis à jour la terminologie « Android for Work » pour refléter les changements apportés à la personnalisation de Google. Les termes « Android for Work » et « Play for Work » ne sont plus utilisés. Une terminologie différente est utilisée en fonction du contexte :
- « Android Enterprise » fait référence à la pile de gestion Android moderne globale.
- « Profil professionnel » ou « Propriétaire du profil » fait référence à des appareils BYOD gérés avec des profils professionnels.
- « Google Play géré » fait référence à l’App Store Google.

#### <a name="rules-for-removing-devices---1609459---"></a>Règles de suppression des appareils<!-- 1609459 -->
De nouvelles règles sont disponibles pour vous permettre de supprimer automatiquement les appareils qui n’ont fait l’objet d’aucun archivage pendant un nombre de jours défini par vous-même. Pour voir la nouvelle règle, accédez au volet **Intune**, sélectionnez **Appareils**, puis sélectionnez **Règles de nettoyage d’appareil**.

#### <a name="corporate-owned-single-use-support-for-android-devices---1630973---"></a>Prise en charge des appareils Android à usage unique appartenant à l’entreprise<!-- 1630973 -->

Intune prend désormais en charge les appareils Android hautement gérés, verrouillés et de style kiosque. Cela permet aux administrateurs de verrouiller davantage l’utilisation d’un appareil à une seule application ou à un petit ensemble d’applications, et empêche les utilisateurs d’activer d’autres applications ou d’effectuer d’autres actions sur l’appareil. Pour configurer un appareil en mode kiosque Android, accédez à Intune > **Inscription de l’appareil** > **Inscription Android** > **Inscriptions d’appareils en mode kiosque et tâche**. Pour plus d’informations, consultez [Configurer l’inscription des appareils kiosque Android entreprise](../enrollment/android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded---2203794--"></a>Évaluation par ligne des identificateurs d’appareil d’entreprise dupliqués chargés<!-- 2203794-->
Pendant le chargement d’ID d’appareils d’entreprise, Intune fournit désormais une liste de tous les doublons et vous donne la possibilité de remplacer ou de conserver les informations existantes. Le rapport s’affiche s’il existe des doublons après avoir choisi **Inscription de l’appareil** > **Identificateurs d’appareil d’entreprise** > **Ajouter des identificateurs**. 

#### <a name="manually-add-corporate-device-identifiers---2203803---"></a>Ajouter manuellement des identificateurs d’appareil d’entreprise<!-- 2203803 -->
Vous pouvez désormais ajouter manuellement des identificateurs d’appareil d’entreprise. Dans **Inscription de l’appareil** > **Identificateurs d’appareils d’entreprise** > **Ajouter**. 


<!-- ########################## -->
## <a name="june-2018"></a>Juin 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies---1817882---"></a>Prise en charge mobile Microsoft Edge pour les stratégies de protection des applications Intune<!-- 1817882 -->
Le navigateur Microsoft Edge pour appareils mobiles prend maintenant en charge les stratégies de protection des applications définies dans Intune.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode---1560077----"></a>Récupérer l’ID de modèle utilisateur de l’application associé (AUMID) pour les applications Microsoft Store pour Entreprises en mode plein écran<!-- 1560077 ! -->
Intune peut désormais récupérer les ID de modèle utilisateur d’application (AUMID) pour les applications Microsoft Store pour Entreprises afin de fournir une configuration améliorée du profil kiosque.

Pour plus d’informations sur les applications Microsoft Store pour Entreprises, consultez [Gérer des applications à partir du Microsoft Store pour Entreprises](../apps/windows-store-for-business.md).

#### <a name="new-company-portal-branding-page---1916370---"></a>Nouvelle page de personnalisation du Portail d’entreprise<!-- 1916370 -->
La page de personnalisation du portail d’entreprise a une nouvelle mise en page, de nouveaux messages et de nouvelles info-bulles.


### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="pradeo---new-mobile-threat-defense-partner---1169249---"></a>Pradeo : nouveau partenaire de Mobile Threat Defense<!-- 1169249 -->
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Pradeo, une solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector---1333688---"></a>Utiliser le mode FIPS avec le connecteur NDES Certificate<!-- 1333688 -->
Quand vous installiez le connecteur NDES Certificate sur un ordinateur sur lequel le mode FIPS (Federal Information Processing Standard) est activé, l’émission et la révocation de certificats ne fonctionnaient pas comme prévu. Avec cette mise à jour, la prise en charge de la norme FIPS est incluse avec le connecteur NDES Certificate. 

Cette mise à jour comprend également :

- Le connecteur NDES Certificate nécessite .NET 4.5 Framework, qui est automatiquement inclus avec Windows Server 2016 et Windows Server 2012 R2. Précédemment, .NET 3.5 Framework était la version minimale exigée.
- La prise en charge de TLS 1.2 est incluse avec le connecteur NDES Certificate. Ainsi, si le serveur avec le connecteur NDES Certificate installé prend en charge TLS 1.2, TLS 1.2 est utilisé. Si le serveur ne prend pas en charge TLS 1.2, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

Pour plus d’informations, consultez [Configurer et utiliser des certificats SCEP ](../protect/certificates-scep-configure.md) et [Configurer et utiliser des certificats PKCS](../protect/certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles---1333680----"></a>Prise en charge des profils de VPN Palo Alto Networks GlobalProtect<!-- 1333680 ! -->
Avec cette mise à jour, vous pouvez choisir Palo Alto Networks GlobalProtect comme type de connexion VPN pour les profils VPN dans Intune (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Type de profil** > **VPN**). Dans cette version, les plateformes suivantes sont prises en charge : 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings---1403702---"></a>Ajouts aux paramètres Options de sécurité locales de l’appareil<!-- 1403702 -->
Vous pouvez désormais configurer des paramètres Options de sécurité locales de l’appareil supplémentaires pour les appareils Windows 10. Des paramètres supplémentaires sont disponibles dans les domaines Client réseau Microsoft, Serveur réseau Microsoft, Accès et sécurité réseau, ainsi qu’Ouverture de session interactive. Recherchez ces paramètres dans la catégorie Endpoint Protection quand vous créez une stratégie de configuration d’appareil Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices---1560072----"></a>Activer le mode plein écran sur les appareils Windows 10<!-- 1560072 ! -->
Sur les appareils Windows 10, vous pouvez créer un profil de configuration et activer le mode kiosque (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** > **Restrictions de l’appareil** > **Kiosque**). Dans cette mise à jour, le paramètre **Kiosque (préversion)** est renommé **Kiosque (obsolète)**. **Kiosque (obsolète)** n’est plus recommandé, mais continuera à fonctionner jusqu’à la mise à jour de juillet. **Kiosque (obsolète)** est remplacé par le nouveau type de profil **Kiosque** (**Créer un profil** > **Windows 10** > **Kiosque (préversion)**), qui contiendra les paramètres permettant de configurer des kiosques sur Windows 10 RS4 et ultérieur.

S’applique à Windows 10 et versions ultérieures.

#### <a name="device-profile-graphical-user-chart-is-back---2160133---"></a>Le graphique utilisateur des profils d’appareil est de retour<!-- 2160133 -->
Tout en améliorant les chiffres indiqués sur le graphique des profils d’appareil (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**), le graphique utilisateur avait été supprimé temporairement.

Avec cette mise à jour, le graphique utilisateur est de retour et affiché dans le portail Azure.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication---1165118---"></a>Prise en charge de l’inscription Windows Autopilot sans authentification utilisateur<!-- 1165118 -->
Intune prend désormais en charge l’inscription Windows Autopilot sans authentification utilisateur. Il s’agit d’une nouvelle option dans le profil de déploiement Windows Autopilot, « Mode de déploiement Autopilot », définie sur « Déploiement autonome ».  L’appareil doit exécuter Windows 10 Insider Preview Build 17672 ou une version ultérieure et posséder une puce TPM 2.0 pour effectuer correctement ce type d’inscription. Dans la mesure où aucune authentification utilisateur n’est exigée, vous devez affecter cette option uniquement aux appareils sur lesquels vous avez un contrôle physique.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot---1821766---"></a>Nouveau paramètre de langue/région lors de la configuration OOBE (Out-of-Box Experience) pour AutoPilot<!-- 1821766 -->
Un nouveau paramètre de configuration est disponible pour définir la langue et la région des profils Autopilot pendant l’expérience OOBE (Out of Box Experience). Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="new-setting-for-configuring-device-keyboard---1821768---"></a>Nouveau paramètre de configuration du clavier de l’appareil<!-- 1821768 -->
Un nouveau paramètre sera disponible pour configurer le clavier pour les profils AutoPilot pendant l’expérience OOBE. Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="autopilot-profiles-moving-to-group-targeting---1877935---"></a>Déplacement des profils AutoPilot vers le ciblage de groupe<!-- 1877935 -->
Des profils de déploiement AutoPilot peuvent être affectés à des groupes Azure AD contenant des appareils AutoPilot.

### <a name="device-management"></a>Gestion des périphériques

#### <a name="set-compliance-by-device-location---851881----"></a>Définir la conformité en fonction de l’emplacement d’appareil<!-- 851881 ! -->
Dans certains cas, vous souhaiterez peut-être limiter l’accès aux ressources d’entreprise à un emplacement spécifique, défini par une connexion réseau. Vous pouvez désormais créer une stratégie de conformité (**Conformité de l’appareil** > **Emplacements**) en fonction de l’adresse IP de l’appareil. Si l’appareil bascule en dehors de la plage IP, il ne peut plus accéder aux ressources d’entreprise.

S’applique à : Appareils Android 6.0 et ultérieur, avec l’application Portail d’entreprise mise à jour

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Empêcher l’installation d’applications et d’expériences consommateurs sur les appareils AutoPilot Windows 10 Entreprise RS4<!-- 1621980 -->
Vous pourrez empêcher l’installation d’applications et d’expériences consommateur sur vos appareils AutoPilot Windows 10 Entreprise RS4. Pour voir cette fonctionnalité, accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Plateforme** = **Windows 10 ou version ultérieure** > **Type de profil** = **Restrictions de l’appareil** > **Configurer** > **Windows à la une** > **Fonctionnalités grand public**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates---1732948---"></a>Désinstaller la dernière version à partir de mises à jour logicielles Windows 10<!-- 1732948 -->
Si vous détectez un problème important sur vos machines Windows 10, vous pouvez choisir de désinstaller (restaurer) la dernière mise à jour des fonctionnalités ou la dernière mise à jour qualité. La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil. La désinstallation déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10. Pour les mises à jour des fonctionnalités en particulier, vous pouvez limiter de 2 à 60 jours la durée pendant laquelle une désinstallation de la version la plus récente peut être appliquée. Pour définir des options de désinstallation de mise à jour logicielle, sélectionnez **Mises à jour logicielles** dans le panneau **Microsoft Intune** dans le portail Azure. Sélectionnez ensuite **Anneaux de mise à jour Windows 10** dans le panneau **Mises à jour logicielles**. Vous pouvez alors choisir l’option **Désinstaller** dans la section **Vue d’ensemble**.

#### <a name="search-all-devices-for-imei-and-serial-number---1793685---"></a>Rechercher l’IMEI et le numéro de série dans tous les appareils<!-- 1793685 -->
Vous pouvez désormais rechercher les IMEI et les numéros de série dans le panneau Tous les appareils (l’e-mail, l’UPN, le nom de l’appareil et le nom d’administration restent disponibles). Dans Intune, choisissez **Appareils** > **Tous les appareils** > entrez votre recherche dans la zone de recherche.

#### <a name="management-name-field-will-be-editable---1875989---"></a>Le champ de nom de gestion est modifiable<!-- 1875989 -->
Vous pourrez maintenant modifier le champ de nom de gestion dans le panneau **Propriétés** d’un appareil. Pour modifier ce champ, choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil > **Propriétés**. Vous pouvez utiliser le champ de nom de gestion pour identifier un appareil de manière unique.

#### <a name="new-all-devices-filter-device-category---1878520---"></a>Nouveau filtre Tous les appareils : Catégorie d’appareil<!-- 1878520 -->
Vous pouvez désormais filtrer la liste **Tous les appareils** par catégorie d’appareil. Pour ce faire, choisissez **Appareils** > **Tous les appareils** > **Filtre** > **Catégorie d’appareil**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices---1985547---"></a>Utiliser TeamViewer pour partager l’écran des appareils iOS et MacOS<!-- 1985547 -->
Les administrateurs peuvent désormais se connecter à [TeamViewer](../remote-actions/teamviewer-support.md) et démarrer une session de partage d’écran avec des appareils iOS et macOS. Les utilisateurs d’iPhone, iPad et macOS pourront partager leurs écrans en direct avec tout autre appareil de bureau ou portable. 

#### <a name="multiple-exchange-connector-support---2070451---"></a>Prise en charge de plusieurs connecteurs Exchange<!-- 2070451 -->
Vous n’êtes plus limité à un seul connecteur Microsoft Intune Exchange par locataire. Intune prend désormais en charge plusieurs connecteurs Exchange afin que vous puissiez configurer l’accès conditionnel Intune avec plusieurs organisations Exchange locales.

Avec un connecteur Exchange local Intune, vous pouvez gérer l’accès de l’appareil aux boîtes aux lettres Exchange locales en fonction de l’inscription ou non d’un appareil dans Intune et de sa conformité aux stratégies de conformité Intune. Pour configurer un connecteur, téléchargez le connecteur Exchange local Intune à partir du portail Azure et installez-le sur un serveur de votre organisation Exchange. Dans le tableau de bord Microsoft Intune, choisissez **Accès local**, puis sous **Installation**, choisissez **Connecteur Exchange ActiveSync**. Téléchargez le connecteur Exchange local et installez-le sur un serveur de votre organisation Exchange. Maintenant que vous n’êtes plus limité à un seul connecteur Exchange par client, si vous avez d’autres organisations Exchange, vous pouvez suivre le même processus pour télécharger et installer un connecteur pour chaque organisation Exchange supplémentaire.

#### <a name="new-device-hardware-detail-ccid---2156657---"></a>Nouveaux renseignements sur le matériel : CCID<!-- 2156657 -->
L’information CCID (Chip Card Interface Device) est désormais incluse pour chaque appareil. Pour la voir, choisissez **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel** > vérifiez sous **Détails du réseau**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups---2196803---"></a>Attribuer tous les utilisateurs et tous les appareils en tant que groupes d’étendue<!-- 2196803 -->
Vous pouvez désormais affecter tous les utilisateurs, tous les appareils, ainsi que tous les utilisateurs et appareils dans des groupes d’étendue. Pour ce faire, choisissez **Rôles Intune** > **Tous les rôles** > **Gestionnaire de stratégie et de profils** > **Affectations** > choisissez une affectation > **Étendue (Groupes)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices---2219806---"></a>Informations UDID désormais incluses pour les appareils iOS et macOS<!-- 2219806 -->
Pour voir l’identificateur unique de l’appareil (UDID) pour les appareils iOS et macOS, accédez à **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel**. L’UDID est disponible uniquement pour les appareils d’entreprise (tel que défini sous **Appareils** > **Tous les appareils** > choisissez un appareil > **Propriétés** > **Propriété de l’appareil**).

### <a name="intune-apps"></a>Applications Intune

#### <a name="improved-troubleshooting-for-app-installation---928990---"></a>Amélioration de la résolution des problèmes d’installation des applications<!-- 928990 -->
Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Nous publions une préversion publique de nos fonctionnalités de résolution des problèmes d’application. Vous remarquerez sous chaque appareil un nouveau nœud appelé **Applications gérées**. Il liste les applications qui ont été distribuées via MDM Intune. À l’intérieur du nœud figure une liste d’états d’installations d’applications. Si vous sélectionnez une application, vous verrez la vue de résolution des problèmes de cette application spécifique. Dans la vue de résolution des problèmes, vous verrez le cycle de vie de bout en bout de l’application, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. De plus, si l’installation de l’application a échoué, vous verrez le code d’erreur et un message utile sur la cause de l’erreur. 

#### <a name="intune-app-protection-policies-and-microsoft-edge---1818968---"></a>Stratégies de protection des applications Intune et Microsoft Edge<!-- 1818968 -->
Le navigateur Microsoft Edge pour appareils mobiles (iOS et Android) prend désormais en charge les stratégies de protection des applications de Microsoft Intune. Les utilisateurs d’appareils iOS et Android qui se connectent avec leur compte d’entreprise Azure AD dans l’application Microsoft Edge seront protégés par Intune. Sur les appareils iOS, la stratégie **Exiger un navigateur géré pour le contenu web** permet aux utilisateurs d’ouvrir des liens dans Microsoft Edge quand il est géré.

<!-- ########################## -->
## <a name="may-2018"></a>Mai 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="configuring-your-app-protection-policies---2144597-part-2---"></a>Configuration de vos stratégies de protection des applications<!-- 2144597 Part 2 -->

Dans le portail Azure, au lieu d’accéder au panneau du service Intune App Protection, vous accédez désormais simplement à Intune. Il n’existe plus maintenant qu’un seul emplacement pour les stratégies de protection des applications dans Intune. Notez que toutes vos stratégies de protection des applications se trouvent dans le panneau **Application mobile** d’Intune, sous **Stratégies de protection des applications**. Cette intégration permet de simplifier l’administration de la gestion de votre cloud. Gardez à l’esprit que toutes les stratégies de protection des applications sont déjà dans Intune et que vous pouvez modifier les stratégies d’accès conditionnel que vous avez précédemment configurées. Les stratégies Intune de protection des applications et d’accès conditionnel sont désormais sous **Accès conditionnel**, qui se trouve sous la section **Gérer** du panneau **Microsoft Intune** ou sous la section **Sécurité** du panneau **Azure Active Directory**. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Présentation des stratégies de protection d’application](../apps/app-protection-policy.md)

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles---1553555---"></a>Nécessite l’installation de stratégies, d’applications et de profils de certificat et de réseau<!-- 1553555 -->
Les administrateurs peuvent empêcher les utilisateurs finaux d’accéder à Windows 10 RS4 Desktop jusqu’à ce qu’Intune installe les stratégies, les applications et les profils de certificat et de réseau pendant le provisionnement des appareils AutoPilot. Pour plus d’informations, consultez [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="samsung-knox-mobile-enrollment-support--1112863--"></a>Prise en charge de l’inscription Samsung Knox Mobile<!--1112863-->
Quand vous utilisez Intune avec Samsung Knox Mobile Enrollment (KME), vous pouvez inscrire un grand nombre d’appareils Android appartenant à l’entreprise. Les utilisateurs sur des réseaux Wi-Fi ou mobiles peuvent s’inscrire en quelques clics quand ils allument leurs appareils pour la première fois. En cas d’utilisation de l’application Knox Deployment App, les appareils peuvent être inscrits à l’aide de Bluetooth ou NFC. Pour plus d’informations, consultez [Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner 

#### <a name="requesting-help-in-the-company-portal-for-windows-10---1874137---"></a>Demande d’aide sur l’application Portail d’entreprise pour Windows 10<!-- 1874137 -->
Le portail d’entreprise pour Windows 10 envoie maintenant les journaux d’application directement à Microsoft quand l’utilisateur lance le flux de travail pour obtenir de l’aide sur un problème. Cela facilite le dépannage et la résolution des problèmes portés à l’attention de Microsoft.

<!-- ########################## -->
## <a name="april-2018"></a>Avril 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Prise en charge des codes secrets pour les codes PIN MAM sur Android<!-- 1438086 -->

Les administrateurs Intune peuvent définir une condition de lancement d’application pour appliquer un code secret au lieu d’un code PIN MAM numérique. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Intune prend en charge un code secret comme le code PIN numérique existant, pouvant définir une longueur minimale et autorisant la répétition des caractères et des séquences par le biais de la console d’administration. Cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise sur Android. Cette fonctionnalité est déjà disponible pour iOS.

#### <a name="line-of-business-lob-app-support-for-macos---1473977---"></a>Prise en charge des applications métier pour macOS<!-- 1473977 -->
Microsoft Intune permettra d’installer des applications métier macOS à partir du portail Azure. Vous pourrez ajouter une application métier macOS à Intune après qu’elle a été prétraitée par l’outil disponible dans GitHub. Dans le portail Azure, choisissez **Applications clientes** à partir du panneau **Intune**. Dans le panneau **Applications clientes**, choisissez **Applications** > **Ajouter**. Dans le panneau **Ajouter une application**, sélectionnez **Application métier**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment---1813073---"></a>Intégration des groupes Tous les utilisateurs et Tous les appareils pour l’affectation d’applications aux profils professionnels Android Entreprise<!-- 1813073 -->
Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications aux profils professionnels Android Entreprise. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](../apps/apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users---1947010---"></a>Intune réinstalle les applications nécessaires désinstallées par les utilisateurs<!-- 1947010 -->
Si un utilisateur final désinstalle une application obligatoire, Intune la réinstalle automatiquement en moins de 24 heures au lieu d’attendre le cycle de réévaluation de 7 jours.

#### <a name="update-where-to-configure-your-app-protection-policies---2144597---"></a>Changement de l’endroit où vous configurez vos stratégies de protection d’application<!-- 2144597 -->

Dans le portail Azure, dans le service Microsoft Intune, nous allons vous rediriger temporairement du panneau du service **Intune App Protection** vers le panneau **Application Mobile**. Notez que toutes vos stratégies de protection d’application sont déjà sur le panneau **Application mobile** dans Intune, sous la configuration de l’application. Au lieu d’accéder à Intune App Protection, vous accédez simplement à Intune. En avril 2018, nous mettrons fin à la redirection et nous la supprimerons complètement du panneau du service **Intune App Protection** : il n’y aura alors plus qu’un seul emplacement pour les stratégies de protection d’application dans Intune. 

**Comment cela m’affecte-t-il ?**
Ce changement affecte les clients autonomes et les clients hybrides Intune (Intune avec Configuration Manager). Cette intégration permet de simplifier l’administration de la gestion de votre cloud.

**Que faire pour se préparer à ce changement ?**
Déclarez **Intune** comme favori à la place du panneau du service **Intune App Protection** et familiarisez-vous si nécessaire avec le flux de travail de la stratégie de protection d’application dans le panneau **Application mobile** d’Intune. Nous vous redirigerons pendant une courte période de temps, puis nous supprimerons le panneau **App Protection**. N’oubliez pas que toutes les stratégies de protection des applications sont déjà dans Intune, et que vous pouvez modifier vos stratégies d’accès conditionnel. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Présentation des stratégies de protection d’application](../apps/app-protection-policy.md) 

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group---1449153---"></a>Le graphique des profils d’appareil et la liste d’états affichent l’ensemble des appareils contenus dans un groupe<!-- 1449153 -->
Quand vous configurez un profil d’appareil (**Configuration de l’appareil** > **Profils**), vous choisissez le profil d’appareil, par exemple iOS. Vous affectez ce profil à un groupe qui inclut les appareils iOS et les appareils non-iOS. Le nombre sur le graphique indique que le profil est appliqué aux appareils iOS *et* non-iOS (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**). Quand vous sélectionnez le graphique sous l’onglet **Vue d’ensemble**, la section **État de l’appareil** liste tous les appareils contenus dans le groupe, au lieu des appareils iOS uniquement. 

Avec cette mise à jour, le graphique (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**) affiche uniquement le nombre associé à un profil d’appareil spécifique. Par exemple, si le profil d’appareil de la configuration s’applique aux appareils iOS, le graphique indique uniquement le nombre des appareils iOS. Quand l’utilisateur sélectionne le graphique et ouvre la section **État de l’appareil**, seuls les appareils iOS sont listés.

Le graphique utilisateur est supprimé le temps que cette mise à jour soit effectuée. 

#### <a name="always-on-vpn-for-windows-10--1333666---"></a>VPN Always On pour Windows 10<!--1333666 -->

Actuellement, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) peut être utilisé sur les appareils Windows 10 à l’aide d’un profil de réseau privé virtuel (VPN) personnalisé créé à l’aide d’OMA-URI.

Avec cette mise à jour, les administrateurs peuvent activer les profils VPN Always On pour Windows 10 directement dans Intune au sein du portail Azure. Les profils VPN Always On se connecteront automatiquement :

- À la connexion des utilisateurs à leurs appareils
- Au changement du réseau sur l’appareil
- À la réactivation de l’écran de l’appareil

#### <a name="new-printer-settings-for-education-profiles---1308900---"></a>Nouveaux paramètres d’imprimante pour les profils Éducation<!-- 1308900 -->

Pour les profils Éducation, de nouveaux paramètres sont disponibles sous la catégorie **Imprimantes** : **Imprimantes**, **Imprimante par défaut**, **Ajouter de nouvelles imprimantes**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile--1098984---"></a>Afficher l’ID d’appelant dans un profil personnel - Profil professionnel Android Entreprise<!--1098984 -->
Quand vous utilisez un profil personnel sur un appareil, les utilisateurs finaux ne voient pas forcément les détails relatifs à l’ID d’appelant d’un contact professionnel. 

Avec cette mise à jour, il existe un nouveau paramètre dans **Android Entreprise** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Afficher l’ID d’appelant du contact professionnel dans le profil personnel

Quand ce paramètre est activé (non configuré), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Quand ce paramètre est désactivé, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. 

S’applique à : Appareils Android v6.0 et ultérieur avec un profil professionnel Android

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings--1102252-----from-1802-and-1804--"></a>Nouveaux paramètres Windows Defender Credential Guard ajoutés aux paramètres Endpoint Protection<!--1102252 --><!--from 1802 and 1804-->

Avec cette mise à jour, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuration de l’appareil** > **Profils** > **Endpoint Protection**) présente les paramètres suivants : 

- **Windows Defender Credential Guard** : active Credential Guard avec une sécurité basée sur la virtualisation. L’activation de cette fonctionnalité permet de protéger les informations d’identification au prochain redémarrage quand **Niveau de sécurité de plateforme avec démarrage sécurisé** et **Sécurité basée sur la virtualisation** sont activés. Les options sont les suivantes :
  - **Désactivé** : si l’option **Activé sans verrouillage** est activée dans Credential Guard, cette option désactive Credential Guard à distance.

  - **Activé avec le verrouillage UEFI** : garantit que Credential Guard ne peut pas être désactivé à l’aide d’une clé de Registre ou d’une stratégie de groupe. Pour désactiver Credential Guard après avoir utilisé ce paramètre, vous devez définir la stratégie de groupe sur « Désactivé ». Ensuite, supprimez la fonctionnalité de sécurité de chaque ordinateur, avec un utilisateur physiquement présent. Ces étapes effacent la configuration persistante dans UEFI. Tant que la configuration UEFI persiste, Credential Guard est activé.

  - **Activé sans verrouillage** : permet de désactiver Credential Guard à distance à l’aide d’une stratégie de groupe. Les appareils utilisant ce paramètre doivent exécuter au moins Windows 10 (version 1511).

Les technologies dépendantes suivantes sont automatiquement activées lors de la configuration de Credential Guard : 

- **Activer la sécurité basée sur la virtualisation** : active la sécurité basée sur la virtualisation au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité et nécessite le démarrage sécurisé.
- **Démarrage sécurisé avec accès direct à la mémoire** : active la sécurité basée sur la virtualisation avec le démarrage sécurisé et l’accès direct à la mémoire. La protection DMA nécessite une prise en charge matérielle et n’est activée que sur des appareils configurés correctement. 

#### <a name="use-a-custom-subject-name-on-scep-certificate---2064190---"></a>Utiliser un nom d’objet personnalisé sur le certificat SCEP<!-- 2064190 -->
Vous pouvez utiliser le nom courant **OnPremisesSamAccountName** dans un objet personnalisé sur un profil de certificat SCEP. Par exemple, vous pouvez utiliser `CN={OnPremisesSamAccountName})`.

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles---1098977---"></a>Blocage des appareils photo et des captures d’écran dans les profils professionnels Android Entreprise<!-- 1098977 -->
Vous disposez de deux nouvelles propriétés de blocage au moment de configurer des restrictions d’appareil pour les appareils Android : 
- Appareil photo : bloque l’accès à tous les appareils photo de l’appareil
- Capture d’écran : bloque la capture d’écran et empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée

S’applique aux profils professionnels Android Entreprise.

#### <a name="use-cisco-anyconnect-client-for-ios---1333708---"></a>Utiliser le client Cisco AnyConnect pour iOS<!-- 1333708 -->

Lorsque vous créez un profil VPN pour iOS, deux nouvelles options sont désormais disponibles : **Cisco AnyConnect** et **Cisco Legacy AnyConnect**. Les profils Cisco AnyConnect prennent en charge les versions 4.0.7x et ultérieures. Les profils VPN Cisco AnyConnect pour iOS existants se nomment **Cisco Legacy AnyConnect** et continuent de fonctionner avec Cisco AnyConnect 4.0.5x et les versions antérieures, comme c’est le cas aujourd’hui.

> [!NOTE]
> Ce changement s’applique uniquement à iOS. Il existe toujours une seule option Cisco AnyConnect pour les plateformes Android, macOS et pour les profils professionnels Android Entreprise.


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132--1734567---"></a>Nouvelles étapes d’inscription pour les utilisateurs sur les appareils dotés de macOS High Sierra 10.13.2+<!--1734567 -->
macOS High Sierra 10.13.2 a introduit le concept d’inscription MDM « approuvée par l’utilisateur ». Les inscriptions approuvées permettent à Intune de gérer certains paramètres sensibles au niveau sécurité. Pour plus d’informations, consultez la documentation de prise en charge d’Apple ici : https://support.apple.com/HT208019.

Les appareils inscrits à l’aide du Portail d’entreprise macOS sont considérés comme « non approuvés par l’utilisateur », sauf si l’utilisateur final ouvre les préférences système et fournit une approbation manuellement. À cette fin, le Portail d’entreprise macOS invite désormais les utilisateurs sur macOS 10.13.2 et ultérieur à approuver manuellement leur inscription à la fin du processus d’inscription. La console d’administration Intune indiquera si un appareil inscrit est approuvé par l’utilisateur.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune---2370684---"></a>Les appareils macOS inscrits auprès de Jamf peuvent désormais s’inscrire auprès d’Intune<!-- 2370684 -->
Les versions 1.3 et 1.4 du portail d’entreprise macOS n’ont pas réussi à inscrire les appareils Jamf auprès d’Intune. Ce problème est résolu dans la version 1.4.2 du portail macOS.

#### <a name="updated-help-experience-in-company-portal-app-for-android---1631531---"></a>Mise à jour de l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android<!-- 1631531 -->
Nous avons mis à jour l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android afin de l’harmoniser avec les bonnes pratiques relatives à la plateforme Android. Désormais, quand les utilisateurs rencontrent un problème dans l’application, ils peuvent appuyer sur **Menu** > **Aide** et :
- Charger les journaux de diagnostic à destination de Microsoft.
- Envoyer un e-mail décrivant le problème et indiquant l’ID d’incident à une personne du support de l’entreprise  

Pour découvrir à quoi ressemble la mise à jour de l’expérience utilisateur de l’aide, accédez à [Envoyer des journaux à l’aide de la messagerie](/intune-user-help/send-logs-to-your-it-admin-by-email-android) et [Envoyer les erreurs à Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table---1471783---"></a>Nouveau graphique de tendance des échecs d’inscription et tableau des raisons de ces échecs<!-- 1471783 -->
Dans la page Vue d’ensemble de l’inscription, vous pouvez voir la tendance des échecs d’inscription et les cinq premières causes d’échecs. En cliquant sur le graphique ou le tableau, vous pouvez explorer les détails et trouver des conseils de dépannage, ainsi que des suggestions de correction.


### <a name="device-management"></a>Gestion des périphériques

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated---1629303---"></a>Advanced Threat Protection (Protection avancée contre les menaces) et Intune sont entièrement intégrés<!-- 1629303 -->

[Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indique le niveau de risque des appareils Windows 10. Dans le Centre de sécurité Windows Defender (portail ATP), vous pouvez créer une connexion à Microsoft Intune. Une fois créée, une stratégie de conformité Intune permet de déterminer un niveau de menace acceptable. Si le niveau de menace est dépassé, une stratégie d’accès conditionnel Azure AD (Active Directory) peut bloquer l’accès à différentes applications au sein de votre organisation.

Cette fonctionnalité permet à ATP d’analyser les fichiers, de détecter les menaces et de signaler tout risque sur vos appareils Windows 10.

Consultez [Activer ATP avec accès conditionnel dans Intune](../protect/advanced-threat-protection.md).

#### <a name="support-for-user-less-devices---1637553---"></a>Prise en charge des appareils sans utilisateurs<!-- 1637553 -->
Intune permet d’évaluer la conformité sur un appareil sans utilisateur, comme Microsoft Surface Hub. La stratégie de conformité peut cibler des appareils spécifiques. Ainsi, la conformité, et la non-conformité, peuvent être déterminées pour les appareils auxquels aucun utilisateur n’est associé.

#### <a name="delete-autopilot-devices---1713650---"></a>Supprimer des appareils Autopilot<!-- 1713650 -->
Les administrateurs Intune peuvent [supprimer les appareils AutoPilot](../enrollment/enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience--1832333---"></a>Amélioration de l’expérience de suppression d’appareil<!--1832333 -->
Vous n’avez plus besoin de supprimer les données d’entreprise ou de réinitialiser un appareil aux paramètres d’usine avant de le [supprimer d’Intune](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal).

Pour voir la nouvelle expérience, connectez-vous à Intune et sélectionnez **Appareils** > **Tous les appareils** > nom de l’appareil > **Supprimer**.

Si vous souhaitez toujours la confirmation de réinitialisation/mise hors service, vous pouvez suivre le cycle de vie d’appareil standard en utilisant les commandes **Supprimer les données d’entreprise** et **Réinitialisation aux paramètres d’usine** avant la commande **Supprimer**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode---1947769---"></a>Lire les sons sur iOS en mode Perdu<!-- 1947769 -->
Quand les appareils iOS supervisés sont en [mode Perdu](../remote-actions/device-lost-mode.md) MDM (Mobile Device Management), vous pouvez [lire un son](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Appareils** > **Tous les appareils** > sélectionnez un appareil iOS > **Vue d’ensemble** > **Plus**). La lecture du son se poursuit jusqu’à ce que l’appareil soit retiré du mode Perdu ou qu’un utilisateur désactive le son sur l’appareil. S’applique aux appareils iOS 9.3 et ultérieur.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device--1972804--"></a>Bloquer ou autoriser les résultats web dans les recherches effectuées sur un appareil Intune<!--1972804-->

Les administrateurs peuvent maintenant bloquer les résultats web des recherches effectuées sur un appareil.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure---2172331---"></a>Amélioration des messages d’erreur liés à l’échec du chargement du Certificat Push MDM Apple<!-- 2172331 -->

Le message d’erreur explique que le même identifiant Apple doit être utilisé au moment du renouvellement d’un certificat MDM existant.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines---2216679---"></a>Test du portail d’entreprise pour macOS sur les machines virtuelles<!-- 2216679 -->

Nous avons publié des conseils pour aider les administrateurs informatiques à tester l’application Portail d’entreprise pour macOS sur des machines virtuelles dans Parallels Desktop et VMware Fusion. Découvrez-en plus dans [Inscrire des machines virtuelles macOS à des fins de test](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### <a name="intune-apps"></a>Applications Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios--1412866---"></a>Mise à jour de l’expérience utilisateur de l’application Portail d’entreprise pour iOS<!--1412866 -->
Nous avons publié une mise à jour majeure de l’expérience utilisateur de l’application Portail d’entreprise pour iOS. La mise à jour présente une toute nouvelle conception visuelle qui offre une apparence actualisée. Nous avons conservé les fonctionnalités de l’application, mais amélioré sa facilité d’utilisation et son accessibilité.  

Vous verrez également :
- Prise en charge de l’iPhone X.
- Lancement et chargement plus rapides des applications, pour faire gagner du temps aux utilisateurs.
- Barres de progression supplémentaires pour fournir aux utilisateurs les toutes dernières informations d’état.
- Améliorations de la façon dont les utilisateurs chargent les journaux pour faciliter le signalement des problèmes.  

Pour voir à quoi ressemble la mise à jour, consultez [Nouveautés de l’interface utilisateur de l’application](../whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca---1056954---"></a>Protéger les données Exchange locales à l’aide de la stratégie de protection des applications et de l’accès conditionnel d’Intune<!-- 1056954 -->
Vous pouvez désormais utiliser les fonctionnalités APP (stratégie de protection des applications) et CA (accès conditionnel) d’Intune pour protéger l’accès aux données Exchange locales avec Outlook Mobile. Pour ajouter ou modifier une stratégie de protection des applications dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Stratégies de protection des applications**. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx).


### <a name="user-interface"></a>Interface utilisateur

#### <a name="improved-device-tiles-in-the-windows-10-company-portal--2213364---"></a>Amélioration des vignettes d’appareil dans le portail d’entreprise Windows 10<!--2213364 -->

Les vignettes ont été mises à jour pour être plus accessibles aux utilisateurs malvoyants et plus visibles pour les outils de lecture d’écran.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos---2216677---"></a>Envoyer des rapports de diagnostic dans l’application Portail d’entreprise pour macOS<!-- 2216677 -->
L’application Portail d’entreprise pour les appareils macOS a été mise à jour afin d’améliorer la façon dont les utilisateurs signalent les erreurs relatives à Intune. À partir de l’application Portail d’entreprise, vos collaborateurs peuvent :

- Charger des rapports de diagnostic directement pour l’équipe de développement Microsoft.
- Envoyer par e-mail un ID d’incident à l’équipe du support informatique de votre entreprise.

Pour plus d’informations, consultez [Envoyer les erreurs pour macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10---1195010---"></a>Intune s’adapte au système Fluent Design dans l’application Portail d’entreprise pour Windows 10<!-- 1195010 -->
La [vue de navigation du système Fluent Design](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics) a été ajoutée à l’application Portail d’entreprise pour Windows 10 d’Intune. Le long de l’application, vous remarquerez une liste verticale statique de toutes les pages de niveau supérieur. Cliquez sur n’importe quel lien pour afficher des pages et passer de l’une à l’autre rapidement. Il s’agit de la première d’une série de mises à jour que vous verrez dans le cadre de nos efforts constants pour créer une expérience plus adaptive, empathique et familière dans Intune. Pour voir à quoi ressemble la mise à jour, consultez [Nouveautés de l’interface utilisateur de l’application](../whats-new-app-ui.md).

<!-- ########################## -->
## <a name="march-2018"></a>Mars 2018

### <a name="app-management"></a>Gestion des applications

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune---748789---"></a>Alertes relatives à l’expiration des applications métier iOS pour Microsoft Intune<!-- 748789 -->

Dans le portail Azure, Intune vous alerte quand des applications métier iOS arrivent à expiration. Quand vous chargez une nouvelle version de l’application métier iOS, Intune supprime la notification d’expiration de la liste des applications. Cette notification d’expiration est active uniquement pour les dernières applications métier iOS chargées. Un avertissement apparaît 30 jours avant l’expiration du profil de provisionnement de l’application métier iOS. Une fois que l’expiration a eu lieu, l’état de l’alerte passe à Expiré.

#### <a name="customize-your-company-portal-themes-with-hex-codes--1049561---"></a>Personnaliser vos thèmes de Portail d’entreprise avec des codes hexadécimaux<!--1049561 -->

Vous pouvez personnaliser la couleur du thème des applications Portail d’entreprise à l’aide de codes hexadécimaux. Quand vous entrez votre code hexadécimal, Intune détermine la couleur de texte qui offre le plus haut niveau de contraste entre la couleur de texte et la couleur d’arrière-plan. Vous pouvez voir un aperçu de la couleur du texte et du logo de votre entreprise par rapport à la couleur dans **Applications clientes** > **Portail d’entreprise**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise---1813081---"></a>Inclusion et exclusion d’affectations d’applications en fonction des groupes pour Android Enterprise<!-- 1813081 -->

Android Enterprise (anciennement Android for Work) prend en charge l’inclusion et l’exclusion de groupes, mais ne prend pas en charge les groupes prédéfinis **Tous les utilisateurs** et **Tous les appareils**. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](../apps/apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestion des périphériques

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome---2258071---"></a>Exporter tous les appareils vers des fichiers CSV dans Internet Explorer, Microsoft Edge ou Chrome<!-- 2258071 -->
Dans **Appareils** > **Tous les appareils**, vous pouvez **Exporter** les appareils vers une liste au format CSV. Les utilisateurs Internet Explorer ayant plus de 10 000 appareils peuvent exporter leurs appareils correctement dans plusieurs fichiers. Chaque fichier contient jusqu’à 10 000 appareils.

Les utilisateurs Microsoft Edge et Chrome ayant plus de 30 000 appareils peuvent exporter leurs appareils dans plusieurs fichiers. Chaque fichier contient jusqu’à 30 000 appareils.

La rubrique [Gérer des appareils](../remote-actions/device-management.md) fournit plus de détails sur ce que vous pouvez faire avec les appareils que vous gérez.

#### <a name="new-security-enhancements-in-the-intune-service----1637539---"></a>Nouvelles améliorations de la sécurité dans le service Intune <!-- 1637539 -->   

Nous avons introduit un bouton bascule dans Intune sur Azure, qui permet aux clients autonomes Intune de définir un appareil auquel aucune stratégie n’est affectée comme étant **Conforme** (fonctionnalité de sécurité désactivée) ou **Non conforme** (fonctionnalité de sécurité activée). Cela permet de garantir l’accès aux ressources uniquement après l’évaluation de la conformité de l’appareil.

Cette fonctionnalité vous impacte différemment selon que vous avez déjà affecté ou non des stratégies de conformité.

- Si vous êtes un nouveau compte ou un compte existant, et si vous n’avez affecté aucune stratégie de conformité à vos appareils, le bouton bascule est automatiquement défini sur **Conforme**. La fonctionnalité est désactivée par défaut dans la console. L’impact est inexistant pour l’utilisateur final.
- Si vous êtes un compte existant, et si vous avez des appareils auxquels vous avez affecté une stratégie de conformité, le bouton bascule est automatiquement défini sur **Non conforme**. La fonctionnalité est activée par défaut avec le déploiement de la mise à jour de mars.

Si vous utilisez des stratégies de conformité avec un accès conditionnel, et si cette fonctionnalité est activée, les appareils auxquels aucune stratégie de conformité n’a été affectée sont désormais bloqués par l’accès conditionnel. Les utilisateurs finaux associés à ces appareils, qui étaient autorisés à accéder aux e-mails, perdent leur accès, sauf si vous affectez au moins une stratégie de conformité à tous les appareils.   

Notez que même si l’état par défaut du bouton bascule est affiché dans l’IU avec les mises à jour de mars du service Intune, cet état n’est pas appliqué immédiatement. Les changements apportés au bouton bascule n’ont aucun impact sur la conformité des appareils tant que nous n’activons pas la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Nous vous informerons via le Centre de messages quand nous aurons activé la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Cela peut prendre quelques jours, une fois que la mise à jour de mars aura été appliquée à votre service Intune.

**Informations supplémentaires** : [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection---846515---"></a>Détection de jailbreak améliorée<!-- 846515 -->

La détection de jailbreak améliorée est un nouveau paramètre de conformité qui améliore la manière dont Intune évalue les appareils jailbreakés. Avec ce paramètre, l’appareil s’enregistre plus fréquemment auprès d’Intune, lequel utilise les services de géolocalisation de l’appareil, ce qui impacte la durée de vie de la batterie.

#### <a name="reset-passwords-for-android-o-devices---1238299---"></a>Réinitialiser les mots de passe des appareils Android O<!-- 1238299 -->
Vous pouvez réinitialiser les mots de passe des appareils Android 8.0 inscrits à l’aide des profils professionnels. Quand vous envoyez une demande de réinitialisation de mot de passe à un appareil Android 8.0, cela entraîne la définition d’un nouveau mot de passe de déverrouillage de l’appareil ou d’une vérification du profil managé pour l’utilisateur actuel. La vérification ou le mot de passe est envoyé et prend effet immédiatement.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups--1307012---"></a>Ciblage des stratégies de conformité pour les appareils dans des groupes d’appareils<!--1307012 -->

Vous pouvez appliquer des stratégies de conformité en ciblant des utilisateurs au sein de groupes d’utilisateurs. Avec cette mise à jour, vous pouvez appliquer des stratégies de conformité en ciblant des appareils au sein de groupes d’appareils. Les appareils ciblés dans le cadre de groupes d’appareils ne reçoivent aucune action de conformité.

#### <a name="new-management-name-column---1333586---"></a>Nouvelle colonne Nom de gestion<!-- 1333586 -->
 Une nouvelle colonne nommée **Nom de la gestion** est disponible dans le panneau des appareils. Il s’agit d’un nom généré automatiquement, non modifiable affecté par appareil, reposant sur la formule suivante :
- Nom par défaut pour tous les appareils : <username><em><devicetype></em><enrollmenttimestamp>
- Pour les appareils ajoutés en bloc : <ID_de_package/ID_de_profil><em><DeviceType></em><EnrollmentTime>

Il s’agit d’une colonne facultative dans le panneau Appareils. Elle n’est pas disponible par défaut. Vous pouvez y accéder uniquement via le sélecteur de colonne. Le nom de l’appareil n’est pas affecté par cette nouvelle colonne.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes--1550837---"></a>Les appareils iOS sont invités à entrer un code confidentiel toutes les 15 minutes<!--1550837 -->
Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code PIN toutes les 15 minutes. Les utilisateurs sont continuellement sollicités jusqu’à ce qu’un code PIN soit défini.

#### <a name="schedule-your-automatic-updates--1805514---"></a>Planifier vos mises à jour automatiques<!--1805514 -->
Intune vous permet de contrôler l’installation des mises à jour automatiques à l’aide des [paramètres des anneaux de mise à jour Windows](../protect/windows-update-for-business-configure.md). Avec cette mise à jour, vous pouvez planifier des mises à jour récurrentes : hebdomadaires, quotidiennes et horaires.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate--2221763---"></a>Utiliser un nom unique comme sujet du certificat SCEP<!--2221763 -->
Quand vous créez un profil de certificat SCEP, vous entrez le nom du sujet. Avec cette mise à jour, vous pouvez utiliser le nom unique complet en tant que sujet. Dans **Nom du sujet**, sélectionnez **Personnalisé**, puis entrez `CN={{OnPrem_Distinguished_Name}}`. Pour utiliser la variable `{{OnPrem_Distinguished_Name}}`, veillez à synchroniser l’attribut utilisateur `onpremisesdistingishedname` qui utilise [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) avec Azure AD.

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="enable-bluetooth-contact-sharing---android-for-work--1098983---"></a>Activer le partage de contacts Bluetooth - Android for Work<!--1098983 -->
Par défaut, Android empêche les contacts inclus dans le profil professionnel de se synchroniser avec des appareils Bluetooth. Ainsi, les contacts de profil professionnel ne s’affichent pas sur l’ID de l’appelant des appareils Bluetooth.

Avec cette mise à jour, il existe un nouveau paramètre dans **Android for Work** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Partage de contacts via Bluetooth

L’administrateur Intune peut configurer ces paramètres pour activer le partage. Cette démarche s’avère utile lors de l’appariement d’un appareil avec un appareil Bluetooth de voiture qui affiche l’ID de l’appelant à des fins d’utilisation en mode mains libres. Quand ce paramètre est activé, les contacts de profil professionnel sont affichés. Dans le cas contraire, ils n’apparaissent pas.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source---1690459---"></a>Configurer Gatekeeper pour contrôler la source de téléchargement des applications macOS<!-- 1690459 -->

Vous pouvez configurer Gatekeeper pour protéger vos appareils en contrôlant les sources de téléchargement des applications. Vous pouvez configurer les sources de téléchargement suivantes : **Mac App Store**, **Mac App Store et développeurs identifiés** ou **Partout**. Vous pouvez déterminer si les utilisateurs peuvent installer une application en appuyant de façon prolongée sur la touche Ctrl pour remplacer ces contrôles Gatekeeper.

Ces paramètres se trouvent sous **Configuration de l’appareil** -> **Créer un profil** -> **macOS** -> **Endpoint protection**.

#### <a name="configure-the-mac-application-firewall---1690461---"></a>Configurer le pare-feu d’applications Mac<!-- 1690461 -->

Vous pouvez configurer le pare-feu d’applications Mac. Vous serez ainsi en mesure de contrôler les connexions au niveau de chaque application, plutôt qu’au niveau de chaque port. Il permet ainsi d’empêcher les applications indésirables de contrôler les ports réseau ayant été ouverts pour des applications légitimes, et de profiter d’une protection optimale.

Cette fonctionnalité se trouve sous **Configuration de l’appareil** -> **Créer un profil** -> **macOS** -> **Endpoint protection**.

Une fois le paramètre de coupe-feu activé, vous pouvez configurer le coupe-feu à l’aide de deux stratégies :

- Bloquer toutes les connexions entrantes

   Vous pouvez bloquer toutes les connexions entrantes pour les appareils ciblés. Si vous procédez ainsi, les connexions entrantes sont bloquées pour toutes les applications.

- Autoriser ou bloquer des applications spécifiques

   Vous pouvez autoriser ou bloquer la réception de connexions entrantes pour des applications spécifiques. Vous pouvez également activer le mode furtif de manière à empêcher les réponses aux demandes de détection.

#### <a name="detailed-error-codes-and-messages---1376342---"></a>Codes et messages d’erreur détaillés<!-- 1376342 -->

Dans Configuration de l’appareil, vous trouverez des codes d’erreur et des messages d’erreur plus détaillés. Cette amélioration du compte-rendu permet de voir les paramètres, leur état et les détails relatifs au dépannage.

##### <a name="more-information"></a>Plus d’informations

- Bloquer toutes les connexions entrantes

   La réception de connexions entrantes est bloquée pour tous les services de partage (par exemple, le partage de fichiers et le partage d’écran). Les services système qui sont toujours autorisés à recevoir des connexions entrantes sont :
  - configd : implémente DHCP et d’autres services de configuration réseau
  - mDNSResponder : implémente Bonjour
  - racoon - implémente IPSec

    Pour utiliser les services de partage, assurez-vous que **Connexions entrantes** a la valeur **Non configuré** (pas **Bloquer**).

- Mode furtif

   Activez cette option pour empêcher l’ordinateur de répondre aux demandes de détection. L’ordinateur continue de répondre aux demandes entrantes pour les applications autorisées. Les demandes inattendues, comme ICMP (ping), sont ignorées.

#### <a name="disable-checks-on-device-restart--1805490---"></a>Désactiver les vérifications au redémarrage de l’appareil<!--1805490 -->
Intune vous permet de contrôler la [gestion des mises à jour logicielles](../protect/windows-update-for-business-configure.md). Avec cette mise à jour, la propriété <strong>Vérifications de redémarrage</strong> est disponible et activée par défaut. Pour ignorer les vérifications usuelles qui se produisent au redémarrage d’un appareil (comme les utilisateurs actifs, les niveaux de batterie, etc.), sélectionnez <strong>Ignorer</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings---1746293---"></a>Nouveaux canaux de la préversion Windows 10 Insider disponibles pour les anneaux de déploiement<!-- 1746293 -->
Vous pouvez désormais sélectionner les canaux de maintenance Windows 10 Insider Preview suivants quand vous créez un anneau de déploiement Windows 10 :
- Version Windows Insider &#8208; Rapide
- Version Windows Insider &#8208; Lente
- Publier la version Windows Insider 

Pour plus d’informations sur ces canaux, consultez [Gérer les versions Insider Preview](https://insider.windows.com/for-business-organization-admin/).   
Pour plus d’informations sur la création de canaux de déploiement dans Intune, consultez [Gérer les mises à jour logicielles dans Intune](../protect/windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings---1631893---"></a>Nouveaux paramètres Windows Defender Exploit Guard<!-- 1631893 -->

Six nouveaux paramètres et fonctionnalités étendues sont maintenant disponibles pour la <strong>Réduction de la surface d’attaque</strong> et l’<strong>Accès contrôlé aux dossiers : Protection des dossiers</strong>. Ces paramètres se trouvent ici : Device configuration\Profiles\
Créez profil\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque

|Nom du paramètre  |Options du paramètre  |Description  |
|---------|---------|---------|
|Protection avancée contre les ransomware|Activé, Auditer, Non configuré|Utiliser une protection agressive contre les ransomware.|
|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows|Activé, Auditer, Non configuré|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe).|
|Création de processus à partir des commandes PSExec et WMI|Bloquer, Auditer, Non configuré|Bloquer les créations de processus issues des commandes PSExec et WMI.|
|Processus non approuvés et non signés exécutés à partir d’USB|Bloquer, Auditer, Non configuré|Bloquer les processus non approuvés et non signés exécutés à partir d’USB.|
|Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée|Bloquer, Auditer, Non configuré|Bloque l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de liste approuvée.|

#### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

|              Nom du paramètre               |                                                              Options du paramètre                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protection des dossiers (déjà implémenté) | Non configuré, Activer, Auditer uniquement (déjà implémentées)<br><br> <strong>Nouveau</strong><br>Bloquer la modification du disque, Auditer la modification du disque |             |

Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.<br><br>**Activer** : empêcher les applications non approuvées de modifier ou de supprimer des fichiers dans des dossiers protégés et d’écrire dans des secteurs de disque.<br><br>
**Bloquer la modification du disque uniquement** :<br>Empêcher les applications non approuvées d’écrire dans des secteurs de disque. Les applications non approuvées peuvent toujours modifier ou supprimer des fichiers dans des dossiers protégés.

### <a name="intune-apps"></a>Applications Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview---710595---"></a>Les sites web Azure Active Directory peuvent nécessiter l’application Intune Managed Browser et prendre en charge l’authentification unique pour Managed Browser (préversion publique)<!-- 710595 -->

Avec Azure AD (Azure Active Directory), vous pouvez désormais restreindre l’accès aux sites web pour l’application Intune Managed Browser sur les appareils mobiles. Dans Managed Browser, les données de site web restent sécurisées et séparées des données personnelles de l’utilisateur final. De plus, Managed Browser prend en charge les fonctionnalités d’authentification unique pour les sites protégés par Azure AD. La connexion à Managed Browser ou l’utilisation de Managed Browser sur un appareil avec une autre application gérée par Intune permet à Managed Browser d’accéder à des sites d’entreprise protégés par Azure AD sans que l’utilisateur ait à entrer ses informations d’identification. Cette fonctionnalité s’applique à des sites comme Outlook Web Access (OWA) et SharePoint Online, ainsi qu’à d’autres sites d’entreprise comme les ressources intranet accessibles via le proxy d’application Azure. Pour plus d’informations, consultez [Contrôles d’accès dans l’accès conditionnel d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates--976944---"></a>Mises à jour visuelles de l’application Portail d’entreprise pour Android<!--976944 -->

Nous avons mis à jour l’application Portail d’entreprise pour Android afin de suivre les recommandations de [Material Design](https://material.io/). Vous pouvez voir les images des nouvelles icônes dans l’article [Nouveautés de l’interface utilisateur d’application](../whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved---1874230-eeready--"></a>Inscription par le biais de l’application Portail d’entreprise améliorée<!-- 1874230 eeready-->
Les utilisateurs qui inscrivent un appareil à l’aide du Portail d’entreprise sur Windows 10 (build 1703) et versions ultérieures peuvent désormais effectuer la première étape de l’inscription sans quitter l’application.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists--1725868---"></a>HoloLens et Surface Hub apparaissent désormais dans les listes d’appareils<!--1725868 -->
Nous avons ajouté la prise en charge de l’affichage des appareils HoloLens et Surface Hub inscrits auprès d’Intune dans l’application Portail d’entreprise pour Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks---1488911---"></a>Catégories de livres personnalisées pour les livres électroniques achetés dans le cadre du programme d’achat en volume (VPP)<!-- 1488911 -->
Vous pouvez créer des catégories de livres électroniques personnalisées, puis leur affecter des livres électroniques achetés en volume. Les utilisateurs finaux pourront ensuite voir les nouvelles catégories de livres électroniques et les livres affectés à ces catégories. Pour plus d’informations, consultez [Gérer les applications et les livres achetés en volume avec Microsoft Intune](../apps/vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option---2070166---"></a>Changements de prise en charge de l’option d’envoi de commentaires dans l’application Portail d’entreprise pour Windows<!-- 2070166 -->
À compter du 30 avril 2018, l’option **Envoyer des commentaires** dans l’application Portail d’entreprise pour Windows fonctionne uniquement sur les appareils qui exécutent la Mise à jour anniversaire Windows 10 (1607) et versions ultérieures. L’option d’envoi de commentaires n’est plus prise en charge lors de l’utilisation de l’application Portail d’entreprise pour Windows avec :  
- Windows 10, version 1507  
- Windows 10, version 1511  
- Windows Phone 8.1 

Si votre appareil exécute Windows 10 RS1 ou ultérieur, téléchargez la dernière version de l’application Portail d’entreprise Windows à partir du Store. Si vous exécutez une version non prise en charge, continuez à envoyer des commentaires par le biais des canaux suivants : 
- L’application Hub de commentaires sur Windows 10
- L’adresse e-mail WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings---1631890---"></a>Nouveaux paramètres Windows Defender Application Guard<!-- 1631890 -->

- **Activer l’accélération graphique** : les administrateurs peuvent activer un processeur graphique virtuel pour Windows Defender Application Guard. Ce paramètre permet à l’UC de décharger l’affichage graphique sur l’unité de traitement graphique virtuelle. Cela peut améliorer les performances quand vous utilisez des sites web qui consomment beaucoup de graphiques ou regardez une vidéo au sein du conteneur.

- **SaveFilestoHost** : les administrateurs peuvent autoriser le passage des fichiers depuis Microsoft Edge, qui s’exécute dans le conteneur, vers le système de fichiers hôte. L’activation de ce paramètre permet aux utilisateurs de télécharger des fichiers à partir de Microsoft Edge, dans le conteneur, vers le système de fichiers hôte.

#### <a name="mam-protection-policies-targeted-based-on-management-state---1665993---"></a>Stratégies de protection MAM ciblées en fonction de l’état de gestion<!-- 1665993 -->
Vous pouvez cibler des stratégies MAM en fonction de l’état de gestion de l’appareil :
- **Appareils Android** : vous pouvez cibler des appareils non gérés, des appareils gérés par Intune et des profils d’entreprise Android gérés par Intune (anciennement Android for Work).
- **Appareils iOS** : vous pouvez cibler des appareils non gérés (MAM uniquement) ou des appareils gérés par Intune.

    > [!NOTE]
    > - La prise en charge de cette fonctionnalité par iOS est déployée tout au long du mois d’avril 2018.

Pour plus d’informations, consultez [Cibler des stratégies de protection des applications en fonction de l’état de gestion des appareils](../apps/app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows---1683758---"></a>Améliorations apportées au langage utilisé dans l’application Portail d’entreprise pour Windows<!-- 1683758 -->
Nous avons amélioré le langage utilisé dans le Portail d’entreprise pour Windows 10 pour qu’il soit plus convivial et plus spécifique à votre entreprise. Pour voir nos exemples d’images, consultez [Nouveautés de l’interface utilisateur des applications](../whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy---1440709---"></a>Derniers ajouts à notre documentation sur la confidentialité des utilisateurs<!-- 1440709 -->
Dans le cadre de nos efforts pour donner aux utilisateurs finaux un plus grand contrôle sur la confidentialité de leurs données, nous avons publié des mises à jour de notre documentation expliquant comment afficher et supprimer les données stockées localement par les applications du Portail d’entreprise. Vous pouvez trouver ces mises à jour aux emplacements suivants :

- **Android** : [Guide pratique pour supprimer un appareil Android d’Intune](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, si l’utilisateur a refusé les conditions d’utilisation** : [Supprimer votre appareil de la gestion si vous avez refusé les conditions d’utilisation](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS** : [Supprimer votre appareil iOS d’Intune](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows** : [Supprimer votre appareil Windows d’Intune](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>Février 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685---"></a>Prise en charge de plusieurs comptes DEP/Apple School Manager par Intune<!-- 747685 -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du [Programme d’inscription des appareils (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) ou [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md). Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

#### <a name="see-enrollment-restrictions-per-user---1634444-eeready-wnready---"></a>Afficher les restrictions d’inscription par utilisateur<!-- 1634444 eeready wnready -->
Le panneau **Résoudre les problèmes** vous permet désormais de voir les [restrictions d’inscription](../enrollment/enrollment-restrictions-set.md) en vigueur pour chaque utilisateur. Pour cela, sélectionnez **Restrictions d’inscription** dans la liste **Affectations**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment---747625-eeready---"></a>Nouvelle option pour l’authentification utilisateur dans le cadre de l’inscription en bloc Apple<!-- 747625 eeready -->

> [!NOTE]
> Les nouveaux locataires la verront tout de suite. Pour les locataires existants, cette fonctionnalité sera déployée en avril. Tant que ce déploiement ne sera pas terminé, vous n’aurez peut-être pas accès à ces nouvelles fonctionnalités.

Intune vous donne maintenant la possibilité d’authentifier les appareils à l’aide de l’application Portail d’entreprise pour les méthodes d’inscription suivantes :

- Programme d'inscription d'appareils Apple
- Apple School Manager
- Inscription à Apple Configurator

Lorsque vous utilisez l’option Portail d’entreprise, l’authentification multifacteur Azure Active Directory peut être appliquée sans bloquer ces méthodes d’inscription.

Lorsque vous utilisez l’option Portail d’entreprise, Intune ignore l’authentification utilisateur dans l’Assistant Réglages iOS pour l’inscription d’affinité utilisateur. Cela signifie que l’appareil est initialement inscrit comme appareil sans utilisateur et, par conséquent, vous ne recevez pas les configurations ou stratégies des groupes d’utilisateurs. Il reçoit uniquement les configurations et les stratégies des groupes d’appareils. Toutefois, Intune installera automatiquement l’application Portail d’entreprise sur l’appareil. Le premier utilisateur à lancer l’application Portail d’entreprise et à s’y connecter sera associé à l’appareil dans Intune. À ce stade, l’utilisateur reçoit les configurations et les stratégies de ses groupes d’utilisateurs. L’association de l’utilisateur ne peut pas être modifiée sans réinscription.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685-eeready---"></a>Prise en charge de plusieurs comptes DEP/Apple School Manager par Intune<!-- 747685 eeready -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du Programme d’inscription des appareils (DEP) ou Apple School Manager. Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

### <a name="remote-printing-over-a-secure-network---1709994----"></a>Impression à distance sur un réseau sécurisé<!-- 1709994  -->
Les solutions d’impression mobiles sans fil PrinterOn permettront aux utilisateurs d’imprimer à distance depuis n’importe où et à tout moment via un réseau sécurisé. PrinterOn s’intégrera au Kit SDK APP d’Intune à la fois pour iOS et Android. Vous pourrez cibler les stratégies de protection d’application pour cette application via le panneau des **stratégies de protection d’application** d’Intune, dans la console d’administration. Les utilisateurs finaux pourront télécharger l’application « PrinterOn for Microsoft » via le Google Play Store ou iTunes afin de l’utiliser dans leur écosystème Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager---1352411---"></a>Prise en charge du Portail d’entreprise macOS pour les inscriptions qui utilisent le gestionnaire d’inscription d’appareil<!-- 1352411 -->

Les utilisateurs peuvent désormais utiliser le Gestionnaire d’inscription d’appareil durant l’inscription auprès du portail d’entreprise macOS.

### <a name="device-management"></a>Gestion des périphériques

#### <a name="windows-defender-health-status-and-threat-status-reports--854704---"></a>Rapports sur l’état de menace et d’intégrité de Windows Defender<!--854704 -->

Il est essentiel de comprendre l’état et l’intégrité de Windows Defender pour gérer des PC Windows.  Avec cette mise à jour, Intune ajoute de nouveaux rapports et de nouvelles actions à l’état et à l’intégrité de l’agent Windows Defender. Grâce à un rapport de cumul d’état dans la [charge de travail Conformité de l’appareil](../protect/compliance-policy-monitor.md), vous pouvez voir les appareils qui nécessitent les actions suivantes :
- mise à jour des signatures
- Redémarrer
- intervention manuelle
- analyse complète
- autres états de l’agent nécessitant une intervention

Un rapport détaillé pour chaque catégorie d’état liste les PC individuels nécessitant une attention particulière, ou ceux qui sont signalés comme **sans problème**.

#### <a name="new-privacy-settings-for-device-restrictions--1308926---"></a>Nouveaux paramètres de confidentialité pour les restrictions de l’appareil<!--1308926 -->
[Deux nouveaux paramètres de confidentialité](../configuration/device-restrictions-windows-10.md#privacy) sont désormais disponibles pour les appareils :
- **Publier les activités de l’utilisateur** : affectez la valeur **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches.
- **Activités locales uniquement** : affectez la valeur **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches en fonction uniquement de l’activité locale.

#### <a name="new-settings-for-the-microsoft-edge-browser--1469166---"></a>Nouveaux paramètres pour le navigateur Microsoft Edge<!--1469166 -->
[Deux nouveaux paramètres](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser) sont désormais disponibles pour les appareils avec le navigateur Microsoft Edge : **Chemin vers le fichier de favoris** et **Modifications des favoris**.

### <a name="app-management"></a>Gestion des applications

#### <a name="protocol-exceptions-for-applications--1035509---"></a>Exceptions de protocoles pour les applications<!--1035509 -->

Vous pouvez à présent créer des exceptions à la stratégie de transfert de données de gestion des applications mobiles (MAM) Intune pour ouvrir des applications non gérées spécifiques. De telles applications doivent être approuvées par le service informatique. Hormis les exceptions que vous créez, le transfert de données est toujours limité aux applications qui sont gérées par Intune quand votre stratégie de transfert de données est définie pour les **applications gérées uniquement**. Vous pouvez créer les restrictions à l’aide de protocoles (iOS) ou de packages (Android).

Par exemple, vous pouvez ajouter le package Webex en tant qu’exception à la stratégie de transfert de données MAM. Cela permet d’ouvrir les liens Webex dans un e-mail Outlook géré directement dans l’application Webex. Le transfert de données sera toujours limité dans d’autres applications non gérées. Pour plus d’informations, consultez [Exceptions de la stratégie de transfert de données pour les applications](../apps/app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results---1469193---"></a>Données chiffrées par la Protection des informations Windows (WIP) dans les résultats de la recherche Windows<!-- 1469193 -->
La stratégie Protection des informations Windows comprend désormais un paramètre vous permettant d’inclure ou non les données chiffrées par cette stratégie dans les résultats de la recherche Windows. Pour définir cette option de stratégie de protection d’application, sélectionnez **Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés** dans les **Paramètres avancés** de la stratégie Protection des informations Windows. La stratégie de protection d’application doit être définie pour la plateforme *Windows 10* et **l’état de l’inscription** de la stratégie d’application doit indiquer **Avec inscription**. Pour plus d’informations, consultez [Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app---1740840---"></a>Configuration d’une application MSI mobile avec mise à jour automatique<!-- 1740840 -->
Vous pouvez configurer une application MSI mobile connue avec mise à jour automatique pour ignorer le processus de vérification de version. Cette fonctionnalité est utile pour éviter d’introduire une condition de concurrence. Une condition de concurrence peut notamment se produire quand l’application est mise à jour automatiquement par le développeur de l’application et aussi par Intune. Les deux peuvent essayer d’appliquer une version de l’application sur un client Windows, générant ainsi un conflit. Pour ces applications MSI mises à jour automatiquement, vous pouvez configurer le paramètre **Ignorer la version de l’application** dans le panneau **Informations sur l’application**. Quand vous basculez ce paramètre sur **Oui**, Microsoft Intune ignore la version de l’application installée sur le client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune---1864117---"></a>Ensembles liés de licences d’application pris en charge par Intune<!-- 1864117 -->
Dans le portail Azure, Intune prend désormais en charge les jeux liés de licences d’application comme élément d’application unique dans l’interface utilisateur. En outre, toutes les applications sous licence en mode hors connexion synchronisées à partir de Microsoft Store pour Entreprises seront consolidées dans une entrée d’application unique et les détails du déploiement des packages individuels seront migrés sur l’entrée unique. Pour voir les ensembles de licences d’application associés dans le portail Azure, sélectionnez **Licences d’application** dans le panneau **Applications clientes**.

### <a name="device-configuration"></a>Configuration de l’appareil
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption---1463582---"></a>Extensions de fichier WIP (Windows Information Protection) pour le chiffrement automatique<!-- 1463582 -->
La stratégie Protection des informations Windows comprend désormais un paramètre vous permettant de spécifier des extensions de fichier. Les fichiers avec ces extensions sont automatiquement chiffrés durant la copie à partir d’un partage SMB (Server Message Block) dans les limites de l’entreprise, telles que définies dans la stratégie Protection des informations Windows.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurer les paramètres de compte de ressource pour les appareils Surface Hub

Vous pouvez à présent configurer à distance les paramètres de compte de ressource pour les appareils Surface Hub.

Le compte de ressource est utilisé par un appareil Surface Hub pour l’authentification sur Skype/Exchange afin de prendre part à une réunion.
Vous pouvez créer un compte de ressource unique afin que l’appareil Surface Hub puisse s’afficher dans la réunion en tant que salle de conférence,
par exemple un compte de ressource tel que **Salle de conférence B41/6233**.

> [!NOTE]
> - Si vous laissez les champs vides, vous allez remplacer les attributs précédemment configurés sur l’appareil.
>
> - Les propriétés de compte de ressource peuvent changer dynamiquement sur l’appareil Surface Hub, par exemple si la rotation de mot de passe est activée. Par conséquent, il est possible que les valeurs dans la console Azure prennent un certain temps avant de refléter la réalité sur l’appareil.
>
>   Pour comprendre ce qui est actuellement configuré sur l’appareil Surface Hub, les informations de compte de ressource peuvent être incluses dans l’inventaire matériel (qui dispose déjà d’un intervalle de 7 jours) ou en tant que propriétés en lecture seule. Pour améliorer la précision une fois que l’action à distance a eu lieu, vous pouvez obtenir l’état des paramètres immédiatement après l’exécution de l’action pour mettre à jour les paramètres/le compte sur l’appareil Surface Hub.

##### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque

|Nom du paramètre  |Options du paramètre  |Description  |
|---------|---------|---------|
|Exécution du contenu d’un exécutable protégé par mot de passe à partir d’un e-mail|Bloquer, Auditer, Non configuré|Empêcher l’exécution de fichiers exécutables téléchargés à partir d’un e-mail et protégés par mot de passe.|
|Protection avancée contre les ransomware|Activé, Auditer, Non configuré|Utiliser une protection agressive contre les ransomware.|
|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows|Activé, Auditer, Non configuré|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe).|
|Création de processus à partir des commandes PSExec et WMI|Bloquer, Auditer, Non configuré|Bloquer les créations de processus issues des commandes PSExec et WMI.|
|Processus non approuvés et non signés exécutés à partir d’USB|Bloquer, Auditer, Non configuré|Bloquer les processus non approuvés et non signés exécutés à partir d’USB.|
|Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée|Bloquer, Auditer, Non configuré|Bloque l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de liste approuvée.|

##### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

|              Nom du paramètre               |                                                              Options du paramètre                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protection des dossiers (déjà implémenté) | Non configuré, Activer, Auditer uniquement (déjà implémentées)<br><br> <strong>Nouveau</strong><br>Bloquer la modification du disque, Auditer la modification du disque |             |

Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.<br><br>**Activer** : empêcher les applications non approuvées de modifier ou de supprimer des fichiers dans des dossiers protégés et d’écrire dans des secteurs de disque.<br><br>
**Bloquer la modification du disque uniquement** :<br>Empêcher les applications non approuvées d’écrire dans des secteurs de disque. Les applications non approuvées peuvent toujours modifier ou supprimer des fichiers dans des dossiers protégés.

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies--1704133--"></a>Ajouts aux paramètres de sécurité du système pour les stratégies de conformité Windows 10 et versions ultérieures<!--1704133-->

Des ajouts apportés aux paramètres de conformité Windows 10 sont désormais disponibles, comme l’obligation d’utiliser le pare-feu et l’antivirus Windows Defender.

### <a name="intune-apps"></a>Applications Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business--1222672--"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises<!--1222672-->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications hors connexion sont installées par Intune et non pas par le Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile---1728700---"></a>Empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes du profil professionnel<!-- 1728700 -->

Quand vous déployez l’application Gmail dans un profil Android for Work, vous pouvez désormais empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel à l’aide du paramètre **Ajouter et supprimer des comptes** du profil de restrictions d’appareil Android for Work.

<!-- ########################## -->
## <a name="january-2018"></a>Janvier 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire---1639263---"></a>Alertes relatives aux jetons expirés et les jetons qui arrivent à expiration<!-- 1639263 -->
La page de vue d’ensemble affiche maintenant des alertes pour les jetons expirés et ceux qui arrivent à expiration. Lorsque vous cliquez sur une alerte pour un jeton unique, vous accéderez à la page des détails de ce jeton.  Si vous cliquez sur une alerte comportant plusieurs jetons, vous accéderez à une liste de tous les jetons avec leur état. Les administrateurs doivent renouveler leurs jetons avant la date d’expiration.

### <a name="device-management"></a>Gestion des périphériques

#### <a name="remote-erase-command-support-for-macos-devices---1438084---"></a>Prise en charge de la commande d’effacement à distance pour les appareils macOS<!-- 1438084 -->

Les administrateurs peuvent exécuter une commande d’effacement à distance pour les appareils macOS.

> [!IMPORTANT]
> La commande d’effacement ne peut pas être annulée et doit être utilisée avec précaution.

La commande d’effacement supprime toutes les données, y compris le système d’exploitation, d’un appareil. Elle entraîne aussi la suppression de l'appareil de la gestion Intune. Aucun avertissement n’est envoyé à l’utilisateur, et l’effacement se produit dès l’envoi de la commande.

Vous pouvez configurer un code PIN de récupération à 6 chiffres. Ce code PIN peut servir à déverrouiller l’appareil effacé avant de lancer la réinstallation du système d’exploitation. Une fois que l’effacement a démarré, le code PIN apparaît dans une barre d’état sur le panneau de présentation de l’appareil dans Intune. Le code PIN restera affiché tant que l’effacement est en cours. Une fois l’effacement terminé, l’appareil disparaît totalement de la gestion Intune. Veillez à enregistrer le code PIN de récupération afin que toute personne qui restaure l’appareil puisse l’utiliser.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token---820870---"></a>Révoquer des licences pour un jeton Programme d’achat en volume iOS<!-- 820870 -->
Vous pouvez révoquer la licence de toutes les applications de Programme d’achat en volume (VPP) iOS pour un jeton VPP donné.

### <a name="app-management"></a>Gestion des applications

#### <a name="revoking-ios-volume-purchase-program-apps----820863---"></a>Révocation des applications du Programme d’achat en volume iOS <!-- 820863 -->
Pour un appareil donné qui a une ou plusieurs applications de Programme d’achat en volume (VPP) iOS, vous pouvez révoquer pour l’appareil la licence d’application associée basée sur l’appareil. La révocation d’une licence d’application ne désinstalle pas l’application VPP de l’appareil. Pour désinstaller une application VPP, vous devez remplacer l’action d’attribution par **Désinstaller**. Pour plus d’informations, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune](../apps/vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type---1332318---"></a>Attribuer des applications mobiles Office 365 aux appareils iOS et Android à l’aide du type d’application intégré<!-- 1332318 -->
Le type d’application **Intégré** facilite la création d’applications Office 365 et leur affectation aux appareils iOS et Android gérés. Ces applications incluent les applications Office 365 telles que Word, Excel, PowerPoint et OneDrive. Vous pouvez affecter des applications spécifiques au type d’application et modifier la configuration des informations des applications.

#### <a name="including-and-excluding-app-assignment-based-on-groups---1406920---"></a>Inclusion et exclusion d’affectations d’applications en fonction des groupes<!-- 1406920 -->

Pendant l’affectation d’une application et après avoir sélectionné un type d’affectation, vous pouvez sélectionner les groupes à inclure et ceux à exclure.

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments----1480316---"></a>Vous pouvez attribuer une stratégie de configuration d’application à des groupes en incluant et excluant des affectations <!-- 1480316 -->

Vous pouvez attribuer une stratégie de configuration d’application à un groupe d’utilisateurs et d’appareils à l’aide d’une combinaison d’affectations d’inclusion et d’exclusion. Les affectations peuvent être choisies sous la forme d’une sélection personnalisée de groupes ou d’un groupe virtuel. Un groupe virtuel peut être notamment **Tous les utilisateurs**, **Tous les appareils** ou **Tous les utilisateurs + Tous les appareils**.

#### <a name="support-for-windows-10-edition-upgrade-policy-----903672archived-1119689---"></a>Prise en charge de la stratégie de mise à niveau de l’édition Windows 10  <!-- 903672(archived), 1119689 -->  
Vous pouvez créer une stratégie de mise à niveau d’édition Windows 10 qui met à niveau les appareils Windows 10 vers Windows 10 Éducation, Windows 10 Éducation N, Windows 10 Professionnel, Windows 10 Professionnel N, Windows 10 Professionnel Éducation et Windows 10 Professionnel Éducation N. Pour plus d’informations sur les mises à niveau d’édition Windows 10, consultez [Guide pratique pour configurer les mises à niveau d’édition Windows 10 ](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal----1737088-1634311---"></a>Les stratégies d’accès conditionnel pour Intune sont disponibles uniquement à partir du Portail Azure <!-- 1737088 1634311 -->

À compter de cette version, vous devez configurer et gérer vos stratégies d’accès conditionnel dans le [portail Azure](https://portal.azure.com) à partir d’**Azure Active Directory** > **Accès conditionnel**. Par souci pratique, vous pouvez également accéder à ce panneau à partir d’Intune dans le portail Azure (**Intune** > **Accès conditionnel**).

#### <a name="updates-to-compliance-emails--1637547---"></a>E-mails de mises à jour de conformité<!--1637547 -->

Quand un e-mail est envoyé pour signaler un appareil non conforme, des détails sur l’appareil non conformes sont inclus.

### <a name="intune-apps"></a>Applications Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices--1583480--"></a>Nouvelles fonctionnalités de l’action « Résoudre » pour les appareils Android<!--1583480-->

L’application Portail d’entreprise pour Android étend l’action « Résoudre » sur **Mettre à jour les paramètres d’appareil** afin de résoudre les [problèmes de chiffrement d’appareil](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10--676506--"></a>Verrouillage à distance disponible dans l’application Portail d’entreprise pour Windows 10<!--676506-->
Les utilisateurs finaux peuvent désormais verrouiller à distance leurs appareils à partir de l’application Portail d’entreprise pour Windows 10. Cela ne s’affichera pas pour l’appareil local qu’ils utilisent de manière active.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10--676546--"></a>Simplification de la résolution des problèmes de conformité affectant l’application Portail d’entreprise pour Windows 10<!--676546-->
Les utilisateurs finaux d’appareils Windows peuvent choisir la raison de la non-conformité dans l’application Portail d’entreprise. Lorsque possible, ils accéderont directement à l’emplacement approprié dans l’application Paramètres pour résoudre le problème.

<!-- ########################## -->
## <a name="december-2017"></a>Décembre 2017

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="new-automatic-redeployment-setting---1469168---"></a>Nouveau paramètre de redéploiement automatique<!-- 1469168 -->
Le paramètre **Redéploiement automatique** permet aux utilisateurs avec des droits d’administration de supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **Ctrl+Win+R** sur l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion. Ce paramètre se trouve sous Windows 10 -> Restrictions sur l’appareil -> Général -> Redéploiement automatique. Pour plus d’informations, consultez [Paramètres de restriction d’appareil Intune pour Windows 10](../configuration/device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy----903672--1119689---"></a>Prise en charge d’éditions source supplémentaires dans la stratégie de mise à niveau de l’édition Windows 10 <!-- 903672,  1119689 -->
Vous pouvez maintenant utiliser la stratégie de mise à niveau de l’édition Windows 10 pour effectuer une mise à niveau à partir d’autres éditions de Windows 10 (Windows 10 Professionnel, Windows10 Professionnel Éducation, Windows 10 Cloud, etc.). Avant cette version, les chemins de mise à niveau de l’édition pris en charge étaient plus limités. Pour plus d’informations, consultez le [Guide pratique de configuration des mises à niveau Windows 10](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings---1335507---"></a>Nouveaux paramètres pour le profil de configuration d’appareil Windows Defender Security Center (WDSC)<!-- 1335507 -->

Intune ajoute une nouvelle section de paramètres pour le profil de configuration d’appareil, sous la Protection du point de terminaison, nommée **Windows Defender Security Center**. Les administrateurs informatiques peuvent configurer les éléments de base auxquels les utilisateurs finaux de l’application Windows Defender Security Center peuvent accéder. Si un administrateur informatique masque un élément de base dans l’application Windows Defender Security Center, les notifications liées à l’élément de base masqué ne s’affichent pas sur l’appareil de l’utilisateur.

Vous trouverez ci-dessous les éléments de base que les administrateurs peuvent masquer dans les paramètres du profil de configuration d’appareil Windows Defender Security Center :
- Protection contre les menaces et les virus
- Performances et intégrité de l’appareil
- Protections du pare-feu et du réseau
- Contrôle d’application et du navigateur
- Options Famille

Les administrateurs informatiques peuvent également personnaliser les notifications que les utilisateurs reçoivent. Par exemple, vous pouvez décider si les utilisateurs reçoivent toutes les notifications générées par les éléments de base visibles dans WDSC ou uniquement les notifications critiques. Les notifications non critiques incluent des résumés périodiques sur l’activité de l’antivirus Windows Defender et des notifications indiquant lorsque des analyses sont terminées. Toutes les autres notifications sont considérées comme critiques. En outre, vous pouvez aussi personnaliser le contenu même de la notification. Par exemple, vous pouvez fournir les coordonnées du service informatique à inclure dans les notifications qui s’affichent sur les appareils des utilisateurs.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling---1361755---"></a>Prise en charge de connecteurs multiples pour le traitement des certificats SCEP et PFX<!-- 1361755 -->

Les clients qui utilisent le connecteur NDES local pour fournir des certificats à des appareils peuvent désormais configurer plusieurs connecteurs dans un seul locataire.

Cette nouvelle fonctionnalité prend en charge le scénario suivant :

- **Haute disponibilité**

Chaque connecteur NDES extraie des demandes de certificat d’Intune.  Si un connecteur NDES a l’état hors connexion, l’autre connecteur peut continuer à traiter les requêtes.

#### <a name="customer-subject-name-can-use-aad_device_id-variable----1468599---"></a>Le nom d’objet du client peut utiliser la variable AAD_DEVICE_ID <!-- 1468599 -->

Lorsque vous créez un profil de certificat SCEP dans Intune, vous pouvez désormais utiliser la variable AAD_DEVICE_ID lorsque vous générez le nom d’objet du client.   Lorsque le certificat est demandé à l’aide de ce profil SCEP, la variable est remplacée par l’ID AAD de l’appareil qui effectue la demande de certificat.


### <a name="device-management"></a>Gestion des périphériques

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747---"></a>Gérer les appareils macOS inscrits auprès de Jamf avec le moteur de conformité des appareils d’Intune<!-- 1592747 -->
Vous pouvez utiliser Jamf pour envoyer des informations sur l’état des appareils macOS à Intune, qui évaluera alors la conformité avec les stratégies définies dans la console Intune. En fonction de cet état et d’autres conditions (notamment, l’emplacement, les risques de l’utilisateur, etc.), l’accès conditionnel appliquera des stratégies de conformité aux appareils macOS qui accèdent aux applications cloud et locales reliées à Azure AD, y compris Office 365. En savoir plus sur la [configuration de l’intégration de Jamf](../protect/conditional-access-integrate-jamf.md) et la [mise en application de la conformité des appareils Jamf gérés](../protect/conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action-----1424701---"></a>Nouvelle action d’appareil iOS  <!-- 1424701 -->

Vous pouvez maintenant arrêter les appareils supervisés iOS 10.3. Cette action arrête immédiatement l’appareil sans avertir l’utilisateur final. L’action **Arrêter (supervisé uniquement)** se trouve dans les propriétés de l’appareil lorsque vous sélectionnez un appareil dans la charge de travail **Appareil**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices---1468103---"></a>Interdire les changements de date/heure sur les appareils Samsung Knox<!-- 1468103 -->

Nous avons ajouté une nouvelle fonctionnalité qui vous permet d’empêcher les changements de date et d’heure sur les appareils Samsung Knox. Vous la trouverez dans **Profils de configuration d’appareil** > **Restrictions d’appareil (Android)** > **Général**.

#### <a name="surface-hub-resource-account-supported---1566442----"></a>Compte de ressource Surface Hub pris en charge<!-- 1566442  -->

Une nouvelle action d’appareil a été ajoutée pour permettre aux administrateurs de définir et de mettre à jour le compte de ressource associé à un Surface Hub.

Le compte de ressource est utilisé par un Surface Hub pour l’authentification avec Skype/Exchange afin de prendre part à une réunion. Vous pouvez créer un compte de ressource unique afin que le Surface Hub s’affiche dans la réunion en tant que salle de conférence. Par exemple, le compte de ressource peut s’afficher comme *Salle de conférence B41/6233*. Le compte de ressource (également appelé compte de l’appareil) pour le Surface Hub doit en général être configuré pour l’emplacement de la salle de conférence et également lorsque d’autres paramètres du compte de ressource sont modifiés.

Lorsque les administrateurs veulent mettre à jour le compte de ressource sur un appareil, ils doivent fournir les informations d’identification Active Directory/Azure Active Directory actuelles associées à l’appareil. Si la rotation de mot de passe est activée sur l’appareil, les administrateurs doivent accéder à Azure Active Directory pour trouver le mot de passe.

> [!NOTE]
> Tous les champs sont transmis sous forme de package et écrasent tous les champs précédemment configurés. Les champs vident écrasent également les champs existants.

Vous trouverez ci-dessous les paramètres que les administrateurs peuvent configurer :

- **Compte de ressource**
  - **Utilisateur Active Directory**

    Nomdedomaine\nomd’utilisateur ou Nom d’utilisateur principal (UPN) : user@domainname.com

  - **Mot de passe**

- **Paramètres facultatifs du compte de ressource** (à définir à l’aide du compte de ressource spécifié)

  - **Période de rotation du mot de passe**

    Permet de s’assurer que le mot de passe du compte est automatiquement mis à jour par le Surface Hub chaque semaine à des fins de sécurité. Pour configurer des paramètres une fois cette option activée, il est nécessaire tout d’abord de réinitialiser le mot de passe du compte dans Azure Active Directory.

  - **Adresse du protocole d’initiation de session (SIP)**

    Utilisée uniquement en cas d’échec de la découverte automatique.

  - **Courrier électronique**

    Adresse e-mail de l’appareil/du compte de ressource.

  - **Serveur Exchange**

    Requis uniquement en cas d’échec de la découverte automatique.

  - **Synchronisation du calendrier**

    Permet de spécifier si la synchronisation du calendrier et d’autres services Exchange Server sont activés. Par exemple : synchronisation de réunion.

#### <a name="install-office-apps-on-macos-devices---1494311---"></a>Installer des applications Office sur des appareils macOS<!-- 1494311 -->
Vous pourrez maintenant installer des applications Office sur des appareils macOS. Ce nouveau type d’application vous permettra d’installer Word, Excel, PowerPoint, Outlook et OneNote. Ces applications bénéficient également de Microsoft AutoUpdate (MAU) qui garantit que vos applications sont sécurisées et à jour.

### <a name="app-management"></a>Gestion des applications

#### <a name="delete-an-ios--volume-purchasing-program-token---820879---"></a>Supprimer un jeton Programme d’achat en volume iOS<!-- 820879 -->
Vous pouvez supprimer le jeton Programme d’achat en volume (VPP) iOS à l’aide de la console. Ceci peut être nécessaire si vous avez des instances dupliquées d’un jeton VPP.

### <a name="intune-apps"></a>Applications Intune


### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data---1667026---"></a>Une nouvelle collection d’entités nommée Utilisateur actuel se limite aux données des utilisateurs actuellement actifs<!-- 1667026 -->

La collecte d’entités **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

En revanche, la nouvelle collection d’entités **Utilisateur actuel** contient uniquement les utilisateurs qui n’ont pas été supprimés. La collection d'entités **Utilisateur actuel** ne contient que des utilisateurs actuellement actifs. Pour plus d’informations sur la collection d’entités **Utilisateur actuel**, consultez la page [Informations de référence sur l’entité Utilisateur actuel](../developer/reports-ref-data-model.md).

### <a name="updated-graph-apis---1736360---"></a>API Graph mises à jour<!-- 1736360 -->

Dans cette version, nous avons mis à jour quelques-unes des API Graph pour Intune (actuellement en version bêta). Consultez le [journal mensuel des modifications de l’API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) pour plus d’informations.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-supports-windows-information-protection-wip-denied-apps---1479103---"></a>Intune prend en charge les applications refusées par la Protection des informations Windows<!-- 1479103 -->
Vous pouvez spécifier les applications refusées dans Intune. Si une application est refusée, son accès aux informations d’entreprise est bloqué (ce qui correspond à l’inverse de la liste des applications autorisées). Pour plus d’informations, consultez [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Liste d’exclusion recommandée pour la Protection des informations Windows).

<!-- ########################## -->
## <a name="november-2017"></a>Novembre 2017

### <a name="troubleshoot-enrollment-issues----746324---"></a>Résoudre les problèmes d’inscription <!-- 746324 -->

L’espace de travail **Résolution des problèmes** montre désormais les problèmes d’inscription des utilisateurs. Des détails sur les problèmes et des suggestions de correction peuvent aider les administrateurs et les agents du support technique à résoudre les problèmes. Certains problèmes d’inscription ne sont pas capturés et certaines erreurs peuvent ne pas avoir de suggestions de correction.

### <a name="group-assigned-enrollment-restrictions---747598---"></a>Restrictions d’inscription assignées aux groupes<!-- 747598 -->

En tant qu’administrateur Intune, vous pouvez désormais [créer des restrictions d’inscription Type d’appareil et Limite d’appareils personnalisées pour des groupes d’utilisateurs](../enrollment/enrollment-restrictions-set.md).

Le portail Azure Intune vous permet de créer jusqu’à 25 instances de chaque type de restriction qui peuvent ensuite être assignées aux groupes d’utilisateurs. Les restrictions assignées aux groupes remplacent les restrictions par défaut.

Toutes les instances d’un type de restriction sont conservées dans une liste classée de manière stricte. Cet ordre définit une valeur de priorité pour la résolution des conflits. Un utilisateur impacté par plusieurs instances de restriction est uniquement limité par l’instance ayant la valeur de priorité la plus élevée. Vous pouvez modifier la priorité d’une instance donnée en la faisant glisser vers un autre emplacement de la liste.

Cette fonctionnalité sera disponible quand les paramètres Android for Work seront migrés depuis le menu Inscription Android for Work vers le menu Restrictions d’inscription. Cette migration pouvant prendre plusieurs jours, votre compte peut être mis à niveau pour d’autres parties de la version de novembre avant que l’affectation aux groupes ne soit activée pour les restrictions d’inscription.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors---1528104---"></a>Prise en charge de plusieurs connecteurs NDES (Service d’inscription de périphérique réseau)<!-- 1528104 -->

NDES permet aux appareils mobiles s’exécutant sans informations d’identification de domaine d’obtenir des certificats basés sur le protocole d’inscription de certificats simple (SCEP).
Cette mise à jour prend en charge plusieurs connecteurs NDES.

### <a name="manage-android-for-work-devices-independently-from-android-devices---1490731-eeready--"></a>Gérer les appareils Android for Work indépendamment des appareils Android<!-- 1490731 EEready-->

Intune prend en charge la gestion de l’inscription des appareils Android for Work indépendamment de la plateforme Android. Ces paramètres sont gérés sous **Inscription de l’appareil** > **Restrictions d’inscription** > **Restrictions de type d’appareil**. (Ils se trouvaient sous **Inscription de l’appareil** > **Inscription Android for Work** > **Paramètres d’inscription d’Android for Work**.)

Par défaut, les paramètres de vos appareils Android for Work sont identiques à ceux de vos appareils Android. Toutefois, ce ne sera plus le cas une fois que vous aurez modifié vos paramètres Android for Work.

Si vous bloquez l’inscription Android for Work personnelle, seuls les appareils Android d’entreprise peuvent s’inscrire en tant qu’Android for Work.

Quand vous utilisez les nouveaux paramètres, tenez compte des points suivants :

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Si vous n’avez jamais intégré l’inscription Android for Work

La nouvelle plateforme Android for Work est bloquée dans les restrictions de type d’appareil par défaut. Une fois la fonctionnalité intégrée, vous pouvez autoriser les appareils à s’inscrire auprès d’Android for Work. Pour ce faire, changez le paramétrage par défaut ou créez une restriction de type d’appareil afin de remplacer la restriction de type d’appareil par défaut.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Si vous avez intégré l’inscription Android for Work

Votre situation varie selon le paramètre que vous avez choisi :

| Paramètre | État Android for Work dans la restriction de type d’appareil par défaut | Remarques |
| --- | --- | --- |
| **Gérer tous les appareils comme Android** | Bloqué | Tous les appareils Android doivent s’inscrire sans Android for Work. |
| **Gérer les appareils pris en charge comme Android for Work** | Autorisé | Tous les appareils Android qui prennent en charge Android for Work doivent s’inscrire auprès d’Android for Work. |
| **Gérer les appareils pris en charge pour les utilisateurs uniquement dans ces groupes comme Android for Work** | Bloqué | Une stratégie de restriction de type d’appareil distincte a été créée pour remplacer le paramétrage par défaut. Cette stratégie définit les groupes que vous avez choisis pour autoriser l’inscription Android for Work. Les utilisateurs dans les groupes sélectionnés continueront à être autorisés à inscrire leurs appareils Android for Work. Tous les autres utilisateurs ne peuvent pas s’inscrire auprès Android for Work. |

Dans tous les cas, les règles que vous avez envisagées sont conservées. Aucune action n’est requise de votre part pour gérer l’autorisation globale ou par groupe d’Android for Work dans votre environnement.

### <a name="google-play-protect-support-on-android---908720---"></a>Prise en charge de Google Play Protect sur Android<!-- 908720 -->

Avec la publication d’Android Oreo, Google introduit une suite de fonctionnalités de sécurité appelée Google Play Protect qui permet aux utilisateurs et aux organisations d’exécuter des applications sécurisées et des images Android sécurisées. Intune prend maintenant en charge les fonctionnalités de Google Play Protect, notamment l’attestation SafetyNet distante. Les administrateurs peuvent définir des critères de stratégie de conformité pour que Google Play Protect soit configuré et sain.
Le paramètre **Attestation d’appareil SafetyNet** nécessite que l’appareil se connecte à un service Google pour vérifier que l’appareil est intègre et qu’il n’est pas compromis. Les administrateurs peuvent également définir un paramètre de profil de configuration pour qu’Android for Work exige que les applications installées soient vérifiées par les services Google Play. Si un appareil n’est pas conforme aux exigences de Google Play Protect, l’accès conditionnel peut empêcher les utilisateurs d’accéder aux ressources de l’entreprise.

- Découvrez comment [créer une stratégie de conformité des appareils pour activer Google Play Protect](../protect/compliance-policy-create-android.md).

### <a name="text-protocol-allowed-from-managed-apps---1414050----"></a>Protocole de texte autorisé depuis des applications gérées<!-- 1414050  -->

Les applications gérées par le SDK d’application Intune peuvent envoyer des SMS.


### <a name="app-install-report-updated-to-include-install-pending-status---1249446---"></a>Mise à jour du rapport d’installation de l’application pour inclure l’état Installation en attente<!-- 1249446 -->  

Le rapport **État de l’installation de l’application** accessible pour chaque application via la liste **Application** dans la charge de travail **Applications clientes** contient désormais un comptage **Installation en attente** pour les utilisateurs et les appareils.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection---1391759---"></a>API d’inventaire des applications iOS 11 pour la détection de menaces mobiles<!-- 1391759 -->

Intune collecte les informations d’inventaire des applications à partir des appareils personnels et d’entreprise et les met à la disposition des fournisseurs de détection des menaces mobiles, comme Lookout for Work. Vous pouvez collecter un inventaire des applications auprès des utilisateurs d’appareils iOS 11+.

**Inventaire des applications**  
Les inventaires à partir des appareils personnels et d’entreprise iOS 11 sont envoyés à votre fournisseur de service de détection des menaces mobiles. Les données de l’inventaire des applications comprennent les informations suivantes :

- ID de l’application
- Version de l’application
- Version abrégée de l’application
- Nom de l’application
- Taille du bundle d’applications
- Taille dynamique de l’application
- Application validée ou non
- Application gérée ou non

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone---1463747-wnready---"></a>Faire migrer des utilisateurs et appareils MDM hybrides vers la version autonome d’Intune<!-- 1463747 wnready -->
De nouveaux processus et de nouveaux outils sont maintenant disponibles pour déplacer les utilisateurs et leurs appareils de MDM hybride vers Intune dans le portail Azure. Vous pouvez ainsi effectuer les tâches suivantes :
- Copier des stratégies et des profils de la console Configuration Manager vers Intune dans le portail Azure
- Déplacer une partie des utilisateurs vers Intune dans le portail Azure, tout en conservant le reste dans un environnement MDM hybride
- Migrer des appareils vers Intune dans le portail Azure sans avoir à les réinscrire

### <a name="on-premises-exchange-connector-high-availability-support----676614---"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local <!-- 676614 -->
Une fois que le connecteur Exchange crée une connexion à Exchange à l’aide du Serveur d’accès au client (CAS) spécifié, le connecteur peut désormais découvrir d’autres CAS. Si l’autorité de certification principale est indisponible, le connecteur bascule vers une autre autorité de certification disponible, jusqu'à ce que l’autorité de certification principale redevienne disponible. Pour plus de détails, voir [Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only---1424595---"></a>Redémarrer un appareil iOS à distance (supervisé uniquement)<!-- 1424595 -->

Vous pouvez désormais déclencher le redémarrage d’un appareil iOS 10.3+ supervisé au moyen d’une action d’appareil. Pour plus d’informations sur l’utilisation de l’action de redémarrage d’appareil, consultez [Redémarrer à distance des appareils avec Intune](../remote-actions/device-restart.md).

> [!Note]
> Cette commande nécessite un appareil supervisé et le droit d’accès **Verrouillage de l’appareil**. L’appareil redémarre immédiatement. Après le redémarrage, les appareils iOS verrouillés par un code secret ne rejoignent pas un réseau Wi-Fi et peuvent se trouver dans l’impossibilité de communiquer avec le serveur.

### <a name="single-sign-on-support-for-ios---1333645---"></a>Prise en charge de l’authentification unique pour iOS<!-- 1333645 -->  

Vous pouvez utiliser l’authentification unique pour les utilisateurs d’iOS. Les applications iOS qui sont codées pour rechercher les informations d’identification de l’utilisateur dans la charge utile d’authentification unique fonctionnent avec cette mise à jour de la configuration de la charge utile. Vous pouvez également utiliser un UPN et un ID d’appareil Intune pour configurer le nom du principal et le domaine. Pour plus d’informations, consultez [Configurer Intune pour l’authentification unique des appareils iOS](../configuration/ios-device-features-settings.md#single-sign-on).

### <a name="add-find-my-iphone-for-personal-devices--1427287--"></a>Ajouter « Rechercher mon iPhone » pour les appareils personnels<!--1427287-->
Vous pouvez désormais savoir si la fonctionnalité Verrou d’activation est activée pour les appareils iOS. Cette fonctionnalité se trouvait avant dans le portail classique.

### <a name="remotely-lock-managed-macos-device-with-intune---1437691---"></a>Verrouiller un appareil macOS géré à distance à l’aide d’Intune<!-- 1437691 -->

Vous pouvez verrouiller un appareil macOS perdu et définir un code PIN de récupération à 6 chiffres. Une fois le verrouillage effectué, le panneau **Vue d’ensemble des appareils** affiche le code PIN jusqu’à ce qu’une autre action d’appareil soit envoyée.

Pour plus d’informations, consultez [Verrouiller à distance des appareils gérés avec Intune](../remote-actions/device-remote-lock.md).

### <a name="new-scep-profile-details-supported---1559808---"></a>Nouveaux détails de profil SCEP pris en charge<!-- 1559808 -->

Les administrateurs peuvent désormais définir des paramètres supplémentaires durant la création d’un profil SCEP sur les plateformes Windows, iOS, macOS et Android.  Les administrateurs peuvent définir un IMEI, un numéro de série ou un nom commun (adresse e-mail incluse) dans le format du nom de l’objet.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset---1588489---"></a>Conserver les données lors d’une réinitialisation des paramètres d’usine <!--1588489 -->
Une nouvelle fonctionnalité est disponible durant la réinitialisation de Windows 10 version 1709 et ultérieure aux paramètres d’usine. Les administrateurs peuvent spécifier si les données d’inscription des appareils et d’autres données provisionnées sont conservées sur un appareil en cas de réinitialisation aux paramètres d’usine.

Les données suivantes sont conservées pendant une réinitialisation des paramètres d’usine :
- Comptes d’utilisateur associés à l’appareil
- État de l’ordinateur (jonction de domaine, joint à Azure Active Directory)
- Inscription MDM
- Applications OEM installées (applications Win32 et du Store)
- Profil utilisateur
- Données utilisateur hors du profil utilisateur
- Ouverture de session automatique de l’utilisateur

Les données suivantes ne sont pas conservées :
- Fichiers utilisateur
- Applications utilisateur installées (applications Win32 et du Store)
- Paramètres d’appareil autres que les paramètres par défaut


### <a name="window-10-update-ring-assignments-are-displayed---1621837---"></a>Les affectations d’anneau de mise à jour de Windows 10 sont affichées<!-- 1621837 -->
Pendant une **résolution de problèmes**, vous pouvez voir les affectations de boucles de mise à jour de Windows 10 pour l’utilisateur affiché.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings----1455974----"></a>Paramètres de la fréquence d’émission des rapports Windows Defender Advanced Threat Protection (Protection avancée contre les menaces) <!-- 1455974  -->
Le service Windows Defender - Protection avancée contre les menaces permet aux administrateurs de gérer la fréquence d’émission des rapports sur les appareils gérés. Avec la nouvelle option **Augmenter la fréquence des rapports de télémétrie**, Windows Defender ATP collecte les données et évalue les risques plus fréquemment. Par défaut, l’émission de rapports optimise le niveau de performance et la vitesse. Augmenter la fréquence d’émission des rapports peut être utile pour les appareils à haut risque. Ce paramètre se trouve dans le profil **Windows Defender ATP** dans **Configurations d’appareil**.

### <a name="audit-updates---1412961---"></a>Auditer les mises à jour<!-- 1412961 -->  
La fonctionnalité d’audit d’Intune enregistre les opérations de modification relatives à Intune.  Tous les opérations de création, de mise à jour, de suppression et de tâche à distance sont capturées et conservées pendant un an.  Le portail Azure fournit une vue filtrable des 30 derniers jours de données d’audit dans chaque charge de travail.  Une API Graph correspondante permet de récupérer les données d’audit stockées pendant l’année écoulée.

La fonctionnalité d’audit se trouve sous le groupe **SURVEILLER**. Il existe un élément de menu **Journaux d’audit** par charge de travail.

### <a name="company-portal-app-for-macos-is-available--1541700--"></a>L’application Portail d’entreprise pour macOS est disponible<!--1541700-->
Le Portail d’entreprise Intune sous macOS bénéficie d’une expérience mise à jour. Il a été optimisé pour afficher clairement toutes les informations et les avis de conformité dont vos utilisateurs ont besoin pour tous les appareils qu’ils ont inscrits. Une fois que le Portail d’entreprise Intune a été déployé sur un appareil, il bénéficie de la mise à jour automatique Microsoft (AutoUpdate) pour macOS. Vous pouvez télécharger le nouveau Portail d’entreprise Intune pour macOS en ouvrant une session sur le site web du Portail d’entreprise Intune sur un appareil macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps----1248473---"></a>Microsoft Planner fait maintenant partie de la liste des applications approuvées par la gestion des applications mobiles (GAM) <!-- 1248473 -->
L’application Microsoft Planner pour iOS et Android fait désormais partie des applications approuvées pour la gestion des applications mobiles (MAM). Elle est configurable par le biais du panneau Intune App Protection sur le Portail Azure de tous les clients.
- Pour plus de détails, consultez la page [Liste MAM des applications approuvées](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices-----1547061---"></a>Fréquence de mise à jour des exigences du VPN par application sur les appareils iOS  <!-- 1547061 -->  
Les administrateurs peuvent à présent supprimer des exigences du VPN par application pour les applications installées sur des appareils iOS ; les appareils concernés seront mis à jour après l’archivage Intune suivant, ce qui se produit généralement dans les 15 minutes.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector---885457---"></a>Prise en charge du pack d’administration d’Operations Manager pour le connecteur Exchange<!-- 885457 -->
Le pack d’administration de System Center Operations Manager pour le connecteur Exchange est maintenant disponible pour vous aider à analyser les journaux du connecteur Exchange. Cette fonctionnalité offre différents moyens de surveiller le service à des fins de résolution des problèmes.

### <a name="co-management-for-windows-10-devices----1243445---"></a>Cogestion pour les appareils Windows 10 <!-- 1243445 -->
La cogestion est une solution qui propose une passerelle entre la gestion classique et la gestion moderne tout en vous donnant la possibilité d’opérer cette transition selon une approche en plusieurs phases. À la base, la cogestion est une solution qui permet aux appareils Windows 10 d’être gérés simultanément par Configuration Manager et Microsoft Intune, et d’être joints à Active Directory (AD) et à Azure Active Directory (Azure AD).  Cette configuration vous offre un moyen de vous moderniser à un rythme qui convient à votre organisation si vous ne pouvez pas le faire d’un coup.  

### <a name="restrict-windows-enrollment-by-os-version---245498---"></a>Limiter l’inscription via Windows en fonction des versions de système d’exploitation<!-- 245498 -->
En tant qu’administrateur Intune, vous pouvez maintenant spécifier une version minimale et maximale de Windows 10 pour les inscriptions d’appareils. Vous pouvez définir ces restrictions dans le panneau **Configurations de plateforme**.

Intune continue à prendre en charge l’inscription des PC et téléphones Windows 8.1. Toutefois, seules les versions de Windows 10 peuvent être configurées avec des limites minimale et maximale. Pour autoriser l’inscription d’appareils 8.1, laissez vide la limite minimale.

### <a name="alerts-for-windows-autopilot-unassigned-devices----1631236---"></a>Alertes relatives aux appareils Windows Autopilot non affectés <!-- 1631236 -->
Une nouvelle alerte est disponible pour les appareils non attribués Windows AutoPilot dans la page **Microsoft Intune** > **Inscription de l’appareil** > **Vue d’ensemble**. Cette alerte indique combien d’appareils du programme AutoPilot n’ont pas de profils de déploiement AutoPilot affectés. Utilisez les informations de l’alerte pour créer des profils et les affecter aux appareils non affectés. Quand vous cliquez sur l’alerte, une liste complète des appareils Windows AutoPilot et des informations détaillées les concernant s’affichent. Pour plus d’informations, consultez [Inscrire des appareils Windows à l’aide du programme de déploiement Windows AutoPilot](../enrollment/enrollment-autopilot.md).


### <a name="refresh-button-for-devices-list------1333581---"></a>Bouton Actualiser pour la liste des appareils   <!-- 1333581 -->
La liste des appareils ne s’actualisant pas automatiquement, vous pouvez utiliser le bouton Actualiser pour mettre à jour les appareils affichés dans la liste.

### <a name="support-for-symantec-cloud-certification-authority-ca----1333638---"></a>Prise en charge de l’Autorité de certification Symantec Cloud <!-- 1333638 -->    
Intune prend désormais en charge l’Autorité de certification Symantec Cloud qui permet à Intune Certificate Connector d’émettre des certificats PKCS de l’Autorité de certification Symantec Cloud sur des appareils gérés par Intune. Si vous utilisez déjà Intune Certificate Connector avec l’Autorité de certification Microsoft, vous pouvez utiliser la configuration existante d’Intune Certificate Connector en y ajoutant la prise en charge de l’Autorité de certification de Symantec.

### <a name="new-items-added-to-device-inventory----1404455---"></a>Nouveaux éléments ajoutés à l’inventaire des appareils  <!--1404455 -->
Les nouveaux éléments suivants sont maintenant disponibles dans [l’inventaire effectué par les appareils inscrits](../remote-actions/device-inventory.md) :

- Adresse MAC Wi-Fi
- Espace de stockage total
- Espace libre total
- MEID
- Opérateur de l’abonné

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Définir l’accès pour les applications avec un correctif de sécurité Android minimal sur l’appareil<!-- 1278463 -->   
Un administrateur peut définir le correctif de sécurité Android minimal qui doit être installé sur l’appareil pour obtenir l’accès à une application gérée sous un compte géré.

> [!Note]  
> Cette fonctionnalité restreint uniquement les correctifs de sécurité publiés par Google sur les appareils Android 6.0 +.

### <a name="app-conditional-launch-support---1193313---"></a>Prise en charge du lancement conditionnel d’applications<!-- 1193313 -->
Les administrateurs informatiques peuvent désormais définir une condition dans le portail d’administration Azure permettant d’appliquer un code secret à la place d’un code PIN numérique via la gestion des applications mobiles (MAM) lors du lancement de l’application. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Cette version d’Intune propose cette fonctionnalité **sur iOS uniquement**. Intune prend en charge un code secret comme un code PIN numérique, il définit une longueur minimale et autorise la répétition des caractères et des séquences. Cette fonctionnalité nécessite la participation des applications (c’est-à-dire, WXP, Outlook, Managed Browser, Yammer) pour intégrer le kit SDK Intune App avec le code de cette fonctionnalité en place dans le but d’appliquer les paramètres du code secret dans les applications ciblées.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report---1233999---"></a>Numéro de version des applications métier dans le rapport d’état d’installation de l’appareil<!-- 1233999 -->
Avec cette version, le rapport d’état d’installation de l’appareil affiche le numéro de version des applications métier pour iOS et Android. Vous pouvez utiliser cette information pour dépanner vos applications ou trouver les appareils qui exécutent des versions d’application anciennes.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile---951708---"></a>Les administrateurs peuvent désormais configurer les paramètres du pare-feu d’un appareil à l’aide d’un profil de configuration d’appareil<!-- 951708 -->   
Les administrateurs peuvent activer le Pare-feu sur les appareils et configurer divers protocoles pour les réseaux privés, publics et de domaine.  Ces paramètres de pare-feu se trouvent dans le profil « Endpoint protection ».

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization---958257---"></a>Windows Defender Application Guard permet de protéger les appareils des sites web non approuvés, comme défini par votre organisation<!-- 958257 -->   
Les administrateurs peuvent définir les sites comme « approuvés » ou « appartenant à l’entreprise » à l’aide d’un flux de travail Protection des informations Windows ou du nouveau profil « Limite réseau » dans les configurations de l’appareil. S’ils sont consultés dans Microsoft Edge, les sites qui ne sont pas listés dans la limite réseau approuvée d’un appareil Windows 10 64 bits s’ouvrent à la place dans un navigateur d’une machine virtuelle Hyper-V.

Application Guard se trouve dans les profils de configuration de l’appareil, dans le profil « Endpoint protection ». À partir de là, les administrateurs peuvent configurer une interaction entre le navigateur virtualisé et la machine hôte, les sites non approuvés et les sites approuvés, puis stocker les données générées dans le navigateur virtualisé. Pour utiliser Application Guard sur un appareil, une limite réseau doit d’abord être configurée. Il est important de définir une seule limite réseau pour un appareil.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps---1031096---"></a>Windows Defender Application Control sur Windows 10 Entreprise offre un mode permettant de faire uniquement confiance aux applications autorisées<!-- 1031096 -->    
Avec des milliers de nouveaux fichiers malveillants créés chaque jour, l’utilisation d’une détection antivirus basée sur les signatures pour lutter contre les programmes malveillants ne constitue probablement plus une défense suffisante contre les nouvelles attaques. En utilisant Windows Defender Application Control sur Windows 10 Entreprise, vous pouvez changer la configuration de l’appareil et passer d’un mode où les applications sont approuvées sauf si elles sont bloquées par un antivirus ou une autre solution de sécurité à un mode où le système d’exploitation approuve uniquement les applications autorisées par votre entreprise. Vous approuvez les applications dans Windows Defender Application Control.

Avec Intune, vous pouvez configurer des stratégies de contrôle d’application en mode « audit uniquement » ou en mode d’application. Les applications ne sont pas bloquées quand vous exécutez le mode « audit uniquement ». Le mode « Audit uniquement » enregistre tous les événements dans les journaux du client local. Vous pouvez également autoriser uniquement l’exécution des composants Windows et des applications du Microsoft Store, ou autoriser l’exécution d’autres applications avec une bonne réputation telle que définie par Intelligent Security Graph.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10---1063615---"></a>Windows Defender Exploit Guard constitue un nouvel ensemble de fonctionnalités de prévention d’intrusion pour Windows 10<!-- 1063615 -->   
Windows Defender Exploit Guard propose des règles personnalisées permettant de réduire l’exploitabilité des applications, empêche les menaces provenant de macros et de scripts, bloque automatiquement les connexions réseau à des adresses IP de mauvaise réputation et peut sécuriser les données contre des ransomware et des menaces inconnues. Windows Defender Exploit Guard présente les composants suivants :

- **Réduction de la surface d’attaque** fournit des règles vous permettant d’empêcher les menaces liées aux macros, aux scripts et aux e-mails.
- **Accès contrôlé au dossier** bloque automatiquement l’accès au contenu des dossiers protégés.
- **Filtre de réseau** bloque la connexion sortante de toutes les applications à une adresse IP/domaine de faible réputation
- **Exploit Protection** fournit la mémoire, le flux de contrôle et les restrictions de stratégie pouvant être utilisés pour protéger les applications contre des attaques.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices---790537---"></a>Gérer des scripts PowerShell dans Intune pour des appareils Windows 10<!-- 790537 -->

L’extension de gestion Intune vous permet de charger des scripts PowerShell dans Intune pour les exécuter sur des appareils Windows 10. L’extension vient en complément des fonctionnalités de gestion des appareils mobiles (MDM) Windows 10 et facilite l’adoption d’une gestion moderne. Pour plus d’informations, consultez [Gérer des scripts PowerShell dans Intune pour des appareils Windows 10](../apps/intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10--------1308850---"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10     <!-- 1308850 -->
- Messagerie (mobile uniquement) - désactivation des tests ou des messages MMS
- Mot de passe - paramètres pour activer FIPS et l’utilisation d’appareils secondaires Windows Hello pour l’authentification 
- Affichage - paramètres pour activer ou désactiver la mise à l’échelle GDI pour les applications héritées

### <a name="windows-10-kiosk-mode-device-restrictions---1308872---"></a>Restrictions des appareils en mode plein écran sur Windows 10<!-- 1308872 -->   
Vous pouvez restreindre les utilisateurs d’appareils Windows 10 au mode plein écran, ce qui limite les utilisateurs à un ensemble d’applications prédéfinies.  Pour ce faire, créez un profil de restriction d’appareil Windows 10 et définissez les paramètres de plein écran.

Le mode plein écran prend en charge deux modes : **application unique** (permet à l’utilisateur d’exécuter une seule application) ou **applications multiples** (permet l’accès à un ensemble d’applications).  Vous définissez le compte d’utilisateur et le nom de l’appareil, ce qui détermine les applications prises en charge.  Lorsque l’utilisateur est connecté, il est limité aux applications définies.  Pour en savoir plus, consultez [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Conditions requises du mode plein écran :

- Intune doit être l’autorité MDM.
- Les applications doivent déjà être installées sur l’appareil cible.
- L’appareil doit être [correctement provisionné](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries---1311967---"></a>Nouveau profil de configuration d’appareil pour créer des limites réseau<!-- 1311967 -->   
Vous trouverez un nouveau profil de configuration d’appareil appelé **Limite réseau** avec vos autres profils de configuration d’appareil. Utilisez ce profil pour définir des ressources en ligne à considérer comme approuvées et appartenant à l’entreprise. Vous devez définir une limite réseau pour un appareil *avant* de pouvoir utiliser les fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows sur l’appareil. Il est important de définir une seule limite réseau pour chaque appareil.

Vous pouvez définir des ressources cloud d’entreprise, des plages d’adresses IP et des serveurs proxy internes à considérer comme approuvées. Une fois définie, la limite réseau peut être utilisée par d’autres fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows.

### <a name="two-additional-settings-for-windows-defender-antivirus---1338409---"></a>Deux paramètres supplémentaires de l’antivirus Windows Defender<!-- 1338409 -->  
**Niveau de blocage des fichiers**

| | |
|---|---|
| Non configuré | **Non configuré** utilise le niveau de blocage de Windows Defender Antivirus par défaut et offre une détection solide sans augmenter le risque de détection des fichiers légitimes. |
| Importante | **Haut** s’applique à un niveau fort de détection.
| Élevé +  | **Haut +** fournit le niveau Haut avec des mesures de protection supplémentaires pouvant impacter les performances du client.
| Tolérance zéro  | **Tolérance zéro** bloque tous les exécutables inconnus. |

Bien qu’improbable, la définition sur **Haut** risque d’entraîner la détection de certains fichiers légitimes.
Nous vous recommandons de définir le niveau de blocage des fichiers avec la valeur par défaut, **Non configuré**.

**Extension du délai d’attente pour l’analyse des fichiers par le cloud**  

| | |
|--|--|
| Nombre de secondes (0-50) | Spécifiez la durée maximale avant que Windows Defender Antivirus ne bloque un fichier lors de l’attente d’un résultat du cloud. La durée par défaut est de 10 secondes : tout temps supplémentaire spécifié ici (jusqu'à 50 secondes) est ajouté à ces 10 secondes. Dans la plupart des cas, l’analyse prend beaucoup moins de temps que la valeur maximale. Prolonger la durée permet au cloud de rechercher des fichiers suspects de manière plus approfondie. Nous vous recommandons d’activer ce paramètre et de spécifier au moins 20 secondes supplémentaires. |

### <a name="citrix-vpn-added-for-windows-10-devices---1512457---"></a>VPN Citrix ajouté aux appareils Windows 10<!-- 1512457 -->  
Vous pouvez configurer un VPN Citrix pour les appareils Windows 10. Vous pouvez choisir le VPN Citrix dans la liste *Sélectionner un type de connexion* du panneau **VPN de base** quand vous configurez un VPN pour Windows 10 et ultérieur.

> [!Note]
> Une configuration de Citrix existait pour iOS et Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios---1550823---"></a>Les connexions Wi-Fi prennent en charge les clés prépartagées sur iOS<!-- 1550823 -->
Les clients peuvent configurer des profils Wi-Fi pour utiliser des clés prépartagées pour les connexions personnelles WPA/WPA2 sur les appareils iOS. Ces profils sont envoyés à l’appareil de l’utilisateur quand l’appareil est inscrit dans Intune.

Quand le profil a été envoyé à l’appareil, l’étape suivante varie en fonction de la configuration du profil.  S’il est configuré pour se connecter automatiquement, il le fait quand l’accès réseau est nécessaire.  Quand le profil se connecte manuellement, l’utilisateur doit activer la connexion manuellement.  

### <a name="access-to-managed-app-logs-for-ios---1469920---"></a>Accès aux journaux d’applications gérées pour iOS<!-- 1469920 -->
Les utilisateurs finaux disposant de Managed Browser peuvent maintenant afficher l’état de gestion de toutes les applications Microsoft publiées et envoyer des journaux afin de résoudre les problèmes liés à leurs applications iOS gérées.

Pour découvrir comment activer le mode dépannage dans Managed Browser sur un appareil iOS, consultez [Guide pratique pour accéder aux journaux des applications gérées à l’aide de Managed Browser sur iOS](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290---1417174---"></a>Améliorations apportées au workflow de configuration des appareils sur le Portail d’entreprise pour iOS dans la version 2.9.0<!-- 1417174 -->

Le workflow de configuration des appareils a été amélioré dans l’application Portail d’entreprise pour iOS. La langue est plus conviviale, et nous avons regroupé des écrans dans la mesure du possible. La langue est également plus adaptée à l’entreprise, car nous utilisons à chaque fois son nom dans le texte de configuration. Vous pouvez voir ce workflow mis à jour sur la page  [Nouveautés de l’interface utilisateur de l’application](../whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model---1544273---"></a>L’entité Utilisateur contient les données utilisateur les plus récentes dans le modèle de données de l’entrepôt de données<!-- 1544273 -->
La première version du modèle de données de l’entrepôt de données Intune ne contenait que des données Intune historiques récentes. Les auteurs de rapports ne pouvaient pas capturer l’état actuel d’un utilisateur. Dans cette mise à jour, **l’entité Utilisateur** est renseignée avec les données utilisateur les plus récentes.

<!-- ########################## -->
## <a name="october-2017"></a>Octobre 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible---1380712---"></a>Le numéro de version des applications métier iOS et Android est visible<!-- 1380712 -->

Les applications dans Intune affichent désormais le numéro de version des applications métier Android et iOS. Le numéro s’affiche dans le portail Azure, dans la liste des applications et dans le panneau de vue d’ensemble des applications. Les utilisateurs finaux peuvent voir le numéro d’application dans l’application Portail d’entreprise et dans le portail web.

__Numéro de version complet__ Le numéro de version complet identifie une version précise de l’application. Le numéro apparaît sous la forme _Version_(_Build_). Par exemple, 2.2(2.2.17560800)

Le numéro de version complet est composé de deux éléments :

- **Version**  
  Le numéro de version est le numéro de version explicite de l’application. Il est utilisé par les utilisateurs finaux pour identifier les différentes versions de l’application.

- **Numéro de build**  
  Le numéro de build est un numéro interne qui peut être utilisé pour la détection de l’application et pour gérer l’application par programmation. Le numéro de build fait référence à une itération de l’application qui référence les changements apportés au code.

Pour découvrir plus en détail les numéros de version et le développement d’applications métier, consultez [Prise en main du kit SDK d’application Microsoft Intune](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration---677972---"></a>Intégration de la gestion des appareils et des applications<!-- 677972 -->   
Maintenant que la gestion des appareils mobiles (MDM) et la gestion des applications mobiles (MAM) d’Intune sont accessibles à partir du portail Azure, Intune a commencé à intégrer l’expérience d’administrateur informatique dans la gestion des applications et des appareils. Ces changements sont destinés à simplifier votre expérience de la gestion des appareils et des applications.

Découvrez plus en détail les changements de MDM et de MAM annoncés sur le [blog de l’équipe de support Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices---1471790---"></a>Nouvelles alertes d’inscription pour les appareils Apple<!-- 1471790 -->
La page de vue d’ensemble de l’inscription affiche les alertes utiles pour les administrateurs informatiques concernant la gestion des appareils Apple. Des alertes s’affichent dans la page Vue d’ensemble quand le certificat push MDM Apple arrive à expiration ou a déjà expiré ; quand le jeton DEP (Programme d’inscription des appareils) expire ou a déjà expiré ; et en présence d’appareils non affectés dans le programme DEP.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment---1080364---"></a>Prise en charge du remplacement de jeton pour la configuration d’application sans inscription de l’appareil<!-- 1080364 -->

Vous pouvez utiliser des jetons pour les valeurs dynamiques des configurations des applications des appareils qui ne sont pas inscrits. Pour plus d’informations, consultez [Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil](../apps/app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10--1299474--"></a>Mise à jour de l’application Portail d’entreprise pour Windows 10<!--1299474-->
La page Paramètres de l’application Portail d’entreprise pour Windows 10 a été mise à jour pour rendre les paramètres et les actions prévues de l’utilisateur plus cohérents à travers l’ensemble des paramètres, ainsi que pour correspondre à la disposition d’autres applications Windows. Vous trouverez des images avant/après sur la page [Nouveautés de l’interface utilisateur de l’application](../whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices--1337920--"></a>Informer les utilisateurs finaux au sujet des informations consultables concernant les appareils Windows 10<!--1337920-->
Nous avons ajouté **Type de propriété** dans l’écran Détails sur l’appareil de l’application Portail d’entreprise pour Windows 10. Ainsi, les utilisateurs auront accès à de plus amples informations sur la confidentialité directement sur cette page à partir de la documentation utilisateur Intune. Ils les trouveront également sur l’écran **À propos de**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android--1165249--"></a>Invites pour la saisie de commentaires dans l’application Portail d’entreprise pour Android<!--1165249-->
L’application Portail d’entreprise pour Android demande désormais aux utilisateurs finaux d’envoyer leurs commentaires. Ces commentaires sont envoyés directement à Microsoft et permettent aux utilisateurs finaux de passer l’application en revue dans Google Play Store. Le retour d’expérience n’est pas obligatoire et peut être facilement ignoré de façon à continuer d’utiliser l’application.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android---1573324-1573150-1558616-1564878---"></a>Rendre vos utilisateurs autonomes avec l’application Portail d’entreprise pour Android<!-- 1573324, 1573150, 1558616, 1564878 -->

L’application Portail d’entreprise pour Android a ajouté des indications permettant aux utilisateurs finaux de comprendre et, dans la mesure du possible, de résoudre eux-mêmes les nouveaux cas d’usage.
- Les utilisateurs finaux sont redirigés vers le [portail Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) pour supprimer un appareil s’ils ont atteint le nombre maximal d’appareils qu’ils sont autorisés à ajouter.
- Les utilisateurs finaux reçoivent des instructions pour les aider à [corriger les erreurs d’activation sur les appareils Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) ou à [désactiver le mode d’économie d’énergie](/intune-user-help/power-saving-mode-android). Si aucune de ces solutions ne résout leur problème, nous indiquons comment [envoyer les journaux à Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices---1583480---"></a>Nouvelle action « Résoudre » disponible pour les appareils Android<!-- 1583480 -->

L’application Portail d’entreprise pour Android dispose désormais d’une action « Resolve » (Résoudre) sur la page _Mettre à jour les paramètres de l’appareil_. Si l’utilisateur final sélectionne cette option, il sera directement dirigé vers le paramètre à cause duquel son appareil n’est pas conforme. L’application Portail d’entreprise pour Android prend en charge cette action pour les paramètres [Code secret de l’appareil](/intune-user-help/set-your-pin-or-password-android), [Débogage USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) et [Sources inconnues](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal---1565657---"></a>Indicateur de progression de la configuration de l’appareil sur le Portail d’entreprise Android<!-- 1565657 -->
L’application Portail d’entreprise pour Android affiche un indicateur de progression du programme d’installation de l’appareil quand un utilisateur inscrit son appareil. L’indicateur affiche de nouveaux états, qui apparaissent dans l’ordre suivant : « Configuration de votre appareil… », « Inscription de votre appareil... », « Fin de l’inscription de votre appareil... », puis « Fin de la configuration de votre appareil... ».

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios--1029830--"></a>Prise en charge de l’authentification basée sur les certificats sur le Portail d’entreprise pour iOS<!--1029830-->
Nous avons ajouté la prise en charge de l’authentification basée sur un certificat (CBA) dans l’application Portail d’entreprise pour iOS. Les utilisateurs avec cette authentification entrent leur nom d’utilisateur et appuient sur le lien « Se connecter avec un certificat ». L’authentification CBA est déjà prise en charge dans les applications Portail d’entreprise pour Android et Windows. Pour en savoir plus, consultez la page [Comment faire pour se connecter à l’application Portail d’entreprise ?](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment---1334712---"></a>Les applications qui sont disponibles avec ou sans inscription peuvent désormais être installées sans invitation à l’inscription.<!-- 1334712 -->

Les applications d’entreprise qui ont été mises à disposition avec ou sans inscription dans l’application Portail d’entreprise Android peuvent désormais être installées sans invitation à l’inscription.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617----"></a>Prise en charge du programme de déploiement Windows AutoPilot dans Microsoft Intune <!-- 747617  -->
Vous pouvez désormais utiliser Microsoft Intune avec le programme de déploiement Windows AutoPilot pour permettre à vos utilisateurs de provisionner eux-mêmes leurs appareils d’entreprise sans passer par le service informatique. Vous pouvez personnaliser l’expérience OOBE (out-of-box experience) pour permettre aux utilisateurs de joindre leurs appareils à Azure AD et de s’inscrire à Intune. Avec Microsoft Intune et Windows AutoPilot, vous n’avez plus à déployer et à gérer les images de système d’exploitation. Pour plus d’informations, consultez [Inscrire des appareils Windows à l’aide du programme Windows AutoPilot Deployment](../enrollment/enrollment-autopilot.md).

### <a name="quickstart-for-device-enrollment----1425655---"></a>Guide de démarrage rapide pour l’inscription des appareils <!-- 1425655 --> 
Le guide de démarrage rapide, désormais disponible dans **Inscription d’appareils**, fournit un tableau de références pour gérer les plateformes et configurer la procédure d’inscription. Vous trouverez une brève description de chaque élément et des liens vers des instructions pas à pas pour simplifier le démarrage.

### <a name="device-categorization---1427491---"></a>Catégorisation des appareils<!-- 1427491 -->
Le graphique des plateformes des appareils inscrits du panneau **Appareils > Vue d’ensemble** organise les appareils par plateforme (Android, iOS, macOS, Windows, Windows Mobile, etc.).  Les appareils qui exécutent d’autres systèmes d’exploitation sont regroupés dans « Autres ».  Il s’agit des appareils fabriqués par Blackberry, NOKIA, etc.  

Pour identifier les appareils affectés dans votre locataire, choisissez **Gérer > Tous les appareils**, puis utilisez **Filtrer** pour limiter le champ **Système d’exploitation**.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium : nouveau partenaire de Mobile Threat Defense  <!-- 954681 -->  
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Zimperium,solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Déroulement de l’intégration à Intune
Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant Zimperium. Vous pouvez configurer des stratégies d’accès conditionnel EMS basées sur l’évaluation des risques de Zimperium, activée par le biais des stratégies de conformité Intune, que vous pouvez utiliser pour autoriser ou bloquer l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées.

### <a name="new-settings-for-windows-10-device-restriction-profile-----978575-1308849---"></a>Nouveaux paramètres pour le profil de restriction des appareils Windows 10 <!--- 978575, 1308849, -->  
Nous ajoutons de nouveaux paramètres au profil de restriction des appareils Windows 10 dans la catégorie Windows Defender SmartScreen.

Pour obtenir plus d’informations sur le profil de restriction des appareils Windows 10, consultez [Paramètres de restriction des appareils Windows 10 et version ultérieure](../configuration/device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Prise en charge à distance des appareils Windows et Windows Mobile  <!-- 1070473 -->  
Intune peut désormais utiliser le logiciel [TeamViewer](https://www.teamviewer.com), vendu séparément, pour vous permettre de fournir une assistance à distance aux utilisateurs qui utilisent des appareils Windows et Windows Mobile.

### <a name="scan-devices-with-windows-defender---1280988--1280990-----"></a>Analyser les appareils avec Windows Defender<!-- 1280988  1280990   -->
Vous pouvez à présent exécuter une **Analyse rapide**, une **Analyse complète** et **Mettre à jour les signatures** avec l’antivirus Windows Defender sur les appareils Windows 10 gérés. À partir du panneau de présentation de l’appareil, choisissez l’action à exécuter sur l’appareil. Vous êtes invité à confirmer l’action avant l’envoi de la commande à l’appareil. 

**Analyse rapide** : analyse les emplacements où les programmes malveillants s’inscrivent pour démarrer, comme les clés de registre et les dossiers de démarrage Windows connus. Une analyse rapide prend en moyenne cinq minutes. Associée au paramètre **Protection en temps réel toujours activé** qui analyse les fichiers lorsqu’ils sont ouverts, fermés et à chaque fois qu’un utilisateur accède à un dossier, une analyse rapide fournit une protection contre les programmes malveillants qui peuvent se trouver dans le système ou le noyau. Lorsque l’analyse s’achève, ses résultats s’affichent sur les appareils des utilisateurs. 

**Analyse complète** : une analyse complète peut être utile sur les appareils confrontés à une menace issue de programmes malveillants afin de déterminer s’il existe des composants inactifs qui nécessitent un nettoyage plus approfondi. Elle est également utile pour exécuter des analyses à la demande. Une analyse complète peut prendre une heure. Lorsque l’analyse s’achève, ses résultats s’affichent sur les appareils des utilisateurs. 

**Mettre à jour les signatures** : la commande de mise à jour de signature met à jour les définitions et les signatures des programmes malveillants dans l’antivirus Windows Defender. Cela permet de garantir l’efficacité d’Antivirus Windows Defender dans la détection des programmes malveillants. Cette fonctionnalité s’applique uniquement aux appareils Windows 10 et est sujette à la connectivité Internet de l’appareil. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal----1400455---"></a>Le bouton Activer/Désactiver n’est plus disponible sur la page Autorité de certification Intune du Portail Azure Intune <!-- 1400455 -->
 Nous avons enlevé une étape du processus de configuration de Certificate Connector sur Intune. Actuellement, vous téléchargez Certificate Connector et vous l’activez dans la console Intune. Mais si vous le désactivez dans la console Intune, il continue d’émettre des certificats.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
Depuis octobre, le bouton Activer/désactiver n’apparaît plus dans la page Autorité de certification du portail Azure. La fonctionnalité Certificate Connector reste la même. Les certificats sont toujours déployés sur les appareils inscrits à Intune. Vous pouvez continuer à télécharger et à installer Certificate Connector. Pour arrêter l’émission de certificats, vous devez désinstaller Certificate Connector au lieu de le désactiver.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Si Certificate Connector est actuellement désactivé, vous devez le désinstaller.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838---"></a>Nouveaux paramètres pour le profil de restriction d’appareils Windows 10 Collaboration  <!--- 1308838 -->
Dans cette version, nous avons ajouté un grand nombre de nouveaux paramètres au profil de restriction d’appareils Windows 10 Collaboration pour vous permettre de gérer les appareils Surface Hub.

Pour plus d’informations sur ce profil, consultez [Paramètres de restriction d’appareils Windows 10 Collaboration](../configuration/device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Empêcher les utilisateurs d’appareils Android de changer la date et l’heure de leur appareil <!-- 1333292 -->
Vous pouvez utiliser la [stratégie d’appareil personnalisée Android](../configuration/custom-settings-android.md) pour empêcher les utilisateurs d’appareils Android de modifier la date et l’heure de l’appareil.

Pour ce faire, configurez une stratégie personnalisée Android avec le paramètre URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Affectez-lui la valeur **TRUE**, puis attribuez-le aux groupes requis.

### <a name="bitlocker-device-configuration---1397398---"></a>Configuration d’appareil BitLocker<!-- 1397398 -->
Les paramètres **Chiffrement Windows > Paramètres de Base** incluent un nouveau paramètre **Avertissement sur le chiffrement d’un autre disque** qui vous permet de désactiver le [message d’avertissement](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption) sur le chiffrement d’un autre disque qui peut être utilisé sur l’appareil de l’utilisateur.  Le message d’avertissement nécessite le consentement de l’utilisateur final pour configurer BitLocker sur l’appareil et bloque la configuration de BitLocker tant qu’elle n’est pas confirmée par l’utilisateur final.  Le nouveau paramètre désactive l’avertissement pour l’utilisateur final.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant---800882---"></a>Le programme d’achat en volume pour les applications métier est désormais synchronisé avec votre locataire Intune<!-- 800882 -->  
Les développeurs tiers peuvent distribuer des applications en privé aux membres autorisés du programme d’achat en volume (VPP) pour les entreprises. Ces membres du programme d’achat en volume pour les entreprises peuvent se connecter à l’App Store du programme d’achat en volume et acheter leurs applications.

À compter de cette version, les applications du programme d’achat en volume pour les entreprises achetées par l’utilisateur final sont désormais synchronisées avec leurs locataires Intune.

### <a name="select-apple-countryregion-store-to-sync-vpp-apps----1332311---"></a>Sélectionner un magasin Apple du pays/de la région pour synchroniser les applications VPP <!-- 1332311 -->  
Vous pouvez configurer le magasin du pays/de la région pour le programme d’achat en volume (VPP) lors du chargement de votre jeton VPP. Intune synchronise les applications VPP pour tous les paramètres régionaux à partir du magasin du pays/de la région VPP spécifié(e).

> [!NOTE]  
> Actuellement, Intune synchronise uniquement les applications VPP à partir du magasin du pays/de la région VPP qui correspond aux paramètres régionaux Intune avec lesquels le client Intune a été créé.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work---1098994---"></a>Bloquer la copie et le collage entre les profils professionnels et personnels dans Android for Work<!-- 1098994 -->
Avec cette version, vous pouvez configurer le profil professionnel Android for Work afin qu’il bloque la copie et le collage entre les applications professionnelles et personnelles. Vous trouverez ce nouveau paramètre dans le profil **Restrictions d’appareils** pour la plateforme **Android for Work** dans **Paramètres du profil professionnel**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores---1281692---"></a>Créer des applications iOS limitées à des App Stores Apple locaux spécifiques<!-- 1281692 -->
Vous pourrez spécifier les paramètres du pays/de la région lors de la création d’une application managée App Store Apple.

> [!Note]  
> Actuellement, vous pouvez uniquement créer des applications gérées par l’App Store d’Apple qui sont présentes dans le Store de l’état/de la région des États-Unis.

### <a name="update-ios-vpp-user-and-device-licensed-apps----1305564---"></a>Mettre à jour les applications sous licence pour l’appareil et l’utilisateur VPP iOS <!-- 1305564 -->  
Vous pourrez configurer le jeton VPP iOS pour mettre à jour toutes les applications achetées pour ce jeton via le service Intune. Intune détecte les mises à jour des applications VPP dans le magasin d’applications et les envoie (Push) automatiquement vers l’appareil lorsque ce dernier se connecte.

Pour savoir comment définir un jeton VPP et activer les mises à jour automatiques, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model---1187917---"></a>Collection d’entités Association appareil-utilisateur ajoutée au modèle de données de l’entrepôt de données Intune<!-- 1187917 -->
Vous pouvez désormais générer des rapports et des visualisations des données en utilisant les informations d’association appareil-utilisateur qui associent les collections d’entité utilisateur et appareil. Le modèle de données est accessible par le biais du fichier Power BI (PBIX) extrait de la page Intune Data Warehouse, via le point de terminaison OData, ou en développant un client personnalisé.

### <a name="review-policy-compliance-for-windows-10-update-rings---1067886---"></a>Vérifier la conformité de la stratégie pour les anneaux de mise à jour Windows 10<!-- 1067886 -->
Vous pouvez consulter un rapport sur la stratégie pour vos boucles de mise à jour de Windows 10 à partir de Mises à jour logicielles > État de déploiement par boucle de mise à jour. Le rapport sur la stratégie inclut l’état du déploiement pour les boucles de mise à jour que vous avez configurées. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions-----1352223---"></a>Nouveau rapport répertoriant les appareils iOS équipés d’anciennes versions de l’iOS  <!-- 1352223 -->
Le rapport **Appareils iOS obsolètes** est disponible à partir de l’espace de travail **Mises à jour logicielles**. Dans ce rapport, vous pouvez afficher la liste des appareils iOS supervisés qui ont été ciblés par une stratégie de mise à jour iOS, et pour lesquels des mises à jour sont disponibles. Pour chaque appareil, vous pouvez afficher un état indiquant la raison pour laquelle l’appareil n’a pas été automatiquement mis à jour. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Afficher les attributions de la stratégie de protection des applications pour résoudre les problèmes<!--  1475003 -->
Dans cette version à venir, l’option **Stratégie de protection des applications** sera ajoutée à la liste déroulante **Affectations** disponible dans le panneau de résolution des problèmes. Vous pouvez maintenant sélectionner des stratégies de protection des applications pour afficher les stratégies de protection des applications affectées aux utilisateurs sélectionnés.



### <a name="improvements-to-device-setup-workflow-in-company-portal--1490692--"></a>Améliorations apportées au workflow de configuration des appareils dans le Portail d’entreprise<!--1490692-->
Nous avons amélioré le workflow de configuration des appareils dans l’application Portail d’entreprise pour Android. Le texte de l’interface est plus convivial et spécifique à votre entreprise, et nous avons regroupé des écrans quand cela était possible. Vous pouvez voir ces derniers sur la page [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices--1484985--"></a>Amélioration de l’aide concernant la demande d’accès aux contacts sur les appareils Android<!--1484985-->

L’application Portail d’entreprise pour Android nécessite souvent que l’utilisateur final accepte l’autorisation pour permettre l’accès des contacts. Si un utilisateur final refuse cet accès, il voit désormais une notification dans l’application qui lui indique d’accorder l’autorisation pour l’accès conditionnel. 

### <a name="secure-startup-remediation-for-android--1490712--"></a>Correction du démarrage sécurisé pour Android<!--1490712-->

Les utilisateurs finaux d’appareils Android pourront désormais cliquer sur le motif de non-conformité dans l’application Portail d’entreprise. Lorsque possible, ils accéderont directement à l’emplacement approprié dans l’application Paramètres pour résoudre le problème. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo--1475932--"></a>Notifications Push supplémentaires pour les utilisateurs finaux sur l’application Portail d’entreprise pour Android Oreo<!--1475932-->

Les utilisateurs finaux verront des notifications supplémentaires leur indiquant si l’application Portail d’entreprise pour Android Oreo effectue des tâches en arrière-plan, par exemple récupérer des stratégies auprès du service Intune. La transparence s’en trouve améliorée pour les utilisateurs finaux, qui savent quand le Portail d’entreprise effectue des tâches d’administration sur leur appareil. Cela fait partie de [l’optimisation générale de l’interface utilisateur du Portail d’entreprise](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune), et en particulier de l’application Portail d’entreprise pour Android Oreo. 

Vous verrez d’autres optimisations relatives aux nouveaux éléments d’interface utilisateur dans Oreo Android.  Les utilisateurs finaux voient des notifications supplémentaires qui leur indiquent quand le portail d’entreprise effectue des tâches en arrière-plan, comme la récupération d’une stratégie auprès du service Intune.  La transparence s’en trouve améliorée pour les utilisateurs finaux, qui savent quand le portail d’entreprise effectue des tâches d’administration sur l’appareil.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles---1485783---"></a>Nouveaux comportements de l’application Portail d’entreprise pour Android avec les profils professionnels<!-- 1485783 -->

Quand vous inscrivez un appareil Android for Work avec un profil professionnel, c’est l’application Portail d’entreprise dans le profil professionnel qui effectue les tâches de gestion sur l’appareil. 

À moins que vous n’utilisiez une application GAM dans le profil personnel, l’application Portail d’entreprise pour Android n’a plus d’utilité. Pour améliorer l’expérience de profil professionnel, Intune masquera automatiquement l’application Portail d’entreprise personnelle après une inscription de profil professionnel réussie.

L’application Portail d’entreprise pour Android peut être activée à tout moment dans le profil personnel en recherchant [Portail d’entreprise dans le Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et en appuyant sur **Activer**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode--1428681--"></a>Portail d’entreprise pour Windows 8.1 et Windows Phone 8.1 désormais simplement maintenu<!--1428681-->

À partir d’octobre 2017, les applications Portail d’entreprise pour Windows 8.1 et Windows Phone 8.1 seront simplement maintenues. Cela signifie que les applications et les scénarios existants, tels que l’inscription et la conformité, continueront d’être pris en charge pour ces plateformes. Ces applications pourront toujours être téléchargées par le biais des canaux de distribution existants, tels que Microsoft Store. 

Une fois en mode soutenu, ces applications recevront uniquement les mises à jour de sécurité critiques. Il n’y aura aucune mise à jour supplémentaire ou nouvelle fonctionnalité disponible pour ces applications. Pour bénéficier des nouvelles fonctionnalités, nous vous recommandons de mettre à jour vos appareils vers Windows 10 ou Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Bloquer l’inscription des appareils Samsung Knox non pris en charge <!-- 1490695 -->

L’application Portail d’entreprise tente uniquement d’inscrire des appareils Samsung Knox pris en charge. Pour éviter les erreurs d’activation Knox qui empêchent l’inscription à MDM, l’inscription des appareils est tentée seulement si l’appareil apparaît dans la [liste des appareils publiée par Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Les appareils Samsung peuvent avoir des numéros de modèles qui prennent en charge Knox, alors que d’autres ne le prennent pas en charge. Vérifiez la compatibilité de votre appareil avec Knox auprès de votre revendeur avant de l’acheter et de le déployer. Vous pouvez trouver la liste complète des appareils vérifiés dans les [paramètres de stratégie Android et Samsung Knox Standard](supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower---1171126-1326920---"></a>Fin du support pour Android 4.3 et versions antérieures<!-- 1171126, 1326920 -->
Les applications gérées et l’application Portail d’entreprise pour Android nécessiteront Android 4.4 et ultérieur pour accéder aux ressources de l’entreprise. En décembre, tous les appareils inscrits seront obligatoirement mis hors service et perdront l’accès aux ressources de l’entreprise. Si vous utilisez des stratégies de protection des applications sans MDM, les applications ne recevront aucune mise à jour et perdront en qualité au fil du temps.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices--1165314--"></a>Informer les utilisateurs finaux au sujet des informations concernant leurs appareils consultables sur les appareils inscrits<!--1165314-->
Nous sommes en train d’ajouter le **Type de propriété** à l’écran Détails de l’appareil sur toutes les applications Portail d’entreprise. Les utilisateurs pourront ainsi en savoir plus sur la confidentialité directement à partir de l’article [Quelles informations mon entreprise peut-elle voir quand j’inscris mon appareil ?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) Cette nouveauté sera introduite dans toutes les applications Portail d’entreprise dans un futur proche. Nous l’avons annoncé pour iOS en [septembre](#september-2017).

<!-- ########################## -->
## <a name="september-2017"></a>Septembre 2017

### <a name="intune-supports-ios-11--1428975--"></a>Intune prend en charge iOS 11<!--1428975-->
Intune prend en charge iOS 11. Ceci avait été annoncé sur le [blog du support technique Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80---1164477---"></a>Fin du support d’iOS 8.0<!-- 1164477 -->
Les applications gérées et l’application Portail d’entreprise pour iOS nécessiteront iOS 9.0 ou une version ultérieure pour accéder aux ressources de l’entreprise. Les appareils qui ne sont pas mis à jour avant septembre ne seront plus en mesure d’accéder au portail d’entreprise ni à ces applications. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10--1132468--"></a>Action d’actualisation ajoutée à l’application Portail d’entreprise pour Windows 10<!--1132468-->
L’application Portail d’entreprise pour Windows 10 permet aux utilisateurs d’actualiser les données dans l’application avec une requête Pull pour actualiser ou, sur les postes de travail, en appuyant sur F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios--739894--"></a>Informer les utilisateurs finaux au sujet des informations concernant leurs appareils consultables sur iOS<!--739894-->

Nous avons ajouté l’information **Type de propriété** dans l’écran des détails de l’appareil qui se trouve sur l’application Portail d’entreprise pour iOS. Ainsi, les utilisateurs auront accès à de plus amples informations sur la confidentialité directement sur cette page à partir de la documentation utilisateur Intune. Ils les trouveront également sur l’écran À propos de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment---1169910---"></a>Autoriser les utilisateurs finaux à accéder à l’application Portail d’entreprise pour Android sans inscription<!---1169910--->

Les utilisateurs finaux n’auront bientôt pas à inscrire leur appareil pour accéder à l’application Portail d’entreprise pour Android. Les utilisateurs finaux des organisations qui utilisent des stratégies de protection des applications ne recevront plus d’invites pour inscrire leur appareil quand ils ouvriront l’application Portail d’entreprise. Les utilisateurs finaux pourront également installer des applications à partir du portail d’entreprise sans inscrire l’appareil. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android---1396349---"></a>Formulation plus facile à comprendre pour l’application Portail d’entreprise pour Android<!---1396349--->  

Le processus d’inscription des utilisateurs finaux sur l’application Portail d’entreprise pour Android a été simplifié grâce à de nouveaux textes. Si vous disposez d’une documentation personnalisée sur l’inscription, mettez-la à jour pour voir les nouveaux écrans. Vous trouverez des exemples d’images sur notre page [Mises à jour de l’interface utilisateur des applications Intune pour utilisateur final](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy---677129---"></a>Application Portail d’entreprise Windows 10 ajoutée à la stratégie d’autorisation Protection des informations Windows<!-- 677129 -->

L’application Portail d’entreprise Windows 10 a été mise à jour pour prendre en charge la Protection des informations Windows. L’application peut être ajoutée à la stratégie d’autorisation Protection des informations Windows. Avec cette modification, il n’est plus nécessaire d’ajouter l’application à la liste **Exempt**.


<!-- ########################## -->
## <a name="august-2017"></a>Août 2017

### <a name="improvements-to-device-overview---1404453---"></a>Vue d’ensemble des améliorations apportées à l’appareil<!-- 1404453 -->  
La vue d’ensemble des améliorations apportées à l’appareil affiche à présent les appareils inscrits mais exclut les appareils gérés par Exchange ActiveSync. Les appareils Exchange ActiveSync n’ont pas les mêmes options de gestion que les appareils inscrits. Pour afficher le nombre d’appareils inscrits et le nombre d’appareils inscrits par plateforme dans le portail Azure d’Intune, accédez à **Appareils** > **Vue d’ensemble**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Améliorations apportées à l’inventaire des appareils collecté par Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
Dans cette version, nous avons apporté les améliorations suivantes aux informations d’inventaire collectées par les appareils que vous gérez :
 
- Pour les appareils Android, vous pouvez maintenant ajouter une colonne à l’inventaire des appareils qui affiche le dernier niveau de correctif logiciel pour chaque appareil. Ajoutez la colonne **Niveau du correctif de sécurité** à votre liste d’appareils pour afficher cette information.
- Quand vous filtrez la vue des appareils, vous pouvez désormais filtrer les appareils sur leur date d’inscription. Par exemple, vous pouvez afficher uniquement les appareils qui ont été inscrits après une date que vous spécifiez.
- Nous avons apporté des améliorations au filtre utilisé par l’élément **Date du dernier archivage**.
- Dans la liste des appareils, vous pouvez maintenant afficher le numéro de téléphone d’appareils appartenant à l’entreprise.
En outre, vous pouvez utiliser le volet de filtre pour rechercher des appareils par numéro de téléphone.

Pour plus d’informations sur l’inventaire des appareils, consultez [Guide d’affichage de l’inventaire des appareils Intune](../remote-actions/device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Prise en charge de l’accès conditionnel pour les appareils macOS 
<!-- 720172 -->
Vous pouvez maintenant définir une stratégie d’accès conditionnel exigeant que les appareils Mac soient inscrits dans Intune et conformes à ses stratégies de conformité des appareils. Par exemple, les utilisateurs peuvent télécharger l’application Portail d’entreprise Intune pour macOS et inscrire leurs appareils Mac dans Intune. Intune évalue si l’appareil Mac est conforme ou non aux spécifications telles que le code PIN, le chiffrement, la version du système d’exploitation et l’intégrité du système.

- Découvrez plus en détail la [prise en charge de l’accès conditionnel pour les appareils macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview---1484796---"></a>L’application Portail d’entreprise pour macOS est en préversion publique<!---1484796--->
L’application Portail d’entreprise pour macOS est désormais disponible dans la préversion publique pour l’accès conditionnel dans Enterprise Mobility + Security. Cette version prend en charge macOS 10.11 et ultérieur. Obtenez-la à l’adresse [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10    
<!--1063965, 1308850  -->
Dans cette version, nous avons ajouté de nouveaux paramètres pour le [profil de restriction d’appareil Windows 10](/intune/device-restrictions-windows-10) dans les catégories suivantes :

- Windows Defender SmartScreen
- App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Mises à jour du profil d’appareil Endpoint Protection Windows 10 pour les paramètres BitLocker
<!--1459533 -->    
Dans cette version, nous avons apporté les améliorations suivantes au fonctionnement des paramètres BitLocker dans un profil d’appareil Endpoint Protection Windows 10 :
 
- Sous **Paramètres des lecteurs de système d’exploitation BitLocker**, pour le paramètre **BitLocker avec puce TPM non compatible**, quand vous sélectionniez **Bloquer**, auparavant, BitLocker aurait en fait été autorisé. Nous avons maintenant résolu ce problème pour bloquer BitLocker quand cette option est sélectionnée.
- Sous **Paramètres des lecteurs de système d’exploitation BitLocker**, pour le paramètre **Agent de récupération de données basé sur les certificats**, vous pouvez maintenant bloquer explicitement l’agent de récupération de données basé sur le certificat. Toutefois, par défaut, l’agent est autorisé.
- Sous **Paramètres des lecteurs de données fixes BitLocker**, pour le paramètre **Agent de récupération de données**, vous pouvez maintenant bloquer explicitement l’agent de récupération de données.
Pour plus d’informations, consultez [Paramètres Endpoint Protection pour Windows 10 et versions ultérieures](../protect/endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users---621669---"></a>Nouvelle expérience de connexion pour les utilisateurs du Portail d’entreprise Android et les utilisateurs de stratégies de protection des applications<!-- 621669 -->
Les utilisateurs peuvent maintenant parcourir les applications, gérer les appareils et consulter les coordonnées du service informatique sur l’application du Portail d’entreprise Android sans inscrire leurs appareils Android. En outre, s’ils utilisent déjà une application protégée par les stratégies Intune App Protection et lancent le Portail d’entreprise Android, ils ne sont plus invités à inscrire l’appareil.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization--1405990--"></a>Nouveau paramètre dans l’application Portail d’entreprise Android pour activer/désactiver l’optimisation de batterie<!--1405990-->
La page **Paramètres** dans l’application Portail d’entreprise pour Android propose un nouveau paramètre qui permet aux utilisateurs de désactiver facilement l’optimisation de batterie pour les applications Portail d’entreprise et Microsoft Authenticator. Le nom de l’application qui est indiqué dans le paramètre varie en fonction de l’application qui gère le compte professionnel. Nous préconisons aux utilisateurs de désactiver l’optimisation de batterie pour améliorer les performances des applications professionnelles qui synchronisent les e-mails et les données. 

### <a name="multi-identity-support-for-onenote-for-ios--------1234281---"></a>Prise en charge de plusieurs identités dans OneNote pour iOS     <!-- 1234281 -->
Les utilisateurs finaux peuvent désormais utiliser des comptes différents (professionnels et personnels) avec Microsoft OneNote pour iOS. Il est possible d’appliquer des stratégies de protection des applications à des données d’entreprise dans des blocs-notes professionnels sans affecter leurs blocs-notes personnels. Par exemple, une stratégie peut autoriser un utilisateur à rechercher des informations dans des blocs-notes de travail, mais l’empêcher de copier et de coller des données d’entreprise du bloc-notes professionnel vers un bloc-notes personnel.
 
- En savoir plus sur les applications qui prennent en charge [la protection d’application et les identités multiples](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) avec Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nouveaux paramètres pour autoriser et bloquer des applications sur les appareils Samsung Knox Standard
<!-- 1305423 822899-->  
Dans cette version, nous ajoutons de nouveaux [paramètres de restriction des appareils](../configuration/device-restrictions-android.md) qui vous permettent de spécifier les listes d’applications suivantes :
 
- Applications que les utilisateurs sont autorisés à installer
- Applications dont l’exécution est bloquée pour les utilisateurs
- Applications qui sont masquées pour l’utilisateur sur l’appareil
 
Vous pouvez spécifier l’application par URL, par nom de package ou à partir de la liste des applications que vous gérez.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Lien vers la nouvelle interface utilisateur des stratégies d’accès conditionnel basé sur l’application Azure AD à partir d’Intune
<!-- 1016201 -->
Les administrateurs informatiques peuvent définir des stratégies conditionnelles basées sur l’application par le biais de la nouvelle interface utilisateur des stratégies d’accès conditionnel dans la charge de travail Azure AD. L’accès conditionnel basé sur l’application qui se trouve dans la section Protection d’application Intune dans Azure restera à cet endroit pour l’instant et sera appliqué côte à côte. Par souci pratique, un lien est également prévu vers la nouvelle interface utilisateur des stratégies d’accès conditionnel dans la charge de travail Intune.

- Découvrez plus en détail [l’accès conditionnel basé sur l’application sur Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

<!-- ########################## -->
## <a name="july-2017"></a>Juillet 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256--1245463----"></a>Restriction d’inscription d’appareils Android et iOS en fonctions des versions du système d’exploitation <!--- 1333256,  1245463 --->
Intune prend désormais en charge la restriction d’inscription d’appareils Android et iOS par numéro de version de système d’exploitation. Sous **Restriction de type d’appareil**, l’administrateur informatique peut désormais définir une configuration de plateforme pour restreindre l’inscription à une plage de valeurs de système d’exploitation minimale et maximale. Les versions du système d’exploitation Android doivent être spécifiées au format Majeure.Mineure.Build.Révision, où Mineure, Build et Révision sont facultatifs. Les versions d’iOS doivent être spécifiées au format Majeure.Mineure.Build, où Build est facultatif. Découvrez plus d’informations sur les [restrictions d’inscription d’appareils](../enrollment/enrollment-restrictions-set.md).

>[!NOTE]
>Ne limite pas l’inscription avec des programmes d’inscription Apple ou Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272--1333275-1245709----"></a>Limiter l’inscription des appareils personnels Android, iOS et macOS <!--- 1333272,  1333275, 1245709 --->
Intune peut limiter l’inscription d’appareils personnels avec des listes vertes de numéros IMEI d’appareils d’entreprise. Intune a récemment étendu cette fonctionnalité à iOS, Android et macOS avec des numéros de série d’appareils. En chargeant les numéros de série sur Intune, vous pouvez prédéclarer des appareils comme appartenant à l’entreprise. Les restrictions d’inscription vous permettent de bloquer les appareils personnels (BYOD), ce qui permet l’inscription des appareils de l’entreprise uniquement. Découvrez plus d’informations sur les [restrictions d’inscription d’appareils](../enrollment/enrollment-restrictions-set.md).

Pour importer des numéros de série, accédez à **Inscription d’appareil** > **Identificateurs d’appareil d’entreprise** et cliquez sur **Ajouter**, puis chargez un fichier .CSV (pas d’en-tête, deux colonnes pour le numéro de série et des détails comme les numéros IMEI). Pour restreindre les appareils personnels, accédez à **Inscription d’appareil** > **Restrictions d’inscription**. Sous **Restrictions de type d’appareil**, sélectionnez **Par défaut**, puis **Configurations de plateforme**. Vous pouvez **Autoriser** ou **Bloquer** les appareils personnels pour iOS, Android et macOS.


### <a name="new-device-action-to-force-devices-to-sync-with-intune---711369---"></a>Nouvelle action d’appareil pour forcer les périphériques à se synchroniser avec Intune<!-- 711369 -->
Dans cette version, nous avons ajouté une nouvelle action qui force l’appareil sélectionné à s’enregistrer immédiatement auprès d’Intune. Quand un appareil s’enregistre, il reçoit immédiatement les actions ou les stratégies en attente qui lui ont été affectées.  Cette action peut vous aider à valider et corriger immédiatement les stratégies que vous avez affectées, sans attendre le prochain enregistrement planifié.
Pour plus d’informations, consultez [Synchroniser un appareil](../remote-actions/device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update---777100---"></a>Forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour logicielle disponible<!-- 777100 -->
Une nouvelle stratégie est disponible dans l’espace de travail des mises à jour logicielles, qui vous permet de forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour logicielle disponible. Pour plus d’informations, consultez [Configurer les stratégies de mise à jour iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile : nouveau partenaire de Mobile Threat Defense <!-- 954651, 1172027 -->
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise avec un accès conditionnel basé sur une évaluation des risques effectuée par CheckPoint SandBlast Mobile, qui est une solution de protection contre les menaces mobiles qui s’intègre à Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Déroulement de l’intégration à Intune
Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant CheckPoint SandBlast Mobile. Vous pouvez configurer des stratégies d’accès conditionnel EMS basées sur l’évaluation des risques de CheckPoint SandBlast Mobile, activée par le biais des stratégies de conformité Intune. Vous pouvez autoriser ou bloquer l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business---748101---"></a>Déployer une application en tant qu’application disponible dans le Microsoft Store pour Entreprises<!-- 748101 -->
Avec cette version, les administrateurs peuvent désormais indiquer que le Microsoft Store pour Entreprises est disponible. Quand il est déclaré disponible, les utilisateurs finaux peuvent installer l’application à partir de l’application ou du site web Portail d’entreprise sans être redirigé vers le Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website--1313244-part-1--"></a>Mises à jour apportées à l’interface utilisateur sur le site web Portail d’entreprise<!--1313244 part 1-->
Nous avons procédé à quelques mises à jour sur l’interface utilisateur du [site Web Portail d’entreprise](https://portal.manage.microsoft.com) pour améliorer l’expérience de l’utilisateur final.

- __Améliorations apportées aux vignettes des applications__ :  des icônes d’application s’affichent désormais avec un arrière-plan généré automatiquement en fonction de la couleur dominante de l’icône (si elle peut être détectée). Quand il est applicable, cet arrière-plan remplace la bordure grise qui apparaissaît sur les vignettes des applications.

    Dans une prochaine version, le site web Portail d’entreprise affichera des grandes icônes quand cela sera possible. Nous recommandons aux administrateurs informatiques de publier des applications en utilisant des icônes d’une taille minimale de 120 x 120 pixels. 

- __Modifications de la navigation__ : les éléments de la barre de navigation sont déplacés dans le menu hamburger situé en haut à gauche. La page Catégories est supprimée. Les utilisateurs peuvent désormais filtrer le contenu par catégorie lors de l’exploration.

- __Mises à jour des applications proposées__ : Nous avons ajouté une page dédiée sur le site où les utilisateurs peuvent rechercher les applications que vous avez choisi de proposer, et nous avons apporté quelques ajustements à l’interface utilisateur de la section correspondante sur la page d’accueil.

### <a name="ibooks-support-for-the-company-portal-website--1231841--"></a>Prise en charge des iBooks par le site web Portail d’entreprise<!--1231841-->
Nous avons ajouté une page dédiée au site web Portail d'entreprise qui permet aux utilisateurs de parcourir et de télécharger des iBooks. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Détails supplémentaires de résolution des problèmes du support technique<!---  Applies to 1263399, 1326964, 1341642 --->
Intune a mis à jour l’affichage de la résolution des problèmes et a ajouté aux informations qu’il fournit des informations pour les administrateurs et le personnel du support technique. Vous pouvez maintenant voir un tableau **Attributions** qui récapitule toutes les attributions de l’utilisateur en fonction de l’appartenance au groupe. La liste comprend :
- Applications mobiles
- Stratégies de conformité
- Profils de configuration

Par ailleurs, le tableau **Appareils** inclut désormais les colonnes **Type de jointure Azure AD** et **Conforme Azure AD**. Pour plus d’informations, consultez [Aider les utilisateurs à résoudre les problèmes](../help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Entrepôt de données Intune (préversion publique)
L’entrepôt de données Intune échantillonne quotidiennement les données pour fournir une vue historique de votre locataire. Vous pouvez accéder aux données via un fichier Power BI (PBIX), via un lien OData qui est compatible avec de nombreux outils analytiques ou en interagissant avec l’API REST. Pour plus d’informations, consultez [Utiliser l’entrepôt de données Intune](../developer/reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10---676547---"></a>Modes clair et sombre disponibles pour l’application Portail d’entreprise pour Windows 10<!---676547--->
Les utilisateurs finaux seront en mesure de personnaliser le mode de couleur de l’application Portail d’entreprise pour Windows 10. Ils pourront apporter la modification dans la section Paramètres de l’application Portail d’entreprise. Le changement apparaîtra une fois que les utilisateurs auront redémarré l’application. Pour Windows 10 versions 1607 et ultérieures, le mode des applications est par défaut le paramètre système. Pour Windows 10 versions 1511 et antérieures, le mode des applications est par défaut le mode clair.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10---807046--"></a>Permettre aux utilisateurs finaux d’étiqueter leur groupe d’appareils dans l’application Portail d’entreprise pour Windows 10<!---807046-->
Les utilisateurs finaux peuvent désormais sélectionner le groupe auquel leur appareil appartient, en le balisant directement à partir de l’application Portail d’entreprise pour Windows 10.

<!-- ########################## -->
## <a name="june-2017"></a>Juin 2017

### <a name="new-role-based-administration-access-for-intune-admins-----1099990---"></a>Nouvel accès à l’administration basée sur les rôles pour les administrateurs Intune  <!-- 1099990 -->  
Un nouveau rôle d’administrateur d’accès conditionnel est ajouté pour afficher, créer, modifier et supprimer des stratégies d’accès conditionnel dans Azure AD. Auparavant, seuls les administrateurs de sécurité et les administrateurs globaux disposaient de cette autorisation. Les administrateurs Intune peuvent obtenir cette autorisation de rôle afin d’avoir accès aux stratégies d’accès conditionnel.


### <a name="tag-corporate-owned-devices-with-serial-number---1215070---"></a>Étiqueter les appareils d’entreprise avec un numéro de série<!-- 1215070 -->  
Intune prend désormais en charge le chargement de numéros de série iOS, macOS et Android en tant qu’identificateurs d’appareil d’entreprise. Vous ne pouvez pas utiliser les numéros de série pour empêcher des appareils personnels de s’inscrire pour le moment, car les numéros de série ne sont pas vérifiés lors de l’inscription. Le blocage des appareils personnels par numéro de série sera disponible dans un futur proche.


### <a name="new-remote-actions-for-ios-devices---854689---"></a>Nouvelles actions à distance pour les appareils iOS<!-- 854689 -->
Dans cette version, nous avons ajouté deux actions à distance pour les appareils iPad partagés qui gèrent l’application Apple Classroom :

- [Déconnecter l’utilisateur actuel](../remote-actions/device-logout-user.md) : déconnecte l’utilisateur actuel de l’appareil iOS de votre choix.
- [Supprimer l’utilisateur](../remote-actions/device-remove-user.md) : supprime un utilisateur que vous choisissez dans le cache local sur un appareil iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app---1044681---"></a>Prise en charge des iPad partagés à l’aide de l’application iOS Classroom<!-- 1044681 -->
Dans cette version, nous avons développé la prise en charge de la gestion de l’application Classroom iOS afin d’inclure les étudiants qui se connectent à des iPad partagés à l’aide de leur ID Apple géré.


### <a name="changes-to-intune-built-in-apps---1332306---"></a>Modifications apportées aux applications intégrées Intune<!-- 1332306 -->
Intune contenait auparavant un nombre d’applications intégrées que vous pouviez affecter rapidement. En réponse à vos commentaires, nous avons supprimé cette liste et ces applications intégrées n’apparaîtront plus.
Toutefois, si vous avez déjà affecté des applications intégrées, elles resteront visibles dans la liste des applications. Vous pouvez continuer à affecter ces applications en fonction de vos besoins.
Dans une version ultérieure, nous prévoyons d’ajouter une méthode plus simple pour sélectionner et affecter les applications intégrées à partir du portail Azure.

### <a name="easier-installation-of-office-365-apps----1121362----"></a>Installation simplifiée des applications Office 365<!--- 1121362 --->
À l’aide du nouveau type d’application **Office 365 ProPlus**, vous pouvez affecter facilement des applications Office 365 ProPlus 2016 aux appareils que vous gérez et qui exécutent la dernière version de Windows 10. Vous pouvez également installer Microsoft Project et Microsoft Visio si vous disposez des licences appropriées. Les applications souhaitées sont regroupées et apparaissent sous la forme d’une application unique dans la liste des applications de la console Intune.
Pour plus d’informations, consultez [Guide pratique pour ajouter des applications Office 365 pour Windows 10](../apps/apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business----777044----"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises<!--- 777044 --->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez alors déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications en mode hors connexion sont installées par Intune et non par le Store.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps-----1257019---"></a>Les équipes Microsoft font désormais partie de la liste d’applications approuvées des Autorités de certification basée sur l’application  <!-- 1257019 -->
L’application Microsoft Teams pour iOS et Android fait désormais partie des applications approuvées pour les stratégies d’accès conditionnel basé sur l’application pour Exchange et SharePoint Online. L’application peut être configurée via le panneau Intune App Protection dans le portail Azure pour tous les clients utilisant actuellement l’accès conditionnel basé sur l’application.

### <a name="managed-browser-and-app-proxy-integration---1287310---"></a>Intégration de Managed Browser et du proxy d’application<!-- 1287310 -->
Intune Managed Browser peut maintenant s’intégrer au service du proxy d’application Azure AD pour permettre aux utilisateurs d’accéder aux sites web internes même quand ils travaillent à distance. Les utilisateurs du navigateur entrent simplement l’URL du site comme ils le font normalement et Managed Browser achemine la demande via la passerelle web du proxy d’application. Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser](../apps/app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser---682951---"></a>Nouveaux paramètres de configuration d’application pour Intune Managed Browser<!-- 682951 -->
Dans cette version, nous avons ajouté des configurations supplémentaires pour l’application Intune Managed Browser pour iOS et Android. Vous pouvez maintenant utiliser une stratégie de configuration d’application pour configurer la page d’accueil par défaut et les signets du navigateur.
Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser](../apps/app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10----951707---"></a>Paramètres BitLocker pour Windows 10 <!-- 951707 -->
Vous pouvez maintenant configurer des paramètres BitLocker pour les appareils Windows 10 à l’aide d’un nouveau profil d’appareil Intune. Par exemple, vous pouvez exiger que les appareils soient chiffrés et configurer également d’autres paramètres qui sont appliqués quand BitLocker est activé.
Pour plus d’informations, consultez [Paramètres Endpoint Protection pour Windows 10 et versions ultérieures](../protect/endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile----978527--978550-978569-1050031-1058611-----"></a>Nouveaux paramètres pour le profil de restriction des appareils Windows 10<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
Dans cette version, nous avons ajouté de nouveaux paramètres pour le profil de restriction d’appareil Windows 10 dans les catégories suivantes :

- Windows Defender
- Cellulaire et connectivité
- Expérience d’écran de verrouillage
- Confidentialité
- Recherche
- Windows à la une
- Navigateur Microsoft Edge

Pour plus d’informations sur les paramètres Windows 10, consultez [Paramètres de restriction des appareils Windows 10 et versions ultérieures](../configuration/device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies--1305217--"></a>L’application Portail d’entreprise pour Android présente désormais une nouvelle expérience d’utilisateur final pour les stratégies de protection des applications<!--1305217-->
En fonction des commentaires des clients, nous avons modifié l’application Portail d’entreprise pour Android afin d’afficher un bouton **Accéder au contenu de l’entreprise**. L’objectif est d’empêcher les utilisateurs finaux d’avoir à passer par le processus d’inscription lorsqu’ils ont seulement besoin d’accéder aux applications qui prennent en charge les stratégies de protection des applications, une fonctionnalité de gestion des applications mobiles d’Intune. Vous pouvez afficher ces modifications dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal--1164569--"></a>Nouvelle action de menu pour supprimer facilement le Portail d’entreprise<!--1164569-->
Suite aux commentaires des utilisateurs, l’application Portail d’entreprise pour Android offre désormais une nouvelle action de menu pour lancer la suppression du portail d’entreprise à partir de votre appareil. Cette action supprime l’appareil de gestion Intune afin que l’application puisse être supprimée de l’appareil par l’utilisateur. Vous pouvez voir ces modifications sur la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md) et dans la [documentation pour les utilisateurs finaux d’Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update--676505--"></a>Améliorations apportées à la synchronisation des applications avec Windows 10 Creators Update<!--676505-->
L’application Portail d’entreprise pour Windows 10 démarre maintenant automatiquement une synchronisation pour les demandes d’installation d’application sur les appareils exécutant Windows 10 Creators Update (version 1703). Cela permet de réduire le problème de blocage des installations d’applications à l’état « Synchronisation en attente ». En outre, les utilisateurs pourront lancer manuellement une synchronisation à partir de l’application. Vous pouvez afficher ces modifications dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal---1058938---"></a>Nouvelle expérience interactive pour le Portail d’entreprise Windows 10<!---1058938--->
L’application Portail d’entreprise pour Windows 10 inclura une expérience de procédure pas à pas Intune interactive pour les appareils qui n’ont pas été identifiés ou inscrits. La nouvelle expérience fournit des instructions détaillées qui guident les utilisateurs lors de l’inscription à Azure Active Directory (requis pour les fonctionnalités d’accès conditionnel) et de l’inscription MDM (obligatoire pour les fonctionnalités de gestion des appareils). L’expérience guidée sera accessible à partir de la page d’accueil de portail d’entreprise. Les utilisateurs peuvent continuer à utiliser l’application s’ils ne terminent pas l’inscription, mais seront confrontés à des fonctionnalités limitées.

Cette mise à jour est visible uniquement sur les appareils exécutant la Mise à jour anniversaire Windows 10 (build 1607) ou version ultérieure. Vous pouvez afficher ces modifications dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Les consoles d’administration Microsoft Intune et d’accès conditionnel sont généralement disponibles
Nous annonçons la disponibilité générale de la nouvelle console d’administration Intune dans le portail Azure et de la console d’administration d’accès conditionnel. Via Intune dans le portail Azure, vous pouvez désormais gérer toutes les fonctionnalités MAM et MDM Intune dans une expérience d’administration consolidée et tirer parti du regroupement et du ciblage d’Azure AD. L’accès conditionnel dans Azure apporte des fonctionnalités riches sur Azure AD et Intune dans une console unifiée. Et niveau expérience d’administration, la migration vers la plateforme Azure vous permet d’utiliser les navigateurs modernes.

Intune est désormais visible sans l’étiquette **Préversion** dans le portail Azure sur portal.azure.com.

Aucune action n’est requise pour les clients existants à ce stade, sauf si vous avez reçu une série de messages dans le centre de message vous demandant d’agir afin que nous puissions faire migrer vos groupes. Vous avez peut-être également reçu un avis du centre de messages vous informant que la migration prenait plus de temps en raison de bogues de notre côté. Nous allons continuer à travailler sans relâche pour migrer les clients concernés.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Améliorations des vignettes de l’application dans l’application Portail d’entreprise pour iOS
Nous avons mis à jour l’apparence des vignettes d’application sur la page d’accueil afin de refléter la couleur de marque que vous définissez pour le portail d’entreprise. Pour en savoir plus, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Un sélecteur de compte est désormais disponible dans l’application Portail d’entreprise pour iOS
Les utilisateurs d’appareils iOS peuvent voir notre nouveau sélecteur de compte lorsqu’ils se connectent au portail d’entreprise s’ils utilisent leur compte professionnel ou scolaire pour se connecter à d’autres applications Microsoft. Pour en savoir plus, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

<!-- ########################## -->
## <a name="may-2017"></a>Mai 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices--1103950--"></a>Changer votre autorité de gestion des périphériques mobiles sans annuler l’inscription des appareils gérés<!--1103950-->
Vous pouvez maintenant changer votre autorité de gestion des appareils mobiles sans avoir à contacter le Support Microsoft et sans avoir à annuler l’inscription et à réinscrire vos appareils gérés existants. Dans la console Configuration Manager, vous pouvez faire basculer votre autorité de gestion des appareils mobiles de Définir sur Configuration Manager (hybride) à Microsoft Intune (autonome), ou inversement.


### <a name="improved-notification-for-samsung-knox-startup-pins--1087143--"></a>Notification améliorée pour les codes PIN de démarrage Samsung Knox<!--1087143-->
Quand les utilisateurs finaux doivent définir un code PIN de démarrage sur les appareils Samsung Knox pour être compatibles avec le chiffrement, la notification affichée aux utilisateurs finaux les mène à l’emplacement exact dans l’application Paramètres lors de l’appui sur la notification.  Auparavant, la notification menait l’utilisateur final à l’écran de modification de mot de passe.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="apple-school-manager-asm-support-with-shared-ipad---748864-770395--"></a>Prise en charge d’Apple School Manager (ASM) avec iPad partagé<!-- 748864, 770395-->

Intune prend maintenant en charge l’utilisation d’Apple School Manager (ASM) à la place du Programme d’inscription d’appareils Apple pour fournir l’inscription des appareils iOS par défaut. L’intégration d’ASM est nécessaire pour utiliser l’application Classroom pour les iPad partagés et pour permettre la synchronisation des données d’ASM vers Azure Active Directory par l’intermédiaire de Microsoft School Data Sync (SDS). Pour plus d’informations, consultez [Activer l’inscription des appareils iOS avec Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md).

> [!NOTE]
> La configuration d’iPad partagés pour travailler avec l’application Classroom requiert des configurations d’éducation iOS dans Azure qui ne sont pas encore disponibles.  Cette fonctionnalité sera bientôt disponible.

### <a name="device-management"></a>Gestion des périphériques

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer---675418---"></a>Fournir une assistance à distance sur des appareils Android à l’aide de TeamViewer<!-- 675418 -->

Intune peut maintenant utiliser le logiciel [TeamViewer](https://www.teamviewer.com), vendu séparément, pour vous permettre de fournir une assistance à distance aux utilisateurs qui utilisent des appareils Android. Pour plus d’informations, consultez [Fournir une assistance à distance pour les appareils Android gérés par Intune](../remote-actions/teamviewer-support.md).

### <a name="app-management"></a>Gestion des applications

#### <a name="new-app-protection-policies-conditions-for-mam---679864---"></a>Nouvelles conditions de stratégies de protection des applications pour la gestion des applications mobiles<!-- 679864 -->

Vous pouvez maintenant définir un ensemble de spécifications de GAM pour les utilisateurs sans inscription qui applique les éléments suivants :

- Version minimale de l’application
- Version minimale du système d’exploitation
- Version minimale du SDK d’application Intune de l’application cible (iOS uniquement)

Cette fonctionnalité est disponible sur iOS et Android. Intune prend en charge l’application de la version minimale pour les versions de plateformes de système d’exploitation, les versions d’applications et le SDK d’application Intune. Sur iOS, les applications intégrées au SDK peuvent également définir l’application de la version minimale au niveau du SDK. L’utilisateur ne peut pas accéder à l’application cible si la configuration minimale requise par la stratégie de protection des applications n’est pas satisfaite aux trois niveaux différents mentionnés ci-dessus. À ce stade, l’utilisateur peut supprimer son compte (pour les applications à plusieurs identités), fermer l’application et/ou mettre à jour la version de son système d’exploitation ou de l’application.

De plus, vous pouvez configurer des paramètres supplémentaires pour fournir une notification non bloquante qui recommande une mise à niveau du système d’exploitation ou de l’application. Cette notification peut être fermée et l’application peut être utilisée normalement.

Pour plus d’informations, consultez les [paramètres de stratégie de protection des applications iOS](../apps/app-protection-policy-settings-ios.md) et les [paramètres de stratégie de protection des applications Android](../apps/app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work---621621---"></a>Configurer les configurations d’application pour Android for Work<!-- 621621 -->
Certaines applications Android du Store prennent en charge des options de configuration gérées qui permettent à un administrateur informatique de contrôler la façon dont une application s’exécute dans le profil de travail. Avec Intune, vous pouvez désormais afficher les configurations prises en charge par une application et les configurer à partir du portail Azure avec un concepteur de configuration ou dans un éditeur JSON. Pour plus d’informations, consultez [Utiliser des configurations d’application pour Android for Work](../apps/app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment---677969---"></a>Nouvelle fonctionnalité de configuration d’application pour la gestion des applications mobiles sans inscription<!-- 677969 -->
Vous pouvez désormais créer des stratégies de configuration d’application via la gestion des applications mobiles sans canal d’inscription. Cette fonctionnalité équivaut aux stratégies de configuration d’application disponibles dans la configuration de l’application de Gestion des appareils mobiles (MDM). Pour un exemple de configuration d’application avec gestion des applications mobiles sans inscription, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser---682960---"></a>Configurer des listes d’URL autorisées et bloquées pour Managed Browser<!-- 682960 -->
Vous pouvez désormais configurer une liste de domaines et d’URL autorisés et bloqués pour Intune Managed Browser avec les paramètres de configuration d’application dans le portail Azure. Vous pouvez configurer ces paramètres même s’il est utilisé sur un appareil non géré. Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view---1069473---"></a>Vue du support technique pour les stratégies de protection des applications<!-- 1069473 -->
Les utilisateurs du support technique informatique peuvent désormais vérifier l’état des licences utilisateur et l’état des applications de stratégie de protection d’application affectées aux utilisateurs dans le panneau de la résolution des problèmes. Pour plus d’informations, consultez [Résolution des problèmes](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="control-website-visits-on-ios-devices---723832---"></a>Contrôler les visites de site web sur les appareils iOS<!-- 723832 -->
Vous pouvez maintenant contrôler les sites web auxquels les utilisateurs d’appareils iOS peuvent accéder à l’aide de l’une des deux méthodes suivantes :

- Ajouter des URL autorisées et bloquées à l’aide du filtrage de contenu web intégré d’Apple.

- Autoriser uniquement l’accès aux sites web spécifiés par le navigateur Safari. Des signets sont créés dans Safari pour chaque site que vous spécifiez.

Pour plus d’informations, consultez [Paramètres de filtre de contenu web pour les appareils iOS](../configuration/ios-device-features-settings.md#web-content-filter).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps---621614---"></a>Préconfigurer les autorisations d’appareils pour les applications Android for Work<!-- 621614 -->
Pour les applications déployées sur des profils professionnels Android for Work, vous pouvez maintenant configurer l’état des autorisations pour chacune des applications.  Par défaut, les applications Android qui nécessitent des autorisations d’appareils telles que l’accès à l’emplacement ou à l’appareil photo invitent les utilisateurs à accepter ou à refuser les autorisations.  Par exemple, si une application utilise le microphone de l’appareil, l’utilisateur final est invité à autoriser l’application à utiliser le microphone. Cette fonctionnalité vous permet de définir des autorisations pour le compte de l’utilisateur final.  Vous pouvez configurer des autorisations pour a) refuser automatiquement sans en avertir l’utilisateur, b) automatiquement approuver sans en avertir l’utilisateur, ou c) inviter l’utilisateur à accepter ou refuser. Pour plus d’informations, consultez [Paramètres de restriction des appareils Android for Work dans Microsoft Intune](../configuration/device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices---728976-1102534---"></a>Définir un code PIN propre à l’application pour les appareils Android for Work<!-- 728976, 1102534 -->
Vous pouvez définir une stratégie de mot de passe qui s’applique uniquement aux applications dans le profil professionnel pour les appareils Android 7.0 et versions ultérieures avec un profil de travail géré en tant qu’appareil Android for Work.  Les options sont les suivantes :

- Définir simplement une stratégie de mot de passe au niveau de l’appareil : il s’agit du code secret que l’utilisateur final doit utiliser pour déverrouiller son appareil.
- Définir simplement une stratégie de mot de passe de profil professionnel : les utilisateurs sont invités à entrer un code secret chaque fois qu’une application dans le profil professionnel est ouverte.
- Définir à la fois une stratégie d’appareil et une stratégie de profil professionnel : l’administrateur informatique peut définir à la fois une stratégie de code secret d’appareil et une stratégie de code secret de profil professionnel à des niveaux différents (par exemple, un code PIN à quatre chiffres pour déverrouiller l’appareil, mais un code PIN à six chiffres pour ouvrir une application professionnelle).

Pour plus d’informations, consultez [Paramètres de restriction des appareils Android for Work dans Microsoft Intune](../configuration/device-restrictions-android-for-work.md).

> [!NOTE]
> Cette fonctionnalité est uniquement disponible sur Android 7.0 et versions ultérieures.  Par défaut, l’utilisateur final peut utiliser les deux codes PIN définis séparément, ou il peut choisir de combiner les deux codes PIN définis dans le plus sécurisé des deux.

#### <a name="new-settings-for-windows-10-devices---978585---"></a>Nouveaux paramètres des appareils Windows 10<!-- 978585 -->
Nous avons ajouté [de nouveaux paramètres de restriction d’appareil Windows](../configuration/device-restrictions-windows-10.md) qui contrôlent des fonctionnalités telles que les affichages sans fil, la détection des appareils, le basculement de tâche et les messages d’erreur de carte SIM.

#### <a name="updates-to-certificate-configuration---918991-and-823198---"></a>Mises à jour de la configuration de certificat<!-- 918991 and 823198 -->
Lors de la création d’un profil de certificat SCEP, l’option <strong>Personnalisé</strong> option est disponible pour <strong>Format du nom du sujet</strong> sur les appareils iOS, Android et Windows. Avant cette mise à jour, le champ <strong>Personnalisé</strong> était disponible pour les appareils iOS uniquement. Pour plus d’informations, consultez [Create a SCEP certificate profile](../protect/certificates-profile-scep.md) (Créer un profil de certificat SCEP).

Lors de la création d’un profil de certificat PKCS, pour **Autre nom de l’objet**, **Attribut personnalisé Azure AD** est disponible. L’option **Service** est disponible lorsque vous sélectionnez **Attribut personnalisé Azure AD**. Pour plus d’informations, consultez [Créer un profil de certificat PKCS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode---662059---"></a>Configurer plusieurs applications pouvant s’exécuter lorsqu’un appareil Android est en mode plein écran<!-- 662059 -->
Lorsqu’un appareil Android est en mode plein écran, vous ne pouviez précédemment configurer qu’une application autorisée à s’exécuter. Vous pouvez désormais configurer plusieurs applications à l’aide de l’ID d’application ou de l’URL du Store, ou en sélectionnant une application Android que vous gérez déjà. Pour plus d’informations, consultez [Paramètres du mode plein écran](../configuration/device-restrictions-android.md#kiosk).

<!-- ########################## -->
## <a name="april-2017"></a>Avril 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Prise en charge de la gestion de l’application Apple Classroom
Vous pouvez désormais gérer l’application iOS Classroom sur des appareils iPad. Configurez l’application Classroom sur l’iPad des enseignants avec les données sur les étudiants et les cours appropriées, puis configurez les iPad des étudiants inscrits à un cours, afin que vous puissiez les contrôler à l’aide de l’application.
Pour plus d’informations, consultez [Configurer les paramètres d’éducation iOS](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps---621621---"></a>Les applications Android prennent en charge les options de configuration gérées<!-- 621621 -->
Les applications Android du Play Store qui prennent en charge les options de configuration gérées peuvent désormais être configurées par Intune.  Cette fonctionnalité permet au personnel informatique d’afficher la liste des valeurs de configuration prises en charge par une application, et fournit une interface interactive et guidée de premier plan pour lui permettre de configurer ces valeurs.

### <a name="new-android-policy-for-complex-pins---722069---"></a>Nouvelle stratégie Android pour les codes PIN complexes<!-- 722069 -->
Vous pouvez maintenant définir un type de [mot de passe](../configuration/device-restrictions-android.md#password) requis « Chiffres complexes » dans un profil d’appareil Android pour les appareils qui exécutent Android 5.0 et versions ultérieures.  Utilisez ce paramètre pour empêcher les utilisateurs d’appareils de créer un code PIN qui contient des nombres répétés ou consécutifs, tel que 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Prise en charge supplémentaire des appareils Android for Work
- **Gérer les paramètres de profil professionnel et le mot de passe**<!-- 612808 -->

  Cette nouvelle stratégie de restriction d’appareil Android for Work vous permet maintenant de gérer les paramètres de profil professionnel et de mot de passe sur les appareils Android for Work que vous gérez.

- **Autoriser le partage de données entre les profils personnels et professionnels**<!-- 1045102 -->

Ce profil de restriction d’appareil Android for Work a été enrichi de nouvelles options afin de vous aider à configurer le partage de données entre vos profils personnels et professionnels.

- **Limiter la copie et le collage entre les profils professionnels et personnels**<!-- 1046094 -->

  Ce nouveau profil d’appareil personnalisé pour les appareils Android for Work vous permet de désormais limiter les actions Copier et Coller entre applications professionnelles et personnelles.

Pour plus d’informations, consultez [Device restrictions for Android for Work](../configuration/device-restrictions-android-for-work.md) (Restrictions d’appareils pour Android for Work).

### <a name="assign-lob-apps-to-ios-and-android-devices---1057568---"></a>Attribuer des applications métier à des appareils iOS et Android<!-- 1057568 -->
Vous pouvez désormais affecter des applications métier pour [iOS](../apps/lob-apps-ios.md) (fichiers .ipa) et [Android](../apps/lob-apps-android.md) (fichiers .apk) à des utilisateurs ou des appareils.


### <a name="new-device-policies-for-ios---723774-723815-723826-723830---"></a>Nouvelles stratégies d’appareil pour iOS<!-- 723774, 723815, 723826, 723830 -->
- **Applications dans l’écran d’accueil** : contrôle les applications qui s’affichent dans [l’écran d’accueil de l’appareil iOS](../configuration/ios-device-features-settings.md#home-screen-layout) d’un utilisateur. Cette stratégie change la disposition de l’écran d’accueil, mais ne déploie aucune application.

- **Connexions aux appareils AirPrint** : contrôle les [appareils AirPrint](../configuration/ios-device-features-settings.md#airprint) (imprimantes réseau) auxquels les utilisateurs finaux d’appareils iOS peuvent se connecter.

- **Connexions aux appareils AirPlay** : contrôle les [appareils AirPlay](../configuration/ios-device-features-settings.md) (comme Apple TV) auxquels les utilisateurs finaux d’appareils iOS peuvent se connecter.

- **Message d’écran de verrouillage personnalisé** : permet de configurer un message personnalisé qui s’affiche sur l’écran de verrouillage des appareils iOS à la place du message d’écran de verrouillage par défaut. Pour plus d’informations, consultez [Activer le mode Perdu sur les appareils iOS](../remote-actions/device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps---723767---"></a>Restreindre les notifications Push sur les applications iOS<!-- 723767 -->
Dans un profil de restriction d’appareil Intune, vous pouvez maintenant configurer les [paramètres de notification](../configuration/ios-device-features-settings.md#app-notifications) suivants pour les appareils iOS :

- Activer ou désactiver entièrement la notification pour une application spécifiée.
- Activer ou désactiver la notification dans le Centre de notification pour une application spécifiée.
- Spécifier le type d’alerte : **Aucune**, **Bannière** ou **Alerte modale**.
- Spécifier si les badges sont autorisés pour cette application.
- Spécifier si les sons de notification sont autorisés.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously---737837---"></a>Configurer les applications iOS pour qu’elles s’exécutent de manière autonome en mode Application unique<!-- 737837 -->
Vous pouvez désormais utiliser un profil d’appareil Intune pour configurer les appareils iOS pour qu’ils exécutent les applications spécifiées en [mode Application unique autonome](../configuration/device-restrictions-ios.md#autonomous-single-app-mode). Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé et il ne peut exécuter que cette application. Vous pouvez par exemple utiliser ce mode quand vous configurez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices---723765---"></a>Configurer des domaines approuvés pour la messagerie et la navigation web sur des appareils iOS<!-- 723765 -->
À partir d’un profil de restriction d’appareil iOS, vous pouvez maintenant configurer les [paramètres de domaine suivants](../configuration/device-restrictions-ios.md#domains) :

- **Domaines d’e-mail non marqués** - Les e-mails reçus ou envoyés par l’utilisateur qui ne correspondent pas aux domaines que vous spécifiez ici sont marqués comme non approuvés.

- **Domaines web gérés** - Les documents téléchargés à partir des URL que vous spécifiez ici sont considérés comme gérés (Safari uniquement).  

- **Domaines de remplissage automatique des mots de passe Safari** - Les utilisateurs peuvent enregistrer des mots de passe dans Safari uniquement à partir des URL qui correspondent aux modèles que vous spécifiez ici. Pour utiliser ce paramètre, il faut que l’appareil soit en mode supervisé et non configuré pour plusieurs utilisateurs. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal---748782---"></a>Applications VPP disponibles dans le Portail d’entreprise iOS<!-- 748782 -->
Vous pouvez désormais affecter des applications achetées en volume (VPP) iOS comme installations **disponibles** pour les utilisateurs finaux. Ces derniers auront besoin d’un compte Apple Store pour installer l’application.

### <a name="synchronize-ebooks-from-apple-vpp-store---800878---"></a>Synchroniser des livres électroniques depuis l’Apple VPP Store<!-- 800878 -->
Vous pouvez maintenant [synchroniser les livres](../apps/vpp-apps-ios.md) que vous avez achetés dans le Store VPP (Programme d’achat en volume) d’Apple avec Intune, et les attribuer à des utilisateurs.

### <a name="multi-user-management-for-samsung-knox-standard-devices---971988---"></a>Gestion des utilisateurs multiples sur les appareils Samsung Knox Standard<!-- 971988 -->
Les appareils qui exécutent Samsung Knox Standard sont désormais pris en charge pour la [gestion des utilisateurs multiples](../enrollment/android-enroll.md) par Intune. Cela signifie que les utilisateurs finaux peuvent se connecter et se déconnecter de l’appareil avec leurs informations d’identification Azure Active Directory, et que l’appareil est géré de façon centralisée qu’il soit en cours d’utilisation ou non.  Quand les utilisateurs finaux se connectent, ils ont accès aux applications et les éventuelles stratégies sont appliquées à ces applications. Quand les utilisateurs se déconnectent, toutes les données d’application sont effacées.

### <a name="additional-windows-device-restriction-settings---818566---"></a>Paramètres de restriction d’appareil Windows supplémentaires<!-- 818566 -->
Nous avons ajouté la prise en charge d’autres [paramètres de restriction d’appareil Windows](../configuration/device-restrictions-windows-10.md), comme une prise en charge supplémentaire du navigateur Microsoft Edge, la personnalisation de l’écran de verrouillage d’appareil, la personnalisation du menu Démarrer, les papiers peints Windows à la une et les paramètres de proxy.

### <a name="multi-user-support-for-windows-10-creators-update---822547---"></a>Prise en charge multi-utilisateur pour Windows 10 Creators Update<!-- 822547 -->
Nous avons ajouté la prise en charge de la [gestion des utilisateurs multiples](../enrollment/windows-enroll.md) pour les appareils qui exécutent Windows 10 Creators Update et sont joints à un domaine Azure Active Directory. Cela signifie que quand différents utilisateurs standard se connectent à l’appareil avec leurs informations d’identification Azure AD, ils reçoivent les applications et les stratégies qui ont été affectées à leur nom d’utilisateur. Les utilisateurs ne peuvent actuellement pas utiliser le portail d’entreprise pour les scénarios de libre-service tels que l’installation d’applications.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start pour les PC Windows 10<!-- 1004830 -->
Une nouvelle [action d’appareil Fresh Start](../remote-actions/device-fresh-start.md) est maintenant disponible pour les PC Windows 10.  Quand vous exécutez cette action, les applications qui ont été installées sur l’ordinateur sont supprimées, et le PC est automatiquement mis à jour vers la dernière version de Windows. Vous pouvez ainsi supprimer des applications OEM préinstallées, comme celles qui sont souvent fournies avec un nouveau PC. Vous pouvez configurer si les données utilisateur sont conservées quand cette action est exécutée sur l’appareil.

### <a name="additional-windows-10-upgrade-paths---903672---"></a>Chemins de mise à niveau Windows 10 supplémentaires<!-- 903672 -->
Vous pouvez désormais créer une [stratégie de mise à niveau d’édition pour mettre à niveau les appareils](../configuration/edition-upgrade-configure-windows-10.md) vers les éditions Windows 10 supplémentaires suivantes :

- Windows 10 Professionnel
- Windows 10 Professionnel N
- Windows 10 Professionnel Éducation
- Windows 10 Professionnel Éducation N

### <a name="bulk-enroll-windows-10-devices---747607---"></a>Inscription en bloc des appareils Windows 10<!-- 747607 -->
Vous pouvez désormais joindre un grand nombre d’appareils qui exécutent la mise à jour Windows 10 Creators pour Azure Active Directory et Intune à l’aide du Concepteur de configuration Windows (WCD). Pour activer [l’inscription MDM en bloc](../enrollment/windows-bulk-enroll.md) pour votre client Azure AD, créez un package de configuration qui joint les appareils à votre client Azure AD à l’aide du Concepteur de configuration Windows, puis appliquez le package aux appareils d’entreprise que vous souhaitez inscrire et gérer en bloc. Une fois le package appliqué à vos appareils, ceux-ci se connectent à Azure AD, s’inscrivent dans Intune et vos utilisateurs Azure AD peuvent s’y connecter.  Les utilisateurs d’Azure AD agissent sur ces appareils en tant qu’utilisateurs standard ; ils reçoivent les stratégies qui leur sont affectées ainsi que les applications dont ils ont besoin. Les scénarios de libre-service et de portail d’entreprise ne sont pas pris en charge actuellement.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations---581122-736644---"></a>Nouveaux paramètres de gestion des applications mobiles pour les codes PIN et les emplacements de stockage géré<!-- 581122, 736644 -->
Deux nouveaux paramètres d’application sont désormais disponibles pour vous aider dans les scénarios de gestion des applications mobiles (GAM) :

- **Désactiver le code PIN de l’application quand le code PIN de l’appareil est géré** - Détecte si un code PIN d’appareil est présent sur l’appareil inscrit et, si c’est le cas, contourne le code PIN de l’application déclenché par les stratégies de protection des applications. Ce paramètre permet de réduire le nombre d’invites de code PIN pour les utilisateurs ouvrant une application GAM sur un appareil inscrit. Cette fonctionnalité est disponible pour iOS et Android.

- **Sélectionnez dans quels services de stockage les données d’entreprise peuvent être enregistrées** - Permet de spécifier les emplacements de stockage où enregistrer les données d’entreprise. Les utilisateurs peuvent enregistrer dans les services d’emplacement de stockage sélectionnés, ce qui signifie que tous les autres services d’emplacement de stockage non répertoriés seront bloqués.

  Liste des services d’emplacement de stockage pris en charge :

  - OneDrive Entreprise
  - SharePoint Online
  - Stockage local

### <a name="help-desk-troubleshooting-portal---907448---"></a>Portail de dépannage du centre de support technique<!-- 907448 -->
Le nouveau [portail de dépannage](../help-desk-operators.md) permet aux opérateurs du centre de support technique et aux administrateurs Intune de visualiser les utilisateurs et leurs appareils, et d’effectuer des tâches pour résoudre les problèmes techniques liés à Intune.

<!-- ########################## -->
## <a name="march-2017"></a>Mars 2017

### <a name="support-for-ios-lost-mode--431695--"></a>Prise en charge du mode Perdu iOS<!--431695-->
Pour les appareils iOS 9.3 et versions ultérieures, Intune a ajouté la prise en charge du **Mode Perdu**. Vous pouvez maintenant verrouiller un appareil pour éviter toute utilisation et afficher un numéro de téléphone de contact et un message sur l’écran de verrouillage de l’appareil.

L’utilisateur final ne peut pas déverrouiller l’appareil tant qu’un administrateur n’a pas désactivé le mode Perdu. Lorsque le mode Perdu est activé, vous pouvez utiliser l’action **Localiser l’appareil** pour afficher l’emplacement géographique de l’appareil sur une carte dans la console Intune.

L’appareil doit être un appareil iOS d’entreprise, inscrit via le programme DEP, qui est en mode supervisé.

Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](../remote-actions/device-management.md)

### <a name="improvements-to-device-actions-report--677150--"></a>Améliorations apportées au rapport Actions de l’appareil<!--677150-->
Nous avons apporté des améliorations au rapport Actions de l’appareil afin d’optimiser les performances. En outre, il est désormais possible de filtrer le rapport par état. Par exemple, vous pouvez filtrer le rapport pour qu’il affiche uniquement les actions d’appareil qui ont été effectuées.

### <a name="custom-app-categories--748805--"></a>Catégories d’applications personnalisées<!--748805-->
Vous pouvez désormais créer, modifier et attribuer des catégories pour les applications que vous ajoutez à Intune. Actuellement, les catégories ne peuvent être spécifiées qu'en anglais.
Consultez [Guide pratique pour ajouter une application à Intune](../apps/apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices--748823--"></a>Attribuer des applications métier aux utilisateurs disposant d’appareils non inscrits<!--748823-->
Vous pouvez désormais attribuer aux utilisateurs des applications cœur de métier à partir du Store, que leurs appareils soient ou non inscrits auprès d’Intune. Si l’appareil n’est pas inscrit auprès de Intune, l’utilisateur doit se rendre sur le site web du portail d’entreprise, au lieu de l’application du portail d’entreprise, pour l’installer.

### <a name="new-compliance-reports--846671--"></a>Nouveaux rapports de conformité<!--846671-->
Vous disposez désormais de rapports de conformité qui vous indiquent la situation de conformité des appareils de votre société et vous permettent de résoudre rapidement les problèmes liés à la conformité rencontrés par vos utilisateurs. Vous pouvez visualiser des informations sur les éléments suivants :

- État de conformité global des appareils
- État de conformité d’un paramètre spécifique
- État de conformité d’une stratégie spécifique

Vous pouvez également utiliser ces rapports pour explorer les détails d’un appareil individuel afin de visualiser les paramètres et stratégies spécifiques affectant cet appareil.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios--951869--"></a>Accès direct aux scénarios d’inscription d’Apple<!--951869-->
Pour les comptes Intune créés après janvier 2017, Intune a activé un accès direct aux scénarios d’inscription Apple à l’aide de la charge de travail Inscrire des appareils dans le portail Azure. Auparavant, la version préliminaire de l’inscription Apple était uniquement accessible à partir de liens dans le portail Azure. Les comptes Intune créés avant janvier 2017 nécessiteront une migration unique pour que ces fonctionnalités deviennent disponibles dans Azure. La planification de la migration n’a pas encore été annoncée, mais les détails correspondants seront diffusés dès que possible. Si votre compte existant ne peut pas accéder à la version préliminaire, nous vous recommandons vivement de créer un compte d’évaluation afin de tester la nouvelle expérience.


<!-- ########################## -->
## <a name="february-2017"></a>Février 2017

### <a name="ability-to-restrict-mobile-device-enrollment--747600-795782--"></a>Possibilité de limiter l’inscription des appareils mobiles<!--747600, 795782-->
Intune ajoute de nouvelles restrictions d’inscription qui contrôlent les plateformes d’appareils mobiles autorisées à être inscrites. Intune sépare les plateformes d’appareils mobiles comme iOS, MacOS, Android, Windows et Windows Mobile.

- La restriction de l’inscription d’appareils mobiles ne limite pas l’inscription des clients de PC.  
- Pour iOS et Android uniquement, il existe une option supplémentaire pour bloquer l’inscription des appareils personnels.

Intune marque tous les nouveaux appareils comme personnels, sauf si l’administrateur prend des mesures pour les marquer comme appareils d’entreprise, comme expliqué dans [cet article](../enrollment/device-enrollment.md).

### <a name="view-all-actions-on-managed-devices--677150--"></a>Afficher toutes les actions sur les appareils gérés<!--677150-->
Un nouveau rapport __Actions de l’appareil__ indique l’utilisateur qui a effectué des actions à distance, comme un rétablissement des paramètres d’usine sur les appareils, et montre également l’état de cette action. Consultez [Qu’est-ce que la gestion des appareils ?](../remote-actions/device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps--664691--"></a>Les appareils non gérés peuvent accéder aux applications attribuées<!--664691-->
Dans le cadre des modifications conceptuelles du site web du portail d’entreprise, les utilisateurs iOS et Android peuvent installer les applications attribuées indiquées comme « disponibles sans inscription » sur leurs appareils non gérés. À l’aide de leurs informations d’identification Intune, les utilisateurs peuvent se connecter au site web du portail d’entreprise et afficher la liste des applications qui leur sont attribuées. Les packages des applications « disponibles sans inscription » peuvent être téléchargés sur le site web du portail d’entreprise. Les applications dont l’installation nécessite une inscription ne sont pas affectées par cette modification, car les utilisateurs sont invités à inscrire leur appareil s’ils souhaitent installer ces applications.

### <a name="custom-app-categories--748805--"></a>Catégories d’applications personnalisées<!--748805-->
Vous pouvez désormais créer, modifier et attribuer des catégories pour les applications que vous ajoutez à Intune. Actuellement, les catégories ne peuvent être spécifiées qu'en anglais.
Consultez [Guide pratique pour ajouter une application à Intune](../apps/apps-add.md).

### <a name="display-device-categories--814654--"></a>Afficher les catégories d’appareils<!--814654-->
Vous pouvez maintenant afficher la catégorie d’appareil sous forme de colonne dans la liste des appareils. Vous pouvez également modifier la catégorie dans la section des propriétés du panneau Propriétés de l’appareil. Consultez [Guide pratique pour ajouter une application à Intune](../apps/apps-add.md).

### <a name="configure-windows-update-for-business-settings--776716--"></a>Configurer les paramètres Windows Update for Business<!--776716-->

Windows en tant que service est la nouvelle façon de fournir des mises à jour pour Windows 10. À partir de Windows 10, les nouvelles mises à jour de fonctionnalités et qualité incluent le contenu de toutes les mises à jour précédentes. Cela signifie que tant que vous avez installé la dernière mise à jour, vous savez que vos appareils Windows 10 sont entièrement à jour. À la différence des versions précédentes de Windows, vous devez maintenant installer la mise à jour complète au lieu d’une partie seulement.

En utilisant Windows Update for Business, vous pouvez simplifier l’expérience de gestion des mises à jour et vous ne devez plus approuver des mises à jour propres à des groupes d’appareils. Vous pouvez toujours gérer les risques dans votre environnement en configurant une stratégie de déploiement de mises à jour afin que Windows Update fasse en sorte que les mises à jour soient installées au moment opportun. Microsoft Intune permet de configurer les paramètres de mise à jour des appareils et vous donne la possibilité de reporter l’installation des mises à jour. Intune ne stocke pas les mises à jour, seulement l’attribution des stratégies de mise à jour. Les appareils accèdent directement à Windows Update. Utilisez Intune pour configurer et gérer les **anneaux de mise à jour Windows 10**. Un anneau de mise à jour contient un groupe de paramètres permettant de configurer le moment et la façon d’installer les mises à jour Windows 10. Pour plus d’informations, consultez [Configurer les paramètres Windows Update for Business](../protect/windows-update-for-business-configure.md).
