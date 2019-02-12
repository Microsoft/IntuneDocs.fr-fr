---
title: Fonctionnalités et paramètres d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Vue d’ensemble des différents profils d’appareil Microsoft Intune, notamment les profils de fonctionnalités, restrictions, e-mail, Wi-Fi, VPN, Éducation, certificats, mise à niveau Windows 10, BitLocker et Windows Defender, Protection des informations Windows, modèles d’administration et paramètres de configuration d’appareil personnalisés dans le Portail Azure. Utilisez ces profils pour gérer et protéger les données et les appareils de votre entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b9bd8aaca9aaf6e39c7a120518eeca1cef31511
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845089"
---
# <a name="apply-features-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Appliquer des paramètres de fonctionnalités sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune

Microsoft Intune inclut des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils de votre organisation. Ces paramètres et fonctionnalités sont ajoutés aux « profils de configuration ». Vous pouvez créer des profils pour différents appareils, différentes plateformes, notamment iOS, Android et Windows, puis utiliser Intune pour appliquer le profil de votre choix aux appareils de votre organisation.

Exemples de profil :

- Sur les appareils Windows 10, utilisez un modèle de profil qui bloque les contrôles ActiveX dans Internet Explorer.
- Sur les appareils iOS et macOS, autorisez les utilisateurs à utiliser les imprimantes AirPrint de votre organisation.
- Autorisez ou empêchez l’accès à Bluetooth sur l’appareil.
- Créez un profil Wi-Fi ou VPN permettant à différents appareils d’accéder à votre réseau d’entreprise.
- Gérez les mises à jour logicielles, notamment le moment de leur installation.
- Exécutez un appareil Android, un appareil kiosque dédié pouvant exécuter une ou plusieurs applications.

Cet article liste les étapes permettant de créer un profil et donne une vue d’ensemble des différents types de profil que vous pouvez créer. Utilisez ces profils pour autoriser ou empêcher l’accès à certaines fonctionnalités sur les appareils.

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Intune**.

2. Sélectionnez **Configuration de l’appareil**. Les options suivantes sont disponibles :

    - **Vue d’ensemble** : liste l’état de vos profils et fournit des détails supplémentaires sur les profils que vous avez affectés aux utilisateurs et aux appareils.
    - **Gérer** : créez des profils d’appareil, chargez des [scripts PowerShell](intune-management-extension.md) personnalisés à exécuter dans le profil, et ajoutez des forfaits de données aux appareils via [eSIM](esim-device-configuration.md).
    - **Surveiller** : vérifiez l’état d’un profil (réussite ou échec), et consultez les journaux de vos profils.
    - **Configurer** : ajoutez une autorité de certification (SCEP ou PFX), ou activez la [Gestion des dépenses de télécommunications](telecom-expenses-monitor.md) dans le profil.

3. Sélectionnez **Profils** > **Créer un profil**. Entrez les propriétés suivantes :

   - **Nom** : Entrez un nom descriptif pour le profil.
   - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :  

       - **Android**
       - **Android Entreprise**
       - **iOS**
       - **MacOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 et versions ultérieures**
       - **Windows 10 et versions ultérieures**

   - **Type de profil** : Sélectionnez le type des paramètres à créer. La liste affichée dépend de la **plateforme** choisie :

       - [Modèles d’administration](administrative-templates-windows.md)
       - [Personnalisé](custom-settings-configure.md)
       - [Optimisation de la distribution](delivery-optimization-windows.md)
       - [Fonctionnalités de l’appareil](device-features-configure.md)
       - [Restrictions relatives aux appareils](device-restrictions-configure.md)
       - [Mise à niveau de l’édition et changement de mode](edition-upgrade-configure-windows-10.md)
       - [Éducation](education-settings-configure.md)
       - [Courrier électronique](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Identity protection](identity-protection-configure.md)  
       - [Kiosque](kiosk-settings.md)
       - [Certificat PKCS](certficates-pfx-configure.md)
       - [Certificat SCEP](certificates-scep-configure.md)
       - [Certificat approuvé](certificates-configure.md)
       - [Stratégies de mise à jour](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Protection des informations Windows](windows-information-protection-configure.md)

     Par exemple, si vous sélectionnez **iOS** pour la plateforme, les options de type de votre profil ressemblent à ce qui suit :

     ![Créer un profil iOS dans Intune](./media/create-device-profile.png)

4. Cliquez sur **Paramètres**. Les paramètres sont organisés par catégorie. Sélectionnez une catégorie pour voir la liste de tous les paramètres que vous pouvez configurer.

5. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements.

Pour plus d’informations sur les différents types de profil, lisez les sections suivantes de cet article.

## <a name="administrative-templates-preview"></a>Modèles d’administration (préversion)

Les [modèles d’administration](administrative-templates-windows.md) incluent des centaines de paramètres que vous pouvez configurer pour Internet Explorer, OneDrive, le Bureau à distance, Word, Excel ainsi que d’autres programmes Office, et bien plus encore.

Ces modèles offrent aux administrateurs une vue claire et simplifiée des paramètres, à l’image de la stratégie de groupe. Toutefois, ils sont basés sur le cloud à 100 %. 

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="device-features"></a>Fonctionnalités de l’appareil

Le profil [Fonctionnalités de l’appareil](device-features-configure.md) contrôle les fonctionnalités des appareils iOS et macOS, par exemple AirPrint, les notifications et les messages d’écran de verrouillage.

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
- Windows 10 et versions ultérieures
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
- Windows 10 et versions ultérieures

## <a name="vpn"></a>VPN

Le profil [Paramètres VPN](vpn-settings-configure.md) affecte des profils VPN aux utilisateurs et appareils de votre organisation, afin qu’ils puissent se connecter au réseau facilement et en toute sécurité. 

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès à distance sécurisé à votre réseau d’entreprise. Les appareils utilisent un profil de connexion VPN pour établir une connexion avec votre serveur VPN. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 et versions ultérieures

## <a name="wi-fi"></a>Wi-Fi

Le profil [Paramètres Wi-Fi](wi-fi-settings-configure.md) affecte les paramètres de réseau sans fil aux utilisateurs et appareils. Quand vous affectez un profil Wi-Fi, vos utilisateurs ont accès à votre Wi-Fi d’entreprise sans avoir à le configurer eux-mêmes. 

Cette fonctionnalité prend en charge : 

- Android
- iOS
- macOS
- Windows 8.1 (importation uniquement)
- Windows 10 et versions ultérieures

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

Pour plus d’informations sur les stratégies de mise à jour des appareils Windows, consultez [Optimisation de la distribution](delivery-optimization-windows.md). 

Cette fonctionnalité prend en charge :
- iOS

## <a name="certificates"></a>Certificats

Le profil [Certificats](certificates-configure.md) configure des certificats approuvés, SCEP et PKCS qui sont affectés aux appareils et utilisés pour authentifier le Wi-Fi, le VPN et les profils de messagerie.

Cette fonctionnalité prend en charge : 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 et versions ultérieures

## <a name="windows-information-protection-profile"></a>Profil Protection des informations Windows

Le profil [Protection des informations Windows](windows-information-protection-configure.md) configure une protection contre la fuite de données sans interférence avec l’expérience de l’employé. Il permet également de protéger les données et les applications d’entreprise contre les fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés utilisent sur le lieu de travail. L’utilisation de la fonctionnalité Protection des informations Windows ne nécessite aucun changement dans votre environnement ou les autres applications.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures

## <a name="shared-multi-user-device"></a>Appareil multiutilisateur partagé

[Windows 10](shared-user-device-settings-windows.md) et [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) comprennent des paramètres permettant de gérer les appareils employés par plusieurs utilisateurs. Ces appareils sont également appelés appareils partagés ou PC partagés. Quand un utilisateur se connecte à l’appareil, vous choisissez s’il peut changer les options de veille ou enregistrer des fichiers sur cet appareil. Dans un autre cas de figure, vous pouvez créer une stratégie qui supprime les informations d’identification inactives des appareils Windows HoloLens pour économiser de l’espace.

Ces paramètres d’appareils multiutilisateur partagés permettent à un administrateur de contrôler certaines fonctionnalités et de gérer les appareils partagés à l’aide d’Intune.

Cette fonctionnalité prend en charge :

- Windows 10 et versions ultérieures
- Windows Holographic for Business

## <a name="custom-profile"></a>Profil personnalisé

Les [paramètres personnalisés](custom-settings-configure.md) permettent aux administrateurs d’affecter des paramètres d'appareil qui ne sont pas intégrés à Intune. Par exemple, sur les appareils Android, vous pouvez entrer des valeurs OMA-URI. Pour les appareils iOS, vous pouvez importer un fichier de configuration que vous avez créé dans l’outil Apple Configurator. 

Cette fonctionnalité prend en charge :

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Gérer et dépanner

[Gérez vos profils](device-profile-monitor.md) pour vérifier l’état des appareils et les profils affectés. Ceci vous aide aussi à résoudre les conflits en visualisant les paramètres qui provoquent un conflit et les profils qui contiennent ces paramètres. [Problèmes courants et résolutions](device-profile-troubleshoot.md) fournit des questions et réponses qui vous aident à utiliser les profils, notamment ce qui se passe quand un profil est supprimé, la cause de l’envoi de notifications à des appareils, etc.

## <a name="next-steps"></a>Étapes suivantes
Choisissez votre plateforme et lancez-vous :

