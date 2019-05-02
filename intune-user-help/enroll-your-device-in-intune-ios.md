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

Une fois votre appareil est inscrit, il devient *gérés*. Votre organisation peut affecter des stratégies et des applications à l’appareil via un fournisseur de gestion (MDM) des appareils mobiles, comme Intune.  

Pour conserver l’accès aux informations professionnelles ou scolaires à partir de votre appareil, vous devez configurer l’appareil avec les paramètres par défaut de votre organisation. Cet article décrit l’utilisation de portail d’entreprise pour vous inscrire appareil et de mettre à jour les exigences de configuration de votre organisation. 

> [!NOTE]
> Si vous avez essayé d’accéder à vos e-mails professionnels dans la messagerie d’entreprise et avez reçu un message vous invitant à passer votre appareil en mode géré, vous êtes au bon endroit. Suivez les instructions ci-dessous pour accéder à vos e-mails et à d’autres ressources de l’entreprise sur votre appareil iOS.  

## <a name="what-to-expect-from-the-company-portal-app"></a>À quoi s’attendre avec l’application Portail d’entreprise ?  

### <a name="security"></a>Sécurité  
Pendant l’installation initiale, l’application vous demande de vous authentifier auprès de votre organisation. Ensuite, elle vous indique les paramètres que vous devez mettre à jour sur votre appareil. Par exemple, les organisations définissent souvent des critères de longueur de mots de passe auxquels vous devez vous plier.     

### <a name="protection"></a>Protection  
Une fois votre appareil inscrit, l’application Portail d’entreprise continue de s’assurer que votre appareil est protégé. Par exemple, si vous installez une application à partir d’une source non fiable, l’application vous alerte et révoque parfois l’accès aux données de l’entreprise. Ce type de stratégie est courant dans les organisations et souvent vous oblige à désinstaller l’application non approuvée avant de vous retrouver l’accès.  

### <a name="setting-notifications"></a>Définition des notifications  
Si après l’inscription votre organisation impose une nouvelle exigence de sécurité, telle que l’authentification multifacteur, l’application Portail d’entreprise vous avertit. Vous aurez la possibilité d’ajuster vos paramètres afin de pouvoir continuer à travailler sur votre appareil.  

Pour plus d’informations sur l’inscription, consultez [Que se passe-t-il quand j’installe l’application Portail d’entreprise et que j’inscris mon appareil ?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Inscrire votre appareil iOS  

Accédez à l’App store pour télécharger et installer le [application portail d’entreprise Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md) sur votre appareil. Vous devrez également maintenir une connexion Wi-Fi et ont accès à Safari lors de l’inscription. 

Une interruption de plus de quelques minutes lors de l’inscription peut entraîner l’application à fermer ou de terminer le programme d’installation. Si cela se produit, ouvrez l’application portail d’entreprise et réessayez.  

1. Ouvrez Portail d’entreprise et connectez-vous avec votre compte professionnel ou scolaire. 

    ![Capture d’écran de l’application portail d’entreprise, de connexion.](./media/ios-01-cp-enroll-1903.PNG)  

2. Quand vous y êtes invité pour recevoir des notifications du portail d’entreprise, appuyez sur **autoriser.** Portail d’entreprise utilise des notifications pour vous avertir si, par exemple, vos paramètres de périphérique doivent être mis à jour. 

    ![Capture d’écran de la page d’accueil de portail d’entreprise, invite de « Notifications ».](./media/ios-04-cp-enroll-1903.PNG)  

3. Sur le **configurer l’accès** s’affiche, sélectionnez **commencer.**  

     ![Capture d’écran du portail d’entreprise, écran « Configurer l’accès ».](./media/ios-05-cp-enroll-1903.PNG)  

4. Lisez la liste des informations sur l’appareil votre organisation peut voir ou non. Puis appuyez sur **continuer**.  

5. Lisez les instructions sur la **quelle est la suite ?** écran. Lorsque vous êtes prêt à télécharger et installer le profil de gestion, appuyez sur **continuer**.  

 > [!IMPORTANT]
> Ces étapes suivantes et les écrans diffèrent selon votre version d’iOS. Suivez les étapes correspondant à votre version d’iOS. 

6. Safari ouvre le site Web portail d’entreprise sur votre appareil. Lorsque vous êtes invité à télécharger le profil de configuration, appuyez sur **autoriser**. Si vous êtes sur un appareil en cours d’exécution :  
    * iOS 12,2 et versions ultérieures : quand le téléchargement est terminé, appuyez sur **terminé.** Passez à étape 7 de cet article.
    * iOS 12.1 et versions antérieures : vous allez être automatiquement redirigé vers l’application paramètres. Passez à l’étape 8 dans cet article.  
 
    Si vous appuyez accidentellement **ignorer**, actualisez la page. Vous allez être invité à ouvrir l’application portail d’entreprise. À partir de l’application, vous pouvez appuyer sur **retélécharger**.

  > [!NOTE]
  > Vous devez installer le profil de gestion, comme décrit dans les étapes suivantes dans les 8 minutes de téléchargement. Si vous n’est pas le cas, le profil sera supprimé et vous devrez redémarrer l’inscription.  

7. iOS 12,2 et versions ultérieures uniquement : lorsque vous êtes invité à ouvrir le portail d’entreprise, appuyez sur **ouvrir**. Le **profil de gestion de l’installation** écran répertorie les étapes pour installer le profil.

    ![Capture d’écran du portail d’entreprise, écran de profil de gestion de l’installation.](./media/ios-1904-settings-icon.PNG)  

8. Accédez à l’application de paramètres, puis appuyez sur **profil téléchargé**.  

    Si **profil téléchargé** n’apparaissent sous la forme d’une option, accédez à **général** > **profils**. Si vous ne voyez pas le profil, vous devrez peut-être télécharger à nouveau.  

    ![Capture d’écran de l’application paramètres, profil téléchargé définition.](./media/ios-1904-settings-badge.PNG)  

9. Appuyez sur **Installer**.  
    
10. Entrez le mot de passe de votre appareil. Puis appuyez sur **installer**.    

    ![Capture d’écran de l’application de paramètres, écran de profil de l’installation, avec un curseur sur le ** installer ** bouton.](./media/ios-1904-password-install.PNG)  


11. L’écran suivant est un avertissement de système standard pour la gestion des appareils. Pour continuer l’installation, appuyez sur **installer**. Si vous êtes invité à approuver la gestion à distance, appuyez sur **approbation**.  

    ![Capture d’écran de l’application paramètres, l’écran d’avertissement système standard pour le certificat racine et de gestion des appareils mobiles.](./media/ios-15-cp-enroll-1903.PNG)  

12. Une fois l’installation terminée, appuyez sur **fait**. Pour vérifier que le profil a été installé, accédez à la **profils et gestion des appareils** paramètres. Vous devez voir le profil figurant sous **gestion des appareils mobiles**.   

    ![Capture d’écran de l’exemple d’application de paramètres, les profils et gestion des appareils paramètres, montrant le profil de gestion.](./media/ios-00-cp-enroll-1903.PNG)  

13. Retournez dans l’application Portail d’entreprise. Portail d’entreprise commence à synchroniser et configurer votre appareil. Portail d’entreprise peut vous inviter à mettre à jour les paramètres de périphérique supplémentaires. Si elle est le cas, appuyez sur **continuer**.  

    ![Capture d’écran du portail d’entreprise, « Configurer l’accès » de l’écran, avec un triangle jaune en regard de la spécification de paramètre.](./media/ios-12-cp-enroll-1903.PNG)  

14. Vous saurez que l’installation est terminée lorsque tous les éléments dans la liste affichent un cercle vert. Appuyez sur **Terminé**.   
    
    ![Capture d’écran du portail d’entreprise, « vous voilà prêt ! » écran, affichant tous les cercles verts.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Si votre organisation surveille les limites de voix et de données, ou vous offre un appareil appartenant à l’entreprise, vous pouvez avoir quelques étapes supplémentaires pour terminer. Si vous êtes invité à installer le **Datalert** application, consultez [en inscrivant votre appareil dans la gestion des dépenses de télécommunications](enroll-your-device-with-telecom-expense-management-ios.md). Si votre organisation fait partie du programme DEP d’Apple, Découvrez [comment inscrire votre appareil d’entreprise](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Étapes suivantes  
Rechercher des applications qui vous aideront à professionnel ou scolaire. En savoir plus [comment les applications sont mises à disposition](use-managed-apps-on-your-device-ios.md) via le portail d’entreprise.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Vous trouverez ses coordonnées sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
