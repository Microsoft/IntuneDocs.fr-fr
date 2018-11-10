---
title: Actions et message de non-conformité avec Microsoft Intune - Azure | Microsoft Docs
description: Créer un e-mail de notification à envoyer aux appareils non conformes. Ajoutez des actions après qu’un appareil a été marqué comme non conforme, par exemple ajoutez une période de grâce pour la conformité, ou créez une planification afin de bloquer l’accès jusqu’à ce que l’appareil soit conforme. Effectuez ces opérations à l’aide de Microsoft Intune dans Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 953b468337d3317027344573d147b65d765e3db3
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236439"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatiser l’envoi d’un e-mail et ajouter des actions pour les appareils non conformes - Intune

Il existe une fonctionnalité **Actions en cas de non-conformité** qui configure une séquence ordonnée d’actions. Ces actions s’appliquent aux appareils qui ne satisfont pas à votre stratégie de conformité. 

## <a name="overview"></a>Vue d’ensemble
Par défaut, quand Intune détecte un appareil qui n’est pas conforme, il le marque immédiatement comme étant non conforme. L’[accès conditionnel](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) Azure Active Directory (AD) bloque alors l’appareil. Quand un appareil n’est pas conforme, les **actions en cas de non-conformité** offrent davantage de flexibilité pour décider de ce qu’il faut faire. Par exemple, ne pas bloquer immédiatement l’appareil et donner à l’utilisateur une période de grâce pendant laquelle il peut configurer la conformité de l’appareil.

Il existe plusieurs types d’actions :

- **Envoyer un e-mail à l’utilisateur final** : personnalisez un e-mail de notification avant de l’envoyer à l’utilisateur final. Vous pouvez personnaliser les destinataires, l’objet et le corps du message, notamment le logo de l’entreprise et les informations de contact.

    Par ailleurs, Intune ajoute des informations sur l’appareil non conforme dans l’e-mail de notification.

- **Verrouiller à distance l’appareil non conforme** : pour les appareils qui ne sont pas conformes, vous pouvez émettre un verrouillage à distance. L’utilisateur est ensuite invité à entrer un code PIN ou un mot de passe pour déverrouiller l’appareil. Découvrez plus en détail la fonctionnalité [Verrouillage à distance](device-remote-lock.md). 

- **Marquer l’appareil comme non conforme** : créez une planification, c’est-à-dire un nombre de jours au terme desquels l’appareil est marqué comme non conforme. Vous pouvez décider d’exécuter l’action immédiatement ou octroyer à l’utilisateur une période de grâce pour se mettre en conformité.

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

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Conformité de l’appareil** > **Notifications**.
3. Sélectionnez **Créer une notification**. Entrez les informations suivantes :

   - **Nom**
   - **Objet**
   - **Message**
   - **En-tête de l’e-mail - Inclure le logo de l’entreprise**
   - **Pied de page de l’e-mail - Inclure le nom de l’entreprise**
   - **Pied de page de l’e-mail - Inclure les informations de contact**

   ![Exemple de message de notification de conformité dans Intune](./media/actionsfornoncompliance-1.PNG)

4. Une fois que vous avez terminé l’ajout des informations, choisissez **Créer**. Le modèle de message de notification est prêt à être utilisé. Notez que le logo que vous chargez dans le cadre de la personnalisation du Portail d’entreprise sera utilisé pour les modèles e-mail. Pour plus d’informations sur la personnalisation du Portail d’entreprise, consultez [Personnalisation de l’identité de la société](company-portal-app.md#company-identity-branding-customization).  

> [!NOTE]
> Vous pouvez également modifier un modèle de notification créé précédemment.

## <a name="add-actions-for-noncompliance"></a>Ajouter des actions en cas de non-conformité

Quand vous créez une stratégie de conformité des appareils, Intune crée automatiquement une action en cas de non-conformité. Quand un appareil ne satisfait pas à votre stratégie de conformité, cette action marque l’appareil comme non conforme. Vous pouvez personnaliser la durée pendant laquelle l’appareil est marqué comme non conforme. Cette action ne peut pas être supprimée.

Vous pouvez également ajouter une autre action quand vous créez une stratégie de conformité ou mettez à jour une stratégie existante. 

1. Dans le [portail Azure](https://portal.azure.com), ouvrez **Microsoft Intune** > **Conformité de l’appareil**.
2. Sélectionnez **Stratégies**, choisissez l’une de vos stratégies, puis sélectionnez **Propriétés**. 

    Vous n’avez pas encore de stratégie ? Créez une stratégie [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) ou une stratégie pour une autre plateforme.
  
    > [!NOTE]
    > Pour le moment, les appareils JAMF et les appareils ciblés avec des groupes d’appareils ne peuvent pas recevoir des actions de conformité.

3. Sélectionnez **Actions en cas de non-conformité** > **Ajouter**.
4. Sélectionnez votre **Action** : 

    - **Envoyer un e-mail à l’utilisateur final** : quand l’appareil n’est pas conforme, envoyer un e-mail à l’utilisateur. En outre : 
    
         - Choisissez le **Modèle de message** que vous avez créé
         - Entrez d’**Autres destinataires** en sélectionnant des groupes
    
    - **Verrouiller à distance l’appareil non conforme** : quand l’appareil n’est pas conforme, verrouiller l’appareil. L’utilisateur est ainsi obligé d’entrer un code PIN ou un mot de passe pour déverrouiller l’appareil. 
    
    - **Planification** : entrez le nombre de jours de non-conformité (0 à 365) au terme desquels l’action doit être déclenchée sur les appareils des utilisateurs. Après cette période de grâce, vous pouvez appliquer une stratégie d’accès conditionnel. Si vous entrez **0** comme nombre de jours, l’accès conditionnel prend effet **immédiatement**. Par exemple, vous pouvez bloquer l’accès aux ressources d’entreprise immédiatement si un appareil n’est pas conforme.

5. Quand vous avez terminé, sélectionnez **Ajouter** > **OK** pour enregistrer les modifications.

## <a name="next-steps"></a>Étapes suivantes
[Superviser l’activité de conformité de l’appareil](device-compliance-monitor.md).
