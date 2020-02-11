---
title: Ajouter des applications système Android Enterprise à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter des applications système Entreprise à Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755253"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Ajouter des applications système Android Enterprise à Microsoft Intune

Avant d’affecter une application à un appareil ou un groupe d’utilisateurs, vous devez d’abord l’ajouter à Microsoft Intune. Les applications système sont prises en charge sur les appareils Android Entreprise. Vous pouvez activer une application système pour les [appareils Android Enterprise dédiés](../enrollment/android-kiosk-enroll.md) ou les [appareils entièrement gérés](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Ajouter l’application

Vous pouvez ajouter une application système Android Enterprise à Intune à partir du portail Azure en procédant comme suit :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans le volet **Sélectionner le type d’application**, sous les types **Autres** disponibles, sélectionnez **Application système Android Enterprise**.
4. Cliquez sur **Sélectionner**. Les étapes **Ajouter une application** sont affichées.
Dans la page **Informations sur l'application**, ajoutez les détails de l'application :
    - **Nom de l’application** : Entrez le nom de l’application.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.  
    - **Nom du package** : Entrez un nom de paquet. Intune validera le nom du paquet.
5. Cliquez sur **Suivant** pour afficher la page **Balises d’étendue**.
8. Cliquez sur **Sélectionner des balises d’étendue** pour ajouter éventuellement des balises d’étendue pour l'application. Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée](~/fundamentals/scope-tags.md).
9. Cliquez sur **Suivant** pour afficher la page **Affectations**.
10. Sélectionnez les affectations de groupe pour l'application. Pour plus d’informations, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils](~/fundamentals/groups-add.md). 
11. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**. Vérifiez les valeurs et les paramètres que vous avez saisis pour l'application.
12. Lorsque vous avez terminé, cliquez sur **Créer** pour ajouter l'application à Intune.

Le volet **Vue d’ensemble** de l'application que vous avez créée s'affiche.

> [!NOTE]
> Vous devrez travailler avec l’OEM de votre appareil pour trouver le nom du package de l’application que vous souhaitez activer ou désactiver.

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. 

Les applications système Android Enterprise activeront ou désactiveront les applications qui font déjà partie de la plate-forme. Pour activer une application, attribuez à l'application système la valeur **Required (Nécessaire)** . Pour désactiver une application, attribuez à l'application système la valeur **Uninstall (Désinstaller)** . Les applications système ne peuvent pas être assignées comme disponibles pour un utilisateur.


## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)
