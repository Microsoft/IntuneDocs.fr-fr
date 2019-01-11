---
title: Guide pratique pour supprimer un appareil Android d’Intune | Microsoft Docs
description: Supprimer un appareil Android dans Portail d’entreprise Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 75b26e178badbaa7905199eb91490134d2b72ba9
ms.sourcegitcommit: 61ed365f7f8826451c41bcab5e19bef97b5a3c72
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2019
ms.locfileid: "54057336"
---
# <a name="unenroll-your-android-device-from-management"></a>Désinscrire votre appareil Android de la gestion  

Supprimez un appareil Android inscrit afin qu’il ne soit plus géré par votre organisation. Cet article explique comment supprimer l’appareil de l’application Portail d’entreprise. Une fois que vous avez supprimé l’appareil :  

* Il perd l’accès aux ressources et aux données protégées de votre organisation.
* Il n’apparaît plus dans l’application Portail d’entreprise.
* Vous ne pouvez pas installer d’applications à partir de l’application Portail d’entreprise.
* Tous les paramètres qui ont été modifiés sur votre appareil quand vous l’avez ajouté (par exemple la désactivation de l’appareil photo ou l’exigence d’une certaine longueur de mot de passe) ne s’appliquent plus.  

1. Dans l’application Portail d’entreprise, en haut à droite, appuyez sur les trois points verticaux. Le menu Action s’ouvre.

   ![Une image de l’application Portail d’entreprise Android, avec le menu Action ouvert en haut à droite. La nouvelle option « Supprimer le portail d’entreprise » est disponible en tant que troisième option, sous « Mon profil » et « Paramètres », et au-dessus de « Conditions générales », « Aide et commentaires » et « À propos ».](./media/android_remove_cp_menu_action_after_1705.png)

2. Appuyez sur **Supprimer le portail d’entreprise**.  

3. Un message s’affiche, indiquant ce qui se passe une fois votre appareil désinscrit. Appuyez sur **OK** pour confirmer que vous souhaitez supprimer l’appareil de l’application Portail d’entreprise.

   ![Une image de la boîte de dialogue de confirmation, qui est disponible après avoir sélectionné la nouvelle option « Supprimer le portail d’entreprise » dans le menu Action. La boîte de dialogue informe l’utilisateur que « en supprimant le portail d’entreprise, votre appareil ne sera plus géré par le support technique de votre entreprise et pourrait perdre l’accès à la messagerie, aux applications et aux données de l’entreprise ». L’utilisateur doit ensuite confirmer qu’il souhaite supprimer l’application Portail d’entreprise en sélectionnant « Oui ».](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Suppression des données collectées par l’application Portail d’entreprise  

Pour supprimer toutes les données que stocke l’application Portail d’entreprise pour Android sur votre appareil :

-   Effacer les données d’application dans Applications -> Cliquer sur l’application -> bouton « Effacer les données »
-   Supprimer le dossier '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal'

## <a name="uninstall-the-company-portal-app"></a>Désinstaller l’application Portail d’entreprise  
Portail d’entreprise est une application de gestion des appareils. Vous ne pouvez pas la désinstaller tant que vous n’avez pas [désinscrit votre appareil de la gestion](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Une fois cette opération terminée, appuyez sur l’icône de l’application Portail d’entreprise jusqu’à ce que vous voyiez **Désinstaller**. Appuyez sur **Désinstaller** pour supprimer l’application de votre appareil.  

Ou bien, appuyez sur **Paramètres** > **Applications** > **Portail d’entreprise** > **Désinstaller**.  

### <a name="remove-company-portal-app-as-device-administrator"></a>Supprimer l’application Portail d’entreprise en tant qu’administrateur de l’appareil  
En dernier recours, vous pouvez désinstaller l’application sur votre appareil en la supprimant en tant qu’administrateur de l’appareil.  

Si vous utilisez un appareil appartenant à l’entreprise, votre organisation peut exiger que l’application Portail d’entreprise reste toujours installée sur votre appareil. Si vous désinstallez l’application, vous risquez de ne plus pouvoir accéder aux ressources métier protégées (comme la messagerie, les applications, le Wi-Fi ou le VPN) tant que vous ne réinstallez pas l’application. Pour plus d’informations sur l’installation, la mise à jour ou la suppression des applications obligatoires, consultez [Ajouter des applications à Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Effectuez les étapes ci-dessous pour désactiver l’application Portail d’entreprise en tant qu’un administrateur de l’appareil. Les noms réels des paramètres peuvent varier en fonction de votre appareil Android.  

**Étapes Android, option 1** :  
1. Sélectionnez **Paramètres** > **Sécurité** > **Paramètres de sécurité supplémentaires** > **Administrateurs d’appareils**.  
2. Désélectionnez l’option **Portail d’entreprise**.  

**Étapes Android, option 2** :  
1. Sélectionnez **Paramètres** > **Écran de verrouillage et sécurité** > **Autres paramètres de sécurité** > **Applications des administrateurs d’appareils**.  
2. Désélectionnez l’option **Portail d’entreprise**.    

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
