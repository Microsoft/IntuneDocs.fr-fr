---
title: Paramètres des appareils Windows Holographic for Business - Microsoft Intune - Azure | Microsoft Docs
description: Découvrez et configurez les paramètres de restriction d’appareil dans Microsoft Intune pour Windows Holographic for Business, notamment la désinscription, la géolocalisation, les mots de passe, l’installation des applications à partir d’un Store, les cookies et les fenêtres contextuelles dans Microsoft Edge, Windows Defender, la recherche, le cloud et le stockage, la connectivité Bluetooth, l’heure système et les données d’utilisation dans Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 477b8a0c9b4cdb575988524cea1f73615254baec
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838476"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Windows Holographic for Business pour autoriser ou restreindre les fonctionnalités avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Windows Holographic for Business, comme Microsoft Hololens. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, la sécurité du contrôle et bien plus encore.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Général

- **Désinscription manuelle** : Permet à l'utilisateur de supprimer manuellement le compte d'espace de travail de l'appareil
- **Cortana** : Active ou désactive l'assistant vocal Cortana.
- **Géolocalisation** : Spécifie si l'appareil peut utiliser les informations des services d'emplacement.

## <a name="password"></a>Mot de passe

- **Mot de passe** : Demande à l’utilisateur final de saisir un mot de passe pour pouvoir accéder à l’appareil.
- **Exiger un mot de passe quand l’appareil quitte un état inactif** : Spécifie que l’utilisateur doit entrer un mot de passe pour déverrouiller l’appareil.

## <a name="app-store"></a>App Store

- **Mettre à jour automatiquement les applications du Store** : Permet la mise à jour automatique des applications installées à partir du Microsoft Store.
- **Installation d’applications approuvées** : Permet le chargement indépendant des applications signées avec un certificat approuvé.
- **Déverrouillage de développement** : Permet d’activer des paramètres de développement Windows, par exemple pour autoriser l’utilisateur à modifier des applications qui ont été chargées indépendamment.

## <a name="microsoft-edge-browser"></a>Navigateur Microsoft Edge

- **Cookies** : Permet au navigateur d’enregistrer les cookies internet sur l’appareil.
- **Fenêtres contextuelles** : Bloque les fenêtres contextuelles dans le navigateur (s’applique à Windows 10 Desktop uniquement).
- **Suggestions de recherche** : Permet à votre moteur de recherche de suggérer des sites à mesure que vous saisissez des expressions de recherche.
- **Gestionnaire de mots de passe** : Activez ou désactivez la fonctionnalité Gestionnaire de mots de passe Microsoft Edge.
- **Envoyer des en-têtes Do Not Track** : Configure le navigateur Microsoft Edge pour envoyer des en-êtes Do Not Track aux sites web que les utilisateurs visitent.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen pour Microsoft Edge** : Activer Microsoft Edge SmartScreen pour accéder au site et aux téléchargements de fichiers.

## <a name="search"></a>Recherche

- **Emplacement de recherche** : Spécifie si la recherche peut utiliser l’emplacement. Informations

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Compte Microsoft** : Permet à l'utilisateur d'associer un compte Microsoft à l’appareil.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

- **Bluetooth** : Contrôle si l’utilisateur peut activer et configurer la fonction Bluetooth sur l’appareil.
- **Découvertibilité de Bluetooth** : Permet à l’appareil d’être découvert par d’autres appareils Bluetooth.
- **Publicité Bluetooth** : Autorise l’appareil à recevoir des annonces publicitaires via Bluetooth.

## <a name="control-panel-and-settings"></a>Panneau de configuration et paramètres

- **Modification de l’heure système** : Empêche l’utilisateur final de changer les date et heure sur l’appareil.

## <a name="kiosk---obsolete"></a>Plein écran - obsolète

Ces paramètres sont en lecture seule et ne peuvent pas être modifiés. Pour configurer le mode Plein écran, consultez [Paramètres kiosque](kiosk-settings-holographic.md).

Un appareil plein écran exécute généralement une application spécifique. Les utilisateurs ne peuvent pas accéder aux fonctionnalités ou fonctions sur l’appareil en dehors de l’application plein écran.

- **Mode kiosque** : Identifie le type de mode kiosque pris en charge par la stratégie. Les options sont les suivantes :

  - **Non configuré** (par défaut) : La stratégie n’active pas de mode kiosque. 
  - **Kiosque à application unique** : Le profil autorise l’appareil à exécuter une seule application. Quand l’utilisateur se connecte, une application spécifique démarre. Ce mode empêche également l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
  - **Kiosque multi-application** : Le profil autorise l’appareil à exécuter plusieurs applications. Seules les applications que vous ajoutez sont disponibles pour l’utilisateur. L’avantage d’un kiosque multi-application ou d’un appareil à usage fixe est que l’utilisateur n’accède qu’aux applications dont il a besoin. Celles dont il n’a pas besoin sont retirées de sa vue. 
  
    Quand vous ajoutez des applications en vue de proposer une expérience de kiosque multi-application, vous ajoutez également un fichier de disposition du menu Démarrer. Le [fichier de disposition du menu Démarrer](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) inclut un exemple de code XML qui peut être utilisé dans Intune. 

#### <a name="single-app-kiosks"></a>Applications uniques plein écran

entrez les paramètres suivants :

- **Compte d’utilisateur** : Entrez les informations de connexion du compte d’utilisateur local (pour l’appareil) ou du compte Azure AD associé à l’application kiosque. Pour les comptes liés à des domaines Azure AD, entrez le compte en utilisant le format `domain\username@tenant.org`. 

    Pour les appareils plein écran dans des environnements publics où l’ouverture de session automatique est activée, un type d’utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Pour configurer un compte Azure Active Directory (AD) pour le mode plein écran, utilisez le format `AzureAD\user@contoso.com`.

- **Identifiant AUMID de l’application** : Entrez l’ID de modèle utilisateur de l’application (AUMID) à exécuter en mode kiosque. Pour plus d’informations, consultez [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Rechercher l’identifiant AUMID d’une application installée).

## <a name="reporting-and-telemetry"></a>Création de rapports et les données de télémétrie

- **Partager les données d’utilisation** : Permet de sélectionner le niveau d’envoi des données de diagnostic.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
