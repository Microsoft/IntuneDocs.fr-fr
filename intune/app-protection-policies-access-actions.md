---
title: Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications
titleSuffix: Microsoft Intune
description: Découvrez comment effectuer une réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f8173b409eb82a3bb98ef0a30570e489fac1fc49
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189691"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Réinitialisation sélective des données à l’aide d’actions d’accès de stratégie de protection des applications dans Intune

À l’aide de stratégies de protection des applications, vous pouvez configurer des paramètres pour empêcher les utilisateurs finaux d’accéder à un compte ou à une application d’entreprise. Ces paramètres ciblent des exigences d’accès et de déplacement des données définies par votre organisation pour des éléments tels que les appareils jailbreakés et les versions minimales de système d’exploitation.
 
Vous pouvez choisir explicitement de réinitialiser les données d’entreprise de votre société de l’appareil de l’utilisateur final en tant qu’action à entreprendre en cas de non-conformité à l’aide de ces paramètres. Pour certains paramètres, vous pourrez configurer plusieurs actions, telles que bloquer l’accès et réinitialiser les données d’après différentes valeurs spécifiées.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Créer une stratégie de protection des applications à l’aide d’actions d’accès

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**.  
    Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Stratégie de protection d’application**.
4. Cliquez sur **Ajouter une stratégie** (vous pouvez également modifier une stratégie existante). 
5. Cliquez sur **Configurer les paramètres requis** pour afficher la liste des paramètres configurables pour la stratégie. 
6. En faisant défiler vers le bas le volet Paramètres, vous verrez une section intitulée **Actions d’accès** avec une table modifiable.

    ![Capture d’écran des actions d’accès de protection des applications Intune](./media/apps-selective-wipe-access-actions01.png)

7. Sélectionnez un **Paramètre** et entrez la **Valeur** que les utilisateurs doivent satisfaire pour se connecter à votre application d’entreprise. 
8. Sélectionnez l’**Action** à effectuer si les utilisateurs ne remplissent pas les critères. Dans certains cas, vous pouvez configurer plusieurs actions pour un même paramètre. Pour plus d’informations, consultez [Guide pratique pour créer et affecter des stratégies de protection des applications](app-protection-policies.md).

>[!NOTE]
> Pour utiliser le paramètre **Modèle(s) d’appareil ou Fabricant(s) d’appareil**, entrez une liste d’identificateurs de modèle séparés par des points-virgules. Évitez les espaces dans les listes de plusieurs valeurs. Ces valeurs ne respectent pas la casse. 

## <a name="policy-settings"></a>Paramètres de stratégie 

Le tableau de paramètres de stratégie de protection des applications a des colonnes pour **Paramètre**, **Valeur** et **Action**.

### <a name="ios-policy-settings"></a>Paramètres de stratégie iOS
Pour iOS, vous pouvez configurer des actions pour les paramètres suivants à l’aide de la liste déroulante **Paramètre** :
-  Nombre max. de tentatives de code PIN
-  Période de grâce hors connexion
-  Appareils jailbreakés/rootés
-  Version min. de l’OS
-  Version min. de l’application
-  Version min. du SDK
-  Modèle(s) d’appareil

Pour utiliser le paramètre **Modèle(s) d’appareil**, entrez une liste d’identificateurs de modèle iOS séparés par des points-virgules. Vous trouverez un identificateur de modèle iOS sous la colonne Type d’appareil dans la [documentation sur la prise en charge d’HockeyApp](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types).<br>
Exemple d’entrée : *iPhone5,2;iPhone5,3*

Sur les appareils de l’utilisateur final, le client Intune effectuerait une action sur la base d’une mise en correspondance simple des chaînes de modèle d’appareil spécifiées dans Intune pour les stratégies de protection d’application. La mise en correspondance dépend entièrement de ce que signale l’appareil. En tant qu’administrateur informatique, vous êtes encouragé à vérifier que le comportement souhaité se produit. Pour cela, testez ce paramètre sur une variété de modèles et de fabricants d’appareils en ciblant un petit groupe d’utilisateurs. La valeur par défaut est **Non configuré**.<br>
Effectuez l’une des actions suivantes : 
- Autoriser spécifié (bloquer non spécifié)
- Autoriser spécifié (réinitialiser non spécifié)

**Que se passe-t-il si l’administrateur informatique entre une liste différente d’identificateurs de modèles iOS dans des stratégies ciblant les mêmes applications d’un même utilisateur Intune ?**<br>
Quand des conflits surviennent entre deux stratégies de protection d’applications au niveau des valeurs configurées, Intune choisit généralement l’approche la plus restrictive. La stratégie résultante envoyée à l’application cible en cours d’ouverture par l’utilisateur Intune ciblé est donc une intersection des identificateurs de modèles iOS répertoriés dans la *stratégie A* et la *stratégie B* ciblant la même combinaison application/utilisateur. Par exemple, si la *stratégie A* spécifie « iPhone5,2;iPhone5,3 » et si la *stratégie B* spécifie « iPhone5,3 », la stratégie résultante appliquée à l’utilisateur Intune ciblé par la *stratégie A* et la *stratégie B* est « iPhone5,3 ». 

### <a name="android-policy-settings"></a>Paramètres de stratégie Android

Pour Android, vous pouvez configurer des actions pour les paramètres suivants à l’aide de la liste déroulante **Paramètre** :
-  Nombre max. de tentatives de code PIN
-  Période de grâce hors connexion
-  Appareils jailbreakés/rootés
-  Version min. de l’OS
-  Version min. de l’application
-  Version min. du correctif
-  Fabricant(s) d’appareil

Pour utiliser le paramètre **Fabricant(s) d’appareil**, entrez une liste de fabricants Android séparés par des points-virgules. Le fabricant d’un appareil Android se trouve sous les paramètres de l’appareil.<br>
Exemple d’entrée : *Fabricant A;Fabricant B* 

>[!NOTE]
> Voici quelques fabricants courants signalés par des appareils utilisant Intune, et pouvant être utilisés comme entrée : Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

Sur les appareils de l’utilisateur final, le client Intune effectuerait une action sur la base d’une mise en correspondance simple des chaînes de modèle d’appareil spécifiées dans Intune pour les stratégies de protection d’application. La mise en correspondance dépend entièrement de ce que signale l’appareil. En tant qu’administrateur informatique, vous êtes encouragé à vérifier que le comportement souhaité se produit. Pour cela, testez ce paramètre sur une variété de modèles et de fabricants d’appareils en ciblant un petit groupe d’utilisateurs. La valeur par défaut est **Non configuré**.<br>
Effectuez l’une des actions suivantes : 
- Autoriser spécifié (bloquer non spécifié)
- Autoriser spécifié (bloquer non spécifié)

**Que se passe-t-il si l’administrateur informatique entre une liste différente de fabricants Android dans des stratégies ciblant les mêmes applications d’un même utilisateur Intune ?**<br>
Quand des conflits surviennent entre deux stratégies de protection d’applications au niveau des valeurs configurées, Intune choisit généralement l’approche la plus restrictive. La stratégie résultante envoyée à l’application cible en cours d’ouverture par l’utilisateur Intune ciblé est donc une intersection des fabricants Android répertoriés dans la *stratégie A* et la *stratégie B* ciblant la même combinaison application/utilisateur. Par exemple, si la *stratégie A* spécifie « Google;Samsung » et si la *stratégie B* spécifie « Google », la stratégie résultante appliquée à l’utilisateur Intune ciblé par la *stratégie A* et la *stratégie B* est « Google ». 

### <a name="additional-settings-and-actions"></a>Actions et paramètres supplémentaires 

Par défaut, la table contient des lignes préremplies pour les paramètres **Période de grâce hors connexion** et **Nombre max. de tentatives de code PIN** si le paramètre **Exiger un code confidentiel d’accès** a la valeur **Oui**.
 
Pour configurer un paramètre, sélectionnez-en un dans la liste déroulante sous la colonne **Paramètre**. Une fois qu’un paramètre est sélectionné, la zone de texte modifiable est activée sous la colonne **Valeur** sur la même ligne, si une valeur doit être définie. De plus, la liste déroulante est activée sous la colonne **Action** avec l’ensemble des actions de lancement conditionnel applicables au paramètre. 

La liste suivante indique les actions les plus courantes :
-  **Bloquer l’accès** : empêcher l’utilisateur final d’accéder à l’application d’entreprise.
-  **Réinitialiser les données** : effacer les données d’entreprise de l’appareil de l’utilisateur final.
-  **Avertir** : présenter une boîte de dialogue à l’utilisateur final en guise de message d’avertissement.

Dans certains cas, comme pour le paramètre **Version min. de l’OS**, vous pouvez configurer le paramètre de façon à effectuer toutes les actions applicables en fonction de différents numéros de version. 

![Capture d’écran des actions d’accès de protection des applications Intune - Version min. de l’OS](./media/apps-selective-wipe-access-actions05.png)

Une fois qu’un paramètre est entièrement configuré, la ligne apparaît dans une vue en lecture seule et est modifiable à tout moment. Une liste déroulante est également ajoutée à cette ligne dans la colonne **Paramètre**. Les paramètres ayant déjà été configurés et n’autorisant pas plusieurs actions ne peuvent pas être sélectionnés dans la liste déroulante.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les stratégies de protection des applications, consultez :
- [Guide pratique pour créer et affecter des stratégies de protection des applications](app-protection-policies.md)
- [Paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md)
- [Paramètres de stratégie de protection des applications Android dans Microsoft Intune](app-protection-policy-settings-android.md) 
