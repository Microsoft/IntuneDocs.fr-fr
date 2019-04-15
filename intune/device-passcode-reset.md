---
title: Réinitialiser des codes secrets de l’appareil avec Microsoft Intune - Azure | Microsoft Docs
description: Supprimez ou réinitialisez le code secret à l’aide de l’action de suppression de code secret sur les appareils que vous gérez ou analysez avec Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7a2b39307f97fa6839095b2595f36a7f554dc35
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389106"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Réinitialiser ou supprimer un code secret de l’appareil dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Ce document décrit à la fois la réinitialisation du code secret au niveau de l’appareil et la réinitialisation du code secret du profil professionnel sur les appareils Android Entreprise (anciennement Android for Work ou AfW). Il est important de noter cette distinction, car les exigences varient selon le cas. Une réinitialisation du code secret au niveau de l’appareil entraîne une réinitialisation du code secret pour l’intégralité de l’appareil. La réinitialisation du code secret du profil professionnel entraîne une réinitialisation du code secret uniquement pour le profil professionnel de l’utilisateur sur les appareils Android Entreprise.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Plateformes prises en charge pour la réinitialisation du code secret au niveau de l’appareil

| Plate-forme | Pris en charge ? |
| ---- | ---- |
| Appareils Android version 6.x ou antérieure | Oui |
| Appareils Android Entreprise en mode plein écran | Oui |
| Périphériques iOS | Oui |
| Appareils Android inscrits avec un profil professionnel, version 7.0 et antérieure | Non |
| Appareils Android version 7.0 ou supérieure | Non |
| macOS | Non |
| Windows | Non |

Pour les appareils Android, cela signifie effectivement que la réinitialisation du code secret au niveau de l’appareil est prise en charge uniquement sur les appareils exécutant la version 6.x ou antérieure, ou sur les appareils Android Entreprise en mode plein écran. En effet, Google a supprimé la prise en charge de la réinitialisation du code secret/mot de passe d’un appareil Android 7 à partir d’une application disposant de droits d’administrateur d’appareils. Cela s’applique à tous les fournisseurs MDM.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Plateformes prises en charge pour la réinitialisation du code secret du profil professionnel d’un appareil Android Entreprise

| Plate-forme | Pris en charge ? |
| ---- | ---- |
| Appareils Android Entreprise inscrits avec un profil professionnel et exécutant les versions 8.0 et ultérieures | Oui |
| Appareils Android Entreprise inscrits avec un profil professionnel et exécutant les versions 7.x et antérieures | Non |
| Appareils Android exécutant les versions 7.x et antérieures | Non |
| iOS | Non |
| macOS | Non |

Pour créer un code secret de profil professionnel, utilisez l’action Réinitialiser le code secret. Cette action entraîne une réinitialisation du code secret et la création d’un code secret temporaire pour le profil professionnel uniquement. 

## <a name="reset-a-passcode"></a>Réinitialiser un code secret


1. Connectez-vous au [Portail Azure](https://portal.azure.com) avec l’un des rôles suivants : administrateur général Azure Active Directory, administrateur du service Intune Azure Active Directory, support technique ou administrateur de rôle. Pour obtenir la liste complète des rôles et des autorisations, consultez le [tableau des RBAC Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Appareils**, puis **Tous les appareils**.
4. Dans la liste des appareils que vous gérez, sélectionnez un appareil et choisissez **... Plus**. Ensuite, choisissez l’action à distance **Supprimer le code secret**.

## <a name="reset-android-work-profile-passcodes"></a>Réinitialiser les codes secrets des profils professionnels Android

Les appareils Android Entreprise pris en charge et inscrits avec un profil professionnel reçoivent un nouveau mot de passe de déverrouillage de profil géré, ou sont soumis à une vérification du profil géré pour l’utilisateur final.

Pour les appareils Android Entreprise exécutant la version 8.x ou ultérieure, et inscrits avec un profil professionnel, les utilisateurs finaux reçoivent une notification les invitant à activer leur code secret de réinitialisation une fois l’inscription effectuée. La notification s’affiche si un mot de passe de profil professionnel est imposé et défini. Une fois le code secret entré, la notification disparaît.


## <a name="remove-ios-passcodes"></a>Supprimer les codes secrets iOS

Au lieu d’être réinitialisés, les codes secrets sont supprimés des appareils iOS. Si une stratégie de conformité relative au code secret est définie, l’appareil invite l’utilisateur à définir un nouveau mot de passe dans les paramètres.

## <a name="next-steps"></a>Étapes suivantes

Pour afficher l’état de l’action que vous venez d’effectuer, dans **Appareils**, sélectionnez **Actions d’appareil**.
