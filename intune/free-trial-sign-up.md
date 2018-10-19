---
title: Démarrage rapide - Essayer gratuitement Microsoft Intune
titlesuffix: ''
description: Dans ce guide de démarrage rapide, vous allez créer un abonnement d’essai gratuit, comprendre les configurations prises en charge, ainsi que les exigences relatives à la mise en réseau, et éventuellement configurer votre nom de domaine.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 37445cb2536e02937cf3002dc1cb56ab4b78f12f
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581391"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Démarrage rapide : Essayer gratuitement Microsoft Intune 

Microsoft Intune vous aide à protéger les données d’entreprise de vos équipes en vous permettant de gérer les appareils et les applications. Dans ce guide de démarrage rapide, vous allez créer un abonnement gratuit pour essayer Intune dans un environnement de test.

Intune fournit une solution MDM (gestion des appareils mobiles) et une solution GAM (gestion des applications mobiles) à partir d’un service cloud sécurisé, administré via le Portail Microsoft Azure. À l’aide d’Intune, vous pouvez vérifier que les ressources d’entreprise de vos équipes (données, appareils et applications) sont correctement configurées, accessibles et mises à jour, en fonction des critères et stratégies de conformité de votre entreprise. 

## <a name="prerequisites"></a>Prérequis
Avant de configurer Microsoft Intune, passez en revue les exigences suivantes :

   - [Systèmes d’exploitation et navigateurs pris en charge](supported-devices-browsers.md) 
   - [Exigences et bande passante de la configuration réseau](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>S’inscrire à une version d’évaluation gratuite de Microsoft Intune

L’essai d’Intune est gratuit pendant 30 jours. Si vous disposez déjà d’un compte professionnel ou scolaire, **connectez-vous** avec ce compte et ajoutez Intune à votre abonnement. Sinon, vous pouvez **ouvrir** un nouveau compte pour utiliser Intune pour votre organisation.

> [!IMPORTANT]
> Vous ne pouvez pas combiner un compte professionnel ou scolaire existant après avoir ouvert un nouveau compte.

1. Accédez à la page d’[essai de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) et remplissez le formulaire.

    ![Capture d’écran de la page web d’inscription pour un compte d’essai Microsoft Intune](./media/account-sign-up-site-full-browser.png)

    Si la plupart des utilisateurs et opérations informatiques ont des paramètres régionaux différents des vôtres, vous pouvez définir ces paramètres régionaux dans **Pays ou région**. Azure utilise vos informations régionales pour fournir les bons services. Vous ne pouvez pas changer ce paramètre plus tard.

2. Créez un compte à l’aide du nom de votre société suivi de **.onmicrosoft.com**. 

    ![Capture d’écran de la page web d’inscription pour un compte d’essai Microsoft Intune](./media/account-sign-up-site-user-id.png)

    Si votre organisation a son propre domaine personnalisé et si vous souhaitez l’utiliser sans **.onmicrosoft.com**, vous pouvez le changer dans le portail Office 365 Admin décrit plus loin dans cet article.

3. À la fin du processus d’inscription, vous pouvez voir les informations relatives à votre nouveau compte.

    ![Image de vos informations de compte](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Se connecter au Portail Azure

1. Ouvrez une nouvelle fenêtre de navigateur, et entrez **https://portal.azure.com** dans la barre d’adresses. 
2. Utilisez les informations d’identification qui vous ont été données au cours des étapes ci-dessus pour vous connecter.

    ![Image de la page de connexion au Portail Azure](./media/azure-portal-signin.png)

3. Pour afficher Microsoft Intune sur le port Azure, sélectionnez **Tous les services** dans la barre latérale à gauche de la page.
4. Recherchez **Microsoft Intune** dans la zone de filtre, puis sélectionnez cette valeur.
5. Sélectionnez l’**étoile** pour ajouter Intune au bas de la liste de vos services favoris, puis ouvrez le tableau de bord Intune.

Quand vous vous inscrivez à une version d’essai, vous recevez également un e-mail contenant les informations de votre compte à l’adresse e-mail que vous avez fournie durant la procédure d’inscription. Cet e-mail confirme que votre version d’évaluation est active.

## <a name="set-the-mdm-authority-to-intune"></a>Définir Intune en tant qu’autorité MDM

Le paramètre d’autorité de gestion des appareils mobiles (MDM) détermine la façon dont vous gérez vos appareils. En tant qu’administrateur informatique, vous devez définir une autorité de gestion des appareils mobiles (MDM) avant que les utilisateurs puissent inscrire des appareils pour la gestion.

Pour définir Intune en tant qu’autorité MDM, effectuez les étapes suivantes.

1. Ouvrez une nouvelle fenêtre de navigateur, et entrez **https://portal.azure.com** dans la barre d’adresses. 
2. Choisissez **Tous les services** > **Microsoft Intune**.
3. Sélectionnez la bannière orange pour ouvrir le paramètre **Autorité de gestion des appareils mobiles**. 

    > [!NOTE]
    > La bannière orange s’affiche seulement si vous n’avez pas encore défini l’autorité MDM.

4. Sous **Autorité de gestion des appareils mobiles**, définissez l’autorité MDM en tant qu’**Autorité MDM Intune**.

## <a name="configure-your-custom-domain-name-optional"></a>Configurer votre nom de domaine personnalisé (facultatif)

Comme indiqué ci-dessus, si votre organisation a son propre domaine personnalisé et si vous souhaitez l’utiliser sans **.onmicrosoft.com**, vous pouvez le changer dans le portail Office 365 Admin. Vous allez ajouter, vérifier et configurer votre nom de domaine personnalisé.  

> [!IMPORTANT]
> Vous ne pouvez pas renommer ou supprimer le nom de domaine initial **onmicrosoft.com**. Vous pouvez ajouter, vérifier ou supprimer les noms de domaine personnalisés utilisés avec Intune pour clarifier l’identité de votre entreprise.

1. Accédez au [portail de gestion Office 365](https://portal.office.com/Admin/Default.aspx), et connectez-vous à l’aide de votre compte d’administrateur.

2. Dans le volet de navigation, choisissez **Configuration** > **Domaines** > **Ajouter un domaine**.

3. Tapez votre nom de domaine personnalisé. Sélectionnez ensuite **Suivant**.

   ![Capture d’écran du Centre d’administration Office 365 avec Paramètres > Domaines sélectionné, et l’ajout d’un nouveau nom de domaine](./media/domain-custom-add.png)

4. Vérifiez que vous êtes le propriétaire du domaine que vous avez entré auparavant. 
    
    Si vous sélectionnez **envoyer le code par courrier**, un e-mail est envoyé au contact inscrit pour votre domaine. Une fois l’e-mail reçu, copiez le code et entrez-le dans le champ **Tapez votre code de vérification ici**. Si le code de vérification correspond, le domaine est ajouté à votre locataire. L’e-mail affiché peut ne pas sembler familier. Certains bureaux d’enregistrement cachent la véritable adresse e-mail fournie durant l’enregistrement du domaine.

   ![Capture d’écran du Centre d’administration Office 365 - Vérification du nom de domaine ajouté](./media/domain-custom-verify.png)

   > [!NOTE]
   > Pour plus d’informations sur la vérification des enregistrements TXT, consultez [Créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Expériences d’administration

Vous pouvez utiliser deux portails :
- Le tableau de bord Intune dans Azure ([portal.azure.com](https://portal.azure.com)) vous permet d’explorer les [fonctionnalités d’Intune](what-is-intune.md). Normalement, vous effectuez votre travail dans le tableau de bord Intune.
- Le centre d’administration Office 365 ([portal.office.com](https://portal.office.com)) vous permet d’ajouter et de gérer des utilisateurs, si vous n’utilisez pas Azure Active Directory pour cela. Vous pouvez également gérer d’autres aspects de votre compte, y compris la facturation et le support.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez créé un abonnement gratuit pour essayer Intune dans un environnement de test, et vous avez éventuellement configuré un nom de domaine personnalisé. Pour en savoir plus sur Microsoft Intune, passez au prochain guide de démarrage rapide afin d’ajouter des utilisateurs et affecter des licences.

> [!div class="nextstepaction"]
> [Créer un utilisateur](get-started-users.md)
