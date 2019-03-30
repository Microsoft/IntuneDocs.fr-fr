---
title: Inscrire un appareil Windows 10 dans le portail d’entreprise Intune | Microsoft Docs
description: Pour inscrire les appareils Windows 10 dans le portail d’entreprise Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4eb5dbb150559de7ad30a598fb78a4fa78033c42
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58068984"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Inscrire des appareils Windows 10 avec le portail d’entreprise Intune

Utilisez le portail d’entreprise Intune pour inscrire votre appareil Windows 10 sous gestion de votre organisation. Cet article explique comment inscrire des appareils avec Windows 10 versions 1607 et ultérieures et Windows 10 version 1511 et antérieure. Avant de commencer, assurez-vous que vous [vérifier la version sur votre appareil](windows-enrollment-company-portal.md#find-windows-10-version-number) afin que vous pouvez suivre les mesures appropriées.  

Windows 10 est pris en charge entre les différents types d’appareils, y compris le bureau, téléphone et tablette. Les étapes d’inscription sont les mêmes sur l’appareil que vous utilisez. Toutefois, votre écran peut différer légèrement parmi les images présentées dans cet article.  

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]  

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Inscrire Windows 10 version 1607 et ultérieur appareil 
Ces étapes décrivent comment inscrire un appareil qui s’exécute sur Windows 10, version 1607 et ultérieure.  

1. Accédez à **Démarrer**. Si vous êtes sur un appareil Windows 10 Mobile, passez à la **toutes les applications** liste.

2. Ouvrez l’application **Paramètres**. Si l’application n’est pas immédiatement disponible dans votre liste d’applications, accédez à la barre de recherche et le type « paramètres ».

3. Sélectionnez **Comptes** > **Accès Professionnel ou Scolaire** > **Se connecter**.  


    ![Sélectionner le compte Accès Professionnel ou Scolaire](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Entrez votre e-mail professionnel ou scolaire, puis sélectionnez **Suivant**.  


   ![Entrer votre compte professionnel ou scolaire](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Connectez-vous à Intune avec votre compte professionnel ou scolaire.  


    ![Ajouter un compte professionnel ou scolaire](./media/w10-enroll-rs1-enter-your-credentials.png)  

    Vous verrez finalement un message indiquant que votre société ou votre école procède à l’inscription de votre appareil.

6. Si votre organisation vous oblige à configurer un code confidentiel pour Windows Hello, vous allez être invité à entrer un code de vérification. Entrez le code et suivez les instructions les étapes à l’écran pour créer un code confidentiel.  

7. À l’écran **Vous voilà prêt !** s’affiche, sélectionnez **Terminé**. Votre appareil est maintenant inscrit.  

8. Pour vérifier votre connexion, revenez en arrière pour **paramètres** > **comptes** > **accès scolaire ou Professionnel**.  Votre compte doit maintenant être répertorié.  


    ![Valider que la connexion a été correctement configurée](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

Vous ne parvenez toujours pas à accéder à votre messagerie professionnelle ou scolaire, à vos fichiers ou à d’autres données ? Découvrez comment [résoudre les problèmes de compte](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Inscrire Windows 10 version 1511 et antérieures appareil  
Ces étapes décrivent comment inscrire un appareil qui s’exécute sur Windows 10, version 1511 et antérieure.  

1. Accédez à **Démarrer**. Si vous êtes sur un appareil Windows 10 Mobile, passez à la **toutes les applications** liste.

2. Ouvrez l’application **Paramètres**. Si l’application n’est pas immédiatement disponible dans votre liste d’applications, accédez à la barre de recherche et le type « paramètres ».

3. Sélectionnez **comptes** > **votre compte**.  


    ![Sélectionner Votre compte](./media/W10-enroll-2-accounts-your-account.png)  

5. Sélectionnez **Ajouter un compte professionnel ou scolaire**.  


    ![Sélectionner Ajouter un compte professionnel ou scolaire](./media/w10-enroll-3-add-work-school-acct.png)  

6. Connectez-vous avec vos informations d'identification professionnelles ou scolaires.  


    ![Se connecter](./media/W10-enroll-4-sign-in.png)  

Vous ne parvenez toujours pas à accéder à votre messagerie professionnelle ou scolaire, à vos fichiers ou à d’autres données ? Découvrez comment [résoudre les problèmes de compte](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).   

## <a name="next-steps"></a>Étapes suivantes  

Pour obtenir de l’aide, contactez le support technique de votre entreprise. Vous pouvez trouver votre organisation plus d’informations sur la [site Web portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980). Connectez-vous au site web avec votre compte professionnel ou scolaire.  

 

