---
title: Configurer des stratégies de protection des applications pendant une migration
titleSuffix: Microsoft Intune
description: Cet article décrit les étapes nécessaires pour configurer des stratégies de protection des applications pendant une migration Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c0571eb2a369e440b3c7732b6d55ba05ace2c34
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839354"
---
# <a name="configure-app-protection-policies-optional"></a>Configurer des stratégies de protection des applications (facultatif)


Les stratégies de protection des applications vous permettent de :
* chiffrer les applications ;
* définir un code PIN au moment où un utilisateur accède à l’application ;
* empêcher les applications de s’exécuter sur des appareils jailbreakés ou rootés et bien d’autres protections.

Si le téléphone de l’utilisateur est perdu ou volé, vous pouvez effacer à distance les données de l’entreprise tout en gardant intactes les données personnelles.

Les stratégies de protection des applications mettent en œuvre des mécanismes de sécurité au niveau de l’application. Vous n’avez pas besoin d’inscrire l’appareil. Vous pouvez les utiliser avec les appareils, qu’ils soient ou non inscrits sur Intune. Par ailleurs, vous pouvez les appliquer aux appareils inscrits auprès d’un fournisseur MDM tiers.

## <a name="app-protection-policies-with-lob-apps"></a>Stratégies de protection des applications et applications métier

Vous pouvez aussi étendre les stratégies de protection des applications mobiles à vos applications métier en utilisant le [Kit de développement logiciel (SDK) d’applications Microsoft Intune](../developer/app-sdk-get-started.md) ou l’outil de création de packages d’applications Microsoft Intune pour les plateformes iOS et Android. Pour plus d’informations, consultez les sections [Outil de création de packages d’applications pour iOS](../developer/app-wrapper-prepare-ios.md) et [Outil de création de packages d’applications pour Android](./../developer/app-wrapper-prepare-android.md). Consultez également la section [Préparer des applications métier pour la protection des applications](../developer/apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>De quelle manière les stratégies de protection des applications facilitent-elles la migration ?

Durant une migration, vous devez retirer les appareils de l’ancien fournisseur MDM et les inscrire dans Intune. Cette opération nécessite une planification précise. Invitez les utilisateurs finaux à désinscrire leurs appareils et à les inscrire immédiatement auprès de Microsoft Intune. Toutefois, il se peut que certains utilisateurs, dont les appareils ne sont pas gérés par l’ancien fournisseur, n’effectuent pas immédiatement la migration vers Intune.

Pendant cet intervalle, votre organisation risque d’être plus vulnérable au vol d’appareils et à la perte de données d’entreprise si l’accès aux ressources reste autorisé. De même, la productivité des utilisateurs peut pâtir du blocage de l’accès aux ressources de l’entreprise.

Intune propose différents mécanismes de protection des données d’entreprise lors de la migration, afin que ces données restent sécurisées si aucune gestion des appareils n’est mise en place.

Lorsque vous désactivez l’accès conditionnel dans l’ancien fournisseur MDM, les utilisateurs peuvent continuer à travailler pendant que vous les intégrez à Intune.

## <a name="task-list-for-app-protection-policies"></a>Liste des tâches associées aux stratégies de protection des applications

- [Guide pratique pour créer et affecter des stratégies de protection des applications](~/apps/app-protection-policies.md)

## <a name="next-steps"></a>Étapes suivantes

[Facteurs de migration spécifiques à prendre en compte](migration-guide-considerations.md)
