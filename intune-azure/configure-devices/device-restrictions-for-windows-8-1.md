---
title: "Paramètres de restriction d’appareil Intune pour Windows 8.1"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : Découvrez les paramètres Intune qui vous permettent de contrôler les paramètres et fonctionnalités des appareils Windows 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fe5785e9-8d35-4ad7-95e8-d50f8d87154a
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 24758b04f45427b25980e8a7eb833c51c73ba077
ms.lasthandoff: 02/18/2017


---

# <a name="windows-81-and-later-device-restriction-settings-in-microsoft-intune"></a>Paramètres de restriction des appareils Windows 8.1 et versions ultérieures dans Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Général
-     **Appliquer toutes les configurations à Windows 10** - Permet aux paramètres de cette stratégie d’être appliqués aux appareils Windows 10 en plus des appareils Windows 10 et Windows 8.1.
-     **Envoi des données de diagnostic** - Autorise l’appareil à soumettre des informations de diagnostic à Microsoft.
-     **Pare-feu** - Nécessite l’activation du Pare-feu Windows.
-     **Contrôle de compte d'utilisateur** - Nécessite l’utilisation du contrôle de compte d’utilisateur (UAC) sur les appareils.
## <a name="password"></a>Mot de passe
-     **Type de mot de passe requis** Oblige l’utilisateur final à saisir un mot de passe pour accéder à l’appareil.
-     **Longueur minimale du mot de passe** - Configure la longueur minimale requise (en caractères) pour le mot de passe sur les appareils.
-     **Nombre d'échecs de connexion avant réinitialisation de l'appareil** - Réinitialise l’appareil si le nombre d’échecs de tentative spécifié est atteint.
-     **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** - Spécifie le nombre de minutes pendant lesquelles un appareil doit être inactif avant qu’un mot de passe soit nécessaire pour le déverrouiller.
-     **Expiration du mot de passe (jours)** - Spécifie le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
-     **Empêcher la réutilisation des mots de passe précédents** - Spécifie si l’utilisateur peut configurer des mots de passe précédemment utilisés.
-     **Mot de passe image et code confidentiel** - Permet l’utilisation d’un mot de passe image et d’un code confidentiel. Un mot de passe image permet à l’utilisateur de se connecter en effectuant des gestes sur une image. Un code confidentiel permet aux utilisateurs de se connecter rapidement à l’aide d’un code à quatre chiffres.
-     **Chiffrement** - Exige que les fichiers soient chiffrés sur l’appareil.<br>Pour appliquer le chiffrement à des appareils exécutant Windows 8.1, vous devez installer la [Mise à jour du client MDM pour Windows publiée en décembre 2014](https://support.microsoft.com/en-us/kb/3013816) sur chaque appareil.
Si vous activez ce paramètre pour les appareils Windows 8.1, tous les utilisateurs de l’appareil doivent disposer d’un compte Microsoft.
Pour que le chiffrement fonctionne, l'appareil doit répondre aux conditions de certification matérielle de la spécification [InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97) de Microsoft.
Quand vous appliquez le chiffrement à un appareil, vous pouvez uniquement obtenir la clé de récupération à partir du compte Microsoft de l’utilisateur, accessible à partir de son compte OneDrive. Vous ne pouvez pas récupérer cette clé au nom d'un utilisateur.     



## <a name="browser"></a>Navigateur
-     **Remplissage automatique** - Permet aux utilisateurs de modifier les paramètres de saisie semi-automatique dans le navigateur.
-     **Avertissements en cas de fraude** - Active ou désactive les avertissements pour les sites web potentiellement frauduleux.
-     **SmartScreen** - Active ou désactive les avertissements pour les sites web potentiellement frauduleux.
-     **JavaScript** - Permet au navigateur d’exécuter des scripts, par exemple un script Java.
-     **Fenêtres publicitaires** - Active ou désactive le bloqueur de fenêtres publicitaires du navigateur.
-     **Envoyer des en-têtes Do Not Track** - Envoie un en-tête Do Not Track aux sites visités dans Internet Explorer.
-     **Plug-ins** - Permet aux utilisateurs d’ajouter des plug-ins à Internet Explorer.
-     **Entrée à mot unique sur le site intranet** - Permet l’utilisation d’un mot unique pour diriger Internet Explorer vers un site web, tel que Bing.
-     **Détection automatique du site intranet** - Facilite la configuration de la sécurité des sites intranet dans Internet Explorer.
-     **Niveau de sécurité pour Internet** - Définit le niveau de sécurité d’Internet Explorer pour les sites Internet.
-     **Niveau de sécurité pour intranet** - Définit le niveau de sécurité d’Internet Explorer pour les sites intranet.
-     **Niveau de sécurité des sites approuvés** - Configure le niveau de sécurité pour la zone Sites de confiance.
-     **Sécurité élevée pour les sites sensibles** - Configure le niveau de sécurité pour la zone Sites sensibles.
-     **Accès au menu du mode Entreprise** - Permet aux utilisateurs d'accéder aux options du menu Mode entreprise à partir d'Internet Explorer.
Si vous sélectionnez ce paramètre, vous pouvez également spécifier un **Emplacement du rapport de journalisation**, qui contient une URL vers un rapport affichant les sites web pour lesquels les utilisateurs ont activé l’accès en Mode entreprise.
-     **Emplacement de la liste des sites en Mode entreprise** - Spécifie l'emplacement de la liste des sites web qui utilisent le mode entreprise quand il est actif.
## <a name="cellular"></a>Données mobiles
-     **Itinérance des données** - Autorise l’itinérance des données quand l’appareil se trouve sur un réseau de téléphonie mobile.
## <a name="cloud-and-storage"></a>Cloud et stockage
-     **URL des dossiers de travail** - Ce paramètre définit l’URL du dossier de travail pour autoriser la synchronisation des documents entre les appareils.
-     **Accéder à l'application Windows Mail sans compte Microsoft** - Autorise l’accès à l’application Windows Mail sans compte Microsoft.     

