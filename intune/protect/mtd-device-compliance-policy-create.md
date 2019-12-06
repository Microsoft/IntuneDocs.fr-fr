---
title: Créer une stratégie de conformité des appareils MTD avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Créez une stratégie de conformité des appareils Intune qui utilise les niveaux de menace MTD partenaires afin de déterminer si un appareil mobile peut accéder aux ressources de l’entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409699"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Créer une stratégie de conformité des appareils Mobile Threat Defense (MTD) avec Intune

Intune avec MTD vous aide à détecter les menaces et à évaluer les risques sur les appareils mobiles. Vous pouvez créer une règle de stratégie de conformité de l’appareil Intune qui évalue les risques et détermine si l’appareil est conforme. Vous pouvez ensuite utiliser une [stratégie d’accès conditionnel](create-conditional-access-intune.md) pour autoriser ou bloquer l’accès à des services en fonction de la conformité de l’appareil.

> [!NOTE]
> Ces informations s’appliquent à tous les partenaires Mobile Threat Defense.

## <a name="before-you-begin"></a>Avant de commencer

Dans le cadre de l’installation de MTD, dans la console de partenaire MTD, vous avez créé une stratégie qui classe les diverses menaces d’après leur gravité : élevée, moyenne et faible. Vous devez maintenant définir le niveau Mobile Threat Defense dans la stratégie de conformité de l’appareil Intune.

Conditions préalables pour la stratégie de conformité de l’appareil avec MTD :

- Configurer l’intégration de MTD avec Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Pour créer une stratégie de conformité de l’appareil MTD

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Stratégies de conformité** > **Créer une stratégie**.

3. Spécifiez un **Nom** et une **Description** pour la stratégie de conformité des appareils, sélectionnez la **Plateforme**, puis **Configurer** dans la section **Paramètres**.

4. Dans le volet **Stratégie de conformité**, choisissez **Intégrité de l’appareil**.

5. Dans le volet **Intégrité de l’appareil**, choisissez le niveau de menace mobile dans la liste déroulante pour **Exiger que l’appareil se situe au Niveau de menace pour l'appareil ou en dessous**.

   - **Sécurisé** : ce niveau est le plus sûr. L'appareil ne peut pas avoir de menace présente et accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.

   - **Faible** : l’appareil est conforme seulement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.

   - **Moyen** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.

   - **Élevé** : ce niveau est le moins sûr. Cela active tous les niveaux de menace et utilise la défense contre les menaces mobiles uniquement à des fins de création de rapport. L’application MTD doit être activée avec ce paramètre sur les appareils.

6. Sélectionnez **OK** deux fois, puis **Créer** pour créer la stratégie.

> [!IMPORTANT]
> Si vous créez des stratégies d’accès conditionnel pour Office 365 ou d’autres services, l’évaluation de la conformité de l’appareil est effectuée et les appareils non conformes ne peuvent pas accéder aux ressources d’entreprise tant que la menace n’est pas résolue sur l’appareil.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Pour affecter une stratégie de conformité de l’appareil MTD

Pour affecter une stratégie de conformité de l’appareil aux utilisateurs :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareil** > **Stratégies de conformité**.

3. Sélectionnez la stratégie que vous souhaitez affecter aux utilisateurs, puis sélectionnez **Affectations**. Utilisez les options disponibles pour *Inclure* et *Exclure* les groupes pour déterminer qui recevra cette stratégie.  

4. Sélectionnez Enregistrer pour terminer l’attribution. Lorsque vous enregistrez l’attribution, la stratégie est déployée sur les utilisateurs sélectionnés et leurs appareils sont évalués pour conformité.

## <a name="next-steps"></a>Étapes suivantes

[Activer MTD avec Intune](mtd-connector-enable.md)
