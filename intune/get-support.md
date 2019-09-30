---
title: Comment obtenir un support technique pour Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenez du support en ligne et par téléphone pour les abonnements d’essai gratuit et payants de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26ef0da99b3d87a87ec58dea9e4fbd6dff9abb6c
ms.sourcegitcommit: bc3450fc7f19006b500edf5b395c01559b483ea4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "71239101"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Comment obtenir un support technique pour Microsoft Intune  

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]  
  
Microsoft fournit un support technique global, en avant-vente, pour la facturation et l’abonnement pour Microsoft Intune. Un support technique est disponible en ligne et par téléphone pour les abonnements payants et d’évaluation. Le support technique en ligne est disponible en anglais et japonais. Le support par téléphone et le support à la facturation en ligne sont disponibles dans d’autres langues.

En tant qu’administrateur informatique, vous pouvez utiliser l’option **Aide et support** afin de créer un ticket de support en ligne pour Intune, à partir du portail Microsoft Azure. Pour que vous puissiez créer et gérer un incident de support, votre compte doit avoir un rôle Azure Active Directory (Azure AD) qui inclut l’*action* **microsoft.office365.supportTickets/tickets/manage**. Pour plus d’informations sur les rôles Azure AD et les autorisations nécessaires pour créer un ticket de support, consultez la section relative aux [rôles d’administration dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Pour obtenir un support technique sur les produits tiers qui fonctionnent avec Intune (comme Saaswedo, Cisco ou Lookout), contactez d’abord le fournisseur du produit. Avant d’ouvrir un incident auprès du support Intune, vérifiez que vous avez correctement configuré l’autre produit.
>
> Pour plus d’informations sur la résolution des problèmes liés à Microsoft Intune, consultez la [section de résolution des problèmes](help-desk-operators.md) dans la documentation d’Intune.

## <a name="known-issues-for-creating-support-incidents"></a>Problèmes connus liés à la création d’incidents de support  

Si votre compte dispose des autorisations requises, mais ne parvient pas à accéder à la fonction Aide et support, ou à créer ou gérer un incident de support, passez en revue les problèmes connus suivants et leur résolution :  
- Jeton utilisateur périmé pour votre compte. Pour résoudre ce problème, déconnectez-vous de toutes les sessions de console actives, reconnectez-vous, puis tentez de créer ou gérer un incident de support. 
- Plusieurs sessions actives. Si vous êtes connecté avec plusieurs utilisateurs ou sessions, déconnectez-vous de toutes les consoles, sauf une. Ensuite, avec une seule session active, essayez de créer ou gérer un incident de support.

Actions supplémentaires qui peuvent être nécessaires pour résoudre les problèmes d’accès :
- Nettoyez tous les cookies de votre session de navigateur active, et recommencez la création ou la gestion d’un incident de support.
- Utilisez une session de navigation InPrivate pour vous connecter à Intune, puis essayez de créer ou de gérer un incident de support.  

Si ces solutions de contournement ne vous aident pas, accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et créez un ticket de support à partir de là. Nous travaillons actuellement à la création d’un correctif qui sera disponible à la fin de l’été.  

## <a name="help-and-support-experience"></a>Expérience Aide et support  

L’expérience Aide et support pour Intune est disponible sur le [portail de gestion des appareils Microsoft 365](https://devicemanagement.microsoft.com) et dans tous les panneaux (ou pages) du portail Azure sous Intune. 

![Panneaux Intune](./media/get-support/intune-blades.png)


:’expérience *Aide et support* est similaire à celle du [Centre d’administration Microsoft 365](https://admin.microsoft.com/) et remplace l’expérience *Aide + support* précédente, qui demeure pour d’autres services dans Azure. 

Pour accéder à Aide et support, utilisez les options suivantes :  
- **Tableau de bord Gestion des appareils** :
  - Une fois que vous avez sélectionné une zone de fonctionnalités pour Intune, sélectionnez l’option **Aide et support**.
  - À partir de n’importe quel nœud dans le portail de gestion des appareils, sélectionnez l’icône **?** en haut à droite dans le portail, puis utilisez la liste déroulante pour sélectionner le service pour lequel vous souhaitez obtenir de l’aide. L’icône **?** dans le portail de gestion des appareils prend en charge plusieurs services, et vous devez sélectionner le service spécifique pour lequel vous souhaitez obtenir de l’aide.  

    ![Sélectionnez votre service](./media/get-support/select-a-service.png)

    Après avoir sélectionné un service, vous voyez la page *Aide et support* pour ce service, où vous pouvez alors [spécifier des détails](#specify-details-about-an-issue) sur le problème spécifique pour lequel vous souhaitez obtenir de l’aide.  

    Si les résultats de votre recherche ne semblent pas correspondre aux attentes de votre service, vérifiez que le service approprié a été sélectionné. La sélection du service apparaît juste après *Aide et support*.  Si le service approprié n’a pas été sélectionné, cliquez sur *Sélectionner un service* pour revenir à la liste déroulante de sélection du service.   

    ![Confirmez votre service](./media/get-support/confirm-your-service-selection.png) 


- **Dans le portail Azure :**
  - Sélectionner **Aide et support** dans un panneau ou une page Intune

  Dans le portail Azure, si vous sélectionnez l’icône **?** en haut à droite ou **Aide + support** dans le volet de navigation de gauche, vous ouvrez *Aide + support* pour Azure. À partir d’*Aide + support* Azure, vous ne pouvez pas ouvrir directement un incident de support Intune, mais vous pouvez accéder à la page *Aide et support* Azure en procédant comme suit : 
  1. Sélectionner une nouvelle demande de support.
  2. Pour le type de problème, spécifiez technique.
  3. Pour le service, spécifiez Microsoft Intune.
  4. Sélectionnez le lien page Aide et support Intune.

> [!NOTE]  
> Si votre instance d’Intune est hébergée sur le cloud de la communauté du secteur public (GCC), également connu en tant que cloud souverain comme Azure Government, consultez Support Intune pour le Cloud de la communauté du secteur public plus loin dans cet article. L’expérience *Aide et support* Intune ne sera disponible sur le GCC que plus tard cette année. 


Lorsque vous ouvrez *Aide et support*, le portail affiche une vue qui varie selon que vous avez ou non des incidents de support actifs, ainsi que des éléments et options supplémentaires lorsque vous bénéficiez du Support Premier :
- **Pas d’incidents de support actifs** : vous voyez la page **Besoin d’aide ?** , comme le montre l’image suivante du tableau de bord Gestion des appareils.  
- **Incidents de support actifs** : vous voyez la page [Tickets de support](#view-support-cases), qui affiche la liste de vos incidents actifs.  
- **Contrat de Support Premier** : Votre expérience est la même qu’avec les deux premières options, même si vous voyez les éléments supplémentaires suivants sur la page Besoin d’aide ? 
  - Après le titre de la page **Besoin d’aide ?** , vous voyez la bannière Support Premier :  
    ![Bannière Support Premier](./media/get-support/premier-banner.png)
  - Dans la section **Obtenir un support** de la page, vous pouvez définir le niveau de **Gravité** initial lorsque vous créez une demande de service par téléphone.


![Tableau de bord de gestion des appareils et page Besoin d’aide ?](./media/get-support/help-support-dashboard.png)

Dans cet affichage, vous pouvez effectuer les actions suivantes :

1. [Spécifier les détails](#specify-details-about-an-issue) du problème spécifique pour lequel vous souhaitez obtenir de l’aide  
2. [Afficher l’aide contextuelle](#view-context-sensitive-help) et les solutions associées en fonction des informations que vous avez spécifiées  
3. [Obtenir un support](#get-support) par e-mail ou par téléphone  
4. [Afficher les incidents](#view-support-cases) nécessitant un support, que vous avez ouverts à l’aide de ce nouveau flux de travail  

### <a name="specify-details-about-an-issue"></a>Spécifier les détails d’un problème 

Quand vous ouvrez Aide et support depuis un emplacement pris en charge par la nouvelle expérience, la page **Besoin d’aide ?** s’ouvre. Dans cette page, vous pouvez spécifier les détails relatifs à un problème. Quand vous entrez les détails, la console propose des requêtes courantes basées sur vos mots clés. Sélectionnez l’un des choix proposés, ou indiquez votre propre description du problème. Si vous entrez votre propre description, sélectionnez **Obtenir de l’aide** pour l’envoyer. Une fois que vous avez envoyé une requête, la console retourne des informations contextuelles pouvant vous aider à résoudre le problème.

Voici des exemples de requêtes que vous pouvez envoyer :
  
- *Impossible de restaurer un appareil iOS*  
- *Impossible de créer une stratégie d’accès conditionnel*  

![Spécifier le problème dans la page Besoin d’aide ?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Afficher une aide contextuelle 

Une fois que vous avez sélectionné un choix proposé, ou que vous avez envoyé votre propre requête, des résultats contextuels apparaissent sous **Afficher les solutions**. Ces résultats incluent à la fois du support autonome spécifique à Intune, et des résultats supplémentaires retournés par une recherche web en fonction des critères de la requête.  
![Afficher les résultats](./media/get-support/view-results.png)

### <a name="get-support"></a>Obtenir un support 

Si le support autonome ou l’aide basée sur le web ne vous aident pas à résoudre le problème, vous pouvez utiliser la console pour ouvrir un incident nécessitant un support par e-mail ou par téléphone.  
Dans la page **Besoin d’aide ?** , sélectionnez l’option à utiliser.  

  > [!NOTE] 
  > Les demandes d’assistance par e-mail ne sont pas disponibles pour tous les locataires.  

- Pour une demande par e-mail, indiquez votre adresse e-mail et, éventuellement, ajoutez des pièces jointes à votre envoi. Sélectionnez **Envoyer** pour ouvrir la demande. 

  ![Demande par e-mail](./media/get-support/email-support.png)
  
- Pour une demande par téléphone, indiquez votre numéro de téléphone. Vous pouvez éventuellement inclure votre adresse e-mail et ajouter des pièces jointes à votre envoi. Sélectionnez M’appeler pour envoyer la demande.  



   ![Demande par téléphone](./media/get-support/phone-support.png)

**Support Premier** :  
si vous avez un contrat de Support Premier, vous disposez des mêmes options pour créer un incident de support téléphonique. Vous pouvez également spécifier la **Gravité** pour le rappel de support et choisir de créer le ticket de support en fonction de votre contrat stratégique.  

![Options de Support Premier](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Afficher les incidents nécessitant un support  

Sélectionnez le bouton d’historique pour voir les incidents que vous avez créés pour obtenir un support.  

![Afficher les incidents nécessitant un support](./media/get-support/view-support-tickets.png)

- Seuls les incidents de support que vous ouvrez à l’aide du nouveau flux de travail sont visibles depuis ce flux de travail. Pour les consulter, utilisez la vue Aide et support depuis la console Gestion des appareils ou depuis un panneau Intune du portail Azure. Ces incidents ont des numéros dont la longueur est de huit chiffres. Vous pouvez également voir ces incidents à partir du Centre d’administration Microsoft 365.  

- Les incidents que vous avez ouverts quand vous n’utilisiez pas l’expérience Aide et support d’Intune restent inchangés. Pour les consulter, vous devez utiliser une vue Aide et support qui ne fait pas partie de l’expérience Intune ou du tableau de bord Gestion des appareils. Ces incidents ont des numéros qui commencent par **117** ou **118**, et dont la longueur est de 15 chiffres. Vous pouvez les afficher :

    1. Connectez-vous à Azure (<https://portal.azure.com>) à l’aide de vos informations d’identification d’administrateur Intune, sélectionnez *?* en haut à droite du portail, puis sélectionnez *Aide + support* pour accéder à la page [Aide + support Azure](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. Dans la page **Aide + support**, vous pouvez afficher la liste des **Demandes de support récentes** et les sélectionner pour afficher des informations supplémentaires.
 

## <a name="azure-help--support-experience"></a>Expérience Aide et support Azure 

Lorsque vous utilisez le volet de navigation gauche **Help + support** ou l’option **?** en haut à droite dans le portail Azure, vous ouvrez l’expérience Aide + support Azure, qui est différente de l’expérience Aide et support Intune.  

Depuis avril 2019, vous ne pouvez pas accéder à l’expérience *Aide + support* Azure pour obtenir de l’aide sur Intune, sauf si votre abonnement se trouve sur le cloud de la communauté du secteur public (GCC).  

Si votre instance d’Intune ne s’exécute pas sur GCC, la navigation dans *Aide + support* Azure vous redirige vers l’expérience *Aide et support* Intune pour créer et gérer des incidents de support.  


## <a name="intune-support-for-government-compute-cloud"></a>Support Intune pour le cloud de la communauté du secteur public  

Lorsque votre abonnement Intune est hébergé sur le cloud de la communauté du secteur public (GCC), également connu en tant que cloud souverain comme Azure Government, vous n’avez pas encore accès à la nouvelle expérience Aide et support Intune.  À la place, utilisez les informations suivantes pour obtenir un support pour Intune. 


### <a name="create-an-online-support-ticket"></a>Créer un ticket de support en ligne 

>[!IMPORTANT]    
> Étant donné qu’*Aide et support* passe à un nouveau système qui n’est pas encore disponible pour le GCC, lorsque vous créez un incident de support, le portail identifie un cas de support qui utilise un numéro d’identification à 15 chiffres. Lorsque le cas à 15 chiffres est créé, un miroir de ce cas est créé afin d’être utilisé par le support Microsoft. Ce cas de mise en miroir est créé dans un nouveau système de support, utilise un ID de cas à 8 chiffres et est utilisé par les services de support pour assurer le suivi de l’ensemble du travail et des communications pour votre incident de support. Peu après la création de votre cas à 15 chiffres, vous recevrez un e-mail qui identifie le numéro à 8 chiffres du cas de support mis en miroir utilisé par les services de support technique.  
> 
> Prenez en charge le travail personnel et communiquez à l’aide du cas de support à 8 chiffres, et utilisez uniquement le dossier de support à 8 chiffres pour consigner les communications et suivre la progression des incidents. Pour cette raison, vous recevez des mises à jour par e-mail de ce cas de support à 8 chiffres qui servent d’enregistrement de suivi de votre cas. Aucun détail n’est consigné dans l’incident de support à 15 chiffres. Lorsque le support se termine et que le cas de support à 8 chiffres se ferme, cet État est reflété par le cas de support à 15 chiffres que vous pouvez afficher dans le portail Azure.  Aucune autre mise à jour ou modification d’état ne doit être attendue dans le cas d’un support à 15 chiffres.  
> 
> Lorsque les transitions entre les outils de support se termineront plus tard cette année, l’expérience de support Intune hébergée sur le cloud pour le secteur public ressemblera à l’expérience par défaut *Aide et support* actuellement disponible pour les abonnements Intune hébergés sur le cloud public.  


1. Connectez-vous au Portail Azure (<https://portal.azure.com>) à l’aide de vos informations d’identification d’administrateur Intune, sélectionnez **?** en haut à droite du portail, puis sélectionnez **Aide + support** pour accéder à la page [Aide + support Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Image du lien point d’interrogation avec lien Aide + support entouré](./media/azure-get-support.png)

2. Dans la page **Aide + support** d’Azure, sélectionnez **Nouvelle demande de support**.

   ![Image du lien Nouvelle demande de support mis en surbrillance sur la page Aide et support](media/azure-support-ticket-link.png)

3. Dans l’onglet **Fonctions de base**, pour la plupart des questions de support technique Intune, choisissez les options suivantes :
   - **Type de problème** : **Technique**
   - **Abonnement** : <*votre abonnement*>
   - **Service** : **Microsoft Intune**
   - **Type de problème** : Choisissez votre type de problème dans le menu déroulant.
   - **Sous-type de problème** : Choisissez le sous-type de problème dans le menu déroulant.
   - **Objet** : Décrivez brièvement le problème pour lequel vous avez besoin d’aide.

   ![Image de l’onglet Fonctions de base sur la page Aide + support - Nouvelle demande de support](./media/get-support/help-new-support-case-basics.png)

   Choisissez **Suivant : Solutions** pour continuer.
4. Dans l’onglet **Solutions**, passez en revue les étapes recommandées qui peuvent vous aider à résoudre votre problème sans ouvrir de ticket. Si vous souhaitez toujours créer une demande de support après être passé au travers de ces étapes, cliquez sur **Suivant : Détails**.

   ![Image de l’onglet Solutions sur la page Aide + support - Nouvelle demande de support](./media/get-support/help-new-support-case-solutions.png)
5. Dans l’onglet **Détails**, renseignez les détails de votre problème, la méthode de support, vos informations de contact, puis cliquez sur **Suivant : Vérifier + créer**.

   ![Image de l’onglet Détails sur la page Aide + support - Nouvelle demande de support](./media/get-support/help-new-support-case-details.png)
6. Passez en revue les informations, vérifiez qu’elles sont correctes, puis choisissez **Créer** pour envoyer votre demande de support.

   ![Image de l’onglet Vérifier + créer sur la page Nouvelle demande de support](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Si vous avez une question relative à la facturation ou à l’abonnement, vous pouvez ouvrir un incident pour obtenir de l’assistance par l’intermédiaire du [Centre d’administration Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Afficher les demandes de support  

Vous pouvez afficher vos demandes de support à partir du Portail Azure. Cependant, des informations limitées sont disponibles.  Pour afficher vos incidents : 

1. Connectez-vous à Azure (<https://portal.azure.com>) à l’aide de vos informations d’identification d’administrateur Intune, sélectionnez **?** en haut à droite du portail, puis sélectionnez **Aide + support** pour accéder à la page [Aide + support Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. Dans la page **Aide + support**, vous pouvez afficher la liste des **Demandes de support récentes**.

   > [!IMPORTANT]  
   > Les clients du cloud de la communauté du secteur public peuvent uniquement afficher le numéro de cas de support à 15 chiffres et l’état de l’incident. Toutes les communications relatives au cas et le suivi du travail ou les alertes sont envoyés par e-mail et font référence au numéro de cas de support à 8 chiffres créé comme miroir du cas de support ouvert à partir de la console Intune.   

## <a name="additional-resources"></a>Ressources supplémentaires  

- [Support relatif à la gestion de la facturation et des abonnements](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licences en volume](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Résoudre les problèmes d’Intune](help-desk-operators.md)
