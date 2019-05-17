---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910331"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>En développement pour Microsoft Intune - Mai 2019

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Application sur le portail Intune de la suppression d’un appareil sur le portail Apple <!--2489996 -->
Si un appareil est supprimé sur le portail du Programme d’inscription des appareils ou sur le portail Apple Business Manager, cette suppression est automatiquement appliquée à Intune lors de la synchronisation suivante.

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Prise en charge de la base de référence lors d’une recherche par mot clé  <!-- 3082036         -->
Lors de la création ou de la modification d’un profil de base de référence de la sécurité, vous serez bientôt en mesure d’utiliser la fonction de *recherche* pour filtrer les paramètres qui s’affichent dans la console.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Réinitialiser et effacer en bloc le contenu des appareils à l’aide de l’API Graph <!-- 3295288 -->
L’API Graph permettra de réinitialiser et d’effacer le contenu d’un maximum de 100 appareils à la fois.

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10 <!-- 3617671 -->
De nombreux appareils Windows 10 et ultérieur ont des circuits microprogrammés Module de plateforme sécurisée (TPM). Cette mise à jour inclut un nouveau paramètre de conformité, qui vérifie la version de la puce TPM sur l’appareil. 

La section [Paramètres de stratégie de conformité de Windows 10 et ultérieur](compliance-policy-create-windows.md#device-security) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Scripts PowerShell pour Intune Management Extension  <!-- 3734186    -->
Vous serez en mesure de configurer des scripts PowerShell, qui s’exécuteront avec les privilèges d’administrateur de l’utilisateur sur l’appareil. Pour en savoir plus, voir [Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune](intune-management-extension.md).

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>Empêcher les utilisateurs finaux de modifier leur point d’accès personnel et désactiver la journalisation de serveur Siri sur des appareils iOS supervisés <!-- 4097904  --> 
Vous pouvez créer un profil de restrictions pour un appareil iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres, que vous pouvez configurer :

- Paramètre du point d’accès personnel
- Paramètre de journalisation du serveur Siri

Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](device-restrictions-ios.md). 

S’applique à : iOS 12.2 et plus

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>Nouveaux paramètres de restriction pour les applications de salle de classe sur les appareils macOS inscrits au programme d’inscription des appareils <!-- 4097905  --> 
Vous pouvez créer des profils de configuration pour les appareils macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut les nouveaux paramètres pour les applications de salle de classe sur les appareils inscrits au programme d’inscription des appareils, en offrant une option de désactivation de la solution iCloud Photo Library.

Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](device-restrictions-macos.md).

S’applique à : macOS 10.14.4 et plus

### <a name="android-enterprise-app-management----4459905-idready---"></a>Gestion d’applications Android Entreprise <!-- 4459905 idready -->
Pour aider les administrateurs informatiques à configurer et à utiliser les fonctions de gestion d’applications Android Entreprise, Intune ajoute automatiquement quatre applications liées à cette solution dans la console d’administration Intune. Ces applications sont les suivantes :

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : cette application est utilisée pour les scénarios impliquant une instance Android Entreprise entièrement gérée.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ce logiciel vous aide à vous connecter à vos comptes lorsque vous utilisez la vérification à deux facteurs.
- **[Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : cette application est utilisée pour les scénarios impliquant des stratégies de protection des applications et des profils de travail Android Entreprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : cette fonctionnalité est utilisée pour les scénarios impliquant des kiosques/une instance Android Entreprise dédiée.

Auparavant, les administrateurs informatiques devaient manuellement rechercher et approuver ces applications dans le [store Google Play géré](https://play.google.com/store/apps) lors de la configuration. Cette modification supprime ces étapes manuelles, afin que la gestion de l’application Android Entreprise soit plus simple et plus rapide pour les clients.

Ces quatre fonctionnalités sont automatiquement ajoutées à la liste des applications Intune des administrateurs la première fois qu’ils connectent leur locataire Intune au store Google Play géré. Pour en savoir plus, voir [Connecter votre compte Intune à votre compte professionnel Android](connect-intune-android-enterprise.md). Pour les locataires qui ont déjà connecté leur locataire ou qui utilisent déjà Android Entreprise, les administrateurs n’ont pas besoin d’intervenir. Ces quatre applications s’afficheront automatiquement dans les 7 jours suivant la fin du lancement de service de mai 2019.

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Paramètres avancés pour le pare-feu Windows Defender <!-- 1311949 -->
Vous serez bientôt en mesure d’utiliser Intune pour gérer les règles de pare-feu personnalisées sur les clients pour Windows Defender. Les règles peuvent spécifier le comportement du trafic entrant et sortant avec les applications, les adresses réseau et les ports. 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Les utilisateurs d’un appareil peuvent voir toutes les applications gérées qu’ils ont installées ou tenté d’installer <!-- 2352913 -->
Le portail d’entreprise pour Windows listera toutes les applications gérées, qu’elles soient obligatoires ou disponibles, qui sont installées sur l’appareil d’un utilisateur. Les utilisateurs pourront voir les installations d’applications tentées et en attente ainsi que leur état actuel. Si votre organisation ne rend pas les applications obligatoires ou disponibles, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Les utilisateurs pourront également trier ou filtrer leurs applications par état de l’installation.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilisez « règles d’applicabilité » lors de la création de profils de configuration d’appareil Windows 10 <!-- 2549910 -->
Vous créez des profils de configuration d’appareil Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme). Vous serez en mesure de créer une **règle d’applicabilité** pour que le profil s’applique seulement à une édition spécifique ou à une version spécifique. Par exemple, vous créez un profil qui active certains paramètres de BitLocker. Une fois que vous avez ajouté le profil, utilisez une règle d’applicabilité pour que le profil s’applique seulement aux appareils exécutant Windows 10 Entreprise.

S’applique à : 
- Windows 10 et versions ultérieures

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tâches de sécurité Intune pour Defender ATP (en préversion publique) <!-- 3208597 -->
Disponible en préversion publique, Intune ajoutera bientôt des tâches de sécurité pour la gestion des menaces et des vulnérabilités de Microsoft Defender récemment annoncée.  Avec cette intégration, les administrateurs du fonctionnement de la sécurité dans Windows Defender ATP peuvent communiquer plus efficacement aux administrateurs Intune les remédiations recommandées pour les menaces émergentes. L’ajout de tâches de sécurité ajoute une approche basée sur les risques pour découvrir, hiérarchiser et remédier aux vulnérabilités et aux mauvaises configurations des points de terminaison.

Pour plus d’informations sur les tâches de sécurité dans Intune, consultez le billet de blog sur [l’utilisation des tâches de sécurité Intune pour étendre la gestion des menaces et des vulnérabilités de Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Ligne de base Windows Defender Advanced Threat Protection <!-- 3754134 -->
Nous allons ajouter une nouvelle base de référence pour vous aider à configurer les paramètres de Windows Defender Advanced Threat Protection.



## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.


