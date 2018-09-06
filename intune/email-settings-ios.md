---
title: Paramètres de messagerie pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Créez un profil de messagerie de configuration d’appareil qui utilise des serveurs Exchange et récupère des attributs auprès d’Azure Active Directory. Vous pouvez également activer SSL, authentifier les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe, et synchroniser la messagerie sur les appareils iOS en utilisant Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d27e90655e54051d73989202d2bc849a66208f5
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910800"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>Paramètres de profil de messagerie pour les appareils iOS - Intune

Utilisez les paramètres de profil de messagerie pour configurer vos appareils exécutant iOS.

> [!IMPORTANT]
> Nous apportons des améliorations à la fonctionnalité de S/MIME décrite dans cet article. Cette fonctionnalité est par conséquent temporairement supprimée d’Intune. Dès qu’elle sera publiée, nous supprimerons cette note.

## <a name="email-settings"></a>Paramètres de messagerie

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange.
- **Nom du compte** : entrez le nom d’affichage du compte de messagerie. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (AAD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :
  - **Nom d’utilisateur principal** : obtient le nom, comme `user1` ou `user1@contoso.com`
  - **Adresse SMTP principale** : obtient le nom au format d’une adresse e-mail, comme `user1@contoso.com`.
  - **Nom de compte SAM** : nécessite le domaine, comme `domain\user1`.

    Entrez également :  
    - **Source du nom de domaine d’utilisateur** : choisissez **AAD** (Azure Active Directory) ou **Personnalisé**.

      Quand vous choisissez d’obtenir les attributs auprès **d’AAD**, entrez :
      - **Attribut de nom de domaine d’utilisateur dans AAD** : choisissez d’obtenir l’attribut **Nom de domaine complet** ou **Nom NetBIOS** de l’utilisateur

      Quand vous choisissez d’utiliser des attributs **Personnalisés**, entrez :
      - **Nom de domaine personnalisé à utiliser** : entrez une valeur utilisée par Intune pour le nom de domaine, comme `contoso.com` ou `contoso`

- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Sélectionnez **Nom d’utilisateur principal** (`user1@contoso.com` ou `user1`) pour utiliser le nom principal complet comme adresse e-mail, ou **Adresse SMTP principale** (`user1@contoso.com`) pour utiliser l’adresse SMTP principale pour vous connecter à Exchange.
- **Méthode d’authentification** : sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie. L’authentification multifacteur Azure n’est pas prise en charge.
  - Si vous avez sélectionné **Certificats**, sélectionnez un profil de certificat SCEP ou PKCS client que vous avez créé précédemment et qui sert à authentifier la connexion Exchange.
- **SSL** : sélectionnez **Activer** pour utiliser une communication SSL (Secure Sockets Layer) afin d’envoyer et de recevoir des e-mails, et de communiquer avec le serveur Exchange.
- **S/MIME** : sélectionnez **Activer S/MIME** pour envoyer des e-mails à l’aide de la signature S/MIME. Quand cette option est activée, vous pouvez également chiffrer les e-mails destinés aux destinataires qui peuvent recevoir du courrier électronique chiffré, et déchiffrer les e-mails reçus.
  - Si vous avez sélectionné **Certificat**, sélectionnez un profil de certificat PKCS que vous avez créé précédemment pour authentifier la connexion Exchange et/ou chiffrer les échanges d’e-mails.
- **Nombre d’e-mails à synchroniser** : sélectionnez le nombre de jours d’e-mails à synchroniser. Vous pouvez aussi sélectionner **Illimité** pour synchroniser tous les messages disponibles.
- **Autoriser le déplacement des messages vers d’autres comptes de messagerie** : sélectionnez **Activer** pour permettre aux utilisateurs de déplacer des e-mails entre les différents comptes configurés sur leur appareil.
- **Autoriser l’envoi d’e-mails à partir d’applications tierces** : sélectionnez **Activer** pour autoriser l’utilisateur à sélectionner ce profil comme compte par défaut pour l’envoi d’e-mails, et autoriser les applications tierces à ouvrir les e-mails dans l’application de messagerie native, par exemple pour y joindre des fichiers.
- **Synchroniser les adresses de messagerie récemment utilisées** : sélectionnez **Activer** pour permettre aux utilisateurs de synchroniser la liste des adresses e-mail qui ont été récemment utilisées sur l’appareil avec le serveur.

## <a name="next-steps"></a>Étapes suivantes
[Configurer les paramètres de messagerie dans Intune](email-settings-configure.md)
