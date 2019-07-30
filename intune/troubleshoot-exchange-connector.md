---
title: Résoudre les problèmes du connecteur Exchange
titleSuffix: Microsoft Intune
description: Résolvez les problèmes liés au connecteur Exchange local Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea3ae66a32353b4aa6c782b13e6a587ee1f4464e
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68491821"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Résoudre les problèmes liés au connecteur Exchange local Intune

Cet article explique comment résoudre les problèmes liés au connecteur Exchange local Intune.

## <a name="steps-for-checking-the-connector-configuration"></a>Étapes de vérification de la configuration du connecteur 

Vérifiez que la [configuration du connecteur Exchange local Intune](exchange-connector-install.md) est correcte. Voici quelques problèmes courants. Après avoir effectué les corrections, vérifiez si le problème est résolu.

- Dans la boîte de dialogue Connecteur Microsoft Intune Exchange, vérifiez que vous avez spécifié un compte d’utilisateur qui dispose des autorisations appropriées pour exécuter les [applets de commande Windows PowerShell Exchange nécessaires](exchange-connector-install.md#exchange-cmdlet-requirements).
- Activez les notifications et spécifiez un compte de notification.
- Lors de la configuration du connecteur Exchange, spécifiez un serveur d’accès au client qui est aussi proche que possible du serveur qui héberge le connecteur Exchange. La latence de communication entre le serveur d’accès au client et le connecteur Exchange peut entraîner des retards dans la découverte des appareils, en particulier lors de l’utilisation d’Exchange Online dédié.
- L’accès d’un utilisateur avec un appareil nouvellement inscrit peut être retardé jusqu’au moment où le connecteur Exchange se synchronise avec le serveur d’accès au client Exchange. Une synchronisation complète est effectuée une fois par jour et une synchronisation (rapide) delta se produit plusieurs fois par jour.  Vous pouvez [forcer manuellement une synchronisation rapide ou complète](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) pour minimiser les délais.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Appareil Exchange ActiveSync non découvert à partir d’Exchange
[Surveillez l’activité du connecteur Exchange](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) pour voir si le connecteur Exchange se synchronise avec le serveur Exchange. Si une synchronisation complète ou rapide a été effectuée correctement depuis que l’appareil est joint, vous pouvez passer à la recherche d’autres problèmes possibles, répertoriés ci-dessous. Si aucune synchronisation n’a eu lieu, collectez les journaux de synchronisation et joignez-les à une demande de support.

- Vérifiez que les utilisateurs ont une licence Intune ; si ce n’est pas le cas, le connecteur Exchange ne détecte pas leurs appareils.
- Si l’adresse SMTP principale d’un utilisateur est différente de son UPN dans Azure Active Directory, le connecteur Exchange ne détecte aucun appareil pour cet utilisateur. Corrigez l’adresse SMTP principale pour résoudre le problème.
- Si vous avez des serveurs de boîtes aux lettres Exchange 2010 et Exchange 2013 dans votre environnement, nous vous recommandons de faire pointer le connecteur Exchange vers un serveur d’accès au client Exchange 2013. Dans le cas contraire, si le connecteur Exchange est configuré pour communiquer avec un serveur d’accès au client Exchange 2010, le connecteur Exchange ne découvre pas les appareils des utilisateurs Exchange 2013. 
- Pour les environnements Exchange Online dédiés, vous devez faire pointer le connecteur Exchange vers un serveur d’accès au client Exchange 2013 (et non pas vers un serveur d’accès au client Exchange 2010) dans l’environnement dédié lors de la configuration initiale, car le connecteur communique seulement avec ce serveur d’accès au client lors de l’exécution d’applets de commande PowerShell.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Utilisation de PowerShell pour obtenir plus de données sur les problèmes liés au connecteur Exchange
- Pour obtenir la liste de tous les périphériques mobiles d’une boîte aux lettres, utilisez`Get-ActiveSyncDeviceStatistics -mailbox mbx`
- Pour obtenir la liste des adresses SMTP d’une boîte aux lettres, utilisez`Get-Mailbox -Identity user | select emailaddresses | fl`
- Pour obtenir des informations sur l’état d’accès du périphérique, utilisez `Get-CASMailbox <upn> | fl`

## <a name="next-steps"></a>Étapes suivantes
Si ces informations ne vous aident pas, vous pouvez également [obtenir du support technique pour Microsoft Intune](get-support.md).
