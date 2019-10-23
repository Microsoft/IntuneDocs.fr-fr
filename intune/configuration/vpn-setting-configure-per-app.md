---
title: Configurer un VPN par application pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Passez en revue les prérequis, créez un groupe pour les utilisateurs d’un réseau privé virtuel (VPN), ajoutez un profil de certificat SCEP, configurez un profil VPN par application et affectez des applications au profil VPN dans Microsoft Intune sur les appareils iOS. Répertorie également les étapes à suivre pour vérifier la connexion VPN sur l’appareil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e3c9e3bbdc65ae3f97e4be871cfaf638f1bafcd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506599"
---
# <a name="set-up-per-app-virtual-private-network-vpn-for-ios-devices-in-intune"></a>Configurer un VPN par application pour les appareils iOS dans Intune

Dans Microsoft Intune, vous pouvez créer et utiliser des réseaux privés virtuels (VPN) affectés à une application. Cette fonctionnalité est appelée « VPN par application ». Il vous incombe de choisir les applications gérées qui peuvent utiliser votre VPN sur des appareils gérés par Intune. Quand vous utilisez des VPN par application, les utilisateurs finaux se connectent automatiquement via le VPN et ont accès à des ressources de l’organisation, par exemple des documents.

Cette fonctionnalité s’applique à :

- iOS 9 et ultérieur

Consultez la documentation de votre fournisseur VPN pour savoir si votre VPN prend en charge le VPN par application.

Cet article vous montre comment créer un profil VPN par application et attribuer ce profil à vos applications. Utilisez ces étapes pour créer une expérience VPN par application sans interruption pour vos utilisateurs finaux. Pour la plupart des VPN qui prennent en charge le VPN par application, l’utilisateur ouvre une application et se connecte automatiquement au VPN.

Avec le VPN par application, certains VPN permettent une authentification par nom d’utilisateur et mot de passe. Autrement dit, les utilisateurs doivent entrer un nom d’utilisateur et un mot de passe pour se connecter au VPN.

## <a name="per-app-vpn-with-zscaler"></a>VPN par application avec Zscaler

Zscaler Private Access (ZPA) s’intègre avec Azure Active Directory (Azure AD) pour l’authentification. En utilisant ZPA, vous n’avez pas besoin des profils de [certificat approuvé](#create-a-trusted-certificate-profile) ou de [certificat SCEP ou PKCS](#create-a-scep-or-pkcs-certificate-profile) (décrits dans cet article). Si vous avez configuré un profil VPN par application pour Zscaler, le fait d’ouvrir une des applications associées ne la connecte pas automatiquement à ZPA. En effet, l’utilisateur doit d’abord se connecter à l’application Zscaler. Ensuite, l’accès à distance est limité aux applications associées.

## <a name="prerequisites-for-per-app-vpn"></a>Prérequis du VPN par application

> [!IMPORTANT]
> Votre fournisseur VPN peut avoir d’autres exigences pour le VPN par application, comme du matériel ou des licences spécifiques. Veillez à consulter leur documentation et répondez aux prérequis avant de configurer les VPN par application dans Intune.

Pour prouver son identité, le serveur VPN présente le certificat qui doit être accepté sans invite par l’appareil. Pour confirmer l’approbation automatique du certificat, créez un profil de certificat approuvé qui contient le certificat racine du serveur VPN émis par l’autorité de certification. 

### <a name="export-the-certificate-and-add-the-ca"></a>Exporter le certificat et ajouter l’autorité de certification

1. Sur votre serveur VPN, ouvrez la console d’administration.
2. Vérifiez que votre serveur VPN utilise une authentification basée sur les certificats. 
3. Exportez le fichier du certificat racine approuvé. Il a une extension .cer et vous l’ajoutez quand vous créez un profil de certificat approuvé.
4. Ajoutez le nom de l’Autorité de certification qui a émis le certificat pour l’authentification auprès du serveur VPN.

    Si l’autorité de certification présentée par l’appareil correspond à une autorité de certification de la liste des autorités de certification approuvées sur le serveur VPN, celui-ci authentifie l’appareil.

## <a name="create-a-group-for-your-vpn-users"></a>Créer un groupe pour vos utilisateurs VPN

Créez ou choisissez un groupe existant dans Azure Active Directory (Azure AD) pour les utilisateurs ou les appareils qui utilisent le VPN par application. Pour créer un groupe, consultez [Ajouter des groupes pour organiser des utilisateurs et des appareils](../fundamentals/groups-add.md).

## <a name="create-a-trusted-certificate-profile"></a>Créer un profil de certificat approuvé

Importez le certificat racine du serveur VPN émis par l’Autorité de certification dans un profil créé dans Intune. Le profil de certificat approuvé permet à l’appareil iOS d’approuver automatiquement l’Autorité de certification que présente le serveur VPN.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :
    - **Nom**
    - **Description**
    - **Plateforme** : sélectionnez **iOS**.
    - **Type de profil** : sélectionnez **Certificat approuvé**.
4. Sélectionnez l’icône de dossier, puis accédez au certificat VPN (fichier .cer) que vous avez exporté à partir de la console d’administration VPN. 
5. Sélectionnez **OK** > **Créer**.

    ![Créer un profil de certificat approuvé pour des appareils iOS dans Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-or-pkcs-certificate-profile"></a>Créer un profil de certificat SCEP ou PKCS

Le profil de certificat racine approuvé permet à l’appareil d’approuver automatiquement le serveur VPN. Le certificat SCEP ou PKCS fournit les informations d’identification du client VPN iOS au serveur VPN. Il permet à l’appareil de s’authentifier en mode silencieux sans demander un nom d’utilisateur et un mot de passe. 

Pour configurer et attribuer le certificat d’authentification client, consultez l’un des articles suivants :

- [Configurer l’infrastructure pour prendre en charge SCEP avec Intune](../protect/certificates-scep-configure.md)
- [Configurer et gérer les certificats PKCS avec Intune](../protect/certficates-pfx-configure.md)

Veillez à configurer le certificat pour l’authentification du client. Vous pouvez le définir directement dans les profils de certificat SCEP (liste **Utilisation améliorée de la clé** > **Authentification du client**). Pour PKCS, définissez l’authentification du client dans le modèle de certificat de l’autorité de certification.

![Créer un profil de certificat SCEP dans Microsoft Intune, notamment le format du nom de l’objet, l’utilisation de la clé, l’utilisation améliorée de la clé, etc.](./media/vpn-setting-configure-per-app/vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Créer un profil VPN par application

Le profil VPN contient le certificat SCEP ou PKCS avec les informations d’identification du client, les informations de connexion au VPN et l’indicateur VPN par application pour permettre à l’application iOS d’utiliser la fonctionnalité de VPN par application.

1. Dans **Intune**, sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**. 
2. Entrez les propriétés suivantes : 
    - **Nom**
    - **Description**
    - **Plateforme** : sélectionnez **iOS**.
    - **Type de profil** : sélectionnez **VPN**.
3. Dans **Type de connexion**, sélectionnez votre application de client VPN.
4. Sélectionnez **VPN de base**. Le document relatif aux [paramètres VPN iOS](vpn-settings-ios.md) liste et décrit tous les paramètres. Si vous prévoyez d’utiliser le VPN par application, veillez à définir les propriétés suivantes comme indiqué : 
    
    - **Méthode d’authentification** : sélectionnez **Certificats**. 
    - **Certificat d’authentification** : sélectionnez un certificat SCEP ou PKCS existant > **OK**.      
    - **Fractionner le tunneling** : sélectionnez **Désactiver** pour forcer l’ensemble du trafic à utiliser le tunnel VPN quand la connexion VPN est active. 

      ![Dans un profil VPN par application, entrer une connexion, une adresse IP ou un nom de domaine complet, une méthode d’authentification et la tunnelisation fractionnée dans Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-create-vpn-profile.png)

    Pour plus d’informations sur les autres paramètres, consultez [Paramètres VPN iOS](vpn-settings-ios.md).

5. Sélectionner **VPN automatique** > **Type de VPN automatique** > **VPN par application**

    ![Dans Intune, définir VPN automatique sur VPN par application sur les appareils iOS](./media/vpn-setting-configure-per-app/vpn-per-app-automatic.png)

6. Sélectionnez **OK** > **OK** > **Créer**.

## <a name="associate-an-app-with-the-vpn-profile"></a>Associer une application au profil VPN

Après avoir ajouté votre profil VPN, associez l’application et le groupe Azure AD au profil.

1. Dans **Intune**, sélectionnez **Applications clientes** > **Applications**.
2. Sélectionnez une application dans la liste > **Affectations** > **Ajouter un groupe**.
3. Dans **Type d’affectation**, sélectionnez **Requis** ou **Disponible pour les appareils inscrits**.
4. Sélectionnez **Groupes inclus** > **Sélectionner les groupes à inclure** > Sélectionnez le groupe [que vous avez créé](#create-a-group-for-your-vpn-users) (dans cet article) > **Sélectionner**.
5. Dans **VPN**, sélectionnez le profil VPN par application [que vous avez créé](#create-a-per-app-vpn-profile) (dans cet article).

    ![Affecter une application au profil VPN par application dans Microsoft Intune](./media/vpn-setting-configure-per-app/vpn-per-app-app-to-vpn.png)

6. Sélectionnez **OK** > **Enregistrer**.

Une association entre une application et un profil est supprimée au prochain archivage de l’appareil si les conditions suivantes sont réunies :

- L’application a été ciblée avec l’intention « installation requise ».
- Le profil et l’application sont ciblés vers le même groupe.
- Vous supprimez la configuration du VPN par application de l’affectation d'applications.

Une association entre une application et un profil est conservée jusqu’à ce que l’utilisateur demande une réinstallation à partir du Portail d’entreprise Intune, quand les conditions suivantes sont réunies :

- L’application a été ciblée avec l’intention « installation disponible ».
- Le profil et l’application sont ciblés vers le même groupe.
- L’utilisateur final ayant demandé l’installation de l’application à partir du Portail d’entreprise Intune, l’application et le profil sont installés sur l’appareil.
- Vous supprimez ou changez la configuration VPN par application dans l’affectation d’applications.

## <a name="verify-the-connection-on-the-ios-device"></a>Vérifier la connexion sur l’appareil iOS

Une fois votre VPN par application configuré et associé à votre application, vérifiez que la connexion fonctionne sur un appareil.

### <a name="before-you-attempt-to-connect"></a>Avant d’essayer de se connecter

- Veillez à déployer toutes les stratégies mentionnées ci-dessus dans le même groupe. À défaut, l’expérience VPN par application ne fonctionnera pas.
- Si vous utilisez l’application VPN Pulse Secure ou une application de client VPN personnalisée, vous pouvez choisir d’utiliser le tunneling de couche paquet ou de couche application. Affectez à **ProviderType** la valeur **app-proxy** pour le tunneling de couche application, ou la valeur **packet-tunnel** pour le tunneling de couche paquet. Consultez la documentation de votre fournisseur VPN pour vérifier que vous utilisez la bonne valeur.

### <a name="connect-using-the-per-app-vpn"></a>Se connecter avec le VPN par application

Vérifiez l’expérience sans contact en vous connectant sans devoir sélectionner le VPN ni taper vos informations d’identification. L’expérience sans contact signifie que :

- L’appareil ne vous demande pas d’approuver le serveur VPN. Autrement dit, l’utilisateur ne voit pas la boîte de dialogue **Approbation dynamique**.
- L’utilisateur n’a pas à taper d’informations d’identification.
- L’appareil de l’utilisateur est connecté au VPN quand l’utilisateur ouvre l’une des applications associées.

<!-- ## Troubleshooting the per-app VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Étapes suivantes

- Pour examiner les paramètres iOS, consultez [Paramètres VPN pour les appareils iOS dans Microsoft Intune](vpn-settings-ios.md).
- Pour plus d’informations sur les paramètres VPN et Intune, consultez [Configurer les paramètres VPN dans Microsoft Intune](vpn-settings-configure.md).
