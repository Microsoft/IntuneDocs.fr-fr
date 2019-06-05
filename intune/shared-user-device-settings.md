---
title: Paramètres d’appareils multi-utilisateurs ou partagés dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez et utilisez des appareils Windows 10 et Windows Holographic for Business qui sont partagés, ou utilisés par plusieurs utilisateurs dans Microsoft Intune. Découvrez la liste de tous les paramètres, et ce qu’ils font sur les appareils, notamment Microsoft HoloLens. Contrôlez les comptes invités, gérez les comptes et supprimez les comptes inactifs, autorisez ou empêchez l’enregistrement dans le stockage local, définissez les options d’alimentation et de mise en veille, choisissez quand les mises à jour sont installées, et utilisez des appareils dans des environnements de formation dans un profil de configuration d’appareil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc1fca439f0edf4a5d4caaad4ff4f9e0bae5972b
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374048"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Contrôler l’accès, les comptes et les fonctionnalités d’alimentation sur des PC partagés ou des appareils multi-utilisateurs à l’aide d’Intune

Les appareils ayant plusieurs utilisateurs sont appelés « appareils partagés », et ils font partie des solutions de gestion des appareils mobiles (MDM). À l’aide de Microsoft Intune, vous pouvez personnaliser les appareils partagés exécutant les plateformes suivantes :

- Windows 10 Professionnel et version ultérieure
- Windows 10 Entreprise et version ultérieure
- Windows Holographic for Business, notamment HoloLens

Par exemple, les écoles disposent d’appareils qui sont généralement utilisés par de nombreux étudiants. Avec ce paramètre, l’administrateur Intune scolaire peut activer la fonctionnalité de PC partagé pour autoriser un utilisateur à la fois. Les étudiants ne peuvent pas basculer entre différents comptes connectés sur l’appareil. Quand l’étudiant se déconnecte, vous choisissez également de supprimer tous les paramètres spécifiques à l’utilisateur.

Les utilisateurs finaux peuvent se connecter à ces appareils partagés avec un compte invité. Une fois que les utilisateurs sont connectés, les informations d’identification sont mises en cache. Durant leur utilisation de l’appareil, ils ne peuvent accéder qu’aux fonctionnalités que vous autorisez. Par exemple, vous choisissez le moment où l’appareil passe en mode veille, si les utilisateurs peuvent voir et enregistrer les fichiers localement, ou bien activer ou désactiver les paramètres de gestion de l’alimentation, et bien plus encore. Vous décidez également si le compte invité est supprimé quand l’utilisateur se déconnecte ou s’il convient de supprimer les comptes inactifs lorsqu’un seuil est atteint.

Cet article vous montre comment créer un profil de configuration et inclut des liens vers les paramètres disponibles avec leurs descriptions.

Quand le profil est créé dans Intune, vous le déployez ou l’affectez à des groupes d’appareils dans votre organisation. Vous pouvez également affecter ce profil à des groupes d’appareils contenant différentes combinaisons de types d’appareils et de versions de système d’exploitation.

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

   - **Nom** : Entrez un nom descriptif pour le nouveau profil.
   - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
   - **Type de profil** : Sélectionnez **Appareil multi-utilisateur partagé**.

4. Configurez les paramètres pour [Windows 10 et ultérieur](shared-user-device-settings-windows.md) ou [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).

5. Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Votre profil est créé et affiché dans la liste, mais il ne fait rien pour le moment. Veillez à [affecter le profil](device-profile-assign.md) à des groupes d’appareils dans votre organisation.

## <a name="next-steps"></a>Étapes suivantes

- Consultez tous les paramètres pour [Windows 10 et version ultérieure](shared-user-device-settings-windows.md) et [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
- [Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
