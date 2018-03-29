---
title: Profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Vue d’ensemble des différents profils d’appareil Microsoft Intune, y compris les profils de fonctionnalités, restrictions, messagerie, Wi-Fi, VPN, Éducation, certificats, mise à niveau Windows 10, BitLocker et Windows Defender, Protection des informations Windows et des paramètres de configuration d’appareil personnalisés dans le portail Azure. Utilisez ces profils pour gérer et protéger les données et les appareils de votre entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e92a10f51fb403c802c1c6d3ea79ccf49a1e93fb
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Que sont les profils d’appareil Microsoft Intune ?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune intègre des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils au sein de votre organisation. Ces paramètres et fonctionnalités sont gérés à l’aide de profils. Exemples de profil : 

- Un profil Wi-Fi qui offre un accès à votre Wi-Fi d’entreprise à différents appareils
- Un profil VPN qui offre un accès à votre serveur VPN à différents appareils au sein de votre réseau d’entreprise

Cette rubrique fournit une vue d’ensemble des différents profils que vous pouvez créer pour vos appareils. Utilisez ces profils pour autoriser et/ou empêcher certaines fonctionnalités sur les appareils.

## <a name="before-you-begin"></a>Avant de commencer
Pour voir les fonctionnalités disponibles, ouvrez le [portail Azure](https://portal.azure.com), puis votre ressource Intune. 

La **configuration de l’appareil** comprend les options suivantes :

- **Vue d’ensemble** : Répertorie l’état de vos profils et fournit des détails supplémentaires sur les profils que vous avez affectés aux utilisateurs et appareils
- **Gérer** : Créez des profils d’appareil et chargez des [scripts PowerShell](intune-management-extension.md) personnalisés à exécuter dans le profil
- **Surveiller** : Vérifiez l’état d’un profil (réussite ou échec) et affichez les journaux de vos profils
- **Configurer** : Ajouter une autorité de certification (SCEP ou PFX) ou activez la Gestion des dépenses de télécommunications sur le profil

## <a name="create-the-profile"></a>Créer le profil

Le menu [Créer des profils d’appareil](device-profile-create.md) fournit des instructions pas à pas pour créer un profil. 

## <a name="device-features-profile"></a>Profil Fonctionnalités de l’appareil

Le profil [Fonctionnalités de l’appareil](device-features-configure.md) contrôle les fonctionnalités sur les appareils iOS et MacOS comme AirPrint, les notifications et les configurations d’appareils partagées.

Cette fonctionnalité prend en charge :  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>Profil Restrictions d’appareil
Le profil [Restrictions d’appareil](device-restrictions-configure.md) contrôle la sécurité, le matériel, le partage de données et d’autres paramètres sur les appareils. Par exemple, vous créez un profil de restriction d’appareil qui empêche les utilisateurs d’appareils iOS d’utiliser l’appareil photo. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Collaboration

## <a name="email-profile"></a>Profil de messagerie
Le profil [Paramètres de messagerie](email-settings-configure.md) crée, affecte et surveille les paramètres de messagerie Exchange ActiveSync sur les appareils. Les profils de messagerie permettent de garantir la cohérence, réduire les appels au support et permettent aux utilisateurs finaux d’accéder à la messagerie d’entreprise sur leurs appareils personnels sans aucune autre configuration de leur part. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="wi-fi-profile"></a>Profil Wi-Fi
Le profil [Paramètres Wi-Fi](wi-fi-settings-configure.md) affecte les paramètres de réseau sans fil aux utilisateurs et appareils. Quand vous affectez un profil Wi-Fi, vos utilisateurs ont accès à votre Wi-Fi d’entreprise sans avoir à le configurer eux-mêmes. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows 8.1 (importation uniquement)

## <a name="vpn-profile"></a>Profil VPN
Le profil [Paramètres VPN](vpn-settings-configure.md) affecte des profils VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter au réseau facilement et en toute sécurité. 

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès à distance sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec le serveur VPN. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>Profil Éducation
Le profil [Paramètres Éducation](education-settings-configure.md) configure les options pour [l’application Windows Take a Test](https://education.microsoft.com/gettrained/win10takeatest). Lorsque vous configurez ces options, aucune autre application ne peut s’exécuter sur l’appareil tant que le test n’est pas terminé.

## <a name="certificates-profile"></a>Profil Certificats
Le profil [Certificats](certificates-configure.md) configure des certificats approuvés, SCEP et PKCS qui peuvent être affectés aux appareils et utilisés pour authentifier le Wi-Fi, le VPN et les profils de messagerie.

Cette fonctionnalité prend en charge : 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>Profil Mise à niveau d’édition
Le profil [Mises à niveau d’édition Windows 10](edition-upgrade-configure-windows-10.md) met automatiquement à niveau les appareils qui exécutent des versions de Windows 10 vers une édition plus récente.

Cette fonctionnalité prend en charge : Windows 10 uniquement

## <a name="endpoint-protection-profile"></a>Profil Endpoint Protection
Le profil [Paramètres Endpoint Protection pour Windows 10](endpoint-protection-windows-10.md) configure les paramètres de BitLocker et Windows Defender pour les appareils Windows 10.

Pour intégrer Windows Defender - Protection avancée contre les menaces avec Microsoft Intune, consultez [Configurer des points de terminaison à l’aide des outils de gestion des appareils mobiles](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection).

Cette fonctionnalité prend en charge : Windows 10 uniquement

## <a name="windows-information-protection-profile"></a>Profil Protection des informations Windows
Le profil [Protection des informations Windows](windows-information-protection-configure.md) configure une protection contre la fuite de données sans interférence avec l’expérience de l’employé. Il permet également de protéger les données et les applications d’entreprise contre les fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés utilisent sur le lieu de travail. Cette protection n’implique aucun changement dans votre environnement ni d’autres applications.

Cette fonctionnalité prend en charge : Windows 10 uniquement

## <a name="custom-profile"></a>Profil personnalisé
Le profil [Paramètres personnalisés](custom-settings-configure.md) vous permet d’affecter des paramètres d’appareil qui ne sont pas intégrés à Intune. Par exemple, sur les appareils Android, vous pouvez entrer des valeurs OMA-URI. Pour les appareils iOS, vous pouvez importer un fichier de configuration que vous avez créé dans l’outil Apple Configurator. 

Cette fonctionnalité prend en charge :

- Android
- iOS
- macOS
- Windows Phone 8.1