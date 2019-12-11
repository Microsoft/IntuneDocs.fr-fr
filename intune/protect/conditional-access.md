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
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188274"
---
# <a name="learn-about-conditional-access-and-intune"></a>En savoir plus sur l’accès conditionnel et Intune

Avec l’accès conditionnel, vous pouvez contrôler les appareils et les applications qui peuvent se connecter à vos ressources d’entreprise et de messagerie. 

Enterprise Mobility + Security (EMS) n’est pas un produit autonome. Cette solution fait partie de tous les services et produits qui d’EMS. L’accès conditionnel offre un contrôle d’accès granulaire pour sécuriser vos données d’entreprise, tout en donnant aux utilisateurs une expérience qui leur permet d’effectuer leur travail au mieux à partir de n’importe quel appareil et de n’importe quel emplacement.

Vous pouvez définir des conditions qui contrôlent l’accès à vos données d’entreprise en fonction de l’emplacement, l’état de l'appareil et de l’utilisateur, et la sensibilité de l’application.

> [!NOTE]
> L’accès conditionnel étend également ses fonctionnalités aux [services Office 365](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access).

![Diagramme de l’accès conditionnel](./media/conditional-access/ca-diagram-1.png)

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
