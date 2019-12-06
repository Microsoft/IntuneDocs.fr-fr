---
title: Inclure et exclure des affectations d’applications dans Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser Microsoft Intune pour inclure et exclure des affectations d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f073c8ad7a8e087a791ee756683011fac6947162
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547963"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inclure et exclure des affectations d’applications dans Microsoft Intune

Dans Intune, vous pouvez déterminer qui a accès à une application en affectant des groupes d’utilisateurs à inclure et à exclure. Avant d’affecter des groupes à l’application, vous devez définir le type d’affectation d’une application. Le type d’affectation rend l’application disponible, obligatoire ou la désinstalle. 

Pour définir la disponibilité d’une application, vous incluez et excluez des affectations d’applications à un groupe d’utilisateurs ou d’appareils à l’aide d’une combinaison d’affectations de groupes d’inclusion et d’exclusion. Cette fonctionnalité est utile quand vous rendez l’application disponible en incluant un grand groupe, puis que vous affinez les utilisateurs sélectionnés en excluant un groupe plus petit. Le groupe plus petit peut être un groupe de test ou un groupe exécutif. 

Il est recommandé de créer et d’affecter des applications spécifiquement pour vos groupes d’utilisateurs, et séparément pour vos groupes d’appareils. Pour plus d’informations sur les groupes, voir [Ajouter des groupes pour organiser les utilisateurs et les appareils](~/fundamentals/groups-add.md).  

Il existe des scénarios importants lorsque vous incluez ou excluez des affectations d’applications :

- L’exclusion est prioritaire sur l’inclusion dans les scénarios « même type de groupe » suivants :
    - Inclure des groupes d’utilisateurs et exclure des groupes d’utilisateurs lors de l’affectation d’applications
    - Inclure des groupes d’appareils et exclure des groupes d’appareils lors de l’affectation d’applications

    Par exemple, si vous affectez un groupe d’appareils au groupe **Tous les utilisateurs d’entreprise**, mais excluez les membres du groupe **Cadres supérieurs**, **tous les utilisateurs de l’entreprise** à l’exception des **cadres supérieurs** obtiennent l’attribution, car les deux groupes sont des groupes d’utilisateurs.
- Intune n’évalue pas les relations entre groupes d’utilisateurs et groupes d’appareils. Si vous affectez des applications à des groupes mixtes, les résultats risquent de ne pas correspondre à votre intention ou à vos attentes.

    Supposons par exemple que vous affectiez un groupe d’appareils au groupe d’utilisateurs **Tous les utilisateurs**, mais que vous excluiez un groupe d’appareils **Tous les appareils personnels**. Dans cette affectation d’application de groupe mixte, **Tous les utilisateurs** reçoivent l’application. L’exclusion ne s’applique pas.

Par conséquent, il n’est pas recommandé d’affecter des applications à des groupes mixtes.

> [!NOTE]
> Quand vous définissez une affectation de groupe pour une application, le type **Non applicable** est déprécié et remplacé par la fonctionnalité d’exclusion de groupe. 
>
> Intune fournit des groupes **Tous les utilisateurs** et **Tous les appareils** précréés dans la console. Les groupes ont des optimisations intégrées pour votre confort. Nous vous recommandons vivement d’utiliser ces groupes pour cibler tous les utilisateurs et tous les appareils au lieu de créer vous-même des groupes « Tous les utilisateurs » ou « Tous les appareils ».  
>
> Android Enterprise prend en charge l’inclusion et l’exclusion de groupes. Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications Android Entreprise. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Inclure et exclure des groupes lors de l’affectation d’applications 
Pour affecter une application à des groupes à l’aide de l’affectation d’inclusion et d’exclusion :
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet **Applications clientes**, sélectionnez **Applications**. La liste des applications ajoutées s’affiche.
5. Sélectionnez l’application que vous voulez attribuer. Un tableau de bord contient des informatinos sur l’application. 
6. Dans la section **Gérer** du menu, sélectionnez **Affectations**. 

    ![Inclure les affectations d’applications lors des affectations d’applications](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. Sélectionnez **Ajouter un groupe** pour ajouter les groupes d’utilisateurs affectés à l’application. 
8. Dans le volet **Ajouter un groupe**, sélectionnez un **Type d’affectation** parmi les types d’affectations disponibles.
9. Comme type d’affectation, sélectionnez **Disponible avec ou sans inscription**.

    ![Affectations d’applications Intune - Ajouter un groupe](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. Sélectionnez **Groupes inclus** pour sélectionner le groupe d’utilisateurs qui peut accéder à cette application.

    > [!NOTE]
    > Quand vous ajoutez un groupe, si un autre groupe a déjà été inclus pour un type d’affectation donné, l’application est présélectionnée et ne peut pas être modifiée pour d’autres types d’affectations d’inclusion. Le groupe déjà utilisé ne peut pas être utilisé comme groupe inclus.

11. Sélectionnez **Oui** pour rendre cette application disponible pour tous les utilisateurs.

    ![Affectations d’applications Intune - Inclure des groupes](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. Cliquez sur **OK** pour définir le groupe à inclure.
13. Sélectionnez **Groupes exclus** pour sélectionner les groupes d’utilisateurs ne pouvant pas accéder à cette application. 
14. Sélectionnez les groupes à exclure. Ces groupes n’ont alors pas accès à cette application.

    ![Affectations d’applications Intune - Exclure des groupes](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. Cliquez sur **Sélectionner** pour effectuer votre sélection de groupes.
16. Dans le volet **Ajouter un groupe**, sélectionnez **OK**. La liste **Affectations** de l’application s’affiche.
17. Cliquez sur **Enregistrer** pour activer les affectations de groupes pour l’application.

Lorsque vous affectez des groupes, les groupes déjà affectés ne peuvent pas être modifiés. Si vous voulez sélectionner un groupe actuellement indisponible, commencez par supprimer l’application de la liste d’affectations de l’application. 

Pour modifier des affectations, dans la liste **Affectations** de l’application, sélectionnez la ligne qui contient l’affectation spécifique que vous souhaitez modifier. Vous pouvez également supprimer une affectation en sélectionnant les points de suspension ( **...** ) à la fin d’une ligne, puis en sélectionnant **Supprimer**. Vous pouvez afficher la vue de la liste **Affectations** par **Type d’affectation** ou par **Inclus/exclus**.

![Affectations d’applications Intune - Terminer](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’inclusion et l’exclusion d’affectations de groupes pour les applications, consultez le [blog Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Pour en savoir plus, consultez le [Guide pratique pour surveiller les affectations et les informations d’applications](apps-monitor.md).
