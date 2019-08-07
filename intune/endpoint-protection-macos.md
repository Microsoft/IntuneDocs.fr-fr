---
title: Ajouter Endpoint Protection sur macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils macOS, utilisez Gatekeeper pour déterminer l’emplacement où les applications peuvent être installées, notamment le Mac App Store. Activez ou configurez également un pare-feu pour autoriser ou bloquer des applications spécifiques, utiliser le mode furtif et même bloquer certains types de connexion entrante à l’aide de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d4aa0c47f0aa099ff469eb31b212f387836ad69b
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68756507"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Paramètres Endpoint Protection pour MacOS dans Intune  

Cet article décrit les paramètres Endpoint Protection que vous pouvez configurer pour les appareils macOS. Vous configurez ces paramètres à l’aide d’un profil de configuration d’appareil macOS pour [Endpoint Protection](endpoint-protection-configure.md) dans Intune.  

## <a name="gatekeeper"></a>Gatekeeper  

- **Autoriser les applications téléchargées à partir de ces emplacements**  
  Limitez les applications qu’un appareil peut lancer, en fonction de l’emplacement à partir duquel les applications ont été téléchargées. L’objectif est de protéger les appareils contre les programmes malveillants et d’autoriser uniquement les applications provenant de sources fiables.  

  - **Non configuré**  
  - **Mac App Store**  
  - **Mac App Store et développeurs identifiés**  
  - **Partout**  

  **Par défaut** : Non configuré  

- **L’utilisateur peut remplacer Gatekeeper**  
  Permet d’empêcher les utilisateurs de remplacer les paramètres Gatekeeper et d’appuyer de façon prolongée sur la touche Ctrl pour installer une application. Quand cette option est activée, les utilisateurs peuvent appuyer de façon prolongée sur la touche Ctrl en ciblant une application de leur choix pour installer cette dernière.  
 
  - **Non configuré** : les utilisateurs peuvent contrôler-Cliquer pour installer des applications.  
  - **Bloquer** : empêche les utilisateurs d’utiliser la commande Ctrl + clic pour installer des applications.  

  **Par défaut** : Non configuré  

## <a name="firewall"></a>Pare-feu  

Utilisez le pare-feu pour contrôler les connexions par application, et non par port. L’utilisation de paramètres par application permet de tirer parti plus facilement de la protection par pare-feu. Elle contribue également à empêcher les applications indésirables de prendre le contrôle des ports réseau ouverts pour les applications légitimes.  

**Général**
- **Pare-feu**  
  Activez le pare-feu pour configurer le mode de prise en charge des connexions entrantes dans votre environnement.  
  - **Non configuré**  
  - **Activer**  

  **Par défaut** : Non configuré  

- **Connexions entrantes**  
  Bloquez toutes les connexions entrantes, à l’exception des connexions nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Cette fonctionnalité bloque également tous les services de partage, par exemple le partage de fichiers et le partage d’écran. Si vous utilisez des services de partage, conservez ce paramètre avec l’état *Non configuré*.  
  - **Non configuré**  
  - **Bloquer**  

  **Par défaut** : Non configuré  

**Autorisez ou bloquez les connexions entrantes pour des applications spécifiques.**  

  - **Applications autorisées**  
    Sélectionnez les applications explicitement autorisées à recevoir des connexions entrantes.  

  - **Applications bloquées**  
    Sélectionnez les applications qui doivent bloquer les connexions entrantes.  

  - **Mode furtif**  
    Pour empêcher l’ordinateur de répondre aux demandes de sondage, activez le mode furtif. L’appareil continue de répondre aux requêtes entrantes des applications autorisées. Les demandes inattendues, comme ICMP (ping), sont ignorées.  
    - **Non configuré**  
    - **Activer**  

    **Par défaut** : Non configuré  

## <a name="filevault"></a>FileVault  
Pour plus d’informations sur les paramètres Apple FileVault, consultez [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) dans le contenu des développeurs Apple. 

- **FileVault**  
  Vous pouvez *activer* le chiffrement de disque complet à l’aide de XTS-AES 128 avec FileVault sur les appareils qui exécutent MacOS 10,13 et versions ultérieures.  
  - **Non configuré**  
  - **Activer**  

  **Par défaut** : Non configuré  

  - **Type de clé de récupération**  
    Les clés de récupération de *clé personnelle* sont créées pour les appareils. Configurez les paramètres suivants pour la clé personnelle.  

    - **Emplacement de la clé de récupération personnelle** : spécifiez un message bref à l’utilisateur qui explique comment et où il peut récupérer sa clé de récupération personnelle. Ce texte est inséré dans le message que l’utilisateur voit sur l’écran de connexion quand il est invité à entrer sa clé de récupération personnelle si un mot de passe est oublié.  
      
    - **Rotation de clé de récupération personnelle** -spécifiez la fréquence de rotation de la clé de récupération personnelle d’un appareil. Vous pouvez sélectionner la valeur par défaut **non configurée**ou une valeur de **1** à **12** mois.  

  - **Désactiver l’invite à la déconnexion**  
    Empêcher l’invite de l’utilisateur qui demande à l’utilisateur d’activer FileVault lorsqu’il se déconnecte.  Lorsque cette valeur est définie sur Enable, l’invite à la déconnexion est désactivée et, à la place, l’utilisateur est invité à indiquer quand il se connecte.  
    - **Non configuré**  
    - **Activer** : désactive l’invite à la déconnexion.

    **Par défaut** : Non configuré  

     > [!IMPORTANT]  
     > Il existe un problème connu lorsque l’option de désactivation de l' **invite à** la déconnexion est définie sur *activer*. Lorsque cette option est définie sur *Enable*, le paramètre du **nombre de fois autorisé à contourner** doit être défini sur une valeur et ne doit pas être défini comme *non configuré*. Si la valeur *n’est pas configurée*, le profil échoue sur l’appareil. Dans ce scénario, l’appareil signale qu’il s’agit d’un résumé de l' **État du profil** comme **erreur** sans plus de détails.
     > 
     > Lorsque l’invite de désactivation de la **connexion** est définie sur *non configurée*, le **nombre de fois autorisées à ignorer** peut être *non configuré* ou avoir une valeur.  
     > 
     > Ce problème sera résolu dans une mise à jour ultérieure. 

  - **Nombre de fois où le contournement est autorisé**  
  Définissez le nombre de fois qu’un utilisateur peut ignorer les invites pour activer FileVault avant que FileVault soit requis pour que l’utilisateur se connecte.  

    - **Non configuré** : le chiffrement sur l’appareil est nécessaire pour que la connexion suivante soit autorisée.  
    - **1** à **10** : permet à un utilisateur d’ignorer l’invite de 1 à 10 fois avant d’exiger un chiffrement sur l’appareil.  
    - **Aucune limite, toujours demander** : l’utilisateur est invité à activer FileVault mais le chiffrement n’est jamais requis.  
 
    **Par défaut** : Non configuré  


