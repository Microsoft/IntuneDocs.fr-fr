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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19fff092f7eccfc6de2a027c7834c52698176cbf
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569164"
---
# <a name="assign-a-role-to-an-intune-user"></a>Attribuer un rôle à un utilisateur d’Intune

Vous pouvez attribuer un rôle [intégré](role-based-access-control.md#built-in-roles) ou [personnalisé](create-custom-role.md) à un utilisateur d’Intune.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- **Administrateur général**
- **Administrateur du service Intune**

1. Dans le [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Administration de locataire** > **Rôles** > **Tous les rôles**.

2. Dans le panneau **Rôles Intune - Tous les rôles**, choisissez le rôle intégré que vous voulez affecter > **Attributions** > **Attribuer**.

5. Dans la page **De base**, entrez un **Nom de l’attribution** et éventuellement une **Description de l’attribution**, puis choisissez **Suivant**.

6. Dans la page **Groupes d’administrateurs**, sélectionnez le groupe qui contient l’utilisateur auquel vous voulez accorder les autorisations. Sélectionnez **Suivant**

7. Dans la page **Étendue (groupes)**, choisissez un groupe contenant les utilisateurs/appareils que le membre ci-dessus sera autorisé à gérer. Choisissez **Suivant**.

8. Dans la page **Étendue (balises)**, choisissez des balises où cette attribution de rôle s’appliquera. Choisissez **Suivant**.

9. Dans la page **Vérifier + créer**, quand vous avez terminé, choisissez **Créer**. La nouvelle affectation s’affiche dans la liste des affectations.

## <a name="next-steps"></a>Étapes suivantes
- [En savoir plus sur le contrôle d’accès en fonction du rôle dans Intune](role-based-access-control.md)
- [Créer un rôle personnalisé](create-custom-role.md)


