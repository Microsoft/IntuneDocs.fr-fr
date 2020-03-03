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
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 257b15879f6df5763c407904a2c2b46319d64fb7
ms.sourcegitcommit: cd90650c339795d44702e9dcd0b9679a7b438bb2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473734"
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

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

Pour une vue d’ensemble des avantages, des scénarios et des prérequis d’Autopilot, consultez [Vue d’ensemble de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Prérequis
- [Configurer l’inscription automatique de Windows](../quickstart-setup-auto-enrollment.md)
- [Abonnement à Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Ajouter des appareils

La première étape de la configuration de Windows Autopilot consiste à ajouter les appareils Windows à Intune. Il vous suffit de créer un fichier CSV et de l’importer dans Intune.

1. Dans n’importe quel éditeur de texte, créez une liste séparée par des virgules (CSV) des valeurs qui identifient les appareils Windows. Utilisez le format suivant :
    
    *numéro-série*, *id-produit-windows*, *hachage-matériel*, *étiquette-groupe-facultative*
    
    Les trois premiers éléments sont obligatoires, mais l’étiquette de groupe (auparavant « ID de commande ») est facultative.

2. Enregistrez le fichier CSV.

3. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Appareils** > **Windows** > **Appareils** (sous **Programme de déploiement Windows Autopilot** > **Importer**.

    ![Capture d’écran d’appareils Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

4. Sous **Ajouter des appareils Windows Autopilot**, recherchez le fichier CSV que vous avez enregistré.

    ![Capture d’écran de l’ajout d’appareils Windows Autopilot](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. Choisissez **Importer** pour démarrer l’importation des informations sur les appareils. L’importation peut prendre plusieurs minutes.

4. Une fois l’importation terminée, choisissez **Appareils** > **Windows** > **Inscription Windows** > **Appareils** (sous **Programme de déploiement Windows Autopilot** > **Synchroniser**). Un message indique que la synchronisation est en cours. Le processus peut durer quelques minutes, en fonction du nombre d’appareils que vous synchronisez.

5. Actualisez la vue pour voir les nouveaux appareils.

## <a name="create-an-autopilot-device-group"></a>Créer un groupe d’appareils Autopilot

Ensuite, vous allez créer un groupe d’appareils et placer dedans les appareils Autopilot que vous venez de charger.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Groupes** > **Nouveau groupe**.
2. Dans le panneau **Groupe** :
    1. Pour **Type de groupe**, choisissez **Sécurité**.
    2. Pour **Nom de groupe**, entrez *Groupe Autopilot*. Pour **Description du groupe**, entrez *Groupe de test pour les appareils Autopilot*.
    3. Pour **Type d’appartenance**, choisissez **Affecté**.
3. Dans le panneau **Groupe**, choisissez **Membres** et ajoutez les appareils Autopilot au groupe. Les appareils Autopilot qui ne sont pas encore inscrits sont ceux dont le nom correspond au numéro de série de l’appareil.
4. Choisissez **Créer**.  

## <a name="create-an-autopilot-deployment-profile"></a>Créer un profil de déploiement Autopilot

Après avoir créé un groupe d’appareils, vous devez créer un profil de déploiement afin de pouvoir configurer les appareils Autopilot.

1. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Windows** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil**.
2. Dans la page **De base**, pour **Nom**, entrez *Profil AutoPilot*. Pour **Description**, entrez *Profil de test pour les appareils Autopilot*.
3. Définissez **Convertir tous les appareils ciblés vers Autopilot** sur **Oui**. Ce paramètre permet de s’assurer que tous les appareils dans la liste sont inscrits auprès du service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures.
4. Sélectionnez **Suivant**.
5. Sur la page **Mode out-of-box experience (OOBE)**, pour **Mode de déploiement**, choisissez **Géré par l’utilisateur**. Les appareils avec ce profil sont associés à l’utilisateur qui inscrit l’appareil. Les informations d’identification de l’utilisateur sont obligatoires pour l’inscription de l’appareil.
6. Dans la zone **Joindre à Azure AD en tant que**, sélectionnez **Joint à Azure AD**.
7. Configurez les options suivantes et laissez les autres sur la valeur par défaut :
    - **Contrat de Licence Utilisateur Final (CLUF)**  : **Masquer**
    - **Paramètres de confidentialité** : **Afficher**
    - **Type de compte d’utilisateur** : **Standard**
8. Sélectionnez **Suivant**.
9. Sur la page **Affectations**, choisissez **Groupes sélectionnés** pour **Affecter à**.
10. Choisissez **Sélectionner les groupes à inclure**, puis **Groupe Autopilot**.
11. Sélectionnez **Suivant**.
12. Sur la page **Réviser + créer**, choisissez **Créer** pour créer le profil.

## <a name="distribute-devices-to-users"></a>Distribuer des appareils aux utilisateurs

Vous pouvez désormais distribuer les appareils Windows à vos utilisateurs. Lorsqu’ils se connectent pour la première fois, le système Autopilot inscrira et configurera automatiquement les appareils. 

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous ne voulez plus utiliser les appareils Autopilot, vous pouvez les supprimer.

1. Si les appareils sont inscrits dans Intune, vous devez d’abord [les supprimer dans le portail Azure Active Directory](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Dans le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Appareils** > **Windows** > **Inscription Windows** > **Appareils** (sous **Programme de déploiement Windows Autopilot**).

3. Sélectionnez les appareils que vous souhaitez supprimer, puis choisissez **Supprimer**.

4. Confirmez la suppression en choisissant **Oui**. La suppression peut prendre quelques minutes.

## <a name="next-steps"></a>Étapes suivantes

Vous trouverez plus d’informations sur les autres options disponibles pour Windows Autopilot.

> [!div class="nextstepaction"]
> [Article détaillé sur l’inscription Autopilot](enrollment-autopilot.md)


