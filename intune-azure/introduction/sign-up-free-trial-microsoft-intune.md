---
title: "S’inscrire à une évaluation gratuite de 30 jours"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : Guide pratique pour s’inscrire à Intune sur Azure."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: eaddfc647c5e755e6b033a7970e003ce516bba04
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>Inscrivez-vous pour une version d’évaluation gratuite de Microsoft Intune pour la préversion du portail Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Cet article vous guide tout au long l’inscription pour une version d’évaluation d’Intune autonome pour la préversion du portail Azure. <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. Visitez la page d’[inscription Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) et remplissez le formulaire pour vous inscrire afin d’obtenir un abonnement d’évaluation.

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![Image de la page d’inscription](./media/1-clicking-try.png)

 > [!TIP]
> Si la plupart des utilisateurs et opérations informatiques ont des paramètres régionaux différents des vôtres, vous pouvez définir ces paramètres régionaux dans **Où votre société se situe-t-elle ?**.

2. À la fin de la procédure d’inscription, vous recevrez un message avec vos nouvelles informations de compte. <br/> ![Image d’informations de compte](./media/2-end-of-sign-up-process.png) <br/>À ce stade, si vous cliquez sur **Vous êtes prêt**, vous êtes dirigé vers le centre d’administration Office 365, où vous pouvez ajouter des utilisateurs à votre environnement de test. <br/><br/>Toutefois, si vous souhaitez accéder directement à la préversion du portail Intune Azure, ouvrez une nouvelle fenêtre de navigateur et saisissez **https://portal.azure.com** dans la barre d’adresse. Vous êtes alors redirigé vers la page de connexion Azure où vous pouvez utiliser les informations d’identification que vous avez reçues pour vous connecter. Utilisez cette adresse chaque fois que vous souhaitez vous connecter à votre version d’évaluation d’Intune. <br/> ![Image de page de connexion au portail Azure](./media/azure-portal-signin.png)

La première fois que vous vous connectez à Intune dans la préversion d’Azure, il est possible vous ne voyiez pas Intune dans votre tableau de bord Azure. Pour ajouter le service Intune à votre tableau de bord Azure :
1. Choisissez **Autres services >** dans la liste des services Azure à gauche du tableau de bord, puis entrez **Intune** dans la zone de recherche.
2. Choisissez **Intune** dans la liste, puis sélectionnez l’étoile pour ajouter le service à la liste des services.<br/> ![Image de la sélection d’Intune dans la liste des services](./media/azure-add-intune1.png)
3. Choisissez ensuite **Intune** dans la liste des services pour ouvrir le tableau de bord Intune.

Quand vous vous inscrivez pour obtenir une version d’évaluation, vous recevez aussi un e-mail contenant les informations de votre compte à l’adresse e-mail que vous avez fournie lors de l’inscription. Cet e-mail confirme que votre version d’évaluation est active.


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>Assurer la clarté des expériences d’administration
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
Il existe trois portails que vous pouvez utiliser pour la préversion d’Intune Azure :
- Le tableau de bord Intune dans Azure ([portal.azure.com](https://portal.azure.com)) où vous pouvez explorer les [fonctionnalités d’Intune dans le portail Azure](what-is-microsoft-intune.md).
- Le centre d’administration d’Office 365 ([portal.office.com](https://portal.office.com)) où vous pouvez ajouter et gérer des utilisateurs si vous n’utilisez pas Azure Active Directory pour cela. Vous pouvez également gérer d’autres aspects de votre compte, y compris la facturation et le support.
- La console d’administration Intune classique ([manage.microsoft.com](https://manage.microsoft.com)) où vous pouvez explorer les fonctionnalités qui n’ont pas encore été ajoutées à Azure.

Normalement, vous effectuez votre travail dans le tableau de bord Intune, comme indiqué ci-dessous. Il s’agit du site où vous configurez et gérez vos groupes, stratégies, appareils et applications.

Vous pouvez accéder à la console d’administration Intune classique à partir du tableau de bord en choisissant la vignette **Ouvrir le portail Intune classique**.

Pour revenir à la préversion d’Intune Azure, entrez https://portal.azure.com dans la barre d’adresse de votre navigateur, puis choisissez **Intune** dans la liste des services.

 ![Image du tableau de bord Intune](./media/intune-azure-dashboard.png)


Toutefois, vous allez utiliser le Centre d’administration Office 365, illustré ci-dessous, pour ajouter et gérer vos utilisateurs et d’autres aspects de votre compte, notamment la facturation et le support.

![Image du Centre d’administration Office 365](./media/office-admin-center.png)

Pour passer du Centre d’administration Office 365 au tableau de bord Intune, entrez https://portal.azure.com dans la barre d’adresse de votre navigateur. Choisissez **Intune** dans la liste des services.

Pour revenir d’Intune au Centre d’administration Office 365, entrez https://portal.office.com dans la barre d’adresse de votre navigateur. Si vous êtes déjà connecté à Intune, vous accéderez directement au Centre d’administration Office 365.

## <a name="next-steps"></a>Étapes suivantes

### <a name="intune-azure-preview"></a>Intune Azure (préversion)
En savoir plus sur [Intune dans le portail Azure en préversion](what-is-microsoft-intune.md)
### <a name="classic-intune"></a>Intune classique
Scénario d’évaluation : [Évaluer la gestion des appareils mobiles dans Microsoft Intune](https://docs.microsoft.com/intune/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>Intégration dans d'autres produits
En savoir plus sur l’utilisation de vos comptes d’utilisateur Azure Active Directory avec Intune :
- [Configuration requise pour les identités](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Configuration requise pour la synchronisation d’annuaires](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Configuration requise pour l’authentification multifacteur](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

En savoir plus sur l’utilisation d’[Intune avec System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)

