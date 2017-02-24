---
title: "Définir l’autorité de gestion des appareils mobiles | Intune Azure (préversion) | Microsoft Docs"
description: "Intune Azure (préversion) : découvrez comment définir l’autorité de gestion des appareils mobiles dans Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 72a162175e278faa236add5698d65233fa851c7b

---

# <a name="set-the-mobile-device-management-authority"></a>Définir l’autorité de gestion des appareils mobiles 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Le paramètre d’autorité de gestion des appareils mobiles détermine la façon dont vous gérez vos appareils. Les configurations possibles sont les suivantes :

- **Intune autonome** : gestion cloud uniquement, que vous configurez à l’aide du portail Azure. Inclut l’ensemble complet de fonctionnalités d’Intune.

- **Intune hybride** : intégration de la solution cloud Intune à System Center Configuration Manager. Vous configurez Intune à l’aide de la console Configuration Manager.

- **Gestion des appareils mobiles pour Office 365** : intégration d’Office 365 à la solution cloud Intune. Vous configurez Intune à partir de votre Centre d’administration Office 365. Comprend un sous-ensemble des fonctionnalités disponibles avec Intune autonome.

>[!IMPORTANT]
>Une fois l’autorité de gestion des appareils mobiles définie, vous devez contacter le [Support Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) pour la modifier. Réfléchissez donc bien à votre choix.

**Pour définir l’autorité de gestion des appareils mobiles :**

1. Dans le portail Azure, choisissez **Plus de services** > **Surveillance + gestion** > **Intune**.

2. Dans le panneau Intune, choisissez **Inscrire des appareils**, puis **Vue d’ensemble**.

3. Dans le panneau **Démarrer la gestion des appareils**, choisissez **Définir l’autorité MDM sur Intune**. Un message indique que vous avez défini Intune comme autorité de gestion des appareils mobiles.



<!--HONumber=Feb17_HO3-->


