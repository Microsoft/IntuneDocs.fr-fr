---
title: Utiliser Microsoft Defender ATP dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) avec Intune, y compris l’installation et la configuration, l’intégration de vos périphériques Intune avec ATP, puis l’évaluation des risques de l’ATP des périphériques avec la conformité de votre appareil Intune et l’application de l’accès conditionnel pour protéger les ressources réseau.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fa80697f24167e2a9634bd506e9548ca654129f
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547096"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Appliquer la conformité pour Microsoft Defender ATP avec accès conditionnel dans Intune

Vous pouvez intégrer Microsoft Defender – Protection avancée contre les menaces (Microsoft Defender – PACM) avec Microsoft Intune sous la forme d’une solution Mobile Threat Defense, afin d’empêcher les violations de la sécurité et de limiter leur impact au sein d’une organisation. Microsoft Defender ATP fonctionne avec les périphériques qui exécutent Windows 10 ou une version ultérieure.

Pour réussir, vous utilisez les configurations suivantes de concert :

- **Établir une connexion de service à service entre Intune et Microsoft Defender ATP**. Cette connexion permet à Microsoft Defender ATP de collecter des données sur les risques machine d’ordinateurs Windows 10 que vous gérez avec Intune.
- **Utilisez un profil de configuration d’appareil pour intégrer des périphériques avec Microsoft Defender ATP**. Vous configurez des périphériques intégrés pour qu’ils communiquent avec Microsoft Defender ATP et pour fournir des données qui permettent d’évaluer leur niveau de risque.
- **Utilisez une stratégie de conformité d’appareil pour définir le niveau de risque que vous souhaitez autoriser**. Les niveaux de risque sont signalés par Microsoft Defender ATP. Les périphériques qui dépassent le niveau de risque autorisé sont identifiés comme non conformes.
- **Utilisez une stratégie d’accès conditionnel** pour empêcher les utilisateurs d’accéder aux ressources de l’entreprise à partir de périphériques qui ne sont pas conformes.

En intégrant Intune à Microsoft Defender – PACM, vous pouvez tirer parti de sa Gestion des menaces et des vulnérabilités (TVM) et [utiliser Intune pour corriger les faiblesses de points de terminaison identifiées par TVM](atp-manage-vulnerabilities.md).

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Exemple d’utilisation de Microsoft Defender ATP avec Intune

L’exemple suivant explique comment ces solutions fonctionnent ensemble pour aider à protéger votre organisation. Pour cet exemple, Microsoft Defender ATP et Intune sont déjà intégrés.

Prenons l’exemple d’un événement dans lequel une personne envoie une pièce jointe Word incorporant du code malveillant à un utilisateur de votre organisation.

- L’utilisateur ouvre la pièce jointe et active le contenu.
- C’est le début d’une attaque avec privilèges élevés. Un attaquant qui se trouve sur un ordinateur distant dispose alors de droits d’administrateur sur l’appareil de la victime.
- L’attaquant accède ensuite à distance aux autres appareils de l’utilisateur. Cette violation de la sécurité peut impacter toute l’organisation.

Microsoft Defender ATP peut résoudre les événements de sécurité comme ceux décrits dans ce scénario.

- Dans notre exemple, Microsoft Defender ATP détecte que l’appareil a exécuté du code anormal, qu’il a subi une élévation de privilèges de processus, qu’il a injecté du code malveillant et qu’il a émis un interpréteur de commandes distant suspect.
- Sur la base de ces actions à partir de l’appareil, Microsoft Defender ATP [classe l’appareil comme étant à haut risque](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity) et comprend un rapport détaillé d’activité suspecte dans le portail de Security Center Microsoft Defender.

Étant donné que vous avez une stratégie de conformité des périphériques Intune pour classifier les périphériques avec un niveau de risque *Moyen* ou *Élevé* comme non conforme, l’appareil compromis est considéré comme non conforme. Cette classification permet à votre stratégie d’accès conditionnel de démarrer et de bloquer l’accès à vos ressources d’entreprise à partir de cet appareil.

## <a name="prerequisites"></a>Prérequis

Pour utiliser Microsoft Defender ATP avec Intune, les éléments suivants doivent être configurés et opérationnels :

- Locataire sous licence pour Enterprise Mobility + Security E3 et Windows E5 (ou Microsoft 365 Entreprise E5)
- Environnement Microsoft Intune, avec des appareils Windows 10 [gérés par Intune](../enrollment/windows-enroll.md) et joints à Azure AD
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) et accès au Centre de sécurité Microsoft Defender (portail ATP)

> [!NOTE]
> Microsoft Defender ATP n’est pas pris en charge avec les stratégies de protection d’applications iOS et Android Intune.

## <a name="enable-microsoft-defender-atp-in-intune"></a>Activer Microsoft Defender ATP dans Intune

La première étape consiste à configurer la connexion de service à service entre Intune et Microsoft Defender ATP. Cela nécessite un accès administratif à la Security Center Microsoft Defender et à Intune.

### <a name="to-enable-defender-atp"></a>Pour activer Defender ATP

Il n’est nécessaire d’activer Defender – PACM qu’une seule fois par locataire.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Sécurité des points de terminaison** > **Microsoft Defender – PACM**, puis **Ouvrir le Centre de sécurité Microsoft Defender**.

   ![Sélectionner l’option pour ouvrir le Centre de sécurité Microsoft Defender](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. Dans **Centre de sécurité Microsoft Defender** :
    1. Sélectionnez **Paramètres** > **Fonctionnalités avancées**.
    2. Pour **Connexion Microsoft Intune**, choisissez **Activé** :

        ![Activer la connexion à Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Sélectionnez **Enregistrer les préférences**.

4. Revenez à **Microsoft Defender – PACM** dans le Centre d’administration du Gestionnaire de points de terminaison Microsoft. Sous **Paramètres de la stratégie de conformité MDM**, définissez **Connecter les appareils Windows 10.0.15063 et versions ultérieures à Microsoft Defender – PACM** sur **Activé**.

5. Sélectionnez **Enregistrer**.

> [!TIP]
> Quand vous intégrez une nouvelle application à Intune Mobile Threat Defense et que vous activez la connexion à Intune, Intune crée une stratégie d’accès conditionnel classique dans Azure Active Directory. Chaque application MTD que vous intégrez, notamment [Defender ATP](advanced-threat-protection.md) ou un de nos autres [partenaires MTD](mobile-threat-defense.md#mobile-threat-defense-partners), crée une stratégie d’accès conditionnel classique. Ces stratégies peuvent être ignorées, mais elles ne doivent pas être modifiées, supprimées ou désactivées.
>
> Si la stratégie classique est supprimée, vous devrez supprimer la connexion à Intune qui était responsable de sa création, puis la configurer à nouveau. Ceci recrée la stratégie classique. Il n’est pas possible de migrer des stratégies classiques pour les applications MTD vers le nouveau type de stratégie pour l’accès conditionnel.
>
> Les stratégies d’accès conditionnel classiques pour les applications MTD :
>
> - Sont utilisées par Intune MTD pour exiger que les appareils soient inscrits dans Azure AD afin qu’ils aient un ID d’appareil avant de communiquer avec des partenaires MTD. L’ID est nécessaire pour que les appareils puissent signaler leur état à Intune.
> - Aucun effet sur les autres ressources ou applications cloud.
> - Sont distinctes des stratégies d’accès conditionnel que vous pouvez créer pour faciliter la gestion de MTD.
> - Par défaut, n’interagissez pas avec les autres stratégies d’accès conditionnel que vous utilisez pour l’évaluation.
>
> Pour afficher les stratégies d’accès conditionnel classiques, dans [Azure](https://portal.azure.com/#home), accédez à **Azure Active Directory** > **Accès conditionnel** > **Stratégies classiques**.

## <a name="onboard-devices-by-using-a-configuration-profile"></a>Intégrer des périphériques à l’aide d’un profil de configuration

Une fois que vous avez établi la connexion de service à service entre Intune et Microsoft Defender ATP, vous intégrez vos appareils gérés par Intune à ATP afin que les données relatives à leur niveau de risque puissent être collectées et utilisées. Utilisez un profil de configuration d’appareil pour intégrer des périphériques avec Microsoft Defender ATP.

Lorsque vous avez établi la connexion à Microsoft Defender ATP, Intune a reçu un package de configuration d’intégration Microsoft Defender ATP de Microsoft Defender ATP. Ce package est déployé sur des périphériques avec le profil de configuration de l’appareil. Le package de configuration configure des périphériques qui communiquent avec les [services Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser les fichiers, détecter les menaces et signaler le niveau de risque à Microsoft Defender ATP. Si vous avez intégré un appareil à l’aide du package de configuration, vous n’avez pas besoin de le refaire. Vous pouvez également intégrer les appareils à l’aide d’une [stratégie de groupe ou de Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="create-the-device-configuration-profile"></a>Créer un profil de configuration d’appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez un **Nom** et une **Description**.
4. Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
5. Pour **Type de profil**, sélectionnez **Microsoft Defender ATP (Windows 10 Desktop)** .
6. Configurez les paramètres :

   - **Type de package de configuration des clients Microsoft Defender ATP** : Sélectionnez **Intégrer** pour ajouter le package de configuration au profil. Sélectionnez **Désintégrer** pour supprimer le package de configuration du profil.
  
     > [!NOTE]
     > Si vous avez correctement établi une connexion avec Microsoft Defender ATP, Intune **intègre** automatiquement le profil de configuration, et le paramètre **Type de package de configuration des clients Microsoft Defender ATP** n’est alors pas disponible.
  
   - **Partage d’exemples pour tous les fichiers** : Si ce paramètre est **activé**, permet de collecter des exemples et de les partager avec Microsoft Defender ATP. Par exemple, si vous constatez la présence d’un fichier suspect, vous pouvez le soumettre à Microsoft Defender ATP pour effectuer une analyse approfondie. **Non configuré** ne partage pas les exemples avec Microsoft Defender ATP.
   - **Augmenter la fréquence des rapports de télémétrie** : si vous avez des appareils à haut risque, **activez** ce paramètre pour qu’ils envoient des données de télémétrie au service Microsoft Defender ATP plus fréquemment.

     [Intégrer des ordinateurs Windows 10 à l’aide de Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) offre plus de détails sur ces paramètres Microsoft Defender ATP.

7. Sélectionnez **OK**, puis **Créer** pour enregistrer vos changements et créer le profil.
8. [Utilisez un profil de configuration d’appareil](../configuration/device-profile-assign.md) pour des périphériques que vous souhaitez évaluer avec Microsoft Defender ATP.

## <a name="create-and-assign-the-compliance-policy"></a>Créer et affecter la stratégie de conformité

La stratégie de conformité détermine le niveau de risque que vous considérez comme acceptable pour un appareil.

### <a name="create-the-compliance-policy"></a>Créer la stratégie de conformité

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Stratégies de conformité** > **Créer une stratégie**.
3. Entrez un **Nom** et une **Description**.
4. Dans **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
5. Sous **Paramètres**, sélectionnez **Microsoft Defender ATP**.
6. Définissez **Exiger que l’appareil se situe au niveau du score de risque machine ou en dessous** sur le niveau de votre choix.

   Les classifications des niveaux de menace sont [déterminées par Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Sans risque** : ce niveau est le plus sûr. Si l’appareil fait l’objet de menaces, il ne peut pas accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme. (Microsoft Defender ATP utilise la valeur *Sécurisé*.)
   - **Faible** : l’appareil est conforme uniquement si les menaces détectées sont de niveau faible. Les appareils avec des niveaux de menace moyen ou élevé ne sont pas conformes.
   - **Moyenne** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.
   - **Élevée** : ce niveau est le moins sûr et permet tous les niveaux de menace. Les appareils dont le niveau de menace est élevé, moyen ou faible sont donc considérés comme conformes.

7. Sélectionnez **OK**, puis **Créer** pour enregistrer vos changements et créer la stratégie.
8. [Attribuez la stratégie de conformité de l’appareil](create-compliance-policy.md#assign-the-policy) aux groupes applicables.

## <a name="create-a-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel

La stratégie d’accès conditionnel bloque l’accès aux ressources des appareils qui dépassent le niveau de menace que vous définissez dans votre stratégie de conformité. Vous pouvez bloquer l’accès aux ressources d’entreprise à partir d’un appareil (comme SharePoint ou Exchange Online).

> [!TIP]
> L’accès conditionnel est une technologie Azure Active Directory (Azure AD). Le nœud Accès conditionnel accessible à partir du Centre d’administration du Gestionnaire de points de terminaison Microsoft est le même que celui qui est accessible à partir *d’Azure AD*.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Sécurité des points de terminaison** > **Accès conditionnel** > **Nouvelle stratégie**.

3. Entrez un **Nom** de stratégie, puis sélectionnez **Utilisateurs et groupes**. Utilisez les options Inclure et Exclure pour ajouter vos groupes à la stratégie, puis sélectionnez **Terminé**.

4. Sélectionnez **Applications cloud**, puis choisissez les applications à protéger. Par exemple, choisissez **Sélectionner les applications**, puis sélectionnez **Office 365 SharePoint Online** et **Office 365 Exchange Online**.

   Sélectionnez **Terminé** pour enregistrer vos changements.

5. Sélectionnez **Conditions** > **Applications clientes** pour appliquer la stratégie aux applications et aux navigateurs. Par exemple, sélectionnez **Oui**, puis activez **Navigateur** et **Applications mobiles et clients de bureau**.

   Sélectionnez **Terminé** pour enregistrer vos changements.

6. Sélectionnez **Accorder** pour appliquer l’accès conditionnel basé sur la conformité des appareils. Par exemple, sélectionnez **Accorder l’accès** > **Exiger que l’appareil soit marqué comme conforme**.

    Choisissez **Sélectionner** pour enregistrer vos changements.

7. Sélectionnez **Activer la stratégie**, puis **Créer** pour enregistrer vos changements.

## <a name="monitor-device-compliance"></a>Surveiller la conformité des appareils

Ensuite, monitorez l’état des appareils qui ont la stratégie de conformité Microsoft Defender ATP.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Monitorage** > **Conformité aux stratégies**.

3. Recherchez votre stratégie Microsoft Defender ATP dans la liste, et identifiez les appareils qui sont conformes ou non.

Vous pouvez également utiliser le rapport *opérationnel* pour les appareils non conformes à partir du même emplacement :

1. Sélectionnez **Appareils** > **Surveiller** > **Appareils non conformes**.

Pour plus d’informations sur les rapports, consultez [Rapports Intune](../fundamentals/reports.md).

## <a name="view-onboarding-status"></a>Afficher l’état de l'intégration

Pour afficher l’état de l’intégration de tous les appareils Windows 10 managés par Intune, vous pouvez accéder à **Conformité des appareils** > **Microsoft Defender ATP**. À partir de cette page, vous pouvez également lancer la création d’un profil de configuration d’appareil pour l’intégration d’un plus grand nombre d’appareils à Microsoft Defender ATP.

## <a name="next-steps"></a>Étapes suivantes

[Accès conditionnel dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)

[Tableau de bord des risques de Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)

[Utilisez les tâches de sécurité avec lesquels Vulnerability Management d’ATP corrige les problèmes sur les appareils](atp-manage-vulnerabilities.md).

[Bien démarrer avec les stratégies de conformité des appareils](device-compliance-get-started.md)
