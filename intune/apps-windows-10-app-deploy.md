---
title: Déploiement d’applications Windows 10 à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez les scénarios de déploiement d’applications Windows 10 disponibles avec Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9c263b9b5fbb7916fb1ae9b9835e2647593f3b1
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567190"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Déploiement d’applications Windows 10 à l’aide de Microsoft Intune 

Microsoft Intune prend en charge une variété de types d’applications et de scénarios de déploiement sur les appareils Windows 10. Une fois que vous avez ajouté une application à Intune, vous pouvez l’attribuer à des utilisateurs et des appareils. Les informations suivantes fournissent plus de détails concernant les scénarios Windows 10 pris en charge. Elles fournissent également des détails importants à noter lors du déploiement d’applications sur Windows. 

Les applications métier et Microsoft Store pour Entreprises sont les types d’applications pris en charge sur les appareils Windows 10. Les extensions de fichier des applications Windows incluent **.msi**, **.appx** et **.appxbundle**.  

> [!Note]
> Les mises à jour Windows 10 minimales nécessaires pour déployer des applications modernes sont les suivantes :
> - Pour Windows 10 1803, [23 mai 2018 - KB4100403 (build du système d’exploitation 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Pour Windows 10 1709, [21 juin 2018 - KB4284822 (build du système d’exploitation 16299.522)](https://support.microsoft.com/help/4284822).

## <a name="windows-10-line-of-business-apps"></a>Applications métier Windows 10

Les applications métier Windows 10 sont signées et chargées dans la console d’administration Intune, et peuvent inclure des applications modernes, telles que les applications UWP (Universal Windows Platform) et les packages d’application Windows (AppX), ainsi que des applications Win 32, telles que de simples fichiers de package Microsoft Installer (MSI). Les mises à jour des applications métier doivent être chargées et déployées manuellement à chaque fois par l’administrateur. Les mises à jour qui sont déployées sont installées automatiquement sur les appareils des utilisateurs finaux qui ont installé l’application sans intervention de l’utilisateur. L’utilisateur n’a aucun contrôle sur les mises à jour. 

## <a name="microsoft-store-for-business-apps"></a>Applications Microsoft Store pour Entreprises

Les applications Microsoft Store pour Entreprises sont des applications modernes achetées à partir du portail d’administration Microsoft Store pour Entreprises, et sont ensuite synchronisées avec Microsoft Intune pour la gestion. Les applications peuvent être **sous licence en ligne** ou **sous licence hors connexion**. Les mises à jour des applications Microsoft Store pour Entreprises sont gérées directement par le Microsoft Store, sans aucune action supplémentaire requise de la part de l’administrateur. L’administrateur peut également empêcher les mises à jour d’applications spécifiques à l’aide d’un URI (Uniform Resource Identifier) personnalisé. Pour plus d’informations, consultez [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). Sur l’appareil, l’utilisateur final peut également désactiver les mises à jour pour toutes les applications Microsoft Store pour Entreprises sur l’appareil. 

## <a name="installing-apps-on-windows-10-devices"></a>Installation d’applications sur les appareils Windows 10
En fonction du type d’application, l’application peut être installée sur un appareil Windows 10 de deux manières :

- **Contexte utilisateur** : Quand une application est déployée dans le contexte utilisateur, l’application gérée est installée pour cet utilisateur sur l’appareil quand il se connecte à l’appareil. Notez que l’installation de l’application ne réussit qu’une fois l’utilisateur connecté à l’appareil. 
    - Les applications métier modernes et les applications Microsoft Store pour Entreprises (en ligne et hors connexion) peuvent être déployées dans le contexte utilisateur et prennent en charge les intentions Obligatoire et Disponible.
    - Les applications Win32 générées en **Mode utilisateur** ou en **Mode double** peuvent être déployées dans le contexte de l’utilisateur et prennent en charge les intentions **Obligatoire** et **Disponible**. 
- **Contexte d’appareil** : Quand une application est déployée dans le contexte d’appareil, l’application gérée est installée directement sur l’appareil par Intune.
    - Seules les applications métier modernes et les applications Microsoft Store pour Entreprises sous licence hors connexion peuvent être déployées dans le contexte d’appareil, et elles prennent uniquement en charge l’intention Obligatoire.
    - Les applications Win32 générées en **Mode machine** ou en **Mode double** peuvent être déployées dans le contexte de l’utilisateur et prennent en charge uniquement l’intention **Obligatoire**.

> [!NOTE]
> Pour les applications Win32 générées en **Mode double**, vous (l’administrateur) devez choisir si l’application fonctionnera comme une application en **Mode utilisateur** ou en **Mode machine** pour toutes les attributions associées à cette instance. Le contexte de déploiement ne peut pas être changé par attribution.  

Quand une application est déployée dans le contexte d’appareil, l’installation réussit uniquement quand elle cible un appareil qui prend en charge le contexte d’appareil. En outre, le déploiement dans le contexte d’appareil prend en charge les conditions suivantes :
- Si une application est déployée dans le contexte d’appareil et qu’elle cible un utilisateur, l’installation échoue avec l’état suivant et l’erreur suivante s’affiche dans la console d’administration :
    - État : Échec.
    - Erreur : Un utilisateur ne peut pas être ciblé par une installation de contexte d’appareil.
- Si une application est déployée dans le contexte d’appareil mais qu’elle cible un appareil ne prenant pas en charge le contexte d’appareil, l’installation échoue avec l’état suivant et l’erreur suivante s’affiche dans la console d’administration :
    - État : Échec.
    - Erreur : Cette plateforme ne prend pas en charge les installations dans le contexte d’appareil. 

> [!Note]
> Une fois qu’une attribution d’application est enregistrée avec un déploiement spécifique, le contexte ne peut pas être modifié pour cette attribution, sauf pour les applications modernes. Dans le cas des applications modernes, le contexte peut être changé de contexte utilisateur en contexte d’appareil. 

En cas de conflit de stratégie sur un appareil/utilisateur, voici les priorités de stratégie permettant de déterminer la stratégie finale :
- Une stratégie de contexte d’appareil a une priorité supérieure à une stratégie de contexte utilisateur. 
- Une stratégie d’installation a une priorité supérieure à une stratégie de désinstallation.

Pour plus d’informations sur l’attribution d’applications à l’aide de Microsoft Intune, consultez [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md) et [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md). Pour plus d’informations sur les types d’applications dans Intune, consultez [Attribuer des applications à Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’attribution d’applications à des groupes, consultez [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md).
- Pour en savoir plus sur le monitoring des affectations d’applications, consultez [Comment surveiller des applications](apps-monitor.md).
