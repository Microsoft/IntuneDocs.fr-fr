---
title: Quelles informations votre entreprise peut-elle voir quand vous inscrivez votre appareil ?
description: Explique ce que le service informatique peut et ne peut pas voir sur votre appareil géré.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.openlocfilehash: 63295d7e05889f5a8beb44e399f36a4fbe27544d
ms.sourcegitcommit: 76c7b315b83eb6cb5b996facf1d250fb3e22f1bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51276113"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Quelles informations mon organisation peut-elle voir quand j’inscris mon appareil ?

Votre organisation ne peut pas voir vos informations personnelles quand vous inscrivez un appareil dans Microsoft Intune. Quand vous inscrivez un appareil, vous autorisez votre organisation à voir certaines informations relatives à votre appareil, comme son modèle et son numéro de série. Votre organisation utilise ces informations pour protéger ses données qui sont stockées sur l’appareil.

**Ce que votre organisation ne peut jamais voir :**

- Historique des appels et de navigation
- E-mails et SMS
- Contacts
- Calendrier
-   Mots de passe
- Photos, notamment celles qui se trouvent dans l’application de photos ou sur la pellicule
- Fichiers

**Ce que votre organisation peut toujours voir :**

- Modèle d’appareil, par exemple Google Pixel
- Fabricant de l’appareil, par exemple Microsoft
- Système d’exploitation et sa version, par exemple iOS 12.0.1
- Noms des applications, tels que Microsoft Word : sur les appareils personnels, votre organisation peut uniquement voir la liste de vos applications gérées. Sur les appareils de l’entreprise, elle peut voir la liste de toutes vos applications.
- Propriétaire de l’appareil
- Nom de l'appareil
- Numéro de série de l’appareil
- IMEI

**Ce que votre organisation est susceptible de voir :**

-  Numéro de téléphone : pour les appareils appartenant à l’**entreprise**, votre numéro de téléphone complet peut être vu. Pour les appareils **personnels**, seuls les quatre derniers chiffres de votre numéro de téléphone sont visibles par votre organisation. Vous pouvez voir le **Type de propriété** pour chaque appareil en ouvrant la page **Détails sur l’appareil** de l’appareil.
- Espace de stockage sur l’appareil : si vous ne réussissez pas à installer une application obligatoire, votre organisation peut regarder si l’espace de stockage disponible sur votre appareil est insuffisant.  
-  Emplacement : votre organisation ne peut jamais voir l’emplacement de votre appareil, sauf s’il s’agit d’un appareil iOS supervisé qui a été perdu. [Comment savoir ?](https://go.microsoft.com/fwlink/?linkid=853816)
- Inventaire des applications : si votre organisation utilise Mobile Threat Defense, elle peut voir plus de détails sur les applications installées sur votre appareil iOS. Découvrez plus d’informations sur [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md).
- Informations sur le réseau : certaines informations sur les connexions réseau des appareils Android peuvent être visibles par l’équipe de support de votre organisation. Par exemple, si votre organisation exige que les appareils restent dans un bâtiment spécifique, votre appareil identifie le réseau auquel il est connecté. 
