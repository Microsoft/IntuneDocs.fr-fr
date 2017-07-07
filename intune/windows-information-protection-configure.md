---
title: Configurer Protection des informations Windows - Intune
titleSuffix: Intune on Azure
description: "Découvrez les paramètres Intune que vous pouvez utiliser pour gérer la Protection des informations Windows."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f233672c-7d9b-4554-af1f-92c001a1a3c5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ac59456dd2bc59a0a50eeab4e483dea2033c0fa
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Guide pratique pour configurer la Protection des informations Windows dans Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Avec l’augmentation du nombre d’appareils appartenant aux employés au sein de l’entreprise, il existe un risque accru de fuites accidentelles de données via les applications et les services, tels que le courrier électronique, les réseaux sociaux et le cloud public, qui sont en dehors du contrôle de l’entreprise. Par exemple, lorsqu’un employé envoie les dernières photos de conception à partir de son compte de messagerie personnel, copie et colle des informations sur les produits dans un tweet ou enregistre un rapport des ventes en cours sur son espace de stockage cloud public.

La **Protection des informations Windows** vous permet de vous protéger contre les fuites de données potentielles sans interférer avec l’expérience des employés. Il permet également de protéger les données et les applications d’entreprise contre des fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés amènent sur leur lieu de travail, sans que cela entraîne nécessairement une modification de votre environnement ou d’autres applications.

Cette stratégie Intune gère la liste des applications protégées par la Protection des informations Windows, les emplacements de réseau d’entreprise, le niveau de protection et les paramètres de chiffrement.

>[!NOTE]
> Pour utiliser l’application Portail d’entreprise de Windows 10 avec la Protection des informations Windows, vous devez ajouter cette application sous le mode **Exempté** de la Protection des informations Windows. 

### <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus, consultez [Protéger vos données d’entreprise à l’aide de Protection des informations Windows](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
