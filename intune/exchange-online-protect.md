---
title: Exchange sans gestion des appareils
titleSuffix: Microsoft Intune
description: Utilisez Microsoft Intune pour accorder aux employés l’accès à leur messagerie Office 365 Exchange Online sans configurer de système de gestion des appareils.
keywords: Accès à l’e-mail Exchange Office 365
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2017
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: e82942148b65b3dce67e640c6e10fa3fbb234295
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179794"
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Protéger Office 365 Exchange Online sans avoir besoin de la gestion des appareils

Si vous voulez permettre aux employés d’accéder à leurs e-mails professionnels sans subir la surcharge que représente la configuration d’un système de gestion des appareils, c’est possible. Vous pouvez accorder un accès à Office 365 Exchange Online via Intune. Pour effectuer les étapes nécessaires, veillez à disposer de licences pour Microsoft 365 ou Azure Active Directory (Premium) et Intune. Les employés doivent avoir un [appareil iOS ou Android pris en charge](supported-devices-browsers.md). 

Si vous décidez de configurer un système de gestion des appareils, c’est possible. Ce type de protection des applications fonctionne indépendamment de la gestion des appareils. 

## <a name="action-plan"></a>Plan d’action

1. [Informez-vous sur l’accès conditionnel](conditional-access.md). 
2. [Informez-vous sur l’accès conditionnel basé sur l’application](app-based-conditional-access-intune.md).
3. [Configurez les stratégies d’accès conditionnel basé sur l’application pour Exchange Online](app-based-conditional-access-intune-create.md).
4. [Bloquez les applications qui ne peuvent pas être gérées](app-modern-authentication-block.md), en particulier celles qui n’utilisent pas Azure Active Directory Authentication Library (ADAL).
5. (Facultatif) [Configurez des stratégies d’accès conditionnel basé sur l’application pour SharePoint Online](app-based-conditional-access-intune-create.md). Ces stratégies bloquent l’accès à vos données d’entreprise provenant d’applications qui ne peuvent pas être gérées et sécurisées. Les stratégies limitent également l’accès via SharePoint Mobile. 

## <a name="what-to-tell-employees-and-students"></a>Que dire à vos employés et étudiants

* Demandez à vos employés et étudiants de télécharger et d’installer Microsoft Outlook ou Microsoft SharePoint pour iOS à partir de l’App Store d’Apple ou pour Android à partir de Google Play Store. 
* Si vous bloquez l’accès aux applications qui n’utilisent pas l’authentification moderne, informez les employés et les étudiants de cette restriction. 

## <a name="next-steps"></a>Étapes suivantes

Vous avez utilisé l’accès conditionnel basé sur l’application pour renforcer la sécurité des données d’entreprise. Au cours des étapes suivantes, vous pouvez découvrir plus en détail les autres méthodes qui vous permettent de renforcer la protection des données de votre entreprise, notamment les suivantes : 

* Configuration de l’[accès conditionnel en fonction de la conformité des appareils, des risques que présente l’appareil, de l’emplacement et des attributs utilisateur dans Active Directory et Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).  
* Configuration de stratégies de protection des applications pour vous permettre de protéger vos données d’entreprise contre des fuites de données intentionnelles ou involontaires. 
* Exploitation d’Azure Information Protection pour protéger les données d’entreprise en dehors de votre réseau. 

Vous souhaitez obtenir de l’aide sur l’activation de cette fonctionnalité ou sur d’autres scénarios EMS ou Office 365 ? Si vous disposez d’au moins 150 licences pour Microsoft 365, Enterprise Mobility + Security ou Azure Active Directory Premium, utilisez vos [avantages FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 