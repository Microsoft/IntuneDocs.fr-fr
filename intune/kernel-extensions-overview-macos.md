---
title: Créer un profil d’appareil d’extensions du noyau macOS avec Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez ou créez un profil d’appareil macOS, puis configurez les extensions du noyau pour autoriser le remplacement de l’utilisateur, ajouter l’identificateur de l’équipe, ainsi qu’un identificateur de groupe et d’équipe dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eca4692189af9272d3d1fc427b4eba638d8b5b27
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882984"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Ajouter des extensions de noyau macOS dans Intune

Sur les appareils macOS, vous pouvez ajouter des fonctionnalités au niveau du noyau. Ces fonctionnalités accèdent à des parties du système d’exploitation auxquelles des programmes normaux ne peuvent pas accéder. Votre organisation peut avoir des besoins ou des exigences spécifiques qui ne sont pas disponibles dans une application, une fonctionnalité d’appareil, etc. 

Pour ajouter des extensions de noyau qui sont toujours autorisées à être chargées sur vos appareils, ajoutez «kernel extensions» (KEXT) dans Microsoft Intune, puis déployez ces extensions sur vos appareils.

Par exemple, vous disposez d’un programme antivirus qui analyse votre appareil à la recherche de contenu malveillant. Vous pouvez ajouter l’extension de noyau de ce programme d’analyse antivirus en tant qu’extension de noyau autorisée dans Intune. Ensuite, affectez l’extension à vos appareils macOS.

Grâce à cette fonctionnalité, les administrateurs peuvent permettre aux utilisateurs de remplacer les extensions de noyau, d’ajouter des identificateurs d’équipe et d’ajouter des extensions de noyau spécifiques dans Intune.

Cette fonctionnalité s’applique à :

- macOS 10.13.2 et versions ultérieures

Pour utiliser cette fonctionnalité, les appareils doivent être:

- Inscrit dans Intune à l’aide de la Programme d’inscription des appareils d’Apple (DEP). [Inscrire automatiquement des appareils MacOS](device-enrollment-program-enroll-macos.md) contient plus d’informations.

  OU

- Inscrit dans Intune avec «inscription approuvée par l’utilisateur» (terme d’Apple). [Préparer les modifications apportées aux extensions du noyau dans MacOS High Sierra](https://support.apple.com/en-us/HT208019) (pour ouvrir le site Web d’Apple), vous avez plus d’informations.

Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités dans un profil, vous pouvez alors envoyer (push) ou déployer le profil aux appareils macOS dans votre organisation.

Cet article explique comment créer un profil de configuration d’appareil à l’aide d’extensions de noyau dans Intune.

> [!TIP]
> Pour plus d’informations sur les extensions de noyau, consultez [vue d’ensemble](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) de l’extension de noyau (ouvre le site Web d’Apple).

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Les extensions de noyau héritées non signées peuvent être ajoutées.
- Veillez à entrer l’identificateur d’équipe et l’ID d’ensemble de l’extension de noyau appropriés. Intune ne valide pas les valeurs que vous entrez. Si vous entrez des informations erronées, l’extension ne fonctionnera pas sur l’appareil.

> [!NOTE]
> Apple a publié des informations sur la signature et la notaire pour tous les logiciels. Sur macOS 10.14.5 et les versions ultérieures, les extensions de noyau déployées via Intune n’ont pas à respecter la stratégie de notaire d’Apple.
>
> Pour plus d’informations sur cette stratégie de notaire, ainsi que sur les mises à jour ou les modifications, consultez les ressources suivantes:
>
> - [L’attribution de notaire à votre application avant la distribution](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (ouvre le site Web d’Apple) 
> - [Préparer les modifications apportées aux extensions du noyau dans MacOS High Sierra](https://support.apple.com/en-us/HT208019) (ouvre le site Web d’Apple)

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : attribuez un nom descriptif au nouveau profil.
    - **Description :** entrez une description pour le profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : sélectionnez **macOS**
    - **Type de profil**: sélectionnez **Extensions**.
    - **Paramètres** : entrez les paramètres à configurer. Pour obtenir la liste de tous les paramètres, ainsi que leur rôle, voir :

        - [MacOS](kernel-extensions-settings-macos.md)

4. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste. [Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).
