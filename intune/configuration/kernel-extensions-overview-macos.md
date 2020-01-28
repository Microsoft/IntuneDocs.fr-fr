---
title: Créer un profil d’appareil d’extensions de noyau macOS avec Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez ou créez un profil d’appareil macOS, puis configurez les extensions de noyau pour autoriser le remplacement utilisateur, ajouter un identificateur d’équipe et un identificateur de bundle dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1075054f3812e8c40f38e705a440c46ba09fdd0e
ms.sourcegitcommit: 11cbd2a9d90dea20f6dc1f54f0a6acbeec3a71d6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146767"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Ajouter des extensions de noyau macOS dans Intune

Sur les appareils macOS, vous pouvez ajouter des fonctionnalités au niveau du noyau. Ces fonctionnalités accèdent à des parties du système d’exploitation auxquelles des programmes ordinaires ne peuvent pas accéder. Votre organisation peut avoir des besoins ou des exigences spécifiques qui ne sont pas disponibles dans une application, une fonctionnalité d’appareil, etc. 

Pour ajouter des extensions de noyau qui sont toujours autorisées à être chargées sur vos appareils, ajoutez « kernel extensions » (KEXT) dans Microsoft Intune, puis déployez ces extensions sur vos appareils.

Par exemple, vous disposez d’un programme de détection des virus qui analyse votre appareil à la recherche de contenu malveillant. Vous pouvez ajouter l’extension de noyau de ce programme de détection des virus en tant qu’extension de noyau autorisée dans Intune. Ensuite, affectez l’extension à vos appareils macOS.

Avec cette fonctionnalité, les administrateurs peuvent permettre aux utilisateurs de remplacer les extensions de noyau et d’ajouter des identificateurs d’équipe ainsi que des extensions de noyau spécifiques dans Intune.

Cette fonctionnalité s’applique à :

- macOS 10.13.2 et versions ultérieures

Pour utiliser cette fonctionnalité, les appareils doivent être :

- Inscrits à Intune via le Programme d’inscription des appareils (DEP) d’Apple. [Inscrire automatiquement des appareils macOS](../enrollment/device-enrollment-program-enroll-macos.md) contient plus d’informations.

  OU

- Inscrits à Intune avec « inscription approuvée par l’utilisateur » (terme d’Apple). [Préparation aux modifications apportées aux extensions de noyau sous macOS High Sierra](https://support.apple.com/en-us/HT208019) (ouvre le site web d’Apple) contient plus d’informations.

Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités dans un profil, vous pouvez alors envoyer (push) ou déployer le profil aux appareils macOS dans votre organisation.

Cet article explique comment créer un profil de configuration d’appareil à l’aide d’extensions de noyau dans Intune.

> [!TIP]
> Pour plus d’informations sur les extensions de noyau, consultez la [vue d’ensemble des extensions de noyau](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (ouvre le site web d’Apple).

## <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Des extensions de noyau héritées non signées peuvent être ajoutées.
- Veillez à entrer l’identificateur d’équipe et l’ID de bundle appropriés de l’extension de noyau. Intune ne valide pas les valeurs que vous entrez. Si vous entrez des informations erronées, l’extension ne fonctionnera pas sur l’appareil. Un identificateur d’équipe comporte exactement 10 caractères alphanumériques. 

> [!NOTE]
> Apple a publié des informations concernant la signature et la notarisation pour tous les logiciels. Sur macOS 10.14.5 et ultérieur, les extensions de noyau déployées via Intune n’ont pas à respecter la stratégie de notarisation d’Apple.
>
> Pour plus d’informations sur cette stratégie de notarisation, ainsi que sur les mises à jour ou les modifications, consultez les ressources suivantes :
>
> - [Notarizing your app before distribution](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (ouvre le site web d’Apple) 
> - [Préparation aux modifications apportées aux extensions de noyau sous macOS High Sierra](https://support.apple.com/en-us/HT208019) (ouvre le site web d’Apple)

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **macOS**
    - **Type de profil** : Sélectionnez **Extensions**.
    - **Paramètres** : Entrez les paramètres à configurer. Pour obtenir la liste de tous les paramètres, ainsi que leur rôle, voir :

        - [MacOS](kernel-extensions-settings-macos.md)

4. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste. [Affectez-le](../device-profile-assign.md) et [supervisez son état](../device-profile-monitor.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois créé, le profil est prêt à être affecté. Vous devez à présent [affecter le profil](../device-profile-assign.md) et [superviser son état](../device-profile-monitor.md).
