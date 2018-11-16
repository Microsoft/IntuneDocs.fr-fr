---
title: Restrictions d’appareil pour Windows Holographic for Business dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez et configurez les paramètres de restriction d’appareil dans Microsoft Intune pour Windows Holographic for Business, notamment la désinscription, la géolocalisation, les mots de passe, l’installation des applications à partir d’un Store, les cookies et les fenêtres contextuelles dans Microsoft Edge, Windows Defender, la recherche, le cloud et le stockage, la connectivité Bluetooth, l’heure système et les données d’utilisation dans Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f79985c9854af462fa9a456304a3184128283b9c
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576798"
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Paramètres de restriction d’appareil pour Windows Holographic for Business dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les paramètres de restriction d’appareil suivants sont pris en charge sur les appareils exécutant Windows Holographic for Business, comme Microsoft Hololens.

## <a name="general"></a>Général

- **Inscription manuelle** - Permet à l’utilisateur de supprimer manuellement le compte d’espace de travail de l’appareil.
- **Cortana** - Active ou désactive l’assistant vocal Cortana.
- **Géolocalisation** - Spécifie si l’appareil peut utiliser les informations des services d’emplacement.

## <a name="password"></a>Mot de passe
-   **Mot de passe** - Demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil.
    -   **Exiger un mot de passe quand l'appareil sort d'un état d'inactivité** : Spécifie que l’utilisateur doit entrer un mot de passe pour déverrouiller l’appareil.

## <a name="app-store"></a>App Store

-   **Mettre à jour automatiquement les applications du Windows store** - Permet aux applications installées à partir du Microsoft Store d’être automatiquement mises à jour.
-   **Installation d’applications approuvées** - Permet de charger indépendamment les applications signées avec un certificat approuvé.
-   **Déverrouillage de développement** - Autorise les paramètres de développement Windows, par exemple pour autoriser l’utilisateur à modifier des applications qui ont été chargées indépendamment.

## <a name="microsoft-edge-browser"></a>Navigateur Microsoft Edge

-   **Cookies** - Permet au navigateur d’enregistrer les cookies internet sur l’appareil.
-   **Fenêtres contextuelles** : Bloque les fenêtres publicitaires dans le navigateur (s’applique à Windows 10 Desktop uniquement).
-   **Suggestions de recherche** - Permet à votre moteur de recherche de suggérer des sites à mesure que vous saisissez des expressions de recherche.
-   **Gestionnaire de mots de passe** : activez ou désactivez la fonctionnalité Gestionnaire de mots de passe Microsoft Edge.
- **Envoyer un en-tête Do Not Track** : configure le navigateur Microsoft Edge pour envoyer des en-têtes Do Not Track aux sites web que les utilisateurs visitent.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen pour Microsoft Edge** : activez Microsoft Edge SmartScreen pour accéder au site et aux téléchargements de fichiers.

## <a name="search"></a>Recherche
- **Emplacement de recherche** : Spécifie si la recherche peut utiliser l’emplacement. Informations

## <a name="cloud-and-storage"></a>Cloud et stockage
-   **Compte Microsoft** - Permet à l’utilisateur d’associer un compte Microsoft à l’appareil.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

-   **Bluetooth** - Contrôle si l’utilisateur peut activer et configurer la fonction Bluetooth sur l’appareil.
-   **Détectabilité de Bluetooth** - Permet à cet appareil d’être découvert par d’autres appareils Bluetooth.
-   **Publicité Bluetooth** - Permet à l’appareil de recevoir des publications via Bluetooth.

## <a name="control-panel-and-settings"></a>Panneau de configuration et paramètres

- **Modification de l’heure système** - Empêche l’utilisateur final de modifier la date et l’heure de l’appareil.

## <a name="kiosk---obsolete"></a>Plein écran - obsolète

Ces paramètres sont en lecture seule et ne peuvent pas être modifiés. Pour configurer le mode Plein écran, consultez [Paramètres kiosque](kiosk-settings.md#windows-holographic-for-business).

Un appareil plein écran exécute généralement une application spécifique. Les utilisateurs ne peuvent pas accéder aux fonctionnalités ou fonctions sur l’appareil en dehors de l’application plein écran.

- **Mode plein écran** : Identifie le type de mode plein écran pris en charge par la stratégie. Les options sont les suivantes :

  - **Non configuré** (par défaut) : la stratégie n’active pas de mode plein écran. 
  - **Application unique plein écran** : le profil autorise l’appareil à exécuter une seule application. Quand l’utilisateur se connecte, une application spécifique démarre. En outre, ce mode empêche l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
  - **Applications multiples plein écran** : le profil autorise l’appareil à exécuter plusieurs applications. Seules les applications que vous ajoutez sont disponibles pour l’utilisateur. L’avantage d’un kiosque multi-application ou d’un appareil à usage fixe est que l’utilisateur n’accède qu’aux applications dont il a besoin. Celles dont il n’a pas besoin sont retirées de sa vue. 
  
    Quand vous ajoutez des applications en vue de proposer une expérience de kiosque multi-application, vous ajoutez également un fichier de disposition du menu Démarrer. Le [fichier de disposition du menu Démarrer](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) inclut un exemple de code XML qui peut être utilisé dans Intune. 

#### <a name="single-app-kiosks"></a>Applications uniques plein écran
entrez les paramètres suivants :

- **Compte d’utilisateur** : entrez le compte d’utilisateur local (pour l’appareil) ou la connexion au compte Azure Active Directory associé à l’application plein écran. Pour les comptes liés à des domaines Azure AD, entrez le compte en utilisant le format `domain\username@tenant.org`. 

    Pour les appareils plein écran dans des environnements publics où l’ouverture de session automatique est activée, un type d’utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Pour configurer un compte Azure Active Directory (AD) pour le mode plein écran, utilisez le format `AzureAD\user@contoso.com`.

- **Identifiant AUMID de l’application** : entrez l’identifiant AUMID de l’application plein écran. Pour plus d’informations, consultez [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Rechercher l’identifiant AUMID d’une application installée).

## <a name="reporting-and-telemetry"></a>Création de rapports et les données de télémétrie

- **Partager les données d’utilisation** - Sélectionner le niveau d'envoi des données de diagnostic.
