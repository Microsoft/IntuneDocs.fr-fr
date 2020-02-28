---
title: Paramètres d’appareil macOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils macOS pour restreindre les fonctionnalités, notamment définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode kiosque, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d26c4c6cd05a411555f7824ad21b72431eb569c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511170"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune



Cet article répertorie et décrit les différents paramètres que vous pouvez contrôler sur les appareils macOS. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, définir des règles de mot de passe, autoriser ou restreindre des applications spécifiques, et bien d’autres opérations.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils macOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration pour les restrictions appliquées aux appareils](../device-restrictions-configure.md).

> [!NOTE]
> Ces paramètres s’appliquent à différents types d’inscription. Pour plus d’informations sur les différents types d’inscriptions, consultez [Inscription macOS](../macos-enroll.md).

## <a name="general"></a>Général

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **Rechercher la définition** : choisissez l’option **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option (par défaut) **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Dictée** : choisissez l’option **Bloquer** pour empêcher l’utilisateur d’entrer du texte par dictée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.
- **Mise en cache du contenu** : choisissez **Non configuré** (par défaut) pour permettre la mise en cache du contenu. La mise en cache du contenu stocke localement les données d’application, les données de navigateur web, les téléchargements et d’autres types de données sur l’appareil. Sélectionnez **Bloquer** pour empêcher que ces données ne soient stockées dans le cache.

  Pour plus d’informations sur la mise en cache du contenu sur macOS, consultez [Gérer la mise en cache de contenu sur Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (ouvre un autre site web).

  Cette fonctionnalité s’applique à :  
  - macOS 10.13 et versions ultérieures

- **Différer les mises à jour logicielles** : lorsque cette option est définie sur **Non configuré** (par défaut), les mises à jour logicielles sont affichées sur l’appareil dès leur publication par Apple. Par exemple, si une mise à jour macOS est publiée par Apple à une date spécifique, cette mise à jour s’affichera automatiquement sur l’appareil autour de la date de publication. Les mises à jour des builds seed sont autorisées sans délai.

  **Activer** vous permet de différer l’affichage des mises à jour logicielles sur les appareils (de 0 à 90 jours). Ce paramètre ne permet pas de contrôler à quel moment les mises à jour sont installées. 

  - **Retarde la visibilité des mises à jour logicielles** : entrez une valeur comprise entre 0 et 90 jours. Quand le délai expire, les utilisateurs reçoivent une notification de mise à jour vers la version la plus récente du système d’exploitation disponible au moment du déclenchement du délai.

    Par exemple, si la mise à jour macOS est disponible le **1er janvier**, et si le **délai de visibilité** est défini sur **5 jours**, la mise à jour ne s’affichera pas comme étant disponible. En revanche, le **sixième jour** suivant la publication, la mise à jour est disponible et les utilisateurs finaux peuvent l’installer.

    Cette fonctionnalité s’applique à :  
    - macOS 10.13.4 et versions ultérieures

- **Captures d’écran** : l’appareil doit être inscrit dans le cadre de l’inscription automatique des appareils (DEP) Apple. Quand la valeur est **Bloquer**, les utilisateurs ne peuvent pas enregistrer de capture d’écran. Elle empêche également l’application Classroom d’observer les écrans à distance. **Non configuré** (par défaut) permet aux utilisateurs de faire des captures d’écran et permet à l’application Classroom d’afficher les écrans à distance.

### <a name="settings-apply-to-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription automatique des appareils

- **Observation des écrans à distance avec l'application Classroom** : **Désactiver** empêche les enseignants d’utiliser l’application Classroom pour voir les écrans des étudiants. **Non configuré** (par défaut) permet aux enseignants de voir les écrans des étudiants.

  Pour utiliser ce paramètre, définissez le paramètre **Captures d’écran** sur **Non configuré** (les captures d’écran sont autorisées).

- **Observation des écrans sans invite par l'application Classroom** : **Autoriser** permet aux enseignants de voir les écrans de leurs élèves sans leur accord. **Non configuré** (par défaut) exige l’accord de l’étudiant pour que l’enseignant puisse voir les écrans.

  Pour utiliser ce paramètre, définissez le paramètre **Captures d’écran** sur **Non configuré** (les captures d’écran sont autorisées).

- **Les étudiants doivent demander l'autorisation de quitter un cours Classroom** : **Exiger** oblige les élèves inscrits dans un cours non géré à obtenir l’approbation d’un enseignant avant de quitter le cours. **Non configuré** (par défaut) permet aux élèves de quitter le cours lorsqu’il le souhaite.

- **Les enseignants peuvent automatiquement verrouiller des appareils ou des applications dans l'application Classroom** : **Autoriser** permet aux enseignants de verrouiller l’appareil ou l’application d’un étudiant sans son accord. **Non configuré** (par défaut) exige l’accord de l’étudiant pour que l’enseignant puisse verrouiller l’appareil ou l’application.

- **Les étudiants peuvent automatiquement rejoindre un cours Classroom** : **Autoriser** permet aux élèves de participer à un cours sans que l’enseignant ait à fournir son approbation. **Non configuré** (par défaut) nécessite l’approbation d’un enseignant pour participer à un cours.

## <a name="password"></a>Mot de passe

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **Mot de passe** : **Demande** à l’utilisateur final de saisir un mot de passe pour pouvoir accéder à l’appareil. **Non configuré** (par défaut) ne requiert pas de mot de passe. Par ailleurs, elle ne force aucune restriction, comme le blocage des mots de passe simples ou la configuration d’une longueur minimale.
  - **Type de mot de passe requis** : Indique si le mot de passe peut être uniquement de nature numérique ou s’il doit être alphanumérique (c’est-à-dire, contenir des lettres et des chiffres).

    Cette fonctionnalité s’applique à :  
    - macOS 10.10.3 et versions ultérieures

  - **Nombre de caractères non alphanumériques dans le mot de passe** : Spécifie le nombre de caractères complexes nécessaires dans le mot de passe (de **0** à **4**).<br>Un caractère complexe est un symbole, par exemple, « **?** ».
  - **Longueur minimale du mot de passe** : Saisissez la longueur minimale du mot de passe qu’un utilisateur doit configurer (entre **4** et **16** caractères).
  - **Mots de passe simples** : Permet d’utiliser des mots de passe simples, tels que **0000** ou **1234**.
  - **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe** : Indique la durée pendant laquelle l’ordinateur doit être inactif avant qu’un mot de passe soit requis pour le déverrouiller.
  - **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** : Spécifie la durée pendant laquelle l’ordinateur doit être inactif avant que l’écran de veille ne se verrouille.
  - **Expiration du mot de passe (en jours)** : Spécifie le nombre de jours qui s’écoule avant que l’utilisateur ne doive changer le mot de passe (entre **1** et **255** jours).
  - **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de mots de passe précédemment utilisés (de **1** à **24**) qui ne peuvent pas être utilisés.

- **Empêcher l’utilisateur de modifier le code secret** : choisissez l’option **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. L’option (par défaut) **Non configuré** permet d’ajouter, modifier ou supprimer des codes secrets.
- **Bloquer le déverrouillage par empreinte digitale** : choisissez l’option **Bloquer** pour empêcher l’utilisateur de déverrouiller l’appareil avec une empreinte digitale. L’option (par défaut) **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.

- **Bloquer le remplissage automatique du mot de passe** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sur macOS. L’option **Bloquer** a également les conséquences suivantes :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option (par défaut)**Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mot de passe à proximité** : choisissez l’option **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils à proximité. L’option (par défaut) **Non configuré** autorise ces demandes de mots de passe.

- **Bloquer le partage de mot de passe** : choisissez l’option **Bloquer** pour empêcher le partage des mots de passe entre les appareils avec AirDrop. L’option (par défaut) **Non configuré** autorise le partage de mots de passe.

## <a name="built-in-apps"></a>Applications intégrées

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **Bloquer le remplissage automatique de Safari** : choisissez l’option **Bloquer** pour désactiver la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option (par défaut) **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.
- **Bloquer l’appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option (par défaut)**Non configuré** autorise l’accès à l’appareil photo de l’appareil.
- **Bloquer Apple Music** : choisissez l’option **Bloquer** pour rétablir l’application Music en mode classique et désactiver le service Music. L’option (par défaut) **Non configuré** autorise l’utilisation du service Apple Music.
- **Bloquer les résultats de recherche Internet de Spotlight** : choisissez l’option **Bloquer** pour empêcher Spotlight de retourner les résultats d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.
- **Bloquer le transfert de fichiers à l'aide d'iTunes** : l’option **Bloquer** désactive les services de partage de fichiers d’application. **Non configuré** (par défaut) autorise les services de partage de fichiers d’application.

  Cette fonctionnalité s’applique à :  
  - macOS 10.13 et versions ultérieures

## <a name="restricted-apps"></a>Applications restreintes

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **Type de liste d’applications restreintes** : Créez une liste d’applications que les utilisateurs ne sont pas autorisés à installer ou à utiliser. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Il n’existe aucune restriction d’Intune. Les utilisateurs ont accès aux applications que vous attribuez et aux applications intégrées.
  - **Applications interdites** : applications non managées par Intune dont vous souhaitez empêcher l’installation sur l’appareil. Rien n’empêche les utilisateurs d’installer une application interdite. Toutefois, si un utilisateur installe une application de cette liste, cela est signalé dans Intune.
  - **Applications approuvées** : applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Rien n’empêche les utilisateurs d’installer une application qui ne figure pas dans la liste approuvée. Toutefois, s’ils le font, cela est signalé dans Intune.
- **ID de l'ensemble d'applications** : entrez l’[ID d’ensemble d’applications](bundle-ids-built-in-ios-apps.md) pour l’application. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site web d’Apple contient une liste d’[applications Apple intégrées](https://support.apple.com/HT208094).
- **Nom de l’application** : entrez le nom de l’application. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site web d’Apple contient une liste d’[applications Apple intégrées](https://support.apple.com/HT208094).
- **Éditeur** : entrez l’éditeur de l’application souhaitée.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** : Sélectionnez cette option pour créer votre liste d’applications.
- **Importez** un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app bundle ID>, <app name>, <app publisher>`. Sinon, sélectionnez **Exporter** pour créer une liste des applications que vous avez ajoutées, au même format.

## <a name="connected-devices"></a>Appareils connectés

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **Bloquer AirDrop** : choisissez l’option **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option (par défaut)**Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Bloquer le déverrouillage automatique avec Apple Watch** : l’option **Bloquer** empêche les utilisateurs de déverrouiller leur appareil macOS avec leur Apple Watch. **Non configuré** (par défaut) permet aux utilisateurs de déverrouiller leur appareil macOS avec leur Apple Watch.

## <a name="cloud-and-storage"></a>Cloud et stockage

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **Bloquer la synchronisation du trousseau iCloud** : choisissez l’option **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option (par défaut) **Non configuré** autorise les utilisateurs à synchroniser ces identifiants.
- **Bloquer la synchronisation des documents iCloud** : Choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et des données. L’option (par défaut) **Non configuré** autorise la synchronisation des documents et des pairs clé-valeur dans votre espace de stockage iCloud.
- **Bloquer la sauvegarde d'e-mails iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et l’application de messagerie macOS. L’option **Non configuré** (par défaut) autorise la synchronisation de la messagerie avec iCloud.
- **Bloquer la sauvegarde de contacts iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et les contacts des appareils. **Non configuré** (par défaut) permet la synchronisation des contacts avec iCloud.
- **Bloquer la sauvegarde de calendriers iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et l’application de calendrier macOS. **Non configuré** (par défaut) autorise la synchronisation du calendrier avec iCloud.
- **Bloquer la sauvegarde de rappels iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et l’application Rappels macOS. **Non configuré** (par défaut) autorise la synchronisation des rappels avec iCloud.
- **Bloquer la sauvegarde de signets iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et les signets des appareils. **Non configuré** (par défaut) autorise la synchronisation des signets avec iCloud.
- **Bloquer la sauvegarde de notes iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et les notes des appareils. **Non configuré** (par défaut) autorise la synchronisation des notes avec iCloud.
- **Bloquer la photothèque iCloud** : **Bloquer** désactive la photothèque iCloud et empêche iCloud de synchroniser les photos des appareils. Toutes les photos qui ne sont pas entièrement téléchargées de la Photothèque iCloud sont supprimées du stockage local de l’appareil. **Non configuré** (par défaut) autorise la synchronisation des photos entre l’appareil et la photothèque iCloud.
- **Handoff** : **Non configuré** (valeur par défaut) permet aux utilisateurs de commencer à travailler sur un appareil macOS, puis de poursuivre le travail qu’ils ont commencé sur un autre appareil iOS/iPadOS ou macOS. **Bloquer** empêche la fonctionnalité Handoff sur l’appareil. 

  Cette fonctionnalité s’applique à :  
  - macOS 10.15 et ultérieur

## <a name="domains"></a>Domaines

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : Inscription d’appareil et inscription automatique d’appareils

- **URL de domaine d'e-mail** : **ajoutez** une ou plusieurs URL à la liste. Quand les utilisateurs reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez configurés, l’e-mail est marqué comme non approuvé dans l’application macOS Mail.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](../device-profile-assign.md) et [suivre son état](../device-profile-monitor.md).

Vous pouvez également appliquer des restrictions sur les fonctionnalités ou les paramètres des appareils [iOS/iPadOS](../device-restrictions-ios.md).
