---
title: Client PC Intune hérité et Intune sur Azure
description: Considérations relatives à l’utilisation d’Intune dans Azure pour gérer les appareils Windows de votre organisation.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 27f3a184e355f63d20a79fd92e8326206f6eee15
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185625"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune dans la console Azure et client PC Intune hérité

Intune utilise une architecture de services d’application SaaS basée sur Azure. Azure inclut des améliorations significatives en termes de mise à l’échelle, de capacité et de performances. Elles offrent des expériences d’administration Intune améliorées et des workflows optimisés dans le portail Azure. 

Lors de l’utilisation d’Intune dans Azure pour gérer les appareils Windows de votre organisation, tenez compte des points suivants :

## <a name="manage-windows-10-devices-by-using-mdm"></a>Gérer les appareils Windows 10 via MDM

Nous vous recommandons d’utiliser la [gestion des appareils mobiles (MDM) pour gérer vos appareils Windows 10](https://docs.microsoft.com/intune/device-restrictions-windows-10) au lieu d’utiliser le client PC Intune hérité. La capacité à gérer Windows 10 via MDM est disponible dans Intune sur le portail Azure. La MDM sous Windows 10 fournit un grand nombre de nouvelles fonctions de gestion et de sécurité qui ne sont pas disponibles via le PC client Intune hérité.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Les fonctionnalités du PC client hérité sont uniquement disponibles dans la console Silverlight

Les workflows de gestion du PC client Intune utilisent la [Console d’administration Intune basée sur Silverlight](https://manage.microsoft.com/), ce qui implique les exigences suivantes :

- Pour toutes les tâches de gestion non groupées à l’aide du PC client Intune, vous devez utiliser la console Silverlight.
- Lors de la gestion de groupes, vous devez utiliser [Intune dans le portail Azure](https://portal.azure.com/). Cette exigence s’explique par le fait qu’Intune utilise désormais les groupes Azure AD au lieu des groupes Intune hérités. 

Suite à ce passage aux groupes Azure AD, le filtrage « basé sur les groupes » dans les affichages du tableau de bord de la console Silverlight a légèrement changé. Pour effectuer un filtrage dans l’interface utilisateur de Silverlight mise à jour, procédez comme suit :

1. Sélectionnez un affichage.
2. Dans la zone **Filtres**, entrez le nom du groupe à filtrer et appuyez sur la touche Entrée. La liste ainsi filtrée affichera uniquement les appareils appartenant à ce groupe.

   ![](media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Continuer à gérer Windows 7 via le PC client Intune

Pour Windows 7, qui ne peut pas être géré via MDM, nous continuerons à prendre en charge les fonctions du PC client Intune existantes uniquement dans la console de Silverlight. Nous vous conseillons d’envisager de passer à la gestion MDM lors de votre mise à niveau vers Windows 10.

## <a name="mdm-capabilities"></a>Fonctions MDM

Pour obtenir une comparaison détaillée entre les fonctions du PC client et les fonctions MDM, consultez [Comparer la gestion des PC Windows en tant qu’ordinateurs ou appareils mobiles](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison). Les mises à jour MDM continueront à introduire de nouvelles fonctions de gestion pour les appareils Windows 10 inscrits auprès de la MDM, notamment des options d’évaluation pour les applications Win 32. Consultez [Nouveautés](https://docs.microsoft.com/intune/whats-new) pour connaître les derniers ajouts de version à ce service.

## <a name="switch-from-pc-client-to-mdm"></a>Passer du PC client à la MDM

Pour passer de la gestion des appareils Windows 10 via le PC client Intune à la gestion via MDM, procédez comme suit :

1. Dans la console de Silverlight, effectuez une **réinitialisation sélective** pour désinscrire l’appareil du PC client.
  ![](media/intune-legacy-pc-client/image02.png)
2. Réinscrivez l’appareil à l’aide de la [MDM (et/ou Azure AD Join)](https://docs.microsoft.com/intune/windows-enroll). 

## <a name="next-steps"></a>Étapes suivantes
[Inscrire des appareils Windows](https://docs.microsoft.com/intune/windows-enroll)

 
