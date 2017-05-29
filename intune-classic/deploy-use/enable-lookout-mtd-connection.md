---
title: Activer Lookout MTP dans Intune | Microsoft Docs
description: "Activer la protection contre les menaces mobiles (MTP) de Lookout dans la console d’administration Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2a99839ece16c56c7bfaacb295796525903f9464
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---

# <a name="enable-lookout-mtd-connection-in-the-intune-classic-console"></a>Activer la connexion Lookout MTD dans la console classique Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pour activer la connexion Lookout Mobile Threat Defense (MTD) dans Intune, vous devez avoir déjà configuré le connecteur Intune dans la console Lookout.  Si vous ne le n'avez pas déjà fait, vous devez [configurer votre abonnement Lookout Mobile Threat Defense](setup-your-lookout-mtd-subscription.md).

Pour activer la connexion à Lookup MTP dans Intune, dans la page **Administration** de la [console Administrateur Microsoft Intune](https://manage.microsoft.com), choisissez **Intégration des services tiers**. Choisissez **État de Lookout** et activez **Synchronisation avec MTP** à l’aide du bouton bascule.

![Capture d’écran de la page Synchronisation avec MTP avec le bouton bascule d’activation mis en surbrillance](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Vous **devez** configurer l’application Lookout for Work avant de créer les règles de la stratégie de conformité et de configurer l’accès conditionnel. Cela garantit que l’application est prête et mise à la disposition des utilisateurs finaux qui souhaitent l’installer pour pouvoir accéder à leur messagerie ou aux autres ressources d’entreprise.

Cette opération termine la configuration de l’intégration de Lookup et d’Intune dans la console d’administration Intune.  Les prochaines étapes de l’implémentation de cette solution consistent à déployer la stratégie pour les [applications Lookout for Work](/intune-classic/deploy-use/device-threat-protection-policy).


## <a name="next-steps"></a>Étapes suivantes
[Configurer l’application Lookout for Work](/intune-classic/deploy-use/device-threat-protection-apps)

