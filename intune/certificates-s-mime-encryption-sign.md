---
title: Signature et chiffrement S/MIME des e-mails - Azure | Microsoft Docs
description: Utiliser ou activer S/MIME pour signer et chiffrer des e-mails dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eaa85870b289bb3b65ce997d8610324f43d69452
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185642"
---
# <a name="smime-email-signing-and-encryption-in-intune"></a>Signature et chiffrement S/MIME des e-mails dans Intune

> [!IMPORTANT]
> Nous apportons des améliorations à la fonctionnalité de S/MIME décrite dans cet article. Cette fonctionnalité est par conséquent temporairement supprimée d’Intune. Dès qu’elle sera publiée, nous supprimerons cette note.

S/MIME fournit un niveau supplémentaire de sécurité pour vos communications par e-mail à l’aide du chiffrement et du déchiffrement. Microsoft Intune peut utiliser S/MIME afin de signer et chiffrer des e-mails pour les appareils mobiles exécutant iOS, Windows, Windows Phone, Android et macOS.

Sur les appareils iOS, vous pouvez créer un profil e-mail géré par Intune qui utilise S/MIME et des certificats pour signer et chiffrer les e-mails entrants et sortants. Pour d’autres plateformes, S/MIME peut être ou non pris en charge. S’il est pris en charge, vous pouvez installer des certificats qui utilisent le chiffrement et la signature S/MIME. Un utilisateur final peut ensuite activer S/MIME dans son application de messagerie.

Pour plus d’informations sur la signature et le chiffrement S/MIME des e-mails, consultez [S/MIME pour la signature et le chiffrement des messages](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

## <a name="signing-certificates"></a>Certificats de signature

Les certificats utilisés pour la signature permettent à l’application de messagerie cliente de communiquer en toute sécurité avec le serveur de messagerie.

Pour utiliser des certificats de signature, créez un modèle sur votre autorité de certification qui se concentre sur la signature. Sur l’autorité de certification Microsoft Active Directory, [Configurer le modèle de certificat de serveur](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) répertorie les étapes pour créer des modèles de certificats.

Les certificats de signature dans Intune utilisent des certificats PKCS. [Configurer et utiliser des certificats PKCS](certficates-pfx-configure.md) explique comment déployer et utiliser un certificat PKCS dans votre environnement Intune. Ces étapes sont les suivantes :

- Téléchargez et installez Microsoft Intune Certificate Connector pour prendre en charge les demandes de certificat PKCS.
- Créez un profil de certificat racine approuvé pour vos appareils. Cette étape inclut l’utilisation de certificats racine approuvé et intermédiaire pour votre autorité de certification, puis le déploiement du profil sur les appareils.
- Créez un profil de certificat PKCS en utilisant le modèle de certificat que vous avez créé. Ce profil émet des certificats de signatures à destination des appareils et déploie le profil de certificat PKCS sur des appareils.

Vous pouvez également importer un certificat de signature pour un utilisateur spécifique. Le certificat de signature est déployé sur n’importe quel appareil qu’un utilisateur inscrit. Pour importer des certificats dans Intune, utilisez les [applets de commande PowerShell dans GitHub](https://github.com/Microsoft/Intune-Resource-Access). Pour déployer un certificat PKCS importé dans Intune à utiliser pour la signature des e-mails, suivez les étapes de [Configurer et utiliser des certificats PKCS avec Intune](certficates-pfx-configure.md). Ces étapes sont les suivantes :

- Téléchargez et installez PFX Certificate Connector pour Microsoft Intune. Ce connecteur fournit des certificats PKCS importés aux appareils.
- Importez des certificats de signature S/MIME des e-mails dans Intune.
- Créez un profil de certificat importé PKCS. Ce profil fournit des certificats PKCS importés aux appareils de l’utilisateur approprié.

## <a name="encryption-certificates"></a>Certificats de chiffrement

Les certificats utilisés pour le chiffrement confirment qu’un e-mail chiffré peut uniquement être déchiffré par le destinataire souhaité. Le chiffrement S/MIME est une couche supplémentaire de sécurité qui peut être utilisée dans des communications par e-mail.

Quand vous envoyez un e-mail chiffré à un autre utilisateur, la clé publique du certificat de chiffrement de cet utilisateur est obtenue et chiffre l’e-mail que vous envoyez. Le destinataire déchiffre l’e-mail à l’aide de la clé privée sur son appareil. Les utilisateurs peuvent avoir un historique des certificats utilisés pour chiffrer un e-mail. Chacun de ces certificats doit être déployé sur l’ensemble des appareils d’un utilisateur spécifique afin que l’e-mail soit correctement déchiffré.

Il est recommandé de ne pas créer les certificats de chiffrement des e-mails dans Intune. Même si Intune accepte l’émission de certificats PKCS qui prennent en charge le chiffrement, Intune crée un certificat unique par appareil. Un certificat unique par appareil n’est pas idéal pour un scénario de chiffrement S/MIME où le certificat de chiffrement doit être partagé entre tous les appareils de l’utilisateur.

Pour déployer des certificats S/MIME à l’aide d’Intune, vous devez importer tous les certificats de chiffrement d’un utilisateur dans Intune. Intune déploie ensuite tous ces certificats sur chaque appareil qu’un utilisateur inscrit. Pour importer des certificats dans Intune, utilisez les [applets de commande PowerShell dans GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Pour déployer un certificat PKCS importé dans Intune à utiliser pour le chiffrement des e-mails, suivez les étapes de [Configurer et utiliser des certificats PKCS avec Intune](certficates-pfx-configure.md). Ces étapes sont les suivantes :

- Téléchargez et installez PFX Certificate Connector pour Microsoft Intune. Ce connecteur fournit des certificats PKCS importés aux appareils.
- Importez des certificats de chiffrement S/MIME des e-mails dans Intune.
- Créez un profil de certificat importé PKCS. Ce profil fournit des certificats PKCS importés aux appareils de l’utilisateur approprié.

 > [!NOTE]
 > Les certificats de chiffrement S/MIME importés sont supprimés par Intune quand les données d’entreprise sont supprimées ou que les utilisateurs sont désinscrits de la gestion. Toutefois, les certificats ne sont pas révoqués sur l’autorité de certification.

## <a name="smime-email-profiles"></a>Profils e-mail S/MIME

Une fois que vous avez créé des profils de certificat de chiffrement et de signature S/MIME, vous pouvez [activer S/MIME pour l’application de messagerie native iOS](email-settings-ios.md).