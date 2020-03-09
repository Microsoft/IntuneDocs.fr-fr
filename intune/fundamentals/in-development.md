---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260229"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>En développement pour Microsoft Intune - Mars 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Recibler les clips web vers Microsoft Edge sur les appareils iOS/iPadOS<!-- 5455276 -->
Les clips web, qui agissent comme des applications web épinglées sur des appareils iOS/iPadOS, devront être mis à jour. Les clips web nouvellement déployés s’ouvrent dans Microsoft Edge au lieu d’Intune Managed Browser s’ils doivent s’ouvrir dans un navigateur protégé. Vous devez recibler des clips web préexistants pour faire en sorte qu’ils s’ouvrent dans Microsoft Edge au lieu de Managed Browser.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>Mises à jour du Portail d’entreprise macOS et iOS<!-- 5779439, 5780234  -->
Le volet Profil dans le Portail d’entreprise macOS et iOS va être mis à jour pour inclure le bouton de déconnexion. Cette mise à jour inclura aussi des améliorations de l’interface utilisateur visibles dans le volet Profil du Portail d’entreprise macOS. Pour plus d’informations sur le Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>Mises à jour du volet Branding et personnalisation<!-- 5236032 -->
Nous mettons à jour le volet Intune actuellement nommé « Branding et personnalisation » en y apportant les améliorations suivantes :

- Renommage du volet en **Personnalisation**.
- Amélioration de l’organisation et de la présentation des paramètres.
- Amélioration des info-bulles et du texte des paramètres.

Pour voir ces paramètres dans Intune, accédez au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) et sélectionnez **Administration de locataire** > **Personnalisation**. Pour plus d’informations sur la personnalisation actuelle, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>Configurer l’extension d’application d’authentification unique Microsoft Azure AD pour iOS<!-- 567534  -->
L’équipe Microsoft Azure AD développe actuellement une extension d’application d’authentification unique (SSO) de type redirection qui permettra aux utilisateurs de systèmes iOS et iPadOS 13.0+ d’accéder facilement aux applications et sites web Microsoft à l’aide d’une authentification unique. Quand l’extension d’application d’authentification unique AAD sera publiée, vous pourrez en quelques clics configurer l’extension SSO avec le profil **Fonctionnalités de l’appareil** > **Extension d’application d’authentification unique** dans la console d’administration. 

Pour plus d’informations sur les extensions d’application d’authentification unique iOS ou sur la configuration des fonctionnalités de l’appareil, consultez [Extension d’application d’authentification unique](~/configuration/device-features-configure.md#single-sign-on-app-extension).

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>Prise en charge du mode paysage dans le Portail d’entreprise pour iOS<!--6048329  -->
Les utilisateurs pourront inscrire leurs appareils, trouver des applications et demander un support informatique en utilisant l’orientation d’écran de leur choix. L’application détectera et adaptera automatiquement les écrans au mode portrait ou paysage, sauf si l’écran est verrouillé par les utilisateurs en mode portrait. 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Configurer si l’inscription est disponible dans le Portail d’entreprise pour Android et iOS<!-- 4260128 idready idstaged -->
Un nouveau paramètre vous permettra de configurer si la fonctionnalité d’inscription d’appareil dans le Portail d’entreprise sur des appareils Android et iOS sera disponible avec des invites, disponible sans invite ou non disponible pour les utilisateurs. Pour voir ces paramètres dans Intune, accédez au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) et sélectionnez **Administration de locataire** > **Personnalisation** > **Modifier** > **Inscription d’appareil**. Pour plus d’informations sur la personnalisation actuelle du Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Amélioration de l’expérience de connexion dans le Portail d’entreprise pour Android<!-- 6103997  -->
Nous changeons la présentation de plusieurs écrans de connexion dans l’application Portail d’entreprise pour Android afin de rendre l’expérience utilisateur plus moderne, simple et fluide.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration de l’appareil

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profils de configuration d’appareil de réseau câblé pour les appareils macOS<!-- 3508686  -->
Un nouveau profil de configuration d’appareil macOS sera disponible pour configurer les réseaux câblés (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **macOS** pour la plateforme > **Réseau câblé** pour le type de profil). Utilisez cette fonctionnalité pour créer des profils 802.1x pour gérer les réseaux câblés et déployer ces réseaux câblés sur vos appareils macOS.

S’applique à :
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>Les profils VPN avec des connexions VPN IKEv2 peuvent utiliser Always On avec les appareils iOS/iPadOS <!-- 1947932  -->
Sur les appareils iOS/iPadOS, vous pouvez créer un profil VPN qui utilise une connexion IKEv2 (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS/iPad** pour la plateforme > **VPN** pour le type de profil). Dans une prochaine mise à jour, vous pourrez configurer Always On avec IKEv2. Une fois configurés, les profils VPN IKEv2 se connectent automatiquement et restent connectés (ou se reconnectent rapidement) au VPN. Ils restent connectés même quand vous passez d’un réseau à l’autre ou que vous redémarrez les appareils.

Sur iOS/iPadOS, le VPN Always On est limité aux profils IKEv2.

Pour afficher les paramètres IKEv2 actuels que vous pouvez configurer, consultez [Ajouter des paramètres VPN sur les appareils iOS/iPadOS dans Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

S’applique à :
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>Amélioration de l’expérience de l’interface utilisateur lors de la création de profils de configuration sur des appareils iOS/iPadOS et macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
Quand vous créez un profil pour des appareils iOS/iPadOS ou macOS, l’expérience dans le Centre d’administration de gestion des points de terminaison est mise à jour. Cette modification a un impact sur les profils de configuration d’appareil suivants (**Appareils** > **Profils de configuration** > **Créer un profil** > **iOS** ou **macOS** pour la plateforme) :

- Personnalisé : iOS/iPados, macOS
- Fonctionnalités de l’appareil : iOS/iPadOS, macOS
- Restrictions de l’appareil : iOS/iPadOS, macOS
- Endpoint Protection : macOS
- Extensions : macOS
- Fichier de préférences : macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Amélioration de l’interface utilisateur lors de la création de profils de configuration OEMConfig sur des appareils Android Entreprise<!-- 5568645   -->
Quand vous créez ou que vous modifiez un profil OEMConfig pour des appareils Android Entreprise, l’expérience dans le Centre d’administration de gestion des points de terminaison est mise à jour. L’expérience mise à jour fournira un récapitulatif des paramètres que vous avez configurés. Cette modification a un impact sur le profil de configuration d’appareil OEMConfig (**Appareils** > **Profils de configuration** > **Créer un profil** > **Android Entreprise** pour la plateforme > **OEMConfig** pour le type de profil).

Cette fonctionnalité s’applique à :
- Android Entreprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>Suppression du paramètre Modification des paramètres d’approbation des applications d’entreprise dans les profils de restrictions sur les appareils iOS/iPadOS<!-- 6225131  -->
Sur les appareils iOS/iPadOS, vous créez un profil de restrictions sur l’appareil (**Appareils** > **Profils de configuration** > **Créer un profil** > **iOS/iPadOS** pour la plateforme > **Restrictions sur l’appareil** pour le type de profil). Comme le paramètre **Modification des paramètres d’approbation des applications d’entreprise** va être supprimé par Apple, il sera aussi supprimé dans Intune. Si vous utilisez actuellement ce paramètre dans un profil, ce paramètre ne sera pas impacté et il sera conservé dans votre profil existant tant que vous ne créerez pas de nouveau profil. Ce paramètre sera également supprimé des rapports dans Intune.

S’applique à :
- iOS/iPadOS

Pour voir les paramètres qui peuvent faire l’objet de restrictions, consultez [Paramètres des appareils iOS et iPadOS pour autoriser ou restreindre les fonctionnalités](../configuration/device-restrictions-ios.md).

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>Mise à jour des paramètres et valeurs des profils de configuration d’appareils pour les plateformes Windows<!-- 4091122 -->
Quand vous créez des profils de configuration d’appareils pour des plateformes Windows (**Appareils** > **Profils de configuration** > **Créer un profil** > n’importe quelle option **Windows** pour la plateforme), certains paramètres et leurs valeurs sont différents du CSP, ce qui peut prêter à confusion. Nous allons changer les noms des paramètres et leurs valeurs pour plus de clarté.

S’applique à :

- Profils de configuration des appareils Windows 10 et versions ultérieures
- Profils de configuration des appareils Windows Holographic for Business
- Profils de configuration des appareils Windows 8.1
- Profils de configuration des appareils Windows Phone 8.1

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Amélioration de l’expérience utilisateur lors de la création de profils de restrictions sur les appareils Android et Android Entreprise<!-- 5841361 -->
Nous allons améliorer l’expérience de création d’un profil pour les appareils Android ou Android Entreprise dans le Centre d’administration Endpoint Management. Ce changement va impacter les profils de configuration d’appareils suivants (**Appareils** > **Profils de configuration** > **Créer un profil** > **Administrateur d’appareil Android** ou **Android Entreprise** pour la plateforme) :

- Restrictions sur les appareils : Administrateur d’appareil Android
- Restrictions sur les appareils : Propriétaire d’appareil Android Entreprise
- Restrictions sur les appareils : Profil professionnel Android Entreprise

Pour plus d’informations sur les restrictions configurables sur les appareils, consultez [Administrateur d’appareil Android](../configuration/device-restrictions-android.md) et [Android Entreprise](../configuration/device-restrictions-android-for-work.md).

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Suppression des bundles et des tableaux de bundles dans les profils de configuration d’appareils OEMConfig sur les appareils Android Entreprise<!-- 5550355  -->
Sur les appareils Android Entreprise, vous créez et mettez à jour des profils OEMConfig. Les utilisateurs pourront supprimer des bundles et des tableaux de bundles à l’aide du **concepteur de configuration** dans Intune.

Pour plus d’informations sur les profils OEMConfig, consultez [Utiliser et gérer des appareils Android Entreprise avec OEMConfig dans Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Cette fonctionnalité s’applique à :
- Android Entreprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>Prise en charge de WPA et WPA2 dans les profils Wi-Fi d’entreprise pour iOS<!--6215273   -->
Nous allons ajouter le champ *Type de sécurité*  dans [Profil Wi-Fi d’entreprise pour iOS](../configuration/wi-fi-settings-ios.md) (sous **Appareils** > **Profils de configuration** > **Créer un profil**, sélectionnez **iOS/iPadOS** comme *Plateforme*, puis **Wi-Fi** comme *Profil*). Cela est similaire aux options disponibles pour un profil Wi-Fi de base pour iOS. Après ce changement, vous pourrez créer des profils qui spécifient un type de sécurité **WPA-Entreprise** ou **WPA/WPA2-Entreprise**, puis choisir un *Type EAP*.

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>Nouvelle expérience utilisateur pour les profils de types certificat, e-mail, VPN et Wi-Fi<!-- 5615208   -->
Nous améliorons l’[expérience utilisateur](../configuration/device-profile-create.md) dans le Centre d’administration Endpoint Management (**Appareils** > **Profils de configuration** > **Créer un profil**) afin de vous permettre de créer et modifier les types de profils ci-dessous. La nouvelle expérience fournira les mêmes paramètres qu’auparavant, mais elle utilisera un processus de type Assistant qui réduira le recours au défilement horizontal. Vous n’aurez pas besoin de modifier vos configurations existantes avec la nouvelle expérience.
- Informations d’identification dérivées
- E-mail
- Certificat PKCS
- Certificat importé PKCS
- Certificat SCEP
- Certificat approuvé
- VPN
- Wi-Fi

(Sous **Appareils** > **Profils de configuration** > **Créer un profil**, sélectionnez l’un des profils ci-dessus comme *Type de profil*.)

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>Configurer l’application Microsoft Defender ATP pour macOS  <!-- 5520115  -->
Vous pourrez bientôt configurer les [paramètres](../protect/endpoint-protection-macos.md) de l’application Microsoft Defender ATP sur des appareils macOS en utilisant un profil de configuration d’appareil Endpoint Protection (**Appareils** > **Profils de configuration** > **Créer un profil**, sélectionner **macOS** comme *Plateforme* et **Endpoint Protection** comme *Type de profil*). Huit paramètres seront disponibles pour la configuration des appareils macOS. 

Defender ATP est pris en charge sur macOS 10.13 (High Sierra) et versions ultérieures ; l’application [Microsoft Defender ATP](../apps/apps-advanced-threat-protection-macos.md) devra être déployée sur l’appareil *après* l’application de ces paramètres. Les paramètres devront être envoyés à l’appareil avant le début du déploiement de l’application. Les versions bêta de macOS ne seront pas prises en charge.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>Nouveau paramètre FileVault dans la stratégie de configuration d’appareils Endpoint Protection pour macOS<!-- 5459801   -->
Nous ajoutons un nouveau paramètre à la catégorie FileVault dans le modèle [Endpoint Protection pour macOS](../protect/endpoint-protection-macos.md) : Masquer la clé de récupération. (Sous **Appareils** > **Profils de configuration** > **Créer un profil**, sélectionnez **macOS** comme *Plateforme* et **Endpoint Protection** comme *Type de profil*.) Ce paramètre masque la clé personnelle à l’utilisateur final durant le chiffrement FileVault 2. L’utilisateur de l’appareil peut afficher sa clé de récupération personnelle à tout moment à partir de l’application Portail d’entreprise iOS ou à partir du site web du Portail d’entreprise pour l’appareil macOS chiffré. Pour voir sa clé de récupération personnelle, l’utilisateur doit afficher les détails de l’appareil, puis cliquer sur *Obtenir la clé de récupération*.

Ce paramètre ne sera pas disponible dans les stratégies déjà créées. Vous devrez recréer les stratégies FileVault et configurer l’utilisation de ce paramètre. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>Changement de l’interface utilisateur pour configurer une stratégie de conformité <!-- 3961639  -->
Nous changeons l’interface utilisateur pour configurer des stratégies de conformité dans Microsoft Endpoint Manager (**Appareils** > **Stratégies de conformité** > **Stratégies** > **Créer une stratégie**). La nouvelle expérience utilisateur fournira les mêmes paramètres et valeurs que ceux que vous utilisiez auparavant. Cette expérience utilisera un processus de type Assistant pour créer une stratégie de conformité ; elle inclura la page dans laquelle vous ajouterez les *Affectations* de la stratégie, puis une page *Résumé* où vous pourrez vérifier votre configuration avant de créer la stratégie. 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Configurer l’agent Optimisation de la distribution pour le téléchargement du contenu d’applications Win32<!-- 5410945  -->
Vous pourrez configurer l’agent Optimisation de la distribution pour télécharger le contenu d’applications Win32 en arrière-plan ou au premier plan en fonction de l’affectation. Pour les applications Win32 existantes, le contenu continuera d’être téléchargé en arrière-plan. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**. Sélectionnez **Windows 10 et ultérieur** comme **Plateforme**. Sous **Type de profil**, sélectionnez **Optimisation de la distribution**. Pour plus d’informations sur l’agent Optimisation de la distribution, consultez [Gestion des applications Win32 - Optimisation de la distribution](~/apps/apps-win32-app-management.md#delivery-optimization).


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Changer l’utilisateur principal pour les appareils Windows <!-- 3794742 -->
Vous serez en mesure de changer l’utilisateur principal pour les appareils Windows hybrides et joints à Azure AD. Pour cela, accédez à **Intune** > **Appareils** > **Tous les appareils** > choisissez un appareil > **Propriétés** > **Utilisateur principal**. 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Nouveau rapport Android dans la page de présentation des appareils Android<!-- 5435435 -->
Nous allons ajouter un rapport dans la console d’administration Microsoft Endpoint Manager, dans la page de présentation des appareils Android qui indique le nombre d’appareils Android inscrits dans chaque solution de gestion des appareils. Ce graphique (comme le même graphique déjà présent dans la console Azure) présente le nombre d’appareils inscrits d’administrateur d’appareils avec profil professionnel entièrement gérés et dédiés. Pour voir le rapport, choisissez **Appareils** > **Android** > **Vue d’ensemble**.

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>Prise en charge des scripts PowerShell pour les appareils BYOD<!-- 1862833  -->
Les scripts PowerShell prendront en charge les appareils Azure AD inscrits auprès d’Intune. Pour plus d’informations sur PowerShell, consultez [Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune](~/apps/intune-management-extension.md). Cette fonctionnalité ne prend pas en charge les appareils qui exécutent Windows 10 Famille.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>Propriétés supplémentaires pour l’inventaire d’appareils avec l’entrepôt de données<!-- 6125732  -->
Des propriétés d’inventaire des appareils supplémentaires seront disponibles avec l’entrepôt de données Intune. Les propriétés suivantes seront exposées via la collection [devices](~/developer/intune-data-warehouse-collections.md#devices) :
- Capacité de stockage 
- Capacité de mémoire
- Version d’Office 365
- Modèle de l’appareil

Pour plus d’informations sur l’entrepôt de données, consultez [API Entrepôt de données Microsoft Intune](~/developer/reports-nav-intune-data-warehouse.md).

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Guider les utilisateurs pour passer de la gestion de l’administrateur d’appareil Android à la gestion des profils professionnels<!--5857738-->
Nous publions un nouveau paramètre de conformité pour la plateforme d’administration des appareils Android. Ce paramètre vous permet de rendre un appareil non conforme s’il est géré avec la gestion de l’administrateur d’appareil.

Sur ces appareils non conformes, dans la page **Paramètres de mise à jour de l’appareil**, les utilisateurs verront le message **Déplacer vers la nouvelle configuration de la gestion des appareils**. S’ils appuient sur le bouton **Résoudre**, ils seront guidés dans les étapes suivantes :

1. Désinscription de la gestion de l’administrateur d’appareil
2. Inscription à la gestion des profils professionnels
3. Résolution des problèmes de conformité 
 
Google diminue peu à peu le support des administrateurs d’appareils dans les nouvelles versions Android dans le but de passer à une gestion des appareils moderne, plus riche et plus sécurisée avec Android Entreprise.  Intune assurera uniquement le support complet des appareils Android gérés par l’administrateur d’appareil qui exécutent Android 10 ou version ultérieure jusqu’au deuxième trimestre 2020. Les appareils gérés par l’administrateur d’appareil (à l’exception des appareils Samsung) et qui exécutent Android 10 ou une version ultérieure ne pourront plus être entièrement gérés après cette date. En particulier, les appareils impactés ne recevront pas de nouvelles exigences en matière de mot de passe. Pour plus d’informations, consultez cette [remarque](#decreasing-support-for-android-device-administrator).

### <a name="retire-noncompliant-devices---1827291---"></a>Mettre hors service les appareils non conformes<!-- 1827291 -->
Nous ajoutons une nouvelle action de conformité facultative qui permet de mettre hors service un appareil non conforme (sous **Appareils** > **Stratégies de conformité** > **Stratégies** > **Créer une stratégie**, accédez à la page *Actions en cas de non-conformité* pour voir les *actions*  possibles).  La mise hors service d’un appareil non conforme supprime toutes les données de l’entreprise et met fin à la gestion de l’appareil par Intune. Cette action s’exécute quand la valeur configurée en jours est atteinte. La valeur minimale est 30 jours.  Une approbation explicite de l’administrateur est nécessaire pour mettre les appareils hors service dans la section *Mettre hors service les appareils non conformes*, où les administrateurs peuvent mettre hors service tous les appareils éligibles.

### <a name="new-information-in-device-details---5604099---"></a>Nouvelles informations dans les détails de l’appareil<!-- 5604099 -->
Les informations suivantes figureront dans la page **Vue d’ensemble** des appareils :
- Capacité de stockage (quantité de stockage physique sur l’appareil)
- Capacité de mémoire (quantité de mémoire physique sur l’appareil)

### <a name="script-support-for-macos-devices---4280361----"></a>Prise en charge des scripts sur les appareils macOS<!-- 4280361  -->
Vous pourrez ajouter et déployer des scripts sur des appareils macOS. Cette prise en charge offre de nouvelles possibilités de configuration des appareils macOS par rapport aux fonctionnalités MDM natives sur les appareils macOS. 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>Mise à jour du workflow d’aide et de support pour prendre en charge des services supplémentaires<!-- 5654170 -->
Nous mettons à jour la page Aide et support dans le Centre d’administration Microsoft Endpoint Manager afin de vous permettre de sélectionner le type de gestion que vous utilisez et ainsi de bénéficier d’une prise en charge plus adaptée (**Dépannage + support** >  **Aide et support**). Après ce changement, vous pourrez sélectionner l’un des types de gestion suivants :
- Configuration Manager (incluant Desktop Analytics)
- Intune
- Cogestion

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>Sécurité

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Prise en charge des informations d’identification dérivées sur les appareils Android COBO<!--4839592-->
Vous pouvez utiliser des informations d’identification dérivées sur des appareils Android Entreprise complètement managés. Une prise en charge sera incluse pour la récupération des informations d’identification dérivées pour Entrust Datacard, Intercede et DISA Purebred. Vous pourrez utiliser des informations d’identification dérivées pour l’authentification de l’application, le Wi-Fi, le VPN ou la signature et/ou le chiffrement S/MIME avec les applications qui le prennent en charge.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Utiliser une stratégie antivirus pour gérer les paramètres de l’antivirus Microsoft Defender et l’expérience de sécurité Windows<!--6131401 -->
À partir du nœud *Sécurité du point de terminaison*, vous pouvez configurer les paramètres de l’**antivirus**. Quand vous configurez la stratégie pour l’antivirus, vous définissez les paramètres de vos appareils Windows 10 via deux types de profils :

- Antivirus Microsoft Defender : gérez les paramètres pour la protection cloud, les exclusions de l’antivirus, la remédiation, les options d’analyse, etc.
- Expérience de sécurité Windows : gérez l’expérience des utilisateurs pour les paramètres de sécurité Windows sur leurs appareils. Vous serez en mesure de configurer ce que les utilisateurs finaux peuvent voir dans le Centre de sécurité Microsoft Defender et les notifications qu’ils reçoivent.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>Clé de récupération chiffrée personnelle de l’utilisateur<!-- 6273943 -->
Une nouvelle fonctionnalité Intune sera proposée pour permettre aux utilisateurs de récupérer leur clé de récupération **FileVault** chiffrée personnelle pour des appareils Mac à partir de l’application Portail d’entreprise Android ou de l’application Intune pour Android. Ces deux applications contiendront un lien permettant d’ouvrir un navigateur Chrome et d’accéder au site web du Portail d’entreprise, où l’utilisateur trouvera la clé de récupération **FileVault** nécessaire pour accéder à ses appareils Mac. Pour plus d’informations sur le chiffrement, consultez [Utiliser le chiffrement d’appareil avec Intune](~/protect/encrypt-devices.md).

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>Paramètres des préférences de confidentialité pour les appareils macOS<!-- 2934232 --> 
Dans la version macOS Catalina 10.15, Apple a ajouté de nouvelles améliorations en matière de sécurité et de confidentialité. Par défaut, les applications et les processus ne peuvent pas accéder à des données spécifiques sans le consentement des utilisateurs. Si les utilisateurs ne donnent pas leur consentement, les applications et les processus peuvent échouer. Intune ajoute la prise en charge de paramètres qui permettent aux administrateurs informatiques de donner ou de refuser le consentement à l’accès aux données pour le compte d’utilisateurs finaux sur des appareils exécutant macOS 10.14 ou une version ultérieure. Ces paramètres garantissent que les applications et les processus continuent de fonctionner correctement et réduisent le nombre d’invites présentées aux utilisateurs finaux. 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Mise à jour du texte et des étiquettes de l’interface utilisateur pour les paramètres des profils Endpoint Protection Windows 10<!-- 5983747 -->
Nous modifions le texte de plusieurs paramètres configurables dans les profils de configuration d’appareils Windows 10 dans l’optique de clarifier l’usage et les résultats prévus de ces paramètres. 

Les paramètres que nous mettons à jour concernent les profils de configuration d’appareils Windows 10 pour : 
- [Restrictions sur l’appareil](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Antivirus Microsoft Defender  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Antivirus Microsoft Defender

Les paramètres pris en charge avec Intune ne sont pas modifiés. Il s’agit uniquement d’une mise à jour du texte de l’interface utilisateur visible dans le Centre d’administration Microsoft Endpoint Management. 


<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).



