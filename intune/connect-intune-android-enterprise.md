---
title: Liez votre compte Intune à votre compte Google Play géré.
titleSuffix: Microsoft Intune
description: Découvrez comment lier votre compte Intune à votre compte Google Play géré.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19efd0821deeac0e76c60ee67e6230da554391a0
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567385"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Lier votre compte Intune à votre compte Google Play géré

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pour prendre en charge les [appareils Android Entreprise avec profil professionnel](android-work-profile-enroll.md), les [appareils Android Entreprise complètement gérés](android-fully-managed-enroll.md) et les [appareils Android Entreprise dédiés](android-kiosk-enroll.md), vous devez lier votre compte de locataire Intune à votre compte Google Play géré.  

> [!NOTE]
> En raison de l’interaction entre les domaines Google et Microsoft, cette étape peut nécessiter un réglage des paramètres de votre navigateur.  Vérifiez que « portal.azure.com » et « play.google.com » sont dans la même zone de sécurité de votre navigateur.

1. Si vous ne l’avez pas déjà fait, préparez la gestion des appareils mobiles en définissant **Microsoft Intune** comme [autorité de gestion des appareils mobiles](mdm-authority-set.md).
2. Connectez-vous à [Intune dans le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Android** > **Google Play géré**.  Si vous utilisez un rôle d’administrateur Intune personnalisé, l’accès à ceci nécessite des autorisations de lecture et de mise à jour pour l’organisation.
   
   ![Écran d’inscription professionnelle Android](./media/android-work-bind.png)

3. Choisissez **J’accepte** pour autoriser Microsoft à [envoyer des informations d’utilisateur et d’appareil à Google](data-intune-sends-to-google.md). 
   
4. Choisissez **Lancez Google pour vous connecter maintenant** pour ouvrir le site web Google Play géré. Le site web s’ouvre dans un nouvel onglet dans votre navigateur.
  
5. Dans la page de connexion de Google, entrez le compte Google à associer à toutes les tâches de gestion d’Android Entreprise pour ce locataire. Il s’agit du compte Google partagé par les administrateurs informatiques de votre organisation pour gérer et publier des applications dans la console Google Play. Vous pouvez utiliser un compte Google existant ou en créer un. Le compte que vous choisissez ne doit pas être associé à un domaine G Suite.
    
    > [!Note]
    > Si vous utilisez le navigateur Microsoft Edge, cliquez sur **Se connecter** en haut à droite pour vous connecter à votre compte Google.

6. Fournissez le nom de votre société comme **Nom d’organisation**. Pour **Enterprise mobility management (EMM) provider** (Fournisseur de gestion de la mobilité d’entreprise), **Microsoft Intune** doit être affiché.

7. Acceptez le contrat Android, puis choisissez **Confirmer**. Votre demande va être traitée.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Déconnecter votre compte d’administration Android Entreprise

Vous pouvez désactiver l’inscription et la gestion d’Android Entreprise. Pour ce faire, vous devez d’abord mettre hors service les appareils avec profil professionnel Android Entreprise inscrits. Ensuite, choisissez **Se déconnecter** dans la console d’administration Intune pour annuler l’inscription de tous les appareils avec profil professionnel Android Entreprise et tous les appareils dédiés inscrits. Cela supprime également la relation entre le compte Google Play géré et Intune.

1. En tant qu’administrateur Intune, dans le [portail Azure](https://portal.azure.com), choisissez **Tous les services** > **Surveillance + Gestion** > **Intune**.
2. Choisissez **Inscription de l’appareil** > **Inscription Android** > **Google Play géré** > **Se déconnecter**.
3. Choisissez **Oui** pour vous déconnecter et annuler l’inscription de tous les appareils professionnels Android dans Intune.

## <a name="next-steps"></a>Étapes suivantes

Une fois connecté au compte Google Play géré, vous pouvez [configurer des appareils avec profil professionnel Android Entreprise](android-work-profile-enroll.md) et [configurer des appareils dédiés Android Entreprise](android-kiosk-enroll.md).
