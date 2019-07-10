---
title: Applications pour les environnements GCC High et DoD
titleSuffix: Microsoft Intune
description: Apprenez-en davantage sur les applications impliquant des environnements GCC High et DoD à l’aide de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17d94252dd957c5699b34e0b8c2cbae2eee0b66f
ms.sourcegitcommit: 63b55e81122e5c15893302b109ae137c30855b55
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67713355"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Déploiement d’applications à l’aide d’Intune dans les environnements GCC High et DoD 

Les administrateurs de locataires peuvent utiliser Microsoft Intune pour distribuer des applications aux employés de la société. De nombreux types d’applications peuvent être déployés à partir d’Intune dans des environnements GCC High ou DoD. Si un administrateur a besoin de charger et de distribuer à une audience GCC High ou DoD une application Windows personnalisée et créée par des fournisseurs tiers, ou une application hors connexion téléchargée à partir du [Microsoft Store pour Entreprises](https://businessstore.microsoft.com/store), il peut choisir de la distribuer en tant qu’[application métier](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Pour les environnements commerciaux, un administrateur de locataires peut synchroniser son Store pour Entreprises avec Intune, mais pour les environnements GCC High et DoD ce service n’est pas disponible. Dans ce cas, les administrateurs doivent déployer l’application en la chargeant directement dans Intune.  

## <a name="add-line-of-business-apps-using-intune"></a>Ajouter des applications métier à l’aide d’Intune 

Pour ajouter une application métier destinée à un environnement GCC High ou DoD à l’aide d’Intune, vous pouvez suivre les instructions relatives aux [applications métier Windows](lob-apps-windows.md). Vous pouvez choisir de déployer d’abord le portail d’entreprise à partir du Microsoft Store pour Entreprises. Si vous choisissez d’utiliser le portail d’entreprise, vous pouvez l’installer et le déployer manuellement. Pour plus d’informations, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Distribuer des applications hors connexion à partir du Store pour Entreprises à l’aide d’Intune  

Si vous avez besoin de [télécharger une application sous licence hors connexion](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) à partir du Microsoft Store pour Entreprises, suivez ces étapes : 

1. Connectez-vous au [Store pour Entreprises](https://businessstore.microsoft.com/).
2. Sélectionnez **Gérer** > **Paramètres**.
3. Sous **Expérience d’achat**, affectez la valeur **Activé** à **Afficher les applications hors connexion**.

Lors de la recherche d’application dans le Store, s’il existe une version hors connexion, vous pouvez changer le type de licence et choisir « hors connexion ». Une fois l’application obtenue, vous pouvez la gérer en sélectionnant **Gérer** > **Produits et services** dans le [Store pour Entreprises](https://businessstore.microsoft.com/). Vous pouvez aussi télécharger l’application et ses dépendances. Ensuite, vous pouvez déployer cette application téléchargée (et ses dépendances) pour les utilisateurs à l’aide d’Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>Synchronisation d’Intune avec le Store pour Entreprises 

Dans un environnement commercial (non gouvernemental), un administrateur peut synchroniser Intune avec le Microsoft Store pour Entreprises. Cette fonctionnalité n’est pas disponible dans les environnements gouvernementaux. Pour plus d’informations sur les différences entre Intune dans les environnements commerciaux et Intune pour les environnements gouvernementaux, consultez [Description du service Enterprise Mobility + Security pour le secteur public américain](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Pour synchroniser Intune avec votre compte Store pour Entreprises, consultez [Guide pratique pour gérer les applications que vous avez achetées dans le Microsoft Store pour Entreprises avec Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Compatibilité 

Passez en revue les déclarations de confidentialité et de conformité des applications et comparez-les aux exigences de conformité, de sécurité et de confidentialité de votre organisation lors de l’évaluation de l’utilisation appropriée de ces services.   

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le déploiement et l’attribution d’applications, consultez [Attribuer des applications à des groupes avec Microsoft Intune](apps-deploy.md).

 
