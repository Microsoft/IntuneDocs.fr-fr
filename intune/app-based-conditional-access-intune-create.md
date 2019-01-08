---
title: Configurer une stratégie d’accès conditionnel basée sur l’application avec Intune
titlesuffix: Microsoft Intune
description: Découvrez comment créer une stratégie d’accès conditionnel basée sur l’application avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 079671064c09c22d151ea71f8b3fb385652aef0f
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816920"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurer des stratégies d’accès conditionnel basées sur des applications avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Configurez des stratégies d’accès conditionnel basées sur des applications pour les applications qui figurent dans la liste des applications approuvées. La liste des applications approuvées se compose d’applications ayant été testées par Microsoft.

> [!IMPORTANT]
> Cet article décrit les étapes permettant d’ajouter une stratégie d’accès conditionnel basé sur l’application. Vous pouvez utiliser les mêmes étapes quand vous ajoutez des applications comme SharePoint Online, Microsoft Teams et Microsoft Exchange Online à partir de la liste des applications approuvées.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Création de stratégies d’accès conditionnel basé sur l’application dans la charge de travail Azure AD

Les administrateurs informatiques peuvent créer des stratégies d’accès conditionnel basé sur l’application à partir de la charge de travail Azure AD. Cet accès signifie qu’il n’est plus nécessaire de basculer entre les charges de travail Azure et Intune.

> [!IMPORTANT]
> Vous devez disposer d’une licence Azure AD Premium pour créer des stratégies d’accès conditionnel Azure AD à partir du portail Intune Azure.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Pour créer une stratégie d’accès conditionnelle basée sur l’application

> [!IMPORTANT]
> Les [stratégies de protection des applications Intune](app-protection-policies.md) doivent être appliquées à vos applications avant d’utiliser des stratégies d’accès conditionnel basé sur l’application.

1. Dans le **tableau de bord Intune**, choisissez **Accès conditionnel**.

2. Dans le volet **Stratégies**, choisissez **Nouvelle stratégie** pour créer votre stratégie d’accès conditionnel basé sur l’application.

4. Une fois que vous entrez un nom de stratégie et configuré les paramètres disponibles dans la section **Affectations**, choisissez **Octroyer** sous la section **Contrôles d’accès**.

5. Choisissez **Demander une application cliente approuvée** , **Sélectionner**, puis **Créer** pour enregistrer la nouvelle stratégie.

## <a name="next-steps"></a>Étapes suivantes
[Bloquer les applications sans authentification moderne](app-modern-authentication-block.md)

### <a name="see-also"></a>Voir aussi

[Protéger les données d’application à l’aide de stratégies de protection des applications](app-protection-policies.md)
[Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
