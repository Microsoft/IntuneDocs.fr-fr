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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68c2dc7df123593513c14e16e2626c7426f50b01
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207415"
---
# <a name="create-a-custom-role-in-intune"></a>Créer un rôle personnalisé dans Intune

Vous pouvez créer un rôle Intune personnalisé qui inclut toutes les autorisations requises pour une fonction de tâche donnée. Par exemple, si un groupe du service informatique gère les applications, les stratégies et les profils de configuration, vous pouvez ajouter toutes ces autorisations ensemble à un même rôle personnalisé. Après avoir créé un rôle personnalisé, vous pouvez l’[attribuer](assign-role.md) à tout utilisateur ayant besoin de ces autorisations.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- **Administrateur général**
- **Administrateur du service Intune**

## <a name="to-create-a-custom-role"></a>Pour créer un rôle personnalisé

1. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Rôles** > **Tous les rôles** > **Ajouter**.

2. Sur le panneau **Ajouter un rôle personnalisé**, entrez le nom et la description du nouveau rôle, puis cliquez sur **Autorisations**.

3. Dans le panneau **Autorisations**, sélectionnez les autorisations que vous souhaitez utiliser avec ce rôle.

4. Dans le panneau **Étendue (balises)** , choisissez les balises pour ce rôle. Ce rôle peut accéder aux ressources qui ont également ces balises.

5. Quand vous avez terminé, choisissez **OK**.

6. Dans le panneau **Ajouter un rôle personnalisé**, cliquez sur **Créer**. Le nouveau rôle s’affiche dans la liste du panneau **Rôles Intune - Tous les rôles**.


## <a name="copy-a-role"></a>Copier un rôle

Vous pouvez également copier un rôle existant.

1. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Rôles** > **Tous les rôles** > Sélectionnez un rôle dans la liste > **Dupliquer**.

2. Sous **Dupliquer un rôle**, entrez un nom. Veillez à utiliser un nom unique.

3. Toutes les autorisations et balises d’étendue du rôle d’origine sont déjà sélectionnées. Par la suite, vous pouvez modifier le **Nom**, la **Description**, les **Autorisations** et l’**Étendue (balises)** du rôle dupliqué.

4. Sélectionnez **Créer**. 

## <a name="next-steps"></a>Étapes suivantes
- [Attribuer un rôle à un utilisateur](assign-role.md)
- [En savoir plus sur le contrôle d’accès en fonction du rôle dans Intune](role-based-access-control.md)
