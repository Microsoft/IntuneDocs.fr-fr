---
title: Valider la configuration de votre stratégie de protection d’application
titleSuffix: Microsoft Intune
description: Découvrez comment tester votre stratégie de protection d’application pour vérifier qu’elle est bien configurée et qu’elle fonctionne correctement.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cac03f35cdec3c1a4815559abc83108bd27d3472
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231115"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Guide pratique de validation de votre configuration de stratégie de protection d’application

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vérifiez que votre stratégie de protection d’application est bien configurée et qu’elle fonctionne correctement. Ces instructions s’appliquent aux stratégies de protection des applications dans le portail Azure.

### <a name="checking-for-symptoms"></a>Recherche de symptômes
Les utilisateurs ont peu de chances de signaler des problèmes étant donné que la protection d’application est un outil de protection des données. En cas de problème avec la configuration de la protection d’application, l’utilisateur dispose d’un accès illimité, comme il en disposerait sans la protection d’application, et il n’a pas conscience de l’existence d’un problème. C’est pourquoi nous vous recommandons de valider la configuration de votre protection d’application en pilotant vos stratégies de protection d’application avec un petit groupe d’utilisateurs à même d’en tester délibérément les restrictions.


### <a name="what-to-check"></a>Les points à vérifier

Si les tests montrent que le comportement de votre stratégie de protection d’application n’est pas conforme à ce qui est prévu, nous vous recommandons de vérifier les éléments suivants :

- Les utilisateurs disposent-ils d’une licence pour la protection d’application ?
- Les utilisateurs disposent-ils d’une licence pour O365 ?
- L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**.

#### <a name="user-app-protection-status"></a>État de protection d’application utilisateur
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
1. Choisissez **Gérer les applications** > **Surveiller** >  **État de protection de l’application** > **Utilisateurs affectés**.

2. Choisissez un utilisateur dans la liste ou recherchez et sélectionnez un utilisateur, puis choisissez **Sélectionner un utilisateur**. En haut de la colonne **Rapports d’application**, vous voyez si l’utilisateur a une licence pour la protection d’application. Vous voyez aussi si l’utilisateur a une licence pour O365, et l’état de l’application pour tous les appareils de l’utilisateur est indiqué.



### <a name="what-to-do"></a>Procédure à suivre
Voici les actions à exécuter selon l’état de l’utilisateur :

- Si l’utilisateur n’est pas autorisé pour la protection d’application, attribuez une licence Intune à l’utilisateur.
- Si l’utilisateur n’a pas de licence pour O365, obtenez-en une pour lui.
- Si l’état de l’application de l’utilisateur est **Non archivé**, vérifiez si vous avez correctement configuré une stratégie de protection d’application pour cette application.
- Vérifiez que ces conditions sont appliquées à tous les utilisateurs auxquels vous voulez appliquer des stratégies de protection d’application.

### <a name="see-also"></a>Voir aussi

[Qu’est ce qu’une stratégie de protection d’application Intune ?](app-protection-policies.md)
