---
title: Paramètres Outlook pour les appareils iOS et Android dans Microsoft Intune
description: Créez une stratégie de configuration pour définir les paramètres Microsoft Outlook sur les appareils iOS et Android.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 691029cc7b9fd8880c5440a84b95bbf2462920d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180321"
---
# <a name="microsoft-outlook-configuration-settings"></a>Paramètres de configuration Microsoft Outlook 

Utilisez une stratégie de configuration pour définir les paramètres Microsoft Outlook sur les appareils iOS et Android. 

Pour créer une stratégie de configuration des applications pour les appareils iOS gérés, consultez [Ajouter des stratégies de configuration des applications pour les appareils iOS gérés](app-configuration-policies-use-ios.md). Pour créer une stratégie de configuration des applications pour les appareils Android gérés, consultez [Ajouter des stratégies de configuration des applications pour les appareils Android gérés](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Paramètres de configuration

Quand vous ajoutez une stratégie de configuration dans Intune, vous pouvez définir des paramètres spécifiques pour configurer Microsoft Outlook. Dans le volet **Paramètres de configuration**, vous pouvez définir la configuration du compte e-mail.

### <a name="basic-authentication-email-account-settings"></a>Paramètres de compte de messagerie d’authentification de base
Outlook pour iOS et Android permet aux administrateurs Exchange de d’envoyer (« push ») des configurations de compte à leurs utilisateurs locaux qui utilisent l’authentification de base avec le protocole ActiveSync. Pour plus d’informations, consultez [Configuration de compte dans Outlook pour iOS et Android à l’aide de l’authentification de base](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup). Pour activer la configuration des paramètres d’un compte, vous pouvez configurer les paramètres suivants :

- **Serveur de messagerie** : entrez le nom d’hôte de votre serveur Exchange local (par exemple, mail.contoso.com).
- **Nom du compte e-mail** : entrez le nom d’affichage du compte e-mail. Ce nom est présenté aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : ce nom est l’attribut obtenu par Intune auprès d’Azure Active Directory (Azure AD). Intune génère dynamiquement le nom d’utilisateur qui est utilisé par ce profil. Parmi les options, citons :
  - **Nom d’utilisateur principal** : obtient le nom, comme `user1` ou `user1@contoso.com`
  - **Adresse SMTP principale** : obtient le nom au format d’une adresse e-mail, comme `user1@contoso.com`.
- **Attribut d’adresse e-mail d’AAD** : choisissez comment l’adresse e-mail de l’utilisateur est générée. Sélectionnez **Nom d’utilisateur principal** (`user1@contoso.com` ou `user1`) pour utiliser le nom principal complet comme adresse e-mail, ou **Adresse SMTP principale** (`user1@contoso.com`) pour utiliser l’adresse SMTP principale pour vous connecter à Exchange. Il est recommandé de sélectionner **Adresse SMTP principale**.
- **Domaine du compte** : (facultatif) domaine du compte.

## <a name="next-steps"></a>Étapes suivantes
[Configurer les paramètres de messagerie dans Intune](email-settings-configure.md)

