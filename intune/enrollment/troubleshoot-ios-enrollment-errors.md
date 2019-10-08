---
title: Résolution des problèmes liés à l’accord de mise en œuvre de périphériques iOS dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggestions pour la résolution des problèmes les plus courants lors de l’inscription d’appareils iOS dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a02e403fdba34b576aa90b82062b7a602cbb517
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735686"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Résoudre des problèmes liés à l’accord de mise en œuvre de périphériques iOS dans Microsoft Intune

Cet article aide les administrateurs Intune à comprendre et à résoudre les problèmes liés à l’inscription d’appareils iOS dans Intune.

## <a name="prerequisites"></a>Prérequis

Avant de commencer le dépannage, il est important de recueillir des informations de base. Ces informations peuvent vous aider à mieux comprendre le problème et à réduire le temps nécessaire pour trouver une solution.

Collectez les informations suivantes sur le problème :

- Quel est le message d’erreur exact ?
- Où s’affiche le message d’erreur ?
- Quand le problème a-t-il commencé ? L’inscription a-t-elle déjà fonctionné ?
- Quelle plateforme (Android, iOS, Windows) rencontre le problème ?
- Combien d’utilisateurs sont affectés ? Tous les utilisateurs sont-ils affectés ou juste quelques-uns ?
- Combien d’appareils sont affectés ? Tous les appareils sont-ils affectés ou simplement certains ?
- Qu’est-ce que l’autorité MDM ? Si c’est System Center Configuration Manager, quelle version de Configuration Manager utilisez-vous ?
- Comment l’inscription est-elle effectuée ? S’agit-il d’un BYOD (Bring Your Own Device) ou d’Apple Programme d’inscription des appareils (DEP) avec des profils d’inscription ?

## <a name="error-messages"></a>Messages d'erreur

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Échec de l’installation du profil. Une erreur réseau s'est produite.

**Cause :** Il y a un problème non spécifié avec iOS sur l’appareil.

#### <a name="resolution"></a>Résolution

1. Pour éviter la perte de données dans les étapes suivantes (la restauration d’iOS supprime toutes les données sur l’appareil), veillez à sauvegarder vos données.
2. Mettez l’appareil en mode de récupération, puis restaurez-le. Veillez à le configurer en tant que nouvel appareil. Pour plus d’informations sur la restauration des appareils iOS, consultez [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Réinscrire le périphérique.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Échec de l’installation du profil. Impossible d'établir une connexion au serveur.

**Cause :** Votre client Intune est configuré pour autoriser uniquement les appareils d’entreprise. 

#### <a name="resolution"></a>Résolution
1. Connectez-vous au portail Azure.
2. Sélectionnez **Plus de services**, recherchez Intune, puis sélectionnez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **restrictions de type d’appareil**, sélectionnez la restriction que vous souhaitez définir **> Propriétés** > **Sélectionnez plateformes** > sélectionnez **autoriser** pour **iOS**, puis cliquez sur **OK**.
5. Sélectionnez **configurer des plateformes**, sélectionnez **autoriser** pour les appareils iOS personnels, puis cliquez sur **OK**.
6. Réinscrire le périphérique.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Ce service n’est pas pris en charge. Aucune stratégie d’accord de mise en œuvre.

**Cause**: un certificat Push MDM Apple n’est pas configuré dans Intune ou le certificat n’est pas valide. 

#### <a name="resolution"></a>Résolution

- Si le certificat Push MDM n’est pas configuré, suivez les étapes de la section [récupération d’un certificat Push MDM Apple](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Si le certificat Push MDM n’est pas valide, suivez les étapes décrites dans [renouveler le certificat Push MDM Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Le Portail d'entreprise est temporairement non disponible. L’application Portail d’entreprise a rencontré un problème. Contactez votre administrateur système si le problème persiste.

**Cause :** L’application Portail d’entreprise est obsolète ou endommagée.

#### <a name="resolution"></a>Résolution
1. Supprimez l’application Portail d’entreprise du périphérique.
2. Téléchargez l’application **Portail d’entreprise Microsoft Intune** à partir de l’**App Store** et installez-la.
3. Réinscrire le périphérique.

### <a name="device-cap-reached"></a>Nombre maximal d'appareils atteint

**Cause :** L’utilisateur tente d’inscrire plus d’appareils que la limite d’inscription de l’appareil.

#### <a name="resolution"></a>Résolution
1. Ouvrez le [portail d’administration Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) > **appareils** > **tous les appareils**, puis vérifiez le nombre d’appareils inscrits par l’utilisateur.
    > [!NOTE]
    > Vous devez également disposer de l’ouverture de session de l’utilisateur concerné sur le portail de l' [utilisateur Intune](https://portal.manage.microsoft.com/) et vérifier les appareils qui ont été inscrits. Il peut y avoir des appareils qui s’affichent dans le portail de l' [utilisateur Intune](https://portal.manage.microsoft.com/) , mais pas dans le [portail d’administration Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview), ces appareils sont également pris en compte dans la limite d’inscription des appareils.
2. Accédez à **administrateur** > **gestion des appareils mobiles** > **règles d’inscription** > Vérifiez la limite d’inscription des appareils. Par défaut, la limite est définie sur 15. 
3. Si le nombre d’appareils inscrits a atteint la limite, supprimez les appareils inutiles ou augmentez la limite d’inscription des appareils. Étant donné que chaque appareil inscrit utilise une licence Intune, nous vous recommandons de toujours supprimer d’abord les appareils inutiles.
4. Réinscrire le périphérique.

### <a name="workplace-join-failed"></a>Échec de la Workplace Join

**Cause :** L’application Portail d’entreprise est obsolète ou endommagée.  

#### <a name="resolution"></a>Résolution
1. Supprimez l’application Portail d’entreprise du périphérique.
2. Téléchargez l’application **Portail d’entreprise Microsoft Intune** à partir de l’**App Store** et installez-la.
3. Réinscrire le périphérique.

### <a name="user-license-type-invalid"></a>Type de licence utilisateur non valide

**Cause :** L’utilisateur qui essaie d’inscrire l’appareil ne dispose pas d’une licence Intune valide.

#### <a name="resolution"></a>Résolution
1. Accédez au [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home#/homepage), puis choisissez **utilisateurs** > **utilisateurs actifs**.
2. Sélectionnez le compte d’utilisateur affecté > **licences du produit** > **modifier**.
3. Vérifiez qu’une licence Intune valide est affectée à cet utilisateur.
4. Réinscrire le périphérique.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Nom de l’utilisateur non reconnu. Ce compte d’utilisateur n’est pas autorisé à utiliser Microsoft Intune. Contactez votre administrateur système si vous pensez que vous avez reçu ce message par erreur.

**Cause :** L’utilisateur qui essaie d’inscrire l’appareil ne dispose pas d’une licence Intune valide.

1. Accédez au [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home#/homepage), puis choisissez **utilisateurs** > **utilisateurs actifs**.
2. Sélectionnez le compte d’utilisateur affecté, puis choisissez **licences du produit** > **modifier**.
3. Vérifiez qu’une licence Intune valide est affectée à cet utilisateur.
4. Réinscrire le périphérique.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Échec de l’installation du profil. La nouvelle charge utile MDM ne correspond pas à l’ancienne charge utile.

**Cause :** Un profil de gestion est déjà installé sur l’appareil.

#### <a name="resolution"></a>Résolution

1. Ouvrez **paramètres** sur le périphérique iOS > **général** > **gestion des appareils**.
2. Appuyez sur le profil de gestion existant, puis sur **Supprimer la gestion**.
3. Réinscrire le périphérique.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Cause :** Le certificat Apple Push Notification Service (APNs) est manquant, non valide ou a expiré.

#### <a name="resolution"></a>Résolution
Vérifiez qu’un certificat APNs valide est ajouté à Intune. Pour plus d’informations, consultez [Configurer la gestion des périphériques iOS et Mac](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune). 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Cause :** Il y a un problème avec le certificat du service de notification push Apple (APNs) configuré dans Intune.

#### <a name="resolution"></a>Résolution
Renouvelez le certificat APNs, puis réinscrivez l’appareil.

> [!IMPORTANT]
> Veillez à renouveler le certificat APNs. Ne remplacez pas le certificat APNs. Si vous remplacez le certificat, vous devez réinscrire tous les appareils iOS dans Intune. 

- Pour renouveler le certificat APNs dans Intune autonome, consultez [renouveler le certificat Push MDM Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Pour renouveler le certificat APNs dans Intune Hybrid avec Configuration Manager, consultez [configurer la gestion des appareils hybrides iOS avec System Center Configuration Manager et Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).
- Pour renouveler le certificat APNs dans Office 365, consultez [créer un certificat APNs pour les appareils iOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>Connexion XPC_TYPE_ERROR non valide

Lorsque vous activez un appareil géré par DEP auquel est affecté un profil d’inscription, l’inscription échoue et vous recevez le message d’erreur suivant :

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Cause :** Il y a un problème de connexion entre l’appareil et le service Apple DEP.

#### <a name="resolution"></a>Résolution
Corrigez le problème de connexion ou utilisez une autre connexion réseau pour inscrire l’appareil. Vous devrez peut-être également contacter Apple si le problème persiste.


## <a name="other-issues"></a>Autres problèmes

### <a name="dep-enrollment-doesnt-start"></a>L’inscription DEP ne démarre pas
Lorsque vous activez un appareil géré par DEP auquel est affecté un profil d’inscription, le processus d’inscription Intune n’est pas initié.

**Cause :** Le profil d’inscription est créé avant le chargement du jeton DEP dans Intune.

#### <a name="resolution"></a>Résolution

1. Modifiez le profil d’inscription. Vous pouvez apporter des modifications au profil. L’objectif est de mettre à jour l’heure de modification du profil.
2. Synchroniser les appareils gérés par DEP : Ouvrez le portail Intune > **Admin** > **gestion des appareils mobiles** > **iOS** > **programme d’Inscription des appareils** > **Synchroniser maintenant**. Une demande de synchronisation est envoyée à Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>L’inscription DEP est bloquée au moment de la connexion de l’utilisateur
Lorsque vous activez un appareil géré par DEP auquel est affecté un profil d’inscription, le programme d’installation initial s’inscrit après que vous avez entré les informations d’identification.

**Cause :** L’authentification multifacteur (MFA) est activée. L’authentification multifacteur actuellement ne fonctionne pas lors de l’inscription sur les appareils DEP.

#### <a name="resolution"></a>Résolution
Désactivez MFA, puis réinscrivez l’appareil.

## <a name="next-steps"></a>Étapes suivantes

- [Résoudre les problèmes d’inscription d’appareils dans Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Posez une question sur le forum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consultez le blog de l’équipe de support Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consultez le blog Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
