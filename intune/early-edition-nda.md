---
title: Edition anticipée - Microsoft Intune
titlesuffix: ''
description: Edition anticipée de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19994745a232a362d6bba0f09ed3934e492a17ed
ms.sourcegitcommit: 2f431f122ce3ee6b5d0cdb04a0b748d00f83e295
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265670"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>Édition préliminaire de Microsoft Intune - Février 2019

> [!Note]
> Notification relative à l’accord de confidentialité : Les modifications suivantes sont en cours de développement pour Intune. Ces informations sont partagées selon les termes de l’accord de confidentialité, de façon très limitée. Ne publiez aucune de ces informations sur des médias sociaux ou des sites web publics comme Twitter, UserVoice, Reddit, etc. 

**L’édition préliminaire** fournit la liste des fonctionnalités, partagée selon les termes de l’accord de confidentialité, qui seront intégrées dans les prochaines versions de Microsoft Intune. Ces informations sont fournies de manière limitée et sont susceptibles de changer. Ne tweetez pas, ne publiez sur UserVoice et ne partagez pas ces informations en dehors de votre entreprise. Certaines fonctionnalités répertoriées ici risquent de ne pas être prêtes d’ici la date limite et d’être repoussées à une version ultérieure. D’autres fonctionnalités sont en cours de test dans un pilote (version d’évaluation) pour s’assurer qu'elles sont prêtes à l'emploi. Joignez votre contact de groupe de produits Microsoft si vous avez des questions ou rencontrez des problèmes.

Cette page est mise à jour périodiquement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>Les scripts PowerShell peuvent s’exécuter dans un hôte 64 bits sur des appareils 64 bits <!-- 1862675  -->
Quand vous ajoutez un script PowerShell à un profil de configuration d’appareil, le script s’exécute toujours en 32 bits, même sur les systèmes d’exploitation 64 bits. Avec cette mise à jour, un administrateur peut exécuter le script dans un hôte PowerShell 64 bits sur des appareils 64 bits (**Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter** > **Configurer** > **Exécuter le script dans un hôte PowerShell 64 bits**).
Pour plus d’informations sur l’utilisation de PowerShell, consultez [Scripts PowerShell dans Intune](intune-management-extension.md).
S'applique à : Windows 10 et versions ultérieures

### <a name="rename-an-enrolled-windows-device----1911112----"></a>Renommer un appareil Windows inscrit <!-- 1911112  -->
Vous pouvez renommer un appareil Windows 10 inscrit (RS4 ou ultérieur). Pour cela, choisissez **Intune** > **Appareils** > **Tous les appareils** > Choisissez un appareil > **Renommer l’appareil**.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>Affecter des certificats SCEP à un appareil macOS sans utilisateur    <!-- 2340521   -->
Vous pouvez affecter des certificats SCEP (Simple Certificate Enrollment Protocol) à un appareil macOS sans utilisateur et associer le certificat à des profils Wi-Fi ou VPN. Ceci étend la prise en charge existante permettant d’[affecter des certificats à des appareils sans utilisateur qui exécutent Windows, iOS et Android](certificates-scep-configure.md#create-a-scep-certificate-profile).

### <a name="intune-conditional-access-ui-update------2432313----"></a>Mise à jour de l’interface utilisateur de l’accès conditionnel Intune   <!-- 2432313  -->
Nous apportons des améliorations à l’interface utilisateur pour l’accès conditionnel dans la console Intune. Par exemple :
- Remplacer le panneau *Accès conditionnel* d’Intune par le panneau d’Azure Active Directory. Ceci garantit que vous avez accès à la gamme complète des paramètres et des configurations pour l’accès conditionnel, qui reste une technologie d’Azure AD.
- Déplacer l’installation du *connecteur du service Exchange* dans ce qui est actuellement le panneau *Accès local*. Nous renommons aussi ce panneau en *Accès Exchange*. Cette modification va dans le sens d’une consolidation de l’endroit où vous configurez et où vous surveillez les détails relatifs à Exchange online et local.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune tirera parti des API Google Play Protect sur les appareils Android <!-- 2577355  -->
Certains administrateurs informatiques sont confrontés à un « paysage » BYOD où les téléphones mobiles des utilisateurs finaux peuvent être rootés ou jailbreakés. Ce comportement, bien que n’étant parfois pas mal intentionné, entraîne un contournement de nombreuses stratégies Intune définies pour protéger les données de l’organisation sur les appareils des utilisateurs finaux. Par conséquent, Intune permet donc la détection du rootage et du jailbreaking pour les appareils inscrits et désinscrits. Avec cette version, Intune peut désormais tirer parti des API Google Play Protect, qui s’ajoutent à nos contrôles de détection du rootage pour les appareils non inscrits. Même si Google ne partage pas l’intégralité des contrôles de détection du rootage qui sont effectués, nous pensons que ces API vont détecter les utilisateurs qui ont rooté leurs appareils pour une raison quelconque, allant de la personnalisation de l’appareil à l’obtention de mises à jour plus récentes du système d’exploitation sur des appareils plus anciens. L’accès de ces utilisateurs aux données de l’entreprise peut alors être bloqué, ou leurs comptes professionnels peuvent être supprimés des applications pour lesquelles une stratégie est activée. L’administrateur informatique dispose désormais de plusieurs mises à jour d’amélioration des rapports dans le panneau Intune App Protection : le rapport « Utilisateurs avec indicateur » montre les utilisateurs qui sont détectés via l’analyse de l’API SafetyNet de Google Play Protect, et le rapport « Applications potentiellement dangereuses » montre les applications qui sont détectées via l’analyse de l’API Verify Apps de Google. Cette fonctionnalité est disponible sur Android. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>Informations sur les applications Win32 disponibles dans le panneau Résolution des problèmes <!-- 2617342    -->
Vous pouvez collecter des fichiers journaux d’incidents pour l’installation d’une application Win32 à partir du panneau **Résolution des problèmes** d’Intune. Pour plus d’informations sur la résolution des problèmes d’installation d’une application, consultez [Résoudre les problèmes d’installation d’applications](troubleshoot-app-install.md).

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Les applications Navigateur kiosque et Navigateur Microsoft Edge peuvent s’exécuter sur les appareils Windows 10 en mode kiosque <!-- 2935135  -->
Vous pouvez utiliser des appareils Windows 10 en mode kiosque pour exécuter une application ou plusieurs applications. Cette mise à jour inclut plusieurs modifications de l’utilisation des applications de navigateur en mode kiosque, notamment :

- Ajoutez le navigateur Microsoft Edge ou le navigateur kiosque pour qu’ils s’exécutent comme applications sur l’appareil kiosque (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil).
- Appliquez une restriction à Microsoft Edge afin qu’il puisse (ou ne puisse pas) s’exécuter en mode kiosque (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **Windows 10 et ultérieur** pour la plateforme > **Restrictions de l’appareil** pour le type de profil > **Navigateur Microsoft Edge**). Quand il n’est pas exécuté en mode kiosque, les paramètres de Microsoft Edge peuvent être modifiés par les utilisateurs finaux.

Pour obtenir la liste des paramètres actuels, consultez :

- [Paramètres d’appareil Windows 10 et ultérieur pour une exécution en tant que kiosque ](kiosk-settings-windows.md)
- [Restrictions d’appareil pour le navigateur Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)

S'applique à : Windows 10 et versions ultérieures

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Affecter automatiquement des étiquettes d’étendue à des ressources créées par un administrateur avec cette étendue <!-- 3173823  -->
Quand un administrateur crée une ressource, les étiquettes d’étendue affectées à l’administrateur sont automatiquement affectées à cette nouvelle ressource.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>Nouveaux paramètres de restriction d’appareil pour les appareils iOS et macOS <!-- 3448774 -->
Vous pouvez restreindre certains paramètres et certaines fonctionnalités sur les appareils exécutant iOS et macOS (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **iOS** ou **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour ajoute des fonctionnalités et des paramètres que vous pouvez contrôler, notamment définir l’heure de l’écran, modifier les paramètres eSIM et les plans mobiles, retarder la visibilité par l’utilisateur des mises à jour logicielles, bloquer la mise en cache du contenu, etc.
Pour connaître les fonctionnalités et les paramètres actuels que vous pouvez restreindre, consultez :
- [Paramètres de restriction d’appareil iOS](device-restrictions-ios.md)
- [Paramètres de restriction d’appareil macOS](device-restrictions-macos.md)

S'applique à :
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>Le rapport des échecs d’inscription est déplacé dans le panneau Inscription des appareils <!-- 3560202 -->
Le rapport **Échecs d’inscription** est déplacé dans la section **Surveiller** du panneau **Inscription des appareils**. Deux nouvelles colonnes (Méthode d’inscription et Version du système d’exploitation) sont également ajoutées.

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>Changement de « Kiosque » en « Appareils dédiés » <!-- 3598402  -->
Pour s’aligner sur la terminologie d’Android, **Kiosque** est changé en **Appareils dédiés** sous Profils de configuration d’appareil, **Android Entreprise** > **Propriétaire de l’appareil** > **Restrictions de l’appareil**.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Les paramètres iOS de Safari et ceux du retardement de la visibilité des mises à jour logicielles par l’utilisateur sont déplacés dans l’interface utilisateur Intune <!-- 3640850, , 3803313  -->
Pour les appareils iOS, vous pouvez définir des paramètres Safari et configurer les mises à jour logicielles. Dans cette mise à jour, ces paramètres sont déplacés dans différentes parties de l’interface utilisateur Intune :

- Les paramètres Safari passent de **Safari** (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil) à **Applications intégrées**. 
- Le paramètre **Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS supervisés** (**Mises à jour logicielles** > **Mettre à jour des stratégies pour iOS**) est déplacé dans  **Restrictions de l’appareil** > **Général**.

Pour obtenir la liste des paramètres actuels, consultez [Paramètres de restriction des appareils iOS](device-restrictions-ios.md) et [Mises à jour logicielles iOS](software-updates-ios.md).

S'applique à : 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>Activation des restrictions dans les paramètres de l’appareil est renommé en Heure de l’écran sur les appareils iOS <!-- 3699164  -->
Vous pouvez configurer **Activation des restrictions dans les paramètres de l’appareil** sur les appareils iOS supervisés (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour le type de profil > **Général**). Dans cette mise à jour, ce paramètre est renommé en **Heure de l’écran (mode supervisé uniquement)**. Le comportement reste le même. Plus précisément : 

- iOS 11.4.1 et antérieur : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. 
- iOS 12.0 et ultérieur : **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil, notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 ne voient plus l’onglet Restrictions dans les paramètres de l’appareil. Ces paramètres se trouvent dans **Heure de l’écran**. 

Pour obtenir la liste des paramètres actuels, consultez [Restrictions des appareils iOS](device-restrictions-ios.md).

S'applique à : 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>Détails de l’état des applications pour les applications iOS <!-- 3761235  -->
Des nouveaux messages d’erreur d’installation d’une application ont été ajoutés et concernent les échecs suivants :
- Échec pour les applications VPP lors de l’installation sur un iPad partagé
- Échec quand l’App Store est désactivé
- Échec de la recherche d’une licence VPP pour l’application
- Échec de l’installation d’applications système avec le fournisseur MDM
- Échec de l’installation d’applications quand l’appareil est en mode perdu ou en mode kiosque
- Échec de l’installation d’applications quand l’utilisateur n’est pas connecté à l’App Store

Dans Intune, sélectionnez **Applications clientes** > **Applications** > « Nom de l’application » > **État de l’installation de l’appareil**. Les nouveaux messages d’erreur sont disponibles dans la colonne **Détails du statut**.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Déploiement en ligne d’un Microsoft Store sous licence pour les applications métier <!-- 1672660  -->
Vous serez en mesure d’assigner un Microsoft Store sous licence en ligne obligatoire pour les applications métier dans le contexte d’appareil. Un Microsoft Store pour une application métier déployé de cette façon permet à l’application d’être installée pour tous les utilisateurs sur l’appareil. Seuls les appareils de bureau Windows 10 version RS4 et ultérieures sont concernés. L’option d’installation dans le contexte d’appareil est disponible dans la page d’affectation des applications clientes pour les applications sous licence en ligne MSFB.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises<!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie App Protection sans inscription) non inscrit, vous pourrez utiliser Google Play dans sa version gérée pour déployer des applications du Store et des applications métier auprès des utilisateurs. Plus précisément, le service informatique pourra proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle il ne sera plus nécessaire d’assouplir la posture de sécurité de appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise<!-- 1927359 -->
Sur les appareils déjà inscrits via l’Assistant Configuration avec l’une des méthodes d’inscription des appareils d’entreprise d’Apple, Intune ne prendra plus en charge le Portail d’entreprise lorsqu’il est installé manuellement par les utilisateurs finaux à partir de l’App store. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. Par ailleurs, l’écran **Identifier votre appareil** de l’application Portail d’entreprise sera bientôt obsolète.  
Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. D’autres informations sur la procédure à suivre seront données dans la documentation à venir.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration<!-- 3322847 -->
Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion privée. Avec cette mise à jour : Les modèles administratifs comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
Les modèles d’administration, disponibles en préversion publique, sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** >**Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et versions ultérieures**, dans **Type de profil**, choisissez **Modèles d’administration**.
La création de rapports est activée. S’applique à : Windows 10 et versions ultérieures

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Mode sombre du Portail d’entreprise Intune macOS <!-- 3300524 -->
Le portail d’entreprise Intune macOS prend désormais en charge le Mode sombre pour macOS. Quand vous activez le Mode sombre sur un appareil macOS 10.14+, le portail d’entreprise ajuste son apparence à des couleurs reflétant ce mode.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Paramètres de stratégie de protection des applications pour les données du web <!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Jeton VPP Apple utilisé par une autre gestion MDM <!-- 1488946 -->
Intune détectera et affichera des détails si un jeton du Programme d’achat en volume (VPP) Apple est utilisé à la fois par Intune et une autre gestion MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Appareils mis hors service dans le tableau de bord de conformité des appareils <!-- 1981119 -->
Dans une prochaine mise à jour, les appareils mis hors service seront retirés du tableau de bord de conformité des appareils. Cela changera vos numéros de conformité.

## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.
