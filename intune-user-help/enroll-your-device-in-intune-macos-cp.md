---
title: Inscrire un appareil macOS dans Intune avec l’application Portail d’entreprise | Microsoft Docs
description: Explique comment inscrire un appareil macOS dans Intune avec l’application Portail d’entreprise
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: af5c7492563c8df0168eff3250ae1bbad2cc323e
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147715"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Inscrire votre appareil macOS dans Intune avec l’application Portail d’entreprise

Inscrire votre appareil macOS avec l’application Portail d’entreprise Intune pour obtenir un accès sécurisé aux e-mails, aux fichiers et aux applications de votre organisation.

Les organisations vous obligent souvent à activer la gestion de votre appareil avant que vous puissiez accéder à des données propriétaires à partir de cet appareil. Une fois qu’un appareil est géré, les organisations peuvent lui transmettre des stratégies et des applications par le biais de leur fournisseur de gestion des appareils mobiles. Pour obtenir un accès continu aux informations professionnelles ou scolaires à partir de votre appareil, vous devez le configurer conformément aux paramètres de stratégie.  

Cet article décrit comment l’application Portail d’entreprise Intune pour macOS vous aide à inscrire, à configurer et à tenir à jour votre appareil pour satisfaire aux exigences de votre organisation.

## <a name="what-to-expect-from-the-company-portal-app"></a>À quoi s’attendre avec l’application Portail d’entreprise ?

Pendant l’installation initiale, l’application vous demande de vous authentifier auprès de votre organisation. Ensuite, elle vous indique les paramètres que vous devez régler sur votre appareil. Par exemple, les organisations définissent souvent des critères de longueur de mots de passe auxquels vous devez vous plier.    

Une fois votre appareil inscrit, l’application Portail d’entreprise continue de s’assurer que votre appareil est protégé. Par exemple, si vous installez une application à partir d’une source non fiable, l’application vous alerte et révoque parfois l’accès aux données de l’entreprise. Les stratégies de protection d’application comme celle-ci sont courantes au sein des organisations. Elles vous obligent souvent à désinstaller les applications non approuvées avant de pouvoir récupérer l’accès.

Si après l’inscription, votre organisation impose une nouvelle exigence de sécurité, telle que l’authentification multifacteur, l’application Portail d’entreprise vous avertit. Vous aurez la possibilité d’ajuster vos paramètres afin de pouvoir continuer à travailler sur votre appareil.  

Pour plus d’informations sur l’inscription, consultez [Que se passe-t-il quand j’installe l’application Portail d’entreprise et que j’inscris mon appareil ?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Configurer la gestion de votre appareil  
Utilisez les étapes suivantes pour inscrire des appareils macOS exécutant OS X El Capitan versions 10.11 et ultérieures.   


1. Pour accéder au site web du portail d’entreprise, ouvrez une nouvelle fenêtre dans __Safari__ et accédez à https://portal.manage.microsoft.com.  

2. Connectez-vous au site web du portail d’entreprise avec votre compte professionnel ou scolaire.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. En haut à gauche de la page, cliquez sur **Menu** > **Appareils**.  

4. La page __Appareils__ affiche une liste des appareils gérés ou une bannière, selon que vous gérez déjà ou non un appareil. 
    * Pour ajouter un appareil qui n’est pas listé, sélectionnez la bannière qui indique **Appuyez ici pour nous indiquer l’appareil que vous utilisez ou ajouter un nouvel appareil.**
    * Si vous n’avez aucun appareil, la bannière indique : **vous n’avez aucun appareil géré. Ajoutez celui-ci en appuyant ici.** Cliquez sur la bannière pour ajouter votre appareil.  

     ![Capture d’écran de la page Appareils, avec un carré rouge autour de l’option de bannière pour mettre en surbrillance l’endroit où vous devez cliquer.](./media/CP-enroll-MACOS-1808.png)  
5.  Effectuez l’étape ci-dessous correspondant au message que vous voyez actuellement dans le portail d’entreprise.  
    * Si vous ajoutez un appareil pour la première fois, vous êtes invité à télécharger l’application Portail d’entreprise sur votre appareil. Cliquez sur **Télécharger** pour continuer.  

         ![Capture de l’écran vous invitant à télécharger l’application Portail d’entreprise macOS. L’utilisateur peut cliquer sur le bouton bleu Télécharger dans la partie inférieure gauche de l’invite, ou sur le bouton gris Annuler dans la partie inférieure droite.](./media/CP-enroll-download-macOS-1808.png)  

    * Si vous avez déjà un appareil macOS géré, vous recevrez une invite avec une liste de vos appareils macOS actuellement gérés. Sélectionnez **Mon appareil n’est pas listé ici** > **Télécharger** pour télécharger l’application Portail d’entreprise sur l’appareil que vous ajoutez.  

         ![Capture de l’écran vous invitant à télécharger l’application Portail d’entreprise macOS. L’utilisateur peut sélectionner *Mon appareil n’est pas listé ici* ou un appareil spécifique au milieu de la page. Un bouton bleu Télécharger s’affiche en bas à gauche de l’invite, et un bouton gris Annuler s’affiche en bas à droite.](./media/cp-mac-os-device-isnt-here-1808.png)  

6. Votre appareil vérifie que le fichier d’installation **CompanyPortal.pkg** peut être ouvert sans risque. Une fois terminé, ouvrez le programme d’installation et finissez l’installation.  

7. Quand le programme d’installation a terminé, accédez à **Launchpad** et ouvrez **Portail d’entreprise**.  

8. Votre appareil macOS vous invite à confirmer que vous souhaitez ouvrir l’application Portail d’entreprise. Cliquez sur **Ouvrir**.  

   > [!TIP]
   > Intune doit avoir accès à votre ordinateur pour vérifier que votre appareil est suffisamment sécurisé pour accéder aux ressources de votre organisation. Si votre ordinateur refuse d’ouvrir l’application Portail d’entreprise, [désactivez Gatekeeper](https://support.apple.com/HT202491). Ensuite, ouvrez l’application.

9. Le premier écran qui apparaît dans l’application Portail d’entreprise vous invite à **vous connecter**. Utilisez le même compte professionnel ou scolaire que celui avec lequel vous vous êtes connecté au site web du portail d’entreprise.

10. Le portail d’entreprise vérifie vos informations de compte, puis affiche vos états **Inscription de l’appareil** et **Conformité de l’appareil**. Des triangles jaunes signalent les actions que vous devez effectuer pour sécuriser votre appareil macOS professionnel ou scolaire. Cliquez sur **Commencer** pour démarrer l’inscription. Découvrez [ce que votre organisation peut voir](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) quand vous inscrivez un appareil.

11. Vous pouvez être invité à fournir les informations de connexion de votre ordinateur. L’inscription de votre appareil peut prendre quelques minutes. Pendant ce temps, vous pouvez effectuer d’autres tâches sur votre appareil. Un message s’affiche une fois la configuration de l’application Portail d’entreprise terminée pour vous informer que vous avez fini.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Vous trouverez ses coordonnées sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
