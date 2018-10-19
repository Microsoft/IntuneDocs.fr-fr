---
title: Configurer l’accès d’un appareil iOS aux ressources de l’entreprise | Microsoft Docs
description: Explique comment passer un appareil iOS en mode géré par Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 85d0df026e49b36e148620ce2d06b4afaaf98ace
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827885"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurer l’accès d’un appareil iOS aux ressources de l’entreprise

Inscrivez votre appareil iOS avec l’application Portail d’entreprise Intune pour obtenir un accès sécurisé aux e-mails, aux fichiers et aux applications de votre organisation.

Pour être autorisé à accéder aux données propriétaires à partir d’un appareil d’entreprise ou personnel, vous devez au préalable passer l’appareil en mode géré. Une fois que votre appareil est en mode géré, votre organisation lui assigne des stratégies et des applications par le biais du fournisseur MDM. 

Pour conserver l’accès aux informations professionnelles ou scolaires à partir de votre appareil, vous devez configurer l’appareil avec les paramètres par défaut de votre organisation. Cet article décrit comment l’application Portail d’entreprise vous aide à inscrire, à configurer et à tenir à jour votre appareil pour satisfaire à ces exigences.

> [!NOTE]
> Si vous avez essayé d’accéder à vos e-mails professionnels dans la messagerie d’entreprise et avez reçu un message vous invitant à passer votre appareil en mode géré, vous êtes au bon endroit. Suivez les instructions ci-dessous pour accéder à vos e-mails et à d’autres ressources de l’entreprise sur votre appareil iOS.

## <a name="what-to-expect-from-the-company-portal-app"></a>À quoi s’attendre avec l’application Portail d’entreprise ?

### <a name="security"></a>Sécurité
Pendant l’installation initiale, l’application vous demande de vous authentifier auprès de votre organisation. Ensuite, elle vous indique les paramètres que vous devez mettre à jour sur votre appareil. Par exemple, les organisations définissent souvent des critères de longueur de mots de passe auxquels vous devez vous plier.    

### <a name="protection"></a>Protection
Une fois votre appareil inscrit, l’application Portail d’entreprise continue de s’assurer que votre appareil est protégé. Par exemple, si vous installez une application à partir d’une source non fiable, l’application vous alerte et révoque parfois l’accès aux données de l’entreprise. Les stratégies de protection d’applications comme celles-ci sont courantes dans les organisations. Elles vous obligent souvent à désinstaller l’application non approuvée avant de vous redonner l’accès.

### <a name="setting-notifications"></a>Définition des notifications
Si après l’inscription votre organisation impose une nouvelle exigence de sécurité, telle que l’authentification multifacteur, l’application Portail d’entreprise vous avertit. Vous aurez la possibilité d’ajuster vos paramètres afin de pouvoir continuer à travailler sur votre appareil.  

Pour plus d’informations sur l’inscription, consultez [Que se passe-t-il quand j’installe l’application Portail d’entreprise et que j’inscris mon appareil ?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios). 

## <a name="before-you-start"></a>Avant de commencer

- Une fois que vous avez commencé l’inscription, vous devez impérativement terminer l’ensemble du processus. Si vous faites une pause pendant plus de quelques minutes, le programme d’installation risque de se terminer et vous obliger à recommencer à zéro.  
- En cas d’échec, revenez à l’application Portail d’entreprise et réessayez.  
- Vérifiez que votre réseau Wi-Fi fonctionne et que Safari est opérationnel sur votre appareil.
- Téléchargez et installez [l’application Portail d’entreprise Intune](install-and-sign-in-to-the-intune-company-portal-app-ios.md).  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>Utiliser l’application Portail d’entreprise pour configurer l’accès aux ressources de l’entreprise

|Ce que vous voyez|Explication|
|---|---|
|![Écran de connexion du Portail d’entreprise, avec un bouton « Se connecter » en bas.](./media/ios-01-cp-enroll-1802.png)|Ouvrez l’application Portail d’entreprise et appuyez sur **Se connecter**.|
|![Invitation à se connecter à Azure AD.](./media/ios-02-cp-enroll-1802.png)|Entrez l’adresse électronique de votre entreprise, puis appuyez sur **Suivant**.|
|![Invitation à saisir le mot de passe Azure AD.](./media/ios-03-cp-enroll-1802.png)|Entrez votre mot de passe, puis appuyez sur **Connexion**.|
|![Écran de démarrage du chargement des ressources de l’entreprise.](./media/ios-04-cp-enroll-1802.png)|Attendez que cet écran soit chargé.|
|![Page des conditions générales.](./media/ios-05-cp-enroll-1802.png)|Lisez et acceptez toutes les conditions générales (**Tout accepter**).|
|![Écran de configuration de l’accès à l’entreprise. La gestion et les paramètres ont actuellement besoin d’une résolution.](./media/ios-06-cp-enroll-1802.png)|Appuyez sur **Commencer** pour démarrer le processus à l’issue duquel votre appareil pourra accéder aux ressources de l’entreprise. Si vous ne pouvez pas le faire pour le moment, vous avez la possibilité de **Différer** le processus, mais cela signifie que vous ne pourrez pas accéder à la messagerie, aux documents, etc.|
|![Écran Ce que peut mon entreprise peut voir.](./media/ios-07-cp-enroll-1802.png)|En appuyant sur le lien **En savoir plus** en bas, vous aurez accès à ce que votre entreprise peut voir. Sinon, appuyez sur **Continuer**.|
|![Écran Et ensuite ?.](./media/ios-08-cp-enroll-1802.png)|Cet écran vous explique tout ce qui se passe au cours de la configuration. Vous allez passer du temps dans Safari, dans l’application Paramètres et dans l’application Portail d’entreprise. Appuyez sur **Continuer**.|
|![Écran de chargement après avoir appuyé sur Suivant dans Et ensuite ?.](./media/ios-09-cp-enroll-1802.png)|Attendez que cet écran soit chargé.|
|![Basculement vers Safari pour l’inscription.](./media/ios-cp-sent-to-safari-1808.png)|Vous accédez automatiquement à Safari pour récupérer des informations de gestion sur votre appareil.|
|![Invite du système qui demande l’ouverture de l’application Paramètres.](./media/ios-8-cp-enroll-1711.png)|Appuyez sur **Autoriser** pour ouvrir l’application Paramètres afin de télécharger le profil de configuration. Cette installation permettra à votre entreprise de gérer ses informations sur votre appareil.|
|![Capture de l’écran Installer un profil dans les paramètres de l’appareil.](./media/ios-9-cp-enroll-1711.png)|Appuyez sur **Installer**.|
|![Installation de la boîte de dialogue modale du profil en bas de l’écran.](./media/ios-10-cp-enroll-1711.png)|Appuyez sur **Installer**.|
|![Écran de chargement de l’installation du profil.](./media/ios-11-cp-enroll-1711.png)|Attendez que cet écran soit chargé.|
|![Écran d’avertissement de gestion de profil.](./media/ios-12-cp-enroll-1711.png)|Cet avertissement, écrit par Apple, vous informe sur les types d’actions réalisables sur un appareil géré. Cliquez [ici](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) pour en savoir plus sur les informations auxquelles votre entreprise a accès.|
|![Invite du système qui demande s’il faut faire confiance à la gestion à distance.](./media/ios-13-cp-enroll-1711.png)|Appuyez sur **Faire confiance** pour permettre à votre société de gérer ses informations et paramètres sur votre appareil.|
|![Écran de chargement de la fin de l’installation du profil.](./media/ios-14-cp-enroll-1711.png)|Attendez que cet écran soit chargé.|
|![Écran Profil installé.](./media/ios-15-cp-enroll-1711.png)|Votre profil est installé, et les paramètres et informations de l’entreprise présents sur votre appareil sont maintenant tout près d’être gérés.|
|![Basculement vers Safari pour l’inscription.](./media/ios-16-cp-enroll-1711.png)|Vous accédez automatiquement à Safari pour finir de récupérer des informations de gestion sur votre appareil. |
|![Invite du système qui demande l’ouverture du Portail d’entreprise.](./media/ios-17-cp-enroll-1711.png)|Appuyez sur **Ouvrir**.|
|![Écran de chargement des ressources de l’entreprise.](./media/ios-21-cp-enroll-1802.png)|Attendez que cet écran soit chargé.|
|![Sélectionnez la catégorie d’appareils sur l’application Portail d’entreprise.](./media/ios-22-cp-enroll-1802.png)|Sélectionnez la meilleure catégorie pour votre appareil. Elle est généralement en rapport avec le propriétaire de l’appareil ou son emplacement habituel.|
|![Catégorie sélectionnée.](./media/ios-23-cp-enroll-1802.png)||
|![Gestion de l’appareil réussie ; vous devez maintenant mettre à jour les paramètres.](./media/ios-24-cp-enroll-1802.png)|Vous avez réussi à passer votre appareil en mode géré. Il reste probablement des paramètres, comme la longueur de votre mot de passe, que votre entreprise vous demandera éventuellement de mettre à jour. Appuyez sur **Continuer** pour continuer.|
|![Confirmation des paramètres de l’appareil.](./media/ios-25-cp-enroll-1802.png)|Le Portail d’entreprise regardera si certains de vos paramètres doivent être mis à jour.|
|![Fin de la vérification des paramètres, avec une version du système d’exploitation incorrecte.](./media/ios-26-cp-enroll-1802.png)|Le Portail d’entreprise donne des instructions pour résoudre les problèmes relatifs aux paramètres. Dès que c’est fait, appuyez sur **Vérifier les paramètres**.|
|![Écran de chargement de la confirmation des paramètres de l’appareil.](./media/ios-27-cp-enroll-1802.png)|Votre appareil vérifie si les paramètres sont suffisamment sécurisés pour lui permettre d’accéder aux ressources de l’entreprise.|
|![Inscription et mise à jour des paramètres réussies.](./media/ios-28-cp-enroll-1802.png)|Félicitations ! Votre appareil est maintenant inscrit dans Intune.|

> [!Note]
> Il peut rester quelques étapes à suivre pour que l’appareil soit totalement géré. Obtenez des informations supplémentaires sur l’[inscription de votre appareil en utilisant la gestion des dépenses de télécommunications](enroll-your-device-with-telecom-expense-management-ios.md). Si votre organisation utilise le Programme d’inscription des appareils (DEP) d’Apple, vous trouverez un complément d’informations [ici](enroll-your-device-dep-ios.md).

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Vous trouverez ses coordonnées sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  
