---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/25/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 21fde80ec80492957b686a66dcfe4db55894c38e
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199487"
---
# <a name="whats-new-in-microsoft-intune"></a>Nouveautés de Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Découvrez les nouveautés hebdomadaires dans Microsoft Intune. Vous pouvez également trouver les changements à venir, les [annonces importantes](#notices) et des informations sur les [versions précédentes](whats-new-archive.md). Le lancement de certaines fonctionnalités peut s’étaler sur plusieurs semaines. Ces fonctionnalités risquent de ne pas être accessibles à tous les clients la première semaine.

> [!Note]
> Pour plus d’informations sur les nouvelles fonctionnalités de gestion des appareils mobiles (MDM) hybride, consultez la page sur les [nouveautés de la gestion hybride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

**Flux RSS** : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-january-21-2019"></a>Semaine du 21 janvier 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifications toast pour les applications Win32 <!-- 3136566   -->
Vous pouvez supprimer l’affichage des notifications toast à l’utilisateur final par affectation d’applications. Dans Intune, sélectionnez **Applications clientes** > **Applications** > sélectionnez l’application > **Affectations** > **Inclure les groupes**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Mise à jour de l’IU des stratégies de protection des applications Intune <!-- 3251427  -->
Nous avons modifié les étiquettes des paramètres et des boutons d’Intune App Protection pour qu’ils soient tous plus faciles à comprendre. Quelques exemples de modifications :  
- Les contrôles **Oui** / **Non** sont principalement remplacés par des contrôles **Bloquer** / ** Autoriser** et **Désactiver** / **Activer**. Les étiquettes sont également mises à jour.  
- Les paramètres ont également été remis en forme pour qu’ils apparaissent à côté de l’étiquette correspondante dans le contrôle, ce qui facilite la navigation.   

Les paramètres par défaut et le nombre de paramètres restent identiques. Toutefois, ce changement permet à l’utilisateur de comprendre, de parcourir et d’utiliser les paramètres plus facilement pour appliquer les stratégies App Protection sélectionnées. Pour plus d’informations, consultez [Paramètres iOS](app-protection-policy-settings-ios.md) et [Paramètres Android](app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook----3301182----"></a>Paramètres supplémentaires pour Outlook <!-- 3301182  -->
Vous pouvez désormais configurer des paramètres supplémentaires pour Outlook pour iOS et Android via Intune.  Les paramètres sont les suivants : Autoriser uniquement l’utilisation de comptes professionnels ou scolaires dans Outlook, iOS et Android, Déployer l’authentification moderne pour les comptes locaux Office 365 et hybrides, Utiliser `SAMAccountName` pour le champ de nom d’utilisateur dans le profil e-mail quand l’authentification de base est sélectionnée, Autoriser l’enregistrement des contacts, Configurer des destinataires externes, Infos-courrier, Configurer **Boîte de réception Prioritaire**, Exiger la biométrie pour accéder à Outlook pour iOS, Bloquer les images externes
> [!NOTE]
> Si vous utilisez des stratégies Intune App Protection pour gérer l’accès aux identités d’entreprise, n’activez pas la **biométrie obligatoire**. Pour plus d’informations, consultez **Exiger des informations d’identification d’entreprise pour l’accès** dans les [paramètres d’accès iOS](app-protection-policy-settings-ios.md#access-settings) et les [paramètres d’accès Android](app-protection-policy-settings-android.md#access-settings).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Supprimer les applications Android Entreprise <!-- 1352553 -->
Vous pouvez supprimer des applications Google Play géré à partir de Microsoft Intune. Pour supprimer une application Google Play géré, ouvrez Microsoft Intune dans le portail Azure et sélectionnez **Applications clientes** > **Applications**. À partir de la liste des applications, sélectionnez les points de suspension (...) à droite de l’application Google Play géré, puis sélectionnez **Supprimer** dans la liste affichée. Lorsque vous supprimez une application Google Play gérée à partir de la liste des applications, l’application Google Play gérée devient automatiquement non approuvée.

#### <a name="managed-google-play-app-type----1352580---"></a>Type d’application Google Play gérée <!-- 1352580 -->
Le type d’application **Google Play géré** vous permet d’ajouter spécifiquement [les applications Google Play gérées](https://play.google.com/work/search?q=microsoft&c=apps) à Intune. En tant qu’administrateur Intune, vous pouvez désormais parcourir, rechercher, approuver, synchroniser et attribuer des applications Google Play géré approuvées dans Intune.  Vous n’avez plus besoin d’accéder séparément à la console Google Play géré, ni de vous authentifier de nouveau.  Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application**, sélectionnez le type d’application **Google Play géré**.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Utiliser les paramètres recommandés par Microsoft avec les bases de référence de la sécurité (préversion publique) <!-- 2055484   -->
Remarque : Cette fonctionnalité est toujours en cours de lancement et sera bientôt disponible.

Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur peut créer des stratégies de sécurité directement à partir de ces bases de référence, puis les déployer pour ses utilisateurs. Vous pouvez également personnaliser les recommandations en fonction des besoins de votre organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

Pour en savoir plus sur les bases de référence de la sécurité, consultez [Créer une base de référence de la sécurité Windows 10 dans Intune](security-baselines-monitor.md).

Cette fonctionnalité s’applique à : Windows 10 et versions ultérieures

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Les utilisateurs non administrateurs peuvent activer BitLocker sur des appareils Windows 10 joints à Azure AD<!-- 2147379   -->
Lorsque vous activez les paramètres BitLocker sur des appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **Endpoint Protection** comme type de profil > **Chiffrement Windows**), vous ajoutez des paramètres BitLocker. 

Cette mise à jour comprend un nouveau paramètre BitLocker permettant aux utilisateurs standard (non administrateurs) d’activer le chiffrement. 

Pour voir les paramètres, accédez à [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Vérifier la conformité de Configuration Manager <!-- 2192052  eepublished  -->
Cette mise à jour inclut un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**  >  **Windows 10 et ultérieur** > **Conformité de Configuration Manager**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide de ce paramètre, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

[Conformité de Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance) décrit ce paramètre.

S'applique à : Windows 10 et versions ultérieures

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personnaliser le papier peint sur les appareils iOS supervisés à l’aide d’un profil de configuration de l’appareil <!-- 2809324   -->
Lorsque vous créez un profil de configuration d’appareil pour des appareils iOS, vous pouvez personnaliser certaines fonctionnalités (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de **papier peint** qui permettent à un administrateur d’utiliser une image .png, .jpg ou .jpeg sur l’écran d’accueil ou l’écran de verrouillage. Ces paramètres de papier peint s’appliquent uniquement aux appareils supervisés. 

Pour obtenir la liste de ces paramètres, consultez [Paramètres des fonctionnalités d’appareil iOS](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>La fonctionnalité Kiosque Windows 10 est en disponibilité générale <!-- 3594661  -->
Dans cette mise à jour, la fonctionnalité Kiosque est en disponibilité générale sur les appareils Windows 10 et ultérieur. Pour voir tous les paramètres que vous pouvez ajouter et configurer, consultez [Paramètres kiosque pour Windows 10 (et ultérieur)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Supprimez le partage de contacts via Bluetooth dans Restrictions d’appareil > Propriétaire de l’appareil pour Android Entreprise <!-- 3598396   -->
Lorsque vous créez un profil de restrictions d’appareil pour les appareils Android Enterprise, vous disposez d’un paramètre **Partage de contacts via Bluetooth**. Dans cette mise à jour, le paramètre **Partage de contacts via Bluetooth** est supprimé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Restrictions d’appareil > Propriétaire de l’appareil** pour le type de profil > **Général**). 

Le paramètre **Partage de contacts via Bluetooth** n’est pas pris en charge pour la gestion du Propriétaire de l’appareil Android Enterprise. Par conséquent, la suppression de ce paramètre n’affectera aucun périphérique ni aucun client, même si ce paramètre est activé et configuré dans votre environnement.

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](device-restrictions-android-for-work.md).

S'applique à : Propriétaire d’appareil Android Entreprise

#### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Mise à jour de l’IU des stratégies de protection des applications Intune <!-- 3251427 -->
Nous avons modifié les étiquettes des paramètres et des boutons d’Intune App Protection pour qu’ils soient tous plus faciles à comprendre. Quelques exemples de modifications :  
- Les contrôles **Oui** / **Non** sont principalement remplacés par des contrôles **Bloquer** / ** Autoriser** et **Désactiver** / **Activer**. Les étiquettes sont également mises à jour.  
- Les paramètres ont également été remis en forme pour qu’ils apparaissent à côté de l’étiquette correspondante dans le contrôle, ce qui facilite la navigation.   

Les paramètres par défaut et le nombre de paramètres restent identiques. Toutefois, ce changement permet à l’utilisateur de comprendre, de parcourir et d’utiliser les paramètres plus facilement pour appliquer les stratégies App Protection sélectionnées. Pour plus d’informations, consultez [Paramètres iOS](app-protection-policy-settings-ios.md) et [Paramètres Android](app-protection-policy-settings-android.md).

### <a name="device-management"></a>Gestion des appareils

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Prise en charge de la réinitialisation sélective des appareils WIP sans inscription <!-- 1434452 -->
WIP-WE (Windows Information Protection Without Enrollment) permet aux clients de protéger leurs données d’entreprise sur des appareils Windows 10 sans nécessiter une inscription complète à MDM. Une fois les documents protégés par une stratégie WIP-WE, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie WIP-WE. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nouveaux journaux des opérations et possibilité d’envoyer des journaux aux services Azure Monitor <!-- 3762211  -->
Intune propose une journalisation d’audit intégrée qui assure le suivi des événements lorsque des modifications sont apportées. Cette mise à jour inclut de nouvelles fonctionnalités de journalisation, notamment les suivantes : 
- Journaux des opérations (préversion) qui présentent des détails sur les utilisateurs et les appareils inscrits, notamment les tentatives qui ont abouti et celles qui ont échoué.
- Les journaux d’audit et les journaux des opérations peuvent être envoyés à Azure Monitor, notamment aux comptes de stockage, aux hubs d’événements et à Log Analytics. Ces services vous permettent de stocker et d’utiliser des analyses comme Splunk et QRadar, ainsi que d’obtenir des visualisations de vos données de journalisation.

[Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](review-logs-using-azure-monitor.md) fournit plus d’informations sur cette fonctionnalité.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorer d’autres écrans de l’Assistant Configuration sur un appareil DEP iOS<!-- 2687509  -->
En plus des écrans que vous pouvez déjà ignorer, vous pouvez définir des appareils DEP iOS pour ignorer les écrans suivants de l’Assistant Installation quand un utilisateur inscrit l’appareil : Afficher la sonnerie, Confidentialité, Migration Android, Bouton d’accueil, iMessage et FaceTime, Intégration, Surveiller la migration, Apparence, Heure de l’écran, Mise à jour logicielle, Configuration SIM.
Pour choisir quels écrans ignorer, accédez à **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton > **Profils** > choisissez un profil > **Propriétés** > **Personnalisation de l’Assistant Configuration** > choisissez **Masquer** pour tous les écrans que vous souhaitez ignorer > **OK**.
Si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple. Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.
Le lancement de cette fonctionnalité a déjà commencé, mais elle ne sera pas disponible pour tous les clients avant quelques jours.

## <a name="week-of-january-14-2019"></a>Semaine du 14 janvier 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Préversion de la prise en charge des appareils Android complètement managés appartenant à l’entreprise <!-- 1574342  -->
Intune prend désormais en charge les appareils Android entièrement gérés, un scénario de type « entreprise propriétaire de l’appareil » dans lequel les appareils sont étroitement gérés par le service informatique et affiliés à différents utilisateurs. Les administrateurs pourront ainsi gérer l’ensemble de l’appareil, appliquer un large éventail de contrôles de stratégie non disponibles avec les profils professionnels et imposer aux utilisateurs d’installer les applications sur la version gérée de Google Play. Pour plus d’informations, consultez [Configurer l’inscription d’appareils Android entièrement gérés dans Intune](android-fully-managed-enroll.md) et [Inscrire vos appareils dédiés ou entièrement gérés](android-dedicated-devices-fully-managed-enroll.md).  Veuillez noter que cette fonctionnalité est en préversion. Certaines fonctionnalités Intune, telles que les certificats, la conformité et l’Accès conditionnel, ne sont pas actuellement disponibles avec les appareils Android des utilisateurs complètement managés.

## <a name="week-of-january-7-2019"></a>Semaine du 7 janvier 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-app-pin----2298397---"></a>Code PIN Intune App<!-- 2298397 -->
En tant qu’administrateur informatique, vous pouvez maintenant configurer le nombre de jours d’attente possibles pour un utilisateur final avant qu’il ne doive changer le code PIN d’application Intune. Le nouveau paramètre, *Réinitialisation du code PIN au bout d’un nombre de jours*, est accessible dans le portail Azure en sélectionnant **Intune** > **Applications clientes** > **Stratégies de protection des applications** > **Créer une stratégie** > **Paramètres** > **Conditions d’accès**. Disponible pour les appareils [iOS](app-protection-policy-settings-ios.md) et [Android](app-protection-policy-settings-android.md), cette fonctionnalité prend en charge une valeur entière positive.


#### <a name="intune-device-reporting-fields----2748738---"></a>Champs des rapports sur les appareils Intune <!-- 2748738 -->
Intune fournit des champs de rapport supplémentaires sur les appareils, notamment l’ID d’inscription d’application, le fabricant Android, le modèle et la version du correctif de sécurité ainsi que le modèle iOS. Dans Intune, ces champs sont disponibles quand vous sélectionnez **Applications clientes** > **État de protection de l’application**, et que vous choisissez **Rapport de protection d’application : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration<!-- 3322847 -->

Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion privée. Avec cette mise à jour :

- Les modèles d’administration comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
- Les modèles d’administration sont disponibles en préversion publique.
- Les modèles d’administration sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et ultérieur**, dans **Type de profil**, choisissez **Modèles d’administration**.
- La création de rapports est activée

Pour plus d’informations sur cette fonctionnalité, accédez à [Modèles Windows 10 pour configurer les paramètres de stratégie de groupe](administrative-templates-windows.md).

S'applique à : Windows 10 et versions ultérieures

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Utiliser S/MIME pour chiffrer et signer plusieurs appareils pour un utilisateur <!-- 1333642 -->
Cette mise à jour inclut le chiffrement S/MIME des e-mails à l’aide d’un nouveau profil de certificat importé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > type de profil **Certificat PKCS importé**). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :
- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.
Pour plus d’informations sur cette fonctionnalité, consultez [Vue d’ensemble de S/MIME pour signer et chiffrer des e-mails](certificates-s-mime-encryption-sign.md).
Pris en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nouvelles options de connexion automatique et de conservation automatique des règles avec des paramètres DNS sur les appareils Windows 10 (et versions ultérieures)<!-- 1333665, 2999078 -->
Sur les appareils Windows 10 et ultérieur, vous pouvez créer un profil de configuration VPN qui comporte la liste des serveurs DNS permettant de résoudre les domaines, par exemple contoso.com. Cette mise à jour contient de nouveaux paramètres de résolution de noms (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez  **Windows 10 et ultérieur** comme plateforme > choisissez **VPN** comme type de profil > **Paramètres DNS** >**Ajouter**) : 
- **Connexion automatique** : lorsque ce paramètre est **Activé**, l’appareil se connecte automatiquement au VPN lorsqu’il contacte le domaine saisi, par exemple, contoso.com.
- **Persistant** : par défaut, toutes les règles de la table de stratégie de résolution de noms (NRPT) sont actives tant que l’appareil est connecté avec ce profil VPN. Lorsque ce paramètre est **Activé** sur une règle NRPT, celle-ci reste active sur l’appareil, même si la connexion VPN est interrompue. La règle tient jusqu'à ce que le profil VPN soit supprimé ou jusqu'à ce que la règle soit supprimée manuellement, ce qui peut être effectuée avec PowerShell.
La page [Paramètres VPN Windows 10](vpn-settings-windows-10.md) décrit les paramètres. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utiliser la détection des réseaux approuvés pour les profils VPN sur les appareils Windows 10<!-- 1500165 -->
Avec la détection des réseaux approuvés, vous pouvez empêcher les profils VPN de créer automatiquement une connexion VPN si l’utilisateur se trouve déjà sur un réseau approuvé. Cette mise à jour vous permet d’ajouter des suffixes DNS pour activer la détection des réseaux approuvés sur les appareils exécutant Windows 10 et versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **VPN** comme type de profil).
La page [Paramètres VPN Windows 10](vpn-settings-windows-10.md) liste les paramètres VPN actuels.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gérer les appareils Windows Holographic for Business utilisés par plusieurs utilisateurs <!-- 1907917, 1063203 -->
Actuellement, vous pouvez configurer les paramètres de PC partagé sur les appareils Windows 10 et Windows Holographic for Business avec un paramètre OMA-URI personnalisé. Avec cette mise à jour, un nouveau profil est ajouté pour configurer les paramètres d’appareil partagé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Appareil multi-utilisateur partagé**).
Pour en savoir plus sur cette fonctionnalité, accédez à [Paramètres Intune pour gérer les appareils partagés](shared-user-device-settings.md).
S'applique à : Windows 10 (et versions ultérieures), Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nouveaux paramètres Windows 10 Update<!--2626030  2512994  -->
Pour vos [boucles de mise à jour Windows 10](windows-update-for-business-configure.md), vous pouvez configurer :
- **Comportement des mises à jour automatiques**  :utilisez une nouvelle option, *Rétablir les valeurs par défaut*, pour restaurer les paramètres de mise à jour automatique d’origine sur un ordinateur Windows 10 exécutant la *mise à jour d’octobre 2018*
- **Empêcher l’utilisateur de suspendre l’installation des mises à jour Windows** : configurez un nouveau paramètre sous Mises à jour logicielles qui vous permet de refuser ou permettre aux utilisateurs de suspendre l’installation des mises à jour dans les *Paramètres* de leurs ordinateurs. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>Les profils de messagerie iOS peuvent utiliser la signature et le chiffrement S/MIME<!-- 2662949 -->
Vous pouvez créer un profil de messagerie comportant différents paramètres. Cette mise à jour contient des paramètres S/MIME servant à signer et à chiffrer les communications par e-mail sur les appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > **E-mail** comme type de profil).
La page [Paramètres de configuration de la messagerie iOS](email-settings-ios.md) liste les paramètres.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Certains paramètres BitLocker prennent en charge l’édition Windows 10 Professionnel<!-- 2727036 -->
Vous pouvez créer un profil de configuration définissant des paramètres Endpoint Protection sur les appareils Windows 10, notamment BitLocker. Cette mise à jour ajoute la prise en charge de l’édition Windows 10 Professionnel pour certains paramètres BitLocker. Pour afficher ces paramètres de protection, accédez à [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>La configuration des appareils partagés est renommée Message de l’écran de verrouillage pour les appareils iOS dans le Portail Azure<!-- 2809362 -->
Lors de la création d’un profil de configuration pour des appareils iOS, vous avez la possibilité d’ajouter des paramètres **Configuration des appareils partagés** pour afficher un texte spécifique sur l’écran de verrouillage. Cette mise à jour inclut les modifications suivantes : 
- Les paramètres **Configuration des appareils partagés** sur le Portail Azure sont renommés « Message de l’écran de verrouillage (mode supervisé uniquement) » (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > choisissez **Fonctionnalités de l’appareil** comme type de profil > **Message de l’écran de verrouillage**).
- Lorsque vous ajoutez des messages d’écran de verrouillage, vous pouvez insérer un numéro de série, un nom d’appareil ou toute autre valeur propre à l’appareil comme variable dans **Informations de l’étiquette** et **Note de l’écran de verrouillage**. Par exemple, vous pouvez entrer `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` entre accolades. [Jetons iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) liste les jetons utilisables.
La page [Paramètres d’affichage des messages sur l’écran de verrouillage](shared-device-settings-ios.md) liste les paramètres.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nouveaux paramètres de restriction d’appareil App Store, affichage de document, jeux ajoutés aux appareils iOS <!-- 2827760-->
Dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions d’appareil** comme type de profil > **App Store, affichage de document, jeux**, les paramètres suivants sont ajoutés : Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés et Autoriser les applications non gérées à lire à partir de comptes de contacts gérés. Pour voir ces paramètres, consultez [Restrictions d’appareil iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nouveaux paramètres de notification, d’indicateurs et de verrouillage du clavier pour les appareils des propriétaires d’appareils Android pour les entreprises<!-- 3201839 3201843 -->
Cette mise à jour comporte de nouvelles fonctionnalités pour les propriétaires d’appareils Android pour les entreprises. Pour pouvoir les utiliser, accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Android pour les entreprises** > dans **Type de profil**, choisissez **Propriétaire de l’appareil uniquement** > **Restrictions de l’appareil**.
Les nouvelles fonctionnalités comprennent : 
- Désactiver l’affichage des notifications système, notamment les appels entrant, les alertes système, les erreurs système, etc.
- Suggérer d’ignorer les tutoriels de démarrage et les conseils sur les applications qui sont ouvertes pour la première fois
- Désactiver les paramètres avancés de verrouillage du clavier, notamment l’appareil photo, les notifications, le déverrouillage par empreinte digitale, etc. Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Les appareils Android pour les entreprises des propriétaires d’appareils peuvent utiliser des connexions VPN Always On<!-- 3202194 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN Always On sur les appareils Android pour les entreprises des propriétaires d’appareils. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer le VPN Always On dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android pour les entreprises** comme plateforme > **Restrictions de l’appareil** sur Propriétaire de l’appareil uniquement > paramètres **Connectivité**. Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10<!-- 3285177 --> 
Cette mise à jour comporte un nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10. À l’aide d’un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme** , choisissez **Windows 10** > dans **Type de profil**, choisissez les paramètres **Restrictions de l’appareil** > **Général**), vous choisissez d’autoriser ou non ce paramètre.
Pour afficher ces paramètres, accédez à [Paramètres de restriction d’appareil Windows 10](device-restrictions-windows-10.md).
S'applique à : Windows 10 et versions ultérieures


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Messages d’échec de la restriction de l’inscription plus détaillés<!-- 3111564 -->
Des messages d’erreur plus détaillés sont disponibles en cas de non-respect des restrictions d’inscription. Pour voir ces messages, accédez à **Intune** > **Résoudre les problèmes** > et consultez la table des échecs d’inscription. Pour plus d’informations, consultez la [liste des échecs d’inscription](help-desk-operators.md#configuration-policies-reference).



### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="tenant-status-dashboard-----1124854---"></a>Tableau de bord État du locataire <!-- 1124854 -->
La nouvelle [page État du locataire](tenant-status.md) fournit un emplacement unique où vous pouvez voir l’état et les détails associés de votre locataire.  Le tableau de bord est divisé en quatre zones :
- **Détails du locataire** : affiche des informations telles que le nom et l’emplacement de votre locataire, votre autorité MDM, le nombre total d’appareils inscrits dans votre locataire et le nombre de licences. Cette section liste également la version de service actuelle de votre locataire.
- **État du connecteur** : affiche des informations sur les connecteurs disponibles que vous avez configurés et peut également répertorier ceux que vous n’avez pas encore activés.  
   En fonction de leur état actuel, les connecteurs sont marqués comme Sain, Avertissement ou Non sain. Sélectionnez un connecteur pour extraire et afficher des détails ou configurer des informations supplémentaires associées.
-  **Intégrité du service Intune** : affiche des détails sur les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.
-  **Actualités Intune** : affiche les messages actifs pour votre locataire. Les messages incluent les éléments tels que des notifications quand votre locataire reçoit les dernières fonctionnalités Intune.  Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nouvelle expérience Aide et support dans le portail d’entreprise pour Windows 10 <!-- 1488939-->
La nouvelle page Aide et support du portail d’entreprise permet aux utilisateurs de résoudre les problèmes et demander de l’aide pour les problèmes liés à l’accès et aux applications. À partir de la nouvelle page, ils peuvent envoyer par e-mail des détails du journal de diagnostic et des erreurs ainsi que rechercher les informations relatives au support technique de leur organisation. Ils y trouveront également une section FAQ avec des liens vers la documentation Intune appropriée. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nouvelle expérience Aide et support pour Intune   <!-- #3307080 -->
Nous allons déployer la nouvelle expérience Aide et support sur tous les locataires au cours des prochains jours. Cette nouvelle expérience est disponible pour Intune et est accessible quand vous utilisez les panneaux Intune dans le [portail Azure](https://portal.azure.com/).
Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs. En plus de recevoir une aide spécifique à chaque problème, vous utilisez le nouveau workflow de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone. Cette nouvelle expérience remplace l’expérience Aide et support précédente incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support. Pour plus d’informations, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-apps----1081941---"></a>Balises d’étendue pour les applications <!-- 1081941 -->
Vous pouvez créer des étiquettes de délimitation afin de limiter l’accès pour les rôles et applications. Vous pouvez ajouter une étiquette de délimitation à une application afin que seules les personnes avec des rôles ayant également reçu cette étiquette de délimitation aient accès à l’application. Des étiquettes de délimitation ne peuvent pas être affectées à des applications achetées dans le cadre du Programme d’achat en volume (VPP) Apple.  Pour plus d’informations, consultez [Utiliser des étiquettes de délimitation pour filtrer les stratégies](scope-tags.md).



## <a name="week-of-december-10-2018"></a>Semaine du 10 décembre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="updates-for-application-transport-security----748318---"></a>Mises à jour pour Application Transport Security<!-- 748318 -->

Microsoft Intune prend en charge le protocole TLS (Transport Layer Security) 1.2+ pour fournir un chiffrement de qualité, garantir une meilleure sécurisation par défaut et s’aligner avec d’autres services Microsoft comme Microsoft Office 365. Pour répondre à cette exigence, les portails d’entreprise iOS et macOS vont appliquer les impératifs de la fonctionnalité ATS (Application Transport Security) mise à jour d’Apple, celle-ci nécessitant également TLS 1.2+. ATS est utilisé pour renforcer la sécurité de toutes les communications d’application via le protocole HTTPS. Ce changement impacte les clients Intune qui utilisent les applications du portail d’entreprise iOS et macOS. Pour plus d’informations, voir le [blog du support Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Le kit SDK Intune App prendra en charge les clés de chiffrement 256 bits<!-- 1832174 -->
Le kit de développement logiciel (SDK) Intune App pour Android utilise maintenant des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Le kit SDK continuera de prendre en charge les clés 128 bits pour assurer la compatibilité avec le contenu et les applications qui utilisent des versions antérieures du kit SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>La mise à jour automatique Microsoft version 4.5.0 doit être appliquée aux appareils macOS <!-- 3503442 -->
Pour continuer à recevoir des mises à jour pour le portail d’entreprise et les applications Office, les appareils macOS gérés par Intune doivent être mis à niveau à l’aide de la mise à jour automatique Microsoft 4.5.0. Il est possible que les utilisateurs disposent déjà de cette version pour leurs applications Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune nécessite macOS 10.12 ou une version ultérieure <!-- 2827778 -->
Intune nécessite désormais macOS 10.12 ou une version ultérieure. Les appareils sur lesquels est installée une version macOS antérieure à celle-ci ne peuvent pas utiliser le portail d’entreprise pour s’inscrire auprès d’Intune. Pour recevoir une assistance technique et pour profiter des nouvelles fonctionnalités, les utilisateurs doivent mettre à niveau leur appareil vers macOS 10.12 ou une version ultérieure, mais également mettre à niveau le portail d’entreprise vers la version la plus récente.

## <a name="week-of-november-26-2018"></a>Semaine du 26 novembre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Désinstallation d’applications sur des appareils iOS supervisés appartenant à l’entreprise <!-- 1281677 -->

Vous pouvez supprimer les applications de votre choix sur les appareils iOS supervisés appartenant à l’entreprise. Vous pouvez supprimer une application en ciblant des groupes d’utilisateurs ou des groupes d’appareils ayant le type d’affectation **Désinstaller**. Pour les appareils iOS personnels ou non supervisés, vous êtes toujours limité à la suppression des applications installées à l’aide d’Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Télécharger du contenu d’applications Win32 Intune<!-- 2617320 -->
Les clients Windows 10 RS3 (et versions ultérieures) téléchargent du contenu d’applications Win32 Intune à l’aide d’un composant d’optimisation de la distribution sur le client Windows 10. L’optimisation de la distribution offre la fonctionnalité pair à pair, activée par défaut. Elle peut être configurée par la stratégie de groupe et, à l’avenir, par la gestion des appareils mobiles (MDM) Intune. Pour plus d’informations, voir [Optimisation de la distribution pour Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu contextuel des applications et des appareils des utilisateurs finaux <!-- 2771453 -->
Les utilisateurs finaux peuvent désormais utiliser le menu contextuel sur l’appareil et dans les applications pour déclencher des actions courantes telles que la modification du nom d’un appareil ou la vérification de la conformité.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Définir un arrière-plan personnalisé dans l’application Managed Home Screen <!-- 3041945 -->
Nous ajoutons un paramètre permettant de personnaliser l’apparence de l’arrière-plan de l’application Managed Home Screen sur les appareils Android pour les entreprises en mode plein écran multiapplication.  Pour configurer l’**l’arrière-plan de l’URL personnalisée**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Enregistrement et application des affectations de stratégies de protection des applications <!-- 3104570 -->
Vous avez maintenant un meilleur contrôle de vos [affectations de stratégies App Protection](app-protection-policies.md#deploy-a-policy-to-users). Lorsque vous sélectionnez *Affectations* afin de définir ou de modifier les affectations d’une stratégie, vous devez **Enregistrer** votre configuration pour que la modification s’applique. Utilisez **Ignorer** pour effacer toutes les modifications apportées sans les enregistrer dans les listes Inclure et Exclure.  Comme il est obligatoire de choisir entre Enregistrer et Ignorer, seuls les utilisateurs souhaités se voient affecter une stratégie App Protection.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nouveaux paramètres du navigateur Microsoft Edge pour Windows 10 et versions ultérieures <!-- 3174639 -->
Cette mise à jour comporte de nouveaux paramètres permettant de contrôler et de gérer le navigateur Microsoft Edge sur les appareils. Pour connaître la liste de ces paramètres, voir [Restriction des appareils pour Windows 10 (et versions ultérieures)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>De nouvelles applications prennent en charge les stratégies App Protection<!-- 3330037 -->
Vous pouvez maintenant gérer les applications suivantes avec les [stratégies Intune App Protection](app-protection-policies.md) :
- Stream (iOS)
- To-Do (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Utilisez des stratégies App Protection pour protéger les données d’entreprise et en contrôler le transfert pour ces applications, comme les autres applications gérées par la stratégie Intune. Remarque : Si Flow n’apparaît pas encore dans la console, ajoutez-le lorsque vous créez ou modifiez des stratégies de protection des données. Pour cela, utilisez l’option **+ Plus d’applications** et spécifiez *l’ID d’application* Flow dans le champ d’entrée : *com.microsoft.flow* pour Android et *com.microsoft.procsimo* pour iOS.


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Les numéros de version et de build iOS et macOS sont affichés <!-- 1892471 -->
Dans **Conformité de l’appareil** > **Conformité de l’appareil**, les versions des systèmes d’exploitation iOS et macOS indiquées peuvent être utilisées dans les stratégies de conformité. Cette mise à jour comporte le numéro de build, configurable pour les deux plateformes.
Quand des mises à jour de sécurité sont publiées, Apple laisse généralement le numéro de version tel quel, mais met à jour le numéro de build. En utilisant le numéro de build dans une stratégie de conformité, vous pouvez facilement vérifier si une mise à jour des vulnérabilités est installée.
Pour utiliser cette fonctionnalité, voir les stratégies de conformité [iOS](compliance-policy-create-ios.md#device-health) et [macOS](compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Les boucles de mise à jour sont remplacées par les paramètres d’optimisation de la distribution pour Windows 10 (et versions ultérieures)<!-- 2753807 -->
L’optimisation de la distribution est un nouveau profil de configuration pour Windows 10 (et versions ultérieures). Cette fonctionnalité simplifie l’expérience de distribution des mises à jour de logiciels aux appareils de l’organisation. Cette mise à jour permet également de fournir les paramètres dans les boucles de mise à jour nouvelles et actuelles à l’aide d’un profil de configuration.
Pour configurer un profil de configuration d’optimisation de la distribution, voir [Paramètres d’optimisation de la distribution de Windows 10 (et versions ultérieures)](delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nouveaux paramètres de restriction d’appareil ajoutés aux appareils iOS et macOS <!-- 2827760 -->
Cette mise à jour comprend de nouveaux paramètres pour vos appareils iOS et macOS qui sont publiés avec iOS 12 :

**Paramètres iOS** : 
- Général : Bloquer la suppression d’applications (mode supervisé uniquement)
- Général : Bloquer le mode USB restreint (mode supervisé uniquement)
- Général : Forcer une date et une heure automatiques (mode supervisé uniquement)
- Mot de passe : Bloquer le remplissage automatique du mot de passe (mode supervisé uniquement)
- Mot de passe : Bloquer les demandes de proximité du mot de passe (mode supervisés uniquement)
- Mot de passe : Bloquer le partage de mot de passe (mode supervisé uniquement)

**Paramètres macOS** : 
- Mot de passe : Bloquer le remplissage automatique du mot de passe
- Mot de passe : Bloquer les demandes de proximité du mot de passe
- Mot de passe : Bloquer le partage de mot de passe

Pour en savoir plus sur ces paramètres, consultez les paramètres de restriction d’appareil [iOS](device-restrictions-ios.md) et [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Sélectionner les applications suivies dans la Page d’état d’inscription<!-- 2531007 -->
Vous pouvez choisir les applications à suivre sur la page d’état de l’inscription. Tant que ces applications ne sont pas installées, l’utilisateur ne peut pas utiliser l’appareil. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Rechercher un appareil Autopilot par numéro de série<!--2595788 -->
Vous pouvez maintenant rechercher des appareils Autopilot par numéro de série. Pour cela, choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > tapez un numéro de série dans la zone **Rechercher par numéro de série** > appuyez sur Entrée.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Effectuer le suivi de l’installation d’Office ProPlus <!--2620217 -->
Les utilisateurs peuvent suivre la progression de l’installation [d’Office ProPlus](apps-add-office365.md) sur la [Page d’état de l’inscription](windows-enrollment-status.md). Pour plus d’informations, voir [Configurer une page d’état de l’inscription](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertes pour l’expiration du jeton VPP ou pour le nombre insuffisant de licences du portail d’entreprise <!-- 2237572 -->
Si vous utilisez le Programme d’achat en volume (VPP) pour préprovisionner le Portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le Portail d’entreprise.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Prise en charge du Programme d’inscription des appareils macOS pour les comptes Apple School Manager <!--3006133 -->
Intune prend maintenant en charge l’utilisation du Programme d’inscription des appareils sur les appareils macOS pour les comptes Apple School Manager.  Pour plus d’informations, voir [Inscrire automatiquement des appareils macOS avec Apple School Manager ou le Programme d’inscription des appareils](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nouvelle référence SKU d’abonnement d’appareil Intune<!--3312071-->
Pour aider les entreprises à réduire le coût de la gestion des appareils, une nouvelle référence (SKU) d’abonnement basée sur les appareils est désormais disponible. Cette référence (SKU) d’appareil Intune est concédée sous licence par appareil sur une base mensuelle. Les prix varient selon le programme de licence. Vous pouvez l’obtenir directement via le portail d’administration Office ainsi que via le [Contrat Entreprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), le [Contrat de Fourniture de Produits et de Services Microsoft ](https://www.microsoft.com/licensing/mpsa/default), les [contrats Open Microsoft ](https://partner.microsoft.com/licensing/licensing-agreements) et le [fournisseur de solutions Cloud](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453).

### <a name="device-management"></a>Gestion des appareils

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Suspendre temporairement le mode kiosque sur les appareils Android pour apporter des changements <!-- 3041935 -->
Pendant que vous utilisez un appareil Android en mode kiosque multiapplication, un administrateur informatique peut être amené à effectuer des changements sur l’appareil. Cette mise à jour comporte de nouveaux paramètres de mode plein écran multiapplication permettant à un administrateur informatique de suspendre temporairement le mode plein écran à l’aide d’un code PIN et d’accéder à la totalité de l’appareil.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Activer le bouton d’accueil virtuel sur les appareils Android Entreprise en mode kiosque <!-- 3042021 -->
Un nouveau paramètre permet aux utilisateurs d’appuyer sur un bouton programmable de leur appareil pour passer de l’application Managed Home Screen à d’autres applications affectées (et inversement) sur leur appareil en mode kiosque multiapplication. Ce paramètre est particulièrement utile dans les scénarios où l’application en mode kiosque d’un utilisateur ne répond pas correctement au bouton Précédent. Vous allez pouvoir configurer ce paramètre pour les appareils Android à usage unique appartenant à l’entreprise. Pour activer ou désactiver le **bouton d’accueil virtuel**, accédez à Intune dans Portail Azure > Configuration de l’appareil. Sélectionnez un profil de configuration d’appareil, ou créez-en un autre pour modifier ses paramètres de mode kiosque.
Pour connaître les paramètres du mode plein écran, voir [Restrictions des appareils Android pour les entreprises](device-restrictions-android-for-work.md).

## <a name="week-of-november-12-2018"></a>Semaine du 12 novembre 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Prise en charge du contrôle d’accès réseau (NAC) pour Citrix SSO pour iOS <!-- 3259404 -->

Citrix a publié une mise à jour de Citrix Gateway pour permettre le contrôle d’accès réseau (NAC) pour Citrix SSO pour iOS dans Intune. Vous pouvez choisir d’inclure un ID d’appareil au sein d’un profil VPN dans Intune, puis d’envoyer (Push) ce profil à vos appareils iOS. Vous devrez installer la dernière mise à jour de Citrix Gateway pour utiliser cette fonctionnalité.

[Configurer les paramètres VPN sur les appareils iOS](vpn-settings-ios.md#base-vpn-settings) fournit plus d’informations sur l’utilisation du contrôle d’accès réseau, notamment certaines exigences supplémentaires. 

## <a name="week-of-november-5-2018"></a>Semaine du 5 novembre 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Prise en charge d’iOS 12 OAuth dans les profils de messagerie iOS <!--2155106 -->

Les profils de messagerie iOS d’Intune prennent en charge iOS 12 OAuth (Open Authorization). Pour voir cette fonctionnalité, créez un profil (**Configuration de l’appareil** > **Profils** > **Créer un profil**  >  **iOS** comme plateforme > **E-mail** comme type de profil). Vous pouvez également mettre à jour un profil de messagerie iOS existant. Si vous activez OAuth dans un profil qui est déjà déployé sur des utilisateurs, ces derniers sont invités à se réauthentifier et à retélécharger leurs e-mails.

[Profils de messagerie iOS](email-settings-ios.md) comprend davantage d’informations sur l’utilisation d’OAuth dans un profil de messagerie.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Prise en charge d’Autopilot pour les appareils joints à un domaine Azure Active Directory hybride (préversion) <!-- 1048100-->
Vous pouvez désormais configurer les appareils joints à un domaine Azure Active Directory hybride à l’aide d’Autopilot. Les appareils doivent être joints au réseau de votre organisation afin d’utiliser la fonctionnalité Autopilot hybride. Pour plus d’informations, consultez [Déployer des appareils joints à un domaine Azure AD hybride à l’aide d’Intune et de Windows Autopilot](windows-autopilot-hybrid.md).
Cette fonctionnalité va être lancée parmi la base d’utilisateurs au cours des prochains jours. Vous ne pourrez donc peut-être pas suivre ces étapes tant que la fonctionnalité n’aura pas été lancée pour votre compte.

## <a name="week-of-october-29-2018"></a>Semaine du 29 octobre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Demander un code PIN non biométrique après le délai d’expiration spécifié <!-- 1506985 -->
En demandant un code PIN non biométrique après un délai d’expiration spécifié par l’administrateur, Intune offre une sécurité renforcée pour les applications compatibles avec GAM (gestion des applications mobiles) en limitant l’utilisation de l’identification biométrique pour l’accès aux données d’entreprise. Les paramètres affectent les utilisateurs qui s’appuient sur Touch ID (iOS), Face ID (iOS), Android Biometric ou d’autres méthodes d’authentification biométriques à venir pour accéder à leurs applications compatibles APP/GAM. Ces paramètres permettent aux administrateurs Intune d’avoir un contrôle plus précis sur l’accès utilisateur, en supprimant les cas où un appareil avec plusieurs empreintes digitales ou d’autres méthodes d’accès biométriques peut révéler des données d’entreprise à un utilisateur inapproprié. Dans le portail Azure, ouvrez **Microsoft Intune**. Sélectionnez **Applications clientes** > **Stratégies de protection des applications** > **Ajouter une stratégie** > **Paramètres**. Recherchez la section **Accès** pour des paramètres spécifiques. Pour plus d’informations sur les paramètres d’accès, consultez [Paramètres iOS](app-protection-policy-settings-ios.md#access-settings) et [Paramètres Android](app-protection-policy-settings-android.md#access-settings).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Paramètres de transfert de données Intune APP sur les appareils inscrits à la GPM iOS <!-- 2244713 -->
Vous pouvez séparer le contrôle des paramètres de transfert de données d’Intune APP sur les appareils inscrits à la solution MDM pour iOS de la spécification de l’identité de l’utilisateur inscrit, également appelé UPN (nom d’utilisateur principal). Les administrateurs qui n’utilisent pas IntuneMAMUPN ne verront aucun changement de comportement. Lorsque cette fonctionnalité est disponible, les administrateurs qui utilisent IntuneMAMUPN pour contrôler le comportement du transfert de données sur les appareils inscrits doivent consulter les nouveaux paramètres et mettre à jour leurs paramètres APP si nécessaire.

#### <a name="windows-10-win32-apps----2617325---"></a>Applications Windows 10 Win32 <!-- 2617325 -->
Vous pouvez configurer vos applications Win32 pour qu’elles soient installées dans un contexte d’utilisateur individuel, au lieu d’être installées pour tous les utilisateurs de l’appareil.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Applications Windows Win32 et scripts PowerShell <!-- 2617330 -->
Les utilisateurs finaux ne sont plus obligés de se connecter à l’appareil pour installer des applications Win32 ou exécuter des scripts PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Résolution des problèmes d’installation des applications clientes <!-- 1363711 -->
Vous pouvez résoudre les problèmes d’installation des applications clientes en consultant la colonne intitulée **Installation de l’application** dans le panneau **Résoudre les problèmes**. Pour voir le panneau **Résoudre les problèmes**, accédez au portail Intune, puis sélectionnez **Résoudre les problèmes** sous **Aide et support**.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Prise en charge du contrôle d’accès réseau sur les clients VPN iOS <!-- 1333693 -->
Avec cette mise à jour, un nouveau paramètre permet d’activer le NAC (contrôle d’accès réseau) quand vous créez un profil de configuration VPN pour Cisco AnyConnect, F5 Access et Citrix SSO pour iOS. Ce paramètre permet d’inclure l’ID NAC de l’appareil dans le profil VPN. Pour le moment, il n’existe aucun client VPN, ni aucune solution partenaire NAC prenant en charge ce nouvel ID NAC. Toutefois, nous vous tiendrons informés via notre [billet de blog de support](ttps://aka.ms/iOS12_and_vpn) le moment venu.

Pour utiliser NAC, vous devez :
1. Autoriser Intune à inclure des ID d’appareil dans les profils VPN
2. Mettre à jour le logiciel/microprogramme de votre fournisseur NAC, avec l’aide directe de ce dernier

Pour plus d’informations sur ce paramètre dans un profil VPN iOS, consultez [Ajouter des paramètres VPN sur des appareils iOS dans Microsoft Intune](vpn-settings-ios.md). Pour plus d’informations sur le contrôle d’accès réseau, consultez [Intégration du NAC (contrôle d’accès réseau) avec Intune](network-access-control-integrate.md). 

S’applique à : iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Supprimer un profil de messagerie d’un appareil, même en présence d’un seul profil de messagerie<!-- 1818139 -->
Avant, vous ne pouviez pas supprimer un profil de messagerie d’un appareil *si* celui-ci était le seul profil de messagerie. Avec cette mise à jour, ce comportement change. Maintenant, vous pouvez supprimer un profil de messagerie, même si ce profil de messagerie est le seul sur l’appareil. Pour plus d’informations, consultez [Ajouter des paramètres de messagerie à des appareils à l’aide d’Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts PowerShell et AAD <!-- 2309469 -->
Les scripts PowerShell dans Intune peuvent être ciblés sur les groupes de sécurité des appareils AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nouveau paramètre par défaut « Type de mot de passe obligatoire » pour Android et Android Entreprise<!-- 2649963 -->
Quand vous créez une stratégie de conformité (**Intune** > **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android** ou **Android Entreprise** pour Plateforme > Sécurité du système), la valeur par défaut de **Type de mot de passe obligatoire** change :

De : Paramètre par défaut de l’appareil : Au moins numérique

S'applique à : Android, Android Entreprise

Pour voir ces paramètres, accédez à [Android](compliance-policy-create-android.md) et [Android Entreprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utiliser une clé prépartagée dans un profil Wi-Fi Windows 10 <!-- 2662938 -->
Via cette mise à jour, vous pouvez utiliser une clé prépartagée (PSK) avec le protocole de sécurité WPA/WPA2-Personnel afin d’authentifier un profil de configuration Wi-Fi pour Windows 10. Vous pouvez également spécifier la configuration des coûts d’une connexion réseau limitée pour les appareils dans la mise à jour d’octobre 2018 de Windows 10.

Actuellement, vous devez importer un profil Wi-Fi ou créer un profil personnalisé pour utiliser une clé prépartagée. Les paramètres actuels sont répertoriés dans [Paramètres Wi-Fi pour Windows 10](wi-fi-settings-windows.md). 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Supprimer des certificats PKCS et SCEP de vos appareils <!-- 3218390 -->
Dans certains scénarios, les certificats PKCS et SCEP restaient sur les appareils, même après le retrait d’une stratégie d’un groupe, la suppression d’un déploiement de configuration ou de conformité, ou la mise à jour administrative d’un profil SCEP ou PKCS existant. Cette mise à jour change le comportement. Il existe des scénarios où les certificats PKCS et SCEP sont supprimés des appareils et d’autres scénarios où ces certificats restent sur l’appareil. Pour en savoir plus sur ces scénarios, consultez [Supprimer des certificats SCEP et PKCS dans Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Utiliser Gatekeeper sur les appareils macOS pour évaluer la conformité <!-- 2504381 -->
Cette mise à jour inclut macOS Gatekeeper pour évaluer la conformité des appareils. Pour définir la propriété Gatekeeper, vous devez [ajouter une stratégie de conformité des appareils pour les appareils macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="enrollment-abandonment-report----1382924---"></a>Rapport d’abandon de l’inscription <!-- 1382924 -->
Un nouveau rapport contenant des informations détaillées sur les inscriptions abandonnées est disponible sous **Inscription de l’appareil** > **Surveiller**. Pour plus d’informations, consultez le [rapport d’abandon du portail d’entreprise](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nouvelle fonctionnalité Conditions d’utilisation dans Azure Active Directory <!-- 2870393 -->
Azure Active Directory comporte une fonctionnalité relative aux conditions d’utilisation que vous pouvez utiliser à la place des conditions générales Intune existantes. La fonctionnalité Conditions d’utilisation d’Azure AD offre davantage de flexibilité quant aux choix des conditions d’utilisation à afficher et au moment où elles sont affichées, une meilleure prise en charge de la localisation, un meilleur contrôle de l’affichage des conditions générales, ainsi que des fonctionnalités améliorées de création de rapports. La fonctionnalité Conditions d’utilisation d’Azure AD nécessite Azure Active Directory Premium P1, qui fait également partie de la suite Enterprise Mobility + Security E3. Pour en savoir plus, consultez l’article [Gérer les conditions générales de votre entreprise pour l’accès utilisateur](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Prise en charge du mode Device Owner pour Android <!--3188762-->
Pour l’inscription Samsung Knox Mobile, Intune prend désormais en charge l’inscription d’appareils en mode de gestion Device Owner pour Android. Les utilisateurs sur des réseaux Wi-Fi ou mobiles peuvent s’inscrire en quelques clics quand ils allument leurs appareils pour la première fois. Pour plus d’informations, consultez [Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung](android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Gestion des appareils
#### <a name="new-settings-for-software-updates------1907869---"></a>Nouveaux paramètres pour les mises à jour logicielles <!-- 1907869 -->  
- Vous pouvez désormais configurer des notifications pour informer les utilisateurs finaux des redémarrages qui doivent être effectués dans le but de finaliser l’installation des dernières mises à jour logicielles.   
- Vous pouvez désormais configurer un message d’avertissement pour les redémarrages qui seront effectués en dehors des heures de travail, ce qui convient aux scénarios BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Grouper les appareils Windows inscrits auprès d’Autopilot par ID de corrélation <!-- 2075110 -->
Intune prend désormais en charge le regroupement d’appareils Windows par ID de corrélation en cas d’inscription à l’aide d’[Autopilot pour les appareils existants](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. L’ID de corrélation est un paramètre du fichier de configuration Autopilot. Intune définit automatiquement l’[attribut d’appareil Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) pour qu’il ait la valeur « OfflineAutopilotprofile-<correlator ID> ». Cela permet de créer des groupes dynamiques Azure AD arbitraires en fonction de l’ID de corrélation par le biais de l’attribut enrollmentprofilename pour les inscriptions Autopilot hors connexion. Pour plus d’informations, consultez [Windows Autopilot pour les appareils existants](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Stratégies de protection des applications Intune <!-- 2984657 -->
Les stratégies de protection des applications Intune vous permettent de configurer divers paramètres de protection des données pour des applications protégées Intune, par exemple Microsoft Outlook et Microsoft Word. Nous avons changé l’aspect de ces paramètres pour [iOS](app-protection-policy-settings-ios.md) et [Android](app-protection-policy-settings-android.md) afin de faciliter la recherche de paramètres individuels. Il existe trois catégories pour les paramètres de stratégie :
- **Réadressage des données** - Ce groupe comprend les contrôles DLP (protection contre la perte de données), par exemple les restrictions d’opérations consistant à couper, copier, coller et enregistrer sous. Ces paramètres déterminent la manière dont les utilisateurs interagissent avec les données dans les applications.
- **Conditions d’accès** - Ce groupe contient les options de code PIN par application, qui déterminent le mode d’accès de l’utilisateur final aux applications dans un contexte professionnel.  
- **Lancement conditionnel** - Ce groupe contient des paramètres tels que les paramètres minimum du système d’exploitation, la détection d’appareils jailbreakés/rootés, ainsi que les périodes de grâce hors connexion.  
  
La fonctionnalité des paramètres ne change pas, mais il est plus facile de les trouver quand vous utilisez le flux de création de stratégies.

### <a name="intune-apps"></a>Applications Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune prend en charge une taille maximale de package de 8 Go pour les applications métier <!-- 1727158 -->
Intune a augmenté la taille maximale de package à 8 Go pour les applications métier. Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Ajouter une image de marque personnalisée pour l’application Portail d’entreprise <!-- 1916266 -->
En tant qu’administrateur Microsoft Intune, vous pouvez charger une image de marque personnalisée, qui est affichée en tant qu’image d’arrière-plan dans la page de profil de l’utilisateur au sein de l’application Portail d’entreprise iOS. Pour plus d’informations sur la configuration de l’application Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune conservera la langue localisée d’Office lors de la mise à jour d’Office sur les ordinateurs des utilisateurs finaux <!-- 2971030 -->
Quand Intune installe Office sur les machines de vos utilisateurs finaux, ceux-ci obtiennent automatiquement les mêmes modules linguistiques que ceux qu’ils avaient avec les installations .MSI Office précédentes. Pour plus d’informations, consultez [Assigner des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nouvelle expérience utilisateur de support Intune dans le portail de Gestion des appareils Microsoft 365 <!-- 3076965 -->
Nous lançons une nouvelle expérience utilisateur d’aide et de support pour Intune dans le [portail de Gestion des appareils Microsoft 365]( http://devicemanagement.microsoft.com). Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs.  

En plus de recevoir une aide spécifique à chaque problème, vous pouvez également utiliser le nouveau flux de travail de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone.  

Pour les clients concernés par le lancement, cette nouvelle expérience utilisateur remplace l’expérience actuelle d’aide et de support incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support.  

*Cette nouvelle expérience utilisateur d’aide et de support est en cours de lancement sur certains locataires. Elle est disponible dans le portail de gestion des appareils. Les participants à cette nouvelle expérience sont choisis au hasard parmi les locataires Intune disponibles. De nouveaux locataires vont être ajoutés au fur et à mesure que nous étendrons le lancement.*  

Pour plus d’informations, consultez [Expérience Aide et support](get-support.md#help-and-support-experience) dans Guide pratique pour obtenir un support technique pour Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Module PowerShell pour Intune – Préversion disponible <!-- 951068 -->
Un nouveau module PowerShell, qui offre une prise en charge de l’API Intune via Microsoft Graph, est désormais disponible en préversion sur [GitHub]( https://aka.ms/intunepowershell). Pour plus d’informations sur l’utilisation de ce module, consultez le fichier README à cet emplacement. 


## <a name="week-of-october-15-2018"></a>Semaine du 15 octobre 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Demande du code PIN lorsque vous changez vos empreintes digitales ou votre Face ID sur un appareil iOS <!-- 2637704  -->
Les utilisateurs sont maintenant invités à entrer un code PIN après avoir apporté des changements biométriques sur leur appareil iOS. Cela inclut les changements apportés aux empreintes digitales ou au Face ID. Le délai de la demande dépend de la configuration du délai d’attente *Revérifier les conditions d’accès requises après (minutes)*.  Si aucun code PIN n’est défini, l’utilisateur est invité à en configurer un. 
 
Cette fonctionnalité est uniquement disponible pour iOS et nécessite la participation d’applications qui intègrent le SDK d’application Intune pour iOS 9.0.1 ou version ultérieure. L’intégration du SDK est nécessaire afin que le comportement puisse être ajouté aux applications ciblées. Cette intégration se produit en continu et repose sur les équipes d’application spécifiques. Certaines applications participantes incluent WXP, Outlook, Managed Browser et Yammer.


## <a name="week-of-october-1-2018"></a>Semaine du 1er octobre 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Accès aux propriétés de profil de clé à l’aide de l’application de portail d’entreprise <!-- 772203 -->
Les utilisateurs finaux peuvent désormais accéder aux propriétés et aux actions de compte de clé, comme la réinitialisation de mot de passe, à partir de l’application Portail d’entreprise. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Les claviers tiers peuvent être bloqués par des paramètres APP sur iOS <!-- 1248481 -->
Sur les appareils iOS, les administrateurs Intune peuvent bloquer l’utilisation de claviers tiers lors de l’accès à des données de l’entreprise dans des applications protégées par une stratégie. Quand la stratégie de protection des applications (APP, Application Protection Policy) est configurée pour bloquer les claviers tiers, l’utilisateur de l’appareil reçoit un message la première fois qu’il interagit avec les données de l’entreprise en utilisant un clavier tiers. Toutes les options autres que celles du clavier natif sont bloquées et les utilisateurs de l’appareil ne les voient pas. La boîte de message ne s’affiche qu’une seule fois aux utilisateurs. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Accès de compte utilisateur aux applications Intune sur les appareils iOS et Android managés <!-- 1248496 -->
En tant qu’administrateur Microsoft Intune, vous pouvez contrôler les comptes d’utilisateur qui sont ajoutés aux applications Microsoft Office sur les appareils managés. Vous pouvez limiter l’accès uniquement aux comptes d’utilisateur professionnels autorisés, et bloquer les comptes personnels sur les appareils inscrits. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Stratégie de configuration d’application Outlook pour iOS et Android <!--1828527 -->
Vous pouvez maintenant créer une stratégie de configuration d’application Outlook pour iOS et Android pour les utilisateurs locaux qui utilisent de l’authentification de base avec le protocole ActiveSync. Des paramètres de configuration supplémentaires sont ajoutés au fur et à mesure qu’ils seront activés pour l’application Outlook pour iOS et Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Modules linguistiques Office 365 Pro Plus <!-- 1833450 -->
En tant qu’administrateur Intune, vous pouvez déployer des langues supplémentaires pour les applications Office 365 Pro Plus gérées par le biais d’Intune. La liste des langues disponibles inclut le **Type** du module linguistique (principal, partiel et de vérification). Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application** du panneau **Ajouter une application**, sélectionnez **Windows 10** sous la **Suite Office 365**. Sélectionnez **Langues** dans le panneau **Paramètres de la suite d’applications**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensions de fichier des applications métier Windows <!-- 1884873 -->
Les extensions de fichier des applications métier Windows sont désormais *.msi*, *.appx*, *.appxbundle*, *.msix* et *.msixbundle*. Vous pouvez ajouter une application dans Microsoft Intune en sélectionnant **Applications clientes** > **Applications** > **Ajouter**. Le volet **Ajouter une application** s’affiche et vous permet de sélectionner le **Type d’application**. Pour les applications métier Windows, sélectionnez **Métier** comme type d’application, sélectionnez **Fichier de package d’application**, puis entrez un fichier d’installation avec l’extension appropriée.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Déploiement d’applications Windows 10 à l’aide d’Intune <!-- 2309001 -->
S’appuyant sur la prise en charge existante des applications métier et des applications Microsoft Store pour Entreprises, les administrateurs peuvent utiliser Intune pour déployer la plupart des applications existantes de leur organisation sur les utilisateurs finaux d’appareils Windows 10. Les administrateurs peuvent ajouter, installer et désinstaller des applications pour les utilisateurs de Windows 10 dans un large éventail de formats, tels que les fichiers MSI, Setup.exe ou MSP. Intune évaluera les règles de spécification avant le téléchargement et l’installation, et informera les utilisateurs finaux de l’état ou des exigences de redémarrage par le biais du Centre de maintenance de Windows 10. Cette fonctionnalité permettra aux organisations intéressées de faire basculer cette charge de travail vers Intune et le cloud. Cette fonctionnalité est actuellement en préversion publique, et nous prévoyons d’y ajouter de nouvelles capacités significatives dans les prochains mois. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu contextuel des applications et des appareils des utilisateurs finaux <!-- 2771453 -->
Les utilisateurs finaux peuvent désormais utiliser le menu contextuel sur un appareil et des applications pour déclencher des actions courantes comme le renommage d’un appareil ou de vérification de la conformité. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Raccourcis clavier du Portail d’entreprise Windows <!-- 2771518 -->
Les utilisateurs finaux peuvent désormais déclencher des actions d’application et d’appareil dans le Portail d’entreprise Windows à l’aide de raccourcis clavier (accélérateurs).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Créer des suffixes DNS dans les profils de configuration VPN sur les appareils exécutant Windows 10 <!-- 1333668 -->
Lorsque vous créez un profil de configuration d’appareil VPN (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **VPN** pour le type de profil), vous entrez des paramètres DNS. Avec cette mise à jour, vous pouvez également entrer plusieurs **suffixes DNS** dans Intune. Lorsque vous utilisez des suffixes DNS, vous pouvez rechercher une ressource réseau à l’aide de son nom court, au lieu du nom de domaine complet (FQDN). Cette mise à jour vous permet également de modifier l’ordre des suffixes DNS dans Intune.
Les paramètres DNS actuels sont répertoriés dans [Paramètres VPN Windows 10](vpn-settings-windows-10.md#dns-settings).
S'applique à : Appareils Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Prise en charge de VPN AlwaysOn pour les profils professionnels d’entreprise Android <!-- 1333705 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN AlwaysOn sur les appareils d’entreprise Android avec des profils professionnels managés. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer un VPN AlwaysOn on dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Restrictions d’appareil** > **Connectivité**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Émettre des certificats SCEP aux appareils sans utilisateur <!-- 1744554 -->
Actuellement, les certificats sont émis aux utilisateurs. Avec cette mise à jour, vous pouvez émettre des certificats SCEP pour des appareils, notamment des appareils sans utilisateur comme les appareils kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Certificat SCEP** pour le profil). Autres mises à jour :
- La propriété **Objet** dans un profil SCEP est maintenant une zone de texte personnalisée et peut inclure de nouvelles variables. 
- La propriété **Autre nom de l'objet (SAN)** dans un profil SCEP est désormais un format de tableau et peut inclure de nouvelles variables. Dans le tableau, un administrateur peut ajouter un attribut et indiquer la valeur dans une zone de texte personnalisée. Le SAN prendra en charge les attributs suivants : 
  - DNS
  - Adresse de messagerie
  - UPN

  Ces nouvelles variables peuvent être ajoutées avec du texte statique dans une zone de texte de valeur personnalisée. Par exemple, l’attribut DNS peut être ajouté en tant que `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Les accolades, les points-virgules et les barres verticales « { } ; | » ne fonctionnent pas dans le texte statique du SAN. Les accolades ne doivent encadrer qu’une des nouvelles variables de certificat d’appareil acceptées pour `Subject` ou `Subject alternative name`. 

Nouvelles variables de certificat d’appareil :  

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

S'applique à : Windows 10 (et versions ultérieures) et iOS, compatible avec le Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Verrouiller à distance des appareils non conformes <!-- 2064495 -->
Si un appareil n’est pas conforme, vous pouvez créer une action dans la stratégie de conformité qui verrouille l’appareil à distance. Dans Intune > **Conformité de l’appareil**, créez une stratégie ou sélectionnez une stratégie existante > **Propriétés**. Sélectionnez **Actions en cas de non-conformité** > **Ajouter** et choisissez de verrouiller l’appareil à distance.
Pris en charge sur : 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 et versions ultérieures 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Améliorations de profil Kiosk Windows 10 et versions ultérieures dans le portail Azure <!-- 2748224 -->
Cette mise à jour comprend les améliorations suivantes du profil de configuration d’appareil Windows 10 Kiosk (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Préversion Kiosk** pour le type de profil) : 
- Actuellement, vous pouvez créer plusieurs profils kiosk sur le même appareil. Avec cette mise à jour, Intune ne prendra en charge qu’un seul profil kiosk par appareil. Si vous avez toujours besoin de plusieurs profils kiosk sur un seul appareil, vous pouvez utiliser un URI personnalisé.
- Dans un profil **Kiosque multi-application**, vous pouvez sélectionner la taille de la vignette d’application et l’ordre de **présentation du menu Démarrer** dans la grille de l’application. Si vous préférez avoir plus de personnalisation, vous pouvez continuer à charger un fichier XML.
- Les paramètres Navigateur Kiosk sont déplacés dans les paramètres **Kiosk**. Actuellement, les paramètres **Navigateur web Kiosk** ont leur propre catégorie dans le portail Azure.
S'applique à : Windows 10 et versions ultérieures




### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Appliquer le profil Autopilot à des appareils Win 10 inscrits qui ne sont pas encore enregistrés dans Autopilot <!-- 1558983 -->
Vous pouvez appliquer des profils Autopilot à des appareils Win 10 inscrits qui n’ont pas encore été enregistrés dans Autopilot. Dans le profil Autopilot, choisissez l’option **Convertir tous les appareils ciblés vers Autopilot** pour enregistrer automatiquement les appareils non Autopilot dans le service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures. Lorsque l’appareil est désinscrit et réinitialisé, Autopilot le provisionne.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Créer et attribuer plusieurs profils Page d’état d’inscription aux groupes Azure AD <!-- 2526564 -->
Vous pouvez maintenant [créer et attribuer](windows-enrollment-status.md) plusieurs profils Page d’état d’inscription aux groupes Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migration du Programme d’inscription des appareils vers Apple Business Manager (ABM) dans Intune <!--2748613-->
Apple Business Manager (ABM) fonctionne dans Intune. Vous pouvez donc mettre à niveau votre compte du Programme d’inscription des appareils (DEP) vers ABM. Le processus est identique dans Intune. Pour mettre à niveau votre compte Apple de DEP vers ABM, accédez à [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Onglets des alertes et de l’état des inscriptions sur la page de présentation de l’inscription des appareils <!--2748656-->
Les alertes et les échecs d’inscription apparaissent maintenant sous des onglets distincts sur la page de présentation de l’inscription des appareils.

### <a name="device-management"></a>Gestion des appareils

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restreindre les applications et bloquer l’accès aux ressources d’entreprise sur les appareils Android <!-- 2451462  -->  
Dans **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android**  >  **Sécurité du système**, il existe un nouveau paramètre dans la section *Sécurité de l’appareil* nommé **Applications restreintes**. Le paramètre **Applications restreintes** utilise une stratégie de conformité pour bloquer l’accès aux ressources d’entreprise si certaines applications sont installées sur l’appareil. L’appareil est considéré comme non conforme jusqu’à ce que les applications restreintes soient supprimées de l’appareil.
S'applique à : 
- Android




## <a name="week-of-september-24-2018"></a>Semaine du 24 septembre 2018

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Centre d’administration Gestion des appareils Microsoft 365 <!-- 3078424 -->
L’une des promesses de Microsoft 365 est la simplification de l’administration, et au fil des années nous avons intégré les services Microsoft 365 backend pour fournir des scénarios de bout en bout tels que l’accès conditionnel Intune et Azure AD. Le nouveau [Centre d’administration Microsoft 365](http://devicemanagement.microsoft.com) est l’endroit où consolider, simplifier et intégrer l’expérience d’administration. L’espace de travail spécialisé pour la gestion des appareils offre un accès aisé à toutes les tâches et les informations de gestion des appareils et des applications dont votre organisation a besoin. Nous pensons qu’il deviendra l’espace de travail cloud principal pour les équipes d’utilisateurs finaux d’enterprise.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Prise en charge de plus d’autorités de certification tierces <!-- 3093107 -->
En utilisant le protocole SCEP (Simple Certificate Enrollment Protocol), vous pouvez maintenant émettre de nouveaux certificats et renouveler des certificats sur les appareils mobiles à l’aide de Windows, iOS, Android et macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Prise en charge par Intune d’iOS 10 et versions ultérieures <!-- 2454656 -->  
L’inscription à Intune, le Portail d’entreprise et Managed Browser prennent désormais uniquement en charge les appareils iOS exécutant iOS 10 et versions ultérieures. Pour vérifier quels sont les appareils ou utilisateurs concernés dans votre organisation, accédez à Intune dans le portail Azure > **Appareils** > **Tous les appareils**. Filtrez par système d’exploitation, puis cliquez sur **Colonnes** pour afficher les détails de la version du système d’exploitation. Demandez à ces utilisateurs de mettre à niveau leurs appareils vers une version de système d’exploitation prise en charge.  

Si vous avez l’un des appareils répertoriés ci-dessous ou que vous voulez inscrire l’un de ces appareils, sachez qu’il ne prend en charge qu’iOS 9 et versions antérieures.  Pour continuer à accéder au Portail d’entreprise Intune, vous devez mettre à niveau ces appareils pour qu’ils prennent en charge iOS 10 ou version ultérieure :  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ème génération) 
* iPad mini (1ère génération)  

## <a name="week-of-september-17-2018"></a>Semaine du 17 septembre 2018

### <a name="app-management"></a>Gestion d'applications

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Supprimer la duplication des vignettes d’état de protection des applications <!-- 3083391 -->
Les vignettes **Statut de l’utilisateur pour iOS** et **Statut de l’utilisateur pour Android** étaient présentes dans les pages **Applications clientes - Vue d’ensemble** et **Applications clientes - État de protection de l’application**. Les vignettes d’état ont été supprimées de la page **Applications clientes - Vue d’ensemble** pour éviter la duplication. 

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

#### <a name="ios-automatic-app-updates----2729759---"></a>Mises à jour automatiques des applications iOS <!-- 2729759 -->
Les mises à jour automatiques des applications fonctionnent pour les applications sous licence d’appareil et d’utilisateur pour iOS version 11.0 et ultérieure.




### <a name="device-configuration"></a>Configuration des appareils

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello cible les utilisateurs et appareils <!-- 1106609 -->
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

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Contrôler le mode S sur des appareils Windows 10 et ultérieur- préversion publique <!-- 1958649 -->
Avec la mise à jour de cette fonctionnalité, vous pouvez créer un profil de configuration d’appareil qui sort un appareil Windows 10 du mode S ou empêcher les utilisateurs de sortir l’appareil du mode S. Cette fonctionnalité se trouve dans Intune > **Configuration de l’appareil** > **Profils** >  **Windows 10 et ultérieur** > **Mise à niveau d’édition et changement de mode**.
[Présentation de Windows 10 en mode S](https://www.microsoft.com/windows/s-mode) propose d’autres informations sur le mode S.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Ajout automatique du package de configuration de Windows Defender ATP au profil de configuration <!-- 2144658 -->
Lors de l’utilisation [d’ATP (Advanced Threat Protection) et de l’intégration d’appareils](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) dans Intune, vous deviez auparavant télécharger un package de configuration et l’ajouter à votre profil de configuration. Avec cette mise à jour, Intune reçoit automatiquement le package du Centre de sécurité Windows Defender et l’ajoute à votre profil.
S’applique à Windows 10 et versions ultérieures.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Exiger que les utilisateurs se connectent pendant la configuration de l’appareil <!--2311457-->
Vous pouvez maintenant définir des profils d’appareil de façon à exiger que l’appareil se connecte à un réseau avant de continuer au-delà de la page Réseau lors de la configuration de Windows 10. Tant que cette fonctionnalité est en préversion, vous avez besoin de Windows Insider build 1809 ou ultérieure pour utiliser ce paramètre.
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).


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
S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilisation de licences d’appareil VPP pour préprovisionner le portail d’entreprise lors d’une inscription DEP <!-- 1608345 -->
Vous pouvez maintenant utiliser des licences d’appareil du programme d’achat en volume (VPP, Volume Purchase Program) pour préprovisionner le portail d’entreprise pendant les inscriptions au Programme d’inscription des appareils (DEP, Device Enrollment Program). Pour ce faire, quand vous [créez ou modifiez un profil d’inscription](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), spécifiez le jeton VPP que vous souhaitez utiliser pour installer le portail d’entreprise. Assurez-vous que votre jeton n’expire pas et que vous avez suffisamment de licences pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune pousse le Portail d’entreprise de l’App Store à la place (un identifiant Apple vous sera demandé).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmation obligatoire pour supprimer un jeton VPP utilisé pour le préprovisionnement du portail d'entreprise <!-- 2237634 -->
Une confirmation est maintenant obligatoire pour supprimer un jeton VPP (Volume Purchase Program) si celui-ci est utilisé pour approvisionner préalablement le portail d’entreprise lors d’une inscription DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloquer les inscriptions d’appareils personnels Windows <!-- 1849498 -->
Vous pouvez [bloquer l’inscription des appareils personnels Windows](enrollment-restrictions-set.md#set-device-type-restrictions) avec la [gestion des appareils mobiles](windows-enroll.md) dans Intune. Les appareils inscrits avec [l’agent de PC Intune](manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité. Cette fonctionnalité sera déployée dans les prochaines semaines et il est possible que vous ne la voyiez pas immédiatement dans l’interface utilisateur.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Spécifier des modèles de nom d’ordinateur dans un profil Autopilot <!--1849855-->
Vous pouvez [spécifier un modèle de nom d’ordinateur](enrollment-autopilot.md#create-an-autopilot-deployment-profile) pour générer et définir le [nom de l’ordinateur](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) lors de l’inscription Autopilot. S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Pour les profils Windows Autopilot, masquer les options de changement de compte dans la page de connexion de l’entreprise et la page d’erreur de domaine <!--1901669 -->
De [nouvelles options de profil Windows Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) permettent aux administrateurs de masquer les options de changement de compte sur les pages de connexion et d’erreur de domaine de l’entreprise. Pour masquer ces options, il est nécessaire de configurer la marque de société dans Azure Active Directory. S’applique : au build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent (dans la préversion).



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
- Un langage plus convivial, avec moins de jargon technique
- La possibilité de partager des liens directs vers les applications
- Des performances améliorées pour les grands catalogues d’applications
- Accessibilité accrue pour tous les utilisateurs  

La [documentation du site web Portail d’entreprise Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) a été mise à jour pour refléter ces modifications. Pour voir un exemple des améliorations de l’application, consultez [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Détection de jailbreak améliorée dans les rapports de conformité<!-- 2198738 -->
Les états du paramètre de détection de jailbreak améliorée apparaissent désormais dans les rapports de conformité de la console d’administration.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-policies---1081974---"></a>Balises d’étendue pour les stratégies <!--1081974 -->
Vous pouvez [créer des étiquettes de délimitation](scope-tags.md) pour limiter l’accès aux ressources Intune. Ajoutez une balise d’étendue à une attribution de rôle, puis la balise d’étendue à un profil de configuration. Le rôle a uniquement accès aux ressources avec des profils de configuration qui ont des balises d’étendue correspondantes (ou aucune balise d’étendue).

## <a name="week-of-august-14-2018"></a>Semaine du 14 août 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Prise en charge de macOS pour le Programme d’inscription des appareils Apple <!-- 747651 -->
Intune prend maintenant en charge l’inscription d’appareils macOS dans le Programme d’inscription des appareils (DEP) Apple. Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils d’Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Semaine du 23 juillet 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Prise en charge des applications métier pour macOS <!-- 1895847 -->
Microsoft Intune permet aux applications métier macOS d’être déployées en mode **Obligatoire** ou **Disponible avec inscription**. Pour les utilisateurs finaux, les applications peuvent être déployées en mode **Disponible** à l’aide du Portail d’entreprise pour macOS ou du [site web Portail d’entreprise](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Prise en charge des applications intégrées iOS pour le mode plein écran <!-- 2051098 -->
En plus des applications du Store et des applications gérées, vous pouvez maintenant sélectionner une application intégrée (par exemple, Safari) qui s’exécute en mode plein écran sur un appareil iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modifier vos déploiements d’applications Office 365 Pro Plus <!-- 2150145 -->
En tant qu’administrateur Microsoft Intune, vous avez une plus grande capacité de modification de vos déploiements d’applications Office 365 Pro Plus. En outre, vous n’avez plus à supprimer vos déploiements pour modifier des propriétés de la suite. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications**. Dans la liste des applications, sélectionnez votre suite Office 365 Pro Plus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>SDK d’application Intune pour Android mis à jour disponible <!-- 2744271-->

Une version mise à jour du SDK d’application Intune pour Android est disponible pour prendre en charge la version Android P. Si vous êtes un développeur d’applications et que vous utilisez le SDK Intune pour Android, vous devez installer la version mise à jour du SDK d’application Intune pour garantir que les fonctionnalités Intune au sein de vos applications Android continuent de fonctionner comme prévu sur les appareils Android P. Cette version du SDK d’application Intune fournit un plug-in intégré qui effectue les mises à jour du Kit SDK. Vous n’avez pas besoin de réécrire le code existant qui est intégré. Pour plus d’informations, consultez [SDK Intune pour Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si vous utilisez l’ancien style de génération de badge pour Intune, nous vous recommandons d’utiliser l’icône porte-documents. Pour plus d’informations sur la personnalisation, consultez [ce référentiel GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Créer une stratégie de conformité des appareils à l’aide de paramètres de pare-feu sur ses appareils macOS <!-- 1497640 -->
Quand vous créez une stratégie de conformité macOS (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : macOS** > **Sécurité du système**), de nouveaux paramètres **Pare-feu** sont disponibles : 

- **Pare-feu** : configurez la façon dont les connexions entrantes sont traitées dans votre environnement.
- **Connexions entrantes** : vous pouvez **bloquer** toutes les connexions entrantes, à l’exception de celles nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage.
- **Mode furtif** : vous pouvez **activer** le mode furtif pour empêcher l’appareil de répondre aux requêtes de sondage. L’appareil continue de répondre aux requêtes entrantes des applications autorisées.

S’applique à : macOS 10.12 et versions ultérieures

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nouveau profil de configuration d’appareils Wi-Fi pour Windows 10 et ultérieur <!-- 1879077 -->
Actuellement, vous pouvez importer et exporter des profils Wi-Fi à l’aide de fichiers XML. Cette mise à jour vous permet de créer un profil de configuration d’appareils Wi-Fi directement dans Intune, tout comme dans certaines autres plateformes.

Pour créer le profil, ouvrez **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Wi-Fi**. 

S’applique à Windows 10 et versions ultérieures.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosque (obsolète) est grisé et ne peut pas être modifié. <!-- 2149998 -->
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
- **Avant** : *Cet appareil n’a pas contacté le service Intune dans l’intervalle de temps spécifié par votre administrateur informatique. Pour résoudre ce problème, ouvrez l’application Portail d’entreprise sur votre appareil et cliquez sur le bouton Vérifier la conformité.*
- **Après** : *Votre appareil ne s’est pas connecté à votre organisation depuis un certain temps. Pour rétablir la connexion, ouvrez l’application Portail d’entreprise sur votre appareil, puis appuyez sur Vérifier les paramètres de votre appareil.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Révoquer une licence d’application VPP iOS <!-- 1863797 -->
En tant qu’administrateur, vous pouvez récupérer une licence d’application VPP iOS attribuée à un utilisateur ou un appareil. Désinstaller une application VPP iOS vous permet également de récupérer la licence de l’application. Avant de désinstaller l’application, l’utilisateur ou l’appareil doit être supprimé du groupe sur lequel elle est ciblée. La suppression de l’utilisateur ou de l’appareil du groupe permet d’éviter une réinstallation de l’application. Une fois ces étapes terminées, vous pouvez choisir d’attribuer la licence de l’application à un autre utilisateur ou appareil. Pour plus d’informations sur les licences d’application VPP iOS, consultez [Gérer les applications iOS achetées en volume dans Microsoft Intune](vpp-apps-ios.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Sélectionnez les catégories d’appareils en utilisant les paramètres Accès scolaire ou professionnel <!-- 1058963 eenotready --> 
Si vous avez activé le [mappage de groupe d’appareils](https://docs.microsoft.com/intune/device-group-mapping), les utilisateurs de Windows 10 seront désormais invités à sélectionner une catégorie d’appareils après l’inscription via le bouton **Se connecter** situé dans **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utiliser SamAccountName comme nom d’utilisateur de compte pour les profils de messagerie <!-- 1500307 -->
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
Lorsque vous créez une stratégie de conformité d’appareil (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : Windows 10 et versions ultérieures** > **Paramètres** > **Sécurité système**), de nouvelles options sont disponibles sous **[Sécurité de l’appareil ](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**  : 
- **Antivirus** : quand la valeur est définie sur **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 
- **Logiciel anti-espion** : quand la valeur est définie sur **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. 

S'applique à : Windows 10 et versions ultérieures 

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

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Prise en charge mobile Microsoft Edge pour les stratégies de protection des applications Intune <!-- 1817882 -->

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

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Prise en charge des profils de VPN Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
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

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Prise en charge de l’inscription Windows Autopilot sans authentification utilisateur <!-- 1165118 -->
Intune prend désormais en charge l’inscription Windows Autopilot sans authentification utilisateur. Il s’agit d’une nouvelle option dans le profil de déploiement Windows Autopilot, « Mode de déploiement Autopilot », définie sur « Déploiement autonome ».  L’appareil doit exécuter Windows 10 Insider Preview Build 17672 ou une version ultérieure et posséder une puce TPM 2.0 pour effectuer correctement ce type d’inscription. Dans la mesure où aucune authentification utilisateur n’est exigée, vous devez affecter cette option uniquement aux appareils sur lesquels vous avez un contrôle physique.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nouveau paramètre de langue/région lors de la configuration OOBE pour AutoPilot <!-- 1821766 -->
Un nouveau paramètre de configuration est disponible pour définir la langue et la région des profils Autopilot pendant l’expérience OOBE (Out of Box Experience). Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nouveau paramètre de configuration du clavier de l’appareil <!-- 1821768 -->
Un nouveau paramètre sera disponible pour configurer le clavier pour les profils AutoPilot pendant l’expérience OOBE. Pour voir ce nouveau paramètre, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil** > **Mode de déploiement** = **Déploiement autonome** > **Valeurs par défaut configurées**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Déplacement des profils AutoPilot vers le ciblage de groupe <!-- 1877935 -->
Des profils de déploiement AutoPilot peuvent être affectés à des groupes Azure AD contenant des appareils AutoPilot.

### <a name="device-management"></a>Gestion des appareils

#### <a name="set-compliance-by-device-location----851881----"></a>Définir la conformité par emplacement de l’appareil <!-- 851881 ! -->
Dans certains cas, vous souhaiterez peut-être limiter l’accès aux ressources d’entreprise à un emplacement spécifique, défini par une connexion réseau. Vous pouvez désormais créer une stratégie de conformité (**Conformité de l’appareil** > **Emplacements**) en fonction de l’adresse IP de l’appareil. Si l’appareil bascule en dehors de la plage IP, il ne peut plus accéder aux ressources d’entreprise.

S'applique à : Appareils Android 6.0 et ultérieur, avec l’application Portail d’entreprise mise à jour

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Empêcher l’installation d’applications et d’expériences consommateur sur les appareils AutoPilot Windows 10 Entreprise RS4 <!-- 1621980 -->
Vous pourrez empêcher l’installation d’applications et d’expériences consommateur sur vos appareils AutoPilot Windows 10 Entreprise RS4. Pour voir cette fonctionnalité, accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Plateforme** = **Windows 10 ou version ultérieure** > **Type de profil** = **Restrictions de l’appareil** > **Configurer** > **Windows à la une** > **Fonctionnalités grand public**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Désinstaller la dernière version à partir de mises à jour logicielles Windows 10 <!-- 1732948 -->
Si vous détectez un problème important sur vos machines Windows 10, vous pouvez choisir de désinstaller (restaurer) la dernière mise à jour des fonctionnalités ou la dernière mise à jour qualité. La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil. La désinstallation déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10. Pour les mises à jour des fonctionnalités en particulier, vous pouvez limiter de 2 à 60 jours la durée pendant laquelle une désinstallation de la version la plus récente peut être appliquée. Pour définir des options de désinstallation de mise à jour logicielle, sélectionnez **Mises à jour logicielles** dans le panneau **Microsoft Intune** dans le portail Azure. Sélectionnez ensuite **Anneaux de mise à jour Windows 10** dans le panneau **Mises à jour logicielles**. Vous pouvez alors choisir l’option **Désinstaller** dans la section **Vue d’ensemble**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Rechercher dans tous les appareils l’IMEI et le numéro de série <!-- 1793685 -->
Vous pouvez désormais rechercher les IMEI et les numéros de série dans le panneau Tous les appareils (l’e-mail, l’UPN, le nom de l’appareil et le nom d’administration restent disponibles). Dans Intune, choisissez **Appareils** > **Tous les appareils** > entrez votre recherche dans la zone de recherche.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Le champ de nom de gestion sera modifiable <!-- 1875989 -->
Vous pourrez maintenant modifier le champ de nom de gestion dans le panneau **Propriétés** d’un appareil. Pour modifier ce champ, choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil > **Propriétés**. Vous pouvez utiliser le champ de nom de gestion pour identifier un appareil de manière unique.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nouveau filtre Tous les appareils : Catégorie d’appareil <!-- 1878520 -->
Vous pouvez désormais filtrer la liste **Tous les appareils** par catégorie d’appareil. Pour ce faire, choisissez **Appareils** > **Tous les appareils** > **Filtre** > **Catégorie d’appareil**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Utiliser TeamViewer pour partager l’écran des appareils iOS et MacOS <!-- 1985547 -->
Les administrateurs peuvent désormais se connecter à [TeamViewer](device-profile-android-teamviewer.md) et démarrer une session de partage d’écran avec des appareils iOS et macOS. Les utilisateurs d’iPhone, iPad et macOS pourront partager leurs écrans en direct avec tout autre appareil de bureau ou portable. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Prise en charge de connecteurs Exchange multiples <!-- 2070451 -->
Vous n’êtes plus limité à un seul connecteur Microsoft Intune Exchange par locataire. Intune prend désormais en charge plusieurs connecteurs Exchange afin que vous puissiez configurer l’accès conditionnel Intune avec plusieurs organisations Exchange locales.

Avec un connecteur Exchange local Intune, vous pouvez gérer l’accès de l’appareil aux boîtes aux lettres Exchange locales en fonction de l’inscription ou non d’un appareil dans Intune et de sa conformité aux stratégies de conformité Intune. Pour configurer un connecteur, téléchargez le connecteur Exchange local Intune à partir du portail Azure et installez-le sur un serveur de votre organisation Exchange. Dans le tableau de bord Microsoft Intune, choisissez **Accès local**, puis sous **Installation**, choisissez **Connecteur Exchange ActiveSync**. Téléchargez le connecteur Exchange local et installez-le sur un serveur de votre organisation Exchange. Maintenant que vous n’êtes plus limité à un seul connecteur Exchange par client, si vous avez d’autres organisations Exchange, vous pouvez suivre le même processus pour télécharger et installer un connecteur pour chaque organisation Exchange supplémentaire.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nouveaux renseignements sur le matériel : CCID <!-- 2156657 -->
L’information CCID (Chip Card Interface Device) est désormais incluse pour chaque appareil. Pour la voir, choisissez **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel** > vérifiez sous **Détails du réseau**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Affecter tous les utilisateurs et tous les appareils en tant que groupes d’étendue <!-- 2196803 -->
Vous pouvez désormais affecter tous les utilisateurs, tous les appareils, ainsi que tous les utilisateurs et appareils dans des groupes d’étendue. Pour ce faire, choisissez **Rôles Intune** > **Tous les rôles** > **Gestionnaire de stratégie et de profils** > **Affectations**  > choisissez une affectation > **Étendue (Groupes)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Information UDID désormais incluse pour les appareils iOS et macOS <!-- 2219806 -->
Pour voir l’identificateur unique de l’appareil (UDID) pour les appareils iOS et macOS, accédez à **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel**. L’UDID est disponible uniquement pour les appareils d’entreprise (tel que défini sous **Appareils** > **Tous les appareils** > choisissez un appareil > **Propriétés** > **Propriété de l’appareil**).

### <a name="intune-apps"></a>Applications Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Amélioration de la résolution des problèmes d’installation des applications <!-- 928990 -->
Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Nous publions une préversion publique de nos fonctionnalités de résolution des problèmes d’application. Vous remarquerez sous chaque appareil un nouveau nœud appelé **Applications gérées**. Il liste les applications qui ont été distribuées via MDM Intune. À l’intérieur du nœud figure une liste d’états d’installations d’applications. Si vous sélectionnez une application, vous verrez la vue de résolution des problèmes de cette application spécifique. Dans la vue de résolution des problèmes, vous verrez le cycle de vie de bout en bout de l’application, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. De plus, si l’installation de l’application a échoué, vous verrez le code d’erreur et un message utile sur la cause de l’erreur. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Stratégies de protection des applications Intune et Microsoft Edge <!-- 1818968 -->
Le navigateur Microsoft Edge pour les appareils mobiles (iOS et Android) prend désormais en charge les stratégies de protection des applications Microsoft Intune. Les utilisateurs d’appareils iOS et Android qui se connectent avec leur compte d’entreprise Azure AD dans l’application Edge seront protégés par Intune. Sur les appareils iOS, la stratégie **Exiger un navigateur géré pour le contenu web** permet aux utilisateurs d’ouvrir des liens dans Microsoft Edge quand il est géré.

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

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Intégration des groupes Tous les utilisateurs et Tous les appareils pour l’affectation d’applications aux profils professionnels Android Entreprise <!-- 1813073 -->
Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications aux profils professionnels Android Entreprise. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune réinstalle les applications nécessaires qui sont désinstallées par les utilisateurs <!-- 1947010 -->
Si un utilisateur final désinstalle une application obligatoire, Intune la réinstalle automatiquement en moins de 24 heures au lieu d’attendre le cycle de réévaluation de 7 jours.

### <a name="device-configuration"></a>Configuration des appareils

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Le graphique des profils d’appareil et la liste d’états affichent tous les appareils contenus dans un groupe <!-- 1449153 -->
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

Pour les profils Éducation, de nouveaux paramètres sont disponibles sous la catégorie **Imprimantes** : **Imprimantes**, **Imprimante par défaut**, **Ajouter de nouvelles imprimantes**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Afficher l’ID d’appelant dans un profil personnel - Profil professionnel Android Entreprise <!--1098984 -->
Quand vous utilisez un profil personnel sur un appareil, les utilisateurs finaux ne voient pas forcément les détails relatifs à l’ID d’appelant d’un contact professionnel. 

Avec cette mise à jour, il existe un nouveau paramètre dans **Android Entreprise** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Afficher l’ID d’appelant du contact professionnel dans le profil personnel

Quand ce paramètre est activé (non configuré), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Quand ce paramètre est désactivé, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. 

S'applique à : Appareils Android v6.0 et ultérieur avec un profil professionnel Android

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nouveaux paramètres Windows Defender Credential Guard ajoutés aux paramètres Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Avec cette mise à jour, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuration de l’appareil** > **Profils** > **Endpoint Protection**) présente les paramètres suivants : 

- **Windows Defender Credential Guard** : active Credential Guard avec une sécurité basée sur la virtualisation. L’activation de cette fonctionnalité permet de protéger les informations d’identification au prochain redémarrage quand **Niveau de sécurité de plateforme avec démarrage sécurisé** et **Sécurité basée sur la virtualisation** sont activés. Les options sont les suivantes :
  - **Désactivé** : si l’option **Activé sans verrouillage** est activée dans Credential Guard, cette option désactive Credential Guard à distance.

  - **Activé avec le verrouillage UEFI** : garantit que Credential Guard ne peut pas être désactivé à l’aide d’une clé de Registre ou d’une stratégie de groupe. Pour désactiver Credential Guard après avoir utilisé ce paramètre, vous devez définir la stratégie de groupe sur « Désactivé ». Ensuite, supprimez la fonctionnalité de sécurité de chaque ordinateur, avec un utilisateur physiquement présent. Ces étapes effacent la configuration persistante dans UEFI. Tant que la configuration UEFI persiste, Credential Guard est activé.

  - **Activé sans verrouillage** : permet de désactiver Credential Guard à distance à l’aide d’une stratégie de groupe. Les appareils utilisant ce paramètre doivent exécuter au moins Windows 10 (version 1511).

Les technologies dépendantes suivantes sont automatiquement activées lors de la configuration de Credential Guard : 

  - **Activer la sécurité basée sur la virtualisation** : active la sécurité basée sur la virtualisation au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité et nécessite le démarrage sécurisé.
  - **Démarrage sécurisé avec accès direct à la mémoire** : active la sécurité basée sur la virtualisation avec le démarrage sécurisé et l’accès direct à la mémoire. La protection DMA nécessite une prise en charge matérielle et n’est activée que sur des appareils configurés correctement. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Utiliser un nom d’objet personnalisé sur le certificat SCEP <!-- 2064190 -->
Vous pouvez utiliser le nom courant **OnPremisesSamAccountName** dans un objet personnalisé sur un profil de certificat SCEP. Par exemple, vous pouvez utiliser `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Blocage des appareils photo et des captures d’écran dans les profils professionnels Android Entreprise <!-- 1098977 -->
Vous disposez de deux nouvelles propriétés de blocage au moment de configurer des restrictions d’appareil pour les appareils Android : 
- Appareil photo : bloque l’accès à tous les appareils photo de l’appareil
- Capture d’écran : bloque la capture d’écran et empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée

S’applique aux profils professionnels Android Entreprise.


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nouvelles étapes d’inscription pour les utilisateurs sur les appareils dotés de macOS High Sierra 10.13.2+ <!--1734567 -->
macOS High Sierra 10.13.2 a introduit le concept d’inscription MDM « approuvée par l’utilisateur ». Les inscriptions approuvées permettent à Intune de gérer certains paramètres sensibles au niveau sécurité. Pour plus d’informations, consultez la documentation de prise en charge d’Apple ici : https://support.apple.com/HT208019.

Les appareils inscrits à l’aide du Portail d’entreprise macOS sont considérés comme « non approuvés par l’utilisateur », sauf si l’utilisateur final ouvre les préférences système et fournit une approbation manuellement. À cette fin, le Portail d’entreprise macOS invite désormais les utilisateurs sur macOS 10.13.2 et ultérieur à approuver manuellement leur inscription à la fin du processus d’inscription. La console d’administration Intune indiquera si un appareil inscrit est approuvé par l’utilisateur.



### <a name="device-management"></a>Gestion des appareils

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>ATP (Protection avancée contre les menaces) et Intune sont entièrement intégrés <!-- 1629303 -->

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

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune s’adapte à Fluent Design System dans l’application Portail d’entreprise pour Windows 10 <!-- 1195010 -->
L’application Portail d’entreprise Intune pour Windows 10 a été mise à jour avec le [mode de navigation de Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Le long de l’application, vous remarquerez une liste verticale statique de toutes les pages de niveau supérieur. Cliquez sur n’importe quel lien pour afficher des pages et passer de l’une à l’autre rapidement. Il s’agit de la première d’une série de mises à jour que vous verrez dans le cadre de nos efforts constants pour créer une expérience plus adaptive, empathique et familière dans Intune. Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semaine du 16 avril 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Utiliser le client Cisco AnyConnect pour iOS <!-- 1333708 -->

Lorsque vous créez un profil VPN pour iOS, deux nouvelles options sont désormais disponibles : **Cisco AnyConnect** et **Cisco Legacy AnyConnect**. Les profils Cisco AnyConnect prennent en charge les versions 4.0.7x et ultérieures. Les profils VPN Cisco AnyConnect pour iOS existants se nomment **Cisco Legacy AnyConnect** et continuent de fonctionner avec Cisco AnyConnect 4.0.5x et les versions antérieures, comme c’est le cas aujourd’hui.

> [!NOTE]
> Ce changement s’applique uniquement à iOS. Il existe toujours une seule option Cisco AnyConnect pour les plateformes Android, macOS et pour les profils professionnels Android Entreprise.

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

## <a name="notices"></a>Remarques

### <a name="upcoming-password-enforcement-change-for-macos-10142-in-intune---1873216--"></a>Changement à venir au niveau de la mise en œuvre des mots de passe pour macOS 10.14.2 dans Intune <!--1873216-->
En juillet, nous avions annoncé dans le MC145129 qu’Intune prévoyait d’intégrer le nouveau paramètre Apple de changement de mot de passe à la prochaine authentification sur les appareils macOS versions 10.13 et ultérieures. Nous envisageons de déployer ce paramètre en février pour macOS 10.14.2 et ultérieur. 

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Ce changement vous concerne si vous avez ou prévoyez d’avoir des appareils macOS 10.14.2 et ultérieur. Maintenant qu’Apple propose ce paramètre de changement de mot de passe à la prochaine authentification, Intune peut forcer les utilisateurs à mettre à jour leur mot de passe pour que celui-ci soit conforme à une stratégie de mot de passe si une telle stratégie est envoyée (push). Du fait de l’ajout de cette nouvelle fonctionnalité Apple, les utilisateurs macOS reçoivent une demande de mise à jour de leur mot de passe, même si celui-ci est déjà conforme. Notez que si un mot de passe est déjà conforme et que la répétition des mots de passe n’est pas interdite, les utilisateurs finaux peuvent mettre à jour leur mot de passe existant. Les utilisateurs finaux ne voient qu’une demande de mise à jour de leur mot de passe quand ils tentent de s’authentifier ou de se connecter à leur appareil. Si vous bloquez les ressources d’entreprise tant que l’appareil n’est pas marqué comme conforme, sachez que les utilisateurs finaux sur des appareils macOS 10.14.2 peuvent se voir refuser l’accès aux ressources d’entreprise (telles que la messagerie ou les sites SharePoint) tant qu’ils ne réinitialisent pas leur mot de passe. À l’avenir, toutes les mises à jour des stratégies de configuration et de conformité des mots de passe forceront les utilisateurs ciblés à mettre à jour leurs mots de passe. D’après nos études réalisées sur les clients avant d’appliquer ce changement, peu de clients sont impactés. En fait, la plupart des utilisateurs finaux mettent à jour leur mot de passe après avoir reçu une demande d’inscription avec mot de passe ou une demande de réinitialisation de leur mot de passe à des fins de conformité.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Prévenez votre support technique. Nous mettrons à jour cette page de nouveautés une fois ce changement déployé. Si vous ne souhaitez pas mettre en œuvre cette stratégie de mot de passe pour les appareils macOS, nous vous recommandons d’annuler l’affectation de votre stratégie macOS existante ou de la supprimer.


### <a name="reminder-intune-support-experience-for-premier-customers-now-in-azure-instead-of-mpo---2828727--"></a>Rappel : expérience de support Intune pour les clients Premier désormais dans Azure et non dans MPO <!--2828727-->
Dans le MC147649 de septembre, nous avions annoncé pour décembre la fin de la création des demandes de support Intune à partir du portail Microsoft Premier Online ou MPO (premier.microsoft.com). Après un léger retard, vous serez redirigé fin janvier vers Intune sur Azure pour créer vos demandes de support. 


#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Après janvier, pour continuer à améliorer l’expérience de support Premier, vous ne pourrez plus créer de demandes de support dans MPO.  Si vous essayez de le faire, vous verrez une invite, que vous ne pourrez pas faire disparaître, indiquant une redirection vers Intune sur Azure. Ici, vous pouvez créer une demande de support qui sera acheminée vers le Support Microsoft dédié à Intune, pour diagnostiquer et résoudre votre problème en temps voulu. Notez que les demandes de support créées dans le portail MPO ne peuvent pas être affichées dans le portail Azure. 

Le portail Azure propose une nouvelle expérience de support, comme nous l’avons récemment annoncé dans le MC171941. Vous trouverez plus d’informations à ce sujet à l’adresse [https://aka.ms/new_support_experience](https://aka.ms/new_support_experience) et à la rubrique Informations supplémentaires.

Si vous utilisez la gestion hybride des appareils mobiles (GPM hybride) ou utilisez la cogestion, vous pouvez continuer à utiliser MPO pour créer des demandes de support pour ConfigMgr, mais utiliser le portail Azure pour créer des demandes de support pour Intune. Pour rappel, MDM hybride est [déprécié](https://docs.microsoft.com/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). Vous devez donc prévoir de passer à Intune sur Azure dès que possible. Pour plus d’informations, consultez [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

Notez que seuls les utilisateurs avec des rôles d’administrateur général, d’administrateur de service Intune et d’administrateur de support de service peuvent créer des tickets de support dans le portail Azure.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
- Cessez d’utiliser MPO et utilisez Intune sur Azure pour créer et gérer toutes vos demandes de support Intune.  
- Informez votre support technique et mettez la documentation à jour si nécessaire.
- Si vous avez des utilisateurs sans rôles d’administrateur général ou d’administrateur de services qui créent actuellement des demandes de support dans MPO, attribuez-leur le rôle d’administrateur de support de service dans Azure Active Directory afin qu’ils puissent continuer à créer des tickets de support dans le portail Azure.

#### <a name="additional-information"></a>Informations supplémentaires
[https://aka.ms/IntuneSupport_MPO_to_Azure](https://aka.ms/IntuneSupport_MPO_to_Azure)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Modification planifiée : Mise à jour de l’expérience utilisateur dans l’application Portail d’entreprise pour iOS
Nous sommes ravis d’annoncer qu’Intune va bientôt publier une mise à jour majeure de l’expérience utilisateur dans l’application iOS Portail d’entreprise. La mise à jour proposera une refonte visuelle de la page d’accueil avec des filtres avancés et un accès plus rapide aux applications et aux livres.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Cette mise à jour de l’expérience utilisateur, tout en conservant les fonctionnalités actuelles du Portail d’entreprise iOS, proposera ce qui suit :
- Page d’accueil avec l’apparence native d’iOS. 
- Fonctionnalités de filtrage sur les listes de contenu et les recherches, avec possibilité de filtrer par type de contenu (applications ou livres électroniques) et par disponibilité (gestion des appareils obligatoire ou disponible sans inscription).
- Recherche de contenu dans les livres électroniques.
- Historique des recherches d’applications et de livres électroniques. Si vous faites partie du programme Apple TestFlight, vous serez informé de la disponibilité dans Intune de l’application mise à jour Portail d’entreprise pour iOS en préversion. Si vous ne faites pas partie du programme Apple TestFlight, il n’est pas trop tard pour vous inscrire. L’inscription vous permet d’utiliser l’application Portail d’entreprise mise à jour avant qu’elle ne soit accessible à vos utilisateurs finaux. Vous pourrez également envoyer vos commentaires directement à l’équipe Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Aucune action de votre part n’est requise. Ces changements seront publiés dans une version à venir de l’application iOS Portail d’entreprise. 

#### <a name="additional-information"></a>Informations supplémentaires
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>Modification planifiée : le connecteur Exchange Online pour Intune ne sera pas disponible dans Intune <!-- 3105122 -->
Pour simplifier votre expérience avec Exchange Online et l’accès conditionnel, nous allons désactiver le connecteur de service à service Exchange Online pour Intune. Cette modification commencera lors de la mise à jour du service de décembre et se terminera lors de la mise à jour du service de février 2019.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Vous recevez ce message, car, selon nos dossiers, vous utilisez peut-être la fonctionnalité de connecteur de service à service dans votre environnement. Ce connecteur prend en charge la gestion Intune des appareils Exchange Active Sync uniquement pour Exchange Online, mais ne gère pas l’infrastructure locale. En raison de la façon dont il s’affiche dans la console, il semble nécessaire pour l’accès conditionnel (CA), ce qui n’est pas le cas en réalité. Dans la mise à jour de décembre du service Intune, nous allons désactiver le bouton permettant de configurer de nouveaux connecteurs de façon à clarifier ce point dans la console. En février 2019, tous les connecteurs Exchange Online pour Intune seront désactivés.

Si vous utilisez ces connecteurs dans votre environnement, vous ne pourrez pas surveiller ou réinitialiser les appareils Exchange Active Sync uniquement dans Intune une fois les connecteurs désactivés, en février. Cette modification devrait n’avoir aucune incidence sur vos utilisateurs finaux.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?

Si vous avez configuré le connecteur de service à service et que vous disposez d’appareils Exchange Active Sync uniquement, passez à d’autres méthodes de gestion de vos appareils. Les options suivantes sont disponibles :

- inscrire les appareils auprès de la gestion des appareils mobiles (MDM) ;
- utiliser des stratégies Intune App Protection pour gérer vos appareils ;
- utiliser les contrôles Exchange, comme l’explique cette documentation. 

#### <a name="additional-information"></a>Informations supplémentaires
[Configurer le connecteur de service Exchange pour Intune et Exchange Online](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Modification planifiée : mises à jour visant à améliorer les performances d’Intune pour l’Éducation <!--1750215-->
Nous ajoutons des mises à jour à Intune pour l’Éducation afin de vous permettre d’affecter des paramètres à vos utilisateurs ou appareils de manière plus rapide et plus fiable. Dans le cadre de ce changement, nous déplacerons fin novembre vos stratégies ou affectations de paramètres dans de nouveaux groupes.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?

En tant que client Intune pour l’Éducation, vous disposez de deux groupes Azure AD (Azure Active Directory) dynamiques : « Tous les utilisateurs » et « Tous les appareils ». Avec ces mises à jour, les groupes Azure AD « Tous les utilisateurs » et « Tous les appareils » ne seront pas visibles dans la console Intune pour l’Éducation. Toutefois, ils apparaîtront toujours dans la console Intune sur Azure où ils seront renommés « Tous les utilisateurs (obsolète, ne pas utiliser) » et « Tous les appareils (obsolète, ne pas utiliser) ».

Une fois les mises à jour déployées, vous n’aurez plus besoin d’utiliser les groupes Azure AD pour affecter des applications et des paramètres dans Intune. Au lieu de cela, vous trouverez vos affectations de paramètres dans de nouveaux groupes que nous créerons pour vous dans la console Intune pour l’Éducation et qui apparaîtront toujours sous la forme « Tous les utilisateurs » et « Tous les appareils », comme avant. Ces changements étant apportés au niveau du backend, vous ne remarquerez aucune différence dans la console Intune pour l’Éducation. Vos utilisateurs finaux et vos appareils inscrits ne devraient pas être impactés. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Le déplacement de vos affectations de stratégie ne nécessite aucune intervention de votre part. Si vous affectez actuellement des stratégies dans la console Intune pour l’Éducation, continuez à le faire.

Si vous affectez actuellement des stratégies aux groupes Azure AD indiqués plus haut dans Intune sur Azure, commencez à les affecter aux groupes Tous les utilisateurs et Tous les appareils dans la console Intune pour l’Éducation. Quand vous constatez que les groupes Azure AD sont renommés dans la console (mention « obsolète »), arrêtez d’affecter des stratégies dans Azure AD. Si vous n’utilisez pas les groupes renommés à d’autres fins, supprimez-les.


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Action nécessaire : mettez à jour les paramètres de mot de passe de stratégie de conformité ou de restriction de votre appareil Android dans Intune
Intune va supprimer le type de mot de passe disponible « Paramètres par défaut de l’appareil » pour les appareils Android 4.4 et ultérieurs. En raison des différences qui existent entre les plateformes Android et les paramètres par défaut des appareils, cette stratégie est souvent considérée comme facultative par l’appareil. Pour dissiper toute confusion quant au moment où ce paramètre est appliqué sur Android, nous allons le supprimer de l’interface utilisateur dans une prochaine version. 
#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
- Si vous avez l’intention d’exiger un mot de passe sur les appareils, nous vous recommandons de modifier vos profils de plateforme Android pour préciser clairement le type de mot de passe exigé plutôt que d’utiliser le « paramètre par défaut de l’appareil ».
- Si vous avez l’intention de laisser votre utilisateur final choisir s’il faut créer un mot de passe, sélectionnez le bouton « Non configuré ». Quand nous supprimerons ce paramètre de l’interface utilisateur, si le paramètre est toujours défini, vous devrez choisir une valeur autre que « Paramètre par défaut de l’appareil » la prochaine fois que vous modifierez le profil.
Que dois-je faire pour me préparer à cette modification ?
Vérifiez les paramètres de mot de passe dans vos stratégies de conformité et de restriction d’appareil Android et Android Entreprise. Ils sont listés sous Sécurité système pour les stratégies de conformité, et sous Mot de passe de l’appareil ou sous Paramètres du profil professionnel pour les restrictions d’appareil. Les informations supplémentaires proposent un lien vers plus de détails et des captures d’écran indiquant où ces paramètres sont configurés.
#### <a name="additional-information"></a>Informations supplémentaires
https://aka.ms/PasswordSettings 

