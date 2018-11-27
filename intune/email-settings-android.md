---
title: Paramètres de messagerie pour les appareils Android et avec profil professionnel Android dans Microsoft Intune - Azure | Microsoft Docs
description: Créez un profil de messagerie de configuration d’appareil qui utilise des serveurs Exchange et récupère des attributs auprès d’Azure Active Directory. Vous pouvez également activer SSL ou SMIME, authentifier les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe, et synchroniser la messagerie et les planifications sur les appareils Android et avec profil professionnel Android en utilisant Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b8ab8dfadb113d81922119a54aefcac43d15b5a1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187427"
---
# <a name="email-profile-settings-for-devices-running-android-and-android-enterprise---intune"></a>Paramètres de profil de messagerie pour les appareils exécutant Android et Android Entreprise - Intune

Utilisez les paramètres de profil de messagerie pour configurer vos appareils exécutant Android.

En tant qu’administrateur Intune, vous pouvez créer et affecter des paramètres de messagerie aux appareils Android suivants :

- Android Samsung Knox Standard
- Android Entreprise

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange.
- **Nom du compte** : entrez le nom d’affichage du compte de messagerie. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (AAD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :
  - **Nom d’utilisateur principal** : obtient le nom, comme `user1` ou `user1@contoso.com`
  - **Nom d’utilisateur** : Obtient seulement le nom, comme `user1`
  - **Nom de compte SAM** : nécessite le domaine, comme `domain\user1`. Le nom de compte SAM peut être utilisé seulement avec les appareils Android. Android Entreprise n’est pas pris en charge.

    Entrez également :  
    - **Source du nom de domaine d’utilisateur** : choisissez **AAD** (Azure Active Directory) ou **Personnalisé**.

      Quand vous choisissez d’obtenir les attributs auprès **d’AAD**, entrez :
      - **Attribut de nom de domaine d’utilisateur dans AAD** : choisissez d’obtenir l’attribut **Nom de domaine complet** ou **Nom NetBIOS** de l’utilisateur

      Quand vous choisissez d’utiliser des attributs **Personnalisés**, entrez :
      - **Nom de domaine personnalisé à utiliser** : entrez une valeur utilisée par Intune pour le nom de domaine, comme `contoso.com` ou `contoso`

- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Sélectionnez **Nom d’utilisateur principal** (`user1@contoso.com` ou `user1`) pour utiliser le nom principal complet comme adresse e-mail, ou **Adresse SMTP principale** (`user1@contoso.com`) pour utiliser l’adresse SMTP principale pour vous connecter à Exchange.

- **Méthode d’authentification** : sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez préalablement créé pour authentifier la connexion Exchange.

### <a name="security-settings"></a>Paramètres de sécurité

- **SSL** : utilisez une communication SSL (Secure Sockets Layer) pour envoyer et recevoir des e-mails, et communiquer avec le serveur Exchange.
- **S/MIME** : envoyez les e-mails sortants avec le chiffrement S/MIME.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez préalablement créé pour authentifier la connexion Exchange.

### <a name="synchronization-settings"></a>Paramètres de synchronisation

- **Nombre d’e-mails à synchroniser** : sélectionnez le nombre de jours de messagerie à synchroniser ou sélectionnez **Illimité** pour synchroniser tous les messages disponibles.
- **Planification de la synchronisation** : sélectionnez la planification selon laquelle les appareils synchronisent les données à partir du serveur Exchange. Vous pouvez également sélectionner **À mesure que les messages arrivent** pour synchroniser les données quand elles arrivent ou **Manuel** pour que ce soit l’utilisateur de l’appareil qui lance la synchronisation.

### <a name="content-sync-settings"></a>Paramètres de synchronisation du contenu

- **Type de contenu à synchroniser** : sélectionnez les types de contenu à partir desquels vous voulez synchroniser les appareils :
  - **Contacts**
  - **Calendrier**
  - **Tâches**

## <a name="android-enterprise"></a>Android Entreprise

- **Application de messagerie** : sélectionnez **Gmail** ou **Nine Work**
- **Serveur de messagerie** : le nom d’hôte de votre serveur Exchange.
- **Attribut de nom d’utilisateur d’AAD** : il s’agit de l’attribut dans Active Directory (AD) ou Azure AD, qui doit être utilisé pour générer le nom d’utilisateur de ce profil de messagerie. Sélectionnez **Adresse SMTP principale**, comme user1@contoso.com ou **Nom d’utilisateur principal**, comme user1 ou user1@contoso.com.
- **Attribut d’adresse de messagerie d’AAD** : la façon dont l’adresse e-mail de l’utilisateur est générée sur chaque appareil. Sélectionnez le **Nom d’utilisateur principal** pour utiliser le nom principal complet en tant qu’adresse de messagerie ou **nom d’utilisateur**.
- **Méthode d’authentification** : sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez créé précédemment pour authentifier la connexion Exchange.
- **SSL** : utilisez une communication SSL (Secure Sockets Layer) pour envoyer et recevoir des e-mails, et communiquer avec le serveur Exchange.
- **Nombre d’e-mails à synchroniser** : sélectionnez le nombre de jours de messagerie à synchroniser ou sélectionnez **Illimité** pour synchroniser tous les messages disponibles.
- **Type de contenu à synchroniser** (Nine Work uniquement) : sélectionnez les types de contenu à partir desquels vous voulez synchroniser les appareils :
  - **Contacts**
  - **Calendrier**
  - **Tâches**

## <a name="next-steps"></a>Étapes suivantes
[Configurer les paramètres de messagerie dans Intune](email-settings-configure.md)
