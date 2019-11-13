---
title: Intégrer Check Point SandBlast MTD
titleSuffix: Microsoft Intune
description: Comment configurer CheckPoint SandBlast Mobile Threat Defense (MTD) avec Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
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
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 514baf3395a2cad9682e6c070b8615f320cc214c
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801457"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Intégrer Check Point SandBlast Mobile à Intune

Effectuez les étapes suivantes pour intégrer la solution Check Point SandBlast Mobile Threat Defense à Intune.

> [!NOTE]
> Ce fournisseur Mobile Threat Defense n’est pas pris en charge pour les appareils non inscrits.

## <a name="before-you-begin"></a>Avant de commencer

Les instructions de cet article sont exécutées dans la [console Check Point SandBlast Mobile](https://intune-4.eu1.locsec.net/). 

Avant d’entamer le processus d’intégration de Check Point SandBlast Mobile à Intune, vérifiez que vous disposez des éléments suivants :

- Abonnement Microsoft Intune

- Informations d’identification d’administrateur Azure Active Directory pour accorder les autorisations suivantes :

  - Connexion et lecture de profil utilisateur

  - Accès à l’annuaire en tant qu’utilisateur connecté

  - Lecture des données de l’annuaire

  - Envoi des informations d’appareil à Intune

- Informations d’identification d’administrateur pour accéder à la console Check Point SandBlast Mobile MTD.

### <a name="check-point-sandblast-app-authorization"></a>Autorisation de l’application Check Point SandBlast

Le processus d’autorisation de l’application Check Point SandBlast se compose des étapes suivantes :

- Autoriser le service Check Point SandBlast Mobile à communiquer à Intune des informations relatives à l’état d’intégrité des appareils.

- Synchroniser CheckPoint SandBlast Mobile avec l’appartenance au groupe d’inscriptions Azure AD pour remplir sa base de données d’appareils.

- Autoriser la console d’administration Check SandBlast à utiliser l’authentification unique (SSO) Azure AD.

- Autoriser l’application Check Point SandBlast Mobile à se connecter en utilisant l’authentification unique Azure AD.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>Pour configurer l’intégration de Check Point SandBlast Mobile

1. Accédez à la [console Check Point SandBlast Mobile MTD](https://intune-4.eu1.locsec.net/) et connectez-vous avec vos informations d’identification.

2. Cliquez sur l’onglet **Settings** (Paramètres).

3. Choisissez **Device management** (Gestion d’appareils), puis **Settings** (Paramètres.

4. Choisissez **Microsoft Intune** dans la liste déroulante **MDM Service** (Service MDM).

5. Après avoir défini Microsoft Intune comme service MDM, la fenêtre **Microsoft Intune Configuration** (Configuration de Microsoft Intune) s’affiche. Choisissez **Add to my organization** (Ajouter à mon organisation) pour chaque plateforme d’appareils (iOS, Android et Windows) pour autoriser Check Point SandBlast Mobile à communiquer avec Intune et Azure AD.

    ![Image montrant la configuration de Check Point MTD avec Intune](./media/checkpoint-sandblast-mobile-mtd-connector-integration/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > Vous devez ajouter toutes les plateformes d’appareils pour passer à l’étape suivante.

6. Choisissez **Accept** (Accepter) pour autoriser l’application Check Point SandBlast Mobile à communiquer avec Intune et Azure Active Directory.

7. Une fois que vous avez activé toutes les plateformes d’appareils, vous devez entrer le groupe de sécurité Azure AD.

8. Choisissez **Verify** (Vérifier). Une fois que le groupe de sécurité Azure AD a été vérifié, choisissez **Save** (Enregistrer).

## <a name="next-steps"></a>Étapes suivantes

- [Configurer les applications Check Point SandBlast Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)
