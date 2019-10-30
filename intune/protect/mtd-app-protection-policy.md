---
title: Créer une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Intune
titleSuffix: Microsoft Intune
description: Créez une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794418"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Créer une stratégie de protection d’applications Mobile Threat Defense avec Intune

> [!NOTE] 
> Cet article s’applique à tous les partenaires Mobile Threat Defense (MTD) qui prennent en charge des stratégies de protection d’applications : Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

Intune avec MTD vous aide à détecter les menaces et à évaluer les risques sur les appareils mobiles. Vous pouvez créer une stratégie de protection d’applications Intune qui évaluera les risques pour déterminer si l’appareil sera autorisé à accéder aux données d’entreprise. 

## <a name="before-you-begin"></a>Avant de commencer

Dans le cadre de l’installation de MTD, dans la console de partenaire MTD, vous avez créé une stratégie qui classe les diverses menaces d’après leur gravité : élevée, moyenne et faible. Vous devez maintenant définir le niveau Mobile Threat Defense dans la stratégie de protection d’applications Intune.

Prérequis pour la stratégie de protection d’applications avec MTD :

- Configurez l’intégration de MTD avec Intune. Sans cette intégration, la stratégie de protection d’applications MTD n’aura aucun effet.

## <a name="to-create-an-mtd-app-protection-policy"></a>Pour créer une stratégie de protection d’applications MTD

1. Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous avec vos informations d’identification Intune.

2. Dans le **tableau de bord Azure**, choisissez **Tous les services** dans le menu de gauche, puis tapez **Intune** dans le filtre de la zone de texte.

3. Choisissez **Intune**. Le **Tableau de bord Intune** s’ouvre.

4. Dans le **Tableau de bord Intune**, choisissez **Applications clientes**, puis choisissez **Stratégies de protection des applications** sous la section **Gérer**.

5. Choisissez **Créer une stratégie**, entrez un **nom** et une **description**, et sélectionnez la **plateforme**. 

6. Dans le volet **Lancement conditionnel**, sous le tableau **Conditions de l’appareil**, choisissez le niveau de menace pour l’appareil dans la liste déroulante sous **Niveau de menace maximal autorisé pour l’appareil**.

    a.  **Sécurisé** : ce niveau est le plus sûr. L'appareil ne peut pas avoir de menace présente et accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.

    b.  **Faible** : l’appareil est conforme seulement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.

    c.  **Moyen** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.

    d.  **Élevé** : ce niveau est le moins sûr. Cela active tous les niveaux de menace et utilise la défense contre les menaces mobiles uniquement à des fins de création de rapport. L’application MTD doit être activée avec ce paramètre sur les appareils.

7. Cliquez sur **Enregistrer** à deux reprises, puis choisissez **Créer**.

## <a name="to-assign-an-mtd-app-protection-policy"></a>Pour affecter une stratégie de protection des applications MTD

Pour affecter une stratégie de conformité de l’appareil à des utilisateurs, choisissez une stratégie que vous avez déjà configurée. Vous trouverez les stratégies existantes dans le volet **Conformité de l’appareil – stratégies**.

1. Choisissez la stratégie que vous souhaitez attribuer aux utilisateurs, puis **Affectations**. Cette action ouvre le volet où vous pouvez sélectionner des **groupes de sécurité Azure Active Directory** et les affecter à la stratégie.

2. Choisissez **Sélectionner les groupes à inclure** pour ouvrir le volet qui affiche les groupes de sécurité Azure AD. Si vous choisissez **Sélectionner**, la stratégie est déployée pour les utilisateurs.

> [!NOTE] 
> Vous avez appliqué la stratégie à des utilisateurs. Les appareils utilisés par les utilisateurs ciblés par la stratégie sont évalués concernant l’accès aux données d’entreprise sur les applications ciblées via la protection des applications Intune.

## <a name="next-steps"></a>Étapes suivantes  

- Découvrez plus en détail [Mobile Threat Defense](~/protect/mobile-threat-defense.md) dans Microsoft Intune.
