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
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d053b0b37931443a343c91b5122b7a097d248c51
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048687"
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

5. Dans le panneau **Autorisations**, sélectionnez les autorisations que vous souhaitez utiliser avec ce rôle. Utilisez le [Tableau RBAC d’Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) comme référence pour déterminer quelles autorisations vous souhaitez appliquer.

6. Dans le panneau **Étendue (balises)**, choisissez les balises pour ce rôle. Ce rôle peut accéder aux ressources qui ont également ces balises.

7. Quand vous avez terminé, choisissez **OK**.

8. Dans le panneau **Ajouter un rôle personnalisé**, cliquez sur **Créer**. Le nouveau rôle s’affiche dans la liste du panneau **Rôles Intune - Tous les rôles**.

## <a name="next-steps"></a>Étapes suivantes
- [Attribuer un rôle à un utilisateur](assign-role.md)
- [En savoir plus sur le contrôle d’accès en fonction du rôle dans Intune](role-based-access-control.md)
