---
title: Activer le connecteur Mobile Threat Defense pour les appareils non inscrits
titleSuffix: Microsoft Intune
description: Activez le connecteur Mobile Threat Defense dans Microsoft Intune pour les appareils non inscrits.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2744a27a733824bab9d920f4de0b49e951c1c34
ms.sourcegitcommit: a4c7339ec9ff5b1b846cb3cca887cf91b5cd4baa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627636"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Activer le connecteur Mobile Threat Defense dans Intune pour les appareils non inscrits

Pendant l’installation de Mobile Threat Defense (MTD), vous avez configuré une stratégie de classification des menaces dans votre console de partenaire Mobile Threat Defense et vous avez créé la stratégie de protection d’applications dans Intune. Si vous avez déjà configuré le connecteur Intune dans la console de partenaire MTD, vous pouvez maintenant activer la connexion MTD pour les applications de partenaire.

> [!NOTE] 
> Cet article s’applique à tous les partenaires Mobile Threat Defense qui prennent en charge des stratégies de protection d’applications : Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>Pour activer le connecteur MTD

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Dans le **Tableau de bord Intune**, choisissez **Conformité des appareils**, puis **Protection contre les menaces mobiles** sous la section **Configuration**.

3. Dans le volet **Mobile Threat Defense**, choisissez **Ajouter**.

4. Choisissez votre solution MTD comme **connecteur Mobile Threat Defense à configurer** dans la liste déroulante.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Modifiez les options en fonction des besoins de votre organisation. Les options visibles dépendent du partenaire MTD.

## <a name="mtd-toggle-options"></a>Options MTD

Vous pouvez décider des options MTD que vous devez activer en fonction des besoins de votre entreprise. Voici plus de détails :

**Paramètres de stratégie de protection des applications**
- **Connecter les appareils Android 4.4 et versions ultérieures à *\<Nom du partenaire MTD>* pour l’évaluation de la stratégie de protection des applications** : Lorsque vous activez cette option, les stratégies de protection des applications qui utilisent la règle de niveau de menace de l’appareil évaluent les appareils, y compris les données de ce connecteur.
- **Connecter les appareils iOS version 11 et ultérieure à *\<nom du partenaire MTD>* pour l’évaluation de la stratégie de protection des applications** : Lorsque vous activez cette option, les stratégies de protection des applications qui utilisent la règle de niveau de menace de l’appareil évaluent les appareils, y compris les données de ce connecteur.

**Paramètres partagés communs**
- **Nombre de jours avant de considérer que le partenaire n’est pas réactif** : nombre de jours d’inactivité au bout desquels Intune considère que le partenaire n’est pas réactif en raison de la perte de connexion. Intune ignore l’état de conformité pour les partenaires MTD non réactifs.

> [!TIP]
> Vous pouvez voir l’**état de la connexion** et l’heure de la **dernière synchronisation** entre Intune et le partenaire MTD dans le volet Mobile Threat Defense.

> [!NOTE] 
> Quand vous activez la connexion Mobile Threat Defense à Intune, Intune crée une stratégie d’accès conditionnel standard dans Azure Active Directory. Chaque application MTD que vous intégrez, notamment [Defender ATP](advanced-threat-protection.md) ou un de nos autres [partenaires MTD](mobile-threat-defense.md#mobile-threat-defense-partners), crée une stratégie d’accès conditionnel classique. **Ces stratégies peuvent être ignorées, mais elles ne doivent pas être modifiées, supprimées ou désactivées.**
> 
> Les stratégies d’accès conditionnel classiques pour les applications MTD : 
> - Sont utilisées par Intune MTD pour exiger que les appareils soient inscrits dans Azure AD afin qu’ils aient un ID d’appareil avant de communiquer avec des partenaires MTD. L’ID est nécessaire pour que les appareils puissent signaler leur état à Intune.  
> - Aucun effet sur les autres ressources ou applications cloud.  
> - Sont distinctes des stratégies d’accès conditionnel que vous pouvez créer pour faciliter la gestion de MTD ou pour exiger l’autorité de certification de protection des applications
> - Par défaut, n’interagissez pas avec les autres stratégies d’accès conditionnel que vous utilisez pour l’évaluation.  
>
> Pour afficher les stratégies d’accès conditionnel classiques, dans [Azure](https://portal.azure.com/#home), accédez à **Azure Active Directory** > **Accès conditionnel** > **Stratégies classiques**.

## <a name="next-steps"></a>Étapes suivantes

- [Créer une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Intune](~/protect/mtd-app-protection-policy.md).
