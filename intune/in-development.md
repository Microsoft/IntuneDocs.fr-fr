---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587380"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>En développement pour Microsoft Intune - Avril 2019

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

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Définir les paramètres de connexion et contrôler les options de redémarrage sur les appareils macOS <!-- 1210083 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). De nouveaux paramètres de fenêtre de connexion vont inclure des éléments comme l’affichage d’une bannière personnalisée, le choix de la façon dont les utilisateurs se connectent, l’affichage ou le masquage des paramètres d’alimentation, etc.

Pour voir les paramètres actuels, accédez à [Paramètres des fonctionnalités des appareils macOS](macos-device-features-settings.md).

S’applique à : macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Paramètres avancés pour le pare-feu Windows Defender <!-- 1311949 -->
Vous serez bientôt en mesure d’utiliser Intune pour gérer les règles de pare-feu personnalisées sur les clients pour Windows Defender. Les règles peuvent spécifier le comportement du trafic entrant et sortant avec les applications, les adresses réseau et les ports. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Exiger l’accès conditionnel de protection des applications  <!--1634317 -->
Vous serez en mesure d’utiliser *Exiger une stratégie de protection des applications*, qui vérifie qu’une stratégie est appliquée à l’application d’un utilisateur avant la fin du processus de connexion, de façon à empêcher les utilisateurs d’accéder aux données que vous protégez avec l’accès conditionnel. Si la vérification de l’application de la stratégie peut ralentir l’expérience de la première utilisation, elle vous protège contre les problèmes réseau, les erreurs de configuration de l’administration ou les actions intentionnelles pour déjouer les stratégies de protection des applications. 

### <a name="retire-noncompliant-devices----1827291---"></a>Mettre hors service les appareils non conformes <!-- 1827291 -->
Nous allons ajouter une nouvelle action de conformité pour mettre hors service un appareil non conforme. La mise hors service d’un appareil non conforme supprime toutes les données de l’entreprise et met fin à la gestion de l’appareil par Intune. Cette action s’exécute quand la valeur configurée en jours est atteinte. La valeur minimale est 30 jours. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurer les paramètres pour les extensions de noyau sur les appareils macOS <!-- 2043024 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme). Un nouveau groupe de paramètres vous permettra de configurer et d’utiliser les extensions de noyau sur vos appareils.

S’applique à : macOS 10.13.2 et versions ultérieures

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurer le profil pour ignorer certains écrans lors de l’exécution de l’Assistant Configuration <!-- 2276470 -->
Lors de la création d’un profil d’inscription macOS, vous serez en mesure de le configurer pour ignorer les écrans suivants quand un utilisateur exécute l’Assistant Configuration :
- Migration Android
- Display Tone (Indiquer la tonalité)
- Confidentialité
- iCloudStorage : si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple. Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.
Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils ou Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Les utilisateurs d’un appareil peuvent voir toutes les applications gérées qu’ils ont installées ou tenté d’installer <!-- 2352913 -->
Le portail d’entreprise pour Windows listera toutes les applications gérées, qu’elles soient obligatoires ou disponibles, qui sont installées sur l’appareil d’un utilisateur. Les utilisateurs pourront voir les installations d’applications tentées et en attente ainsi que leur état actuel. Si votre organisation ne rend pas les applications obligatoires ou disponibles, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Les utilisateurs pourront également trier ou filtrer leurs applications par état de l’installation.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Balises d’étendue pour les jetons VPP Apple <!--2371886 -->
Vous pourrez ajouter des étiquettes d’étendue à des jetons VPP Apple. Seuls les utilisateurs attribués avec la même balise d’étendue ont accès au jeton VPP Apple ayant cette balise. Les applications et livres électroniques VPP achetés avec ce jeton héritent de ses balises d’étendue. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilisez « règles d’applicabilité » lors de la création de profils de configuration d’appareil Windows 10 <!-- 2549910 -->
Vous créez des profils de configuration d’appareil Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme). Vous serez en mesure de créer une **règle d’applicabilité** pour que le profil s’applique seulement à une édition spécifique ou à une version spécifique. Par exemple, vous créez un profil qui active certains paramètres de BitLocker. Une fois que vous avez ajouté le profil, utilisez une règle d’applicabilité pour que le profil s’applique seulement aux appareils exécutant Windows 10 Entreprise.

S’applique à : 
- Windows 10 et versions ultérieures

### <a name="enable-win32-app-dependencies----2617348---"></a>Activer les dépendances d’application Win32 <!-- 2617348 -->
Préversion publique - En tant qu’administrateur, vous pourrez exiger que les autres applications soient installées en tant que dépendances avant d’installer votre application Win32. Plus précisément, l’appareil doit installer la ou les applications dépendantes avant d’installer l’application Win32. Cette fonctionnalité sera disponible seulement une fois l’agent de gestion Intune mis à niveau vers la version 1904 (ultérieure à la version 1.18.120.0), ce qui peut prendre une ou deux semaines supplémentaires une fois le service mis à niveau vers la version 1904. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Sélectionnez **Application Windows (Win32)** comme **Type d’application**. Pour plus d’informations, consultez [Intune autonome - Gestion des applications Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nouveau paramètre de restriction d’appareil pour Android Entreprise, Propriétaire de l’appareil : permet aux utilisateurs de se connecter à des réseaux Wi-Fi sur des appareils Android Entreprise dédiés s’exécutant en mode kiosque multi-application <!--3041940 -->
Les administrateurs pourront activer/désactiver un nouveau paramètre qui permet aux utilisateurs de configurer Bluetooth sur leurs appareils Android Entreprise dédiés s’exécutant en mode kiosque multi-application. Pour voir ce paramètre dans la console Intune, choisissez **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions de l’appareil** pour le type de profil > **Paramètres**  > **Appareils dédiés** > sélectionnez **Multi-application** à partir de la liste déroulante des paramètres **Mode kiosque**. Une option appelée **Configuration Wi-Fi** pourra être activée. 

S’applique à : Appareils Android Entreprise dédiés s’exécutant en mode kiosque multi-application. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nouveau paramètre de restriction d’appareil pour Android Entreprise, Propriétaire de l’appareil : permet aux utilisateurs de configurer Bluetooth et l’appairage sur des appareils Android Entreprise dédiés <!--3041941 -->
Les administrateurs pourront activer/désactiver un nouveau paramètre qui permet aux utilisateurs de configurer Bluetooth sur leurs appareils Android Entreprise dédiés s’exécutant en mode kiosque multi-application. Pour voir ce paramètre dans la console Intune, choisissez **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions de l’appareil** pour le type de profil > **Paramètres**  > **Appareils dédiés** > sélectionnez **Multi-application** à partir de la liste déroulante des paramètres **Mode kiosque**. Une option appelée **Configuration Bluetooth** pourra être activée. 

S’applique à : Appareils Android Entreprise dédiés s’exécutant en mode kiosque multi-application. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Superviser l’état de la base de référence de sécurité (préversion publique) <!-- 3082047 --> 
Quand vous surveillez l’*État de l’appareil* pour vos bases de référence de sécurité, la vue organisera l’état selon les catégories de la base de référence, comme *Au-dessus du verrouillage*, *BitLocker*et *Navigateur*. Toutes les catégories disponibles de la base de référence seront représentées. Pour chaque catégorie, vous verrez combien d’appareils ne correspondent pas à une catégorie spécifique de la base de référence, sont mal configurés ou ne sont pas applicables.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tâches de sécurité Intune pour Defender ATP (en préversion publique) <!-- 3208597 -->
Disponible en préversion publique, Intune ajoutera bientôt des tâches de sécurité pour la gestion des menaces et des vulnérabilités de Microsoft Defender récemment annoncée.  Avec cette intégration, les administrateurs du fonctionnement de la sécurité dans Windows Defender ATP peuvent communiquer plus efficacement aux administrateurs Intune les remédiations recommandées pour les menaces émergentes. L’ajout de tâches de sécurité ajoute une approche basée sur les risques pour découvrir, hiérarchiser et remédier aux vulnérabilités et aux mauvaises configurations des points de terminaison.

Pour plus d’informations sur les tâches de sécurité dans Intune, consultez le billet de blog sur [l’utilisation des tâches de sécurité Intune pour étendre la gestion des menaces et des vulnérabilités de Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Créer et utiliser des profils de configuration d’appareils OEMConfig dans Intune <!-- 3305883 -->
Intune prendra en charge la configuration des appareils Android Entreprise avec OEMConfig. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres à des appareils Android Entreprise à l’aide d’OEMConfig (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme).

La prise en charge des fabricants OEM s’effectue actuellement par OEM. Si une application OEMConfig que vous voulez n’est pas disponible dans la liste des applications OEMConfig, contactez `IntuneOEMConfig@microsoft.com`.

S’applique à : 
- Android Entreprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nouveaux paramètres de restriction d’appareil pour les propriétaires d’appareils Android Entreprise <!-- 3574254 -->
Sur les appareils Android Entreprise, vous pouvez créer un profil de restriction d’appareil pour autoriser ou restreindre les fonctionnalités, définir des règles de mot de passe, et plus encore (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement > Restrictions sur l’appareil** pour le type de profil). 

Nouveaux paramètres, notamment des paramètres de mot de passe, autorisant un accès complet aux applications dans Google Play Store pour les appareils entièrement gérés ; d’autres paramètres seront disponibles. 

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md). 

S’applique à : Appareils Android Entreprise entièrement gérés

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10 <!-- 3617671 -->
De nombreux appareils Windows 10 et ultérieur ont des circuits microprogrammés Module de plateforme sécurisée (TPM). Un nouveau paramètre de conformité vérifiera si l’appareil comporte un module de plateforme sécurisée (TPM).

[Paramètres de stratégie de conformité de Windows 10 et ultérieur](compliance-policy-create-windows.md) liste les paramètres actuels.

S’applique à : 
- Windows 10 et versions ultérieures

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune <!-- 3695227 -->
Vous pourrez indiquer que vos applications Win32 doivent être installées sur des appareils joints à Azure AD et inscrits auprès d’Intune. Pour plus d’informations sur les applications Win32 dans Intune, consultez [Gestion des applications Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Ligne de base Windows Defender Advanced Threat Protection <!-- 3754134 -->
Nous allons ajouter une nouvelle base de référence pour vous aider à configurer les paramètres de Windows Defender Advanced Threat Protection.

### <a name="device-overview-shows-primary-user---794259---"></a>La vue d’ensemble de l’appareil indique l’utilisateur principal <!--794259 -->
La page de vue d’ensemble de l’appareil indique l’utilisateur principal, également appelé utilisateur d’UDA (affinité entre appareil et utilisateur). Pour voir l’utilisateur principal d’un appareil, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil. L’utilisateur principal apparaît en haut de la page **Vue d’ensemble**.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Prise en charge étendue des appareils Android Entreprise entièrement gérés <!-- 3903241, 3903244, 3903246 -->
Nous allons développer la prise en charge des appareils Android Entreprise entièrement gérés ([première annonce en janvier 2019](whats-new.md#week-of-january-14-2019) pour y inclure les éléments suivants :
- Compatibilité
- Accès conditionnel
- Nouvelle application pour utilisateur final

Pour configurer des appareils Android complètement managés, accédez à **Inscription des appareils** > **Inscription Android** > **Appareils des utilisateurs complètement managés appartenant à l’entreprise**. La prise en charge des appareils Android complètement gérés reste en préversion et certaines fonctionnalités Intune peuvent ne pas être entièrement opérationnelles. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Création de rapports d’applications Google Play gérées supplémentaires pour les appareils avec profil professionnel Android Entreprise <!-- 4105925 -->
Pour les applications Google Play gérées déployées sur des appareils avec profil professionnel Android Entreprise, il sera possible de voir le numéro de version spécifique de l’application installée sur un appareil. Cela concerne uniquement les applications obligatoires. Les mêmes fonctionnalités seront activées pour les applications disponibles dans une version ultérieure.

### <a name="ios-third-party-keyboards----4111843---"></a>Claviers tiers iOS <!-- 4111843 -->
La prise en charge de la stratégie de protection des applications Intune pour le paramètre **Claviers de tiers** prendra fin en raison d’une modification de la plateforme iOS. Vous ne pourrez pas configurer ce paramètre dans la console d’administration Intune et il ne sera pas appliqué sur le client dans le SDK d’application Intune.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Empêcher les utilisateurs de rechercher les mises à jour de Windows <!-- 3316758 -->
Nous ajoutons un nouveau paramètre d’anneau de mise à jour de Windows que vous pouvez utiliser pour empêcher des utilisateurs de rechercher des mises à jour de Windows. Ce paramètre ne sera pas disponible à partir du portail, mais il pourra être configuré avec l’API Graph d’Intune.

### <a name="windows-update-notifications----3316782---"></a>Notifications Windows Update <!-- 3316782 -->
Nous avons ajouté la prise en charge pour les configurations de l’anneau Windows Update : vous pourrez ainsi configurer les notifications Windows Update que vos utilisateurs voient. Ce paramètre ne sera pas disponible à partir du portail, mais il pourra être configuré avec l’API Graph d’Intune.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Accès plus facile aux paramètres de diagnostic <!-- 3804627 -->
Nous ajoutons une nouvelle option au panneau **Journaux d’audit** dans chaque charge de travail Journal d’audit de la console Intune, que vous pouvez utiliser pour ouvrir directement la page *Paramètres de diagnostic*.

## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.


