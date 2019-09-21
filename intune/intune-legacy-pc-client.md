---
title: Client PC Intune hérité et Intune sur Azure
description: Considérations relatives à l’utilisation d’Intune dans Azure pour gérer les appareils Windows de votre organisation.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3891ce150ea740baa3ba18591139c66d78d9d00
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166370"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune dans la console Azure et client PC Intune hérité

Intune utilise une architecture de services d’application SaaS basée sur Azure. Azure inclut des améliorations significatives en termes de mise à l’échelle, de capacité et de performances. Elles offrent des expériences d’administration Intune améliorées et des workflows optimisés dans le portail Azure. 

Lors de l’utilisation d’Intune dans Azure pour gérer les appareils Windows de votre organisation, tenez compte des points suivants :

## <a name="manage-windows-10-devices-by-using-mdm"></a>Gérer les appareils Windows 10 via GPM

Nous vous recommandons d’utiliser la [gestion des périphériques mobiles (GPM) pour gérer vos appareils Windows 10](device-restrictions-windows-10.md) au lieu d’utiliser le PC client Intune hérité. La capacité à gérer Windows 10 via GPM est disponible dans Intune sur le portail Azure. La GPM sous Windows 10 fournit un grand nombre de nouvelles fonctions de gestion et de sécurité qui ne sont pas disponibles via le PC client Intune hérité.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Les fonctionnalités du PC client hérité sont uniquement disponibles dans la console Silverlight

Les workflows de gestion du PC client Intune utilisent la [Console d’administration Intune basée sur Silverlight](https://manage.microsoft.com/), ce qui implique les exigences suivantes :

- Pour toutes les tâches de gestion non groupées à l’aide du PC client Intune, vous devez utiliser la console Silverlight.
- Lors de la gestion de groupes, vous devez utiliser [Intune dans le portail Azure](https://portal.azure.com/). Cette exigence s’explique par le fait qu’Intune utilise désormais les groupes Azure AD au lieu des groupes Intune hérités. 

Suite à ce passage aux groupes Azure AD, le filtrage « basé sur les groupes » dans les affichages du tableau de bord de la console Silverlight a légèrement changé. Pour effectuer un filtrage dans l’interface utilisateur de Silverlight mise à jour, procédez comme suit :

1. Sélectionnez un affichage.
2. Dans la zone **Filtres**, entrez le nom du groupe à filtrer et appuyez sur la touche Entrée. La liste ainsi filtrée affichera uniquement les appareils appartenant à ce groupe.

   ![Entrée de la liste déroulante des filtres avec aucun sélectionné](media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Continuer à gérer Windows 7 via le PC client Intune

Pour Windows 7, qui ne peut pas être géré via GPM, nous continuerons à prendre en charge les fonctions du PC client Intune existantes uniquement dans la console de Silverlight. Nous vous conseillons d’envisager de passer à la gestion GPM lors de votre mise à niveau vers Windows 10.

## <a name="mdm-capabilities"></a>Fonctions GPM

Pour obtenir une comparaison détaillée entre les fonctions du PC client et les fonctions GPM, consultez [Comparer la gestion des PC Windows en tant qu’ordinateurs ou appareils mobiles](pc-management-comparison.md). Les mises à jour GPM continueront à introduire de nouvelles fonctions de gestion pour les appareils Windows 10 inscrits auprès de la GPM, notamment des options d’évaluation pour les applications Win 32. Consultez [Nouveautés](whats-new.md) pour connaître les derniers ajouts de version à ce service.

## <a name="switch-from-pc-client-to-mdm"></a>Passer du PC client à la GPM

Pour passer de la gestion des appareils Windows 10 via le PC client Intune à la gestion via GPM, procédez comme suit :

1. Dans la console de Silverlight, effectuez une **réinitialisation sélective** pour désinscrire l’appareil du PC client.
  ![Menu contextuel d’avertissement avec la case d’option « Réinitialiser sélectivement l’appareil » sélectionnée](media/intune-legacy-pc-client/image02.png)
2. Réinscrivez l’appareil à l’aide de la [GPM (et/ou Azure AD Join)](windows-enroll.md).

## <a name="next-steps"></a>Étapes suivantes
[Inscrire des appareils Windows](windows-enroll.md)
