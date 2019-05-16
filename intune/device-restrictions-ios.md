---
title: Paramètres d’appareil iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils iOS pour restreindre les fonctionnalités, y compris définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode kiosque, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/02/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d0623e9d12132ac470813d65510bc2c76379109
ms.sourcegitcommit: 79baf89e4a7a7b1cecb8ccf5cb976736ae6a7286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58871469"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils iOS. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, définir des règles de mot de passe, autoriser ou restreindre des applications spécifiques, et bien d’autres opérations.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils iOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration pour les restrictions appliquées aux appareils](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Général

- **Partager des données d’utilisation** : choisissez **Bloquer** pour empêcher l’appareil d’envoyer des données de diagnostic et d’utilisation à Apple. L’option (par défaut) **Non configuré** autorise l’envoi de ces données.
  - **Modification des paramètres d’envoi des diagnostics (mode supervisé uniquement)**  : l’option **Bloquer** empêche l’utilisateur de modifier les paramètres d’envoi des diagnostics et d’analyse des applications du volet **Diagnostics et utilisation** (paramètres de l’appareil). L’option (par défaut) **Non configuré**permet à l’utilisateur de modifier ces paramètres d’appareil.

    Cette fonctionnalité s’applique à :  
    - iOS 9.3.2 et versions ultérieures

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. Dans iOS 9.0 et ultérieur, cela bloque également les enregistrements d’écran. L’option (par défaut) **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran en tant qu’image ou vidéo.
  - **Observation de l’écran à distance avec l’application Classroom (mode supervisé uniquement)** : choisissez l’option **Bloquer** pour empêcher l’application Classroom d’observer à distance l’écran de l’appareil. L’option (par défaut) **Non configuré** autorise l’application Apple Classroom à afficher l’écran.

    Cette fonctionnalité s’applique à :  
    - iOS 9.3 et version ultérieure

  - **Observation des écrans sans invite par l’application En classe (mode supervisé uniquement)** : si cette option est définie sur **Autoriser**, les enseignants peuvent observer en mode silencieux l’écran des appareils iOS des étudiants qui n’en sont pas avertis à l’aide de l’application En classe. Les appareils des étudiants inscrits dans une classe et qui utilisent l’application Classroom accordent automatiquement une autorisation à l’enseignant de cette classe. **Non configuré** (par défaut) désactive cette fonctionnalité.
- **Certificats TLS non approuvés** : choisissez l’option **Bloquer** pour empêcher les certificats Transport Layer Security (TLS) non autorisés sur l’appareil. L’option **Non configuré** (par défaut) autorise les certificats TLS.
- **Approbation des applications d’entreprise** : choisissez **Bloquer** pour supprimer le bouton **Approuver Enterprise Developer** du menu Paramètres > Général > Profils et gestion des appareils sur l’appareil. L’option (par défaut) **Non configuré** permet à l’utilisateur de choisir de faire confiance aux applications qui n’ont pas été téléchargées sur l’App Store.
- **Modification de compte (mode supervisé uniquement)**  : si cette option est définie sur **Bloquer**, l’utilisateur ne peut pas mettre à jour les paramètres spécifiques à l’appareil dans l’application Réglages d’iOS. Par exemple, l’utilisateur ne peut ni créer de nouveaux comptes d’appareils ni modifier le nom d’utilisateur ou le mot de passe. L’option (par défaut) **Non configuré** permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique également aux options accessibles à partir des applications iOS comme Mail, Contacts, Calendrier, Twitter, etc. Elle ne s’applique pas aux applications avec des paramètres de compte qui ne sont pas configurables à partir des applications iOS comme Microsoft Outlook.
- **Heure de l’écran (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de définir leurs propres restrictions concernant l’heure de l’écran (paramètres de l’appareil). L’option **Non configuré** permet à l’utilisateur de configurer des restrictions sur l’appareil (par exemple, le contrôle parental ou les restrictions liées au contenu et à la confidentialité).

  Ce paramètre s’appelait autrefois **Activation des restrictions dans les paramètres de l’appareil**. Impact de cette modification :  
  
  - iOS 11.4.1 et versions antérieures : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. Il s’agit du même paramètre, et rien ne change pour les utilisateurs finaux.
  - iOS 12.0 et versions ultérieures : l’option **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil (Paramètres > Général > Heure de l’écran), notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 n’affichent plus l’onglet Restrictions dans les paramètres de l’appareil (Paramètres > Général > Gestion des appareils > Profil de gestion > Restrictions). Ces paramètres se trouvent dans **Heure de l’écran**.
  
- **Utiliser la réinitialisation de tous les paramètres et du contenu sur l’appareil (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher les utilisateurs d’utiliser l’option de réinitialisation de tout le contenu et de tous les paramètres sur l’appareil (mode supervisé uniquement). L’option (par défaut) **Non configuré** permet aux utilisateurs d’accéder à ces paramètres.
- **Modification du nom de l’appareil (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher toute modification du nom de l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier le nom de l’appareil.
- **Modification des paramètres de notification (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher toute modification des paramètres de notification. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier les paramètres de notification de l’appareil.
- **Modification du papier peint (supervisée uniquement)**  : choisissez **Bloquer** pour empêcher toute modification du papier peint. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier le fond d’écran de l’appareil.
- **Modification des paramètres d’approbation d’application d’entreprise (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres d’approbation d’application d’entreprise sur les appareils supervisés. L’option (par défaut) **Non configuré** autorise l’utilisateur à faire confiance aux applications qui n’ont pas été téléchargées sur l’App Store.
- **Modifications au profil de configuration (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le profil de configuration sur l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à installer des profils de configuration.
- **Verrou d’activation (mode supervisé uniquement)** : choisissez **Autoriser** pour activer le verrou d’activation sur les appareils iOS supervisés. Le verrouillage d'activation rend plus difficile la réactivation d'un appareil perdu ou volé.
- **Bloquer la suppression d’applications (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des applications. L’option (par défaut) **Non configuré** autorise les utilisateurs à supprimer des applications de l’appareil.
- **Bloque le mode USB restreint (mode supervisé uniquement)**  : choisissez **Bloquer** pour désactiver le mode USB restreint sur les appareils supervisés. Le mode USB restreint empêche les accessoires USB d'échanger des données avec un appareil verrouillé depuis plus d'une heure. L’option **Non configuré** (par défaut) autorise le mode USB restreint.
- **Application de la date et de l’heure automatique (mode supervisé uniquement)**  : **activez** cette option pour forcer les appareils supervisés à définir automatiquement la date et l’heure. Le fuseau horaire de l’appareil est mis à jour quand l’appareil se connecte à des réseaux cellulaires ou si les services de localisation ont été activés en mode Wi-Fi.
- **Require students to request permission to leave Classroom course (supervised only)** (Obliger les élèves à demander l’autorisation de quitter le cours Classroom - mode supervisé uniquement) : **activez** cette option pour obliger les élèves inscrits à un cours non managé et qui utilisent l’app Classroom à demander à l’enseignant l’autorisation de quitter le cours. L’option (par défaut) **Non configuré** dispense les étudiants de demander une autorisation.

  Cette fonctionnalité s’applique à :  
  - iOS 11.3 et versions ultérieures

- **Autoriser Classroom à verrouiller une application et verrouiller l’appareil sans envoyer d’invite (mode supervisé uniquement)**  : **Activer** permet aux enseignants de verrouiller les applications ou de verrouiller l’appareil à l’aide de l’application Classroom, sans en informer l’étudiant. Le verrouillage des applications signifie que l’appareil peut uniquement accéder aux applications qui ont été spécifiées par l’enseignant. **Non configuré** (par défaut) empêche les enseignants de verrouiller les applications ou les appareils à l’aide de l’application Classroom sans en informer l’étudiant. 

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Participer automatiquement aux cours Classroom sans envoyer d’invite (mode supervisé uniquement)**  : **Activer** permet automatiquement aux étudiants de rejoindre un cours de l’application Classroom sans que l’enseignant ait à fournir son approbation. **Non configuré** (par défaut) demande à l’enseignant s’il souhaite autoriser les étudiants à rejoindre un cours dans l’application Classroom.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Autoriser les mises à jour PKI à distance** : l’option **Autoriser** permet à vos utilisateurs de recevoir des mises à jour logicielles sans connecter leurs appareils à un ordinateur.
- **Limiter le suivi des publicités** : choisissez **Limiter** pour désactiver l’identificateur de publicités de l’appareil. **Non configuré** (par défaut) maintient l’activation de l’identificateur.
- **Bloquer la création de VPN (mode supervisé uniquement)**  : l’option **Bloquer** empêche les utilisateurs de créer des paramètres de configuration VPN. L’option (par défaut) **Non configuré** permet aux utilisateurs de créer des VPN sur l’appareil.
- **Modification des paramètres eSIM (mode supervisé uniquement)**  : l’option **Bloquer** empêche les utilisateurs de supprimer ou d’ajouter un forfait mobile pour l’eSIM de l’appareil. L’option (par défaut) **Non configuré** permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique à :  
  - iOS 12.1 et versions ultérieures

- **Différer les mises à jour logicielles (mode supervisé uniquement)**  : lorsque cette option est définie sur **Non configuré** (par défaut), les mises à jour logicielles sont affichées sur l’appareil dès leur publication par Apple. Par exemple, si une mise à jour iOS est publiée par Apple à une date spécifique, cette mise à jour s’affiche automatiquement sur l’appareil autour de la date de publication.

  **Activer** vous permet de différer l’affichage des mises à jour logicielles sur les appareils (de 0 à 90 jours). Ce paramètre ne permet pas de contrôler à quel moment les mises à jour sont installées. 

  - **Retarde la visibilité des mises à jour logicielles** : entrez une valeur comprise entre 0 et 90 jours. Quand le délai expire, les utilisateurs reçoivent une notification de mise à jour vers la version la plus récente du système d’exploitation disponible au moment du déclenchement du délai.

    Par exemple, si la version iOS 12.a est disponible le **1er janvier**, et si le **délai de visibilité** est défini sur **5 jours**, iOS 12.a ne s’affichera pas comme étant disponible sur les appareils des utilisateurs finaux. En revanche, le **sixième jour** suivant la publication, la mise à jour est disponible et les utilisateurs finaux peuvent l’installer.

    Ce paramètre s’applique à :  
    - iOS 11.3 et versions ultérieures

## <a name="password"></a>Mot de passe

- **Mot de passe** : **Exige** que l’utilisateur final entre un mot de passe pour accéder à l’appareil. L’option **Non configuré** autorise les utilisateurs à accéder à l’appareil sans entrer de mot de passe.
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
- **Modification du code secret (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. Les modifications apportées aux restrictions du code secret sont ignorées sur les appareils supervisés après le blocage de cette fonctionnalité. L’option **Non configuré** (par défaut) permet d’ajouter, modifier ou supprimer des codes secrets.

  - **Modification de l’empreinte digitale (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher la modification, l’ajout ou la suppression par l’utilisateur des empreintes digitales Touch ID. L’option (par défaut) **Non configuré** autorise l’utilisateur à mettre à jour les empreintes digitales Touch ID sur l’appareil.

- **Bloquer le remplissage automatique des mots de passe (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sous iOS. L’option **Bloquer** a également les conséquences suivantes :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option **Non configuré** (par défaut) autorise ces fonctionnalités.

- **Bloquer les demandes de mots de passe de proximité (mode supervisé uniquement)** : choisissez **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils situés à proximité. L’option **Non configuré** (par défaut) autorise ces demandes de mots de passe.
- **Bloquer le partage de mots de passe (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher le partage de mots de passe entre les appareils avec AirDrop. L’option **Non configuré** (par défaut) autorise le partage de mots de passe.
- **Exiger une authentification Touch ID ou Face ID pour le remplissage automatique du mot de passe ou des informations de carte de crédit (mode supervisé uniquement)**  : lorsque cette option est définie sur **Exiger**, les utilisateurs doivent s’authentifier à l’aide de TouchID ou de FaceID avant qu’un mot de passe ou des informations de carte de crédit ne puissent être automatiquement renseignés dans Safari et autres applications. **Non configuré** (par défaut) permet aux utilisateurs de contrôler cette fonctionnalité dans les paramètres de l’appareil.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

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
  - **Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés (mode supervisé uniquement)**  : choisissez l’option **Autoriser** pour permettre aux utilisateurs d’ajouter ou de synchroniser les informations de tous les contacts Outlook, y compris des contacts professionnels et d’entreprise, dans l’application Contacts intégrée à l’appareil. Avec l’option **Non configuré**, les utilisateurs ne sont pas autorisés à ajouter des contacts Outlook dans l’application Contacts intégrée sur l’appareil.
  
    Pour utiliser ce paramètre, définissez le paramètre **Affichage des documents d’entreprise dans les applications non gérées**  sur **Bloquer**.
  
- **Affichage des documents autres que ceux d’entreprise dans les applications d’entreprise** : choisissez **Bloquer** pour empêcher l’affichage de documents autres que ceux de l’entreprise dans les applications d’entreprise. L’option **Non configuré** autorise tout document à être affiché dans les applications d’entreprise gérées.
  - **Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés (mode supervisé uniquement)**  : choisissez l’option **Autoriser** pour permettre aux utilisateurs d’ajouter des informations de contact de l’application iContacts dans Outlook. L’option **Non configuré** empêche la lecture, y compris la suppression des doublons, dans l’application Contacts intégrée sur l’appareil.
  
    Pour utiliser ce paramètre, définissez le paramètre **Affichage de documents externes à l’entreprise dans les applications d’entreprise**  sur **Bloquer**.
  
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

#### <a name="safari"></a>Safari

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

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- **Applications interdites** : la liste des applications non gérées par Intune dont vous ne souhaitez pas qu’elles soient installées sur l’appareil. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.
- **Applications approuvées** : la liste des applications que les utilisateurs sont autorisés à installer. Pour rester conformes, ils ne doivent pas installer d’autres applications. Les applications qui sont gérées par Intune sont autorisées automatiquement. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Vous pouvez sinon exporter une liste existante comportant la liste des applications restreintes au même format.

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

- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Vous pouvez sinon exporter une liste existante comportant la liste des applications restreintes au même format.

## <a name="wireless"></a>Sans fil

- **Itinérance de données** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Récupération en arrière-plan globale en cas d'itinérance**  : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de récupération en arrière-plan globale lors de l’itinérance sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’appareil à récupérer des données comme les courriers électroniques lorsqu’il est en mode itinérance sur un réseau cellulaire.
- **Numérotation vocale** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil. L’option (par défaut) **Non configuré** autorise la numérotation vocale sur l’appareil.
- **Itinérance vocale** : choisissez **Bloquer** pour empêcher l’itinérance vocale sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Modifications des paramètres d'utilisation des données cellulaires des applications (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher toute modification des paramètres d’utilisation des données cellulaires des applications. L’option (par défaut) **Non configuré** permet à l’utilisateur de contrôler quelles applications sont autorisées à utiliser les données cellulaires.
- **Changements des paramètres de forfait mobile (mode supervisé uniquement)**  : l’option **Bloquer** empêche les utilisateurs de modifier les paramètres du forfait mobile. L’option**Non configuré** (par défaut) permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Point d’accès personnel** : l’option **Bloquer** désactive le point d’accès personnel sur l’appareil de l’utilisateur à chaque synchronisation de l’appareil. Ce paramètre n’est peut-être pas compatible avec certains opérateurs. **Non configuré** (par défaut) conserve la configuration de point d’accès personnel comme la valeur par défaut définie par l’utilisateur.
- **Rejoindre uniquement les réseaux Wi-Fi utilisant des profils de configuration (mode supervisé uniquement)** : **activez** cette option pour forcer l’appareil à rejoindre uniquement les réseaux Wi-Fi configurés à l’aide d’un profil de configuration Intune. L’option (par défaut) **Non configuré** autorise l’appareil à utiliser d’autres réseaux Wi-Fi.
- **Règles d’utilisation des données mobiles (applications gérées uniquement)** : définissez les types de données que les applications gérées peuvent utiliser sur les réseaux mobiles. Les options disponibles sont les suivantes :
  - **Bloquer l’utilisation de données cellulaires** : bloquez l’utilisation de données cellulaires pour **toutes les applications managées** ou **Choisir des applications spécifiques**.
  - **Bloquer l’utilisation de données cellulaires en itinérance** : bloquez l’utilisation de données cellulaires en itinérance pour **toutes les applications managées** ou **Choisir des applications spécifiques**.

## <a name="connected-devices"></a>Appareils connectés

- **AirDrop (supervisé uniquement)**: choisissez **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Appairage avec une Apple Watch (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’appairage avec une Apple Watch. L’option (par défaut) **Non configuré** autorise l’appairage avec une Apple Watch.
- **Détection du poignet pour une Apple Watch appairée** : **activez** cette option pour forcer une Apple Watch appairée à utiliser la détection du poignet. Si cette option est activée, l’Apple Watch n’affiche pas de notification si elle n’est pas portée. 
- **Modification Bluetooth (mode supervisé uniquement)** : **Bloquer** empêche l’utilisateur final de modifier les paramètres Bluetooth sur l’appareil. L’option (par défaut) **Non configuré** permet à l’utilisateur de modifier ces paramètres.
- **Appairage d’hôtes pour contrôler les appareils avec lesquels un appareil iOS peut s’appairer (mode supervisé uniquement)** : l’option (par défaut) **Non configuré** autorise l’appairage d’hôtes afin que l’administrateur puisse déterminer les appareils avec lesquels un appareil iOS peut s’appairer. L’option **Bloquer** empêche l’appairage d’hôtes.
- **Exiger un mot de passe associé pour les demandes AirPlay sortantes** : **nécessite** un mot de passe de jumelage lorsque l’utilisateur a recours à AirPlay pour diffuser le contenu vers d’autres appareils Apple. L’option (par défaut) **Non configuré** permet à l’utilisateur de diffuser en continu du contenu à l’aide d’AirPlay, sans entrer de mot de passe.
- **Bloquer AirPrint (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité AirPrint sur l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisation d’AirPrint.
  - **Bloquer le stockage des informations d'identification AirPrint dans le trousseau (mode supervisé uniquement)**  : choisissez **Bloquer** afin d’empêcher l’utilisation du stockage Trousseau pour le nom d’utilisateur et le mot de passe sur l’appareil. L’option (par défaut) **Non configuré** permet de stocker le nom d’utilisateur et le mot de passe AirPrint dans l’application Trousseau.
  - **Exiger un certificat TLS approuvé pour AirPrint (mode supervisé uniquement)**  : **activez** cette option pour forcer l’appareil à utiliser des certificats approuvés pour la communication de l'impression TLS.
  - **Bloquer la découverte par iBeacon des imprimantes AirPrint (mode supervisé uniquement)**  : choisissez **Bloquer** pour empêcher les balises AirPrint Bluetooth malveillants de lancer des attaques d’hameçonnage sur le réseau. L’option (par défaut) **Non configuré** permet de publier des imprimantes AirPrint sur l’appareil.
- **Bloquer la configuration de nouveaux appareils à proximité (mode supervisé uniquement)**  : l’option **Bloquer** désactive le message qui invite l’utilisateur à configurer de nouveaux appareils situés à proximité. **Non configuré** (par défaut) affiche des messages invitant l’utilisateur à connecter d’autres appareils Apple situés à proximité.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

## <a name="keyboard-and-dictionary"></a>Clavier et dictionnaire

- **Recherche de définition de mot (supervisé uniquement)**  : choisissez **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Claviers prédictifs (mode supervisé uniquement)** : l’option **Non configuré** autorise l’utilisation de claviers prédictifs pour suggérer des mots que l’utilisateur pourrait vouloir utiliser. L’option **Bloquer** empêche cette fonctionnalité.
- **Correction automatique (mode supervisé uniquement)** : l’option **Non configuré** permet à l’appareil de corriger automatiquement les mots mal orthographiés. Choisissez **Bloquer** pour désactiver la correction automatique.
- **Vérification orthographique du clavier (mode supervisé uniquement)**  : l’option **Non configuré** active le vérificateur d’orthographe sur l’appareil. Choisissez **Bloquer** pour désactiver le vérificateur d’orthographe.
- **Raccourcis clavier (mode supervisé uniquement)**  : l’option **Non configuré** permet d’utiliser les raccourcis clavier sur l’appareil. Choisissez **Bloquer** pour empêcher l’utilisation des raccourcis clavier.
- **Dictée (mode supervisé uniquement)** : choisissez **Bloquer** pour empêcher l’utilisateur de saisir du texte à l’aide de l’entrée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Sauvegarder sur iCloud** : l’option **Non configuré** autorise l’utilisateur à sauvegarder les données de l’appareil dans iCloud. Choisissez **Bloquer** pour empêcher l’utilisateur de sauvegarder les données de l’appareil dans iCloud.
- **Bloquer la synchronisation des documents sur iCloud (mode supervisé uniquement)**  : l’option **Non configuré** autorise la synchronisation des documents et des clés-valeurs dans votre espace de stockage iCloud. Choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et des données.
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

- Entrer les valeurs **Nom de l’application** et **ID d'ensemble d'applications**, puis sélectionner **Ajouter**. La section [ID d’ensemble pour les applications iOS intégrées](#bundle-ids-for-built-in-ios-apps) (dans cet article) inclut quelques applications et leurs ID.
- **Importer** un fichier CSV contenant la liste des noms d’application et leur ID d’ensemble. Ou, **exporter** une liste existante incluant les applications.

## <a name="kiosk-supervised-only"></a>Plein écran (supervisé uniquement)

- **Application à exécuter en mode plein écran** : choisissez le type d’applications que vous souhaitez exécuter en mode plein écran. Les options disponibles sont les suivantes :
  - **Non configuré** : les paramètres Kiosque ne sont pas appliqués. L’appareil ne s’exécute pas en mode Kiosque.
  - **App Store** : entrez l’URL d’une application de l’App Store d’iTunes.
  - **Application gérée** : choisissez une application que vous avez ajoutée à Intune.
  - **Application intégrée** : entrez l’[ID de bundle](#bundle-ids-for-built-in-ios-apps) (dans cet article) de l’application intégrée.

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
- **Réglages de couleurs inversées** : **Autoriser** les réglages de couleurs inversées pour permettre aux utilisateurs d’ajuster la fonction de couleurs inversées. L’option **Non configuré** désactive cette fonctionnalité.
- **Lire le texte sélectionné** : **autoriser** les paramètres d’accessibilité Sélection Speak sur l’appareil. Cette fonctionnalité lit à voix haute le texte que l’utilisateur sélectionne. L’option **Non configuré** désactive cette fonctionnalité.
- **Contrôle de VoiceOver** : **autoriser** les modifications VoiceOver pour permettre aux utilisateurs de mettre à jour la fonction VoiceOver, notamment la vitesse de lecture à voix haute du texte à l’écran. L’option **Non configuré** empêche toute modification de VoiceOver.
- **Réglage du zoom** : **autoriser** l’utilisateur à régler le zoom. L’option **Non configuré** empêche toute modification du zoom.

> [!NOTE]
> Avant de pouvoir configurer un appareil iOS pour le mode plein écran, vous devez utiliser l’outil Apple Configurator ou le Programme d’inscription des appareils Apple pour mettre l’appareil en mode supervisé. Consultez le guide Apple sur l’utilisation de l’outil Apple Configurator.
> Si l’application iOS que vous spécifiez est installée après l’attribution du profil, l’appareil ne bascule en mode plein écran qu’après son redémarrage.

## <a name="domains"></a>Domains

- **Domaines d’e-mail non marqués** > **URL de domaine d’e-mail** : ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs finaux reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez saisis, l’e-mail est marqué comme non approuvé dans l’application iOS Mail.

- **Domaines web gérés** > **URL de domaine web** : ajoutez une ou plusieurs URL à la liste. Les documents téléchargés à partir des domaines que vous saisissez sont considérés comme gérés. Ce paramètre s’applique uniquement aux documents téléchargés à l’aide du navigateur Safari.

- **Domaines de remplissage automatique des mots de passe Safari (en mode supervisé uniquement)** > **URL de domaine** : ajoutez une ou plusieurs URL à la liste. Les utilisateurs peuvent uniquement enregistrer les mots de passe web à partir des URL de cette liste. Ce paramètre s’applique uniquement au navigateur Safari et aux appareils iOS 9.3 et versions ultérieures en mode supervisé. Si vous ne spécifiez aucune URL, les mots de passe peuvent être enregistrés à partir de tous les sites web.

## <a name="bundle-ids-for-built-in-ios-apps"></a>ID de bundle pour les applications iOS intégrées

La liste suivante indique l’ID d’ensemble de quelques applications iOS intégrées parmi les plus courantes. Pour rechercher l’ID d’ensemble d’autres applications, contactez votre éditeur de logiciels.

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
| com.apple.DocumentsApp      | Fichiers        | Apple     |
| com.apple.mobileme.fmf1     | Trouver des amis | Apple     |
| com.apple.mobileme.fmip1    | Trouver un iPhone  | Apple     |
| com.apple.gamecenter        | Centre de jeux  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Intégrité       | Apple     |
| com.apple.Home              | Accueil         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
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
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Paramètres     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Bourse       | Apple     |
| com.apple.tips              | Conseils         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Vidéos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Portefeuille       | Apple     |
| com.apple.Bridge            | Regardez        | Apple     |
| com.apple.weather           | Météo      | Apple     |

## <a name="settings-that-require-supervised-mode"></a>Paramètres qui nécessitent le mode supervisé

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
> Apple a confirmé que certains paramètres passeront en mode supervisé uniquement en 2019. Nous vous recommandons de prendre ceci en considération lors de l’utilisation de ces paramètres. Plutôt qu’attendre qu’ils soient migrés en mode supervisé uniquement par Apple :
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

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également appliquer des restrictions sur les fonctionnalités ou les paramètres des appareils [macOS](device-restrictions-macos.md).
