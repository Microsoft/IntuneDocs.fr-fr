---
title: Comment obtenir un support technique pour Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenez du support en ligne et par téléphone pour les abonnements d’essai gratuit et payants de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/05/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf1e87d40459d194f2c4aa0ff702a137e45504ab
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569751"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Comment obtenir un support technique pour Microsoft Intune

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

Microsoft fournit un support technique global, en avant-vente, pour la facturation et l’abonnement pour Microsoft Intune. Un support technique est disponible en ligne et par téléphone pour les abonnements payants et d’évaluation. Le support technique en ligne est disponible en anglais et japonais. Le support par téléphone et le support à la facturation en ligne sont disponibles dans d’autres langues.

En tant qu’administrateur informatique, vous pouvez utiliser l’option **Aide et support** afin de créer un ticket de support en ligne pour Intune, à partir du portail Microsoft Azure. Pour que vous puissiez créer et gérer un incident de support, votre compte doit posséder un rôle Azure Active Directory (Azure AD) qui inclut l’*action* **microsoft.office365.supportTickets/allEntities/allTasks**. Pour plus d’informations sur les rôles Azure AD et les autorisations nécessaires pour créer un ticket de support, consultez la section relative aux [rôles d’administration dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal). 

**Problèmes connus pour la création d’incidents de support**

Si votre compte dispose des autorisations requises, mais ne parvient pas à accéder à la fonction Aide et support, ou à créer ou gérer un incident de support, passez en revue les problèmes connus suivants et leur résolution :  
- Jeton utilisateur périmé pour votre compte. Pour résoudre ce problème, déconnectez-vous de toutes les sessions de console actives, reconnectez-vous, puis tentez de créer ou gérer un incident de support. 
- Plusieurs sessions actives. Si vous êtes connecté avec plusieurs utilisateurs ou sessions, déconnectez-vous de toutes les consoles, sauf une. Ensuite, avec une seule session active, essayez de créer ou gérer un incident de support.

Actions supplémentaires qui peuvent être nécessaires pour résoudre les problèmes d’accès :
- Nettoyez tous les cookies de votre session de navigateur active, et recommencez la création ou la gestion d’un incident de support.
- Utilisez une session de navigation InPrivate pour vous connecter à Intune, puis essayez de créer ou de gérer un incident de support.  

Si ces solutions de contournement ne vous aident pas, accédez au [Centre d’administration Microsoft 365](https://admin.microsoft.com) et créez un ticket de support à partir de là. Nous travaillons actuellement à la création d’un correctif qui sera disponible à la fin de l’été. 



>[!IMPORTANT]  
> Pour obtenir un support technique sur les produits tiers qui fonctionnent avec Intune (comme Saaswedo, Cisco ou Lookout), contactez d’abord le fournisseur du produit. Avant d’ouvrir un incident auprès du support Intune, vérifiez que vous avez correctement configuré l’autre produit.
>
> Pour plus d’informations sur la résolution des problèmes liés à Microsoft Intune, consultez la [section de résolution des problèmes](help-desk-operators.md) dans la documentation d’Intune.




## <a name="help-and-support-experience"></a>Expérience Aide et support
> [!TIP]   
> Une nouvelle expérience Aide et support est disponible pour tous les clients. Si vous ne la voyez pas sur le vôtre, effacez le cache de votre navigateur et rechargez la page.

L’expérience Aide et support pour Intune est disponible sur le [portail de gestion des appareils Microsoft 365](http://devicemanagement.microsoft.com) et dans tous les panneaux (ou pages) du portail Azure sous Intune. 

![Panneaux Intune](./media/get-support/intune-blades.png)


Cette nouvelle expérience est similaire à celle du [Centre d’administration Microsoft 365](https://admin.microsoft.com/) et remplace l’expérience Aide et support précédente. 

Pour accéder à Aide et support, utilisez les options suivantes :  
- **Tableau de bord Gestion des appareils** :
   - Sélectionner une option disponible pour **Aide et support**
   - Sélectionner l’icône **?** en haut à droite du portail

- **Dans le portail Azure** :
   - Sélectionner **Aide et support** dans un panneau ou une page Intune

   La sélection de l’icône **?** en haut à droite ou d’**Aide + support** dans le volet de navigation de gauche (où que vous soyez dans le portail Azure) ouvre *Aide + support* pour Azure. Pour une expérience optimale, utilisez *Aide et support* à partir du panneau Intune.  

Avec la nouvelle expérience, vous avez accès à la vue **Besoin d’aide ?**, comme le montre l’image suivante du tableau de bord Gestion des appareils :  
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
Dans la page **Besoin d’aide ?**, sélectionnez l’option à utiliser.  

- Pour une demande par e-mail, indiquez votre adresse e-mail et, éventuellement, ajoutez des pièces jointes à votre envoi. Sélectionnez **Envoyer** pour ouvrir la demande.  

  ![Demande par e-mail](./media/get-support/email-support.png)
  
- Pour une demande par téléphone, indiquez votre numéro de téléphone. Vous pouvez éventuellement inclure votre adresse e-mail et ajouter des pièces jointes à votre envoi. Sélectionnez M’appeler pour envoyer la demande.  

   ![Demande par téléphone](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>Afficher les incidents nécessitant un support
Sélectionnez le bouton d’historique pour voir les incidents que vous avez créés pour obtenir un support.  

![Afficher les incidents nécessitant un support](./media/get-support/view-support-tickets.png)

- Seuls les incidents de support que vous ouvrez à l’aide du nouveau flux de travail sont visibles depuis ce flux de travail. Pour les consulter, utilisez la vue Aide et support depuis la console Gestion des appareils ou depuis un panneau Intune du portail Azure. Ces incidents ont des numéros dont la longueur est de huit chiffres. Vous pouvez également voir ces incidents à partir du Centre d’administration Microsoft 365.  

- Les incidents que vous avez ouverts quand vous n’utilisiez pas l’expérience Aide et support d’Intune restent inchangés. Pour les consulter, vous devez utiliser une vue Aide et support qui ne fait pas partie de l’expérience Intune ou du tableau de bord Gestion des appareils. Ces incidents ont des numéros qui commencent par **117** ou **118**, et dont la longueur est de 15 chiffres. Vous pouvez les afficher :

    1. Connectez-vous à Azure (<https://portal.azure.com>) à l’aide de vos informations d’identification d’administrateur Intune, sélectionnez *?* en haut à droite du portail, puis sélectionnez *Aide + support* pour accéder à la page [Aide + support Azure](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. Dans la page **Aide + support**, vous pouvez afficher la liste des **Demandes de support récentes** et les sélectionner pour afficher des informations supplémentaires.


## <a name="azure-help--support-experience"></a>Expérience Aide et support Azure
Les informations suivantes décrivent l’expérience Aide et support Azure à laquelle vous pouvez toujours accéder depuis le portail Azure quand vous utilisez le volet de navigation de gauche **Aide + support** ou l’option **?** en haut à droite du portail Azure. Depuis janvier 2019, vous ne pouvez plus accéder à l’expérience *Aide + support* Azure à partir de la zone *Aide et support* des panneaux Intune.  

### <a name="create-an-online-support-ticket"></a>Créer un ticket de support en ligne

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

<!--
  - **Support plan**: **Technical support - included** (for Intune technical issues, support is complimentary) or **Premier**
     >[!IMPORTANT]
     >- If you are a **Premier customer** and don't see **Support plan: Premier**, contact your Technical Account Manager for help linking your contract and tenant.
     >- Support for Intune, and for Intune when used with Configuration Manager, is free of charge. To review details of the Premier Support offering, see the [Description of Services](https://enterprise.microsoft.com/en-us/services/services-list/) documentation, section 5.3.3 "Advisory Services."

4. On the **Problem** blade, to make sure your request is addressed by the right subject matter expert for your problem, select the following options:

   - **Severity**
   - **Problem type**
   - **Category**

     These details also let us provide **Related help** that might solve your problem without filing a ticket.

     ![Screenshot of Azure portal help and support page with Problem items filled out and displaying solutions based on your problem](./media/support-need-solutions.png)

     To help the support team research and resolve your problem, enter the following information:
    
   - **Details**
   - **Date**
   - **Time**
   - **Supplemental data**

   Choose **Next**.

5. Provide **Contact information** for this support request. Microsoft support uses this information to contact you.
6. Choose **Create** to submit your support request.
-->
>[!IMPORTANT]
>Si vous avez une question relative à la facturation ou à l’abonnement, vous pouvez ouvrir un incident pour obtenir de l’assistance par l’intermédiaire du [Centre d’administration Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Afficher les demandes de support
Vous pouvez afficher une demande de support à partir du Portail Azure. Pour cela :

1. Connectez-vous à Azure (<https://portal.azure.com>) à l’aide de vos informations d’identification d’administrateur Intune, sélectionnez **?** en haut à droite du portail, puis sélectionnez **Aide + support** pour accéder à la page [Aide + support Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. Dans la page **Aide + support**, vous pouvez afficher la liste des **Demandes de support récentes** et les sélectionner pour afficher des informations supplémentaires.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Support relatif à la gestion de la facturation et des abonnements](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licences en volume](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Résoudre les problèmes d’Intune](help-desk-operators.md)
