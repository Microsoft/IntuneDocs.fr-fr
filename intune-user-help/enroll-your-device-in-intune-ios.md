---
title: Configurer l’accès d’un appareil iOS aux ressources de l’entreprise | Microsoft Docs
description: Explique comment passer un appareil iOS en mode géré par Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 92d1ca850d8bb542f0b7fe027ab7af8c12089ef8
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181753"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurer l’accès d’un appareil iOS aux ressources de l’entreprise  

Inscrivez votre appareil iOS avec l’application Portail d’entreprise Intune pour obtenir un accès sécurisé aux e-mails, aux fichiers et aux applications de votre organisation.

Une fois que votre appareil est inscrit, il devient *géré*. Votre organisation peut affecter des stratégies et des applications à l’appareil via un fournisseur MDM, comme Intune.  

> [!NOTE]
> Nous ne vendons pas les données collectées par notre service à des tiers pour une raison quelconque.  

Pour conserver l’accès aux informations professionnelles ou scolaires à partir de votre appareil, vous devez configurer votre appareil avec les paramètres par défaut de votre organisation. Cet article décrit comment utiliser le portail d’entreprise pour inscrire votre appareil et pour gérer les exigences de configuration de votre organisation.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

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

2. Quand vous êtes invité à recevoir des notifications du portail d’entreprise, appuyez sur **Autoriser**. Le portail d’entreprise utilise des notifications pour vous avertir, par exemple si les paramètres de votre appareil doivent être mis à jour.  

3. Dans l’écran **Configurer l’accès**, sélectionnez **Commencer**.   

    ![Exemple de capture d’écran de l’application Portail d’entreprise, écran « Configurer l’accès ».](./media/ios-enrollment-checklist-1909.PNG)  

4. L’écran **Sélectionner le type d’appareil et d’inscription** s’affiche et vous invite à entrer votre type d’appareil.  
    * Appuyez sur **(Organisation) est propriétaire de cet appareil** si vous avez reçu votre appareil de votre organisation. Passez ensuite à [Sécuriser l’ensemble de l’appareil](#secure-entire-device) dans cet article pour terminer l’installation.  
    * Appuyez sur **Je suis propriétaire de cet appareil** si vous utilisez un appareil personnel que vous avez apporté de chez vous. Passez ensuite à l’étape suivante.  

    Si vous ne voyez pas cet écran, passez à [Sécuriser l’ensemble de l’appareil](#secure-entire-device) pour terminer l’installation.  
    
    ![Exemple de capture d’écran du portail d’entreprise, écran « Sélectionner le type d’appareil et d’inscription », options relatives au type d’appareil.](./media/ios-device-type-1909.PNG)  


5. Choisissez comment protéger les données de votre appareil une fois celui-ci inscrit.  
    * Appuyez sur **Sécuriser l’ensemble de l’appareil** pour sécuriser toutes les applications et les données sur l’appareil. Accédez ensuite à [Sécuriser l’ensemble de l’appareil](enroll-your-device-in-intune-ios.md#secure-entire-device) pour terminer l’installation.
    * Appuyez sur **Sécuriser les applications et les données liées au travail uniquement** pour sécuriser uniquement les applications et les données auxquelles vous accédez avec votre compte professionnel. Accédez ensuite à [Sécuriser les applications et les données liées au travail uniquement](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data).  

    ![Exemple de capture d’écran du portail d’entreprise, écran « Sélectionner le type d’appareil et d’inscription », options relatives au type d’inscription.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Sécuriser l’ensemble de l’appareil  

1. Dans l’écran **Gestion des appareils et confidentialité**, parcourez la liste des informations présentes sur l’appareil que votre organisation peut ou ne peut pas voir. Appuyez ensuite sur **Continuer**.  


 > [!IMPORTANT]
> Ces étapes et ces écrans suivants diffèrent selon votre version d’iOS. Suivez les étapes correspondant à votre version d’iOS. 

2. Safari ouvre le site web Portail d’entreprise sur votre appareil. Quand vous êtes invité à télécharger le profil de configuration, appuyez sur **Autoriser**. Si vous êtes sur un appareil exécutant :  
    * iOS 12.2 et ultérieur : quand le téléchargement est terminé, appuyez sur **Fermer**. Passez ensuite à l’étape 3.  
    * iOS 12.1 et antérieur : Une fois le téléchargement terminé, vous êtes automatiquement redirigé vers l’application Paramètres. Passez à l’étape 4.  
 
    Si vous appuyez accidentellement **Ignorer**, actualisez la page. Vous êtes invité à ouvrir l’application Portail d’entreprise. Une fois que vous y êtes, appuyez sur **Retélécharger**.

  > [!NOTE]
  > Vous devez installer le profil de gestion comme décrit dans les étapes suivantes dans les 8 minutes de son téléchargement. Si vous ne le faites pas, le profil est supprimé et vous devez recommencer l’inscription.  

3. Quand vous êtes invité à ouvrir le portail d’entreprise, appuyez sur **Ouvrir**. Lisez les informations contenues dans l’écran **Comment installer le profil de gestion**.  

4. Accédez à l’application Paramètres et appuyez sur **Inscrire dans <nom de l’organisation>** ou **Profil téléchargé**.  

    ![Exemple de capture d’écran de l’application Paramètres, option Inscrire dans organisation.](./media/enroll-in-organization-ios-1909.PNG)  

   Si vous ne voyez pas ces options, accédez à **Général** > **Profils et gestion des appareils**> **Profil de gestion**. Si vous ne voyez toujours pas le profil de gestion, il peut être nécessaire de le retélécharger.  

5. Appuyez sur **Installer**.  
    
6. Entrez le mot de passe de votre appareil. Appuyez ensuite sur **Installer**.    

7. L’écran suivant est un avertissement système standard sur la gestion des appareils. Pour continuer l’installation, appuyez sur **Installer**. Si vous êtes invité à approuver la gestion à distance, appuyez sur **Approuver**.  

8. Une fois l’installation terminée, appuyez sur **Suivant**. Pour vérifier que le profil a été installé, accédez aux paramètres **Profils et gestion des appareils**. Vous devez normalement voir le profil sous **Gestion des appareils mobiles**.   

    ![Exemple de capture d’écran de l’application Paramètres, paramètres de Profils & gestion des appareils, montrant le profil de gestion.](./media/ios-12-cp-enroll-1904.PNG)  

9. Revenez à l’application Portail d’entreprise. Le portail d’entreprise commence à synchroniser et à configurer votre appareil. Le portail d’entreprise peut vous inviter à mettre à jour des paramètres d’appareil supplémentaires. Si c’est le cas, appuyez sur **Continuer**.  

10. La configuration est terminée quand tous les éléments de la liste montrent une coche verte. Appuyez sur **Terminé**.   

> [!Note]
> Si votre organisation surveille les limites pour la voix et les données, ou si elle vous fournit un appareil d’entreprise, quelques étapes supplémentaires peuvent être nécessaires pour terminer la configuration. Si vous êtes invité à installer l’application **Datalert**, consultez [Inscription de votre appareil dans la gestion des dépenses de télécommunication](enroll-your-device-with-telecom-expense-management-ios.md). Si votre organisation fait partie du programme DEP d’Apple, découvrez [comment inscrire votre appareil d’entreprise](enroll-your-device-dep-ios.md).  

### <a name="secure-work-related-apps-and-data"></a>Sécuriser les applications et les données liées au travail  
1. L’écran **Télécharger Microsoft Authenticator** apparaît (si vous avez déjà Authenticator, vous ne voyez pas cet écran et vous pouvez passer à l’étape 2).  
    1. Appuyez sur **Télécharger à partir de l’App Store**.
    2. Quand l’App Store s’ouvre, installez l’application. 
    3. Revenez au portail d’entreprise et appuyez sur **Continuer**.    
    
   Une fois Microsoft Authenticator installé, vous n’avez rien d’autre à faire avec l’application. Elle doit simplement être présente sur votre appareil. 

   ![Exemple de capture d’écran du portail d’entreprise, écran « Télécharger Microsoft Authenticator ».](./media/download-ms-authenticator-1909.PNG)  

2. Dans l’écran **Gestion des appareils et confidentialité**, parcourez la liste des informations présentes sur l’appareil que votre organisation peut ou ne peut pas voir. Appuyez ensuite sur **Continuer**.  


 > [!IMPORTANT]
> Ces étapes et ces écrans suivants diffèrent selon votre version d’iOS. Suivez les étapes correspondant à votre version d’iOS. 

3. Safari ouvre le site web Portail d’entreprise sur votre appareil. Quand vous êtes invité à télécharger le profil de configuration, appuyez sur **Autoriser**. Si vous êtes sur un appareil exécutant :  
    * iOS 12.2 et ultérieur : quand le téléchargement est terminé, appuyez sur **Fermer**. Passez ensuite à l’étape 4.  
    * iOS 12.1 et antérieur : Une fois le téléchargement terminé, vous êtes automatiquement redirigé vers l’application Paramètres. Passez à l’étape 5.  
 
    Si vous appuyez accidentellement **Ignorer**, actualisez la page. Vous êtes invité à ouvrir l’application Portail d’entreprise. Dans l’application, vous pouvez appuyer sur **Retélécharger**.

  > [!NOTE]
  > Vous devez installer le profil de gestion comme décrit dans les étapes suivantes dans les 8 minutes de son téléchargement. Si vous ne le faites pas, le profil est supprimé et vous devez recommencer l’inscription.  

4. Quand vous êtes invité à ouvrir le portail d’entreprise, appuyez sur **Ouvrir**. Lisez les informations contenues dans l’écran **Comment installer le profil de gestion**. 

5. Accédez à l’application Paramètres et appuyez sur **Inscrire dans <nom de l’organisation>** ou **Profil téléchargé**.  

    ![Exemple de capture d’écran de l’application Paramètres, option Inscrire dans organisation.](./media/enroll-in-organization-ios-1909.PNG)  

   Si vous ne voyez pas ces options, accédez à **Général** > **Profils et gestion des appareils**> **Profil de gestion**. Si vous ne voyez toujours pas le profil de gestion, il peut être nécessaire de le retélécharger.   


6. Dans l’écran **Inscription de l’utilisateur**, appuyez sur **Inscrire mon iPhone**.  

    ![Exemple de capture d’écran de l’application Paramètres, écran « Inscription de l’utilisateur » avec le bouton Inscrire mis en surbrillance.](./media/user-enrollment-information-1909.PNG)  

7. Entrez le mot de passe de l’appareil. Appuyez ensuite sur **Installer**.  

8. Dans l’écran **Connexion**, entrez le mot de passe de votre identifiant Apple géré. Dans la plupart des cas, ces informations d’identification sont les mêmes que celles que vous utilisez pour vous connecter à votre compte professionnel ou scolaire, sauf si votre organisation vous a fourni un ensemble différent d’informations d’identification. 
9. Appuyez sur **Connexion**.  
10. Un message de réussite apparaît brièvement à l’écran après l’installation du profil. Pour vérifier que le profil est installé, accédez aux paramètres  **Profils et gestion des appareils** . Vous devez normalement voir le profil sous  **Gestion des appareils mobiles**.  

    ![Exemple de capture d’écran de l’application Paramètres, paramètres de Profils & gestion des appareils, montrant le profil de gestion.](./media/ios-12-cp-enroll-1904.PNG)  

11. Revenez à l’application Portail d’entreprise. Le portail d’entreprise commence à synchroniser et à configurer votre appareil. Le portail d’entreprise peut vous inviter à mettre à jour des paramètres d’appareil supplémentaires. Si c’est le cas, appuyez sur **Continuer**.    

12. La configuration est terminée quand tous les éléments de la liste montrent une coche verte. Appuyez sur  **Terminé**.  

## <a name="it-administrator-support"></a>Support technique pour les administrateurs informatiques  
Si vous êtes administrateur informatique et que vous rencontrez des problèmes lors de l’inscription d’appareils, consultez [Résolution des problèmes d’inscription d’appareils iOS dans Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Cet article liste les erreurs courantes, leurs causes et les étapes pour les résoudre.  

## <a name="next-steps"></a>Étapes suivantes  
Recherchez des applications qui vous aident dans le domaine professionnel ou scolaire. Découvrez [comment les applications sont rendues disponibles](use-managed-apps-on-your-device-ios.md) via le portail d’entreprise.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Vous trouverez ses coordonnées sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
