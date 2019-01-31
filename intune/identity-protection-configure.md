---
title: Utiliser un code confidentiel pour se connecter à des appareils Windows 10 avec Microsoft Intune – Azure | Microsoft Docs
description: Utilisez Windows Hello Entreprise pour permettre aux utilisateurs de se connecter aux appareils à l’aide d’un code confidentiel, d’une empreinte digitale et plus encore. Créez un profil de configuration de la protection des identités dans Intune pour les appareils Windows 10 avec ces paramètres, et affectez-le à des groupes d’utilisateurs et d’appareils.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 843806681fcee4ddec175207c2c49d6db95e0f0d
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831379"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Utiliser Windows Hello Entreprise sur des appareils Windows 10 avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows Hello Entreprise est une méthode de connexion aux appareils Windows qui remplace les mots de passe, les cartes à puce et les cartes à puce virtuelles. Intune comporte des paramètres prédéfinis permettant aux administrateurs de configurer et d’utiliser Windows Hello Entreprise. Par exemple, vous pouvez les utiliser pour :

- activer Windows Hello Entreprise pour les appareils et les utilisateurs ;
- définir les critères de code confidentiel des appareils (par exemple, longueur minimale ou maximale) ;
- autoriser ou empêcher l’utilisation de gestes (par exemple, les empreintes digitales) pour se connecter aux appareils.

Cette fonctionnalité s’applique aux appareils qui exécutent :

- Windows 10 et versions ultérieures
- Windows 10 Mobile
- Windows Holographic for Business

Intune utilise des « profils de configuration » pour créer et personnaliser ces paramètres selon les besoins de votre organisation. Après avoir ajouté ces fonctionnalités à un profil, envoyez (push) ou déployez ces paramètres auprès des différents groupes d’utilisateurs et d’appareils de votre organisation.

Cet article explique comment créer un profil de configuration d’appareil. Pour connaître la liste de tous les paramètres, ainsi que leur rôle, voir [Paramètres des appareils Windows 10 permettant d’activer Windows Hello Entreprise](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Créer le profil d’appareil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**. Windows Hello entreprise est uniquement pris en charge sur les appareils qui exécutent Windows 10 et versions ultérieures.
    - **Type de profil** : sélectionnez **Protection des identités**.
    - **Configurer Windows Hello Entreprise** : choisissez la configuration de Windows Hello Entreprise. Les options disponibles sont les suivantes :

        - **Non configuré** : [approvisionne Windows Hello Entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) sur l’appareil. Lorsque vous affectez des profils Identity Protection uniquement à des utilisateurs, le contexte d’appareil est défini par défaut sur **Non configuré**
        - **Désactivé** : si vous ne souhaitez pas utiliser Windows Hello Entreprise, sélectionnez cette option. Elle désactive Windows Hello Entreprise pour tous les utilisateurs.
        - **Activé** : choisissez cette option pour [approvisionner]((https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)) et configurer les paramètres Windows Hello Entreprise dans Intune. Entrez les paramètres à configurer. Pour obtenir la liste de tous les paramètres, ainsi que leur rôle, voir :

            - [Paramètres des appareils Windows 10 permettant d’activer Windows Hello Entreprise](identity-protection-windows-settings.md)

4. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Le profil est créé et apparaît dans la liste des profils. Maintenant, [affectez-le à des groupes](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->

## <a name="next-steps"></a>Étapes suivantes

- Voir la liste de tous [les paramètres, ainsi que leur rôle](identity-protection-windows-settings.md).
- [Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).