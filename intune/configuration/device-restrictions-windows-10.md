---
title: Paramètres de restriction des appareils pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres et leur description pour la création de restrictions d’appareil sur les appareils Windows 10 et versions ultérieures. Utilisez ces paramètres dans un profil de configuration pour contrôler les captures d’écran, les exigences de mot de passe, les paramètres Kiosk, les applications dans le magasin, le navigateur Microsoft Edge, Microsoft Defender, l’accès au cloud, le menu Démarrer et autres dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81da5ca8e7eaa76f9a6705cc9e3c816234c461db
ms.sourcegitcommit: af384c46ec8d8def6aa32c3b89947748dc6fd28f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76517556"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités dans Intune

Cet article liste et décrit tous les paramètres que vous pouvez contrôler sur les appareils Windows 10 et versions ultérieures. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, pour définir des règles de mot de passe, pour personnaliser l’écran de verrouillage, pour utiliser Microsoft Defender, et bien plus encore.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur les appareils Windows 10.

> [!Note]
> Toutes les options ne sont pas disponibles dans toutes les éditions de Windows. Pour voir les éditions prises en charge, reportez-vous à [Fournisseurs de services de configuration de stratégie](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (ouvre un autre site web Microsoft).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>App Store

Ces paramètres utilisent le [fournisseur de service de configuration Policy ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), qui liste également les éditions de Windows prises en charge.

- **App Store (mobile uniquement)**  : **Non configuré** (valeur par défaut) permet aux utilisateurs finaux d’accéder à l’App Store sur des appareils mobiles. **Bloquer** empêche l’utilisation de l’App Store.
- **Mettre à jour automatiquement les applications du Store** : **Non configuré** (valeur par défaut) permet aux applications installées à partir du Microsoft Store d’être automatiquement mises à jour. **Bloquer** empêche l’installation automatique des mises à jour.
- **Installation d’applications approuvées** : choisissez si les applications non-Microsoft Store peuvent être installées (procédure également appelée « chargement indépendant »). Le chargement indépendant consiste à installer puis à exécuter ou tester une application qui n’est pas certifiée par le Microsoft Store (par exemple une application qui est interne à votre entreprise uniquement.) Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Bloquer** : empêche le chargement indépendant. Les applications non-Microsoft Store ne peuvent pas être installées.
  - **Autoriser** : autorise le chargement de indépendant. Les applications non-Microsoft Store peuvent être installées.
- **Déverrouillage de développement** : Permet d’activer des paramètres de développement Windows, par exemple pour autoriser l’utilisateur à modifier des applications qui ont été chargées indépendamment. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Bloquer** : interdit les applications en mode développeur et le chargement indépendant.
  - **Autoriser** : autorise les applications en mode développeur et le chargement indépendant.

  L’article [Activer votre appareil pour le développement](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) contient plus d’informations sur cette fonctionnalité.

- **Données d’application utilisateur partagées** : choisissez **Autoriser** pour partager les données d’application entre différents utilisateurs sur le même appareil et avec d’autres instances de cette application. **Non configuré** (valeur par défaut) empêche le partage de données avec d’autres utilisateurs et d’autres instances de la même application.
- **Utiliser uniquement un magasin privé** : **Autoriser** autorise uniquement le téléchargement des applications à partir d’un magasin privé, et non un magasin public, y compris un catalogue de vente au détail. **Non configuré** (valeur par défaut) autorise le téléchargement des applications à partir d’un magasin privé et d’un magasin public.
- **Lancement des applications du Windows Store** : l’option **Bloquer** désactive toutes les applications qui ont été préinstallées sur l’appareil ou téléchargées à partir du Microsoft Store. **Non configuré** (valeur par défaut) autorise l’ouverture de ces applications.
- **Installer les données d’application sur le volume système :** l’option **Bloquer** empêche les applications de stocker des données sur le volume système de l’appareil. **Non configuré** (valeur par défaut) autorise les applications à stocker des données sur le volume de disque du système.
- **Installer les applications sur le lecteur système** : **Bloquer** empêche l’installation des applications sur le lecteur système de l’appareil. **Non configuré** (valeur par défaut) autorise l’installation des applications sur le lecteur système.
- **Jeux DVR (poste de travail uniquement)**  : **Bloquer** désactive l’enregistrement et la diffusion des jeux Windows. **Non configuré** (valeur par défaut) autorise l’enregistrement et la diffusion des jeux.
- **Applications de Store uniquement** : Ce paramètre détermine l’expérience utilisateur quand les utilisateurs installent des applications à partir d’emplacements autres que le Microsoft Store. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Autorise les utilisateurs finaux à installer des applications à partir d’emplacements autres que le Microsoft Store, dont des applications définies dans d’autres paramètres de stratégie.  
  - **Partout** : Désactive les recommandations d’applications et autorise les utilisateurs à installer des applications à partir de n’importe quel emplacement.  
  - **Store uniquement** : Oblige les utilisateurs finaux à installer uniquement des applications à partir du Microsoft Store.
  - **Recommandations** : Quand les utilisateurs installent une application à partir du web qui est disponible dans le Microsoft Store, un message leur recommande de la télécharger à partir du Store.  
  - **Préférer le Store** : Avertit les utilisateurs quand ils installent des applications à partir d’emplacements autres que le Microsoft Store.

  [CSP SmartScreen/EnableAppInstallControl](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Contrôle utilisateur sur les installations** : lorsque la valeur **Non configuré** (valeur par défaut) est sélectionnée, Windows Installer empêcher les utilisateurs de modifier les options d’installation généralement réservées aux administrateurs système, comme l’entrée dans le répertoire pour installer les fichiers. **Bloquer** permet aux utilisateurs de modifier ces options d’installation, et certaines des fonctionnalités de sécurité de Windows Installer sont ignorées.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Installer des applications avec des privilèges élevés** : lorsque la valeur **Non configuré** (valeur par défaut) est sélectionnée, le système applique les autorisations de l’utilisateur actif lors de l’installation de programmes qu’un administrateur système ne déploie ou n’offre pas. **Bloquer** indique à Windows Installer d’utiliser des autorisations élevées quand il installe un programme sur le système. Ces privilèges sont étendus à tous les programmes.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Applications de démarrage** : entrez une liste d’applications à ouvrir lorsqu’un utilisateur se connecte à l’appareil. Veillez à utiliser une liste délimitée par des points-virgules pour les noms des familles de packages (NFP) des applications Windows. Pour que cette stratégie fonctionne, le manifeste dans les applications Windows doit utiliser une tâche de démarrage.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

Ces paramètres utilisent les fournisseurs de service de configuration [Connectivity Policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) et [Wi-Fi Policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi), qui listent également les éditions de Windows prises en charge.

- [Fournisseur de service de configuration Wi-Fi Policy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Canal de données mobiles** : choisissez si les utilisateurs finaux peuvent utiliser des données, par exemple naviguer sur le web, quand ils sont connectés à un réseau cellulaire. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre. Les utilisateurs finaux peuvent la désactiver.
  - **Bloquer** : ne pas autoriser le canal de données mobiles. Les utilisateurs finaux ne peuvent pas l’activer.
  - **Autoriser (non modifiable)** : autorise le canal de données mobiles. Les utilisateurs finaux ne peuvent pas la désactiver.

- **Itinérance de données** : **Bloquer** empêche l’itinérance des données mobiles sur l’appareil. **Non configuré** (valeur par défaut) autorise l’itinérance entre réseaux lors de l’accès aux données.
- **VPN sur le réseau de téléphonie mobile** : **Bloquer** empêche l’appareil d’accéder aux connexions VPN quand il est connecté à un réseau cellulaire. **Non configuré** (valeur par défaut) autorise le VPN à utiliser toute connexion, y compris un réseau cellulaire.
- **Itinérance VPN sur le réseau de téléphonie mobile** : **Bloquer** empêche l’appareil d’accéder aux connexions VPN quand il est en itinérance sur un réseau cellulaire. **Non configuré** (valeur par défaut) autorise les connexions VPN lors de l’itinérance.
- **Service d’appareils connectés** : **Bloquer** désactive le composant Plateforme d’appareils connectés (CDP). Le CDP autorise la découverte et la connexion à d’autres appareils (via Bluetooth/réseau local ou le cloud) pour prendre en charge le lancement d’applications à distance, la messagerie à distance, les sessions d’application à distance et d’autres expériences entre appareils. **Non configuré** (valeur par défaut) autorise le service d’appareils connectés, qui active la découverte et la connexion à d’autres appareils Bluetooth.
- **NFC** : **Bloquer** empêche l’utilisation des fonctionnalités NFC (Near Field Communications). **Non configuré** (valeur par défaut) permet aux utilisateurs d’activer et de configurer les fonctionnalités NFC sur l’appareil.
- **Wi-Fi** : **Bloquer** empêche les utilisateurs d’activer, de configurer et d’utiliser des connexions Wi-Fi sur l’appareil. **Non configuré** (valeur par défaut) autorise les connexions Wi-Fi.
- **Se connecter automatiquement aux points d’accès Wi-Fi** : **Bloquer** empêche les appareils de se connecter automatiquement aux points d’accès Wi-Fi. **Non configuré** (valeur par défaut) permet aux appareils de se connecter automatiquement aux points d’accès Wi-Fi gratuits et d’accepter automatiquement les termes et conditions de la connexion.
- **Configuration manuelle du Wi-Fi** : **Bloquer** empêche les appareils de se connecter au réseau Wi-Fi en dehors des réseaux installés par serveur MDM. **Non configuré** (valeur par défaut) permet aux utilisateurs finaux d’ajouter et de configurer leurs propres SSID réseau de connexions Wi-Fi.
- **Intervalle de recherche de Wi-Fi** : Spécifiez la fréquence à laquelle les appareils recherchent des réseaux Wi-Fi. Entrez une valeur comprise entre 1 (plus fréquent) et 500 (moins fréquent). La valeur par défaut est `0` (zéro).

### <a name="bluetooth"></a>BlueTooth

Ces paramètres utilisent le [fournisseur de service de configuration Policy Bluetooth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth), qui liste également les éditions de Windows prises en charge.

- **Bluetooth** : **Bloquer** empêche les utilisateurs d’activer le Bluetooth. **Non configuré** (valeur par défaut) autorise Bluetooth sur l’appareil.
- **Découvertibilité de Bluetooth** : **Bloquer** empêche l’appareil d’être détectable par d’autres appareils Bluetooth. **Non configuré** (valeur par défaut) permet à d’autres appareils Bluetooth, tels qu’un casque, de détecter l’appareil.
- **Précouplage Bluetooth** : **Bloquer** empêche des appareils Bluetooth spécifiques d’être couplés automatiquement à un appareil hôte. **Non configuré** (valeur par défaut) autorise le couplage automatique avec l’appareil hôte.
- **Publicité Bluetooth** : **Bloquer** empêche l’appareil d’envoyer des publicités Bluetooth. **Non configuré** (valeur par défaut) permet à l’appareil d’envoyer des publicités Bluetooth.
- **Services Bluetooth autorisés** : **Ajoutez** une liste de services et de profils Bluetooth autorisés sous forme de chaînes hexadécimales, par exemple `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [Le guide d’utilisation ServicesAllowedList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) contient plus d’informations sur la liste des services.

## <a name="cloud-and-storage"></a>Cloud et stockage

Ces paramètres utilisent le [fournisseur de service de configuration Policy Accounts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts), qui liste également les éditions de Windows prises en charge.

- **Compte Microsoft** : **Bloquer** empêche les utilisateurs finaux d’associer un compte Microsoft avec l’appareil. **Non configuré** (valeur par défaut) autorise l’ajout et l’utilisation d’un compte Microsoft.
- **Compte non-Microsoft** : **Bloquer** empêche les utilisateurs finaux d’ajouter des comptes non-Microsoft à l’aide de l’interface utilisateur. **Non configuré** (valeur par défaut) permet aux utilisateurs d’ajouter des comptes de messagerie qui ne sont pas associés à un compte Microsoft.
- **Synchronisation des paramètres du compte Microsoft** : **Non configuré** (par défaut) permet aux paramètres d’appareil et d’application associés à un compte Microsoft de se synchroniser entre les appareils. **Bloquer** empêche cette synchronisation.
- **Assistant de connexion de compte Microsoft** : quand vous choisissez **Non configuré** (valeur par défaut), les utilisateurs finaux peuvent démarrer et arrêter le service **Assistant Connexion avec un compte Microsoft** (wlidsvc). Ce service de système d’exploitation permet aux utilisateurs de se connecter à leur compte Microsoft. **Désactiver** empêche les utilisateurs finaux de contrôler le service Assistant Connexion avec un compte Microsoft (wlidsvc).

## <a name="cloud-printer"></a>Imprimante cloud

Ces paramètres utilisent le [fournisseur de service de configuration Policy EnterpriseCloudPrint](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint), qui liste également les éditions de Windows prises en charge.

- **URL de découverte d’imprimantes** : Entrez l’URL de recherche des imprimantes cloud. Par exemple, entrez `https://cloudprinterdiscovery.contoso.com`.
- **URL d’autorisation d’accès à l’imprimante** : Entrez l’URL du point de terminaison d’authentification pour obtenir des jetons OAuth. Par exemple, entrez `https://azuretenant.contoso.com/adfs`.
- **GUID de l’application cliente native Azure** : Entrez le GUID identifiant l’application cliente autorisée à obtenir des jetons OAuth à partir d’OAuthAuthority. Par exemple, entrez `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **URI de ressource du service d’impression** : Entrez l’URI de ressource OAuth pour le service d’impression configuré dans le portail Azure. Par exemple, entrez `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Nombre maximal d’imprimantes à interroger** : Entrez le nombre maximal d’imprimantes à interroger. La valeur par défaut est `20`.
- **URI de ressource du service de découverte d’imprimantes** : Entrez l’URI de ressource OAuth pour le service de découverte d’imprimantes configuré dans le portail Azure. Par exemple, entrez `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Après avoir configuré une [impression cloud hybride Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), vous pouvez configurer ces paramètres et les déployer sur vos appareils Windows.

## <a name="control-panel-and-settings"></a>Panneau de configuration et paramètres

- **Application Paramètres** : **Bloquer** empêche les utilisateurs finaux d’accéder à l’application Paramètres de Windows. **Non configuré** (valeur par défaut) autorise les utilisateurs à ouvrir l’application Paramètres sur l’appareil.
  - **Système** : **Bloquer** empêche l’accès à la zone Système de l’application Paramètres. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
    - **Modification des paramètres d’alimentation et de veille (poste de travail uniquement)**  : **Bloquer** empêche l’utilisateur final de changer les paramètres d’alimentation et de veille sur l’appareil. **Non configuré** (valeur par défaut) permet aux utilisateurs de modifier les paramètres d’alimentation et de veille.
  - **Appareils** : **Bloquer** empêche l’accès à la zone Appareils de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Réseau et Internet** : **Bloquer** empêche l’accès à la zone Réseau et Internet de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Personnalisation** : **Bloquer** empêche l’accès à la zone Personnalisation de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Applications** : **Bloquer** empêche l’accès à la zone Applications de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Comptes** : **Bloquer** empêche l’accès à la zone Comptes de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Heure et langue** : **Bloquer** empêche l’accès à la zone Heure et langue de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
    - **Modification de l’heure système** : **Bloquer** empêche les utilisateurs finaux de modifier les paramètres de date et d’heure sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Les utilisateurs peuvent modifier ces paramètres.
    - **Modification des paramètres régionaux (poste de travail uniquement)**  : **Bloquer** empêche les utilisateurs finaux de modifier les paramètres de région sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Les utilisateurs peuvent modifier ces paramètres.
    - **Modification des paramètres de langue (Desktop uniquement)**  : **Bloquer** empêche les utilisateurs finaux de modifier les paramètres de langue sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Les utilisateurs peuvent modifier ces paramètres.

      [Fournisseur de service de configuration Policy Settings](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Jeux** : **Bloquer** empêche l’accès à la zone Jeux de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Options d’ergonomie** : **Bloquer** empêche l’accès à la zone Options d’ergonomie de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Confidentialité** : **Bloquer** empêche l’accès à la zone Confidentialité de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Mise à jour et sécurité** : **Bloquer** empêche l’accès à la zone Mise à jour et sécurité de l’application Paramètres sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.

## <a name="display"></a>Afficher

Ces paramètres utilisent le [fournisseur de service de configuration Policy Display](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display), qui liste également les éditions de Windows prises en charge.

La mise à l’échelle DPI GDI permet aux applications sans prise en charge DPI de bénéficier d’une prise en charge DPI par moniteur.

- **Activer la mise à l’échelle GDI pour des applications** : **ajoutez** les applications héritées dont la mise à l'échelle DPI GDI doit être activée. Par exemple, entrez `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  La mise à l’échelle DPI GDI est activée pour toutes les applications héritées dans votre liste.

- **Désactiver la mise à l'échelle GDI pour des applications** : **ajoutez** les applications héritées dont la mise à l'échelle DPI GDI doit être désactivée. Par exemple, entrez `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  La mise à l’échelle DPI GDI est désactivée pour toutes les applications héritées dans votre liste.

Vous pouvez également **importer** un fichier .csv avec la liste des applications.

## <a name="general"></a>Général

Ces paramètres utilisent le [fournisseur de service de configuration Policy Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), qui liste également les éditions de Windows prises en charge. 

- **Capture d’écran (mobile uniquement)**  : **Bloquer** empêche les utilisateurs finaux d’effectuer des captures d’écran sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Copier et coller (mobile uniquement)**  : **Bloquer** empêche les utilisateurs finaux d’utiliser la fonctionnalité copier-coller entre applications sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Désinscription manuelle** : **Bloquer** empêche les utilisateurs finaux de supprimer le compte d’espace de travail à l’aide du Panneau d’espace de travail sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.

  Ce paramètre de stratégie ne s’applique pas si l’ordinateur est joint à Azure AD et que l’inscription automatique est activée.

- **Installation manuelle du certificat racine (mobile uniquement)**  : **Bloquer** empêche l’utilisateur d’installer manuellement les certificats racines et les certificats CAP intermédiaires. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Appareil photo** : **Bloquer** empêche les utilisateurs finaux d’utiliser l’appareil photo sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.

  [CSP Camera](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-camera)

- **Synchronisation des fichiers OneDrive** : **Bloquer** empêche les utilisateurs finaux de synchroniser des fichiers sur OneDrive à partir de l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Stockage amovible** : **Bloquer** empêche les utilisateurs finaux d’utiliser des dispositifs de stockage externe, tels que des cartes SD, avec l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Géolocalisation** : **Bloquer** empêche les utilisateurs finaux d’activer les services de localisation sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Partage Internet** : **Bloquer** empêche le partage de connexion Internet sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Réinitialisation du téléphone** : **Bloquer** empêche les utilisateurs finaux de rétablir les paramètres d’usine de l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Connexion USB** : **Bloquer** empêche l’accès aux dispositifs de stockage externe via une connexion USB sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Le chargement USB n’est pas affecté par ce paramètre.
- **Mode antivol (mobile uniquement)**  : **Bloquer** empêche les utilisateurs finaux de sélectionner la préférence du mode antivol sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Cortana** : **Bloquer** désactive l’assistant vocal Cortana sur l’appareil. Quand Cortana est désactivé, les utilisateurs peuvent toujours rechercher des éléments sur l’appareil. **Non configuré** (valeur par défaut) autorise l’utilisation de Cortana.
- **Enregistrement vocal (mobile uniquement)**  : **Bloquer** empêche les utilisateurs finaux d’utiliser l’enregistreur vocal sur l’appareil. **Non configuré** (valeur par défaut) autorise l’enregistrement vocal pour les applications.
- **Modification du nom de l’appareil** (mobile uniquement) : **Bloquer** empêche les utilisateurs finaux de modifier le nom de l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Ajouter des packages de configuration** : **Bloquer** empêche l’utilisation de l’agent de configuration du runtime qui installe les packages de configuration sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Supprimer les packages de configuration** : **Bloquer** empêche l’utilisation de l’agent de configuration du runtime qui supprime les packages de configuration de l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Découverte d’appareil** : **Bloquer** empêche l’appareil d’être détecté par d’autres appareils. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Sélecteur de tâches (mobile uniquement)**  : **Bloquer** empêcher de changer de tâche sur l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Boîte de dialogue d’erreur de carte SIM (mobile uniquement)**  : **Bloquer** empêche que des messages d’erreur s’affichent sur l’appareil si aucune carte SIM n’est détectée. **Non configuré** (par défaut) affiche les messages d’erreur.
- **Espace de travail Windows Ink** : choisissez si et comment l’utilisateur accède à l’espace de travail Ink. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : l’espace de travail Windows Ink est activé et l’utilisateur est autorisé à l’utiliser au-dessus de l’écran de verrouillage.
  - **Désactivé sur l’écran de verrouillage** : l’espace de travail Ink est activé et la fonctionnalité est activée. Toutefois, l’utilisateur ne peut pas y accéder au-dessus de l’écran de verrouillage.
  - **Disabled** : l’accès à l’espace de travail Ink est désactivé. La fonctionnalité est désactivée.

  [Fournisseur de service de configuration Policy WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Redéploiement automatique** : choisissez **Autoriser** pour que les utilisateurs avec des droits d’administration puissent supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **Ctrl+Win+R** sur l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion. **Non configuré** (par défaut) désactive cette fonctionnalité.
- **Demander aux utilisateurs de se connecter au réseau pendant la configuration de l’appareil** : Choisissez l’option **Exiger** pour que l’appareil se connecte à un réseau avant de continuer au-delà de la page Réseau lors de la configuration de Windows. **Non configuré** (valeur par défaut) permet aux utilisateurs d’aller au-delà de la page Réseau, même s’ils ne sont pas connectés à un réseau.

  Le paramètre entre en vigueur la prochaine fois que l’appareil est effacé ou réinitialisé. Comme pour les autres configurations Intune, l’appareil doit être inscrit et géré par Intune pour recevoir des paramètres de configuration. Mais une fois qu’il est inscrit et qu’il reçoit des stratégies, le fait de réinitialiser l’appareil applique le paramètre lors de l’installation suivante de Windows.

  [CSP TenantLockdown](https://docs.microsoft.com/windows/client-management/mdm/tenantlockdown-csp)

- **Accès direct à la mémoire** : **Bloquer** empêche l’accès direct à la mémoire (DMA) pour tous les ports en aval PCI enfichables à chaud tant qu’un utilisateur ne se connecte pas à Windows. **Activé** (valeur par défaut) autorise l’accès à DMA, même lorsqu’un utilisateur n’est pas connecté.

  [DataProtection/AllowDirectMemoryAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Terminer les processus à partir du Gestionnaire des tâches** : Ce paramètre détermine si les non-administrateurs peuvent utiliser le Gestionnaire des tâches pour mettre fin aux tâches. L’option **Empêcher** empêche les utilisateurs standard (non-administrateurs) d’utiliser le Gestionnaire des tâches pour terminer un processus ou une tâche sur l’appareil. L’option **Non configuré** (par défaut) permet aux utilisateurs standard d’arrêter un processus ou une tâche à l’aide du Gestionnaire des tâches.

## <a name="locked-screen-experience"></a>Expérience d’écran de verrouillage

- **Notifications du centre de notifications (mobile uniquement)**  : **Bloquer** empêche l’affichage des notifications du Centre de notifications sur l’écran de verrouillage de l’appareil. **Non configuré** (valeur par défaut) permet aux utilisateurs de choisir quelles applications affichent des notifications sur l’écran de verrouillage.

  [Fournisseur de service de configuration AboveLock/AllowActionCenterNotifications](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#AboveLock_AllowActionCenterNotifications)

- **URL de l’image de l’écran verrouillé (poste de travail uniquement)**  : Entrez l’URL d’une image au format JPG, JPEG ou PNG qui est utilisée comme papier peint de l’écran de verrouillage Windows. Par exemple, entrez `https://contoso.com/image.png`. Ce paramètre verrouille l’image et ne peut pas être modifié par la suite.

  [CSP Personalization/LockScreenImageUrl](https://docs.microsoft.com/en-us/windows/client-management/mdm/personalization-csp)

- **Délai d’expiration de l’écran configurable par l’utilisateur (mobile uniquement)**  : **Autoriser** permet aux utilisateurs de configurer un délai d’expiration. **Non configuré** (valeur par défaut) n’offre pas cette possibilité aux utilisateurs.

  [Fournisseur de service de configuration DeviceLock/AllowScreenTimeoutWhileLockedUserConfig](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_AllowScreenTimeoutWhileLockedUserConfig)

- **Cortana sur écran verrouillé (poste de travail uniquement)**  : **Bloquer** empêche les utilisateurs d’interagir avec Cortana quand l’appareil est sur l’écran de verrouillage. **Non configuré** (valeur par défaut) autorise l’interaction avec Cortana.

  [Fournisseur de service de configuration AboveLock/AllowCortanaAboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Notifications toast sur écran verrouillé** : **Bloquer** empêche l’affichage des notifications Toast sur l’écran de verrouillage de l’appareil. **Non configuré** (valeur par défaut) autorise ces notifications.

  [Fournisseur de service de configuration AboveLock/AllowToasts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Délai d’expiration de l’écran (mobile uniquement)**  : définit la durée (en secondes) entre le verrouillage de l’écran et la désactivation de l’écran. Les valeurs prises en charge sont 11-1800. Par exemple, entrez `300` pour définir ce délai d’attente sur cinq minutes.

  [Fournisseur de service de configuration DeviceLock/ScreenTimeoutWhileLocked](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_ScreenTimeoutWhileLocked)

## <a name="messaging"></a>Messagerie

Ces paramètres utilisent le [fournisseur de service de configuration Policy Messaging](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging), qui liste également les éditions de Windows prises en charge.

- **Synchronisation des messages (mobile uniquement)**  : **Bloquer** désactive la sauvegarde et la restauration des messages texte, ainsi que la synchronisation des messages entre les appareils Windows. La désactivation aide à éviter que des informations soient stockées sur des serveurs en dehors du contrôle de l’organisation. **Non configuré** (valeur par défaut) permet aux utilisateurs de modifier ces paramètres et de synchroniser leurs messages.
- **MMS (mobile uniquement)**  : **Bloquer** désactive la fonctionnalité d’envoi et de réception de MMS sur l’appareil. Pour les entreprises, utilisez cette stratégie afin de désactiver MMS sur les appareils dans le cadre des exigences d’audit ou de gestion. **Non configuré** (valeur par défaut) autorise l’envoi et la réception de MMS.
- **RCS (mobile uniquement)**  : **Bloquer** désactive la fonctionnalité d’envoi et de réception de RCS (Rich Communication Services) sur l’appareil. Pour les entreprises, utilisez cette stratégie afin de désactiver RCS sur les appareils dans le cadre des exigences d’audit ou de gestion. **Non configuré** (valeur par défaut) autorise l’envoi et la réception RCS.

## <a name="microsoft-edge-browser"></a>Navigateur Microsoft Edge

Ces paramètres utilisent le [fournisseur de service de configuration Policy Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), qui liste également les éditions de Windows prises en charge.

### <a name="use-microsoft-edge-kiosk-mode"></a>Utiliser le mode kiosque Microsoft Edge

Les paramètres disponibles varient selon ce que vous choisissez. Les options disponibles sont les suivantes :

- **Non** (par défaut) : Microsoft Edge ne s’exécute pas en mode kiosque. Tous les paramètres de Microsoft Edge peuvent être changés et configurés.
- **Signalisation numérique/interactive (kiosque mono-application)** : filtre les paramètres de Microsoft Edge qui sont applicables pour le mode kiosque Microsoft Edge de signalisation numérique/Interactive pour une utilisation seulement sur les kiosques mono-applications de Windows 10. Choisissez ce paramètre pour ouvrir une URL en plein écran et pour afficher le contenu seulement sur ce site web. [Configurer les signes numériques](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fournit plus d’informations sur cette fonctionnalité.
- **Navigation publique InPrivate (kiosque mono-application)** : filtre les paramètres de Microsoft Edge qui sont applicables pour le mode kiosque Microsoft Edge de navigation publique InPrivate pour une utilisation sur les kiosques mono-applications de Windows 10. Exécute une version multi-onglet de Microsoft Edge.
- **Mode normal (kiosque multiapplication)** : filtre les paramètres de Microsoft Edge qui sont applicables pour le mode kiosque de Microsoft Edge normal. Exécute une version complète de Microsoft Edge avec toutes les fonctionnalités de navigation.
- **Navigation publique (kiosque multiapplication)** : filtre les paramètres de Microsoft Edge qui s’appliquent à la navigation publique sur un kiosque multi-application de Windows 10.  Exécute une version multi-onglet de Microsoft Edge InPrivate.

> [!TIP]
> Pour plus d’informations sur ce que font ces options, consultez [Types de configuration du mode kiosque de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Ce profil de restrictions d’appareil est directement lié au profil de kiosque que vous créez avec les [paramètres de kiosque de Windows](kiosk-settings-windows.md). Pour récapituler :

1. Créez le profil de [paramètres de kiosque de Windows](kiosk-settings-windows.md) pour exécuter l’appareil en mode kiosque. Sélectionnez Microsoft Edge comme application et définissez le mode kiosque de Microsoft Edge dans le profil de kiosque.
2. Créez le profil de restrictions d’appareil décrit dans cet article et configurez les fonctionnalités et paramètres spécifiques autorisés dans Microsoft Edge. Veillez à choisir le même type de mode kiosque de Microsoft Edge que celui sélectionné dans votre profil de kiosque ([Paramètres de kiosque de Windows](kiosk-settings-windows.md)). 

    [Paramètres du mode kiosque pris en charge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) est une ressource précieuse.

> [!IMPORTANT] 
> Veillez à affecter ce profil Microsoft Edge aux mêmes appareils que ceux de votre profil de kiosque ([Paramètres de kiosque de Windows](kiosk-settings-windows.md)).

[Fournisseur de services de configuration ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Expérience de démarrage

- **Démarrer Microsoft Edge avec** : Choisissez les pages qui s’ouvrent au démarrage de Microsoft Edge. Les options disponibles sont les suivantes :
  - **Pages de démarrage personnalisées** : entrez les pages de démarrage, telles que `http://www.contoso.com`. Microsoft Edge charge les pages de démarrage que vous entrez.
  - **Page Nouvel onglet** : Microsoft Edge charge ce qui est entré dans le paramètre **URL de nouvel onglet**.
  - **Page de la dernière session** : Microsoft Edge charge la page de la dernière session.
  - **Pages d’accueil dans les paramètres de l’application locale** : Microsoft Edge démarre avec la page de démarrage par défaut définie par le système d’exploitation.

- **Autoriser l’utilisateur à changer les pages d’accueil** : **Oui** (par défaut) permet aux utilisateurs de modifier les pages de démarrage. Les administrateurs peuvent utiliser `EdgeHomepageUrls` pour entrer les pages d’accueil que les utilisateurs voient par défaut quand ils ouvrent Microsoft Edge. **Non** empêche les utilisateurs de changer les pages d’accueil.
- **Autoriser le contenu web dans une page Nouvel onglet** : quand vous sélectionnez **Oui** (valeur par défaut), Microsoft Edge ouvre l’URL entrée dans le paramètre **URL de nouvel onglet**. Si le paramètre **URL de nouvel onglet** est vide, Microsoft Edge ouvre la nouvelle page d’onglets mentionnée dans les paramètres Microsoft Edge. L’utilisateur peut la changer. Quand vous sélectionnez **Non**, Microsoft Edge ouvre un nouvel onglet avec une page vierge. Les utilisateurs ne peuvent pas le changer.
- **URL de nouvel onglet** : Entrez l’URL pour ouvrir la page Nouvel onglet. Par exemple, entrez `https://www.bing.com` ou `https://www.contoso.com`.

- **Bouton Accueil** : Choisissez ce qui doit se passer lorsque le bouton Accueil est sélectionné. Les options disponibles sont les suivantes :
  - **Pages de démarrage** : ouvre l’option que vous avez choisie pour le paramètre **Démarrer Microsoft Edge avec**.
  - **Page Nouvel onglet** : ouvre l’URL que vous avez entrée dans le paramètre **URL de nouvel onglet**.
  - **URL du bouton Démarrage** : entrez l’URL à ouvrir. Par exemple, entrez `https://www.bing.com` ou `https://www.contoso.com`.
  - **Masquer le bouton d’accueil** : Masque le bouton d’accueil
- **Autoriser les utilisateurs à changer le bouton d’accueil** : L’option **Oui** permet aux utilisateurs de modifier le bouton d’accueil. Les modifications de l’utilisateur remplacent les paramètres de l’administrateur pour le bouton Accueil. **Non** (valeur par défaut) empêche les utilisateurs de changer la configuration du bouton Accueil choisie par l’administrateur.
- **Afficher la page d'expérience de première exécution (mobile uniquement)** : **Oui** (valeur par défaut) affiche la page d’introduction de première utilisation dans Microsoft Edge. **Non** empêche l’affichage de la page d’introduction lors de la première exécution de Microsoft Edge. Cette fonctionnalité permet aux entreprises, notamment celles inscrites dans les configurations zéro émissions, de bloquer cette page.
- **Emplacement de la liste d’URL d’expérience de première exécution** (Windows 10 Mobile uniquement) : entrez l’URL qui pointe vers le fichier XML contenant les URL des pages de première exécution. Par exemple, entrez `https://www.contoso.com/sites.xml`.

- **Actualiser le navigateur après la durée d’inactivité** : entrez le nombre de minutes d’inactivité avant actualisation du navigateur, de 0 à 1 440 minutes. La valeur par défaut est de `5` minutes. Quand la valeur est `0` (zéro), le navigateur ne s’actualise pas après une période d’inactivité.

  Ce paramètre est disponible seulement lors de l’exécution en [navigation publique InPrivate (kiosque mono-application)](#use-microsoft-edge-kiosk-mode).

- **Autoriser les fenêtres contextuelles** (poste de travail uniquement) : L’option **Oui** (valeur par défaut) autorise les fenêtres contextuelles dans le navigateur web. **Non** empêche l’affichage des fenêtres indépendantes dans le navigateur.
- **Envoyer le trafic intranet à Internet Explorer** (poste de travail uniquement) : L’option **Oui** permet aux utilisateurs d’ouvrir des sites web intranet dans Internet Explorer au lieu de Microsoft Edge. Ce paramètre est fourni pour des raisons de compatibilité descendante. **Non** (valeur par défaut) autorise les utilisateurs à utiliser Microsoft Edge.
- **Emplacement de la liste des sites en mode Entreprise** (poste de travail uniquement) : entrez l’URL qui pointe vers le fichier XML contenant une liste des sites web qui s’ouvrent en mode Entreprise. Les utilisateurs ne peuvent pas modifier cette liste. Par exemple, entrez `https://www.contoso.com/sites.xml`.
- **Message lors de l’ouverture de sites dans Internet Explorer** : Utilisez ce paramètre pour configurer Microsoft Edge afin d’afficher une notification avant l’ouverture d’un site dans Internet Explorer 11. Les options disponibles sont les suivantes :
  - **Ne pas afficher ce message** : Le comportement par défaut du système d’exploitation est utilisé, ce qui peut ne pas afficher un message.
  - **Afficher un message indiquant que le site est ouvert dans Internet Explorer 11** : Affiche le message lors de l’ouverture des sites dans Internet Explorer. Les sites s’ouvrent dans Internet Explorer. 
  - **Afficher le message avec l'option d'ouvrir les sites dans Microsoft Edge** : affichez un message lors de l’ouverture de sites dans Microsoft Edge. Le message inclut un lien **Poursuivre dans Microsoft Edge** qui permet aux utilisateurs de Microsoft Edge au lieu d’Internet Explorer.

  > [!IMPORTANT]
  > Ce paramètre exige que vous utilisiez l’option **Emplacement de la liste des sites en mode Entreprise**, l’option **Envoyer le trafic intranet vers Internet Explorer**, ou les deux.

- **Autoriser la liste de compatibilité Microsoft** : **Oui** (valeur par défaut) permet l’utilisation d’une liste de compatibilité de Microsoft. **Non** empêche l’affichage de la liste de compatibilité Microsoft dans Microsoft Edge. Cette liste de Microsoft permet à Microsoft Edge d’afficher correctement les sites ayant des problèmes de compatibilité connus.
- **Précharger les pages de démarrage et la page Nouvel onglet** : **Oui** (valeur par défaut) utilise le comportement par défaut du système d’exploitation, qui peut être de précharger ces pages. Le préchargement réduit le temps de démarrage de Microsoft Edge et de chargement des nouveaux onglets. **Non** empêche Microsoft Edge de précharger les pages d’accueil et la page Nouvel onglet.
- **Prélancer les pages de démarrage et la page Nouvel onglet** : **Oui** (valeur par défaut) utilise le comportement par défaut du système d’exploitation, qui peut être de prélancer ces pages. Le prélancement aide les performances de Microsoft Edge et réduit le temps nécessaire pour démarrer Microsoft Edge. **Non** empêche Microsoft Edge de prélancer les pages d’accueil et la page Nouvel onglet.

### <a name="favorites-and-search"></a>Favoris et recherche

- **Afficher la barre des Favoris** : Choisissez ce qui doit se passer pour les favoris de n’importe quelle page Microsoft Edge. Les options disponibles sont les suivantes :
  - **Sur les pages d’accueil et la page Nouvel onglet** : affiche la barre des favoris au démarrage de Microsoft Edge et sur toutes les pages d’onglets. Les utilisateurs finaux peuvent modifier ce paramètre.
  - **Dans toutes les pages** : Affiche le volet des favoris dans toutes les pages. Les utilisateurs finaux ne peuvent pas modifier ce paramètre.
  - **Masqué** : Masque le volet des favoris dans toutes les pages. Les utilisateurs finaux ne peuvent pas modifier ce paramètre.
- **Autoriser le changement des Favoris** : **Oui** (valeur par défaut) utilise le paramètre par défaut du système d’exploitation, qui autorise les utilisateurs à modifier la liste. **Non** empêche les utilisateurs d’ajouter, d’importer, de trier ou de modifier la liste des favoris.
  - **Liste de favoris** : Ajoutez une liste d’URL au fichier des favoris. Par exemple, ajoutez `http://contoso.com/favorites.html`.
- **Synchroniser les favoris entre les navigateurs Microsoft (poste de travail uniquement)**  : L’option **Oui** force Windows à synchroniser les favoris entre Internet Explorer et Microsoft Edge. Les ajouts, suppressions, modifications et changements d’ordre dans les favoris sont partagés entre les navigateurs.  **Non** (valeur par défaut) utilise le comportement par défaut du système d’exploitation, qui peut donner aux utilisateurs le choix de synchroniser les favoris entre les navigateurs.
- **Moteur de recherche par défaut** : Choisissez le moteur de recherche par défaut sur l’appareil. Les utilisateurs finaux peuvent changer cette valeur à tout moment. Les options disponibles sont les suivantes :
  - Moteur de recherche dans les paramètres client Microsoft Edge
  - Bing
  - Google
  - Yahoo
  - Valeur personnalisée : dans **URL du fichier xml OpenSearch**, entrez une URL HTTPS avec le fichier XML qui inclut le nom court et l’URL du moteur de recherche, au minimum. Par exemple, entrez `https://www.contoso.com/opensearch.xml`.
- **Afficher les suggestions de recherche** : L’option **Oui** (valeur par défaut) permet à votre moteur de recherche de suggérer des sites à mesure que vous saisissez des expressions de recherche dans la barre d’adresses. **Non** empêche l’utilisation de cette fonctionnalité.
- **Autoriser les changements sur le moteur de recherche** : **Oui** (par défaut) permet aux utilisateurs d’ajouter de nouveaux moteurs de recherche, ou de changer le moteur de recherche par défaut dans Microsoft Edge. Choisissez **Non** pour empêcher les utilisateurs de personnaliser le moteur de recherche.

  Ce paramètre est disponible seulement lors de l’exécution en [mode normal (kiosque multi-application)](#use-microsoft-edge-kiosk-mode).

### <a name="privacy-and-security"></a>Confidentialité et sécurité

- **Autoriser la navigation InPrivate** : **Oui** (valeur par défaut) autorise la navigation InPrivate dans Microsoft Edge. Après la fermeture de tous les onglets InPrivate, Microsoft Edge supprime les données de navigation de l’appareil. **Non** empêche l’utilisateur final d’ouvrir des sessions de navigation InPrivate.
- **Enregistrer l’historique de navigation** : **Oui** (valeur par défaut) autorise l’enregistrement de l’historique de navigation dans Microsoft Edge. **Non** empêche l’enregistrement de l’historique de navigation.
- **Effacer les données de navigation en quittant (poste de travail uniquement)**  : L’option **Oui** efface l’historique et les données de navigation quand l’utilisateur quitte Microsoft Edge. **Non** (valeur par défaut) utilise le comportement par défaut du système d’exploitation, qui peut mettre en cache les données de navigation.
- **Synchroniser les paramètres de navigateur entre les appareils de l’utilisateur** : Choisissez la façon dont vous souhaitez synchroniser les paramètres de navigateur entre les appareils. Les options disponibles sont les suivantes :
  - **Autoriser** : Autorise la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur
  - **Bloquer et activer le remplacement utilisateur**: Bloque la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur. Les utilisateurs peuvent remplacer ce paramètre.
  - **Bloquer** : bloquer la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils des utilisateurs. Les utilisateurs ne peuvent pas remplacer ce paramètre.

Quand « Bloquer et activer le remplacement utilisateur » est sélectionné, l’utilisateur peut remplacer la désignation de l’administrateur.

- **Autoriser le gestionnaire de mots de passe** : **Oui** (valeur par défaut) autorise Microsoft Edge à utiliser automatiquement le gestionnaire de mots de passe, qui permet aux utilisateurs d’enregistrer et de gérer les mots de passe sur l’appareil. **Non** empêche Microsoft Edge d’utiliser le gestionnaire de mots de passe.
- **Cookies** : Choisissez la façon dont les cookies sont gérés dans le navigateur web. Les options disponibles sont les suivantes :
  - **Autoriser** : Les cookies sont stockés sur l’appareil.
  - **Bloquer tous les cookies** : Les cookies ne sont pas stockés sur l’appareil.
  - **Bloquer uniquement les cookies tiers** : Les cookies tiers ou de partenaire ne sont pas stockés sur l’appareil.
- **Autoriser le remplissage automatique dans les formulaires** : **Oui** (valeur par défaut) permet aux utilisateurs de modifier les paramètres de saisie semi-automatique dans le navigateur et de renseigner automatiquement les champs de formulaire. **Non** désactive la fonctionnalité de remplissage automatique dans Microsoft Edge.
- **Envoyer des en-têtes Do Not Track** : **Oui** envoie des en-têtes Do Not Track aux sites web exigeant des informations de suivi (recommandé). **Non** (valeur par défaut) n’envoie pas d’en-têtes, ce qui permet aux sites web d’effectuer le suivi de l’utilisateur. L’utilisateur peut configurer cette option.
- **Montrer l'adresse IP localhost WebRTC** : **Oui** (valeur par défaut) permet d’afficher l’adresse IP localhost des utilisateurs lors d’appels téléphoniques effectués à l’aide de ce protocole. **Non** empêche l’affichage de l’adresse IP localhost des utilisateurs. 
- **Autoriser la collecte des données de vignette dynamique** : **Oui** (valeur par défaut) autorise Microsoft Edge à recueillir des informations à partir des vignettes dynamiques épinglées au menu Démarrer. **Non** empêche la collecte de ces informations, ce qui est susceptible de limiter l’expérience des utilisateurs.
- **L’utilisateur peut remplacer les erreurs de certificat** : **Oui** (valeur par défaut) permet aux utilisateurs d’accéder aux sites web qui contiennent des erreurs SSL/TLS (Secure Sockets Layer/Transport Layer Security). **Non** (recommandé pour une sécurité accrue) empêche les utilisateurs d’accéder à des sites web présentant des erreurs SSL ou TLS.

### <a name="additional"></a>Informations supplémentaires

- **Autoriser le navigateur Microsoft Edge (mobile uniquement)** : **Oui** (par défaut) autorise l’utilisation du navigateur web Microsoft Edge sur l’appareil mobile. **Non** empêche l’utilisation de Microsoft Edge sur l’appareil. Si vous choisissez **Non**, les autres paramètres individuels s’appliquent uniquement au poste de travail.
- **Autoriser la liste déroulante de la barre d’adresses** : **Oui** (valeur par défaut) autorise Microsoft Edge à afficher la liste déroulante de la barre d’adresses avec une liste de suggestions. **Non** empêche Microsoft Edge d’afficher une liste de suggestions dans une liste déroulante à mesure que vous tapez. Quand cette option a la valeur **non**, vous :
  - Aidez à réduire la bande passante réseau entre Microsoft Edge et les services Microsoft.
  - Désactivez **Afficher les suggestions de recherche et de site à mesure que je tape** dans Microsoft Edge > Paramètres.
- **Autoriser le mode plein écran** : **Oui** (valeur par défaut) autorise Microsoft Edge à utiliser le mode plein écran, qui affiche uniquement le contenu web et masque l’interface utilisateur de Microsoft Edge. **Non** empêche l’affichage en mode plein écran dans Microsoft Edge.
- **Autoriser la page À propos des indicateurs** : **Oui** (valeur par défaut) utilise la valeur par défaut du système d’exploitation, ce qui peut permettre l’accès à la page `about:flags`. La page `about:flags` permet aux utilisateurs de modifier les paramètres de développeur et d’activer des fonctionnalités expérimentales. **Non** empêche les utilisateurs finaux d’accéder à la page `about:flags` dans Microsoft Edge.
- **Autoriser les outils de développement** : **Oui** (valeur par défaut) permet aux utilisateurs d’utiliser les outils de développement F12 pour générer et déboguer des pages web par défaut. **Non** empêche les utilisateurs finaux d’utiliser les outils de développement F12.
- **Autoriser JavaScript** : **Oui** (par défaut) autorise l’exécution de scripts, tels que JavaScript, dans le navigateur Microsoft Edge. **Non** empêche l’exécution des scripts Java dans le navigateur.
- **L’utilisateur peut installer des extensions** : L’option **Oui** (par défaut) autorise l’utilisateur final à installer des extensions Microsoft Edge sur l’appareil. **Non** empêche l’installation.
- **Autoriser le chargement indépendant des extensions de développement** : **Oui** (valeur par défaut) utilise la valeur par défaut du système d’exploitation, ce qui peut autoriser le chargement indépendant. Le chargement indépendant installe et exécute des extensions non vérifiées. **Non** empêche Microsoft Edge d’effectuer un chargement indépendant à l’aide de la fonctionnalité **Charger des extensions**. Cela n’empêche pas le chargement indépendant des extensions à l’aide d’autres moyens, tels que PowerShell.
- **Extensions nécessaires** : Choisissez les extensions qui ne peuvent pas être désactivées par les utilisateurs finaux dans Microsoft Edge. Entrez les noms des familles de packages, puis sélectionnez **Ajouter**. [Rechercher un nom de famille de packages (NFP) pour un VPN par application](https://docs.microsoft.com/configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn) fournit des conseils.

  Vous pouvez également **importer** un fichier CSV qui inclut les noms des familles de packages. Ou bien **exportez** les noms des familles de packages que vous entrez.

## <a name="network-proxy"></a>Proxy réseau

Ces paramètres utilisent le [fournisseur de service de configuration Policy NetworkProxy](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), qui liste également les éditions de Windows prises en charge.

- **Détecter automatiquement les paramètres du proxy** : **Bloquer** empêche l’appareil de détecter automatiquement un script de configuration automatique de proxy (PAC). **Non configuré** (valeur par défaut) active cette fonctionnalité. Quand cette option est activée, l’appareil tente de trouver le chemin d’un script PAC.
- **Utiliser un script de proxy** : choisissez **Autoriser** pour entrer un chemin vers votre script PAC pour configurer le serveur proxy. **Non configuré** (valeur par défaut) ne vous permet pas d’entrer l’URL d’un script PAC.
  - **URL de l’adresse du script de configuration** : Entrez l’URL d’un script PAC que vous souhaitez utiliser pour configurer le serveur proxy.
- **Utiliser un serveur proxy manuel** : choisissez **Autoriser** pour entrer manuellement le nom ou l’adresse IP et le numéro de port TCP d’un serveur proxy. **Non configuré** (valeur par défaut) ne vous permet pas d’entrer manuellement les détails d’un serveur proxy.
  - **Adresse** : Entrez le nom ou l’adresse IP du serveur proxy.
  - **Numéro de port** : Entrez le numéro de port de votre serveur proxy.
  - **Exceptions du proxy** : Entrez les URL qui ne doivent pas utiliser le serveur proxy. Utilisez des points-virgules pour séparer chaque élément.
  - **Ignorer le serveur proxy pour les adresses locales** : **Non configuré** (valeur par défaut) empêche l’utilisation d’un serveur proxy pour les adresses locales sur votre intranet. **Autoriser** utilise un serveur proxy pour les adresses locales.

## <a name="password"></a>Mot de passe

Ces paramètres utilisent le [fournisseur de service de configuration Policy DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), qui liste également les éditions de Windows prises en charge.

- **Mot de passe** : **Demande** à l’utilisateur final de saisir un mot de passe pour pouvoir accéder à l’appareil. **Non configuré** (valeur par défaut) autorise l’accès à l’appareil sans mot de passe. S’applique uniquement aux comptes locaux. Les mots de passe des comptes de domaine restent configurés par Active Directory (AD) et Azure AD.

  - **Type de mot de passe requis** : Sélectionnez le type de mot de passe. Les options disponibles sont les suivantes :
    - **Non configuré** : le mot de passe peut inclure des chiffres et des lettres.
    - **Numérique** : le mot de passe ne doit comporter que des nombres.
    - **Alphanumériques** : le mot de passe doit être une combinaison de chiffres et de lettres.
  - **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères requis, de 4 à 16. Par exemple, entrez `6` pour exiger au moins six caractères dans le mot de passe.
  
    > [!IMPORTANT]
    > Lorsque la configuration requise du mot de passe est modifiée sur un ordinateur de bureau Windows, les utilisateurs sont affectés lors de leur prochaine connexion, car c’est à ce moment-là que l’appareil passe d’inactif à actif. Les utilisateurs dont les mots de passe sont conformes à la configuration requise sont toujours invités à modifier leur mot de passe.
    
  - **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre d’échecs d’authentification autorisé (jusqu’à 11) avant réinitialisation de l’appareil. Le nombre valide que vous entrez dépend de l’édition. Le [CSP DeviceLock/MaxDevicePasswordFailedAttempts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) liste les valeurs prises en charge. `0` (zéro) peut désactiver la fonctionnalité de réinitialisation de l’appareil.

    Ce paramètre a également un impact différent selon l’édition. Pour obtenir des informations spécifiques sur ce paramètre, consultez la section sur le [fournisseur de service de configuration DeviceLock/MaxDevicePasswordFailedAttempts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** : entrez la durée pendant laquelle l’appareil doit être inactif avant le verrouillage de l’écran.
  - **Expiration du mot de passe (en jours)** : entrez la durée (en jours) après laquelle le mot de passe de l’appareil doit être modifié (de 1 à 365). Par exemple, entrez `90` pour que le mot de passe expire après 90 jours.
  - **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de mots de passe précédemment utilisés (de 1 à 24) qui ne peuvent pas être utilisés. Par exemple, entrez `5` pour que les utilisateurs ne puissent pas définir comme nouveau mot de passe leur mot de passe actuel ni l’un de leurs quatre mots de passe précédents.
  - **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (Mobile et Holographic)**  : choisissez **Exiger** pour que l’utilisateur doive entrer un mot de passe afin de déverrouiller l’appareil après une période d’inactivité. **Non configuré** (valeur par défaut) ne nécessite pas de code PIN ou de mot de passe quand l’appareil quitte un état d’inactivité.
  - **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, comme `1234` ou `1111`. Choisissez **Non configuré** (valeur par défaut) pour permettre aux utilisateurs de créer des mots de passe tels que `1234` ou `1111`. Ce paramètre autorise ou bloque également l’utilisation des mots de passe d’image Windows.
- **Chiffrement automatique durant AADJ** : **Bloquer** empêche le chiffrement automatique de l’appareil BitLocker quand l’appareil est préparé pour une première utilisation, quand l’appareil est joint à Azure AD. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Vous trouverez plus d’informations sur [Chiffrement d’appareil BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Fournisseur de services de configuration Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Stratégie FIPS (Federal Information Processing Standard)** : **Autoriser** utilise la stratégie FIPS, qui est une norme de l’administration américaine pour le chiffrement, le hachage et la signature. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Par défaut, le système d’exploitation n’utilise pas les algorithmes FIPS.

  [Fournisseur de services de configuration Cryptography/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Authentification des appareils Windows Hello** : **Autoriser** les utilisateurs à utiliser un appareil mobile Windows Hello, comme un téléphone, un appareil de suivi d’activité physique ou un appareil IoT, pour se connecter à un ordinateur Windows 10. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Par défaut, le système d’exploitation empêche les appareils mobiles Windows Hello de s’authentifier auprès de Windows.

  [Fournisseur de services de configuration Authentication/AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Connexion web** : active la prise en charge de la connexion Windows pour les fournisseurs fédérés non-ADFS (Active Directory Federation Services), comme SAML (Security Assertion Markup Language). SAML utilise des jetons sécurisés qui fournissent une expérience d’authentification unique aux navigateurs web. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Activé** : le fournisseur d’informations d’identification web est activé pour la connexion.
  - **Disabled** : le fournisseur d’informations d’identification web est désactivé pour la connexion.

  [Fournisseur de services de configuration Authentication/EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Domaine de locataire Azure AD par défaut** : entrez un nom de domaine existant dans votre organisation Azure AD. Quand des utilisateurs de ce domaine se connectent, ils n’ont pas besoin de taper le nom de domaine. Par exemple, entrez `contoso.com`. Les utilisateurs du domaine `contoso.com` peuvent se connecter en utilisant leur nom d’utilisateur, comme `abby`, au lieu de `abby@contoso.com`.

  [Fournisseur de services de configuration Authentication/PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>Exceptions de confidentialité par application

Vous pouvez ajouter des applications qui doivent avoir un comportement de confidentialité différent de celui défini dans « Confidentialité par défaut ».

- **Nom du package** : Nom de la famille du package d’application.
- **Nom de l’application** : Nom de l’application.

### <a name="exceptions"></a>Exceptions

- **Informations de compte** : Définissez si cette application peut accéder au nom, à la photo et à d’autres informations de contact de l’utilisateur.
- **Applications en arrière-plan** : Définissez si cette application peut s’exécuter en arrière-plan.
- **Calendrier** : Définissez si cette application peut accéder au calendrier.
- **Historique des appels** : Définissez si cette application peut accéder à l’historique de mes appels.
- **Appareil photo** : Définissez si cette application peut accéder à l’appareil photo.
- **Contacts** : Définissez si cette application peut accéder aux contacts.
- **E-Mail** : Définissez si cette application peut accéder aux e-mails et en envoyer.
- **Emplacement** : Définissez si cette application peut accéder aux informations de localisation.
- **Messagerie** : Définissez si cette application peut lire ou envoyer des SMS ou MMS.
- **Microphone** : Définissez si cette application peut utiliser le microphone.
- **Mouvement** : Définissez si cette application peut accéder aux informations de mouvement de l’appareil.
- **Notifications** : Définissez si cette application peut accéder aux notifications.
- **Téléphone** : Définissez si cette application peut accéder au téléphone.
- **Radios** : Certaines applications utilisent des signaux radio (comme Bluetooth) sur votre appareil pour envoyer et recevoir des données, et doivent activer et désactiver ces signaux radio. Définissez si cette application peut contrôler ces signaux radio.
- **Tâches** : Définissez si cette application peut accéder à vos tâches.
- **Appareils de confiance** : Choisissez si cette application peut utiliser des appareils de confiance. Les appareils de confiance sont des appareils déjà connectés ou ayant été fournis avec l’appareil. Par exemple, utilisez des téléviseurs, des projecteurs, etc. comme appareils de confiance.
- **Commentaires et diagnostics** : Définissez si cette application peut accéder aux informations de diagnostic.
- **Synchronisation avec des appareils** : Choisissez si cette application peut automatiquement partager et synchroniser des informations avec des appareils sans fil qui ne sont pas explicitement appairés à l’appareil.

## <a name="personalization"></a>Personalization

Ces paramètres utilisent le [fournisseur de service de configuration Policy Personalization](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), qui liste également les éditions de Windows prises en charge.

- **URL de l’image d’arrière-plan du poste de travail (Desktop uniquement)**  : Entrez l’URL d’une image au format JPEG, JPG ou PNG que vous souhaitez utiliser comme papier peint du Bureau Windows. Les utilisateurs ne peuvent pas changer d’image. Par exemple, entrez `https://contoso.com/logo.png`.

## <a name="printer"></a>Imprimante

- **Imprimantes** : Liste des imprimantes locales qui ont été ajoutées.
- **Imprimante par défaut** : Définissez l’imprimante par défaut.
- **Accès utilisateur à l’ajout de nouvelles imprimantes** : Autorisez ou bloquez l’utilisation des imprimantes locales.

## <a name="privacy"></a>Confidentialité

Ces paramètres utilisent le [fournisseur de service de configuration Policy Privacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), qui liste également les éditions de Windows prises en charge.

- **Personnalisation des entrées** : **Bloquer** empêche l’utilisation de la voix pour la dictée et pour communiquer avec Cortana et d’autres applications qui utilisent la reconnaissance vocale basée sur le cloud Microsoft. Elle est désactivée et les utilisateurs ne peuvent pas activer la reconnaissance vocale en ligne à l’aide des paramètres. **Non configuré** (valeur par défaut) permet aux utilisateurs de choisir. Si vous autorisez ces services, Microsoft peut collecter des données vocales pour améliorer le service.
- **Acceptation automatique des invites de consentement de l’utilisateur pour le couplage et la confidentialité** : Choisissez **Autoriser** afin que Windows accepte automatiquement les messages de consentement du couplage et de la confidentialité lors de l’exécution des applications. **Non configuré** (valeur par défaut) empêche l’acceptation automatique de la fenêtre de consentement de l’utilisateur relative au couplage et à la confidentialité lors de l’ouverture des applications.
- **Publier les activités de l’utilisateur** : **Bloquer** empêche les expériences partagées et la découverte des ressources récemment utilisées dans le flux d’activités. **Non configuré** (valeur par défaut) active cette fonctionnalité afin que les applications puissent publier les activités des utilisateurs finaux.
- **Activités locales uniquement** : L’option **Bloquer** empêche les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches en fonction uniquement de l’activité locale. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.

Vous pouvez configurer les informations auxquelles toutes les applications sur l’appareil peuvent accéder. Définissez également des exceptions pour chaque application à l’aide de l’option **Exceptions de confidentialité par application**.

### <a name="exceptions"></a>Exceptions

- **Informations de compte** : Définissez si cette application peut accéder au nom, à la photo et à d’autres informations de contact de l’utilisateur.
- **Applications en arrière-plan** : Définissez si cette application peut s’exécuter en arrière-plan.
- **Calendrier** : Définissez si cette application peut accéder au calendrier.
- **Historique des appels** : Définissez si cette application peut accéder à l’historique de mes appels.
- **Appareil photo** : Définissez si cette application peut accéder à l’appareil photo.
- **Contacts** : Définissez si cette application peut accéder aux contacts.
- **E-Mail** : Définissez si cette application peut accéder aux e-mails et en envoyer.
- **Emplacement** : Définissez si cette application peut accéder aux informations de localisation.
- **Messagerie** : Définissez si cette application peut lire ou envoyer des SMS ou MMS.
- **Microphone** : Définissez si cette application peut utiliser le microphone.
- **Mouvement** : Définissez si cette application peut accéder aux informations de mouvement de l’appareil.
- **Notifications** : Définissez si cette application peut accéder aux notifications.
- **Téléphone** : Définissez si cette application peut accéder au téléphone.
- **Radios** : Certaines applications utilisent des signaux radio (comme Bluetooth) sur votre appareil pour envoyer et recevoir des données, et doivent activer et désactiver ces signaux radio. Définissez si cette application peut contrôler ces signaux radio.
- **Tâches** : Définissez si cette application peut accéder à vos tâches.
- **Appareils de confiance** : Choisissez si cette application peut utiliser des appareils de confiance. Les appareils de confiance sont des appareils déjà connectés ou ayant été fournis avec l’appareil. Par exemple, utilisez des téléviseurs, des projecteurs, etc. comme appareils de confiance.
- **Commentaires et diagnostics** : Choisissez si cette application peut accéder aux informations de diagnostic.
- **Synchroniser avec les appareils** - Définir si cette application peut automatiquement partager et synchroniser des informations avec des appareils sans fil qui ne sont pas explicitement jumelés avec ce PC, cette tablette ou ce téléphone.

## <a name="projection"></a>Projection

Ces paramètres utilisent le [fournisseur de service de configuration Policy WirelessDisplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), qui liste également les éditions de Windows prises en charge.

- **Entrées utilisateur à partir de récepteurs d’affichage sans fil** : **Bloquer** empêche l’entrée utilisateur à partir du récepteur d’affichage sans fil. **Non configuré** (valeur par défaut) autorise un affichage sans fil à renvoyer l’entrée clavier, souris, stylet et tactile vers l’appareil source.
- **Projection sur ce PC** : **Bloquer** empêche les autres appareils de trouver cet appareil pour la projection. **Non configuré** (valeur par défaut) permet à l’appareil d’être détectable, et autorise la projection sur l’appareil par-dessus l’écran de verrouillage.
- **Exiger un code PIN pour l’appairage** : choisissez **Exiger** pour toujours demander un code PIN lors de la connexion à un projecteur. **Non configuré** (valeur par défaut) ne nécessite pas de code PIN pour coupler l’appareil à un projecteur.

## <a name="reporting-and-telemetry"></a>Création de rapports et les données de télémétrie

- **Partager les données d’utilisation** : Choisissez le niveau des données de diagnostic qui sont envoyées. Les options disponibles sont les suivantes :
  - **Non configuré** : aucune donnée n’est partagée.
  - **Sécurité** : informations requises pour aider à garantir la sécurité de Windows, notamment les données sur les paramètres de composant de télémétrie et d’expérience des utilisateurs connectés, l’outil de suppression des logiciels malveillants et Microsoft Defender.
  - **De base** : informations de base sur l’appareil, notamment les données relatives à la qualité, la compatibilité des applications, les données d’utilisation des applications et les données du niveau de sécurité.
  - **Amélioré** : informations supplémentaires, notamment comment Windows, Windows Server, System Center et les applications sont utilisés, comment ils fonctionnent, les données de fiabilité avancées ainsi que les données des niveaux Sécurité et De base.
  - **Complètes** : toutes les données nécessaires pour identifier et aider à résoudre les problèmes, ainsi que les données des niveaux Sécurité, De base et Amélioré.

  [Fournisseur de services de configuration System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Envoyer des données de navigation Microsoft Edge à Microsoft 365 Analytics** : Pour utiliser cette fonctionnalité, définissez les paramètres **Partager les données d’utilisation** sur **Amélioré** ou **Complet**. Cette fonctionnalité contrôle les données que Microsoft Edge envoie à Microsoft 365 Analytics pour les appareils d’entreprise avec un ID commercial configuré. Les options disponibles sont les suivantes :
  - **Non configuré** : Intune ne change pas ni ne met à jour ce paramètre. Par défaut, le système d’exploitation n’envoie pas de données d’historique de navigation.
  - **Envoyer uniquement les données intranet** : Permet à l’administrateur d’envoyer l’historique des données intranet.
  - **Envoyer uniquement les données Internet** : Permet à l’administrateur d’envoyer l’historique des données Internet.
  - **Envoyer les données intranet et Internet** : Permet à l’administrateur d’envoyer l’historique des données intranet et Internet.

  [Fournisseur de services de configuration Browser/ConfigureTelemetryForMicrosoft365Analytics](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Serveur proxy de télémétrie** : Entrez le nom de domaine complet (FQDN) ou l’adresse IP d’un serveur proxy pour transférer les demandes Expériences des utilisateurs connectés et télémétrie à l’aide d’une connexion SSL. Le format de ce paramètre est *serveur*:*port*. En cas d'échec du proxy nommé ou si aucun proxy n'est entré à l'activation de cette stratégie, les données Expériences des utilisateurs connectés et télémétrie ne sont pas envoyées et restent sur l'appareil local.

  Exemples de formats :

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [Fournisseur de services de configuration System/TelemetryProxy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="search"></a>Recherche

Ces paramètres utilisent le [fournisseur de service de configuration Policy Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), qui liste également les éditions de Windows prises en charge. 

- **Recherche sécurisée (mobile uniquement)**  : Contrôlez la manière dont Cortana filtre les contenus pour adultes dans les résultats de recherche. Les options disponibles sont les suivantes :
  - **Défini par l’utilisateur** : autoriser les utilisateurs finaux à choisir leurs propres paramètres.
  - **Strict** : niveau de filtrage le plus élevé en matière de contenu pour adultes.
  - **Modéré** : niveau de filtrage modéré en matière de contenu pour adultes. Les résultats de recherche valides ne sont pas filtrés.
- **Afficher les résultats web dans la recherche** : si vous choisissez **Bloquer**, les utilisateurs ne peuvent pas effectuer de recherche et les résultats web ne sont pas visibles dans la Recherche. **Non configuré** (valeur par défaut) permet aux utilisateurs d’effectuer des recherches sur le web, et les résultats sont affichés sur l’appareil.

## <a name="start"></a>Démarrer

Ces paramètres utilisent le [fournisseur de service de configuration Policy Start](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), qui liste également les éditions de Windows prises en charge.  

- **Disposition du menu Démarrer** : substituer la disposition de démarrage par défaut et personnaliser le menu Démarrer sur les appareils de bureau. Chargez un fichier XML qui inclut vos personnalisations, notamment l’ordre dans lequel les applications sont listées. Les utilisateurs ne peuvent pas changer la disposition du menu Démarrer que vous entrez.
- **Épingler des sites web à des vignettes dans le menu Démarrer** : Importez des images provenant de Microsoft Edge et affichez-les sous forme de liens dans le menu Démarrer de Windows pour les appareils de bureau.
- **Désépingler les applications de la barre des tâches** : **Bloquer** empêche les utilisateurs de détacher des applications de la barre des tâches. **Non configuré** (valeur par défaut) autorise les utilisateurs à détacher des applications de la barre des tâches.
- **Changement rapide d’utilisateur** : **Bloquer** empêche le passage d’un utilisateur connecté à un autre sans déconnexion. **Non configuré** (valeur par défaut) affiche **Changer d’utilisateur** sur la vignette de l’utilisateur.
- **Applications les plus utilisées** : **Bloquer** masque les applications les plus utilisées dans le menu Démarrer. Le bouton bascule correspondant dans l’application Paramètres est également désactivé. **Non configuré** (valeur par défaut) affiche les applications les plus utilisées.
- **Applications ajoutées récemment** : **Bloquer** masque les applications récemment ajoutées dans le menu Démarrer. Le bouton bascule correspondant dans l’application Paramètres est également désactivé. **Non configuré** (valeur par défaut) affiche les applications ajoutées récemment dans le menu Démarrer.
- **Mode de l’écran de démarrage** : Choisissez comment afficher l’écran de démarrage. Les options disponibles sont les suivantes :
  - **Défini par l’utilisateur** : ne force pas la taille de Démarrer. Les utilisateurs peuvent définir la taille.
  - **Plein écran** : force une taille en plein écran de Démarrer.
  - **Ne pas utiliser le plein écran** : force une taille non-plein écran de Démarrer.
- **Éléments ouverts récemment dans les listes de raccourcis** : **Bloquer** masque les listes de raccourcis dans le menu Démarrer et la barre des tâches. Le bouton bascule correspondant dans l’application Paramètres est également désactivé. **Non configuré** (valeur par défaut) affiche les éléments récemment ouverts dans les listes de raccourcis.
- **Liste d’applications** : choisissez comment les listes d’applications sont affichées. Les options disponibles sont les suivantes :
  - **Défini par l’utilisateur** : aucun paramètre n’est forcé. Les utilisateurs choisissent la façon dont la liste d’applications est présentée sur l’appareil.
  - **Réduire** : masquer la liste de toutes les applications.
  - **Réduire et désactiver l’application Paramètres** : Masquer la liste de toutes les applications et désactiver **Afficher la liste des applications dans le menu Démarrer** dans l’application Paramètres.
  - **Supprime et désactive l’application Paramètres** : Masquer la liste de toutes les applications, supprimer le bouton Toutes les applications et désactiver **Afficher la liste des applications dans le menu Démarrer** dans l’application Paramètres.
- **Bouton d’alimentation** : **Bloquer** masque le bouton d’alimentation dans le menu Démarrer. **Non configuré** (par défaut) affiche le bouton d’alimentation.
- **Vignette de l’utilisateur** : **Bloquer** masque la vignette utilisateur dans le menu Démarrer. **Non configuré** (valeur par défaut) affiche la vignette de l’utilisateur et définit également les paramètres suivants :
  - **Verrouiller** : **Bloquer** masque l’option **Verrouiller** dans la vignette de l’utilisateur du menu Démarrer. **Non configuré** (valeur par défaut) affiche l’option **Verrouiller**.
  - **Se déconnecter** : **Bloquer** masque l’option **Se déconnecter** dans la vignette de l’utilisateur du menu Démarrer. **Non configuré** (par défaut) affiche le bouton **Déconnexion**.
- **Arrêter** : **Bloquer** masque les options **Mettre à jour et arrêter** et **Arrêter** sur le bouton d’alimentation dans le menu Démarrer. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Veille** : **Bloquer** masque l’option **Mettre en veille** sur le bouton d’alimentation du menu Démarrer. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Mise en veille prolongée** : **Bloquer** masque l’option **Mettre en veille prolongée** sur le bouton d’alimentation du menu Démarrer. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Changer de compte** : **Bloquer** masque l’option **Changer de compte** sur la vignette de l’utilisateur du menu Démarrer. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Options de redémarrage** :  **Bloquer** masque les options **Mettre à jour et redémarrer** et **Redémarrer** sur le bouton d’alimentation dans le menu Démarrer. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
- **Documents sur Démarrer** : Masquez ou affichez le dossier Documents dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Téléchargements sur Démarrer** : Masquez ou affichez le dossier Téléchargements dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Explorateur de fichiers sur Démarrer** : Masquez ou affichez l’Explorateur de fichiers dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Groupe résidentiel sur Démarrer** : Masquez ou affichez le raccourci Groupe résidentiel dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Musique sur Démarrer** : Masquez ou affichez le dossier Musique dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Réseau sur Démarrer** : Masquez ou affichez Réseau dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Dossier Personnel sur Démarrer** : Masquez ou affichez le dossier Personnel dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Images sur Démarrer** : Masquez ou affichez le dossier Images dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Paramètres sur Démarrer** : Masquez ou affichez le raccourci Paramètres dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.
- **Vidéos sur Démarrer** : Masquez ou affichez le dossier Vidéos dans le menu Démarrer de Windows. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : aucun paramètre n’est forcé. Les utilisateurs choisissent d’afficher ou de masquer le raccourci.
  - **Masquer** : le raccourci est masqué et le paramètre est désactivé dans l’application Paramètres.
  - **Afficher** : le raccourci est affiché et le paramètre est désactivé dans l’application Paramètres.

## <a name="microsoft-defender-smart-screen"></a>Microsoft Defender SmartScreen

- **SmartScreen pour Microsoft Edge** : **Exiger** désactive Microsoft Defender SmartScreen et empêche les utilisateurs de l’activer. **Non configuré** (valeur par défaut) active SmartScreen. Aide à protéger les utilisateurs contre les menaces potentielles, et empêche les utilisateurs de le désactiver.

  Microsoft Edge utilise Windows Defender SmartScreen (activé) pour protéger les utilisateurs contre d’éventuels courriers indésirables d’hameçonnage et logiciels malveillants.

  [Fournisseur de services de configuration Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Accès à un site malveillant** : **Bloquer** empêche les utilisateurs d’ignorer les avertissements concernant le filtre Microsoft Defender SmartScreen et d’accéder au site. **Non configuré** (valeur par défaut) autorise les utilisateurs à ignorer les avertissements et à poursuivre vers le site.

  [Fournisseur de services de configuration Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Téléchargement des fichiers non vérifiés** : **Bloquer** empêche les utilisateurs d'ignorer les avertissements du filtre SmartScreen de Microsoft Defender et les empêche de télécharger les fichiers non vérifiés. **Non configuré** (valeur par défaut) permet aux utilisateurs d’ignorer les avertissements et de continuer à télécharger les fichiers non vérifiés.

  [Fournisseur de services de configuration Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Windows à la une

Ces paramètres utilisent le [fournisseur de service de configuration Policy Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), qui liste également les éditions de Windows prises en charge.

- **Windows à la une** : **Bloquer** désactive Windows à la une sur l’écran de verrouillage : Conseils Windows, les fonctionnalités Microsoft grand public et d’autres fonctionnalités associées. Si votre objectif est de réduire le trafic réseau à partir des appareils, affectez la valeur **Bloquer**. **Non configuré** (valeur par défaut) autorise les fonctionnalités Windows à la une et peut être contrôlé par les utilisateurs finaux. Quand cette option est activée, vous pouvez également autoriser ou bloquer les paramètres suivants :

  - **Windows à la une sur l’écran de verrouillage** : **Bloquer** empêche Windows à la une d’afficher des informations sur l’écran de verrouillage de l’appareil. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Suggestions de tiers dans Windows à la une** : **Bloquer** empêche Windows à la une de suggérer du contenu qui n’est pas publié par Microsoft. **Non configuré** (valeur par défaut) autorise les suggestions d’applications et de contenu provenant d’éditeurs de logiciels partenaires dans les fonctionnalités de Windows à la une, comme la une sur l’écran de verrouillage, les applications suggérées dans le menu Démarrer et les conseils Windows.
  - **Fonctionnalités grand public** : **Bloquer** désactive les fonctionnalités destinées au grand public uniquement, comme les suggestions du démarrage, les notifications d’appartenance, l’installation d’application post-OOBE et les vignettes de redirection. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.
  - **Conseils Windows** : **Bloquer** désactive les info-bulles de conseils Windows. **Non configuré** (valeur par défaut) autorise l’affichage des conseils Windows.
  - **Windows à la une dans le centre de notifications** : **Bloquer** empêche l’affichage des notifications de Windows à la une dans le centre de notifications. **Non configuré** (valeur par défaut) peut afficher des notifications dans le centre de notifications qui suggèrent des applications ou des fonctionnalités pour aider les utilisateurs à être plus productifs sur Windows.
  - **Personnalisation de Windows à la une** : **Bloquer** empêche Windows d’utiliser des données de diagnostic pour fournir des expériences personnalisées à l’utilisateur. **Non configuré** (valeur par défaut) permet à Microsoft d’utiliser des données de diagnostic pour fournir des recommandations personnalisées, des conseils et des offres afin d’adapter Windows aux besoins de l’utilisateur.
  - **Écrans d’accueil de Windows** : **Bloquer** désactive la fonctionnalité Écrans d’accueil de Windows de Windows à la une. L’expérience Écrans d’accueil de Windows ne s’affichera pas en cas de mises à jour et de modifications apportées à Windows et à ses applications. **Non configuré** (valeur par défaut) autorise l’expérience Écrans d’accueil de Windows qui montre à l’utilisateur des informations sur les fonctionnalités nouvelles ou mises à jour.

## <a name="microsoft-defender-antivirus"></a>Antivirus Microsoft Defender

Ces paramètres utilisent le [fournisseur de service de configuration Policy Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), qui liste également les éditions de Windows prises en charge.

- **Surveillance en temps réel** : **Activer** active l’analyse en temps réel pour les logiciels malveillants, les logiciels espions et d’autres logiciels indésirables. Les utilisateurs ne peuvent pas la désactiver. 

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active cette fonctionnalité et autorise les utilisateurs à la changer.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **Analyse du comportement** : **Activer** active l’analyse du comportement et vérifie certains modèles connus d’activité suspecte sur les appareils. Les utilisateurs ne sont pas autorisés à désactiver l’analyse du comportement. 

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active l’analyse du comportement et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **Système NIS (Network Inspection System)**  : Le système NIS vous permet de vous protéger contre les attaques réseau. Il utilise les signatures de vulnérabilités connues fournies par le Microsoft Endpoint Protection Center pour faciliter la détection et le blocage du trafic malveillant.

  **Activer** active la protection réseau et le blocage du trafic réseau. Les utilisateurs ne peuvent pas la désactiver. Quand le paramètre est activé, il bloque les utilisateurs qui tentent de se connecter à des vulnérabilités connues.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active le système NIS et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **Analyser tous les téléchargements** : **Activer** active ce paramètre ; Defender analyse alors tous les fichiers téléchargés depuis Internet. Les utilisateurs ne sont pas autorisés à désactiver ce paramètre. 

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active ce paramètre et autorise les utilisateurs à le changer.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **Analyser les scripts chargés dans les navigateurs web Microsoft** : **Activer** permet à Defender d’analyser les scripts utilisés dans Internet Explorer. Les utilisateurs ne sont pas autorisés à désactiver ce paramètre. 

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active ce paramètre et autorise les utilisateurs à le changer.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- **Accès de l’utilisateur final à Defender** : **Bloquer** masque l’interface utilisateur de Microsoft Defender aux utilisateurs finaux. Toutes les notifications de Microsoft Defender sont également supprimées.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous bloquez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation permet aux utilisateurs d’accéder à l’interface utilisateur de Microsoft Defender et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  Quand ce paramètre est modifié, le changement est appliqué au prochain redémarrage de l’ordinateur de l’utilisateur final.

  [CSP Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **Intervalle de mise à jour de la veille de sécurité (en heures)**  : Entrez la fréquence (entre 0 et 24) à laquelle Defender doit rechercher les nouvelles mises à jour de la veille de sécurité. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre. Par défaut, le système d’exploitation recherche les mises à jour toutes les 8 heures.
  - **Ne pas vérifier** : Defender ne recherche pas les nouvelles mises à jour de la veille de sécurité.
  - **1-24** : `1` vérifie toutes les heures, `2` vérifie toutes les deux heures, `24` vérifie tous les jours, et ainsi de suite.
  
  [CSP Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **Surveiller l’activité des fichiers et des programmes** : Autorise Defender à surveiller l’activité des fichiers et des programmes sur des appareils. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre. Par défaut, le système d’exploitation surveille l’activité de tous les fichiers.
  - **Surveillance désactivée**
  - **Surveiller tous les fichiers**
  - **Surveiller les fichiers entrants uniquement**
  - **Surveiller les fichiers sortants uniquement**

  [CSP Defender/RealTimeScanDirection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **Nombre de jours avant la suppression des programmes malveillants en quarantaine** : continuer le suivi des logiciels malveillants résolus pendant le nombre de jours que vous entrez, pour vous permettre de vérifier manuellement les appareils précédemment affectés. Si vous définissez le nombre de jours du suivi sur `0`, les logiciels malveillants restent dans le dossier de quarantaine et ne sont pas automatiquement supprimés. Quand vous affectez la valeur `90`, les éléments mis en quarantaine sont stockés pendant 90 jours sur le système, puis supprimés.

  [CSP Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **Limite de l’utilisation du processeur pendant une analyse** : Limitez la quantité d’UC que les analyses sont autorisées à utiliser (de `0` à `100`).
- **Analyser les fichiers d’archive** : **Activer** active Defender afin qu’il analyse les fichiers d’archive, tels que les fichiers Zip ou Cab. Les utilisateurs ne sont pas autorisés à désactiver ce paramètre.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active cette analyse et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **Analyser les e-mails entrants** : **Activer** permet à Defender d’analyser les e-mails dès qu’ils arrivent sur l’appareil. Quand ce paramètre est activé, le moteur analyse les fichiers de la boîte aux lettres et des e-mails pour vérifier le corps et les pièces jointes des e-mails. Vous pouvez analyser les fichiers aux formats .pst (Outlook), .dbx, .mbx, MIME (Outlook Express) et BinHex (Mac).

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation désactive cette analyse et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- **Analyser les disques amovibles lors d’une analyse complète** : **Activer** active les analyses des lecteurs amovibles par Defender pendant une analyse complète. Les utilisateurs ne sont pas autorisés à désactiver ce paramètre.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation permet à Defender d’analyser les lecteurs amovibles, comme les clés USB, et autorise les utilisateurs à changer ce paramètre.

  Durant une analyse rapide, les lecteurs amovibles peuvent quand même être analysés.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **Analyser les lecteurs réseau mappés lors d’une analyse complète** : **Activer** à Defender d’analyser les fichiers sur un lecteur réseau mappé. Si les fichiers sur le lecteur sont en lecture seule, Defender ne peut pas supprimer les logiciels malveillants détectés dans ces fichiers. Les utilisateurs ne sont pas autorisés à désactiver ce paramètre.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation active cette fonctionnalité et autorise les utilisateurs à la changer.

  Durant une analyse rapide, les lecteurs réseau mappés peuvent quand même être analysés.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **Analyser les fichiers ouverts à partir de dossiers réseau** : **Activer** permet à Defender d’analyser les fichiers ouverts à partir de dossiers réseau ou de lecteurs réseau partagés, tels que les fichiers auxquels vous accédez à partir d’un chemin UNC. Les utilisateurs ne sont pas autorisés à désactiver ce paramètre. Si les fichiers sur le lecteur sont en lecture seule, Defender ne peut pas supprimer les logiciels malveillants détectés dans ces fichiers.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation analyse les fichiers ouverts à partir de dossiers réseau et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **Protection du cloud** : **Activer** active Microsoft Active Protection Service pour recevoir des informations sur l’activité des logiciels malveillants en provenance des appareils que vous gérez. Les utilisateurs ne peuvent pas modifier ce paramètre. 

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous activez le paramètre, puis le redéfinissez à **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré. Par défaut, le système d’exploitation permet à Microsoft Active Protection Service de recevoir des informations et autorise les utilisateurs à changer ce paramètre.

  Intune ne désactive pas cette fonctionnalité. Pour la désactiver, utilisez un URI personnalisé.

  [CSP Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **Demander confirmation aux utilisateurs avant l’envoi d’un échantillon** : Contrôle si les fichiers potentiellement malveillants susceptibles de nécessiter une analyse plus approfondie sont envoyés automatiquement à Microsoft. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre. Par défaut, le système d’exploitation envoie automatiquement des échantillons sécurisés.
  - **Toujours demander**
  - **Demander confirmation avant d’envoyer des données personnelles**
  - **Ne jamais envoyer de données**
  - **Envoyer toutes les données sans demande de confirmation** : Les données sont envoyées automatiquement.

  [CSP Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **Heure de l’analyse rapide quotidienne** : choisissez l’heure à laquelle exécuter une analyse rapide quotidienne. **Non configuré** : n’exécute pas d’analyse quotidienne. Si vous voulez davantage de personnalisation, configurez le paramètre **Type d’analyse système à effectuer**.

  [Fournisseur de services de configuration Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **Type d’analyse système à effectuer** : planifiez une analyse du système, notamment le niveau de l’analyse, et le jour et l’heure auxquels exécuter l’analyse. Les options disponibles sont les suivantes :
  - **Non configuré** : ne planifie d’analyse système sur l’appareil. Les utilisateurs finaux peuvent exécuter manuellement des analyses selon ce qui est nécessaire ou souhaité sur leurs appareils.
  - **Désactiver** : désactive les systèmes d’analyse sur l’appareil. Choisissez cette option si vous utilisez une solution anti-virus d’un partenaire qui analyse les appareils.
  - **Analyse rapide** : examine les emplacements habituels où des programmes malveillants pourraient être inscrits, comme les clés du Registre et les dossiers de démarrage de Windows connus.
    - **Jour planifié** : choisissez le jour où exécuter l’analyse.
    - **Heure planifiée** : choisissez l’heure où exécuter l’analyse.
  - **Analyse complète** : examine les emplacements habituels où des programmes malveillants pourraient être inscrits, et analyse également tous les fichiers et dossiers sur l’appareil.
    - **Jour planifié** : choisissez le jour où exécuter l’analyse.
    - **Heure planifiée** : choisissez l’heure où exécuter l’analyse.

  > [!TIP]
  > Ce paramètre peut entrer en conflit avec le paramètre **Heure de l’analyse rapide quotidienne**. Quelques recommandations :  
  >
  > - Si vous souhaitez planifier une analyse rapide quotidienne et une analyse complète hebdomadaire, procédez comme suit :
  >   1. Configurez le paramètre **Heure de l’analyse rapide quotidienne**.
  >   2. Configurez le paramètre **Type d’analyse système à effectuer** pour une analyse complète.
  > 
  > - Si vous souhaitez planifier seulement une analyse rapide quotidienne (aucune analyse complète), utilisez l’un des paramètres suivants : **Heure de l’analyse rapide quotidienne** ou **Type d’analyse système à effectuer**. Par exemple, pour exécuter une analyse rapide tous les mardis à 6h00, configurez le paramètre **Type d’analyse système à effectuer**.
  > 
  > - Ne configurez pas le paramètre **Heure de l’analyse rapide quotidienne** en combinaison avec **Type d’analyse système à effectuer** défini sur **Analyse rapide**. Ces paramètres peuvent être en conflit, l’analyse pouvant alors ne pas s’exécuter.

  [Fournisseur de services de configuration Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Fournisseur de services de configuration Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Fournisseur de services de configuration Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Détecter les applications potentiellement indésirables** : Choisissez le niveau de protection quand Windows détecte des applications potentiellement indésirables. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : la protection Microsoft Defender contre les applications potentiellement indésirables est désactivée.
  - **Bloquer** : Microsoft Defender détecte les applications potentiellement indésirables, et les éléments détectés sont bloqués. Ces éléments s’affichent dans l’historique, ainsi que d’autres menaces.
  - **Audit** : Microsoft Defender détecte les applications potentiellement indésirables, mais n’effectue aucune action. Vous pouvez consulter les informations sur les applications pour lesquelles Microsoft Defender prendrait des mesures, par exemple rechercher les événements créés par Microsoft Defender dans l’observateur d’événements.

  Pour plus d’informations sur les applications potentiellement indésirables, consultez [Détecter et bloquer les applications potentiellement indésirables](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

  [CSP Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **Consentement concernant l’envoi d’exemples** : Actuellement, ce paramètre n’a aucun effet. N’utilisez pas ce paramètre, qui est susceptible d’être supprimé dans une version ultérieure.

- **Protection de l’accès** : **Bloquer** empêche l’analyse des fichiers consultés ou téléchargés. Les utilisateurs ne peuvent pas l’activer.

  Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre. Si vous bloquez le paramètre, puis le redéfinissez sur **Non configuré**, Intune laisse le paramètre dans son état précédemment configuré par le système d’exploitation. Par défaut, le système d’exploitation active cette fonctionnalité et autorise les utilisateurs à la changer.

  Intune n’active pas cette fonctionnalité. Pour l’activer, utilisez un URI personnalisé.

  [CSP Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection)

- **Actions en cas de détection de menaces de programmes malveillants** : Choisissez la façon dont vous souhaitez gérer les menaces de programmes malveillants. Quand **Non configuré** (valeur par défaut) est défini, Microsoft Defender choisit la meilleure option. Lorsque cette option est définie sur **Activer**, choisissez les actions que Defender doit exécuter pour chaque niveau de menace détecté : faible, modéré, élevé et grave. Les options disponibles sont les suivantes :
  
  - **Nettoyer**
  - **Quarantaine**
  - **Supprimer**
  - **Autoriser**
  - **Défini par l’utilisateur**
  - **Bloquer**

  Si votre action n’est pas possible, Microsoft Defender choisit la meilleure option pour s’assurer que la menace est éliminée. 

  [CSP Defender/ThreatSeverityDefaultAction](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="microsoft-defender-antivirus-exclusions"></a>Exclusions de l’antivirus Microsoft Defender

- **Fichiers et dossiers à exclure des analyses et de la protection en temps réel** : Ajoute un ou plusieurs fichiers et dossiers comme **C:\Chemin** ou **%ProgramFiles%\Chemin\NomFichier.exe** à la liste des exclusions. Ces fichiers et dossiers ne sont pas inclus dans les analyses en temps réel ou planifiées.
- **Extensions de fichier à exclure des analyses et de la protection en temps réel** : Ajoutez une ou plusieurs extensions de fichier comme **jpg** ou **txt** à la liste des exclusions. Tous les fichiers avec ces extensions ne sont pas inclus dans les analyses en temps réel ou planifiées.
- **Processus à exclure des analyses et de la protection en temps réel** : Ajoutez un ou plusieurs processus du type **.exe**, **.com**, ou **.scr** à la liste des exclusions. Ces processus ne sont pas inclus dans les analyses en temps réel ou planifiées.

## <a name="power-settings"></a>Paramètres d’alimentation

### <a name="battery"></a>Batterie

- **Niveau de batterie à partir duquel activer l’économiseur d’énergie** : Quand l’appareil fonctionne sur batterie, entrez le niveau de charge de la batterie (entre 0 et 100) auquel l’économiseur d’énergie doit être activé. Entrez une valeur en pourcentage qui indique le niveau de charge de la batterie. La valeur par défaut est 70 %. Lorsque la valeur est définie à 70 %, l’économiseur d’énergie est activé quand le niveau de charge de la batterie atteint 70 % ou une valeur inférieure.

  [CSP Power/EnergySaverBatteryThresholdOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdonbattery)

- **Fermeture du capot (mobile uniquement)**  : Quand l’appareil fonctionne sur batterie, choisissez l’action exécutée à la fermeture du capot. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Aucune action** : L’appareil reste allumé et continue à utiliser la batterie.
  - **Veille** : L’appareil passe en mode Veille et consomme peu de batterie. L’ordinateur reste allumé, et les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM).
  - **Mise en veille prolongée** : L’appareil passe en mode Veille prolongée. Les applications et fichiers ouverts sont stockés sur le disque dur, et l’appareil s’éteint.
  - **Arrêt** : L’appareil s’arrête. Les applications et fichiers ouverts sont fermés sans être enregistrés au préalable.

  [CSP Power/SelectLidCloseActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectlidcloseactiononbattery)

- **Bouton d’alimentation** : Quand l’appareil fonctionne sur batterie, choisissez l’action exécutée à la sélection du bouton d’alimentation. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Aucune action** : L’appareil reste allumé et continue à utiliser la batterie.
  - **Veille** : L’appareil passe en mode Veille et consomme peu de batterie. L’ordinateur reste allumé, et les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM).
  - **Mise en veille prolongée** : L’appareil passe en mode Veille prolongée. Les applications et fichiers ouverts sont stockés sur le disque dur, et l’appareil s’éteint.
  - **Arrêt** : L’appareil s’arrête. Les applications et fichiers ouverts sont fermés sans être enregistrés au préalable.

  [CSP Power/SelectPowerButtonActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectpowerbuttonactiononbattery)

- **Bouton de veille** : Quand l’appareil fonctionne sur batterie, choisissez l’action exécutée à la sélection du bouton de veille. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Aucune action** : L’appareil reste allumé et continue à utiliser la batterie.
  - **Veille** : L’appareil passe en mode Veille et consomme peu de batterie. L’ordinateur reste allumé, et les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM).
  - **Mise en veille prolongée** : L’appareil passe en mode Veille prolongée. Les applications et fichiers ouverts sont stockés sur le disque dur, et l’appareil s’éteint.
  - **Arrêt** : L’appareil s’arrête. Les applications et fichiers ouverts sont fermés sans être enregistrés au préalable.

  [CSP Power/SelectSleepButtonActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectsleepbuttonactiononbattery)

- **Veille mode hybride** : Quand l’appareil fonctionne sur batterie, **Désactiver** empêche l’appareil de passer en veille mode hybride. En veille mode hybride, les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM) et sur le disque dur. L’appareil consomme peu de batterie. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.

  [CSP Power/TurnOffHybridSleepOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-turnoffhybridsleeponbattery)

### <a name="pluggedin"></a>Sur secteur

- **Niveau de batterie à partir duquel activer l’économiseur d’énergie** : Quand l’appareil est branché, entrez le niveau de charge de la batterie (entre 0 et 100) auquel l’économiseur d’énergie doit être activé. Entrez une valeur en pourcentage qui indique le niveau de charge de la batterie. La valeur par défaut est 70 %. Lorsque la valeur est définie à 70 %, l’économiseur d’énergie est activé quand le niveau de charge de la batterie atteint 70 % ou une valeur inférieure.

  [CSP Power/EnergySaverBatteryThresholdPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdpluggedin)

- **Fermeture du capot (mobile uniquement)**  : Quand l’appareil est branché, choisissez l’action exécutée à la fermeture du capot. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Aucune action** : L’appareil reste allumé.
  - **Veille** : L’appareil passe en mode Veille. L’ordinateur reste allumé, et les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM).
  - **Mise en veille prolongée** : L’appareil passe en mode Veille prolongée. Les applications et fichiers ouverts sont stockés sur le disque dur, et l’appareil s’éteint.
  - **Arrêt** : L’appareil s’arrête. Les applications et fichiers ouverts sont fermés sans être enregistrés au préalable.
  
    [CSP Power/SelectLidCloseActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectlidcloseactionpluggedin)
  
- **Bouton d’alimentation** : Quand l’appareil est branché, choisissez l’action exécutée à la sélection du bouton d’alimentation. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Aucune action** : L’appareil reste allumé.
  - **Veille** : L’appareil passe en mode Veille. L’ordinateur reste allumé, et les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM).
  - **Mise en veille prolongée** : L’appareil passe en mode Veille prolongée. Les applications et fichiers ouverts sont stockés sur le disque dur, et l’appareil s’éteint.
  - **Arrêt** : L’appareil s’arrête. Les applications et fichiers ouverts sont fermés sans être enregistrés au préalable.

  [CSP Power/SelectPowerButtonActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectpowerbuttonactionpluggedin)

- **Bouton de veille** : Quand l’appareil est branché, choisissez l’action exécutée à la sélection du bouton de veille. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Intune ne change pas ni ne met à jour ce paramètre.
  - **Aucune action** : L’appareil reste allumé.
  - **Veille** : L’appareil passe en mode Veille. L’ordinateur reste allumé, et les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM).
  - **Mise en veille prolongée** : L’appareil passe en mode Veille prolongée. Les applications et fichiers ouverts sont stockés sur le disque dur, et l’appareil s’éteint.
  - **Arrêt** : L’appareil s’arrête. Les applications et fichiers ouverts sont fermés sans être enregistrés au préalable.

  [CSP Power/SelectSleepButtonActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectsleepbuttonactionpluggedin)

- **Veille mode hybride** : Quand l’appareil est branché, **Désactiver** empêche l’appareil de passer en veille mode hybride. En veille mode hybride, les applications et fichiers ouverts sont stockés dans la mémoire vive (RAM) et sur le disque dur. Quand **Non configuré** (valeur par défaut) est défini, Intune ne change pas ni ne met à jour ce paramètre.

  [CSP Power/TurnOffHybridSleepPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-turnoffhybridsleeppluggedin)

## <a name="next-steps"></a>Étapes suivantes

Pour plus de détails techniques sur chaque paramètre et sur les éditions de Windows prises en charge, consultez [Référence CSP de stratégie Windows 10](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider).
