---
title: Configurer les paramètres de messagerie pour les appareils iOS/iPadOS dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres e-mail que vous pouvez configurer et ajouter aux appareils iOS et iPadOS dans Microsoft Intune, notamment sur l’utilisation des serveurs Exchange et l’obtention d’attributs à partir d’Azure Active Directory. Vous pouvez également activer le protocole SSL, authentifier les utilisateurs avec des certificats ou un nom d’utilisateur/mot de passe, et synchroniser les e-mails sur les appareils iOS/iPadOS en utilisant des profils de configuration d’appareil Microsoft Intune.
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
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ea06c50b1da237d4a822e80a8085b3b51913cec
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512804"
---
# <a name="add-e-mail-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Ajouter des paramètres de messagerie pour les appareils iOS et iPadOS dans Microsoft Intune

Dans Microsoft Intune, vous pouvez créer et configurer votre messagerie de sorte qu’elle se connecte à un serveur e-mail. Vous pouvez également choisir la façon dont les utilisateurs s’authentifient, utiliser S/MIME pour le chiffrement, et bien plus encore.

Cet article liste et décrit tous les paramètres d’e-mail qui sont disponibles pour les appareils iOS/iPadOS. Vous pouvez créer un profil de configuration d’appareil pour envoyer (push) ou déployer ces paramètres d’e-mail sur vos appareils iOS/iPadOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](../email-settings-configure.md).

> [!NOTE]
> Ces paramètres sont disponibles pour tous les types d’inscription. Pour plus d’informations sur les types d’inscriptions, consultez [Inscription iOS/iPadOS](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>Paramètres du compte Exchange ActiveSync

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange.
- **Nom du compte** : entrez le nom d’affichage du compte de messagerie. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (AAD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Les options disponibles sont les suivantes :
  - **Nom principal de l’utilisateur** : Obtient le nom, par exemple `user1` ou `user1@contoso.com`
  - **Adresse SMTP principale** : Obtient le nom au format d’une adresse e-mail, comme `user1@contoso.com`.
  - **Nom de compte SAM** : nécessite le domaine, par exemple `domain\user1`. Entrez également :  
    - **Source du nom de domaine d’utilisateur** : choisissez **AAD** (Azure Active Directory) ou **Personnalisé**.
      - **AAD** : obtenez les attributs à partir d’Azure AD. Entrez également :
        - **Attribut de nom de domaine d’utilisateur dans AAD** : choisissez d’obtenir l’attribut **Nom de domaine complet** (`contoso.com`) ou **Nom NetBIOS** (`contoso`) de l’utilisateur.

      - **Personnalisé** : obtenez les attributs à partir d’un nom de domaine personnalisé. Entrez également :
        - **Nom de domaine personnalisé à utiliser** : entrez une valeur utilisée par Intune pour le nom de domaine, par exemple `contoso.com` ou `contoso`.

- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Les options disponibles sont les suivantes :
  - **Nom d’utilisateur principal** : utilisez le nom principal complet (par exemple, `user1@contoso.com` ou `user1`) comme adresse e-mail.
  - **Adresse SMTP principale** : utilisez l’adresse SMTP principale (par exemple, `user1@contoso.com`) pour la connexion à Exchange.
- **Méthode d’authentification** : choisissez la façon dont les utilisateurs s’authentifient auprès du serveur e-mail. Les options disponibles sont les suivantes :
  - **Certificat** : sélectionnez un profil de certificat SCEP ou PKCS client que vous avez créé précédemment pour authentifier la connexion Exchange. Cette option offre à vos utilisateurs l’expérience la plus sûre et la plus fluide.
  - **Nom d’utilisateur et mot de passe** : les utilisateurs sont invités à entrer leur nom d’utilisateur et leur mot de passe.
  - **Informations d’identification dérivées** : utilisez un certificat dérivé de la carte à puce d’un utilisateur. Pour plus d’informations, consultez [Utiliser des informations d’identification dérivées dans Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > L’authentification multifacteur Azure n’est pas prise en charge.
  
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

## <a name="exchange-activesync-profile-configuration"></a>Configuration du profil Exchange ActiveSync

> [!IMPORTANT]
> La configuration de ces paramètres déploie un nouveau profil sur l’appareil, même lorsqu’un profil de messagerie existant est mis à jour pour inclure ces paramètres. Les utilisateurs sont invités à entrer le mot de passe de leur compte Exchange ActiveSync. Ces paramètres prennent effet lorsque le mot de passe est saisi.

- **Données Exchange à synchroniser** : lorsque vous utilisez Exchange ActiveSync, choisissez les services Exchange qui sont synchronisés sur l’appareil : Calendrier, Contacts, Rappels, Notes et E-mail. Les options disponibles sont les suivantes :
  - **Toutes les données** (par défaut) : la synchronisation est activée pour tous les services.
  - **E-mail uniquement** : la synchronisation est activée pour les e-mails uniquement. La synchronisation est désactivée pour les autres services.
  - **Calendrier uniquement** : la synchronisation est activée pour le calendrier uniquement. La synchronisation est désactivée pour les autres services.
  - **Calendrier et Contacts uniquement** : la synchronisation est activée pour le calendrier et les contacts uniquement. La synchronisation est désactivée pour les autres services.
  - **Contacts uniquement** : la synchronisation est activée pour les contacts uniquement. La synchronisation est désactivée pour les autres services.

  Cette fonctionnalité s’applique à :  
  - iOS 13.0 et ultérieur
  - iPadOS 13.0 et ultérieur

- **Autoriser les utilisateurs à modifier les paramètres de synchronisation** : choisissez si les utilisateurs peuvent modifier les paramètres Exchange ActiveSync pour les services Exchange sur l’appareil : Calendrier, Contacts, Rappels, Notes et E-mail. Les options disponibles sont les suivantes :

  - **Oui** (valeur par défaut) : les utilisateurs peuvent modifier le comportement de synchronisation de tous les services. Si vous choisissez **Oui**, les modifications sont autorisées pour *tous* les services.
  - **Non** : les utilisateurs ne peuvent pas modifier les paramètres de synchronisation de tous les services. Si vous choisissez **Non**, les modifications sont bloquées pour *tous* les services.

  > [!TIP]
  > Si vous avez configuré le paramètre **Données Exchange à synchroniser** pour synchroniser uniquement certains services, nous vous recommandons de sélectionner **Non** pour ce paramètre. Le fait de choisir **Non** empêche les utilisateurs de modifier le service Exchange qui est synchronisé.

  Cette fonctionnalité s’applique à :  
  - iOS 13.0 et ultérieur
  - iPadOS 13.0 et ultérieur

## <a name="exchange-activesync-email-settings"></a>Paramètres de messagerie Exchange ActiveSync

- **S/MIME** : S/MIME utilise des certificats de messagerie qui fournissent une sécurité supplémentaire à vos communications par e-mail en signant, en chiffrant et en déchiffrant. Lorsque vous utilisez l’option S/MIME pour un e-mail, vous pouvez vérifier l’authenticité de l’expéditeur, ainsi que l’intégrité et la confidentialité du message.

  Les options disponibles sont les suivantes :

  - **Désactiver S/MIME** (par défaut) : n’utilise pas un certificat de messagerie S/MIME pour signer, chiffrer ou déchiffrer des e-mails.
  - **Activer S/MIME** : permet aux utilisateurs de se connecter et/ou de chiffrer des e-mails dans l’application de messagerie native iOS/iPadOS. Entrez également :

    - **Signature S/MIME activée** : l’option **Désactiver** (valeur par défaut) ne permet pas aux utilisateurs de signer numériquement le message. **Activer** : permet aux utilisateurs de signer numériquement les e-mails sortants pour le compte que vous avez entré. La signature permet aux utilisateurs qui reçoivent un message d’être sûrs que celui-ci provient réellement d’un expéditeur donné, et non d’une personne se faisant passer pour lui.
      - **Autoriser l’utilisateur à modifier le paramètre** : l’option **Activer** permet aux utilisateurs de modifier les options de signature. L’option **Désactiver** (valeur par défaut) empêche les utilisateurs de modifier la signature et les force à utiliser la signature que vous avez configurée.
      - **Type de certificat de signature** : Vos options :
        - **Non configuré** : Intune ne change pas ni ne met à jour ce paramètre.
        - **Aucun** : en tant qu’administrateur, vous ne forcez pas un certificat spécifique. Sélectionnez cette option pour que les utilisateurs puissent choisir leur propre certificat.
        - **Informations d’identification dérivées** : utilisez un certificat dérivé de la carte à puce d’un utilisateur. Pour plus d’informations, consultez [Utiliser des informations d’identification dérivées dans Microsoft Intune](../protect/derived-credentials.md).
        - **Certificats** : Sélectionnez un profil de certificat PKCS ou SCEP existant qui est utilisé pour la signature des e-mails.
      - **Autoriser l’utilisateur à modifier le paramètre** : l’option **Activer** permet aux utilisateurs de modifier le certificat de signature. L’option **Désactiver** (par défaut) empêche les utilisateurs de modifier le certificat de signature, et les force à utiliser celui que vous avez configuré.

        Cette fonctionnalité s’applique à :  
        - iOS 12 et versions ultérieures
        - iPadOS 12 et versions ultérieures

    - **Chiffrer par défaut** : L’option **Activer** chiffre par défaut tous les messages. L’option **Désactiver** (par défaut) ne chiffre pas par défaut tous les messages.
      - **Autoriser l’utilisateur à changer le paramètre** : L’option **Activer** permet aux utilisateurs de modifier le comportement de chiffrement par défaut. L’option **Désactiver** empêche les utilisateurs de modifier le comportement de chiffrement par défaut, et les force à utiliser le chiffrement que vous avez configuré.

        Cette fonctionnalité s’applique à :  
        - iOS 12 et versions ultérieures
        - iPadOS 12 et versions ultérieures

    - **Forcer le chiffrement par message** : Le chiffrement par message permet aux utilisateurs de choisir quels e-mails chiffrer avant de les envoyer.

      **Activer** : affiche l’option de chiffrement par message lors de la création d’un e-mail. Les utilisateurs peuvent ensuite accepter ou refuser le chiffrement par message. Si le paramètre **Chiffrer par défaut** est également activé, l’activation du chiffrement par message permet aux utilisateurs de refuser le chiffrement par message.

      L’option **Désactiver** (par défaut) empêche l’affichage de l’option de chiffrement par message. Si le paramètre **Chiffrer par défaut** est aussi désactivé, l’activation du chiffrement par message permet aux utilisateurs d’accepter le chiffrement par message.

      - **Type de certificat de chiffrement** : Vos options :
        - **Non configuré** : Intune ne change pas ni ne met à jour ce paramètre.
        - **Aucun** : en tant qu’administrateur, vous ne forcez pas un certificat spécifique. Sélectionnez cette option pour que les utilisateurs puissent choisir leur propre certificat.
        - **Informations d’identification dérivées** : utilisez un certificat dérivé de la carte à puce d’un utilisateur. Pour plus d’informations, consultez [Utiliser des informations d’identification dérivées dans Microsoft Intune](../protect/derived-credentials.md).
        - **Certificats** : Sélectionnez un profil de certificat PKCS ou SCEP existant qui est utilisé pour la signature des e-mails.
      - **Autoriser l’utilisateur à changer le paramètre** : L’option **Activer** permet aux utilisateurs de modifier le certificat de chiffrement. L’option **Désactiver** (par défaut) empêche les utilisateurs de modifier le certificat de chiffrement, et les force à utiliser celui que vous avez configuré.

        Cette fonctionnalité s’applique à :  
        - iOS 12 et versions ultérieures
        - iPadOS 12 et versions ultérieures

- **Nombre d’e-mails à synchroniser** : Choisissez la quantité d’e-mails (en jours) à synchroniser. Vous pouvez aussi sélectionner **Illimité** pour synchroniser tous les messages disponibles.
- **Autoriser le déplacement des messages vers d’autres comptes e-mail** : L’option **Activer** (valeur par défaut) permet aux utilisateurs de déplacer des e-mails entre différents comptes qu’ils ont configurés sur leurs appareils.
- **Autoriser l’envoi d’e-mails à partir d’applications tierces** : L’option **Activer** (valeur par défaut) permet aux utilisateurs de sélectionner ce profil comme compte par défaut pour l’envoi d’e-mails. Les applications tierces peuvent ainsi ouvrir les e-mails dans l’application de messagerie native, par exemple pour joindre des fichiers à un e-mail.
- **Synchroniser les adresses e-mail récemment utilisées** : L’option **Activer** (valeur par défaut) permet aux utilisateurs de synchroniser avec le serveur la liste des adresses e-mail qui ont été récemment utilisées sur l’appareil.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](../device-profile-assign.md) et [superviser son état](../device-profile-monitor.md).

Configurez les paramètres de messagerie sur les appareils [Android](../email-settings-android.md), [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md) et [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
