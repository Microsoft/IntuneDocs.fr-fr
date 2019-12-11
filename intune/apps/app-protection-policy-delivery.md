---
title: Comprendre les délais de distribution des stratégies de protection des applications
titleSuffix: Microsoft Intune
description: Découvrez les différentes fenêtres de déploiement pour les stratégies de protection des applications afin de comprendre quand des modifications doivent apparaître sur l’appareil de l’utilisateur final.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7460d5ccf046b25510d798c3a7ed4aa9ecd87a8a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72499168"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Comprendre les délais de distribution des stratégies de protection des applications

Découvrez les différentes fenêtres de déploiement pour les stratégies de protection des applications afin de comprendre quand des modifications doivent apparaître sur l’appareil de l’utilisateur final.

## <a name="delivery-timing-summary"></a>Résumé des délais de distribution

La distribution des stratégies de protection des applications dépend de l’état de la licence et de l’inscription au service Intune de vos utilisateurs.  

|    État utilisateur    |    Comportement de la protection des applications     |    Intervalle avant nouvelle tentative (voir la Remarque)    |    Pourquoi cela se produit-il ?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Locataire non intégré    |    Attendez le prochain intervalle avant nouvelle tentative.  La protection des applications n’est pas active pour l’utilisateur.    |    24 heures    |    Se produit quand vous n’avez pas configuré votre locataire pour Intune.    |
|    Utilisateur dépourvu de licence     |    Attendez le prochain intervalle avant nouvelle tentative.  La protection des applications n’est pas active pour l’utilisateur.     |    12 heures ; toutefois, sur les appareils Android, cet intervalle requiert le SDK d’application Intune version 5.6.0 ou ultérieure. Sinon, pour les appareils Android, l’intervalle est de 24 heures.   |    Se produit quand vous n’avez pas accordé de licence Intune à l’utilisateur.    |
|    Utilisateur dépourvu de stratégies de protection des applications    |    Attendez le prochain intervalle avant nouvelle tentative.  La protection des applications n’est pas active pour l’utilisateur.    |    12 heures        |    Se produit quand vous n’avez pas attribué de paramètres de stratégie de protection des applications à l’utilisateur.    |
|    Utilisateur inscrit avec succès pour MAM Intune    |    La protection des applications est appliquée en fonction des paramètres de stratégie.    Les mises à jour se produisent en fonction de l’intervalle avant nouvelle tentative    |    Service Intune défini en fonction de la charge utilisateur.    En règle générale, 30 minutes.     |    Se produit quand l’utilisateur a été correctement inscrit auprès du service Intune pour la configuration de la gestion des applications mobiles.    |

> [!NOTE]
> Les intervalles avant nouvelle tentative peuvent exiger que se produise une utilisation active de l’application, ce qui signifie que l’application est lancée et en cours d’utilisation.  Si l’intervalle avant nouvelle tentative est de 24 heures et que l’utilisateur patiente 48 heures avant de lancer l’application, la nouvelle tentative du client de la protection des applications intervient au bout de 48 heures.

## <a name="handling-network-connectivity-issues"></a>Gestion des problèmes de connectivité réseau

Quand l’inscription de l’utilisateur échoue en raison de problèmes de connectivité réseau, un intervalle avant nouvelle tentative accéléré est utilisé.  Le client de la protection des applications effectue des tentatives à des intervalles de plus en plus long jusqu’à ce que l’intervalle atteigne 60 minutes ou qu’une connexion soit établie.  Le client effectue ensuite une tentative toutes les 60 minutes jusqu’à ce qu’une connexion soit établie. Ensuite, le client retourne à l’intervalle entre nouvelle tentative standard en fonction de l’état utilisateur.

## <a name="next-steps"></a>Étapes suivantes

[Affecter des licences aux utilisateurs pour qu’ils puissent inscrire des appareils dans Intune](../fundamentals/licenses-assign.md)

