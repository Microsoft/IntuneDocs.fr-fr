---
title: Inscrire un appareil Android avec le portail d’entreprise Intune | Microsoft Docs
description: Décrit comment inscrire un appareil Android avec le portail d’entreprise Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5baf0e9079cc148101a68e5cd2d3a4ed500f567f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414861"
---
# <a name="enroll-your-device-with-company-portal"></a>Inscrire votre appareil Android avec le portail d’entreprise  
Inscrivez votre appareil Android personnel ou d’entreprise pour obtenir un accès sécurisé à l’e-mail, aux applications et aux données de l’entreprise. Le portail d’entreprise prend en charge les appareils Android, notamment Samsung Knox, exécutant Android 4.4 et ultérieur.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox est un type de sécurité que certains appareils Samsung utilisent pour avoir une protection supplémentaire par rapport aux appareils Android natifs. Pour vérifier si vous avez un appareil Samsung Knox, accédez à **Paramètres** > **À propos de l’appareil**. Si **Version Knox** n’apparaît pas dans la liste, c’est que vous avez un appareil Android natif.

## <a name="enroll-device"></a>Inscrire un appareil  
Veillez à [installez l’application Portail d’entreprise Intune gratuite à partir de Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Au cours de l’inscription, vous pouvez être invité à choisir une catégorie qui décrit le mieux votre utilisation de l’appareil. Le support technique de votre entreprise utilise votre réponse pour vérifier les applications auxquelles vous avez accès.  

1. Ouvrez l’application Portail d’entreprise et connectez-vous avec votre compte professionnel ou scolaire.  

2. Si vous êtes invité à accepter les termes et conditions de votre organisation, appuyez sur **ACCEPTER TOUT**.  

   ![Exemple d’image du Portail d’entreprise, écran des conditions, en mettant en surbrillance le bouton « accepter tout ».](./media/accept-terms-1911.png)  


3. Examinez ce que votre organisation peut et ne peut pas voir. Appuyez ensuite sur **CONTINUER**.


    ![Exemple d’image de Portail d’entreprise, nous nous soucions de votre écran de confidentialité, en mettant en surbrillance le bouton continuer.](./media/android-privacy-screen-1911.png)  
4. Examinez ce qu’il faut attendre dans les étapes à venir. Appuyez ensuite sur **suivant**.  

    ![Exemple d’image de Portail d’entreprise, écran suivant, en mettant en surbrillance le bouton suivant.](./media/android-whats-next-1911.png)  


5. Selon votre version d’Android, vous pouvez être invité à autoriser l’accès à certaines parties de votre appareil. Ces invites sont requises par Google et ne sont pas contrôlées par Microsoft.  

    Appuyez sur **autoriser** pour les autorisations suivantes :  
    * **Autoriser portail d’entreprise à créer et gérer des appels téléphoniques**: cette autorisation permet à votre appareil de partager son numéro IMEI (Mobile Station Equipment Identity) avec Intune, le fournisseur de gestion des appareils de votre organisation. Il est possible d’autoriser cette autorisation. Microsoft ne fera jamais ou ne gérera jamais d’appels téléphoniques.  
    * **Autoriser portail d’entreprise à accéder à vos contacts**: cette autorisation permet à l’application portail d’entreprise de créer, utiliser et gérer votre compte professionnel.  Il est possible d’autoriser cette autorisation. Microsoft n’accédera jamais à vos contacts. 

    Si vous refusez l’autorisation, vous serez reinvité la prochaine fois que vous vous connecterez à Portail d’entreprise. Pour désactiver ces messages, sélectionnez **Ne plus demander**. Pour gérer les autorisations de l’application, accédez à paramètres application > **applications** > **Portail d’entreprise** > **autorisations** > **téléphone**.  

6. Activez l’application d’administration de l’appareil. 

    Portail d’entreprise a besoin d’autorisations d’administrateur d’appareil pour gérer votre appareil en toute sécurité. L’activation de l’application permet à votre organisation d’identifier les problèmes de sécurité possibles, tels que les tentatives répétées de déverrouillage de votre appareil et la réponse appropriée.  

    ![Exemple d’image de l’écran activer l’administrateur de l’appareil, en mettant en surbrillance le bouton Activer.](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft ne contrôle pas la messagerie sur cet écran. Nous savons que son formulation peut paraître un peu radicale. Portail d’entreprise ne pouvez pas spécifier les restrictions et l’accès qui sont pertinents pour votre organisation. Si vous avez des questions sur la façon dont votre organisation utilise l’application, contactez votre responsable de support informatique. Pour trouver les informations de contact de votre organisation, accédez au [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  


7. L’inscription de votre appareil commence. Si vous utilisez un appareil Samsung Knox, vous êtes invité à examiner et à accepter d’abord la politique de confidentialité de l’agent PUCS.   

    ![Exemple d’image de l’écran de politique de confidentialité Samsung Knox qui s’affiche lors de l’inscription.](./media/and-enroll-7-knox-privacy-policy.png)  

8. Dans l’écran Configuration de l’accès à l' **entreprise** , vérifiez que votre appareil est inscrit. Appuyez ensuite sur **CONTINUER**.  

    ![Exemple d’image de Portail d’entreprise, écran de configuration de l’accès à l’entreprise, qui indique que la gestion de votre appareil est terminée.](./media/update-settings-1911.png)  

9. Votre organisation peut vous demander de mettre à jour les paramètres de votre appareil. Appuyez sur **résoudre** pour ajuster un paramètre. Lorsque vous avez terminé la mise à jour des paramètres, appuyez sur **Continuer**.  

   ![Exemple d’image de Portail d’entreprise, mettre à jour les paramètres de l’appareil, mettre en surbrillance les boutons résoudre et continuer.](./media/resolve-settings-1911.png)  

10. Une fois l’installation terminée, appuyez sur **terminé**.    

    ![Exemple d’image de Portail d’entreprise, écran de configuration de l’accès à l’entreprise, montrant la configuration terminée et le bouton terminé.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>Étapes suivantes  

Avant d’essayer d’installer une application scolaire ou professionnelle, accédez à **paramètres** > **sécurité**et activez **sources inconnues**. Si vous n’activez pas cette option, le message s’affiche quand vous tentez d’installer une application : « Installation bloquée. Pour des raisons de sécurité, votre appareil est configuré pour bloquer les installations d’applications provenant de sources inconnues. Vous pouvez appuyer sur les **paramètres** du message pour accéder directement à **sources inconnues**.  

> [!Note]
> Si votre organisation utilise un logiciel de gestion des dépenses de télécommunications, vous devrez exécuter une procédure supplémentaire pour finaliser l’inscription de votre appareil. Découvrez-en plus [ici](enroll-your-device-with-telecom-expense-management-android.md).

Si vous recevez une erreur pendant que vous inscrivez votre appareil dans Intune, vous pouvez [envoyer un e-mail au support technique de votre entreprise](send-logs-to-your-it-admin-by-email-android.md).  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  