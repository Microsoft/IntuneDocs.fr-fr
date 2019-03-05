---
title: Paramètres de messagerie pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres e-mail que vous pouvez configurer et ajouter aux appareils iOS dans Microsoft Intune, notamment sur l’utilisation des serveurs Exchange et l’obtention d’attributs à partir d’Azure Active Directory. Vous pouvez également activer le protocole SSL, authentifier les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe, et synchroniser les e-mails sur les appareils iOS en utilisant des profils de configuration d’appareil Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9bc681b017cef5a91e7bc10bbdfbd6e14943e43a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229086"
---
# <a name="email-profile-settings-for-ios-devices-in-intune"></a>Paramètres de profil e-mail pour les appareils iOS dans Intune

Dans Microsoft Intune, vous pouvez créer et configurer votre messagerie de sorte qu’elle se connecte à un serveur e-mail. Vous pouvez également choisir la façon dont les utilisateurs s’authentifient, utiliser S/MIME pour le chiffrement, et bien plus encore.

Cet article liste et décrit tous les paramètres d’e-mail qui sont disponibles pour les appareils iOS. Vous pouvez créer un profil de configuration d’appareil pour envoyer (push) ou déployer ces paramètres d’e-mail sur vos appareils iOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](email-settings-configure.md#create-a-device-profile).

## <a name="email-settings"></a>Paramètres de messagerie

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange.
- **Nom du compte** : entrez le nom d’affichage du compte de messagerie. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (AAD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :
  - **Nom principal de l’utilisateur** : Obtient le nom, par exemple `user1` ou `user1@contoso.com`
  - **Adresse SMTP principale** : Obtient le nom au format d’une adresse e-mail, comme `user1@contoso.com`.
  - **Nom de compte SAM** : nécessite le domaine, par exemple `domain\user1`.

    Entrez également :  
    - **Source du nom de domaine d’utilisateur** : choisissez **AAD** (Azure Active Directory) ou **Personnalisé**.

      Quand vous choisissez d’obtenir les attributs auprès **d’AAD**, entrez :
      - **Attribut de nom de domaine d’utilisateur dans AAD** : choisissez d’obtenir l’attribut **Nom de domaine complet** ou **Nom NetBIOS** de l’utilisateur

      Quand vous choisissez d’utiliser des attributs **Personnalisés**, entrez :
      - **Nom de domaine personnalisé à utiliser** : entrez une valeur utilisée par Intune pour le nom de domaine, par exemple `contoso.com` ou `contoso`

- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Sélectionnez **Nom d’utilisateur principal** (`user1@contoso.com` ou `user1`) pour utiliser le nom principal complet comme adresse e-mail. Sélectionnez **Adresse SMTP principale** (`user1@contoso.com`) pour utiliser l’adresse SMTP principale des utilisateurs pour se connecter à Exchange.
- **Méthode d’authentification** : Sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie. L’authentification multifacteur Azure n’est pas prise en charge.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez créé précédemment et qui sert à authentifier la connexion Exchange.
- **SSL** : L’option **Activer** utilise une communication SSL (Secure Sockets Layer) afin d’envoyer et de recevoir des e-mails, et de communiquer avec le serveur Exchange.
- **OAuth** : L’option **Activer** utilise une communication OAuth (Open Authorization) afin d’envoyer et de recevoir des e-mails, et de communiquer avec Exchange. Si votre serveur OAuth utilise l’authentification par certificat, choisissez **certificat** comme **Méthode d’authentification** et incluez le certificat avec le profil. Sinon, choisissez **Nom d’utilisateur et mot de passe** comme **Méthode d’authentification**. Quand vous utilisez OAuth :

  - Vérifiez que votre solution de messagerie prend en charge OAuth avant de cibler ce profil à vos utilisateurs. Office 365 Exchange Online prend en charge OAuth. Exchange local et d’autres solutions proposées par des partenaires ou des tiers peuvent ne pas prendre en charge OAuth. Exchange local peut être configuré pour l’authentification moderne (consultez le billet de blog [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/)).

    Si le profil de messagerie utilise Oauth et que le service de messagerie ne le prend pas en charge, l’option **Entrer à nouveau le mot de passe** apparaît hors d’usage. Par exemple, rien ne se produit quand l’utilisateur sélectionne **Entrer à nouveau le mot de passe** dans les paramètres des appareils d’Apple.

  - Quand OAuth est activé, les utilisateurs finaux bénéficient d’une expérience de connexion à la messagerie différente (« authentification moderne »), qui prend en charge l’authentification multifacteur (MFA). 

  - Certaines organisations empêchent l’utilisateur final [d’accéder aux applications en libre-service](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). Dans ce scénario, la connexion par authentification moderne peut échouer jusqu’à ce qu’un administrateur crée l’application d’entreprise « Comptes iOS » et accorde aux utilisateurs l’accès à l’application dans Azure AD.

    L’action par défaut consiste à ajouter une application à l’aide de la fonctionnalité **Ajouter une application** du [panneau d’accès aux applications](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **sans l’approbation de l’entreprise**. Pour plus d’informations, consultez [Affecter des utilisateurs aux applications](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Quand vous activez OAuth, voilà ce qui se passe :  
  > 1. Un nouveau profil est émis aux appareils qui sont déjà ciblés.
  > 2. Les utilisateurs finaux sont invités à retaper leurs informations d’identification.

- **S/MIME** : L’option **Activer S/MIME** permet aux utilisateurs de se connecter et/ou de chiffrer des e-mails dans l’application de messagerie native iOS. 

  Lorsque vous utilisez l’option S/MIME pour un e-mail, vous pouvez vérifier l’authenticité de l’expéditeur, ainsi que l’intégrité et la confidentialité du message.

  - **Signature S/MIME activée** : Choisissez **Activer** pour permettre aux utilisateurs de signer numériquement les e-mails sortants pour le compte que vous avez entré. La signature permet aux utilisateurs qui reçoivent un message d’être sûrs que celui-ci provient réellement d’un expéditeur donné, et non d’une personne se faisant passer pour lui. L’option **Désactiver** ne permet pas aux utilisateurs de signer numériquement leurs messages.
    - **Autoriser l’utilisateur à changer le paramètre** : Choisissez **Activer** pour permettre aux utilisateurs de modifier le comportement de signature S/MIME. L’option **Désactiver** empêche les utilisateurs de modifier le paramètre de signature S/MIME que vous avez configuré. Disponible dans iOS 12 et versions ultérieures.

  - **Certificat de signature S/MIME** : Sélectionnez un profil de certificat PKCS ou SCEP existant qui est utilisé pour la signature des e-mails.
    - **Autoriser l’utilisateur à changer le paramètre** : Choisissez **Activer** pour permettre aux utilisateurs de modifier le certificat de signature. L’option **Désactiver** empêche les utilisateurs de modifier le certificat de signature, et les force à utiliser celui que vous avez configuré. Disponible dans iOS 12 et versions ultérieures.

  - **Chiffrer par défaut** : L’option **Activer** chiffre par défaut tous les messages. L’option **Désactiver** ne chiffre pas par défaut tous les messages.
    - **Autoriser l’utilisateur à changer le paramètre** : Choisissez **Activer** pour permettre aux utilisateurs de modifier le comportement de chiffrement par défaut. L’option **Désactiver** empêche les utilisateurs de modifier le comportement de chiffrement par défaut, et les force à utiliser le paramètre que vous avez configuré. Disponible dans iOS 12 et versions ultérieures.

  - **Forcer le chiffrement par message** : Le chiffrement par message permet aux utilisateurs de choisir quels e-mails chiffrer avant de les envoyer. Choisissez **Activer** pour afficher l’option de chiffrement par message lors de la création d’un e-mail. Les utilisateurs peuvent ensuite accepter ou refuser le chiffrement par message. L’option **Désactiver** empêche l’affichage de l’option de chiffrement par message.

    Si le paramètre **Chiffrer par défaut** est activé, l’activation du chiffrement par message permet aux utilisateurs de refuser le chiffrement par message. Si le paramètre **Chiffrer par défaut** est désactivé, l’activation du chiffrement par message permet aux utilisateurs d’accepter le chiffrement par message.

  - **Certificat de chiffrement S/MIME** : Sélectionnez un profil de certificat PKCS ou SCEP existant qui est utilisé pour le chiffrement des e-mails.
    - **Autoriser l’utilisateur à changer le paramètre** : Choisissez **Activer** pour permettre aux utilisateurs de modifier le certificat de chiffrement. L’option **Désactiver** empêche les utilisateurs de modifier le certificat de chiffrement, et les force à utiliser celui que vous avez configuré. Disponible dans iOS 12 et versions ultérieures.
- **Nombre d’e-mails à synchroniser** : Choisissez la quantité d’e-mails (en jours) à synchroniser. Vous pouvez aussi sélectionner **Illimité** pour synchroniser tous les messages disponibles.
- **Autoriser le déplacement des messages vers d’autres comptes e-mail** : L’option **Activer** permet aux utilisateurs de déplacer des e-mails entre différents comptes qu’ils ont configurés sur leur appareil.
- **Autoriser l’envoi d’e-mails à partir d’applications tierces** : Sélectionnez **Activer** pour permettre aux utilisateurs de sélectionner ce profil comme compte par défaut pour l’envoi d’e-mails. Les applications tierces peuvent ainsi ouvrir les e-mails dans l’application de messagerie native, par exemple pour joindre des fichiers à un e-mail.
- **Synchroniser les adresses e-mail récemment utilisées** : Sélectionnez **Activer** pour permettre aux utilisateurs de synchroniser la liste des adresses e-mail qui ont été récemment utilisées sur l’appareil avec le serveur.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Configurez les paramètres d’e-mail sur les appareils [Android](email-settings-android.md), [Windows 10](email-settings-windows-10.md) et [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
