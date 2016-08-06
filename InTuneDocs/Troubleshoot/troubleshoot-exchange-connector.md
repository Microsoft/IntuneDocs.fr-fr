---
title: "Dépannage du connecteur Exchange | Microsoft Intune"
description: "Résoudre des problèmes liés au connecteur Intune Exchange."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b16c19c95384655e170c199597dd6bd31afb90d
ms.openlocfilehash: 04ac69a30f6c1d91fe755f9720fbc2adc51745f7


---

# Dépannage du connecteur Exchange
Cette rubrique décrit comment résoudre les problèmes éventuellement liés au connecteur Intune Exchange.

## Étapes de vérification de la configuration du connecteur 

Vérifiez la configuration du connecteur Exchange et regardez si le problème a été résolu.

- Veillez à spécifier un compte de notification lors de l’installation initiale du connecteur Exchange.
- Le compte de service du connecteur Exchange doit avoir les autorisations appropriées pour exécuter les applets de commande PowerShell utilisées par le connecteur Exchange.
- Lorsque vous configurez le connecteur Exchange, spécifiez un serveur d’accès au client (CAS) qui est aussi proche que possible du serveur qui héberge le connecteur Exchange. La latence de communication entre le serveur d’accès au client et le connecteur Exchange peut entraîner des retards de découverte des appareils, en particulier lorsque vous utilisez O365 dédié.
- N’oubliez pas qu’il existe un décalage dans les synchronisations du connecteur Exchange sur le serveur d’accès au client Exchange. Une synchronisation complète est effectuée une fois par jour et une synchronisation delta (rapide) a lieu toutes les deux heures. Il est probable qu’un utilisateur avec un appareil nouvellement inscrit connaisse un délai dans l’obtention de l’accès.
- 
## Appareil Exchange ActiveSync non découvert à partir d’Exchange
Vérifiez si le connecteur Exchange est synchronisé sur le serveur Exchange. Pour ce faire, recherchez les journaux d’une synchronisation complète ou delta. Référez-vous à Journaux du connecteur Exchange. Si une synchronisation complète ou delta a été effectuée depuis que l’appareil a été associé, il ne s’agit pas de la source du problème. Si aucune synchronisation n’a eu lieu, collectez les journaux de synchronisation et joignez-les à votre demande de support.

- Si un utilisateur ne dispose pas d’une licence Intune, le connecteur Exchange ne détecte pas ses appareils.
- Si l’adresse SMTP principale d’un utilisateur est différente de celle de leur UPN dans AAD, le connecteur Exchange ne détecte aucun appareil de cet utilisateur Intune/AAD. Corrigez l’adresse SMTP principale.
- Si le serveur d’accès au client avec lequel le connecteur Exchange communique pendant un cycle de découverte est un serveur d’accès au client Exchange 2010 et que vous disposez de serveurs de messagerie Exchange 2010 et 2013, le connecteur Exchange ne détecte aucun appareil Exchange 2013 de l’utilisateur. Pour résoudre ce problème, configurez le connecteur Exchange de manière à ce qu’il pointe vers un serveur d’accès au client Exchange 2013.  Bien que ce problème concerne principalement les topologies O365 Dédié, nous vous recommandons comme bonne pratique de définir un serveur d’accès au client Exchange 2013.
- Pour les environnements Exchange dédié (O365 dédié), vous devez faire pointer le connecteur Exchange vers un serveur d’accès au client Exchange 2013 (et non 2010) dans l’environnement dédié lors de l’installation initiale, car il communique uniquement avec ce serveur d’accès au client lors de l’exécution d’applets de commande PowerShell.


## Utilisation de PowerShell pour obtenir plus de données sur les problèmes liés au connecteur Exchange
- Pour obtenir une liste de tous les appareils mobiles d’une boîte aux lettres, utilisez Get-ActiveSyncDeviceStatistics -mailbox mbx
- Pour obtenir une liste des adresses SMTP pour une boîte aux lettres, utilisez Get-Mailbox -Identity user | select emailaddresses | fl.
- Pour obtenir des informations détaillées sur l’état de l’accès à un appareil, utilisez Get-CASMailbox <upn> | fl

### Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Aug16_HO1-->


