---
title: "Définition des restrictions d’inscription dans Intune | Version préliminaire d’Intune Azure | Microsoft Docs"
description: "Version préliminaire d&quot;Intune Azure : restriction de l’inscription par la plateforme et définition d’une limite d’inscriptions d’appareils dans Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: c4fa22fad4df9c0e4699cf258eb9518a1534bb94
ms.lasthandoff: 02/15/2017

---

# <a name="set-enrollment-restrictions"></a>Définir des restrictions d’inscription 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Vous pouvez définir les types et le nombre maximal d’appareils qui peuvent être inscrits. Dans le panneau Restrictions d’inscription, vous pouvez définir :

- Les plateformes qui peuvent être inscrites et s’il convient de bloquer l’inscription d’appareils personnels iOS et Android.

- Le nombre maximal d’appareils qu’un utilisateur est autorisé à inscrire.

## <a name="set-device-type-restrictions"></a>Définition des restrictions de type d'appareil

1. Dans le portail Azure, choisissez **Plus de services** > **Surveillance + gestion** > **Intune**.

2. Dans le panneau Intune, choisissez **Inscrire des appareils**, puis choisissez **Restrictions d’inscription**.

3. Sous **Restrictions de type d'appareil**, sélectionnez **Par défaut**.

4. Dans le panneau **Tous les utilisateurs**, sélectionnez **plateformes**.

5. Pour les plateformes qui sont autorisées à s’inscrire dans Intune, sélectionnez **Autoriser**. Pour les plateformes pour lesquelles vous souhaitez empêcher l’inscription, sélectionnez **Bloquer**. Les plateformes ont la valeur **Autoriser** par défaut. 

    >[!NOTE]
    >Ces paramètres ne s’appliquent pas aux inscriptions Windows qui utilisent le logiciel client Intune et ne les bloquent pas non plus. Ces paramètres affectent uniquement l’inscription avec la gestion des appareils mobiles. 

6. Sélectionnez **Enregistrer**.

7. Sélectionnez **Configurations des plateformes**.

8. Choisissez **Autoriser** ou **Bloquer** en ce qui concerne l’inscription des appareils personnels iOS et Android.

9. Sélectionnez **Enregistrer**.

## <a name="set-device-limit-restrictions"></a>Définition des restrictions de limite d'appareil

1. Dans le portail Azure, choisissez **Plus de services** > **Surveillance + gestion** > **Intune**.

2. Dans le panneau Intune, choisissez **Inscrire des appareils**, puis choisissez **Restrictions d’inscription**.

3. Sous **Restrictions de limite d’appareil**, sélectionnez **par défaut**.

4. Dans le panneau **Tous les utilisateurs**, sélectionnez **Limite d’appareil**.

5. Sélectionnez le nombre maximal d'appareils qu'un utilisateur peut inscrire, puis sélectionnez **Enregistrer**.

