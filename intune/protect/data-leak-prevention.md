---
title: Éviter les fuites de données sur les appareils non gérés
titleSuffix: Microsoft Intune
description: Autorisez l’accès aux données d’entreprise sur les appareils et évitez les fuites de données à l’aide de Microsoft Intune.
keywords: protection des données éviter les fuites appareil O365 Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3affffdf69445ced667d718587303a5409423bf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502397"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>Éviter les fuites de données sur les appareils non gérés à l’aide de Microsoft Intune

Si vous autorisez l’accès aux données d’entreprise hébergées par Office 365, vous pouvez contrôler la façon dont les utilisateurs partagent et enregistrent des données sans risquer des fuites de données accidentelles ou intentionnelles. Microsoft Intune fournit des stratégies de protection des applications que vous définissez pour sécuriser les données d’entreprise sur les appareils appartenant à l’utilisateur. Vous n’avez pas à inscrire les appareils auprès du service Intune. 

Les stratégies de protection des applications configurées avec Intune fonctionnent également sur des appareils gérés avec une solution de gestion d’appareils non-Microsoft. Les données personnelles stockées sur les appareils ne sont pas affectées ; seules les données d’entreprise sont gérées par le service informatique. 

Vous pouvez définir des stratégies de protection des applications pour les applications mobiles Office sur les appareils exécutant Windows, iOS ou Android pour protéger les données d’entreprise. Ces stratégies vous permettent de définir des stratégies, telles que le code PIN basé sur une application ou le chiffrement des données d’entreprise, ou des paramètres plus avancés pour limiter la façon dont les options Couper, Copier, Coller et Enregistrer sous sont employées par les utilisateurs entre les applications gérées et non gérées. Vous pouvez également réinitialiser à distance les données d’entreprise sans obliger les utilisateurs à inscrire des appareils.

Les stratégies de protection des applications Intune sont indépendantes de la gestion des appareils. Les stratégies de protection des applications vous permettent de gérer les applications mobiles Office à la fois sur les appareils non gérés et gérés par Intune, ainsi que les appareils gérés par les solutions MDM non-Microsoft.

## <a name="before-you-begin"></a>Avant de commencer

Le plan d’action suivant peut être utilisé quand les conditions suivantes sont remplies :

* Votre entreprise est prête à passer en toute sécurité au cloud.
* Votre entreprise utilise Office 365 Exchange Online, SharePoint Online, OneDrive Entreprise ou Yammer.
* Votre entreprise compte des licences pour Microsoft 365, EMS (Enterprise Mobility + Security) ou Azure Information Protection.
* Votre entreprise permet aux utilisateurs d’accéder à ses données à partir d’appareils Android, iOS ou Windows de l’entreprise ou personnels.
* Votre entreprise ne souhaite pas exiger l’inscription des appareils personnels dans un service de gestion des appareils.

## <a name="action-plan"></a>Plan d’action

Pour les appareils iOS et Android :

1. Découvrez le fonctionnement des [stratégies de protection des applications](../apps/app-protection-policy.md).
2. Découvrez comment [créer et déployer des stratégies de protection des applications](../apps/app-protection-policies.md) pour les applications mobiles Office.
3. [Surveillez les stratégies de protection des applications](../apps/app-protection-policies-monitor.md) que vous créez et déployez.

Pour les appareils Windows 10 :

1. Découvrez le fonctionnement de la [Protection des informations Windows (WIP)](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip).
2. Préparez-vous à configurer des [stratégies de protection des applications pour Windows 10](../apps/app-protection-policies-configure-windows-10.md).
3. [Créez et déployez des stratégies de protection des applications WIP avec Intune](../apps/windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>Que dire à vos employés et étudiants

Si nécessaire, partagez les liens suivants pour fournir des informations supplémentaires :

* [Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-ios.md)
* [Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](../fundamentals/end-user-mam-apps-android.md)

## <a name="next-steps"></a>Étapes suivantes

Vous souhaitez obtenir de l’aide sur l’activation de cette fonctionnalité ou sur d’autres scénarios EMS ou Office 365 ? Si vous disposez d’au moins 150 licences pour Microsoft 365, Enterprise Mobility + Security ou Azure Active Directory Premium, utilisez vos [avantages FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program).
