---
title: Accès conditionnel avec Microsoft Intune
titlesuffix: ''
description: Découvrez comment définir les conditions que les utilisateurs, appareils et applications doivent respecter pour accéder aux ressources d’entreprise dans Microsoft Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/06/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a62166792570c5bb81391d05d1cbc3f8486543a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022337"
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

Intune ajoute des stratégies de conformité des appareils mobiles et de gestion des applications pour prendre en charge la solution d’accès conditionnel d’EMS.

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
