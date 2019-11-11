---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182929"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>En développement pour Microsoft Intune - Novembre 2019

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Prise en charge S/MIME pour Microsoft Outlook Mobile <!-- 2669398  -->
Intune prendra en charge la diffusion de certificats de chiffrement et de signature S/MIME qui peuvent être utilisés avec Outlook Mobile sur iOS et Android. Pour obtenir des informations connexes, consultez [paramètres de messagerie pour les appareils iOS](~/configuration/email-settings-ios.md) et [paramètres de messagerie pour les appareils Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Prise en charge des paramètres personnalisés pour les applications macOS <!-- 4736278  -->
Intune prend en charge les paramètres personnalisés, ce qui vous permet d’ajouter des clés et des valeurs spécifiques à un fichier de liste de propriétés de préférences (. plist) existant pour configurer les applications macOS et l’appareil. Toutes les applications ne prennent pas en charge les préférences gérées et, dans certains cas, seuls des paramètres spécifiques peuvent être gérés. Les paramètres sont déployés uniquement via le canal de l’appareil. Vous ne devez télécharger que des fichiers de liste de propriétés ou des fichiers. XML qui ciblent les paramètres de canal de l’appareil.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Valeur du type d’affectation dans Windows Portail d’entreprise <!-- 5459950  -->
La page **applications installées** de l’application portail d’entreprise Windows est mise à jour. La colonne **type d’affectation** de la page **applications installées** a été mise à jour pour être appelée « obligatoire pour votre organisation ». Les valeurs possibles sont **Oui** ou **non** pour désigner les applications requises et disponibles. Cette modification est apportée en réponse à une certaine confusion de l’utilisateur final. Pour plus d’informations sur le portail d’entreprise Windows, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Exécuter des applications Win32 sur des appareils Windows 10 en mode S <!-- 3747604  --> 
Vous pouvez installer et exécuter des applications Win32 sur des appareils gérés en mode Windows 10 S. Créez une ou plusieurs stratégies supplémentaires pour le mode S en utilisant les outils Windows Defender application Control (WDAC) PowerShell. Utilisez le portail de signature Device Guard pour signer les stratégies supplémentaires. Ensuite, chargez et distribuez les stratégies via Intune. 

Dans Intune, vous trouverez cette fonctionnalité en sélectionnant **applications clientes**  >  les**stratégies supplémentaires Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Définir la disponibilité de l’application en fonction d’une date et d’une heure <!-- 3510685  -->
En tant qu’administrateur, vous pouvez configurer l’heure de début et l’échéance d’une application requise. À l’heure de début, l’extension de gestion Intune télécharge le contenu de l’application et le met en cache. L’application sera installée à l’heure d’échéance. Pour les applications disponibles, l’heure de début indiquera quand l’application sera visible dans Portail d’entreprise. 

Pour définir la disponibilité des applications en fonction de la date et de l’heure :

1. Dans Intune, sélectionnez **Applications clientes** > **Applications**. 
1. Sélectionnez une application dans la liste ou ajoutez-en une en sélectionnant **Ajouter**. 
1. Dans le panneau de l’application, sélectionnez **affectations** > **Ajouter un groupe**. 
1. Définissez le **type d’affectation** sur **obligatoire** , puis sélectionnez **groupes inclus**. 
1. Définissez **rendre cette application obligatoire pour tous les utilisateurs** sur **Oui**. 
1. Sélectionnez **modifier** pour modifier les options de l' **expérience utilisateur final** . 
1. Dans le panneau **expérience utilisateur final** , définissez le **temps disponible du logiciel** en fonction des besoins. 

Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Exiger le redémarrage des applications Win32 <!-- 3136567  -->
Vous pouvez exiger qu’une application Win32 redémarre après une installation réussie. Vous pouvez choisir la durée (période de grâce) avant le redémarrage.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Afficher les notifications de l’application Portail d’entreprise sur Windows <!-- 1808082  -->
Nous allons mettre à jour l’application Portail d’entreprise sur les appareils Windows pour afficher les notifications Toast aux utilisateurs, même lorsque l’application est fermée. La mise à jour affiche les notifications pour les applications disponibles uniquement lorsque l’état de l’installation est terminé ou a échoué. L’application Portail d’entreprise n’affiche pas de notifications pour les applications requises.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Afficher les messages d’état d’installation de l’application Portail d’entreprise <!-- 2514416  -->
L’application Portail d’entreprise affiche des messages d’état d’installation d’application supplémentaires pour les utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.
- L’application a été correctement installée mais nécessite un redémarrage.
- L’application est en cours d’installation, mais nécessite un redémarrage pour continuer.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation <!-- 2576686 -->
L’application Intune sur des appareils Android et iOS vous permettra de contrôler le contenu de la notification d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur l’Application, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Utiliser des certificats PKCS avec des profils Wi-Fi sur les appareils Windows 10 et versions ultérieures <!-- 3246388  -->
Actuellement, vous pouvez authentifier les profils Wi-Fi Windows avec des certificats SCEP (configuration de l'**appareil** > **profils** > **créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme > **Wi-Fi** pour type de profil > **Enterprise** > **type EAP**). Vous pouvez utiliser des certificats PKCS avec vos profils Wi-Fi Windows. Cette fonctionnalité permet aux utilisateurs d’authentifier des profils Wi-Fi à l’aide de profils de certificat PKCS nouveaux ou existants dans votre locataire. 

Pour plus d’informations sur les profils Wi-Fi, consultez [Ajouter des paramètres Wi-Fi pour les appareils Windows 10 et versions ultérieures dans Intune](../configuration/wi-fi-settings-windows.md).

S’applique à :
- Windows 10 et versions ultérieures

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Nouveaux paramètres ExchangeActiveSync lors de la création d’un profil de configuration de périphérique de messagerie sur des appareils iOS <!-- 4892824  --> 
Sur les appareils iOS/iPados, vous pouvez configurer la connectivité de messagerie dans un profil de configuration d’appareil (configuration de l'**appareil** > **profils** > **créer un profil** > **iOS/iPad** pour la plateforme > la **messagerie** pour le type de profil). 

De nouveaux paramètres ExchangeActiveSync sont disponibles, notamment :
- Choisissez les services à synchroniser (ou bloquer la synchronisation), tels que la messagerie, le calendrier et les contacts.
- Autoriser (ou bloquer) les utilisateurs à modifier les paramètres de synchronisation de ces services sur leurs appareils. 

Pour afficher les paramètres actuels, accédez à la page [paramètres de profil de messagerie pour les appareils iOS dans Intune](../configuration/email-settings-ios.md).

S’applique à :
- iOS 13.0 et ultérieur
- iPadOS 13.0 et ultérieur

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Empêcher les utilisateurs d’ajouter des comptes Google personnels au propriétaire des appareils Android Enterprise et à des appareils dédiés <!-- 5353228  -->
Vous pouvez empêcher les utilisateurs de créer des comptes Google personnels sur Android Enterprise Device owner et dédiés (**configuration** des appareils > **profils** > **créer un profil** > **Android Enterprise** pour la plateforme > propriétaire de l' **appareil uniquement > des restrictions d’appareil** pour le type de profil > **paramètres utilisateurs et comptes**).

Pour voir les paramètres actuels que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :
- Propriétaire d’appareil Android Entreprise
- Appareils dédiés Android Entreprise

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>La journalisation côté serveur pour les commandes Siri est supprimée dans le profil de restrictions d’appareil iOS <!-- 5468501  -->
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

1. Sélectionnez **Intune** > **inscription d’appareils** > **l'inscription Windows** > **Windows AutoPilot** > **les appareils**.
1. Choisissez l’appareil.
1. Dans le volet de droite, modifiez la valeur de **balise de groupe** .
1. Sélectionnez **Enregistrer**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Cibler des groupes d’utilisateurs macOS pour exiger la gestion de JAMF <!-- 4061739 -->
Vous pourrez cibler des groupes d’utilisateurs spécifiques pour que les appareils macOS puissent être gérés par JAMF. Cette cible vous permet d’appliquer l’intégration de la conformité JAMF à un sous-ensemble d’appareils macOS, tandis que d’autres appareils continuent d’être gérés par Intune. Le ciblage vous permettra également de migrer progressivement les appareils des utilisateurs d’un système de gestion des appareils mobiles (MDM) vers l’autre.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Applications Intune

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Amélioration de l’expérience d’inscription macOS dans Portail d’entreprise <!-- 5074349  -->
L’Portail d’entreprise pour l’expérience d’inscription macOS aura un processus d’inscription plus simple qui s’alignera plus étroitement sur le Portail d’entreprise pour l’expérience d’inscription iOS. Les utilisateurs des appareils verront les éléments suivants :  

* Une interface utilisateur plus élégante.  
* Liste de contrôle d’inscription améliorée.  
* Instructions claires sur la façon d’inscrire leurs appareils.  
* Options de dépannage améliorées.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Conception de liste de contrôle améliorée dans Portail d’entreprise application pour Android<!-- 5550857  -->
La liste de vérification de l’installation de l’application Portail d’entreprise pour Android sera mise à jour avec une conception légère et de nouvelles icônes. Les modifications seront alignées sur les mises à jour récentes apportées à l’application Portail d’entreprise pour iOS.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Analyse et résolution des problèmes

### <a name="updated-support-experience-------5012398------"></a>Expérience de support mise à jour   <!--  5012398    -->
Dans le cadre des améliorations continues, nous allons mettre à jour l’expérience de prise en charge dans la console pour Intune.  Nous allons améliorer la recherche et les commentaires dans la console pour les problèmes courants, et nous allons simplifier le flux de travail pour contacter le support technique.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Rôles personnalisés ou intégrés en double <!-- 1081938 -->
Vous pourrez copier des rôles intégrés et personnalisés. Pour ce faire, accédez à **Intune** > **rôles** > **tous les rôles** > choisissez un rôle dans la liste > **en double**. Veillez à entrer un nouveau nom unique.

<!-- ***********************************************-->

## <a name="security"></a>Sécurité

### <a name="bitlocker-key-rotation--------2564951--------"></a>Rotation de clé BitLocker     <!-- 2564951      -->
Vous pouvez utiliser Intune pour faire pivoter les clés de récupération BitLocker pour les appareils gérés qui exécutent Windows version 1909 ou ultérieure. 

<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur les développements récents, consultez [Nouveautés sur Microsoft Intune](whats-new.md).
