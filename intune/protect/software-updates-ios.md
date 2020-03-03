---
title: Configurer des stratégies de mise à jour logicielle iOS/iPadOS dans Microsoft Intune - Azure | Microsoft Docs
description: Dans Microsoft Intune, créez ou ajoutez une stratégie de configuration pour limiter les moments où les mises à jour logicielles s’installent automatiquement sur les appareils iOS/iPadOS. Vous pouvez choisir la date et l’heure auxquelles les mises à jour ne sont pas installées. Vous pouvez également affecter cette stratégie à des groupes, des utilisateurs ou des appareils, et vérifier si les installations ont réussi.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576149"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Ajouter des stratégies de mise à jour logicielle iOS/iPadOS dans Intune

Les stratégies de mise à jour logicielle vous permettent de forcer les appareils iOS/iPadOS supervisés à installer automatiquement les mises à jour du système d’exploitation. Les appareils supervisés sont ceux qui sont inscrits avec Apple Business Manager ou Apple School Manager. Lors de la configuration d’une stratégie pour déployer des mises à jour, vous pouvez :

- Choisissez de déployer la *mise à jour la plus récente* qui est disponible, ou choisissez de déployer une mise à jour plus ancienne sur la base du numéro de version de la mise à jour si vous ne voulez pas déployer la dernière mise à jour. Si vous choisissez de déployer une mise à jour plus ancienne, vous devez aussi définir une stratégie de configuration d’appareil pour limiter la visibilité des mises à jour logicielles.
- Spécifiez une planification qui détermine le moment où la mise à jour est installée. Les planifications peuvent être simplement l’installation des mises à jour lors de la prochaine vérification de l’appareil, ou la création de plages de dates et d’heures pendant lesquelles les mises à jour peuvent être installées ou dont l’installation est bloquée.

Cette fonctionnalité s’applique à :

- iOS versions 10.3 et ultérieures (supervisé)

Par défaut, les appareils effectuent un check-in avec Intune toutes les 8 heures. Si une mise à jour est disponible via une stratégie de mise à jour, l’appareil télécharge la mise à jour. L’appareil installe ensuite la mise à jour lors du check-in suivant dans votre configuration de planification. Bien que le processus de mise à jour n’implique généralement aucune interaction de l’utilisateur, si l’appareil a un code secret, l’utilisateur doit l’entrer pour démarrer une mise à jour logicielle. Les profils n’empêchent pas les utilisateurs de mettre à jour le système d’exploitation manuellement. Il est possible d’empêcher les utilisateurs d’effectuer une mise à jour manuelle du système d’exploitation avec une stratégie de configuration d’appareil pour limiter la visibilité des mises à jour logicielles.

## <a name="configure-the-policy"></a>Configurer la stratégie

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Mettre à jour les stratégies pour iOS/iPadOS** > **Créer un profil**.
3. Sous l’onglet **De base**, spécifiez un nom pour cette stratégie, spécifiez une description (facultatif), puis sélectionnez **Suivant**.

   ![Onglet De base](./media/software-updates-ios/basics-tab.png)

4. Sous l’onglet **Paramètres de stratégie de mise à jour**, configurez les éléments suivants :

   1. **Sélectionner la version à installer**. Vous pouvez choisir :

      - *Dernière mise à jour* : Ceci déploie la mise à jour la plus récemment publiée pour iOS/iPadOS.
      - Toute version précédente disponible dans la zone de liste déroulante. Si vous sélectionnez une version antérieure, vous devez aussi déployer une stratégie de configuration des appareils pour retarder la visibilité des mises à jour logicielles.

   2. **Type de calendrier** : Configurez la planification pour cette stratégie :

      - *Mettre à jour lors du check-in suivant* : La mise à jour s’installe sur l’appareil lors du check-in suivant avec Intune. Il s’agit de l’option la plus simple, qui ne nécessite pas de configuration supplémentaire.
      - *Mettre à jour pendant l’intervalle planifié* : Vous configurez une ou plusieurs fenêtres de temps pendant lesquelles la mise à jour sera installée suite au check-in.
      - *Mettre à jour en dehors de l’intervalle planifié* : Vous configurez une ou plusieurs fenêtres de temps pendant lesquelles les mises à jour ne seront pas installées suite au check-in.

   3. **Planification hebdomadaire** : Si vous choisissez un type de planification autre que *Mettre à jour lors du check-in suivant*, configurez les options suivantes :

      ![Exemple de sélection pour mettre à jour pendant la plage de temps planifiée](./media/software-updates-ios/scheduled-time.png)

      - **Fuseau horaire** : choisissez un fuseau horaire.
      - **Fenêtre de temps** : Définissez une ou plusieurs plages de temps qui limitent le moment où les mises à jour sont installées. L’effet des options suivantes dépend du type de planification que vous avez sélectionné. En utilisant un jour de début et de fin, les plages nocturnes sont prises en charge. Les options sont les suivantes :

        - **Jour de début** : Choisissez le jour du début de la fenêtre de planification.
        - **Heure de début** : Choisissez le jour de la fin de la fenêtre de planification. Par exemple, si vous sélectionnez 5:00 et que vous avez un type de planification *Mettre à jour pendant l’intervalle planifié*, les mises à jour logicielles peuvent commencer à 5:00. Si vous avez choisi un type de planification *Mettre à jour en dehors de l’intervalle planifié*, 5:00 est le début de la période de temps pendant laquelle les mises à jour ne peuvent pas être installées.
        - **Jour de fin** : Choisissez le jour de fin de la fenêtre de planification.
        - **Heure de fin** : Choisissez l’heure de fin de la fenêtre de planification. Par exemple, si vous sélectionnez 1:00 et que vous avez un type de planification *Mettre à jour pendant l’intervalle planifié*, 1:00 est l’heure à laquelle les mises à jour logicielles ne peuvent plus s’installer. Si vous avez choisi un type de planification *Mettre à jour en dehors de l’intervalle planifié*, 1:00 est le début de la période de temps pendant laquelle les mises à jour peuvent s’installer.

       Si vous ne configurez pas les heures de début ou de fin, la configuration n’a aucune restriction et les mises à jour peuvent être installées à tout moment.  

       > [!NOTE]
       > Pour retarder la visibilité des mises à jour logicielles pendant un laps de temps spécifique sur vos appareils iOS/iPadOS supervisés, configurez ces paramètres dans [Restrictions de l’appareil](../configuration/device-restrictions-ios.md#general). Les stratégies de mise à jour logicielle remplacent toutes les restrictions d’appareil. Lorsque vous définissez une stratégie de mise à jour logicielle et une restriction pour retarder la visibilité des mises à jour logicielles, l’appareil force une mise à jour logicielle conformément à la stratégie. La restriction s’applique : les utilisateurs ne voient donc pas l’option leur permettant de mettre à jour l’appareil, et la mise à jour est repoussée comme défini par votre stratégie de mise à jour d’iOS.

   Après avoir configuré *Mettre à jour les paramètres de la stratégie*, sélectionnez **Suivant**.

5. Sous l’onglet **Balises d’étendue**, sélectionnez **+ Sélectionner des balises d’étendue** pour ouvrir le volet *Sélectionner des balises* si vous voulez appliquer des balises d’étendue à la stratégie de mise à jour.

   - Dans le volet **Sélectionner des balises**, choisissez une ou plusieurs balises, puis cliquez sur **Sélectionner** pour les ajouter à la stratégie et revenir au volet *Balises d’étendue*.

   Quand vous êtes prêt, sélectionnez **Suivant** pour accéder à *Affectations*.

6. Sous l’onglet **Affectations**, choisissez **+ Sélectionner les groupes à inclure**, puis affectez la stratégie de mise à jour à un ou plusieurs groupes. Utilisez **+ Sélectionner les groupes à exclure** pour affiner l’affectation. Quand vous êtes prêt, sélectionnez **Suivant** pour continuer.

   La conformité de la mise à jour des appareils utilisés par les utilisateurs ciblés par la stratégie de conformité est évaluée. Cette stratégie prend également en charge les appareils sans utilisateur.

7. Sous l’onglet **Vérifier + créer**, vérifiez les paramètres, puis sélectionnez **Créer** quand vous êtes prêt à enregistrer votre stratégie de mise à jour d’iOS/iPadOS. Votre nouvelle stratégie s’affiche dans la liste des stratégies de mise à jour pour iOS/iPadOS.

Pour obtenir des conseils de la part de l’équipe du support technique Intune, consultez [Différer la visibilité des mises à jour logicielles dans Intune pour les appareils supervisés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> La Gestion des appareils mobiles Apple ne vous permet de forcer un appareil à installer des mises à jour en fonction d’une certaine date ou heure. Vous ne pouvez pas utiliser les stratégies de mise à jour logicielle Intune pour rétrograder la version du système d’exploitation sur un appareil.

## <a name="edit-a-policy"></a>Modifier une stratégie

Vous pouvez modifier une stratégie existante, notamment en changeant les heures restreintes :

1. Sélectionnez **Appareils** > **Mettre à jour les stratégies pour iOS**. Sélectionnez la stratégie à modifier.

2. Lorsque vous voyez les **propriétés** des stratégies, sélectionnez **Modifier** pour la page de stratégie que vous souhaitez modifier.

   ![Modifier une stratégie](./media/software-updates-ios/edit-policy.png)

3. Après avoir introduit une modification, sélectionnez **Vérifier + enregistrer** > **Enregistrer** pour enregistrer vos modifications et revenir aux *propriétés* des stratégies.

> [!NOTE]
> Si les paramètres **Heure de début** et **Heure de fin** sont tous les deux définis sur minuit, Intune ne vérifie pas les restrictions relatives aux plages d’installation des mises à jour. Ainsi, toute configuration pour **Sélectionnez les heures durant lesquelles empêcher l’installation de mises à jour** est ignorée et les mises à jour peuvent s’installer à tout moment.

## <a name="monitor-device-installation-failures"></a>Suivre les échecs d’installation d’appareil

<!-- 1352223 -->
**Mises à jour logicielles** > **Échecs d’installation pour les appareils iOS** montre une liste des appareils iOS/iPadOS supervisés ciblés par une stratégie de mise à jour, ayant tenté d’effectuer une mise à jour et dont la mise à jour a échoué. Pour chaque appareil, vous pouvez afficher un état indiquant la raison pour laquelle l’appareil n’a pas été automatiquement mis à jour. Les appareils intègres et à jour ne sont pas affichés dans la liste. Les appareils marqués comme « À jour » disposent de la dernière mise à jour prise en charge par l’appareil lui-même.

## <a name="next-steps"></a>Étapes suivantes

[Superviser son état](../configuration/device-profile-monitor.md).
