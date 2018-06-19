---
title: Synchroniser manuellement votre appareil Windows | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: aa556b2939986759aa92e63750fd161c05afbc38
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048017"
---
# <a name="sync-your-windows-device-manually"></a>Synchroniser votre appareil Windows manuellement

Quand la vitesse d’installation des applications est loin d’être idéale, lancez une synchronisation manuelle de l’appareil. Les synchronisations manuelles forcent votre appareil à se connecter à Intune pour obtenir les dernières mises à jour et communications. La vitesse d’installation peut augmenter une fois la synchronisation de l’appareil terminée.

Intune prend en charge la synchronisation manuelle à partir de l’application Portail d’entreprise et de l’application Paramètres de l’appareil. 

La fonctionnalité de l’application Portail d’entreprise est prise en charge sur les appareils Windows 10 exécutant Creators Update (1703) ou version ultérieure. 
* [Synchroniser à partir de l’application Portail d’entreprise](#Sync-from-Company-Portal-app-for-Windows)  

Tous les appareils Windows peuvent être synchronisés à partir de l’application Paramètres de l’appareil, notamment :

* [Windows 10 Desktop](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-from-company-portal-app-for-windows"></a>Synchroniser à partir de l’application Portail d’entreprise pour Windows
Effectuez les étapes suivantes pour synchroniser manuellement n’importe quel appareil Windows 10 exécutant Creators Update (1703) ou version ultérieure.

1.  Ouvrez l'application Portail d'entreprise sur votre appareil.

2.  Sélectionnez **Paramètres** > **Synchroniser**.

    ![Capture d’écran de la page d’accueil de l’application Portail d’entreprise avec Paramètres mis en surbrillance](./media/RS1_homePage_settings_04.png)  
    
    ![Capture d’écran de la page de paramètres de l’application Portail d’entreprise avec Synchroniser mis en surbrillance](./media/RS1_settingspage_sync05.png)    

## <a name="sync-from-settings-app"></a>Synchroniser à partir de l’application Paramètres 
Effectuez ces étapes pour synchroniser manuellement vos appareils Microsoft HoloLens, Windows 10 Desktop, Windows 10 Mobile ou Windows Phone 8.1 à partir de l’application Paramètres.

### <a name="windows-10-desktop"></a>Windows 10 Desktop
1. Sur votre appareil, sélectionnez **Démarrer** > **Paramètres**.

2. Sélectionnez **Comptes**.

    ![Choix de Comptes dans la page Paramètres](./media/win10pc-sync-2-settings-accounts.png)  

3. Il existe plusieurs versions de Windows 10 pour les ordinateurs de bureau. Comparez votre écran aux captures d’écran ci-dessous pour déterminer l’ensemble des étapes à suivre. 

    * Si votre écran indique **Accès professionnel ou scolaire**, passez aux étapes décrites dans [Accès professionnel ou scolaire](#access-work-or-school).

    ![Option Accès professionnel ou scolaire dans l’application Paramètres](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * Si votre écran indique **Accès professionnel**, passez aux étapes décrites dans [Accès professionnel](#work-access).  

    ![Choix d’accès professionnel comme type de compte](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>Étapes pour l’accès professionnel ou scolaire

1. Cliquez sur **Accès professionnel ou scolaire**.

    ![Capture d’écran montrant l’option Accès professionnel ou scolaire](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. Sélectionnez le compte en regard duquel figure une icône de porte-documents. Si vous ne voyez pas ce compte, votre entreprise a peut-être configuré vos paramètres d’une autre manière. Dans ce cas, cliquez sur le compte en regard duquel figure un logo Microsoft.

     ![Choisissez votre nom de compte en regard du porte-documents ou du logo Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Cliquez sur **Informations**. 

4. Cliquez sur **Synchroniser**. 

#### <a name="work-access-steps"></a>Étapes pour l’accès professionnel

1.  Cliquez sur **Accès professionnel**.

    ![Choix d’accès professionnel comme type de compte](./media/win10pc-sync-3-work-access.png)

2. Sous **Inscription à la gestion des appareils**, sélectionnez le nom de votre société.

    ![Choix du nom de la société pour la gestion des appareils](./media/win10pc-sync-4-tap-com-name.png)

3. Cliquez sur **Synchroniser**. Le bouton reste désactivé tant que la synchronisation n’est pas terminée.

    ![Choix du bouton Synchroniser](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. Sur votre appareil, accédez à **Toutes les applications** > **Paramètres** > **Comptes**.

       ![Choix de Comptes dans l’écran Paramètres](./media/win10m-sync-1-settings-accounts.png)

   2. Sélectionnez **Accès professionnel**.

       ![Choix d’accès professionnel comme type de compte](./media/win10m-sync-2-work-access.png)

   3. Sous **Inscription à la gestion des appareils**, sélectionnez le nom de votre société.

       ![Choix du nom de la société pour la gestion des appareils](./media/win10m-sync-3-tap-comp-name.png)

   4. Sélectionnez l’icône **Synchroniser**. Le bouton reste désactivé tant que la synchronisation n’est pas terminée.

       ![Choix de l’icône Synchroniser](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
Ces instructions s’appliquent aux appareils HoloLens exécutant la Mise à jour anniversaire Windows 10 (également appelée RS1). 
1.  Ouvrez l’application Paramètres sur votre appareil.  

2.  Sélectionnez **Comptes** > **Accès professionnel**.  
    ![Capture d’écran de l’application Paramètres HoloLens avec lien Comptes mis en surbrillance](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3.  Sélectionnez votre compte connecté > **Synchroniser**. ![Capture d’écran de l’application Paramètres HoloLens avec bouton Synchroniser mis en surbrillance](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. Accédez à **Toutes les applications** > **Paramètres** > **espace de travail**.

    ![Liste des paramètres](./media/wp81-1-sync-settings-workplace.png)

2. Sélectionnez le nom de votre société.

    ![Choix du nom de la société pour le compte de l’espace de travail](./media/wp81-2-sync-tap-compname.png)

3. Sélectionnez l’icône **Synchroniser**.

    ![Choix de l’icône Synchroniser](./media/wp81-3-sync-tap-sync-button.png)

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://portal.manage.microsoft.com#HelpDeskDialog).
