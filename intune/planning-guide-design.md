---
title: Créer un design
titlesuffix: Microsoft Intune
description: Cet article vous permet de créer une conception dans le cadre de la conception et de l'implémentation d'un cloud Microsoft Intune uniquement.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.openlocfilehash: 1d8ccd4e432623cf7d0ce4ce66651a95e13b8473
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186492"
---
# <a name="create-a-design"></a>Créer un design

Votre conception Intune est basée sur les informations que vous collectez et les décisions que vous prenez quand vous effectuez les autres [sections de ce guide](planning-guide.md). Elle vous permet de rassembler :

-   L'environnement actuel

-   Options de déploiement Intune

-   Conditions d’identité requises pour les dépendances externes

-   Considérations relatives aux plateformes d'appareils

-   Conditions requises pour la remise  

Bien qu’il existe des conditions minimales concernant l’infrastructure en local, un plan de conception est toujours utile pour vérifier que vous disposez d’une solution de gestion d’appareils mobiles adéquate qui répond à vos objectifs et exigences.

Examinons chacun de ces domaines plus en détail. 

## <a name="record-your-current-environment"></a>Enregistrer votre environnement actuel
Il est par ailleurs courant de changer de conception pendant les phases de test et d’implémentation. Utilisez votre plan de conception pour documenter ces changements et les raisons qui les motivent.

Votre environnement actuel peut influencer les décisions en matière de conception et doit être documenté et référencé quand vous prenez d’autres décisions de conception Intune. Voici quelques exemples d’enregistrement de l’environnement actuel :

-   **Identifier dans le cloud**

    -   Utilisez-vous DirSync ou Azure Active Directory (Azure AD) Connect ?

    -   Votre environnement est-il fédéré ?

    -   Est-ce que l’authentification multifacteur est activée ?

-   **Environnement de courrier électronique**

    -   Vous utilisez Exchange ? Localement ou dans le cloud ?

    -   Êtes-vous au milieu d’un projet de migration Exchange vers le cloud ?

-   **Solution actuelle de gestion des appareils mobiles (MDM)**

    -   Utilisez-vous d'autres solutions de gestion des appareils mobiles ?

    -   Quelles solutions de gestion des appareils mobiles utilisez-vous pour l’entreprise et les scénarios d’utilisation BYOD ?

    -   Quelles fonctionnalités utilisez-vous (par exemple : paramètres d’appareils d’applications, configurations Wi-Fi) ?

    -   Quelles sont les plateformes d'appareils prises en charge ?

    -   Quels groupes et combien d’utilisateurs exploitent la solution de gestion des appareils mobiles ?

-   **Solution de certificat**

    -   Avez-vous implémenté une solution de certificat ?

    -   Quel type de certificats utilisez-vous ?

-   **Gestion des systèmes**

    -   Comment gérez-vous votre environnement PC et serveur ?

    -   Utilisez-vous System Center Configuration Manager ? Utilisez-vous une plate-forme de gestion système tierce ?

-   **Solution VPN**

    -   Quelle est votre solution VPN ?

    -   Est-ce que vous l’utilisez pour des scénarios d’utilisation en entreprise et BYOD ?

Veillez à noter tous les projets ou tous les autres plans mis en place susceptibles d’affecter votre environnement durant l’enregistrement de l’environnement de gestion des appareils mobiles actuel. Voici un exemple de méthode d’enregistrement de l’environnement actuel durant la création de votre conception Intune :

| **Zone de la solution** | **Environnement actuel** | **Commentaires** |
|---|---|---|
| **Identité** | Azure AD, Azure AD Connect, non fédéré, sans authentification multifacteur | Projet en place pour activer l’authentification multifacteur avant la fin de l’année |                 
| **Environnement de courrier électronique** | Exchange sur site, Exchange en ligne | En cours de migration d'Exchange sur site vers Exchange en ligne. 75 % de boîtes aux lettres migrés. Les 25 % restants seront migrés avant le début du projet pilote Intune. |                
| **SharePoint** | SharePoint sur site | Aucun plan pour migrer vers SharePoint en ligne |  
| **Gestion des appareils mobiles actuelle** | Exchange ActiveSync |  |
| **Solution de certificat** | Microsoft Server 2012 R2, services de certificats AD | Utiliser uniquement une PKI pour les serveurs de sites Web |
| **System Management** | System Center Configuration Manager CB 1606 | Souhaiterait étudier une solution Intune hybride |
| **Solution VPN** | Cisco AnyConnect |  |


Vous pouvez [télécharger un modèle du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour développer un plan de conception Intune.

## <a name="choose-an-intune-deployment-option"></a>Choisissez une option de déploiement Intune

Intune propose deux options de déploiement : autonome et hybride. Autonome fait référence au service Intune en cours d’exécution dans le cloud, hybride fait référence à l’intégration d’Intune avec System Center Configuration Manager. Ce guide couvre principalement l’option autonome. [Choisissez l’option qui répond aux besoins de votre entreprise](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

## <a name="intune-tenant-location"></a>Emplacement du client Intune

Si votre organisation est présente dans plusieurs pays, tenez compte de l’emplacement de votre locataire quand vous vous abonnez au service. Le pays est défini lorsque vous souscrivez un abonnement Intune pour la première fois. Voici les régions du monde concernées :

-   Amérique du Nord

-   Europe, Moyen-Orient et Afrique

-   Asie et Pacifique

>[!IMPORTANT]
> Il n’est pas possible de modifier l’emplacement du pays et du client ultérieurement.

## <a name="external-dependencies"></a>Dépendances externes

Les dépendances externes sont des services et des produits distincts d'Intune, mais elles constituent une condition requise pour Intune ou peuvent s'intégrer à Intune. Il est important d’identifier les exigences de toutes les dépendances externes et la façon dont elles sont configurées. Voici quelques exemples de dépendances externes courantes :

-   Fournisseur

-   Groupes d’utilisateurs et d’appareils

-   Infrastructure à clé publique (PKI)

Examinons plus en détail les dépendances externes courantes ci-dessous

### <a name="identity"></a>Fournisseur

L’identité est la façon dont nous identifions les utilisateurs qui appartiennent à votre organisation et inscrivent un appareil. Intune nécessite Azure Active Directory (Azure AD) comme fournisseur d’identité d'utilisateur. Si vous employez déjà ce service, vous pouvez utiliser votre identité déjà présente dans le cloud. En outre, Azure AD Connect est l’outil recommandé pour synchroniser les identités de vos utilisateurs locaux avec les services de cloud Microsoft. Si votre organisation utilise déjà Office 365, il est important qu’Intune utilise le même environnement Azure AD.

En savoir plus sur les exigences d’Intune suivantes en matière d’identité :

- [Exigences en matière d’identité](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions).

- [Exigences en matière de synchronisation d’annuaires](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

- [Exigences en matière d’authentification multifacteur](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

### <a name="user-and-device-groups"></a>Groupes d’utilisateurs et d’appareils

Les groupes d’utilisateurs et d’appareils déterminent la cible d’un déploiement, notamment les stratégies, les applications et les profils. Vous devez déterminer les groupes d’utilisateurs et d’appareils nécessaires.

Nous vous recommandons de créer tous les groupes dans l’annuaire Active Directory local, puis de le synchroniser à Azure AD. Découvrez plus en détail la planification et la création de groupes d’utilisateurs et d’appareils :

-   [Planifier vos groupes d’utilisateurs et d’appareils](users-add.md).

-   [Créer des groupes d’utilisateurs et d’appareils](groups-add.md).

### <a name="public-key-infrastructure-pki"></a>Infrastructure à clé publique (PKI)
L’infrastructure à clé publique fournit des certificats aux appareils ou utilisateurs pour qu’ils puissent s’authentifier en toute sécurité auprès d’un service. Intune prend en charge une infrastructure PKI Microsoft. Les certificats d’utilisateur et d’appareil peuvent être transmis à un appareil mobile pour répondre aux exigences de l’authentification basée sur un certificat. Avant d’utiliser des certificats, vous devez déterminer si vous en avez besoin, si l’infrastructure du réseau peut prendre en charge l’authentification basée sur un certificat, et si des certificats sont actuellement utilisés dans l’environnement existant.

Si vous comptez utiliser des certificats avec des profils VPN, Wi-Fi ou de messagerie avec Intune, veillez à [mettre en place une infrastructure PKI](certificates-configure.md) prise en charge, prête à créer et à déployer des profils de certificat.

En outre, si des certificats SCEP seront émis, vous devez choisir le serveur qui hébergera la fonctionnalité Service d’inscription de périphériques réseau (NDES), et comment la communication s’effectuera.

Informations supplémentaires :

-   [Guide pratique pour configurer des profils de certificats Intune](certificates-configure.md)

-   [Comment configurer l’infrastructure de certificats pour SCEP](certificates-scep-configure.md)

-   [Guide pratique pour configurer l’infrastructure de certificat pour PFX](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Considérations relatives aux plateformes d'appareils

Examinez de plus près les aspects suivants de vos appareils pour comprendre comment les gérer correctement.

-   Plateformes d’appareil prises en charge

-   Appareils

-   Propriété des appareils

-   Inscription en bloc

Examinons ces domaines plus en détail.

### <a name="determine-supported-device-platforms"></a>Déterminer les plateformes d'appareils prises en charge

Vous devez identifier les appareils qui seront utilisés dans l’environnement et vérifier s'ils sont pris en charge ou non par Intune lors de la création de votre conception. Intune prend en charge les plateformes iOS, Android et Windows.

[Liste complète des appareils pris en charge par Intune](supported-devices-browsers.md).

### <a name="devices"></a>Appareils

Intune gère les appareils mobiles pour sécuriser les données d’entreprise et permettre aux utilisateurs de travailler depuis plusieurs endroits. Comme Intune prend en charge de nombreuses plateformes d’appareils, nous vous recommandons de documenter les appareils ainsi que les plateformes et versions de système d’exploitation pris en charge dans la conception de votre organisation. Par exemple :

| **Plate-forme d'appareil** | **Versions du système d'exploitation** |
|:---:|:---:|
| iOS - iPhone | 10.0+ |                
| iOS - iPad | 10.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Tablette Windows 10 | 10+ |


Vous pouvez [télécharger un modèle du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour développer votre liste d’appareils.
### <a name="device-ownership"></a>Propriété des appareils

Intune prend en charge les appareils d’entreprise et les appareils personnels. Un appareil est considéré comme appartenant à l’entreprise s’il est inscrit par un gestionnaire d’inscription des appareils ou par un programme d’inscription des appareils. Par exemple, un appareil peut être inscrit auprès du Programme d’inscription des appareils Apple (DEP), marqué comme appartenant à l’entreprise et placé dans un groupe d’appareils auquel s’appliquent des stratégies d’entreprise et des applications ciblées.

Pour plus d’informations sur les scénarios d’utilisation d’entreprise et BYOD, consultez la [Section 3 : déterminer les exigences du scénario d’utilisation](planning-guide-requirements.md).

### <a name="bulk-enrollment"></a>Inscription en bloc

 Vous pouvez inscrire des appareils en bloc de différentes manières selon la plateforme. Si vous exigez l’inscription en bloc, [déterminez d’abord la méthode d’inscription en bloc](device-enrollment.md) et incorporez-la dans votre conception.

## <a name="feature-requirements"></a>Exigences concernant les fonctionnalités

Dans les sections suivantes, nous examinons les fonctionnalités et capacités qui répondent aux besoins de votre scénario d’utilisation :

-   Stratégies de conditions générales

-   Stratégies de configuration

-   Profils de ressources

-   Applications

-   Stratégie de conformité

-   Accès conditionnel

Examinons chacun de ces domaines plus en détail.

### <a name="terms-and-conditions-policies"></a>Stratégies de conditions générales

Vous pouvez utiliser des [conditions générales](terms-and-conditions-create.md) pour expliquer les stratégies ou les conditions qu’un utilisateur final doit accepter avant d’inscrire son appareil. Intune permet d’ajouter et de déployer plusieurs stratégies de conditions générales pour des groupes d’utilisateurs.

Vous devez déterminer si des conditions générales sont nécessaires. Dans ce cas, vous devez désigner une personne chargée de fournir ces informations au sein de l’organisation. Voici un exemple montrant comment documenter la stratégie de conditions générales.

| **Nom des conditions générales** | **Scénario d'utilisation** | **Groupe ciblé** |
|:---:|:---:|:---:|
| Conditions générales d'entreprise | Entreprise | Utilisateurs d’entreprise |                 
| Conditions générales BYOD | BYOD | Utilisateurs BYOD |                


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour mapper vos conditions générales à vos groupes d’utilisateurs.

### <a name="configuration-policies"></a>Stratégies de configuration

Utilisez des stratégies de configuration utilisées pour gérer les paramètres de sécurité et les fonctionnalités sur un appareil. Lorsque vous concevez vos stratégies de configuration, consultez la section Exigences du scénario d’utilisation pour déterminer les exigences des appareils Intune. Documentez les paramètres et la façon dont ils doivent être configurés. Documentez également les groupes d’utilisateurs ou d’appareils ciblés.

Vous devez créer au moins une stratégie de configuration par plateforme. Vous pouvez créer plusieurs stratégies de configuration par plateforme si nécessaire. Voici un exemple de conception de quatre stratégies de configuration pour différentes plateformes et scénarios d’utilisation.

| **Nom de la stratégie** | **Plate-forme d'appareil** | **Paramètres** | **Groupe cible** |   
|:---:|:---:|:---:|:---:|
| Entreprise - iOS | iOS | Code PIN nécessaire, longueur : 6, restreindre la sauvegarde sur le cloud | Appareils d'entreprise |                                                           
| Entreprise - Android | Android | Code PIN nécessaire, longueur : 6, restreindre la sauvegarde sur le cloud | Appareils d'entreprise |                                                           
| BYOD – iOS  | iOS | Code PIN nécessaire, longueur : 4 | Appareils BYOD |
| BYOD – Android  | Android | Code PIN nécessaire, longueur : 4 | Appareils BYOD |


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de stratégie de configuration.

### <a name="profiles"></a>Profils

Utilisez des profils pour aider l’utilisateur final à se connecter aux données d’entreprise. Intune prend en charge plusieurs types de profils. Consultez les scénarios d’utilisation et les exigences pour déterminer quand les profils seront configurés. Tous les profils d’appareils sont classés par type de plateforme et doivent être inclus dans la documentation de conception.

-   Profils de certificat

-   Profil Wi-Fi

-   Profil VPN

-   Profil de messagerie

Examinons chaque type de profil plus en détail.

#### <a name="certificate-profiles"></a>Profils de certificat

Les profils de certificat permettent à Intune de transmettre un certificat à un utilisateur ou à un appareil. Intune prend en charge les profils suivants :

-   Protocole SCEP (Simple Certificate Enrollment Protocol)

-   Certificat racine approuvé

-   Certificat PFX.

Nous vous recommandons de documenter quel groupe d’utilisateurs a besoin d’un certificat, le nombre de profils de certificat dont vous avez besoin et les groupes d’utilisateurs sur lesquels ils sont déployés.

>[!NOTE]
> N’oubliez pas que le certificat racine approuvé est requis pour le certificat SCEP. Assurez-vous par conséquent que tous les utilisateurs ciblés pour le certificat SCEP reçoivent également un certificat racine approuvé. Si vous avez besoin de certificats SCEP, concevez et documentez les modèles de certificat SCEP nécessaires.

Voici un exemple montrant comment documenter les certificats lors de la conception :

| **Type** | **Nom du profil** | **Plate-forme d'appareil** | **Scénarios d'utilisation** |   
|:---:|:---:|:---:|:---:|
| Autorité de certification racine | Autorité de certification racine d’entreprise | Android, iOS, Windows mobile | Entreprise, BYOD  |                                                           
| SCEP | Certificat d'utilisateur | Android, iOS, Windows mobile | Entreprise, BYOD |                                                           


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de profil de certificat.

#### <a name="wi-fi-profile"></a>Profil Wi-Fi

Les profils Wi-Fi permettent de connecter automatiquement un appareil mobile à un réseau sans fil. Intune prend en charge le déploiement de profils Wi-Fi sur toutes les plateformes prises en charge. En savoir plus sur [comment Intune prend en charge les profils Wi-Fi.](wi-fi-settings-configure.md)

Voici un exemple de conception pour un profil Wi-Fi :

| **Type** | **Nom du profil** | **Plate-forme d'appareil** | **Scénarios d'utilisation** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Profil Wi-Fi Asie | Android | Entreprise, BYOD - région Asie|                                                           
| Wi-Fi | Profil Wi-Fi Amérique du Nord | Android, iOS, Windows 10 Mobile | Entreprise, BYOD - région Amérique du Nord |                                                           


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de profil Wi-Fi.

#### <a name="vpn-profile"></a>Profil VPN

Les profils VPN permettent aux utilisateurs d’accéder en toute sécurité à votre réseau à partir d’emplacements distants. Intune prend en charge les profils VPN provenant de connexions VPN mobiles natives et de fournisseurs tiers. En savoir plus sur les [profils VPN et les fournisseurs pris en charge par Intune](vpn-settings-configure.md).

Voici un exemple de documentation de la conception d’un profil VPN.

| **Type** | **Nom du profil** | **Plate-forme d'appareil** | **Scénarios d'utilisation** |   
|:---:|:---:|:---:|:---:|
| VPN | Profil VPN Cisco AnyConnect | Android, iOS, Windows 10 Mobile | Entreprise, BYOD - Amérique du Nord et Allemagne|                                                           
| VPN | Pulse Secure | Android | Entreprise, BYOD - région Asie |                                                           


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de profil VPN.
#### <a name="email-profile"></a>Profil de messagerie

Les profils de messagerie permettent de configurer automatiquement un client de messagerie à l’aide des informations de connexion et la configuration de la messagerie. Intune prend en charge les profils de messagerie sur certains appareils. Découvrez plus en détail [les profils de messagerie et les plateformes prises en charge](email-settings-configure.md).

Voici un exemple de documentation de la conception de profils de messagerie :

| **Type** | **Nom du profil** | **Plate-forme d'appareil** | **Scénarios d'utilisation** |   
|:---:|:---:|:---:|:---:|
| Profil de messagerie | Profil de messagerie iOS | iOS | Entreprise – BYOD travailleur de l'information |                                                           
| Profil de messagerie | Profil de messagerie Android Knox | Android Knox | BYOD |


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de profil de messagerie.
### <a name="apps"></a>Applications

Vous pouvez utiliser Intune pour fournir des applications à des utilisateurs ou à des appareils de plusieurs façons. Parmi les types d’applications pris en charge, citons les applications logicielles d’installation, les applications d’un App Store public, les liens externes ou les applications iOS gérées. En plus des déploiements d’applications individuels, vous pouvez gérer et déployer des applications achetées en volume dans le cadre des programmes d’achat en volume pour iOS et Windows. Informations supplémentaires :

-   [Types d’applications que vous pouvez fournir](app-management.md)

-   [Programme d’achat en volume (VPP) iOS pour les entreprises](vpp-apps-ios.md)

-   [Applications Microsoft Store pour Entreprises](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Exigences de type d’application

Comme les applications peuvent être déployées sur des utilisateurs et des appareils, nous vous est recommandons de déterminer les applications qui seront gérées par Intune. Lorsque vous en dressez la liste, essayez de répondre aux questions suivantes :

-   Les applications nécessitent-elle une intégration à des services cloud ?

-   Les applications sont-elles toutes accessibles aux utilisateurs BYOD ?

-   Quelles sont les options de déploiement disponibles pour ces applications ?

-   Votre entreprise doit-elle fournir un accès à des données d’applications SaaS (Software as a service) à ses partenaires ?

-   Les applications nécessitent-elle un accès à Internet à partir des appareils de l'utilisateur ?

-   Les applications sont-elles disponibles publiquement dans un App Store, ou s’agit-il d’applications métier personnalisées ?


#### <a name="app-protection-policies"></a>Stratégies de protection des applications

Les stratégies de protection des applications limitent les perte de données en définissant la manière dont l’application gère les données d’entreprise. Intune prend en charge les stratégies de protection des applications pour toute application créée pour fonctionner avec la gestion des applications mobiles. Quand vous concevez la stratégie de protection des applications, vous devez déterminer les restrictions à appliquer aux données d’entreprise dans une application donnée. Nous vous recommandons d’examiner la façon dont les [stratégies de protection des applications](app-protection-policy.md) fonctionnent. Voici un exemple montrant comment documenter les applications existantes et quelle protection est nécessaire.

| **Application** | **Fonction** | **Plateformes** | **Scénario d'utilisation** | **Stratégie de protection d'application** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Disponible | iOS | Entreprise - Cadres | Ne peut pas être jailbreaké, chiffrement des fichiers |                                                         
| Word | Disponible | iOS, Android - Samsung Knox, non-Knox, Windows 10 Mobile | Entreprise, BYOD | Ne peut pas être jailbreaké, chiffrement des fichiers |                                                         


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de stratégie de protection des applications.
#### <a name="compliance-policies"></a>Stratégies de conformité

Les stratégies de conformité déterminent si un appareil est conforme à certaines exigences. Intune utilise des stratégies de conformité pour déterminer si un appareil est considéré comme conforme ou non conforme. L’état de conformité peut ensuite servir à restreindre ou à autoriser l’accès aux ressources d’entreprise. Si un accès conditionnel est requis, nous vous recommandons de concevoir une [stratégie de conformité d’appareil](device-compliance.md).

Reportez-vous aux exigences et aux cas d’utilisation pour déterminer le nombre de stratégies de conformité d’appareils nécessaires et les groupes d’utilisateurs ciblés. Par ailleurs, vous devez déterminer la durée pendant laquelle un appareil peut rester déconnecté sans s’identifier avant d’être considéré comme non conforme.

Voici un exemple de conception d’une stratégie de conformité :

| **Nom de la stratégie** | **Plate-forme d'appareil** | **Paramètres** | **Groupe cible** |   
|:---:|:---:|:---:|:---:|
| Stratégie de conformité | iOS, Android - Samsung Knox, non-Knox, Windows 10 Mobile | Code PIN - requis, ne peut pas être jailbreaké | Entreprise, BYOD |


Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de stratégie de conformité.
#### <a name="conditional-access-policies"></a>Stratégies d'accès conditionnel

L’accès conditionnel est utilisé pour autoriser uniquement les appareils compatibles à accéder aux e-mails et aux autres ressources de l’entreprise. Intune fonctionne avec Enterprise Mobility + Security (EMS) pour contrôler l’accès aux ressources de l’entreprise. Vous devez déterminer si l’accès conditionnel est requis, et ce qui doit être sécurisé. En savoir plus sur l'[accès conditionnel](conditional-access.md).

Pour l’accès en ligne, déterminez les plateformes et les groupes d’utilisateurs ciblés par les stratégies d’accès conditionnel. Vous devez également déterminer si vous devez installer/configurer le connecteur service à service Intune pour Exchange Online ou Exchange sur site. Découvrez comment installer et configurer les connecteurs service à service Intune : <!---these links are correct--->

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange local](exchange-connector-install.md)

Voici un exemple montrant comment documenter des stratégies d’accès conditionnel :

| **Service** | **Plateformes pour l'authentification moderne** | **Authentification de base** | **Scénarios d'utilisation** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS, Android | Bloquer les appareils non conformes sur les plateformes prises en charge par Intune | Entreprise, BYOD |
| SharePoint Online | iOS, Android |  | Entreprise, BYOD |

Vous pouvez [télécharger un modèle à partir du tableau ci-dessus](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) pour identifier vos besoins en matière de stratégie d’accès conditionnel.

## <a name="next-steps"></a>Étapes suivantes

La section suivante fournit des conseils sur le [processus d’implémentation Intune](planning-guide-onboarding.md).
