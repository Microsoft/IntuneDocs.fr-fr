---
title: Inclure et exclure des affectations d’applications dans Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser Microsoft Intune pour inclure et exclure des affectations d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb55951390c3fe19651087e16c3185018cfd9dab
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049304"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inclure et exclure des affectations d’applications dans Microsoft Intune

Dans Intune, vous pouvez déterminer qui a accès à une application en affectant des groupes d’utilisateurs à inclure et à exclure. Avant d’affecter des groupes à l’application, vous devez définir le type d’affectation d’une application. Le type d’affectation rend l’application disponible, obligatoire ou la désinstalle. 

Pour définir la disponibilité d’une application, vous incluez et excluez des affectations d’applications à un groupe d’utilisateurs ou d’appareils à l’aide d’une combinaison d’affectations de groupes d’inclusion et d’exclusion. Cette fonctionnalité est utile quand vous rendez l’application disponible en incluant un grand groupe, puis que vous affinez les utilisateurs sélectionnés en excluant un groupe plus petit. Le groupe plus petit peut être un groupe de test ou un groupe exécutif. 

Quand vous excluez des groupes d’une affectation d’applications, vous devez exclure uniquement des groupes d’utilisateurs ou uniquement des groupes d’appareils. Vous ne pouvez pas exclure un mélange de groupes d’utilisateurs et de groupes d’appareils. 

Intune ne prend pas en compte l’association entre utilisateurs et appareils quand vous excluez des groupes. L’inclusion de groupes d’utilisateurs tout en excluant des groupes d’appareils n’aboutira vraisemblablement pas aux résultats voulus. L’inclusion est prioritaire sur l’exclusion. Par exemple, si vous ciblez une application iOS sur **Tous les utilisateurs** et excluez **Tous les iPad**, le résultat net est que tous les utilisateurs utilisant un iPad peuvent obtenir l’application. Cependant, si vous ciblez l’application iOS sur **Tous les appareils** et excluez **Tous les iPad**, le déploiement est réussi.  

> [!NOTE]
> Quand vous définissez une affectation de groupe pour une application, le type **Non applicable** est déprécié et remplacé par la fonctionnalité d’exclusion de groupe. 
>
> Intune fournit des groupes **Tous les utilisateurs** et **Tous les appareils** précréés dans la console. Les groupes ont des optimisations intégrées pour votre confort. Nous vous recommandons vivement d’utiliser ces groupes pour cibler tous les utilisateurs et tous les appareils au lieu de créer vous-même des groupes « Tous les utilisateurs » ou « Tous les appareils ».  
>
> Android Enterprise prend en charge l’inclusion et l’exclusion de groupes. Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications Android Entreprise. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>Inclure et exclure des groupes lors de l’affectation d’applications 
Pour affecter une application à des groupes à l’aide de l’affectation d’inclusion et d’exclusion :
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le menu **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet **Applications clientes**, sélectionnez **Applications**. La liste des applications ajoutées s’affiche.
5. Sélectionnez l’application que vous voulez attribuer. Un tableau de bord contient des informatinos sur l’application. 
6. Dans la section **Gérer** du menu, sélectionnez **Affectations**. 

    ![Inclure les affectations d’applications lors des affectations d’applications](./media/apps-inc-exl-01.png)
7. Sélectionnez **Ajouter un groupe** pour ajouter les groupes d’utilisateurs affectés à l’application. 
8. Dans le volet **Ajouter un groupe**, sélectionnez un **Type d’affectation** parmi les types d’affectations disponibles.
9. Comme type d’affectation, sélectionnez **Disponible avec ou sans inscription**.

    ![Affectations d’applications Intune - Ajouter un groupe](./media/apps-inc-exl-02.png)
10. Sélectionnez **Groupes inclus** pour sélectionner le groupe d’utilisateurs qui peut accéder à cette application.

    > [!NOTE]
    > Quand vous ajoutez un groupe, si un autre groupe a déjà été inclus pour un type d’affectation donné, l’application est présélectionnée et ne peut pas être modifiée pour d’autres types d’affectations d’inclusion. Le groupe déjà utilisé ne peut pas être utilisé comme groupe inclus.

11. Sélectionnez **Oui** pour rendre cette application disponible pour tous les utilisateurs.

    ![Affectations d’applications Intune - Inclure des groupes](./media/apps-inc-exl-03.png)
12. Cliquez sur **OK** pour définir le groupe à inclure.
13. Sélectionnez **Groupes exclus** pour sélectionner les groupes d’utilisateurs ne pouvant pas accéder à cette application. 
14. Sélectionnez les groupes à exclure. Ces groupes n’ont alors pas accès à cette application.

    ![Affectations d’applications Intune - Exclure des groupes](./media/apps-inc-exl-04.png)
15. Cliquez sur **Sélectionner** pour effectuer votre sélection de groupes.
16. Dans le volet **Ajouter un groupe**, sélectionnez **OK**. La liste **Affectations** de l’application s’affiche.
17. Cliquez sur **Enregistrer** pour activer les affectations de groupes pour l’application.

Lorsque vous affectez des groupes, les groupes déjà affectés ne peuvent pas être modifiés. Si vous voulez sélectionner un groupe actuellement indisponible, commencez par supprimer l’application de la liste d’affectations de l’application. 

Pour modifier des affectations, dans la liste **Affectations** de l’application, sélectionnez la ligne qui contient l’affectation spécifique que vous souhaitez modifier. Vous pouvez également supprimer une affectation en sélectionnant les points de suspension (**...**) à la fin d’une ligne, puis en sélectionnant **Supprimer**. Vous pouvez afficher la vue de la liste **Affectations** par **Type d’affectation** ou par **Inclus/exclus**.

![Affectations d’applications Intune - Terminer](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’inclusion et l’exclusion d’affectations de groupes pour les applications, consultez le [blog Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Pour en savoir plus, consultez le [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).
