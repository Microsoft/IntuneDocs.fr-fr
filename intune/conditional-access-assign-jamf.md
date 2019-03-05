---
title: Stratégie de conformité d’appareil pour les appareils Jamf | Microsoft Intune
titlesuffix: Microsoft Intune
description: Utilisez des stratégies de conformité Microsoft Intune avec l’accès conditionnel Azure Active Directory pour permettre de sécuriser les appareils gérés par Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5416f90a7acb0f2030481d744e114db6513c5366
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231432"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Appliquer la conformité sur les Mac gérés par Jamf Pro

S'applique à : Intune dans le portail Azure

Vous pouvez utiliser Azure Active Directory et les stratégies d’accès conditionnel de Microsoft Intune. Assurez-vous que vos utilisateurs finaux respectent les exigences de l’organisation. Vous pouvez appliquer ces stratégies à des Mac [gérés par Jamf Pro](conditional-access-integrate-jamf.md). Cela nécessite à la fois un accès aux consoles Intune et Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configuration des stratégies de conformité d’appareils dans Intune

1. Ouvrez Microsoft Azure, puis accédez à **Intune** > **Conformité de l’appareil** > **Stratégies**. Vous pouvez créer des stratégies pour macOS, notamment choisir une série d’actions (par exemple, l’envoi d’avertissements par e-mail) pour les utilisateurs et groupes non conformes.
2. Recherchez les groupes désirés et appliquez-leur les stratégies.

> [!Note]
> Intune exige le chiffrement de disque complet pour être conforme.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Déployer l’application Portail d’entreprise pour macOS dans Jamf Pro

Vous devez déployer l’application Portail d’entreprise pour macOS dans Jamf Pro en tant qu’installation en arrière-plan en appliquant la procédure ci-dessous :

1. Sur un appareil macOS, téléchargez la version actuelle de [l’application Portail d’entreprise pour macOS](https://go.microsoft.com/fwlink/?linkid=862280). Ne l’installez pas ; vous avez besoin d’une copie de l’application à charger vers Jamf Pro.
2. Ouvrez Jamf Pro, puis accédez à **Gestion de l’ordinateur** > **Packages**.
3. Créez un package avec l’application Portail d’entreprise pour macOS, puis cliquez sur **Enregistrer**.
4. Ouvrez **Ordinateurs** > **Stratégies**, puis sélectionnez **Nouveau**.
5. Utilisez la charge utile **Général** pour configurer les paramètres de la stratégie. Ces paramètres doivent être configurés comme suit :
   - Déclencheur : sélectionnez **Inscription terminée** et **Archivage récurrent**.
   - Fréquence d’exécution : sélectionnez **Une fois par ordinateur**.
6. Sélectionnez la charge utile **Packages** et cliquez sur **Configurer**.
7. Cliquez sur **Ajouter** pour sélectionner le package avec l’application Portail d’entreprise.
8. Choisissez l’option **Installer** dans le menu contextuel **Action**.
9. Configurez les paramètres pour le package.
10. Cliquez sur l’onglet **Étendue** pour spécifier les ordinateurs sur lesquels l’application Portail d’entreprise doit être installée. Cliquez sur **Save**. La stratégie sera appliquée aux appareils inclus dans l’étendue la prochaine fois que le déclencheur sélectionné sera exécuté sur l’ordinateur et qu’il répondra aux critères définis dans la charge utile **Général**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Créer une stratégie dans Jamf Pro pour que les utilisateurs inscrivent leurs appareils auprès d’Azure Active Directory

> [!NOTE]
> Vous devez [déployer le portail d’entreprise](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) pour macOS avant de passer aux étapes suivantes.  

Les utilisateurs finaux doivent lancer l’application Portail d’entreprise via le libre-service Jamf pour inscrire l’appareil auprès d’Azure AD en tant qu’appareil géré par Jamf Pro. Cette opération oblige les utilisateurs finaux à agir. Nous vous recommandons de [contacter l’utilisateur final](end-user-educate.md) par e-mail, à l’aide d’une notification Jamf Pro ou au moyen d’une autre méthode de notification pour l’inviter à cliquer sur le bouton dans Jamf Self Service.

> [!WARNING]
> L’application Portail d’entreprise doit être lancée à partir de Jamf Self Service pour procéder à l’inscription de l’appareil. <br><br>Le fait de lancer manuellement l’application Portail d’entreprise (par exemple, à partir du dossier Applications ou Téléchargements) n’inscrit pas l’appareil. Si un utilisateur final lance manuellement le Portail d’entreprise, le message d’avertissement « AccountNotOnboarded » s’affiche.

1. Dans Jamf Pro, accédez à **Ordinateurs** > **Stratégies** et créez une stratégie pour l’inscription d’appareils.
2. Configurez la charge utile **Intégration de Microsoft Intune**, notamment la fréquence de déclenchement et d’exécution.
3. Cliquez sur l’onglet **Étendue** et incluez tous les appareils ciblés dans l’étendue de la stratégie.
4. Cliquez sur l’onglet **Libre-service** pour rendre la stratégie disponible dans le libre-service Jamf. Incluez la stratégie dans la catégorie **Conformité de l'appareil**. Cliquez sur **Save**.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Suppression d’un appareil géré par Jamf dans Intune

Vous pouvez supprimer un appareil géré par Jamf dans la console Intune en sélectionnant **Supprimer** dans l’affichage **Tous les appareils**. Pour supprimer des appareils en bloc, sélectionnez les appareils concernés, puis cliquez sur **Supprimer**.

Vous pouvez obtenir des informations sur la façon de [supprimer un appareil géré par Jamf dans la documentation de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Vous pouvez aussi ouvrir un ticket de support auprès du [Support Jamf](https://www.jamf.com/support/) pour obtenir une aide supplémentaire. 

## <a name="next-steps"></a>Étapes suivantes

- [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Bien démarrer avec l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
