---
title: Dans le développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune dans le développement
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
# <a name="in-development-for-microsoft-intune---april-2019"></a>Dans le développement pour Microsoft Intune - avril 2019

Pour faciliter votre préparation et planification, cette page listes Intune UI met à jour et de fonctionnalités qui en cours de développement, mais pas encore été publié. De plus :

- Si nous pensons que vous devez effectuer une action avant une modification, nous allons publier un billet de centre de messages Office complémentaire.
- Quand une fonctionnalité est lancée en production, soit en version préliminaire ou à la disposition générale, la description de la fonctionnalité déplace hors de cette page et sur le [page Nouveautés](whats-new.md).
- Cette page et le [page Nouveautés](whats-new.md) sont régulièrement mis à jour. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour stratégiques livrables et chronologies.

> [!Note]
> Ces éléments reflètent les attentes en cours de Microsoft sur les fonctionnalités Intune proposée dans une version ultérieure. Dates et des fonctionnalités individuelles peuvent changer. Pas tous les éléments de développement ont une description de la fonctionnalité sur cette page.

**Flux RSS** : recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Définir les paramètres de connexion et de contrôler les options de redémarrage sur des appareils macOS <!-- 1210083 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**configuration de l’appareil** > **profils** > **créer un profil** > Choisissez **macOS** pour plateforme > **fonctionnalités de l’appareil** pour le type de profil). Paramètres de la fenêtre Nouvelle connexion sera incluent des éléments tels que montrant une bannière personnalisée, choisissez comment les utilisateurs se connecteront, affichent ou masquer les paramètres d’alimentation et bien plus encore.

Pour afficher les paramètres actuels, accédez à [paramètres de la fonctionnalité appareil macOS](macos-device-features-settings.md).

S’applique à : macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Paramètres avancés pour le pare-feu Windows Defender <!-- 1311949 -->
Vous serez bientôt en mesure d’utiliser Intune pour gérer les règles de pare-feu personnalisées sur les clients pour Windows Defender. Règles peuvent spécifier le comportement de trafic entrant et sortant aux applications, les adresses réseau et les ports. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Nécessitent un accès conditionnel de Protection application  <!--1634317 -->
Vous serez en mesure d’utiliser *stratégie de Protection des applications nécessitent*, ce qui confirme la stratégie est appliquée à l’application un utilisateur avant la fin de connexion pour empêcher les utilisateurs d’accéder aux données que vous protégez l’accès conditionnel. Tandis que l’assurance de la stratégie peut ralentir la première utilisation, il vous protège contre les problèmes de réseau, les erreurs de configuration d’administration ou les efforts intentionnels pour déjouer les stratégies de protection d’application. 

### <a name="retire-noncompliant-devices----1827291---"></a>Mettre hors service des appareils non conformes <!-- 1827291 -->
Nous allons ajouter une nouvelle action de conformité pour mettre hors service un appareil non conforme. Mise hors service un appareil non conforme supprime toutes les données d’entreprise, ainsi que l’appareil d’être gérés par Intune. Cette action s’exécute lorsque la valeur en jours configurée est atteinte. La valeur minimale est 30 jours. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurer les paramètres pour les extensions de noyau sur les appareils macOS <!-- 2043024 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**configuration de l’appareil** > **profils** > **créer un profil** > Choisissez **macOS** pour la plateforme). Un nouveau groupe de paramètres vous permettra de configurer et utiliser les extensions de noyau sur vos appareils.

S’applique à : macOS 10.13.2 et versions ultérieures

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurer le profil pour ignorer certains écrans lors de l’exécution de l’Assistant Configuration <!-- 2276470 -->
Lors de la création d’un profil d’inscription macOS, vous serez en mesure de le configurer pour ignorer les écrans suivants quand un utilisateur exécute l’Assistant Configuration :
- Migration Android
- Display Tone (Indiquer la tonalité)
- Confidentialité
- iCloudStorage : si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple. Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.
Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils ou Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Les utilisateurs peuvent afficher toutes les applications gérées qu’ils ont installé ou a tenté d’installer <!-- 2352913 -->
Portail d’entreprise pour Windows va répertorier toutes les applications gérées&ndash; obligatoire et disponible&ndash; qui sont installés sur le périphérique d’un utilisateur. Les utilisateurs pourront à vue tentée et en attente d’installations d’applications, ainsi que leur état actuel. Si votre organisation ne rend pas les applications requises ou disponibles, les utilisateurs voient un message expliquant que les applications d’entreprise ont été installées. Les utilisateurs pourront également trier ou filtrer leurs applications en état de l’installation.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Balises d’étendue pour les jetons VPP d’Apple <!--2371886 -->
Vous serez en mesure d’ajouter des balises d’étendue pour les jetons VPP d’Apple. Seuls les utilisateurs affectés avec la même balise d’étendue ont accès au jeton VPP Apple avec cette balise. Applications VPP et les livres électroniques achetés avec ce jeton héritent ses balises d’étendue. Pour plus d’informations sur les balises d’étendue, consultez [utilisez RBAC et l’étendue de balises](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilisez « règles d’applicabilité » lorsque la création de profils de configuration d’appareil Windows 10 <!-- 2549910 -->
Vous créez des profils de configuration d’appareil Windows 10 (**configuration de l’appareil** > **profils** > **créer un profil**  >  **Windows 10** pour la plateforme). Vous serez en mesure de créer un **règle de mise en application** pour le profil s’applique uniquement à une édition spécifique ou une version spécifique. Par exemple, vous créez un profil qui permet à certains paramètres de BitLocker. Une fois que vous ajoutez le profil, utilisez une règle de mise en application pour le profil s’applique uniquement aux appareils exécutant Windows 10 entreprise.

S’applique à : 
- Windows 10 et versions ultérieures

### <a name="enable-win32-app-dependencies----2617348---"></a>Activer les dépendances d’application Win32 <!-- 2617348 -->
Version préliminaire publique - en qualité d’administrateur, vous pourrez exiger que les autres applications sont installées en tant que dépendances avant d’installer votre application Win32. Plus précisément, l’appareil doit installer les ou les applications dépendantes avant d’installer l’application Win32. Cette fonctionnalité sera disponible uniquement après que l’agent de gestion Intune a été mis à niveau vers la version de 1904 (supérieure à 1.18.120.0) qui peut prendre 1 ou 2 semaines supplémentaires une fois que nous mettre à niveau le service sur 1904. Dans Intune, sélectionnez **les applications clientes** > **applications** > **ajouter** pour afficher le **ajouter une application** panneau. Sélectionnez **application Windows (Win32)** en tant que le **type d’application**. Pour plus d’informations, consultez [Intune Standalone - gestion des applications Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nouveau paramètre de restriction d’appareil pour Android Enterprise, le propriétaire de l’appareil : permettre aux utilisateurs de se connecter aux réseaux Wi-Fi sur les appareils Android Enterprise dédié le mode applications multiples plein écran <!--3041940 -->
Les administrateurs pourront activer/désactiver un nouveau paramètre qui permet aux utilisateurs de configurer le Bluetooth sur leurs appareils Android Enterprise dédié exécutant le mode applications multiples plein écran. Pour afficher ce paramètre dans la console Intune, choisissez **Intune** > **configuration de l’appareil** > **profils**  >  **Créer un profil** > choisissez **Android Enterprise** pour plateforme > **propriétaire de l’appareil uniquement, les restrictions d’appareil** pour le type de profil > **paramètres**   >  **Périphériques dédiés** > sélectionnez **multi-application** à partir de la **mode plein écran** paramètre de liste déroulante. Une option appelée **configuration Wi-Fi** sera disponible pour l’activer. 

S’applique à : Android Enterprise dédié des appareils qui exécutent le mode applications multiples plein écran. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nouveau paramètre de restriction d’appareil pour Android Enterprise, le propriétaire de l’appareil : permettre aux utilisateurs de configurer le Bluetooth et association sur les appareils Android Enterprise dédié <!--3041941 -->
Les administrateurs pourront activer/désactiver un nouveau paramètre qui permet aux utilisateurs de configurer le Bluetooth sur leurs appareils Android Enterprise dédié exécutant le mode applications multiples plein écran. Pour afficher ce paramètre dans la console Intune, choisissez **Intune** > **configuration de l’appareil** > **profils**  >  **Créer un profil** > choisissez **Android Enterprise** pour plateforme > **propriétaire de l’appareil uniquement, les restrictions d’appareil** pour le type de profil > **paramètres**   >  **Périphériques dédiés** > sélectionnez **multi-application** à partir de la **mode plein écran** paramètre de liste déroulante. Une option appelée **Bluetooth configuration** sera disponible pour l’activer. 

S’applique à : Android Enterprise dédié des appareils qui exécutent le mode applications multiples plein écran. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Surveiller l’état de sécurité de base (version préliminaire publique) <!-- 3082047 --> 
Quand vous surveillez le *état de l’appareil* pour vos bases de sécurité, la vue s’organiser l’état par les catégories de ligne de base, comme *par-dessus le verrouillage*, *BitLocker*et  *Navigateur*. Toutes les catégories disponibles de la ligne de base seront représentées. Pour chaque catégorie, vous verrez combien d’appareils ne correspondent pas à une catégorie spécifique de la ligne de base, est mal configuré ou n’est pas applicables.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tâches de sécurité Intune pour Defender ATP (en préversion publique) <!-- 3208597 -->
Sera disponible en version préliminaire publique, Intune bientôt ajoutera des tâches de sécurité pour le Microsoft Defender Threat & la gestion des vulnérabilités récemment annoncée.  Avec cette intégration, les administrateurs d’opérations de sécurité dans Windows Defender ATP les menaces peuvent communiquer plus efficacement les corrections recommandées pour les menaces émergentes pour les administrateurs Intune. L’ajout de tâches de sécurité ajoute une approche basée sur les risques pour détecter, hiérarchiser et résoudre les erreurs de configuration et les vulnérabilités de point de terminaison.

Pour en savoir plus sur les tâches de sécurité dans Intune, consultez le blog sur [à l’aide des tâches de sécurité Intune pour étendre des menaces et la gestion des vulnérabilités de Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Créer et utiliser des profils de configuration d’appareil OEMConfig dans Intune <!-- 3305883 -->
Intune prendra en charge de configuration des appareils Android Enterprise avec OEMConfig. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer les paramètres aux appareils d’entreprise Android à l’aide de OEMConfig (**configuration de l’appareil** > **profils**  >  **Créer un profil** > **Android enterprise** pour la plateforme).

Prise en charge pour les fabricants OEM est actuellement sur une base par l’OEM. Si une application OEMConfig souhaité n’est pas disponible dans la liste des applications de OEMConfig, contactez `IntuneOEMConfig@microsoft.com`.

S’applique à : 
- Android Entreprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nouveaux paramètres de restriction d’appareil d’entreprise Android, propriétaire de l’appareil <!-- 3574254 -->
Sur les appareils Android Enterprise, vous pouvez créer un profil de restriction d’appareil pour autoriser ou limiter les fonctionnalités, définir des règles de mot de passe et bien plus encore (**configuration de l’appareil** > **profils**  >  **Créer un profil** > choisissez **Android Enterprise** pour plateforme > **propriétaire uniquement de l’appareil > restrictions d’appareil** pour le type de profil). 

Nouveaux paramètres, y compris les paramètres de mot de passe, ce qui complète l’accès à des applications dans Google Play Store pour les appareils entièrement gérés, et bien plus encore sera disponible. 

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md). 

S’applique à : Android Enterprise entièrement les appareils gérés

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Recherchez une puce de module de plateforme sécurisée dans une stratégie de conformité Windows 10 <!-- 3617671 -->
Nombreux appareils Windows 10 et versions ultérieures ont chipsets de Module de plateforme sécurisée (TPM). Un nouveau paramètre de conformité vérifie si un module de plateforme sécurisée sur l’appareil.

[Windows 10 et les paramètres de stratégie de conformité ultérieure](compliance-policy-create-windows.md) répertorie les paramètres actuels.

S’applique à : 
- Windows 10 et versions ultérieures

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurer vos applications Win32 sur Intune inscrit des appareils joints à Azure AD <!-- 3695227 -->
Vous serez en mesure d’affecter vos applications Win32 sur Intune inscrit à Azure AD les appareils joints à un. Pour plus d’informations sur les applications Win32 dans Intune, consultez [gestion des applications Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Ligne de base Windows Defender Advanced Threat Protection <!-- 3754134 -->
Nous allons ajouter la nouvelle ligne de base pour vous aider à configurer les paramètres de Windows Defender Advanced Threat Protection.

### <a name="device-overview-shows-primary-user---794259---"></a>Vue d’ensemble de l’appareil indique à l’utilisateur principal <!--794259 -->
La page de vue d’ensemble du périphérique affiche l’utilisateur principal, également appelé l’utilisateur d’affinité utilisateur périphérique (UDA). Pour afficher l’utilisateur principal pour un appareil, choisissez **Intune** > **appareils** > **tous les appareils** > Choisissez un appareil. L’utilisateur principal apparaît près du haut de la **vue d’ensemble** page.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Prise en charge étendue pour les appareils Android Enterprise entièrement gérés <!-- 3903241, 3903244, 3903246 -->
Nous allons étendre la prise en charge des appareils d’entreprise Android entièrement gérés ([annoncé en janvier de 2019](whats-new.md#week-of-january-14-2019) inclure les éléments suivants :
- Compatibilité
- Accès conditionnel
- Utilisateur final nouvelle application

Pour configurer des appareils Android complètement managés, accédez à **Inscription des appareils** > **Inscription Android** > **Appareils des utilisateurs complètement managés appartenant à l’entreprise**. Prise en charge pour le reste des appareils Android entièrement géré en préversion et certaines fonctionnalités Intune ne peuvent pas être entièrement opérationnelles. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Création de rapports pour appareils avec profil professionnel Android Enterprise Application supplémentaire Google Play géré <!-- 4105925 -->
Pour les applications de Google Play géré déployées sur les appareils avec profil professionnel Android Enterprise, il sera possible d’afficher le numéro de version spécifique de l’application est installée sur un appareil. Cela concerne uniquement les applications requises. Les mêmes fonctionnalités pour les applications disponibles seront activée dans une version ultérieure.

### <a name="ios-third-party-keyboards----4111843---"></a>Claviers tiers iOS <!-- 4111843 -->
Prise en charge de la stratégie de protection des applications Intune (application) pour le **tiers claviers** paramètre prendra fin en raison d’une modification de la plateforme iOS. Vous ne serez pas en mesure de configurer ce paramètre dans la Console d’administration Intune et ne sont pas appliquée sur le client dans le SDK d’application Intune.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Empêcher les utilisateurs de l’analyse des mises à jour de Windows <!-- 3316758 -->
Nous ajoutons un nouveau paramètre d’anneau de mise à jour de Windows que vous pouvez utiliser pour empêcher des utilisateurs de l’analyse des mises à jour de Windows. Ce paramètre n’est pas disponible à partir du portail, mais peut être configuré à l’aide de l’API Graph Intune.

### <a name="windows-update-notifications----3316782---"></a>Notifications de mise à jour de Windows <!-- 3316782 -->
Nous avons ajouté la prise en charge pour les configurations d’anneau de mise à jour de Windows afin d’être en mesure de configurer les notifications de mise à jour de Windows que vos utilisateurs voient. Ce paramètre n’est pas disponible à partir du portail, mais peut être configuré à l’aide de l’API Graph Intune.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Faciliter l’accès aux paramètres de Diagnostic <!-- 3804627 -->
Nous ajoutons une nouvelle option pour le **journaux d’Audit** panneau chaque charge de travail du journal d’Audit dans la console Intune que vous pouvez utiliser pour ouvrir directement le *les paramètres de Diagnostic* page.

## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.


