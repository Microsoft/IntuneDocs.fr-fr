---
title: Paramètres d’appareil iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils iOS pour restreindre les fonctionnalités, y compris définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode kiosque, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune; seodec18
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 80eb088063522ba3acb293776064fd98846b9a3e
ms.sourcegitcommit: 8e3a20b2ad59d3a6789ee81b9cbe6d2c711da11d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54380501"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils iOS. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, définir des règles de mot de passe, autoriser ou restreindre des applications spécifiques, et bien d’autres opérations.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils iOS.

## <a name="before-you-begin"></a>Avant de commencer
[Créez un profil de configuration d’appareil](device-restrictions-configure.md).

## <a name="general"></a>Général

- **Partager les données d’utilisation** : choisissez **Bloquer** pour empêcher l’appareil d’envoyer des données de diagnostic et d’utilisation à Apple. L’option **Non configuré** autorise l’envoi de ces données.
  - **Envoi des données de diagnostic** : l’option **Bloquer** empêche l’utilisateur de modifier les paramètres d’envoi des diagnostics et d’analytique des applications du volet **Diagnostics et utilisation** (paramètres de l’appareil). Pour utiliser ce paramètre, l’appareil doit être en mode supervisé (iOS 9.3.2+). L’option **Non configuré** permet à l’utilisateur de modifier ces paramètres d’appareil.
- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. L’option **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran comme image.
  - **Observation des écrans à distance par l’application Classroom (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’application Classroom d’observer à distance l’écran de l’appareil. Pour utiliser ce paramètre, l’appareil doit être en mode supervisé (iOS 9.3+). L’option **Non configuré** autorise l’application Apple Classroom à afficher l’écran.
  - **Observation des écrans sans invite par l’application Classroom (mode supervisé uniquement)**  : si cette option est définie sur **Autoriser**, les enseignants peuvent observer l’écran des appareils iOS des étudiants qui utilisent l’application Classroom, sans que les étudiants en soient avertis. Les appareils des étudiants inscrits dans une classe et qui utilisent l’application Classroom accordent automatiquement une autorisation à l’enseignant de cette classe. L’option **Non configuré** désactive cette fonctionnalité.
- **Certificats TLS non approuvés** : choisissez l’option **Bloquer** pour empêcher l’utilisation de certificats TLS (Transport Layer Security) non autorisés sur l’appareil. L’option **Non configuré** autorise les certificats TLS.
- **Approbation d’applications d’entreprise** : choisissez l’option **Bloquer** pour supprimer le bouton **Approuver Enterprise Developer** du menu Paramètres > Général > Profils et gestion des appareils sur l’appareil. L’option **Non configuré** permet à l’utilisateur de choisir de faire confiance aux applications qui n’ont pas été téléchargées à partir de l’App Store.
- **Modification de compte (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisateur de mettre à jour les paramètres de l’appareil dans l’application Réglages d’iOS. Par exemple, l’utilisateur ne peut ni créer de nouveaux comptes d’appareils ni modifier le nom d’utilisateur ou le mot de passe. L’option **Non configuré** permet aux utilisateurs de modifier ces paramètres.
  Cette fonctionnalité s’applique également aux options accessibles à partir des applications iOS comme Mail, Contacts, Calendrier, Twitter, etc. Elle ne s’applique pas aux applications avec des paramètres de compte qui ne sont pas configurables à partir des applications iOS comme Microsoft Outlook.
- **Activation des restrictions dans les paramètres de l’appareil (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les utilisateurs d’activer des restrictions dans les paramètres de l’appareil. L’option **Non configuré** autorise l’utilisateur à configurer des restrictions sur l’appareil (par exemple le contrôle parental).
- **Utiliser l’option d’effacement de tout le contenu et de tous les paramètres sur l’appareil (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de sélectionner l’option permettant d’effacer tout le contenu et tous les paramètres sur l’appareil (disponible en mode supervisé uniquement). L’option **Non configuré** permet aux utilisateurs d’accéder à ces paramètres.
- **Modification du nom de l’appareil (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisateur de changer le nom de l’appareil. L’option **Non configuré** autorise l’utilisateur à modifier le nom de l’appareil.
- **Modification des paramètres de notification (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisateur de modifier les paramètres de notification. L’option **Non configuré** autorise l’utilisateur à modifier les paramètres de notification de l’appareil.
- **Modification du papier peint (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le papier peint. L’option **Non configuré** autorise l’utilisateur à modifier le papier peint sur l’appareil.
- **Modification des paramètres d’approbation des applications d’entreprise (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres d’approbation des applications d’entreprise sur les appareils supervisés. L’option **Non configuré** autorise l’utilisateur à faire confiance aux applications qui n’ont pas été téléchargées à partir de l’App Store.
- **Changements apportés au profil de configuration (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le profil de configuration de l’appareil. L’option **Non configuré** autorise l’utilisateur à installer des profils de configuration.
- **Verrou d’activation (mode supervisé uniquement)**  : choisissez **Autoriser** pour activer le verrou d’activation sur les appareils iOS supervisés. Le verrouillage d'activation rend plus difficile la réactivation d'un appareil perdu ou volé.
- **Bloquer la suppression d’applications (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des applications. L’option **Non configuré** autorise les utilisateurs à supprimer des applications de l’appareil.
- **Bloquer le mode USB restreint (mode supervisé uniquement)**  : choisissez **Bloquer** pour désactiver le mode USB restreint sur les appareils supervisés. Le mode USB restreint empêche les accessoires USB d'échanger des données avec un appareil verrouillé depuis plus d'une heure. L’option **Non configuré** autorise le mode USB restreint.
- **Forcer une date et une heure automatiques (mode supervisé uniquement)**  : choisissez l’option **Exiger** pour forcer les appareils supervisés à définir automatiquement la date et l’heure. Le fuseau horaire de l’appareil est mis à jour quand l’appareil se connecte à des réseaux cellulaires ou si les services de localisation ont été activés en mode Wi-Fi.
- **Obliger les élèves à demander une autorisation pour quitter un cours En classe (mode supervisé uniquement)**  : choisissez l’option **Exiger** pour obliger les étudiants inscrits à un cours non géré dans l’application Classroom à demander à l’enseignant l’autorisation de quitter le cours. Uniquement disponible sous iOS 11.3+. L’option **Non configuré** dispense les étudiants de demander l’autorisation.
- **Autoriser les mises à jour PKI à distance** : choisissez l’option **Autoriser** pour permettre aux utilisateurs de recevoir les mises à jour logicielles sans avoir à connecter leurs appareils à un ordinateur.
- **Limiter le suivi des publicités** : choisissez **Limiter** pour désactiver l’identificateur de publicité d’appareil. **Non configuré** : cette option reste activée.
- **Bloquer la création de VPN (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les utilisateurs de créer des paramètres de configuration VPN. L’option **Non configuré** permet aux utilisateurs de créer des VPN sur l’appareil.

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
- raccourcis clavier 
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

- **Mot de passe** : Demande à l’utilisateur final de saisir un mot de passe pour pouvoir accéder à l’appareil. L’option Non configuré autorise les utilisateurs à accéder à l’appareil sans entrer un mot de passe.
  - **Mots de passe simples** : choisissez l’option **Bloquer** pour exiger des mots de passe plus complexes. L’option **Non configuré** autorise les mots de passe simples comme `0000` et `1234`.
  - **Type de mot de passe requis** : choisissez le type de mot de passe exigé par votre organisation. Les options disponibles sont les suivantes :
    - **Paramètre par défaut de l’appareil**
    - **Numérique**
    - **Alphanumérique**
  - **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre de caractères de symbole, par exemple `#` ou `@`, devant être inclus dans le mot de passe.
  - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit entrer (entre 4 et 14 caractères).
  - **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : spécifie le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil (entre 1 et 11).
  - **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe**<sup>1</sup> : entrez la durée d’inactivité de l’appareil au bout de laquelle l’utilisateur doit entrer à nouveau le mot de passe. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie. Option prise en charge sur les appareils iOS 8.0 et versions ultérieures.
  - **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil**<sup>1</sup> : entrez le nombre maximal de minutes d’inactivité autorisées sur l’appareil avant le verrouillage de l’écran. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie.
  - **Expiration du mot de passe (en jours)** : entrez le nombre de jours après lesquels l’utilisateur doit changer le mot de passe de l’appareil.
  - **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe.
  - **Déverrouillage par empreinte digitale** : choisissez l’option **Bloquer** pour empêcher l’utilisateur de déverrouiller l’appareil avec une empreinte digitale. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.
- **Modification du code secret (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. Les modifications apportées aux restrictions du code secret sont ignorées sur les appareils supervisés après le blocage de cette fonctionnalité. L’option **Non configuré** permet des codes secrets être ajouté, modifié ou supprimé.
  - **Modification de l’empreinte digitale (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher la modification, l’ajout ou la suppression par l’utilisateur des empreintes digitales Touch ID. L’option **Non configuré** autorise l’utilisateur à mettre à jour les empreintes digitales Touch ID sur l’appareil.
- **Bloquer le remplissage automatique des mots de passe (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sur iOS. L’option **Bloquer** a également les conséquences suivantes :
  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option **Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mot de passe à proximité (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils à proximité. L’option **Non configuré** autorise ces demandes de mots de passe.
- **Bloquer le partage de mot de passe (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher le partage des mots de passe entre les appareils avec AirDrop. L’option **Non configuré** autorise le partage de mots de passe.

<sup>1</sup> Lorsque vous configurez les paramètres **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** et **Nombre maximal de minutes entre le verrouillage de l'écran et la demande du mot de passe**, ceux-ci sont appliqués de manière séquentielle. Par exemple, si vous affectez aux deux paramètres une valeur de **5** minutes, l’écran s’éteint automatiquement après 5 minutes, et l’appareil se verrouille après 5 minutes de plus. Toutefois, si l'utilisateur désactive manuellement l'écran, le second paramètre est immédiatement appliqué. Dans le même exemple, une fois que l’utilisateur a désactivé l’écran, l’appareil se verrouille 5 minutes plus tard.

## <a name="locked-screen-experience"></a>Expérience d’écran verrouillé

- **Accès au centre de contrôle quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’utilisateur d’accéder à l’application du centre de contrôle quand l’appareil est verrouillé. L’option **Non configuré** autorise les utilisateurs à accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé.
- **Notifications quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès aux notifications quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisateur à accéder aux notifications sans déverrouiller l’appareil.
- **Notifications de Wallet quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès à l’application Wallet quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisateur à accéder à l’application Wallet lorsque l’appareil est verrouillé.
- **Mode Aujourd’hui quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès au mode Aujourd’hui quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisateur à afficher la vue Aujourd'hui lorsque l’appareil est verrouillé.

## <a name="app-store-doc-viewing-gaming"></a>App Store, affichage de document, jeux

- **App Store** : choisissez l’option **Bloquer** pour empêcher l’accès à l’App Store sur les appareils supervisés. L’option **Non configuré** autorise l’accès.
  - **Installation d’applications à partir de l’App Store (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’accès à l’App Store à partir de l’écran d’accueil de l’appareil. Les utilisateurs finaux peuvent continuer à utiliser iTunes ou l’outil Apple Configurator pour installer des applications. L’option **Non configuré** permet d’accéder à l’App Store depuis l’écran d’accueil.
  - **Téléchargements automatiques des applications (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher le téléchargement automatique des applications achetées sur d’autres appareils. Cela n’affecte pas les mises à jour des applications existantes. L’option **Non configuré** autorise le téléchargement sur l’appareil des applications achetées sur d’autres appareils iOS.
- **Mot de passe pour accéder à l’App Store** : choisissez l’option **Exiger** pour obliger l’utilisateur à entrer un mot de passe pour pouvoir accéder à l’App Store. L’option **Non configuré** autorise l’accès à l’App Store sans entrer de mot de passe.
- **Achats dans l’application** : choisissez l’option **Bloquer** pour empêcher les achats dans l’application sur l’App Store. L’option **Non configuré** autorise les achats au sein d’une application en cours d’exécution.
- **Contenu iTunes explicite (musique, podcast ou actualités) (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour bloquer la musique, les podcasts ou les actualités iTunes à contenu explicite. L’option **Non configuré** autorise l’appareil à accéder au contenu réservé aux adultes depuis le magasin.
- **Télécharger du contenu de l’iBooks Store indiqué comme étant de la « Littérature érotique » (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les utilisateurs de télécharger du contenu de l’iBooks Store indiqué comme étant de la littérature érotique. L’option **Non configuré** autorise l’utilisateur à télécharger des livres de la catégorie « Littérature érotique ».
- **Affichage des documents d’entreprise dans les applications non gérées** : choisissez l’option **Bloquer** pour empêcher l’affichage de documents externes à l’entreprise dans les applications non gérées. L’option **Non configuré** autorise l’affichage de documents d’entreprise depuis toute application. Par exemple, vous voulez empêcher les utilisateurs d’enregistrer des fichiers de OneDrive dans Dropbox. Attribuez la valeur **Bloquer** à ce paramètre. Une fois que l’appareil a reçu la stratégie (par exemple, après un redémarrage), il cesse d’autoriser l’enregistrement.
  - **Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés** : choisissez l’option **Autoriser** pour permettre aux utilisateurs d’ajouter ou de synchroniser les informations de tous les contacts Outlook, y compris des contacts professionnels et d’entreprise, dans l’application Contacts intégrée sur l’appareil. Avec l’option **Non configuré**, les utilisateurs ne sont pas autorisés à ajouter des contacts Outlook dans l’application Contacts intégrée sur l’appareil.
  
    Pour utiliser ce paramètre, définissez le paramètre **Affichage des documents d’entreprise dans les applications non gérées**  sur **Bloquer**.
  
- **Affichage de documents externes à l’entreprise dans les applications d’entreprise** : choisissez l’option **Bloquer** pour empêcher l’affichage de documents externes à l’entreprise dans les applications d’entreprise. L’option **Non configuré** autorise tout document à être affiché dans les applications d’entreprise gérées.
  - **Autoriser les applications non gérées à lire à partir de comptes de contacts gérés** : choisissez l’option **Autoriser** pour permettre aux utilisateurs d’ajouter des informations de contact de l’application iContacts dans Outlook. L’option **Non configuré** empêche la lecture, y compris la suppression des doublons, dans l’application Contacts intégrée sur l’appareil.
  
    Pour utiliser ce paramètre, définissez le paramètre **Affichage de documents externes à l’entreprise dans les applications d’entreprise**  sur **Bloquer**.
  
- **Traiter AirDrop comme une destination non gérée** : choisissez l’option **Exiger** pour qu’AirDrop soit toujours considéré comme une cible de déplacement non gérée. Cette option empêche les applications gérées d’envoyer des données à l’aide via Airdrop. 
- **Ajout d’amis Game Center (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter des amis Game Center. L’option **Non configuré** autorise l’utilisateur à ajouter des amis dans le Game Center.
- **Game Center (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisation de l’application Game Center. L’option **Non configuré** autorise l’utilisation de l’application Game Center sur l’appareil.
- **Jeux multijoueurs (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les jeux multijoueurs. L’option **Non configuré** autorise l’utilisateur à jouer à des jeux multijoueur sur l’appareil.
- **Région des classifications** : choisissez la région des classifications que vous souhaitez utiliser pour les téléchargements autorisés. Puis choisissez les évaluations autorisées pour les catégories **Films** et **Émissions TV**.
- **Applications** : choisissez la classification par âge autorisée pour les applications que les utilisateurs peuvent télécharger, ou choisissez l’option **Autoriser toutes les applications**.

## <a name="built-in-apps"></a>Applications intégrées

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option **Non configuré** autorise l’accès à l’appareil photo de l’appareil.
  - **FaceTime** : choisissez l’option **Bloquer** pour empêcher l’accès à l’application FaceTime. L’option **Non configuré** autorise l’accès à l’application FaceTime sur l’appareil.
- **Siri** : choisissez l’option **Bloquer** pour empêcher l’accès à Siri. L’option **Non configuré** autorise l’utilisation de l’assistant vocal Siri sur l’appareil.
  - **Siri quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès à Siri quand l’appareil est verrouillé. L’option **Non configuré** autorise l’utilisation de l’assistant vocal Siri sur l’appareil verrouillé.
  - **Filtre d’obscénités de Siri (mode supervisé uniquement)**  : choisissez l’option **Exiger** pour empêcher Siri de dicter ou d’employer un langage obscène.
  - **Siri peut interroger le contenu généré par l’utilisateur à partir d’Internet (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher Siri d’accéder à des sites web pour répondre aux questions. L’option **Non configuré** autorise Siri à accéder au contenu généré par les utilisateurs depuis Internet.
- **Apple News (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’accès à l’application Apple News sur l’appareil. L’option **Non configuré** autorise l’utilisation de l’application Apple News.
- **iBooks Store (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’accès à l’iBooks Store. L’option **Non configuré** autorise les utilisateurs à parcourir l’iBooks Store et à y acheter des livres.
- **Application Messages sur l’appareil (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les utilisateurs d’utiliser l’application Messages sur l’appareil. L’option **Non configuré** permet d’utiliser l’application Messages pour envoyer et lire des SMS.
- **Podcasts (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisation de l’application Podcasts. L’option **Non configuré** autorise l’utilisation de l’application Podcasts.
- **Service Music (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour rétablir l’application Music en mode classique et désactiver le service Music. L’option **Non configuré** autorise l’utilisation du service Apple Music.
- **Service iTunes Radio (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisation de l’application iTunes Radio. L’option **Non configuré** autorise l’utilisation de l’application iTunes Radio.
- **Modifier les paramètres de l’application Localiser mes amis (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les modifications des paramètres de l’application Localiser mes amis. L’option **Non configuré** autorise l’utilisateur à modifier les paramètres de l’application Localiser mes amis.
- **La recherche Spotlight peut retourner des résultats d’Internet (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher Spotlight de retourner les résultats d’une recherche sur Internet. L’option **Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.
- **Bloquer la suppression d’applications système de l’appareil (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher la suppression des applications système sur l’appareil. L’option **Non configuré** autorise les utilisateurs à supprimer des applications système.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- **Applications interdites** : liste des applications non managées par Intune dont vous souhaitez empêcher l’installation sur l’appareil. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.
- **Applications approuvées** : liste des applications que les utilisateurs sont autorisés à installer. Pour rester conformes, ils ne doivent pas installer d’autres applications. Les applications qui sont gérées par Intune sont autorisées automatiquement. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Vous pouvez sinon exporter une liste existante comportant la liste des applications restreintes au même format.

> [!IMPORTANT]
> Les profils d’appareils qui utilisent les paramètres d’applications restreintes doivent être affectés à des groupes d’utilisateurs.

## <a name="show-or-hide-apps-supervised-only"></a>Afficher ou masquer des applications (mode supervisé uniquement)

Dans la liste des applications affichées ou masquées, vous pouvez configurer une des listes suivantes sur des appareils supervisés tournant sous iOS 9.3 ou versions ultérieures.

- **Applications masquées** : listez les applications que vous souhaitez masquer aux utilisateurs. Les utilisateurs ne peuvent ni afficher ni ouvrir ces applications.
- **Applications visibles** : listez les applications que les utilisateurs sont autorisés à afficher et lancer. Aucune autre application ne peut être affichée ou lancée.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Vous pouvez sinon exporter une liste existante comportant la liste des applications restreintes au même format.

## <a name="wireless"></a>Sans fil

- **Itinérance de données** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Récupération en arrière-plan globale en cas d’itinérance** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de récupération en arrière-plan globale lors de l’itinérance sur le réseau mobile. L’option **Non configuré** autorise l’appareil à récupérer des données comme les courriers électroniques lorsqu’il est en mode itinérance sur un réseau cellulaire.
- **Numérotation vocale** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil. L’option **Non configuré** autorise la numérotation vocale sur l’appareil.
- **Itinérance vocale** : choisissez l’option **Bloquer** pour empêcher l’itinérance vocale sur le réseau mobile. L’option **Non configuré** autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Modifications des paramètres d’utilisation des données mobiles des applications (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les modifications des paramètres d’utilisation des données mobiles des applications. L’option **Non configuré** permet à l’utilisateur de contrôler les applications qui sont autorisées à utiliser des données cellulaires.
- **Point d’accès personnel** : choisissez l’option **Bloquer** pour empêcher l’appareil d’être utilisé comme point d’accès personnel. Ce paramètre n’est peut-être pas compatible avec certains opérateurs. L’option **Non configuré** autorise cette fonctionnalité.
- **Rejoindre uniquement les réseaux Wi-Fi utilisant des profils de configuration (mode supervisé uniquement)**  : choisissez l’option **Exiger** pour forcer l’appareil à utiliser uniquement les réseaux WiFi définis par les profils de configuration Intune. L’option **Non configuré** autorise l’appareil à utiliser d’autres réseaux Wi-Fi.
- **Règles d’utilisation des données mobiles (applications gérées uniquement)**  : définissez les types de données que les applications managées peuvent utiliser sur les réseaux mobiles. Les options disponibles sont les suivantes :
  - **Bloquer l’utilisation des données mobiles** : bloquez l’utilisation des données mobiles dans **toutes les applications managées** ou uniquement dans les applications sélectionnées (avec **Choisir des applications spécifiques**).
  - **Bloquer l’utilisation des données mobiles en cas d’itinérance** : bloquez l’utilisation des données mobiles lors de l’itinérance dans **toutes les applications managées** ou uniquement dans les applications sélectionnées (avec **Choisir des applications spécifiques**).

## <a name="connected-devices"></a>Appareils connectés

- **AirDrop (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option **Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Appairage avec une Apple Watch (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’appairage avec une Apple Watch. L’option **Non configuré** autorise l’appairage avec une Apple Watch.
- **Détection du poignet pour une Apple Watch appairée** : choisissez l’option **Exiger** pour forcer l’Apple Watch appairée à utiliser la fonctionnalité de détection du poignet. Si cette option est activée, l’Apple Watch n’affiche pas de notification si elle n’est pas portée. 
- **Modification de Bluetooth (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisateur de modifier les paramètres Bluetooth sur l’appareil. L’option **Non configuré** permet à l’utilisateur de modifier ces paramètres.
- **Appairage d’hôte pour contrôler les appareils avec lesquels un appareil iOS peut s’appairer (mode supervisé uniquement)**  : l’option **Non configuré** autorise l’appairage d’hôte pour laisser l’administrateur contrôler les appareils avec lesquels un appareil iOS peut être appairé. L’option **Bloquer** empêche l’appairage d’hôtes.
- **Exiger un mot de passe associé pour les demandes AirPlay sortantes** : choisissez l’option **Exiger** pour obliger l’utilisateur à entrer un mot de passe d’appairage quand il se sert d’AirPlay pour le streaming de contenu sur d’autres appareils Apple. L’option **Non configuré** permet à l’utilisateur de diffuser en continu du contenu à l’aide d’AirPlay, sans entrer de mot de passe.
- **Bloquer AirPrint (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité AirPrint sur l’appareil. L’option **Non configuré** autorise l’utilisation d’AirPrint.
  - **Bloquer le stockage des informations d’identification AirPrint dans le trousseau (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher le stockage du nom d’utilisateur et du mot de passe dans le trousseau sur l’appareil. L’option **Non configuré** permet de stocker le nom d’utilisateur et le mot de passe AirPrint dans l’application Trousseau.
  - **Exiger un certificat TLS approuvé pour AirPrint (mode supervisé uniquement)**  : choisissez l’option **Exiger** pour forcer l’appareil à utiliser des certificats approuvés pour la communication de l’impression TLS.
  - **Bloquer la découverte par iBeacon des imprimantes AirPrint (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher le hameçonnage du trafic réseau par des balises AirPrint Bluetooth malveillantes. L’option **Non configuré** permet de publier des imprimantes AirPrint sur l’appareil.

## <a name="keyboard-and-dictionary"></a>Clavier et dictionnaire

- **Recherche de définition de mot (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Claviers prédictifs (mode supervisé uniquement)**  : l’option **Non configuré** autorise l’utilisation de claviers prédictifs pour suggérer des mots que l’utilisateur pourrait vouloir utiliser. L’option **Bloquer** empêche cette fonctionnalité.
- **Correction automatique (mode supervisé uniquement)**  : l’option **Non configuré** autorise l’appareil à corriger automatiquement les mots mal orthographiés. Choisissez **Bloquer** pour désactiver la correction automatique.
- **Vérification orthographique du clavier (mode supervisé uniquement)**  : l’option **Non configuré** autorise l’utilisation du vérificateur d’orthographe sur l’appareil. Choisissez **Bloquer** pour désactiver le vérificateur d’orthographe.
- **Raccourcis clavier (mode supervisé uniquement)**  : l’option **Non configuré** autorise l’utilisation des raccourcis clavier sur l’appareil. Choisissez **Bloquer** pour empêcher l’utilisation des raccourcis clavier.
- **Dictée (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisateur d’entrer du texte par dictée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Sauvegarder sur iCloud** : l’option **Non configuré** autorise l’utilisateur à sauvegarder les données de l’appareil sur iCloud. Choisissez **Bloquer** pour empêcher l’utilisateur de sauvegarder les données de l’appareil dans iCloud.
- **Synchronisation de documents sur iCloud (mode supervisé uniquement)**  : l’option **Non configuré** autorise la synchronisation des documents et des paires clé-valeur dans votre espace de stockage iCloud. Choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et des données.
- **Synchronisation du flux de photos sur iCloud** : l’option **Non configuré** autorise les utilisateurs à activer **Mon flux de photos** sur leur appareil afin de synchroniser les photos sur iCloud et de les publier sur tous les appareils des utilisateurs. Choisissez **Bloquer** pour empêcher la synchronisation du flux de photos sur iCloud.
- **Sauvegarde chiffrée** : choisissez l’option **Exiger** pour rendre obligatoire le chiffrement des sauvegardes sur l’appareil.
- **Photothèque iCloud** : choisissez l’option **Bloquer** pour empêcher le stockage de photos et vidéos dans le cloud à partir de la photothèque iCloud. Toutes les photos qui ne sont pas entièrement téléchargées de la Photothèque iCloud sur l’appareil sont supprimées de l’appareil. L’option **Non configuré** autorise l’utilisation de la photothèque iCloud.
- **Applications gérées synchronisées avec le cloud** : choisissez l’option **Non configuré** pour autoriser les applications managées par Intune à synchroniser les données dans le compte iCloud de l’utilisateur. Choisissez **Bloquer** pour empêcher cette synchronisation des données sur iCloud.
- **Flux de photos partagé** : choisissez l’option **Bloquer** pour désactiver le **partage de photos iCloud** sur l’appareil. L’option **Non configuré** autorise la diffusion en continu des photos partagées.
- **Continuation de l’activité** : l’option **Non configuré** autorise les utilisateurs à poursuivre le travail qu’ils ont commencé sur un appareil iOS sur un autre appareil iOS ou macOS (Handoff). Choisissez **Bloquer** pour désactiver cette fonctionnalité.
- **Bloquer la synchronisation du trousseau iCloud** : choisissez l’option **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option **Non configuré** autorise les utilisateurs à modifier ces identifiants.
- **Bloquer la sauvegarde des livres d’entreprise** : choisissez l’option **Bloquer** pour empêcher les utilisateurs de sauvegarder des livres d’entreprise. L’option **Non configuré** autorise les utilisateurs à sauvegarder ces livres.
- **Bloquer la synchronisation des métadonnées des livres d’entreprise (notes et mises en surbrillance)**  : l’option **Bloquer** empêche la synchronisation des notes et mises en surbrillance dans les livres d’entreprise. L’option **Non configuré** autorise la synchronisation.

## <a name="autonomous-single-app-mode-supervised-only"></a>Mode Application unique autonome (mode supervisé uniquement)

Utilisez ces paramètres pour configurer les appareils iOS pour qu’ils exécutent des applications spécifiques en mode Application unique autonome. Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé. Il peut uniquement exécuter cette application. Par exemple, ajoutez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

Pour ajouter des applications, vous pouvez :

- Entrer les valeurs **Nom de l’application** et **ID d'ensemble d'applications**, puis sélectionner **Ajouter**. La section [Référence à un ID d’ensemble pour les applications iOS intégrées](#bundle-id-reference-for-built-in-ios-apps) (dans cet article) inclut quelques apps et leur ID.
- **Importer** un fichier CSV contenant la liste des noms d’application et leur ID d’ensemble. Ou, **exporter** une liste existante incluant les applications.

## <a name="kiosk-supervised-only"></a>Plein écran (supervisé uniquement)

- **Application à exécuter en mode kiosque** : choisissez le type d’applications que vous souhaitez exécuter en mode kiosque. Les options disponibles sont les suivantes : 
  - **Store App** : entrez l’URL vers une application de l’App Store iTunes
  - **Application gérée** : choisissez une application que vous avez ajoutée à Intune
  - **Application intégrée** : entrez l’[ID de bundle](#bundle-id-reference-for-built-in-ios-apps) de l’application intégrée

- **Assistance tactile** : choisissez l’option **Exiger** pour forcer l’activation du paramètre d’accessibilité Assistance tactile sur l’appareil. Cette fonctionnalité aide les utilisateurs à effectuer des gestes à l’écran qui peuvent être difficiles à réaliser pour eux. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Inverser les couleurs** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité qui permet aux utilisateurs ayant des troubles visuels de régler l’affichage. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Audio mono** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité sur l’appareil. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **VoiceOver** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité sur l’appareil afin de permettre la lecture à voix haute du texte à l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Zoom** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité sur l’appareil et permettre ainsi aux utilisateurs d’agrandir l’affichage en touchant l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Verrouillage automatique** : choisissez l’option **Autoriser** pour permettre le verrouillage automatique de l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Modification de sonnerie** : choisissez l’option **Autoriser** pour permettre le changement de la sonnerie (désactivation du son) sur l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Rotation de l’écran** : choisissez l’option **Autoriser** pour permettre le changement de l’orientation de l’écran quand l’utilisateur fait pivoter l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Bouton de veille de l’écran** : choisissez l’option **Autoriser** pour désactiver le bouton de veille/sortie de veille de l’écran sur l’appareil. L’option **Non configuré** active cette fonctionnalité.
- **Tactile** : choisissez l’option **Bloquer** pour désactiver l’écran tactile sur l’appareil. L’option **Non configuré** permet l’utilisation de l’écran tactile.
- **Boutons de volume** : choisissez l’option **Autoriser** pour permettre l’utilisation des boutons de volume sur l’appareil. L’option **Non configuré** désactive les boutons de volume.
- **Commande d’assistance tactile** : choisissez l’option **Autoriser** pour permettre l’utilisation de la fonction d’assistance tactile. L’option **Non configuré** désactive cette fonctionnalité.
- **Inverser le contrôle des couleurs** : choisissez l’option **Autoriser** pour permettre les réglages de couleurs inversées afin que les utilisateurs puissent ajuster la fonction de couleurs inversées. L’option **Non configuré** désactive cette fonctionnalité.
- **Lire le texte sélectionné** : choisissez l’option **Autoriser** pour permettre l’activation des paramètres d’accessibilité de sélection de la reconnaissance vocale sur l’appareil. Cette fonctionnalité lit à voix haute le texte que l’utilisateur sélectionne. L’option **Non configuré** désactive cette fonctionnalité.
- **Contrôle de VoiceOver** : choisissez l’option **Autoriser** pour permettre aux utilisateurs de modifier la fonction VoiceOver, notamment la vitesse de lecture à voix haute du texte à l’écran. L’option **Non configuré** empêche toute modification de VoiceOver.
- **Réglage du zoom** : choisissez l’option **Autoriser** pour permettre aux utilisateurs de changer le zoom. L’option **Non configuré** empêche toute modification du zoom.

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

- **Safari (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher l’utilisation du navigateur Safari sur l’appareil. L’option **Non configuré** autorise l’utilisation du navigateur Safari.
- **Remplissage automatique** : choisissez l’option **Bloquer** pour désactiver la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.
- **Cookies** : choisissez la façon dont les cookies sont gérés sur l’appareil. Les options disponibles sont les suivantes :
  - Autoriser
  - Bloquer tous les cookies
  - Autoriser les cookies des sites web visités
  - Autoriser les cookies du site web actuel
- **JavaScript** : choisissez l’option **Bloquer** pour empêcher l’exécution des scripts Java dans le navigateur sur l’appareil. L’option **Non configuré** autorise les scripts Java.
- **Avertissements en cas de fraude** : choisissez l’option **Exiger** pour forcer l’affichage d’avertissements en cas de fraude dans le navigateur web de l’appareil. L’option **Non configuré** désactive cette fonctionnalité.
- **Fenêtres contextuelles** : choisissez l’option **Bloquer** pour désactiver le bloqueur de fenêtres contextuelles dans le navigateur web. L’option **Non configuré** autorise le bloqueur de fenêtres publicitaires.

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domaines d’e-mail non marqués

Dans **URL de domaine d’e-mail**, ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs finaux reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez saisis, l’e-mail est marqué comme non approuvé dans l’application iOS Mail.

### <a name="managed-web-domains"></a>Domaines web gérés

Dans **URL de domaine web**, ajoutez une ou plusieurs URL à la liste. Les documents téléchargés à partir des domaines que vous saisissez sont considérés comme gérés. Ce paramètre s’applique uniquement aux documents téléchargés à l’aide du navigateur Safari.

### <a name="safari-password-autofill-domains"></a>Domaines de remplissage automatique des mots de passe Safari

Dans **URL de domaine**, ajoutez une ou plusieurs URL à la liste. Les utilisateurs peuvent uniquement enregistrer les mots de passe web à partir des URL de cette liste. Ce paramètre s’applique uniquement au navigateur Safari et aux appareils iOS 9.3 et versions ultérieures en mode supervisé. Si vous ne spécifiez aucune URL, les mots de passe peuvent être enregistrés à partir de tous les sites web.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Vous pouvez également définir des paramètres et restrictions d’appareil sur les appareils [macOS](device-restrictions-macos.md).
