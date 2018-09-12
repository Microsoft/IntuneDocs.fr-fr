---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 0205715a8e35d009401886af4bd0bf88fb9cf662
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347285"
---
# <a name="whats-new-in-microsoft-intune"></a>Nouveautés de Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Découvrez les nouveautés hebdomadaires dans Microsoft Intune. Vous pouvez également découvrir les [modifications à venir](#whats-coming), les [avis importants](#notices) sur le service et des informations sur les [versions précédentes](whats-new-archive.md). Le lancement de certaines fonctionnalités peut s’étaler sur plusieurs semaines. Ces fonctionnalités risquent de ne pas être accessibles à tous les clients la première semaine.

> [!Note]
> Pour plus d’informations sur les nouvelles fonctionnalités de gestion des appareils mobiles (MDM) hybride, consultez la page sur les [nouveautés de la gestion hybride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-august-27-2018"></a>Semaine du 27 août 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Prise en charge du tunnel de paquets pour les profils VPN par application iOS pour les types de connexions personnalisés et Pulse Secure <!-- 1520957 -->
Lors de l’utilisation de profils VPN par application iOS, vous pouvez choisir d’utiliser le tunneling de couche application (app-proxy) ou de niveau paquet (packet-tunnel). Ces options sont disponibles avec les types de connexions suivants :
- VPN personnalisé
- Pulse Secure. Si vous ne savez pas quelle valeur utiliser, consultez la documentation de votre fournisseur VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Différer le moment où les mises à jour logicielles iOS sont affichées sur l’appareil <!-- 1949583 -->
Dans Intune > **Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS**, vous pouvez configurer les jours et heures où vous ne souhaitez pas que les appareils installent des mises à jour. Dans une prochaine mise à jour, vous serez en mesure de différer le moment où une mise à jour logicielle est visiblement indiquée sur l’appareil, entre 1 et 90 jours. 
[Configurer des stratégies de mise à jour iOS dans Microsoft Intune](software-updates-ios.md) liste les paramètres actuels.

#### <a name="office-365-proplus-version----2213968---"></a>Version d’Office 365 ProPlus <!-- 2213968 -->
Lors de l’affectation des applications Office 365 ProPlus à des appareils Windows 10 avec Intune, vous pouvez sélectionner la version d’Office. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications** > **Ajouter une application**. Sélectionnez ensuite **Suite Office 365 ProPlus (Windows 10)** à partir de la liste déroulante **Type**. Sélectionnez **Paramètres de la suite d’applications** pour afficher le panneau correspondant. Affectez une valeur à **Canal de mise à jour**, par exemple **Tous les mois**. Supprimez éventuellement l’autre version d’Office (msi) des appareils des utilisateurs finaux en sélectionnant **Oui**. Sélectionnez **Spécifique** pour installer une version spécifique de Microsoft Office pour le canal sélectionné sur les appareils des utilisateurs finaux. À ce stade, vous pouvez sélectionner la **Version spécifique** d’Office à utiliser. Les versions disponibles changeront au fil du temps. Par conséquent, quand vous créez un déploiement, les versions disponibles peuvent être plus récentes et ne pas disposer de certaines versions antérieures. Les déploiements actuels continuent de déployer l’ancienne version, mais la liste des versions est en permanence actualisée par canal. Pour plus d’informations, consultez [Présentation des canaux de mise à jour pour Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Prise en charge du paramètre d’inscription DNS pour VPN Windows 10 <!-- 2282852 -->
Avec cette mise à jour, vous pouvez configurer des profils VPN Windows 10 pour inscrire dynamiquement les adresses IP affectées à l’interface VPN auprès du DNS interne, sans avoir besoin d’utiliser des profils personnalisés.
Pour plus d’informations sur les paramètres de profil VPN actuellement disponibles, consultez [Paramètres VPN de Windows 10](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Le nom de fichier du programme d’installation du portail d’entreprise macOS inclut désormais le numéro de version <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759-wnready---"></a>Mises à jour automatiques des applications iOS <!-- 2729759 wnready -->
Les mises à jour automatiques des applications fonctionnent pour les applications sous licence d’appareil et d’utilisateur pour iOS version 11.0 et ultérieure.




### <a name="device-configuration"></a>Configuration des appareils

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello cible les utilisateurs et appareils <!-- 1106609 -->
Quand vous créez une stratégie [Windows Hello Entreprise](windows-hello.md), elle s’applique à tous les utilisateurs au sein de l’organisation (au niveau locataire). Avec cette mise à jour, la stratégie peut également être appliquée à des utilisateurs ou des appareils spécifiques à l’aide d’une stratégie de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Identity Protection** > **Windows Hello Entreprise**).
Dans le portail Azure d’Intune, la configuration et les paramètres de Windows Hello existent désormais à la fois dans **Inscription de l’appareil** et dans **Configuration de l’appareil**. **Inscription de l’appareil** cible toute l’organisation (au niveau locataire) et prend en charge Windows AutoPilot (OOBE). **Configuration de l’appareil** cible des appareils et des utilisateurs à l’aide d’une stratégie appliquée lors de l’archivage.
Cette fonctionnalité s’applique à :  
- Windows 10 et versions ultérieures
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler est une connexion disponible pour les profils VPN sur iOS <!-- 1769858 eeready -->
Quand vous créez un profil de configuration d’appareil VPN iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** >  plateforme **iOS** > type de profil **VPN**), il existe plusieurs types de connexions, notamment Cisco, Citrix et bien plus encore. Cette mise à jour ajoute Zscaler comme type de connexion. 
[Paramètres VPN pour les appareils exécutant iOS](vpn-settings-ios.md) liste les types de connexions disponibles.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077-eeready---"></a>Mode FIPS pour les profils Wi-Fi d’entreprise pour Windows 10 <!-- 1879077 eeready -->
Vous pouvez désormais activer le mode FIPS (Federal Information Processing Standards) pour les profils Wi-Fi d’entreprise pour Windows 10 dans le portail Azure Intune. Vérifiez que le mode FIPS est activé sur votre infrastructure Wi-Fi si vous l’activez dans vos profils Wi-Fi.
[Paramètres Wi-Fi pour les appareils Windows 10 et ultérieur dans Intune](wi-fi-settings-windows.md) vous montre comment créer un profil Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Contrôler le mode S sur des appareils Windows 10 et ultérieur- préversion publique <!-- 1958649 -->
Avec la mise à jour de cette fonctionnalité, vous pouvez créer un profil de configuration d’appareil qui sort un appareil Windows 10 du mode S ou empêcher les utilisateurs de sortir l’appareil du mode S. Cette fonctionnalité se trouve dans Intune > **Configuration de l’appareil** > **Profils** >  **Windows 10 et ultérieur** > **Mise à niveau d’édition et changement de mode**.
[Présentation de Windows 10 en mode S](https://www.microsoft.com/windows/s-mode) propose d’autres informations sur le mode S.
S’applique à : Windows 10 et ultérieur (1809 et ultérieur)

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Ajout automatique du package de configuration de Windows Defender ATP au profil de configuration <!-- 2144658 -->
Lors de l’utilisation [d’ATP (Advanced Threat Protection) et de l’intégration d’appareils](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) dans Intune, vous deviez auparavant télécharger un package de configuration et l’ajouter à votre profil de configuration. Avec cette mise à jour, Intune reçoit automatiquement le package du Centre de sécurité Windows Defender et l’ajoute à votre profil.
S’applique à Windows 10 et versions ultérieures.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Exiger que les utilisateurs se connectent pendant la configuration de l’appareil <!--2311457-->
Vous pouvez maintenant définir des profils d’appareil de façon à exiger que l’appareil se connecte à un réseau avant de continuer au-delà de la page Réseau lors de la configuration de Windows 10. Tant que cette fonctionnalité est en préversion, vous avez besoin de Windows Insider build 1809 ou ultérieure pour utiliser ce paramètre.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Restreindre des applications et bloquer l’accès aux ressources d’entreprise sur les appareils iOS et Android Entreprise<!-- 2451462 -->
Dans **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **iOS** > **Sécurité système**, il existe un nouveau paramètre, **Applications restreintes**. Ce nouveau paramètre utilise une stratégie de conformité pour bloquer l’accès aux ressources d’entreprise si certaines applications sont installées sur l’appareil. L’appareil est considéré comme non conforme jusqu’à ce que les applications restreintes soient supprimées de l’appareil.
S’applique à : iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Mises à jour de la prise en charge VPN moderne pour iOS <!-- 2459928, 1819876, and 2650856 -->
Cette mise à jour ajoute la prise en charge des clients VPN iOS suivants : 
- F5 Access (versions 3.0.1 et ultérieures)
- Citrix SSO
- Palo Alto Networks GlobalProtect versions 5.0 et ultérieure. Également dans cette mise à jour :
- Le type de connexion **Accès F5** existant a été renommé en **Accès F5 hérité** pour iOS.
- Le type de connexion **Palo Alto Networks GlobalProtect** existant est renommé en **Palo Alto Networks GlobalProtect (hérité)** pour iOS.
Les profils existants avec ces types de connexions continuent de fonctionner avec leur client VPN hérité respectif. Si vous utilisez Cisco Legacy AnyConnect, Accès F5 hérité, Citrix VPN ou Palo Alto Networks GlobalProtect version 4.1 et antérieur avec iOS, vous devez passer aux nouvelles applications. Faites-le dès que possible pour vous assurer que l’accès VPN est disponible pour les appareils iOS quand ils effectuent la mise à jour vers iOS 12.
Pour plus d’informations sur iOS 12 et les profils VPN, consultez le [blog de l’équipe du support technique Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exporter des stratégies de conformité du portail Azure Classic pour recréer ces stratégies dans le portail Azure Intune <!-- 2469637 -->
Les stratégies de conformité créées dans le portail Azure Classic seront dépréciées. Vous pouvez examiner et supprimer des stratégies de conformité existantes, mais vous ne pouvez pas les mettre à jour. Si vous avez besoin migrer des stratégies de conformité vers le portail Azure Intune actuel, vous pouvez exporter les stratégies sous forme de fichier avec la virgule comme séparateur (fichier *.csv*). Ensuite, utilisez les informations détaillées du fichier pour recréer ces stratégies dans le portail Azure Intune.

> [!IMPORTANT]
> Une fois le portail Azure Classic mis hors service, vous ne pourrez plus accéder à ou afficher vos stratégies de conformité. Veillez donc à exporter et à recréer vos stratégies dans le portail Azure avant la mise hors service du portail Azure Classic.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile : nouveau partenaire de Mobile Threat Defense <!-- 22662717 -->
Vous pouvez contrôler l’accès des appareils mobiles aux ressources d’entreprise grâce à l’accès conditionnel basé sur une évaluation des risques menée par Better Mobile, une solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Verrouiller le portail d’entreprise en mode Application unique jusqu’à la connexion de l’utilisateur <!--1067692 --> 
Vous avez désormais la possibilité d’exécuter le portail d’entreprise en mode Application unique si vous authentifiez un utilisateur via le portail d’entreprise au lieu de l’Assistant Configuration lors de l’inscription DEP. Cette option verrouille l’appareil immédiatement après l’exécution de l’Assistant Configuration afin qu’un utilisateur soit obligé de se connecter pour accéder à l’appareil. Ce processus permet de s’assurer que l’appareil termine l’intégration et qu’il n’est pas laissé orphelin dans un état sans aucun utilisateur lié.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Affecter un utilisateur et un nom convivial à un appareil Autopilot <!--1346521 -->
Vous pouvez désormais [affecter un utilisateur à un appareil Autopilot spécifique](enrollment-autopilot.md). Les administrateurs pourront également donner des noms conviviaux pour accueillir l’utilisateur lors de la configuration de leur appareil avec Autopilot.
S’applique à : Windows Insider 1809 ou ultérieur (dans la préversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilisation de licences d’appareil VPP pour préprovisionner le portail d’entreprise lors d’une inscription DEP <!-- 1608345 -->
Vous pouvez maintenant utiliser des licences d’appareil du programme d’achat en volume (VPP, Volume Purchase Program) pour préprovisionner le portail d’entreprise pendant les inscriptions au Programme d’inscription des appareils (DEP, Device Enrollment Program). Pour ce faire, quand vous [créez ou modifiez un profil d’inscription](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), spécifiez le jeton VPP que vous souhaitez utiliser pour installer le portail d’entreprise. Assurez-vous que votre jeton n’expire pas et que vous avez suffisamment de licences pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune pousse le Portail d’entreprise de l’App Store à la place (un identifiant Apple vous sera demandé).

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloquer les inscriptions d’appareils personnels Windows <!-- 1849498 -->
Vous pouvez [bloquer l’inscription des appareils personnels Windows](enrollment-restrictions-set.md#set-device-type-restrictions) avec la [gestion des appareils mobiles](windows-enroll.md) dans Intune. Les appareils inscrits avec [l’agent de PC Intune](manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Spécifier des modèles de nom d’ordinateur dans un profil Autopilot <!--1849855-->
Vous pouvez [spécifier un modèle de nom d’ordinateur](enrollment-autopilot.md#create-an-autopilot-deployment-profile) pour générer et définir le [nom de l’ordinateur](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) lors de l’inscription Autopilot.

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Pour les profils Windows Autopilot, masquer les options de changement de compte dans la page de connexion de l’entreprise et la page d’erreur de domaine <!--1901669 -->
De [nouvelles options de profil Windows Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) permettent aux administrateurs de masquer les options de changement de compte sur les pages de connexion et d’erreur de domaine de l’entreprise. Pour masquer ces options, il est nécessaire de configurer la marque de société dans Azure Active Directory. S’applique à : Windows Insider 1809 ou version ultérieure (dans la préversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilisation de licences d’appareil VPP pour préprovisionner le portail d’entreprise lors d’une inscription DEP <!-- 1608345 -->
Vous pouvez maintenant utiliser des licences d’appareil du programme d’achat en volume (VPP, Volume Purchase Program) pour préprovisionner le portail d’entreprise pendant les inscriptions au Programme d’inscription des appareils (DEP, Device Enrollment Program). Pour ce faire, quand vous [créez ou modifiez un profil d’inscription](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), spécifiez le jeton VPP que vous souhaitez utiliser pour installer le portail d’entreprise. Assurez-vous que votre jeton n’expire pas et que vous avez suffisamment de licences pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune pousse le Portail d’entreprise de l’App Store à la place (un identifiant Apple vous sera demandé).

### <a name="device-management"></a>Gestion des appareils

#### <a name="delete-jamf-devices----2653306--"></a>Supprimer des appareils Jamf <!-- 2653306-->
Vous pouvez supprimer des appareils gérés par JAMF, en accédant à **Appareils** > choisissez l’appareil Jamf > **Supprimer**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Modifier la terminologie pour « mettre hors service » et « réinitialiser » <!-- 2175759 -->
Pour être cohérent avec l’API Graph, les termes suivants ont été changés dans l’interface utilisateur et la documentation d’Intune :
- **Supprimer les données d’entreprise** est remplacé par « Mettre hors service »
- **Réinitialisation d’usine** est remplacé par **réinitialiser**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Boîte de dialogue de confirmation si l’administrateur essaie de supprimer le certificat Push MDM <!-- 297909500-->
Si quelqu’un tente de supprimer un certificat Push MDM Apple, une boîte de dialogue de confirmation indique le nombre d’appareils iOS et macOS associés. Si le certificat est supprimé, ces appareils doivent être réinscrits.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Paramètres de sécurité supplémentaires pour le programme d’installation de Windows <!-- 2282430 -->
Vous pouvez permettre aux utilisateurs de contrôler les installations d’applications. Si cette fonctionnalité est activée, les installations qui sinon pourraient être arrêtées en raison d’une violation de sécurité sont autorisées à poursuivre leur exécution. Vous pouvez indiquer au programme d’installation de Windows d’utiliser des autorisations élevées quand il installe un programme sur un système. Vous pouvez en outre autoriser l’indexation des éléments de la Protection des informations Windows et le stockage de leurs métadonnées dans un emplacement non chiffré. Quand la stratégie est désactivée, les éléments protégés par la Protection des informations Windows ne sont pas indexés et n’apparaissent pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Les fonctionnalités de ces options sont désactivées par défaut. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nouvelle mise à jour de l’expérience utilisateur du site web Portail d’entreprise<!--2000968 -->
En nous basant sur les commentaires que nous ont envoyés des clients, nous avons ajouté de nouvelles fonctionnalités au site web Portail d’entreprise. Vous allez constater une nette amélioration des fonctionnalités existantes et de la facilité d’utilisation sur vos appareils. Les différentes zones du site, comme les détails de l’appareil, le feedback et le support, ainsi que la vue d’ensemble de l’appareil, bénéficient d’une nouvelle présentation interactive et moderne. Vous découvrirez également les points suivants :

- Flux de travail simplifiés sur toutes les plateformes d’appareils
- Flux d’identification et d’inscription des appareils améliorés
- Plus de messages d’erreur utiles
- Langage plus convivial, avec moins de jargon technique
- Possibilité de partager des liens directs vers les applications
- Performances améliorées des grands catalogues d’applications
- Accessibilité accrue pour tous les utilisateurs  

La [documentation du site web Portail d’entreprise Intune](https://docs.microsoft.com/en-us/intune-user-help/using-the-intune-company-portal-website) a été mise à jour pour refléter ces modifications. Pour voir un exemple des améliorations de l’application, consultez [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Détection de jailbreak améliorée dans les rapports de conformité<!-- 2198738 -->
Les états du paramètre de détection de jailbreak améliorée apparaissent désormais dans les rapports de conformité de la console d’administration.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-policies---1081974-eeready--"></a>Étiquettes de délimitation pour les stratégies <!--1081974 eeready-->
Vous pouvez [créer des étiquettes de délimitation](scope-tags.md) pour limiter l’accès aux ressources Intune. Ajoutez une étiquette de délimitation à une attribution de rôle, puis l’étiquette de délimitation à un profil de configuration. Le rôle a uniquement accès aux ressources avec des profils de configuration qui ont des étiquettes de délimitation correspondantes (ou aucune étiquette de délimitation).

## <a name="week-of-august-14-2018"></a>Semaine du 14 août 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Prise en charge de macOS pour le Programme d’inscription des appareils Apple <!-- 747651 -->
Intune prend maintenant en charge l’inscription d’appareils macOS dans le Programme d’inscription des appareils (DEP) Apple. Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils d’Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Semaine du 23 juillet 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Prise en charge des applications métier pour macOS <!-- 1895847 -->
Microsoft Intune permet aux applications métier macOS d’être déployées en mode **Obligatoire** ou **Disponible avec inscription**. Pour les utilisateurs finaux, les applications peuvent être déployées en mode **Disponible** à l’aide du Portail d’entreprise pour macOS ou du [site web Portail d’entreprise](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Prise en charge des applications intégrées iOS pour le mode kiosque <!-- 2051098 -->
En plus des applications du Store et des applications gérées, vous pouvez maintenant sélectionner une application intégrée (par exemple, Safari) qui s’exécute en mode kiosque sur un appareil iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modifier vos déploiements d’applications Office 365 Pro Plus <!-- 2150145 -->
En tant qu’administrateur Microsoft Intune, vous avez une plus grande capacité de modification de vos déploiements d’applications Office 365 Pro Plus. En outre, vous n’avez plus à supprimer vos déploiements pour modifier des propriétés de la suite. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications**. Dans la liste des applications, sélectionnez votre suite Office 365 Pro Plus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>SDK d’application Intune pour Android mis à jour disponible <!-- 2744271-->

Une version mise à jour du SDK d’application Intune pour Android est disponible pour prendre en charge la version Android P. Si vous êtes un développeur d’applications et que vous utilisez le SDK Intune pour Android, vous devez installer la version mise à jour du SDK d’application Intune pour garantir que les fonctionnalités Intune au sein de vos applications Android continuent de fonctionner comme prévu sur les appareils Android P. Cette version du SDK d’application Intune fournit un plug-in intégré qui effectue les mises à jour du Kit SDK. Vous n’avez pas besoin de réécrire le code existant qui est intégré. Pour plus d’informations, consultez [SDK Intune pour Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si vous utilisez l’ancien style de génération de badge pour Intune, nous vous recommandons d’utiliser l’icône porte-documents. Pour plus d’informations sur la personnalisation, consultez [ce référentiel GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Utiliser S/MIME pour chiffrer et signer les appareils d’un utilisateur  <!-- 1333642 -->
Cette mise à jour inclut le chiffrement S/MIME des e-mails à l’aide d’un nouveau profil de certificat importé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > type de profil **Certificat PKCS importé**). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :

- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.

Prise en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Créer une stratégie de conformité des appareils à l’aide de paramètres de pare-feu sur ses appareils macOS <!-- 1497640 -->
Quand vous créez une stratégie de conformité macOS (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : macOS** > **Sécurité du système**), de nouveaux paramètres **Pare-feu** sont disponibles : 

- **Pare-feu** : configurez la façon dont les connexions entrantes sont traitées dans votre environnement.
- **Connexions entrantes** : **Bloquer** toutes les connexions entrantes, à l’exception de celles nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage.
- **Mode furtif** : **Activer** le mode furtif pour empêcher l’appareil de répondre aux demandes de sondage. L’appareil continue de répondre aux requêtes entrantes des applications autorisées.

S’applique à : macOS 10.12 et versions ultérieures

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nouveau profil de configuration d’appareils Wi-Fi pour Windows 10 et ultérieur <!-- 1879077 -->
Actuellement, vous pouvez importer et exporter des profils Wi-Fi à l’aide de fichiers XML. Cette mise à jour vous permet de créer un profil de configuration d’appareils Wi-Fi directement dans Intune, tout comme dans certaines autres plateformes.

Pour créer le profil, ouvrez **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Wi-Fi**. 

S’applique à Windows 10 et versions ultérieures.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>Kiosque (obsolète) est grisé et ne peut pas être modifié. <!-- 2149998 eeready -->
La [fonctionnalité Kiosque](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuration de l’appareil** > **Profils** > **Créer un profil**  >  **Windows 10 et ultérieur** > **Restrictions d’appareil**) est obsolète et remplacée par [Paramètres Kiosque pour Windows 10 et ultérieur](kiosk-settings.md). Avec cette mise à jour, la fonctionnalité **Kiosque (obsolète)** est grisée et il est impossible de changer ou de mettre à jour l’interface utilisateur. 

Pour activer le mode Kiosque, consultez [Paramètres Kiosque pour Windows 10 et ultérieur](kiosk-settings.md).

S’applique à Windows 10 et ultérieur, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>Utilisation d’autorités de certification tierces par les API <!-- 2184013 -->
Dans cette mise à jour, une API Java permet l’intégration d’autorités de certification tierces à Intune et SCEP. Ensuite, les utilisateurs pourront ajouter le certificat SCEP à un profil et l’appliqueront aux appareils avec MDM.

Actuellement, Intune prend en charge les [demandes SCEP avec les services de certificats Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Affichage ou masquage du bouton Terminer la session sur un navigateur Kiosque <!-- 2455253 -->
Vous pouvez maintenant configurer les navigateurs Kiosque pour afficher ou non le bouton Terminer la session. Vous pourrez voir la commande dans **Configuration de l’appareil** > **Kiosque (préversion)** > **Navigateur web kiosque**. Si elle est activée, quand un utilisateur clique sur le bouton, l’application demande une confirmation pour terminer la session. Lorsque vous confirmez, le navigateur efface toutes les données de navigation et retourne à l’URL par défaut.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Créer un profil de configuration mobile eSIM <!-- 2564077 -->
Dans **Configuration de l’appareil**, vous pouvez créer un profil mobile eSIM. Vous pouvez importer un fichier qui contient les codes d’activation mobiles fournis par votre opérateur mobile. Vous pouvez ensuite déployer ces profils sur vos appareils Windows 10 eSIM LTE, tels que Surface Pro LTE et autres appareils compatibles eSIM.

Vérifiez si vos [appareils prennent en charge les profils eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

S’applique à Windows 10 et versions ultérieures. 




### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marquer automatiquement les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile comme « entreprise ». <!-- 2404851 -->
Par défaut, les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile sont maintenant marqués **entreprise** sous **Propriété de l’appareil**. Vous n’avez pas à identifier manuellement les appareils d’entreprise avec leur numéro IMEI ni de série avant de les inscrire à l’aide de l’inscription Knox Mobile.

### <a name="device-management"></a>Gestion des appareils

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Suppression en bloc d’appareils dans le panneau Appareils <!-- 1793693 -->

Vous pouvez maintenant supprimer plusieurs appareils à la fois dans le panneau Appareils. Choisissez **Appareils** > **Tous les appareils** > sélectionner les appareils à supprimer > **Supprimer**. Pour les appareils qui ne peuvent pas être supprimés, une alerte s’affiche.

## <a name="week-of-july-16-2018"></a>Semaine du 16 juillet 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Nouvelles opportunités de synchronisation dans l’application Portail d’entreprise pour Windows  
L’application Portail d’entreprise pour Windows vous permet désormais de lancer une synchronisation directement à partir de la barre des tâches Windows et du menu Démarrer. Cette fonctionnalité est particulièrement utile si votre seule tâche consiste à synchroniser des appareils et à accéder aux ressources d’entreprise. Pour accéder à la nouvelle fonctionnalité, cliquez avec le bouton droit sur l’icône Portail d’entreprise épinglée à votre barre des tâches ou au menu Démarrer. Dans les options de menu (également appelées liste de raccourcis), sélectionnez **Synchroniser cet appareil**. Le portail d’entreprise s’ouvre à la page **Paramètres** et lance la synchronisation. Pour examiner les nouvelles fonctionnalités, consultez [Nouveautés de l’interface utilisateur](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nouvelles expériences d’exploration dans l’application Portail d’entreprise pour Windows  

Désormais, quand vous parcourez ou recherchez des applications dans l’application Portail d’entreprise pour Windows, vous pouvez basculer entre la vue **Vignettes** existante et la nouvelle vue **Détails**. La nouvelle vue répertorie les détails des applications, tels que le nom, l’éditeur, la date de publication et l’état d’installation.  

La vue **Installée** de la page **Applications** vous permet de voir les détails concernant les installations d’applications terminées et en cours. Pour voir à quoi ressemble la nouvelle vue, consultez [Nouveautés de l’interface utilisateur](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Amélioration de l’expérience de l’application Portail d’entreprise pour les gestionnaires d’inscription d’appareil  
Quand un gestionnaire d’inscription d’appareil se connecte à l’application Portail d’entreprise pour Windows, l’application affiche à présent uniquement l’appareil en cours d’exécution actuel du gestionnaire. Cette amélioration permet de réduire les délais d’attente qui se produisaient auparavant quand l’application essayait d’afficher tous les appareils inscrits par le gestionnaire d’inscription d’appareil.  


## <a name="week-of-july-9-2018"></a>Semaine du 9 juillet 2018

### <a name="app-management"></a>Gestion d'applications

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquer l’accès à l’application en fonction des modèles et des fournisseurs d’appareils non approuvés  <!-- 1425689 ! -->
L’administrateur informatique Intune peut appliquer une liste donnée de fabricants Android et/ou de modèles iOS par le biais de stratégies Intune App Protection. L’administrateur informatique peut fournir une liste de fabricants (séparés par des points-virgules) pour les stratégies Android et une liste de modèles d’appareils pour les stratégies iOS. Les stratégies de protection des applications Intune concernent uniquement Android et iOS. Deux actions distinctes peuvent être effectuées sur cette liste donnée :
- Blocage de l’accès à l’application sur les appareils qui ne figurent pas dans la liste, ou
- Réinitialisation sélective des données d’entreprise sur les appareils qui ne figurent pas dans la liste 

L’utilisateur ne peut pas accéder à l’application cible si les conditions requises par la stratégie ne sont pas remplies. En fonction des paramètres, l’utilisateur peut être bloqué ou une réinitialisation sélective de ses données d’entreprise est effectuée dans l’application. Sur les appareils iOS, cette fonctionnalité nécessite la participation d’applications (comme WXP, Outlook, Managed Browser ou Yammer) pour intégrer le SDK Intune App dans le but d’appliquer cette fonctionnalité avec les applications ciblées. Cette intégration se produit par propagation et dépend des équipes d’application spécifiques. Sur Android, cette fonctionnalité nécessite la version la plus récente du portail d’entreprise. 

Sur les appareils de l’utilisateur final, le client Intune effectue une action sur la base d’une mise en correspondance simple des chaînes spécifiées dans le panneau Intune pour les stratégies de protection d’application. Cela dépend entièrement de la valeur signalée par l’appareil. Par conséquent, il est conseillé à l’administrateur informatique de vérifier que le comportement prévu est exact. Pour ce faire, vous pouvez tester ce paramètre en ciblant différents fabricants d’appareils et modèles sur un petit groupe d’utilisateurs. Dans Microsoft Intune, sélectionnez **Applications clientes** > **Stratégies de protection des applications** pour afficher et ajouter des stratégies de protection des applications. Pour plus d’informations sur les stratégies de protection d’applications, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md) et [Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Accès aux builds de préversion du portail d’entreprise macOS <!-- 1734766 -->
À l’aide de Microsoft AutoUpdate, vous pouvez vous inscrire pour recevoir des builds de manière anticipée en rejoignant le programme Insider. L’inscription vous permet d’utiliser le portail d’entreprise mis à jour avant qu’il soit accessible à vos utilisateurs finaux. Pour plus d’informations, consultez le [blog Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Semaine du 2 juillet 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Surveiller l’état de configuration d’applications iOS par appareil <!-- 880037 -->
En tant qu’administrateur Microsoft Intune, vous pouvez surveiller l’état de configuration d’applications iOS pour chaque appareil géré. À partir de **Microsoft Intune** dans le portail Azure, sélectionnez **Appareils** > **Tous les appareils**. Dans la liste des appareils gérés, sélectionnez un appareil spécifique pour afficher le panneau correspondant. Dans le panneau de l’appareil, sélectionnez **Configuration de l’application**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Actions d’accès pour les stratégies de protection des applications <!-- 1483510 -->
Vous pouvez configurer des stratégies de protection des applications afin de réinitialiser explicitement, de bloquer ou d’avertir les appareils non conformes. L’action *Réinitialiser* supprime d’un appareil les données d’entreprise de votre société. Si une réinitialisation se produit, l’utilisateur de l’appareil est informé de la raison de la réinitialisation et des étapes de correction. Pour certains paramètres, comme la version minimale du système d’exploitation, vous pourrez appliquer plusieurs actions telles que le blocage et la réinitialisation. Notez que ces actions sont déclenchées quand l’application est lancée.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Réinitialisation sélective des données d’application de l’organisation <!-- 1507030 -->
Les administrateurs peuvent désormais configurer une réinitialisation sélective des données de l’organisation comme une nouvelle action quand les conditions des paramètres d’accès APP (stratégies de protection d’application) ne sont pas remplies.  Cette fonctionnalité permet aux administrateurs de protéger et de supprimer automatiquement des données d’entreprise sensibles dans des applications en fonction de critères préconfigurés.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Révocation d’une application iOS achetée par le biais d’un programme VPP <!-- 1777384 -->
En tant qu’administrateur Microsoft Intune, vous pouvez révoquer toutes les licences pour une application iOS sélectionnée achetée via le programme d’achat en volume (VPP). Vous pouvez notifier les utilisateurs quand une application pour laquelle ils bénéficient d’une licence utilisateur ne leur est plus affectée. La révocation d’une licence d’application ne désinstalle pas l’application VPP de l’appareil. Pour désinstaller une application VPP, vous devez remplacer l’action d’attribution par **Désinstaller**. Le nombre de licences récupérées est répercutée dans le nœud **Applications sous licence** dans la charge de travail **Application** d’Intune. Pour plus d’informations sur les applications VPP iOS, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Mises à jour pour les messages de non-conformité dans l’application Portail d’entreprise <!-- 1832222 -->
Nous avons révisé les messages que les utilisateurs d’appareils voient quand un appareil est hors conformité. Les messages conservent leur sens d’origine, mais ils ont été formulés dans un style plus convivial et avec moins de jargon technique. Nous avons également actualisé les liens vers la documentation et les étapes de correction pour qu’ils soient à jour.
Voici un exemple d’amélioration de message, avec le texte avant et après modification :
- **Avant** : *Cet appareil n’a pas contacté le service Intune dans l’intervalle de temps spécifié par votre administrateur informatique. Pour résoudre ce problème, ouvrez l’application Portail d’entreprise sur votre appareil et cliquez sur le bouton Vérifier la conformité.*
- **Après** : *Votre appareil ne s’est pas connecté à votre organisation depuis un certain temps. Pour rétablir la connexion, ouvrez l’application Portail d’entreprise sur votre appareil, puis appuyez sur Vérifier les paramètres de votre appareil.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Révoquer une licence d’application VPP iOS <!-- 1863797 -->
En tant qu’administrateur, vous pouvez récupérer une licence d’application VPP iOS attribuée à un utilisateur ou un appareil. Désinstaller une application VPP iOS vous permet également de récupérer la licence de l’application. Avant de désinstaller l’application, l’utilisateur ou l’appareil doit être supprimé du groupe sur lequel elle est ciblée. La suppression de l’utilisateur ou de l’appareil du groupe permet d’éviter une réinstallation de l’application. Une fois ces étapes terminées, vous pouvez choisir d’attribuer la licence de l’application à un autre utilisateur ou appareil. Pour plus d’informations sur les licences d’application VPP iOS, consultez [Gérer les applications iOS achetées en volume dans Microsoft Intune](vpp-apps-ios.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Sélectionnez les catégories d’appareils en utilisant les paramètres Accès scolaire ou professionnel <!-- 1058963 eenotready --> 
Si vous avez activé le [mappage de groupe d’appareils](https://docs.microsoft.com/en-us/intune/device-group-mapping), les utilisateurs de Windows 10 seront désormais invités à sélectionner une catégorie d’appareils après l’inscription via le bouton **Se connecter** situé dans **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utiliser SamAccountName comme nom d’utilisateur de compte pour les profils de messagerie <!-- 1500307 -->
Vous pouvez utiliser le **SamAccountName** local comme nom d’utilisateur de compte pour les profils de messagerie pour Android, iOS et Windows 10. Vous pouvez également obtenir le domaine à partir de l’attribut `domain` ou `ntdomain` dans Azure Active Directory (Azure AD). Il est également possible d’entrer un domaine statique personnalisé.

Pour utiliser cette fonctionnalité, vous devez synchroniser l’attribut `sAMAccountName` de votre environnement Active Directory local avec Azure AD.

S’applique à : [Andoid](email-settings-android.md), [iOS](email-settings-ios.md) et [Windows 10 et versions ultérieures](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Affichage des profils de configuration d’appareil en conflit <!-- 1556983 -->
Dans **Configuration de l’appareil**, vous voyez une liste des profils existants. Avec cette mise à jour, une nouvelle colonne qui fournit des détails sur les profils en conflit a été ajoutée. Vous pouvez sélectionner une ligne en conflit pour voir le paramètre et le profil en conflit. 

Découvrez-en plus sur la [gestion des profils de configuration](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nouveaux états pour les appareils dans la conformité des appareils <!-- 2308882 -->
Dans **Conformité de l’appareil** > **Stratégies** > Sélectionner une stratégie > **Vue d’ensemble**, les nouveaux états suivants ont été ajoutés :
- réussi
- erreur
- conflit
- en attente
- non applicable. Une image indiquant le nombre d’appareils d’une autre plateforme est également affichée. Par exemple, si vous regardez un profil iOS, la nouvelle vignette indique le nombre d’appareils non iOS qui sont également attribués à ce profil. Consultez [Stratégies de conformité des appareils](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>La conformité de l’appareil prend en charge les solutions antivirus tierces <!-- 2325484 -->
Quand vous créez une stratégie de conformité des appareils (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : Windows 10 et versions ultérieures** > **Paramètres** > **Sécurité du système**), il existe de nouvelles options **[Sécurité de l’appareil](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** : 
- **Antivirus** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 
- **Logiciel anti-espion** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 

S’applique à : Windows 10 et versions ultérieures 

### <a name="device-enrollment"></a>Inscription des appareils

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Colonne indiquant les appareils sans profils dans la liste des jetons du programme d’inscription <!-- 1853904 -->
La liste des jetons du programme d’inscription contient une nouvelle colonne qui indique le nombre d’appareils auxquels aucun profil n’a été affecté. Les administrateurs peuvent ainsi affecter aisément des profils à ces appareils avant de les octroyer à des utilisateurs. Pour voir la nouvelle colonne, accédez à **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.

### <a name="device-management"></a>Gestion des appareils

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Changement des noms Google pour Android for Work et Play for Work <!--842873 -->
Intune a mis à jour la terminologie « Android for Work » pour refléter les changements apportés à la personnalisation de Google. Les termes « Android for Work » et « Play for Work » ne sont plus utilisés. Une terminologie différente est utilisée en fonction du contexte :
- « Android Enterprise » fait référence à la pile de gestion Android moderne globale.
- « Profil professionnel » ou « Propriétaire du profil » fait référence à des appareils BYOD gérés avec des profils professionnels.
- « Google Play géré » fait référence à l’App Store Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Règles de suppression des appareils <!-- 1609459 -->
De nouvelles règles sont disponibles pour vous permettre de supprimer automatiquement les appareils qui n’ont fait l’objet d’aucun archivage pendant un nombre de jours défini par vous-même. Pour voir la nouvelle règle, accédez au volet **Intune**, sélectionnez **Appareils**, puis sélectionnez **Règles de nettoyage d’appareil**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Prise en charge des appareils Android appartenant à l’entreprise et à usage unique <!-- 1630973 -->

Intune prend désormais en charge les appareils Android hautement gérés, verrouillés et de style kiosque. Cela permet aux administrateurs de verrouiller davantage l’utilisation d’un appareil à une seule application ou à un petit ensemble d’applications, et empêche les utilisateurs d’activer d’autres applications ou d’effectuer d’autres actions sur l’appareil. Pour configurer un appareil en mode kiosque Android, accédez à Intune > **Inscription de l’appareil** > **Inscription Android** > **Inscriptions d’appareils en mode kiosque et tâche**. Pour plus d’informations, consultez [Configurer l’inscription des appareils kiosque Android entreprise](android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Consultation par ligne des identificateurs d’appareil d’entreprise en double chargés <!-- 2203794-->
Pendant le chargement d’ID d’appareils d’entreprise, Intune fournit désormais une liste de tous les doublons et vous donne la possibilité de remplacer ou de conserver les informations existantes. Le rapport s’affiche s’il existe des doublons après avoir choisi **Inscription de l’appareil** > **Identificateurs d’appareil d’entreprise** > **Ajouter des identificateurs**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Ajouter manuellement des identificateurs d’appareil d’entreprise <!-- 2203803 -->
Vous pouvez désormais ajouter manuellement des identificateurs d’appareil d’entreprise. Dans **Inscription de l’appareil** > **Identificateurs d’appareils d’entreprise** > **Ajouter**. 

## <a name="week-of-june-25-2018"></a>Semaine du 25 juin 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo : nouveau partenaire de Mobile Threat Defense <!-- 1169249 -->

Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Pradeo, une solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Semaine du 18 juin 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Prise en charge mobile Edge pour les stratégies de protection des applications Intune <!-- 1817882 -->

Le navigateur Microsoft Edge pour appareils mobiles prend maintenant en charge les stratégies de protection des applications définies dans Intune.

## <a name="week-of-june-11-2018"></a>Semaine du 11 juin 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Utiliser le mode FIPS avec le connecteur NDES Certificate <!-- 1333688 -->
Quand vous installiez le connecteur NDES Certificate sur un ordinateur sur lequel le mode FIPS (Federal Information Processing Standard) est activé, l’émission et la révocation de certificats ne fonctionnaient pas comme prévu. Avec cette mise à jour, la prise en charge de la norme FIPS est incluse avec le connecteur NDES Certificate. 

Cette mise à jour comprend également :

- Le connecteur NDES Certificate nécessite .NET 4.5 Framework, qui est automatiquement inclus avec Windows Server 2016 et Windows Server 2012 R2. Précédemment, .NET 3.5 Framework était la version minimale exigée.
- La prise en charge de TLS 1.2 est incluse avec le connecteur NDES Certificate. Ainsi, si le serveur avec le connecteur NDES Certificate installé prend en charge TLS 1.2, TLS 1.2 est utilisé. Si le serveur ne prend pas en charge TLS 1.2, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

Pour plus d’informations, consultez [Configurer et utiliser des certificats SCEP ](certificates-scep-configure.md) et [Configurer et utiliser des certificats PKCS](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Semaine du 4 juin 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Récupérer l’ID de modèle utilisateur de l’application associé (AUMID) pour les applications Microsoft Store pour Entreprises en mode kiosque <!-- 1560077 ! -->
Intune peut désormais récupérer les ID de modèle utilisateur d’application (AUMID) pour les applications Microsoft Store pour Entreprises afin de fournir une configuration améliorée du profil kiosque.

Pour plus d’informations sur les applications Microsoft Store pour Entreprises, consultez [Gérer des applications à partir du Microsoft Store pour Entreprises](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nouvelle page de personnalisation du portail d’entreprise <!-- 1916370 -->
La page de personnalisation du portail d’entreprise a une nouvelle mise en page, de nouveaux messages et de nouvelles info-bulles.


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Prise en charge des profils de VPN Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->
Avec cette mise à jour, vous pouvez choisir Palo Alto Networks GlobalProtect comme type de connexion VPN pour les profils VPN dans Intune (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Type de profil** > **VPN**). Dans cette version, les plateformes suivantes sont prises en charge : 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ajouts aux paramètres Options de sécurité locales de l’appareil <!-- 1403702 -->
Vous pouvez désormais configurer des paramètres Options de sécurité locales de l’appareil supplémentaires pour les appareils Windows 10. Des paramètres supplémentaires sont disponibles dans les domaines Client réseau Microsoft, Serveur réseau Microsoft, Accès et sécurité réseau, ainsi qu’Ouverture de session interactive. Recherchez ces paramètres dans la catégorie Endpoint Protection quand vous créez une stratégie de configuration d’appareil Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Activer le mode kiosque sur les appareils Windows 10 <!-- 1560072 ! -->
Sur les appareils Windows 10, vous pouvez créer un profil de configuration et activer le mode kiosque (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** > **Restrictions de l’appareil** > **Kiosque**). Dans cette mise à jour, le paramètre **Kiosque (préversion)** est renommé **Kiosque (obsolète)**. **Kiosque (obsolète)** n’est plus recommandé, mais continuera à fonctionner jusqu’à la mise à jour de juillet. **Kiosque (obsolète)** est remplacé par le nouveau type de profil **Kiosque** (**Créer un profil** > **Windows 10** > **Kiosque (préversion)**), qui contiendra les paramètres permettant de configurer des kiosques sur Windows 10 RS4 et ultérieur.

S’applique à Windows 10 et versions ultérieures.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Le graphique utilisateur des profils d’appareil est de retour <!-- 2160133 -->
Tout en améliorant les chiffres indiqués sur le graphique des profils d’appareil (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble** ), le graphique utilisateur avait été supprimé temporairement.

Avec cette mise à jour, le graphique utilisateur est de retour et affiché dans le portail Azure.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Prise en charge de l’inscription Windows Autopilot sans authentification utilisateur <!-- 1165118 wnready -->
Intune prend désormais en charge l’inscription Windows Autopilot sans authentification utilisateur. Il s’agit d’une nouvelle option dans le profil de déploiement Windows Autopilot, « Mode de déploiement Autopilot », définie sur « Déploiement autonome ».  L’appareil doit exécuter Windows 10 Insider Preview Build 17672 ou une version ultérieure et posséder une puce TPM 2.0 pour effectuer correctement ce type d’inscription. Dans la mesure où aucune authentification utilisateur n’est exigée, vous devez affecter cette option uniquement aux appareils sur lesquels vous avez un contrôle physique.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Nouveau paramètre de langue/région lors de la configuration OOBE pour AutoPilot <!-- 1821766 eeready -->
Un nouveau paramètre de configuration est disponible pour définir la langue et la région des profils Autopilot pendant l’expérience OOBE (Out of Box Experience). Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nouveau paramètre de configuration du clavier de l’appareil <!-- 1821768 -->
Un nouveau paramètre sera disponible pour configurer le clavier pour les profils AutoPilot pendant l’expérience OOBE. Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Déplacement des profils AutoPilot vers le ciblage de groupe <!-- 1877935 -->
Des profils de déploiement AutoPilot peuvent être affectés à des groupes Azure AD contenant des appareils AutoPilot.

### <a name="device-management"></a>Gestion des appareils

#### <a name="set-compliance-by-device-location----851881----"></a>Définir la conformité par emplacement de l’appareil <!-- 851881 ! -->
Dans certains cas, vous souhaiterez peut-être limiter l’accès aux ressources d’entreprise à un emplacement spécifique, défini par une connexion réseau. Vous pouvez désormais créer une stratégie de conformité (**Conformité de l’appareil** > **Emplacements**) en fonction de l’adresse IP de l’appareil. Si l’appareil bascule en dehors de la plage IP, il ne peut plus accéder aux ressources d’entreprise.

S’applique à : appareils Android 6.0 et ultérieur, avec l’application Portail d’entreprise mise à jour

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Empêcher l’installation d’applications et d’expériences consommateur sur les appareils AutoPilot Windows 10 Entreprise RS4 <!-- 1621980 -->
Vous pourrez empêcher l’installation d’applications et d’expériences consommateur sur vos appareils AutoPilot Windows 10 Entreprise RS4. Pour voir cette fonctionnalité, accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Plateforme** = **Windows 10 ou version ultérieure** > **Type de profil** = **Restrictions de l’appareil** > **Configurer** > **Windows à la une** > **Fonctionnalités grand public**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Désinstaller la dernière version à partir de mises à jour logicielles Windows 10 <!-- 1732948 eeready -->
Si vous détectez un problème important sur vos machines Windows 10, vous pouvez choisir de désinstaller (restaurer) la dernière mise à jour des fonctionnalités ou la dernière mise à jour qualité. La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil. La désinstallation déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10. Pour les mises à jour des fonctionnalités en particulier, vous pouvez limiter de 2 à 60 jours la durée pendant laquelle une désinstallation de la version la plus récente peut être appliquée. Pour définir des options de désinstallation de mise à jour logicielle, sélectionnez **Mises à jour logicielles** dans le panneau **Microsoft Intune** dans le portail Azure. Sélectionnez ensuite **Anneaux de mise à jour Windows 10** dans le panneau **Mises à jour logicielles**. Vous pouvez alors choisir l’option **Désinstaller** dans la section **Vue d’ensemble**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Rechercher dans tous les appareils l’IMEI et le numéro de série <!-- 1793685 -->
Vous pouvez désormais rechercher les IMEI et les numéros de série dans le panneau Tous les appareils (l’e-mail, l’UPN, le nom de l’appareil et le nom d’administration restent disponibles). Dans Intune, choisissez **Appareils** > **Tous les appareils** > entrez votre recherche dans la zone de recherche.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Le champ de nom de gestion sera modifiable <!-- 1875989 -->
Vous pourrez maintenant modifier le champ de nom de gestion dans le panneau **Propriétés** d’un appareil. Pour modifier ce champ, choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil > **Propriétés**. Vous pouvez utiliser le champ de nom de gestion pour identifier un appareil de manière unique.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nouveau filtre Tous les appareils : Catégorie d’appareil <!-- 1878520 -->
Vous pouvez désormais filtrer la liste **Tous les appareils** par catégorie d’appareil. Pour ce faire, choisissez **Appareils** > **Tous les appareils** > **Filtre** > **Catégorie d’appareil**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Utiliser TeamViewer pour partager l’écran des appareils iOS et MacOS <!-- 1985547 -->
Les administrateurs peuvent désormais se connecter à [TeamViewer](device-profile-android-teamviewer.md) et démarrer une session de partage d’écran avec des appareils iOS et macOS. Les utilisateurs d’iPhone, iPad et macOS pourront partager leurs écrans en direct avec tout autre appareil de bureau ou portable. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Prise en charge de connecteurs Exchange multiples <!-- 2070451 -->
Vous n’êtes plus limité à un seul connecteur Microsoft Intune Exchange par locataire. Intune prend désormais en charge plusieurs connecteurs Exchange afin que vous puissiez configurer l’accès conditionnel Intune avec plusieurs organisations Exchange locales.

Avec un connecteur Exchange local Intune, vous pouvez gérer l’accès de l’appareil aux boîtes aux lettres Exchange locales en fonction de l’inscription ou non d’un appareil dans Intune et de sa conformité aux stratégies de conformité Intune. Pour configurer un connecteur, téléchargez le connecteur Exchange local Intune à partir du portail Azure et installez-le sur un serveur de votre organisation Exchange. Dans le tableau de bord Microsoft Intune, choisissez **Accès local**, puis sous **Installation**, choisissez **Connecteur Exchange ActiveSync**. Téléchargez le connecteur Exchange local et installez-le sur un serveur de votre organisation Exchange. Maintenant que vous n’êtes plus limité à un seul connecteur Exchange par client, si vous avez d’autres organisations Exchange, vous pouvez suivre le même processus pour télécharger et installer un connecteur pour chaque organisation Exchange supplémentaire.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nouveau renseignements sur le matériel : CCID <!-- 2156657 -->
L’information CCID (Chip Card Interface Device) est désormais incluse pour chaque appareil. Pour la voir, choisissez **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel** > vérifiez sous **Détails du réseau**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Affecter tous les utilisateurs et tous les appareils en tant que groupes d’étendue <!-- 2196803 -->
Vous pouvez désormais affecter tous les utilisateurs, tous les appareils, ainsi que tous les utilisateurs et appareils dans des groupes d’étendue. Pour ce faire, choisissez **Rôles Intune** > **Tous les rôles** > **Gestionnaire de stratégie et de profils** > **Affectations**  > choisissez une affectation > **Étendue (Groupes)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>Information UDID désormais incluse pour les appareils iOS et macOS <!-- 2219806 wnready-->
Pour voir l’identificateur unique de l’appareil (UDID) pour les appareils iOS et macOS, accédez à **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel**. L’UDID est disponible uniquement pour les appareils d’entreprise (tel que défini sous **Appareils** > **Tous les appareils** > choisissez un appareil > **Propriétés** > **Propriété de l’appareil**).

### <a name="intune-apps"></a>Applications Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Amélioration de la résolution des problèmes d’installation des applications <!-- 928990 -->
Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Nous publions une préversion publique de nos fonctionnalités de résolution des problèmes d’application. Vous remarquerez sous chaque appareil un nouveau nœud appelé **Applications gérées**. Il liste les applications qui ont été distribuées via MDM Intune. À l’intérieur du nœud figure une liste d’états d’installations d’applications. Si vous sélectionnez une application, vous verrez la vue de résolution des problèmes de cette application spécifique. Dans la vue de résolution des problèmes, vous verrez le cycle de vie de bout en bout de l’application, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. De plus, si l’installation de l’application a échoué, vous verrez le code d’erreur et un message utile sur la cause de l’erreur. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Stratégies de protection des applications Intune et Microsoft Edge <!-- 1818968 -->
Le navigateur Microsoft Edge pour les appareils mobiles (iOS et Android) prend désormais en charge les stratégies de protection des applications Microsoft Intune. Les utilisateurs d’appareils iOS et Android qui se connectent avec leur compte d’entreprise Azure AD dans l’application Edge seront protégés par Intune. Sur les appareils iOS, la stratégie **Exiger un navigateur géré pour le contenu web** permet aux utilisateurs d’ouvrir des liens dans Edge quand il est géré.

## <a name="week-of-may-14-2018"></a>Semaine du 14 mai 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Nécessitent l’installation de stratégies, d’applications et de profils de certificat et de réseau <!-- 1553555 -->

Les administrateurs peuvent empêcher les utilisateurs finaux d’accéder au Bureau de Windows 10 RS4 jusqu’à ce qu’Intune installe les stratégies, les applications et les profils de certificat et réseau pendant le provisionnement des appareils AutoPilot. Pour plus d’informations, consultez [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configuration de vos stratégies de protection des applications<!-- 2144597 Part 2 -->

Dans le portail Azure, au lieu d’accéder au panneau du service Intune App Protection, vous accédez désormais simplement à Intune. Il n’existe plus maintenant qu’un seul emplacement pour les stratégies de protection des applications dans Intune. Notez que toutes vos stratégies de protection des applications se trouvent dans le panneau **Application mobile** d’Intune, sous **Stratégies de protection des applications**. Cette intégration permet de simplifier l’administration de la gestion de votre cloud. Gardez à l’esprit que toutes les stratégies de protection des applications sont déjà dans Intune et que vous pouvez modifier les stratégies d’accès conditionnel que vous avez précédemment configurées. Les stratégies Intune de protection des applications et d’accès conditionnel sont désormais sous **Accès conditionnel**, qui se trouve sous la section **Gérer** du panneau **Microsoft Intune** ou sous la section **Sécurité** du panneau **Azure Active Directory**. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Semaine du 7 mai 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Prise en charge de Samsung Knox Mobile Enrollment <!--1112863-->

Quand vous utilisez Intune avec Samsung Knox Mobile Enrollment (KME), vous pouvez inscrire un grand nombre d’appareils Android appartenant à l’entreprise. Les utilisateurs sur des réseaux Wi-Fi ou mobiles peuvent s’inscrire en quelques clics quand ils allument leurs appareils pour la première fois. En cas d’utilisation de l’application Knox Deployment App, les appareils peuvent être inscrits à l’aide de Bluetooth ou NFC. Pour plus d’informations, consultez [Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung](android-samsung-knox-mobile-enroll.md).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Demande d’aide dans le portail d’entreprise pour Windows 10 <!-- 1874137 -->

Le portail d’entreprise pour Windows 10 envoie maintenant les journaux d’application directement à Microsoft quand l’utilisateur lance le flux de travail pour obtenir de l’aide sur un problème. Cela facilite le dépannage et la résolution des problèmes portés à l’attention de Microsoft.

## <a name="week-of-april-23-2018"></a>Semaine du 23 avril 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Prise en charge des codes secrets pour les codes PIN MAM sur Android<!-- 1438086 -->

Les administrateurs Intune peuvent définir une condition de lancement d’application pour appliquer un code secret au lieu d’un code PIN MAM numérique. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Intune prend en charge un code secret comme le code PIN numérique existant, pouvant définir une longueur minimale et autorisant la répétition des caractères et des séquences par le biais de la console d’administration. Cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise sur Android. Cette fonctionnalité est déjà disponible pour iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Prise en charge des applications métier pour macOS <!-- 1473977 -->
Microsoft Intune permettra d’installer des applications métier macOS à partir du portail Azure. Vous pourrez ajouter une application métier macOS à Intune après qu’elle a été prétraitée par l’outil disponible dans GitHub. Dans le portail Azure, choisissez **Applications clientes** à partir du panneau **Intune**. Dans le panneau **Applications clientes**, choisissez **Applications** > **Ajouter**. Dans le panneau **Ajouter une application**, sélectionnez **Application métier**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Intégration des groupes Tous les utilisateurs et Tous les appareils pour l’affectation d’applications Android for Work (AFW) <!-- 1813073 -->
Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications AFW. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune réinstalle les applications nécessaires qui sont désinstallées par les utilisateurs <!-- 1947010 -->
Si un utilisateur final désinstalle une application obligatoire, Intune la réinstalle automatiquement en moins de 24 heures au lieu d’attendre le cycle de réévaluation de 7 jours.

### <a name="device-configuration"></a>Configuration des appareils

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Le graphique des profils d’appareil et la liste d’états affichent tous les appareils contenus dans un groupe <!-- 1449153 eeready -->
Quand vous configurez un profil d’appareil (**Configuration de l’appareil** > **Profils**), vous choisissez le profil d’appareil, par exemple iOS. Vous affectez ce profil à un groupe qui inclut les appareils iOS et les appareils non-iOS. Le nombre sur le graphique indique que le profil est appliqué aux appareils iOS *et* non-iOS (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**). Quand vous sélectionnez le graphique sous l’onglet **Vue d’ensemble**, la section **État de l’appareil** liste tous les appareils contenus dans le groupe, au lieu des appareils iOS uniquement. 

Avec cette mise à jour, le graphique (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**) affiche uniquement le nombre associé à un profil d’appareil spécifique. Par exemple, si le profil d’appareil de la configuration s’applique aux appareils iOS, le graphique indique uniquement le nombre des appareils iOS. Quand l’utilisateur sélectionne le graphique et ouvre la section **État de l’appareil**, seuls les appareils iOS sont listés.

Le graphique utilisateur est supprimé le temps que cette mise à jour soit effectuée. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN Always On pour Windows 10 <!--1333666 -->

Actuellement, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) peut être utilisé sur les appareils Windows 10 à l’aide d’un profil de réseau privé virtuel (VPN) personnalisé créé à l’aide d’OMA-URI.

Avec cette mise à jour, les administrateurs peuvent activer les profils VPN Always On pour Windows 10 directement dans Intune au sein du portail Azure. Les profils VPN Always On se connecteront automatiquement :

- À la connexion des utilisateurs à leurs appareils
- Au changement du réseau sur l’appareil
- À la réactivation de l’écran de l’appareil

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nouveaux paramètres d’imprimante pour les profils Éducation <!-- 1308900 -->

Pour les profils Éducation, de nouveaux paramètres sont disponibles sous la catégorie **Imprimantes** : **Imprimantes**, **Imprimante par défaut**, **Ajouter de nouvelles imprimantes**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Afficher l’ID d’appelant dans un profil personnel - Android for Work <!--1098984 -->
Quand vous utilisez un profil personnel sur un appareil, les utilisateurs finaux ne voient pas forcément les détails relatifs à l’ID d’appelant d’un contact professionnel. 

Avec cette mise à jour, il existe un nouveau paramètre dans **Android for Work** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Afficher l’ID d’appelant du contact professionnel dans le profil personnel

Quand ce paramètre est activé (non configuré), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Quand ce paramètre est désactivé, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. 

S’applique aux appareils avec profil professionnel Android pour le système d’exploitation Android v6.0 et les versions ultérieures

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nouveaux paramètres Windows Defender Credential Guard ajoutés aux paramètres Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Avec cette mise à jour, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuration de l’appareil** > **Profils** > **Endpoint Protection**) présente les paramètres suivants : 

- **Windows Defender Credential Guard** : Active Credential Guard avec une sécurité basée sur la virtualisation. L’activation de cette fonctionnalité permet de protéger les informations d’identification au prochain redémarrage quand **Niveau de sécurité de plateforme avec démarrage sécurisé** et **Sécurité basée sur la virtualisation** sont activés. Les options sont les suivantes :
  - **Désactivé** : Si Credential Guard était activé avec l’option **Activé sans verrouillage**, cette option désactive Credential Guard à distance.

  - **Activé avec le verrouillage UEFI** : Garantit que Credential Guard ne peut pas être désactivé en utilisant une clé de Registre ou une stratégie de groupe. Pour désactiver Credential Guard après avoir utilisé ce paramètre, vous devez définir la stratégie de groupe sur « Désactivé ». Ensuite, supprimez la fonctionnalité de sécurité de chaque ordinateur, avec un utilisateur physiquement présent. Ces étapes effacent la configuration persistante dans UEFI. Tant que la configuration UEFI persiste, Credential Guard est activé.

  - **Activé sans verrouillage** : Permet de désactiver Credential Guard à distance à l’aide d’une stratégie de groupe. Les appareils utilisant ce paramètre doivent exécuter au moins Windows 10 (version 1511).

Les technologies dépendantes suivantes sont automatiquement activées lors de la configuration de Credential Guard : 

  - **Activer la sécurité basée sur la virtualisation (VBS)**  : Active la sécurité basée sur la virtualisation (VBS) au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité et nécessite le démarrage sécurisé.
  - **Démarrage sécurisé avec accès direct à la mémoire (DMA)**  : Active VBS avec démarrage sécurisé et accès direct à la mémoire. La protection DMA nécessite une prise en charge matérielle et n’est activée que sur des appareils configurés correctement. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Utiliser un nom d’objet personnalisé sur le certificat SCEP <!-- 2064190 -->
Vous pouvez utiliser le nom courant **OnPremisesSamAccountName** dans un objet personnalisé sur un profil de certificat SCEP. Par exemple, vous pouvez utiliser `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blocage des appareils photo et des captures d’écran sur Android for Work <!-- 1098977 eeready-->
Vous disposez de deux nouvelles propriétés de blocage au moment de configurer des restrictions d’appareil pour les appareils Android : 
- Appareil photo : bloque l’accès à tous les appareils photo sur l’appareil
- Capture d’écran : bloque la capture d’écran et empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée

S’applique à Android for Work.


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nouvelles étapes d’inscription pour les utilisateurs sur les appareils dotés de macOS High Sierra 10.13.2+ <!--1734567 -->
macOS High Sierra 10.13.2 a introduit le concept d’inscription MDM « approuvée par l’utilisateur ». Les inscriptions approuvées permettent à Intune de gérer certains paramètres sensibles au niveau sécurité. Pour plus d’informations, consultez la documentation de prise en charge d’Apple ici : https://support.apple.com/HT208019.

Les appareils inscrits à l’aide du Portail d’entreprise macOS sont considérés comme « non approuvés par l’utilisateur », sauf si l’utilisateur final ouvre les préférences système et fournit une approbation manuellement. À cette fin, le Portail d’entreprise macOS invite désormais les utilisateurs sur macOS 10.13.2 et ultérieur à approuver manuellement leur inscription à la fin du processus d’inscription. La console d’administration Intune indiquera si un appareil inscrit est approuvé par l’utilisateur.



### <a name="device-management"></a>Gestion des appareils

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>ATP (Protection avancée contre les menaces) et Intune sont entièrement intégrés <!-- EEready 1629303 -->

[Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indique le niveau de risque des appareils Windows 10. Dans le Centre de sécurité Windows Defender (portail ATP), vous pouvez créer une connexion à Microsoft Intune. Une fois créée, une stratégie de conformité Intune permet de déterminer un niveau de menace acceptable. Si le niveau de menace est dépassé, une stratégie d’accès conditionnel Azure AD (Active Directory) peut bloquer l’accès à différentes applications au sein de votre organisation.

Cette fonctionnalité permet à ATP d’analyser les fichiers, de détecter les menaces et de signaler tout risque sur vos appareils Windows 10.

Consultez [Activer ATP avec accès conditionnel dans Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Prise en charge des appareils sans utilisateurs <!-- 1637553 -->
Intune permet d’évaluer la conformité sur un appareil sans utilisateur, comme Microsoft Surface Hub. La stratégie de conformité peut cibler des appareils spécifiques. Ainsi, la conformité, et la non-conformité, peuvent être déterminées pour les appareils auxquels aucun utilisateur n’est associé.

#### <a name="delete-autopilot-devices----1713650---"></a>Supprimer les appareils AutoPilot <!-- 1713650 -->
Les administrateurs Intune peuvent [supprimer les appareils AutoPilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Amélioration de l’expérience de suppression d’appareil <!--1832333 -->
Vous n’avez plus besoin de supprimer les données d’entreprise ou de réinitialiser un appareil aux paramètres d’usine avant de le [supprimer d’Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Pour voir la nouvelle expérience, connectez-vous à Intune et sélectionnez **Appareils** > **Tous les appareils** > nom de l’appareil > **Supprimer**.

Si vous souhaitez toujours la confirmation de réinitialisation/mise hors service, vous pouvez suivre le cycle de vie d’appareil standard en utilisant les commandes **Supprimer les données d’entreprise** et **Réinitialisation aux paramètres d’usine** avant la commande **Supprimer**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Lire les sons sur iOS en mode Perdu <!-- 1947769 -->
Quand les appareils iOS supervisés sont en [mode Perdu](device-lost-mode.md) MDM (Mobile Device Management), vous pouvez [lire un son](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Appareils** > **Tous les appareils** > sélectionnez un appareil iOS > **Vue d’ensemble** > **Plus**). La lecture du son se poursuit jusqu’à ce que l’appareil soit retiré du mode Perdu ou qu’un utilisateur désactive le son sur l’appareil. S’applique aux appareils iOS 9.3 et ultérieur.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquer ou autoriser les résultats web dans les recherches effectuées sur un appareil Intune <!--1972804-->

Les administrateurs peuvent maintenant bloquer les résultats web des recherches effectuées sur un appareil.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Amélioration des messages d’erreur liés à l’échec du chargement du certificat Push MDM Apple <!-- 2172331 -->

Le message d’erreur explique que le même identifiant Apple doit être utilisé au moment du renouvellement d’un certificat MDM existant.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Tester le portail d’entreprise pour macOS sur des machines virtuelles <!-- 2216679 -->

Nous avons publié des conseils pour aider les administrateurs informatiques à tester l’application Portail d’entreprise pour macOS sur des machines virtuelles dans Parallels Desktop et VMware Fusion. Découvrez-en plus dans [Inscrire des machines virtuelles macOS à des fins de test](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interface utilisateur

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Amélioration des vignettes d’appareil dans le portail d’entreprise Windows 10 <!--2213364 -->

Les vignettes ont été mises à jour pour être plus accessibles aux utilisateurs malvoyants et proposer un meilleur rendu pour les outils de lecture d’écran.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Envoyer des rapports de diagnostic dans l’application Portail d’entreprise pour macOS <!-- 2216677 -->
L’application Portail d’entreprise pour les appareils macOS est mise à jour pour améliorer la façon dont les utilisateurs signalent les erreurs relatives à Intune. À partir de l’application Portail d’entreprise, vos collaborateurs peuvent :

- Charger des rapports de diagnostic directement pour l’équipe de développement Microsoft.
- Envoyer par e-mail un ID d’incident à l’équipe de support informatique de votre entreprise.

Pour plus d’informations, consultez [Envoyer les erreurs pour macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune s’adapte à Fluent Design System dans l’application Portail d’entreprise pour Windows 10 <!-- 1195010 WNready -->
L’application Portail d’entreprise Intune pour Windows 10 a été mise à jour avec le [mode de navigation de Fluent Design System](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). Le long de l’application, vous remarquerez une liste verticale statique de toutes les pages de niveau supérieur. Cliquez sur n’importe quel lien pour afficher des pages et passer de l’une à l’autre rapidement. Il s’agit de la première d’une série de mises à jour que vous verrez dans le cadre de nos efforts constants pour créer une expérience plus adaptive, empathique et familière dans Intune. Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semaine du 16 avril 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Utiliser le client Cisco AnyConnect pour iOS <!-- EEready 1333708 -->

Quand vous créez un profil VPN pour iOS, vous disposez désormais de deux options : **Cisco AnyConnect** et **Cisco Legacy AnyConnect**. Les profils Cisco AnyConnect prennent en charge les versions 4.0.7x et ultérieures. Les profils VPN Cisco AnyConnect pour iOS existants se nomment **Cisco Legacy AnyConnect** et continuent de fonctionner avec Cisco AnyConnect 4.0.5x et les versions antérieures, comme c’est le cas aujourd’hui.

> [!NOTE]
> Ce changement s’applique uniquement à iOS. Il existe toujours une seule option Cisco AnyConnect pour les plateformes Android, Android for Work et macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Les appareils macOS inscrits auprès de Jamf peuvent désormais s’inscrire auprès d’Intune <!-- 2370684 -->

Les versions 1.3 et 1.4 du portail d’entreprise macOS n’ont pas réussi à inscrire les appareils Jamf auprès d’Intune. Ce problème est résolu dans la version 1.4.2 du portail macOS.


## <a name="week-of-april-9-2018"></a>Semaine du 9 avril 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Mise à jour de l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android <!-- 1631531 -->

Nous avons mis à jour l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android afin de l’harmoniser avec les bonnes pratiques relatives à la plateforme Android. Désormais, quand les utilisateurs rencontrent un problème dans l’application, ils peuvent appuyer sur **Menu** > **Aide** et :
- Charger les journaux de diagnostic sur le site de Microsoft
- Envoyer un e-mail décrivant le problème et indiquant l’ID d’incident à une personne du support de l’entreprise  

Pour découvrir à quoi ressemble la mise à jour de l’expérience utilisateur de l’aide, accédez à [Envoyer des journaux à l’aide de la messagerie](/intune-user-help/send-logs-to-your-it-admin-by-email-android) et [Envoyer les erreurs à Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nouveau graphique de tendance des échecs d’inscription et tableau des raisons de ces échecs <!-- 1471783 -->

Dans la page Vue d’ensemble de l’inscription, vous pouvez voir la tendance des échecs d’inscription et les cinq premières causes d’échecs. En cliquant sur le graphique ou le tableau, vous pouvez explorer les détails et trouver des conseils de dépannage, ainsi que des suggestions de correction.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Mise à jour de l’emplacement de configuration de vos stratégies de protection des applications <!-- 2144597 -->

Dans le portail Azure du service Microsoft Intune, nous allons vous rediriger temporairement du panneau de service **Intune App Protection** vers le panneau **Application mobile**. Notez que toutes vos stratégies de protection d’application sont déjà sur le panneau **Application mobile** dans Intune, sous la configuration de l’application. Au lieu d’accéder à Intune App Protection, vous accédez simplement à Intune. En avril 2018, nous mettrons fin à la redirection et nous la supprimerons complètement du panneau du service **Intune App Protection** : il n’y aura alors plus qu’un seul emplacement pour les stratégies de protection d’application dans Intune. 

**Comment cela m’affecte-t-il ?**
Ce changement affecte les clients autonomes et les clients hybrides Intune (Intune avec Configuration Manager). Cette intégration permet de simplifier l’administration de la gestion de votre cloud.

**Que faire pour se préparer à ce changement ?**
Mettez **Intune** en favori à la place du panneau de service **Intune App Protection**, et veillez à vous familiariser avec le workflow de stratégie de protection des applications dans le panneau **Application mobile** d’Intune. Pendant une courte période, nous allons assurer la redirection, puis nous supprimerons le panneau **Protection d’applications**. N’oubliez pas que toutes les stratégies de protection des applications sont déjà dans Intune, et que vous pouvez modifier vos stratégies d’accès conditionnel. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semaine du 2 avril 2018

### <a name="intune-apps"></a>Applications Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Mise à jour de l’expérience utilisateur dans l’application Portail d’entreprise pour iOS <!--1412866 -->
Nous avons publié une mise à jour majeure de l’expérience utilisateur de l’application Portail d’entreprise pour iOS. La mise à jour comporte une refonte visuelle complète incluant une apparence plus moderne. Nous avons conservé les fonctionnalités de l’application, mais nous avons étendu sa facilité d’utilisation et son accessibilité.  

Vous découvrirez également les points suivants :
- Prise en charge de l’iPhone X.
- Lancement et chargement plus rapides des applications, pour faire gagner du temps aux utilisateurs.
- Barres de progression supplémentaires pour fournir aux utilisateurs les toutes dernières informations d’état.
- Améliorations de la façon dont les utilisateurs chargent les journaux pour faciliter le signalement des problèmes.  

Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Protéger les données Exchange locales à l’aide de la stratégie de protection des applications et de l’accès conditionnel d’Intune <!-- 1056954 -->
Vous pouvez désormais utiliser les fonctionnalités APP (stratégie de protection des applications) et CA (accès conditionnel) d’Intune pour protéger l’accès aux données Exchange locales avec Outlook Mobile. Pour ajouter ou modifier une stratégie de protection des applications dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Stratégies de protection des applications**. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Semaine du 26 mars 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertes relatives à l’expiration des applications métier iOS pour Microsoft Intune <!-- 748789 -->

Dans le portail Azure, Intune vous alerte quand des applications métier iOS arrivent à expiration. Quand vous chargez une nouvelle version de l’application métier iOS, Intune supprime la notification d’expiration de la liste des applications. Cette notification d’expiration est active uniquement pour les dernières applications métier iOS chargées. Un avertissement apparaît 30 jours avant l’expiration du profil de provisionnement de l’application métier iOS. Une fois que l’expiration a eu lieu, l’état de l’alerte passe à Expiré.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personnaliser vos thèmes de portail d’entreprise avec des codes hexadécimaux<!--1049561 -->

Vous pouvez personnaliser la couleur du thème des applications Portail d’entreprise à l’aide de codes hexadécimaux. Quand vous entrez votre code hexadécimal, Intune détermine la couleur de texte qui offre le plus haut niveau de contraste entre la couleur de texte et la couleur d’arrière-plan. Vous pouvez voir un aperçu de la couleur du texte et du logo de votre entreprise par rapport à la couleur dans **Applications clientes** > **Portail d’entreprise**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusion et exclusion d’affectations d’applications en fonction de groupes pour Android Enterprise <!-- 1813081 -->

Android Enterprise (anciennement Android for Work) prend en charge l’inclusion et l’exclusion de groupes, mais ne prend pas en charge les groupes prédéfinis **Tous les utilisateurs** et **Tous les appareils**. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestion des appareils

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nouvelles améliorations de la sécurité dans le service Intune <!-- 1637539 -->   

Nous avons introduit un bouton bascule dans Intune sur Azure, qui permet aux clients autonomes Intune de définir un appareil auquel aucune stratégie n’est affectée comme étant **Conforme** (fonctionnalité de sécurité désactivée) ou **Non conforme** (fonctionnalité de sécurité activée). Cela permet de garantir l’accès aux ressources uniquement après l’évaluation de la conformité de l’appareil.

Cette fonctionnalité vous impacte différemment selon que vous avez déjà affecté ou non des stratégies de conformité.

- Si vous êtes un nouveau compte ou un compte existant, et si vous n’avez affecté aucune stratégie de conformité à vos appareils, le bouton bascule est automatiquement défini sur **Conforme**. La fonctionnalité est désactivée par défaut dans la console. L’impact est inexistant pour l’utilisateur final.
- Si vous êtes un compte existant, et si vous avez des appareils auxquels vous avez affecté une stratégie de conformité, le bouton bascule est automatiquement défini sur **Non conforme**. La fonctionnalité est activée par défaut avec le déploiement de la mise à jour de mars.

Si vous utilisez des stratégies de conformité avec un accès conditionnel, et si cette fonctionnalité est activée, les appareils auxquels aucune stratégie de conformité n’a été affectée sont désormais bloqués par l’accès conditionnel. Les utilisateurs finaux associés à ces appareils, qui étaient autorisés à accéder aux e-mails, perdent leur accès, sauf si vous affectez au moins une stratégie de conformité à tous les appareils.   

Notez que même si l’état par défaut du bouton bascule est affiché dans l’IU avec les mises à jour de mars du service Intune, cet état n’est pas appliqué immédiatement. Les changements apportés au bouton bascule n’ont aucun impact sur la conformité des appareils tant que nous n’activons pas la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Nous vous informerons via le Centre de messages quand nous aurons activé la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Cela peut prendre quelques jours, une fois que la mise à jour de mars aura été appliquée à votre service Intune.

**Informations supplémentaires** : [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Détection de jailbreak améliorée <!-- 846515 -->

La détection de jailbreak améliorée est un nouveau paramètre de conformité qui améliore la manière dont Intune évalue les appareils jailbreakés. Avec ce paramètre, l’appareil s’enregistre plus fréquemment auprès d’Intune, lequel utilise les services de géolocalisation de l’appareil, ce qui impacte la durée de vie de la batterie.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Réinitialiser les mots de passe pour les appareils Android O <!-- 1238299 -->
Vous pouvez réinitialiser les mots de passe des appareils Android 8.0 inscrits à l’aide des profils professionnels. Quand vous envoyez une demande de réinitialisation de mot de passe à un appareil Android 8.0, cela entraîne la définition d’un nouveau mot de passe de déverrouillage de l’appareil ou d’une vérification du profil managé pour l’utilisateur actuel. La vérification ou le mot de passe est envoyé et prend effet immédiatement.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ciblage des stratégies de conformité pour les appareils dans des groupes d’appareils <!--1307012 -->

Vous pouvez appliquer des stratégies de conformité en ciblant des utilisateurs au sein de groupes d’utilisateurs. Avec cette mise à jour, vous pouvez appliquer des stratégies de conformité en ciblant des appareils au sein de groupes d’appareils. Les appareils ciblés dans le cadre de groupes d’appareils ne reçoivent aucune action de conformité.

#### <a name="new-management-name-column----1333586---"></a>Nouvelle colonne Nom d’administration <!-- 1333586 -->
 Une nouvelle colonne nommée **Nom de la gestion** est disponible dans le panneau des appareils. Il s’agit d’un nom généré automatiquement, non modifiable affecté par appareil, reposant sur la formule suivante :
- Nom par défaut pour tous les appareils : <username><em><devicetype></em><enrollmenttimestamp>
- Pour les appareils ajoutés en bloc : <ID_de_package/ID_de_profil><em><DeviceType></em><EnrollmentTime>

Il s’agit d’une colonne facultative dans le panneau Appareils. Elle n’est pas disponible par défaut. Vous pouvez y accéder uniquement via le sélecteur de colonne. Le nom de l’appareil n’est pas affecté par cette nouvelle colonne.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Les appareils iOS sont invités à entrer un code confidentiel toutes les 15 minutes <!--1550837 -->
Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code PIN toutes les 15 minutes. Les utilisateurs sont continuellement sollicités jusqu’à ce qu’un code PIN soit défini.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Planifier vos mises à jour automatiques <!--1805514 -->
Intune vous permet de contrôler l’installation des mises à jour automatiques à l’aide des [paramètres des anneaux de mise à jour Windows](windows-update-for-business-configure.md). Avec cette mise à jour, vous pouvez planifier des mises à jour récurrentes : hebdomadaires, quotidiennes et horaires.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Utiliser le nom unique en tant que sujet de certificat SCEP <!--2221763 -->
Quand vous créez un profil de certificat SCEP, vous entrez le nom du sujet. Avec cette mise à jour, vous pouvez utiliser le nom unique complet en tant que sujet. Dans **Nom du sujet**, sélectionnez **Personnalisé**, puis entrez `CN={{OnPrem_Distinguished_Name}}`. Pour utiliser la variable `{{OnPrem_Distinguished_Name}}`, veillez à synchroniser l’attribut utilisateur `onpremisesdistingishedname` qui utilise [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) avec Azure AD.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Activer le partage de contacts Bluetooth - Android for Work <!--1098983 -->
Par défaut, Android empêche les contacts inclus dans le profil professionnel de se synchroniser avec des appareils Bluetooth. Ainsi, les contacts de profil professionnel ne s’affichent pas sur l’ID de l’appelant des appareils Bluetooth.

Avec cette mise à jour, il existe un nouveau paramètre dans **Android for Work** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Partage de contacts via Bluetooth

L’administrateur Intune peut configurer ces paramètres pour activer le partage. Cette démarche s’avère utile lors de l’appariement d’un appareil avec un appareil Bluetooth de voiture qui affiche l’ID de l’appelant à des fins d’utilisation en mode mains libres. Quand ce paramètre est activé, les contacts de profil professionnel sont affichés. Dans le cas contraire, ils n’apparaissent pas.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Configurer Gatekeeper pour contrôler la source de téléchargement des applications macOS <!-- 1690459 -->

Vous pouvez configurer Gatekeeper pour protéger vos appareils en contrôlant les sources de téléchargement des applications. Vous pouvez configurer les sources de téléchargement suivantes : **Mac App Store**, **Mac App Store et développeurs identifiés** ou **N’importe où**. Vous pouvez déterminer si les utilisateurs peuvent installer une application en appuyant de façon prolongée sur la touche Ctrl pour remplacer ces contrôles Gatekeeper.

Ces paramètres se trouvent sous **Configuration de l’appareil** -> **Créer un profil** -> **macOS**  ->  **Endpoint protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurer le coupe-feu applicatif Mac <!-- 1690461 -->

Vous pouvez configurer le pare-feu d’applications Mac. Vous serez ainsi en mesure de contrôler les connexions au niveau de chaque application, plutôt qu’au niveau de chaque port. Il permet ainsi d’empêcher les applications indésirables de contrôler les ports réseau ayant été ouverts pour des applications légitimes, et de profiter d’une protection optimale.

Cette fonctionnalité se trouve sous **Configuration de l’appareil** -> **Créer un profil** -> **macOS**  ->  **Endpoint protection**.

Une fois le paramètre de coupe-feu activé, vous pouvez configurer le coupe-feu à l’aide de deux stratégies :

- Bloquer toutes les connexions entrantes

   Vous pouvez bloquer toutes les connexions entrantes pour les appareils ciblés. Si vous procédez ainsi, les connexions entrantes sont bloquées pour toutes les applications.

- Autoriser ou bloquer des applications spécifiques

   Vous pouvez autoriser ou bloquer la réception de connexions entrantes pour des applications spécifiques. Vous pouvez également activer le mode furtif de manière à empêcher les réponses aux demandes de détection.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Codes et messages d’erreur détaillés <!-- 1376342 -->

Dans Configuration de l’appareil, vous trouverez des codes d’erreur et des messages d’erreur plus détaillés. Cette amélioration du compte-rendu permet de voir les paramètres, leur état et les détails relatifs au dépannage.

##### <a name="more-information"></a>Plus d’informations

- Bloquer toutes les connexions entrantes

   La réception de connexions entrantes est bloquée pour tous les services de partage (par exemple, le partage de fichiers et le partage d’écran). Les services système qui sont toujours autorisés à recevoir des connexions entrantes sont :
  - configd : implémente DHCP et d’autres services de configuration réseau
  - mDNSResponder : implémente Bonjour
  - racoon : implémente IPSec

    Pour utiliser les services de partage, assurez-vous que **Connexions entrantes** a la valeur **Non configuré** (pas **Bloquer**).

- Mode furtif

   Activez cette option pour empêcher l’ordinateur de répondre aux demandes de détection. L’ordinateur continue de répondre aux demandes entrantes pour les applications autorisées. Les demandes inattendues, comme ICMP (ping), sont ignorées.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Désactiver les vérifications au redémarrage de l’appareil <!--1805490 -->
Intune vous permet de [gérer les mises à jour logicielles]](windows-update-for-business-configure.md). Avec cette mise à jour, la propriété <strong>Vérifications de redémarrage</strong> est disponible et activée par défaut. Pour ignorer les vérifications usuelles qui se produisent au redémarrage d’un appareil (comme les utilisateurs actifs, les niveaux de batterie, etc.), sélectionnez <strong>Ignorer</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nouveaux canaux Windows 10 Insider Preview disponibles pour les anneaux de déploiement <!-- 1746293 -->
Vous pouvez désormais sélectionner les canaux de maintenance Windows 10 Insider Preview suivants quand vous créez un anneau de déploiement Windows 10 :
- Version Windows Insider &#8208; Rapide
- Version Windows Insider &#8208; Lente
- Publier la version Windows Insider 

Pour plus d’informations sur ces canaux, consultez [Gérer les versions Insider Preview](https://insider.windows.com/en-us/for-business-organization-admin/).   
Pour plus d’informations sur la création de canaux de déploiement dans Intune, consultez [Gérer les mises à jour logicielles dans Intune](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Applications Intune

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Inscription par le biais de l’application Portail d’entreprise améliorée <!-- 1874230 eeready-->
Les utilisateurs qui inscrivent un appareil à l’aide du Portail d’entreprise sur Windows 10 (build 1703) et versions ultérieures peuvent désormais effectuer la première étape de l’inscription sans quitter l’application.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens et Surface Hub apparaissent désormais dans les listes d’appareils <!--1725868 -->
Nous avons ajouté la prise en charge de l’affichage des appareils HoloLens et Surface Hub inscrits auprès d’Intune dans l’application Portail d’entreprise pour Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Catégories de livres personnalisées pour les livres électroniques achetés dans le cadre d’un programme d’achat en volume <!-- 1488911 -->
Vous pouvez créer des catégories de livres électroniques personnalisées, puis leur affecter des livres électroniques achetés en volume. Les utilisateurs finaux pourront ensuite voir les nouvelles catégories de livres électroniques et les livres affectés à ces catégories. Pour plus d’informations, consultez [Gérer les applications et les livres achetés en volume avec Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Changements de prise en charge de l’option d’envoi de commentaires dans l’application Portail d’entreprise pour Windows <!-- 2070166 -->
À compter du 30 avril 2018, l’option **Envoyer des commentaires** dans l’application Portail d’entreprise pour Windows fonctionne uniquement sur les appareils qui exécutent la Mise à jour anniversaire Windows 10 (1607) et versions ultérieures. L’option d’envoi de commentaires n’est plus prise en charge lors de l’utilisation de l’application Portail d’entreprise pour Windows avec :  
- Windows 10, version 1507  
- Windows 10, version 1511  
- Windows Phone 8.1 

Si votre appareil exécute Windows 10 RS1 ou ultérieur, téléchargez la dernière version de l’application Portail d’entreprise Windows à partir du Store. Si vous exécutez une version non prise en charge, continuez à envoyer des commentaires par le biais des canaux suivants : 
- L’application Hub de commentaires sur Windows 10
- L’adresse e-mail WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nouveaux paramètres Windows Defender Application Guard <!-- 1631890 -->

- **Activer l’accélération graphique** : les administrateurs peuvent activer un processeur graphique virtuel pour Windows Defender Application Guard. Ce paramètre permet à l’UC de décharger l’affichage graphique sur l’unité de traitement graphique virtuelle. Cela peut améliorer les performances quand vous utilisez des sites web qui consomment beaucoup de graphiques ou regardez une vidéo au sein du conteneur.

- **SaveFilestoHost** : les administrateurs peuvent autoriser le passage des fichiers depuis Microsoft Edge, qui s’exécute dans le conteneur, vers le système de fichiers hôte. L’activation de ce paramètre permet aux utilisateurs de télécharger des fichiers à partir de Microsoft Edge, dans le conteneur, vers le système de fichiers hôte.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Stratégies de protection MAM ciblées en fonction de l’état de gestion <!-- 1665993 -->
Vous pouvez cibler des stratégies MAM en fonction de l’état de gestion de l’appareil :
- **Appareils Android** : vous pouvez cibler des appareils non gérés, des appareils gérés par Intune et des profils d’entreprise Android gérés par Intune (anciennement Android for Work).
- **Appareils iOS** : vous pouvez cibler des appareils non gérés (MAM uniquement) ou des appareils gérés par Intune.

    > [!NOTE]
    > - La prise en charge de cette fonctionnalité par iOS est déployée tout au long du mois d’avril 2018.

Pour plus d’informations, consultez [Cibler des stratégies de protection des applications en fonction de l’état de gestion des appareils](app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Améliorations du langage utilisé dans l’application Portail d’entreprise pour Windows <!-- 1683758 -->
Nous avons amélioré le langage utilisé dans le Portail d’entreprise pour Windows 10 pour qu’il soit plus convivial et plus spécifique à votre entreprise. Pour voir nos exemples d’images, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nouveaux ajouts à notre documentation sur la confidentialité des utilisateurs <!-- 1440709 -->
Dans le cadre de nos efforts pour donner aux utilisateurs finaux un plus grand contrôle sur la confidentialité de leurs données, nous avons publié des mises à jour de notre documentation expliquant comment afficher et supprimer les données stockées localement par les applications du Portail d’entreprise. Vous pouvez trouver ces mises à jour aux emplacements suivants :

- **Android** : [Guide pratique pour supprimer un appareil Android d’Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, si l’utilisateur a refusé les conditions d’utilisation** : [Guide pratique pour supprimer la gestion de votre appareil si vous avez refusé les « Conditions d’utilisation »](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS** : [Guide pratique pour supprimer votre appareil iOS d’Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows** : [Guide pratique pour supprimer votre appareil Windows d’Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Semaine du 19 mars 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exporter tous les appareils vers des fichiers CSV dans Internet Explorer, Edge ou Chrome <!-- 2258071 -->
Dans **Appareils** > **Tous les appareils**, vous pouvez **Exporter** les appareils vers une liste au format CSV. Les utilisateurs Internet Explorer ayant plus de 10 000 appareils peuvent exporter leurs appareils correctement dans plusieurs fichiers. Chaque fichier contient jusqu’à 10 000 appareils.

Les utilisateurs Edge et Chrome ayant plus de 30 000 appareils peuvent exporter leurs appareils correctement dans plusieurs fichiers. Chaque fichier contient jusqu’à 30 000 appareils.

La rubrique [Gérer des appareils](device-management.md) fournit plus de détails sur ce que vous pouvez faire avec les appareils que vous gérez.

## <a name="week-of-march-12-2018"></a>Semaine du 12 mars 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Les sites web Azure Active Directory peuvent nécessiter l’application Intune Managed Browser et la prise en charge de l’authentification unique pour Managed Browser (préversion publique) <!-- 710595 -->

Avec Azure AD (Azure Active Directory), vous pouvez désormais restreindre l’accès aux sites web pour l’application Intune Managed Browser sur les appareils mobiles. Dans Managed Browser, les données de site web restent sécurisées et séparées des données personnelles de l’utilisateur final. Par ailleurs, Managed Browser prend en charge les fonctionnalités d’authentification unique pour les sites protégés par Azure AD. Si vous vous connectez à Managed Browser ou que vous utilisez Managed Browser sur un appareil avec une autre application gérée par Intune, Managed Browser peut accéder aux sites d’entreprise protégés par Azure AD sans que l’utilisateur ne doive entrer ses informations d’identification. Cette fonctionnalité s’applique aux sites comme Outlook Web Access (OWA) et SharePoint Online, ainsi qu’à d’autres sites d’entreprise tels que les ressources intranet accessibles par le proxy de l’application Azure. Pour plus d’informations, consultez [Contrôles d’accès dans l’accès conditionnel d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Mises à jour visuelles de l’application Portail d’entreprise pour Android <!--976944 -->

Nous avons mis à jour l’application Portail d’entreprise pour Android afin de suivre les recommandations de [Material Design](https://material.io/). Vous pouvez voir les images des nouvelles icônes dans l’article [Nouveautés de l’interface utilisateur d’application](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nouveaux paramètres Windows Defender Exploit Guard <!-- 1631893 -->

Six nouveaux paramètres de <strong>réduction de la surface d’attaque</strong> et fonctionnalités étendues <strong>d’accès contrôlé aux dossiers : Protection des dossiers</strong> sont maintenant disponibles. Ces paramètres se trouvent dans : Configuration de l’appareil\Profils\
Créez profil\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque

|Nom du paramètre  |Options du paramètre  |Description  |
|---------|---------|---------|
|Protection avancée contre les ransomware|Activé, Auditer, Non configuré|Utiliser une protection agressive contre les ransomware.|
|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows|Activé, Auditer, Non configuré|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe).|
|Création de processus à partir des commandes PSExec et WMI|Bloquer, Auditer, Non configuré|Bloquer les créations de processus issues des commandes PSExec et WMI.|
|Processus non approuvés et non signés exécutés à partir d’USB|Bloquer, Auditer, Non configuré|Bloquer les processus non approuvés et non signés exécutés à partir d’USB.|
|Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée|Bloquer, Auditer, Non configuré|Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à des critères de prédominance, d’âge ou de liste approuvée.|

#### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

|              Nom du paramètre               |                                                              Options du paramètre                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protection des dossiers (déjà implémenté) | Non configuré, Activer, Auditer uniquement (déjà implémentées)<br><br> <strong>Nouveau</strong><br>Bloquer la modification du disque, Auditer la modification du disque |             |

Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.<br><br>**Activer** : Empêcher les applications non approuvées de modifier ou supprimer des fichiers dans des dossiers protégés et d’écrire dans des secteurs de disque.<br><br>
**Bloquer la modification du disque uniquement** :<br>Empêcher les applications non approuvées d’écrire dans des secteurs de disque. Les applications non approuvées peuvent toujours modifier ou supprimer des fichiers dans des dossiers protégés.

## <a name="week-of-february-19-2018"></a>Semaine du 19 février 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Prise en charge d’Intune pour plusieurs comptes DEP / Apple School Manager <!-- 747685 -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du [Programme d’inscription des appareils (DEP)](device-enrollment-program-enroll-ios.md) ou [Apple School Manager](apple-school-manager-set-up-ios.md). Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Afficher les restrictions d’inscription par utilisateur <!-- 1634444 eeready wnready -->
Le panneau **Résoudre les problèmes** vous permet désormais de voir les [restrictions d’inscription](enrollment-restrictions-set.md) en vigueur pour chaque utilisateur. Pour cela, sélectionnez **Restrictions d’inscription** dans la liste **Affectations**.

### <a name="device-management"></a>Gestion des appareils
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Rapports sur l’état des menaces et l’état d’intégrité de Windows Defender<!--854704 -->

Il est essentiel de comprendre l’état et l’intégrité de Windows Defender pour gérer des PC Windows.  Avec cette mise à jour, Intune ajoute de nouveaux rapports et de nouvelles actions à l’état et à l’intégrité de l’agent Windows Defender. Grâce à un rapport de cumul d’état dans la [charge de travail Conformité de l’appareil](compliance-policy-monitor.md), vous pouvez voir les appareils qui nécessitent les actions suivantes :
- mise à jour des signatures
- Redémarrer
- intervention manuelle
- analyse complète
- autres états de l’agent nécessitant une intervention

Un rapport détaillé pour chaque catégorie d’état liste les PC individuels nécessitant une attention particulière, ou ceux qui sont signalés comme **sans problème**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nouveaux paramètres de confidentialité pour les restrictions de l’appareil <!--1308926 -->
[Deux nouveaux paramètres de confidentialité](device-restrictions-windows-10.md#privacy) sont désormais disponibles pour les appareils :
- **Publier les activités de l’utilisateur** : affectez la valeur **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches.
- **Activités locales uniquement** : affectez la valeur **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches en fonction uniquement de l’activité locale.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nouveaux paramètres pour le navigateur Microsoft Edge <!--1469166 -->
[Deux nouveaux paramètres](device-restrictions-windows-10.md#edge-browser) sont désormais disponibles pour les appareils avec le navigateur Microsoft Edge : **Chemin vers le fichier de favoris** et **Modifications des favoris**.

### <a name="app-management"></a>Gestion d'applications
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Exceptions de protocoles pour les applications<!--1035509 -->

Vous pouvez à présent créer des exceptions à la stratégie de transfert de données de gestion des applications mobiles (MAM) Intune pour ouvrir des applications non gérées spécifiques. De telles applications doivent être approuvées par le service informatique. Hormis les exceptions que vous créez, le transfert de données est toujours limité aux applications qui sont gérées par Intune quand votre stratégie de transfert de données est définie pour les **applications gérées uniquement**. Vous pouvez créer les restrictions à l’aide de protocoles (iOS) ou de packages (Android).

Par exemple, vous pouvez ajouter le package Webex en tant qu’exception à la stratégie de transfert de données MAM. Cela permet d’ouvrir les liens Webex dans un e-mail Outlook géré directement dans l’application Webex. Le transfert de données sera toujours limité dans d’autres applications non gérées. Pour plus d’informations, consultez [Exceptions de la stratégie de transfert de données pour les applications](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Données chiffrées Windows Information Protection (WIP) dans les résultats de la recherche Windows <!-- 1469193 -->
La stratégie Protection des informations Windows comprend désormais un paramètre vous permettant d’inclure ou non les données chiffrées par cette stratégie dans les résultats de la recherche Windows. Pour définir cette option de stratégie de protection d’application, sélectionnez **Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés** dans les **Paramètres avancés** de la stratégie Protection des informations Windows. La stratégie de protection d’application doit être définie pour la plateforme *Windows 10* et **l’état de l’inscription** de la stratégie d’application doit indiquer **Avec inscription**. Pour plus d’informations, consultez [Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configuration d’une application MSI mobile avec mise à jour automatique <!-- 1740840 -->
Vous pouvez configurer une application MSI mobile connue avec mise à jour automatique pour ignorer le processus de vérification de version. Cette fonctionnalité est utile pour éviter d’introduire une condition de concurrence. Une condition de concurrence peut notamment se produire quand l’application est mise à jour automatiquement par le développeur de l’application et aussi par Intune. Les deux peuvent essayer d’appliquer une version de l’application sur un client Windows, générant ainsi un conflit. Pour ces applications MSI mises à jour automatiquement, vous pouvez configurer le paramètre **Ignorer la version de l’application** dans le panneau **Informations sur l’application**. Quand vous basculez ce paramètre sur **Oui**, Microsoft Intune ignore la version de l’application installée sur le client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Jeux liés de licences d’application pris en charge dans Intune <!-- 1864117 -->
Dans le portail Azure, Intune prend désormais en charge les jeux liés de licences d’application comme élément d’application unique dans l’interface utilisateur. En outre, toutes les applications sous licence en mode hors connexion synchronisées à partir de Microsoft Store pour Entreprises seront consolidées dans une entrée d’application unique et les détails du déploiement des packages individuels seront migrés sur l’entrée unique. Pour voir les ensembles de licences d’application associés dans le portail Azure, sélectionnez **Licences d’application** dans le panneau **Applications clientes**.

### <a name="device-configuration"></a>Configuration des appareils
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Extensions de fichier Protection des informations de Windows pour le chiffrement automatique <!-- 1463582 -->
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
|Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée|Bloquer, Auditer, Non configuré|Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à des critères de prédominance, d’âge ou de liste approuvée.|

##### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

|              Nom du paramètre               |                                                              Options du paramètre                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protection des dossiers (déjà implémenté) | Non configuré, Activer, Auditer uniquement (déjà implémentées)<br><br> <strong>Nouveau</strong><br>Bloquer la modification du disque, Auditer la modification du disque |             |

Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.<br><br>**Activer** : Empêcher les applications non approuvées de modifier ou supprimer des fichiers dans des dossiers protégés et d’écrire dans des secteurs de disque.<br><br>
**Bloquer la modification du disque uniquement** :<br>Empêcher les applications non approuvées d’écrire dans des secteurs de disque. Les applications non approuvées peuvent toujours modifier ou supprimer des fichiers dans des dossiers protégés.

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Ajouts aux paramètres de sécurité du système pour les stratégies de conformité Windows 10 et versions ultérieures <!--1704133-->

Des ajouts apportés aux paramètres de conformité Windows 10 sont désormais disponibles, comme l’obligation d’utiliser le pare-feu et l’antivirus Windows Defender.


### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle
### <a name="intune-apps"></a>Applications Intune
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises <!--1222672-->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications hors connexion sont installées par Intune et non pas par le Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Empêcher des utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel <!-- 1728700 -->

Quand vous déployez l’application Gmail dans un profil Android for Work, vous pouvez désormais empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel à l’aide du paramètre **Ajouter et supprimer des comptes** du profil de restrictions d’appareil Android for Work.

## <a name="week-of-february-5-2018"></a>Semaine du 5 février 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nouvelle option pour l’authentification utilisateur dans le cadre de l’inscription en bloc Apple <!-- 747625 eeready -->

> [!NOTE]
> Les nouveaux locataires la verront tout de suite. Pour les locataires existants, cette fonctionnalité sera déployée en avril. Tant que ce déploiement ne sera pas terminé, vous n’aurez peut-être pas accès à ces nouvelles fonctionnalités.

Intune vous donne maintenant la possibilité d’authentifier les appareils à l’aide de l’application Portail d’entreprise pour les méthodes d’inscription suivantes :

- Programme d'inscription d'appareils Apple
- Apple School Manager
- Inscription à Apple Configurator

Lorsque vous utilisez l’option Portail d’entreprise, l’authentification multifacteur Azure Active Directory peut être appliquée sans bloquer ces méthodes d’inscription.

Lorsque vous utilisez l’option Portail d’entreprise, Intune ignore l’authentification utilisateur dans l’Assistant Réglages iOS pour l’inscription d’affinité utilisateur. Cela signifie que l’appareil est initialement inscrit comme appareil sans utilisateur et, par conséquent, vous ne recevez pas les configurations ou stratégies des groupes d’utilisateurs. Il reçoit uniquement les configurations et les stratégies des groupes d’appareils. Toutefois, Intune installera automatiquement l’application Portail d’entreprise sur l’appareil. Le premier utilisateur à lancer l’application Portail d’entreprise et à s’y connecter sera associé à l’appareil dans Intune. À ce stade, l’utilisateur reçoit les configurations et les stratégies de ses groupes d’utilisateurs. L’association de l’utilisateur ne peut pas être modifiée sans réinscription.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Prise en charge d’Intune pour plusieurs comptes DEP / Apple School Manager <!-- 747685 eeready -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du Programme d’inscription des appareils (DEP) ou Apple School Manager. Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impression à distance sur un réseau sécurisé <!-- 1709994  -->
Les solutions d’impression mobiles sans fil PrinterOn permettront aux utilisateurs d’imprimer à distance depuis n’importe où et à tout moment via un réseau sécurisé. PrinterOn s’intégrera au Kit SDK APP d’Intune à la fois pour iOS et Android. Vous pourrez cibler les stratégies de protection d’application pour cette application via le panneau des **stratégies de protection d’application** d’Intune, dans la console d’administration. Les utilisateurs finaux pourront télécharger l’application « PrinterOn for Microsoft » via le Google Play Store ou iTunes afin de l’utiliser dans leur écosystème Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Prise en charge du portail d’entreprise macOS pour les inscriptions qui utilisent le gestionnaire d’inscription d’appareil <!-- 1352411 -->

Les utilisateurs peuvent désormais utiliser le Gestionnaire d’inscription d’appareil durant l’inscription auprès du portail d’entreprise macOS.

## <a name="week-of-january-29-2018"></a>Semaine du 29 janvier 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertes pour les jetons expirés et les jetons qui arrivent à expiration <!-- 1639263 -->
La page de vue d’ensemble affiche maintenant des alertes pour les jetons expirés et ceux qui arrivent à expiration. Lorsque vous cliquez sur une alerte pour un jeton unique, vous accéderez à la page des détails de ce jeton.  Si vous cliquez sur une alerte comportant plusieurs jetons, vous accéderez à une liste de tous les jetons avec leur état. Les administrateurs doivent renouveler leurs jetons avant la date d’expiration.

### <a name="device-management"></a>Gestion des appareils

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Prise en charge de la commande d’effacement à distance pour les appareils macOS <!-- 1438084 -->

Les administrateurs peuvent exécuter une commande d’effacement à distance pour les appareils macOS.

> [!IMPORTANT]
> La commande d’effacement ne peut pas être annulée et doit être utilisée avec précaution.

La commande d’effacement supprime toutes les données, y compris le système d’exploitation, d’un appareil. Elle entraîne aussi la suppression de l'appareil de la gestion Intune. Aucun avertissement n’est envoyé à l’utilisateur, et l’effacement se produit dès l’envoi de la commande.

Vous pouvez configurer un code PIN de récupération à 6 chiffres. Ce code PIN peut servir à déverrouiller l’appareil effacé avant de lancer la réinstallation du système d’exploitation. Une fois que l’effacement a démarré, le code PIN apparaît dans une barre d’état sur le panneau de présentation de l’appareil dans Intune. Le code PIN restera affiché tant que l’effacement est en cours. Une fois l’effacement terminé, l’appareil disparaît totalement de la gestion Intune. Veillez à enregistrer le code PIN de récupération afin que toute personne qui restaure l’appareil puisse l’utiliser.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Révoquer des licences pour un jeton Programme d’achat en volume iOS <!-- 820870 -->
Vous pouvez révoquer la licence de toutes les applications de Programme d’achat en volume (VPP) iOS pour un jeton VPP donné.

### <a name="app-management"></a>Gestion d'applications

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Révocation des applications du Programme d’achat en volume iOS  <!-- 820863 -->
Pour un appareil donné qui a une ou plusieurs applications de Programme d’achat en volume (VPP) iOS, vous pouvez révoquer pour l’appareil la licence d’application associée basée sur l’appareil. La révocation d’une licence d’application ne désinstalle pas l’application VPP de l’appareil. Pour désinstaller une application VPP, vous devez remplacer l’action d’attribution par **Désinstaller**. Pour plus d’informations, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Affecter des applications mobiles Office 365 aux appareils iOS et Android à l’aide du type d’application intégré <!-- 1332318 -->
Le type d’application **Intégré** facilite la création d’applications Office 365 et leur affectation aux appareils iOS et Android gérés. Ces applications incluent les applications Office 365 telles que Word, Excel, PowerPoint et OneDrive. Vous pouvez affecter des applications spécifiques au type d’application et modifier la configuration des informations des applications.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusion et exclusion d’affectations d’applications en fonction de groupes <!-- 1406920 -->

Pendant l’affectation d’une application et après avoir sélectionné un type d’affectation, vous pouvez sélectionner les groupes à inclure et ceux à exclure.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Vous pouvez attribuer une stratégie de configuration d’application à des groupes en incluant et excluant des affectations  <!-- 1480316 -->

Vous pouvez attribuer une stratégie de configuration d’application à un groupe d’utilisateurs et d’appareils à l’aide d’une combinaison d’affectations d’inclusion et d’exclusion. Les affectations peuvent être choisies sous la forme d’une sélection personnalisée de groupes ou d’un groupe virtuel. Un groupe virtuel peut être notamment **Tous les utilisateurs**, **Tous les appareils** ou **Tous les utilisateurs + Tous les appareils**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Prise en charge de la stratégie de mise à niveau de l’édition Windows 10   <!-- 903672(archived), 1119689 -->  
Vous pouvez créer une stratégie de mise à niveau d’édition Windows 10 qui met à niveau les appareils Windows 10 vers Windows 10 Éducation, Windows 10 Éducation N, Windows 10 Professionnel, Windows 10 Professionnel N, Windows 10 Professionnel Éducation et Windows 10 Professionnel Éducation N. Pour plus d’informations sur les mises à niveau d’édition Windows 10, consultez [Guide pratique pour configurer les mises à niveau d’édition Windows 10 ](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Les stratégies d’accès conditionnel pour Intune sont disponibles uniquement à partir du portail Azure <!-- 1737088 1634311 -->

À partir de cette version, vous pouvez configurer et gérer vos stratégies d’accès conditionnel dans le [portail Azure](https://portal.azure.com) en accédant à **Azure Active Directory** > **Accès conditionnel**. Pour des raisons pratiques, vous pouvez également accéder à ce panneau à partir d’Intune dans le portail Azure, depuis **Intune** > **Accès conditionnel**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Mises à jour des e-mails de conformité <!--1637547 -->

Quand un e-mail est envoyé pour signaler un appareil non conforme, des informations sur cet appareil non conforme sont ajoutées.


## <a name="week-of-january-22-2018"></a>Semaine du 22 janvier 2018

### <a name="intune-apps"></a>Applications Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nouvelles fonctionnalités de l’action « Résoudre » pour les appareils Android <!--1583480-->

L’application Portail d’entreprise pour Android étend l’action « Résoudre » sur **Mettre à jour les paramètres d’appareil** afin de résoudre les [problèmes de chiffrement d’appareil](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Verrouillage à distance disponible dans l’application Portail d’entreprise pour Windows 10 <!--676506-->
Les utilisateurs finaux peuvent désormais verrouiller à distance leurs appareils à partir de l’application Portail d’entreprise pour Windows 10. Cela ne s’affichera pas pour l’appareil local qu’ils utilisent de manière active.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Résolution plus rapide des problèmes de conformité affectant l’application Portail d’entreprise pour Windows 10 <!--676546-->
Les utilisateurs finaux d’appareils Windows peuvent choisir la raison de la non-conformité dans l’application Portail d’entreprise. Quand c’est possible, ils sont directement positionnés à l’emplacement approprié dans l’application Paramètres pour corriger le problème.

## <a name="week-of-december-11-2017"></a>Semaine du 11 décembre 2017

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nouveau paramètre de redéploiement automatique <!-- 1469168 -->
Le paramètre **Redéploiement automatique** permet aux utilisateurs avec des droits d’administration de supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **Ctrl+Win+R** sur l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion. Ce paramètre se trouve sous Windows 10 -> Restrictions sur l’appareil -> Général -> Redéploiement automatique. Pour plus d’informations, consultez [Paramètres de restriction d’appareil Intune pour Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Prise en charge d’éditions source supplémentaires dans la stratégie de mise à niveau de l’édition Windows 10 <!-- 903672,  1119689 -->
Vous pouvez maintenant utiliser la stratégie de mise à niveau de l’édition Windows 10 pour effectuer une mise à niveau à partir d’autres éditions de Windows 10 (Windows 10 Professionnel, Windows10 Professionnel Éducation, Windows 10 Cloud, etc.). Avant cette version, les chemins de mise à niveau de l’édition pris en charge étaient plus limités. Pour plus d’informations, consultez le [Guide pratique de configuration des mises à niveau Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nouveaux paramètres pour le profil de configuration d’appareil Windows Defender Security Center (WDSC) <!-- 1335507 -->

Intune ajoute une nouvelle section de paramètres pour le profil de configuration d’appareil, sous la Protection du point de terminaison, nommée **Windows Defender Security Center**. Les administrateurs informatiques peuvent configurer les éléments de base auxquels les utilisateurs finaux de l’application Windows Defender Security Center peuvent accéder. Si un administrateur informatique masque un élément de base dans l’application Windows Defender Security Center, les notifications liées à l’élément de base masqué ne s’affichent pas sur l’appareil de l’utilisateur.

Vous trouverez ci-dessous les éléments de base que les administrateurs peuvent masquer dans les paramètres du profil de configuration d’appareil Windows Defender Security Center :
- Protection contre les menaces et les virus
- Performances et intégrité de l’appareil
- Protections du pare-feu et du réseau
- Contrôle d’application et du navigateur
- Options Famille

Les administrateurs informatiques peuvent également personnaliser les notifications que les utilisateurs reçoivent. Par exemple, vous pouvez décider si les utilisateurs reçoivent toutes les notifications générées par les éléments de base visibles dans WDSC ou uniquement les notifications critiques. Les notifications non critiques incluent des résumés périodiques sur l’activité de l’antivirus Windows Defender et des notifications indiquant lorsque des analyses sont terminées. Toutes les autres notifications sont considérées comme critiques. En outre, vous pouvez aussi personnaliser le contenu même de la notification. Par exemple, vous pouvez fournir les coordonnées du service informatique à inclure dans les notifications qui s’affichent sur les appareils des utilisateurs.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Prise en charge de connecteurs multiples pour le traitement des certificats SCEP et PFX <!-- 1361755 -->

Les clients qui utilisent le connecteur NDES local pour fournir des certificats à des appareils peuvent désormais configurer plusieurs connecteurs dans un seul locataire.

Cette nouvelle fonctionnalité prend en charge le scénario suivant :

- **Haute disponibilité**

Chaque connecteur NDES extraie des demandes de certificat d’Intune.  Si un connecteur NDES a l’état hors connexion, l’autre connecteur peut continuer à traiter les requêtes.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Le nom d’objet du client peut utiliser la variable AAD_DEVICE_ID <!-- 1468599 -->

Lorsque vous créez un profil de certificat SCEP dans Intune, vous pouvez désormais utiliser la variable AAD_DEVICE_ID lorsque vous générez le nom d’objet du client.   Lorsque le certificat est demandé à l’aide de ce profil SCEP, la variable est remplacée par l’ID AAD de l’appareil qui effectue la demande de certificat.


### <a name="device-management"></a>Gestion des appareils

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gérer les appareils macOS inscrits auprès de Jamf avec le moteur de conformité des appareils d’Intune<!-- 1592747 -->
Vous pouvez utiliser Jamf pour envoyer des informations sur l’état des appareils macOS à Intune, qui évaluera alors la conformité avec les stratégies définies dans la console Intune. En fonction de cet état et d’autres conditions (notamment, l’emplacement, les risques de l’utilisateur, etc.), l’accès conditionnel appliquera des stratégies de conformité aux appareils macOS qui accèdent aux applications cloud et locales reliées à Azure AD, y compris Office 365. En savoir plus sur la [configuration de l’intégration de Jamf](conditional-access-integrate-jamf.md) et la [mise en application de la conformité des appareils Jamf gérés](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nouvelle action sur appareil iOS   <!-- 1424701 -->

Vous pouvez maintenant arrêter les appareils supervisés iOS 10.3. Cette action arrête immédiatement l’appareil sans avertir l’utilisateur final. L’action **Arrêter (supervisé uniquement)** se trouve dans les propriétés de l’appareil lorsque vous sélectionnez un appareil dans la charge de travail **Appareil**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Interdire les changements de date/heure sur les appareils Samsung Knox <!-- 1468103 -->

Nous avons ajouté une nouvelle fonctionnalité qui vous permet d’empêcher les changements de date et d’heure sur les appareils Samsung Knox. Vous la trouverez dans **Profils de configuration d’appareil** > **Restrictions d’appareil (Android)** > **Général**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Compte de ressource Surface Hub pris en charge <!-- 1566442  -->

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

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installer des applications Office sur des appareils macOS <!-- 1494311 -->
Vous pourrez maintenant installer des applications Office sur des appareils macOS. Ce nouveau type d’application vous permettra d’installer Word, Excel, PowerPoint, Outlook et OneNote. Ces applications bénéficient également de Microsoft AutoUpdate (MAU) qui garantit que vos applications sont sécurisées et à jour.

### <a name="app-management"></a>Gestion d'applications

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Supprimer un jeton Programme d’achat en volume iOS <!-- 820879 -->
Vous pouvez supprimer le jeton Programme d’achat en volume (VPP) iOS à l’aide de la console. Ceci peut être nécessaire si vous avez des instances dupliquées d’un jeton VPP.

### <a name="intune-apps"></a>Applications Intune


### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Nouvelle collection d’entités, nommée Utilisateur actuel, limitée aux données des utilisateurs actuellement actifs<!-- 1667026 -->

La collecte d’entités **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

En revanche, la nouvelle collection d’entités **Utilisateur actuel** contient uniquement les utilisateurs qui n’ont pas été supprimés. La collection d'entités **Utilisateur actuel** ne contient que des utilisateurs actuellement actifs. Pour plus d’informations sur la collection d’entités **Utilisateur actuel**, consultez la page [Informations de référence sur l’entité Utilisateur actuel](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>API Graph mises à jour <!-- 1736360 -->

Dans cette version, nous avons mis à jour quelques-unes des API Graph pour Intune (actuellement en version bêta). Consultez le [journal mensuel des modifications de l’API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) pour plus d’informations.

## <a name="week-of-december-4-2017"></a>Semaine du 4 décembre 2017

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune prend en charge les applications refusées dans Protection des informations Windows <!-- 1479103 -->
Vous pouvez spécifier les applications refusées dans Intune. Si une application est refusée, son accès aux informations d’entreprise est bloqué (ce qui correspond à l’inverse de la liste des applications autorisées). Pour plus d’informations, consultez [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Liste d’exclusion recommandée pour la Protection des informations Windows).



## <a name="notices"></a>Remarques

### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Prenez des mesures : mettez à jour les paramètres de mot de passe de stratégie de conformité ou de restriction de votre appareil Android dans Intune
Intune va supprimer le type de mot de passe disponible « Paramètres par défaut de l’appareil » pour les appareils Android 4.4 et ultérieurs. En raison des différences qui existent entre les plateformes Android et les paramètres par défaut des appareils, cette stratégie est souvent considérée comme facultative par l’appareil. Pour dissiper toute confusion quant au moment où ce paramètre est appliqué sur Android, nous allons le supprimer de l’interface utilisateur dans une prochaine version. 
#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
- Si vous avez l’intention d’exiger un mot de passe sur les appareils, nous vous recommandons de modifier vos profils de plateforme Android pour préciser clairement le type de mot de passe exigé plutôt que d’utiliser le « paramètre par défaut de l’appareil ».
- Si vous avez l’intention de laisser votre utilisateur final choisir s’il faut créer un mot de passe, sélectionnez le bouton « Non configuré ». Quand nous supprimerons ce paramètre de l’interface utilisateur, si le paramètre est toujours défini, vous devrez choisir une valeur autre que « Paramètre par défaut de l’appareil » la prochaine fois que vous modifierez le profil.
Que dois-je faire pour me préparer à cette modification ?
Vérifiez les paramètres de mot de passe dans vos stratégies de conformité et de restriction d’appareil Android et Android Entreprise. Ils sont listés sous Sécurité système pour les stratégies de conformité, et sous Mot de passe de l’appareil ou sous Paramètres du profil professionnel pour les restrictions d’appareil. Les informations supplémentaires proposent un lien vers plus de détails et des captures d’écran indiquant où ces paramètres sont configurés.
####<a name="additional-information"></a>Informations supplémentaires
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>Modification prévue : changement du mot de passe à la prochaine authentification ajouté dans Intune<!-- 1873216 -->
Dans la version de septembre du service, Intune envisage d’intégrer le paramètre Apple de **changement de mot de passe à la prochaine authentification** récemment publié pour les appareils exécutant les versions macOS 10.13 et ultérieures. Avant ce paramètre, les fournisseurs MDM ne pouvaient pas vérifier que le code secret de l’appareil avait été changé pour être conforme. Les stratégies de configuration et de conformité d’Intune vérifient uniquement que le mot de passe d’un appareil est marqué comme conforme la prochaine fois qu’il est changé. Lors de l’ajout de cette nouvelle fonctionnalité Apple, vos utilisateurs macOS reçoivent une demande de mise à jour de leur mot de passe, même si celui-ci est conforme.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Cela a un impact sur les environnements avec une stratégie d’appareil macOS utilisant Intune ou une gestion MDM hybride. Maintenant qu’Apple dispose de ce paramètre de **changement de mot de passe à la prochaine authentification**, Intune peut forcer les utilisateurs à mettre à jour leur mot de passe quand une stratégie de mot de passe est envoyée. Si vous bloquez les ressources de l’entreprise tant que l’appareil n’est pas marqué conforme, vos utilisateurs finaux peuvent se voir refuser l’accès aux ressources de l’entreprise, telles que la messagerie ou les sites SharePoint, tant qu’ils ne réinitialisent pas leur mot de passe. À l’avenir, toutes les mises à jour des stratégies de configuration et de conformité des mots de passe vont forcer les utilisateurs ciblés à mettre à jour leurs mots de passe.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Prévenez votre support technique. Si vous ne souhaitez pas appliquer cette stratégie d’appareil macOS, nous vous recommandons d’annuler l’attribution ou de supprimer votre stratégie macOS existante. Une recherche parmi les clients suppose que la plupart d’entre eux ne sont pas affectés par cette modification. La plupart des utilisateurs finaux mettent à jour leur mot de passe après avoir reçu une demande d’inscription avec un mot de passe ou de réinitialisation de leur mot de passe pour rester conformes.


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>Changement planifié : Intune est appelé à prendre en charge iOS versions 10 et ultérieures en septembre <!-- 2454656 -->
En septembre, Apple est censé publier iOS 12. Peu après la publication, nous ferons en sorte que l’inscription à Intune, le Portail d’entreprise et le navigateur géré prennent en charge iOS versions 10 et ultérieures.  

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?  
Les applications mobiles Office 365 étant prises en charge sur iOS versions 10 et ultérieures, vous avez peut-être déjà mis à niveau votre système d’exploitation ou vos appareils. Si tel est le cas, ce changement ne vous concerne pas.  

Toutefois, si vous avez l’un des appareils répertoriés ci-dessous ou que vous voulez inscrire un de ces appareils, soyez conscient qu’il ne prend en charge qu’iOS versions 9 et antérieures.  Pour continuer à accéder au Portail d’entreprise Intune, vous devez mettre à niveau ces appareils d’ici septembre, pour qu’ils prennent en charge iOS versions 10 ou ultérieures :  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (3ème génération)  
* iPad mini (1ère génération)  

À compter de juillet, les appareils inscrits à MDM utilisant iOS 9 et le Portail d’entreprise recevront une invite de mise à niveau du système d’exploitation ou de l’appareil. Si vous utilisez des stratégies de protection des applications, vous pouvez également définir le paramètre d’accès « Exiger une version minimale du système d’exploitation iOS (avertissement seulement) ».  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?   
Recherchez les appareils ou utilisateurs qui sont concernés dans votre organisation. Dans Intune dans le portail Azure, accédez à Appareils > Tous les appareils et filtrez par système d’exploitation.  Cliquez sur Colonnes pour voir les détails tels que la version du système d’exploitation. Demandez aux utilisateurs de mettre à niveau leurs appareils avant septembre, avec une version de système d’exploitation prise en charge.  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Changement planifié : Déplacement d’Intune vers TLS 1.2
À compter du 31 octobre 2018, Intune prendra en charge le protocole TLS (Transport Layer Security) version 1.2 pour fournir le meilleur chiffrement, afin de garantir que notre service est plus sécurisé par défaut et de s’aligner avec d’autres services Microsoft tels que Microsoft Office 365. Office a communiqué ce changement dans MC128929.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
À compter du 31 octobre 2018, Intune ne prendra plus en charge les versions 1.0 ou 1.1 du protocole TLS. Toutes les combinaisons client-serveur et navigateur-serveur doivent utiliser TLS version 1.2 afin de garantir une connexion sans problèmes à Intune. Notez que ce changement aura un impact sur les appareils des utilisateurs finaux qui ne sont plus pris en charge par Intune, mais qui reçoivent toujours la stratégie par le biais d’Intune et qui ne peut pas utiliser le protocole TLS version 1.2. Il s’agit d’appareils comme ceux exécutant Android 4.3 et des versions antérieures. Pour obtenir la liste des appareils et navigateurs concernés, consultez la section Informations supplémentaires ci-dessous.

Après le 31 octobre 2018, si vous rencontrez un problème lié à l’utilisation d’une ancienne version de TLS, vous devrez effectuer une mise à jour vers TLS 1.2 ou vers un appareil qui prend en charge TLS 1.2 dans le cadre du processus de résolution.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Nous vous recommandons de supprimer de façon proactive les dépendances TLS 1.0 et 1.1 dans vos environnements, et de désactiver, dans la mesure du possible, TLS 1.0 et 1.1 au niveau du système d’exploitation. Commencez à planifier votre migration vers TLS 1.2 dès aujourd’hui. Consultez le billet de blog de support ci-dessous pour obtenir la liste des appareils qui ne sont pas pris en charge par Intune aujourd’hui, mais qui peuvent encore recevoir la stratégie et qui ne pourront pas communiquer à l’aide du protocole TLS version 1.2. Vous devrez informer ces utilisateurs qu’ils perdront l’accès aux ressources d’entreprise.

**Informations supplémentaires** : [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)


### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Modification prévue : modification de la prise en charge du plug-in Cordova dans le SDK de l’application Microsoft Intune
Intune met fin au support du [plug-in Cordova du SDK de l’application Microsoft Intune](app-sdk-cordova.md) le 1er mai 2018. Nous vous recommandons d’utiliser l’outil de création de package de restrictions d’application Intune à la place, pour préparer vos applications basées sur Cordova afin qu’elles soient gérables et disponibles dans Intune. À la prise d’effet de ce changement, le SDK de l’application Microsoft Intune pour le plug-in Cordova ne sera plus tenu à jour et ne recevra pas de mises à jour. Les développeurs d’applications ne pourront pas utiliser ce plug-in. Intune prévoit de continuer la prise en charge des applications créées avec Cordova. Toutefois, toutes les applications créées avec le SDK de l’application Microsoft Intune pour le plug-in Cordova auront des fonctionnalités réduites dans Intune. Une fois traitées avec l’outil de création de package de restrictions d’application Intune, les applications peuvent être déployées pour les utilisateurs finaux de façon habituelle. Pour les applications Android basées sur Cordova publiées dans Google Play Store :
- Les utilisateurs finaux sont invités à indiquer leurs informations d’identification pour recevoir la stratégie Intune au premier lancement.
- Les applications doivent être publiées dans l’App Store ciblé pour les utilisateurs Intune, par exemple « Application Contoso pour Intune ».

Pour plus d’informations sur l’outil de création de package de restrictions d’application, consultez [Outil de création de package de restrictions d’application pour iOS](app-wrapper-prepare-ios.md) et [Outil de création de package de restrictions d’application pour Android](app-wrapper-prepare-android.md). Pour tout problème ou toute question, contactez [ msintuneappsdk@microsoft.com ](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Modification planifiée : utiliser Intune sur Azure maintenant pour la gestion des appareils mobiles<!-- 1227338 -->
Il y a plus d’un an, nous avons annoncé une [préversion publique d’Intune sur Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) et avons donné suite six mois auparavant avec la [disponibilité générale de la nouvelle expérience d’administration](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) pour Intune. À partir du 31 août 2018, la gestion des périphériques mobiles (GPM) sera désactivée sur la console Silverlight classique pour les clients qui utilisent Intune autonome. Vous pouvez utiliser à la place [Intune sur Azure](https://aka.ms/Intune_on_Azure) pour vos besoins de gestion des appareils mobiles. Si vous utilisez toujours la console classique pour la gestion des appareils mobiles, arrêtez et familiarisez-vous avec Intune sur Azure. Cette modification ne devrait pas avoir d’impact sur les utilisateurs finaux. La gestion classique des PC restera dans Silverlight. Vous trouverez plus d’informations sur cette modification et la façon dont elle vous affecte [ici](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accès direct aux scénarios d’inscription d’Apple <!--951869-->
Pour les comptes Intune créés après janvier 2017, Intune a activé un accès direct aux scénarios d’inscription Apple à l’aide de la charge de travail Inscrire des appareils dans le portail Azure. Auparavant, la version préliminaire de l’inscription Apple était uniquement accessible à partir de liens dans le portail classique Intune. Les comptes Intune créés avant janvier 2017 nécessitent une migration unique pour que ces fonctionnalités deviennent disponibles dans Azure. La planification de la migration n’a pas encore été annoncée, mais les détails correspondants seront diffusés dès que possible. Si votre compte existant ne peut pas accéder au portail Azure, nous vous recommandons vivement de créer un compte d’essai afin de tester la nouvelle expérience.

## <a name="whats-coming"></a>Nouveautés à venir

### <a name="local-device-security-option-settings----1251887---"></a>Paramètres d’option de sécurité d’appareil local <!-- 1251887 -->
Vous pourrez activer les paramètres de sécurité sur les appareils Windows 10 à l’aide des nouveaux paramètres présents dans Options de sécurité locales de l’appareil. Recherchez ces paramètres dans la catégorie Endpoint Protection quand vous créez une stratégie de configuration d’appareil Windows 10.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Nouvelle mise à jour de l’expérience utilisateur du site web Portail d’entreprise<!--2000968-->

Nous allons introduire une nouvelle expérience du site web Portail d’entreprise en août, avec des mises à jour de l’interface utilisateur, des workflows simplifiés et des améliorations apportées à l’accessibilité. Cette nouvelle expérience inclut des améliorations demandées par les clients comme le partage d’applications et l’amélioration des performances globales pour plus de convivialité.
Nous avons ajouté de nouvelles fonctionnalités en nous basant sur les commentaires que nous ont envoyés des clients comme vous, afin d’améliorer considérablement les fonctionnalités existantes et leur mode d’utilisation :

* Améliorations de l’interface utilisateur dans l’ensemble du site web
* Possibilité de partager des liens directs vers les applications
* Performances améliorées des grands catalogues d’applications

Vous n’avez rien à faire pour vous préparer à ce changement. Nous vous informerons quand le site web Portail d’entreprise sera mis à jour et à votre disposition. Toutefois, vous devrez éventuellement mettre à jour les documents destinés aux utilisateurs finaux avec des captures d’écran actualisées. Notez que vous devez également mettre à jour la documentation de l’application Portail d’entreprise sur iOS, étant donné que le site web alimente la section **Applications** de l’application iOS. Vous pouvez voir un exemple d’image sur la page [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Mises à jour requises par Apple pour Application Transport Security <!--748318-->
La société Apple a annoncé qu’elle appliquera des exigences spécifiques pour ATS (Application Transport Security). ATS est utilisé pour renforcer la sécurité de toutes les communications d’application via le protocole HTTPS. Cette modification a une incidence sur les clients Intune qui utilisent les applications de portail d’entreprise iOS. Nous donnerons tous les détails nécessaires sur notre [Blog pour le support Intune](https://aka.ms/compportalats).



## <a name="see-also"></a>Voir aussi
* [Blog Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Feuille de route de la plateforme cloud](https://www.microsoft.com/cloud-platform/roadmap)
* [Nouveautés de l’interface utilisateur du portail d’entreprise](whats-new-app-ui.md)
* [Nouveautés des mois précédents](whats-new-archive.md)
