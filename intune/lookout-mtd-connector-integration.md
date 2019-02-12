---
title: Configurer l’intégration de Lookout à Microsoft Intune | Microsoft Intune
description: Découvrez-en plus sur l’intégration d’Intune avec Lookout Mobile Threat Defense (MTD) pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: beb2af07b47a96613ab759ae43752a7c956d6984
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845479"
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>Configurer l’intégration de Lookout Mobile Threat Defense avec Intune

Les étapes suivantes sont nécessaires pour configurer l’abonnement à Lookout Mobile Threat Defense :

| #        |Étape  |
| ------------- |:-------------|
| 1 | [Obtenir vos informations Azure AD](#collect-azure-ad-information) |
| 2 | [Configurer votre abonnement](#configure-your-subscription) |
| 3 | [Configurer les groupes d’inscription](#configure-enrollment-groups) |
| 4 | [Configurer la synchronisation des états](#configure-state-sync) |
| 5 | [Configurer le destinataire des rapports d’erreurs envoyés par e-mail](#configure-error-report-email-recipient-information) |
| 6 | [Configurer les paramètres d’inscription](#configure-enrollment-settings) |
| 7 | [Configurer les notifications par e-mail](#configure-email-notifications) |
| 8 | [Configurer la classification des menaces](#configure-threat-classification) |
| 9 | [Surveillance de l’inscription](#watching-enrollment) |

> [!IMPORTANT]
> Un locataire Lookout Mobile Endpoint Security existant qui n’est pas déjà associé à votre locataire Azure AD ne peut pas être utilisé pour l’intégration à Azure AD et Intune. Contactez le support de Lookout pour créer un locataire Lookout Mobile Endpoint Security. Utilisez le nouveau locataire pour intégrer vos utilisateurs Azure AD.

## <a name="collect-azure-ad-information"></a>Obtenir vos informations Azure AD
Votre locataire Lookout Mobility Endpoint Security sera associé à votre abonnement Azure AD pour intégrer Lookout à Intune. Pour activer votre abonnement au service Lookout Mobile Threat Defense, le support technique Lookout (enterprisesupport@lookout.com) a besoin des informations suivantes :

* **ID de locataire Azure AD**
* **ID d’objet de groupe Azure AD** pour l’accès **complet** à la console Lookout
* **ID d’objet de groupe Azure AD** pour l’accès **restreint** à la console Lookout (facultatif)

Consultez les étapes suivantes pour savoir comment collecter les informations demandées par l’équipe du support technique Lookout.

1. Connectez-vous au [portail Azure](https://portal.azure.com) et sélectionnez votre abonnement. 

2. Lorsque vous choisissez le nom de votre abonnement, l’URL inclut l’ID d’abonnement.  Si vous ne trouvez pas votre ID d’abonnement, consultez cet [article du support technique Microsoft](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) qui fournit des conseils à cette fin.

3. Obtenez votre ID de groupe Azure AD. La console Lookout offre deux niveaux d’accès :  
   * **Accès complet** : l’administrateur Azure AD peut créer un groupe pour les utilisateurs qui ont un accès complet et éventuellement créer un autre groupe pour les utilisateurs qui ont un accès restreint.  Seuls les utilisateurs qui sont membres de ces groupes seront autorisés à se connecter à la **console Lookout**.
   * **Accès restreint** : les utilisateurs membres de ce groupe n’ont pas accès à certains modules d’inscription et de configuration dans la console Lookout, et peuvent accéder en lecture seule au module **Stratégie de sécurité** dans la console Lookout.  

     > [!TIP] 
     > Pour plus d’informations sur les autorisations, consultez [cet article](https://personal.support.lookout.com/hc/articles/114094105653) sur le site web de Lookout.

     > [!NOTE] 
     > L’**ID d’objet de groupe** est indiqué dans la page **Propriétés** du groupe dans le **portail de gestion Azure AD**.

4. Une fois que vous avez collecté ces informations, contactez le support technique Lookout (adresse e-mail : enterprisesupport@lookout.com). Le support technique Lookout travaillera avec votre contact principal pour intégrer votre abonnement et créer votre compte d’entreprise Lookout sur la base des informations que vous avez collectées.

## <a name="configure-your-subscription"></a>Configurer votre abonnement

1. Une fois que le support de Lookout crée votre compte d'entreprise Lookout, Lookout envoie au contact principal de votre entreprise un e-mail contenant un lien vers l’URL de connexion : <https://aad.lookout.com/les?action=consent>.

2. La première connexion à la console Lookout doit être effectuée à l'aide d'un compte d’utilisateur ayant le rôle Azure AD Administrateur général, afin d'inscrire votre locataire Azure AD. Les connexions ultérieures n'ont pas besoin de ce niveau de privilège Azure AD. La page de consentement s’affiche. Choisissez **Accepter** pour terminer l’inscription. Une fois que vous avez donné votre consentement, vous êtes redirigé vers la console Lookout.

   ![capture d’écran de la page de première connexion de la console Lookout](./media/lookout_mtp_initial_login.png)

3. Dans la [console Lookout](https://aad.lookout.com), à partir du module **Système**, choisissez l’onglet **Connecteurs**, puis sélectionnez **Intune**.

   ![Image de la console Lookout avec l’option Intune sous l’onglet Connecteurs](./media/lookout_mtp_setup-intune-connector.png)

4. Accédez à **Connecteurs** > **Paramètres de connexion** et spécifiez la **fréquence de pulsations** en minutes.

   ![Image de l’onglet Paramètres de connexion avec la fréquence de pulsations définie](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Configurer les groupes d’inscription
1. Comme meilleure pratique, créez un groupe de sécurité Azure AD dans le [portail de gestion Azure AD](https://manage.windowsazure.com) contenant un petit nombre d’utilisateurs afin de tester l’intégration Lookout.

    > [!NOTE] 
    > Tous les appareils pris en charge par Lookout, inscrits auprès d’Intune au sein d’un groupe d’inscription dans Azure AD, et qui sont identifiés et pris en charge, sont inscrits et activables dans la console MTD Lookout.

2. Dans la [console Lookout](https://aad.lookout.com), à partir du module **Système**, choisissez l’onglet **Connecteurs**, puis sélectionnez **Enrollment Management** (Gestion de l’inscription) pour définir un ensemble d’utilisateurs dont les appareils doivent être inscrits auprès de Lookout. Ajoutez le groupe de sécurité Azure AD **Nom d'affichage** pour l’inscription.

    ![capture d’écran de la page d’inscription dans le connecteur Intune](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > Le **Nom d’affichage** respecte la casse comme indiqué dans les **Propriétés** du groupe de sécurité sur le portail Azure. Comme le montre l’image ci-dessous, le **nom complet** du groupe de sécurité a une casse mixte, et le titre est entièrement en minuscules. Dans la console Lookout, respectez a casse de **Nom d'affichage** pour le groupe de sécurité.
    >![Image de la page des propriétés du service Azure Active Directory dans le portail Azure](./media/aad-group-display-name.png)

    >[!NOTE] 
    >La bonne pratique consiste à utiliser la valeur par défaut (5 minutes) pour l’incrément de durée de recherche de nouveaux appareils. Limitations actuelles, **Lookout ne peut pas valider les noms d’affichage de groupe** : Vérifiez que le champ **NOM D'AFFICHAGE** dans le portail Azure correspond exactement au groupe de sécurité Azure AD. **La création de groupes imbriqués n’est pas prise en charge** :  Les groupes de sécurité Azure AD utilisés dans Lookout doivent contenir uniquement des utilisateurs. Ils ne peuvent pas contenir d’autres groupes.

3.  Lorsqu'un groupe est créé, la prochaine fois qu'un utilisateur ouvre l'application Lookout for Work sur son appareil pris en charge, ce dernier est activé dans Lookout.

4.  Une fois que vous êtes satisfait de vos résultats, étendez l’inscription à d'autres groupes d’utilisateurs.

## <a name="configure-state-sync"></a>Configurer la synchronisation des états
Dans l’option **Synchronisation des états**, spécifiez le type de données à envoyer à Intune.  L’état de l’appareil et l’état de la menace sont requis pour que l’intégration Lookout Intune fonctionne correctement. Ces paramètres sont activés par défaut.

## <a name="configure-error-report-email-recipient-information"></a>Configurer le destinataire des rapports d’erreurs envoyés par e-mail
Dans l’option **Gestion des erreurs**, entrez l’adresse e-mail à laquelle doivent être envoyés les rapports d’erreurs.

![capture d’écran de la page Gestion des erreurs dans le connecteur Intune](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Configurer les paramètres d’inscription
Dans le module **Système**, dans la page **Connecteurs**, spécifiez le nombre de jours au terme desquels un appareil est considéré comme déconnecté.  Les appareils déconnectés sont considérés comme non conformes et ne peuvent pas accéder à vos applications d’entreprise en fonction des stratégies d’accès conditionnel Intune. Vous pouvez spécifier des valeurs comprises entre 1 et 90 jours.

![Paramètres d’inscription Lookout dans le module Système](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Configurer les notifications par e-mail
Si vous souhaitez recevoir des alertes sur les menaces par e-mail, connectez-vous à la [console Lookout](https://aad.lookout.com) avec le compte d’utilisateur qui doit recevoir les notifications. Sous l’onglet **Préférences** du module **Système**, choisissez les niveaux de menace qui doivent générer des notifications et définissez-les sur **ACTIVÉ**. Enregistrez vos modifications.

![capture d’écran de la page des préférences pour le compte d’utilisateur connecté](./media/lookout-mtp-email-notifications.png) Si vous ne souhaitez plus recevoir de notifications par e-mail, définissez les notifications avec la valeur **DÉSACTIVÉ**, puis enregistrez vos modifications.

### <a name="configure-threat-classification"></a>Configurer la classification des menaces
Lookout Mobile Threat Defense classe les menaces mobiles de différents types. Les [classifications des menaces dans Lookout](https://personal.support.lookout.com/hc/articles/114094130693) ont des niveaux de risque par défaut qui leur sont associés. Ces niveaux peuvent être modifiés à tout moment en fonction des besoins de votre entreprise.

![capture d’écran de la page de stratégie montrant des menaces et des classifications](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Les niveaux de risque sont un aspect important de la solution Mobile Threat Defense car l’intégration d’Intune évalue la conformité de l’appareil en fonction de ces niveaux de risque lors de l’exécution. L’administrateur Intune définit une règle de stratégie qui identifie un appareil comme non conforme si celui-ci a une menace active avec un niveau minimum (**haut**, **moyen** ou **faible**). La stratégie de classification des menaces de Lookout Mobile Threat Defense évalue la conformité d’appareil dans Intune.

## <a name="watching-enrollment"></a>Surveillance de l’inscription
Une fois l’installation terminée, Lookout Mobile Threat Defense commence à rechercher dans Azure AD les appareils qui correspondent aux groupes d’inscription spécifiés.  Les informations sur les appareils inscrits se trouvent dans le module Appareils.  Les appareils s’affichent dans l’état initial En attente.  L’état de l’appareil change une fois que l’application Lookout for Work est installée, ouverte et activée sur l’appareil.  Pour plus d’informations sur l’envoi (push) de l’application Lookout for Work sur l’appareil, consultez [Ajouter des applications Lookout for work avec Intune](mtd-apps-ios-app-configuration-policy-add-assign.md).

## <a name="next-steps"></a>Étapes suivantes

[Configurer les applications Lookout](mtd-apps-ios-app-configuration-policy-add-assign.md)
