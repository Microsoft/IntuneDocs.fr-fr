---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cafe9d3036a727d79de88eda050399138da55675
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977748"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>En développement pour Microsoft Intune - Février 2020

Pour faciliter votre préparation et votre planification, cette page répertorie les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore mises en production. Outre les informations de cette page : 

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité entre en production, qu’il s’agisse d’une préversion ou d’une version en disponibilité générale, la description de la fonctionnalité est déplacée de cette page vers [Nouveautés](whats-new.md).
- Cette page et la page [Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!NOTE]
> Cette page reflète nos attentes actuelles concernant les fonctionnalités d’Intune dans une version ultérieure. Les dates et les fonctionnalités individuelles peuvent changer. Cette page ne décrit pas toutes les fonctionnalités en développement.

**Flux RSS** : découvrez quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestion des applications

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Afficher les notifications de l’application Portail d’entreprise sur Windows<!-- 1808082  -->
Nous allons mettre à jour l’application Portail d’entreprise sur les appareils Windows pour afficher les notifications toast aux utilisateurs, même quand l’application est fermée. La mise à jour montre les notifications pour les applications disponibles seulement quand l’état de l’installation est Terminé ou Échec. L’application Portail d’entreprise ne montrera pas de notifications pour les applications nécessaires. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Afficher les messages d’état d’installation pour l’application Portail d’entreprise<!-- 2514416  -->
L’application Portail d’entreprise montrera des messages d’état d’installation d’application supplémentaires aux utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Recibler les clips web vers Microsoft Edge sur les appareils iOS<!-- 5455276 -->
Les clips web, qui agissent comme des applications web épinglées sur des appareils iOS, devront être mis à jour. Les clips web nouvellement déployés s’ouvrent dans Microsoft Edge au lieu d’Intune Managed Browser s’ils doivent s’ouvrir dans un navigateur protégé. Vous devez recibler des clips web préexistants pour faire en sorte qu’ils s’ouvrent dans Microsoft Edge au lieu de Managed Browser.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>améliorations de l’expérience utilisateur du Portail d’entreprise macOS<!-- 5568987 -->
Nous apportons des améliorations à l’expérience d’inscription des appareils macOS et à l’application Portail d’entreprise pour Mac. Voici ce à quoi vous pouvez vous attendre :
- Une meilleure expérience de Microsoft **AutoUpdate** lors de l’inscription, afin de garantir que vos utilisateurs disposent de la dernière version du Portail d’entreprise.
- Une étape de vérification de la conformité améliorée lors de l’inscription.
- La prise en charge de la copie des ID d’incident, pour que vos utilisateurs puissent envoyer plus rapidement les erreurs de leurs appareils à l’équipe de support technique de votre entreprise.

Pour plus d’informations sur l’inscription et l’application Portail d’entreprise pour Mac, consultez Inscrire votre appareil macOS en utilisant l’application Portail d’entreprise (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp). 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Écran supprimé du Portail d’entreprise, inscription de profil professionnel Android<!--6103987 -->
L’écran **Quelle est la prochaine étape**  est supprimé du flux d’inscription de profil professionnel Android dans le Portail d’entreprise, afin de faciliter l’expérience utilisateur. Accédez à [Inscrire avec un profil professionnel Android]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile) pour voir le déroulement actuel de l’inscription d’un profil professionnel Android.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>Application Microsoft Defender Advanced Threat Protection pour macOS<!-- 5424518 idready -->
Intune offre un moyen simple de déployer l’application Microsoft Defender Advanced Threat Protection pour macOS sur les appareils Mac gérés. Pour plus d’informations, consultez [Microsoft Defender Advanced Threat Protection pour Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration de l’appareil

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profils de configuration d’appareil de réseau câblé pour les appareils macOS<!-- 3508686  -->
Un nouveau profil de configuration d’appareil macOS sera disponible pour configurer les réseaux câblés (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Réseau câblé** pour le type de profil). Utilisez cette fonctionnalité pour créer des profils 802.1x pour gérer les réseaux câblés et déployer ces réseaux câblés sur vos appareils macOS.

S’applique à :
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>Les profils VPN avec des connexions VPN IKEv2 peuvent utiliser Always On avec les appareils iOS <!-- 1947932 idready -->
Sur les appareils iOS, vous pouvez créer un profil VPN qui utilise une connexion IKEv2 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS/iPad** pour la plateforme > **VPN** pour le type de profil). Dans une prochaine mise à jour, vous pourrez configurer Always On avec IKEv2. Une fois configurés, les profils VPN IKEv2 se connectent automatiquement et restent connectés (ou se reconnectent rapidement) au VPN. Ils restent connectés même quand vous passez d’un réseau à l’autre ou que vous redémarrez les appareils.

Sur iOS, le VPN Always On est limité aux profils IKEv2.

Pour afficher les paramètres IKEv2 actuels que vous pouvez configurer, consultez [Ajouter des paramètres VPN sur les appareils iOS dans Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

S’applique à :
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Amélioration de l’expérience de l’interface utilisateur lors de la création de profils de configuration sur des appareils iOS et macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Quand vous créez un profil pour des appareils iOS ou macOS, l’expérience dans le Centre d’administration de gestion des points de terminaison est mise à jour. Cette modification a un impact sur les profils de configuration d’appareil suivants (**Appareils** > **Profils de configuration** > **Créer un profil** > **iOS** ou **macOS** pour la plateforme) :

- Personnalisé : iOS, macOS
- Fonctionnalités de l’appareil : iOS, macOS
- Limites des appareils : iOS, macOS
- Endpoint Protection : macOS
- Extensions : macOS
- Fichier de préférences : macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Amélioration de l’interface utilisateur lors de la création de profils de configuration OEMConfig sur des appareils Android Entreprise<!-- 5568645 idready  -->
Quand vous créez ou que vous modifiez un profil OEMConfig pour des appareils Android Entreprise, l’expérience dans le Centre d’administration de gestion des points de terminaison est mise à jour. L’expérience mise à jour fournira un récapitulatif des paramètres que vous avez configurés. Cette modification a un impact sur le profil de configuration d’appareil OEMConfig (**Appareils** > **Profils de configuration** > **Créer un profil** > **Android Entreprise** pour la plateforme > **OEMConfig** pour le type de profil).

Cette fonctionnalité s’applique à :
- Android Entreprise 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des périphériques

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Changer l’utilisateur principal pour les appareils Windows <!-- 3794742 -->
Vous serez en mesure de changer l’utilisateur principal pour les appareils Windows hybrides et joints à Azure AD. Pour cela, accédez à **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil > **Propriétés** > **Utilisateur principal**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Numéro de série sur la page Certificat Push MDM Apple<!--5947765 -->
La page Certificat Push MDM Apple montrera le numéro de série. Le numéro de série est nécessaire pour accéder à nouveau au certificat Push MDM Apple si l’accès à l’ID Apple qui a créé le certificat est perdu. Pour voir le numéro de série, accédez à **Appareils** > **iOS** > **Inscription iOS** > **Certificat Push MDM Apple**.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Choisir les mises à jour iOS/iPadOS à envoyer aux appareils inscrits<!--5879689 -->
Vous pourrez choisir une mise à jour iOS/iPadOS à envoyer aux appareils qui ont été inscrits avec Apple Business Manager ou Apple School Manager. Ces appareils doivent avoir une stratégie de configuration d’appareil définie pour retarder la visibilité des mises à jour logicielles pendant un certain nombre de jours. Pour voir cette fonctionnalité, accédez à MEM > **Appareils** > **iOS** > **Mettre à jour les stratégies pour iOS/iPadOS** > **Créer un profil**.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Nouvelles options de planification des mises à jour pour l’envoi des mises à jour du système d’exploitation aux appareils iOS/iPadOS inscrits<!--5879689-->
Vous pouvez utiliser les options suivantes lors de la planification des mises à jour du système d’exploitation pour les appareils iOS/iPadOS. Ceci s’applique aux appareils qui ont utilisé les types d’inscription Apple Business Manager ou Apple School Manager.
- Mettre à jour lors du check-in suivant
- Mettre à jour pendant l’intervalle planifié
- Mettre à jour en dehors de l’intervalle planifié

Pour les deux dernières options, vous pouvez créer plusieurs fenêtres de temps.

Pour voir les nouvelles options, accédez à MEM > **Appareils** > **iOS** > **Mettre à jour les stratégies pour iOS/iPadOS** > **Créer un profil**.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Analyse et résolution des problèmes

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Amélioration de l’expérience de création de rapports Intune<!-- 3791418 idready -->
Intune offre désormais une meilleure expérience de création de rapports, avec notamment de nouveaux types de rapports, une meilleure organisation des rapports, des vues plus ciblées, des fonctionnalités de rapport améliorées, ainsi que des données plus cohérentes et ponctuelles. L’expérience de création de rapports passe de la préversion à la disponibilité générale. En outre, la version en disponibilité générale fournit une prise en charge de la localisation, des correctifs de bogues, des améliorations de conception et des données de conformité d’appareil agrégées sur les vignettes dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Les nouveaux types de rapport se concentrent sur les éléments suivants :
- **Opérationnel** : fournit des enregistrements actualisés en se concentrant sur les éléments d’intégrité négatifs. 
- **Organisationnel** : fournit un résumé plus large de l’état global.
- **Historique** : fournit les modèles et tendances sur une période donnée.
- **Spécialiste** : vous permet d’utiliser des données brutes pour créer vos propres rapports personnalisés.

Le premier ensemble de nouveaux rapports se concentre sur la conformité des appareils. Pour plus d’informations, consultez [Blog - Infrastructure de création de rapports Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) et [Rapports Intune](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Modifications à venir de l’interface utilisateur des rôles Intune<!--5801612 idready-->
L’interface utilisateur du [Centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Administration des locataires** > **Rôles** changera en faveur d’une conception plus conviviale et plus intuitive. Cette expérience fournit les mêmes paramètres et les mêmes informations détaillées que celles que vous utilisez maintenant, mais la nouvelle expérience utilise un processus de type Assistant.


<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Prise en charge des informations d’identification dérivées sur les appareils Android COBO<!--4839592-->
Vous pouvez utiliser des informations d’identification dérivées sur des appareils Android Entreprise complètement managés. Une prise en charge sera incluse pour la récupération des informations d’identification dérivées pour Entrust Datacard, Intercede et DISA Purebred. Vous pourrez utiliser des informations d’identification dérivées pour l’authentification de l’application, le Wi-Fi, le VPN ou la signature et/ou le chiffrement S/MIME avec les applications qui le prennent en charge.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Utiliser une stratégie antivirus pour gérer les paramètres de l’antivirus Microsoft Defender et l’expérience de sécurité Windows<!--6131401 -->
À partir du nœud *Sécurité du point de terminaison*, vous pouvez configurer les paramètres de l’**antivirus**. Quand vous configurez la stratégie pour l’antivirus, vous définissez les paramètres de vos appareils Windows 10 via deux types de profils :

- Antivirus Microsoft Defender : gérez les paramètres pour la protection cloud, les exclusions de l’antivirus, la remédiation, les options d’analyse, etc.
- Expérience de sécurité Windows : gérez l’expérience des utilisateurs pour les paramètres de sécurité Windows sur leurs appareils. Vous serez en mesure de configurer ce que les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender et les notifications qu’ils reçoivent. 

<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).


