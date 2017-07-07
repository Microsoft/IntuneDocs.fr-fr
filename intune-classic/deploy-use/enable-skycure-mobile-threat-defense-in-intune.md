---
title: Activer Skycure Mobile Threat Defense dans Intune
description: Activez Skycure Mobile Threat Defense dans la console classique Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4dad45d15fec7189fdcf184839040b9e3f9a3a48
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Activer Skycure Mobile Threat Defense dans Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Pour activer la protection contre les menaces mobiles Skycure, vous devez avoir déjà configuré le [connecteur Intune dans la console Skycure] (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Pour activer la connexion Skycure MTD dans Intune

1.  Accédez à la [console classique Intune](https://manage.microsoft.com/) puis entrez vos informations d’identification.

2.  Choisissez **Administrateur** &gt; **Intégration de service tiers**, puis choisissez **État de Skycure** et **Synchronisation avec MTD** à l’aide du bouton bascule.

    ![Activer le bouton bascule Skycure dans la console classique Intune classique](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Vous devez configurer les applications Skycure avant de créer les règles de la stratégie de conformité et de configurer l’accès conditionnel. Cela garantit que l’application est prête et mise à la disposition des utilisateurs finaux qui souhaitent l’installer pour pouvoir accéder à leur messagerie ou aux autres ressources d’entreprise.

Cette opération termine la configuration de l’intégration de Skycure et d’Intune dans la console d’administration Intune. Les prochaines étapes de l’implémentation de cette solution consistent à déployer les applications Skycure et à définir la stratégie de conformité.

## <a name="next-steps"></a>Étapes suivantes

[Créer la stratégie de conformité Skycure Mobile Threat Defense](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
