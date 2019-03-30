---
title: Guide du SDK de l’application Microsoft Intune pour les tests développeurs Android
description: Le SDK d’application Microsoft Intune pour Android guide de test vous permet de tester votre application Android gérée par Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072469"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Guide du SDK de l’application Microsoft Intune pour les tests développeurs Android

Le SDK d’application Microsoft Intune pour Android guide de test est conçu pour vous aider à tester votre application Android gérée par Intune.  

## <a name="prerequisite-test-accounts"></a>Comptes de test requis
Nouveaux comptes peuvent être créés avec et sans données prégénérées. Comment créer un compte :
1. Accédez à la [Microsoft démos](https://demos.microsoft.com/environments/create/tenant) site. 
2. [Configurer Intune](https://docs.microsoft.com/intune/setup-steps) pour activer la gestion des appareils mobiles (MDM).
3. [Créer des utilisateurs](https://docs.microsoft.com/intune/users-add).
4. [Créer des groupes](https://docs.microsoft.com/intune/groups-add).
5. [Attribuer des licences](https://docs.microsoft.com/intune/licenses-assign) selon les besoins de vos tests.


## <a name="azure-portal-policy-configuration"></a>Configuration de la stratégie du portail Azure
[Créer et affecter des stratégies de protection d’application](https://docs.microsoft.com/intune/app-protection-policies) dans le [Intune panneau du portail Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Votre [stratégie de configuration d’application](https://docs.microsoft.com/intune/app-configuration-policies-overview) peut également être créée et attribuée dans le panneau Intune.

> [!NOTE]
> Si votre application n’est pas répertoriée dans le portail Azure, vous pouvez le cibler avec une stratégie en sélectionnant le **plus d’applications** option et en fournissant le nom de package dans la zone de texte.

> [!IMPORTANT]
> Pour une stratégie de configuration d’application à appliquer, l’utilisateur de l’inscription doit être ciblée par un [stratégie Intune app protection](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Cas de test

Les cas de test suivants fournissent des étapes de configuration et de confirmation. Utilisez ce guide pour aider à résoudre les problèmes d’application Android gérée par Intune.

### <a name="required-pin-and-corporate-credentials"></a>Code PIN exigé et les informations d’identification d’entreprise

Vous pouvez exiger un code confidentiel pour accéder aux ressources d’entreprise. En outre, vous pouvez appliquer l’authentification d’entreprise avant que les utilisateurs peuvent utiliser des applications gérées. Utilisez les étapes suivantes pour définir ces exigences :

1. Configurer **exiger le code PIN pour l’accès** et **exiger des informations d’identification d’entreprise pour l’accès** à **Oui**. Pour plus d’informations, consultez [Paramètres de la stratégie de protection d’applications Android dans Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Confirmez les conditions suivantes :
    - Lancement de l’application doit présenter une invite pour la broche d’entrée / d’installation et/ou de l’utilisateur de production qui a été utilisé lors de l’inscription avec le portail d’entreprise.
    - Échec de présentation d’une invite de connexion valide peut être en raison d’un manifeste android mal configuré, en particulier les valeurs pour l’intégration de la bibliothèque ADAL (SkipBroker ClientID et autorité).
    - Échec de présentation d’invite peut être dû à intégré de manière incorrecte `MAMActivity` valeur. Pour plus d’informations sur `MAMActivity`, consultez [Microsoft Intune App SDK for guide du développeur Android](app-sdk-android.md).

> [!NOTE] 
> Si le test ci-dessus ne fonctionne pas, les tests ci-dessous également échouera probablement. Révision [SDK](app-sdk-android.md##sdk-integration) et [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) intégration.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Limiter le transfert et de recevoir des données avec d’autres applications
Vous pouvez contrôler les transferts de données entre les applications d’entreprise gérées comme suit :

1. Définissez **autoriser l’application à transférer des données vers d’autres applications** à **applications gérées par la stratégie**.
2. Définissez **Autoriser l’application à recevoir des données d’autres applications** sur la valeur **Toutes les applications**. Utilisation des intentions et les fournisseurs de contenu est affectée par ces stratégies.
3. Confirmez les conditions suivantes :
    - Ouverture à partir d’une application non managée dans vos fonctions d’application correctement.
    - Partage de contenu entre des applications gérées est autorisé.
    - Partage des applications gérées pour les applications non gérées (par exemple, Chrome) est bloqué.

### <a name="restrict-cut-copy-and-paste"></a>Restreindre les opérations de couper, copier et coller
Vous pouvez restreindre le Presse-papiers du système pour les applications gérées comme suit :

1. Définissez **restreindre les opérations couper, copier et coller avec d’autres applications** à **gérées par la stratégie avec coller dans**.
2. Confirmez les conditions suivantes :
    - Une application non managée (par exemple, les Messages) copier du texte à partir de votre application vers un géré est bloquée.

### <a name="prevent-save-as"></a>Empêcher **Enregistrer sous**
Vous pouvez contrôler **enregistrer en tant que** fonctionnalité comme suit :

1. Si votre application nécessite [intégré contrôles 'enregistrer sous'](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), affectez la valeur **empêcher « Enregistrer sous »** à **Oui**.
2. Confirmez les conditions suivantes :
    - Enregistrer est limité aux seuls les emplacements managés appropriés.

### <a name="file-encryption"></a>Chiffrement de fichier
Vous pouvez chiffrer les données sur l’appareil comme suit :

1. Définissez **chiffrer les données d’application** à **Oui**.
2. Confirmez les conditions suivantes :
    - Comportement d’application normal n’est pas affectée.

### <a name="prevent-android-backups"></a>Empêcher les sauvegardes Android
Vous pouvez contrôler sauvegarde d’une application comme suit :

1. Si vous avez défini [intégré des restrictions liées aux sauvegardes](app-sdk-android.md#protecting-backup-data), configurer **interdire les sauvegardes Android** à **Oui**.
2. Confirmez les conditions suivantes :
    - Les sauvegardes sont limitées.

### <a name="unenrollment"></a>Désinscription
Vous pouvez réinitialiser à distance des applications gérées à partir de contenant des documents et e-mails et données personnelles sont déchiffrées quand il est administré n’est plus comme suit :

1. À partir du portail Azure, [effectuer une réinitialisation](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Si votre application n’enregistre pas pour tous les gestionnaires réinitialisation confirment les conditions suivantes :
    - Une réinitialisation complète de l’application se produit.
3. Si votre application a demandé `WIPE_USER_DATA` ou `WIPE_USER_AUXILARY_DATA`, vérifiez les conditions suivantes :
    - Le contenu géré est supprimé de l’application. Pour plus d’informations, consultez [Intune App SDK for guide du développeur Android - réinitialisation sélective de](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Prise en charge de plusieurs identités
L’intégration de [prise en charge plusieurs identité](app-sdk-android.md#multi-identity-optional) est une modification de risque élevé devant être testé. Problèmes les plus courants sera en raison d’une configuration incorrecte de l’identité (contexte et le niveau de menace) et également les fichiers de suivi (`MAMFileProtectionManager`).

Au minimum les scénarios suivants pour plusieurs identités doivent être revalidées :

- **Enregistrer en tant que** stratégie fonctionne correctement pour les identités.
- Copier coller restrictions sont appliquées correctement à partir de code managé au personnel.
- Uniquement les données appartenant à l’identité gérée sont chiffrées et fichiers personnels ne sont pas modifiés.
- La réinitialisation sélective lors de la désinscription supprime uniquement les données d’identité gérée.
- L’utilisateur final est invité à entrer lancement conditionnel lors de la modification du code non managé pour le compte géré (première fois uniquement).

### <a name="app-configuration-optional"></a>Configuration de l’application (facultative)
Vous pouvez configurer le comportement d’applications gérées comme suit :

1. Si votre application consomme des paramètres de configuration d’application, vous devez tester que votre application gère correctement toutes les valeurs que vous (administrateur) pouvez définir. [Stratégies de configuration](https://docs.microsoft.com/intune/app-configuration-policies-overview) peuvent être créées et assignées à l’aide d’Intune.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter une application métier Android à Microsoft Intune](lob-apps-android.md).
