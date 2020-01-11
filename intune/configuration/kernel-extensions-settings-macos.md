---
title: paramètres d’extension du noyau macOS dans Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur les appareils macOS pour utiliser des extensions de noyau. Autorisez également les utilisateurs à remplacer les extensions approuvées, à autoriser toutes les extensions d’un identificateur d’équipe ou à autoriser des extensions ou des applications spécifiques dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89f54111258b5e628d9f83c381fde146bf996216
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206327"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>paramètres de l’appareil macOS pour configurer et utiliser des extensions de noyau dans Intune



Cet article répertorie et décrit les différents paramètres d’extension de noyau que vous pouvez contrôler sur les appareils macOS. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour ajouter et gérer des extensions de noyau sur vos appareils.

Pour en savoir plus sur les extensions de noyau dans Intune et sur les conditions préalables requises, consultez [Ajouter des extensions de noyau MacOS](../kernel-extensions-overview-macos.md).

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils macOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’extensions du noyau de l’appareil](../kernel-extensions-overview-macos.md).

> [!NOTE]
> Ces paramètres s’appliquent à différents types d’inscription. Pour plus d’informations sur les différents types d’inscription, consultez [inscription MacOS](../macos-enroll.md).

## <a name="kernel-extensions"></a>Extensions du noyau

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>Les paramètres s’appliquent à : inscription d’appareil automatique approuvée par l’utilisateur

- **Autoriser les remplacements**de l’utilisateur : **autoriser** permet aux utilisateurs d’approuver les extensions du noyau qui ne sont pas incluses dans le profil de configuration. **Non configuré** (par défaut) empêche les utilisateurs d’autoriser les extensions qui ne sont pas incluses dans le profil de configuration. Cela signifie que seules les extensions incluses dans le profil de configuration sont autorisées.

  Pour plus d’informations sur cette fonctionnalité, consultez [chargement d’une extension de noyau approuvée](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) par l’utilisateur (ouvre le site Web d’Apple).

- **Identificateurs d’équipe autorisés**: utilisez ce paramètre pour autoriser un ou plusieurs ID d’équipe. Toutes les extensions de noyau signées avec les ID d’équipe que vous entrez sont autorisées et approuvées. En d’autres termes, utilisez cette option pour autoriser toutes les extensions de noyau au sein du même ID d’équipe, qui peut être un développeur ou un partenaire spécifique.

  **Ajoutez** un identificateur d’équipe des extensions de noyau valides et signées que vous souhaitez charger. Vous pouvez ajouter plusieurs identificateurs d’équipe. L’identificateur d’équipe doit être alphanumérique (lettres et chiffres) et comporter 10 caractères. Par exemple, entrez `ABCDE12345`.

  Une fois que vous avez ajouté un identificateur d’équipe, il peut également être supprimé.

  Pour plus d’informations, [recherchez votre ID d’équipe](https://help.apple.com/developer-account/#/dev55c3c710c) (qui ouvre le site Web d’Apple).

- **Extensions de noyau autorisées**: utilisez ce paramètre pour autoriser des extensions de noyau spécifiques. Seules les extensions de noyau que vous entrez sont autorisées ou approuvées. 

  **Ajoutez** l’identificateur de Bundle et l’identificateur d’équipe d’une extension de noyau que vous souhaitez charger. Pour les extensions de noyau héritées non signées, utilisez un identificateur d’équipe vide. Vous pouvez ajouter plusieurs extensions de noyau. L’identificateur d’équipe doit être alphanumérique (lettres et chiffres) et comporter 10 caractères. Par exemple, entrez `com.contoso.appname.macos` pour **ID d’offre groupée**et `ABCDE12345` pour **identificateur d’équipe**.

  > [!TIP]
  > Pour obtenir l’ID d’ensemble d’une extension de noyau (kext) sur un appareil macOS, vous pouvez :
  >
  > 1. Dans le terminal, exécutez `kextstat | grep -v com.apple`et notez la sortie. Installez le logiciel ou kext souhaité. Réexécutez `kextstat | grep -v com.apple` et recherchez les modifications.
  >
  >    Dans le terminal, `kextstat` répertorie toutes les extensions du noyau sur le système d’exploitation. 
  >
  > 2. Sur l’appareil, ouvrez le fichier de liste de propriétés d’informations (info. plist) pour un kext. L’ID d’offre groupée est affiché. Chaque kext a un fichier info. plist stocké dans. 

> [!NOTE]
> Vous n’êtes pas obligé d’ajouter des identificateurs d’équipe et des extensions de noyau. Vous pouvez configurer l’un ou l’autre.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](../device-profile-assign.md) et [suivre son état](../device-profile-monitor.md).
