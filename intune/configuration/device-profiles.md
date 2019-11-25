---
title: Fonctionnalités et paramètres d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Vue d’ensemble des différents profils d’appareil Microsoft Intune. Obtenez des informations sur les profils de fonctionnalités, restrictions, e-mail, Wi-Fi, VPN, Éducation, certificats, mise à niveau Windows 10, BitLocker et Microsoft Defender, Protection des informations Windows, modèles d’administration et paramètres de configuration d’appareil personnalisés dans le Portail Azure. Utilisez ces profils pour gérer et protéger les données et les appareils de votre entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0dd9eddd986e6717e6bf706b02a7b06f712a032
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059894"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune inclut des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils de votre organisation. Ces paramètres et fonctionnalités sont ajoutés aux « profils de configuration ». Vous pouvez créer des profils pour différents appareils et différentes plateformes, notamment iOS, Android et Windows. Ensuite, utilisez Intune pour appliquer ou « attribuer » le profil aux appareils.

Dans le cadre de votre solution de gestion des périphériques mobiles (GPM), utilisez ces profils de configuration pour effectuer différentes tâches. Exemples de profil :

- Sur les appareils Windows 10, utilisez un modèle de profil qui bloque les contrôles ActiveX dans Internet Explorer.
- Sur les appareils iOS et macOS, autorisez les utilisateurs à utiliser les imprimantes AirPrint de votre organisation.
- Autorisez ou empêchez l’accès à Bluetooth sur l’appareil.
- Créez un profil Wi-Fi ou VPN permettant à différents appareils d’accéder à votre réseau d’entreprise.
- Gérez les mises à jour logicielles, notamment le moment de leur installation.
- Exécutez un appareil Android, un appareil kiosque dédié pouvant exécuter une ou plusieurs applications.

Cet article fournit une vue d’ensemble des différents types de profils que vous pouvez créer. Utilisez ces profils pour autoriser ou empêcher l’accès à certaines fonctionnalités sur les appareils.

## <a name="administrative-templates"></a>Modèles d’administration

Les [modèles d’administration](administrative-templates-windows.md) incluent des centaines de paramètres que vous pouvez configurer pour Internet Explorer, OneDrive, le Bureau à distance, Word, Excel ainsi que d’autres programmes Office.

Ces modèles offrent aux administrateurs une vue simplifiée des paramètres, à l’image de la stratégie de groupe. Toutefois, ils sont basés sur le cloud à 100 %.

Cette fonctionnalité prend en charge :

- Windows 10 1809 et versions ultérieures sur le microprogramme pris en charge.

## <a name="certificates"></a>Certificats

[Certificats](../protect/certificates-configure.md) permet de configurer les certificats approuvés, SCEP et PKCS qui sont attribués aux appareils. Ces certificats authentifient les profils Wi-Fi, VPN et de messagerie.

Cette fonctionnalité prend en charge : 

- Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 et versions ultérieures

## <a name="custom-profile"></a>Profil personnalisé

Les [paramètres personnalisés](custom-settings-configure.md) permettent aux administrateurs d’attribuer des paramètres d’appareil qui ne sont pas intégrés à Intune. Sur les appareils Android, vous pouvez entrer des valeurs OMA-URI. Pour les appareils iOS, vous pouvez importer un fichier de configuration que vous avez créé dans l’outil Apple Configurator.

Cette fonctionnalité prend en charge :

- Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1

## <a name="delivery-optimization"></a>Optimisation de la distribution

[L’optimisation de la distribution](delivery-optimization-windows.md) fournit une meilleure expérience pour les mises à jour logicielles. Ces paramètres remplacent les paramètres **Mises à jour logicielles** > **Anneau de mise à jour Windows 10**.

Utilisez ces paramètres pour contrôler le mode de téléchargement des mises à jour logicielles sur des appareils dans votre organisation. Par exemple, vous pouvez laisser les utilisateurs obtenir leurs propres mises à jour, ou obtenir les mises à jour avec les services cloud de l’optimisation de la distribution dans un profil d’appareil.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="device-features"></a>Fonctionnalités de l’appareil

Le profil [Fonctionnalités de l’appareil](device-features-configure.md) contrôle les fonctionnalités des appareils iOS et macOS, par exemple AirPrint, les notifications et les messages d’écran de verrouillage.

Cette fonctionnalité prend en charge :

- iOS/iPadOS
- macOS

## <a name="device-firmware-configuration-interface"></a>Interface de configuration du microprogramme d’appareil

L’[interface de configuration du microprogramme d’appareil](device-firmware-configuration-interface-windows.md) (DFCI) permet aux administrateurs d’activer ou de désactiver les paramètres UEFI (BIOS) à l’aide d’Intune. Utilisez ces paramètres pour renforcer la sécurité au niveau du microprogramme, qui est généralement plus résilient aux attaques malveillantes.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="device-restrictions"></a>Restrictions d’appareil

Le profil [Restrictions d’appareil](device-restrictions-configure.md) contrôle la sécurité, le matériel, le partage de données et d’autres paramètres sur les appareils. Par exemple, vous créez un profil de restriction d’appareil qui empêche les utilisateurs d’appareils iOS d’utiliser l’appareil photo. 

Cette fonctionnalité prend en charge :

- Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows 10 et versions ultérieures
- Windows 10 Collaboration

## <a name="edition-upgrade"></a>Mise à niveau d’édition

Le profil [Mises à niveau d’édition Windows 10](edition-upgrade-configure-windows-10.md) met automatiquement à niveau les appareils qui exécutent des versions de Windows 10 vers une édition plus récente.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="education"></a>Éducation

Le profil [Paramètres d’éducation - Windows 10](education-settings-configure.md) configure les options pour [l’application Windows Take a Test](https://education.microsoft.com/gettrained/win10takeatest). Lorsque vous configurez ces options, aucune autre application ne peut s’exécuter sur l’appareil tant que le test n’est pas terminé.

Le profil [Paramètres d’éducation - iOS](../fundamentals/education-settings-configure-ios-shared.md) utilise l’application iOS Classroom pour orienter l’apprentissage et contrôler les appareils des étudiants dans la salle de classe. Vous pouvez configurer des appareils iPad pour permettre à plusieurs étudiants de partager un seul appareil.

## <a name="email"></a>E-mail

La fonctionnalité [Paramètres de messagerie](email-settings-configure.md) crée, affecte et surveille les paramètres de messagerie Exchange ActiveSync sur les appareils. Les profils de messagerie permettent de garantir la cohérence, réduire les appels au support et permettent aux utilisateurs finaux d’accéder à la messagerie d’entreprise sur leurs appareils personnels sans aucune autre configuration de leur part. 

Cette fonctionnalité prend en charge : 

- Android
- Android Entreprise
- iOS/iPadOS
- Windows Phone 8.1
- Windows 10 et versions ultérieures

## <a name="endpoint-protection"></a>Endpoint Protection

Le profil [Paramètres Endpoint Protection pour Windows 10](../protect/endpoint-protection-windows-10.md) configure les paramètres de BitLocker et Microsoft Defender pour les appareils Windows 10.

Pour intégrer Microsoft Defender - Protection avancée contre les menaces avec Microsoft Intune, consultez [Configurer des points de terminaison à l’aide des outils de gestion des appareils mobiles](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm).

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="esim-cellular---public-preview"></a>eSIM cellulaire - Préversion publique

Les [profils cellulaires eSIM](esim-device-configuration.md) permettent aux administrateurs de configurer des plans de données cellulaires sur vos appareils gérés pour l’accès à Internet et aux données. Une fois les codes d’activation obtenus auprès de votre opérateur mobile, utilisez Intune pour importer ces codes d’activation, puis les affecter à vos appareils compatibles eSIM.

Cette fonctionnalité prend en charge :

- Windows 10 Fall Creators Update et versions ultérieures

## <a name="extensions"></a>Extensions

Les [extensions de noyau](kernel-extensions-overview-macos.md) permettent aux administrateurs d'ajouter des fonctionnalités ou des programmes au niveau du noyau sur les appareils macOS. Configurez ces paramètres pour approuver toutes les extensions d'un développeur ou d'un partenaire spécifique, ou pour autoriser des extensions spécifiques du noyau.

Cette fonctionnalité prend en charge :

- macOS

## <a name="identity-protection"></a>Protection des identités

[Identity Protection](../protect/identity-protection-configure.md) contrôle l’expérience Windows Hello Entreprise sur les appareils Windows 10 et Windows 10 Mobile. Configurez ces paramètres pour rendre Windows Hello Entreprise disponible aux utilisateurs et aux appareils, et pour spécifier les exigences relatives aux codes PIN des appareils et aux mouvements.  

Cette fonctionnalité prend en charge :  

- Windows 10 et versions ultérieures
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

Le profil [Paramètres kiosque](kiosk-settings.md) configure un appareil pour exécuter une ou plusieurs applications. Vous pouvez également personnaliser d’autres fonctionnalités sur votre kiosque, notamment un menu de démarrage et un navigateur web.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

Les paramètres Kiosk sont également disponible en tant que restrictions d’appareil pour [Android](device-restrictions-android.md#kiosk), [Android Entreprise](device-restrictions-android-for-work.md#dedicated-device-settings) et [ios](device-restrictions-ios.md#kiosk).

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md) est une norme qui permet aux OEM (fabricants d'équipements d'origine) et aux EMM (gestion de la mobilité en entreprise) de créer et de prendre en charge des fonctionnalités spécifiques aux OEM de manière standardisée sur les appareils Android Enterprise. Avec OEMConfig, un OEM crée un schéma qui définit les fonctionnalités de gestion spécifiques à l'OEM, et l'intègre à une application chargée sur Google Play. Intune lit le schéma à partir de l'application et permet aux administrateurs Intune de configurer les paramètres du schéma.

Cette fonctionnalité prend en charge :

- Android Enterprise (OEMConfig)

## <a name="powershell-scripts"></a>Scripts PowerShell

Les [scripts PowerShell sur les appareils Windows 10](../apps/intune-management-extension.md) utilisent l'extension de gestion Intune pour charger vos scripts PowerShell dans Intune, puis exécutent ces scripts sur vos appareils. Découvrez également les éléments requis pour utiliser l'extension, comment les ajouter à Intune, et d'autres informations importantes.


Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures
- Windows Holographic for Business

## <a name="shared-multi-user-device"></a>Appareil multiutilisateur partagé

[Windows 10](shared-user-device-settings-windows.md) et [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) comprennent des paramètres permettant de gérer les appareils employés par plusieurs utilisateurs. Ces appareils sont également appelés appareils partagés ou PC partagés. Quand un utilisateur se connecte à l’appareil, vous choisissez s’il peut changer les options de veille ou enregistrer des fichiers sur cet appareil. Dans un autre cas de figure, pour économiser de l’espace, vous pouvez créer un profil qui supprime les informations d’identification inactives des appareils Windows HoloLens.

Ces paramètres d’appareils multiutilisateur partagés permettent à un administrateur de contrôler certaines fonctionnalités et de gérer les appareils partagés à l’aide d’Intune.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures
- Windows Holographic for Business

## <a name="update-policies"></a>Stratégies de mise à jour

L’article [Stratégies de mise à jour iOS](../protect/software-updates-ios.md) vous montre comment créer et affecter des stratégies iOS pour installer des mises à jour logicielles sur vos appareils iOS. Vous pouvez également consulter l’état de l’installation.

Pour plus d’informations sur les stratégies de mise à jour des appareils Windows, consultez [Optimisation de la distribution](delivery-optimization-windows.md). 

Cette fonctionnalité prend en charge :

- iOS/iPadOS

## <a name="vpn"></a>VPN

Le profil [Paramètres VPN](vpn-settings-configure.md) affecte des profils VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter au réseau facilement et en toute sécurité. 

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès à distance sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec votre serveur VPN. 

Cette fonctionnalité prend en charge : 

- Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 et versions ultérieures

## <a name="wi-fi"></a>Wi-Fi

Le profil [Paramètres Wi-Fi](wi-fi-settings-configure.md) affecte les paramètres de réseau sans fil aux utilisateurs et appareils. Quand vous affectez un profil Wi-Fi, vos utilisateurs ont accès à votre Wi-Fi d’entreprise sans avoir à le configurer eux-mêmes. 

Cette fonctionnalité prend en charge : 

- Android
- Android Entreprise
- iOS/iPadOS
- macOS
- Windows 8.1 (importation uniquement)
- Windows 10 et versions ultérieures

## <a name="windows-information-protection-profile"></a>Profil Protection des informations Windows

Le profil [Protection des informations Windows](../protect/windows-information-protection-configure.md) configure une protection contre la fuite de données sans interférence avec l’expérience de l’employé. Il permet également de protéger les données et les applications d’entreprise contre les fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés utilisent sur le lieu de travail. L’utilisation de la fonctionnalité Protection des informations Windows ne nécessite aucun changement dans votre environnement ou les autres applications.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="zebra-mobility-extensions-mx"></a>Extensions Zebra Mobility (MX)

Les [extensions Zebra Mobility (MX)](android-zebra-mx-overview.md) permettent aux administrateurs d’utiliser et de gérer des appareils Zebra dans Intune. Vous créez des profils StageNow avec vos paramètres, puis utilisez Intune pour attribuer et déployer ces profils pour vos appareils Zebra. La section [Journaux StageNow et problèmes courants](android-zebra-mx-logs-troubleshoot.md) est une ressource précieuse pour résoudre les problèmes de profils et connaître les problèmes potentiels lors de l’utilisation de StageNow.

Cette fonctionnalité prend en charge :

- Android (Mobility Extensions)

## <a name="manage-and-troubleshoot"></a>Gérer et dépanner

[Gérez vos profils](device-profile-monitor.md) pour vérifier l’état des appareils et les profils affectés. Ceci vous aide aussi à résoudre les conflits en visualisant les paramètres qui provoquent un conflit et les profils qui incluent ces paramètres. [Solutions aux problèmes courants](device-profile-troubleshoot.md) permet aux administrateurs d’utiliser des profils. Il décrit ce qui se passe lorsque vous supprimez un profil, ce qui entraîne l’envoi de notifications à des appareils, et bien plus encore.

## <a name="next-steps"></a>Étapes suivantes

Choisissez votre plateforme et lancez-vous.
