---
title: Edition anticipée - Microsoft Intune
titlesuffix: ''
description: Edition anticipée de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/09/2019
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
ms.openlocfilehash: 0efc84da6a9efb594600b9ca33aa5eb7622c8101
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203431"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Édition anticipée pour Microsoft Intune - Janvier 2019

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

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Applications Android Entreprise <!-- 1352553  -->
Vous serez en mesure de supprimer les applications gérées Google Play depuis Microsoft Intune. Pour supprimer une application Google Play gérée, vous ouvrirez Microsoft Intune dans le portail Azure et sélectionnerez **Applications clientes** > **Applications**. À partir de la liste des applications, vous sélectionnerez les points de suspension (...) à droite de l’application Google Play gérée, puis **Supprimer** dans la liste affichée. Lorsque vous supprimez une application Google Play gérée à partir de la liste des applications, l’application Google Play gérée devient automatiquement non approuvée.

### <a name="managed-google-play-app-type----1352580---"></a>Type d’application Google Play gérée <!-- 1352580 -->
Le type d’application **Google Play géré** vous permet d’ajouter spécifiquement [les applications Google Play gérées](https://play.google.com/work/search?q=microsoft&c=apps) à Intune. En tant qu’administrateur Intune, vous pourrez désormais parcourir, rechercher, approuver, synchroniser et attribuer des applications approuvées Google Play gérées dans Intune. Vous n’aurez plus besoin d’accéder séparément à la console Google Play gérée, ni de vous authentifier de nouveau. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application**, sélectionnez le type d’application **Google Play géré**.

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Préversion de la prise en charge des appareils Android complètement managés appartenant à l’entreprise <!-- 1574342  -->
Intune prendra en charge les appareils Android complètement managés, un scénario de type « entreprise propriétaire de l’appareil » dans lequel les appareils sont étroitement gérés par le service informatique et affiliés à différents utilisateurs. Les administrateurs pourront ainsi gérer l’ensemble de l’appareil, appliquer un large éventail de contrôles de stratégie non disponibles avec les profils professionnels et imposer aux utilisateurs d’installer les applications sur la version gérée de Google Play. Pour configurer des appareils Android complètement managés, accédez à **Inscription des appareils** > **Inscription Android** > **Appareils des utilisateurs complètement managés appartenant à l’entreprise**. Veuillez noter que cette fonctionnalité est en préversion. Certaines fonctionnalités Intune, telles que les certificats, la conformité et l’Accès conditionnel, ne sont pas actuellement disponibles avec les appareils Android des utilisateurs complètement managés.

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Déploiement en ligne d’un Microsoft Store sous licence pour les applications métier <!-- 1672660  -->
Vous serez en mesure d’assigner un Microsoft Store sous licence en ligne obligatoire pour les applications métier dans le contexte d’appareil. Un Microsoft Store pour une application métier déployé de cette façon permet à l’application d’être installée pour tous les utilisateurs sur l’appareil. Seuls les appareils de bureau Windows 10 version RS4 et ultérieures sont concernés. L’option d’installation dans le contexte d’appareil est disponible dans la page d’affectation des applications clientes pour les applications sous licence en ligne MSFB.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configurer le profil pour ignorer certains écrans lors de l’exécution de l’Assistant Configuration <!-- 2276470  -->
Lors de la création d’un profil d’inscription macOS, vous serez en mesure de le configurer pour ignorer tout ou partie de la liste d’écrans suivants lorsqu’un utilisateur exécute l’Assistant Configuration :
- Migration Android
- Display Tone (Indiquer la tonalité)
- Confidentialité
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Affecter des profils Autopilot au groupe virtuel Tous les appareils <!--2715522  -->
Vous pourrez affecter des profils Autopilot au groupe virtuel Tous les appareils. Pour ce faire, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > choisissez un profil >  **Affectations** > sous **Affecter à** choisissez **Tous les appareils**. Pour plus d’informations sur les profils Autopilot, consultez [Inscrire des appareils Windows à l’aide de Windows Autopilot](enrollment-autopilot.md).

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>Personnaliser le papier peint sur les appareils iOS supervisés à l’aide d’un profil de configuration de l’appareil <!-- 2809324  -->
Lorsque vous créez un profil de configuration d’appareil pour les appareils iOS, vous serez en mesure d’autoriser ou restreindre certains paramètres dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions d’appareil** pour le type de profil. Cette mise à jour inclut de nouveaux paramètres de **Papier peint** qui permettent à un administrateur d’utiliser une image .png, .jpg ou .jpeg comme papier peint, d’afficher un aperçu de l’image et d’interdire aux utilisateurs de changer de papier peint. Les paramètres de papier peint s’appliquent uniquement aux appareils supervisés. Pour obtenir la liste des paramètres actuels, consultez [Paramètres de restriction des appareils iOS](device-restrictions-ios.md).

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifications toast pour les applications Win32 <!-- 3136566   -->
Vous pouvez supprimer l’affichage des notifications toast à l’utilisateur final par affectation d’applications. À partir d’Intune, sélectionnez **Applications clientes** > **Applications** > sélectionnez l’application > **Affectations** > **Inclure les groupes**. 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>Supprimez le partage de contacts via Bluetooth dans Restrictions d’appareil > Propriétaire de l’appareil pour Android Entreprise <!-- 3598396 -->
Lorsque vous créez un profil de restrictions d’appareil pour les appareils Android Enterprise, vous disposez d’un paramètre **Partage de contacts via Bluetooth**. Dans cette mise à jour, le paramètre **Partage de contacts via Bluetooth** sera supprimé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Restrictions d’appareil > Propriétaire de l’appareil** pour le type de profil > **Général**). 

Le paramètre **Partage de contacts via Bluetooth** n’est pas pris en charge pour la gestion du Propriétaire de l’appareil Android Enterprise. Par conséquent, la suppression de ce paramètre n’affectera aucun périphérique ni aucun client, même si ce paramètre est activé et configuré dans votre environnement.

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md).

S'applique à : Propriétaire d’appareil Android Entreprise

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises<!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie App Protection sans inscription) non inscrit, vous pourrez utiliser Google Play dans sa version gérée pour déployer des applications du Store et des applications métier auprès des utilisateurs. Plus précisément, le service informatique pourra proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle il ne sera plus nécessaire d’assouplir la posture de sécurité de appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Le kit SDK Intune App prendra en charge les clés de chiffrement 256 bits<!-- 1832174 -->
Le kit de développement logiciel (SDK) Intune App pour Android utilisera des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Le kit SDK continuera de prendre en charge les clés 128 bits pour assurer la compatibilité avec le contenu et les applications qui utilisent des versions antérieures du kit SDK.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise<!-- 1927359 -->
Sur les appareils déjà inscrits via l’Assistant Configuration avec l’une des méthodes d’inscription des appareils d’entreprise d’Apple, Intune ne prendra plus en charge le Portail d’entreprise lorsqu’il est installé manuellement par les utilisateurs finaux à partir de l’App store. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. Par ailleurs, l’écran **Identifier votre appareil** de l’application Portail d’entreprise sera bientôt obsolète.  
Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. D’autres informations sur la procédure à suivre seront données dans la documentation à venir.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Les utilisateurs non administrateurs peuvent activer BitLocker sur des appareils Windows 10 joints à Azure AD<!-- 2147379 -->
Lorsque vous activez les paramètres BitLocker sur des appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **Endpoint Protection** comme type de profil > **Chiffrement Windows**), vous ajoutez des paramètres BitLocker. Cette mise à jour comprend un nouveau paramètre BitLocker permettant aux utilisateurs standard (non administrateurs) d’activer le chiffrement. Pour voir les paramètres actuels, voir [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).


### <a name="additional-settings-for-outlook----3301182---"></a>Paramètres supplémentaires pour Outlook <!-- 3301182 -->
Vous pouvez désormais configurer des paramètres supplémentaires pour Outlook pour iOS et Android via Intune.  Les paramètres sont les suivants :
- Autoriser uniquement les comptes professionnels ou scolaires à être utilisés dans Outlook sur iOS et Android
- Déployer une authentification moderne pour Office 365 et une authentification moderne hybride pour les comptes locaux
- Utiliser `SAMAccountName` pour le champ de nom d’utilisateur dans le profil d’e-mail quand l’authentification de base est sélectionnée
- Autoriser l’enregistrement des contacts
- Configurer la fonctionnalité Infos-courrier pour les destinataires externes
- Configurer la **Boîte de réception Prioritaire**
- Imposer la biométrie pour accéder à Outlook pour iOS 
- Bloquer les images externes

> [!NOTE]
> Si vous utilisez des stratégies Intune App Protection pour gérer l’accès aux identités d’entreprise, n’activez pas la **biométrie obligatoire**. Pour plus d’informations, consultez **Exiger des informations d’identification d’entreprise pour l’accès** dans le cadre des [exigences d’accès iOS](app-protection-policy-settings-ios.md#access-settings) et des [exigences d’accès Android](app-protection-policy-settings-android.md#access-settings).

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration<!-- 3322847 -->
Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion privée. Avec cette mise à jour : Les modèles administratifs comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
Les modèles d’administration, disponibles en préversion publique, sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** >**Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et versions ultérieures**, dans **Type de profil**, choisissez **Modèles d’administration**.
La création de rapports est activée. S’applique à : Windows 10 et versions ultérieures

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Mode sombre du Portail d’entreprise Intune macOS <!-- 3300524 -->
Le portail d’entreprise Intune macOS prend désormais en charge le Mode sombre pour macOS. Lorsque vous activez le Mode sombre sur un appareil macOS 10.14 ou version ultérieure, le portail d’entreprise ajuste son apparence aux couleurs de ce mode.

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Utiliser les paramètres recommandés par Microsoft avec les lignes de base de sécurité <!-- 2055484 -->
Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur pourra créer des stratégies de sécurité directement à partir de ces lignes de base, et les déployer ensuite pour ses utilisateurs. Il pourra également personnaliser les recommandations en fonction des besoins de son organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Stratégies de protection des informations Windows déployées sans inscription de l’utilisateur <!-- 1434452 -->
Les stratégies de protection des informations Windows pourront être déployées sans que les utilisateurs MDM soient obligés d’inscrire leur appareil Windows 10. Cette configuration permet aux organisations de protéger leurs documents d’entreprise conformément à la configuration de la protection des informations Windows, tout en permettant à l’utilisateur de conserver la gestion de ses propres appareils Windows. Une fois les documents protégés par une stratégie de protection des informations Windows, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie de protection des informations Windows. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Paramètres de stratégie de protection des applications pour les données du web <!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Jeton VPP Apple utilisé par une autre gestion MDM <!-- 1488946 -->
Intune détectera et affichera des détails si un jeton du Programme d’achat en volume (VPP) Apple est utilisé à la fois par Intune et une autre gestion MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Appareils mis hors service dans le tableau de bord de conformité des appareils <!-- 1981119 -->
Dans une prochaine mise à jour, les appareils mis hors service seront retirés du tableau de bord de conformité des appareils. Cela changera vos numéros de conformité.



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Vérifier la conformité de Configuration Manager <!-- 2192052 -->
Une prochaine mise à jour va offrir un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**   >  **Windows 10**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide du paramètre Intune, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

S’applique à Windows 10 et ultérieur



## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.



