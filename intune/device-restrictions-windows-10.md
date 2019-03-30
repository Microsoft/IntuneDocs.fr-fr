---
title: Paramètres de restriction des appareils pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres et leur description pour la création de restrictions d’appareil sur les appareils Windows 10 et versions ultérieures. Utilisez ces paramètres dans un profil de configuration pour contrôler les captures d’écran, les exigences de mot de passe, les paramètres Kiosk, les applications dans le magasin, le navigateur Edge, Windows Defender, l’accès au cloud, le menu Démarrer et autres dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8190365ad2b50dfa7369b8899e8984b6a52f1cba
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566743"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités dans Intune

Cet article liste et décrit tous les paramètres que vous pouvez contrôler sur les appareils Windows 10 et versions ultérieures. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, pour définir des règles de mot de passe, pour personnaliser l’écran de verrouillage, pour utiliser Windows Defender, et bien plus encore.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur les appareils Windows 10.

> [!Note]
> Toutes les options ne sont pas disponibles dans toutes les éditions de Windows.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>App Store

- **App store (mobile uniquement)** : active ou bloque l’utilisation de l’App Store sur les appareils Windows 10 Mobile.
- **Mettre à jour automatiquement les applications du Windows store** : permet aux applications installées à partir du Microsoft Store d’être automatiquement mises à jour.
- **Installation d’applications approuvées** : permet de charger indépendamment les applications signées avec un certificat approuvé.
- **Déverrouillage de développement** : autorise les paramètres de développement Windows, par exemple pour autoriser l’utilisateur à modifier des applications qui ont été chargées indépendamment.
- **Données d'application utilisateur partagées** : permet aux applications de partager des données entre différents utilisateurs sur le même appareil.
- **Utiliser uniquement un store privé** : activez cette option pour autoriser les utilisateurs à télécharger uniquement des applications à partir de votre Store privé.
- **Lancement des applications du Windows Store** : permet de désactiver toutes les applications qui ont été préalablement installées sur l’appareil ou qui ont été téléchargées à partir du Microsoft Store.
- **Installer des données d'application sur le volume système** : empêche les applications de stocker des données sur le volume système de l’appareil.
- **Installer des données d'application sur le lecteur système** : empêche les applications de stocker des données sur le lecteur système de l’appareil.
- **Jeux DVR (Desktop uniquement)** : détermine si l’enregistrement et la diffusion des jeux sont autorisés ou non.
- **Applications du Store uniquement** : détermine si les utilisateurs peuvent installer des applications à partir d’emplacements autres que l’App Store.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

- **Canal de données mobiles** : empêche les utilisateurs d’utiliser des données, par exemple de naviguer sur le web, quand ils sont connectés à un réseau cellulaire. 
- **Itinérance des données** : autorise l’itinérance entre réseaux lors de l’accès aux données.
- **VPN sur le réseau de téléphonie mobile** : détermine si l’appareil peut accéder aux connexions VPN quand il est connecté à un réseau cellulaire.
- **Itinérance VPN sur le réseau de téléphonie mobile** : détermine si l’appareil peut accéder aux connexions VPN quand il est en itinérance sur un réseau cellulaire.
- **Bluetooth** : contrôle si l’utilisateur peut activer et configurer la fonction Bluetooth sur l’appareil.
- **Détectabilité de Bluetooth** : permet à cet appareil d’être découvert par d’autres appareils Bluetooth.
- **Précouplage Bluetooth** : permet de configurer des appareils Bluetooth spécifiques pour qu’ils soient couplés automatiquement à un appareil hôte.
- **Publicité Bluetooth** : permet à l’appareil de recevoir des publications via Bluetooth.
- **Service d’appareils connectés** : permet de choisir s’il faut autoriser le service d’appareils connectés, qui active la découverte et la connexion à d’autres appareils Bluetooth.
- **NFC** : permet à l’utilisateur d’activer et de configurer les fonctionnalités NFC (Near Field Communications) sur l’appareil.
- **Wi-Fi** : permet à l’utilisateur d’activer et de configurer le Wi-Fi sur l’appareil (Windows 10 Mobile uniquement).
- **Se connecter automatiquement aux points d'accès Wi-Fi** : permet à l’appareil de se connecter automatiquement aux points d’accès Wi-Fi gratuits et d’accepter automatiquement les termes et conditions de la connexion.
- **Configuration manuelle du Wi-Fi** : détermine si les utilisateurs peuvent configurer leurs propres connexions Wi-Fi ou s’ils peuvent uniquement utiliser les connexions configurées par un profil Wi-Fi (Windows 10 Mobile uniquement).
- **Intervalle de recherche de Wi-Fi** : spécifie la fréquence à laquelle les appareils recherchent des réseaux Wi-Fi. Spécifiez une valeur comprise entre 1 (plus fréquent) et 500 (moins fréquent).
- **Services Bluetooth autorisés** : spécifie (sous forme de chaînes hexadécimales) une liste de services et de profils Bluetooth autorisés.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Compte Microsoft** : permet à l’utilisateur d’associer un compte Microsoft à l’appareil.
- **Compte non-Microsoft** : permet à l’utilisateur d’ajouter des comptes de messagerie à l’appareil qui ne sont pas associés à un compte Microsoft.
- **Synchronisation des paramètres du compte Microsoft** : permet aux paramètres d’appareil et d’application associés à un compte Microsoft de se synchroniser entre les appareils.
- **Assistant de connexion de compte Microsoft** : choisissez **Désactiver** pour empêcher les utilisateurs finaux de contrôler le service Assistant de connexion de compte Microsoft (wlidsvc), par exemple l’arrêt ou le démarrage manuel du service. Lorsqu’il est défini sur **Pas configuré**, le service NT wlidsvc utilise le système d’exploitation (SE) par défaut, ce qui peut permettre aux utilisateurs finaux de démarrer et d’arrêter le service. Ce service est utilisé par le système d’exploitation pour permettre aux utilisateurs de se connecter à leur compte Microsoft.

## <a name="cloud-printer"></a>Imprimante cloud

- **URL de découverte d’imprimantes** : entrez l’URL de recherche des imprimantes cloud.
- **URL d’autorisation d’accès à l’imprimante** : entrez l’URL du point de terminaison d’authentification pour obtenir des jetons OAuth. Par exemple, entrez quelque chose du genre `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID de l’application cliente native Azure** : entrez le GUID identifiant l’application cliente autorisée à obtenir des jetons OAuth à partir d’OAuthAuthority.
- **URI de ressource du service d’impression** : entrez l’URI de ressource OAuth pour le service d’impression configuré dans le portail Azure. Par exemple, entrez quelque chose du genre `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Nombre maximal d’imprimantes à interroger (Mobile uniquement)** : entrez le nombre maximal d’imprimantes à interroger. Par exemple, entrez `10`.
- **URI de ressource du service de découverte d’imprimantes** : entrez l’URI de ressource OAuth pour le service de découverte d’imprimantes configuré dans le portail Azure. Par exemple, entrez quelque chose du genre `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Après avoir configuré une [impression cloud hybride Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), vous pouvez configurer ces paramètres et les déployer sur des appareils Windows.

## <a name="control-panel-and-settings"></a>Panneau de configuration et paramètres

- **Application Paramètres** : bloque l’accès à l’application Paramètres de Windows.
  - **Système** : bloque l’accès à la zone système de l’application Paramètres.
    - **Modification des paramètres d'alimentation et de veille (poste de travail uniquement)** : empêche l’utilisateur final de modifier les paramètres d’alimentation et de veille sur l’appareil.
  - **Appareils** : bloque l’accès à la zone des appareils de l’application Paramètres.
  - **Réseau Internet** : bloque l’accès à la zone réseau et internet de l’application Paramètres.
  - **Personnalisation** : bloque l’accès à la zone de personnalisation de l’application Paramètres.
  - **Comptes** : bloque l’accès à la zone des comptes de l’application Paramètres.
  - **Heure et langue** : bloque l’accès à la zone heure et langue de l’application Paramètres.
    - **Modification de l’heure système** : empêche l’utilisateur final de modifier la date et l’heure de l’appareil.
    - **Modification des paramètres régionaux (Desktop uniquement)** : empêche l’utilisateur final de modifier les paramètres régionaux sur l’appareil.
    - **Modification des paramètres de langue (poste de travail uniquement)** : empêche l’utilisateur final de modifier les paramètres linguistiques sur l’appareil.
  - **Jeux** : bloque l’accès à l’application Jeux dans Paramètres.
  - **Options d’ergonomie** : bloque l’accès à la zone d’options d’ergonomie de l’application Paramètres.
  - **Confidentialité** : bloque l’accès à la zone de confidentialité de l’application Paramètres.
  - **Mise à jour et sécurité** : bloque l’accès à la zone des mises à jour et de la sécurité dans l’application des paramètres.

## <a name="display"></a>Afficher

- **Activer la mise à l'échelle GDI pour des applications**
- **Désactiver la mise à l'échelle GDI pour des applications**

  La mise à l'échelle DPI GDI permet aux applications sans prise en charge DPI de bénéficier d'une prise en charge DPI par moniteur. Entrez les applications héritées dont la mise à l'échelle DPI GDI a été activée. Si la mise à l'échelle DPI GDI est configurée pour s'activer et se désactiver sur une application, la mise à l'échelle est désactivée pour l'application.

## <a name="general"></a>Général

- **Capture d’écran (mobile uniquement)** : autorise l’utilisateur à capturer le contenu de l’écran d’appareil en tant qu’image.
- **Copier et coller (mobile uniquement)** : autorise les actions copier-coller entre les applications sur l’appareil.
- **Inscription manuelle** : permet à l’utilisateur de supprimer manuellement le compte d’espace de travail de l’appareil.
  - Ce paramètre de stratégie n’est pas appliqué si l’ordinateur est joint à Azure AD et que l’inscription automatique est activée. 
  - Ce paramètre de stratégie ne s’applique pas aux ordinateurs Windows 10 Famille.
- **Installation manuelle du certificat racine (mobile uniquement)** : empêche l’utilisateur d’installer manuellement les certificats racines et les certificats CAP intermédiaires.

- **Appareil photo** : autorise ou bloque l’utilisation de l’appareil photo sur l’appareil.
- **Synchronisation des fichiers OneDrive** : empêche l’appareil de synchroniser des fichiers avec OneDrive.
- **Stockage amovible** : spécifie si des appareils de stockage externe comme une carte SD peuvent être utilisés avec l’appareil.
- **Géolocalisation** : spécifie si l’appareil peut utiliser les informations des services d’emplacement.
- **Partage Internet** : autorise l’utilisation du partage de connexion Internet sur l’appareil.
- **Réinitialisation du téléphone** : détermine si l’utilisateur peut réinitialiser son appareil.
- **Connexion USB (mobile uniquement)** : détermine si les appareils peuvent accéder à des appareils de stockage externe par le biais d’une connexion USB.
- **Mode antivol (mobile uniquement)** : détermine si le mode antivol Windows est activé.
- **Cortana** : active ou désactive l’assistant vocal Cortana.
- **Enregistrement vocal (mobile uniquement)** : autorise ou bloque l’utilisation de l’enregistreur vocal de l’appareil.
- **Modification du nom de l’appareil** : empêche l’utilisateur final de modifier le nom de l’appareil (Windows 10 Mobile uniquement).
- **Ajouter des packages de configuration** : bloque l’agent de configuration du runtime qui installe les packages de configuration.
- **Supprimer les packages de configuration** : bloque l’agent de configuration du runtime qui supprime les packages de configuration.
- **Découverte d’appareil** : empêche un appareil d’être détecté par d’autres appareils.
- **Sélecteur de tâches (mobile uniquement)** : bloque le sélecteur de tâches sur l’appareil.
- **Boîte de dialogue d’erreur de carte SIM (mobile uniquement)** : empêche un message d’erreur de s’afficher sur l’appareil si aucune carte SIM n’est détectée.
- **Espace de travail Windows Ink** : empêche les utilisateurs d’accéder à l’espace de travail Windows Ink. **Non configuré** : l’espace de travail Windows Ink est activé et l’utilisateur est autorisé à l’utiliser au-dessus de l’écran de verrouillage.
- **Redéploiement automatique** : permet aux utilisateurs avec des droits d’administration de supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **Ctrl+Win+R** sur l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion.
- **Demander aux utilisateurs de se connecter au réseau pendant la configuration de l’appareil (Windows Insider uniquement)** : choisissez **Exiger** pour que l’appareil se connecte à un réseau avant de passer à la page Réseau durant la configuration de Windows 10. Tant que cette fonctionnalité est en préversion, vous avez besoin de Windows Insider build 1809 ou ultérieure pour utiliser ce paramètre.
- **Accès direct à la mémoire** : **Bloquer** empêche l’accès direct à la mémoire (DMA) pour tous les ports en aval PCI enfichables à chaud tant qu’un utilisateur ne se connecte pas à Windows. **Activé** (valeur par défaut) autorise l’accès à DMA, même lorsqu’un utilisateur n’est pas connecté.

  CSP : [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Mettre fin aux processus de Gestionnaire des tâches**: ce paramètre détermine si les utilisateurs non-administrateurs peuvent utiliser des Gestionnaire des tâches pour mettre fin aux tâches. L’option **Empêcher** empêche les utilisateurs standard (non-administrateurs) d’utiliser le Gestionnaire des tâches pour terminer un processus ou une tâche sur l’appareil. L’option **Non configuré** (par défaut) permet aux utilisateurs standard d’arrêter un processus ou une tâche à l’aide du Gestionnaire des tâches.


## <a name="locked-screen-experience"></a>Expérience d’écran de verrouillage

- **Notifications du centre de notifications (mobile uniquement)** : active les notifications du Centre de notifications sur l’écran de verrouillage de l’appareil (Windows 10 Mobile uniquement).
- **URL de l’image de l’écran verrouillé (Desktop uniquement)** : entrer l’URL d’une image au format JPEG qui est utilisée comme papier peint de l’écran de verrouillage Windows. Ce paramètre verrouille l’image. L’image ne peut pas être modifiée par la suite.
- **Délai d’expiration de l’écran configurable par l’utilisateur (mobile uniquement)** : permet aux utilisateurs de configurer la durée 
- **Cortana sur écran verrouillé (poste de travail uniquement)** : ne pas autoriser l’utilisateur à interagir avec Cortana quand l’appareil est sur l’écran de verrouillage (Windows 10 Desktop uniquement).
- **Notifications toast sur écran verrouillé** : bloquer l’affichage des messages d’alerte sur l’écran de verrouillage de l’appareil.
- **Délai d’expiration de l’écran (mobile uniquement)** : spécifie la durée (en secondes) au bout de laquelle l’écran s’éteint après le verrouillage.

## <a name="messaging"></a>Messagerie

- **Synchronisation des messages (mobile uniquement)** : désactiver Messages sur tous les appareils et sauvegarder/restaurer les SMS.
- **MMS (mobile uniquement)** : désactiver la fonctionnalité d'envoi/de réception de MMS sur l'appareil.
- **RCS (mobile uniquement)** : désactiver la fonctionnalité d'envoi/de réception de RCS (Rich Communication Services) sur l'appareil.

## <a name="microsoft-edge-browser"></a>Navigateur Microsoft Edge

### <a name="use-microsoft-edge-kiosk-mode"></a>Utiliser le mode plein écran Microsoft Edge

Les paramètres disponibles varient selon que vous choisissez. Les options disponibles sont les suivantes :

- **Ne** (valeur par défaut) : Microsoft Edge n’est pas en cours d’exécution en mode plein écran. Tous les paramètres Microsoft Edge sont disponibles pour vous permettre de modifier et de configurer.
- **Signalisation numérique/Interactive (application unique plein écran)**: paramètres Edge de filtres qui s’appliquent pour le mode de plein écran Edge de signalisation numérique/Interactive pour une utilisation uniquement sur les bornes d’application unique de Windows 10. Choisissez ce paramètre pour ouvrir une URL en plein écran et afficher uniquement le contenu sur ce site Web. [Configurer des signes numériques](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fournit des informations sur cette fonctionnalité.
- **Publique la navigation inPrivate (application unique plein écran)**: paramètres Edge de filtres qui s’appliquent à InPrivate publique navigation Edge mode plein écran pour une utilisation sur les bornes d’application unique de Windows 10. Exécute une version de l’onglet multi de Microsoft Edge.
- **Mode normal (kiosque multi-application)**: paramètres Edge de filtres qui s’appliquent pour le mode plein écran du bord Normal. Exécute une version complète de Microsoft Edge avec toutes les fonctionnalités de navigation.
- **Navigation au public (kiosque multi-application)**: paramètres Edge de filtres qui s’appliquent à la consultation publique sur un kiosque multi-application de Windows 10.  Exécute une version de l’onglet multi de InPrivate de Microsoft Edge.

> [!TIP]
> Pour plus d’informations sur les opérations de ces options, consultez [types de configuration de mode plein écran Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Ce profil de restrictions d’appareil est directement lié au profil plein écran vous créez à l’aide de la [paramètres de plein écran Windows](kiosk-settings-windows.md). Pour récapituler :

1. Créer le [paramètres de plein écran Windows](kiosk-settings-windows.md) profil à exécuter l’appareil en mode plein écran. Sélectionnez Microsoft Edge en tant que l’application et définir le Mode plein écran de bord dans le profil de plein écran.
2. Créez le profil de restrictions d’appareil décrit dans cet article et configurer les paramètres autorisés dans Microsoft Edge et les fonctionnalités spécifiques. Veillez à choisir le même type de mode plein écran Edge comme sélectionné dans votre profil de plein écran ([paramètres de plein écran Windows](kiosk-settings-windows.md)). 

    [Prise en charge des paramètres du mode plein écran](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) est une ressource précieuse.

> [!IMPORTANT] 
> Veillez à affecter ce profil Microsoft Edge pour les mêmes unités que celles de votre profil de plein écran ([paramètres de plein écran Windows](kiosk-settings-windows.md)).

CSP : [ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Expérience de démarrage

- **Démarrer Microsoft Edge avec** : choisir les pages qui s’ouvrent au démarrage de Microsoft Edge. Les options disponibles sont les suivantes :
  - **Pages de démarrage** : Microsoft Edge démarre avec la page de démarrage par défaut définie par le système d’exploitation
  - **Page Nouvel onglet** : Microsoft Edge charge ce qui est défini dans le paramètre **URL de la page Nouvel onglet**
  - **Page de la dernière session** : Microsoft Edge charge la page de la dernière session 
  - **Page de démarrage personnalisée** : Microsoft Edge charge la page de démarrage définie par l’administrateur informatique
- **L’utilisateur peut modifier les pages de démarrage** : l’option **Autoriser** permet aux utilisateurs de modifier les pages de démarrage. Les administrateurs peuvent utiliser `EdgeHomepageUrls` pour entrer les pages de démarrage que les utilisateurs voient par défaut lorsqu’ils ouvrent Microsoft Edge. **Non configuré** empêche les utilisateurs de modifier les pages de démarrage.
- **URL de la page Nouvel onglet** : entrer l’URL pour ouvrir la page Nouvel onglet. Par exemple, entrez `https://www.bing.com`.
- **Ouvrir du contenu web sur la page Nouvel onglet** : choisir **Bloquer** pour empêcher Microsoft Edge d’ouvrir un site web dans un nouvel onglet. Si l’option Bloquer est sélectionnée, le nouvel onglet s’ouvre vide. **Non configuré** utilise le comportement par défaut du système d’exploitation sur l’appareil, ce qui peut permettre aux utilisateurs de choisir ce qui est affiché.
- **Bouton Accueil** : choisir ce qui se passe lorsque le bouton Accueil est sélectionné. Les options disponibles sont les suivantes :
  - **Pages de démarrage** : l’option que vous avez choisi pour le paramètre **Démarrer Microsoft Edge avec** s’ouvre
  - **Page Nouvel onglet** : l’option que vous avez choisi pour le paramètre **URL de la page Nouvel onglet** s’ouvre
  - **URL du bouton Accueil personnalisé** : l’option que vous avez choisi pour le paramètre **URL du bouton Accueil** s’ouvre
  - **Masquer le bouton Accueil** : masque le bouton Accueil
- **L’utilisateur peut modifier le bouton Accueil** : l’option **Autoriser** permet aux utilisateurs de modifier le bouton Accueil. Les modifications de l’utilisateur remplacent les paramètres de l’administrateur pour le bouton Accueil. **Non configuré** utilise le comportement par défaut du système d’exploitation sur l’appareil, ce qui empêcher les utilisateurs de changer la façon dont l’administrateur a configuré le bouton Accueil.
- **Afficher la page Expérience de la première exécution** : **empêcher** l’affichage de la page d’introduction lors de la première exécution de Microsoft Edge. Cette fonctionnalité permet aux entreprises, notamment celles inscrites dans les configurations zéro émissions, de bloquer cette page. **Non configuré** affiche la page d’introduction.
  - **URL Expérience de la première exécution** : entrer l’URL de la page à afficher la première fois qu’un utilisateur exécute Microsoft Edge (Windows 10 Mobile uniquement).
- **Actualisez le navigateur après la durée d’inactivité**: entrez le nombre de minutes inactifs jusqu'à ce que l’actualisation du navigateur, à partir de 0-1 440 minutes. Valeur par défaut est `5` minutes. Lorsque la valeur `0` (zéro), le navigateur n’actualise pas après une inactivité.

  Ce paramètre est uniquement disponible lors de l’exécution [de navigation InPrivate Public (application unique plein écran)](#use-microsoft-edge-kiosk-mode).

  CSP : [ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **Fenêtres contextuelles** : choisir **Bloquer** pour arrêter les fenêtres contextuelles dans le navigateur. S’applique à Windows 10 Desktop uniquement. **Non configuré** autorise les fenêtres contextuelles dans le navigateur web.
- **Envoyer le trafic intranet vers Internet Explorer** : **autorise** les utilisateurs à ouvrir des sites web intranet dans Internet Explorer au lieu de Microsoft Edge (Windows 10 Desktop uniquement). **Non configuré** autorise les utilisateurs à afficher Microsoft Edge.
- **Emplacement de la liste des sites en mode entreprise** : entrer l’URL qui inclut la liste des sites web qui s’ouvrent en Mode entreprise. Les utilisateurs ne peuvent pas modifier cette liste. S’applique à Windows 10 Desktop uniquement.
- **Message lors de l’ouverture de sites dans Internet Explorer** : utiliser ce paramètre pour configurer Microsoft Edge afin d’afficher une notification avant l’ouverture d’un site dans Internet Explorer 11. Les options disponibles sont les suivantes :
  - **Non configuré** : le comportement par défaut du système d’exploitation est utilisé, ce qui peut ne pas afficher un message.
  - **Afficher le message sans option pour ouvrir des sites dans Microsoft Edge** : afficher le message lors de l’ouverture de sites dans Internet Explorer. Les sites s’ouvrent dans Internet Explorer. Il n’y a pas d’option pour ouvrir des sites dans Microsoft Edge.
  - **Afficher le message lors de l’ouverture de sites dans Microsoft Edge** : afficher le message lors de l’ouverture de sites dans Internet Explorer. Le message inclut un lien **Poursuivre dans Microsoft Edge** qui permet aux utilisateurs de Microsoft Edge au lieu d’Internet Explorer.

  > [!IMPORTANT]
  > Ce paramètre requiert que vous activiez l’option **Configurer la liste des sites en Mode entreprise**, l’option **Envoyer tous les sites intranet vers Internet Explorer 11**, ou les deux.

- **Liste de compatibilité Microsoft** : l’option **Bloquer** bloque la liste de compatibilité de Microsoft dans Microsoft Edge. Cette liste de Microsoft permet à Microsoft Edge d’afficher correctement les sites ayant des problèmes de compatibilité connus. **Non configuré** permet l’utilisation d’une liste de compatibilité de Microsoft.
- **Précharger les pages de démarrage et la page Nouvel onglet** : choisir **Bloquer** pour empêcher Microsoft Edge de précharger les pages de démarrage et la page Nouvel onglet. Le préchargement réduit le temps de démarrage de Microsoft Edge et de chargement d’un nouvel onglet. **Non configuré** utilise le comportement par défaut du système d’exploitation, qui peut être de précharger ces pages.
- **Prélancer les pages de démarrage et la page Nouvel onglet** : choisir **Bloquer** pour empêcher Microsoft Edge de prélancer les pages de démarrage et la page Nouvel onglet. Le prélancement aide les performances de Microsoft Edge et réduit le temps nécessaire pour démarrer Microsoft Edge. **Non configuré** utilise le comportement par défaut du système d’exploitation, qui peut être de prélancer ces pages.

### <a name="favorites-and-search"></a>Favoris et recherche

- **Barre Favoris** : choisir ce qui se passe pour la barre Favoris dans n’importe quelle page de Microsoft Edge. Les options disponibles sont les suivantes :
  - **Non configuré** : utilise le comportement par défaut du système d’exploitation, qui peut être de masquer la barre Favoris sur toutes les pages. L’utilisateur peut modifier ce paramètre.
  - **Masquer** : masque la barre Favoris sur toutes les pages. L’utilisateur ne peut pas modifier ce paramètre.
  - **Afficher** : affiche la barre Favoris sur toutes les pages. L’utilisateur ne peut pas modifier ce paramètre.
- **Liste Favoris** : ajouter une liste d’URL au fichier des favoris. Par exemple, ajoutez `http://contoso.com/favorites.html`.
- **Limiter les modifications des favoris** : l’option **Bloquer** empêche les utilisateurs d’ajouter, d’importer, de trier ou de modifier la liste des favoris. **Non configuré** utilise le comportement par défaut du système d’exploitation, ce qui peut permettre aux utilisateurs de modifier la liste.
- **Synchroniser les favoris entre les navigateurs Microsoft (Desktop uniquement)** : l’option **Exiger** force Windows à synchroniser les Favoris entre Internet Explorer et Microsoft Edge. Les ajouts, suppressions, modifications et changements d’ordre dans les favoris sont partagés entre les navigateurs.  **Non configuré** utilise le comportement par défaut du système d’exploitation, ce qui peut donner aux utilisateurs le choix de synchroniser les favoris entre les navigateurs.
- **Moteur de recherche par défaut** : choisir le moteur de recherche par défaut sur l’appareil. Les utilisateurs finaux peuvent modifier cette valeur à tout moment. Les options disponibles sont les suivantes :
  - Par défaut
  - Bing
  - Google
  - Yahoo
  - Valeur personnalisée
- **Suggestions de recherche** : **Non configuré** permet à votre moteur de recherche de suggérer des sites à mesure que vous saisissez des expressions de recherche dans la barre d’adresses. L’option **Bloquer** empêche cette fonctionnalité.
- **Autoriser les modifications sur le moteur de recherche**: **Oui** (valeur par défaut) permet aux utilisateurs d’ajouter de nouveaux moteurs de recherche, ou modifier le moteur de recherche par défaut dans Microsoft Edge. Choisissez **non** pour empêcher les utilisateurs de personnaliser le moteur de recherche.

  Ce paramètre est uniquement disponible lors de l’exécution [mode Normal (kiosque multi-application)](#use-microsoft-edge-kiosk-mode).

  CSP : [AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>Confidentialité et sécurité

- **Navigation inPrivate** : l’option **Bloquer** empêche l’utilisateur final d’ouvrir des sessions de navigation InPrivate. L’option **Non configuré** autorise cette fonctionnalité.
- **Enregistrer l’historique de navigation** : l’option **Bloquer** empêche Microsoft Edge d’enregistrer l’historique de navigation. L’option **Non configuré** autorise l’enregistrement de l’historique de navigation.
- **Effacer les données de navigation à la sortie (Desktop uniquement)** : l’option **Exiger** efface l’historique et les données de navigation quand l’utilisateur quitte Microsoft Edge. **Non configuré** utilise le comportement par défaut du système d’exploitation, ce qui peut mettre en cache les données de navigation.
- **Synchroniser les paramètres du navigateur entre les appareils de l’utilisateur** : choisir la façon dont vous souhaitez synchroniser les paramètres du navigateur entre les appareils. Les options disponibles sont les suivantes :
  - **Autoriser** : autoriser la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur
  - **Bloquer et activer le remplacement par l’utilisateur** : bloquer la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur. Les utilisateurs peuvent remplacer ce paramètre.
  - **Bloquer** : bloquer la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur. Les utilisateurs ne peuvent pas remplacer ce paramètre.
- **Gestionnaire de mots de passe** : l’option **Bloquer** désactive la fonctionnalité Gestionnaire de mots de passe Microsoft Edge. L’option **Non configuré** autorise cette fonctionnalité.
- **Cookies** : choisir la façon dont les cookies sont gérés dans le navigateur web. Les options disponibles sont les suivantes :
  - **Autoriser** : les cookies sont stockés sur l’appareil.
  - **Bloquer tous les cookies** : les cookies ne sont pas stockés sur l’appareil.
  - **Bloquer uniquement les cookies tiers** : les cookies tiers ou de partenaire ne sont pas stockés sur l’appareil.
- **Remplissage automatique** : l’option **Bloquer** désactive la fonctionnalité de remplissage automatique sur l’appareil. **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur (Windows 10 Desktop uniquement).
- **Envoyer des en-têtes Do Not Track** : **Non configuré** exige que les appareils envoient des en-têtes Do Not Track aux sites web exigeant des informations de suivi (recommandé). Choisir **Bloquer** pour empêcher l’appareil d’envoyer ces en-têtes, ce qui permet aux sites web d’effectuer le suivi de l’utilisateur.
- **Adresse IP localhost WebRTC** : l’option **Bloquer** empêche l’affichage de l’adresse IP localhost des utilisateurs lors d’appels téléphoniques effectués à l’aide du protocole RTC web. **Non configuré** permet d’afficher l’adresse IP localhost des utilisateurs lors d’appels téléphoniques effectués à l’aide de ce protocole.
- **Collecte de données pour les vignettes dynamiques** : choisir **Bloquer** pour empêcher Windows de collecter des informations sur la vignette dynamique quand un site est épinglé au menu Démarrer à partir de Microsoft Edge. **Non configuré** autorise la collecte de ces informations.
- **L’utilisateur peut remplacer les erreurs de certificat** : l’option **Bloquer** empêche les utilisateurs d’accéder à des sites web qui contiennent des erreurs SSL ou TLS. **Non configuré** autorise les utilisateurs à accéder à ces sites.

### <a name="additional"></a>Supplémentaire

- **Navigateur Microsoft Edge (mobile uniquement)** : choisir **Bloquer** afin d’éviter l’utilisation de Microsoft Edge sur l’appareil. Si vous bloquez Microsoft Edge, les paramètres individuels s’appliquent uniquement au bureau. **Non configuré** autorise l’utilisation du navigateur Microsoft Edge sur l’appareil.
- **Liste déroulante des barres d’adresse (Desktop uniquement)** : l’option **Bloquer** empêche Microsoft Edge d’afficher une liste de suggestions dans une liste déroulante quand vous tapez. Cette option aide à réduire la bande passante réseau entre Microsoft Edge et les services Microsoft. **Non configuré** autorise Microsoft Edge afficher une liste de suggestions.
- **Plein écran** : choisir **Bloquer** pour empêcher Microsoft Edge d’afficher uniquement le contenu web et de masquer Microsoft Edge (mode plein écran). **Non configuré** utilise la valeur par défaut du système d’exploitation, ce qui permet à Microsoft Edge d’utiliser le mode plein écran.
- **À propos des indicateurs** : l’option **Bloquer** empêche les utilisateurs finaux d’accéder à la page `about:flags` dans Microsoft Edge qui inclut les paramètres expérimentaux et de développement. **Non configuré** utilise la valeur par défaut du système d’exploitation, ce qui peut permettre l’accès à la page `about:flags`.
- **Outils de développement** : l’option **Bloquer** empêche l’utilisateur final d’ouvrir les outils de développement Microsoft Edge. **Non configuré** permet aux utilisateurs d’ouvrir les outils de développement.
- **Extensions** : l’option **Non configuré** autoriser l’utilisateur final à installer des extensions Microsoft Edge sur l’appareil. L’option **Bloquer** empêche l’installation.
- **Chargement indépendant des extensions de développement** : l’option **Bloquer** empêche Microsoft Edge d’effectuer un chargement indépendant, qui permet d’installer et d’exécuter des extensions non vérifiées à l’aide de la fonctionnalité **Charger des extensions**. **Non configuré** utilise la valeur par défaut du système d’exploitation, ce qui peut autoriser le chargement indépendant.
- **Extensions obligatoires** : choisir les extensions qui ne peuvent pas être désactivées par les utilisateurs finaux dans Microsoft Edge. Entrez les noms des familles de packages, puis sélectionnez **Ajouter**. Les listes [Rechercher le nom d’une famille de packages (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) offrent quelques conseils.

  Vous pouvez également **importer** un fichier CSV qui inclut les noms des familles de packages.

- **JavaScript** : choisir **Bloquer** pour empêcher que les scripts Java dans le navigateur s’exécutent sur l’appareil. **Non configuré** autorise l’exécution de scripts, tels que JavaScript, dans le navigateur Microsoft Edge.

## <a name="network-proxy"></a>Proxy réseau

- **Détecter automatiquement les paramètres du proxy** : quand cette option est activée, l’appareil tente de trouver le chemin d’un script PAC.
- **Utiliser un script de proxy** : sélectionnez cette option pour entrer un chemin à un script PAC pour configurer le serveur proxy.
  - **URL de l’adresse du script de configuration** : entrez l’URL d’un script PAC que vous souhaitez utiliser pour configurer le serveur proxy.
- **Utiliser un serveur proxy manuel** : sélectionnez cette option pour entrer manuellement les informations du serveur proxy.
  - **Adresse** : entrez le nom ou l’adresse IP du serveur proxy.
  - **Numéro de port** : entrez le numéro de port de votre serveur proxy.
  - **Exceptions du proxy** : entrez les URL qui ne doivent pas utiliser le serveur proxy. Utilisez des points-virgules pour séparer chaque élément.
  - **Ignorer le serveur proxy pour les adresses locales** : si vous ne souhaitez pas utiliser le serveur proxy pour les adresses locales sur votre intranet, activez cette option.

## <a name="password"></a>Mot de passe

- **Mot de passe** : demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil.
  - **Type de mot de passe requis** : spécifie si le mot de passe doit être numérique uniquement ou alphanumérique.
  - **Longueur minimale du mot de passe** : s’applique à Windows 10 Mobile uniquement.
  - **Nombre d'échecs de connexion avant réinitialisation de l'appareil** : pour les appareils exécutant Windows 10 : si BitLocker est activé sur l’appareil, ce dernier passe en mode de récupération BitLocker après le nombre d’échecs de connexion que vous avez spécifié. Si BitLocker n’est pas activé sur l’appareil, alors ce paramètre ne s’applique pas. Pour les appareils exécutant Windows 10 Mobile : après le nombre d’échecs de connexion que vous spécifiez, l’appareil est réinitialisé.
  - **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** : spécifie la durée pendant laquelle l’appareil doit être inactif avant le verrouillage de l’écran.
  - **Expiration du mot de passe (jours)** : spécifie la durée après laquelle le mot de passe d’un appareil doit être modifié.
  - **Empêcher la réutilisation des mots de passe précédents** : spécifie le nombre de mots de passe précédemment utilisés conservés par l’appareil.
  - **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (Mobile uniquement)** : spécifie que l’utilisateur doit entrer un mot de passe pour déverrouiller l’appareil (Windows 10 Mobile uniquement).
  - **Mots de passe simples** : permet d’utiliser des mots de passe simples, tels que 1111 ou 1234. Ce paramètre autorise ou bloque également l’utilisation des mots de passe d’image Windows.

## <a name="per-app-privacy-exceptions"></a>Exceptions de confidentialité par application

Vous pouvez ajouter des applications qui doivent avoir un comportement de confidentialité différent de celui défini dans « Confidentialité par défaut ».

- **Nom du package** : nom de famille du package d'application.
- **Nom de l’application**  : nom de l’application.

### <a name="exceptions"></a>Exceptions

- **Informations de compte** : définir si cette application peut accéder au nom, à la photo et à d'autres informations de contact de l'utilisateur.
- **Applications en arrière-plan** : définir si cette application peut s'exécuter en arrière-plan.
- **Calendrier** : définir si cette application peut accéder au calendrier.
- **Historique des appels** : définir si cette application peut accéder à l'historique de mes appels.
- **Appareil photo** : définir si cette application peut accéder à l'appareil photo.
- **Contacts** : définir si cette application peut accéder aux contacts.
- **Courrier électronique** : définir si cette application peut accéder aux e-mails et en envoyer.
- **Emplacement** : définir si cette application peut accéder aux informations de localisation.
- **Messages** : définir si cette application peut lire ou envoyer des SMS ou MMS.
- **Microphone** : définir si cette application peut utiliser le microphone.
- **Mouvement** : définir si cette application peut accéder aux informations de mouvement de l'appareil.
- **Notifications** : définir si cette application peut accéder aux notifications.
- **Téléphone** : définir si cette application peut accéder au téléphone.
- **Radios** : certaines applications utilisent des signaux radio, comme Bluetooth, dans votre appareil pour envoyer et recevoir des données, et doivent activer et désactiver ces signaux radio. Définissez si cette application peut contrôler ces signaux radio.
- **Tâches** : définir si cette application peut accéder à vos tâches.
- **Appareils approuvés** : choisir si cette application peut utiliser des appareils approuvés (matériel déjà connecté) ou du matériel fourni avec l’appareil. Par exemple, utilisez des téléviseurs, des projecteurs, etc. comme appareils de confiance.
- **Commentaires et diagnostics** : définir si cette application peut accéder aux informations de diagnostic.
- **Synchroniser avec les appareils** : choisir si cette application peut automatiquement partager et synchroniser des informations avec des appareils sans fil qui ne sont pas explicitement jumelés avec l’appareil.

## <a name="personalization"></a>Personalization

- **URL de l’image d’arrière-plan du poste de travail (Desktop uniquement)** : entrez l’URL d’une image au format JPEG que vous souhaitez utiliser comme papier peint du Bureau Windows. Les utilisateurs ne peuvent pas changer d’image.

## <a name="printer"></a>Imprimante

- **Imprimantes** : liste des imprimantes locales qui ont été ajoutées.
- **Imprimante par défaut** : définissez l’imprimante par défaut.
- **Accès utilisateur pour ajouter de nouvelles imprimantes** : autorisez ou bloquez l’utilisation d’imprimantes locales.

## <a name="privacy"></a>Confidentialité

- **Personnalisation des entrées** : ne pas autoriser l’utilisation des services cloud de reconnaissance vocale pour les applications du Microsoft Store, la dictée ou Cortana. Si vous autorisez ces services, Microsoft peut collecter des données vocales pour améliorer le service.
- **Acceptation automatique des invites de consentement de l’utilisateur pour le couplage et la confidentialité** : autoriser Windows à accepter automatiquement les messages de consentement de couplage et de confidentialité lors de l’exécution des applications.
- **Publier les activités de l’utilisateur** : sélectionnez **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches.
- **Activités locales uniquement** : sélectionnez **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches en fonction uniquement de l’activité locale.

Vous pouvez configurer les informations auxquelles toutes les applications sur l’appareil peuvent accéder. Vous pouvez définir des exceptions pour chaque application à l’aide de l’option **Exceptions de confidentialité par application**.

### <a name="exceptions"></a>Exceptions

- **Informations de compte** : définir si cette application peut accéder au nom, à la photo et à d'autres informations de contact de l'utilisateur.
- **Applications en arrière-plan** : définir si cette application peut s'exécuter en arrière-plan.
- **Calendrier** : définir si cette application peut accéder au calendrier.
- **Historique des appels** : définir si cette application peut accéder à l'historique de mes appels.
- **Appareil photo** : définir si cette application peut accéder à l'appareil photo.
- **Contacts** : définir si cette application peut accéder aux contacts.
- **Courrier électronique** : définir si cette application peut accéder aux e-mails et en envoyer.
- **Emplacement** : définir si cette application peut accéder aux informations de localisation.
- **Messages** : définir si cette application peut lire ou envoyer des SMS ou MMS.
- **Microphone** : définir si cette application peut utiliser le microphone.
- **Mouvement** : définir si cette application peut accéder aux informations de mouvement de l'appareil.
- **Notifications** : définir si cette application peut accéder aux notifications.
- **Téléphone** : définir si cette application peut accéder au téléphone.
- **Radios** : certaines applications utilisent des signaux radio, comme Bluetooth, dans votre appareil pour envoyer et recevoir des données, et doivent activer et désactiver ces signaux radio. Définissez si cette application peut contrôler ces signaux radio.
- **Tâches** : définir si cette application peut accéder à vos tâches.
- **Appareils de confiance**: choisissez si cette application peut utiliser des appareils de confiance. Les appareils de confiance sont des appareils déjà connectés ou ayant été fournis avec l’appareil. Par exemple, utilisez des téléviseurs, des projecteurs, et ainsi de suite comme appareils approuvés.
- **Commentaires et diagnostics** : choisir si cette application peut accéder aux informations de diagnostic.
- **Synchroniser avec les appareils** - Définir si cette application peut automatiquement partager et synchroniser des informations avec des appareils sans fil qui ne sont pas explicitement jumelés avec ce PC, cette tablette ou ce téléphone.

## <a name="projection"></a>Projection

- **Entrées utilisateur à partir de récepteurs d'affichage sans fil** : bloque la saisie des utilisateurs à partir de récepteurs d’affichage sans fil.
- **Projection sur ce PC** : empêche les autres appareils de trouver le PC pour la projection.
- **Exiger un code PIN pour l'appairage** : exige un code PIN lors de la connexion à un projecteur.

## <a name="reporting-and-telemetry"></a>Création de rapports et les données de télémétrie

- **Partager des données d’utilisation** : choisissez le niveau des données de diagnostic qui sont envoyées. Les options disponibles sont les suivantes :
  - Sécurité
  - Basique
  - Étendu
  - Complète
- **Envoyer les données de navigation Microsoft Edge à Microsoft 365 Analytics** : pour utiliser cette fonctionnalité, définissez les paramètres **Partager des données d’utilisation** sur **Étendu** ou **Complet**. Cette fonctionnalité contrôle les données que Microsoft Edge envoie à Microsoft 365 Analytics pour les appareils d’entreprise avec un ID commercial configuré. Les options disponibles sont les suivantes :
  - **Non configuré** : utilise la valeur par défaut du système d’exploitation, ce qui peut n’envoyer aucune donnée de l’historique de navigation
  - **Envoyer uniquement les données intranet** : permet à l’administrateur d’envoyer l’historique des données intranet
  - **Envoyer uniquement les données Internet** : permet à l’administrateur d’envoyer l’historique des données Internet
  - **Envoyer les données intranet et Internet** : permet à l’administrateur d’envoyer l’historique des données intranet et Internet
- **Serveur proxy de télémétrie** : entrez le nom de domaine complet (FQDN) ou l'adresse IP d'un serveur proxy pour transférer les demandes Expériences des utilisateurs connectés et télémétrie à l'aide d'une connexion SSL (Secure Sockets Layer). Le format de ce paramètre est *serveur*:*port*. En cas d'échec du proxy nommé ou si aucun proxy n'est entré à l'activation de cette stratégie, les données Expériences des utilisateurs connectés et télémétrie ne sont pas envoyées et restent sur l'appareil local.

  Exemples de formats :

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Recherche

- **Recherche sécurisée (mobile uniquement)** : contrôler la manière dont Cortana filtre les contenus pour adultes dans les résultats de la recherche. Vous pouvez sélectionner **Strict** ou **Modéré**, ou encore autoriser l’utilisateur à choisir ses propres paramètres.
- **Afficher les résultats web dans la recherche** : empêcher ou autoriser l’affichage des résultats web dans les recherches effectuées sur l’appareil.

## <a name="start"></a>Démarrer

- **Disposition du menu Démarrer** : pour personnaliser le menu Démarrer sur les appareils de bureau, vous pouvez charger un fichier XML qui inclut vos personnalisations, notamment l’ordre dans lequel les applications sont listées. Les utilisateurs ne peuvent pas changer la disposition du menu Démarrer que vous entrez.
- **Épingler des sites web à des vignettes dans le menu Démarrer** : importez des images provenant de Microsoft Edge et affichez-les sous forme de liens dans le menu Démarrer de Windows pour les appareils de bureau.
- **Détacher des applications de la barre des tâches** : choisissez **Bloquer** pour empêcher l’utilisateur de détacher des applications de la barre des tâches.
- **Changement rapide d’utilisateur** : choisir **Bloquer** pour empêcher le passage d’un utilisateur connecté à un autre sans déconnexion.
- **Applications les plus utilisées** : choisir **Bloquer** pour ne pas afficher les applications les plus utilisées dans le menu Démarrer. Le bouton bascule correspondant dans l’application Paramètres est également désactivé.
- **Applications ajoutées récemment** : choisir **Bloquer** pour ne pas afficher les applications ajoutées récemment dans le menu Démarrer. Le bouton bascule correspondant dans l’application Paramètres est également désactivé.
- **Mode de l’écran de démarrage** : choisir comment afficher l’écran de démarrage. Vous avez le choix entre **Plein écran** et **Ne pas utiliser le plein écran**.
- **Éléments ouverts récemment dans les listes de raccourcis** : choisir **Bloquer** pour ne pas afficher les listes de raccourcis dans le menu Démarrer et la barre des tâches. Le bouton bascule correspondant dans l’application Paramètres est également désactivé.
- **Liste d’applications** : choisir comment afficher l’application Paramètres. Les options disponibles sont les suivantes : 
  - Réduire
  - Réduire et désactiver l’application Paramètres 
  - Supprime et désactive l’application Paramètres
- **Bouton d’alimentation** : choisir **Bloquer** pour ne pas afficher le bouton d’alimentation dans le menu Démarrer.
- **Vignette de l’utilisateur** : choisir **Bloquer** pour ne pas afficher la vignette de l’utilisateur dans le menu Démarrer.
  - **Verrouiller** : choisir **Bloquer** pour ne pas afficher l’option `Lock` dans la vignette de l’utilisateur du menu Démarrer.
  - **Déconnexion** : choisir **Bloquer** pour ne pas afficher l’option `Sign out` dans la vignette de l’utilisateur du menu Démarrer.
- **Arrêter** : choisir **Bloquer** pour ne pas afficher les options `Update and shut down` et `Shut down` dans le bouton d’alimentation du menu Démarrer.
- **Veille** : choisir **Bloquer** pour ne pas afficher l’option `Sleep` dans le bouton d’alimentation du menu Démarrer.
- **Mettre en veille prolongée** : choisir **Bloquer** pour ne pas afficher l’option `Hibernate` dans le bouton d’alimentation du menu Démarrer.
- **Changer de compte** : choisir **Bloquer** pour ne pas afficher `Switch account` dans la vignette de l’utilisateur du menu Démarrer.
- **Options de redémarrage** : choisir **Bloquer** pour ne pas afficher les options `Update and restart` et `Restart` dans le bouton d’alimentation du menu Démarrer.
- **Documents sur Démarrer** : masquer ou afficher le dossier Documents dans le menu Démarrer de Windows.
- **Téléchargements sur Démarrer** : masquer ou afficher le dossier Téléchargements dans le menu Démarrer de Windows.
- **Explorateur de fichiers sur Démarrer** : masquer ou afficher l’application Explorateur de fichiers dans le menu Démarrer de Windows.
- **Groupe résidentiel sur Démarrer** : masquer ou afficher le dossier Groupe résidentiel dans le menu Démarrer de Windows.
- **Musique sur Démarrer** : masquer ou afficher le dossier Musique dans le menu Démarrer de Windows.
- **Réseau sur Démarrer** : masquer ou afficher le dossier Réseau dans le menu Démarrer de Windows.
- **Dossier Personnel sur Démarrer** : masquer ou afficher le dossier Personnel dans le menu Démarrer de Windows.
- **Images sur Démarrer** : masquer ou afficher le dossier Images dans le menu Démarrer de Windows.
- **Paramètres sur Démarrer** : masquer ou afficher le dossier Paramètres dans le menu Démarrer de Windows.
- **Vidéos sur Démarrer** : masquer ou afficher le dossier Vidéos dans le menu Démarrer de Windows.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen pour Microsoft Edge** : activer Microsoft Edge SmartScreen pour accéder au site et aux téléchargements de fichiers.
- **Accès à un site malveillant** : empêcher les utilisateurs d'ignorer les avertissements concernant le filtre Windows Defender SmartScreen et d’accéder au site.
- **Téléchargement des fichiers non vérifiés** : empêcher les utilisateurs d'ignorer les avertissements concernant le filtre Windows Defender SmartScreen et de télécharger des fichiers non vérifiés.

## <a name="windows-spotlight"></a>Windows à la une

- **Windows à la une** : utilisez ce paramètre pour bloquer toutes les fonctionnalités Windows à la une sur les appareils Windows 10. Si vous bloquez ce paramètre, les paramètres suivants ne sont pas disponibles :
  - **Windows à la une sur l’écran de verrouillage** : empêche Windows à la une d’afficher des informations sur l’écran de verrouillage de l’appareil.
  - **Suggestions de tiers dans Windows à la une** : empêche Windows à la une de suggérer du contenu qui n’est pas publié par Microsoft.
  - **Fonctionnalités grand public** : permet de bloquer certaines fonctionnalités grand public, comme l’affichage de suggestions sur le menu Démarrer ou encore les notifications d’appartenance.
  - **Conseils Windows** : permet de bloquer l’affichage des info-bulles dans Windows.
  - **Windows à la une dans le centre de notifications** : empêche l’affichage des suggestions de Windows à la une telles que le nouveau contenu de sécurité ou d’application dans le Centre de notifications de Windows.
  - **Personnalisation de Windows à la une** : empêche Windows à la une de personnaliser les résultats en fonction de l’utilisation d’un appareil.
  - **Écrans d’accueil de Windows** : bloquer l’expérience d’accueil de Windows qui montre à l’utilisateur des informations sur les fonctionnalités nouvelles ou mises à jour.

## <a name="windows-defender-antivirus"></a>Antivirus Windows Defender

- **Surveillance en temps réel** : active la recherche en temps réel des logiciels malveillants, logiciels espions et autres logiciels indésirables.
- **Analyse du comportement** : permet à Defender de rechercher certains modèles connus d’activité suspecte sur les appareils.
- **Système NIS (Network Inspection System)** : le système NIS vous aide à vous protéger contre les attaques réseau. Il utilise les signatures de vulnérabilités connues fournies par le Microsoft Endpoint Protection Center pour faciliter la détection et le blocage du trafic malveillant.
- **Analyser tous les téléchargements** : contrôle si Defender analyse tous les fichiers téléchargés depuis Internet.
- **Analyser les scripts chargés dans les navigateurs web Microsoft** : permet à Defender d’analyser les scripts utilisés dans Internet Explorer.
- **Accès de l'utilisateur final à Defender** : détermine si l'interface utilisateur de Windows Defender est masquée aux utilisateurs finaux. Quand ce paramètre est modifié, le changement est appliqué au prochain redémarrage de l’ordinateur de l’utilisateur final.
- **Intervalle de mise à jour des signatures (en heures)** : spécifie l’intervalle auquel Defender vérifie les nouveaux fichiers de signatures.
- **Surveiller l’activité des fichiers et des programmes** : autorise Defender à surveiller l’activité des fichiers et des programmes sur des appareils.
- **Nombre de jours avant la suppression des programmes malveillants en quarantaine** : permet à Defender de continuer à suivre les logiciels malveillants résolus pendant un certain nombre de jours que vous spécifiez, pour vous permettre de vérifier manuellement les appareils affectés. Si vous définissez le nombre de jours du suivi sur **0**, les logiciels malveillants restent dans le dossier de quarantaine et ne sont pas automatiquement supprimés.
- **Limite de l'utilisation du processeur pendant une analyse** : vous permet de limiter la quantité de ressources du processeur que les analyses sont autorisées à utiliser (de **1** à **100**).
- **Analyser les fichiers d’archive** : permet à Defender d’analyser les fichiers archivés tels que les archives .zip ou .cab.
- **Analyser les e-mails entrants** : permet à Defender d’analyser les e-mails quand ils arrivent sur l’appareil.
- **Analyser les disques amovibles lors d'une analyse complète** : permet à Defender d'analyser les lecteurs amovibles tels que les clés USB.
- **Analyser les lecteurs réseau mappés lors d'une analyse complète** : permet à Defender d’analyser les fichiers sur un lecteur réseau mappé.
  Si les fichiers sur le lecteur sont en lecture seule, Defender ne peut pas supprimer les logiciels malveillants détectés dans ces fichiers.
- **Analyser les fichiers ouverts à partir de dossiers réseau** : permet à Defender d’analyser les fichiers sur des lecteurs réseau partagés (par exemple les fichiers accessibles à partir d’un chemin UNC). Si les fichiers sur le lecteur sont en lecture seule, Defender ne peut pas supprimer les logiciels malveillants détectés dans ces fichiers.
- **Protection du cloud** : autorise ou empêche Microsoft Active Protection Service de recevoir des informations sur l’activité des logiciels malveillants en provenance des appareils que vous gérez. Ces informations serviront à améliorer le service.
- **Demander confirmation aux utilisateurs avant l’envoi d’un échantillon** : contrôle si les fichiers potentiellement malveillants susceptibles de nécessiter une analyse plus approfondie sont envoyés automatiquement à Microsoft.
- **Heure de l'analyse rapide quotidienne** : permet de planifier une analyse rapide exécutée tous les jours à l’heure de votre choix.
- **Type d’analyse système à effectuer** : entrer le niveau d’analyse effectué quand vous planifiez une analyse système.
- **Détecter les applications potentiellement indésirables** : choisissez le niveau de protection quand Windows détecte des applications potentiellement indésirables, parmi les niveaux suivants :
  - **Bloquer**
  - **Audit** Pour plus d’informations sur les applications potentiellement indésirables, consultez [Détecter et bloquer les applications potentiellement non désirées](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Actions en cas de détection de menaces de programmes malveillants** : utilisez cette option pour choisir les actions que Defender doit exécuter pour chaque niveau de menace détecté (faible, modéré, élevé et grave). Les options disponibles sont les suivantes :
  - **Nettoyer**
  - **Quarantaine**
  - **Supprimer**
  - **Autoriser**
  - **Défini par l’utilisateur**
  - **Bloquer**

### <a name="windows-defender-antivirus-exclusions"></a>Exclusions de l’antivirus Windows Defender

- **Fichiers et dossiers à exclure des analyses et de la protection en temps réel** : ajoute un ou plusieurs fichiers et dossiers comme **C:\Chemin** ou **%ProgramFiles%\Chemin\NomFichier.exe** à la liste des exclusions. Ces fichiers et dossiers ne sont pas inclus dans les analyses en temps réel ou planifiées.
- **Extensions de fichier à exclure des analyses et de la protection en temps réel** : ajoute une ou plusieurs extensions de fichier comme **jpg** ou **txt** à la liste des exclusions. Tous les fichiers avec ces extensions ne sont pas inclus dans les analyses en temps réel ou planifiées.
- **Processus à exclure des analyses et de la protection en temps réel** : ajoute un ou plusieurs processus de type **.exe**, **.com** ou **.scr** à la liste des exclusions. Ces processus ne sont pas inclus dans les analyses en temps réel ou planifiées.

## <a name="next-steps"></a>Étapes suivantes

Pour plus de détails techniques sur chaque paramètre et sur les éditions de Windows prises en charge, consultez [Référence CSP de stratégie Windows 10](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider).
