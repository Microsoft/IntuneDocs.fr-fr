---
title: Tutoriel - Utiliser Autopilot pour inscrire des appareils dans Intune
titleSuffix: Microsoft Intune
description: Dans ce tutoriel, vous allez configurer Windows Autopilot pour inscrire des appareils dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36aa9ad733e2ae5e0f4a292b073fbebd5f5f5f8f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57395980"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Tutoriel : utiliser Autopilot pour inscrire des appareils Windows dans Intune
Windows Autopilot simplifie l’inscription des appareils. Avec Microsoft Intune et Autopilot, vous pouvez donner de nouveaux appareils à vos utilisateurs finaux sans devoir créer, gérer et appliquer des images de système d’exploitation personnalisées. 

Dans ce tutoriel, vous apprendrez à :
> [!div class="checklist"]
> * Ajouter des appareils à Intune
> * Créer un groupe d’appareils Autopilot
> * Créer un profil de déploiement Autopilot
> * Affecter le profil de déploiement Autopilot au groupe d’appareils
> * Distribuer des appareils Windows aux utilisateurs

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

Pour une vue d’ensemble des avantages, des scénarios et des prérequis d’Autopilot, consultez [Vue d’ensemble de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Prérequis
- [Configurer l’inscription automatique de Windows](quickstart-setup-auto-enrollment.md)
- [Abonnement à Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Ajouter des appareils

La première étape de la configuration de Windows Autopilot consiste à ajouter les appareils Windows à Intune. Il vous suffit de créer un fichier CSV et de l’importer dans Intune.

1. Dans n’importe quel éditeur de texte, créez une liste séparée par des virgules (CSV) des valeurs qui identifient les appareils Windows. Utilisez le format suivant :
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-order-id*
    
    Les trois premiers éléments sont obligatoires, mais l’ID de commande est facultatif.

2. Enregistrez le fichier CSV.

3. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > **Importer**.

    ![Capture d’écran d’appareils Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

4. Sous **Ajouter des appareils Windows Autopilot**, recherchez le fichier CSV que vous avez enregistré.

    ![Capture d’écran de l’ajout d’appareils Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

5. Choisissez **Importer** pour démarrer l’importation des informations sur les appareils. L’importation peut prendre plusieurs minutes.

4. Une fois l’importation effectuée, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Windows Autopilot** > **Appareils** > **Synchroniser**. Un message indique que la synchronisation est en cours. Le processus peut durer quelques minutes, en fonction du nombre d’appareils que vous synchronisez.

5. Actualisez la vue pour voir les nouveaux appareils.

## <a name="create-an-autopilot-device-group"></a>Créer un groupe d’appareils Autopilot

Ensuite, vous allez créer un groupe d’appareils et placer dedans les appareils Autopilot que vous venez de charger.

1. Dans [Intune dans le Portail Azure](https://aka.ms/intuneportal), choisissez **Groupes** > **Nouveau groupe**.
2. Dans le panneau **Groupe** :
    1. Pour **Type de groupe**, choisissez **Sécurité**.
    2. Pour **Nom de groupe**, entrez *Groupe Autopilot*. Pour **Description du groupe**, entrez *Groupe de test pour les appareils Autopilot*.
    3. Pour **Type d’appartenance**, choisissez **Affecté**.
3. Dans le panneau **Groupe**, choisissez **Membres** et ajoutez les appareils Autopilot au groupe. Les appareils Autopilot qui ne sont pas encore inscrits sont ceux dont le nom correspond au numéro de série de l’appareil.
4. Choisissez **Créer**.  

## <a name="create-an-autopilot-deployment-profile"></a>Créer un profil de déploiement Autopilot

Après avoir créé un groupe d’appareils, vous devez créer un profil de déploiement afin de pouvoir configurer les appareils Autopilot.

1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil**.
2. Pour **Nom**, entrez *Profil Autopilot*. Pour **Description**, entrez *Profil de test pour les appareils Autopilot*.
3. Définissez **Convertir tous les appareils ciblés vers Autopilot** sur **Oui**. Ce paramètre permet de s’assurer que tous les appareils dans la liste sont inscrits auprès du service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures.
4. Pour **Mode de déploiement**, choisissez **Piloté par l’utilisateur**. Les appareils avec ce profil sont associés à l’utilisateur qui inscrit l’appareil. Les informations d’identification de l’utilisateur sont obligatoires pour l’inscription de l’appareil.
5. Dans la zone **Joindre à Azure AD en tant que**, sélectionnez **Joint à Azure AD**.
6. Choisissez **OOBE (Out-Of-Box Experience)**, configurez les options suivantes et conservez la valeur par défaut des autres options, puis choisissez **Enregistrer** :
    - **Contrat de Licence Utilisateur Final (CLUF)**  : **Masquer**
    - **Paramètres de confidentialité** : **Afficher**
    - **Type de compte d’utilisateur** : **Standard**

6. Choisissez **Créer** pour créer le profil. Le profil de déploiement Autopilot peut désormais être affecté aux appareils.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Affecter un profil de déploiement Autopilot à un groupe d’appareils

Maintenant que le profil de déploiement est créé, vous allez l’affecter au groupe d’appareils.
1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > Choisir un profil.
2. Dans le panneau du profil, choisissez **Affectations**. 
3. Choisissez **Sélectionner des groupes**, puis dans le panneau **Sélectionner des groupes**, choisissez **Groupe Autopilot**, puis **Sélectionner**.

## <a name="distribute-devices-to-users"></a>Distribuer des appareils aux utilisateurs

Vous pouvez désormais distribuer les appareils Windows à vos utilisateurs. Lorsqu’ils se connectent pour la première fois, le système Autopilot inscrira et configurera automatiquement les appareils. 

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous ne souhaitez plus utiliser les appareils Autopilot, vous pouvez les supprimer.

1. Si les appareils sont inscrits dans Intune, vous devez d’abord [les supprimer dans le portail Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Dans [Intune dans le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils**.

3. Sous **Appareils Windows Autopilot**, choisissez les appareils à supprimer, puis choisissez **Supprimer**.

4. Confirmez la suppression en choisissant **Oui**. La suppression peut prendre quelques minutes.

## <a name="next-steps"></a>Étapes suivantes

Vous trouverez plus d’informations sur les autres options disponibles pour Windows Autopilot.

> [!div class="nextstepaction"]
> [Article détaillé sur l’inscription Autopilot](enrollment-autopilot.md)


