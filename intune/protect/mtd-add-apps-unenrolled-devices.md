---
title: Ajouter les applications Mobile Threat Defense sur des appareils non inscrits
titleSuffix: Microsoft Intune
description: Ajoutez les applications Mobile Threat Defense sur des appareils non inscrits par les utilisateurs d’appareils.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
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
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794457"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Ajouter les applications Mobile Threat Defense sur des appareils non inscrits

Par défaut, lorsque vous utilisez des stratégies de protection d’applications Intune avec Mobile Threat Defense, Intune guide l’utilisateur final à installer sur son appareil toutes les applications requises pour activer les connexions avec les services appropriés, et à s’y connecter.

Les utilisateurs finaux ont besoin de Microsoft Authenticator (iOS) pour inscrire leur appareil et de Mobile Threat Defense (Android et iOS) pour recevoir des notifications lorsqu’une menace est identifiée sur leurs appareils mobiles et pour recevoir des conseils afin de contrer les menaces.

Si vous le souhaitez, vous pouvez utiliser Intune pour ajouter et déployer Microsoft Authenticator et les applications Mobile Threat Defense (MTD).

> [!NOTE] 
> Cet article s’applique à tous les partenaires Mobile Threat Defense qui prennent en charge des stratégies de protection d’applications : Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).
> 
> Pour les appareils non inscrits, vous **n’avez pas besoin d’une stratégie de configuration des applications iOS** qui configure l’application Mobile Threat Defense pour iOS que vous utilisez avec Intune. Il s’agit d’une différence clé par rapport aux appareils inscrits dans Intune. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Configurer Microsoft Authenticator pour iOS via Intune (facultatif)
Quand vous utilisez des stratégies de protection d’applications Intune avec Mobile Threat Defense, Intune guide l’utilisateur final dans la procédure d’installation, de connexion et d’inscription de son appareil auprès de Microsoft Authenticator (iOS).

Toutefois, si vous souhaitez mettre l’application à la disposition des utilisateurs finaux via le Portail d’entreprise Intune, consultez les instructions permettant d’[ajouter des applications de l’App Store iOS dans Microsoft Intune](../apps/store-apps-ios.md). Utilisez cette [URL de Microsoft Authenticator dans l’App Store iOS](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) à la fin de la section **Configurer les informations sur l’application**. N’oubliez pas d’[attribuer l’application à des groupes avec Intune](../apps/apps-deploy.md) comme dernière étape.

> [!NOTE] 
> Pour les appareils iOS, vous avez besoin de [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) pour que l’identité des utilisateurs puisse être vérifiée par Azure AD. Le Portail d’entreprise Intune fonctionne en tant que service broker sur les appareils Android, pour que l’identité des utilisateurs puisse être vérifiée par Azure AD.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Proposer les applications Mobile Threat Defense via Intune (facultatif)
Quand vous utilisez des stratégies de protection d’applications Intune avec Mobile Threat Defense, Intune guide l’utilisateur final dans la procédure d’installation et de connexion à l’application cliente Mobile Threat Defense requise. 

Toutefois, si vous souhaitez mettre l’application à la disposition des utilisateurs finaux via le Portail d’entreprise Intune, vous pouvez suivre les étapes ci-dessous dans le [Portail Azure](https://portal.azure.com/). Vérifiez que vous êtes familiarisé avec ce processus :

- [Ajout d’une application dans Intune](../apps/apps-add.md).
- [Affectation d’une application avec Intune](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Mettre Lookout for Work à la disposition des utilisateurs finaux
- **Android**  
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](../apps/store-apps-android.md). Utilisez cette [URL de Lookout for Work dans le Play Store](https://play.google.com/store/apps/details?id=com.lookout.enterprise) à la fin de la section **Configurer les informations sur l’application**.

- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](../apps/store-apps-ios.md). Utilisez cette [URL de Lookout for Work dans l’App Store iOS](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) à la fin de la section **Configurer les informations sur l’application**.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>Mettre Zimperium à la disposition des utilisateurs finaux
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store iOS à Microsoft Intune](../apps/store-apps-ios.md). Utilisez cette [URL de Zimperium dans l’App Store](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) à la fin de la section **Configurer les informations sur l’application**.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Mettre Better Mobile à la disposition des utilisateurs finaux 
- **Android**
  - Consultez les instructions relatives à [l’ajout d’applications de l’App Store Android à Microsoft Intune](../apps/store-apps-android.md). Utilisez cette [URL d’Active Shield dans le Play Store](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) à la fin de la section **Configurer les informations sur l’application**.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>Étapes suivantes  

- [Activer le connecteur Mobile Threat Defense dans Intune pour les appareils non inscrits](~/protect/mtd-enable-unenrolled-devices.md)

