---
title: Messages du Portail d’entreprise que les utilisateurs peuvent voir sur les appareils
titlesuffix: Microsoft Intune
description: Découvrez les différents messages que les utilisateurs finaux peuvent voir dans le Portail d’entreprise.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: aanavath
ms.suite: ems
ms.openlocfilehash: 3ed729e437fcdbc4352bf5fa8ceada4ddf336708
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Aider les utilisateurs finaux à comprendre les messages de l’application Portail d’entreprise

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> Les informations ci-après s’appliquent uniquement aux appareils équipés d’Android 6.0 ou d’une version ultérieure.

Découvrez les différents messages liés aux applications, que les utilisateurs finaux peuvent voir dans le Portail d’entreprise. Ces messages liés aux applications sont généralement affichés à différents moments du processus d’inscription. Découvrez où les messages s’affichent, ce qu’ils signifient et ce qui se passe si les utilisateurs refusent l’accès. Découvrez aussi comment mieux expliquer les messages aux utilisateurs.

- __Autoriser l’application Portail d’entreprise à passer et gérer des appels téléphoniques ?__
- __Autoriser l’application Portail d’entreprise à accéder aux photos, aux fichiers multimédias et aux fichiers de votre appareil ?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Autoriser l’application Portail d’entreprise à passer et gérer des appels téléphoniques ?

### <a name="where-it-appears"></a>Emplacement
Le message **Autoriser l’application Portail d’entreprise à passer et gérer des appels téléphoniques ?** s’affiche quand les utilisateurs appuient sur le bouton **Inscrire** de l’application Portail d’entreprise lorsqu’ils inscrivent leur appareil.

### <a name="what-it-means"></a>Signification
En acceptant cette invite, les utilisateurs autorisent l’envoi des numéros de téléphone et IMEI de leur appareil au service Intune. Ces numéros apparaîtront sur la page __Matériel__ de la console d’administration.

> [!NOTE]
> **L’application Portail d’entreprise ne passe et ne gère jamais d’appels téléphoniques !** Le texte du message est contrôlé par Google et ne peut pas être modifié.

Pour visualiser la page **Matériel**, vous devez accéder à **Groupes** > **Tous les appareils mobiles** > **Appareils**. Sélectionnez l’appareil de l’utilisateur et accédez à **Afficher les propriétés** > **Matériel**.

### <a name="what-happens-if-users-deny-access"></a>Ce qui se passe si les utilisateurs refusent l’accès
Si les utilisateurs refusent l’accès, ils peuvent continuer à utiliser l’application Portail d’entreprise et à inscrire leur appareil. Toutefois, les champs du numéro IMEI et du numéro de téléphone de l’appareil restent vides sur la page __Matériel__ de la console d’administration. La deuxième fois que les utilisateurs se connectent à l’application Portail d’entreprise après avoir refusé l’accès, le message affiche une case **Ne plus me demander** que les utilisateurs peuvent cocher pour faire cesser l’affichage de l’invite.

Si les utilisateurs autorisent, puis refusent par la suite l’accès, le message s’affiche la prochaine fois qu’ils se connectent à l’application Portail d’entreprise après l’inscription.

Si les utilisateurs décident par la suite d’autoriser l’accès, ils peuvent accéder à **Paramètres** > **Applications** > **Portail d’entreprise** > **Autorisations** > **Téléphone**, puis activer l’accès.

### <a name="how-to-explain-this-to-your-users"></a>Explication de ce mode de fonctionnement à vos utilisateurs
Pour plus d’informations, envoyez à vos utilisateurs la procédure [Inscrire un appareil Android dans Intune](/intune-user-help/enroll-your-device-in-intune-android).

## <a name="allow-company-portal-to-access-your-contacts"></a>Autoriser le portail d’entreprise à accéder à vos contacts ?

### <a name="where-it-appears"></a>Emplacement
Le message **Autoriser le Portail d’entreprise à accéder à vos contacts ?** s’affiche quand les utilisateurs appuient sur le bouton **Inscrire** de l’application Portail d’entreprise lorsqu’ils inscrivent leur appareil.

### <a name="what-it-means"></a>Signification
En acceptant cette invite, les utilisateurs autorisent Intune à créer leur compte professionnel et à gérer l’identité Azure Active Directory qui est enregistrée pour l’utilisateur sur l’appareil.

> [!NOTE]
> **Microsoft n’accède jamais à vos contacts !** Le texte du message est contrôlé par Google et ne peut pas être modifié.

### <a name="what-happens-if-users-deny-access"></a>Ce qui se passe si les utilisateurs refusent l’accès
S’ils refusent l’accès, leur appareil n’est pas inscrit dans Intune et ne peut donc pas être géré. La deuxième fois que les utilisateurs se connectent à l’application Portail d’entreprise après avoir refusé l’accès, le message affiche une case **Ne plus me demander** que les utilisateurs peuvent cocher pour demander l’arrêt de l’affichage de l’invite.

Si les utilisateurs autorisent, puis refusent par la suite l’accès, le message s’affiche la prochaine fois qu’ils se connectent à l’application Portail d’entreprise après l’inscription.

Si les utilisateurs décident par la suite d’autoriser l’accès, ils peuvent accéder à **Paramètres** > **Applications** > **Portail d’entreprise** > **Autorisations** > **Téléphone**, puis activer l’accès.

### <a name="how-to-explain-this-to-your-users"></a>Explication de ce mode de fonctionnement à vos utilisateurs
Pour plus d’informations, envoyez à vos utilisateurs la procédure [Inscrire un appareil Android dans Intune](/intune-user-help/enroll-your-device-in-intune-android).

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Autoriser l’application Portail d’entreprise à accéder aux photos, aux fichiers multimédias et aux fichiers de votre appareil ?

### <a name="where-it-appears"></a>Emplacement
Le message **Autoriser l’application Portail d’entreprise à accéder aux photos, aux fichiers multimédias et aux fichiers de votre appareil ?** s’affiche quand les utilisateurs appuient sur **Envoyer les données** pour envoyer les journaux à leur administrateur informatique.

### <a name="what-it-means"></a>Signification
En acceptant cette invite, les utilisateurs autorisent leur appareil à écrire des journaux de données sur la carte mémoire SD de l’appareil. Ceci permet également le déplacement de ces journaux via un câble USB.   

> [!NOTE]
> **L’application Portail d’entreprise n’accède jamais aux photos, aux fichiers multimédias ni aux fichiers des utilisateurs !** Le texte du message est contrôlé par Google et ne peut pas être modifié.

### <a name="what-happens-if-users-deny-access"></a>Ce qui se passe si les utilisateurs refusent l’accès
Si les utilisateurs refusent l’accès, ils peuvent toujours envoyer les journaux de données par e-mail, mais les journaux ne sont pas copiés sur la carte mémoire Secure Digital de l’appareil.

La deuxième fois que les utilisateurs se connectent à l’application Portail d’entreprise après le refus de l’accès, le message affiche une case **Ne plus me demander** que les utilisateurs peuvent cocher pour que le message ne s’affiche plus. Si les utilisateurs autorisent, puis refusent par la suite l’accès, le message s’affiche la prochaine fois qu’ils essaient d’envoyer les journaux. Cependant, si les utilisateurs décident par la suite d’autoriser l’accès, ils peuvent accéder à **Paramètres** > **Applications** > **Portail d’entreprise** > **Autorisations** > **Stockage**, puis activer l’autorisation.


### <a name="how-to-explain-this-to-your-users"></a>Explication de ce mode de fonctionnement à vos utilisateurs
Envoyez à vos utilisateurs la procédure [Envoyer des journaux à votre administrateur informatique par e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>Le support technique de votre entreprise a besoin de vous donner accès aux ressources d’entreprise

### <a name="where-it-appears"></a>Emplacement
Si vous n’avez pas ajouté l’application Portail d’entreprise à la liste **Applications autorisées** ou **Applications exemptes**, et qu’un utilisateur tente de se connecter, la connexion échoue. Le message suivant s’affiche :

> **Le support technique de votre entreprise a besoin de vous donner accès aux ressources d’entreprise**  
> Votre entreprise utilise des stratégies Protection des informations Windows pour protéger votre appareil. Le support technique de votre entreprise doit vérifier que ces stratégies permettent au Portail d’entreprise d’accéder à ces ressources.

### <a name="what-it-means"></a>Signification

Ajoutez l’application Portail d’entreprise à la liste **Applications autorisées** ou **Applications exemptes** dans la stratégie de protection des applications Windows Information Protection. Pour plus d’informations, consultez [Créer et déployer une stratégie de protection d’application Protection des informations Windows (WIP) avec Intune](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune).

### <a name="see-also"></a>Voir aussi
[Comment former vos utilisateurs finaux à Microsoft Intune](end-user-educate.md)
