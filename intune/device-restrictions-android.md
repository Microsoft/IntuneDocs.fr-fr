---
title: "Paramètres de restriction d’appareil Intune pour Android"
titlesuffix: Azure portal
description: "Découvrez les paramètres Intune qui vous permettent de contrôler les paramètres et fonctionnalités des appareils Android."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 559550860d0882b20a005a5d0957be761978cbe6
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Paramètres de restriction des appareils Android et Samsung Knox Standard dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilisez ces paramètres avec une stratégie de restriction d’appareil Android pour configurer les appareils de votre organisation.

>[!TIP]
>Si les paramètres souhaités ne sont pas disponibles, vous pouvez normalement configurer vos appareils à l’aide un [profil personnalisé](custom-settings-android.md).

## <a name="general"></a>Général

- **Appareil photo** - Autorise l’utilisation de l’appareil photo de l’appareil.
- **Copier et coller (Samsung Knox uniquement)** - Autorise les fonctions Copier et Coller sur l’appareil.
- **Partage du Presse-papiers entre applications (Samsung Knox uniquement)** - Autorise l’utilisation du Presse-papiers pour copier-coller entre les applications.
- **Envoi des données de diagnostic (Samsung Knox uniquement)** - Empêche l’utilisateur d’envoyer des données de diagnostic depuis l’appareil.
- **Réinitialisation aux paramètres d’usine (Samsung Knox uniquement)** - Autorise l’utilisateur à rétablir les paramètres d’usine sur l’appareil.
- **Géolocalisation (Samsung Knox uniquement)** - Permet à l’appareil d’utiliser les informations de localisation.
- **Mise hors tension (Samsung Knox uniquement)** - Autorise l’utilisateur à mettre l’appareil hors tension.<br>Si vous désactivez cette option, vous ne pouvez pas définir le **Nombre d’échecs de connexion avant réinitialisation de l’appareil**.
- **Capture d’écran (Samsung Knox uniquement)** - Autorise l’utilisateur à capturer le contenu de l’écran comme image.
- **Assistant vocal (Samsung Knox uniquement)** - Autorise l’utilisation du logiciel Assistant vocal sur l’appareil.
- **YouTube (Samsung Knox uniquement)** - Autorise l’utilisation de l’application YouTube sur l’appareil.
- **Appareils partagés(Samsung Knox uniquement)** - Permet de configurer un appareil Samsung Knox standard géré en tant qu’appareil partagé. Dans ce mode, les utilisateurs finaux peuvent se connecter et se déconnecter de l’appareil avec leurs informations d’identification Azure AD. L’appareil reste géré, qu’il soit en cours d’utilisation ou non.<br>Utilisée conjointement avec un profil de certificat SCEP, cette fonctionnalité permet aux utilisateurs finaux de partager un appareil avec le même ensemble d’applications pour tous les utilisateurs, mais avec leur propre certificat utilisateur SCEP.  Quand les utilisateurs se déconnectent, toutes les données d’application sont effacées.  Cette fonctionnalité est limitée aux applications métier.
- **Empêcher les changements de date et d'heure (Samsung Knox)** : empêchez l’utilisateur de modifier la date et l’heure sur l’appareil. 

## <a name="password"></a>Mot de passe

- **Mot de passe** - L’utilisateur final doit entrer un mot de passe pour accéder à l’appareil. |Yes|Yes|
- **Longueur minimale du mot de passe** - Entrez la longueur minimale du mot de passe qu’un utilisateur doit configurer (entre 4 et 16 caractères).
- **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** - Spécifie le nombre de minutes d’inactivité avant verrouillage automatique de l’appareil.
- **Nombre d'échecs de connexion avant réinitialisation de l'appareil** - Spécifie le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil.
- **Expiration du mot de passe (jours)** - Spécifie le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
-  **Type de mot de passe obligatoire** - Spécifie le niveau de complexité du mot de passe exigé, et si les appareils biométriques peuvent être utilisés. Choisissez parmi :
    - **Paramètre par défaut de l’appareil**
    - **Sécurité biométrique faible**
    - **Au moins numérique**
    - **Chiffres complexes** - Les chiffres répétés ou consécutifs tels que « 1111 » ou « 1234 » ne sont pas autorisés<sup>1</sup>
    - **Au moins alphabétique**
    - **Au moins alphanumérique**
    - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** - Empêche l’utilisateur final de créer un mot de passe qu’il a déjà utilisé.
- **Déverrouillage par empreinte digitale (Samsung Knox uniquement)** - Permet l’utilisation d’une empreinte digitale pour déverrouiller les appareils pris en charge.
- **Smart Lock et autres agents de confiance** - Vous permet de contrôler la fonctionnalité Smart Lock sur les appareils Android compatibles (Samsung Knox Standard 5.0 et modèles ultérieurs). Cette fonctionnalité du téléphone, parfois appelée agents de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil si celui-ci se trouve à un emplacement approuvé. Par exemple, cela peut servir lorsque l’appareil est connecté à un appareil Bluetooth spécifique ou quand il se trouve à proximité d’une balise NFC. Vous pouvez utiliser ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.
- **Chiffrement** - Exige que les fichiers soient chiffrés sur l’appareil.

<sup>1</sup> avant d’affecter ce paramètre sur les appareils, veillez à mettre à jour de l’application portail d’entreprise vers la dernière version sur ces appareils.

Si vous configurez le paramètre **Chiffres complexes** et l’affectez à un appareil qui exécute une version antérieure à la version 5.0 d’Android, le comportement suivant s’applique.
- Si l’application Portail d’entreprise exécute une version antérieure à 1704, aucune stratégie de code PIN ne sera appliquée à l’appareil et une erreur s’affichera dans le portail Azure.
- Si l’application Portail d’entreprise fonctionne avec la version 1704 ou une version ultérieure, un simple code PIN peut être appliqué. Les versions d’Android antérieures à 5.0 ne gèrent pas ce paramètre. Aucune erreur ne s’affiche dans le portail Azure.


## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (Samsung Knox uniquement)** - Permet à l’utilisateur d’accéder à Google Play Store sur l’appareil.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes pour les appareils Android et Samsung Knox Standard :

Une liste **Applications interdites** : répertorie les applications (qui ne sont pas gérées par Intune) qui seront signalées si les utilisateurs les installent et les exécutent.
Une liste **Applications approuvées** : répertorie les applications que les utilisateurs sont autorisés à installer. Pour rester conformes, les utilisateurs ne doivent pas installer d’autres applications. Les applications qui sont gérées par Intune sont autorisées automatiquement.
Les profils d’appareil qui contiennent des paramètres d’applications restreintes doivent être attribués à des groupes d’utilisateurs.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application, et l'URL de l'application dans l’App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Comment spécifier l’URL vers une application dans l’App Store

Pour spécifier une URL d’application dans la liste des applications conformes et non conformes, procédez comme suit :

Dans la [section Applications de Google Play](https://play.google.com/store/apps), recherchez l’application à utiliser.

Ouvrez la page d’installation de l’application, puis copiez l’URL dans le Presse-papiers. Vous pouvez maintenant utiliser cette URL dans la liste des applications conformes ou non conformes.

Exemple : Accédez à la [section Applications de Google Play](https://play.google.com/store/apps) pour rechercher **Microsoft Planner**. Utilisez l’URL **https://play.google.com/store/apps/details?id=com.microsoft.planner**.

### <a name="additional-options"></a>Options supplémentaires

Vous pouvez également cliquer sur **Importer** pour obtenir la liste à partir d’un fichier .csv. Utilisez le format <*URL de l’application*>, <*Nom de l’application*>, <*Développeur de l’application*>, ou cliquer sur **Exporter** dans le fichier csv contenant le contenu de la liste des applications restreintes dans le même format.      

## <a name="browser"></a>Navigateur

- **Navigateur web (Samsung Knox uniquement)** - Spécifie si le navigateur web par défaut de l’appareil peut être utilisé.
- **Remplissage automatique (Samsung Knox uniquement)** - Autorise l’utilisation de la fonction de remplissage automatique du navigateur web.
- **Cookies (Samsung Knox uniquement)** - Autorise le navigateur web de l’appareil à utiliser des cookies.
- **Javascript (Samsung Knox uniquement)** - Autorise le navigateur web de l’appareil à exécuter des scripts Java.
- **Fenêtres publicitaires (Samsung Knox uniquement)** - Autorise l’utilisation du bloqueur de fenêtres publicitaires dans le navigateur.

## <a name="allow-or-block-apps"></a>Autoriser ou bloquer des applications

Ces paramètres peuvent être utilisés pour spécifier les applications qui peuvent être installées ou lancées sur les appareils qui exécutent Samsung Knox Standard uniquement.
En outre, vous pouvez également spécifier les applications installées qui seront masquées sur l’appareil de l’utilisateur. Les utilisateurs ne peuvent pas exécuter ces applications.

- **Applications dont l’installation est autorisée (Samsung Knox Standard uniquement)**
- **Applications dont le lancement est bloqué (Samsung Knox Standard uniquement)**
- **Applications masquées pour l’utilisateur (Samsung Knox Standard uniquement)**

Pour chaque paramètre, configurez une liste d’applications à l’aide d’une des opérations suivantes :

- **Ajouter des applications par nom de package** : Option principalement utilisée pour les applications métier. Entrez le nom de l’application et le nom du package de l’application.
- **Ajouter des applications par URL** : entrez le nom de l’application et son URL dans Google Play Store.
- **Ajouter des applications gérées** : sélectionnez l’application requise dans la liste des applications que vous gérez avec Intune.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Sauvegarde Google (Samsung Knox uniquement)** - Autorise l’utilisation de la sauvegarde de Google.
- **Synchronisation automatique de compte Google (Samsung Knox uniquement)** - Autorise la synchronisation automatique des paramètres du compte Google.
- **Stockage amovible (Samsung Knox uniquement)** - Permet à l’appareil d’utiliser un stockage amovible, par exemple une carte SD.
- **Chiffrement des cartes de stockage (Samsung Knox uniquement)** - Spécifie si la carte de stockage de l’appareil doit être chiffrée.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

- **Itinérance des données (Samsung Knox uniquement)** - Autorise l’itinérance des données quand l’appareil se trouve sur un réseau cellulaire.
- **Messagerie SMS/MMS (Samsung Knox uniquement)** - Permet l’utilisation de la messagerie SMS et MMS sur l’appareil.
- **Numérotation vocale (Samsung Knox uniquement)** - Active ou désactive la fonctionnalité de numérotation vocale sur l’appareil.
- **Itinérance vocale (Samsung Knox uniquement)** - Autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Bluetooth (Samsung Knox uniquement)** - Autorise l’utilisation de la fonctionnalité Bluetooth sur l’appareil.
- **NFC (Samsung Knox uniquement)** - Autorise les opérations qui utilisent la communication en champ proche sur les appareils pris en charge.
- **Wi-Fi (Samsung Knox uniquement)** - Autorise l’utilisation des fonctionnalités Wi-Fi de l’appareil.
- **Connexion Wi-Fi (Samsung Knox uniquement)** - Permet l’utilisation de la connexion Wi-Fi sur l’appareil.

## <a name="kiosk"></a>Kiosk

Les paramètres Kiosk s’appliquent uniquement aux appareils Samsung Knox Standard et uniquement aux applications que vous gérez à l’aide d’Intune.

- **Sélectionner une application gérée** : choisissez une des options suivantes pour ajouter une ou plusieurs applications gérées pouvant s’exécuter quand l’appareil est en mode plein écran. Aucune autre application ne pourra s'exécuter sur l'appareil.
    - **Ajouter des applications par nom de package**
    - **Ajouter des applications par URL**
    - **Ajouter des applications gérées**
- **Bouton de veille de l'écran** - Active ou désactive le bouton Veille/sortie de veille de l’écran sur l’appareil.
- **Boutons de volume** - Active ou désactive l’utilisation des boutons de volume sur l’appareil.


## <a name="next-steps"></a>Étapes suivantes

Continuez à utiliser les instructions du [Guide pratique pour configurer des paramètres de restriction d’appareils dans Microsoft Intune](device-restrictions-configure.md) pour créer puis pour affecter le profil de restriction d’appareil.
