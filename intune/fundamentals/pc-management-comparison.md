---
title: Comparer les options de gestion des PC Windows
titleSuffix: Microsoft Intune
description: Inscrire des appareils iOS d’entreprise à l’aide du programme d’inscription des appareils Apple ou d’Apple Configurator
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 217b93fcd78010428ce427a755e6c0c20f4372df
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736271"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Comparer la gestion des PC Windows en tant qu’ordinateurs ou appareils mobiles

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

Les organisations peuvent utiliser Microsoft Intune pour gérer les PC Windows en tant qu’appareils mobiles avec la gestion des appareils mobiles (MDM) ou en tant qu’ordinateurs avec le logiciel client Intune.  Microsoft recommande l’utilisation de la solution MDM dans la mesure du possible. Toutefois, pour vous aider à mieux comprendre les différences entre ces options, le tableau suivant compare les deux options de gestion.

|**Fonctionnalité/Scénario** |**Windows en tant qu’ordinateur**<br>Client logiciel Intune | **Windows en tant qu’appareil mobile**<br>GESTION DES APPAREILS MOBILES |
|--------------|-------------------------------|-------------------------------|
|**Systèmes d’exploitation** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Prise en charge du portail Intune** |[Console Silverlight](https://manage.microsoft.com)|[Portail Azure](https://portal.azure.com) |
|**Accès conditionnel**|Non disponible|Disponible <br>[Qu’est-ce que l’accès conditionnel ?](../protect/conditional-access.md)|
|**Inscription en bloc**|Non disponible|Disponible <br>[Inscription en bloc des appareils Windows](../enrollment/windows-bulk-enroll.md)|
|**Profils d’appareils**|Non disponible|Disponible <br>[Que sont les profils d’appareil Microsoft Intune ?](../configuration/device-profiles.md)|
|**Inscription sans agent**|Non disponible |Disponible<br>[Inscrire des appareils Windows](../enrollment/windows-enroll.md)|
|**Gestion des mises à jour logicielles**| Mises à jour Windows et mises à jour des applications Microsoft<br>[Maintenir des PC Windows à jour avec les mises à jour logicielles](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Microsoft Store pour Entreprises pour les mises à jour des applications Windows 10 et Microsoft<br> [Configurer les paramètres Windows Update Entreprise](../protect/windows-update-for-business-configure.md) |
|**Gestion des licences logicielles**|Disponible <br>[Gérer les contrats de licence des logiciels de PC Windows](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Microsoft Store pour Entreprises (applications .appx uniquement)<br>[Gérer les applications achetées sur le Microsoft Store pour Entreprises](../apps/windows-store-for-business.md)|
|**Inventaire**|Disponible <br>[Afficher l’inventaire logiciel et matériel pour les PC Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Disponible <br>[Comment surveiller les informations d’applications](../apps/apps-monitor.md)<br>[Qu’est-ce que la gestion des appareils](../remote-actions/device-management.md)|
|**Stratégie de Pare-feu Windows**|Disponible <br>[Protéger les PC Windows à l’aide de stratégies de Pare-feu Windows](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Disponible <br>[Pare-feu Windows Defender](../protect/endpoint-protection-windows-10.md#windows-defender-firewall)|
|**Protection contre les programmes malveillants**|Endpoint Protection<br>[Contribuer à la sécurisation des PC Windows avec Endpoint Protection](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[Activer Windows Defender](../protect/advanced-threat-protection.md)|
|**Assistance à distance** |TeamViewer<br>[Demander et fournir une assistance à distance pour les PC Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Utiliser TeamViewer pour administrer à distance des appareils Intune](../remote-actions/teamviewer-support.md) |
|**Déploiement d'applications** | Non disponible pour Microsoft Store pour Entreprises,<br>.exe, .appx, et .msi incluant plusieurs fichiers uniquement<br>[Ajouter des applications pour les PC Windows exécutant le logiciel client Intune](add-apps-for-windows-pcs-in-microsoft-intune.md)|Disponible pour les applications du Microsoft Store et les applications métier<br>[Guide pratique d’ajout d’applications du Windows Store](../apps/store-apps-windows.md)<br>[Guide pratique pour ajouter des applications métier Windows](../apps/lob-apps-windows.md)|
|**Protection d’applications**|Non disponible|Disponible <br>[Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md)|
|**Attestation d’intégrité**|Non disponible|Disponible|


## <a name="advantages-of-mdm-windows-pc-management"></a>Avantages de la gestion des PC Windows avec gestion des appareils mobiles (MDM)
La gestion des PC Windows avec la gestion des appareils mobiles moderne présente les avantages suivants :
- **Scalabilité** : la gestion MDM évolue avec la gestion cloud Intune. Le logiciel client Intune est limité à 7 000 PC.
- **Simplicité** : utilise les fonctionnalités de gestion modernes incluses dans le système d’exploitation sans se baser sur un client logiciel téléchargé
- **Cohérence** : vos PC Windows sont gérés comme tous les autres appareils mobiles de votre organisation
<!-- - **Cloud optimization** - -->