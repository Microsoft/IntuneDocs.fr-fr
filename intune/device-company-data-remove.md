---
title: "Supprimer les données d’entreprise d’appareils avec Intune"
titleSuffix: Intune on Azure
description: "Apprenez à supprimer uniquement les données d’entreprise des appareils que vous gérez avec Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8074d6e7cc0a061a6708f8c8bfae1a4dfcb6daa3
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Supprimer les données d’entreprise des appareils gérés par Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L’action d’appareil **Supprimer les données d’entreprise** supprime uniquement les données d’entreprise des appareils gérés par Intune. L’action ne supprime pas les données personnelles de l’appareil. Après la suppression, l’appareil n’est plus géré par Intune et ne peut plus accéder aux ressources d’entreprise.

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows - Prise en charge (les appareils Windows joints à Azure Active Directory ne sont pas pris en charge)
- Windows Phone - Prise en charge
- iOS - Prise en charge
- macOS - Prise en charge
- Android - Prise en charge

## <a name="how-to-remove-company-data"></a>Comment supprimer des données d’entreprise

1. Connectez-vous au portail Azure.
2. Choisissez **Autres services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Appareils**.
4. Dans le panneau **Appareils et groupes**, choisissez **Tous les appareils**.
5. Dans la liste des appareils que vous gérez, choisissez un appareil, puis choisissez l’action à distance d’appareil **Supprimer les données d’entreprise**.

## <a name="next-steps"></a>Étapes suivantes

Pour connaître l’état de l’action que vous venez d’effectuer, allez dans le panneau **Appareils et groupes**, et choisissez **Actions d’appareil**.
