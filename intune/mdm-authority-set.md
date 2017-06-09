---
title: "Définir l’autorité de gestion des appareils mobiles"
titleSuffix: Intune Azure preview
description: "Intune Azure (préversion) : découvrez comment définir l’autorité de gestion des appareils mobiles dans Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Définir l’autorité de gestion des appareils mobiles

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Le paramètre d’autorité de gestion des appareils mobiles (MDM) détermine la façon dont vous gérez vos appareils. En tant qu’administrateur informatique, vous devez définir une autorité de gestion des appareils mobiles (MDM) avant que les utilisateurs puissent inscrire des appareils pour la gestion.

Les configurations possibles sont les suivantes :

- **Intune autonome** : gestion cloud uniquement, que vous configurez à l’aide du portail Azure. Inclut l’ensemble complet de fonctionnalités d’Intune. [Configurez l’autorité MDM dans la console Intune](#mdm-authority-set-to-intune).

- **Intune hybride** : intégration de la solution cloud Intune à System Center Configuration Manager. Vous configurez Intune à l’aide de la console Configuration Manager. [Configurez l’autorité MDM dans Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestion des appareils mobiles pour Office 365** : intégration d’Office 365 à la solution cloud Intune. Vous configurez Intune à partir de votre Centre d’administration Office 365. Comprend un sous-ensemble des fonctionnalités disponibles avec Intune autonome. Configurez l’autorité MDM dans le Centre d'administration Office 365.

>[!IMPORTANT]
>Une fois l’autorité de gestion des appareils mobiles définie, vous devez contacter le [Support Microsoft](https://docs.microsoft.com/intune-classic/troubleshoot/get-support) pour la modifier. Réfléchissez donc bien à votre choix.

## <a name="set-mdm-authority-to-intune"></a>Définir l'autorité MDM sur Intune

1. Dans le portail Azure, choisissez **Plus de services** > **Surveillance + gestion** > **Intune**.
  ![Capture d’écran de la charge de travail Dépannage d’Intune avec le lien Sélectionner utilisateur](media/set-mdm-auth.png)
2. Dans le panneau Intune, choisissez **Inscription de l’appareil**, puis choisissez **Vue d’ensemble**.

3. Dans le panneau **Démarrer la gestion des appareils**, choisissez **Définir l’autorité MDM sur Intune**. Un message indique que vous avez défini Intune comme autorité de gestion des appareils mobiles.
