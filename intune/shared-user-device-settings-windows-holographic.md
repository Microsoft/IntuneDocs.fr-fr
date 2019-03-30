---
title: Paramètres des appareils partagés Windows Holographic for Business - Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez et utilisez des appareils Windows Holographic for Business qui sont partagés, ou utilisés par plusieurs utilisateurs dans Microsoft Intune. Découvrez la liste de tous les paramètres de gestion des comptes, et ce qu’ils font sur les appareils, notamment Microsoft HoloLens.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 151ceaa40f2993d3160b9de34eee92e53c35925d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565857"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Paramètres Windows Holographic for Business pour gérer les appareils partagés à l’aide d’Intune

Les appareils Windows Holographic for Business, tels que Microsoft HoloLens, peuvent être utilisés par plusieurs utilisateurs. Les appareils ayant plusieurs utilisateurs sont appelés « appareils partagés », et ils font partie des solutions de gestion des appareils mobiles (MDM).

À l’aide de Microsoft Intune, les utilisateurs peuvent se connecter à ces appareils partagés avec un compte invité. Durant leur utilisation de l’appareil, ils ne peuvent accéder qu’aux fonctionnalités que vous autorisez.

Cet article liste et décrit les paramètres que vous utilisez dans un profil de configuration d’appareil Windows Holographic for Business (et versions ultérieures). Quand le profil est créé dans Intune, vous pouvez le déployer ou l’affecter à des groupes d’appareils dans votre organisation. Vous pouvez également affecter ce profil à un groupe d’appareils contenant différentes combinaisons de types d’appareils et de versions de système d’exploitation.

Pour plus d’informations sur cette fonctionnalité dans Intune, consultez [Contrôler l’accès, les comptes et les fonctionnalités d’alimentation sur des PC partagés ou des appareils à utilisateurs multiples](shared-user-device-settings.md). Pour plus d’informations sur le fournisseur de services de configuration Windows, consultez [AccountManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp).

## <a name="before-your-begin"></a>Avant de commencer

[Créez le profil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Paramètres d’appareils partagés par plusieurs utilisateurs

> [!NOTE]
> Les appareils qui exécutent Windows Holographic for Business, y compris Microsoft HoloLens, prennent uniquement en charge les paramètres de **gestion des comptes**. Si vous configurez d’autres paramètres Intune, y compris le **mode PC partagé**, cela n’aura aucun impact sur ces appareils.

- **Gestion du compte** : affectez la valeur **Activer** pour supprimer automatiquement les comptes locaux créés par des invités et les comptes dans AD et Azure Active Directory. Quand un utilisateur se déconnecte de l’appareil, ou lors de l’exécution de la maintenance du système, ces comptes sont supprimés. Quand cette option est activée, définissez également :
  - **Suppression du compte**: choisissez lors de la suppression des comptes : **au seuil d’espace de stockage**, **au seuil d’espace de stockage et de seuil inactive**, ou **immédiatement après la déconnexion** . Entrez également :
    - **Commencez par supprimer les threshold(%)**: entrez un pourcentage (0-100) d’espace disque. Quand l’espace de stockage/disque total est inférieur à la valeur entrée, les comptes mis en cache sont supprimés. Les comptes sont supprimés de manière continue afin de récupérer l’espace disque. Les comptes inactifs depuis le plus longtemps sont supprimés en premier.
    - **Arrêter la suppression threshold(%)**: entrez un pourcentage (0-100) d’espace disque. Quand l’espace de stockage/disque total atteint la valeur entrée, la suppression cesse.

  Affectez la valeur **Désactiver** pour conserver les comptes locaux, AD et Azure AD créés par des invités.

  > [!NOTE]
  > Les appareils Microsoft HoloLens prennent uniquement en charge les paramètres de **gestion des comptes**.

## <a name="next-steps"></a>Étapes suivantes

- [Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
- Découvrez les paramètres de [Windows 10 et des versions ultérieures](shared-user-device-settings-windows.md).
