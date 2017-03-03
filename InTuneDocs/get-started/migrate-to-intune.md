---
title: Migrer vers Intune | Microsoft Docs
description: "Vous pouvez procéder comme suit pour migrer vers Intune depuis votre solution de gestion de mobilité d’entreprise."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 43ac18d298901f24c8d6352537b285bf0108f667


---

# <a name="migrate-to-intune"></a>Migrer vers Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Vous pouvez procéder comme suit pour migrer vers Intune depuis votre solution de gestion de mobilité d’entreprise :

![Étapes de migration pour Intune](./media/migrate-intune-steps.png)

## <a name="notify-users"></a>Notification aux utilisateurs

Une fois que vous êtes certain que le déploiement pilote Intune répond à vos besoins, annoncez à vos utilisateurs la future migration de leurs appareils vers Intune. Des e-mails, des instructions et des [affiches](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) peuvent aider à cerner les attentes et fournir des détails d’inscription pour les étapes que l’utilisateur doit suivre pour maintenir une connectivité ininterrompue aux ressources d’entreprise et aux applications. Assurez-vous que votre équipe de support est prête à aider les utilisateurs dans le processus de migration.

## <a name="modify-your-existing-enterprise-mobility-management-solution"></a>Modification de votre solution de gestion de mobilité d’entreprise existante

Selon la manière dont vous souhaitez gérer les stratégies d’accès conditionnel entre votre solution de gestion de mobilité d’entreprise existante et Intune, vous devrez peut-être désactiver vos stratégies d’accès conditionnel existant. Vous désactiverez vos stratégies d’accès conditionnel existantes OU n’inclurez pas les utilisateurs/appareils que vous vous apprêtez à migrer vers Intune dans les stratégies d’accès conditionnel existantes.  N’utilisez pas Intune et votre solution de gestion de mobilité d’entreprise pour appliquer des stratégies d’accès conditionnel aux mêmes utilisateurs/appareils.

## <a name="enable-intune-conditional-access-policy-optional"></a>Activation de stratégies d’accès conditionnel Intune (facultatif)

Si vous avez décidé d’appliquer immédiatement les stratégies d’accès conditionnel sans une période de grâce pour la migration des appareils, activez des stratégies d’accès conditionnel dans Intune au cours de cette étape.  Assurez-vous que cette décision est bien communiquée à vos utilisateurs et à votre équipe de support technique.  Si les appareils ne sont pas inscrits à Intune et ne sont pas conformes aux stratégies Intune, les utilisateurs ne pourront pas accéder aux ressources d’entreprise jusqu’à ce qu’ils s’inscrivent à Intune et que les appareils soient conformes aux stratégies Intune.

## <a name="unenrolling-devices-from-your-existing-enterprise-mobility-management-solution"></a>Désinscription d’appareils de votre solution de gestion mobilité d’entreprise existante

Les appareils doivent être désinscrits de votre solution de gestion de mobilité d’entreprise existante avant leur inscription à Intune. Nous recommandons d’autoriser les utilisateurs d’annuler l’inscription de leurs appareils eux-mêmes pour une expérience utilisateur optimale.  Suivez les conseils de désinscription donnés par le fournisseur de votre solution pour vous assurer que vous supprimez correctement les utilisateurs et les appareils de votre plateforme et garantir une interruption minimale pour vos utilisateurs finaux.

## <a name="enrolling-devices-in-intune"></a>Inscription des appareils à Intune

Les utilisateurs planifiés pour la migration doivent immédiatement s’inscrire à Intune pour éviter la perte de l’accès aux ressources d’entreprise, aux e-mails et aux applications ou rétablir cet accès. Si vous avez configuré l’accès conditionnel et que les utilisateurs essaient de se connecter à la messagerie électronique avant de s’inscrire auprès d’Intune, leur accès est refusé et un e-mail d’inscription leur est envoyé. Cet e-mail les guide lors du processus d’inscription de leur appareil auprès d’Intune.  Les utilisateurs peuvent également s’inscrire à Intune par le biais de l’application Portail d’entreprise Intune ou en mode natif par le biais des systèmes d’exploitation Windows 8.1 et Windows 10 Mobile. Reportez-vous à [Ce qu’il faut dire à vos utilisateurs finaux concernant l’utilisation de Microsoft Intune](/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) pour obtenir des conseils supplémentaires sur les étapes d’inscription par plateforme.

## <a name="configure-intune-conditional-access-optional"></a>Configuration d’un accès conditionnel Intune (facultatif)

Si vous avez autorisé une période de grâce pour l’application de l’accès conditionnel, activez des stratégies d’accès conditionnel dans Intune pour démarrer la mise en œuvre lorsque la période de grâce que vous avez communiquée à vos utilisateurs finaux est terminée. Tous les appareils devront répondre immédiatement aux exigences de la stratégie d’accès conditionnel Intune.

## <a name="enroll-remaining-devices-and-users"></a>Inscription des appareils et des utilisateurs restants

Maintenant que vous avez activé l’accès conditionnel, tous les utilisateurs doivent s’inscrire à Intune et répondre aux stratégies de conformité de votre organisation pour accéder aux ressources d’entreprise. Si vous avez migré vos utilisateurs dans une inscription en plusieurs phases (pas simultanément), répétez les étapes ci-dessus jusqu’à ce que tous les appareils et tous les utilisateurs soient inscrits et gérés par Intune.

## <a name="retire-the-previous-enterprise-mobility-management-solution"></a>Mise hors service de la précédente solution de gestion de mobilité d’entreprise

Une fois que vous avez migré tous vos utilisateurs et tous les appareils dans Intune et que vous avez validé la réussite des migrations vers Intune, vous pouvez mettre hors service la solution de gestion mobilité précédente et/ou annuler l’abonnement au service. Suivez les instructions du fournisseur de solutions pour vous assurer que vous avez supprimé correctement les exigences d’infrastructure inutiles et annulé toutes les licences/tous les abonnements.

## <a name="additional-migration-resources"></a>Ressources supplémentaires sur la migration

Avez-vous besoin d’une aide supplémentaire pour la migration vers Intune ? Nous fournissons des options d’assistance par des experts pour garantir une migration sans problème :

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft Consulting Services](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Support technique et non-technique Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Forum TechNet Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## <a name="get-a-downloadable-copy-of-this-guide"></a>Obtenir une copie téléchargeable de ce guide

Pour obtenir une copie téléchargeable de ce guide dans son intégralité, accédez à la [Galerie TechNet](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).



<!--HONumber=Feb17_HO3-->


