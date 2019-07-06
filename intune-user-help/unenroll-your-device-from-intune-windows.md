---
title: Supprimer votre appareil Windows de la gestion Intune
description: Décrit comment supprimer un appareil Windows de la gestion Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50833b33583dcc1b49eb9009995b8ccd6c79e1f0
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546643"
---
# <a name="remove-your-windows-device-from-management"></a>Supprimer votre appareil Windows de la gestion

Supprimez un appareil Windows inscrit de la gestion quand vous ne devez ou ne voulez plus :  
* Utiliser votre appareil dans un cadre professionnel ou scolaire. 
* Accéder à vos e-mails, applications ou autres ressources professionnelles ou scolaires.

Après l’annulation de l’inscription de l’appareil, vous n’avez plus accès aux ressources professionnelles ou scolaires à partir de cet appareil. Vous pouvez supprimer les appareils Windows suivants de la gestion.  
* Appareils Windows 10 
* Ordinateurs Windows 8.1
* Téléphones Windows 8.1
 
Pour plus d’informations sur les conséquences de la suppression de votre appareil de la gestion, consultez [Que se passe-t-il quand vous supprimez votre appareil d’Intune ?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).  

## <a name="remove-your-windows-10-device"></a>Supprimer votre appareil Windows 10
Pour supprimer un appareil Windows 10 de la gestion, effectuez les étapes suivantes.

### <a name="remove-in-company-portal-app-home-page"></a>Suppression à partir de la page **d’accueil** dans l’application Portail d’entreprise  

1. Ouvrez l'application Portail d'entreprise.
2. Dans la **page d’accueil**, accédez à la section **Mes appareils**.
3. Sélectionnez l’appareil à supprimer.
3. En haut à droite de la page d’application, sélectionnez l’icône **Voir plus**.
4. Sélectionnez **Supprimer**. 
5. Pour confirmer la suppression de l’appareil, sélectionnez **Supprimer**.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Suppression à partir du menu contextuel de l’appareil dans l’application Portail d’entreprise  

1. Ouvrez l’application Portail d’entreprise et accédez à **Mes appareils**.

    ![Exemple de capture d’écran de la page d’accueil de l’application Portail d’entreprise pour Windows, avec la section Mes appareils mise en surbrillance.](./media/1809_CheckAccess_Context_Select_Device.png)

2. Appuyez de façon prolongée sur l’appareil, ou cliquez dessus avec le bouton droit, pour ouvrir le [menu contextuel](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus) associé.  

3. Sélectionnez **Supprimer**.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page d’accueil. Le menu contextuel de l’appareil est visible dans la section **Mes appareils** de la page, et contient les actions « Renommer », « Supprimer » et « Vérifier l’accès ».](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. Dans le message de confirmation, cliquez sur **En savoir plus** pour obtenir des informations sur le changement de vos conditions d’accès aux ressources professionnelles ou scolaires. Pour confirmer la suppression de l’appareil, sélectionnez **Supprimer**.   

     ![Exemple de capture d’écran de la page d’accueil de l’application Portail d’entreprise pour Windows. Dans le champ Renommer qui s’affiche sur l’appareil, l’utilisateur peut taper un nouveau nom, puis cliquer sur Renommer ou Annuler.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>Suppression dans l’application Paramètres de l’appareil
1. Ouvrez l’application Paramètres. 
2. Accédez à **Comptes** > **Accès scolaire ou professionnel**.
3. Sélectionnez le compte connecté que vous souhaitez supprimer > **Déconnecter**.
4. Pour confirmer la suppression de l’appareil, sélectionnez **Oui**.

## <a name="remove-your-windows-81-computer"></a>Supprimer votre ordinateur Windows 8.1
Pour supprimer un ordinateur Windows 8.1 d’Intune, effectuez les étapes suivantes.

1. Accédez à **Paramètres du PC** > **Réseau** > **Espace de travail**.
2. Sous **Jonction d’espace de travail**, sélectionnez **Quitter**.
3. Sous **Activer la gestion des appareils**, sélectionnez **Désactiver**.
4. Dans la fenêtre contextuelle qui s’ouvre, sélectionnez **Désactiver**.

## <a name="remove-your-windows-81-phone"></a>Supprimer votre téléphone Windows 8.1
Pour supprimer un téléphone Windows 8.1 d’Intune, effectuez les étapes suivantes.

1. Accédez à **Paramètres** > **Espace de travail**.
2. Appuyez sur le compte Espace de travail que vous voulez désinscrire.
3. Appuyez sur **Supprimer** dans le bas de l’écran.
4. Dans la boîte de dialogue **Supprimer le compte**, appuyez sur **Supprimer**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Suppression de vos informations personnelles après la suppression du portail d’entreprise  

Il existe deux types de données que stocke les le portail d’entreprise sur votre appareil Windows :

- **Journaux de diagnostic** : données d’activité d’application standard collectées par Microsoft. Elles sont automatiquement effacées quand vous désinstallez l’application Portail d’entreprise. Les données d’activité de l’application portent par exemple sur la durée pendant laquelle l’application a été ouverte, ou sur d’éventuels plantages.
- **Cache d’application** : fichiers de prise en charge nécessaires au fonctionnement de l’application, comme les icônes et les paramètres.

Pour supprimer les journaux et le cache stockés, effectuez une des actions suivantes :

* [Désinstallez l’application Portail d’entreprise](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs). 

* Réinitialisez l’application Portail d’entreprise. Ouvrez l’application **Paramètres** et sélectionnez > **Applications** > **Portail d’entreprise** > **Options avancées** > **Réinitialiser**. 

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
