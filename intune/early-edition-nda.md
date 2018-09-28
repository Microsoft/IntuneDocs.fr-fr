---
title: Édition préliminaire
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: beee1462c1b6e683287b4d304df386ce525be820
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141637"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Édition préliminaire pour Microsoft Intune - Septembre 2018

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>Accès de compte utilisateur aux applications Intune sur les appareils iOS et Android managés <!-- ! 1248496  -->

En tant qu’administrateur Microsoft Intune, vous pourrez contrôler les comptes utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pourrez limiter l’accès uniquement aux comptes utilisateur professionnels autorisés et bloquer les comptes personnels sur les appareils inscrits. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Créer des suffixes DNS dans les profils de configuration VPN sur les appareils exécutant Windows 10 <!-- 1333668 -->
Lorsque vous créez un profil de configuration d’appareil VPN (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **VPN** pour le type de profil), vous entrez des paramètres DNS. Vous pourrez également entrer plusieurs **suffixes DNS** dans Intune. Lorsque vous utilisez des suffixes DNS, vous pouvez rechercher une ressource réseau à l’aide de son nom court, au lieu du nom de domaine complet (FQDN). Cette mise à jour vous permet également de modifier l’ordre des suffixes DNS dans Intune.
Les paramètres DNS actuels sont répertoriés dans [Paramètres VPN Windows 10](vpn-settings-windows-10.md#dns-settings).
S’applique à : appareils Windows 10

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Prise en charge de VPN AlwaysOn pour les profils professionnels d’entreprise Android <!-- 1333705 -->
Vous pourrez utiliser des connexions VPN AlwaysOn sur les appareils d’entreprise Android avec des profils professionnels managés. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Le paramètre VPN AlwaysOn se trouve sous **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Restrictions d’appareil** sous **Profils professionnels uniquement** pour le type de profil > **Connectivité**. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Stratégie de configuration d’application Outlook pour iOS et Android <!--1828527 -->
Vous pourrez créer une stratégie de configuration d’application Outlook pour iOS et Android. Les paramètres de configuration supplémentaires seront ajoutés au fur et à mesure qu’ils seront activés pour Outlook pour iOS et Android.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>Verrouiller à distance des appareils non conformes <!-- 2064495 -->
Si un appareil n’est pas conforme, vous pourrez créer une action dans la stratégie de conformité qui verrouille l’appareil à distance. Dans Intune > **Conformité de l’appareil**, créez une nouvelle stratégie ou sélectionnez une stratégie existante. Sélectionnez **Actions en cas de non-conformité** > **Ajouter** et choisissez de verrouiller l’appareil à distance.
Pris en charge sur : 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 et versions ultérieures 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Paramètres de transfert de données Intune APP sur les appareils inscrits à la GPM iOS <!-- 2244713 -->
Vous pourrez séparer le contrôle des paramètres de transfert de données Intune APP sur les appareils inscrits à la GPM iOS de la spécification de l’identité de l’utilisateur inscrit. Les administrateurs qui n’utilisent pas IntuneMAMUPN ne verront aucun changement de comportement. Lorsque cette fonctionnalité est disponible, les administrateurs qui utilisent IntuneMAMUPN pour contrôler le comportement du transfert de données sur les appareils inscrits doivent consulter les nouveaux paramètres et mettre à jour leurs paramètres APP si nécessaire.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utiliser une clé prépartagée dans un profil Wi-Fi Windows 10 <!-- 2662938 -->
Vous pourrez utiliser une clé prépartagée (PSK) avec le protocole de sécurité WPA/WPA2-Personnel afin d’authentifier un profil de configuration Wi-Fi pour Windows 10.
Actuellement, vous devez importer un profil Wi-Fi ou créer un profil personnalisé pour utiliser une clé prépartagée. Les paramètres actuels sont répertoriés dans [Paramètres Wi-Fi pour Windows 10](wi-fi-settings-windows.md). 

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>La fréquence de synchronisation d’appareil Autopilot passe à toutes les 12 heures <!-- 2753673 -->
Les appareils Autopilot se synchroniseront toutes les 12 heures au lieu de toutes les 24 heures.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Appliquer le profil Autopilot à des appareils Win 10 inscrits qui ne sont pas encore enregistrés dans Autopilot <!-- 1558983 -->
Vous pouvez appliquer des profils Autopilot à des appareils Win 10 inscrits qui n’ont pas encore été enregistrés dans Autopilot. Dans le profil Autopilot, choisissez l’option **Convertir tous les appareils ciblés vers Autopilot** pour enregistrer automatiquement les appareils non Autopilot dans le service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures. Lorsque l’appareil est désinscrit et réinitialisé, Autopilot le provisionne. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>Créer et attribuer plusieurs profils Page d’état d’inscription aux groupes Azure AD <!-- 2526564-->
Vous pourrez créer et attribuer plusieurs profils Page d’état d’inscription à des groupes d’utilisateurs Azure AAD.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Mises à jour de la page d’accueil Intune et renommer le nœud <!--2867309 -->
Les mises à jour de la page d’accueil Intune incluront de nouveaux graphiques et de nouvelles vignettes de surveillance pour une meilleure visualisation des données. Le nœud **Applications mobiles** deviendra **Applications clientes**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Accès accru de l’utilisateur final à l’aide de l’application du portail d’entreprise <!-- 772203 -->
Les utilisateurs finaux pourront accéder à des actions importantes sur le compte, comme la réinitialisation du mot de passe et leur profil AAD, à partir de l’application du portail d’entreprise.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Émettre des certificats SCEP aux appareils sans utilisateur <!-- 1744554 -->
Actuellement, les certificats sont émis aux utilisateurs. Vous pourrez émettre des certificats SCEP pour des appareils, notamment des appareils sans utilisateur comme les appareils kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Certificat SCEP** pour le profil). Les autres mises à jour incluront :
- La propriété **Objet** dans un profil SCEP est maintenant une zone de texte personnalisée et peut inclure de nouvelles variables. 
- La propriété **Autre nom de l'objet (SAN)** dans un profil SCEP est désormais un format de tableau et peut inclure de nouvelles variables. Dans le tableau, un administrateur peut ajouter un attribut et indiquer la valeur dans une zone de texte personnalisée. Le SAN prendra en charge les attributs suivants : 
  - DNS
  - Adresse de messagerie
  - UPN Ces nouvelles variables peuvent être ajoutées avec du texte statique dans une zone de texte de valeur personnalisée. Par exemple, l’attribut DNS peut être ajouté en tant que `DNS = {{AzureADDeviceId}}.domain.com`.
  > [!NOTE]
  > Les accolades, les points-virgules et les barres verticales « { } ; | » ne fonctionnent pas dans le texte statique du SAN. Les accolades ne doivent encadrer qu’une des nouvelles variables de certificat d’appareil acceptées pour `Subject` ou `Subject alternative name`. Nouvelles variables de certificat d’appareil :  
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

S’applique à : Windows 10 et versions ultérieures et iOS, pris en charge pour Wi-Fi



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

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Améliorations de profil Kiosk Windows 10 et versions ultérieures dans le portail Azure <!-- 2748224 eeready -->
Le profil de configuration d’appareil Windows 10 Kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Préversion Kiosk** pour le type de profil) sera amélioré : 
- Actuellement, vous pouvez créer plusieurs profils kiosk sur le même appareil. Avec cette mise à jour, Intune ne prendra en charge qu’un seul profil kiosk par appareil. Si vous avez toujours besoin de plusieurs profils kiosk sur un seul appareil, vous pouvez utiliser un URI personnalisé.
-Dans un profil **kiosk multi-application**, vous pouvez sélectionner la taille de la mosaïque d’application et l’ordre de **présentation du menu Démarrer** dans la grille de l’application. Si vous préférez avoir plus de personnalisation, vous pouvez continuer à charger un fichier XML.
- Les paramètres Navigateur Kiosk sont déplacés dans les paramètres **Kiosk**. Actuellement, les paramètres **Navigateur web Kiosk** ont leur propre catégorie dans le portail Azure.
S’applique à : Windows 10 et versions ultérieures

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Amélioration de l’expérience de l’application Portail d’entreprise pour les utilisateurs du gestionnaire d’inscription d’appareil <!-- 675800 -->
Quand un gestionnaire d’inscription d’appareil se connecte à l’application Portail d’entreprise pour Windows, l’application affiche uniquement l’appareil en cours d’exécution actuel du gestionnaire. Cette amélioration permet de réduire les délais d’attente qui se produisaient auparavant quand l’application essayait de charger tous les appareils inscrits par le gestionnaire d’inscription d’appareil.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Vérifier la conformité de Configuration Manager <!-- 2192052 -->
Une prochaine mise à jour va offrir un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**   >  **Windows 10**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide du paramètre Intune, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

S’applique à Windows 10 et ultérieur

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertes pour l’expiration du jeton VPP ou pour le nombre insuffisant de licences du portail d’entreprise <!-- 2237572 -->
Si vous utilisez le programme d’achat en volume (VPP) pour préprovisionner le portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le portail d’entreprise.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Paramètres de sécurité supplémentaires pour le programme d’installation de Windows <!-- 2282430 -->
Vous pourrez autoriser les utilisateurs à contrôler les installations d’applications. Si cette fonctionnalité est activée, les installations qui sinon pourraient être arrêtées en raison d’une violation de sécurité sont autorisées à poursuivre leur exécution. Vous pourrez faire en sorte que le programme d’installation de Windows utilise des autorisations élevées quand il installe un programme sur un système. Vous pourrez en outre autoriser l’indexation des éléments de la Protection des informations Windows et le stockage de leurs métadonnées dans un emplacement non chiffré. Quand la stratégie est désactivée, les éléments protégés par la Protection des informations Windows ne seront pas indexés et n’apparaîtront pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Les fonctionnalités de ces options seront désactivées par défaut. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Les claviers tiers peuvent être bloqués par des paramètres APP sur iOS <!-- 1248481 -->
Sur les appareils iOS, les administrateurs Intune peuvent bloquer l’utilisation de claviers tiers lors de l’accès à des données d’entreprise dans des applications protégées par une stratégie. Quand la stratégie de protection d’application (APP, Application Protection Policy) est configurée pour bloquer les claviers tiers, l’utilisateur de l’appareil reçoit un message la première fois qu’il interagit avec des données d’entreprise en utilisant un clavier tiers. Toutes les options autres que celles du clavier natif sont bloquées et les utilisateurs d’appareils ne les voient pas. La boîte de message ne s’affiche qu’une seule fois aux utilisateurs. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Modules linguistiques Office 365 Pro Plus <!-- 1833450 -->
En tant qu’administrateur Intune, vous pourrez déployer des langues supplémentaires pour les applications Office 365 Pro Plus gérées par le biais d’Intune. La liste des langues disponibles inclut le **Type** du module linguistique (principal, partiel et de vérification). Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications mobiles** > **Applications** > **Ajouter**. Dans la liste **Type d’application** du panneau **Ajouter une application**, sélectionnez **Windows 10** sous la **Suite Office 365**. Sélectionnez **Langues** dans le panneau **Paramètres de la suite d’applications**.

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



