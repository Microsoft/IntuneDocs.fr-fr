---
title: Accès conditionnel avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Découvrez comment définir les conditions que les utilisateurs, appareils et applications doivent respecter pour accéder aux ressources d’entreprise dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb9dd31c87d27ec7885d25269988cfd968e81e08
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504567"
---
# <a name="learn-about-conditional-access-and-intune"></a>En savoir plus sur l’accès conditionnel et Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L’accès conditionnel fait référence aux moyens grâce auxquels vous pouvez contrôler les appareils et les applications qui sont autorisés à se connecter à vos ressources d’entreprise et de messagerie. Dans cette rubrique, vous allez découvrir ce qu’est l’accès conditionnel basé sur l’application et basé sur l’appareil, et découvrir des scénarios courants d’utilisation de l’accès conditionnel avec Intune.

L’accès conditionnel d’Enterprise Mobility + Security (EMS) n’est pas un produit autonome, il s’agit d’une solution qui tire parti de tous les services et produits qui font partie de la suite EMS. Il offre un contrôle d’accès granulaire pour sécuriser vos données d’entreprise, tout en donnant aux utilisateurs une expérience qui leur permet d’effectuer leur travail au mieux à partir de n’importe quel appareil et de n’importe quel emplacement.

Vous pouvez définir des conditions qui contrôlent l’accès à vos données d’entreprise en fonction de l’emplacement, l’état de l'appareil et de l’utilisateur, et la sensibilité de l’application.

> [!NOTE] 
> L’accès conditionnel étend également ses fonctionnalités aux [services Office 365](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access).

![Diagramme architectural de l’accès conditionnel](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Utiliser l’accès conditionnel avec Intune

L’accès conditionnel est une fonctionnalité d’Azure Active Directory fournie avec la licence Azure Active Directory Premium. Intune améliore cette fonctionnalité en ajoutant la conformité des appareils mobiles et la gestion des applications mobiles à la solution. 

![Intune et accès conditionnel lors de l’utilisation d’EMS](./media/conditional-access/intune-with-ca-1.png)

Moyens d’utilisation de l’accès conditionnel avec Intune :

- **Accès conditionnel basé sur l’appareil**

  - Accès conditionnel pour Exchange sur site

  - Accès conditionnel basé sur le contrôle d’accès réseau

  - Accès conditionnel basé sur les risques que présente l’appareil

  - Accès conditionnel pour les PC Windows

    - Appartenant à l’entreprise

    - Apportez votre propre appareil (BYOD)

- **Accès conditionnel basé sur l’application**

## <a name="next-steps"></a>Étapes suivantes

[Utilisations courantes de l’accès conditionnel avec Intune](conditional-access-intune-common-ways-use.md)
