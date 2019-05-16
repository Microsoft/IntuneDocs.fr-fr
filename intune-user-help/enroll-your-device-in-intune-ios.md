---
title: Configurer l’accès d’un appareil iOS aux ressources de l’entreprise | Microsoft Docs
description: Explique comment passer un appareil iOS en mode géré par Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292422"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurer l’accès d’un appareil iOS aux ressources de l’entreprise  

Inscrivez votre appareil iOS avec l’application Portail d’entreprise Intune pour obtenir un accès sécurisé aux e-mails, aux fichiers et aux applications de votre organisation.

Une fois que votre appareil est inscrit, il devient *géré*. Votre organisation peut affecter des stratégies et des applications à l’appareil via un fournisseur MDM, comme Intune.  

Pour conserver l’accès aux informations professionnelles ou scolaires à partir de votre appareil, vous devez configurer votre appareil avec les paramètres par défaut de votre organisation. Cet article décrit comment utiliser le portail d’entreprise pour inscrire votre appareil et pour gérer les exigences de configuration de votre organisation. 

> [!NOTE]
> Si vous avez essayé d’accéder à vos e-mails professionnels dans la messagerie d’entreprise et avez reçu un message vous invitant à passer votre appareil en mode géré, vous êtes au bon endroit. Suivez les instructions ci-dessous pour accéder à vos e-mails et à d’autres ressources de l’entreprise sur votre appareil iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>À quoi s’attendre avec l’application Portail d’entreprise ?  

### <a name="security"></a>Sécurité  
Pendant l’installation initiale, l’application vous demande de vous authentifier auprès de votre organisation. Ensuite, elle vous indique les paramètres que vous devez mettre à jour sur votre appareil. Par exemple, les organisations définissent souvent des critères de longueur de mots de passe auxquels vous devez vous plier.     

### <a name="protection"></a>Protection  
Une fois votre appareil inscrit, l’application Portail d’entreprise continue de s’assurer que votre appareil est protégé. Par exemple, si vous installez une application à partir d’une source non fiable, l’application vous alerte et révoque parfois l’accès aux données de l’entreprise. Ce type de stratégie est courant dans les organisations et vous oblige souvent à désinstaller l’application non approuvée avant de pouvoir récupérer l’accès.  

### <a name="setting-notifications"></a>Définition des notifications  
Si après l’inscription votre organisation impose une nouvelle exigence de sécurité, telle que l’authentification multifacteur, l’application Portail d’entreprise vous avertit. Vous aurez la possibilité d’ajuster vos paramètres afin de pouvoir continuer à travailler sur votre appareil.  

Pour plus d’informations sur l’inscription, consultez [Que se passe-t-il quand j’installe l’application Portail d’entreprise et que j’inscris mon appareil ?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Inscrire votre appareil iOS  

Accédez à l’App Store pour télécharger et installer l’[application Portail d’entreprise Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) sur votre appareil. Vous devrez également établir une connexion Wi-Fi et avoir accès à Safari lors de l’inscription. 

Une interruption de plus de quelques minutes lors de l’inscription peut entraîner la fermeture de l’application ou mettre fin à la configuration. Si cela se produit, ouvrez l’application Portail d’entreprise et réessayez.  

1. Ouvrez Portail d’entreprise et connectez-vous avec votre compte professionnel ou scolaire. 

    ![Exemple de capture d’écran de l’application Portail d’entreprise, Se connecter.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quand vous êtes invité à recevoir des notifications du portail d’entreprise, appuyez sur **Autoriser**. Le portail d’entreprise utilise des notifications pour vous avertir, par exemple si les paramètres de votre appareil doivent être mis à jour. 

    ![Exemple de capture d’écran de la page d’accueil du portail d’entreprise, Invite « Notifications ».](./media/ios-04-cp-enroll-1903.PNG)  

3. Dans l’écran **Configurer l’accès**, sélectionnez **Commencer**.  

     ![Exemple de capture d’écran de l’application Portail d’entreprise, écran « Configurer l’accès ».](./media/ios-05-cp-enroll-1903.PNG)  

4. Lisez la liste des informations présentes sur l’appareil que votre organisation peut voir ou ne pas voir. Appuyez ensuite sur **Continuer**.  

5. Lisez les instructions dans l’écran **Quelle est la prochaine étape ?**. Quand vous êtes prêt à télécharger et à installer le profil de gestion, appuyez sur **Continuer**.  

 > [!IMPORTANT]
> Ces étapes et ces écrans suivants diffèrent selon votre version d’iOS. Suivez les étapes correspondant à votre version d’iOS. 

6. Safari ouvre le site web Portail d’entreprise sur votre appareil. Quand vous êtes invité à télécharger le profil de configuration, appuyez sur **Autoriser**. Si vous êtes sur un appareil exécutant :  
    * iOS 12.2 et ultérieur : quand le téléchargement est terminé, appuyez sur **Terminé**. Passez à l’étape 7 de cet article.
    * iOS 12.1 et antérieur : vous êtes automatiquement redirigé vers l’application Paramètres. Passez à l’étape 8 de cet article.  
 
    Si vous appuyez accidentellement **Ignorer**, actualisez la page. Vous êtes invité à ouvrir l’application Portail d’entreprise. Dans l’application, vous pouvez appuyer sur **Retélécharger**.

  > [!NOTE]
  > Vous devez installer le profil de gestion comme décrit dans les étapes suivantes dans les 8 minutes de son téléchargement. Si vous ne le faites pas, le profil est supprimé et vous devez recommencer l’inscription.  

7. iOS 12.2 et ultérieure uniquement : quand vous êtes invité à ouvrir le portail d’entreprise, appuyez sur **Ouvrir**. L’écran **Installation du profil de gestion** liste les étapes pour installer le profil.

    ![Exemple de capture d’écran du portail d’entreprise, écran Installation du profil de gestion.](./media/ios-1904-settings-icon.PNG)  

8. Accédez à l’application Paramètres, puis appuyez sur **Profil téléchargé**.  

    Si l’option **Profil téléchargé** n’apparaît pas, accédez à **Général** > **Profils**. Si vous ne voyez toujours pas le profil, il peut être nécessaire de le retélécharger.  

    ![Exemple de capture d’écran de l’application Paramètres, paramètre Profil téléchargé.](./media/ios-1904-settings-badge.PNG)  

9. Appuyez sur **Installer**.  
    
10. Entrez le mot de passe de votre appareil. Appuyez ensuite sur **Installer**.    

    ![Exemple de capture d’écran de l’application Paramètres, écran Installation du profil, avec un curseur sur le bouton **Installer**.](./media/ios-1904-password-install.PNG)  


11. L’écran suivant est un avertissement système standard pour la gestion des appareils. Pour continuer l’installation, appuyez sur **Installer**. Si vous êtes invité à approuver la gestion à distance, appuyez sur **Approuver**.  

    ![Exemple de capture d’écran de l’application Paramètres, écran d’avertissement système standard pour le certificat racine et la gestion des appareils mobiles.](./media/ios-15-cp-enroll-1903.PNG)  

12. Une fois l’installation terminée, appuyez sur **Suivant**. Pour vérifier que le profil a été installé, accédez aux paramètres **Profils et gestion des appareils**. Vous devez normalement voir le profil sous **Gestion des appareils mobiles**.   

    ![Exemple de capture d’écran de l’application Paramètres, paramètres de Profils & gestion des appareils, montrant le profil de gestion.](./media/ios-00-cp-enroll-1903.PNG)  

13. Revenez à l’application Portail d’entreprise. Le portail d’entreprise commence à synchroniser et à configurer votre appareil. Le portail d’entreprise peut vous inviter à mettre à jour des paramètres d’appareil supplémentaires. Si c’est le cas, appuyez sur **Continuer**.  

    ![Exemple de capture d’écran du portail d’entreprise, écran « Configurer l’accès », avec un triangle jaune en regard de la spécification des paramètres.](./media/ios-12-cp-enroll-1903.PNG)  

14. La configuration est terminée quand tous les éléments de la liste montrent un cercle vert. Appuyez sur **Terminé**.   
    
    ![Exemple de capture d’écran du portail d’entreprise, écran « Vous êtes prêt à commencer ! », montrant tous les cercles verts.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Si votre organisation surveille les limites pour la voix et les données, ou si elle vous fournit un appareil d’entreprise, quelques étapes supplémentaires peuvent être nécessaires pour terminer la configuration. Si vous êtes invité à installer l’application **Datalert**, consultez [Inscription de votre appareil dans la gestion des dépenses de télécommunication](enroll-your-device-with-telecom-expense-management-ios.md). Si votre organisation fait partie du programme DEP d’Apple, découvrez [comment inscrire votre appareil d’entreprise](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Étapes suivantes  
Recherchez des applications qui vous aident dans le domaine professionnel ou scolaire. Découvrez [comment les applications sont rendues disponibles](use-managed-apps-on-your-device-ios.md) via le portail d’entreprise.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Vous trouverez ses coordonnées sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
