---
title: Créer des stratégies de conformité des appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Création de stratégies de conformité, vue d’ensemble des niveaux d’état et de gravité, utilisation de l’état InGracePeriod, utilisation de l’accès conditionnel, gestion des appareils sans stratégie attribuée et différences de conformité dans le portail Azure et dans le portail classique au sein de Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
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
ms.openlocfilehash: c8452f9b56032864380ec703bfd444dc85ef129b
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188259"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Créer une stratégie de conformité dans Microsoft Intune

Les stratégies de conformité des appareils sont une fonctionnalité clé quand vous utilisez Intune pour protéger les ressources de votre organisation. Dans Intune, vous pouvez créer des règles et des paramètres que les appareils doivent respecter pour être considérés comme conformes, par exemple une version de système d’exploitation minimale. Si l’appareil n’est pas conforme, vous pouvez bloquer l’accès aux données et aux ressources à l’aide de l’[accès conditionnel](conditional-access.md).

Vous pouvez également prendre des mesures en cas de non-conformité, par exemple l’envoi d’un e-mail de notification à l’utilisateur. Pour obtenir une vue d’ensemble de ce que les stratégies de conformité font, et comment elles sont utilisées, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

Cet article :

- Répertorie les conditions préalables et les étapes pour créer une stratégie de conformité.
- Vous montre comment attribuer la stratégie à vos groupes d’utilisateurs ou d’appareils.
- Décrit les fonctionnalités supplémentaires, notamment les balises d’étendue pour « filtrer » vos stratégies, et les étapes que vous pouvez effectuer sur les appareils non conformes.
- Répertorie les durées de cycle d’actualisation d’archivage lorsque des appareils reçoivent des mises à jour de stratégie.

## <a name="before-you-begin"></a>Avant de commencer

Pour utiliser des stratégies de conformité des appareils, veillez à respecter ceci :

- Utiliser les abonnements suivants :

  - Intune
  - Si vous utilisez l’accès conditionnel, vous avez besoin de l’édition Azure Active Directory (AD) Premium. [Tarification d’Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) répertorie ce que vous obtenez avec les différentes éditions. La conformité d’Intune ne nécessite pas Azure AD.

- Utiliser une plateforme prise en charge :

  - Administrateur d’appareil Android
  - Android Entreprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Inscrire des appareils dans Intune (nécessaire pour connaître l’état de conformité)

- Inscrivez les appareils auprès d’un seul utilisateur ou sans utilisateur principal. Les appareils inscrits auprès de plusieurs utilisateurs ne sont pas pris en charge.

## <a name="create-the-policy"></a>Créer la stratégie

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Stratégies de conformité** > **Créer une stratégie**.

3. Spécifiez les propriétés suivantes :

   - **Nom** : Attribuez un nom descriptif à la stratégie. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de stratégie approprié est **Marquer les appareils jailbreakés iOS comme non conformes**.

   - **Description** : Entrez une description de la stratégie. Ce paramètre est facultatif, mais recommandé.

   - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :
     - **Administrateur d’appareil Android**
     - **Android Entreprise**
     - **iOS/iPadOS**
     - **MacOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 et versions ultérieures**
     - **Windows 10 et versions ultérieures**

     Pour *Android Entreprise*, vous devez sélectionner un **type de profil** :
     - **Propriétaire de l’appareil**
     - **Profil professionnel**

   - **Paramètres** : Les articles suivants répertorient et décrivent les paramètres pour chaque plateforme :
     - [Administrateur d’appareil Android](compliance-policy-create-android.md)
     - [Android Entreprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [MacOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 et versions ultérieures](compliance-policy-create-windows-8-1.md)
     - [Windows 10 et versions ultérieures](compliance-policy-create-windows.md)  

   - **Emplacements** *(Administrateur d’appareil Android)*  : Dans votre stratégie, vous pouvez forcer la conformité selon l’emplacement de l’appareil. Choisissez parmi les emplacements existants. Vous n’avez pas encore d’emplacement ? L’article [Utiliser des emplacements (délimitation du réseau)](use-network-locations.md) dans Intune fournit des conseils.  

   - **Actions en cas de non-conformité** : Pour les appareils qui ne respectent pas vos stratégies de conformité, vous pouvez ajouter une séquence d’actions à appliquer automatiquement. Vous pouvez changer la planification quand l’appareil est marqué comme non conforme, par exemple après un jour. Vous pouvez également configurer une deuxième action qui envoie un e-mail à l’utilisateur quand l’appareil n’est pas conforme.

     L’article [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) fournit plus d’informations, notamment sur la création d’un e-mail de notification pour vos utilisateurs.

     Par exemple, vous utilisez la fonctionnalité Emplacements et ajoutez un emplacement à une stratégie de conformité. L’action par défaut en cas de non-conformité s’applique quand vous sélectionnez au moins un emplacement. Si l’appareil n’est pas connecté aux emplacements sélectionnés, il est immédiatement considéré comme non conforme. Vous pouvez accorder aux utilisateurs une période de grâce, par exemple un jour.

   - **Étendue (balises)**  : Les balises d’étendue permettent d’attribuer et de filtrer les stratégies à des groupes spécifiques, tels que les ventes, les ressources humaines, tous les employés US-NC, etc. Après avoir ajouté les paramètres, vous pouvez également ajouter une balise d’étendue à vos stratégies de conformité. La section [Utiliser des balises d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md) est une ressource utile.

4. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements. La stratégie est créée et apparaît dans la liste. Ensuite, attribuez la stratégie à vos groupes.

## <a name="assign-the-policy"></a>Affecter la stratégie

Une fois qu’une stratégie est créée, l’étape suivante consiste à attribuer la stratégie à vos groupes :

1. Choisissez une stratégie que vous avez créée. Les stratégies existantes se trouvent dans **Appareil** > **Stratégies de conformité** > **Stratégies**.

2. Sélectionnez les *Affectations de* > **stratégie**. Vous pouvez inclure ou exclure des groupes de sécurité Azure AD (Azure Active Directory).

3. Choisissez **Groupes sélectionnés** pour voir vos groupes de sécurité Azure AD. Sélectionnez les groupes auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Enregistrer** pour déployer la stratégie.

La conformité des utilisateurs ou des appareils ciblés par votre stratégie est évaluée lors de l’archivage avec Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Évaluer le nombre d’utilisateurs ciblés

Lorsque vous attribuez la stratégie, vous pouvez également **évaluer** le nombre d’utilisateurs affectés. Cette fonctionnalité calcule les utilisateurs ; elle ne calcule pas les appareils.

1. Dans Intune, sélectionnez **Appareils** > **Stratégies de conformité** > **Stratégies**.

2. Sélectionnez une *Évaluation* > **d’affectations** > **de stratégie**. Un message vous indique le nombre d’utilisateurs ciblés par cette stratégie.

Si le bouton **Évaluer** est grisé, vérifiez que la stratégie est attribuée à un ou plusieurs groupes.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Durées de cycle d’actualisation

Intune utilise différents cycles d’actualisation pour rechercher les mises à jour des stratégies de conformité. Si l’appareil vient d’être inscrit, la fréquence d’archivage est plus élevée. [Cycles d’actualisation de la stratégie et du profil](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) répertorie les temps d’actualisation estimés.

Les utilisateurs peuvent ouvrir l’application Portail d’entreprise et synchroniser l’appareil à tout moment pour rechercher immédiatement les mises à jour de stratégie.

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

Par exemple, trois stratégies de conformité sont attribuées à un appareil : un état Inconnu (gravité = 1), un état Conforme (gravité = 3) et un état InGracePeriod (gravité = 4). L’état InGracePeriod a le niveau de gravité le plus élevé. Par conséquent, les trois stratégies ont l’état de conformité InGracePeriod.

## <a name="next-steps"></a>Étapes suivantes

[Supervisez vos stratégies](compliance-policy-monitor.md).
