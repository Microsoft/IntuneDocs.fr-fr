---
title: Paramètres kiosque pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez vos appareils Windows 10 (et ultérieur) en tant que kiosques mono-application et multi-application, personnalisez le menu Démarrer, ajoutez des applications, affichez la barre des tâches et configurez un navigateur web dans Microsoft Intune.
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
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7886f533f6ffa379132ac7c898bc5c1a1dac9111
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836538"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Paramètres d’appareil Windows 10 et ultérieur pour une exécution en tant que kiosque dans Intune

Vous pouvez configurer les appareils Windows 10 et ultérieur pour qu’ils s’exécutent en mode kiosque mono-application ou en mode kiosque multi-application.

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Windows 10 et version ultérieure. Dans le cadre de votre solution de gestion des appareils mobiles, utilisez ces paramètres pour configurer vos appareils Windows 10 et version ultérieure afin qu’ils s’exécutent en mode kiosque.

En tant qu’administrateur Intune, vous pouvez créer ces paramètres et les affecter à vos appareils.

Pour en savoir plus sur la fonctionnalité de kiosque Windows dans Intune, consultez [Configurer les paramètres kiosque](kiosk-settings.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez le profil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran

Lorsque vous choisissez le mode kiosque à application unique, entrez les paramètres suivants :

- **Type d’ouverture de session utilisateur** : les applications que vous ajoutez s’exécutent sous le compte d’utilisateur que vous entrez. Les options disponibles sont les suivantes :

  - **Ouverture de session automatique (Windows 10, version 1803+)**  : pour les kiosques dans des environnements publics qui ne nécessitent pas de connexion de la part de l’utilisateur, similaire à un compte invité. Ce paramètre utilise le [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Compte d’utilisateur local** : entrez le compte d’utilisateur local (sur l’appareil). Le compte que vous entrez est utilisé pour la connexion au kiosque.

- **Type d’application** : Sélectionnez **Application du Store**.

- **Application à exécuter en mode kiosque** : choisissez **Ajouter une application du Store**, puis sélectionnez une application dans la liste.

    Aucune application n’est répertoriée ? En ajouter à l’aide de la procédure sous [Applications clientes](apps-add.md).

    Cliquez sur **OK** pour enregistrer vos modifications.

- **Paramètres du navigateur kiosque** : Ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à obtenir l’[application de navigateur kiosque](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) dans le Store, ajoutez-la à Intune en tant qu’[application cliente](apps-add.md), puis affectez l’application aux appareils kiosques.

  entrez les paramètres suivants :

  - **URL de page d’accueil par défaut** : entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur kiosque. Par exemple, entrez `http://bing.com` ou `http://www.contoso.com`.

  - **Bouton Accueil** : **Afficher** ou **Masquer** le bouton Accueil du navigateur kiosque. Par défaut, le bouton ne s’affiche pas.

  - **Boutons de navigation** : **Afficher** ou **Masquer** les boutons Suivant et Précédent. Par défaut, les boutons de navigation ne s’affichent pas.

  - **Bouton Terminer la session** : **Afficher** ou **Masquer** le bouton de fin de session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, etc.), puis ouvre l’URL par défaut. Par défaut, le bouton ne s’affiche pas.

  - **Actualiser le navigateur après la durée d’inactivité** : entrez la durée d’inactivité (1 à 1 440 minutes) avant le redémarrage du navigateur kiosque dans un nouvel état. La durée d’inactivité est le nombre de minutes écoulées depuis la dernière interaction de l’utilisateur. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

  - **Sites web autorisés** : utilisez ce paramètre pour autoriser l’ouverture de sites web spécifiques. En d’autres termes, utilisez cette fonctionnalité pour restreindre ou empêcher des sites web sur l’appareil. Par exemple, vous pouvez autoriser l’ouverture de tous les sites web sur `http://contoso.com*`. Par défaut, tous les sites web sont autorisés.
 
      Pour autoriser des sites web spécifiques, chargez un fichier dans lequel les sites web autorisés sont listés sur des lignes séparées. Si vous n’ajoutez pas de fichier, tous les sites web sont autorisés. Intune prend en charge * (astérisque) comme caractère générique.

      Votre exemple de fichier doit ressembler à la liste suivante :

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="multi-app-kiosks"></a>Applications multiples plein écran

Dans ce mode, les applications sont disponibles dans le menu Démarrer. Ce sont les seules applications que l’utilisateur peut ouvrir.

Lorsque vous choisissez le mode kiosque multi-application, entrez les paramètres suivants :

- **Cibler Windows 10 dans les appareils en mode S** : Choisissez **Oui** pour autoriser les applications de Store et les applications AUMID (à l’exception des applications Win32) dans le profil kiosque. Choisissez **Non** pour autoriser les applications Store, les applications Win32 et les applications AUMID dans le profil de kiosque. Lorsque vous choisissez **Non**, ce profil de kiosque n’est pas déployé sur des appareils en mode S.

- **Type d’ouverture de session utilisateur** : les applications que vous ajoutez s’exécutent sous le compte d’utilisateur que vous entrez. Les options disponibles sont les suivantes :

  - **Ouverture de session automatique (Windows 10, version 1803+)**  : pour les kiosques dans des environnements publics qui ne nécessitent pas de connexion de la part de l’utilisateur, similaire à un compte invité. Ce paramètre utilise le [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Compte d’utilisateur local** : **Ajoutez** le compte d’utilisateur local (à appareil). Le compte que vous entrez est utilisé pour la connexion au kiosque.
  - **Utilisateur ou groupe Azure AD (Windows 10, version 1803+)**  : Sélectionnez **Ajouter** pour choisir les utilisateurs ou groupes Azure AD dans la liste. Vous pouvez sélectionner plusieurs utilisateurs et groupes. Choisissez **Sélectionner** pour enregistrer vos changements.
  - **Visiteur HoloLens** : le compte visiteur est un compte invité qui ne nécessite pas d’informations d’identification ou d’authentification de l’utilisateur, comme décrit dans [Concepts du mode PC partagé](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applications** : ajoutez les applications à exécuter sur l’appareil kiosque. N’oubliez pas que vous pouvez ajouter plusieurs applications.

  - **Ajouter une application de Store** : ajoutez une application à partir du Microsoft Store pour Entreprises. Si vous n’avez aucune application répertoriée, vous pouvez obtenir des applications et [les ajouter à Intune](store-apps-windows.md). Par exemple, vous pouvez ajouter Kiosk Browser, Excel, OneNote et bien plus encore.

  - **Ajouter une application Win32** : une application Win32 est une application de bureau classique, par exemple Visual Studio Code ou Google Chrome. Entrez les propriétés suivantes :

    - **Nom d’application** : Obligatoire. Entrez un nom pour l'application.
    - **Chemin local** : Obligatoire. Entrez le chemin d’accès au fichier exécutable, par exemple `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **Identifiant AUMID de l’application** : Entrez l’identifiant AUMID de l’application Win32. Ce paramètre détermine la mise en page de démarrage de la mosaïque sur le bureau. Pour obtenir cet ID, consultez [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
    - **Taille de la vignette** : Obligatoire. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.
  
  - **Ajouter par AUMID** : utilisez cette option pour ajouter des applications fournies avec Windows, par exemple le Bloc-notes ou la Calculatrice. Entrez les propriétés suivantes : 

    - **Nom d’application** : Obligatoire. Entrez un nom pour l'application.
    - **Identifiant AUMID de l’application** : Obligatoire. Entrez l’identifiant AUMID de l’application Windows. Pour obtenir cet ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Taille de la vignette** : Obligatoire. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.

  > [!TIP]
  > Après avoir ajouté toutes les applications, vous pouvez modifier l’ordre d’affichage en cliquant sur les applications et en les faisant glisser dans la liste.  

  Cliquez sur **OK** pour enregistrer vos modifications.

- **Paramètres du navigateur kiosque** : Ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à déployer une application de navigateur web sur les appareils de type kiosque via des [Applications clientes](apps-add.md).

  entrez les paramètres suivants :

  - **URL de page d’accueil par défaut** : entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur kiosque. Par exemple, entrez `http://bing.com` ou `http://www.contoso.com`.

  - **Bouton Accueil** : **Afficher** ou **Masquer** le bouton Accueil du navigateur kiosque. Par défaut, le bouton ne s’affiche pas.

  - **Boutons de navigation** : **Afficher** ou **Masquer** les boutons Suivant et Précédent. Par défaut, les boutons de navigation ne s’affichent pas.

  - **Bouton Terminer la session** : **Afficher** ou **Masquer** le bouton de fin de session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, etc.), puis ouvre l’URL par défaut. Par défaut, le bouton ne s’affiche pas.

  - **Actualiser le navigateur après la durée d’inactivité** : entrez la durée d’inactivité (1 à 1 440 minutes) avant le redémarrage du navigateur kiosque dans un nouvel état. La durée d’inactivité est le nombre de minutes écoulées depuis la dernière interaction de l’utilisateur. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

  - **Sites web autorisés** : utilisez ce paramètre pour autoriser l’ouverture de sites web spécifiques. En d’autres termes, utilisez cette fonctionnalité pour restreindre ou empêcher des sites web sur l’appareil. Par exemple, vous pouvez autoriser l’ouverture de tous les sites web sur `contoso.com*`. Par défaut, tous les sites web sont autorisés.

    Pour autoriser des sites web spécifiques, chargez un fichier .csv qui inclut une liste des sites web autorisés. Si vous n’ajoutez pas de fichier .csv, tous les sites web sont autorisés.

  Cliquez sur **OK** pour enregistrer vos modifications.

- **Utiliser une autre disposition de démarrage** : choisissez **Oui** pour entrer un fichier XML qui décrit la façon dont les applications apparaissent dans le menu Démarrer, et notamment l’ordre des applications. Utilisez cette option si vous avez besoin de davantage de personnalisation dans votre menu Démarrer. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fournit quelques conseils et un exemple de code XML.

- **Barre des tâches Windows** : choisissez d’**Afficher** ou de **Masquer** la barre des tâches. Par défaut, la barre des tâches ne s’affiche pas. Des icônes, telles que l’icône Wi-Fi, sont visibles, mais les paramètres ne sont pas modifiables par les utilisateurs finaux.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils kiosque pour des appareils [Android](device-restrictions-android.md#kiosk), [Android Entreprise](device-restrictions-android-for-work.md#kiosk-settings) et [Windows Holographic for Business](kiosk-settings-holographic.md).
