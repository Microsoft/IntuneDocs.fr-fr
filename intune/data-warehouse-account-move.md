---
title: Déplacer les données de votre compte Intune Data Warehouse
titleSuffix: Microsoft Intune
description: Découvrez comment sauvegarder vos données d’entrepôt de données Intune quand vous déplacez votre compte.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c73e4c8aa5f71fb80110d4a223b9872c8dbaff3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798100"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Déplacer les données de votre compte Intune Data Warehouse 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quand vous demandez le déplacement de votre compte, vous demandez en fait le changement d’emplacement de votre centre de données. Une fois le déplacement effectué, votre entrepôt de données est réinitialisé et commence à enregistrer les données depuis le nouvel emplacement en fonction du jour spécifié pour le début du déplacement. Pour sauvegarder vos données d’entrepôt de données antérieures, suivez les étapes ci-après **avant** le déplacement de votre compte. Dans la mesure où la plupart des tables d’entrepôt de données conservent les données pendant 30 jours, s’il manque des données dans ces tables, elles ne seront plus disponibles 30 jours après le déplacement de votre compte. Pour en savoir plus sur les périodes de rétention de tables spécifiques, consultez [Modèle de données de l’entrepôt de données](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Sauvegarder vos données d’entrepôt de données 

Pour sauvegarder vos données d’entrepôt de données, vous devez les enregistrer dans un fichier *.csv* à l’aide de l’API d’entrepôt de données :  

1. Si vous utilisez l’API d’entrepôt de données pour la première fois, suivez le processus à usage unique décrit dans l’article suivant, [Obtenir des données à partir de l’API d’entrepôt de données Intune avec un client REST](reports-proc-data-rest.md).
2. Utilisez l’exemple PowerShell intitulé [Accéder à l’entrepôt de données Intune avec PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell) pour télécharger toutes vos données dans des fichiers CSV. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Sauvegarder vos graphiques de tendances à partir du portail Azure

Certains graphiques de tendances dans votre affichage du portail Azure vont être réinitialisés. Vous pouvez sauvegarder ces graphiques en exécutant le script suivant dans **Graph** :   

### <a name="terms--conditions-acceptance-reports"></a>Rapports d’acceptation des conditions générales
1. Dans le portail Azure, accédez à **Microsoft Intune** -> **Inscription de l’appareil** -> **Conditions générales**.
2. Pour chaque élément **Conditions générales**, sélectionnez **Rapport d’acceptation**, puis **Exporter**.
3. Enregistrez le rapport localement.
 
### <a name="app-protection-reports"></a>Rapports de protection de l’application  
1. Dans le portail Azure, accédez à **Microsoft Intune** -> **Applications clientes** -> **État de protection de l’application**.
2. Cliquez sur l’icône de téléchargement ( ⤓ ) pour enregistrer chaque rapport.

### <a name="device-configuration-charts"></a>Graphiques de configuration de l’appareil 
1. Dans le portail Azure, accédez à **Microsoft Intune** -> **Configuration de l’appareil**.
2. À l’aide de l’[Afficheur Graph](https://developer.microsoft.com/graph/graph-explorer) Microsoft, téléchargez les données des graphiques. 
    - Pour connaître l’état de déploiement de tous les profils de configuration d’appareil pour tous les appareils, consultez l’[état de déploiement des appareils](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content).

    - Pour connaître l’état de déploiement de tous les profils de configuration d’appareil pour tous les utilisateurs, consultez l’[état de déploiement des utilisateurs](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content).

    - Pour connaître l’état de déploiement d’un profil, consultez l’[état de déploiement du profil](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview).
  
    > [!NOTE]
    > Vous devez avoir un jeton d’authentification valide pour accéder aux informations relatives à la configuration de l’appareil et à l’état du déploiement.

## <a name="device-enrollment-charts"></a>Graphiques d’inscription des appareils
1. Dans le portail Azure, accédez à **Microsoft Intune** -> **Inscription de l’appareil**.
2. À l’aide de l’[Afficheur Graph](https://developer.microsoft.com/graph/graph-explorer) Microsoft, téléchargez les données des graphiques.
    - Pour connaître l’état de l’inscription, copiez cette [requête d’état d’inscription](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content), puis collez-la dans l’[Afficheur Graph](https://developer.microsoft.com/graph/graph-explorer).
    - Pour connaître le top des échecs d’inscription de cette semaine, copiez cette [requête d’échecs d’inscription](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content), puis collez-la dans l’[Afficheur Graph](https://developer.microsoft.com/graph/graph-explorer).

    > [!NOTE]
    > Vous devez avoir un jeton d’authentification valide pour accéder aux données relatives à l’inscription des appareils. 

## <a name="after-a-data-warehouse-account-move"></a>Après le déplacement d’un compte d’entrepôt de données

Après le déplacement du compte d’entrepôt de données, vous pouvez constater dans Intune que l’entrepôt de données a été réinitialisé et que vos données sont désormais stockées au nouvel emplacement. Les graphiques et les options d’exportation sont réinitialisés. Vous voyez s’afficher une notification qui, quand vous cliquez dessus, vous redirige vers un article expliquant pourquoi les graphiques ont été réinitialisés.  

## <a name="data-warehouse-move-example"></a>Exemple de déplacement de l’entrepôt de données 

Le client X demande qu’un compte soit déplacé à partir du 06/01/2018. En réponse à sa demande, le client reçoit un lien qui lui permet de voir la documentation décrivant les étapes à suivre, s’il souhaite sauvegarder son entrepôt de données antérieur. Le 06/01/2018, l’entrepôt de données et les graphiques qu’il prend en charge sont réinitialisés. De plus, cette date marque le début du stockage des données dans le nouveau centre de données. 

## <a name="next-steps"></a>Étapes suivantes

 - Découvrez les [nouveautés hebdomadaires dans Intune](whats-new.md). Vous pouvez également découvrir les modifications à venir, les annonces importantes sur le service et des informations sur les versions précédentes.
 - Consultez le [Blog de Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
