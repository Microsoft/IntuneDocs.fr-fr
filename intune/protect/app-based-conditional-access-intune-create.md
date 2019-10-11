---
title: Configurer une stratégie d’accès conditionnel basée sur l’application avec Intune
titleSuffix: Microsoft Intune
description: Découvrez comment créer une stratégie d’accès conditionnel basée sur l’application avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9cbe57d0cf69f036cd36d2c1b95c48b198645e7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723084"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurer des stratégies d’accès conditionnel basées sur des applications avec Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Configurez des stratégies d’accès conditionnel basées sur des applications pour les applications qui figurent dans la liste des applications approuvées. La liste des applications approuvées se compose d’applications ayant été testées par Microsoft.

> [!IMPORTANT]
> Cet article décrit les étapes permettant d’ajouter une stratégie d’accès conditionnel basé sur l’application. Vous pouvez utiliser les mêmes étapes quand vous ajoutez des applications comme SharePoint Online, Microsoft Teams et Microsoft Exchange Online à partir de la liste des applications approuvées.

## <a name="create-app-based-conditional-access-policies"></a>Créer des stratégies d’accès conditionnel basées sur l’application
L’accès conditionnel est une technologie Azure Active Directory (Azure AD). Le nœud d’accès conditionnel accessible à partir d’*Intune* est le même nœud que celui accessible à partir d’*Azure AD*. Cela signifie que vous n’avez pas besoin de basculer entre Intune et Azure AD pour configurer des stratégies.

> [!IMPORTANT]
> Vous devez disposer d’une licence Azure AD Premium pour créer des stratégies d’accès conditionnel à partir du portail Intune.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Créer des stratégies d’accès conditionnel basées sur l’application

> [!IMPORTANT]
> Les [stratégies de protection des applications Intune](../apps/app-protection-policies.md) doivent être appliquées à vos applications avant d’utiliser des stratégies d’accès conditionnel basé sur l’application.

1. Dans le **tableau de bord Intune**, sélectionnez **Accès conditionnel**.

2. Dans le volet **Stratégies**, choisissez **Nouvelle stratégie** pour créer votre stratégie d’accès conditionnel basé sur l’application.

4. Une fois que vous entrez un nom de stratégie et configuré les paramètres disponibles dans la section **Affectations**, choisissez **Octroyer** sous la section **Contrôles d’accès**.

5. Choisissez **Demander une application cliente approuvée** , **Sélectionner**, puis **Créer** pour enregistrer la nouvelle stratégie.

## <a name="next-steps"></a>Étapes suivantes
[Bloquer les applications sans authentification moderne](app-modern-authentication-block.md)

## <a name="see-also"></a>Voir aussi

[Protéger les données d’application à l’aide de stratégies de protection des applications](../apps/app-protection-policies.md)
[Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
