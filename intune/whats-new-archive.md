---
title: Nouveautés des mois précédents dans Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Passer en revue les annonces antérieures sur la page Nouveautés d’Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ea9f8662faad1f8ef70fbba4c3706930d31157ac
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347710"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Nouveautés de la préversion de Microsoft Intune - mois précédents

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="november-2017"></a>Novembre 2017

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Résoudre les problèmes d’inscription  <!-- 746324 -->

L’espace de travail **Résolution des problèmes** montre désormais les problèmes d’inscription des utilisateurs. Des détails sur les problèmes et des suggestions de correction peuvent aider les administrateurs et les agents du support technique à résoudre les problèmes. Certains problèmes d’inscription ne sont pas capturés et certaines erreurs peuvent ne pas avoir de suggestions de correction.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrictions d’inscription assignées aux groupes <!-- 747598 -->

En tant qu’administrateur Intune, vous pouvez désormais [créer des restrictions d’inscription Type d’appareil et Limite d’appareils personnalisées pour des groupes d’utilisateurs](enrollment-restrictions-set.md).

Le portail Azure Intune vous permet de créer jusqu’à 25 instances de chaque type de restriction qui peuvent ensuite être assignées aux groupes d’utilisateurs. Les restrictions assignées aux groupes remplacent les restrictions par défaut.

Toutes les instances d’un type de restriction sont conservées dans une liste classée de manière stricte. Cet ordre définit une valeur de priorité pour la résolution des conflits. Un utilisateur impacté par plusieurs instances de restriction est uniquement limité par l’instance ayant la valeur de priorité la plus élevée. Vous pouvez modifier la priorité d’une instance donnée en la faisant glisser vers un autre emplacement de la liste.

Cette fonctionnalité sera disponible quand les paramètres Android for Work seront migrés depuis le menu Inscription Android for Work vers le menu Restrictions d’inscription. Cette migration pouvant prendre plusieurs jours, votre compte peut être mis à niveau pour d’autres parties de la version de novembre avant que l’affectation aux groupes ne soit activée pour les restrictions d’inscription.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Prise en charge de plusieurs connecteurs NDES (Service d’inscription de périphérique réseau)<!-- 1528104 -->

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

### <a name="google-play-protect-support-on-android----908720---"></a>Support de Google Play Protect sur Android <!-- 908720 -->

Avec la publication d’Android Oreo, Google introduit une suite de fonctionnalités de sécurité appelée Google Play Protect qui permet aux utilisateurs et aux organisations d’exécuter des applications sécurisées et des images Android sécurisées. Intune prend maintenant en charge les fonctionnalités de Google Play Protect, notamment l’attestation SafetyNet distante. Les administrateurs peuvent définir des critères de stratégie de conformité pour que Google Play Protect soit configuré et sain.
Le paramètre **Attestation d’appareil SafetyNet** nécessite que l’appareil se connecte à un service Google pour vérifier que l’appareil est intègre et qu’il n’est pas compromis. Les administrateurs peuvent également définir un paramètre de profil de configuration pour qu’Android for Work exige que les applications installées soient vérifiées par les services Google Play. Si un appareil n’est pas conforme aux exigences de Google Play Protect, l’accès conditionnel peut empêcher les utilisateurs d’accéder aux ressources de l’entreprise.

- Découvrez comment [créer une stratégie de conformité des appareils pour activer Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocole de texte autorisé à partir des applications gérées <!-- 1414050  -->

Les applications gérées par le SDK d’application Intune peuvent envoyer des SMS.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Mise à jour du rapport d’installation de l’application pour inclure l’état Installation en attente <!-- 1249446 -->  

Le rapport **État de l’installation de l’application** accessible pour chaque application via la liste **Application** dans la charge de travail **Applications clientes** contient désormais un comptage **Installation en attente** pour les utilisateurs et les appareils.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API d’inventaire des applications iOS 11 pour la détection des menaces mobiles <!-- 1391759 -->

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

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local <!-- 676614 -->
Une fois que le connecteur Exchange crée une connexion à Exchange en utilisant l’autorité de certification spécifiée, le connecteur a désormais la possibilité de découverte d’autres autorités de certification. Si l’autorité de certification principale est indisponible, le connecteur bascule vers une autre autorité de certification disponible, jusqu'à ce que l’autorité de certification principale redevienne disponible. Pour plus de détails, voir [Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Redémarrer à distance un appareil iOS (supervisé uniquement) <!-- 1424595 -->

Vous pouvez désormais déclencher le redémarrage d’un appareil iOS 10.3+ supervisé au moyen d’une action d’appareil. Pour plus d’informations sur l’utilisation de l’action de redémarrage d’appareil, consultez [Redémarrer à distance des appareils avec Intune](device-restart.md).

> [!Note]
> Cette commande nécessite un appareil supervisé et le droit d’accès **Verrouillage de l’appareil**. L’appareil redémarre immédiatement. Après le redémarrage, les appareils iOS verrouillés par un code secret ne rejoignent pas un réseau Wi-Fi et peuvent se trouver dans l’impossibilité de communiquer avec le serveur.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Prise en charge de l’authentification unique pour iOS <!-- 1333645 -->  

Vous pouvez utiliser l’authentification unique pour les utilisateurs d’iOS. Les applications iOS qui sont codées pour rechercher les informations d’identification de l’utilisateur dans la charge utile d’authentification unique fonctionnent avec cette mise à jour de la configuration de la charge utile. Vous pouvez également utiliser un UPN et un ID d’appareil Intune pour configurer le nom du principal et le domaine. Pour plus d’informations, consultez [Configurer Intune pour l’authentification unique des appareils iOS](sso-ios.md).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Ajouter « Rechercher mon iPhone » pour les appareils personnels <!--1427287-->
Vous pouvez désormais savoir si la fonctionnalité Verrou d’activation est activée pour les appareils iOS. Cette fonctionnalité se trouvait avant dans le portail classique.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Verrouiller à distance un appareil macOS géré avec Intune <!-- 1437691 -->

Vous pouvez verrouiller un appareil macOS perdu et définir un code PIN de récupération à 6 chiffres. Une fois le verrouillage effectué, le panneau **Vue d’ensemble des appareils** affiche le code PIN jusqu’à ce qu’une autre action d’appareil soit envoyée.

Pour plus d’informations, consultez [Verrouiller à distance des appareils gérés avec Intune](device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Nouveaux détails de profil SCEP pris en charge <!-- 1559808 -->

Les administrateurs peuvent désormais définir des paramètres supplémentaires durant la création d’un profil SCEP sur les plateformes Windows, iOS, macOS et Android.  Les administrateurs peuvent définir un IMEI, un numéro de série ou un nom commun (adresse e-mail incluse) dans le format du nom de l’objet.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Conserver les données pendant une réinitialisation des paramètres d’usine <!--1588489 -->
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


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Les affectations de boucles de mise à jour de Windows 10 sont affichées <!-- 1621837 -->
Pendant une **résolution de problèmes**, vous pouvez voir les affectations de boucles de mise à jour de Windows 10 pour l’utilisateur affiché.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Paramètres de la fréquence d’émission des rapports Windows Defender - Protection avancée contre les menaces <!-- 1455974  -->
Le service Windows Defender - Protection avancée contre les menaces permet aux administrateurs de gérer la fréquence d’émission des rapports sur les appareils gérés. Avec la nouvelle option **Augmenter la fréquence des rapports de télémétrie**, Windows Defender ATP collecte les données et évalue les risques plus fréquemment. Par défaut, l’émission de rapports optimise le niveau de performance et la vitesse. Augmenter la fréquence d’émission des rapports peut être utile pour les appareils à haut risque. Ce paramètre se trouve dans le profil **Windows Defender ATP** dans **Configurations d’appareil**.

### <a name="audit-updates----1412961---"></a>Auditer les mises à jour <!-- 1412961 -->  
La fonctionnalité d’audit d’Intune enregistre les opérations de modification relatives à Intune.  Tous les opérations de création, de mise à jour, de suppression et de tâche à distance sont capturées et conservées pendant un an.  Le portail Azure fournit une vue filtrable des 30 derniers jours de données d’audit dans chaque charge de travail.  Une API Graph correspondante permet de récupérer les données d’audit stockées pendant l’année écoulée.

La fonctionnalité d’audit se trouve sous le groupe **SURVEILLER**. Il existe un élément de menu **Journaux d’audit** par charge de travail.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>L’application Portail d’entreprise pour macOS est disponible<!--1541700-->
L’expérience du Portail d’entreprise Intune sous macOS a été mise à jour. Elle a été optimisée pour afficher clairement toutes les informations et notifications de conformité dont les utilisateurs ont besoin pour tous les appareils qu’ils ont inscrits. Une fois que le Portail d’entreprise Intune a été déployé sur un appareil, il bénéficie de la mise à jour automatique Microsoft (AutoUpdate) pour macOS. Vous pouvez télécharger le nouveau Portail d’entreprise Intune pour macOS en ouvrant une session sur le site web du Portail d’entreprise Intune sur un appareil macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner fait maintenant partie de la liste des applications approuvées de la gestion des applications mobiles (MAM)<!-- 1248473 -->
L’application Microsoft Planner pour iOS et Android fait à présent partie des applications approuvées pour la gestion des applications mobiles (MAM). Elle est configurable par le biais du panneau Intune App Protection sur le Portail Azure de tous les clients.
- Pour plus de détails, consultez la page [Liste MAM des applications approuvées](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Fréquence de mise à jour des exigences du VPN par application sur les appareils iOS<!-- 1547061 -->  
Les administrateurs peuvent à présent supprimer des exigences du VPN par application pour les applications installées sur des appareils iOS ; les appareils concernés seront mis à jour après l’archivage Intune suivant, ce qui se produit généralement dans les 15 minutes.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Prise en charge du pack d’administration de System Center Operations Manager pour le connecteur Exchange<!-- 885457 -->
Le pack d’administration de System Center Operations Manager (SCOM) pour le connecteur Exchange est maintenant disponible pour vous aider à analyser les journaux du connecteur Exchange. Cette fonctionnalité offre différents moyens de surveiller le service à des fins de résolution des problèmes.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestion pour les appareils Windows 10 <!-- 1243445 -->
La cogestion est une solution qui propose une passerelle entre la gestion classique et la gestion moderne tout en vous donnant la possibilité d’opérer cette transition selon une approche en plusieurs phases. À la base, la cogestion est une solution qui permet aux appareils Windows 10 d’être gérés simultanément par Configuration Manager et Microsoft Intune, et d’être joints à Active Directory (AD) et à Azure Active Directory (Azure AD).  Cette configuration vous offre un moyen de vous moderniser à un rythme qui convient à votre organisation si vous ne pouvez pas le faire d’un coup.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Limiter l’inscription Windows par version de système d’exploitation<!-- 245498 -->
En tant qu’administrateur Intune, vous pouvez maintenant spécifier une version minimale et maximale de Windows 10 pour les inscriptions d’appareils. Vous pouvez définir ces restrictions dans le panneau **Configurations de plateforme**.

Intune continue à prendre en charge l’inscription des PC et téléphones Windows 8.1. Toutefois, seules les versions de Windows 10 peuvent être configurées avec des limites minimale et maximale. Pour autoriser l’inscription d’appareils 8.1, laissez vide la limite minimale.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertes pour les appareils non affectés Windows AutoPilot  <!-- 1631236 -->
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

### <a name="app-conditional-launch-support----1193313---"></a>Prise en charge du lancement conditionnel d’applications<!-- 1193313 -->
Les administrateurs informatiques peuvent désormais définir une condition dans le portail d’administration Azure permettant d’appliquer un code secret à la place d’un code PIN numérique via la gestion des applications mobiles (MAM) lors du lancement de l’application. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Cette version d’Intune propose cette fonctionnalité **sur iOS uniquement**. Intune prend en charge un code secret comme un code PIN numérique, il définit une longueur minimale et autorise la répétition des caractères et des séquences. Cette fonctionnalité nécessite la participation des applications (c’est-à-dire, WXP, Outlook, Managed Browser, Yammer) pour intégrer le kit SDK Intune App avec le code de cette fonctionnalité en place dans le but d’appliquer les paramètres du code secret dans les applications ciblées.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numéro de version des applications métier dans le rapport d’état d’installation de l’appareil<!-- 1233999 -->
Avec cette version, le rapport d’état d’installation de l’appareil affiche le numéro de version des applications métier pour iOS et Android. Vous pouvez utiliser cette information pour dépanner vos applications ou trouver les appareils qui exécutent des versions d’application anciennes.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Les administrateurs peuvent désormais configurer les paramètres du Pare-feu d’un appareil avec un profil de configuration d’appareil <!-- 951708 -->   
Les administrateurs peuvent activer le Pare-feu sur les appareils et configurer divers protocoles pour les réseaux privés, publics et de domaine.  Ces paramètres de pare-feu se trouvent dans le profil « Endpoint protection ».

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard permet de protéger les appareils des sites web non approuvés, comme défini par votre organisation <!-- 958257 -->   
Les administrateurs peuvent définir les sites comme « approuvés » ou « appartenant à l’entreprise » à l’aide d’un flux de travail Protection des informations Windows ou du nouveau profil « Limite réseau » dans les configurations de l’appareil. S’ils sont consultés dans Microsoft Edge, les sites qui ne sont pas listés dans la limite réseau approuvée d’un appareil Windows 10 64 bits s’ouvrent à la place dans un navigateur d’une machine virtuelle Hyper-V.

Application Guard se trouve dans les profils de configuration de l’appareil, dans le profil « Endpoint protection ». À partir de là, les administrateurs peuvent configurer une interaction entre le navigateur virtualisé et la machine hôte, les sites non approuvés et les sites approuvés, puis stocker les données générées dans le navigateur virtualisé. Pour utiliser Application Guard sur un appareil, une limite réseau doit d’abord être configurée. Il est important de définir une seule limite réseau pour un appareil.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Control sur Windows 10 Entreprise offre un mode permettant d’approuver uniquement les applications autorisées <!-- 1031096 -->    
Avec des milliers de nouveaux fichiers malveillants créés chaque jour, l’utilisation d’une détection antivirus basée sur les signatures pour lutter contre les programmes malveillants ne constitue probablement plus une défense suffisante contre les nouvelles attaques. En utilisant Windows Defender Application Control sur Windows 10 Entreprise, vous pouvez changer la configuration de l’appareil et passer d’un mode où les applications sont approuvées sauf si elles sont bloquées par un antivirus ou une autre solution de sécurité à un mode où le système d’exploitation approuve uniquement les applications autorisées par votre entreprise. Vous approuvez les applications dans Windows Defender Application Control.

Avec Intune, vous pouvez configurer des stratégies de contrôle d’application en mode « audit uniquement » ou en mode d’application. Les applications ne sont pas bloquées quand vous exécutez le mode « audit uniquement ». Le mode « Audit uniquement » enregistre tous les événements dans les journaux du client local. Vous pouvez également autoriser uniquement l’exécution des composants Windows et des applications du Microsoft Store, ou autoriser l’exécution d’autres applications avec une bonne réputation telle que définie par Intelligent Security Graph.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard est un nouvel ensemble de fonctionnalités de prévention d’intrusion pour Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard propose des règles personnalisées permettant de réduire l’exploitabilité des applications, empêche les menaces provenant de macros et de scripts, bloque automatiquement les connexions réseau à des adresses IP de mauvaise réputation et peut sécuriser les données contre des ransomware et des menaces inconnues. Windows Defender Exploit Guard présente les composants suivants :

- **Réduction de la surface d’attaque (ASR)** fournit des règles vous permettant d’empêcher les menaces de macro, de script et d’e-mail.
- **Accès contrôlé au dossier** bloque automatiquement l’accès au contenu des dossiers protégés.
- **Filtre de réseau** bloque la connexion sortante de toutes les applications à une adresse IP/domaine de faible réputation
- **Exploit Protection** fournit la mémoire, le flux de contrôle et les restrictions de stratégie pouvant être utilisés pour protéger les applications contre des attaques.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gérer des scripts PowerShell dans Intune pour des appareils Windows 10 <!-- 790537 -->

L’extension de gestion Intune vous permet de charger des scripts PowerShell dans Intune pour les exécuter sur des appareils Windows 10. L’extension vient en complément des fonctionnalités de gestion des appareils mobiles (MDM) Windows 10 et facilite l’adoption d’une gestion moderne. Pour plus d’informations, consultez [Gérer des scripts PowerShell dans Intune pour des appareils Windows 10](intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10      <!-- 1308850 -->
-    Messagerie (mobile uniquement) - désactivation des tests ou des messages MMS
-    Mot de passe - paramètres pour activer FIPS et l’utilisation d’appareils secondaires Windows Hello pour l’authentification 
-    Affichage - paramètres pour activer ou désactiver la mise à l’échelle GDI pour les applications héritées

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrictions des appareils en mode plein écran Windows 10<!-- 1308872 -->   
Vous pouvez restreindre les utilisateurs d’appareils Windows 10 au mode plein écran, ce qui limite les utilisateurs à un ensemble d’applications prédéfinies.  Pour ce faire, créez un profil de restriction d’appareil Windows 10 et définissez les paramètres de plein écran.

Le mode plein écran prend en charge deux modes : **application unique** (permet à l’utilisateur d’exécuter une seule application) ou **applications multiples** (permet l’accès à un ensemble d’applications).  Vous définissez le compte d’utilisateur et le nom de l’appareil, ce qui détermine les applications prises en charge.  Lorsque l’utilisateur est connecté, il est limité aux applications définies.  Pour en savoir plus, consultez [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Conditions requises du mode plein écran :

- Intune doit être l’autorité MDM.
- Les applications doivent déjà être installées sur l’appareil cible.
- L’appareil doit être [correctement provisionné](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nouveau profil de configuration d’appareil pour la création de limites réseau<!-- 1311967 -->   
Vous trouverez un nouveau profil de configuration d’appareil appelé **Limite réseau** avec vos autres profils de configuration d’appareil. Utilisez ce profil pour définir des ressources en ligne à considérer comme approuvées et appartenant à l’entreprise. Vous devez définir une limite réseau pour un appareil *avant* de pouvoir utiliser les fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows sur l’appareil. Il est important de définir une seule limite réseau pour chaque appareil.

Vous pouvez définir des ressources cloud d’entreprise, des plages d’adresses IP et des serveurs proxy internes à considérer comme approuvées. Une fois définie, la limite réseau peut être utilisée par d’autres fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Deux paramètres supplémentaires pour Windows Defender Antivirus<!-- 1338409 -->  
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

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix ajouté pour les appareils Windows 10 <!-- 1512457 -->  
Vous pouvez configurer un VPN Citrix pour les appareils Windows 10. Vous pouvez choisir le VPN Citrix dans la liste *Sélectionner un type de connexion* du panneau **VPN de base** quand vous configurez un VPN pour Windows 10 et ultérieur.

> [!Note]
> Une configuration de Citrix existait pour iOS et Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Les connexions Wi-Fi prennent en charge les clés prépartagées sur iOS <!-- 1550823 -->
Les clients peuvent configurer des profils Wi-Fi pour utiliser des clés prépartagées pour les connexions personnelles WPA/WPA2 sur les appareils iOS. Ces profils sont envoyés à l’appareil de l’utilisateur quand l’appareil est inscrit dans Intune.

Quand le profil a été envoyé à l’appareil, l’étape suivante varie en fonction de la configuration du profil.  S’il est configuré pour se connecter automatiquement, il le fait quand l’accès réseau est nécessaire.  Quand le profil se connecte manuellement, l’utilisateur doit activer la connexion manuellement.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Accès aux journaux d’applications gérées pour iOS <!-- 1469920 -->
Les utilisateurs finaux disposant de Managed Browser peuvent désormais afficher l’état de gestion de toutes les applications Microsoft publiées, et envoyer les journaux afin de dépannage leurs applications iOS gérées.

Pour découvrir comment activer le mode de dépannage dans Managed Browser sur un appareil iOS, consultez [Comment accéder aux journaux des applications gérées à l’aide de Managed Browser sur iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Améliorations apportées au workflow de configuration des appareils sur le Portail d’entreprise pour iOS dans la version 2.9.0<!-- 1417174 -->

Le workflow de configuration des appareils a été amélioré dans l’application Portail d’entreprise pour iOS. La langue est plus conviviale, et nous avons regroupé des écrans dans la mesure du possible. La langue est également plus adaptée à l’entreprise, car nous utilisons à chaque fois son nom dans le texte de configuration. Vous pouvez voir ce workflow mis à jour sur la page  [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L’entité Utilisateur contient les données utilisateur les plus récentes dans le modèle de données de l’entrepôt de données <!-- 1544273 -->
La première version du modèle de données de l’entrepôt de données Intune ne contenait que des données Intune historiques récentes. Les auteurs de rapports ne pouvaient pas capturer l’état actuel d’un utilisateur. Dans cette mise à jour, **l’entité Utilisateur** est renseignée avec les données utilisateur les plus récentes.


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

### <a name="device-and-app-management-integration----677972---"></a>Intégration de la gestion des appareils et des applications<!-- 677972 -->   
Maintenant que la gestion des appareils mobiles (MDM) et la gestion des applications mobiles (MAM) d’Intune sont accessibles à partir du portail Azure, Intune a commencé à intégrer l’expérience d’administrateur informatique dans la gestion des applications et des appareils. Ces changements sont destinés à simplifier votre expérience de la gestion des appareils et des applications.

Découvrez plus en détail les changements de MDM et de MAM annoncés sur le [blog de l’équipe de support Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nouvelles alertes d’inscription pour les appareils Apple <!-- 1471790 -->
La page de vue d’ensemble de l’inscription affiche les alertes utiles pour les administrateurs informatiques concernant la gestion des appareils Apple. Des alertes s’affichent dans la page Vue d’ensemble quand le certificat push MDM Apple arrive à expiration ou a déjà expiré ; quand le jeton DEP (Programme d’inscription des appareils) expire ou a déjà expiré ; et en présence d’appareils non affectés dans le programme DEP.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Prise en charge du remplacement de jeton pour la configuration d’application sans inscription de l’appareil <!-- 1080364 -->

Vous pouvez utiliser des jetons pour les valeurs dynamiques des configurations des applications des appareils qui ne sont pas inscrits. Pour plus d’informations, consultez [Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil](app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Mise à jour de l’application Portail d’entreprise pour Windows 10<!--1299474-->
La page Paramètres de l’application Portail d’entreprise pour Windows 10 a été mise à jour pour rendre les paramètres et les actions prévues de l’utilisateur plus cohérents à travers l’ensemble des paramètres, ainsi que pour correspondre à la disposition d’autres applications Windows. Vous trouverez des images avant/après sur la page [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Communication d’informations aux utilisateurs finaux au sujet des données consultables sur les appareils Windows 10<!--1337920-->
Nous avons ajouté le **Type de propriété** dans l’écran Détails de l’appareil de l’application Portail d’entreprise pour Windows 10. Les utilisateurs peuvent ainsi trouver plus d’informations sur la confidentialité directement à partir de cette page dans la documentation de l’utilisateur final d’Intune. Ils les trouveront également sur l’écran **À propos de**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Invites pour entrer des commentaires dans l’application Portail d’entreprise pour Android<!--1165249-->
L’application Portail d’entreprise pour Android demande maintenant un retour d’expérience des utilisateurs finaux. Ces commentaires sont envoyés directement à Microsoft et permettent aux utilisateurs finaux d’évaluer l’application dans le Google Play Store public. Le retour d’expérience n’est pas obligatoire et peut être facilement ignoré de façon à continuer d’utiliser l’application.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Rendre vos utilisateurs autonomes avec l’application Portail d’entreprise pour Android <!-- 1573324, 1573150, 1558616, 1564878 -->

L’application Portail d’entreprise pour Android a ajouté des indications permettant aux utilisateurs finaux de comprendre et, dans la mesure du possible, de résoudre eux-mêmes les nouveaux cas d’usage.
- Les utilisateurs finaux sont redirigés vers le [portail Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) pour supprimer un appareil s’ils ont atteint le nombre maximal d’appareils qu’ils sont autorisés à ajouter.
- Les utilisateurs finaux reçoivent des instructions pour les aider à [corriger les erreurs d’activation sur les appareils Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) ou à [désactiver le mode d’économie d’énergie](/intune-user-help/power-saving-mode-android). Si aucune de ces solutions ne résout leur problème, nous indiquons comment [envoyer les journaux à Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nouvelle action « Résoudre » disponible pour les appareils Android <!-- 1583480 -->

L’application Portail d’entreprise pour Android introduit une action « Résoudre » dans la page _Mettre à jour les paramètres de l’appareil_. Cette option permettra à l’utilisateur final d’accéder directement au paramètre ayant rendu son appareil non conforme. L’application Portail d’entreprise pour Android prend en charge cette action pour les paramètres [Code secret de l’appareil](/intune-user-help/set-your-pin-or-password-android), [Débogage USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) et [Sources inconnues](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicateur de progression de la configuration de l’appareil sur le Portail d’entreprise Android<!-- 1565657 -->
L’application Portail d’entreprise pour Android affiche un indicateur de progression de la configuration de l’appareil au moment où l’utilisateur l’inscrit. L’indicateur affiche de nouveaux états : tout d’abord, « Configuration de votre appareil en cours... », puis « Inscription de votre appareil en cours... », « Fin de l’inscription de votre appareil... » et enfin « Fin de la configuration de votre appareil... ».

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Prise en charge de l’authentification basée sur les certificats sur le portail d’entreprise pour iOS<!--1029830-->
Nous avons ajouté la prise en charge de l’authentification basée sur les certificats dans l’application Portail d’entreprise pour iOS. Les utilisateurs avec cette authentification entrent leur nom d’utilisateur et appuient sur le lien « Se connecter avec un certificat ». L’authentification basée sur les certificats est déjà prise en charge sur les applications du Portail d’entreprise pour Android et Windows. Vous pouvez en savoir plus sur la page [Comment faire pour se connecter à l’application Portail d’entreprise](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Les applications qui sont disponibles avec ou sans inscription peuvent désormais être installées sans invitation à l’inscription. <!-- 1334712 -->

Les applications d’entreprise qui ont été mises à disposition avec ou sans inscription dans l’application Portail d’entreprise Android peuvent désormais être installées sans invitation à l’inscription.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Prise en charge du programme de déploiement Windows AutoPilot dans Microsoft Intune  <!-- 747617  -->
Vous pouvez désormais utiliser Microsoft Intune avec le programme de déploiement Windows AutoPilot pour permettre à vos utilisateurs de provisionner eux-mêmes leurs appareils d’entreprise sans passer par le service informatique. Vous pouvez personnaliser l’expérience OOBE (out-of-box experience) pour permettre aux utilisateurs de joindre leurs appareils à Azure AD et de s’inscrire à Intune. Avec Microsoft Intune et Windows AutoPilot, vous n’avez plus à déployer et à gérer les images de système d’exploitation. Pour plus d’informations, consultez [Inscrire des appareils Windows à l’aide du programme Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="quick-start-for-device-enrollment-----1425655---"></a>Guide de démarrage rapide pour l’inscription d’appareils  <!-- 1425655 --> 
Le guide de démarrage rapide, désormais disponible dans **Inscription d’appareils**, fournit un tableau de références pour gérer les plateformes et configurer la procédure d’inscription. Vous trouverez une brève description de chaque élément et des liens vers des instructions pas à pas pour simplifier le démarrage.

### <a name="device-categorization----1427491---"></a>Catégorisation des appareils <!-- 1427491 -->
Le graphique des plateformes des appareils inscrits du panneau **Appareils > Vue d’ensemble** organise les appareils par plateforme (Android, iOS, macOS, Windows, Windows Mobile, etc.).  Les appareils qui exécutent d’autres systèmes d’exploitation sont regroupés dans « Autres ».  Il s’agit des appareils fabriqués par Blackberry, NOKIA, etc.  

Pour identifier les appareils affectés dans votre locataire, choisissez **Gérer > Tous les appareils**, puis utilisez **Filtrer** pour limiter le champ **Système d’exploitation**.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium : nouveau partenaire de Mobile Threat Defense <!-- 954681 -->  
Vous pouvez contrôler l’accès des appareils mobiles aux ressources de l’entreprise à l’aide d’un accès conditionnel basé sur une évaluation des risques effectuée par Zimperium,solution Mobile Threat Defense qui s’intègre à Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Déroulement de l’intégration à Intune
Le risque est évalué en fonction des données de télémétrie recueillies par les appareils exécutant Zimperium. Vous pouvez configurer des stratégies d’accès conditionnel EMS basées sur l’évaluation des risques de Zimperium, activée par le biais des stratégies de conformité Intune, que vous pouvez utiliser pour autoriser ou bloquer l’accès des appareils non conformes aux ressources d’entreprise en fonction des menaces détectées.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nouveaux paramètres pour le profil de restriction d’appareils Windows 10  <!--- 978575, 1308849, -->  
Nous ajoutons de nouveaux paramètres au profil de restriction des appareils Windows 10 dans la catégorie Windows Defender SmartScreen.

Pour obtenir plus d’informations sur le profil de restriction des appareils Windows 10, consultez [Paramètres de restriction des appareils Windows 10 et version ultérieure]( device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Support à distance pour les appareils Windows et Windows Mobile   <!-- 1070473 -->  
Intune peut désormais utiliser le logiciel [TeamViewer](https://www.teamviewer.com), vendu séparément, pour vous permettre de fournir une assistance à distance aux utilisateurs qui utilisent des appareils Windows et Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analyser les appareils avec Windows Defender <!-- 1280988  1280990   -->
Vous pouvez à présent exécuter une **Analyse rapide**, une **Analyse complète** et **Mettre à jour les signatures** avec l’antivirus Windows Defender sur les appareils Windows 10 gérés. À partir du panneau de présentation de l’appareil, choisissez l’action à exécuter sur l’appareil. Vous êtes invité à confirmer l’action avant l’envoi de la commande à l’appareil. 

**Analyse rapide** : une analyse rapide analyse les emplacements où les programmes malveillants s’enregistrent pour démarrer, comme les clés de registre et les dossiers de démarrage Windows connus. Une analyse rapide prend en moyenne cinq minutes. Associée au paramètre **Protection en temps réel toujours activé** qui analyse les fichiers lorsqu’ils sont ouverts, fermés et à chaque fois qu’un utilisateur accède à un dossier, une analyse rapide fournit une protection contre les programmes malveillants qui peuvent se trouver dans le système ou le noyau. Lorsque l’analyse s’achève, ses résultats s’affichent sur les appareils des utilisateurs. 

**Analyse complète** : une analyse complète peut être utile sur les appareils confrontés à une menace issue de programmes malveillants afin de déterminer s’il existe des composants inactifs qui nécessitent un nettoyage plus approfondi. Elle est également utile pour exécuter des analyses à la demande. Une analyse complète peut prendre une heure. Lorsque l’analyse s’achève, ses résultats s’affichent sur les appareils des utilisateurs. 

**Mettre à jour les signatures** : la commande de mise à jour de signature met à jour les définitions et les signatures des programmes malveillants dans Antivirus Windows Defender. Cela permet de garantir l’efficacité d’Antivirus Windows Defender dans la détection des programmes malveillants. Cette fonctionnalité s’applique uniquement aux appareils Windows 10 et est sujette à la connectivité Internet de l’appareil. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Le bouton Activer/Désactiver n’est plus disponible dans la page Autorité de certification Intune du portail Intune Azure  <!-- 1400455 -->
 Nous avons enlevé une étape du processus de configuration de Certificate Connector sur Intune. Actuellement, vous téléchargez Certificate Connector et vous l’activez dans la console Intune. Mais si vous le désactivez dans la console Intune, il continue d’émettre des certificats.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Depuis octobre, le bouton Activer/désactiver n’apparaît plus dans la page Autorité de certification du portail Azure. La fonctionnalité Certificate Connector reste la même. Les certificats sont toujours déployés sur les appareils inscrits à Intune. Vous pouvez continuer à télécharger et à installer Certificate Connector. Pour arrêter l’émission de certificats, vous devez désinstaller Certificate Connector au lieu de le désactiver.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Si Certificate Connector est actuellement désactivé, vous devez le désinstaller.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nouveaux paramètres pour le profil de restriction d’appareils Windows 10 Collaboration   <!--- 1308838 -->
Dans cette version, nous avons ajouté un grand nombre de nouveaux paramètres au profil de restriction d’appareils Windows 10 Collaboration pour vous permettre de gérer les appareils Surface Hub.

Pour plus d’informations sur ce profil, consultez [Paramètres de restriction d’appareils Windows 10 Collaboration](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Empêcher les utilisateurs d’appareils Android de modifier la date et l’heure de leur appareil  <!-- 1333292 -->
Vous pouvez utiliser la [stratégie d’appareil personnalisée Android](custom-settings-android.md) pour empêcher les utilisateurs d’appareils Android de modifier la date et l’heure de l’appareil.

Pour ce faire, configurez une stratégie personnalisée Android avec le paramètre URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange Affectez-lui la valeur **TRUE**, puis attribuez-le aux groupes requis.

### <a name="bitlocker-device-configuration----1397398---"></a>Configuration d’appareil BitLocker <!-- 1397398 -->
Les paramètres **Chiffrement Windows > Paramètres de Base** incluent un nouveau paramètre **Avertissement sur le chiffrement d’un autre disque** qui vous permet de désactiver le [message d’avertissement](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) sur le chiffrement d’un autre disque qui peut être utilisé sur l’appareil de l’utilisateur.  Le message d’avertissement nécessite le consentement de l’utilisateur final pour configurer BitLocker sur l’appareil et bloque la configuration de BitLocker tant qu’elle n’est pas confirmée par l’utilisateur final.  Le nouveau paramètre désactive l’avertissement pour l’utilisateur final.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Le programme d’achat en volume pour les applications d’entreprise est désormais synchronisé avec votre locataire Intune <!-- 800882 -->  
Les développeurs tiers peuvent distribuer des applications en privé aux membres autorisés du programme d’achat en volume (VPP) pour les entreprises. Ces membres du programme d’achat en volume pour les entreprises peuvent se connecter à l’App Store du programme d’achat en volume et acheter leurs applications.

À compter de cette version, les applications du programme d’achat en volume pour les entreprises achetées par l’utilisateur final sont désormais synchronisées avec leurs locataires Intune.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Sélectionner le magasin Apple du pays/région pour synchroniser les applications VPP<!-- 1332311 -->  
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


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Collection d’entité d’association d’appareil utilisateur ajoutée au modèle de données Intune Data Warehouse <!-- 1187917 -->
Vous pouvez désormais générer des rapports et des visualisations des données en utilisant les informations d’association appareil-utilisateur qui associent les collections d’entité utilisateur et appareil. Le modèle de données est accessible par le biais du fichier Power BI (PBIX) extrait de la page Intune Data Warehouse, via le point de terminaison OData, ou en développant un client personnalisé.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Vérifier la conformité de la stratégie pour les boucles de mise à jour de Windows 10 <!-- 1067886 -->
Vous pouvez consulter un rapport sur la stratégie pour vos boucles de mise à jour de Windows 10 à partir de Mises à jour logicielles > État de déploiement par boucle de mise à jour. Le rapport sur la stratégie inclut l’état du déploiement pour les boucles de mise à jour que vous avez configurées. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nouveau rapport qui répertorie les appareils iOS équipés d’anciennes versions iOS   <!-- 1352223 -->
Le rapport **Appareils iOS obsolètes** est disponible à partir de l’espace de travail **Mises à jour logicielles**. Dans ce rapport, vous pouvez afficher la liste des appareils iOS supervisés qui ont été ciblés par une stratégie de mise à jour iOS, et pour lesquels des mises à jour sont disponibles. Pour chaque appareil, vous pouvez afficher un état indiquant la raison pour laquelle l’appareil n’a pas été automatiquement mis à jour. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Afficher les attributions de la stratégie de protection des applications pour la résolution des problèmes <!--  1475003 -->
Dans cette version à venir, l’option **Stratégie de protection des applications** sera ajoutée à la liste déroulante **Affectations** disponible dans le panneau de résolution des problèmes. Vous pouvez maintenant sélectionner des stratégies de protection des applications pour afficher les stratégies de protection des applications affectées aux utilisateurs sélectionnés.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Améliorations apportées au workflow de configuration des appareils dans le portail d’entreprise <!--1490692-->
Nous avons amélioré le workflow de configuration des appareils dans l’application Portail d’entreprise pour Android. Le texte de l’interface est plus convivial et spécifique à votre entreprise, et nous avons regroupé des écrans quand cela était possible. Vous pouvez voir cela dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Amélioration de l’aide sur la demande d’accès aux contacts sur les appareils Android <!--1484985-->

L’application Portail d’entreprise pour Android nécessite souvent que l’utilisateur final accepte l’autorisation pour les contacts. Si un utilisateur final refuse cet accès, il voit désormais une notification dans l’application qui lui indique d’accorder l’autorisation pour l’accès conditionnel. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Correction du démarrage sécurisé pour Android <!--1490712-->

Les utilisateurs finaux d’appareils Android peuvent désormais indiquer la raison de la non-conformité dans l’application Portail d’entreprise. Quand c’est possible, ils sont directement positionnés à l’emplacement approprié dans l’application Paramètres pour corriger le problème. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notifications Push supplémentaires pour les utilisateurs finaux sur l’application Portail d’entreprise pour Android Oreo <!--1475932-->

Les utilisateurs finaux voient des notifications supplémentaires qui leur indiquent quand l’application Portail d’entreprise pour Android Oreo effectue des tâches en arrière-plan, comme la récupération de stratégies auprès du service Intune. La transparence s’en trouve améliorée pour les utilisateurs finaux, qui savent quand le Portail d’entreprise effectue des tâches d’administration sur leur appareil. Cette amélioration fait partie de [l’optimisation générale de l’interface utilisateur du portail d’entreprise](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) pour l’application Portail d’entreprise pour Android Oreo. 

Vous verrez d’autres optimisations relatives aux nouveaux éléments d’interface utilisateur dans Oreo Android.  Les utilisateurs finaux voient des notifications supplémentaires qui leur indiquent quand le portail d’entreprise effectue des tâches en arrière-plan, comme la récupération d’une stratégie auprès du service Intune.  La transparence s’en trouve améliorée pour les utilisateurs finaux, qui savent quand le portail d’entreprise effectue des tâches d’administration sur l’appareil.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nouveaux comportements de l’application Portail d’entreprise pour Android avec les profils professionnels <!-- 1485783 -->

Lorsque vous inscrivez un appareil Android for Work avec un profil professionnel, c’est l’application Portail d’entreprise dans le profil professionnel qui effectue les tâches de gestion sur l’appareil. 

L’application Portail d’entreprise pour Android n’a plus aucune utilité, sauf si vous utilisez une application GAM dans le profil professionnel. Pour améliorer l’expérience liée au profil professionnel, Intune masque automatiquement l’application Portail d’entreprise personnelle après l’inscription réussie d’un profil professionnel.

L’application Portail d’entreprise pour Android peut être activée à tout moment dans le profil personnel en recherchant [Portail d’entreprise dans le Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) et en appuyant sur **Activer**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Migration du Portail d’entreprise pour Windows 8.1 et Windows Phone 8.1 vers le mode soutenu <!--1428681-->

À partir d’octobre 2017, les applications Portail d’entreprise pour Windows 8.1 et Windows Phone 8.1 passent en mode soutenu. Cela signifie que les applications et les scénarios existants, comme l’inscription et la conformité, seront toujours pris en charge pour ces plateformes. Ces applications resteront disponibles au téléchargement par le biais des canaux de publication existants, comme Microsoft Store. 

Une fois en mode soutenu, ces applications recevront uniquement les mises à jour de sécurité critiques. Aucune mise à jour ou fonctionnalité supplémentaire ne sera publiée pour ces applications. Pour obtenir les nouvelles fonctionnalités, nous vous recommandons de mettre à jour les appareils vers Windows 10 ou Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Bloquer l’inscription des appareils Samsung Knox non pris en charge <!-- 1490695 -->

L’application Portail d’entreprise tente d’inscrire seulement les appareils Samsung Knox pris en charge. Pour éviter les erreurs d’activation Knox qui empêchent l’inscription à MDM, l’inscription des appareils est tentée seulement si l’appareil apparaît dans la [liste des appareils publiée par Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Les appareils Samsung peuvent avoir des numéros de modèles qui prennent en charge Knox, alors que d’autres ne le prennent pas en charge. Vérifiez la compatibilité de Knox auprès du revendeur de votre appareil avant l’achat et le déploiement. Vous pouvez trouver la liste complète des appareils vérifiés dans les [paramètres de stratégie Android et Samsung Knox Standard](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fin de la prise en charge d’Android 4.3 et antérieur <!-- 1171126, 1326920 -->
Les applications gérées et l’application Portail d’entreprise pour Android nécessiteront Android 4.4 et ultérieur pour accéder aux ressources de l’entreprise. En décembre, tous les appareils inscrits seront obligatoirement mis hors service et perdront l’accès aux ressources de l’entreprise. Si vous utilisez des stratégies de protection des applications sans MDM, les applications ne recevront aucune mise à jour et perdront en qualité au fil du temps.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Indiquer aux utilisateurs finaux quelles informations de leur appareil peuvent être vues sur les appareils inscrits <!--1165314-->
Nous ajoutons l’information **Type de propriété** dans l’écran des détails des appareils qui se trouve sur toutes les applications du portail d’entreprise. Ainsi, les utilisateurs ont accès à plus d’informations sur la confidentialité directement dans l’article [Quelles informations votre entreprise peut-elle voir ?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Ceci sera introduit dans toutes les applications du portail d’entreprise dans un futur proche. Nous avons annoncé ceci pour iOS en [septembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

## <a name="september-2017"></a>Septembre 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune prend en charge iOS 11 <!--1428975-->
Intune prend en charge iOS 11. Ceci avait été annoncé sur le [blog du support technique Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fin de la prise en charge d’iOS 8.0 <!-- 1164477 -->
Les applications gérées et l’application Portail d’entreprise pour iOS nécessiteront iOS 9.0 et ultérieur pour accéder aux ressources d’entreprise. Les appareils qui ne sont pas mis à jour avant septembre ne seront plus en mesure d’accéder au portail d’entreprise ni à ces applications. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Action d’actualisation ajoutée à l’application Portail d’entreprise pour Windows 10 <!--1132468-->
L’application Portail d’entreprise pour Windows 10 permet aux utilisateurs d’actualiser les données dans l’application avec une requête Pull pour actualiser ou, sur les postes de travail, en appuyant sur F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Utilisateurs finaux renseignés sur les informations de leur appareil qui sont consultables pour iOS <!--739894-->

Nous avons ajouté l’information **Type de propriété** dans l’écran des détails de l’appareil qui se trouve sur l’application Portail d’entreprise pour iOS. Ainsi, les utilisateurs auront accès à de plus amples informations sur la confidentialité directement sur cette page à partir de la documentation utilisateur Intune. Ils pourront également trouver cette information dans l’écran À propos de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Autoriser les utilisateurs finaux à accéder à l’application Portail d’entreprise pour Android sans inscription <!---1169910--->

Les utilisateurs finaux n’auront bientôt pas à inscrire leur appareil pour accéder à l’application Portail d’entreprise pour Android. Les utilisateurs finaux des organisations qui utilisent des stratégies de protection des applications ne recevront plus d’invites pour inscrire leur appareil quand ils ouvriront l’application Portail d’entreprise. Les utilisateurs finaux pourront également installer des applications à partir du portail d’entreprise sans inscrire l’appareil. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Formulation plus facile à comprendre pour l’application Portail d’entreprise pour Android <!---1396349--->  

Le processus d’inscription de l’application Portail d’entreprise pour Android a été simplifié à l’aide d’un nouveau texte afin de faciliter l’inscription des utilisateurs finaux. Si vous disposez d’une documentation personnalisée sur l’inscription, mettez-la à jour pour voir les nouveaux écrans. Vous trouverez des exemples d’images sur notre page [Mises à jour de l’interface utilisateur pour les applications utilisateur final Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Application Portail d’entreprise Windows 10 ajoutée à la stratégie d’autorisation Protection des informations Windows <!-- 677129 -->

L’application Portail d’entreprise Windows 10 a été mise à jour pour prendre en charge la Protection des informations Windows (WIP). L’application peut être ajoutée à la stratégie d’autorisation Protection des informations Windows. Grâce à cette modification, il n’est plus nécessaire d’ajouter l’application à la liste **Exempté**.


## <a name="august-2017"></a>Août 2017

### <a name="improvements-to-device-overview----1404453---"></a>Vue d’ensemble des améliorations apportées à l’appareil <!-- 1404453 -->  
La vue d’ensemble des améliorations apportées à l’appareil affiche à présent les appareils inscrits mais exclut les appareils gérés par Exchange ActiveSync. Les appareils Exchange ActiveSync n’ont pas les mêmes options de gestion que les appareils inscrits. Pour afficher le nombre d’appareils inscrits et le nombre d’appareils inscrits par plateforme dans le portail Azure d’Intune, accédez à **Appareils** > **Vue d’ensemble**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Améliorations apportées à l’inventaire des appareils collecté par Intune
<!-- 961134, 1104426, 1281327, 1333543 --> Dans cette version, nous avons apporté les améliorations suivantes aux informations d’inventaire collectées par les appareils que vous gérez :
 
-   Pour les appareils Android, vous pouvez maintenant ajouter une colonne à l’inventaire des appareils qui affiche le dernier niveau de correctif logiciel pour chaque appareil. Ajoutez la colonne **Niveau du correctif de sécurité** à votre liste d’appareils pour afficher cette information.
-   Quand vous filtrez la vue des appareils, vous pouvez désormais filtrer les appareils sur leur date d’inscription. Par exemple, vous pouvez afficher uniquement les appareils qui ont été inscrits après une date que vous spécifiez.
-   Nous avons apporté des améliorations au filtre utilisé par l’élément **Date du dernier archivage**.
-   Dans la liste des appareils, vous pouvez maintenant afficher le numéro de téléphone d’appareils appartenant à l’entreprise.
En outre, vous pouvez utiliser le volet de filtre pour rechercher des appareils par numéro de téléphone.
 
Pour plus d’informations sur l’inventaire des appareils, consultez [Guide d’affichage de l’inventaire des appareils Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Prise en charge de l’accès conditionnel pour les appareils macOS 
<!-- 720172 --> Vous pouvez maintenant définir une stratégie d’accès conditionnel exigeant que les appareils Mac soient inscrits dans Intune et conformes à ses stratégies de conformité des appareils. Par exemple, les utilisateurs peuvent télécharger l’application Portail d’entreprise Intune pour macOS et inscrire leurs appareils Mac dans Intune. Intune évalue si l’appareil Mac est conforme ou non aux spécifications telles que le code PIN, le chiffrement, la version du système d’exploitation et l’intégrité du système.

- Découvrez plus en détail la [prise en charge de l’accès conditionnel pour les appareils macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>L’application Portail d’entreprise pour macOS est en préversion publique <!---1484796--->
L’application Portail d’entreprise pour macOS est désormais disponible dans la préversion publique pour l’accès conditionnel dans Enterprise Mobility + Security. Cette version prend en charge macOS 10.11 et ultérieur. Obtenez-la à l’adresse [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10    
<!--1063965, 1308850  --> Dans cette version, nous avons ajouté de nouveaux paramètres pour le [profil de restriction d’appareil Windows 10](/intune/device-restrictions-windows-10) dans les catégories suivantes :

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Mises à jour du profil d’appareil Endpoint Protection Windows 10 pour les paramètres BitLocker
<!--1459533 -->    
Dans cette version, nous avons apporté les améliorations suivantes au fonctionnement des paramètres BitLocker dans un profil d’appareil Endpoint Protection Windows 10 :
 
Sous **Paramètres des lecteurs de système d’exploitation BitLocker**, pour le paramètre **BitLocker avec puce TPM non compatible**, quand vous sélectionniez **Bloquer**, auparavant, BitLocker aurait en fait été autorisé. Nous avons maintenant résolu ce problème pour bloquer BitLocker quand cette option est sélectionnée.
Sous **Paramètres des lecteurs de système d’exploitation BitLocker**, pour le paramètre **Agent de récupération de données basé sur les certificats**, vous pouvez maintenant bloquer explicitement l’agent de récupération de données basé sur le certificat. Toutefois, par défaut, l’agent est autorisé.
Sous **Paramètres des lecteurs de données fixes BitLocker**, pour le paramètre **Agent de récupération de données**, vous pouvez maintenant bloquer explicitement l’agent de récupération de données.
Pour plus d’informations, consultez [Paramètres Endpoint Protection pour Windows 10 et versions ultérieures](endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nouvelle expérience de connexion pour les utilisateurs du portail d’entreprise Android et les utilisateurs de stratégies de protection des applications <!-- 621669 -->
Les utilisateurs peuvent maintenant parcourir les applications, gérer les appareils et consulter les coordonnées du service informatique sur l’application du Portail d’entreprise Android sans inscrire leurs appareils Android. Par ailleurs, si un utilisateur final utilise déjà une application protégée par des stratégies Intune App Protection et qu’il lance le portail d’entreprise Android, il ne reçoit plus d’invite d’inscription pour son appareil.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nouveau paramètre dans l’application Portail d’entreprise Android pour activer/désactiver l’optimisation de batterie <!--1405990-->
La page **Paramètres** dans l’application Portail d’entreprise pour Android propose un nouveau paramètre qui permet aux utilisateurs de désactiver facilement l’optimisation de batterie pour les applications Portail d’entreprise et Microsoft Authenticator. Le nom de l’application qui est indiqué dans le paramètre varie en fonction de l’application qui gère le compte professionnel. Nous préconisons aux utilisateurs de désactiver l’optimisation de batterie pour améliorer les performances des applications professionnelles qui synchronisent les e-mails et les données. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Prise en charge de la multi-identité pour OneNote pour iOS      <!-- 1234281 -->
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
<!-- 1016201 --> Les administrateurs informatiques peuvent définir des stratégies conditionnelles basées sur l’application par le biais de la nouvelle interface utilisateur des stratégies d’accès conditionnel dans la charge de travail Azure AD. L’accès conditionnel basé sur l’application qui se trouve dans la section Protection d’application Intune dans Azure restera à cet endroit pour l’instant et sera appliqué côte à côte. Par souci pratique, un lien est également prévu vers la nouvelle interface utilisateur des stratégies d’accès conditionnel dans la charge de travail Intune.

- Découvrez plus en détail [l’accès conditionnel basé sur l’application sur Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Juillet 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restriction d’inscription d’appareils Android et iOS par version de système d’exploitation <!--- 1333256,  1245463 --->
Intune prend désormais en charge la restriction d’inscription d’appareils Android et iOS par numéro de version de système d’exploitation. Sous **Restriction de type d’appareil**, l’administrateur informatique peut désormais définir une configuration de plateforme pour restreindre l’inscription à une plage de valeurs de système d’exploitation minimale et maximale. Les versions du système d’exploitation Android doivent être spécifiées au format Majeure.Mineure.Build.Révision, où Mineure, Build et Révision sont facultatifs. Les versions d’iOS doivent être spécifiées au format Majeure.Mineure.Build, où Build est facultatif. Découvrez plus d’informations sur les [restrictions d’inscription d’appareils](enrollment-restrictions-set.md).

>[!NOTE]
>Ne limite pas l’inscription avec des programmes d’inscription Apple ou Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Limiter l’inscription des appareils personnels Android, iOS et macOS <!--- 1333272,  1333275, 1245709 --->
Intune peut limiter l’inscription d’appareils personnels avec des listes vertes de numéros IMEI d’appareils d’entreprise. Intune a récemment étendu cette fonctionnalité à iOS, Android et macOS avec des numéros de série d’appareils. En chargeant les numéros de série sur Intune, vous pouvez prédéclarer des appareils comme appartenant à l’entreprise. Les restrictions d’inscription vous permettent de bloquer les appareils personnels (BYOD), ce qui permet l’inscription des appareils de l’entreprise uniquement. Découvrez plus d’informations sur les [restrictions d’inscription d’appareils](enrollment-restrictions-set.md).

Pour importer des numéros de série, accédez à **Inscription d’appareil** > **Identificateurs d’appareil d’entreprise** et cliquez sur **Ajouter**, puis chargez un fichier .CSV (pas d’en-tête, deux colonnes pour le numéro de série et des détails comme les numéros IMEI).  Pour restreindre les appareils personnels, accédez à **Inscription d’appareil** > **Restrictions d’inscription**. Sous **Restrictions de type d’appareil**, sélectionnez **Par défaut**, puis **Configurations de plateforme**. Vous pouvez **Autoriser** ou **Bloquer** les appareils personnels pour iOS, Android et macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nouvelle action de l’appareil pour forcer les appareils à la synchronisation avec Intune<!-- 711369 -->
Dans cette version, nous avons ajouté une nouvelle action qui force l’appareil sélectionné à s’enregistrer immédiatement auprès d’Intune. Quand un appareil s’enregistre, il reçoit immédiatement les actions ou les stratégies en attente qui lui ont été affectées.  Cette action peut vous aider à valider et corriger immédiatement les stratégies que vous avez affectées, sans attendre le prochain enregistrement planifié.
Pour plus d’informations, consultez [Synchroniser un appareil](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour logicielle disponible<!-- 777100 -->
Une nouvelle stratégie est disponible dans l’espace de travail des mises à jour logicielles, qui vous permet de forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour logicielle disponible. Pour plus d’informations, consultez [Configurer les stratégies de mise à jour iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile : nouveau partenaire de Mobile Threat Defense <!-- 954651, 1172027 -->
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

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Prise en charge des iBooks pour le site web Portail d'entreprise <!--1231841-->
Nous avons ajouté une page dédiée au site web Portail d'entreprise qui permet aux utilisateurs de parcourir et de télécharger des iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Détails supplémentaires de résolution des problèmes pour le support technique<!---  Applies to 1263399, 1326964, 1341642 --->
Intune a mis à jour l’affichage de la résolution des problèmes et a ajouté aux informations qu’il fournit des informations pour les administrateurs et le personnel du support technique. Vous pouvez maintenant voir un tableau **Attributions** qui récapitule toutes les attributions de l’utilisateur en fonction de l’appartenance au groupe. La liste comprend :
- Applications mobiles
- Stratégies de conformité
- Profils de configuration
 
Par ailleurs, le tableau **Appareils** inclut désormais les colonnes **Type de jointure Azure AD** et **Conforme Azure AD**. Pour plus d’informations, consultez [Aider les utilisateurs à résoudre les problèmes](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Entrepôt de données Intune (préversion publique)
L’entrepôt de données Intune échantillonne quotidiennement les données pour fournir une vue historique de votre locataire. Vous pouvez accéder aux données via un fichier Power BI (PBIX), via un lien OData qui est compatible avec de nombreux outils analytiques ou en interagissant avec l’API REST. Pour plus d’informations, consultez [Utiliser l’entrepôt de données Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modes clair et sombre disponibles pour l’application Portail d’entreprise pour Windows 10 <!---676547--->
Les utilisateurs finaux seront en mesure de personnaliser le mode de couleur de l’application Portail d’entreprise pour Windows 10. Ils pourront apporter la modification dans la section Paramètres de l’application Portail d’entreprise. Le changement apparaîtra une fois que les utilisateurs auront redémarré l’application. Pour Windows 10 versions 1607 et ultérieures, le mode des applications est par défaut le paramètre système. Pour Windows 10 versions 1511 et antérieures, le mode des applications est par défaut le mode clair.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permettre aux utilisateurs finaux de baliser leur groupe d’appareils dans l’application Portail d’entreprise pour Windows 10 <!---807046-->
Les utilisateurs finaux peuvent désormais sélectionner le groupe auquel leur appareil appartient, en le balisant directement à partir de l’application Portail d’entreprise pour Windows 10.



## <a name="june-2017"></a>Juin 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nouvel accès à l’administration basée sur les rôles pour les administrateurs Intune <!-- 1099990 -->  
Un nouveau rôle d’administrateur d’accès conditionnel est ajouté pour afficher, créer, modifier et supprimer des stratégies d’accès conditionnel dans Azure AD. Auparavant, seuls les administrateurs de sécurité et les administrateurs globaux disposaient de cette autorisation. Les administrateurs Intune peuvent obtenir cette autorisation de rôle afin d’avoir accès aux stratégies d’accès conditionnel.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Marquer les appareils d’entreprise avec un numéro de série <!-- 1215070 -->  
Intune prend désormais en charge le chargement de numéros de série iOS, macOS et Android en tant qu’identificateurs d’appareil d’entreprise. Vous ne pouvez pas utiliser les numéros de série pour empêcher des appareils personnels de s’inscrire pour le moment, car les numéros de série ne sont pas vérifiés lors de l’inscription. Le blocage des appareils personnels par numéro de série sera disponible dans un futur proche.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nouvelles actions à distance pour les appareils iOS <!-- 854689 -->
Dans cette version, nous avons ajouté deux actions à distance pour les appareils iPad partagés qui gèrent l’application Apple Classroom :

-   [Déconnecter l’utilisateur actuel](device-logout-user.md) : déconnecte l’utilisateur actuel d’un appareil iOS que vous choisissez.
-   [Supprimer l’utilisateur](device-remove-user.md) : supprime un utilisateur que vous choisissez dans le cache local sur un appareil iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Prise en charge des iPad partagés avec l’application Classroom d’iOS<!-- 1044681 -->
Dans cette version, nous avons développé la prise en charge de la gestion de l’application Classroom iOS afin d’inclure les étudiants qui se connectent à des iPad partagés à l’aide de leur ID Apple géré.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Modifications apportées aux applications intégrées Intune<!-- 1332306 -->
Intune contenait auparavant un certain nombre d’applications intégrées que l’on pouvait affecter rapidement. En réponse à vos commentaires, nous avons supprimé cette liste et ces applications intégrées n’apparaîtront plus.
Toutefois, si vous avez déjà affecté des applications intégrées, elles resteront visibles dans la liste des applications. Vous pouvez continuer à affecter ces applications en fonction de vos besoins.
Dans une version ultérieure, nous prévoyons d’ajouter une méthode plus simple pour sélectionner et affecter les applications intégrées à partir du portail Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Installation plus facile des applications Office 365 <!--- 1121362 --->
À l’aide du nouveau type d’application **Office 365 ProPlus**, vous pouvez affecter facilement des applications Office 365 ProPlus 2016 aux appareils que vous gérez et qui exécutent la dernière version de Windows 10. Vous pouvez également installer Microsoft Project et Microsoft Visio si vous disposez des licences appropriées. Les applications souhaitées sont regroupées et apparaissent sous la forme d’une application unique dans la liste des applications de la console Intune.
Pour plus d’informations, consultez [Guide pratique pour ajouter des applications Office 365 pour Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises <!--- 777044 --->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez alors déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications en mode hors connexion sont installées par Intune et non par le Store.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Les équipes Microsoft font désormais partie de la liste d’Autorités de certification basée sur l’application des applications approuvées<!-- 1257019 -->
L’application Microsoft Teams pour iOS et Android fait désormais partie des applications approuvées pour les stratégies d’accès conditionnel basé sur l’application pour Exchange et SharePoint Online. L’application peut être configurée via le panneau Intune App Protection dans le portail Azure pour tous les clients utilisant actuellement l’accès conditionnel basé sur l’application.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Managed Browser et intégration du proxy d’application <!-- 1287310 -->
Intune Managed Browser peut maintenant s’intégrer au service du proxy d’application Azure AD pour permettre aux utilisateurs d’accéder aux sites web internes même quand ils travaillent à distance. Les utilisateurs du navigateur entrent simplement l’URL du site comme ils le font normalement et Managed Browser achemine la demande via la passerelle web du proxy d’application. Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nouveaux paramètres de configuration d’application pour Intune Managed Browser <!-- 682951 -->
Dans cette version, nous avons ajouté des configurations supplémentaires pour l’application Intune Managed Browser pour iOS et Android. Vous pouvez maintenant utiliser une stratégie de configuration d’application pour configurer la page d’accueil par défaut et les signets du navigateur.
Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Paramètres BitLocker pour Windows 10 <!-- 951707 -->
Vous pouvez maintenant configurer des paramètres BitLocker pour les appareils Windows 10 à l’aide d’un nouveau profil d’appareil Intune. Par exemple, vous pouvez exiger que les appareils soient chiffrés et configurer également d’autres paramètres qui sont appliqués quand BitLocker est activé.
Pour plus d’informations, consultez [Paramètres Endpoint Protection pour Windows 10 et versions ultérieures](endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nouveaux paramètres pour le profil de restriction d’appareils Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
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

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nouvelle action de menu pour supprimer facilement le portail d’entreprise <!--1164569-->
Suite aux commentaires des utilisateurs, l’application Portail d’entreprise pour Android offre désormais une nouvelle action de menu pour lancer la suppression du portail d’entreprise à partir de votre appareil. Cette action supprime l’appareil de gestion Intune afin que l’application puisse être supprimée de l’appareil par l’utilisateur. Vous pouvez voir ces modifications sur la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md) et dans la [documentation pour les utilisateurs finaux d’Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Améliorations apportées à la synchronisation des applications avec Windows 10 Creators Update<!--676505-->
L’application Portail d’entreprise pour Windows 10 démarre maintenant automatiquement une synchronisation pour les demandes d’installation d’application sur les appareils exécutant Windows 10 Creators Update (version 1703). Cela permet de réduire le problème de blocage des installations d’applications à l’état « Synchronisation en attente ». En outre, les utilisateurs pourront lancer manuellement une synchronisation à partir de l’application. Vous pouvez afficher ces modifications dans la page [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nouvelle expérience interactive pour le portail d’entreprise Windows 10 <!---1058938--->
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

## <a name="may-2017"></a>Mai 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Changer votre autorité de gestion des appareils mobiles sans annuler l’inscription des appareils gérés <!--1103950-->
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

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nouvelles conditions de stratégies de protection des applications pour la GAM<!-- 679864 -->

Vous pouvez maintenant définir un ensemble de spécifications de GAM pour les utilisateurs sans inscription qui applique les éléments suivants :

- Version minimale de l’application
- Version minimale du système d’exploitation
- Version minimale du SDK d’application Intune de l’application cible (iOS uniquement)

Cette fonctionnalité est disponible sur iOS et Android. Intune prend en charge l’application de la version minimale pour les versions de plateformes de système d’exploitation, les versions d’applications et le SDK d’application Intune. Sur iOS, les applications intégrées au SDK peuvent également définir l’application de la version minimale au niveau du SDK. L’utilisateur ne peut pas accéder à l’application cible si la configuration minimale requise par la stratégie de protection des applications n’est pas satisfaite aux trois niveaux différents mentionnés ci-dessus. À ce stade, l’utilisateur peut supprimer son compte (pour les applications à plusieurs identités), fermer l’application et/ou mettre à jour la version de son système d’exploitation ou de l’application.

De plus, vous pouvez configurer des paramètres supplémentaires pour fournir une notification non bloquante qui recommande une mise à niveau du système d’exploitation ou de l’application. Cette notification peut être fermée et l’application peut être utilisée normalement.

Pour plus d’informations, consultez les [paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md) et les [paramètres de stratégie de protection des applications Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurer les configurations d’application pour Android for Work <!-- 621621 -->
Certaines applications Android du Store prennent en charge des options de configuration gérées qui permettent à un administrateur informatique de contrôler la façon dont une application s’exécute dans le profil de travail. Avec Intune, vous pouvez désormais afficher les configurations prises en charge par une application et les configurer à partir du portail Azure avec un concepteur de configuration ou dans un éditeur JSON. Pour plus d’informations, consultez [Utiliser des configurations d’application pour Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nouvelle fonctionnalité de configuration d’application pour la gestion des applications mobiles sans inscription <!-- 677969 -->
Vous pouvez désormais créer des stratégies de configuration d’application via la gestion des applications mobiles sans canal d’inscription. Cette fonctionnalité équivaut aux stratégies de configuration d’application disponibles dans la configuration de l’application de Gestion des appareils mobiles (MDM). Pour un exemple de configuration d’application avec gestion des applications mobiles sans inscription, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurer des listes d’URL autorisées et bloquées pour Managed Browser <!-- 682960 -->
Vous pouvez désormais configurer une liste de domaines et d’URL autorisés et bloqués pour Intune Managed Browser avec les paramètres de configuration d’application dans le portail Azure. Vous pouvez configurer ces paramètres même s’il est utilisé sur un appareil non géré. Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Vue du support technique pour les stratégies de protection d’application <!-- 1069473 -->
Les utilisateurs du support technique informatique peuvent désormais vérifier l’état des licences utilisateur et l’état des applications de stratégie de protection d’application affectées aux utilisateurs dans le panneau de la résolution des problèmes. Pour plus d’informations, consultez [Résolution des problèmes](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Visites pour le site web de contrôle sur les appareils iOS <!-- 723832 -->
Vous pouvez maintenant contrôler les sites web auxquels les utilisateurs d’appareils iOS peuvent accéder à l’aide de l’une des deux méthodes suivantes :

- Ajouter des URL autorisées et bloquées à l’aide du filtrage de contenu web intégré d’Apple.

- Autoriser uniquement l’accès aux sites web spécifiés par le navigateur Safari. Des signets sont créés dans Safari pour chaque site que vous spécifiez.

Pour plus d’informations, consultez [Paramètres de filtre de contenu web pour les appareils iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Préconfigurer les autorisations d’appareils pour les applications Android for Work<!-- 621614 -->
Pour les applications déployées sur des profils professionnels Android for Work, vous pouvez maintenant configurer l’état des autorisations pour chacune des applications.  Par défaut, les applications Android qui nécessitent des autorisations d’appareils telles que l’accès à l’emplacement ou à l’appareil photo invitent les utilisateurs à accepter ou à refuser les autorisations.  Par exemple, si une application utilise le microphone de l’appareil, l’utilisateur final est invité à autoriser l’application à utiliser le microphone. Cette fonctionnalité vous permet de définir des autorisations pour le compte de l’utilisateur final.  Vous pouvez configurer des autorisations pour a) refuser automatiquement sans en avertir l’utilisateur, b) automatiquement approuver sans en avertir l’utilisateur, ou c) inviter l’utilisateur à accepter ou refuser. Pour plus d’informations, consultez [Paramètres de restriction des appareils Android for Work dans Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Définir un code PIN propre à l’application pour les appareils Android for Work<!-- 728976, 1102534 -->
Vous pouvez définir une stratégie de mot de passe qui s’applique uniquement aux applications dans le profil professionnel pour les appareils Android 7.0 et versions ultérieures avec un profil de travail géré en tant qu’appareil Android for Work.  Les options sont les suivantes :

- Définir simplement une stratégie de mot de passe au niveau de l’appareil : il s’agit du code secret que l’utilisateur final doit utiliser pour déverrouiller son appareil.
- Définir simplement une stratégie de mot de passe de profil professionnel : les utilisateurs sont invités à entrer un code secret chaque fois qu’une application dans le profil professionnel est ouverte.
- Définir à la fois une stratégie d’appareil et une stratégie de profil professionnel : l’administrateur informatique peut définir à la fois une stratégie de code secret d’appareil et une stratégie de code secret de profil professionnel à des niveaux différents (par exemple, un code PIN à quatre chiffres pour déverrouiller l’appareil, mais un code PIN à six chiffres pour ouvrir une application professionnelle).

Pour plus d’informations, consultez [Paramètres de restriction des appareils Android for Work dans Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Cette fonctionnalité est uniquement disponible sur Android 7.0 et versions ultérieures.  Par défaut, l’utilisateur final peut utiliser les deux codes PIN définis séparément, ou il peut choisir de combiner les deux codes PIN définis dans le plus sécurisé des deux.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nouveaux paramètres pour les appareils Windows 10 <!-- 978585 -->
Nous avons ajouté [de nouveaux paramètres de restriction d’appareil Windows](device-restrictions-windows-10.md) qui contrôlent des fonctionnalités telles que les affichages sans fil, la détection des appareils, le basculement de tâche et les messages d’erreur de carte SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Mises à jour à la configuration de certificat <!-- 918991 and 823198 -->
Lors de la création d’un profil de certificat SCEP, l’option <strong>Personnalisé</strong> option est disponible pour <strong>Format du nom du sujet</strong> sur les appareils iOS, Android et Windows. Avant cette mise à jour, le champ <strong>Personnalisé</strong> était disponible pour les appareils iOS uniquement. Pour plus d’informations, consultez [Create a SCEP certificate profile](certificates-scep-configure.md#create-a-scep-certificate-profile) (Créer un profil de certificat SCEP).

Lors de la création d’un profil de certificat PKCS, pour **Autre nom de l’objet**, **Attribut personnalisé Azure AD** est disponible. L’option **Service** est disponible lorsque vous sélectionnez **Attribut personnalisé Azure AD**. Pour plus d’informations, consultez [Créer un profil de certificat PKCS](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurer plusieurs applications qui peuvent s’exécuter quand un appareil Android est en mode plein écran <!-- 662059 -->
Lorsqu’un appareil Android est en mode plein écran, vous ne pouviez précédemment configurer qu’une application autorisée à s’exécuter. Vous pouvez désormais configurer plusieurs applications à l’aide de l’ID d’application ou de l’URL du Store, ou en sélectionnant une application Android que vous gérez déjà. Pour plus d’informations, consultez [Paramètres du mode plein écran](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Avril 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Prise en charge de la gestion de l’application Apple Classroom
Vous pouvez désormais gérer l’application iOS Classroom sur des appareils iPad. Configurez l’application Classroom sur l’iPad des enseignants avec les données sur les étudiants et les cours appropriées, puis configurez les iPad des étudiants inscrits à un cours, afin que vous puissiez les contrôler à l’aide de l’application.
Pour plus d’informations, consultez [Configurer les paramètres d’éducation iOS](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Prise en charge des options de configuration gérées pour les applications Android <!-- 621621 -->
Les applications Android du Play Store qui prennent en charge les options de configuration gérées peuvent désormais être configurées par Intune.  Cette fonctionnalité permet au personnel informatique d’afficher la liste des valeurs de configuration prises en charge par une application, et fournit une interface interactive et guidée de premier plan pour lui permettre de configurer ces valeurs.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nouvelle stratégie Android pour les codes PIN complexes <!-- 722069 -->
Vous pouvez maintenant définir un type de [mot de passe](device-restrictions-android.md#password) requis « Chiffres complexes » dans un profil d’appareil Android pour les appareils qui exécutent Android 5.0 et versions ultérieures.  Utilisez ce paramètre pour empêcher les utilisateurs d’appareils de créer un code PIN qui contient des nombres répétés ou consécutifs, tel que 1111 ou 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Prise en charge supplémentaire des appareils Android for Work
- **Gérer les paramètres de profil professionnel et de mot de passe** <!-- 612808 -->

  Cette nouvelle stratégie de restriction d’appareil Android for Work vous permet maintenant de gérer les paramètres de profil professionnel et de mot de passe sur les appareils Android for Work que vous gérez.

- **Autoriser le partage de données entre profils professionnels et personnels** <!-- 1045102 -->

Ce profil de restriction d’appareil Android for Work a été enrichi de nouvelles options afin de vous aider à configurer le partage de données entre vos profils personnels et professionnels.

- **Limiter la copie et le collage entre profils professionnels et personnels** <!-- 1046094 -->

  Ce nouveau profil d’appareil personnalisé pour les appareils Android for Work vous permet de désormais limiter les actions Copier et Coller entre applications professionnelles et personnelles.

Pour plus d’informations, consultez [Device restrictions for Android for Work](device-restrictions-android-for-work.md) (Restrictions d’appareils pour Android for Work).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Affecter des applications métier aux appareils iOS et Android <!-- 1057568 -->
Vous pouvez désormais affecter des applications métier pour [iOS](lob-apps-ios.md) (fichiers .ipa) et [Android](lob-apps-android.md) (fichiers .apk) à des utilisateurs ou des appareils.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nouvelles stratégies d’appareil pour iOS <!-- 723774, 723815, 723826, 723830 -->
- **Applications dans l’écran d’accueil** : contrôle les applications qui s’affichent dans [l’écran d’accueil de l’appareil iOS](home-screen-settings-ios.md) d’un utilisateur. Cette stratégie change la disposition de l’écran d’accueil, mais ne déploie aucune application.

- **Connexions aux appareils AirPrint** : contrôle les [appareils AirPrint](air-print-settings-ios-macos.md) (imprimantes réseau) auxquels les utilisateurs finaux d’appareils iOS peuvent se connecter.

- **Connexions aux appareils AirPlay** : contrôle les [appareils AirPlay](airplay-settings-ios.md) (comme Apple TV) auxquels les utilisateurs finaux d’appareils iOS peuvent se connecter.

- **Message d’écran de verrouillage personnalisé** : permet de configurer un message personnalisé qui s’affiche sur l’écran de verrouillage des appareils iOS à la place du message d’écran de verrouillage par défaut. Pour plus d’informations, consultez [Activer le mode Perdu sur les appareils iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restreindre les notifications Push pour les applications iOS <!-- 723767 -->
Dans un profil de restriction d’appareil Intune, vous pouvez maintenant configurer les [paramètres de notification](app-notification-settings-ios.md) suivants pour les appareils iOS :

- Activer ou désactiver entièrement la notification pour une application spécifiée.
- Activer ou désactiver la notification dans le Centre de notification pour une application spécifiée.
- Spécifier le type d’alerte : **Aucune**, **Bannière** ou **Alerte modale**.
- Spécifier si les badges sont autorisés pour cette application.
- Spécifier si les sons de notification sont autorisés.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurer les applications iOS pour s’exécuter en mode Application unique autonome <!-- 737837 -->
Vous pouvez désormais utiliser un profil d’appareil Intune pour configurer les appareils iOS pour qu’ils exécutent les applications spécifiées en [mode Application unique autonome](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé et il ne peut exécuter que cette application. Vous pouvez par exemple utiliser ce mode quand vous configurez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurer des domaines approuvés pour l’e-mail et la navigation web sur des appareils iOS <!-- 723765 -->
À partir d’un profil de restriction d’appareil iOS, vous pouvez maintenant configurer les [paramètres de domaine suivants](device-restrictions-ios.md#domains) :

- **Domaines d’e-mail non marqués** - Les e-mails reçus ou envoyés par l’utilisateur qui ne correspondent pas aux domaines que vous spécifiez ici sont marqués comme non approuvés.

- **Domaines web gérés** - Les documents téléchargés à partir des URL que vous spécifiez ici sont considérés comme gérés (Safari uniquement).  

- **Domaines de remplissage automatique des mots de passe Safari** - Les utilisateurs peuvent enregistrer des mots de passe dans Safari uniquement à partir des URL qui correspondent aux modèles que vous spécifiez ici. Pour utiliser ce paramètre, il faut que l’appareil soit en mode supervisé et non configuré pour plusieurs utilisateurs. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Applications VPP disponibles dans le portail d’entreprise iOS <!-- 748782 -->
Vous pouvez désormais affecter des applications achetées en volume (VPP) iOS comme installations **disponibles** pour les utilisateurs finaux. Ces derniers auront besoin d’un compte Apple Store pour installer l’application.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synchroniser des livres électroniques à partir de l’Apple VPP Store <!-- 800878 -->
Vous pouvez maintenant [synchroniser les livres](vpp-apps-ios.md) que vous avez achetés dans le Store VPP (Programme d’achat en volume) d’Apple avec Intune, et les attribuer à des utilisateurs.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestion des utilisateurs multiples pour les appareils Samsung Knox Standard <!-- 971988 -->
Les appareils qui exécutent Samsung Knox Standard sont désormais pris en charge pour la [gestion des utilisateurs multiples](android-enroll.md) par Intune. Cela signifie que les utilisateurs finaux peuvent se connecter et se déconnecter de l’appareil avec leurs informations d’identification Azure Active Directory, et que l’appareil est géré de façon centralisée qu’il soit en cours d’utilisation ou non.  Quand les utilisateurs finaux se connectent, ils ont accès aux applications et les éventuelles stratégies sont appliquées à ces applications. Quand les utilisateurs se déconnectent, toutes les données d’application sont effacées.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Paramètres supplémentaires de restriction d’appareil Windows <!-- 818566 -->
Nous avons ajouté la prise en charge d’autres [paramètres de restriction d’appareil Windows](device-restrictions-windows-10.md), comme une prise en charge supplémentaire du navigateur Edge, la personnalisation de l’écran de verrouillage d’appareil, la personnalisation du menu Démarrer, les papiers peints Windows à la une et les paramètres de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Prise en charge multi-utilisateur pour Windows 10 Creators Update <!-- 822547 -->
Nous avons ajouté la prise en charge de la [gestion des utilisateurs multiples](windows-enroll.md) pour les appareils qui exécutent Windows 10 Creators Update et sont joints à un domaine Azure Active Directory. Cela signifie que quand différents utilisateurs standard se connectent à l’appareil avec leurs informations d’identification Azure AD, ils reçoivent les applications et les stratégies qui ont été affectées à leur nom d’utilisateur. Les utilisateurs ne peuvent actuellement pas utiliser le portail d’entreprise pour les scénarios de libre-service tels que l’installation d’applications.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start pour les PC Windows 10<!-- 1004830 -->
Une nouvelle [action d’appareil Fresh Start](device-fresh-start.md) est maintenant disponible pour les PC Windows 10.  Quand vous exécutez cette action, les applications qui ont été installées sur l’ordinateur sont supprimées, et le PC est automatiquement mis à jour vers la dernière version de Windows. Vous pouvez ainsi supprimer des applications OEM préinstallées, comme celles qui sont souvent fournies avec un nouveau PC. Vous pouvez configurer si les données utilisateur sont conservées quand cette action est exécutée sur l’appareil.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Chemins de mise à niveau Windows 10 supplémentaires <!-- 903672 -->
Vous pouvez désormais créer une [stratégie de mise à niveau d’édition pour mettre à niveau les appareils](edition-upgrade-configure-windows-10.md) vers les éditions Windows 10 supplémentaires suivantes :

- Windows 10 Professionnel
- Windows 10 Professionnel N
- Windows 10 Professionnel Éducation
- Windows 10 Professionnel Éducation N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscription en bloc des appareils Windows 10 <!-- 747607 -->
Vous pouvez désormais joindre un grand nombre d’appareils qui exécutent la mise à jour Windows 10 Creators pour Azure Active Directory et Intune à l’aide du Concepteur de configuration Windows (WCD). Pour activer [l’inscription MDM en bloc](windows-bulk-enroll.md) pour votre client Azure AD, créez un package de configuration qui joint les appareils à votre client Azure AD à l’aide du Concepteur de configuration Windows, puis appliquez le package aux appareils d’entreprise que vous souhaitez inscrire et gérer en bloc. Une fois le package appliqué à vos appareils, ceux-ci se connectent à Azure AD, s’inscrivent dans Intune et vos utilisateurs Azure AD peuvent s’y connecter.  Les utilisateurs d’Azure AD agissent sur ces appareils en tant qu’utilisateurs standard ; ils reçoivent les stratégies qui leur sont affectées ainsi que les applications dont ils ont besoin. Les scénarios de libre-service et de portail d’entreprise ne sont pas pris en charge actuellement.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nouveaux paramètres GAM pour les codes PIN et les emplacements de stockage géré <!-- 581122, 736644 -->
Deux nouveaux paramètres d’application sont désormais disponibles pour vous aider dans les scénarios de gestion des applications mobiles (GAM) :

- **Désactiver le code PIN de l’application quand le code PIN de l’appareil est géré** - Détecte si un code PIN d’appareil est présent sur l’appareil inscrit et, si c’est le cas, contourne le code PIN de l’application déclenché par les stratégies de protection des applications. Ce paramètre permet de réduire le nombre d’invites de code PIN pour les utilisateurs ouvrant une application GAM sur un appareil inscrit. Cette fonctionnalité est disponible pour iOS et Android.

- **Sélectionnez dans quels services de stockage les données d’entreprise peuvent être enregistrées** - Permet de spécifier les emplacements de stockage où enregistrer les données d’entreprise. Les utilisateurs peuvent enregistrer dans les services d’emplacement de stockage sélectionnés, ce qui signifie que tous les autres services d’emplacement de stockage non répertoriés seront bloqués.

  Liste des services d’emplacement de stockage pris en charge :

  - OneDrive Entreprise
  - SharePoint Online
  - Stockage local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portail de dépannage du centre de support technique <!-- 907448 -->
Le nouveau [portail de dépannage](help-desk-operators.md) permet aux opérateurs du centre de support technique et aux administrateurs Intune de visualiser les utilisateurs et leurs appareils, et d’effectuer des tâches pour résoudre les problèmes techniques liés à Intune.

## <a name="march-2017"></a>Mars 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Prise en charge du mode Perdu iOS<!--431695-->
Pour les appareils iOS 9.3 et versions ultérieures, Intune a ajouté la prise en charge du **Mode Perdu**. Vous pouvez maintenant verrouiller un appareil pour éviter toute utilisation et afficher un numéro de téléphone de contact et un message sur l’écran de verrouillage de l’appareil.

L’utilisateur final ne peut pas déverrouiller l’appareil tant qu’un administrateur n’a pas désactivé le mode Perdu. Lorsque le mode Perdu est activé, vous pouvez utiliser l’action **Localiser l’appareil** pour afficher l’emplacement géographique de l’appareil sur une carte dans la console Intune.

L’appareil doit être un appareil iOS d’entreprise, inscrit via le programme DEP, qui est en mode supervisé.

Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md)

### <a name="improvements-to-device-actions-report---677150--"></a>Améliorations du rapport Actions de l’appareil <!--677150-->
Nous avons apporté des améliorations au rapport Actions de l’appareil afin d’optimiser les performances. En outre, il est désormais possible de filtrer le rapport par état. Par exemple, vous pouvez filtrer le rapport pour qu’il affiche uniquement les actions d’appareil qui ont été effectuées.

### <a name="custom-app-categories---748805--"></a>Catégories d’applications personnalisées <!--748805-->
Vous pouvez désormais créer, modifier et attribuer des catégories pour les applications que vous ajoutez à Intune. Actuellement, les catégories ne peuvent être spécifiées qu'en anglais.
Consultez [Guide pratique pour ajouter une application à Intune](apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Attribuer des applications cœur de métier aux utilisateurs disposant d’appareils non inscrits <!--748823-->
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


## <a name="february-2017"></a>Février 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilité de limiter l’inscription des appareils mobiles <!--747600, 795782-->
Intune ajoute de nouvelles restrictions d’inscription qui contrôlent les plateformes d’appareils mobiles autorisées à être inscrites. Intune sépare les plateformes d’appareils mobiles comme iOS, MacOS, Android, Windows et Windows Mobile.

* La restriction de l’inscription d’appareils mobiles ne limite pas l’inscription des clients de PC.  
* Pour iOS et Android uniquement, il existe une option supplémentaire pour bloquer l’inscription des appareils personnels.

Intune marque tous les nouveaux appareils comme personnels, sauf si l’administrateur prend des mesures pour les marquer comme appareils d’entreprise, comme expliqué dans [cet article](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Afficher toutes les actions sur les appareils gérés <!--677150-->
Un nouveau rapport __Actions de l’appareil__ indique l’utilisateur qui a effectué des actions à distance, comme un rétablissement des paramètres d’usine sur les appareils, et montre également l’état de cette action. Consultez [Qu’est-ce que la gestion des appareils ?](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Les appareils non gérés peuvent accéder aux applications attribuées <!--664691-->
Dans le cadre des modifications conceptuelles du site web du portail d’entreprise, les utilisateurs iOS et Android peuvent installer les applications attribuées indiquées comme « disponibles sans inscription » sur leurs appareils non gérés. À l’aide de leurs informations d’identification Intune, les utilisateurs peuvent se connecter au site web du portail d’entreprise et afficher la liste des applications qui leur sont attribuées. Les packages des applications « disponibles sans inscription » peuvent être téléchargés sur le site web du portail d’entreprise. Les applications dont l’installation nécessite une inscription ne sont pas affectées par cette modification, car les utilisateurs sont invités à inscrire leur appareil s’ils souhaitent installer ces applications.

### <a name="custom-app-categories---748805--"></a>Catégories d’applications personnalisées <!--748805-->
Vous pouvez désormais créer, modifier et attribuer des catégories pour les applications que vous ajoutez à Intune. Actuellement, les catégories ne peuvent être spécifiées qu'en anglais.
Consultez [Guide pratique pour ajouter une application à Intune](apps-add.md).

### <a name="display-device-categories---814654--"></a>Afficher des catégories d’appareils <!--814654-->
Vous pouvez maintenant afficher la catégorie d’appareil sous forme de colonne dans la liste des appareils. Vous pouvez également modifier la catégorie dans la section des propriétés du panneau Propriétés de l’appareil. Consultez [Guide pratique pour ajouter une application à Intune](apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurer les paramètres Windows Update for Business <!--776716-->

Windows en tant que service est la nouvelle façon de fournir des mises à jour pour Windows 10. À partir de Windows 10, les nouvelles mises à jour de fonctionnalités et qualité incluent le contenu de toutes les mises à jour précédentes. Cela signifie que tant que vous avez installé la dernière mise à jour, vous savez que vos appareils Windows 10 sont entièrement à jour. À la différence des versions précédentes de Windows, vous devez maintenant installer la mise à jour complète au lieu d’une partie seulement.

En utilisant Windows Update for Business, vous pouvez simplifier l’expérience de gestion des mises à jour et vous ne devez plus approuver des mises à jour propres à des groupes d’appareils. Vous pouvez toujours gérer les risques dans votre environnement en configurant une stratégie de déploiement de mises à jour afin que Windows Update fasse en sorte que les mises à jour soient installées au moment opportun. Microsoft Intune permet de configurer les paramètres de mise à jour des appareils et vous donne la possibilité de reporter l’installation des mises à jour. Intune ne stocke pas les mises à jour, seulement l’attribution des stratégies de mise à jour. Les appareils accèdent directement à Windows Update. Utilisez Intune pour configurer et gérer les **anneaux de mise à jour Windows 10**. Un anneau de mise à jour contient un groupe de paramètres permettant de configurer le moment et la façon d’installer les mises à jour Windows 10. Pour plus d’informations, consultez [Configurer les paramètres Windows Update for Business](windows-update-for-business-configure.md).
