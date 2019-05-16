---
title: Paramètres d’appareil macOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils macOS pour restreindre les fonctionnalités, notamment définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode kiosque, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798375"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils macOS pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article répertorie et décrit les différents paramètres que vous pouvez contrôler sur les appareils macOS. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, définir des règles de mot de passe, autoriser ou restreindre des applications spécifiques, et bien d’autres opérations.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils macOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration pour les restrictions appliquées aux appareils](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Général

- **Bloquer la recherche de définition** : choisissez **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option (par défaut) **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Bloquer la dictée** : choisissez **Bloquer** pour empêcher l’utilisateur d’entrer du texte par dictée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.
- **Bloquer la mise en cache du contenu** : choisissez **Non configuré** (par défaut) pour permettre la mise en cache du contenu. La mise en cache du contenu stocke localement les données d’application, les données de navigateur web, les téléchargements et d’autres types de données sur l’appareil. Sélectionnez **Bloquer** pour empêcher que ces données ne soient stockées dans le cache.

  Pour plus d’informations sur la mise en cache du contenu sur macOS, consultez [Gérer la mise en cache de contenu sur Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (ouvre un autre site web).

  Cette fonctionnalité s’applique à :  
  - macOS 10.13 et versions ultérieures

- **Différer les mises à jour logicielles** : lorsque cette option est définie sur **Non configuré** (par défaut), les mises à jour logicielles sont affichées sur l’appareil dès leur publication par Apple. Par exemple, si une mise à jour macOS est publiée par Apple à une date spécifique, cette mise à jour s’affichera automatiquement sur l’appareil autour de la date de publication. Les mises à jour des builds seed sont autorisées sans délai.

  **Activer** vous permet de différer l’affichage des mises à jour logicielles sur les appareils (de 0 à 90 jours). Ce paramètre ne permet pas de contrôler à quel moment les mises à jour sont installées. 

  - **Retarde la visibilité des mises à jour logicielles** : entrez une valeur comprise entre 0 et 90 jours. Quand le délai expire, les utilisateurs reçoivent une notification de mise à jour vers la version la plus récente du système d’exploitation disponible au moment du déclenchement du délai.

    Par exemple, si la mise à jour macOS est disponible le **1er janvier**, et si le **délai de visibilité** est défini sur **5 jours**, la mise à jour ne s’affichera pas comme étant disponible sur les appareils. En revanche, le **sixième jour** suivant la publication, la mise à jour est disponible et les utilisateurs finaux peuvent l’installer.

    Cette fonctionnalité s’applique à :  
    - macOS 10.13.4 et versions ultérieures

## <a name="password"></a>Mot de passe

- **Mot de passe** : **Exige** que l’utilisateur final entre un mot de passe pour accéder à l’appareil. **Non configuré** (par défaut) ne nécessite pas de mot de passe et ne force aucune restriction, comme le blocage des mots de passe simples ou la configuration d’une longueur minimale.
  - **Type de mot de passe requis** : indique si le mot de passe peut être uniquement de nature numérique ou s’il doit être alphanumérique (c’est-à-dire, contenir des lettres et des chiffres). Ce paramètre est uniquement pris en charge sur les systèmes Mac OS X 10.10.3 et les versions ultérieures.
  - **Nombre de caractères non alphanumériques dans le mot de passe** : indique le nombre de caractères complexes requis dans le mot de passe (**0** à **4**).<br>Un caractère complexe est un symbole, par exemple, « **?** ».
  - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit configurer (entre **4** et **16** caractères).
  - **Mots de passe simples** : permet d’utiliser des mots de passe simples, tels que **0000** ou **1234**.
  - **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe** : indique la durée pendant laquelle l’ordinateur doit être inactif avant qu’un mot de passe soit requis pour le déverrouiller.
  - **Nombre de minutes d’inactivité avant le verrouillage de l’appareil** : indique la durée pendant laquelle l’ordinateur doit être inactif avant le verrouillage de l’écran.
  - **Expiration du mot de passe (jours)** : indique le nombre de jours qui s’écoulent avant que l’utilisateur ne doive changer le mot de passe (entre **1** et **255** jours).
  - **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de mots de passe précédents qui ne peuvent pas être réutilisés (entre**1** et **24**).

- **Empêcher l’utilisateur de modifier le code secret** : choisissez **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. L’option (par défaut) **Non configuré** permet d’ajouter, modifier ou supprimer des codes secrets.
- **Bloquer le déverrouillage par empreinte digitale** : choisissez **Bloquer** afin d’empêcher l’utilisation d’une empreinte digitale pour déverrouiller l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.

- **Bloquer le remplissage automatique des mots de passe** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sous macOS. L’option **Bloquer** a également les conséquences suivantes :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option (par défaut)**Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mots de passe de proximité** : choisissez **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils situés à proximité. L’option (par défaut) **Non configuré** autorise ces demandes de mots de passe.

- **Bloquer le partage de mots de passe** : choisissez **Bloquer** pour empêcher le partage de mots de passe entre les appareils avec AirDrop. L’option (par défaut) **Non configuré** autorise le partage de mots de passe.

## <a name="built-in-apps"></a>Applications intégrées

- **Bloquer le remplissage automatique dans Safari** : l’option **Bloquer** désactive la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option (par défaut) **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.
- **Bloquer l’appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option (par défaut)**Non configuré** autorise l’accès à l’appareil photo de l’appareil.
- **Bloquer Apple Music** : choisissez l’option **Bloquer** pour rétablir l’application Music en mode classique et désactiver le service Music. L’option (par défaut) **Non configuré** autorise l’utilisation du service Apple Music.
- **Empêcher Spotlight de retourner des résultats de recherche provenant d’Internet** : choisissez **Bloquer** pour empêcher Spotlight de retourner des résultats à partir d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.
- **Bloquer le transfert de fichiers à l’aide d’iTunes** : l’option **Bloquer** désactive les services de partage de fichiers d’application. Disponible dans macOS 10.13 et ultérieur. **Non configuré** (par défaut) autorise les services de partage de fichiers d’application.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- Liste d’**Applications interdites** : répertorie les applications qui ne sont pas gérées par Intune et que les utilisateurs ne sont pas autorisés à installer et à exécuter. Rien n’empêche les utilisateurs d’installer une application interdite, mais, s’ils le font, l’administrateur en est informé.
- Liste d’**Applications approuvées** : répertorie les applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Rien n’empêche les utilisateurs d’installer une application qui ne figure pas dans la liste approuvée. Toutefois, s’ils le font, l’administrateur en est informé.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application et l’ID d’ensemble de l'application (par exemple *com.apple.calculator*).

## <a name="connected-devices"></a>Appareils connectés

- **Bloquer AirDrop** : choisissez l’option **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option (par défaut)**Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Bloquer le déverrouillage automatique avec Apple Watch** : l’option **Bloquer** empêche les utilisateurs de déverrouiller leur appareil macOS avec leur Apple Watch. **Non configuré** (par défaut) permet aux utilisateurs de déverrouiller leur appareil macOS avec leur Apple Watch.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Bloquer la synchronisation du trousseau iCloud** : choisissez **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option (par défaut) **Non configuré** autorise les utilisateurs à synchroniser ces identifiants.
- **Bloquer la synchronisation des documents avec iCloud** : choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et les données. L’option (par défaut) **Non configuré** autorise la synchronisation des documents et des pairs clé-valeur dans votre espace de stockage iCloud.
- **Bloquer la sauvegarde de la messagerie dans iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et l’application de messagerie macOS. L’option **Non configuré** (par défaut) autorise la synchronisation de la messagerie avec iCloud.
- **Bloquer la sauvegarde des contacts dans iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et les contacts des appareils. **Non configuré** (par défaut) permet la synchronisation des contacts avec iCloud.
- **Bloquer la sauvegarde du calendrier dans iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et l’application Calendrier de macOS. **Non configuré** (par défaut) autorise la synchronisation du calendrier avec iCloud.
- **Bloquer la sauvegarde des rappels dans iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et l’application Rappels de macOS. **Non configuré** (par défaut) autorise la synchronisation des rappels avec iCloud.
- **Bloquer la sauvegarde des signets dans iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et les signets des appareils. **Non configuré** (par défaut) autorise la synchronisation des signets avec iCloud.
- **Bloquer la sauvegarde des notes dans iCloud** : l’option **Bloquer** empêche la synchronisation entre iCloud et les notes des appareils. **Non configuré** (par défaut) autorise la synchronisation des notes avec iCloud.

## <a name="domains"></a>Domains

- **URL de domaine d’e-mail** : ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez configurés, l’e-mail est marqué comme non approuvé dans l’application MacOS Mail.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également appliquer des restrictions sur les fonctionnalités ou les paramètres des appareils [iOS](device-restrictions-ios.md).
