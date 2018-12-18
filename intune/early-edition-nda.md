---
title: Edition anticipée - Microsoft Intune
titlesuffix: ''
description: Edition anticipée de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
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
ms.openlocfilehash: 35298713738c666ca19d57e647412729a85bbc4a
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112831"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Édition préliminaire de Microsoft Intune – Décembre 2018

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

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises<!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie App Protection sans inscription) non inscrit, vous pourrez utiliser Google Play dans sa version gérée pour déployer des applications du Store et des applications métier auprès des utilisateurs. Plus précisément, le service informatique pourra proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle il ne sera plus nécessaire d’assouplir la posture de sécurité de appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nouvelles options de connexion automatique et de conservation automatique des règles avec des paramètres DNS sur les appareils Windows 10 (et versions ultérieures)<!-- 1333665, 2999078 -->
Sur les appareils Windows 10 (et versions ultérieures), il sera possible de créer un profil de configuration de VPN qui comportera la liste des serveurs DNS permettant de résoudre les domaines, par exemple, contoso.com. Il comprendra de nouveaux paramètres de résolution de noms (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez  **Windows 10 et versions ultérieures** comme plateforme > choisissez **VPN** comme type de profil > **Paramètres DNS** >**Ajouter**) : 

- **Connexion automatique** : lorsque ce paramètre est **Activé**, l’appareil se connecte automatiquement au VPN lorsqu’il contacte le domaine saisi, par exemple, contoso.com.
- **Persistant** : par défaut, toutes les règles de la table de stratégie de résolution de noms (NRPT) sont actives tant que l’appareil est connecté avec ce profil VPN. Lorsque ce paramètre est **Activé** sur une règle NRPT, celle-ci reste active sur l’appareil, même si la connexion VPN est interrompue ou le profil VPN supprimé. La règle est maintenue à moins d’être supprimée manuellement (avec PowerShell).

La page [Paramètres de VPN Windows 10](vpn-settings-windows-10.md) présente la liste actuelle des paramètres. 

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642-eeready---"></a>Utiliser S/MIME pour chiffrer et signer les appareils d’un utilisateur  <!-- 1333642 eeready -->
Le chiffrement S/MIME des e-mails utilisant un nouveau profil de certificat importé est désormais pris en charge (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > type de profil **Certificat PKCS importé**). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :

- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.

Pris en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Page Aide et support dans l’application Portail d’entreprise Windows<!-- 1488939 -->
Une nouvelle page sera ajoutée à l’application Portail d’entreprise Windows : la page Aide et support, qui donnera les informations de contact du support technique. Par ailleurs, les utilisateurs finaux pourront envoyer des journaux du Portail d’entreprise en cas de problème. La page comportera également une section FAQ qui leur sera utile.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utiliser la détection des réseaux approuvés pour les profils VPN sur les appareils Windows 10<!-- 1500165 -->
Avec la détection des réseaux approuvés, vous pourrez empêcher les profils VPN de créer automatiquement une connexion VPN si l’utilisateur se trouve déjà sur un réseau approuvé. Vous aurez la possibilité d’ajouter des suffixes DNS permettant la détection des réseaux approuvés sur les appareils Windows 10 (et versions ultérieures) (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **VPN** comme type de profil).
La page [Paramètres VPN Windows 10](vpn-settings-windows-10.md) liste les paramètres VPN actuels.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Le kit SDK Intune App prendra en charge les clés de chiffrement 256 bits<!-- 1832174 -->
Le kit de développement logiciel (SDK) Intune App pour iOS utilisera des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Le kit SDK continuera de prendre en charge les clés 128 bits pour assurer la compatibilité avec le contenu et les applications qui utilisent des versions antérieures du kit SDK.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Paramètres de PC partagé activés dans le profil Intune<!-- 1907917 -->
Actuellement, vous pouvez configurer les paramètres de PC partagé sur les appareils de bureau Windows 10 avec un paramètre OMA-URI personnalisé. Un nouveau profil sera ajouté pour configurer les paramètres de PC partagé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** > **Appareil multi-utilisateur partagé**).
S'applique à : Windows 10 (et versions ultérieures), Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise<!-- 1927359 -->
Intune ne gèrera plus l’application Portail d’entreprise si elle installée à partir de l’App Store, sur certains appareils. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. Par ailleurs, l’écran **Identifier votre appareil** de l’application Portail d’entreprise sera bientôt obsolète.  
Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. D’autres informations sur la procédure à suivre seront données dans la documentation à venir.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Les utilisateurs non administrateurs peuvent activer BitLocker sur des appareils Windows 10 joints à Azure AD<!-- 2147379 -->
Lorsque vous activez les paramètres BitLocker sur des appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **Endpoint Protection** comme type de profil > **Chiffrement Windows**), vous ajoutez des paramètres BitLocker. Cette mise à jour comprend un nouveau paramètre BitLocker permettant aux utilisateurs standard (non administrateurs) d’activer le chiffrement. Pour voir les paramètres actuels, voir [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-app-pin----2298397---"></a>Code PIN Intune App<!-- 2298397 -->
En tant qu’administrateur informatique, vous pourrez configurer le nombre de jours d’attente possibles avant que le code PIN Intune App de l’utilisateur final doive être modifié. Le nouveau paramètre sera accessible sur le Portail Azure en sélectionnant **Intune** > **Applications clientes** > **Stratégies App Protection** > **Créer une stratégie** > **Paramètres** > **Exigences d’accès**. Cette fonctionnalité sera disponible sur les appareils iOS et Android. Ce paramètre accepte une valeur entière positive.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>Nouveaux paramètres Windows 10 Update<!-- 2626030 2512994 -->
Pour vos boucles de mise à jour Windows 10, vous pourrez :
- restaurer les paramètres de mise à jour automatique d’origine sur un ordinateur Windows 10 fonctionnant sur la *Mise à jour d’octobre 2018* ;
- configurer un nouveau paramètre de mises à jour de logiciels permettant d’empêcher ou d’autoriser les utilisateurs à suspendre l’installation des mises à jour dans les *Paramètres* de leurs ordinateurs. 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>Les profils de messagerie iOS peuvent utiliser la signature et le chiffrement S/MIME<!-- 2662949 -->
Vous pourrez créer un profil de messagerie comportant différents paramètres, notamment des paramètres S/MIME servant à signer et à chiffrer les communications par e-mail sur les appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > **E-mail** comme type de profil).

La page [Paramètres de configuration de la messagerie iOS](email-settings-ios.md) liste les paramètres actuels.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Ignorer d’autres écrans de l’Assistant Configuration sur un appareil DEP iOS<!-- 2687509 -->
En plus des écrans que vous pouvez déjà ignorer, vous pourrez définir des appareils DEP iOS pour ignorer les écrans suivants de l’Assistant Installation quand un utilisateur inscrit l’appareil : Afficher la sonnerie, Confidentialité, Migration Android, Bouton d’accueil, iMessage et FaceTime, Intégration, Surveiller la migration, Apparence, Heure de l’écran, Mise à jour logicielle, Configuration SIM.
Pour choisir quels écrans ignorer, accédez à **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton > **Profils** > choisissez un profil > **Propriétés** > **Personnalisation de l’Assistant Configuration** > choisissez **Masquer** pour tous les écrans que vous souhaitez ignorer > **OK**.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Certains paramètres BitLocker prennent en charge l’édition Windows 10 Professionnel<!-- 2727036 -->
Vous pourrez créer un profil de configuration définissant des paramètres Endpoint Protection sur les appareils Windows 10, notamment BitLocker. Certains paramètres BitLocker prennent en charge l’édition Windows 10 Professionnel. Pour voir les paramètres actuels de l’édition Windows 10, voir [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).
Intune proposera des champs de création de rapports supplémentaires sur les appareils, notamment le fabricant Android, le modèle et le version de la mise à jour de sécurité, ainsi que le modèle iOS. Dans Intune, ces champs seront accessibles en sélectionnant **Applications clientes** > **État App Protection** et en choisissant **Rapport App Protection : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 

### <a name="intune-device-reporting-fields----2748738---"></a>Champs des rapports sur les appareils Intune <!-- 2748738 -->
Intune proposera des champs de création de rapports supplémentaires sur les appareils, notamment le fabricant Android, le modèle et le version de la mise à jour de sécurité, ainsi que le modèle iOS. Dans Intune, ces champs seront accessibles en sélectionnant **Applications clientes** > **État App Protection** et en choisissant **Rapport App Protection : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>La configuration des appareils partagés est renommée Message de l’écran de verrouillage pour les appareils iOS sur le Portail Azure<!-- 2809362 -->
Lors de la création d’un profil de configuration pour des appareils iOS, vous aurez la possibilité d’ajouter des paramètres **Configuration des appareils partagés** pour afficher un texte spécifique sur l’écran de verrouillage. Les modifications sont les suivantes : 

- Les paramètres **Configuration des appareils partagés** sur le Portail Azure sont renommés « Message de l’écran de verrouillage (mode supervisé uniquement) » (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > choisissez **Fonctionnalités de l’appareil** comme type de profil > **Message de l’écran de verrouillage**).
- Lorsque vous ajoutez des messages d’écran de verrouillage, vous pouvez insérer un numéro de série, un nom d’appareil ou toute autre valeur propre à l’appareil comme variable dans **Informations de l’étiquette**. Par exemple, vous pouvez entrer `Device name: {{device name}}` ou `Serial number is {{serial number}}` entre accolades. [Jetons iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) liste les jetons utilisables.

La page [Paramètres d’affichage des messages sur l’écran de verrouillage](shared-device-settings-ios.md) liste les paramètres actuels.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>Messages d’échec de la restriction de l’inscription plus détaillés<!-- 3111564-->
Des messages d’erreur plus détaillés seront disponibles en cas de non-respect des restrictions d’inscription. Pour voir ces messages, accédez à **Intune** > **Résoudre les problèmes** > et consultez la table des échecs d’inscription.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nouveaux paramètres de notification, d’indicateurs et de verrouillage du clavier pour les appareils des propriétaires d’appareils Android pour les entreprises<!-- 3201839 3201843 -->
Cette mise à jour comporte de nouvelles fonctionnalités pour les propriétaires d’appareils Android pour les entreprises. Pour pouvoir les utiliser, accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Android pour les entreprises** > dans **Type de profil**, choisissez **Propriétaire de l’appareil uniquement** > **Restrictions de l’appareil**.
Les nouvelles fonctionnalités incluent : 
- Désactiver l’affichage des notifications système, notamment les appels entrant, les alertes système, les erreurs système, etc.
- Suggérer d’ignorer les tutoriels de démarrage et les conseils sur les applications qui sont ouvertes pour la première fois
- Désactiver les paramètres avancés de verrouillage du clavier, notamment l’appareil photo, les notifications, le déverrouillage par empreinte digitale, etc.

Pour voir les paramètres actuels, accédez à [Paramètres de restriction des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Les appareils Android pour les entreprises des propriétaires d’appareils peuvent utiliser des connexions VPN Always On<!-- 3202194 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN Always On sur les appareils Android pour les entreprises des propriétaires d’appareils. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer le VPN Always On dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android pour les entreprises** comme plateforme > **Restrictions de l’appareil** sur Propriétaire de l’appareil uniquement > paramètres **Connectivité**. Pour voir les paramètres actuels, accédez à [Paramètres de restriction des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10<!-- 3285177 --> 
Cette mise à jour comporte un nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10. À l’aide d’un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme** , choisissez **Windows 10** > dans **Type de profil**, choisissez les paramètres **Restrictions de l’appareil** > **Général**), vous choisissez d’autoriser ou non ce paramètre.
Pour voir les paramètres actuels, accédez à [Paramètres de restriction des appareils Windows 10](device-restrictions-windows-10.md).
S'applique à : Windows 10 et versions ultérieures

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration<!-- 3322847 -->
Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion privée. Avec cette mise à jour : Les modèles administratifs comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
Les modèles d’administration, disponibles en préversion publique, sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** >**Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et versions ultérieures**, dans **Type de profil**, choisissez **Modèles d’administration**.
La création de rapports est activée. S’applique à : Windows 10 et versions ultérieures


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
- **État du connecteur** : contient des informations sur les connecteurs configurés, tels qu’Apple VPP, Windows Store pour Entreprises et les connecteurs de certificat. En fonction de leur état actuel, les connecteurs sont marqués comme *Sain*, *Avertissement* ou *Défectueux*.
- **Intégrité du service Intune** : répertorie les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office ([https://portal.office.com](https://portal.office.com)).
- **Actualités Intune** : contient des messages actifs pour votre locataire, notamment des notifications signalant que votre locataire a reçu les dernières fonctionnalités d’Intune. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office ([https://portal.office.com](https://portal.office.com)).


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


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Changer le processus de mise à jour pour les connecteurs locaux <!-- 2277554 -->
Suite aux commentaires que nous ont envoyés des clients, le mode de mise à jour des connecteurs locaux va changer. Après avoir installé initialement un connecteur local, les mises à jour se produiront automatiquement. Ce changement commence par le nouveau connecteur PFX Certificate Connector pour Microsoft Intune et s’appliquera par la suite aux autres types de connecteurs locaux. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Vérifier la conformité de Configuration Manager <!-- 2192052 -->
Une prochaine mise à jour va offrir un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**   >  **Windows 10**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide du paramètre Intune, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

S’applique à Windows 10 et ultérieur



## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.



