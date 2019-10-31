---
title: Intégrer Zimperium MTD à Microsoft Intune
titleSuffix: Microsoft Intune
description: Comment configurer la solution Zimperium Mobile Threat Defense (MTD) à Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
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
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d843cf707cf182655d0044dde289caca730ccd6b
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810303"
---
# <a name="integrate-zimperium-with-intune"></a>Intégrer Zimperium à Intune

Suivez les étapes ci-dessous pour intégrer la solution Zimperium Mobile Threat Defense à Intune.

## <a name="before-you-begin"></a>Avant de commencer

Les étapes suivantes doivent être effectuées dans la [console Zimperium MTD](https://www.zimperium.com/platform) et établissent une connexion au service Lookout pour les appareils inscrits dans Intune (à l’aide de la conformité de l’appareil) et les appareils non inscrits (à l’aide des stratégies de protection des applications).

Avant d’entamer le processus d’intégration de Zimperium à Intune, vérifiez que vous disposez de l’abonnement et des informations d’identification suivantes :

- Abonnement Microsoft Intune

- Informations d’identification d’administrateur Administrateur général Azure Active Directory pour accorder les autorisations suivantes :

  - Connexion et lecture de profil utilisateur

  - Accès à l’annuaire en tant qu’utilisateur connecté

  - Lecture des données de l’annuaire

  - Envoi des informations d’appareil à Intune

- Informations d’identification d’administrateur pour accéder à la console Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorisation de l’application Zimperium

Le processus d’autorisation de l’application Zimperium se déroule ainsi :

- Accordez au service Zimperium les autorisations de communiquer à Intune des informations relatives à l’état d’intégrité des appareils. Pour accorder ces autorisations, vous devez utiliser les informations d’identification Administrateur général. L’octroi d’autorisations est une opération unique. Une fois que les autorisations sont accordées, les informations d’identification Administrateur général ne sont pas nécessaires pour les opérations quotidiennes.

- Synchroniser Zimperium avec l’appartenance au groupe d’inscriptions Azure Active Directory pour remplir sa base de données d’appareils.

- Autoriser la console d’administration Zimperium à utiliser l’authentification unique (SSO) Azure AD.

- Autoriser l’application Zimperium à se connecter en utilisant l’authentification unique Azure AD.

Pour plus d’informations sur le consentement et les applications Azure Active Directory, consultez [Demander les autorisations à un administrateur d’annuaire](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) dans l’article Azure Active Directory *Autorisations et consentement dans le point de terminaison Azure Active Directory v2.0*.


## <a name="to-set-up-zimperium-integration"></a>Pour configurer l’intégration de Zimperium

1. Accédez à la [console Zimperium MTD](https://www.zimperium.com/platform) et connectez-vous avec vos informations d’identification. Pour effectuer le processus de configuration de l’intégration de Zimperium, vous devez vous connecter avec un utilisateur Azure Active Directory qui a le rôle Administrateur général. Cette opération de configuration unique utilise les droits Administrateur général pour accorder l’autorisation dans votre organisation aux applications Zimperium de communiquer avec Intune. 

2. Choisissez **Management** (Administration) dans le menu de gauche.

3. Choisissez l’onglet **MDM settings** (Paramètres MDM).

4. Choisissez **Add MDM** (Ajouter MDM), puis sélectionnez **Microsoft Intune** dans la liste **MDM provider** (Fournisseur MDM).

5. Après avoir défini Microsoft Intune comme service MDM, la fenêtre **Configuration Microsoft Intune** s’affiche ; choisissez **Ajouter Azure Active Directory** pour chaque option : **applications zConsole Zimperium**, **zIPS iOS et Android**  pour autoriser Zimperium à communiquer avec Intune et Azure AD via l’authentification unique Azure AD.

    > [!IMPORTANT]  
    > Vous devez ajouter les applications zConsole Zimperium, zIPS iOS et Android pour terminer le processus d’intégration à Intune.

6. Choisissez **Accepter** pour autoriser l’application Zimperium à communiquer avec Intune et Azure Active Directory.

7. Après avoir ajouté les applications **zConsole Zimperium**, **zIPS iOS et Android** à Azure AD, ajoutez les groupes de sécurité Azure AD. Cet ajout permet à Zimperium de synchroniser le groupe de sécurité Azure AD avec son service.

8. Choisissez **Terminer** pour enregistrer la configuration et démarrer la première synchronisation de groupe de sécurité Azure AD.

9. Déconnectez-vous de la console Zimperium MTD.

## <a name="next-steps"></a>Étapes suivantes

- [Configurer des applications Zimperium pour les appareils inscrits](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Configurer des applications Zimperium pour les appareils non inscrits](~/protect/mtd-add-apps-unenrolled-devices.md)
