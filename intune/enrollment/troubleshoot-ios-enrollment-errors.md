---
title: Résolution des problèmes d’inscription des appareils iOS/iPadOS dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggestions pour résoudre les problèmes les plus courants lors de l’inscription d’appareils iOS/iPadOS dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514317"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Résoudre les problèmes d’inscription des appareils iOS/iPadOS dans Microsoft Intune

Cet article aide les administrateurs Intune à comprendre et à résoudre les problèmes liés à l’inscription d’appareils iOS/iPadOS dans Intune.

## <a name="prerequisites"></a>Prérequis

Avant de commencer le dépannage, il est important de recueillir quelques informations de base. Ces informations peuvent vous aider à mieux comprendre le problème et à réduire le temps nécessaire pour trouver une solution.

Collectez les informations suivantes concernant le problème :

- Quel est le message d’erreur exact ?
- Où s’affiche le message d’erreur ?
- Quand le problème a-t-il commencé ? L’inscription a-t-elle déjà fonctionné ?
- Quelle plateforme (Android, iOS/iPadOS, Windows) rencontre le problème ?
- Combien d’utilisateurs sont affectés ? Tous les utilisateurs sont-ils affectés ou seulement quelques-uns ?
- Combien d’appareils sont affectés ? Tous les appareils sont-ils affectés ou seulement quelques-uns ?
- Qu’est-ce que l’autorité MDM ?
- Comment l’inscription est-elle effectuée ? S’agit-il d’une inscription BYOD (Bring Your Own Device) ou du Programme d’inscription d’appareils Apple (DEP) avec profils d’inscription ?

## <a name="error-messages"></a>Messages d’erreur

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Échec de l’installation du profil. Une erreur réseau s'est produite.

**Cause :** il y a un problème non spécifié avec iOS/iPadOS sur l’appareil.

#### <a name="resolution"></a>Résolution

1. Pour éviter la perte de données dans les étapes suivantes (la restauration d’iOS/iPadOS supprime toutes les données sur l’appareil), veillez à sauvegarder vos données.
2. Mettez l’appareil en mode de récupération, puis restaurez-le. Veillez à le configurer en tant que nouvel appareil. Pour plus d’informations sur la restauration des appareils iOS/iPadOS, consultez [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Réinscrire le périphérique.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Échec de l’installation du profil. Impossible d'établir une connexion au serveur.

**Cause :** votre client Intune est configuré pour autoriser uniquement les appareils appartenant à l’entreprise. 

#### <a name="resolution"></a>Résolution
1. Connectez-vous au portail Azure.
2. Sélectionnez **Plus de services**, recherchez Intune, puis sélectionnez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareil**, sélectionnez la restriction à définir > **Propriétés** > **Sélectionner des plateformes** > choisissez **Autoriser** pour **iOS**, puis cliquez sur **OK**.
5. Sélectionnez **Configurer des plateformes**, choisissez **Autoriser** pour les appareils iOS/iPadOS personnels, puis cliquez sur **OK**.
6. Réinscrire le périphérique.

**Cause :** les enregistrements CNAME requis dans DNS n’existent pas.

#### <a name="resolution"></a>Résolution
Créez des enregistrements de ressources CNAME DNS pour le domaine de votre entreprise. Par exemple, si le domaine de votre entreprise est contoso.com, créez un enregistrement CNAME dans DNS, qui redirige EnterpriseEnrollment.contoso.com vers EnterpriseEnrollment-s.manage.microsoft.com.

La création d’entrées CNAME dans DNS est facultative, mais les enregistrements CNAME facilitent l’inscription pour les utilisateurs. Si aucun enregistrement CNAME d’inscription n’est trouvé, les utilisateurs sont invités à taper le nom du serveur de gestion des appareils mobiles (enrollment.manage.microsoft.com).

S'il existe plusieurs domaines vérifiés, créez un enregistrement CNAME pour chaque domaine. Ces enregistrements doivent contenir les informations suivantes :

|TYPE|Nom d'hôte|Pointe vers|TTL|
|------|------|------|------|
|CNAME|enterpriseenrollment.domaine_entreprise.com|EnterpriseEnrollment-s.manage.microsoft.com|1 h|
|CNAME|EnterpriseRegistration.domaine_entreprise.com|EnterpriseRegistration.windows.net|1 h|

Si votre entreprise utilise plusieurs domaines pour les informations d’identification de l’utilisateur, créez des enregistrements CNAME pour chaque domaine.

> [!NOTE]
> La propagation des modifications DNS peut prendre jusqu’à 72 heures. Vous ne pouvez pas vérifier le changement au niveau du DNS dans Intune tant que l’enregistrement DNS ne s’est pas propagé.

**Cause :** vous inscrivez un appareil précédemment inscrit avec un autre compte d’utilisateur, et l’utilisateur précédent n’a pas été correctement supprimé d’Intune.

#### <a name="resolution"></a>Résolution
1. Annulez toute installation de profil en cours.
2. Ouvrez [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) dans Safari.
3. Réinscrire le périphérique.

> [!NOTE]
> Si l’inscription échoue toujours, supprimez les cookies dans Safari (ne bloquez pas les cookies), puis réinscrivez l’appareil.

**Cause :** l’appareil est déjà inscrit auprès d’un autre fournisseur MDM.

#### <a name="resolution"></a>Résolution
1. Ouvrez **Paramètres** sur l’appareil iOS/iPadOS, puis accédez à **Général > Gestion de l’appareil**.
2. Supprimez un profil de gestion existant.
3. Réinscrire le périphérique.

**Cause :** l’utilisateur qui tente d’inscrire l’appareil ne dispose pas d’une licence Microsoft Intune.

#### <a name="resolution"></a>Résolution
1. Accédez au [Centre d’administration Office 365](https://portal.office.com/adminportal/home#/homepage), puis choisissez **Utilisateurs > Utilisateurs actifs**.
2. Sélectionnez le compte d’utilisateur auquel vous souhaitez affecter une licence d’utilisateur Intune, puis choisissez **Licences du produit > Modifier**.
3. Positionnez le commutateur sur **On** pour la licence que vous souhaitez attribuer à cet utilisateur, puis choisissez **Enregistrer**.
4. Réinscrire le périphérique.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Ce service n’est pas pris en charge. Aucune stratégie d’accord de mise en œuvre.

**Cause** : un certificat Push MDM Apple n’est pas configuré dans Intune, ou le certificat n’est pas valide. 

#### <a name="resolution"></a>Résolution

- Si le certificat Push MDM n’est pas configuré, suivez les étapes de la section [Obtenir un certificat Push MDM Apple](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Si le certificat Push MDM n’est pas valide, suivez les étapes décrites dans [Renouveler un certificat Push MDM Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Le Portail d'entreprise est temporairement non disponible. L’application Portail d’entreprise a rencontré un problème. Contactez votre administrateur système si le problème persiste.

**Cause :** l’application Portail d’entreprise est obsolète ou endommagée.

#### <a name="resolution"></a>Résolution
1. Supprimez l’application Portail d’entreprise du périphérique.
2. Téléchargez l’application **Portail d’entreprise Microsoft Intune** à partir de l’**App Store** et installez-la.
3. Réinscrire le périphérique.
 > [!NOTE]
    > Cette erreur peut également se produire si l’utilisateur tente d’inscrire plus d’appareils que l’inscription de l’appareil n’est configurée pour autoriser. Suivez les étapes de résolution de la section **Nombre maximal d'appareils atteint** ci-dessous si le problème persiste.

### <a name="device-cap-reached"></a>Nombre maximal d'appareils atteint

**Cause :** l’utilisateur tente d’inscrire plus d’appareils que la limite d’inscription d’appareils.

#### <a name="resolution"></a>Résolution
1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Tous les appareils**, puis vérifiez le nombre d’appareils inscrits par l’utilisateur.
    > [!NOTE]
    > Vous devez également disposer de l’ouverture de session de l’utilisateur affecté sur le [portail de l’utilisateur Intune](https://portal.manage.microsoft.com/) et vérifier les appareils qui ont été inscrits. Certains appareils s’affichent dans le [portail de l'utilisateur Intune](https://portal.manage.microsoft.com/), mais pas dans le [portail d’administration Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Ces appareils sont également pris en compte dans la limite d’inscription des appareils.
2. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Restrictions d’inscription** > vérifiez la limite d’inscription des appareils. La limite par défaut est définie sur 15. 
3. Si vous avez atteint la limite d’appareils inscrits, supprimez les appareils inutiles ou augmentez la limite d’inscription des appareils. Comme chaque appareil inscrit utilise une licence Intune, nous vous recommandons de toujours commencer par supprimer les appareils inutiles.
4. Réinscrire le périphérique.

### <a name="workplace-join-failed"></a>Échec de Workplace Join

**Cause :** l’application Portail d’entreprise est obsolète ou endommagée.  

#### <a name="resolution"></a>Résolution
1. Supprimez l’application Portail d’entreprise du périphérique.
2. Téléchargez l’application **Portail d’entreprise Microsoft Intune** à partir de l’**App Store** et installez-la.
3. Réinscrire le périphérique.

### <a name="user-license-type-invalid"></a>Type de licence utilisateur non valide

**Cause :** l’utilisateur qui tente d’inscrire l’appareil ne dispose pas d’une licence Intune valide.

#### <a name="resolution"></a>Résolution
1. Accédez au [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home#/homepage), puis choisissez **Utilisateurs** > **Utilisateurs actifs**.
2. Sélectionnez le compte d'utilisateur affecté > **Licences de produit** > **Modifier**.
3. Vérifiez qu’une licence Intune valide est affectée à cet utilisateur.
4. Réinscrire le périphérique.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Nom de l’utilisateur non reconnu. Ce compte d’utilisateur n’est pas autorisé à utiliser Microsoft Intune. Contactez votre administrateur système si vous pensez que vous avez reçu ce message par erreur.

**Cause :** l’utilisateur qui tente d’inscrire l’appareil ne dispose pas d’une licence Intune valide.

1. Accédez au [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home#/homepage), puis choisissez **Utilisateurs** > **Utilisateurs actifs**.
2. Sélectionnez le compte d’utilisateur affecté, puis choisissez **Licences de produit** > **Modifier**.
3. Vérifiez qu’une licence Intune valide est affectée à cet utilisateur.
4. Réinscrire le périphérique.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Échec de l’installation du profil. La nouvelle charge utile MDM ne correspond pas à l’ancienne charge utile.

**Cause :** un profil de gestion est déjà installé sur l’appareil.

#### <a name="resolution"></a>Résolution

1. Ouvrez **Paramètres** sur l’appareil iOS/iPadOS > **Général** > **Gestion de l’appareil**.
2. Appuyez sur le profil de gestion existant, puis sur **Supprimer la gestion**.
3. Réinscrire le périphérique.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Cause :** le certificat Apple Push Notification Service (APNs) est manquant, non valide ou a expiré.

#### <a name="resolution"></a>Résolution
Vérifiez qu’un certificat APNs valide est ajouté à Intune. Pour plus d’informations, consultez [Configurer l’accord de mise en œuvre iOS/iPadOS](ios-enroll.md).

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Cause :** il y a un problème avec le certificat Apple Push Notification Service (APNs) configuré dans Intune.

#### <a name="resolution"></a>Résolution
Renouvelez le certificat APNs, puis réinscrivez l’appareil.

> [!IMPORTANT]
> Veillez à renouveler le certificat APNs. Ne remplacez pas le certificat APNs. Si vous remplacez le certificat, vous devez réinscrire tous les appareils iOS/iPadOS dans Intune. 

- Pour renouveler le certificat APNs dans Intune autonome, consultez [Renouveler un certificat Push MDM Apple](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Pour renouveler le certificat APNs dans Office 365, consultez [Créer un certificat APNs pour les appareils iOS/iPadOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>Connexion XPC_TYPE_ERROR non valide

Lorsque vous activez un appareil géré par DEP auquel est affecté un profil d’inscription, l’inscription échoue et vous recevez le message d’erreur suivant :

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Cause :** il y a un problème de connexion entre l’appareil et le service Apple DEP.

#### <a name="resolution"></a>Résolution
Corrigez le problème de connexion, ou utilisez une autre connexion réseau pour inscrire l’appareil. Vous devrez peut-être contacter Apple si le problème persiste.


## <a name="other-issues"></a>Autres problèmes

### <a name="dep-enrollment-doesnt-start"></a>L’inscription DEP ne démarre pas
Lorsque vous activez un appareil géré par DEP auquel est affecté un profil d’inscription, le processus d’inscription Intune n’est pas initié.

**Cause :** le profil d’inscription est créé avant le chargement du jeton DEP dans Intune.

#### <a name="resolution"></a>Résolution

1. Modifiez le profil d’inscription. Vous pouvez apporter des modifications au profil. L’objectif est de mettre à jour l’heure de modification du profil.
2. Synchroniser les appareils gérés par le programme DEP : dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **iOS** > **Inscription iOS** > **Jetons du programme d’inscription** > choisissez un jeton > **Synchroniser maintenant**. Une demande de synchronisation est envoyée à Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>L’inscription DEP se bloque lors de la connexion de l’utilisateur
Lorsque vous activez un appareil géré par DEP auquel est affecté un profil d’inscription, le programme d’installation initial se bloque après la saisie de vos informations d’identification.

**Cause :** l’authentification multifacteur (MFA) est activée. Actuellement, l’authentification multifacteur (MFA) ne fonctionne pas lors de l’inscription sur les appareils DEP.

#### <a name="resolution"></a>Résolution
Désactivez MFA, puis réinscrivez l’appareil.


## <a name="next-steps"></a>Étapes suivantes

- [Résoudre les problèmes d’inscription d’appareils dans Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Posez une question sur le forum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Lire le blog de l’équipe de support Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Lire le blog Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
