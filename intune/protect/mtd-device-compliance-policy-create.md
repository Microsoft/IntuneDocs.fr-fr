---
title: Créer une stratégie de conformité des appareils MTD avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Créez une stratégie de conformité des appareils Intune qui utilise les niveaux de menace MTD partenaires afin de déterminer si un appareil mobile peut accéder aux ressources de l’entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2315136fe277f06f6dbb11c13139a9dc193ce6f7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722109"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Créer une stratégie de conformité des appareils Mobile Threat Defense (MTD) avec Intune

> [!NOTE] 
> Ces informations s’appliquent à tous les partenaires Mobile Threat Defense.

Intune avec MTD vous aide à détecter les menaces et à évaluer les risques sur les appareils mobiles. Vous pouvez créer une règle de stratégie de conformité de l’appareil Intune qui évalue les risques et détermine si l’appareil est conforme. Vous pouvez ensuite utiliser une [stratégie d’accès conditionnel](create-conditional-access-intune.md) pour autoriser ou bloquer l’accès à des services en fonction de la conformité de l’appareil.

## <a name="before-you-begin"></a>Avant de commencer

Dans le cadre de l’installation de MTD, dans la console de partenaire MTD, vous avez créé une stratégie qui classe les diverses menaces d’après leur gravité : élevée, moyenne et faible. Vous devez maintenant définir le niveau Mobile Threat Defense dans la stratégie de conformité de l’appareil Intune.

Conditions préalables pour la stratégie de conformité de l’appareil avec MTD :

- Configurer l’intégration de MTD avec Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Pour créer une stratégie de conformité de l’appareil MTD

1. Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous avec vos informations d’identification Intune.

2. Dans le **tableau de bord Azure**, choisissez **Tous les services** dans le menu de gauche, puis tapez **Intune** dans le filtre de la zone de texte.

3. Choisissez **Intune**. Le **Tableau de bord Intune** s’ouvre.

4. Dans le **Tableau de bord Intune**, choisissez **Conformité de l’appareil**, puis choisissez **Stratégies** dans la section **Gérer**.

5. Choisissez **Créer une stratégie**, entrez le **Nom** de la stratégie de conformité d’appareil, sa **Description**, sélectionnez la **Plateforme**, puis choisissez **Configurer** dans la section **Paramètres**.

6. Dans le volet **Stratégie de conformité**, choisissez **Intégrité de l’appareil**.

7. Dans le volet **Intégrité de l’appareil**, choisissez le niveau de menace mobile dans la liste déroulante sous **Exiger que l’appareil se situe au Niveau de menace pour l'appareil ou en dessous**.

    a.  **Sécurisé** : ce niveau est le plus sûr. L'appareil ne peut pas avoir de menace présente et accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.

    b.  **Faible** : l’appareil est conforme seulement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.

    c.  **Moyen** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.

    d.  **Élevé** : ce niveau est le moins sûr. Cela active tous les niveaux de menace et utilise la défense contre les menaces mobiles uniquement à des fins de création de rapport. L’application MTD doit être activée avec ce paramètre sur les appareils.

8. Cliquez sur **OK** à deux reprises, puis choisissez **Créer**.

> [!IMPORTANT]
> Si vous créez des stratégies d’accès conditionnel pour Office 365 ou d’autres services, l’évaluation de la conformité de l’appareil est effectuée et les appareils non conformes ne peuvent pas accéder aux ressources d’entreprise tant que la menace n’est pas résolue sur l’appareil.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Pour affecter une stratégie de conformité de l’appareil MTD

Pour affecter une stratégie de conformité de l’appareil à des utilisateurs, choisissez une stratégie que vous avez déjà configurée. Vous trouverez les stratégies existantes dans le volet **Conformité de l’appareil – stratégies**.

1. Choisissez la stratégie que vous souhaitez attribuer aux utilisateurs, puis **Affectations**. Cette action ouvre le volet où vous pouvez sélectionner des **Groupes de sécurité Azure Active Directory** et les assigner à la stratégie.

2. Choisissez **Sélectionner des groupes à inclure** pour ouvrir le volet qui affiche les groupes de sécurité Azure AD.  Si vous choisissez **Sélectionner**, la stratégie est déployée pour les utilisateurs.

    > [!NOTE] 
    > Vous avez appliqué la stratégie à des utilisateurs. La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie est évaluée.

## <a name="next-steps"></a>Étapes suivantes

- [Activer MTD avec Intune](mtd-connector-enable.md)
