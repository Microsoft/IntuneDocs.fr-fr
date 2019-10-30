---
title: Vue d’ensemble du cycle de vie de la gestion des appareils mobiles Microsoft Intune
description: Découvrez comment Intune vous aide à gérer les appareils tout au long de leur cycle de vie, de l’inscription à la mise hors service éventuelle, en passant par la configuration.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 816ad4bb5b17f3a480fbf834280c4e9792c394a9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502984"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Vue d’ensemble du cycle de vie de la gestion des appareils mobiles dans Microsoft Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Tous les appareils que vous gérez ont un *cycle de vie*. Intune peut vous aider à gérer ce cycle de vie : de l’inscription de l’appareil à sa mise hors service quand il n’est plus nécessaire, en passant par sa configuration et sa protection.

![Le cycle de vie de l’appareil](./media/device-lifecycle/device-lifecycle.png "Le cycle de vie de l’appareil Intune")

## <a name="enroll"></a>Inscription
De nos jours, les stratégies de gestion des appareils mobiles traitent une large gamme de téléphones, de tablettes et de PC (iOS, Android, Windows et Mac OS X). Si vous devez gérer un appareil, ce qui est généralement le cas pour les appareils d’entreprise, la première étape consiste à [configurer l’inscription de cet appareil](../enrollment/device-enrollment.md). Vous pouvez également gérer les PC Windows en les inscrivant dans Intune (gestion des appareils mobiles) ou en [installant le logiciel client Intune](../manage-windows-pcs-with-microsoft-intune.md).

## <a name="configure"></a>Configurer
L’inscription de vos appareils n’est que la première étape. Pour tirer parti de toutes les offres d’Intune et vous assurer que vos appareils sécurisés et conformes aux normes de l’entreprise, vous pouvez choisir parmi une large gamme de stratégies. Ces stratégies permettent de configurer quasiment tous les aspects du fonctionnement d’un appareil géré. Par exemple, les utilisateurs doivent-ils avoir un mot de passe sur les appareils qui contiennent des données de l’entreprise ? Vous pouvez l'exiger. Avez-vous un Wi-Fi d’entreprise ? Vous pouvez le configurer automatiquement. Voici les types d’options de configuration disponibles :

- [**Configuration des appareils**](../configuration/device-profiles.md). Ces stratégies vous permettent de configurer les fonctionnalités des appareils que vous gérez. Par exemple, vous pouvez exiger l’utilisation d’un mot de passe sur un Windows Phone, ou désactiver l’utilisation de la caméra sur un iPhone.
- [**Accès aux ressources de l’entreprise**](../configuration/device-profiles.md). Le fait d’autoriser vos utilisateurs à accéder à leurs ressources de travail sur leur appareil personnel peut représenter un réel défi. Par exemple, comment vous assurez-vous que tous les appareils qui doivent accéder à la messagerie d’entreprise sont configurés correctement ? Comment faire en sorte que les utilisateurs puissent accéder au réseau de l’entreprise par le biais d’une connexion VPN sans avoir à connaître les paramètres complexes associés ? Intune peut réduire ce fardeau en configurant automatiquement les appareils que vous gérez de manière à ce qu’ils puissent accéder aux ressources d’entreprise les plus couramment utilisées.
- [**Stratégies de gestion des PC Windows (avec le logiciel client Intune)** ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). L’inscription des PC Windows auprès d’Intune permet de tirer le meilleur parti des fonctionnalités de gestion des appareils. Toutefois, Intune continue à prendre en charge la gestion des PC Windows avec le logiciel client Intune. Si vous avez besoin d’informations sur certaines des tâches que vous pouvez effectuer sur des PC, lisez ce qui suit.

## <a name="protect"></a>Protéger
Dans le monde informatique moderne, la protection des appareils contre tout accès non autorisé est l’une des tâches les plus importantes à réaliser. Outre les éléments de l’étape de **configuration** du cycle de vie des appareils, Intune fournit davantage de fonctionnalités qui protègent les appareils que vous gérez de tout accès non autorisé ou d’attaques malveillantes :
- [**Authentification multifacteur**](../enrollment/multi-factor-authentication.md). L’ajout d’une couche supplémentaire d’authentification pour les connexions utilisateur peut renforcer davantage la sécurité des appareils. De nombreux appareils prennent en charge l’authentification multifacteur qui nécessite un second niveau d’authentification, tels qu’un appel téléphonique ou un SMS avant que les utilisateurs puissent disposer d’un accès.
- [**Paramètres Windows Hello Entreprise**](../protect/windows-hello.md). Windows Hello Entreprise est une autre méthode d’authentification qui permet aux utilisateurs d’utiliser un *geste* (par exemple, la reconnaissance des empreintes digitales ou Windows Hello) pour se connecter sans avoir besoin d’un mot de passe.
- [**Stratégies permettant de protéger les PC Windows (avec le logiciel client Intune)** ](../policies-to-protect-windows-pcs-in-microsoft-intune.md). Quand vous gérez des ordinateurs Windows à l’aide du logiciel client Intune, vous pouvez utiliser des stratégies qui permettent de contrôler les paramètres pour Endpoint Protection, les mises à jour logicielles et le pare-feu Windows sur les ordinateurs que vous gérez.

## <a name="retire"></a>Mettre hors service
Quand un appareil est perdu ou volé, lorsqu’il doit être remplacé ou lorsque des utilisateurs changent de poste, il doit généralement être [mis hors service ou réinitialisé](../remote-actions/device-management.md). Pour ce faire, vous pouvez, par exemple, réinitialiser l’appareil, le supprimer de la gestion ou réinitialiser les données d’entreprise qu’il contient.

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur la [gestion des appareils dans Microsoft Intune](../remote-actions/device-management.md)
