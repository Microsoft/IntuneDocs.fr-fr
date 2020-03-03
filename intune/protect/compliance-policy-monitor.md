---
title: Surveiller les stratégies de conformité des appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez le tableau de bord de conformité des appareils pour analyser la conformité globale des appareils, afficher des rapports et afficher la conformité des appareils par stratégie et par paramètre.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 128f615a9551c31e6b0e0de4f1d269083874bf48
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515116"
---
# <a name="monitor-intune-device-compliance-policies"></a>Surveiller les stratégies de conformité d’appareils Intune

Les rapports de conformité vous permettent d’examiner la conformité des appareils et de résoudre les problèmes liés à la conformité dans votre organisation. Avec ces rapports, vous pouvez voir des informations sur :

- Les états de conformité globale des appareils
- L’état de conformité pour un paramètre spécifique
- L’état de conformité pour une stratégie spécifique
- Explorer des appareils spécifiques pour voir des paramètres et des stratégies spécifiques qui affectent l’appareil

## <a name="open-the-compliance-dashboard"></a>Ouvrir le tableau de bord de conformité

Ouvrez le **Tableau de bord de conformité des appareils Intune** :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez l’onglet**Appareils** > **Vue d’ensemble** > **État de conformité**.

> [!IMPORTANT]
> Les appareils doivent être inscrits dans Intune pour recevoir des stratégies de conformité d’appareils.

## <a name="dashboard-overview"></a>Vue d’ensemble du tableau de bord

Quand le tableau de bord s’ouvre, vous obtenez une vue d’ensemble avec tous les rapports de conformité. Dans ces rapports, vous pouvez voir et vérifier les éléments suivants :

- Conformité globale des appareils
- Conformité des appareils par stratégie
- Conformité des appareils par paramètre
- État de l’agent de menace
- État de la protection d’appareil

![Image du tableau de bord montrant le tableau de bord de conformité des appareils et les différents rapports](./media/compliance-policy-monitor/idc-1.png)

En explorant ce rapport, vous pouvez également voir toutes les stratégies et paramètres de conformité spécifiques qui s’appliquent à un appareil individuel, avec l’état de conformité pour chaque paramètre.

### <a name="device-compliance-status"></a>État de conformité de l’appareil

Le graphique **État de conformité de l’appareil** montre l’état de conformité de tous les appareils inscrits auprès d’Intune. Les états de conformité des appareils sont conservés dans deux bases de données : Intune et Azure Active Directory.

> [!IMPORTANT]
> Intune suit la planification des enregistrements de l’appareil pour toutes les évaluations de conformité sur l’appareil. [Découvrez-en plus sur la planification des enregistrements d’appareils](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Descriptions des différents états des stratégies de conformité des appareils :

- **Conforme** : l’appareil a correctement appliqué un ou plusieurs paramètres de stratégie de conformité d’appareil.

- **Période de grâce** : l’appareil est ciblé par un ou plusieurs paramètres de stratégie de conformité d’appareil. L’utilisateur n’a cependant pas encore appliqué les stratégies. Cela signifie que l’appareil n’est pas conforme, mais qu’il est dans la période de grâce définie par l’administrateur.

  - Découvrez plus d’informations sur les [Actions destinées aux appareils non conformes](actions-for-noncompliance.md).

- **Non évalué** : état initial des nouveaux appareils inscrits. Les autres raisons possibles sont les suivantes :

  - Il peut aussi s’agir d’appareils auxquels aucune stratégie de conformité n’a été affectée et qui n’ont pas de déclencheur pour vérifier leur conformité
  - Les appareils non enregistrés depuis la dernière mise à jour de la stratégie de conformité
  - Les appareils non associés à un utilisateur spécifique, tels que :
    - les appareils iOS/iPadOS achetés dans le cadre du Programme d’inscription des appareils (DEP) d’Apple
    - les appareils dédiés Android en mode kiosque ou Android Entreprise
  - Les appareils inscrits avec un compte de gestionnaire d’inscription des appareils

- **Non conforme** : l’appareil n’a pas pu appliquer un ou plusieurs paramètres de stratégie de conformité d’appareil. L’autre possibilité est que l’utilisateur ne s’est pas conformé aux stratégies.

- **Appareil non synchronisé** : l’appareil n’a pas pu signaler l’état de sa stratégie de conformité d’appareil pour l’une des raisons suivantes :

  - **Inconnu** : l’appareil est hors connexion ou n’a pas pu communiquer avec Intune ou Azure AD pour d’autres raisons.

  - **Erreur** : l’appareil n’a pas pu communiquer avec Intune et Azure AD, et a reçu un message d’erreur avec la raison.

> [!IMPORTANT]
> Les appareils inscrits dans Intune, mais non ciblés par des stratégies de conformité des appareils, sont inclus dans ce rapport sous le compartiment **Conforme**.

#### <a name="drill-down-for-more-details"></a>Explorer pour voir plus de détails

Dans le graphique **État de conformité des appareils**, sélectionnez un état. Par exemple, sélectionnez l’état **Non conforme** :

![Choisir l’état Non conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

Cette action a pour effet d’ouvrir la fenêtre **Conformité de l’appareil** et d’afficher les appareils dans un graphique **État de l’appareil**. Le graphique donne plus de détails sur les appareils qui se trouvent dans cet état, notamment la plateforme du système d’exploitation et la dernière date d’enregistrement.
![Image du tableau de bord montrant plus d’informations sur l’appareil dans cet état spécifique](./media/compliance-policy-monitor/drill-down-details.png)

Si vous voulez voir tous les appareils appartenant à un utilisateur spécifique, vous pouvez aussi filtrer le rapport graphique en tapant l’e-mail de l’utilisateur.

#### <a name="filter-and-columns"></a>Filtrer et Colonnes

![Sélectionnez Filtrer et Colonne pour changer les résultats apparaissant dans le graphique](./media/compliance-policy-monitor/filter-columns.png)

Quand vous sélectionnez le bouton **Filtrer**, le menu déroulant du filtre s’ouvre avec plus d’options, notamment l’état de **Conformité** et les appareils **Jailbreakés**. **Appliquez** le filtre pour mettre à jour les résultats.

Utilisez la propriété **Colonnes** pour ajouter ou supprimer des colonnes dans la sortie graphique. Par exemple, **Nom principal de l’utilisateur** peut faire apparaître l’adresse e-mail inscrite sur l’appareil. **Appliquez** les colonnes pour mettre à jour les résultats.

#### <a name="device-details"></a>Détails sur l'appareil

Dans le graphique **Détails des appareils**, sélectionnez un appareil en particulier, puis **Conformité de l’appareil** :

![Choisir un appareil spécifique, puis Conformité de l’appareil pour voir les stratégies de conformité appliquées](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Intune affiche plus de détails sur les paramètres de stratégie de conformité appliqués sur cet appareil. Quand vous sélectionnez la stratégie spécifique, tous les paramètres de la stratégie apparaissent.

### <a name="devices-without-compliance"></a>Appareils sans conformité

Sur la page *État de conformité*, à côté du graphique *Conformité à la stratégie*, vous pouvez sélectionner la vignette **Appareils sans stratégie de conformité** pour afficher des informations sur les appareils auxquels aucune stratégie de conformité n’a été affectée :

![Voir les appareils auxquels aucune stratégie de conformité n’est affectée](./media/compliance-policy-monitor/devices-without-policies.png)

Quand vous sélectionnez la vignette, elle montre tous les appareils sans stratégie de conformité. Elle montre également l’utilisateur de l’appareil, l’état de déploiement de la stratégie et le modèle d’appareil.

#### <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- Avec le paramètre de sécurité **Marquer les appareils sans stratégie de conformité comme étant**, il est important d’identifier les appareils sans stratégie de conformité. Vous pouvez ensuite leur affecter au moins une stratégie de conformité.

  Vous pouvez configurer le paramètre de sécurité dans le portail Intune. Accédez à **Appareils** > **Stratégies de conformité** > **Paramètres de stratégie de conformité**. Définissez ensuite **Marquer les appareils sans stratégie de conformité comme étant** sur **Conforme** ou sur **Non conforme**.

  En savoir plus sur cette [amélioration de la sécurité du service Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Les utilisateurs auxquels une stratégie de conformité est affectée n’apparaissent pas dans le rapport, quelle que soit la plateforme de l’appareil. Par exemple, si vous avez affecté une stratégie de conformité Windows à un utilisateur qui a un appareil Android, celui-ci ne figure pas dans le rapport. Cependant, Intune considère que cet appareil Android n’est pas conforme. Pour éviter les problèmes, nous vous recommandons de créer des stratégies pour chaque plateforme d’appareil et de les déployer pour tous les utilisateurs.

### <a name="per-policy-device-compliance"></a>Conformité des appareils par stratégie

Le graphique **Conformité à la stratégie** montre les stratégies et le nombre d’appareils conformes et non conformes.

![Voir une liste des stratégies, et combien d’appareils sont conformes et non conformes pour ces stratégies](./media/compliance-policy-monitor/idc-8.png)

### <a name="setting-compliance"></a>Configuration de la conformité

Le graphique **Conformité des paramètres** montre tous les paramètres de stratégie de conformité d’appareil de toutes les stratégies de conformité, les plateformes auxquelles les paramètres de stratégie sont appliqués et le nombre d’appareils non conformes.

![Voir une liste de tous les paramètres dans les différentes stratégies](./media/compliance-policy-monitor/idc-10.png)

## <a name="view-compliance-reports"></a>Afficher les rapports de conformité

En plus d’utiliser les graphiques sur *État de conformité*, vous pouvez accéder à **Rapports** > **Conformité des appareils**.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Surveiller**, puis sous **Conformité**, sélectionnez le rapport que vous souhaitez afficher. Voici quelques-uns des rapports de conformité disponibles :

   - Conformité de l’appareil
   - Appareils non conformes
   - Appareils sans stratégie de conformité
   - Configuration de la conformité
   - Conformité aux stratégies
   - Rapport d’attestation de l’intégrité Windows
   - État de l’agent de menace

Pour plus d’informations sur les rapports, consultez [Rapports Intune](../fundamentals/reports.md)

## <a name="view-status-of-device-policies"></a>Voir l’état des stratégies d’appareil

Vous pouvez vérifier les différents états de vos stratégies, par plateforme. Par exemple, vous avez une stratégie de conformité macOS. Vous souhaitez voir les appareils qui sont impactés par cette stratégie et savoir s’il existe des conflits ou des échecs.

Cette fonctionnalité est incluse dans le rapport d’état des appareils :

1. Sélectionnez **Appareils** > **Stratégies de conformité** > **Stratégies**. La liste des stratégies apparaît, dont la plateforme, si la stratégie est affectée.
2. Sélectionnez une stratégie, puis choisissez **Vue d’ensemble**. Dans cette vue, l’affectation de stratégie inclut les états suivants :

    - **Réussite** : la stratégie est appliquée
    - **Erreur** : impossible d’appliquer la stratégie. Ce message s’affiche généralement avec un code d’erreur qui établit un lien vers une explication.
    - **Conflit** : deux paramètres sont appliqués au même appareil et Intune ne peut pas résoudre le conflit. Un administrateur doit examiner le problème.
    - **En attente** : l’appareil n’est pas encore enregistré dans Intune pour recevoir la stratégie.
    - **Non applicable** : l’appareil ne peut pas recevoir la stratégie. Par exemple, la stratégie met à jour un paramètre spécifique à iOS 11.1, mais l’appareil utilise iOS 10.

3. Pour voir les détails sur les appareils utilisant cette stratégie, sélectionnez un des états. Par exemple, sélectionnez **Réussi**. La fenêtre suivante montre les détails propres aux appareils, notamment leur nom et l’état du déploiement.

## <a name="how-intune-resolves-policy-conflicts"></a>Résolution des conflits de stratégie par Intune

Des conflits de stratégie peuvent se produire quand plusieurs stratégies Intune sont appliquées à un appareil. Si les paramètres de stratégie se chevauchent, Intune résout les conflits en appliquant les règles suivantes :

- Si les paramètres en conflit proviennent d’une stratégie de configuration Intune et d’une stratégie de conformité, les paramètres de la stratégie de conformité sont prioritaires sur ceux de la stratégie de configuration. Cela est valable même si les paramètres de la stratégie de configuration sont plus sécurisés.

- Si vous avez déployé plusieurs stratégies de conformité, Intune utilise la plus sécurisée d’entre elles.

## <a name="next-steps"></a>Étapes suivantes

[Vue d’ensemble des stratégies de conformité](device-compliance-get-started.md)
