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
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827817"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>En développement pour Microsoft Intune - Janvier 2020

Pour faciliter votre préparation et votre planification, cette page répertorie les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore mises en production. Outre les informations de cette page : 

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité entre en production, qu’il s’agisse d’une version d’évaluation ou d’une disponibilité générale, la description de la fonctionnalité est déplacée de cette page vers [Nouveautés](whats-new.md).
- Cette page et la page [Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!NOTE]
> Cette page reflète nos attentes actuelles concernant les fonctionnalités Intune dans une version ultérieure. Les dates et les fonctionnalités individuelles peuvent changer. Cette page ne décrit pas toutes les fonctionnalités du développement.

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
Nous allons mettre à jour l’application Portail d’entreprise sur les appareils Windows pour afficher les notifications Toast aux utilisateurs, même lorsque l’application est fermée. La mise à jour affiche les notifications pour les applications disponibles uniquement lorsque l’état de l’installation est terminé ou a échoué. L’application Portail d’entreprise n’affiche pas de notifications pour les applications requises. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Afficher les messages d’état d’installation de l’application Portail d’entreprise<!-- 2514416  -->
L’application Portail d’entreprise affiche des messages d’état d’installation d’application supplémentaires pour les utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>Recibler des clips Web vers Microsoft Edge sur des appareils iOS<!-- 5455276 idready -->
Les clips Web, qui jouent le rôle d’applications Web épinglées sur des appareils iOS, devront être mis à jour. Les clips Web récemment déployés s’ouvrent dans Microsoft Edge au lieu du Intune Managed Browser si nécessaire pour s’ouvrir dans un navigateur protégé. Vous devez recibler des clips Web préexistants pour vous assurer qu’ils s’ouvrent dans Microsoft Edge au lieu de l’Managed Browser. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Modification de l’expérience utilisateur lors de l’ajout d’applications à Intune<!-- 4705829 idready -->
Vous verrez une nouvelle expérience utilisateur lors de l’ajout d’applications via Intune. Cette expérience fournit les mêmes paramètres et détails que ceux que vous avez utilisés précédemment, mais la nouvelle expérience suit un processus de type assistant avant l’ajout d’une application à Intune. Cette nouvelle expérience fournit également une page de vérification avant l’ajout de l’application. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Applications** > **Toutes les applications** > **Ajouter**. Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----3136567--"></a>Exiger le redémarrage des applications Win32 <!-- 3136567-->
Vous pouvez exiger qu’une application Win32 soit redémarrée après une installation réussie. Vous pouvez également choisir la durée (période de grâce) avant le redémarrage.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration de l’appareil

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Ajouter des paramètres de proxy automatique aux profils Wi-Fi pour les profils de travail Android Enterprise<!-- 4490822 idready -->
Sur les appareils Android Enterprise Work Profile, vous pouvez créer des profils Wi-Fi. Lorsque vous choisissez le type d’entreprise Wi-Fi, vous pouvez également entrer le type de protocole EAP (Extensible Authentication Protocol) utilisé sur votre réseau Wi-Fi.

Dans une prochaine mise à jour, lorsque vous choisissez le type d’entreprise, vous pouvez entrer des paramètres de proxy automatiques, y compris une URL de serveur proxy, par exemple `proxy.contoso.com`.

Pour afficher les paramètres Wi-Fi actuels que vous pouvez configurer, accédez à [Ajouter des paramètres Wi-Fi pour les appareils exécutant Android Enterprise et Android Kiosk dans Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

S’applique à :
- Profil professionnel Android Entreprise

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profils de configuration de périphérique réseau câblé pour les appareils macOS<!-- 3508686  -->
Un nouveau profil de configuration d’appareil macOS sera disponible pour configurer les réseaux câblés (**configuration** de l’appareil > **profils** > **créer un profil** > **MacOS** pour la plateforme > **réseau câblé** pour le type de profil). Utilisez cette fonctionnalité pour créer des profils 802.1 x pour gérer les réseaux câblés et déployer ces réseaux câblés sur vos appareils macOS.

S’applique à :
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>Les profils VPN avec des connexions VPN IKEv2 peuvent utiliser Always on avec des appareils iOS <!-- 1947932 idready -->
Sur les appareils iOS, vous pouvez créer un profil VPN qui utilise une connexion IKEv2 (**configuration** de l’appareil > **profils** > **créer un profil** > **iOS/iPad** pour la plateforme > **VPN** pour le type de profil). Dans une prochaine mise à jour, vous pouvez configurer Always on avec IKEv2. Une fois configurés, les profils VPN IKEv2 se connectent automatiquement et restent connectés (ou se reconnectent rapidement) au VPN. Il reste connecté même lorsque vous passez d’un réseau à un autre, ou que vous redémarrez des appareils.

Sur iOS, le VPN Always on est limité aux profils IKEv2.

Pour afficher les paramètres IKEv2 actuels que vous pouvez configurer, consultez [Ajouter des paramètres VPN sur les appareils iOS dans Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

S’applique à :
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Amélioration de l’interface utilisateur lors de la création de profils de configuration sur des appareils iOS et macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Lorsque vous créez un profil pour des appareils iOS ou macOS, l’expérience dans le centre d’administration de la gestion des points de terminaison est mise à jour. Cette modification a un impact sur les profils de configuration d’appareil suivants (**périphériques** > **profils de configuration** > **créer un profil** > **iOS** ou **MacOS** pour la plateforme) :

- Personnalisé : iOS, macOS
- Fonctionnalités de l’appareil : iOS, macOS
- Limites des appareils : iOS, macOS
- Endpoint Protection : macOS
- Extensions : macOS
- Fichier de préférences : macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Amélioration de l’interface utilisateur lors de la création de profils de configuration OEMConfig sur des appareils d’entreprise Android<!-- 5568645 idready  -->
Lorsque vous créez ou modifiez un profil OEMConfig pour des appareils d’entreprise Android, l’expérience dans le centre d’administration de la gestion des points de terminaison est mise à jour. L’expérience mise à jour fournira un résumé des paramètres que vous avez configurés en un clin d’œil. Cette modification a un impact sur le profil de configuration d’appareil OEMConfig (**appareils** > **profils de configuration** > **créer un profil** > **Android Enterprise** pour la plateforme > **OEMConfig** pour le type de profil).

Cette fonctionnalité s’applique à :
- Android Entreprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscription des appareils

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>Bloquer les inscriptions Android par le fabricant de l’appareil<!--5197392 idready-->
Vous serez en mesure de bloquer l’inscription d’appareils en fonction du fabricant de l’appareil. Cela s’applique aux appareils Android Device Administrator et Android Enterprise Work Profile. Pour afficher les restrictions d’inscription, accédez au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)> les **appareils** > **restrictions d’inscription**.



<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des périphériques


### <a name="new-information-in-device-details---4471759-5604099----"></a>Nouvelles informations dans les détails de l’appareil<!-- 4471759 5604099  -->
Les informations suivantes seront ajoutées à la page **vue d’ensemble** des appareils :
- Capacité de la mémoire (quantité de mémoire physique sur l’appareil)
- Capacité de stockage (quantité de stockage physique sur l’appareil) 
- Type et vitesse du processeur UC
- Données de RAM et de processeur

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>Nouveau gestionnaire de sécurité de point de terminaison de rôle intégré Intune<!--4253397 idready-->
Un nouveau rôle intégré Intune est disponible : le gestionnaire de sécurité des points de terminaison. Ce nouveau rôle donne aux administrateurs un accès complet au nœud Gestionnaire des points de terminaison dans Intune et aux accès prêts à d’autres domaines uniquement. Le rôle est une extension du rôle « administrateur de la sécurité » de Azure AD. Si vous avez actuellement des administrateurs généraux en tant que rôles, aucune modification n’est nécessaire. Si vous utilisez des rôles et que vous souhaitez la granularité fournie par le gestionnaire de sécurité des points de terminaison, affectez ce rôle lorsqu’il est disponible. Pour plus d’informations sur les rôles intégrés, consultez [contrôle d’accès en fonction du rôle](role-based-access-control.md).

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Modifications de l’interface utilisateur des rôles Intune<!--5801612 idready-->
L’interface utilisateur du [Centre](https://go.microsoft.com/fwlink/?linkid=2109431) d’administration du gestionnaire des points de terminaison de Microsoft > les **rôles** de > **administration des locataires** change en une conception plus conviviale et intuitive. Cette expérience fournit les mêmes paramètres et détails que vous utilisez maintenant, mais la nouvelle expérience utilise un processus de type assistant.


<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Prise en charge des informations d’identification dérivées sur les appareils Android COBO<!--4839592-->
Vous pouvez utiliser des informations d’identification dérivées sur des appareils Android Enterprise entièrement gérés. La prise en charge sera incluse pour la récupération des informations d’identification dérivées pour Entrust Datacard, intercéder et DISA purebred. Vous pouvez utiliser des informations d’identification dérivées pour l’authentification de l’application, le Wi-Fi, le VPN ou la signature et/ou le chiffrement S/MIME avec les applications qui le prennent en charge. 

<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).


