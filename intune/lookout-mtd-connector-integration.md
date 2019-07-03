---
title: Configurer l’intégration de Lookout à Microsoft Intune
titleSuffix: Microsoft Intune
description: Découvrez-en plus sur l’intégration d’Intune à Lookout Mobile Endpoint Security, une solution de protection contre les menaces mobiles, pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529874"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Configurez l’intégration de Lookout Mobile Endpoint Security à Intune
Un environnement qui remplit les [conditions préalables](lookout-mobile-threat-defense-connector.md#prerequisites) permet d’intégrer Lookout Mobile Endpoint Security avec Intune. Les informations contenues dans cet article vous guideront lors de la configuration de l’intégration et des paramètres importants dans Lookout pour une utilisation avec Intune.  

> [!IMPORTANT]
> Un locataire Lookout Mobile Endpoint Security existant qui n’est pas déjà associé à votre locataire Azure AD ne peut pas être utilisé pour l’intégration à Azure AD et Intune. Contactez le support de Lookout pour créer un locataire Lookout Mobile Endpoint Security. Utilisez le nouveau locataire pour intégrer vos utilisateurs Azure AD.

## <a name="collect-azure-ad-information"></a>Obtenir vos informations Azure AD  
Pour intégrer Lookout à Intune, vous associez votre locataire Lookout Mobility Endpoint Security à votre abonnement Azure Active Directory (AD).

Pour activer l’intégration de votre abonnement Lookout Mobile Endpoint Security à Intune, vous fournissez les informations suivantes pour le support technique Lookout (enterprisesupport@lookout.com) :  

- **ID de répertoire de locataire Azure AD**  

- **ID d’objet de groupe Azure AD** pour le groupe avec accès **total** à la console de Lookout Mobile Endpoint Security (MES).  
  Vous créez ce groupe d’utilisateurs dans Azure AD pour contenir les utilisateurs ayant un *accès total* pour se connecter à la **console Lookout**. Les utilisateurs doivent être membres de ce groupe ou du groupe facultatif à *accès restreint* pour se connecter à la console Lookout. 

- **ID d’objet de groupe Azure AD** pour le groupe à accès **restreint** à la console Lookout MES *(groupe facultatif)* . 
  Vous créez ce groupe d’utilisateurs facultatif dans Azure AD pour contenir des utilisateurs qui ne devraient pas avoir accès à plusieurs modules de configuration et d’inscription de la console Lookout. Au lieu de cela, ces utilisateurs ont accès en lecture seule au module **Stratégie de sécurité** de la console Lookout. Les utilisateurs doivent être membres de ce groupe facultatif ou du groupe à *accès total* pour se connecter à la console Lookout.

 > [!TIP] 
 > Pour plus d’informations sur les autorisations, consultez [cet article](https://personal.support.lookout.com/hc/articles/114094105653) sur le site web de Lookout.

### <a name="collect-information-from-azure-ad"></a>Collecter des informations à partir d’Azure AD 

1. Connectez-vous au [portail Azure](https://portal.azure.com) avec un compte administrateur général.

2. Accédez à **Azure Active Directory** > **Propriétés** et recherchez votre **ID de répertoire**. Utilisez le bouton *Copie* pour copier l’ID de répertoire, puis enregistrez-le dans un fichier texte.

   ![Propriétés d’Azure AD](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. Ensuite, recherchez l’ID de groupe Azure AD pour les comptes que vous utilisez pour accorder aux utilisateurs Azure AD l’accès à la Console Lookout. Un groupe bénéficie d’un *accès total* et le second groupe, qui bénéficie d’un *accès restreint*, est facultatif. Pour obtenir l’*ID d’objet*, pour chaque compte :  
   1. Accédez à **Azure Active Directory** > **Groupes** pour ouvrir le volet *Groupes - Tous les groupes*.  

   2. Sélectionnez le groupe que vous avez créé pour l’*accès total* pour ouvrir son volet *Vue d’ensemble*.  

   3. Utilisez le bouton *Copie* pour copier l’ID d’objet, puis enregistrez-le dans un fichier texte.  

   4. Répétez le processus pour le groupe à *accès restreint* si vous utilisez ce groupe.  

      ![ID d’objet de groupe Azure AD](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   Après avoir collecté ces informations, contactez le support technique Lookout (adresse e-mail : enterprisesupport@lookout.com). Le support technique Lookout travaillera avec votre contact principal pour intégrer votre abonnement et créer votre compte d’entreprise Lookout sur la base des informations que vous avez fournies.  

## <a name="configure-your-lookout-subscription"></a>Configurer votre abonnement Lookout  
Une fois que le support de Lookout a créé votre compte d'entreprise Lookout, il envoie au contact principal de votre entreprise un e-mail contenant un lien vers l’URL de connexion : https://aad.lookout.com/les?action=consent. 

### <a name="initial-sign-in"></a>Connexion initiale  
Lors de la première connexion à la console Lookout MES, une page de consentement s’affiche (https://aad.lookout.com/les?action=consent). Un administrateur général Azure AD n’a qu’à se connecter et à **Accepter**. Lors des connexions suivantes, il n’est pas nécessaire d’avoir ce niveau de privilège Azure AD. 

 La page de consentement s’affiche. Choisissez **Accepter** pour terminer l’inscription. 
   ![capture d’écran de la page de première connexion de la console Lookout](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

Lorsque vous avez donné votre consentement, vous êtes redirigé vers la console Lookout.

Après la connexion initiale et une fois le consentement donné, les utilisateurs qui se connectent à partir de https://aad.lookout.com sont redirigés vers la Console MES. Si l’autorisation n’a pas encore été accordée, toutes les tentatives de connexion provoquent une erreur de connexion incorrecte.

### <a name="configure-the-intune-connector"></a>Configurer le connecteur Intune  
La procédure suivante suppose que vous avez déjà créé un groupe d’utilisateurs dans Azure AD pour tester votre déploiement de Lookout. La meilleure pratique consiste à démarrer avec un petit groupe d’utilisateurs pour permettre à vos administrateurs Lookout et Intune de se familiariser avec les intégrations de produits. Ensuite, vous pouvez étendre l’inscription à d’autres groupes d’utilisateurs.

1. Connectez-vous à la [console Lookout MES](https://aad.lookout.com) et accédez à **Système** > **Connecteurs**, puis sélectionnez **Ajouter un connecteur**.  Sélectionnez **Intune**.

   ![Image de la console Lookout avec l’option Intune sous l’onglet Connecteurs](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. Sur le volet *Microsoft Intune*, sélectionnez **Paramètres de connexion** et spécifiez la **Fréquence des pulsations** en minutes. 

   ![Image de l’onglet Paramètres de connexion avec la fréquence de pulsations définie](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. Sélectionnez **Gestion des inscriptions** et, pour **Utiliser les groupes de sécurité Azure AD suivants pour identifier les appareils à inscrire dans Lookout for Work**, spécifiez le *nom du groupe* d’un groupe Azure AD à utiliser avec Lookout, puis sélectionnez **Enregistrer les modifications**.

    ![capture d’écran de la page d’inscription dans le connecteur Intune](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **À propos des groupes que vous utilisez** :
   - Une bonne pratique consiste à commencer par un groupe de sécurité Azure AD contenant un petit nombre d’utilisateurs afin de tester l’intégration de Lookout.
   - Le **Nom du groupe** respecte la casse comme indiqué dans les **Propriétés** du groupe de sécurité sur le portail Azure.  
   - Les groupes que vous spécifiez pour la **gestion des inscriptions** définissent l’ensemble des utilisateurs dont les appareils seront inscrits avec Lookout. Quand un utilisateur est membre d’un groupe d’inscription, ses appareils dans Azure AD sont inscrits et éligibles à l’activation dans Lookout MES. La première fois qu’un utilisateur ouvre l’application *Lookout for Work* sur un appareil pris en charge, il est invité à l’activer.

4. Sélectionnez **Synchronisation des états** et vérifiez que l’*état de l’appareil* et l’*état des menaces* sont définis sur **Activé**.  Les deux sont requis pour que l’intégration Lookout Intune fonctionne correctement.  

5. Sélectionnez **Gestion des erreurs**, spécifiez l’adresse e-mail qui doit recevoir les rapports d’erreurs, puis sélectionnez **Enregistrer les modifications**.
 
   ![capture d’écran de la page Gestion des erreurs dans le connecteur Intune](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. Sélectionnez **Créer un connecteur** pour terminer la configuration du connecteur. Plus tard, lorsque vous êtes satisfait de vos résultats, vous pouvez étendre l’inscription à d'autres groupes d’utilisateurs.

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Configurer Intune pour utiliser Lookout comme fournisseur de protection contre les menaces mobiles
Après avoir configuré Lookout MES, vous devez configurer une connexion à Lookout dans Intune.  

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Accédez à **Conformité des appareils** > **Protection contre les menaces mobiles** et sélectionnez **Ajouter**.

3. Sur le volet *Ajouter le connecteur*, utilisez la liste déroulante et sélectionnez **Lookout for Work**.  

4. Sélectionnez **Créer**. Une fois que le connecteur établit un contact avec Lookout MES, les *Paramètres du connecteur* deviennent disponibles.

5. Définir **Activer la synchronisation des applications pour les appareils iOS** sur **Activé**. 

6. Sélectionnez **Enregistrer** pour terminer la configuration.  Intune et Lookout MES sont désormais intégrés et prêts à être utilisés.


## <a name="additional-settings-in-the-lookout-mes-console"></a>Paramètres supplémentaires dans la console Lookout MES
Voici les paramètres supplémentaires que vous pouvez configurer dans la console Lookout MES.  

### <a name="configure-enrollment-settings"></a>Configurer les paramètres d’inscription
Dans la console Lookout MES, sélectionnez **Système** > **Gérer l’inscription** > **Paramètres d’inscription**.  

- Pour l’**état déconnecté**, spécifiez le nombre de jours avant qu’un appareil non connecté soit marqué comme étant déconnecté.  

  Les appareils déconnectés sont considérés comme non conformes et ne peuvent pas accéder à vos applications d’entreprise en fonction des stratégies d’accès conditionnel Intune. Vous pouvez spécifier des valeurs comprises entre 1 et 90 jours.

  ![Paramètres d’inscription Lookout dans le module Système](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>Configurer les notifications par e-mail
Pour recevoir des alertes sur les menaces par e-mail, connectez-vous à la [console Lookout MES](https://aad.lookout.com) avec le compte d’utilisateur qui doit recevoir les notifications.  

- Accédez à **Préférences** , puis définissez les notifications que vous souhaitez recevoir pour **ACTIVÉ**, puis **enregistrez** les modifications.  

- Si vous ne souhaitez plus recevoir de notifications par e-mail, définissez les notifications sur **DÉSACTIVÉ** et enregistrez vos modifications.

  ![capture d’écran de la page Préférences avec compte d’utilisateur affiché](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>Configurer les classifications des menaces  
Lookout Mobile Endpoint Security classifie des menaces mobiles de différents types. Les classifications des menaces dans Lookout ont des niveaux de risque par défaut qui leur sont associés. Ces niveaux de risque peuvent être modifiés à tout moment en fonction des besoins de votre entreprise.

Pour plus d’informations sur les classifications des niveaux de menace et la façon de gérer les niveaux de risque associés, consultez la [référence de menaces Lookout](https://enterprise.support.lookout.com/hc/articles/360011812974).

>[!IMPORTANT]
> Les niveaux de risque sont un aspect important de la solution Mobile Endpoint Security car l’intégration d’Intune calcule la conformité de l’appareil en fonction de ces niveaux de risque lors de l’exécution.  
> 
> L’administrateur Intune définit une règle de stratégie qui identifie un appareil comme non conforme si celui-ci a une menace active avec un niveau minimum (**haut**, **moyen** ou **faible**). La stratégie de classification des menaces de Lookout Endpoint Security a un impact direct sur la conformité de l’appareil dans Intune.  

## <a name="monitor-enrollment"></a>Surveiller l’inscription
Après que la configuration est terminée, Lookout Mobile Endpoint Security commence à rechercher dans Azure AD les appareils qui correspondent aux groupes d’inscription spécifiés.  Vous pouvez trouver des informations sur les appareils inscrits en accédant à **Appareils** dans la console Lookout MES.  
- L’état initial des appareils est *En attente*.  
- L’état de l’appareil est mis à jour une fois que l’application *Lookout for Work* est installée, ouverte et activée sur l’appareil.

Pour plus d’informations sur la façon de déployer l’application *Lookout for Work* sur un appareil, consultez [Ajouter des applications Lookout for work avec Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Étapes suivantes

[Configurer les applications Lookout](mtd-apps-ios-app-configuration-policy-add-assign.md)
