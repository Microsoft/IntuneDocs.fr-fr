---
title: Inscrire un appareil iOS ou iPados avec Portail d’entreprise Intune et DISA purebred
description: Découvrez comment inscrire un appareil iOS ou iPados et configurer l’authentification dérivée des informations d’identification avec DISA purebred.
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
ms.openlocfilehash: 31858828cbbfaa1ca71d94f6e0f568c35bb490c1
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856577"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>Configurer un appareil iOS ou iPados avec Portail d’entreprise et DISA purebred  

Inscrivez votre appareil avec l’application Portail d’entreprise Intune pour obtenir un accès mobile et sécurisé aux e-mails, aux fichiers et aux applications de votre organisation. Une fois que votre appareil est inscrit, il devient *géré*. Votre organisation peut affecter des stratégies et des applications à l’appareil via un fournisseur MDM, comme Intune.  

Lors de l’inscription, vous allez également installer des informations d’identification dérivées sur votre appareil. Votre organisation peut vous obliger à utiliser les informations d’identification dérivées comme méthode d’authentification lors de l’accès aux ressources, ou pour la signature et le chiffrement des messages électroniques. 

Vous devez probablement configurer des informations d’identification dérivées si vous utilisez une carte à puce pour :

* Se connecter à des applications scolaires ou professionnelles, à des réseaux Wi-Fi et à des réseaux privés virtuels (VPN)
* Signer et chiffrer des e-mails scolaires ou professionnels à l’aide de certificats S/MIME  

Cet article vous apprendra les éléments suivants :  

   * Inscrire un appareil mobile iOS ou iPados avec Portail d’entreprise Intune.  
   * Obtenir des informations d’identification dérivées du fournisseur d’informations d’identification dérivé de votre organisation, [DISA purebred](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>Que sont les informations d’identification dérivées ?  
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

Vous devez également contacter un agent ou un représentant purebred au cours de l’installation.      

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
    a. Appuyez sur le lien vers les instructions de configuration de votre organisation. Si votre organisation ne fournit pas d’instructions supplémentaires, vous êtes redirigé vers cet article.  
    b. Cliquez sur **ouvrir** pour ouvrir l’application purebred.  

    ![Exemple de capture d’écran de l’écran de configuration de l’accès à la carte à puce mobile Portail d’entreprise.](./media/smart-card-open-disa-purebred.png)  
9. Lorsque vous êtes invité à autoriser Portail d’entreprise à ouvrir l’application d’inscription purebred, sélectionnez **ouvrir**.   

    ![Exemple de capture d’écran de l’invite de Portail d’entreprise pour ouvrir l’application DISA purebred.](./media/open-app-prompt-disa-purbred.png)  
10. Lorsque l’application fonctionne, travaillez avec l’agent purebred de votre organisation pour configurer et télécharger le profil de configuration de pré-inscription purebred.   
11. Accédez à l’application Paramètres > profils de > **généraux** **& de gestion des périphériques** > profil d' **installation** et appuyez sur **installer**.  
12. Entrez le code secret de votre appareil.  
13. Installez le profil. Vous devrez peut-être appuyer sur **installer** plusieurs fois pour démarrer l’installation. 
14. Revenez à l’application d’inscription purebred. Suivez les instructions de votre agent purebred pour continuer.  
 
15. Une fois que vous avez téléchargé le profil de configuration, accédez à l’application Paramètres > **général** > **profils & de gestion des périphériques** > installer un **Profil** et appuyez sur **installer**.   
16.  Entrez le code secret de votre appareil.
17. Installez le profil. Vous devrez peut-être appuyer sur **installer** plusieurs fois pour démarrer l’installation. 
18. Une fois l’installation terminée, revenez à l’application Portail d’entreprise.  
19.  Dans l’écran d’accès à l’installation de la **carte à puce mobile** , appuyez sur **Continuer**.  

20. À partir de l’écran **importer des certificats** , vous allez récupérer et importer les informations d’identification dérivées que vous avez obtenues à partir de DISA purebred.  

    a. Appuyez sur **Continuer**.   

    ![exemple de capture d’écran de l’écran définir des certificats d’importation Portail d’entreprise.](./media/import-certificate-disa-purebred.png)  
    b. Accédez à iCloud lecteur **parcourir** > **emplacements** et appuyez sur **plus d’emplacements**.  

    ![exemple de capture d’écran du lecteur iCloud, parcourir le menu Sélectionner d’autres emplacements.](./media/icloud-drive-more-locations.png)  
    c. Appuyez sur le commutateur pour activer la **chaîne de clé purebred**.  

    ![Exemple de capture d’écran de lecteur iCloud, vue Parcourir, mise en surbrillance indiquant que le commutateur de la chaîne de clés purebred est activé.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Appuyez sur le **package d’informations d’identification purebred**.  

    ![exemple de capture d’écran d’un écran iOS avec une option de package d’informations d’identification purebred sélectionnable.](./media/purebred-credential-package.png)  
    f. Une liste de certificats s’affiche. Sélectionnez-en un, puis appuyez sur **Importer la clé**.  

    ![Exemple de capture d’écran d’une liste de certificats sélectionnables, avec un tel est déjà sélectionné.](./media/import-purebred-keychain.png) 
21. Revenez à l’application Portail d’entreprise et attendez que Portail d’entreprise termine la configuration de votre appareil.   

## <a name="next-steps"></a>Étapes suivantes  
Une fois l’inscription terminée, vous aurez accès aux ressources de travail, telles que la messagerie, le Wi-Fi et toutes les applications que votre organisation met à disposition. Pour plus d’informations sur la façon d’obtenir, de rechercher, d’installer et de désinstaller des applications dans le Portail d’entreprise consultez :

* [Gérer des applications à partir du site web du portail d’entreprise](manage-apps-cpweb.md)  
* [Utiliser des applications gérées sur votre appareil](use-managed-apps-on-your-device-ios.md)  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
