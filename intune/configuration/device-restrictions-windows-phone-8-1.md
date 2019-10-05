---
title: Paramètres de restriction d’appareil Microsoft Intune pour Windows Phone 8.1
titleSuffix: ''
description: Découvrez les paramètres Intune qui vous permettent de contrôler les paramètres et les fonctionnalités des appareils exécutant Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb5ffa2fe17c3272cb98c670fa42e69f189e7004
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734737"
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Paramètres de restriction d’appareil Windows Phone 8.1 dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article décrit les paramètres de restriction d’appareil Microsoft Intune que vous pouvez configurer pour les appareils exécutant Windows Phone 8.1.


## <a name="general"></a>Général

- **Appareil photo** - Autorise ou bloque l’appareil photo de l’appareil.
- **Copier et coller** - Autorise ou bloque la fonction copier-coller sur les appareils.
- **Stockage amovible** - Autorise l’appareil à utiliser du stockage amovible, tel qu’une carte SD.
- **Géolocalisation** - Permet à l’appareil d’utiliser les informations d’emplacement.
- **Compte Microsoft** - Permet ou empêche l’utilisateur d’associer un compte Microsoft à l’appareil.
- **Capture d'écran** - Permet à l'utilisateur de capturer le contenu de l'écran en tant qu'image.
- **Envoi des données de diagnostic** - Autorise l’appareil à soumettre des informations de diagnostic à Microsoft.
- **Synchronisation personnalisée des comptes e-mail** - Autorise l’appareil à se connecter à des comptes de messagerie non Microsoft.

## <a name="password"></a>Mot de passe

- **Mot de passe** - Demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil.
  - **Type de mot de passe requis** - Spécifie le type de mot de passe requis, par exemple alphanumérique ou numérique uniquement.
  - **Longueur minimale du mot de passe** - Spécifie le nombre minimal de caractères devant figurer dans le mot de passe.
  - **Mots de passe simples** - Indique que les mots de passe simples tels que « 0000 » et « 1234 » peuvent être utilisés.
  - **Nombre d'échecs de connexion avant réinitialisation de l'appareil** - Spécifie le nombre de saisies possibles d’un mot de passe incorrect avant que l’appareil soit réinitialisé.
  - **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** - Spécifie la durée pendant laquelle un appareil doit rester inactif avant le verrouillage automatique de l’écran.
  - **Expiration du mot de passe (jours)** - Spécifie le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
  - **Empêcher la réutilisation des mots de passe précédents** - Spécifie le nombre de mots de passe précédemment utilisés mémorisés.
- **Chiffrement** - Exige que les données sur les appareils mobiles pris en charge soient chiffrées.

## <a name="app-store"></a>App Store

- **App store** - Permet aux utilisateurs de se connecter à l'App Store depuis l'appareil.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

Une liste **Applications bloquées** - Répertorie les applications qui ne sont pas gérées par Intune et que les utilisateurs ne sont pas autorisés à installer et à exécuter.
Une liste **Applications autorisées** - Répertorie les applications que les utilisateurs sont autorisés à installer. Les applications qui sont gérées par Intune sont autorisées automatiquement.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application, et l'URL de l'application dans l’App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Comment spécifier l’URL vers une application dans l’App Store

Pour insérer une URL d’application dans la liste des applications autorisées ou bloquées, utilisez le format suivant :

Dans la page [Windows Phone Store](https://www.microsoft.com/store/apps/windows-phone), recherchez l’application à utiliser.

Ouvrez la page de l'application, puis copiez l'URL dans le Presse-papiers. Vous pouvez maintenant utiliser cette URL dans la liste des applications autorisées ou bloquées.

Exemple : recherchez l'application Skype dans le Store. L’URL que vous utilisez est `http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51`.



### <a name="additional-options"></a>Options supplémentaires

Vous pouvez également cliquer sur **Importer** pour remplir la liste à partir d’un fichier csv au format <*URL de l’application*>, <*Nom de l’application*>, <*Développeur de l’application*>, ou cliquer sur **Exporter** pour créer un fichier csv contenant le contenu de la liste des applications restreintes dans le même format.


## <a name="browser"></a>Navigateur

- **Navigateur web** - Autorise ou bloque le navigateur web intégré sur les appareils.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

- **Wi-Fi** - Active ou désactive la fonctionnalité Wi-Fi de l'appareil.
- **Connexion Wi-Fi** - Autorise l’utilisation de la connexion Wi-Fi sur l’appareil.
- **Se connecter automatiquement aux points d'accès Wi-Fi** - Autorise l’appareil à se connecter automatiquement aux points d’accès Wi-Fi gratuits et à accepter automatiquement les termes et conditions de la connexion.
- **Rapports de point d'accès Wi-Fi** - Envoie des informations concernant les connexions Wi-Fi pour aider l’utilisateur à détecter les connexions proches.
- **NFC** - Active ou désactive les opérations qui utilisent la communication NFC sur les appareils pris en charge.
- **Bluetooth** - Active ou désactive la fonctionnalité Bluetooth de l’appareil.
