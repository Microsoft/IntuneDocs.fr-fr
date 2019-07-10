---
title: Configurer l’intégration de Better Mobile à Intune
titleSuffix: Intune on Azure
description: Intégration du connecteur Better Mobile à Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7072d7d3d24578e0f82ea21eb653906dfa30b4c
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546974"
---
# <a name="integrate-better-mobile-with-intune"></a>Intégrer Better Mobile à Intune

Suivez les étapes ci-dessous pour intégrer la solution Better Mobile Threat Defense à Intune.

## <a name="before-you-begin"></a>Avant de commencer

> [!NOTE]
> Les étapes ci-dessous doivent être suivies dans la [console d’administration de Better Mobile](https://aad.bmobi.net).

Avant de commencer le processus d’intégration de Better Mobile à Intune, munissez-vous des éléments suivants :

- Abonnement Microsoft Intune

- Informations d’identification d’administrateur Azure Active Directory pour accorder les autorisations suivantes :

    - Connexion et lecture de profil utilisateur

    - Accès à l’annuaire en tant qu’utilisateur connecté

    - Lecture des données de l’annuaire

    - Envoi des informations d’appareil à Intune

- Informations d’identification administrateur pour accéder à la console d’administration de Better Mobile.

### <a name="better-mobile-app-authorization"></a>Autorisation de l’application Better Mobile

Le processus d’autorisation de l’application Better Mobile est le suivant :

- Autoriser le service Better Mobile à communiquer à Intune des informations relatives à l’état d’intégrité de l’appareil.

- Better Mobile se synchronise avec l’appartenance au groupe d’inscription Azure AD pour remplir la base de données de son appareil.

- Autoriser la console d’administration de Better Mobile à utiliser l’authentification unique (SSO) Azure AD.

- Autoriser l’application Better Mobile à se connecter avec l’authentification unique Azure AD.

## <a name="to-set-up-better-mobile-integration"></a>Configurer l’intégration de Better Mobile

1. Accédez à la [console d’administration de Better Mobile](https://aad.bmobi.net), puis connectez-vous avec vos informations d’identification.
2. Choisissez **Intégration** > **EMM/MDM** > **AJOUTER UN COMPTE**.

     ![Image de la console d’administration de Better Mobile](media/better_mobile_console.png)
 
3. Choisissez **Intune**.
4. À côté de **NOM DU COMPTE**, tapez un descripteur. 
5. Dans la fenêtre **Connexion Microsoft**, entrez vos informations d’identification Intune.
6. Dans la fenêtre **Autorisations demandées**, choisissez **Accepter**.
7. Recherchez les groupes de sécurité Azure AD à partir desquels vous souhaitez que Better Mobile synchronise les appareils, et sélectionnez-les dans la liste. Ensuite, sélectionnez **Continuer**.
8. Sélectionnez **Terminé**.
9. La page **Ajouter un compte** s’affiche de nouveau. Fermez la page. 

## <a name="next-steps"></a>Étapes suivantes

- [Configurer des applications Better clientes](mtd-apps-ios-app-configuration-policy-add-assign.md)
