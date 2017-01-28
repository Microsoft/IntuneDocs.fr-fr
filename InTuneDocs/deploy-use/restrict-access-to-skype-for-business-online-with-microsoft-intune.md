---
title: "Protéger l’accès à Skype Entreprise Online | Microsoft Docs"
description: "Protégez et contrôlez l’accès à Skype Entreprise Online en utilisant l’accès conditionnel."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1b2d7125-f63f-43cf-ac1e-94fbedf2a7e8
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f34d54710f0ec662eecec85f7fa041061132a0d
ms.openlocfilehash: 37915fcfc0f10e65aa65d400422d72adc63513fa


---

# <a name="protect-access-to-skype-for-business-online-with-microsoft-intune"></a>Protéger l’accès à Skype Entreprise Online avec Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Vous pouvez utiliser une stratégie d’accès conditionnel à **Skype Entreprise Online** pour contrôler l’accès à Skype Entreprise Online.
L’accès conditionnel comprend deux composants :
- Une stratégie de conformité des appareils que l’appareil doit respecter pour être considéré comme conforme.
- Une stratégie d’accès conditionnel dans laquelle vous spécifiez les conditions que l’appareil doit remplir pour que vous puissiez accéder au service.
Pour en savoir plus sur le fonctionnement de l’accès conditionnel, lisez l’article [Protéger l’accès à la messagerie et aux services O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Lorsqu’un utilisateur ciblé tente d’utiliser Skype Entreprise Online sur son appareil, l’évaluation suivante se produit :

![Diagramme illustrant les points de décision utilisés pour déterminer si un appareil est autorisé ou non à accéder à Skype Entreprise Online](../media/ConditionalAccess_SkypeforBusiness.png)

**Avant** de configurer une stratégie d’accès conditionnel à Skype Entreprise Online, vous devez :
- Disposer d’un **abonnement Skype Entreprise Online** et affecter une licence Skype Entreprise Online aux utilisateurs.
- Avoir un **abonnement Enterprise Mobility + Security (EMS)** ou un **abonnement Azure Active Directory (Azure AD) Premium**, et les utilisateurs doivent disposer d’une licence EMS ou Azure AD. Pour plus d’informations, consultez [Tarification d’Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) ou [Tarification d’Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).

-   [Authentification moderne activée](https://docs.microsoft.com/en-us/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) pour Skype Entreprise Online.
-  Faire en sorte que tous vos utilisateurs utilisent **Skype Entreprise Online**. Si votre déploiement comprend à la fois Skype Entreprise Online et Skype Entreprise local, la stratégie d’accès conditionnel n’est pas appliquée aux utilisateurs.

Pour accéder à Skype Entreprise Online, un appareil doit être :

-   Un appareil **Android** ou **iOS**.

-   **Inscrit** auprès de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   **Conforme** à toutes les stratégies de conformité [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] déployées.


L’état de l’appareil est stocké dans Azure Active Directory, qui autorise ou bloque l’accès en fonction des conditions que vous spécifiez.

Si une condition n’est pas remplie, l’utilisateur reçoit l’un des messages suivants quand il tente de se connecter :

-   Si l’appareil n’est pas inscrit auprès d’[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] ou qu’il n’est pas inscrit dans Azure Active Directory, l’utilisateur reçoit un message contenant des instructions pour installer l’application Portail d’entreprise et inscrire l’appareil.

-   Si l’appareil n’est pas conforme, l’utilisateur reçoit un message le dirigeant vers l’application ou le site web du portail d’entreprise [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], où il peut trouver des informations sur le problème et des solutions pour le résoudre.

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Configurer l’accès conditionnel à Skype Entreprise Online

### <a name="step-1-configure-azure-active-directory-security-groups"></a>Étape 1 : configurer les groupes de sécurité Azure Active Directory
Avant de commencer, configurez les groupes de sécurité Azure Active Directory pour la stratégie d'accès conditionnel. Vous pouvez configurer ces groupes dans le **Centre d’administration Office 365**. Ces groupes seront utilisés pour cibler ou exempter les utilisateurs de la stratégie. Quand un utilisateur est ciblé par la stratégie, chaque appareil qu’il utilise doit être conforme à cette stratégie pour qu’il puisse accéder aux ressources.

Vous pouvez spécifier deux types de groupes que la stratégie Skype Entreprise pourra utiliser :

-   **Groupes ciblés** : contient les groupes d’utilisateurs auxquels la stratégie s’applique.

-   **Groupes exemptés** : contient les groupes d’utilisateurs exempts de la stratégie.

Si un utilisateur se trouve dans les deux groupes, il est exempt de la stratégie.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Étape 2 : configurer et déployer une stratégie de conformité
[Créez](create-a-device-compliance-policy-in-microsoft-intune.md) et [déployez](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) une stratégie de conformité pour tous les appareils qui seront affectés par la stratégie. Il s’agit de tous les appareils utilisés par les utilisateurs des **Groupes ciblés**.

> [!NOTE]
> Tandis que les stratégies de conformité sont déployées sur les groupes [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], les stratégies d’accès conditionnel sont destinées aux groupes de sécurité Azure Active Directory.


> [!IMPORTANT]
> Si vous n’avez pas déployé de stratégie de conformité, les appareils seront traités comme étant conformes.

Quand vous êtes prêt, passez à l’**Étape 3**.

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Étape 3: Configurer la stratégie Skype Entreprise Online
Ensuite, configurez la stratégie de manière à restreindre l’accès à Skype Entreprise Online aux appareils gérés et conformes. Cette stratégie sera stockée dans Azure Active Directory.

1.  Dans la [Console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **Stratégie** > **Accès conditionnel** > **Stratégie Skype Entreprise Online**.

  ![Capture d’écran de la page de stratégie d’accès conditionnel à Skype Entreprise Online](./media/conditional_access_SFBPolicy.png)

2.  Choisissez **Activer la stratégie d’accès conditionnel**.

3.  Sous **Accès aux applications**, vous pouvez choisir d’appliquer la stratégie d’accès conditionnel à :

    -   **iOS**

    -   **Android**

4.  Sous **Groupes ciblés**, choisissez **Modifier** pour sélectionner les groupes de sécurité Azure Active Directory auxquels la stratégie sera appliquée. Vous pouvez cibler cette stratégie sur tous les utilisateurs ou seulement sur un groupe d’utilisateurs donné.

5.  Sous **Groupes exemptés**, vous pouvez éventuellement choisir **Modifier** pour sélectionner les groupes de sécurité Azure Active Directory exempts de cette stratégie.

6.  Quand vous avez terminé, choisissez **Enregistrer**.

Vous avez maintenant configuré l’accès conditionnel à Skype Entreprise Online. La stratégie d’accès conditionnel prend effet immédiatement. Il est donc inutile de la déployer.


## <a name="monitor-the-compliance-and-conditional-access-policies"></a>analyser la conformité et les stratégies d'accès conditionnel
Dans l'espace de travail **Groupes** , vous pouvez afficher l'état de l'accès conditionnel de vos appareils.

Sélectionnez un groupe d’appareils mobiles. Ensuite, sous l’onglet **Appareils**, choisissez l’un des **Filtres** suivants :

* **Appareils non enregistrés avec AAD** : l’accès à Skype Entreprise Online est bloqué pour ces appareils.

* **Appareils non conformes** : l’accès à Skype Entreprise Online est bloqué pour ces appareils.

* **Appareils enregistrés avec AAD et conformes** : ces appareils peuvent accéder à Skype Entreprise Online.



<!--HONumber=Jan17_HO1-->


