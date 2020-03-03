---
title: Configurer Microsoft Intune
description: Configuration requise et conditions préalables avant de commencer à utiliser votre abonnement Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b12781c55abc3ce7d9e964b0f139fc4c1d1fd69b
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529360"
---
# <a name="set-up-intune"></a>Configurer Intune

Ces étapes de configuration vous permettent d’activer la gestion des appareils mobiles à l’aide d’Intune. Les appareils doivent être gérés pour que les utilisateurs puissent avoir accès aux ressources d’entreprise ou pour gérer les paramètres sur ces appareils.

Certaines étapes, comme la configuration d’un abonnement Intune et la définition de l’autorité de gestion des appareils mobiles, sont nécessaires dans la plupart des scénarios. D’autres étapes, comme la configuration d’un domaine personnalisé ou l’ajout d’applications, sont facultatives selon les besoins de votre entreprise.

Si vous utilisez actuellement Microsoft Endpoint Configuration Manager pour gérer vos ordinateurs et serveurs, vous pouvez [attacher Configuration Manager au cloud grâce à la cogestion](https://docs.microsoft.com/configmgr/comanage/overview).

>[!TIP]
>Si vous achetez au moins 150 licences pour Intune dans le cadre d’un plan éligible, vous pouvez utiliser *l’offre du Centre FastTrack*. Avec ce service, les spécialistes Microsoft vous accompagnent dans la préparation de votre environnement pour Intune. Consultez la section [Offre Enterprise Mobility + Security (EMS) du Centre FastTrack](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).

| Étapes | État  |
|---|---|
|   1   | [Configurations prises en charge](supported-devices-browsers.md) : informations à connaître avant de commencer. Cela inclut les configurations prises en charge et les spécifications réseau.|
|   2   |  [Se connecter à Intune](account-sign-up.md) : Connectez-vous à votre abonnement d’évaluation ou créez un abonnement Intune. |
|   3   | [Configurer le nom de domaine](custom-domain-name-configure.md) : Définissez l’inscription DNS pour connecter le nom de domaine de votre entreprise à Intune. Les utilisateurs ont alors accès à un domaine qu’ils connaissent quand ils se connectent à Intune et qu’ils utilisent des ressources. |
|   4   | [Ajouter des utilisateurs](users-add.md) et des [groupes](../groups-add.md) : Ajoutez des utilisateurs ou connectez-vous à Active Directory pour synchroniser avec Intune. Obligatoire, sauf si vos appareils sont des appareils kiosque « sans utilisateur », par exemple. Les groupes sont utilisés pour attribuer des applications, des paramètres et d’autres ressources.|
|   5   | [Attribuer des licences](../licenses-assign.md) : Autorisez les utilisateurs à utiliser Intune. Chaque utilisateur ou appareil sans utilisateur nécessite une licence Intune pour accéder au service. |
|   6   | [Définir l’autorité MDM](../mdm-authority-set.md) : Utilisez des groupes d’utilisateurs et d’appareils pour simplifier les tâches de gestion. Les groupes sont utilisés pour attribuer des applications, des paramètres et d’autres ressources. |
|   7   | [Ajouter des applications](../apps/apps-add.md) : Les applications peuvent être attribuées à des groupes et installées de manière automatique ou facultative. |
|   8   | [Configurer des appareils](../configuration/device-profiles.md) : Configurez des profils pour gérer les paramètres d’appareil. Les profils d’appareil peuvent préconfigurer des paramètres pour la messagerie, le VPN, le Wi-Fi et des fonctionnalités de l’appareil. Ils peuvent également restreindre les appareils pour vous aider à protéger aussi bien les données que les appareils. |
|   9   |  [Personnaliser le portail d’entreprise](../apps/company-portal-app.md) : Personnalisez le portail d’entreprise Intune dont se servent les utilisateurs pour inscrire des appareils et installer des applications. Ces paramètres s’affichent dans l’application Portail d’entreprise et le site web du portail d’entreprise Intune.       |
|  10   | [Activer l’inscription d’appareil](mdm-authority-set.md) : Activez la gestion Intune des appareils iOS/iPadOS, Windows, Android et Mac en définissant l’autorité MDM et en activant des plateformes spécifiques. |
|  11   |  [Configurer des stratégies d’application](../apps/app-protection-policy.md) : Indiquez des paramètres spécifiques en fonction des stratégies de protection des applications dans Microsoft Intune. |
