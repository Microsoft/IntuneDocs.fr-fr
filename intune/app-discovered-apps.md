---
title: Applications découvertes
titleSuffix: Microsoft Intune
description: Découvrez les informations détaillées sur les applications détectées qu’Intune a trouvées sur un appareil.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53555a01899cfec15c319e790620b2bfeaa302bc
ms.sourcegitcommit: 948ff8f56639e6dc7091134a0efd8d44efca63f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2019
ms.locfileid: "68590903"
---
# <a name="intune-discovered-apps"></a>Applications découvertes par Intune

Les **applications découvertes** par Intune sont les applications détectées sur les appareils inscrits auprès d’Intune dans votre locataire. La liste de ces applications agit comme un inventaire logiciel pour votre locataire. Les **applications découvertes** font l’objet d’un rapport distinct des rapports sur l’[installation des applications](apps-monitor.md). Pour les appareils personnels, Intune ne collecte jamais d’informations sur les applications qui ne sont pas gérées. Sur les appareils d’entreprise, toute application, qu’il s’agisse ou non d’une application gérée, est collectée pour ce rapport. Vous trouverez ci-dessous un tableau qui indique le comportement attendu correspondant. En général, le rapport est actualisé tous les 7 jours à partir du moment de l’inscription (il n’y a donc pas d’actualisation hebdomadaire pour le tout le locataire). La seule exception à cette période d’actualisation concerne les informations sur les applications collectées via l’extension de gestion Intune pour les applications Win32, qui sont collectées toutes les 24 heures.

## <a name="monitor-discovered-apps-with-intune"></a>Surveiller les applications découvertes avec Intune

Intune fournit une liste des applications détectées sur les appareils inscrits auprès d’Intune dans votre locataire.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications découvertes**.

>[!NOTE]
>Vous pouvez exporter la liste des applications découvertes dans un fichier. csv en sélectionnant **Exporter** dans le panneau **Applications découvertes**.
>
>Pour les applications Win32 découvertes, il n’existe actuellement pas de compte d’agrégats. Ce type de données ne peut être affiché que sur une base par appareil.

Intune fournit également la liste des applications découvertes pour l’appareil individuel dans votre locataire. 

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet Intune, sélectionnez **Appareils** > **Tous les appareils**.
3. Sélectionnez un appareil.
4. Pour afficher les applications détectées pour cet appareil , sélectionnez **Applications découvertes** dans la section **Moniteur**. 

## <a name="details-of-discovered-apps"></a>Détails des applications découvertes

La liste suivante fournit le type de plate-forme d’application, les applications qui sont surveillées pour les appareils personnels, les applications qui sont surveillées pour les appareils d’entreprise et le cycle d’actualisation. Pour plus d’informations sur les types d’applications pris en charge dans Intune, consultez [Types d’applications dans Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Plate-forme | Pour les appareils personnels | Pour les appareils d’entreprise | Cycle d’actualisation |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Applications Win32) - REMARQUE : [Nécessite l’extension de gestion Intune](intune-management-extension.md) sur l’appareil | Non applicable | Toutes les applications Win32 trouvées dans la liste Ajouter ou supprimer des programmes | Toutes les 24 heures à partir de l’inscription de l’appareil |
| Windows 10 (Applications modernes) | Seulement les applications modernes gérées | Toutes les applications modernes installées sur l’appareil | Tous les 7 jours à partir de l’inscription de l’appareil |
| Windows 8.1 | Uniquement les applications gérées | Uniquement les applications gérées | Tous les 7 jours à partir de l’inscription de l’appareil |
| Windows Phone 8 | Uniquement les applications gérées | Uniquement les applications gérées | Tous les 7 jours à partir de l’inscription de l’appareil |
| Windows RT | Uniquement les applications gérées | Uniquement les applications gérées | Tous les 7 jours à partir de l’inscription de l’appareil |
| iOS | Uniquement les applications gérées | Toutes les applications installées sur l’appareil | Tous les 7 jours à partir de l’inscription de l’appareil |
| macOS | Toutes les applications installées sur l’appareil | Toutes les applications installées sur l’appareil | Tous les 7 jours à partir de l’inscription de l’appareil |
| Android | Uniquement les applications gérées | Toutes les applications installées sur l’appareil | Tous les 7 jours à partir de l’inscription de l’appareil |
| Android Entreprise | Uniquement les applications gérées | Uniquement les applications installées dans le profil professionnel | Tous les 7 jours à partir de l’inscription de l’appareil |

Il peut arriver que le nombre d’applications découvertes ne corresponde pas au nombre d’états d’installation d’applications. Voici quelques sources d’incohérences :
- Une modification de ciblage d’une application managée installée peut faire baisser le nombre d’installations dans le panneau d’état, tandis que l’application reste comptée parmi les applications détectées.
- Si plusieurs instances de la même application sont ciblées dans un locataire, le chevauchement potentiel d’utilisateurs ou d’appareils entraîne des disparités dans les volumes. Chaque instance de l’application compte les utilisateurs qui se chevauchent, mais les applications découvertes sont comptées plusieurs fois.
- Les applications découvertes et leur état sont collectés à différents intervalles de temps, ce qui peut causer des écarts dans le nombre d’applications.

## <a name="next-steps"></a>Étapes suivantes

- [Types d’applications dans Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Surveiller les informations sur les applications et les affectations avec Microsoft Intune](apps-monitor.md)
