---
title: Profils de provisionnement d’applications iOS/iPadOS dans Microsoft Intune
titleSuffix: ''
description: Intune vous fournit les outils nécessaires pour affecter de manière proactive un nouveau profil de provisionnement aux appareils dont les applications arrivent à expiration.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 184209573be3a63a1317df702782d4935383c6d9
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781371"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Utiliser les profils de provisionnement d’application iOS pour empêcher l’expiration de vos applications

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Introduction

Les applications métier Apple iOS/iPadOS affectées à des iPhones et des iPads intègrent un profil de provisionnement et du code signé avec un certificat. Quand l’application s’exécute, iOS/iPadOS vérifie son intégrité et applique les stratégies définies par le profil de configuration. Les validations suivantes se produisent :

- **Intégrité du fichier d’installation** : iOS/iPadOS compare les informations détaillées de l’application avec la clé publique du certificat de signature de l’entreprise. Si ces éléments diffèrent, le contenu de l’application est susceptible d’avoir changé. L’application n’est pas autorisée à s’exécuter.
- **Mise en œuvre des fonctionnalités** : iOS/iPadOS tente d’appliquer les fonctionnalités de l’application à partir du profil de configuration d’entreprise (pas les profils de configuration de développeurs) inclus dans le fichier d’installation de l’application (.ipa).


Le certificat de signature d’entreprise que vous utilisez pour signer des applications dure généralement trois ans. Toutefois, le profil de configuration expire au bout d’1 an. Tant que le certificat est toujours valide, Intune vous offre les outils pour affecter de façon proactive un nouveau profil de configuration aux appareils qui disposent d’applications arrivant prochainement à expiration.
Après l’expiration du certificat, vous devez à nouveau signer l’application avec un nouveau certificat et incorporer un nouveau profil de configuration avec la clé du nouveau certificat.

En tant qu’administrateur, vous pouvez inclure et exclure des groupes de sécurité pour affecter une configuration de provisionnement d’application iOS/iPadOS. Par exemple, vous pouvez affecter une configuration de provisionnement d’application iOS/iPadOS à tous les utilisateurs mais exclure un groupe composé de cadres de direction.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Comment créer un profil de configuration d’application mobile iOS

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Profils de provisionnement d’application iOS** > **Créer un profil**.
3. Dans la page **De base**, ajoutez les valeurs suivantes :
    - **Nom** : nommez ce profil de configuration mobile.
    - **Description** : vous pouvez également fournir une description de la stratégie (facultatif).
    - **Charger le fichier de profil** : choisissez **Ouvrir**, puis sélectionnez le fichier de profil de configuration mobile Apple (avec l’extension `.mobileprovision`) que vous avez téléchargé depuis le [site web Apple Developer](https://developer.apple.com/).

   La **date d’expiration** est renseignée à partir d’une valeur dans le fichier de profil de configuration mobile Apple que vous avez ajouté ci-dessus.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Cliquez sur **Suivant : Balises d’étendue**.<br>
   Dans la page **Balises d’étendue**, vous pouvez éventuellement configurer des balises d’étendue pour déterminer qui peut voir le profil de provisionnement d’application iOS/iPadOS dans Intune. Pour plus d’informations sur les balises d’étendue, voir [Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md).
5. Cliquez sur **Suivant : Affectations**.<br>
   La page **Affectations** vous permet d’affecter le profil aux utilisateurs et appareils. Il est important de noter que vous pouvez affecter un profil à un appareil, que celui-ci soit ou non géré par Intune.
6. Cliquez sur **Suivant : Vérifier + créer** pour examiner les valeurs que vous avez entrées pour le profil.
7. Quand vous avez terminé, cliquez sur **Créer** pour créer le profil de provisionnement d’application iOS/iPadOS dans Intune. 

## <a name="next-steps"></a>Étapes suivantes

Affectez le profil aux appareils iOS/iPadOS requis. Pour plus d’informations, suivez les étapes de [Guide pratique pour attribuer des profils d’appareil](../device-profile-assign.md).
