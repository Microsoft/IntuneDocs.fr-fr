---
title: Qu’est-ce que la gestion des applications dans Microsoft Intune ?
titleSuffix: ''
description: En savoir plus sur les fonctionnalités de gestion des applications client par plateforme pour Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a0d495265580bc9801a1fadb636a62274a4f728a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725749"
---
# <a name="what-is-microsoft-intune-app-management"></a>Qu’est-ce que la gestion des applications Microsoft Intune ?


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En tant qu’administrateur informatique, vous pouvez utiliser Microsoft Intune pour gérer les applications clientes utilisées par les équipes de votre entreprise. Cette fonctionnalité s’ajoute à la gestion des appareils et à la protection des données. L’une des priorités d’un administrateur est de vérifier que les utilisateurs finaux ont accès aux applications dont ils ont besoin pour travailler. Cet objectif peut représenter un défi, car :
- Il existe un large éventail de plateformes d'appareils et de types d’applications.
- Vous devrez peut-être gérer des applications sur les appareils de l’entreprise, ainsi que sur les appareils personnels des utilisateurs.
- Vous devez vérifier que votre réseau et vos données restent sécurisés.

Vous pourrez également souhaiter affecter et gérer des applications sur les appareils qui ne sont pas inscrits avec Intune.

## <a name="mobile-application-management-mam-basics"></a>Notions de base de la gestion des applications mobiles (MAM)

La [gestion des applications mobiles Intune](app-lifecycle.md) se rapporte à la suite de fonctionnalités de gestion Intune qui vous permettent de publier, d’envoyer des notifications Push, de configurer, de sécuriser, de surveiller et de mettre à jour des applications mobiles pour vos utilisateurs.

La gestion MAM vous permet de gérer et de protéger les données de votre organisation au sein d'une application. La gestion **MAM sans inscription** (MAM-WE) permet de gérer les applications professionnelles et scolaires contenant des données sensibles sur pratiquement tous types d’[appareils](app-management.md#app-management-capabilities-by-platform), y compris les appareils personnels dans les scénarios BYOD (**Apportez votre propre appareil**). Plusieurs applications de productivité, telles que les applications Microsoft Office, peuvent être gérées par la MAM Intune. Consultez la liste officielle des [applications protégées par Microsoft Intune](apps-supported-intune-apps.md) accessibles au public.

La MAM Intune prend en charge deux configurations :
- **Gestion des appareils mobiles et gestion des applications mobiles Intune** : Les administrateurs informatiques peuvent uniquement gérer des applications à l’aide de la MAM et des stratégies de protection des applications sur des appareils inscrits à la gestion des périphériques mobiles (MDM). Pour gérer des applications en utilisant à la fois la gestion MDM et la gestion MAM, les clients doivent utiliser la console Intune sur le portail Azure, à l’adresse https://portal.azure.com.
- **MAM sans inscription d’appareils** : la MAM sans inscription d’appareils (ou MAM-WE en anglais), permet aux administrateurs informatiques de gérer des applications à l’aide de la MAM et de stratégies de protection des applications sur les appareils qui ne sont ne pas inscrits à la MDM Intune. Cela signifie que les applications peuvent être gérées par Intune sur des appareils inscrits avec des fournisseurs EMM tiers. Pour gérer des applications à l’aide de la MAM sans inscription d’appareils, les clients doivent utiliser la console Intune dans le portail Azure à l’adresse https://portal.azure.com. Il est également possible de gérer les applications avec Intune sur les appareils inscrits auprès de fournisseurs tiers de gestion de la mobilité d’entreprise (EMM) ou non inscrits à un quelconque service de gestion MDM. Pour plus d’informations sur BYOD et la solution EMS de Microsoft, voir [Décisions d’ordre informatique pour activer BYOD avec Microsoft Enterprise Mobility + Security (EMS)](../fundamentals/byod-technology-decisions.md).

## <a name="app-management-capabilities-by-platform"></a>Fonctionnalités de gestion d’application par plateforme

Intune propose toute une gamme de fonctionnalités qui vous permettent de gérer les applications dont vous avez besoin sur les appareils de votre choix. Le tableau suivant fournit un récapitulatif des fonctionnalités de gestion des applications.

|  | Android/Android Enterprise | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Ajouter et affecter des applications à des appareils et à des utilisateurs | Oui | Oui | Oui | Oui | Oui |
| Affecter des applications à des appareils non inscrits auprès d’Intune | Oui | Oui | Non | Non | Non |
| Utiliser des stratégies de configuration d’application pour contrôler le comportement des applications au démarrage | Oui | Oui | Non | Non | Non |
| Utiliser des stratégies d’approvisionnement d’application mobile pour renouveler les applications arrivées à expiration | Non | Oui | Non | Non | Non |
| Protéger les données de l’entreprise dans les applications avec des stratégies de protection d’applications | Oui | Oui | Non | Non <sup>1</sup> | Non |
| Supprimer exclusivement les données d’entreprise d’une application installée (effacement d’application sélectif) | Oui | Oui | Non | Oui | Oui |
| Effectuer le monitoring des affectations d’applications | Oui | Oui | Oui | Oui | Oui |
| Affecter et suivre des applications achetées en volume dans un App Store | Non | Non | Non | Oui | Non |
| Installation obligatoire d’applications sur les appareils (obligatoire) <sup>2</sup> | Oui | Oui | Oui | Oui | Oui |
| Installation facultative sur les appareils à partir du Portail d’entreprise (installation disponible) | Oui <sup>3</sup> | Oui | Oui | Oui | Oui |
| Installer un raccourci vers une application sur le web (lien web) | Oui <sup>4</sup> | Oui | Oui | Oui | Oui |
| Applications métier internes | Oui | Oui | Oui | Oui | Non |
| Applications issues d’un magasin | Oui | Oui | Non | Oui | Oui |
| Mettre à jour des applications | Oui | Oui | Non | Oui | Oui |

<sup>1</sup> Envisagez d’utiliser [Windows Information Protection](../windows-information-protection-configure.md) pour protéger les applications sur les appareils qui exécutent Windows 10.<br>
<sup>2</sup> S’applique uniquement aux appareils gérés par Intune.<br>
<sup>3</sup> Intune prend en charge les applications disponibles dans le Google Play Store géré sur les appareils Android Enterprise.<br>
<sup>4</sup> Intune n’installe aucun raccourci vers une application en tant que lien web sur les appareils Android Enterprise standard. Cependant, la prise en charge des liens web est fournie pour [les appareils Android Enterprise dédiés à plusieurs applications ](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings). 


## <a name="get-started"></a>Prise en main

Vous pouvez trouver la plupart des informations relatives aux applications dans la charge de travail **Applications clientes**, à laquelle vous pouvez accéder comme suit :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Microsoft Intune**, sélectionnez **Applications clientes**.

    ![Volet de la charge de travail « Applications clientes »](./media/app-management/apps-workload.png)

Les quatre prochaines sections décrivent les options disponibles dans le volet **Applications clientes**.

### <a name="manage"></a>Gestion
- **Applications** : sélectionnez cette option pour ajouter, afficher, affecter et analyser les applications que le personnel utilise. Pour plus d'informations, voir :
  - [Ajouter des applications](apps-add.md).
  - [Affecter des applications](apps-deploy.md).
  - [Surveiller des applications](apps-monitor.md).
- **Stratégies de configuration des applications** : sélectionnez cette option pour fournir les paramètres qui peuvent être nécessaires quand un utilisateur exécute une application. Pour plus d'informations, voir :
  - [Stratégies de configuration des applications pour Intune](app-configuration-policies-overview.md).
    - [Stratégies de configuration des applications iOS](app-configuration-policies-use-ios.md).
    - [Stratégies de configuration des applications Android](app-configuration-policies-use-android.md).
- **Stratégies de protection des applications** : sélectionnez cette option pour associer des paramètres à une application et protéger les données d’entreprise qu’elle utilise. Par exemple, vous pouvez limiter les fonctionnalités d’une application quand elle communique avec d’autres applications, ou vous pouvez demander à l’utilisateur d’entrer un code PIN pour accéder à une application d’entreprise. Pour plus d'informations, voir :
  - [Stratégies de protection des applications](app-protection-policies.md).
- **Réinitialisation sélective des applications** : sélectionnez cette option pour supprimer uniquement les données d’entreprise de l’appareil d’un utilisateur spécifique. Pour plus d'informations, voir :
  - [Réinitialisation sélective des applications](apps-selective-wipe.md).
- **Profils de provisionnement d’application iOS** : les applications iOS incluent un profil de provisionnement et un code signé par un certificat. Lors de l’expiration du certificat, l’application ne peut plus être exécutée. Intune vous fournit les outils nécessaires pour affecter de manière proactive une nouvelle stratégie de profil de provisionnement aux appareils dont les applications arrivent à expiration. Pour plus d'informations, voir :
  - [Profils de provisionnement d’applications iOS](app-provisioning-profile-ios.md).

Pour plus d’informations sur cette section, consultez [Gérer des applications](app-management.md).

### <a name="monitor"></a>Surveillance
- **Licences d’application** : affichez, affectez et surveillez les applications achetées en volume dans les App Stores. Pour plus d'informations, voir :
  - [Applications du Programme d’achat en volume (VPP) iOS](vpp-apps-ios.md).
  - [Applications achetées en volume sur le Microsoft Store pour Entreprises](windows-store-for-business.md).
- **Applications découvertes** : affichez les applications affectées par Intune ou installées sur un appareil. Pour plus d’informations, voir [Applications découvertes Intune](app-discovered-apps.md).
- **État de l'installation de l’application** : affichez l’état d’une affectation d’application que vous avez créée. Pour plus d’informations, voir [Effectuer le monitoring des affectations et des informations sur les applications avec Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **État de protection de l’application** : affichez l’état d’une stratégie de protection d’application pour l’utilisateur sélectionné.
- **Journaux d’audit** : affichez les activités liées à l’application Intune et effectuées par tous les administrateurs informatiques.

Pour plus d’informations sur cette section, consultez [Surveiller les applications](apps-monitor.md).

### <a name="set-up"></a>Configurer
- **Jetons VPP iOS** : appliquez et affichez vos licences du programme VPP (programme d’achat en volume) iOS. Pour plus d'informations, voir :
  - [Applications iOS achetées en volume](vpp-apps-ios.md)
- **Certificat d’entreprise Windows** : appliquez ou affichez l’état d’un certificat de signature de code permettant de distribuer des applications métier sur vos appareils Windows gérés.
- **Certificat Symantec Windows** : appliquez ou affichez l’état d’un certificat de signature de code Symantec permettant de distribuer des fichiers appx XAP et WP8.x sur des appareils Windows 10 Mobile.
- **Microsoft Store pour Entreprises** : configurez l’intégration au Microsoft Store pour Entreprises. Par la suite, vous pouvez synchroniser les applications achetées avec Intune, les affecter et suivre l’utilisation des licences. Pour plus d'informations, voir :
  - [Applications achetées en volume sur le Microsoft Store pour Entreprises](windows-store-for-business.md).
- **Clés de chargement indépendant Windows** : ajoutez une clé de chargement indépendant Windows pour installer une application directement sur des appareils, au lieu de la publier et de la télécharger à partir du Windows Store. Pour plus d'informations, voir :
  - [Chargement indépendant d’une application Windows](app-sideload-windows.md).
- **Personnalisation du portail d’entreprise** : personnalisez le portail d’entreprise pour lui donner une image proche de votre société. Pour plus d'informations, voir :
  - [Configuration du portail d’entreprise](company-portal-app.md).
- **Catégories d’applications** : ajoutez, épinglez et supprimez des noms de catégories d’application.
- **Profil professionnel Android** : approuvez et synchronisez les applications que vous avez approuvées pour votre entreprise. Pour plus d'informations, voir :
  - [Applications de profil professionnel Android](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Aide et support
- **Aide et support** : résolvez des problèmes, demandez du support ou affichez l’état d’Intune. Pour plus d'informations, voir :
  - [Résolution des problèmes](../fundamentals/help-desk-operators.md).

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter une application à Microsoft Intune](apps-add.md)
