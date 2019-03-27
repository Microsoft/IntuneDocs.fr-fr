---
title: 'Démarrage rapide : Envoyer des notifications aux appareils non conformes'
titlesuffix: Microsoft Intune
description: Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour envoyer des notifications par e-mail aux appareils non conformes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 757191515ca88cedf1a5edcdb243b1ecb730ec3c
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57991119"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Démarrage rapide : Envoyer des notifications aux appareils non conformes

Dans ce guide de démarrage rapide, vous allez utiliser Microsoft Intune pour envoyer un e-mail de notification aux membres de votre personnel qui utilisent des appareils non conformes.

Par défaut, quand Intune détecte un appareil qui n’est pas conforme, il le marque immédiatement comme étant non conforme. [L’accès conditionnel](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) Azure Active Directory (AD) bloque alors l’appareil. Quand un appareil n’est pas conforme, Intune vous permet d’ajouter des actions en cas de non-conformité qui offrent plus de flexibilité pour décider de ce qu’il faut faire. Par exemple, vous pouvez accorder aux utilisateurs une période de grâce pour leur laisser le temps de mettre en conformité leurs appareils non conformes avant de bloquer ces derniers.

Une des actions possibles en présence d’appareils non conformes est d’envoyer un e-mail aux utilisateurs finaux de ces appareils. Vous pouvez aussi personnaliser un e-mail de notification avant de l’envoyer aux utilisateurs. Plus précisément, vous pouvez personnaliser les destinataires, l’objet et le corps du message, y compris le logo de l’entreprise et les informations de contact. Intune fournit également des informations sur l’appareil non conforme dans l’e-mail de notification.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
- Quand vous utilisez des stratégies de conformité des appareils pour bloquer l’accès des appareils aux ressources de l’entreprise, l’accès conditionnel AAD doit être configuré. Si vous avez précédemment suivi le guide de démarrage rapide [Créer une stratégie de conformité des appareils](quickstart-set-password-length-android.md), vous utilisez déjà Azure Active Directory. Pour plus d’informations sur AAD, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) et [Utilisations courantes de l’accès conditionnel avec Intune](conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous au portail [Intune](https://aka.ms/intuneportal) comme [administrateur général](users-add.md#types-of-administrators) ou [administrateur de service](users-add.md#types-of-administrators) Intune. 

## <a name="create-a-notification-message-template"></a>Créer un modèle de message de notification

Pour envoyer un e-mail à vos utilisateurs, créez un modèle de message de notification. Quand un appareil n’est pas conforme, les détails que vous entrez dans le modèle sont indiqués dans l’e-mail envoyé à vos utilisateurs.

1. Dans Intune, sélectionnez **Conformité des appareils** > **Notifications** > **Créer une notification**. 
2. Entrez les informations suivantes :

   - **Nom** : *Administrateur Contoso*
   - **Objet** : *Conformité de l’appareil*
   - **Message** : *Votre appareil n’est actuellement pas conforme aux exigences de conformité de notre organisation.*
   - **En-tête de l’e-mail - Inclure le logo de l’entreprise** : Définissez la valeur **Activé** pour afficher le logo de votre organisation.
   - **Pied de page de l’e-mail - Inclure le nom de l’entreprise** : Définissez la valeur **Activé** pour afficher le nom de votre organisation.
   - **Pied de page de l’e-mail - Inclure les informations de contact** : Définissez la valeur **Activé** pour afficher les informations de contact de votre organisation.

   ![Exemple de message de notification de conformité dans Intune](./media/quickstart-send-notification-01.png)

3. Une fois que vous avez terminé l’ajout des informations, choisissez **Créer**. Le modèle de message de notification est prêt à être utilisé.

    > [!NOTE]
    > Vous pouvez également modifier un modèle de notification existant.

Pour plus d’informations sur l’ajout du nom, des informations de contact et du logo pour votre entreprise, consultez [Informations et déclaration de confidentialité de l’entreprise](company-portal-app.md#company-information-and-privacy-statement), [Informations concernant le support](company-portal-app.md#support-information) et [Personnalisation de l’identité de la société](company-portal-app.md#company-identity-branding-customization). 

## <a name="add-a-noncompliance-policy"></a>Ajouter une stratégie de non-conformité

Quand vous créez une stratégie de conformité des appareils, Intune crée automatiquement une action en cas de non-conformité. Quand un appareil ne satisfait pas à votre stratégie de conformité, Intune marque automatiquement l’appareil comme non conforme. Vous pouvez personnaliser la durée pendant laquelle l’appareil reste marqué comme non conforme. Vous pouvez également ajouter une autre action quand vous créez une stratégie de conformité ou mettez à jour une stratégie de conformité existante. 

Effectuez les étapes suivantes si vous souhaitez créer une stratégie de conformité pour les appareils Windows 10.

1. Dans Intune, sélectionnez **Conformité des appareils**.
2. Sélectionnez **Stratégies** > **Créer une stratégie**.
3. Entrez les informations suivantes :

   - **Nom** : *Conformité Windows 10*
   - **Description** : *Stratégie de conformité Windows 10*
   - **Plateforme** : Windows 10 et versions ultérieures

4. Sélectionnez **Paramètres** > **Sécurité système** pour afficher les paramètres de sécurité des appareils.
5. Définissez **Exiger un mot de passe pour déverrouiller des appareils mobiles** sur **Exiger**. Ce paramètre indique si les utilisateurs doivent entrer un mot de passe avant d'accéder aux informations stockées sur leurs périphériques mobiles. 
6. Définissez **Longueur minimale du mot de passe** sur **6**. Ce paramètre indique le nombre minimal de chiffres ou de caractères figurant dans le mot de passe.

    ![Paramètres de sécurité système pour une nouvelle stratégie de conformité](./media/quickstart-send-notification-02.png) 

7. Cliquez sur **OK**, **OK** et **Créer** pour créer une stratégie de conformité.
8. Sélectionnez le nom de votre nouvelle stratégie : **Conformité Windows 10**.
9. Sélectionnez **Propriétés** > **Action en cas de non-conformité** > **Ajouter**.
10. Dans la zone déroulante **Action**, vérifiez que l’option **Envoyer un e-mail aux utilisateurs finaux** est sélectionnée.
11. Sélectionnez **Modèle de message** > **Administrateur Contoso** > **Sélectionner** pour sélectionner le modèle de message que vous avez créé précédemment dans cette rubrique.
12. Sélectionnez **OK** > **OK** > **Enregistrer** pour enregistrer vos modifications.

## <a name="assign-the-policy"></a>Affecter la stratégie

Vous pouvez attribuer la stratégie de conformité à un groupe spécifique d’utilisateurs ou bien à tous les utilisateurs. Quand Intune détecte qu’un appareil n’est pas conforme, il notifie l’utilisateur qu’il doit mettre à jour son appareil pour le mettre en conformité avec la stratégie qui s’applique. Effectuez les étapes suivantes pour attribuer la stratégie.

1. Sélectionnez la stratégie **Conformité Windows 10** que vous avez créée précédemment.
2. Sélectionnez **Affectations**.
3. Dans la zone de liste déroulante **Attribuer à**, sélectionnez **Tous les utilisateurs**. La stratégie sera ainsi attribuée à l’ensemble des utilisateurs. Tout utilisateur d’un appareil **Windows version 10 ou ultérieure** qui n’est pas conforme à cette stratégie de conformité recevra une notification.

    > [!NOTE]
    > Vous pouvez inclure et exclure des groupes quand vous attribuez des stratégies de conformité.

4. Cliquez sur **Save**.

Une fois que vous avez correctement créé et enregistré la stratégie, celle-ci apparaît dans la liste **Conformité des appareils : stratégies**. Notez que, dans la liste, **Attribué** a la valeur **Oui**.

## <a name="next-steps"></a>Étapes suivantes

Pour ce guide de démarrage rapide, vous avez utilisé Intune pour créer et attribuer une stratégie de conformité pour les appareils Windows 10 de votre personnel afin d’exiger un mot de passe d’au moins six caractères. Pour plus d’informations sur la création des stratégies de conformité des appareils Windows, consultez [Ajouter une stratégie de conformité des appareils pour les appareils Windows dans Intune](compliance-policy-create-windows.md).

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Ajouter et attribuer une application cliente](quickstart-add-assign-app.md)
