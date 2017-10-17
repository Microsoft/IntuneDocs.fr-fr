---
title: "Obtenir un certificat Push MDM Apple"
titlesuffix: Azure portal
description: "Découvrez la procédure permettant d’obtenir un certificat Push MDM Apple pour gérer les appareils iOS avec Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8d05199359f7e4ca2c41415c0db13e339c66c162
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2017
---
# <a name="get-an-apple-mdm-push-certificate"></a>Obtenir un certificat Push MDM Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune permet la gestion des appareils mobiles (MDM) pour les iPad, iPhone et ordinateurs Mac et permet aux utilisateurs d’accéder à la messagerie et aux applications de l’entreprise. Intune requiert un certificat Push MDM pour qu’Intune puisse gérer les appareils iOS et Mac. Une fois le certificat ajouté à Intune, vos utilisateurs peuvent installer l’application Portail d’entreprise pour inscrire leurs appareils. Vous pouvez également configurer la gestion des appareils iOS d’entreprise avec le programme DEP d’Apple ou inscrire des appareils à l’aide d’Apple Configurator, par exemple. Pour plus d’informations sur les options d’inscription, consultez [Choisir comment inscrire des appareils iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Procédure pour obtenir le certificat
Dans le portail Azure, choisissez **Inscription d’appareil** > **Inscription Apple** **Certificat Push MDM Apple**, puis suivez les étapes ci-après dans le portail Azure.

**Étape 1. Téléchargez la demande de signature de certificat Intune requise pour créer un certificat Push MDM Apple.**<br>
Sélectionnez **Télécharger votre CSR** pour télécharger et enregistrer le fichier de demande en local. Le fichier est utilisé pour demander un certificat de relation d’approbation à partir du portail Apple Push Certificates.

  ![Capture d’écran montrant l’écran Configurer le certificat Push MDM avec Push MDM non configuré.](./media/create-mdm-push-certificate.png)

**Étape 2. Créez un certificat Push MDM Apple.**<br>
Sélectionnez **Créer votre certificat Push MDM** pour accéder au portail Apple Push Certificates. Connectez-vous avec votre identifiant Apple d’entreprise, puis cliquez sur **Créer un certificat**. Sélectionnez **Choisir un fichier** et accédez au fichier de demande de signature de certificat, puis choisissez **Charger**. Dans la page Confirmation, choisissez **Télécharger** pour télécharger le fichier de certificat (.pem), puis enregistrez-le localement.

> [!NOTE]
> Le certificat est associé à l’identifiant Apple utilisé pour le créer. Bonne pratique : utilisez un identifiant Apple d’entreprise pour les tâches de gestion. N’utilisez jamais un identifiant Apple personnel.

**Étape 3 : Entrez l’identifiant Apple utilisé pour créer votre certificat Push MDM Apple.**<br>
Notez cet identifiant qui vous servira quand vous devrez renouveler ce certificat.

**Étape 4 :. Accédez à votre certificat Push MDM Apple à télécharger.**<br>
Accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Télécharger**. Avec le certificat Push, Intune peut inscrire et gérer des appareils Apple.

## <a name="renew-apple-mdm-push-certificate"></a>Renouveler un certificat Push MDM Apple
Le certificat Push MDM Apple est valide pendant un an et doit être renouvelé tous les ans pour assurer la gestion des appareils iOS et macOS. Si votre certificat a expiré, les appareils Apple inscrits ne peuvent pas être contactés.

Le certificat est associé à l’identifiant Apple utilisé pour le créer. Renouvelez le certificat Push MDM avec le même identifiant Apple utilisé pour le créer.

1. Dans le portail Azure, choisissez **Inscription d’appareil** > **Inscription Apple**, puis **Certificat Push MDM Apple**.
2. Choisissez **Télécharger votre CSR** pour télécharger et enregistrer le fichier de demande en local. Le fichier est utilisé pour demander un certificat de relation d’approbation à partir du portail Apple Push Certificates.
3. Recherchez le certificat que vous souhaitez renouveler et sélectionnez **Renouveler**.
4. Dans l’écran **Renouveler le certificat Push**, ajoutez une note qui vous permettra d’identifier le certificat par la suite, sélectionnez **Choisir un fichier** pour accéder au nouveau fichier de demande que vous avez téléchargé, puis choisissez **Charger**.
5. Dans l’écran **Confirmation**, sélectionnez **Télécharger** et enregistrez le fichier .pem localement.
6. Dans le portail Azure, sélectionnez l’icône **Certificat Push MDM Apple**, sélectionnez le fichier .pem téléchargé à partir d’Apple et choisissez **Charger**.

Votre certificat Push MDM Apple apparaît **Actif** et valide pendant 365 jours.
