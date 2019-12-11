---
title: Inscrire votre Mac avec Portail d’entreprise Intune | Microsoft Docs
description: Découvrez comment inscrire votre Mac dans Intune avec l’application Portail d’entreprise.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba285fc9de58b3fb739a16722e0e05e36e840e87
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098140"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>Inscrire votre appareil macOS à l’aide de l’application Portail d’entreprise  

Inscrire votre appareil macOS avec l’application Portail d’entreprise Intune pour obtenir un accès sécurisé aux e-mails, aux fichiers et aux applications de votre entreprise ou école.

Les organisations requièrent généralement que vous inscriviez votre appareil avant de pouvoir accéder aux données propriétaires. Une fois que votre appareil est inscrit, il devient *géré*. Votre organisation peut affecter des stratégies et des applications à l’appareil via un fournisseur MDM, comme Intune. Pour obtenir un accès continu aux informations professionnelles ou scolaires sur votre appareil, vous devez le configurer conformément aux paramètres de stratégie de votre organisation.  

Cet article décrit comment utiliser l’application Portail d’entreprise pour macOS pour inscrire, configurer et tenir à jour votre appareil afin de satisfaire aux exigences de votre organisation.  


## <a name="what-to-expect-from-the-company-portal-app"></a>À quoi s’attendre avec l’application Portail d’entreprise ?

Lors de la configuration initiale, l’application Portail d’entreprise vous oblige à vous connecter et à vous authentifier auprès de votre organisation. Portail d’entreprise vous informe ensuite des paramètres de l’appareil que vous devez configurer pour répondre aux besoins de votre organisation. Par exemple, les organisations définissent souvent des critères de longueur de mots de passe auxquels vous devez vous plier.    

Une fois que vous avez inscrit votre appareil, Portail d’entreprise vous assurez toujours que votre appareil est protégé conformément aux exigences de votre organisation. Par exemple, si vous installez une application à partir d’une source non approuvée, Portail d’entreprise vous alerte et peut restreindre l’accès aux ressources de votre organisation. Les stratégies de protection d’application comme celle-ci sont courantes. Pour récupérer l’accès, vous aurez probablement besoin de désinstaller l’application non approuvée. 

Si après l’inscription, votre organisation impose une nouvelle exigence de sécurité, telle que l’authentification multifacteur, l’application Portail d’entreprise vous avertit. Vous aurez la possibilité d’ajuster vos paramètres afin de pouvoir continuer à travailler sur votre appareil.  

Pour plus d’informations sur l’inscription, consultez [Que se passe-t-il quand j’installe l’application Portail d’entreprise et que j’inscris mon appareil ?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-macos-device-managed"></a>Gestion de votre appareil macOS  
Procédez comme suit pour inscrire votre appareil macOS auprès de votre organisation. Votre appareil doit exécuter macOS 10,12 ou une version ultérieure.   

> [!NOTE]
> Tout au long de ce processus, vous pouvez être invité à autoriser Portail d’entreprise à utiliser des informations confidentielles stockées dans votre trousseau. Ces invites font partie de la sécurité Apple. Lorsque vous recevez l’invite, tapez votre mot de passe de Trousseau d’accès et sélectionnez **toujours autoriser**. Si vous appuyez sur **entrée** ou **retour** sur votre **clavier, l’invite sélectionnera**à la place, ce qui peut entraîner des invites supplémentaires.  

### <a name="install-company-portal-app"></a>Installer l’application Portail d’entreprise  
1. Accédez à [inscrire mon Mac](https://go.microsoft.com/fwlink/?linkid=853070).  
2. Le fichier Portail d’entreprise installer. pkg sera téléchargé. Ouvrez le programme d’installation et suivez les étapes. 
3. Acceptez le contrat de licence de logiciel. 
4. Entrez le mot de passe de votre appareil ou votre empreinte digitale pour installer le logiciel.  
5. Ouvrez Portail d’entreprise. 

> [!IMPORTANT]
> Microsoft AutoUpdate peut s’ouvrir pour mettre à jour vos logiciels Microsoft. Une fois toutes les mises à jour installées, ouvrez l’application Portail d’entreprise. Pour une meilleure expérience d’installation, installez les dernières versions de Microsoft AutoUpdate et Portail d’entreprise.  


### <a name="enroll-your-mac"></a>Inscrire votre Mac  


1. Connectez-vous à l’application Portail d’entreprise avec votre compte professionnel ou scolaire.  
2. Lorsque l’application s’ouvre, sélectionnez **Démarrer**.  
3. Examinez [ce que votre organisation peut et ne peut pas voir](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) sur votre appareil inscrit. Ensuite, sélectionnez **Continuer**.  
4. Dans l’écran **installer le profil de gestion** , sélectionnez Télécharger le **Profil**.   

    ![Exemple de capture d’écran de Portail d’entreprise, installer l’écran de profil de gestion, en mettant en surbrillance le bouton « Télécharger le profil ».](./media/install-mgmt-profile-mac-1911.PNG)   
5. Les préférences système de votre appareil s’ouvrent. Sélectionnez **installer** , puis cliquez à nouveau sur **installer** . Si vous y êtes invité, entrez le mot de passe de votre appareil.  

    ![Exemple de capture d’écran des préférences système macOS, invite d’installation, mise en surbrillance du bouton « installer ».](./media/system-preference-install-1911.PNG)  
6. Une fois le profil installé, il s’affiche dans la liste des profils sous le **profil de gestion.**  

   ![Exemple de capture d’écran des préférences système macOS, écran profils et mise en surbrillance du profil de gestion installé.](./media/system-preference-verify-1911.PNG)   
7. Revenez à Portail d’entreprise.   
8. Votre organisation peut vous demander de mettre à jour les paramètres de votre appareil. Lorsque vous avez terminé la mise à jour des paramètres, sélectionnez **vérifier les paramètres**.  

    ![Exemple de capture d’écran de Portail d’entreprise, mettre à jour l’écran Paramètres de l’appareil, en mettant en surbrillance le bouton « vérifier les paramètres »](./media/update-settings-mac-1911.PNG)  
9. Une fois l’installation terminée, sélectionnez **terminé**.  


 ## <a name="troubleshooting-and-feedback"></a>Résolution des problèmes et commentaires   

Si vous rencontrez des problèmes lors de l’inscription, accédez à **aide** > **Envoyer un rapport de diagnostic** pour signaler le problème aux développeurs d’applications Microsoft. Ces informations sont utilisées pour aider à améliorer l’application. Ils utiliseront également ces informations pour aider à résoudre le problème si votre personne du support technique y accède pour obtenir de l’aide.  

Une fois que vous avez signalé le problème à Microsoft, vous pouvez envoyer les détails de votre expérience à votre personne du support technique. Sélectionnez les détails de l' **e-mail**. Tapez ce que vous avez rencontré dans le corps de l’e-mail. Pour Rechercher l’adresse de messagerie de votre personne de support, accédez à l’application Portail d’entreprise > **contact**. Ou consultez le [site web portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

En outre, les Microsoft Intune Portail d’entreprise équipe aimeraient recevoir vos commentaires. Accédez à **aide** > **Envoyer des commentaires** pour partager vos pensées et vos idées.  

## <a name="unverified-profiles"></a>Profils non vérifiés  
Quand vous affichez les profils de gestion des appareils mobiles (MDM) installés dans **Préférences système** > **Profils**, vous verrez peut-être certains profils présentant l’état Non vérifié. Cela n’est pas un problème tant que le profil de gestion affiche l’état Vérifié.  

Le profil de gestion définit la connexion au canal MDM. Quand le profil de gestion est vérifié, tous les autres profils remis à l’ordinateur, par le biais de ce canal, héritent les caractéristiques de sécurité du profil de gestion.  

## <a name="updating-the-company-portal-app"></a>Mise à jour de l’application Portail d’entreprise

La mise à jour de l’application Portail d’entreprise s’effectue de la même façon que pour n’importe quelle autre application Office, par le biais de Microsoft AutoUpdate pour macOS. En savoir plus sur la [mise à jour des applications Microsoft pour macOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Étapes suivantes  
Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  


