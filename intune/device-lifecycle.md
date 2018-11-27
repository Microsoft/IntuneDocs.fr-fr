---
title: Vue d’ensemble du cycle de vie de la gestion des appareils mobiles Microsoft Intune
description: Découvrez comment Intune vous aide à gérer les appareils tout au long de leur cycle de vie, de l’inscription à la mise hors service éventuelle, en passant par la configuration.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: b78f7414e4ba383e934abd467a9f4c7c67c6bac5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182599"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Vue d’ensemble du cycle de vie de la gestion des appareils mobiles dans Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Tous les appareils que vous gérez ont un *cycle de vie*. Intune peut vous aider à gérer ce cycle de vie : de l’inscription de l’appareil à sa mise hors service quand il n’est plus nécessaire, en passant par sa configuration et sa protection.

![Le cycle de vie de l'appareil](./media/device-lifecycle.png "le cycle de vie de l'appareil Intune")

## <a name="enroll"></a>Inscription
De nos jours, les stratégies de gestion des appareils mobiles traitent une large gamme de téléphones, de tablettes et de PC (iOS, Android, Windows et Mac OS X). Si vous devez gérer un appareil, ce qui est généralement le cas pour les appareils d’entreprise, la première étape consiste à [configurer l’inscription de cet appareil](device-enrollment.md) ([portail classique](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)). Vous pouvez également gérer les PC Windows en les inscrivant dans Intune (gestion des appareils mobiles) ou en [installant le logiciel client Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune).

## <a name="configure"></a>Configurer
L’inscription de vos appareils n’est que la première étape. Pour tirer parti de toutes les offres d’Intune et vous assurer que vos appareils sécurisés et conformes aux normes de l’entreprise, vous pouvez choisir parmi une large gamme de stratégies. Ces stratégies permettent de configurer quasiment tous les aspects du fonctionnement d’un appareil géré. Par exemple, les utilisateurs doivent-ils avoir un mot de passe sur les appareils qui contiennent des données de l’entreprise ? Vous pouvez l'exiger. Avez-vous un Wi-Fi d’entreprise ? Vous pouvez le configurer automatiquement. Voici les types d’options de configuration disponibles :

- [**Configuration de l’appareil** ](device-profiles.md) ([portail classique](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)). Ces stratégies vous permettent de configurer les fonctionnalités des appareils que vous gérez. Par exemple, vous pouvez exiger l’utilisation d’un mot de passe sur un Windows Phone, ou désactiver l’utilisation de la caméra sur un iPhone.
- [**Accès aux ressources d’entreprise** ](device-profiles.md) ([portal classique](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)). Le fait d’autoriser vos utilisateurs à accéder à leurs ressources de travail sur leur appareil personnel peut représenter un réel défi. Par exemple, comment vous assurez-vous que tous les appareils qui doivent accéder à la messagerie d’entreprise sont configurés correctement ? Comment faire en sorte que les utilisateurs puissent accéder au réseau de l’entreprise par le biais d’une connexion VPN sans avoir à connaître les paramètres complexes associés ? Intune peut réduire ce fardeau en configurant automatiquement les appareils que vous gérez de manière à ce qu’ils puissent accéder aux ressources d’entreprise les plus couramment utilisées.
- [**Stratégies de gestion des PC Windows (avec le logiciel client Intune)**](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client). L’inscription des PC Windows auprès d’Intune permet de tirer le meilleur parti des fonctionnalités de gestion des appareils. Toutefois, Intune continue à prendre en charge la gestion des PC Windows avec le logiciel client Intune. Si vous avez besoin d’informations sur certaines des tâches que vous pouvez effectuer sur des PC, lisez ce qui suit.

## <a name="protect"></a>Protéger
Dans le monde informatique moderne, la protection des appareils contre tout accès non autorisé est l’une des tâches les plus importantes à réaliser. Outre les éléments de l’étape de **configuration** du cycle de vie des appareils, Intune fournit davantage de fonctionnalités qui protègent les appareils que vous gérez de tout accès non autorisé ou d’attaques malveillantes :
- [**Authentification multifacteur**](/intune-classic/deploy-use/protect-your-devices-with-microsoft-intune). L’ajout d’une couche supplémentaire d’authentification pour les connexions utilisateur peut renforcer davantage la sécurité des appareils. De nombreux appareils prennent en charge l’authentification multifacteur qui nécessite un second niveau d’authentification, tels qu’un appel téléphonique ou un SMS avant que les utilisateurs puissent disposer d’un accès.
- [**Paramètres Windows Hello Entreprise**](windows-hello.md) ([portail classique](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)) Windows Hello Entreprise est une autre méthode d’authentification qui permet aux utilisateurs d’utiliser un *geste* (par exemple, la reconnaissance des empreintes digitales ou Windows Hello) pour se connecter sans avoir besoin d’un mot de passe.
- [**Stratégies permettant de protéger les PC Windows (avec le logiciel client Intune)**](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune). Quand vous gérez des ordinateurs Windows à l’aide du logiciel client Intune, vous pouvez utiliser des stratégies qui permettent de contrôler les paramètres pour Endpoint Protection, les mises à jour logicielles et le pare-feu Windows sur les ordinateurs que vous gérez.

## <a name="retire"></a>Mettre hors service
Quand un appareil est perdu ou volé, lorsqu’il doit être remplacé ou lorsque des utilisateurs changent de poste, il doit généralement être [mis hors service ou réinitialisé](device-management.md) ([portail classique](/intune-classic/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)). Pour ce faire, vous pouvez, par exemple, réinitialiser l’appareil, le supprimer de la gestion ou réinitialiser les données d’entreprise qu’il contient.
