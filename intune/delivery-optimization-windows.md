---
title: Paramètres d’optimisation de la distribution pour Windows 10 dans Microsoft Intune – Azure | Microsoft Docs
description: Configurez la façon dont les mises à jour de logiciels sont distribuées à vos appareils à l’aide des services cloud d’optimisation de la distribution disponibles avec les appareils Windows 10 (et versions ultérieures). Dans Intune, créez un profil de configuration d’appareil pour installer les mises à jour à partir d’Internet. Découvrez également comment remplacer des boucles de mise à jour par un profil d’optimisation de la distribution.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f335c8acf9e979366fe75d1a3da2318b7ec46400
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836691"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Paramètres d’optimisation de la distribution de Windows 10 (et versions ultérieures) dans Microsoft Intune

> [!NOTE]
> Le paramètre **Mises à jour de logiciels – Boucles de mise à jour Windows 10** est remplacé par les paramètres **Optimisation de la distribution**. Il est possible de changer des boucles de mise à jour en paramètres **Optimisation de la distribution**. [Déplacer les boucles de mise à jour existantes pour l’optimisation de la distribution](#move-existing-update-rings-to-delivery-optimization) (dans cet article) répertorie les étapes. 


Cette fonctionnalité s’applique à la plateforme suivante :

- Windows 10 et versions ultérieures

Cet article liste et décrit tous les paramètres d’optimisation de la distribution configurables sur des appareils Windows 10. Ces paramètres sont ajoutés à un profil de configuration d’appareil, puis affectés ou déployés sur les appareils avec Microsoft Intune.

Pour plus d’informations sur l’optimisation de la distribution sur Windows 10, consultez [Configurer l’optimisation de la distribution des mises à jour Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.

2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.

3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : sélectionnez la plateforme :  

        - **Windows 10 et versions ultérieures**

    - **Type de profil** : Sélectionnez **Optimisation de la distribution**.
    - **Paramètres** : Choisissez comment vous souhaitez que les mises à jour soient téléchargées. Les options disponibles sont les suivantes : 

        - **Non configuré** : les utilisateurs finaux mettent à jour leurs appareils suivant la méthode de leur choix (**Windows Update** ou paramètres **Optimisation de la distribution** proposés par le système d’exploitation).
        - **HTTP uniquement, sans appairage** : recevez exclusivement les mises à jour issues d’Internet. et non celles qui proviennent d’autres ordinateurs présents sur le réseau (peering ou pair à pair).
        - **HTTP fusionné avec le peering derrière le même NAT** : recevez les mises à jour provenant d’Internet et d’autres ordinateurs présents sur le réseau. 
        - **HTTP fusionné avec le peering sur un groupe privé** : Le peering se produit sur les appareils du même site Active Directory (s’il existe) ou du même domaine. Lorsque cette option est sélectionnée, il croise les adresses IP de la traduction d’adresses réseau (NAT).
        - **HTTP fusionné avec un appairage Internet** : recevez les mises à jour provenant d’Internet et d’autres ordinateurs présents sur le réseau.
        - **Mode de téléchargement simple sans appairage** : recevez les mises à jour provenant d’Internet et émises par le propriétaire des mises à jour, par exemple, Microsoft. Il ne contacte pas les services de cloud d’optimisation de la distribution.
        - **Mode contournement** : utilisez le Service de transfert intelligent en arrière-plan (BITS) pour recevoir des mises à jour. N’utilisez pas l’optimisation de la distribution.

4. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements.

Le profil est créé et apparaît dans la liste. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Déplacer les boucles de mise à jour existantes pour l’optimisation de la distribution

Le paramètre **Mises à jour de logiciels – Boucles de mise à jour Windows 10** est remplacé par les paramètres **Optimisation de la distribution**. Il est facile de changer des boucles de mise à jour en paramètres **Optimisation de la distribution**. Étapes :

1. Créer un profil de configuration d’optimisation de la distribution :

    1. Dans Intune, sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
    2. Entrez les propriétés suivantes :

        - **Nom** : Entrez un nom descriptif pour le nouveau profil.
        - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
        - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
        - **Type de profil** : Sélectionnez **Optimisation de la distribution**.
        - **Paramètres** : Pour **Mode de téléchargement de l’optimisation de la distribution**, choisissez le mode utilisé par la boucle de mise à jour de logiciel existante. Les options disponibles sont les suivantes :
            - **Non configuré**
            - **HTTP uniquement, sans peering**
            - **HTTP fusionné avec le peering derrière le même NAT**
            - **HTTP fusionné avec le peering sur un groupe privé**
            - **Mélange HTTP/peering Internet**
            - **Mode de téléchargement simple sans peering**
            - **Mode de contournement**

2. Affectez ce nouveau profil aux mêmes appareils et utilisateurs que la boucle de mise à jour de logiciels existante. La page [Affectez le profil](device-profile-assign.md) liste les étapes à suivre.

3. Supprimez la configuration de la boucle logicielle existante :
    1. Dans Intune, accédez à **Mises à jour de logiciels** > Boucles de mise à jour Windows 10.
    2. Dans la liste, sélectionnez votre boucle de mise à jour.
    3. Dans les paramètres, définissez le **Mode de téléchargement de l’optimisation de la distribution** sur **Non configuré**.
    4. **OK** > **Enregistrez** les modifications apportées.

## <a name="next-steps"></a>Étapes suivantes

[Affectez le profil](device-profile-assign.md) et [effectuez le monitoring de son état](device-profile-monitor.md).
