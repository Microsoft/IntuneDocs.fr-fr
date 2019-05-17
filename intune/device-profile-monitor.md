---
title: Voir les profils d’appareil avec Microsoft Intune - Azure | Microsoft Docs
description: Affichez et gérez les informations détaillées des profils de configuration d’appareil dans Microsoft Intune, consultez un graphique du nombre d’appareils attribués à un profil, et découvrez quels appareils ont des profils attribués ou déployés. Vous pouvez aussi résoudre les problèmes des profils qui ont des paramètres en conflit.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 786cd6e7d0acaeb6e78035d8ec580c30d29d09e7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57391705"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Suivre les profils d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune inclut certaines fonctionnalités dans le portail Azure pour faciliter le monitoring et la gestion de vos profils de configuration d’appareil. Vous pouvez, par exemple, vérifier l’état d’un profil, consulter les appareils attribués et mettre à jour les propriétés d’un profil.

## <a name="view-existing-profiles"></a>Afficher les profils existants

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils**.

Tous vos profils existants sont répertoriés et incluent des informations détaillées, comme la plateforme et si le profil est attribué à des appareils.

## <a name="view-details-on-a-profile"></a>Afficher les détails d’un profil

Une fois le profil d’appareil créé, Intune fournit des graphiques. Ces graphiques affichent l’état d’un profil, à savoir s’il a été attribué correctement à des appareils ou si le profil indique un conflit.

1. Sélectionnez un profil existant. Par exemple, sélectionnez un profil macOS.
2. Sélectionnez l’onglet **Vue d’ensemble**.

    Le graphique du haut montre le nombre d’appareils attribués au profil d’appareil spécifique. Par exemple, si le profil d’appareil de la configuration s’applique aux appareils macOS, le graphique indique le nombre des appareils macOS.

    Il indique également le nombre d’appareils pour d’autres plateformes ayant le même profil d’appareil. Par exemple, il affiche le nombre d’appareils non macOS.

    ![Afficher le nombre d’appareils attribués au profil d’appareil](./media/device-configuration-profile-graphical-chart.png)

    Le graphique du bas montre le nombre d’utilisateurs attribués au profil d’appareil spécifique. Par exemple, si le profil d’appareil de la configuration s’applique aux utilisateurs macOS, le graphique indique le nombre d’utilisateurs macOS.

3. Sélectionnez le cercle dans le graphique du haut. **État de l’appareil** s’ouvre.

    Les appareils attribués au profil sont répertoriés et il est indiqué si le profil est déployé avec succès. Notez également que seuls les appareils avec la plateforme spécifique sont répertoriés (par exemple, macOS).

    Fermez les informations**État de l’appareil**.

4. Sélectionnez le cercle dans le graphique du bas. **État de l’utilisateur** s’ouvre. 

    Les utilisateurs attribués au profil sont répertoriés et les informations indiquent si le profil est déployé avec succès. Notez également que seuls les utilisateurs avec la plateforme spécifique sont répertoriés (par exemple, macOS).

    Fermez les informations **État de l’utilisateur**.

5. De retour dans la liste **Profils**, sélectionnez un profil spécifique. Vous pouvez également changer les propriétés existantes :
  - **Propriétés** : Modifiez le nom, ou mettez à jour les paramètres existants.
  - **Affectations** : Incluez ou excluez les appareils que la stratégie doit concerner. Choisissez **Groupes sélectionnés** pour choisir des groupes spécifiques.
  - **État de l’appareil** : Les appareils attribués au profil sont répertoriés et il est indiqué si le profil est déployé avec succès. Vous pouvez sélectionner un appareil spécifique pour obtenir davantage d’informations, notamment les applications installées.
  - **État de l’utilisateur** : Répertorie les noms d’utilisateur avec les appareils concernés par ce profil, et indique si le profil est déployé avec succès. Vous pouvez sélectionner un utilisateur spécifique pour obtenir davantage d’informations.
  - **État par paramètre** : Filtre la sortie en affichant les paramètres individuels au sein du profil, et indique si le paramètre est correctement appliqué.

## <a name="view-conflicts"></a>Visualiser les conflits

Dans **Appareils** > **Tous les appareils**, vous pouvez voir les paramètres qui provoquent un conflit. Quand il existe un conflit, vous voyez également tous les profils de configuration qui contiennent ce paramètre. Les administrateurs peuvent utiliser cette fonctionnalité pour résoudre et corriger les éventuelles incohérences dans les profils.

1. Dans Intune, sélectionnez **Appareils** > **Tous les appareils** > sélectionnez un appareil existant dans la liste. Un utilisateur final peut obtenir le nom de l’appareil à partir de son application Portail d’entreprise.
2. Sélectionnez **Configuration de l’appareil**. Toutes les stratégies de configuration qui s’appliquent à l’appareil sont listées.
3. Sélectionnez la stratégie. Ceci vous montre tous les paramètres de cette stratégie qui s’appliquent à l’appareil. Si un appareil a un état **Conflit**, sélectionnez cette ligne. Dans la nouvelle fenêtre, vous voyez tous les profils et les noms des profils qui ont le paramètre à l’origine du conflit.

Maintenant que vous savez quel paramètre provoque un conflit et quelles stratégies incluent ce paramètre, il doit être plus facile de résoudre le conflit. 

## <a name="next-steps"></a>Étapes suivantes
[Attribuer des profils d’utilisateur et d’appareil](device-profile-assign.md)  
[Problèmes courants avec les profils d’appareil et résolutions](device-profile-troubleshoot.md)
