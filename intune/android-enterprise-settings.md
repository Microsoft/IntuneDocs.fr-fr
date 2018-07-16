---
title: Paramètres du mode kiosque Android dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez des appareils en mode kiosque Android Entreprise.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28eca6fa3738519602ee5b2a778bc75bde487156
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909097"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Paramètres du mode kiosque Android Entreprise dans Intune

Les profils du mode kiosque Android prennent en charge les paramètres de configuration suivants. Quand vous créez un profil, ces paramètres s’affichent quand vous choisissez **Type de profil** > **Propriétaire de l’appareil uniquement** > **Restrictions d’appareil**. Pour afficher ces paramètres, choisissez **Propriétés** à partir d’un profil de restriction d’appareil Android Entreprise, puis choisissez **Configurer**.

## <a name="general-settings"></a>Paramètres généraux :

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les utilisateurs de capturer l’écran de l’appareil.
- **Appareil photo** : choisissez **Bloquer** pour désactiver l’appareil photo de l’appareil.
- **Stratégie d’autorisation par défaut**: ce paramètre définit la stratégie d’autorisation par défaut pour les demandes d’autorisations d’exécution. Les valeurs possibles sont :
    - **Paramètre par défaut de l’appareil** : utiliser le paramètre par défaut de l’appareil.
    - **Demander** : l’utilisateur est invité à approuver l’autorisation.
    - **Accorder automatiquement** : les autorisations sont automatiquement accordées.
    - **Refuser automatiquement** : les autorisations sont automatiquement refusées.
- **Changements du volume** : choisissez **Bloquer** pour empêcher les utilisateurs de changer le volume de l’appareil.
- **Réinitialisation aux paramètres d’usine** : choisissez **Bloquer** pour empêcher les utilisateurs de réinitialiser l’appareil aux paramètres d’usine.
- **Démarrage sans échec** : choisissez **Bloquer** pour empêcher les utilisateurs de redémarrer l’appareil en mode sans échec.
- **Barre d’état** : choisissez **Bloquer** pour empêcher les utilisateurs d’accéder à la barre d’état, notamment aux notifications et aux paramètres rapides.
- **Changements des paramètres Wi-Fi** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les configurations Wi-Fi créées par le propriétaire de l’appareil. Les utilisateurs peuvent créer leurs propres configurations Wi-Fi.
- **Configuration du point d’accès Wi-Fi** : choisissez **Bloquer** pour empêcher les utilisateurs de créer ou de modifier des configurations Wi-Fi.
- **Fonctionnalités de débogage** : choisissez **Autoriser** pour permettre aux utilisateurs d’utiliser les fonctionnalités de débogage.
- **Réglage du microphone** : choisissez **Bloquer** pour empêcher les utilisateurs de régler le volume ou de désactiver le microphone.
- **E-mails de protection contre la réinitialisation aux paramètres d’usine** : choisissez **Adresses e-mail du compte Google** pour définir des adresses e-mail (séparées par des points-virgules) permettant de déverrouiller l’appareil après une réinitialisation aux paramètres d’usine. Si aucun e-mail n’est spécifié, tout le monde peut déverrouiller l’appareil après une réinitialisation aux paramètres d’usine.
- **Trappe de secours du réseau** : choisissez **Activer** pour autoriser l’activation de la fonctionnalité de trappe de secours du réseau. Si une connexion réseau n’est pas possible au moment du démarrage, la trappe de secours invite l’utilisateur à se connecter temporairement à un réseau afin d’actualiser la stratégie de l’appareil. Une fois la stratégie appliquée, le réseau temporaire est oublié et l’appareil continue de démarrer. Vous n’avez plus la possibilité de vous connecter à un réseau s’il n’existe pas de réseau approprié dans la dernière stratégie et que l’appareil démarre dans une application en mode de verrouillage de tâche, ou si l’utilisateur ne peut pas atteindre les paramètres de l’appareil.
- **Autoriser l’installation à partir de sources inconnues** : choisissez **Autoriser** pour permettre aux utilisateurs d’effectuer l’installation à partir de sources inconnues.
- **Mise à jour système** : choisissez une option pour définir la façon dont l’appareil traite les mises à jour à distance :
    - **Paramètre par défaut de l’appareil** : utiliser le paramètre par défaut de l’appareil.
    - **Automatique** : les mises à jour logicielles sont installées automatiquement.
    - **Différé** : les mises à jour sont remises à une date ultérieure.
    - **Fenêtre de maintenance** : les utilisateurs sont invités à approuver la mise à jour dans une fenêtre de maintenance.

## <a name="kiosk-settings"></a>Paramètres kiosque

- **Mode kiosque** : définit si l’appareil peut exécuter une seule application ou plusieurs. Pour plus d’informations, consultez [Paramètres de kiosque pour les appareils Android](android-kiosk-settings.md).
    - **Kiosque avec une seule application** : les utilisateurs ne peuvent accéder qu’à une seule application.
    - **Kiosque multi-application**: les utilisateurs peuvent accéder à un ensemble limité d’applications.

## <a name="device-password-settings"></a>Paramètres de mot de passe des appareils

- **Keyguard** : choisissez **Désactiver** pour empêcher les utilisateurs d’utiliser Keyguard sur l’appareil.
- **Type de mot de passe obligatoire** : définissez le type de mot de passe demandé pour l’appareil.
- **Longueur minimale du mot de passe** : définissez la longueur minimale du mot de passe demandé pour l’appareil.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : définissez le nombre d’échecs de connexion qui doivent se produire avant réinitialisation de l’appareil.

## <a name="power-settings"></a>Paramètres d’alimentation

- **Délai avant verrouillage de l’écran** : définissez la durée d’inactivité nécessaire avant le verrouillage de l’appareil.
- **Écran actif quand l’appareil est branché** : choisissez quelles sources d’alimentation permettent de conserver actif l’écran de l’appareil quand il est branché.

## <a name="users-and-accounts-settings"></a>Paramètres des utilisateurs et des comptes

- **Ajouter de nouveaux utilisateurs** : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter de nouveaux utilisateurs.
- **Suppression d’utilisateurs** : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des utilisateurs.
- **Modifications apportées aux comptes** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier des comptes.

## <a name="next-steps"></a>Étapes suivantes
[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).


