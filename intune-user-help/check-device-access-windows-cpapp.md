---
title: Vérifier l’accès de l’appareil | Microsoft Docs
description: Vérifiez l’accès de l’appareil pour déterminer si votre appareil est conforme aux exigences de l’organisation, et s’il peut accéder aux ressources professionnelles ou scolaires.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49075fd750ade6aaa412d551f4177822b52ce7f2
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490109"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Vérifier l’accès de l’appareil à partir de l’application Portail d’entreprise pour Windows

Vérifiez que votre appareil a accès aux ressources professionnelles ou scolaires. 

Les organisations imposent certaines exigences, telles que le chiffrement et des limites de mot de passe, afin de s’assurer que seuls les appareils sécurisés et approuvés accèdent à leurs données. Les appareils gérés doivent toujours remplir ces exigences pour pouvoir accéder aux ressources de l’organisation.

L’action **Vérifier l’accès** évalue les paramètres et l’état d’accès de votre appareil. La page **Détails de l’appareil** affiche les paramètres que vous devez changer pour récupérer l’accès. 

Effectuez les étapes décrites dans cet article afin de vérifier l’accès de votre appareil à partir de l’application Portail d’entreprise pour Windows.  

## <a name="check-access-from-device-details-page"></a>Vérifier l’accès à partir de la page Détails de l’appareil  
1. Ouvrez l’application Portail d’entreprise pour Windows et accédez à **Mes appareils**.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page d’accueil, avec la section Mes appareils mise en évidence.](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Sélectionnez un appareil.  
3. Dans la page **Détails de l’appareil**, sélectionnez **Vérifier l’accès**. L’application synchronise votre appareil avec les exigences et vérifications en vigueur dans votre organisation, afin de s’assurer de la conformité de votre appareil. Cette vérification peut prendre plusieurs minutes.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec le bouton Vérifier l’accès mis en évidence.](./media/1809_CheckAccess_Checking_Status.png) 

4. Examinez l’état mis à jour. Il indique que votre appareil **peut accéder aux ressources de votre organisation** ou **ne peut pas accéder aux ressources de votre organisation**.  

   ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec la section État mise en évidence.](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Si votre appareil ne peut pas accéder aux ressources, consultez l’alerte en haut de la page. Cliquez sur **Plus** pour développer les détails. Cliquez sur **Moins** pour les réduire.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec l’alerte en haut de la page mise en évidence.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. S’il y a lieu, le message affiche des liens et des actions de correction supplémentaires pour vous aider à résoudre le problème. Sélectionnez une ou plusieurs de ces options pour commencer immédiatement les étapes de résolution. Les actions Résoudre, Synchroniser et Contacter le service informatique (décrites ci-dessous) sont visibles uniquement si vous utilisez Portail d’entreprise sur l’appareil vérifié.  

     * L’action **Comment résoudre ce problème** ouvre un article d’aide pertinent, le cas échéant.  
     * L’action **Résoudre** vous redirige vers le paramètre concerné sur votre appareil.  
     * L’action **Synchroniser** évalue votre appareil afin de s’assurer de sa conformité aux exigences de votre organisation.  
     * L’action **Contacter le service informatique** vous redirige vers la page de coordonnées de votre support informatique.   
 
6. Une fois que vous avez changé les paramètres nécessaires, cliquez sur **Vérifier l’accès** pour confirmer l’état de votre appareil.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec la section État mise en évidence.](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Vérifier l’accès à partir du menu contextuel de l’appareil  
1. Ouvrez l’application Portail d’entreprise pour Windows et accédez à **Mes appareils**.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page d’accueil, avec la section Mes appareils mise en évidence.](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Appuyez de façon prolongée sur l’appareil, ou cliquez dessus avec le bouton droit, pour ouvrir le [menu contextuel](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus) associé.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page d’accueil. Le menu contextuel de l’appareil est visible dans la section **Mes appareils** de la page, et contient les actions « Renommer », « Supprimer » et « Vérifier l’accès ».](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Sélectionnez **Vérifier l’accès**. L’application synchronise votre appareil avec les exigences et vérifications en vigueur dans votre organisation, afin de s’assurer de la conformité de votre appareil. Cette vérification peut prendre plusieurs minutes.  
 
4. Un message s’affiche sous l’appareil pour vous indiquer si votre appareil **peut accéder aux ressources de l’entreprise** ou **ne peut pas accéder aux ressources de l’entreprise**. 

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec la section État mise en évidence.](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Si votre appareil ne peut pas accéder aux ressources, sélectionnez-le.  
6. Dans la page **Détails de l’appareil**, consultez l’alerte affichée en haut. Cliquez sur **Plus** pour développer les détails. Cliquez sur **Moins** pour les réduire.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec l’alerte en haut de la page mise en évidence.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. S’il y a lieu, le message affiche des liens et des actions de correction supplémentaires pour vous aider à résoudre le problème. Sélectionnez une ou plusieurs de ces options pour commencer immédiatement les étapes de résolution. Les actions Résoudre, Synchroniser et Contacter le service informatique (décrites ci-dessous) sont visibles uniquement si vous utilisez Portail d’entreprise sur l’appareil vérifié.  

     * L’action **Comment résoudre ce problème** ouvre un article d’aide pertinent, le cas échéant.  
     * L’action **Résoudre** vous redirige vers le paramètre concerné sur votre appareil.  
     * L’action **Synchroniser** évalue votre appareil afin de s’assurer de sa conformité aux exigences de votre organisation.  
     * L’action **Contacter le service informatique** vous redirige vers la page de coordonnées de votre support informatique.    

7. Une fois que vous avez changé les paramètres nécessaires, cliquez sur **Vérifier l’accès** en bas de la page.  

    ![Exemple de capture d’écran de l’application Portail d’entreprise pour Windows, page Détails de l’appareil, avec l’action Vérifier l’accès mise en évidence.](./media/1809_CheckAccess_Device_details_button.png) 


Besoin d'aide ? Recherchez les coordonnées du support de votre entreprise sur le [site web Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
