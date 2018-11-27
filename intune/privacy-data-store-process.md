---
title: Stockage et traitement des données dans Intune
description: Découvrez comment les données personnelles sont stockées et traitées dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f1adab40170227926dce1eb7c14117accf1d7d0a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185913"
---
# <a name="data-storage-and-processing-in-intune"></a>Stockage et traitement des données dans Intune

Une fois qu’Intune [a collecté les données](privacy-data-collect.md), leur stockage et leur traitement sont effectués comme indiqué ci-dessous.

## <a name="storing-personal-data"></a>Stockage des données personnelles

Toutes les données collectées autres que les données de télémétrie sont traitées via le service Intune et sont stockées dans un ou plusieurs des emplacements de stockage suivants : 

- SQLAzure 
- Collections fiables (Service Fabric)  
- Azure Storage 

Les données de télémétrie (journaux des services, journaux de performances, erreurs, etc.) qui sont essentiels pour la surveillance et la fourniture d’un service stable sont envoyées aux banques de données de télémétrie de Microsoft.

### <a name="storage-locations"></a>Emplacements de stockage

Microsoft offre et exploite les services Intune dans plusieurs régions du monde. Intune respecte les choix d’emplacement de stockage faits par l’administrateur pour les données des clients.

Pour plus d’informations, consultez [Microsoft Intune : où sont les données de mon client ?](For more information, see Microsoft Intune Where is my customer data?)

### <a name="personal-data-retention"></a>Conservation des données personnelles

En général, les données personnelles sont conservées par Intune pendant trente jours après la suppression de l’utilisateur de la gestion Intune.

Les données de télémétrie recueillies dans le cadre de l’utilisation d’Intune sont conservées pendant un maximum de 30 jours.

Les journaux d’audit sont conservés pendant jusqu’à un an.

## <a name="processing-personal-data"></a>Traitement des données personnelles

Intune traite les données personnelles avec des systèmes certifiés ISO. Pour plus d’informations, consultez le [Portail d’approbation de services](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Profilage et marketing

Microsoft Intune n’utilise aucune des données personnelles collectées dans le cadre de la fourniture du service à des fins de profilage ou de marketing. 

### <a name="restrict-processing-of-personal-data"></a>Limiter le traitement des données personnelles

Pour limiter le traitement des données personnelles d’un utilisateur, vous pouvez supprimer son compte en procédant comme suit :
1. Exportation d’une copie électronique des données personnelles de l’utilisateur, notamment
    - comptes
    - données des services
    - journaux associés
2. Suppression du compte de l’utilisateur et des données associées dans Intune.

## <a name="next-steps"></a>Étapes suivantes

Découvrez plus d’informations sur la façon dont Intune [sécurise et partage](privacy-data-secure-share.md) les données personnelles. 