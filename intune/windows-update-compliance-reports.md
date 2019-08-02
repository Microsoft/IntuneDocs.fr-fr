---
title: Utiliser des rapports Update Compliance pour les mises à jour Windows dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilisez OMS Update Compliance pour afficher les données de rapport des mises à jour Windows que vous déployez avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09f3cafc16d8a08885731aa244a089367c6c0933
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660408"
---
# <a name="intune-compliance-reports-for-updates"></a>Rapports de conformité Intune pour les mises à jour
Quand vous utilisez Intune pour déployer une mise à jour Windows sur des appareils Windows 10, affichez les détails de la conformité des mises à jour à l’aide d’Intune ou d’une solution gratuite appelée *Update Compliance*, qui fait partie de Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Utiliser Intune
Pour consulter un rapport de stratégie sur l’état de déploiement des boucles de mise à jour Windows 10 que vous avez configurées : 
1. Connectez-vous au [portail Azure](https://portal.azure.com/).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Mises à jour logicielles** > **Vue d’ensemble**. Vous pouvez voir des informations générales sur l’état des anneaux de mise à jour que vous avez affectés.
4. Ouvrez un des rapports suivants :  

   **Pour tous les anneaux de déploiement** :
   1. Dans **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10**
   2. Dans la section **Surveiller**, choisissez **Par état d’anneau de déploiement de mises à jour**.  

   **Pour des anneaux de déploiement spécifiques** :  

   1. Dans **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10**, choisissez l’anneau de déploiement à examiner.  
   2. Dans la section **Surveiller**, choisissez les rapports suivants pour voir des informations plus détaillées sur l’anneau de mise à jour :  
      - **État de l’appareil**  
      - **État de l’utilisateur**  

## <a name="use-update-compliance"></a>Utiliser Update Compliance
Vous pouvez superviser les déploiements de mises à jour Windows 10 à l’aide d’[Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), solution Windows Analytics gratuite. Update Compliance est disponible gratuitement par le biais du portail Azure pour les appareils qui répondent à ses [prérequis](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Quand vous utilisez cette solution, vous déployez un ID commercial sur un des appareils Windows 10 gérés par Intune pour lequel vous souhaitez générer des rapports sur la conformité des mises à jour.  

Dans la console Intune, vous utilisez les paramètres OMA-URI d’une stratégie personnalisée pour configurer l’ID commercial. Pour plus d’informations, consultez [Paramètres de stratégie Intune pour les appareils Windows 10 dans Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

Le chemin OMA-URI (qui respecte la casse) pour la configuration de l’ID commercial est : *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

Par exemple, vous pouvez utiliser les valeurs suivantes dans **Ajouter ou modifier un paramètre OMA-URI** :
- **Nom du paramètre** : ID commercial Windows Analytics
- **Description du paramètre** : configuration d’un ID commercial pour les solutions Windows Analytics
- **OMA-URI** (sensible à la casse) : *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Type de données** : Chaîne
- **Valeur** : \<utilisez le GUID indiqué sous l’onglet Télémétrie Windows dans votre espace de travail OMS>
 
> [!NOTE]  
> Pour plus d’informations sur MS DM Server, consultez [Fournisseur de services de configuration DMClient]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Étapes suivantes
[Gérer les mises à jour logicielles dans Intune](windows-update-for-business-configure.md)

