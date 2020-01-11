---
title: Paramètres de messagerie Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Créez des profils de messagerie de configuration d’appareil qui utilisent des serveurs Exchange et récupèrent des attributs auprès d’Azure Active Directory. Activez SSL ou SMIME, authentifiez les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe et synchronisez les e-mails et les planifications sur les appareils avec profil professionnel Android en utilisant Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc86e82f189377d63422cc3306b8554637164b0f
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206429"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Paramètres des appareils Android Enterprise permettant de configurer les e-mails, l’authentification et la synchronisation dans Intune



Cet article liste et décrit les différents paramètres de messagerie que vous pouvez contrôler sur les appareils Android Entreprise. Dans votre solution de gestion des appareils mobiles, définissez ces paramètres pour configurer un serveur de messagerie, utiliser SSL pour chiffrer les e-mails et bien plus encore.

En tant qu’administrateur Intune, vous pouvez créer et affecter des paramètres de messagerie aux appareils Android Enterprise dans le profil professionnel.

Pour plus d’informations sur les profils de messagerie dans Intune, consultez [Configurer les paramètres de messagerie](email-settings-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

Créez un [profil de configuration d’appareil](email-settings-configure.md#create-a-device-profile) (choisissez le profil professionnel) ou créez une [stratégie de configuration d’application](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android Entreprise

- **Application de messagerie** : sélectionnez **Gmail** ou **Nine Work**
- **Serveur de messagerie** : nom d’hôte de votre serveur Exchange. Par exemple, entrez `outlook.office365.com`.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (Azure AD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :

  - **Nom principal de l’utilisateur** : Obtient le nom, par exemple `user1` ou `user1@contoso.com`
  - **Nom d’utilisateur** : obtient seulement le nom, par exemple `user1`

- **Attribut d’adresse e-mail d’AAD** : Ce nom est l’attribut de messagerie obtenu par Intune auprès d’Azure AD. Intune génère dynamiquement l’adresse e-mail utilisée par ce profil. Les options disponibles sont les suivantes :
  - **Nom d’utilisateur principal** :  utilise le nom principal complet (par exemple, `user1@contoso.com` ou `user1`) comme adresse e-mail.
  - **Adresse SMTP principale** : utilise l’adresse SMTP principale (par exemple, `user1@contoso.com`) pour la connexion à Exchange.

- **Méthode d’authentification** : sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez préalablement créé pour authentifier la connexion Exchange.
- **SSL** : choisissez **Activer** pour utiliser une communication SSL (Secure Sockets Layer) afin d’envoyer et de recevoir des e-mails, et de communiquer avec le serveur Exchange.
- **Nombre d’e-mails à synchroniser** : choisissez la quantité d’e-mails à synchroniser. Vous pouvez aussi sélectionner **Illimité** pour synchroniser tous les e-mails disponibles.
- **Type de contenu à synchroniser** (Nine Work uniquement) : choisissez les données à synchroniser sur les appareils. Les options disponibles sont les suivantes :
  - **Contacts** : choisissez **Activer** pour autoriser les utilisateurs finaux à synchroniser les contacts sur leurs appareils.
  - **Calendrier** : choisissez **Activer** pour autoriser les utilisateurs finaux à synchroniser l’agenda sur leurs appareils.
  - **Tâches** : choisissez **Activer** pour autoriser les utilisateurs finaux à synchroniser les tâches sur leurs appareils.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils de messagerie pour des appareils [Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 et ultérieur](email-settings-windows-10.md) et [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
