---
title: Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android à l’aide de Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ecb043300578e5eba0613b6fa5f0fb249b1e515c
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692160"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung

Cette rubrique vous aide à configurer Intune pour l’inscription d’appareils Android pris en charge à l’aide de Samsung Knox Mobile Enrollment (KME). En utilisant Intune avec Samsung KME, vous pouvez inscrire un grand nombre d’appareils d’entreprise Android quand les utilisateurs finaux allument leurs appareils pour la première fois et se connectent à un réseau Wi-Fi ou de téléphonie mobile. De plus, les appareils peuvent être inscrits à l’aide de Bluetooth ou NFC en cas d’utilisation de l’application Knox Deployment.

Pour activer l’inscription Intune à l’aide de Samsung KME, vous devez utiliser les portails Intune et Samsung Knox dans cet ordre :

1. Dans le portail Knox :
    1. [Créer un profil de gestion des appareils mobiles](#create-mdm-profile)
    2. [Ajouter des appareils](#add-devices)
    3. [Affecter un profil de gestion des appareils mobiles aux appareils](#assign-an-mdm-profile-to-devices)
2. Dans le portail Knox, [configurer la connexion des utilisateurs finaux](#configure-how-end-users-sign-in).
3. [Distribuer les appareils](#distribute-devices).


Une liste d’identificateurs d’appareils (numéros de série et IMEI) est ajoutée automatiquement au portail Knox quand vous achetez des appareils auprès de revendeurs participant au programme de déploiement de Knox.


## <a name="prerequisites"></a>Prérequis

Pour vous inscrire à Intune en utilisant KME, vous devez d’abord inscrire votre société sur le portail Samsung Knox en effectuant les étapes suivantes :
1. [Assurez-vous que KME est disponible dans votre région/pays](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries) : KME est disponible dans plus de 55 pays/régions. Vérifiez que votre pays ou région de déploiement sont pris en charge.

2. [Appareils pris en charge](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+) : KME est disponible sur tous les appareils Samsung ayant au minimum Knox 2.4 pour l’inscription d’appareils Android, et au minimum Knox 2.8 pour l’inscription d’appareils Android Entreprise.

3. [Configuration réseau requise](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm) : vérifiez que les règles d’accès réseau et de pare-feu nécessaires sont autorisées sur votre réseau.

4. [Obtention d’un compte Samsung](https://www2.samsungknox.com/en/user/register) : un compte Samsung est nécessaire pour inscrire et activer KME et pour gérer tous les droits Knox Enterprise à partir d’un emplacement unique.

5. Examen de l’inscription : une fois que vous avez créé et envoyé votre profil, Samsung vérifie votre demande et l’approuve immédiatement ou la place en attente en vue d’un examen plus approfondi. Une fois votre compte approuvé, vous pouvez passer aux étapes suivantes.

## <a name="create-mdm-profile"></a>Créer un profil de gestion des appareils mobiles

Une fois votre entreprise correctement inscrite, vous pouvez créer votre profil MDM pour Microsoft Intune dans le portail Knox à l’aide des informations ci-dessous. Vous pouvez créer des profils MDM pour Android et Android Entreprise dans le portail Knox. 

### <a name="for-android-enterprise"></a>Pour Android Entreprise

| Champs de profil de gestion des appareils mobiles| Nécessaire ? | Valeurs | 
|-------------------|-----------|-------| 
|MDM Server URI     | Non        |Laissez ce champ vide. 
|Nom du profil       | Oui       |Entrez le nom de profil de votre choix. 
|Description        | Non        |Entrez une description du profil. 
|MDM Agent APK      | Oui       |https://aka.ms/intune_kme_deviceowner 
|Activer cette application en tant que propriétaire d’appareil Google | Oui | Choisissez cette option pour vous inscrire à Android Entreprise. 
|MDM pris en charge      | Oui       |Microsoft Intune 
|Laisser toutes les applications système activées | Non | Choisissez cette option pour avoir la garantie que toutes les applications sont activées et disponibles pour le profil. Si cette option n’est pas sélectionnée, seul un ensemble limité d’applications système s’affiche dans la barre d’état des applications de l’appareil. Les applications telles que l’application de messagerie restent masquées. 
|Custom JSON        | Non        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": « Entrez la chaîne du jeton d’inscription Intune »}. Découvrez [comment créer un profil d’inscription](android-kiosk-enroll.md). 
| Ajouter des contrats juridiques | Non | Laissez ce champ vide. 

### <a name="for-android"></a>Pour Android

Pour obtenir des instructions pas à pas, consultez les instructions sur [Création du profil Samsung](https://docs.samsungknox.com/KME-Getting-Started/Content/create-profiles.htm).

| Champs de profil de gestion des appareils mobiles| Nécessaire ? | Valeurs |
|-------------------|-----------|-------|
|MDM Server URI     | Non        |Laissez ce champ vide.
|Nom du profil       | Oui       |Entrez le nom de profil de votre choix.
|description        | Non        |Entrez une description du profil.
|MDM Agent APK      | Oui       |https://aka.ms/intune_kme
|Activer cette application en tant que propriétaire d’appareil Google | Non | Laissez cette option non sélectionnée pour Android. Cette option s’applique uniquement à Android Entreprise.
|Skip Setup wizard  | Non        |Choisissez cette option pour ignorer les invites de configuration d’appareil standard pour l’utilisateur final.
|Allow End User to Cancel Enrollment | Non | Choisissez cette option pour autoriser les utilisateurs à annuler KME.
|Custom JSON        | Non        |Laissez ce champ vide.
| Ajouter des contrats juridiques | Non | Laissez ce champ vide.
Associate a Knox license with this profile | Non | Laissez cette option désactivée. L’inscription à Intune à l’aide de KME ne nécessite pas de licence Knox.

## <a name="add-devices"></a>Ajouter des appareils

Pour affecter des profils de gestion des appareils mobiles à des appareils, les appareils Samsung Knox pris en charge doivent être ajoutés au portail Knox en appliquant l’une des méthodes suivantes :
- **Passer par des revendeurs approuvés par Samsung :** utilisez cette méthode si vous achetez des appareils auprès de revendeurs Samsung approuvés. Les revendeurs peuvent charger automatiquement des appareils pour vous après l’approbation. [Pour savoir comment ajouter des revendeurs, consultez le guide de l’utilisateur de Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Utiliser l’application Knox Deployment App (KDA) :** utilisez cette méthode si vous avez des appareils existants qui doivent être inscrits à l’aide de KME. Vous pouvez utiliser Bluetooth ou NFC pour ajouter des appareils au portail Knox à l’aide de cette méthode. [Pour en savoir plus sur l’utilisation de l’application KDA, consultez le guide de l’utilisateur de Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Affecter un profil de gestion des appareils mobiles aux appareils
Vous devez affecter un profil MDM aux appareils ajoutés dans le portail Knox avant de pouvoir les inscrire. [Pour en savoir plus sur la configuration des appareils, consultez le guide de l’utilisateur de Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configurer le mode de connexion des utilisateurs finaux

Pour les appareils inscrits à Intune via KME pour Android, vous pouvez configurer le mode de connexion de l’utilisateur final, comme suit :

- **Sans association de nom d’utilisateur :** dans le portail Knox, sous **Device details** (Détails de l’appareil), laissez les champs **User ID** (ID utilisateur) et **Password** (Mot de passe) vides pour les appareils ajoutés. Cette option exige que l’utilisateur final entre à la fois le nom d’utilisateur et le mot de passe lors de l’inscription à Intune.

- **Avec association de nom d’utilisateur :** dans le portail Knox, sous **Device details** (Détails de l’appareil), spécifiez un **User ID** (ID utilisateur) (tel qu’un nom d’utilisateur pour l’utilisateur affecté ou un compte de [gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md)) pour les appareils ajoutés. Cette option préremplit le nom d’utilisateur et exige que l’utilisateur final entre un mot de passe lors de l’inscription à Intune.

> [!NOTE]
>
>L’association avec utilisateur s’applique uniquement à l’inscription via l’administrateur des appareils Android. Quand l’association utilisateur est définie, seul l’utilisateur associé peut inscrire l’appareil à l’aide de KME. Cela est vrai même après une réinitialisation aux paramètres d’usine de l’appareil. Quand aucune association utilisateur n’est définie dans le portail Knox, tout utilisateur disposant d’une licence Intune valide peut inscrire l’appareil à l’aide de KME.
>Pour les appareils Android Enterprise entièrement gérés, même si l'association avec utilisateurs est définie, elle ne sera pas transmise à l'appareil et ne liera pas l'appareil à l'utilisateur.
>

## <a name="distribute-devices"></a>Distribuer les appareils

Après avoir créé et affecté un profil de gestion des appareils mobiles, associé un nom d’utilisateur et identifié les appareils comme appartenant à l’entreprise dans Intune, vous pouvez distribuer les appareils aux utilisateurs.

Encore besoin d’aide ? Consultez le [Guide d’utilisation complet de KME](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Forum aux questions

- **Prise en charge du propriétaire de l’appareil :**  - **Prise en charge du propriétaire de l’appareil :** Intune prend en charge l’inscription d’appareils dédiés et complètement managés à l’aide du portail KME. Les autres modes Device Owner pour Android Entreprise seront pris en charge quand ils seront disponibles dans Intune.

- **Aucune prise en charge de profil professionnel :** KME est une méthode d’inscription des appareils d’entreprise dans le profil professionnel Android qui garantit la séparation des données personnelles et professionnelles sur les appareils personnels. Par conséquent, l’inscription d’appareils dans un profil professionnel à l’aide de KME n’est pas un scénario pris en charge dans Intune.

- **Réinitialisation aux paramètres d’usine pour l’inscription à Android Entreprise :** si vous réaffectez des appareils déjà configurés, vous devez effectuer une réinitialisation aux paramètres d’usine des appareils durant leur inscription à Android Entreprise.

- **Mises à jour à l’aide d’un compte Google Play :** un compte Google Play n’est pas nécessaire pour l’inscription de l’appareil auprès de Microsoft Intune. Toutefois, pour les inscriptions via l’administrateur des appareils Android, les mises à jour ultérieures de l’application Portail d’entreprise Intune pourront nécessiter l’existence d’un compte Google Play sur l’appareil. Vous n’êtes pas obligé d’avoir un compte Google Play au moment de l’inscription en tant que propriétaire d'appareil Google.

- **Le champ de mot de passe est ignoré :** si le champ de **mot de passe** est renseigné dans **Détails de l’appareil** du portail Knox, il est ignoré par l’application Portail d’entreprise Intune durant l’inscription Android. L’utilisateur final doit entrer un mot de passe sur l’appareil pour terminer l’inscription de l’appareil.


## <a name="getting-support"></a>Obtenir de l’aide
Découvrez [comment obtenir une assistance technique pour Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


