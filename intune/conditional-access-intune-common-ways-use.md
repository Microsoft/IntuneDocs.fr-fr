---
title: Accès conditionnel avec Microsoft Intune
titlesuffix: ''
description: Découvrez comment l’accès conditionnel Intune est couramment utilisé pour l’accès conditionnel basé sur l’application et sur l’appareil.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d147bc5ee22718ecce102cc549b29faa17a617e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Quelles sont les utilisations courantes de l’accès conditionnel avec Intune ?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Il existe deux types d’accès conditionnel avec Intune : l’accès conditionnel basé sur l’appareil et l’accès conditionnel basé sur l’application. Vous devez configurer les stratégies de conformité associées pour déterminer l’accès conditionnel au niveau de votre organisation. L’accès conditionnel est couramment utilisé pour, par exemple, autoriser ou bloquer l’accès à Exchange sur site, contrôler l’accès au réseau ou intégrer une solution Mobile Threat Defense.

Les informations ci-dessous vous aident à comprendre comment utiliser les fonctionnalités de conformité des *appareils* mobiles et les fonctionnalités de gestion des *applications* mobiles d’Intune. 

## <a name="device-based-conditional-access"></a>Accès conditionnel basé sur l’appareil

Intune et Azure Active Directory fonctionnent ensemble pour s’assurer que seuls les appareils gérés et compatibles sont autorisés à accéder à la messagerie, aux services Office 365, aux applications SaaS et aux [applications locales](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). En outre, vous pouvez définir une stratégie dans Azure Active Directory pour autoriser uniquement les ordinateurs qui sont joints au domaine, ou les appareils mobiles qui sont inscrits dans Intune pour accéder aux services Office 365.

Intune fournit des fonctionnalités de stratégie de conformité des appareils qui évaluent l’état de conformité des appareils. L’état de conformité est signalé à Azure Active Directory, qui l’utilise pour appliquer la stratégie d’accès conditionnel créée dans Azure Active Directory lorsque l’utilisateur tente d’accéder aux ressources de votre entreprise.

Vous configurez les stratégies d’accès conditionnel basées sur l’appareil pour Exchange Online et les autres produits Office 365 via le [portail Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

-   Découvrez-en davantage sur [l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Découvrez plus d’informations sur la [conformité des appareils Intune](device-compliance.md).

-   Découvrez-en davantage sur [la protection de l’e-mail, d’Office 365 et d’autres services à l’aide de l’accès conditionnel avec Intune](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="conditional-access-for-exchange-on-premises"></a>Accès conditionnel pour Exchange sur site

L’accès conditionnel peut servir à autoriser ou bloquer l’accès à **Exchange en local** en fonction des stratégies de conformité d’appareil et de l’état d’inscription. Quand vous utilisez un accès conditionnel avec une stratégie de conformité d'appareil, seuls les appareils conformes peuvent accéder à Exchange en local.

Vous pouvez configurer des paramètres avancés dans l’accès conditionnel pour un contrôle plus précis, par exemple pour :

-   Autoriser ou bloquer certaines plateformes.

-   Bloquer immédiatement les appareils qui ne sont pas gérés par Intune.

La conformité de tout appareil utilisé pour accéder à une instance d’Exchange locale est vérifiée lorsque les stratégies d’accès conditionnel et de conformité d’appareil sont appliquées.

Quand un appareil ne remplit pas les conditions définies, l'utilisateur final est guidé tout au long du processus d'inscription de cet appareil pour résoudre le problème qui empêche l'appareil d'être conforme.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Fonctionnement de l’accès conditionnel pour Exchange sur site

Le connecteur Intune Exchange extrait tous les enregistrements Exchange Active Sync (EAS) qui existent sur le serveur Exchange. Intune peut ainsi prendre ces enregistrements EAS et les mapper à des enregistrements d’appareils Intune. Ces enregistrements sont les appareils inscrits et reconnus par Intune. Ce processus autorise ou bloque l’accès à la messagerie.

Si l’enregistrement EAS est nouveau et qu’Intune ne le sait pas, Intune émet une applet de commande qui bloque l’accès à la messagerie. Voici plus de détails sur le fonctionnement de ce processus :

![Exchange local avec organigramme de l’autorité de certification](./media/ca-intune-common-ways-1.png)

1.  L’utilisateur essaie d’accéder à une messagerie d’entreprise hébergée sur une instance locale d’Exchange 2010 SP1 (ou une version ultérieure).

2.  Si l’appareil n’est pas géré par Intune, son accès à la messagerie est bloqué. Intune envoie une notification de blocage au client EAS.

3.  EAS reçoit une notification de blocage, met l’appareil en quarantaine et envoie l’e-mail de mise en quarantaine, qui contient des étapes de résolution et des liens permettant aux utilisateurs d’inscrire leurs appareils.

4.  Le processus de jonction d’espace de travail se produit. Il s’agit de la première étape pour que les appareils soient gérés par Intune.

5.  L’appareil obtient est inscrit dans Intune.

6.  Intune mappe l’enregistrement EAS à un enregistrement d’appareil, puis enregistre l’état de conformité de l’appareil.

7.  L’ID du client EAS est enregistré par le processus d’inscription d’appareil d’Azure Active Directory, ce qui crée une relation entre l’enregistrement d’appareil Intune et le client EAS.

8.  L’inscription d’appareil Azure AD enregistre les informations d’état de l’appareil.

9.  Si l’utilisateur respecte les stratégies d’accès conditionnel, Intune émet une applet de commande via le connecteur Intune Exchange qui permet la synchronisation de la messagerie.

10. Exchange Server envoie la notification au client EAS afin que l’utilisateur puisse accéder à la messagerie.

#### <a name="whats-the-intune-role"></a>Quel est le rôle Intune ?

Intune évalue et gère l’état de l’appareil.

#### <a name="whats-the-exchange-server-role"></a>Quel est le rôle du serveur Exchange ?

Le serveur Exchange fournit l’API et l’infrastructure pour déplacer des appareils en quarantaine.

> [!IMPORTANT]
> N’oubliez pas que l’utilisateur de l’appareil doit déployer un profil de conformité sur l’appareil afin que sa conformité soit évaluée. Si aucune stratégie de conformité n’est déployée sur l’utilisateur, l’appareil est considéré comme conforme et aucune restriction d’accès ne s’applique.

### <a name="conditional-access-based-on-network-access-control"></a>Accès conditionnel basé sur le contrôle d’accès réseau

Intune est intégré avec des partenaires comme Cisco ISE, Aruba Clear Pass et Citrix NetScaler pour fournir des contrôles d’accès basés sur l’inscription Intune et l’état de conformité de l’appareil.

L’accès par les utilisateurs peut être accepté ou refusé lors de la tentative d’accéder au Wi-Fi ou aux ressources VPN de l’entreprise selon que l’appareil est géré et conforme ou non aux stratégies de conformité d’appareil d’Intune.

-   En savoir plus sur l’[intégration du contrôle d’accès réseau avec Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Accès conditionnel basé sur les risques que présente l’appareil

Intune fait équipe avec des fournisseurs de défense contre les menaces mobiles qui fournissent une solution de sécurité pour détecter les logiciels malveillants, les chevaux de Troie et autres menaces sur les appareils mobiles.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Comment fonctionne l’intégration entre Intune et la défense contre les menaces mobiles ?

Lorsqu’il est installé sur un appareil, l’agent de défense contre les menaces mobiles peut renvoyer des messages d’état de conformité à Intune pour indiquer si une menace a été identifiée sur l’appareil mobile proprement dit.

L’intégration entre Intune et la défense contre les menaces mobiles joue un rôle dans les décisions d’accès conditionnel basé sur les risques posés par les appareils.

-   Découvrez-en davantage sur la [défense contre les menaces mobiles](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense).

### <a name="conditional-access-for-windows-pcs"></a>Accès conditionnel pour les PC Windows

L’accès conditionnel pour PC offre des fonctionnalités similaires à celles disponibles pour les appareils mobiles. Examinons les façons dont vous pouvez utiliser l’accès conditionnel lors de la gestion des PC avec Intune.

#### <a name="corporate-owned"></a>Appartenant à l’entreprise

-   **Domaine Active Directory local joint :** il s’agit de l’option de déploiement de l’accès conditionnel la plus courante pour les organisations qui sont à l’aise avec le fait qu’elles gèrent déjà leurs PC via des stratégies de groupe Active Directory et/ou avec System Center Configuration Manager.

-   **Domaine Azure AD joint et gestion par Intune :** ce scénario est généralement conçu pour le CYOD (choisissez votre propre appareil) et les scénarios d’itinérance sur ordinateur portable où ces appareils sont rarement connectés au réseau d’entreprise. L’appareil est joint à Azure AD et est inscrit sur Intune, ce qui supprime les dépendances sur l’instance AD locale et les contrôleurs de domaine. Cela peut servir de critère d’accès conditionnel lors de l’accès aux ressources d’entreprise.

-   **Active Directory joint et System Center Configuration Manager :** à partir de Current Branch, System Center Configuration Manager fournit des fonctionnalités d’accès conditionnel qui peuvent évaluer des critères de compatibilité spécifiques, en plus d’être un PC joint au domaine :

    -   Le PC est-il chiffré ?

    -   Des programmes malveillants sont-ils installés ? Est-il à jour ?

    -   L’appareil est-il jailbreaké ou rooté ?

#### <a name="bring-your-own-device-byod"></a>Apportez votre propre appareil (BYOD)

-   **Jonction d’espace et gestion Intune :** ici, l’utilisateur peut joindre ses appareils personnels pour accéder aux ressources et services de l’entreprise. Vous pouvez utiliser le rattachement à l’espace de travail et inscrire des appareils dans Intune pour recevoir des stratégies au niveau de l’appareil, ce qui est également une option pour évaluer les critères d’accès conditionnel.

## <a name="app-based-conditional-access"></a>Accès conditionnel basé sur l’application

Intune et Azure Active Directory fonctionnent ensemble pour s’assurer que seules les applications gérées peuvent accéder à l’e-mail d’entreprise ou aux autres services Office 365.

-   Découvrez-en davantage sur [l’accès conditionnel basé sur l’application avec Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Étapes suivantes

[Guide pratique de configuration de l’accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Comment installer le connecteur Exchange local avec Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[Guide de création d’une stratégie d’accès conditionnel à Exchange sur site](conditional-access-exchange-create.md)
