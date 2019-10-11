---
title: Ajouter des applications système Android Enterprise à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications système Entreprise à Microsoft Intune
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ffc99b34016eba6511f63d1df2184abc3cae858
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725164"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Ajouter des applications système Android Enterprise à Microsoft Intune

Avant d’affecter une application à un appareil ou un groupe d’utilisateurs, vous devez d’abord l’ajouter à Microsoft Intune. Les applications système sont prises en charge sur les appareils Android Entreprise. Vous pouvez activer une application système pour les [appareils Android Enterprise dédiés](../enrollment/android-kiosk-enroll.md) ou les [appareils entièrement gérés](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Ajouter l’application

Vous pouvez ajouter une application système Android Enterprise à Intune à partir du portail Azure en procédant comme suit :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications** > **Ajouter**.
3. Dans le volet **Ajouter une application**, sous les types **Autres** disponibles, sélectionnez **Application système Android Enterprise**.
4. Pour configurer des informations sur l’application, sélectionnez **Configurer**, puis indiquez les informations suivantes :
    - **Nom de l’application** : Entrez le nom de l’application.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.  
    - **Nom du package** : Entrez un nom de paquet. Intune validera le nom du paquet.
5. Sélectionnez **OK**.
6. Sélectionnez **Ajouter**.

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. 

Les applications système Android Enterprise activeront ou désactiveront les applications qui font déjà partie de la plate-forme. Pour activer une application, attribuez à l'application système la valeur **Required (Nécessaire)** . Pour désactiver une application, attribuez à l'application système la valeur **Uninstall (Désinstaller)** . Les applications système ne peuvent pas être assignées comme disponibles pour un utilisateur.

## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)
