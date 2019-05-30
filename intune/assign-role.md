---
title: Attribuer un rôle à un utilisateur d’Intune
description: Découvrez comment attribuer un rôle intégré ou personnalisé à un utilisateur dans Microsoft Intune.
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
ms.openlocfilehash: a22fef1c04ae52a8a4cc65eaadc1ef6fcd524c19
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043594"
---
# <a name="assign-a-role-to-an-intune-user"></a>Attribuer un rôle à un utilisateur d’Intune

Vous pouvez attribuer un rôle [intégré](role-based-access-control.md#built-in-roles) ou [personnalisé](create-custom-role.md) à un utilisateur d’Intune.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- **Administrateur général**
- **Administrateur du service Intune**

Pour obtenir une liste complète des autorisations pour chaque rôle intégré, consultez le [tableau RBAC d’Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.

3. Dans le panneau **Intune**, choisissez **Rôles** > **Tous les rôles**.

4. Dans le panneau **Rôles Intune - Tous les rôles**, choisissez le rôle intégré que vous souhaitez affecter.

5. Dans le panneau <*Nom de rôle*> - **Vue d’ensemble**, choisissez **Gérer** > **Affectations**.

6. Sur le panneau de rôle personnalisé, choisissez **Affecter**.

7. Dans le panneau **Attributions de rôles**, entrez un **Nom d’affectation** et, éventuellement, une **Description d’affectation** pour l’affectation.

8. Pour **Membres (groupes)**, choisissez un groupe qui contient l’utilisateur auquel vous souhaitez accorder les autorisations.

9. Pour **Étendue (groupes)**, choisissez un groupe contenant les utilisateurs/appareils que le membre ci-dessus sera autorisé à gérer.

10. Pour **Étendue (balises)**, choisissez des balises où cette attribution de rôle s’appliquera.

11. Quand vous avez terminé, choisissez **OK**. La nouvelle affectation s’affiche dans la liste des affectations.


## <a name="next-steps"></a>Étapes suivantes
- [En savoir plus sur le contrôle d’accès en fonction du rôle dans Intune](role-based-access-control.md)
- [Créer un rôle personnalisé](create-custom-role.md)
