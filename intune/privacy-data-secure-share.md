---
title: Sécurité et partage des données dans Intune
description: Découvrez comment les données personnelles sont sécurisées et partagées dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 631d76aca2c393be3c81cb8b6f532605664f4ce4
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031637"
---
# <a name="data-security-and-sharing-in-intune"></a>Sécurité et partage des données dans Intune


## <a name="data-security"></a>Sécurité des données

Microsoft Intune est un composant essentiel de l’offre de service cloud Suite Microsoft Enterprise Mobility + Security. Pour prendre en charge la [stratégie de gouvernance des données](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx), tous les services cloud Microsoft sont développés avec les méthodologies [Confidentialité Microsoft](https://www.microsoft.com/en-us/trustcenter/privacy) et [Sécurité Microsoft](https://www.microsoft.com/en-us/trustcenter/security/).  

Microsoft Intune suit les mêmes mesures techniques et d’organisation que celles qui sont mises en œuvre par les équipes du service Microsoft Azure pour la sécurisation des processus contre les violations des données.

Pour plus d’informations, consultez le [Portail d’approbation de services](https://www.microsoft.com/en-us/TrustCenter/stp).

Intune utilise des techniques de minimisation des données, comme les suivantes :

- aggregation
- collecte de données facultative pour certaines fonctionnalités
- données rendues moins précises ou moins sensibles

Intune utilise également des techniques comme RBAC et la sécurité JiT pour la prise en charge des incidents, de façon à assurer la protection des données par défaut. 

### <a name="data-breach-reporting"></a>Rapports de violation des données

Quand un incident de sécurité communicable au client est identifié, les clients en sont informés. Ce processus implique de travailler avec l’équipe Microsoft O365 pour communiquer la notification de violation à tous les clients Microsoft O365 utilisant Intune.

## <a name="data-sharing"></a>Partage des données

Quand les administrateurs d’un locataire activent certaines fonctionnalités (comme le Programme d’inscription des appareils Apple), Microsoft Intune demande le consentement de l’administrateur pour partager les données avec les tiers appropriés. Dans ce cas, Intune peut partager des données personnelles avec :

- Des tiers agissant en tant qu’agents de Microsoft.
- Des tiers qui n’agissent pas en tant qu’agents de Microsoft, mais seulement quand les administrateurs de locataire autorisent explicitement Intune à le faire.

Tous les tiers agissant en tant qu’agents de Microsoft sont inclus dans la [liste des sous-traitants des services en ligne](https://aka.ms/Online_Serv_Subcontractor_List).

Le partage de données avec ces entités est fait dans le but d’aider le service clientèle et le support technique, la maintenance du service et d’autres opérations.

Le contrat d’un locataire avec le tiers détermine les données personnelles d’Intune conservées dans le service du tiers. Il accorde également à Intune l’autorisation de transmettre des données au service du tiers.  

Pour plus d’informations sur les données partagées avec certains tiers, consultez les articles suivants :
- [Données envoyées par Intune à Apple](data-intune-sends-to-apple.md)
- [Données envoyées par Intune à Google](data-intune-sends-to-google.md)
- [Données envoyées par Apple à Intune](data-apple-sends-to-intune.md)
- [Données envoyées par Google à Intune](data-google-sends-to-intune.md)
- [Données envoyées par Jamf Pro à Intune](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>Partage de données avec System Center Configuration Manager

Microsoft Intune ne partage aucune donnée avec System Center Configuration Manager. System Center Configuration Manager est un produit local déployé, géré et exploité directement par le client. Les données d’utilisation et de diagnostic collectées par Configuration Manager sont destinées seulement à améliorer l’expérience d’installation, la qualité et la sécurité des versions futures.

Pour plus d’informations, consultez [Données de diagnostic et d’utilisation de SCCM](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). 


## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [visualiser et corriger](privacy-data-view-correct.md) les données personnelles dans Intune.
