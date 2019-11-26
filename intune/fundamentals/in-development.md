---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 796439581ca0ae91e788a91ab0bc2ef8f6019626
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199339"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>En développement pour Microsoft Intune - Décembre 2019

Pour faciliter votre préparation et votre planification, cette page répertorie les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore mises en production. Outre les informations de cette page :

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité entre en production, qu’il s’agisse d’une version d’évaluation ou d’une disponibilité générale, la description de la fonctionnalité est déplacée de cette page vers [Nouveautés](whats-new.md).
- Cette page et la page [Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!NOTE]
> Cette page reflète nos attentes actuelles concernant les fonctionnalités Intune dans une version ultérieure. Les dates et les fonctionnalités individuelles peuvent changer. Cette page ne décrit pas toutes les fonctionnalités du développement.

**Flux RSS** : découvrez quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestion d'applications

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>applications VPP avec licence utilisateur iOS<!-- 5619268 idready -->
Pour les appareils iOS d’inscription utilisateur, les utilisateurs finaux ne seront plus présentés avec les applications VPP avec licence d’appareil déployées comme disponibles. Toutefois, les utilisateurs finaux continuent de voir toutes les applications VPP sous licence utilisateur au sein du Portail d’entreprise. Pour plus d’informations sur les applications VPP, consultez [Guide pratique pour gérer les applications iOS et macOS achetées par le biais d’un programme d’achat en volume Apple avec Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Récupérer une clé de récupération personnelle à partir d’appareils macOS chiffrés par MEM<!-- 4851745 idready -->
Les utilisateurs finaux seront en mesure de récupérer leur clé de récupération personnelle (clé FileVault) à l’aide de l’application Portail d’entreprise iOS. L’appareil qui a la clé de récupération personnelle doit être inscrit auprès d’Intune et chiffré avec FileVault via Intune. À l’aide de l’application Portail d’entreprise iOS, un utilisateur final peut ouvrir l’affichage Web de Safari et récupérer sa clé de récupération personnelle. Dans Intune, sélectionnez les **appareils** > *l’appareil MacOS chiffré et inscrit* > récupérer la **clé de récupération**. Pour plus d’informations sur FileVault, consultez [chiffrement FileVault pour MacOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="microsoft-app-icons-update--4677605--"></a>Mise à jour des icônes d’application Microsoft<!--4677605-->
Les icônes utilisées pour les applications Microsoft dans le volet de ciblage de l’application pour les stratégies de configuration d’application et de stratégie de protection des applications sont mises à jour.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Prise en charge S/MIME pour Microsoft Outlook Mobile<!-- 2669398  -->
Intune prendra en charge la diffusion de certificats de chiffrement et de signature S/MIME qui peuvent être utilisés avec Outlook Mobile sur iOS et Android. Pour obtenir des informations connexes, consultez [paramètres de messagerie pour les appareils iOS](~/configuration/email-settings-ios.md) et [paramètres de messagerie pour les appareils Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Prise en charge des paramètres personnalisés pour les applications macOS<!-- 4736278  -->
Intune prend en charge les paramètres personnalisés, ce qui vous permet d’ajouter des clés et des valeurs spécifiques à un fichier de liste de propriétés de préférences (. plist) existant pour configurer les applications macOS et l’appareil. Toutes les applications ne prennent pas en charge les préférences gérées et, dans certains cas, seuls des paramètres spécifiques peuvent être gérés. Les paramètres sont déployés uniquement via le canal de l’appareil. Vous ne devez télécharger que des fichiers de liste de propriétés ou des fichiers. XML qui ciblent les paramètres de canal de l’appareil.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Afficher les notifications de l’application Portail d’entreprise sur Windows<!-- 1808082  -->
Nous allons mettre à jour l’application Portail d’entreprise sur les appareils Windows pour afficher les notifications Toast aux utilisateurs, même lorsque l’application est fermée. La mise à jour affiche les notifications pour les applications disponibles uniquement lorsque l’état de l’installation est terminé ou a échoué. L’application Portail d’entreprise n’affiche pas de notifications pour les applications requises.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Afficher les messages d’état d’installation de l’application Portail d’entreprise<!-- 2514416  -->
L’application Portail d’entreprise affiche des messages d’état d’installation d’application supplémentaires pour les utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation<!-- 2576686 -->
L’application Intune sur des appareils Android et iOS vous permettra de contrôler le contenu de la notification d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur l’Application, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Empêche les utilisateurs de configurer les informations d’identification de certificat dans le magasin de clés géré sur les appareils Android Enterprise propriétaire de l’appareil<!-- 3311998 idready -->
Sur les appareils Android Enterprise Owner, un nouveau paramètre empêche les utilisateurs de configurer les informations d’identification de leur certificat dans le magasin de clés managé (**configuration** de l’appareil > **profils** > **créer un profil** > **Android Enterprise** pour la plateforme > propriétaire de l’appareil **uniquement > les restrictions d’appareil** pour le type de profil > **utilisateurs + comptes**).

Pour voir les paramètres actuels, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Propriétaire de l’appareil Android Enterprise, y compris les appareils dédiés et entièrement gérés

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Profils de configuration de périphérique réseau câblé pour les appareils macOS<!-- 3508686 idready -->
Sur les appareils macOS, une mise à jour ultérieure inclut un nouveau profil de configuration d’appareil qui configure des réseaux câblés (**configuration** de l’appareil > **profils** > **créer un profil** > **MacOS** pour la plateforme > **réseau câblé** pour le type de profil). Utilisez cette fonctionnalité pour créer des profils 802.1 x pour gérer les réseaux câblés et déployer ces réseaux câblés sur vos appareils macOS.

S’applique à :
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Ajouter des paramètres de proxy automatique aux profils Wi-Fi pour les profils de travail Android Enterprise<!-- 4490822 idready -->
Sur les appareils Android Enterprise Work Profile, vous pouvez créer des profils Wi-Fi. Lorsque vous choisissez le type d’entreprise Wi-Fi, vous pouvez également entrer le type de protocole EAP (Extensible Authentication Protocol) utilisé sur votre réseau Wi-Fi.

Dans une prochaine mise à jour, lorsque vous choisissez le type d’entreprise, vous pouvez entrer des paramètres de proxy automatiques, y compris une URL de serveur proxy, par exemple `proxy.contoso.com`.

Pour afficher les paramètres Wi-Fi actuels que vous pouvez configurer, accédez à [Ajouter des paramètres Wi-Fi pour les appareils exécutant Android Enterprise et Android Kiosk dans Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

S’applique à :
- Profil professionnel Android Entreprise

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>Activer le contrôle d’accès réseau (NAC) avec Cisco AnyConnect VPN sur les appareils iOS<!-- 4860111 idready -->
Sur les appareils iOS, vous pouvez créer un profil VPN et utiliser différents types de connexion, notamment Cisco AnyConnect (configuration de l'**appareil** > **profils** > **créer un profil** > **iOS** pour la plateforme > **VPN** pour le type de profil > **Cisco AnyConnect** pour le type de connexion). 

Dans une prochaine mise à jour, vous pourrez activer le contrôle d’accès réseau (NAC) avec Cisco AnyConnect. Pour utiliser cette fonctionnalité :

1. Dans le Guide de l' [administrateur du moteur Cisco Identity services](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html), suivez les étapes de la section **configuration de Microsoft Intune en tant que serveur MDM** pour configurer le moteur Cisco Identity services (ISE) dans Azure.
2. Dans le profil de configuration d’appareil Intune, sélectionnez le paramètre **activer le Access Control réseau (NAC)** .

Pour afficher tous les paramètres VPN disponibles, accédez à [configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md).

S’applique à :
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Mise à jour de l’expérience d’authentification unique pour les applications et sites Web sur vos appareils iOS, iPados et macOS<!-- 4999578 idready -->
Intune ajoute des paramètres d’authentification unique pour les appareils iOS, iPados et macOS. Actuellement, vous pouvez configurer des extensions d’application SSO d’identification et l’extension Kerberos intégrée d’Apple dans Intune. Dans une prochaine mise à jour, vous serez en mesure de configurer des extensions d’application SSO de redirection écrites par votre organisation ou par votre fournisseur d’identité. 

Utilisez ces paramètres pour configurer une expérience d’authentification unique transparente pour les applications et les sites Web qui utilisent des méthodes d’authentification modernes, telles que OAuth et SAML2. 

Pour afficher les paramètres d’extension d’application SSO que vous pouvez configurer, accédez à [SSO sur iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) et [SSO sur MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

S’applique à :
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Exiger l’utilisation de claviers approuvés sur Android<!--4761794 IDready -->
Vous pouvez spécifier une liste de claviers approuvés pour une utilisation dans les applications Android gérées. À partir de l’application gérée, l’utilisateur est invité à basculer vers l’un des claviers approuvés déjà installés sur son appareil ou, si nécessaire, il est dirigé vers le Google Play Store pour télécharger et configurer l’un des claviers approuvés. L’utilisateur pourra uniquement modifier les champs de texte dans une application gérée si son clavier actif est l’un des claviers approuvés.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Utiliser des certificats PKCS avec des profils Wi-Fi sur les appareils Windows 10 et versions ultérieures<!-- 3246388  -->
Actuellement, vous pouvez authentifier les profils Wi-Fi Windows avec des certificats SCEP (configuration de l'**appareil** > **profils** > **créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Wi-Fi** pour type de profil > **Enterprise** > **type EAP**). Vous pouvez utiliser des certificats PKCS avec vos profils Wi-Fi Windows. Cette fonctionnalité permet aux utilisateurs d’authentifier des profils Wi-Fi à l’aide de profils de certificat PKCS nouveaux ou existants dans votre locataire. 

Pour plus d’informations sur les profils Wi-Fi, consultez [Ajouter des paramètres Wi-Fi pour les appareils Windows 10 et versions ultérieures dans Intune](../configuration/wi-fi-settings-windows.md).

S’applique à :
- Windows 10 et versions ultérieures

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Nouveaux paramètres ExchangeActiveSync lors de la création d’un profil de configuration de périphérique de messagerie sur des appareils iOS<!-- 4892824  --> 
Sur les appareils iOS/iPados, vous pouvez configurer la connectivité de messagerie dans un profil de configuration d’appareil (configuration de l'**appareil** > **profils** > **créer un profil** > **iOS/iPad** pour la plateforme > la **messagerie** pour le type de profil). 

De nouveaux paramètres ExchangeActiveSync sont disponibles, notamment :
- Choisissez les services à synchroniser (ou bloquer la synchronisation), tels que la messagerie, le calendrier et les contacts.
- Autoriser (ou bloquer) les utilisateurs à modifier les paramètres de synchronisation de ces services sur leurs appareils. 

Pour afficher les paramètres actuels, accédez à la page [paramètres de profil de messagerie pour les appareils iOS dans Intune](../configuration/email-settings-ios.md).

S’applique à :
- iOS 13.0 et ultérieur
- iPadOS 13.0 et ultérieur

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Empêcher les utilisateurs d’ajouter des comptes Google personnels au propriétaire des appareils Android Enterprise et à des appareils dédiés<!-- 5353228  -->
Vous pouvez empêcher les utilisateurs de créer des comptes Google personnels sur Android Enterprise Device owner et dédiés (**configuration** des appareils > **profils** > **créer un profil** > **Android Enterprise** pour la plateforme > propriétaire de l' **appareil uniquement > des restrictions d’appareil** pour le type de profil > **paramètres utilisateurs et comptes**).

Pour voir les paramètres actuels que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Propriétaire d’appareil Android Entreprise
- Appareils dédiés Android Entreprise

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>La journalisation côté serveur pour les commandes Siri est supprimée dans le profil de restrictions d’appareil iOS<!-- 5468501  -->
Sur les appareils iOS, vous pouvez créer des profils de restriction d’appareil qui configurent la journalisation côté serveur pour les commandes Siri (configuration de l'**appareil** > **profils** > **créer un profil** > **iOS/iPad** pour la plateforme > **Restrictions d’appareil** pour le type de profil > les **applications intégrées**). Le paramètre **de journalisation côté serveur pour les commandes Siri** sera supprimé.

Ce paramètre sera supprimé de la console d’administration Intune. Ce paramètre n’a aucun effet sur l’appareil, même si les stratégies existantes pour lesquelles ce paramètre est configuré continuent à afficher le paramètre. Si vous souhaitez supprimer le paramètre des stratégies existantes, accédez à la stratégie, apportez une modification mineure, enregistrez-la et la stratégie sera mise à jour.

Pour voir les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils iOS et iPadOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

S’applique à :
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils



### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Modifier la valeur du nom de l’appareil pour les appareils AutoPilot<!-- 2640074  -->
Vous pouvez modifier la valeur du nom de l’appareil pour les appareils AutoPilot Azure AD joints. Pour ce faire, accédez à **Intune** > **inscription d’appareils** > **inscription windows** > **Windows AutoPilot** > **appareils** > Choisissez l’appareil > modifier la valeur du nom de l' **appareil** dans le volet droit > **Enregistrer**.

### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Modifier la valeur de balise de groupe pour les appareils AutoPilot<!-- 4816775 -->
Vous pouvez modifier la valeur de **balise de groupe** pour les appareils AutoPilot :

1. Sélectionnez **Intune** > **inscription d’appareils** > l' **inscription Windows** > **les appareils** > **Windows AutoPilot**.
1. Choisissez l’appareil.
1. Dans le volet de droite, modifiez la valeur de **balise de groupe** .
1. Sélectionnez **Enregistrer**.

### <a name="target-macos-user-groups-to-require-jamf-management---4061739---"></a>Cibler des groupes d’utilisateurs macOS pour exiger la gestion de JAMF<!-- 4061739 -->
Vous pourrez cibler des groupes d’utilisateurs spécifiques pour que les appareils macOS puissent être gérés par JAMF. Cette cible vous permet d’appliquer l’intégration de la conformité JAMF à un sous-ensemble d’appareils macOS, tandis que d’autres appareils continuent d’être gérés par Intune. Le ciblage vous permettra également de migrer progressivement les appareils des utilisateurs d’un système de gestion des appareils mobiles (MDM) vers l’autre.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Applications Intune

### <a name="improved-macos-enrollment-experience-in-company-portal---5074349----"></a>Amélioration de l’expérience d’inscription macOS dans Portail d’entreprise<!-- 5074349  -->
L’Portail d’entreprise pour l’expérience d’inscription macOS aura un processus d’inscription plus simple qui s’alignera plus étroitement sur le Portail d’entreprise pour l’expérience d’inscription iOS. Les utilisateurs des appareils verront les éléments suivants :  

* Une interface utilisateur plus élégante.  
* Liste de contrôle d’inscription améliorée.  
* Instructions claires sur la façon d’inscrire leurs appareils.  
* Options de dépannage améliorées.  

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Analyse et résolution des problèmes

### <a name="centralized-audit-logs--5603185-5697164--"></a>Journaux d’audit centralisés<!--5603185, 5697164-->
Une nouvelle expérience de journal d’audit centralisée collecte les journaux d’audit de toutes les catégories dans une seule page. You’l être en mesure de filtrer les journaux pour obtenir les données que vous recherchez. Pour afficher les journaux d’audit, accédez à **administration des clients** > **journaux d’audit**. Pour plus d’informations, consultez [modification à venir des journaux d’audit dans Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

### <a name="duplicate-custom-or-built-in-roles---1081938---"></a>Rôles personnalisés ou intégrés en double<!-- 1081938 -->
Vous pourrez copier des rôles intégrés et personnalisés. Pour ce faire, accédez à **Intune** > **rôles** > **tous les rôles** > choisissez un rôle dans la liste > **en double**. Veillez à entrer un nouveau nom unique.

<!-- ***********************************************-->

## <a name="security"></a>Sécurité

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Utiliser des profils de certificat PKCS pour approvisionner des appareils avec des certificats<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
Vous pouvez utiliser un profil de certificat PKCS pour émettre des certificats pour les appareils, en développant la prise en charge actuelle des certificats basés sur l’utilisateur. Les certificats basés sur des appareils seront pris en charge par les plateformes Android, iOS et Windows, et peuvent être utilisés pour les profils Wi-Fi et VPN.

<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).


