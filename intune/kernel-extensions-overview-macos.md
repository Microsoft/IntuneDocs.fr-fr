---
title: Créer de profil de périphérique du noyau extensions macOS avec Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajouter ou créer un macOS profil d’appareil, puis configurer les extensions de noyau pour autoriser le remplacement d’utilisateur, ajouter l’identificateur de l’équipe et un identificateur d’offre groupée et d’équipe dans Microsoft Intune.
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
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403904"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Ajouter des extensions de noyau macOS dans Intune

Sur les appareils macOS, vous pouvez ajouter des fonctionnalités au niveau du noyau. Ces fonctionnalités accéder aux parties du système d’exploitation aux programmes ordinaires ne peut pas accéder. Votre organisation peut avoir des besoins spécifiques ou des spécifications qui ne sont pas disponibles dans une application, une fonctionnalité de l’appareil et ainsi de suite. 

Pour ajouter des extensions de noyau qui sont toujours autorisées à charger sur vos appareils, ajoutez « extensions de noyau » (KEXT) dans Microsoft Intune, puis déployez ces extensions sur vos appareils.

Par exemple, vous avez un programme antivirus qui analyse votre appareil de contenu malveillant. Vous pouvez ajouter cette extension de noyau du programme antivirus comme une extension de noyau autorisées dans Intune. Ensuite, « attribuer » l’extension sur vos appareils macOS.

Avec cette fonctionnalité, les administrateurs peuvent permettre aux utilisateurs de remplacer les extensions de noyau, ajouter des identificateurs de l’équipe et ajouter des extensions de noyau spécifiques dans Intune.

Cette fonctionnalité s’applique à :

- macOS 10.13.2 et versions ultérieures

Pour utiliser cette fonctionnalité, les appareils doivent être :

- Inscrits dans Intune à l’aide Device Enrollment Program (DEP d’Apple). [Inscrire automatiquement des appareils macOS](device-enrollment-program-enroll-macos.md) a plus d’informations.

  OU

- Inscrits dans Intune avec « inscription approuvé par l’utilisateur » (terme d’Apple). [Préparer des modifications aux extensions de noyau dans macOS High Sierra](https://support.apple.com/en-us/HT208019) (ouvre le site web d’Apple) a plus d’informations.

Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités dans un profil, vous pouvez alors envoyer (push) ou déployer le profil aux appareils macOS dans votre organisation.

Cet article vous montre comment créer un profil de configuration d’appareil à l’aide des extensions de noyau dans Intune.

> [!TIP]
> Pour plus d’informations sur les extensions de noyau, consultez [présentation de l’extension du noyau](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (ouvre le site web d’Apple).

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Les extensions de noyau hérité non signés peuvent être ajoutées.
- Veillez à entrer l’identificateur de l’équipe appropriée et de regrouper des ID de l’extension de noyau. Intune ne valide pas les valeurs que vous entrez. Si vous entrez des informations incorrectes, l’extension ne fonctionnera pas sur l’appareil.

> [!NOTE]
> Apple a publié d’informations sur la signature et notarisation pour tous les logiciels. Sur macOS 10.14.5 et versions ultérieur, noyau extensions déployées via Intune n’êtes pas obligé de répondre à la stratégie de notarisation d’Apple.
>
> Pour plus d’informations sur cette stratégie notarisation et les mises à jour ou modifications, consultez les ressources suivantes :
>
>  - [Notarizing votre application avant la distribution](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (ouvre le site web d’Apple) 
>  - [Préparer des modifications aux extensions de noyau dans macOS High Sierra](https://support.apple.com/en-us/HT208019) (ouvre le site web d’Apple)

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
