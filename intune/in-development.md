---
title: Dans le développement - Microsoft Intune
titlesuffix: ''
description: Fonctionnalités de Microsoft Intune dans le développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a34cf1ec89165821e853b00be1fd8c83717767e2
ms.sourcegitcommit: aab39bf86707ccaef45fd6527fff4f1c89336710
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58429672"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>Dans le développement pour Microsoft Intune - mars 2019

Pour faciliter votre préparation et planification, cette page listes Intune UI met à jour et de fonctionnalités qui en cours de développement, mais pas encore été publié. De plus :

- Si nous pensons que vous devez effectuer une action avant une modification, nous allons publier un billet de centre de messages Office gratuit.
- Quand une fonctionnalité est lancée en production, soit en version préliminaire ou à la disposition générale, la description de la fonctionnalité déplace hors de cette page et sur le [page Nouveautés](whats-new.md).
- Cette page et le [page Nouveautés](whats-new.md) sont régulièrement mis à jour. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour stratégiques livrables et chronologies.

> [!Note]
> Ces éléments reflètent les attentes en cours de Microsoft sur les fonctionnalités Intune proposée dans une version ultérieure. Dates et des fonctionnalités individuelles peuvent changer. Pas tous les éléments de développement ont une description de la fonctionnalité sur cette page.

**Flux RSS** : recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure


<!-- 1903 start-->

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>Balises d’étendue pour les stratégies de configuration <!--2371891 -->
Vous serez en mesure d’ajouter une balise d’étendue à une stratégie de configuration d’application afin que seules les personnes avec des rôles affectés également cette balise d’étendue aient accès à la stratégie de configuration d’application. La stratégie de configuration d’application peut uniquement être destinée aux associé ou applications affectées de la même balise d’étendue.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Affecter des profils Autopilot au groupe virtuel Tous les appareils <!--2715522 -->
Vous pourrez affecter des profils Autopilot au groupe virtuel Tous les appareils. Pour ce faire, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Profils de déploiement** > choisissez un profil >  **Affectations** > sous **Affecter à** choisissez **Tous les appareils**. Pour plus d’informations sur les profils Autopilot, consultez [Inscrire des appareils Windows à l’aide de Windows Autopilot](enrollment-autopilot.md).

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Empêcher les utilisateurs de l’analyse des mises à jour de Windows    <!-- 3316758    -->
Nous ajoutons un nouveau paramètre d’anneau de mise à jour de Windows que vous pouvez utiliser pour empêcher des utilisateurs de l’analyse des mises à jour de Windows. Ce paramètre n’est pas disponible à partir du portail, mais peut être configuré à l’aide de l’API Graph Intune.

### <a name="windows-update-notifications-----3316782---"></a>Notifications de mise à jour de Windows  <!-- 3316782 -->
Nous avons ajouté la prise en charge pour les configurations d’anneau de mise à jour de Windows afin d’être en mesure de configurer les notifications de mise à jour de Windows que vos utilisateurs voient. Ce paramètre n’est pas disponible à partir du portail, mais peut être configuré à l’aide de l’API Graph Intune.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Modifications apportées à leur inscription au portail d’entreprise pour les utilisateurs d’appareils iOS 12 <!--3448635 -->  
Portail d’entreprise pour iOS a mis à jour les écrans d’inscription de l’application et les étapes pour s’aligner avec les modifications de l’inscription MDM publiées dans Apple iOS 12.2. Le flux de travail mis à jour demande désormais aux utilisateurs de :

- Autoriser Safari ouvrir le site Web portail d’entreprise (par le biais de Safari) et de télécharger le profil de gestion avant de retourner à l’application portail d’entreprise.
- Ouvrez l’application paramètres afin d’installer le profil de gestion sur son appareil.
- Retourner à l’application de portail d’entreprise pour effectuer d’inscription.

Pour plus d’informations sur la façon dont vous pouvez préparer ces modifications, consultez le [post de la Communauté technologique Microsoft](https://aka.ms/CP_changes_iOS12). En attendant, pour prendre en charge les nouvelles inscriptions iOS dans le portail d’entreprise, nous avons mis à jour les étapes de [inscription iOS appareil dans Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Ces modifications de document seront actives après la publication de Apple iOS version 12.2. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>Prise en charge des connecteurs supplémentaires sur la page d’état du client <!-- 3617202     -->
La page d’état du client affiche les informations d’état des connecteurs supplémentaires, y compris *Windows Defender Advanced Threat Protection* (ATP) et d’autres connecteurs Mobile Threat Defense.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune de lui accordant l’accès en lecture seule à certains rôles d’Azure Active Directory <!-- 3637917 -->
Nous allons l’octroi Qu'intune accès en lecture seule aux rôles Azure AD suivants. Autorisations accordées aux rôles d’Azure AD remplacent les autorisations accordées avec le contrôle d’accès en fonction du rôle Intune (RBAC).

Accès en lecture seule aux données d’audit de Intune :

- Administrateur de conformité
- Administrateur des données de conformité

Accès en lecture seule à toutes les données d’Intune :

- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur Sécurité
- Lecteur global

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>Faciliter l’accès aux paramètres de Diagnostic   <!-- 3804627   -->
Nous ajoutons une nouvelle option pour le **journaux d’Audit** panneau chaque charge de travail du journal d’Audit dans la console Intune que vous pouvez utiliser pour ouvrir directement le *les paramètres de Diagnostic* page.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>Créer et utiliser des profils de configuration d’appareil sur les appareils Android Zebra dans Intune <!-- 3895244  -->
Intune prendra en charge de configuration des appareils Android Zebra. Plus précisément, vous serez en mesure de : 

- Créer un profil de configuration d’appareil et appliquer les paramètres aux appareils Android Zebra à l’aide de profils de mobilité Extensions (MX) générés par StageNow (**configuration de l’appareil** > **profils**  >  **Créer un profil** > **Android** pour la plateforme).

S'applique à :  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Déploiement en ligne d’un Microsoft Store sous licence pour les applications métier <!-- 1672660  -->
Vous serez en mesure d’assigner un Microsoft Store sous licence en ligne obligatoire pour les applications métier dans le contexte d’appareil. Un Microsoft Store pour une application métier déployé de cette façon permet à l’application d’être installée pour tous les utilisateurs sur l’appareil. Seuls les appareils de bureau Windows 10 version RS4 et ultérieures sont concernés. L’option d’installation dans le contexte d’appareil est disponible dans la page d’affectation des applications clientes pour les applications sous licence en ligne MSFB.

## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.
