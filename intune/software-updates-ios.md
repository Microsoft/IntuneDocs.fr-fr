---
title: Configurer des stratégies de mise à jour logicielle iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Dans Microsoft Intune, créez ou ajoutez une stratégie de configuration pour contrôler l’installation automatique des mises à jour logicielles sur les appareils iOS gérés ou surveillés par Intune. Vous pouvez choisir la date et l’heure auxquelles les mises à jour ne sont pas installées. Vous pouvez également affecter cette stratégie à des groupes, des utilisateurs ou des appareils, et vérifier si les installations ont réussi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: fdd33ea0b5d8189712c6390861131c684cfaa67d
ms.sourcegitcommit: ab08dd841f16ae11f958c43b6262a9f6a0cabdd4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49101951"
---
# <a name="configure-ios-update-policies-in-intune"></a>Configurer des stratégies de mise à jour iOS dans Intune

Les stratégies de mise à jour logicielle vous permettent de forcer les appareils iOS supervisés à installer automatiquement la dernière mise à jour de système d’exploitation disponible. Cette fonctionnalité est disponible uniquement pour les appareils supervisés. Lors de la configuration d’une stratégie, vous pouvez ajouter les jours et heures auxquelles vous ne souhaitez pas que les appareils installent une mise à jour. 

L’appareil effectue une vérification auprès d’Intune toutes les huit heures. Si une mise à jour est disponible, et qu’il ne s’agit pas d’une période limitée, l’appareil télécharge et installe la dernière mise à jour du système d’exploitation. Aucune interaction utilisateur n’est nécessaire pour mettre à jour l’appareil. La stratégie n’empêche pas un utilisateur de mettre à jour le système d’exploitation manuellement.

Cette fonctionnalité prend en charge les appareils exécutant iOS 10.3 et versions ultérieures. Le paramètre de délai est disponible dans iOS 11.3 et les versions ultérieures.

## <a name="configure-the-policy"></a>Configurer la stratégie
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Mises à jour logicielles** > **Mettre à jour les stratégies pour iOS** > **Créer**.
4. Entrez un nom et une description pour la stratégie.
5. Cliquez sur **Paramètres**. 

    Indiquez quand les appareils iOS ne sont pas forcés à installer les dernières mises à jour. Ces paramètres créent une plage de temps limitée. Vous pouvez configurer les **Jours** de la semaine, le **Fuseau horaire**, **l’heure de début**, **l’heure de fin** et s’il faut **Retarder la visibilité des mises à jour logicielles (en jours)** pour entrer des utilisateurs. Vous pouvez sélectionner une plage de délai des mises à jour logicielles comprise entre 1 et 90 jours. Pour ne pas définir de délai pour les mises à jour logicielles, entrez 0. Ces paramètres de mise à jour s’appliquent seulement aux appareils iOS supervisés.

6. Cliquez sur **OK** pour enregistrer vos modifications. Sélectionnez **Créer** pour créer la stratégie.

Le profil est créé et affiché dans la liste des stratégies. La Gestion des appareils mobiles Apple ne vous permet de forcer un appareil à installer des mises à jour en fonction d’une certaine date ou heure. 

## <a name="change-the-restricted-times-for-the-policy"></a>Changer les heures restreintes de la stratégie

1. Dans **Mises à jour logicielles**, sélectionnez **Mettre à jour les stratégies pour iOS**.
2. Choisissez une stratégie existante > **Propriétés**.
3. Mettez à jour la période limitée :

    1. Choisir les jours de la semaine
    2. Choisissez le fuseau horaire dans lequel cette stratégie est appliquée.
    3. Entrez l’heure de début et de fin pour les heures sur liste rouge.

    > [!NOTE]
    > Si l’**Heure de début** et l’**Heure de fin** sont toutes deux définies sur minuit, la vérification de temps de maintenance est désactivée.

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

