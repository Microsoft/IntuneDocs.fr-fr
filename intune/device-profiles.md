---
title: Profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Vue d’ensemble des différents profils d’appareil Microsoft Intune, y compris les profils de fonctionnalités, restrictions, messagerie, Wi-Fi, VPN, Éducation, certificats, mise à niveau Windows 10, BitLocker et Windows Defender, Protection des informations Windows et des paramètres de configuration d’appareil personnalisés dans le portail Azure. Utilisez ces profils pour gérer et protéger les données et les appareils de votre entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: c9a3146b1ad5f6f7c439d2e49cf534e14d154f76
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728699"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Que sont les profils d’appareil Microsoft Intune ?

Microsoft Intune intègre des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils au sein de votre organisation. Ces paramètres et fonctionnalités sont gérés à l’aide de profils. Exemples de profil : 

- Un profil Wi-Fi qui offre un accès à votre Wi-Fi d’entreprise à différents appareils
- Un profil VPN qui offre un accès à votre serveur VPN à différents appareils au sein de votre réseau d’entreprise

Cet article fournit une vue d’ensemble des différents profils que vous pouvez créer pour vos appareils. Utilisez ces profils pour autoriser et/ou empêcher certaines fonctionnalités sur les appareils.

## <a name="before-you-begin"></a>Avant de commencer

Pour voir les fonctionnalités disponibles, ouvrez le [portail Azure](https://portal.azure.com), puis votre ressource Intune. 

La **configuration de l’appareil** comprend les options suivantes :

- **Vue d’ensemble** : Répertorie l’état de vos profils et fournit des détails supplémentaires sur les profils que vous avez affectés aux utilisateurs et appareils
- **Gérer** : Créez des profils d’appareil et chargez des [scripts PowerShell](intune-management-extension.md) personnalisés à exécuter dans le profil
- **Surveiller** : Vérifiez l’état d’un profil (réussite ou échec) et affichez les journaux de vos profils
- **Configurer** : Ajouter une autorité de certification (SCEP ou PFX) ou activez la Gestion des dépenses de télécommunications sur le profil

## <a name="create-the-profile"></a>Créer le profil

Le menu [Créer des profils d’appareil](device-profile-create.md) fournit des instructions pas à pas pour créer un profil. 

## <a name="device-features---ios-and-macos"></a>Fonctionnalités de l’appareil - iOS et macOS

Le profil [Fonctionnalités de l’appareil](device-features-configure.md) contrôle les fonctionnalités sur les appareils iOS et MacOS comme AirPrint, les notifications et les configurations d’appareils partagées.

Cette fonctionnalité prend en charge :
- iOS 
- macOS

## <a name="device-restrictions"></a>Restrictions d’appareil

Le profil [Restrictions d’appareil](device-restrictions-configure.md) contrôle la sécurité, le matériel, le partage de données et d’autres paramètres sur les appareils. Par exemple, vous créez un profil de restriction d’appareil qui empêche les utilisateurs d’appareils iOS d’utiliser l’appareil photo. 

Cette fonctionnalité prend en charge :

- Android
- Android Entreprise
- iOS
- macOS
- Windows 10
- Windows 10 Collaboration

## <a name="delivery-optimization"></a>Optimisation de la distribution

[L’optimisation de la distribution](delivery-optimization-windows.md) fournit une meilleure expérience pour les mises à jour logicielles. Ces paramètres remplacent les paramètres **Mises à jour logicielles** > **Anneau de mise à jour Windows 10**.

Utilisez ces paramètres pour contrôler le mode de téléchargement des mises à jour logicielles sur des appareils dans votre organisation. Par exemple, vous pouvez laisser les utilisateurs obtenir leurs propres mises à jour, ou obtenir les mises à jour avec les services cloud de l’optimisation de la distribution dans un profil d’appareil.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="endpoint-protection"></a>Endpoint Protection

Le profil [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md) configure les paramètres de BitLocker et Windows Defender pour les appareils Windows 10.

Pour intégrer Windows Defender - Protection avancée contre les menaces avec Microsoft Intune, consultez [Configurer des points de terminaison à l’aide des outils de gestion des appareils mobiles](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection).

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="identity-protection"></a>Protection des identités

[Identity Protection](identity-protection-configure.md) contrôle l’expérience Windows Hello Entreprise sur les appareils Windows 10 et Windows 10 Mobile. Configurez ces paramètres pour rendre Windows Hello Entreprise disponible aux utilisateurs et aux appareils, et pour spécifier les exigences relatives aux codes PIN des appareils et aux mouvements.  

Cette fonctionnalité prend en charge :  

- Windows 10 et versions ultérieures
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

Le profil [Paramètres kiosque](kiosk-settings.md) configure un appareil pour exécuter une ou plusieurs applications. Vous pouvez également personnaliser d’autres fonctionnalités sur votre kiosque, notamment un menu de démarrage et un navigateur web.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

Les paramètres Kiosk sont également disponible en tant que restrictions d’appareil pour [Android](device-restrictions-android.md#kiosk), [Android Entreprise](device-restrictions-android-for-work.md#kiosk-settings) et [ios](device-restrictions-ios.md#kiosk-supervised-only).

## <a name="email"></a>E-mail

La fonctionnalité [Paramètres de messagerie](email-settings-configure.md) crée, affecte et surveille les paramètres de messagerie Exchange ActiveSync sur les appareils. Les profils de messagerie permettent de garantir la cohérence, réduire les appels au support et permettent aux utilisateurs finaux d’accéder à la messagerie d’entreprise sur leurs appareils personnels sans aucune autre configuration de leur part. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN

Le profil [Paramètres VPN](vpn-settings-configure.md) affecte des profils VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter au réseau facilement et en toute sécurité. 

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès à distance sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec votre serveur VPN. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi

Le profil [Paramètres Wi-Fi](wi-fi-settings-configure.md) affecte les paramètres de réseau sans fil aux utilisateurs et appareils. Quand vous affectez un profil Wi-Fi, vos utilisateurs ont accès à votre Wi-Fi d’entreprise sans avoir à le configurer eux-mêmes. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows 8.1 (importation uniquement)

## <a name="esim-cellular---public-preview"></a>eSIM cellulaire - Préversion publique

Les [profils cellulaires eSIM](esim-device-configuration.md) permettent aux administrateurs de configurer des plans de données cellulaires sur vos appareils gérés pour l’accès à Internet et aux données. Une fois les codes d’activation obtenus auprès de votre opérateur mobile, utilisez Intune pour importer ces codes d’activation, puis les affecter à vos appareils compatibles eSIM.

Cette fonctionnalité prend en charge :
- Windows 10 Fall Creators Update et versions ultérieures

## <a name="education"></a>Éducation

Le profil [Paramètres d’éducation - Windows 10](education-settings-configure.md) configure les options pour [l’application Windows Take a Test](https://education.microsoft.com/gettrained/win10takeatest). Lorsque vous configurez ces options, aucune autre application ne peut s’exécuter sur l’appareil tant que le test n’est pas terminé.

Le profil [Paramètres d’éducation - iOS](education-settings-configure-ios-shared.md) utilise l’application iOS Classroom pour orienter l’apprentissage et contrôler les appareils des étudiants dans la salle de classe. Vous pouvez configurer des appareils iPad pour permettre à plusieurs étudiants de partager un seul appareil.

## <a name="edition-upgrade"></a>Mise à niveau d’édition

Le profil [Mises à niveau d’édition Windows 10](edition-upgrade-configure-windows-10.md) met automatiquement à niveau les appareils qui exécutent des versions de Windows 10 vers une édition plus récente.

Cette fonctionnalité prend en charge : 
- Windows 10 et versions ultérieures

## <a name="update-policies"></a>Stratégies de mise à jour

L’article [Stratégies de mise à jour iOS](software-updates-ios.md) vous montre comment créer et affecter des stratégies iOS pour installer des mises à jour logicielles sur vos appareils iOS. Vous pouvez également consulter l’état de l’installation.

Cette fonctionnalité prend en charge :
- iOS

## <a name="certificates"></a>Certificats

Le profil [Certificats](certificates-configure.md) configure des certificats approuvés, SCEP et PKCS qui sont affectés aux appareils et utilisés pour authentifier le Wi-Fi, le VPN et les profils de messagerie.

Cette fonctionnalité prend en charge : 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Profil Protection des informations Windows

Le profil [Protection des informations Windows](windows-information-protection-configure.md) configure une protection contre la fuite de données sans interférence avec l’expérience de l’employé. Il permet également de protéger les données et les applications d’entreprise contre les fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés utilisent sur le lieu de travail. L’utilisation de Windows Information Protection ne nécessite pas modifications de votre environnement ou d’autres applications.

Cette fonctionnalité prend en charge :
- Windows 10 et versions ultérieures

## <a name="custom-profile"></a>Profil personnalisé

Les [paramètres personnalisés](custom-settings-configure.md) permettent aux administrateurs d’affecter des paramètres d'appareil qui ne sont pas intégrés à Intune. Par exemple, sur les appareils Android, vous pouvez entrer des valeurs OMA-URI. Pour les appareils iOS, vous pouvez importer un fichier de configuration que vous avez créé dans l’outil Apple Configurator. 

Cette fonctionnalité prend en charge :

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Gérer et dépanner

[Gérez vos profils](device-profile-monitor.md) pour vérifier l’état des appareils et les profils affectés. Ceci vous aide aussi à résoudre les conflits en visualisant les paramètres qui provoquent un conflit et les profils qui contiennent ces paramètres. [Problèmes courants et résolutions](device-profile-troubleshoot.md) fournit des questions et réponses qui vous aident à utiliser les profils, notamment ce qui se passe quand un profil est supprimé, la cause de l’envoi de notifications à des appareils, etc.
