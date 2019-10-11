---
title: Créer des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou configurez un profil de configuration d’appareil dans Microsoft Intune. Sélectionnez le type de plateforme, configurez les paramètres, ajoutez une balise d’étendue.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0858eefede678615e5b856fa0e40e48a791e4cce
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724098"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Créer un profil d’appareil dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Les profils d’appareil vous permettent d’ajouter et configurer des paramètres, puis de transmettre ces paramètres aux appareils de votre organisation. [Appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide des profils d’appareil dans Microsoft Intune](device-profiles.md) fournit des informations plus détaillées, y compris sur ce que vous pouvez faire.

Cet article :

- Répertorie les étapes pour créer un profil.
- Vous montre comment ajouter une balise d’étendue pour « filtrer » le profil.
- Décrit les règles de mise en application sur les appareils Windows 10 et vous montre comment créer une règle.
- Répertorie les durées de cycle d’actualisation d’archivage lorsque des appareils reçoivent des profils et des mises à jour du profil.

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Sélectionnez **Configuration de l’appareil**. Les options suivantes sont disponibles :

    - **Vue d’ensemble** : liste l’état de vos profils et fournit des détails supplémentaires sur les profils que vous avez affectés aux utilisateurs et aux appareils.
    - **Gérer** : créez des profils d’appareil, chargez des [scripts PowerShell](../apps/intune-management-extension.md) personnalisés à exécuter dans le profil, et ajoutez des forfaits de données aux appareils via [eSIM](esim-device-configuration.md).
    - **Surveiller** : vérifiez l’état d’un profil (réussite ou échec), et consultez les journaux de vos profils.
    - **Configurer** : ajoutez une autorité de certification (SCEP ou PFX), ou activez la [Gestion des dépenses de télécommunications](telecom-expenses-monitor.md) dans le profil.

3. Sélectionnez **Profils** > **Créer un profil**. Entrez les propriétés suivantes :

   - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil approprié est **Profil de messagerie WP pour toute l’entreprise**.
   - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
   - **Plateforme** : Choisissez la plateforme de vos appareils. Les options disponibles sont les suivantes :  

       - **Android**
       - **Android Entreprise**
       - **iOS/iPadOS**
       - **MacOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 et versions ultérieures**
       - **Windows 10 et versions ultérieures**

   - **Type de profil** : Sélectionnez le type des paramètres à créer. La liste affichée dépend de la **plateforme** choisie.
   - **Paramètres** : Les articles suivants décrivent les paramètres pour chaque type de profil :

       - [Modèles d’administration](administrative-templates-windows.md)
       - [Personnalisé](../custom-settings-configure.md)
       - [Optimisation de la distribution](../delivery-optimization-windows.md)
       - [Fonctionnalités de l’appareil](../device-features-configure.md)
       - [Restrictions relatives aux appareils](device-restrictions-configure.md)
       - [Mise à niveau de l’édition et changement de mode](edition-upgrade-configure-windows-10.md)
       - [Éducation](education-settings-configure.md)
       - [Courrier électronique](email-settings-configure.md)
       - [Endpoint Protection](../protect/endpoint-protection-configure.md)
       - [Identity protection](../protect/identity-protection-configure.md)  
       - [Kiosque](kiosk-settings.md)
       - [Certificat PKCS](../protect/certficates-pfx-configure.md)
       - [Certificat SCEP](../protect/certificates-scep-configure.md)
       - [Certificat approuvé](../protect/certificates-configure.md)
       - [Stratégies de mise à jour](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](../protect/advanced-threat-protection.md)
       - [Protection des informations Windows](../protect/windows-information-protection-configure.md)

     Par exemple, si vous sélectionnez **iOS/iPadOS** pour la plateforme, les options de type de votre profil ressemblent au profil suivant :

     ![Créer un profil iOS dans Intune](./media/device-profile-create/create-device-profile.png)

4. Une fois que vous avez fini, sélectionnez **OK** >  **Créer** pour enregistrer vos changements. Le profil est créé et apparaît dans la liste.

## <a name="scope-tags"></a>Balises d'étendue

Après avoir ajouté les paramètres, vous pouvez également ajouter une balise d’étendue au profil. Les balises d’étendue affectent et filtrent les stratégies à des groupes spécifiques, tels que les ressources humaines ou tous les employés US-NC.

Pour plus d’informations sur les balises d’étendue, et sur ce que vous pouvez faire, consultez [Use RBAC and scope tags for distributed IT](../fundamentals/scope-tags.md) (Utiliser RBAC et les balises d’étendue pour l’informatique distribuée).

### <a name="add-a-scope-tag"></a>Ajouter une balise d’étendue

1. Sélectionnez **Étendue (balises)** .
2. Sélectionnez **Ajouter** pour créer une balise d’étendue. Ou bien sélectionnez une balise d’étendue existante dans la liste.
3. Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="applicability-rules"></a>Règles de mise en application

S’applique à :

- Windows 10 et versions ultérieures

Les règles de mise en application permettent aux administrateurs de cibler des appareils dans un groupe qui répondent à des critères spécifiques. Par exemple, vous créez un profil de restriction d’appareil qui s’applique au groupe **Tous les appareils Windows 10**. De plus, vous souhaitez uniquement attribuer le profil aux appareils exécutant Windows 10 Entreprise.

Pour effectuer cette tâche, créez une **règle de mise en application**. Ces règles sont utiles pour les scénarios suivants :

- Vous utilisez Windows 10 Éducation (EDU). À Bellows College, vous souhaitez cibler tous les appareils Windows 10 EDU entre RS3 et RS4.
- Vous souhaitez cibler tous les utilisateurs dans les Ressources humaines de Contoso, mais uniquement les appareils Windows 10 Professionnel or Entreprise.

Pour aborder ces scénarios, vous devez faire ce qui suit :

- Créez un groupe d’appareils qui comprend tous les appareils à Bellows College. Dans le profil, ajoutez une règle de mise en application pour qu’elle s’applique si la version minimale du système d’exploitation est `16299` et la version maximale est `17134`. Attribuez ce profil au groupe d’appareils de Bellows College.

  Lorsqu’il est attribué, le profil s’applique aux appareils compris entre les versions minimale et maximale que vous entrez. Pour les appareils qui ne sont pas compris entre les versions minimale et maximale que vous entrez, leur état indique **Non applicable**.

- Créez un groupe d’utilisateurs qui comprend tous les utilisateurs des Ressources humaines (RH) chez Contoso. Dans le profil, ajoutez une règle de mise en application pour qu’elle s’applique aux appareils exécutant Windows 10 Professionnel ou Entreprise. Attribuez ce profil au groupe d’utilisateurs RH.

  Lorsqu’il est attribué, le profil s’applique aux appareils exécutant Windows 10 Professionnel ou Entreprise. Pour les appareils qui n’exécutent pas ces éditions, leur état indique **Non applicable**.

- Si deux profils possèdent exactement les mêmes paramètres, alors le profil sans règle de mise en application est appliqué. 

  Par exemple, ProfilA cible le groupe d’appareils Windows 10, active BitLocker et n’a pas de règle de mise en application. ProfileB cible le même groupe d’appareils Windows 10, active BitLocker et dispose d’une règle de mise en application pour appliquer uniquement le profil à Windows 10 Entreprise.

  Lorsque les deux profils sont attribués, ProfilA est appliqué, car il n’a pas de règle de mise en application. 

Lorsque vous attribuez le profil aux groupes, les règles de mise en application agissent comme un filtre et ciblent uniquement les appareils qui répondent à vos critères.

### <a name="add-a-rule"></a>Ajouter une règle

1. Sélectionnez **Règles de mise en application**. Vous pouvez choisir la **Règle**, la **Propriété** et **l’édition du système d’exploitation** :

    ![Ajouter une règle de mise en application à un profil de configuration d’appareil dans Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. Dans **Règle**, choisissez si vous souhaitez inclure ou exclure des utilisateurs ou des groupes. Les options disponibles sont les suivantes :

    - **Attribuer le profil si** : Inclut les utilisateurs ou les groupes qui répondent aux critères que vous entrez.
    - **Ne pas attribuer le profil si** : Exclut les utilisateurs ou les groupes qui répondent aux critères que vous entrez.

3. Dans **Propriété**, choisissez votre filtre. Les options disponibles sont les suivantes : 

    - **Édition du système d’exploitation** : Dans la liste, cochez les éditions de Windows 10 que vous souhaitez inclure (ou exclure) dans votre règle.
    - **Version du système d’exploitation** : Entrez les numéros **min** et **max** de la version Windows 10 à inclure (ou exclure) dans votre règle. Les deux valeurs sont obligatoires.

      Par exemple, vous pouvez entrer `10.0.16299.0` (RS3 ou 1709) pour la version minimale et `10.0.17134.0` (RS4 ou 1803) pour la version maximale. Ou bien, vous pouvez être plus granulaire et entrer `10.0.16299.001` pour la version minimale et `10.0.17134.319` pour la version maximale.

4. Sélectionnez **Ajouter** pour enregistrer vos changements.

## <a name="refresh-cycle-times"></a>Durées de cycle d’actualisation

Intune utilise différents cycles d’actualisation pour rechercher les mises à jour des profils de configuration. Si l’appareil vient d’être inscrit, la fréquence d’archivage est plus élevée. [Cycles d’actualisation de la stratégie et du profil](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) répertorie les temps d’actualisation estimés.

Les utilisateurs peuvent ouvrir l’application Portail d’entreprise et synchroniser l’appareil à tout moment pour rechercher immédiatement les mises à jour de profil.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](../device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
