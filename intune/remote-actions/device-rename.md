---
title: Renommer un appareil avec Microsoft Intune - Azure | Microsoft Docs
description: Renommez un appareil à l’aide de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11b339a3e94e60db43e8237d9f3d2c729b48a57d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413612"
---
# <a name="rename-a-device-in-intune"></a>Renommer un appareil dans Intune

L’action **Renommer un appareil** vous permet de renommer un appareil inscrit dans Intune. Le nom de l’appareil est modifié dans Intune et sur l’appareil.

Vous pouvez renommer les types d’appareils suivants :
- Windows et appartenant à l’entreprise 
- Mode iOS/iPadOS supervisé
- macOS 10 et appartenant à l’entreprise

Cette fonctionnalité ne prend actuellement pas en charge le renommage des appareils Azure AD Windows hybrides.

## <a name="rename-a-device"></a>Renommer un appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Choisissez **Appareils** > **Tous les appareils** > choisissez un appareil > **Plus** > **Renommer un appareil**.
4. Dans le panneau **Renommer un appareil**, saisissez le nouveau nom dans la zone de texte. Vous pouvez utiliser des lettres, des chiffres et des traits d’union. Le nom doit contenir au moins une lettre ou un trait d’union.
5. Si vous souhaitez redémarrer l’appareil après l’avoir renommé, choisissez **Oui** en regard de **Redémarrer après le renommage**.
6. Choisissez **Renommer**.

## <a name="windows-device-rename-rules"></a>Règles de changement de nom d’appareil Windows
Quand vous renommez un appareil Windows, le nouveau nom doit respecter les règles suivantes :
- 15 caractères ou moins (doit être inférieur ou égal à 63 octets, à l’exclusion de la valeur NULL de fin)
- Valeur non null ou chaîne vide
- Caractères ASCII autorisés : Lettres (a-z, A-Z), chiffres (0-9) et traits d’union
- Caractères Unicode autorisés : caractères >= 0x80, format UTF8 valide, mappage possible à un nom de domaine international (autrement dit, RtlIdnToNameprepUnicode convient ; voir la RFC 3492)
- Les noms ne doivent pas contenir que des chiffres
- Aucun espace dans le nom
- Caractères non autorisés : { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>Étapes suivantes

Pour connaître l’état de l’action d’appareil **Renommer**, consultez la page **Vue d’ensemble** de l’appareil.
