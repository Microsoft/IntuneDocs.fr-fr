---
title: Paramètres de courrier Android dans Microsoft Intune – Azure | Microsoft Docs
description: Créez des profils de messagerie de configuration d’appareil qui utilisent des serveurs Exchange et récupèrent des attributs auprès d’Azure Active Directory. Activez SSL ou SMIME, authentifiez les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe et synchronisez la messagerie et les agendas sur les appareils Android Samsung Knox avec Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a1bc53e0f05818b28bbd975e0de5cf5c9368afb
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512855"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Paramètres des appareils Android permettant de configurer la messagerie, l’authentification et la synchronisation dans Intune

Cet article liste et décrit les différents paramètres de courrier que l’on peut contrôler sur les appareils Android Samsung Knox dans Intune. Dans votre solution de gestion des appareils mobiles, définissez ces paramètres pour configurer un serveur de messagerie, utiliser SSL pour chiffrer les e-mails et bien plus encore.

En tant qu’administrateur Intune, vous pouvez créer et affecter des paramètres de courrier aux appareils Android Samsung Knox Standard.

Pour plus d’informations sur les profils de courrier dans Intune, voir [Configurer les paramètres de courrier](email-settings-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange. Par exemple, entrez `outlook.office365.com`.
- **Nom du compte** : entrez le nom d’affichage du compte de messagerie. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (Azure AD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :
  - **Nom principal de l’utilisateur** : Obtient le nom, par exemple `user1` ou `user1@contoso.com`
  - **Nom d’utilisateur** : obtient seulement le nom, par exemple `user1`
  - **Nom de compte SAM** : nécessite le domaine, par exemple `domain\user1`. Le nom de compte SAM n’est utilisé qu’avec les appareils Android.

    Entrez également :  
    - **Source du nom de domaine d’utilisateur** : choisissez **AAD** (Azure Active Directory) ou **Personnalisé**.

      Quand vous choisissez d’obtenir les attributs auprès **d’AAD**, entrez :
      - **Attribut de nom de domaine d’utilisateur dans AAD** : choisissez d’obtenir l’attribut **Nom de domaine complet** ou **Nom NetBIOS** de l’utilisateur

      Quand vous choisissez d’utiliser des attributs **Personnalisés**, entrez :
      - **Nom de domaine personnalisé à utiliser** : entrez une valeur utilisée par Intune pour le nom de domaine, par exemple `contoso.com` ou `contoso`

- **Attribut d’adresse e-mail d’AAD** : Ce nom est l’attribut de messagerie obtenu par Intune auprès d’Azure AD. Intune génère dynamiquement l’adresse e-mail utilisée par ce profil. Les options disponibles sont les suivantes :
  - **Nom d’utilisateur principal** :  utilise le nom principal complet (par exemple, `user1@contoso.com` ou `user1`) comme adresse e-mail.
  - **Adresse SMTP principale** : utilise l’adresse SMTP principale (par exemple, `user1@contoso.com`) pour la connexion à Exchange.

- **Méthode d’authentification** : Sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez préalablement créé pour authentifier la connexion Exchange.

### <a name="security-settings"></a>Paramètres de sécurité

- **SSL** : Utilisez la communication SSL (Secure Sockets Layer) pour envoyer et recevoir des e-mails, et communiquer avec le serveur Exchange.
- **S/MIME** : Envoyez des messages électroniques en utilisant le chiffrement S/MIME.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez préalablement créé pour authentifier la connexion Exchange.

### <a name="synchronization-settings"></a>Paramètres de synchronisation

- **Nombre d’e-mails à synchroniser** : sélectionnez le nombre de jours d’e-mails à synchroniser ou sélectionnez **Illimité** pour synchroniser tous les e-mails disponibles.
- **Planification de la synchronisation** : sélectionnez la planification selon laquelle les appareils synchronisent les données à partir du serveur Exchange. Vous pouvez également sélectionner **À mesure que les messages arrivent** pour synchroniser les données quand elles arrivent ou **Manuel** pour que ce soit l’utilisateur de l’appareil qui lance la synchronisation.

### <a name="content-sync-settings"></a>Paramètres de synchronisation du contenu

- **Type de contenu à synchroniser** : sélectionnez les types de contenu à synchroniser sur les appareils. L’option **Non configuré** désactive ce paramètre. Si l’option **Non configuré** est sélectionnée et qu’un utilisateur final active la synchronisation sur l’appareil, la synchronisation est désactivée à nouveau quand l’appareil se synchronise avec Intune (dans la mesure où la stratégie est réitérée). 

  Vous pouvez synchroniser le contenu suivant :  
  - **Contacts** : choisissez **Activer** pour autoriser les utilisateurs finaux à synchroniser les contacts sur leurs appareils.
  - **Calendrier** : choisissez **Activer** pour autoriser les utilisateurs finaux à synchroniser l’agenda sur leurs appareils.
  - **Tâches** : choisissez **Activer** pour autoriser les utilisateurs finaux à synchroniser les tâches sur leurs appareils.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également créer des profils de messagerie pour [Android Enterprise – Profil professionnel](email-settings-android-enterprise.md), [iOS/iPadOS](email-settings-ios.md), [Windows 10 (et versions ultérieures)](email-settings-windows-10.md) et [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
