---
title: Comment obtenir un support technique pour Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenez du support en ligne et par téléphone pour les abonnements d’essai gratuit et payants de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5aca7dbae7a74af399bcbf21aec1dd9dd2d1e851
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390761"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Comment obtenir un support technique pour Microsoft Intune

Microsoft fournit un support technique global, en avant-vente, pour la facturation et l’abonnement pour Microsoft Intune. Un support technique est disponible en ligne et par téléphone pour les abonnements payants et d’évaluation. Le support technique en ligne est disponible en anglais et japonais. Le support par téléphone et le support à la facturation en ligne sont disponibles dans d’autres langues.

En tant qu’administrateur informatique, vous pouvez utiliser l’option **Aide et support** afin de créer un ticket de support en ligne pour Intune, à partir du portail Microsoft Azure. Pour que vous puissiez créer et gérer un incident de support, votre compte doit avoir un rôle Azure Active Directory (Azure AD) incluant *l’action* **microsoft.office365.supportTickets**. Pour plus d’informations sur les rôles Azure AD et les autorisations nécessaires pour créer un ticket de support, consultez la section relative aux [rôles d’administration dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Pour obtenir un support technique sur les produits tiers qui fonctionnent avec Intune (comme Saaswedo, Cisco ou Lookout), contactez d’abord le fournisseur du produit. Avant d’ouvrir un incident auprès du support Intune, vérifiez que vous avez correctement configuré l’autre produit.
>
> Pour plus d’informations sur la résolution des problèmes liés à Microsoft Intune, consultez la [section de résolution des problèmes](help-desk-operators.md) dans la documentation d’Intune.


## <a name="help-and-support-experience"></a>Expérience Aide et support

L’expérience Aide et support pour Intune est disponible sur le [centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) et dans tous les panneaux (ou pages) du portail Azure sous Intune.

:’expérience *Aide et support* est similaire à celle du [Centre d’administration Microsoft 365](https://admin.microsoft.com/) et remplace l’expérience *Aide + support* précédente, qui demeure pour d’autres services dans Azure.

> [!TIP]
> À partir du 18 novembre 2019, une expérience mise à jour et rationalisée dans la console pour obtenir de l’aide et du support est déployée sur les locataires. Si cette nouvelle expérience n’est pas encore à votre disposition, elle le sera bientôt.

### <a name="options-to-access-help-and-support"></a>Options d’accès à l’aide et au support

Lorsque vous utilisez un locataire nouvellement créé pour Intune, il est possible qu’*Aide et support* ne s’ouvre pas et que le message suivant soit retourné :

- *Nous avons rencontré un problème inconnu. Actualisez la page, mais si le problème persiste, créez un incident via le [Centre d’administration M365](https://admin.microsoft.com) et référencez l’ID de session fourni.*

Les détails de l’erreur incluent un *ID de session*, les détails de l’*Extension*, entre autres. 
 
Ce problème se produit lorsque vous n’avez pas encore authentifié votre nouveau compte de locataire par le biais du **Centre d’administration M365** sur https://admin.microsoft.com, ou à partir du **portail Office 365** sur https://portal.office.com. Pour résoudre ce problème, sélectionnez le lien pour le *Centre d’administration M365* dans le message, ou visitez https://portal.office.com et connectez-vous. Après l’authentification sur l’un des deux sites, *Aide et support* pour Intune devient accessible.


**Accéder à l’aide et au support** :

- **Dans le portail Azure**

  - Sélectionnez **Aide et support** sur un panneau ou une page Intune.

  > [!NOTE]  
  > Si votre instance d’Intune est hébergée sur le cloud privé pour le secteur public, également appelé cloud souverain à l’instar d’Azure Government, voir [Support Intune du cloud privé pour le secteur public](#intune-support-for-private-cloud-for-government) plus loin dans cet article. L’expérience *Aide et support* Intune sera disponible sur le cloud privé pour le secteur public l’année prochaine seulement.

- **À partir du Centre d’administration de Microsoft Endpoint Manager**
  - Une fois que vous avez sélectionné une zone de fonctionnalités pour Intune, sélectionnez l’option **Aide et support**.
  - Dans le Centre d’administration de Microsoft Endpoint Manager, sélectionnez le **?** en haut à droite dans le portail, puis utilisez la liste déroulante pour sélectionner le service pour lequel vous souhaitez obtenir de l’aide. L’icône **?** dans le Centre d’administration de Microsoft Endpoint Manager prend en charge plusieurs services, et vous devez sélectionner le service spécifique pour lequel vous souhaitez obtenir de l’aide.  

    ![Sélectionnez votre service](./media/get-support/select-a-service.png)

    Lorsqu’un service est sélectionné, la page *Aide et support* correspondante s’affiche. Vous pouvez alors spécifier des détails pour [trouver des solutions](#find-solutions) à un problème donné.

    Si les résultats de votre recherche ne correspondent pas à vos attentes concernant le service, vérifiez que vous avez sélectionné le bon service. La sélection du service apparaît juste après *Aide et support*.  Si le service approprié n’a pas été sélectionné, cliquez sur *Sélectionner un service* pour revenir à la liste déroulante de sélection du service.

    ![Confirmez votre service](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>Expérience de support

  Lorsque vous ouvrez Aide et support, le portail affiche la fenêtre **Besoin d’aide ?**  :

  ![Afficher la fenêtre Besoin d’aide](./media/get-support/need-help.png)

  Dans le coin supérieur gauche se trouvent trois icônes permettant d’ouvrir les différents volets de la fenêtre *Besoin d’aide ?* . Le volet affiché est identifié par le soulignement.

  Les clients disposant d’un contrat de support **Premier** ou **Unifié** ont des [options supplémentaires](#premier-and-unified-support-customers) de support, et voient apparaître une bannière comme celle-ci dans *Besoin d’aide ?*  : ![Bannière Premier](./media/get-support/premier-banner.png)

  *Besoin d’aide ?* s’ouvre sur le volet *Rechercher des solutions*. Cependant, si vous avez un cas de support actif, la fenêtre s’ouvre sur le volet *Demandes de service* permettant d’afficher des détails sur les cas de support actifs et fermés.

#### <a name="find-solutions"></a>Rechercher des solutions

![Sélectionner le volet Rechercher des solutions](./media/get-support/find-solutions.png)

Dans le volet *Rechercher des solutions*, donnez quelques détails sur un problème dans la zone de texte fournie. Le volet indique alors des recommandations susceptibles de correspondre au texte saisi. Vous y trouverez également des liens vers des articles recommandés qui pourront vous aider à résoudre le problème.

Quand une correspondance solide est trouvée pour la description fournie, des conseils de dépannage s’affichent directement dans la fenêtre *Besoin d’aide ?* .

Supposons par exemple que vous entriez **Erreurs de synchronisation de mot de passe**. Parmi les résultats figurent des conseils de dépannage directement dans le volet et des liens vers des articles recommandés de notre bibliothèque de documentation.

![Afficher les recommandations de dépannage](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>Contactez le support technique

![Sélectionner le volet Contacter le support](./media/get-support/contact-support.png)

Le volet *Contacter le support* permet d’envoyer une demande d’assistance. Il apparaît une fois que des mots clés de base ont été saisis dans le volet *Rechercher des solutions*.

Lorsque vous demandez de l’aide, donnez une description du problème aussi détaillée que possible.  Après avoir confirmé votre numéro de téléphone et votre adresse e-mail, sélectionnez le mode de contact de votre choix. La fenêtre indique le temps de réponse pour les deux modes, ce qui vous permet de savoir quand vous devriez recevoir une réponse. Avant de soumettre votre demande, joignez des fichiers, par exemple des journaux ou des captures d’écran, susceptibles de donner des détails sur le problème.

![Formulaire Contacter le support](./media/get-support/contact-support-form.png)

Après avoir renseigné les informations nécessaires, sélectionnez **Me contacter** pour envoyer la demande.

#### <a name="service-requests"></a>Demandes de service

![Volet Sélectionner les demandes de service](./media/get-support/service-requests.png)

Le volet *Demandes de service* affiche votre historique de cas. Les cas actifs se trouvent en haut de la liste ; les problèmes fermés peuvent également être examinés.

![Afficher la liste des demandes de service](./media/get-support/service-requests-pane.png)

Si vous disposez d’un numéro de cas de support actif, vous pouvez l’entrer ici pour accéder directement à ce problème. Sinon, vous pouvez sélectionner un incident dans la liste des incidents actifs et fermés pour afficher plus d’informations le concernant.

Après avoir consulté les détails d’un incident, sélectionnez la flèche gauche qui s’affiche en haut de la fenêtre des demandes de service, juste au-dessus des trois icônes du volet *Besoin d’aide ?* . La flèche précédent renvoie à l’affichage de la liste des incidents de support que vous avez ouverts.

#### <a name="premier-and-unified-support-customers"></a>Clients du Support Premier et du Support Unifié

Si vous disposez d’un contrat de support **Premier** ou **Unifié**, vous pouvez indiquer la gravité de votre problème et planifier un rappel du support à une date et une heure données. Vous avez accès à ces options lorsque vous ouvrez ou soumettez un nouveau problème ou que vous modifiez un cas de support actif.

**Gravité** : les options permettant de spécifier la gravité d’un problème dépendent du contrat de support :

- *Premier* : Gravité A, B ou C
- *Unifié* : Critique ou non critique

Si vous sélectionnez le niveau de gravité **A** ou **Critique**, seul le cas de support téléphonique, qui représente l’option la plus rapide, est disponible.

**Planification de rappel** : vous pouvez demander un rappel à une date et une heure données.

## <a name="azure-help--support-experience"></a>Expérience Aide et support Azure

Vous ne pouvez plus utiliser l’expérience *Aide et support* Azure pour obtenir de l’aide sur Intune, sauf si votre abonnement porte sur un cloud privé pour le secteur public.
Si votre instance d’Intune ne s’exécute pas sur un cloud privé pour le secteur public, la navigation dans *Aide et support* Azure vous redirige vers l’expérience *Aide et support* Intune pour créer et gérer des incidents de support :

Lorsque vous utilisez le volet de navigation gauche **Help + support** ou l’option **?** pour ouvrir le volet *Aide*, puis sélectionnez **Aide et support**, et ouvrez la page *Aide et support* Azure. 


À partir de cette page, sélectionnez **+ Nouvelle demande de support** pour ouvrir l’onglet *De base* de la page *Aide et support + Nouvelle demande de support*.

![Aide + support](./media/get-support/help-plus-support.png)

Sur cette page :

- Pour *Type de problème*, spécifiez **Technique**.
- Pour *Service*, sélectionnez **Microsoft Intune**.

  Vous voyez ensuite un lien qui vous redirige vers la page d’[aide et de support d’Intune](https://aka.ms/intunehelpsupport).
  
  ![Nouvelle demande de support](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>Support Intune pour le cloud privé du secteur public

Si votre abonnement Intune est hébergé sur le cloud privé pour le secteur public, aussi appelé cloud souverain à l’instar d’Azure Government, vous n’avez pas encore accès à la nouvelle expérience Aide et support Intune.  À la place, utilisez les informations suivantes pour obtenir un support pour Intune.

### <a name="create-an-online-support-ticket"></a>Créer un ticket de support en ligne

>[!IMPORTANT]
> Étant donné qu’*Aide et support* passe à un nouveau système qui n’est pas encore disponible pour le cloud privé du secteur public, quand vous créez un incident de support, le portail identifie un cas de support qui utilise un numéro d’identification à 15 chiffres. Lorsque le cas à 15 chiffres est créé, un miroir de ce cas est créé afin d’être utilisé par le support Microsoft. Ce cas de mise en miroir est créé dans un nouveau système de support, utilise un ID de cas à 8 chiffres et est utilisé par les services de support pour assurer le suivi de l’ensemble du travail et des communications pour votre incident de support. Peu après la création de votre cas à 15 chiffres, vous recevrez un e-mail qui identifie le numéro à 8 chiffres du cas de support mis en miroir utilisé par les services de support technique.
>
> Prenez en charge le travail personnel et communiquez à l’aide du cas de support à 8 chiffres, et utilisez uniquement le dossier de support à 8 chiffres pour consigner les communications et suivre la progression des incidents. Pour cette raison, vous recevez des mises à jour par e-mail de ce cas de support à 8 chiffres qui servent d’enregistrement de suivi de votre cas. Aucun détail n’est consigné dans l’incident de support à 15 chiffres. Lorsque le support se termine et que le cas de support à 8 chiffres se ferme, cet État est reflété par le cas de support à 15 chiffres que vous pouvez afficher dans le portail Azure.  Aucune autre mise à jour ou modification d’état ne doit être attendue dans le cas d’un support à 15 chiffres.
>
> Lorsque les transitions entre les outils de support se termineront plus tard cette année, l’expérience de support Intune hébergée sur le cloud pour le secteur public ressemblera à l’expérience par défaut *Aide et support* actuellement disponible pour les abonnements Intune hébergés sur le cloud public.

1. Connectez-vous au Portail Azure (<https://portal.azure.us>) à l’aide de vos informations d’identification d’administrateur Intune, sélectionnez **?** en haut à droite du portail, puis sélectionnez **Aide + support** pour accéder à la page [Aide + support Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Image du lien point d’interrogation avec lien Aide + support entouré](./media/get-support/azure-get-support.png)

2. Dans la page **Aide + support** d’Azure, sélectionnez **Nouvelle demande de support**.

   ![Image du lien Nouvelle demande de support mis en surbrillance sur la page Aide et support](./media/get-support/azure-support-ticket-link.png)

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
   > Les clients du cloud privé pour le secteur public peuvent uniquement afficher le numéro de cas de support à 15 chiffres et l’état de l’incident. Toutes les communications relatives au cas et le suivi du travail ou les alertes sont envoyés par e-mail et font référence au numéro de cas de support à 8 chiffres créé comme miroir du cas de support ouvert à partir de la console Intune.

## <a name="additional-resources"></a>Ressources supplémentaires  

- [Support relatif à la gestion de la facturation et des abonnements](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licences en volume](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Résoudre les problèmes d’Intune](help-desk-operators.md)
