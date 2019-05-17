---
title: Créer une stratégie d’accès conditionnel Exchange
titleSuffix: Microsoft Intune
description: Configurer l’accès conditionnel pour Exchange sur site et Exchange Online Dedicated hérité dans Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 003e6e5aa78440861e6aff5be138c4a302171c1b
ms.sourcegitcommit: a2cd14c30949cef17bfc6576513e7660a8015669
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2019
ms.locfileid: "59571737"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Créer une stratégie d’accès conditionnel pour Exchange sur site et Exchange Online Dedicated hérité

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article montre comment configurer l’accès conditionnel pour Exchange sur site basé sur la conformité des appareils.

Si vous disposez d’un environnement Exchange Online Dedicated et que vous ne savez pas s’il s’agit de la nouvelle configuration ou d’une configuration héritée, contactez votre responsable de compte. Pour contrôler l’accès à la messagerie Exchange sur site ou Exchange Online Dedicated (environnement hérité), configurez l’accès conditionnel à Exchange sur site dans Intune.

## <a name="before-you-begin"></a>Avant de commencer

Avant de configurer l’accès conditionnel, vérifiez les éléments suivants :

- Votre version d’Exchange doit être **Exchange 2010 SP1 ou une version ultérieure**. Le groupe de serveurs d’accès au client (CAS) du serveur Exchange est pris en charge.

- Vous devez utiliser le [connecteur Exchange Active Sync sur site](exchange-connector-install.md) qui connecte Intune à Exchange sur site.

    >[!IMPORTANT]
    >Le connecteur Exchange local est propre à votre client Intune et ne peut pas être utilisé avec un autre client. Intune prend désormais en charge plusieurs connecteurs Exchange locaux par abonnement. Si vous avez plusieurs organisations Exchange locales, vous pouvez configurer un connecteur distinct pour chacune d’elles.

- Vous pouvez installer le connecteur d’une organisation Exchange locale sur n’importe quelle machine, tant que celle-ci peut communiquer avec le serveur Exchange.

- Le connecteur prend en charge l’**Environnement CAS Exchange**. Techniquement, vous pouvez installer directement le connecteur sur le serveur CAS Exchange si vous le souhaitez, mais cette opération est déconseillée car elle augmente la charge sur le serveur. Quand vous configurez le connecteur, vous devez faire en sorte qu’il communique avec l’un des serveurs CAS Exchange.

- Vous devez configurer **Exchange ActiveSync** avec l’authentification par certificat ou via les informations d’identification entrées par l’utilisateur.

- Une fois les stratégies d’accès conditionnel configurées et ciblées sur un utilisateur, l’**appareil** dont l’utilisateur se sert pour se connecter à sa messagerie doit :
    - Être **inscrit** auprès d’Intune ou avoir un PC joint à un domaine.
    - Être **inscrit dans Azure Active Directory**. En outre, l’ID Exchange ActiveSync du client doit être inscrit auprès d’Azure Active Directory.
<br></br>
- Le service Azure AD Device Registration Service (DRS) est activé automatiquement pour les clients Intune et Office 365. Les clients qui ont déjà déployé le service ADFS Device Registration Service ne voient pas les appareils inscrits dans leur annuaire Active Directory local. **Cela ne s’applique pas aux PC Windows ni aux appareils Windows Phone**.

- **Conforme** aux stratégies de conformité d’appareil déployées sur cet appareil.

- Si l’appareil ne répond pas aux paramètres d’accès conditionnel, l’utilisateur reçoit un des messages suivants quand il tente de se connecter :
    - Si l’appareil n’est pas inscrit auprès d’Intune ou qu’il n’est pas inscrit dans Azure Active Directory, l’utilisateur reçoit un message contenant des instructions pour installer l’application Portail d’entreprise, inscrire l’appareil et activer la messagerie. Ce processus associe également l’ID Exchange ActiveSync de l’appareil à l’enregistrement de l’appareil dans Azure Active Directory.
    - Si l’appareil n’est pas conforme, l’utilisateur reçoit un message le dirigeant vers le site web ou l’application Portail d’entreprise Intune, où il peut trouver des informations sur le problème et des solutions pour y remédier.

### <a name="support-for-mobile-devices"></a>Prise en charge des appareils mobiles

- Windows Phone 8.1 et versions ultérieures
- Application de messagerie native sur iOS.
- Clients de messagerie EAS, comme Gmail sur Android 4 ou ultérieur.
- Clients de messagerie EAS sur les **appareils avec profil professionnel Android** : seules les applications **Gmail** et **Nine Work for Android Enterprise** dans le **profil professionnel** sont prises en charge sur les appareils avec profil professionnel Android. Pour que l’accès conditionnel fonctionne avec les profils professionnels Android, vous devez déployer un profil de messagerie pour l’application Gmail ou Nine Work for Android Enterprise, et également déployer ces applications comme installation obligatoire.

> [!NOTE]
> Microsoft Outlook pour Android et iOS n’est pas pris en charge via le connecteur local Exchange. Si vous souhaitez tirer parti des stratégies d’accès conditionnel d’Azure Active Directory et des stratégies Intune App Protection avec Outlook pour iOS et Android pour vos boîtes aux lettres locales, consultez [Utilisation de l’authentification hybride moderne avec Outlook pour iOS et Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). 

### <a name="support-for-pcs"></a>Prise en charge des PC

L'application native **Courrier** sur Windows 8.1 et les versions ultérieures (en cas d’inscription auprès d'Intune)


## <a name="configure-exchange-on-premises-access"></a>Configuration de l'accès à Exchange sur site

1. Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous avec vos informations d’identification Intune.

2. Accédez à **Intune** > **Accès à Exchange**, puis sélectionnez **Accès à Exchange sur site**. 

3. Dans le volet **Accès à Exchange sur site**, choisissez **Oui** pour *Activer le contrôle d’accès à Exchange sur site*.

4. Choisissez **Tous les services** dans le menu de gauche, puis entrez **Intune** dans le filtre de la zone de texte.

5. Choisissez **Intune**, vous voyez le **tableau de bord Intune**.

6. Choisissez **Accès local**. Le volet **Accès local** affiche l’état de la stratégie d’accès conditionnel et les appareils qui en sont affectés.

7. Sous **Gérer**, choisissez **Accès à Exchange sur site**.

8. Dans le volet **Accès à Exchange sur site**, choisissez **Oui** pour activer le contrôle d’accès Exchange sur site.

    > [!NOTE]
    > Si vous n’avez pas configuré de connecteur Exchange Active Sync local, cette option est désactivée.  Vous devez tout d’abord installer et configurer au moins un connecteur avant d’activer l’accès conditionnel pour Exchange local. Pour plus de détails, consultez la rubrique [Installer le connecteur Exchange local de Microsoft Intune](exchange-connector-install.md)

9. Sous **Affectation**, choisissez **Groupes inclus**.  Utilisez le groupe d’utilisateurs de sécurité auquel appliquer l'accès conditionnel. Dans ce cas, les utilisateurs doivent inscrire leurs appareils auprès d’Intune et se conformer aux profils de conformité.

10. Si vous voulez exclure des groupes d’utilisateurs spécifiques, vous pouvez le faire en choisissant **Groupes exclus**, puis en sélectionnant un groupe d’utilisateurs exempté de l’inscription et de la conformité des appareils.

11. Sous **Paramètres**, choisissez **Notifications utilisateur** pour modifier l'e-mail par défaut. Ce message est envoyé aux utilisateurs si leur appareil n’est pas conforme alors qu'ils souhaitent accéder à Exchange sur site. Le modèle de message utilise le langage de balisage.  Vous voyez également un aperçu du message en cours de frappe.
    > [!TIP]
    > Pour en savoir plus sur le langage de balisage, consultez cet [article](https://en.wikipedia.org/wiki/Markup_language) Wikipedia.

12. Dans le volet des **paramètres d’accès Exchange Active Sync avancés**, définissez la règle globale par défaut pour l’accès à partir d’appareils qui ne sont pas gérés par Intune et pour les règles de niveau plateforme comme décrit dans les deux prochaines étapes. Pour accéder au volet des paramètres avancés, dans la vue *Accès à Exchange - Accès à Exchange sur site*, sélectionnez *Connecteur local Exchange ActiveSync*.

13. Si vous avez un appareil qui n'est pas affecté par l'accès conditionnel ou d'autres règles, vous pouvez choisir de l'autoriser l'accès à Exchange ou le bloquer.

   - Quand vous définissez cette option pour autoriser l’accès, tous les appareils peuvent accéder immédiatement à Exchange sur site.  Les appareils qui appartiennent aux utilisateurs dans les **Groupes inclus** sont bloqués s’ils sont évalués par la suite comme non conforme aux stratégies de conformité ou ne sont pas inscrits auprès d'Intune.
   - Quand vous définissez cette option pour bloquer l’accès, l’accès initial des appareils à Exchange sur site est immédiatement bloqué.  Les appareils qui appartiennent à des utilisateurs des **Groupes inclus** reçoivent un accès une fois que ces appareils sont inscrits auprès d’Intune et déterminés comme conformes. Les appareils Android qui n’exécutent pas Samsung Knox standard sont toujours bloqués, car ils ne prennent pas en charge ce paramètre.

14. Sous **Exceptions de la plateforme d'appareils**, choisissez **Ajouter** pour spécifier les plateformes. Si le paramètre **Accès aux appareils non gérés** est défini sur **Bloqué**, les appareils qui sont inscrits et conformes sont autorisés, même s’il existe une exception de plateforme qui bloque. Choisissez **OK** pour enregistrer les paramètres.

15. Dans le volet **Local**, cliquez sur **Enregistrer** pour enregistrer la stratégie d’accès conditionnel.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Création de stratégies d’accès conditionnel Azure AD dans Intune

L’accès conditionnel est une technologie Azure Active Directory (Azure AD). Le nœud d’accès conditionnel accessible à partir d’*Intune* est le même nœud que celui accessible à partir d’*Azure AD*.  

> [!IMPORTANT]
> Vous devez disposer d’une licence Azure AD Premium pour créer des stratégies d’accès conditionnel Azure AD à partir du portail Intune Azure.

### <a name="to-create-a-conditional-access-policy"></a>Pour créer une stratégie d’accès conditionnel

1. Dans le **tableau de bord Intune**, sélectionnez **Accès conditionnel**.

2. Dans le volet **Stratégies**, sélectionnez **Nouvelle stratégie** pour créer votre stratégie d’accès conditionnel Azure AD.

## <a name="see-also"></a>Voir aussi

[Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
