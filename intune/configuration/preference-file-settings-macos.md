---
title: Ajouter des paramètres de fichier de préférences aux appareils macOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez un fichier XML ou plist qui contient des informations clés sur votre application. Utilisez un fichier de préférences profil de configuration d’appareil pour modifier les informations de clé dans le fichier de liste de propriétés et l’affecter à vos appareils macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ed04c1bf135793da9cece9debc2c7cdd481601a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74691689"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Ajouter un fichier de liste de propriétés aux appareils macOS à l’aide de Microsoft Intune

À l’aide de Microsoft Intune, vous pouvez ajouter un fichier de liste de propriétés (. plist) pour les appareils macOS ou les applications sur les appareils macOS.

Cette fonctionnalité s’applique à :

- Appareils macOS exécutant la version 10.7 ou une version ultérieure

Les fichiers de liste de propriétés incluent généralement des informations sur les applications macOS. Pour plus d’informations, consultez [à propos des informations sur les fichiers de liste de propriétés](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (site Web d’Apple) et paramètres de [charge utile personnalisés](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

Cet article répertorie et décrit les différents paramètres de fichier de liste de propriétés que vous pouvez ajouter aux appareils macOS. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour ajouter l’ID d’ensemble d’applications (`com.company.application`) et ajoutez son fichier. plist.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils macOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez le profil](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Ces paramètres ne sont pas validés. Veillez à tester vos modifications avant d’attribuer le profil à vos appareils.
- Si vous ne savez pas comment entrer une clé d’application, modifiez le paramètre dans l’application. Ensuite, examinez le fichier de préférences de l’application à l’aide de [Xcode](https://developer.apple.com/xcode/) pour voir comment le paramètre est configuré. Apple recommande de supprimer les paramètres non gérables à l’aide de Xcode avant d’importer le fichier.
- Seules certaines applications fonctionnent avec des préférences gérées et peuvent ne pas vous permettre de gérer tous les paramètres.
- Veillez à charger les fichiers de liste de propriétés qui ciblent les paramètres de canal d’appareil, et non les paramètres de canal utilisateur. Les fichiers de liste de propriétés ciblent la totalité du périphérique.

## <a name="preference-file"></a>Fichier de préférences

- **Nom de domaine de préférence**: les fichiers de liste de propriétés sont généralement utilisés pour les navigateurs Web (Microsoft Edge), [Microsoft Defender-protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)et les applications personnalisées. Lorsque vous créez un domaine de préférence, un ID de Bundle est également créé. Entrez l’ID de Bundle, par exemple `com.company.application`. Par exemple, entrez `com.Contoso.applicationName`, `com.Microsoft.Edge` ou `com.microsoft.wdav`.
- **Fichier de liste de propriétés**: sélectionnez le fichier de liste de propriétés associé à votre application. Assurez-vous qu’il s’agit d’un fichier `.plist` ou `.xml`. Par exemple, téléchargez un fichier `YourApp-Manifest.plist` ou `YourApp-Manifest.xml`.
- **Contenu du fichier**: les informations de clé du fichier de liste de propriétés sont affichées. Si vous avez besoin de modifier les informations de clé, ouvrez le fichier de liste dans un autre éditeur, puis rechargez le fichier dans Intune.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et affiché dans la liste des profils.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Pour plus d’informations sur les fichiers de préférences pour Microsoft Edge, consultez [configurer les paramètres de stratégie Microsoft Edge sur MacOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
