---
title: Déploiement d’applications Windows 10 à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez les scénarios de déploiement d’applications Windows 10 disponibles avec Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa4510b95e1e84d9f94158833dac555daa33c690
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912554"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Déploiement d’applications Windows 10 à l’aide de Microsoft Intune 

Microsoft Intune prend en charge une variété de types d’applications et de scénarios de déploiement sur les appareils Windows 10. Une fois que vous avez ajouté une application à Intune, vous pouvez l’attribuer à des utilisateurs et des appareils. Cet article fournit plus de détails sur les scénarios Windows 10 pris en charge, ainsi que des détails clés à noter lorsque vous déployez des applications sur Windows. 

Les applications métier et Microsoft Store pour Entreprises sont les types d’applications pris en charge sur les appareils Windows 10. Les extensions de fichier des applications Windows incluent .msi, .appx et .appxbundle.  

> [!Note]
> Pour déployer des applications modernes, vous devez disposer au minimum de :
> - Pour Windows 10 1803, [23 mai 2018 - KB4100403 (build du système d’exploitation 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Pour Windows 10 1709, [21 juin 2018 - KB4284822 (build du système d’exploitation 16299.522)](https://support.microsoft.com/help/4284822).
>
> Seul le système Windows 10 1803 (et ses versions ultérieures) prend en charge l’installation d’applications lorsqu’aucun utilisateur principal n’est associé.
>
> Le déploiement d'applications métier n'est pas pris en charge sur les appareils exécutant les éditions Windows 10 Famille.

## <a name="supported-windows-10-app-types"></a>Types d'applications Windows 10 pris en charge

Des types d'applications spécifiques sont pris en charge en fonction de la version de Windows 10 que vos utilisateurs exécutent. Le tableau suivant indique le type d'application et sa compatibilité avec Windows 10.

| Type d’application | Accueil | Pro | Entreprises | Enterprise | Éducation | S-Mode | Hololense | SurfaceHub | WCOS | Mobile |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  .MSI | Non | Oui | Oui | Oui | Oui | Non | Non | Non | Non | Non |
| .IntuneWin | Non | Oui | Oui | Oui | Oui | 19H2+ | Non | Non | Non | Non |
| Office C2R | Non | Oui | Oui | Oui | Oui | Non | Non | Non | Non | Non |
| Application métier : APPX/MSIX | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui |
| MSFB Offline | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui |
| MSFB Online | Oui | Oui | Oui | Oui | Oui | Oui | RS4+ | Oui | Oui | Oui |
| Applications web | Oui | Oui | Oui | Oui | Oui | Oui | Oui<sup>1 | Oui<sup>1 | Oui | Oui |
| Lien vers le Store | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui | Oui |

<sup>1</sup> Lancer à partir du portail d'entreprise uniquement.

> [!NOTE]
> Tous les types d'applications Windows nécessitent une inscription.

## <a name="windows-10-lob-apps"></a>Applications métier Windows 10

Vous pouvez signer et charger des applications métier Windows 10 dans la console d’administration Intune. Celles-ci peuvent comprendre les applications UWP (Universal Windows Platform) et les packages d’application Windows (AppX), ainsi que des applications Win 32, telles que de simples fichiers de package Microsoft Installer (MSI). L’administrateur doit charger et déployer manuellement les mises à jour des applications métier. Ces mises à jour sont installées automatiquement sur les appareils des utilisateurs qui ont installé l’application. Aucune intervention de l’utilisateur n’est requise, et l’utilisateur n’a aucun contrôle sur les mises à jour. 

## <a name="microsoft-store-for-business-apps"></a>Applications Microsoft Store pour Entreprises

Les applications Microsoft Store pour Entreprises sont des applications modernes achetées à partir du portail d’administration Microsoft Store pour Entreprises. Elles sont ensuite synchronisées avec Microsoft Intune pour la gestion. Les applications peuvent être sous licence en ligne ou sous licence hors connexion. Le Microsoft Store gère directement les mises à jour, sans aucune action supplémentaire requise par l’administrateur. Vous pouvez également empêcher les mises à jour d’applications spécifiques à l’aide d’un URI (Uniform Resource Identifier) personnalisé. Pour plus d’informations, consultez [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). L’utilisateur final peut également désactiver les mises à jour pour toutes les applications Microsoft Store pour Entreprises sur l’appareil. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Catégoriser les applications du Microsoft Store pour Entreprises 
Pour catégoriser les applications du Microsoft Store pour Entreprises : 

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications**. 
3. Sélectionnez une application du Microsoft Store pour Entreprises. Puis sélectionnez **Propriétés** > **Informations sur l’application** > **Catégorie**. 
4. Sélectionnez une catégorie.

## <a name="install-apps-on-windows-10-devices"></a>Installer des applications sur les appareils Windows 10
En fonction du type d’application, l’application peut être installée sur un appareil Windows 10 de deux manières :

- **Contexte utilisateur** : Quand une application est déployée dans le contexte utilisateur, l’application gérée est installée pour cet utilisateur sur l’appareil quand il se connecte à l’appareil. Notez que l’installation de l’application ne réussit qu’une fois l’utilisateur connecté à l’appareil. 
  - Les applications métier modernes et les applications Microsoft Store pour Entreprises (en ligne et hors connexion) peuvent être déployées dans le contexte de l’utilisateur. Les applications prennent en charge les intentions Obligatoire et Disponible.
  - Les applications Win32 générées en Mode utilisateur ou en Mode double peuvent être déployées dans le contexte de l’utilisateur et prennent en charge les intentions Obligatoire et Disponible. 
- **Contexte d’appareil** : Quand une application est déployée dans le contexte d’appareil, l’application gérée est installée directement sur l’appareil par Intune.
  - Seules les applications métier modernes et les applications Microsoft Store pour Entreprises sous licence hors connexion peuvent être déployées dans le contexte d’appareil. Ces applications prennent uniquement en charge l’intention Obligatoire.
  - Les applications Win32 générées en Mode machine ou en Mode double peuvent être déployées dans le contexte de l’appareil et prennent en charge uniquement l’intention Obligatoire.

> [!NOTE]
> Pour les applications Win32 générées en Mode double, l’administrateur doit choisir si l’application fonctionnera comme une application en Mode utilisateur ou en Mode machine pour toutes les attributions associées à cette instance. Le contexte de déploiement ne peut pas être changé par attribution.  

Les applications ne peuvent être installées dans le contexte de l’appareil que si elles sont prises en charge par l’appareil et le type d'application Intune. Vous pouvez installer les types d'applications suivants dans le contexte de l’appareil et les affecter à un groupe d’appareils :

- Applications Win32
- Microsoft Store sous licence en mode hors connexion pour les applications métier
- Applications métier (MSI, APPX et MSIX)
- Office 365 ProPlus

Les applications métier Windows (en particulier APPX et MSIX) et les applications Microsoft Store for Business (applications hors connexion) que vous avez choisi d'installer dans le contexte d'un appareil doivent être affectées à un groupe d’appareils. L'installation échoue si l'une de ces applications est déployée dans le contexte de l'utilisateur. L’état et l’erreur suivants s’affichent dans la console d’administration :
  - État : Échec.
  - Erreur : Un utilisateur ne peut pas être ciblé par une installation de contexte d’appareil.

> [!IMPORTANT]
> Lorsqu'une application est utilisée en combinaison avec un scénario de provisionnement AutoPilot de type « White Glove », les applications métier et les applications Microsoft Store pour Entreprises déployées dans le contexte d'un appareil n’ont pas besoin de cibler un groupe d'appareils. Pour plus d’informations, consultez [Déploiement « White Glove » AutoPilot sous Windows](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove).

> [!Note]
> Une fois que vous enregistrez une affectation d’application avec un déploiement spécifique, vous ne pouvez pas modifier le contexte de cette affectation, à l’exception des applications modernes. Pour les applications modernes, vous pouvez modifier le contexte en passant du contexte utilisateur au contexte d’appareil. 

En cas de conflit dans les stratégies sur un seul utilisateur ou appareil, les priorités suivantes s’appliquent :
- Une stratégie de contexte d’appareil a une priorité supérieure à une stratégie de contexte utilisateur. 
- Une stratégie d’installation a une priorité supérieure à une stratégie de désinstallation.

Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md). Pour plus d’informations sur les types d’applications dans Intune, consultez [Attribuer des applications à Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Étapes suivantes

- [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md)
- [Comment surveiller les applications](apps-monitor.md)
