---
title: Résoudre les problèmes du connecteur Exchange
titleSuffix: Microsoft Intune
description: Résolvez les problèmes liés au connecteur Exchange local Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508848"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Résoudre les problèmes liés au connecteur Intune Exchange

Cet article explique comment résoudre les problèmes liés au connecteur Intune Exchange.

## <a name="before-you-start"></a>Avant de commencer

Avant de commencer à résoudre les problèmes liés à un connecteur Exchange dans Intune, recueillez des informations de base afin de travailler sur une base solide. Cette approche peut vous aider à mieux comprendre la nature du problème et à le résoudre plus rapidement.

- Vérifiez que votre processus répond à la configuration requise pour l’installation. Consultez [Configurer le connecteur Intune Exchange local](exchange-connector-install.md).
- Vérifiez que votre compte dispose des autorisations d’administrateur Exchange et Intune.
- Notez le texte du message d’erreur complet et exact, les détails et l’emplacement d’affichage du message.
- Déterminez à quel moment le problème a démarré : 
  - Configurez-vous le connecteur pour la première fois ? 
  - Le connecteur fonctionne-t-il correctement, puis échoue-t-il ?
  - Si elle fonctionnait, quelles modifications se sont produites dans l’environnement Intune, dans l’environnement Exchange ou sur l’ordinateur qui exécute le logiciel connecteur ?
- Qu’est-ce que l’autorité MDM ? Si c’est System Center Configuration Manager, quelle version de Configuration Manager utilisez-vous ?
- Quelle version d’Exchange utilisez-vous ?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Utiliser PowerShell pour obtenir plus de données sur les problèmes liés au connecteur Exchange

- Pour obtenir la liste de tous les périphériques mobiles d’une boîte aux lettres, utilisez `Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Pour obtenir la liste des adresses SMTP d’une boîte aux lettres, utilisez `Get-Mailbox -Identity user | select emailaddresses | fl`
- Pour obtenir des informations sur l’état d’accès du périphérique, utilisez `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>Vérifier la configuration du connecteur

Passez en revue la [Configuration requise pour le connecteur Exchange local](exchange-connector-install.md#intune-exchange-connector-requirements) pour vous assurer que votre environnement et le connecteur sont correctement configurés. 

### <a name="general-considerations-for-the-connector"></a>Considérations générales pour le connecteur

- Assurez-vous que votre pare-feu et vos serveurs proxy autorisent la communication entre le serveur qui héberge le connecteur Exchange Intune et le service Intune.

- L’ordinateur qui héberge le connecteur Exchange Intune et le serveur d’accès au client Exchange (CAS) doit être joint à un domaine et se trouver sur le même réseau local. Assurez-vous que les autorisations requises sont ajoutées pour le compte utilisé par Intune Exchange Connector.

- Le compte de notification est utilisé pour récupérer les paramètres de *découverte automatique* . Pour plus d’informations sur les Autodisover dans Exchange, consultez [découverte automatique dans Exchange Server](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016).

- Intune Exchange Connector envoie une demande à l’URL EWS en utilisant les informations d’identification du compte de notification pour envoyer des messages électroniques de notification avec le lien de *prise en main* (pour s’inscrire à Intune). L’utilisation du lien de *prise en main* pour l’inscription est une condition requise pour les appareils Android non Knox. Dans le cas contraire, ces appareils seront bloqués par l’accès conditionnel.

### <a name="common-issues-for-connector-configurations"></a>Problèmes courants pour les configurations de connecteur

- **Autorisations de compte** : dans la boîte de dialogue Connecteur Microsoft Intune Exchange, vérifiez que vous avez spécifié un compte d’utilisateur qui dispose des autorisations appropriées pour exécuter les [applets de commande Windows PowerShell Exchange nécessaires](exchange-connector-install.md#exchange-cmdlet-requirements).
- **E-mails de notification**: activez les notifications et spécifiez un compte de notification.
- **Synchronisation du serveur d’accès au client**: lors de la configuration du connecteur Exchange, spécifiez une autorité de certification qui a la plus faible latence réseau possible pour le serveur hébergeant le connecteur Exchange. La latence de communication entre le serveur d’accès au client et le connecteur Exchange peut entraîner des retards dans la découverte des appareils, en particulier lors de l’utilisation d’Exchange Online dédié.
- **Calendrier des synchronisations** : l’accès d’un utilisateur avec un appareil nouvellement inscrit peut être retardé jusqu’au moment où le connecteur Exchange se synchronise avec le serveur d’accès au client Exchange. Une synchronisation complète est effectuée une fois par jour et une synchronisation (rapide) delta se produit plusieurs fois par jour. Vous pouvez [forcer manuellement une synchronisation rapide ou complète](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) pour minimiser les délais.

## <a name="next-steps"></a>Étapes suivantes
Les articles suivants peuvent vous aider à résoudre des problèmes courants et des erreurs spécifiques :

- [Résolvez les problèmes courants liés à Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md).
- [Résolvez les erreurs courantes pour Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Demandez de l’aide au support technique ou à la communauté Intune :

- Consultez [obtenir](../fundamentals/get-support.md) de l’aide pour utiliser la console Intune pour résoudre le problème ou pour ouvrir un dossier de support auprès de Microsoft. 
- Publiez votre problème dans les [forums Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
