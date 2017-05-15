---
title: "Qu’est-ce que la gestion des applications | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : Utilisez cette rubrique pour apprendre les notions de gestion des applications avec Microsoft Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: a9748a0ad6b9bbe10e36ba133ba74edb6aa6e09a
ms.openlocfilehash: 34970d6adcfe41a6de9636a5605a17f9f5ef2d82
ms.contentlocale: fr-fr
ms.lasthandoff: 05/05/2017


---

# <a name="what-is-microsoft-intune-app-management"></a>Qu’est-ce que la gestion des applications Microsoft Intune ?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


En tant qu’administrateur informatique, vous allez probablement avoir la charge de vous assurer que vos utilisateurs ont accès aux applications dont ils ont besoin pour effectuer leur travail. Cela peut être un défi, car :
- Il existe un large éventail de plateformes d'appareils et de types d’applications.
- Vous devrez peut-être gérer des applications sur des appareils d’entreprise ainsi que des appareils personnels des utilisateurs.
- Vous devez faire tout cela, tout en veillant à la sécurité de votre réseau et de vos données. 

Vous pourrez également souhaiter affecter et gérer des applications sur les appareils qui ne sont pas inscrits avec Intune.

Intune propose une gamme de fonctionnalités pour vous aider à obtenir les applications dont vous avez besoin, sur les appareils de votre choix.

## <a name="app-management-capabilities-by-platform"></a>Fonctionnalités de gestion d’application par plateforme

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|Ajout et affectation d’applications pour des appareils et utilisateurs|Oui|Oui|Oui|Oui|
|Affectation d’applications pour les appareils non inscrits avec Intune|Oui|Oui|Non|Non|
|Utilisation de stratégies de configuration d’application pour contrôler le comportement des applications au démarrage|Non|Oui|Non|Non|
|Utilisation de stratégies de configuration d’application mobile pour renouveler les applications arrivées à expiration|Non|Oui|Non|Non|
|Protection des données dans les applications avec des stratégies de protection d’application|Oui|Oui|Non|Non<sup>1</sup>|
|Suppression des données d’entreprise uniquement à partir d’une application installée (réinitialisation sélective d’application)|Oui|Oui|Oui|Oui|
|Surveillance des affectations d’applications|Oui|Oui|Oui|Oui|
|Affectation et suivi des applications achetées en volume à partir d’une boutique d’applications|Non|Non|Non|Oui|
|Installation obligatoire d’applications sur des appareils (requis)<sup>2</sup>|Oui|Oui|Oui|Oui|
|Installation facultative sur des appareils à partir du portail d’entreprise (installation disponible)|Oui|Oui|Oui|Oui|
|Installation d’un raccourci vers une application sur le web (clip web)|Oui|Oui|Oui|Oui|
|Applications métier internes|Oui|Oui|Non|Non|
|Applications à partir d’une boutique|Oui|Oui|Oui|Oui|
|Mettre à jour des applications|Oui|Oui|Oui|Oui|

<sup>1</sup> Envisagez d’utiliser [Windows Information Protection](/intune-azure/configure-devices/how-to-configure-windows-information-protection) pour protéger les applications sur les appareils qui exécutent Windows 10.

<sup>2</sup>S’applique aux appareils gérés par Intune uniquement.


## <a name="how-to-get-started"></a>Mise en route

Vous trouverez la plupart des éléments liés à l’application dans la charge de travail **Mobile Apps**, à laquelle vous pouvez accéder comme suit :

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de Services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Applications mobiles**.

    ![La charge de travail Mobile Apps](./media/apps-workload.png)

### <a name="manage"></a>Gestion
- **Applications** : c’est ici que vous allez ajouter, affecter et surveiller la plupart de vos applications. 
    - [Ajouter des applications](add-apps.md)
    - [Attribuer des applications](deploy-apps.md)
    - [Surveillance des applications](monitor-apps.md)
- **Stratégies de configuration d’application** : les stratégies de configuration d’application vous permettent de fournir des paramètres pouvant être nécessaires quand un utilisateur exécute une application. Pour plus d'informations, consultez :
    - [Stratégies de configuration des applications](app-configuration-policies.md)
- **Stratégies de protection d’application** : vous permettent d’associer des paramètres à une application afin de protéger les données d’entreprise qu’elle utilise. Par exemple, vous pourrez limiter les fonctionnalités d’une application pour communiquer avec d’autres applications, ou demander à l’utilisateur d’entrer un code confidentiel pour accéder à une application d’entreprise.
    - [Stratégies de protection des applications](app-protection-policies.md)
- **Réinitialisation sélective d’application** : supprime uniquement les données d’entreprise à partir d’un appareil utilisateur que vous sélectionnez.
    - [Réinitialisation sélective d’applications](app-selective-wipe.md)
- **Profils de configuration iOS** : les applications iOS incluent un profil de configuration et du code signé par un certificat. Lors de l’expiration du certificat, l’application ne peut plus être exécutée. Intune vous offre les outils pour affecter de façon proactive une nouvelle stratégie de profil de configuration pour les appareils qui disposent d’applications arrivant prochainement à expiration.
    - [Profils de configuration d’applications iOS](ios-app-provisioning-profile.md)

### <a name="monitor"></a>Surveillance
- **Applications sous licence** : affichez, affectez et surveillez les applications achetées en volume dans les App Stores.
    - [Applications achetées en volume à partir du Windows Store pour Entreprises](wsfb-apps.md)
- **Applications découvertes** : affiche toutes les applications qui ont été affectées par Intune et installées sur un appareil.
- **État d’installation de l’application** : affiche l’état d’une affectation d’application que vous avez créée.
- **État de protection de l’application** : affiche l’état d’une stratégie de protection d’application pour un utilisateur que vous sélectionnez.

Pour plus d’informations, consultez [Surveiller des applications](monitor-apps.md)

### <a name="setup"></a>Setup
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](ios-vpp-apps.md) --->
- **Windows Store pour Entreprises** : configurer l’intégration à Windows Store pour les entreprises. Après cela, vous pouvez synchroniser les applications achetées à Intune, et affecter puis suivre l’utilisation de votre licence. 
    - [Applications achetées en volume à partir du Windows Store pour Entreprises](wsfb-apps.md)
- **Personnalisation du portail d’entreprise** : personnalisez le portail d’entreprise pour lui donner une image proche de votre société. 
    - [Configuration du portail d’entreprise](company-portal-app.md)

