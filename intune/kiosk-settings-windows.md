---
title: Paramètres kiosque pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez vos appareils Windows 10 (et ultérieur) en tant que kiosques mono-application et multi-application, personnalisez le menu Démarrer, ajoutez des applications, affichez la barre des tâches et configurez un navigateur web dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6fb1111a7f660e8c59f45fb1893364dcadd34dca
ms.sourcegitcommit: 6a8de7bb4870ea19aa08db1f188ea7b5e8a387dd
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69487749"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Paramètres d’appareil Windows 10 et ultérieur pour une exécution en tant que kiosque dans Intune

Vous pouvez configurer les appareils Windows 10 et ultérieur pour qu’ils s’exécutent en mode kiosque mono-application ou en mode kiosque multi-application.

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Windows 10 et version ultérieure. Dans le cadre de votre solution de gestion des appareils mobiles, utilisez ces paramètres pour configurer vos appareils Windows 10 et version ultérieure afin qu’ils s’exécutent en mode kiosque.

En tant qu’administrateur Intune, vous pouvez créer ces paramètres et les affecter à vos appareils.

Pour en savoir plus sur la fonctionnalité de kiosque Windows dans Intune, consultez [Configurer les paramètres kiosque](kiosk-settings.md).

## <a name="before-you-begin"></a>Avant de commencer

- [Créez le profil](kiosk-settings.md#create-the-profile).

- Ce profil de kiosque est directement lié au profil de restrictions d’appareil que vous créez avec les [paramètres de kiosque de Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser). Pour récapituler :

  1. Créez ce profil de kiosque pour exécuter l’appareil en mode kiosque.
  2. Créez le [profil de restrictions d’appareil](device-restrictions-windows-10.md#microsoft-edge-browser) et configurez les fonctionnalités et paramètres spécifiques autorisés dans Microsoft Edge.

> [!IMPORTANT] 
> Veillez à attribuer ce profil de kiosque aux mêmes appareils que ceux de votre [profil Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran

Exécute une seule application sur l’appareil.

- **Sélectionner un mode kiosque** : choisissez **Kiosque plein écran mono-application**.

- **Type d’ouverture de session utilisateur** : les applications que vous ajoutez s’exécutent comme le compte d’utilisateur que vous entrez. Les options disponibles sont les suivantes :

  - **Ouverture de session automatique (Windows 10 version 1803 et versions ultérieures)** : utilisez les bornes des environnements publics qui ne nécessitent pas de connexion de l’utilisateur, similaire à un compte invité. Ce paramètre utilise le [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Compte d’utilisateur local** : entrez le compte d’utilisateur local (sur l’appareil). Le compte que vous entrez se connecte au kiosque.

- **Type d’application** : sélectionnez le type d’application. Les options disponibles sont les suivantes :

  - **Ajouter un navigateur Microsoft Edge** : sélectionnez **Navigateur Microsoft Edge**, puis choisissez le **Type de mode kiosque Microsoft Edge** :

    - **Signalisation numérique/interactive**:  ouvre une URL en mode plein écran et affiche uniquement le contenu sur ce site web. [Configurer les signes numériques](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fournit plus d’informations sur cette fonctionnalité.
    - **Navigation publique (InPrivate)**  : exécute une version multi-onglets limitée de Microsoft Edge. Les utilisateurs peuvent parcourir publiquement ou terminer leur session de navigation.

    Pour plus d’informations sur ces options, consultez [Déployer le mode kiosque dans Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Ce paramètre active le navigateur Microsoft Edge sur l’appareil. Pour configurer des paramètres propres à Microsoft Edge, créez un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme > **Restrictions de l’appareil** >  **Navigateur Microsoft Edge**). [Navigateur Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) liste et décrit les paramètres disponibles.

  - **Ajouter un navigateur kiosque** : sélectionnez **Paramètres du navigateur kiosque**. Ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à obtenir l' [application de navigateur Kiosk](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) à partir du Store, puis à l’ajouter à Intune en tant qu' [application cliente](apps-add.md). Ensuite, attribuez l’application aux appareils kiosque.

    entrez les paramètres suivants :

    - **URL de la page d’accueil par défaut** : entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur du kiosque. Par exemple, entrez `http://bing.com` ou `http://www.contoso.com`.

    - **Bouton Accueil** : **Afficher** ou **Masquer** le bouton Accueil du navigateur du kiosque. Par défaut, le bouton ne s’affiche pas.

    - **Boutons de navigation** : **Afficher** ou **Masquer** les boutons Suivant et Précédent. Par défaut, les boutons de navigation ne s’affichent pas.

    - **Bouton Terminer la session** : **Afficher** ou **Masquer** le bouton de fin de session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, etc.), puis ouvre l’URL par défaut. Par défaut, le bouton ne s’affiche pas.

    - **Actualiser le navigateur après la durée d’inactivité** : entrez la durée d’inactivité (1 à 1 440 minutes) avant le redémarrage du navigateur de kiosque dans un nouvel état. La durée d’inactivité est le nombre de minutes écoulées depuis la dernière interaction de l’utilisateur. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

    - **Sites web autorisés** : utilisez ce paramètre pour autoriser l’ouverture de sites web spécifiques. En d’autres termes, utilisez cette fonctionnalité pour restreindre ou empêcher des sites web sur l’appareil. Par exemple, vous pouvez autoriser l’ouverture de tous les sites web sur `http://contoso.com*`. Par défaut, tous les sites web sont autorisés.

      Pour autoriser des sites web spécifiques, chargez un fichier dans lequel les sites web autorisés sont listés sur des lignes séparées. Si vous n’ajoutez pas de fichier, tous les sites web sont autorisés. Intune prend en charge `*` (astérisque) comme caractère générique.

      Votre exemple de fichier doit ressembler à la liste suivante :

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`

    > [!NOTE]
    > Les kiosques Windows 10 avec ouverture de la ligne automatique activée à l’aide de Microsoft Kiosk Browser doivent utiliser une licence hors connexion de la Microsoft Store pour l’entreprise. Cette exigence est due au fait que l’ouverture de la chaîne automatique utilise un compte d’utilisateur local sans informations d’identification d’Azure Active Directory (AD). Ainsi, les licences en ligne ne peuvent pas être évaluées. Pour plus d’informations, consultez [Distribuer des applications hors connexion](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Ajouter une application de Store** : sélectionnez **Ajouter une application de Store**, puis choisissez une application dans la liste.

    Aucune application n’est répertoriée ? En ajouter à l’aide de la procédure sous [Applications clientes](apps-add.md).

## <a name="multi-app-kiosks"></a>Applications multiples plein écran

Dans ce mode, les applications sont disponibles dans le menu Démarrer. Ce sont les seules applications que l’utilisateur peut ouvrir. Si une application a une dépendance sur une autre application, les deux doivent être incluses dans la liste des applications autorisées. Par exemple, Internet Explorer 64 bits ayant une dépendance sur Internet Explorer 32 bits, vous devez autoriser « C:\Program Files\internet explorer\iexplore.exe » et « C:\Program Files (x86)\Internet Explorer\iexplore.exe ». 

- **Sélectionner un mode kiosque** : choisissez **Kiosque multi-application**.

- **Cibler Windows 10 dans les appareils en mode S** :
  - **Oui** : Autorise les applications Store et les applications AUMID (à l’exception des applications Win32) dans le profil kiosque.
  - **Non** : autorise les applications Store, les applications Win32 et les applications AUMID dans le profil kiosque. Ce profil de kiosque n’est pas déployé sur des appareils en mode S.

- **Type d’ouverture de session utilisateur** : les applications que vous ajoutez s’exécutent comme le compte d’utilisateur que vous entrez. Les options disponibles sont les suivantes :

  - **Ouverture de session automatique (Windows 10 version 1803 et versions ultérieures)** : utilisez les bornes des environnements publics qui ne nécessitent pas de connexion de l’utilisateur, similaire à un compte invité. Ce paramètre utilise le [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Compte d'utilisateur local** : **Ajouter** le compte d'utilisateur local (à l’appareil). Le compte que vous entrez se connecte au kiosque.
  - **Utilisateur ou groupe Azure Active Directory (Windows 10 version 1803 et versions ultérieures)** : sélectionnez **Ajouter**, puis choisissez des utilisateurs ou des groupes Azure Active Directory dans la liste. Vous pouvez sélectionner plusieurs utilisateurs et groupes. Choisissez **Sélectionner** pour enregistrer vos changements.
  - **Visiteur HoloLens** : Le compte visiteur est un compte invité ne nécessitant pas d’informations d’identification de l’utilisateur ou d’authentification, comme décrit dans [Concepts du mode PC partagé](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Navigateur et applications** : ajoutez les applications à exécuter sur l’appareil kiosque. N’oubliez pas que vous pouvez ajouter plusieurs applications.

  - **Navigateurs**

    - **Ajouter Microsoft Edge** : Microsoft Edge est ajouté à la grille d’applications, et toutes les applications peuvent s’exécuter sur ce kiosque. Choisissez le **Type de mode kiosque Microsoft Edge** :

      - **Mode normal (version complète de Microsoft Edge)**  : exécute une version complète de Microsoft Edge avec toutes les fonctionnalités de navigation. L’état et les données utilisateur sont enregistrés entre les sessions.
      - **Navigation publique (InPrivate)**  : exécute une version multi-onglets de Microsoft Edge InPrivate avec une expérience adaptée aux appareils qui s’exécutent en mode plein écran.

      Pour plus d’informations sur ces options, consultez [Déployer le mode kiosque dans Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Ce paramètre active le navigateur Microsoft Edge sur l’appareil. Pour configurer des paramètres propres à Microsoft Edge, créez un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10** pour la plateforme > **Restrictions de l’appareil** >  **Navigateur Microsoft Edge**). [Navigateur Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser) liste et décrit les paramètres disponibles.

    - **Ajouter le navigateur du kiosque** : ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à déployer une application de navigateur web sur les appareils de type kiosque via des [Applications clientes](apps-add.md).

      entrez les paramètres suivants :

      - **URL de la page d’accueil par défaut** : entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur du kiosque. Par exemple, entrez `http://bing.com` ou `http://www.contoso.com`.

      - **Bouton Accueil** : **Afficher** ou **Masquer** le bouton Accueil du navigateur du kiosque. Par défaut, le bouton ne s’affiche pas.

      - **Boutons de navigation** : **Afficher** ou **Masquer** les boutons Suivant et Précédent. Par défaut, les boutons de navigation ne s’affichent pas.

      - **Bouton Terminer la session** : **Afficher** ou **Masquer** le bouton de fin de session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, etc.), puis ouvre l’URL par défaut. Par défaut, le bouton ne s’affiche pas.

      - **Actualiser le navigateur après la durée d’inactivité** : entrez la durée d’inactivité (1 à 1 440 minutes) avant le redémarrage du navigateur de kiosque dans un nouvel état. La durée d’inactivité est le nombre de minutes écoulées depuis la dernière interaction de l’utilisateur. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

      - **Sites web autorisés** : utilisez ce paramètre pour autoriser l’ouverture de sites web spécifiques. En d’autres termes, utilisez cette fonctionnalité pour restreindre ou empêcher des sites web sur l’appareil. Par exemple, vous pouvez autoriser l’ouverture de tous les sites web sur `contoso.com*`. Par défaut, tous les sites web sont autorisés.

        Pour autoriser des sites web spécifiques, chargez un fichier .csv qui inclut une liste des sites web autorisés. Si vous n’ajoutez pas de fichier .csv, tous les sites web sont autorisés.

      > [!NOTE]
      > Les kiosques Windows 10 avec ouverture de la ligne automatique activée à l’aide de Microsoft Kiosk Browser doivent utiliser une licence hors connexion de la Microsoft Store pour l’entreprise. Cette exigence est due au fait que l’ouverture de la chaîne automatique utilise un compte d’utilisateur local sans informations d’identification d’Azure Active Directory (AD). Ainsi, les licences en ligne ne peuvent pas être évaluées. Pour plus d’informations, consultez [Distribuer des applications hors connexion](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Applications**

    - **Ajouter une application de Store** : ajoutez une application de Microsoft Store pour Entreprises. Si vous n’avez aucune application répertoriée, vous pouvez obtenir des applications et [les ajouter à Intune](store-apps-windows.md). Par exemple, vous pouvez ajouter Kiosk Browser, Excel, OneNote et bien plus encore.

    - **Application Win32** : une application Win32 est une application de bureau traditionnelle, telle que Visual Studio Code ou Google Chrome. Entrez les propriétés suivantes :

      - **Nom de l’application** : requis. Entrez un nom pour l'application.
      - **Chemin d’accès local** : requis. Entrez le chemin d’accès au fichier exécutable, par exemple `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **Identifiant AUMID de l’application** : entrez l’ID AUMID de l’application Win32. Ce paramètre détermine la mise en page de démarrage de la mosaïque sur le bureau. Pour obtenir cet ID, consultez [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

    - **Ajouter par AUMID** : utilisez cette option pour ajouter des applications Windows de boîte de réception, telles que le bloc-notes ou la calculatrice. Entrez les propriétés suivantes :

      - **Nom de l’application** : requis. Entrez un nom pour l'application.
      - **Identifiant du modèle utilisateur de l’application (AUMID)**  : requis. Entrez l’identifiant AUMID de l’application Windows. Pour obtenir cet ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

    - **Démarrage automatique** : facultatif. Choisissez une application à lancer automatiquement quand l’utilisateur se connecte. Une seule application peut être lancée automatiquement.
    - **Taille de la mosaïque** : requise. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.

  > [!TIP]
  > Après avoir ajouté toutes les applications, vous pouvez modifier l’ordre d’affichage en cliquant sur les applications et en les faisant glisser dans la liste.  

- **Utiliser une autre mise en page de démarrage** : choisissez **Oui** pour entrer un fichier XML qui décrit comment les applications s’affichent dans le menu Démarrer, notamment l’ordre des applications. Utilisez cette option si vous avez besoin de davantage de personnalisation dans votre menu Démarrer. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fournit quelques conseils et un exemple de code XML.

- **Barre des tâches Windows** : choisissez d’**Afficher** ou de **Masquer** la barre des tâches. Par défaut, la barre des tâches ne s’affiche pas. Des icônes, telles que l’icône Wi-Fi, sont visibles, mais les paramètres ne sont pas modifiables par les utilisateurs finaux.

- **Autoriser l’accès au dossier Téléchargements** : choisissez **Oui** pour autoriser les utilisateurs à accéder au dossier Téléchargements dans l’Explorateur Windows. Par défaut, l’accès au dossier Téléchargements est désactivé. Cette fonctionnalité est couramment utilisée pour permettre aux utilisateurs finaux d’accéder aux éléments téléchargés à partir d’un navigateur.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils kiosque pour des appareils [Android](device-restrictions-android.md#kiosk), [Android Entreprise](device-restrictions-android-for-work.md#dedicated-device-settings) et [Windows Holographic for Business](kiosk-settings-holographic.md).
