---
title: Gérer les versions de système d’exploitation avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Découvrez comment gérer les versions de système d’exploitation sur plusieurs plateformes avec Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6afd4b0bb45db580f3be47680675bd268681a11
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506370"
---
# <a name="manage-operating-system-versions-with-intune"></a>Gérer les versions de système d’exploitation avec Intune
Sur les plateformes mobiles et de bureau modernes, le rythme de publication des mises à jour importantes, des correctifs et des nouvelles versions est soutenu. Vous disposez d’outils pour gérer entièrement les mises à jour et les correctifs sur Windows, mais d’autres plateformes telles qu’iOS et Android exigent la participation de vos utilisateurs finaux.  Microsoft Intune offre des fonctionnalités qui vous permettent de structurer la gestion des versions de vos systèmes d’exploitation sur différentes plateformes.

Intune peut ainsi vous aider à gérer ces scénarios courants : 
- Déterminer les versions de système d’exploitation présentes sur les appareils des utilisateurs finaux
- Contrôler l’accès aux données organisationnelles sur les appareils pendant que vous validez une nouvelle version de système d’exploitation
- Encourager/exiger la mise à niveau du système d’exploitation des utilisateurs finaux avec la dernière version approuvée par votre organisation
- Gérer le lancement d’une nouvelle version de système d’exploitation à l’échelle de l’organisation
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Gestion des versions de système d’exploitation avec des restrictions d’inscription à la gestion des appareils mobiles (MDM) Intune
Les restrictions d’inscription à MDM Intune vous permettent de définir les conditions que doit remplir un appareil client avant d’autoriser son inscription. L’objectif est de faire en sorte que les utilisateurs finaux n’inscrivent que des appareils conformes avant de pouvoir accéder aux ressources de l’organisation. Les appareils doivent notamment respecter les versions minimale et maximale autorisées du système d’exploitation pour les plateformes prises en charge.
 
![Panneau de restrictions de la configuration de plateforme](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>Dans la pratique
Pour contrôler l’accès à leurs ressources, les organisations utilisent des restrictions de type d’appareil avec les paramètres suivants : 
1. Spécification d’une version minimale du système d’exploitation pour veiller à ce que les utilisateurs finaux utilisent les plateformes actuelles et prises en charge dans l’organisation 
2. Non-spécification d’une version maximale du système d’exploitation (aucune limite) ou indication de la dernière version validée dans l’organisation dans le but de tester en interne les nouvelles versions

Pour plus d’informations, consultez [Définition des restrictions de type d’appareil](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions).
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Signalement des versions de système d’exploitation et respect des stratégies de conformité d’appareil MDM Intune
Les stratégies de conformité d’appareil MDM Intune vous permettent d’effectuer les tâches suivantes : 
- Spécifier des règles de conformité
- Voir l’état de conformité grâce au signalement
- Mettre un appareil en quarantaine et définir un accès conditionnel en cas de non-conformité

Comme les restrictions d’inscription, les stratégies de conformité d’appareil permettent de spécifier les versions minimale et maximale du système d’exploitation. Les stratégies ont également une chronologie de conformité pour offrir à vos utilisateurs une période de grâce pendant laquelle ils doivent se conformer. Les stratégies de conformité d’appareil assurent la conformité des appareils inscrits par les utilisateurs finaux à la stratégie de l’organisation.

![Conformité des appareils : actions pour les appareils non conformes](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>Dans la pratique
Les organisations utilisent des stratégies de conformité d’appareil pour les mêmes scénarios que les restrictions d’inscription. Grâce à ces stratégies, les utilisateurs de votre organisation exécutent des versions de système d’exploitation actuelles et validées. Si l’appareil d’un utilisateur final n’est pas conforme, vous pouvez bloquer son accès aux ressources de l’organisation par le biais de l’accès conditionnel jusqu’à ce que la version de son système d’exploitation soit comprise dans la plage autorisée par votre organisation. Si l’appareil d’un utilisateur final n’est pas conforme, l’utilisateur est notifié et se voit proposer une procédure à suivre pour récupérer l’accès.   

Pour plus d’informations, consultez [Bien démarrer avec la conformité des appareils](https://docs.microsoft.com/intune/device-compliance-get-started).
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Gestion des versions de système d’exploitation à l’aide de stratégies de protection des applications Intune    
Les stratégies de protection des applications Intune et les paramètres d’accès de gestion des applications mobiles (MAM) vous permettent de spécifier la version minimale du système d’exploitation au niveau de la couche application. Vous pouvez ainsi informer vos utilisateurs et les encourager ou les obliger à mettre à jour leur système d’exploitation avec une version minimale spécifiée.
 
Vous avez deux options : 
- **Avertir** : cette option conseille à l’utilisateur final d’effectuer la mise à niveau s’il ouvre une application avec une stratégie de protection d’application ou des paramètres d’accès MAM sur un appareil dont la version du système d’exploitation est antérieure à la version spécifiée. L’accès est autorisé pour l’application et les données de l’organisation.
  ![Image de la boîte de dialogue Avertissement sur la mise à jour d’Android](./media/os-version-update-warning.png) 

- **Bloquer** : cette option indique à l’utilisateur final qu’il doit obligatoirement effectuer la mise à niveau quand il ouvre une application avec une stratégie de protection d’application ou des paramètres d’accès MAM sur un appareil dont la version du système d’exploitation est antérieure à la version spécifiée. L’accès est autorisé pour l’application et les données de l’organisation.
  ![Image de la boîte de dialogue Accès à l’application bloqué](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>Dans la pratique
Les organisations utilisent les paramètres de stratégies de protection des applications pour éduquer les utilisateurs finaux qui ouvrent ou reprennent des applications sur la nécessité de les tenir à jour. Par exemple, pour une version actuelle n, les utilisateurs finaux peuvent recevoir un avertissement s’ils utilisent la version n moins 1 et se voir bloquer l’accès s’ils utilisent la version n moins 2.
 
Pour plus d’informations, consultez [Guide pratique pour créer et affecter des stratégies de protection des applications](https://docs.microsoft.com/intune/app-protection-policies).

## <a name="managing-a-new-operating-system-version-rollout"></a>Gestion du lancement d’une nouvelle version de système d’exploitation
Vous pouvez utiliser les fonctionnalités Intune décrites dans cet article pour migrer le système d’exploitation de votre organisation vers une nouvelle version selon la chronologie de votre choix. Les étapes suivantes fournissent un exemple de modèle de déploiement pour migrer vos utilisateurs du système d’exploitation v1 vers le système d’exploitation v2 en sept jours.
- **Étape 1** : Utilisez des restrictions d’inscription pour exiger le système d’exploitation v2 comme version minimale lors de l’inscription de l’appareil. De cette façon, vous êtes certain que les nouveaux appareils des utilisateurs finaux sont conformes au moment de l’inscription.
- **Étape 2a** : Utilisez des stratégies de protection des applications Intune pour avertir les utilisateurs de l’obligation d’utiliser le système d’exploitation v2 au moment de l’ouverture ou de la reprise de l’application.
- **Étape 2b** : Utilisez des stratégies de conformité d’appareil pour exiger le système d’exploitation v2 comme version minimale d’un appareil conforme. Utilisez des **Actions** en cas de non-conformité pour autoriser une période de grâce de sept jours et envoyer aux utilisateurs finaux une notification par e-mail avec votre chronologie et vos exigences.
  -  Les utilisateurs finaux sont ainsi informés par e-mail de la nécessité de mettre à jour les appareils existants par le biais du portail d’entreprise Intune et au moment de l’ouverture de l’application si elle est associée à une stratégie de protection des applications.
  - Vous pouvez exécuter un rapport de conformité pour identifier les utilisateurs non conformes. 
- **Étape 3a** : Utilisez des stratégies de protection des applications Intune pour bloquer les utilisateurs au moment de l’ouverture ou de la reprise d’une application si l’appareil n’exécute pas le système d’exploitation v2.
- **Étape 3b** : Utilisez des stratégies de conformité d’appareil pour exiger le système d’exploitation v2 comme version minimale d’un appareil conforme.
  - Ces stratégies exigent la mise à jour des appareils pour qu’ils puissent continuer à accéder aux données de l’organisation. Les services protégés sont bloqués s’ils sont utilisés avec l’accès conditionnel aux appareils. Les applications associées à une stratégie de protection des applications sont bloquées quand elles sont ouvertes ou quand elles accèdent aux données de l’organisation.

## <a name="next-steps"></a>Étapes suivantes
Utilisez les ressources suivantes pour gérer les versions de système d’exploitation dans votre organisation : 

- [Définir les restrictions de type d’appareil](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Bien démarrer avec la conformité des appareils](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Guide pratique pour créer et affecter des stratégies de protection des applications](https://docs.microsoft.com/intune/app-protection-policies)
