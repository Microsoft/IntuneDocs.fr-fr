---
title: Paramètres Outlook pour les appareils iOS et Android dans Microsoft Intune
description: Créez une stratégie de configuration pour définir les paramètres Microsoft Outlook sur les appareils iOS et Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828728"
---
# <a name="microsoft-outlook-configuration-settings"></a>Paramètres de configuration Microsoft Outlook 

Utilisez une stratégie de configuration pour définir les paramètres Microsoft Outlook sur les appareils iOS et Android. 

Pour créer une stratégie de configuration des applications pour les appareils iOS gérés, consultez [Ajouter des stratégies de configuration des applications pour les appareils iOS gérés](app-configuration-policies-use-ios.md). Pour créer une stratégie de configuration des applications pour les appareils Android gérés, consultez [Ajouter des stratégies de configuration des applications pour les appareils Android gérés](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Paramètres de configuration

Quand vous ajoutez une stratégie de configuration dans Intune, vous pouvez définir des paramètres spécifiques pour configurer Microsoft Outlook. Dans le volet **Paramètres de configuration**, vous pouvez définir la configuration du compte e-mail.

### <a name="email-account-settings"></a>Paramètres de compte e-mail

Les paramètres de configuration suivants sont spécifiques à Microsoft Outlook.

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange.
- **Nom du compte e-mail** : entrez le nom d’affichage du compte e-mail. Ce nom est présenté aux utilisateurs sur leurs appareils.
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
- **Domaine du compte** : (facultatif) domaine du compte.

## <a name="next-steps"></a>Étapes suivantes
[Configurer les paramètres de messagerie dans Intune](email-settings-configure.md)

