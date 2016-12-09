---
title: "Réinitialiser les données d’applications d’entreprise gérées | Microsoft Intune"
description: "Découvrez comment sélectivement supprimer des données de votre entreprise à partir d’appareils à distance."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d32a66ee283906586e25173e736c02ee8bf23042


---

# <a name="wipe-managed-company-app-data-with-microsoft-intune"></a>Réinitialiser les données d’applications d’entreprise managées avec Microsoft Intune
Lorsqu'un appareil est perdu ou volé, ou si l'employé quitte votre entreprise, vous devez vous assurer que les données de l'application d’entreprise sont supprimées de l'appareil. Mais vous ne voulez peut-être pas supprimer les données personnelles de l’appareil, en particulier si cet appareil appartient à un employé.

Pour supprimer des données d’application d’entreprise de manière sélective, créez une demande de réinitialisation en suivant les étapes indiquées dans cette rubrique. Une fois la demande terminée, les données d’entreprise sont supprimées de l’application dès sa prochaine exécution sur l’appareil.
>[!NOTE]
> Les contacts synchronisés avec le carnet d’adresses natif directement à partir de l’application sont supprimés. Les contacts synchronisés à partir du carnet d’adresses natif vers une autre source externe ne peuvent pas être effacés. Actuellement, ceci s’applique uniquement à l’application Microsoft Outlook.



## <a name="create-a-wipe-request"></a>Créer une demande de réinitialisation

1.  Dans le panneau **Gestion des applications mobiles Intune**, choisissez la vignette **Demandes de réinitialisation**.

    ![Capture d’écran du panneau Gestion des applications mobiles Intune avec vignettes Résumé](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  Choisissez **Nouvelles demandes de réinitialisation**. Le panneau **Nouvelle demande de réinitialisation** s’ouvre.

    ![Capture d'écran du panneau Nouvelle demande de réinitialisation](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  Choisissez **Utilisateur** pour ouvrir le panneau **Utilisateur** et sélectionnez l’utilisateur possédant les données des applications à réinitialiser.

4.  Choisissez **Appareil**.  Cette opération ouvre le panneau **Appareil** qui répertorie tous les appareils associés à l’utilisateur sélectionné.  Sélectionnez l’appareil à réinitialiser.

5.  Vous voilà revenu dans le panneau **Nouvelle demande de réinitialisation**. Choisissez **Ok** pour effectuer une demande de réinitialisation. Le service crée une demande de réinitialisation distincte pour chaque application protégée sur l’appareil et en fait le suivi.


![Capture d'écran de la mosaïque de demande de réinitialisation ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## <a name="monitor-your-wipe-requests"></a>Analyser vos demandes de réinitialisation
La vignette **Demande de réinitialisation** du panneau **Gestion des applications mobiles Intune** propose un rapport de synthèse.  Ce dernier indique l’état général des demandes de réinitialisation, notamment le nombre de demandes en attente et d’échecs. Vous pouvez obtenir d’autres détails en procédant comme suit :

1.  Dans le panneau **Gestion des applications mobiles Intune**, choisissez la vignette **Demande de réinitialisation** pour ouvrir le panneau **Demande de réinitialisation**.

2.  Le panneau **Demande de réinitialisation** affiche la liste de vos demandes regroupées par utilisateurs. Étant donné que le système crée une demande de réinitialisation pour chaque application protégée en cours d’exécution sur l’appareil, vous pouvez voir plusieurs demandes pour un même utilisateur. L’état de la demande de réinitialisation est indiquée : **en attente**, **échec**ou **réussite**.

L’utilisateur doit ouvrir l’application pour que la réinitialisation se produise. Cette opération peut prendre jusqu’à 30 minutes après l’envoi de la demande.

Les réinitialisations en attente sont affichées jusqu’à ce que vous les supprimiez manuellement.  Pour supprimer manuellement une demande de réinitialisation, cliquez dessus avec le bouton droit et sélectionnez Supprimer.

### <a name="see-also"></a>Voir aussi
[Protéger les données d’application à l’aide des stratégies de gestion des applications mobiles](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Utilisation du portail Azure](azure-portal-for-microsoft-intune-mam-policies.md)



<!--HONumber=Dec16_HO2-->


