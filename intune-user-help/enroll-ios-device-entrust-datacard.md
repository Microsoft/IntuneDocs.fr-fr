---
title: Inscrire un appareil iOS ou iPados avec Portail d’entreprise Intune et Entrust Datacard
description: Inscrire un appareil iOS ou iPados et configurer l’authentification des informations d’identification dérivées avec Entrust Datacard.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: b976e9a47a56c7af1e754f5b5b0162410e278025
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856390"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-entrust-datacard"></a>Configurer un appareil iOS ou iPados avec Portail d’entreprise et Entrust Datacard

Inscrivez votre appareil avec l’application Portail d’entreprise Intune pour obtenir un accès mobile et sécurisé aux e-mails, aux fichiers et aux applications de votre organisation. Une fois que votre appareil est inscrit, il devient *géré*. Votre organisation peut affecter des stratégies et des applications à l’appareil via un fournisseur MDM, comme Intune.  

Lors de l’inscription, vous allez également installer des informations d’identification dérivées sur votre appareil. Votre organisation peut vous obliger à utiliser les informations d’identification dérivées comme méthode d’authentification lors de l’accès aux ressources, ou pour la signature et le chiffrement des messages électroniques. 

Vous devez probablement configurer des informations d’identification dérivées si vous utilisez une carte à puce pour :  

* Se connecter à des applications scolaires ou professionnelles, à des réseaux Wi-Fi et à des réseaux privés virtuels (VPN)
* Signer et chiffrer des e-mails scolaires ou professionnels à l’aide de certificats S/MIME  

Cet article vous apprendra les éléments suivants :  

   * Inscrire un appareil mobile iOS ou iPados avec Portail d’entreprise Intune.  
   * Obtenir des informations d’identification dérivées du fournisseur d’informations d’identification dérivé de votre organisation, [Entrust Datacard](https://www.entrustdatacard.com/).  

### <a name="what-are-derived-credentials"></a>Que sont les informations d’identification dérivées ?  
Les informations d’identification dérivées sont un certificat dérivé de vos informations d’identification de carte à puce et installées sur votre appareil. Elle vous permet d’accéder à distance aux ressources de travail, tout en empêchant les utilisateurs non autorisés d’accéder à des informations sensibles.  

Les informations d’identification dérivées sont utilisées pour : 
* Authentifier les élèves et les employés qui se connectent aux applications scolaires ou professionnelles, au Wi-Fi et au VPN
* Signer et chiffrer des e-mails scolaires ou professionnels avec des certificats S/MIME

Les informations d’identification dérivées sont une implémentation des recommandations du NIST (National Institute of Standards and Technology) en matière d’informations d’identification de vérification de l’identité personnelle (PIV) dérivées, fournies dans la publication spéciale (SP) 800-157.  

## <a name="prerequisites"></a>Prérequis

 Pour terminer l’inscription, vous devez disposer des éléments suivants :

* Votre école ou carte à puce fournie par votre entreprise
* Accès à un ordinateur ou une borne où vous pouvez vous connecter avec votre carte à puce
* Votre appareil mobile
* L’application Portail d’entreprise Intune pour iOS et iPados est installée sur votre appareil  


## <a name="enroll-device"></a>Inscrire un appareil  
1. Ouvrez l’application Portail d’entreprise pour iOS/iPad sur votre appareil mobile et connectez-vous avec votre compte professionnel.  

2. Notez le code affiché à l’écran.  

    ![Exemple d’image de Portail d’entreprise application avec le code et le message à l’écran.](./media/copy-code-intercede.png)   

3. Basculez vers votre appareil compatible avec la carte à puce et accédez à https://microsoft.com/devicelogin. 
4. Entrez le code que vous avez écrit précédemment.  

    ![Exemple de capture d’écran de l’invite de Portail d’entreprise site Web « Enter Code ».](./media/enter-code-intercede.png)   

5. Insérez votre carte à puce pour vous connecter.   
6. Revenez à l’application Portail d’entreprise sur votre appareil mobile et suivez les instructions à l’écran pour inscrire votre appareil.  
7. Une fois l’inscription terminée, Portail d’entreprise vous informera de la configuration de votre carte à puce. Appuyez sur la notification. Si vous ne recevez pas de notification, vérifiez votre adresse de messagerie.   

    ![Exemple de capture d’écran de la Portail d’entreprise notification push sur l’écran d’accueil de l’appareil.](./media/action-required-in-app-intercede.png)  

8. Sur l’écran d’accès à la configuration de la **carte à puce mobile** :   
    a. Appuyez sur le lien vers les instructions d’installation de votre organisation. Si votre organisation ne fournit pas d’instructions supplémentaires, vous êtes redirigé vers cet article.  
    b. Appuyez sur **commencer**.  

    ![Exemple de capture d’écran de l’écran de configuration de l’accès à la carte à puce mobile Portail d’entreprise.](./media/smart-card-info-intercede.png)

9. Basculez vers votre appareil compatible avec la carte à puce et ouvrez IdentityGuard. 
10. Recherchez la zone connexion intelligente des informations d’identification et sélectionnez le bouton de connexion.  
11. Lorsque vous êtes invité à sélectionner un certificat, choisissez les informations d’identification de votre carte à puce. Cliquez ensuite sur **OK**. 
12. Entrez le code confidentiel de votre carte à puce.  
13. Vous êtes invité à choisir dans une liste d’actions. Sélectionnez celui qui vous permet d’inscrire des informations d’identification Smart Mobile dérivées. Le lien ou le bouton peut indiquer que **j’aimerais s’inscrire pour une information d’identification de carte à puce mobile dérivée.**  
14. Sélectionnez que vous avez téléchargé et installé avec succès l’application compatible avec les informations d’identification intelligentes. Passez ensuite à l’écran suivant.   
15. Entrez des informations sur vos informations d’identification de carte à puce dérivées.  
    a. Pour le nom de l’identité, entrez un nom quelconque, par exemple *Entrust Derived cred*.  
    b. Dans le menu déroulant, sélectionnez **Entrust IdentityGudard mobile intelligent Credential**.  
    c. Passez à l’écran suivant. Vous verrez un code QR avec un mot de passe numérique sous celui-ci.  

16. Revenez à votre appareil mobile. Dans l’écran Portail d’entreprise > **accéder au code QR** , appuyez sur **Continuer**. 

    ![Exemple de capture d’écran de l’écran Portail d’entreprise de l’extraction du code QR.](./media/get-qr-code-intercede.png)  
17. Appuyez sur **utiliser l’appareil photo** > **OK**.  

    ![Exemple de capture d’écran d’une invite de Portail d’entreprise demandant l’autorisation d’autoriser l’accès à l’appareil photo.](./media/allow-cp-camera-access-intercede.png)  
18. Numérisez l’image du code QR sur votre appareil compatible avec la carte à puce.  
19. Entrez le mot de passe numérique qui apparaît sous le code QR.  

    ![Exemple de capture d’écran de l’écran Portail d’entreprise mot de passe requis, entrez le champ mot de passe.](./media/enter-password-derived-credentials.png)   

20. Attendez que Portail d’entreprise termine la configuration de votre appareil.  


## <a name="next-steps"></a>Étapes suivantes  
Une fois l’inscription terminée, vous aurez accès aux ressources de travail, telles que la messagerie, le Wi-Fi et toutes les applications que votre organisation met à disposition. Pour plus d’informations sur la façon d’obtenir, de rechercher, d’installer et de désinstaller des applications dans le Portail d’entreprise consultez :

* [Gérer des applications à partir du site web du portail d’entreprise](manage-apps-cpweb.md)  
* [Utiliser des applications gérées sur votre appareil](use-managed-apps-on-your-device-ios.md)  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
