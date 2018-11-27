---
title: Données envoyées par Google à Intune
titleSuffix: Microsoft Intune
description: Liste des données que Google envoie à Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a0678e562ab7b63c99f10c455837cf03ee30da21
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52178777"
---
# <a name="data-google-sends-to-intune"></a>Données envoyées par Google à Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quand la gestion des appareils Android Enterprise est activée sur un appareil, Microsoft Intune établit une connexion avec Google, ce qui permet le partage d’informations relatives aux utilisateurs et aux appareils entre Intune et Google. Pour que Microsoft Intune puisse établir une connexion, vous devez créer un compte Google.

Le tableau suivant liste les données que Google envoie à Intune quand la gestion des appareils est activée sur un appareil :


| Données envoyées par Google à Intune | Détails | Rôle | Exemple |
|:---:|:---:|:---:|:---:|
| Données d’entreprise | Identificateurs de l’entreprise du client dans Google. | Permet de lier les informations du client entre Intune et Google. | **enterpriseId**. Exemple : LC04eik8a6.<br>**Nom**. Nom d’administrateur entré durant la configuration d’Android Enterprise. Exemple : Jean Dupont.<br>**E-mail de l’administrateur**. YourAdmin@gmail.com utilisé durant la configuration d’Android Enterprise. |
| Données d’application | Données relatives aux applications gérées du Play Store. | Permet de cibler l’application pour les utilisateurs ou les appareils en tant qu’application disponible ou obligatoire. | **Nom de l’application**. Exemple : Application de gestion des stocks Contoso Warehouse.<br>**Identificateur unique représentant l’application**. Exemple : app:com.Contoso.Warehouse.InventoryTracking |
| Compte de service | Compte de service Google interne unique à utiliser avec des appels clients spécifiques. | Permet d’effectuer des appels dans Google au nom du client (pour afficher des applications, des appareils, etc.) | **Nom**. Exemple : InternalAccount@InternalService.com.<br>**Clés**. Exemple : ServiceAccountPassword |


Pour cesser d’utiliser la gestion des appareils Android Enterprise avec Microsoft Intune et supprimer les données, vous devez à la fois désactiver la gestion des appareils Android Enterprise de Microsoft Intune et supprimer votre compte Google. Reportez-vous au compte Google pour savoir comment effectuer la gestion du compte.


