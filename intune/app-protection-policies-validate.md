---
title: Valider la configuration de votre stratégie de protection d’application
titleSuffix: Microsoft Intune
description: Découvrez comment tester votre stratégie de protection d’application pour vérifier qu’elle est bien configurée et qu’elle fonctionne correctement dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 760ff85bc31cf66e66a3bf98f7da22d5ce48eee0
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569439"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Guide pratique de validation de votre configuration de stratégie de protection d’application dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vérifiez que votre stratégie de protection d’application est bien configurée et qu’elle fonctionne correctement. Ces instructions s’appliquent aux stratégies de protection des applications dans le portail Azure.

## <a name="checking-for-symptoms"></a>Recherche de symptômes
Les utilisateurs ont peu de chances de signaler des problèmes étant donné que la protection d’application est un outil de protection des données. En cas de problème avec la configuration de la protection d’application, l’utilisateur disposera d’un accès illimité, comme il en disposerait sans la protection d’application, et il n’aurait pas conscience de l’existence d’un problème. C’est pourquoi nous vous recommandons de valider la configuration de votre protection d’application en pilotant vos stratégies de protection d’application avec un petit groupe d’utilisateurs à même d’en tester délibérément les restrictions.

## <a name="what-to-check"></a>Les points à vérifier

Si les tests montrent que le comportement de votre stratégie de protection d’application ne fonctionne pas comme prévu, vérifiez les éléments suivants :

- Les utilisateurs disposent-ils d’une licence pour la protection d’application ?
- Les utilisateurs disposent-ils d’une licence pour O365 ?
- L’état de chacune des applications de protection d’application des utilisateurs est-il comme prévu ? Les états possibles des applications sont **Archivé** et **Non archivé**.

### <a name="user-app-protection-status"></a>État de protection d’application utilisateur
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Sélectionnez **Applications clientes** >  **État de protection d’application**, puis sélectionnez la vignette **Utilisateurs attribués**. 
4. Sur la page **Rapports d’application**, sélectionnez **Sélectionner un utilisateur** pour afficher la liste des utilisateurs et des groupes. 
5. Recherchez et sélectionnez un utilisateur dans la liste, puis choisissez **Sélectionner un utilisateur**. En haut du volet **Rapports d’application**, vous voyez si l’utilisateur a une licence pour la protection d’application. Vous voyez aussi si l’utilisateur a une licence pour O365, et l’état de l’application pour tous les appareils de l’utilisateur est indiqué.

## <a name="what-to-do"></a>Procédure à suivre
Voici les actions à exécuter selon l’état de l’utilisateur :

- Si l’utilisateur n’est pas autorisé pour la protection d’application, attribuez une [licence Intune](licenses.md) à l’utilisateur.
- Si l’utilisateur n’a pas de licence pour O365, obtenez une [licence](licenses.md) pour lui.
- Si l’état de l’application de l’utilisateur est **Non archivé**, vérifiez si vous avez correctement configuré une [stratégie de protection d’application](app-protection-policies-validate.md) pour cette application.
- Vérifiez que ces conditions sont appliquées à tous les utilisateurs auxquels vous voulez appliquer des [stratégies de protection d’application](app-protection-policies-monitor.md).

## <a name="see-also"></a>Voir aussi

- [Qu’est ce qu’une stratégie de protection d’application Intune ?](app-protection-policies.md)
- [Licences incluant Intune](licenses.md)
- [Affecter des licences aux utilisateurs pour qu’ils puissent inscrire des appareils dans Intune](licenses-assign.md)
- [Guide pratique de validation de votre configuration de stratégie de protection d’application](app-protection-policies-validate.md)
- [Guide pratique de surveillance des stratégies de protection des applications](app-protection-policies-monitor.md)

