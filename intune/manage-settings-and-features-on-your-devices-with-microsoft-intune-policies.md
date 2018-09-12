---
title: Stratégies d’appareils, profils et questions-réponses avec Intune - Azure | Microsoft Docs
description: Découvrez les différentes stratégies et profils que vous pouvez utiliser dans Microsoft Intune, y compris les stratégies permettant de configurer des appareils, d’accéder aux ressources d’entreprise, d’activer l’accès conditionnel et d’inscrire des appareils d’entreprise. Vous pouvez également obtenir des réponses aux questions les plus fréquemment posées.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8a7a7405fe40d3568e736c244d9fcb308350709
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43318001"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Gérer des paramètres et des fonctionnalités sur vos appareils avec des stratégies Intune

Les *stratégies* Microsoft Intune sont des groupes de paramètres qui contrôlent les fonctionnalités des appareils mobiles et des ordinateurs. Créez des stratégies à l’aide de modèles qui incluent des paramètres recommandés ou personnalisés. Ensuite, déployez-les dans des groupes d’appareils ou d’utilisateurs.

## <a name="types-of-policies"></a>Types de stratégie

Les stratégies Intune appartiennent aux catégories suivantes : La catégorie que vous utilisez affecte la façon de créer et de déployer la stratégie.

- **Stratégies de configuration** : couramment utilisées pour gérer les paramètres de sécurité et les fonctionnalités sur vos appareils, y compris l’accès aux ressources d’entreprise. Consultez les [profils d’appareil Intune](device-profiles.md).
- **Stratégies de conformité d’appareil** : définissent les règles et les paramètres auxquels doit se conformer un appareil pour être considéré conforme par les stratégies d’accès conditionnel. Vous pouvez également utiliser des stratégies de conformité pour surveiller et corriger les problèmes de conformité des appareils indépendamment de l’accès conditionnel. Consultez les [stratégies de conformité des appareils](device-compliance-get-started.md).
- **Stratégies d’accès conditionnel** : permettent de sécuriser la messagerie et d’autres services en fonction des conditions que vous spécifiez. [Qu’est-ce que l’accès conditionnel ?](conditional-access.md) et [Quelles sont les utilisations courantes de l’accès conditionnel avec Intune ?](conditional-access-intune-common-ways-use.md) constituent de bonnes ressources pour démarrer.
- [Stratégies d’inscription des appareils d’entreprise](ios-enroll.md) : pour plus d’informations sur les stratégies d’inscription des appareils d’entreprise, consultez **Inscrire des appareils iOS dans Intune**.

## <a name="frequently-asked-questions-about-intune-policies"></a>Forum aux questions sur les stratégies Intune

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>Combien de temps faut-il pour que les appareils mobiles obtiennent une stratégie ou des applications une fois que celles-ci ont été déployées ?
Quand une stratégie ou une application est déployée, Intune commence immédiatement par indiquer à l’appareil de s’enregistrer auprès du service Intune. Cette étape prend généralement moins de 5 minutes.

Si un appareil ne se manifeste pas pour obtenir la stratégie après l’envoi de la première notification, Intune effectue trois autres tentatives.  Si l’appareil est hors connexion (par exemple, s’il est éteint ou n’est pas connecté à un réseau), il ne peut pas recevoir de notifications. Dans ce cas, l’appareil obtient la stratégie lors de son prochain enregistrement planifié auprès du service Intune de la manière suivante :

| Plate-forme | Fréquence d’enregistrement |
| --- | --- |
| iOS | Toutes les 6 heures | 
| Mac OS X | Toutes les 6 heures |
| Android | Toutes les 8 heures | 
| Windows Phone | Toutes les 8 heures | 
| Windows 8.1  | Toutes les 8 heures |  
| PC Windows 10 inscrits en tant qu’appareils | Toutes les 8 heures | 

Si l’appareil vient d’être inscrit, la fréquence d’enregistrement est plus élevée :

| Plate-forme | Fréquence |
| --- | --- |
| iOS | Toutes les 15 minutes pendant 6 heures, puis toutes les 6 heures |  
| Mac OS X | Toutes les 15 minutes pendant 6 heures, puis toutes les 6 heures | 
| Android | Toutes les 3 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures | 
| Windows Phone | Toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures | 
| Les PC Windows inscrits en tant qu’appareils | Toutes les 3 minutes pendant 30 minutes, puis toutes les 8 heures | 

Les utilisateurs peuvent également ouvrir l’application Portail d’entreprise et synchroniser l’appareil pour qu’il recherche immédiatement les stratégies à tout moment.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quelles sont les actions qui déclenchent l’envoi immédiat d’une notification par Intune ?
Les appareils s’enregistrent auprès d’Intune quand ils reçoivent une notification leur demandant de s’enregistrer ou lors de leur enregistrement planifié.  Quand vous ciblez un appareil ou un utilisateur avec une action de type réinitialisation, verrouillage, réinitialisation de code secret, déploiement d’application, déploiement de profil (Wi-Fi, VPN, messagerie) ou déploiement de stratégie, Intune tente immédiatement d’indiquer à l’appareil qu’il doit s’enregistrer auprès du service Intune.

D’autres modifications, comme la modification des coordonnées dans le portail d’entreprise, ne déclenchent pas l’envoi immédiat d’une notification aux appareils.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>Si plusieurs stratégies sont déployées sur le même utilisateur ou appareil, quels sont les paramètres appliqués ?
Quand plusieurs stratégies sont déployées pour le même utilisateur ou appareil, l’évaluation du paramètre à appliquer est effectuée au niveau de chaque paramètre :

- Les paramètres de stratégie de conformité ont toujours la priorité sur les paramètres de stratégie de configuration.

- En présence de deux stratégies de conformité, c’est le paramètre de la stratégie de conformité la plus restrictive qui est appliqué.

- Si un paramètre de stratégie de configuration est en conflit avec un paramètre d’une autre stratégie de configuration, ce conflit est signalé dans Intune. Corrigez ces conflits manuellement.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>Que se passe-t-il quand des stratégies de gestion des applications mobiles entrent en conflit ? Laquelle s’applique à l’application ?
Les valeurs en conflit sont les paramètres les plus restrictifs disponibles dans une stratégie GAM, à l’exception des champs d’entrée numérique (comme le nombre de tentatives autorisées avant la réinitialisation du code PIN).  Les champs d’entrée numérique sont définis sur les mêmes valeurs que quand vous créez une stratégie GAM dans la console en choisissant les paramètres recommandés.

Des conflits se produisent quand deux paramètres de stratégie sont identiques.  Par exemple, vous avez configuré deux stratégies MAM identiques, à l’exception du paramètre de copier/coller.  Dans ce scénario, le paramètre Copier/Coller est défini sur la valeur la plus restrictive, mais les autres paramètres sont appliqués selon leur configuration.

Si une stratégie est déployée sur l’application et active, puis qu’une deuxième stratégie est déployée, la première est prioritaire et reste appliquée. La deuxième stratégie est signalée comme étant conflictuelle. Si elles sont appliquées en même temps, ce qui signifie qu’aucune d’elles n’est prioritaire, elles sont toutes les deux en conflit. Tous les paramètres en conflit sont définis sur les valeurs les plus restrictives.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Que se passe-t-il quand les stratégies personnalisées iOS entrent en conflit ?
Intune n’évalue pas la charge utile des fichiers de configuration Apple ni la stratégie OMA-URI personnalisée. Son rôle se limite simplement au mécanisme de livraison.

Lorsque vous déployez une stratégie personnalisée, vérifiez que les paramètres configurés ne sont pas en conflit avec les stratégies de conformité, de configuration ou d’autres stratégies personnalisées. Si une stratégie personnalisée comprend des paramètres en conflit, l’ordre dans lequel les paramètres sont appliqués est aléatoire.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Que se passe-t-il quand une stratégie est supprimée ou qu’elle n’est plus applicable ?
Quand vous supprimez une stratégie ou retirez un appareil d’un groupe dans lequel une stratégie a été déployée, la stratégie et les paramètres sont supprimés de cet appareil conformément aux listes suivantes.

#### <a name="enrolled-devices"></a>Appareils inscrits

- Profils Wi-Fi, VPN, de certificat et de messagerie : ces profils sont supprimés de tous les appareils inscrits et pris en charge.
- Tous les autres types de stratégie :
  - **Appareils Windows et Android** : les paramètres ne sont pas supprimés de l’appareil.
  - **Appareils Windows Phone 8.1** : les paramètres suivants sont supprimés :
    - Exiger un mot de passe pour déverrouiller des appareils mobiles
    - Autoriser les mots de passe simples
    - Longueur minimale du mot de passe
    - Type de mot de passe requis
    - Expiration du mot de passe (jours)
    - Mémoriser l'historique des mots de passe
    - Nombre d'échecs de connexion répétée autorisé avant réinitialisation de l'appareil
    - Minutes d'inactivité avant demande du mot de passe
    - Type de mot de passe requis - Nombre minimum de jeux de caractères
    - Autoriser l'appareil photo
    - Exiger le chiffrement sur l'appareil mobile
    - Autoriser le stockage amovible
    - Autoriser le navigateur web
    - Autoriser la boutique d'applications
    - Autoriser la capture d'écran
    - Autoriser la géolocalisation
    - Autoriser le compte Microsoft
    - Autoriser la fonction copier-coller
    - Autoriser la connexion Wi-Fi
    - Autoriser la connexion automatique aux points d'accès Wi-Fi gratuits
    - Autoriser l'indication des points d'accès Wi-Fi
    - Autoriser la réinitialisation
    - Autoriser Bluetooth
    - Autoriser NFC
    - Autoriser le Wi-Fi

  - **iOS** : tous les paramètres sont supprimés, sauf :
    - Autoriser l'itinérance vocale
    - Autoriser l'itinérance des données
    - Autoriser la synchronisation automatique lors de l'itinérance

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Où puis-je trouver de l’aide concernant mes problèmes de stratégies ?

Consultez [Résoudre les problèmes liés aux stratégies](troubleshoot-policies-in-microsoft-intune.md).
