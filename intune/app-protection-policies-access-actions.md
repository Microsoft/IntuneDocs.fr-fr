---
title: Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications
titleSuffix: Microsoft Intune
description: Découvrez comment effectuer une réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909114"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Intune

À l’aide de stratégies de protection des applications, vous pouvez configurer des paramètres pour empêcher les utilisateurs finaux d’accéder à un compte ou à une application d’entreprise. Ces paramètres ciblent des exigences d’accès et de déplacement des données définies par votre organisation pour des éléments tels que les appareils jailbreakés et les versions minimales de système d’exploitation.
 
Vous pouvez choisir explicitement de réinitialiser les données d’entreprise de votre société de l’appareil de l’utilisateur final en tant qu’action à entreprendre en cas de non-conformité à l’aide de ces paramètres. Pour certains paramètres, vous pourrez configurer plusieurs actions, telles que bloquer l’accès et réinitialiser les données d’après différentes valeurs spécifiées.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Créer une stratégie de protection des applications à l’aide d’actions d’accès

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**.  
    Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Applications mobiles** > **Stratégie de protection d’application**.
4. Cliquez sur **Ajouter une stratégie** (vous pouvez également modifier une stratégie existante). 
5. Cliquez sur **Configurer les paramètres requis** pour afficher la liste des paramètres configurables pour la stratégie. 
6. En faisant défiler vers le bas dans le volet **Paramètres**, vous verrez une section intitulée **Actions d’accès** avec une table modifiable.

    ![Capture d’écran des actions d’accès de protection des applications Intune](./media/apps-selective-wipe-access-actions01.png)

7. Sélectionnez un **Paramètre** et entrez la **Valeur** que les utilisateurs doivent satisfaire pour se connecter à votre application d’entreprise. 
8. Sélectionnez l’**Action** à effectuer si les utilisateurs ne remplissent pas les critères. Dans certains cas, vous pouvez configurer plusieurs actions pour un même paramètre. Pour plus d’informations, consultez [Guide pratique pour créer et affecter des stratégies de protection des applications](app-protection-policies.md).

>[!NOTE]
> Pour utiliser le paramètre **Modèle(s) d’appareil**, entrez une liste d’identificateurs de modèle séparés par des points-virgules. 

## <a name="policy-settings"></a>Paramètres de stratégie 

Le tableau de paramètres de stratégie de protection des applications a des colonnes pour **Paramètre**, **Valeur** et **Action**.

Pour iOS, vous pouvez configurer des actions pour les paramètres suivants à l’aide de la liste déroulante **Paramètre** :
-  Nombre max. de tentatives de code PIN
-  Période de grâce hors connexion
-  Appareils jailbreakés/rootés
-  Version min. de l’OS
-  Version min. de l’application
-  Version min. du SDK
-  Modèle(s) d’appareil

Pour Android, vous pouvez configurer des actions pour les paramètres suivants à l’aide de la liste déroulante **Paramètre** :
-  Nombre max. de tentatives de code PIN
-  Période de grâce hors connexion
-  Appareils jailbreakés/rootés
-  Version min. de l’OS
-  Version min. de l’application
-  Version min. du correctif
-  Fabricant(s) d’appareil

Par défaut, la table contient des lignes préremplies pour les paramètres **Période de grâce hors connexion** et **Nombre max. de tentatives de code PIN** si le paramètre **Exiger un code confidentiel d’accès** a la valeur **Oui**.
 
Pour configurer un paramètre, sélectionnez-en un dans la liste déroulante sous la colonne **Paramètre**. Une fois qu’un paramètre est sélectionné, la zone de texte modifiable est activée sous la colonne **Valeur** sur la même ligne, si une valeur doit être définie. De plus, la liste déroulante est activée sous la colonne **Action** avec l’ensemble des actions de lancement conditionnel applicables au paramètre. 

La liste suivante indique les actions les plus courantes :
-  **Bloquer l’accès** : empêcher l’utilisateur final d’accéder à l’application d’entreprise.
-  **Réinitialiser les données** : effacer les données d’entreprise de l’appareil de l’utilisateur final.
-  **Avertir** : présenter une boîte de dialogue à l’utilisateur final en guise de message d’avertissement.

### <a name="additional-settings-and-actions"></a>Actions et paramètres supplémentaires 

Dans certains cas, comme pour le paramètre **Version min. de l’OS**, vous pouvez configurer le paramètre de façon à effectuer toutes les actions applicables en fonction de différents numéros de version. 

![Capture d’écran des actions d’accès de protection des applications Intune - Version min. de l’OS](./media/apps-selective-wipe-access-actions05.png)

Une fois qu’un paramètre est entièrement configuré, la ligne apparaît dans une vue en lecture seule et est modifiable à tout moment. Une liste déroulante est également ajoutée à cette ligne dans la colonne **Paramètre**. Les paramètres ayant déjà été configurés et n’autorisant pas plusieurs actions ne peuvent pas être sélectionnés dans la liste déroulante.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les stratégies de protection des applications, consultez :
- [Guide pratique pour créer et affecter des stratégies de protection des applications](app-protection-policies.md)
- [Paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md)
- [Paramètres de stratégie de protection des applications Android dans Microsoft Intune](app-protection-policy-settings-android.md) 

