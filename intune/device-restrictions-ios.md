---
title: Ajouter des paramètres de restriction des appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils iOS pour définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode plein écran, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a677742c5d2f876c0714f13c4f62d059ced98584
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728971"
---
# <a name="ios-device-restrictions-settings-list-in-microsoft-intune"></a>Liste des paramètres de restriction des appareils iOS dans Microsoft Intune

Cet article répertorie et décrit tous les paramètres de restriction que vous pouvez appliquer aux appareils iOS. Ces paramètres sont ajoutés à un profil de configuration d’appareil, puis affectés ou déployés sur vos appareils iOS via Microsoft Intune.

## <a name="general"></a>Général

- **Partager des données d’utilisation** : choisissez **Bloquer** pour empêcher l’appareil d’envoyer des données de diagnostic et d’utilisation à Apple. L’option **Non configuré** autorise l’envoi de ces données.
  - **Envoi des données de diagnostic** : l’option **Bloquer** empêche l’utilisateur de modifier les paramètres d’envoi des diagnostics et d’analyse des applications du volet **Diagnostics et utilisation** (paramètres de l’appareil). Pour utiliser ce paramètre, l’appareil doit être en mode supervisé (iOS 9.3.2+). L’option **Non configuré** permet à l’utilisateur de modifier ces paramètres d’appareil.
- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. L’option **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran comme image.
  - **Observation de l’écran à distance avec l’application Classroom (mode supervisé uniquement)** : choisissez l’option **Bloquer** pour empêcher l’application Classroom d’observer à distance l’écran de l’appareil. Pour utiliser ce paramètre, l’appareil doit être en mode supervisé (iOS 9.3+). L’option **Non configuré** autorise l’application Apple Classroom à afficher l’écran.
  - **Observation des écrans sans invite par l’application En classe (mode supervisé uniquement)**  : si cette option est définie sur **Autoriser**, les enseignants peuvent observer en mode silencieux l’écran des appareils iOS des étudiants qui n’en sont pas avertis à l’aide de l’application En classe. Les appareils des étudiants inscrits dans une classe et qui utilisent l’application Classroom accordent automatiquement une autorisation à l’enseignant de cette classe. L’option **Non configuré** désactive cette fonctionnalité.
- **Certificats TLS non approuvés** : choisissez l’option **Bloquer** pour empêcher les certificats Transport Layer Security (TLS) non autorisés sur l’appareil. L’option **Non configuré** autorise les certificats TLS.
- **Approbation des applications d’entreprise** : choisissez **Bloquer** pour supprimer le bouton **Approuver Enterprise Developer** du menu Paramètres > Général > Profils et gestion des appareils sur l’appareil. L’option **Non configuré** permet à l’utilisateur de choisir de faire confiance aux applications qui n’ont pas été téléchargées à partir de l’App Store.
- **Modification de compte (mode supervisé uniquement)**  : si cette option est définie sur **Bloquer**, l’utilisateur ne peut pas mettre à jour les paramètres spécifiques à l’appareil dans l’application Réglages d’iOS. Par exemple, l’utilisateur ne peut ni créer de nouveaux comptes d’appareils ni modifier le nom d’utilisateur ou le mot de passe. L’option **Non configuré** permet aux utilisateurs de modifier ces paramètres.
  Cette fonctionnalité s’applique également aux options accessibles à partir des applications iOS comme Mail, Contacts, Calendrier, Twitter, etc. Elle ne s’applique pas aux applications avec des paramètres de compte qui ne sont pas configurables à partir des applications iOS comme Microsoft Outlook.
- **Activation des restrictions dans les paramètres de l’appareil (appareils supervisés uniquement)** : choisissez **Bloquer** pour empêcher les utilisateurs d’activer les restrictions dans les paramètres de l’appareil. L’option **Non configuré** autorise l’utilisateur à configurer des restrictions sur l’appareil (par exemple le contrôle parental).
- **Utiliser la réinitialisation de tous les paramètres et du contenu sur l’appareil (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher les utilisateurs d’utiliser l’option de réinitialisation de tout le contenu et de tous les paramètres sur l’appareil (mode supervisé uniquement). L’option **Non configuré** permet aux utilisateurs d’accéder à ces paramètres.
- **Modification du nom de l’appareil (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher toute modification du nom de l’appareil. L’option **Non configuré** autorise l’utilisateur à modifier le nom de l’appareil.
- **Modification des paramètres de notification (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher toute modification des paramètres de notification. L’option **Non configuré** autorise l’utilisateur à modifier les paramètres de notification de l’appareil.
- **Modification du papier peint (supervisée uniquement)**  : choisissez **Bloquer** pour empêcher toute modification du papier peint. L’option **Non configuré** autorise l’utilisateur à modifier le papier peint sur l’appareil.
- **Modification des paramètres d’approbation d’application d’entreprise (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres d’approbation d’application d’entreprise sur les appareils supervisés. L’option **Non configuré** autorise l’utilisateur à faire confiance aux applications qui n’ont pas été téléchargées à partir de l’App Store.
- **Modifications au profil de configuration (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le profil de configuration sur l’appareil. L’option **Non configuré** autorise l’utilisateur à installer des profils de configuration.
- **Verrou d’activation (mode supervisé uniquement)** : choisissez **Autoriser** pour activer le verrou d’activation sur les appareils iOS supervisés. Le verrouillage d'activation rend plus difficile la réactivation d'un appareil perdu ou volé.
- **Bloquer la suppression d’applications (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des applications. L’option **Non configuré** autorise les utilisateurs à supprimer des applications de l’appareil.
- **Bloque le mode USB restreint (mode supervisé uniquement)**  : choisissez **Bloquer** pour désactiver le mode USB restreint sur les appareils supervisés. Le mode USB restreint empêche les accessoires USB d'échanger des données avec un appareil verrouillé depuis plus d'une heure. L’option **Non configuré** autorise le mode USB restreint.
- **Application de la date et de l’heure automatique (mode supervisé uniquement)**  : **activez** cette option pour forcer les appareils supervisés à définir automatiquement la date et l’heure. Le fuseau horaire de l’appareil est mis à jour quand l’appareil se connecte à des réseaux cellulaires ou si les services de localisation ont été activés en mode Wi-Fi.
- **Require students to request permission to leave Classroom course (supervised only)** (Obliger les élèves à demander l’autorisation de quitter le cours Classroom - mode supervisé uniquement) : **activez** cette option pour obliger les élèves inscrits à un cours non managé et qui utilisent l’app Classroom à demander à l’enseignant l’autorisation de quitter le cours. Uniquement disponible sous iOS 11.3+. L’option **Non configuré** dispense les étudiants de demander l’autorisation.
- **Autoriser les mises à jour PKI à distance** : l’option **Autoriser** permet à vos utilisateurs de recevoir des mises à jour logicielles sans connecter leurs appareils à un ordinateur.
- **Limiter le suivi des publicités** : choisissez **Limiter** pour désactiver l’identificateur de publicités de l’appareil. **Non configuré** : cette option reste activée.
- **Bloquer la création de VPN (mode supervisé uniquement)**  : l’option **Bloquer** empêche les utilisateurs de créer des paramètres de configuration VPN. L’option **Non configuré** permet aux utilisateurs de créer des VPN sur l’appareil.

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

- **Mot de passe** : Demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil. L’option Non configuré autorise les utilisateurs à accéder à l’appareil sans entrer un mot de passe.
  - **Mots de passe simples** : choisissez **Bloquer** pour exiger des mots de passe plus complexes. L’option **Non configuré** autorise les mots de passe simples comme `0000` et `1234`.
  - **Type de mot de passe requis** : choisissez le type de mot de passe dont votre organisation a besoin. Les options disponibles sont les suivantes :
    - **Paramètre par défaut de l’appareil**
    - **Numérique**
    - **Alphanumérique**
  - **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre de caractères de symbole, par exemple `#` ou `@`, devant être inclus dans le mot de passe.
  - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit saisir (entre 4 et 14 caractères).
  - **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil (entre 1 et 11).
  - **Nombre maximal de minutes après verrouillage de l’écran avant de demander un mot de passe**<sup>1</sup> : spécifiez la durée pendant laquelle l’appareil reste inactif avant que l’utilisateur doive entrer à nouveau son mot de passe. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie. Option prise en charge sur les appareils iOS 8.0 et versions ultérieures.
  - **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil**<sup>1</sup> : entrez le nombre maximal de minutes d’inactivité autorisée sur l’appareil avant le verrouillage de l’écran. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie.
  - **Expiration du mot de passe (jours)** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
  - **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe.
  - **Déverrouillage par empreinte digitale** : choisissez **Bloquer** afin d’empêcher l’utilisation d’une empreinte digitale pour déverrouiller l’appareil. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.
- **Modification du code secret (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. Les modifications apportées aux restrictions du code secret sont ignorées sur les appareils supervisés après le blocage de cette fonctionnalité. L’option **Non configuré** permet des codes secrets être ajouté, modifié ou supprimé.
  - **Modification de l’empreinte digitale (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher la modification, l’ajout ou la suppression par l’utilisateur des empreintes digitales Touch ID. L’option **Non configuré** autorise l’utilisateur à mettre à jour les empreintes digitales Touch ID sur l’appareil.
- **Bloquer le remplissage automatique des mots de passe (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sous iOS. L’option **Bloquer** a également les conséquences suivantes :
  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option **Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mots de passe de proximité (mode supervisé uniquement)** : choisissez **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils situés à proximité. L’option **Non configuré** autorise ces demandes de mots de passe.
- **Bloquer le partage de mots de passe (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher le partage de mots de passe entre les appareils avec AirDrop. L’option **Non configuré** autorise le partage de mots de passe.

<sup>1</sup> Lorsque vous configurez les paramètres **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** et **Nombre maximal de minutes entre le verrouillage de l'écran et la demande du mot de passe**, ceux-ci sont appliqués de manière séquentielle. Par exemple, si vous affectez aux deux paramètres une valeur de **5** minutes, l’écran s’éteint automatiquement après 5 minutes, et l’appareil se verrouille après 5 minutes de plus. Toutefois, si l'utilisateur désactive manuellement l'écran, le second paramètre est immédiatement appliqué. Dans le même exemple, une fois que l’utilisateur a désactivé l’écran, l’appareil se verrouille 5 minutes plus tard.

## <a name="locked-screen-experience"></a>Expérience d’écran verrouillé

- **Accès au centre de contrôle quand l'appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’utilisateur d’accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé. L’option **Non configuré** autorise les utilisateurs à accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé.
- **Notifications lorsque l’appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’accès aux notifications quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisateur à accéder aux notifications sans déverrouiller l’appareil.
- **Notifications de Wallet quand l’appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’accès à l’application Wallet quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisateur à accéder à l’application Wallet lorsque l’appareil est verrouillé.
- **Vue Aujourd'hui lors du verrouillage de l’appareil** : choisissez **Bloquer** pour empêcher l’accès à la vue Aujourd'hui lorsque l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisateur à afficher la vue Aujourd'hui lorsque l’appareil est verrouillé.

## <a name="app-store-doc-viewing-gaming"></a>App Store, affichage de document, jeux

- **App Store** : l’option **Bloquer** empêche l’accès à l’App Store sur les appareils supervisés. L’option **Non configuré** autorise l’accès.
  - **Installation d’applications à partir de l’App Store (mode supervisé uniquement)** : choisissez **Bloquer** pour bloquer l’App Store à partir de l’écran d’accueil des appareils. Les utilisateurs finaux peuvent continuer à utiliser iTunes ou l’outil Apple Configurator pour installer des applications. L’option **Non configuré** permet d’accéder à l’App Store depuis l’écran d’accueil.
  - **Téléchargements automatiques des applications (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher le téléchargement automatique des applications achetées sur d’autres appareils. Cela n’affecte pas les mises à jour des applications existantes. L’option **Non configuré** autorise le téléchargement sur l’appareil des applications achetées sur d’autres appareils iOS.
- **Mot de passe pour accéder à l'App Store** : l’option **Exiger** oblige l’utilisateur à saisir un mot de passe pour pouvoir visiter l’App Store. L’option **Non configuré** autorise l’accès à l’App Store sans entrer de mot de passe.
- **Achats dans l’application** : choisissez **Bloquer** pour empêcher les achats sur l’App Store dans l’application. L’option **Non configuré** autorise les achats au sein d’une application en cours d’exécution.
- **Contenu iTunes explicite (musique, podcast ou actualités) (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’affichage de contenu explicite dans la musique, les podcasts ou les actualités iTunes. L’option **Non configuré** autorise l’appareil à accéder au contenu réservé aux adultes depuis le magasin.
- **Télécharger du contenu de l'iBook Store indiqué comme étant de la « Littérature érotique »**  : choisissez **Bloquer** pour empêcher les utilisateurs de télécharger du contenu de l’iBook Store indiqué comme étant de la littérature érotique. L’option **Non configuré** autorise l’utilisateur à télécharger des livres de la catégorie « Littérature érotique ».
- **Affichage de documents d’entreprise dans les applications non gérées** : choisissez **Bloquer** pour empêcher l’affichage de documents d’entreprise dans les applications non gérées. L’option **Non configuré** autorise l’affichage de documents d’entreprise depuis toute application. Par exemple, vous voulez empêcher les utilisateurs d’enregistrer des fichiers de OneDrive dans Dropbox. Attribuez la valeur **Bloquer** à ce paramètre. Une fois que l’appareil a reçu la stratégie (par exemple, après un redémarrage), il cesse d’autoriser l’enregistrement.
- **Affichage des documents autres que ceux d’entreprise dans les applications d’entreprise** : choisissez **Bloquer** pour empêcher l’affichage de documents autres que ceux de l’entreprise dans les applications d’entreprise. L’option **Non configuré** autorise tout document à être affiché dans les applications d’entreprise gérées.
- **Traiter AirDrop comme une destination non gérée** : **activez** cette option pour forcer AirDrop à être considéré comme une cible de dépôt non gérée. Cette option empêche les applications gérées d’envoyer des données à l’aide via Airdrop. 
- **Ajout d’amis Game Center (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter des amis Game Center. L’option **Non configuré** autorise l’utilisateur à ajouter des amis dans le Game Center.
- **Game Center (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de l’application Game Center. L’option **Non configuré** autorise l’utilisation de l’application Game Center sur l’appareil.
- **Jeux multijoueur (mode supervisé uniquement)**: choisissez **Bloquer** pour empêcher les jeux multijoueur. L’option **Non configuré** autorise l’utilisateur à jouer à des jeux multijoueur sur l’appareil.
- **Région des classifications** : choisissez la région des classifications que vous souhaitez utiliser pour les téléchargements autorisés. Puis choisissez les évaluations autorisées pour les catégories **Films** et **Émissions TV**.
- **Applications** : choisissez la catégorie d’âge autorisée pour les applications que les utilisateurs peuvent télécharger, ou choisissez **Autoriser toutes les applications**.

## <a name="built-in-apps"></a>Applications intégrées

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option **Non configuré** autorise l’accès à l’appareil photo de l’appareil.
  - **FaceTime** : choisissez **Bloquer** pour empêcher l’accès à l’application FaceTime. L’option **Non configuré** autorise l’accès à l’application FaceTime sur l’appareil.
- **Siri** : choisissez **Bloquer** pour empêcher l’accès à Siri. L’option **Non configuré** autorise l’utilisation de l’assistant vocal Siri sur l’appareil.
  - **Siri quand l’appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’accès à Siri quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisation de l’assistant vocal Siri sur l’appareil verrouillé.
  - **Filtre d’obscénités de Siri (mode supervisé uniquement)** : **activez** cette option pour empêcher Siri de dicter ou d’employer un langage obscène.
  - **Siri à consulter le contenu généré par les utilisateurs depuis Internet (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher Siri d’accéder aux sites web pour répondre aux questions. L’option **Non configuré** autorise Siri à accéder au contenu généré par les utilisateurs depuis Internet.
- **Apple News (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’accès à l’application Apple News sur l’appareil. L’option **Non configuré** autorise l’utilisation de l’application Apple News.
- **iBooks Store (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’accès à l’iBooks Store. L’option **Non configuré** autorise les utilisateurs à parcourir l’iBooks Store et à y acheter des livres.
- **Application Messages sur l’appareil (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs d’utiliser l’application Messages sur l’appareil. L’option **Non configuré** permet d’utiliser l’application Messages pour envoyer et lire des SMS.
- **Podcasts (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisation de l’application Podcasts. L’option **Non configuré** autorise l’utilisation de l’application Podcasts.
- **Service Music (mode supervisé uniquement)**  : choisissez **Bloquer** pour rétablir l’application Musique en mode classique et désactiver le service Apple Music. L’option **Non configuré** autorise l’utilisation du service Apple Music.
- **Service iTunes Radio (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisation de l’application iTunes Radio. L’option **Non configuré** autorise l’utilisation de l’application iTunes Radio.
- **Modifications aux paramètres de l’application Localiser mes amis (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher toute modification des paramètres de l’application Localiser mes amis. L’option **Non configuré** autorise l’utilisateur à modifier les paramètres de l’application Localiser mes amis.
- **Recherche Spotlight pour renvoyer des résultats à partir d’Internet (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher Spotlight de renvoyer des résultats à partir d’une recherche sur Internet. L’option **Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.
- **Bloquer la suppression d’applications système de l’appareil (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher la suppression d’applications système de l’appareil. L’option **Non configuré** autorise les utilisateurs à supprimer des applications système.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- **Applications interdites** : la liste des applications non gérées par Intune dont vous ne souhaitez pas qu’elles soient installées sur l’appareil. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.
- **Applications approuvées** : la liste des applications que les utilisateurs sont autorisés à installer. Pour rester conformes, ils ne doivent pas installer d’autres applications. Les applications qui sont gérées par Intune sont autorisées automatiquement. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format <app url>, <app name>, <app publisher>. Vous pouvez sinon exporter une liste existante comportant la liste des applications restreintes au même format.

> [!IMPORTANT]
> Les profils d’appareils qui utilisent les paramètres d’applications restreintes doivent être affectés à des groupes d’utilisateurs.

## <a name="show-or-hide-apps-supervised-only"></a>Afficher ou masquer des applications (mode supervisé uniquement)

Dans la liste des applications affichées ou masquées, vous pouvez configurer une des listes suivantes sur des appareils supervisés tournant sous iOS 9.3 ou versions ultérieures.

- **Applications masquées** : spécifiez une liste d’applications masquée aux utilisateurs. Les utilisateurs ne peuvent ni afficher ni ouvrir ces applications.
- **Applications visibles** : spécifiez une liste d’applications que les utilisateurs peuvent voir et lancer. Aucune autre application ne peut être affichée ou lancée.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format <app url>, <app name>, <app publisher>. Vous pouvez sinon exporter une liste existante comportant la liste des applications restreintes au même format.

## <a name="wireless"></a>Sans fil

- **Itinérance de données** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Récupération en arrière-plan globale en cas d'itinérance**  : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de récupération en arrière-plan globale lors de l’itinérance sur le réseau cellulaire. L’option **Non configuré** autorise l’appareil à récupérer des données comme les courriers électroniques lorsqu’il est en mode itinérance sur un réseau cellulaire.
- **Numérotation vocale** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil. L’option **Non configuré** autorise la numérotation vocale sur l’appareil.
- **Itinérance vocale** : choisissez **Bloquer** pour empêcher l’itinérance vocale sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Modifications des paramètres d'utilisation des données cellulaires des applications (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher toute modification des paramètres d’utilisation des données cellulaires des applications. L’option **Non configuré** permet à l’utilisateur de contrôler les applications qui sont autorisées à utiliser des données cellulaires.
- **Point d’accès personnel** : choisissez **Bloquer** pour empêcher l’appareil d’être utilisé comme point d’accès personnel. Ce paramètre n’est peut-être pas compatible avec certains opérateurs. L’option **Non configuré** autorise cette fonctionnalité.
- **Rejoindre uniquement les réseaux Wi-Fi utilisant des profils de configuration (mode supervisé uniquement)** : **activez** cette option pour forcer l’appareil à rejoindre uniquement les réseaux Wi-Fi configurés à l’aide d’un profil de configuration Intune. L’option **Non configuré** autorise l’appareil à utiliser d’autres réseaux Wi-Fi.
- **Règles d’utilisation des données mobiles (applications gérées uniquement)** : définissez les types de données que les applications gérées peuvent utiliser sur les réseaux mobiles. Les options disponibles sont les suivantes :
  - **Bloquer l’utilisation de données cellulaires** : bloquez l’utilisation de données cellulaires pour **toutes les applications managées** ou **Choisir des applications spécifiques**.
  - **Bloquer l’utilisation de données cellulaires en itinérance** : bloquez l’utilisation de données cellulaires en itinérance pour **toutes les applications managées** ou **Choisir des applications spécifiques**.

## <a name="connected-devices"></a>Appareils connectés

- **AirDrop (supervisé uniquement)**: choisissez **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option **Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Appairage avec une Apple Watch (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’appairage avec une Apple Watch. L’option **Non configuré** autorise l’appairage avec une Apple Watch.
- **Détection du poignet pour une Apple Watch appairée** : **activez** cette option pour forcer une Apple Watch appairée à utiliser la détection du poignet. Si cette option est activée, l’Apple Watch n’affiche pas de notification si elle n’est pas portée. 
- **Modification Bluetooth (mode supervisé uniquement)** : **Bloquer** empêche l’utilisateur final de modifier les paramètres Bluetooth sur l’appareil. L’option **Non configuré** permet à l’utilisateur de modifier ces paramètres.
- **Appariement d’hôtes pour contrôler les appareils avec lesquels un appareil iOS peut s’apparier (mode supervisé uniquement)** : l’option **Non configuré** autorise l’appariement d’hôtes à permettre à l’administrateur de déterminer les appareils avec lesquels un appareil iOS peut s’apparier. L’option **Bloquer** empêche l’appairage d’hôtes.
- **Exiger un mot de passe associé pour les demandes AirPlay sortantes** : **nécessite** un mot de passe de jumelage lorsque l’utilisateur a recours à AirPlay pour diffuser le contenu vers d’autres appareils Apple. L’option **Non configuré** permet à l’utilisateur de diffuser en continu du contenu à l’aide d’AirPlay, sans entrer de mot de passe.
- **Bloquer AirPrint (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité AirPrint sur l’appareil. L’option **Non configuré** autorise l’utilisation d’AirPrint.
  - **Bloquer le stockage des informations d'identification AirPrint dans le trousseau (mode supervisé uniquement)**  : choisissez **Bloquer** afin d’empêcher l’utilisation du stockage Trousseau pour le nom d’utilisateur et le mot de passe sur l’appareil. L’option **Non configuré** permet de stocker le nom d’utilisateur et le mot de passe AirPrint dans l’application Trousseau.
  - **Exiger un certificat TLS approuvé pour AirPrint (mode supervisé uniquement)**  : **activez** cette option pour forcer l’appareil à utiliser des certificats approuvés pour la communication de l'impression TLS.
  - **Bloquer la découverte par iBeacon des imprimantes AirPrint (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les balises AirPrint Bluetooth malveillants de lancer des attaques d’hameçonnage sur le réseau. L’option **Non configuré** permet de publier des imprimantes AirPrint sur l’appareil.

## <a name="keyboard-and-dictionary"></a>Clavier et dictionnaire

- **Recherche de définition de mot (supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Claviers prédictifs (mode supervisé uniquement)** : l’option **Non configuré** autorise l’utilisation de claviers prédictifs pour suggérer des mots que l’utilisateur pourrait vouloir utiliser. L’option **Bloquer** empêche cette fonctionnalité.
- **Correction automatique (mode supervisé uniquement)** : l’option **Non configuré** permet à l’appareil de corriger automatiquement les mots mal orthographiés. Choisissez **Bloquer** pour désactiver la correction automatique.
- **Vérification orthographique du clavier (mode supervisé uniquement)**  : l’option **Non configuré** active le vérificateur d’orthographe sur l’appareil. Choisissez **Bloquer** pour désactiver le vérificateur d’orthographe.
- **Raccourcis clavier (mode supervisé uniquement)**  : l’option **Non configuré** permet d’utiliser les raccourcis clavier sur l’appareil. Choisissez **Bloquer** pour empêcher l’utilisation des raccourcis clavier.
- **Dictée (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisateur de saisir du texte à l’aide de l’entrée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Sauvegarder sur iCloud** : l’option **Non configuré** autorise l’utilisateur à sauvegarder les données de l’appareil dans iCloud. Choisissez **Bloquer** pour empêcher l’utilisateur de sauvegarder les données de l’appareil dans iCloud.
- **Synchronisation de documents sur iCloud (mode supervisé uniquement)** : l’option **Non configuré** autorise la synchronisation des documents et des clés-valeurs sur votre espace de stockage iCloud. Choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et des données.
- **Synchronisation du flux de photos sur iCloud** : l’option **Non configuré** permet aux utilisateurs d’activer **Mon flux de photos** sur leur appareil afin de synchroniser les photos avec iCloud et de les mettre à la disposition de tous les appareils des utilisateurs. Choisissez **Bloquer** pour empêcher la synchronisation du flux de photos sur iCloud.
- **Sauvegarde chiffrée** : **activez** cette option pour exiger le chiffrement des sauvegardes d’appareil.
- **Photothèque iCloud** : choisissez **Bloquer** pour empêcher la photothèque iCloud de stocker des photos et vidéos dans le cloud. Toutes les photos qui ne sont pas entièrement téléchargées de la Photothèque iCloud sur l’appareil sont supprimées de l’appareil. L’option **Non configuré** autorise l’utilisation de la photothèque iCloud.
- **Applications gérées synchronisées avec le cloud** : l’option **Non configuré** autorise les applications que vous gérez avec Intune à synchroniser les données sur le compte iCloud de l’utilisateur. Choisissez **Bloquer** pour empêcher cette synchronisation des données sur iCloud.
- **Flux de photos partagé** : choisissez **Bloquer** pour désactiver le **partage de photos iCloud** sur l'appareil. L’option **Non configuré** autorise la diffusion en continu des photos partagées.
- **Continuation de l’activité** : l’option **Non configuré** autorise les utilisateurs à reprendre le travail qu’ils ont commencé sur un appareil iOS sur un autre appareil iOS ou macOS (Handoff). Choisissez **Bloquer** pour désactiver cette fonctionnalité.
- **Bloquer la synchronisation du trousseau iCloud** : choisissez **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option **Non configuré** autorise les utilisateurs à modifier ces identifiants.
- **Bloquer la sauvegarde des livres d'entreprise** : choisissez **Bloquer** pour empêcher les utilisateurs de sauvegarder des livres d’entreprise. L’option **Non configuré** autorise les utilisateurs à sauvegarder ces livres.
- **Bloquer la synchronisation des métadonnées des livres d'entreprise (notes et mises en surbrillance)**  : choisissez **Bloquer** pour empêcher la synchronisation des notes et des mises en surbrillance dans les livres d’entreprise. L’option **Non configuré** autorise la synchronisation.

## <a name="autonomous-single-app-mode-supervised-only"></a>Mode Application unique autonome (mode supervisé uniquement)

Utilisez ces paramètres pour configurer les appareils iOS pour qu’ils exécutent des applications spécifiques en mode Application unique autonome. Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé. Il peut uniquement exécuter cette application. Par exemple, ajoutez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

Pour ajouter des applications, vous pouvez :

- Entrer les valeurs **Nom de l’application** et **ID d'ensemble d'applications**, puis sélectionner **Ajouter**. La section [Référence à un ID d’ensemble pour les applications iOS intégrées](#bundle-id-reference-for-built-in-ios-apps) (dans cet article) inclut quelques apps et leur ID.
- **Importer** un fichier CSV contenant la liste des noms d’application et leur ID d’ensemble. Ou, **exporter** une liste existante incluant les applications.

## <a name="kiosk-supervised-only"></a>Plein écran (supervisé uniquement)

- **Application à exécuter en mode plein écran** : choisissez le type d’applications que vous souhaitez exécuter en mode plein écran. Les options disponibles sont les suivantes : 
  - **Application du magasin** : entrer l’URL pointant vers une application de l'App Store d'iTunes
  - **Application gérée** : choisir une application que vous avez ajoutée à Intune
  - **Application intégrée** : entrer l’[ID d’ensemble](#bundle-id-reference-for-built-in-ios-apps) de l’application intégrée

- **Assistance tactile** : cette option **nécessite** le paramètre d’accessibilité Assistance tactile sur l’appareil. Cette fonctionnalité aide les utilisateurs à effectuer des gestes à l’écran qui peuvent être difficiles à réaliser pour eux. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Inverser les couleurs** : **activez** le paramètre d’accessibilité Inverser les couleurs pour permettre aux utilisateurs ayant des troubles visuels d’ajuster l’affichage. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Audio mono** : cette option **nécessite** le paramètre d’accessibilité Audio mono sur l’appareil. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **VoiceOver** : cette option **nécessite** le paramètre d’accessibilité VoiceOver sur l’appareil pour lire à voix haute le texte à l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Zoom** : cette option **nécessite** le paramètre d’accessibilité Zoom sur l’appareil pour effectuer un zoom avant à l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Verrouillage automatique** : **autoriser** le verrouillage automatique de l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Modification de sonnerie** : **autoriser** la modification de sonnerie (désactivation du son) sur l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Rotation d’écran** : **autoriser** la modification de l’orientation de l’écran lorsque l’utilisateur fait pivoter l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Bouton de mise en veille de l’écran** : choisissez **Autoriser** pour désactiver le bouton Veille/sortie de veille de l’écran sur l’appareil. L’option **Non configuré** active cette fonctionnalité.
- **Tactile** : choisissez **Bloquer** pour désactiver l'écran tactile sur l'appareil. L’option **Non configuré** permet l’utilisation de l’écran tactile.
- **Boutons de volume** : **autoriser** l’utilisation des boutons de volume sur l’appareil. L’option **Non configuré** désactive les boutons de volume.
- **Commande d’assistance tactile** : **autoriser** l’utilisation de la fonction d’assistance tactile. L’option **Non configuré** désactive cette fonctionnalité.
- **Réglages de couleurs inversées** : **autoriser** les réglages de couleurs inversées pour permettre aux utilisateurs d’ajuster la fonction de couleurs inversées. L’option **Non configuré** désactive cette fonctionnalité.
- **Lire le texte sélectionné** : **autoriser** les paramètres d’accessibilité Sélection Speak sur l’appareil. Cette fonctionnalité lit à voix haute le texte que l’utilisateur sélectionne. L’option **Non configuré** désactive cette fonctionnalité.
- **Contrôle de VoiceOver** : **autoriser** les modifications VoiceOver pour permettre aux utilisateurs de mettre à jour la fonction VoiceOver, notamment la vitesse de lecture à voix haute du texte à l’écran. L’option **Non configuré** empêche toute modification de VoiceOver.
- **Réglage du zoom** : **autoriser** l’utilisateur à régler le zoom. L’option **Non configuré** empêche toute modification du zoom.

> [!NOTE]
> Avant de pouvoir configurer un appareil iOS pour le mode plein écran, vous devez utiliser l’outil Apple Configurator ou le Programme d’inscription des appareils Apple pour mettre l’appareil en mode supervisé. Consultez le guide Apple sur l’utilisation de l’outil Apple Configurator.
> Si l’application iOS que vous spécifiez est installée après l’attribution du profil, l’appareil ne bascule en mode plein écran qu’après son redémarrage.

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
| com.apple.Maps              | Mappages         | Apple     |
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

- **Safari (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisation du navigateur Safari sur l’appareil. L’option **Non configuré** autorise l’utilisation du navigateur Safari.
- **Remplissage automatique** : l’option **Bloquer** désactive la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.
- **Cookies** : choisissez la façon dont les cookies sont gérés sur l’appareil. Les options disponibles sont les suivantes :
  - Autoriser
  - Bloquer tous les cookies
  - Autoriser les cookies des sites web visités
  - Autoriser les cookies du site web actuel
- **JavaScript** : choisissez **Bloquer** pour empêcher que les scripts Java dans le navigateur s’exécutent sur l’appareil. L’option **Non configuré** autorise les scripts Java.
- **Avertissements en cas de fraude** : **activez** cette option pour forcer l’affichage des avertissements en cas de fraude dans le navigateur web de l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Fenêtres publicitaires** : choisissez **Bloquer** pour désactiver le bloqueur de fenêtres publicitaires dans le navigateur web. L’option **Non configuré** autorise le bloqueur de fenêtres publicitaires.

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domaines d’e-mail non marqués

Dans **URL de domaine d’e-mail**, ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs finaux reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez saisis, l’e-mail est marqué comme non approuvé dans l’application iOS Mail.

### <a name="managed-web-domains"></a>Domaines web gérés

Dans **URL de domaine web**, ajoutez une ou plusieurs URL à la liste. Les documents téléchargés à partir des domaines que vous saisissez sont considérés comme gérés. Ce paramètre s’applique uniquement aux documents téléchargés à l’aide du navigateur Safari.

### <a name="safari-password-autofill-domains"></a>Domaines de remplissage automatique des mots de passe Safari

Dans **URL de domaine**, ajoutez une ou plusieurs URL à la liste. Les utilisateurs peuvent uniquement enregistrer les mots de passe web à partir des URL de cette liste. Ce paramètre s’applique uniquement au navigateur Safari et aux appareils iOS 9.3 et versions ultérieures en mode supervisé. Si vous ne spécifiez aucune URL, les mots de passe peuvent être enregistrés à partir de tous les sites web.

## <a name="next-steps"></a>Étapes suivantes

[Affectez le profil](device-profile-assign.md) et [effectuez le monitoring de son état](device-profile-monitor.md).
