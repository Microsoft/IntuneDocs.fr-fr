---
title: Paramètres de Protection des informations Windows dans Microsoft Intune
titleSuffix: ''
description: Découvrez les paramètres Microsoft Intune que vous pouvez utiliser pour gérer la Protection des informations Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e1505c48d8605f2ac53b0d93ca933137fac981e3
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179216"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Guide pratique pour configurer la Protection des informations Windows dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Avec l’augmentation du nombre d’appareils appartenant aux employés au sein de l’entreprise, il existe un risque accru de fuites accidentelles de données via les applications et les services, tels que le courrier électronique, les réseaux sociaux et le cloud public, qui sont en dehors du contrôle de l’entreprise. Par exemple, lorsqu’un employé envoie les dernières photos de conception à partir de son compte de messagerie personnel, copie et colle des informations sur les produits dans un tweet ou enregistre un rapport des ventes en cours sur son espace de stockage cloud public.

La **Protection des informations Windows** vous permet de vous protéger contre les fuites de données potentielles sans interférer avec l’expérience des employés. Il permet également de protéger les données et les applications d’entreprise contre des fuites accidentelles de données sur les appareils d’entreprise et les appareils personnels que les employés amènent sur leur lieu de travail, sans que cela entraîne nécessairement une modification de votre environnement ou d’autres applications.

Cette stratégie Intune gère la liste des applications protégées par la Protection des informations Windows, les emplacements de réseau d’entreprise, le niveau de protection et les paramètres de chiffrement.

>[!NOTE]
> Pour utiliser l’application Portail d’entreprise de Windows 10 avec la Protection des informations Windows, vous devez ajouter cette application sous le mode **Exempté** de la Protection des informations Windows. 

### <a name="next-steps"></a>Étapes suivantes
Pour plus d'informations, voir :
-  [Protéger vos données d’entreprise à l’aide de la Protection des informations Windows](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
- [Créer une stratégie Protection des informations Windows (WIP) à l’aide de la console classique pour Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Créer une stratégie Protection des informations Windows (WIP) avec GPM à l’aide du portail Azure pour Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Créer une stratégie Protection des informations Windows (WIP) avec GAM à l’aide du portail Azure pour Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
