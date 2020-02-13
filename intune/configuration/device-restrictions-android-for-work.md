---
title: Paramètres d’appareil Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils Android Entreprise et Android for Work, vous pouvez restreindre certains paramètres, notamment les opérations de copier-coller, l’affichage des notifications, les autorisations d’application, le partage de données, la longueur de mot de passe, les échecs de connexion, l’utilisation d’empreintes digitales pour le déverrouillage, la réutilisation des mots de passe et l’activation du partage Bluetooth des contacts professionnels. Configurez les appareils comme appareils dédiés plein écran pour exécuter une ou plusieurs applications.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122f0b0194a96b844e274ab39a73224eb23cc6b3
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051590"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités avec Intune

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils Android Entreprise. Dans votre solution de gestion des appareils mobiles, utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, pour exécuter les applications sur les appareils dédiés, pour contrôler la sécurité, et bien plus encore.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Propriétaire de l’appareil uniquement

Ces paramètres s’appliquent aux types d’inscription d’Android Enterprise où Intune contrôle la totalité de l’appareil, comme les appareils Android Enterprise complètement managés ou dédiés.

### <a name="general-settings"></a>Paramètres généraux :

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. Cela empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée. L’option **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran comme image.
- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option **Non requis** autorise l’accès à l’appareil photo de l’appareil.
- **Stratégie d’autorisation par défaut** : ce paramètre définit la stratégie d’autorisation par défaut pour les demandes d’autorisations d’exécution. Les valeurs possibles sont :
  - **Paramètre par défaut de l’appareil** : utilise le paramètre par défaut de l’appareil.
  - **Demander** : l’utilisateur est invité à approuver l’autorisation.
  - **Accorder automatiquement** : les autorisations sont automatiquement accordées.
  - **Refuser automatiquement** : les autorisations sont automatiquement refusées.
- **Changements de date et d’heure** : choisissez **Bloquer** pour empêcher les utilisateurs de régler manuellement la date et l’heure. L’option **Non configuré** autorise les utilisateurs à régler la date et l’heure sur l’appareil.
- **Changements du volume** : **Bloquer** empêche les utilisateurs de modifier le volume de l’appareil et désactive le son du volume maître. L’option **Non configuré** autorise l’utilisation des paramètres de volume sur l’appareil.
- **Réinitialisation aux paramètres d’usine** : choisissez **Bloquer** pour empêcher les utilisateurs de réinitialiser l’appareil aux paramètres d’usine. L’option **Non configuré** permet aux utilisateurs d’utiliser ce paramètre sur l’appareil.
- **Démarrage sans échec** : choisissez **Bloquer** pour empêcher les utilisateurs de redémarrer l’appareil en mode sans échec. L’option **Non configuré** autorise les utilisateurs à redémarrer l’appareil en mode sans échec.
- **Barre d’état** : choisissez **Bloquer** pour empêcher les utilisateurs d’accéder à la barre d’état, notamment aux notifications et aux paramètres rapides. L’option **Non configuré** autorise les utilisateurs à accéder à la barre d’état.
- **Itinérance des services de données** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Changements des paramètres Wi-Fi** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres Wi-Fi créés par le propriétaire de l’appareil. Les utilisateurs peuvent créer leurs propres configurations Wi-Fi. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres Wi-Fi sur l’appareil.
- **Configuration du point d’accès Wi-Fi** : choisissez **Bloquer** pour empêcher les utilisateurs de créer ou de modifier des configurations Wi-Fi. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres Wi-Fi sur l’appareil.
- **Configuration Bluetooth** : choisissez **Bloquer** pour empêcher les utilisateurs de configurer le Bluetooth sur l’appareil. L’option **Non configuré** autorise l’utilisation du Bluetooth sur l’appareil.
- **Connexion et accès aux points d’accès** : choisissez **Bloquer** pour empêcher la connexion et l’accès aux points d’accès mobiles. L’option **Non configuré** permet d’accéder de se connecter et d’accéder aux points d’accès mobiles.
- **Stockage USB** : choisissez **Autoriser** pour accéder au stockage USB sur l’appareil. L’option **Non configuré** empêche l’accès au stockage USB.
- **Transfert de fichiers USB** : choisissez **Bloquer** pour empêcher le transfert de fichiers via USB. L’option **Non configuré** autorise le transfert de fichiers.
- **Support externe** : choisissez **Bloquer** pour empêcher l’utilisation ou la connexion d’un support externe sur l’appareil. L’option **Non configuré** autorise l’utilisation d’un support externe sur l’appareil.
- **Transmettre des données à l’aide de NFC** : choisissez **Bloquer** afin d’empêcher l’utilisation de la technologie Near Field Communication (NFC) pour transmettre des données à partir d’applications. L’option **Non configuré** autorise l’utilisation de NFC pour partager des données entre les appareils.
- **Fonctionnalités de débogage** : choisissez **Autoriser** pour permettre l’utilisation des fonctionnalités de débogage sur l’appareil. L’option **Non configuré** empêche l’utilisation des fonctionnalités de débogage sur l’appareil.
- **Réglage du microphone** : choisissez **Bloquer** pour empêcher les utilisateurs d’activer le microphone et d’en régler le volume. L’option **Non configuré** permet l’utilisation du microphone et le réglage de son volume sur l’appareil.
- **E-mails de protection contre la réinitialisation aux paramètres d’usine** : choisissez **Adresses e-mail du compte Google**. Entrez les adresses e-mail des administrateurs de l’appareil autorisés à déverrouiller l’appareil réinitialisé. Veillez à séparer les adresses e-mail par un point-virgule, par exemple `admin1@gmail.com;admin2@gmail.com`. Si aucune adresse e-mail n’est spécifiée, quiconque peut déverrouiller un appareil réinitialisé aux paramètres d’usine. Ces e-mails s’appliquent seulement quand une réinitialisation aux paramètres d’usine non demandée par l’utilisateur est exécutée, comme l’exécution d’une réinitialisation aux paramètres d’usine via le menu de récupération.
- **Trappe de secours du réseau** : choisissez **Activer** pour autoriser les utilisateurs à activer la fonctionnalité de trappe de secours du réseau. Si aucune connexion réseau n’est établie au démarrage de l’appareil, la trappe de secours vous demande de vous connecter temporairement à un réseau et d’actualiser la stratégie de l’appareil. Une fois la stratégie appliquée, le réseau temporaire est oublié et l’appareil continue de démarrer. Cette fonctionnalité connecte les appareils à un réseau si :
  - La dernière stratégie ne contient aucun réseau approprié.
  - L’appareil démarre dans une application en mode de verrouillage de tâche.
  - L’utilisateur ne peut pas atteindre les paramètres de l’appareil.

  L’option **Non configuré** empêche les utilisateurs d’activer la fonctionnalité de trappe de secours du réseau sur l’appareil.

- **Mise à jour système** : choisissez une option pour définir la façon dont l’appareil traite les mises à jour à distance :
  - **Paramètre par défaut de l’appareil** : utilise le paramètre par défaut de l’appareil.
  - **Automatique** : les mises à jour sont installées automatiquement, sans interaction de l’utilisateur. La définition de cette stratégie entraîne l’installation immédiate des mises à jour en attente.
  - **Différé** : les mises à jour sont reportées de 30 jours. À la fin des 30 jours, Android invite l’utilisateur à installer la mise à jour. Il est possible pour les fabricants ou les opérateurs d’appareils d’empêcher (exempter) le report des mises à jour de sécurité importantes. Une mise à jour exemptée affiche une notification système sur l’appareil de l’utilisateur.
  - **Fenêtre de maintenance** : permet d’installer les mises à jour automatiquement durant une fenêtre de maintenance quotidienne définie dans Intune. L’installation est tentée quotidiennement pendant 30 jours, et cette opération peut échouer en raison d’un espace ou d’un niveau de batterie insuffisant. Après 30 jours, Android invite l’utilisateur à procéder à l’installation. Cette fenêtre est également utilisée pour installer les mises à jour des applications Play. Utilisez cette option pour les appareils dédiés, par exemple les bornes, car les applications de premier plan d’appareils mono-application dédiés peuvent être mises à jour.

- **Fenêtres de notification** : quand cette option a la valeur **Désactiver**, les notifications, notamment les toasts, les appels entrants, les appels sortants, les alertes système et les erreurs système, ne sont pas affichées sur l’appareil. quand elle a la valeur **Non configuré**, les paramètres par défaut du système d’exploitation sont utilisés (ce qui peut entraîner l’affichage des notifications).
- **Ignorer les premiers conseils d’utilisation** : **Activer** masque ou ignore les suggestions des applications qui dirigent vers des tutoriels, ou les conseils au démarrage de l’application. Quand vous affectez la valeur **Non configuré**, les paramètres par défaut du système d’exploitation sont utilisés (ce qui peut entraîner l’affichage de ces suggestions au démarrage de l’application).

### <a name="system-security-settings"></a>Paramètres de sécurité système

- **Exiger l’analyse des menaces sur les applications** : **Exiger** (par défaut) permet à Google Play Protect d’analyser les applications avant et après leur installation. S’il détecte une menace, il peut avertir l’utilisateur et lui recommander de supprimer l’application de l’appareil. **Non configuré** ne permet pas à Google Play Protect d’analyser des applications.

### <a name="dedicated-device-settings"></a>Paramètres de l’appareil dédié

Utilisez ces paramètres pour configurer une expérience plein écran sur vos appareils dédiés. Vous pouvez configurer un appareil pour exécuter une ou plusieurs applications. Quand un appareil est en mode plein écran, seules les applications que vous ajoutez sont disponibles. Ces paramètres s’appliquent aux appareils Android Enterprise dédiés. Ils ne sont pas appliqués à des appareils Android Enterprise entièrement gérés.

**Mode kiosque** : choisissez si l’appareil exécute une ou plusieurs applications.

- **Une seule application** : les utilisateurs ne peuvent accéder qu’à une seule application sur l’appareil. Lors du démarrage de l’appareil, seule l’application spécifique démarre. Les utilisateurs ne peuvent pas ouvrir de nouvelles applications, ni changer l’application en cours d’exécution.

  - **Sélectionner une application gérée** : sélectionnez l’application Google Play gérée dans la liste.

    Si la liste ne contient aucune application, [ajoutez des applications Android](../apps/apps-add-android-for-work.md) à l’appareil. Veillez à [attribuer l’application au groupe d’appareils créé pour vos appareils dédiés](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Lors de l’utilisation du mode kiosque mono-application, les applications de numéroteur/téléphone peuvent ne pas fonctionner correctement. 
  
- **Multi-application** : les utilisateurs peuvent accéder à un ensemble limité d’applications sur l’appareil. Lors du démarrage de l’appareil, seules les applications que vous ajoutez s’exécutent. Vous pouvez également ajouter des liens web que les utilisateurs peuvent ouvrir. Quand la stratégie est appliquée, les utilisateurs voient des icônes pour les applications autorisées dans l’écran d’accueil.

  > [!IMPORTANT]
  > Pour les appareils multi-application dédiés, l’application [Managed Home Screen](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) à partir de Google Play **doit être** :
  >   - [Ajoutée en tant qu’application cliente](../apps/apps-add-android-for-work.md) dans Intune
  >   - [Attribuée au groupe d’appareils](../apps/apps-deploy.md) créé pour vos appareils dédiés
  >
  > L’application **Managed Home Screen** ne doit pas nécessairement figurer dans le profil de configuration, mais elle doit être ajoutée comme une application cliente. Lorsque l’application **Managed Home Screen** est ajoutée comme application cliente, toutes les autres applications que vous ajoutez au profil de configuration apparaissent sous forme d’icônes dans l’application **Managed Home Screen**.
  >
  > Quand vous utilisez le mode kiosque multi-application, les applications de numéroteur/téléphone peuvent ne pas fonctionner correctement. 

  - **Ajouter** : sélectionnez vos applications dans la liste.

    Si l’application **Managed Home Screen** n’est pas répertoriée, [ajoutez-la à partir de Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Veillez à [attribuer l’application](../apps/apps-deploy.md) au groupe d’appareils créé pour vos appareils dédiés.

    Vous pouvez également ajouter à l’appareil d’autres [applications Android](../apps/apps-add-android-for-work.md) et [applications web](../apps/web-app.md) créées par votre organisation. Veillez à [attribuer l’application au groupe d’appareils créé pour vos appareils dédiés](../apps/apps-deploy.md).

  - **Bouton Accueil virtuel** : bouton de touche programmable qui renvoie les utilisateurs à Managed Home Screen, qui leur permet de basculer entre les applications. Les options disponibles sont les suivantes :

    - **Non configuré** (par défaut) : il n’est pas montré de bouton d’accueil. Les utilisateurs doivent utiliser le bouton Précédent pour basculer entre les applications.
    - **Balayer vers le haut** : un bouton d’accueil apparaît quand un utilisateur effectue un balayage vers le haut sur l’appareil.
    - **Flottant** : affiche un bouton d’accueil permanent et flottant sur l’appareil.

  - **Quitter le mode kiosque** : choisissez **Activer** pour autoriser les administrateurs à quitter temporairement le mode kiosque pour mettre à jour l’appareil. Pour utiliser cette fonctionnalité, l’administrateur :
  
    1. continue à sélectionner le bouton de retour jusqu’à ce que le bouton **Quitter le kiosque** s’affiche ; 
    2. sélectionne le bouton **Quitter le kiosque** et entre le code confidentiel **Quitter le code de mode kiosque**.
    3. Quand vous avez terminé, sélectionnez l’application **Managed Home Screen**. Cette étape verrouille à nouveau l’appareil en mode kiosque multi-application.

      Si la valeur est **Non configuré**, les administrateurs ne peuvent pas suspendre le mode kiosque. Si l’administrateur continue de cliquer sur le bouton Précédent et sélectionne le bouton **Quitter le kiosque**, un message indique qu’un code secret est requis.

    - **Code permettant de quitter le mode kiosque**  : entrez un code PIN numérique de 4 à 6 chiffres. L’administrateur utilise ce code PIN pour interrompre temporairement le mode kiosque.

  - **Définir l’arrière-plan de l’URL personnalisée** : entrez une URL pour personnaliser l’arrière-plan de l’appareil dédié.

    > [!NOTE]
    > Dans la plupart des cas, nous recommandons de commencer avec des images des tailles minimales suivantes :
    >
    > - Téléphone : 1080 x 1920 px
    > - Tablette : 1920 x 1080 px
    >
    > Pour une expérience optimale et claire, il est conseillé de créer des composants d’images par appareil selon les caractéristiques de l’écran.
    >
    > Les écrans modernes affichent une densité supérieure de pixels et peuvent obtenir une définition d’image 2K/4K.

  - **Configuration Wi-Fi** : **Activer** montre le contrôle Wi-Fi sur Managed Home Screen et permet aux utilisateurs finaux de connecter l’appareil à différents réseaux Wi-Fi. L’activation de cette fonctionnalité active également l’emplacement de l’appareil. **Non configuré** (par défaut) n’affiche pas le contrôle Wi-Fi sur Managed Home Screen. Il empêche les utilisateurs de se connecter aux réseaux Wi-Fi pendant l’utilisation de Managed Home Screen.

  - **Configuration Bluetooth** : **Activer** montre le contrôle Bluetooth sur Managed Home Screen et permet aux utilisateurs finaux d’appairer des appareils sur Bluetooth. L’activation de cette fonctionnalité active également l’emplacement de l’appareil. **Non configuré** (par défaut) ne montre pas le contrôle Bluetooth sur Managed Home Screen. Il empêche les utilisateurs de configurer Bluetooth et d’appairer des appareils pendant l’utilisation de Managed Home Screen.

  - **Accès à la lampe torche** : **Activer** montre le contrôle de torche sur Managed Home Screen et permet aux utilisateurs finaux d’activer ou de désactiver la torche. **Non configuré** (par défaut) ne montre pas le contrôle de torche sur Managed Home Screen. Il empêche les utilisateurs d’utiliser la torche pendant l’utilisation de Managed Home Screen.

  - **Contrôle du volume du média** : **Activer** montre le contrôle du volume du média sur Managed Home Screen et permet aux utilisateurs finaux d’ajuster le volume du média de l’appareil à l’aide d’un curseur. **Non configuré** (par défaut) ne montre pas la commande du volume multimédia sur Managed Home Screen. Il empêche les utilisateurs de régler le volume multimédia de l’appareil pendant l’utilisation de Managed Home Screen, sauf si ses boutons physiques le permettent. 

  - **Mode écran de veille** : **Activer** montre un écran de veille sur Managed Home Screen quand l’appareil est verrouillé ou dépasse le délai d’expiration. **Non configuré** (par défaut) ne montre pas d’écran de veille sur Managed Home Screen.

    Quand cette option est activée, configurez également :

    - **Définir une image d’écran de veille personnalisée** : entrez l’URL d’un fichier PNG, JPG, JPEG, GIF, BMP, WebP ou ICOimage personnalisé. Par exemple, entrez :

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.webp`

      Si vous n’entrez pas d’URL, l’image par défaut de l’appareil est utilisée, s’il existe une image par défaut.
      
      > [!TIP]
      > Toute URL de ressource de fichier qui peut être transformée en bitmap est prise en charge.

    - **Durée en secondes pendant laquelle l’appareil affiche l’écran de veille avant d’éteindre l’écran** : choisissez la durée pendant laquelle l’appareil montre l’écran de veille. Entrez une valeur comprise entre 0 et 9999999 secondes. La valeur par défaut est de `0` secondes. Quand il est laissé vide ou défini sur zéro (`0`), l’économiseur d’écran est actif jusqu’à ce qu’un utilisateur interagisse avec l’appareil.
    - **Durée d’inactivité en secondes de l’appareil avant l’affichage de l’écran de veille** : choisissez la durée d’inactivité de l’appareil avant de montrer l’écran de veille. Entrez une valeur comprise entre 1 et 9999999 secondes. La valeur par défaut est de `30` secondes. Vous devez entrer un nombre supérieur à zéro (`0`).
    - **Détecter la présence d’un média avant de démarrer l’écran de veille** : **Activer** (par défaut) ne montre pas l’écran de veille si l’audio ou la vidéo est en cours de lecture sur l’appareil. **Non configuré** montre l’écran de veille, même si l’audio ou la vidéo est en cours de lecture.

### <a name="device-password-settings"></a>Paramètres de mot de passe des appareils

- **Désactiver l’écran de verrouillage** : choisissez **Désactiver** pour empêcher l’utilisation de la fonctionnalité de verrouillage d’écran Keyguard sur l’appareil. L’option **Non configuré** permet l’utilisation des fonctionnalités Keyguard.
- **Désactivé sur l’écran de verrouillage** : quand keyguard est activé sur l’appareil, choisissez les fonctionnalités à désactiver. Par exemple, quand l’option **Sécuriser l’appareil photo** est cochée, la fonctionnalité appareil photo est désactivée sur l’appareil. Toutes les fonctionnalités non cochées sont activées sur l’appareil.

  Ces fonctionnalités sont disponibles pour les utilisateurs lorsque l’appareil est verrouillé. Les utilisateurs ne verront pas les fonctionnalités vérifiées ni ne pourront y accéder.

- **Type de mot de passe requis** : définissez le type de mot de passe demandé pour l’appareil. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Mot de passe requis, sans restriction**
  - **Biométrie faible** : [Biométrie forte et faible](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (dirige sur le site web d’Android)
  - **Numérique** : le mot de passe ne doit comporter que des nombres, par exemple `123456789`. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Chiffres complexes** : les chiffres répétés ou consécutifs (comme « 1111 » ou « 1234 ») ne sont pas autorisés. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Alphabétique** : des lettres de l’alphabet sont nécessaires. Les nombres et symboles ne sont pas nécessaires. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Alphanumériques** : inclut des lettres majuscules, minuscules et des caractères numériques. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Alphanumérique avec symboles** : inclut des lettres majuscules, minuscules, des caractères numériques, des signes de ponctuation et des symboles. Entrez également :

    - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe (entre 4 et 16 caractères).
    - **Nombre de caractères obligatoires** : entrez le nombre de caractères du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères minuscules obligatoires** : entrez le nombre de caractères en minuscules du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères majuscules obligatoires** : entrez le nombre de caractères en majuscules du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères obligatoires autres que des lettres** : entrez le nombre de caractères non lettres (tout caractère hors lettres de l’alphabet) du mot de passe (entre 0 et 16 caractères).
    - **Nombre de caractères numériques obligatoires** : entrez le nombre de caractères numériques (`1`, `2`, `3`, etc.) du mot de passe (entre 0 et 16 caractères).
    - **Nombre de symboles obligatoires** : entrez le nombre de symboles (`&`, `#`, `%`, etc.) du mot de passe (entre 0 et 16 caractères).

- **Nombre de jours avant expiration du mot de passe** : entrez le nombre de jours (entre 1 et 365) après lesquels l’utilisateur doit changer le mot de passe de l’appareil. Par exemple, pour modifier le mot de passe après 60 jours, entrez `60`. Lorsque le mot de passe arrive à expiration, les utilisateurs sont invités à créer un mot de passe.
- **Nombre de mots de passe obligatoires avant que l’utilisateur puisse en réutiliser un** : entrez le nombre de mots de passe récents qui ne peuvent pas être réutilisés, entre 1 et 24. Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : spécifie le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil (entre 4 et 11).

### <a name="power-settings"></a>Paramètres d’alimentation

- **Délai avant verrouillage de l’écran** : entrez la durée maximale qu’un utilisateur peut définir pour le délai avant que l’appareil soit verrouillé. Par exemple, si vous définissez ce paramètre sur **10 minutes**, les utilisateurs peuvent définir une durée allant de 15 secondes à 10 minutes. Quand il est défini sur **Non configuré** (par défaut), Intune ne change pas ou ne contrôle pas ce paramètre.

- **Écran actif quand l’appareil est branché** : choisissez quelles sources d’alimentation permettent de maintenir l’écran actif lorsque l’appareil est branché.

### <a name="users-and-accounts-settings"></a>Paramètres des utilisateurs et des comptes

- **Ajouter de nouveaux utilisateurs** : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter de nouveaux utilisateurs. Chaque utilisateur dispose d’un espace personnel sur l’appareil, regroupant les écrans d’accueil personnalisés ainsi que les comptes, applications et paramètres. L’option **Non configuré** (par défaut) autorise les utilisateurs à ajouter d’autres utilisateurs à l’appareil.
- **Suppression d’utilisateurs** : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des utilisateurs. L’option **Non configuré** (par défaut) autorise les utilisateurs à supprimer d’autres utilisateurs de l’appareil.
- **Modifications du compte** (appareils dédiés uniquement) : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les comptes. L’option **Non configuré** (par défaut) autorise les utilisateurs à mettre à jour les comptes d’utilisateurs sur l’appareil.

  > [!NOTE]
  > Ce paramètre n’est pas respecté sur les appareils (complètement managés) du propriétaire de l’appareil. Si vous configurez ce paramètre, le paramètre est ignoré et n’a aucun impact.

- **L’utilisateur peut configurer les informations d’identification** : **Bloquer** empêche les utilisateurs de configurer des certificats affectés à des appareils, même des appareils qui ne sont pas associés à un compte d’utilisateur. **Non configuré** peut permettre aux utilisateurs de configurer ou de changer leurs informations d’identification quand ils y accèdent dans le magasin de clés. 
- **Comptes Google personnels** : **Bloquer** empêche les utilisateurs d’ajouter leur compte Google personnel à l’appareil. **Non configuré** (par défaut) permet aux utilisateurs d’ajouter leur compte Google personnel.

### <a name="applications"></a>Applications

- **Autoriser l’installation à partir de sources inconnues** : choisissez **Autoriser** pour que les utilisateurs puissent activer les **Sources inconnues**. Ce paramètre permet aux applications d’être installées à partir de sources inconnues, y compris celles ne provenant pas de Google Play Store. L’option **Non configuré** empêche les utilisateurs d’activer le paramètre **Sources inconnues**.
- **Autoriser l’accès à toutes les applications dans Google Play Store** : Si cette option est définie sur **Autoriser**, les utilisateurs ont accès à toutes les applications dans Google Play Store. Ils ne peuvent pas accéder aux applications bloquées par l’administrateur dans [Applications clientes](../apps/apps-add-android-for-work.md). **Non configuré** oblige les utilisateurs à n’accéder qu’aux applications rendues disponibles par l’administrateur dans Google Play Store ou aux applications requises dans [Applications clientes](../apps/apps-add-android-for-work.md).
- **Mises à jour automatiques d’application** : choisissez à quel moment installer les mises à jour automatiques. Les options disponibles sont les suivantes :
  - **Non configuré**
  - **Choix de l’utilisateur**
  - **Jamais**
  - **Wi-Fi uniquement**
  - **Toujours**

### <a name="connectivity"></a>Connectivité

- **VPN AlwaysOn** : choisissez **Activer** pour indiquer à un client VPN de se connecter et de se reconnecter automatiquement au réseau VPN. Les connexions VPN Always On restent activées ou s’activent immédiatement quand l’utilisateur verrouille ou redémarre son appareil, ou quand le réseau sans fil change. 

  Choisissez **Non configuré** pour désactiver en permanence la fonctionnalité VPN Always On pour tous les clients VPN.

  > [!IMPORTANT]
  > Veillez à ne déployer qu’une seule stratégie VPN AlwaysOn sur un seul appareil. Le déploiement de plusieurs stratégies VPN AlwaysOn sur un seul appareil n’est pas pris en charge.

- **Client VPN** : choisissez un client VPN qui prend en charge AlwaysOn. Les options disponibles sont les suivantes :
  - Cisco AnyConnect
  - Accès F5
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personnalisé
    - **ID de package** : entrez l’ID de package de l’application dans le Google Play Store. Par exemple, si l’URL de l’application dans le Play Store est `https://play.google.com/store/details?id=com.contosovpn.android.prod`, l’ID de package est `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Le client VPN que vous choisissez doit être installé sur l’appareil et doit prendre en charge le VPN par application dans les profils professionnels. Sinon, une erreur se produit. 
  > - Vous devez approuver l’application cliente VPN dans le **Google Play Store géré**, la synchroniser avec Intune et la déployer sur l’appareil. Une fois l’opération effectuée, l’application est installée dans le profil professionnel de l’utilisateur.
  > - Vous devez néanmoins toujours configurer le client VPN avec un [profil VPN](vpn-settings-android-enterprise.md) ou via un [profil de configuration d’application](../apps/app-configuration-policies-use-android.md).
  > - Il peut exister des problèmes connus liés à l’utilisation du VPN par application avec un accès F5 pour Android 3.0.4. Pour plus d’informations, consultez [Release notes for F5 Access for Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) sur le site F5.

- **Mode de verrouillage** : choisissez **Activer** pour forcer l’ensemble du trafic réseau à utiliser le tunnel VPN. Si aucune connexion au VPN n’est établie, l’appareil n’a pas d’accès réseau.

  Choisissez **Non configuré** pour permettre au trafic de passer par le tunnel VPN ou le réseau mobile.

- **Proxy global recommandé** : choisissez **Activer** pour ajouter un proxy global aux appareils. Quand ce paramètre est activé, le trafic HTTP et HTTPS, y compris certaines applications sur l’appareil, utilisent le proxy que vous entrez. Ce proxy est seulement une recommandation. Il est possible que certaines applications n’utilisent pas le proxy. **Non configuré** (par défaut) n’ajoute pas de proxy global recommandé.

  Pour plus d’informations sur cette fonctionnalité, consultez [setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)) (ouvre un site Android).

  Quand ce paramètre est activé, entrez également le **Type** de proxy. Les options disponibles sont les suivantes :

  - **Direct** : choisissez cette option pour entrer manuellement les détails du serveur proxy, notamment :
    - **Hôte** : entrez le nom d’hôte ou l’adresse IP de votre serveur proxy. Par exemple, entrez `proxy.contoso.com` ou `127.0.0.1`.
    - **Numéro de port** : entrez le numéro de port TCP utilisé par votre serveur proxy. Par exemple, entrez `8080`.
    - **Hôtes exclus** : entrez une liste de noms d’hôtes ou d’adresses IP qui n’utiliseront pas le proxy. Cette liste peut inclure un caractère générique astérisque (`*`) et plusieurs hôtes séparés par des points-virgules (`;`) sans espace. Par exemple, entrez `127.0.0.1;web.contoso.com;*.microsoft.com`.

  - **Configuration automatique du proxy** : entrez l’**URL PAC** vers un script de configuration automatique de proxy. Par exemple, entrez `https://proxy.contoso.com/proxy.pac`.

    Pour plus d’informations sur les fichiers PAC, consultez [Fichier de configuration automatique de proxy (PAC)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (ouvre un site non-Microsoft).

## <a name="work-profile-only"></a>Profil professionnel uniquement

Ces paramètres s’appliquent aux types d’inscription d’Android Enterprise où Intune contrôle seulement le profil professionnel, comme l’inscription de profil professionnel Android Enterprise sur un appareil personnel ou BYOD.

### <a name="work-profile-settings"></a>Paramètres de profil professionnel

#### <a name="general"></a>Général

- **Copier-coller les données entre le profil professionnel et le profil personnel** : choisissez **Bloquer** afin d’empêcher tout copier-coller entre les applications professionnelles et personnelles. L’option **Non configuré** permet aux utilisateurs de partager des données par copier-coller dans les applications du profil personnel 
- **Partage de données entre profils professionnels et personnels** : choisissez cette option pour autoriser les applications du profil professionnel à partager des données avec les applications du profil personnel. Par exemple, vous pouvez contrôler les actions de partage dans les applications, notamment l’option **Partager** dans l’application de navigateur Chrome. Ce paramètre ne s’applique pas au comportement du Presse-papiers pour les opérations de type copier/coller. Voici vos options de partage :
  - **Paramètre par défaut de l’appareil** : comportement de partage par défaut de l’appareil, qui varie en fonction de la version d’Android. Par défaut, le partage du profil personnel vers le profil professionnel est autorisé. Le partage du le profil professionnel vers le profil personnel est aussi bloqué par défaut. Ce paramètre empêche les partages de données du profil professionnel vers le profil personnel. Sur les appareils exécutant les versions 6.0 et ultérieures, Google ne bloque pas le partage du profil personnel vers le profil professionnel.
  - **Les applications du profil professionnel peuvent gérer une demande de partage venant d’un profil personnel** : active la fonctionnalité intégrée Android qui autorise le partage des données entre le profil personnel et le profil professionnel. Lorsque cette option est activée, une demande de partage à partir d’une application du profil personnel peut partager avec les applications associées au profil professionnel. Ce paramètre est le comportement par défaut des appareils Android exécutant des versions antérieures à 6.0.
  - **Empêcher tout partage en dehors des limites** : empêche le partage entre les profils professionnels et personnels.
  - **Aucune restriction sur le partage** : permet le partage dans les deux sens au-delà de la limite du profil professionnel. Lorsque vous sélectionnez ce paramètre, les applications du profil de travail peuvent partager des données avec des applications sans badge du profil personnel. Ce paramètre autorise le partage des applications gérées du profil professionnel avec les applications situées du côté non géré de l’appareil. Vous devez donc utiliser ce paramètre avec précaution.

- **Notifications du profil professionnel quand l’appareil est verrouillé** : permet de déterminer si les applications du profil professionnel peuvent afficher des données dans des notifications quand l’appareil est verrouillé. L’option **Bloquer** n’affiche pas les données. L’option **Non configuré** affiche les données.
- **Autorisations des applications par défaut** : Définit la stratégie d’autorisation par défaut pour toutes les applications dans le profil professionnel. À compter d’Android 6, l’utilisateur est invité à accorder certaines autorisations requises par les applications lorsque l’application est lancée. Ce paramètre de stratégie vous permet de décider si les utilisateurs sont invités à accorder des autorisations pour toutes les applications du profil professionnel. Par exemple, vous pouvez affecter au profil professionnel une application qui nécessite un accès à l’emplacement. Normalement, cette application invite l’utilisateur à approuver ou refuser l’accès à l’emplacement pour l’application. Utilisez cette stratégie pour accorder automatiquement les autorisations sans invite, refuser automatiquement les autorisations sans invite, ou laisser l’utilisateur final décider. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Demander**
  - **Accorder automatiquement**
  - **Refuser automatiquement**

  Vous pouvez également utiliser une stratégie de configuration d’application pour accorder des autorisations à des applications individuelles (**Applications clientes** > **Stratégies de configuration des applications**).

- **Ajouter et supprimer des comptes** : choisissez **Bloquer** pour empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel. Par exemple, quand vous déployez l’application Gmail dans un profil professionnel Android, vous pouvez empêcher les utilisateurs finaux d’ajouter ou de supprimer des comptes dans ce profil professionnel. L’option **Non configuré** permet d’ajouter des comptes dans le profil professionnel.  

  > [!NOTE]
  > Les comptes Google ne peuvent pas être ajoutés à un profil professionnel.

- **Partage de contacts via Bluetooth** : permet d’accéder aux contacts professionnels à partir d’un autre appareil, par exemple une voiture, qui est apparié à l’aide de Bluetooth. Ce paramètre n’étant pas configuré par défaut, les contacts du profil professionnel ne sont pas visibles. Sélectionnez **Activer** pour autoriser ce partage et afficher les contacts de profil professionnel. Ce paramètre s’applique aux appareils avec profil professionnel Android sur le système d’exploitation Android 6.0 et versions ultérieures. L’activation de ce paramètre peut permettre à certains appareils Bluetooth de mettre en cache des contacts professionnels à la première connexion. La désactivation de cette stratégie après un jumelage/une synchronisation initiale ne supprime pas toujours les contacts professionnels d’un appareil Bluetooth.

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil dans le profil professionnel. Cela empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée. L’option **Non configuré** permet d’effectuer des captures d’écran.

- **Afficher l’ID d’appelant du contact professionnel dans le profil personnel** : quand ce paramètre est activé (**Non configuré**), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Si cette option est définie sur **Bloquer**, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. S’applique à Android OS v6.0 et versions plus récentes.

- **Rechercher des contacts professionnels à partir du profil personnel** : choisissez **Bloquer** pour empêcher les utilisateurs de rechercher des contacts professionnels dans des applications du profil personnel. L’option **Non requis** permet de rechercher des contacts professionnels dans le profil personnel.

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil dans le profil professionnel. L’appareil photo dans le profil personnel n’est pas affectée par ce paramètre. L’option **Non requis** autorise l’accès à l’appareil photo dans le profil professionnel.

- **Autoriser les widgets dans les applications du profil professionnel** : **Activer** permet aux utilisateurs finaux de placer les widgets exposés par des applications sur l’écran d’accueil. **Non configuré** (valeur par défaut) désactive cette fonctionnalité.

  Par exemple, Outlook est installé sur les profils professionnels de vos utilisateurs. Quand ce paramètre est défini sur **Activer**, les utilisateurs peuvent placer le widget Agenda sur l’écran d’accueil de l’appareil.

#### <a name="work-profile-password"></a>Mot de passe de profil professionnel

- **Exiger le mot de passe du profil professionnel** : s’applique à Android 7.0 et ultérieur avec profil professionnel activé. Choisissez **Exiger** pour définir une stratégie de mot de passe qui s’applique uniquement aux applications dans le profil professionnel. Par défaut, l’utilisateur final peut utiliser les deux codes PIN définis séparément ou choisir de combiner les deux codes PIN définis dans le plus sécurisé des deux. L’option **Non configuré** permet l’utilisation d’applications professionnelles, sans entrer de mot de passe.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères du mot de passe de l’utilisateur (**4**-**16**).
- **Nombre maximal de minutes d’inactivité avant le verrouillage du profil professionnel** : sélectionnez la durée d’inactivité autorisée avant que le profil professionnel ne soit verrouillé. L’utilisateur doit ensuite entrer ses informations d’identification pour rétablir l’accès.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre de saisies possibles d’un mot de passe incorrect avant que le profil professionnel ne soit réinitialisé.
- **Expiration du mot de passe (en jours)** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (**1**-**255**).
- **Type de mot de passe obligatoire** : sélectionnez le type de mot de passe qui doit être défini sur l’appareil. Choisissez parmi :
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
- **Smart Lock et autres agents de confiance** : choisissez **Bloquer** pour empêcher Smart Lock ou d’autres agents de confiance d’ajuster les paramètres d’écran de verrouillage sur les appareils compatibles. Cette fonctionnalité, également connue sous le nom d’agent de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil, si ce dernier se trouve dans un emplacement approuvé. Par exemple, contournez le mot de passe du profil professionnel quand l’appareil est connecté à un appareil Bluetooth spécifique, ou quand il est à proximité d’une étiquette NFC. Utilisez ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.

### <a name="device-password"></a>Mot de passe de l’appareil

Ces paramètres de mot de passe s’appliquent aux profils personnels des appareils qui utilisent un profil professionnel.

- **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères du mot de passe de l’utilisateur (**4**-**14**).
- **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** : sélectionnez le délai autorisé avant le verrouillage automatique d’un appareil inactif
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre de saisies possibles d’un mot de passe incorrect avant que le profil professionnel ne soit réinitialisé.
- **Expiration du mot de passe (en jours)** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (**1**-**255**).
- **Type de mot de passe requis** : sélectionnez le type de mot de passe qui doit être défini sur l’appareil. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Obligatoire**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs, par exemple « 1111 » ou « 1234 » ne sont pas autorisés
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe (**1**-**24**).
- **Déverrouillage par empreinte digitale** : choisissez **Bloquer** pour empêcher l’utilisation du lecteur d’empreintes digitales de l’appareil pour le déverrouiller. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.
- **Smart Lock et autres agents de confiance** : choisissez **Bloquer** pour empêcher Smart Lock ou d’autres agents de confiance d’ajuster les paramètres d’écran de verrouillage sur les appareils compatibles. Cette fonctionnalité, également connue sous le nom d’agent de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil, si ce dernier se trouve dans un emplacement approuvé. Par exemple, contournez le mot de passe du profil professionnel quand l’appareil est connecté à un appareil Bluetooth spécifique, ou quand il est à proximité d’une étiquette NFC. Utilisez ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.

### <a name="system-security"></a>Sécurité système

- **Exiger l’analyse des menaces sur les applications** : l’option **Exiger** applique la règle indiquant que le paramètre **Vérifier les applications** est activé pour les profils professionnels et personnels.

   > [!Note]
   > Ce paramètre ne fonctionne que pour les appareils Android 8 (Oreo) et versions supérieures.

- **Empêcher les installations d’applications à partir de sources inconnues dans le profil personnel** : par défaut, les appareils de profil professionnel Android Enterprise ne peuvent pas installer d’applications à partir de sources autres que le Play Store. Par nature, les appareils de profil professionnel sont conçus pour être à double profil :

  - Un profil professionnel géré avec MDM.
  - Un profil personnel qui est isolé de la gestion MDM.

  Ce paramètre permet aux administrateurs de contrôler davantage les installations d’applications provenant de sources inconnues. **Non configuré** (par défaut) autorise les installations d’applications provenant de sources inconnues dans le profil personnel. **Bloquer** empêche les installations d’applications à partir de sources autres que le Play Store dans le profil personnel.

### <a name="connectivity"></a>Connectivité

- **VPN AlwaysOn** : choisissez **Activer** pour indiquer à un client VPN de se connecter et de se reconnecter automatiquement au réseau VPN. Les connexions VPN Always On restent activées ou s’activent immédiatement quand l’utilisateur verrouille ou redémarre son appareil, ou quand le réseau sans fil change. 

  Choisissez **Non configuré** pour désactiver en permanence la fonctionnalité VPN Always On pour tous les clients VPN.

  > [!IMPORTANT]
  > Veillez à ne déployer qu’une seule stratégie VPN Always On sur un seul appareil. Le déploiement de plusieurs stratégies VPN Always On sur un seul appareil n’est pas pris en charge.

- **Client VPN** : choisissez un client VPN qui prend en charge AlwaysOn. Les options disponibles sont les suivantes :
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

- **Mode de verrouillage** : choisissez **Activer** pour forcer l’ensemble du trafic réseau à utiliser le tunnel VPN. Si aucune connexion au VPN n’est établie, l’appareil n’a pas d’accès réseau.

  Choisissez **Non configuré** pour permettre au trafic de passer par le tunnel VPN ou le réseau mobile.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils plein écran pour des appareils [Android](device-restrictions-android.md#kiosk) et [Windows 10](kiosk-settings.md) dédiés.

## <a name="see-also"></a>Voir aussi

[Configuration et dépannage des appareils d’entreprise Android dans Microsoft Intune](https://support.microsoft.com/help/4476974)
