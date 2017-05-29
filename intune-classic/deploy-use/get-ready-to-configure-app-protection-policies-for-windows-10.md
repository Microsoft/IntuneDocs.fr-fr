---
title: "Préparer la configuration des stratégies de protection d’application pour Windows 10 | Microsoft Docs"
description: Configuration du fournisseur de gestion des applications mobiles dans Azure AD
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ebc7cfc8-40b9-47c2-8357-d392ebbb27c8
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c48f9181e8fd740ab080a8620f3873909d0fd0f1
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Préparer la configuration des stratégies de protection d’application pour Windows 10

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Avant de créer une stratégie de protection d’application Windows 10, vous devez activer la gestion des applications mobiles (MAM) pour Windows 10 en définissant le fournisseur MAM dans Azure AD. Cette configuration vous permet de définir l’état d’inscription lors de la création d’une nouvelle stratégie de Protection des informations Windows (WIP) avec Intune.

> [!NOTE]
> L’état de l’inscription peut être MAM ou gestion des appareils mobiles (MDM).

## <a name="to-configure-the-mam-provider"></a>Pour configurer le fournisseur MAM

1.  Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous avec vos informations d’identification Intune.

2.  Dans le menu de gauche, choisissez **Azure Active Directory**.

    ![Configuration du fournisseur MAM](../media/AppManagement/mam-provider-sc-1.png)

3.  Le panneau **Azure AD** s’ouvre, choisissez **Mobilité (MDM et MAM)**, puis cliquez sur **Microsoft Intune**.

    ![Mobilité (gestion des données de référence et gestion des applications mobiles)](../media/AppManagement/mam-provider-sc-2.png)

4.  Le volet Configuration s’ouvre, choisissez d’abord **Restaurer les URL MAM par défaut**, puis configurez ce qui suit :

    a.  Étendue des utilisateurs MAM : vous pouvez utiliser MAM pour protéger des données d’entreprise sur un groupe spécifique d’utilisateurs qui utilisent des appareils Windows 10, ou tous les utilisateurs.

    b.  URL de conditions d’utilisation de MAM : l’URL des conditions d’utilisation du service MAM. Permet d’afficher les conditions de service MAM pour les utilisateurs finaux.

    c.  URL de découverte MAM : il s’agit de l’URL que les appareils recherchent lorsqu’ils ont besoin appliquer des stratégies de protection d’application.

    d.  URL de conformité MAM :

5.  Une fois ces paramètres configurés, cliquez sur **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

[Créer une stratégie de protection d’application WIP](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune)

