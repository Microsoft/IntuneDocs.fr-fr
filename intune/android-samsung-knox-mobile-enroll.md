---
title: Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung
titlesuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android à l’aide de Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88cb733c688019b2fc5455a0184e968d91e77806
ms.sourcegitcommit: b0ad42fe5b5627e5555b2f9e5bb81bb44dbff078
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2018
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Inscrire automatiquement des appareils Android à l’aide de Knox Mobile Enrollment de Samsung

Cette rubrique vous aide à configurer Intune pour l’inscription d’appareils Android pris en charge à l’aide de Samsung Knox Mobile Enrollment (KME). En utilisant Intune avec Samsung KME, vous pouvez inscrire un grand nombre d’appareils d’entreprise Android quand les utilisateurs finaux allument leurs appareils pour la première fois et se connectent à un réseau Wi-Fi ou de téléphonie mobile. De plus, les appareils peuvent être inscrits à l’aide de Bluetooth ou NFC en cas d’utilisation de l’application Knox Deployment.

Pour activer l’inscription Intune à l’aide de Samsung KME, vous devez utiliser les portails Intune et Samsung Knox dans cet ordre :

1. Dans le portail Knox :
    1. [Créer un profil de gestion des appareils mobiles](#create-mdm-profile)
    2. [Ajouter des appareils](#add-devices)
    3. [Affecter un profil de gestion des appareils mobiles aux appareils](#assign-an-mdm-profile-to-devices)
2. Dans le portail Azure, [identifier les appareils comme appartenant à l’entreprise](#identify-devices-as-corporate-owned).
3. Dans le portail Knox, [configurer la connexion des utilisateurs finaux](#configure-how-end-users-sign-in).
4. [Distribuer les appareils](#distribute-devices).


Une liste d’identificateurs d’appareils (numéros de série et IMEI) est ajoutée automatiquement au portail Knox quand vous achetez des appareils auprès de revendeurs participant au programme Knox Deployment.


## <a name="prerequisites"></a>Prérequis

Pour vous inscrire à Intune en utilisant KME, vous devez d’abord inscrire votre société sur le portail Samsung Knox en effectuant les étapes suivantes :
1.  [Vérifiez que KME est disponible dans votre région](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries) : KME est disponible dans plus de 55 pays. Vérifiez que votre pays de déploiement est pris en charge.

2.  [Appareils pris en charge](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+) : KME est disponible sur tous les appareils Samsung avec au minimum Knox 2.4.

3.  [Configuration réseau requise](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm) : vérifiez que les règles d’accès réseau et de pare-feu nécessaires sont autorisées sur votre réseau.

4.  [Créez un compte Samsung](https://www2.samsungknox.com/en/user/register) : un compte Samsung est nécessaire pour inscrire et activer KME et pour gérer tous les droits Knox Enterprise à partir d’un emplacement unique.

5.  Examen de l’inscription : une fois votre profil créé et envoyé, Samsung examine votre demande et l’approuve immédiatement ou la place en attente en vue d’un examen plus approfondi. Une fois votre compte approuvé, vous pouvez passer aux étapes suivantes.

## <a name="create-mdm-profile"></a>Créer un profil de gestion des appareils mobiles

Une fois votre société inscrite, vous pouvez créer votre profil de gestion des appareils mobiles pour Microsoft Intune dans le portail Knox en utilisant les informations ci-dessous. Pour obtenir des instructions pas à pas, consultez l’[Assistant Configuration de profil Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm).

| Champs de profil de gestion des appareils mobiles| Nécessaire ? | Valeurs |
|-------------------|-----------|-------|
|MDM Server URI     | Non        |Laissez ce champ vide.
|Profile Name       | Oui       |Entrez le nom de profil de votre choix.
|description        | Non        |Entrez une description du profil.
|MDM Agent APK      | Oui       |https://aka.ms/intune_kme
|Skip Setup wizard  | Non        |Choisissez cette option pour ignorer les invites de configuration d’appareil standard pour le compte de l’utilisateur final.
|Allow End User to Cancel Enrollment | Non | Choisissez cette option pour autoriser les utilisateurs à annuler KME.
|Custom JSON        | Non        |Laissez ce champ vide.
| EULAs, Terms of Service & User Agreements| Non | Choisissez cette option pour afficher les contrats en rapport avec Knox afin que l’utilisateur les accepte.
Associate a Knox license with this profile | Non | Laissez cette option désactivée. L’inscription à Intune à l’aide de KME ne nécessite pas de licence Knox.

## <a name="add-devices"></a>Ajouter des appareils

Pour affecter des profils de gestion des appareils mobiles à des appareils, les appareils Samsung Knox pris en charge doivent être ajoutés au portail Knox en appliquant l’une des méthodes suivantes :
- **Passer par des revendeurs approuvés par Samsung :** utilisez cette méthode si vous achetez des appareils auprès de revendeurs Samsung approuvés. Les revendeurs peuvent charger automatiquement des appareils pour vous après l’approbation. [Pour savoir comment ajouter des revendeurs, consultez le guide de l’utilisateur de Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Utiliser l’application Knox Deployment App (KDA) :** utilisez cette méthode si vous avez des appareils existants qui doivent être inscrits à l’aide de KME. Vous pouvez utiliser Bluetooth ou NFC pour ajouter des appareils au portail Knox à l’aide de cette méthode. [Pour en savoir plus sur l’utilisation de l’application KDA, consultez le guide de l’utilisateur de Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Affecter un profil de gestion des appareils mobiles aux appareils
Vous devez affecter un profil MDM aux appareils ajoutés dans le portail Knox avant de pouvoir les inscrire. [Pour en savoir plus sur la configuration des appareils, consultez le guide de l’utilisateur de Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="identify-devices-as-corporate-owned"></a>Identifier les appareils comme appartenant à l’entreprise
Vous pouvez identifier les appareils inscrits comme appartenant à l’entreprise à l’aide de KME. Cette opération doit être effectuée avant l’inscription des appareils. Elle vous permet d’effectuer d’autres tâches d’administration et de collecter des informations supplémentaires, comme le numéro de téléphone complet et un inventaire des applications.

Suivez ces étapes pour identifier les appareils comme appartenant à l’entreprise :

1. Exportez la liste des appareils à partir du portail Knox dans un fichier CSV.

2. Mettez en forme le fichier CSV à l’aide du numéro IMEI ou du numéro de série comme indiqué [ici](https://docs.microsoft.com/en-us/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number).

3. Dans le portail Azure, chargez le fichier CSV sur **Inscription de l’appareil** > **Identificateurs d’appareil d’entreprise** > **Ajouter**.

Maintenant, les appareils identifiés qui vont être inscrits sont marqués comme appartenant à l’entreprise.

> [!NOTE]
>Intune affecte automatiquement l’état « Appartenant à l’entreprise » aux appareils inscrits avec le compte de [gestionnaire d’inscription d’appareil](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll).

## <a name="configure-how-end-users-sign-in"></a>Configurer le mode de connexion des utilisateurs finaux

Pour les appareils inscrits dans Intune à l’aide de KME, vous pouvez configurer la façon dont un utilisateur final se connecte comme suit :

- **Sans association de nom d’utilisateur :** dans le portail Knox sous **Device details** (Détails de l’appareil), laissez les champs **User ID** (ID utilisateur) et **Password** (Mot de passe) vides pour les appareils ajoutés. Cela exige que l’utilisateur final entre à la fois le nom d’utilisateur et le mot de passe lors de l’inscription à Intune.

- **Avec association de nom d’utilisateur :** dans le portail Knox sous **Device details** (Détails de l’appareil), spécifiez un **User ID** (ID utilisateur) (tel qu’un nom d’utilisateur pour l’utilisateur affecté ou un compte de [gestionnaire d’inscription d’appareil](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll)) pour les appareils ajoutés. Cela préremplit le nom d’utilisateur et exige que l’utilisateur final entre un mot de passe lors de l’inscription à Intune.

> [!NOTE]
>
>Quand l’association utilisateur est définie, seul l’utilisateur associé peut inscrire l’appareil à l’aide de KME. C’est vrai même après une réinitialisation aux paramètres d’usine de l’appareil. Quand aucune association utilisateur n’est définie dans le portail Knox, tout utilisateur disposant d’une licence Intune valide peut inscrire l’appareil à l’aide de KME.
>

## <a name="distribute-devices"></a>Distribuer des appareils

Après avoir créé et affecté un profil de gestion des appareils mobiles, associé un nom d’utilisateur et identifié les appareils comme appartenant à l’entreprise dans Intune, vous pouvez distribuer les appareils aux utilisateurs.

Encore besoin d’aide ? Consultez le [Guide de l’utilisateur de Knox Mobile Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Forum aux questions
- **Compte Google Play :** un compte Google Play n’est pas nécessaire pour l’inscription de l’appareil auprès de Microsoft Intune. Toutefois, les mises à jour ultérieures de l’application Portail d’entreprise Intune pourront nécessiter l’existence d’un compte Google Play sur l’appareil.

- **Mode de propriétaire de l’appareil Google :** l’inscription en mode Google Device Owner de l’appareil à l’aide de KME n’est pas prise en charge dans cette préversion. Ce scénario est en cours d’étude.

- **Le champ « Password » est ignoré :** si le champ **password** est renseigné dans **Device details** (Détails de l’appareil) dans le portail Knox, il est ignoré par l’application Portail d’entreprise Intune. L’utilisateur final doit entrer un mot de passe sur l’appareil pour terminer l’inscription de l’appareil.

## <a name="getting-support"></a>Obtenir de l’aide
Découvrez [comment obtenir une assistance technique pour Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


