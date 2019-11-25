---
title: Paramètres d’optimisation de la distribution pour Windows 10 dans Microsoft Intune – Azure | Microsoft Docs
description: Configurez la façon dont les appareils Windows 10 que vous gérez avec Intune utilisent l’optimisation de la distribution. Dans Intune, créez un profil de configuration d’appareil pour installer les mises à jour à partir d’Internet. Découvrez également comment remplacer des boucles de mise à jour par un profil d’optimisation de la distribution.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 44078f61e4f1939b1f0b15b3dde5ac54938ffbc3
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059977"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Paramètres d’optimisation de la distribution dans Microsoft Intune

Avec Intune, vous pouvez utiliser les paramètres d’optimisation de la distribution pour vos appareils Windows 10 afin de réduire la consommation de bande passante quand ces appareils téléchargent des applications et des mises à jour. L’optimisation de la distribution est configurée dans le cadre de vos profils de configuration d’appareil.  

Cet article décrit comment configurer les paramètres d’optimisation de la distribution dans le cadre d’un profil de configuration d’appareil. Après avoir créé un profil, vous l’affectez à vos appareils Windows 10 ou l’y déployez. 

Pour obtenir la liste des paramètres d’optimisation de la distribution pris en charge par Intune, consultez [Paramètres d’optimisation de la distribution pour Intune](../delivery-optimization-settings.md).  

Pour en savoir plus sur l’optimisation de la distribution sur Windows 10, consultez [Mises à jour de l’optimisation de la distribution](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) dans la documentation Windows.  

> [!NOTE]
> Le paramètre **Mises à jour de logiciels – Boucles de mise à jour Windows 10** est remplacé par les paramètres **Optimisation de la distribution**. Il est possible de changer des boucles de mise à jour en paramètres **Optimisation de la distribution**. [Déplacer les boucles de mise à jour existantes pour l’optimisation de la distribution](#move-existing-update-rings-to-delivery-optimization) (dans cet article)

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Optimisation de la distribution**.

4. Choisissez **Paramètres** > **Configurer**, puis définissez le mode de téléchargement des mises à jour et des applications. Pour plus d’informations sur les paramètres disponibles, consultez [Paramètres d’optimisation de la distribution pour Intune](../delivery-optimization-settings.md).

5. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements.

Le profil est créé, puis apparaît dans la liste. Vous devez à présent [affecter le profil](device-profile-assign.md), puis [superviser son état](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Déplacer les boucles de mise à jour existantes pour l’optimisation de la distribution

Les paramètres **Optimisation de la distribution** remplacent **Mises à jour de logiciels – Boucles de mise à jour Windows 10**. Il est facile de changer des boucles de mise à jour en paramètres **Optimisation de la distribution**. Pour conserver les mêmes paramètres quand vous créez un profil d’optimisation de la distribution, utilisez le même *mode de téléchargement de l’optimisation de la distribution*, puis définissez les paramètres que vous utilisez déjà. Toutefois, vous pouvez choisir de reconfigurer les paramètres d’optimisation de la distribution pour tirer parti de la gamme complète des paramètres supplémentaires que le profil d’optimisation de la distribution peut gérer.

1. Créer un profil de configuration d’optimisation de la distribution :

    1. Dans le Centre d’administration du gestionnaire de points de terminaison Microsoft, sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
    2. Entrez les propriétés suivantes :

        - **Nom** : Entrez un nom descriptif pour le nouveau profil.
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
    1. Dans le Centre d’administration du gestionnaire de points de terminaison Microsoft, accédez à **Mises à jour logicielles** > Anneaux de mise à jour Windows 10.
    2. Dans la liste, sélectionnez votre boucle de mise à jour.
    3. Dans les paramètres, définissez le **Mode de téléchargement de l’optimisation de la distribution** sur **Non configuré**.
    4. **OK** > **Enregistrez** les modifications apportées.

## <a name="next-steps"></a>Étapes suivantes

[Affectez le profil](device-profile-assign.md) et [effectuez le monitoring de son état](device-profile-monitor.md).  
Voir les [paramètres d’optimisation de la distribution](../delivery-optimization-settings.md) pour Intune.
