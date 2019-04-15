---
title: Obtenir un certificat Push MDM Apple pour Intune
titleSuffix: ''
description: Obtenez un certificat Push MDM Apple pour gérer les appareils iOS avec Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51fe7ab05174f614ad4278cd83ede31c6bb9beb2
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567450"
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obtenir un certificat Push MDM Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune nécessite un certificat Push MDM Apple pour gérer les appareils iOS et macOS. Une fois le certificat ajouté à Intune, vos utilisateurs peuvent inscrire leurs appareils avec :

- L'application Portail d’entreprise.

- Les méthodes d’inscription en bloc d’Apple comme le programme d’inscription des appareils, Apple School Manager ou Apple Configurator.

Pour plus d’informations sur les options d’inscription, consultez [Choisir comment inscrire des appareils iOS](enrollment-method-choose-ios.md).

Lors de l’expiration d’un certificat push, vous devez le renouveler. Lors du renouvellement, veillez à utiliser le même identifiant Apple que vous avez utilisé lors de la création du certificat push.


## <a name="steps-to-get-your-certificate"></a>Procédure pour obtenir le certificat
Dans le [portail Azure](https://portal.azure.com), choisissez **Inscription d’appareil** > **Inscription Apple** > **Certificat Push MDM Apple**, puis suivez les étapes ci-après dans le [portail Azure](https://portal.azure.com).

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>Étape 1. Autoriser Microsoft à envoyer des informations d’utilisateur et d’appareil à Apple
Sélectionnez **J’accepte.** pour autoriser Microsoft à envoyer des données à Apple.

![Écran Configurer le certificat Push MDM avec Push MDM non configuré.](./media/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>Étape 2. Télécharger la demande de signature de certificat Intune nécessaire à la création d’un certificat Push MDM Apple
Sélectionnez **Télécharger votre CSR** pour télécharger et enregistrer le fichier de demande en local. Le fichier est utilisé pour demander un certificat de relation d’approbation à partir du portail Apple Push Certificates.

  ### <a name="step-3-create-an-apple-mdm-push-certificate"></a>Étape 3. Créer un certificat Push MDM Apple
Sélectionnez **Créer votre certificat Push MDM** pour accéder au portail Apple Push Certificates. Connectez-vous avec votre identifiant Apple d’entreprise, puis cliquez sur **Créer un certificat**. Sélectionnez **Choisir un fichier** et accédez au fichier de demande de signature de certificat, puis choisissez **Charger**. Dans la page Confirmation, choisissez **Télécharger** pour télécharger le fichier de certificat (.pem), puis enregistrez-le localement.

> [!NOTE]
> Le certificat est associé à l’identifiant Apple utilisé pour le créer. Comme meilleure pratique, utilisez un ID Apple d’entreprise pour les tâches de gestion et assurez-vous que la boîte aux lettres est analysée par plusieurs personnes comme une liste de distribution. N’utilisez jamais un identifiant Apple personnel.

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>Étape 4. Entrer l’identifiant Apple utilisé pour créer votre certificat Push MDM Apple
Notez cet identifiant qui vous servira quand vous devrez renouveler ce certificat.

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>Étape 5. Accéder à votre certificat Push MDM Apple à charger
Accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Télécharger**. Avec le certificat Push, Intune peut inscrire et gérer des appareils Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Renouveler un certificat Push MDM Apple
Le certificat Push MDM Apple est valide pendant un an et doit être renouvelé tous les ans pour assurer la gestion des appareils iOS et macOS. Si votre certificat a expiré, les appareils Apple inscrits ne peuvent pas être contactés.

Le certificat est associé à l’identifiant Apple utilisé pour le créer. Renouvelez le certificat Push MDM avec le même identifiant Apple utilisé pour le créer.

1. Dans le [portail Azure](https://portal.azure.com), choisissez **Inscription des appareils** > **Inscription Apple**, puis choisissez la mosaïque **Certificat de transmission de type push GPM Apple**.
2. Choisissez **Télécharger votre CSR** pour télécharger et enregistrer le fichier de demande en local. Le fichier est utilisé pour demander un certificat de relation d’approbation à partir du portail Apple Push Certificates.
3. Sélectionnez **Créer votre certificat Push MDM** pour accéder au portail Apple Push Certificates. Recherchez le certificat que vous souhaitez renouveler et sélectionnez **Renouveler**.
4. Dans l’écran **Renouveler le certificat Push**, ajoutez une note qui vous permettra d’identifier le certificat par la suite, sélectionnez **Choisir un fichier** pour accéder au nouveau fichier de demande que vous avez téléchargé, puis choisissez **Charger**.
   > [!TIP]
   > Un certificat peut être identifié par son UID. Examinez **l’ID d’objet** dans les détails du certificat pour trouver la partie GUID de l’UID. Sinon, sur un appareil iOS inscrit, accédez à **Settings** > **General** > **Device** **Management** > **Management Profile** > **More Details** > **Management Profile** (Paramètres, Général, Appareil, Gestion, Profil de gestion, Plus de détails, Profil de gestion). La deuxième ligne, **Topic** (Rubrique), contient le GUID unique que vous pouvez associer au certificat dans le portail Apple Push Certificates.
 
6. Dans l’écran **Confirmation**, sélectionnez **Télécharger** et enregistrez le fichier .pem localement.
7. Dans le [portail Azure](https://portal.azure.com), sélectionnez l’icône de navigation **Certificat Push MDM Apple**, sélectionnez le fichier .pem téléchargé à partir d’Apple, puis choisissez **Charger**.

Votre certificat Push MDM Apple apparaît **Actif** et valide pendant 365 jours.
