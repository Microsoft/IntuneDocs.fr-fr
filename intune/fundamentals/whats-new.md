---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f32637173ec6cf5f7c284a87193eafffb6a16e6c
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72786128"
---
# <a name="whats-new-in-microsoft-intune"></a>Nouveautés de Microsoft Intune

Découvrez les nouveautés hebdomadaires dans Microsoft Intune. Vous pouvez également trouver des [annonces importantes](#notices), des [publications précédentes](whats-new-archive.md) et des informations sur [le mode de publication des mises à jour par le service Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> Chaque [mise à jour mensuelle](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) peut mettre jusqu'à trois jours pour être déployée et le sera dans l’ordre suivant :
>
> - Jour 1 : Asie-Pacifique (APAC)
> - Jour 2 : Europe, Moyen-Orient et Afrique (EMEA)
> - Jour 3 : Amérique du Nord
>
> Le lancement de certaines fonctionnalités peut s’étaler sur plusieurs semaines. Ces fonctionnalités risquent de ne pas être accessibles à tous les clients la première semaine.
>
> Consultez la [page En développement](in-development.md) pour obtenir une liste des fonctionnalités à venir dans une version.

**Flux RSS** : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  


<!-- ########################## -->

## <a name="week-of-october-21-2019"></a>Semaine du 21 octobre 2019

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073-idready-wnready---"></a>Nouveau profil d’interface de configuration de microprogramme d’appareil pour les appareils Windows 10 et versions ultérieures <!-- 2266073 idready wnready -->

Sur Windows 10 et versions ultérieures, vous pouvez créer un profil de configuration d’appareil pour contrôler les paramètres et les fonctionnalités (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour la plateforme). Dans cette mise à jour, il existe un nouveau type de profil d’interface de configuration de microprogramme d’appareil qui permet à Intune de gérer les paramètres UEFI (BIOS).

Pour plus d’informations sur cette fonctionnalité, consultez [Utiliser des profils DFCI sur des appareils Windows dans Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

S’applique à :

- Windows 10 RS5 (1809) et versions plus récentes sur le microprogramme pris en charge

## <a name="week-of-october-14-2019"></a>Semaine du 14 octobre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion d'applications 

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956-----"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android <!-- 3041956   -->
Pour les installations d’applications disponibles sur les appareils dédiés et entièrement gérés avec un profil professionnel Android Entreprise, vous pouvez afficher l’état d’installation des applications ainsi que la version installée des applications Google Play gérées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](~/apps/app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](~/enrollment/android-enterprise-overview.md) et [Type d’application Google Play gérée](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview----3872025-4678761----"></a>Microsoft Edge version 77 et ultérieures pour Windows 10 et macOS (préversion publique) <!-- 3872025, 4678761  -->
Microsoft Edge version 77 et ultérieures peuvent désormais être déployés sur des PC exécutant Windows 10 et macOS. La préversion publique offre les canaux **Dev** et **Bêta** pour Windows 10 et un canal **Bêta** pour macOS. Le déploiement s’effectue en anglais (EN) uniquement, mais les utilisateurs finaux peuvent changer la langue d’affichage dans le navigateur sous **Paramètres** > **Langues**. Microsoft Edge est une application Win32 installée dans le contexte du système et sur des architectures similaires (application x86 sur un système d’exploitation x86 et application x64 sur un système d’exploitation x64). Par ailleurs, les mises à jour automatiques du navigateur sont définies sur **Activé** par défaut, et Microsoft Edge ne peut pas être désinstallé. Pour plus d’informations, consultez [Ajouter Microsoft Edge pour Windows 10 à Microsoft Intune](~/apps/apps-windows-edge.md) et [Documentation Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029-----"></a>Mise à jour de l’interface utilisateur de la protection des applications et de l’interface utilisateur de provisionnement d’applications iOS <!-- 4102027, 4102029   -->
L’interface utilisateur permettant de créer et modifier les stratégies de protection des applications et les profils de provisionnement d’applications iOS dans Intune a été mise à jour. Les modifications de l’interface utilisateur incluent :
- Une expérience simplifiée qui s’apparente à un Assistant condensé dans un seul panneau. 
- Une mise à jour du flux de création pour inclure les affectations.
- Une page récapitulative de tous les éléments définis pendant l’affichage des propriétés, préalablement à la création d’une stratégie ou pendant la modification d’une propriété. Par ailleurs, pendant la modification de propriétés, le récapitulatif présente uniquement la liste des éléments de la catégorie des propriétés modifiées.

Pour plus d’informations, consultez [Guide pratique pour créer et affecter des stratégies de protection des applications](~/apps/app-protection-policies.md) et [Utiliser des profils de provisionnement d’applications iOS](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios----4850318-4831296-3610611----"></a>Scénarios guidés Intune <!-- 4850318, 4831296, 3610611  -->
Intune propose désormais des scénarios guidés pour vous aider à effectuer une tâche ou plusieurs tâches dans Intune. Un scénario guidé est une série d’étapes personnalisée (workflow) centrée sur un cas d’usage de bout en bout. Les scénarios courants sont définis en fonction du rôle joué par un administrateur, un utilisateur ou un appareil dans votre organisation. Ces workflows nécessitent généralement un ensemble de profils, de paramètres, d’applications et de contrôles de sécurité soigneusement orchestrés pour offrir une expérience utilisateur et une sécurité optimales. Les nouveaux scénarios guidés sont les suivants :
- [Déployer Microsoft Edge pour mobile](~/fundamentals/guided-scenarios-edge.md)
- [Applications mobiles Microsoft Office sécurisées](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Bureau moderne géré par le cloud](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Pour plus d’informations, consultez [Vue d’ensemble des scénarios guidés Intune](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available----4969237-----"></a>Variable de configuration des applications supplémentaire disponible <!-- 4969237   -->
Au moment de créer une stratégie de configuration des applications, vous pouvez inclure la variable de configuration `AAD Device ID` parmi vos paramètres de configuration. Dans Intune, sélectionnez **Applications clientes** > **Stratégies de configuration des applications** > **Ajouter**. Entrez les détails de votre stratégie de configuration, puis sélectionnez **Paramètres de configuration** pour afficher le panneau **Paramètres de configuration**. Pour plus d’informations, consultez [Stratégies de configuration des applications pour les appareils Android Enterprise gérés – Utiliser le concepteur de configuration](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Créer des groupes d’objets de gestion appelés ensembles de stratégies <!-- 3762880  -->
Les ensembles de stratégies vous permettent de créer un ensemble de références à des entités de gestion existantes qui doivent être identifiées, ciblées et supervisées comme une seule unité conceptuelle. Les ensembles de stratégies ne remplacent pas les concepts ou objets existants. Vous pouvez continuer d’affecter des objets individuels dans Intune et les référencer dans un ensemble de stratégies. Par conséquent, toute modification apportée à ces objets individuels est répercutée dans l’ensemble de stratégies.  Dans Intune, sélectionnez **Ensembles de stratégies** > **Créer** pour créer un ensemble de stratégies. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration des appareils

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089-----------"></a>Mise à jour de l’interface utilisateur pour créer et modifier des anneaux de mise à jour Windows 10  <!-- 4099089         -->
Nous avons mis à jour l’expérience de l’interface utilisateur pour [créer et modifier des anneaux de mise à jour Windows 10](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) pour Intune. Voici les changements apportés à l’interface utilisateur :  
- Un format de type Assistant condensé dans un même panneau de console, qui met fin à la prolifération des panneaux à laquelle vous étiez auparavant exposé au moment de configurer des anneaux de mise à jour.   
- Le workflow révisé inclut les affectations avant la finalisation de la configuration initiale de l’anneau.
- Une page récapitulative dans laquelle vous pouvez examiner toutes les configurations que vous avez effectuées, avant d’enregistrer et déployer un nouvel anneau de mise à jour. Pendant la modification d’un anneau de mise à jour, le récapitulatif présente uniquement la liste des éléments définis dans une catégorie de propriétés que vous avez modifiées.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy-----4099090---------"></a>Mise à jour de l’interface utilisateur pour créer et modifier une stratégie de mise à jour logicielle iOS  <!-- 4099090       --> 
Nous avons mis à jour l’expérience de l’interface utilisateur pour [créer](../protect/software-updates-ios.md#configure-the-policy) et [modifier](../protect/software-updates-ios.md#edit-a-policy) des stratégies de mise à jour logicielle iOS pour Intune.  Voici les changements apportés à l’interface utilisateur :  
- Un format de type Assistant condensé dans un même panneau de console, qui met fin à la prolifération des panneaux à laquelle vous étiez auparavant exposé pendant la configuration des stratégies de mise à jour.   
- Le workflow révisé inclut les affectations avant la finalisation de la configuration initiale de la stratégie.
- Une page récapitulative dans laquelle vous pouvez examiner toutes les configurations que vous avez effectuées, avant d’enregistrer et déployer une nouvelle stratégie. Pendant la modification d’une stratégie, le récapitulatif présente uniquement la liste des éléments définis dans une catégorie de propriétés que vous avez modifiées.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings------4464404---wnready-----"></a>Les paramètres de redémarrage commencé sont supprimés des anneaux Windows Update  <!--  4464404   WNReady   -->
Comme annoncé précédemment, les anneaux de mise à jour Windows 10 d’Intune [prennent désormais en charge les paramètres d’échéance](../protect/windows-update-settings.md) et ne prennent plus en charge le *redémarrage commencé*. Les paramètres de *redémarrage engagé* ne sont plus accessibles pendant la configuration ou la gestion d’anneaux de mise à jour dans Intune.  

Ce changement est en adéquation avec les récentes [modifications apportées à la maintenance de Windows](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) et sur les appareils qui exécutent Windows 10 1903 ou une version ultérieure, les *échéances* remplacent les configurations du *redémarrage commencé*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices----4760025-----"></a>Empêcher les installations d’applications à partir de sources inconnues sur les appareils avec profil professionnel Android Entreprise <!-- 4760025   -->
Sur les appareils avec profil professionnel Android Entreprise, les utilisateurs ne peuvent pas installer d’applications à partir de sources inconnues. Dans cette mise à jour, il existe un nouveau paramètre : **Empêcher les installations d’applications à partir de sources inconnues dans le profil personnel**. Par défaut, ce paramètre empêche les utilisateurs d’effectuer un chargement indépendant d’applications de sources inconnues vers le profil personnel de l’appareil.

Pour voir les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Profil professionnel Android Entreprise

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339-----"></a>Créer un proxy HTTP global sur les appareils de propriétaires d’appareils Android Entreprise <!-- 4816339   -->
Sur les appareils Android Entreprise, vous pouvez configurer un proxy HTTP global pour respecter les standards de navigation web de votre organisation (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil > Restrictions de l’appareil** pour le type de profil > **Connectivité**). Une fois la configuration terminée, l’ensemble du trafic HTTP utilise ce proxy.

Pour configurer cette fonctionnalité et voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Propriétaire d’appareil Android Entreprise

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise----5021055-----"></a>Le paramètre Se connecter automatiquement est supprimé dans les profils Wi-Fi de l’administrateur d’appareil Android et Android Entreprise <!-- 5021055   -->
Sur les appareils de l’administrateur d’appareil Android et Android Enterprise, vous pouvez créer un profil Wi-Fi pour configurer différents paramètres (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Administrateur d’appareil Android** ou **Android Entreprise** pour la plateforme > **Wi-Fi** pour le type de profil). Dans cette mise à jour, le paramètre **Se connecter automatiquement** est supprimé, car il n’est [pas pris en charge par Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Si vous utilisez ce paramètre dans un profil Wi-Fi, vous avez peut-être remarqué que **Se connecter automatiquement** ne fonctionne pas. Vous n’avez aucune action à effectuer, mais sachez que ce paramètre a été retiré de l’interface utilisateur Intune.

Pour voir les paramètres actuels, accédez à [Paramètres Wi-Fi Android](../configuration/wi-fi-settings-android.md) ou [Paramètres Wi-Fi Android Entreprise](../configuration/wi-fi-settings-android-enterprise.md).

S’applique à :
- Administrateur d’appareil Android 
- Android Entreprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328-----"></a>Nouveaux paramètres de configuration d’appareil pour les appareils iOS et iPadOS supervisés <!-- 5199328   -->
Sur les appareils iOS et iPadOS, vous pouvez créer un profil pour restreindre les fonctionnalités et les paramètres sur les appareils (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS/iPadOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Dans cette mise à jour, vous pouvez contrôler les nouveaux paramètres suivants : 
- Accès à un lecteur réseau dans l’application Fichiers  
- Accès à un lecteur USB dans l’application Fichiers 
- Wi-Fi toujours activé 

Pour voir les paramètres, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

S’applique à :
- iOS 13.0 et ultérieur
- iPadOS 13.0 et ultérieur

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697-----"></a>Spécifier les versions du système d’exploitation d’appareil Android qui s’inscrivent avec le profil professionnel ou l’inscription d’administrateur d’appareil <!-- 4350697   -->
À partir des exigences du type d’appareil Intune, vous pouvez utiliser la version du système d’exploitation de l’appareil pour spécifier les appareils utilisateur qui utiliseront l’inscription de profil professionnel Android Entreprise ou l’inscription d’administrateur d’appareil Android.  Pour en savoir plus, consultez la section relative à la [définition de restrictions d’inscription](../enrollment/enrollment-restrictions-set.md).

#### <a name="windows-autopilot-deployment-reports----3856172---"></a>Programme de déploiement Windows AutoPilot <!-- 3856172 -->
Un nouveau rapport détaille chaque appareil déployé via Windows Autopilot. Pour plus d’informations, consultez [Rapport de déploiement Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report). Nous déployons actuellement cette fonctionnalité pour tous les clients et prévoyons son achèvement d’ici la fin de la semaine prochaine.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des appareils

#### <a name="new-restrictions-for-renaming-windows-devices----3478938----"></a>Nouvelles restrictions pour le changement de nom des appareils Windows <!-- 3478938  -->
Au moment de renommer un appareil Windows, vous devez suivre les nouvelles règles :
- 15 caractères ou moins (doit être inférieur ou égal à 63 octets, à l’exclusion de la valeur NULL de fin)
- Valeur non null ou chaîne vide
- Caractères ASCII autorisés : Lettres (a-z, A-Z), chiffres (0-9) et traits d’union
- Caractères Unicode autorisés : caractères >= 0x80, format UTF8 valide, mappage possible à un nom de domaine international (autrement dit, RtlIdnToNameprepUnicode convient ; voir le document RFC 3492)
- Les noms ne doivent pas contenir que des chiffres
- Aucun espace dans le nom
- Caractères non autorisés : { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Pour plus d’informations, consultez [Renommer un appareil dans Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page----4924364---"></a>Nouveau rapport Android dans la page de présentation des appareils <!-- 4924364 -->
Dans la page de présentation des appareils figure un nouveau rapport qui indique le nombre d’appareils Android inscrits dans chaque solution de gestion d’appareils. Ce graphique présente le nombre d’appareils inscrits d’administrateur d’appareils avec profil professionnel entièrement gérés et dédiés. Pour afficher le rapport, choisissez **Intune** > **Appareils** > **Vue d’ensemble**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils 

#### <a name="pkcs-certificates-for-macos-----1333650---------"></a>Certificats PKCS pour macOS  <!-- 1333650       -->
Vous pouvez désormais [utiliser des certificats PKCS avec macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Vous pouvez sélectionner le certificat PKCS comme type de profil pour macOS et déployer des certificats d’utilisateur et d’appareil qui présentent les [champs Objet personnalisé et Autre nom de l’objet](../protect/certficates-pfx-configure.md#subject-name-format-for-macos).  

Le certificat PKCS pour macOS prend aussi en charge le nouveau paramètre _Autoriser toutes les applications à accéder à la clé privée_. Ce paramètre vous permet d’autoriser toutes les applications associées à accéder à la clé privée du certificat.  Pour plus d’informations sur ce paramètre, consultez la documentation Apple à l’adresse https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----------1736036-1736037-1772050-2777333-----------"></a>Informations d’identification dérivées pour provisionner des appareils mobiles iOS avec des certificats      <!--  1736036, 1736037, 1772050, 2777333         -->  
Intune prend en charge l’utilisation d’[informations d’identification dérivées](../protect/derived-credentials.md) comme méthode d’authentification et pour la signature et le chiffrement S/MIME pour les appareils iOS. Les informations d’identification dérivées sont une implémentation du standard *NIST (National Institute of Standards and Technology) 800-157* pour le déploiement de certificats sur les appareils.  

Les informations d’identification dérivées reposent sur l’utilisation d’une carte de vérification d’identité personnelle (PIV) ou d’une carte d’accès commun (CAC), comme une carte à puce. Pour obtenir des informations d’identification dérivées pour leur appareil mobile, les utilisateurs doivent accéder à l’application Portail d’entreprise pour suivre un workflow d’inscription propre au fournisseur utilisé.  Tous les fournisseurs d’informations d’identification dérivées imposent l’utilisation d’une carte à puce sur un ordinateur pour s’authentifier auprès d’eux. Le fournisseur émet alors un certificat à destination de l’appareil qui est dérivé de la carte à puce de l’utilisateur.  

Intune prend en charge les fournisseurs d’informations d’identification dérivées suivants :   
- DISA Purebred
- Entrust Datacard
- Intercede

Vous pouvez utiliser les informations d’identification dérivées comme méthode d’authentification pour les profils de configuration d’appareil pour un VPN, le Wi-Fi et l’e-mail. Vous pouvez aussi les utiliser pour l’authentification des applications et pour le chiffrement et la signature S/MIME.  

Pour plus d’informations sur le standard, consultez [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) sur www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates--------5437939----------"></a>Utiliser l’API Graph pour spécifier un nom d’utilisateur principal local comme variable pour les certificats SCEP    <!--  5437939        -->  
Quand vous utilisez l’[API Graph Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0), vous pouvez spécifier onPremisesUserPrincipalName comme variable pour l’autre nom d’objet des certificats SCEP.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Semaine du 23 septembre 2019

#### <a name="ios-user-enrollment-in-preview----4817900---"></a>Inscription des utilisateurs iOS en préversion <!-- 4817900 -->
La version iOS 13.1 d'Apple inclut l’inscription utilisateur, une nouvelle forme de gestion simplifiée pour les appareils iOS. Elle peut être utilisée à la place de la méthode Inscription des appareils ou Inscription automatique des appareils (anciennement Programme d’inscription des appareils) pour les appareils personnels. La préversion d'Intune prend en charge cette fonctionnalité en vous permettant de :

- Inscription d'utilisateur cible à des groupes d'utilisateurs.
- Donner aux utilisateurs finaux la possibilité de choisir entre une inscription d'utilisateur plus simple ou une inscription d'appareil plus avancée lorsqu'ils inscrivent leurs appareils.

Depuis le 24/9/2019 et la version iOS 13.1, nous déployons ces mises à jour pour tous les clients et prévoyons leur achèvement d’ici la fin de la semaine prochaine.
S’applique à :

iOS 13.1 et versions ultérieures

#### <a name="intune-support-for-ipados-and-ios-131-devices---5439574--"></a>Prise en charge Intune pour les appareils iPadOS et iOS 13.1 <!--5439574-->
Intune prend désormais en charge à la fois les appareils iPadOS et iOS 13.1. Pour plus d’informations, consultez [ce billet de blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Semaine du 16 septembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion d'applications 

#### <a name="managed-google-play-private-lob-apps----1464182----"></a>Applications métier privées Google Play gérées <!-- 1464182  -->
Intune permet désormais aux administrateurs informatiques de publier des applications métier Android privées sur Google Play géré via un iframe incorporé dans la console Intune.  Auparavant, les administrateurs informatiques devaient publier les applications métier directement sur la console de publication de Google, ce qui nécessitait plusieurs étapes et prenait beaucoup de temps. Cette nouvelle fonctionnalité facilite la publication d’applications métier avec un ensemble d’étapes minimal, sans avoir à sortir de la console Intune.  Les administrateurs n’ont plus besoin de s’inscrire manuellement en tant que développeur avec Google, ni de payer les frais d’inscription à Google de 25 USD.  Les scénarios de gestion d’entreprise Android qui utilisent Google Play géré peuvent tirer parti de cette fonctionnalité (profil de travail, appareils dédiés, entièrement gérés et non inscrits). Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Google Play géré** sur la liste **Type d’application**. Pour en savoir plus sur les applications Google Play gérées, consultez [Ajouter des applications Google Play managé à des appareils d’entreprise Android avec Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience----1473353-3598357---"></a>Application Portail d’entreprise Windows <!-- 1473353, 3598357 -->
Le portail d’entreprise Windows est en cours de mise à jour. Vous pourrez utiliser plusieurs filtres sur la page Applications dans le Portail d’entreprise Windows. La page Détails de l’appareil est également en cours de mise à jour pour offrir une expérience utilisateur améliorée. Nous sommes en train de déployer ces mises à jour pour tous les clients et prévoyons leur achèvement d’ici la fin de la semaine suivante.

#### <a name="macos-support-for-web-apps----3174427---"></a>prise en charge macOS pour les applications web <!-- 3174427 -->
Les applications web, qui vous permettent d’ajouter un raccourci vers une URL sur le web, peuvent être installées sur le Dock à l’aide du Portail d’entreprise macOS. Les utilisateurs finaux peuvent accéder à l’action **Installer** à partir de la page des détails de l’application pour une application web dans le Portail d’entreprise macOS. Pour plus d’informations sur le type d’application **Lien web**, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md) et [Ajouter des applications web à Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps----3173501----"></a>Prise en charge macOS pour les applications VPP <!-- 3173501  -->
Les applications macOS, achetées à l’aide d’Apple Business Manager, s’affichent dans la console lors de la synchronisation des jetons Apple VPP dans Intune. Vous pouvez attribuer, révoquer et réassigner des licences d’appareil et d’utilisateur pour des groupes à l’aide de la console Intune. Microsoft Intune vous aide à gérer les applications VPP achetées pour une utilisation dans votre entreprise en :

- Signalant les informations de licence de l’App Store.
- Effectuant le suivi du nombre de licences utilisées.
- Vous empêchant d’installer davantage de copies de l’application que vous n’en possédez.

Pour plus d’informations sur Intune et VPP, consultez [Gérer les applications et les livres achetés en volume avec Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support----2871756----"></a>Prise en charge de l’iframe Google Play managés <!-- 2871756  -->
Intune propose désormais un support pour l’ajout et la gestion des liens web directement dans la console Intune via l’iframe Google Play géré.  Cela permet aux administrateurs informatiques d’envoyer une URL et une image d’icône, puis de déployer ces liens sur des appareils, comme des applications Android standard. Les scénarios de gestion d’entreprise Android qui utilisent Google Play géré peuvent tirer parti de cette fonctionnalité (profil de travail, appareils dédiés, entièrement gérés et non inscrits). Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Google Play géré** sur la liste **Type d’application**. Pour en savoir plus sur les applications Google Play gérées, consultez [Ajouter des applications Google Play managé à des appareils d’entreprise Android avec Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices----4252734----"></a>Installer des applications métier Android sur des appareils Zebra en mode silencieux <!-- 4252734  -->
Lors de l’installation d’applications métier Android sur des [appareils Zebra](../configuration/android-zebra-mx-overview.md), au lieu d’être invité à télécharger et à installer l’application métier, vous pourrez l’installer en mode silencieux. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans le volet **Ajouter une application**, sélectionnez **Application métier**. Pour plus d’informations, consultez [Ajouter une application métier Android à Microsoft Intune](../apps/lob-apps-android.md).

Actuellement, une fois l’application métier téléchargée, une notification **Téléchargement réussi** s’affiche sur l’appareil de l’utilisateur. La notification ne peut être ignorée qu’en appuyant sur **Tout effacer** dans la nuance de notification. Ce problème de notification sera résolu dans une prochaine version, et l’installation sera complètement silencieuse, sans aucun indicateur visuel.

#### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Lire et écrire des opérations d’API Graph pour les applications Intune <!-- 5031704  -->
Les applications peuvent appeler les opérations de lecture et d’écriture d’API Graph Intune avec leur identité d’application, sans informations d’identification d’utilisateur. Pour en savoir plus sur l’accès à l’API Microsoft Graph API pour Intune, consultez la section relative à [l’utilisation d’Intune dans Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios----3586942----"></a>Partage et chiffrement des données protégés pour le kit de développement logiciel (SDK) Intune App pour iOS <!-- 3586942  -->
Le kit de développement logiciel (SDK) Intune App pour iOS utilisera des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Toutes les applications auront besoin d’un kit de développement logiciel (SDK) versions 8.1.1 pour autoriser le partage de données protégées.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration des appareils

#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438-----"></a>Prise en charge des profils VPN IKEv2 pour iOS <!-- 1943438   -->
Dans cette mise à jour, vous pouvez créer des profils VPN pour le client VPN natif iOS en utilisant le protocole IKEv2. IKEv2 est un nouveau type de connexion dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **VPN** comme type de profil > **Type de connexion**.

Ces profils VPN configurent le client VPN natif, donc aucune application cliente VPN n’est installée ni envoyée à des appareils gérés. Cette fonctionnalité nécessite que les appareils soient inscrits auprès d’Intune (inscription MDM).

Pour afficher les paramètres VPN actuels que vous pouvez configurer, consultez [Configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md).

S’applique à :
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161-----"></a>Les fonctionnalités de l’appareil, les restrictions de l’appareil et les profils d’extension pour les paramètres iOS et macOS sont affichés par type d’inscription. <!-- 4886161   -->

Dans Intune, vous créez des profils pour les appareils iOS et macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** ou **macOS** pour plateforme > **Fonctionnalités de l’appareil**, **Restrictions de l’appareil**, ou **Extensions** pour le type de profil). 

Dans cette mise à jour, les paramètres disponibles dans le portail Intune sont catégorisés par le type d’inscription auquel ils s’appliquent :

- iOS
  - Inscription des utilisateurs
  - Inscription des appareils
  - Inscription automatique des appareils (supervisée)
  - Tous les types d’inscription

- macOS
  - Utilisateur approuvé
  - Inscription des appareils
  - Inscription automatique des appareils
  - Tous les types d’inscription

S’applique à :
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835-----"></a>Nouveaux paramètres de contrôle vocal pour les appareils iOS supervisés exécutés en mode plein écran <!-- 4892835   -->
Dans Intune, vous pouvez créer des stratégies pour exécuter des appareils iOS supervisés en mode plein écran, ou un appareil dédié (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour type de profil > **Plein écran**). 

Dans cette mise à jour, vous pouvez contrôler les nouveaux paramètres suivants :
- **Contrôle vocal** : active le contrôle vocal sur l’appareil en mode plein écran.
- **Modification du contrôle vocal** : autorisez les utilisateurs à modifier le paramètre de contrôle vocal sur l’appareil en mode plein écran.

Pour afficher les paramètres actuels, accédez à [Paramètres de plein écran d’iOS](../configuration/device-restrictions-ios.md#kiosk).

S’applique à :
- iOS 13.0 et versions ultérieures

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175-----"></a>Utiliser l’authentification unique pour les applications et sites web sur vos appareils iOS et macOS <!-- 4893175   -->
Dans cette mise à jour, il y a de nouveaux paramètres d’authentification unique pour les appareils iOS et macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** ou **macOS** pour plateforme > **Fonctionnalités de l’appareil** pour le type de profil).

Utilisez ces paramètres pour configurer une expérience d’authentification unique, en particulier pour les applications et les sites Web qui utilisent l’authentification Kerberos. Vous pouvez choisir entre une extension d’application d’authentification unique d’informations d’identification générique et une extension Kerberos intégrée à Apple.

Pour afficher les fonctionnalités actuelles de l’appareil que vous pouvez configurer, accédez à [Fonctionnalités de l’appareil iOS](../configuration/ios-device-features-settings.md) et à [Fonctionnalités de l’appareil macOS](../configuration/macos-device-features-settings.md).

S’applique à :
- iOS 13.0 et ultérieur
- macOS 10.15 et ultérieur

#### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079-----"></a>Associer des domaines à des applications sur des appareils macOS 10.15 et ultérieurs <!-- 4898079   -->
Sur les appareils macOS, vous pouvez configurer différentes fonctionnalités et envoyer ces fonctionnalités sur vos appareils à l’aide d’une stratégie (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour plateforme > **Fonctionnalités de l’appareil** pour type de profil). Dans cette mise à jour, vous pouvez associer des domaines à vos applications. Cette fonctionnalité permet de partager des informations d’identification avec des sites web associés à votre application et peut être utilisée avec l’extension d’authentification unique d’Apple, les liens universels et le remplissage automatique du mot de passe. 

Pour voir les fonctionnalités actuelles que vous pouvez configurer, accédez à [Paramètres des fonctionnalités d’appareil macOS dans Intune](../configuration/macos-device-features-settings.md).

S’applique à :
- macOS 10.15 et ultérieur

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474-----"></a>Utilisez « iTunes » et « applications » dans l’URL de l’App Store iTunes lors de l’affichage ou du masquage d’applications sur des appareils iOS supervisés <!-- 4928474   --> 
Dans Intune, vous pouvez créer des stratégies pour afficher ou masquer des applications sur vos appareils iOS supervisés (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour type de profil > **Afficher ou masquer des applications**). 

Vous pouvez entrer l’URL de l’App Store iTunes, par exemple `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. Dans cette mise à jour, `apps` et `itunes` peuvent être utilisés dans l’URL, par exemple :
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Pour plus d'informations sur ces paramètres, consultez [Afficher ou masquer les applications](../configuration/device-restrictions-ios.md#show-or-hide-apps).

S’applique à :
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Les valeurs de type de mot de passe de la stratégie de conformité Windows 10 sont plus claires et correspondent au fournisseur de services de chiffrement.<!-- 5138985 -->
Sur les appareils Windows 10, vous pouvez créer une stratégie de conformité qui requiert des fonctionnalités de mot de passe spécifiques (**Conformité des appareils** > **Stratégies** > **Créer une stratégie** > **Windows 10 et versions ultérieures** pour plateforme > **Sécurité système**). Dans cette mise à jour :
- Les valeurs **Type de mot de passe** sont plus claires et mises à jour pour correspondre à [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- Le paramètre **Expiration du mot de passe (jours)**  est mis à jour pour autoriser des valeurs de 1 à 730 jours. 

Pour plus d’informations sur les paramètres de conforme de Windows 10, consultez [Windows 10 et versions ultérieures pour marquer les appareils comme conformes ou non conformes](../protect/compliance-policy-create-windows.md). 

S’applique à :
- Windows 10 et versions ultérieures

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access-------4092920---"></a>Interface utilisateur mise à jour pour la configuration de l’accès à Microsoft Exchange local    <!-- 4092920 -->  
Nous avons mis à jour la console dans laquelle vous [configurez l’accès à Microsoft Exchange local](../protect/conditional-access-exchange-create.md). Toutes les configurations pour l’accès à Exchange local sont désormais disponibles dans le volet de la console où vous *autorisez le contrôle de l’accès à Exchange local*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices----1109650----"></a>Autoriser ou restreindre l’ajout de widgets d’applications à l’écran d’accueil sur les appareils de profil professionnel Android Entreprise <!-- 1109650  --> 
Sur les appareils Android Enterprise, vous pouvez configurer les fonctionnalités dans le profil professionnel (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour plate-forme > **Profil professionnel uniquement > Restrictions de l’appareil** pour type de profil). Dans cette mise à jour, vous pouvez autoriser les utilisateurs à ajouter des widgets exposés par les applications de profil professionnel à l’écran d’accueil de l’appareil.

Pour voir les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Profil professionnel Android Entreprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790-----"></a>Par défaut, les nouveaux locataires sont éloignés de la gestion des administrateurs d’appareils Android <!-- 4869790   -->
Les fonctionnalités d’administrateur d’appareils Android ont été remplacées par Android Entreprise. Par conséquent, nous vous recommandons d’utiliser Android Entreprise pour de nouvelles inscriptions à la place. Dans une prochaine mise à jour, les nouveaux locataires devront suivre les étapes préalables suivantes de l’inscription Android pour utiliser la gestion des administrateurs d’appareils : Accédez à **Intune** > **Inscription d’un appareil** > **Inscription Android** > **Appareils personnels et appartenant à l’entreprise avec privilèges d’administration d’appareils** > **Utiliser un administrateur d’appareils pour gérer les appareils**.

Les environnements des locataires existants ne seront pas modifiés. 

Pour plus d’informations sur l’administrateur d’appareils Android dans Intune, consultez [Inscription de l’administrateur d’appareils Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile----5012045-idmiss---"></a>Liste des appareils DEP associés à un profil <!-- 5012045 idmiss -->
Vous pouvez maintenant voir une liste paginée d’appareils du programme automatisé d’inscription des appareils (DEP) Apple associés à un profil. Vous pouvez effectuer une recherche dans la liste à partir de n’importe quelle page de la liste. Pour voir la liste, accédez à **Intune** > **Inscription d’appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisir un jeton > **Profils** > choisir un profil > **Appareils associés** (sous **Surveiller**). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des appareils

#### <a name="more-android-fully-managed-support----3464667-4631425-4631440-5227935-4062195-----"></a>Plus de prise en charge d’appareils Android entièrement gérés <!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Nous avons ajouté la prise en charge suivante pour les appareils Android entièrement gérés :

- Les certificats SCEP pour appareils Android entièrement gérés sont disponibles pour l’authentification par certificat sur les appareils gérés en tant que propriétaire de l’appareil. Les certificats SCEP sont déjà pris en charge sur les appareils de profil professionnel.  Avec les certificats SCEP pour le propriétaire de l’appareil, vous serez en mesure d’effectuer les opérations suivantes : <!-- 5227935 -->
    - Créer un profil SCEP sous la section DO d’Android Entreprise
    - Lier des certificats SCEP au profil Wi-Fi DO pour l’authentification
    - Lier des certificats SCEP aux profils VPN DO pour l’authentification
    - Lier des certificats SCEP aux profils de messagerie DO pour l’authentification (via AppConfig)
- Les applications système sont prises en charge sur les appareils Android Entreprise. Dans Intune, ajoutez une application système Android Entreprise en sélectionnant **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application**, sélectionnez **Application système Android Entreprise**. Pour plus d’informations, consultez [Ajouter des applications système Android à Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- Dans **Conformité de l’appareil** > **Android Entreprise** > **Propriétaire de l’appareil**, vous pouvez créer une stratégie de conformité qui définit le niveau d’attestation de Google SafetyNet.   <!-- 4631425 -->
- Sur les appareils Android Entreprise entièrement gérés, les fournisseurs de protection contre les menaces mobiles sont pris en charge. Dans **Conformité de l’appareil** > **Android Entreprise** > **Propriétaire de l’appareil**, vous pouvez choisir un niveau de menace acceptable. <!-- 4631440 --> [Paramètres Android Entreprise pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) répertorie les paramètres actuels.
- Sur les appareils Android Entreprise complètement managés, l’application Microsoft Launcher peut désormais être configurée via des stratégies de configuration d’application pour offrir à l’utilisateur final une expérience standardisée de l’appareil complètement managé. L’application Microsoft Launcher peut être utilisée pour personnaliser votre appareil Android. Si vous l’associez à un compte Microsoft ou un compte professionnel/scolaire, vous avez accès à votre calendrier, à vos documents et à vos activités récentes dans votre flux personnalisé. <!-- 5334044 -->

Avec cette mise à jour, nous sommes heureux d’annoncer que la prise en charge d’Android Enterprise entièrement gérée par Intune est désormais à disponibilité générale.

S’applique à :

- Appareils Android Entreprise complètement gérés

#### <a name="send-custom-notifications-to-a-single-device-----4928910---"></a>Envoyer des notifications à un seul appareil  <!-- 4928910 -->
Vous pouvez maintenant sélectionner un seul appareil, puis utiliser une action d’appareil à distance pour [envoyer une notification personnalisée uniquement à cet appareil](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment----4950491---"></a>Les actions de réinitialisation de réinitialisation et de code secret ne sont pas disponibles pour les appareils iOS inscrits à l’aide de l’inscription de l’utilisateur. <!-- 4950491 -->
L’inscription de l’utilisateur est un nouveau type d’inscription d’appareils Apple. Lorsque vous inscrivez des appareils à l’aide de l’inscription de l’utilisateur, les opérations à distance de réinitialisation et de réinitialisation du code secret ne sont pas disponibles pour ces appareils.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices----4665317---"></a>Prise en charge des appareils iOS 13 et macOS Catalina par Intune <!-- 4665317 -->
Intune prend maintenant en charge la gestion des appareils iOS 13 et macOS Catalina. Pour plus d’informations, consultez ce [billet de blog Prise en charge de iOS 13 et iPadOS par Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation-------3444125---"></a>Prise en charge de BitLocker pour la rotation de mot de passe de récupération pilotée par le client   <!--  3444125 -->
Utilisez les paramètres de protection de point de terminaison Intune pour configurer la [rotation de mot de passe de récupération pilotée par le client](../protect/endpoint-protection-windows-10.md#windows-encryption) pour BitLocker sur les appareils qui exécutent Windows version 1909 ou ultérieure.

Ce paramètre déclenche une actualisation du mot de passe de récupération piloté par le client après la récupération d’un lecteur de système d’exploitation (à l’aide de bootmgr ou de WinRE) et le déverrouillage du mot de passe de récupération sur un lecteur de données fixe. Ce paramètre actualise le mot de passe de récupération spécifique qui a été utilisé. Les autres mots de passe inutilisés sur le volume restent inchangés. Pour plus d’informations, consultez la documentation du fournisseur de services de chiffrement BitLocker pour [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus-----4705448----------"></a>Protection contre les falsifications pour l’antivirus Windows Defender  <!-- 4705448        -->
Utilisez Intune pour gérer la *protection contre les falsifications* pour l’antivirus Windows Defender. Vous trouverez le [paramètre de protection contre les falsifications](../protect/endpoint-protection-windows-10.md#windows-defender-security-center) dans le groupe Centre de sécurité Microsoft Defender si vous utilisez des profils de configuration pour la protection des points de terminaison Windows 10. Vous pouvez définir la protection contre les falsifications sur *Activée* pour activer les restrictions de protection contre les falsifications, sur *Désactivée* pour la désactiver, ou sur *Non configurée* pour conserver la configuration actuelle des appareils.  

Pour plus d’informations sur la protection contre les falsifications, consultez [Empêcher les modifications des paramètres de sécurité avec la protection contre les falsifications](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) dans la documentation de Windows. 

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available-----5317392---------"></a>Les paramètres avancés pour le pare-feu Windows Defender sont maintenant à disponibilité générale <!--  5317392       -->  
Les [règles de pare-feu personnalisées Windows Defender pour la protection des points de terminaison](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) que vous configurez dans le cadre d’un profil de configuration d’appareil ne sont plus en préversion publique, mais à disponibilité générale.  Vous pouvez utiliser ces règles pour spécifier le comportement du trafic entrant et sortant avec les applications, les adresses réseau et les ports. Ces règles ont été publiées en juillet en préversion publique. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-now-support-terms-of-use-policies----2358863-idmiss---"></a>Les balises d’étendue prennent désormais en charge les stratégies des conditions d’utilisation. <!-- 2358863 idmiss -->
Vous pouvez désormais assigner des [balises d’étendue](scope-tags.md) à des stratégies de conditions d’utilisation. Pour ce faire, accédez à **Intune** > **Inscription d’appareils** > **Conditions d’utilisation** > choisir un élément de la liste > **Propriétés** > **Balises d’étendue** > choisir une balise d’étendue.

## <a name="week-of-september-9-2019"></a>Semaine du 9 septembre 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="updates-to-microsoft-intune-app----4997846---"></a>Mise à jour de l’application Microsoft Intune <!-- 4997846 -->
L’application Microsoft Intune pour Android a été mise à jour avec les améliorations suivantes :
- Mise à jour et amélioration de la disposition pour inclure la navigation inférieure pour les actions les plus importantes.
- Ajout d’une page supplémentaire qui affiche le profil de l’utilisateur.
- Ajout de l’affichage des notifications actionnables dans l’application pour l’utilisateur, comme la nécessité de mettre à jour les paramètres de l’appareil.
- Ajout de l’affichage des notifications push personnalisées, alignant l’application sur la prise en charge récemment ajoutée dans les applications Portail d’entreprise pour iOS et Android. Pour plus d’informations, voir [Envoyer des notifications personnalisées dans Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993---"></a>Pour les appareils iOS, personnalisez l’écran de confidentialité du processus d’inscription du Portail d’entreprise <!-- 4394993 -->
À l’aide de Markdown, vous pouvez personnaliser l’écran de confidentialité du Portail d’entreprise que les utilisateurs finaux voient lors de l’inscription à iOS. Plus précisément, vous serez en mesure de personnaliser la liste des éléments que votre organisation ne peut pas voir ou faire sur l’appareil. Pour plus d’informations, consultez [Guide pratique pour configurer l’application Portail d’entreprise Intune](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Semaine du 2 septembre 2019

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-user-interface-update--tenant-status-dashboard-----5273210----"></a>Mise à jour de l’interface utilisateur Intune - Tableau de bord État du locataire  <!-- 5273210  -->
L’interface utilisateur du tableau de bord État du locataire a été mise à jour pour s’aligner sur les styles d’interface utilisateur d’Azure. Pour plus d’informations, consultez [État du locataire](../tenant-status.md).


## <a name="week-of-august-26-2019"></a>Semaine du 26 août 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Configurer les paramètres Microsoft Edge à l’aide de modèles d’administration pour Windows 10 et versions ultérieures <!-- 5228061 -->

Sur les appareils Windows 10 et versions ultérieures, vous pouvez créer des modèles d’administration pour configurer des paramètres de stratégie de groupe dans Intune. Dans cette mise à jour, vous pouvez configurer les paramètres qui s’appliquent à partir de la version 77 de Microsoft Edge.

Pour en savoir plus sur les modèles d’administration, consultez [Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Intune](../configuration/administrative-templates-windows.md).

S’applique à :

- Windows 10 et versions ultérieures (Windows RS4+)

## <a name="week-of-august-12-2019"></a>Semaine du 12 août 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>Contrôler le comportement de désinstallation de l’application iOS lors de la désinscription de l’appareil <!-- 3504144   -->
Les administrateurs peuvent gérer si une application est supprimée ou conservée sur un appareil quand l’appareil est désinscrit au niveau d’un utilisateur ou d’un groupe d’appareils. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Catégoriser les applications du Microsoft Store pour Entreprises <!-- 3926922 -->
Vous pouvez catégoriser les applications du Microsoft Store pour Entreprises. Pour ce faire, sélectionnez **Intune** > **Applicationsclientes** > **Applications** > Sélectionnez une application du Microsoft Store pour Entreprises >  **Informations sur l’application** > **Catégorie**. Dans le menu déroulant, attribuez une catégorie.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Notifications personnalisées pour les utilisateurs de l’application Microsoft Intune <!-- 4843354  -->
L’application Microsoft Intune pour Android prend désormais en charge l’affichage des notifications push personnalisées, en l’alignant sur la prise en charge récemment ajoutée dans les applications Portail d’entreprise pour iOS et Android. Pour plus d’informations, voir [Envoyer des notifications personnalisées dans Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Nouvelles fonctionnalités pour les appareils dédiés Android Entreprise s’exécutant en mode plein écran multi-application <!-- 3755304 3041943 3041946   -->

Dans Intune, vous pouvez contrôler les fonctionnalités et les paramètres dans une expérience en mode plein écran sur vos appareils dédiés Android Enterprise (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour plateforme > **Propriétaire de l’appareil uniquement, restrictions sur l’appareil** pour le type de profil).

Dans cette mise à jour, les fonctionnalités suivantes sont ajoutées :

- **Périphériques dédiés** > **Multi-application** : Le **bouton d’accueil virtuel** peut être affiché en balayant sur l’appareil, ou en flottant sur l’écran pour que les utilisateurs puissent le déplacer.
- **Périphériques dédiés** > **Multi-application** : **L’accès à la lampe torche** permet aux utilisateurs d’utiliser la lampe torche. 
- **Périphériques dédiés** > **Multi-application** : Le **contrôle du volume du média** permet aux utilisateurs de contrôler le volume du média de l’appareil à l’aide d’un curseur. 
- **Périphériques dédiés** > **Multi-application** :  **Activer un économiseur d’écran**, télécharger une image personnalisée et contrôler quand l’économiseur d’écran est affiché.

Pour voir les paramètres actuels, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

S’applique à :

- Appareils dédiés Android Entreprise

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Nouveaux profils d’applications et de configuration pour les appareils Android Entreprise complètement managés <!-- 3574215 3574238 3574235 3574232   -->
À l’aide de profils, vous pouvez configurer des paramètres qui appliquent des paramètres VPN, d’e-mail et Wi-Fi à votre propriétaire d’appareil Android Enterprise (complètement managés). Dans cette mise à jour, vous pouvez :

- utiliser [des stratégies de configuration d’applications](../apps/app-configuration-policies-use-android.md) pour déployer des paramètres de messagerie Outlook, Gmail et Nine Work ;
- utiliser des profils de configuration d'appareil pour déployer des [paramètres de certificat racine approuvés](../protect/certificates-configure.md) ;
- utiliser des profils de configuration d'appareil pour déployer des paramètres [VPN](../configuration/vpn-settings-android-enterprise.md) et [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Cette fonctionnalité permet aux utilisateurs de s’authentifier avec leur nom d'utilisateur et leur mot de passe pour les profils VPN, Wi-Fi et d’e-mail. Actuellement, l’authentification basée sur des certificats n’est pas disponible.

S’applique à :  
- Propriétaire d’appareil Android Entreprise (complètement managé)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>Contrôler les applications, les fichiers, les documents et les dossiers qui s’ouvrent quand les utilisateurs se connectent à des appareils macOS <!--3914202   -->
Vous pouvez activer et configurer des fonctionnalités sur des appareils macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). 

Dans cette mise à jour, il y a un nouveau paramètres Éléments de connexion pour contrôler quelles applications et quels fichiers, documents et dossiers s’ouvrent lorsqu’un utilisateur se connecte à l’appareil inscrit. 

Pour voir les paramètres actuels, accédez à [Paramètres des fonctionnalités d’appareil macOS dans Intune](../configuration/macos-device-features-settings.md).

S’applique à :  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Les délais remplacent des paramètres de redémarrage engagés pour les anneaux Windows Update   <!-- 4464404        -->
Pour s’aligner sur [les modifications récentes des services de maintenance Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), les anneaux de mise à jour Windows 10 d’Intune prennent désormais en charge les [paramètres de prise en charge des délais](../protect/windows-update-settings.md). Les *délais* déterminent à quel moment un appareil installe les mises à jour de sécurité et de fonctionnalités.  Sur les appareils qui exécutent Windows 10 1903 ou une version ultérieure, les *délais* remplacent les configurations de *redémarrage engagé*.  À l’avenir, les *délais* remplaceront le *redémarrage engagé* sur les versions antérieures de Windows 10 également.  

Si vous ne configurez pas les *délais*, les appareils continuent d’utiliser leurs paramètres de *redémarrage commencé*. Cependant, Intune déconseillera la prise en charge des paramètres de redémarrage commencé dans une future mise à jour.  

Prévoyez d’utiliser des *délais* pour tous vos appareils Windows 10. Après la mise en place des paramètres des *délais*, vous pouvez modifier vos configurations Intune pour que le *redémarrage engagé* ne soit pas configuré. Lorsqu’il n’est pas configuré, Intune arrête de gérer ces paramètres sur les appareils, mais ne supprime pas les dernières configurations du paramètre de l’appareil. Pour cette raison, les dernières configurations définies pour le *redémarrage engagé* restent actives et sont utilisées sur les appareils jusqu’à ce que ces paramètres soient modifiés par une méthode autre qu’Intune. Plus tard, lorsque la version des appareils Windows changera que la prise en charge des *délais* par Intune s’étendra à la version Windows des appareils, l’appareil commencera à utiliser les nouveaux paramètres, qui sont déjà en place.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Prendre en charge plusieurs connecteurs de certificats Microsoft Intune   <!--   4704642      -->
Intune prend désormais en charge l’installation et l’utilisation de plusieurs [connecteurs de certificats Microsoft Intune pour les opérations PKCS](../protect/certficates-pfx-configure.md). Ceci modifie l’équilibrage de charge et la haute disponibilité du connecteur. Chaque instance de connecteur peut traiter les demandes de certificat d’Intune.  Si un connecteur n’est pas disponible, d’autres connecteurs continuent de traiter les demandes. 

Pour utiliser plusieurs connecteurs, vous n’avez pas besoin de procéder à une mise à niveau vers la dernière version du logiciel connecteur.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Nouveaux paramètres et modifications apportées aux paramètres existants pour restreindre les fonctionnalités sur les appareils iOS et macOS <!-- 4867699 4867709   -->
Vous pouvez créer des profils pour restreindre des paramètres sur les appareils exécutant iOS et macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** ou **macOS** pour le type de plateforme > **Restrictions sur l'appareil**). Cette mise à jour inclut les fonctionnalités suivantes :

- Sur **macOS** > **Restrictions sur l’appareil** > **Cloud et stockage**, utilisez le nouveau paramètre **Handoff** pour empêcher des utilisateurs de commencer à travailler sur un appareil macOS, puis de continuer sur un autre appareil macOS ou iOS.

  Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-macos.md).

- Sur **iOS** > **Restrictions sur les appareils**, il y a quelques modifications :

  - **Applications intégrées** > **Localiser mon iPhone (mode supervisé uniquement)**  : Nouveau paramètre qui bloque cette fonctionnalité dans la fonctionnalité Rechercher mon application. 
  - **Applications intégrées** > **Localiser mes amis (mode supervisé uniquement)**  : Nouveau paramètre qui bloque cette fonctionnalité dans la fonctionnalité Rechercher mon application. 
  - **Sans fil** > **Modification de l’état Wi-Fi (mode supervisé uniquement)**  : Nouveau paramètre qui empêche les utilisateurs d’activer ou de désactiver le Wi-Fi sur l’appareil.
  - **Clavier et dictionnaire** > **QuickPath (mode supervisé uniquement)**  : Nouveau paramètre qui bloque la fonctionnalité QuickPath.
  - **Cloud et stockage** : **La continuation de l’activité** est renommée **Handoff**.

  Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

S’applique à :  
- macOS 10.15 et ultérieur
- iOS 13 et ultérieur

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Certaines restrictions sur les appareils iOS non supervisés seront supervisées uniquement avec la version iOS 13.0. <!-- 4867809   -->
Dans cette mise à jour, certains paramètres s’appliquent aux appareils supervisés uniquement avec la version iOS 13.0. Si ces paramètres sont configurés et attribués à des appareils non supervisés antérieurs à la version iOS 13.0, les paramètres sont toujours appliqués à ces appareils non supervisés. Ils s’appliquent également encore après la mise à niveau des appareils vers iOS 13.0. Ces restrictions sont supprimées sur les appareils non supervisés qui sont sauvegardés et restaurés. 

Ces paramètres incluent :

- App Store, affichage de document, jeux
  - App Store
  - Contenu iTunes explicite (musique, podcast ou actualités)
  - Ajout d’amis Game Center
  - Jeux multijoueur
- Applications intégrées
  - Appareil photo
    - FaceTime
  - Safari
    - Remplissage automatique
- Cloud et stockage
  - Sauvegarder sur iCloud
  - Bloquer la synchronisation des documents iCloud
  - Bloquer la synchronisation du trousseau iCloud

Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

S’applique à :  
- iOS 13.0 et ultérieur

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Amélioration de l’état des appareils pour le chiffrement FileVault macOS  <!-- 4944983         -->
Nous avons mis à jour plusieurs [messages d’état de l’appareil](../protect/encryption-monitor.md#device-encryption-status) pour le chiffrement FileVault sur les appareils MacOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>Certains paramètres d’analyse de l’antivirus Windows Defender dans le rapport indiquent un état d’échec <!-- 5119229 -->
Dans Intune, vous pouvez créer des stratégies afin d’utiliser l’antivirus Windows Defender pour analyser vos appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour plateforme > **Restrictions sur l’appareil** pour type de profil > **Antivirus Windows Defender**). Les rapports sur la **durée d’exécution d’une analyse quotidienne rapide** et le **type d’analyse système à effectuer** indique un état d’échec lorsqu’il s’agit en fait d’un état de réussite. 

Dans cette mise à jour, ce comportement est corrigé. Ainsi, les paramètres **Durée d’exécution d’une analyse quotidienne rapide** et **Type d’analyse système à effectuer** montrent un état de réussite lorsque l’analyse est terminée et un état d’échec lorsque les paramètres ne sont pas appliqués. 

Pour plus d’informations sur les paramètres de l’antivirus Windows Defender, consultez [Paramètres de l’appareil Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus). 

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="default-scope-tags----3702875----"></a>Balises de portée par défaut <!-- 3702875  -->
Une nouvelle balise d’étendue par défaut intégrée est désormais disponible. Tous les objets Intune sans balise qui prennent en charge des balises d’étendue sont automatiquement attribués à la balise d’étendue par défaut. La balise d’étendue **par défaut** est ajoutée à toutes les attributions de rôles existantes pour maintenir la parité avec l’expérience d’administration actuelle. Si vous ne souhaitez pas qu’un administrateur voit les objets Intune avec la balise d’étendue par défaut, supprimez la balise d’étendue par défaut de l’attribution de rôle. Cette fonctionnalité est similaire à la fonctionnalité des étendues de sécurité de System Center Configuration Manager. Pour plus d’informations, voir [Use RBAC and scope tags for distributed IT](scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée).

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Support de l’administrateur d’appareil d’inscription Android <!-- 4869749   -->
L’option d’inscription de l’administrateur de l’appareil Android a été ajoutée à la page d’inscription Android (**Intune** > **Inscription de l’appareil** > **Inscription Android**). L’administrateur de l’appareil Android est toujours activé par défaut pour tous les locataires.  Pour plus d’informations, consultez [Inscription de l’administrateur de l’appareil Android](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Ignorer d’autres écrans dans l’Assistant Configuration <!--4877451  -->
Vous pouvez définir des profils de Programme d’inscription des appareils pour ignorer les écrans suivants de l’Assistant Configuration :
- Pour iOS
    - Apparence
    - Langage Express
    - Langage par défaut
    - Migration d’un appareil vers un autre
- Pour macOS
    - Extinction de l’écran
    - Configuration de Touch ID

Pour plus d’informations sur la personnalisation de l’Assistant Configuration, consultez [Créer un profil d’inscription Apple pour iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) et [Créer un profil d’inscription Apple pour MacOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Ajouter une colonne utilisateur au processus de chargement CSV d’un appareil Autopilot <!-- 3823054 -->
Vous pouvez maintenant ajouter une colonne utilisateur au téléchargement CSV pour les appareils Autopilot. Ceci vous permet d’affecter des utilisateurs en bloc au moment où vous importez le volume partagé de cluster. Pour plus d’informations, consultez [Inscrire des appareils Windows dans Intune avec Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Gestion des appareils

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurer une limite de temps de nettoyage automatique des appareils réduite à 30 jours <!--4231059  -->
Vous pouvez définir la limite de temps de nettoyage automatique des appareils sur 30 jours (au lieu de la limite précédente de 90 jours) après la dernière connexion. Pour ce faire, accédez à **Intune** > **Appareils** > **Configuration** > **Règles de nettoyage des appareils**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Numéro de build inclus sur la page Matériel du périphérique Android <!-- 4461910   -->
Une nouvelle entrée sur la page Matériel de chaque appareil Android inclut le numéro de build du système d’exploitation de l’appareil. Pour plus d’informations, consultez [Afficher les détails de l’appareil dans Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Semaine du 5 août 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies est un OEM pris en charge pour OEMConfig sur les appareils Android Entreprise  <!-- 4843713 -->

Dans Intune, vous pouvez créer des profils de configuration d’appareils et appliquer des paramètres à des appareils Android Entreprise à l’aide d’OEMConfig (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **OEMConfig** pour le type de profil).

Dans cette mise à jour, Zebra Technologies est un fabricant d’ordinateurs OEM pris en charge pour OEMConfig. Pour plus d’informations sur OEMConfig, consultez [Utilisation et gestion des appareils Android Entreprise avec OEMConfig](../configuration/android-oem-configuration-overview.md).

S’applique à :  
- Android Entreprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Semaine du 22 juillet 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Notifications personnalisées destinées aux groupes et aux utilisateurs    <!-- 16766574          -->
Depuis l’application Portail d’entreprise, envoyez des notifications push personnalisées aux utilisateurs, sur les appareils iOS et Android que vous gérez avec Intune. Ces notifications push mobiles sont hautement personnalisables, avec du texte libre, et peuvent être utilisées pour n’importe quel motif. Vous pouvez les cibler sur différents groupes d’utilisateurs de votre organisation. Pour en savoir plus, voir [Envoyer des notifications personnalisées dans Intune](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>Application du contrôleur de stratégie d’appareil de Google <!-- 3041950  -->
L’application Managed Home Screen permet désormais d’accéder à l’application Android Device Policy de Google. L’application Managed Home Screen est un lanceur personnalisé utilisé pour les appareils inscrits dans Intune en tant qu’appareils dédiés Android Enterprise (AE) utilisant le mode kiosque multi-application. Vous pouvez accéder à l’application Android Device Policy ou guider les utilisateurs vers cette application à des fins de support et de débogage. Cette fonctionnalité de lancement est disponible au moment de l’inscription et du verrouillage de l’appareil dans Managed Home Screen. Aucune installation supplémentaire n’est nécessaire pour utiliser cette fonctionnalité.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Paramètres de protection Outlook pour les appareils iOS et Android <!-- 3212619 -->
Vous pouvez maintenant configurer les paramètres généraux de configuration de la protection des données et des applications pour Outlook sur iOS et Android, en utilisant des contrôles d’administration Intune simples, sans inscription d’appareil. Les paramètres de configuration d’application généraux fournissent la parité avec les paramètres que les administrateurs peuvent activer lors de la gestion de Microsoft Outlook pour iOS et Android sur des appareils inscrits. Pour plus d’informations sur les paramètres Outlook, voir [Déploiement des paramètres de configuration d’une application Outlook pour iOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Utilisez « règles d’applicabilité » lors de la création de profils de configuration d’appareil Windows 10 <!-- 2549910 eeready   idstaged -->

Vous créez des profils de configuration d’appareil Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme > **Règles de mise en application**). Vous serez en mesure de créer une **règle d’applicabilité** pour que le profil s’applique seulement à une édition ou version spécifique. Par exemple, vous créez un profil qui active certains paramètres de BitLocker. Une fois que vous avez ajouté le profil, utilisez une règle d’applicabilité pour que le profil s’applique seulement aux appareils exécutant Windows 10 Entreprise.

Pour savoir comment ajouter une règle d’applicabilité, voir [Règles de mise en application](../configuration/device-profile-create.md#applicability-rules).

S’applique à : Windows 10 et versions ultérieures

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>Utiliser des jetons pour ajouter des informations spécifiques à l’appareil dans des profils personnalisés pour les appareils iOS et macOS <!-- 3330008  -->
Vous pouvez utiliser des profils personnalisés sur des appareils iOS et macOS pour configurer des paramètres et des fonctionnalités non intégrés à Intune (**Configuration des appareils** > **Profils** > **Créer un profil** > **iOS** ou **macOS** pour la plate-forme > **Personnalité** pour le type de profil). Dans cette mise à jour, vous pouvez ajouter des jetons dans vos fichiers `.mobileconfig` pour ajouter des informations spécifiques à l’appareil. Par exemple, vous pouvez ajouter `Serial Number: {{serialnumber}}` à votre fichier de configuration pour afficher le numéro de série de l’appareil.

Pour créer un profil personnalisé, voir [Utiliser des paramètres personnalisés pour les appareils macOS dans Microsoft Intune](../configuration/custom-settings-ios.md) ou [Utiliser des paramètres personnalisés pour les appareils iOS dans Microsoft Intune](../configuration/custom-settings-macos.md).

S’applique à :
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Nouveau concepteur de configuration lors de la création d’un profil OEMConfig pour Android Enterprise <!-- 3712769   -->
Dans Intune, vous pouvez créer un profil de configuration d’appareil qui utilise une application OEMConfig (Configuration des appareils > Profils > Créer un profil > Android Enterprise pour la plateforme > OEMConfig pour le type de profil). Dans ce cas, un éditeur JSON s’ouvre avec un modèle et des valeurs, que vous pouvez modifier. 

Cette mise à jour inclut un concepteur de configuration, qui offre une expérience utilisateur améliorée grâce à l’affichage des détails incorporés dans l’application, y compris des titres et des descriptions. L’éditeur JSON reste disponible. Il affiche toutes les modifications que vous apportez dans le concepteur de configuration.

Pour connaître les paramètres actuels, consultez la section relative à [l’utilisation et la gestion des appareils Android Enterprise avec OEMConfig](../configuration/android-oem-configuration-overview.md).

S’applique à : Android Entreprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Interface utilisateur mise à jour pour la configuration de Windows Hello  <!-- 4089576            -->
Nous avons mis à jour la console dans laquelle vous [ configurez Intune pour l’utilisation de Windows Hello Entreprise.](../protect/windows-hello.md) Tous les paramètres de configuration sont désormais disponibles dans le volet de la console dans lequel vous activez la prise en charge de Windows Hello. 


#### <a name="intune-powershell-sdk----4924113---"></a>Kit de développement logiciel (SDK) PowerShell Intune <!-- 4924113 --> 
Le Kit de développement logiciel (SDK) Intune PowerShell, qui prend en charge l’API Intune via Microsoft Graph, a été mis à jour vers la version 6.1907.1.0. Ce Kit prend désormais en charge les éléments suivants :
- Il gère Azure Automation.
- Il prend en charge les opérations de lecture d’authentification pour l’application uniquement. 
- Il prend en charge les noms abrégés conviviaux en tant qu’alias.
- Il respecte les conventions d’affectation de noms de PowerShell. Plus précisément, le paramètre `PSCredential` (sur la cmdlet `Connect-MSGraph`) a été renommé comme suit : `Credential`.
- Il prend en charge la spécification manuelle de la valeur de l’en-tête `Content-Type` lors de l’utilisation de la cmdlet `Invoke-MSGraphRequest`.

Pour en savoir plus, consultez la section relative au [Kit de développement logiciel (SDK) pour l’API Graph de Microsoft Intune](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Mises à jour relatives aux restrictions d’inscription  <!-- 2871968 -->
Les restrictions d’inscription pour les nouveaux locataires ont été mises à jour afin que les profils de travail Android Enterprise soient autorisés par défaut. Les locataires existants ne sont pas modifiés. Pour utiliser les profils de travail Android Enterprise, vous devez tenter de [connecter votre compte Intune à votre compte Google Play managé](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Mises à jour de l’interface utilisateur pour les restrictions d’inscription et les inscriptions Apple <!--4089575, 4089579  -->
Les deux processus suivants utilisent une interface utilisateur de style Assistant :
- Inscription d’appareils Apple. Pour en savoir plus, voir [Inscrire automatiquement des appareils iOS avec le Programme d’inscription des appareils d’Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Création de restrictions d’inscription. Pour en savoir plus, consultez la section relative à la [définition de restrictions d’inscription](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Gestion de la préconfiguration des identificateurs d’appareils d’entreprise pour les appareils Android Q <!-- 4711509  idmiss -->
Dans Android Q (V10), Google supprime la capacité des agents MDM sur les appareils Android managés par des appareils Android existants (administrateur d’appareil) à collecter des informations sur les identificateurs d’appareil.  Intune propose une fonctionnalité pour permettre aux administrateurs informatiques de [préconfigurer une liste de numéros de série d’appareil, ou IMEI,](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) de façon à baliser ces appareils automatiquement, en tant que propriété d’entreprise. Cette fonctionnalité ne fonctionne pas pour les appareils Android Q managés par l’administrateur d’appareils.  Que vous chargiez le numéro de série ou le numéro IMEI de l’appareil, ce dernier est toujours considéré comme personnel lors de l’inscription dans Intune.  Vous pouvez basculer manuellement la propriété vers l’entreprise après l’inscription.  Cela affecte uniquement les nouvelles inscriptions.  Les appareils Android managés avec des profils de travail ne sont pas affectés par cette modification et continuent de fonctionner comme ils le font aujourd’hui.  En outre, les appareils Android Q inscrits en tant qu’administrateurs de l’appareil ne pourront plus signaler le numéro de série ou IMEI en tant que propriétés de l’appareil dans la console Intune.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Les icônes associées aux inscriptions Android Entreprise ont été modifiées (profil de travail, appareils dédiés ou appareils entièrement managés) <!-- 4977730 -->
Les icônes des profils d’inscription d’Android Entreprise ont été modifiées. Pour afficher les nouvelles icônes, accédez à **Intune** > **Inscription** > **Inscription Android** > et cherchez dans **Profils d’inscription**.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Modification relative à la collection de données de diagnostic Windows <!-- 4113859 -->
La valeur par défaut de la collection de données de diagnostic a changé pour les appareils exécutant Windows 10, version 1903 et versions ultérieures. À compter de Windows 10 version 1903, la collection des données de diagnostic est activée par défaut. Les données de diagnostic Windows sont des données techniques vitales des appareils Windows. Elles portent sur ces derniers et indiquent les performances de Windows et d’autres logiciels associés. Pour plus d’informations, consultez [Configurer les données de diagnostic Windows dans votre organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Les appareils AutoPilot ont également opté pour la télémétrie « complète », sauf indication contraire dans le profil Autopilot avec [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestion des appareils

#### <a name="improve-device-location---3855417----"></a>Améliorer la localisation d’appareils<!-- 3855417  -->
Vous pouvez effectuer un zoom avant sur les coordonnées exactes d’un appareil à l’aide de l’action **Localiser l’appareil**. Pour plus d’informations sur la localisation d’appareils iOS perdus, consultez la section relative à la [recherche d’appareils iOS perdus](../remote-actions/device-locate.md).


### <a name="device-security"></a>Sécurité des appareils

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Paramètres avancés pour le pare-feu Windows Defender (préversion publique)  <!--  1311949     -->  
Utilisez Intune afin de gérer [des règles de pare-feu personnalisées dans le cadre d’un profil de configuration d’appareil](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) pour la protection des terminaux sur Windows 10. Les règles peuvent spécifier le comportement du trafic entrant et sortant avec les applications, les adresses réseau et les ports. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Interface utilisateur mise à jour pour la gestion des bases de référence de la sécurité   <!-- 4091125     -->
Nous avons mis à jour [l’expérience de création et de modification](../protect/security-baselines.md#create-the-profile) dans la console Intune pour nos bases de référence de la sécurité. Ces modifications sont notamment :

Un format de style Assistant plus simple, condensé au sein d’un même panneau. Cette nouvelle conception met un terme à la prolifération des panneaux, qui oblige les professionnels de l’informatique à parcourir plusieurs volets distincts.  
Vous pouvez maintenant créer des affectations dans le cadre de l’expérience de création et de modification, au lieu de devoir affecter des bases de référence ultérieurement. Nous avons ajouté une synthèse des paramètres que vous pouvez afficher avant de créer une base de référence et d’en modifier une. Lors de la modification, la synthèse affiche uniquement la liste des éléments définis dans une catégorie de propriétés en cours de modification.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Semaine du 15 juillet 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Icônes Managed Home Screen et Managed Settings <!-- 4918107 -->
L’icône Managed Home Screen et celle des **paramètres managés** ont été mises à jour. L’application Managed Home Screen est uniquement utilisée pour les appareils inscrits dans Intune, en tant qu’appareils dédiés Android Enterprise (AE) qui exécutent le mode kiosque multi-application. Pour en savoir plus sur l’application Managed Home Screen, voir [Configurer l’application Microsoft Managed Home Screen pour Android Entreprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android Device Policy sur des appareils Android Enterprise dédiés <!-- 4918136 -->
Vous pouvez accéder à l’application Android Device Policy à partir de l’écran de débogage de l’application Managed Home Screen. L’application Managed Home Screen est uniquement utilisée pour les appareils inscrits dans Intune, en tant qu’appareils dédiés Android Enterprise (AE) qui exécutent le mode kiosque multi-application. Pour en savoir plus, voir [Configurer l’application Microsoft Managed Home Screen pour Android Entreprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>Mises à jour du Portail d’entreprise iOS <!-- 3902931 -->
Le nom de votre société sur les invites de gestion des applications iOS remplace le texte « i.manage.microsoft.com » en cours. Par exemple, les utilisateurs verront le nom de leur société au lieu de « i.manage.microsoft.com » lorsque les utilisateurs tenteront d’installer une application iOS à partir du Portail d’entreprise ou lorsque les utilisateurs autorisent la gestion de l’application. Elle sera déployée pour tous les clients au cours des prochains jours.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>Gérer FileVault pour macOS   <!--  3858502 + 4557986 + 1210104  -->
Vous pouvez utiliser Intune pour [gérer le chiffrement de clé FileVault pour les appareils macOS](../protect/encrypt-devices.md). Pour chiffrer des appareils, vous pouvez utiliser un profil de configuration de protection des points de terminaison.

La prise en charge de FileVault inclut le chiffrement des appareils non chiffrés, le dépôt de la clé (escrow) de récupération personnelle des appareils, la rotation automatique ou manuelle des clés de chiffrement personnelles et la récupération des clés pour vos appareils d’entreprise. Les utilisateurs finaux peuvent également utiliser le site Web Portail d’entreprise pour obtenir la clé de récupération personnelle de leurs appareils chiffrés. 

Nous avons également développé le rapport sur le chiffrement de façon à inclure des [informations sur FileVault](../protect/encryption-monitor.md) avec des informations pour BitLocker, afin que vous puissiez afficher l’ensemble des détails sur le chiffrement d’appareils depuis un endroit centralisé. 

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>La réinitialisation automatique de Windows AutoPilot supprime l’utilisateur principal de l’appareil <!-- 4156123 -->
Lorsque le logiciel Autopilot est utilisé sur un appareil, l’utilisateur principal de l’appareil sera supprimé. L’utilisateur suivant qui se connecte après la réinitialisation est défini en tant qu’utilisateur principal. Cette fonction sera déployée pour tous les clients au cours des jours suivants.

## <a name="week-of-july-8-2019"></a>Semaine du 8 juillet 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nouveaux paramètres Office, Windows et OneDrive dans les modèles d’administration Windows 10 <!-- 3510695 -->

Vous pouvez créer des modèles d’administration dans Intune qui imitent la gestion de stratégies de groupe locale (**Gestion des appareils** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Modèles d’administration** pour le type de profil).

Cette mise à jour inclut davantage de paramètres Office, Windows et OneDrive, que vous pouvez ajouter à vos modèles. Grâce à ces nouveaux paramètres, vous pouvez désormais configurer plus de 2 500 paramètres entièrement basés sur le Cloud.

Pour plus d’informations sur cette fonctionnalité, voir [Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Microsoft Intune](../configuration/administrative-templates-windows.md).

S’applique à : Windows 10 et versions ultérieures

## <a name="week-of-july-1-2019"></a>Semaine du 1 juillet 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>AAD et APP sur des appareils Android Enterprise <!-- 3574267 -->
Lors de l’intégration d’appareils Android Enterprise entièrement managés, les utilisateurs peuvent s’inscrire auprès de Microsoft Active Directory (AAD) lors de la configuration initiale de leur nouvel appareil ou de leur appareil sur lequel les paramètres d’usine ont été rétablis. Auparavant, une fois la configuration d’un appareil entièrement managé terminée, l’utilisateur doit gérer manuellement l’application Microsoft Intune pour démarrer l’inscription auprès d’AAD. Désormais, lorsque l’utilisateur se trouve sur la page d’origine de l’appareil après la configuration initiale, l’appareil est inscrit et enregistré.

Outre les mises à jour d’AAD, les stratégies Intune App Protection (APP) sont désormais prises en charge sur les appareils Android Enterprise entièrement managés. Cette fonctionnalité sera disponible lors du lancement. Pour en savoir plus, voir [Ajouter des applications Google Play managé à des appareils d’entreprise Android avec Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Semaine du 24 juin 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configurer le navigateur qui est autorisé à établir une liaison aux données de l’organisation <!-- 3145939 -->
Les stratégies Intune App Protection (APP) sur les appareils Android et iOS vous permettent de transférer des liens web de l’organisation vers un navigateur spécifique au-delà de Microsoft Intune Managed Browser ou de Microsoft Edge.  Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>La page Toutes les applications identifie les applications MSFB comme étant en ligne ou hors ligne<!--4089647 -->
La page **Toutes les applications** inclut désormais des étiquettes permettant d’identifier les applications Microsoft Store for Business (MSFB) comme étant hors ligne ou en ligne. Chaque application MSFB comprend désormais un suffixe indiquant qu’elle est **en ligne** ou **hors ligne**. La page Détails de l’application comprend également des informations sur le **type de licence** et la **prise en charge de l’installation de contextes d’appareil** (uniquement les applications sous licence hors ligne).

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Application Portail d’entreprise sur les appareils Windows partagés <!--4393553 -->
Les utilisateurs peuvent désormais accéder à l’application Portail d’entreprise sur des appareils Windows partagés. Les utilisateurs finaux verront apparaître l’étiquette **Partagé** sur la mosaïque de l’appareil. Cela s’applique à la version de l’application Portail d’entreprise 10.3.45609.0 de Windows, ainsi que les versions ultérieures.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Afficher toutes les applications dans la nouvelle page Portail d’entreprise <!-- 4224326 -->
La page **Applications installées** du portail d’entreprise liste toutes les applications gérées (obligatoires ou disponibles) qui sont installées sur l’appareil d’un utilisateur. En plus du type d’affectation, les utilisateurs peuvent voir l’éditeur de l’application, sa date de publication et son état actuel d’installation. Si aucune application n’est obligatoire ou disponible, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Pour afficher la nouvelle page sur le Web, accédez au [site web Portail d’entreprise](https://portal.manage.microsoft.com), puis cliquez sur **Applications installées**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>La nouvelle vue permet aux utilisateurs de l’application de voir toutes les applications gérées qui sont installées sur l’appareil <!-- 2352913 -->  
L’application Portail d’entreprise pour Windows liste désormais toutes les applications gérées (obligatoires ou disponibles), qui sont installées sur l’appareil d’un utilisateur. Les utilisateurs peuvent également voir les installations d’applications tentées et en attente, ainsi que leur état actuel. Si aucune application n’est obligatoire ou disponible, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Pour afficher la nouvelle vue, dans le volet de navigation du portail d’entreprise, sélectionnez **Applications** > **Applications installées**.    

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurer les paramètres pour les extensions de noyau sur les appareils macOS <!-- 2043024 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme). Cette mise à jour inclut un nouveau groupe de paramètres permettant de configurer et d’utiliser les extensions de noyau sur vos appareils. Vous pouvez ajouter des extensions spécifiques ou autoriser toutes les extensions d’un partenaire ou d’un développeur spécifique.

Pour en savoir plus sur cette fonctionnalité, consultez la [vue d’ensemble des extensions de noyau](../configuration/kernel-extensions-overview-macos.md) et [les paramètres des extensions de noyau](../configuration/kernel-extensions-settings-macos.md).

S’applique à : macOS 10.13.2 et versions ultérieures

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>Le paramètre Applications du Store uniquement pour les appareils Windows 10 inclut des options de configuration supplémentaires <!-- 2697002 -->
Quand vous créez un profil de restrictions d’appareil pour les appareils Windows, vous pouvez utiliser le paramètre **Applications du Store uniquement** afin que les utilisateurs installent uniquement des applications de l’App Store Windows (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **Restrictions sur l’appareil** comme type de profil). Dans cette mise à jour, ce paramètre est développé pour prendre en charge davantage d’options. 

Pour consulter le paramètre actuel, voir [Paramètres des appareils Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités dans Intune](../configuration/device-restrictions-windows-10.md#app-store).

S’applique à : Windows 10 et versions ultérieures

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Déployez plusieurs profils d’appareils Extensions de mobilité Zebra sur un appareil, sur le même groupe d’utilisateurs ou sur le même groupe d’appareils <!-- 4089955 -->
Dans Intune, vous pouvez utiliser des Extensions de mobilité Zebra (MX) dans un profil de configuration d’appareil pour personnaliser des paramètres d’appareils Zebra non intégrés à Intune. Actuellement, vous pouvez déployer un profil sur un seul appareil. Dans cette mise à jour, vous pouvez déployer plusieurs profils pour :
- Le même groupe d’utilisateurs
- Le même groupe d’appareils
- Un seul appareil

[Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Microsoft Intune](../configuration/android-zebra-mx-overview.md) montre comment utiliser MX dans Intune.

S’applique à : Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Certains paramètres kiosque sur les appareils iOS sont définis avec « Bloquer » à la place de « Autoriser » <!-- 4404075  -->
Quand vous créez un profil de restrictions d’appareil sur des appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions sur l’appareil** comme type de profil > **Kiosque**), vous définissez le **Verrouillage automatique**, la **Modification de sonnerie**, la **Rotation de l'écran**, le **Bouton de veille de l’écran** et les **Boutons de volume**. 

Dans cette mise à jour, les valeurs sont **Bloquer** (pour bloquer la fonctionnalité) ou **Non configuré** (pour autoriser la fonctionnalité). Pour consulter les paramètres, accédez à la section [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md#kiosk). 

S’applique à : iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>Utiliser Face ID pour l’authentification par mot de passe sur les appareils iOS <!-- 4490704 -->
Quand vous créez un profil de restrictions d’appareil pour les appareils iOS, vous pouvez utiliser une empreinte digitale comme mot de passe. Dans cette mise à jour, les paramètres de mot de passe par empreinte digitale autorisent également la reconnaissance faciale (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions sur l’appareil** comme type de profil > **Mot de passe**). Par conséquent, les paramètres suivants sont modifiés :

- **Déverrouillage par empreinte digitale** est désormais **Déverrouillage de Touch ID et Face ID**.
- **Modification de l’empreinte digitale (supervisé uniquement)** est désormais **Modification de Touch ID et Face ID (supervisé uniquement)** .

Face ID est disponible dans iOS 11.0 et versions ultérieures. Pour consulter les paramètres, voir [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md#password).

S’applique à : iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>Les restrictions appliquées aux fonctionnalités de l’App Store et de jeu sur les appareils iOS dépendent désormais de la région de classification <!-- 4593948 -->
Dans les appareils iOS, vous pouvez autoriser ou restreindre les fonctionnalités liées au jeu, à l’App Store et à l’affichage de documents (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions sur l’appareil** comme type de profil > **App Store, affichage de documents, jeux**). Vous pouvez également choisir la région des classifications ; par exemple, les États-Unis. 

Dans cette mise à jour, la fonctionnalité **Applications** est devenue un enfant de **Région des classifications** et dépend de **Région des classifications**. Pour consulter les paramètres, voir [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

S’applique à : iOS

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Prise en charge de la jonction Azure AD Hybride par Windows AutoPilot <!-- 4809146-->
La version de Windows Autopilot pour les appareils existants prend désormais en charge la jonction Azure AD Hybride (en plus de la prise en charge de la fonction Jonction Azure AD). S’applique aux appareils Windows 10 version 1809 et versions ultérieures. Pour en savoir plus, voir [Windows Autopilot pour les appareils existants](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Gestion des appareils

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Voir le niveau du correctif de sécurité pour les appareils Android <!-- 4461911 -->
Vous pouvez désormais afficher le niveau du correctif de sécurité pour les appareils Android. Pour ce faire, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel**.
Le niveau de correctif est indiqué dans la section **Système d’exploitation**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Affecter des balises d’étendue à tous les appareils gérés d’un groupe de sécurité <!-- 3173810 -->
Vous pouvez maintenant affecter des balises d’étendue à un groupe de sécurité et tous les appareils qu’il contient sont également associés à ces balises. La balise d’étendue sera également affectée à tous les appareils présents dans ces groupes. Les balises d’étendue définies avec cette fonctionnalité remplacent les balises d’étendue définies avec le flux actuel de balises d’étendue d’appareil. Pour en savoir plus, voir [Use RBAC and scope tags for distributed IT](scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée).

### <a name="device-security"></a>Sécurité des appareils

#### <a name="use-keyword-search-with-security-baselines-------"></a>Utiliser la recherche par mot clé avec les bases de référence de la sécurité <!--  -->
Lorsque vous créez ou modifiez des [profils de base de référence de la sécurité](../protect/security-baselines.md#create-the-profile), vous pouvez spécifier des mots clés dans la nouvelle barre *Rechercher* pour filtrer les groupes de paramètres disponibles sur ceux qui contiennent vos critères de recherche. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>La fonctionnalité Bases de référence de sécurité est désormais disponible en général  <!-- 3785395 -->
La fonctionnalité **Bases de référence de sécurité** n’est plus en préversion et est en disponibilité générale.  Cela signifie que la fonctionnalité est prête à être utilisée en production. Toutefois, les modèles de base de référence peuvent rester en préversion et être évalués ; ils passent en disponibilité générale au cas par cas.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>Le modèle Base de référence de sécurité MDM est en disponibilité générale   <!-- 3794072, 4217151,  3534649 -->
Le modèle Base de référence de sécurité MDM n’est plus en préversion et est en disponibilité générale. Le modèle en disponibilité générale est identifié en tant que **base de référence de sécurité MDM pour mai 2019**.  Il s’agit d’un nouveau modèle, et non d’une mise à niveau à partir de la préversion.  En tant que nouveau modèle, vous devez vérifier les [paramètres qu’il contient](../protect/security-baseline-settings-mdm.md), puis créer des profils pour déployer le modèle sur votre appareil. D’autres modèles de base de référence de sécurité peuvent rester en préversion. Pour obtenir la liste des bases de référence de sécurité disponibles, voir [Bases de référence de la sécurité disponibles](../protect/security-baselines.md#available-security-baselines).  

Outre le fait qu’il s’agit d’un nouveau modèle, le modèle *Base de référence de sécurité MDM pour mai 2019* comprend les deux paramètres que nous avons récemment annoncés dans notre article dans le développement :  
- Au-dessus du verrouillage : activation vocale des applications à partir d’un écran verrouillé  
- DeviceGuard : utilisation de la sécurité basée sur la virtualisation au prochain redémarrage de l’appareil.  

Le modèle *Base de référence de sécurité MDM pour mai 2019* comprend également l’ajout de plusieurs nouveaux paramètres, la suppression d’autres paramètres et une révision de la valeur par défaut d’un paramètre. Pour obtenir une liste détaillée des modifications apportées de la préversion à la mise en disponibilité générale, voir **Ce qui a changé dans le nouveau modèle**.

#### <a name="security-baseline-versioning-----3194322---"></a>Bases de référence de la sécurité pour le contrôle de version  <!-- 3194322 -->
Bases de référence de la sécurité pour le contrôle de version dans Intune. Avec cette prise en charge, au fur et à mesure que de nouvelles versions de chaque base de référence de la sécurité sont publiées, vous pouvez mettre à jour vos profils de base de référence de la sécurité existants pour utiliser la nouvelle version et ce, sans avoir à recréer et à déployer une nouvelle base. En outre, dans la console Intune, vous pouvez afficher des informations sur chaque base de référence de la sécurité, comme le nombre de profils individuels qui l’utilisent, le nombre de versions de bases différentes utilisées par vos profils et la date de la dernière version d’une base de référence de la sécurité.  Pour en savoir plus, consultez la section relative aux **bases de référence de la sécurité**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>Le paramètre Utilisez des clés de sécurité pour la connexion a été déplacé  <!-- 4501151 -->
Le paramètre de configuration d’appareil relatif à la protection des identités appelé **Utilisez des clés de sécurité pour la connexion** n’est plus un sous-paramètre de *Configurer Windows Hello Entreprise*. Il s’agit désormais d’un paramètre de niveau supérieur qui est toujours disponible, même lorsque vous n’activez pas l’utilisation de Windows Hello Entreprise. Pour en savoir plus, consultez la section relative à la [protection des identités](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>De nouvelles autorisations pour les administrateurs de groupe affectés   <!-- 4504437   -->
Le rôle d’administrateur scolaire intégré d’Intune dispose désormais d’autorisations de création, de lecture, de mise à jour et de suppression (CRUD) pour les applications managées. Suite à cette mise à jour, si vous êtes affecté en tant qu’administrateur de groupe dans Intune Éducation, vous pouvez désormais créer, afficher, mettre à jour et supprimer le certificat Push MDM iOS, les jetons de serveur MDM iOS et les jetons VPP iOS, ainsi que [toutes les autorisations existantes dont vous disposez](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Pour effectuer l’une de ces actions suivantes, accédez à **Paramètres du client** > **Gestion des appareils iOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Les applications peuvent utiliser l’API Graph pour appeler des opérations de lecture sans informations d’identification de l’utilisateur <!-- 4655885 -->
Les applications peuvent appeler des opérations de lecture d’API Graph Intune avec leur identité sans informations d’identification d’utilisateur. Pour en savoir plus sur l’accès à l’API Microsoft Graph API pour Intune, consultez la section relative à [l’utilisation d’Intune dans Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Application de balises d’étendue aux applications Microsoft Store for Entreprises <!-- 4392555 -->
Vous pouvez désormais appliquer des balises d’étendue aux applications Microsoft Store for Entreprises. Pour en savoir plus à ce sujet, voir [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Semaine du 17 juin 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="new-features-in-microsoft-intune-app"></a>Nouvelles fonctionnalités dans l’application Microsoft Intune
Nous avons ajouté de nouvelles fonctionnalités à l’application Microsoft Intune (préversion) pour Android. Les utilisateurs d’appareils Android complètement managés peuvent maintenant :  

* Afficher et gérer des appareils qu’ils ont inscrits via le Portail d’entreprise Intune ou l’application Microsoft Intune    
* Contacter leur organisation pour bénéficier du support    
* Envoyer leurs commentaires à Microsoft    
* afficher les conditions générales, si elles ont été définies par leur organisation.    

## <a name="week-of-june-10-2019"></a>Semaine du 10 juin 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Nouveaux exemples d’applications illustrant l’intégration du kit de développement logiciel (SDK) Intune disponible sur GitHub <!-- 2653471 -->
Le compte GitHub msintuneappsdk a ajouté de nouveaux exemples d'application pour iOS (Swift), Android, Xamarin.iOS, Xamarin Forms et Xamarin.Android. Ces applications sont censées remplacer notre documentation existante et fournir des exemples d’intégration du kit de développement logiciel (SDK) de l’application Intune dans vos propres applications mobiles. Si vous êtes développeur d’applications et que vous avez besoin de conseils supplémentaires concernant le kit de développement logiciel (SDK) Intune, consultez les exemples liés :
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) : une application de messagerie instantanée iOS native (Swift) qui utilise la bibliothèque d'authentification Azure Active Directory (ADAL) pour l’authentification répartie.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) : une application Android native de listes de tâches à effectuer qui utilise la bibliothèque d'authentification Active Directory pour l’authentification répartie.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) : application Xamarin.Android de listes de tâches à effectuer qui utilise la bibliothèque d'authentification Active Directory pour l’authentification répartie. Ce référentiel contient également l’application Xamarin.Forms.
- [Exemple d’application Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) : un exemple d’application « barebones ».

## <a name="week-of-may-27-2019"></a>Semaine du 27 mai 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Création de rapports pour les applications potentiellement dangereuses sur les appareils Android <!-- 4223162 -->
Intune fournit désormais des informations supplémentaires sur la création de rapports pour les applications potentiellement dangereuses sur les appareils Android. 

## <a name="week-of-may-20-2019"></a>Semaine du 20 mai 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="windows-company-portal-app----3316993---"></a>Application Portail d’entreprise Windows <!-- 3316993 -->
L’application Portail d’entreprise Windows a désormais une nouvelle page intitulée **Appareils**. La page **Appareils** montre aux utilisateurs finaux tous leurs appareils inscrits. Les utilisateurs voient cette modification dans le portail d’entreprise dès lors qu’ils utilisent la version 10.3.4291.0 et ultérieure. Pour plus d’informations sur la configuration du portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nom de l’attribut OrderID des appareils Autopilot changé en Balise de groupe <!-- 4659453 -->

Pour le rendre plus intuitif, le nom de l’attribut **OrderID** sur les appareils Autopilot est devenu **Balise de groupe**. Quand vous utilisez des fichiers CSV pour charger les informations des appareils Autopilot, vous devez utiliser Balise de groupe comme en-tête de colonne, et non plus OrderID.  

## <a name="week-of-may-13-2019"></a>Semaine du 13 mai 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise  <!-- 1927359  -->
Sur les appareils déjà inscrits via l’Assistant Configuration avec l’une des méthodes d’inscription des appareils d’entreprise d’Apple, Intune ne prendra plus en charge le Portail d’entreprise lorsqu’il est installé manuellement par les utilisateurs finaux à partir de l’App store. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. 

Par ailleurs, l’écran **Identifier votre appareil** du Portail d’entreprise iOS est en cours de suppression. Par conséquent, les administrateurs qui souhaitent activer l’accès conditionnel ou déployer des applications d’entreprise doivent mettre à jour le profil d’inscription DEP. Cette exigence s’applique uniquement si l’inscription DEP est authentifiée avec l’Assistant Configuration. Dans ce cas, vous devez envoyer le Portail d’entreprise sur l’appareil. Pour ce faire, choisissez **Intune** > **Inscription d’appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisir un jeton > **Profils** > choisir un profil > **Propriétés** > définir **Installer le Portail d’entreprise** sur **Oui**.

Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurer comment les utilisateurs finaux mettent à jour une application métier (LOB) à l’aide d’une stratégie de protection d’application <!-- 3568384 -->
Vous pouvez maintenant configurer où vos utilisateurs finaux peuvent obtenir une version mise à jour d’une application métier (LOB). Les utilisateurs finaux voient cette fonctionnalité dans la boîte de dialogue **Version de l’application min** du lancement conditionnel qui invite les utilisateurs finaux à mettre à jour vers une version minimale de l’application métier. Vous devez fournir ces détails de mise à jour dans le cadre de votre stratégie de protection des applications métier (APPLICATION). Cette fonctionnalité est disponible sur iOS et Android. Sur iOS, cette fonctionnalité nécessite que l’application soit intégrée (ou incluse dans un wrapper à l’aide de l’outil correspondant) dans le kit de développement logiciel (SDK) Intune pour iOS version 10.0.7 ou supérieure. Sur Android, cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise. Pour configurer la façon dont un utilisateur final met à jour une application métier, cette dernière a besoin d’une stratégie de configuration d’application managée reçue avec la clé, `com.microsoft.intune.myappstore`. La valeur envoyée définit à partir de quel magasin de l’utilisateur final doit télécharger l’application. Si l’application est déployée via le Portail d’entreprise, la valeur doit être `CompanyPortal`. Pour tous les autres magasins, vous devez entrer une URL complète.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Scripts PowerShell pour Intune Management Extension  <!-- 3734186  -->
Vous pouvez configurer des scripts PowerShell, qui s’exécuteront avec les privilèges Administrateur de l’utilisateur sur l’appareil. Pour en savoir plus, voir [Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune](../apps/intune-management-extension.md) et [Gestion de l’application Win32](../apps/app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Gestion d’applications Android Entreprise <!-- 4459905 -->
Pour aider les administrateurs informatiques à configurer et à utiliser les fonctions de gestion d’applications Android Entreprise, Intune ajoute automatiquement quatre applications liées à cette solution dans la console d’administration Intune. Ces quatre applications sont les suivantes :

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : cette application est utilisée pour les scénarios impliquant une instance Android Entreprise entièrement gérée.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ce logiciel vous aide à vous connecter à vos comptes lorsque vous utilisez la vérification à deux facteurs.
- **[Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : cette application est utilisée pour les scénarios impliquant des stratégies de protection des applications et des profils de travail Android Entreprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : cette fonctionnalité est utilisée pour les scénarios impliquant des kiosques/une instance Android Entreprise dédiée.

Auparavant, les administrateurs informatiques devaient manuellement rechercher et approuver ces applications dans le [store Google Play géré](https://play.google.com/store/apps) lors de la configuration. Cette modification supprime ces étapes manuelles, afin que la gestion de l’application Android Entreprise soit plus simple et plus rapide pour les clients.

Ces quatre fonctionnalités sont automatiquement ajoutées à la liste des applications Intune des administrateurs la première fois qu’ils connectent leur locataire Intune au store Google Play géré. Pour en savoir plus, voir [Connecter votre compte Intune à votre compte professionnel Android](../enrollment/connect-intune-android-enterprise.md). Pour les locataires qui ont déjà connecté leur locataire ou qui utilisent déjà Android Entreprise, les administrateurs n’ont pas besoin d’intervenir. Ces quatre applications s’afficheront automatiquement dans les 7 jours suivant la fin du lancement de service de mai 2019.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Mise à jour du connecteur de certificat PFX pour Microsoft Intune  <!-- 1533038 -->
Nous avons publié une mise à jour pour [PFX Certificate Connector pour Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) qui permet de résoudre le problème suivant : les certificats PFX existants sont continuellement retraités, ce qui entraîne l’arrêt du traitement des nouvelles demandes par le connecteur.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Tâches de sécurité Intune pour Defender ATP (en préversion publique)     <!-- 3208597 -->
Dans la préversion publique, vous pouvez utiliser Intune pour gérer les [tâches de sécurité pour Microsoft Defender Advanced Threat Protection (ATP)](../protect/atp-manage-vulnerabilities.md). Cette intégration dans ATP ajoute une approche basée sur les risques de la détection, de la hiérarchisation et des mauvaises configurations des points de terminaison tout en réduisant le délai entre la découverte et la correction.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10 <!-- 3617671   idstaged-->
De nombreux appareils Windows 10 et ultérieur ont des circuits microprogrammés Module de plateforme sécurisée (TPM). Cette mise à jour inclut un nouveau paramètre de conformité, qui vérifie la version de la puce TPM sur l’appareil. 

La section [Paramètres de stratégie de conformité de Windows 10 et ultérieur](../protect/compliance-policy-create-windows.md#device-security) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Empêcher les utilisateurs finaux de modifier leur point d’accès personnel et désactiver la journalisation de serveur Siri sur des appareils iOS <!-- 4097904   -->  
Vous pouvez créer un profil de restrictions pour un appareil iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres, que vous pouvez configurer :

- **Applications intégrées** : Journalisation côté serveur pour les commandes de Siri
- **Sans fil** : Modification par l’utilisateur du point d’accès personnel (mode supervisé uniquement)

Pour afficher ces paramètres, accédez à [Paramètres d’application intégrée pour iOS](../configuration/device-restrictions-ios.md#built-in-apps) et [Paramètres sans fil pour iOS](../configuration/device-restrictions-ios.md#wireless).

S’applique à : iOS 12.2 et plus

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nouveaux paramètres de restriction pour les applications de salle de classe sur les appareils macOS <!-- 4097905   --> 
Vous pouvez créer des profils de configuration pour les appareils macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut les nouveaux paramètres pour les applications de salle de classe, l’option de blocage des captures d’écran et l’option de désactivation de la solution iCloud Photo Library.

Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-macos.md).

S’applique à : macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Le paramètre du mot de passe iOS permettant d’accéder à l’App Store est renommé.<!-- 4557891  -->
Le paramètre **Mot de passe permettant d’accéder à l’App Store** est renommé pour **Demander le mot de passe iTunes Store pour tous les achats** (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour plateforme > **Restrictions d’appareil** pour type de profil > **App Store, affichage de documents et jeux**).

Pour afficher les paramètres disponibles, accédez aux [paramètres iOS App Store, affichage de documents et jeux](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

S’applique à : iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Base de référence de Microsoft Defender Advanced Threat Protection (préversion)  <!--  3754134 -->
Nous avons ajouté une préversion de base de référence de la sécurité pour les paramètres [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md). Cette ligne de base est disponible lorsque votre environnement répond à la configuration requise pour l’utilisation de [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Une page d’état de l’inscription Windows (ESP) est désormais disponible <!-- 3605348 -->
La Page d’état d’inscription n’est désormais plus une préversion. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Mise à jour de l’interface utilisateur Intune : création d’un profil d'inscription Autopilot  <!-- 4593669 -->
L’interface utilisateur pour la création d’un profil d’inscription Autopilot a été mise à jour pour s’aligner sur les styles d’interface utilisateur d’Azure. Pour en savoir plus, voir [Créer un profil d’inscription Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). À l’avenir, des scénarios supplémentaires Intune seront actualisés conformément à ce nouveau style d’interface utilisateur.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Activer la réinitialisation d’Autopilot pour tous les appareils Windows <!-- 4225665 -->
La réinitialisation d’Autopilot fonctionne maintenant pour tous les appareils Windows, y compris ceux qui ne sont pas configurés pour utiliser la page d’état d’inscription. Si une page d’état d’inscription n’a pas été configurée pour l’appareil lors de son inscription initiale, l’appareil passera directement au bureau après la connexion. La synchronisation et l’affichage conforme dans Intune peuvent prendre jusqu’à huit heures. Pour plus d’informations, consultez [Réinitialiser les appareils par réinitialisation à distance de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Format IMEI exact non requis lors de la recherche dans Tous les appareils <!--30407680 -->
Vous n’aurez pas à inclure d’espaces dans les chiffres IMEI pour effectuer une recherche dans **Tous les appareils**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Application sur le portail Intune de la suppression d’un appareil sur le portail Apple <!--2489996 -->
Si un appareil est supprimé sur le portail du Programme d’inscription des appareils ou sur le portail Apple Business Manager, cette suppression est automatiquement appliquée à Intune lors de la synchronisation suivante.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>La Page d’état d’inscription effectue maintenant le suivi des applications Win32 <!-- 2714451 -->
Cela s’applique uniquement aux appareils exécutant Windows 10 version 1903 et versions ultérieures. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Gestion des appareils

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Réinitialiser et effacer en bloc le contenu des appareils à l’aide de l’API Graph <!-- 3295288 -->
L’API Graph permet désormais de réinitialiser et d’effacer le contenu d’un maximum de 100 appareils à la fois.


### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Le rapport de chiffrement ne fait pas partie de la préversion publique   <!-- 4587546      -->
Le [rapport pour le chiffrement de lecteur BitLocker et d’appareil](../protect/encryption-monitor.md) est maintenant généralement disponible et ne fait plus partie de la préversion publique. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Signature Outlook et paramètres biométriques pour les appareils iOS et Android <!-- 4050557 -->
Vous pouvez maintenant spécifier si la signature par défaut est activée dans Outlook sur les appareils iOS et Android. De plus, vous pouvez choisir d’autoriser les utilisateurs à modifier le paramètre biométrique dans Outlook sur iOS.

## <a name="week-of-may-6-2019"></a>Semaine du 6 mai 2019 

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Prise en charge du contrôle d’accès réseau (NAC) pour l’accès F5 sur les appareils iOS <!-- 4500808 -->

F5 a publié une mise à jour vers BIG-IP 13 qui autorise la fonctionnalité NAC pour l’accès F5 sur iOS dans Intune. Pour utiliser cette fonctionnalité :

- Effectuez une mise à jour de BIG-IP avec la version 13.1.1.5 actualisée. BIG-IP 14 n’est pas pris en charge.
- Intégrez BIG-IP avec Intune pour le contrôle d’accès réseau. Étapes dans [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Cochez le paramètre **Activer le contrôle d'accès réseau (NAC)** dans le profil VPN dans Intune.

Pour voir le paramètre disponible, accédez à [Configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md).

S’applique à : iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Mise à jour du connecteur de certificat PFX pour Microsoft Intune <!-- doc-vso 1521237  -->  
Nous avons publié une mise à jour pour le [connecteur de certificat PFX pour Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) qui baisse l’intervalle d’interrogation de 5 minutes à 30 secondes.

## <a name="week-of-april-22-2019"></a>Semaine du 22 avril 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Utiliser le Gestionnaire de conformité pour créer des évaluations pour Microsoft Intune<!-- 4404750 -->

Le [Gestionnaire de conformité](https://servicetrust.microsoft.com/ComplianceManager) (qui ouvre un autre site Microsoft) est un outil d’évaluation des risques basés sur les workflows dans le portail Microsoft Service Trust. Il vous permet de suivre, d’attribuer et de vérifier les activités de conformité aux normes de votre organisation liées aux services Microsoft. Vous pouvez créer votre propre évaluation de conformité avec Office 365, Azure, Dynamics, les Services professionnels et Intune. Deux évaluations sont disponibles dans Intune : FFIEC et RGPD.

Le Gestionnaire de conformité vous permet de faire converger vos efforts en décomposant les contrôles : les contrôles gérés par Microsoft et les contrôles gérés par votre organisation. Vous pouvez effectuer les évaluations, puis les exporter et les imprimer.

La conformité au [FFIEC (Federal Financial Institutions examen Conseil)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (qui ouvre un autre site Microsoft) est un ensemble de normes applicables aux opérations bancaires en ligne émises par le FFIEC. Il s’agit de l’évaluation la plus demandée pour les établissements financiers qui utilisent Intune. Elle interprète la façon dont Intune aide à satisfaire les exigences de cybersécurité liées aux workloads dans le cloud public. L’évaluation FFIEC d’Intune est la deuxième évaluation FFIEC dans le Gestionnaire de conformité.

Dans l’exemple suivant, vous pouvez voir la répartition des contrôles FFIEC. Microsoft traite 64 contrôles. Vous êtes chargé des 12 autres contrôles.

![Consultez un exemple d’évaluation Intune pour le FFIEC, notamment les actions du client et les actions de Microsoft](./media/whats-new/intune-ffiec-assessment-status.png)

Le [Règlement général sur la protection des données (RGPD)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (qui ouvre un autre site Microsoft) est une loi de l’Union européenne (UE) qui permet de protéger les droits des individus et leurs données. Le RGPD est l’évaluation la plus demandée pour permettre de se conformer aux réglementations sur la protection des données personnelles. 

Dans l’exemple suivant, vous voyez la répartition des contrôles RGPD. Microsoft traite 49 contrôles. Vous êtes chargé des 66 autres contrôles.

![Consultez un exemple d’évaluation Intune pour le RGPD, notamment les actions du client et les actions de Microsoft](./media/whats-new/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Semaine du 15 avril 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Chiffrement OpenSSL pour les stratégies de protection des applications Android <!-- 3747362 -->
Les stratégies de protection des applications Intune sur les appareils Android utilise désormais une bibliothèque de chiffrement OpenSSL qui est conforme à la norme FIPS 140-2. Pour plus d’informations, consultez la section [Chiffrement](../apps/app-protection-policy-settings-android.md#encryption) de [Paramètres de la stratégie de protection des applications Android dans Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Activer les dépendances d’application Win32 <!-- 2617348  -->
En qualité d’administrateur, vous pouvez exiger que les autres applications soient installées en tant que dépendances avant d’installer votre application Win32. Plus précisément, l’appareil doit installer la ou les applications dépendantes avant d’installer l’application Win32. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Sélectionnez **Application Windows (Win32)** comme **Type d’application**. Après avoir ajouté l’application, vous pouvez sélectionner **Dépendances** pour ajouter l’application dépendante qui doit être installée avant que l’application Win32 puisse être installée. Pour plus d’informations, consultez [Intune autonome - Gestion des applications Win32](./../apps/app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Informations sur l’installation de versions d’application pour les applications Microsoft Store pour Entreprises <!-- 3537391   -->
Les rapports d’installation des applications incluent des informations sur les versions d’application concernant Microsoft Store pour les applications métier. Dans Intune, sélectionnez **Applications clientes** > **Applications**. Sélectionnez une **Application du Microsoft Store pour Entreprises** , puis **État de l’installation de l’appareil** sous la section **Superviser**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Ajouts apportés aux règles de spécification des applications Win32 <!-- 3676883   -->
Vous pouvez créer des règles de spécification basées sur des scripts PowerShell, des valeurs de Registre et des informations sur le système de fichiers. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Application Windows (Win32)** comme **Type d’application** dans le panneau **Ajouter une application**.  Sélectionnez **Spécifications** > **Ajouter** pour configurer des règles de spécification supplémentaires. Ensuite, sélectionnez **Type de fichier**, **Registre** ou **Script** comme **Type de spécification**. Pour plus d’informations, consultez [Gestion des applications Win32](./../apps/app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune <!-- 3695227  -->
Vous pouvez attribuer vos applications Win32 à installer sur des appareils joints à Azure AD et inscrits auprès d’Intune. Pour plus d’informations sur les applications Win32 dans Intune, consultez [Gestion des applications Win32](./../apps/app-management.md).

#### <a name="device-overview-shows-primary-user---3794259----"></a>La vue d’ensemble de l’appareil indique l’utilisateur principal <!--3794259  -->
La page de vue d’ensemble de l’appareil indique l’utilisateur principal, également appelé utilisateur d’UDA (affinité entre appareil et utilisateur). Pour voir l’utilisateur principal d’un appareil, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil. L’utilisateur principal apparaît en haut de la page **Vue d’ensemble**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Création de rapports d’applications Google Play gérées supplémentaires pour les appareils avec profil professionnel Android Entreprise <!-- 4105925  -->
Pour les applications Google Play gérées qui sont déployées sur des appareils avec profil professionnel Android Entreprise, vous pouvez afficher le numéro de version spécifique de l’application installée sur un appareil. Cela concerne uniquement les applications obligatoires.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Claviers tiers iOS <!-- 4111843   -->
La prise en charge de la stratégie de protection des applications Intune pour le paramètre **Claviers tiers** pour iOS n’existe plus en raison d’un changement de plateforme iOS. Vous ne pouvez plus configurer ce paramètre dans la console d’administration Intune, ni l’appliquer sur le client dans le kit SDK de l’application Intune.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Définir les paramètres de connexion et contrôler les options de redémarrage sur les appareils macOS <!-- 1210083  -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de fenêtre de connexion, comme l’affichage d’une bannière personnalisée, le choix de la façon dont les utilisateurs se connectent, l’affichage ou le masquage des paramètres d’alimentation, et plus encore.

Pour afficher ces paramètres, accédez à [Paramètres des fonctionnalités d’appareil macOS](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurer le Wi-Fi sur les appareils dédiés des propriétaires d’appareils Android Entreprise s’exécutant en mode kiosque multi-application <!--3041940  -->
Vous pouvez activer des paramètres sur un propriétaire d’appareil Android Entreprise en cas d’exécution en tant qu’appareil dédié en mode kiosque multi-application. Dans cette mise à jour, vous pouvez permettre aux utilisateurs de configurer des réseaux Wi-Fi et à s’y connecter (**Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions sur l’appareil** pour le type de profil >  **Appareils dédiés** > **Mode kiosque** : **Multi-application** > **Configuration Wi-Fi**). 

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md).

S’applique à : Appareils dédiés Android Entreprise s’exécutant en mode kiosque multi-application


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurer le Bluetooth et l’appairage sur les appareils dédiés des propriétaires d’appareils Android Entreprise s’exécutant en mode kiosque multi-application <!-- 3041941  -->
Vous pouvez activer des paramètres sur un propriétaire d’appareil Android Entreprise en cas d’exécution en tant qu’appareil dédié en mode kiosque multi-application. Dans cette mise à jour, vous pouvez autoriser les utilisateurs finaux à activer le Bluetooth et à appairer les appareils en Bluetooth (**Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement, Restrictions sur l’appareil** pour le type de profil >  **Appareils dédiés** > **Mode kiosque** : **Multi-application** > **Configuration Bluetooth**). 

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md).

S’applique à : Appareils dédiés Android Entreprise s’exécutant en mode kiosque multi-application

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Créer et utiliser des profils de configuration d’appareils OEMConfig dans Intune <!-- 3305883  -->
Dans cette mise à jour, Intune prend en charge la configuration des appareils Android Entreprise avec OEMConfig. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres à des appareils Android Entreprise à l’aide d’OEMConfig (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme).

La prise en charge des fabricants OEM s’effectue actuellement par OEM. Si une application OEMConfig que vous voulez n’est pas disponible dans la liste des applications OEMConfig, contactez `IntuneOEMConfig@microsoft.com`.

Pour en savoir plus sur cette fonctionnalité, accédez à [Utiliser et gérer des appareils Android Entreprise avec OEMConfig dans Microsoft Intune](../configuration/android-oem-configuration-overview.md).

S’applique à : Android Entreprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notifications Windows Update  <!-- 3316758, 3316782  -->
Nous avons ajouté deux *paramètres d’expérience utilisateur* aux configurations des anneaux de mise à jour Windows que vous pouvez gérer à partir de la console Intune. Vous pouvez désormais :
- Bloquer ou autoriser des utilisateurs à [rechercher des mises à jour Windows](../protect/windows-update-settings.md).
- Gérer le [niveau de notification Windows Update](../protect/windows-update-settings.md) que voient les utilisateurs.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nouveaux paramètres de restriction d’appareil pour les propriétaires d’appareils Android Entreprise <!-- 3574254  -->
Sur les appareils Android Entreprise, vous pouvez créer un profil de restriction d’appareil pour autoriser ou restreindre les fonctionnalités, définir des règles de mot de passe, et plus encore (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil uniquement > Restrictions sur l’appareil** pour le type de profil). 

Cette mise à jour inclut de nouveaux paramètres de mot de passe et permet un accès complet aux applications dans Google Play Store pour les appareils complètement gérés, entre autres. Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md). 

S’applique à : Appareils Android Entreprise complètement gérés

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10 <!-- 3617671 -->

Cette fonctionnalité a été différée et devrait être publiée ultérieurement.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Mise à jour des changements apportés à l’interface utilisateur pour le navigateur Microsoft Edge sur les appareils Windows 10 et versions ultérieures <!-- 3775833   -->
Quand vous créez un profil de configuration d’appareil, vous pouvez autoriser ou limiter les fonctionnalités Microsoft Edge sur les appareils Windows 10 et les versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** sur la plateforme > **restrictions d’appareil** pour le type de profil > **Navigateur Microsoft Edge**). Dans cette mise à jour, les paramètres Microsoft Edge sont plus descriptifs et plus faciles à comprendre. 

Pour voir ces fonctionnalités, accédez à [Paramètres de restriction d’appareil pour le navigateur Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

S’applique à : Windows 10 et versions ultérieures

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Prise en charge étendue des appareils Android Entreprise complètement gérés (préversion)  <!--   3903241, 3903244, 3903246   -->
Toujours dans la préversion publique, nous avons développé notre prise en charge des appareils Android Entreprise complètement gérés ([annoncée en janvier 2019](whats-new.md#week-of-january-14-2019) pour inclure les éléments suivants : 

- Sur les appareils dédiés et complètement gérés, vous pouvez créer des [stratégies de conformité](../protect/compliance-policy-create-android-for-work.md) pour inclure des règles de mot de passe et une configuration requise pour le système d’exploitation (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil** pour le type de profil). 

  Sur les appareils dédiés, l’appareil peut s’afficher comme étant **Non conforme**. L’accès conditionnel n’est pas disponible sur les appareils dédiés. Veillez à effectuer toutes les tâches ou actions pour obtenir des appareils dédiés conformes à vos stratégies attribuées.

- [Accès conditionnel](../protect/conditional-access.md) : les stratégies d’accès conditionnel qui s’appliquent à Android s’appliquent également aux appareils Android Entreprise complètement gérés. Les utilisateurs peuvent désormais inscrire leur appareil complètement géré dans Azure Active Directory à l’aide de l’**application Microsoft Intune**. Ensuite, recherchez et résolvez tous les problèmes de conformité pour accéder aux ressources de l’organisation.

- Nouvelle application utilisateur final (application Microsoft Intune) : il existe une nouvelle application utilisateur final pour les appareils Android complètement managés, appelée **Microsoft Intune**. Cette nouvelle application est légère et moderne, et offre des fonctionnalités similaires à celles de l’application Portail d’entreprise, mais pour les appareils complètement gérés. Pour plus d’informations, consultez [Application Microsoft Intune sur Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Pour configurer des appareils Android complètement managés, accédez à **Inscription des appareils** > **Inscription Android** > **Appareils des utilisateurs complètement managés appartenant à l’entreprise**. La prise en charge des appareils Android complètement gérés reste en préversion et certaines fonctionnalités Intune peuvent ne pas être entièrement opérationnelles.  

Pour en savoir plus sur cette préversion, consultez notre blog [Microsoft Intune - Preview 2 pour les appareils Android complètement gérés](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configurer le profil pour ignorer certains écrans lors de l’exécution de l’Assistant Configuration <!-- 2276470  -->
Lors de la création d’un profil d’inscription macOS, vous pouvez le configurer pour ignorer les écrans suivants quand un utilisateur exécute l’Assistant Configuration :
- Apparence
- Display Tone (Indiquer la tonalité)
- iCloudStorage : si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple.  Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.
Pour plus d’informations, consultez [Inscrire automatiquement des appareils macOS avec le Programme d’inscription des appareils ou Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Nommage d’appareils en bloc lors de l’inscription d’appareils iOS d’entreprise<!--3566569  -->
Quand vous utilisez l’une des méthodes d’inscription d’entreprise d’Apple (DEP/ABM/ASM), vous pouvez définir un format de nom d’appareil pour nommer automatiquement les appareils iOS entrants. Vous pouvez spécifier un format qui inclut le type d’appareil et le numéro de série dans votre modèle. Pour ce faire, choisissez **Intune** > **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription** > **Sélectionner un jeton** >**Créer un profil** > **Format de nommage d’appareil**. Vous pouvez modifier des profils existants, mais le nom sera appliqué uniquement aux appareils récemment synchronisés.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Mise à jour du message d’expiration par défaut dans la page d’état d’inscription <!-- 3959331 -->
Nous avons mis à jour le message d’expiration par défaut que les utilisateurs voient quand la page d’état d’inscription (ESP) dépasse la valeur de délai spécifiée dans le profil ESP. Le nouveau message par défaut est ce que les utilisateurs voient et ce qui les aide à comprendre les actions suivantes à entreprendre avec leur déploiement ESP.  

### <a name="device-management"></a>Gestion des appareils

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Mettre hors service les appareils non conformes  <!-- 1827291   -->
Cette fonctionnalité a été différée et devrait être publiée ultérieurement.


### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Changements de l’entrepôt de données Intune V1.0 se reflétant vers la version bêta <!-- 4403765 -->
Quand la version V1.0 a été introduite dans 1808, elle comportait certaines différences significatives par rapport à la version bêta de l’API. Dans 1903, ces changements seront reflétés dans la version bêta de l’API. Si vous avez des rapports importants qui utilisent la version bêta de l’API, nous vous recommandons vivement de passer ces rapports en version V1.0 afin d’éviter les changements cassants. Pour plus d’informations, consultez [Journal des changements pour l’API de l’entrepôt de données Intune](../developer/reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Superviser l’état de la base de référence de sécurité (préversion publique) <!-- 3082047 --> 
Nous avons ajouté une [vue par catégorie](../protect/security-baselines-monitor.md#per-category-view) pour la supervision des bases de référence de sécurité. (Les bases de référence de sécurité restent en préversion). La vue par catégorie affiche chaque catégorie de la base de référence, ainsi que le pourcentage d’appareils appartenant à chaque groupe d’état pour cette catégorie. Vous pouvez maintenant voir combien d’appareils ne correspondent pas aux catégories individuelles, sont mal configurés ou ne sont pas applicables.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Balises d’étendue pour les jetons VPP Apple <!--2371886  -->
Vous pouvez maintenant ajouter des balises d’étendue à des jetons VPP Apple. Seuls les utilisateurs attribués avec la même balise d’étendue ont accès au jeton VPP Apple ayant cette balise. Les applications et livres électroniques VPP achetés avec ce jeton héritent de ses balises d’étendue. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Semaine du 1 avril 2019

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Mise à jour des connecteurs de certificat  <!-- ICM 113304612 -->
Nous avons publié des mises à jour à la fois pour le [connecteur de certificat Intune et le connecteur de certificat PFX](../protect/certficates-pfx-configure.md#whats-new-for-connectors). Les nouvelles versions résolvent plusieurs problèmes connus.  

### <a name="app-management"></a>Gestion d'applications

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Mise à jour de l’expérience utilisateur de l’application Portail d’entreprise pour iOS <!-- 2536024 -->
La page d’accueil de l’application Portail d’entreprise pour les appareils iOS a été repensée. Désormais, elle adhère davantage aux modèles d’interface utilisateur iOS, et fournit également une meilleure détectabilité des applications et des livres électroniques.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Changements apportés à l’inscription sur le portail d’entreprise pour les utilisateurs d’appareils iOS 12 <!--3448635 -->  
Les étapes et les écrans d’inscription iOS sur le portail d’entreprise ont été mis à jour afin de s’aligner avec les changements de l’inscription MDM publiés dans Apple iOS 12.2. Le workflow mis à jour invite les utilisateurs à effectuer les opérations suivantes :  

* Autoriser Safari à ouvrir le site web Portail d’entreprise et à télécharger le profil de gestion avant de retourner à l’application Portail d’entreprise.  
* Ouvrir l’application Paramètres pour installer le profil de gestion sur leur appareil.
* Retourner à l’application Portail d’entreprise pour terminer l’inscription.  

Pour connaître les étapes et les écrans d’inscription mis à jour, consultez [Inscrire un appareil iOS dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Semaine du 25 mars 2019

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Prise en charge de l’application Conformité de Power BI à partir du panneau Entrepôt de données dans Microsoft Intune <!-- 4260871 -->
Auparavant, le lien **Télécharger le fichier Power BI** dans le panneau **Entrepôt de données Intune** téléchargeait un rapport de l’entrepôt de données Intune (fichier .pbix). Ce rapport a été remplacé par l’application Conformité de Power BI. L’application Conformité de Power BI ne nécessite pas de chargement ou de configuration spéciaux. Elle s’ouvrira directement dans le portail en ligne Power BI et affichera des données spécifiquement pour votre locataire Intune en fonction de vos informations d’identification. Dans Intune, sélectionnez le lien **Configurer l’entrepôt de données Intune** à droite du panneau Intune. Cliquez ensuite sur **Obtenir l’application Power BI**. Pour plus d’informations, consultez [Se connecter à l’entrepôt de données avec Power BI](../developer/reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Semaine du 18 mars 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Déployer Microsoft Visio et Microsoft Project <!-- 3725386  -->
Vous pouvez désormais déployer Microsoft Visio Pro pour Office 365 et le client de bureau Microsoft Project Online en tant qu’applications indépendantes pour les appareils Windows 10 à l’aide de Microsoft Intune, si vous possédez des licences pour ces applications. À partir d’Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter** pour afficher le panneau **Ajouter une application**. Dans le panneau **Ajouter une application**, sélectionnez **Windows 10** comme **Type d’application**. Sélectionnez ensuite **Configurer la suite d’applications** pour sélectionner les applications à installer. Pour plus d’informations sur les applications Office 365 pour des appareils Windows 10, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Changement de nom du produit Microsoft Visio Pro pour Office 365 <!-- 3593653  -->
**Microsoft Visio Pro pour Office 365** s’appellera désormais **Microsoft Visio Online - Plan 2**.  Pour plus d’informations sur Microsoft Visio, consultez [Visio Online - Plan 2](https://products.office.com/visio/visio-online-plan-2). Pour plus d’informations sur les applications Office 365 pour des appareils Windows 10, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Paramètre de limite de caractères d’une stratégie de protection d’application Intune <!-- 3291302  -->
Les administrateurs Intune peuvent spécifier une exception au paramètre de stratégie **Restreindre les opérations Couper, Copier et Coller avec d’autres applications** de la stratégie de protection d’application Intune.  En tant qu’administrateur, vous pouvez spécifier le nombre de caractères qui peuvent être coupés ou copiés à partir d’une application gérée. Ce paramètre permet de partager le nombre spécifié de caractères avec toute application, quelle que soit la valeur du paramètre « Restreindre les opérations Couper, Copier et Coller avec d’autres applications ». Notez que la version de l’application Portail d’entreprise Intune pour Android exige la version 5.0.4364.0 ou une version ultérieure. Pour plus d’informations, consultez [Protection des données iOS](../apps/app-protection-policy-settings-ios.md#data-protection), [Protection des données Android](../apps/app-protection-policy-settings-android.md#data-protection) et [Consulter les journaux de la protection des applications clientes](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Code XML de l’outil Déploiement d’Office (ODT) pour le déploiement d’Office ProPlus <!-- 3192477   -->
Vous pourrez fournir le code XML de l’outil Déploiement d’Office (ODT) lors de la création d’une instance d’Office ProPlus dans la console d’administration Intune. Cela offre davantage de possibilités de personnalisation si les options existantes de l’interface utilisateur Intune ne répondent pas à vos besoins. Pour plus d’informations, consultez [Attribuer des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune](../apps/apps-add-office365.md) et [Options de configuration pour l’outil Déploiement d’Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Les icônes d’application s’affichent désormais avec un arrière-plan généré automatiquement <!-- 1429026  -->
Dans l’application Portail d’entreprise Windows, des icônes d’application s’afficheront désormais avec un arrière-plan généré automatiquement en fonction de la couleur dominante de l’icône (si elle peut être détectée). S’il y a lieu, cet arrière-plan remplacera la bordure grise qui était précédemment visible sur les vignettes d’application. Les utilisateurs verront ce changement dans les versions du portail d’entreprise ultérieures à 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installer des applications disponibles à l’aide de l’application Portail d’entreprise après l’inscription en bloc de Windows <!-- 2751523   -->
Les appareils Windows inscrits auprès d’Intune à l’aide de l’[inscription en bloc de Windows](../enrollment/windows-bulk-enroll.md) (packages de provisionnement) pourront utiliser l’application Portail d’entreprise pour installer des applications disponibles. Pour plus d’informations sur l’application Portail d’entreprise, consultez [Ajouter manuellement l’application Portail d’entreprise Windows 10](../apps/store-apps-company-portal-app.md) et [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>L’application Microsoft Teams peut être sélectionnée comme faisant partie de la suite d’applications Office <!-- 3828932  -->
L’application Microsoft Teams peut être incluse ou exclue dans l’installation de la suite d’applications Office ProPlus. Cette fonctionnalité fonctionne pour le numéro de build 16.0.11328.20116+ d’Office ProPlus. L’utilisateur doit se déconnecter puis se connecter à l’appareil pour terminer l’installation. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez l’un des types d’application de la **Suite Office 365**, puis sélectionnez **Configurer la suite d’applications**.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Démarrer automatiquement une application quand vous exécutez plusieurs applications en mode kiosque sur les appareils Windows 10 et les versions ultérieures <!-- 2351390 -->

Sur Windows 10 et les versions ultérieures, vous pouvez exécuter un appareil en mode kiosque et exécuter de nombreuses applications. Cette mise à jour comprend un paramètre **Démarrage automatique** (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil > **Kiosque multi-application**). Utilisez ce paramètre pour démarrer automatiquement une application quand l’utilisateur se connecte à l’appareil.

Pour obtenir la liste et la description de tous les paramètres kiosque, consultez [Paramètres d’appareil Windows 10 et versions ultérieures pour une exécution en tant que kiosque dans Intune](../configuration/kiosk-settings-windows.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Les journaux des opérations donnent également des détails sur les appareils non conformes <!-- 4063755  -->
Lors du routage de journaux Intune vers des fonctionnalités de supervision Azure, vous pouvez également router les journaux des opérations. Dans cette mise à jour, les journaux des opérations fournissent également des informations sur les appareils non conformes. 

Pour plus d’informations sur cette fonctionnalité, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Router des journaux vers Azure Monitor dans un plus grand nombre de workloads Intune <!-- 3804627 -->
Dans Intune, vous pouvez router des journaux d’audit et des journaux des opérations vers des hubs d’événements, du stockage et de l’analytique des journaux d’activité dans Azure Monitor (**Intune** > **Supervision** > **Paramètres de diagnostic**). Dans cette mise à jour, vous pouvez router ces journaux dans un plus grand nombre de workloads Intune, notamment la conformité, les configurations, les applications clientes, entre autres. 

Pour en savoir plus sur le routage de journaux vers Azure Monitor, consultez [Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics](../review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Créer et utiliser Mobility Extensions sur les appareils Android Zebra dans Intune <!-- 3305880   -->
Dans cette mise à jour, Intune prend en charge la configuration des appareils Android Zebra. Plus précisément, vous pouvez créer un profil de configuration d’appareil et appliquer des paramètres aux appareils Android Zebra à l’aide de profils Mobility Extensions (MX) générés par StageNow (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android** pour la plateforme > **Profil MX (Zebra uniquement)** pour le type de profil).

Pour plus d’informations sur cette fonctionnalité, consultez [Utiliser et gérer des appareils Zebra avec des extensions de mobilité dans Intune](../configuration/android-zebra-mx-overview.md).

S’applique à : Android

### <a name="device-management"></a>Gestion des appareils

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Rapport de chiffrement pour les appareils Windows 10 (en préversion publique)<!-- 2351538 -->  
Utilisez le nouveau [rapport de chiffrement (préversion)](../protect/encryption-monitor.md) pour voir des détails sur l’état de chiffrement de vos appareils Windows 10. Les détails disponibles incluent la version TPM d’un appareil, la préparation et l’état du chiffrement, la création de rapports d’erreurs, et plus encore.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Accéder aux clés de récupération BitLocker à partir du portail Intune (en préversion publique) <!-- 2351547   -->  
Vous pouvez désormais utiliser Intune pour [afficher des détails](../protect/encryption-monitor.md) sur l’ID de clé BitLocker et les clés de récupération BitLocker à partir d’Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Prise en charge de Microsoft Edge pour des scénarios Intune sur des appareils iOS et Android <!-- 3411007 -->
Microsoft Edge prendra en charge les mêmes scénarios de gestion qu’Intune Managed Browser avec, en plus, des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise de Microsoft Edge qui sont activées par des stratégies Intune incluent la double identité, l’intégration de stratégies de protection des applications, l’intégration de proxy d’application Azure, ainsi que les raccourcis de page d’accueil et les favoris gérés. Pour plus d’informations, consultez [Prise en charge de Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Le connecteur Exchange Online/Intune cessera de prendre en charge les appareils uniquement EAS <!--3105122  -->
La console Intune ne prend plus en charge l’affichage et la gestion des appareils uniquement EAS connectés à Exchange Online avec le connecteur Intune. À la place, vous disposez des options suivantes :
- inscrire les appareils auprès de la gestion des appareils mobiles (MDM) ;
- utiliser des stratégies Intune App Protection pour gérer vos appareils ;
- utiliser les contrôles Exchange comme indiqué dans [Appareils clients et mobiles dans Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online).

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Rechercher un appareil précis dans la page Tous les appareils à l’aide de [nom] <!--4254930 -->
Vous pouvez désormais rechercher un nom de d’appareil exact. Accédez à **Intune** > **Appareils** > **Tous les appareils** > dans la zone de recherche, placez le nom de l’appareil entre {} pour rechercher un correspondance exacte. Par exemple, **{Appareil12345}** .

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Prise en charge de connecteurs supplémentaires dans la page État du locataire <!-- 3617202  -->
La [page État du locataire](../tenant-status.md) affiche maintenant des informations sur l’état des connecteurs supplémentaires, notamment *Windows Defender - Protection avancée contre les menaces* (ATP) et d’autres connecteurs Mobile Threat Defense.

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Octroi d’un accès en lecture seule Intune à certains rôles Azure Active Directory <!-- 3637917  -->
L’accès en lecture seule Intune a été octroyé aux rôles Azure AD suivants. Les autorisations accordées avec les rôles Azure AD remplacent les autorisations accordées avec le contrôle d’accès en fonction du rôle (RBAC) Intune.

Accès en lecture seule aux données d’audit Intune :

- Administrateur de conformité
- Administrateur des données de conformité

Accès en lecture seule à toutes les données Intune :

- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur Sécurité

Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Balises d’étendue pour les profils de provisionnement d’applications iOS <!--2934430   -->
Vous pouvez ajouter une balise d’étendue à un profil de provisionnement d’application iOS afin que seules les personnes avec des rôles auxquels cette balise d’étendue a également été attribuée aient accès au profil de provisionnement d’application iOS. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Balises d’étendue pour les stratégies de configuration des applications <!--2371891   -->
Vous pouvez ajouter une balise d’étendue à une stratégie de configuration des applications afin que seules les personnes avec des rôles auxquels cette balise d’étendue a également été attribuée aient accès à la stratégie de configuration des applications. La stratégie de configuration des applications peut uniquement cibler des applications auxquelles la même balise d’étendue a été attribuée ou être associée à ces applications. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Prise en charge de Microsoft Edge pour des scénarios Intune sur des appareils iOS et Android <!-- 3411007 -->
Microsoft Edge prendra en charge les mêmes scénarios de gestion qu’Intune Managed Browser avec, en plus, des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise de Microsoft Edge qui sont activées par des stratégies Intune incluent la double identité, l’intégration de stratégies de protection des applications, l’intégration de proxy d’application Azure, ainsi que les raccourcis de page d’accueil et les favoris gérés. Pour plus d’informations, consultez [Prise en charge de Microsoft Edge](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Semaine du 25 février 2019

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="intune-powershell-module----951068----"></a>Module PowerShell Intune <!-- 951068  -->
Le nouveau module PowerShell Intune, qui offre une prise en charge de l’API Intune par le biais de Microsoft Graph, est désormais disponible dans [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Informations sur la façon d’utiliser ce module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Exemples de scénarios utilisant ce module](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Prise en charge améliorée de l’optimisation de la distribution  <!--3183757  -->
Nous avons étendu la prise en charge de la configuration de l’optimisation de la distribution dans Intune. Vous pouvez désormais configurer une liste développée de [paramètres d’optimisation de la distribution](../configuration/delivery-optimization-settings.md) et la cibler sur vos appareils directement à partir de la console Intune.


## <a name="week-of-february-18-2019"></a>Semaine du 18 février 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune exploitera les API Google Play Protect sur les appareils Android <!-- 2577355   -->
Certains administrateurs informatiques sont confrontés à un « paysage » BYOD où les téléphones mobiles des utilisateurs finaux peuvent être rootés ou jailbreakés. Ce comportement, bien que n’étant parfois pas mal intentionné, entraîne un contournement de nombreuses stratégies Intune définies pour protéger les données de l’organisation sur les appareils des utilisateurs finaux. Par conséquent, Intune permet donc la détection du rootage et du jailbreaking pour les appareils inscrits et désinscrits. Avec cette version, Intune peut désormais tirer parti des API Google Play Protect, qui s’ajoutent à nos contrôles de détection du rootage pour les appareils non inscrits. Même si Google ne partage pas l’intégralité des contrôles de détection du rootage qui sont effectués, nous pensons que ces API vont détecter les utilisateurs qui ont rooté leurs appareils pour une raison quelconque, allant de la personnalisation de l’appareil à l’obtention de mises à jour plus récentes du système d’exploitation sur des appareils plus anciens. L’accès de ces utilisateurs aux données de l’entreprise peut alors être bloqué, ou leurs comptes professionnels peuvent être supprimés des applications pour lesquelles une stratégie est activée. L’administrateur informatique dispose désormais de plusieurs mises à jour d’amélioration des rapports dans le panneau Intune App Protection : le rapport « Utilisateurs avec indicateur » montre les utilisateurs qui sont détectés via l’analyse de l’API SafetyNet de Google Play Protect, et le rapport « Applications potentiellement dangereuses » montre les applications qui sont détectées via l’analyse de l’API Verify Apps de Google. Cette fonctionnalité est disponible sur Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informations sur les applications Win32 disponibles dans le panneau Résolution des problèmes <!-- 2617342   -->
Vous pouvez désormais collecter des fichiers journaux des échecs pour l’installation d’une application Win32 à partir du panneau **Résolution des problèmes** des applications Intune. Pour plus d’informations sur la résolution des problèmes liés à l’installation d’une application, consultez [Résoudre les problèmes d’installation d’applications](./../apps/troubleshoot-app-install.md) et [Résoudre les problèmes d’application Win32](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Détails de l’état des applications pour les applications iOS <!-- 3761235   -->
Des nouveaux messages d’erreur d’installation d’une application ont été ajoutés et concernent les échecs suivants :
- Échec pour les applications VPP lors de l’installation sur un iPad partagé
- Échec quand l’App Store est désactivé
- Échec de la recherche d’une licence VPP pour l’application
- Échec de l’installation d’applications système avec le fournisseur MDM
- Échec de l’installation d’applications quand l’appareil est en mode perdu ou en mode kiosque
- Échec de l’installation d’applications quand l’utilisateur n’est pas connecté à l’App Store

Dans Intune, sélectionnez **Applications clientes** > **Applications** > « Nom de l’application » > **État de l’installation de l’appareil**. Les nouveaux messages d’erreur sont disponibles dans la colonne **Détails du statut**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nouvel écran Catégories d’application dans l’application Portail d’entreprise pour Windows 10<!-- 3834780  -->
Un nouvel écran appelé **Catégories d’application** a été ajouté pour améliorer l’expérience de navigation et de sélection des applications dans le portail d’entreprise pour Windows 10. Les applications des utilisateurs s’affichent désormais triées dans des catégories telles que **Proposée(s)** , **Éducation** et **Productivité**. Ce changement apparaît dans la version 10.3.3451.0 et les versions ultérieures du portail d’entreprise. Pour afficher le nouvel écran, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md). Pour plus d’informations sur les applications dans le portail d’entreprise, consultez [Installer et partager des applications sur votre appareil](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Application Conformité de Power BI <!-- 1455231 doc-work-item -->
Accédez à votre entrepôt de données Intune dans Power BI à l’aide de l’application [Conformité Intune (Entrepôt de données)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Avec cette application Power BI, vous pouvez désormais accéder à des rapports précréés et les partager sans aucune configuration supplémentaire et sans quitter votre navigateur web. Pour plus d’informations, consultez [Journal des changements - Application Conformité de Power BI](../developer/reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Les scripts PowerShell peuvent s’exécuter dans un hôte 64 bits sur des appareils 64 bits <!-- 1862675   -->
Quand vous ajoutez un script PowerShell à un profil de configuration d’appareil, le script s’exécute toujours en 32 bits, même sur les systèmes d’exploitation 64 bits. Avec cette mise à jour, un administrateur peut exécuter le script dans un hôte PowerShell 64 bits sur des appareils 64 bits (**Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter** > **Configurer** > **Exécuter le script dans un hôte PowerShell 64 bits**).

Pour plus d’informations sur l’utilisation de PowerShell, consultez [Scripts PowerShell dans Intune](../apps/intune-management-extension.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>Les utilisateurs macOS sont invités à mettre à jour leur mot de passe <!-- 1873216 -->
Intune applique le paramètre **ChangeAtNextAuth** sur les appareils macOS. Ce paramètre a un impact sur les utilisateurs finaux et sur les appareils qui ont des stratégies de conformité des mots de passe ou des profils de mot de passe de restriction sur les appareils. Les utilisateurs finaux sont invités à mettre à jour une fois leur mot de passe. Cette invite se produit chaque fois qu’un utilisateur exécute pour la première fois une tâche nécessitant une authentification, comme la connexion à l’appareil. Les utilisateurs peuvent également être invités à mettre à jour leur mot de passe lors de l’exécution de toute opération nécessitant des privilèges d’administration, comme la demande d’accès au trousseau. 

Tout changement apporté à une stratégie de mot de passe nouvelle ou existante par l’administrateur invite les utilisateurs finaux à mettre à nouveau à jour leur mot de passe.

S’applique à :  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Attribuer des certificats SCEP à un appareil macOS sans utilisateur    <!-- 2340521    -->
Vous pouvez attribuer des certificats SCEP (Simple Certificate Enrollment Protocol, protocole d’inscription de certificats simple) à l’aide d’attributs d’appareil à des appareils macOS, notamment à des appareils sans affinité utilisateur, et associer le profil de certificat à des profils Wi-Fi ou VPN. La prise en charge existante est ainsi étendue, permettant d’[attribuer des certificats SCEP à des appareils avec et sans affinité utilisateur](../protect/certificates-profile-scep.md) qui exécutent Windows, iOS et Android.  Cette mise à jour ajoute la possibilité de sélectionner le type de certificat *Appareil* quand vous configurez un profil de certificat SCEP pour macOS.

S’applique à : 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Mise à jour de l’interface utilisateur de l’accès conditionnel Intune   <!-- 2432313   -->
Nous avons apporté des améliorations à l’interface utilisateur pour l’accès conditionnel dans la console Intune. Par exemple :
- Remplacement du panneau *Accès conditionnel* d’Intune par le panneau d’Azure Active Directory. Cela garantit que vous avez accès à la gamme complète des paramètres et des configurations pour l’[accès conditionnel](../protect/conditional-access.md) (qui reste une technologie Azure AD) à partir de la console Intune. 
- Nous avons renommé le panneau *Accès local* en *Accès à Exchange*, et déplacé le programme d’installation *Connecteur de service Exchange* dans ce panneau renommé.  Ce changement consolide l’endroit où vous [configurez et supervisez les détails relatifs à Exchange Online et local](../protect/exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Les applications de navigateur kiosque et de navigateur Microsoft Edge peuvent s’exécuter sur des appareils Windows 10 en mode kiosque <!-- 2935135   -->
Vous pouvez utiliser des appareils Windows 10 en mode kiosque pour exécuter une ou plusieurs applications. Cette mise à jour inclut plusieurs modifications de l’utilisation des applications de navigateur en mode kiosque, notamment :

- Ajoutez le navigateur Microsoft Edge ou le navigateur kiosque pour qu’ils s’exécutent comme applications sur l’appareil kiosque (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **Windows 10 et ultérieur** pour la plateforme > **Kiosque** pour le type de profil).
- De nouvelles fonctionnalités et de nouveaux paramètres sont disponibles pour définir des autorisations ou des restrictions (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **Windows 10 et ultérieur** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil), notamment :

- Navigateur Microsoft Edge :
  - Utiliser le mode kiosque Microsoft Edge
  - Actualiser le navigateur après la durée d’inactivité

- Favoris et recherche :
  - Autoriser les changements sur le moteur de recherche

Pour obtenir la liste de ces paramètres, consultez :

- [Paramètres d’appareil Windows 10 et ultérieur pour une exécution en tant que kiosque ](../configuration/kiosk-settings-windows.md)
- [Restrictions d’appareil pour le navigateur Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Restrictions d’appareils concernant les favoris et la recherche](../configuration/device-restrictions-windows-10.md##favorites-and-search)

S’applique à : Windows 10 et versions ultérieures

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nouveaux paramètres de restriction d’appareil pour les appareils iOS et macOS <!-- 3448774   -->
Vous pouvez restreindre certains paramètres et certaines fonctionnalités sur les appareils exécutant iOS et macOS (**Configuration de l’appareil** > **Profils** > **Nouveau profil**  >  **iOS** ou **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour ajoute des fonctionnalités et des paramètres que vous pouvez contrôler, notamment définir l’heure de l’écran, modifier les paramètres eSIM et les forfaits mobiles, entre autres, sur les appareils iOS. Citons également le retardement de la visibilité par l’utilisateur des mises à jour logicielles, ainsi que le blocage de la mise en cache du contenu sur les appareils iOS. 

Pour connaître les fonctionnalités et les paramètres que vous pouvez restreindre, consultez :

- [Paramètres de restriction d’appareil iOS](../configuration/device-restrictions-ios.md)
- [Paramètres de restriction d’appareil macOS](../configuration/device-restrictions-macos.md)

S’applique à :

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Les appareils « kiosque » sont désormais appelés « appareils dédiés » sur les appareils Android Entreprise <!-- 3598402   -->
Pour s’aligner sur la terminologie d’Android, **kiosque** est remplacé par **appareils dédiés** pour les appareils Android Entreprise (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise pour la plateforme > **Propriétaire de l’appareil uniquement** > **Restrictions sur l’appareil** > **Appareils dédiés**).

Pour afficher les paramètres disponibles, accédez à [Paramètres des appareils pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

S’applique à :  
Android Entreprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Les paramètres Safari et Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS sont déplacés dans l’interface utilisateur Intune <!-- 3640850, 3803313   -->
Pour les appareils iOS, vous pouvez définir des paramètres Safari et configurer les mises à jour logicielles. Dans cette mise à jour, ces paramètres sont déplacés dans différentes parties de l’interface utilisateur Intune :

- Les paramètres Safari sont passés de **Safari** (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil) à **[Applications intégrées](../configuration/device-restrictions-ios.md#built-in-apps)** .
- Le paramètre **Retardement de la visibilité des mises à jour logicielles par l’utilisateur pour les appareils iOS supervisés** (**Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS**) est déplacé dans  **Restrictions sur l’appareil** >  **[Général](../configuration/device-restrictions-ios.md#general)** .  Pour plus d’informations sur l’impact sur les stratégies existantes, consultez [Mises à jour logicielles iOS](../protect/software-updates-ios.md#configure-the-policy). 

Pour obtenir la liste des paramètres, consultez :

- [Restrictions sur les appareils iOS](../configuration/device-restrictions-ios.md) 
- [Mises à jour logicielles iOS](../protect/software-updates-ios.md)

Cette fonctionnalité s’applique à : 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>L’option Activation des restrictions dans les paramètres de l’appareil est renommée en Heure de l’écran sur les appareils iOS <!-- 3699164   -->
Vous pouvez configurer **Activation des restrictions dans les paramètres de l’appareil** sur les appareils iOS supervisés (**Configuration de l’appareil** > **Profils** > **Nouveau profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour le type de profil > **Général**). Dans cette mise à jour, ce paramètre est renommé en **Heure de l’écran (mode supervisé uniquement)** . 

Le comportement reste le même. Plus précisément : 

- iOS 11.4.1 et antérieur : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. 
- iOS 12.0 et ultérieur : **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil, notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 ne voient plus l’onglet Restrictions dans les paramètres de l’appareil. Ces paramètres se trouvent dans **Heure de l’écran**. 

Pour obtenir la liste des paramètres, consultez [Restrictions sur les appareils iOS](../configuration/device-restrictions-ios.md#general).

S’applique à : 
- iOS


### <a name="device-management"></a>Gestion des appareils

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Renommer un appareil Windows inscrit <!-- 1911112  -->
Vous pouvez maintenant renommer un appareil Windows 10 inscrit (RS4 ou version ultérieure). Pour cela, choisissez **Intune** > **Appareils** > **Tous les appareils** > Choisissez un appareil > **Renommer l’appareil**. Cette fonctionnalité ne prend actuellement pas en charge le renommage des appareils Azure AD Windows hybrides.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Attribuer automatiquement des balises d’étendue à des ressources créées par un administrateur avec cette étendue <!-- 3173823  -->
Quand un administrateur crée une ressource, les étiquettes d’étendue affectées à l’administrateur sont automatiquement affectées à cette nouvelle ressource.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Le rapport des échecs d’inscription est déplacé dans le panneau Inscription des appareils <!-- 3560202  -->
Le rapport **Échecs d’inscription** a été déplacé dans la section **Superviser** du panneau **Inscription de l’appareil**. Deux nouvelles colonnes (Méthode d’inscription et Version du système d’exploitation) ont été ajoutées.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Rapport d’abandon du portail d’entreprise renommé en Inscriptions d’utilisateur incomplètes <!--3815076 eemiss -->
Le **rapport d’abandon du portail d’entreprise** a été renommé en **Inscriptions d’utilisateur incomplètes**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Semaine du 4 février 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Mode sombre du portail d’entreprise macOS Intune <!-- 3300524  -->
Le portail d’entreprise Intune macOS prend désormais en charge le Mode sombre pour macOS. Quand vous activez le Mode sombre sur un appareil macOS 10.14+, le portail d’entreprise ajuste son apparence à des couleurs reflétant ce mode.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Semaine du 21 janvier 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifications toast pour les applications Win32 <!-- 3136566   -->
Vous pouvez supprimer l’affichage des notifications toast à l’utilisateur final par affectation d’applications. Dans Intune, sélectionnez **Applications clientes** > **Applications** > sélectionnez l’application > **Affectations** > **Inclure les groupes**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Mise à jour de l’interface utilisateur des stratégies de protection des applications Intune <!-- 3251427  -->
Nous avons modifié les étiquettes des paramètres et des boutons d’Intune App Protection pour qu’ils soient tous plus faciles à comprendre. Quelques exemples de modifications :  
- Les commandes **Oui** / **Non** sont remplacées principalement par les commandes **Bloquer** / **Autoriser** et **Désactiver** / **Activer**. Les étiquettes sont également mises à jour.  
- Les paramètres ont également été remis en forme pour qu’ils apparaissent à côté de l’étiquette correspondante dans le contrôle, ce qui facilite la navigation.   

Les paramètres par défaut et le nombre de paramètres restent identiques. Toutefois, ce changement permet à l’utilisateur de comprendre, de parcourir et d’utiliser les paramètres plus facilement pour appliquer les stratégies App Protection sélectionnées. Pour plus d’informations, consultez [Paramètres iOS](../apps/app-protection-policy-settings-ios.md) et [Paramètres Android](../apps/app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Paramètres supplémentaires pour Outlook <!-- 3301182  -->
Vous pouvez désormais configurer les paramètres supplémentaires suivants pour Outlook pour iOS et Android à l’aide d’Intune :

- Autoriser uniquement les comptes professionnels ou scolaires à être utilisés dans Outlook sur iOS et Android
- Déployer une authentification moderne pour Office 365 et une authentification moderne hybride pour les comptes locaux
- Utiliser `SAMAccountName` pour le champ de nom d’utilisateur dans le profil d’e-mail quand l’authentification de base est sélectionnée
- Autoriser l’enregistrement des contacts
- Configurer la fonctionnalité Infos-courrier pour les destinataires externes
- Configurer la **Boîte de réception Prioritaire**
- Imposer la biométrie pour accéder à Outlook pour iOS
- Bloquer les images externes

> [!NOTE]
> Si vous utilisez des stratégies Intune App Protection pour gérer l’accès aux identités d’entreprise, n’activez pas la **biométrie obligatoire**. Pour plus d’informations, consultez **Exiger des informations d’identification d’entreprise pour l’accès** dans les [paramètres d’accès iOS](../apps/app-protection-policy-settings-ios.md#access-requirements) et les [paramètres d’accès Android](../apps/app-protection-policy-settings-android.md#access-requirements).

Pour plus d’informations, consultez [Paramètres de configuration Microsoft Outlook](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Supprimer les applications Android Entreprise <!-- 1352553 -->
Vous pouvez supprimer des applications Google Play géré à partir de Microsoft Intune. Pour supprimer une application Google Play géré, ouvrez Microsoft Intune dans le portail Azure et sélectionnez **Applications clientes** > **Applications**. À partir de la liste des applications, sélectionnez les points de suspension (...) à droite de l’application Google Play géré, puis sélectionnez **Supprimer** dans la liste affichée. Lorsque vous supprimez une application Google Play gérée à partir de la liste des applications, l’application Google Play gérée devient automatiquement non approuvée.

#### <a name="managed-google-play-app-type----1352580---"></a>Type d’application Google Play géré <!-- 1352580 -->
Le type d’application **Google Play géré** vous permet d’ajouter spécifiquement [les applications Google Play gérées](https://play.google.com/work/search?q=microsoft&c=apps) à Intune. En tant qu’administrateur Intune, vous pouvez désormais parcourir, rechercher, approuver, synchroniser et attribuer des applications Google Play géré approuvées dans Intune.  Vous n’avez plus besoin d’accéder séparément à la console Google Play géré, ni de vous authentifier de nouveau.  Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application**, sélectionnez le type d’application **Google Play géré**.

### <a name="default-android-pin-keyboard----3802457---"></a>Clavier de code PIN Android par défaut <!-- 3802457 -->
Les utilisateurs finaux qui ont défini un code PIN de stratégie Intune App Protection sur leurs appareils Android avec un type de code PIN « Numérique » verront désormais le clavier Android par défaut, au lieu de l’interface utilisateur du clavier Android fixe qui était affichée précédemment. Cette modification a été apportée pour des raisons de cohérence lors de l’utilisation des claviers par défaut sur Android et iOS, pour les deux types de code PIN « Numérique » et/ou « Code secret ». Pour plus d’informations sur les paramètres d’accès de l’utilisateur final sur Android, comme le code PIN de la stratégie de protection des applications, consultez [Exigences d’accès Android](../apps/app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Utiliser les paramètres recommandés par Microsoft avec les bases de référence de sécurité (préversion publique) <!-- 2055484   -->

Intune s’intègre à d’autres services axés sur la sécurité, notamment Windows Defender ATP et Office 365 ATP. Les utilisateurs demandent une stratégie commune et un ensemble cohérent de flux de travail de sécurité de bout en bout entre les services Microsoft 365. Notre objectif est d’aligner les stratégies afin de créer des solutions qui opèrent la liaison entre les opérations de sécurité et les tâches d’administration courantes. Dans Intune, nous souhaitons atteindre cet objectif en publiant un ensemble de « Lignes de base de sécurité » recommandées par Microsoft (**Intune** > **Lignes de base de sécurité**).  Un administrateur peut créer des stratégies de sécurité directement à partir de ces bases de référence, puis les déployer pour ses utilisateurs. Vous pouvez également personnaliser les recommandations en fonction des besoins de votre organisation. Intune garantit que les appareils restent conformes avec ces lignes de base, et signale aux administrateurs les utilisateurs ou appareils qui ne sont pas conformes.

Cette fonctionnalité étant en préversion publique, les profils créés maintenant ne sont pas déplacés vers les modèles Base de référence de la sécurité qui sont en disponibilité générale. Nous vous déconseillons d’utiliser ces modèles en préversion dans votre environnement de production.

Pour en savoir plus sur les bases de référence de la sécurité, consultez [Créer une base de référence de la sécurité Windows 10 dans Intune](../protect/security-baselines-monitor.md).

Cette fonctionnalité s’applique à : Windows 10 et versions ultérieures

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Les utilisateurs non-administrateurs peuvent activer BitLocker sur des appareils Windows 10 joints à Azure AD<!-- 2147379   -->
Lorsque vous activez les paramètres BitLocker sur des appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** comme plateforme > **Endpoint Protection** comme type de profil > **Chiffrement Windows**), vous ajoutez des paramètres BitLocker. 

Cette mise à jour comprend un nouveau paramètre BitLocker permettant aux utilisateurs standard (non administrateurs) d’activer le chiffrement. 

Pour voir les paramètres, accédez à [Paramètres Endpoint Protection pour Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Vérifier la conformité de Configuration Manager <!-- 2192052  eepublished  -->
Cette mise à jour inclut un nouveau paramètre de conformité System Center Configuration Manager (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**  >  **Windows 10 et ultérieur** > **Conformité de Configuration Manager**). Configuration Manager envoie des signaux pour la conformité Intune. À l’aide de ce paramètre, vous pouvez exiger que tous les signaux Configuration Manager retournent la valeur « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

[Conformité de Configuration Manager](../protect/compliance-policy-create-windows.md#configuration-manager-compliance) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personnaliser le papier peint sur les appareils iOS supervisés à l’aide d’un profil de configuration d’appareil <!-- 2809324   -->
Lorsque vous créez un profil de configuration d’appareil pour des appareils iOS, vous pouvez personnaliser certaines fonctionnalités (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres de **papier peint** qui permettent à un administrateur d’utiliser une image .png, .jpg ou .jpeg sur l’écran d’accueil ou l’écran de verrouillage. Ces paramètres de papier peint s’appliquent uniquement aux appareils supervisés. 

Pour obtenir la liste de ces paramètres, consultez [Paramètres des fonctionnalités d’appareil iOS](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>La fonctionnalité Kiosque Windows 10 est en disponibilité générale <!-- 3594661  -->
Dans cette mise à jour, la fonctionnalité Kiosque est en disponibilité générale sur les appareils Windows 10 et ultérieur. Pour voir tous les paramètres que vous pouvez ajouter et configurer, consultez [Paramètres kiosque pour Windows 10 (et ultérieur)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Le paramètre Partage de contacts via Bluetooth est supprimé dans Restrictions sur l’appareil > Propriétaire de l’appareil pour Android Entreprise <!-- 3598396   -->
Lorsque vous créez un profil de restrictions d’appareil pour les appareils Android Enterprise, vous disposez d’un paramètre **Partage de contacts via Bluetooth**. Dans cette mise à jour, le paramètre **Partage de contacts via Bluetooth** est supprimé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Restrictions d’appareil > Propriétaire de l’appareil** pour le type de profil > **Général**). 

Le paramètre **Partage de contacts via Bluetooth** n’est pas pris en charge pour la gestion du Propriétaire de l’appareil Android Enterprise. Par conséquent, la suppression de ce paramètre n’affectera aucun périphérique ni aucun client, même si ce paramètre est activé et configuré dans votre environnement.

Pour consulter la liste actuelle des paramètres, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-android-for-work.md).

S’applique à : Propriétaire d’appareil Android Entreprise

### <a name="device-management"></a>Gestion des appareils

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Prise en charge de la réinitialisation sélective pour les appareils WIP sans inscription <!-- 1434452 -->
WIP-WE (Windows Information Protection Without Enrollment) permet aux clients de protéger leurs données d’entreprise sur des appareils Windows 10 sans nécessiter une inscription complète à MDM. Une fois les documents protégés par une stratégie WIP-WE, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie WIP-WE. À partir d’Intune dans le portail Azure, sélectionnez **Application mobile** > **Réinitialisation sélective des applications**.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nouveaux journaux des opérations et possibilité d’envoyer des journaux aux services Azure Monitor <!-- 3762211  -->
Intune propose une journalisation d’audit intégrée qui assure le suivi des événements lorsque des modifications sont apportées. Cette mise à jour inclut de nouvelles fonctionnalités de journalisation, notamment les suivantes : 
- Journaux des opérations (préversion) qui présentent des détails sur les utilisateurs et les appareils inscrits, notamment les tentatives qui ont abouti et celles qui ont échoué.
- Les journaux d’audit et les journaux des opérations peuvent être envoyés à Azure Monitor, notamment aux comptes de stockage, aux hubs d’événements et à Log Analytics. Ces services vous permettent de stocker et d’utiliser des analyses comme Splunk et QRadar, ainsi que d’obtenir des visualisations de vos données de journalisation.

[Envoyer les données de journal à des comptes de stockage, des hubs d’événements ou Log Analytics dans Intune](../review-logs-using-azure-monitor.md) fournit plus d’informations sur cette fonctionnalité.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorer des autres écrans de l’Assistant Configuration sur un appareil DEP iOS <!-- 2687509  -->
En plus des écrans que vous pouvez déjà ignorer, vous pouvez définir des appareils DEP iOS pour ignorer les écrans suivants de l’Assistant Installation quand un utilisateur inscrit l’appareil : Afficher la sonnerie, Confidentialité, Migration Android, Bouton d’accueil, iMessage et FaceTime, Intégration, Surveiller la migration, Apparence, Heure de l’écran, Mise à jour logicielle, Configuration SIM.
Pour choisir quels écrans ignorer, accédez à **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton > **Profils** > choisissez un profil > **Propriétés** > **Personnalisation de l’Assistant Configuration** > choisissez **Masquer** pour tous les écrans que vous souhaitez ignorer > **OK**.
Si vous créez ou modifiez un profil, les écrans ignorés sélectionnés ont besoin de se synchroniser avec le serveur MDM Apple. Les utilisateurs peuvent effectuer une synchronisation manuelle des appareils pour éviter tout retard dans la sélection des modifications de profil.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises <!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie de protection des applications sans inscription) non inscrit, vous pouvez désormais utiliser Google Play dans sa version managée pour déployer des applications du Store et des applications métier pour les utilisateurs. Plus précisément, vous pouvez proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle ils n’ont plus besoin d’assouplir la posture de sécurité de leurs appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Semaine du 14 janvier 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Préversion de la prise en charge des appareils Android complètement gérés appartenant à l’entreprise <!-- 1574342  -->
Intune prend désormais en charge les appareils Android entièrement gérés, un scénario de type « entreprise propriétaire de l’appareil » dans lequel les appareils sont étroitement gérés par le service informatique et affiliés à différents utilisateurs. Les administrateurs pourront ainsi gérer l’ensemble de l’appareil, appliquer un large éventail de contrôles de stratégie non disponibles avec les profils professionnels et imposer aux utilisateurs d’installer les applications sur la version gérée de Google Play. Pour plus d’informations, consultez [Configurer l’inscription d’appareils Android entièrement gérés dans Intune](../enrollment/android-fully-managed-enroll.md) et [Inscrire vos appareils dédiés ou entièrement gérés](../enrollment/android-dedicated-devices-fully-managed-enroll.md).  Veuillez noter que cette fonctionnalité est en préversion. Certaines fonctionnalités Intune, telles que les certificats, la conformité et l’Accès conditionnel, ne sont pas actuellement disponibles avec les appareils Android des utilisateurs complètement managés.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Semaine du 7 janvier 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-app-pin----2298397---"></a>Code PIN d’application Intune <!-- 2298397 -->
En tant qu’administrateur informatique, vous pouvez maintenant configurer le nombre de jours d’attente possibles pour un utilisateur final avant qu’il ne doive changer le code PIN d’application Intune. Le nouveau paramètre, *Réinitialisation du code PIN au bout d’un nombre de jours*, est accessible dans le portail Azure en sélectionnant **Intune** > **Applications clientes** > **Stratégies de protection des applications** > **Créer une stratégie** > **Paramètres** > **Conditions d’accès**. Disponible pour les appareils [iOS](../apps/app-protection-policy-settings-ios.md) et [Android](../apps/app-protection-policy-settings-android.md), cette fonctionnalité prend en charge une valeur entière positive.


#### <a name="intune-device-reporting-fields----2748738---"></a>Champs de création de rapport sur les appareils Intune <!-- 2748738 -->
Intune fournit des champs de création de rapport supplémentaires sur les appareils, notamment l’ID d’inscription d’application, le fabricant Android, le modèle et la version du correctif de sécurité ainsi que le modèle iOS. Dans Intune, ces champs sont disponibles quand vous sélectionnez **Applications clientes** > **État de protection de l’application**, et que vous choisissez **Rapport de protection d’application : iOS, Android**. Ces paramètres vous aideront par ailleurs à configurer la liste **Autoriser** pour le fabricant d’appareil (Android), la liste **Autoriser** pour le modèle d’appareil (Android et iOS) et le paramètre de version minimale de la mise à jour de sécurité Android. 


### <a name="device-configuration"></a>Configuration des appareils

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration <!-- 3322847 -->

Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion publique. Avec cette mise à jour :

- Les modèles d’administration comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
- Les modèles d’administration sont disponibles en préversion publique.
- Les modèles d’administration sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et ultérieur**, dans **Type de profil**, choisissez **Modèles d’administration**.
- La création de rapports est activée

Pour plus d’informations sur cette fonctionnalité, accédez à [Modèles Windows 10 pour configurer les paramètres de stratégie de groupe](../configuration/administrative-templates-windows.md).

S’applique à : Windows 10 et versions ultérieures

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Utiliser S/MIME pour chiffrer et signer plusieurs appareils pour un utilisateur  <!-- 1333642 -->
Cette mise à jour inclut le chiffrement S/MIME des e-mails à l’aide d’un nouveau profil de certificat importé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > type de profil **Certificat PKCS importé**). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :
- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.
Pour plus d’informations sur cette fonctionnalité, consultez [Vue d’ensemble de S/MIME pour signer et chiffrer des e-mails](../protect/certificates-s-mime-encryption-sign.md).
Pris en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nouvelles options de connexion automatique et de conservation automatique des règles quand vous utilisez des paramètres DNS sur les appareils Windows 10 et les versions ultérieures <!-- 1333665, 2999078 -->
Sur les appareils Windows 10 et ultérieur, vous pouvez créer un profil de configuration VPN qui comporte la liste des serveurs DNS permettant de résoudre les domaines, par exemple contoso.com. Cette mise à jour contient de nouveaux paramètres de résolution de noms (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez  **Windows 10 et ultérieur** comme plateforme > choisissez **VPN** comme type de profil > **Paramètres DNS** >**Ajouter**) : 
- **Connexion automatique** : lorsque ce paramètre est **Activé**, l’appareil se connecte automatiquement au VPN lorsqu’il contacte le domaine saisi, par exemple, contoso.com.
- **Persistant** : par défaut, toutes les règles de la table de stratégie de résolution de noms (NRPT) sont actives tant que l’appareil est connecté avec ce profil VPN. Lorsque ce paramètre est **Activé** sur une règle NRPT, celle-ci reste active sur l’appareil, même si la connexion VPN est interrompue. La règle tient jusqu'à ce que le profil VPN soit supprimé ou jusqu'à ce que la règle soit supprimée manuellement, ce qui peut être effectuée avec PowerShell.
La page [Paramètres VPN Windows 10](../configuration/vpn-settings-windows-10.md) décrit les paramètres. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Utiliser la détection des réseaux approuvés pour les profils VPN sur les appareils Windows 10 <!-- 1500165 -->
Avec la détection des réseaux approuvés, vous pouvez empêcher les profils VPN de créer automatiquement une connexion VPN si l’utilisateur se trouve déjà sur un réseau approuvé. Cette mise à jour vous permet d’ajouter des suffixes DNS pour activer la détection des réseaux approuvés sur les appareils exécutant Windows 10 et versions ultérieures (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **VPN** comme type de profil).
La page [Paramètres VPN Windows 10](../configuration/vpn-settings-windows-10.md) liste les paramètres VPN actuels.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gérer les appareils Windows Holographic for Business utilisés par plusieurs utilisateurs <!-- 1907917, 1063203 -->
Actuellement, vous pouvez configurer les paramètres de PC partagé sur les appareils Windows 10 et Windows Holographic for Business avec un paramètre OMA-URI personnalisé. Avec cette mise à jour, un nouveau profil est ajouté pour configurer les paramètres d’appareil partagé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Appareil multi-utilisateur partagé**).
Pour en savoir plus sur cette fonctionnalité, accédez à [Paramètres Intune pour gérer les appareils partagés](../configuration/shared-user-device-settings.md).
S’applique à : Windows 10 (et versions ultérieures), Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nouveaux paramètres de mise à jour de Windows 10 <!--2626030  2512994  -->
Pour vos [boucles de mise à jour Windows 10](../protect/windows-update-for-business-configure.md), vous pouvez configurer :
- **Comportement des mises à jour automatiques**  :utilisez une nouvelle option, *Rétablir les valeurs par défaut*, pour restaurer les paramètres de mise à jour automatique d’origine sur un ordinateur Windows 10 exécutant la *mise à jour d’octobre 2018*
- **Empêcher l’utilisateur de suspendre l’installation des mises à jour Windows** : configurez un nouveau paramètre sous Mises à jour logicielles qui vous permet de refuser ou permettre aux utilisateurs de suspendre l’installation des mises à jour dans les *Paramètres* de leurs ordinateurs. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>Les profils de messagerie iOS peuvent utiliser la signature et le chiffrement S/MIME <!-- 2662949 -->
Vous pouvez créer un profil de messagerie comportant différents paramètres. Cette mise à jour contient des paramètres S/MIME servant à signer et à chiffrer les communications par e-mail sur les appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > **E-mail** comme type de profil).
La page [Paramètres de configuration de la messagerie iOS](../configuration/email-settings-ios.md) liste les paramètres.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Certains paramètres BitLocker prennent en charge l’édition Windows 10 Professionnel<!-- 2727036 -->
Vous pouvez créer un profil de configuration définissant des paramètres Endpoint Protection sur les appareils Windows 10, notamment BitLocker. Cette mise à jour ajoute la prise en charge de l’édition Windows 10 Professionnel pour certains paramètres BitLocker. Pour afficher ces paramètres de protection, accédez à [Paramètres Endpoint Protection pour Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Le paramètre Configuration des appareils partagés est renommé Message d’écran de verrouillage pour les appareils iOS dans le portail Azure<!-- 2809362 -->
Lors de la création d’un profil de configuration pour des appareils iOS, vous avez la possibilité d’ajouter des paramètres **Configuration des appareils partagés** pour afficher un texte spécifique sur l’écran de verrouillage. Cette mise à jour inclut les modifications suivantes : 
- Les paramètres **Configuration des appareils partagés** sur le Portail Azure sont renommés « Message de l’écran de verrouillage (mode supervisé uniquement) » (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **iOS** comme plateforme > choisissez **Fonctionnalités de l’appareil** comme type de profil > **Message de l’écran de verrouillage**).
- Lorsque vous ajoutez des messages d’écran de verrouillage, vous pouvez insérer un numéro de série, un nom d’appareil ou toute autre valeur propre à l’appareil comme variable dans **Informations de l’étiquette** et **Note de l’écran de verrouillage**. Par exemple, vous pouvez entrer `Device name: {{devicename}}` ou `Serial number is {{serialnumber}}` entre accolades. [Jetons iOS](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) liste les jetons utilisables.
La page [Paramètres d’affichage des messages sur l’écran de verrouillage](../configuration/ios-device-features-settings.md#lock-screen-message) liste les paramètres.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nouveaux paramètres de restriction d’appareil App Store, affichage de document, jeux ajoutés aux appareils iOS <!-- 2827760-->
Dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions d’appareil** comme type de profil > **App Store, affichage de document, jeux**, les paramètres suivants sont ajoutés : Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés et Autoriser les applications non gérées à lire à partir de comptes de contacts gérés. Pour voir ces paramètres, consultez [Restrictions d’appareil iOS](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nouveaux paramètres de notification, d’indicateurs et de keyguard pour les appareils des propriétaires d’appareils Android Entreprise <!-- 3201839 3201843 -->
Cette mise à jour comporte de nouvelles fonctionnalités pour les propriétaires d’appareils Android pour les entreprises. Pour pouvoir les utiliser, accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme**, choisissez **Android pour les entreprises** > dans **Type de profil**, choisissez **Propriétaire de l’appareil uniquement** > **Restrictions de l’appareil**.

Les nouvelles fonctionnalités incluent : 

- Désactiver l’affichage des notifications système, notamment les appels entrant, les alertes système, les erreurs système, etc.
- Suggérer d’ignorer les tutoriels de démarrage et les conseils sur les applications qui sont ouvertes pour la première fois.
- Désactiver les paramètres avancés de verrouillage du clavier, notamment l’appareil photo, les notifications, le déverrouillage par empreinte digitale, etc.


Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Les appareils des propriétaires d’appareils Android Entreprise peuvent utiliser des connexions VPN Always On <!-- 3202194 -->
Dans cette mise à jour, vous pouvez utiliser des connexions VPN Always On sur les appareils Android pour les entreprises des propriétaires d’appareils. Les connexions VPN AlwaysOn restent connectées ou se reconnectent immédiatement lorsque l’utilisateur déverrouille son appareil, lorsque l’appareil redémarre ou lorsque le réseau sans fil change. Vous pouvez également placer la connexion en mode « verrouillé », ce qui bloque tout le trafic réseau jusqu’à ce que la connexion VPN soit active.
Vous pouvez activer le VPN Always On dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android pour les entreprises** comme plateforme > **Restrictions de l’appareil** sur Propriétaire de l’appareil uniquement > paramètres **Connectivité**. Pour voir les paramètres, accédez à [Paramètres de restriction d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10 <!-- 3285177 --> 
Cette mise à jour comporte un nouveau paramètre permettant de mettre fin aux processus dans le Gestionnaire des tâches sur les appareils Windows 10. À l’aide d’un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > dans **Plateforme** , choisissez **Windows 10** > dans **Type de profil**, choisissez les paramètres **Restrictions de l’appareil** > **Général**), vous choisissez d’autoriser ou non ce paramètre.
Pour afficher ces paramètres, accédez à [Paramètres de restriction d’appareil Windows 10](../configuration/device-restrictions-windows-10.md).
S’applique à : Windows 10 et versions ultérieures

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Messages d’échec de la restriction d’inscription plus détaillés <!-- 3111564 -->
Des messages d’erreur plus détaillés sont disponibles en cas de non-respect des restrictions d’inscription. Pour voir ces messages, accédez à **Intune** > **Résoudre les problèmes** > et consultez la table des échecs d’inscription. Pour plus d’informations, consultez la [liste des échecs d’inscription](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="tenant-status-dashboard-----1124854---"></a>Tableau de bord État du locataire  <!-- 1124854 -->
La nouvelle [page État du locataire](tenant-status.md) fournit un emplacement unique où vous pouvez voir l’état et les détails associés de votre locataire.  Le tableau de bord est divisé en quatre zones :
- **Détails du locataire** : affiche des informations telles que le nom et l’emplacement de votre locataire, votre autorité MDM, le nombre total d’appareils inscrits dans votre locataire et le nombre de licences. Cette section liste également la version de service actuelle de votre locataire.
- **État du connecteur** : affiche des informations sur les connecteurs disponibles que vous avez configurés et peut également répertorier ceux que vous n’avez pas encore activés.  
   En fonction de leur état actuel, les connecteurs sont marqués comme Sain, Avertissement ou Non sain. Sélectionnez un connecteur pour extraire et afficher des détails ou configurer des informations supplémentaires associées.
- **Intégrité du service Intune** : affiche des détails sur les pannes ou incidents actifs pour votre locataire. Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.
- **Actualités Intune** : affiche les messages actifs pour votre locataire. Les messages incluent les éléments tels que des notifications quand votre locataire reçoit les dernières fonctionnalités Intune.  Les informations contenues dans cette section sont récupérées directement à partir du Centre de messages Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nouvelle expérience d’aide et de support dans le portail d’entreprise pour Windows 10 <!-- 1488939-->
La nouvelle page Aide et support du portail d’entreprise permet aux utilisateurs de résoudre les problèmes et demander de l’aide pour les problèmes liés à l’accès et aux applications. À partir de la nouvelle page, ils peuvent envoyer par e-mail des détails du journal de diagnostic et des erreurs ainsi que rechercher les informations relatives au support technique de leur organisation. Ils y trouveront également une section FAQ avec des liens vers la documentation Intune appropriée. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nouvelle expérience d’aide et de support pour Intune   <!-- #3307080 -->
Nous allons déployer la nouvelle expérience Aide et support sur tous les locataires au cours des prochains jours. Cette nouvelle expérience est disponible pour Intune et est accessible quand vous utilisez les panneaux Intune dans le [portail Azure](https://portal.azure.com/).
Cette nouvelle expérience utilisateur vous permet de décrire le problème avec vos propres mots et de recevoir des insights de résolution de problème, ainsi qu’un contenu de correction basé sur le web. Ces solutions sont proposées par le biais d’un algorithme d’apprentissage automatique basé sur des règles, piloté par les recherches des utilisateurs. En plus de recevoir une aide spécifique à chaque problème, vous utilisez le nouveau workflow de création d’incident pour ouvrir un incident nécessitant un support par e-mail ou par téléphone. Cette nouvelle expérience remplace l’expérience Aide et support précédente incluant un ensemble statique d’options présélectionnées en fonction de la zone de la console où vous vous trouvez quand vous ouvrez Aide et support. Pour plus d’informations, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-for-apps----1081941---"></a>Balises d’étendue pour les applications <!-- 1081941 -->
Vous pouvez créer des étiquettes de délimitation afin de limiter l’accès pour les rôles et applications. Vous pouvez ajouter une étiquette de délimitation à une application afin que seules les personnes avec des rôles ayant également reçu cette étiquette de délimitation aient accès à l’application. Il n’est actuellement pas possible d’attribuer des balises d’étendue aux applications ajoutées à Intune par Google Play géré ou achetées avec le programme d’achat en volume (VPP) Apple (une prise en charge future est planifiée). Pour plus d’informations, consultez [Utiliser des étiquettes de délimitation pour filtrer les stratégies](scope-tags.md).

## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
