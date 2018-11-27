---
title: Édition préliminaire
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: fbe8cc0fc3e835ee5807dfbe56ea1aa3c728547e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184724"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Édition préliminaire pour Microsoft Intune - Novembre 2018

> [!Note]
> Notification de l’accord de confidentialité : Les modifications suivantes sont en cours de développement pour Intune. Ces informations sont partagées selon les termes de l’accord de confidentialité, de façon très limitée. Ne publiez aucune de ces informations sur des médias sociaux ou des sites web publics comme Twitter, UserVoice, Reddit, etc. 

**L’édition préliminaire** fournit la liste des fonctionnalités, partagée selon les termes de l’accord de confidentialité, qui seront intégrées dans les prochaines versions de Microsoft Intune. Ces informations sont fournies de manière limitée et sont susceptibles de changer. Ne tweetez pas, ne publiez sur UserVoice et ne partagez pas ces informations en dehors de votre entreprise. Certaines fonctionnalités répertoriées ici risquent de ne pas être prêtes d’ici la date limite et d’être repoussées à une version ultérieure. D’autres fonctionnalités sont en cours de test dans un pilote (version d’évaluation) pour s’assurer qu'elles sont prêtes à l'emploi. Joignez votre contact de groupe de produits Microsoft si vous avez des questions ou rencontrez des problèmes.

Cette page est mise à jour périodiquement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Désinstallation d’applications sur des appareils iOS supervisés appartenant à l’entreprise <!-- 1281677 -->
Vous allez pouvoir supprimer les applications de votre choix sur les appareils iOS supervisés appartenant à l’entreprise. Vous pouvez supprimer une application en ciblant des groupes d’utilisateurs ou des groupes d’appareils ayant le type d’affectation **Désinstaller**. Pour les appareils iOS personnels ou non supervisés, vous êtes toujours limité à la suppression des applications installées à l’aide d’Intune.

### <a name="track-installation-of-office-proplus---2620217--"></a>Effectuer le suivi de l’installation d’Office ProPlus <!--2620217-->
Vous allez pouvoir suivre la progression de l’installation d’[Office ProPlus](apps-add-office365.md) à l’aide de la [Page d’état d’inscription](windows-enrollment-status.md).

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Prise en charge du Programme d’inscription des appareils macOS pour les comptes Apple School Manager <!--3006133-->
Intune prend en charge l’utilisation du Programme d’inscription des appareils sur les appareils macOS pour les comptes Apple School Manager.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Suspendre temporairement le mode kiosque sur les appareils Android pour apporter des changements <!-- 3041935 -->
Pendant que vous utilisez un appareil Android en mode kiosque multiapplication, un administrateur informatique peut être amené à effectuer des changements sur l’appareil. Un nouveau paramètre de mode kiosque multiapplication permet à un administrateur informatique de suspendre temporairement le mode kiosque à l’aide d’un code PIN, et d’accéder à la totalité de l’appareil.
Pour voir les paramètres actuels du mode kiosque, consultez [Paramètres kiosque Android](android-kiosk-settings.md).

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Définir un arrière-plan personnalisé dans l’application Managed Home Screen <!-- 3041945 -->
Nous allons ajouter un paramètre qui vous permet de personnaliser l’apparence de l’arrière-plan de l’application Managed Home Screen sur les appareils Android Entreprise en mode kiosque multiapplication.  Pour configurer l’**l’arrière-plan de l’URL personnalisée**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Activer le bouton d’accueil virtuel sur les appareils Android Entreprise en mode kiosque <!-- 3042021 -->
Un nouveau paramètre permet aux utilisateurs d’appuyer sur un bouton programmable de leur appareil pour passer de l’application Managed Home Screen à d’autres applications affectées (et inversement) sur leur appareil en mode kiosque multiapplication. Ce paramètre est particulièrement utile dans les scénarios où l’application en mode kiosque d’un utilisateur ne répond pas correctement au bouton Précédent. Vous allez pouvoir configurer ce paramètre pour les appareils Android à usage unique appartenant à l’entreprise. Pour activer ou désactiver le **bouton d’accueil virtuel**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Enregistrement et application des affectations de stratégies de protection des applications <!-- 3104570 -->
Vous aurez un meilleur contrôle de vos affectations de stratégies de protection des applications. En enregistrant et en appliquant vos affectations de stratégies de protection des applications, seuls les utilisateurs visés sont directement impactés par une affectation de stratégie de protection des applications.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nouveaux paramètres du navigateur Microsoft Edge pour Windows 10 et versions ultérieures <!-- 3174639 -->
Un nouveau paramètre va être ajouté pour vous aider à contrôler et gérer le navigateur Microsoft Edge sur vos appareils. Pour obtenir la liste des paramètres actuels, consultez [Restriction des appareils pour Windows 10 (et versions ultérieures)](device-restrictions-windows-10.md#microsoft-edge-browser).

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Sélectionner les applications suivies dans la Page d’état d’inscription<!-- 2531007 -->
Vous pouvez choisir les applications à suivre dans la Page d’état d’inscription.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Mise à jour de l’IU des stratégies de protection des applications Intune <!-- 3251427 -->

Les stratégies de protection des applications Intune vous permettent de configurer divers paramètres de protection des données pour des applications protégées Intune, par exemple Microsoft Outlook et Word. Nous changeons les étiquettes des paramètres et des boutons pour faciliter leur compréhension. Les contrôles ne sont plus des contrôles **oui**/**non** et deviennent principalement des contrôles **bloquer**/**autoriser** et **désactiver**/**activer**. Les étiquettes sont également mises à jour pour des raisons de clarté. Le format des paramètres a également changé. Le paramètre et son étiquette se présentent côte à côte dans le contrôle, ce qui permet une meilleure navigation. Les paramètres par défaut et le nombre de paramètres restent identiques. Toutefois, ce changement permet à l’utilisateur de comprendre, de parcourir et d’utiliser les paramètres plus facilement pour appliquer les stratégies de protection des applications sélectionnées.



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Utiliser les paramètres recommandés par Microsoft avec les lignes de base de sécurité <!-- 2055484 -->
Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur pourra créer des stratégies de sécurité directement à partir de ces lignes de base, et les déployer ensuite pour ses utilisateurs. Il pourra également personnaliser les recommandations en fonction des besoins de son organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

### <a name="scope-tags-for-apps---1081941---"></a>Balises d’étendue pour les applications <!--1081941 -->
Vous serez en mesure de créer des balises d’étendue pour limiter l’accès aux ressources Intune. Ajoutez une balise d’étendue à une attribution de rôle, puis la balise d’étendue à un profil de configuration. Le rôle a uniquement accès aux ressources avec des profils de configuration qui ont des balises d’étendue correspondantes (ou aucune balise d’étendue).
Pour créer une balise d’étendue, choisissez **Rôles Intune** > **Étendue (balises)** > **Créer**.
Pour ajouter une balise d’étendue à une attribution de rôle, choisissez **Rôles Intune** > **Tous les rôles** > **Gestionnaire de stratégies et de profils** > **Attributions** > **Étendue (balises)**.
Pour ajouter une balise d’étendue à un profil de configuration, choisissez **Configuration de l’appareil** > **Profils** > choisissez un profil > **Propriétés** > **Étendue (balises)**.

### <a name="tenant-health-dashboard----1124854---"></a>Tableau de bord d’intégrité du locataire <!-- 1124854 -->
La page État du locataire dans Intune vous fournira des informations sur l’état du locataire dans un emplacement unique. La page est divisée en quatre sections :  
- **Détails du locataire** : contient des informations telles que votre autorité MDM, le nombre total d’appareils inscrits dans votre locataire et le nombre de licences. Cette section indique également la version actuelle du service pour votre locataire.
- **État du connecteur** : contient des informations sur les connecteurs configurés, tels qu’Apple VPP, Windows Store pour Entreprises et les connecteurs de certificat. En fonction de leur état actuel, les connecteurs sont marqués comme *Sain*, *Avertissement* ou *Défectueux*.
- **État du service Intune** : répertorie les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office ([https://portal.office.com](https://portal.office.com)).
- **Actualités Intune** : contient des messages actifs pour votre locataire, notamment des notifications signalant que votre locataire a reçu les dernières fonctionnalités d’Intune. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Stratégies de protection des informations Windows déployées sans inscription de l’utilisateur <!-- 1434452 -->
Les stratégies de protection des informations Windows pourront être déployées sans que les utilisateurs MDM soient obligés d’inscrire leur appareil Windows 10. Cette configuration permet aux organisations de protéger leurs documents d’entreprise conformément à la configuration de la protection des informations Windows, tout en permettant à l’utilisateur de conserver la gestion de ses propres appareils Windows. Une fois les documents protégés par une stratégie de protection des informations Windows, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie de protection des informations Windows. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Paramètres de stratégie de protection des applications pour les données du web <!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Jeton VPP Apple utilisé par une autre gestion MDM <!-- 1488946 -->
Intune détectera et affichera des détails si un jeton du Programme d’achat en volume (VPP) Apple est utilisé à la fois par Intune et une autre gestion MDM.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-available-in-compliance-policies----1892471---"></a>Les numéros de version et de build iOS et macOS sont disponibles dans les stratégies de conformité <!-- 1892471 -->
Dans **Conformité de l’appareil** > **Conformité de l’appareil**, les versions des systèmes d’exploitation iOS et macOS indiquées peuvent être utilisées dans les stratégies de conformité. Dans une prochaine mise à jour, le numéro de build sera également configurable pour les deux plateformes.

Quand des mises à jour de sécurité sont publiées, Apple laisse généralement le numéro de version tel quel, mais met à jour le numéro de build. En utilisant le numéro de build dans une stratégie de conformité, vous pouvez facilement vérifier si une mise à jour des vulnérabilités est installée.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Appareils mis hors service dans le tableau de bord de conformité des appareils <!-- 1981119 -->
Dans une prochaine mise à jour, les appareils mis hors service seront retirés du tableau de bord de conformité des appareils. Cela changera vos numéros de conformité.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Changer le processus de mise à jour pour les connecteurs locaux <!-- 2277554 -->
Suite aux commentaires que nous ont envoyés des clients, le mode de mise à jour des connecteurs locaux va changer. Après avoir installé initialement un connecteur local, les mises à jour se produiront automatiquement. Ce changement commence par le nouveau connecteur PFX Certificate Connector pour Microsoft Intune et s’appliquera par la suite aux autres types de connecteurs locaux. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Vérifier la conformité de Configuration Manager <!-- 2192052 -->
Une prochaine mise à jour va offrir un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**   >  **Windows 10**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide du paramètre Intune, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

S’applique à Windows 10 et ultérieur

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertes pour l’expiration du jeton VPP ou pour le nombre insuffisant de licences du portail d’entreprise <!-- 2237572 -->
Si vous utilisez le programme d’achat en volume (VPP) pour préprovisionner le portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le portail d’entreprise.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.



