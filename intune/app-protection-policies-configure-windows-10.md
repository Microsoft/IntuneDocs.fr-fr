---
title: Préparer la configuration des stratégies de protection d’application pour Windows 10
titleSuffix: Microsoft Intune
description: Configuration du fournisseur de gestion des applications mobiles dans Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5953038f3627f98f0e034aeba4c2c92ea3dca2d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184384"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Préparer la configuration des stratégies de protection d’application pour Windows 10 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Activez la gestion des applications mobiles (GAM) pour Windows 10 en définissant le fournisseur GAM dans Azure AD. La définition d’un fournisseur GAM dans Azure AD vous permet de définir l’état d’inscription durant la création d’une nouvelle stratégie de Protection des informations Windows (WIP) avec Intune. L’état de l’inscription peut être MAM ou gestion des appareils mobiles (MDM).

## <a name="to-configure-the-mam-provider"></a>Pour configurer le fournisseur MAM

1. Connectez-vous au portail Azure et sélectionnez **Azure Active Directory**.

2. Sélectionnez **Mobilité (MDM et GAM)** dans le groupe **Gérer**.

3. Cliquez sur **Microsoft Intune**.

4. Configurez les paramètres dans le groupe **Restaurer les URL Gestion des applications mobiles par défaut** du panneau **Configurer**.

   **Portée de l'utilisateur Gestion des applications mobiles**  
   Utilisez l’inscription automatique GAM pour gérer les données d’entreprise sur les périphériques Windows de vos employés. L’inscription automatique GAM sera configurée pour des scénarios BYOD (Apportez votre propre appareil).<ul><li>**Aucune.**<br>Sélectionnez cette option si aucun utilisateur ne peut être inscrit dans MAM.</li><li>**Quelques-uns**<br>Sélectionnez les groupes Azure AD qui contiennent les utilisateurs qui seront inscrits dans GAM.</li><li>**Tous**<br>Sélectionnez cette option si tous les utilisateurs peuvent être inscrits dans GAM.</li></ul>

   **URL des conditions d'utilisation de GAM**  
   L’URL des conditions d’utilisation MAM n’est pas prise en charge pour Microsoft Intune. Cette zone d’entrée doit être vide pour appliquer des stratégies de protection.

   **URL de détection de GAM**  
   Il s’agit de l’URL du point de terminaison d’inscription du service GAM. Le point de terminaison sert à inscrire des appareils à gérer à travers le service GAM.

   **URL de conformité GAM**  
   L’URL de conformité MAM n’est pas prise en charge pour Microsoft Intune. Cette zone d’entrée doit être vide pour appliquer des stratégies de protection. 

5.  Cliquez sur **Save**.

## <a name="next-steps"></a>Étapes suivantes

[Créer une stratégie de protection d’application WIP](windows-information-protection-policy-create.md)
