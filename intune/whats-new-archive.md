---
title: Nouveautés des mois précédents dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Passer en revue les annonces antérieures sur la page Nouveautés d’Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/25/2019
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8df4a1d7f929301c11f577a9b7e50ef1647dda11
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423711"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Nouveautés de la préversion de Microsoft Intune - mois précédents

[!INCLUDE [azure_portal](./includes/azure_portal.md)]


<!-- ########################## -->
## <a name="september-2018"></a>Septembre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Supprimer la duplication des vignettes d’état de protection des applications <!-- 3083391 -->
Les vignettes **Statut de l’utilisateur pour iOS** et **Statut de l’utilisateur pour Android** étaient présentes dans les pages **Applications clientes - Vue d’ensemble** et **Applications clientes - État de protection de l’application**. Les vignettes d’état ont été supprimées de la page **Applications clientes - Vue d’ensemble** pour éviter la duplication. 

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Prise en charge de plus d’autorités de certification tierces <!-- 3093107 -->
En utilisant le protocole SCEP (Simple Certificate Enrollment Protocol), vous pouvez maintenant émettre de nouveaux certificats et renouveler des certificats sur les appareils mobiles à l’aide de Windows, iOS, Android et macOS.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Prise en charge d’iOS 10 et versions ultérieures par Intune <!-- 2454656 -->  
L’inscription à Intune, le Portail d’entreprise et Managed Browser prennent désormais uniquement en charge les appareils iOS exécutant iOS 10 et versions ultérieures. Pour vérifier quels sont les appareils ou utilisateurs concernés dans votre organisation, accédez à Intune dans le portail Azure > **Appareils** > **Tous les appareils**. Filtrez par système d’exploitation, puis cliquez sur **Colonnes** pour afficher les détails de la version du système d’exploitation. Demandez à ces utilisateurs de mettre à niveau leurs appareils vers une version de système d’exploitation prise en charge.  

Si vous avez l’un des appareils répertoriés ci-dessous ou que vous voulez inscrire l’un de ces appareils, sachez qu’il ne prend en charge qu’iOS 9 et versions antérieures.  Pour continuer à accéder au Portail d’entreprise Intune, vous devez mettre à niveau ces appareils pour qu’ils prennent en charge iOS 10 ou version ultérieure :  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ème génération) 
* iPad mini (1ère génération)  

### <a name="device-management"></a>Gestion des appareils

#### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Centre d’administration Gestion des périphériques Microsoft 365 <!-- 3078424 -->
L’une des promesses de Microsoft 365 est la simplification de l’administration, et au fil des années nous avons intégré les services Microsoft 365 backend pour fournir des scénarios de bout en bout tels que l’accès conditionnel Intune et Azure AD. Le nouveau [Centre d’administration Microsoft 365](http://devicemanagement.microsoft.com) est l’endroit où consolider, simplifier et intégrer l’expérience d’administration. L’espace de travail spécialisé pour la gestion des appareils offre un accès aisé à toutes les tâches et les informations de gestion des appareils et des applications dont votre organisation a besoin. Nous pensons qu’il deviendra l’espace de travail cloud principal pour les équipes d’utilisateurs finaux d’enterprise.


<!-- ########################## -->
## <a name="august-2018"></a>Août 2018

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

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Le nom de fichier du programme d’installation du Portail d’entreprise macOS inclut désormais le numéro de version <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Mises à jour automatiques des applications iOS <!-- 2729759 -->
Les mises à jour automatiques des applications fonctionnent pour les applications sous licence d’appareil et d’utilisateur pour iOS version 11.0 et ultérieure.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello cible les utilisateurs et les appareils <!-- 1106609 -->
Quand vous créez une stratégie [Windows Hello Entreprise](windows-hello.md), elle s’applique à tous les utilisateurs au sein de l’organisation (au niveau locataire). Avec cette mise à jour, la stratégie peut également être appliquée à des utilisateurs ou des appareils spécifiques à l’aide d’une stratégie de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Identity Protection** > **Windows Hello Entreprise**).
Dans le portail Azure d’Intune, la configuration et les paramètres de Windows Hello existent désormais à la fois dans **Inscription de l’appareil** et dans **Configuration de l’appareil**. **Inscription de l’appareil** cible toute l’organisation (au niveau locataire) et prend en charge Windows AutoPilot (OOBE). **Configuration de l’appareil** cible des appareils et des utilisateurs à l’aide d’une stratégie appliquée lors de l’archivage.
Cette fonctionnalité s’applique à :  
- Windows 10 et versions ultérieures
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler est une connexion disponible pour les profils VPN sur iOS <!-- 1769858 -->
Quand vous créez un profil de configuration d’appareil VPN iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** >  plateforme **iOS** > type de profil **VPN**), il existe plusieurs types de connexions, notamment Cisco, Citrix et bien plus encore. Cette mise à jour ajoute Zscaler comme type de connexion. 
[Paramètres VPN pour les appareils exécutant iOS](vpn-settings-ios.md) liste les types de connexions disponibles.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Mode FIPS pour les profils Wi-Fi d’entreprise pour Windows 10 <!-- 1879077 -->
Vous pouvez désormais activer le mode FIPS (Federal Information Processing Standards) pour les profils Wi-Fi d’entreprise pour Windows 10 dans le portail Azure Intune. Vérifiez que le mode FIPS est activé sur votre infrastructure Wi-Fi si vous l’activez dans vos profils Wi-Fi.
[Paramètres Wi-Fi pour les appareils Windows 10 et ultérieur dans Intune](wi-fi-settings-windows.md) vous montre comment créer un profil Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Contrôle du mode S sur les appareils Windows 10 et versions ultérieures (préversion publique) <!-- 1958649 -->
Avec la mise à jour de cette fonctionnalité, vous pouvez créer un profil de configuration d’appareil qui sort un appareil Windows 10 du mode S ou empêcher les utilisateurs de sortir l’appareil du mode S. Cette fonctionnalité se trouve dans Intune > **Configuration de l’appareil** > **Profils** >  **Windows 10 et ultérieur** > **Mise à niveau d’édition et changement de mode**.
[Présentation de Windows 10 en mode S](https://www.microsoft.com/windows/s-mode) propose d’autres informations sur le mode S.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Ajout automatique du package de configuration de Windows Defender ATP au profil de configuration <!-- 2144658 -->
Lors de l’utilisation [d’ATP (Advanced Threat Protection) et de l’intégration d’appareils](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) dans Intune, vous deviez auparavant télécharger un package de configuration et l’ajouter à votre profil de configuration. Avec cette mise à jour, Intune reçoit automatiquement le package du Centre de sécurité Windows Defender et l’ajoute à votre profil.
S’applique à Windows 10 et versions ultérieures.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Exiger que les utilisateurs se connectent pendant la configuration de l’appareil <!--2311457-->
Vous pouvez maintenant définir des profils d’appareil de façon à exiger que l’appareil se connecte à un réseau avant de continuer au-delà de la page Réseau lors de la configuration de Windows 10. Tant que cette fonctionnalité est en préversion, vous avez besoin de Windows Insider build 1809 ou ultérieure pour utiliser ce paramètre.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Restreindre des applications et bloquer l’accès aux ressources d’entreprise sur les appareils iOS et Android Entreprise <!-- 2451462 -->
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

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Verrouillage du Portail d’entreprise en mode Application unique jusqu’à la connexion de l’utilisateur <!--1067692 --> 
Vous avez désormais la possibilité d’exécuter le portail d’entreprise en mode Application unique si vous authentifiez un utilisateur via le portail d’entreprise au lieu de l’Assistant Configuration lors de l’inscription DEP. Cette option verrouille l’appareil immédiatement après l’exécution de l’Assistant Configuration afin qu’un utilisateur soit obligé de se connecter pour accéder à l’appareil. Ce processus permet de s’assurer que l’appareil termine l’intégration et qu’il n’est pas laissé orphelin dans un état sans aucun utilisateur lié.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Attribuer un utilisateur et un nom convivial à un appareil Autopilot <!--1346521 -->
Vous pouvez désormais [affecter un utilisateur à un appareil Autopilot spécifique](enrollment-autopilot.md). Les administrateurs pourront également donner des noms conviviaux pour accueillir l’utilisateur lors de la configuration de leur appareil avec Autopilot.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilisation de licences d’appareil VPP pour préprovisionner le Portail d’entreprise lors d’une inscription DEP <!-- 1608345 -->
Vous pouvez maintenant utiliser des licences d’appareil du programme d’achat en volume (VPP, Volume Purchase Program) pour préprovisionner le portail d’entreprise pendant les inscriptions au Programme d’inscription des appareils (DEP, Device Enrollment Program). Pour ce faire, quand vous [créez ou modifiez un profil d’inscription](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), spécifiez le jeton VPP que vous souhaitez utiliser pour installer le portail d’entreprise. Assurez-vous que votre jeton n’expire pas et que vous avez suffisamment de licences pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune pousse le Portail d’entreprise de l’App Store à la place (un identifiant Apple vous sera demandé).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmation obligatoire pour supprimer un jeton VPP utilisé pour le préprovisionnement du Portail d’entreprise <!-- 2237634 -->
Une confirmation est maintenant obligatoire pour supprimer un jeton VPP (Volume Purchase Program) si celui-ci est utilisé pour approvisionner préalablement le portail d’entreprise lors d’une inscription DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloquer les inscriptions d’appareils personnels Windows <!-- 1849498 -->
Vous pouvez [bloquer l’inscription des appareils personnels Windows](enrollment-restrictions-set.md#set-device-type-restrictions) avec la [gestion des appareils mobiles](windows-enroll.md) dans Intune. Les appareils inscrits avec [l’agent de PC Intune](manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité. Cette fonctionnalité sera déployée dans les prochaines semaines et il est possible que vous ne la voyiez pas immédiatement dans l’interface utilisateur.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Spécifier des modèles de nom d’ordinateur dans un profil Autopilot <!--1849855-->
Vous pouvez [spécifier un modèle de nom d’ordinateur](enrollment-autopilot.md#create-an-autopilot-deployment-profile) pour générer et définir le [nom de l’ordinateur](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) lors de l’inscription Autopilot. S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Pour les profils Windows Autopilot, masquez les options de changement de compte dans la page de connexion de l’entreprise et la page d’erreur de domaine <!--1901669 -->
De [nouvelles options de profil Windows Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) permettent aux administrateurs de masquer les options de changement de compte sur les pages de connexion et d’erreur de domaine de l’entreprise. Pour masquer ces options, il est nécessaire de configurer la marque de société dans Azure Active Directory. S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Prise en charge de macOS pour le Programme d’inscription des appareils Apple <!-- 747651 -->
Intune prend maintenant en charge l’inscription d’appareils macOS dans le Programme d’inscription des appareils (DEP) Apple. Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils d’Apple](device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Gestion des appareils

#### <a name="delete-jamf-devices----2653306--"></a>Supprimer des appareils Jamf <!-- 2653306-->
Vous pouvez supprimer des appareils gérés par JAMF, en accédant à **Appareils** > choisissez l’appareil Jamf > **Supprimer**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Modifier la terminologie pour « mettre hors service » et « réinitialiser » <!-- 2175759 -->
Pour être cohérent avec l’API Graph, les termes suivants ont été changés dans l’interface utilisateur et la documentation d’Intune :
- **Supprimer les données d’entreprise** est remplacé par « Mettre hors service »
- **Réinitialisation d’usine** est remplacé par **réinitialiser**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Boîte de dialogue de confirmation si l’administrateur essaie de supprimer le Certificat Push MDM Apple <!-- 297909500-->
Si quelqu’un tente de supprimer un certificat Push MDM Apple, une boîte de dialogue de confirmation indique le nombre d’appareils iOS et macOS associés. Si le certificat est supprimé, ces appareils doivent être réinscrits.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Paramètres de sécurité supplémentaires pour le programme d’installation de Windows <!-- 2282430 -->
Vous pouvez permettre aux utilisateurs de contrôler les installations d’applications. Si cette fonctionnalité est activée, les installations qui sinon pourraient être arrêtées en raison d’une violation de sécurité sont autorisées à poursuivre leur exécution. Vous pouvez indiquer au programme d’installation de Windows d’utiliser des autorisations élevées quand il installe un programme sur un système. Vous pouvez en outre autoriser l’indexation des éléments de la Protection des informations Windows et le stockage de leurs métadonnées dans un emplacement non chiffré. Quand la stratégie est désactivée, les éléments protégés par la Protection des informations Windows ne sont pas indexés et n’apparaissent pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Les fonctionnalités de ces options sont désactivées par défaut. 

#### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nouvelle mise à jour de l’expérience utilisateur du site web Portail d’entreprise <!--2000968 -->
En nous basant sur les commentaires que nous ont envoyés des clients, nous avons ajouté de nouvelles fonctionnalités au site web Portail d’entreprise. Vous allez constater une nette amélioration des fonctionnalités existantes et de la facilité d’utilisation sur vos appareils. Les différentes zones du site, comme les détails de l’appareil, le feedback et le support, ainsi que la vue d’ensemble de l’appareil, bénéficient d’une nouvelle présentation interactive et moderne. Vous découvrirez également les points suivants :

- Flux de travail simplifiés sur toutes les plateformes d’appareils
- Flux d’identification et d’inscription des appareils améliorés
- Plus de messages d’erreur utiles
- Un langage plus convivial, avec moins de jargon technique
- La possibilité de partager des liens directs vers les applications
- Des performances améliorées pour les grands catalogues d’applications
- Accessibilité accrue pour tous les utilisateurs  

La [documentation du site web Portail d’entreprise Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) a été mise à jour pour refléter ces modifications. Pour voir un exemple des améliorations de l’application, consultez [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Détection de jailbreak améliorée dans les rapports de conformité<!-- 2198738 -->
Les états du paramètre de détection de jailbreak améliorée apparaissent désormais dans les rapports de conformité de la console d’administration.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-policies---1081974---"></a>Étiquettes de délimitation pour les stratégies <!--1081974 -->
Vous pouvez [créer des étiquettes de délimitation](scope-tags.md) pour limiter l’accès aux ressources Intune. Ajoutez une balise d’étendue à une attribution de rôle, puis la balise d’étendue à un profil de configuration. Le rôle a uniquement accès aux ressources avec des profils de configuration qui ont des balises d’étendue correspondantes (ou aucune balise d’étendue).





<!-- ########################## -->
## <a name="july-2018"></a>Juillet 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Prise en charge des applications métier pour macOS <!-- 1895847 -->
Microsoft Intune permet aux applications métier macOS d’être déployées en mode **Obligatoire** ou **Disponible avec inscription**. Pour les utilisateurs finaux, les applications peuvent être déployées en mode **Disponible** à l’aide du Portail d’entreprise pour macOS ou du [site web Portail d’entreprise](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Prise en charge des applications intégrées iOS pour le mode plein écran <!-- 2051098 -->
En plus des applications du Store et des applications gérées, vous pouvez maintenant sélectionner une application intégrée (par exemple, Safari) qui s’exécute en mode plein écran sur un appareil iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modifier vos déploiements d’applications Office 365 Pro Plus <!-- 2150145 -->
En tant qu’administrateur Microsoft Intune, vous avez une plus grande capacité de modification de vos déploiements d’applications Office 365 Pro Plus. En outre, vous n’avez plus à supprimer vos déploiements pour modifier des propriétés de la suite. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications**. Dans la liste des applications, sélectionnez votre suite Office 365 Pro Plus.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Une mise à jour du Kit de développement logiciel (SDK) Intune pour Android est maintenant disponible <!-- 2744271-->
Une version mise à jour du SDK d’application Intune pour Android est disponible pour prendre en charge la version Android P. Si vous êtes un développeur d’applications et que vous utilisez le SDK Intune pour Android, vous devez installer la version mise à jour du SDK d’application Intune pour garantir que les fonctionnalités Intune au sein de vos applications Android continuent de fonctionner comme prévu sur les appareils Android P. Cette version du SDK d’application Intune fournit un plug-in intégré qui effectue les mises à jour du Kit SDK. Vous n’avez pas besoin de réécrire le code existant qui est intégré. Pour plus d’informations, consultez [SDK Intune pour Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si vous utilisez l’ancien style de génération de badge pour Intune, nous vous recommandons d’utiliser l’icône porte-documents. Pour plus d’informations sur la personnalisation, consultez [ce référentiel GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Nouvelles opportunités de synchronisation dans l’application Portail d’entreprise pour Windows  
L’application Portail d’entreprise pour Windows vous permet désormais de lancer une synchronisation directement à partir de la barre des tâches Windows et du menu Démarrer. Cette fonctionnalité est particulièrement utile si votre seule tâche consiste à synchroniser des appareils et à accéder aux ressources d’entreprise. Pour accéder à la nouvelle fonctionnalité, cliquez avec le bouton droit sur l’icône Portail d’entreprise épinglée à votre barre des tâches ou au menu Démarrer. Dans les options de menu (également appelées liste de raccourcis), sélectionnez **Synchroniser cet appareil**. Le portail d’entreprise s’ouvre à la page **Paramètres** et lance la synchronisation. Pour examiner les nouvelles fonctionnalités, consultez [Nouveautés de l’interface utilisateur](whats-new-app-ui.md).   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nouvelles expériences d’exploration dans l’application Portail d’entreprise pour Windows  
Désormais, quand vous parcourez ou recherchez des applications dans l’application Portail d’entreprise pour Windows, vous pouvez basculer entre la vue **Vignettes** existante et la nouvelle vue **Détails**. La nouvelle vue répertorie les détails des applications, tels que le nom, l’éditeur, la date de publication et l’état d’installation.  

La vue **Installée** de la page **Applications** vous permet de voir les détails concernant les installations d’applications terminées et en cours. Pour voir à quoi ressemble la nouvelle vue, consultez [Nouveautés de l’interface utilisateur](whats-new-app-ui.md).  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Amélioration de l’expérience de l’application Portail d’entreprise pour les gestionnaires d’inscription d’appareil  
Quand un gestionnaire d’inscription d’appareil se connecte à l’application Portail d’entreprise pour Windows, l’application affiche à présent uniquement l’appareil en cours d’exécution actuel du gestionnaire. Cette amélioration permet de réduire les délais d’attente qui se produisaient auparavant quand l’application essayait d’afficher tous les appareils inscrits par le gestionnaire d’inscription d’appareil.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquer l’accès à l’application en fonction des modèles et des fournisseurs d’appareils non approuvés  <!-- 1425689 ! -->
L’administrateur informatique Intune peut appliquer une liste donnée de fabricants Android et/ou de modèles iOS par le biais de stratégies Intune App Protection. L’administrateur informatique peut fournir une liste de fabricants (séparés par des points-virgules) pour les stratégies Android et une liste de modèles d’appareils pour les stratégies iOS. Les stratégies de protection des applications Intune concernent uniquement Android et iOS. Deux actions distinctes peuvent être effectuées sur cette liste donnée :
- Blocage de l’accès à l’application sur les appareils qui ne figurent pas dans la liste, ou
- Réinitialisation sélective des données d’entreprise sur les appareils qui ne figurent pas dans la liste 

L’utilisateur ne peut pas accéder à l’application cible si les conditions requises par la stratégie ne sont pas remplies. En fonction des paramètres, l’utilisateur peut être bloqué ou une réinitialisation sélective de ses données d’entreprise est effectuée dans l’application. Sur les appareils iOS, cette fonctionnalité nécessite la participation d’applications (comme WXP, Outlook, Managed Browser ou Yammer) pour intégrer le SDK Intune App dans le but d’appliquer cette fonctionnalité avec les applications ciblées. Cette intégration se produit par propagation et dépend des équipes d’application spécifiques. Sur Android, cette fonctionnalité nécessite la version la plus récente du portail d’entreprise. 

Sur les appareils de l’utilisateur final, le client Intune effectue une action sur la base d’une mise en correspondance simple des chaînes spécifiées dans le panneau Intune pour les stratégies de protection d’application. Cela dépend entièrement de la valeur signalée par l’appareil. Par conséquent, il est conseillé à l’administrateur informatique de vérifier que le comportement prévu est exact. Pour ce faire, vous pouvez tester ce paramètre en ciblant différents fabricants d’appareils et modèles sur un petit groupe d’utilisateurs. Dans Microsoft Intune, sélectionnez **Applications clientes** > **Stratégies de protection des applications** pour afficher et ajouter des stratégies de protection des applications. Pour plus d’informations sur les stratégies de protection d’applications, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md) et [Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Intune](app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Accès aux builds de préversion du portail d’entreprise macOS <!-- 1734766 -->
À l’aide de Microsoft AutoUpdate, vous pouvez vous inscrire pour recevoir des builds de manière anticipée en rejoignant le programme Insider. L’inscription vous permet d’utiliser le portail d’entreprise mis à jour avant qu’il soit accessible à vos utilisateurs finaux. Pour plus d’informations, consultez le [blog Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Créer une stratégie de conformité des appareils à l’aide de paramètres de pare-feu sur ses appareils macOS <!-- 1497640 -->
Quand vous créez une stratégie de conformité macOS (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : macOS** > **Sécurité du système**), de nouveaux paramètres **Pare-feu** sont disponibles : 

- **Pare-feu** : configurez la façon dont les connexions entrantes sont traitées dans votre environnement.
- **Connexions entrantes** : **Bloquer** toutes les connexions entrantes, à l’exception de celles nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage.
- **Mode furtif** : **Activer** le mode furtif pour empêcher l’appareil de répondre aux demandes de sondage. L’appareil continue de répondre aux requêtes entrantes des applications autorisées.

S’applique à : macOS 10.12 et versions ultérieures

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nouveau profil de configuration d’appareils Wi-Fi pour Windows 10 et versions ultérieures <!-- 1879077 -->
Actuellement, vous pouvez importer et exporter des profils Wi-Fi à l’aide de fichiers XML. Cette mise à jour vous permet de créer un profil de configuration d’appareils Wi-Fi directement dans Intune, tout comme dans certaines autres plateformes.

Pour créer le profil, ouvrez **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Wi-Fi**. 

S’applique à Windows 10 et versions ultérieures.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosque : (obsolète) est grisé et ne peut pas être modifié <!-- 2149998 -->
La fonctionnalité Kiosque (préversion) (**Configuration de l’appareil**  > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** > **Restrictions d’appareil**) est obsolète et remplacée par [Paramètres Kiosque pour Windows 10 et ultérieur](kiosk-settings.md). Avec cette mise à jour, la fonctionnalité **Kiosque (obsolète)** est grisée et il est impossible de changer ou de mettre à jour l’interface utilisateur. 

Pour activer le mode Kiosque, consultez [Paramètres Kiosque pour Windows 10 et ultérieur](kiosk-settings.md).

S’applique à Windows 10 et ultérieur, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>Utilisation d’autorités de certification tierces par les API <!-- 2184013 -->
Dans cette mise à jour, une API Java permet l’intégration d’autorités de certification tierces à Intune et SCEP. Ensuite, les utilisateurs pourront ajouter le certificat SCEP à un profil et l’appliqueront aux appareils avec MDM.

Actuellement, Intune prend en charge les [demandes SCEP avec les services de certificats Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Basculer pour afficher ou masquer le bouton Terminer la session sur un navigateur kiosque <!-- 2455253 -->
Vous pouvez maintenant configurer les navigateurs Kiosque pour afficher ou non le bouton Terminer la session. Vous pourrez voir la commande dans **Configuration de l’appareil** > **Kiosque (préversion)** > **Navigateur web kiosque**. Si elle est activée, quand un utilisateur clique sur le bouton, l’application demande une confirmation pour terminer la session. Lorsque vous confirmez, le navigateur efface toutes les données de navigation et retourne à l’URL par défaut.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Créer un profil de configuration mobile eSIM <!-- 2564077 -->
Dans **Configuration de l’appareil**, vous pouvez créer un profil mobile eSIM. Vous pouvez importer un fichier qui contient les codes d’activation mobiles fournis par votre opérateur mobile. Vous pouvez ensuite déployer ces profils sur vos appareils Windows 10 eSIM LTE, tels que Surface Pro LTE et autres appareils compatibles eSIM.

Vérifiez si vos [appareils prennent en charge les profils eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

S’applique à Windows 10 et versions ultérieures. 

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Sélectionner des catégories d’appareils à l’aide des paramètres Accès Professionnel ou Scolaire <!-- 1058963 eenotready --> 
Si vous avez activé le [mappage de groupe d’appareils](https://docs.microsoft.com/intune/device-group-mapping), les utilisateurs de Windows 10 seront désormais invités à sélectionner une catégorie d’appareils après l’inscription via le bouton **Se connecter** situé dans **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utiliser sAMAccountName en tant que nom d’utilisateur de compte pour les profils de messagerie <!-- 1500307 -->
Vous pouvez utiliser le **SamAccountName** local comme nom d’utilisateur de compte pour les profils de messagerie pour Android, iOS et Windows 10. Vous pouvez également obtenir le domaine à partir de l’attribut `domain` ou `ntdomain` dans Azure Active Directory (Azure AD). Il est également possible d’entrer un domaine statique personnalisé.

Pour utiliser cette fonctionnalité, vous devez synchroniser l’attribut `sAMAccountName` de votre environnement Active Directory local avec Azure AD.

S’applique à [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 et ultérieur](email-settings-windows-10.md)

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
Quand vous créez une stratégie de conformité des appareils (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : Windows 10 et versions ultérieures** > **Paramètres** > **Sécurité du système**), il existe de nouvelles options **[Sécurité de l’appareil](compliance-policy-create-windows.md)** : 
- **Antivirus** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 
- **Logiciel anti-espion** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 

S’applique à : Windows 10 et versions ultérieures 

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marquer automatiquement les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile comme « entreprise ». <!-- 2404851 -->
Par défaut, les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile sont maintenant marqués **entreprise** sous **Propriété de l’appareil**. Vous n’avez pas à identifier manuellement les appareils d’entreprise avec leur numéro IMEI ni de série avant de les inscrire à l’aide de l’inscription Knox Mobile.

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Colonne indiquant les appareils sans profils dans la liste des jetons du programme d’inscription <!-- 1853904 -->
La liste des jetons du programme d’inscription contient une nouvelle colonne qui indique le nombre d’appareils auxquels aucun profil n’a été affecté. Les administrateurs peuvent ainsi affecter aisément des profils à ces appareils avant de les octroyer à des utilisateurs. Pour voir la nouvelle colonne, accédez à **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.

### <a name="device-management"></a>Gestion des appareils

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Suppression en bloc d’appareils dans le panneau Appareils <!-- 1793693 -->
Vous pouvez maintenant supprimer plusieurs appareils à la fois dans le panneau Appareils. Choisissez **Appareils** > **Tous les appareils** > sélectionner les appareils à supprimer > **Supprimer**. Pour les appareils qui ne peuvent pas être supprimés, une alerte s’affiche.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Changement des noms Google pour Android for Work et Play for Work <!--842873 -->
Intune a mis à jour la terminologie « Android for Work » pour refléter les changements apportés à la personnalisation de Google. Les termes « Android for Work » et « Play for Work » ne sont plus utilisés. Une terminologie différente est utilisée en fonction du contexte :
- « Android Enterprise » fait référence à la pile de gestion Android moderne globale.
- « Profil professionnel » ou « Propriétaire du profil » fait référence à des appareils BYOD gérés avec des profils professionnels.
- « Google Play géré » fait référence à l’App Store Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Règles de suppression des appareils <!-- 1609459 -->
De nouvelles règles sont disponibles pour vous permettre de supprimer automatiquement les appareils qui n’ont fait l’objet d’aucun archivage pendant un nombre de jours défini par vous-même. Pour voir la nouvelle règle, accédez au volet **Intune**, sélectionnez **Appareils**, puis sélectionnez **Règles de nettoyage d’appareil**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Prise en charge des appareils Android à usage unique appartenant à l’entreprise <!-- 1630973 -->

Intune prend désormais en charge les appareils Android hautement gérés, verrouillés et de style kiosque. Cela permet aux administrateurs de verrouiller davantage l’utilisation d’un appareil à une seule application ou à un petit ensemble d’applications, et empêche les utilisateurs d’activer d’autres applications ou d’effectuer d’autres actions sur l’appareil. Pour configurer un appareil en mode kiosque Android, accédez à Intune > **Inscription de l’appareil** > **Inscription Android** > **Inscriptions d’appareils en mode kiosque et tâche**. Pour plus d’informations, consultez [Configurer l’inscription des appareils kiosque Android entreprise](android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Évaluation par ligne des identificateurs d’appareil d’entreprise dupliqués chargés <!-- 2203794-->
Pendant le chargement d’ID d’appareils d’entreprise, Intune fournit désormais une liste de tous les doublons et vous donne la possibilité de remplacer ou de conserver les informations existantes. Le rapport s’affiche s’il existe des doublons après avoir choisi **Inscription de l’appareil** > **Identificateurs d’appareil d’entreprise** > **Ajouter des identificateurs**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Ajouter manuellement des identificateurs d’appareil d’entreprise <!-- 2203803 -->
Vous pouvez désormais ajouter manuellement des identificateurs d’appareil d’entreprise. Dans **Inscription de l’appareil** > **Identificateurs d’appareils d’entreprise** > **Ajouter**. 


<!-- ########################## -->
## <a name="june-2018"></a>Juin 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Prise en charge mobile Microsoft Edge pour les stratégies de protection des applications Intune <!-- 1817882 -->
Le navigateur Microsoft Edge pour appareils mobiles prend maintenant en charge les stratégies de protection des applications définies dans Intune.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Récupérer l’ID de modèle utilisateur de l’application associé (AUMID) pour les applications Microsoft Store pour Entreprises en mode plein écran <!-- 1560077 ! -->
Intune peut désormais récupérer les ID de modèle utilisateur d’application (AUMID) pour les applications Microsoft Store pour Entreprises afin de fournir une configuration améliorée du profil kiosque.

Pour plus d’informations sur les applications Microsoft Store pour Entreprises, consultez [Gérer des applications à partir du Microsoft Store pour Entreprises](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nouvelle page de personnalisation du Portail d’entreprise <!-- 1916370 -->
La page de personnalisation du portail d’entreprise a une nouvelle mise en page, de nouveaux messages et de nouvelles info-bulles.


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo : nouveau partenaire de Mobile Threat Defense <!-- 1169249 -->
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Pradeo, une solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Utiliser le mode FIPS avec le connecteur NDES Certificate <!-- 1333688 -->
Quand vous installiez le connecteur NDES Certificate sur un ordinateur sur lequel le mode FIPS (Federal Information Processing Standard) est activé, l’émission et la révocation de certificats ne fonctionnaient pas comme prévu. Avec cette mise à jour, la prise en charge de la norme FIPS est incluse avec le connecteur NDES Certificate. 

Cette mise à jour comprend également :

- Le connecteur NDES Certificate nécessite .NET 4.5 Framework, qui est automatiquement inclus avec Windows Server 2016 et Windows Server 2012 R2. Précédemment, .NET 3.5 Framework était la version minimale exigée.
- La prise en charge de TLS 1.2 est incluse avec le connecteur NDES Certificate. Ainsi, si le serveur avec le connecteur NDES Certificate installé prend en charge TLS 1.2, TLS 1.2 est utilisé. Si le serveur ne prend pas en charge TLS 1.2, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

Pour plus d’informations, consultez [Configurer et utiliser des certificats SCEP ](certificates-scep-configure.md) et [Configurer et utiliser des certificats PKCS](certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Prise en charge des profils de VPN Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
Avec cette mise à jour, vous pouvez choisir Palo Alto Networks GlobalProtect comme type de connexion VPN pour les profils VPN dans Intune (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Type de profil** > **VPN**). Dans cette version, les plateformes suivantes sont prises en charge : 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ajouts aux paramètres Options de sécurité locales de l’appareil <!-- 1403702 -->
Vous pouvez désormais configurer des paramètres Options de sécurité locales de l’appareil supplémentaires pour les appareils Windows 10. Des paramètres supplémentaires sont disponibles dans les domaines Client réseau Microsoft, Serveur réseau Microsoft, Accès et sécurité réseau, ainsi qu’Ouverture de session interactive. Recherchez ces paramètres dans la catégorie Endpoint Protection quand vous créez une stratégie de configuration d’appareil Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Activer le mode plein écran sur les appareils Windows 10 <!-- 1560072 ! -->
Sur les appareils Windows 10, vous pouvez créer un profil de configuration et activer le mode kiosque (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** > **Restrictions de l’appareil** > **Kiosque**). Dans cette mise à jour, le paramètre **Kiosque (préversion)** est renommé **Kiosque (obsolète)**. **Kiosque (obsolète)** n’est plus recommandé, mais continuera à fonctionner jusqu’à la mise à jour de juillet. **Kiosque (obsolète)** est remplacé par le nouveau type de profil **Kiosque** (**Créer un profil** > **Windows 10** > **Kiosque (préversion)**), qui contiendra les paramètres permettant de configurer des kiosques sur Windows 10 RS4 et ultérieur.

S’applique à Windows 10 et versions ultérieures.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Le graphique utilisateur des profils d’appareil est de retour <!-- 2160133 -->
Tout en améliorant les chiffres indiqués sur le graphique des profils d’appareil (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble** ), le graphique utilisateur avait été supprimé temporairement.

Avec cette mise à jour, le graphique utilisateur est de retour et affiché dans le portail Azure.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Prise en charge de l’inscription Windows Autopilot sans authentification utilisateur <!-- 1165118 -->
Intune prend désormais en charge l’inscription Windows Autopilot sans authentification utilisateur. Il s’agit d’une nouvelle option dans le profil de déploiement Windows Autopilot, « Mode de déploiement Autopilot », définie sur « Déploiement autonome ».  L’appareil doit exécuter Windows 10 Insider Preview Build 17672 ou une version ultérieure et posséder une puce TPM 2.0 pour effectuer correctement ce type d’inscription. Dans la mesure où aucune authentification utilisateur n’est exigée, vous devez affecter cette option uniquement aux appareils sur lesquels vous avez un contrôle physique.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nouveau paramètre de langue/région lors de la configuration OOBE (Out-of-Box Experience) pour AutoPilot <!-- 1821766 -->
Un nouveau paramètre de configuration est disponible pour définir la langue et la région des profils Autopilot pendant l’expérience OOBE (Out of Box Experience). Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nouveau paramètre de configuration du clavier de l’appareil <!-- 1821768 -->
Un nouveau paramètre sera disponible pour configurer le clavier pour les profils AutoPilot pendant l’expérience OOBE. Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Déplacement des profils AutoPilot vers le ciblage de groupe <!-- 1877935 -->
Des profils de déploiement AutoPilot peuvent être affectés à des groupes Azure AD contenant des appareils AutoPilot.

### <a name="device-management"></a>Gestion des appareils

#### <a name="set-compliance-by-device-location----851881----"></a>Définir la conformité en fonction de l’emplacement d’appareil <!-- 851881 ! -->
Dans certains cas, vous souhaiterez peut-être limiter l’accès aux ressources d’entreprise à un emplacement spécifique, défini par une connexion réseau. Vous pouvez désormais créer une stratégie de conformité (**Conformité de l’appareil** > **Emplacements**) en fonction de l’adresse IP de l’appareil. Si l’appareil bascule en dehors de la plage IP, il ne peut plus accéder aux ressources d’entreprise.

S’applique à : appareils Android 6.0 et ultérieur, avec l’application Portail d’entreprise mise à jour

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Empêcher l’installation d’applications et d’expériences consommateurs sur les appareils AutoPilot Windows 10 Entreprise RS4<!-- 1621980 -->
Vous pourrez empêcher l’installation d’applications et d’expériences consommateur sur vos appareils AutoPilot Windows 10 Entreprise RS4. Pour voir cette fonctionnalité, accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Plateforme** = **Windows 10 ou version ultérieure** > **Type de profil** = **Restrictions de l’appareil** > **Configurer** > **Windows à la une** > **Fonctionnalités grand public**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Désinstaller la dernière version à partir de mises à jour logicielles Windows 10 <!-- 1732948 -->
Si vous détectez un problème important sur vos machines Windows 10, vous pouvez choisir de désinstaller (restaurer) la dernière mise à jour des fonctionnalités ou la dernière mise à jour qualité. La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil. La désinstallation déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10. Pour les mises à jour des fonctionnalités en particulier, vous pouvez limiter de 2 à 60 jours la durée pendant laquelle une désinstallation de la version la plus récente peut être appliquée. Pour définir des options de désinstallation de mise à jour logicielle, sélectionnez **Mises à jour logicielles** dans le panneau **Microsoft Intune** dans le portail Azure. Sélectionnez ensuite **Anneaux de mise à jour Windows 10** dans le panneau **Mises à jour logicielles**. Vous pouvez alors choisir l’option **Désinstaller** dans la section **Vue d’ensemble**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Rechercher l’IMEI et le numéro de série dans tous les appareils <!-- 1793685 -->
Vous pouvez désormais rechercher les IMEI et les numéros de série dans le panneau Tous les appareils (l’e-mail, l’UPN, le nom de l’appareil et le nom d’administration restent disponibles). Dans Intune, choisissez **Appareils** > **Tous les appareils** > entrez votre recherche dans la zone de recherche.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Le champ de nom de gestion est modifiable <!-- 1875989 -->
Vous pourrez maintenant modifier le champ de nom de gestion dans le panneau **Propriétés** d’un appareil. Pour modifier ce champ, choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil > **Propriétés**. Vous pouvez utiliser le champ de nom de gestion pour identifier un appareil de manière unique.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nouveau filtre Tous les appareils : Catégorie d’appareil <!-- 1878520 -->
Vous pouvez désormais filtrer la liste **Tous les appareils** par catégorie d’appareil. Pour ce faire, choisissez **Appareils** > **Tous les appareils** > **Filtre** > **Catégorie d’appareil**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Utiliser TeamViewer pour partager l’écran des appareils iOS et MacOS <!-- 1985547 -->
Les administrateurs peuvent désormais se connecter à [TeamViewer](device-profile-android-teamviewer.md) et démarrer une session de partage d’écran avec des appareils iOS et macOS. Les utilisateurs d’iPhone, iPad et macOS pourront partager leurs écrans en direct avec tout autre appareil de bureau ou portable. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Prise en charge de plusieurs connecteurs Exchange <!-- 2070451 -->
Vous n’êtes plus limité à un seul connecteur Microsoft Intune Exchange par locataire. Intune prend désormais en charge plusieurs connecteurs Exchange afin que vous puissiez configurer l’accès conditionnel Intune avec plusieurs organisations Exchange locales.

Avec un connecteur Exchange local Intune, vous pouvez gérer l’accès de l’appareil aux boîtes aux lettres Exchange locales en fonction de l’inscription ou non d’un appareil dans Intune et de sa conformité aux stratégies de conformité Intune. Pour configurer un connecteur, téléchargez le connecteur Exchange local Intune à partir du portail Azure et installez-le sur un serveur de votre organisation Exchange. Dans le tableau de bord Microsoft Intune, choisissez **Accès local**, puis sous **Installation**, choisissez **Connecteur Exchange ActiveSync**. Téléchargez le connecteur Exchange local et installez-le sur un serveur de votre organisation Exchange. Maintenant que vous n’êtes plus limité à un seul connecteur Exchange par client, si vous avez d’autres organisations Exchange, vous pouvez suivre le même processus pour télécharger et installer un connecteur pour chaque organisation Exchange supplémentaire.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nouveaux renseignements concernant le matériel : CCID <!-- 2156657 -->
L’information CCID (Chip Card Interface Device) est désormais incluse pour chaque appareil. Pour la voir, choisissez **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel** > vérifiez sous **Détails du réseau**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Attribuer tous les utilisateurs et tous les appareils en tant que groupes d’étendue <!-- 2196803 -->
Vous pouvez désormais affecter tous les utilisateurs, tous les appareils, ainsi que tous les utilisateurs et appareils dans des groupes d’étendue. Pour ce faire, choisissez **Rôles Intune** > **Tous les rôles** > **Gestionnaire de stratégie et de profils** > **Affectations**  > choisissez une affectation > **Étendue (Groupes)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Informations UDID désormais incluses pour les appareils iOS et macOS <!-- 2219806 -->
Pour voir l’identificateur unique de l’appareil (UDID) pour les appareils iOS et macOS, accédez à **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel**. L’UDID est disponible uniquement pour les appareils d’entreprise (tel que défini sous **Appareils** > **Tous les appareils** > choisissez un appareil > **Propriétés** > **Propriété de l’appareil**).

### <a name="intune-apps"></a>Applications Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Amélioration de la résolution des problèmes d’installation des applications <!-- 928990 -->
Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Nous publions une préversion publique de nos fonctionnalités de résolution des problèmes d’application. Vous remarquerez sous chaque appareil un nouveau nœud appelé **Applications gérées**. Il liste les applications qui ont été distribuées via MDM Intune. À l’intérieur du nœud figure une liste d’états d’installations d’applications. Si vous sélectionnez une application, vous verrez la vue de résolution des problèmes de cette application spécifique. Dans la vue de résolution des problèmes, vous verrez le cycle de vie de bout en bout de l’application, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. De plus, si l’installation de l’application a échoué, vous verrez le code d’erreur et un message utile sur la cause de l’erreur. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Stratégies de protection des applications Intune et Microsoft Edge <!-- 1818968 -->
Le navigateur Microsoft Edge pour les appareils mobiles (iOS et Android) prend désormais en charge les stratégies de protection des applications Microsoft Intune. Les utilisateurs d’appareils iOS et Android qui se connectent avec leur compte d’entreprise Azure AD dans l’application Microsoft Edge seront protégés par Intune. Sur les appareils iOS, la stratégie **Exiger un navigateur géré pour le contenu web** permet aux utilisateurs d’ouvrir des liens dans Microsoft Edge quand il est géré.

<!-- ########################## -->
## <a name="may-2018"></a>Mai 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configuration de vos stratégies de protection des applications <!-- 2144597 Part 2 -->

Dans le portail Azure, au lieu d’accéder au panneau du service Intune App Protection, vous accédez désormais simplement à Intune. Il n’existe plus maintenant qu’un seul emplacement pour les stratégies de protection des applications dans Intune. Notez que toutes vos stratégies de protection des applications se trouvent dans le panneau **Application mobile** d’Intune, sous **Stratégies de protection des applications**. Cette intégration permet de simplifier l’administration de la gestion de votre cloud. Gardez à l’esprit que toutes les stratégies de protection des applications sont déjà dans Intune et que vous pouvez modifier les stratégies d’accès conditionnel que vous avez précédemment configurées. Les stratégies Intune de protection des applications et d’accès conditionnel sont désormais sous **Accès conditionnel**, qui se trouve sous la section **Gérer** du panneau **Microsoft Intune** ou sous la section **Sécurité** du panneau **Azure Active Directory**. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Nécessite l’installation de stratégies, d’applications et de profils de certificat et de réseau <!-- 1553555 -->
Les administrateurs peuvent empêcher les utilisateurs finaux d’accéder à Windows 10 RS4 Desktop jusqu’à ce qu’Intune installe les stratégies, les applications et les profils de certificat et de réseau pendant le provisionnement des appareils AutoPilot. Pour plus d’informations, consultez [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Prise en charge de l’inscription Samsung Knox Mobile <!--1112863-->
Quand vous utilisez Intune avec Samsung Knox Mobile Enrollment (KME), vous pouvez inscrire un grand nombre d’appareils Android appartenant à l’entreprise. Les utilisateurs sur des réseaux Wi-Fi ou mobiles peuvent s’inscrire en quelques clics quand ils allument leurs appareils pour la première fois. En cas d’utilisation de l’application Knox Deployment App, les appareils peuvent être inscrits à l’aide de Bluetooth ou NFC. Pour plus d’informations, consultez [Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung](android-samsung-knox-mobile-enroll.md).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner 

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Demande d’aide sur l’application Portail d’entreprise pour Windows 10 <!-- 1874137 -->
Le portail d’entreprise pour Windows 10 envoie maintenant les journaux d’application directement à Microsoft quand l’utilisateur lance le flux de travail pour obtenir de l’aide sur un problème. Cela facilite le dépannage et la résolution des problèmes portés à l’attention de Microsoft.

<!-- ########################## -->
## <a name="april-2018"></a>Avril 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Prise en charge des codes secrets pour les codes PIN MAM sur Android<!-- 1438086 -->

Les administrateurs Intune peuvent définir une condition de lancement d’application pour appliquer un code secret au lieu d’un code PIN MAM numérique. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Intune prend en charge un code secret comme le code PIN numérique existant, pouvant définir une longueur minimale et autorisant la répétition des caractères et des séquences par le biais de la console d’administration. Cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise sur Android. Cette fonctionnalité est déjà disponible pour iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Prise en charge des applications métier pour macOS <!-- 1473977 -->
Microsoft Intune permettra d’installer des applications métier macOS à partir du portail Azure. Vous pourrez ajouter une application métier macOS à Intune après qu’elle a été prétraitée par l’outil disponible dans GitHub. Dans le portail Azure, choisissez **Applications clientes** à partir du panneau **Intune**. Dans le panneau **Applications clientes**, choisissez **Applications** > **Ajouter**. Dans le panneau **Ajouter une application**, sélectionnez **Application métier**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Intégration des groupes Tous les utilisateurs et Tous les appareils pour l’affectation d’applications aux profils professionnels Android Entreprise <!-- 1813073 -->
Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications aux profils professionnels Android Entreprise. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune réinstalle les applications nécessaires désinstallées par les utilisateurs <!-- 1947010 -->
Si un utilisateur final désinstalle une application obligatoire, Intune la réinstalle automatiquement en moins de 24 heures au lieu d’attendre le cycle de réévaluation de 7 jours.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Changement de l’endroit où vous configurez vos stratégies de protection d’application <!-- 2144597 -->

Dans le portail Azure, dans le service Microsoft Intune, nous allons vous rediriger temporairement du panneau du service **Intune App Protection** vers le panneau **Application Mobile**. Notez que toutes vos stratégies de protection d’application sont déjà sur le panneau **Application mobile** dans Intune, sous la configuration de l’application. Au lieu d’accéder à Intune App Protection, vous accédez simplement à Intune. En avril 2018, nous mettrons fin à la redirection et nous la supprimerons complètement du panneau du service **Intune App Protection** : il n’y aura alors plus qu’un seul emplacement pour les stratégies de protection d’application dans Intune. 

**Comment cela m’affecte-t-il ?**
Ce changement affecte les clients autonomes et les clients hybrides Intune (Intune avec Configuration Manager). Cette intégration permet de simplifier l’administration de la gestion de votre cloud.

**Que faire pour se préparer à ce changement ?**
Mettez **Intune** en favori à la place du panneau de service **Intune App Protection**, et veillez à vous familiariser avec le workflow de stratégie de protection des applications dans le panneau **Application mobile** d’Intune. Pendant une courte période, nous allons assurer la redirection, puis nous supprimerons le panneau **Protection d’applications**. N’oubliez pas que toutes les stratégies de protection des applications sont déjà dans Intune, et que vous pouvez modifier vos stratégies d’accès conditionnel. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 

### <a name="device-configuration"></a>Configuration des appareils

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Le graphique des profils d’appareil et la liste d’états affichent l’ensemble des appareils contenus dans un groupe <!-- 1449153 -->
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

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Afficher l’ID d’appelant dans un profil personnel - Profil professionnel Android Entreprise <!--1098984 -->
Quand vous utilisez un profil personnel sur un appareil, les utilisateurs finaux ne voient pas forcément les détails relatifs à l’ID d’appelant d’un contact professionnel. 

Avec cette mise à jour, il existe un nouveau paramètre dans **Android Entreprise** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
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

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Blocage des appareils photo et des captures d’écran dans les profils professionnels Android Entreprise <!-- 1098977 -->
Vous disposez de deux nouvelles propriétés de blocage au moment de configurer des restrictions d’appareil pour les appareils Android : 
- Appareil photo : bloque l’accès à tous les appareils photo sur l’appareil
- Capture d’écran : bloque la capture d’écran et empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée

S’applique aux profils professionnels Android Entreprise.

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Utiliser le client Cisco AnyConnect pour iOS <!-- 1333708 -->

Quand vous créez un profil VPN pour iOS, vous disposez désormais de deux options : **Cisco AnyConnect** et **Cisco Legacy AnyConnect**. Les profils Cisco AnyConnect prennent en charge les versions 4.0.7x et ultérieures. Les profils VPN Cisco AnyConnect pour iOS existants se nomment **Cisco Legacy AnyConnect** et continuent de fonctionner avec Cisco AnyConnect 4.0.5x et les versions antérieures, comme c’est le cas aujourd’hui.

> [!NOTE]
> Ce changement s’applique uniquement à iOS. Il existe toujours une seule option Cisco AnyConnect pour les plateformes Android, macOS et pour les profils professionnels Android Entreprise.


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nouvelles étapes d’inscription pour les utilisateurs sur les appareils dotés de macOS High Sierra 10.13.2+ <!--1734567 -->
macOS High Sierra 10.13.2 a introduit le concept d’inscription MDM « approuvée par l’utilisateur ». Les inscriptions approuvées permettent à Intune de gérer certains paramètres sensibles au niveau sécurité. Pour plus d’informations, consultez la documentation de prise en charge d’Apple ici : https://support.apple.com/HT208019.

Les appareils inscrits à l’aide du Portail d’entreprise macOS sont considérés comme « non approuvés par l’utilisateur », sauf si l’utilisateur final ouvre les préférences système et fournit une approbation manuellement. À cette fin, le Portail d’entreprise macOS invite désormais les utilisateurs sur macOS 10.13.2 et ultérieur à approuver manuellement leur inscription à la fin du processus d’inscription. La console d’administration Intune indiquera si un appareil inscrit est approuvé par l’utilisateur.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Les appareils macOS inscrits auprès de Jamf peuvent désormais s’inscrire auprès d’Intune <!-- 2370684 -->
Les versions 1.3 et 1.4 du portail d’entreprise macOS n’ont pas réussi à inscrire les appareils Jamf auprès d’Intune. Ce problème est résolu dans la version 1.4.2 du portail macOS.

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Mise à jour de l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android <!-- 1631531 -->
Nous avons mis à jour l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android afin de l’harmoniser avec les bonnes pratiques relatives à la plateforme Android. Désormais, quand les utilisateurs rencontrent un problème dans l’application, ils peuvent appuyer sur **Menu** > **Aide** et :
- Charger les journaux de diagnostic sur le site de Microsoft
- Envoyer un e-mail décrivant le problème et indiquant l’ID d’incident à une personne du support de l’entreprise  

Pour découvrir à quoi ressemble la mise à jour de l’expérience utilisateur de l’aide, accédez à [Envoyer des journaux à l’aide de la messagerie](/intune-user-help/send-logs-to-your-it-admin-by-email-android) et [Envoyer les erreurs à Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nouveau graphique de tendance des échecs d’inscription et tableau des raisons de ces échecs <!-- 1471783 -->
Dans la page Vue d’ensemble de l’inscription, vous pouvez voir la tendance des échecs d’inscription et les cinq premières causes d’échecs. En cliquant sur le graphique ou le tableau, vous pouvez explorer les détails et trouver des conseils de dépannage, ainsi que des suggestions de correction.


### <a name="device-management"></a>Gestion des appareils

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (Protection avancée contre les menaces) et Intune sont entièrement intégrés <!-- 1629303 -->

[Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indique le niveau de risque des appareils Windows 10. Dans le Centre de sécurité Windows Defender (portail ATP), vous pouvez créer une connexion à Microsoft Intune. Une fois créée, une stratégie de conformité Intune permet de déterminer un niveau de menace acceptable. Si le niveau de menace est dépassé, une stratégie d’accès conditionnel Azure AD (Active Directory) peut bloquer l’accès à différentes applications au sein de votre organisation.

Cette fonctionnalité permet à ATP d’analyser les fichiers, de détecter les menaces et de signaler tout risque sur vos appareils Windows 10.

Consultez [Activer ATP avec accès conditionnel dans Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Prise en charge des appareils sans utilisateurs <!-- 1637553 -->
Intune permet d’évaluer la conformité sur un appareil sans utilisateur, comme Microsoft Surface Hub. La stratégie de conformité peut cibler des appareils spécifiques. Ainsi, la conformité, et la non-conformité, peuvent être déterminées pour les appareils auxquels aucun utilisateur n’est associé.

#### <a name="delete-autopilot-devices----1713650---"></a>Supprimer des appareils Autopilot <!-- 1713650 -->
Les administrateurs Intune peuvent [supprimer les appareils AutoPilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Amélioration de l’expérience de suppression d’appareil <!--1832333 -->
Vous n’avez plus besoin de supprimer les données d’entreprise ou de réinitialiser un appareil aux paramètres d’usine avant de le [supprimer d’Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Pour voir la nouvelle expérience, connectez-vous à Intune et sélectionnez **Appareils** > **Tous les appareils** > nom de l’appareil > **Supprimer**.

Si vous souhaitez toujours la confirmation de réinitialisation/mise hors service, vous pouvez suivre le cycle de vie d’appareil standard en utilisant les commandes **Supprimer les données d’entreprise** et **Réinitialisation aux paramètres d’usine** avant la commande **Supprimer**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Lire les sons sur iOS en mode Perdu <!-- 1947769 -->
Quand les appareils iOS supervisés sont en [mode Perdu](device-lost-mode.md) MDM (Mobile Device Management), vous pouvez [lire un son](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Appareils** > **Tous les appareils** > sélectionnez un appareil iOS > **Vue d’ensemble** > **Plus**). La lecture du son se poursuit jusqu’à ce que l’appareil soit retiré du mode Perdu ou qu’un utilisateur désactive le son sur l’appareil. S’applique aux appareils iOS 9.3 et ultérieur.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquer ou autoriser les résultats web dans les recherches effectuées sur un appareil Intune <!--1972804-->

Les administrateurs peuvent maintenant bloquer les résultats web des recherches effectuées sur un appareil.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Amélioration des messages d’erreur liés à l’échec du chargement du Certificat Push MDM Apple <!-- 2172331 -->

Le message d’erreur explique que le même identifiant Apple doit être utilisé au moment du renouvellement d’un certificat MDM existant.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Test du portail d’entreprise pour macOS sur les machines virtuelles <!-- 2216679 -->

Nous avons publié des conseils pour aider les administrateurs informatiques à tester l’application Portail d’entreprise pour macOS sur des machines virtuelles dans Parallels Desktop et VMware Fusion. Découvrez-en plus dans [Inscrire des machines virtuelles macOS à des fins de test](macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### <a name="intune-apps"></a>Applications Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Mise à jour de l’expérience utilisateur de l’application Portail d’entreprise pour iOS <!--1412866 -->
Nous avons publié une mise à jour majeure de l’expérience utilisateur de l’application Portail d’entreprise pour iOS. La mise à jour comporte une refonte visuelle complète incluant une apparence plus moderne. Nous avons conservé les fonctionnalités de l’application, mais nous avons étendu sa facilité d’utilisation et son accessibilité.  

Vous découvrirez également les points suivants :
- Prise en charge de l’iPhone X.
- Lancement et chargement plus rapides des applications, pour faire gagner du temps aux utilisateurs.
- Barres de progression supplémentaires pour fournir aux utilisateurs les toutes dernières informations d’état.
- Améliorations de la façon dont les utilisateurs chargent les journaux pour faciliter le signalement des problèmes.  

Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Protéger les données Exchange locales à l’aide de la stratégie de protection des applications et de l’accès conditionnel d’Intune <!-- 1056954 -->
Vous pouvez désormais utiliser les fonctionnalités APP (stratégie de protection des applications) et CA (accès conditionnel) d’Intune pour protéger l’accès aux données Exchange locales avec Outlook Mobile. Pour ajouter ou modifier une stratégie de protection des applications dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Stratégies de protection des applications**. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).


### <a name="user-interface"></a>Interface utilisateur

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Amélioration des vignettes d’appareil dans le portail d’entreprise Windows 10 <!--2213364 -->

Les vignettes ont été mises à jour pour être plus accessibles aux utilisateurs malvoyants et proposer un meilleur rendu pour les outils de lecture d’écran.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Envoyer des rapports de diagnostic dans l’application Portail d’entreprise pour macOS <!-- 2216677 -->
L’application Portail d’entreprise pour les appareils macOS a été mise à jour afin d’améliorer la façon dont les utilisateurs signalent les erreurs relatives à Intune. À partir de l’application Portail d’entreprise, vos collaborateurs peuvent :

- Charger des rapports de diagnostic directement pour l’équipe de développement Microsoft.
- Envoyer par e-mail un ID d’incident à l’équipe de support informatique de votre entreprise.

Pour plus d’informations, consultez [Envoyer les erreurs pour macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune s’adapte au système Fluent Design dans l’application Portail d’entreprise pour Windows 10 <!-- 1195010 -->
L’application Portail d’entreprise Intune pour Windows 10 a été mise à jour avec l’[affichage de navigation de Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Le long de l’application, vous remarquerez une liste verticale statique de toutes les pages de niveau supérieur. Cliquez sur n’importe quel lien pour afficher des pages et passer de l’une à l’autre rapidement. Il s’agit de la première d’une série de mises à jour que vous verrez dans le cadre de nos efforts constants pour créer une expérience plus adaptive, empathique et familière dans Intune. Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

<!-- ########################## -->
## <a name="march-2018"></a>Mars 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertes relatives à l’expiration des applications métier iOS pour Microsoft Intune <!-- 748789 -->

Dans le portail Azure, Intune vous alerte quand des applications métier iOS arrivent à expiration. Quand vous chargez une nouvelle version de l’application métier iOS, Intune supprime la notification d’expiration de la liste des applications. Cette notification d’expiration est active uniquement pour les dernières applications métier iOS chargées. Un avertissement apparaît 30 jours avant l’expiration du profil de provisionnement de l’application métier iOS. Une fois que l’expiration a eu lieu, l’état de l’alerte passe à Expiré.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personnaliser vos thèmes de Portail d’entreprise avec des codes hexadécimaux <!--1049561 -->

Vous pouvez personnaliser la couleur du thème des applications Portail d’entreprise à l’aide de codes hexadécimaux. Quand vous entrez votre code hexadécimal, Intune détermine la couleur de texte qui offre le plus haut niveau de contraste entre la couleur de texte et la couleur d’arrière-plan. Vous pouvez voir un aperçu de la couleur du texte et du logo de votre entreprise par rapport à la couleur dans **Applications clientes** > **Portail d’entreprise**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusion et exclusion d’affectations d’applications en fonction des groupes pour Android Enterprise <!-- 1813081 -->

Android Enterprise (anciennement Android for Work) prend en charge l’inclusion et l’exclusion de groupes, mais ne prend pas en charge les groupes prédéfinis **Tous les utilisateurs** et **Tous les appareils**. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestion des appareils

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>Exporter tous les appareils vers des fichiers CSV dans Internet Explorer, Microsoft Edge ou Chrome <!-- 2258071 -->
Dans **Appareils** > **Tous les appareils**, vous pouvez **Exporter** les appareils vers une liste au format CSV. Les utilisateurs Internet Explorer ayant plus de 10 000 appareils peuvent exporter leurs appareils correctement dans plusieurs fichiers. Chaque fichier contient jusqu’à 10 000 appareils.

Les utilisateurs Microsoft Edge et Chrome ayant plus de 30 000 appareils peuvent exporter leurs appareils dans plusieurs fichiers. Chaque fichier contient jusqu’à 30 000 appareils.

La rubrique [Gérer des appareils](device-management.md) fournit plus de détails sur ce que vous pouvez faire avec les appareils que vous gérez.

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nouvelles améliorations de la sécurité dans le service Intune  <!-- 1637539 -->   

Nous avons introduit un bouton bascule dans Intune sur Azure, qui permet aux clients autonomes Intune de définir un appareil auquel aucune stratégie n’est affectée comme étant **Conforme** (fonctionnalité de sécurité désactivée) ou **Non conforme** (fonctionnalité de sécurité activée). Cela permet de garantir l’accès aux ressources uniquement après l’évaluation de la conformité de l’appareil.

Cette fonctionnalité vous impacte différemment selon que vous avez déjà affecté ou non des stratégies de conformité.

- Si vous êtes un nouveau compte ou un compte existant, et si vous n’avez affecté aucune stratégie de conformité à vos appareils, le bouton bascule est automatiquement défini sur **Conforme**. La fonctionnalité est désactivée par défaut dans la console. L’impact est inexistant pour l’utilisateur final.
- Si vous êtes un compte existant, et si vous avez des appareils auxquels vous avez affecté une stratégie de conformité, le bouton bascule est automatiquement défini sur **Non conforme**. La fonctionnalité est activée par défaut avec le déploiement de la mise à jour de mars.

Si vous utilisez des stratégies de conformité avec un accès conditionnel, et si cette fonctionnalité est activée, les appareils auxquels aucune stratégie de conformité n’a été affectée sont désormais bloqués par l’accès conditionnel. Les utilisateurs finaux associés à ces appareils, qui étaient autorisés à accéder aux e-mails, perdent leur accès, sauf si vous affectez au moins une stratégie de conformité à tous les appareils.   

Notez que même si l’état par défaut du bouton bascule est affiché dans l’IU avec les mises à jour de mars du service Intune, cet état n’est pas appliqué immédiatement. Les changements apportés au bouton bascule n’ont aucun impact sur la conformité des appareils tant que nous n’activons pas la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Nous vous informerons via le Centre de messages quand nous aurons activé la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Cela peut prendre quelques jours, une fois que la mise à jour de mars aura été appliquée à votre service Intune.

**Informations supplémentaires** : [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Détection de jailbreak améliorée <!-- 846515 -->

La détection de jailbreak améliorée est un nouveau paramètre de conformité qui améliore la manière dont Intune évalue les appareils jailbreakés. Avec ce paramètre, l’appareil s’enregistre plus fréquemment auprès d’Intune, lequel utilise les services de géolocalisation de l’appareil, ce qui impacte la durée de vie de la batterie.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Réinitialiser les mots de passe des appareils Android O <!-- 1238299 -->
Vous pouvez réinitialiser les mots de passe des appareils Android 8.0 inscrits à l’aide des profils professionnels. Quand vous envoyez une demande de réinitialisation de mot de passe à un appareil Android 8.0, cela entraîne la définition d’un nouveau mot de passe de déverrouillage de l’appareil ou d’une vérification du profil managé pour l’utilisateur actuel. La vérification ou le mot de passe est envoyé et prend effet immédiatement.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ciblage des stratégies de conformité pour les appareils dans des groupes d’appareils <!--1307012 -->

Vous pouvez appliquer des stratégies de conformité en ciblant des utilisateurs au sein de groupes d’utilisateurs. Avec cette mise à jour, vous pouvez appliquer des stratégies de conformité en ciblant des appareils au sein de groupes d’appareils. Les appareils ciblés dans le cadre de groupes d’appareils ne reçoivent aucune action de conformité.

#### <a name="new-management-name-column----1333586---"></a>Nouvelle colonne Nom de gestion <!-- 1333586 -->
 Une nouvelle colonne nommée **Nom de la gestion** est disponible dans le panneau des appareils. Il s’agit d’un nom généré automatiquement, non modifiable affecté par appareil, reposant sur la formule suivante :
- Nom par défaut pour tous les appareils : <username><em><devicetype></em><enrollmenttimestamp>
- Pour les appareils ajoutés en bloc : <ID_de_package/ID_de_profil><em><DeviceType></em><EnrollmentTime>

Il s’agit d’une colonne facultative dans le panneau Appareils. Elle n’est pas disponible par défaut. Vous pouvez y accéder uniquement via le sélecteur de colonne. Le nom de l’appareil n’est pas affecté par cette nouvelle colonne.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Les appareils iOS sont invités à entrer un code confidentiel toutes les 15 minutes <!--1550837 -->
Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code PIN toutes les 15 minutes. Les utilisateurs sont continuellement sollicités jusqu’à ce qu’un code PIN soit défini.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Planifier vos mises à jour automatiques <!--1805514 -->
Intune vous permet de contrôler l’installation des mises à jour automatiques à l’aide des [paramètres des anneaux de mise à jour Windows](windows-update-for-business-configure.md). Avec cette mise à jour, vous pouvez planifier des mises à jour récurrentes : hebdomadaires, quotidiennes et horaires.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Utiliser un nom unique comme sujet du certificat SCEP <!--2221763 -->
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

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurer le pare-feu d’applications Mac <!-- 1690461 -->

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
Intune vous permet de contrôler la [gestion des mises à jour logicielles](windows-update-for-business-configure.md). Avec cette mise à jour, la propriété <strong>Vérifications de redémarrage</strong> est disponible et activée par défaut. Pour ignorer les vérifications usuelles qui se produisent au redémarrage d’un appareil (comme les utilisateurs actifs, les niveaux de batterie, etc.), sélectionnez <strong>Ignorer</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nouveaux canaux de la préversion Windows 10 Insider disponibles pour les anneaux de déploiement <!-- 1746293 -->
Vous pouvez désormais sélectionner les canaux de maintenance Windows 10 Insider Preview suivants quand vous créez un anneau de déploiement Windows 10 :
- Version Windows Insider &#8208; Rapide
- Version Windows Insider &#8208; Lente
- Publier la version Windows Insider 

Pour plus d’informations sur ces canaux, consultez [Gérer les versions Insider Preview](https://insider.windows.com/for-business-organization-admin/).   
Pour plus d’informations sur la création de canaux de déploiement dans Intune, consultez [Gérer les mises à jour logicielles dans Intune](windows-update-for-business-configure.md).

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

### <a name="intune-apps"></a>Applications Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Les sites web Azure Active Directory peuvent nécessiter l’application Intune Managed Browser et prendre en charge l’authentification unique pour Managed Browser (préversion publique) <!-- 710595 -->

Avec Azure AD (Azure Active Directory), vous pouvez désormais restreindre l’accès aux sites web pour l’application Intune Managed Browser sur les appareils mobiles. Dans Managed Browser, les données de site web restent sécurisées et séparées des données personnelles de l’utilisateur final. Par ailleurs, Managed Browser prend en charge les fonctionnalités d’authentification unique pour les sites protégés par Azure AD. Si vous vous connectez à Managed Browser ou que vous utilisez Managed Browser sur un appareil avec une autre application gérée par Intune, Managed Browser peut accéder aux sites d’entreprise protégés par Azure AD sans que l’utilisateur ne doive entrer ses informations d’identification. Cette fonctionnalité s’applique aux sites comme Outlook Web Access (OWA) et SharePoint Online, ainsi qu’à d’autres sites d’entreprise tels que les ressources intranet accessibles par le proxy de l’application Azure. Pour plus d’informations, consultez [Contrôles d’accès dans l’accès conditionnel d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Mises à jour visuelles de l’application Portail d’entreprise pour Android <!--976944 -->

Nous avons mis à jour l’application Portail d’entreprise pour Android afin de suivre les recommandations de [Material Design](https://material.io/). Vous pouvez voir les images des nouvelles icônes dans l’article [Nouveautés de l’interface utilisateur d’application](whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Inscription par le biais de l’application Portail d’entreprise améliorée <!-- 1874230 eeready-->
Les utilisateurs qui inscrivent un appareil à l’aide du Portail d’entreprise sur Windows 10 (build 1703) et versions ultérieures peuvent désormais effectuer la première étape de l’inscription sans quitter l’application.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens et Surface Hub apparaissent désormais dans les listes d’appareils <!--1725868 -->
Nous avons ajouté la prise en charge de l’affichage des appareils HoloLens et Surface Hub inscrits auprès d’Intune dans l’application Portail d’entreprise pour Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Catégories de livres personnalisées pour les livres électroniques achetés dans le cadre du programme d’achat en volume (VPP) <!-- 1488911 -->
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

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Améliorations apportées au langage utilisé dans l’application Portail d’entreprise pour Windows <!-- 1683758 -->
Nous avons amélioré le langage utilisé dans le Portail d’entreprise pour Windows 10 pour qu’il soit plus convivial et plus spécifique à votre entreprise. Pour voir nos exemples d’images, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Derniers ajouts à notre documentation sur la confidentialité des utilisateurs <!-- 1440709 -->
Dans le cadre de nos efforts pour donner aux utilisateurs finaux un plus grand contrôle sur la confidentialité de leurs données, nous avons publié des mises à jour de notre documentation expliquant comment afficher et supprimer les données stockées localement par les applications du Portail d’entreprise. Vous pouvez trouver ces mises à jour aux emplacements suivants :

- **Android** : [Guide pratique pour supprimer un appareil Android d’Intune](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, si l’utilisateur a refusé les conditions d’utilisation** : [Guide pratique pour supprimer la gestion de votre appareil si vous avez refusé les « Conditions d’utilisation »](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS** : [Guide pratique pour supprimer votre appareil iOS d’Intune](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows** : [Guide pratique pour supprimer votre appareil Windows d’Intune](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>Février 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Prise en charge de plusieurs comptes DEP/Apple School Manager par Intune <!-- 747685 -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du [Programme d’inscription des appareils (DEP)](device-enrollment-program-enroll-ios.md) ou [Apple School Manager](apple-school-manager-set-up-ios.md). Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Afficher les restrictions d’inscription par utilisateur <!-- 1634444 eeready wnready -->
Le panneau **Résoudre les problèmes** vous permet désormais de voir les [restrictions d’inscription](enrollment-restrictions-set.md) en vigueur pour chaque utilisateur. Pour cela, sélectionnez **Restrictions d’inscription** dans la liste **Affectations**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nouvelle option pour l’authentification utilisateur dans le cadre de l’inscription en bloc Apple <!-- 747625 eeready -->

> [!NOTE]
> Les nouveaux locataires la verront tout de suite. Pour les locataires existants, cette fonctionnalité sera déployée en avril. Tant que ce déploiement ne sera pas terminé, vous n’aurez peut-être pas accès à ces nouvelles fonctionnalités.

Intune vous donne maintenant la possibilité d’authentifier les appareils à l’aide de l’application Portail d’entreprise pour les méthodes d’inscription suivantes :

- Programme d'inscription d'appareils Apple
- Apple School Manager
- Inscription à Apple Configurator

Lorsque vous utilisez l’option Portail d’entreprise, l’authentification multifacteur Azure Active Directory peut être appliquée sans bloquer ces méthodes d’inscription.

Lorsque vous utilisez l’option Portail d’entreprise, Intune ignore l’authentification utilisateur dans l’Assistant Réglages iOS pour l’inscription d’affinité utilisateur. Cela signifie que l’appareil est initialement inscrit comme appareil sans utilisateur et, par conséquent, vous ne recevez pas les configurations ou stratégies des groupes d’utilisateurs. Il reçoit uniquement les configurations et les stratégies des groupes d’appareils. Toutefois, Intune installera automatiquement l’application Portail d’entreprise sur l’appareil. Le premier utilisateur à lancer l’application Portail d’entreprise et à s’y connecter sera associé à l’appareil dans Intune. À ce stade, l’utilisateur reçoit les configurations et les stratégies de ses groupes d’utilisateurs. L’association de l’utilisateur ne peut pas être modifiée sans réinscription.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Prise en charge de plusieurs comptes DEP/Apple School Manager par Intune <!-- 747685 eeready -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du Programme d’inscription des appareils (DEP) ou Apple School Manager. Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impression à distance sur un réseau sécurisé <!-- 1709994  -->
Les solutions d’impression mobiles sans fil PrinterOn permettront aux utilisateurs d’imprimer à distance depuis n’importe où et à tout moment via un réseau sécurisé. PrinterOn s’intégrera au Kit SDK APP d’Intune à la fois pour iOS et Android. Vous pourrez cibler les stratégies de protection d’application pour cette application via le panneau des **stratégies de protection d’application** d’Intune, dans la console d’administration. Les utilisateurs finaux pourront télécharger l’application « PrinterOn for Microsoft » via le Google Play Store ou iTunes afin de l’utiliser dans leur écosystème Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Prise en charge du Portail d’entreprise macOS pour les inscriptions qui utilisent le gestionnaire d’inscription d’appareil <!-- 1352411 -->

Les utilisateurs peuvent désormais utiliser le Gestionnaire d’inscription d’appareil durant l’inscription auprès du portail d’entreprise macOS.

### <a name="device-management"></a>Gestion des appareils

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Rapports sur l’état de menace et d’intégrité de Windows Defender <!--854704 -->

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

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>Nouveaux paramètres pour le navigateur Microsoft Edge <!--1469166 -->
[Deux nouveaux paramètres](device-restrictions-windows-10.md#microsoft-edge-browser) sont désormais disponibles pour les appareils avec le navigateur Microsoft Edge : **Chemin vers le fichier de favoris** et **Modifications des favoris**.

### <a name="app-management"></a>Gestion d'applications

#### <a name="protocol-exceptions-for-applications---1035509---"></a>Exceptions de protocoles pour les applications <!--1035509 -->

Vous pouvez à présent créer des exceptions à la stratégie de transfert de données de gestion des applications mobiles (MAM) Intune pour ouvrir des applications non gérées spécifiques. De telles applications doivent être approuvées par le service informatique. Hormis les exceptions que vous créez, le transfert de données est toujours limité aux applications qui sont gérées par Intune quand votre stratégie de transfert de données est définie pour les **applications gérées uniquement**. Vous pouvez créer les restrictions à l’aide de protocoles (iOS) ou de packages (Android).

Par exemple, vous pouvez ajouter le package Webex en tant qu’exception à la stratégie de transfert de données MAM. Cela permet d’ouvrir les liens Webex dans un e-mail Outlook géré directement dans l’application Webex. Le transfert de données sera toujours limité dans d’autres applications non gérées. Pour plus d’informations, consultez [Exceptions de la stratégie de transfert de données pour les applications](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Données chiffrées par la Protection des informations Windows (WIP) dans les résultats de la recherche Windows <!-- 1469193 -->
La stratégie Protection des informations Windows comprend désormais un paramètre vous permettant d’inclure ou non les données chiffrées par cette stratégie dans les résultats de la recherche Windows. Pour définir cette option de stratégie de protection d’application, sélectionnez **Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés** dans les **Paramètres avancés** de la stratégie Protection des informations Windows. La stratégie de protection d’application doit être définie pour la plateforme *Windows 10* et **l’état de l’inscription** de la stratégie d’application doit indiquer **Avec inscription**. Pour plus d’informations, consultez [Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configuration d’une application MSI mobile avec mise à jour automatique <!-- 1740840 -->
Vous pouvez configurer une application MSI mobile connue avec mise à jour automatique pour ignorer le processus de vérification de version. Cette fonctionnalité est utile pour éviter d’introduire une condition de concurrence. Une condition de concurrence peut notamment se produire quand l’application est mise à jour automatiquement par le développeur de l’application et aussi par Intune. Les deux peuvent essayer d’appliquer une version de l’application sur un client Windows, générant ainsi un conflit. Pour ces applications MSI mises à jour automatiquement, vous pouvez configurer le paramètre **Ignorer la version de l’application** dans le panneau **Informations sur l’application**. Quand vous basculez ce paramètre sur **Oui**, Microsoft Intune ignore la version de l’application installée sur le client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Ensembles liés de licences d’application pris en charge par Intune <!-- 1864117 -->
Dans le portail Azure, Intune prend désormais en charge les jeux liés de licences d’application comme élément d’application unique dans l’interface utilisateur. En outre, toutes les applications sous licence en mode hors connexion synchronisées à partir de Microsoft Store pour Entreprises seront consolidées dans une entrée d’application unique et les détails du déploiement des packages individuels seront migrés sur l’entrée unique. Pour voir les ensembles de licences d’application associés dans le portail Azure, sélectionnez **Licences d’application** dans le panneau **Applications clientes**.

### <a name="device-configuration"></a>Configuration des appareils
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Extensions de fichier WIP (Windows Information Protection) pour le chiffrement automatique <!-- 1463582 -->
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

### <a name="intune-apps"></a>Applications Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises <!--1222672-->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications hors connexion sont installées par Intune et non pas par le Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes du profil professionnel <!-- 1728700 -->

Quand vous déployez l’application Gmail dans un profil Android for Work, vous pouvez désormais empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel à l’aide du paramètre **Ajouter et supprimer des comptes** du profil de restrictions d’appareil Android for Work.

<!-- ########################## -->
## <a name="january-2018"></a>Janvier 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertes relatives aux jetons expirés et les jetons qui arrivent à expiration <!-- 1639263 -->
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

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Attribuer des applications mobiles Office 365 aux appareils iOS et Android à l’aide du type d’application intégré <!-- 1332318 -->
Le type d’application **Intégré** facilite la création d’applications Office 365 et leur affectation aux appareils iOS et Android gérés. Ces applications incluent les applications Office 365 telles que Word, Excel, PowerPoint et OneDrive. Vous pouvez affecter des applications spécifiques au type d’application et modifier la configuration des informations des applications.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusion et exclusion d’affectations d’applications en fonction des groupes <!-- 1406920 -->

Pendant l’affectation d’une application et après avoir sélectionné un type d’affectation, vous pouvez sélectionner les groupes à inclure et ceux à exclure.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Vous pouvez attribuer une stratégie de configuration d’application à des groupes en incluant et excluant des affectations  <!-- 1480316 -->

Vous pouvez attribuer une stratégie de configuration d’application à un groupe d’utilisateurs et d’appareils à l’aide d’une combinaison d’affectations d’inclusion et d’exclusion. Les affectations peuvent être choisies sous la forme d’une sélection personnalisée de groupes ou d’un groupe virtuel. Un groupe virtuel peut être notamment **Tous les utilisateurs**, **Tous les appareils** ou **Tous les utilisateurs + Tous les appareils**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Prise en charge de la stratégie de mise à niveau de l’édition Windows 10   <!-- 903672(archived), 1119689 -->  
Vous pouvez créer une stratégie de mise à niveau d’édition Windows 10 qui met à niveau les appareils Windows 10 vers Windows 10 Éducation, Windows 10 Éducation N, Windows 10 Professionnel, Windows 10 Professionnel N, Windows 10 Professionnel Éducation et Windows 10 Professionnel Éducation N. Pour plus d’informations sur les mises à niveau d’édition Windows 10, consultez [Guide pratique pour configurer les mises à niveau d’édition Windows 10 ](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Les stratégies d’accès conditionnel pour Intune sont disponibles uniquement à partir du Portail Azure  <!-- 1737088 1634311 -->

À partir de cette version, vous pouvez configurer et gérer vos stratégies d’accès conditionnel dans le [portail Azure](https://portal.azure.com) en accédant à **Azure Active Directory** > **Accès conditionnel**. Pour des raisons pratiques, vous pouvez également accéder à ce panneau à partir d’Intune dans le portail Azure, depuis **Intune** > **Accès conditionnel**.

#### <a name="updates-to-compliance-emails---1637547---"></a>E-mails de mises à jour de conformité <!--1637547 -->

Quand un e-mail est envoyé pour signaler un appareil non conforme, des informations sur cet appareil non conforme sont ajoutées.

### <a name="intune-apps"></a>Applications Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nouvelles fonctionnalités de l’action « Résoudre » pour les appareils Android <!--1583480-->

L’application Portail d’entreprise pour Android étend l’action « Résoudre » sur **Mettre à jour les paramètres d’appareil** afin de résoudre les [problèmes de chiffrement d’appareil](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Verrouillage à distance disponible dans l’application Portail d’entreprise pour Windows 10 <!--676506-->
Les utilisateurs finaux peuvent désormais verrouiller à distance leurs appareils à partir de l’application Portail d’entreprise pour Windows 10. Cela ne s’affichera pas pour l’appareil local qu’ils utilisent de manière active.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Simplification de la résolution des problèmes de conformité affectant l’application Portail d’entreprise pour Windows 10 <!--676546-->
Les utilisateurs finaux d’appareils Windows peuvent choisir la raison de la non-conformité dans l’application Portail d’entreprise. Quand c’est possible, ils sont directement positionnés à l’emplacement approprié dans l’application Paramètres pour corriger le problème.

<!-- ########################## -->
## <a name="december-2017"></a>Décembre 2017

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nouveau paramètre de redéploiement automatique <!-- 1469168 -->
Le paramètre **Redéploiement automatique** permet aux utilisateurs avec des droits d’administration de supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **Ctrl+Win+R** sur l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion. Ce paramètre se trouve sous Windows 10 -> Restrictions sur l’appareil -> Général -> Redéploiement automatique. Pour plus d’informations, consultez [Paramètres de restriction d’appareil Intune pour Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Prise en charge d’éditions source supplémentaires dans la stratégie de mise à niveau de l’édition Windows 10  <!-- 903672,  1119689 -->
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

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Le nom d’objet du client peut utiliser la variable AAD_DEVICE_ID  <!-- 1468599 -->

Lorsque vous créez un profil de certificat SCEP dans Intune, vous pouvez désormais utiliser la variable AAD_DEVICE_ID lorsque vous générez le nom d’objet du client.   Lorsque le certificat est demandé à l’aide de ce profil SCEP, la variable est remplacée par l’ID AAD de l’appareil qui effectue la demande de certificat.


### <a name="device-management"></a>Gestion des appareils

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gérer les appareils macOS inscrits auprès de Jamf avec le moteur de conformité des appareils d’Intune <!-- 1592747 -->
Vous pouvez utiliser Jamf pour envoyer des informations sur l’état des appareils macOS à Intune, qui évaluera alors la conformité avec les stratégies définies dans la console Intune. En fonction de cet état et d’autres conditions (notamment, l’emplacement, les risques de l’utilisateur, etc.), l’accès conditionnel appliquera des stratégies de conformité aux appareils macOS qui accèdent aux applications cloud et locales reliées à Azure AD, y compris Office 365. En savoir plus sur la [configuration de l’intégration de Jamf](conditional-access-integrate-jamf.md) et la [mise en application de la conformité des appareils Jamf gérés](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nouvelle action d’appareil iOS   <!-- 1424701 -->

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

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Une nouvelle collection d’entités nommée Utilisateur actuel se limite aux données des utilisateurs actuellement actifs <!-- 1667026 -->

La collecte d’entités **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

En revanche, la nouvelle collection d’entités **Utilisateur actuel** contient uniquement les utilisateurs qui n’ont pas été supprimés. La collection d'entités **Utilisateur actuel** ne contient que des utilisateurs actuellement actifs. Pour plus d’informations sur la collection d’entités **Utilisateur actuel**, consultez la page [Informations de référence sur l’entité Utilisateur actuel](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>API Graph mises à jour <!-- 1736360 -->

Dans cette version, nous avons mis à jour quelques-unes des API Graph pour Intune (actuellement en version bêta). Consultez le [journal mensuel des modifications de l’API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) pour plus d’informations.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune prend en charge les applications refusées par la Protection des informations Windows <!-- 1479103 -->
Vous pouvez spécifier les applications refusées dans Intune. Si une application est refusée, son accès aux informations d’entreprise est bloqué (ce qui correspond à l’inverse de la liste des applications autorisées). Pour plus d’informations, consultez [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Liste d’exclusion recommandée pour la Protection des informations Windows).

<!-- ########################## -->
## <a name="november-2017"></a>Novembre 2017

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Résoudre les problèmes d’inscription  <!-- 746324 -->

L’espace de travail **Résolution des problèmes** montre désormais les problèmes d’inscription des utilisateurs. Des détails sur les problèmes et des suggestions de correction peuvent aider les administrateurs et les agents du support technique à résoudre les problèmes. Certains problèmes d’inscription ne sont pas capturés et certaines erreurs peuvent ne pas avoir de suggestions de correction.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrictions d’inscription assignées aux groupes <!-- 747598 -->

En tant qu’administrateur Intune, vous pouvez désormais [créer des restrictions d’inscription Type d’appareil et Limite d’appareils personnalisées pour des groupes d’utilisateurs](enrollment-restrictions-set.md).

Le portail Azure Intune vous permet de créer jusqu’à 25 instances de chaque type de restriction qui peuvent ensuite être assignées aux groupes d’utilisateurs. Les restrictions assignées aux groupes remplacent les restrictions par défaut.

Toutes les instances d’un type de restriction sont conservées dans une liste classée de manière stricte. Cet ordre définit une valeur de priorité pour la résolution des conflits. Un utilisateur impacté par plusieurs instances de restriction est uniquement limité par l’instance ayant la valeur de priorité la plus élevée. Vous pouvez modifier la priorité d’une instance donnée en la faisant glisser vers un autre emplacement de la liste.

Cette fonctionnalité sera disponible quand les paramètres Android for Work seront migrés depuis le menu Inscription Android for Work vers le menu Restrictions d’inscription. Cette migration pouvant prendre plusieurs jours, votre compte peut être mis à niveau pour d’autres parties de la version de novembre avant que l’affectation aux groupes ne soit activée pour les restrictions d’inscription.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Prise en charge de plusieurs connecteurs NDES (Service d’inscription de périphérique réseau) <!-- 1528104 -->

NDES permet aux appareils mobiles s’exécutant sans informations d’identification de domaine d’obtenir des certificats basés sur le protocole d’inscription de certificats simple (SCEP).
Cette mise à jour prend en charge plusieurs connecteurs NDES.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gérer les appareils Android for Work indépendamment des appareils Android <!-- 1490731 EEready-->

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

### <a name="google-play-protect-support-on-android----908720---"></a>Prise en charge de Google Play Protect sur Android <!-- 908720 -->

Avec la publication d’Android Oreo, Google introduit une suite de fonctionnalités de sécurité appelée Google Play Protect qui permet aux utilisateurs et aux organisations d’exécuter des applications sécurisées et des images Android sécurisées. Intune prend maintenant en charge les fonctionnalités de Google Play Protect, notamment l’attestation SafetyNet distante. Les administrateurs peuvent définir des critères de stratégie de conformité pour que Google Play Protect soit configuré et sain.
Le paramètre **Attestation d’appareil SafetyNet** nécessite que l’appareil se connecte à un service Google pour vérifier que l’appareil est intègre et qu’il n’est pas compromis. Les administrateurs peuvent également définir un paramètre de profil de configuration pour qu’Android for Work exige que les applications installées soient vérifiées par les services Google Play. Si un appareil n’est pas conforme aux exigences de Google Play Protect, l’accès conditionnel peut empêcher les utilisateurs d’accéder aux ressources de l’entreprise.

- Découvrez comment [créer une stratégie de conformité des appareils pour activer Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-android).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocole de texte autorisé depuis des applications gérées <!-- 1414050  -->

Les applications gérées par le SDK d’application Intune peuvent envoyer des SMS.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Mise à jour du rapport d’installation de l’application pour inclure l’état Installation en attente <!-- 1249446 -->  

Le rapport **État de l’installation de l’application** accessible pour chaque application via la liste **Application** dans la charge de travail **Applications clientes** contient désormais un comptage **Installation en attente** pour les utilisateurs et les appareils.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API d’inventaire des applications iOS 11 pour la détection de menaces mobiles <!-- 1391759 -->

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

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Faire migrer des utilisateurs et appareils MDM hybrides vers la version autonome d’Intune <!-- 1463747 wnready -->
De nouveaux processus et de nouveaux outils sont maintenant disponibles pour déplacer les utilisateurs et leurs appareils de MDM hybride vers Intune dans le portail Azure. Vous pouvez ainsi effectuer les tâches suivantes :
- Copier des stratégies et des profils de la console Configuration Manager vers Intune dans le portail Azure
- Déplacer une partie des utilisateurs vers Intune dans le portail Azure, tout en conservant le reste dans un environnement MDM hybride
- Migrer des appareils vers Intune dans le portail Azure sans avoir à les réinscrire

Pour plus d’informations, consultez [Faire migrer des utilisateurs et appareils MDM hybrides vers la version autonome d’Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local  <!-- 676614 -->
Une fois que le connecteur Exchange crée une connexion à Exchange en utilisant l’autorité de certification spécifiée, le connecteur a désormais la possibilité de découverte d’autres autorités de certification. Si l’autorité de certification principale est indisponible, le connecteur bascule vers une autre autorité de certification disponible, jusqu'à ce que l’autorité de certification principale redevienne disponible. Pour plus de détails, voir [Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Redémarrer un appareil iOS à distance (supervisé uniquement) <!-- 1424595 -->

Vous pouvez désormais déclencher le redémarrage d’un appareil iOS 10.3+ supervisé au moyen d’une action d’appareil. Pour plus d’informations sur l’utilisation de l’action de redémarrage d’appareil, consultez [Redémarrer à distance des appareils avec Intune](device-restart.md).

> [!Note]
> Cette commande nécessite un appareil supervisé et le droit d’accès **Verrouillage de l’appareil**. L’appareil redémarre immédiatement. Après le redémarrage, les appareils iOS verrouillés par un code secret ne rejoignent pas un réseau Wi-Fi et peuvent se trouver dans l’impossibilité de communiquer avec le serveur.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Prise en charge de l’authentification unique pour iOS <!-- 1333645 -->  

Vous pouvez utiliser l’authentification unique pour les utilisateurs d’iOS. Les applications iOS qui sont codées pour rechercher les informations d’identification de l’utilisateur dans la charge utile d’authentification unique fonctionnent avec cette mise à jour de la configuration de la charge utile. Vous pouvez également utiliser un UPN et un ID d’appareil Intune pour configurer le nom du principal et le domaine. Pour plus d’informations, consultez [Configurer Intune pour l’authentification unique des appareils iOS](sso-ios.md).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Ajouter « Rechercher mon iPhone » pour les appareils personnels <!--1427287-->
Vous pouvez désormais savoir si la fonctionnalité Verrou d’activation est activée pour les appareils iOS. Cette fonctionnalité se trouvait avant dans le portail classique.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Verrouiller un appareil macOS géré à distance à l’aide d’Intune <!-- 1437691 -->

Vous pouvez verrouiller un appareil macOS perdu et définir un code PIN de récupération à 6 chiffres. Une fois le verrouillage effectué, le panneau **Vue d’ensemble des appareils** affiche le code PIN jusqu’à ce qu’une autre action d’appareil soit envoyée.

Pour plus d’informations, consultez [Verrouiller à distance des appareils gérés avec Intune](device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Nouveaux détails de profil SCEP pris en charge <!-- 1559808 -->

Les administrateurs peuvent désormais définir des paramètres supplémentaires durant la création d’un profil SCEP sur les plateformes Windows, iOS, macOS et Android.  Les administrateurs peuvent définir un IMEI, un numéro de série ou un nom commun (adresse e-mail incluse) dans le format du nom de l’objet.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Conserver les données lors d’une réinitialisation des paramètres d’usine  <!--1588489 -->
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


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Les affectations d’anneau de mise à jour de Windows 10 sont affichées <!-- 1621837 -->
Pendant une **résolution de problèmes**, vous pouvez voir les affectations de boucles de mise à jour de Windows 10 pour l’utilisateur affiché.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Paramètres de la fréquence d’émission des rapports Windows Defender Advanced Threat Protection (Protection avancée contre les menaces)  <!-- 1455974  -->
Le service Windows Defender - Protection avancée contre les menaces permet aux administrateurs de gérer la fréquence d’émission des rapports sur les appareils gérés. Avec la nouvelle option **Augmenter la fréquence des rapports de télémétrie**, Windows Defender ATP collecte les données et évalue les risques plus fréquemment. Par défaut, l’émission de rapports optimise le niveau de performance et la vitesse. Augmenter la fréquence d’émission des rapports peut être utile pour les appareils à haut risque. Ce paramètre se trouve dans le profil **Windows Defender ATP** dans **Configurations d’appareil**.

### <a name="audit-updates----1412961---"></a>Auditer les mises à jour <!-- 1412961 -->  
La fonctionnalité d’audit d’Intune enregistre les opérations de modification relatives à Intune.  Tous les opérations de création, de mise à jour, de suppression et de tâche à distance sont capturées et conservées pendant un an.  Le portail Azure fournit une vue filtrable des 30 derniers jours de données d’audit dans chaque charge de travail.  Une API Graph correspondante permet de récupérer les données d’audit stockées pendant l’année écoulée.

La fonctionnalité d’audit se trouve sous le groupe **SURVEILLER**. Il existe un élément de menu **Journaux d’audit** par charge de travail.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>L’application Portail d’entreprise pour macOS est disponible <!--1541700-->
L’expérience du Portail d’entreprise Intune sous macOS a été mise à jour. Elle a été optimisée pour afficher clairement toutes les informations et notifications de conformité dont les utilisateurs ont besoin pour tous les appareils qu’ils ont inscrits. Une fois que le Portail d’entreprise Intune a été déployé sur un appareil, il bénéficie de la mise à jour automatique Microsoft (AutoUpdate) pour macOS. Vous pouvez télécharger le nouveau Portail d’entreprise Intune pour macOS en ouvrant une session sur le site web du Portail d’entreprise Intune sur un appareil macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner fait maintenant partie de la liste des applications approuvées par la gestion des applications mobiles (GAM)  <!-- 1248473 -->
L’application Microsoft Planner pour iOS et Android fait à présent partie des applications approuvées pour la gestion des applications mobiles (MAM). Elle est configurable par le biais du panneau Intune App Protection sur le Portail Azure de tous les clients.
- Pour plus de détails, consultez la page [Liste MAM des applications approuvées](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Fréquence de mise à jour des exigences du VPN par application sur les appareils iOS   <!-- 1547061 -->  
Les administrateurs peuvent à présent supprimer des exigences du VPN par application pour les applications installées sur des appareils iOS ; les appareils concernés seront mis à jour après l’archivage Intune suivant, ce qui se produit généralement dans les 15 minutes.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Prise en charge du pack d’administration d’Operations Manager pour le connecteur Exchange <!-- 885457 -->
Le pack d’administration de System Center Operations Manager pour le connecteur Exchange est maintenant disponible pour vous aider à analyser les journaux du connecteur Exchange. Cette fonctionnalité offre différents moyens de surveiller le service à des fins de résolution des problèmes.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestion pour les appareils Windows 10  <!-- 1243445 -->
La cogestion est une solution qui propose une passerelle entre la gestion classique et la gestion moderne tout en vous donnant la possibilité d’opérer cette transition selon une approche en plusieurs phases. À la base, la cogestion est une solution qui permet aux appareils Windows 10 d’être gérés simultanément par Configuration Manager et Microsoft Intune, et d’être joints à Active Directory (AD) et à Azure Active Directory (Azure AD).  Cette configuration vous offre un moyen de vous moderniser à un rythme qui convient à votre organisation si vous ne pouvez pas le faire d’un coup.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Limiter l’inscription via Windows en fonction des versions de système d’exploitation <!-- 245498 -->
En tant qu’administrateur Intune, vous pouvez maintenant spécifier une version minimale et maximale de Windows 10 pour les inscriptions d’appareils. Vous pouvez définir ces restrictions dans le panneau **Configurations de plateforme**.

Intune continue à prendre en charge l’inscription des PC et téléphones Windows 8.1. Toutefois, seules les versions de Windows 10 peuvent être configurées avec des limites minimale et maximale. Pour autoriser l’inscription d’appareils 8.1, laissez vide la limite minimale.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertes relatives aux appareils Windows Autopilot non affectés  <!-- 1631236 -->
Une nouvelle alerte est disponible pour les appareils non attribués Windows AutoPilot dans la page **Microsoft Intune** > **Inscription de l’appareil** > **Vue d’ensemble**. Cette alerte indique combien d’appareils du programme AutoPilot n’ont pas de profils de déploiement AutoPilot affectés. Utilisez les informations de l’alerte pour créer des profils et les affecter aux appareils non affectés. Quand vous cliquez sur l’alerte, une liste complète des appareils Windows AutoPilot et des informations détaillées les concernant s’affichent. Pour plus d’informations, consultez [Inscrire des appareils Windows à l’aide du programme de déploiement Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot).


### <a name="refresh-button-for-devices-list-------1333581---"></a>Bouton Actualiser pour la liste des appareils    <!-- 1333581 -->
La liste des appareils ne s’actualisant pas automatiquement, vous pouvez utiliser le bouton Actualiser pour mettre à jour les appareils affichés dans la liste.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Prise en charge de l’Autorité de certification Symantec Cloud  <!-- 1333638 -->    
Intune prend désormais en charge l’Autorité de certification Symantec Cloud qui permet à Intune Certificate Connector d’émettre des certificats PKCS de l’Autorité de certification Symantec Cloud sur des appareils gérés par Intune. Si vous utilisez déjà Intune Certificate Connector avec l’Autorité de certification Microsoft, vous pouvez utiliser la configuration existante d’Intune Certificate Connector en y ajoutant la prise en charge de l’Autorité de certification de Symantec.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nouveaux éléments ajoutés à l’inventaire des appareils   <!--1404455 -->
Les nouveaux éléments suivants sont maintenant disponibles dans [l’inventaire effectué par les appareils inscrits](device-inventory.md) :

- Adresse MAC Wi-Fi
- Espace de stockage total
- Espace libre total
- MEID
- Opérateur de l’abonné

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Définir l’accès pour les applications avec un correctif de sécurité Android minimal sur l’appareil<!-- 1278463 -->   
Un administrateur peut définir le correctif de sécurité Android minimal qui doit être installé sur l’appareil pour obtenir l’accès à une application gérée sous un compte géré.

> [!Note]  
> Cette fonctionnalité restreint uniquement les correctifs de sécurité publiés par Google sur les appareils Android 6.0 +.

### <a name="app-conditional-launch-support----1193313---"></a>Prise en charge du lancement conditionnel d’applications <!-- 1193313 -->
Les administrateurs informatiques peuvent désormais définir une condition dans le portail d’administration Azure permettant d’appliquer un code secret à la place d’un code PIN numérique via la gestion des applications mobiles (MAM) lors du lancement de l’application. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Cette version d’Intune propose cette fonctionnalité **sur iOS uniquement**. Intune prend en charge un code secret comme un code PIN numérique, il définit une longueur minimale et autorise la répétition des caractères et des séquences. Cette fonctionnalité nécessite la participation des applications (c’est-à-dire, WXP, Outlook, Managed Browser, Yammer) pour intégrer le kit SDK Intune App avec le code de cette fonctionnalité en place dans le but d’appliquer les paramètres du code secret dans les applications ciblées.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numéro de version des applications métier dans le rapport d’état d’installation de l’appareil <!-- 1233999 -->
Avec cette version, le rapport d’état d’installation de l’appareil affiche le numéro de version des applications métier pour iOS et Android. Vous pouvez utiliser cette information pour dépanner vos applications ou trouver les appareils qui exécutent des versions d’application anciennes.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Les administrateurs peuvent désormais configurer les paramètres du pare-feu d’un appareil à l’aide d’un profil de configuration d’appareil <!-- 951708 -->   
Les administrateurs peuvent activer le Pare-feu sur les appareils et configurer divers protocoles pour les réseaux privés, publics et de domaine.  Ces paramètres de pare-feu se trouvent dans le profil « Endpoint protection ».

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard permet de protéger les appareils des sites web non approuvés, comme défini par votre organisation <!-- 958257 -->   
Les administrateurs peuvent définir les sites comme « approuvés » ou « appartenant à l’entreprise » à l’aide d’un flux de travail Protection des informations Windows ou du nouveau profil « Limite réseau » dans les configurations de l’appareil. S’ils sont consultés dans Microsoft Edge, les sites qui ne sont pas listés dans la limite réseau approuvée d’un appareil Windows 10 64 bits s’ouvrent à la place dans un navigateur d’une machine virtuelle Hyper-V.

Application Guard se trouve dans les profils de configuration de l’appareil, dans le profil « Endpoint protection ». À partir de là, les administrateurs peuvent configurer une interaction entre le navigateur virtualisé et la machine hôte, les sites non approuvés et les sites approuvés, puis stocker les données générées dans le navigateur virtualisé. Pour utiliser Application Guard sur un appareil, une limite réseau doit d’abord être configurée. Il est important de définir une seule limite réseau pour un appareil.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Control sur Windows 10 Entreprise offre un mode permettant de faire uniquement confiance aux applications autorisées <!-- 1031096 -->    
Avec des milliers de nouveaux fichiers malveillants créés chaque jour, l’utilisation d’une détection antivirus basée sur les signatures pour lutter contre les programmes malveillants ne constitue probablement plus une défense suffisante contre les nouvelles attaques. En utilisant Windows Defender Application Control sur Windows 10 Entreprise, vous pouvez changer la configuration de l’appareil et passer d’un mode où les applications sont approuvées sauf si elles sont bloquées par un antivirus ou une autre solution de sécurité à un mode où le système d’exploitation approuve uniquement les applications autorisées par votre entreprise. Vous approuvez les applications dans Windows Defender Application Control.

Avec Intune, vous pouvez configurer des stratégies de contrôle d’application en mode « audit uniquement » ou en mode d’application. Les applications ne sont pas bloquées quand vous exécutez le mode « audit uniquement ». Le mode « Audit uniquement » enregistre tous les événements dans les journaux du client local. Vous pouvez également autoriser uniquement l’exécution des composants Windows et des applications du Microsoft Store, ou autoriser l’exécution d’autres applications avec une bonne réputation telle que définie par Intelligent Security Graph.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard constitue un nouvel ensemble de fonctionnalités de prévention d’intrusion pour Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard propose des règles personnalisées permettant de réduire l’exploitabilité des applications, empêche les menaces provenant de macros et de scripts, bloque automatiquement les connexions réseau à des adresses IP de mauvaise réputation et peut sécuriser les données contre des ransomware et des menaces inconnues. Windows Defender Exploit Guard présente les composants suivants :

- **Réduction de la surface d’attaque** fournit des règles vous permettant d’empêcher les menaces liées aux macros, aux scripts et aux e-mails.
- **Accès contrôlé au dossier** bloque automatiquement l’accès au contenu des dossiers protégés.
- **Filtre de réseau** bloque la connexion sortante de toutes les applications à une adresse IP/domaine de faible réputation
- **Exploit Protection** fournit la mémoire, le flux de contrôle et les restrictions de stratégie pouvant être utilisés pour protéger les applications contre des attaques.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gérer des scripts PowerShell dans Intune pour des appareils Windows 10 <!-- 790537 -->

L’extension de gestion Intune vous permet de charger des scripts PowerShell dans Intune pour les exécuter sur des appareils Windows 10. L’extension vient en complément des fonctionnalités de gestion des appareils mobiles (MDM) Windows 10 et facilite l’adoption d’une gestion moderne. Pour plus d’informations, consultez [Gérer des scripts PowerShell dans Intune pour des appareils Windows 10](intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10      <!-- 1308850 -->
-    Messagerie (mobile uniquement) - désactivation des tests ou des messages MMS
-    Mot de passe - paramètres pour activer FIPS et l’utilisation d’appareils secondaires Windows Hello pour l’authentification 
-    Affichage - paramètres pour activer ou désactiver la mise à l’échelle GDI pour les applications héritées

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrictions des appareils en mode plein écran sur Windows 10 <!-- 1308872 -->   
Vous pouvez restreindre les utilisateurs d’appareils Windows 10 au mode plein écran, ce qui limite les utilisateurs à un ensemble d’applications prédéfinies.  Pour ce faire, créez un profil de restriction d’appareil Windows 10 et définissez les paramètres de plein écran.

Le mode plein écran prend en charge deux modes : **application unique** (permet à l’utilisateur d’exécuter une seule application) ou **applications multiples** (permet l’accès à un ensemble d’applications).  Vous définissez le compte d’utilisateur et le nom de l’appareil, ce qui détermine les applications prises en charge.  Lorsque l’utilisateur est connecté, il est limité aux applications définies.  Pour en savoir plus, consultez [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Conditions requises du mode plein écran :

- Intune doit être l’autorité MDM.
- Les applications doivent déjà être installées sur l’appareil cible.
- L’appareil doit être [correctement provisionné](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nouveau profil de configuration d’appareil pour créer des limites réseau <!-- 1311967 -->   
Vous trouverez un nouveau profil de configuration d’appareil appelé **Limite réseau** avec vos autres profils de configuration d’appareil. Utilisez ce profil pour définir des ressources en ligne à considérer comme approuvées et appartenant à l’entreprise. Vous devez définir une limite réseau pour un appareil *avant* de pouvoir utiliser les fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows sur l’appareil. Il est important de définir une seule limite réseau pour chaque appareil.

Vous pouvez définir des ressources cloud d’entreprise, des plages d’adresses IP et des serveurs proxy internes à considérer comme approuvées. Une fois définie, la limite réseau peut être utilisée par d’autres fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Deux paramètres supplémentaires de l’antivirus Windows Defender <!-- 1338409 -->  
**Niveau de blocage des fichiers**

| | |
|---|---|
| non configuré | **Non configuré** utilise le niveau de blocage de Windows Defender Antivirus par défaut et offre une détection solide sans augmenter le risque de détection des fichiers légitimes. |
| Importante | **Haut** s’applique à un niveau fort de détection.
| Élevé +  | **Haut +** fournit le niveau Haut avec des mesures de protection supplémentaires pouvant impacter les performances du client.
| Tolérance zéro  | **Tolérance zéro** bloque tous les exécutables inconnus. |

Bien qu’improbable, la définition sur **Haut** risque d’entraîner la détection de certains fichiers légitimes.
Nous vous recommandons de définir le niveau de blocage des fichiers avec la valeur par défaut, **Non configuré**.

**Extension du délai d’attente pour l’analyse des fichiers par le cloud**  

| | |
|--|--|
| Nombre de secondes (0-50) | Spécifiez la durée maximale avant que Windows Defender Antivirus ne bloque un fichier lors de l’attente d’un résultat du cloud. La durée par défaut est de 10 secondes : tout temps supplémentaire spécifié ici (jusqu'à 50 secondes) est ajouté à ces 10 secondes. Dans la plupart des cas, l’analyse prend beaucoup moins de temps que la valeur maximale. Prolonger la durée permet au cloud de rechercher des fichiers suspects de manière plus approfondie. Nous vous recommandons d’activer ce paramètre et de spécifier au moins 20 secondes supplémentaires. |

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix ajouté aux appareils Windows 10 <!-- 1512457 -->  
Vous pouvez configurer un VPN Citrix pour les appareils Windows 10. Vous pouvez choisir le VPN Citrix dans la liste *Sélectionner un type de connexion* du panneau **VPN de base** quand vous configurez un VPN pour Windows 10 et ultérieur.

> [!Note]
> Une configuration de Citrix existait pour iOS et Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Les connexions Wi-Fi prennent en charge les clés prépartagées sur iOS <!-- 1550823 -->
Les clients peuvent configurer des profils Wi-Fi pour utiliser des clés prépartagées pour les connexions personnelles WPA/WPA2 sur les appareils iOS. Ces profils sont envoyés à l’appareil de l’utilisateur quand l’appareil est inscrit dans Intune.

Quand le profil a été envoyé à l’appareil, l’étape suivante varie en fonction de la configuration du profil.  S’il est configuré pour se connecter automatiquement, il le fait quand l’accès réseau est nécessaire.  Quand le profil se connecte manuellement, l’utilisateur doit activer la connexion manuellement.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Accès aux journaux d’applications gérées pour iOS <!-- 1469920 -->
Les utilisateurs finaux disposant de Managed Browser peuvent désormais afficher l’état de gestion de toutes les applications Microsoft publiées, et envoyer les journaux afin de dépannage leurs applications iOS gérées.

Pour découvrir comment activer le mode de dépannage dans Managed Browser sur un appareil iOS, consultez [Comment accéder aux journaux des applications gérées à l’aide de Managed Browser sur iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Améliorations apportées au workflow de configuration des appareils sur le Portail d’entreprise pour iOS dans la version 2.9.0 <!-- 1417174 -->

Le workflow de configuration des appareils a été amélioré dans l’application Portail d’entreprise pour iOS. La langue est plus conviviale, et nous avons regroupé des écrans dans la mesure du possible. La langue est également plus adaptée à l’entreprise, car nous utilisons à chaque fois son nom dans le texte de configuration. Vous pouvez voir ce workflow mis à jour sur la page  [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L’entité Utilisateur contient les données utilisateur les plus récentes dans le modèle de données de l’entrepôt de données <!-- 1544273 -->
La première version du modèle de données de l’entrepôt de données Intune ne contenait que des données Intune historiques récentes. Les auteurs de rapports ne pouvaient pas capturer l’état actuel d’un utilisateur. Dans cette mise à jour, **l’entité Utilisateur** est renseignée avec les données utilisateur les plus récentes.

<!-- ########################## -->
## <a name="october-2017"></a>Octobre 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Le numéro de version des applications métier iOS et Android est visible <!-- 1380712 -->

Les applications dans Intune affichent désormais le numéro de version des applications métier Android et iOS. Le numéro s’affiche dans le portail Azure, dans la liste des applications et dans le panneau de vue d’ensemble des applications. Les utilisateurs finaux peuvent voir le numéro d’application dans l’application Portail d’entreprise et dans le portail web.

__Numéro de version complet__ Le numéro de version complet identifie une version précise de l’application. Le numéro apparaît sous la forme _Version_(_Build_). Par exemple, 2.2(2.2.17560800)

Le numéro de version complet est composé de deux éléments :

 - **Version**  
   Le numéro de version est le numéro de version explicite de l’application. Il est utilisé par les utilisateurs finaux pour identifier les différentes versions de l’application.

 - **Numéro de build**  
    Le numéro de build est un numéro interne qui peut être utilisé pour la détection de l’application et pour gérer l’application par programmation. Le numéro de build fait référence à une itération de l’application qui référence les changements apportés au code.

Pour découvrir plus en détail les numéros de version et le développement d’applications métier, consultez [Prise en main du kit SDK d’application Microsoft Intune](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Intégration de la gestion des appareils et des applications <!-- 677972 -->   
Maintenant que la gestion des appareils mobiles (MDM) et la gestion des applications mobiles (MAM) d’Intune sont accessibles à partir du portail Azure, Intune a commencé à intégrer l’expérience d’administrateur informatique dans la gestion des applications et des appareils. Ces changements sont destinés à simplifier votre expérience de la gestion des appareils et des applications.

Découvrez plus en détail les changements de MDM et de MAM annoncés sur le [blog de l’équipe de support Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nouvelles alertes d’inscription pour les appareils Apple <!-- 1471790 -->
La page de vue d’ensemble de l’inscription affiche les alertes utiles pour les administrateurs informatiques concernant la gestion des appareils Apple. Des alertes s’affichent dans la page Vue d’ensemble quand le certificat push MDM Apple arrive à expiration ou a déjà expiré ; quand le jeton DEP (Programme d’inscription des appareils) expire ou a déjà expiré ; et en présence d’appareils non affectés dans le programme DEP.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Prise en charge du remplacement de jeton pour la configuration d’application sans inscription de l’appareil <!-- 1080364 -->

Vous pouvez utiliser des jetons pour les valeurs dynamiques des configurations des applications des appareils qui ne sont pas inscrits. Pour plus d’informations, consultez [Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil](app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Mise à jour de l’application Portail d’entreprise pour Windows 10 <!--1299474-->
La page Paramètres de l’application Portail d’entreprise pour Windows 10 a été mise à jour pour rendre les paramètres et les actions prévues de l’utilisateur plus cohérents à travers l’ensemble des paramètres, ainsi que pour correspondre à la disposition d’autres applications Windows. Vous trouverez des images avant/après sur la page [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informer les utilisateurs finaux au sujet des informations consultables concernant les appareils Windows 10 <!--1337920-->
Nous avons ajouté le **Type de propriété** dans l’écran Détails de l’appareil de l’application Portail d’entreprise pour Windows 10. Les utilisateurs peuvent ainsi trouver plus d’informations sur la confidentialité directement à partir de cette page dans la documentation de l’utilisateur final d’Intune. Ils les trouveront également sur l’écran **À propos de**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Invites pour la saisie de commentaires dans l’application Portail d’entreprise pour Android <!--1165249-->
L’application Portail d’entreprise pour Android demande maintenant un retour d’expérience des utilisateurs finaux. Ces commentaires sont envoyés directement à Microsoft et permettent aux utilisateurs finaux d’évaluer l’application dans le Google Play Store public. Le retour d’expérience n’est pas obligatoire et peut être facilement ignoré de façon à continuer d’utiliser l’application.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Rendre vos utilisateurs autonomes avec l’application Portail d’entreprise pour Android <!-- 1573324, 1573150, 1558616, 1564878 -->

L’application Portail d’entreprise pour Android a ajouté des indications permettant aux utilisateurs finaux de comprendre et, dans la mesure du possible, de résoudre eux-mêmes les nouveaux cas d’usage.
- Les utilisateurs finaux sont redirigés vers le [portail Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) pour supprimer un appareil s’ils ont atteint le nombre maximal d’appareils qu’ils sont autorisés à ajouter.
- Les utilisateurs finaux reçoivent des instructions pour les aider à [corriger les erreurs d’activation sur les appareils Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) ou à [désactiver le mode d’économie d’énergie](/intune-user-help/power-saving-mode-android). Si aucune de ces solutions ne résout leur problème, nous indiquons comment [envoyer les journaux à Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nouvelle action « Résoudre » disponible pour les appareils Android <!-- 1583480 -->

L’application Portail d’entreprise pour Android introduit une action « Résoudre » dans la page _Mettre à jour les paramètres de l’appareil_. Cette option permettra à l’utilisateur final d’accéder directement au paramètre ayant rendu son appareil non conforme. L’application Portail d’entreprise pour Android prend en charge cette action pour les paramètres [Code secret de l’appareil](/intune-user-help/set-your-pin-or-password-android), [Débogage USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) et [Sources inconnues](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicateur de progression de la configuration de l’appareil sur le Portail d’entreprise Android <!-- 1565657 -->
L’application Portail d’entreprise pour Android affiche un indicateur de progression de la configuration de l’appareil au moment où l’utilisateur l’inscrit. L’indicateur affiche de nouveaux états : tout d’abord, « Configuration de votre appareil en cours... », puis « Inscription de votre appareil en cours... », « Fin de l’inscription de votre appareil... » et enfin « Fin de la configuration de votre appareil... ».

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Prise en charge de l’authentification basée sur les certificats sur le Portail d’entreprise pour iOS <!--1029830-->
Nous avons ajouté la prise en charge de l’authentification basée sur les certificats dans l’application Portail d’entreprise pour iOS. Les utilisateurs avec cette authentification entrent leur nom d’utilisateur et appuient sur le lien « Se connecter avec un certificat ». L’authentification basée sur les certificats est déjà prise en charge sur les applications du Portail d’entreprise pour Android et Windows. Vous pouvez en savoir plus sur la page [Comment faire pour se connecter à l’application Portail d’entreprise](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Les applications qui sont disponibles avec ou sans inscription peuvent désormais être installées sans invitation à l’inscription. <!-- 1334712 -->

Les applications d’entreprise qui ont été mises à disposition avec ou sans inscription dans l’application Portail d’entreprise Android peuvent désormais être installées sans invitation à l’inscription.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617---"></a>Prise en charge du programme de déploiement Windows AutoPilot dans Microsoft Intune  <!-- 747617  -->
Vous pouvez désormais utiliser Microsoft Intune avec le programme de déploiement Windows AutoPilot pour permettre à vos utilisateurs de provisionner eux-mêmes leurs appareils d’entreprise sans passer par le service informatique. Vous pouvez personnaliser l’expérience OOBE (out-of-box experience) pour permettre aux utilisateurs de joindre leurs appareils à Azure AD et de s’inscrire à Intune. Avec Microsoft Intune et Windows AutoPilot, vous n’avez plus à déployer et à gérer les images de système d’exploitation. Pour plus d’informations, consultez [Inscrire des appareils Windows à l’aide du programme Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="quickstart-for-device-enrollment----1425655---"></a>Guide de démarrage rapide pour l’inscription des appareils  <!-- 1425655 --> 
Le guide de démarrage rapide, désormais disponible dans **Inscription d’appareils**, fournit un tableau de références pour gérer les plateformes et configurer la procédure d’inscription. Vous trouverez une brève description de chaque élément et des liens vers des instructions pas à pas pour simplifier le démarrage.

### <a name="device-categorization----1427491---"></a>Catégorisation des appareils <!-- 1427491 -->
Le graphique des plateformes des appareils inscrits du panneau **Appareils > Vue d’ensemble** organise les appareils par plateforme (Android, iOS, macOS, Windows, Windows Mobile, etc.).  Les appareils qui exécutent d’autres systèmes d’exploitation sont regroupés dans « Autres ».  Il s’agit des appareils fabriqués par Blackberry, NOKIA, etc.  

Pour identifier les appareils affectés dans votre locataire, choisissez **Gérer > Tous les appareils**, puis utilisez **Filtrer** pour limiter le champ **Système d’exploitation**.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium : nouveau partenaire de Mobile Threat Defense   <!-- 954681 -->  
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Zimperium,solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Déroulement de l’intégration à Intune
Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant Zimperium. Vous pouvez configurer des stratégies d’accès conditionnel EMS basées sur l’évaluation des risques de Zimperium, activée par le biais des stratégies de conformité Intune, que vous pouvez utiliser pour autoriser ou bloquer l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nouveaux paramètres pour le profil de restriction des appareils Windows 10  <!--- 978575, 1308849, -->  
Nous ajoutons de nouveaux paramètres au profil de restriction des appareils Windows 10 dans la catégorie Windows Defender SmartScreen.

Pour obtenir plus d’informations sur le profil de restriction des appareils Windows 10, consultez [Paramètres de restriction des appareils Windows 10 et version ultérieure]( device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Prise en charge à distance des appareils Windows et Windows Mobile   <!-- 1070473 -->  
Intune peut désormais utiliser le logiciel [TeamViewer](https://www.teamviewer.com), vendu séparément, pour vous permettre de fournir une assistance à distance aux utilisateurs qui utilisent des appareils Windows et Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988-1280990---"></a>Analyser les appareils avec Windows Defender <!-- 1280988  1280990   -->
Vous pouvez à présent exécuter une **Analyse rapide**, une **Analyse complète** et **Mettre à jour les signatures** avec l’antivirus Windows Defender sur les appareils Windows 10 gérés. À partir du panneau de présentation de l’appareil, choisissez l’action à exécuter sur l’appareil. Vous êtes invité à confirmer l’action avant l’envoi de la commande à l’appareil. 

**Analyse rapide** : une analyse rapide analyse les emplacements où les programmes malveillants s’enregistrent pour démarrer, comme les clés de registre et les dossiers de démarrage Windows connus. Une analyse rapide prend en moyenne cinq minutes. Associée au paramètre **Protection en temps réel toujours activé** qui analyse les fichiers lorsqu’ils sont ouverts, fermés et à chaque fois qu’un utilisateur accède à un dossier, une analyse rapide fournit une protection contre les programmes malveillants qui peuvent se trouver dans le système ou le noyau. Lorsque l’analyse s’achève, ses résultats s’affichent sur les appareils des utilisateurs. 

**Analyse complète** : une analyse complète peut être utile sur les appareils confrontés à une menace issue de programmes malveillants afin de déterminer s’il existe des composants inactifs qui nécessitent un nettoyage plus approfondi. Elle est également utile pour exécuter des analyses à la demande. Une analyse complète peut prendre une heure. Lorsque l’analyse s’achève, ses résultats s’affichent sur les appareils des utilisateurs. 

**Mettre à jour les signatures** : la commande de mise à jour de signature met à jour les définitions et les signatures des programmes malveillants dans Antivirus Windows Defender. Cela permet de garantir l’efficacité d’Antivirus Windows Defender dans la détection des programmes malveillants. Cette fonctionnalité s’applique uniquement aux appareils Windows 10 et est sujette à la connectivité Internet de l’appareil. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Le bouton Activer/Désactiver n’est plus disponible sur la page Autorité de certification Intune du Portail Azure Intune  <!-- 1400455 -->
 Nous avons enlevé une étape du processus de configuration de Certificate Connector sur Intune. Actuellement, vous téléchargez Certificate Connector et vous l’activez dans la console Intune. Mais si vous le désactivez dans la console Intune, il continue d’émettre des certificats.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Depuis octobre, le bouton Activer/désactiver n’apparaît plus dans la page Autorité de certification du portail Azure. La fonctionnalité Certificate Connector reste la même. Les certificats sont toujours déployés sur les appareils inscrits à Intune. Vous pouvez continuer à télécharger et à installer Certificate Connector. Pour arrêter l’émission de certificats, vous devez désinstaller Certificate Connector au lieu de le désactiver.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Si Certificate Connector est actuellement désactivé, vous devez le désinstaller.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nouveaux paramètres pour le profil de restriction d’appareils Windows 10 Collaboration   <!--- 1308838 -->
Dans cette version, nous avons ajouté un grand nombre de nouveaux paramètres au profil de restriction d’appareils Windows 10 Collaboration pour vous permettre de gérer les appareils Surface Hub.

Pour plus d’informations sur ce profil, consultez [Paramètres de restriction d’appareils Windows 10 Collaboration](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Empêcher les utilisateurs d’appareils Android de changer la date et l’heure de leur appareil  <!-- 1333292 -->
Vous pouvez utiliser la [stratégie d’appareil personnalisée Android](custom-settings-android.md) pour empêcher les utilisateurs d’appareils Android de modifier la date et l’heure de l’appareil.

Pour ce faire, configurez une stratégie personnalisée Android avec le paramètre URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Affectez-lui la valeur **TRUE**, puis attribuez-le aux groupes requis.

### <a name="bitlocker-device-configuration---1397398---"></a>Configuration d’appareil BitLocker <!-- 1397398 -->
Les paramètres **Chiffrement Windows > Paramètres de Base** incluent un nouveau paramètre **Avertissement sur le chiffrement d’un autre disque** qui vous permet de désactiver le [message d’avertissement](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) sur le chiffrement d’un autre disque qui peut être utilisé sur l’appareil de l’utilisateur.  Le message d’avertissement nécessite le consentement de l’utilisateur final pour configurer BitLocker sur l’appareil et bloque la configuration de BitLocker tant qu’elle n’est pas confirmée par l’utilisateur final.  Le nouveau paramètre désactive l’avertissement pour l’utilisateur final.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Le programme d’achat en volume pour les applications métier est désormais synchronisé avec votre locataire Intune <!-- 800882 -->  
Les développeurs tiers peuvent distribuer des applications en privé aux membres autorisés du programme d’achat en volume (VPP) pour les entreprises. Ces membres du programme d’achat en volume pour les entreprises peuvent se connecter à l’App Store du programme d’achat en volume et acheter leurs applications.

À compter de cette version, les applications du programme d’achat en volume pour les entreprises achetées par l’utilisateur final sont désormais synchronisées avec leurs locataires Intune.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Sélectionner un magasin Apple du pays/région pour synchroniser les applications VPP  <!-- 1332311 -->  
Vous pouvez configurer le magasin du pays/région pour le programme d’achat en volume (VPP) lors du chargement de votre jeton VPP. Intune synchronise les applications VPP pour tous les paramètres régionaux à partir du magasin du pays/région VPP spécifié.

> [!NOTE]  
> Actuellement, Intune synchronise uniquement les applications VPP à partir du magasin du pays/région VPP qui correspond aux paramètres régionaux Intune avec lesquels le client Intune a été créé.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloquer la copie et le collage entre les profils professionnels et personnels dans Android for Work <!-- 1098994 -->
Avec cette version, vous pouvez configurer le profil professionnel Android for Work afin qu’il bloque la copie et le collage entre les applications professionnelles et personnelles. Vous trouverez ce nouveau paramètre dans le profil **Restrictions d’appareils** pour la plateforme **Android for Work** dans **Paramètres du profil professionnel**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Créer des applications iOS limitées à des App Stores Apple locaux spécifiques <!-- 1281692 -->
Vous pourrez spécifier les paramètres régionaux lors de la création d’une application managée App Store Apple.

> [!Note]  
> Actuellement, vous pouvez uniquement créer des applications gérées par l’App Store d’Apple qui sont présentes dans le Store des États-Unis.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Mettre à jour les applications sous licence pour l’appareil et l’utilisateur VPP iOS  <!-- 1305564 -->  
Vous pourrez configurer le jeton VPP iOS pour mettre à jour toutes les applications achetées pour ce jeton via le service Intune. Intune détecte les mises à jour des applications VPP dans le magasin d’applications et les envoie (Push) automatiquement vers l’appareil lorsque ce dernier se connecte.

Pour savoir comment définir un jeton VPP et activer les mises à jour automatiques, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Collection d’entités Association appareil-utilisateur ajoutée au modèle de données de l’entrepôt de données Intune <!-- 1187917 -->
Vous pouvez désormais générer des rapports et des visualisations des données en utilisant les informations d’association appareil-utilisateur qui associent les collections d’entité utilisateur et appareil. Le modèle de données est accessible par le biais du fichier Power BI (PBIX) extrait de la page Intune Data Warehouse, via le point de terminaison OData, ou en développant un client personnalisé.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Vérifier la conformité de la stratégie pour les anneaux de mise à jour Windows 10 <!-- 1067886 -->
Vous pouvez consulter un rapport sur la stratégie pour vos boucles de mise à jour de Windows 10 à partir de Mises à jour logicielles > État de déploiement par boucle de mise à jour. Le rapport sur la stratégie inclut l’état du déploiement pour les boucles de mise à jour que vous avez configurées. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions----1352223---"></a>Nouveau rapport répertoriant les appareils iOS équipés d’anciennes versions de l’iOS   <!-- 1352223 -->
Le rapport **Appareils iOS obsolètes** est disponible à partir de l’espace de travail **Mises à jour logicielles**. Dans ce rapport, vous pouvez afficher la liste des appareils iOS supervisés qui ont été ciblés par une stratégie de mise à jour iOS, et pour lesquels des mises à jour sont disponibles. Pour chaque appareil, vous pouvez afficher un état indiquant la raison pour laquelle l’appareil n’a pas été automatiquement mis à jour. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Afficher les attributions de la stratégie de protection des applications pour résoudre les problèmes <!--  1475003 -->
Dans cette version à venir, l’option **Stratégie de protection des applications** sera ajoutée à la liste déroulante **Affectations** disponible dans le panneau de résolution des problèmes. Vous pouvez maintenant sélectionner des stratégies de protection des applications pour afficher les stratégies de protection des applications affectées aux utilisateurs sélectionnés.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Améliorations apportées au workflow de configuration des appareils dans le Portail d’entreprise <!--1490692-->
Nous avons amélioré le workflow de configuration des appareils dans l’application Portail d’entreprise pour Android. Le texte de l’interface est plus convivial et spécifique à votre entreprise, et nous avons regroupé des écrans quand cela était possible. Vous pouvez voir cela dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Amélioration de l’aide concernant la demande d’accès aux contacts sur les appareils Android <!--1484985-->

L’application Portail d’entreprise pour Android nécessite souvent que l’utilisateur final accepte l’autorisation pour les contacts. Si un utilisateur final refuse cet accès, il voit désormais une notification dans l’application qui lui indique d’accorder l’autorisation pour l’accès conditionnel. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Correction du démarrage sécurisé pour Android <!--1490712-->

Les utilisateurs finaux d’appareils Android peuvent désormais indiquer la raison de la non-conformité dans l’application Portail d’entreprise. Quand c’est possible, ils sont directement positionnés à l’emplacement approprié dans l’application Paramètres pour corriger le problème. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notifications Push supplémentaires pour les utilisateurs finaux sur l’application Portail d’entreprise pour Android Oreo <!--1475932-->

Les utilisateurs finaux voient des notifications supplémentaires qui leur indiquent quand l’application Portail d’entreprise pour Android Oreo effectue des tâches en arrière-plan, comme la récupération de stratégies auprès du service Intune. La transparence s’en trouve améliorée pour les utilisateurs finaux, qui savent quand le Portail d’entreprise effectue des tâches d’administration sur leur appareil. Cette amélioration fait partie de [l’optimisation générale de l’interface utilisateur du portail d’entreprise](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) pour l’application Portail d’entreprise pour Android Oreo. 

Vous verrez d’autres optimisations relatives aux nouveaux éléments d’interface utilisateur dans Oreo Android.  Les utilisateurs finaux voient des notifications supplémentaires qui leur indiquent quand le portail d’entreprise effectue des tâches en arrière-plan, comme la récupération d’une stratégie auprès du service Intune.  La transparence s’en trouve améliorée pour les utilisateurs finaux, qui savent quand le portail d’entreprise effectue des tâches d’administration sur l’appareil.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nouveaux comportements de l’application Portail d’entreprise pour Android avec les profils professionnels <!-- 1485783 -->

Lorsque vous inscrivez un appareil Android for Work avec un profil professionnel, c’est l’application Portail d’entreprise dans le profil professionnel qui effectue les tâches de gestion sur l’appareil. 

L’application Portail d’entreprise pour Android n’a plus aucune utilité, sauf si vous utilisez une application GAM dans le profil professionnel. Pour améliorer l’expérience liée au profil professionnel, Intune masque automatiquement l’application Portail d’entreprise personnelle après l’inscription réussie d’un profil professionnel.

L’application Portail d’entreprise pour Android peut être activée à tout moment dans le profil personnel en recherchant [Portail d’entreprise dans le Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et en appuyant sur **Activer**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Portail d’entreprise pour Windows 8.1 et Windows Phone 8.1 désormais simplement maintenu <!--1428681-->

À partir d’octobre 2017, les applications Portail d’entreprise pour Windows 8.1 et Windows Phone 8.1 passent en mode soutenu. Cela signifie que les applications et les scénarios existants, comme l’inscription et la conformité, seront toujours pris en charge pour ces plateformes. Ces applications resteront disponibles au téléchargement par le biais des canaux de publication existants, comme Microsoft Store. 

Une fois en mode soutenu, ces applications recevront uniquement les mises à jour de sécurité critiques. Aucune mise à jour ou fonctionnalité supplémentaire ne sera publiée pour ces applications. Pour obtenir les nouvelles fonctionnalités, nous vous recommandons de mettre à jour les appareils vers Windows 10 ou Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Bloquer l’inscription des appareils Samsung Knox non pris en charge  <!-- 1490695 -->

L’application Portail d’entreprise tente d’inscrire seulement les appareils Samsung Knox pris en charge. Pour éviter les erreurs d’activation Knox qui empêchent l’inscription à MDM, l’inscription des appareils est tentée seulement si l’appareil apparaît dans la [liste des appareils publiée par Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Les appareils Samsung peuvent avoir des numéros de modèles qui prennent en charge Knox, alors que d’autres ne le prennent pas en charge. Vérifiez la compatibilité de Knox auprès du revendeur de votre appareil avant l’achat et le déploiement. Vous pouvez trouver la liste complète des appareils vérifiés dans les [paramètres de stratégie Android et Samsung Knox Standard](supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fin du support pour Android 4.3 et versions antérieures <!-- 1171126, 1326920 -->
Les applications gérées et l’application Portail d’entreprise pour Android nécessiteront Android 4.4 et ultérieur pour accéder aux ressources de l’entreprise. En décembre, tous les appareils inscrits seront obligatoirement mis hors service et perdront l’accès aux ressources de l’entreprise. Si vous utilisez des stratégies de protection des applications sans MDM, les applications ne recevront aucune mise à jour et perdront en qualité au fil du temps.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informer les utilisateurs finaux au sujet des informations concernant leurs appareils consultables sur les appareils inscrits <!--1165314-->
Nous ajoutons l’information **Type de propriété** dans l’écran des détails des appareils qui se trouve sur toutes les applications du portail d’entreprise. Ainsi, les utilisateurs ont accès à plus d’informations sur la confidentialité directement dans l’article [Quelles informations votre entreprise peut-elle voir ?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Ceci sera introduit dans toutes les applications du portail d’entreprise dans un futur proche. Nous avons annoncé ceci pour iOS en [septembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

<!-- ########################## -->
## <a name="september-2017"></a>Septembre 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune prend en charge iOS 11 <!--1428975-->
Intune prend en charge iOS 11. Ceci avait été annoncé sur le [blog du support technique Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fin du support d’iOS 8.0 <!-- 1164477 -->
Les applications gérées et l’application Portail d’entreprise pour iOS nécessiteront iOS 9.0 et ultérieur pour accéder aux ressources d’entreprise. Les appareils qui ne sont pas mis à jour avant septembre ne seront plus en mesure d’accéder au portail d’entreprise ni à ces applications. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Action d’actualisation ajoutée à l’application Portail d’entreprise pour Windows 10 <!--1132468-->
L’application Portail d’entreprise pour Windows 10 permet aux utilisateurs d’actualiser les données dans l’application avec une requête Pull pour actualiser ou, sur les postes de travail, en appuyant sur F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informer les utilisateurs finaux au sujet des informations concernant leurs appareils consultables sur iOS <!--739894-->

Nous avons ajouté l’information **Type de propriété** dans l’écran des détails de l’appareil qui se trouve sur l’application Portail d’entreprise pour iOS. Les utilisateurs peuvent ainsi trouver plus d’informations sur la confidentialité directement à partir de cette page dans la documentation de l’utilisateur final d’Intune. Ils pourront également trouver cette information dans l’écran À propos de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Autoriser les utilisateurs finaux à accéder à l’application Portail d’entreprise pour Android sans inscription <!---1169910--->

Les utilisateurs finaux n’auront bientôt pas à inscrire leur appareil pour accéder à l’application Portail d’entreprise pour Android. Les utilisateurs finaux des organisations qui utilisent des stratégies de protection des applications ne recevront plus d’invites pour inscrire leur appareil quand ils ouvriront l’application Portail d’entreprise. Les utilisateurs finaux pourront également installer des applications à partir du portail d’entreprise sans inscrire l’appareil. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Formulation plus facile à comprendre pour l’application Portail d’entreprise pour Android <!---1396349--->  

Le processus d’inscription de l’application Portail d’entreprise pour Android a été simplifié à l’aide d’un nouveau texte afin de faciliter l’inscription des utilisateurs finaux. Si vous disposez d’une documentation personnalisée sur l’inscription, mettez-la à jour pour voir les nouveaux écrans. Vous trouverez des exemples d’images sur notre page [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Application Portail d’entreprise Windows 10 ajoutée à la stratégie d’autorisation Protection des informations Windows <!-- 677129 -->

L’application Portail d’entreprise Windows 10 a été mise à jour pour prendre en charge la Protection des informations Windows (WIP). L’application peut être ajoutée à la stratégie d’autorisation Protection des informations Windows. Grâce à cette modification, il n’est plus nécessaire d’ajouter l’application à la liste **Exempté**.


<!-- ########################## -->
## <a name="august-2017"></a>Août 2017

### <a name="improvements-to-device-overview----1404453---"></a>Vue d’ensemble des améliorations apportées à l’appareil <!-- 1404453 -->  
La vue d’ensemble des améliorations apportées à l’appareil affiche à présent les appareils inscrits mais exclut les appareils gérés par Exchange ActiveSync. Les appareils Exchange ActiveSync n’ont pas les mêmes options de gestion que les appareils inscrits. Pour afficher le nombre d’appareils inscrits et le nombre d’appareils inscrits par plateforme dans le portail Azure d’Intune, accédez à **Appareils** > **Vue d’ensemble**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Améliorations apportées à l’inventaire des appareils collecté par Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
Dans cette version, nous avons apporté les améliorations suivantes aux informations d’inventaire collectées par les appareils que vous gérez :
 
-   Pour les appareils Android, vous pouvez maintenant ajouter une colonne à l’inventaire des appareils qui affiche le dernier niveau de correctif logiciel pour chaque appareil. Ajoutez la colonne **Niveau du correctif de sécurité** à votre liste d’appareils pour afficher cette information.
-   Quand vous filtrez la vue des appareils, vous pouvez désormais filtrer les appareils sur leur date d’inscription. Par exemple, vous pouvez afficher uniquement les appareils qui ont été inscrits après une date que vous spécifiez.
-   Nous avons apporté des améliorations au filtre utilisé par l’élément **Date du dernier archivage**.
-   Dans la liste des appareils, vous pouvez maintenant afficher le numéro de téléphone d’appareils appartenant à l’entreprise.
En outre, vous pouvez utiliser le volet de filtre pour rechercher des appareils par numéro de téléphone.

Pour plus d’informations sur l’inventaire des appareils, consultez [Guide d’affichage de l’inventaire des appareils Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Prise en charge de l’accès conditionnel pour les appareils macOS 
<!-- 720172 -->
Vous pouvez maintenant définir une stratégie d’accès conditionnel exigeant que les appareils Mac soient inscrits dans Intune et conformes à ses stratégies de conformité des appareils. Par exemple, les utilisateurs peuvent télécharger l’application Portail d’entreprise Intune pour macOS et inscrire leurs appareils Mac dans Intune. Intune évalue si l’appareil Mac est conforme ou non aux spécifications telles que le code PIN, le chiffrement, la version du système d’exploitation et l’intégrité du système.

- Découvrez plus en détail la [prise en charge de l’accès conditionnel pour les appareils macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>L’application Portail d’entreprise pour macOS est en préversion publique <!---1484796--->
L’application Portail d’entreprise pour macOS est désormais disponible dans la préversion publique pour l’accès conditionnel dans Enterprise Mobility + Security. Cette version prend en charge macOS 10.11 et ultérieur. Obtenez-la à l’adresse [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10    
<!--1063965, 1308850  -->
Dans cette version, nous avons ajouté de nouveaux paramètres pour le [profil de restriction d’appareil Windows 10](/intune/device-restrictions-windows-10) dans les catégories suivantes :

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Mises à jour du profil d’appareil Endpoint Protection Windows 10 pour les paramètres BitLocker
<!--1459533 -->     Dans cette version, nous avons apporté les améliorations suivantes au fonctionnement des paramètres BitLocker dans un profil d’appareil Endpoint Protection Windows 10 :
 
-   Sous **Paramètres des lecteurs de système d’exploitation BitLocker**, pour le paramètre **BitLocker avec puce TPM non compatible**, quand vous sélectionniez **Bloquer**, auparavant, BitLocker aurait en fait été autorisé. Nous avons maintenant résolu ce problème pour bloquer BitLocker quand cette option est sélectionnée.
-   Sous **Paramètres des lecteurs de système d’exploitation BitLocker**, pour le paramètre **Agent de récupération de données basé sur les certificats**, vous pouvez maintenant bloquer explicitement l’agent de récupération de données basé sur le certificat. Toutefois, par défaut, l’agent est autorisé.
-   Sous **Paramètres des lecteurs de données fixes BitLocker**, pour le paramètre **Agent de récupération de données**, vous pouvez maintenant bloquer explicitement l’agent de récupération de données.
Pour plus d’informations, consultez [Paramètres Endpoint Protection pour Windows 10 et versions ultérieures](endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nouvelle expérience de connexion pour les utilisateurs du Portail d’entreprise Android et les utilisateurs de stratégies de protection des applications <!-- 621669 -->
Les utilisateurs finaux peuvent désormais parcourir les applications, gérer les appareils et afficher des informations de contact informatique au moyen de l’application Portail d’entreprise Android sans inscrire leurs appareils Android. Par ailleurs, si un utilisateur final utilise déjà une application protégée par des stratégies Intune App Protection et qu’il lance le portail d’entreprise Android, il ne reçoit plus d’invite d’inscription pour son appareil.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nouveau paramètre dans l’application Portail d’entreprise Android pour activer/désactiver l’optimisation de batterie <!--1405990-->
La page **Paramètres** dans l’application Portail d’entreprise pour Android propose un nouveau paramètre qui permet aux utilisateurs de désactiver facilement l’optimisation de batterie pour les applications Portail d’entreprise et Microsoft Authenticator. Le nom de l’application qui est indiqué dans le paramètre varie en fonction de l’application qui gère le compte professionnel. Nous préconisons aux utilisateurs de désactiver l’optimisation de batterie pour améliorer les performances des applications professionnelles qui synchronisent les e-mails et les données. 

### <a name="multi-identity-support-for-onenote-for-ios----1234281---"></a>Prise en charge de plusieurs identités dans OneNote pour iOS      <!-- 1234281 -->
Les utilisateurs finaux peuvent désormais utiliser des comptes différents (professionnels et personnels) avec Microsoft OneNote pour iOS. Il est possible d’appliquer des stratégies de protection des applications à des données d’entreprise dans des blocs-notes professionnels sans affecter leurs blocs-notes personnels. Par exemple, une stratégie peut autoriser un utilisateur à rechercher des informations dans des blocs-notes de travail, mais l’empêcher de copier et de coller des données d’entreprise du bloc-notes professionnel vers un bloc-notes personnel.
 
- En savoir plus sur les applications qui prennent en charge [la protection d’application et les identités multiples](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) avec Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nouveaux paramètres pour autoriser et bloquer des applications sur les appareils Samsung Knox Standard
<!-- 1305423 822899-->  
Dans cette version, nous ajoutons de nouveaux [paramètres de restriction des appareils](device-restrictions-android.md) qui vous permettent de spécifier les listes d’applications suivantes :
 
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

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256-1245463----"></a>Restriction d’inscription d’appareils Android et iOS en fonctions des versions du système d’exploitation  <!--- 1333256,  1245463 --->
Intune prend désormais en charge la restriction d’inscription d’appareils Android et iOS par numéro de version de système d’exploitation. Sous **Restriction de type d’appareil**, l’administrateur informatique peut désormais définir une configuration de plateforme pour restreindre l’inscription à une plage de valeurs de système d’exploitation minimale et maximale. Les versions du système d’exploitation Android doivent être spécifiées au format Majeure.Mineure.Build.Révision, où Mineure, Build et Révision sont facultatifs. Les versions d’iOS doivent être spécifiées au format Majeure.Mineure.Build, où Build est facultatif. Découvrez plus d’informations sur les [restrictions d’inscription d’appareils](enrollment-restrictions-set.md).

>[!NOTE]
>Ne limite pas l’inscription avec des programmes d’inscription Apple ou Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272-1333275-1245709---"></a>Limiter l’inscription des appareils personnels Android, iOS et macOS  <!--- 1333272,  1333275, 1245709 --->
Intune peut limiter l’inscription d’appareils personnels avec des listes vertes de numéros IMEI d’appareils d’entreprise. Intune a récemment étendu cette fonctionnalité à iOS, Android et macOS avec des numéros de série d’appareils. En chargeant les numéros de série sur Intune, vous pouvez prédéclarer des appareils comme appartenant à l’entreprise. Les restrictions d’inscription vous permettent de bloquer les appareils personnels (BYOD), ce qui permet l’inscription des appareils de l’entreprise uniquement. Découvrez plus d’informations sur les [restrictions d’inscription d’appareils](enrollment-restrictions-set.md).

Pour importer des numéros de série, accédez à **Inscription d’appareil** > **Identificateurs d’appareil d’entreprise** et cliquez sur **Ajouter**, puis chargez un fichier .CSV (pas d’en-tête, deux colonnes pour le numéro de série et des détails comme les numéros IMEI). Pour restreindre les appareils personnels, accédez à **Inscription d’appareil** > **Restrictions d’inscription**. Sous **Restrictions de type d’appareil**, sélectionnez **Par défaut**, puis **Configurations de plateforme**. Vous pouvez **Autoriser** ou **Bloquer** les appareils personnels pour iOS, Android et macOS.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nouvelle action d’appareil pour forcer les périphériques à se synchroniser avec Intune <!-- 711369 -->
Dans cette version, nous avons ajouté une nouvelle action qui force l’appareil sélectionné à s’enregistrer immédiatement auprès d’Intune. Quand un appareil s’enregistre, il reçoit immédiatement les actions ou les stratégies en attente qui lui ont été affectées.  Cette action peut vous aider à valider et corriger immédiatement les stratégies que vous avez affectées, sans attendre le prochain enregistrement planifié.
Pour plus d’informations, consultez [Synchroniser un appareil](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour logicielle disponible <!-- 777100 -->
Une nouvelle stratégie est disponible dans l’espace de travail des mises à jour logicielles, qui vous permet de forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour logicielle disponible. Pour plus d’informations, consultez [Configurer les stratégies de mise à jour iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile : nouveau partenaire de Mobile Threat Defense  <!-- 954651, 1172027 -->
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise avec un accès conditionnel basé sur une évaluation des risques effectuée par CheckPoint SandBlast Mobile, qui est une solution de protection contre les menaces mobiles qui s’intègre à Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Déroulement de l’intégration à Intune
Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant CheckPoint SandBlast Mobile. Vous pouvez configurer des stratégies d’accès conditionnel EMS basées sur l’évaluation des risques de CheckPoint SandBlast Mobile, activée par le biais des stratégies de conformité Intune. Vous pouvez autoriser ou bloquer l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Déployer une application en tant qu’application disponible dans le Microsoft Store pour Entreprises <!-- 748101 -->
Avec cette version, les administrateurs peuvent désormais indiquer que le Microsoft Store pour Entreprises est disponible. Quand il est déclaré disponible, les utilisateurs finaux peuvent installer l’application à partir de l’application ou du site web Portail d’entreprise sans être redirigé vers le Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Mises à jour apportées à l’interface utilisateur sur le site web Portail d’entreprise <!--1313244 part 1-->
Nous avons procédé à quelques mises à jour sur l’interface utilisateur du [site Web Portail d’entreprise](https://portal.manage.microsoft.com) pour améliorer l’expérience de l’utilisateur final.

- __Améliorations apportées aux vignettes des applications__ : des icônes d’application s’affichent désormais avec un arrière-plan généré automatiquement en fonction de la couleur dominante de l’icône (si elle peut être détectée). Quand il est applicable, cet arrière-plan remplace la bordure grise qui apparaissaît sur les vignettes des applications.

    Dans une prochaine version, le site web Portail d’entreprise affichera des grandes icônes quand cela sera possible. Nous recommandons aux administrateurs informatiques de publier des applications en utilisant des icônes d’une taille minimale de 120 x 120 pixels. 

- __Modifications de la navigation__ : les éléments de la barre de navigation sont déplacés dans le menu hamburger situé en haut à gauche. La page Catégories est supprimée. Les utilisateurs peuvent désormais filtrer le contenu par catégorie lors de l’exploration.

- __Mises à jour des applications proposées__  : nous avons ajouté une page dédiée sur le site où les utilisateurs peuvent rechercher les applications que vous avez choisi de proposer, et nous avons apporté quelques ajustements à l’interface utilisateur de la section correspondante sur la page d’accueil.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Prise en charge des iBooks par le site web Portail d’entreprise <!--1231841-->
Nous avons ajouté une page dédiée au site web Portail d'entreprise qui permet aux utilisateurs de parcourir et de télécharger des iBooks. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Détails supplémentaires de résolution des problèmes du support technique <!---  Applies to 1263399, 1326964, 1341642 --->
Intune a mis à jour l’affichage de la résolution des problèmes et a ajouté aux informations qu’il fournit des informations pour les administrateurs et le personnel du support technique. Vous pouvez maintenant voir un tableau **Attributions** qui récapitule toutes les attributions de l’utilisateur en fonction de l’appartenance au groupe. La liste comprend :
- Applications mobiles
- Stratégies de conformité
- Profils de configuration

Par ailleurs, le tableau **Appareils** inclut désormais les colonnes **Type de jointure Azure AD** et **Conforme Azure AD**. Pour plus d’informations, consultez [Aider les utilisateurs à résoudre les problèmes](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Entrepôt de données Intune (préversion publique)
L’entrepôt de données Intune échantillonne quotidiennement les données pour fournir une vue historique de votre locataire. Vous pouvez accéder aux données via un fichier Power BI (PBIX), via un lien OData qui est compatible avec de nombreux outils analytiques ou en interagissant avec l’API REST. Pour plus d’informations, consultez [Utiliser l’entrepôt de données Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modes clair et sombre disponibles pour l’application Portail d’entreprise pour Windows 10 <!---676547--->
Les utilisateurs finaux seront en mesure de personnaliser le mode de couleur de l’application Portail d’entreprise pour Windows 10. Ils pourront apporter la modification dans la section Paramètres de l’application Portail d’entreprise. Le changement apparaîtra une fois que les utilisateurs auront redémarré l’application. Pour Windows 10 versions 1607 et ultérieures, le mode des applications est par défaut le paramètre système. Pour Windows 10 versions 1511 et antérieures, le mode des applications est par défaut le mode clair.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permettre aux utilisateurs finaux d’étiqueter leur groupe d’appareils dans l’application Portail d’entreprise pour Windows 10 <!---807046-->
Les utilisateurs finaux peuvent désormais sélectionner le groupe auquel leur appareil appartient, en le balisant directement à partir de l’application Portail d’entreprise pour Windows 10.

<!-- ########################## -->
## <a name="june-2017"></a>Juin 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nouvel accès à l’administration basée sur les rôles pour les administrateurs Intune   <!-- 1099990 -->  
Un nouveau rôle d’administrateur d’accès conditionnel est ajouté pour afficher, créer, modifier et supprimer des stratégies d’accès conditionnel dans Azure AD. Auparavant, seuls les administrateurs de sécurité et les administrateurs globaux disposaient de cette autorisation. Les administrateurs Intune peuvent obtenir cette autorisation de rôle afin d’avoir accès aux stratégies d’accès conditionnel.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Étiqueter les appareils d’entreprise avec un numéro de série <!-- 1215070 -->  
Intune prend désormais en charge le chargement de numéros de série iOS, macOS et Android en tant qu’identificateurs d’appareil d’entreprise. Vous ne pouvez pas utiliser les numéros de série pour empêcher des appareils personnels de s’inscrire pour le moment, car les numéros de série ne sont pas vérifiés lors de l’inscription. Le blocage des appareils personnels par numéro de série sera disponible dans un futur proche.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nouvelles actions à distance pour les appareils iOS <!-- 854689 -->
Dans cette version, nous avons ajouté deux actions à distance pour les appareils iPad partagés qui gèrent l’application Apple Classroom :

-   [Déconnecter l’utilisateur actuel](device-logout-user.md) : déconnecte l’utilisateur actuel de l’appareil iOS de votre choix.
-   [Supprimer l’utilisateur](device-remove-user.md) : supprime un utilisateur que vous choisissez dans le cache local sur un appareil iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Prise en charge des iPad partagés à l’aide de l’application iOS Classroom <!-- 1044681 -->
Dans cette version, nous avons développé la prise en charge de la gestion de l’application Classroom iOS afin d’inclure les étudiants qui se connectent à des iPad partagés à l’aide de leur ID Apple géré.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Modifications apportées aux applications intégrées Intune <!-- 1332306 -->
Intune contenait auparavant un nombre d’applications intégrées que vous pouviez affecter rapidement. En réponse à vos commentaires, nous avons supprimé cette liste et ces applications intégrées n’apparaîtront plus.
Toutefois, si vous avez déjà affecté des applications intégrées, elles resteront visibles dans la liste des applications. Vous pouvez continuer à affecter ces applications en fonction de vos besoins.
Dans une version ultérieure, nous prévoyons d’ajouter une méthode plus simple pour sélectionner et affecter les applications intégrées à partir du portail Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Installation simplifiée des applications Office 365 <!--- 1121362 --->
À l’aide du nouveau type d’application **Office 365 ProPlus**, vous pouvez affecter facilement des applications Office 365 ProPlus 2016 aux appareils que vous gérez et qui exécutent la dernière version de Windows 10. Vous pouvez également installer Microsoft Project et Microsoft Visio si vous disposez des licences appropriées. Les applications souhaitées sont regroupées et apparaissent sous la forme d’une application unique dans la liste des applications de la console Intune.
Pour plus d’informations, consultez [Guide pratique pour ajouter des applications Office 365 pour Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises <!--- 777044 --->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez alors déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications en mode hors connexion sont installées par Intune et non par le Store.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Les équipes Microsoft font désormais partie de la liste d’applications approuvées des Autorités de certification basée sur l’application   <!-- 1257019 -->
L’application Microsoft Teams pour iOS et Android fait désormais partie des applications approuvées pour les stratégies d’accès conditionnel basé sur l’application pour Exchange et SharePoint Online. L’application peut être configurée via le panneau Intune App Protection dans le portail Azure pour tous les clients utilisant actuellement l’accès conditionnel basé sur l’application.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Intégration de Managed Browser et du proxy d’application <!-- 1287310 -->
Intune Managed Browser peut maintenant s’intégrer au service du proxy d’application Azure AD pour permettre aux utilisateurs d’accéder aux sites web internes même quand ils travaillent à distance. Les utilisateurs du navigateur entrent simplement l’URL du site comme ils le font normalement et Managed Browser achemine la demande via la passerelle web du proxy d’application. Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nouveaux paramètres de configuration d’application pour Intune Managed Browser <!-- 682951 -->
Dans cette version, nous avons ajouté des configurations supplémentaires pour l’application Intune Managed Browser pour iOS et Android. Vous pouvez maintenant utiliser une stratégie de configuration d’application pour configurer la page d’accueil par défaut et les signets du navigateur.
Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Paramètres BitLocker pour Windows 10  <!-- 951707 -->
Vous pouvez maintenant configurer des paramètres BitLocker pour les appareils Windows 10 à l’aide d’un nouveau profil d’appareil Intune. Par exemple, vous pouvez exiger que les appareils soient chiffrés et configurer également d’autres paramètres qui sont appliqués quand BitLocker est activé.
Pour plus d’informations, consultez [Paramètres Endpoint Protection pour Windows 10 et versions ultérieures](endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nouveaux paramètres pour le profil de restriction des appareils Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
Dans cette version, nous avons ajouté de nouveaux paramètres pour le profil de restriction d’appareil Windows 10 dans les catégories suivantes :

-  Windows Defender
-  Cellulaire et connectivité
-  Expérience d’écran de verrouillage
-  Confidentialité
-  Recherche
-  Windows à la une
-  Navigateur Microsoft Edge

Pour plus d’informations sur les paramètres Windows 10, consultez [Paramètres de restriction des appareils Windows 10 et versions ultérieures](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>L’application Portail d’entreprise pour Android présente désormais une nouvelle expérience d’utilisateur final pour les stratégies de protection des applications <!--1305217-->
En fonction des commentaires des clients, nous avons modifié l’application Portail d’entreprise pour Android afin d’afficher un bouton **Accéder au contenu de l’entreprise**. L’objectif est d’empêcher les utilisateurs finaux d’avoir à passer par le processus d’inscription lorsqu’ils ont seulement besoin d’accéder aux applications qui prennent en charge les stratégies de protection des applications, une fonctionnalité de gestion des applications mobiles d’Intune. Vous pouvez afficher ces modifications dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nouvelle action de menu pour supprimer facilement le Portail d’entreprise <!--1164569-->
Suite aux commentaires des utilisateurs, l’application Portail d’entreprise pour Android offre désormais une nouvelle action de menu pour lancer la suppression du portail d’entreprise à partir de votre appareil. Cette action supprime l’appareil de gestion Intune afin que l’application puisse être supprimée de l’appareil par l’utilisateur. Vous pouvez voir ces modifications sur la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md) et dans la [documentation pour les utilisateurs finaux d’Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Améliorations apportées à la synchronisation des applications avec Windows 10 Creators Update <!--676505-->
L’application Portail d’entreprise pour Windows 10 démarre maintenant automatiquement une synchronisation pour les demandes d’installation d’application sur les appareils exécutant Windows 10 Creators Update (version 1703). Cela permet de réduire le problème de blocage des installations d’applications à l’état « Synchronisation en attente ». En outre, les utilisateurs pourront lancer manuellement une synchronisation à partir de l’application. Vous pouvez afficher ces modifications dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nouvelle expérience interactive pour le Portail d’entreprise Windows 10 <!---1058938--->
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

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Changer votre autorité de gestion des périphériques mobiles sans annuler l’inscription des appareils gérés <!--1103950-->
Vous pouvez maintenant changer votre autorité de gestion des appareils mobiles sans avoir à contacter le Support Microsoft et sans avoir à annuler l’inscription et à réinscrire vos appareils gérés existants. Dans la console Configuration Manager, vous pouvez faire [basculer votre autorité de gestion des appareils mobiles](/sccm/mdm/deploy-use/change-mdm-authority) de Définir sur Configuration Manager (hybride) à Microsoft Intune (autonome), ou inversement.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notification améliorée pour les codes PIN de démarrage Samsung Knox <!--1087143-->
Quand les utilisateurs finaux doivent définir un code PIN de démarrage sur les appareils Samsung Knox pour être compatibles avec le chiffrement, la notification affichée aux utilisateurs finaux les mène à l’emplacement exact dans l’application Paramètres lors de l’appui sur la notification.  Auparavant, la notification menait l’utilisateur final à l’écran de modification de mot de passe.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Prise en charge d’Apple School Manager (ASM) avec iPad partagé <!-- 748864, 770395-->

Intune prend maintenant en charge l’utilisation d’Apple School Manager (ASM) à la place du Programme d’inscription d’appareils Apple pour fournir l’inscription des appareils iOS par défaut. L’intégration d’ASM est nécessaire pour utiliser l’application Classroom pour les iPad partagés et pour permettre la synchronisation des données d’ASM vers Azure Active Directory par l’intermédiaire de Microsoft School Data Sync (SDS). Pour plus d’informations, consultez [Activer l’inscription des appareils iOS avec Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> La configuration d’iPad partagés pour travailler avec l’application Classroom requiert des configurations d’éducation iOS dans Azure qui ne sont pas encore disponibles.  Cette fonctionnalité sera bientôt disponible.

### <a name="device-management"></a>Gestion des appareils

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Fournir une assistance à distance sur des appareils Android à l’aide de TeamViewer <!-- 675418 -->

Intune peut maintenant utiliser le logiciel [TeamViewer](https://www.teamviewer.com), vendu séparément, pour vous permettre de fournir une assistance à distance aux utilisateurs qui utilisent des appareils Android. Pour plus d’informations, consultez [Fournir une assistance à distance pour les appareils Android gérés par Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Gestion d'applications

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nouvelles conditions de stratégies de protection des applications pour la gestion des applications mobiles <!-- 679864 -->

Vous pouvez maintenant définir un ensemble de spécifications de GAM pour les utilisateurs sans inscription qui applique les éléments suivants :

- Version minimale de l’application
- Version minimale du système d’exploitation
- Version minimale du SDK d’application Intune de l’application cible (iOS uniquement)

Cette fonctionnalité est disponible sur iOS et Android. Intune prend en charge l’application de la version minimale pour les versions de plateformes de système d’exploitation, les versions d’applications et le SDK d’application Intune. Sur iOS, les applications intégrées au SDK peuvent également définir l’application de la version minimale au niveau du SDK. L’utilisateur ne peut pas accéder à l’application cible si la configuration minimale requise par la stratégie de protection des applications n’est pas satisfaite aux trois niveaux différents mentionnés ci-dessus. À ce stade, l’utilisateur peut supprimer son compte (pour les applications à plusieurs identités), fermer l’application et/ou mettre à jour la version de son système d’exploitation ou de l’application.

De plus, vous pouvez configurer des paramètres supplémentaires pour fournir une notification non bloquante qui recommande une mise à niveau du système d’exploitation ou de l’application. Cette notification peut être fermée et l’application peut être utilisée normalement.

Pour plus d’informations, consultez les [paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md) et les [paramètres de stratégie de protection des applications Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurer les configurations d’application pour Android for Work <!-- 621621 -->
Certaines applications Android du Store prennent en charge des options de configuration gérées qui permettent à un administrateur informatique de contrôler la façon dont une application s’exécute dans le profil de travail. Avec Intune, vous pouvez désormais afficher les configurations prises en charge par une application et les configurer à partir du portail Azure avec un concepteur de configuration ou dans un éditeur JSON. Pour plus d’informations, consultez [Utiliser des configurations d’application pour Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nouvelle fonctionnalité de configuration d’application pour la gestion des applications mobiles sans inscription <!-- 677969 -->
Vous pouvez désormais créer des stratégies de configuration d’application via la gestion des applications mobiles sans canal d’inscription. Cette fonctionnalité équivaut aux stratégies de configuration d’application disponibles dans la configuration de l’application de Gestion des appareils mobiles (MDM). Pour un exemple de configuration d’application avec gestion des applications mobiles sans inscription, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurer des listes d’URL autorisées et bloquées pour Managed Browser <!-- 682960 -->
Vous pouvez désormais configurer une liste de domaines et d’URL autorisés et bloqués pour Intune Managed Browser avec les paramètres de configuration d’application dans le portail Azure. Vous pouvez configurer ces paramètres même s’il est utilisé sur un appareil non géré. Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Vue du support technique pour les stratégies de protection des applications <!-- 1069473 -->
Les utilisateurs du support technique informatique peuvent désormais vérifier l’état des licences utilisateur et l’état des applications de stratégie de protection d’application affectées aux utilisateurs dans le panneau de la résolution des problèmes. Pour plus d’informations, consultez [Résolution des problèmes](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Contrôler les visites de site web sur les appareils iOS <!-- 723832 -->
Vous pouvez maintenant contrôler les sites web auxquels les utilisateurs d’appareils iOS peuvent accéder à l’aide de l’une des deux méthodes suivantes :

- Ajouter des URL autorisées et bloquées à l’aide du filtrage de contenu web intégré d’Apple.

- Autoriser uniquement l’accès aux sites web spécifiés par le navigateur Safari. Des signets sont créés dans Safari pour chaque site que vous spécifiez.

Pour plus d’informations, consultez [Paramètres de filtre de contenu web pour les appareils iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Préconfigurer les autorisations d’appareils pour les applications Android for Work <!-- 621614 -->
Pour les applications déployées sur des profils professionnels Android for Work, vous pouvez maintenant configurer l’état des autorisations pour chacune des applications.  Par défaut, les applications Android qui nécessitent des autorisations d’appareils telles que l’accès à l’emplacement ou à l’appareil photo invitent les utilisateurs à accepter ou à refuser les autorisations.  Par exemple, si une application utilise le microphone de l’appareil, l’utilisateur final est invité à autoriser l’application à utiliser le microphone. Cette fonctionnalité vous permet de définir des autorisations pour le compte de l’utilisateur final.  Vous pouvez configurer des autorisations pour a) refuser automatiquement sans en avertir l’utilisateur, b) automatiquement approuver sans en avertir l’utilisateur, ou c) inviter l’utilisateur à accepter ou refuser. Pour plus d’informations, consultez [Paramètres de restriction des appareils Android for Work dans Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Définir un code PIN propre à l’application pour les appareils Android for Work <!-- 728976, 1102534 -->
Vous pouvez définir une stratégie de mot de passe qui s’applique uniquement aux applications dans le profil professionnel pour les appareils Android 7.0 et versions ultérieures avec un profil de travail géré en tant qu’appareil Android for Work.  Les options sont les suivantes :

- Définir simplement une stratégie de mot de passe au niveau de l’appareil : il s’agit du code secret que l’utilisateur final doit utiliser pour déverrouiller son appareil.
- Définir simplement une stratégie de mot de passe de profil professionnel : les utilisateurs sont invités à entrer un code secret chaque fois qu’une application dans le profil professionnel est ouverte.
- Définir à la fois une stratégie d’appareil et une stratégie de profil professionnel : l’administrateur informatique peut définir à la fois une stratégie de code secret d’appareil et une stratégie de code secret de profil professionnel à des niveaux différents (par exemple, un code PIN à quatre chiffres pour déverrouiller l’appareil, mais un code PIN à six chiffres pour ouvrir une application professionnelle).

Pour plus d’informations, consultez [Paramètres de restriction des appareils Android for Work dans Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Cette fonctionnalité est uniquement disponible sur Android 7.0 et versions ultérieures.  Par défaut, l’utilisateur final peut utiliser les deux codes PIN définis séparément, ou il peut choisir de combiner les deux codes PIN définis dans le plus sécurisé des deux.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nouveaux paramètres des appareils Windows 10 <!-- 978585 -->
Nous avons ajouté [de nouveaux paramètres de restriction d’appareil Windows](device-restrictions-windows-10.md) qui contrôlent des fonctionnalités telles que les affichages sans fil, la détection des appareils, le basculement de tâche et les messages d’erreur de carte SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Mises à jour de la configuration de certificat <!-- 918991 and 823198 -->
Lors de la création d’un profil de certificat SCEP, l’option <strong>Personnalisé</strong> option est disponible pour <strong>Format du nom du sujet</strong> sur les appareils iOS, Android et Windows. Avant cette mise à jour, le champ <strong>Personnalisé</strong> était disponible pour les appareils iOS uniquement. Pour plus d’informations, consultez [Create a SCEP certificate profile](certificates-scep-configure.md#create-a-scep-certificate-profile) (Créer un profil de certificat SCEP).

Lors de la création d’un profil de certificat PKCS, pour **Autre nom de l’objet**, **Attribut personnalisé Azure AD** est disponible. L’option **Service** est disponible lorsque vous sélectionnez **Attribut personnalisé Azure AD**. Pour plus d’informations, consultez [Créer un profil de certificat PKCS](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurer plusieurs applications pouvant s’exécuter lorsqu’un appareil Android est en mode plein écran <!-- 662059 -->
Lorsqu’un appareil Android est en mode plein écran, vous ne pouviez précédemment configurer qu’une application autorisée à s’exécuter. Vous pouvez désormais configurer plusieurs applications à l’aide de l’ID d’application ou de l’URL du Store, ou en sélectionnant une application Android que vous gérez déjà. Pour plus d’informations, consultez [Paramètres du mode plein écran](device-restrictions-android.md#kiosk).



<!-- ########################## -->
## <a name="april-2017"></a>Avril 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Prise en charge de la gestion de l’application Apple Classroom
Vous pouvez désormais gérer l’application iOS Classroom sur des appareils iPad. Configurez l’application Classroom sur l’iPad des enseignants avec les données sur les étudiants et les cours appropriées, puis configurez les iPad des étudiants inscrits à un cours, afin que vous puissiez les contrôler à l’aide de l’application.
Pour plus d’informations, consultez [Configurer les paramètres d’éducation iOS](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Les applications Android prennent en charge les options de configuration gérées <!-- 621621 -->
Les applications Android du Play Store qui prennent en charge les options de configuration gérées peuvent désormais être configurées par Intune.  Cette fonctionnalité permet au personnel informatique d’afficher la liste des valeurs de configuration prises en charge par une application, et fournit une interface interactive et guidée de premier plan pour lui permettre de configurer ces valeurs.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nouvelle stratégie Android pour les codes PIN complexes <!-- 722069 -->
Vous pouvez maintenant définir un type de [mot de passe](device-restrictions-android.md#password) requis « Chiffres complexes » dans un profil d’appareil Android pour les appareils qui exécutent Android 5.0 et versions ultérieures.  Utilisez ce paramètre pour empêcher les utilisateurs d’appareils de créer un code PIN qui contient des nombres répétés ou consécutifs, tel que 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Prise en charge supplémentaire des appareils Android for Work
- **Gérer les paramètres de profil professionnel et le mot de passe** <!-- 612808 -->

  Cette nouvelle stratégie de restriction d’appareil Android for Work vous permet maintenant de gérer les paramètres de profil professionnel et de mot de passe sur les appareils Android for Work que vous gérez.

- **Autoriser le partage de données entre profils professionnels et personnels** <!-- 1045102 -->

Ce profil de restriction d’appareil Android for Work a été enrichi de nouvelles options afin de vous aider à configurer le partage de données entre vos profils personnels et professionnels.

- **Limiter la copie et le collage entre les profils professionnels et personnels** <!-- 1046094 -->

  Ce nouveau profil d’appareil personnalisé pour les appareils Android for Work vous permet de désormais limiter les actions Copier et Coller entre applications professionnelles et personnelles.

Pour plus d’informations, consultez [Device restrictions for Android for Work](device-restrictions-android-for-work.md) (Restrictions d’appareils pour Android for Work).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Attribuer des applications métier à des appareils iOS et Android <!-- 1057568 -->
Vous pouvez désormais affecter des applications métier pour [iOS](lob-apps-ios.md) (fichiers .ipa) et [Android](lob-apps-android.md) (fichiers .apk) à des utilisateurs ou des appareils.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nouvelles stratégies d’appareil pour iOS <!-- 723774, 723815, 723826, 723830 -->
- **Applications dans l’écran d’accueil** : contrôle les applications qui s’affichent dans [l’écran d’accueil de l’appareil iOS](home-screen-settings-ios.md) d’un utilisateur. Cette stratégie change la disposition de l’écran d’accueil, mais ne déploie aucune application.

- **Connexions aux appareils AirPrint** : contrôle les [appareils AirPrint](air-print-settings-ios-macos.md) (imprimantes réseau) auxquels les utilisateurs finaux d’appareils iOS peuvent se connecter.

- **Connexions aux appareils AirPlay** : contrôle les [appareils AirPlay](airplay-settings-ios.md) (comme Apple TV) auxquels les utilisateurs finaux d’appareils iOS peuvent se connecter.

- **Message d’écran de verrouillage personnalisé** : permet de configurer un message personnalisé qui s’affiche sur l’écran de verrouillage des appareils iOS à la place du message d’écran de verrouillage par défaut. Pour plus d’informations, consultez [Activer le mode Perdu sur les appareils iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restreindre les notifications Push sur les applications iOS <!-- 723767 -->
Dans un profil de restriction d’appareil Intune, vous pouvez maintenant configurer les [paramètres de notification](app-notification-settings-ios.md) suivants pour les appareils iOS :

- Activer ou désactiver entièrement la notification pour une application spécifiée.
- Activer ou désactiver la notification dans le Centre de notification pour une application spécifiée.
- Spécifier le type d’alerte : **Aucune**, **Bannière** ou **Alerte modale**.
- Spécifier si les badges sont autorisés pour cette application.
- Spécifier si les sons de notification sont autorisés.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurer les applications iOS pour qu’elles s’exécutent de manière autonome en mode Application unique <!-- 737837 -->
Vous pouvez désormais utiliser un profil d’appareil Intune pour configurer les appareils iOS pour qu’ils exécutent les applications spécifiées en [mode Application unique autonome](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé et il ne peut exécuter que cette application. Vous pouvez par exemple utiliser ce mode quand vous configurez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurer des domaines approuvés pour la messagerie et la navigation web sur des appareils iOS <!-- 723765 -->
À partir d’un profil de restriction d’appareil iOS, vous pouvez maintenant configurer les [paramètres de domaine suivants](device-restrictions-ios.md#domains) :

- **Domaines d’e-mail non marqués** - Les e-mails reçus ou envoyés par l’utilisateur qui ne correspondent pas aux domaines que vous spécifiez ici sont marqués comme non approuvés.

- **Domaines web gérés** - Les documents téléchargés à partir des URL que vous spécifiez ici sont considérés comme gérés (Safari uniquement).  

- **Domaines de remplissage automatique des mots de passe Safari** - Les utilisateurs peuvent enregistrer des mots de passe dans Safari uniquement à partir des URL qui correspondent aux modèles que vous spécifiez ici. Pour utiliser ce paramètre, il faut que l’appareil soit en mode supervisé et non configuré pour plusieurs utilisateurs. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Applications VPP disponibles dans le Portail d’entreprise iOS <!-- 748782 -->
Vous pouvez désormais affecter des applications achetées en volume (VPP) iOS comme installations **disponibles** pour les utilisateurs finaux. Ces derniers auront besoin d’un compte Apple Store pour installer l’application.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synchroniser des livres électroniques depuis l’Apple VPP Store <!-- 800878 -->
Vous pouvez maintenant [synchroniser les livres](vpp-apps-ios.md) que vous avez achetés dans le Store VPP (Programme d’achat en volume) d’Apple avec Intune, et les attribuer à des utilisateurs.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestion des utilisateurs multiples sur les appareils Samsung Knox Standard <!-- 971988 -->
Les appareils qui exécutent Samsung Knox Standard sont désormais pris en charge pour la [gestion des utilisateurs multiples](android-enroll.md) par Intune. Cela signifie que les utilisateurs finaux peuvent se connecter et se déconnecter de l’appareil avec leurs informations d’identification Azure Active Directory, et que l’appareil est géré de façon centralisée qu’il soit en cours d’utilisation ou non.  Quand les utilisateurs finaux se connectent, ils ont accès aux applications et les éventuelles stratégies sont appliquées à ces applications. Quand les utilisateurs se déconnectent, toutes les données d’application sont effacées.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Paramètres de restriction d’appareil Windows supplémentaires <!-- 818566 -->
Nous avons ajouté la prise en charge d’autres [paramètres de restriction d’appareil Windows](device-restrictions-windows-10.md), comme une prise en charge supplémentaire du navigateur Microsoft Edge, la personnalisation de l’écran de verrouillage d’appareil, la personnalisation du menu Démarrer, les papiers peints Windows à la une et les paramètres de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Prise en charge multi-utilisateur pour Windows 10 Creators Update <!-- 822547 -->
Nous avons ajouté la prise en charge de la [gestion des utilisateurs multiples](windows-enroll.md) pour les appareils qui exécutent Windows 10 Creators Update et sont joints à un domaine Azure Active Directory. Cela signifie que quand différents utilisateurs standard se connectent à l’appareil avec leurs informations d’identification Azure AD, ils reçoivent les applications et les stratégies qui ont été affectées à leur nom d’utilisateur. Les utilisateurs ne peuvent actuellement pas utiliser le portail d’entreprise pour les scénarios de libre-service tels que l’installation d’applications.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start pour les PC Windows 10<!-- 1004830 -->
Une nouvelle [action d’appareil Fresh Start](device-fresh-start.md) est maintenant disponible pour les PC Windows 10.  Quand vous exécutez cette action, les applications qui ont été installées sur l’ordinateur sont supprimées, et le PC est automatiquement mis à jour vers la dernière version de Windows. Vous pouvez ainsi supprimer des applications OEM préinstallées, comme celles qui sont souvent fournies avec un nouveau PC. Vous pouvez configurer si les données utilisateur sont conservées quand cette action est exécutée sur l’appareil.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Chemins de mise à niveau Windows 10 supplémentaires <!-- 903672 -->
Vous pouvez désormais créer une [stratégie de mise à niveau d’édition pour mettre à niveau les appareils](edition-upgrade-configure-windows-10.md) vers les éditions Windows 10 supplémentaires suivantes :

- Windows 10 Professionnel
- Windows 10 Professionnel N
- Windows 10 Professionnel Éducation
- Windows 10 Professionnel Éducation N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscription en bloc des appareils Windows 10 <!-- 747607 -->
Vous pouvez désormais joindre un grand nombre d’appareils qui exécutent la mise à jour Windows 10 Creators pour Azure Active Directory et Intune à l’aide du Concepteur de configuration Windows (WCD). Pour activer [l’inscription MDM en bloc](windows-bulk-enroll.md) pour votre client Azure AD, créez un package de configuration qui joint les appareils à votre client Azure AD à l’aide du Concepteur de configuration Windows, puis appliquez le package aux appareils d’entreprise que vous souhaitez inscrire et gérer en bloc. Une fois le package appliqué à vos appareils, ceux-ci se connectent à Azure AD, s’inscrivent dans Intune et vos utilisateurs Azure AD peuvent s’y connecter.  Les utilisateurs d’Azure AD agissent sur ces appareils en tant qu’utilisateurs standard ; ils reçoivent les stratégies qui leur sont affectées ainsi que les applications dont ils ont besoin. Les scénarios de libre-service et de portail d’entreprise ne sont pas pris en charge actuellement.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nouveaux paramètres de gestion des applications mobiles pour les codes PIN et les emplacements de stockage géré <!-- 581122, 736644 -->
Deux nouveaux paramètres d’application sont désormais disponibles pour vous aider dans les scénarios de gestion des applications mobiles (GAM) :

- **Désactiver le code PIN de l’application quand le code PIN de l’appareil est géré** - Détecte si un code PIN d’appareil est présent sur l’appareil inscrit et, si c’est le cas, contourne le code PIN de l’application déclenché par les stratégies de protection des applications. Ce paramètre permet de réduire le nombre d’invites de code PIN pour les utilisateurs ouvrant une application GAM sur un appareil inscrit. Cette fonctionnalité est disponible pour iOS et Android.

- **Sélectionnez dans quels services de stockage les données d’entreprise peuvent être enregistrées** - Permet de spécifier les emplacements de stockage où enregistrer les données d’entreprise. Les utilisateurs peuvent enregistrer dans les services d’emplacement de stockage sélectionnés, ce qui signifie que tous les autres services d’emplacement de stockage non répertoriés seront bloqués.

  Liste des services d’emplacement de stockage pris en charge :

  - OneDrive Entreprise
  - SharePoint Online
  - Stockage local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portail de dépannage du centre de support technique <!-- 907448 -->
Le nouveau [portail de dépannage](help-desk-operators.md) permet aux opérateurs du centre de support technique et aux administrateurs Intune de visualiser les utilisateurs et leurs appareils, et d’effectuer des tâches pour résoudre les problèmes techniques liés à Intune.

<!-- ########################## -->
## <a name="march-2017"></a>Mars 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Prise en charge du mode Perdu iOS <!--431695-->
Pour les appareils iOS 9.3 et versions ultérieures, Intune a ajouté la prise en charge du **Mode Perdu**. Vous pouvez maintenant verrouiller un appareil pour éviter toute utilisation et afficher un numéro de téléphone de contact et un message sur l’écran de verrouillage de l’appareil.

L’utilisateur final ne peut pas déverrouiller l’appareil tant qu’un administrateur n’a pas désactivé le mode Perdu. Lorsque le mode Perdu est activé, vous pouvez utiliser l’action **Localiser l’appareil** pour afficher l’emplacement géographique de l’appareil sur une carte dans la console Intune.

L’appareil doit être un appareil iOS d’entreprise, inscrit via le programme DEP, qui est en mode supervisé.

Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md)

### <a name="improvements-to-device-actions-report---677150--"></a>Améliorations apportées au rapport Actions de l’appareil <!--677150-->
Nous avons apporté des améliorations au rapport Actions de l’appareil afin d’optimiser les performances. En outre, il est désormais possible de filtrer le rapport par état. Par exemple, vous pouvez filtrer le rapport pour qu’il affiche uniquement les actions d’appareil qui ont été effectuées.

### <a name="custom-app-categories---748805--"></a>Catégories d’applications personnalisées <!--748805-->
Vous pouvez désormais créer, modifier et attribuer des catégories pour les applications que vous ajoutez à Intune. Actuellement, les catégories ne peuvent être spécifiées qu'en anglais.
Consultez [Guide pratique pour ajouter une application à Intune](apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Attribuer des applications métier aux utilisateurs disposant d’appareils non inscrits <!--748823-->
Vous pouvez désormais attribuer aux utilisateurs des applications cœur de métier à partir du Store, que leurs appareils soient ou non inscrits auprès d’Intune. Si l’appareil n’est pas inscrit auprès de Intune, l’utilisateur doit se rendre sur le site web du portail d’entreprise, au lieu de l’application du portail d’entreprise, pour l’installer.

### <a name="new-compliance-reports---846671--"></a>Nouveaux rapports de conformité <!--846671-->
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

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accès direct aux scénarios d’inscription d’Apple <!--951869-->
Pour les comptes Intune créés après janvier 2017, Intune a activé un accès direct aux scénarios d’inscription Apple à l’aide de la charge de travail Inscrire des appareils dans le portail Azure. Auparavant, la version préliminaire de l’inscription Apple était uniquement accessible à partir de liens dans le portail Azure. Les comptes Intune créés avant janvier 2017 nécessiteront une migration unique pour que ces fonctionnalités deviennent disponibles dans Azure. La planification de la migration n’a pas encore été annoncée, mais les détails correspondants seront diffusés dès que possible. Si votre compte existant ne peut pas accéder à la version préliminaire, nous vous recommandons vivement de créer un compte d’évaluation afin de tester la nouvelle expérience.


<!-- ########################## -->
## <a name="february-2017"></a>Février 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilité de limiter l’inscription des appareils mobiles <!--747600, 795782-->
Intune ajoute de nouvelles restrictions d’inscription qui contrôlent les plateformes d’appareils mobiles autorisées à être inscrites. Intune sépare les plateformes d’appareils mobiles comme iOS, MacOS, Android, Windows et Windows Mobile.

* La restriction de l’inscription d’appareils mobiles ne limite pas l’inscription des clients de PC.  
* Pour iOS et Android uniquement, il existe une option supplémentaire pour bloquer l’inscription des appareils personnels.

Intune marque tous les nouveaux appareils comme personnels, sauf si l’administrateur prend des mesures pour les marquer comme appareils d’entreprise, comme expliqué dans [cet article](device-enrollment.md).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Afficher toutes les actions sur les appareils gérés <!--677150-->
Un nouveau rapport __Actions de l’appareil__ indique l’utilisateur qui a effectué des actions à distance, comme un rétablissement des paramètres d’usine sur les appareils, et montre également l’état de cette action. Consultez [Qu’est-ce que la gestion des appareils ?](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Les appareils non gérés peuvent accéder aux applications attribuées <!--664691-->
Dans le cadre des modifications conceptuelles du site web du portail d’entreprise, les utilisateurs iOS et Android peuvent installer les applications attribuées indiquées comme « disponibles sans inscription » sur leurs appareils non gérés. À l’aide de leurs informations d’identification Intune, les utilisateurs peuvent se connecter au site web du portail d’entreprise et afficher la liste des applications qui leur sont attribuées. Les packages des applications « disponibles sans inscription » peuvent être téléchargés sur le site web du portail d’entreprise. Les applications dont l’installation nécessite une inscription ne sont pas affectées par cette modification, car les utilisateurs sont invités à inscrire leur appareil s’ils souhaitent installer ces applications.

### <a name="custom-app-categories---748805--"></a>Catégories d’applications personnalisées <!--748805-->
Vous pouvez désormais créer, modifier et attribuer des catégories pour les applications que vous ajoutez à Intune. Actuellement, les catégories ne peuvent être spécifiées qu'en anglais.
Consultez [Guide pratique pour ajouter une application à Intune](apps-add.md).

### <a name="display-device-categories---814654--"></a>Afficher les catégories d’appareils <!--814654-->
Vous pouvez maintenant afficher la catégorie d’appareil sous forme de colonne dans la liste des appareils. Vous pouvez également modifier la catégorie dans la section des propriétés du panneau Propriétés de l’appareil. Consultez [Guide pratique pour ajouter une application à Intune](apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurer les paramètres Windows Update for Business <!--776716-->

Windows en tant que service est la nouvelle façon de fournir des mises à jour pour Windows 10. À partir de Windows 10, les nouvelles mises à jour de fonctionnalités et qualité incluent le contenu de toutes les mises à jour précédentes. Cela signifie que tant que vous avez installé la dernière mise à jour, vous savez que vos appareils Windows 10 sont entièrement à jour. À la différence des versions précédentes de Windows, vous devez maintenant installer la mise à jour complète au lieu d’une partie seulement.

En utilisant Windows Update for Business, vous pouvez simplifier l’expérience de gestion des mises à jour et vous ne devez plus approuver des mises à jour propres à des groupes d’appareils. Vous pouvez toujours gérer les risques dans votre environnement en configurant une stratégie de déploiement de mises à jour afin que Windows Update fasse en sorte que les mises à jour soient installées au moment opportun. Microsoft Intune permet de configurer les paramètres de mise à jour des appareils et vous donne la possibilité de reporter l’installation des mises à jour. Intune ne stocke pas les mises à jour, seulement l’attribution des stratégies de mise à jour. Les appareils accèdent directement à Windows Update. Utilisez Intune pour configurer et gérer les **anneaux de mise à jour Windows 10**. Un anneau de mise à jour contient un groupe de paramètres permettant de configurer le moment et la façon d’installer les mises à jour Windows 10. Pour plus d’informations, consultez [Configurer les paramètres Windows Update for Business](windows-update-for-business-configure.md).
