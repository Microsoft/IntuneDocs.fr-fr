---
title: Stratégies de conformité des appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Conditions d’utilisation de stratégies de conformité, vue d’ensemble des niveaux d’état et de gravité, utilisation de l’état InGracePeriod, utilisation de l’accès conditionnel, gestion des appareils sans stratégie attribuée et différences de conformité dans le portail Azure et dans le portail classique au sein de Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 806df8077045a4ad81cb7e221bd053059461a2fd
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199402"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Bien démarrer avec les stratégies de conformité des appareils dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

De nombreuses solutions de gestion des appareils mobiles vous permettent de protéger les données de l’organisation en obligeant les utilisateurs et les appareils à répondre à certaines exigences. Dans Intune, cette fonctionnalité est appelée « stratégies de conformité ». Les stratégies de conformité définissent les règles et les paramètres que les utilisateurs et les appareils doivent satisfaire pour être conformes. Quand elles sont associées à l’accès conditionnel, les administrateurs peuvent bloquer les utilisateurs et les appareils qui ne respectent pas les règles. Par exemple, un administrateur Intune peut exiger ceci :

- Les utilisateurs finaux utilisent un mot de passe pour accéder aux données de l’organisation sur des appareils mobiles.

- L’appareil n’est pas jailbreaké ni rooté.

- Une version de système d’exploitation minimale ou maximale est installée sur l’appareil.

- L’appareil se situe à un certain niveau de menace ou en dessous.

Vous pouvez également utiliser des stratégies de conformité des appareils pour superviser l’état de conformité sur vos appareils.

> [!IMPORTANT]
> Intune suit la planification des enregistrements de l’appareil pour toutes les évaluations de conformité sur l’appareil. [Découvrez-en plus sur la planification des enregistrements d’appareils](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>Prérequis

Pour utiliser des stratégies de conformité des appareils, veillez à respecter ceci :

- Utiliser les abonnements suivants :

  - Intune
  - Azure Active Directory (AD) Premium

- Utiliser une plateforme prise en charge :

  - Android
  - iOS
  - macOS (préversion)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- Inscrivez les appareils dans Intune pour en connaître l’état de conformité.

- Inscrivez les appareils auprès d’un seul utilisateur ou sans utilisateur principal. Les appareils inscrits auprès de plusieurs utilisateurs ne sont pas pris en charge.

## <a name="how-device-compliance-policies-work-with-azure-ad"></a>Fonctionnement des stratégies de conformité des appareils avec Azure AD

Quand un appareil est inscrit dans Intune, le processus d’inscription Azure AD démarre, puis met à jour les attributs de l’appareil dans Azure AD. Une information clé est l’état de conformité de l’appareil. Cet état de conformité est utilisé par les stratégies d’accès conditionnel pour bloquer ou autoriser l’accès à l’e-mail et à d’autres ressources de l’entreprise.

Le [processus d’inscription AD Azure](https://docs.microsoft.com/azure/active-directory/device-management-introduction) fournit plus d’informations.

## <a name="refresh-cycle-times"></a>Durées de cycle d’actualisation

Lors de la vérification de la conformité, Intune utilise le même cycle d’actualisation que les profils de configuration. En règle générale, ces durées sont les suivantes :

- iOS : toutes les six heures
- macOS : toutes les six heures
- Android : toutes les huit heures
- PC Windows 10 inscrits en tant qu’appareils : toutes les huit heures
- Windows Phone : toutes les huit heures
- Windows 8.1 : toutes les huit heures

Les vérifications de conformité se produisent plus fréquemment juste après l’inscription d’un appareil.

### <a name="assign-an-ingraceperiod-status"></a>Attribuer un état InGracePeriod

L’état InGracePeriod pour une stratégie de conformité est une valeur. Cette valeur est déterminée par la combinaison de la période de grâce d’un appareil et de l’état réel de l’appareil pour cette stratégie de conformité.

Plus précisément, si un appareil a un état NonCompliant pour une stratégie de conformité affectée et si :

- L’appareil n’a pas de période de grâce affectée, la valeur affectée pour la stratégie de conformité est NonCompliant
- L’appareil a une période de grâce qui a expiré, la valeur affectée pour la stratégie de conformité est NonCompliant
- L’appareil a une période de grâce qui se situe dans le futur, la valeur affectée pour la stratégie de conformité est InGracePeriod

Le tableau suivant récapitule ces points :

|État de conformité réel|Valeur de la période de grâce affectée|État de conformité effectif|
|---------|---------|---------|
|NonCompliant |Aucune période de grâce affectée |NonCompliant |
|NonCompliant |Date d’hier|NonCompliant|
|NonCompliant |Date de demain|InGracePeriod|

Pour plus d’informations sur la surveillance des stratégies de conformité des appareils, consultez [Surveiller les stratégies de conformité d’appareils Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Attribuer un état de stratégie de conformité résultant

Si un appareil a plusieurs stratégies de conformité et qu’il a des états de conformité différents pour au moins deux stratégies de conformité attribuées, un seul état de conformité résultant est attribué. Cette affectation est basée sur un niveau de gravité conceptuel affecté à chaque état de conformité. Chaque état de conformité a le niveau de gravité suivant :

|État  |Gravité  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|Conforme|3|
|InGracePeriod|4|
|NonCompliant|5|
|Erreur|6|

Quand un appareil a plusieurs stratégies de conformité, le niveau de gravité le plus élevé de toutes les stratégies lui est attribué.

Par exemple, un appareil a trois stratégies de conformité qui lui sont affectées : un état Inconnu (gravité = 1), un état Conforme (gravité = 3) et un état InGracePeriod (gravité = 4). L’état InGracePeriod ayant le niveau de gravité le plus élevé, les trois stratégies ont l’état de conformité InGracePeriod.

## <a name="ways-to-use-device-compliance-policies"></a>Utilisations des stratégies de conformité des appareils

#### <a name="with-conditional-access"></a>Avec accès conditionnel
Si un appareil est conforme aux règles de stratégie, vous pouvez lui accorder l’accès à l’e-mail et aux autres ressources d’entreprise. Sinon, cet accès leur est refusé. Il s’agit d’un accès conditionnel.

#### <a name="without-conditional-access"></a>Sans accès conditionnel
Vous pouvez également utiliser des stratégies de conformité d’appareils sans accès conditionnel. Quand vous utilisez des stratégies de conformité indépendamment, les appareils ciblés sont évalués et signalés avec leur état de conformité. Par exemple, vous pouvez obtenir un rapport sur le nombre d’appareils qui ne sont pas chiffrés, ou sur les appareils jailbreakés ou rootés. Quand vous utilisez des stratégies de conformité sans accès conditionnel, il n’y a aucune restriction d’accès aux ressources de l’organisation.

## <a name="ways-to-deploy-device-compliance-policies"></a>Déploiement des stratégies de conformité des appareils
Vous pouvez déployer une stratégie de conformité pour des utilisateurs dans des groupes d’utilisateurs ou sur des appareils dans des groupes d’appareils. Quand une stratégie de conformité est déployée sur un utilisateur, la conformité de tous ses appareils est vérifiée. Sur les appareils Windows 10 version 1803 et les appareils plus récents, il est recommandé de déployer sur des groupes d’appareils *si* l’utilisateur principal n’a pas inscrit l’appareil. L’utilisation de groupes d’appareils dans ce scénario permet la création de rapports de conformité.

Un ensemble de paramètres de stratégie de conformité intégrés (**Intune** > **Conformité de l’appareil**) est évalué sur tous les appareils inscrits auprès d’Intune. Par exemple :

- **Marquer les appareils sans stratégie de conformité comme étant** : Cette propriété a deux valeurs :

  - **Conforme** : fonctionnalité de sécurité désactivée
  - **Non conforme** (par défaut) : fonctionnalité de sécurité activée

  Si un appareil n’a pas de stratégie de conformité attribuée, il est considéré comme non conforme. Par défaut, les appareils sont marqués comme **non conformes**. Si vous utilisez l’accès conditionnel, nous vous recommandons de modifier le paramètre en **Non conforme**. Si un utilisateur final n’est pas conforme en raison du défaut d’attribution d’une stratégie, le portail d’entreprise indique `No compliance policies have been assigned`.

- **Détection de jailbreak améliorée** : Quand ce paramètre est activé, les appareils iOS sont enregistrés dans Intune plus fréquemment. L’activation de cette propriété utilise les services de localisation de l’appareil et a un impact sur l’utilisation de la batterie. Les données d’emplacement utilisateur ne sont pas stockées par Intune.

  L’activation de ce paramètre nécessite que les appareils :
  - Activent les services de localisation au niveau du système d’exploitation
  - Autorisent le portail d’entreprise à utiliser les services de localisation
  - Évaluent et signalent leur état jailbreak à Intune au moins une fois toutes les 72 heures. Sinon, l’appareil est marqué comme non conforme. L’évaluation est déclenchée soit par l’ouverture de l’application Portail d’entreprise, soit par le déplacement physique de l’appareil d’au moins 500 mètres. Si l’appareil ne se déplace pas de 500 mètres dans les 72 heures, l’utilisateur doit ouvrir l’application Portail d’entreprise pour une évaluation de jailbreak améliorée.

- **Période de validité de l’état de conformité (jours)**  : Entrez la période pendant laquelle les appareils signalent l’état de toutes les stratégies de conformité reçues. Les appareils qui ne retournent pas l’état au cours de cette période sont considérés comme non conformes. La valeur par défaut est de 30 jours.

Tous les appareils ont une **Stratégie de conformité d’appareil intégrée** (portail Azure > Conformité de l’appareil > Conformité à la stratégie). Utilisez cette stratégie intégrée pour superviser ces paramètres.

Pour savoir le temps qu’il faut pour que les appareils mobiles reçoivent une stratégie une fois celle-ci déployée, consultez [Résoudre les problèmes de profils d’appareil](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Les rapports de conformité sont un excellent moyen de vérifier l’état des appareils. Consultez [Surveiller les stratégies de conformité](compliance-policy-monitor.md) pour obtenir des conseils.

### <a name="actions-for-noncompliance"></a>Actions en cas de non-conformité
Vous pouvez configurer une séquence chronologique d’actions qui s’appliquent aux appareils qui ne répondent pas aux critères de la stratégie de conformité. Ces actions en cas de non-conformité peuvent être automatisées, comme décrit dans [Automatiser des actions en cas de non-conformité](actions-for-noncompliance.md).

## <a name="azure-classic-portal-vs-azure-portal"></a>Portail Azure Classic et Portail Azure

Principale différence au moment de l’utilisation de stratégies de conformité dans le portail Azure :

- Dans le portail Azure, les stratégies de conformité sont créées séparément pour chaque plateforme prise en charge
- Dans le portail Azure Classic, une stratégie de conformité des appareils est commune à toutes les plateformes prises en charge

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>Stratégies de conformité des appareils dans le portail classique et dans le portail Azure

Les stratégies de conformité des appareils créées dans le [portail classique](https://manage.microsoft.com) n’apparaissent pas dans le [portail Azure](https://portal.azure.com). Toutefois, elles continuent de cibler des utilisateurs et peuvent être gérées à l’aide du portail classique.

Pour utiliser les fonctionnalités liées à la conformité des appareils dans le portail Azure, vous devez créer des stratégies de conformité d’appareil dans le portail Azure. Si, dans le portail Azure, vous affectez une stratégie de conformité des appareils à un utilisateur auquel est déjà associée une stratégie de ce type dans le portail classique, les stratégies du portail Azure sont prioritaires par rapport aux stratégies qui sont créées dans le portail classique.

## <a name="next-steps"></a>Étapes suivantes

- Créez une stratégie de conformité des appareils pour les plateformes suivantes :

  - [Android](compliance-policy-create-android.md)
  - [Profil professionnel Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [MacOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Pour plus d’informations sur les entités de la stratégie Intune Data Warehouse, consultez [Informations de référence sur les entités de stratégie](reports-ref-policy.md).
