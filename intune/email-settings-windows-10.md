---
title: Paramètres de messagerie pour les appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Créez un profil de messagerie de configuration d’appareil qui utilise des serveurs Exchange et récupère des attributs à partir d’Azure Active Directory. Vous pouvez également activer le protocole SSL et synchroniser l’e-mail et les planifications sur les appareils Windows 10 à l’aide de Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bf9581fe81aea3d2671da0adb2d37bbc203875c8
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303529"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Paramètres de profil de messagerie pour les appareils exécutant Windows 10 - Intune

Utilisez les paramètres de profil de messagerie pour configurer l’application Courrier sur vos appareils Windows 10.

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

- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Sélectionnez **Nom d’utilisateur principal** (`user1@contoso.com` ou `user1`) pour utiliser le nom principal complet comme adresse e-mail, ou **Adresse SMTP principale** (`user1@contoso.com`) pour utiliser l’adresse SMTP principale pour vous connecter à Exchange.

## <a name="security-settings"></a>Paramètres de sécurité

- **SSL** : Utilisez la communication SSL (Secure Sockets Layer) pour envoyer et recevoir des e-mails, et communiquer avec le serveur Exchange.

## <a name="synchronization-settings"></a>Paramètres de synchronisation

- **Nombre d’e-mails à synchroniser** : Choisissez la quantité d’e-mails (en jours) à synchroniser. Vous pouvez aussi sélectionner **Illimité** pour synchroniser tous les messages disponibles.
- **Planification de la synchronisation** : Sélectionnez la planification de la synchronisation des données des appareils à partir du serveur Exchange. Vous pouvez également sélectionner **À mesure que les messages arrivent** pour synchroniser les données dès qu’elles arrivent, ou **Manuel** pour que ce soit l’utilisateur de l’appareil qui lance la synchronisation.

## <a name="content-sync-settings"></a>Paramètres de synchronisation du contenu

- **Type de contenu à synchroniser** : sélectionnez les types de contenu à synchroniser avec les appareils :
  - **Contacts**
  - **Calendrier**
  - **Tâches**

## <a name="next-steps"></a>Étapes suivantes
[Configurer les paramètres de messagerie dans Intune](email-settings-configure.md)
