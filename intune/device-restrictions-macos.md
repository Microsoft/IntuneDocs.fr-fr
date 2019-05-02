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

[Créer un profil de configuration des restrictions de périphérique](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Général

- **Bloquer la recherche de définition** : choisissez **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option (par défaut) **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Bloquer la dictée** : choisissez **Bloquer** pour empêcher l’utilisateur d’entrer du texte par dictée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.
- **Bloquer le contenu de la mise en cache**: choisissez **ne pas configuré** (valeur par défaut) pour activer le contenu de la mise en cache. Contenu de la mise en cache stocke les données d’application, des données de navigateur web, des téléchargements et bien plus encore localement sur l’appareil. Sélectionnez **bloc** pour empêcher que ces données sont stockées dans le cache.

  Pour plus d’informations sur le contenu de la mise en cache sur macOS, consultez [gérer le contenu de la mise en cache sur Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (ouvre un autre site Web).

  Cette fonctionnalité s’applique à :  
  - macOS 10.13 et versions ultérieures

- **Différer les mises à jour logicielles**: lorsque la valeur **ne pas configuré** (valeur par défaut), les mises à jour logicielles sont affichés sur l’appareil comme Apple les libère. Par exemple, si une mise à jour de macOS est libérée par Apple à une date spécifique, puis cette mise à jour naturellement apparaît sur l’appareil autour de la date de publication. Mises à jour de la génération initiale sont autorisées sans délai.

  **Activer** vous permet de délai lorsque les mises à jour logicielles sont affichées sur les appareils, à partir de 0 à 90 jours. Ce paramètre ne contrôle pas lorsque les mises à jour sont ou ne sont pas installés. 

  - **Délai de visibilité des mises à jour logicielles**: entrez une valeur comprise entre 0 et 90 jours. Quand le délai expire, les utilisateurs reçoivent une notification de mise à jour vers la version la plus récente du système d’exploitation disponible au moment du déclenchement du délai.

    Par exemple, si une mise à jour de macOS est disponible sur **le 1er janvier**, et **retarder visibilité** a la valeur **5 jours**, la mise à jour n’est pas affichée sous la forme d’une mise à jour disponible sur les appareils. Sur le **sixième jour** suivant la publication, la mise à jour est disponible et les utilisateurs finaux peuvent l’installer.

    Cette fonctionnalité s’applique à :  
    - macOS 10.13.4 et versions ultérieures

## <a name="password"></a>Mot de passe

- **Mot de passe** : **Exige** que l’utilisateur final entre un mot de passe pour accéder à l’appareil. **Ne pas configuré** (valeur par défaut) ne nécessite pas un mot de passe et ne force pas les restrictions, telles que le blocage des mots de passe simples ou de la définition d’une longueur minimale.
  - **Type de mot de passe requis** : indique si le mot de passe peut être uniquement de nature numérique ou s’il doit être alphanumérique (c’est-à-dire, contenir des lettres et des chiffres). Ce paramètre est uniquement pris en charge sur les systèmes Mac OS X 10.10.3 et les versions ultérieures.
  - **Nombre de caractères non alphanumériques dans le mot de passe** : indique le nombre de caractères complexes requis dans le mot de passe (**0** à **4**).<br>Un caractère complexe est un symbole, par exemple, « **?** ».
  - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit configurer (entre **4** et **16** caractères).
  - **Mots de passe simples** : permet d’utiliser des mots de passe simples, tels que **0000** ou **1234**.
  - **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe** : indique la durée pendant laquelle l’ordinateur doit être inactif avant qu’un mot de passe soit requis pour le déverrouiller.
  - **Nombre de minutes d’inactivité avant le verrouillage de l’appareil** : indique la durée pendant laquelle l’ordinateur doit être inactif avant le verrouillage de l’écran.
  - **Expiration du mot de passe (jours)** : indique le nombre de jours qui s’écoulent avant que l’utilisateur ne doive changer le mot de passe (entre **1** et **255** jours).
  - **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de mots de passe précédents qui ne peuvent pas être réutilisés (entre**1** et **24**).

- **Empêcher l’utilisateur de modifier le code secret**: choisissez **bloc** pour arrêter le code secret soit modifié, ajouté ou supprimé. L’option (par défaut) **Non configuré** permet d’ajouter, modifier ou supprimer des codes secrets.
- **Bloquer le déverrouillage par empreinte digitale** : choisissez **Bloquer** afin d’empêcher l’utilisation d’une empreinte digitale pour déverrouiller l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.

- **Bloquer le remplissage automatique des mots de passe** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sous macOS. En choisissant **bloc** a également l’impact suivant :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option (par défaut)**Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mots de passe de proximité** : choisissez **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils situés à proximité. L’option (par défaut) **Non configuré** autorise ces demandes de mots de passe.

- **Bloquer le partage de mots de passe** : choisissez **Bloquer** pour empêcher le partage de mots de passe entre les appareils avec AirDrop. L’option (par défaut) **Non configuré** autorise le partage de mots de passe.

## <a name="built-in-apps"></a>Applications intégrées

- **Bloquer le remplissage automatique dans Safari** : l’option **Bloquer** désactive la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option (par défaut) **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.
- **Bloquer l’appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option (par défaut)**Non configuré** autorise l’accès à l’appareil photo de l’appareil.
- **Bloquer Apple Music** : choisissez l’option **Bloquer** pour rétablir l’application Music en mode classique et désactiver le service Music. L’option (par défaut) **Non configuré** autorise l’utilisation du service Apple Music.
- **Résultats de recherche Internet de Spotlight bloc**: **bloc** arrête Spotlight de retourner des résultats à partir d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.
- **Bloquer le transfert de fichiers à l’aide d’iTunes**: **bloc** désactive les services de partage de fichiers application. Disponible dans macOS 10.13 et versions ultérieures. **Ne pas configuré** (valeur par défaut) autorise les services de partage de fichiers application.

## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- Liste d’**Applications interdites** : répertorie les applications qui ne sont pas gérées par Intune et que les utilisateurs ne sont pas autorisés à installer et à exécuter. Les utilisateurs peuvent ne pas installer une application interdite, mais s’ils le font, il est signalé à l’administrateur.
- Liste d’**Applications approuvées** : répertorie les applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Les utilisateurs ne sont pas empêchés d’installer une application qui n’est pas dans la liste approuvée. Toutefois, s’ils le font, il est signalé à l’administrateur.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application et l’ID d’ensemble de l'application (par exemple *com.apple.calculator*).

## <a name="connected-devices"></a>Appareils connectés

- **Bloquer AirDrop** : choisissez l’option **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option (par défaut)**Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Déverrouillage automatique de bloc Apple Watch**: **bloc** empêche les utilisateurs de déverrouiller son appareil macOS avec leurs Apple Watch. **Ne pas configuré** (valeur par défaut) permet aux utilisateurs de déverrouiller son appareil macOS avec leurs Apple Watch.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Bloquer la synchronisation du trousseau iCloud** : choisissez **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option (par défaut) **Non configuré** autorise les utilisateurs à synchroniser ces identifiants.
- **Bloquer la synchronisation de documents d’iCloud**: **bloc** empêche la synchronisation des documents et données iCloud. L’option (par défaut) **Non configuré** autorise la synchronisation des documents et des pairs clé-valeur dans votre espace de stockage iCloud.
- **Bloquer le courrier sauvegarde iCloud**: **bloc** empêche la synchronisation à l’application de messagerie macOS iCloud. **Ne pas configuré** (valeur par défaut) autorise la synchronisation de messagerie sur iCloud.
- **Bloquer le Contact sauvegarde iCloud**: **bloc** iCloud empêche de synchroniser les contacts d’appareils. **Ne pas configuré** (valeur par défaut) permet la synchronisation des contacts à l’aide d’iCloud.
- **Bloquer le calendrier sauvegarde iCloud**: **bloc** empêche la synchronisation à l’application de calendrier macOS iCloud. **Ne pas configuré** (valeur par défaut) permet la synchronisation du calendrier sur iCloud.
- **Bloquer le rappel sauvegarde iCloud**: **bloc** empêche la synchronisation à l’application de rappels macOS iCloud. **Ne pas configuré** (valeur par défaut) autorise la synchronisation de rappels sur iCloud.
- **Bloquer le signet sauvegarde iCloud**: **bloc** iCloud empêche de synchroniser les appareils de signets. **Ne pas configuré** (valeur par défaut) autorise la synchronisation de signet sur iCloud.
- **Bloquer les Notes sauvegarde iCloud**: **bloc** iCloud empêche de synchroniser les notes de publication de périphériques. **Ne pas configuré** (valeur par défaut) autorise la synchronisation de Notes sur iCloud.

## <a name="domains"></a>Domains

- **URL de domaine d’e-mail** : ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez configurés, l’e-mail est marqué comme non approuvé dans l’application MacOS Mail.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également limiter les fonctionnalités de l’appareil et les paramètres sur [iOS](device-restrictions-ios.md) appareils.
