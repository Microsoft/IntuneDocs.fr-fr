---
title: Paramètres de messagerie Android et Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Créez des profils de messagerie de configuration d’appareil qui utilisent des serveurs Exchange et récupèrent des attributs auprès d’Azure Active Directory. Activez SSL ou SMIME, authentifiez les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe, et synchronisez la messagerie et les planifications sur les appareils Android et avec profil professionnel Android en utilisant Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b96363d679a6f09327bf9a1b46421e786d1956a8
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316880"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Paramètres des appareils Android et Android Enterprise permettant de configurer la messagerie, l’authentification et la synchronisation dans Intune

Cet article liste et décrit les différents paramètres de messagerie que vous pouvez contrôler sur les appareils Android et Android Enterprise. Dans votre solution de gestion des appareils mobiles, définissez ces paramètres pour configurer un serveur de messagerie, utiliser SSL pour chiffrer les e-mails et bien plus encore.

En tant qu’administrateur Intune, vous pouvez créer et affecter des paramètres de messagerie aux appareils Android suivants :

- Android Samsung Knox Standard
- Android Entreprise

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](email-settings-configure.md).

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange.
- **Nom du compte** : entrez le nom d’affichage du compte de messagerie. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (AAD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :
  - **Nom principal de l’utilisateur** : Obtient le nom, par exemple `user1` ou `user1@contoso.com`
  - **Nom d’utilisateur** : obtient seulement le nom, par exemple `user1`
  - **Nom de compte SAM** : nécessite le domaine, par exemple `domain\user1`. Le nom de compte SAM peut être utilisé seulement avec les appareils Android. Android Entreprise n’est pas pris en charge.

    Entrez également :  
    - **Source du nom de domaine d’utilisateur** : choisissez **AAD** (Azure Active Directory) ou **Personnalisé**.

      Quand vous choisissez d’obtenir les attributs auprès **d’AAD**, entrez :
      - **Attribut de nom de domaine d’utilisateur dans AAD** : choisissez d’obtenir l’attribut **Nom de domaine complet** ou **Nom NetBIOS** de l’utilisateur

      Quand vous choisissez d’utiliser des attributs **Personnalisés**, entrez :
      - **Nom de domaine personnalisé à utiliser** : entrez une valeur utilisée par Intune pour le nom de domaine, par exemple `contoso.com` ou `contoso`

- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Sélectionnez **Nom d’utilisateur principal** (`user1@contoso.com` ou `user1`) pour utiliser le nom principal complet comme adresse e-mail, ou **Adresse SMTP principale** (`user1@contoso.com`) pour utiliser l’adresse SMTP principale pour vous connecter à Exchange.

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
  - **Contacts**
  - **Calendrier**
  - **Tâches**

## <a name="android-enterprise"></a>Android Entreprise

- **Application de messagerie** : sélectionnez **Gmail** ou **Nine Work**
- **Serveur de messagerie** : nom d’hôte de votre serveur Exchange.
- **Attribut de nom d’utilisateur d’AAD** : il s’agit de l’attribut dans Active Directory (AD) ou Azure AD qui doit être utilisé pour générer le nom d’utilisateur de ce profil de messagerie. Sélectionnez **Adresse SMTP principale**, comme user1@contoso.com ou **Nom d’utilisateur principal**, comme user1 ou user1@contoso.com.
- **Attribut d’adresse e-mail d’AAD** : Façon dont l’adresse de messagerie de l’utilisateur est générée sur chaque appareil. Sélectionnez le **Nom d’utilisateur principal** pour utiliser le nom principal complet en tant qu’adresse de messagerie ou **nom d’utilisateur**.
- **Méthode d’authentification** : Sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez créé précédemment pour authentifier la connexion Exchange.
- **SSL** : Utilisez la communication SSL (Secure Sockets Layer) pour envoyer et recevoir des e-mails, et communiquer avec le serveur Exchange.
- **Nombre d’e-mails à synchroniser** : sélectionnez le nombre de jours d’e-mails à synchroniser ou sélectionnez **Illimité** pour synchroniser tous les e-mails disponibles.
- **Type de contenu à synchroniser** (Nine Work uniquement) : sélectionnez les types de contenu à synchroniser sur les appareils. L’option **Non configuré** désactive ce paramètre. Si l’option **Non configuré** est sélectionnée et qu’un utilisateur final active la synchronisation sur l’appareil, la synchronisation est désactivée à nouveau quand l’appareil se synchronise avec Intune (dans la mesure où la stratégie est réitérée). 

  Vous pouvez synchroniser le contenu suivant : 
  - **Contacts**
  - **Calendrier**
  - **Tâches**

## <a name="next-steps"></a>Étapes suivantes
[Configurer les paramètres de messagerie dans Intune](email-settings-configure.md)
