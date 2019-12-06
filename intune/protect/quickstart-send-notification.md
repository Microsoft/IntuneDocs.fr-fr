---
title: 'Démarrage rapide : Envoyer des notifications aux appareils non conformes'
titleSuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous utilisez Microsoft Intune pour envoyer des notifications par e-mail aux appareils non conformes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410249"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Démarrage rapide : Envoyer des notifications aux appareils non conformes

Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour envoyer un e-mail de notification aux membres de votre personnel qui utilisent des appareils non conformes.

Par défaut, quand Intune détecte un appareil qui n’est pas conforme, il le marque immédiatement comme étant non conforme. L’[Accès conditionnel](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) Azure Active Directory (Azure AD) bloque alors l’appareil. Quand un appareil n’est pas conforme, Intune vous permet d’ajouter des actions en cas de non-conformité qui offrent plus de flexibilité pour décider de ce qu’il faut faire. Par exemple, vous pouvez accorder aux utilisateurs une période de grâce pour leur laisser le temps de mettre en conformité leurs appareils non conformes avant de bloquer ces derniers.

Une action à effectuer lorsqu’un appareil ne satisfait pas à la conformité consiste à envoyer un e-mail à l’utilisateur de l’appareil. Vous pouvez aussi personnaliser un e-mail de notification avant de l’envoyer. Plus précisément, vous pouvez personnaliser les destinataires, l’objet et le corps du message, y compris le logo de l’entreprise et les informations de contact. Intune fournit également des informations sur l’appareil non conforme dans l’e-mail de notification.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

Quand vous utilisez des stratégies de conformité de l’appareil pour bloquer l’accès des appareils aux ressources de l’entreprise, l’accès conditionnel Azure AD doit être configuré. Si vous avez précédemment suivi le guide de démarrage rapide [Créer une stratégie de conformité des appareils](quickstart-set-password-length-android.md), vous utilisez déjà Azure Active Directory. Pour plus d’informations sur Azure AD, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) et [Utilisations courantes de l’accès conditionnel avec Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) comme [Administrateur général](../fundamentals/users-add.md#types-of-administrators) ou [Administrateur de service Intune](../fundamentals/users-add.md#types-of-administrators). Si vous avez créé un abonnement d’essai Intune, le compte que vous avez utilisé est l’administrateur général.

## <a name="create-a-notification-message-template"></a>Créer un modèle de message de notification

Pour envoyer un e-mail à vos utilisateurs, créez un modèle de message de notification. Quand un appareil n’est pas conforme, les détails que vous entrez dans le modèle sont indiqués dans l’e-mail envoyé à vos utilisateurs.

1. Dans Intune, sélectionnez **Appareils** > **Stratégies de conformité** > **Notifications** > **Créer une notification**.
2. Entrez les informations suivantes :

   - **Nom** : *Administrateur Contoso*
   - **Objet** : *Conformité de l’appareil*
   - **Message** : *Votre appareil n’est actuellement pas conforme aux exigences de conformité de notre organisation.*
   - **En-tête de l’e-mail - Inclure le logo de l’entreprise** : Définissez la valeur **Activé** pour afficher le logo de votre organisation.
   - **Pied de page de l’e-mail - Inclure le nom de l’entreprise** : Définissez la valeur **Activé** pour afficher le nom de votre organisation.
   - **Pied de page de l’e-mail - Inclure les informations de contact** : Définissez la valeur **Activé** pour afficher les informations de contact de votre organisation.

   ![Exemple de message de notification de conformité dans Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Sélectionnez **Suivant** et passez en revue votre notification. Sélectionnez **Créer**, et le modèle de message de notification est prêt à être utilisé.

   > [!NOTE]
   > Vous pouvez également modifier un modèle de notification existant.

Pour plus d’informations sur la définition du nom de votre société, ses informations de contact et son logo, consultez les articles suivants :

- [Informations et déclaration de confidentialité de l’entreprise](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Informations concernant le support](../apps/company-portal-app.md#support-information)
- [Personnalisation de l’identité de la société](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Ajouter une stratégie de non-conformité

Quand vous créez une stratégie de conformité des appareils, Intune crée automatiquement une action en cas de non-conformité. Intune marque ensuite les appareils comme non conformes lorsqu’ils ne satisfont pas à votre stratégie de conformité. Vous pouvez personnaliser la durée pendant laquelle l’appareil reste marqué comme non conforme. Vous pouvez également ajouter une autre action quand vous créez une stratégie de conformité ou mettez à jour une stratégie de conformité existante.

Effectuez les étapes suivantes si vous souhaitez créer une stratégie de conformité pour les appareils Windows 10.

1. Dans Intune, sélectionnez **Appareils** > **Stratégies de conformité** > **Créer une stratégie**.

2. Entrez les informations suivantes :

   - **Nom** : *Conformité Windows 10*
   - **Description** : *Stratégie de conformité Windows 10*
   - **Plateforme** : Windows 10 et versions ultérieures

3. Sélectionnez **Paramètres** > **Sécurité système** pour afficher les paramètres de sécurité des appareils.

4. Configurez les options suivantes :

   - Définissez **Exiger un mot de passe pour déverrouiller des appareils mobiles** sur **Exiger**. Ce paramètre indique si les utilisateurs doivent entrer un mot de passe avant d'accéder aux informations stockées sur leurs périphériques mobiles.

   - Définissez **Longueur minimale du mot de passe** sur **6**. Ce paramètre indique le nombre minimal de chiffres ou de caractères figurant dans le mot de passe.

   ![Paramètres de sécurité système pour une nouvelle stratégie de conformité](./media/quickstart-send-notification/system-security-settings-01.png)

5. Sélectionnez **OK** > **OK** > **Créer** pour créer une stratégie de conformité.

6. Sélectionnez **Propriétés** > **Action en cas de non-conformité** > **Ajouter**.

7. Dans la zone déroulante **Action**, vérifiez que l’option **Envoyer un e-mail aux utilisateurs finaux** est sélectionnée.

8. Sélectionnez **Modèle de message**, le modèle de message que vous avez créé précédemment dans cette rubrique, puis **Sélectionner** pour sélectionner le modèle de message.

9. Sélectionnez **AJOUTER** > **OK** > **Enregistrer** pour enregistrer vos modifications.

## <a name="assign-the-policy"></a>Affecter la stratégie

Vous pouvez attribuer la stratégie de conformité à un groupe spécifique d’utilisateurs ou bien à tous les utilisateurs. Quand Intune détecte qu’un appareil n’est pas conforme, il notifie l’utilisateur qu’il doit mettre à jour son appareil pour le mettre en conformité avec la stratégie qui s’applique. Effectuez les étapes suivantes pour attribuer la stratégie.

1. Dans Intune, accédez à **Appareils** > **Stratégies de conformité** et sélectionnez la stratégie **Conformité Windows 10** que vous avez créée précédemment.

2. Sélectionnez **Affectations**.

3. Dans la zone de liste déroulante **Attribuer à**, sélectionnez **Tous les utilisateurs**. La stratégie sera ainsi attribuée à l’ensemble des utilisateurs. Tout utilisateur d’un appareil **Windows version 10 ou ultérieure** qui n’est pas conforme à cette stratégie de conformité recevra une notification.

    > [!NOTE]
    > Vous pouvez inclure et exclure des groupes quand vous attribuez des stratégies de conformité.

4. Cliquez sur **Save**.

Une fois que vous avez correctement créé et enregistré la stratégie, celle-ci apparaît dans la liste **Stratégies de conformité : stratégies**. Notez que, dans la liste, **Attribué** a la valeur **Oui**.

## <a name="next-steps"></a>Étapes suivantes

Pour ce guide de démarrage rapide, vous avez utilisé Intune pour créer et attribuer une stratégie de conformité pour les appareils Windows 10 de votre personnel afin d’exiger un mot de passe d’au moins six caractères. Pour plus d’informations sur la création des stratégies de conformité des appareils Windows, consultez [Ajouter une stratégie de conformité des appareils pour les appareils Windows dans Intune](compliance-policy-create-windows.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Ajouter et attribuer une application cliente](../apps/quickstart-add-assign-app.md)
