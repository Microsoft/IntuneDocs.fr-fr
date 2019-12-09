---
title: Ajouter des applications système Android Enterprise à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications système Entreprise à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d45455a97f8016527dce49839b5493f16b173d43
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563660"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Ajouter des applications système Android Enterprise à Microsoft Intune

Avant d’affecter une application à un appareil ou un groupe d’utilisateurs, vous devez d’abord l’ajouter à Microsoft Intune. Les applications système sont prises en charge sur les appareils Android Entreprise. Vous pouvez activer une application système pour les [appareils Android Enterprise dédiés](../enrollment/android-kiosk-enroll.md) ou les [appareils entièrement gérés](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Ajouter l’application

Vous pouvez ajouter une application système Android Enterprise à Intune à partir du portail Azure en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Ajouter une application**, sous les types **Autres** disponibles, sélectionnez **Application système Android Enterprise**.
4. Pour configurer des informations sur l’application, sélectionnez **Configurer**, puis indiquez les informations suivantes :
    - **Nom de l’application** : Entrez le nom de l’application.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.  
    - **Nom du package** : Entrez un nom de paquet. Intune validera le nom du paquet.
5. Sélectionnez **OK**.
6. Sélectionnez **Ajouter**.

> [!NOTE]
> Vous devrez travailler avec l’OEM de votre appareil pour trouver le nom du package de l’application que vous souhaitez activer ou désactiver.

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. 

Les applications système Android Enterprise activeront ou désactiveront les applications qui font déjà partie de la plate-forme. Pour activer une application, attribuez à l'application système la valeur **Required (Nécessaire)** . Pour désactiver une application, attribuez à l'application système la valeur **Uninstall (Désinstaller)** . Les applications système ne peuvent pas être assignées comme disponibles pour un utilisateur.


## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)
