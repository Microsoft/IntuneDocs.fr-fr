---
title: Configurer des stratégies de mise à jour logicielle iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Dans Microsoft Intune, créez ou ajoutez une stratégie de configuration pour contrôler l’installation automatique des mises à jour logicielles sur les appareils iOS gérés ou surveillés par Intune. Vous pouvez choisir la date et l’heure auxquelles les mises à jour ne sont pas installées. Vous pouvez également affecter cette stratégie à des groupes, des utilisateurs ou des appareils, et vérifier si les installations ont réussi.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf07f942feeab0a73c01625f90c04ec3b989c1c2
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044854"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Ajouter des stratégies de mise à jour de logiciel iOS dans Intune

Les stratégies de mise à jour logicielle vous permettent de forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour de système d’exploitation disponible. Lors de la configuration d’une stratégie, vous pouvez ajouter les jours et heures auxquelles vous ne souhaitez pas que les appareils installent une mise à jour. 

Cette fonctionnalité s’applique à :

- iOS versions 10.3 et ultérieures (supervisé)

L’appareil effectue une vérification auprès d’Intune toutes les huit heures. Si une mise à jour est disponible, et qu’il ne s’agit pas d’une période limitée, l’appareil télécharge et installe la dernière mise à jour du système d’exploitation. Aucune interaction utilisateur n’est nécessaire pour mettre à jour l’appareil. La stratégie n’empêche pas un utilisateur de mettre à jour le système d’exploitation manuellement.

## <a name="configure-the-policy"></a>Configurer la stratégie

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.
2. Sélectionnez **Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS** > **Créer**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour votre stratégie de mises à jour de logiciel. Par exemple, entrez `iOS restricted update times`.
    - **Description** : entrez une description pour votre stratégie. Ce paramètre est facultatif, mais recommandé.

4. Sélectionnez **Paramètres > Configurer**. entrez les paramètres suivants :

    - **Sélectionnez les heures durant lesquelles empêcher l’installation de mises à jour** : spécifiez une plage de temps limitée durant laquelle les mises à jour ne peuvent pas être installées de force. 
      - Les blocs nocturnes ne sont pas pris en charge et risquent de ne pas fonctionner. Par exemple, ne configurez pas une stratégie avec une *heure de début* de 20h00 et une *heure de fin* de 6h00.
      - Une stratégie qui démarre à minuit et se termine à minuit couvre 0 heure, et non pas 24 heures ; elle aboutit donc à l’absence de restriction.

      Quand vous définissez la plage de temps limitée, entrez les informations suivantes :

      - **Jours** : choisissez le ou les jours de la semaine au cours desquels les mises à jour ne sont pas installées. Par exemple, cochez Lundi, Mercredi et Vendredi pour empêcher l’installation de mises à jour durant ces jours.
      - **Fuseau horaire** : choisissez un fuseau horaire.
      - **Heure de début** : choisissez l’heure de début de la plage de temps limitée. Par exemple, entrez 5h00 pour que les mises à jour ne soient pas installées à partir de 5h00.
      - **Heure de fin** : choisissez l’heure de fin de la plage de temps limitée. Par exemple, entrez 1h00 pour que les mises à jour puissent être installées à partir de 1h00.

    - **Différer la visibilité des mises à jour logicielles pour les utilisateurs finaux sans changer les mises à jour planifiées (jours)**  : 

      **Ce paramètre a été déplacé vers [Restrictions de l’appareil](device-restrictions-ios.md#general). Il sera supprimé de cet emplacement dans le portail**. Pendant une courte période, les stratégies existantes peuvent être changées ici. Après environ un mois, ce paramètre sera supprimé des stratégies existantes.

      Pour limiter l’impact, nous vous recommandons de :
        - Supprimer la stratégie existante de cet emplacement dans le portail
        - Créer une [stratégie de restriction d’appareil](device-restrictions-ios.md#general)
        - Cibler les mêmes utilisateurs que la stratégie d’origine

      En cas de conflit, ce paramètre n’a aucun effet, *sauf si* les deux valeurs sont identiques. Pour éviter un conflit, veillez à changer la stratégie existante ou à la supprimer de cet emplacement dans le portail.
      > [! Important]  
      > Une stratégie dont l’*heure de début* et l’*heure de fin* sont définies sur minuit couvre 0 heure, et non pas 24 heures. Cette stratégie aboutit à l’absence de restriction.  

5. Sélectionnez **OK** > **Créer** pour enregistrer vos changements et créer la stratégie.

Le profil est créé et affiché dans la liste des stratégies.

Pour obtenir des conseils de la part de l’équipe du support technique Intune, consultez [Différer la visibilité des mises à jour logicielles dans Intune pour les appareils supervisés](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> La Gestion des appareils mobiles Apple ne vous permet de forcer un appareil à installer des mises à jour en fonction d’une certaine date ou heure.

## <a name="change-the-restricted-times-for-the-policy"></a>Changer les heures restreintes de la stratégie

1. Dans **Mises à jour logicielles**, sélectionnez **Mettre à jour les stratégies pour iOS**.
2. Choisissez une stratégie existante > **Propriétés**.
3. Mettez à jour la période limitée :

    1. Choisir les jours de la semaine
    2. Choisissez le fuseau horaire dans lequel cette stratégie est appliquée.
    3. Entrez l’heure de début et de fin pour les heures sur liste rouge.

    > [!NOTE]
    > Si l’**heure de début** et l’**heure de fin** sont toutes deux définies sur minuit, Intune ne vérifie pas les restrictions relatives aux plages d’installation des mises à jour. Ainsi, toute configuration pour **Sélectionnez les heures durant lesquelles empêcher l’installation de mises à jour** est ignorée et les mises à jour peuvent s’installer à tout moment.  

## <a name="assign-the-policy-to-users"></a>Affecter la stratégie à des utilisateurs

Les stratégies existantes sont affectées à des groupes, des utilisateurs ou des appareils. Une fois affectée, la stratégie est appliquée.

1. Dans **Mises à jour logicielles**, sélectionnez **Mettre à jour les stratégies pour iOS**.
2. Choisissez une stratégie existante > **Affectations**. 
3. Sélectionnez des groupes, des utilisateurs ou des appareils Azure Active Directory à inclure ou exclure de cette stratégie.
4. Choisissez **Enregistrer** pour déployer la stratégie sur vos groupes.

La conformité de la mise à jour des appareils utilisés par les utilisateurs ciblés par la stratégie de conformité est évaluée. Cette stratégie prend également en charge les appareils sans utilisateur.

## <a name="monitor-device-installation-failures"></a>Suivre les échecs d’installation d’appareil
<!-- 1352223 -->
**Mises à jour logicielles** > **Échecs d’installation pour les appareils iOS** affiche une liste des appareils iOS supervisés ciblés par une stratégie de mise à jour, ayant tenté d’effectuer une mise à jour et dont la mise à jour a échoué. Pour chaque appareil, vous pouvez afficher un état indiquant la raison pour laquelle l’appareil n’a pas été automatiquement mis à jour. Les appareils intègres et à jour ne sont pas affichés dans la liste. Les appareils marqués comme « À jour » disposent de la dernière mise à jour prise en charge par l’appareil lui-même.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
