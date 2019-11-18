---
title: Configurer des stratégies de mise à jour logicielle iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Dans Microsoft Intune, créez ou ajoutez une stratégie de configuration pour limiter les moments où les mises à jour logicielles s’installent automatiquement sur les appareils iOS. Vous pouvez choisir la date et l’heure auxquelles les mises à jour ne sont pas installées. Vous pouvez également affecter cette stratégie à des groupes, des utilisateurs ou des appareils, et vérifier si les installations ont réussi.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f9750603d19d9b19697c7d2660351c4586432f6
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984199"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Ajouter des stratégies de mise à jour de logiciel iOS dans Intune

Les stratégies de mise à jour logicielle vous permettent de forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour de système d’exploitation disponible. Lors de la configuration d’une stratégie, vous pouvez ajouter les jours et heures auxquelles vous ne souhaitez pas que les appareils installent une mise à jour.

Cette fonctionnalité s’applique à :

- iOS versions 10.3 et ultérieures (supervisé)

L’appareil effectue une vérification auprès d’Intune toutes les huit heures. Si une mise à jour est disponible, l’appareil la télécharge et l’installe, sauf pendant les heures restreintes. Bien que le processus de mise à jour n’implique généralement aucune interaction de l’utilisateur, si l’appareil a un code secret, l’utilisateur est invité à l’entrer pour lancer une mise à jour de logiciel. Cela s’applique à iOS 10.3 (et versions ultérieures). La stratégie n’empêche pas un utilisateur de mettre à jour le système d’exploitation manuellement.

## <a name="configure-the-policy"></a>Configurer la stratégie

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS** > **Créer**.
3. Sous l’onglet **De base**, spécifiez un nom pour cette stratégie, spécifiez une description (facultatif), puis sélectionnez **Suivant**.

   ![Onglet De base](./media/software-updates-ios/basics-tab.png) 

4. Sous l’onglet **Mettre à jour les paramètres de la stratégie**, spécifiez une plage de temps limitée durant laquelle les mises à jour ne peuvent pas être installées de force.  
   - Les blocs nocturnes ne sont pas pris en charge et risquent de ne pas fonctionner. Par exemple, ne configurez pas une stratégie avec une *heure de début* de 20h00 et une *heure de fin* de 6h00.
   - Une stratégie qui démarre à minuit et se termine à minuit couvre 0 heure, et non pas 24 heures. Cette configuration aboutit donc à une absence de restriction.

   Quand vous définissez la plage de temps limitée, entrez les informations suivantes :

   - **Jours** : choisissez le ou les jours de la semaine au cours desquels les mises à jour ne sont pas installées. Par exemple, cochez Lundi, Mercredi et Vendredi pour empêcher l’installation de mises à jour durant ces jours.
   - **Fuseau horaire** : choisissez un fuseau horaire.
   - **Heure de début** : choisissez l’heure de début de la plage de temps limitée. Par exemple, entrez 5h00 pour que les mises à jour ne soient pas installées à partir de 5h00.
   - **Heure de fin** : choisissez l’heure de fin de la plage de temps limitée. Par exemple, entrez 1h00 pour que les mises à jour puissent être installées à partir de 1h00.
  
   > [!IMPORTANT]  
   > Une stratégie dont l’*heure de début* et l’*heure de fin* sont définies sur minuit couvre 0 heure, et non pas 24 heures. Cette stratégie aboutit à l’absence de restriction.  
    
   Pour retarder la visibilité des mises à jour logicielles pendant un laps de temps spécifique sur vos appareils iOS supervisés, configurez ces paramètres dans [Restrictions de l’appareil](../configuration/device-restrictions-ios.md#general). Les stratégies de mise à jour logicielle remplacent toutes les restrictions d’appareil. Lorsque vous définissez une stratégie de mise à jour logicielle et une restriction pour retarder la visibilité des mises à jour logicielles, l’appareil force une mise à jour logicielle conformément à la stratégie. La restriction s’applique afin que les utilisateurs ne voient pas l’option leur permettant de mettre à jour l’appareil, et la mise à jour est repoussée à la première fenêtre de temps définie par votre stratégie de mise à jour iOS.

   Après avoir configuré *Mettre à jour les paramètres de la stratégie*, sélectionnez **Suivant**. 

5. Sous l’onglet **Balises d’étendue**, sélectionnez **+ Sélectionner des balises d’étendue** pour ouvrir le volet *Sélectionner des balises* si vous voulez appliquer des balises d’étendue à la stratégie de mise à jour.
   
   - Dans le volet **Sélectionner des balises**, choisissez une ou plusieurs balises, puis cliquez sur **Sélectionner** pour les ajouter à la stratégie et revenir au volet *Balises d’étendue*.  

   Quand vous êtes prêt, sélectionnez **Suivant** pour accéder à *Affectations*.

6. Sous l’onglet **Affectations**, choisissez **+ Sélectionner les groupes à inclure**, puis affectez la stratégie de mise à jour à un ou plusieurs groupes. Utilisez **+ Sélectionner les groupes à exclure** pour affiner l’affectation. Quand vous êtes prêt, sélectionnez **Suivant** pour continuer. 

   La conformité de la mise à jour des appareils utilisés par les utilisateurs ciblés par la stratégie de conformité est évaluée. Cette stratégie prend également en charge les appareils sans utilisateur.

7. Sous l’onglet **Vérifier + créer**, vérifiez les paramètres, puis sélectionnez **Créer** quand vous êtes prêt à enregistrer votre stratégie de mise à jour iOS. Votre nouvelle stratégie s’affiche dans la liste des stratégies de mise à jour pour iOS.


Pour obtenir des conseils de la part de l’équipe du support technique Intune, consultez [Différer la visibilité des mises à jour logicielles dans Intune pour les appareils supervisés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> La Gestion des appareils mobiles Apple ne vous permet de forcer un appareil à installer des mises à jour en fonction d’une certaine date ou heure.

## <a name="edit-a-policy"></a>Modifier une stratégie
Vous pouvez modifier une stratégie existante, notamment en changeant les heures restreintes :

1. Dans **Mises à jour logicielles**, sélectionnez **Mettre à jour les stratégies pour iOS**, puis sélectionnez la stratégie que vous souhaitez modifier.

2. Lorsque vous voyez les **propriétés** des stratégies, sélectionnez **Modifier** pour la page de stratégie que vous souhaitez modifier.  
   ![Modifier une stratégie](./media/software-updates-ios/edit-policy.png)   

3. Après avoir introduit une modification, sélectionnez **Vérifier + enregistrer** > **Enregistrer** pour enregistrer vos modifications et revenir aux *propriétés* des stratégies.  
 
> [!NOTE]
> Si les paramètres **Heure de début** et **Heure de fin** sont tous les deux définis sur minuit, Intune ne vérifie pas les restrictions relatives aux plages d’installation des mises à jour. Ainsi, toute configuration pour **Sélectionnez les heures durant lesquelles empêcher l’installation de mises à jour** est ignorée et les mises à jour peuvent s’installer à tout moment.  


## <a name="monitor-device-installation-failures"></a>Suivre les échecs d’installation d’appareil
<!-- 1352223 -->
**Mises à jour logicielles** > **Échecs d’installation pour les appareils iOS** affiche une liste des appareils iOS supervisés ciblés par une stratégie de mise à jour, ayant tenté d’effectuer une mise à jour et dont la mise à jour a échoué. Pour chaque appareil, vous pouvez afficher un état indiquant la raison pour laquelle l’appareil n’a pas été automatiquement mis à jour. Les appareils intègres et à jour ne sont pas affichés dans la liste. Les appareils marqués comme « À jour » disposent de la dernière mise à jour prise en charge par l’appareil lui-même.

## <a name="next-steps"></a>Étapes suivantes

[Superviser son état](../configuration/device-profile-monitor.md).
