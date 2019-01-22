---
title: Paramètres de restriction des appareils pour Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres et leur description pour la création de restrictions d’appareil sur les appareils Windows 10 et versions ultérieures. Utilisez ces paramètres dans un profil de configuration pour contrôler les captures d’écran, les exigences de mot de passe, les paramètres Kiosk, les applications dans le magasin, le navigateur Edge, Windows Defender, l’accès au cloud, le menu Démarrer et autres dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: f2b75eb5a87dbfd7a17aee83f173d3d472920428
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203635"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Windows 10 (et versions ultérieures) pour autoriser ou restreindre les fonctionnalités dans Intune

Cet article liste et décrit tous les paramètres que vous pouvez contrôler sur les appareils Windows 10 et versions ultérieures. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, pour définir des règles de mot de passe, pour personnaliser l’écran de verrouillage, pour utiliser Windows Defender, et bien plus encore.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur les appareils Windows 10.

> [!Note]
> Toutes les options ne sont pas disponibles dans toutes les éditions de Windows.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md).

## <a name="app-store"></a>App Store

- **App Store (mobile uniquement)**  : Activez ou bloquez l’utilisation de l’App Store sur les appareils Windows 10 Mobile.
- **Mettre à jour automatiquement les applications du Store** : Permet la mise à jour automatique des applications installées à partir du Microsoft Store.
- **Installation d’applications approuvées** : Permet le chargement indépendant des applications signées avec un certificat approuvé.
- **Déverrouillage de développement** : Permet d’activer des paramètres de développement Windows, par exemple pour autoriser l’utilisateur à modifier des applications qui ont été chargées indépendamment.
- **Données d’application utilisateur partagées** : Permet aux applications de partager des données entre différents utilisateurs sur le même appareil.
- **Utiliser uniquement un magasin privé** : Activez cette option pour autoriser les utilisateurs à télécharger des applications uniquement à partir de votre magasin privé.
- **Lancement des applications du Windows Store** : Utilisé pour désactiver toutes les applications qui ont été préinstallées sur l’appareil ou téléchargées à partir du Microsoft Store.
- **Installer les données d’application sur le volume système :** Empêche les applications de stocker des données sur le volume système de l’appareil.
- **Installer les applications sur le lecteur système** : Empêche les applications de stocker des données sur le lecteur système de l’appareil.
- **Jeux DVR (Desktop uniquement)**  : Détermine si l’enregistrement et la diffusion des jeux sont autorisés ou non.
- **Applications du Store uniquement** : Détermine si les utilisateurs peuvent installer des applications à partir d’emplacements autres que l’App Store.

## <a name="cellular-and-connectivity"></a>Mobile et connectivité

- **Canal de données mobiles** : Empêche les utilisateurs d’utiliser des données, par exemple de naviguer sur le web, quand ils sont connectés à un réseau mobile. 
- **Itinérance des données** : Autorisez l'itinérance entre réseaux lors de l'accès aux données.
- **VPN sur le réseau de téléphonie mobile** : Contrôle si l’appareil peut accéder aux connexions VPN lorsqu'il est connecté à un réseau mobile.
- **Itinérance VPN sur le réseau de téléphonie mobile** : Contrôle si l’appareil peut accéder aux connexions VPN lorsqu'il est en itinérance sur un réseau mobile.
- **Bluetooth** : Contrôle si l’utilisateur peut activer et configurer la fonction Bluetooth sur l’appareil.
- **Découvertibilité de Bluetooth** : Permet à l’appareil d’être découvert par d’autres appareils Bluetooth.
- **Précouplage Bluetooth** : Permet de configurer des appareils Bluetooth spécifiques pour qu’ils soient couplés automatiquement à un appareil hôte.
- **Publicité Bluetooth** : Autorise l’appareil à recevoir des annonces publicitaires via Bluetooth.
- **Service d’appareils connectés** : Permet de choisir s’il faut autoriser le service d’appareils connectés, qui active la découverte et la connexion à d’autres appareils Bluetooth.
- **NFC** : Permet à l’utilisateur d’activer et de configurer les fonctionnalités NFC (Near Field Communications) sur l’appareil.
- **Wi-Fi** : Permet à l’utilisateur d’activer et de configurer le Wi-Fi sur l’appareil (Windows 10 Mobile uniquement).
- **Se connecter automatiquement aux points d’accès Wi-Fi** : Permet à l’appareil de se connecter automatiquement aux points d'accès Wi-Fi gratuits et d’accepter automatiquement les termes et conditions de la connexion.
- **Configuration manuelle du Wi-Fi** : Détermine si les utilisateurs peuvent configurer leurs propres connexions Wi-Fi ou s’ils peuvent uniquement utiliser les connexions configurées par un profil Wi-Fi (Windows 10 Mobile uniquement).
- **Intervalle de recherche de Wi-Fi** : Spécifie la fréquence à laquelle les appareils recherchent des réseaux Wi-Fi. Spécifiez une valeur comprise entre 1 (plus fréquent) et 500 (moins fréquent).
- **Services Bluetooth autorisés** : Spécifie (sous forme de chaînes hexadécimales) une liste de services et de profils Bluetooth autorisés.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Compte Microsoft** : Permet à l'utilisateur d'associer un compte Microsoft à l’appareil.
- **Compte non-Microsoft** : Permet à l’utilisateur d’ajouter des comptes de messagerie à l’appareil qui ne sont pas associés à un compte Microsoft.
- **Synchronisation des paramètres du compte Microsoft** : Permet aux paramètres d’appareil et d’application associés à un compte Microsoft de se synchroniser entre les appareils.

## <a name="cloud-printer"></a>Imprimante cloud

- **URL de découverte d’imprimantes** : Entrez l’URL de recherche des imprimantes cloud.
- **URL d’autorisation d’accès à l’imprimante** : Entrez l’URL du point de terminaison d’authentification pour obtenir des jetons OAuth. Par exemple, entrez quelque chose du genre `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID de l’application cliente native Azure** : Entrez le GUID identifiant l’application cliente autorisée à obtenir des jetons OAuth à partir d’OAuthAuthority.
- **URI de ressource du service d’impression** : Entrez l’URI de ressource OAuth pour le service d’impression configuré dans le portail Azure. Par exemple, entrez quelque chose du genre `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Nombre maximal d’imprimantes à interroger (Mobile uniquement)**  : Entrez le nombre maximal d’imprimantes à interroger. Par exemple, entrez `10`.
- **URI de ressource du service de découverte d’imprimantes** : Entrez l’URI de ressource OAuth pour le service de découverte d’imprimantes configuré dans le portail Azure. Par exemple, entrez quelque chose du genre `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Après avoir configuré une [impression cloud hybride Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), vous pouvez configurer ces paramètres et les déployer sur des appareils Windows.

## <a name="control-panel-and-settings"></a>Panneau de configuration et paramètres

- **Application Paramètres** : Bloque l’accès à l’application Paramètres de Windows.
  - **Système** : Bloque l’accès à la zone système de l’application Paramètres.
    - **Modification des paramètres d’alimentation et de veille (Desktop uniquement)**  : Empêche l’utilisateur final de changer les paramètres d’alimentation et de veille sur l’appareil.
  - **Appareils** : Bloque l’accès à la zone des appareils de l’application Paramètres.
  - **Réseau et Internet** : Bloque l’accès à la zone réseau et internet de l’application Paramètres.
  - **Personnalisation** : Bloque l’accès à la zone de personnalisation de l’application Paramètres.
  - **Comptes** : Bloque l’accès à la zone des comptes de l’application Paramètres.
  - **Heure et langue** : Bloque l’accès à la zone heure et langue de l’application Paramètres.
    - **Modification de l’heure système** : Empêche l’utilisateur final de changer les date et heure sur l’appareil.
    - **Modification des paramètres régionaux (Desktop uniquement)**  : Empêche l’utilisateur final de changer les paramètres de région sur l’appareil.
    - **Modification des paramètres de langue (Desktop uniquement)**  : Empêche l’utilisateur de changer les paramètres de langue sur l’appareil.
  - **Jeux** : Bloque l’accès à l’application Jeux dans Paramètres.
  - **Options d’ergonomie** : Bloque l’accès à la zone d’options d’ergonomie de l’application Paramètres.
  - **Confidentialité** : Bloque l’accès à la zone de confidentialité de l’application Paramètres.
  - **Mise à jour et sécurité** : Bloque l’accès à la zone des mises à jour et de la sécurité de l’application Paramètres.

## <a name="display"></a>Afficher

- **Activer la mise à l'échelle GDI pour des applications**
- **Désactiver la mise à l'échelle GDI pour des applications**

  La mise à l'échelle DPI GDI permet aux applications sans prise en charge DPI de bénéficier d'une prise en charge DPI par moniteur. Entrez les applications héritées dont la mise à l'échelle DPI GDI a été activée. Si la mise à l'échelle DPI GDI est configurée pour s'activer et se désactiver sur une application, la mise à l'échelle est désactivée pour l'application.

## <a name="general"></a>Général

- **Capture d’écran (mobile uniquement)**  : Autorise l’utilisateur à capturer le contenu de l’écran d’appareil en tant qu’image.
- **Copier et coller (mobile uniquement)**  : Autorise les actions copier-coller entre les applications sur l’appareil.
- **Désinscription manuelle** : Permet à l'utilisateur de supprimer manuellement le compte d'espace de travail de l'appareil
  - Ce paramètre de stratégie n’est pas appliqué si l’ordinateur est joint à Azure AD et que l’inscription automatique est activée. 
  - Ce paramètre de stratégie ne s’applique pas aux ordinateurs Windows 10 Famille.
- **Installation manuelle du certificat racine (mobile uniquement)**  : Empêche l’utilisateur d’installer manuellement les certificats racines et les certificats CAP intermédiaires.

- **Appareil photo** : Autorise ou bloque l’utilisation de l’appareil photo sur l’appareil.
- **Synchronisation des fichiers OneDrive** : Empêche l’appareil de synchroniser des fichiers avec OneDrive.
- **Stockage amovible** : Spécifie si des appareils de stockage externe comme une carte SD peuvent être utilisés avec l’appareil.
- **Géolocalisation** : Spécifie si l'appareil peut utiliser les informations des services d'emplacement.
- **Partage Internet** : Autorise l'utilisation du partage de connexion Internet sur l'appareil.
- **Réinitialisation du téléphone** : Détermine si l’utilisateur peut réinitialiser son appareil.
- **Connexion USB (mobile uniquement)**  : Contrôle si les appareils peuvent accéder à des périphériques de stockage externe via une connexion USB.
- **Mode antivol (mobile uniquement)**  : Configurer si le mode antivol Windows est activé.
- **Cortana** : Active ou désactive l'assistant vocal Cortana.
- **Enregistrement vocal (mobile uniquement)**  : Autorise ou bloque l’utilisation de l’enregistreur vocal de l’appareil.
- **Modification du nom de l’appareil** : Empêche l’utilisateur final de modifier le nom de l’appareil (Windows 10 Mobile uniquement).
- **Ajouter des packages de configuration** : Bloque l’agent de configuration du runtime qui installe les packages de configuration.
- **Supprimer les packages de configuration** : Bloque l’agent de configuration du runtime qui supprime les packages de provisionnement.
- **Découverte d’appareil** : Empêche un appareil d’être découvert par d’autres appareils.
- **Sélecteur de tâches (mobile uniquement)**  : Bloque le sélecteur de tâches sur l’appareil.
- **Boîte de dialogue d’erreur de carte SIM (mobile uniquement)**  : Empêche un message d’erreur de s’afficher sur l’appareil si aucune carte SIM n’est détectée.
- **Espace de travail Windows Ink** : Empêche les utilisateurs d’accéder à l’espace de travail Windows Ink. **Non configuré** : l’espace de travail Windows Ink est activé et l’utilisateur est autorisé à l’utiliser au-dessus de l’écran de verrouillage.
- **Redéploiement automatique** : Permet aux utilisateurs avec des droits administratifs de supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **CTRL + Win + R** dans l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion.
- **Demander aux utilisateurs de se connecter au réseau pendant l’installation de l’appareil (Windows Insider uniquement)**  : Choisissez l’option **Exiger** pour que l’appareil se connecte à un réseau avant de continuer au-delà de la page Réseau lors de la configuration de Windows 10. Tant que cette fonctionnalité est en préversion, vous avez besoin de Windows Insider build 1809 ou ultérieure pour utiliser ce paramètre.
- **Terminer les processus à partir du Gestionnaire des tâches** : Ce paramètre détermine si les non-administrateurs peuvent utiliser le Gestionnaire des tâches pour mettre fin aux tâches. L’option **Empêcher** empêche les utilisateurs standard (non-administrateurs) d’utiliser le Gestionnaire des tâches pour terminer un processus ou une tâche sur l’appareil. L’option **Non configuré** (par défaut) permet aux utilisateurs standard d’arrêter un processus ou une tâche à l’aide du Gestionnaire des tâches.

## <a name="kiosk-preview---obsolete"></a>Plein écran (préversion) - Obsolète

Ces paramètres sont en lecture seule et ne peuvent pas être modifiés. Pour configure le mode Plein écran, consultez [Paramètres Kiosque dans Windows 10 et versions ultérieures](kiosk-settings.md).

Un appareil plein écran exécute généralement une application ou un ensemble spécifique d’applications. Les utilisateurs ne peuvent pas accéder aux fonctionnalités ou fonctions sur l’appareil.

- **Mode kiosque** : Identifie le type de mode kiosque pris en charge par la stratégie. Les options sont les suivantes :

  - **Non configuré** (par défaut) : La stratégie n’active pas le mode kiosque sur l’appareil.
  - **Kiosque à application unique** : Le profil autorise l’appareil à exécuter une seule application. Quand l’utilisateur se connecte, une application spécifique démarre. Ce mode empêche également l’utilisateur d’ouvrir de nouvelles applications ou de basculer vers une autre application.
  - **Kiosque multi-application** : Le profil autorise l’appareil à exécuter de nombreuses applications. Seules les applications que vous ajoutez sont disponibles pour l’utilisateur. L’avantage des applications multiples plein écran ou d’un appareil à usage fixe est que l’utilisateur n’accède qu’aux applications dont il a besoin, les autres étant retirées de sa vue ; son expérience s’en trouve simplifiée.

#### <a name="single-app-kiosks"></a>Applications uniques plein écran

entrez les paramètres suivants :

- **Compte d’utilisateur** : Entrez le compte d’utilisateur local (pour l’appareil), un compte de domaine AD ou un compte Azure AD associé à l’application kiosque.
  - Compte local : Entrez-le au format `devicename\accountname`, `.\accountname` ou `accountname`
  - Compte de domaine : Entrez-le au format `domain\accountname`.
  - Compte AD Azure : Entrez-le au format `AzureAD\emailaddress`. Veillez à entrer « AzureAD », car c’est un nom de domaine fixe. Faites-le suivre de l’adresse e-mail d’Azure AD. Par exemple, entrez `AzureAD\user@contoso.onmicrosoft.com`.

    Pour les appareils plein écran dans des environnements publics où l’ouverture de session automatique est activée, un type d’utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Si vous utilisez un compte Azure AD pour le mode plein écran, veillez à entrer `AzureAD\user@yourorganization.com`.

- **Identifiant AUMID de l’application** : Entrez l’ID de modèle utilisateur de l’application (AUMID) à exécuter en mode kiosque. Pour plus d’informations, consultez [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Rechercher l’identifiant AUMID d’une application installée).

#### <a name="multi-app-kiosks"></a>Applications multiples plein écran

Les [Applications multiples plein écran](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) utilisent une configuration plein écran qui répertorie les applications autorisées et d’autres paramètres. 

Utilisez le bouton **Ajouter** pour créer une configuration plein écran (ou sélectionnez une configuration existante). Ensuite, entrez les paramètres suivants :

- **Nom de la configuration du mode Kiosque** : Entrez un nom convivial pour identifier la configuration.

- **Applications kiosque** : Entrez les applications qui sont disponibles dans le menu Démarrer. Les applications que vous ajoutez sont les seules que l’utilisateur peut ouvrir.

  - **Type d’application** : Choisissez le type de l’application kiosque :
    - **Applications Win32** : Application de bureau traditionnelle. Vous avez besoin du chemin qualifié complet de l’exécutable, en ce qui concerne l’appareil.
    - **Application UWP** : Application Windows universelle. Vous avez besoin de [l’identifiant AUMID de l’application](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

  - **Identificateur** : Entrez le chemin qualifié complet du fichier exécutable (applications Win32) ou [l’identifiant AUMID de l’application](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (applications UWP).

- **Barre des tâches** : Choisissez de montrer (**Activer**) la barre des tâches ou de la garder masquée (**Non configurée**) sur l’appareil kiosque.

- **Disposition du menu Démarrer** : Entrez un fichier XML qui décrit comment les applications s’affichent dans le menu Démarrer. [Personnaliser et exporter la disposition de l’écran de démarrage](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fournit quelques conseils et un exemple de code XML.

  [Créer une borne Windows10 qui exécute des applications](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) fournit plus de détails sur l’utilisation et la création de fichiers XML.

- **Utilisateurs attribués** : Ajoutez un ou plusieurs comptes d’utilisateurs qui peuvent utiliser les applications que vous ajoutez. Quand le compte se connecte, seules les applications définies dans la configuration sont disponibles. Le compte peut être local sur l’appareil, ou il peut s’agir d’un compte Azure AD associé à l’application kiosque.

    Pour les appareils plein écran dans des environnements publics où l’ouverture de session automatique est activée, un type d’utilisateur avec les privilèges minimum (par exemple, le compte d’utilisateur standard local) doit être utilisé. Pour configurer un compte Azure Active Directory (AD) pour le mode plein écran, utilisez le format `domain\user@tenant.com`.

## <a name="locked-screen-experience"></a>Expérience d’écran de verrouillage

- **Notifications du centre de notifications (mobile uniquement)**  : Active les notifications du Centre de notifications dans l’écran de verrouillage de l’appareil (Windows 10 Mobile uniquement).
- **URL de l’image de l’écran verrouillé (Desktop uniquement)**  : Entrez l’URL d’une image au format JPEG qui est utilisée comme papier peint de l’écran de verrouillage Windows. Les utilisateurs ne peuvent pas modifier ce paramètre.
- **Délai d’expiration de l’écran configurable par l’utilisateur (mobile uniquement)**  : Permet aux utilisateurs de configurer un délai d’expiration 
- **Cortana sur écran verrouillé (Desktop uniquement)**  : N’autorise pas l’utilisateur à interagir avec Cortana quand l’appareil est sur l’écran de verrouillage (Windows 10 Desktop uniquement).
- **Notifications toast sur écran verrouillé** : Bloque l’affichage des messages d’alerte sur l’écran de verrouillage de l’appareil.
- **Délai d’expiration de l’écran (mobile uniquement)**  : Spécifie la durée (en secondes) au bout de laquelle l’écran s’éteint après le verrouillage.

## <a name="messaging"></a>Messagerie

- **Synchronisation des messages (mobile uniquement)**  : Désactive Messages sur tous les appareils et sauvegarde/restaure les SMS.
- **MMS (mobile uniquement)**  : Désactive la fonctionnalité d’envoi/de réception de MMS sur l’appareil.
- **RCS (mobile uniquement)**  : Désactive la fonctionnalité d’envoi/de réception des services RCS (Rich Communication Services) sur l’appareil.

## <a name="microsoft-edge-browser"></a>Navigateur Microsoft Edge

### <a name="start-experience"></a>Expérience de démarrage

- **Démarrer Microsoft Edge avec** : Choisissez les pages qui s’ouvrent au démarrage de Microsoft Edge. Les options disponibles sont les suivantes :
  - **Pages de démarrage** : Microsoft Edge démarre avec la page de démarrage par défaut définie par le système d’exploitation
  - **Page Nouvel onglet** : Microsoft Edge charge ce qui est défini dans le paramètre **URL de la page Nouvel onglet**
  - **Page de la dernière session** : Microsoft Edge charge la page de la dernière session 
  - **Pages de démarrage personnalisées** : Microsoft Edge charge la page de démarrage définie par l’administrateur informatique
- **L’utilisateur peut changer les pages de démarrage** : L’option **Autoriser** permet aux utilisateurs de modifier les pages de démarrage. Les administrateurs peuvent utiliser `EdgeHomepageUrls` pour entrer les pages de démarrage que les utilisateurs voient par défaut lorsqu’ils ouvrent Microsoft Edge. **Non configuré** empêche les utilisateurs de modifier les pages de démarrage.
- **URL de la page Nouvel onglet** : Entrez l’URL pour ouvrir la page Nouvel onglet. Par exemple, entrez `https://www.bing.com`.
- **Ouvrir du contenu web sur la page Nouvel onglet** : Choisissez l’option **Bloquer** pour empêcher Microsoft Edge d’ouvrir un site web dans un nouvel onglet. Si l’option Bloquer est sélectionnée, le nouvel onglet s’ouvre vide. **Non configuré** utilise le comportement par défaut du système d’exploitation sur l’appareil, ce qui peut permettre aux utilisateurs de choisir ce qui est affiché.
- **Bouton Accueil** : Choisissez ce qui doit se passer lorsque le bouton Accueil est sélectionné. Les options disponibles sont les suivantes :
  - **Pages de démarrage** : L’option que vous avez choisie pour le paramètre **Démarrer Microsoft Edge avec** s’ouvre
  - **Page Nouvel onglet** : L’option que vous avez choisie pour le paramètre **URL de la page Nouvel onglet** s’ouvre
  - **URL du bouton d’accueil personnalisé** : L’option que vous avez choisie pour le paramètre **URL du bouton Démarrage** s’ouvre
  - **Masquer le bouton d’accueil** : Masque le bouton d’accueil
- **L’utilisateur peut changer le bouton d’accueil** : L’option **Autoriser** permet aux utilisateurs de modifier le bouton d’accueil. Les modifications de l’utilisateur remplacent les paramètres de l’administrateur pour le bouton Accueil. **Non configuré** utilise le comportement par défaut du système d’exploitation sur l’appareil, ce qui empêcher les utilisateurs de changer la façon dont l’administrateur a configuré le bouton Accueil.
- **Afficher la page de la première utilisation** : L’option **Empêcher** empêche l’affichage de la page de présentation lors de la première exécution de Microsoft Edge. Cette fonctionnalité permet aux entreprises, notamment celles inscrites dans les configurations zéro émissions, de bloquer cette page. **Non configuré** affiche la page d’introduction.
  - **URL de la première utilisation** : Entrez l’URL de la page à afficher la première fois qu’un utilisateur exécute Microsoft Edge (Windows 10 Mobile uniquement).
- **Fenêtres contextuelles** : Choisissez l’option **Bloquer** pour bloquer les fenêtres indépendantes dans le navigateur. S’applique à Windows 10 Desktop uniquement. L’option **Non configuré** autorise les fenêtres contextuelles dans le navigateur web.
- **Envoyer le trafic intranet à Internet Explorer** : L’option **Autoriser** permet aux utilisateurs d’ouvrir des sites web intranet dans Internet Explorer au lieu de Microsoft Edge (Windows 10 Desktop uniquement). **Non configuré** autorise les utilisateurs à afficher Microsoft Edge.
- **Emplacement de la liste de sites en mode Entreprise** : Entrez l’URL qui inclut la liste des sites web qui s’ouvrent en mode Entreprise. Les utilisateurs ne peuvent pas modifier cette liste. S’applique à Windows 10 Desktop uniquement.
- **Message lors de l’ouverture de sites dans Internet Explorer** : Utilisez ce paramètre pour configurer Microsoft Edge afin d’afficher une notification avant l’ouverture d’un site dans Internet Explorer 11. Les options disponibles sont les suivantes :
  - **Non configuré** : Le comportement par défaut du système d’exploitation est utilisé, ce qui peut ne pas afficher un message.
  - **Afficher le message sans l’option permettant d’ouvrir des sites dans Microsoft Edge** : Affiche le message lors de l’ouverture des sites dans Internet Explorer. Les sites s’ouvrent dans Internet Explorer. Il n’y a pas d’option pour ouvrir des sites dans Microsoft Edge.
  - **Afficher un message lors de l’ouverture de sites dans Microsoft Edge** : Affiche le message lors de l’ouverture des sites dans Internet Explorer. Le message inclut un lien **Poursuivre dans Microsoft Edge** qui permet aux utilisateurs de Microsoft Edge au lieu d’Internet Explorer.

  > [!IMPORTANT]
  > Ce paramètre requiert que vous activiez l’option **Configurer la liste des sites en Mode entreprise**, l’option **Envoyer tous les sites intranet vers Internet Explorer 11**, ou les deux.

- **Liste de compatibilité Microsoft** : L’option **Bloquer** empêche l’affichage de la liste de compatibilité Microsoft dans Microsoft Edge. Cette liste de Microsoft permet à Microsoft Edge d’afficher correctement les sites ayant des problèmes de compatibilité connus. **Non configuré** permet l’utilisation d’une liste de compatibilité de Microsoft.
- **Précharger les pages de démarrage et la page Nouvel onglet** : Choisissez l’option **Bloquer** pour empêcher Microsoft Edge de précharger les pages de démarrage et la page Nouvel onglet. Le préchargement réduit le temps de démarrage de Microsoft Edge et de chargement d’un nouvel onglet. **Non configuré** utilise le comportement par défaut du système d’exploitation, qui peut être de précharger ces pages.
- **Prélancer les pages de démarrage et la page Nouvel onglet** : Choisissez l’option **Bloquer** pour empêcher Microsoft Edge de prélancer les pages de démarrage et la page Nouvel onglet. Le prélancement aide les performances de Microsoft Edge et réduit le temps nécessaire pour démarrer Microsoft Edge. **Non configuré** utilise le comportement par défaut du système d’exploitation, qui peut être de prélancer ces pages.

### <a name="favorites-and-search"></a>Favoris et recherche

- **Volet des favoris** : Choisissez ce qui doit se passer pour les favoris de n’importe quelle page Microsoft Edge. Les options disponibles sont les suivantes :
  - **Non configuré** : Utilise le comportement par défaut du système d’exploitation, qui peut être de masquer le volet des favoris dans toutes les pages. L’utilisateur peut modifier ce paramètre.
  - **Masquer** : Masque le volet des favoris dans toutes les pages. L’utilisateur ne peut pas modifier ce paramètre.
  - **Afficher** : Affiche le volet des favoris dans toutes les pages. L’utilisateur ne peut pas modifier ce paramètre.
- **Liste de favoris** : Ajoutez une liste d’URL au fichier des favoris. Par exemple, ajoutez `http://contoso.com/favorites.html`.
- **Limiter les modifications des favoris** : Choisissez l’option **Bloquer** pour empêcher les utilisateurs d’ajouter, d’importer, de trier ou de modifier la liste des favoris. **Non configuré** utilise le comportement par défaut du système d’exploitation, ce qui peut permettre aux utilisateurs de modifier la liste.
- **Synchroniser les favoris entre les navigateurs Microsoft (Desktop uniquement)**  : L’option **Exiger** force Windows à synchroniser les favoris entre Internet Explorer et Microsoft Edge. Les ajouts, suppressions, modifications et changements d’ordre dans les favoris sont partagés entre les navigateurs.  **Non configuré** utilise le comportement par défaut du système d’exploitation, ce qui peut donner aux utilisateurs le choix de synchroniser les favoris entre les navigateurs.
- **Moteur de recherche par défaut** : Choisissez le moteur de recherche par défaut sur l’appareil. Les utilisateurs finaux peuvent modifier cette valeur à tout moment. Les options disponibles sont les suivantes :
  - Par défaut
  - Bing
  - Google
  - Yahoo
  - Valeur personnalisée
- **Suggestions de recherche** : L’option **Non configuré** permet à votre moteur de recherche de suggérer des sites à mesure que vous saisissez des expressions de recherche dans la barre d’adresses. L’option **Bloquer** empêche cette fonctionnalité.

### <a name="privacy-and-security"></a>Confidentialité et sécurité

- **Navigation InPrivate** : L’option **Bloquer** empêche l’utilisateur final d’ouvrir des sessions de navigation InPrivate. L’option **Non configuré** autorise cette fonctionnalité.
- **Enregistrer l’historique de navigation** : L’option **Bloquer** empêche Microsoft Edge d’enregistrer l’historique de navigation. L’option **Non configuré** autorise l’enregistrement de l’historique de navigation.
- **Effacer les données de navigation en quittant (Desktop uniquement)**  : L’option **Exiger** efface l’historique et les données de navigation quand l’utilisateur quitte Microsoft Edge. **Non configuré** utilise le comportement par défaut du système d’exploitation, ce qui peut mettre en cache les données de navigation.
- **Synchroniser les paramètres de navigateur entre les appareils de l’utilisateur** : Choisissez la façon dont vous souhaitez synchroniser les paramètres de navigateur entre les appareils. Les options disponibles sont les suivantes :
  - **Autoriser** : Autorise la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur
  - **Bloquer et activer le remplacement utilisateur**: Bloque la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur. Les utilisateurs peuvent remplacer ce paramètre.
  - **Bloquer** : Bloque la synchronisation des paramètres du navigateur Microsoft Edge entre les appareils de l’utilisateur. Les utilisateurs ne peuvent pas remplacer ce paramètre.
- **Gestionnaire de mots de passe** : L’option **Bloquer** désactive la fonctionnalité Gestionnaire de mots de passe Microsoft Edge. L’option **Non configuré** autorise cette fonctionnalité.
- **Cookies** : Choisissez la façon dont les cookies sont gérés dans le navigateur web. Les options disponibles sont les suivantes :
  - **Autoriser** : Les cookies sont stockés sur l’appareil.
  - **Bloquer tous les cookies** : Les cookies ne sont pas stockés sur l’appareil.
  - **Bloquer uniquement les cookies tiers** : Les cookies tiers ou de partenaire ne sont pas stockés sur l’appareil.
- **Remplissage automatique** : L’option **Bloquer** désactive la fonctionnalité de remplissage automatique sur l’appareil. **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur (Windows 10 Desktop uniquement).
- **Envoyer des en-têtes Do Not Track** : L’option **Non configuré** exige que les appareils envoient des en-têtes Do Not Track aux sites web exigeant des informations de suivi (recommandé). Choisir **Bloquer** pour empêcher l’appareil d’envoyer ces en-têtes, ce qui permet aux sites web d’effectuer le suivi de l’utilisateur.
- **Adresse IP localhost WebRTC** : L’option **Bloquer** empêche l’affichage de l’adresse IP localhost des utilisateurs lors d’appels téléphoniques effectués à l’aide du protocole RTC web. **Non configuré** permet d’afficher l’adresse IP localhost des utilisateurs lors d’appels téléphoniques effectués à l’aide de ce protocole.
- **Collecte de données pour les vignettes dynamiques** : Choisissez l’option **Bloquer** pour empêcher Windows de collecter des informations sur la vignette dynamique quand un site est épinglé au menu Démarrer dans Microsoft Edge. **Non configuré** autorise la collecte de ces informations.
- **L’utilisateur peut remplacer les erreurs de certificat** : L’option **Bloquer** empêche les utilisateurs d’accéder à des sites web qui contiennent des erreurs SSL ou TLS. **Non configuré** autorise les utilisateurs à accéder à ces sites.

### <a name="additional"></a>Supplémentaire

- **Navigateur Microsoft Edge (Mobile uniquement)**  : Choisissez l’option **Bloquer** pour empêcher l’utilisation de Microsoft Edge sur l’appareil. Si vous bloquez Microsoft Edge, les paramètres individuels s’appliquent uniquement au bureau. **Non configuré** autorise l’utilisation du navigateur Microsoft Edge sur l’appareil.
- **Liste déroulante des barres d’adresse (Desktop uniquement)**  : L’option **Bloquer** empêche Microsoft Edge d’afficher une liste de suggestions dans une liste déroulante à mesure que vous tapez. Cette option aide à réduire la bande passante réseau entre Microsoft Edge et les services Microsoft. **Non configuré** autorise Microsoft Edge afficher une liste de suggestions.
- **Plein écran** : Choisissez l’option **Bloquer** pour empêcher Microsoft Edge d’afficher uniquement le contenu web et de masquer Microsoft Edge (mode plein écran). **Non configuré** utilise la valeur par défaut du système d’exploitation, ce qui permet à Microsoft Edge d’utiliser le mode plein écran.
- **À propos des indicateurs** : L’option **Bloquer** empêche les utilisateurs finaux d’accéder à la page `about:flags` de Microsoft Edge qui inclut les paramètres expérimentaux et de développement. **Non configuré** utilise la valeur par défaut du système d’exploitation, ce qui peut permettre l’accès à la page `about:flags`.
- **Outils de développement** : L’option **Bloquer** empêche l’utilisateur final d’ouvrir les outils de développement Microsoft Edge. **Non configuré** permet aux utilisateurs d’ouvrir les outils de développement.
- **Extensions** : L’option **Non configuré** autorise l’utilisateur final à installer des extensions Microsoft Edge sur l’appareil. L’option **Bloquer** empêche l’installation.
- **Chargement indépendant des extensions de développement** : L’option **Bloquer** empêche Microsoft Edge d’effectuer un chargement indépendant, qui permet d’installer et d’exécuter des extensions non vérifiées à l’aide de la fonctionnalité **Charger des extensions**. **Non configuré** utilise la valeur par défaut du système d’exploitation, ce qui peut autoriser le chargement indépendant.
- **Extensions nécessaires** : Choisissez les extensions qui ne peuvent pas être désactivées par les utilisateurs finaux dans Microsoft Edge. Entrez les noms des familles de packages, puis sélectionnez **Ajouter**. Les listes [Rechercher le nom d’une famille de packages (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) offrent quelques conseils.

  Vous pouvez également **importer** un fichier CSV qui inclut les noms des familles de packages.

- **JavaScript** : Choisissez l’option **Bloquer** pour empêcher que les scripts Java du navigateur ne s’exécutent sur l’appareil. **Non configuré** autorise l’exécution de scripts, tels que JavaScript, dans le navigateur Microsoft Edge.

## <a name="network-proxy"></a>Proxy réseau

- **Détecter automatiquement les paramètres du proxy** : Quand cette option est activée, l’appareil tente de trouver le chemin d’un script PAC.
- **Utiliser un script de proxy** : Sélectionnez cette option pour entrer le chemin d’un script PAC afin de configurer le serveur proxy.
  - **URL de l’adresse du script de configuration** : Entrez l’URL d’un script PAC que vous souhaitez utiliser pour configurer le serveur proxy.
- **Utiliser un serveur proxy manuel** : Sélectionnez cette option pour entrer manuellement les informations du serveur proxy.
  - **Adresse** : Entrez le nom ou l’adresse IP du serveur proxy.
  - **Numéro de port** : Entrez le numéro de port de votre serveur proxy.
  - **Exceptions du proxy** : Entrez les URL qui ne doivent pas utiliser le serveur proxy. Utilisez des points-virgules pour séparer chaque élément.
  - **Ignorer le serveur proxy pour les adresses locales** : Si vous ne souhaitez pas utiliser le serveur proxy pour les adresses locales sur votre intranet, activez cette option.

## <a name="password"></a>Mot de passe

- **Mot de passe** : Demande à l’utilisateur final de saisir un mot de passe pour pouvoir accéder à l’appareil.
  - **Type de mot de passe requis** : Spécifie si le mot de passe doit être numérique uniquement ou alphanumérique.
  - **Longueur minimale du mot de passe** : S’applique à Windows 10 Mobile uniquement.
  - **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : Pour les appareils exécutant Windows 10 : Si BitLocker est activé sur l’appareil, ce dernier passe en mode de récupération BitLocker après le nombre d’échecs de connexion que vous avez spécifié. Si BitLocker n’est pas activé sur l’appareil, alors ce paramètre ne s’applique pas. Pour les appareils exécutant Windows 10 Mobile : Après le nombre d’échecs de connexion que vous spécifiez, l’appareil est réinitialisé.
  - **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** : Spécifie la durée pendant laquelle l’appareil doit être inactif avant que l’écran de veille se verrouille.
  - **Expiration du mot de passe (en jours)** : Spécifie la durée après laquelle le mot de passe d'un appareil doit être modifié.
  - **Empêcher la réutilisation des mots de passe précédents** : Spécifie le nombre de mots de passe précédemment utilisés conservés par l’appareil.
  - **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (mobile uniquement)**  : Spécifie que l’utilisateur doit entrer un mot de passe pour déverrouiller l’appareil (Windows 10 Mobile uniquement).
  - **Mots de passe simples** : Permet d’utiliser des mots de passe simples, tels que 1111 ou 1234. Ce paramètre autorise ou bloque également l’utilisation des mots de passe d’image Windows.
- **Chiffrement** : Active le chiffrement sur les appareils ciblés.

## <a name="per-app-privacy-exceptions"></a>Exceptions de confidentialité par application

Vous pouvez ajouter des applications qui doivent avoir un comportement de confidentialité différent de celui défini dans « Confidentialité par défaut ».

- **Nom du package** : Nom de la famille du package d’application.
- **Nom de l’application** : Nom de l’application.

### <a name="exceptions"></a>Exceptions

- **Informations de compte** : Définissez si cette application peut accéder au nom, à la photo et à d’autres informations de contact de l’utilisateur.
- **Applications en arrière-plan** : Définissez si cette application peut s’exécuter en arrière-plan.
- **Calendrier** : Définissez si cette application peut accéder au calendrier.
- **Historique des appels** : Définissez si cette application peut accéder à l’historique de mes appels.
- **Appareil photo** : Définissez si cette application peut accéder à l’appareil photo.
- **Contacts** : Définissez si cette application peut accéder aux contacts.
- **E-Mail** : Définissez si cette application peut accéder aux e-mails et en envoyer.
- **Emplacement** : Définissez si cette application peut accéder aux informations de localisation.
- **Messagerie** : Définissez si cette application peut lire ou envoyer des SMS ou MMS.
- **Microphone** : Définissez si cette application peut utiliser le microphone.
- **Mouvement** : Définissez si cette application peut accéder aux informations de mouvement de l’appareil.
- **Notifications** : Définissez si cette application peut accéder aux notifications.
- **Téléphone** : Définissez si cette application peut accéder au téléphone.
- **Radios** : Certaines applications utilisent des signaux radio (comme Bluetooth) sur votre appareil pour envoyer et recevoir des données, et doivent activer et désactiver ces signaux radio. Définissez si cette application peut contrôler ces signaux radio.
- **Tâches** : Définissez si cette application peut accéder à vos tâches.
- **Appareils de confiance** : Choisissez si cette application peut utiliser des appareils approuvés (matériel déjà connecté) ou du matériel fourni avec l’appareil. Par exemple, utilisez des téléviseurs, des projecteurs, etc. comme appareils de confiance.
- **Commentaires et diagnostics** : Définissez si cette application peut accéder aux informations de diagnostic.
- **Synchronisation avec des appareils** : Choisissez si cette application peut automatiquement partager et synchroniser des informations avec des appareils sans fil qui ne sont pas explicitement appairés à l’appareil.

## <a name="personalization"></a>Personalization

- **URL de l’image d’arrière-plan du poste de travail (Desktop uniquement)**  : Entrez l’URL d’une image au format JPEG que vous souhaitez utiliser comme papier peint du Bureau Windows. Les utilisateurs ne peuvent pas changer d’image.

## <a name="printer"></a>Imprimante

- **Imprimantes** : Liste des imprimantes locales qui ont été ajoutées.
- **Imprimante par défaut** : Définissez l’imprimante par défaut.
- **Accès utilisateur à l’ajout de nouvelles imprimantes** : Autorisez ou bloquez l’utilisation des imprimantes locales.

## <a name="privacy"></a>Confidentialité

- **Personnalisation des entrées** : N’autorisez pas l’utilisation des services cloud de reconnaissance vocale pour les applications du Microsoft Store, la dictée ou Cortana. Si vous autorisez ces services, Microsoft peut collecter des données vocales pour améliorer le service.
- **Acceptation automatique des invites de consentement de l’utilisateur pour le couplage et la confidentialité** : Autorisez Windows à accepter automatiquement les messages de consentement du couplage et de la confidentialité lors de l’exécution des applications.
- **Publier les activités de l’utilisateur** : L’option **Bloquer** empêche les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches.
- **Activités locales uniquement** : L’option **Bloquer** empêche les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches en fonction uniquement de l’activité locale.

Vous pouvez configurer les informations auxquelles toutes les applications sur l’appareil peuvent accéder. Vous pouvez définir des exceptions pour chaque application à l’aide de l’option **Exceptions de confidentialité par application**.

### <a name="exceptions"></a>Exceptions

- **Informations de compte** : Définissez si cette application peut accéder au nom, à la photo et à d’autres informations de contact de l’utilisateur.
- **Applications en arrière-plan** : Définissez si cette application peut s’exécuter en arrière-plan.
- **Calendrier** : Définissez si cette application peut accéder au calendrier.
- **Historique des appels** : Définissez si cette application peut accéder à l’historique de mes appels.
- **Appareil photo** : Définissez si cette application peut accéder à l’appareil photo.
- **Contacts** : Définissez si cette application peut accéder aux contacts.
- **E-Mail** : Définissez si cette application peut accéder aux e-mails et en envoyer.
- **Emplacement** : Définissez si cette application peut accéder aux informations de localisation.
- **Messagerie** : Définissez si cette application peut lire ou envoyer des SMS ou MMS.
- **Microphone** : Définissez si cette application peut utiliser le microphone.
- **Mouvement** : Définissez si cette application peut accéder aux informations de mouvement de l’appareil.
- **Notifications** : Définissez si cette application peut accéder aux notifications.
- **Téléphone** : Définissez si cette application peut accéder au téléphone.
- **Radios** : Certaines applications utilisent des signaux radio (comme Bluetooth) sur votre appareil pour envoyer et recevoir des données, et doivent activer et désactiver ces signaux radio. Définissez si cette application peut contrôler ces signaux radio.
- **Tâches** : Définissez si cette application peut accéder à vos tâches.
- **Appareils de confiance** : Choisissez si cette application peut utiliser des appareils de confiance. Les appareils de confiance sont des appareils déjà connectés ou ayant été fournis avec l’appareil. Par exemple, utilisez des téléviseurs, des projecteurs, et ainsi de suite comme appareils approuvés.
- **Commentaires et diagnostics** : Choisissez si cette application peut accéder aux informations de diagnostic.
- **Synchroniser avec les appareils** - Définir si cette application peut automatiquement partager et synchroniser des informations avec des appareils sans fil qui ne sont pas explicitement jumelés avec ce PC, cette tablette ou ce téléphone.

## <a name="projection"></a>Projection

- **Entrées utilisateur à partir de récepteurs d’affichage sans fil** : Empêche l’entrée utilisateur à partir du récepteur d’affichage sans fil.
- **Projection sur ce PC** : Empêche les autres appareils de trouver le PC pour la projection.
- **Exiger un code PIN pour l’appairage** : Exige un code PIN lors de la connexion à un projecteur.

## <a name="reporting-and-telemetry"></a>Création de rapports et les données de télémétrie

- **Partager les données d’utilisation** : Choisissez le niveau des données de diagnostic qui sont envoyées. Les options disponibles sont les suivantes :
  - Sécurité
  - Basique
  - Étendu
  - Complète
- **Envoyer des données de navigation Microsoft Edge à Microsoft 365 Analytics** : Pour utiliser cette fonctionnalité, définissez les paramètres **Partager les données d’utilisation** sur **Amélioré** ou **Complet**. Cette fonctionnalité contrôle les données que Microsoft Edge envoie à Microsoft 365 Analytics pour les appareils d’entreprise avec un ID commercial configuré. Les options disponibles sont les suivantes :
  - **Non configuré** : Utilise la valeur par défaut du système d’exploitation, ce qui peut n’envoyer aucune donnée concernant l’historique de navigation
  - **Envoyer uniquement les données intranet** : Permet à l’administrateur d’envoyer l’historique des données intranet.
  - **Envoyer uniquement les données Internet** : Permet à l’administrateur d’envoyer l’historique des données Internet.
  - **Envoyer les données intranet et Internet** : Permet à l’administrateur d’envoyer l’historique des données intranet et Internet.
- **Serveur proxy de télémétrie** : Entrez le nom de domaine complet (FQDN) ou l’adresse IP d’un serveur proxy pour transférer les demandes Expériences des utilisateurs connectés et télémétrie à l’aide d’une connexion SSL. Le format de ce paramètre est *serveur*:*port*. En cas d'échec du proxy nommé ou si aucun proxy n'est entré à l'activation de cette stratégie, les données Expériences des utilisateurs connectés et télémétrie ne sont pas envoyées et restent sur l'appareil local.

  Exemples de formats :

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Recherche

- **Recherche sécurisée (mobile uniquement)**  : Contrôlez la manière dont Cortana filtre les contenus pour adultes dans les résultats de recherche. Vous pouvez sélectionner **Strict** ou **Modéré**, ou encore autoriser l’utilisateur à choisir ses propres paramètres.
- **Afficher les résultats web dans la recherche** : Empêchez ou autorisez l’affichage des résultats web dans les recherches effectuées sur l’appareil.

## <a name="start"></a>Démarrer

- **Disposition du menu Démarrer** : Pour personnaliser le menu Démarrer sur les appareils de bureau, vous pouvez charger un fichier XML qui inclut vos personnalisations, notamment l’ordre dans lequel les applications sont listées. Les utilisateurs ne peuvent pas changer la disposition du menu Démarrer que vous entrez.
- **Épingler des sites web à des vignettes dans le menu Démarrer** : Importez des images provenant de Microsoft Edge et affichez-les sous forme de liens dans le menu Démarrer de Windows pour les appareils de bureau.
- **Désépingler les applications de la barre des tâches** : Choisissez **Bloquer** pour empêcher l’utilisateur de désépingler des applications du menu Démarrer.
- **Changement rapide d’utilisateur** : Choisissez **Bloquer** pour empêcher le passage d’un utilisateur connecté à un autre sans déconnexion.
- **Applications les plus utilisées** : Choisissez **Bloquer** pour ne pas afficher les applications les plus utilisées dans le menu Démarrer. Le bouton bascule correspondant dans l’application Paramètres est également désactivé.
- **Applications ajoutées récemment** : Choisissez **Bloquer** pour ne pas afficher les applications ajoutées récemment dans le menu Démarrer. Le bouton bascule correspondant dans l’application Paramètres est également désactivé.
- **Mode de l’écran de démarrage** : Choisissez comment afficher l’écran de démarrage. Vous avez le choix entre **Plein écran** et **Ne pas utiliser le plein écran**.
- **Éléments ouverts récemment dans les listes de raccourcis** : Choisissez **Bloquer** pour ne pas afficher les listes de raccourcis dans le menu Démarrer et la barre des tâches. Le bouton bascule correspondant dans l’application Paramètres est également désactivé.
- **Liste d’applications** : Choisissez comment afficher l’application Paramètres. Les options disponibles sont les suivantes : 
  - Réduire
  - Réduire et désactiver l’application Paramètres 
  - Supprime et désactive l’application Paramètres
- **Bouton d’alimentation** : Choisissez **Bloquer** pour ne pas afficher le bouton d’alimentation dans le menu Démarrer.
- **Vignette de l’utilisateur** : Choisissez **Bloquer** pour ne pas afficher la vignette de l’utilisateur dans le menu Démarrer.
  - **Verrouiller** : Choisissez **Bloquer** pour ne pas afficher l’option `Lock` dans la vignette de l’utilisateur du menu Démarrer.
  - **Se déconnecter** : Choisissez **Bloquer** pour ne pas afficher l’option `Sign out` dans la vignette de l’utilisateur du menu Démarrer.
- **Arrêter** : Choisissez **Bloquer** pour ne pas afficher les options `Update and shut down` et `Shut down` dans le bouton d’alimentation du menu Démarrer.
- **Veille** : Choisissez **Bloquer** pour ne pas afficher l’option `Sleep` dans le bouton d’alimentation du menu Démarrer.
- **Mise en veille prolongée** : Choisissez **Bloquer** pour ne pas afficher l’option `Hibernate` dans le bouton d’alimentation du menu Démarrer.
- **Changer de compte** : Choisissez **Bloquer** pour empêcher `Switch account` de s’afficher dans la vignette utilisateur, dans le menu Démarrer.
- **Options de redémarrage** :  Choisissez **Bloquer** pour ne pas afficher les options `Update and restart` et `Restart` dans le bouton d’alimentation du menu Démarrer.
- **Documents sur Démarrer** : Masquez ou affichez le dossier Documents dans le menu Démarrer de Windows.
- **Téléchargements sur Démarrer** : Masquez ou affichez le dossier Téléchargements dans le menu Démarrer de Windows.
- **Explorateur de fichiers sur Démarrer** : Masquez ou affichez l’application Explorateur de fichiers dans le menu Démarrer de Windows.
- **Groupe résidentiel sur Démarrer** : Masquez ou affichez le dossier Groupe résidentiel dans le menu Démarrer de Windows.
- **Musique sur Démarrer** : Masquez ou affichez le dossier Musique dans le menu Démarrer de Windows.
- **Réseau sur Démarrer** : Masquez ou affichez le dossier Réseau dans le menu Démarrer de Windows.
- **Dossier Personnel sur Démarrer** : Masquez ou affichez le dossier Personnel dans le menu Démarrer de Windows.
- **Images sur Démarrer** : Masquez ou affichez le dossier Images dans le menu Démarrer de Windows.
- **Paramètres sur Démarrer** : Masquez ou affichez le dossier Paramètres dans le menu Démarrer de Windows.
- **Vidéos sur Démarrer** : Masquez ou affichez le dossier Vidéos dans le menu Démarrer de Windows.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen pour Microsoft Edge** : Activer Microsoft Edge SmartScreen pour accéder au site et aux téléchargements de fichiers.
- **Accès à un site malveillant** : Empêchez les utilisateurs d’ignorer les avertissements concernant le filtre Windows Defender SmartScreen et d’accéder au site.
- **Téléchargement des fichiers non vérifiés** : Empêchez les utilisateurs d’ignorer les avertissements concernant le filtre Windows Defender SmartScreen et de télécharger des fichiers non vérifiés.

## <a name="windows-spotlight"></a>Windows à la une

- **Windows à la une** : Utilisez ce paramètre pour bloquer toutes les fonctionnalités Windows à la une sur les appareils Windows 10. Si vous bloquez ce paramètre, les paramètres suivants ne sont pas disponibles :
  - **Windows à la une sur l’écran de verrouillage** : Empêchez Windows à la une d’afficher des informations sur l’écran de verrouillage de l’appareil.
  - **Suggestions de tiers dans Windows à la une** : Empêchez Windows à la une de suggérer du contenu qui n’est pas publié par Microsoft.
  - **Fonctionnalités grand public** : Permet de bloquer certaines fonctionnalités grand public, comme l’affichage de suggestions sur le menu Démarrer ou encore les notifications d’appartenance.
  - **Conseils Windows** : Permet de bloquer l’affichage des info-bulles dans Windows.
  - **Windows à la une dans le centre de notifications** : Empêchez l’affichage des suggestions de Windows à la une, telles que le nouveau contenu de sécurité ou d’application, dans le Centre de notifications de Windows.
  - **Personnalisation de Windows à la une** : Empêche Windows à la une de personnaliser les résultats en fonction de l’utilisation d’un appareil.
  - **Écrans d’accueil de Windows** : Bloquez l’expérience d’accueil de Windows qui montre à l’utilisateur des informations sur les fonctionnalités nouvelles ou mises à jour.

## <a name="windows-defender-antivirus"></a>Antivirus Windows Defender

- **Surveillance en temps réel** : Active la recherche en temps réel des logiciels malveillants, logiciels espions et autres logiciels indésirables.
- **Analyse du comportement** : Permet à Defender de rechercher certains modèles connus d'activité suspecte sur les appareils.
- **Système NIS (Network Inspection System)**  : Le système NIS vous permet de vous protéger contre les attaques réseau. Il utilise les signatures de vulnérabilités connues fournies par le Microsoft Endpoint Protection Center pour faciliter la détection et le blocage du trafic malveillant.
- **Analyser tous les téléchargements** : Contrôle si Defender analyse tous les fichiers téléchargés depuis Internet.
- **Analyser les scripts chargés dans les navigateurs web Microsoft** : Configure Defender pour analyser les scripts utilisés dans Internet Explorer Defender.
- **Accès de l’utilisateur final à Defender** : Détermine si l'interface utilisateur de Windows Defender est masquée aux utilisateurs finaux. Quand ce paramètre est modifié, le changement est appliqué au prochain redémarrage de l’ordinateur de l’utilisateur final.
- **Intervalle de mise à jour des signatures (en heures)**  : Spécifiez l’intervalle auquel Defender doit vérifier les nouveaux fichiers de signature.
- **Surveiller l’activité des fichiers et des programmes** : Autorise Defender à surveiller l’activité des fichiers et des programmes sur des appareils.
- **Nombre de jours avant la suppression des programmes malveillants en quarantaine** : Permet à Defender de continuer à suivre les logiciels malveillants résolus pendant un certain nombre de jours que vous spécifiez, pour vous permettre de vérifier manuellement les appareils affectés. Si vous définissez le nombre de jours du suivi sur **0**, les logiciels malveillants restent dans le dossier de quarantaine et ne sont pas automatiquement supprimés.
- **Limite de l’utilisation du processeur pendant une analyse** : Vous permet de limiter la quantité de ressources du processeur que les analyses sont autorisées à utiliser (de **1** à **100**).
- **Analyser les fichiers d’archive** : Permet à Defender d'analyser les fichiers archivés tels que les archives Zip ou Cab.
- **Analyser les e-mails entrants** : Permet à Defender d’analyser les messages électroniques lorsqu'ils arrivent sur l’appareil.
- **Analyser les disques amovibles lors d’une analyse complète** : Permet à Defender d'analyser les lecteurs amovibles tels que les clés USB.
- **Analyser les lecteurs réseau mappés lors d’une analyse complète** : Permet à Defender d’analyser les fichiers sur un lecteur réseau mappé.
  Si les fichiers sur le lecteur sont en lecture seule, Defender ne peut pas supprimer les logiciels malveillants détectés dans ces fichiers.
- **Analyser les fichiers ouverts à partir de dossiers réseau** : Permet à Defender d’analyser les fichiers sur des lecteurs réseau partagés (par exemple, les fichiers accessibles à partir d’un chemin UNC). Si les fichiers sur le lecteur sont en lecture seule, Defender ne peut pas supprimer les logiciels malveillants détectés dans ces fichiers.
- **Protection du cloud** : Autorise ou empêche Microsoft Active Protection Service de recevoir des informations sur l’activité des logiciels malveillants en provenance des appareils que vous gérez. Ces informations serviront à améliorer le service.
- **Demander confirmation aux utilisateurs avant l’envoi d’un échantillon** : Contrôle si les fichiers potentiellement malveillants susceptibles de nécessiter une analyse plus approfondie sont envoyés automatiquement à Microsoft.
- **Heure de l’analyse rapide quotidienne** : Permet de planifier une analyse rapide exécutée tous les jours à l’heure de votre choix.
- **Type d’analyse système à effectuer** : Entrez le niveau d’analyse qui doit être utilisé quand vous planifiez une analyse système.
- **Détecter les applications potentiellement indésirables** : Choisissez le niveau de protection quand Windows détecte des applications potentiellement indésirables, parmi les niveaux suivant :
  - **Bloquer**
  - **Audit** Pour plus d’informations sur les applications potentiellement indésirables, consultez [Détecter et bloquer les applications potentiellement non désirées](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Actions en cas de détection de menaces de programmes malveillants** : Utilisez cette option pour choisir les actions que Defender doit exécuter pour chaque niveau de menace détecté (faible, modéré, élevé et grave). Les options disponibles sont les suivantes :
  - **Nettoyer**
  - **Quarantaine**
  - **Supprimer**
  - **Autoriser**
  - **Défini par l’utilisateur**
  - **Bloquer**

### <a name="windows-defender-antivirus-exclusions"></a>Exclusions de l’antivirus Windows Defender

- **Fichiers et dossiers à exclure des analyses et de la protection en temps réel** : Ajoute un ou plusieurs fichiers et dossiers comme **C:\Chemin** ou **%ProgramFiles%\Chemin\NomFichier.exe** à la liste des exclusions. Ces fichiers et dossiers ne sont pas inclus dans les analyses en temps réel ou planifiées.
- **Extensions de fichier à exclure des analyses et de la protection en temps réel** : Ajoutez une ou plusieurs extensions de fichier comme **jpg** ou **txt** à la liste des exclusions. Tous les fichiers avec ces extensions ne sont pas inclus dans les analyses en temps réel ou planifiées.
- **Processus à exclure des analyses et de la protection en temps réel** : Ajoutez un ou plusieurs processus du type **.exe**, **.com**, ou **.scr** à la liste des exclusions. Ces processus ne sont pas inclus dans les analyses en temps réel ou planifiées.

## <a name="next-steps"></a>Étapes suivantes

Pour plus de détails techniques sur chaque paramètre et sur les éditions de Windows prises en charge, consultez [Référence CSP de stratégie Windows 10](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider).
