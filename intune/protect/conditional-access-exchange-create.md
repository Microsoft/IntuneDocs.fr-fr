---
title: Créer une stratégie d’accès conditionnel Exchange
titleSuffix: Microsoft Intune
description: Configurez l’accès conditionnel pour Exchange sur site et Exchange Online Dedicated hérité dans Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4962b4c75460b129f9df7729b5a34485d8ee0760
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576077"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Créer une stratégie d’accès conditionnel pour Exchange sur site et Exchange Online Dedicated hérité

Cet article montre comment configurer l’accès conditionnel pour Exchange sur site basé sur la conformité des appareils.

Si vous disposez d’un environnement Exchange Online Dedicated et que vous ne savez pas s’il s’agit de la nouvelle configuration ou d’une configuration héritée, contactez votre responsable de compte. Pour contrôler l’accès à la messagerie Exchange sur site ou Exchange Online Dedicated (environnement hérité), configurez l’accès conditionnel à Exchange sur site dans Intune.

## <a name="before-you-begin"></a>Avant de commencer

Avant de configurer l’accès conditionnel, vérifiez que les configurations suivantes existent :

- Votre version d’Exchange est **Exchange 2010 SP1 ou une version ultérieure**. Le groupe de serveurs d’accès au client (CAS) du serveur Exchange est pris en charge.

- Vous avez installé et utilisez le [connecteur Exchange ActiveSync sur site](exchange-connector-install.md) qui connecte Intune à Exchange sur site.

    >[!IMPORTANT]  
    >Intune prend en charge plusieurs connecteurs Exchange locaux par abonnement.  Cependant, le connecteur Exchange local est propre à un seul client Intune et ne peut pas être utilisé avec un autre client.  Si vous avez plusieurs organisations Exchange locales, vous pouvez configurer un connecteur distinct pour chacune d’elles.

- Vous pouvez installer le connecteur d’une organisation Exchange locale sur n’importe quelle machine, tant que celle-ci peut communiquer avec le serveur Exchange.

- Le connecteur prend en charge l’**Environnement CAS Exchange**. Intune prend en charge l’installation du connecteur directement sur le serveur CAS Exchange. Nous vous recommandons de l’installer sur un autre ordinateur distinct en raison de la charge supplémentaire que le connecteur met sur le serveur. Quand vous configurez le connecteur, vous devez faire en sorte qu’il communique avec l’un des serveurs CAS Exchange.

- Vous devez configurer **Exchange ActiveSync** avec l’authentification par certificat ou via les informations d’identification entrées par l’utilisateur.

- Une fois les stratégies d’accès conditionnel configurées et ciblées sur un utilisateur, l’**appareil** dont l’utilisateur se sert pour se connecter à sa messagerie doit :
  - Être **inscrit** auprès d’Intune ou avoir un PC joint à un domaine.
  - Être **inscrit dans Azure Active Directory**. En outre, l’ID Exchange ActiveSync du client doit être inscrit auprès d’Azure Active Directory.

- Le service Azure AD Device Registration Service (DRS) est activé automatiquement pour les clients Intune et Office 365. Les clients qui ont déjà déployé le service ADFS Device Registration Service ne voient pas les appareils inscrits dans leur annuaire Active Directory local. **Cela ne s’applique pas aux PC Windows ni aux appareils Windows Phone**.

- **Conforme** aux stratégies de conformité d’appareil déployées sur cet appareil.

- Si l’appareil ne répond pas aux paramètres d’accès conditionnel, l’utilisateur reçoit un des messages suivants quand il tente de se connecter :
  - Si l’appareil n’est pas inscrit auprès d’Intune ni dans Azure Active Directory, l’utilisateur reçoit un message contenant des instructions pour installer l’application Portail d’entreprise, inscrire l’appareil et activer la messagerie. Ce processus associe également l’ID Exchange ActiveSync de l’appareil à l’enregistrement de l’appareil dans Azure Active Directory.
  - Si l’appareil n’est pas conforme, un message s’affiche et dirige l’utilisateur vers le site web de Portail d’entreprise Intune ou vers l’application Portail d’entreprise. À partir du portail d'entreprise, l’utilisateur trouver des informations sur le problème et la façon d’y remédier.

### <a name="support-for-mobile-devices"></a>Prise en charge des appareils mobiles

- Windows Phone 8.1 et versions ultérieures
- Application de messagerie native sur iOS/iPadOS.
- Clients de messagerie EAS, comme Gmail sur Android 4 ou ultérieur.
- Clients de messagerie EAS sur les **appareils avec profil professionnel Android** : seules les applications **Gmail** et **Nine Work for Android Enterprise** dans le **profil professionnel** sont prises en charge sur les appareils avec profil professionnel Android. Pour que l’accès conditionnel fonctionne avec les profils professionnels Android, vous devez déployer un profil de messagerie pour l’application Gmail ou Nine Work for Android Enterprise, et également déployer ces applications comme installation obligatoire.

> [!NOTE]
> Microsoft Outlook pour Android et iOS/iPadOS n’est pas pris en charge via le connecteur local Exchange. Si vous voulez tirer parti des stratégies d’accès conditionnel d’Azure Active Directory et des stratégies Intune App Protection avec Outlook pour iOS/iPadOS et Android pour vos boîtes aux lettres locales, consultez [Utilisation de l’authentification hybride moderne avec Outlook pour iOS/iPadOS et Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

### <a name="support-for-pcs"></a>Prise en charge des PC

L'application native **Courrier** sur Windows 8.1 et les versions ultérieures (en cas d’inscription dans MDM auprès d'Intune)

## <a name="configure-exchange-on-premises-access"></a>Configuration de l'accès à Exchange sur site

Avant de pouvoir utiliser la procédure suivante pour configurer le contrôle d’accès Exchange sur site, vous devez installer et configurer au moins un [Connecteur Exchange local Intune](exchange-connector-install.md) pour Exchange sur site.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Accédez à **Administration de locataire** > **Accès à Exchange**, puis sélectionnez **Accès à Exchange local**.

3. Dans le volet **Accès à Exchange sur site**, choisissez **Oui** pour *Activer le contrôle d’accès à Exchange sur site*.

   > [!div class="mx-imgBorder"]
   > ![Exemple de capture d’écran Accès à Exchange local](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. Sous **Affectation**, choisissez **Sélectionner les groupes à inclure**, puis sélectionnez un ou plusieurs groupes pour configurer l’accès.

   Les membres des groupes que vous sélectionnez disposent d’une stratégie d’accès conditionnel pour l’accès à Exchange sur site. Les utilisateurs qui reçoivent cette stratégie doivent inscrire leurs appareils dans Intune et être conformes aux profils de conformité avant de pouvoir accéder à Exchange sur site.

   > [!div class="mx-imgBorder"]
   > ![Sélectionner les groupes à inclure](./media/conditional-access-exchange-create/select-groups.png)

5. Pour exclure des groupes, choisissez **Sélectionner les groupes à exclure**, puis sélectionnez un ou plusieurs groupes exempts des conditions pour inscrire des appareils et être conformes aux profils de conformité avant d’accéder à Exchange sur site.

   Sélectionnez **Enregistrer** pour enregistrer votre configuration et revenir au volet **Accès à Exchange**.

6. Ensuite, configurez les paramètres du connecteur Exchange local Intune. Dans la console, sélectionnez **Administration de locataire** > **Accès à Exchange**> **Connecteur local Exchange ActiveSync**, puis choisissez le connecteur de l’organisation Exchange que vous souhaitez configurer.

7. Pour **Notifications à l’utilisateur**, sélectionnez **Modifier** afin d’ouvrir le workflow **Modifier l’organisation** où vous pouvez modifier le message de *notification à l’utilisateur*.

   > [!div class="mx-imgBorder"]
   > ![Exemple de capture d’écran du workflow Modifier l’organisation pour les notifications](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   Modifiez l’e-mail par défaut envoyé aux utilisateurs si leur appareil n’est pas conforme et qu’ils veulent accéder à Exchange sur site. Le modèle de message utilise le langage de balisage. Vous voyez également un aperçu du message en cours de frappe

   Sélectionnez **Vérifier + enregistrer** puis **Enregistrer** pour enregistrer vos modifications afin de terminer la configuration de l’accès local à Exchange.

   > [!TIP]
   > Pour en savoir plus sur le langage de balisage, consultez cet [article](https://en.wikipedia.org/wiki/Markup_language) Wikipedia.

8. Ensuite, sélectionnez **Paramètres d’accès avancés Exchange ActiveSync** pour ouvrir le workflow *Paramètres d’accès avancés Exchange ActiveSync* dans lequel vous configurez les règles d’accès aux appareils.

   > [!div class="mx-imgBorder"]
   > ![Exemple de capture d’écran du workflow Modifier l’organisation pour les paramètres avancés](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - Pour **Accès aux appareils non gérés**, définissez la règle globale par défaut pour l’accès à partir d’appareils qui ne sont pas affectés par l’accès conditionnel ou d’autres règles :

     - **Autoriser l’accès** : tous les appareils peuvent accéder immédiatement à Exchange sur site. Les appareils qui appartiennent aux utilisateurs des groupes que vous avez configurés comme inclus dans la procédure précédente sont bloqués s’ils sont évalués ultérieurement comme non conformes aux stratégies conformes ou qu’ils ne sont pas inscrits dans Intune.

     - **Bloquer l'accès** et **Quarantaine** : l’accès initial pour tous les appareils à Exchange sur site est immédiatement bloqué. Les appareils qui appartiennent à des utilisateurs dans les groupes que vous avez configurés comme inclus dans la procédure précédente obtiennent un accès après inscription dans Intune et sont évalués comme étant conformes.

       Les appareils Android qui n’exécutent pas Samsung Knox standard sont toujours bloqués, car ils *ne prennent pas en charge* ce paramètre.

   - Pour **Exceptions de la plateforme d’appareils**, sélectionnez **Ajouter**, puis spécifiez les détails en fonction des besoins de votre environnement.

      Si le paramètre **Accès aux appareils non gérés** est défini sur **Bloqué**, les appareils qui sont inscrits et conformes sont autorisés, même s’il existe une exception de plateforme qui les bloque.  

9. Sélectionnez **OK** pour enregistrer vos modifications.

10. Sélectionnez **Vérifier + enregistrer** puis **Enregistrer** pour enregistrer la stratégie d’accès conditionnel Exchange.

## <a name="next-steps"></a>Étapes suivantes

Ensuite, créez une stratégie de conformité et affectez-la aux utilisateurs pour qu’Intune évalue leurs appareils mobiles. Voir [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

[Résolution des problèmes du connecteur Exchange local Intune dans Microsoft Intune](https://support.microsoft.com/help/4471887)
