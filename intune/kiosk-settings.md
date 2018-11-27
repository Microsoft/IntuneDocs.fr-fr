---
title: Paramètres kiosque pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez vos appareils Windows 10 (et versions ultérieures) en tant que kiosques mono-application et multi-application. Personnalisez le menu Démarrer et la barre des tâches, ajoutez des applications, et configurez un navigateur web. Configurez également des appareils Windows Holographic for Business en tant que kiosques multi-application dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 7552c9c1fa8e94560505a8971143886160cff6ce
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185950"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Paramètres kiosque pour Windows 10 (et versions ultérieures) dans Intune

Sur les appareils Windows 10, vous pouvez utiliser Intune pour exécuter ces appareils comme kiosque. Le kiosque peut exécuter une application ou de nombreuses applications. Vous pouvez également afficher et personnaliser un menu de démarrage, ajouter des applications différentes, y compris les applications Win32, ajouter une page d’accueil spécifique à un navigateur web et bien plus encore. 

Utilisez la procédure décrite dans cet article pour créer un kiosque mono-application ou multi-application dans Intune.

Intune prend en charge un profil de kiosque par appareil. Si vous avez besoin de plusieurs profils de kiosque sur un seul appareil, vous pouvez utiliser un [OMA-URI personnalisé](custom-settings-windows-10.md).

## <a name="kiosk-settings"></a>Paramètres kiosque

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

   - **Nom** : attribuez un nom descriptif au nouveau profil.
   - **Description :** entrez une description pour le profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : sélectionnez **Windows 10 et ultérieur**
   - **Type de profil** : sélectionnez **Kiosque (préversion)**

4. Sélectionnez un **mode kiosque**. **Mode kiosque** : identifie le type de mode kiosque pris en charge par la stratégie. Les options sont les suivantes :

    - **Non configuré** (par défaut) : La stratégie n’active pas de mode kiosque.
    - **Application unique, kiosque plein écran** : l’appareil s’exécute comme compte d’utilisateur unique et le verrouille sur une seule application Store. De cette façon, quand l’utilisateur se connecte, une application spécifique démarre. Ce mode empêche également l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
    - **Kiosque multi-application** : l’appareil exécute plusieurs applications Store, des applications Win32 ou des applications de boîte de réception Windows à l’aide de l’identifiant AUMID de l’application. Seules les applications que vous ajoutez sont disponibles sur l’appareil.

        L’avantage d’un kiosque multiapplication ou d’un appareil à usage fixe est que l’utilisateur accède uniquement aux applications dont il a besoin. Celles dont il n’a pas besoin sont retirées de sa vue.

## <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran
Lorsque vous choisissez le mode kiosque à application unique, entrez les paramètres suivants :

- **Type d’ouverture de session utilisateur** : les applications que vous ajoutez s’exécutent comme le compte d’utilisateur que vous entrez. Les options disponibles sont les suivantes :

  - **Ouverture de session automatique (Windows 10 version 1803 et versions ultérieures)**  : pour les kiosques dans des environnements publics qui ne nécessitent pas d’ouverture de session par l’utilisateur, similaire à un compte invité. Ce paramètre utilise le [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Compte d’utilisateur local** : entrez le compte d’utilisateur local (sur l’appareil). Le compte que vous entrez est utilisé pour la connexion au kiosque.

- **Type d’application** : sélectionnez **application Store**.

- **Application à exécuter en mode kiosque** : choisissez **Ajouter une application Store**, puis sélectionnez une application dans la liste.

    Aucune application n’est répertoriée ? En ajouter à l’aide de la procédure sous [Applications clientes](apps-add.md).

    Cliquez sur **OK** pour enregistrer vos modifications.

- **Paramètres de navigateur du kiosque** : ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à obtenir l’[application de navigateur kiosque](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) dans le Store, ajoutez-la à Intune en tant qu’[application cliente](apps-add.md), puis affectez l’application aux appareils du kiosque.

  entrez les paramètres suivants :

  - **URL de la page d’accueil par défaut** : entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur du kiosque. Par exemple, entrez `http://bing.com` ou `http://www.contoso.com`.

  - **Bouton Accueil** : **Afficher** ou **Masquer** le bouton Accueil du navigateur du kiosque. Par défaut, le bouton ne s’affiche pas.

  - **Boutons de navigation** : **Afficher** ou **Masquer** les boutons Suivant et Précédent. Par défaut, les boutons de navigation ne s’affichent pas.

  - **Bouton Terminer la session** : **Afficher** ou **Masquer** le bouton de fin de session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, etc.), puis ouvre l’URL par défaut. Par défaut, le bouton ne s’affiche pas.

  - **Actualiser le navigateur après la durée d’inactivité** : entrez la durée d’inactivité (1 à 1 440 minutes) avant le redémarrage du navigateur de kiosque dans un nouvel état. La durée d’inactivité est le nombre de minutes écoulées depuis la dernière interaction de l’utilisateur. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

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

- **Cibler Windows 10 dans les appareils en mode S** : choisissez **Oui** pour autoriser les applications Store et AUMID (excepté pour les applications Win32) dans le profil de kiosque. Choisissez **Non** pour autoriser les applications Store, les applications Win32 et les applications AUMID dans le profil de kiosque. Lorsque vous choisissez **Non**, ce profil de kiosque n’est pas déployé sur des appareils en mode S.

- **Type d’ouverture de session utilisateur** : les applications que vous ajoutez s’exécutent comme le compte d’utilisateur que vous entrez. Les options disponibles sont les suivantes :

  - **Ouverture de session automatique (Windows 10 version 1803 et versions ultérieures)**  : pour les kiosques dans des environnements publics qui ne nécessitent pas d’ouverture de session par l’utilisateur, similaire à un compte invité. Ce paramètre utilise le [CSP AssignedAccess](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Compte d'utilisateur local** : **Ajouter** le compte d'utilisateur local (à l’appareil). Le compte que vous entrez est utilisé pour la connexion au kiosque.
  - **Utilisateur Azure AD ou groupe (Windows 10 version 1803 et versions ultérieures)**  : sélectionnez **Ajouter** pour choisir des utilisateurs Azure AD ou des groupes dans la liste. Vous pouvez sélectionner plusieurs utilisateurs et groupes. Choisissez **Sélectionner** pour enregistrer vos changements.
  - **Visiteur HoloLens** : Le compte visiteur est un compte invité ne nécessitant pas d’informations d’identification de l’utilisateur ou d’authentification, comme décrit dans [Concepts du mode PC partagé](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applications** : ajoutez les applications à exécuter sur l’appareil kiosque. N’oubliez pas que vous pouvez ajouter plusieurs applications.

  - **Ajouter une application de Store** : ajoutez une application de Microsoft Store pour Entreprises. Si vous n’avez aucune application répertoriée, vous pouvez obtenir des applications et [les ajouter à Intune](store-apps-windows.md). Par exemple, vous pouvez ajouter Kiosk Browser, Excel, OneNote et bien plus encore.

  - **Application Win32** : une application Win32 est une application de bureau traditionnelle, telle que Visual Studio Code ou Google Chrome. Entrez les propriétés suivantes :

    - **Nom de l’application** : requis. Entrez un nom pour l'application.
    - **Chemin d’accès local** : requis. Entrez le chemin d’accès au fichier exécutable, par exemple `C:\Program Files (x86)\Microsoft VS Code\Code.exe` ou `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **Identifiant AUMID de l’application** : entrez l’ID AUMID de l’application Win32. Ce paramètre détermine la mise en page de démarrage de la mosaïque sur le bureau. Pour obtenir cet ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
    - **Taille de la mosaïque** : requise. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.
  
  - **Ajouter par AUMID** : utilisez cette option pour ajouter des applications Windows de boîte de réception, telles que le bloc-notes ou la calculatrice. Entrez les propriétés suivantes : 

    - **Nom de l’application** : requis. Entrez un nom pour l'application.
    - **Identifiant du modèle utilisateur de l’application (AUMID)**  : requis. Entrez l’identifiant AUMID de l’application Windows. Pour obtenir cet ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Taille de la mosaïque** : requise. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.

  > [!TIP]
  > Après avoir ajouté toutes les applications, vous pouvez modifier l’ordre d’affichage en cliquant sur les applications et en les faisant glisser dans la liste.  

  Cliquez sur **OK** pour enregistrer vos modifications.

- **Paramètres de navigateur du kiosque** : ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à déployer une application de navigateur web sur les appareils de type kiosque via des [Applications clientes](apps-add.md).

  entrez les paramètres suivants :

  - **URL de la page d’accueil par défaut** : entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur du kiosque. Par exemple, entrez `http://bing.com` ou `http://www.contoso.com`.

  - **Bouton Accueil** : **Afficher** ou **Masquer** le bouton Accueil du navigateur du kiosque. Par défaut, le bouton ne s’affiche pas.

  - **Boutons de navigation** : **Afficher** ou **Masquer** les boutons Suivant et Précédent. Par défaut, les boutons de navigation ne s’affichent pas.

  - **Bouton Terminer la session** : **Afficher** ou **Masquer** le bouton de fin de session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, etc.), puis ouvre l’URL par défaut. Par défaut, le bouton ne s’affiche pas.

  - **Actualiser le navigateur après la durée d’inactivité** : entrez la durée d’inactivité (1 à 1 440 minutes) avant le redémarrage du navigateur de kiosque dans un nouvel état. La durée d’inactivité est le nombre de minutes écoulées depuis la dernière interaction de l’utilisateur. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

  - **Sites web autorisés** : utilisez ce paramètre pour autoriser l’ouverture de sites web spécifiques. En d’autres termes, utilisez cette fonctionnalité pour restreindre ou empêcher des sites web sur l’appareil. Par exemple, vous pouvez autoriser l’ouverture de tous les sites web sur `contoso.com*`. Par défaut, tous les sites web sont autorisés.

    Pour autoriser des sites web spécifiques, chargez un fichier .csv qui inclut une liste des sites web autorisés. Si vous n’ajoutez pas de fichier .csv, tous les sites web sont autorisés.

  Cliquez sur **OK** pour enregistrer vos modifications.

- **Utiliser une autre mise en page de démarrage** : choisissez **Oui** pour entrer un fichier XML qui décrit comment les applications s’affichent dans le menu Démarrer, notamment l’ordre des applications. Utilisez cette option si vous avez besoin de davantage de personnalisation dans votre menu Démarrer. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fournit quelques conseils et un exemple de code XML.

- **Barre des tâches Windows** : choisissez d’**Afficher** ou de **Masquer** la barre des tâches. Par défaut, la barre des tâches ne s’affiche pas.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Vous pouvez configurer les appareils Windows Holographic for Business pour qu’ils s’exécutent en mode kiosque mono-application ou en mode kiosque multi-application. Certaines fonctionnalités ne sont pas prises en charge sur Windows Holographic for Business.

#### <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran
Lorsque vous choisissez le mode kiosque à application unique, entrez les paramètres suivants :

- **Type d’ouverture de session d’utilisateur** : sélectionnez **Compte d’utilisateur local** pour entrer le compte d’utilisateur local (sur l’appareil) ou un compte Microsoft Account (MSA) associé à l’application kiosque. Les types de comptes d’utilisateur **Ouverture de session automatique** ne sont pas pris en charge sur Windows Holographic for Business.

- **Type d’application** : sélectionnez **application Store**.

- **Application à exécuter en mode kiosque** : choisissez **Ajouter une application Store**, puis sélectionnez une application dans la liste.

    Aucune application n’est répertoriée ? En ajouter à l’aide de la procédure sous [Applications clientes](apps-add.md).

    Cliquez sur **OK** pour enregistrer vos modifications.

#### <a name="multi-app-kiosks"></a>Applications multiples plein écran
Dans ce mode, les applications sont disponibles dans le menu Démarrer. Ce sont les seules applications que l’utilisateur peut ouvrir. Lorsque vous choisissez le mode kiosque multi-application, entrez les paramètres suivants :

- **Cibler Windows 10 dans les appareils en mode S** : choisissez **Non**. Le mode S n’est pas pris en charge sur Windows Holographic for Business.

- **Type d’ouverture de session d’utilisateur** : ajoutez un ou plusieurs comptes d’utilisateurs qui peuvent utiliser les applications que vous ajoutez. Les options disponibles sont les suivantes : 

  - **Ouverture de session automatique** : pas prise en charge sur Windows Holographic for Business.
  - **Comptes d'utilisateurs locaux** : **Ajouter** le compte d'utilisateur local (à l’appareil). Le compte que vous entrez est utilisé pour la connexion au kiosque.
  - **Utilisateur ou groupe Azure AD (Windows 10, version 1803 et versions ultérieures)**  : nécessite des informations d’identification de l’utilisateur pour se connecter à l’appareil. Sélectionnez **Ajouter** pour choisir les utilisateurs ou groupes Azure AD dans la liste. Vous pouvez sélectionner plusieurs utilisateurs et groupes. Choisissez **Sélectionner** pour enregistrer vos changements.
  - **Visiteur HoloLens** : Le compte visiteur est un compte invité ne nécessitant pas d’informations d’identification de l’utilisateur ou d’authentification, comme décrit dans [Concepts du mode PC partagé](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Applications** : ajoutez les applications à exécuter sur l’appareil kiosque. N’oubliez pas que vous pouvez ajouter plusieurs applications.

  - **Ajouter des applications Store** : sélectionnez une application existante que vous avez ajoutée avec [Applications clientes](apps-add.md). Si vous n’avez aucune application répertoriée, vous pouvez obtenir des applications et [les ajouter à Intune](store-apps-windows.md).
  - **Ajouter une application Win32** : pas pris en charge sur Windows Holographic for Business.
  - **Ajouter par AUMID** : utilisez cette option pour ajouter des applications Windows de boîte de réception. Entrez les propriétés suivantes : 

    - **Nom de l’application** : requis. Entrez un nom pour l'application.
    - **Identifiant du modèle utilisateur de l’application (AUMID)**  : requis. Entrez l’identifiant AUMID de l’application Windows. Pour obtenir cet ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Taille de la mosaïque** : requise. Choisissez la taille de la mosaïque application : petite, moyenne ou grande.

- **Paramètres du navigateur de kiosque** : pas pris en charge sur Windows Holographic for Business.

- **Utiliser une autre mise en page de démarrage** : choisissez **Oui** pour entrer un fichier XML qui décrit comment les applications s’affichent dans le menu Démarrer, notamment l’ordre des applications. Utilisez cette option si vous avez besoin de davantage de personnalisation dans votre menu Démarrer. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) fournit quelques conseils et inclut un fichier XML spécifique pour les appareils Windows Holographic for Business.

- **Barre des tâches Windows** : pas prise en charge sur Windows Holographic for Business.



## <a name="next-steps"></a>Étapes suivantes
[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
