---
title: Paramètres d’appareil Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils Android Entreprise et Android for Work, vous pouvez restreindre certains paramètres, notamment les opérations de copier-coller, l’affichage des notifications, les autorisations d’application, le partage de données, la longueur de mot de passe, les échecs de connexion, l’utilisation d’empreintes digitales pour le déverrouillage, la réutilisation des mots de passe et l’activation du partage Bluetooth des contacts professionnels. Configurez les appareils comme appareils dédiés plein écran pour exécuter une ou plusieurs applications.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8bd537315a09c0c7cf338ac0892fc4ae3d1dc8fc
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550190"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités avec Intune

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Android Entreprise. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, pour exécuter les applications sur les appareils dédiés, pour contrôler la sécurité, et bien plus encore.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Propriétaire de l’appareil uniquement

### <a name="general-settings"></a>Paramètres généraux :

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. Cela empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée. L’option **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran comme image.
- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option **Non requis** autorise l’accès à l’appareil photo de l’appareil.
- **Stratégie d’autorisation par défaut**: ce paramètre définit la stratégie d’autorisation par défaut pour les demandes d’autorisations d’exécution. Les valeurs possibles sont :
  - **Paramètre par défaut de l’appareil** : utiliser le paramètre par défaut de l’appareil.
  - **Demander** : l’utilisateur est invité à approuver l’autorisation.
  - **Accorder automatiquement** : les autorisations sont automatiquement accordées.
  - **Refuser automatiquement** : les autorisations sont automatiquement refusées.
- **Changements de date et d'heure** : choisissez **Bloquer** pour empêcher les utilisateurs de régler manuellement la date et l’heure. L’option **Non configuré** autorise les utilisateurs à régler la date et l’heure sur l’appareil.
- **Changements du volume** : choisissez **Bloquer** pour empêcher les utilisateurs de changer le volume de l’appareil. L’option **Non configuré** autorise l’utilisation des paramètres de volume sur l’appareil.
- **Réinitialisation aux paramètres d’usine** : choisissez **Bloquer** pour empêcher les utilisateurs de réinitialiser l’appareil aux paramètres d’usine. L’option **Non configuré** permet aux utilisateurs d’utiliser ce paramètre sur l’appareil.
- **Démarrage sans échec** : choisissez **Bloquer** pour empêcher les utilisateurs de redémarrer l’appareil en mode sans échec. L’option **Non configuré** autorise les utilisateurs à redémarrer l’appareil en mode sans échec.
- **Barre d’état** : choisissez **Bloquer** pour empêcher les utilisateurs d’accéder à la barre d’état, notamment aux notifications et aux paramètres rapides. L’option **Non configuré** autorise les utilisateurs à accéder à la barre d’état.
- **Itinérance des services de données** : choisissez **Bloquer** pour empêcher l’itinérance des données sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Changements des paramètres Wi-Fi** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres Wi-Fi créés par le propriétaire de l’appareil. Les utilisateurs peuvent créer leurs propres configurations Wi-Fi. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres Wi-Fi sur l’appareil.
- **Configuration du point d’accès Wi-Fi** : choisissez **Bloquer** pour empêcher les utilisateurs de créer ou de modifier des configurations Wi-Fi. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres Wi-Fi sur l’appareil.
- **Configuration Bluetooth** : choisissez **Bloquer** pour empêcher les utilisateurs de configurer le Bluetooth sur l’appareil. L’option **Non configuré** autorise l’utilisation du Bluetooth sur l’appareil.
- **Connexion et accès aux points d’accès** : choisissez **Bloquer** pour empêcher la connexion et l’accès aux points d’accès mobiles. L’option **Non configuré** permet d’accéder de se connecter et d’accéder aux points d’accès mobiles.
- **Stockage USB** : choisissez **Autoriser** pour accéder au stockage USB sur l’appareil. L’option **Non configuré** empêche l’accès au stockage USB.
- **Transfert de fichiers USB** : choisissez **Bloquer** pour empêcher le transfert de fichiers via USB. L’option **Non configuré** autorise le transfert de fichiers.
- **Support externe** : choisissez **Bloquer** pour empêcher l’utilisation ou la connexion d’un support externe sur l’appareil. L’option **Non configuré** autorise l’utilisation d’un support externe sur l’appareil.
- **Transmettre des données à l'aide de NFC** : choisissez **Bloquer** afin d’empêcher l’utilisation de la technologie Near Field Communication (NFC) pour transmettre des données à partir d’applications. L’option **Non configuré** autorise l’utilisation de NFC pour partager des données entre les appareils.
- **Fonctionnalités de débogage** : choisissez **Autoriser** pour permettre l’utilisation des fonctionnalités de débogage sur l’appareil. L’option **Non configuré** empêche l’utilisation des fonctionnalités de débogage sur l’appareil.
- **Réglage du microphone** : choisissez **Bloquer** pour empêcher les utilisateurs d’activer le microphone et d’en régler le volume. L’option **Non configuré** permet l’utilisation du microphone et le réglage de son volume sur l’appareil.
- **E-mails de protection contre la réinitialisation aux paramètres d'usine** : choisissez **Adresses e-mail du compte Google**. Entrez les adresses e-mail des administrateurs de l’appareil autorisés à déverrouiller l’appareil réinitialisé. Veillez à séparer les adresses e-mail par un point-virgule, par exemple `admin1@gmail.com;admin2@gmail.com`. Si aucune adresse e-mail n’est spécifiée, quiconque peut déverrouiller un appareil réinitialisé aux paramètres d’usine. Ces courriers électroniques s’appliquent uniquement lorsqu’une réinitialisation de la fabrique non-utilisateur est exécutée, comme l’exécution d’une réinitialisation aux paramètres d’usine via le menu récupération.
- **Trappe de secours du réseau** : choisissez **Activer** pour autoriser les utilisateurs à activer la fonctionnalité de trappe de secours du réseau. Si aucune connexion réseau n’est établie au démarrage de l’appareil, la trappe de secours vous demande de vous connecter temporairement à un réseau et d’actualiser la stratégie de l’appareil. Une fois la stratégie appliquée, le réseau temporaire est oublié et l’appareil continue de démarrer. Cette fonctionnalité connecte les appareils à un réseau si :
  - La dernière stratégie ne contient aucun réseau approprié.
  - L’appareil démarre dans une application en mode de verrouillage de tâche.
  - L’utilisateur ne peut pas atteindre les paramètres de l’appareil.

  L’option **Non configuré** empêche les utilisateurs d’activer la fonctionnalité de trappe de secours du réseau sur l’appareil.

- **Mise à jour système** : choisissez une option pour définir la façon dont l’appareil traite les mises à jour à distance :
  - **Paramètre par défaut de l’appareil** : utiliser le paramètre par défaut de l’appareil.
  - **Automatique** : les mises à jour sont installées automatiquement, sans interaction de l’utilisateur. La définition de cette stratégie entraîne l’installation immédiate des mises à jour en attente.
  - **Différé** : les mises à jour sont reportées de 30 jours. À la fin des 30 jours, Android invite l’utilisateur à installer la mise à jour. Il est possible pour les fabricants ou les opérateurs d’appareils d’empêcher (exempter) le report des mises à jour de sécurité importantes. Une mise à jour exemptée affiche une notification système sur l’appareil de l’utilisateur. 
  - **Fenêtre de maintenance** : permet d’installer les mises à jour automatiquement durant une fenêtre de maintenance quotidienne définie dans Intune. L’installation est tentée quotidiennement pendant 30 jours, et cette opération peut échouer en raison d’un espace ou d’un niveau de batterie insuffisant. Après 30 jours, Android invite l’utilisateur à procéder à l’installation. Cette fenêtre est également utilisée pour installer les mises à jour des applications Play. Utilisez cette option pour les appareils dédiés, par exemple les bornes, car les applications de premier plan d’appareils mono-application dédiés peuvent être mises à jour.

- **Fenêtre de notification** : quand cette option a la valeur **Désactiver**, les notifications, notamment les toasts, les appels entrants, les appels sortants, les alertes système et les erreurs système, ne sont pas affichées sur l’appareil. quand elle a la valeur **Non configuré**, les paramètres par défaut du système d’exploitation sont utilisés (ce qui peut entraîner l’affichage des notifications).
- **Ignorer les premiers conseils d’utilisation** : choisissez **Activer** pour masquer ou ignorer les suggestions des applications concernant l’exécution de tutoriels ou la lecture de conseils d’introduction lors du démarrage de l’application. Quand vous affectez la valeur **Non configuré**, les paramètres par défaut du système d’exploitation sont utilisés (ce qui peut entraîner l’affichage de ces suggestions au démarrage de l’application).

### <a name="system-security-settings"></a>Paramètres de sécurité système

- **Analyse des menaces sur les applications** : **Exiger** (par défaut) permet à Google Play Protect d’analyser les applications avant et après leur installation. S’il détecte une menace, il peut avertir l’utilisateur et lui recommander de supprimer l’application de l’appareil. **Non configuré** ne permet pas à Google Play Protect d’analyser des applications.

### <a name="dedicated-device-settings"></a>Paramètres de l’appareil dédié

Utilisez ces paramètres pour configurer une expérience plein écran sur vos appareils dédiés. Vous pouvez configurer un appareil pour exécuter une ou plusieurs applications. Quand un appareil est en mode plein écran, seules les applications que vous ajoutez sont disponibles. Ces paramètres s’appliquent aux appareils Android Enterprise dédiés. Ils ne sont pas appliqués à des appareils Android Enterprise entièrement gérés.

**Mode plein écran** : choisissez si l’appareil exécute une ou plusieurs applications.

- **Application unique** : les utilisateurs ne peuvent accéder qu’à une seule application sur l’appareil. Lors du démarrage de l’appareil, seule l’application spécifique démarre. Les utilisateurs ne peuvent pas ouvrir de nouvelles applications, ni changer l’application en cours d’exécution.

  - **Sélectionner une application gérée** : sélectionnez l’application Google Play gérée dans la liste.

    Si la liste ne contient aucune application, [ajoutez des applications Android](apps-add-android-for-work.md) à l’appareil. Veillez à [attribuer l’application au groupe d’appareils créé pour vos appareils dédiés](apps-deploy.md).

  > [!IMPORTANT]
  > Lors de l’utilisation d’un mode plein écran, les applications de numéroteur/téléphone peuvent ne pas fonctionner correctement. 
  
- **Multi-application**: les utilisateurs peuvent accéder à un ensemble limité d’applications sur l’appareil. Lors du démarrage de l’appareil, seules les applications que vous ajoutez s’exécutent. Vous pouvez également ajouter des liens web que les utilisateurs peuvent ouvrir. Quand la stratégie est appliquée, les utilisateurs voient des icônes pour les applications autorisées dans l’écran d’accueil.

  > [!IMPORTANT]
  > Pour les appareils multi-application dédiés, l’application [Managed Home Screen](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) à partir de Google Play **doit être** :
  >   - [Ajoutée en tant qu’application cliente](apps-add-android-for-work.md) dans Intune
  >   - [Attribuée au groupe d’appareils](apps-deploy.md) créé pour vos appareils dédiés
  > 
  > L’application **Managed Home Screen** ne doit pas nécessairement figurer dans le profil de configuration, mais elle doit être ajoutée comme une application cliente. Lorsque l’application **Managed Home Screen** est ajoutée comme application cliente, toutes les autres applications que vous ajoutez au profil de configuration apparaissent sous forme d’icônes dans l’application **Managed Home Screen**. 
  >
  > Lorsque vous utilisez le mode plein écran à plusieurs applications, les applications de numéroteur/téléphone peuvent ne pas fonctionner correctement. 

  - **Ajouter**: sélectionnez vos applications dans la liste.

    Si l’application **Managed Home Screen** n’est pas répertoriée, [ajoutez-la à partir de Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Veillez à [attribuer l’application](apps-deploy.md) au groupe d’appareils créé pour vos appareils dédiés.

    Vous pouvez également ajouter à l’appareil d’autres [applications Android](apps-add-android-for-work.md) et [applications web](web-app.md) créées par votre organisation. Veillez à [attribuer l’application au groupe d’appareils créé pour vos appareils dédiés](apps-deploy.md).

  - **Bouton Accueil virtuel**: bouton de touche programmable qui renvoie les utilisateurs à l’écran d’accueil géré afin que les utilisateurs puissent basculer entre les applications. Les options disponibles sont les suivantes :

    - **Non configuré** (valeur par défaut): un bouton de démarrage n’est pas affiché. Les utilisateurs doivent utiliser le bouton précédent pour basculer entre les applications.
    - **Balayer vers le haut**: un bouton d’installation s’affiche lorsqu’un utilisateur passe sur l’appareil.
    - **Floating**: affiche un bouton d’hébergement permanent et flottant sur l’appareil.

  - **Quitter le mode kiosque** : choisissez **Activer** pour autoriser les administrateurs à quitter temporairement le mode plein écran (kiosque) pour mettre à jour l’appareil. Pour utiliser cette fonctionnalité, l’administrateur :
  
    1. continue à sélectionner le bouton de retour jusqu’à ce que le bouton **Quitter le kiosque** s’affiche ; 
    2. sélectionne le bouton **Quitter le kiosque** et entre le code confidentiel **Quitter le code de mode kiosque**.
    3. Lorsque vous avez terminé, sélectionnez l’application gérée de l' **écran d’accueil** . Cette étape verrouille à nouveau l’appareil en mode kiosque multi-application.

      Si la valeur **n’est pas configurée**, les administrateurs ne peuvent pas suspendre le mode plein écran. Si l’administrateur continue de cliquer sur le bouton Précédent et sélectionne le bouton **Quitter le kiosque**, un message indique qu’un code secret est requis.

    - **Code permettant de quitter le mode kiosque** : entrez un code PIN composé de 4 à 6 chiffres. L’administrateur utilise ce code PIN pour interrompre temporairement le mode kiosque.

  - **Définir l’arrière-plan de l’URL personnalisée** : entrez une URL pour personnaliser l’arrière-plan de l’appareil dédié.

    > [!NOTE]
    > Dans la plupart des cas, nous recommandons de commencer avec des images des tailles minimales suivantes :
    >
    > - Téléphone : 1080 x 1920 px
    > - Tablette : 1920 x 1080 px
    >
    > Pour une expérience optimale et claire, il est conseillé de créer des composants d’images par appareil selon les caractéristiques de l’écran.
    >
    > Les écrans modernes affichent une densité supérieure de pixels et peuvent obtenir une définition d’image 2K/4K.

  - **Configuration Wi-Fi**: **activer** affiche le contrôle Wi-Fi sur l’écran d’accueil géré et permet aux utilisateurs finaux de connecter l’appareil à différents réseaux WiFi. L’activation de cette fonctionnalité active également l’emplacement de l’appareil. **Non configuré** (par défaut) n’affiche pas le contrôle Wi-Fi sur l’écran d’accueil géré. Il empêche les utilisateurs de se connecter aux réseaux Wi-Fi tout en utilisant l’écran d’accueil géré.

  - **Configuration Bluetooth**: **activer** affiche le contrôle Bluetooth sur l’écran d’accueil géré et permet aux utilisateurs finaux de coupler des appareils sur Bluetooth. L’activation de cette fonctionnalité active également l’emplacement de l’appareil. **Non configuré** (par défaut) n’affiche pas le contrôle Bluetooth sur l’écran d’accueil géré. Il empêche les utilisateurs de configurer Bluetooth et d’apparier les appareils tout en utilisant l’écran d’accueil géré.

  - **Accès torche**: **activer** affiche le contrôle torche sur l’écran d’accueil géré et permet aux utilisateurs finaux d’activer ou de désactiver le flash. **Non configuré** (par défaut) n’affiche pas le contrôle torche sur l’écran d’accueil géré. Il empêche les utilisateurs d’utiliser la torche lors de l’utilisation de l’écran d’accueil géré.

  - **Media Volume Control**: **Enable** affiche le contrôle du volume de média sur l’écran d’accueil géré et permet aux utilisateurs finaux d’ajuster le volume multimédia de l’appareil à l’aide d’un curseur. **Non configuré** (par défaut) n’affiche pas le contrôle du volume de média sur l’écran d’accueil géré. Il empêche les utilisateurs d’ajuster le volume de média de l’appareil lors de l’utilisation de l’écran d’accueil géré, sauf si leurs boutons matériels le prennent en charge. 

  - **Mode**d’économiseur d’écran: **activer** affiche un économiseur d’écran sur l’écran d’accueil géré lorsque l’appareil est verrouillé ou expire. **Non configuré** (par défaut) n’affiche pas un économiseur d’écran sur l’écran d’accueil géré.

    Lorsque cette option est activée, configurez également:

    - **Définir l’image de l’écran de veille personnalisée**: entrez l’URL d’une image personnalisée. Par exemple, entrez :

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Si vous n’entrez pas d’URL, l’image par défaut de l’appareil est utilisée, s’il existe une image par défaut.

    - **Nombre de secondes pendant lesquelles l’appareil affiche l’économiseur d’écran avant**de désactiver l’écran: choisissez la durée pendant laquelle l’appareil affiche l’écran de veille. Entrez une valeur comprise entre 0-9999999 secondes. La valeur par défaut est de `0` secondes. Si vous ne renseignez pas le champ,`0`ou la valeur zéro (), l’écran de veille est actif jusqu’à ce qu’un utilisateur interagisse avec l’appareil.
    - **Nombre de secondes d’inactivité de l’appareil avant l’affichage de l’écran de veille**: choisissez la durée d’inactivité de l’appareil avant d’en montrer l’écran de veille. Entrez une valeur comprise entre 1-9999999 secondes. La valeur par défaut est de `30` secondes. Vous devez entrer un nombre supérieur à zéro (`0`).
    - **Détecter le support avant de démarrer**l’économiseur d’écran: **activer** (par défaut) n’affiche pas l’écran de veille si l’audio ou la vidéo est en cours de lecture sur l’appareil. **Non configuré** affiche l’écran de veille, même si l’audio ou la vidéo est en train de fonctionner.

### <a name="device-password-settings"></a>Paramètres de mot de passe des appareils

- **Désactiver le verrouillage d’écran** : choisissez **Désactiver** pour empêcher l’utilisation de la fonctionnalité de verrouillage d’écran Keyguard sur l’appareil. L’option **Non configuré** permet l’utilisation des fonctionnalités Keyguard.
- **Désactiver les fonctionnalités de verrouillage d’écran** : quand keyguard est activé sur l’appareil, choisissez les fonctionnalités à désactiver. Par exemple, quand l’option **Sécuriser l’appareil photo** est cochée, la fonctionnalité appareil photo est désactivée sur l’appareil. Toutes les fonctionnalités non cochées sont activées sur l’appareil.

  Ces fonctionnalités sont disponibles pour les utilisateurs lorsque l’appareil est verrouillé. Les utilisateurs ne verront pas les fonctionnalités vérifiées ni ne pourront y accéder.

- **Type de mot de passe obligatoire** : définissez le type de mot de passe demandé pour l’appareil. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Mot de passe requis, sans restriction**
  - **Biométrie faible** : [Biométrie forte et faible](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (dirige sur le site web d’Android)
  - **Numérique** : le mot de passe ne doit comporter que des nombres, par exemple `123456789`. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Chiffres complexes** : les chiffres répétés ou consécutifs (comme « 1111 » ou « 1234 ») ne sont pas autorisés. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Alphabétique** : des lettres de l’alphabet sont nécessaires. Les nombres et symboles ne sont pas nécessaires. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Alphanumériques** : inclut des lettres majuscules, minuscules et des caractères numériques. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Alphanumérique avec symboles** : inclut des lettres majuscules, minuscules, des caractères numériques, des signes de ponctuation et des symboles. Entrez également :

    - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe (entre 4 et 16 caractères).
    - **Nombre de caractères requis** : entrez le nombre de caractères du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères minuscules** : entrez le nombre de caractères minuscules du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères majuscules** : entrez le nombre de caractères majuscules du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères non lettres requis** : entrez le nombre de caractères non lettres (tout caractère hors lettres de l’alphabet) du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères numériques requis** : entrez le nombre de caractères numériques (`1`, `2`, `3`, etc.) du mot de passe (entre 0 et 16 caractères).
    - **Nombre de symboles requis** : entrez le nombre de symboles (`&`, `#`, `%`, etc.) du mot de passe (entre 0 et 16 caractères).

- **Nombre de jours avant expiration du mot de passe** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (entre 1 et 365). Par exemple, pour modifier le mot de passe après 60 jours, entrez `60`. Lorsque le mot de passe arrive à expiration, les utilisateurs sont invités à créer un mot de passe.
- **Nombre de mots de passe requis avant que l’utilisateur puisse réutiliser un mot de passe** : entrez le nombre de mots de passe récents ne pouvant être réutilisés (entre 1 et 24). Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil (entre 4 et 11).

### <a name="power-settings"></a>Paramètres d’alimentation

- **Délai avant verrouillage de l’écran** : définissez la durée d’inactivité nécessaire avant le verrouillage de l’appareil.
- **Écran actif quand l’appareil est branché** : choisissez quelles sources d’alimentation permettent de conserver actif l’écran de l’appareil quand il est branché.

### <a name="users-and-accounts-settings"></a>Paramètres des utilisateurs et des comptes

- **Ajouter de nouveaux utilisateurs** : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter de nouveaux utilisateurs. Chaque utilisateur dispose d’un espace personnel sur l’appareil, regroupant les écrans d’accueil personnalisés ainsi que les comptes, applications et paramètres. L’option **Non configuré** autorise les utilisateurs à ajouter d’autres utilisateurs à l’appareil.
- **Suppression d’utilisateurs** : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des utilisateurs. L’option **Non configuré** autorise les utilisateurs à supprimer d’autres utilisateurs de l’appareil.
- **Modifications apportées aux comptes** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier des comptes. L’option **Non configuré** autorise les utilisateurs à mettre à jour les comptes d’utilisateurs sur l’appareil.

### <a name="applications"></a>Applications

- **Autoriser l’installation à partir de sources inconnues** : choisissez **Autoriser** pour permettre aux utilisateurs d’activer **Sources inconnues**. Ce paramètre permet aux applications d’être installées à partir de sources inconnues, y compris celles ne provenant pas de Google Play Store. L’option **Non configuré** empêche les utilisateurs d’activer le paramètre **Sources inconnues**.
- **Autoriser l’accès à toutes les applications dans Google Play Store** : lorsque cette option est définie sur **Autoriser**, les utilisateurs peuvent accéder à toutes les applications dans Google Play Store. Ils ne peuvent pas accéder aux applications bloquées par l’administrateur dans [Applications clientes](apps-add-android-for-work.md). **Non configuré** oblige les utilisateurs à n’accéder qu’aux applications rendues disponibles par l’administrateur dans Google Play Store ou aux applications requises dans [Applications clientes](apps-add-android-for-work.md).
- **Mises à jour automatiques d'application** : choisissez à quel moment installer les mises à jour automatiques. Les options disponibles sont les suivantes :
  - **Non configuré**
  - **Choix de l’utilisateur**
  - **Jamais**
  - **Wi-Fi uniquement**
  - **Toujours**

### <a name="connectivity"></a>Connectivité

- **VPN Always On** : choisissez **Activer** pour indiquer à un client VPN de se connecter et de se reconnecter automatiquement au réseau VPN. Les connexions VPN Always On restent activées ou s’activent immédiatement quand l’utilisateur verrouille ou redémarre son appareil, ou quand le réseau sans fil change. 

  Choisissez **Non configuré** pour désactiver en permanence la fonctionnalité VPN Always On pour tous les clients VPN.

  > [!IMPORTANT]
  > Veillez à ne déployer qu’une seule stratégie VPN Always On sur un seul appareil. Le déploiement de plusieurs stratégies VPN Always On sur un seul appareil n’est pas pris en charge.

- **Client VPN** : choisissez un client VPN qui prend en charge Always On. Les options disponibles sont les suivantes :
  - Cisco AnyConnect
  - Accès F5
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personnalisé
    - **ID de package** : entrez l’ID de package de l’application dans le Google Play Store. Par exemple, si l’URL de l’application dans le Play Store est `https://play.google.com/store/details?id=com.contosovpn.android.prod`, l’ID de package est `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Le client VPN que vous choisissez doit être installé sur l’appareil et doit prendre en charge le VPN par application dans les profils professionnels. Sinon, une erreur se produit. 
  > - Vous devez approuver l’application cliente VPN dans le **Google Play Store géré**, la synchroniser avec Intune et la déployer sur l’appareil. Une fois l’opération effectuée, l’application est installée dans le profil professionnel de l’utilisateur.
  > - Il peut exister des problèmes connus liés à l’utilisation du VPN par application avec un accès F5 pour Android 3.0.4. Pour plus d’informations, consultez [Release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) sur le site F5.

- **Mode de verrouillage** : choisissez **Activer** pour forcer l’ensemble du trafic réseau à utiliser le tunnel VPN. Si aucune connexion au VPN n’est établie, l’appareil n’a pas d’accès réseau.

  Choisissez **Non configuré** pour permettre au trafic de passer par le tunnel VPN ou le réseau mobile.

## <a name="work-profile-only"></a>Profil professionnel uniquement 

### <a name="work-profile-settings"></a>Paramètres de profil professionnel

#### <a name="general"></a>Général

- **Copier-coller entre les profils professionnel et personnel** : choisissez **Bloquer** pour empêcher les opérations copier et coller entre les applications professionnelles et personnelles. L’option **Non configuré** permet aux utilisateurs de partager des données par copier-coller dans les applications du profil personnel 
- **Partage des données entre les profils professionnels et personnels** : choisissez si les applications associées au profil professionnel peuvent ou non partager avec des applications du profil personnel. Par exemple, vous pouvez contrôler les actions de partage dans les applications, notamment l’option **Partager** dans l’application de navigateur Chrome. Ce paramètre ne s’applique pas au comportement du Presse-papiers pour les opérations de type copier/coller. Voici vos options de partage :
  - **Restrictions de partage par défaut** : comportement de partage par défaut de l’appareil, qui varie en fonction de la version d’Android. Par défaut, le partage du profil personnel vers le profil professionnel est autorisé. Le partage du le profil professionnel vers le profil personnel est aussi bloqué par défaut. Ce paramètre empêche les partages de données du profil professionnel vers le profil personnel. Sur les appareils exécutant les versions 6.0 et ultérieures, Google ne bloque pas le partage du profil personnel vers le profil professionnel.
  - **Les applications du profil professionnel peuvent gérer une demande de partage provenant d’un profil personnel** : active la fonctionnalité Android intégrée qui autorise le partage entre le profil personnel et le profil professionnel. Lorsque cette option est activée, une demande de partage à partir d’une application du profil personnel peut partager avec les applications associées au profil professionnel. Ce paramètre est le comportement par défaut des appareils Android exécutant des versions antérieures à 6.0.
  - **Autoriser le partage en dehors des limites** : permet le partage dans les deux sens au-delà de la limite du profil professionnel. Lorsque vous sélectionnez ce paramètre, les applications du profil de travail peuvent partager des données avec des applications sans badge du profil personnel. Ce paramètre autorise le partage des applications gérées du profil professionnel avec les applications situées du côté non géré de l’appareil. Vous devez donc utiliser ce paramètre avec précaution.

- **Notifications du profil professionnel quand l’appareil est verrouillé** : permet de déterminer si les applications du profil professionnel peuvent afficher des données dans des notifications quand l’appareil est verrouillé. L’option **Bloquer** n’affiche pas les données. L’option **Non configuré** affiche les données.
- **Autorisations des applications par défaut** : définit la stratégie d’autorisation par défaut pour toutes les applications du profil professionnel. À compter d’Android 6, l’utilisateur est invité à accorder certaines autorisations requises par les applications lorsque l’application est lancée. Ce paramètre de stratégie vous permet de décider si les utilisateurs sont invités à accorder des autorisations pour toutes les applications du profil professionnel. Par exemple, vous pouvez affecter au profil professionnel une application qui nécessite un accès à l’emplacement. Normalement, cette application invite l’utilisateur à approuver ou refuser l’accès à l’emplacement pour l’application. Utilisez cette stratégie pour accorder automatiquement les autorisations sans invite, refuser automatiquement les autorisations sans invite, ou laisser l’utilisateur final décider. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Demander**
  - **Accorder automatiquement**
  - **Refuser automatiquement**

  Vous pouvez également utiliser une stratégie de configuration d’application pour accorder des autorisations à des applications individuelles (**Applications clientes** > **Stratégies de configuration des applications**).

- **Ajouter et supprimer des comptes** : choisissez **Bloquer** pour empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel. Par exemple, quand vous déployez l’application Gmail dans un profil professionnel Android, vous pouvez empêcher les utilisateurs finaux d’ajouter ou de supprimer des comptes dans ce profil professionnel. L’option **Non configuré** permet d’ajouter des comptes dans le profil professionnel.  

- **Partage de contacts via Bluetooth** : permet d’accéder aux contacts professionnels à partir d’un autre appareil, par exemple une voiture, qui est apparié à l’aide de Bluetooth. Ce paramètre n’étant pas configuré par défaut, les contacts du profil professionnel ne sont pas visibles. Sélectionnez **Activer** pour autoriser ce partage et afficher les contacts de profil professionnel. Ce paramètre s’applique aux appareils avec profil professionnel Android sur le système d’exploitation Android 6.0 et versions ultérieures. L’activation de ce paramètre peut permettre à certains appareils Bluetooth de mettre en cache des contacts professionnels à la première connexion. La désactivation de cette stratégie après un jumelage/une synchronisation initiale ne supprime pas toujours les contacts professionnels d’un appareil Bluetooth.

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil dans le profil professionnel. Cela empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée. L’option **Non configuré** permet d’effectuer des captures d’écran.

- **Afficher l’ID d’appelant du contact professionnel dans le profil personnel** : quand ce paramètre est activé (**non configuré**), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Si cette option est définie sur **Bloquer**, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. S’applique à Android OS v6.0 et versions plus récentes.

- **Rechercher des contacts professionnels à partir du profil personnel** : choisissez **Bloquer** pour empêcher les utilisateurs de rechercher des contacts professionnels dans des applications du profil personnel. L’option **Non requis** permet de rechercher des contacts professionnels dans le profil personnel.

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil dans le profil professionnel. L’appareil photo dans le profil personnel n’est pas affectée par ce paramètre. L’option **Non requis** autorise l’accès à l’appareil photo dans le profil professionnel.

#### <a name="work-profile-password"></a>Mot de passe de profil professionnel

- **Exiger le mot de passe du profil professionnel** : s’applique à Android 7.0 et ultérieur avec profil professionnel activé. Choisissez **Exiger** pour définir une stratégie de mot de passe qui s’applique uniquement aux applications dans le profil professionnel. Par défaut, l’utilisateur final peut utiliser les deux codes PIN définis séparément ou choisir de combiner les deux codes PIN définis dans le plus sécurisé des deux. L’option **Non configuré** permet l’utilisation d’applications professionnelles, sans entrer de mot de passe.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères du mot de passe de l’utilisateur (**4**-**16**).
- **Nombre maximal de minutes d’inactivité avant le verrouillage du profil professionnel** : sélectionnez le délai de verrouillage du profil professionnel. L’utilisateur doit ensuite entrer ses informations d’identification pour rétablir l’accès.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre de saisies possibles d’un mot de passe incorrect avant que le profil professionnel soit supprimé.
- **Expiration du mot de passe (jours)**  : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (**1**-**255**).
- **Type de mot de passe requis** : sélectionnez le type de mot de passe qui doit être défini sur l’appareil. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Obligatoire**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs, par exemple « 1111 » ou « 1234 » ne sont pas autorisés
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe (**1**-**24**).
- **Déverrouillage par empreinte digitale** : choisissez **Bloquer** pour empêcher l’utilisation du lecteur d’empreintes digitales de l’appareil pour le déverrouiller. L’option **Non configuré** permet aux utilisateurs de déverrouiller des appareils à l’aide d’une empreinte digitale dans le profil professionnel.
- **Smart Lock et autres agents de confiance** : choisissez **Bloquer** pour empêcher Smart Lock ou d’autres agents de confiance d’ajuster les paramètres d’écran de verrouillage sur les appareils compatibles. Cette fonctionnalité, également connue sous le nom d’agent de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil, si ce dernier se trouve dans un emplacement approuvé. Par exemple, contournez le mot de passe du profil professionnel quand l’appareil est connecté à un appareil Bluetooth spécifique, ou quand il est à proximité d’une étiquette NFC. Utilisez ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.

### <a name="device-password"></a>Mot de passe de l’appareil

Ces paramètres de mot de passe s’appliquent aux profils personnels des appareils qui utilisent un profil professionnel.

- **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères du mot de passe de l’utilisateur (**4**-**14**).
- **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** : sélectionnez le délai de verrouillage automatique d’un appareil inactif.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre de saisies possibles d’un mot de passe incorrect avant que toutes les données de l’appareil soient supprimées.
- **Expiration du mot de passe (jours)**  : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (**1**-**255**).
- **Type de mot de passe requis** : sélectionnez le type de mot de passe qui doit être défini sur l’appareil. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Obligatoire**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs tels que « 1111 » ou « 1234 » ne sont pas autorisés.
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe (**1**-**24**).
- **Déverrouillage par empreinte digitale** : choisissez **Bloquer** pour empêcher l’utilisation du lecteur d’empreintes digitales de l’appareil pour le déverrouiller. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.
- **Smart Lock et autres agents de confiance** : choisissez **Bloquer** pour empêcher Smart Lock ou d’autres agents de confiance d’ajuster les paramètres d’écran de verrouillage sur les appareils compatibles. Cette fonctionnalité, également connue sous le nom d’agent de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil, si ce dernier se trouve dans un emplacement approuvé. Par exemple, contournez le mot de passe du profil professionnel quand l’appareil est connecté à un appareil Bluetooth spécifique, ou quand il est à proximité d’une étiquette NFC. Utilisez ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.

### <a name="system-security"></a>Sécurité système

- **Analyse des menaces sur les applications** : l’option **Exiger** applique la règle indiquant que le paramètre **Vérifier les applications** est activé pour les profils professionnels et personnels.

   > [!Note]
   > Ce paramètre ne fonctionne que pour les appareils Android O et versions supérieures.

### <a name="connectivity"></a>Connectivité

- **VPN Always On** : choisissez **Activer** pour indiquer à un client VPN de se connecter et de se reconnecter automatiquement au réseau VPN. Les connexions VPN Always On restent activées ou s’activent immédiatement quand l’utilisateur verrouille ou redémarre son appareil, ou quand le réseau sans fil change. 

  Choisissez **Non configuré** pour désactiver en permanence la fonctionnalité VPN Always On pour tous les clients VPN.

  > [!IMPORTANT]
  > Veillez à ne déployer qu’une seule stratégie VPN Always On sur un seul appareil. Le déploiement de plusieurs stratégies VPN Always On sur un seul appareil n’est pas pris en charge.

- **Client VPN** : choisissez un client VPN qui prend en charge Always On. Les options disponibles sont les suivantes :
  - Cisco AnyConnect
  - Accès F5
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personnalisé
    - **ID de package** : entrez l’ID de package de l’application dans le Google Play Store. Par exemple, si l’URL de l’application dans le Play Store est `https://play.google.com/store/details?id=com.contosovpn.android.prod`, l’ID de package est `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Le client VPN que vous choisissez doit être installé sur l’appareil et doit prendre en charge le VPN par application dans les profils professionnels. Sinon, une erreur se produit. 
  > - Vous devez approuver l’application cliente VPN dans le **Google Play Store géré**, la synchroniser avec Intune et la déployer sur l’appareil. Une fois l’opération effectuée, l’application est installée dans le profil professionnel de l’utilisateur.
  > - Il peut exister des problèmes connus liés à l’utilisation du VPN par application avec un accès F5 pour Android 3.0.4. Pour plus d’informations, consultez [Release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) sur le site F5.

- **Mode de verrouillage** : choisissez **Activer** pour forcer l’ensemble du trafic réseau à utiliser le tunnel VPN. Si aucune connexion au VPN n’est établie, l’appareil n’a pas d’accès réseau.

  Choisissez **Non configuré** pour permettre au trafic de passer par le tunnel VPN ou le réseau mobile.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils plein écran pour des appareils [Android](device-restrictions-android.md#kiosk) et [Windows 10](kiosk-settings.md) dédiés.

## <a name="see-also"></a>Voir aussi

[Configuration et dépannage des appareils d’entreprise Android dans Microsoft Intune](https://support.microsoft.com/help/4476974)
