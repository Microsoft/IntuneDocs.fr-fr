---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/08/2019
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
ms.openlocfilehash: 37ed7bfd204289c963b8134252d9d76f2379ecba
ms.sourcegitcommit: 768d581cb8bcc5fdcb8ade95d402b11223ab226c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73882494"
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

## <a name="week-of-november-4-2019"></a>Semaine du 4 novembre 2019

### <a name="device-security"></a>Sécurité des appareils

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Les bases de référence de sécurité sont prises en charge dans Microsoft Azure Government<!-- 4062552 -->

Les instances d’Intune hébergées sur *Microsoft Azure Government* peuvent désormais utiliser des [bases de référence de sécurité](../protect/security-baselines.md) pour vous aider à sécuriser et à protéger vos utilisateurs et appareils.

## <a name="week-of-october-28-2019"></a>Semaine du 28 octobre 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Conception de liste de contrôle améliorée dans l’application Portail d’entreprise pour Android<!-- 5550857 -->  
La liste de contrôle de d’installation d’application Portail d’entreprise pour Android a été mise à jour avec un design épuré et de nouvelles icônes. Les modifications s’alignent sur les mises à jour récentes apportées à l’application Portail d’entreprise pour iOS. Pour une comparaison côte à côte des modifications, consultez [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md). Pour consulter les étapes d’inscription mises à jour, consultez [S’inscrire avec un profil professionnel Android](/intune-user-help/enroll-device-android-work-profile) et [Inscrire votre appareil Android](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Applications Win32 sur des appareils Windows 10 en mode S<!-- 3747604 --> 
Vous pouvez installer et exécuter des applications Win32 sur des appareils gérés en mode S Windows 10. Pour ce faire, vous pouvez créer une ou plusieurs stratégies supplémentaires pour le mode S à l’aide des outils PowerShell Windows Defender application Control (WDAC). Signez les stratégies supplémentaires avec le portail de signature Device Guard, puis chargez et distribuez ces stratégies via Intune. Pour trouver cette fonctionnalité dans Intune, sélectionnez **Applications clientes** > **Stratégies supplémentaires en mode S Windows 10**. Pour plus d’informations, consultez [Activer des applications Win32 sur des appareils en mode S](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Définir la disponibilité de l’application Win32 en fonction d’une date et d’une heure<!-- 3510685 -->
En tant qu’administrateur, vous pouvez configurer l’heure de début et l’échéance d’une application Win32 requise. À l’heure de début, l’extension de gestion Intune démarre le téléchargement du contenu de l’application et le met en cache. L’application est installée à l’heure définie. Pour les applications disponibles, l’heure de début indique quand l’application est visible dans le Portail d’entreprise. Pour plus d’informations, consultez [Gestion des applications Win32 Intune](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Exiger le redémarrage de l’appareil en fonction de la période de grâce après l’installation de l’application Win32<!-- 3136567 -->
Vous pouvez exiger qu’un appareil redémarre après l’installation réussie d’une application Win32. Pour plus d’informations, consultez [Gestion des applications Win32 - Configurer les détails d’une installation d’application](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Mode sombre pour le Portail d’entreprise iOS<!-- 4911422 -->
Le Mode sombre est disponible sur le Portail d’entreprise iOS. Les utilisateurs peuvent télécharger des applications de l’entreprise, gérer leurs appareils et bénéficier d’un support informatique dans le modèle de couleurs de leur choix en fonction des paramètres de l’appareil. Le Portail d’entreprise iOS correspondra automatiquement aux paramètres de l’appareil de l’utilisateur final (Mode sombre ou clair). Pour plus d’informations, voir [Présentation du mode sombre sur le Portail d’entreprise Microsoft Intune pour iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Pour plus d’informations sur le portail d’entreprise iOS, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Version minimale de l’application appliquée au Portail d’entreprise Android<!-- 2378776 -->
Le paramètre **Version minimale du Portail d’entreprise** d’une stratégie de protection d’applications permet de définir une version minimale spécifique du Portail d’entreprise pour l’appliquer sur l’appareil des utilisateurs finaux. Vous pouvez ainsi lancer l’action **Bloquer l’accès**, **Effacer les données** ou **Avertir** lorsque la valeur n’est pas remplie. Les formats possibles de cette valeur suivent le modèle *[Majeure].[Mineure]* , *[Majeure].[Mineure].[Build]* ou *[Majeure].[Mineure].[Build].[Révision]* .

Le paramètre **Version minimale du Portail d’entreprise**, s’il est configuré, affecte tous les utilisateurs finaux qui utilisent la version 5.0.4560.0 et les versions à venir du Portail d’entreprise. Il n’a aucun effet sur ceux qui utilisent une version antérieure à la version dans laquelle cette fonctionnalité est publiée. Les utilisateurs finaux qui utilisent la mise à jour automatique des applications sur leur appareil ne verront a priori pas de boîtes de dialogue correspondant à cette fonctionnalité, dans la mesure où ils auront normalement la dernière version du Portail d’entreprise. Ce paramètre concerne uniquement les appareils Android inscrits et non inscrits avec protection des applications. Pour plus d’informations, voir [Paramètres de la stratégie de protection d’applications Android – Lancement conditionnel](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Gestion des appareils Microsoft 365

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Présentation du nœud Sécurité du point de terminaison dans la Gestion des appareils Microsoft 365<!-- 5630102 -->

Le nœud **Sécurité du point de terminaison** est désormais mis à la disposition générale dans l’espace de travail spécialiste de la Gestion des appareils Microsoft 365, à l’adresse https://devicemanagement.microsoft.com, qui regroupe les fonctionnalités permettant de sécuriser les points de terminaison :

- Bases de référence de la sécurité :  groupe préconfiguré de paramètres permettant d’appliquer un groupe connu de paramètres et de valeurs par défaut recommandés par Microsoft.

- Tâches de sécurité : tirez parti de la Gestion des menaces et des vulnérabilités de Microsoft Defender – PACM et utilisez Intune pour corriger les faiblesses des points de terminaison.

- Microsoft Defender – PACM : Microsoft Defender – Protection avancée contre les menaces intégrée permettant de mieux éviter les violations de la sécurité.

Ces paramètres resteront accessibles à partir d’autres nœuds applicables comme les appareils ; par ailleurs, l’état configuré actuel sera le même quel que soit l’endroit où ces fonctionnalités seront utilisées et activées.

Pour plus d’informations sur ces améliorations, voir le [billet de blog Intune Customer Success](https://aka.ms/Endpoint_security_node) sur le site web Microsoft Tech Community.

### <a name="device-management"></a>Gestion des appareils

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune prend en charge iOS 11 et les versions ultérieures<!-- 4665324  -->

L’inscription à Intune et le Portail d’entreprise Intune prennent maintenant en charge iOS 11 et les versions ultérieures. Les versions antérieures ne sont pas prises en charge.

### <a name="device-security"></a>Sécurité des appareils

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Base de référence Microsoft Edge (préversion)<!--  3787164  -->

Nous avons ajouté une base de référence de la sécurité en préversion pour les [paramètres Microsoft Edge](../protect/security-baseline-settings-edge.md). 

<!-- ########################## -->
## <a name="week-of-october-21-2019"></a>Semaine du 21 octobre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Gestion des appareils Microsoft 365

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Amélioration de l’expérience d’administration dans la Gestion des appareils Microsoft 365<!-- 5551239 -->

Une expérience d’administration actualisée et simplifiée est désormais mise à la disposition générale dans l’espace de travail spécialiste de la Gestion des appareils Microsoft 365, à l’adresse [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com) :

- **Navigation mise à jour** : vous trouverez une navigation de premier niveau simplifiée qui regroupe les fonctionnalités de façon logique.
- **Nouveaux filtres de plateforme** : vous pouvez sélectionner une seule plateforme pour afficher uniquement les stratégies et les applications correspondantes, sur les pages Appareils et Applications.
- **Nouvelle page d’accueil** : identifiez rapidement l’intégrité des services, l’état de votre locataire, les actualités, etc., sur la nouvelle page d’accueil.

Pour plus d’informations sur ces améliorations, voir le [billet de blog Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) sur le site web Microsoft Tech Community.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion d'applications

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Ajouter les applications Mobile Threat Defense sur des appareils non inscrits<!-- 3005337 -->
Vous pouvez créer une stratégie de protection d’applications Intune permettant de bloquer ou d’effacer de manière sélective les données d’entreprise des utilisateurs en fonction de l’intégrité d’un appareil. L’intégrité de l’appareil est déterminée par la solution Mobile Threat Defense (MTD) choisie. Cette fonctionnalité est aujourd’hui disponible avec les appareils inscrits dans Intune sous la forme d’un paramètre de conformité des appareils. Avec cette nouvelle fonctionnalité, nous étendons aux appareils non inscrits la détection des menaces d’un fournisseur Mobile Threat Defense. Sur Android, la dernière version du Portail d’entreprise est nécessaire sur l’appareil. Sur iOS, cette fonctionnalité sera disponible lorsque les applications auront intégré la dernière version du kit SDK Intune (12.0.15 et versions ultérieures). Nous mettrons à jour la rubrique Nouveautés dès que la première application aura adopté la dernière version de ce kit. Les applications restantes seront mises à disposition au fur et à mesure. Pour plus d’informations, voir [Créer une stratégie de protection d’applications Mobile Threat Defense avec Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices---2266073----"></a>Nouveau profil d’interface de configuration de microprogramme d’appareil pour les appareils Windows 10 et versions ultérieures<!-- 2266073  -->

Sur Windows 10 et versions ultérieures, vous pouvez créer un profil de configuration d’appareil pour contrôler les paramètres et les fonctionnalités (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour la plateforme). Dans cette mise à jour, il existe un nouveau type de profil d’interface de configuration de microprogramme d’appareil qui permet à Intune de gérer les paramètres UEFI (BIOS).

Pour plus d’informations sur cette fonctionnalité, consultez [Utiliser des profils DFCI sur des appareils Windows dans Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

S’applique à :
- Windows 10 RS5 (1809) et versions plus récentes sur le microprogramme pris en charge

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Afficher uniquement la page d’état d’inscription sur les appareils configurés par l’expérience OOBE (out-of-box experience)<!--3959566-->
Vous pouvez maintenant choisir d’afficher uniquement la page d’état d’inscription sur les appareils configurés par l’expérience OOBE Autopilot.

Pour afficher le nouveau bouton bascule, choisissez **Intune** > **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription** > **Créer un profil** > **Paramètres** > **Afficher uniquement la page sur les appareils configurés par l’expérience OOBE (out-of-box experience)** .


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Semaine du 14 octobre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion d'applications 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android<!-- 3041956   -->
Pour les installations d’applications disponibles sur les appareils dédiés et entièrement gérés avec un profil professionnel Android Entreprise, vous pouvez afficher l’état d’installation des applications ainsi que la version installée des applications Google Play gérées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](~/apps/app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](~/enrollment/android-enterprise-overview.md) et [Type d’application Google Play gérée](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge version 77 et ultérieures pour Windows 10 et macOS (préversion publique)<!-- 3872025, 4678761  -->
Microsoft Edge 77 et les versions ultérieures pourront être déployés sur les PC sous Windows 10 et macOS. 

La préversion publique offre les canaux **Dev** et **Bêta** pour Windows 10 et un canal **Bêta** pour macOS. Le déploiement s’effectue en anglais (EN) uniquement, mais les utilisateurs finaux peuvent changer la langue d’affichage dans le navigateur sous **Paramètres** > **Langues**. Microsoft Edge est une application Win32 installée dans le contexte du système et sur des architectures similaires (application x86 sur un système d’exploitation x86 et application x64 sur un système d’exploitation x64). Par ailleurs, les mises à jour automatiques du navigateur sont définies sur **Activé** par défaut, et Microsoft Edge ne peut pas être désinstallé. Pour plus d’informations, consultez [Ajouter Microsoft Edge pour Windows 10 à Microsoft Intune](~/apps/apps-windows-edge.md) et [Documentation Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Mise à jour de l’interface utilisateur de la protection des applications et de l’interface utilisateur de provisionnement d’applications iOS<!-- 4102027, 4102029   -->
L’interface utilisateur permettant de créer et modifier les stratégies de protection des applications et les profils de provisionnement d’applications iOS dans Intune a été mise à jour. Les modifications de l’interface utilisateur incluent :
- Une expérience simplifiée qui s’apparente à un Assistant condensé dans un seul panneau. 
- Une mise à jour du flux de création pour inclure les affectations.
- Une page récapitulative de tous les éléments définis pendant l’affichage des propriétés, préalablement à la création d’une stratégie ou pendant la modification d’une propriété. Par ailleurs, pendant la modification de propriétés, le récapitulatif présente uniquement la liste des éléments de la catégorie des propriétés modifiées.

Pour plus d’informations, consultez [Guide pratique pour créer et affecter des stratégies de protection des applications](~/apps/app-protection-policies.md) et [Utiliser des profils de provisionnement d’applications iOS](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Scénarios guidés Intune<!-- 4850318, 4831296, 3610611  -->
Intune propose désormais des scénarios guidés pour vous aider à effectuer une tâche ou plusieurs tâches dans Intune. Un scénario guidé est une série d’étapes personnalisée (workflow) centrée sur un cas d’usage de bout en bout. Les scénarios courants sont définis en fonction du rôle joué par un administrateur, un utilisateur ou un appareil dans votre organisation. Ces workflows nécessitent généralement un ensemble de profils, de paramètres, d’applications et de contrôles de sécurité soigneusement orchestrés pour offrir une expérience utilisateur et une sécurité optimales. Les nouveaux scénarios guidés sont les suivants :
- [Déployer Microsoft Edge pour mobile](~/fundamentals/guided-scenarios-edge.md)
- [Applications mobiles Microsoft Office sécurisées](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Bureau moderne géré par le cloud](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Pour plus d’informations, consultez [Vue d’ensemble des scénarios guidés Intune](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Variable de configuration des applications supplémentaire disponible<!-- 4969237   -->
Au moment de créer une stratégie de configuration des applications, vous pouvez inclure la variable de configuration `AAD Device ID` parmi vos paramètres de configuration. Dans Intune, sélectionnez **Applications clientes** > **Stratégies de configuration des applications** > **Ajouter**. Entrez les détails de votre stratégie de configuration, puis sélectionnez **Paramètres de configuration** pour afficher le panneau **Paramètres de configuration**. Pour plus d’informations, consultez [Stratégies de configuration des applications pour les appareils Android Enterprise gérés – Utiliser le concepteur de configuration](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Créer des groupes d’objets de gestion appelés ensembles de stratégies<!-- 3762880  -->
Les ensembles de stratégies vous permettent de créer un ensemble de références à des entités de gestion existantes qui doivent être identifiées, ciblées et supervisées comme une seule unité conceptuelle. Les ensembles de stratégies ne remplacent pas les concepts ou objets existants. Vous pouvez continuer d’affecter des objets individuels dans Intune et les référencer dans un ensemble de stratégies. Par conséquent, toute modification apportée à ces objets individuels est répercutée dans l’ensemble de stratégies.  Dans Intune, sélectionnez **Ensembles de stratégies** > **Créer** pour créer un ensemble de stratégies. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration des appareils

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Mise à jour de l’interface utilisateur pour créer et modifier des anneaux de mise à jour Windows 10<!-- 4099089         -->
Nous avons mis à jour l’expérience de l’interface utilisateur pour [créer et modifier des anneaux de mise à jour Windows 10](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) pour Intune. Voici les changements apportés à l’interface utilisateur :  
- Un format de type Assistant condensé dans un même panneau de console, qui met fin à la prolifération des panneaux à laquelle vous étiez auparavant exposé au moment de configurer des anneaux de mise à jour.   
- Le workflow révisé inclut les affectations avant la finalisation de la configuration initiale de l’anneau.
- Une page récapitulative dans laquelle vous pouvez examiner toutes les configurations que vous avez effectuées, avant d’enregistrer et déployer un nouvel anneau de mise à jour. Pendant la modification d’un anneau de mise à jour, le récapitulatif présente uniquement la liste des éléments définis dans une catégorie de propriétés que vous avez modifiées.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Mise à jour de l’interface utilisateur pour créer et modifier une stratégie de mise à jour logicielle iOS<!-- 4099090       --> 
Nous avons mis à jour l’expérience de l’interface utilisateur pour [créer](../protect/software-updates-ios.md#configure-the-policy) et [modifier](../protect/software-updates-ios.md#edit-a-policy) des stratégies de mise à jour logicielle iOS pour Intune.  Voici les changements apportés à l’interface utilisateur :  
- Un format de type Assistant condensé dans un même panneau de console, qui met fin à la prolifération des panneaux à laquelle vous étiez auparavant exposé pendant la configuration des stratégies de mise à jour.   
- Le workflow révisé inclut les affectations avant la finalisation de la configuration initiale de la stratégie.
- Une page récapitulative dans laquelle vous pouvez examiner toutes les configurations que vous avez effectuées, avant d’enregistrer et déployer une nouvelle stratégie. Pendant la modification d’une stratégie, le récapitulatif présente uniquement la liste des éléments définis dans une catégorie de propriétés que vous avez modifiées.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Les paramètres de redémarrage commencé sont supprimés des anneaux Windows Update<!--  4464404   WNReady   -->
Comme annoncé précédemment, les anneaux de mise à jour Windows 10 d’Intune [prennent désormais en charge les paramètres d’échéance](../protect/windows-update-settings.md) et ne prennent plus en charge le *redémarrage commencé*. Les paramètres de *redémarrage engagé* ne sont plus accessibles pendant la configuration ou la gestion d’anneaux de mise à jour dans Intune.  

Ce changement est en adéquation avec les récentes [modifications apportées à la maintenance de Windows](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) et sur les appareils qui exécutent Windows 10 1903 ou une version ultérieure, les *échéances* remplacent les configurations du *redémarrage commencé*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Empêcher les installations d’applications à partir de sources inconnues sur les appareils avec profil professionnel Android Entreprise<!-- 4760025   -->
Sur les appareils avec profil professionnel Android Entreprise, les utilisateurs ne peuvent pas installer d’applications à partir de sources inconnues. Dans cette mise à jour, il existe un nouveau paramètre : **Empêcher les installations d’applications à partir de sources inconnues dans le profil personnel**. Par défaut, ce paramètre empêche les utilisateurs d’effectuer un chargement indépendant d’applications de sources inconnues vers le profil personnel de l’appareil.

Pour voir les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Profil professionnel Android Entreprise

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Créer un proxy HTTP global sur les appareils de propriétaires d’appareils Android Entreprise<!-- 4816339   -->
Sur les appareils Android Entreprise, vous pouvez configurer un proxy HTTP global pour respecter les standards de navigation web de votre organisation (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **Propriétaire de l’appareil > Restrictions de l’appareil** pour le type de profil > **Connectivité**). Une fois la configuration terminée, l’ensemble du trafic HTTP utilisera ce proxy.

Pour configurer cette fonctionnalité et voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Propriétaire d’appareil Android Entreprise

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Le paramètre Se connecter automatiquement est supprimé dans les profils Wi-Fi de l’administrateur d’appareil Android et Android Entreprise<!-- 5021055   -->
Sur les appareils de l’administrateur d’appareil Android et Android Enterprise, vous pouvez créer un profil Wi-Fi pour configurer différents paramètres (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Administrateur d’appareil Android** ou **Android Entreprise** pour la plateforme > **Wi-Fi** pour le type de profil). Dans cette mise à jour, le paramètre **Se connecter automatiquement** est supprimé, car il n’est [pas pris en charge par Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Si vous utilisez ce paramètre dans un profil Wi-Fi, vous avez peut-être remarqué que **Se connecter automatiquement** ne fonctionne pas. Vous n’avez aucune action à effectuer, mais sachez que ce paramètre a été retiré de l’interface utilisateur Intune.

Pour voir les paramètres actuels, accédez à [Paramètres Wi-Fi Android](../configuration/wi-fi-settings-android.md) ou [Paramètres Wi-Fi Android Entreprise](../configuration/wi-fi-settings-android-enterprise.md).

S’applique à :
- Administrateur d’appareil Android 
- Android Entreprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Nouveaux paramètres de configuration d’appareil pour les appareils iOS et iPadOS supervisés<!-- 5199328   -->
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

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Spécifier les versions du système d’exploitation d’appareil Android qui s’inscrivent avec le profil professionnel ou l’inscription d’administrateur d’appareil<!-- 4350697   -->
À partir des exigences du type d’appareil Intune, vous pouvez utiliser la version du système d’exploitation de l’appareil pour spécifier les appareils utilisateur qui utiliseront l’inscription de profil professionnel Android Entreprise ou l’inscription d’administrateur d’appareil Android.  Pour en savoir plus, consultez la section relative à la [définition de restrictions d’inscription](../enrollment/enrollment-restrictions-set.md).

#### <a name="windows-autopilot-deployment-reports---3856172---"></a>Programme de déploiement Windows AutoPilot<!-- 3856172 -->
Un nouveau rapport détaille chaque appareil déployé via Windows Autopilot. Pour plus d’informations, consultez [Rapport de déploiement Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report). Nous déployons actuellement cette fonctionnalité pour tous les clients et prévoyons son achèvement d’ici la fin de la semaine prochaine.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des appareils

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Nouvelles restrictions pour le changement de nom des appareils Windows<!-- 3478938  -->
Au moment de renommer un appareil Windows, vous devez suivre les nouvelles règles :
- 15 caractères ou moins (doit être inférieur ou égal à 63 octets, à l’exclusion de la valeur NULL de fin)
- Valeur non null ou chaîne vide
- Caractères ASCII autorisés : Lettres (a-z, A-Z), chiffres (0-9) et traits d’union
- Caractères Unicode autorisés : caractères >= 0x80, format UTF8 valide, mappage possible à un nom de domaine international (autrement dit, RtlIdnToNameprepUnicode convient ; voir la RFC 3492)
- Les noms ne doivent pas contenir que des chiffres
- Aucun espace dans le nom
- Caractères non autorisés : { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Pour plus d’informations, consultez [Renommer un appareil dans Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Nouveau rapport Android dans la page de présentation des appareils<!-- 4924364 -->
Dans la page de présentation des appareils figure un nouveau rapport qui indique le nombre d’appareils Android inscrits dans chaque solution de gestion d’appareils. Ce graphique présente le nombre d’appareils inscrits d’administrateur d’appareils avec profil professionnel entièrement gérés et dédiés. Pour afficher le rapport, choisissez **Intune** > **Appareils** > **Vue d’ensemble**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>Certificats PKCS pour macOS<!-- 1333650       -->
Vous pouvez désormais [utiliser des certificats PKCS avec macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Vous pouvez sélectionner le certificat PKCS comme type de profil pour macOS et déployer des certificats d’utilisateur et d’appareil qui présentent les [champs Objet personnalisé et Autre nom de l’objet](../protect/certficates-pfx-configure.md#subject-name-format-for-macos).  

Le certificat PKCS pour macOS prend aussi en charge le nouveau paramètre _Autoriser toutes les applications à accéder à la clé privée_. Ce paramètre vous permet d’autoriser toutes les applications associées à accéder à la clé privée du certificat.  Pour plus d’informations sur ce paramètre, consultez la documentation Apple à l’adresse https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Informations d’identification dérivées pour provisionner des appareils mobiles iOS avec des certificats<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune prend en charge l’utilisation d’[informations d’identification dérivées](../protect/derived-credentials.md) comme méthode d’authentification et pour la signature et le chiffrement S/MIME pour les appareils iOS. Les informations d’identification dérivées sont une implémentation du standard *NIST (National Institute of Standards and Technology) 800-157* pour le déploiement de certificats sur les appareils.  

Les informations d’identification dérivées reposent sur l’utilisation d’une carte de vérification d’identité personnelle (PIV) ou d’une carte d’accès commun (CAC), comme une carte à puce. Pour obtenir des informations d’identification dérivées pour leur appareil mobile, les utilisateurs doivent accéder à l’application Portail d’entreprise pour suivre un workflow d’inscription propre au fournisseur utilisé.  Tous les fournisseurs d’informations d’identification dérivées imposent l’utilisation d’une carte à puce sur un ordinateur pour s’authentifier auprès d’eux. Le fournisseur émet alors un certificat à destination de l’appareil qui est dérivé de la carte à puce de l’utilisateur.  

Intune prend en charge les fournisseurs d’informations d’identification dérivées suivants :
- DISA Purebred
- Entrust Datacard
- Intercede

Vous pouvez utiliser les informations d’identification dérivées comme méthode d’authentification pour les profils de configuration d’appareil pour un VPN, le Wi-Fi et l’e-mail. Vous pouvez aussi les utiliser pour l’authentification des applications et pour le chiffrement et la signature S/MIME.  

Pour plus d’informations sur le standard, consultez [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) sur www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Utiliser l’API Graph pour spécifier un nom d’utilisateur principal local comme variable pour les certificats SCEP<!--  5437939        -->  
Quand vous utilisez l’[API Graph Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0), vous pouvez spécifier onPremisesUserPrincipalName comme variable pour l’autre nom d’objet des certificats SCEP.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Semaine du 23 septembre 2019

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Inscription des utilisateurs iOS en préversion<!-- 4817900 -->
La version iOS 13.1 d'Apple inclut l’inscription utilisateur, une nouvelle forme de gestion simplifiée pour les appareils iOS. Elle peut être utilisée à la place de la méthode Inscription des appareils ou Inscription automatique des appareils (anciennement Programme d’inscription des appareils) pour les appareils personnels. La préversion d'Intune prend en charge cette fonctionnalité en vous permettant de :

- Inscription d'utilisateur cible à des groupes d'utilisateurs.
- Donner aux utilisateurs finaux la possibilité de choisir entre une inscription d'utilisateur plus simple ou une inscription d'appareil plus avancée lorsqu'ils inscrivent leurs appareils.

Depuis le 24/9/2019 et la version iOS 13.1, nous déployons ces mises à jour pour tous les clients et prévoyons leur achèvement d’ici la fin de la semaine prochaine.
S’applique à :

iOS 13.1 et versions ultérieures

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Prise en charge Intune pour les appareils iPadOS et iOS 13.1<!--5439574-->
Intune prend désormais en charge à la fois les appareils iPadOS et iOS 13.1. Pour plus d’informations, consultez [ce billet de blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>Semaine du 16 septembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion d'applications 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Applications métier privées Google Play gérées<!-- 1464182  -->
Intune permet désormais aux administrateurs informatiques de publier des applications métier Android privées sur Google Play géré via un iframe incorporé dans la console Intune.  Auparavant, les administrateurs informatiques devaient publier les applications métier directement sur la console de publication de Google, ce qui nécessitait plusieurs étapes et prenait beaucoup de temps. Cette nouvelle fonctionnalité facilite la publication d’applications métier avec un ensemble d’étapes minimal, sans avoir à sortir de la console Intune.  Les administrateurs n’ont plus besoin de s’inscrire manuellement en tant que développeur avec Google, ni de payer les frais d’inscription à Google de 25 USD.  Les scénarios de gestion d’entreprise Android qui utilisent Google Play géré peuvent tirer parti de cette fonctionnalité (profil de travail, appareils dédiés, entièrement gérés et non inscrits). Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Google Play géré** sur la liste **Type d’application**. Pour en savoir plus sur les applications Google Play gérées, consultez [Ajouter des applications Google Play managé à des appareils d’entreprise Android avec Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Application Portail d’entreprise Windows<!-- 1473353, 3598357 -->
Le portail d’entreprise Windows est en cours de mise à jour. Vous pourrez utiliser plusieurs filtres sur la page Applications dans le Portail d’entreprise Windows. La page Détails de l’appareil est également en cours de mise à jour pour offrir une expérience utilisateur améliorée. Nous sommes en train de déployer ces mises à jour pour tous les clients et prévoyons leur achèvement d’ici la fin de la semaine suivante.

#### <a name="macos-support-for-web-apps---3174427---"></a>prise en charge macOS pour les applications web<!-- 3174427 -->
Les applications web, qui vous permettent d’ajouter un raccourci vers une URL sur le web, peuvent être installées sur le Dock à l’aide du Portail d’entreprise macOS. Les utilisateurs finaux peuvent accéder à l’action **Installer** à partir de la page des détails de l’application pour une application web dans le Portail d’entreprise macOS. Pour plus d’informations sur le type d’application **Lien web**, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md) et [Ajouter des applications web à Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>Prise en charge macOS pour les applications VPP<!-- 3173501  -->
Les applications macOS, achetées à l’aide d’Apple Business Manager, s’affichent dans la console lors de la synchronisation des jetons Apple VPP dans Intune. Vous pouvez attribuer, révoquer et réassigner des licences d’appareil et d’utilisateur pour des groupes à l’aide de la console Intune. Microsoft Intune vous aide à gérer les applications VPP achetées pour une utilisation dans votre entreprise en :

- Signalant les informations de licence de l’App Store.
- Effectuant le suivi du nombre de licences utilisées.
- Vous empêchant d’installer davantage de copies de l’application que vous n’en possédez.

Pour plus d’informations sur Intune et VPP, consultez [Gérer les applications et les livres achetés en volume avec Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>Prise en charge de l’iframe Google Play managés<!-- 2871756  -->
Intune propose désormais un support pour l’ajout et la gestion des liens web directement dans la console Intune via l’iframe Google Play géré.  Cela permet aux administrateurs informatiques d’envoyer une URL et une image d’icône, puis de déployer ces liens sur des appareils, comme des applications Android standard. Les scénarios de gestion d’entreprise Android qui utilisent Google Play géré peuvent tirer parti de cette fonctionnalité (profil de travail, appareils dédiés, entièrement gérés et non inscrits). Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Sélectionnez ensuite **Google Play géré** sur la liste **Type d’application**. Pour en savoir plus sur les applications Google Play gérées, consultez [Ajouter des applications Google Play managé à des appareils d’entreprise Android avec Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Installer des applications métier Android sur des appareils Zebra en mode silencieux<!-- 4252734  -->
Lors de l’installation d’applications métier Android sur des [appareils Zebra](../configuration/android-zebra-mx-overview.md), au lieu d’être invité à télécharger et à installer l’application métier, vous pourrez l’installer en mode silencieux. Dans Intune, sélectionnez **Applications clientes** > **Applications** > **Ajouter**. Dans le volet **Ajouter une application**, sélectionnez **Application métier**. Pour plus d’informations, consultez [Ajouter une application métier Android à Microsoft Intune](../apps/lob-apps-android.md).

Actuellement, une fois l’application métier téléchargée, une notification **Téléchargement réussi** s’affiche sur l’appareil de l’utilisateur. La notification ne peut être ignorée qu’en appuyant sur **Tout effacer** dans la nuance de notification. Ce problème de notification sera résolu dans une prochaine version, et l’installation sera complètement silencieuse, sans aucun indicateur visuel.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Lire et écrire des opérations d’API Graph pour les applications Intune<!-- 5031704  -->
Les applications peuvent appeler les opérations de lecture et d’écriture d’API Graph Intune avec leur identité d’application, sans informations d’identification d’utilisateur. Pour en savoir plus sur l’accès à l’API Microsoft Graph API pour Intune, consultez la section relative à [l’utilisation d’Intune dans Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Partage et chiffrement des données protégés pour le kit de développement logiciel (SDK) Intune App pour iOS<!-- 3586942  -->
Le kit de développement logiciel (SDK) Intune App pour iOS utilisera des clés de chiffrement 256 bits lorsque le chiffrement sera activé par des stratégies App Protection. Toutes les applications auront besoin d’un kit de développement logiciel (SDK) versions 8.1.1 pour autoriser le partage de données protégées.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration des appareils

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Prise en charge des profils VPN IKEv2 pour iOS<!-- 1943438   -->
Dans cette mise à jour, vous pouvez créer des profils VPN pour le client VPN natif iOS en utilisant le protocole IKEv2. IKEv2 est un nouveau type de connexion dans **Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **VPN** comme type de profil > **Type de connexion**.

Ces profils VPN configurent le client VPN natif, donc aucune application cliente VPN n’est installée ni envoyée à des appareils gérés. Cette fonctionnalité nécessite que les appareils soient inscrits auprès d’Intune (inscription MDM).

Pour afficher les paramètres VPN actuels que vous pouvez configurer, consultez [Configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md).

S’applique à :
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Les fonctionnalités de l’appareil, les restrictions de l’appareil et les profils d’extension pour les paramètres iOS et macOS sont affichés par type d’inscription.<!-- 4886161   -->

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

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Nouveaux paramètres de contrôle vocal pour les appareils iOS supervisés exécutés en mode plein écran<!-- 4892835   -->
Dans Intune, vous pouvez créer des stratégies pour exécuter des appareils iOS supervisés en mode plein écran, ou un appareil dédié (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour plateforme > **Restrictions de l’appareil** pour type de profil > **Plein écran**).

Dans cette mise à jour, vous pouvez contrôler les nouveaux paramètres suivants :
- **Contrôle vocal** : active le contrôle vocal sur l’appareil en mode plein écran.
- **Modification du contrôle vocal** : autorisez les utilisateurs à modifier le paramètre de contrôle vocal sur l’appareil en mode plein écran.

Pour afficher les paramètres actuels, accédez à [Paramètres de plein écran d’iOS](../configuration/device-restrictions-ios.md#kiosk).

S’applique à :
- iOS 13.0 et versions ultérieures

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Utiliser l’authentification unique pour les applications et sites web sur vos appareils iOS et macOS<!-- 4893175   -->
Dans cette mise à jour, il y a de nouveaux paramètres d’authentification unique pour les appareils iOS et macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** ou **macOS** pour plateforme > **Fonctionnalités de l’appareil** pour le type de profil).

Utilisez ces paramètres pour configurer une expérience d’authentification unique, en particulier pour les applications et les sites Web qui utilisent l’authentification Kerberos. Vous pouvez choisir entre une extension d’application d’authentification unique d’informations d’identification générique et une extension Kerberos intégrée à Apple.

Pour afficher les fonctionnalités actuelles de l’appareil que vous pouvez configurer, accédez à [Fonctionnalités de l’appareil iOS](../configuration/ios-device-features-settings.md) et à [Fonctionnalités de l’appareil macOS](../configuration/macos-device-features-settings.md).

S’applique à :
- iOS 13.0 et ultérieur
- macOS 10.15 et ultérieur

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associer des domaines à des applications sur des appareils macOS 10.15 et ultérieurs<!-- 4898079   -->
Sur les appareils macOS, vous pouvez configurer différentes fonctionnalités et envoyer ces fonctionnalités sur vos appareils à l’aide d’une stratégie (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour plateforme > **Fonctionnalités de l’appareil** pour type de profil). Dans cette mise à jour, vous pouvez associer des domaines à vos applications. Cette fonctionnalité permet de partager des informations d’identification avec des sites web associés à votre application et peut être utilisée avec l’extension d’authentification unique d’Apple, les liens universels et le remplissage automatique du mot de passe. 

Pour voir les fonctionnalités actuelles que vous pouvez configurer, accédez à [Paramètres des fonctionnalités d’appareil macOS dans Intune](../configuration/macos-device-features-settings.md).

S’applique à :
- macOS 10.15 et ultérieur

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Utilisez « iTunes » et « applications » dans l’URL de l’App Store iTunes lors de l’affichage ou du masquage d’applications sur des appareils iOS supervisés<!-- 4928474   --> 
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

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Interface utilisateur mise à jour pour la configuration de l’accès à Microsoft Exchange local<!-- 4092920 -->  
Nous avons mis à jour la console dans laquelle vous [configurez l’accès à Microsoft Exchange local](../protect/conditional-access-exchange-create.md). Toutes les configurations pour l’accès à Exchange local sont désormais disponibles dans le volet de la console où vous *autorisez le contrôle de l’accès à Exchange local*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Autoriser ou restreindre l’ajout de widgets d’applications à l’écran d’accueil sur les appareils de profil professionnel Android Entreprise<!-- 1109650  --> 
Sur les appareils Android Enterprise, vous pouvez configurer les fonctionnalités dans le profil professionnel (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour plate-forme > **Profil professionnel uniquement > Restrictions de l’appareil** pour type de profil). Dans cette mise à jour, vous pouvez autoriser les utilisateurs à ajouter des widgets exposés par les applications de profil professionnel à l’écran d’accueil de l’appareil.

Pour voir les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Profil professionnel Android Entreprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Par défaut, les nouveaux locataires sont éloignés de la gestion des administrateurs d’appareils Android<!-- 4869790   -->
Les fonctionnalités d’administrateur d’appareils Android ont été remplacées par Android Entreprise. Par conséquent, nous vous recommandons d’utiliser Android Entreprise pour de nouvelles inscriptions à la place. Dans une prochaine mise à jour, les nouveaux locataires devront suivre les étapes préalables suivantes de l’inscription Android pour utiliser la gestion des administrateurs d’appareils : Accédez à **Intune** > **Inscription d’un appareil** > **Inscription Android** > **Appareils personnels et appartenant à l’entreprise avec privilèges d’administration d’appareils** > **Utiliser un administrateur d’appareils pour gérer les appareils**.

Les environnements des locataires existants ne seront pas modifiés.

Pour plus d’informations sur l’administrateur d’appareils Android dans Intune, consultez [Inscription de l’administrateur d’appareils Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>Liste des appareils DEP associés à un profil<!-- 5012045 idmiss -->
Vous pouvez maintenant voir une liste paginée d’appareils du programme automatisé d’inscription des appareils (DEP) Apple associés à un profil. Vous pouvez effectuer une recherche dans la liste à partir de n’importe quelle page de la liste. Pour voir la liste, accédez à **Intune** > **Inscription d’appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisir un jeton > **Profils** > choisir un profil > **Appareils associés** (sous **Surveiller**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des appareils

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Plus de prise en charge d’appareils Android entièrement gérés<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
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

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Envoyer des notifications à un seul appareil<!-- 4928910 -->
Vous pouvez maintenant sélectionner un seul appareil, puis utiliser une action d’appareil à distance pour [envoyer une notification personnalisée uniquement à cet appareil](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Les actions de réinitialisation de réinitialisation et de code secret ne sont pas disponibles pour les appareils iOS inscrits à l’aide de l’inscription de l’utilisateur.<!-- 4950491 -->
L’inscription de l’utilisateur est un nouveau type d’inscription d’appareils Apple. Lorsque vous inscrivez des appareils à l’aide de l’inscription de l’utilisateur, les opérations à distance de réinitialisation et de réinitialisation du code secret ne sont pas disponibles pour ces appareils.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Prise en charge des appareils iOS 13 et macOS Catalina par Intune<!-- 4665317 -->
Intune prend maintenant en charge la gestion des appareils iOS 13 et macOS Catalina.
Pour plus d’informations, consultez ce [billet de blog Prise en charge de iOS 13 et iPadOS par Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>Prise en charge de BitLocker pour la rotation de mot de passe de récupération pilotée par le client<!--  3444125 -->
Utilisez les paramètres de protection de point de terminaison Intune pour configurer la [rotation de mot de passe de récupération pilotée par le client](../protect/endpoint-protection-windows-10.md#windows-encryption) pour BitLocker sur les appareils qui exécutent Windows version 1909 ou ultérieure.

Ce paramètre déclenche une actualisation du mot de passe de récupération piloté par le client après la récupération d’un lecteur de système d’exploitation (à l’aide de bootmgr ou de WinRE) et le déverrouillage du mot de passe de récupération sur un lecteur de données fixe. Ce paramètre actualise le mot de passe de récupération spécifique qui a été utilisé. Les autres mots de passe inutilisés sur le volume restent inchangés. Pour plus d’informations, consultez la documentation du fournisseur de services de chiffrement BitLocker pour [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Protection contre les falsifications pour l’antivirus Windows Defender<!-- 4705448        -->
Utilisez Intune pour gérer la *protection contre les falsifications* pour l’antivirus Windows Defender. Vous trouverez le [paramètre de protection contre les falsifications](../protect/endpoint-protection-windows-10.md#windows-defender-security-center) dans le groupe Centre de sécurité Microsoft Defender si vous utilisez des profils de configuration pour la protection des points de terminaison Windows 10. Vous pouvez définir la protection contre les falsifications sur *Activée* pour activer les restrictions de protection contre les falsifications, sur *Désactivée* pour la désactiver, ou sur *Non configurée* pour conserver la configuration actuelle des appareils.  

Pour plus d’informations sur la protection contre les falsifications, consultez [Empêcher les modifications des paramètres de sécurité avec la protection contre les falsifications](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) dans la documentation de Windows.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Les paramètres avancés pour le pare-feu Windows Defender sont maintenant à disponibilité générale<!--  5317392       -->  
Les [règles de pare-feu personnalisées Windows Defender pour la protection des points de terminaison](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) que vous configurez dans le cadre d’un profil de configuration d’appareil ne sont plus en préversion publique, mais à disponibilité générale.  Vous pouvez utiliser ces règles pour spécifier le comportement du trafic entrant et sortant avec les applications, les adresses réseau et les ports. Ces règles ont été publiées en juillet en préversion publique. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>Les balises d’étendue prennent désormais en charge les stratégies des conditions d’utilisation.<!-- 2358863 idmiss -->
Vous pouvez désormais assigner des [balises d’étendue](scope-tags.md) à des stratégies de conditions d’utilisation. Pour ce faire, accédez à **Intune** > **Inscription d’appareils** > **Conditions d’utilisation** > choisir un élément de la liste > **Propriétés** > **Balises d’étendue** > choisir une balise d’étendue.

## <a name="week-of-september-9-2019"></a>Semaine du 9 septembre 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Mise à jour de l’application Microsoft Intune<!-- 4997846 -->
L’application Microsoft Intune pour Android a été mise à jour avec les améliorations suivantes :
- Mise à jour et amélioration de la disposition pour inclure la navigation inférieure pour les actions les plus importantes.
- Ajout d’une page supplémentaire qui affiche le profil de l’utilisateur.
- Ajout de l’affichage des notifications actionnables dans l’application pour l’utilisateur, comme la nécessité de mettre à jour les paramètres de l’appareil.
- Ajout de l’affichage des notifications push personnalisées, alignant l’application sur la prise en charge récemment ajoutée dans les applications Portail d’entreprise pour iOS et Android. Pour plus d’informations, voir [Envoyer des notifications personnalisées dans Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>Pour les appareils iOS, personnalisez l’écran de confidentialité du processus d’inscription du Portail d’entreprise<!-- 4394993 -->
À l’aide de Markdown, vous pouvez personnaliser l’écran de confidentialité du Portail d’entreprise que les utilisateurs finaux voient lors de l’inscription à iOS. Plus précisément, vous serez en mesure de personnaliser la liste des éléments que votre organisation ne peut pas voir ou faire sur l’appareil. Pour plus d’informations, consultez [Guide pratique pour configurer l’application Portail d’entreprise Intune](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Semaine du 2 septembre 2019

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Mise à jour de l’interface utilisateur Intune - Tableau de bord État du locataire<!-- 5273210  -->
L’interface utilisateur du tableau de bord État du locataire a été mise à jour pour s’aligner sur les styles d’interface utilisateur d’Azure. Pour plus d’informations, consultez [État du locataire](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Semaine du 26 août 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Configurer les paramètres Microsoft Edge à l’aide de modèles d’administration pour Windows 10 et versions ultérieures<!-- 5228061 -->

Sur les appareils Windows 10 et versions ultérieures, vous pouvez créer des modèles d’administration pour configurer des paramètres de stratégie de groupe dans Intune. Dans cette mise à jour, vous pouvez configurer les paramètres qui s’appliquent à partir de la version 77 de Microsoft Edge.

Pour en savoir plus sur les modèles d’administration, consultez [Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Intune](../configuration/administrative-templates-windows.md).

S’applique à :

- Windows 10 et versions ultérieures (Windows RS4+)

## <a name="week-of-august-12-2019"></a>Semaine du 12 août 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Contrôler le comportement de désinstallation de l’application iOS lors de la désinscription de l’appareil<!-- 3504144   -->
Les administrateurs peuvent gérer si une application est supprimée ou conservée sur un appareil quand l’appareil est désinscrit au niveau d’un utilisateur ou d’un groupe d’appareils. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Catégoriser les applications du Microsoft Store pour Entreprises<!-- 3926922 -->
Vous pouvez catégoriser les applications du Microsoft Store pour Entreprises. Pour ce faire, sélectionnez **Intune** > **Applicationsclientes** > **Applications** > Sélectionnez une application du Microsoft Store pour Entreprises >  **Informations sur l’application** > **Catégorie**. Dans le menu déroulant, attribuez une catégorie.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Notifications personnalisées pour les utilisateurs de l’application Microsoft Intune<!-- 4843354  -->
L’application Microsoft Intune pour Android prend désormais en charge l’affichage des notifications push personnalisées, en l’alignant sur la prise en charge récemment ajoutée dans les applications Portail d’entreprise pour iOS et Android. Pour plus d’informations, voir [Envoyer des notifications personnalisées dans Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Nouvelles fonctionnalités pour les appareils dédiés Android Entreprise s’exécutant en mode plein écran multi-application<!-- 3755304 3041943 3041946   -->

Dans Intune, vous pouvez contrôler les fonctionnalités et les paramètres dans une expérience en mode plein écran sur vos appareils dédiés Android Enterprise (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour plateforme > **Propriétaire de l’appareil uniquement, restrictions sur l’appareil** pour le type de profil).

Dans cette mise à jour, les fonctionnalités suivantes sont ajoutées :

- **Périphériques dédiés** > **Multi-application** : Le **bouton d’accueil virtuel** peut être affiché en balayant sur l’appareil, ou en flottant sur l’écran pour que les utilisateurs puissent le déplacer.
- **Périphériques dédiés** > **Multi-application** : **L’accès à la lampe torche** permet aux utilisateurs d’utiliser la lampe torche. 
- **Périphériques dédiés** > **Multi-application** : Le **contrôle du volume du média** permet aux utilisateurs de contrôler le volume du média de l’appareil à l’aide d’un curseur. 
- **Périphériques dédiés** > **Multi-application** :  **Activer un économiseur d’écran**, télécharger une image personnalisée et contrôler quand l’économiseur d’écran est affiché.

Pour voir les paramètres actuels, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

S’applique à :

- Appareils dédiés Android Entreprise

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Nouveaux profils d’applications et de configuration pour les appareils Android Entreprise complètement managés<!-- 3574215 3574238 3574235 3574232   -->
À l’aide de profils, vous pouvez configurer des paramètres qui appliquent des paramètres VPN, d’e-mail et Wi-Fi à votre propriétaire d’appareil Android Enterprise (complètement managés). Dans cette mise à jour, vous pouvez :

- utiliser [des stratégies de configuration d’applications](../apps/app-configuration-policies-use-android.md) pour déployer des paramètres de messagerie Outlook, Gmail et Nine Work ;
- utiliser des profils de configuration d'appareil pour déployer des [paramètres de certificat racine approuvés](../protect/certificates-configure.md) ;
- utiliser des profils de configuration d'appareil pour déployer des paramètres [VPN](../configuration/vpn-settings-android-enterprise.md) et [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Cette fonctionnalité permet aux utilisateurs de s’authentifier avec leur nom d'utilisateur et leur mot de passe pour les profils VPN, Wi-Fi et d’e-mail. Actuellement, l’authentification basée sur des certificats n’est pas disponible.

S’applique à :  
- Propriétaire d’appareil Android Entreprise (complètement managé)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Contrôler les applications, les fichiers, les documents et les dossiers qui s’ouvrent quand les utilisateurs se connectent à des appareils macOS<!--3914202   -->
Vous pouvez activer et configurer des fonctionnalités sur des appareils macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Fonctionnalités de l’appareil** pour le type de profil). 

Dans cette mise à jour, il y a un nouveau paramètres Éléments de connexion pour contrôler quelles applications et quels fichiers, documents et dossiers s’ouvrent lorsqu’un utilisateur se connecte à l’appareil inscrit. 

Pour voir les paramètres actuels, accédez à [Paramètres des fonctionnalités d’appareil macOS dans Intune](../configuration/macos-device-features-settings.md).

S’applique à :  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Les délais remplacent des paramètres de redémarrage engagés pour les anneaux Windows Update<!-- 4464404        -->
Pour s’aligner sur [les modifications récentes des services de maintenance Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), les anneaux de mise à jour Windows 10 d’Intune prennent désormais en charge les [paramètres de prise en charge des délais](../protect/windows-update-settings.md). Les *délais* déterminent à quel moment un appareil installe les mises à jour de sécurité et de fonctionnalités.  Sur les appareils qui exécutent Windows 10 1903 ou une version ultérieure, les *délais* remplacent les configurations de *redémarrage engagé*.  À l’avenir, les *délais* remplaceront le *redémarrage engagé* sur les versions antérieures de Windows 10 également.  

Si vous ne configurez pas les *délais*, les appareils continuent d’utiliser leurs paramètres de *redémarrage commencé*. Cependant, Intune déconseillera la prise en charge des paramètres de redémarrage commencé dans une future mise à jour.  

Prévoyez d’utiliser des *délais* pour tous vos appareils Windows 10. Après la mise en place des paramètres des *délais*, vous pouvez modifier vos configurations Intune pour que le *redémarrage engagé* ne soit pas configuré. Lorsqu’il n’est pas configuré, Intune arrête de gérer ces paramètres sur les appareils, mais ne supprime pas les dernières configurations du paramètre de l’appareil. Pour cette raison, les dernières configurations définies pour le *redémarrage engagé* restent actives et sont utilisées sur les appareils jusqu’à ce que ces paramètres soient modifiés par une méthode autre qu’Intune. Plus tard, lorsque la version des appareils Windows changera que la prise en charge des *délais* par Intune s’étendra à la version Windows des appareils, l’appareil commencera à utiliser les nouveaux paramètres, qui sont déjà en place.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Prendre en charge plusieurs connecteurs de certificats Microsoft Intune<!--   4704642      -->
Intune prend désormais en charge l’installation et l’utilisation de plusieurs [connecteurs de certificats Microsoft Intune pour les opérations PKCS](../protect/certficates-pfx-configure.md). Ceci modifie l’équilibrage de charge et la haute disponibilité du connecteur. Chaque instance de connecteur peut traiter les demandes de certificat d’Intune.  Si un connecteur n’est pas disponible, d’autres connecteurs continuent de traiter les demandes.

Pour utiliser plusieurs connecteurs, vous n’avez pas besoin de procéder à une mise à niveau vers la dernière version du logiciel connecteur.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Nouveaux paramètres et modifications apportées aux paramètres existants pour restreindre les fonctionnalités sur les appareils iOS et macOS<!-- 4867699 4867709   -->
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

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Certaines restrictions sur les appareils iOS non supervisés seront supervisées uniquement avec la version iOS 13.0.<!-- 4867809   -->
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

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Amélioration de l’état des appareils pour le chiffrement FileVault macOS<!-- 4944983         -->
Nous avons mis à jour plusieurs [messages d’état de l’appareil](../protect/encryption-monitor.md#device-encryption-status) pour le chiffrement FileVault sur les appareils MacOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Certains paramètres d’analyse de l’antivirus Windows Defender dans le rapport indiquent un état d’échec<!-- 5119229 -->
Dans Intune, vous pouvez créer des stratégies afin d’utiliser l’antivirus Windows Defender pour analyser vos appareils Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** pour plateforme > **Restrictions sur l’appareil** pour type de profil > **Antivirus Windows Defender**). Les rapports sur la **durée d’exécution d’une analyse quotidienne rapide** et le **type d’analyse système à effectuer** indique un état d’échec lorsqu’il s’agit en fait d’un état de réussite. 

Dans cette mise à jour, ce comportement est corrigé. Ainsi, les paramètres **Durée d’exécution d’une analyse quotidienne rapide** et **Type d’analyse système à effectuer** montrent un état de réussite lorsque l’analyse est terminée et un état d’échec lorsque les paramètres ne sont pas appliqués.

Pour plus d’informations sur les paramètres de l’antivirus Windows Defender, consultez [Paramètres de l’appareil Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="default-scope-tags---3702875----"></a>Balises de portée par défaut<!-- 3702875  -->
Une nouvelle balise d’étendue par défaut intégrée est désormais disponible. Tous les objets Intune sans balise qui prennent en charge des balises d’étendue sont automatiquement attribués à la balise d’étendue par défaut. La balise d’étendue **par défaut** est ajoutée à toutes les attributions de rôles existantes pour maintenir la parité avec l’expérience d’administration actuelle. Si vous ne souhaitez pas qu’un administrateur voit les objets Intune avec la balise d’étendue par défaut, supprimez la balise d’étendue par défaut de l’attribution de rôle. Cette fonctionnalité est similaire à la fonctionnalité des étendues de sécurité de System Center Configuration Manager. Pour plus d’informations, voir [Use RBAC and scope tags for distributed IT](scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Support de l’administrateur d’appareil d’inscription Android<!-- 4869749   -->
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

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Ajouter une colonne utilisateur au processus de chargement CSV d’un appareil Autopilot<!-- 3823054 -->
Vous pouvez maintenant ajouter une colonne utilisateur au téléchargement CSV pour les appareils Autopilot. Ceci vous permet d’affecter des utilisateurs en bloc au moment où vous importez le volume partagé de cluster. Pour plus d’informations, consultez [Inscrire des appareils Windows dans Intune avec Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Gestion des appareils

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Configurer une limite de temps de nettoyage automatique des appareils réduite à 30 jours<!--4231059  -->
Vous pouvez définir la limite de temps de nettoyage automatique des appareils sur 30 jours (au lieu de la limite précédente de 90 jours) après la dernière connexion. Pour ce faire, accédez à **Intune** > **Appareils** > **Configuration** > **Règles de nettoyage des appareils**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Numéro de build inclus sur la page Matériel du périphérique Android<!-- 4461910   -->
Une nouvelle entrée sur la page Matériel de chaque appareil Android inclut le numéro de build du système d’exploitation de l’appareil. Pour plus d’informations, consultez [Afficher les détails de l’appareil dans Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Semaine du 5 août 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies est un OEM pris en charge pour OEMConfig sur les appareils Android Entreprise<!-- 4843713 -->

Dans Intune, vous pouvez créer des profils de configuration d’appareils et appliquer des paramètres à des appareils Android Entreprise à l’aide d’OEMConfig (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Entreprise** pour la plateforme > **OEMConfig** pour le type de profil).

Dans cette mise à jour, Zebra Technologies est un fabricant d’ordinateurs OEM pris en charge pour OEMConfig. Pour plus d’informations sur OEMConfig, consultez [Utilisation et gestion des appareils Android Entreprise avec OEMConfig](../configuration/android-oem-configuration-overview.md).

S’applique à :  
- Android Entreprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Semaine du 22 juillet 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Notifications personnalisées destinées aux groupes et aux utilisateurs<!-- 16766574          -->
Depuis l’application Portail d’entreprise, envoyez des notifications push personnalisées aux utilisateurs, sur les appareils iOS et Android que vous gérez avec Intune. Ces notifications push mobiles sont hautement personnalisables, avec du texte libre, et peuvent être utilisées pour n’importe quel motif. Vous pouvez les cibler sur différents groupes d’utilisateurs de votre organisation. Pour en savoir plus, voir [Envoyer des notifications personnalisées dans Intune](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Application du contrôleur de stratégie d’appareil de Google<!-- 3041950  -->
L’application Managed Home Screen permet désormais d’accéder à l’application Android Device Policy de Google. L’application Managed Home Screen est un lanceur personnalisé utilisé pour les appareils inscrits dans Intune en tant qu’appareils dédiés Android Enterprise (AE) utilisant le mode kiosque multi-application. Vous pouvez accéder à l’application Android Device Policy ou guider les utilisateurs vers cette application à des fins de support et de débogage. Cette fonctionnalité de lancement est disponible au moment de l’inscription et du verrouillage de l’appareil dans Managed Home Screen. Aucune installation supplémentaire n’est nécessaire pour utiliser cette fonctionnalité.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Paramètres de protection Outlook pour les appareils iOS et Android<!-- 3212619 -->
Vous pouvez maintenant configurer les paramètres généraux de configuration de la protection des données et des applications pour Outlook sur iOS et Android, en utilisant des contrôles d’administration Intune simples, sans inscription d’appareil. Les paramètres de configuration d’application généraux fournissent la parité avec les paramètres que les administrateurs peuvent activer lors de la gestion de Microsoft Outlook pour iOS et Android sur des appareils inscrits. Pour plus d’informations sur les paramètres Outlook, voir [Déploiement des paramètres de configuration d’une application Outlook pour iOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Utilisez « règles d’applicabilité » lors de la création de profils de configuration d’appareil Windows 10 <!-- 2549910 eeready   idstaged -->

Vous créez des profils de configuration d’appareil Windows 10 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme > **Règles de mise en application**). Vous serez en mesure de créer une **règle d’applicabilité** pour que le profil s’applique seulement à une édition ou version spécifique. Par exemple, vous créez un profil qui active certains paramètres de BitLocker. Une fois que vous avez ajouté le profil, utilisez une règle d’applicabilité pour que le profil s’applique seulement aux appareils exécutant Windows 10 Entreprise.

Pour savoir comment ajouter une règle d’applicabilité, voir [Règles de mise en application](../configuration/device-profile-create.md#applicability-rules).

S’applique à : Windows 10 et versions ultérieures

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Utiliser des jetons pour ajouter des informations spécifiques à l’appareil dans des profils personnalisés pour les appareils iOS et macOS<!-- 3330008  -->
Vous pouvez utiliser des profils personnalisés sur des appareils iOS et macOS pour configurer des paramètres et des fonctionnalités non intégrés à Intune (**Configuration des appareils** > **Profils** > **Créer un profil** > **iOS** ou **macOS** pour la plate-forme > **Personnalité** pour le type de profil). Dans cette mise à jour, vous pouvez ajouter des jetons dans vos fichiers `.mobileconfig` pour ajouter des informations spécifiques à l’appareil. Par exemple, vous pouvez ajouter `Serial Number: {{serialnumber}}` à votre fichier de configuration pour afficher le numéro de série de l’appareil.

Pour créer un profil personnalisé, voir [Utiliser des paramètres personnalisés pour les appareils macOS dans Microsoft Intune](../configuration/custom-settings-ios.md) ou [Utiliser des paramètres personnalisés pour les appareils iOS dans Microsoft Intune](../configuration/custom-settings-macos.md).

S’applique à :
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Nouveau concepteur de configuration lors de la création d’un profil OEMConfig pour Android Enterprise<!-- 3712769   -->
Dans Intune, vous pouvez créer un profil de configuration d’appareil qui utilise une application OEMConfig (Configuration des appareils > Profils > Créer un profil > Android Enterprise pour la plateforme > OEMConfig pour le type de profil). Dans ce cas, un éditeur JSON s’ouvre avec un modèle et des valeurs, que vous pouvez modifier. 

Cette mise à jour inclut un concepteur de configuration, qui offre une expérience utilisateur améliorée grâce à l’affichage des détails incorporés dans l’application, y compris des titres et des descriptions. L’éditeur JSON reste disponible. Il affiche toutes les modifications que vous apportez dans le concepteur de configuration.

Pour connaître les paramètres actuels, consultez la section relative à [l’utilisation et la gestion des appareils Android Enterprise avec OEMConfig](../configuration/android-oem-configuration-overview.md).

S’applique à : Android Entreprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Interface utilisateur mise à jour pour la configuration de Windows Hello<!-- 4089576            -->
Nous avons mis à jour la console dans laquelle vous [ configurez Intune pour l’utilisation de Windows Hello Entreprise.](../protect/windows-hello.md) Tous les paramètres de configuration sont désormais disponibles dans le volet de la console dans lequel vous activez la prise en charge de Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>Kit de développement logiciel (SDK) PowerShell Intune<!-- 4924113 --> 
Le Kit de développement logiciel (SDK) Intune PowerShell, qui prend en charge l’API Intune via Microsoft Graph, a été mis à jour vers la version 6.1907.1.0. Ce Kit prend désormais en charge les éléments suivants :
- Il gère Azure Automation.
- Il prend en charge les opérations de lecture d’authentification pour l’application uniquement. 
- Il prend en charge les noms abrégés conviviaux en tant qu’alias.
- Il respecte les conventions d’affectation de noms de PowerShell. Plus précisément, le paramètre `PSCredential` (sur la cmdlet `Connect-MSGraph`) a été renommé comme suit : `Credential`.
- Il prend en charge la spécification manuelle de la valeur de l’en-tête `Content-Type` lors de l’utilisation de la cmdlet `Invoke-MSGraphRequest`.

Pour en savoir plus, consultez la section relative au [Kit de développement logiciel (SDK) pour l’API Graph de Microsoft Intune](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Mises à jour relatives aux restrictions d’inscription<!-- 2871968 -->
Les restrictions d’inscription pour les nouveaux locataires ont été mises à jour afin que les profils de travail Android Enterprise soient autorisés par défaut. Les locataires existants ne sont pas modifiés. Pour utiliser les profils de travail Android Enterprise, vous devez tenter de [connecter votre compte Intune à votre compte Google Play managé](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Mises à jour de l’interface utilisateur pour les restrictions d’inscription et les inscriptions Apple<!--4089575, 4089579  -->
Les deux processus suivants utilisent une interface utilisateur de style Assistant :
- Inscription d’appareils Apple. Pour en savoir plus, voir [Inscrire automatiquement des appareils iOS avec le Programme d’inscription des appareils d’Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Création de restrictions d’inscription. Pour en savoir plus, consultez la section relative à la [définition de restrictions d’inscription](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Gestion de la préconfiguration des identificateurs d’appareils d’entreprise pour les appareils Android Q<!-- 4711509  idmiss -->
Dans Android Q (V10), Google supprime la capacité des agents MDM sur les appareils Android managés par des appareils Android existants (administrateur d’appareil) à collecter des informations sur les identificateurs d’appareil.  Intune propose une fonctionnalité pour permettre aux administrateurs informatiques de [préconfigurer une liste de numéros de série d’appareil, ou IMEI,](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) de façon à baliser ces appareils automatiquement, en tant que propriété d’entreprise. Cette fonctionnalité ne fonctionne pas pour les appareils Android Q managés par l’administrateur d’appareils.  Que vous chargiez le numéro de série ou le numéro IMEI de l’appareil, ce dernier est toujours considéré comme personnel lors de l’inscription dans Intune.  Vous pouvez basculer manuellement la propriété vers l’entreprise après l’inscription.  Cela affecte uniquement les nouvelles inscriptions.  Les appareils Android managés avec des profils de travail ne sont pas affectés par cette modification et continuent de fonctionner comme ils le font aujourd’hui.  En outre, les appareils Android Q inscrits en tant qu’administrateurs de l’appareil ne pourront plus signaler le numéro de série ou IMEI en tant que propriétés de l’appareil dans la console Intune.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Les icônes associées aux inscriptions Android Entreprise ont été modifiées (profil de travail, appareils dédiés ou appareils entièrement managés)<!-- 4977730 -->
Les icônes des profils d’inscription d’Android Entreprise ont été modifiées. Pour afficher les nouvelles icônes, accédez à **Intune** > **Inscription** > **Inscription Android** > et cherchez dans **Profils d’inscription**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Modification relative à la collection de données de diagnostic Windows<!-- 4113859 -->
La valeur par défaut de la collection de données de diagnostic a changé pour les appareils exécutant Windows 10, version 1903 et versions ultérieures. À compter de Windows 10 version 1903, la collection des données de diagnostic est activée par défaut. Les données de diagnostic Windows sont des données techniques vitales des appareils Windows. Elles portent sur ces derniers et indiquent les performances de Windows et d’autres logiciels associés. Pour plus d’informations, consultez [Configurer les données de diagnostic Windows dans votre organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Les appareils AutoPilot ont également opté pour la télémétrie « complète », sauf indication contraire dans le profil Autopilot avec [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestion des appareils

#### <a name="improve-device-location---3855417----"></a>Améliorer la localisation d’appareils<!-- 3855417  -->
Vous pouvez effectuer un zoom avant sur les coordonnées exactes d’un appareil à l’aide de l’action **Localiser l’appareil**. Pour plus d’informations sur la localisation d’appareils iOS perdus, consultez la section relative à la [recherche d’appareils iOS perdus](../remote-actions/device-locate.md).

### <a name="device-security"></a>Sécurité des appareils

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Paramètres avancés pour le pare-feu Windows Defender (préversion publique)<!--  1311949     -->  
Utilisez Intune afin de gérer [des règles de pare-feu personnalisées dans le cadre d’un profil de configuration d’appareil](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) pour la protection des terminaux sur Windows 10. Les règles peuvent spécifier le comportement du trafic entrant et sortant avec les applications, les adresses réseau et les ports. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Interface utilisateur mise à jour pour la gestion des bases de référence de la sécurité<!-- 4091125     -->
Nous avons mis à jour [l’expérience de création et de modification](../protect/security-baselines.md#create-the-profile) dans la console Intune pour nos bases de référence de la sécurité. Ces modifications sont notamment :

Un format de style Assistant plus simple, condensé au sein d’un même panneau. Cette nouvelle conception met un terme à la prolifération des panneaux, qui oblige les professionnels de l’informatique à parcourir plusieurs volets distincts.  
Vous pouvez maintenant créer des affectations dans le cadre de l’expérience de création et de modification, au lieu de devoir affecter des bases de référence ultérieurement. Nous avons ajouté une synthèse des paramètres que vous pouvez afficher avant de créer une base de référence et d’en modifier une. Lors de la modification, la synthèse affiche uniquement la liste des éléments définis dans une catégorie de propriétés en cours de modification.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Semaine du 15 juillet 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Icônes Managed Home Screen et Managed Settings<!-- 4918107 -->
L’icône Managed Home Screen et celle des **paramètres managés** ont été mises à jour. L’application Managed Home Screen est uniquement utilisée pour les appareils inscrits dans Intune, en tant qu’appareils dédiés Android Enterprise (AE) qui exécutent le mode kiosque multi-application. Pour en savoir plus sur l’application Managed Home Screen, voir [Configurer l’application Microsoft Managed Home Screen pour Android Entreprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Device Policy sur des appareils Android Enterprise dédiés<!-- 4918136 -->
Vous pouvez accéder à l’application Android Device Policy à partir de l’écran de débogage de l’application Managed Home Screen. L’application Managed Home Screen est uniquement utilisée pour les appareils inscrits dans Intune, en tant qu’appareils dédiés Android Enterprise (AE) qui exécutent le mode kiosque multi-application. Pour en savoir plus, voir [Configurer l’application Microsoft Managed Home Screen pour Android Entreprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>Mises à jour du Portail d’entreprise iOS<!-- 3902931 -->
Le nom de votre société sur les invites de gestion des applications iOS remplace le texte « i.manage.microsoft.com » en cours. Par exemple, les utilisateurs verront le nom de leur société au lieu de « i.manage.microsoft.com » lorsque les utilisateurs tenteront d’installer une application iOS à partir du Portail d’entreprise ou lorsque les utilisateurs autorisent la gestion de l’application. Elle sera déployée pour tous les clients au cours des prochains jours.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Gérer FileVault pour macOS<!--  3858502 + 4557986 + 1210104  -->
Vous pouvez utiliser Intune pour [gérer le chiffrement de clé FileVault pour les appareils macOS](../protect/encrypt-devices.md). Pour chiffrer des appareils, vous pouvez utiliser un profil de configuration de protection des points de terminaison.

La prise en charge de FileVault inclut le chiffrement des appareils non chiffrés, le dépôt de la clé (escrow) de récupération personnelle des appareils, la rotation automatique ou manuelle des clés de chiffrement personnelles et la récupération des clés pour vos appareils d’entreprise. Les utilisateurs finaux peuvent également utiliser le site Web Portail d’entreprise pour obtenir la clé de récupération personnelle de leurs appareils chiffrés.

Nous avons également développé le rapport sur le chiffrement de façon à inclure des [informations sur FileVault](../protect/encryption-monitor.md) avec des informations pour BitLocker, afin que vous puissiez afficher l’ensemble des détails sur le chiffrement d’appareils depuis un endroit centralisé.

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>La réinitialisation automatique de Windows AutoPilot supprime l’utilisateur principal de l’appareil<!-- 4156123 -->
Lorsque le logiciel Autopilot est utilisé sur un appareil, l’utilisateur principal de l’appareil sera supprimé. L’utilisateur suivant qui se connecte après la réinitialisation est défini en tant qu’utilisateur principal. Cette fonction sera déployée pour tous les clients au cours des jours suivants.

## <a name="week-of-july-8-2019"></a>Semaine du 8 juillet 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nouveaux paramètres Office, Windows et OneDrive dans les modèles d’administration Windows 10 <!-- 3510695 -->

Vous pouvez créer des modèles d’administration dans Intune qui imitent la gestion de stratégies de groupe locale (**Gestion des appareils** > **Profils** > **Créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Modèles d’administration** pour le type de profil).

Cette mise à jour inclut davantage de paramètres Office, Windows et OneDrive, que vous pouvez ajouter à vos modèles. Grâce à ces nouveaux paramètres, vous pouvez désormais configurer plus de 2 500 paramètres entièrement basés sur le Cloud.

Pour plus d’informations sur cette fonctionnalité, voir [Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Microsoft Intune](../configuration/administrative-templates-windows.md).

S’applique à : Windows 10 et versions ultérieures

## <a name="week-of-july-1-2019"></a>Semaine du 1 juillet 2019 

### <a name="app-management"></a>Gestion d'applications

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD et APP sur des appareils Android Enterprise<!-- 3574267 -->
Lors de l’intégration d’appareils Android Enterprise entièrement managés, les utilisateurs peuvent s’inscrire auprès de Microsoft Active Directory (AAD) lors de la configuration initiale de leur nouvel appareil ou de leur appareil sur lequel les paramètres d’usine ont été rétablis. Auparavant, une fois la configuration d’un appareil entièrement managé terminée, l’utilisateur doit gérer manuellement l’application Microsoft Intune pour démarrer l’inscription auprès d’AAD. Désormais, lorsque l’utilisateur se trouve sur la page d’origine de l’appareil après la configuration initiale, l’appareil est inscrit et enregistré.

Outre les mises à jour d’AAD, les stratégies Intune App Protection (APP) sont désormais prises en charge sur les appareils Android Enterprise entièrement managés. Cette fonctionnalité sera disponible lors du lancement. Pour en savoir plus, voir [Ajouter des applications Google Play managé à des appareils d’entreprise Android avec Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Semaine du 24 juin 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Configurer le navigateur qui est autorisé à établir une liaison aux données de l’organisation<!-- 3145939 -->
Les stratégies Intune App Protection (APP) sur les appareils Android et iOS vous permettent de transférer des liens web de l’organisation vers un navigateur spécifique au-delà de Microsoft Intune Managed Browser ou de Microsoft Edge.  Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>La page Toutes les applications identifie les applications MSFB comme étant en ligne ou hors ligne<!--4089647 -->
La page **Toutes les applications** inclut désormais des étiquettes permettant d’identifier les applications Microsoft Store for Business (MSFB) comme étant hors ligne ou en ligne. Chaque application MSFB comprend désormais un suffixe indiquant qu’elle est **en ligne** ou **hors ligne**. La page Détails de l’application comprend également des informations sur le **type de licence** et la **prise en charge de l’installation de contextes d’appareil** (uniquement les applications sous licence hors ligne).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Application Portail d’entreprise sur les appareils Windows partagés<!--4393553 -->
Les utilisateurs peuvent désormais accéder à l’application Portail d’entreprise sur des appareils Windows partagés. Les utilisateurs finaux verront apparaître l’étiquette **Partagé** sur la mosaïque de l’appareil. Cela s’applique à la version de l’application Portail d’entreprise 10.3.45609.0 de Windows, ainsi que les versions ultérieures.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Afficher toutes les applications dans la nouvelle page Portail d’entreprise<!-- 4224326 -->
La page **Applications installées** du portail d’entreprise liste toutes les applications gérées (obligatoires ou disponibles) qui sont installées sur l’appareil d’un utilisateur. En plus du type d’affectation, les utilisateurs peuvent voir l’éditeur de l’application, sa date de publication et son état actuel d’installation. Si aucune application n’est obligatoire ou disponible, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Pour afficher la nouvelle page sur le Web, accédez au [site web Portail d’entreprise](https://portal.manage.microsoft.com), puis cliquez sur **Applications installées**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>La nouvelle vue permet aux utilisateurs de l’application de voir toutes les applications gérées qui sont installées sur l’appareil<!-- 2352913 -->  
L’application Portail d’entreprise pour Windows liste désormais toutes les applications gérées (obligatoires ou disponibles), qui sont installées sur l’appareil d’un utilisateur. Les utilisateurs peuvent également voir les installations d’applications tentées et en attente, ainsi que leur état actuel. Si aucune application n’est obligatoire ou disponible, les utilisateurs verront un message expliquant qu’aucune application d’entreprise n’a été installée. Pour afficher la nouvelle vue, dans le volet de navigation du portail d’entreprise, sélectionnez **Applications** > **Applications installées**.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Configurer les paramètres pour les extensions de noyau sur les appareils macOS<!-- 2043024 -->
Sur les appareils macOS, vous pouvez créer un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > choisissez **macOS** pour la plateforme). Cette mise à jour inclut un nouveau groupe de paramètres permettant de configurer et d’utiliser les extensions de noyau sur vos appareils. Vous pouvez ajouter des extensions spécifiques ou autoriser toutes les extensions d’un partenaire ou d’un développeur spécifique.

Pour en savoir plus sur cette fonctionnalité, consultez la [vue d’ensemble des extensions de noyau](../configuration/kernel-extensions-overview-macos.md) et [les paramètres des extensions de noyau](../configuration/kernel-extensions-settings-macos.md).

S’applique à : macOS 10.13.2 et versions ultérieures

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Le paramètre Applications du Store uniquement pour les appareils Windows 10 inclut des options de configuration supplémentaires<!-- 2697002 -->
Quand vous créez un profil de restrictions d’appareil pour les appareils Windows, vous pouvez utiliser le paramètre **Applications du Store uniquement** afin que les utilisateurs installent uniquement des applications de l’App Store Windows (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** comme plateforme > **Restrictions sur l’appareil** comme type de profil). Dans cette mise à jour, ce paramètre est développé pour prendre en charge davantage d’options.

Pour consulter le paramètre actuel, voir [Paramètres des appareils Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités dans Intune](../configuration/device-restrictions-windows-10.md#app-store).

S’applique à : Windows 10 et versions ultérieures

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Déployez plusieurs profils d’appareils Extensions de mobilité Zebra sur un appareil, sur le même groupe d’utilisateurs ou sur le même groupe d’appareils<!-- 4089955 -->
Dans Intune, vous pouvez utiliser des Extensions de mobilité Zebra (MX) dans un profil de configuration d’appareil pour personnaliser des paramètres d’appareils Zebra non intégrés à Intune. Actuellement, vous pouvez déployer un profil sur un seul appareil. Dans cette mise à jour, vous pouvez déployer plusieurs profils pour :
- Le même groupe d’utilisateurs
- Le même groupe d’appareils
- Un seul appareil

[Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Microsoft Intune](../configuration/android-zebra-mx-overview.md) montre comment utiliser MX dans Intune.

S’applique à : Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Certains paramètres kiosque sur les appareils iOS sont définis avec « Bloquer » à la place de « Autoriser »<!-- 4404075  -->
Quand vous créez un profil de restrictions d’appareil sur des appareils iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions sur l’appareil** comme type de profil > **Kiosque**), vous définissez le **Verrouillage automatique**, la **Modification de sonnerie**, la **Rotation de l'écran**, le **Bouton de veille de l’écran** et les **Boutons de volume**.

Dans cette mise à jour, les valeurs sont **Bloquer** (pour bloquer la fonctionnalité) ou **Non configuré** (pour autoriser la fonctionnalité). Pour consulter les paramètres, accédez à la section [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md#kiosk).

S’applique à : iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Utiliser Face ID pour l’authentification par mot de passe sur les appareils iOS<!-- 4490704 -->
Quand vous créez un profil de restrictions d’appareil pour les appareils iOS, vous pouvez utiliser une empreinte digitale comme mot de passe. Dans cette mise à jour, les paramètres de mot de passe par empreinte digitale autorisent également la reconnaissance faciale (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions sur l’appareil** comme type de profil > **Mot de passe**). Par conséquent, les paramètres suivants sont modifiés :

- **Déverrouillage par empreinte digitale** est désormais **Déverrouillage de Touch ID et Face ID**.
- **Modification de l’empreinte digitale (supervisé uniquement)** est désormais **Modification de Touch ID et Face ID (supervisé uniquement)** .

Face ID est disponible dans iOS 11.0 et versions ultérieures. Pour consulter les paramètres, voir [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md#password).

S’applique à : iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Les restrictions appliquées aux fonctionnalités de l’App Store et de jeu sur les appareils iOS dépendent désormais de la région de classification<!-- 4593948 -->
Dans les appareils iOS, vous pouvez autoriser ou restreindre les fonctionnalités liées au jeu, à l’App Store et à l’affichage de documents (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** comme plateforme > **Restrictions sur l’appareil** comme type de profil > **App Store, affichage de documents, jeux**). Vous pouvez également choisir la région des classifications ; par exemple, les États-Unis.

Dans cette mise à jour, la fonctionnalité **Applications** est devenue un enfant de **Région des classifications** et dépend de **Région des classifications**. Pour consulter les paramètres, voir [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

S’applique à : iOS

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Prise en charge de la jonction Azure AD Hybride par Windows AutoPilot<!-- 4809146-->
La version de Windows Autopilot pour les appareils existants prend désormais en charge la jonction Azure AD Hybride (en plus de la prise en charge de la fonction Jonction Azure AD). S’applique aux appareils Windows 10 version 1809 et versions ultérieures. Pour en savoir plus, voir [Windows Autopilot pour les appareils existants](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Gestion des appareils

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Voir le niveau du correctif de sécurité pour les appareils Android<!-- 4461911 -->
Vous pouvez désormais afficher le niveau du correctif de sécurité pour les appareils Android. Pour ce faire, choisissez **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil > **Matériel**.
Le niveau de correctif est indiqué dans la section **Système d’exploitation**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Affecter des balises d’étendue à tous les appareils gérés d’un groupe de sécurité<!-- 3173810 -->
Vous pouvez maintenant affecter des balises d’étendue à un groupe de sécurité et tous les appareils qu’il contient sont également associés à ces balises. La balise d’étendue sera également affectée à tous les appareils présents dans ces groupes. Les balises d’étendue définies avec cette fonctionnalité remplacent les balises d’étendue définies avec le flux actuel de balises d’étendue d’appareil. Pour en savoir plus, voir [Use RBAC and scope tags for distributed IT](scope-tags.md) (Utiliser RBAC et des balises d’étendue pour l’informatique distribuée).

### <a name="device-security"></a>Sécurité des appareils

#### <a name="use-keyword-search-with-security-baselines------"></a>Utiliser la recherche par mot clé avec les bases de référence de la sécurité<!--  -->
Lorsque vous créez ou modifiez des [profils de base de référence de la sécurité](../protect/security-baselines.md#create-the-profile), vous pouvez spécifier des mots clés dans la nouvelle barre *Rechercher* pour filtrer les groupes de paramètres disponibles sur ceux qui contiennent vos critères de recherche.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>La fonctionnalité Bases de référence de sécurité est désormais disponible en général<!-- 3785395 -->
La fonctionnalité **Bases de référence de sécurité** n’est plus en préversion et est en disponibilité générale.  Cela signifie que la fonctionnalité est prête à être utilisée en production. Toutefois, les modèles de base de référence peuvent rester en préversion et être évalués ; ils passent en disponibilité générale au cas par cas.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>Le modèle Base de référence de sécurité MDM est en disponibilité générale<!-- 3794072, 4217151,  3534649 -->
Le modèle Base de référence de sécurité MDM n’est plus en préversion et est en disponibilité générale. Le modèle en disponibilité générale est identifié en tant que **base de référence de sécurité MDM pour mai 2019**.  Il s’agit d’un nouveau modèle, et non d’une mise à niveau à partir de la préversion.  En tant que nouveau modèle, vous devez vérifier les [paramètres qu’il contient](../protect/security-baseline-settings-mdm.md), puis créer des profils pour déployer le modèle sur votre appareil. D’autres modèles de base de référence de sécurité peuvent rester en préversion. Pour obtenir la liste des bases de référence de sécurité disponibles, voir [Bases de référence de la sécurité disponibles](../protect/security-baselines.md#available-security-baselines).  

Outre le fait qu’il s’agit d’un nouveau modèle, le modèle *Base de référence de sécurité MDM pour mai 2019* comprend les deux paramètres que nous avons récemment annoncés dans notre article dans le développement :  
- Au-dessus du verrouillage : activation vocale des applications à partir d’un écran verrouillé  
- DeviceGuard : utilisation de la sécurité basée sur la virtualisation au prochain redémarrage de l’appareil.  

Le modèle *Base de référence de sécurité MDM pour mai 2019* comprend également l’ajout de plusieurs nouveaux paramètres, la suppression d’autres paramètres et une révision de la valeur par défaut d’un paramètre. Pour obtenir une liste détaillée des modifications apportées de la préversion à la mise en disponibilité générale, voir **Ce qui a changé dans le nouveau modèle**.

#### <a name="security-baseline-versioning---3194322---"></a>Bases de référence de la sécurité pour le contrôle de version<!-- 3194322 -->
Bases de référence de la sécurité pour le contrôle de version dans Intune. Avec cette prise en charge, au fur et à mesure que de nouvelles versions de chaque base de référence de la sécurité sont publiées, vous pouvez mettre à jour vos profils de base de référence de la sécurité existants pour utiliser la nouvelle version et ce, sans avoir à recréer et à déployer une nouvelle base. En outre, dans la console Intune, vous pouvez afficher des informations sur chaque base de référence de la sécurité, comme le nombre de profils individuels qui l’utilisent, le nombre de versions de bases différentes utilisées par vos profils et la date de la dernière version d’une base de référence de la sécurité.  Pour en savoir plus, consultez la section relative aux **bases de référence de la sécurité**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>Le paramètre Utilisez des clés de sécurité pour la connexion a été déplacé<!-- 4501151 -->
Le paramètre de configuration d’appareil relatif à la protection des identités appelé **Utilisez des clés de sécurité pour la connexion** n’est plus un sous-paramètre de *Configurer Windows Hello Entreprise*. Il s’agit désormais d’un paramètre de niveau supérieur qui est toujours disponible, même lorsque vous n’activez pas l’utilisation de Windows Hello Entreprise. Pour en savoir plus, consultez la section relative à la [protection des identités](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>De nouvelles autorisations pour les administrateurs de groupe affectés<!-- 4504437   -->
Le rôle d’administrateur scolaire intégré d’Intune dispose désormais d’autorisations de création, de lecture, de mise à jour et de suppression (CRUD) pour les applications managées. Suite à cette mise à jour, si vous êtes affecté en tant qu’administrateur de groupe dans Intune Éducation, vous pouvez désormais créer, afficher, mettre à jour et supprimer le certificat Push MDM iOS, les jetons de serveur MDM iOS et les jetons VPP iOS, ainsi que [toutes les autorisations existantes dont vous disposez](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Pour effectuer l’une de ces actions suivantes, accédez à **Paramètres du client** > **Gestion des appareils iOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Les applications peuvent utiliser l’API Graph pour appeler des opérations de lecture sans informations d’identification de l’utilisateur<!-- 4655885 -->
Les applications peuvent appeler des opérations de lecture d’API Graph Intune avec leur identité sans informations d’identification d’utilisateur. Pour en savoir plus sur l’accès à l’API Microsoft Graph API pour Intune, consultez la section relative à [l’utilisation d’Intune dans Microsoft Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Application de balises d’étendue aux applications Microsoft Store for Entreprises<!-- 4392555 -->
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

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Nouveaux exemples d’applications illustrant l’intégration du kit de développement logiciel (SDK) Intune disponible sur GitHub<!-- 2653471 -->
Le compte GitHub msintuneappsdk a ajouté de nouveaux exemples d'application pour iOS (Swift), Android, Xamarin.iOS, Xamarin Forms et Xamarin.Android. Ces applications sont censées remplacer notre documentation existante et fournir des exemples d’intégration du kit de développement logiciel (SDK) de l’application Intune dans vos propres applications mobiles. Si vous êtes développeur d’applications et que vous avez besoin de conseils supplémentaires concernant le kit de développement logiciel (SDK) Intune, consultez les exemples liés :
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) : une application de messagerie instantanée iOS native (Swift) qui utilise la bibliothèque d'authentification Azure Active Directory (ADAL) pour l’authentification répartie.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) : une application Android native de listes de tâches à effectuer qui utilise la bibliothèque d'authentification Active Directory pour l’authentification répartie.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) : application Xamarin.Android de listes de tâches à effectuer qui utilise la bibliothèque d'authentification Active Directory pour l’authentification répartie. Ce référentiel contient également l’application Xamarin.Forms.
- [Exemple d’application Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) : un exemple d’application « barebones ».

## <a name="week-of-may-27-2019"></a>Semaine du 27 mai 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Création de rapports pour les applications potentiellement dangereuses sur les appareils Android<!-- 4223162 -->
Intune fournit désormais des informations supplémentaires sur la création de rapports pour les applications potentiellement dangereuses sur les appareils Android. 

## <a name="week-of-may-20-2019"></a>Semaine du 20 mai 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="windows-company-portal-app---3316993---"></a>Application Portail d’entreprise Windows<!-- 3316993 -->
L’application Portail d’entreprise Windows a désormais une nouvelle page intitulée **Appareils**. La page **Appareils** montre aux utilisateurs finaux tous leurs appareils inscrits. Les utilisateurs voient cette modification dans le portail d’entreprise dès lors qu’ils utilisent la version 10.3.4291.0 et ultérieure. Pour plus d’informations sur la configuration du portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nom de l’attribut OrderID des appareils Autopilot changé en Balise de groupe <!-- 4659453 -->

Pour le rendre plus intuitif, le nom de l’attribut **OrderID** sur les appareils Autopilot est devenu **Balise de groupe**. Quand vous utilisez des fichiers CSV pour charger les informations des appareils Autopilot, vous devez utiliser Balise de groupe comme en-tête de colonne, et non plus OrderID.  

## <a name="week-of-may-13-2019"></a>Semaine du 13 mai 2019

### <a name="app-management"></a>Gestion d'applications

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise<!-- 1927359  -->
Sur les appareils déjà inscrits via l’Assistant Configuration avec l’une des méthodes d’inscription des appareils d’entreprise d’Apple, Intune ne prendra plus en charge le Portail d’entreprise lorsqu’il est installé manuellement par les utilisateurs finaux à partir de l’App store. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. 

Par ailleurs, l’écran **Identifier votre appareil** du Portail d’entreprise iOS est en cours de suppression. Par conséquent, les administrateurs qui souhaitent activer l’accès conditionnel ou déployer des applications d’entreprise doivent mettre à jour le profil d’inscription DEP. Cette exigence s’applique uniquement si l’inscription DEP est authentifiée avec l’Assistant Configuration. Dans ce cas, vous devez envoyer le Portail d’entreprise sur l’appareil. Pour ce faire, choisissez **Intune** > **Inscription d’appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisir un jeton > **Profils** > choisir un profil > **Propriétés** > définir **Installer le Portail d’entreprise** sur **Oui**.

Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Configurer comment les utilisateurs finaux mettent à jour une application métier (LOB) à l’aide d’une stratégie de protection d’application<!-- 3568384 -->
Vous pouvez maintenant configurer où vos utilisateurs finaux peuvent obtenir une version mise à jour d’une application métier (LOB). Les utilisateurs finaux voient cette fonctionnalité dans la boîte de dialogue **Version de l’application min** du lancement conditionnel qui invite les utilisateurs finaux à mettre à jour vers une version minimale de l’application métier. Vous devez fournir ces détails de mise à jour dans le cadre de votre stratégie de protection des applications métier (APPLICATION). Cette fonctionnalité est disponible sur iOS et Android. Sur iOS, cette fonctionnalité nécessite que l’application soit intégrée (ou incluse dans un wrapper à l’aide de l’outil correspondant) dans le kit de développement logiciel (SDK) Intune pour iOS version 10.0.7 ou supérieure. Sur Android, cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise. Pour configurer la façon dont un utilisateur final met à jour une application métier, cette dernière a besoin d’une stratégie de configuration d’application managée reçue avec la clé, `com.microsoft.intune.myappstore`. La valeur envoyée définit à partir de quel magasin de l’utilisateur final doit télécharger l’application. Si l’application est déployée via le Portail d’entreprise, la valeur doit être `CompanyPortal`. Pour tous les autres magasins, vous devez entrer une URL complète.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Scripts PowerShell pour Intune Management Extension<!-- 3734186  -->
Vous pouvez configurer des scripts PowerShell, qui s’exécuteront avec les privilèges Administrateur de l’utilisateur sur l’appareil. Pour en savoir plus, voir [Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune](../apps/intune-management-extension.md) et [Gestion de l’application Win32](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Gestion d’applications Android Entreprise<!-- 4459905 -->
Pour aider les administrateurs informatiques à configurer et à utiliser les fonctions de gestion d’applications Android Entreprise, Intune ajoute automatiquement quatre applications liées à cette solution dans la console d’administration Intune. Ces quatre applications sont les suivantes :

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : cette application est utilisée pour les scénarios impliquant une instance Android Entreprise entièrement gérée.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ce logiciel vous aide à vous connecter à vos comptes lorsque vous utilisez la vérification à deux facteurs.
- **[Portail d’entreprise Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : cette application est utilisée pour les scénarios impliquant des stratégies de protection des applications et des profils de travail Android Entreprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : cette fonctionnalité est utilisée pour les scénarios impliquant des kiosques/une instance Android Entreprise dédiée.

Auparavant, les administrateurs informatiques devaient manuellement rechercher et approuver ces applications dans le [store Google Play géré](https://play.google.com/store/apps) lors de la configuration. Cette modification supprime ces étapes manuelles, afin que la gestion de l’application Android Entreprise soit plus simple et plus rapide pour les clients.

Ces quatre fonctionnalités sont automatiquement ajoutées à la liste des applications Intune des administrateurs la première fois qu’ils connectent leur locataire Intune au store Google Play géré. Pour en savoir plus, voir [Connecter votre compte Intune à votre compte professionnel Android](../enrollment/connect-intune-android-enterprise.md). Pour les locataires qui ont déjà connecté leur locataire ou qui utilisent déjà Android Entreprise, les administrateurs n’ont pas besoin d’intervenir. Ces quatre applications s’afficheront automatiquement dans les 7 jours suivant la fin du lancement de service de mai 2019.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Mise à jour du connecteur de certificat PFX pour Microsoft Intune<!-- 1533038 -->
Nous avons publié une mise à jour pour [PFX Certificate Connector pour Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) qui permet de résoudre le problème suivant : les certificats PFX existants sont continuellement retraités, ce qui entraîne l’arrêt du traitement des nouvelles demandes par le connecteur.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Tâches de sécurité Intune pour Defender ATP (en préversion publique)<!-- 3208597 -->
Dans la préversion publique, vous pouvez utiliser Intune pour gérer les [tâches de sécurité pour Microsoft Defender Advanced Threat Protection (ATP)](../protect/atp-manage-vulnerabilities.md). Cette intégration dans ATP ajoute une approche basée sur les risques de la détection, de la hiérarchisation et des mauvaises configurations des points de terminaison tout en réduisant le délai entre la découverte et la correction.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Rechercher une puce TMP dans une stratégie de conformité des appareils Windows 10<!-- 3617671   idstaged-->
De nombreux appareils Windows 10 et ultérieur ont des circuits microprogrammés Module de plateforme sécurisée (TPM). Cette mise à jour inclut un nouveau paramètre de conformité, qui vérifie la version de la puce TPM sur l’appareil.

La section [Paramètres de stratégie de conformité de Windows 10 et ultérieur](../protect/compliance-policy-create-windows.md#device-security) décrit ce paramètre.

S’applique à : Windows 10 et versions ultérieures

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Empêcher les utilisateurs finaux de modifier leur point d’accès personnel et désactiver la journalisation de serveur Siri sur des appareils iOS<!-- 4097904   -->  
Vous pouvez créer un profil de restrictions pour un appareil iOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut de nouveaux paramètres, que vous pouvez configurer :

- **Applications intégrées** : Journalisation côté serveur pour les commandes de Siri
- **Sans fil** : Modification par l’utilisateur du point d’accès personnel (mode supervisé uniquement)

Pour afficher ces paramètres, accédez à [Paramètres d’application intégrée pour iOS](../configuration/device-restrictions-ios.md#built-in-apps) et [Paramètres sans fil pour iOS](../configuration/device-restrictions-ios.md#wireless).

S’applique à : iOS 12.2 et plus

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Nouveaux paramètres de restriction pour les applications de salle de classe sur les appareils macOS<!-- 4097905   --> 
Vous pouvez créer des profils de configuration pour les appareils macOS (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Restrictions de l’appareil** pour le type de profil). Cette mise à jour inclut les nouveaux paramètres pour les applications de salle de classe, l’option de blocage des captures d’écran et l’option de désactivation de la solution iCloud Photo Library.

Pour consulter les paramètres en cours, accédez à la section [Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-macos.md).

S’applique à : macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Le paramètre du mot de passe iOS permettant d’accéder à l’App Store est renommé.<!-- 4557891  -->
Le paramètre **Mot de passe permettant d’accéder à l’App Store** est renommé pour **Demander le mot de passe iTunes Store pour tous les achats** (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour plateforme > **Restrictions d’appareil** pour type de profil > **App Store, affichage de documents et jeux**).

Pour afficher les paramètres disponibles, accédez aux [paramètres iOS App Store, affichage de documents et jeux](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

S’applique à : iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Base de référence de Microsoft Defender Advanced Threat Protection (préversion)<!--  3754134 -->
Nous avons ajouté une préversion de base de référence de la sécurité pour les paramètres [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md). Cette ligne de base est disponible lorsque votre environnement répond à la configuration requise pour l’utilisation de [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Une page d’état de l’inscription Windows (ESP) est désormais disponible<!-- 3605348 -->
La Page d’état d’inscription n’est désormais plus une préversion. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Mise à jour de l’interface utilisateur Intune : création d’un profil d'inscription Autopilot<!-- 4593669 -->
L’interface utilisateur pour la création d’un profil d’inscription Autopilot a été mise à jour pour s’aligner sur les styles d’interface utilisateur d’Azure. Pour en savoir plus, voir [Créer un profil d’inscription Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). À l’avenir, des scénarios supplémentaires Intune seront actualisés conformément à ce nouveau style d’interface utilisateur.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Activer la réinitialisation d’Autopilot pour tous les appareils Windows<!-- 4225665 -->
La réinitialisation d’Autopilot fonctionne maintenant pour tous les appareils Windows, y compris ceux qui ne sont pas configurés pour utiliser la page d’état d’inscription. Si une page d’état d’inscription n’a pas été configurée pour l’appareil lors de son inscription initiale, l’appareil passera directement au bureau après la connexion. La synchronisation et l’affichage conforme dans Intune peuvent prendre jusqu’à huit heures. Pour plus d’informations, consultez [Réinitialiser les appareils par réinitialisation à distance de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Format IMEI exact non requis lors de la recherche dans Tous les appareils<!--30407680 -->
Vous n’aurez pas à inclure d’espaces dans les chiffres IMEI pour effectuer une recherche dans **Tous les appareils**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Application sur le portail Intune de la suppression d’un appareil sur le portail Apple<!--2489996 -->
Si un appareil est supprimé sur le portail du Programme d’inscription des appareils ou sur le portail Apple Business Manager, cette suppression est automatiquement appliquée à Intune lors de la synchronisation suivante.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>La Page d’état d’inscription effectue maintenant le suivi des applications Win32<!-- 2714451 -->
Cela s’applique uniquement aux appareils exécutant Windows 10 version 1903 et versions ultérieures. Pour plus d’informations, voir [Configurer une page d’état de l’inscription](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Gestion des appareils

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Réinitialiser et effacer en bloc le contenu des appareils à l’aide de l’API Graph<!-- 3295288 -->
L’API Graph permet désormais de réinitialiser et d’effacer le contenu d’un maximum de 100 appareils à la fois.

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>Le rapport de chiffrement ne fait pas partie de la préversion publique<!-- 4587546      -->
Le [rapport pour le chiffrement de lecteur BitLocker et d’appareil](../protect/encryption-monitor.md) est maintenant généralement disponible et ne fait plus partie de la préversion publique.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Signature Outlook et paramètres biométriques pour les appareils iOS et Android<!-- 4050557 -->
Vous pouvez maintenant spécifier si la signature par défaut est activée dans Outlook sur les appareils iOS et Android. De plus, vous pouvez choisir d’autoriser les utilisateurs à modifier le paramètre biométrique dans Outlook sur iOS.

## <a name="week-of-may-6-2019"></a>Semaine du 6 mai 2019

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Prise en charge du contrôle d’accès réseau (NAC) pour l’accès F5 sur les appareils iOS<!-- 4500808 -->

F5 a publié une mise à jour vers BIG-IP 13 qui autorise la fonctionnalité NAC pour l’accès F5 sur iOS dans Intune. Pour utiliser cette fonctionnalité :

- Effectuez une mise à jour de BIG-IP avec la version 13.1.1.5 actualisée. BIG-IP 14 n’est pas pris en charge.
- Intégrez BIG-IP avec Intune pour le contrôle d’accès réseau. Étapes dans [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Cochez le paramètre **Activer le contrôle d'accès réseau (NAC)** dans le profil VPN dans Intune.

Pour voir le paramètre disponible, accédez à [Configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md).

S’applique à : iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Mise à jour du connecteur de certificat PFX pour Microsoft Intune<!-- doc-vso 1521237  -->  
Nous avons publié une mise à jour pour le [connecteur de certificat PFX pour Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) qui baisse l’intervalle d’interrogation de 5 minutes à 30 secondes.




## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
