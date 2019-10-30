---
title: Configurer l’intégration de Sophos Mobile à Intune
titleSuffix: Intune on Azure
description: Découvrez comment configurer la solution Sophos Mobile avec Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aad6268606dfcf69c304bb5c5b270c8c4795e4b2
ms.sourcegitcommit: 1a5b185acd27954b10b6d59409d82eb80fd71284
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72681285"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Intégrer Sophos Mobile à Intune  

Suivez les étapes ci-dessous pour intégrer la solution Sophos Mobile Threat Defense à Intune.  

> [!NOTE]
> Ce fournisseur Mobile Threat Defense n’est pas pris en charge pour les appareils non inscrits.

## <a name="before-you-begin"></a>Avant de commencer  

Avant de commencer le processus d’intégration de Sophos Mobile à Intune, veillez à avoir les éléments suivants :  
- Abonnement Microsoft Intune  
- Informations d’identification d’administrateur Azure Active Directory pour accorder les autorisations suivantes :  
  - Connexion et lecture de profil utilisateur  
  - Accès à l’annuaire en tant qu’utilisateur connecté  
  - Lecture des données de l’annuaire  
  - Envoi des informations d’appareil à Intune  
- Informations d’identification administrateur pour accéder à la console d’administration de Sophos Mobile.  


### <a name="sophos-mobile-app-authorization"></a>Autorisation de l’application Sophos Mobile  
  
Le processus d’autorisation de l’application Sophos Mobile est le suivant :  
- Autoriser le service Sophos Mobile à communiquer avec Intune des informations relatives à l’état d’intégrité de l’appareil.  
- Sophos Mobile se synchronise avec l’appartenance au groupe d’inscription Azure AD pour renseigner la base de données de son appareil.  
- Autoriser la console d’administration de Sophos Mobile à utiliser l’authentification unique (SSO) Azure AD.  
- Autoriser l’application Sophos Mobile à se connecter avec l’authentification unique Azure AD.  


## <a name="to-set-up-sophos-mobile-integration"></a>Pour configurer l’intégration de Sophos Mobile  

1. Connectez-vous au [portail Azure]( https://portal.azure.com/), accédez à **Intune** > **Conformité de l’appareil** > **Mobile Threat Defense** > et sélectionnez **Ajouter**.  
2. Dans la page **Ajouter un connecteur**, utilisez la liste déroulante et sélectionnez **Sophos**. Ensuite, sélectionnez **Créer**.  
3. Sélectionnez le lien *Ouvrir la console d’administration Sophos*.  
4. Connectez-vous à la [console d’administration Sophos](https://central.sophos.com/) avec vos informations d’identification Sophos.  
5. Accédez à **Mobile** > **Paramètres** > **Configuration** > **Configuration de Sophos**.  
6. Dans la page **Configuration de Sophos**, sélectionnez l’onglet **Intune MTD**.  
   ![Configuration de Sophos](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Sélectionnez **Lier**, puis sélectionnez **Oui**. Sophos se connecte à Intune et vous demande de vous connecter à votre abonnement Intune. 
8. Dans la fenêtre d’authentification Microsoft Intune, entrez vos informations d’identification Intune et **Acceptez** la demande d’autorisation pour *Sophos Mobile Thread Defense*.  
   ![Authentification Intune](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. Dans la page **Configuration de Sophos**, sélectionnez **Enregistrer** afin de terminer la configuration pour Intune :  
   ![Enregistrer la configuration de Sophos](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. Quand le message **Intégration réussie** s’affiche, l’intégration est terminée.  
1. Sophos est maintenant disponible dans la console Intune.  


## <a name="next-steps"></a>Étapes suivantes  
[Configurer les applications clientes de Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
