---
title: Scénarios d’accès conditionnel
titleSuffix: Microsoft Intune
description: Découvrez comment l’accès conditionnel Intune est couramment utilisé pour l’accès conditionnel basé sur l’application et sur l’appareil.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d30749a7eaa3d516bef2f2acff3e010d69db1c0e
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547056"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Quelles sont les utilisations courantes de l’accès conditionnel avec Intune ?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Il existe deux types d’accès conditionnel avec Intune : l’accès conditionnel basé sur l’appareil et l’accès conditionnel basé sur l’application. Vous devez configurer les stratégies de conformité associées pour déterminer l’accès conditionnel au niveau de votre organisation. L’accès conditionnel est couramment utilisé pour, par exemple, autoriser ou bloquer l’accès à Exchange, contrôler l’accès au réseau ou intégrer une solution Mobile Threat Defense.
 
Les informations de cet article peuvent vous aider à comprendre comment utiliser les fonctionnalités de conformité des *appareils* mobiles et les fonctionnalités de gestion des *applications* mobiles d’Intune. 

> [!NOTE]
> L’accès conditionnel est une fonctionnalité d’Azure Active Directory fournie avec la licence Azure Active Directory Premium. Intune améliore cette fonctionnalité en ajoutant la conformité des appareils mobiles et la gestion des applications mobiles à la solution. Le nœud d’accès conditionnel accessible à partir d’*Intune* est le même nœud que celui accessible à partir d’*Azure AD*.  

## <a name="device-based-conditional-access"></a>Accès conditionnel basé sur l’appareil

Intune et Azure Active Directory fonctionnent ensemble pour s’assurer que seuls les appareils gérés et compatibles peuvent accéder à la messagerie, aux services Office 365, aux applications SaaS et aux [applications locales](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). En outre, vous pouvez définir une stratégie dans Azure Active Directory pour autoriser uniquement les ordinateurs qui sont joints au domaine, ou les appareils mobiles qui sont inscrits dans Intune pour accéder aux services Office 365.

Intune fournit des fonctionnalités de stratégie de conformité des appareils qui évaluent l’état de conformité des appareils. L’état de conformité est signalé à Azure Active Directory, qui l’utilise pour appliquer la stratégie d’accès conditionnel créée dans Azure Active Directory lorsque l’utilisateur tente d’accéder aux ressources de votre entreprise.

Vous configurez les stratégies d’accès conditionnel basées sur l’appareil pour Exchange Online et les autres produits Office 365 via le [portail Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).  

- Découvrez plus d’informations sur la façon [d’exiger des appareils gérés avec l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices).

- Découvrez plus d’informations sur la [conformité des appareils Intune](device-compliance-get-started.md).

- Découvrez plus d’informations sur les [navigateurs pris en charge avec l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers).

> [!NOTE]
> Sur les appareils Android, quand vous activez l’accès basé sur l’appareil pour SharePoint Online ou l’accès basé sur le navigateur à Exchange Online, les utilisateurs doivent activer l’option **Activer l’accès au navigateur** sur l’appareil inscrit, en effectuant les opérations suivantes :
> 1. Lancez **l’application Portail d’entreprise**.
> 2. Accédez à la page **Paramètres** via les trois points (...) ou le bouton de menu matériel.
> 3. Appuyez sur le bouton **Activer l’accès du navigateur** . 
> 4. Dans le navigateur Chrome, déconnectez-vous d’Office 365 et redémarrez Chrome.

### <a name="conditional-access-based-on-network-access-control"></a>Accès conditionnel basé sur le contrôle d’accès réseau

Intune s’intègre avec des partenaires comme Cisco ISE, Aruba Clear Pass et Citrix NetScaler pour fournir des contrôles d’accès basés sur l’inscription Intune et l’état de conformité de l’appareil.

L’accès par les utilisateurs peut être accepté ou refusé au Wi-Fi ou aux ressources VPN de l’entreprise selon que l’appareil qu’ils utilisent est géré et conforme ou non aux stratégies de conformité d’appareil d’Intune.

- En savoir plus sur l’[intégration du contrôle d’accès réseau avec Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Accès conditionnel basé sur les risques que présente l’appareil

Intune fait équipe avec des fournisseurs de défense contre les menaces mobiles qui proposent une solution de sécurité visant à détecter les programmes malveillants, les chevaux de Troie et d’autres menaces sur les appareils mobiles.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Comment fonctionne l’intégration entre Intune et la défense contre les menaces mobiles ?

Lorsqu’il est installé sur un appareil, l’agent de défense contre les menaces mobiles renvoie des messages d’état de conformité à Intune pour indiquer quand une menace est identifiée sur l’appareil mobile proprement dit.

L’intégration entre Intune et la défense contre les menaces mobiles joue un rôle dans les décisions d’accès conditionnel basé sur les risques posés par les appareils.

- Découvrez-en davantage sur la [défense contre les menaces mobiles](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Accès conditionnel pour les PC Windows

L’accès conditionnel pour PC offre des fonctionnalités similaires à celles des appareils mobiles. Examinons les façons dont vous pouvez utiliser l’accès conditionnel lors de la gestion des PC avec Intune.

#### <a name="corporate-owned"></a>Appartenant à l’entreprise

- **Jonction à un domaine Active Directory local** : Cette option est généralement utilisée par les organisations qui sont déjà habituées à gérer leurs PC avec des stratégies de groupe AD ou Configuration Manager.

- **Jonction à un domaine Azure AD et gestion Intune** : Ce scénario est destiné aux organisations qui souhaitent donner la priorité au cloud (c’est-à-dire, utiliser principalement des services cloud, avec l’objectif de réduire l’utilisation d’une infrastructure locale) ou utiliser uniquement le cloud (aucune infrastructure locale). La jonction Azure AD fonctionne bien dans un environnement hybride, ce qui permet d’accéder à des ressources et des applications cloud et locales. L’appareil est joint à Azure AD et est inscrit auprès d’Intune, qui peut être utilisé comme critère d’accès conditionnel lors de l’accès aux ressources de l’entreprise.

- **Domaine AD joint et Configuration Manager :** En tant que branche actuelle, Configuration Manager fournit des fonctionnalités d’accès conditionnel qui peuvent évaluer des critères de compatibilité spécifiques, en plus d’être un PC joint au domaine :

  - Le PC est-il chiffré ?

  - Une protection contre les programmes malveillants est-elle installée ? Est-il à jour ?

  - L’appareil est-il jailbreaké ou rooté ?

#### <a name="bring-your-own-device-byod"></a>Apportez votre propre appareil (BYOD)

- **Workplace Join et gestion Intune** : ici, l’utilisateur peut joindre ses appareils personnels pour accéder aux ressources et services de l’entreprise. Vous pouvez utiliser le rattachement à l’espace de travail et inscrire des appareils dans Intune MDM pour recevoir des stratégies au niveau de l’appareil, ce qui est également une option pour évaluer les critères d’accès conditionnel.

Découvrez-en davantage sur la [gestion des appareils dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/overview).

## <a name="app-based-conditional-access"></a>Accès conditionnel basé sur l’application

Intune et Azure Active Directory fonctionnent ensemble pour s’assurer que seules les applications gérées peuvent accéder à l’e-mail d’entreprise ou aux autres services Office 365.

- Découvrez-en davantage sur [l’accès conditionnel basé sur l’application avec Intune](app-based-conditional-access-intune.md).

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Accès conditionnel Intune pour Exchange sur site

L’accès conditionnel peut servir à autoriser ou bloquer l’accès à **Exchange en local** en fonction des stratégies de conformité d’appareil et de l’état d’inscription. Quand vous utilisez un accès conditionnel avec une stratégie de conformité d'appareil, seuls les appareils conformes peuvent accéder à Exchange en local.

Vous pouvez configurer des paramètres avancés dans l’accès conditionnel pour un contrôle plus précis, par exemple pour :

- Autoriser ou bloquer certaines plateformes.

- Bloquer immédiatement les appareils qui ne sont pas gérés par Intune.

La conformité de tout appareil utilisé pour accéder à une instance d’Exchange locale est vérifiée lorsque les stratégies d’accès conditionnel et de conformité d’appareil sont appliquées.

Quand un appareil ne remplit pas les conditions définies, l'utilisateur final est guidé tout au long du processus d'inscription de cet appareil pour résoudre le problème qui empêche l'appareil d'être conforme.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Fonctionnement de l’accès conditionnel pour Exchange sur site

L’accès conditionnel pour Exchange sur site fonctionne différemment des stratégies basées sur l’accès conditionnel Azure. Vous installez le connecteur Intune Exchange sur site pour interagir directement avec le serveur Exchange. Le connecteur Intune Exchange extrait tous les enregistrements Exchange Active Sync (EAS) qui existent sur le serveur Exchange. Intune peut ainsi prendre ces enregistrements EAS et les mapper à des enregistrements d’appareils Intune. Ces enregistrements sont les appareils inscrits et reconnus par Intune. Ce processus autorise ou bloque l’accès à la messagerie.

Si l’enregistrement EAS est nouveau et qu’Intune ne le sait pas, Intune émet une cmdlet (prononcer « command-let ») qui indique au serveur Exchange de bloquer l’accès à la messagerie. Voici plus de détails sur le fonctionnement de ce processus :

![Exchange local avec organigramme de l’autorité de certification](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. L’utilisateur essaie d’accéder à une messagerie d’entreprise hébergée sur une instance locale d’Exchange 2010 SP1 (ou une version ultérieure).

2. Si l’appareil n’est pas géré par Intune, son accès à la messagerie est bloqué. Intune envoie une notification de blocage au client EAS.

3. EAS reçoit une notification de blocage, met l’appareil en quarantaine et envoie l’e-mail de mise en quarantaine, qui contient des étapes de résolution et des liens permettant aux utilisateurs d’inscrire leurs appareils.

4. Le processus de jonction d’espace de travail se produit. Il s’agit de la première étape pour que les appareils soient gérés par Intune.

5. L’appareil obtient est inscrit dans Intune.

6. Intune mappe l’enregistrement EAS à un enregistrement d’appareil, puis enregistre l’état de conformité de l’appareil.

7. L’ID du client EAS est enregistré par le processus d’inscription d’appareil d’Azure Active Directory, ce qui crée une relation entre l’enregistrement d’appareil Intune et le client EAS.

8. L’inscription d’appareil Azure AD enregistre les informations d’état de l’appareil.

9. Si l’utilisateur respecte les stratégies d’accès conditionnel, Intune émet une cmdlet via le connecteur Intune Exchange qui permet la synchronisation de la messagerie.

10. Exchange Server envoie la notification au client EAS afin que l’utilisateur puisse accéder à la messagerie.


#### <a name="whats-the-intune-role"></a>Quel est le rôle Intune ?

Intune évalue et gère l’état de l’appareil.

#### <a name="whats-the-exchange-server-role"></a>Quel est le rôle du serveur Exchange ?

Le serveur Exchange fournit l’API et l’infrastructure pour déplacer des appareils en quarantaine.

> [!IMPORTANT]
> N’oubliez pas que l’utilisateur de l’appareil doit déployer un profil de conformité et une licence Intune sur l’appareil afin que sa conformité puisse être évaluée. Si aucune stratégie de conformité n’est déployée sur l’utilisateur, l’appareil est considéré comme conforme et aucune restriction d’accès ne s’applique.

## <a name="next-steps"></a>Étapes suivantes

[Guide pratique de configuration de l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Configurer des stratégies d’accès conditionnel basées sur l’application](app-based-conditional-access-intune-create.md)

[Comment installer le connecteur Exchange local avec Intune](exchange-connector-install.md).

[Guide de création d’une stratégie d’accès conditionnel à Exchange sur site](conditional-access-exchange-create.md)
