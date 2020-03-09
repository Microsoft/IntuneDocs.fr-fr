---
title: Activer le connecteur Mobile Threat Defense pour les appareils non inscrits
titleSuffix: Microsoft Intune
description: Activez le connecteur Mobile Threat Defense dans Microsoft Intune pour les appareils non inscrits.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
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
ms.openlocfilehash: 25d7c357c0ea313891f80433f33cd4ac57cfad2c
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782087"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Activer le connecteur Mobile Threat Defense dans Intune pour les appareils non inscrits

Pendant l’installation de Mobile Threat Defense (MTD), vous avez configuré une stratégie de classification des menaces dans votre console de partenaire Mobile Threat Defense et vous avez créé la stratégie de protection d’applications dans Intune. Si vous avez déjà configuré le connecteur Intune dans la console de partenaire MTD, vous pouvez maintenant activer la connexion MTD pour les applications de partenaire.

> [!NOTE]
> Cet article s’applique à tous les partenaires Mobile Threat Defense qui prennent en charge des stratégies de protection d’applications :
>
> - Better Mobile (Android, iOS/iPadOS)
> - Zimperium (Android, iOS/iPadOS)
> - Lookout for Work (Android, iOS/iPadOS)

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Les stratégies d’accès conditionnel classiques pour les applications MTD

Quand vous intégrez une nouvelle application à Intune Mobile Threat Defense et que vous activez la connexion à Intune, Intune crée une stratégie d’accès conditionnel classique dans Azure Active Directory. Chaque application MTD que vous intégrez, notamment [Defender ATP](advanced-threat-protection.md) ou un de nos autres [partenaires MTD](mobile-threat-defense.md#mobile-threat-defense-partners), crée une stratégie d’accès conditionnel classique. Ces stratégies peuvent être ignorées, mais elles ne doivent pas être modifiées, supprimées ou désactivées.

Si la stratégie classique est supprimée, vous devrez supprimer la connexion à Intune qui était responsable de sa création, puis la configurer à nouveau. Ce processus recrée la stratégie classique. Il n’est pas possible de migrer des stratégies classiques pour les applications MTD vers le nouveau type de stratégie pour l’accès conditionnel.

Les stratégies d’accès conditionnel classiques pour les applications MTD :

- Sont utilisées par Intune MTD pour exiger que les appareils soient inscrits dans Azure AD afin qu’ils aient un ID d’appareil avant de communiquer avec des partenaires MTD. L’ID est nécessaire pour que les appareils puissent signaler leur état à Intune.

- Aucun effet sur les autres ressources ou applications cloud.

- Sont distinctes des stratégies d’accès conditionnel que vous pouvez créer pour faciliter la gestion de MTD.

- Par défaut, n’interagissez pas avec les autres stratégies d’accès conditionnel que vous utilisez pour l’évaluation.

Pour afficher les stratégies d’accès conditionnel classiques, dans [Azure](https://portal.azure.com/#home), accédez à **Azure Active Directory** > **Accès conditionnel** > **Stratégies classiques**.

## <a name="to-enable-the-mtd-connector"></a>Pour activer le connecteur MTD

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Administration client** > **Connecteurs et jetons** > **Protection contre les menaces mobiles**.

3. Dans le volet **Mobile Threat Defense**, choisissez **Ajouter**.

4. Choisissez votre solution MTD comme **connecteur Mobile Threat Defense à configurer** dans la liste déroulante.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Activez les options nécessaires en fonction des besoins de votre entreprise. Les options visibles dépendent du partenaire MTD.

## <a name="mobile-threat-defense-toggle-options"></a>Options de Mobile Threat Defense

Vous pouvez décider des options MTD que vous devez activer en fonction des besoins de votre entreprise. Voici des informations détaillées concernant ces options :

**Paramètres de stratégie de protection des applications**

- **Connecter les appareils Android 4.4 et versions ultérieures à *\<Nom du partenaire MTD>* pour l’évaluation de la stratégie de protection des applications** : Lorsque vous activez cette option, les stratégies de protection des applications qui utilisent la règle de niveau de menace de l’appareil évaluent les appareils, y compris les données de ce connecteur.

- **Connecter les appareils iOS version 11 et ultérieure à *\<nom du partenaire MTD>* pour l’évaluation de la stratégie de protection des applications** : Lorsque vous activez cette option, les stratégies de protection des applications qui utilisent la règle de niveau de menace de l’appareil évaluent les appareils, y compris les données de ce connecteur.

**Paramètres partagés communs**

- **Nombre de jours avant de considérer que le partenaire n’est pas réactif** : nombre de jours d’inactivité au bout desquels Intune considère que le partenaire n’est pas réactif en raison de la perte de connexion. Intune ignore l’état de conformité pour les partenaires MTD non réactifs.

> [!TIP]
> Vous pouvez voir l’**état de la connexion** et l’heure de la **dernière synchronisation** entre Intune et le partenaire MTD dans le volet Mobile Threat Defense.

## <a name="next-steps"></a>Étapes suivantes

- [Créer une stratégie de protection d’applications Mobile Threat Defense (MTD) avec Intune](~/protect/mtd-app-protection-policy.md).
