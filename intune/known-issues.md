---
title: Problèmes connus dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez les problèmes connus affectant Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 421eea460ee7c00b79a63a014291a8abb88ddaea
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347795"
---
# <a name="known-issues-in-microsoft-intune"></a>Problèmes connus dans Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilisez cet article pour connaître les problèmes connus dans Microsoft Intune.

Si vous souhaitez signaler un bogue qui n’est pas répertorié ici, [créez une demande de support](get-support.md).

Si vous souhaitez voir une nouvelle fonctionnalité dans Intune, envoyez un rapport sur le site [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="migration"></a>Migration

### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal"></a>Exporter des stratégies de conformité du portail Azure Classic pour recréer ces stratégies dans le portail Azure Intune

Les stratégies de conformité créées dans le portail Azure Classic seront dépréciées. Vous pouvez examiner et supprimer des stratégies de conformité existantes, mais vous ne pouvez pas les mettre à jour. Si vous avez besoin migrer des stratégies de conformité vers le portail Azure Intune actuel, vous pouvez exporter les stratégies sous forme de fichier avec la virgule comme séparateur (fichier .csv). Ensuite, utilisez les informations détaillées du fichier pour recréer ces stratégies dans le portail Azure Intune.

> [!IMPORTANT]
> Une fois le portail Azure Classic mis hors service, vous ne pourrez plus accéder à ou afficher vos stratégies de conformité. Veillez donc à exporter et à recréer vos stratégies dans le portail Azure avant la mise hors service du portail Azure Classic.

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Les fonctionnalités du client PC hérité Intune sont uniquement disponibles dans la console Silverlight

La capacité à gérer Windows 10 dans Intune sur le portail Azure est disponible par le biais de l’inscription MDM Windows. Pour plus d’informations, consultez [Intune dans la console Azure et PC client Intune hérité](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Les groupes créés par Intune pendant la migration peuvent affecter les fonctionnalités d’autres produits Microsoft

Lorsque vous migrez depuis Intune vers le portail Azure, un nouveau groupe nommé **Tous les utilisateurs - b0b08746-4dbe-4a37-9adf-9e7652c0b421** peut s’afficher. Ce groupe contient tous les utilisateurs dans votre Azure Active Directory, pas seulement les utilisateurs Intune sous licence. Cette utilisation peut entraîner des problèmes avec d’autres produits Microsoft si vous prévoyez que certains utilisateurs existants ou nouveaux ne soient membres d’aucun groupe.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Les panneaux d’état pour les stratégies migrées ne fonctionnent pas

Vous ne pouvez pas voir les informations d’état des stratégies qui ont été migrées à partir du portail classique Azure dans le portail Azure. Toutefois, vous pouvez continuer à afficher des rapports pour ces stratégies dans le portail classique. Pour afficher les informations d’état pour les stratégies de configuration migrées, recréez-les dans le portail Azure.

## <a name="apps"></a>Applications


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>Affichage de plusieurs invites d’installation pour certaines applications VPP
Il est possible que vous receviez plusieurs invites d’installation pour certaines applications VPP déjà installées sur les appareils d’utilisateurs finaux. Ce problème se produit si l’option **Mises à jour automatiques des applications** est **activée** pour le jeton VPP que vous avez chargé sur Intune dans le portail Azure.    

Pour contourner ce problème, vous pouvez désactiver l’option **Mises à jour automatiques des applications** pour le jeton VPP. Pour cela, dans le portail Azure, ouvrez Microsoft Intune. Dans Intune, sélectionnez **Applications clientes** > **Jetons VPP iOS**. Ensuite, sélectionnez le jeton VPP qui a déployé l’application concernée et sélectionnez **Modifier** > **Mises à jour automatiques des applications** > **Désactivé** > **Enregistrer**. Vous pouvez également arrêter le déploiement de l’application concernée comme application VPP, ce qui entraîne l’arrêt des invites.    

Il s’agit d’un problème connu dans la version actuelle. Un correctif sera bientôt publié pour résoudre ce problème. Une fois ce correctif implémenté, vos utilisateurs ne recevront plus plusieurs invites leur demandant d’installer une application.

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Applications iOS achetées en volume disponibles uniquement dans la langue du client Intune par défaut
Les applications iOS achetées en volume sont affichées et peuvent être affectées uniquement pour le même code de pays/région que votre compte Intune. Intune synchronise uniquement les applications ayant les mêmes paramètres régionaux iTunes que le code de pays/région du compte de client Intune. Par exemple, si vous achetez une application disponible uniquement dans un Store américain alors que votre compte Intune est allemand, Intune n’affiche pas cette application.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Plusieurs copies du même programme d’achat en volume iOS sont chargées
Ne cliquez pas à plusieurs reprises sur le bouton **Charger** pour le même jeton VPP, sinon des jetons VPP en double seraient chargés et les applications seraient synchronisées plusieurs fois pour le même jeton VPP.

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>Une partie du trafic Managed Browser n’est pas routée par le biais du proxy d’application Azure <!-- 2463492 -->
Il existe un problème connu lié à l’intégration de Managed Browser et du proxy d’application selon lequel du trafic tertiaire (tel que des appels javascript ou AJAX) n’est pas routé par le biais du proxy d’application Azure. Il s’agit d’un problème connu dans la version actuelle.  

<!-- ## Groups -->

## <a name="device-configuration"></a>Configuration des appareils

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Vous ne pouvez pas enregistrer une stratégie de protection des informations Windows pour certains appareils

Pour les appareils non inscrits avec Intune, vous pouvez spécifier un seul domaine principal dans le champ **Identité d’entreprise** dans les paramètres d’une stratégie de protection des informations Windows.
Si vous ajoutez des domaines supplémentaires (dans **Paramètres avancés** > **Réseau de périmètre** > **Ajouter un domaine protégé**), vous ne pouvez pas enregistrer la stratégie. Le message d’erreur affiché sera prochainement modifié pour être plus précis.

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Prise en charge des clients VPN Cisco AnyConnect et Cisco Legacy AnyConnect - iOS

Sur les appareils iOS, l’intégration du contrôle d’accès réseau ne fonctionne pas avec le nouveau client Cisco AnyConnect. Nous travaillons avec Cisco pour parvenir à une intégration du contrôle d’accès réseau.

La rubrique [Créer des profils VPN dans Intune](vpn-settings-ios.md) fournit plus de détails sur les clients Cisco AnyConnect et Cisco Legacy AnyConnect.

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Utilisation du type de mot de passe numérique avec les appareils macOS Sierra

Actuellement, si vous sélectionnez le **type de mot de passe requis** **numérique** dans un profil de restriction d’appareil pour des appareils macOS Sierra, il est appliqué en tant que valeur **Alphanumérique**. Si vous souhaitez utiliser un mot de passe numérique avec ces appareils, ne configurez pas ce paramètre.
Ce problème sera peut-être corrigé dans une future version de macOS.

Pour plus d’informations sur ces paramètres, consultez [Paramètres de restriction des appareils macOS dans Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Compatibilité

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Les stratégies de conformité d’Intune ne s’affichent pas dans la nouvelle console

Les stratégies de conformité créées dans le portail classique sont migrées, mais ne s’affichent pas dans le portail Azure en raison de changements de conception dans le portail Azure. Les stratégies de conformité créées dans le portail classique Intune sont toujours appliquées, mais vous devez les consulter et les modifier dans le portail classique.

En outre, les nouvelles stratégies de conformité que vous créez dans le portail Azure ne sont pas visibles dans le portail classique.

Pour plus d’informations, consultez [Qu’est-ce que la compatibilité des appareils ?](device-compliance.md).

<!-- ## Enrollment -->


## <a name="data-protection"></a>Protection des données

### <a name="ios-app-protection-policies"></a>Stratégies de protection des applications iOS

Vous pouvez définir des [stratégies de protection des applications pour iOS](app-protection-policy-settings-ios.md). Ces stratégies sont proposées aux utilisateurs d’appareils gérés par l’intermédiaire de la gestion des applications mobiles (GAM) sans inscription. En raison d’une erreur temporaire, vous pouvez uniquement définir ces stratégies pour les versions d’iOS à une seule décimale. Ainsi, au lieu de définir iOS 10.3.1 comme version minimale, définissez iOS 10.3. Ce problème sera résolu dans une prochaine mise à jour du SDK iOS.


## <a name="administration-and-accounts"></a>Administration et comptes

Les administrateurs globaux (également appelés administrateurs de clients) peuvent continuer à effectuer des tâches d’administration quotidiennes sans licence Intune ou Enterprise Mobility Suite (EMS) distincte. Toutefois, pour utiliser le service, par exemple pour inscrire leur propre appareil ou un appareil d’entreprise, ou pour utiliser le portail d’entreprise Intune, ils doivent avoir une licence Intune ou EMS.

<!-- ## Additional items -->
