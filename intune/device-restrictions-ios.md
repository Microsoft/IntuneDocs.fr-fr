---
title: Paramètres de restrictions d’appareil Microsoft Intune pour iOS
titleSuffix: ''
description: Découvrez les paramètres Intune qui vous permettent de contrôler les paramètres et les fonctionnalités des appareils exécutant iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 71ed2458e35934de9da297140d49d6d4128b0784
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329816"
---
# <a name="microsoft-intune-ios-device-restriction-settings"></a>Paramètres de restriction des appareils iOS de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article décrit les paramètres des restrictions d’appareils Microsoft Intune que vous pouvez configurer pour les appareils exécutant iOS.

## <a name="general"></a>Général

-   **Partager des données d’utilisation** : autorisez ou bloquez l’appareil à partir de l’envoi de données de télémétrie de diagnostic et d’utilisation à Apple.
-   **Envoi des données de diagnostic** : autoriser ou bloquer l’envoi de données de diagnostic à Apple depuis l’appareil.
-   **Capture d'écran** : permet à l’utilisateur de capturer le contenu de l’écran en tant qu’image.
    - **Observation des écrans à distance par l’application En classe (mode supervisé uniquement)** : autoriser ou bloquer l’affichage par l’application En classe d’Apple de l’écran des appareils iOS.
    - **Observation des écrans sans invite par l’application En classe (mode supervisé uniquement)**  : s’ils sont autorisés, les enseignants peuvent observer en mode silencieux l’écran des appareils iOS des étudiants qui n’en sont pas avertis à l’aide de l’application En classe.
-   **Certificats TLS non approuvés** : autoriser les certificats Transport Layer Security non autorisés sur l’appareil.
-   **Approbation des applications d’entreprise** : permet à l’utilisateur de choisir de faire confiance aux applications qui n’ont pas été téléchargées à partir de l’App Store.
- **Modification de compte (en mode supervisé uniquement)** - Si désactivée, cette option empêche l’utilisateur de modifier les paramètres spécifiques à l’appareil à partir de l’application des paramètres iOS, par exemple la création de nouveaux comptes d’appareils et la modification du nom d’utilisateur ou du mot de passe.
Cette restriction s’applique également aux options accessibles à partir des applications iOS comme Mail, Contacts, Calendrier, Facebook et Twitter. Elle ne s’applique pas aux applications avec des paramètres de compte qui ne sont pas configurables à partir des applications iOS comme Microsoft Outlook.
- **Activation des restrictions dans les paramètres de l’appareil (appareils supervisés uniquement)** : autorisez l’utilisateur à configurer les restrictions d'appareil (contrôle parental) sur l’appareil.
- **Utiliser la réinitialisation de tous les paramètres et du contenu sur l’appareil (mode supervisé uniquement)** : autorisez l’utilisateur à utiliser l’option de réinitialisation de tout le contenu et de tous les paramètres sur l’appareil.
- **Modification du nom de l'appareil (mode supervisé uniquement)** : autorise l’utilisateur à modifier le nom de l’appareil.
- **Modification des paramètres de notification (mode supervisé uniquement)** : autorisez l’utilisateur à modifier les paramètres de notification de l'appareil.
- **Modification des paramètres d’approbation d’application d’entreprise (mode supervisé uniquement)** : permet à l’utilisateur de sélectionner les applications approuvées qui n’ont pas été téléchargées à partir de l’App Store.
- **Modifications au profil de configuration (mode supervisé uniquement)** : autoriser l’utilisateur à installer des profils de configuration.
- **Verrou d’activation (mode supervisé uniquement)** : active le verrou d’activation sur les appareils iOS supervisés.

## <a name="configurations-requiring-supervision"></a>Configurations nécessitant une supervision

Vous pouvez activer le mode supervisé iOS seulement pendant l’installation initiale de l’appareil par le biais du programme DEP d’Apple ou d’Apple Configurator. Une fois le mode supervisé activé, Intune peut configurer un appareil avec les fonctionnalités suivantes :

- Verrouillage d’application (Mode Application unique) 
- Proxy HTTP global 
- Ignorer le verrouillage d’activation 
- Mode Application unique autonome 
- Filtrage de contenu web 
- Définition de l’écran d’arrière-plan et de verrouillage 
- Envoi (push) d’application en mode silencieux 
- VPN AlwaysOn 
- Autoriser l’installation d’applications gérées exclusivement 
- iBookstore 
- iMessages 
- Centre de jeux 
- AirDrop 
- AirPlay 
- Appairage d’hôtes 
- Synchronisation cloud 
- Recherche Spotlight 
- Handoff 
- Effacer l’appareil 
- Interface utilisateur - Restrictions 
- Installation de profils de configuration par l’interface utilisateur 
- Actualités 
- Raccourcis clavier 
- Modifications du code secret 
- Changements du nom de l’appareil 
- Téléchargements automatiques d’applications 
- Changements apportés à l’approbation d’applications d’entreprise 
- Apple Music 
- Mail Drop 
- Appairage avec Apple Watch 

> [!NOTE]
> Apple a confirmé que certains paramètres passeront en mode supervisé uniquement en 2019. Nous recommandons de prendre ceci en considération lors de l’utilisation de ces paramètres, au lieu d’attendre qu’Apple les migre en mode supervisé uniquement :
> - Installation de l’application par les utilisateurs finaux
> - Suppression d’applications
> - FaceTime
> - Safari
> - iTunes
> - Contenu explicite
> - Documents et données iCloud
> - Jeux multijoueur
> - Ajouter des amis du centre de jeux
> - Siri

## <a name="password"></a>Mot de passe
-   **Mot de passe** - Demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil.
    -   **Mots de passe simples** : autorise des mots de passe simples, comme 0000 et 1234.
    -   **Type de mot de passe requis** : spécifiez le type de mot de passe requis, par exemple des caractères numériques uniquement, ou des caractères alphanumériques.
    -   **Nombre de caractères non alphanumériques dans le mot de passe** : spécifie le nombre de caractères de symbole (comme **#** ou **@**) devant être inclus dans le mot de passe.
    -   **Longueur minimale du mot de passe** : spécifie le nombre minimal de caractères à inclure dans le mot de passe.
    -   **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : spécifie le nombre de tentatives d’entrée de mots de passe incorrects différents avant que ce paramètre déclenche l’effacement du contenu de l’appareil.
    -   **Nombre maximal de minutes après verrouillage de l’écran avant de demander un mot de passe**<sup>1</sup> : spécifiez la durée pendant laquelle l’appareil peut rester inactif avant que l’utilisateur doive entrer à nouveau son mot de passe.
    -   **Nombre maximal de minutes d’inactivité avant verrouillage de l’écran**<sup>1</sup> : spécifiez le nombre de minutes avant que l’écran de l’appareil s’éteigne.
    -   **Expiration du mot de passe (jours)** : spécifie le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
    -   **Empêcher la réutilisation des mots de passe précédents** : spécifiez le nombre de mots de passe précédemment utilisés conservés par l’appareil.
    -   **Déverrouillage par empreinte digitale** : autorisez l’utilisation d’une empreinte digitale pour déverrouiller les appareils compatibles.
- **Modification du code secret (mode supervisé uniquement)**  : empêche la modification, l’ajout ou la suppression du code secret.
    - **Modification de l’empreinte digitale (mode supervisé uniquement)**  : empêche la modification, l’ajout ou la suppression par l’utilisateur des paramètres Touch ID.

<sup>1</sup> Lorsque vous configurez les paramètres **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** et **Nombre maximal de minutes entre le verrouillage de l'écran et la demande du mot de passe**, ceux-ci sont appliqués de manière séquentielle. Par exemple, si vous affectez aux deux paramètres une valeur de **5** minutes, l’écran s’éteint automatiquement après 5 minutes, et l’appareil se verrouille après 5 minutes de plus. Toutefois, si l'utilisateur désactive manuellement l'écran, le second paramètre est immédiatement appliqué. Dans le même exemple, une fois que l’utilisateur a désactivé l’écran, l’appareil se verrouille 5 minutes plus tard.

## <a name="locked-screen-experience"></a>Expérience d’écran verrouillé

-   **Accès au centre de contrôle quand l'appareil est verrouillé** : autorise l’utilisateur à accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé.
-   **Notifications lorsque l’appareil est verrouillé** : autorisez l’utilisateur à accéder à l’affichage des notifications sans déverrouiller l’appareil.
-   **Livret lors du verrouillage de l’appareil** : autoriser l’utilisateur à accéder à l’application de livret lorsque l’appareil est verrouillé.
-   **Vue Aujourd'hui lors du verrouillage de l’appareil** : autorisez l’utilisateur à afficher la vue Aujourd'hui lorsque l’appareil est verrouillé.

## <a name="app-store-doc-viewing-gaming"></a>App Store, affichage de document, jeux


-   **App Store** : bloquez l’accès à l’App Store sur les appareils supervisés.
    - **Installation d’applications à partir de l’App Store (mode supervisé uniquement)** : bloque l’App Store à partir de l’écran d’accueil des appareils. Les utilisateurs finaux peuvent continuer à utiliser iTunes ou l’outil Apple Configurator pour installer des applications.
    - **Téléchargements automatiques des applications (mode supervisé uniquement)** : empêche le téléchargement sur cet appareil des applications qui ont été achetées sur un autre appareil iOS.
-   **Mot de passe pour accéder à l'App Store** : oblige l’utilisateur à saisir un mot de passe pour pouvoir visiter l’App Store.
-   **Achats dans l'application** : autoriser les achats depuis une application en cours d’exécution.
-   **Contenu explicite dans les musiques, podcasts et actualités sur iTunes (mode supervisé uniquement)** : autorisez l’appareil à accéder au contenu adulte à partir du Store.
-   **Télécharger du contenu de l'iBook Store indiqué comme étant de la « Littérature érotique »** : autorisez l’utilisateur à télécharger des livres de la catégorie « Littérature érotique ».
-   **Affichage de documents d’entreprise dans les applications non gérées** : autorisez l’affichage des documents d’entreprise dans n’importe quelle application.<br>**Exemple** : Vous voulez empêcher les utilisateurs d’enregistrer des fichiers de OneDrive dans Dropbox. Attribuez la valeur Non à ce paramètre. Une fois que l’appareil a reçu la stratégie (par exemple, après un redémarrage), il cesse d’autoriser l’enregistrement.
-   **Affichage des documents autres que ceux d’entreprise dans les applications d’entreprise** : autorisez l’affichage de tous les documents dans les applications d’entreprise gérées.
-   **Traiter AirDrop comme une destination non gérée** : empêche les applications gérées de pouvoir envoyer des données via AirDrop. AirDrop.
-   **Ajout d’amis Game Center (mode supervisé uniquement)** : autorisez l’utilisateur à ajouter des amis dans Game Center.
-   **Game Center (mode supervisé uniquement)** : bloquez ou activez l’utilisation de l’application Game Center.
-   **Jeux multijoueur (en mode supervisé uniquement)** autorisez l’utilisateur à jouer à des jeux multijoueur sur l’appareil.
-   **Plage de classifications** : choisissez la plage de classifications pour laquelle vous souhaitez configurer les téléchargements autorisés, puis cliquez sur les évaluations autorisées pour **Films** et **Émissions TV**.
-   **Applications** : choisissez la catégorie d’âge autorisée pour les applications que les utilisateurs peuvent télécharger, ou choisissez **Autoriser toutes les applications**.

## <a name="built-in-apps"></a>Applications intégrées

-   **Appareil photo** : spécifie si l’appareil photo de l’appareil peut être utilisé.
    -   **FaceTime** : autorisez l’utilisation de l’application FaceTime.
-   **Siri** : autoriser l’utilisation de l’assistant vocal Siri sur l’appareil.
    -   **Siri quand l'appareil est verrouillé** : autoriser l’utilisation de l’assistant vocal Siri sur l’appareil lorsqu’il est verrouillé.
    -   **Filtre d’obscénités de Siri (en mode supervisé uniquement)** : empêche Siri de dicter ou d’employer un langage obscène.
    -   **Siri à consulter le contenu généré par les utilisateurs depuis Internet (mode supervisé uniquement)** : autorisez Siri à accéder aux sites web pour répondre aux questions.
- **Apple News (mode supervisé uniquement)** : autorisez l’utilisation de l’application Apple News.
- **iBooks Store (en mode supervisé uniquement)** : autorise l’utilisateur à parcourir et à acheter des livres depuis l’IBooks Store.
- **Application Messages sur l’appareil (mode supervisé uniquement)** : autorisez l’utilisation de l’application Messages pour envoyer et lire des messages texte.
- **Podcasts (mode supervisé uniquement)** : autorisez l’utilisation de l’application Podcasts.
- **Service Music (mode supervisé uniquement)** : autorisez l’utilisation de l’application Apple Music.
- **Service iTunes Radio (mode supervisé uniquement)** : autorisez l’utilisation de l’application de iTunes Radio.
- **Modifications aux paramètres de l’application Find My Friends (mode supervisé uniquement)** : autorisez l’utilisateur à modifier les paramètres de l’application Find My Friends.
- **Recherche Spotlight pour renvoyer des résultats à partir d’Internet (mode supervisé uniquement)** : laissez la recherche Spotlight se connecter à Internet pour fournir des résultats.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- Une liste **Applications interdites** : répertorie les applications qui ne sont pas gérées par Intune et que les utilisateurs ne sont pas autorisés à installer et à exécuter. Rien n’empêche les utilisateurs d’installer une application interdite, mais, s’ils le font, vous en êtes informé.
- Une liste **Applications approuvées** : répertorie les applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Rien n’empêche les utilisateurs d’installer une application qui ne figure pas dans la liste approuvée, mais, s’ils le font, vous en êtes informé.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application, et l'URL de l'application dans l’App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Comment spécifier l’URL vers une application dans l’App Store

Pour insérer une URL d’application dans la liste des applications, utilisez le format suivant :

À l’aide d’un moteur de recherche, recherchez l’application à utiliser dans l’App Store iTunes, puis ouvrez la page de l’application.
Copiez l’URL de la page et utilisez-la en tant qu’adresse permettant de configurer la liste des applications autorisées ou interdites, ou une application à exécuter en mode kiosque.
Les profils d’appareil qui contiennent des paramètres d’applications restreintes doivent être attribués à des groupes d’utilisateurs.

Exemple : rechercher Microsoft Word pour iPad. L’URL que vous utilisez est https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Vous pouvez également utiliser iTunes pour rechercher l’application, puis la commande **Copier le lien** pour obtenir l’URL de l’application.

### <a name="additional-options"></a>Options supplémentaires

Vous pouvez également cliquer sur **Importer** pour remplir la liste à partir d’un fichier csv au format <*URL de l’application*>, <*Nom de l’application*>, <*Développeur de l’application*>, ou cliquer sur **Exporter** pour créer un fichier csv contenant le contenu de la liste des applications restreintes dans le même format.

## <a name="show-or-hide-apps-supervised-only"></a>Afficher ou masquer des applications (mode supervisé uniquement)

Dans la liste des applications affichées ou masquées, vous pouvez configurer une des listes suivantes (nécessite des appareils supervisés tournant sous iOS 9.3 ou version ultérieure).

- Liste **Applications masquées** : spécifiez une liste d’applications masquée aux utilisateurs. Les utilisateurs ne peuvent pas afficher ou lancer ces applications.
- Liste **Applications visibles** : spécifiez une liste d’applications que les utilisateurs peuvent voir et lancer. Aucune autre application ne peut être affichée ou lancée.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application, et l'URL de l'application dans l’App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Comment spécifier l’URL vers une application dans l’App Store

Pour insérer une URL d’application dans la liste des applications, utilisez le format suivant :

À l’aide d’un moteur de recherche, recherchez l’application à utiliser dans l’App Store iTunes, puis ouvrez la page de l’application.
Copiez l’URL de la page et utilisez-la en tant qu’adresse permettant de configurer la liste des applications autorisées ou interdites, ou une application à exécuter en mode kiosque.

Exemple : rechercher Microsoft Word pour iPad. L’URL que vous utilisez est https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Vous pouvez également utiliser le logiciel iTunes pour rechercher l'application, puis la commande **Copier le lien** pour obtenir l'URL de l'application.

### <a name="additional-options"></a>Options supplémentaires

Vous pouvez également cliquer sur **Importer** pour remplir la liste à partir d’un fichier csv au format <*URL de l’application*>, <*Nom de l’application*>, <*Développeur de l’application*>, ou cliquer sur **Exporter** pour créer un fichier csv contenant le contenu de la liste des applications affichées ou masquées dans le même format.


## <a name="wireless"></a>Sans fil
-   **Itinérance des données** : autoriser l’itinérance des données quand l’appareil se trouve sur un réseau cellulaire.
-   **Récupération en arrière-plan globale en cas d'itinérance** : autoriser l’appareil à récupérer des données comme les courriers électroniques lorsqu’il est en mode itinérance sur un réseau cellulaire.
-   **Numérotation vocale** : autoriser l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil.
-   **Itinérance vocale** : autoriser l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
-   **Modifications apportées aux paramètres d’utilisation des données cellulaires des applications (mode supervisé uniquement)** : autorisez l’utilisateur à contrôler les applications qui sont autorisées à utiliser des données cellulaires.
-   **Point d’accès personnel** : n’autorisez pas l’appareil à servir de point d’accès personnel. Ce paramètre n’est peut-être pas compatible avec certains opérateurs.
-   **Rejoindre uniquement les réseaux Wi-Fi utilisant des profils de configuration (mode supervisé uniquement)** : autorisez uniquement l’appareil à rejoindre les réseaux Wi-Fi qui ont été configurés avec un profil Wi-Fi Intune.

- **Règles d’utilisation des données mobiles (applications gérées uniquement)** : vous permet de définir les types de données que les applications gérées peuvent utiliser sur les réseaux mobiles. Choisissez parmi :
    - **Bloquer l’utilisation de données cellulaires** : vous pouvez bloquer l’utilisation de données cellulaires pour ** toutes les applications managées ** ou **Choisir des applications spécifiques**.
    - **Bloquer l’utilisation de données cellulaires en itinérance** : vous pouvez bloquer l’utilisation de données cellulaires en itinérance pour ** toutes les applications managées ** ou **Choisir des applications spécifiques**.

## <a name="connected-devices"></a>Appareils connectés

-   **AirDrop (en mode supervisé uniquement)** : autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils proches.
-   **Appariement Apple Watch (mode supervisé uniquement)** : autorise l’appareil à s’associer avec une Apple Watch.
-   **Détection du poignet pour une Apple Watch appairée** : quand elle est activée, l’Apple Watch n’affiche pas de notification si elle n’est pas portée.
-   **Modification Bluetooth (mode supervisé uniquement)** : empêche l’utilisateur final de modifier les paramètres Bluetooth sur l’appareil.
-   **Appariement d’hôtes pour contrôler les appareils avec lesquels un appareil iOS peut s’apparier (mode supervisé uniquement)** : autorisez l’appariement d’hôtes à permettre à l’administrateur de déterminer les appareils avec lesquels un appareil iOS peut s’apparier.
-   **Exiger un mot de passe associé pour les demandes AirPlay sortantes** : nécessite un mot de passe de jumelage lorsque l’utilisateur a recours à AirPlay pour diffuser le contenu vers d’autres appareils Apple.

## <a name="keyboard-and-dictionary"></a>Clavier et dictionnaire

-   **Recherche de définition des mots (en mode supervisé uniquement)** : autorise la fonctionnalité iOS qui vous permet de mettre un mot en surbrillance et de rechercher sa définition.
-   **Claviers prédictifs (en mode supervisé uniquement)** : autorise l’utilisation de claviers prédictifs qui suggèrent des mots que l’utilisateur pourrait vouloir utiliser.
-   **Correction automatique (en mode supervisé uniquement)** : permet à l’appareil de corriger automatiquement les mots mal orthographiés.
-   **Vérification orthographique du clavier (mode supervisé uniquement)** : active l’outil de vérification orthographique de l’appareil.
-   **Raccourcis clavier (mode supervisé uniquement)** : permet d’utiliser les raccourcis clavier.
-   **Dictée (mode supervisé uniquement)** : empêche l’utilisateur de se servir de l’entrée vocale pour entrer du texte.

## <a name="cloud-and-storage"></a>Cloud et stockage
-   **Sauvegarder sur iCloud** : autorise l’utilisateur à sauvegarder les données de l’appareil dans iCloud.
-   **Synchronisation de documents sur iCloud (en mode supervisé uniquement)** : autorisez la synchronisation des documents et des clés-valeurs sur votre espace de stockage iCloud.
-   **Synchronisation du flux de photos sur iCloud** : permet aux utilisateurs d’activer **Mon flux de photos** sur leur appareil afin de synchroniser les photos avec iCloud et de les mettre à la disposition de tous les appareils des utilisateurs.
-   **Sauvegarde chiffrée** : exiger le chiffrement des sauvegardes d’appareil.
-   **Photothèque iCloud** : si défini sur **Non**, désactive l’utilisation de la Photothèque iCloud qui permet aux utilisateurs de stocker des photos et des vidéos dans le cloud.   Toutes les photos qui ne sont pas entièrement téléchargées de la Photothèque iCloud sur l’appareil sont supprimées de l’appareil si cette valeur est définie sur **Non**.
-   **Applications gérées synchronisées avec le cloud** : autorisez les applications que vous gérez avec Intune à synchroniser les données sur le compte iCloud de l’utilisateur.
-   **Flux de photos partagé** : choisissez **Non** pour désactiver le **partage de photos iCloud** sur l'appareil.
-   **Continuation de l’activité** : autorise l’utilisateur à reprendre le travail qu’il a commencé sur un appareil iOS sur un autre appareil iOS ou macOS (continuité).

## <a name="autonomous-single-app-mode-supervised-only"></a>Mode Application unique autonome (mode supervisé uniquement)

Utilisez ces paramètres pour configurer les appareils iOS pour qu’ils exécutent les applications spécifiées en mode Application unique autonome. Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé et il ne peut exécuter que cette application. Vous pouvez par exemple utiliser ce mode quand vous configurez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

### <a name="settings"></a>Paramètres

- **Nom de l’application** : entrez le nom de l’application tel qu’il doit apparaître dans la liste des applications sur ce panneau.
- **ID d'ensemble d'applications** : entrez l’ID d’ensemble de l’application. Pour plus d’aide, consultez la section **Référence à un ID d’ensemble pour les applications iOS intégrées** de cette rubrique.

Une fois que vous spécifiez le nom de chaque application et l’ID d’ensemble, cliquez sur **Ajouter** pour l’ajouter à la liste.

- **Importer** : importez un fichier .csv contenant une liste de noms d’application et leurs ID d’ensemble associés.
- **Exporter** : exportez les noms d’application et les ID d’ensemble associés que vous avez configurés dans un fichier .csv.

## <a name="kiosk-supervised-only"></a>Plein écran (supervisé uniquement)
-   **Application gérée qui s’exécute en mode plein écran** : choisissez **Application gérée** pour sélectionner une application que vous avez ajoutée à Intune, **Application de Store** pour spécifier l’URL d’une application dans le Store, ou **Application intégrée** pour spécifier l’ID d’offre groupée de l’application intégrée. Pour plus d’informations, consultez [Référence à un ID d’ensemble pour les applications iOS intégrées](device-restrictions-ios.md#bundle-id-reference-for-built-in-ios-apps) et [Comment spécifier l’URL vers une application dans l’App Store](device-restrictions-ios.md#how-to-specify-the-url-to-an-app-in-the-store-1).
    -   **Assistance tactile** : active ou désactive le paramètre d’accessibilité **Assistance tactile**, qui permet à l’utilisateur d’effectuer des mouvements à l’écran pouvant être difficiles à effectuer.
    -   **Inverser les couleurs** - Active ou désactive le paramètre d’accessibilité Inverser les couleurs qui ajuste l’affichage pour aider les utilisateurs ayant des troubles visuels.
    -   **Audio mono** : active ou désactive le paramètre d’accessibilité Audio mono.
    -   **VoiceOver** : activez ou désactivez le paramètre d’accessibilité **VoiceOver**, qui lit à haute voix le texte affiché à l’appareil.
    -   **Zoom** : active ou désactive le paramètre d’accessibilité **Zoom**, qui vous permet d’utiliser la fonctionnalité tactile pour agrandir l’affichage de l’appareil.
    -   **Verrouillage automatique** : active ou désactive le verrouillage automatique de l’appareil.
    -   **Fonction de sonnerie** - Active ou désactive le commutateur de sonnerie (désactivation du son) sur l’appareil.
    -   **Rotation d’écran** : active ou désactive la modification de l’orientation de l’écran lorsque l’utilisateur fait pivoter l’appareil.
    -   **Bouton de mise en veille de l’écran** : active ou désactive le bouton Veille/sortie de veille de l’écran sur l’appareil.
    -   **Tactile** : active ou désactive l’écran tactile sur l’appareil.
    -   **Boutons de volume** - Active ou désactive l’utilisation des boutons de volume sur l’appareil.
    -   **Assistance tactile** : active ou désactive les réglages d’assistance tactile, qui permettent à l’utilisateur de régler la fonction d’assistance tactile.
    -   **Réglages de couleurs inversées** : active ou désactive les réglages de couleurs inversées, qui permettent à l’utilisateur d’ajuster la fonction de couleurs inversées.
    -   **Lire le texte sélectionné** : active ou désactive les paramètres d’accessibilité Sélection Speak, qui peuvent lire à haute voix le texte que l’utilisateur sélectionne.
    -   **Contrôle VoiceOver** : active ou désactive les réglages VoiceOver qui vous permettent de régler la fonction VoiceOver (par exemple, la vitesse de lecture à haute voix du texte affiché à l’écran).
    -   **Contrôle du zoom** : active ou désactive les réglages du zoom qui vous permettent de régler la fonction de zoom.

>[!NOTE]
> Avant de pouvoir configurer un appareil iOS pour le mode plein écran, vous devez utiliser l’outil Apple Configurator ou le Programme d’inscription des appareils Apple pour mettre l’appareil en mode supervisé. Pour en savoir plus sur l’outil Apple Configurator, consultez votre documentation Apple.
>Si l’application iOS que vous spécifiez est installée après l’attribution du profil, l’appareil ne bascule en mode plein écran qu’après son redémarrage.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Référence à un ID d’ensemble pour les applications iOS intégrées

Cette liste affiche l’ID d’ensemble de quelques applications iOS intégrées parmi les plus courantes. Pour rechercher l’ID d’ensemble d’autres applications, contactez votre éditeur de logiciels.

| ID d’offre groupée                   | Nom de l’application     | Éditeur |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculatrice   | Apple     |
| com.apple.mobilecal         | Calendrier     | Apple     |
| com.apple.camera            | Appareil photo       | Apple     |
| com.apple.mobiletimer       | Horloge        | Apple     |
| com.apple.compass           | Boussole      | Apple     |
| com.apple.MobileAddressBook | Contacts     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.mobileme.fmf1     | Trouver des amis | Apple     |
| com.apple.mobileme.fmip1    | Trouver un iPhone  | Apple     |
| com.apple.gamecenter        | Centre de jeux  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Intégrité       | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.MapsMaps          |              | Apple     |
| com.apple.MobileSMS         | Messages     | Apple     |
| com.apple.Music             | Musique        | Apple     |
| com.apple.news              | Actualités         | Apple     |
| com.apple.mobilenotes       | Remarques        | Apple     |
| com.apple.Numbers           | Nombres      | Apple     |
| com.apple.Pages             | Pages        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Photo       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Rappels    | Apple     |
| com.apple.MobileSafari      | Safari       | Apple     |
| com.apple.Preferences       | Paramètres     | Apple     |
| com.apple.stocks            | Bourse       | Apple     |
| com.apple.tips              | Conseils         | Apple     |
| com.apple.videos            | Vidéos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Portefeuille       | Apple     |
| com.apple.Bridge            | Regardez        | Apple     |
| com.apple.weather           | Météo      | Apple     |

## <a name="safari"></a>Safari
-   **Supervisé (en mode supervisé uniquement)** : spécifier si le navigateur Safari peut être utilisé sur l’appareil.
-   **Remplissage automatique** : autorise l’utilisateur à modifier les paramètres de saisie semi-automatique dans le navigateur.
-   **Cookies** : autorise le navigateur à utiliser des cookies.
-   **JavaScript** : autoriser l’exécution des scripts Java dans le navigateur.
-   **Avertissement de fraude** : autoriser l’affichage d’avertissements antifraude dans le navigateur.
-   **Fenêtres publicitaires** : activer ou désactiver le bloqueur de fenêtres publicitaires du navigateur.


## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domaines d’e-mail non marqués

Dans le champ **URL de domaine d’e-mail**, ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs finaux reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez configurés, l’e-mail est marqué comme non approuvé dans l’application iOS Mail.


### <a name="managed-web-domains"></a>Domaines web gérés

Dans le champ **URL de domaine web**, ajoutez une ou plusieurs URL à la liste. Les documents téléchargés à partir des domaines que vous spécifiez sont considérés comme gérés. Ce paramètre s’applique uniquement aux documents téléchargés à l’aide du navigateur Safari.


### <a name="safari-password-autofill-domains"></a>Domaines de remplissage automatique des mots de passe Safari

Dans le champ **URL de domaine**, ajoutez une ou plusieurs URL à la liste. Les utilisateurs peuvent uniquement enregistrer les mots de passe web à partir des URL de cette liste. Ce paramètre s’applique uniquement au navigateur Safari et aux appareils iOS 9.3 et versions ultérieures en mode supervisé. Si vous ne spécifiez aucune URL, les mots de passe peuvent être enregistrés à partir de tous les sites web.
