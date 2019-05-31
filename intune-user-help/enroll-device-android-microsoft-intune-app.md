---
title: Inscrire des appareils d’entreprise avec l’application Microsoft Intune | Microsoft Docs
description: Décrit comment inscrire un appareil Android d’entreprise dans Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e68e404a91927192f1006626d1b865acd5eb589
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197041"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Inscrire votre appareil d’entreprise avec l’application Microsoft Intune

Inscrivez votre appareil Android d’entreprise pour obtenir un accès sécurisé à l’e-mail, aux applications et à d’autres données que votre organisation rend disponibles. L’application Microsoft Intune prend en charge les appareils d’entreprise exécutant Android 6.0 et ultérieur. Il est installé automatiquement lors de l’inscription sur les nouveaux appareils et sur les appareils faisant l’objet d’une réinitialisation aux paramètres d’usine. 

Il existe quatre façons de s’inscrire. Votre organisation doit vous faire savoir quelle option utiliser.
 
* NFC (Communication en champ proche)  
* Jeton  
* Code QR   
* Google Zero Touch  

## <a name="enroll-device"></a>Inscrire un appareil 
Effectuez ces étapes pour configurer et inscrire votre appareil.  

> [!NOTE]
> La version d’Android ou le fabricant de l’appareil peut vous demander d’effectuer des étapes supplémentaires qui ne sont pas décrites dans cette procédure. Les couleurs et le texte que vous voyez dans les captures d’écran peuvent également être différents sur votre appareil.  

1. Allumez votre nouvel appareil ou votre appareil réinitialisé aux paramètres d’usine.  
2. Sur l’écran de **Bienvenue**, sélectionnez votre langue.   Si vous avez été invité à vous inscrire avec un code QR ou avec NFC, suivez la procédure ci-dessous qui correspond à la méthode.  
     * NFC : Placez votre appareil pris en charge par NFC à côté d’un appareil programmeur pour vous connecter au réseau de votre organisation. Suivez les invites à l’écran. Quand vous atteignez l’écran pour les conditions d’utilisation du service de Chrome, passez à l’étape 5.  

      * Code QR : suivez les étapes de [Inscription avec un code QR](#qr-code-enrollment).  

      S’il vous a été demandé d’utiliser une autre méthode, passez à l’étape 3.    

1. Connectez-vous au Wi-Fi, puis appuyez sur **SUIVANT**. Suivez l’étape qui correspond à votre méthode d’inscription. 

    * Jeton : Quand vous accédez à l’écran de connexion de Google, suivez les étapes de [Inscription avec un jeton](#token-enrollment).    
    * Google Zero Touch : Une fois que vous êtes connecté au Wi-Fi, votre appareil est reconnu par votre organisation. Passez à l’étape 4 et suivez les invites à l’écran jusqu’à ce que la configuration soit terminée.    
 
       ![Exemple d’image de l’écran des conditions d’utilisation de Google que vous voyez si vous utilisez Google Zero Touch, mettant en évidence le bouton Accepter et continuer.](./media/google-zero-touch-intune-app-01.png)   
   
4. Passez en revue les conditions d’utilisation de Google. Appuyez ensuite sur **ACCEPTER ET CONTINUER**.  

      ![Exemple d’image de l’écran des conditions d’utilisation de Google, mettant en évidence le bouton Accepter et continuer.](./media/fully-managed-intune-app-04.png)   

6. Passez en revue les conditions d’utilisation du service de Chrome. Appuyez ensuite sur **ACCEPTER ET CONTINUER**.  

   ![Exemple d’image de l’écran des conditions d’utilisation du service de Chrome, mettant en évidence le bouton Accepter et continuer.](./media/fully-managed-intune-app-06.png)   

7. Sur l’écran de connexion, connectez-vous avec votre compte professionnel ou scolaire.   

    a. Entrez votre adresse e-mail et appuyez sur **Suivant**.      
    b. Entrez votre mot de passe et appuyez sur **Se connecter**.  

8. Selon les exigences de votre organisation, vous pouvez être invité à mettre à jour des paramètres, comme le verrouillage d’écran ou le chiffrement. Si vous voyez ces invites, appuyez sur **DÉFINIR** et suivez les instructions à l’écran.  

   ![Exemple d’image de l’écran de configuration de votre téléphone professionnel, mettant en évidence le bouton Définir.](./media/fully-managed-intune-app-10.png)   

9. Pour installer des applications professionnelles sur votre appareil, appuyez sur **INSTALLER**. Une fois l’installation terminée, appuyez sur **SUIVANT**.  

   ![Exemple d’image de l’écran de configuration de votre téléphone professionnel, mettant en évidence le bouton Installer.](./media/fully-managed-intune-app-11.png)   

10. Quand vous recevez le message indiquant que votre appareil est prêt, appuyez sur **TERMINÉ**. 

11. Accédez à vos applications et ouvrez l’application Microsoft Intune. Sélectionnez **SE CONNECTER**. 

12. Dans l’écran **Configurer l’accès**, vous voyez une liste de tâches en attente. Appuyez sur **CONTINUER**.  

       ![Exemple d’image de l’application Microsoft Intune, écran Configurer l’accès, montrant des tâches en attente.](./media/fully-managed-intune-app-14.png)   

13. Une fois l’inscription de l’appareil terminée, appuyez sur **CONTINUER**. Microsoft Intune peut vous inviter à mettre à jour des paramètres d’appareil supplémentaires.   

       ![Exemple d’image de l’application Microsoft Intune, écran Mettre à jour les paramètres de l’appareil.](./media/fully-managed-intune-app-15-2.png)   

14. La configuration est terminée quand un cercle vert apparaît pour tous les éléments de la liste. Vous pouvez désormais accéder aux ressources de l’entreprise.  

       ![Exemple d’image de l’application Microsoft Intune, écran Configurer l’accès, montrant des tâches terminées.](./media/fully-managed-intune-app-16.png)   


## <a name="qr-code-enrollment"></a>Inscription avec un code QR  
Dans cette section, vous allez scanner le code QR fourni par votre entreprise.  Quand vous avez terminé, nous vous redirigeons vers les étapes d’inscription de l’appareil.     
  
1. Dans l’écran **Bienvenue**, appuyez sur l’écran cinq fois de suite pour démarrer la configuration du code QR.  

   ![Exemple d’image de l’écran Bienvenue de la configuration de l’appareil, mettant en évidence les instructions indiquant d’appuyer sur l’écran.](./media/qr-code-intune-app-01.png)  

2. Suivez les instructions à l’écran pour vous connecter au Wi-Fi.  
3. Si votre appareil n’a pas de scanneur de code QR, les écrans de configuration montrent la progression dès lors qu’un scanneur est installé. Attendez que l’installation se termine.  
4. Quand vous y êtes invité, scannez le code QR du profil d’inscription que votre organisation vous a donné.  
5. Revenez à [Inscription de l’appareil](#enroll-device), à l’étape 4, pour continuer l’installation.  

## <a name="token-enrollment"></a>Inscription avec un jeton  
Dans cette section, vous allez entrer le jeton fourni par votre entreprise. Quand vous avez terminé, nous vous redirigeons vers les étapes d’inscription de l’appareil.  

1. Dans l’écran de connexion de Google, dans la zone **E-mail ou téléphone**, tapez **afw#setup**. Appuyez sur **Suivant**. 

   ![Exemple d’image de l’écran de connexion Google, indiquant que « afw#setup » est tapé dans le champ.](./media/token-intune-app-01.png)   

2. Choisissez **Installer** pour l’application **Stratégie de l’appareil Android**. Continuez l’installation. En fonction de votre appareil, vous devrez peut-être passer en revue et accepter des conditions d’utilisation supplémentaires.    

3. Dans l’écran **Inscrire cet appareil**, sélectionnez **Suivant**.  

   ![Exemple d’image de l’écran Inscrire cet appareil. Montre l’illustration d’un code QR ; met en évidence le bouton Suivant.](./media/token-intune-app-02.png)  

4. Sélectionnez **Entrer le code**.

   ![Exemple de capture d’écran d’un scanneur de code QR actif. Met en évidence le bouton Entrer le code.](./media/token-intune-app-03.png)  

5. Dans l’écran **Scanner ou entrer le code**, tapez le code que votre organisation vous a donné.  Cliquez ensuite sur **Suivant**.  

   ![Exemple d’image de l’écran Scanner ou entrer le code, mettant en évidence le bouton Suivant.](./media/token-intune-app-04.png)  

6. Revenez à [Inscription de l’appareil](#enroll-device), à l’étape 4, pour continuer l’installation.  



## <a name="next-steps"></a>Étapes suivantes   
Encore besoin d’aide ? Contactez le support technique de votre entreprise (consultez le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour les informations de contact) ou écrivez à <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">l’équipe Microsoft Android</a>.  
