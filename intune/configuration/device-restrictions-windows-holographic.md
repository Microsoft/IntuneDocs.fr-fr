---
title: Paramètres des appareils Windows Holographic for Business - Microsoft Intune - Azure | Microsoft Docs
description: Découvrez et configurez les paramètres de restriction d’appareil dans Microsoft Intune pour Windows Holographic for Business, notamment la désinscription, la géolocalisation, les mots de passe, l’installation des applications à partir d’un Store, les cookies et les fenêtres contextuelles dans Microsoft Edge, Windows Defender, la recherche, le cloud et le stockage, la connectivité Bluetooth, l’heure système et les données d’utilisation dans Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10efed6bf1f6017881618ac692a190e26b8df638
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734750"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Windows Holographic for Business pour autoriser ou restreindre les fonctionnalités avec Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Windows Holographic for Business, comme Microsoft Hololens. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, la sécurité du contrôle et bien plus encore.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Général

- **Inscription manuelle** : permet à l’utilisateur de supprimer manuellement le compte d’espace de travail de l’appareil.
- **Cortana** : active ou désactive l’assistant vocal Cortana.
- **Géolocalisation** : spécifie si l’appareil peut utiliser les informations des services d’emplacement.

## <a name="password"></a>Mot de passe

- **Mot de passe** : demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil.
- **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité** : spécifie que l’utilisateur doit entrer un mot de passe pour déverrouiller l’appareil.

## <a name="app-store"></a>App Store

- **Mettre à jour automatiquement les applications du Windows store** : permet aux applications installées à partir du Microsoft Store d’être automatiquement mises à jour.
- **Installation d’applications approuvées** : permet de charger indépendamment les applications signées avec un certificat approuvé.
- **Déverrouillage de développement** : autorise les paramètres de développement Windows, par exemple pour autoriser l’utilisateur à modifier des applications qui ont été chargées indépendamment.

## <a name="microsoft-edge-browser"></a>Navigateur Microsoft Edge

- **Cookies** : permet au navigateur d’enregistrer les cookies internet sur l’appareil.
- **Fenêtres contextuelles** : bloque les fenêtres publicitaires dans le navigateur (s’applique à Windows 10 Desktop uniquement).
- **Suggestions de recherche** : permet à votre moteur de recherche de suggérer des sites à mesure que vous saisissez des expressions de recherche.
- **Gestionnaire de mots de passe** : activez ou désactivez la fonctionnalité Gestionnaire de mots de passe Microsoft Edge.
- **Envoyer un en-tête Do Not Track** : configure le navigateur Microsoft Edge pour envoyer des en-têtes Do Not Track aux sites web que les utilisateurs visitent.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen pour Microsoft Edge** : activer Microsoft Edge SmartScreen pour accéder au site et aux téléchargements de fichiers.

## <a name="search"></a>Recherche

- **Emplacement de recherche** : Spécifie si la recherche peut utiliser l’emplacement. Informations

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Compte Microsoft** : permet à l’utilisateur d’associer un compte Microsoft à l’appareil.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

- **Bluetooth** : contrôle si l’utilisateur peut activer et configurer la fonction Bluetooth sur l’appareil.
- **Détectabilité de Bluetooth** : permet à cet appareil d’être découvert par d’autres appareils Bluetooth.
- **Publicité Bluetooth** : permet à l’appareil de recevoir des publications via Bluetooth.

## <a name="control-panel-and-settings"></a>Panneau de configuration et paramètres

- **Modification de l’heure système** : empêche l’utilisateur final de modifier la date et l’heure de l’appareil.

## <a name="kiosk---obsolete"></a>Plein écran - obsolète

Ces paramètres sont en lecture seule et ne peuvent pas être modifiés. Pour configurer le mode Plein écran, consultez [Paramètres kiosque](kiosk-settings-holographic.md).

Un appareil plein écran exécute généralement une application spécifique. Les utilisateurs ne peuvent pas accéder aux fonctionnalités ou fonctions sur l’appareil en dehors de l’application plein écran.

- **Mode kiosque** : identifie le type de mode kiosque pris en charge par la stratégie. Les options sont les suivantes :

  - **Non configuré** (par défaut) : La stratégie n’active pas de mode kiosque. 
  - **Application unique plein écran** : le profil autorise l’appareil à exécuter une seule application. Quand l’utilisateur se connecte, une application spécifique démarre. Ce mode empêche également l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
  - **Kiosque multi-application** : le profil autorise l’appareil à exécuter plusieurs applications. Seules les applications que vous ajoutez sont disponibles pour l’utilisateur. L’avantage d’un kiosque multi-application ou d’un appareil à usage fixe est que l’utilisateur n’accède qu’aux applications dont il a besoin. Celles dont il n’a pas besoin sont retirées de sa vue. 
  
    Quand vous ajoutez des applications en vue de proposer une expérience de kiosque multi-application, vous ajoutez également un fichier de disposition du menu Démarrer. Le [fichier de disposition du menu Démarrer](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) inclut un exemple de code XML qui peut être utilisé dans Intune. 

### <a name="single-app-kiosks"></a>Applications uniques plein écran

entrez les paramètres suivants :

- **Compte d’utilisateur** : entrez le compte d’utilisateur local (pour l’appareil) ou la connexion au compte Azure Active Directory associé à l’application kiosque. Pour les comptes liés à des domaines Azure AD, entrez le compte en utilisant le format `domain\username@tenant.org`. 

    Pour les appareils plein écran dans des environnements publics où l’ouverture de session automatique est activée, un type d’utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Pour configurer un compte Azure Active Directory (AD) pour le mode plein écran, utilisez le format `AzureAD\user@contoso.com`.

- **Identifiant AUMID de l’application** : entrez l’identifiant AUMID de l’application plein écran. Pour plus d’informations, consultez [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Rechercher l’identifiant AUMID d’une application installée).

## <a name="reporting-and-telemetry"></a>Création de rapports et les données de télémétrie

- **Partager les données d’utilisation** : sélectionnez le niveau d’envoi des données de diagnostic.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
