---
title: Paramètres d’optimisation de la distribution pour Windows 10 dans Microsoft Intune – Azure | Microsoft Docs
description: Configurez la façon dont les appareils Windows 10 que vous gérez avec Intune utilisent l’optimisation de la distribution. Dans Intune, créez un profil de configuration d’appareil pour installer les mises à jour à partir d’Internet. Découvrez également comment remplacer des boucles de mise à jour par un profil d’optimisation de la distribution.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124807"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Paramètres d’optimisation de la distribution dans Microsoft Intune

Avec Intune, utilisez les paramètres d’optimisation de la distribution pour vos appareils Windows 10 afin de réduire la consommation de bande passante quand ces appareils téléchargent des applications et des mises à jour. Configurez l’optimisation de la distribution dans le cadre de vos profils de configuration d’appareil.  

Cet article décrit comment configurer les paramètres d’optimisation de la distribution dans le cadre d’un profil de configuration d’appareil. Après avoir créé un profil, vous l’affectez à vos appareils Windows 10 ou l’y déployez. 

Pour voir la liste des paramètres d’optimisation de la distribution pris en charge par Intune, consultez [Paramètres d’optimisation de la distribution pour Intune](../delivery-optimization-settings.md).  

Pour en savoir plus sur l’optimisation de la distribution sur Windows 10, consultez [Mises à jour de l’optimisation de la distribution](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) dans la documentation Windows.  

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Optimisation de la distribution**.

4. Choisissez **Paramètres** > **Configurer**, puis définissez le mode de téléchargement des mises à jour et des applications. Pour plus d’informations sur les paramètres disponibles, consultez [Paramètres d’optimisation de la distribution pour Intune](../delivery-optimization-settings.md).

5. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements.

Le profil est créé, puis apparaît dans la liste. Vous devez à présent [affecter le profil](device-profile-assign.md), puis [superviser son état](device-profile-monitor.md).

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>Supprimer l’optimisation de la distribution des anneaux de mise à jour Windows 10

L’optimisation de la distribution était précédemment configurée dans le cadre des anneaux de mise à jour logicielle. Depuis février 2019, les paramètres d’optimisation de la distribution sont configurés dans le cadre d’un profil de configuration d’appareil avec optimisation de la distribution, qui comprend des paramètres supplémentaires affectant plus que la distribution des mises à jour logicielles aux appareils. Si vous ne l’avez pas déjà fait, supprimez le paramètre d’optimisation de la distribution de vos anneaux de mise à jour en le définissant sur *Non configuré*, puis utilisez un profil d’optimisation de la distribution pour gérer davantage d’options disponibles.

1. Créez un profil de configuration d’appareil avec optimisation de la distribution :

    1. Dans le Centre d’administration du Gestionnaire de points de terminaison Microsoft, sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
    2. Entrez les propriétés suivantes :

        - **Nom** : Entrez un nom descriptif pour le nouveau profil.
        - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
        - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
        - **Type de profil** : Sélectionnez **Optimisation de la distribution**.
        - **Paramètres** : pour le **Mode de téléchargement de l’optimisation de la distribution**, choisissez le mode utilisé par la boucle de mise à jour de logiciel existante, sauf si vous souhaitez changer les paramètres que vous appliquez à vos appareils. Les options disponibles sont les suivantes :
            - **Non configuré**
            - **HTTP uniquement, sans peering**
            - **HTTP fusionné avec le peering derrière le même NAT**
            - **HTTP fusionné avec le peering sur un groupe privé**
            - **Mélange HTTP/peering Internet**
            - **Mode de téléchargement simple sans peering**
            - **Mode de contournement**
    3. Configurez les paramètres supplémentaires que vous souhaitez éventuellement gérer.

2. Affectez ce nouveau profil aux mêmes appareils et utilisateurs que la boucle de mise à jour de logiciels existante. La page [Affectez le profil](device-profile-assign.md) liste les étapes à suivre.

3. Supprimez la configuration de la boucle logicielle existante :
    1. Dans le Centre d’administration du Gestionnaire de points de terminaison Microsoft, accédez à **Mises à jour de logiciels** > Anneaux de mise à jour Windows 10.
    2. Dans la liste, sélectionnez votre boucle de mise à jour.
    3. Dans les paramètres, définissez le **Mode de téléchargement de l’optimisation de la distribution** sur **Non configuré**.
    4. **OK** > **Enregistrez** les modifications apportées.

## <a name="next-steps"></a>Étapes suivantes

[Affectez le profil](device-profile-assign.md) et [effectuez le monitoring de son état](device-profile-monitor.md).  
Voir les [paramètres d’optimisation de la distribution](../delivery-optimization-settings.md) pour Intune.
