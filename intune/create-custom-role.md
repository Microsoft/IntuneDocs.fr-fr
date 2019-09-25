---
title: Créer un rôle personnalisé dans Intune
description: Découvrez comment créer un rôle personnalisé dans Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7e8f5077f2052a11c980ae3f5629af810a8a0b
ms.sourcegitcommit: 49f25efb9bc0f16f587f27878cf45de5e4e6a27f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71094696"
---
# <a name="create-a-custom-role-in-intune"></a>Créer un rôle personnalisé dans Intune

Vous pouvez créer un rôle Intune personnalisé qui inclut toutes les autorisations requises pour une fonction de tâche donnée. Par exemple, si un groupe du service informatique gère les applications, les stratégies et les profils de configuration, vous pouvez ajouter toutes ces autorisations ensemble à un même rôle personnalisé. Après avoir créé un rôle personnalisé, vous pouvez l’[attribuer](assign-role.md) à tout utilisateur ayant besoin de ces autorisations.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- **Administrateur général**
- **Administrateur du service Intune**

## <a name="to-create-a-custom-role"></a>Pour créer un rôle personnalisé

1. Connectez-vous au [Portail Azure](https://portal.azure.com) avec vos informations d’identification Intune.

2. Choisissez **Tous les services** dans le menu de gauche, puis entrez **Intune** dans le filtre de la zone de texte.

3. Choisissez **Intune** > **Rôles** > **Tous les rôles** > **Ajouter**.

4. Sur le panneau **Ajouter un rôle personnalisé**, entrez le nom et la description du nouveau rôle, puis cliquez sur **Autorisations**.

5. Dans le panneau **Autorisations**, sélectionnez les autorisations que vous souhaitez utiliser avec ce rôle.

6. Dans le panneau **Étendue (balises)** , choisissez les balises pour ce rôle. Ce rôle peut accéder aux ressources qui ont également ces balises.

7. Quand vous avez terminé, choisissez **OK**.

8. Dans le panneau **Ajouter un rôle personnalisé**, cliquez sur **Créer**. Le nouveau rôle s’affiche dans la liste du panneau **Rôles Intune - Tous les rôles**.

## <a name="next-steps"></a>Étapes suivantes
- [Attribuer un rôle à un utilisateur](assign-role.md)
- [En savoir plus sur le contrôle d’accès en fonction du rôle dans Intune](role-based-access-control.md)
