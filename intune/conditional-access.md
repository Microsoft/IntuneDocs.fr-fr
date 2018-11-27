---
title: Accès conditionnel avec Microsoft Intune
titlesuffix: ''
description: Découvrez comment définir les conditions que les utilisateurs, appareils et applications doivent respecter pour accéder aux ressources d’entreprise dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 1e9e8db76978f9547d10fd4709d74ea809f2c281
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184843"
---
# <a name="whats-conditional-access"></a>Qu’est-ce que l’accès conditionnel ?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L’accès conditionnel fait référence aux moyens grâce auxquels vous pouvez contrôler les appareils et les applications qui sont autorisés à se connecter à vos ressources d’entreprise et de messagerie. Dans cette rubrique, vous allez découvrir ce qu’est l’accès conditionnel basé sur l’application et basé sur l’appareil, et découvrir des scénarios courants d’utilisation de l’accès conditionnel avec Intune.

L’accès conditionnel d’Enterprise Mobility + Security (EMS) n’est pas un produit autonome, il s’agit d’une solution qui tire parti de tous les services et produits qui font partie de la suite EMS. Il offre un contrôle d’accès granulaire pour sécuriser vos données d’entreprise, tout en donnant aux utilisateurs une expérience qui leur permet d’effectuer leur travail au mieux à partir de n’importe quel appareil et de n’importe quel emplacement.

Vous pouvez définir des conditions qui contrôlent l’accès à vos données d’entreprise en fonction de l’emplacement, l’état de l'appareil et de l’utilisateur, et la sensibilité de l’application.

> [!NOTE] 
> L’accès conditionnel étend également ses fonctionnalités aux [services Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Diagramme architectural de l’accès conditionnel](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Accès conditionnel avec Intune

L’accès conditionnel est une fonctionnalité d’Azure Active Directory fournie avec la licence Azure Active Directory Premium. Intune améliore cette fonctionnalité en ajoutant la conformité des appareils mobiles et la gestion des applications mobiles à la solution. 

![Intune et accès conditionnel lors de l’utilisation d’EMS](./media/intune-with-ca-1.png)

Moyens d’utilisation de l’accès conditionnel avec Intune :

-   **Accès conditionnel basé sur l’appareil**

    -   Accès conditionnel pour Exchange sur site

    -   Accès conditionnel basé sur le contrôle d’accès réseau

    -   Accès conditionnel basé sur les risques que présente l’appareil

    -   Accès conditionnel pour les PC Windows

        -   Appartenant à l’entreprise

        -   Apportez votre propre appareil (BYOD)

-   **Accès conditionnel basé sur l’application**

## <a name="next-steps"></a>Étapes suivantes

[Utilisations courantes de l’accès conditionnel avec Intune](conditional-access-intune-common-ways-use.md)
