---
title: Activer Lookout MTP dans Intune | Microsoft Intune
description: "Activer la protection contre les menaces mobiles (MTP) de Lookout dans la console d’administration Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 1bef6c15387309e1b36bc85758ca699acd54fdd0


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Activer la connexion à Lookout MTP dans la console d’administration Intune
Cette rubrique explique comment activer la connexion à Lookout MTP dans Intune. Avant d’effectuer cette étape, vous devez avoir configuré le connecteur Intune dans la console Lookout.  Si vous ne l’avez pas encore fait, suivez la procédure décrite dans [Configurer votre abonnement pour la protection contre les menaces mobiles de Lookout](set-up-your-subscription-with-lookout-mtp.md).

Pour activer la connexion à Lookup MTP dans Intune, dans la page **Administration** de la [console Administrateur Microsoft Intune](https://manage.microsoft.com), choisissez **Intégration des services tiers**. Choisissez **État de Lookout** et activez **Synchronisation avec MTP** à l’aide du bouton bascule.

![Capture d’écran de la page Synchronisation avec MTP avec le bouton bascule d’activation mis en surbrillance](../media/mtp/lookout-intune-synchronization.png)

Cette opération termine la configuration de l’intégration de Lookup et d’Intune dans la console d’administration Intune.  Les prochaines étapes de l’implémentation de cette solution consistent à déployer les [applications Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) et à définir la stratégie de [conformité](enable-device-threat-protection-rule-in-compliance-policy.md).

>[!IMPORTANT]
> Vous **devez** configurer l’application Lookout for Work avant de créer les règles de la stratégie de conformité et de configurer l’accès conditionnel. Cela garantit que l’application est prête et mise à la disposition des utilisateurs finaux qui souhaitent l’installer pour pouvoir accéder à leur messagerie ou aux autres ressources d’entreprise.
## <a name="next-steps"></a>Étapes suivantes
[Configurer l’application Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Dec16_HO2-->


