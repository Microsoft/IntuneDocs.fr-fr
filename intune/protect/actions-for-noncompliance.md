---
title: Actions et message de non-conformité avec Microsoft Intune - Azure | Microsoft Docs
description: Créer un e-mail de notification à envoyer aux appareils non conformes. Ajoutez des actions après qu’un appareil a été marqué comme non conforme, par exemple ajoutez une période de grâce pour la conformité, ou créez une planification afin de bloquer l’accès jusqu’à ce que l’appareil soit conforme. Effectuez ces opérations à l’aide de Microsoft Intune dans Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e3867bfc2de29c059766e134bd0d2c8801e1c70
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712906"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatiser l’envoi d’un e-mail et ajouter des actions pour les appareils non conformes dans Intune

Pour les appareils qui ne respectent pas vos règles ou stratégies de conformité, vous pouvez ajouter des **actions en cas de non-conformité**. Cette fonctionnalité configure une séquence chronologique d’actions, comme l’envoi d’un e-mail à l’utilisateur final, etc.

## <a name="overview"></a>Vue d’ensemble

Par défaut, quand Intune détecte un appareil qui n’est pas conforme, il le marque immédiatement comme étant non conforme. L’[Accès conditionnel](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) Azure Active Directory (AD) bloque alors l’appareil. Quand un appareil n’est pas conforme, une **action en cas de non-conformité** offre davantage de flexibilité pour décider de ce que vous devez faire. Par exemple, ne pas bloquer immédiatement l’appareil et donner à l’utilisateur une période de grâce pendant laquelle il peut configurer la conformité de l’appareil.

Il existe plusieurs types d’actions :

- **Envoyer un e-mail à l’utilisateur final** : Personnalisez une notification par e-mail avant de l’envoyer à l’utilisateur final. Vous pouvez personnaliser les destinataires, l’objet et le corps du message, notamment le logo de l’entreprise et les informations de contact.

    Par ailleurs, Intune ajoute des informations sur l’appareil non conforme dans l’e-mail de notification.

- **Verrouiller à distance l’appareil non conforme** : Pour les appareils qui ne sont pas conformes, vous pouvez émettre un verrouillage à distance. L’utilisateur est ensuite invité à entrer un code PIN ou un mot de passe pour déverrouiller l’appareil. Découvrez plus en détail la fonctionnalité [Verrouillage à distance](../remote-actions/device-remote-lock.md).

- **Marquer l’appareil comme non conforme** : Créez une planification, c’est-à-dire un nombre de jours au terme desquels l’appareil est marqué comme non conforme. Vous pouvez décider d’exécuter l’action immédiatement ou octroyer à l’utilisateur une période de grâce pour se mettre en conformité.

Cet article vous montre comment :

- Créer un modèle de message de notification
- Créer une action en cas de non-conformité, par exemple envoyer un e-mail ou verrouiller un appareil à distance


## <a name="before-you-begin"></a>Avant de commencer

- Pour définir des actions en cas de non-conformité, vous devez avoir au moins une stratégie de conformité de l’appareil. Pour créer une stratégie de conformité de l’appareil, consultez les plateformes suivantes :

  - [Android](compliance-policy-create-android.md)
  - [Profils professionnels Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [MacOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Quand vous utilisez des stratégies de conformité de l’appareil pour bloquer l’accès des appareils aux ressources de l’entreprise, l’accès conditionnel Azure AD doit être configuré. Consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) ou [Utilisations courantes de l’accès conditionnel avec Intune](conditional-access-intune-common-ways-use.md) pour obtenir des conseils.

## <a name="create-a-notification-message-template"></a>Créer un modèle de message de notification

Pour envoyer un e-mail à vos utilisateurs, créez un modèle de message de notification. Quand un appareil n’est pas conforme, les détails que vous entrez dans le modèle sont indiqués dans l’e-mail envoyé à vos utilisateurs.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Stratégies de conformité** > **Notifications** > **Créer une notification**.
3. Sous *Informations de base*, spécifiez les informations suivantes :

   - **Nom**
   - **Objet**
   - **Message**

4. Toujours sous *Informations de base*, configurez les options de notification suivantes, dont la valeur par défaut est toujours *Activée*:

   - **En-tête de l’e-mail - Inclure le logo de l’entreprise**
   - **Pied de page de l’e-mail - Inclure le nom de l’entreprise**
   - **Pied de page de l’e-mail - Inclure les informations de contact**

   Le logo que vous chargez dans le cadre de la personnalisation du Portail d’entreprise est utilisé pour les modèles d’e-mail. Pour plus d’informations sur la personnalisation du Portail d’entreprise, consultez [Personnalisation de l’identité de la société](../apps/company-portal-app.md#company-identity-branding-customization).

   ![Exemple de message de notification de conformité dans Intune](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

   Sélectionnez **Suivant** pour continuer.

5. Sous **Vérifier + créer**, vérifiez que le modèle de message de notification est prêt à être utilisé dans vos configurations. Sélectionnez **Créer** pour terminer la création de la notification.

> [!NOTE]
> Vous pouvez également sélectionner un modèle de notification déjà créé, et **Modifier** ses informations pour le mettre à jour.

## <a name="add-actions-for-noncompliance"></a>Ajouter des actions en cas de non-conformité

Quand vous créez une stratégie de conformité des appareils, Intune crée automatiquement une action en cas de non-conformité. Si un appareil ne répond pas à votre stratégie de conformité, cette action marque l’appareil comme non conforme. Vous pouvez personnaliser la durée pendant laquelle l’appareil est marqué comme non conforme. Cette action ne peut pas être supprimée.

Vous pouvez également ajouter une autre action quand vous créez une stratégie de conformité ou mettez à jour une stratégie existante.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Stratégies de conformité** > **Stratégies**, sélectionnez l’une de vos stratégies, puis sélectionnez **Propriétés**.

   Vous n’avez pas encore de stratégie ? Créez une stratégie [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) ou une stratégie pour une autre plateforme.

   > [!NOTE]
   > Pour le moment, les appareils JAMF et les appareils ciblés avec des groupes d’appareils ne peuvent pas recevoir des actions de conformité.

3. Sélectionnez **Actions en cas de non-conformité** > **Ajouter**.

4. Sélectionnez votre **Action** :

   - **Envoyer un e-mail à l’utilisateur final** : Quand l’appareil n’est pas conforme, choisissez d’envoyer un e-mail à l’utilisateur. En outre :
     - Choisissez le **Modèle de message** que vous avez créé
     - Entrez d’**Autres destinataires** en sélectionnant des groupes

   - **Verrouiller à distance l’appareil non conforme** : Quand l’appareil n’est pas conforme, verrouillez-le. L’utilisateur est ainsi obligé d’entrer un code PIN ou un mot de passe pour déverrouiller l’appareil.

5. Configurer une **planification** : Entrez le nombre de jours de non-conformité (0 à 365) au terme desquels l’action doit être déclenchée sur les appareils des utilisateurs. Après cette période de grâce, vous pouvez appliquer une stratégie d’[accès conditionnel](conditional-access-intune-common-ways-use.md). Si vous entrez **0** (zéro) comme nombre de jours, l’accès conditionnel prend effet **immédiatement**. Par exemple, si un appareil n’est pas conforme, utilisez l’accès conditionnel pour bloquer immédiatement l’accès à la messagerie, à SharePoint et à d’autres ressources de l’organisation.

   Lorsque vous créez une stratégie de conformité, l’action **Marquer l’appareil comme non conforme** est automatiquement créée et définie automatiquement sur **0** jour (immédiatement). Avec cette action, lorsque l’appareil fait l’objet d’un check-in, il est évalué comme non conforme immédiatement. Si vous utilisez également l’accès conditionnel, ce dernier démarre immédiatement. Si vous souhaitez autoriser une période de grâce, modifiez la **Planification** en la définissant sur l’action **Marquer l’appareil comme non conforme**.

   Dans votre stratégie de conformité, par exemple, vous pouvez également notifier l’utilisateur. Vous pouvez ajouter l’action **Envoyer un e-mail à l’utilisateur final**. Dans cette action **Envoyer un e-mail**, définissez la **planification** sur 2 jours. Si l’appareil ou l’utilisateur final est toujours évalué comme non conforme le jour 2, votre e-mail est envoyé le jour 2. Si vous souhaitez envoyer un nouveau message à l’utilisateur le jour 5 de la non-conformité, ajoutez une autre action et définissez la **planification** sur 5 jours.

   Pour plus d’informations sur la conformité et les actions intégrées, consultez la [présentation de la conformité](device-compliance-get-started.md).

6. Quand vous avez terminé, sélectionnez **Ajouter** > **OK** pour enregistrer les modifications.

## <a name="next-steps"></a>Étapes suivantes

[Supervisez vos stratégies](compliance-policy-monitor.md).
