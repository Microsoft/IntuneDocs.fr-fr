---
title: "Stratégies de conformité des appareils de Microsoft Intune"
titleSuffix: 
description: "Découvrez plus d’informations sur la conformité des appareils dans Microsoft Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb3ec168844708d80c83909ab6c58a52ca62e53c
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="get-started-with-microsoft-intune-device-compliance-policies"></a>Bien démarrer avec les stratégies de conformité des appareils Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Les stratégies de conformité des appareils Intune définissent les règles et les paramètres auxquels doit se conformer un appareil pour être considéré comme conforme par Intune.

Ces règles sont les suivantes :

- Utiliser un mot de passe pour accéder aux appareils

- Chiffrement

- Si l’appareil est jailbroken ou rooté

- Version minimale du système d’exploitation requise

- Version maximale autorisée du système d’exploitation

- Exiger que l’appareil soit au niveau ou sous le niveau de défense contre les menaces mobiles

Vous pouvez également utiliser des stratégies de conformité des appareils pour surveiller l’état de conformité dans vos appareils.

## <a name="device-compliance-requirements"></a>Exigences de conformité des appareils

Les exigences de conformité sont, pour simplifier, des règles comme l’exigence d’un code PIN ou d’un chiffrement que vous pouvez spécifier comme requises ou non requises pour une stratégie de conformité.

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

##  <a name="pre-requisites"></a>Prérequis

Vous devez souscrire aux abonnements suivants pour utiliser des stratégies de conformité des appareils avec Intune :

- Intune

- Azure AD Premium

###  <a name="supported-platforms"></a>Plateformes prises en charge :

-   Android

-   iOS

-   macOS (préversion)

-   Windows 8.1

-   Windows Phone 8.1

-   Windows 10

> [!IMPORTANT]
> Les appareils doivent être inscrits dans Intune pour signaler leur état de conformité.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Fonctionnement des stratégies de conformité des appareils Intune avec Azure AD

Quand un appareil est inscrit dans Intune, le processus d’inscription Azure AD ajoute des informations aux attributs de l’appareil dans Azure AD. Une information clé de l’appareil est son état de conformité, qui est utilisé par les stratégies d’accès conditionnel pour bloquer ou autoriser l’accès à la messagerie et à d’autres ressources de l’entreprise.

- Découvrez plus en détail le [processus d’inscription Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction).

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>Affectation d’un état de profil de configuration d’appareil résultant

Si un appareil a plusieurs profils de configuration qui lui sont affectés et qu’il a des états de conformité différents pour au moins deux profils de configuration affectés, alors un seul état de conformité résultant doit être affecté. Cette affectation est basée sur un niveau de gravité conceptuel affecté à chaque état de conformité. Chaque état de conformité a le niveau de gravité suivant :


|État  |Gravité  |
|---------|---------|
|Pending     |1|
|Réussi     |2|
|Failed     |3|
|Erreur     |4|

Un état résultant d’au moins deux profils de configuration est alors affecté en sélectionnant le niveau de gravité le plus élevé de tous les profils affectés à un appareil.

Par exemple, un appareil comporte trois profils qui lui sont affectés : un état En attente (gravité = 1), un état Réussi (gravité = 2) et un état Erreur (gravité = 4). L’état Erreur a le niveau de gravité le plus élevé, donc il est affecté comme état de conformité résultant pour les trois profils.

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>Affectation d’un état InGracePeriod pour une stratégie de conformité affectée

L’état InGracePeriod d’une stratégie de conformité est une valeur déterminée en tenant compte de la combinaison de la période de grâce d’un appareil et l’état réel de l’appareil pour la stratégie de conformité affectée. 

Plus précisément, si un appareil a un état NonCompliant pour une stratégie de conformité affectée et si :

- l’appareil n’a pas de période de grâce affectée, alors la valeur affectée pour la stratégie de conformité est NonCompliant.
- l’appareil a une période de grâce qui a expiré, alors la valeur affectée pour la stratégie de conformité est NonCompliant.
- l’appareil a une période de grâce qui se situe dans le futur, alors la valeur affectée pour la stratégie de conformité est InGracePeriod.

Le tableau suivant récapitule les points précédents :


|État de conformité réel|Valeur de la période de grâce affectée|État de conformité effectif|
|---------|---------|---------|
|NonCompliant |Aucune période de grâce affectée |NonCompliant |
|NonCompliant |Date d’hier|NonCompliant|
|NonCompliant |Date de demain|InGracePeriod|

Pour plus d’informations sur la surveillance des stratégies de conformité des appareils, consultez [Surveiller les stratégies de conformité d’appareils Intune](compliance-policy-monitor.md).

### <a name="assigning-a-resulting-compliance-policy-status"></a>Affectation d’un état de stratégie de conformité résultant

Si un appareil a plusieurs stratégies de conformité qui lui sont affectées et qu’il a des états de conformité différents pour au moins deux stratégies de conformité affectées, alors un seul état de conformité résultant doit être affecté. Cette affectation est basée sur un niveau de gravité conceptuel affecté à chaque état de conformité. Chaque état de conformité a le niveau de gravité suivant : 

|État  |Gravité  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|Conforme|3|
|InGracePeriod|4|
|NonCompliant|5|
|Erreur|6|

Un état résultant d’au moins deux stratégies de conformité est alors déterminé en sélectionnant le niveau de gravité le plus élevé de toutes les stratégies affectées à un appareil.
 
Par exemple, un appareil comporte trois stratégies de conformité qui lui sont affectées : un état Inconnu (gravité = 1), un état Conforme (gravité = 3) et un état InGracePeriod (gravité = 4). L’état InGracePeriod a le niveau de gravité le plus élevé, donc il est affecté comme état de conformité résultant pour les trois stratégies.  

##  <a name="ways-to-use-device-compliance-policies"></a>Utilisations des stratégies de conformité des appareils

### <a name="with-conditional-access"></a>Avec accès conditionnel
Vous pouvez utiliser une stratégie de conformité avec accès conditionnel pour permettre uniquement aux appareils conformes à une ou plusieurs règles de conformité des appareils d’accéder aux e-mails et à d’autres ressources de l’entreprise.

### <a name="without-conditional-access"></a>Sans accès conditionnel
Vous pouvez également utiliser des stratégies de conformité d’appareils indépendamment de l’accès conditionnel. Quand vous utilisez des stratégies de conformité indépendamment, les appareils ciblés sont évalués et signalés avec leur état de conformité. Par exemple, vous pouvez obtenir un rapport sur le nombre d’appareils qui ne sont pas chiffrés, ou les appareils qui sont jailbreakés ou rootés. Mais quand vous utilisez des stratégies de conformité indépendamment, aucune restriction d’accès aux ressources de l’entreprise n’est appliquée.

Vous déployez les stratégies de conformité sur les utilisateurs. Quand une stratégie de conformité est déployée sur un utilisateur, la conformité de ses appareils est vérifiée. Pour en savoir plus sur le temps nécessaire pour que les appareils mobiles reçoivent une stratégie une fois celle-ci déployée, consultez [Résoudre les problèmes de profils d’appareil dans Microsoft Intune](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

#### <a name="actions-for-non-compliance"></a>Actions en cas de non-conformité

Les actions en cas de non-conformité vous permettent de configurer une séquence chronologique d’actions appliquées aux appareils qui ne répondent pas aux critères de la stratégie de conformité. Pour plus d’informations, consultez [Automatiser des actions en cas de non-conformité](actions-for-noncompliance.md).

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Utilisation des stratégies de conformité des appareils dans le portail classique Intune et dans le Portail Azure

Passez en revue les principales différences pour faciliter la transition vers le nouveau flux de travail de la stratégie de conformité des appareils dans le portail Azure.

- Dans le portail Azure, les stratégies de conformité sont créées séparément pour chaque plateforme prise en charge.
- Dans le portail classique Intune, une stratégie de conformité des appareils était commune à toutes les plateformes prises en charge.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Migrer les stratégies de conformité des appareils du portail classique Intune vers le portail Azure

Les stratégies de conformité des appareils créées dans le [portail classique Intune](https://manage.microsoft.com) n’apparaissent pas dans le nouveau [portail Intune Azure](https://portal.azure.com). Toutefois, elles continuent de cibler des utilisateurs et peuvent être gérées par le biais du portail classique Intune.

Si vous souhaitez tirer parti des nouvelles fonctionnalités liées à la conformité des appareils dans le portail Azure, vous devez créer des stratégies de conformité d’appareil dans le portail Azure lui-même. Si, dans le portail Azure, vous affectez une nouvelle stratégie de conformité des appareils à un utilisateur déjà associé à une stratégie de ce type dans le portail Intune classique, les stratégies du portail Intune Azure sont prioritaires par rapport à celles qui sont créées à partir du portail classique Intune.

##  <a name="next-steps"></a>Étapes suivantes

- Créez une stratégie de conformité des appareils pour les plateformes suivantes :

   - [Android](compliance-policy-create-android.md)
   - [Android for Work](compliance-policy-create-android-for-work.md)
   - [iOS](compliance-policy-create-ios.md)
   - [MacOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- Pour plus d’informations sur les entités de la stratégie Intune Data Warehouse, consultez [Informations de référence sur les entités de stratégie](reports-ref-policy.md).
