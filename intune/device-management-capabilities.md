---
title: Fonctionnalités de gestion des appareils dans Microsoft Intune
description: Lisez cette rubrique pour savoir comment Intune peut vous aider à gérer les appareils que vous inscrivez.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39fd7256b9db7590a3a6b601b8884494062fe897
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845293"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Fonctionnalités de gestion des appareils inscrits de Microsoft Intune

Microsoft Intune vous permet de gérer une gamme d’appareils en les *inscrivant* auprès du service. Vous pouvez inscrire certains types d’appareils vous-même, ou les utilisateurs peuvent s’inscrire à l’aide de l’application *Portail d’entreprise*. L’inscription leur permet de parcourir et d’installer des applications, de s’assurer que leurs appareils sont conformes aux stratégies de l’entreprise et de contacter leur support informatique.

Cet article fournit une liste complète des fonctionnalités dont vous bénéficiez après avoir inscrit vos appareils.

La gestion, le stock, le déploiement d'applications, le provisionnement et la mise hors service sont gérés dans le portail Intune.

Les utilisateurs ont accès au portail d’entreprise, ce qui leur permet d’installer des applications, d’inscrire et de supprimer des appareils, et de contacter le service informatique ou le support technique.



## <a name="device-security-and-configuration"></a>Configuration et sécurité des appareils

|Fonctionnalité|Détails|Plus d'informations|
|--------------|-----------|--------------------|
|Stratégies de configuration<br><br>Stratégies personnalisées| Vous permettent de gérer de nombreux paramètres et fonctionnalités sur les appareils mobiles de votre organisation. Par exemple, vous pouvez exiger un mot de passe, restreindre le nombre de tentatives de connexion ayant échoué, limiter la durée avant le verrouillage de l’écran, définir une date d’expiration du mot de passe et empêcher la réutilisation de mots de passe déjà utilisés. Vous pouvez également contrôler l’utilisation de fonctionnalités matérielles et logicielles telles que l’appareil photo ou le navigateur web.<br><br>Utilisez des stratégies personnalisées quand les stratégies de configuration ne contiennent pas les paramètres dont vous avez besoin. Pour les appareils iOS, vous pouvez importer les paramètres que vous avez exportés à l’aide de l’outil Apple Configurator. Pour d’autres appareils, vous pouvez utiliser des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour configurer les paramètres et fonctionnalités sur l’appareil.|[Gérer des paramètres et des fonctionnalités sur vos appareils avec des stratégies Microsoft Intune](device-compliance-get-started.md)|
|Réinitialisation à distance, verrouillage à distance et réinitialisation du code d'accès|Supprime les données sensibles en cas de perte ou de vol d’un appareil. Par exemple, vous pouvez verrouiller l'appareil à distance, restaurer ses paramètres d'usine ou effacer uniquement les données d'entreprise.<br><br>Vous pouvez réinitialiser les codes secrets si les utilisateurs ne peuvent plus accéder à leur appareil, verrouiller des appareils perdus ou volés ou supprimer les données d'appareils perdus ou volés.|Protéger vos appareils à l’aide du [verrouillage à distance](device-remote-lock.md) et de la [réinitialisation du code d’accès](device-passcode-reset.md)|
|Mode plein écran|Permet de verrouiller certaines fonctionnalités des appareils mobiles, comme la capture d’écran et les boutons d’alimentation. Vous permet également de limiter les appareils à l'exécution d'une seule application que vous spécifiez.|[Paramètres de la stratégie de configuration iOS dans Microsoft Intune](device-restrictions-ios.md)|

## <a name="app-management"></a>Gestion d'applications

|Fonctionnalité|Détails|Plus d’informations|
|--------------|-----------|--------------------|
|Déploiement et gestion d'applications|Fournit une gamme d'outils pour vous aider à gérer les applications mobiles tout au long de leur cycle de vie, notamment le déploiement d'applications à partir de fichiers d'installation ou de magasins d'applications, l'analyse détaillée de l'état des applications et la suppression d'applications.|[Déploiement d’applications dans Microsoft Intune](apps-deploy.md)|
|Applications conformes et non conformes|Vous permet de spécifier des listes d’applications conformes (que les utilisateurs sont autorisés à installer) et non conformes (que les utilisateurs ne sont pas autorisés à installer).|[Paramètres de la stratégie d’iOS dans Microsoft Intune](device-restrictions-ios.md)|
|Gestion des applications mobiles|Configure des restrictions pour les applications à l’aide de la gestion des applications mobiles pour tous les appareils (gérés ou non avec Intune). Vous pouvez renforcer la sécurité de vos données d’entreprise en limitant les opérations de copier-coller, de sauvegarde externe des données ou de transfert des données entre les applications.|[Configurer et déployer des stratégies de gestion des applications mobiles dans la console Microsoft Intune](app-wrapper-prepare-android.md)|
|Configuration des applications mobiles iOS|Utilise des stratégies de configuration des applications mobiles pour fournir les paramètres des applications iOS pouvant être nécessaires lors de l’exécution d’une application. Par exemple, une application peut exiger que l’utilisateur spécifie un numéro de port ou des informations d’ouverture de session. Vous pouvez simplifier la configuration de l’application et réduire le nombre d’appels au support technique.|[Configurer des applications iOS avec des stratégies de configuration des applications mobiles dans Microsoft Intune](app-configuration-policies-use-ios.md)|
|Profils de configuration d’application mobile iOS|Permet de déployer des profils de configuration pour les applications iOS qui approchent de leur date d’expiration. |[Utiliser les stratégies de profil de configuration iOS mobile pour empêcher l’expiration de vos applications](app-provisioning-profile-ios.md)|
|Managed Browser|Configure des stratégies Managed Browser pour contrôler les sites web auxquels les utilisateurs de l’appareil peuvent accéder. En outre, vous pouvez également appliquer des stratégies de gestion des applications mobiles à Managed Browser.|[Gérer l'accès à Internet à l'aide de stratégies Managed Browser avec Microsoft Intune](app-configuration-managed-browser.md)|
|Windows Hello Entreprise|Vous permet d’intégrer Windows Hello Entreprise afin de disposer d’un autre mode de connexion pour Windows 10 qui fait appel à Active Directory local ou Azure Active Directory pour remplacer des mots de passe, des cartes à puce ou des cartes à puce virtuelles.|[Contrôler les paramètres Windows Hello Entreprise sur des appareils avec Microsoft Intune](windows-hello.md)|
|Applications achetées en volume|Vous permet de gérer les applications que vous avez achetées par le biais d’un programme d’achat en volume en important les informations de licence à partir du magasin d’applications, en effectuant le suivi du nombre de licences que vous avez utilisées et en vous empêchant d’installer un nombre de copies de l’application supérieur au nombre dont vous êtes propriétaire.|[Gérer les applications achetées en volume avec Microsoft Intune](vpp-apps.md)|

## <a name="company-resource-access"></a>Accès aux ressources d'entreprise

|Fonctionnalité|Détails|Plus d’informations|
|--------------|-----------|--------------------|
|Profils de certificat|Crée et déploie des profils de certificat approuvés et des certificats SCEP (Simple Certificate Enrollment Protocol) qui peuvent être utilisés pour sécuriser et authentifier des profils Wi-Fi, VPN et de messagerie.|[Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](certificates-configure.md)|
|Profils Wi-Fi|Déploie des paramètres de réseau sans fil sur vos utilisateurs. En déployant ces paramètres, vous réduisez l’effort que doit fournir l’utilisateur pour se connecter au réseau d’entreprise.|[Connexions Wi-Fi dans Microsoft Intune](wi-fi-settings-configure.md)|
|Profils de messagerie|Crée et déploie les paramètres de messagerie sur les appareils pour que les utilisateurs puissent accéder à leur e-mail professionnel sur leur appareil personnel sans aucune autre configuration de leur part.|[Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](email-settings-configure.md)|
|Profils VPN|Déploie des paramètres VPN sur les utilisateurs et les appareils de votre organisation. En déployant ces paramètres, vous réduisez l’effort que doit fournir l’utilisateur pour se connecter aux ressources du réseau d’entreprise.|[Connexions VPN dans Microsoft Intune](device-profiles.md#vpn)|
|Stratégies d'accès conditionnel|Gère l’accès à la messagerie Microsoft Exchange et à SharePoint Online à partir des appareils qui ne sont pas gérés par Intune.|[Restreindre l’accès à la messagerie et à SharePoint avec Microsoft Intune](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Étapes suivantes

[Afficher la liste des appareils que vous pouvez gérer](device-management.md).
