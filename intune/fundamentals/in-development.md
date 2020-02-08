---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912627"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>En développement pour Microsoft Intune - Janvier 2020

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
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Modifications à venir de l’interface utilisateur des rôles Intune<!--5801612 idready-->
L’interface utilisateur du [Centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Administration des locataires** > **Rôles** changera en faveur d’une conception plus conviviale et plus intuitive. Cette expérience fournit les mêmes paramètres et les mêmes informations détaillées que celles que vous utilisez maintenant, mais la nouvelle expérience utilise un processus de type Assistant.


<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Prise en charge des informations d’identification dérivées sur les appareils Android COBO<!--4839592-->
Vous pouvez utiliser des informations d’identification dérivées sur des appareils Android Entreprise complètement managés. Une prise en charge sera incluse pour la récupération des informations d’identification dérivées pour Entrust Datacard, Intercede et DISA Purebred. Vous pourrez utiliser des informations d’identification dérivées pour l’authentification de l’application, le Wi-Fi, le VPN ou la signature et/ou le chiffrement S/MIME avec les applications qui le prennent en charge. 

<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).


