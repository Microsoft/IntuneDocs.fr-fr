---
title: Paramètres kiosque pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez vos appareils Windows 10 (et versions ultérieures) en tant que kiosques mono-application et multi-application. Personnalisez le menu Démarrer et la barre des tâches, ajoutez des applications, et configurez un navigateur web. Configurez également des appareils Windows Holographic for Business en tant que kiosques multi-application dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9dd7608981da1454c1f3be29eb6ff40a5d7f3394
ms.sourcegitcommit: 23adbc50191f68c4b66ea845a044da19c659ac84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45562865"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Paramètres kiosque pour Windows 10 (et versions ultérieures) dans Intune

Les profils kiosque servent à configurer les appareils Windows 10 pour exécuter une ou plusieurs applications. Quand vous créez un profil kiosque, vous choisissez également si un menu de démarrage doit être affiché, si un navigateur web est installé, et bien plus encore.

## <a name="kiosk-settings"></a>Paramètres kiosque

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

   - **Nom** : attribuez un nom descriptif au nouveau profil.
   - **Description :** entrez une description pour le profil. Ceci est facultatif, mais recommandé.
   - **Plateforme** : sélectionnez **Windows 10 et ultérieur**
   - **Type de profil** : sélectionnez **Kiosque (préversion)**
   
4. Sélectionnez **Kiosque** > **Ajouter**.
5. Entrez un **Nom de configuration kiosque** pour votre kiosque. Ce nom identifie un groupe d’applications, la disposition de ces applications dans le menu de démarrage et les utilisateurs affectés à cette configuration kiosque.
6. Sélectionnez le **mode kiosque**. **Mode kiosque** : identifie le type de mode kiosque pris en charge par la stratégie. Les options sont les suivantes :

    - **Non configuré** (par défaut) : La stratégie n’active pas de mode kiosque.
    - **Kiosque avec une seule application en plein écran**: Le profil permet à l’appareil de s’exécuter comme un seul compte d’utilisateur et le verrouille sur une seule application de plateforme Windows universelle (UWP). De cette façon, quand l’utilisateur se connecte, une application spécifique démarre. Ce mode empêche également l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
    - **Kiosk multiapplication** : Le profil permet à l’appareil d’exécuter plusieurs applications de plateforme Windows universelle (UWP) ou d’applications Win32. Vous pouvez aussi affecter différentes applications à différents comptes d’utilisateur. Seules les applications que vous ajoutez sont disponibles pour l’utilisateur. L’avantage d’un kiosque multiapplication ou d’un appareil à usage fixe est que l’utilisateur accède uniquement aux applications dont il a besoin. Celles dont il n’a pas besoin sont retirées de sa vue.

#### <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran
entrez les paramètres suivants :

- **Identificateur d’application de plateforme Windows universelle (UWP)** : Entrez **l’ID de modèle utilisateur d’application (AUMID)** de l’application kiosque. Sinon, sélectionnez une application gérée existante que vous avez ajoutée via [Applications clientes](apps-add.md).

    Consultez [Rechercher l’ID de modèle utilisateur d’application d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

- **Type de compte d’utilisateur** : Options disponibles :

  - **Ouverture de session automatique** : Pour les kiosques dans des environnements publics où l’ouverture de session automatique est activée, un utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Pour configurer un compte Azure Active Directory (AD) pour le mode plein écran, utilisez le format `AzureAD\user@contoso.com`.
  - **Compte d’utilisateur local** : Entrez le compte d’utilisateur local (pour l’appareil) ou la connexion au compte Azure Active Directory associé à l’application kiosque. Pour les comptes liés à des domaines Azure AD, entrez le compte en utilisant le format `domain\username@tenant.org`.

#### <a name="multi-app-kiosks"></a>Applications multiples plein écran
Dans ce mode, les applications sont disponibles dans le menu Démarrer. Ce sont les seules applications que l’utilisateur peut ouvrir. 

Les [Applications multiples plein écran](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) utilisent une configuration plein écran qui répertorie les applications autorisées et d’autres paramètres.

entrez les paramètres suivants :

- **Ajouter une application Win32** : Une application Win32 est une application de bureau traditionnelle. Entrez le **Nom d’application** et **l’Identificateur**. **L’Identificateur** est le nom du chemin complet de l’exécutable sur l’appareil.
- [Ajouter des applications gérées](apps-add.md) : sélectionnez une application gérée existante que vous avez ajoutée via **Applications clientes dans Intune**.
- **Ajouter une application par AUMID** : Entrez [l’AUMID de l’application](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (applications UWP).
- **Barre des tâches** : choisissez de montrer (**Activer**) la barre des tâches ou de la garder masquée (**Non configurée**) sur l’appareil plein écran.
- **Disposition du menu Démarrer** : Entrez un fichier XML qui décrit comment les applications apparaissent dans le menu Démarrer, notamment l’ordre des applications. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fournit quelques conseils et un exemple de code XML.

  [Créer une borne Windows10 qui exécute plusieurs applications](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) fournit plus de détails sur l’utilisation et la création de fichiers XML.

- **Type de compte d’utilisateur** : Ajoutez un ou plusieurs comptes d’utilisateurs qui peuvent utiliser les applications que vous ajoutez. Quand le compte se connecte, seules les applications définies dans la configuration sont disponibles. Le compte peut être local sur l’appareil ou il peut s’agir d’une connexion de compte Azure AD associée à l’application kiosque.

    Pour les kiosques dans des environnements publics où l’ouverture de session automatique est activée, un type d’utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Pour configurer un compte Azure Active Directory (AD) pour le mode plein écran, utilisez le format `domain\user@tenant.com`.

## <a name="kiosk-web-browser-settings"></a>Paramètres du navigateur web kiosque

Ces paramètres contrôlent une application de navigateur web sur le kiosque. Veillez à déployer une application de navigateur web sur les appareils de type borne via [Applications clientes](apps-add.md).

1. entrez les paramètres suivants :

    - **URL de la page d’accueil par défaut** : Entrez l’URL par défaut affichée à l’ouverture ou au redémarrage du navigateur kiosque.

    - **Afficher le bouton Accueil** : Affichez (**Autoriser**) ou masquez (**Non configuré**) le bouton Accueil du navigateur kiosque. Par défaut, le bouton est Non configuré.

    - **Afficher les boutons de navigation** : Affichez (**Autoriser**) ou masquez (**Non configuré**) les boutons Suivant et Précédent. Par défaut, les boutons de navigation sont « Non configuré ».

    - **Afficher le Bouton Terminer la session** : Affichez (**Autoriser**) ou masquez (**Non configuré**) le bouton Terminer la session. Quand ce bouton est affiché et que l’utilisateur le sélectionne, l’application l’invite à mettre fin à la session. Après confirmation, le navigateur efface toutes les données de navigation (cookies, cache, et ainsi de suite) et retourne à l’URL par défaut. Par défaut, le bouton est Non configuré. 

    - **Actualiser le navigateur quand l’utilisateur dépasse la limite du délai d’inactivité** : Entrez la durée d’inactivité de session en minutes avant que le redémarrage du navigateur kiosque dans un nouvel état. La valeur est un entier compris entre 1 et 1440 minutes. Par défaut, la valeur est vide, ce qui signifie qu’il n’y a pas d’expiration du délai d’inactivité.

    - **Sites web bloqués** : Liste des URL de site web bloqué (avec prise en charge des caractères génériques). Utilisez ce paramètre pour empêcher le navigateur d’ouvrir des sites spécifiques. Vous pouvez aussi **Importer** un fichier .csv contenant une liste. Sinon, créez un fichier .csv (**Exporter**) qui contient les sites que vous ajoutez.

    - **Exceptions de site web** : Liste d’exceptions pour les URL de site web bloqué (avec prise en charge des caractères génériques). Utilisez ce paramètre pour autoriser le navigateur à ouvrir des sites spécifiques. Ces exceptions sont un sous-ensemble des URL bloquées. Si une URL est dans la liste des sites web bloqués et dans la liste des exceptions de site web, l’exception est prioritaire.

    Vous pouvez aussi **Importer** un fichier .csv contenant une liste. Sinon, créez un fichier .csv (**Exporter**) qui contient les sites que vous ajoutez.

2. Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Vous pouvez configurer les appareils Windows Holographic for Business pour qu’ils s’exécutent en mode kiosque mono-application ou en mode kiosque multi-application. 

#### <a name="single-full-screen-app-kiosks"></a>Kiosques avec une seule application en plein écran
entrez les paramètres suivants :

- **Identificateur d’application de plateforme Windows universelle (UWP)** : Entrez **l’ID de modèle utilisateur d’application (AUMID)** de l’application kiosque. Sinon, sélectionnez une application gérée existante que vous avez ajoutée à l’aide de [Mobile Apps](apps-add.md).

    Pour obtenir l’ID, consultez [Rechercher l’identifiant AUMID d’une application installée](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

- **Type de compte d’utilisateur** : Sélectionnez **Compte d’utilisateur local** pour entrer le compte d’utilisateur local (sur l’appareil) ou une connexion de compte Microsoft Account (MSA) associée à l’application kiosque. Les types de comptes d’utilisateur **Ouverture de session automatique** ne sont pas pris en charge sur Windows Holographic for Business.

#### <a name="multi-app-kiosks"></a>Applications multiples plein écran
Dans ce mode, les applications sont disponibles dans le menu Démarrer. Ce sont les seules applications que l’utilisateur peut ouvrir.

entrez les paramètres suivants :

- [Ajouter des applications gérées](apps-add.md) : sélectionnez une application gérée existante que vous avez ajoutée via **Applications clientes dans Intune**.
- **Ajouter une application par AUMID** : Entrez [l’AUMID de l’application](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (applications UWP).
- **Disposition du menu Démarrer** : Entrez un fichier XML qui décrit comment les applications apparaissent dans le menu Démarrer, notamment l’ordre des applications. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) fournit quelques conseils et inclut un fichier XML spécifique pour les appareils Windows Holographic for Business.
- **Type de compte d’utilisateur** : Ajoutez un ou plusieurs comptes d’utilisateurs qui peuvent utiliser les applications que vous ajoutez. Les options prises en charge sont les suivantes : 
  - **Visiteur HoloLens** : Le compte visiteur est un compte invité ne nécessitant pas d’informations d’identification de l’utilisateur ou d’authentification, comme décrit dans [Concepts du mode PC partagé](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
  - **Utilisateurs Azure AD** : nécessite des informations d’identification de l’utilisateur pour se connecter à l’appareil. Utilisez le format `domain\user@tenant.com`.
  - **Comptes d’utilisateur locaux** : nécessite des informations d’identification de l’utilisateur pour se connecter à l’appareil. 

Quand le compte se connecte, seules les applications définies dans la configuration sont disponibles.

## <a name="next-steps"></a>Étapes suivantes
[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
