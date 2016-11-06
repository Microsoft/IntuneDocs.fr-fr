---
title: "Fonctionnalités de gestion des appareils inscrits | Microsoft Intune"
description: "Lisez cette rubrique pour savoir comment Intune peut vous aider à gérer les appareils que vous inscrivez."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 710295f0eaeee71bba549c22706ecbfd062ffcb1


---
# Fonctionnalités de gestion des appareils inscrits de Microsoft Intune

Microsoft Intune vous permet de gérer une gamme d’appareils en les *inscrivant* auprès du service. Vous pouvez inscrire certains types d’appareils vous-même, ou les utilisateurs peuvent s’inscrire à l’aide de l’application *Portail d’entreprise*. Cela leur permet également d’effectuer des opérations telles que rechercher et installer des applications, vérifier la conformité de leurs appareils aux stratégies d’entreprise, et contacter leur support technique.

Cette rubrique fournit une liste complète des fonctionnalités auxquelles vous avez accès après avoir inscrit votre appareil.

La gestion, l'inventaire, le déploiement d'applications, l'approvisionnement et la mise hors service sont gérés par le biais de la console d'administration Intune. Les utilisateurs ont accès au portail d’entreprise, ce qui leur permet d’installer des applications, d’inscrire et de supprimer des appareils, et de contacter le service informatique ou le support technique.



## Configuration et sécurité des appareils

|Fonctionnalité|Détails|Plus d'informations|
|--------------|-----------|--------------------|
|Stratégies de configuration<br><br>Stratégies personnalisées| Vous permettent de gérer de nombreux paramètres et fonctionnalités sur les appareils mobiles de votre organisation. Par exemple, vous pouvez exiger un mot de passe, restreindre le nombre de tentatives de connexion ayant échoué, limiter la durée avant le verrouillage de l’écran, définir une date d’expiration du mot de passe et empêcher la réutilisation de mots de passe déjà utilisés. Vous pouvez également contrôler l’utilisation de fonctionnalités matérielles et logicielles telles que l’appareil photo ou le navigateur web.<br><br>Utilisez des stratégies personnalisées quand les stratégies de configuration ne contiennent pas les paramètres dont vous avez besoin. Pour les appareils iOS, vous pouvez importer les paramètres que vous avez exportés à l’aide de l’outil Apple Configurator. Pour d’autres appareils, vous pouvez utiliser des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour configurer les paramètres et fonctionnalités sur l’appareil.|[Gérer des paramètres et des fonctionnalités sur vos appareils avec des stratégies Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Réinitialisation à distance, verrouillage à distance et réinitialisation du code d'accès|Supprime les données sensibles en cas de perte ou de vol d’un appareil. Par exemple, vous pouvez verrouiller l'appareil à distance, restaurer ses paramètres d'usine ou effacer uniquement les données d'entreprise.<br><br>Vous pouvez réinitialiser les codes secrets si les utilisateurs ne peuvent plus accéder à leur appareil, verrouiller des appareils perdus ou volés ou supprimer les données d'appareils perdus ou volés.|[Protégez vos appareils avec le verrouillage à distance et la réinitialisation du mot de passe](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) et [Retirer des appareils de la gestion Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|Mode plein écran|Permet de verrouiller certaines fonctionnalités des appareils mobiles, comme la capture d’écran et les boutons d’alimentation. Vous permet également de limiter les appareils à l'exécution d'une seule application que vous spécifiez.|[Paramètres de la stratégie de configuration iOS dans Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## Gestion d'applications

|Fonctionnalité|Détails|Plus d'informations|
|--------------|-----------|--------------------|
|Déploiement et gestion d'applications|Fournit une gamme d'outils pour vous aider à gérer les applications mobiles tout au long de leur cycle de vie, notamment le déploiement d'applications à partir de fichiers d'installation ou de magasins d'applications, l'analyse détaillée de l'état des applications et la suppression d'applications.|[Déploiement d’applications dans Microsoft Intune](/intune/deploy-use/deploy-apps)|
|Applications conformes et non conformes|Vous permet de spécifier des listes d’applications conformes (que les utilisateurs sont autorisés à installer) et non conformes (que les utilisateurs ne sont pas autorisés à installer).|[Paramètres de la stratégie d’iOS dans Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Gestion des applications mobiles|Configure des restrictions pour les applications à l’aide de la gestion des applications mobiles pour tous les appareils (gérés ou non avec Intune). Une telle stratégie vous permet de renforcer la sécurité de vos données d’entreprise en limitant les opérations de copier-coller, de sauvegarde externe des données ou de transfert des données entre les applications.|[Configurer et déployer des stratégies de gestion des applications mobiles dans la console Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Créer et déployer des stratégies de gestion des applications mobiles à l’aide de Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Préparer des applications iOS pour la gestion des applications mobiles avec l'outil de création de package de restrictions d'application Microsoft Intune](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Préparer des applications Android pour la gestion des applications mobiles avec l'outil de création de package de restrictions d'application Microsoft Intune](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Configuration des applications mobiles iOS|Utilise des stratégies de configuration des applications mobiles pour fournir les paramètres des applications iOS pouvant être nécessaires lors de l’exécution d’une application. Par exemple, une application peut exiger que l’utilisateur spécifie un numéro de port ou des informations d’ouverture de session. Cela peut simplifier la configuration de l’application et réduire le nombre d’appels au support technique.|[Configurer des applications iOS avec des stratégies de configuration des applications mobiles dans Microsoft Intune](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Profils de configuration d’application mobile iOS|Permet de déployer des profils de configuration pour les applications iOS qui approchent de leur date d’expiration. |[Utiliser les stratégies de profil de configuration iOS mobile pour empêcher l’expiration de vos applications](/intune/deploy-use/ios-mobile-app-provisioning-profiles)|
|Managed Browser|Configure des stratégies Managed Browser pour contrôler les sites web auxquels les utilisateurs de l’appareil peuvent accéder. En outre, vous pouvez également appliquer des stratégies de gestion des applications mobiles à Managed Browser.|[Gérer l'accès à Internet à l'aide de stratégies Managed Browser avec Microsoft Intune](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello Entreprise|Vous permet d’intégrer Windows Hello Entreprise afin de disposer d’un autre mode de connexion pour Windows 10 qui fait appel à Active Directory local ou Azure Active Directory pour remplacer des mots de passe, des cartes à puce ou des cartes à puce virtuelles.|[Contrôler les paramètres Windows Hello Entreprise sur des appareils avec Microsoft Intune](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|Applications achetées en volume|Vous permet de gérer les applications que vous avez achetées par le biais d’un programme d’achat en volume en important les informations de licence à partir du magasin d’applications, en effectuant le suivi du nombre de licences que vous avez utilisées et en vous empêchant d’installer un nombre de copies de l’application supérieur au nombre dont vous êtes propriétaire.|[Gérer les applications achetées en volume avec Microsoft Intune](/intune/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## Accès aux ressources d'entreprise

|Fonctionnalité|Détails|Plus d'informations|
|--------------|-----------|--------------------|
|Profils de certificat|Crée et déploie des profils de certificat approuvés et des certificats SCEP (Simple Certificate Enrollment Protocol) qui peuvent être utilisés pour sécuriser et authentifier des profils Wi-Fi, VPN et de messagerie.|[Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Profils Wi-Fi|Déploie des paramètres de réseau sans fil sur vos utilisateurs. En déployant ces paramètres, vous réduisez l’effort que doit fournir l’utilisateur pour se connecter au réseau d’entreprise.|[Connexions Wi-Fi dans Microsoft Intune](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Profils de messagerie|Crée et déploie des paramètres de messagerie sur les appareils. Les utilisateurs peuvent ainsi accéder à leur messagerie professionnelle sur leur appareil personnel sans aucune autre configuration de leur part.|[Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Profils VPN|Déploie des paramètres VPN sur les utilisateurs et les appareils de votre organisation. En déployant ces paramètres, vous réduisez l’effort que doit fournir l’utilisateur pour se connecter aux ressources du réseau d’entreprise.|[Connexions VPN dans Microsoft Intune](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Stratégies d'accès conditionnel|Gère l’accès à la messagerie Microsoft Exchange et à SharePoint Online à partir des appareils qui ne sont pas gérés par Intune.|[Restreindre l’accès à la messagerie et à SharePoint avec Microsoft Intune](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## Inventaire et rapports

|Fonctionnalité|Détails|Plus d'informations|
|--------------|-----------|--------------------|
|Inventaire et rapports|Recherche des informations sur les appareils que vous gérez et sur les logiciels utilisés par les appareils.|[Comprendre vos appareils grâce à l’inventaire de Microsoft Intune](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### Voir aussi
[Fonctionnalités de gestion des PC Windows dans Microsoft Intune](windows-pc-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->


