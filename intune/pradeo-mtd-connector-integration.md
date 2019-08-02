---
title: Configurer l’intégration de Pradeo à Intune
titleSuffix: Intune on Azure
description: Intégration du connecteur Pradeo à Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe238832b55053df9726eb339885f1f0ed0241fa
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670770"
---
# <a name="integrate-pradeo-mobile-threat-defense-with-intune"></a>Intégrer Pradeo Mobile Threat Defense avec Intune

Effectuez les étapes suivantes pour intégrer la solution Pradeo Mobile Threat Defense à Intune.

## <a name="before-you-begin"></a>Avant de commencer

> [!NOTE]
> Les étapes suivantes doivent être effectuées dans la [console Pradeo Security](https://www.apps-security.com).

Avant de commencer le processus d’intégration de Pradeo à Intune, veillez à disposer des éléments suivants :

- Abonnement Microsoft Intune

- Informations d’identification d’administrateur Azure Active Directory pour accorder les autorisations suivantes :

  - Connexion et lecture de profil utilisateur

  - Accès à l’annuaire en tant qu’utilisateur connecté

  - Lecture des données de l’annuaire

  - Envoi des informations d’appareil à Intune

- Informations d’identification d’administrateur pour accéder à la console Pradeo Security.

### <a name="pradeo-app-authorization"></a>Autorisation de l’application Pradeo

Le processus d’autorisation de l’application Pradeo est le suivant :

- Autoriser le service Pradeo à communiquer à Intune des informations relatives à l’état d’intégrité des appareils.

- Pradeo se synchronise avec l’appartenance au groupe d’inscription Azure AD pour remplir la base de données de son appareil.

- Autoriser la console d’administration Pradeo à utiliser l’authentification unique (SSO) Azure AD.

- Autoriser l’application Pradeo à se connecter à l’aide de l’authentification unique Azure AD.

## <a name="to-set-up-pradeo-integration"></a>Pour configurer l’intégration de Pradeo

1. Accédez à la [console Pradeo Security](https://www.apps-security.com), puis connectez-vous avec vos informations d’identification.

2. Choisissez **Administration - Gestion de mobilité d’entreprise** dans le menu.

3. Choisissez le **logo Intune**.

4. Dans la fenêtre **EMM (gestion de mobilité d’entreprise) - Intune**, sous **Étape 1**, choisissez le bouton **Connecteur Pradeo**. 

    ![Capture d’écran de la fenêtre Pradeo EMM Intune](./media/pradeo_setup.png)

5. Dans la fenêtre de connexion Microsoft Intune, entrez vos informations d’identification Intune.

5. La page web Pradeo se rouvre. Sous **Étape 2**, choisissez le bouton **Intégrité de l’appareil Pradeo**.

7. Dans la fenêtre Connecteur Intune-Pradeo, sélectionnez **Accepter**. 

8. Dans la fenêtre du connecteur API d’appareil Pradeo, sélectionnez **Accepter**.

9. La page web Pradeo se rouvre. Sous **Étape 3**, choisissez le bouton **Se connecter à Microsoft**. 

10. Dans la fenêtre d’authentification Microsoft Intune, entrez vos informations d’identification Intune.

11. Quand le message **Intégration réussie** s’affiche, l’intégration est terminée.

## <a name="next-steps"></a>Étapes suivantes

- [Configurer les applications Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)
