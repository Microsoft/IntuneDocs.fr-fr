---
title: Stratégie de conformité d’appareil pour les appareils Jamf
titleSuffix: Microsoft Intune
description: Utilisez des stratégies de conformité Microsoft Intune avec l’accès conditionnel Azure Active Directory pour permettre de sécuriser les appareils gérés par Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3552eca925865eb3278b50490a6b70ee5807e2b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502455"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Appliquer la conformité sur les Mac gérés par Jamf Pro

Lorsque vous [intégrez Jamf Pro à Intune](conditional-access-integrate-jamf.md), vous pouvez utiliser des stratégies d'accès conditionnel pour garantir la conformité de vos appareils Mac aux exigences de votre organisation.  Cet article vous aidera dans les tâches suivantes :  

- Créer des stratégies d’accès conditionnel.
- Configurer Jamf Pro pour déployer l'application Portail d'entreprise Intune sur les appareils que vous gérez avec Jamf.
- Configurer les appareils pour qu'ils s'inscrivent auprès d’Azure AD lorsque l'utilisateur de l'appareil se connecte à l'application Portail d'entreprise depuis l'application Jamf Self Service. L'inscription d'un appareil crée une identité dans Azure AD permettant d'évaluer l’appareil à l’aide de stratégies d'accès conditionnel pour l'accès aux ressources de l'entreprise.  
 
Les procédures décrites dans cet article nécessitent l'accès aux consoles Intune et Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configuration des stratégies de conformité d’appareils dans Intune

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), puis sélectionnez **Conformité de l’appareil** > **Stratégies**. 
2. Si vous utilisez une stratégie précédemment créée, sélectionnez cette stratégie dans la console, puis passez à l'étape suivante de cette procédure.  
   
   Sélectionnez **Créer une stratégie**, puis spécifiez les détails d'une stratégie avec une *plate-forme* **macOS**. Configurez les options *Paramètres*et *Actions en cas de non-conformité* pour répondre aux exigences de votre organisation, puis sélectionnez **Créer** pour enregistrer la stratégie.

3. Dans le volet de *présentation* des stratégies, sélectionnez **Affectations**. Utilisez les options disponibles pour choisir les utilisateurs et groupes de sécurité Azure Active Directory (Azure AD) qui recevront cette stratégie. L'intégration de Jamf à Intune ne prend pas en charge une stratégie de conformité qui cible des groupes d’appareils. 

4. Lorsque vous sélectionnez **Enregistrer**, la stratégie est appliquée aux utilisateurs.  

Les stratégies que vous déployez ciblent les appareils utilisés par les utilisateurs affectés. La conformité de ces appareils est évaluée. Les appareils conformes sont marqués comme conformes pour le paramètre « *Exiger que l'appareil soit marqué comme conforme* » dans Azure AD.  

> [!NOTE]
> Intune exige le chiffrement de disque complet pour être conforme.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Déployer l’application Portail d’entreprise pour macOS dans Jamf Pro

Créez une stratégie dans Jamf Pro pour déployer le Portail d'entreprise Intune. Cette stratégie déploie l'application du portail d'entreprise afin qu'elle soit disponible dans Jamf Self Service. Créez cette stratégie avant de créer une stratégie dans Jamf Pro pour que les utilisateurs puissent enregistrer des appareils avec Azure AD.  

Pour effectuer la procédure suivante, vous devez avoir accès à un appareil macOS et au portail Jamf Pro. 

### <a name="to-deploy-the-company-portal-app"></a>Pour déployer l’app Portail d'entreprise  

1. Sur un appareil macOS, téléchargez la version actuelle de [l’application Portail d’entreprise pour macOS](https://go.microsoft.com/fwlink/?linkid=862280), mais ne l’installez pas. Vous n'avez besoin que d'une copie de l'application pour pouvoir l’uploader sur Jamf Pro.  

2. Ouvrez Jamf Pro, puis sélectionnez **Gestion des ordinateurs** > **Packages**.

3. Créez un package avec l’application Portail d’entreprise pour macOS, puis sélectionnez **Enregistrer**.

4. Ouvrez **Ordinateurs** > **Stratégies**, puis sélectionnez **Nouveau**.

5. Utilisez la charge utile **Général** pour configurer les paramètres de la stratégie. Ces paramètres doivent être configurés comme suit :
   - Déclencheur : sélectionnez **Inscription terminée** et **Archivage récurrent**.
   - Fréquence d’exécution : sélectionnez **Une fois par ordinateur**.

6. Sélectionnez la charge utile **Packages** et cliquez sur **Configurer**.

7. Cliquez sur **Ajouter** pour sélectionner le package avec l’application Portail d’entreprise.

8. Sélectionnez l’option **Installer** dans le menu contextuel **Action**.
9. Configurez les paramètres pour le package.

10. Sélectionnez l’onglet **Étendue** pour spécifier les ordinateurs sur lesquels l’application Portail d’entreprise doit être installée. Sélectionnez **Enregistrer**. La stratégie sera appliquée aux appareils inclus dans l’étendue la prochaine fois que le déclencheur sélectionné sera exécuté sur l’ordinateur et qu’il répondra aux critères définis dans la charge utile **Général**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Créer une stratégie dans Jamf Pro pour que les utilisateurs inscrivent leurs appareils auprès d’Azure Active Directory  

Après avoir [déployé le portail d'entreprise](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) pour macOS via Jamf Pro Self Service, vous pouvez créer la stratégie Jamf Pro qui inscrit l’appareil d'un utilisateur auprès d’Azure AD. 

L'inscription d'un appareil nécessite que l'utilisateur de l’appareil sélectionne manuellement l'application Portail d'entreprise Intune dans Jamf Self Service. Nous vous recommandons de [contacter vos utilisateurs finaux](../fundamentals/end-user-educate.md) par e-mail, via des notifications Jamf Pro, ou toute autre méthode utilisée par votre organisation pour les inviter à effectuer cette action afin d’inscrire leurs appareils. 

> [!WARNING]
> Le fait de lancer manuellement l’application Portail d’entreprise (par exemple, à partir du dossier Applications ou Téléchargements) n’inscrit pas l’appareil. Si un utilisateur d’appareil lance manuellement le Portail d’entreprise, le message d’avertissement **'AccountNotOnboarded'** s’affiche.

### <a name="to-create-the-registration-policy"></a>Pour créer la stratégie d’inscription  

1. Dans Jamf Pro, sélectionnez **Ordinateurs** > **Stratégies**, puis créez une stratégie pour l’inscription d’appareils.

2. Configurez la charge utile **Intégration de Microsoft Intune**, notamment la fréquence de déclenchement et d’exécution.

3. Sélectionnez l’onglet **Étendue** et incluez tous les appareils ciblés dans l’étendue de la stratégie.

4. Sélectionnez l’onglet **Self Service** pour rendre la stratégie disponible dans Jamf Self Service. Incluez la stratégie dans la catégorie **Conformité de l'appareil**. Cliquez sur **Save**.

## <a name="validate-intune-and-jamf-integration"></a>Valider l’intégration Intune et Jamf  

Utilisez la console Jamf Pro pour confirmer que la communication entre Jamf Pro et Microsoft Intune est correctement établie. 

- Dans Jamf Pro, accédez à **Paramètres** > **Gestion globale** > **Intégration Microsoft Intune**, puis sélectionnez **Test**. 

    La console affiche un message indiquant la réussite ou l'échec de la connexion.  

Si le test de connexion de la console Jamf Pro échoue, vérifiez la configuration de Jamf. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Suppression d’un appareil géré par Jamf dans Intune

Vous pouvez supprimer un appareil géré par Jamf dans la console Intune en sélectionnant **Supprimer** dans l’affichage **Tous les appareils**. Pour supprimer des appareils en bloc, sélectionnez les appareils concernés, puis cliquez sur **Supprimer**.

Vous pouvez obtenir des informations sur la façon de [supprimer un appareil géré par Jamf dans la documentation de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Vous pouvez aussi ouvrir un ticket de support auprès du [Support Jamf](https://www.jamf.com/support/) pour obtenir une aide supplémentaire. 

## <a name="next-steps"></a>Étapes suivantes

- [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Bien démarrer avec l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
