---
title: Intégrer Zimperium MTD à Microsoft Intune
titleSuffix: ''
description: Comment configurer la solution Zimperium Mobile Threat Defense (MTD) à Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 68896a363cab37aabe9a597872da0fe75c44c473
ms.sourcegitcommit: 3903f20cb5686532ccd8c36aa43c5150cee7cca2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52267235"
---
# <a name="integrate-zimperium-with-intune"></a>Intégrer Zimperium à Intune

Suivez les étapes ci-dessous pour intégrer la solution Zimperium Mobile Threat Defense à Intune.

## <a name="before-you-begin"></a>Avant de commencer

> [!NOTE]
> Les étapes suivantes doivent être effectuées dans la  [console Zimperium MTD](https://sso.zimperium.com/signon/aad/).

Avant d’entamer le processus d’intégration de Zimperium à Intune, vérifiez que vous disposez de l’abonnement et des informations d’identification suivantes :

-   Abonnement Microsoft Intune

-   Informations d’identification d’administrateur Azure Active Directory pour accorder les autorisations suivantes :

    -   Connexion et lecture de profil utilisateur

    -   Accès à l’annuaire en tant qu’utilisateur connecté

    -   Lecture des données de l’annuaire

    -   Envoi des informations d’appareil à Intune

-   Informations d’identification d’administrateur pour accéder à la console Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorisation de l’application Zimperium

Le processus d’autorisation de l’application Zimperium se déroule ainsi :

-   Autoriser le service Zimperium à communiquer à Intune des informations relatives à l’état d’intégrité des appareils.

-   Synchroniser Zimperium avec l’appartenance au groupe d’inscriptions Azure Active Directory pour remplir sa base de données d’appareils.

-   Autoriser la console d’administration Zimperium à utiliser l’authentification unique (SSO) Azure AD.

-   Autoriser l’application Zimperium à se connecter en utilisant l’authentification unique Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Pour configurer l’intégration de Zimperium

1.  Accédez à la  [console Zimperium MTD](https://sso.zimperium.com/signon/aad/)  et connectez-vous avec vos informations d’identification.

2.  Choisissez **Management** (Administration) dans le menu de gauche.

3.  Choisissez l’onglet **MDM settings** (Paramètres MDM).

4.  Choisissez **Add MDM** (Ajouter MDM), puis sélectionnez **Microsoft Intune** dans la liste **MDM provider** (Fournisseur MDM).

5.  Après avoir défini Microsoft Intune comme service MDM, la fenêtre  **Microsoft Intune Configuration**  s’affiche. Choisissez  **Ajouter Azure Active Directory**  pour chaque option : applications **Zimperium zConsole**, **zIPS iOS et Android** pour autoriser Zimperium à communiquer avec Intune et Azure AD via l’authentification unique Azure AD.

    > [!IMPORTANT]
    > Vous devez ajouter les applications zConsole Zimperium, zIPS iOS et Android pour effectuer le processus d’intégration à Intune.

6.  Choisissez  **Accepter**  pour autoriser l’application Zimperium à communiquer avec Intune et Azure Active Directory.

7.  Après avoir ajouté les applications **Zimperium zConsole** et **zIPS iOS et Android** à Azure AD, ajoutez les groupes de sécurité Azure AD. Cet ajout permet à Zimperium de synchroniser le groupe de sécurité Azure AD avec son service.

8.  Choisissez  **Terminer** pour enregistrer la configuration et démarrer la première synchronisation de groupe de sécurité Azure AD.

## <a name="next-steps"></a>Étapes suivantes

-   [Configurer les applications Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)
