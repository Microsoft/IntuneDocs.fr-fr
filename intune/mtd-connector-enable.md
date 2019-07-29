---
title: Activer le connecteur Mobile Threat Defense dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Activez le connecteur entre votre partenaire Mobile Threat Defense (MTD) et Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4dd77be45c21db53dd82322049d377ced247c4c7
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427341"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Activer le connecteur Mobile Threat Defense dans Intune

> [!NOTE] 
> Cette rubrique s’applique à tous les partenaires Mobile Threat Defense.

Pendant l’installation de Mobile Threat Defense (MTD), vous avez configuré une stratégie de classification des menaces dans votre console de partenaire MTD et avez créé la stratégie de conformité des appareils dans Intune. Si vous avez déjà configuré le connecteur Intune dans la console de partenaire MTD, vous pouvez maintenant activer la connexion MTD pour les applications de partenaire.

Quand vous intégrez une nouvelle application à Intune Mobile Threat Defense et que vous activez la connexion, Intune crée une stratégie d’accès conditionnel classique dans Azure Active Directory. Chaque application MTD que vous intégrez, comme [Defender ATP](advanced-threat-protection.md) ou un de nos autres [partenaires MTD](mobile-threat-defense.md#mobile-threat-defense-partners), crée une stratégie d’accès conditionnel classique.  Ces stratégies peuvent être ignorées, mais elles ne doivent pas être modifiées, supprimées ou désactivées.

Les stratégies d’accès conditionnel classiques pour les applications MTD : 

- Sont utilisées par Intune MTD pour exiger que les appareils soient inscrits dans Azure AD afin qu’ils aient un ID d’appareil. L’ID est nécessaire pour que les appareils puissent signaler leur état à Intune.  
- Sont distinctes des stratégies d’accès conditionnel que vous pouvez créer pour faciliter la gestion de MTD.
- Par défaut, n’interagissez pas avec les autres stratégies d’accès conditionnel que vous utilisez pour l’évaluation.  

Pour afficher les stratégies d’accès conditionnel classiques, dans [Azure](https://portal.azure.com/#home), accédez à **Azure Active Directory** > **Accès conditionnel** > **Stratégies classiques**.


## <a name="to-enable-the-mtd-connector"></a>Pour activer le connecteur MTD

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. Dans le **Tableau de bord Intune**, choisissez **Conformité des appareils**, puis **Protection contre les menaces mobiles** sous la section **Configuration**.

5. Dans le volet **Mobile Threat Defense**, choisissez **Ajouter**.

6. Choisissez votre solution MTD comme **connecteur Mobile Threat Defense à configurer** dans la liste déroulante.

    ![Configuration de MTD dans le portail Intune Azure](./media/enable-mtd-connector-1.png)

7. Modifiez les options en fonction des besoins de votre organisation. Les options visibles dépendent du partenaire MTD.

## <a name="mtd-toggle-options"></a>Options MTD

Vous pouvez décider des options MTD que vous devez activer en fonction des besoins de votre entreprise. Voici plus de détails :

- **Connecter les appareils Android 4.1+ à [nom du partenaire MTD] for Work MTD** : quand vous activez cette option, les appareils Android version 4.1 ou ultérieure peuvent signaler les risques de sécurité à Intune.
  - **Marquer comme non conforme si aucune donnée n’est reçue** : si Intune ne reçoit pas de données du partenaire MTD concernant un appareil sur cette plateforme, l’appareil est considéré comme non conforme.
<br></br>
- **Connecter les appareils iOS 8.0+ à [nom du partenaire MTD] for Work MTD** : quand vous activez cette option, les appareils iOS version 8.0 ou ultérieure peuvent signaler les risques de sécurité à Intune.
  - **Marquer comme non conforme si aucune donnée n’est reçue** : si Intune ne reçoit pas de données du partenaire MTD concernant un appareil sur cette plateforme, l’appareil est considéré comme non conforme.
<br></br>
- **Activer la synchronisation des applications pour les appareils iOS** : autorise ce partenaire Mobile Threat Defense à demander les métadonnées des applications iOS dans Intune afin d’analyser les menaces.

- **Bloquer les versions de système d’exploitation non prises en charge** : bloque l’appareil s’il exécute un système d’exploitation d’une version antérieure à la version minimale prise en charge.

- **Nombre de jours avant de considérer que le partenaire n’est pas réactif** : nombre de jours d’inactivité au bout desquels Intune considère que le partenaire n’est pas réactif en raison de la perte de connexion. Intune ignore l’état de conformité pour les partenaires MTD non réactifs.

> [!IMPORTANT] 
> Dans la mesure du possible, nous vous recommandons d’ajouter et d’affecter les applications MTD avant de créer les règles de conformité des appareils et de stratégie d’accès conditionnel. Cela aide à garantir que l’application MTD est prête et mise à la disposition des utilisateurs finaux qui souhaitent l’installer pour pouvoir accéder à leur e-mail ou à d’autres ressources de l’entreprise.

> [!TIP]
> Vous pouvez voir l’**état de la connexion** et l’heure de la **dernière synchronisation** entre Intune et le partenaire MTD dans le volet Mobile Threat Defense.
