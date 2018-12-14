---
title: Surveiller les stratégies de conformité des appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le tableau de bord de conformité des appareils pour analyser la conformité globale des appareils, afficher des rapports et afficher la conformité des appareils par stratégie et par paramètre.
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
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e26de8691e78e4b35e8618c48f38c7972af233f8
ms.sourcegitcommit: 88f760abcea7348a0c6d00b533b54a6ff68d3985
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977301"
---
# <a name="monitor-intune-device-compliance-policies"></a>Surveiller les stratégies de conformité d’appareils Intune

Les rapports de conformité vous permettent d’examiner la conformité des appareils et de résoudre les problèmes liés à la conformité dans votre organisation. Avec ces rapports, vous pouvez voir des informations sur :

- Les états de conformité globale des appareils
- L’état de conformité pour un paramètre spécifique
- L’état de conformité pour une stratégie spécifique
- Explorer des appareils spécifiques pour voir des paramètres et des stratégies spécifiques qui affectent l’appareil

## <a name="open-the-compliance-dashboard"></a>Ouvrir le tableau de bord de conformité

Ouvrez le **Tableau de bord de conformité des appareils Intune** :

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.

2. Sélectionnez **Conformité de l’appareil** > **Vue d’ensemble**. Le **tableau de bord de conformité des appareils** s’ouvre.

> [!IMPORTANT]
> Les appareils doivent être inscrits dans Intune pour recevoir des stratégies de conformité d’appareils.

## <a name="dashboard-overview"></a>Vue d’ensemble du tableau de bord

Quand le tableau de bord s’ouvre, vous obtenez une vue d’ensemble avec tous les rapports de conformité. Dans ces rapports, vous pouvez voir et vérifier les éléments suivants :

- Conformité globale des appareils
- Conformité des appareils par stratégie
- Conformité des appareils par paramètre
- État de la protection d’appareil
- État de l’agent de menace

![Image du tableau de bord montrant le tableau de bord de conformité des appareils et les différents rapports](./media/compliance-policy-monitor/idc-1.png)

En explorant ce rapport, vous pouvez également voir toutes les stratégies et paramètres de conformité spécifiques qui s’appliquent à un appareil individuel, avec l’état de conformité pour chaque paramètre.

### <a name="device-compliance-status-report"></a>Rapport d’état de conformité des appareils

Le graphique montre les états de conformité pour tous les appareils inscrits auprès d’Intune. Les états de conformité des appareils sont conservés dans deux bases de données : Intune et Azure Active Directory. 

> [!IMPORTANT]
> Intune suit la planification des enregistrements de l’appareil pour toutes les évaluations de conformité sur l’appareil. [Découvrez-en plus sur la planification des enregistrements d’appareils](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Descriptions des différents états des stratégies de conformité des appareils :

- **Conforme** : l’appareil a correctement appliqué un ou plusieurs paramètres de stratégie de conformité d’appareil.

- **Période de grâce** : l’appareil est ciblé par un ou plusieurs paramètres de stratégie de conformité d’appareil. L’utilisateur n’a cependant pas encore appliqué les stratégies. Cela signifie que l’appareil n’est pas conforme, mais qu’il est dans la période de grâce définie par l’administrateur.

  - Découvrez plus d’informations sur les [Actions destinées aux appareils non conformes](actions-for-noncompliance.md).

- **Non évalué** : état initial des nouveaux appareils inscrits. Il peut aussi s’agir d’appareils auxquels aucune stratégie de conformité n’a été affectée et qui n’ont pas de déclencheur pour vérifier leur conformité.

- **Non conforme** : l’appareil n’a pas pu appliquer un ou plusieurs paramètres de stratégie de conformité d’appareil. L’autre possibilité est que l’utilisateur ne s’est pas conformé aux stratégies.

- **Appareil non synchronisé** : l’appareil n’a pas pu signaler l’état de sa stratégie de conformité d’appareil pour l’une des raisons suivantes :

  - **Inconnu** : l’appareil est hors connexion ou n’a pas pu communiquer avec Intune ou Azure AD pour d’autres raisons.

  - **Erreur** : l’appareil n’a pas pu communiquer avec Intune et Azure AD, et a reçu un message d’erreur avec la raison.

> [!IMPORTANT]
> Les appareils inscrits dans Intune, mais non ciblés par des stratégies de conformité des appareils, sont inclus dans ce rapport sous le compartiment **Conforme**.

#### <a name="drill-down-for-more-details"></a>Explorer pour voir plus de détails

Dans le graphique **État de conformité des appareils**, sélectionnez un état. Par exemple, sélectionnez l’état **Non conforme** :

![Choisir l’état Non conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

Il vous montre plus de détails sur les appareils dans cet état, notamment la plateforme du système d’exploitation, la dernière date d’enregistrement et d’autres informations. 

![Image du tableau de bord montrant plus d’informations sur l’appareil dans cet état spécifique](./media/compliance-policy-monitor/drill-down-details.png)

Si vous voulez voir tous les appareils appartenant à un utilisateur spécifique, vous pouvez aussi filtrer le rapport graphique en tapant l’e-mail de l’utilisateur.

#### <a name="filter-and-columns"></a>Filtrer et Colonnes

![Sélectionnez Filtrer et Colonne pour changer les résultats apparaissant dans le graphique](./media/compliance-policy-monitor/filter-columns.png)

Quand vous sélectionnez le bouton **Filtrer**, le menu déroulant du filtre s’ouvre avec plus d’options, notamment l’état de conformité, les appareils jailbreakés et d’autres possibilités. **Appliquez** le filtre pour mettre à jour les résultats.

Utilisez la propriété **Colonnes** pour ajouter ou supprimer des colonnes dans la sortie graphique. Par exemple, **Nom principal de l’utilisateur** peut faire apparaître l’adresse e-mail inscrite sur l’appareil. **Appliquez** les colonnes pour mettre à jour les résultats.

#### <a name="device-details"></a>Détails sur l'appareil

Dans le graphique, sélectionnez un appareil spécifique, puis sélectionnez **Conformité de l’appareil** :

![Choisir un appareil spécifique, puis Conformité de l’appareil pour voir les stratégies de conformité appliquées](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Ceci fournit plus de détails sur les paramètres de stratégie de conformité d’appareil appliqués sur cet appareil. Quand vous sélectionnez la stratégie spécifique, tous les paramètres de la stratégie apparaissent.

### <a name="devices-without-compliance-policy"></a>Appareils sans stratégie de conformité
Dans **Conformité des appareils** > **Vue d’ensemble**, le rapport identifie également les appareils auxquels aucune stratégie de conformité n’est affectée :

![Voir les appareils auxquels aucune stratégie de conformité n’est affectée](./media/compliance-policy-monitor/devices-without-policies.png)

Quand vous sélectionnez la vignette, elle montre tous les appareils sans stratégie de conformité. Elle montre également l’utilisateur de l’appareil, l’état de déploiement de la stratégie et le modèle d’appareil.

#### <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Avec le paramètre de sécurité **Marquer les appareils sans stratégie de conformité comme étant**, il est important d’identifier les appareils sans stratégie de conformité. Vous pouvez ensuite leur affecter au moins une stratégie de conformité.

  Vous pouvez configurer le paramètre de sécurité dans le portail Intune. Sélectionnez **Conformité des appareils** > **Paramètres de stratégie de conformité**. Définissez ensuite **Marquer les appareils sans stratégie de conformité comme étant** sur **Conforme** ou sur **Non conforme**. 

  En savoir plus sur cette [amélioration de la sécurité du service Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Les utilisateurs auxquels une stratégie de conformité est affectée n’apparaissent pas dans le rapport, quelle que soit la plateforme de l’appareil. Par exemple, si vous avez affecté une stratégie de conformité Windows à un utilisateur qui a un appareil Android, celui-ci ne figure pas dans le rapport. Cependant, Intune considère que cet appareil Android n’est pas conforme. Pour éviter les problèmes, nous vous recommandons de créer des stratégies pour chaque plateforme d’appareil et de les déployer pour tous les utilisateurs.

### <a name="per-policy-device-compliance-report"></a>Rapport de conformité d’appareil par stratégie

Le rapport **Conformité des appareils** > **Conformité à la stratégie** vous montre les stratégies, et combien d’appareils sont conformes et non conformes. 

![Voir une liste des stratégies, et combien d’appareils sont conformes et non conformes pour ces stratégies](./media/compliance-policy-monitor/idc-8.png)

Quand vous sélectionnez une stratégie spécifique, vous pouvez voir **l’état de conformité**, **l’alias d’e-mail de l’utilisateur**, le **modèle d’appareil** et **l’emplacement** pour chaque appareil ciblé par cette stratégie de conformité.

## <a name="setting-compliance-report"></a>Rapport de conformité par paramètre

Le rapport **Conformité des appareils** > **Définition de la conformité** vous montre, par paramètre de conformité, le nombre total d’appareils dans chaque état de conformité. Il montre tous les paramètres de stratégie de conformité d’appareil de toutes les stratégies de conformité, les plateformes auxquelles les paramètres de stratégie sont appliqués et le nombre d’appareils non conformes.

![Voir une liste de tous les paramètres dans les différentes stratégies](./media/compliance-policy-monitor/idc-10.png)

Quand vous sélectionnez un paramètre spécifique, vous pouvez voir **l’état de conformité**, **l’alias d’e-mail de l’utilisateur**, le **modèle d’appareil** et **l’emplacement** pour chaque appareil ciblé par ce paramètre.

> [!NOTE]
> Les appareils Windows 10 qui sont joints à Azure AD peuvent afficher le compte système en tant qu'utilisateur non conforme. Ce comportement est normal et n’affecte pas la conformité globale des appareils. 

## <a name="view-status-of-device-policies"></a>Voir l’état des stratégies d’appareil

Vous pouvez vérifier les différents états de vos stratégies, par plateforme. Par exemple, vous avez une stratégie de conformité macOS. Vous souhaitez voir les appareils qui sont impactés par cette stratégie et savoir s’il existe des conflits ou des échecs.

Cette fonctionnalité est incluse dans le rapport d’état des appareils :

1. Sélectionnez **Conformité de l’appareil** > **Stratégies**. La liste des stratégies apparaît, dont la plateforme, si la stratégie est affectée.
2. Sélectionnez une stratégie, puis choisissez **Vue d’ensemble**. Dans cette vue, l’affectation de stratégie inclut les états suivants :

    - Réussite : la stratégie est appliquée
    - Erreur : impossible d’appliquer la stratégie. Ce message s’affiche généralement avec un code d’erreur qui établit un lien vers une explication. 
    - Conflit : deux paramètres sont appliqués au même appareil et Intune ne peut pas résoudre le conflit. Un administrateur doit examiner le problème.
    - En attente : l’appareil n’est pas encore enregistré dans Intune pour recevoir la stratégie. 
    - Non applicable : l’appareil ne peut pas recevoir la stratégie. Par exemple, la stratégie met à jour un paramètre spécifique à iOS 11.1, mais l’appareil utilise iOS 10. 

3. Pour voir les détails sur les appareils utilisant cette stratégie, sélectionnez un des états. Par exemple, sélectionnez **Réussi**. La fenêtre suivante montre les détails propres aux appareils, notamment leur nom et l’état du déploiement.

## <a name="how-intune-resolves-policy-conflicts"></a>Résolution des conflits de stratégie par Intune
Des conflits de stratégie peuvent se produire quand plusieurs stratégies Intune sont appliquées à un appareil. Si les paramètres de stratégie se chevauchent, Intune résout les conflits en appliquant les règles suivantes :

- Si les paramètres en conflit proviennent d’une stratégie de configuration Intune et d’une stratégie de conformité, les paramètres de la stratégie de conformité sont prioritaires sur ceux de la stratégie de configuration. Cela est valable même si les paramètres de la stratégie de configuration sont plus sécurisés.

- Si vous avez déployé plusieurs stratégies de conformité, Intune utilise la plus sécurisée d’entre elles.
