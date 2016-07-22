---
title: "Guide de référence des stratégies Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 3d9e03a3c89af72caeaa9c9c47426f331adb0fca


---

# Guide de référence des stratégies Microsoft Intune

Utilisez les informations de cette rubrique pour vous aider à déterminer la stratégie Microsoft Intune à utiliser pour gérer vos appareils.

> [!TIP]
> Pour plus d’informations sur la façon d’utiliser les stratégies, consultez [Gérer des paramètres et des fonctionnalités sur vos appareils avec des stratégies Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).


## Stratégies de configuration Android

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Configuration personnalisée (Android 4 et versions ultérieures, Samsung Knox Standard 4.0 et versions ultérieures)**|Déployer les paramètres OMA-URI, par exemple, les paramètres Wi-Fi, qui peuvent être utilisés pour contrôler les fonctionnalités de l'appareil. Cela est utile quand le paramètre dont vous avez besoin n'est pas disponible dans une stratégie de configuration.<br /><br />Pour plus d’informations, consultez [Paramètres de stratégie Android dans Microsoft Intune](android-policy-settings-in-microsoft-intune.md).|
|**Profil de messagerie (Samsung Knox Standard 4.0 et versions ultérieures)**|Créez, déployez et analysez les paramètres de messagerie Exchange Active Sync sur les appareils gérés. L'utilisateur peut ainsi accéder à sa messagerie professionnelle sur son appareil personnel sans aucune autre configuration de sa part.<br /><br />Pour plus d’informations, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).|
|**Configuration générale (Android 4 et versions ultérieures, Samsung Knox Standard 4.0 et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles.<br />Spécifier les applications qui sont conformes ou non conformes et signaler quand elles sont utilisées.<br />Configurer le mode plein écran qui verrouille les appareils pour autoriser uniquement certaines fonctionnalités, par exemple, autoriser l'appareil à n'exécuter qu'une seule application ou désactiver les boutons de volume.<br /><br />Pour plus d’informations, consultez [Paramètres de stratégie Android dans Microsoft Intune](android-policy-settings-in-microsoft-intune.md).|
|**Profil de certificat PKCS #12 (.PFX) (Android 4 et versions ultérieures)**|Utilisez ce profil pour créer et déployer des paramètres PFX pour les demandes de certificat d’appareil.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil de certificat SCEP (Android 4 et versions ultérieures)**|Configurez un certificat SCEP (Simple Certificate Enrollment Protocol) utilisable avec un certificat d'appareil mobile approuvé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil de certificat approuvé (Android 4 et versions ultérieures)**|Configurez un certificat d'appareil mobile approuvé qui peut être utilisé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil VPN (Android 4 et versions ultérieures)**|Configurez et déployez des paramètres qui octroient aux utilisateurs un accès sécurisé à votre réseau d'entreprise à partir de leur appareil mobile. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter à son travail.<br /><br />Pour plus d’informations, consultez [Connexions VPN dans Microsoft Intune.md](vpn-connections-in-microsoft-intune.md).|
|**Profil Wi-Fi (Android 4 et versions ultérieures)**|Configurez et déployez des paramètres de réseau sans fil pour les utilisateurs de votre organisation. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter au réseau sans fil.<br /><br />Pour plus d’informations, consultez [Connexions Wi-Fi dans Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## Stratégies de configuration iOS

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Configuration personnalisée (iOS 7.1 et versions ultérieures)**|Déployez des profils de configuration que vous avez créés à l'aide de l'outil Apple Configurator sur des appareils iOS. Cela est utile quand le paramètre dont vous avez besoin n'est pas disponible dans une stratégie de configuration.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie iOS dans Microsoft Intune](ios-policy-settings-in-microsoft-intune.md).|
|**Profil de messagerie (iOS 7.1 et versions ultérieures)**|Créez, déployez et analysez les paramètres de messagerie Exchange Active Sync sur les appareils gérés. L'utilisateur peut ainsi accéder à sa messagerie professionnelle sur son appareil personnel sans aucune autre configuration de sa part.<br /><br />Pour plus d’informations, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).|
|**Configuration générale (iOS 7.1 et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles.<br />-   Spécifier les applications qui sont conformes ou non conformes et signaler quand elles sont utilisées.<br />Configurer le mode plein écran qui verrouille les appareils pour autoriser uniquement certaines fonctionnalités, par exemple, autoriser l'appareil à n'exécuter qu'une seule application ou désactiver les boutons de volume.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie iOS dans Microsoft Intune](ios-policy-settings-in-microsoft-intune.md).|
|**Profil de certificat SCEP (iOS 7.1 et versions ultérieures)**|Configurez un certificat SCEP (Simple Certificate Enrollment Protocol) utilisable avec un certificat d'appareil mobile approuvé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil de certificat approuvé (iOS 7.1 et versions ultérieures)**|Configurez un certificat d'appareil mobile approuvé qui peut être utilisé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil VPN (iOS 7.1 et versions ultérieures)**|Configurez et déployez des paramètres qui octroient aux utilisateurs un accès sécurisé à votre réseau d'entreprise à partir de leur appareil mobile. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter à son travail.<br /><br />Pour plus d’informations, consultez [Connexions VPN dans Microsoft Intune.md](vpn-connections-in-microsoft-intune.md).|
|**Profil Wi-Fi (iOS 7.1 et versions ultérieures)**|Configurez et déployez des paramètres de réseau sans fil pour les utilisateurs de votre organisation. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter au réseau sans fil.<br /><br />Pour plus d’informations, consultez [Connexions Wi-Fi dans Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|
|**Stratégie de configuration des applications mobiles (iOS 7.1 et versions ultérieures)**|Utilisez des stratégies de configuration des applications mobiles pour fournir automatiquement les paramètres pouvant être nécessaires quand l’utilisateur exécute une application iOS.<br /><br />Pour plus d’informations, consultez [Configurer des applications iOS avec des stratégies de configuration des applications mobiles dans Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).|

## Stratégies de configuration Mac OS X

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Configuration personnalisée (Mac OS X 10.9 et versions ultérieures)**|Déployer sur des ordinateurs Mac les profils de configuration que vous avez créés à l’aide de l’outil Apple Configurator. Cela est utile quand le paramètre dont vous avez besoin n'est pas disponible dans une stratégie de configuration.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie Mac OS X dans Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md).|
|**Configuration générale (Mac OS X 10.9 et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles.<br />Spécifier les applications qui sont conformes ou non conformes et signaler quand elles sont utilisées.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie Mac OS X dans Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md).|
|**Profil de certificat SCEP (Mac OS X 10.9 et versions ultérieures)**|Configurez un certificat SCEP (Simple Certificate Enrollment Protocol) utilisable avec un certificat d'appareil mobile approuvé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil de certificat approuvé (Mac OS X 10.9 et versions ultérieures)**|Configurez un certificat d'appareil mobile approuvé qui peut être utilisé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil VPN (Mac OS X 10.9 et versions ultérieures)**|Configurez et déployez des paramètres qui octroient aux utilisateurs un accès sécurisé à votre réseau d'entreprise à partir de leur appareil mobile. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter à son travail.<br /><br />Pour plus d’informations, consultez [Connexions VPN dans Microsoft Intune.md](vpn-connections-in-microsoft-intune.md).|
|**Profil VPN (Mac OS X 10.9 et versions ultérieures)**|Configurez et déployez des paramètres de réseau sans fil pour les utilisateurs de votre organisation. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter au réseau sans fil.<br /><br />Pour plus d’informations, consultez [Connexions Wi-Fi dans Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## Stratégies de configuration Windows
S'applique uniquement à Windows Phone et aux appareils Windows inscrits.

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Configuration personnalisée (Windows 10 Desktop et Mobile, et versions ultérieures)**|Déployer les paramètres OMA-URI qui peuvent être utilisés pour contrôler les fonctionnalités de l'appareil. Cela est utile quand le paramètre dont vous avez besoin n'est pas disponible dans une stratégie de configuration.<br />    Pour plus d’informations, consultez [Paramètres de la stratégie Windows 10 dans Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md).|
|**Configuration personnalisée (Windows Phone 8.1 et versions ultérieures)**|Déployer les paramètres OMA-URI qui peuvent être utilisés pour contrôler les fonctionnalités de l'appareil. Cela est utile quand le paramètre dont vous avez besoin n'est pas disponible dans une stratégie de configuration.<br /><br />Pour plus d’informations, consultez [Paramètres de Windows Phone 8.1 dans Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md).|
|**Stratégie de mise à niveau d’édition (Windows 10 Desktop et versions ultérieures)**<br><br>**Stratégie de mise à niveau d’édition (Windows 10 Holographique et versions ultérieures)**|Configurer et déployer des stratégies contenant des informations sur les licences ou les clés de produits qui sont utilisées pour mettre à jour des appareils Windows 10 vers une version plus récente.<br><br>Pour plus d’informations, consultez [Stratégie de mise à niveau d’édition](edition-upgrade-policy-settings-in-microsoft-intune.md).|  
|**Profil de messagerie (Windows Phone 8 et versions ultérieures)**<br /><br />**Profil de messagerie (Windows 10 Desktop et Mobile, et versions ultérieures)**|Créez, déployez et analysez les paramètres de messagerie Exchange Active Sync sur les appareils gérés. L'utilisateur peut ainsi accéder à sa messagerie professionnelle sur son appareil personnel sans aucune autre configuration de sa part.<br /><br />Pour plus d’informations, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).|
|**Configuration générale (Windows 10 Desktop et Mobile, et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles pour les appareils Windows 10 Desktop et Mobile inscrits.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie Windows 10 dans Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md).|
|**Configuration générale (Windows 10 Collaboration et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils pour les appareils Windows 10 Collaboration inscrits (par exemple, un appareil Surface Hub).<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie de configuration Windows Collaboration dans Microsoft Intune](windows-team-configuration-policy-settings-in-microsoft-intune.md).|
|**Configuration générale (Windows 8.1 et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles pour les appareils Windows inscrits.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie Windows dans Microsoft Intune](windows-configuration-policy-settings-in-microsoft-intune.md).|
|**Configuration générale (Windows Phone 8.1 et versions ultérieures)**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles.<br />Spécifiez les applications que les utilisateurs peuvent ou ne peuvent pas utiliser, et bloquez l'installation ou l'utilisation des applications non conformes.<br /><br />Pour plus d’informations, consultez [Paramètres de Windows Phone 8.1 dans Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md).|
|**Profil de certificat PKCS #12 (.PFX) (Windows 10 Desktop et Mobile, et versions ultérieures)**|Utilisez ce profil pour créer et déployer des paramètres PFX pour les demandes de certificat d’appareil.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil de certificat SCEP (Windows 8.1 et versions ultérieures)**<br /><br />**Profil de certificat SCEP (Windows Phone 8.1 et versions ultérieures)**|Configurez un certificat SCEP (Simple Certificate Enrollment Protocol) utilisable avec un certificat d'appareil mobile approuvé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil de certificat approuvé (Windows 8.1 et versions ultérieures)**<br /><br />**Profil de certificat approuvé (Windows Phone 8.1 et versions ultérieures)**|Configurez un certificat d'appareil mobile approuvé qui peut être utilisé pour authentifier les appareils mobiles et les autoriser à accéder à des ressources réseau telles que celles configurées par les profils VPN et Wi-Fi.<br /><br />Pour plus d’informations, consultez [Sécuriser l’accès aux ressources avec des profils de certificat dans Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profil VPN (Windows 10 Desktop et Mobile, et versions ultérieures)**<br /><br />**Profil VPN (Windows 8.1 et versions ultérieures)**<br /><br />**Profil VPN (Windows Phone 8.1 et versions ultérieures)**|Configurez et déployez des paramètres qui octroient aux utilisateurs un accès sécurisé à votre réseau d'entreprise à partir de leur appareil mobile. En déployant ces paramètres, vous réduisez l'effort que doit fournir l'utilisateur final pour se connecter à son travail.<br /><br />Pour plus d’informations, consultez [Connexions VPN dans Microsoft Intune.md](vpn-connections-in-microsoft-intune.md).|
|**Importation Wi-Fi**|Importer et déployer des configurations Wi-Fi Windows que vous avez précédemment exportées vers un fichier.<br /><br />Pour plus d’informations, consultez [Connexions Wi-Fi dans Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## Stratégies logicielles

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Stratégie Managed Browser (Android 4 et versions ultérieures)**<br /><br />**Stratégie Managed Browser (iOS 7.1 et versions ultérieures)**|Spécifiez les sites web auxquels les utilisateurs peuvent et ne peuvent pas accéder quand ils utilisent l'application Managed Browser.<br /><br />Pour plus d’informations, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).|
|**Stratégie de gestion des applications mobiles (Android 4 et versions ultérieures)**<br /><br />**Stratégie de gestion des applications mobiles (iOS 7.1 et versions ultérieures)**|Modifiez les fonctionnalités des applications que vous déployez pour les adapter aux stratégies de sécurité et de conformité de votre entreprise. Par exemple, vous pouvez restreindre les opérations Couper, Copier et Coller au sein d'une application limitée, ou configurer une application de sorte à ouvrir tous les liens web dans Managed Browser.<br /><br />Pour plus d’informations, consultez [Configurer et déployer des données à l’aide des stratégies de gestion des applications mobiles avec Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) (en anglais)|

## Paramètres communs d'appareils mobiles

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Stratégie Exchange ActiveSync**|Configurer les paramètres fonctionnels et de sécurité des appareils mobiles pour les appareils gérés par Exchange ActiveSync.<br /><br />Pour plus d’informations, consultez [Paramètres de la stratégie Exchange ActiveSync dans Microsoft Intune](exchange-activesync-policy-settings-in-microsoft-intune.md).|
|**Stratégie de sécurité des appareils mobiles**|<ul><li>Configure les paramètres des appareils mobiles (toutes les plateformes), notamment :<br /><br /><ul><li>Sécurité</li><li>Chiffrement</li><li>d'exploitation</li><li>Courrier électronique</li><li>Applications</li></ul></li></ul> **Important:** Microsoft Intune offre désormais des **stratégies de configuration** distinctes pour chaque plateforme d’appareil, qui contiennent les paramètres les plus récents que vous pouvez utiliser. Vous pouvez continuer à utiliser la stratégie de sécurité des appareils mobiles et tous les déploiements existants continueront de fonctionner, mais vous devez planifier la migration vers les nouvelles stratégies de configuration dès que possible.<br />Pour plus d’informations, consultez [Paramètres de stratégie de sécurité des appareils mobiles dans Microsoft Intune](mobile-device-security-policy-settings-in-microsoft-intune.md).|

## Stratégies d'accès conditionnel de conformité

### Accès conditionnel

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Stratégie Exchange Online**<br /><br />**Stratégie Exchange On-Premises**|Bloquer l’accès à la messagerie Microsoft Exchange à partir des appareils qui ne sont pas gérés par Intune ou qui ne sont pas conformes à une stratégie de conformité que vous avez créée.<br /><br />Pour plus d’informations, consultez [Restreindre l’accès à Exchange Online et au nouvel environnement Exchange Online Dedicated avec Intune](restrict-access-to-exchange-online-with-microsoft-intune.md).|
|**Stratégies SharePoint Online**|Bloquer l’accès à SharePoint Online à partir des appareils qui ne sont pas gérés par Intune ou qui ne sont pas conformes à une stratégie de conformité que vous avez créée.<br /><br />Pour plus d’informations, consultez [Restreindre l’accès à SharePoint Online avec Microsoft Intune](restrict-access-to-sharepoint-online-with-microsoft-intune.md).|
|**Skype pour Entreprises**|Bloquer l’accès à Skype pour Entreprises à partir des appareils qui ne sont pas gérés par Intune ou qui ne sont pas conformes à une stratégie de conformité que vous avez créée.<br /><br />Pour plus d’informations, consultez [Restreindre l’accès à Skype pour Entreprises avec Microsoft Intune](restrict-access-to-skype-for-business-online-with-microsoft-intune.md).|
> [!NOTE]
> Vous ne déployez pas de stratégies d'accès conditionnel pour les utilisateurs et les appareils. Au lieu de cela, vous configurez la stratégie requise, qui s'applique à tous les groupes ciblés dans la stratégie.

### Stratégies de conformité

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Stratégies de conformité**|Définir le niveau de conformité des appareils, puis signaler les appareils non conformes. Ces stratégies sont utilisées avec un accès conditionnel pour aider à évaluer les appareils qui ne doivent pas recevoir les services.<br /><br />Pour plus d’informations, consultez [Stratégies de conformité d’appareils dans Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).|

## Gestion des PC Windows

|Nom de la stratégie|À utiliser pour|
|---------------|------------------------|
|**Paramètres de l'Agent Microsoft Intune**|Configurer le client PC Intune sur les ordinateurs, notamment les paramètres pour :<br /><br />-   Endpoint Protection<br />-   Mises à jour logicielles<br />-   Planification de la vérification de stratégie<br /><br />Ce type de stratégie peut être déployé uniquement sur des groupes d'appareils.<br /><br />Les clients Intune téléchargent les nouvelles stratégies et les stratégies mises à jour conformément au paramètre **Fréquence de détection des applications et mises à jour**, dont la valeur par défaut est de 8 heures. Toutefois, vous pouvez forcer une actualisation de la stratégie sur les ordinateurs à tout moment.<br /><br />Pour plus d’informations, consultez [Maintenir des PC Windows à jour avec les mises à jour logicielles dans Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Paramètres de Microsoft Intune Center**|Configurer les informations qui s’affichent dans Microsoft Intune Center sur les ordinateurs gérés.<br /><br />Ce type de stratégie peut être déployé uniquement sur des groupes d'appareils.<br /><br />Pour plus d’informations, consultez [Tâches courantes de gestion des PC Windows avec le client Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).|
|**Paramètres du pare-feu de Windows**|Configure les paramètres du Pare-feu Windows et des exceptions pour les communications réseau courantes sur les ordinateurs, notamment :<br /><br />-   BranchCache<br />-   Assistance à distance<br />-   Partage de fichiers multimédias<br /><br />Ce type de stratégie peut être déployé uniquement sur des groupes d'appareils.<br /><br />Pour plus d’informations, consultez [Contribuer à la sécurisation des PC Windows avec Endpoint Protection pour Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).|

### Voir aussi

[Gérer des paramètres et des fonctionnalités sur vos appareils avec des stratégies Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


