---
title: Édition préliminaire
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 606005c3d8abafe989b35841cebf8c11e1f6b04e
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075878"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Édition préliminaire pour Microsoft Intune - Octobre 2018

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Utiliser les paramètres recommandés par Microsoft avec les lignes de base de sécurité <!-- 2055484 -->
Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur pourra créer des stratégies de sécurité directement à partir de ces lignes de base, et les déployer ensuite pour ses utilisateurs. Il pourra également personnaliser les recommandations en fonction des besoins de son organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

### <a name="remove-ability-for-admins-to-wipe-personal-devices-and-reset-passcodes----2934699---"></a>Supprimer la capacité des administrateurs à réinitialiser les appareils personnels et les codes secrets <!-- 2934699 -->
Pour éviter que les utilisateurs ne craignent que les administrateurs d’entreprise puissent réinitialiser leurs appareils personnels, les actions à distance [Réinitialiser](devices-wipe.md#wipe) et [Réinitialiser le code secret](device-passcode-reset.md) ne s’appliqueront plus aux appareils personnels. Les utilisateurs peuvent réinitialiser leurs codes secrets et effacer leurs appareils de tout appareil à l’aide du site web Portail d’entreprise.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>Prise en charge d’Autopilot pour les appareils hybrides joints à Azure Active Directory <!-- 1048100 -->
Vous pourrez configurer les appareils hybrides joints à Azure Active Directory à l’aide d’Autopilot. Les appareils doivent être joints au réseau de votre organisation afin d’utiliser la fonctionnalité Autopilot hybride.

### <a name="scope-tags-for-apps---1081941---"></a>Balises d’étendue pour les applications <!--1081941 -->
Vous serez en mesure de créer des balises d’étendue pour limiter l’accès aux ressources Intune. Ajoutez une balise d’étendue à une attribution de rôle, puis la balise d’étendue à un profil de configuration. Le rôle a uniquement accès aux ressources avec des profils de configuration qui ont des balises d’étendue correspondantes (ou aucune balise d’étendue).
Pour créer une balise d’étendue, choisissez **Rôles Intune** > **Étendue (balises)** > **Créer**.
Pour ajouter une balise d’étendue à une attribution de rôle, choisissez **Rôles Intune** > **Tous les rôles** > **Gestionnaire de stratégies et de profils** > **Attributions** > **Étendue (balises)**.
Pour ajouter une balise d’étendue à un profil de configuration, choisissez **Configuration de l’appareil** > **Profils** > choisissez un profil > **Propriétés** > **Étendue (balises)**.

## <a name="tenant-health-dashboard----1124854---"></a>Tableau de bord d’intégrité du locataire <!-- 1124854 -->
La page État du locataire dans Intune vous fournira des informations sur l’état du locataire dans un emplacement unique. La page est divisée en quatre sections :  
- **Détails du locataire** : contient des informations telles que votre autorité MDM, le nombre total d’appareils inscrits dans votre locataire et le nombre de licences. Cette section indique également la version actuelle du service pour votre locataire.
- **État du connecteur** : contient des informations sur les connecteurs configurés, tels qu’Apple VPP, Windows Store pour Entreprises et les connecteurs de certificat. En fonction de leur état actuel, les connecteurs sont marqués comme *Sain*, *Avertissement* ou *Défectueux*.
- **État du service Intune** : répertorie les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office ([https://portal.office.com](https://portal.office.com)).
- **Actualités Intune** : contient des messages actifs pour votre locataire, notamment des notifications signalant que votre locataire a reçu les dernières fonctionnalités d’Intune. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office ([https://portal.office.com](https://portal.office.com)).

### <a name="enrollment-abandonment-report----1382924---"></a>Rapport d’abandon de l’inscription <!-- 1382924 -->
Un nouveau rapport qui fournit des détails sur les inscriptions abandonnées sera disponible sous **Inscription de l’appareil** > **Moniteur**.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Stratégies de protection des informations Windows déployées sans inscription de l’utilisateur <!-- 1434452 -->
Les stratégies de protection des informations Windows pourront être déployées sans que les utilisateurs MDM soient obligés d’inscrire leur appareil Windows 10. Cette configuration permet aux organisations de protéger leurs documents d’entreprise conformément à la configuration de la protection des informations Windows, tout en permettant à l’utilisateur de conserver la gestion de ses propres appareils Windows. Une fois les documents protégés par une stratégie de protection des informations Windows, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie de protection des informations Windows. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Ajouter une image de marque personnalisée pour l’application Portail d’entreprise <!-- 1916266 -->
En tant qu’administrateur Microsoft Intune, vous pourrez charger une image de marque personnalisée qui sera affichée comme image d’arrière-plan dans la page de profil de l’utilisateur dans l’application Portail d’entreprise. Pour plus d’informations sur la configuration de l’application Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md).

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Grouper les appareils Windows inscrits auprès d’Autopilot par ID de corrélation <!-- 2075110 -->
Intune prendra en charge le regroupement des appareils Windows par ID de corrélation en cas d’inscription à l’aide d’[Autopilot pour les appareils existants](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) par le biais de Configuration Manager. L’ID de corrélation est un paramètre du fichier de configuration Autopilot. Intune définira automatiquement [l’attribut d’appareil Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) pour qu’il soit égal à « OfflineAutopilotprofile-\<ID_corrélation\> ». Cela permet de créer des groupes dynamiques Azure AD arbitraires en fonction de l’ID de corrélation par le biais de l’attribut enrollmentprofilename pour les inscriptions Autopilot hors connexion. 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Prise en charge d’iOS 12 OAuth dans les profils de messagerie iOS <!--2155106 -->
Les profils de messagerie iOS d’Intune prendront en charge iOS 12 OAuth. Pour voir cette fonctionnalité, choisissez **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **OAuth**. Si ce paramètre est activé, deux choses se produiront :
1. Un nouveau profil sera émis aux appareils qui sont déjà ciblés
2. Les utilisateurs finaux seront invités à redonner leurs informations d’identification

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nouveau paramètre par défaut « Type de mot de passe obligatoire » pour Android et Android Entreprise<!-- 2649963 -->
Quand vous créez une stratégie de conformité (**Intune** > **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android** ou **Android Entreprise** pour Plateforme > Sécurité du système), la valeur par défaut **Type de mot de passe obligatoire** changera : Valeur par défaut actuelle : Valeur par défaut de l’appareil Nouvelle valeur par défaut : Au moins numérique S’applique à : Android, Android Enterprise

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Affecter des profils Autopilot au groupe virtuel Tous les appareils <!--2715522 -->
Vous pourrez affecter des profils Autopilot au groupe virtuel Tous les appareils. Pour ce faire, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > choisissez un profil >  **Affectations** > sous **Affecter à** choisissez **Tous les appareils**.

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nouvelle fonctionnalité Conditions d’utilisation dans Azure Active Directory <!-- 2870393 -->
Azure Active Directory aura une fonctionnalité Conditions d’utilisation que vous pourrez utiliser à la place des conditions générales Intune existantes. La fonctionnalité Conditions d’utilisation d’Azure AD offre davantage de flexibilité quant aux choix des conditions d’utilisation à afficher et au moment où elles sont affichées, une meilleure prise en charge de la localisation, un meilleur contrôle de l’affichage des conditions générales, ainsi que des fonctionnalités améliorées de création de rapports. La fonctionnalité Conditions d’utilisation d’Azure AD nécessite Azure Active Directory Premium P1, qui fait également partie de la suite Enterprise Mobility + Security E3.


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune conservera la langue localisée d’Office lors de la mise à jour d’Office sur les ordinateurs des utilisateurs finaux <!-- 2971030 -->
Quand Intune installera Office sur les ordinateurs de vos utilisateurs finaux, ceux-ci obtiendront automatiquement les mêmes modules linguistiques que ceux qu’ils avaient avec les installations .MSI Office précédentes. 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Paramètres de transfert de données Intune APP sur les appareils inscrits à la GPM iOS <!-- 2244713 -->
Vous pourrez séparer le contrôle des paramètres de transfert de données Intune APP sur les appareils inscrits à la GPM iOS de la spécification de l’identité de l’utilisateur inscrit. Les administrateurs qui n’utilisent pas IntuneMAMUPN ne verront aucun changement de comportement. Lorsque cette fonctionnalité est disponible, les administrateurs qui utilisent IntuneMAMUPN pour contrôler le comportement du transfert de données sur les appareils inscrits doivent consulter les nouveaux paramètres et mettre à jour leurs paramètres APP si nécessaire.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utiliser une clé prépartagée dans un profil Wi-Fi Windows 10 <!-- 2662938 -->
Vous pourrez utiliser une clé prépartagée (PSK) avec le protocole de sécurité WPA/WPA2-Personnel afin d’authentifier un profil de configuration Wi-Fi pour Windows 10.
Actuellement, vous devez importer un profil Wi-Fi ou créer un profil personnalisé pour utiliser une clé prépartagée. Les paramètres actuels sont répertoriés dans [Paramètres Wi-Fi pour Windows 10](wi-fi-settings-windows.md). 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Paramètres de stratégie de protection des applications pour les données du web <!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>La fréquence de synchronisation d’appareil Autopilot passe à toutes les 12 heures <!-- 2753673 -->
Les appareils Autopilot se synchroniseront toutes les 12 heures au lieu de toutes les 24 heures.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Mises à jour de la page d’accueil Intune et renommer le nœud <!--2867309 -->
Les mises à jour de la page d’accueil Intune incluront de nouveaux graphiques et de nouvelles vignettes de surveillance pour une meilleure visualisation des données. Le nœud **Applications mobiles** deviendra **Applications clientes**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Accès accru de l’utilisateur final à l’aide de l’application Portail d’entreprise <!-- 772203 -->
Les utilisateurs finaux pourront accéder à des actions importantes sur le compte, comme la réinitialisation du mot de passe et leur profil AAD, à partir de l’application du portail d’entreprise.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Jeton VPP Apple utilisé par une autre gestion MDM <!-- 1488946 -->
Intune détectera et affichera des détails si un jeton du Programme d’achat en volume (VPP) Apple est utilisé à la fois par Intune et une autre gestion MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Le numéro de version et le numéro de build d’iOS sont affichés <!-- 1892471 -->
Dans **Conformité de l’appareil** > **Conformité de l’appareil**, la version du système d’exploitation iOS s’affiche. Dans une prochaine mise à jour, le numéro de build sera également affiché.
Quand des mises à jour de sécurité sont publiées, Apple laisse généralement le numéro de version tel quel, mais met à jour le numéro de build. En affichant le numéro de build, vous pouvez vérifier facilement si une mise à jour des vulnérabilités est installée.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Appareils mis hors service dans le tableau de bord de conformité des appareils <!-- 1981119 -->
Dans une prochaine mise à jour, les appareils mis hors service seront retirés du tableau de bord de conformité des appareils. Cela changera vos numéros de conformité.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Changer le processus de mise à jour pour les connecteurs locaux <!-- 2277554 -->
Suite aux commentaires que nous ont envoyés des clients, le mode de mise à jour des connecteurs locaux va changer. Après avoir installé initialement un connecteur local, les mises à jour se produiront automatiquement. Ce changement commence par le nouveau connecteur PFX Certificate Connector pour Microsoft Intune et s’appliquera par la suite aux autres types de connecteurs locaux. 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Amélioration de l’expérience de l’application Portail d’entreprise pour les utilisateurs du gestionnaire d’inscription d’appareil <!-- 675800 -->
Quand un gestionnaire d’inscription d’appareil se connecte à l’application Portail d’entreprise pour Windows, l’application affiche uniquement l’appareil en cours d’exécution actuel du gestionnaire. Cette amélioration permet de réduire les délais d’attente qui se produisaient auparavant quand l’application essayait de charger tous les appareils inscrits par le gestionnaire d’inscription d’appareil.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Vérifier la conformité de Configuration Manager <!-- 2192052 -->
Une prochaine mise à jour va offrir un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**   >  **Windows 10**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide du paramètre Intune, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

S’applique à Windows 10 et ultérieur

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertes pour l’expiration du jeton VPP ou pour le nombre insuffisant de licences du portail d’entreprise <!-- 2237572 -->
Si vous utilisez le programme d’achat en volume (VPP) pour préprovisionner le portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le portail d’entreprise.

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Les claviers tiers peuvent être bloqués par des paramètres APP sur iOS <!-- 1248481 -->
Sur les appareils iOS, les administrateurs Intune peuvent bloquer l’utilisation de claviers tiers lors de l’accès à des données d’entreprise dans des applications protégées par une stratégie. Quand la stratégie de protection d’application (APP, Application Protection Policy) est configurée pour bloquer les claviers tiers, l’utilisateur de l’appareil reçoit un message la première fois qu’il interagit avec des données d’entreprise en utilisant un clavier tiers. Toutes les options autres que celles du clavier natif sont bloquées et les utilisateurs d’appareils ne les voient pas. La boîte de message ne s’affiche qu’une seule fois aux utilisateurs. 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Demander un code secret non biométrique après le délai d’expiration spécifié <!-- 1506985 --> 

En demandant un code secret non biométrique après un délai d’expiration spécifié par l’administrateur, Intune offre une sécurité renforcée pour les applications compatibles avec la gestion des applications mobiles (MAM) en limitant l’utilisation de l’identification biométrique pour l’accès aux données d’entreprise. Les paramètres affectent les utilisateurs qui s’appuient sur Touch ID (iOS), Face ID (iOS), Android Biométrique ou d’autres méthodes d’authentification biométriques à venir pour accéder à leurs applications compatibles APP/MAM. Ces paramètres permettent aux administrateurs Intune d’avoir un contrôle plus précis sur l’accès utilisateur, en supprimant les cas où un appareil avec plusieurs empreintes digitales ou d’autres méthodes d’accès biométriques peut révéler des données d’entreprise à un utilisateur inapproprié. Dans le portail Azure, ouvrez **Microsoft Intune**. Sélectionnez **Applications mobiles** > **Stratégies de protection des applications** > **Ajouter une stratégie** > **Paramètres**. Recherchez la section **Accès** pour des paramètres spécifiques.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Mise à jour de l’expérience Aide et commentaires sur l’application Portail d’entreprise pour Android <!--1631531 -->

L’expérience Aide et commentaires sur l’application Portail d’entreprise pour Android sera mise à jour de manière à pour se conformer aux bonnes pratiques pour les applications Android. L’application Portail d’entreprise pour Android sera mise à jour dans les prochains mois de manière à scinder l’élément de menu **Aide et commentaires** en deux éléments distincts **Aide** et **Envoyer des commentaires**. La page **Aide** contiendra une section **Questions fréquentes (FAQ)** et un bouton **Assistance par e-mail** pour amener les utilisateurs finaux à transmettre les journaux à Microsoft et à envoyer un e-mail au service de support de l’entreprise décrivant le problème. L’élément de menu **Envoyer des commentaires** permettra à l’utilisateur d’envoyer des commentaires à Microsoft. L’utilisateur devra choisir entre « J’aime quelque chose », « Je n’aime pas quelque chose » ou « J’ai une idée ».



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.



