---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601550"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>En développement pour Microsoft Intune - Octobre 2019

Pour faciliter votre préparation et votre planification, cette page répertorie les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore mises en production. Outre les informations de cette page :

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité entre en production, qu’il s’agisse d’une version d’évaluation ou d’une disponibilité générale, la description de la fonctionnalité est déplacée de cette page vers [Nouveautés](whats-new.md).
- Cette page et la page [Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!NOTE]
> Cette page reflète nos attentes actuelles concernant les fonctionnalités Intune dans une version ultérieure. Les dates et les fonctionnalités individuelles peuvent changer. Cette page ne décrit pas toutes les fonctionnalités du développement.

**Flux RSS** : découvrez quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

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
## <a name="app-management"></a>Gestion d'applications

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Appliquer le mode sombre dans iOS Portail d’entreprise <!-- 4911422  -->
Le mode sombre est prévu pour les Portail d’entreprise iOS. Vous serez en mesure de télécharger des applications d’entreprise, de gérer vos appareils et de bénéficier d’un support informatique dans le modèle de couleurs de votre choix. Pour plus d’informations sur le portail d’entreprise iOS, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Exécuter des applications Win32 sur des appareils Windows 10 en mode S <!-- 3747604  --> 
Vous pouvez installer et exécuter des applications Win32 sur des appareils gérés en mode Windows 10 S. Créez une ou plusieurs stratégies supplémentaires pour le mode S en utilisant les outils Windows Defender application Control (WDAC) PowerShell. Utilisez le portail de signature Device Guard pour signer les stratégies supplémentaires. Ensuite, chargez et distribuez les stratégies via Intune. 

Dans Intune, vous trouverez cette fonctionnalité en sélectionnant **applications clientes**  >  les**stratégies supplémentaires Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Définir la disponibilité de l’application en fonction d’une date et d’une heure <!-- 3510685  -->
En tant qu’administrateur, vous pouvez configurer l’heure de début et l’échéance d’une application requise. À l’heure de début, l’extension de gestion Intune télécharge le contenu de l’application et le met en cache. L’application sera installée à l’heure d’échéance. Pour les applications disponibles, l’heure de début indiquera quand l’application sera visible dans Portail d’entreprise. 

Pour définir la disponibilité des applications en fonction de la date et de l’heure :

1. Dans Intune, sélectionnez **Applications clientes** > **Applications**. 
1. Sélectionnez une application dans la liste ou ajoutez-en une en sélectionnant **Ajouter**. 
1. Dans le panneau de l’application, sélectionnez **affectations** > **Ajouter un groupe**. 
1. Définissez le **type d’affectation** sur **obligatoire** , puis sélectionnez **groupes inclus**. 
1. Définissez **rendre cette application obligatoire pour tous les utilisateurs** sur **Oui**. 
1. Sélectionnez **modifier** pour modifier les options de l' **expérience utilisateur final** . 
1. Dans le panneau **expérience utilisateur final** , définissez le **temps disponible du logiciel** en fonction des besoins. 

Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Exiger le redémarrage des applications Win32 <!-- 3136567  -->
Vous pouvez exiger qu’une application Win32 redémarre après une installation réussie. Vous pouvez choisir la durée (période de grâce) avant le redémarrage.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Afficher les notifications de l’application Portail d’entreprise sur Windows <!-- 1808082  -->
Nous allons mettre à jour l’application Portail d’entreprise sur les appareils Windows pour afficher les notifications Toast aux utilisateurs, même lorsque l’application est fermée. La mise à jour affiche les notifications pour les applications disponibles uniquement lorsque l’état de l’installation est terminé ou a échoué. L’application Portail d’entreprise n’affiche pas de notifications pour les applications requises.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Afficher les messages d’état d’installation de l’application Portail d’entreprise <!-- 2514416  -->
L’application Portail d’entreprise affiche des messages d’état d’installation d’application supplémentaires pour les utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.
- L’application a été correctement installée mais nécessite un redémarrage.
- L’application est en cours d’installation, mais nécessite un redémarrage pour continuer.

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Affecter la version bêta de Microsoft Edge pour macOS <!-- 4678761  -->
Vous pourrez ajouter et affecter la dernière version de Microsoft Edge Beta à Intune pour les appareils macOS. 

Pour affecter la version bêta de Microsoft Edge pour les appareils macOS :
1. Dans Intune, sélectionnez **applications clientes**  > **applications**  > **Ajouter une application**  > **Microsoft Edge-MacOS**. 
1. Affectez la version bêta Microsoft Edge aux groupes prévus. Microsoft AutoUpdate (MAU) assure la mise à jour de Microsoft Edge. 
 
Pour plus d’informations sur Microsoft Edge, consultez [gérer l’accès Web à l’aide de Microsoft Edge avec Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation <!-- 2576686 -->
L’application Intune sur des appareils Android et iOS vous permettra de contrôler le contenu de la notification d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur l’Application, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Nouveau profil d’interface de configuration du microprogramme de l’appareil pour les appareils qui exécutent Windows 10 et versions ultérieures <!-- 2266073  -->
Sur Windows 10 et versions ultérieures, vous pouvez créer un profil de configuration d’appareil pour contrôler les paramètres et les fonctionnalités : 

1. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
1. Pour la plateforme, sélectionnez **Windows 10 et version ultérieure**. 
 
Un nouveau type de profil d’interface de configuration du microprogramme de l’appareil permet à Intune de gérer les paramètres UEFI (BIOS).

Pour plus d’informations sur les paramètres actuels que vous pouvez configurer, consultez [appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide de profils d’appareil dans Microsoft Intune](../configuration/device-profiles.md).

Cette fonctionnalité s’applique à Windows 10 RS5 (1809) et versions ultérieures sur les appareils sélectionnés.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscription des appareils

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>Pour les appareils iOS, personnalisez la fenêtre de confidentialité de l’inscription de Portail d’entreprise <!-- 4394993  -->
À l’aide de Markdown, vous pourrez personnaliser la fenêtre de confidentialité du Portail d’entreprise que les utilisateurs finaux voient lors de l’inscription à iOS. Plus précisément, vous serez en mesure de personnaliser la liste des éléments que votre organisation ne peut pas voir ou faire sur l’appareil.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Modifier la valeur de balise de groupe pour les appareils AutoPilot<!-- 4816775 -->
Vous pouvez modifier la valeur de **balise de groupe** pour les appareils AutoPilot :

1. Sélectionnez **Intune** > **inscription d’appareils** > **l'inscription Windows** > **Windows AutoPilot** > **les appareils**.
1. Choisissez l’appareil.
1. Dans le volet de droite, modifiez la valeur de **balise de groupe** .
1. Sélectionnez **Enregistrer**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Cibler des groupes d’utilisateurs macOS pour exiger la gestion de JAMF <!-- 4061739 -->
Vous pourrez cibler des groupes d’utilisateurs spécifiques pour que les appareils macOS puissent être gérés par JAMF. Cette cible vous permet d’appliquer l’intégration de la conformité JAMF à un sous-ensemble d’appareils macOS, tandis que d’autres appareils continuent d’être gérés par Intune. Le ciblage vous permettra également de migrer progressivement les appareils des utilisateurs d’un système de gestion des appareils mobiles (MDM) vers l’autre.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Déployer des mises à jour logicielles sur des appareils macOS <!-- 3194876 -->
Vous serez en mesure de déployer des mises à jour logicielles sur des groupes d’appareils macOS. Cette fonctionnalité comprend des mises à jour critiques, de microprogramme, de fichier de configuration et autres. Vous pouvez envoyer des mises à jour lors de l’archivage suivant de l’appareil. Ou vous pouvez sélectionner une planification hebdomadaire pour déployer des mises à jour dans ou hors des périodes que vous définissez. 

Cette fonctionnalité vous aide quand vous souhaitez mettre à jour des appareils en dehors des heures de travail standard ou en dehors des heures de travail de votre support technique. Vous obtiendrez également un rapport détaillé de tous les appareils macOS sur lesquels des mises à jour sont déployées. Vous pouvez accéder au rapport par appareil pour voir l’état d’une mise à jour particulière.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Analyse et résolution des problèmes

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Rapport Android sur la page vue d’ensemble des appareils <!-- 2984353  -->
Nous allons ajouter un nouveau rapport à la page **vue d’ensemble des appareils** . Le rapport affiche le nombre d’appareils Android inscrits dans chaque solution de gestion des appareils. Le graphique affiche le nombre d’appareils pour le profil professionnel, entièrement géré, dédié et administrateur de l’appareil inscrit. 

Pour afficher le rapport, choisissez **Intune** > **appareils** > **vue d’ensemble**.

### <a name="updated-support-experience-------5012398------"></a>Expérience de support mise à jour   <!--  5012398    -->
Dans le cadre des améliorations continues, nous allons mettre à jour l’expérience de prise en charge dans la console pour Intune.  Nous allons améliorer la recherche et les commentaires dans la console pour les problèmes courants, et nous allons simplifier le flux de travail pour contacter le support technique.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).
