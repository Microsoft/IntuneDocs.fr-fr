---
title: Préparation de Microsoft Intune à la gestion des appareils mobiles
titlesuffix: Microsoft Intune
description: Évaluez vos exigences stratégiques et techniques avant de migrer vers Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 1e21fef5102b22dfe698a9adb73736508452acfe
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186373"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>Phase 1 : Préparer Microsoft Intune à la gestion des appareils mobiles (MDM)

Avant d’étudier plus en détail la configuration d’Intune, passons en revue les exigences de la gestion des appareils mobiles de votre organisation. Il peut être judicieux d’exécuter des rapports d’utilisateurs actifs dans votre fournisseur MDM actuel de façon à identifier les groupes d’utilisateurs critiques. Dès lors, vous pourrez commencer à vous pencher sur les questions de la section [Évaluation des exigences MDM](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Évaluation des exigences MDM

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Quels appareils devez-vous prendre en charge ?

-   Quelles [plates-formes](supported-devices-browsers.md) devez-vous prendre en charge ?

-   Les appareils que vous devez prendre en charge appartiennent-ils à l’entreprise ou s’agit d’appareils personnels ?

-   Quel type de connectivité utilisez-vous ? Wi-Fi, mobile ou VPN ?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>Quelles opérations vos utilisateurs doivent-ils exécuter sur les appareils gérés ?

-   Devez-vous configurer des applications pour vos utilisateurs finaux ?

-   Utilisez-vous des applications métier personnalisées ? Avez-vous uniquement besoin d’applications de Store public ?

-   Devez-vous configurer des comptes e-mail ?

### <a name="what-kinds-of-users"></a>Quels sont les types d’utilisateurs ?

-   Combien de personnes utiliseront un seul appareil ?

-   De quelles conditions d’utilisation avez-vous besoin ?

    -   Veillez à faire appel au service juridique aussitôt que possible.
    -   Quelle est la localisation requise ?

-   Les utilisateurs sont-ils familiarisés avec la technologie et l’informatique en général ?

### <a name="what-is-your-device-security-policy"></a>Quelle stratégie de sécurité des appareils mobiles comptez-vous appliquer ?

- Devez-vous appliquer un chiffrement au niveau des appareils ?

- Quelle est la longueur actuelle des codes PIN/codes secrets de vos appareils ?

- Devez-vous désactiver des fonctionnalités de l’appareil, ou imposer des restrictions à certains comportements des appareils ? Vous pouvez contrôler différents paramètres spécifiques de la plateforme grâce aux profils de configuration des appareils, par exemple :
    - Désactiver l’appareil photo
    - Verrouiller le mode d’application unique<br/>

- Quels types d’authentification devez-vous prendre en charge ? Si vous avez besoin d’une authentification basée sur un certificat, quels types de certificat faut-il configurer ?
  - Intune peut configurer des certificats avec des profils d’accès aux ressources pour les appareils inscrits.
  -   Quel type d’infrastructure à clé publique (PKI) devez-vous prendre en charge ?
  <br></br>
- Devez-vous prendre en charge un réseau privé virtuel (VPN) au niveau des appareils ou des applications ?

  -   Intune peut configurer des configurations VPN pour les fournisseurs VPN tiers.
  <br/><br/>
- Est-il possible de mettre en place des exceptions temporaires pour certaines exigences afin d’éviter les temps d’arrêt ? Ou les appareils dotés d’un accès doivent-ils toujours se conformer aux exigences de sécurité ?

## <a name="next-steps"></a>Étapes suivantes
Pour voir comment des entreprises de différents secteurs d’activité ont évalué leurs besoins en matière de gestion des appareils mobiles, consultez ces [études de cas](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune).

Examinez la [configuration de base Intune](migration-guide-setup.md).
