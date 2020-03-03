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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569181"
---
# <a name="create-a-custom-role-in-intune"></a>Créer un rôle personnalisé dans Intune

Vous pouvez créer un rôle Intune personnalisé qui inclut toutes les autorisations requises pour une fonction de tâche donnée. Par exemple, si un groupe du service informatique gère les applications, les stratégies et les profils de configuration, vous pouvez ajouter toutes ces autorisations ensemble à un même rôle personnalisé. Après avoir créé un rôle personnalisé, vous pouvez l’[attribuer](assign-role.md) à tout utilisateur ayant besoin de ces autorisations.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- **Administrateur général**
- **Administrateur du service Intune**

## <a name="to-create-a-custom-role"></a>Pour créer un rôle personnalisé

1. Dans le [centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Administration de locataire** > **Rôles** > **Tous les rôles** > **Créer**.

2. Dans la page **De base**, entrez un nom et une description pour le nouveau rôle, puis choisissez **Suivant**.

3. Dans la page **Autorisations**, choisissez les autorisations que vous voulez utiliser avec ce rôle.

4. Dans la page **Étendue (balises)**, choisissez les balises pour ce rôle. Ce rôle peut accéder aux ressources qui ont également ces balises. Choisissez **Suivant**.

5. Dans la page **Vérifier + créer**, quand vous avez terminé, choisissez **Créer**. Le nouveau rôle s’affiche dans la liste du panneau **Rôles Intune - Tous les rôles**.

## <a name="copy-a-role"></a>Copier un rôle

Vous pouvez également copier un rôle existant.

1. Dans le [centre d’administration du gestionnaire de points de terminaison](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Administration de locataire** > **Rôles** > **Tous les rôles** > cochez la case pour un rôle dans la liste > **Dupliquer**.

2. Dans la page **De base**, entrez un nom. Veillez à utiliser un nom unique.

3. Toutes les autorisations et balises d’étendue du rôle d’origine sont déjà sélectionnées. Par la suite, vous pouvez modifier le **Nom**, la **Description**, les **Autorisations** et l’**Étendue (balises)** du rôle dupliqué.

4. Une fois que vous avez apporté toutes les modifications souhaitées, choisissez **Suivant** pour accéder à la page **Vérifier + créer**. Sélectionnez **Créer**. 

## <a name="next-steps"></a>Étapes suivantes
- [Attribuer un rôle à un utilisateur](assign-role.md)
- [En savoir plus sur le contrôle d’accès en fonction du rôle dans Intune](role-based-access-control.md)


