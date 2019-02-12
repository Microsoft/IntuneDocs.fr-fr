---
title: Utiliser Windows Defender ATP dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez comment activer Windows Defender Advanced Threat Protection (ATP) dans un scénario de bout en bout. Cet article décrit notamment comment activer ATP dans Intune et dans le Centre de sécurité Windows Defender (portail ATP), intégrer des appareils à l’aide d’un profil de configuration ATP, créer une stratégie de conformité des appareils Intune, créer une stratégie d’accès conditionnel Azure AD et monitorer la conformité des appareils.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 1/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afa2ef4cf1199597f61af99d631243e2d3b51e64
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845174"
---
# <a name="enforce-compliance-for-windows-defender-atp-with-conditional-access-in-intune"></a>Appliquer la conformité pour Windows Defender ATP avec accès conditionnel dans Intune

Windows Defender Advanced Threat Protection (ATP) et Microsoft Intune fonctionnent de concert pour empêcher les violations de la sécurité et limiter leur impact au sein d’une organisation.

Cette fonctionnalité s’applique à : Appareils Windows 10

Prenons l’exemple d’une personne qui envoie une pièce jointe Word incorporant du code malveillant à un utilisateur de votre organisation. L’utilisateur ouvre la pièce jointe et active le contenu. C’est le début d’une attaque avec privilèges élevés. Un attaquant qui se trouve sur un ordinateur distant dispose alors de droits d’administrateur sur l’appareil de la victime. L’attaquant accède ensuite à distance aux autres appareils de l’utilisateur.

Cette violation de la sécurité peut impacter toute l’organisation.

Windows Defender ATP peut résoudre les événements de sécurité comme ceux décrits dans ce scénario. Le Centre de sécurité Windows Defender (console ATP) signale les appareils comme présentant un « risque élevé » et inclut un rapport détaillé de l’activité suspecte. Dans notre exemple, Windows Defender ATP détecte que l’appareil a exécuté du code anormal, qu’il a subi une élévation de privilèges de processus, qu’il a injecté du code malveillant et qu’il a émis un interpréteur de commandes distant suspect. Windows Defender ATP vous donne ensuite des options pour atténuer la menace.

À l’aide d’Intune, vous pouvez créer une stratégie de conformité qui détermine un niveau de risque acceptable. Si un appareil dépasse ce risque, il devient non conforme. Si vous utilisez conjointement l’accès conditionnel Azure Active Directory (AD), l’utilisateur ne peut pas accéder aux ressources d’entreprise.

Cet article vous montre comment :

- Activer Intune dans ATP, et activer ATP dans Intune. Ces tâches créent une connexion de service à service entre Intune et Windows Defender ATP. Cette connexion permet à Windows Defender ATP d’écrire le risque ordinateur pour vos appareils Intune.
- Créer la stratégie de conformité dans Intune.
- Activer l’accès conditionnel dans Azure Active Directory (AD) sur les appareils en fonction de leur niveau de menace.

## <a name="prerequisites"></a>Prérequis

Pour utiliser ATP avec Intune, les éléments suivants doivent être configurés et opérationnels :

- Locataire sous licence pour Enterprise Mobility + Security E3 et Windows E5 (ou Microsoft 365 Entreprise E5)
- Environnement Microsoft Intune, avec des appareils Windows 10 [gérés par Intune](windows-enroll.md) et joints à Azure AD
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) et accès au Centre de sécurité Windows Defender (portail ATP)

## <a name="enable-windows-defender-atp-in-intune"></a>Activer Windows Defender ATP dans Intune

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Conformité de l’appareil** > **Windows Defender ATP** > **Ouvrir le Centre de sécurité Windows Defender**.

    ![Sélectionner l’option pour ouvrir le Centre de sécurité Windows Defender](./media/atp-device-compliance-open-windows-defender.png)

4. Dans le **Centre de sécurité Windows Defender** :
    1. Sélectionnez **Paramètres** > **Fonctionnalités avancées**.
    2. Pour **Connexion Microsoft Intune**, choisissez **Activé** :

        ![Activer la connexion à Intune](./media/atp-security-center-intune-toggle.png)

    3. Sélectionnez **Enregistrer les préférences**.

5. Revenez à Intune, **Conformité de l’appareil** > **Windows Defender ATP**. Définissez **Connecter les appareils Windows versions 10.0.15063 et ultérieures à Windows Defender ATP** sur **Activé**.
6. Sélectionnez **Enregistrer**.

En général, cette tâche ne doit être effectuée qu’une seule fois. Si ATP est déjà activé dans votre ressource Intune, il est donc inutile de la répéter.

## <a name="onboard-devices-using-a-configuration-profile"></a>Intégrer des appareils à l’aide d’un profil de configuration

Quand un utilisateur final s’inscrit dans Intune, vous pouvez envoyer des paramètres différents à l’appareil en utilisant un profil de configuration. Ceci s’applique également à Windows Defender ATP.

Windows Defender inclut un package de configuration intégré qui communique avec les [services Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) pour analyser les fichiers, détecter les menaces et signaler le niveau de risque à Windows Defender ATP.

Quand vous faites l’intégration, Intune obtient un package de configuration généré automatiquement auprès de Windows Defender ATP. Quand le profil est envoyé ou déployé sur l’appareil, ce package de configuration est également envoyé à l’appareil. Ceci permet à Windows Defender ATP de surveiller les éventuelles menaces sur l’appareil.

Si vous avez intégré un appareil à l’aide du package de configuration, vous n’avez pas besoin de le refaire. Vous pouvez également intégrer les appareils [à l’aide d’une stratégie de groupe ou de SCCM (System Center Configuration Manager)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

### <a name="create-the-configuration-profile"></a>Créer le profil de configuration

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez un **Nom** et une **Description**.
4. Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
5. Pour **Type de profil**, sélectionnez **Windows Defender ATP (Windows 10 Desktop)**.
6. Configurez les paramètres :

  - **Type de package de configuration des clients Windows Defender ATP** : Sélectionnez **Intégrer** pour ajouter le package de configuration au profil. Sélectionnez **Désintégrer** pour supprimer le package de configuration du profil.
  
    > [!NOTE] 
    > Si vous avez correctement établi une connexion avec Windows Defender ATP, Intune **intègre** automatiquement le profil de configuration, et le paramètre **Type de package de configuration des clients Windows Defender ATP** n’est alors pas disponible.
  
  - **Partage d’exemples pour tous les fichiers** : Si ce paramètre est **activé**, permet de collecter des exemples et de les partager avec Windows Defender ATP. Par exemple, si vous constatez la présence d’un fichier suspect, vous pouvez le soumettre à Windows Defender ATP pour effectuer une analyse approfondie. **Non configuré** ne partage pas les exemples avec Windows Defender ATP.
  - **Augmenter la fréquence des rapports de télémétrie** : si vous avez des appareils à haut risque, **activez** ce paramètre pour qu’ils envoient des données de télémétrie au service Windows Defender ATP plus fréquemment.

    [Intégrer des ordinateurs Windows 10 à l’aide de System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) offre plus de détails sur ces paramètres Windows Defender ATP.

7. Sélectionnez **OK**, puis **Créer** pour enregistrer vos changements et créer le profil.

## <a name="create-the-compliance-policy"></a>Créer la stratégie de conformité
La stratégie de conformité détermine un niveau acceptable de risque sur un appareil.

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**.
3. Entrez un **Nom** et une **Description**.
4. Dans **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
5. Dans les paramètres **Windows Defender ATP**, définissez **Exiger que l’appareil se situe au niveau du score de risque machine ou en dessous** sur le niveau de votre choix :

  - **Sans risque** : ce niveau est le plus sûr. Si l’appareil fait l’objet de menaces, il ne peut pas accéder aux ressources de l’entreprise. Si des menaces sont détectées, l’appareil est évalué comme non conforme.
  - **Faible** : l’appareil est conforme uniquement si les menaces détectées sont de niveau faible. Les appareils avec des niveaux de menace moyen ou élevé ne sont pas conformes.
  - **Moyen** : l’appareil est conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées, l’appareil est considéré comme non conforme.
  - **Élevé** : ce niveau est le moins sûr et permet tous les niveaux de menace. Les appareils dont le niveau de menace est élevé, moyen ou faible sont donc considérés comme conformes.

6. Sélectionnez **OK**, puis **Créer** pour enregistrer vos changements et créer la stratégie.

## <a name="assign-the-policy"></a>Affecter la stratégie

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Conformité de l’appareil** > **Stratégies**> sélectionnez votre stratégie de conformité Windows Defender ATP.
3. Sélectionnez **Affectations**.
4. Incluez ou excluez vos groupes Azure AD pour leur affecter la stratégie.
5. Pour déployer la stratégie sur les groupes, sélectionnez **Enregistrer**. La conformité des appareils ciblés par la stratégie est évaluée.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel Azure AD
La stratégie d’accès conditionnel bloque l’accès aux ressources *si* l’appareil n’est pas conforme. Si un appareil dépasse le niveau de menace, vous pouvez donc bloquer l’accès aux ressources d’entreprise (comme SharePoint ou Exchange Online).

1. Dans le [Portail Azure](https://portal.azure.com), ouvrez **Azure Active Directory** > **Accès conditionnel** > **Nouvelle stratégie**.
2. Entrez un **Nom** de stratégie, puis sélectionnez **Utilisateurs et groupes**. Utilisez les options Inclure et Exclure pour ajouter vos groupes à la stratégie, puis sélectionnez **Terminé**.
3. Sélectionnez **Applications cloud**, puis choisissez les applications à protéger. Par exemple, choisissez **Sélectionner les applications**, puis sélectionnez **Office 365 SharePoint Online** et **Office 365 Exchange Online**.

    Sélectionnez **Terminé** pour enregistrer vos changements.

4. Sélectionnez **Conditions** > **Applications clientes** pour appliquer la stratégie aux applications et aux navigateurs. Par exemple, sélectionnez **Oui**, puis activez **Navigateur** et **Applications mobiles et clients de bureau**.

    Sélectionnez **Terminé** pour enregistrer vos changements.

5. Sélectionnez **Accorder** pour appliquer l’accès conditionnel basé sur la conformité des appareils. Par exemple, sélectionnez **Accorder l’accès** > **Exiger que l’appareil soit marqué comme conforme**.

    Choisissez **Sélectionner** pour enregistrer vos changements.

6. Sélectionnez **Activer la stratégie**, puis **Créer** pour enregistrer vos changements.

[Qu’est-ce que l’accès conditionnel ?](conditional-access.md) est une bonne ressource.

## <a name="monitor-device-compliance"></a>Surveiller la conformité des appareils
Ensuite, monitorez l’état des appareils qui ont la stratégie de conformité Windows Defender ATP.

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Conformité de l’appareil** > **Conformité à la stratégie**.
3. Recherchez votre stratégie Windows Defender ATP dans la liste, et identifiez les appareils qui sont conformes ou non.

## <a name="more-good-stuff"></a>Autres informations utiles
[Accès conditionnel dans Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Tableau de bord des risques de Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Bien démarrer avec les stratégies de conformité des appareils](device-compliance-get-started.md)  
[Accès conditionnel dans Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
