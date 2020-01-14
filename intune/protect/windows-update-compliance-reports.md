---
title: Utiliser des rapports Update Compliance pour les mises à jour Windows dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilisez OMS Update Compliance pour afficher les données de rapport des mises à jour Windows que vous déployez avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1e493e0d2d562c0f69454d1999e82b528c724a2
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731277"
---
# <a name="intune-compliance-reports-for-updates"></a>Rapports de conformité Intune pour les mises à jour

Quand vous utilisez Intune pour déployer une mise à jour Windows sur des appareils Windows 10, affichez les détails de la conformité des mises à jour à l’aide d’Intune ou d’une solution gratuite appelée *Update Compliance*, qui fait partie de Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Utiliser Intune

Pour consulter un rapport de stratégie sur l’état de déploiement des boucles de mise à jour Windows 10 que vous avez configurées :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Vue d’ensemble** > **État des mises à jour logicielles**. Vous pouvez voir des informations générales sur l’état des anneaux de mise à jour que vous avez affectés.

3. Pour afficher des détails supplémentaires, sélectionnez **Analyser**. Ensuite, sous **Mises à jour logicielles**, sélectionnez **Par état d’anneau de déploiement de mises à jour** et choisissez l’anneau de déploiement à examiner.

   Dans la section **Surveiller**, choisissez les rapports suivants pour voir des informations plus détaillées sur l’anneau de mise à jour :

   - **État de l’appareil** : cette opération affiche l’état de la configuration de l’appareil. Pour plus d’informations, consultez [Mettre à jour deviceConfigurationDeviceStatus]( https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0).

   - **État de l’utilisateur** : affiche le nom d’utilisateur, l’état et la date du dernier rapport. Pour plus d’informations, consultez [Répertorier deviceConfigurationUserStatuses](https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationuserstatus-list?view=graph-rest-1.0).

   - **État de la mise à jour de l’utilisateur final** : cette opération affiche l’état de mise à jour des appareils Windows. Pour plus d’informations, consultez [windowsUpdateState](https://docs.microsoft.com/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

## <a name="use-update-compliance"></a>Utiliser Update Compliance

Vous pouvez superviser les déploiements de mises à jour Windows 10 à l’aide d’[Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), solution Windows Analytics gratuite. Update Compliance est disponible gratuitement par le biais du portail Azure pour les appareils qui répondent à ses [prérequis](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Quand vous utilisez cette solution, vous déployez un ID commercial sur un des appareils Windows 10 gérés par Intune pour lequel vous souhaitez générer des rapports sur la conformité des mises à jour.  

Dans Intune, utilisez les paramètres OMA-URI d’une stratégie personnalisée pour configurer l’ID commercial. Consultez [Utiliser des paramètres personnalisés pour les appareils Windows 10 dans Intune](../configuration/custom-settings-windows-10.md).

Le chemin OMA-URI (qui respecte la casse) pour la configuration de l’ID commercial est : *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

Par exemple, vous pouvez utiliser les valeurs suivantes dans **Ajouter ou modifier un paramètre OMA-URI** :

- **Nom du paramètre** : ID commercial Windows Analytics
- **Description du paramètre** : configuration d’un ID commercial pour les solutions Windows Analytics
- **OMA-URI** (sensible à la casse) : *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Type de données** : Chaîne
- **Valeur** : \<utilisez le GUID indiqué sous l’onglet Télémétrie Windows dans votre espace de travail OMS>

> [!NOTE]
> Pour plus d’informations sur MS DM Server, consultez [Fournisseur de services de configuration DMClient]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Étapes suivantes

[Gérer les mises à jour logicielles dans Intune](windows-update-for-business-configure.md)
