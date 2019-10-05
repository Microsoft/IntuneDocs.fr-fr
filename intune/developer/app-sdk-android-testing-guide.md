---
title: Guide du SDK de l’application Microsoft Intune pour les tests développeurs Android
description: Le guide de test du SDK d’application Microsoft Intune pour Android vous permet de tester votre application Android gérée par Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1484567721283ddb91f3ecebbc448e7356ceaf5a
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830547"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Guide du SDK de l’application Microsoft Intune pour les tests développeurs Android

Le guide de test du SDK d’application Microsoft Intune pour Android a pour but de vous permettre de tester votre application Android gérée par Intune.  

## <a name="prerequisite-test-accounts"></a>Prérequis : comptes de test
Vous pouvez créer des comptes avec ou sans données prégénérées. Comment créer un compte :
1. Accédez au site [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant). 
2. [Configurez Intune](../fundamentals/setup-steps.md) pour activer la gestion des appareils mobiles.
3. [Créez des utilisateurs](../fundamentals/users-add.md).
4. [Créer des groupes](../fundamentals/groups-add.md).
5. [Attribuez les licences](../fundamentals/licenses-assign.md) à des fins de test.


## <a name="azure-portal-policy-configuration"></a>Configuration des stratégies dans le portail Azure
[Créez et affectez des stratégies de protection des applications](../apps/app-protection-policies.md) dans le [panneau Intune du portail Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Vous pouvez également créer et affecter votre [stratégie de configuration des applications](../apps/app-configuration-policies-overview.md) dans le panneau Intune.

> [!NOTE]
> Si votre application n’est pas listée dans le portail Azure, vous pouvez la cibler avec une stratégie en sélectionnant l’option **Autres applications** et en indiquant le nom du package dans la zone de texte.

## <a name="test-cases"></a>Cas de test

Les cas de test suivants fournissent des étapes de configuration et de validation. Utilisez ce guide pour résoudre les problèmes concernant les applications Android gérées par Intune.

### <a name="required-pin-and-corporate-credentials"></a>Exigence d’un code PIN et d’informations d’identification d’entreprise

Vous pouvez exiger que l’utilisateur fournisse un code PIN pour accéder aux ressources de l’entreprise. De plus, vous pouvez mettre en place un système d’authentification d’entreprise pour l’accès aux applications gérées. Effectuez les étapes suivantes pour configurer ces exigences :

1. Définissez les options **Exiger un code confidentiel d’accès** et **Exiger des informations d’identification d’entreprise pour l’accès** sur **Oui**. Pour plus d’informations, consultez [Paramètres de la stratégie de protection d’applications Android dans Microsoft Intune](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Confirmez les conditions suivantes :
    - Lors du lancement de l’application, vous êtes invité à entrer ou configurer un code PIN et/ou à entrer l’utilisateur de production qui a été indiqué lors de l’inscription dans le portail d’entreprise.
    - Si l’invite d’identification qui s’affiche n’est pas valide, cela peut être dû à une mauvaise configuration du manifeste Android, et plus particulièrement, des valeurs pour l’intégration ADAL (SkipBroker ClientID et Authority).
    - Si aucune invite ne s’affiche, cela peut être dû à une valeur `MAMActivity` mal intégrée. Pour plus d’informations sur `MAMActivity`, consultez [Guide du Kit SDK de l’application Microsoft Intune pour les développeurs Android](app-sdk-android.md).

> [!NOTE] 
> Si le test ci-dessus échoue, il est très probable que les tests qui suivent échouent également. Lisez les informations concernant l’intégration [SDK](app-sdk-android.md##sdk-integration) et [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Restreindre le transfert et la réception de données entre les applications
Vous pouvez contrôler les transferts de données entre les différentes applications d’entreprise gérées de la façon suivante :

1. Définissez l’option **Autoriser l’application à transférer des données vers d’autres applications** sur **Applications gérées par la stratégie**.
2. Définissez **Autoriser l’application à recevoir des données d’autres applications** sur la valeur **Toutes les applications**. L’utilisation des intentions et des fournisseurs de contenu sera impactée par ces stratégies.
3. Confirmez les conditions suivantes :
    - L’ouverture de votre application à partir d’une application non gérée fonctionne correctement.
    - Le partage de contenu entre applications gérées est autorisé.
    - Le partage entre les applications gérées et les applications non gérées (par exemple, Chrome) est bloqué.

### <a name="restrict-cut-copy-and-paste"></a>Restreindre les opérations de couper, copier et coller
Pour limiter le Presse-papiers du système aux applications gérées, effectuez les étapes suivantes :

1. Définissez l’option **Restreindre les opérations couper, copier et coller avec d’autres applications** sur **Applications gérées par une stratégie avec Coller dans**.
2. Confirmez les conditions suivantes :
    - La copie de texte provenant de votre application vers une application non gérée (par exemple, Messages) est bloquée.

### <a name="prevent-save-as"></a>Empêcher **Enregistrer sous**
Vous pouvez contrôler la fonctionnalité **Enregistrer sous** de la façon suivante :

1. Si votre application nécessite des [contrôles Enregistrer sous intégrés](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), définissez l’option **Interdire « Enregistrer sous »** sur **Oui**.
2. Confirmez les conditions suivantes :
    - L’enregistrement est limité aux emplacements gérés définis.

### <a name="file-encryption"></a>Chiffrement de fichier
Vous pouvez chiffrer les données des appareils de la façon suivante :

1. Définissez l’option **Chiffrer les données de l’application** sur **Oui**.
2. Confirmez les conditions suivantes :
    - Le comportement habituel de l’application n’est pas impacté.

### <a name="prevent-android-backups"></a>Empêcher les sauvegardes Android
Vous pouvez contrôler la sauvegarde des applications de la façon suivante :

1. Si vous avez défini des [restrictions de sauvegardes intégrées](app-sdk-android.md#protecting-backup-data), définissez l’option **Interdire les sauvegardes Android** sur **Oui**.
2. Confirmez les conditions suivantes :
    - Les sauvegardes sont limitées.

### <a name="unenrollment"></a>Désinscription
Pour réinitialiser à distance les applications gérées afin d’en supprimer les adresses e-mail et les documents d’entreprise, et pour déchiffrer les données personnelles lorsque celles-ci ne sont plus gérées, procédez de la façon suivante :

1. Dans le portail Azure, [démarrez un processus de réinitialisation](../apps/apps-selective-wipe.md).
2. Si votre application n’est pas inscrite à un gestionnaire de réinitialisation, vérifiez les conditions suivantes :
    - Une réinitialisation complète de l’application s’est produite.
3. Si votre application est inscrite à `WIPE_USER_DATA` ou `WIPE_USER_AUXILARY_DATA`, vérifiez les conditions suivantes :
    - Le contenu géré a été supprimé de l’application. Pour plus d’informations, consultez [Guide du Kit SDK de l’application Microsoft Intune pour les développeurs Android - Réinitialisation sélective](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Prise en charge de plusieurs identités
L’intégration d’une [prise en charge multi-identité](app-sdk-android.md#multi-identity-optional) présente des risques élevés et doit donc être rigoureusement testée. Les problèmes les plus courants sont dus à une configuration incorrecte de l’identité (contexte/niveau de menace) ainsi qu’aux fichiers de suivi (`MAMFileProtectionManager`).

Pour les scénarios multi-identités suivants, vous devez au minimum effectuer une revalidation :

- La stratégie **Enregistrer sous** fonctionne correctement pour les identités managées.
- Les restrictions de copier-coller sont appliquées correctement entre les applications gérées et les applications personnelles.
- Seules les données appartenant à l’identité managée sont chiffrées, et les fichiers personnels ne sont pas modifiés.
- Lors d’une désinscription, la réinitialisation sélective supprime uniquement les données des identités managées.
- L’utilisateur final est invité à effectuer un lancement conditionnel lorsqu’il passe d’un compte non géré à un compte géré (la première fois uniquement).

### <a name="app-configuration-optional"></a>Configuration de l’application (facultatif)
Vous pouvez configurer le comportement des applications gérées de la façon suivante :

1. Si votre application utilise des paramètres de configuration d’application, vous devez effectuer des tests pour vérifier que votre application peut gérer correctement toutes les valeurs que vous (en tant qu’administrateur) pouvez définir. Les [stratégies de configuration d’application](../apps/app-configuration-policies-overview.md) peuvent être créées et affectées dans Intune.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter une application métier Android à Microsoft Intune](../apps/lob-apps-android.md).
