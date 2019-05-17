---
title: Créer des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou configurez un profil de configuration d’appareil dans Microsoft Intune. Sélectionnez le type de plateforme, configurez les paramètres et ajoutez une balise d’étendue.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570401"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Créer un profil d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les profils d’appareil vous permettent d’ajouter et configurer des paramètres, puis de transmettre ces paramètres aux appareils de votre organisation. [Appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune](device-profiles.md) fournit des informations plus détaillées, y compris sur ce que vous pouvez faire.

Cet article :

- Répertorie les étapes pour créer un profil.
- Vous montre comment ajouter une balise d’étendue pour « filtrer » le profil.
- Répertorie les durées de cycle d’actualisation d’archivage lorsque des appareils reçoivent des profils et des mises à jour du profil.

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Intune**.

2. Sélectionnez **Configuration de l’appareil**. Les options suivantes sont disponibles :

    - **Vue d’ensemble** : liste l’état de vos profils et fournit des détails supplémentaires sur les profils que vous avez affectés aux utilisateurs et aux appareils.
    - **Gérer** : créez des profils d’appareil, chargez des [scripts PowerShell](intune-management-extension.md) personnalisés à exécuter dans le profil, et ajoutez des forfaits de données aux appareils via [eSIM](esim-device-configuration.md).
    - **Surveiller** : vérifiez l’état d’un profil (réussite ou échec), et consultez les journaux de vos profils.
    - **Configurer** : ajoutez une autorité de certification (SCEP ou PFX), ou activez la [Gestion des dépenses de télécommunications](telecom-expenses-monitor.md) dans le profil.

3. Sélectionnez **Profils** > **Créer un profil**. Entrez les propriétés suivantes :

   - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil approprié est **Profil de messagerie WP pour toute l’entreprise**.
   - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :  

       - **Android**
       - **Android Entreprise**
       - **iOS**
       - **MacOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 et versions ultérieures**
       - **Windows 10 et versions ultérieures**

   - **Type de profil** : Sélectionnez le type des paramètres à créer. La liste affichée dépend de la **plateforme** choisie.
   - **Paramètres** : Les articles suivants décrivent les paramètres pour chaque type de profil :

       - [Modèles d’administration](administrative-templates-windows.md)
       - [Personnalisé](custom-settings-configure.md)
       - [Optimisation de la distribution](delivery-optimization-windows.md)
       - [Fonctionnalités de l’appareil](device-features-configure.md)
       - [Restrictions relatives aux appareils](device-restrictions-configure.md)
       - [Mise à niveau de l’édition et changement de mode](edition-upgrade-configure-windows-10.md)
       - [Éducation](education-settings-configure.md)
       - [Courrier électronique](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Identity protection](identity-protection-configure.md)  
       - [Kiosque](kiosk-settings.md)
       - [Certificat PKCS](certficates-pfx-configure.md)
       - [Certificat SCEP](certificates-scep-configure.md)
       - [Certificat approuvé](certificates-configure.md)
       - [Stratégies de mise à jour](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Protection des informations Windows](windows-information-protection-configure.md)

     Par exemple, si vous sélectionnez **iOS** pour la plateforme, les options de type de votre profil ressemblent au profil suivant :

     ![Créer un profil iOS dans Intune](./media/create-device-profile.png)

4. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements. Le profil est créé et apparaît dans la liste.

## <a name="scope-tags"></a>Balises d'étendue

Après avoir ajouté les paramètres, vous pouvez également ajouter une balise d’étendue au profil. Les balises d’étendue affectent et filtrent les stratégies à des groupes spécifiques, tels que les ressources humaines ou tous les employés US-NC.

Pour plus d’informations sur les balises d’étendue, et sur ce que vous pouvez faire, consultez [Use RBAC and scope tags for distributed IT](scope-tags.md) (Utiliser RBAC et les balises d’étendue pour l’informatique distribuée).

### <a name="add-a-scope-tag"></a>Ajouter une balise d’étendue

1. Sélectionnez **Étendue (balises)**.
2. Sélectionnez **Ajouter** pour créer une balise d’étendue. Ou bien sélectionnez une balise d’étendue existante dans la liste.
3. Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="refresh-cycle-times"></a>Durées de cycle d’actualisation

Intune utilise les cycles d’actualisation suivants pour rechercher les mises à jour des profils de configuration :

| Plate-forme | Cycle d’actualisation|
| --- | --- |
| iOS | Toutes les 6 heures |
| macOS | Toutes les 6 heures |
| Android | Toutes les 8 heures |
| PC Windows 10 inscrits en tant qu’appareils | Toutes les 8 heures |
| Windows Phone | Toutes les 8 heures |
| Windows 8.1 | Toutes les 8 heures |

Si l’appareil vient d’être inscrit, la fréquence d’archivage est plus élevée :

| Plate-forme | Fréquence |
| --- | --- |
| iOS | Toutes les 15 minutes pendant 6 heures, puis toutes les 6 heures |  
| macOS | Toutes les 15 minutes pendant 6 heures, puis toutes les 6 heures | 
| Android | Toutes les 3 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures | 
| PC Windows 10 inscrits en tant qu’appareils | Toutes les 3 minutes pendant 30 minutes, puis toutes les 8 heures | 
| Windows Phone | Toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures | 
| Windows 8.1 | Toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures | 

Les utilisateurs peuvent ouvrir l’application Portail d’entreprise et synchroniser l’appareil à tout moment pour rechercher immédiatement les mises à jour de profil.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
