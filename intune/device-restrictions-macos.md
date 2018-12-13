---
title: Paramètres de restriction d’appareil Microsoft Intune pour macOS
titlesuffix: ''
description: Découvrez les paramètres Intune qui vous permettent de contrôler les paramètres et les fonctionnalités des appareils exécutant macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0a2a096bfb4b5fafd895425a775abc13afc643e2
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728534"
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Paramètres de restriction d’appareil macOS dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article décrit les paramètres de restriction d’appareil de Microsoft Intune que vous pouvez configurer pour les appareils exécutant macOS.

## <a name="password"></a>Mot de passe
- **Mot de passe** - Demande à l’utilisateur final d’entrer un mot de passe pour accéder à l’appareil.
  - **Type de mot de passe requis** - Indique si le mot de passe peut être uniquement de nature numérique ou s’il doit être alphanumérique (c’est-à-dire, contenir des lettres et des chiffres). Ce paramètre est uniquement pris en charge sur les systèmes Mac OS X 10.10.3 et les versions ultérieures.
  - **Nombre de caractères non alphanumériques dans le mot de passe** : spécifie le nombre de caractères complexes requis dans le mot de passe (**0** à **4**).<br>Un caractère complexe est un symbole, par exemple, « **?** ».
  - **Longueur minimale du mot de passe** - Entrez la longueur minimale du mot de passe qu’un utilisateur doit configurer (entre **4** et **16** caractères).
  - **Mots de passe simples** - Permet d’utiliser des mots de passe simples, tels que **0000** ou **1234**.
  - **Nombre maximal de minutes entre le verrouillage de l'écran et la demande du mot de passe** - Indique la durée pendant laquelle l’ordinateur doit être inactif avant qu’un mot de passe soit requis pour le déverrouiller.
  - **Nombre de minutes d'inactivité avant le verrouillage de l'appareil** - Indique la durée pendant laquelle l’ordinateur doit être inactif avant le verrouillage de l’écran.
  - **Expiration du mot de passe (jours)** - Spécifie le nombre de jours qui s’écoule avant que l’utilisateur ne doive changer le mot de passe (entre **1** et **255** jours).
  - **Empêcher la réutilisation des mots de passe précédents** - Spécifie le nombre de mots de passe précédents qui ne peuvent pas être réutilisés (**1** à **24**).

- **Bloquer le remplissage automatique des mots de passe** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sous macOS. L’option **Bloquer** a également les conséquences suivantes :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option **Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mots de passe de proximité** : choisissez **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils situés à proximité. L’option **Non configuré** autorise ces demandes de mots de passe.

- **Bloquer le partage de mots de passe** : choisissez **Bloquer** pour empêcher le partage de mots de passe entre les appareils avec AirDrop. L’option **Non configuré** autorise le partage de mots de passe.


## <a name="restricted-apps"></a>Applications restreintes

Dans la liste des applications restreintes, vous pouvez configurer une des listes suivantes :

- Une liste **Applications interdites** : répertorie les applications qui ne sont pas gérées par Intune et que les utilisateurs ne sont pas autorisés à installer et à exécuter. Rien n’empêche les utilisateurs d’installer une application interdite, mais, s’ils le font, vous en êtes informé.
- Une liste **Applications approuvées** : répertorie les applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Rien n’empêche les utilisateurs d’installer une application qui ne figure pas dans la liste approuvée, mais, s’ils le font, vous en êtes informé.

Pour configurer la liste, cliquez sur **Ajouter**, puis spécifiez un nom de votre choix, éventuellement l'éditeur de l'application et l’ID d’ensemble de l'application (par exemple *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domaines d’e-mail non marqués

Dans le champ **URL de domaine d’e-mail**, ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez configurés, l’e-mail est marqué comme non approuvé dans l’application MacOS Mail.

